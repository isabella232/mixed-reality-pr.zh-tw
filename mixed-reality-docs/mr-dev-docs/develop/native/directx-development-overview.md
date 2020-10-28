---
title: 原生開發概觀
description: 直接使用 Windows Mixed Reality Api 來建立以 DirectX 為基礎的混合現實引擎。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX，全像攝影轉譯、原生、原生應用程式、WinRT、WinRT 應用程式、平臺 Api、自訂引擎、中介軟體
ms.openlocfilehash: fb51dfe15de26b80db255f0daca69e913f9ad35c
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903124"
---
# <a name="native-development-overview"></a><span data-ttu-id="8c6b6-104">原生開發概觀</span><span class="sxs-lookup"><span data-stu-id="8c6b6-104">Native development overview</span></span>

![原生橫幅標誌](../images/native_logo_banner.png)

<span data-ttu-id="8c6b6-106">[Unity](../unity/unity-development-overview.md)或[Unreal](../unreal/unreal-development-overview.md)這類3d 引擎不是唯一開放給您的混合現實開發途徑。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="8c6b6-107">您也可以透過使用 DirectX 11 或 DirectX 12 的 Windows Mixed Reality Api，直接撰寫程式碼，來建立混合的現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-107">You can also create Mixed Reality apps by directly coding to the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="8c6b6-108">藉由直接運用平臺，您基本上就是建立自己的中介軟體或架構。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-108">By leveraging the platform directly, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="8c6b6-109">如果您有想要維護的現有 WinRT 專案，請前往我們的主要 [winrt 檔](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="8c6b6-110">開發檢查點</span><span class="sxs-lookup"><span data-stu-id="8c6b6-110">Development checkpoints</span></span>

<span data-ttu-id="8c6b6-111">使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="8c6b6-112">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="8c6b6-112">1. Getting started</span></span>

<span data-ttu-id="8c6b6-113">Windows Mixed Reality 支援 [兩種類型的應用程式](../../design/app-views.md)：</span><span class="sxs-lookup"><span data-stu-id="8c6b6-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="8c6b6-114"> (UWP 或 Win32) 的 **混合現實應用程式** ，其使用 [HolographicSpace API](getting-a-holographicspace.md)或 [OpenXR api](openxr.md) ，將 [沉浸式視圖](../../design/app-views.md)轉譯為填滿耳機顯示器的使用者</span><span class="sxs-lookup"><span data-stu-id="8c6b6-114">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="8c6b6-115">**2d 應用程式** (UWP) ，其使用 DIRECTX、XAML 或其他架構在 Windows Mixed Reality 首頁的平板上轉譯 [2d 視圖](../../design/app-views.md#2d-views)</span><span class="sxs-lookup"><span data-stu-id="8c6b6-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="8c6b6-116">[2d 視圖和沉浸式視圖](../../design/app-views.md)的 DirectX 開發之間的差異，主要是要考慮全像攝影轉譯和空間輸入。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="8c6b6-117">您的 UWP 應用程式 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 或您的 Win32 應用程式的 HWND 是必要的，而且維持在相同的狀態。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="8c6b6-118">適用于您應用程式的 WinRT Api 也是如此。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="8c6b6-119">但是，您必須使用這些 Api 的不同子集來利用全像全像的功能。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="8c6b6-120">例如，目前的 swapchain 和框架是由系統針對全像的應用程式管理，以便啟用姿勢預測的框架迴圈。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-120">For example, the swapchain and frame present is managed by the system for holographic applications in order to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="8c6b6-121">2.核心基本要素</span><span class="sxs-lookup"><span data-stu-id="8c6b6-121">2. Core building blocks</span></span>

<span data-ttu-id="8c6b6-122">Windows Mixed Reality 的應用程式會使用下列 Api 來建立 HoloLens 和其他沉浸式耳機的 [混合現實](../../discover/mixed-reality.md) 體驗：</span><span class="sxs-lookup"><span data-stu-id="8c6b6-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="8c6b6-123">功能</span><span class="sxs-lookup"><span data-stu-id="8c6b6-123">Feature</span></span>  |  <span data-ttu-id="8c6b6-124">功能</span><span class="sxs-lookup"><span data-stu-id="8c6b6-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="8c6b6-125">目光</span><span class="sxs-lookup"><span data-stu-id="8c6b6-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="8c6b6-126">讓使用者藉由注視全像投影而將其定為目標</span><span class="sxs-lookup"><span data-stu-id="8c6b6-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="8c6b6-127">手勢</span><span class="sxs-lookup"><span data-stu-id="8c6b6-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="8c6b6-128">將空間動作新增至您的應用程式</span><span class="sxs-lookup"><span data-stu-id="8c6b6-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="8c6b6-129">全像攝影的呈現</span><span class="sxs-lookup"><span data-stu-id="8c6b6-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="8c6b6-130">在您的使用者附近的確切位置繪製全像影像</span><span class="sxs-lookup"><span data-stu-id="8c6b6-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="8c6b6-131">移動控制器</span><span class="sxs-lookup"><span data-stu-id="8c6b6-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="8c6b6-132">讓您的使用者在您的混合現實環境中採取行動</span><span class="sxs-lookup"><span data-stu-id="8c6b6-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="8c6b6-133">空間對應</span><span class="sxs-lookup"><span data-stu-id="8c6b6-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="8c6b6-134">透過虛擬網格重疊對應您的實體空間，以標示環境的界限</span><span class="sxs-lookup"><span data-stu-id="8c6b6-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="8c6b6-135">語音</span><span class="sxs-lookup"><span data-stu-id="8c6b6-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="8c6b6-136">擷取使用者說出的關鍵字、片語和指令</span><span class="sxs-lookup"><span data-stu-id="8c6b6-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="8c6b6-137">您可以在 OpenXR [藍圖](openxr.md#roadmap) 檔中找到即將推出和開發中的核心功能。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="8c6b6-138">3. 部署和測試</span><span class="sxs-lookup"><span data-stu-id="8c6b6-138">3. Deploying and testing</span></span>

<span data-ttu-id="8c6b6-139">您可以在 HoloLens 2 上使用 OpenXR 或在電腦上使用 Windows Mixed Reality 沉浸式頭戴裝置進行開發。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-139">You can develop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset on the desktop.</span></span>  <span data-ttu-id="8c6b6-140">如果您沒有耳機的存取權，您可以改用 [HoloLens 2 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或 [Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 模擬器。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="8c6b6-141">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="8c6b6-141">What's next?</span></span>

<span data-ttu-id="8c6b6-142">開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-142">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="8c6b6-143">完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。</span><span class="sxs-lookup"><span data-stu-id="8c6b6-143">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="8c6b6-144">請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！</span><span class="sxs-lookup"><span data-stu-id="8c6b6-144">Note that these topics and resources are not in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8c6b6-145">其他資源</span><span class="sxs-lookup"><span data-stu-id="8c6b6-145">Additional resources</span></span>

<span data-ttu-id="8c6b6-146">如果您想要 OpenXR 遊戲的等級，請參閱下列連結：</span><span class="sxs-lookup"><span data-stu-id="8c6b6-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="8c6b6-147">OpenXR 最佳做法</span><span class="sxs-lookup"><span data-stu-id="8c6b6-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="8c6b6-148">OpenXR 效能</span><span class="sxs-lookup"><span data-stu-id="8c6b6-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="8c6b6-149">對 OpenXR 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="8c6b6-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="8c6b6-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c6b6-150">See also</span></span>
* [<span data-ttu-id="8c6b6-151">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="8c6b6-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="8c6b6-152">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="8c6b6-152">App views</span></span>](../../design/app-views.md)
