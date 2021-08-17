---
title: " (OpenXR) 撰寫全像遠端遠端應用程式"
description: 瞭解如何將遠端電腦上轉譯的遠端內容串流至使用 OpenXR 的全像遠端應用程式 HoloLens 2。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、遠端、全像全像遠端、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、NuGet
ms.openlocfilehash: 3fd210db1b179cbceff057e25bf451be0e7ca843
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184589"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>使用 OpenXR API 撰寫全像遠端執行遠端應用程式

>[!IMPORTANT]
>本檔說明如何使用[OpenXR API](../native/openxr.md)建立 HoloLens 2 和 Windows Mixed Reality 耳機的遠端應用程式。 **HoloLens (第1代)** 的遠端應用程式必須使用 NuGet 套件1.x 版。 這表示針對 HoloLens 2 撰寫的遠端應用程式與 HoloLens 1 不相容，反之亦然。 您可以在[這裡](add-holographic-remoting.md)找到 HoloLens 1 的檔。

全像的遠端處理應用程式可以將遠端轉譯的內容串流至 HoloLens 2 並 Windows Mixed Reality 沉浸式耳機。 您也可以存取更多的系統資源，並將遠端 [沉浸式觀點](../../design/app-views.md) 整合到現有的桌上型電腦軟體。 遠端應用程式會從 HoloLens 2 接收輸入資料流程、在虛擬沉浸式視圖中轉譯內容，並將內容框架串流回 HoloLens 2。 連接是使用標準 Wi-fi 進行的。 在桌面或 UWP 應用程式中，透過 NuGet 封包新增了全像的遠端處理功能。 需要額外的程式碼，以處理連接並以沉浸式視圖呈現。 一般的遠端連線的延遲將會降到50毫秒。 播放程式應用程式可以即時報告延遲時間。

此頁面上的所有程式碼和工作專案都可在「全像 [遠端範例」 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。

## <a name="prerequisites"></a>必要條件

良好的起點是可運作的 OpenXR 型桌面或 UWP 應用程式。 如需詳細資訊，請參閱 [OpenXR 入門](../native/openxr-getting-started.md)。

>[!IMPORTANT]
>使用「全像」遠端處理的任何應用程式都應該撰寫為使用 [多執行緒的單元](/windows/win32/com/multithreaded-apartments)。 支援使用 [單一執行緒的單元](/windows/win32/com/single-threaded-apartments) ，但會導致效能不佳，而且可能會在播放期間間斷情形。 使用 c + +/WinRT [WinRT：： init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 多執行緒的單元是預設值。

## <a name="get-the-holographic-remoting-nuget-package"></a>取得全像 NuGet 套件的全像遠端

若要將 NuGet 套件新增至 Visual Studio 中的專案，必須執行下列步驟。
1. 在 Visual Studio 中開啟專案。
2. 以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 封裝**.。。
3. 在出現的面板中，選取 **[流覽]** ，然後搜尋「全像的遠端處理」。
4. 選取 [ **OpenXr**]，並確定 **挑選最新** 的2.x 版，然後選取 [ **安裝**]。
5. 如果出現 [ **預覽** ] 對話方塊，請選取 **[確定]**。
6. 當 [授權合約] 對話方塊出現時，選取 [ **我接受** ]。
7. 針對下列 NuGet 套件重複步驟3到6： OpenXR. 標頭、OpenXR 載入器

>[!NOTE]
>NuGet 套件的 **1.x 版仍** 適用于想要以 HoloLens 1 為目標的開發人員。 如需詳細資訊，請參閱[HoloLens (第一代) ) 新增全像遠端 (](add-holographic-remoting.md)。

## <a name="select-the-holographic-remoting-openxr-runtime"></a>選取全像遠端 OpenXR 執行時間

您必須在遠端應用程式中執行的第一個步驟是選取全像 OpenXR NuGet 套件中的「全像遠端 OpenXR 執行時間」。 若要這麼做，您可以將 ```XR_RUNTIME_JSON``` 環境變數設定為應用程式內的 RemotingXR.js檔案路徑。 OpenXR 載入器會使用此環境變數，而不使用系統預設 OpenXR 執行時間，而是改為重新導向至全像「全像」遠端 OpenXR 執行時間。 使用 OpenXr NuGet 套件時，檔案上的 RemotingXR.js會在編譯至輸出檔案夾時自動複製，OpenXr 執行時間選取範圍通常如下所示。

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>使用全像全像遠端擴充功能建立 XrInstance

一般 OpenXR 應用程式的第一個步驟應該是選取 OpenXR 擴充功能，並建立 XrInstance。 OpenXR 核心規格不提供任何遠端特定 API。 基於這個理由，「全像 ```XR_MSFT_holographic_remoting``` 確定當您呼叫 xrCreateInstance 時， ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` 會包含在 XrInstanceCreateInfo 中。

>[!TIP]
>根據預設，您的應用程式呈現內容只會串流至在 HoloLens 2 或 Windows Mixed Reality 耳機上執行的全像遠端播放程式。 若要在遠端電腦上顯示轉譯的內容，您可以透過視窗的交換鏈（例如，「全像」）來提供第二個名為的 OpenXR 延伸模組 ```XR_MSFT_holographic_remoting_frame_mirroring``` 。 ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME```如果您想要使用該功能，請務必使用此延伸模組。

>[!IMPORTANT]
>To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="connect-to-the-device"></a>連線至裝置

當您的遠端應用程式建立 XrInstance，並透過 xrGetSystem 查詢 XrSystemId 之後，就可以建立與播放機裝置的連線。

>[!WARNING]
> 全像遠端 OpenXR 執行時間只能在建立連接之後提供裝置特定資料，例如 view 設定或環境 blend 模式。 ```xrEnumerateViewConfigurations```、 ```xrEnumerateViewConfigurationViews``` 、 ```xrGetViewConfigurationProperties``` 、 ```xrEnumerateEnvironmentBlendModes``` 和 ```xrGetSystemProperties``` 將會提供預設值，以符合您在連線到 HoloLens 2 上執行的播放玩家之前，您通常會得到的值，然後再完全連接。
強烈建議您不要在建立連接之前呼叫這些方法。 在成功建立 XrSession 之後，會話狀態至少 XR_SESSION_STATE_READY，就會使用這些方法。

您可以透過下列方式設定一般屬性，例如最大位元速率、已啟用音訊、視頻編碼器或深度緩衝區串流解析 ```xrRemotingSetContextPropertiesMSFT``` 。

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

您可以透過下列兩種方式之一來完成連接。
1) 遠端應用程式會連接到在裝置上執行的播放程式。
2) 在裝置上執行的播放程式會連接到遠端應用程式。

若要建立從遠端應用程式到 player 裝置的連線，請呼叫方法，透過 ```xrRemotingConnectMSFT``` 結構指定主機名稱和埠  ```XrRemotingConnectInfoMSFT``` 。 全像遠端播放機使用的埠是 **8265**。

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

您可以藉由呼叫方法來接聽遠端應用程式上的連入連線 ```xrRemotingListenMSFT``` 。 交握埠和傳輸埠都可以透過結構來指定 ```XrRemotingListenInfoMSFT``` 。 交握埠用於初始交握。 然後，資料會透過傳輸埠來傳送。 預設會使用 **8265** 和 **8266** 。

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

當您呼叫或時，連接狀態必須中斷連接 ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` 。 您可以在建立 XrInstance 之後隨時取得連接狀態，並透過來查詢 XrSystemId ```xrRemotingGetConnectionStateMSFT``` 。

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

可用的連接狀態為：
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``` 或 ```xrRemotingListenMSFT``` 必須在嘗試透過 xrCreateSession 建立 XrSession 之前呼叫。 如果您嘗試在連接狀態為時建立 XrSession， ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 會話建立將會成功，但會話狀態將會立即轉換為 XR_SESSION_STATE_LOSS_PENDING。

全像的遠端執行 ```xrCreateSession``` 支援等候建立連接。 您可以呼叫 ```xrRemotingConnectMSFT``` 或 ```xrRemotingListenMSFT``` 立即進行呼叫，這會封鎖並等候建立連接。 Timeout 會固定為10秒。 如果可以在這段時間內建立連線，XrSession 建立將會成功，且會話狀態將會轉換為 XR_SESSION_STATE_READY。 如果無法建立連線，會話建立也會成功，但會立即轉換為 XR_SESSION_STATE_LOSS_PENDING。

一般情況下，連接狀態會是 XrSession 狀態的幾個。 連接狀態的任何變更也會影響會話狀態。 比方說，如果連接狀態從切換 `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` 到 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 會話狀態，也會轉換成 XR_SESSION_STATE_LOSS_PENDING。

## <a name="handling-remoting-specific-events"></a>處理遠端處理特定事件

全像「全像遠端 OpenXR 執行時間」會公開三個事件，這對監視連接的狀態非常重要。
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```：當成功建立裝置的連線時，就會觸發。
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```：當建立的連接已關閉或無法建立連接時，就會觸發。
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```：接聽連入連線開始時。

這些事件會放置在佇列中，而您的遠端應用程式必須透過變更規律性從佇列讀取 ```xrPollEvent``` 。

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a>在本機預覽資料流程內容

若要在傳送至裝置的遠端應用程式中顯示相同的內容， ```XR_MSFT_holographic_remoting_frame_mirroring``` 可以使用擴充功能。 使用此延伸模組，您可以使用 ```XrRemotingFrameMirrorImageInfoMSFT``` 未連結至 XrFrameEndInfo 的，將材質提交至 xrEndFrame，如下所示。

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

上述範例會使用 DX11 相互作用交換鏈材質，並在呼叫 xrEndFrame 之後立即呈現視窗。 使用方式不限於交換鏈材質，也不需要額外的 GPU 同步處理。 如需使用方式和條件約束的詳細資訊，請查看 [延伸模組規格](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring)。
如果您的遠端應用程式使用 DX12，請使用 XrRemotingFrameMirrorImageD3D12MSFT 而不是 XrRemotingFrameMirrorImageD3D11MSFT。

## <a name="see-also"></a>另請參閱
* [全像遠端處理總覽](holographic-remoting-overview.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [建立全像攝影遠端處理的連線安全](holographic-remoting-secure-connection.md)
* [全像遠端的疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)