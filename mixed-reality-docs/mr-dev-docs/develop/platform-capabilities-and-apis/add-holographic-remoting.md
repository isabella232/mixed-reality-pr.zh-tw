---
title: 新增全像遠端
description: 瞭解如何安裝、設定和使用全像的遠端處理，透過網路將全像是 HoloLens 裝置呈現。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality、全像全像全像）、遠端轉譯、網路轉譯、HoloLens、遠端全息全像、混合現實耳機、Windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 3f9d3d23d18f680ce1001310e4ce49089edaae6a
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184619"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>新增全像遠端 (HoloLens (第一代) ) 

>[!IMPORTANT]
> 本檔說明如何建立 HoloLens 1 的主應用程式。 **HoloLens (第1代)** 的主機應用程式必須使用 NuGet 套件1.x 版。 這表示針對 HoloLens 1 所撰寫的主機應用程式與 HoloLens 2 不相容，反之亦然。

## <a name="hololens-2"></a>HoloLens 2

使用全像攝影版的 HoloLens 開發人員必須更新其應用程式，使其與 HoloLens 2 相容。 這需要新版本的全像攝影遠端 NuGet 套件。 連接到 HoloLens 2 上的全像遠端播放程式時，請務必使用「全像」 NuGet 套件的2.0.0.0 版或更高版本，否則連線將會失敗。

>[!NOTE]
> 您可以在[這裡](holographic-remoting-create-remote-wmr.md)找到 HoloLens 2 的特定指引。


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>在您的桌面或 UWP 應用程式中新增全像遠端處理

此頁面說明如何在桌面或 UWP 應用程式中新增「全像」遠端處理。

全像「全像」遠端功能可讓您的應用程式以 HoloLens，其中包含桌上型電腦或 UWP 裝置（例如 Xbox One）上的全像內容。 您也可以存取更多系統資源，讓您能夠將遠端 [沉浸式視圖](../../design/app-views.md) 整合至現有的桌上型電腦軟體。 遠端主機應用程式會從 HoloLens 接收輸入資料流程、在虛擬沉浸式視圖中轉譯內容，並將內容框架串流回 HoloLens。 連接是使用標準 Wi-fi 進行的。 若要使用遠端處理，請使用 NuGet 套件將全像遠端處理新增至您的桌面或 UWP 應用程式，然後撰寫程式碼以處理連接並呈現沉浸式視圖。 Helper 程式庫包含在程式碼範例中，可簡化處理裝置連線的工作。

一般的遠端連線的延遲將會降到50毫秒。 播放程式應用程式可以即時報告延遲時間。

>[!NOTE]
>本文中的程式碼片段目前示範如何使用 c + + [/cx，而](../native/creating-a-holographic-directx-project.md)不是 c + + 全像 c + + 全像 c + + 的 + 17 相容 c + +/WinRT。  這些概念對 c + +/WinRT 專案而言是相等的，不過您必須轉譯程式碼。

### <a name="get-the-remoting-nuget-packages"></a>取得遠端 NuGet 套件

遵循下列步驟來取得適用于全像攝影的 NuGet 套件，並從您的專案新增參考：
1. 在 Visual Studio 中移至您的專案。
2. 以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 封裝 ...**
3. 在出現的面板中，選取 **流覽]** ，然後搜尋「全像全像」。
4. 選取 [選取 **安裝**]，然後選取 [ **Microsoft** ]。
5. 如果出現 [ **預覽** ] 對話方塊，請選取 **[確定]**。
6. 當 [授權合約] 對話方塊出現時，選取 [ **我接受** ]。

### <a name="create-the-holographicstreamerhelpers"></a>建立 HolographicStreamerHelpers

首先，我們需要將 HolographicStreamerHelpers 的實例加入至將處理遠端處理的類別。

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

您也需要追蹤連接狀態。 如果您想要轉譯預覽，您必須要有材質才能將它複製到。 您也需要一些東西，例如線上狀態鎖定、一些儲存 HoloLens IP 位址的方法等等。

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>初始化 HolographicStreamerHelpers 並連接到 HoloLens

若要連線到 HoloLens 裝置，請建立 HolographicStreamerHelpers 的實例，並連接到目標 IP 位址。 您必須設定影片畫面格大小，以符合 HoloLens 顯示寬度和高度，因為全像全像遠端程式庫預期編碼器和解碼器解析度必須完全相符。

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

裝置連接是非同步。 您的應用程式需要提供連接、中斷連線和框架傳送事件的事件處理常式。

OnConnected 事件可以更新 UI、開始轉譯等等。 在我們的桌面程式碼範例中，我們會使用「已連線」訊息來更新視窗標題。

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected 事件可以處理重新連接、UI 更新等等。 在此範例中，如果發生暫時性失敗，我們會重新連接。

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

當遠端處理元件準備好傳送框架時，您的應用程式有機會在 SendFrameEvent 中建立它的複本。 在這裡，我們會將畫面格複製到交換鏈，讓我們可以將它顯示在預覽視窗中。

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>轉譯全息內容

若要使用遠端處理來轉譯內容，您可以在桌面或 UWP 應用程式內設定虛擬 IFrameworkView，並處理來自遠端的全像攝影框架。 此視圖使用相同的方式來使用所有 Windows 全息型 api，但設定方式稍有不同。

全像是 HolographicRemotingHelpers 類別，而不是自行建立：

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

您可以從桌面或 UWP 應用程式的主要迴圈中提供滴答更新，而不是在執行方法中使用 update 迴圈。 這可讓您的桌面或 UWP 應用程式保有訊息處理的控制權。

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

全像 app view 的 Tick () 方法會完成 update、draw、現在時迴圈的一個反復專案。

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

全像應用程式視圖更新、轉譯和呈現迴圈，與在 HoloLens 上執行時完全相同，但您可以在桌上型電腦上存取更大量的系統資源。 您可以呈現許多三角形、擁有更多繪圖、執行更多物理，以及使用 x64 進程載入需要 2 GB 以上 RAM 的內容。

### <a name="disconnect-and-end-the-remote-session"></a>中斷連線並結束遠端會話

若要中斷連線-例如，當使用者按一下 UI 按鈕來中斷 HolographicStreamerHelpers 的連線中斷 () ，然後釋放物件。

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>取得遠端播放機

Windows app store 中提供 Windows 的全像遠端播放機，作為遠端主機應用程式連接的端點。 若要取得 Windows 的全像遠端播放程式，請從您的 HoloLens 流覽 Windows app store、搜尋遠端處理，然後下載應用程式。 遠端處理播放套裝程式含在螢幕上顯示統計資料的功能，這在對遠端主機應用程式進行偵錯工具時很有用。

## <a name="notes-and-resources"></a>注意事項和資源

全像「全像」應用程式視圖需要一種方法來提供您的應用程式與 Direct3D 裝置，必須用來將全像空間初始化。 您的應用程式應該使用此 Direct3D 裝置來複製和顯示預覽框架。

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

程式 **代碼範例：** 您可以使用完整的全像 [遠端處理常式代碼範例](https://github.com/Microsoft/HoloLensCompanionKit)，其中包含了一種全像桌面應用程式，可與桌上型電腦 WIN32、uwp DIRECTX 和 UWP 的遠端處理和遠端處理主項目目相容。 

**調試附注：** 全像全像遠端程式庫可能會擲回第一個可能發生的例外狀況。 這些例外狀況可能會顯示在偵錯工具中，視當時作用中的 Visual Studio 例外狀況設定而定。 這些例外狀況是由全像「全像」遠端程式庫在內部攔截，可以忽略。

## <a name="see-also"></a>另請參閱
* [全像遠端處理總覽](holographic-remoting-overview.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [建立全像攝影遠端處理的連線安全](holographic-remoting-secure-connection.md)
* [全像遠端的疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)