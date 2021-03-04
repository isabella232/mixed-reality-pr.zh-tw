---
title: UsingVisualProfiler
description: 在 MRTK 中使用 Visual profiler 的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 8356b404416ffc7b9818ed7fb79e1c0f36d76a59
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780649"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="73d8f-104">使用 visual profiler</span><span class="sxs-lookup"><span data-stu-id="73d8f-104">Using the visual profiler</span></span>

<span data-ttu-id="73d8f-105">VisualProfiler 可讓您輕鬆地在應用程式內查看混合現實應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="73d8f-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="73d8f-106">所有混合現實工具組平臺都支援分析工具，包括：</span><span class="sxs-lookup"><span data-stu-id="73d8f-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="73d8f-107">Microsoft HoloLens (第1代) </span><span class="sxs-lookup"><span data-stu-id="73d8f-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="73d8f-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="73d8f-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="73d8f-109">Windows Mixed Reality 沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="73d8f-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="73d8f-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="73d8f-110">OpenVR</span></span>

<span data-ttu-id="73d8f-111">開發應用程式時，請將焦點放在場景的多個部分，因為 Visual Profiler 會顯示相對於目前視圖的資料。</span><span class="sxs-lookup"><span data-stu-id="73d8f-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73d8f-112">使用複雜物件、粒子效果或活動將注意力集中在場景的部分。</span><span class="sxs-lookup"><span data-stu-id="73d8f-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="73d8f-113">這些因素和其他因素通常有助於降低應用程式效能，而不是理想的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="73d8f-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="73d8f-114">Visual profiler 介面</span><span class="sxs-lookup"><span data-stu-id="73d8f-114">Visual profiler interface</span></span>

![Visual Profiler 介面](../Images/Diagnostics/VisualProfiler.png)

<span data-ttu-id="73d8f-116">Visual Profiler 介面包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="73d8f-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="73d8f-117">畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="73d8f-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="73d8f-118">畫面格時間</span><span class="sxs-lookup"><span data-stu-id="73d8f-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="73d8f-119">框架圖形</span><span class="sxs-lookup"><span data-stu-id="73d8f-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="73d8f-120">記憶體使用率</span><span class="sxs-lookup"><span data-stu-id="73d8f-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="73d8f-121">畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="73d8f-121">Frame rate</span></span>

<span data-ttu-id="73d8f-122">介面左上角是畫面播放速率，以每秒的畫面格速率來測量。</span><span class="sxs-lookup"><span data-stu-id="73d8f-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="73d8f-123">為了獲得最佳的使用者體驗和緩和，此值應該越高越好。</span><span class="sxs-lookup"><span data-stu-id="73d8f-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="73d8f-124">特定平臺和硬體設定在可達成的最大畫面播放速率中扮演著重要的角色。</span><span class="sxs-lookup"><span data-stu-id="73d8f-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="73d8f-125">一些常見的目標值包括：</span><span class="sxs-lookup"><span data-stu-id="73d8f-125">Some common target values include:</span></span>

- <span data-ttu-id="73d8f-126">Microsoft HoloLens：60</span><span class="sxs-lookup"><span data-stu-id="73d8f-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="73d8f-127">Windows Mixed Reality Ultra：90</span><span class="sxs-lookup"><span data-stu-id="73d8f-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="73d8f-128">由於在 [預設的 MRC 為使用中時，在 HoloLens 上的畫面播放速率節流](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)，因此當影片和相片被捕獲時，visual profiler 會自行隱藏。</span><span class="sxs-lookup"><span data-stu-id="73d8f-128">Due to [frame rate throttling on HoloLens when default MRC is active](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="73d8f-129">這項設定可以在診斷系統設定檔中覆寫。</span><span class="sxs-lookup"><span data-stu-id="73d8f-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="73d8f-130">畫面格時間</span><span class="sxs-lookup"><span data-stu-id="73d8f-130">Frame time</span></span>

<span data-ttu-id="73d8f-131">畫面播放速率的右邊是花費在 CPU 的畫面格時間（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="73d8f-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="73d8f-132">為了達到先前所述的目標畫面播放速率，應用程式可以在每個框架中花費下列時間長度：</span><span class="sxs-lookup"><span data-stu-id="73d8f-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="73d8f-133">60 fps：16.6 毫秒</span><span class="sxs-lookup"><span data-stu-id="73d8f-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="73d8f-134">90 fps：11.1 毫秒</span><span class="sxs-lookup"><span data-stu-id="73d8f-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="73d8f-135">已規劃在未來的版本中新增 GPU 時間。</span><span class="sxs-lookup"><span data-stu-id="73d8f-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="73d8f-136">框架圖形</span><span class="sxs-lookup"><span data-stu-id="73d8f-136">Frame graph</span></span>

<span data-ttu-id="73d8f-137">框架圖形提供應用程式框架速率歷程記錄的圖形顯示。</span><span class="sxs-lookup"><span data-stu-id="73d8f-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Visual Profiler 框架圖形](../Images/Diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="73d8f-139">使用應用程式時，請尋找遺漏的框架，指出應用程式未達到其目標畫面播放速率，而且可能需要優化工作。</span><span class="sxs-lookup"><span data-stu-id="73d8f-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="73d8f-140">記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="73d8f-140">Memory utilization</span></span>

<span data-ttu-id="73d8f-141">記憶體使用量顯示可讓您輕鬆瞭解目前的視圖如何影響應用程式的記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="73d8f-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Visual Profiler 框架圖形](../Images/Diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="73d8f-143">使用應用程式時，請尋找總記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="73d8f-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="73d8f-144">關鍵指標包括接近記憶體限制，以及快速變更使用方式。</span><span class="sxs-lookup"><span data-stu-id="73d8f-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="73d8f-145">自訂 visual profiler</span><span class="sxs-lookup"><span data-stu-id="73d8f-145">Customizing the visual profiler</span></span>

<span data-ttu-id="73d8f-146">您可以透過診斷系統設定檔自訂 Visual Profiler 的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="73d8f-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="73d8f-147">如需詳細資訊，請參閱設定 [診斷系統](ConfiguringDiagnostics.md) 。</span><span class="sxs-lookup"><span data-stu-id="73d8f-147">Please see [Configuring the Diagnostics System](ConfiguringDiagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="73d8f-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73d8f-148">See also</span></span>

- [<span data-ttu-id="73d8f-149">診斷系統</span><span class="sxs-lookup"><span data-stu-id="73d8f-149">Diagnostics System</span></span>](DiagnosticsSystemGettingStarted.md)
- [<span data-ttu-id="73d8f-150">設定診斷系統</span><span class="sxs-lookup"><span data-stu-id="73d8f-150">Configuring the Diagnostics System</span></span>](ConfiguringDiagnostics.md)
