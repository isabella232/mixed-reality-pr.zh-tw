---
title: 取得 HolographicSpace
description: 瞭解如何在您的混合現實應用程式中使用 HolographicSpace API 進行全像轉譯和空間輸入。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality、HolographicSpace、CoreWindow、空間輸入、轉譯、交換鏈、全像攝影框架、更新迴圈、遊戲迴圈、參考框架、locatability、範例程式碼、逐步解說、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 215c3cbacd4c7975d05b3a1b3f3992c9198642f7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580912"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="fb0e5-104">取得 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="fb0e5-104">Getting a HolographicSpace</span></span>

> [!NOTE]
> <span data-ttu-id="fb0e5-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="fb0e5-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)**。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="fb0e5-107"><a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別是您的入口網站，進入全像全球。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-107">The <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="fb0e5-108">它會控制沉浸式轉譯、提供相機資料，並提供空間推理 Api 的存取權。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-108">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="fb0e5-109">您將針對 UWP 應用程式的 <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> 或您的 Win32 應用程式 HWND 建立一個。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-109">You'll create one for your UWP app's <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="fb0e5-110">設定全像空間</span><span class="sxs-lookup"><span data-stu-id="fb0e5-110">Set up the holographic space</span></span>

<span data-ttu-id="fb0e5-111">建立全像空間物件是建立 Windows Mixed Reality 應用程式的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-111">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="fb0e5-112">傳統的 Windows 應用程式會轉譯成針對其應用程式視圖的核心視窗所建立的 Direct3D 交換鏈。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-112">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="fb0e5-113">此交換鏈會顯示于全像平板使用者的平板中。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-113">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="fb0e5-114">若要讓您的應用程式視圖成為全像2D 的平板電腦，請建立其核心視窗的全像空間，而不是交換鏈。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-114">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="fb0e5-115">展示此全像空間所建立的全螢幕畫面格，可將您的應用程式放入全螢幕轉譯模式。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-115">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="fb0e5-116">針對從全像 [ *DirectX 11 應用程式開始 (通用 Windows) 範本*](creating-a-holographic-directx-project.md)的 **UWP 應用程式**，請在 AppView 中的 **SetWindow** 方法中尋找此程式碼：</span><span class="sxs-lookup"><span data-stu-id="fb0e5-116">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="fb0e5-117">如果您要建立 [從 *BasicHologram* win32 範例開始](creating-a-holographic-directx-project.md#creating-a-win32-project)的 **win32 應用程式**，請查看 **app：： CreateWindowAndHolographicSpace** 中的 HWND 範例。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-117">If you're building a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an HWND example.</span></span> <span data-ttu-id="fb0e5-118">然後，您可以建立相關聯的 <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>，將它轉換成沉浸式 HWND：</span><span class="sxs-lookup"><span data-stu-id="fb0e5-118">You can then convert it into an immersive HWND by creating an associated <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="fb0e5-119">一旦取得 UWP CoreWindow 或 Win32 HWND 的 HolographicSpace，HolographicSpace 就可以處理全像攝影、建立座標系統，以及進行全像攝影轉譯。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-119">Once you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, the HolographicSpace can handle holographic cameras, create coordinate systems, and do holographic rendering.</span></span> <span data-ttu-id="fb0e5-120">目前的全像空間可用於 DirectX 範本中的多個位置：</span><span class="sxs-lookup"><span data-stu-id="fb0e5-120">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="fb0e5-121">**DeviceResources** 類別需要從 HolographicSpace 物件取得一些資訊，才能建立 Direct3D 裝置。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-121">The **DeviceResources** class needs to get some information from the HolographicSpace object to create the Direct3D device.</span></span> <span data-ttu-id="fb0e5-122">這是與全像全像顯示器相關聯的 DXGI 介面卡識別碼。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-122">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="fb0e5-123"><a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別會使用您應用程式的 Direct3D 11 裝置來建立及管理裝置資源，例如每個全像攝影相機的背景緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-123">The <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="fb0e5-124">如果您有興趣查看此函式的本質，您可以在 DeviceResources 中找到它。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-124">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="fb0e5-125">函式 **DeviceResources：： InitializeUsingHolographicSpace** 示範如何藉由查閱 LUID 來取得介面卡，以及如何在未指定慣用介面卡時選擇預設的介面卡。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-125">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="fb0e5-126">應用程式的主要類別會使用 **AppView：： SetWindow** 或 **App：： CreateWindowAndHolographicSpace** 的全像空間來進行更新和轉譯。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-126">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="fb0e5-127">雖然下列各節提及範本中的函式名稱（例如 **AppView：： SetWindow** ），這會假設您已從全像 uwp 應用程式範本開始，但您看到的程式碼片段同樣適用于 UWP 和 Win32 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-127">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="fb0e5-128">接下來，我們將深入探討 **SetHolographicSpace** 在 AppMain 類別中負責的設定流程。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-128">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="fb0e5-129">訂閱攝影機事件、建立和移除相機資源</span><span class="sxs-lookup"><span data-stu-id="fb0e5-129">Subscribe to camera events, create, and remove camera resources</span></span>

<span data-ttu-id="fb0e5-130">您應用程式的全像攝影空間，是透過一或多個全像攝影攝影機來查看，代表場景上的不同觀點。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-130">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras, which represent different perspectives on the scene.</span></span> <span data-ttu-id="fb0e5-131">現在您已有全像攝影空間，您可以接收全像攝影攝影機的資料。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-131">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="fb0e5-132">您的應用程式必須藉由建立該攝影機的特定資源來回應 **CameraAdded** 事件。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-132">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera.</span></span> <span data-ttu-id="fb0e5-133">這類資源的範例是您的背景緩衝區轉譯目標視圖。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-133">An example of such a resource is your back buffer render target view.</span></span> <span data-ttu-id="fb0e5-134">您可以在應用程式建立任何內建的框架之前，在 **DeviceResources：： SetHolographicSpace** 函式中看到此程式碼（由 **AppView：： SetWindow** 呼叫）：</span><span class="sxs-lookup"><span data-stu-id="fb0e5-134">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="fb0e5-135">您的應用程式也需要釋出為該攝影機建立的資源，以回應 **CameraRemoved** 事件。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-135">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="fb0e5-136">從 **DeviceResources：： SetHolographicSpace**：</span><span class="sxs-lookup"><span data-stu-id="fb0e5-136">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="fb0e5-137">事件處理常式必須完成一些工作，讓全像攝影轉譯流暢地流動，並讓您的應用程式呈現。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-137">The event handlers must complete some work to keep holographic rendering flowing smoothly, and your app rendering at all.</span></span> <span data-ttu-id="fb0e5-138">閱讀詳細資料的程式碼和批註：您可以在主要類別中尋找 **OnCameraAdded** 和 **OnCameraRemoved** ，以瞭解 **DeviceResources** 如何處理 **m_cameraResources** 對應。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-138">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="fb0e5-139">現在，我們將焦點放在 AppMain 和設定，讓您的應用程式知道全像攝影攝影機。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-139">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="fb0e5-140">記住這一點，請務必記下下列兩個需求：</span><span class="sxs-lookup"><span data-stu-id="fb0e5-140">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="fb0e5-141">針對 **CameraAdded** 事件處理常式，應用程式可以非同步運作，以完成建立資源，以及為新的全像攝影中心載入資產。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-141">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="fb0e5-142">使用多個畫面格來完成這項工作的應用程式應該要求延遲，並在非同步載入之後完成延遲。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-142">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously.</span></span> <span data-ttu-id="fb0e5-143">[PPL](/cpp/parallel/concrt/parallel-patterns-library-ppl)工作可以用來執行非同步工作。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-143">A [PPL task](/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="fb0e5-144">您的應用程式必須在結束事件處理常式或完成延遲時，確保它可以立即呈現給該攝影機。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-144">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="fb0e5-145">結束事件處理常式或完成延遲，會告訴系統您的應用程式現在已準備好接收包含該攝影機的全像攝影畫面。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-145">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="fb0e5-146">當應用程式收到 **CameraRemoved** 事件時，它必須釋放對背景緩衝區的所有參考，並立即結束函式。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-146">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="fb0e5-147">這包括轉譯目標視圖，以及可能保存 [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)參考的任何其他資源。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-147">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="fb0e5-148">應用程式也必須確保背景緩衝區未以轉譯目標的形式附加，如 **CameraResources：： ReleaseResourcesForBackBuffer** 所示。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-148">The app must also ensure that the back buffer isn't attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="fb0e5-149">為了協助加速作業，您的應用程式可以釋出背景緩衝區，然後啟動工作以非同步完成相機的任何其他終止工作。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-149">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other tear down work for the camera.</span></span> <span data-ttu-id="fb0e5-150">全像「全像」應用程式範本包含可用於此用途的 PPL 工作。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-150">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="fb0e5-151">如果您想要判斷畫面上顯示的是新增或移除的相機，請使用 **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) 和 [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) 屬性。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-151">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="fb0e5-152">為您的全像內容建立參考框架</span><span class="sxs-lookup"><span data-stu-id="fb0e5-152">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="fb0e5-153">您應用程式的內容必須放置在要在 HolographicSpace 中轉譯的 [空間座標系統](coordinate-systems-in-directx.md) 中。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-153">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="fb0e5-154">系統提供兩個主要的參考框架，您可以用來建立您的全像影像的座標系統。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-154">The system provides two primary frames of reference, which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="fb0e5-155">Windows 內建的參考框架有兩種：連結至裝置的參考框架，以及裝置在使用者的環境中移動時仍保持靜止的參考框架。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-155">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="fb0e5-156">全像「全像」應用程式範本預設會使用固定的參考框架;這是呈現全球鎖定的全像是最簡單的方式之一。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-156">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="fb0e5-157">固定的參考框架是針對裝置目前位置附近的穩定位置所設計。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-157">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="fb0e5-158">這表示，從裝置進一步的座標可能會稍微偏離使用者的環境，因為裝置會深入瞭解它周圍的空間。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-158">This means that coordinates further from the device can drift slightly relative to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="fb0e5-159">有兩種方式可以建立固定的參考框架：從 [空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)取得座標系統，或使用預設 <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-159">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="fb0e5-160">如果您要建立沉浸式耳機的 Windows Mixed Reality 應用程式，建議的起點是 [空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-160">If you're creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage).</span></span> <span data-ttu-id="fb0e5-161">空間階段也會提供玩家所磨損之沉浸式耳機功能的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-161">The spatial stage also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="fb0e5-162">在這裡，我們會示範如何使用預設 <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-162">Here, we show how to use the default <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="fb0e5-163">空間定位器代表 Windows Mixed Reality 裝置，並會追蹤裝置的動作，並提供可理解的座標系統（相對於其位置）。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-163">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="fb0e5-164">從 **AppMain：： OnHolographicDisplayIsAvailableChanged**：</span><span class="sxs-lookup"><span data-stu-id="fb0e5-164">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="fb0e5-165">當應用程式啟動時，請建立固定的參考框架。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-165">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="fb0e5-166">這類似于定義全局座標系統，並在應用程式啟動時，將原點放置於裝置的位置。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-166">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="fb0e5-167">此參考框架不會與裝置一起移動。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-167">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="fb0e5-168">從 **AppMain：： SetHolographicSpace**：</span><span class="sxs-lookup"><span data-stu-id="fb0e5-168">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="fb0e5-169">所有的參考框架都是引力對齊的，也就是說 y 軸會指向與使用者環境相關的「向上」。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-169">All reference frames are gravity aligned, meaning that the y-axis points "up" in relation to the user's environment.</span></span> <span data-ttu-id="fb0e5-170">由於 Windows 使用「右手」座標系統，因此– Z 軸的方向會與裝置在參考框架建立時所面向的「轉寄」方向一致。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-170">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="fb0e5-171">當您的應用程式需要精確放置個別的全像投影時，請使用 <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> 將個別的全像點放置到真實世界的某個位置。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-171">When your app requires precise placement of individual holograms, use a <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="fb0e5-172">例如，當使用者指出要特別注意的點時，請使用空間錨點。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-172">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="fb0e5-173">錨點位置不會漂移，但可以調整。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-173">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="fb0e5-174">根據預設，當錨點調整之後，它會在發生更正之後，讓其在接下來的幾個框架上達到適當的位置。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-174">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="fb0e5-175">視您的應用程式而定，當發生這種情況時，您可能會想要以不同的方式處理調整 (例如，將其延後到全像全像) 為止。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-175">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="fb0e5-176"><a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>屬性和<a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件可啟用這些自訂。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-176">The <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="fb0e5-177">回應 locatability 已變更的事件</span><span class="sxs-lookup"><span data-stu-id="fb0e5-177">Respond to locatability changed events</span></span>

<span data-ttu-id="fb0e5-178">呈現世界鎖定的全像裝置，需要裝置在世界各地找出本身。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-178">Rendering world-locked holograms requires the device to locate itself in the world.</span></span> <span data-ttu-id="fb0e5-179">這可能不一定是因為環境條件，而如果是的話，使用者可能會預期追蹤中斷的視覺表示。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-179">This may not always be possible because of environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="fb0e5-180">此視覺指示必須使用附加至裝置的參考框架來呈現，而不是使用非固定的環境。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-180">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="fb0e5-181">您的應用程式可以要求在追蹤因為任何原因而中斷時收到通知。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-181">Your app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="fb0e5-182">註冊 LocatabilityChanged 事件，以偵測裝置在世界中尋找本身的能力變更。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-182">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="fb0e5-183">從 **AppMain：： SetHolographicSpace：**</span><span class="sxs-lookup"><span data-stu-id="fb0e5-183">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="fb0e5-184">然後，請使用此事件來判斷何時無法將靜止的全像全球呈現。</span><span class="sxs-lookup"><span data-stu-id="fb0e5-184">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb0e5-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb0e5-185">See also</span></span>
* [<span data-ttu-id="fb0e5-186">DirectX 中的呈現</span><span class="sxs-lookup"><span data-stu-id="fb0e5-186">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="fb0e5-187">DirectX 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="fb0e5-187">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)