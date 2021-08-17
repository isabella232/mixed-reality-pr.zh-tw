---
title: " (WMR) 撰寫全像遠端遠端應用程式"
description: 瞭解如何將遠端電腦上轉譯的遠端內容串流至使用 HolographicSpace 的全像遠端應用程式 HoloLens 2。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、遠端、全像全像遠端、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、NuGet
ms.openlocfilehash: 0c5943ff92ce797e39ec0d2d98c129fa91eb3f14
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184719"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>使用 HolographicSpace API 撰寫全像遠端執行遠端應用程式

>[!IMPORTANT]
>本檔說明如何使用[HolographicSpace API](../native/getting-a-holographicspace.md)建立 HoloLens 2 的遠端應用程式。 **HoloLens (第1代)** 的遠端應用程式必須使用 NuGet 套件1.x 版。 這表示針對 HoloLens 2 撰寫的遠端應用程式與 HoloLens 1 不相容，反之亦然。 您可以在[這裡](add-holographic-remoting.md)找到 HoloLens 1 的檔。

全像的遠端處理應用程式可以將遠端轉譯的內容串流至 HoloLens 2 並 Windows Mixed Reality 沉浸式耳機。 您也可以存取更多的系統資源，並將遠端 [沉浸式觀點](../../design/app-views.md) 整合到現有的桌上型電腦軟體。 遠端應用程式會從 HoloLens 2 接收輸入資料流程、在虛擬沉浸式視圖中轉譯內容，並將內容框架串流回 HoloLens 2。 連接是使用標準 Wi-fi 進行的。 在桌面或 UWP 應用程式中，透過 NuGet 封包新增了全像的遠端處理功能。 需要額外的程式碼，以處理連接並以沉浸式視圖呈現。 一般的遠端連線的延遲將會降到50毫秒。 播放程式應用程式可以即時報告延遲時間。

此頁面上的所有程式碼和工作專案都可在「全像 [遠端範例」 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。

## <a name="prerequisites"></a>必要條件

良好的起點是以 [HOLOGRAPHICSPACE API](../native/getting-a-holographicspace.md)為目標的可運作 DirectX 型桌面或 UWP 應用程式。 如需詳細資訊，請參閱 [DirectX 開發總覽](../native/directx-development-overview.md)。 [C + + 全息版專案範本](../native/creating-a-holographic-directx-project.md)是不錯的起點。

>[!IMPORTANT]
>使用「全像」遠端處理的任何應用程式都應該撰寫為使用 [多執行緒的單元](/windows/win32/com/multithreaded-apartments)。 支援使用 [單一執行緒的單元](/windows/win32/com/single-threaded-apartments) ，但會導致效能不佳，而且可能會在播放期間間斷情形。 使用 c + +/WinRT [WinRT：： init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 多執行緒的單元是預設值。



## <a name="get-the-holographic-remoting-nuget-package"></a>取得全像 NuGet 套件的全像遠端

若要將 NuGet 套件新增至 Visual Studio 中的專案，必須執行下列步驟。
1. 在 Visual Studio 中開啟專案。
2. 以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 封裝**.。。
3. 在出現的面板中，選取 **[流覽]** ，然後搜尋「全像的遠端處理」。
4. 選取 [ **Microsoft**]，並確定 **挑選最新** 的2.x 版，然後選取 [ **安裝**]。
5. 如果出現 [ **預覽** ] 對話方塊，請選取 **[確定]**。
6. 當 [授權合約] 對話方塊出現時，選取 [ **我接受** ]。

>[!NOTE]
>NuGet 套件的 **1.x 版仍** 適用于想要以 HoloLens 1 為目標的開發人員。 如需詳細資訊，請參閱[HoloLens (第一代) ) 新增全像遠端 (](add-holographic-remoting.md)。

## <a name="create-the-remote-context"></a>建立遠端內容

在第一個步驟中，應用程式應該建立遠端內容。

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>全像是以遠端處理特定執行時間取代 Windows 一部分的 Windows Mixed Reality 執行時間，來進行全像的遠端處理工作。 這是在建立遠端內容期間完成的。 基於這個理由，在建立遠端內容之前，對任何 Windows Mixed Reality API 進行的任何呼叫都會導致非預期的行為。 建議的方法是在與任何混合現實 API 互動之前儘早建立遠端內容。 使用之後建立或抓取的物件來呼叫 CreateRemoteCoNtext 之前，絕對不要混合透過任何 Windows Mixed Reality API 建立或取出的物件。

接下來必須建立全像空間。 不需要指定 CoreWindow。 沒有 CoreWindow 的桌面應用程式可以直接傳遞 ```nullptr``` 。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>連線至裝置

當遠端應用程式準備好轉譯內容時，可建立與播放機裝置的連線。

您可以透過下列兩種方式之一來完成連接。
1) 遠端應用程式會連接到在裝置上執行的播放程式。
2) 在裝置上執行的播放程式會連接到遠端應用程式。

若要建立從遠端應用程式到 player 裝置的連線，請 ```Connect``` 在遠端內容上呼叫方法來指定主機名稱和埠。 全像遠端播放機使用的埠是 **8265**。

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>如同任何 c + +/WinRT API， ```Connect``` 可能會擲回需要處理的 WinRT：： hresult_error。

>[!TIP]
>若要避免使用[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/)語言投射， ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` 可以包含位於全像「遠端 NuGet 套件內的檔案。 它包含基礎 COM 介面的宣告。 不過，我們建議使用 c + +/WinRT。

您可以藉由呼叫方法來接聽遠端應用程式上的連入連線 ```Listen``` 。 交握埠和傳輸埠都可以在此呼叫期間指定。 交握埠用於初始交握。 然後，資料會透過傳輸埠來傳送。 預設會使用 **8265** 和 **8266** 。

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>NuGet 套件內的會包含由全像全像的應用 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 程式所公開之 API 的詳細檔。

## <a name="handling-remoting-specific-events"></a>處理遠端處理特定事件

遠端內容會公開三個事件，這對監視連接的狀態非常重要。
1) OnConnected：已成功建立裝置的連線時觸發。
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected：如果建立的連接已關閉或無法建立連接，則會觸發。
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) OnListening：接聽連入連線開始時。
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

此外，您也可以使用遠端內容上的屬性來查詢連接狀態 ```ConnectionState``` 。
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>處理語音事件

您可以使用遠端語音介面，向 HoloLens 2 註冊語音觸發程式，並讓它們遠端處理遠端應用程式。

需要此額外成員才能追蹤遠端語音的狀態。

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

首先，必須抓取遠端語音介面。

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

您可以使用非同步協助程式方法來初始化遠端語音。 這應該會以非同步方式完成，因為初始化可能需要相當長的時間。 [使用 c + +/WinRT 的並行和非同步作業](/windows/uwp/cpp-and-winrt-apis/concurrency) 說明如何使用 c + +/winrt 撰寫非同步函式

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

有兩種方式可以指定要辨識的片語。
1) 語音文法 xml 檔案內的規格。 如需詳細資料，請參閱 [如何建立基本的 XML 文法](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 。
2) 藉由將字典向量內的傳遞給來指定 ```ApplyParameters``` 。

在 OnRecognizedSpeech 回呼中，可以處理語音事件：

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>在本機預覽資料流程內容

若要在傳送至裝置的遠端應用程式中顯示相同的內容， ```OnSendFrame``` 可以使用遠端內容的事件。 每次全像全像遠端連結 ```OnSendFrame``` 庫將目前的框架傳送到遠端裝置時，就會觸發此事件。 這是取得內容，並將它 array.blit 到桌面或 UWP 視窗的理想時間。

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a>深度 Reprojection

從版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0)開始，全像攝影遠端支援 [深度 Reprojection](hologram-stability.md#reprojection)。 這需要從遠端應用程式將色彩緩衝區和深度緩衝區串流至 HoloLens 2。 預設會啟用深度緩衝區串流，並將其設定為使用色彩緩衝區的一半解析度。 這可以變更如下：

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

請注意，如果不應該使用預設值，就 ```ConfigureDepthVideoStream``` 必須在建立 HoloLens 2 的連接之前呼叫。 最好的地方就是建立遠端內容。 DepthBufferStreamResolution 的可能值為：

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* 停用的 (在 [2.1.3](holographic-remoting-version-history.md#v2.1.3) 版本中新增，如果未使用，則會建立其他深度的影片串流) 

請記住，使用完整的解析度深度緩衝區也會影響頻寬需求，而且需要在您提供的最大頻寬值中加以考慮 ```CreateRemoteContext``` 。

除了設定解決方案之外，您也必須透過 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)認可深度緩衝區。

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

若要確認深度 reprojection 是否可在 HoloLens 2 上正確運作，您可以透過裝置入口網站啟用深度視覺化檢視。 如需詳細資料，請參閱 [驗證深度設定是否正確](hologram-stability.md#verifying-depth-is-set-correctly) 。

## <a name="optional-custom-data-channels"></a>選用：自訂資料通道

自訂資料通道可以用來透過已建立的遠端連線來傳送使用者資料。 如需詳細資訊，請參閱 [自訂資料通道](holographic-remoting-custom-data-channels.md) 。

## <a name="see-also"></a>另請參閱
* [全像遠端處理總覽](holographic-remoting-overview.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [自訂全像攝影遠端資料通道](holographic-remoting-custom-data-channels.md)
* [建立全像攝影遠端處理的連線安全](holographic-remoting-secure-connection.md)
* [全像遠端的疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)