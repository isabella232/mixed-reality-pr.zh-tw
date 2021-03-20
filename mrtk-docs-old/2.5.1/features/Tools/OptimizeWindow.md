---
title: OptimizeWindow
description: MRTK 中的檔優化視窗
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 89272df3e8eb4c944099559d926949095df44db4
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683981"
---
# <a name="optimize-window"></a><span data-ttu-id="73b47-104">優化視窗</span><span class="sxs-lookup"><span data-stu-id="73b47-104">Optimize window</span></span>

<span data-ttu-id="73b47-105">[MRTK 優化] 視窗是一種公用程式，可協助自動化和通知設定混合現實專案的程式，以達到 Unity 的最佳 [效能](../../performance/PerfGettingStarted.md) 。</span><span class="sxs-lookup"><span data-stu-id="73b47-105">The MRTK Optimize Window is a utility to help automate and inform in the process of configuring a mixed reality project for best [performance](../../performance/PerfGettingStarted.md) in Unity.</span></span> <span data-ttu-id="73b47-106">此工具通常著重于將設定設為正確預設值的設定，可節省處理的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="73b47-106">This tool generally focuses on rendering configurations that when set to the correct preset can save milliseconds of processing.</span></span>

<span data-ttu-id="73b47-107">作用中的 *組建目標* 是目前由專案進行編譯的 [組建平臺](https://docs.unity3d.com/Manual/BuildSettings.html) 。</span><span class="sxs-lookup"><span data-stu-id="73b47-107">The *Active Build Target* is the [build platform currently targeted](https://docs.unity3d.com/Manual/BuildSettings.html) by the project for compiling.</span></span>

<span data-ttu-id="73b47-108">*效能目標* 會指示優化工具的目標裝置端點類型。</span><span class="sxs-lookup"><span data-stu-id="73b47-108">The *Performance Target* instructs the optimize tool on what kind of device endpoints to target.</span></span>

- <span data-ttu-id="73b47-109">*AR 耳機* 是行動裝置類別的裝置，例如 HoloLens</span><span class="sxs-lookup"><span data-stu-id="73b47-109">*AR Headsets* are mobile-class devices, such as HoloLens</span></span>
- <span data-ttu-id="73b47-110">*VR 獨立式* 是行動裝置類別的裝置，例如 Oculus Go 或尋找</span><span class="sxs-lookup"><span data-stu-id="73b47-110">*VR Standalone* are mobile-class devices, such as the Oculus Go or Quest</span></span>
- <span data-ttu-id="73b47-111">*VR 行動網卡* 是電腦支援的裝置，例如 Samsung 電影對白、Oculus RIFT 或 HTC Vive 等等。</span><span class="sxs-lookup"><span data-stu-id="73b47-111">*VR Tethered* are PC-powered devices, such as the Samsung Odyssey, Oculus Rift or HTC Vive etc.</span></span>

![MRTK 優化視窗效能目標](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a><span data-ttu-id="73b47-113">設定優化</span><span class="sxs-lookup"><span data-stu-id="73b47-113">Setting optimizations</span></span>

<span data-ttu-id="73b47-114">[設定優化] 索引標籤包含 Unity 專案的一些重要轉譯設定。</span><span class="sxs-lookup"><span data-stu-id="73b47-114">The settings optimization tab covers some of the important rendering configurations for a Unity project.</span></span> <span data-ttu-id="73b47-115">本節可協助自動化，並通知您應變更哪些設定，以獲得最佳的執行結果。</span><span class="sxs-lookup"><span data-stu-id="73b47-115">This section can help automate and inform you of which settings should be changed for the best performing results.</span></span>

<span data-ttu-id="73b47-116">綠色核取圖示表示已在專案/場景中為此特定設定設定最佳值。</span><span class="sxs-lookup"><span data-stu-id="73b47-116">A green check icon means that an optimal value has been configured in the project/scene for this particular setting.</span></span> <span data-ttu-id="73b47-117">黃色警告圖示表示可以改善目前的設定。</span><span class="sxs-lookup"><span data-stu-id="73b47-117">A yellow warning icon indicates the current configuration can be improved.</span></span> <span data-ttu-id="73b47-118">按一下指定區段中的相關聯按鈕，會將 Unity 專案/場景中的該設定自動設定為更理想的值。</span><span class="sxs-lookup"><span data-stu-id="73b47-118">Clicking the associated button in a given section will auto-configure that setting in the Unity project/scene to a more optimal value.</span></span>

![MRTK 優化視窗設定](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="73b47-120">單一階段實例轉譯</span><span class="sxs-lookup"><span data-stu-id="73b47-120">Single Pass Instanced rendering</span></span>

<span data-ttu-id="73b47-121">[單一傳遞實例](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 轉譯是混合現實應用程式最有效率的轉譯路徑。</span><span class="sxs-lookup"><span data-stu-id="73b47-121">[Single Pass instanced rendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) is the most efficient rendering path for mixed reality applications.</span></span> <span data-ttu-id="73b47-122">這項設定可確保轉譯管線只針對兩個眼睛執行一次，而且繪製呼叫會在兩個眼睛之間進行具現化。</span><span class="sxs-lookup"><span data-stu-id="73b47-122">This configuration ensures the render pipeline is executed only once for both eyes and that draw calls are instanced across both eyes.</span></span>

### <a name="depth-buffer-sharing"></a><span data-ttu-id="73b47-123">深度緩衝區共用</span><span class="sxs-lookup"><span data-stu-id="73b47-123">Depth buffer sharing</span></span>

<span data-ttu-id="73b47-124">為了改善全像全 [像影像，](../../performance/hologram-Stabilization.md)開發人員可以共用應用程式的深度緩衝區，以提供平臺資訊給要在轉譯的場景中穩定的位置和位置。</span><span class="sxs-lookup"><span data-stu-id="73b47-124">To improve [hologram stabilization](../../performance/hologram-Stabilization.md), developers can share the application's depth buffer which gives the platform information on where and what holograms to stabilize in the rendered scene.</span></span>

### <a name="depth-buffer-format"></a><span data-ttu-id="73b47-125">深度緩衝區格式</span><span class="sxs-lookup"><span data-stu-id="73b47-125">Depth buffer format</span></span>

<span data-ttu-id="73b47-126">此外，對於 *AR 耳機*，建議在啟用深度緩衝區共用時使用16位深度格式，相較于24位。</span><span class="sxs-lookup"><span data-stu-id="73b47-126">Furthermore, for *AR Headsets*, it is recommended to utilize a 16-bit depth format when enabling depth buffer sharing compared to 24-bit.</span></span> <span data-ttu-id="73b47-127">這表示較低的精確度，但會節省效能。</span><span class="sxs-lookup"><span data-stu-id="73b47-127">This means lower precision but saves on performance.</span></span> <span data-ttu-id="73b47-128">如果因為計算圖元深度的精確度較不精確而發生 [z 的](https://en.wikipedia.org/wiki/Z-fighting) 問題，建議您將距離最接近相機的 [剪切平面](https://docs.unity3d.com/Manual/class-Camera.html) 移 (例如：50m，而不是變更為 1000m) 。</span><span class="sxs-lookup"><span data-stu-id="73b47-128">If [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) occurs because there is less precision in calculating depth for pixels, then it is recommended to move the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) closer to the camera (ex: 50m instead of 1000m).</span></span>

> [!NOTE]
> <span data-ttu-id="73b47-129">如果使用 *16 位深度格式*，則樣板緩衝區所需的效果將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。</span><span class="sxs-lookup"><span data-stu-id="73b47-129">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="73b47-130">相反地，選取 *24 位深度格式* 通常會建立 [8 位的樣板緩衝區](https://docs.unity3d.com/Manual/SL-Stencil.html)（如果適用于端點圖形平台）。</span><span class="sxs-lookup"><span data-stu-id="73b47-130">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html), if applicable on the endpoint graphics platform.</span></span>
>
> <span data-ttu-id="73b47-131">如果使用需要樣板緩衝區的 [遮罩元件](https://docs.unity3d.com/Manual/script-Mask.html) ，請考慮改用 [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) ，這不需要樣板緩衝區，因此可與 *16 位深度格式* 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="73b47-131">If using a [Mask component](https://docs.unity3d.com/Manual/script-Mask.html) which requires the stencil buffer, consider using [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) instead, which does not require the stencil buffer and thus can be used in conjunction with a *16-bit depth format*.</span></span>

### <a name="real-time-global-illumination"></a><span data-ttu-id="73b47-132">即時全球照明</span><span class="sxs-lookup"><span data-stu-id="73b47-132">Real-time Global Illumination</span></span>

<span data-ttu-id="73b47-133">Unity 中的[即時全球照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供絕佳的美觀結果，但代價很高。</span><span class="sxs-lookup"><span data-stu-id="73b47-133">[Real-time Global illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide fantastic aesthetic results but at a very high cost.</span></span> <span data-ttu-id="73b47-134">全球照明照明在混合現實中相當昂貴，因此建議您在開發期間停用這項功能。</span><span class="sxs-lookup"><span data-stu-id="73b47-134">Global illumination lighting is very expensive in mixed reality and thus it is recommended to disable this feature in development.</span></span>

> [!NOTE]
> <span data-ttu-id="73b47-135">Unity 中的全域照明設定是針對每個場景設定，而不是在整個專案中進行一次。</span><span class="sxs-lookup"><span data-stu-id="73b47-135">Global illumination settings in Unity are set per-scene and not once across the entire project.</span></span>

## <a name="scene-analysis"></a><span data-ttu-id="73b47-136">場景分析</span><span class="sxs-lookup"><span data-stu-id="73b47-136">Scene analysis</span></span>

<span data-ttu-id="73b47-137">[ *場景分析* ] 索引標籤的設計目的，是要通知開發人員目前在場景中的元素，可能會對效能造成最大的影響。</span><span class="sxs-lookup"><span data-stu-id="73b47-137">The *Scene Analysis* tab is designed to inform developers on which elements currently in the scene will likely have the most impact on performance.</span></span>

![MRTK 優化視窗場景分析](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a><span data-ttu-id="73b47-139">光源分析</span><span class="sxs-lookup"><span data-stu-id="73b47-139">Lighting analysis</span></span>

<span data-ttu-id="73b47-140">本節將檢查目前在場景中的燈數目，以及應該停用陰影的任何燈光。</span><span class="sxs-lookup"><span data-stu-id="73b47-140">This section will examine the number of lights currently in the scene, as well as any lights that should disable shadows.</span></span> <span data-ttu-id="73b47-141">陰影轉換是非常耗費資源的作業。</span><span class="sxs-lookup"><span data-stu-id="73b47-141">Shadow casting is a very expensive operation.</span></span>

### <a name="polygon-count-analysis"></a><span data-ttu-id="73b47-142">多邊形計數分析</span><span class="sxs-lookup"><span data-stu-id="73b47-142">Polygon count analysis</span></span>

<span data-ttu-id="73b47-143">此工具也會提供多邊形計數統計資料。</span><span class="sxs-lookup"><span data-stu-id="73b47-143">The tool also provides polygon count statistics.</span></span> <span data-ttu-id="73b47-144">快速識別哪些 Gameobject 在指定場景中具有最高的多邊形複雜度以進行優化，可能會非常有説明。</span><span class="sxs-lookup"><span data-stu-id="73b47-144">It can be very helpful to quickly identify which GameObjects have the highest polygon complexity in a given scene to target for optimizations.</span></span>

### <a name="unity-ui-raycast-analysis"></a><span data-ttu-id="73b47-145">Unity UI raycast 分析</span><span class="sxs-lookup"><span data-stu-id="73b47-145">Unity UI raycast analysis</span></span>

<span data-ttu-id="73b47-146">圖形 raycast 作業會在 MRTK 中針對每個指標執行，以判斷是否有任何 Unity UI 元素成為焦點。</span><span class="sxs-lookup"><span data-stu-id="73b47-146">Graphics raycast operations are performed per pointer in MRTK to determine if any Unity UI elements are in focus.</span></span> <span data-ttu-id="73b47-147">這些 raycasts 可能相當昂貴，而且為了協助改善效能，不需要在結果中傳回的 UI 元素應該停用為 raycast 目標。</span><span class="sxs-lookup"><span data-stu-id="73b47-147">These raycasts can be quite expensive and to help improve performance, UI elements that do not need to be returned in the results should be disabled as raycast targets.</span></span> <span data-ttu-id="73b47-148">每個 [圖形](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) 元素都有 [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) 屬性。</span><span class="sxs-lookup"><span data-stu-id="73b47-148">Every [Graphic](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) element has a [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) property.</span></span> <span data-ttu-id="73b47-149">此工具會搜尋已啟用這個屬性的文字 UI 元素，因此可能會被停用。</span><span class="sxs-lookup"><span data-stu-id="73b47-149">This tool will search for text UI elements that have this property enabled and thus are likely candidates to be disabled.</span></span>

## <a name="shader-analysis"></a><span data-ttu-id="73b47-150">著色器分析</span><span class="sxs-lookup"><span data-stu-id="73b47-150">Shader analysis</span></span>

<span data-ttu-id="73b47-151">[Unity 標準著色器](https://docs.unity3d.com/Manual/shader-StandardShader.html)可以為遊戲產生非常高品質的視覺效果結果，但通常不適合混合現實應用程式的效能需求，特別是因為這類應用程式通常是 GPU 界限。</span><span class="sxs-lookup"><span data-stu-id="73b47-151">The [Unity Standard shader](https://docs.unity3d.com/Manual/shader-StandardShader.html) can produce very high quality visual results for games but is not generally best suited for the performance needs of mixed reality applications, especially since such applications are generally GPU bounded.</span></span> <span data-ttu-id="73b47-152">因此，建議開發人員利用 [MRTK 標準著色器](../rendering/MRTKStandardShader.md) 來平衡美學 & 圖形功能與效能。</span><span class="sxs-lookup"><span data-stu-id="73b47-152">Thus, it is recommended to developers to utilize the [MRTK Standard shader](../rendering/MRTKStandardShader.md) to balance aesthetics & graphical features with performance.</span></span>

<span data-ttu-id="73b47-153">[ *著色器分析* ] 索引標籤會使用 Unity 標準著色器來掃描目前專案的物料資產資料夾，或在需要時，使用「混合現實」工具組提供著色器的所有材質。</span><span class="sxs-lookup"><span data-stu-id="73b47-153">The *Shader Analysis* tab scans the current project's Asset folder for materials using the Unity Standard shader or if desired, all materials not using Mixed Reality Toolkit provided shaders.</span></span> <span data-ttu-id="73b47-154">一旦探索到之後，開發人員就可以使用適當的按鈕來轉換所有材質或個別轉換。</span><span class="sxs-lookup"><span data-stu-id="73b47-154">Once discovered, developers can convert all materials or convert individually using the appropriate buttons.</span></span>

![MRTK 優化視窗著色器分析](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a><span data-ttu-id="73b47-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73b47-156">See also</span></span>

- [<span data-ttu-id="73b47-157">效能</span><span class="sxs-lookup"><span data-stu-id="73b47-157">Performance</span></span>](../../performance/PerfGettingStarted.md)
- [<span data-ttu-id="73b47-158">全像穩定</span><span class="sxs-lookup"><span data-stu-id="73b47-158">Hologram Stabilization</span></span>](../../performance/hologram-stabilization.md)
