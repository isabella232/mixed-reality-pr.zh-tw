---
title: ConfiguringDiagnostics
description: 在 MRTK 中設定診斷的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 7ae5381a5660f9173bdacd25013538b8790e15ef
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780731"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="5bf7f-104">設定診斷系統</span><span class="sxs-lookup"><span data-stu-id="5bf7f-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="5bf7f-105">一般設定</span><span class="sxs-lookup"><span data-stu-id="5bf7f-105">General settings</span></span>

![診斷一般設定](../Images/Diagnostics/DiagnosticsGeneralSettings.png)

### <a name="show-diagnostics"></a><span data-ttu-id="5bf7f-107">顯示診斷</span><span class="sxs-lookup"><span data-stu-id="5bf7f-107">Show diagnostics</span></span>

<span data-ttu-id="5bf7f-108">指出診斷系統是否要顯示設定的診斷選項。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-108">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="5bf7f-109">停用時，所有設定的診斷選項都會隱藏。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-109">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="5bf7f-110">Profiler 設定</span><span class="sxs-lookup"><span data-stu-id="5bf7f-110">Profiler settings</span></span>

![診斷 Profiler 設定](../Images/Diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="5bf7f-112">顯示 profiler</span><span class="sxs-lookup"><span data-stu-id="5bf7f-112">Show profiler</span></span>

<span data-ttu-id="5bf7f-113">指出是否要顯示 Visual Profiler。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-113">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="5bf7f-114">框架取樣率</span><span class="sxs-lookup"><span data-stu-id="5bf7f-114">Frame sample rate</span></span>

<span data-ttu-id="5bf7f-115">收集畫面播放速率計算框架的時間長度（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-115">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="5bf7f-116">範圍為0到5秒。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-116">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="5bf7f-117">視窗錨點</span><span class="sxs-lookup"><span data-stu-id="5bf7f-117">Window anchor</span></span>

<span data-ttu-id="5bf7f-118">分析工具視窗應該錨定的視圖埠部分。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-118">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="5bf7f-119">預設值為 [下置]。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-119">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="5bf7f-120">視窗位移</span><span class="sxs-lookup"><span data-stu-id="5bf7f-120">Window offset</span></span>

<span data-ttu-id="5bf7f-121">從 view 埠中央算出的位移，以放置 Visual Profiler。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-121">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="5bf7f-122">位移將會以 *視窗錨點* 屬性的方向進行。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-122">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="5bf7f-123">視窗比例</span><span class="sxs-lookup"><span data-stu-id="5bf7f-123">Window scale</span></span>

<span data-ttu-id="5bf7f-124">套用至 profiler 視窗的大小乘數。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-124">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="5bf7f-125">例如，將此值設定為2會將視窗大小加倍。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-125">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="5bf7f-126">視窗遵循速度</span><span class="sxs-lookup"><span data-stu-id="5bf7f-126">Window follow speed</span></span>

<span data-ttu-id="5bf7f-127">移動分析工具視窗以維持查看埠內部可見度的速度。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-127">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="5bf7f-128">以程式設計方式控制診斷系統</span><span class="sxs-lookup"><span data-stu-id="5bf7f-128">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="5bf7f-129">您也可以在執行時間切換診斷系統和 profiler 的可見度。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-129">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="5bf7f-130">例如，下列程式碼將會隱藏診斷系統和 profiler。</span><span class="sxs-lookup"><span data-stu-id="5bf7f-130">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="5bf7f-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bf7f-131">See also</span></span>

- [<span data-ttu-id="5bf7f-132">診斷系統</span><span class="sxs-lookup"><span data-stu-id="5bf7f-132">Diagnostics System</span></span>](DiagnosticsSystemGettingStarted.md)
- [<span data-ttu-id="5bf7f-133">使用 Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="5bf7f-133">Using the Visual Profiler</span></span>](UsingVisualProfiler.md)
