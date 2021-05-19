---
title: 設定診斷
description: 在 MRTK 中設定診斷的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 2ff761baa728017eb011cb9105cf203e6e3a72e4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144178"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="a9ca4-104">設定診斷系統</span><span class="sxs-lookup"><span data-stu-id="a9ca4-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="a9ca4-105">一般設定</span><span class="sxs-lookup"><span data-stu-id="a9ca4-105">General settings</span></span>

![診斷一般設定](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="a9ca4-107">啟用詳細資訊記錄</span><span class="sxs-lookup"><span data-stu-id="a9ca4-107">Enable verbose logging</span></span>

<span data-ttu-id="a9ca4-108">指出是否將啟用詳細資訊 MRTK 記錄。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="a9ca4-109">這會預設為 false，但可以開啟以取得詳細的追蹤，讓 MRTK 小組能夠進行偵測/深入探索問題。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="a9ca4-110">例如，當您提出問題時，請從編輯器或從) 播放程式將 Unity player 記錄 (附加到，以協助縮小 bug 和問題的來源。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="a9ca4-111">請注意，此選項獨立于診斷系統是否已啟用，這會顯示在診斷系統底下，因為它是記錄選項，但最終會以較高的層級運作，因為它會影響整個 MRTK 程式碼基底的記錄。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="a9ca4-112">顯示診斷</span><span class="sxs-lookup"><span data-stu-id="a9ca4-112">Show diagnostics</span></span>

<span data-ttu-id="a9ca4-113">指出診斷系統是否要顯示設定的診斷選項。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="a9ca4-114">停用時，所有設定的診斷選項都會隱藏。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="a9ca4-115">Profiler 設定</span><span class="sxs-lookup"><span data-stu-id="a9ca4-115">Profiler settings</span></span>

![診斷 Profiler 設定](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="a9ca4-117">顯示 profiler</span><span class="sxs-lookup"><span data-stu-id="a9ca4-117">Show profiler</span></span>

<span data-ttu-id="a9ca4-118">指出是否要顯示 Visual Profiler。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="a9ca4-119">框架取樣率</span><span class="sxs-lookup"><span data-stu-id="a9ca4-119">Frame sample rate</span></span>

<span data-ttu-id="a9ca4-120">收集畫面播放速率計算框架的時間長度（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="a9ca4-121">範圍為0到5秒。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="a9ca4-122">視窗錨點</span><span class="sxs-lookup"><span data-stu-id="a9ca4-122">Window anchor</span></span>

<span data-ttu-id="a9ca4-123">分析工具視窗應該錨定的視圖埠部分。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="a9ca4-124">預設值為 [下置]。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="a9ca4-125">視窗位移</span><span class="sxs-lookup"><span data-stu-id="a9ca4-125">Window offset</span></span>

<span data-ttu-id="a9ca4-126">從 view 埠中央算出的位移，以放置 Visual Profiler。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="a9ca4-127">位移將會以 *視窗錨點* 屬性的方向進行。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="a9ca4-128">視窗比例</span><span class="sxs-lookup"><span data-stu-id="a9ca4-128">Window scale</span></span>

<span data-ttu-id="a9ca4-129">套用至 profiler 視窗的大小乘數。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="a9ca4-130">例如，將此值設定為2會將視窗大小加倍。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="a9ca4-131">視窗遵循速度</span><span class="sxs-lookup"><span data-stu-id="a9ca4-131">Window follow speed</span></span>

<span data-ttu-id="a9ca4-132">移動分析工具視窗以維持查看埠內部可見度的速度。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="a9ca4-133">以程式設計方式控制診斷系統</span><span class="sxs-lookup"><span data-stu-id="a9ca4-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="a9ca4-134">您也可以在執行時間切換診斷系統和 profiler 的可見度。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="a9ca4-135">例如，下列程式碼將會隱藏診斷系統和 profiler。</span><span class="sxs-lookup"><span data-stu-id="a9ca4-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="a9ca4-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9ca4-136">See also</span></span>

- [<span data-ttu-id="a9ca4-137">診斷系統</span><span class="sxs-lookup"><span data-stu-id="a9ca4-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="a9ca4-138">使用 Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="a9ca4-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
