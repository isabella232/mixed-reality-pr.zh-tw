---
title: 應用程式品質準則
description: 本檔說明影響混合現實應用程式品質的主要因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式品質準則、混合現實、混合現實應用程式、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: c18f4e8470f7f183fdf250472fd3a977f925dfbf
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677987"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="31d3e-104">應用程式品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-104">App quality criteria</span></span>

<span data-ttu-id="31d3e-105">本檔說明影響混合現實應用程式品質的主要因素。</span><span class="sxs-lookup"><span data-stu-id="31d3e-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="31d3e-106">針對每個因素，會提供下列資訊</span><span class="sxs-lookup"><span data-stu-id="31d3e-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="31d3e-107">總覽-品質因素的簡短描述，以及其重要性。</span><span class="sxs-lookup"><span data-stu-id="31d3e-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="31d3e-108">裝置影響-受影響的視窗混合現實裝置類型。</span><span class="sxs-lookup"><span data-stu-id="31d3e-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="31d3e-109">品質準則–如何評估品質因素。</span><span class="sxs-lookup"><span data-stu-id="31d3e-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="31d3e-110">如何測量–測量問題 (或) 經驗的方法。</span><span class="sxs-lookup"><span data-stu-id="31d3e-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="31d3e-111">建議-提供更佳使用者體驗的方法摘要。</span><span class="sxs-lookup"><span data-stu-id="31d3e-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="31d3e-112">資源-相關的開發人員和設計資源，可用於建立更好的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="31d3e-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="31d3e-113">畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="31d3e-113">Frame rate</span></span>

<span data-ttu-id="31d3e-114">畫面播放速率是全像全像要件的第一次，也是使用者的舒適。</span><span class="sxs-lookup"><span data-stu-id="31d3e-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="31d3e-115">低於建議目標的畫面播放速率可能會導致全息圖顯得抖動、對體驗的 believability 造成負面影響，並可能造成眼睛疲勞。</span><span class="sxs-lookup"><span data-stu-id="31d3e-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="31d3e-116">您在 Windows Mixed Reality 沉浸式耳機上體驗的目標畫面播放速率將會是60Hz 或90Hz，視您想要支援的 Windows Mixed Reality 相容電腦而定。</span><span class="sxs-lookup"><span data-stu-id="31d3e-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="31d3e-117">HoloLens 的目標畫面播放速率為60Hz。</span><span class="sxs-lookup"><span data-stu-id="31d3e-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-118">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-121">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-121">✔️</span></span></td>
        <td><span data-ttu-id="31d3e-122">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-123">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-123">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-124">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-124">Best</span></span>  |  <span data-ttu-id="31d3e-125">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-125">Meets</span></span> |  <span data-ttu-id="31d3e-126">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="31d3e-127">應用程式一致地符合每秒的畫面格 (FPS) 目標裝置的目標： HoloLens 上的 60fps;在 Ultra 電腦上 90fps;以及60fps 在主流電腦上。</span><span class="sxs-lookup"><span data-stu-id="31d3e-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="31d3e-128">應用程式有間歇性的框架下降不會阻礙核心體驗;或 FPS 一致地低於所需的目標，但不會妨礙應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="31d3e-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="31d3e-129">應用程式平均每10秒或更短的畫面播放速率都有下降。</span><span class="sxs-lookup"><span data-stu-id="31d3e-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-130">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-130">How to measure</span></span>

* <span data-ttu-id="31d3e-131">「系統效能」下的 [Windows 裝置入口網站](using-the-windows-device-portal.md#system-performance) 會提供即時的畫面播放速率圖形。</span><span class="sxs-lookup"><span data-stu-id="31d3e-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="31d3e-132">針對開發的偵錯工具，請在應用程式中新增畫面播放速率診斷計數器。</span><span class="sxs-lookup"><span data-stu-id="31d3e-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="31d3e-133">請參閱範例計數器的資源。</span><span class="sxs-lookup"><span data-stu-id="31d3e-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="31d3e-134">當應用程式正在執行時，可能會在裝置上經歷畫面播放速率下降，方法是將您的標題從側邊移動</span><span class="sxs-lookup"><span data-stu-id="31d3e-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="31d3e-135">如果全息圖顯示非預期的抖動移動，則低畫面播放速率或穩定性平面可能是原因。</span><span class="sxs-lookup"><span data-stu-id="31d3e-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-136">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-136">Recommendations</span></span>

* <span data-ttu-id="31d3e-137">在開發工作的開頭新增畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="31d3e-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="31d3e-138">產生下降畫面播放速率的變更應該進行評估，並適當地解析為效能錯誤。</span><span class="sxs-lookup"><span data-stu-id="31d3e-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-139">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="31d3e-140">文件</span><span class="sxs-lookup"><span data-stu-id="31d3e-140">Documentation</span></span>

* [<span data-ttu-id="31d3e-141">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="31d3e-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="31d3e-142">全像穩定性和幀的影像</span><span class="sxs-lookup"><span data-stu-id="31d3e-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="31d3e-143">資產效能預算</span><span class="sxs-lookup"><span data-stu-id="31d3e-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="31d3e-144">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="31d3e-145">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="31d3e-145">Tools and tutorials</span></span>

* [<span data-ttu-id="31d3e-146">MRToolkit，FPS 計數器顯示</span><span class="sxs-lookup"><span data-stu-id="31d3e-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="31d3e-147">MRToolkit，著色器</span><span class="sxs-lookup"><span data-stu-id="31d3e-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="31d3e-148">外部參考</span><span class="sxs-lookup"><span data-stu-id="31d3e-148">External references</span></span>

* [<span data-ttu-id="31d3e-149">Unity，將行動應用程式優化</span><span class="sxs-lookup"><span data-stu-id="31d3e-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="31d3e-150">全像投影穩定性</span><span class="sxs-lookup"><span data-stu-id="31d3e-150">Hologram stability</span></span>

<span data-ttu-id="31d3e-151">穩定的全像影像會提高應用程式的可用性和 believability，並為使用者建立更舒適的觀賞體驗。</span><span class="sxs-lookup"><span data-stu-id="31d3e-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="31d3e-152">全像應用程式開發的結果，以及裝置瞭解 (追蹤) 其環境的能力。</span><span class="sxs-lookup"><span data-stu-id="31d3e-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="31d3e-153">雖然畫面播放速率是穩定性的第一要件，但其他因素可能會影響穩定性，包括：</span><span class="sxs-lookup"><span data-stu-id="31d3e-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="31d3e-154">使用穩定平面</span><span class="sxs-lookup"><span data-stu-id="31d3e-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="31d3e-155">距離空間錨點</span><span class="sxs-lookup"><span data-stu-id="31d3e-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="31d3e-156">追蹤</span><span class="sxs-lookup"><span data-stu-id="31d3e-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-157">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-160">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-161">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-161">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-162">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-162">Best</span></span>  |  <span data-ttu-id="31d3e-163">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-163">Meets</span></span> |  <span data-ttu-id="31d3e-164">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="31d3e-165">全像投影一樣穩定。</span><span class="sxs-lookup"><span data-stu-id="31d3e-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="31d3e-166">次要內容展示非預期的移動;或非預期的移動不會妨礙整體應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="31d3e-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="31d3e-167">框架中的主要內容表現了非預期的移動。</span><span class="sxs-lookup"><span data-stu-id="31d3e-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-168">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-168">How to measure</span></span>

<span data-ttu-id="31d3e-169">在佩戴裝置和觀賞體驗時：</span><span class="sxs-lookup"><span data-stu-id="31d3e-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="31d3e-170">將您的標題從側邊移至側面，如果全像是顯示非預期的移動，那麼低畫面播放速率或穩定性平面與焦點平面之間的對齊可能是可能的原因。</span><span class="sxs-lookup"><span data-stu-id="31d3e-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="31d3e-171">四處移動全像影像和環境，尋找像是泳道和 jumpiness 的行為。</span><span class="sxs-lookup"><span data-stu-id="31d3e-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="31d3e-172">這種類型的動作可能是因為裝置無法追蹤環境或空間錨點的距離所造成。</span><span class="sxs-lookup"><span data-stu-id="31d3e-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="31d3e-173">如果框架中有大型或多個全息圖，請觀察各種深度的全像全像投影行為，並將您的頭部位置從側邊移至側面，如果出現 shakiness，可能是穩定平面所造成。</span><span class="sxs-lookup"><span data-stu-id="31d3e-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-174">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-174">Recommendations</span></span>

* <span data-ttu-id="31d3e-175">在開發工作的開頭新增畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="31d3e-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="31d3e-176">使用穩定平面。</span><span class="sxs-lookup"><span data-stu-id="31d3e-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="31d3e-177">一律在其錨點的3計量中轉譯錨定的全像投影。</span><span class="sxs-lookup"><span data-stu-id="31d3e-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="31d3e-178">請確定您的環境已設定適當的追蹤。</span><span class="sxs-lookup"><span data-stu-id="31d3e-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="31d3e-179">設計您的體驗，以避免在框架內的各種焦點深度層級進行全像投影。</span><span class="sxs-lookup"><span data-stu-id="31d3e-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-180">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="31d3e-181">文件</span><span class="sxs-lookup"><span data-stu-id="31d3e-181">Documentation</span></span>

* [<span data-ttu-id="31d3e-182">全像穩定性和幀的影像</span><span class="sxs-lookup"><span data-stu-id="31d3e-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="31d3e-183">使用穩定平面的案例研究</span><span class="sxs-lookup"><span data-stu-id="31d3e-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="31d3e-184">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="31d3e-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="31d3e-185">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-185">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="31d3e-186">空間錨點</span><span class="sxs-lookup"><span data-stu-id="31d3e-186">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="31d3e-187">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="31d3e-187">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="31d3e-188">固定的參考框架</span><span class="sxs-lookup"><span data-stu-id="31d3e-188">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="31d3e-189">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="31d3e-189">Tools and tutorials</span></span>

* [<span data-ttu-id="31d3e-190">MR IPD 套件，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="31d3e-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="31d3e-191">在實際表面上的全息圖位置</span><span class="sxs-lookup"><span data-stu-id="31d3e-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="31d3e-192">不一致具有實體 (物件的全像地理位置的，如果要放置在彼此之間的關聯，) 會清楚指出非全像全像的非等量和真實世界。</span><span class="sxs-lookup"><span data-stu-id="31d3e-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="31d3e-193">放置的精確度應該相對於案例的需求;例如，一般表面放置可以使用空間地圖，但是更準確的放置將需要使用標記和校正。</span><span class="sxs-lookup"><span data-stu-id="31d3e-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-194">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-195"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-195"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-196"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-196"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-197">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-198">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-198">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-199">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-199">Best</span></span>  |  <span data-ttu-id="31d3e-200">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-200">Meets</span></span> |  <span data-ttu-id="31d3e-201">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="31d3e-202">全像平面的全像平面的圖格對齊。</span><span class="sxs-lookup"><span data-stu-id="31d3e-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="31d3e-203">如果需要更多精確度，應用程式應該提供有效的方法，以在所需的應用程式規格內共同作業。</span><span class="sxs-lookup"><span data-stu-id="31d3e-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="31d3e-204">NA</span><span class="sxs-lookup"><span data-stu-id="31d3e-204">NA</span></span> | <span data-ttu-id="31d3e-205">將表面平面中斷或遠離表面，以將實體目標物件顯示為未對齊。</span><span class="sxs-lookup"><span data-stu-id="31d3e-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="31d3e-206">如果需要精確度，則全像全像全像）會符合案例的相近規格。</span><span class="sxs-lookup"><span data-stu-id="31d3e-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-207">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-207">How to measure</span></span>

* <span data-ttu-id="31d3e-208">放在空間地圖上的全像影像應該不會明顯地浮動在表面上方或下方。</span><span class="sxs-lookup"><span data-stu-id="31d3e-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="31d3e-209">需要精確放置的全像投影必須有某種形式的標記和校正系統，才能精確地因應案例需求。</span><span class="sxs-lookup"><span data-stu-id="31d3e-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-210">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-210">Recommendations</span></span>

* <span data-ttu-id="31d3e-211">空間地圖適用于在不需要 precision 時將物件放在表面上。</span><span class="sxs-lookup"><span data-stu-id="31d3e-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="31d3e-212">為了獲得最佳的精確度，請使用標記或海報來設定全像是 (或某些手動對齊機制) 來進行最終校正。</span><span class="sxs-lookup"><span data-stu-id="31d3e-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="31d3e-213">請考慮將超大的全像分割分成邏輯部分，並將每個部分對齊表面。</span><span class="sxs-lookup"><span data-stu-id="31d3e-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="31d3e-214">不正確地設定 interpupillary 距離 (IPD) 也可以影響全息圖對齊。</span><span class="sxs-lookup"><span data-stu-id="31d3e-214">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="31d3e-215">一律將 HoloLens 設定為使用者的 IPD。</span><span class="sxs-lookup"><span data-stu-id="31d3e-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-216">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="31d3e-217">文件</span><span class="sxs-lookup"><span data-stu-id="31d3e-217">Documentation</span></span>

* [<span data-ttu-id="31d3e-218">空間對應放置</span><span class="sxs-lookup"><span data-stu-id="31d3e-218">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="31d3e-219">會議室掃描流程</span><span class="sxs-lookup"><span data-stu-id="31d3e-219">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="31d3e-220">空間錨點最佳作法</span><span class="sxs-lookup"><span data-stu-id="31d3e-220">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="31d3e-221">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="31d3e-221">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="31d3e-222">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="31d3e-222">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="31d3e-223">Vuforia 開發總覽</span><span class="sxs-lookup"><span data-stu-id="31d3e-223">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="31d3e-224">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="31d3e-224">Tools and tutorials</span></span>

* [<span data-ttu-id="31d3e-225">MR 工具組、空間對應庫</span><span class="sxs-lookup"><span data-stu-id="31d3e-225">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="31d3e-226">MR 配套套件，海報校正範例</span><span class="sxs-lookup"><span data-stu-id="31d3e-226">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="31d3e-227">MR IPD 套件，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="31d3e-227">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="31d3e-228">外部參考</span><span class="sxs-lookup"><span data-stu-id="31d3e-228">External references</span></span>

* [<span data-ttu-id="31d3e-229">Lowes 案例研究，精確度對齊</span><span class="sxs-lookup"><span data-stu-id="31d3e-229">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="31d3e-230">觀賞緩和區域</span><span class="sxs-lookup"><span data-stu-id="31d3e-230">Viewing zone of comfort</span></span>

<span data-ttu-id="31d3e-231">應用程式開發人員藉由在不同的深度放置內容和全息，來控制使用者的眼睛。</span><span class="sxs-lookup"><span data-stu-id="31d3e-231">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="31d3e-232">使用 HoloLens 的使用者永遠都能容納 2.0 m，以維護清楚的影像，因為 HoloLens 顯示器是固定于大約 2.0 m 與使用者之間的距離。</span><span class="sxs-lookup"><span data-stu-id="31d3e-232">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="31d3e-233">不當的內容深度可能會導致 visual 不適感或疲勞。</span><span class="sxs-lookup"><span data-stu-id="31d3e-233">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-234">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-234">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-235"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-235"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-236"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-236"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-237">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-237">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-238">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-238">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="31d3e-239">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-239">Best</span></span> </td><td><ul>
<li><span data-ttu-id="31d3e-240">將內容放在2m。</span><span class="sxs-lookup"><span data-stu-id="31d3e-240">Place content at 2m.</span></span></li><li><span data-ttu-id="31d3e-241">當您無法在2m 上放置全像全像，但無法避免聚合和住宿之間的衝突時，將會在 1.25 m 和5m 之間放置全像位置的最佳區域。</span><span class="sxs-lookup"><span data-stu-id="31d3e-241">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="31d3e-242">在每個案例中，設計人員都應該結構內容，以鼓勵使用者在 (的情況下互動 1 + m，例如調整內容大小和預設位置參數) 。</span><span class="sxs-lookup"><span data-stu-id="31d3e-242">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="31d3e-243">除非此案例特別需要，否則裁剪平面應該會在 fadeout 開始時，從1m 開始執行。</span><span class="sxs-lookup"><span data-stu-id="31d3e-243">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="31d3e-244">如果需要更仔細觀察 motionless 全息圖，內容不應比50cm 更接近。</span><span class="sxs-lookup"><span data-stu-id="31d3e-244">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="31d3e-245">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-245">Meets</span></span></td><td> <span data-ttu-id="31d3e-246">內容位於觀看和移動的指導方針中，但不正確的使用或不使用裁剪平面。</span><span class="sxs-lookup"><span data-stu-id="31d3e-246">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="31d3e-247">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-247">Fail</span></span> </td><td> <span data-ttu-id="31d3e-248">內容呈現太接近的 (通常是 &lt; 1.25 m，或 &lt; 需要更深入觀察的靜止全像50cm。 ) </span><span class="sxs-lookup"><span data-stu-id="31d3e-248">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-249">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-249">How to measure</span></span>

* <span data-ttu-id="31d3e-250">內容通常應該2m 離開，但不能比5m 更接近1.25 或更早。</span><span class="sxs-lookup"><span data-stu-id="31d3e-250">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="31d3e-251">除了少數例外狀況，您應該將 HoloLens 裁剪轉譯距離設定為. 85CM 與 fadeout 的內容，起價為1m。</span><span class="sxs-lookup"><span data-stu-id="31d3e-251">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="31d3e-252">處理內容並記下裁剪平面效果。</span><span class="sxs-lookup"><span data-stu-id="31d3e-252">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="31d3e-253">固定內容不應接近50cm 的距離。</span><span class="sxs-lookup"><span data-stu-id="31d3e-253">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-254">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-254">Recommendations</span></span>

* <span data-ttu-id="31d3e-255">設計內容以取得2m 的最佳觀賞距離。</span><span class="sxs-lookup"><span data-stu-id="31d3e-255">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="31d3e-256">將 [裁剪轉譯距離] 設定為 [85cm]，其中 fadeout 的內容是從1m 開始。</span><span class="sxs-lookup"><span data-stu-id="31d3e-256">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="31d3e-257">對於需要更近觀賞的靜止全像影像，裁剪平面應該不會接近30cm，而且 fadeout 至少應該從裁剪平面開始10cm。</span><span class="sxs-lookup"><span data-stu-id="31d3e-257">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-258">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-258">Resources</span></span>

* [<span data-ttu-id="31d3e-259">呈現距離</span><span class="sxs-lookup"><span data-stu-id="31d3e-259">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="31d3e-260">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="31d3e-260">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="31d3e-261">使用 scale 進行實驗</span><span class="sxs-lookup"><span data-stu-id="31d3e-261">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="31d3e-262">文字，建議使用的字型大小</span><span class="sxs-lookup"><span data-stu-id="31d3e-262">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="31d3e-263">深度切換</span><span class="sxs-lookup"><span data-stu-id="31d3e-263">Depth switching</span></span>

<span data-ttu-id="31d3e-264">不論是在哪裡觀賞緩和問題，使用者都需要經常或快速地在接近或遠的焦點物件之間切換， (包括全像全半形的內容) 可能會導致 oculomotor 疲勞和一般不適感。</span><span class="sxs-lookup"><span data-stu-id="31d3e-264">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-265">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-265">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-266"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-266"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-267"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-267"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-268">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-268">✔️</span></span></td>
        <td><span data-ttu-id="31d3e-269">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-269">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-270">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-270">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-271">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-271">Best</span></span>  |  <span data-ttu-id="31d3e-272">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-272">Meets</span></span> |  <span data-ttu-id="31d3e-273">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-273">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="31d3e-274">不會導致使用者 unnaturally 將的有限或自然深度切換。</span><span class="sxs-lookup"><span data-stu-id="31d3e-274">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="31d3e-275">最深度的參數是核心，並設計為應用程式體驗或非預期的真實世界內容所造成的深度深度切換。</span><span class="sxs-lookup"><span data-stu-id="31d3e-275">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="31d3e-276">一致的深度切換，或不必要或核心到應用程式體驗的深度切換。</span><span class="sxs-lookup"><span data-stu-id="31d3e-276">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-277">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-277">How to measure</span></span>

* <span data-ttu-id="31d3e-278">如果應用程式要求使用者一致且/或突然變更深度焦點，則會有深度切換問題。</span><span class="sxs-lookup"><span data-stu-id="31d3e-278">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-279">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-279">Recommendations</span></span>

* <span data-ttu-id="31d3e-280">將主要內容保持在一致的焦點平面上，並確定穩定平面符合焦點平面。</span><span class="sxs-lookup"><span data-stu-id="31d3e-280">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="31d3e-281">這可減輕 oculomotor 疲勞和非預期的全像移動。</span><span class="sxs-lookup"><span data-stu-id="31d3e-281">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-282">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-282">Resources</span></span>

* [<span data-ttu-id="31d3e-283">呈現距離</span><span class="sxs-lookup"><span data-stu-id="31d3e-283">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="31d3e-284">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="31d3e-284">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="31d3e-285">使用空間音效</span><span class="sxs-lookup"><span data-stu-id="31d3e-285">Use of spatial sound</span></span>

<span data-ttu-id="31d3e-286">在 Windows Mixed Reality 中，音訊引擎會使用方向、距離和環境模擬來模擬3D 音效，以提供混合現實體驗的 aural 元件。</span><span class="sxs-lookup"><span data-stu-id="31d3e-286">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="31d3e-287">在應用程式中使用空間音效，可讓開發人員 convincingly 將音效放在三維空間 (球體) 在使用者周圍。</span><span class="sxs-lookup"><span data-stu-id="31d3e-287">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="31d3e-288">這些音效看起來就像是來自真實的實體物件，或是使用者的環境中的混合現實全息。</span><span class="sxs-lookup"><span data-stu-id="31d3e-288">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="31d3e-289">空間音效是深度、協助工具和 UX 設計在混合現實應用程式中的強大工具。</span><span class="sxs-lookup"><span data-stu-id="31d3e-289">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-290">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-290">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-291"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-291"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-292"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-292"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-293">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-293">✔️</span></span></td>
        <td><span data-ttu-id="31d3e-294">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-294">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-295">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-295">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-296">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-296">Best</span></span>  |  <span data-ttu-id="31d3e-297">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-297">Meets</span></span> |  <span data-ttu-id="31d3e-298">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-298">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="31d3e-299">音效會以邏輯方式 hrtf，而且 UX 會適當地使用音效來協助物件探索和使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="31d3e-299">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="31d3e-300">音效自然且與物件相關，並在整個案例中正規化。</span><span class="sxs-lookup"><span data-stu-id="31d3e-300">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="31d3e-301">空間音訊可適當地用於 believability，但卻遺失，以協助使用者提供意見反應和探索。</span><span class="sxs-lookup"><span data-stu-id="31d3e-301">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="31d3e-302">音效未如預期般 hrtf，以及/或缺乏音效來協助使用者在 UX 內。</span><span class="sxs-lookup"><span data-stu-id="31d3e-302">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="31d3e-303">或空間音訊在案例設計中未被視為或使用。</span><span class="sxs-lookup"><span data-stu-id="31d3e-303">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-304">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-304">How to measure</span></span>

* <span data-ttu-id="31d3e-305">一般情況下，相關的音效應該會從目標全息的 (（例如，來自全像狗的吠音效）發出。 ) </span><span class="sxs-lookup"><span data-stu-id="31d3e-305">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="31d3e-306">聲音提示應該用於整個 UX，以協助使用者提供全像全像攝影框架外的動作意見反應或認知。</span><span class="sxs-lookup"><span data-stu-id="31d3e-306">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-307">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-307">Recommendations</span></span>

* <span data-ttu-id="31d3e-308">使用空間音訊協助物件探索和使用者介面。</span><span class="sxs-lookup"><span data-stu-id="31d3e-308">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="31d3e-309">實際音效的效果優於合成或非自然音效。</span><span class="sxs-lookup"><span data-stu-id="31d3e-309">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="31d3e-310">大部分的音效都應該 hrtf。</span><span class="sxs-lookup"><span data-stu-id="31d3e-310">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="31d3e-311">避免不可見的發射器。</span><span class="sxs-lookup"><span data-stu-id="31d3e-311">Avoid invisible emitters.</span></span>
* <span data-ttu-id="31d3e-312">避免空間遮罩。</span><span class="sxs-lookup"><span data-stu-id="31d3e-312">Avoid spatial masking.</span></span>
* <span data-ttu-id="31d3e-313">將所有音效標準化。</span><span class="sxs-lookup"><span data-stu-id="31d3e-313">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-314">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-314">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="31d3e-315">文件</span><span class="sxs-lookup"><span data-stu-id="31d3e-315">Documentation</span></span>

* [<span data-ttu-id="31d3e-316">空間音效</span><span class="sxs-lookup"><span data-stu-id="31d3e-316">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="31d3e-317">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="31d3e-317">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="31d3e-318">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="31d3e-318">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="31d3e-319">案例研究、HoloTour 的空間音效</span><span class="sxs-lookup"><span data-stu-id="31d3e-319">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="31d3e-320">個案研究，在 RoboRaid 中使用空間音效</span><span class="sxs-lookup"><span data-stu-id="31d3e-320">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="31d3e-321">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="31d3e-321">Tools and tutorials</span></span>

* [<span data-ttu-id="31d3e-322">MRToolkit，空間音訊</span><span class="sxs-lookup"><span data-stu-id="31d3e-322">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="31d3e-323">專注于全像攝影框架 (FOV) 界限</span><span class="sxs-lookup"><span data-stu-id="31d3e-323">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="31d3e-324">設計完善的使用者體驗可以建立和維護在使用者周圍擴充之虛擬環境的實用內容。</span><span class="sxs-lookup"><span data-stu-id="31d3e-324">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="31d3e-325">減輕 FOV 界限的影響，牽涉到精心設計的內容規模和內容、空間音訊的使用、指引系統，以及使用者的位置。</span><span class="sxs-lookup"><span data-stu-id="31d3e-325">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="31d3e-326">如果完成，使用者會覺得 FOV 界限不會受到影響，同時讓應用程式體驗更舒適。</span><span class="sxs-lookup"><span data-stu-id="31d3e-326">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-327">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-327">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-328"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-328"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-329"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-329"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-330">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-330">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-331">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-331">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-332">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-332">Best</span></span>  |  <span data-ttu-id="31d3e-333">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-333">Meets</span></span> |  <span data-ttu-id="31d3e-334">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-334">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="31d3e-335">使用者永遠都不會遺失內容和觀賞。</span><span class="sxs-lookup"><span data-stu-id="31d3e-335">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="31d3e-336">針對大型物件提供內容協助。</span><span class="sxs-lookup"><span data-stu-id="31d3e-336">Context assistance is provided for large objects.</span></span> <span data-ttu-id="31d3e-337">探索和觀看指引是針對框架外的物件提供。</span><span class="sxs-lookup"><span data-stu-id="31d3e-337">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="31d3e-338">一般情況下，全像影像的移動設計和縮放比例適用于舒適的觀賞體驗。</span><span class="sxs-lookup"><span data-stu-id="31d3e-338">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="31d3e-339">使用者絕對不會遺失內容，但在有限的情況下可能需要額外的頸部動作。</span><span class="sxs-lookup"><span data-stu-id="31d3e-339">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="31d3e-340">在有限的情況下，縮放會導致全像是垂直或水準框架，而導致某些頸部的移動顯示全像影像。</span><span class="sxs-lookup"><span data-stu-id="31d3e-340">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="31d3e-341">使用者可能遺失內容和（或）一致的頸部動作來觀看全像全像投影。</span><span class="sxs-lookup"><span data-stu-id="31d3e-341">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="31d3e-342">沒有大型全息型物件的內容指引、移動物件很容易在框架外遺失，也沒有可搜尋的指引，或高的全像全像投影需要定期移動。</span><span class="sxs-lookup"><span data-stu-id="31d3e-342">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-343">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-343">How to measure</span></span>

* <span data-ttu-id="31d3e-344"> (大型) 全息圖的內容遺失或無法理解，因為已在界限上修剪。</span><span class="sxs-lookup"><span data-stu-id="31d3e-344">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="31d3e-345">因為缺乏注意總監或內容快速移入和移出全像外框，所以很難找到全像的位置。</span><span class="sxs-lookup"><span data-stu-id="31d3e-345">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="31d3e-346">案例需要定期和重複的向上和向下鍵，才能完全查看會導致疲勞的全像投影。</span><span class="sxs-lookup"><span data-stu-id="31d3e-346">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-347">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-347">Recommendations</span></span>

* <span data-ttu-id="31d3e-348">使用符合 FOV 的小型物件開始體驗，然後以視覺提示轉換成較大的版本。</span><span class="sxs-lookup"><span data-stu-id="31d3e-348">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="31d3e-349">使用「空間音訊」和「注意總監」來協助使用者尋找 FOV 以外的內容。</span><span class="sxs-lookup"><span data-stu-id="31d3e-349">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="31d3e-350">盡可能避免以垂直方式裁剪 FOV 的全像影像。</span><span class="sxs-lookup"><span data-stu-id="31d3e-350">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="31d3e-351">為使用者提供應用程式內的指引，以取得最佳的觀賞位置。</span><span class="sxs-lookup"><span data-stu-id="31d3e-351">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-352">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-352">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="31d3e-353">文件</span><span class="sxs-lookup"><span data-stu-id="31d3e-353">Documentation</span></span>

* [<span data-ttu-id="31d3e-354">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="31d3e-354">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="31d3e-355">案例研究、HoloStudio UI 和互動設計學習</span><span class="sxs-lookup"><span data-stu-id="31d3e-355">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="31d3e-356">物件和環境的規模</span><span class="sxs-lookup"><span data-stu-id="31d3e-356">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="31d3e-357">資料指標，視覺提示</span><span class="sxs-lookup"><span data-stu-id="31d3e-357">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="31d3e-358">外部參考</span><span class="sxs-lookup"><span data-stu-id="31d3e-358">External references</span></span>

* [<span data-ttu-id="31d3e-359">關於 FOV 的許多 ado</span><span class="sxs-lookup"><span data-stu-id="31d3e-359">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="31d3e-360">內容會回應使用者位置</span><span class="sxs-lookup"><span data-stu-id="31d3e-360">Content reacts to user position</span></span>

<span data-ttu-id="31d3e-361">全像「真實」物件的方式，全像是對使用者的位置做出回應。</span><span class="sxs-lookup"><span data-stu-id="31d3e-361">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="31d3e-362">值得注意的設計考慮是 UI 元素，這些元素不一定會假設使用者的位置是固定的，而且會適應使用者的動作。</span><span class="sxs-lookup"><span data-stu-id="31d3e-362">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="31d3e-363">設計可正確調整為使用者位置的應用程式，將會建立更可信的體驗，並讓您更容易使用。</span><span class="sxs-lookup"><span data-stu-id="31d3e-363">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-364">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-364">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-365"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-365"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-366"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-366"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-367">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-367">✔️</span></span></td>
        <td><span data-ttu-id="31d3e-368">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-368">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-369">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-369">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="31d3e-370">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-370">Best</span></span> </td><td> <span data-ttu-id="31d3e-371">內容和 UI 會適應使用者的位置，讓使用者可以自然地與預期使用者移動範圍內的內容互動。</span><span class="sxs-lookup"><span data-stu-id="31d3e-371">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="31d3e-372">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-372">Meets</span></span> </td><td> <span data-ttu-id="31d3e-373">UI 可適應使用者的位置，但可能會妨礙需要使用者調整其位置的重要內容。</span><span class="sxs-lookup"><span data-stu-id="31d3e-373">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="31d3e-374">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-374">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="31d3e-375">UI 元素在移動期間遺失或鎖定，導致使用者 unnaturally 回到 (或尋找) 控制項。</span><span class="sxs-lookup"><span data-stu-id="31d3e-375">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="31d3e-376">UI 元素會限制主要內容的顯示。</span><span class="sxs-lookup"><span data-stu-id="31d3e-376">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="31d3e-377">UI 移動不是針對以 <a href="../../design/billboarding-and-tag-along.md">標記方向</a> 的 UI 元素而優化的觀賞距離和動力。</span><span class="sxs-lookup"><span data-stu-id="31d3e-377">UI movement is not optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-378">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-378">How to measure</span></span>

* <span data-ttu-id="31d3e-379">所有度量都應該在案例的合理範圍內完成。</span><span class="sxs-lookup"><span data-stu-id="31d3e-379">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="31d3e-380">雖然使用者移動會有所不同，但請不要嘗試對應用程式進行極大的使用者移動。</span><span class="sxs-lookup"><span data-stu-id="31d3e-380">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="31d3e-381">針對 UI 專案，不論使用者是否移動，都應該可以使用相關的控制項。</span><span class="sxs-lookup"><span data-stu-id="31d3e-381">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="31d3e-382">比方說，如果使用者是以縮放比例流覽3D 地圖，則不論位置為何，縮放控制項都應可立即提供給使用者使用。</span><span class="sxs-lookup"><span data-stu-id="31d3e-382">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-383">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-383">Recommendations</span></span>

* <span data-ttu-id="31d3e-384">使用者是相機，並負責控制移動。</span><span class="sxs-lookup"><span data-stu-id="31d3e-384">The user is the camera and they control the movement.</span></span> <span data-ttu-id="31d3e-385">讓它們磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="31d3e-385">Let them drive.</span></span>
* <span data-ttu-id="31d3e-386">請考慮 billboarding 適用于文字和功能表系統的情況，如果使用者要四處移動，則會被鎖定或遮蔽。</span><span class="sxs-lookup"><span data-stu-id="31d3e-386">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="31d3e-387">針對需要追蹤使用者的內容使用標籤，同時讓使用者能夠查看他們之前的內容。</span><span class="sxs-lookup"><span data-stu-id="31d3e-387">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-388">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-388">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="31d3e-389">文件</span><span class="sxs-lookup"><span data-stu-id="31d3e-389">Documentation</span></span>

* [<span data-ttu-id="31d3e-390">互動設計</span><span class="sxs-lookup"><span data-stu-id="31d3e-390">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="31d3e-391">色彩、燈光和材質</span><span class="sxs-lookup"><span data-stu-id="31d3e-391">Color, light, and material</span></span>](../../color,-light-and-materials.md)
* [<span data-ttu-id="31d3e-392">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="31d3e-392">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="31d3e-393">本能互動</span><span class="sxs-lookup"><span data-stu-id="31d3e-393">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="31d3e-394">自我運動和使用者運動</span><span class="sxs-lookup"><span data-stu-id="31d3e-394">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="31d3e-395">輸入互動清楚明瞭</span><span class="sxs-lookup"><span data-stu-id="31d3e-395">Input interaction clarity</span></span>

<span data-ttu-id="31d3e-396">輸入互動清楚地對應用程式的可用性很重要，並包括互動方法的輸入一致性、是多麼平易近人、可探索性。</span><span class="sxs-lookup"><span data-stu-id="31d3e-396">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="31d3e-397">使用者應該能夠在不重新的情況下使用全平臺的一般互動。</span><span class="sxs-lookup"><span data-stu-id="31d3e-397">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="31d3e-398">如果應用程式具有自訂輸入，則應該清楚地傳達和示範。</span><span class="sxs-lookup"><span data-stu-id="31d3e-398">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-399">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-399">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-400"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-400"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-401"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-401"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-402">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-402">✔️</span></span></td>
        <td><span data-ttu-id="31d3e-403">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-403">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-404">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-404">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-405">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-405">Best</span></span>  |  <span data-ttu-id="31d3e-406">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-406">Meets</span></span> |  <span data-ttu-id="31d3e-407">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-407">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="31d3e-408">輸入互動方法與 Windows Mixed Reality 提供的 [指導](../../design/interaction-fundamentals.md)方針一致。</span><span class="sxs-lookup"><span data-stu-id="31d3e-408">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="31d3e-409">任何自訂輸入都不應與標準輸入一樣重複 (而是使用標準的互動) ，而且必須清楚地傳達並向使用者展示。</span><span class="sxs-lookup"><span data-stu-id="31d3e-409">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="31d3e-410">類似于最佳，但自訂輸入是具有標準輸入方法的多餘。</span><span class="sxs-lookup"><span data-stu-id="31d3e-410">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="31d3e-411">使用者仍然可以透過應用程式體驗來達成目標和進度。</span><span class="sxs-lookup"><span data-stu-id="31d3e-411">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="31d3e-412">難以瞭解輸入方法或按鈕對應。</span><span class="sxs-lookup"><span data-stu-id="31d3e-412">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="31d3e-413">輸入經過大量自訂，不支援標準輸入、沒有指示，或可能造成疲勞和緩和問題。</span><span class="sxs-lookup"><span data-stu-id="31d3e-413">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-414">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-414">How to measure</span></span>

* <span data-ttu-id="31d3e-415">應用程式會使用一致的 [標準輸入方法。](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="31d3e-415">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="31d3e-416">如果應用程式具有自訂輸入，則會透過下列方式明確地傳達：</span><span class="sxs-lookup"><span data-stu-id="31d3e-416">If the app has custom input, it is clearly communicated through:</span></span>
* <span data-ttu-id="31d3e-417">首次執行體驗</span><span class="sxs-lookup"><span data-stu-id="31d3e-417">First-run experience</span></span>
* <span data-ttu-id="31d3e-418">簡介畫面</span><span class="sxs-lookup"><span data-stu-id="31d3e-418">Introductory screens</span></span>
* <span data-ttu-id="31d3e-419">工具提示</span><span class="sxs-lookup"><span data-stu-id="31d3e-419">Tooltips</span></span>
* <span data-ttu-id="31d3e-420">手勢指導</span><span class="sxs-lookup"><span data-stu-id="31d3e-420">Hand coach</span></span>
* <span data-ttu-id="31d3e-421">說明區段</span><span class="sxs-lookup"><span data-stu-id="31d3e-421">Help section</span></span>
* <span data-ttu-id="31d3e-422">旁白</span><span class="sxs-lookup"><span data-stu-id="31d3e-422">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-423">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-423">Recommendations</span></span>

* <span data-ttu-id="31d3e-424">盡可能使用標準輸入方法。</span><span class="sxs-lookup"><span data-stu-id="31d3e-424">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="31d3e-425">提供非標準輸入方法的示範、教學課程和工具提示。</span><span class="sxs-lookup"><span data-stu-id="31d3e-425">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="31d3e-426">在整個應用程式中使用一致的互動模型。</span><span class="sxs-lookup"><span data-stu-id="31d3e-426">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-427">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-427">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="31d3e-428">文件</span><span class="sxs-lookup"><span data-stu-id="31d3e-428">Documentation</span></span>

* [<span data-ttu-id="31d3e-429">本能互動</span><span class="sxs-lookup"><span data-stu-id="31d3e-429">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="31d3e-430">互動物件</span><span class="sxs-lookup"><span data-stu-id="31d3e-430">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="31d3e-431">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="31d3e-431">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="31d3e-432">資料指標</span><span class="sxs-lookup"><span data-stu-id="31d3e-432">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="31d3e-433">緩和和注視</span><span class="sxs-lookup"><span data-stu-id="31d3e-433">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="31d3e-434">語音輸入</span><span class="sxs-lookup"><span data-stu-id="31d3e-434">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="31d3e-435">運動控制器</span><span class="sxs-lookup"><span data-stu-id="31d3e-435">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="31d3e-436">Unity 的輸入移植指南</span><span class="sxs-lookup"><span data-stu-id="31d3e-436">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="31d3e-437">Unity 中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="31d3e-437">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="31d3e-438">Unity 中的目光</span><span class="sxs-lookup"><span data-stu-id="31d3e-438">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="31d3e-439">Unity 中的筆勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="31d3e-439">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="31d3e-440">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="31d3e-440">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="31d3e-441">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="31d3e-441">Keyboard, mouse, and controller input in DirectX</span></span>](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="31d3e-442">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="31d3e-442">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="31d3e-443">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="31d3e-443">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="31d3e-444">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="31d3e-444">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="31d3e-445">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="31d3e-445">Tools and tutorials</span></span>

* [<span data-ttu-id="31d3e-446">案例研究：追求更多個人運算的能力</span><span class="sxs-lookup"><span data-stu-id="31d3e-446">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="31d3e-447">Cast 研究： HoloStudio UI 和互動設計學習</span><span class="sxs-lookup"><span data-stu-id="31d3e-447">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="31d3e-448">範例應用程式：元素的定期資料表</span><span class="sxs-lookup"><span data-stu-id="31d3e-448">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="31d3e-449">範例應用程式：陰曆模組</span><span class="sxs-lookup"><span data-stu-id="31d3e-449">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="31d3e-450">互動物件</span><span class="sxs-lookup"><span data-stu-id="31d3e-450">Interactable objects</span></span>

<span data-ttu-id="31d3e-451">按鈕一直以來都是用來觸發2D 抽象世界中事件的比喻。</span><span class="sxs-lookup"><span data-stu-id="31d3e-451">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="31d3e-452">在三維混合現實世界中，我們不再需要局限于這種抽象概念。</span><span class="sxs-lookup"><span data-stu-id="31d3e-452">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="31d3e-453">任何專案都可以是觸發事件的互動物件。</span><span class="sxs-lookup"><span data-stu-id="31d3e-453">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="31d3e-454">互動物件可以表示為來自資料表咖啡杯的任何事物，以及浮動在空氣中的球形球。</span><span class="sxs-lookup"><span data-stu-id="31d3e-454">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="31d3e-455">無論表單為何，使用者都應該透過視覺和音訊提示清楚地辨識互動物件。</span><span class="sxs-lookup"><span data-stu-id="31d3e-455">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-456">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-456">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-457"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-457"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-458"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-458"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-459">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-459">✔️</span></span></td>
        <td><span data-ttu-id="31d3e-460">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-460">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-461">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-461">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-462">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-462">Best</span></span>  |  <span data-ttu-id="31d3e-463">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-463">Meets</span></span> |  <span data-ttu-id="31d3e-464">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-464">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="31d3e-465">無論何種形式，互動物件都可以透過視覺和音訊提示，在三種狀態中辨識：閒置、目標和選取。</span><span class="sxs-lookup"><span data-stu-id="31d3e-465">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="31d3e-466">「看起來」清楚且一致地在整個體驗中使用。</span><span class="sxs-lookup"><span data-stu-id="31d3e-466">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="31d3e-467">物件會進行調整並散佈，以允許無錯誤的目標。</span><span class="sxs-lookup"><span data-stu-id="31d3e-467">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="31d3e-468">使用者可以透過音訊或視覺效果的意見反應將物件辨識為互動，並且可以將物件設為目標並啟用。</span><span class="sxs-lookup"><span data-stu-id="31d3e-468">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="31d3e-469">由於沒有視覺效果或音訊提示，使用者無法辨識互動物件。</span><span class="sxs-lookup"><span data-stu-id="31d3e-469">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="31d3e-470">互動會因為物件之間的縮放或距離而容易出錯。</span><span class="sxs-lookup"><span data-stu-id="31d3e-470">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-471">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-471">How to measure</span></span>

* <span data-ttu-id="31d3e-472">互動物件可辨識為 ' 互動 ';包括按鈕、功能表和應用程式特定內容。</span><span class="sxs-lookup"><span data-stu-id="31d3e-472">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="31d3e-473">根據經驗法則，在目標為互動物件時，應該會有視覺和音訊提示。</span><span class="sxs-lookup"><span data-stu-id="31d3e-473">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-474">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-474">Recommendations</span></span>

* <span data-ttu-id="31d3e-475">使用視覺效果和音訊意見反應進行互動。</span><span class="sxs-lookup"><span data-stu-id="31d3e-475">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="31d3e-476">您應針對每個輸入狀態， (閒置、目標、選取的) ，來區分視覺效果意見反應</span><span class="sxs-lookup"><span data-stu-id="31d3e-476">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="31d3e-477">互動物件應該調整並放置，以找出錯誤的目標。</span><span class="sxs-lookup"><span data-stu-id="31d3e-477">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="31d3e-478">群組互動物件 (例如功能表列或清單) 應該具有適當的目標間距。</span><span class="sxs-lookup"><span data-stu-id="31d3e-478">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="31d3e-479">支援 voice 命令的按鈕和功能表應該提供命令關鍵字的文字標籤 ( "見它，例如" ) </span><span class="sxs-lookup"><span data-stu-id="31d3e-479">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-480">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-480">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="31d3e-481">文件</span><span class="sxs-lookup"><span data-stu-id="31d3e-481">Documentation</span></span>

* [<span data-ttu-id="31d3e-482">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="31d3e-482">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="31d3e-483">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="31d3e-483">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="31d3e-484">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="31d3e-484">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="31d3e-485">語音輸入</span><span class="sxs-lookup"><span data-stu-id="31d3e-485">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="31d3e-486">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="31d3e-486">Tools and tutorials</span></span>

* [<span data-ttu-id="31d3e-487">混合現實工具組-UX</span><span class="sxs-lookup"><span data-stu-id="31d3e-487">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="31d3e-488">掃描房間</span><span class="sxs-lookup"><span data-stu-id="31d3e-488">Room scanning</span></span>

<span data-ttu-id="31d3e-489">需要空間對應資料的應用程式依賴裝置在一段時間內自動收集此資料，並在使用者探索其環境中使用中的裝置時，跨會話自動收集此資料。</span><span class="sxs-lookup"><span data-stu-id="31d3e-489">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="31d3e-490">這項資料的完整性和品質取決於許多因素，包括使用者已完成的探索量、從探索以來經過的時間，以及裝置掃描區域之後是否已移動傢俱和大門等物件。</span><span class="sxs-lookup"><span data-stu-id="31d3e-490">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="31d3e-491">許多應用程式會在體驗開始時分析空間對應資料，以判斷使用者是否應該執行額外的步驟，以改善空間地圖的完整性和品質。</span><span class="sxs-lookup"><span data-stu-id="31d3e-491">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="31d3e-492">如果使用者需要掃描環境，請在掃描體驗期間提供清楚的指引。</span><span class="sxs-lookup"><span data-stu-id="31d3e-492">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-493">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-493">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-494"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-494"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-495"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-495"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-496">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-496">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-497">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-497">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-498">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-498">Best</span></span>  |  <span data-ttu-id="31d3e-499">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-499">Meets</span></span> |  <span data-ttu-id="31d3e-500">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-500">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="31d3e-501">空間網格的視覺效果可讓使用者掃描正在進行中。</span><span class="sxs-lookup"><span data-stu-id="31d3e-501">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="31d3e-502">使用者清楚知道要做什麼，以及何時開始和停止掃描。</span><span class="sxs-lookup"><span data-stu-id="31d3e-502">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="31d3e-503">提供空間網格的視覺效果，但使用者可能不清楚知道要執行的動作，也不會提供任何進度資訊。</span><span class="sxs-lookup"><span data-stu-id="31d3e-503">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="31d3e-504">沒有網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="31d3e-504">No visualization of mesh.</span></span> <span data-ttu-id="31d3e-505">未提供任何指引資訊給使用者，找出要查看的位置，或掃描何時啟動/停止。</span><span class="sxs-lookup"><span data-stu-id="31d3e-505">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-506">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-506">How to measure</span></span>

* <span data-ttu-id="31d3e-507">在需要的房間掃描期間，會提供視覺和音訊指引來指出要查看的位置，以及開始和停止掃描的時機。</span><span class="sxs-lookup"><span data-stu-id="31d3e-507">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-508">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-508">Recommendations</span></span>

* <span data-ttu-id="31d3e-509">指出使用者鄰近區中的總數量必須是經驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="31d3e-509">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="31d3e-510">當掃描啟動並停止（例如進度指示器）時進行通訊。</span><span class="sxs-lookup"><span data-stu-id="31d3e-510">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="31d3e-511">在掃描期間使用網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="31d3e-511">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="31d3e-512">提供視覺和音訊提示，以鼓勵使用者查看和四處移動房間。</span><span class="sxs-lookup"><span data-stu-id="31d3e-512">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="31d3e-513">通知使用者移至何處以改善資料。</span><span class="sxs-lookup"><span data-stu-id="31d3e-513">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="31d3e-514">在許多情況下，最好讓使用者知道他們需要做什麼事 (例如查看最上方的 [傢俱]) ，以便取得所需的掃描品質。</span><span class="sxs-lookup"><span data-stu-id="31d3e-514">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-515">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-515">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="31d3e-516">文件</span><span class="sxs-lookup"><span data-stu-id="31d3e-516">Documentation</span></span>

* [<span data-ttu-id="31d3e-517">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="31d3e-517">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="31d3e-518">案例研究：擴充 HoloLens 的空間對應功能</span><span class="sxs-lookup"><span data-stu-id="31d3e-518">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="31d3e-519">案例研究： HoloTour 的空間音效設計</span><span class="sxs-lookup"><span data-stu-id="31d3e-519">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="31d3e-520">案例研究：在片段中建立沉浸式體驗</span><span class="sxs-lookup"><span data-stu-id="31d3e-520">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="31d3e-521">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="31d3e-521">Tools and tutorials</span></span>

* [<span data-ttu-id="31d3e-522">混合現實工具組-UX</span><span class="sxs-lookup"><span data-stu-id="31d3e-522">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="31d3e-523">方向指標</span><span class="sxs-lookup"><span data-stu-id="31d3e-523">Directional indicators</span></span>

<span data-ttu-id="31d3e-524">在混合現實應用程式中，內容可能會在真實世界物件的視野或 pixels occluded 之外。</span><span class="sxs-lookup"><span data-stu-id="31d3e-524">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="31d3e-525">設計完善的應用程式可讓使用者更容易找到不可見的內容。</span><span class="sxs-lookup"><span data-stu-id="31d3e-525">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="31d3e-526">方向指標會將使用者警示至重要內容，並提供相對於使用者位置之內容的指引。</span><span class="sxs-lookup"><span data-stu-id="31d3e-526">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="31d3e-527">非可見內容的指引可以採用音效發射器、方向箭號或直接視覺提示的形式。</span><span class="sxs-lookup"><span data-stu-id="31d3e-527">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-528">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-528">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-529"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-529"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-530"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-530"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-531">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-531">✔️</span></span></td>
        <td><span data-ttu-id="31d3e-532">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-532">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-533">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-533">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-534">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-534">Best</span></span>  |  <span data-ttu-id="31d3e-535">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-535">Meets</span></span> |  <span data-ttu-id="31d3e-536">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-536">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="31d3e-537">視覺效果和音訊提示會直接引導使用者前往視野以外的相關內容。</span><span class="sxs-lookup"><span data-stu-id="31d3e-537">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="31d3e-538">箭號或某些指標，可在內容的一般方向中指向使用者。</span><span class="sxs-lookup"><span data-stu-id="31d3e-538">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="31d3e-539">相關內容位於視野的範圍之外，且不佳或未提供任何位置指引給使用者。</span><span class="sxs-lookup"><span data-stu-id="31d3e-539">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-540">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-540">How to measure</span></span>

* <span data-ttu-id="31d3e-541">您可以透過視覺和/或音訊提示，探索使用者欄位外的相關內容。</span><span class="sxs-lookup"><span data-stu-id="31d3e-541">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-542">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-542">Recommendations</span></span>

* <span data-ttu-id="31d3e-543">當相關內容不在使用者的 view 欄位之外時，請使用方向指標和音訊提示，將使用者引導至內容。</span><span class="sxs-lookup"><span data-stu-id="31d3e-543">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="31d3e-544">在許多情況下，直接的視覺效果指南優先于方向箭號。</span><span class="sxs-lookup"><span data-stu-id="31d3e-544">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="31d3e-545">方向指標不應內建在游標內。</span><span class="sxs-lookup"><span data-stu-id="31d3e-545">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-546">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-546">Resources</span></span>

* [<span data-ttu-id="31d3e-547">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="31d3e-547">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="31d3e-548">載入資料</span><span class="sxs-lookup"><span data-stu-id="31d3e-548">Data loading</span></span>

<span data-ttu-id="31d3e-549">進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。</span><span class="sxs-lookup"><span data-stu-id="31d3e-549">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="31d3e-550">這可能表示使用者無法在進度指標可見時與應用程式互動，也可以指出等候時間可能的時間長度。</span><span class="sxs-lookup"><span data-stu-id="31d3e-550">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="31d3e-551">裝置影響</span><span class="sxs-lookup"><span data-stu-id="31d3e-551">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31d3e-552"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-552"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="31d3e-553"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="31d3e-553"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31d3e-554">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-554">✔️</span></span></td>
        <td><span data-ttu-id="31d3e-555">✔️</span><span class="sxs-lookup"><span data-stu-id="31d3e-555">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="31d3e-556">品質準則</span><span class="sxs-lookup"><span data-stu-id="31d3e-556">Quality criteria</span></span>

|  <span data-ttu-id="31d3e-557">最佳</span><span class="sxs-lookup"><span data-stu-id="31d3e-557">Best</span></span>  |  <span data-ttu-id="31d3e-558">會見</span><span class="sxs-lookup"><span data-stu-id="31d3e-558">Meets</span></span> |  <span data-ttu-id="31d3e-559">失敗</span><span class="sxs-lookup"><span data-stu-id="31d3e-559">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="31d3e-560">以進度列或環形形式呈現的動畫視覺指標，顯示任何資料載入或處理期間的進度。</span><span class="sxs-lookup"><span data-stu-id="31d3e-560">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="31d3e-561">視覺指標會提供等待時間長度的指引。</span><span class="sxs-lookup"><span data-stu-id="31d3e-561">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="31d3e-562">使用者會收到資料載入進行中的通知，但不會指出等候的時間長度。</span><span class="sxs-lookup"><span data-stu-id="31d3e-562">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="31d3e-563">沒有任何資料載入或處理時間超過5秒的程式指示器。</span><span class="sxs-lookup"><span data-stu-id="31d3e-563">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="31d3e-564">如何測量</span><span class="sxs-lookup"><span data-stu-id="31d3e-564">How to measure</span></span>

* <span data-ttu-id="31d3e-565">在資料載入期間，請確認沒有任何空白狀態超過5秒。</span><span class="sxs-lookup"><span data-stu-id="31d3e-565">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="31d3e-566">建議</span><span class="sxs-lookup"><span data-stu-id="31d3e-566">Recommendations</span></span>

* <span data-ttu-id="31d3e-567">提供資料載入 animator，顯示當使用者可能會察覺到此應用程式停止或損毀時的進度。</span><span class="sxs-lookup"><span data-stu-id="31d3e-567">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="31d3e-568">合理的經驗法則是任何可能需要5秒以上的「載入」活動。</span><span class="sxs-lookup"><span data-stu-id="31d3e-568">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="31d3e-569">資源</span><span class="sxs-lookup"><span data-stu-id="31d3e-569">Resources</span></span>

* [<span data-ttu-id="31d3e-570">顯示進度</span><span class="sxs-lookup"><span data-stu-id="31d3e-570">Displaying progress</span></span>](../../design/progress.md)
