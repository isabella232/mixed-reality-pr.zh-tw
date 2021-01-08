---
title: 新增全像遠端
description: 瞭解如何安裝、設定和使用全像全像的遠端處理，透過網路將全像是的 HoloLens 裝置呈現。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality，全像全像全像全像，遠端轉譯、網路轉譯、HoloLens、遠端全息全像、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 68c1dd43dac4830da061d4900ce768692057e781
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006668"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a><span data-ttu-id="813fd-104">新增全像 (HoloLens (first gen) # A3</span><span class="sxs-lookup"><span data-stu-id="813fd-104">Add Holographic Remoting (HoloLens (first gen))</span></span>

>[!IMPORTANT]
> <span data-ttu-id="813fd-105">本檔說明如何建立 HoloLens 1 的主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="813fd-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="813fd-106">適用于 HoloLens 的主機應用程式 **(第1代)** 必須使用 NuGet 套件1.x 版。</span><span class="sxs-lookup"><span data-stu-id="813fd-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="813fd-107">這表示針對 HoloLens 1 所撰寫的主機應用程式與 HoloLens 2 不相容，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="813fd-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="813fd-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="813fd-108">HoloLens 2</span></span>

<span data-ttu-id="813fd-109">HoloLens 開發人員必須更新應用程式，才能使其與 HoloLens 2 相容。</span><span class="sxs-lookup"><span data-stu-id="813fd-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="813fd-110">這需要新版本的全像「全像」版本的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="813fd-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="813fd-111">連接到 HoloLens 2 上的全像遠端播放程式時，請務必使用「全像」、「全像」的「全像」、「全像」、「全像」、「</span><span class="sxs-lookup"><span data-stu-id="813fd-111">Be sure to use version 2.0.0.0 or above of the Holographic Remoting NuGet package when connecting to the Holographic Remoting Player on HoloLens 2 or the connection will fail.</span></span>

>[!NOTE]
> <span data-ttu-id="813fd-112">您可以在 [這裡](holographic-remoting-create-remote-wmr.md)找到 HoloLens 2 的特定指引。</span><span class="sxs-lookup"><span data-stu-id="813fd-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-remote-wmr.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="813fd-113">在您的桌面或 UWP 應用程式中新增全像遠端處理</span><span class="sxs-lookup"><span data-stu-id="813fd-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="813fd-114">此頁面說明如何在桌面或 UWP 應用程式中新增「全像」遠端處理。</span><span class="sxs-lookup"><span data-stu-id="813fd-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="813fd-115">全像「全像」遠端功能可讓您的應用程式以 HoloLens 取代在桌上型電腦或 UWP 裝置（例如 Xbox One）上裝載的全息內容。</span><span class="sxs-lookup"><span data-stu-id="813fd-115">Holographic remoting lets your app target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One.</span></span> <span data-ttu-id="813fd-116">您也可以存取更多系統資源，讓您能夠將遠端 [沉浸式視圖](../../design/app-views.md) 整合至現有的桌上型電腦軟體。</span><span class="sxs-lookup"><span data-stu-id="813fd-116">You also have access to more system resources, making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="813fd-117">遠端主機應用程式會從 HoloLens 接收輸入資料流程、在虛擬沉浸式視圖中轉譯內容，並將內容框架串流回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="813fd-117">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="813fd-118">連接是使用標準 Wi-fi 進行的。</span><span class="sxs-lookup"><span data-stu-id="813fd-118">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="813fd-119">若要使用遠端處理，請使用 NuGet 套件將全像遠端處理新增至您的桌面或 UWP 應用程式，然後撰寫程式碼以處理連接並轉譯沉浸式視圖。</span><span class="sxs-lookup"><span data-stu-id="813fd-119">To use remoting, use a NuGet package to add holographic remoting to your desktop or UWP app, then write code to handle the connection and render an immersive view.</span></span> <span data-ttu-id="813fd-120">Helper 程式庫包含在程式碼範例中，可簡化處理裝置連線的工作。</span><span class="sxs-lookup"><span data-stu-id="813fd-120">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="813fd-121">一般的遠端連線的延遲將會降到50毫秒。</span><span class="sxs-lookup"><span data-stu-id="813fd-121">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="813fd-122">播放程式應用程式可以即時報告延遲時間。</span><span class="sxs-lookup"><span data-stu-id="813fd-122">The player app can report the latency in real time.</span></span>

>[!NOTE]
><span data-ttu-id="813fd-123">本文中的程式碼片段目前示範如何使用 c + + [/cx，而](../native/creating-a-holographic-directx-project.md)不是 c + + 全像 c + + 全像 c + + 的 + 17 相容 c + +/WinRT。</span><span class="sxs-lookup"><span data-stu-id="813fd-123">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="813fd-124">這些概念對 c + +/WinRT 專案而言是相等的，不過您必須轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="813fd-124">The concepts are equivalent for a C++/WinRT project, though you'll need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="813fd-125">取得遠端 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="813fd-125">Get the remoting NuGet packages</span></span>

<span data-ttu-id="813fd-126">遵循下列步驟來取得適用于全像攝影的 NuGet 套件，並從您的專案新增參考：</span><span class="sxs-lookup"><span data-stu-id="813fd-126">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="813fd-127">在 Visual Studio 中移至您的專案。</span><span class="sxs-lookup"><span data-stu-id="813fd-127">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="813fd-128">以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 套件 ...** ]</span><span class="sxs-lookup"><span data-stu-id="813fd-128">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="813fd-129">在出現的面板中，選取 **流覽]** ，然後搜尋「全像全像」。</span><span class="sxs-lookup"><span data-stu-id="813fd-129">In the panel that appears, selecct **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="813fd-130">選取 [選取 **安裝**]，然後選取 [ **Microsoft** ]。</span><span class="sxs-lookup"><span data-stu-id="813fd-130">Select **Microsoft.Holographic.Remoting** and selecct **Install**.</span></span>
5. <span data-ttu-id="813fd-131">如果出現 [ **預覽** ] 對話方塊，請選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="813fd-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="813fd-132">當 [授權合約] 對話方塊出現時，選取 [ **我接受** ]。</span><span class="sxs-lookup"><span data-stu-id="813fd-132">Select **I Accept** when the license agreement dialog appears.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="813fd-133">建立 HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="813fd-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="813fd-134">首先，我們需要將 HolographicStreamerHelpers 的實例加入至將處理遠端處理的類別。</span><span class="sxs-lookup"><span data-stu-id="813fd-134">First, we need to add an instance of HolographicStreamerHelpers to the class that will handle remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="813fd-135">您也需要追蹤連接狀態。</span><span class="sxs-lookup"><span data-stu-id="813fd-135">You'll also need to track connection state.</span></span> <span data-ttu-id="813fd-136">如果您想要轉譯預覽，您必須要有材質才能將它複製到。</span><span class="sxs-lookup"><span data-stu-id="813fd-136">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="813fd-137">您也需要一些像是線上狀態鎖定、一些儲存 HoloLens IP 位址等專案的方式。</span><span class="sxs-lookup"><span data-stu-id="813fd-137">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="813fd-138">初始化 HolographicStreamerHelpers 並連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="813fd-138">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="813fd-139">若要連接到 HoloLens 裝置，請建立 HolographicStreamerHelpers 的實例，並連接到目標 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="813fd-139">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="813fd-140">您必須設定影片畫面格大小，使其符合 HoloLens 顯示器的寬度和高度，因為全像是「全像」遠端程式庫預期編碼器和解碼器解析度必須完全相符。</span><span class="sxs-lookup"><span data-stu-id="813fd-140">You'll need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

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

<span data-ttu-id="813fd-141">裝置連接是非同步。</span><span class="sxs-lookup"><span data-stu-id="813fd-141">The device connection is asynchronous.</span></span> <span data-ttu-id="813fd-142">您的應用程式需要提供連接、中斷連線和框架傳送事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="813fd-142">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="813fd-143">OnConnected 事件可以更新 UI、開始轉譯等等。</span><span class="sxs-lookup"><span data-stu-id="813fd-143">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="813fd-144">在我們的桌面程式碼範例中，我們會使用「已連線」訊息來更新視窗標題。</span><span class="sxs-lookup"><span data-stu-id="813fd-144">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="813fd-145">OnDisconnected 事件可以處理重新連接、UI 更新等等。</span><span class="sxs-lookup"><span data-stu-id="813fd-145">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="813fd-146">在此範例中，如果發生暫時性失敗，我們會重新連接。</span><span class="sxs-lookup"><span data-stu-id="813fd-146">In this example, we reconnect if there's a transient failure.</span></span>

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

<span data-ttu-id="813fd-147">當遠端處理元件準備好傳送框架時，您的應用程式有機會在 SendFrameEvent 中建立它的複本。</span><span class="sxs-lookup"><span data-stu-id="813fd-147">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="813fd-148">在這裡，我們會將畫面格複製到交換鏈，讓我們可以將它顯示在預覽視窗中。</span><span class="sxs-lookup"><span data-stu-id="813fd-148">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

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

### <a name="render-holographic-content"></a><span data-ttu-id="813fd-149">轉譯全息內容</span><span class="sxs-lookup"><span data-stu-id="813fd-149">Render holographic content</span></span>

<span data-ttu-id="813fd-150">若要使用遠端處理來轉譯內容，您可以在桌面或 UWP 應用程式內設定虛擬 IFrameworkView，並處理來自遠端的全像攝影框架。</span><span class="sxs-lookup"><span data-stu-id="813fd-150">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="813fd-151">此視圖使用所有的 Windows 全像攝影 Api，但設定方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="813fd-151">All of the Windows Holographic APIs are used the same way by this view, but it's set up slightly differently.</span></span>

<span data-ttu-id="813fd-152">全像是 HolographicRemotingHelpers 類別，而不是自行建立：</span><span class="sxs-lookup"><span data-stu-id="813fd-152">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="813fd-153">您可以從桌面或 UWP 應用程式的主要迴圈中提供滴答更新，而不是在執行方法中使用 update 迴圈。</span><span class="sxs-lookup"><span data-stu-id="813fd-153">Instead of using an update loop in a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="813fd-154">這可讓您的桌面或 UWP 應用程式保有訊息處理的控制權。</span><span class="sxs-lookup"><span data-stu-id="813fd-154">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="813fd-155">全像應用程式視圖的刻度 ( # A1 方法會完成 update、draw、現在時迴圈的一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="813fd-155">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

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

<span data-ttu-id="813fd-156">全像應用程式視圖更新、轉譯和呈現迴圈，與在 HoloLens 上執行時完全相同，但您可以在桌上型電腦上存取更大量的系統資源。</span><span class="sxs-lookup"><span data-stu-id="813fd-156">The holographic app view update, render, and present loop are exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="813fd-157">您可以呈現許多三角形、擁有更多繪圖、執行更多物理，以及使用 x64 進程載入需要 2 GB 以上 RAM 的內容。</span><span class="sxs-lookup"><span data-stu-id="813fd-157">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="813fd-158">中斷連線並結束遠端會話</span><span class="sxs-lookup"><span data-stu-id="813fd-158">Disconnect and end the remote session</span></span>

<span data-ttu-id="813fd-159">若要中斷連線-例如，當使用者按一下 UI 按鈕進行中斷連線時 ( # A1 HolographicStreamerHelpers，然後釋放物件。</span><span class="sxs-lookup"><span data-stu-id="813fd-159">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

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

## <a name="get-the-remoting-player"></a><span data-ttu-id="813fd-160">取得遠端播放機</span><span class="sxs-lookup"><span data-stu-id="813fd-160">Get the remoting player</span></span>

<span data-ttu-id="813fd-161">Windows app store 中提供的 Windows 全像遠端存取播放程式，可作為遠端主機應用程式連接的端點。</span><span class="sxs-lookup"><span data-stu-id="813fd-161">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="813fd-162">若要取得 Windows 全像遠端播放播放程式，請從您的 HoloLens 流覽 Windows app store、搜尋遠端處理，然後下載應用程式。</span><span class="sxs-lookup"><span data-stu-id="813fd-162">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="813fd-163">遠端處理播放套裝程式含在螢幕上顯示統計資料的功能，這在對遠端主機應用程式進行偵錯工具時很有用。</span><span class="sxs-lookup"><span data-stu-id="813fd-163">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="813fd-164">注意事項和資源</span><span class="sxs-lookup"><span data-stu-id="813fd-164">Notes and resources</span></span>

<span data-ttu-id="813fd-165">全像「全像」應用程式視圖需要一種方法來提供您的應用程式與 Direct3D 裝置，必須用來將全像空間初始化。</span><span class="sxs-lookup"><span data-stu-id="813fd-165">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="813fd-166">您的應用程式應該使用此 Direct3D 裝置來複製和顯示預覽框架。</span><span class="sxs-lookup"><span data-stu-id="813fd-166">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="813fd-167">程式 **代碼範例：** 您可以使用完整的全像 [遠端處理常式代碼範例](https://github.com/Microsoft/HoloLensCompanionKit)，其中包含了一種全像桌面應用程式，可與桌上型電腦 WIN32、uwp DIRECTX 和 UWP 的遠端處理和遠端處理主項目目相容。</span><span class="sxs-lookup"><span data-stu-id="813fd-167">**Code sample:** A complete [Holographic Remoting code sample](https://github.com/Microsoft/HoloLensCompanionKit) is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> 

<span data-ttu-id="813fd-168">**調試附注：** 全像全像遠端程式庫可能會擲回第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="813fd-168">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="813fd-169">這些例外狀況可能會顯示在偵錯工具中，視當時作用中的 Visual Studio 例外狀況設定而定。</span><span class="sxs-lookup"><span data-stu-id="813fd-169">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="813fd-170">這些例外狀況是由全像「全像」遠端程式庫在內部攔截，可以忽略。</span><span class="sxs-lookup"><span data-stu-id="813fd-170">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
