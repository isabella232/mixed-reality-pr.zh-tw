---
title: 原生開發概觀
description: 直接使用 Windows Mixed Reality Api 來建立以 DirectX 為基礎的混合現實引擎。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX，全像攝影轉譯、原生、原生應用程式、WinRT、WinRT 應用程式、平臺 Api、自訂引擎、中介軟體、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 493715660ff8df79df25e09c82fe48b863053ed3
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613072"
---
# <a name="native-development-overview"></a><span data-ttu-id="dfa34-104">原生開發概觀</span><span class="sxs-lookup"><span data-stu-id="dfa34-104">Native development overview</span></span>

![原生橫幅標誌](../images/native_logo_banner.png)

<span data-ttu-id="dfa34-106">[Unity](../unity/unity-development-overview.md)或[Unreal](../unreal/unreal-development-overview.md)這類3d 引擎不是唯一開放給您的混合現實開發途徑。</span><span class="sxs-lookup"><span data-stu-id="dfa34-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="dfa34-107">您也可以使用 Windows Mixed Reality Api 搭配 DirectX 11 或 DirectX 12 來建立混合的現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="dfa34-107">You can also create Mixed Reality apps using the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="dfa34-108">藉由進入平臺來源，您基本上就是建立自己的中介軟體或架構。</span><span class="sxs-lookup"><span data-stu-id="dfa34-108">By going to the platform source, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="dfa34-109">如果您有想要維護的現有 WinRT 專案，請前往我們的主要 [winrt 檔](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="dfa34-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="dfa34-110">開發檢查點</span><span class="sxs-lookup"><span data-stu-id="dfa34-110">Development checkpoints</span></span>

<span data-ttu-id="dfa34-111">使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。</span><span class="sxs-lookup"><span data-stu-id="dfa34-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="dfa34-112">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="dfa34-112">1. Getting started</span></span>

<span data-ttu-id="dfa34-113">Windows Mixed Reality 支援 [兩種類型的應用程式](../../design/app-views.md)：</span><span class="sxs-lookup"><span data-stu-id="dfa34-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="dfa34-114">UWP 或 Win32 **混合現實應用程式，這些應用程式** 會使用 [HolographicSpace API](getting-a-holographicspace.md)或 [OpenXR api](openxr.md)來呈現可填滿耳機顯示器的 [沉浸式視圖](../../design/app-views.md)</span><span class="sxs-lookup"><span data-stu-id="dfa34-114">UWP or Win32 **Mixed Reality applications** that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) that fills the headset display</span></span>
* <span data-ttu-id="dfa34-115">**2d 應用程式** (UWP) ，其使用 DIRECTX、XAML 或其他架構在 Windows Mixed Reality 首頁的平板上轉譯 [2d 視圖](../../design/app-views.md#2d-views)</span><span class="sxs-lookup"><span data-stu-id="dfa34-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="dfa34-116">[2d 視圖和沉浸式視圖](../../design/app-views.md)的 DirectX 開發之間的差異，主要是要考慮全像攝影轉譯和空間輸入。</span><span class="sxs-lookup"><span data-stu-id="dfa34-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="dfa34-117">您的 UWP 應用程式 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 或您的 Win32 應用程式的 HWND 是必要的，而且維持在相同的狀態。</span><span class="sxs-lookup"><span data-stu-id="dfa34-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="dfa34-118">適用于您應用程式的 WinRT Api 也是如此。</span><span class="sxs-lookup"><span data-stu-id="dfa34-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="dfa34-119">但是，您必須使用這些 Api 的不同子集來利用全像全像的功能。</span><span class="sxs-lookup"><span data-stu-id="dfa34-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="dfa34-120">例如，「全像」應用程式的系統會管理 swapchain 和框架，以啟用姿勢預測的框架迴圈。</span><span class="sxs-lookup"><span data-stu-id="dfa34-120">For example, the system for holographic applications manages the swapchain and frame present to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="dfa34-121">2.核心基本要素</span><span class="sxs-lookup"><span data-stu-id="dfa34-121">2. Core building blocks</span></span>

<span data-ttu-id="dfa34-122">Windows Mixed Reality 的應用程式會使用下列 Api 來建立 HoloLens 和其他沉浸式耳機的 [混合現實](../../discover/mixed-reality.md) 體驗：</span><span class="sxs-lookup"><span data-stu-id="dfa34-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="dfa34-123">功能</span><span class="sxs-lookup"><span data-stu-id="dfa34-123">Feature</span></span>  |  <span data-ttu-id="dfa34-124">功能</span><span class="sxs-lookup"><span data-stu-id="dfa34-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="dfa34-125">目光</span><span class="sxs-lookup"><span data-stu-id="dfa34-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="dfa34-126">讓使用者藉由注視全像投影而將其定為目標</span><span class="sxs-lookup"><span data-stu-id="dfa34-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="dfa34-127">手勢</span><span class="sxs-lookup"><span data-stu-id="dfa34-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="dfa34-128">將空間動作新增至您的應用程式</span><span class="sxs-lookup"><span data-stu-id="dfa34-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="dfa34-129">全像攝影的呈現</span><span class="sxs-lookup"><span data-stu-id="dfa34-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="dfa34-130">在您的使用者附近的確切位置繪製全像影像</span><span class="sxs-lookup"><span data-stu-id="dfa34-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="dfa34-131">移動控制器</span><span class="sxs-lookup"><span data-stu-id="dfa34-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="dfa34-132">讓您的使用者在您的混合現實環境中採取行動</span><span class="sxs-lookup"><span data-stu-id="dfa34-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="dfa34-133">空間對應</span><span class="sxs-lookup"><span data-stu-id="dfa34-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="dfa34-134">透過虛擬網格重疊對應您的實體空間，以標示環境的界限</span><span class="sxs-lookup"><span data-stu-id="dfa34-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="dfa34-135">語音</span><span class="sxs-lookup"><span data-stu-id="dfa34-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="dfa34-136">擷取使用者說出的關鍵字、片語和指令</span><span class="sxs-lookup"><span data-stu-id="dfa34-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="dfa34-137">您可以在 OpenXR [藍圖](openxr.md#roadmap) 檔中找到即將推出和開發中的核心功能。</span><span class="sxs-lookup"><span data-stu-id="dfa34-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="dfa34-138">3. 部署和測試</span><span class="sxs-lookup"><span data-stu-id="dfa34-138">3. Deploying and testing</span></span>

<span data-ttu-id="dfa34-139">您可以在 HoloLens 2 上使用 OpenXR 或 Windows Mixed Reality 沉浸式耳機開發桌上型電腦。</span><span class="sxs-lookup"><span data-stu-id="dfa34-139">You can develop on a desktop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset.</span></span>  <span data-ttu-id="dfa34-140">如果您沒有耳機的存取權，您可以改用 [HoloLens 2 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或 [Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 模擬器。</span><span class="sxs-lookup"><span data-stu-id="dfa34-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="dfa34-141">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="dfa34-141">What's next?</span></span>

<span data-ttu-id="dfa34-142">開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。</span><span class="sxs-lookup"><span data-stu-id="dfa34-142">A developer's job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="dfa34-143">下列各節會將您帶到您已完成的初學者層級內容以外的區域。</span><span class="sxs-lookup"><span data-stu-id="dfa34-143">The following sections can take you into areas beyond the beginner level material you've already completed.</span></span> <span data-ttu-id="dfa34-144">這些主題和資源不會以任何順序排列，因此您可以隨時跳到探索！</span><span class="sxs-lookup"><span data-stu-id="dfa34-144">These topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dfa34-145">其他資源</span><span class="sxs-lookup"><span data-stu-id="dfa34-145">Additional resources</span></span>

<span data-ttu-id="dfa34-146">如果您想要 OpenXR 遊戲的等級，請參閱下列連結：</span><span class="sxs-lookup"><span data-stu-id="dfa34-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="dfa34-147">OpenXR 最佳做法</span><span class="sxs-lookup"><span data-stu-id="dfa34-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="dfa34-148">OpenXR 效能</span><span class="sxs-lookup"><span data-stu-id="dfa34-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="dfa34-149">對 OpenXR 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="dfa34-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="dfa34-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfa34-150">See also</span></span>
* [<span data-ttu-id="dfa34-151">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="dfa34-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="dfa34-152">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="dfa34-152">App views</span></span>](../../design/app-views.md)
