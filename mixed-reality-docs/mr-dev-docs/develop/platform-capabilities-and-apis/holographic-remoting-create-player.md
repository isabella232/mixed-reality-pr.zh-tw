---
title: 撰寫自訂全像攝影遠端播放程式
description: 建立自訂 Hologaphic 遠端應用程式，以將在遠端電腦上轉譯的內容顯示到您的 HoloLens 2。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、遠端、全像全像 Remoting、NuGet、應用程式資訊清單、播放機內容、遠端應用程式、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 23449749e709075e6530730e596bfcc9cd088c1e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006548"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>撰寫自訂全像攝影遠端播放應用程式

>[!IMPORTANT]
>本檔說明如何建立 HoloLens 2 的自訂播放程式應用程式。 針對 HoloLens 2 撰寫的自訂播放程式與針對 HoloLens 1 所撰寫的遠端應用程式不相容。 這表示這兩個應用程式都必須使用 NuGet 套件 **2.x 版。**

藉由建立自訂的全像遠端播放程式應用程式，您可以建立自訂應用程式，以便在 HoloLens 2 上的遠端電腦上顯示 [沉浸式視圖](../../design/app-views.md) 。 此頁面上的所有程式碼和工作專案都可在「全像 [遠端範例」 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。

全像遠端播放機可讓您的應用程式顯示桌上型電腦或 UWP [裝置上轉譯的全](rendering.md) 像 Xbox One，並可存取更多系統資源。 全像遠端播放機應用程式會將輸入資料串流至全像的遠端處理遠端應用程式，並將沉浸式觀賞視為影片和音訊串流。 連接是使用標準 Wi-fi 進行的。 若要建立播放程式應用程式，請使用 NuGet 套件將全像是在 UWP 應用程式中新增全像的遠端處理。 然後撰寫程式碼來處理連接，並顯示沉浸式視圖。 

## <a name="prerequisites"></a>Prerequisites

良好的起點是已以 Windows Mixed Reality API 為目標的可運作 DirectX 型 UWP 應用程式。 如需詳細資訊，請參閱 [DirectX 開發總覽](../native/directx-development-overview.md)。 如果您沒有現有的應用程式，而且想要從頭開始，則 [c + +](../native/creating-a-holographic-directx-project.md) 全像的專案範本是不錯的起點。

>[!IMPORTANT]
>使用「全像」遠端處理的任何應用程式都應該撰寫為使用 [多執行緒的單元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。 支援使用 [單一執行緒的單元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) ，但會導致效能不佳，而且可能會在播放期間間斷情形。 使用 c + +/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 多執行緒的單元是預設值。

## <a name="get-the-holographic-remoting-nuget-package"></a>取得全像 Remoting NuGet 套件

若要將 NuGet 套件新增至 Visual Studio 中的專案，必須執行下列步驟。
1. 在 Visual Studio 中開啟專案。
2. 以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 套件 ...** ]
3. 在出現的面板中，選取 **[流覽]** ，然後搜尋「全像的遠端處理」。
4. 選取 [ **Microsoft**]，並確定 **挑選最新** 的2.x 版，然後選取 [ **安裝**]。
5. 如果出現 [ **預覽** ] 對話方塊，請選取 **[確定]**。
6. 當 [授權合約] 對話方塊出現時，選取 [ **我接受** ]。

>[!IMPORTANT]
><a name="idl"></a>NuGet 套件內的包含適用于全像全像攝影的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` API 的詳細檔。

## <a name="modify-the-packageappxmanifest-of-the-application"></a>修改應用程式的 package.appxmanifest

若要讓應用程式知道 NuGet 套件所新增的 Microsoft.Holographic.AppRemoting.dll，必須在專案上採取下列步驟：

1. 在 [方案總管以滑鼠右鍵按一下 **package.appxmanifest** 檔案，然後選取 [**開啟方式**...]。
2. 選取 **XML (文字) 編輯器** ，然後選取 **[確定]**
3. 將下列幾行新增至檔案，並儲存
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>建立播放機內容

在第一個步驟中，應用程式應該建立播放機內容。

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>全像是以遠端處理特定執行時間取代 Windows 一部分的 Windows Mixed Reality 執行時間，來進行全像的遠端處理工作。 這是在建立播放程式內容期間完成的。 因此，在建立播放程式內容之前，對任何 Windows Mixed Reality API 進行的任何呼叫都會導致非預期的行為。 建議的方法是在與任何混合現實 API 互動之前儘早建立播放機內容。 在使用之前建立或抓取的物件來呼叫之前，絕對不會透過任何 Windows Mixed Reality API 來混合建立或抓取的物件 ```PlayerContext::Create``` 。

接著，您可以藉由呼叫 [HolographicSpace CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)來建立 HolographicSpace。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>連接至遠端應用程式

一旦播放程式應用程式準備好可轉譯內容，就可以建立遠端應用程式的連接。

您可以透過下列其中一種方式來建立連接：
1) 在 HoloLens 2 上執行的播放程式應用程式會連接到遠端應用程式。
2) 遠端應用程式會連接到在 HoloLens 2 上執行的播放機應用程式。

若要從播放程式應用程式連接至遠端應用程式，請 ```Connect``` 在指定主機名稱和埠的播放程式內容上呼叫方法。 預設通訊埠為 **8265**。

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>如同任何 c + +/WinRT API， ```Connect``` 可能會擲回需要處理的 WinRT：： hresult_error。

您可以藉由呼叫方法來接聽播放程式應用程式上的連入連線 ```Listen``` 。 交握埠和傳輸埠都可以在此呼叫期間指定。 交握埠用於初始交握。 然後，資料會透過傳輸埠來傳送。 預設會使用通訊埠編號 **8265** 和 **8266** 。

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>處理連接相關事件

會 ```PlayerContext``` 公開三個事件來監視連接的狀態
1) OnConnected：已成功建立遠端應用程式的連線時觸發。
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected：如果已建立的連接終止或無法建立連線，就會觸發。
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>可能 ```ConnectionFailureReason``` 的值記載于檔案 ```Microsoft.Holographic.AppRemoting.idl``` [](#idl)中。

3) OnListening：接聽連入連線開始時。
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

此外，您也可以使用 player 內容上的屬性來查詢連接狀態 ```ConnectionState``` 。
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>顯示遠端呈現的框架

若要顯示遠端呈現的內容，請 ```PlayerContext::BlitRemoteFrame``` 在呈現 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)時呼叫。 

```BlitRemoteFrame``` 要求目前 HolographicFrame 的背景緩衝區必須系結為轉譯目標。 您可以透過[Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)屬性從[HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)接收背景緩衝區。

呼叫時，會 ```BlitRemoteFrame``` 從遠端應用程式將接收到的最新框架複製到 HolographicFrame 的背景緩衝區中。 此外，如果遠端應用程式在呈現遠端框架期間已指定焦點點，則會設定焦點點集合。

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` 可能會覆寫目前框架的焦點點。 
>- 若要指定回溯焦點點，請先呼叫 [HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` 。 
>- 若要覆寫遠端焦點點，請在之後呼叫 [HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` 。

成功時， ```BlitRemoteFrame``` 傳回 ```BlitResult::Success_Color``` 。 否則，它會傳回失敗原因：
- ```BlitResult::Failed_NoRemoteFrameAvailable```：因為沒有可用的遠端框架，所以失敗。
- ```BlitResult::Failed_NoCamera```：因為沒有相機存在而失敗。
- ```BlitResult::Failed_RemoteFrameTooOld```：因為遠端框架太舊而失敗 (請參閱 PlayerCoNtext：： BlitRemoteFrameTimeout 屬性) 。

>[!IMPORTANT]
> 從版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 開始，自訂播放程式就可以透過全像遠端處理來使用深度 reprojection。

```BlitResult``` 也可以 ```BlitResult::Success_Color_Depth``` 在下列情況下傳回：

- 遠端應用程式已透過 HolographicCameraRenderingParameters 認可深度緩衝區 [。 CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。
- 自訂播放程式應用程式在呼叫之前已系結有效的深度緩衝區 ```BlitRemoteFrame``` 。

如果符合這些條件，則 ```BlitRemoteFrame``` 會將遠端深度 array.blit 至目前系結的本機深度緩衝區。 然後，您可以轉譯其他本機內容，這會與遠端轉譯的內容有深度交集。 此外，您也可以在自訂播放程式中透過 [HolographicCameraRenderingParameters CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 本機深度緩衝區，以取得遠端和本機呈現內容的深度 reprojection。 如需詳細資訊，請參閱 [深度 Reprojection](hologram-stability.md#reprojection) 。

### <a name="projection-transform-mode"></a>投射轉換模式

其中一個問題是，透過全像 reprojection 使用深度時所呈現的問題，就是可以使用與自訂播放機應用程式直接轉譯的本機內容不同的投影轉換來轉譯遠端內容。 常見的使用案例是在播放程式端和遠端端透過 [HolographicCamera：： SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) 和 [HolographicCamera：： SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) 指定不同的接近平面的值 (。 在此情況下，如果播放程式端的投射轉換應該反映遠端近/遠的平面距離或區域，則不會很清楚。

從版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 開始，您可以透過來控制投影轉換模式 ```PlayerContext::ProjectionTransformConfig``` 。 支援的值為：

- ```Local``` - [HolographicCameraPose：:P rojectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) 會傳回投影轉換，以反映您的自訂播放程式在 HolographicCamera 上所設定的近/遠平面距離。
- ```Remote``` -投射轉換會反映遠端應用程式所指定的近/遠平面距離。
- ```Merged``` -與遠端應用程式和自訂播放程式應用程式合併的近/遠平面距離。 根據預設，這是藉由最少接近平面距離和最大平面距離來完成。 如果遠端或本機端是反向的 < 接近，則會翻轉遠端近/遠的平面距離。

## <a name="optional-set-blitremoteframetimeout"></a>選擇性：設定 BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` 從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。 

```PlayerContext::BlitRemoteFrameTimeout```如果未收到新的遠端框架，屬性會指定重複使用遠端畫面格的時間量。 

常見的使用案例是讓 BlitRemoteFrame timeout 在一段時間內沒有收到新的框架時，顯示空白畫面。 啟用時，方法的傳回型別 ```BlitRemoteFrame``` 也可以用來切換至本機呈現的回送內容。 

若要啟用超時，請將屬性值設定為等於或大於100毫秒的持續時間。 若要停用超時，請將屬性設定為零的持續時間。 如果已啟用 timeout，且未在設定的期間內收到任何遠端框架，則 BlitRemoteFrame 將會失敗並傳回， ```Failed_RemoteFrameTooOld``` 直到收到新的遠端畫面格為止。

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>選用：取得與最後一個遠端框架相關的統計資料

若要診斷效能或網路問題，可以透過屬性抓取最後一個遠端框架的相關統計資料 ```PlayerContext::LastFrameStatistics``` 。 在呼叫 HolographicFrame 時，會更新統計資料 [：:P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)。

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

如需詳細資訊，請參閱檔案 ```PlayerFrameStatistics``` 中的 ```Microsoft.Holographic.AppRemoting.idl``` [檔](#idl)。

## <a name="optional-custom-data-channels"></a>選用：自訂資料通道

自訂資料通道可以用來透過已建立的遠端連線來傳送使用者資料。 如需詳細資訊，請參閱 [自訂資料通道](holographic-remoting-custom-data-channels.md) 。

## <a name="see-also"></a>另請參閱
* [使用 Windows Mixed Reality Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-openxr.md)
* [自訂全像攝影遠端資料通道](holographic-remoting-custom-data-channels.md)
* [建立全像攝影遠端處理的連線安全](holographic-remoting-secure-connection.md)
* [全像遠端的疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
