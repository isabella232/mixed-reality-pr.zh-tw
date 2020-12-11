---
title: 撰寫自訂全像攝影遠端播放程式
description: 藉由建立自訂的全像遠端播放程式應用程式，您可以建立自訂應用程式，以顯示在遠端電腦上轉譯的內容到您的 HoloLens 2。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、遠端、全像全像 Remoting、NuGet、應用程式資訊清單、播放機內容、遠端應用程式、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: ac3ee68cf3cff3e024ce40acceac61a2fe123399
ms.sourcegitcommit: 99ae85159b7cf75f919021771ebb8299868beea9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97102893"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="852a4-104">撰寫自訂全像攝影遠端播放應用程式</span><span class="sxs-lookup"><span data-stu-id="852a4-104">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="852a4-105">本檔說明如何建立 HoloLens 2 的自訂播放程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="852a4-105">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="852a4-106">針對 HoloLens 2 撰寫的自訂播放程式與針對 HoloLens 1 所撰寫的遠端應用程式不相容。</span><span class="sxs-lookup"><span data-stu-id="852a4-106">Custom players written for HoloLens 2 are not compatible with remote applications written for HoloLens 1.</span></span> <span data-ttu-id="852a4-107">這表示這兩個應用程式都必須使用 NuGet 套件 **2.x 版。**</span><span class="sxs-lookup"><span data-stu-id="852a4-107">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="852a4-108">藉由建立自訂的全像遠端播放程式應用程式，您可以建立自訂應用程式，以便在 HoloLens 2 上的遠端電腦上顯示 [沉浸式視圖](../../design/app-views.md) 。</span><span class="sxs-lookup"><span data-stu-id="852a4-108">By creating a custom Holographic Remoting player app, you can create a custom application capable of displaying [immersive views](../../design/app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="852a4-109">此頁面上的所有程式碼和工作專案都可在「全像 [遠端範例」 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。</span><span class="sxs-lookup"><span data-stu-id="852a4-109">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="852a4-110">全像遠端播放機可讓您的應用程式顯示桌上型電腦或 UWP [裝置上轉譯的全](rendering.md) 像 Xbox One，並可存取更多系統資源。</span><span class="sxs-lookup"><span data-stu-id="852a4-110">A Holographic Remoting player lets your app display holographic content [rendered](rendering.md) on a desktop PC or UWP device like the Xbox One with access to more system resources.</span></span> <span data-ttu-id="852a4-111">全像遠端播放機應用程式會將輸入資料串流至全像的遠端處理遠端應用程式，並將沉浸式觀賞視為影片和音訊串流。</span><span class="sxs-lookup"><span data-stu-id="852a4-111">A Holographic Remoting player app streams input data to a Holographic Remoting remote application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="852a4-112">連接是使用標準 Wi-fi 進行的。</span><span class="sxs-lookup"><span data-stu-id="852a4-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="852a4-113">若要建立播放程式應用程式，請使用 NuGet 套件將全像是在 UWP 應用程式中新增全像的遠端處理。</span><span class="sxs-lookup"><span data-stu-id="852a4-113">To create a player app, use a NuGet package to add Holographic Remoting to your UWP app.</span></span> <span data-ttu-id="852a4-114">然後撰寫程式碼來處理連接，並顯示沉浸式視圖。</span><span class="sxs-lookup"><span data-stu-id="852a4-114">Then write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="852a4-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="852a4-115">Prerequisites</span></span>

<span data-ttu-id="852a4-116">良好的起點是已以 Windows Mixed Reality API 為目標的可運作 DirectX 型 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="852a4-116">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="852a4-117">如需詳細資訊，請參閱 [DirectX 開發總覽](../native/directx-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="852a4-117">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="852a4-118">如果您沒有現有的應用程式，而且想要從頭開始，則 [c + +](../native/creating-a-holographic-directx-project.md) 全像的專案範本是不錯的起點。</span><span class="sxs-lookup"><span data-stu-id="852a4-118">If you don't have an existing app and want to start from scratch the [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="852a4-119">使用「全像」遠端處理的任何應用程式都應該撰寫為使用 [多執行緒的單元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="852a4-119">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="852a4-120">支援使用 [單一執行緒的單元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) ，但會導致效能不佳，而且可能會在播放期間間斷情形。</span><span class="sxs-lookup"><span data-stu-id="852a4-120">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="852a4-121">使用 c + +/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 多執行緒的單元是預設值。</span><span class="sxs-lookup"><span data-stu-id="852a4-121">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="852a4-122">取得全像 Remoting NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="852a4-122">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="852a4-123">若要將 NuGet 套件新增至 Visual Studio 中的專案，必須執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="852a4-123">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="852a4-124">在 Visual Studio 中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="852a4-124">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="852a4-125">以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 套件 ...** ]</span><span class="sxs-lookup"><span data-stu-id="852a4-125">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="852a4-126">在出現的面板中，選取 **[流覽]** ，然後搜尋「全像的遠端處理」。</span><span class="sxs-lookup"><span data-stu-id="852a4-126">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="852a4-127">選取 [ **Microsoft**]，並確定 **挑選最新** 的2.x 版，然後選取 [ **安裝**]。</span><span class="sxs-lookup"><span data-stu-id="852a4-127">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="852a4-128">如果出現 [ **預覽** ] 對話方塊，請選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="852a4-128">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="852a4-129">當 [授權合約] 對話方塊出現時，選取 [ **我接受** ]。</span><span class="sxs-lookup"><span data-stu-id="852a4-129">Select **I Accept** when the license agreement dialog appears.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="852a4-130">NuGet 套件內的包含適用于全像全像攝影的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` API 的詳細檔。</span><span class="sxs-lookup"><span data-stu-id="852a4-130">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="852a4-131">修改應用程式的 package.appxmanifest</span><span class="sxs-lookup"><span data-stu-id="852a4-131">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="852a4-132">若要讓應用程式知道 NuGet 套件所新增的 Microsoft.Holographic.AppRemoting.dll，必須在專案上採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="852a4-132">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="852a4-133">在 [方案總管以滑鼠右鍵按一下 **package.appxmanifest** 檔案，然後選取 [**開啟方式**...]。</span><span class="sxs-lookup"><span data-stu-id="852a4-133">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="852a4-134">選取 **XML (文字) 編輯器** ，然後選取 **[確定]**</span><span class="sxs-lookup"><span data-stu-id="852a4-134">Select **XML (Text) Editor** and select **OK**</span></span>
3. <span data-ttu-id="852a4-135">將下列幾行新增至檔案，並儲存</span><span class="sxs-lookup"><span data-stu-id="852a4-135">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="852a4-136">建立播放機內容</span><span class="sxs-lookup"><span data-stu-id="852a4-136">Create the player context</span></span>

<span data-ttu-id="852a4-137">在第一個步驟中，應用程式應該建立播放機內容。</span><span class="sxs-lookup"><span data-stu-id="852a4-137">As a first step the application should create a player context.</span></span>

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
><span data-ttu-id="852a4-138">全像是以遠端處理特定執行時間取代 Windows 一部分的 Windows Mixed Reality 執行時間，來進行全像的遠端處理工作。</span><span class="sxs-lookup"><span data-stu-id="852a4-138">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="852a4-139">這是在建立播放程式內容期間完成的。</span><span class="sxs-lookup"><span data-stu-id="852a4-139">This is done during the creation of the player context.</span></span> <span data-ttu-id="852a4-140">因此，在建立播放程式內容之前，對任何 Windows Mixed Reality API 進行的任何呼叫都會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="852a4-140">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="852a4-141">建議的方法是在與任何混合現實 API 互動之前儘早建立播放機內容。</span><span class="sxs-lookup"><span data-stu-id="852a4-141">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="852a4-142">在使用之前建立或抓取的物件來呼叫之前，絕對不會透過任何 Windows Mixed Reality API 來混合建立或抓取的物件 ```PlayerContext::Create``` 。</span><span class="sxs-lookup"><span data-stu-id="852a4-142">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="852a4-143">接著，您可以藉由呼叫 [HolographicSpace CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)來建立 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="852a4-143">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a><span data-ttu-id="852a4-144">連接至遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="852a4-144">Connect to the remote app</span></span>

<span data-ttu-id="852a4-145">一旦播放程式應用程式準備好可轉譯內容，就可以建立遠端應用程式的連接。</span><span class="sxs-lookup"><span data-stu-id="852a4-145">Once the player app is ready for rendering content a connection to the remote app can be established.</span></span>

<span data-ttu-id="852a4-146">您可以透過下列其中一種方式來建立連接：</span><span class="sxs-lookup"><span data-stu-id="852a4-146">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="852a4-147">在 HoloLens 2 上執行的播放程式應用程式會連接到遠端應用程式。</span><span class="sxs-lookup"><span data-stu-id="852a4-147">The player app running on HoloLens 2 connects to the remote app.</span></span>
2) <span data-ttu-id="852a4-148">遠端應用程式會連接到在 HoloLens 2 上執行的播放機應用程式。</span><span class="sxs-lookup"><span data-stu-id="852a4-148">The remote app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="852a4-149">若要從播放程式應用程式連接至遠端應用程式，請 ```Connect``` 在指定主機名稱和埠的播放程式內容上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="852a4-149">To connect from the player app to the remote app call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="852a4-150">預設通訊埠為 **8265**。</span><span class="sxs-lookup"><span data-stu-id="852a4-150">The default port is **8265**.</span></span>

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
><span data-ttu-id="852a4-151">如同任何 c + +/WinRT API， ```Connect``` 可能會擲回需要處理的 WinRT：： hresult_error。</span><span class="sxs-lookup"><span data-stu-id="852a4-151">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="852a4-152">您可以藉由呼叫方法來接聽播放程式應用程式上的連入連線 ```Listen``` 。</span><span class="sxs-lookup"><span data-stu-id="852a4-152">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="852a4-153">交握埠和傳輸埠都可以在此呼叫期間指定。</span><span class="sxs-lookup"><span data-stu-id="852a4-153">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="852a4-154">交握埠用於初始交握。</span><span class="sxs-lookup"><span data-stu-id="852a4-154">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="852a4-155">然後，資料會透過傳輸埠來傳送。</span><span class="sxs-lookup"><span data-stu-id="852a4-155">The data is then sent over the transport port.</span></span> <span data-ttu-id="852a4-156">預設會使用通訊埠編號 **8265** 和 **8266** 。</span><span class="sxs-lookup"><span data-stu-id="852a4-156">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="852a4-157">處理連接相關事件</span><span class="sxs-lookup"><span data-stu-id="852a4-157">Handling connection-related events</span></span>

<span data-ttu-id="852a4-158">會 ```PlayerContext``` 公開三個事件來監視連接的狀態</span><span class="sxs-lookup"><span data-stu-id="852a4-158">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="852a4-159">OnConnected：已成功建立遠端應用程式的連線時觸發。</span><span class="sxs-lookup"><span data-stu-id="852a4-159">OnConnected: Triggered when a connection to the remote app has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="852a4-160">OnDisconnected：如果已建立的連接終止或無法建立連線，就會觸發。</span><span class="sxs-lookup"><span data-stu-id="852a4-160">OnDisconnected: Triggered if an established connection is terminated or a connection couldn't be established.</span></span>
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
><span data-ttu-id="852a4-161">可能 ```ConnectionFailureReason``` 的值記載于檔案 ```Microsoft.Holographic.AppRemoting.idl``` [](#idl)中。</span><span class="sxs-lookup"><span data-stu-id="852a4-161">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="852a4-162">OnListening：接聽連入連線開始時。</span><span class="sxs-lookup"><span data-stu-id="852a4-162">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="852a4-163">此外，您也可以使用 player 內容上的屬性來查詢連接狀態 ```ConnectionState``` 。</span><span class="sxs-lookup"><span data-stu-id="852a4-163">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="852a4-164">顯示遠端呈現的框架</span><span class="sxs-lookup"><span data-stu-id="852a4-164">Display the remotely rendered frame</span></span>

<span data-ttu-id="852a4-165">若要顯示遠端呈現的內容，請 ```PlayerContext::BlitRemoteFrame``` 在呈現 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)時呼叫。</span><span class="sxs-lookup"><span data-stu-id="852a4-165">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="852a4-166">```BlitRemoteFrame``` 要求目前 HolographicFrame 的背景緩衝區必須系結為轉譯目標。</span><span class="sxs-lookup"><span data-stu-id="852a4-166">```BlitRemoteFrame``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="852a4-167">您可以透過[Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)屬性從[HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)接收背景緩衝區。</span><span class="sxs-lookup"><span data-stu-id="852a4-167">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="852a4-168">呼叫時，會 ```BlitRemoteFrame``` 從遠端應用程式將接收到的最新框架複製到 HolographicFrame 的背景緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="852a4-168">When called, ```BlitRemoteFrame``` copies the latest received frame from the remote application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="852a4-169">此外，如果遠端應用程式在呈現遠端框架期間已指定焦點點，則會設定焦點點集合。</span><span class="sxs-lookup"><span data-stu-id="852a4-169">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="852a4-170">```PlayerContext::BlitRemoteFrame``` 可能會覆寫目前框架的焦點點。</span><span class="sxs-lookup"><span data-stu-id="852a4-170">```PlayerContext::BlitRemoteFrame``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="852a4-171">若要指定回溯焦點點，請先呼叫 [HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` 。</span><span class="sxs-lookup"><span data-stu-id="852a4-171">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame```.</span></span> 
>- <span data-ttu-id="852a4-172">若要覆寫遠端焦點點，請在之後呼叫 [HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` 。</span><span class="sxs-lookup"><span data-stu-id="852a4-172">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame```.</span></span>

<span data-ttu-id="852a4-173">成功時， ```BlitRemoteFrame``` 傳回 ```BlitResult::Success_Color``` 。</span><span class="sxs-lookup"><span data-stu-id="852a4-173">On success, ```BlitRemoteFrame``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="852a4-174">否則，它會傳回失敗原因：</span><span class="sxs-lookup"><span data-stu-id="852a4-174">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="852a4-175">```BlitResult::Failed_NoRemoteFrameAvailable```：因為沒有可用的遠端框架，所以失敗。</span><span class="sxs-lookup"><span data-stu-id="852a4-175">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="852a4-176">```BlitResult::Failed_NoCamera```：因為沒有相機存在而失敗。</span><span class="sxs-lookup"><span data-stu-id="852a4-176">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="852a4-177">```BlitResult::Failed_RemoteFrameTooOld```：因為遠端框架太舊而失敗 (請參閱 PlayerCoNtext：： BlitRemoteFrameTimeout 屬性) 。</span><span class="sxs-lookup"><span data-stu-id="852a4-177">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

>[!IMPORTANT]
> <span data-ttu-id="852a4-178">從版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 開始，自訂播放程式就可以透過全像遠端處理來使用深度 reprojection。</span><span class="sxs-lookup"><span data-stu-id="852a4-178">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) it is possible with a custom player to use depth reprojection via Holographic Remoting.</span></span>

<span data-ttu-id="852a4-179">```BlitResult``` 也可以 ```BlitResult::Success_Color_Depth``` 在下列情況下傳回：</span><span class="sxs-lookup"><span data-stu-id="852a4-179">```BlitResult``` can also return ```BlitResult::Success_Color_Depth``` under the following conditions:</span></span>

- <span data-ttu-id="852a4-180">遠端應用程式已透過 HolographicCameraRenderingParameters 認可深度緩衝區 [。 CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。</span><span class="sxs-lookup"><span data-stu-id="852a4-180">The remote app has committed a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>
- <span data-ttu-id="852a4-181">自訂播放程式應用程式在呼叫之前已系結有效的深度緩衝區 ```BlitRemoteFrame``` 。</span><span class="sxs-lookup"><span data-stu-id="852a4-181">The custom player app has bound a valid depth buffer before calling ```BlitRemoteFrame```.</span></span>

<span data-ttu-id="852a4-182">如果符合這些條件，則 ```BlitRemoteFrame``` 會將遠端深度 array.blit 至目前系結的本機深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="852a4-182">If these conditions are met ```BlitRemoteFrame``` will blit the remote depth into the currently bound local depth buffer.</span></span> <span data-ttu-id="852a4-183">然後，您可以轉譯其他本機內容，這會與遠端轉譯的內容有深度交集。</span><span class="sxs-lookup"><span data-stu-id="852a4-183">You can then render additional local content, which will have depth intersection with the remote rendered content.</span></span> <span data-ttu-id="852a4-184">此外，您也可以在自訂播放程式中透過 [HolographicCameraRenderingParameters CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 本機深度緩衝區，以取得遠端和本機呈現內容的深度 reprojection。</span><span class="sxs-lookup"><span data-stu-id="852a4-184">Additionally you can commit the local depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in your custom player to have depth reprojection for remote and local rendered content.</span></span> <span data-ttu-id="852a4-185">如需詳細資訊，請參閱 [深度 Reprojection](hologram-stability.md#reprojection) 。</span><span class="sxs-lookup"><span data-stu-id="852a4-185">See [Depth Reprojection](hologram-stability.md#reprojection) for details.</span></span>

### <a name="projection-transform-mode"></a><span data-ttu-id="852a4-186">投射轉換模式</span><span class="sxs-lookup"><span data-stu-id="852a4-186">Projection Transform Mode</span></span>

<span data-ttu-id="852a4-187">其中一個問題是，透過全像 reprojection 使用深度時所呈現的問題，就是可以使用與自訂播放機應用程式直接轉譯的本機內容不同的投影轉換來轉譯遠端內容。</span><span class="sxs-lookup"><span data-stu-id="852a4-187">One problem, which surfaces when using depth reprojection via Holographic Remoting is that the remote content can be rendered with a different projection transform than local content directly rendered by your custom player app.</span></span> <span data-ttu-id="852a4-188">常見的使用案例是在播放程式端和遠端端透過 [HolographicCamera：： SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) 和 [HolographicCamera：： SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) 指定不同的接近平面的值 (。</span><span class="sxs-lookup"><span data-stu-id="852a4-188">A common use-case is to specify different values for near and far plane (via [HolographicCamera::SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) and [HolographicCamera::SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) on the player side and the remote side.</span></span> <span data-ttu-id="852a4-189">在此情況下，如果播放程式端的投射轉換應該反映遠端近/遠的平面距離或區域，則不會很清楚。</span><span class="sxs-lookup"><span data-stu-id="852a4-189">In this case, it's not clear if the projection transform on the player side should reflect the remote near/far plane distances or the local ones.</span></span>

<span data-ttu-id="852a4-190">從版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 開始，您可以透過來控制投影轉換模式 ```PlayerContext::ProjectionTransformConfig``` 。</span><span class="sxs-lookup"><span data-stu-id="852a4-190">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) you can control the projection transform mode via ```PlayerContext::ProjectionTransformConfig```.</span></span> <span data-ttu-id="852a4-191">支援的值為：</span><span class="sxs-lookup"><span data-stu-id="852a4-191">Supported values are:</span></span>

- <span data-ttu-id="852a4-192">```Local``` - [HolographicCameraPose：:P rojectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) 會傳回投影轉換，以反映您的自訂播放程式在 HolographicCamera 上所設定的近/遠平面距離。</span><span class="sxs-lookup"><span data-stu-id="852a4-192">```Local``` - [HolographicCameraPose::ProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) returns a projection transform, which reflects the near/far plane distances set by your custom player app on the HolographicCamera.</span></span>
- <span data-ttu-id="852a4-193">```Remote``` -投射轉換會反映遠端應用程式所指定的近/遠平面距離。</span><span class="sxs-lookup"><span data-stu-id="852a4-193">```Remote``` - Projection transform reflects the near/far plane distances specified by the remote app.</span></span>
- <span data-ttu-id="852a4-194">```Merged``` -與遠端應用程式和自訂播放程式應用程式合併的近/遠平面距離。</span><span class="sxs-lookup"><span data-stu-id="852a4-194">```Merged``` - Near/Far plane distances from your remote app and your custom player app are merged.</span></span> <span data-ttu-id="852a4-195">根據預設，這是藉由最少接近平面距離和最大平面距離來完成。</span><span class="sxs-lookup"><span data-stu-id="852a4-195">By default this is done by taking the minimum of the near plane distances and the maximum of the far plane distances.</span></span> <span data-ttu-id="852a4-196">如果遠端或本機端是反向的 < 接近，則會翻轉遠端近/遠的平面距離。</span><span class="sxs-lookup"><span data-stu-id="852a4-196">In case either the remote or local side are inverted, say far < near, the remote near/far plane distances are flipped.</span></span>

## <a name="optional-set-blitremoteframetimeout"></a><span data-ttu-id="852a4-197">選擇性：設定 BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="852a4-197">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="852a4-198">```PlayerContext::BlitRemoteFrameTimeout``` 從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。</span><span class="sxs-lookup"><span data-stu-id="852a4-198">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="852a4-199">```PlayerContext::BlitRemoteFrameTimeout```如果未收到新的遠端框架，屬性會指定重複使用遠端畫面格的時間量。</span><span class="sxs-lookup"><span data-stu-id="852a4-199">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="852a4-200">常見的使用案例是讓 BlitRemoteFrame timeout 在一段時間內沒有收到新的框架時，顯示空白畫面。</span><span class="sxs-lookup"><span data-stu-id="852a4-200">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="852a4-201">啟用時，方法的傳回型別 ```BlitRemoteFrame``` 也可以用來切換至本機呈現的回送內容。</span><span class="sxs-lookup"><span data-stu-id="852a4-201">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="852a4-202">若要啟用超時，請將屬性值設定為等於或大於100毫秒的持續時間。</span><span class="sxs-lookup"><span data-stu-id="852a4-202">To enable the timeout, set the property value to a duration equal or greater than 100 ms.</span></span> <span data-ttu-id="852a4-203">若要停用超時，請將屬性設定為零的持續時間。</span><span class="sxs-lookup"><span data-stu-id="852a4-203">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="852a4-204">如果已啟用 timeout，且未在設定的期間內收到任何遠端框架，則 BlitRemoteFrame 將會失敗並傳回， ```Failed_RemoteFrameTooOld``` 直到收到新的遠端畫面格為止。</span><span class="sxs-lookup"><span data-stu-id="852a4-204">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="852a4-205">選用：取得與最後一個遠端框架相關的統計資料</span><span class="sxs-lookup"><span data-stu-id="852a4-205">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="852a4-206">若要診斷效能或網路問題，可以透過屬性抓取最後一個遠端框架的相關統計資料 ```PlayerContext::LastFrameStatistics``` 。</span><span class="sxs-lookup"><span data-stu-id="852a4-206">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="852a4-207">在呼叫 HolographicFrame 時，會更新統計資料 [：:P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)。</span><span class="sxs-lookup"><span data-stu-id="852a4-207">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="852a4-208">如需詳細資訊，請參閱檔案 ```PlayerFrameStatistics``` 中的 ```Microsoft.Holographic.AppRemoting.idl``` [檔](#idl)。</span><span class="sxs-lookup"><span data-stu-id="852a4-208">For more information, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="852a4-209">選用：自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="852a4-209">Optional: Custom data channels</span></span>

<span data-ttu-id="852a4-210">自訂資料通道可以用來透過已建立的遠端連線來傳送使用者資料。</span><span class="sxs-lookup"><span data-stu-id="852a4-210">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="852a4-211">如需詳細資訊，請參閱 [自訂資料通道](holographic-remoting-custom-data-channels.md) 。</span><span class="sxs-lookup"><span data-stu-id="852a4-211">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="852a4-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="852a4-212">See Also</span></span>
* [<span data-ttu-id="852a4-213">使用 Windows Mixed Reality Api 撰寫全像遠端執行遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="852a4-213">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="852a4-214">使用 OpenXR Api 撰寫全像遠端執行遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="852a4-214">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="852a4-215">自訂全像攝影遠端資料通道</span><span class="sxs-lookup"><span data-stu-id="852a4-215">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="852a4-216">建立全像攝影遠端處理的連線安全</span><span class="sxs-lookup"><span data-stu-id="852a4-216">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="852a4-217">全像遠端的疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="852a4-217">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="852a4-218">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="852a4-218">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="852a4-219">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="852a4-219">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
