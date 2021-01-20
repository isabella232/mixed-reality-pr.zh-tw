---
title: 應用程式品質準則
description: 本檔說明影響混合現實應用程式品質的主要因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式品質準則、混合現實、混合現實應用程式、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 3f6752c0a15ae7db21be1f4a6d2843339ab28a5c
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581260"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="9751d-104">應用程式品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-104">App quality criteria</span></span>

<span data-ttu-id="9751d-105">本檔說明影響混合現實應用程式品質的主要因素。</span><span class="sxs-lookup"><span data-stu-id="9751d-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="9751d-106">針對每個因素，會提供下列資訊</span><span class="sxs-lookup"><span data-stu-id="9751d-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="9751d-107">總覽-品質因素的簡短描述，以及其重要性。</span><span class="sxs-lookup"><span data-stu-id="9751d-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="9751d-108">裝置影響-受影響的視窗混合現實裝置類型。</span><span class="sxs-lookup"><span data-stu-id="9751d-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="9751d-109">品質準則–如何評估品質因素。</span><span class="sxs-lookup"><span data-stu-id="9751d-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="9751d-110">如何測量–測量問題 (或) 經驗的方法。</span><span class="sxs-lookup"><span data-stu-id="9751d-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="9751d-111">建議-提供更佳使用者體驗的方法摘要。</span><span class="sxs-lookup"><span data-stu-id="9751d-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="9751d-112">資源-相關的開發人員和設計資源，可用於建立更好的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="9751d-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="9751d-113">畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="9751d-113">Frame rate</span></span>

<span data-ttu-id="9751d-114">畫面播放速率是全像全像要件的第一次，也是使用者的舒適。</span><span class="sxs-lookup"><span data-stu-id="9751d-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="9751d-115">低於建議目標的畫面播放速率可能會導致全息圖顯得抖動、對體驗的 believability 造成負面影響，並可能造成眼睛疲勞。</span><span class="sxs-lookup"><span data-stu-id="9751d-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="9751d-116">您 Windows Mixed Reality 沉浸式耳機的目標畫面播放速率是 60 Hz 或 90 Hz，視您支援的 Windows Mixed Reality 相容電腦而定。</span><span class="sxs-lookup"><span data-stu-id="9751d-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="9751d-117">HoloLens 的目標畫面播放速率是 60 Hz。</span><span class="sxs-lookup"><span data-stu-id="9751d-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-118">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-121">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-121">✔️</span></span></td>
        <td><span data-ttu-id="9751d-122">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-123">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-123">Quality criteria</span></span>

|  <span data-ttu-id="9751d-124">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-124">Best</span></span>  |  <span data-ttu-id="9751d-125">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-125">Meets</span></span> |  <span data-ttu-id="9751d-126">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="9751d-127">應用程式一致地符合每秒的畫面格 (FPS) 目標裝置的目標： HoloLens 上的 60 FPS;Ultra 電腦上的 90 fps;和 60 fps （主流電腦）。</span><span class="sxs-lookup"><span data-stu-id="9751d-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="9751d-128">應用程式有間歇性的框架下降不會阻礙核心經驗，或 FPS 的一致性低於所需的目標，但不會妨礙應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="9751d-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="9751d-129">應用程式平均每10秒或更短的畫面播放速率都有下降。</span><span class="sxs-lookup"><span data-stu-id="9751d-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9751d-130">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-130">How to measure</span></span>

* <span data-ttu-id="9751d-131">「系統效能」下的 [Windows 裝置入口網站](using-the-windows-device-portal.md#system-performance) 會提供即時的畫面播放速率圖形。</span><span class="sxs-lookup"><span data-stu-id="9751d-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="9751d-132">針對開發的偵錯工具，請在應用程式中新增畫面播放速率診斷計數器。</span><span class="sxs-lookup"><span data-stu-id="9751d-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="9751d-133">請參閱範例計數器的資源。</span><span class="sxs-lookup"><span data-stu-id="9751d-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="9751d-134">當應用程式正在執行時，可能會在裝置上經歷畫面播放速率下降，方法是將您的標題從側邊移動</span><span class="sxs-lookup"><span data-stu-id="9751d-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="9751d-135">如果全息圖顯示非預期的抖動移動，則低畫面播放速率或穩定性平面可能是原因。</span><span class="sxs-lookup"><span data-stu-id="9751d-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-136">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-136">Recommendations</span></span>

* <span data-ttu-id="9751d-137">在開發工作的開頭新增畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="9751d-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="9751d-138">產生下降畫面播放速率的變更應該進行評估，並適當地解析為效能錯誤。</span><span class="sxs-lookup"><span data-stu-id="9751d-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-139">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9751d-140">文件</span><span class="sxs-lookup"><span data-stu-id="9751d-140">Documentation</span></span>

* [<span data-ttu-id="9751d-141">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="9751d-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="9751d-142">全像穩定性和幀的影像</span><span class="sxs-lookup"><span data-stu-id="9751d-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="9751d-143">資產效能預算</span><span class="sxs-lookup"><span data-stu-id="9751d-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="9751d-144">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="9751d-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9751d-145">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="9751d-145">Tools and tutorials</span></span>

* [<span data-ttu-id="9751d-146">混合現實工具組，FPS 計數器顯示</span><span class="sxs-lookup"><span data-stu-id="9751d-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="9751d-147">混合現實工具組、著色器</span><span class="sxs-lookup"><span data-stu-id="9751d-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="9751d-148">外部參考</span><span class="sxs-lookup"><span data-stu-id="9751d-148">External references</span></span>

* [<span data-ttu-id="9751d-149">Unity，將行動應用程式優化</span><span class="sxs-lookup"><span data-stu-id="9751d-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="9751d-150">全像投影穩定性</span><span class="sxs-lookup"><span data-stu-id="9751d-150">Hologram stability</span></span>

<span data-ttu-id="9751d-151">穩定的全像影像會提高應用程式的可用性和 believability，並為使用者建立更舒適的觀賞體驗。</span><span class="sxs-lookup"><span data-stu-id="9751d-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="9751d-152">全像應用程式開發的結果，以及裝置瞭解 (追蹤) 其環境的能力。</span><span class="sxs-lookup"><span data-stu-id="9751d-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="9751d-153">雖然畫面播放速率是穩定性的第一要件，但其他因素可能會影響穩定性，包括：</span><span class="sxs-lookup"><span data-stu-id="9751d-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="9751d-154">使用穩定平面</span><span class="sxs-lookup"><span data-stu-id="9751d-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="9751d-155">距離空間錨點</span><span class="sxs-lookup"><span data-stu-id="9751d-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="9751d-156">追蹤</span><span class="sxs-lookup"><span data-stu-id="9751d-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-157">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-160">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-161">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-161">Quality criteria</span></span>

|  <span data-ttu-id="9751d-162">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-162">Best</span></span>  |  <span data-ttu-id="9751d-163">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-163">Meets</span></span> |  <span data-ttu-id="9751d-164">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9751d-165">全像投影一樣穩定。</span><span class="sxs-lookup"><span data-stu-id="9751d-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="9751d-166">次要內容顯示非預期的移動;或非預期的移動不會妨礙整體應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="9751d-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="9751d-167">框架中的主要內容會顯示非預期的移動。</span><span class="sxs-lookup"><span data-stu-id="9751d-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9751d-168">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-168">How to measure</span></span>

<span data-ttu-id="9751d-169">在佩戴裝置和觀賞體驗時：</span><span class="sxs-lookup"><span data-stu-id="9751d-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="9751d-170">將您的標題從側邊移至側面。</span><span class="sxs-lookup"><span data-stu-id="9751d-170">Move your head from side to side.</span></span> <span data-ttu-id="9751d-171">如果全像投影顯示非預期的移動，則很可能會造成穩定性平面的低畫面播放速率或不當對齊。</span><span class="sxs-lookup"><span data-stu-id="9751d-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="9751d-172">四處移動全像影像和環境，尋找像是泳道和 jumpiness 的行為。</span><span class="sxs-lookup"><span data-stu-id="9751d-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="9751d-173">這種類型的動作可能是因為裝置無法追蹤環境或空間錨點的距離所造成。</span><span class="sxs-lookup"><span data-stu-id="9751d-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="9751d-174">如果框架中有大型或多個全息圖，請觀察各種深度的全像全像投影行為，並將您的頭部位置從側邊移至側面，如果出現 shakiness，可能是穩定平面所造成。</span><span class="sxs-lookup"><span data-stu-id="9751d-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-175">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-175">Recommendations</span></span>

* <span data-ttu-id="9751d-176">在開發工作的開頭新增畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="9751d-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="9751d-177">使用穩定平面。</span><span class="sxs-lookup"><span data-stu-id="9751d-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="9751d-178">一律在其錨點的3計量中轉譯錨定的全像投影。</span><span class="sxs-lookup"><span data-stu-id="9751d-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="9751d-179">請確定您的環境已設定好進行適當追蹤。</span><span class="sxs-lookup"><span data-stu-id="9751d-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="9751d-180">設計您的體驗，以避免在框架內的各種焦點深度層級進行全像投影。</span><span class="sxs-lookup"><span data-stu-id="9751d-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-181">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9751d-182">文件</span><span class="sxs-lookup"><span data-stu-id="9751d-182">Documentation</span></span>

* [<span data-ttu-id="9751d-183">全像穩定性和幀的影像</span><span class="sxs-lookup"><span data-stu-id="9751d-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="9751d-184">使用穩定平面的案例研究</span><span class="sxs-lookup"><span data-stu-id="9751d-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="9751d-185">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="9751d-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="9751d-186">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="9751d-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="9751d-187">空間錨點</span><span class="sxs-lookup"><span data-stu-id="9751d-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="9751d-188">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="9751d-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="9751d-189">固定的參考框架</span><span class="sxs-lookup"><span data-stu-id="9751d-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9751d-190">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="9751d-190">Tools and tutorials</span></span>

* [<span data-ttu-id="9751d-191">MR IPD 套件，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="9751d-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="9751d-192">在實際表面上的全息圖位置</span><span class="sxs-lookup"><span data-stu-id="9751d-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="9751d-193">不一致具有實體 (物件的全像地理位置的，如果要放置在彼此之間的關聯，) 會清楚指出非全像的非等量和真實世界。</span><span class="sxs-lookup"><span data-stu-id="9751d-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="9751d-194">放置的精確度應該相對於案例的需求;例如，一般表面放置可以使用空間地圖，但是更準確的放置將需要使用標記和校正。</span><span class="sxs-lookup"><span data-stu-id="9751d-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-195">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-198">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-199">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-199">Quality criteria</span></span>

|  <span data-ttu-id="9751d-200">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-200">Best</span></span>  |  <span data-ttu-id="9751d-201">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-201">Meets</span></span> |  <span data-ttu-id="9751d-202">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="9751d-203">全像平面的全像平面的圖格對齊。</span><span class="sxs-lookup"><span data-stu-id="9751d-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="9751d-204">如果您需要更多精確度，應用程式應該提供有效率的方法，讓您在應用程式規格內共同作業。</span><span class="sxs-lookup"><span data-stu-id="9751d-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="9751d-205">NA</span><span class="sxs-lookup"><span data-stu-id="9751d-205">NA</span></span> | <span data-ttu-id="9751d-206">將表面平面中斷或遠離表面，以將實體目標物件顯示為未對齊。</span><span class="sxs-lookup"><span data-stu-id="9751d-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="9751d-207">如果需要精確度，則全像全像全像）會符合案例的相近規格。</span><span class="sxs-lookup"><span data-stu-id="9751d-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9751d-208">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-208">How to measure</span></span>

* <span data-ttu-id="9751d-209">放在空間地圖上的全像全像，不應該在表面上方或下方動態浮動。</span><span class="sxs-lookup"><span data-stu-id="9751d-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="9751d-210">需要精確放置的全像投影必須有某種形式的標記和校正系統，才能精確地因應案例需求。</span><span class="sxs-lookup"><span data-stu-id="9751d-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-211">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-211">Recommendations</span></span>

* <span data-ttu-id="9751d-212">空間地圖適用于在不需要 precision 時將物件放在表面上。</span><span class="sxs-lookup"><span data-stu-id="9751d-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="9751d-213">為了獲得最佳的精確度，請使用標記或海報來設定全像是 (或某些手動對齊機制) 來進行最終校正。</span><span class="sxs-lookup"><span data-stu-id="9751d-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="9751d-214">請考慮將超大的全像分割分成邏輯部分，並將每個部分對齊表面。</span><span class="sxs-lookup"><span data-stu-id="9751d-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="9751d-215">不正確地設定 interpupillary 距離 (IPD) 也可以影響全息圖對齊。</span><span class="sxs-lookup"><span data-stu-id="9751d-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="9751d-216">一律將 HoloLens 設定為使用者的 IPD。</span><span class="sxs-lookup"><span data-stu-id="9751d-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-217">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9751d-218">文件</span><span class="sxs-lookup"><span data-stu-id="9751d-218">Documentation</span></span>

* [<span data-ttu-id="9751d-219">空間對應放置</span><span class="sxs-lookup"><span data-stu-id="9751d-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="9751d-220">會議室掃描流程</span><span class="sxs-lookup"><span data-stu-id="9751d-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="9751d-221">空間錨點最佳作法</span><span class="sxs-lookup"><span data-stu-id="9751d-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="9751d-222">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="9751d-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="9751d-223">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="9751d-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="9751d-224">Vuforia 開發總覽</span><span class="sxs-lookup"><span data-stu-id="9751d-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9751d-225">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="9751d-225">Tools and tutorials</span></span>

* [<span data-ttu-id="9751d-226">MR 工具組、空間對應庫</span><span class="sxs-lookup"><span data-stu-id="9751d-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="9751d-227">MR 配套套件，海報校正範例</span><span class="sxs-lookup"><span data-stu-id="9751d-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="9751d-228">MR IPD 套件，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="9751d-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="9751d-229">外部參考</span><span class="sxs-lookup"><span data-stu-id="9751d-229">External references</span></span>

* [<span data-ttu-id="9751d-230">Lowes 案例研究，精確度對齊</span><span class="sxs-lookup"><span data-stu-id="9751d-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="9751d-231">觀賞緩和區域</span><span class="sxs-lookup"><span data-stu-id="9751d-231">Viewing zone of comfort</span></span>

<span data-ttu-id="9751d-232">應用程式開發人員藉由在不同的深度放置內容和全息，來控制使用者的眼睛。</span><span class="sxs-lookup"><span data-stu-id="9751d-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="9751d-233">使用 HoloLens 的使用者永遠都能容納 2.0 m 來維持清晰的影像，因為 HoloLens 顯示器是固定的，而與使用者之間的距離大約是 2.0 m。</span><span class="sxs-lookup"><span data-stu-id="9751d-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="9751d-234">不當的內容深度可能會導致 visual 不適感或疲勞。</span><span class="sxs-lookup"><span data-stu-id="9751d-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-235">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-238">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-239">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="9751d-240">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="9751d-241">將內容放在2分鐘。</span><span class="sxs-lookup"><span data-stu-id="9751d-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="9751d-242">當您無法在2分鐘放置全像，而且無法避免聚合和住宿之間的衝突時，將會在 1.25 m 和 5 m 之間放置全息圖的最佳區域。</span><span class="sxs-lookup"><span data-stu-id="9751d-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="9751d-243">在每個案例中，設計人員都應該結構內容，以鼓勵使用者在 (的情況下互動 1 + m，例如調整內容大小和預設位置參數) 。</span><span class="sxs-lookup"><span data-stu-id="9751d-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="9751d-244">除非此案例不需要，否則裁剪平面應以淡出的方式從 1 m 開始執行。</span><span class="sxs-lookup"><span data-stu-id="9751d-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="9751d-245">如果需要進一步觀察 motionless 全息圖，內容不應接近 50 cm。</span><span class="sxs-lookup"><span data-stu-id="9751d-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="9751d-246">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-246">Meets</span></span></td><td> <span data-ttu-id="9751d-247">內容位於觀看和移動的指導方針中，但不正確的使用或不使用裁剪平面。</span><span class="sxs-lookup"><span data-stu-id="9751d-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9751d-248">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-248">Fail</span></span> </td><td> <span data-ttu-id="9751d-249">內容呈現太近的 (通常是 &lt; 1.25 m，或 &lt; 50 cm 適用于需要進一步觀察的靜止全像。 ) </span><span class="sxs-lookup"><span data-stu-id="9751d-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="9751d-250">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-250">How to measure</span></span>

* <span data-ttu-id="9751d-251">內容通常應該是 2 m，但無法接近1.25 或超過 5 m。</span><span class="sxs-lookup"><span data-stu-id="9751d-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="9751d-252">在少數例外狀況下，您應該將 HoloLens 裁剪轉譯距離設定為85CM，並從 1 m 開始淡出內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="9751d-253">處理內容並記下裁剪平面效果。</span><span class="sxs-lookup"><span data-stu-id="9751d-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="9751d-254">固定內容不應接近 50 cm。</span><span class="sxs-lookup"><span data-stu-id="9751d-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-255">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-255">Recommendations</span></span>

* <span data-ttu-id="9751d-256">設計內容以取得 2 m 的最佳觀賞距離。</span><span class="sxs-lookup"><span data-stu-id="9751d-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="9751d-257">將裁剪轉譯距離設定為 85 cm，從 1 m 開始的內容淡出。</span><span class="sxs-lookup"><span data-stu-id="9751d-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="9751d-258">對於需要更近觀賞的靜止全像影像，裁剪平面應該不會接近 30 cm，且淡出應該從裁剪平面開始至少 10 cm。</span><span class="sxs-lookup"><span data-stu-id="9751d-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-259">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-259">Resources</span></span>

* [<span data-ttu-id="9751d-260">呈現距離</span><span class="sxs-lookup"><span data-stu-id="9751d-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="9751d-261">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="9751d-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="9751d-262">使用 scale 進行實驗</span><span class="sxs-lookup"><span data-stu-id="9751d-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="9751d-263">文字，建議使用的字型大小</span><span class="sxs-lookup"><span data-stu-id="9751d-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="9751d-264">深度切換</span><span class="sxs-lookup"><span data-stu-id="9751d-264">Depth switching</span></span>

<span data-ttu-id="9751d-265">不論是在哪裡觀賞緩和問題，使用者都需要經常或快速地在接近或遠的焦點物件之間切換， (包括全像全半形的內容) 可能會導致 oculomotor 疲勞和一般不適感。</span><span class="sxs-lookup"><span data-stu-id="9751d-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-266">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-269">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-269">✔️</span></span></td>
        <td><span data-ttu-id="9751d-270">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-271">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-271">Quality criteria</span></span>

|  <span data-ttu-id="9751d-272">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-272">Best</span></span>  |  <span data-ttu-id="9751d-273">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-273">Meets</span></span> |  <span data-ttu-id="9751d-274">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9751d-275">不會導致使用者 unnaturally 將的有限或自然深度切換。</span><span class="sxs-lookup"><span data-stu-id="9751d-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="9751d-276">最深度的參數是核心，並設計為應用程式體驗或非預期的真實世界內容所造成的深度深度切換。</span><span class="sxs-lookup"><span data-stu-id="9751d-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="9751d-277">一致的深度切換，或不必要或核心到應用程式體驗的深度切換。</span><span class="sxs-lookup"><span data-stu-id="9751d-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9751d-278">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-278">How to measure</span></span>

* <span data-ttu-id="9751d-279">如果應用程式要求使用者一致且/或突然變更深度焦點，則會有深度切換問題。</span><span class="sxs-lookup"><span data-stu-id="9751d-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-280">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-280">Recommendations</span></span>

* <span data-ttu-id="9751d-281">將主要內容保持在一致的焦點平面上，並確定穩定平面符合焦點平面。</span><span class="sxs-lookup"><span data-stu-id="9751d-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="9751d-282">這可減輕 oculomotor 疲勞和非預期的全像移動。</span><span class="sxs-lookup"><span data-stu-id="9751d-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-283">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-283">Resources</span></span>

* [<span data-ttu-id="9751d-284">呈現距離</span><span class="sxs-lookup"><span data-stu-id="9751d-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="9751d-285">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="9751d-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="9751d-286">使用空間音效</span><span class="sxs-lookup"><span data-stu-id="9751d-286">Use of spatial sound</span></span>

<span data-ttu-id="9751d-287">在 Windows Mixed Reality 中，音訊引擎會使用方向、距離和環境模擬來模擬3D 音效，以提供混合現實體驗的 aural 元件。</span><span class="sxs-lookup"><span data-stu-id="9751d-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="9751d-288">在應用程式中使用空間音效，可讓開發人員 convincingly 將聲音放在三維空間 (球體) 在使用者周圍。</span><span class="sxs-lookup"><span data-stu-id="9751d-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="9751d-289">這些音效看起來就像是來自真實的實體物件，或是使用者的環境中的混合現實全息。</span><span class="sxs-lookup"><span data-stu-id="9751d-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="9751d-290">空間音效是深度、協助工具和 UX 設計在混合現實應用程式中的強大工具。</span><span class="sxs-lookup"><span data-stu-id="9751d-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-291">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-294">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-294">✔️</span></span></td>
        <td><span data-ttu-id="9751d-295">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-296">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-296">Quality criteria</span></span>

|  <span data-ttu-id="9751d-297">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-297">Best</span></span>  |  <span data-ttu-id="9751d-298">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-298">Meets</span></span> |  <span data-ttu-id="9751d-299">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9751d-300">音效會以邏輯方式 hrtf，而且 UX 會適當地使用音效來協助物件探索和使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="9751d-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="9751d-301">音效自然且與物件相關，並在整個案例中正規化。</span><span class="sxs-lookup"><span data-stu-id="9751d-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="9751d-302">空間音訊可適當地用於 believability，但卻遺失，以協助使用者提供意見反應和探索。</span><span class="sxs-lookup"><span data-stu-id="9751d-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="9751d-303">音效未如預期般 hrtf，以及/或缺乏音效來協助使用者在 UX 內。</span><span class="sxs-lookup"><span data-stu-id="9751d-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="9751d-304">或空間音訊在案例設計中未被視為或使用。</span><span class="sxs-lookup"><span data-stu-id="9751d-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9751d-305">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-305">How to measure</span></span>

* <span data-ttu-id="9751d-306">一般情況下，相關的音效應該會從目標全息的 (（例如，來自全像狗的吠音效）發出。 ) </span><span class="sxs-lookup"><span data-stu-id="9751d-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="9751d-307">聲音提示應該用於整個 UX，以協助使用者提供全像全像攝影框架外的動作意見反應或認知。</span><span class="sxs-lookup"><span data-stu-id="9751d-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-308">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-308">Recommendations</span></span>

* <span data-ttu-id="9751d-309">使用空間音訊協助物件探索和使用者介面。</span><span class="sxs-lookup"><span data-stu-id="9751d-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="9751d-310">實際音效的效果優於合成或非自然音效。</span><span class="sxs-lookup"><span data-stu-id="9751d-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="9751d-311">大部分的音效都應該 hrtf。</span><span class="sxs-lookup"><span data-stu-id="9751d-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="9751d-312">避免不可見的發射器。</span><span class="sxs-lookup"><span data-stu-id="9751d-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="9751d-313">避免空間遮罩。</span><span class="sxs-lookup"><span data-stu-id="9751d-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="9751d-314">將所有音效標準化。</span><span class="sxs-lookup"><span data-stu-id="9751d-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-315">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9751d-316">文件</span><span class="sxs-lookup"><span data-stu-id="9751d-316">Documentation</span></span>

* [<span data-ttu-id="9751d-317">空間音效</span><span class="sxs-lookup"><span data-stu-id="9751d-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="9751d-318">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="9751d-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="9751d-319">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="9751d-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="9751d-320">案例研究、HoloTour 的空間音效</span><span class="sxs-lookup"><span data-stu-id="9751d-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="9751d-321">個案研究，在 RoboRaid 中使用空間音效</span><span class="sxs-lookup"><span data-stu-id="9751d-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9751d-322">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="9751d-322">Tools and tutorials</span></span>

* [<span data-ttu-id="9751d-323">混合現實工具組-空間音訊</span><span class="sxs-lookup"><span data-stu-id="9751d-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="9751d-324">專注于全像攝影框架 (FOV) 界限</span><span class="sxs-lookup"><span data-stu-id="9751d-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="9751d-325">設計完善的使用者體驗可以建立和維護在使用者周圍擴充之虛擬環境的實用內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="9751d-326">減輕 FOV 界限的影響，牽涉到精心設計的內容規模和內容、空間音訊的使用、指引系統，以及使用者的位置。</span><span class="sxs-lookup"><span data-stu-id="9751d-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="9751d-327">如果完成，使用者會覺得 FOV 界限不會受到影響，同時讓應用程式體驗更舒適。</span><span class="sxs-lookup"><span data-stu-id="9751d-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-328">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-331">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-332">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-332">Quality criteria</span></span>

|  <span data-ttu-id="9751d-333">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-333">Best</span></span>  |  <span data-ttu-id="9751d-334">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-334">Meets</span></span> |  <span data-ttu-id="9751d-335">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9751d-336">使用者永遠都不會遺失內容和觀賞。</span><span class="sxs-lookup"><span data-stu-id="9751d-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="9751d-337">針對大型物件提供內容協助。</span><span class="sxs-lookup"><span data-stu-id="9751d-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="9751d-338">探索和觀看指引是針對框架外的物件提供。</span><span class="sxs-lookup"><span data-stu-id="9751d-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="9751d-339">一般情況下，全像影像的移動設計和縮放比例適用于舒適的觀賞體驗。</span><span class="sxs-lookup"><span data-stu-id="9751d-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="9751d-340">使用者絕對不會遺失內容，但在有限的情況下可能需要額外的頸部動作。</span><span class="sxs-lookup"><span data-stu-id="9751d-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="9751d-341">在有限的情況下，縮放會導致全像是垂直或水準框架，而導致某些頸部的移動顯示全像影像。</span><span class="sxs-lookup"><span data-stu-id="9751d-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="9751d-342">使用者可能遺失內容和（或）一致的頸部動作來觀看全像全像投影。</span><span class="sxs-lookup"><span data-stu-id="9751d-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="9751d-343">沒有大型全息型物件的內容指引、移動物件很容易在框架外遺失，也沒有可搜尋的指引，或高的全像全像投影需要定期移動。</span><span class="sxs-lookup"><span data-stu-id="9751d-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9751d-344">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-344">How to measure</span></span>

* <span data-ttu-id="9751d-345"> (大型) 全息圖的內容遺失或無法理解，因為已在界限上修剪。</span><span class="sxs-lookup"><span data-stu-id="9751d-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="9751d-346">因為缺乏注意總監或內容快速移入和移出全像全像外框，所以很難找到全像影像的位置。</span><span class="sxs-lookup"><span data-stu-id="9751d-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="9751d-347">案例需要定期和重複的向上和向下鍵，才能完全查看會導致疲勞的全像投影。</span><span class="sxs-lookup"><span data-stu-id="9751d-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-348">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-348">Recommendations</span></span>

* <span data-ttu-id="9751d-349">使用符合 FOV 的小型物件開始體驗，然後以視覺提示轉換成較大的版本。</span><span class="sxs-lookup"><span data-stu-id="9751d-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="9751d-350">使用「空間音訊」和「注意總監」來協助使用者尋找 FOV 以外的內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="9751d-351">盡可能避免以垂直方式裁剪 FOV 的全像影像。</span><span class="sxs-lookup"><span data-stu-id="9751d-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="9751d-352">為使用者提供應用程式內的指引，以取得最佳的觀賞位置。</span><span class="sxs-lookup"><span data-stu-id="9751d-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-353">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9751d-354">文件</span><span class="sxs-lookup"><span data-stu-id="9751d-354">Documentation</span></span>

* [<span data-ttu-id="9751d-355">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="9751d-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="9751d-356">案例研究、HoloStudio UI 和互動設計學習</span><span class="sxs-lookup"><span data-stu-id="9751d-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="9751d-357">物件和環境的規模</span><span class="sxs-lookup"><span data-stu-id="9751d-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="9751d-358">資料指標，視覺提示</span><span class="sxs-lookup"><span data-stu-id="9751d-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="9751d-359">外部參考</span><span class="sxs-lookup"><span data-stu-id="9751d-359">External references</span></span>

* [<span data-ttu-id="9751d-360">關於 FOV 的許多 ado</span><span class="sxs-lookup"><span data-stu-id="9751d-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="9751d-361">內容會回應使用者位置</span><span class="sxs-lookup"><span data-stu-id="9751d-361">Content reacts to user position</span></span>

<span data-ttu-id="9751d-362">全像「真實」物件的方式，全像是對使用者的位置做出回應。</span><span class="sxs-lookup"><span data-stu-id="9751d-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="9751d-363">值得注意的設計考慮是 UI 元素，這些元素不一定會假設使用者的位置是固定的，而且會適應使用者的動作。</span><span class="sxs-lookup"><span data-stu-id="9751d-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="9751d-364">設計可正確調整為使用者位置的應用程式，將會建立更可信的體驗，並讓您更容易使用。</span><span class="sxs-lookup"><span data-stu-id="9751d-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-365">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-368">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-368">✔️</span></span></td>
        <td><span data-ttu-id="9751d-369">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-370">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="9751d-371">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-371">Best</span></span> </td><td> <span data-ttu-id="9751d-372">內容和 UI 會適應使用者的位置，讓使用者可以自然地與預期使用者移動範圍內的內容互動。</span><span class="sxs-lookup"><span data-stu-id="9751d-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9751d-373">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-373">Meets</span></span> </td><td> <span data-ttu-id="9751d-374">UI 可適應使用者的位置，但可能會妨礙需要使用者調整其位置的重要內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="9751d-375">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="9751d-376">UI 元素在移動期間遺失或鎖定，導致使用者 unnaturally 回到 (或尋找) 控制項。</span><span class="sxs-lookup"><span data-stu-id="9751d-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="9751d-377">UI 元素會限制主要內容的顯示。</span><span class="sxs-lookup"><span data-stu-id="9751d-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="9751d-378">UI 移動並未針對以 <a href="../../design/billboarding-and-tag-along.md">標記為方向</a> 的 UI 元素的觀賞距離和動力進行優化。</span><span class="sxs-lookup"><span data-stu-id="9751d-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="9751d-379">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-379">How to measure</span></span>

* <span data-ttu-id="9751d-380">所有度量都應該在案例的合理範圍內完成。</span><span class="sxs-lookup"><span data-stu-id="9751d-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="9751d-381">雖然使用者移動會有所不同，但請不要嘗試對應用程式進行極大的使用者移動。</span><span class="sxs-lookup"><span data-stu-id="9751d-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="9751d-382">針對 UI 專案，不論使用者是否移動，都應該可以使用相關的控制項。</span><span class="sxs-lookup"><span data-stu-id="9751d-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="9751d-383">比方說，如果使用者是以縮放比例流覽3D 地圖，則不論位置為何，縮放控制項都應可立即提供給使用者使用。</span><span class="sxs-lookup"><span data-stu-id="9751d-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-384">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-384">Recommendations</span></span>

* <span data-ttu-id="9751d-385">使用者是相機，並負責控制移動。</span><span class="sxs-lookup"><span data-stu-id="9751d-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="9751d-386">讓它們磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="9751d-386">Let them drive.</span></span>
* <span data-ttu-id="9751d-387">請考慮 billboarding 適用于文字和功能表系統的情況，如果使用者要四處移動，則會被鎖定或遮蔽。</span><span class="sxs-lookup"><span data-stu-id="9751d-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="9751d-388">針對需要追蹤使用者的內容使用標籤，同時讓使用者能夠查看他們之前的內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-389">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9751d-390">文件</span><span class="sxs-lookup"><span data-stu-id="9751d-390">Documentation</span></span>

* [<span data-ttu-id="9751d-391">互動設計</span><span class="sxs-lookup"><span data-stu-id="9751d-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="9751d-392">色彩、燈光和材質</span><span class="sxs-lookup"><span data-stu-id="9751d-392">Color, light, and material</span></span>](../../design/color-light-and-materials.md)
* [<span data-ttu-id="9751d-393">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="9751d-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="9751d-394">本能互動</span><span class="sxs-lookup"><span data-stu-id="9751d-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="9751d-395">自我運動和使用者運動</span><span class="sxs-lookup"><span data-stu-id="9751d-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="9751d-396">輸入互動清楚明瞭</span><span class="sxs-lookup"><span data-stu-id="9751d-396">Input interaction clarity</span></span>

<span data-ttu-id="9751d-397">輸入互動清楚地對應用程式的可用性很重要，並包括互動方法的輸入一致性、是多麼平易近人、可探索性。</span><span class="sxs-lookup"><span data-stu-id="9751d-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="9751d-398">使用者可以在不重新的情況下使用全平臺的一般互動。</span><span class="sxs-lookup"><span data-stu-id="9751d-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="9751d-399">如果應用程式具有自訂輸入，則應該清楚地傳達和示範。</span><span class="sxs-lookup"><span data-stu-id="9751d-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-400">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-403">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-403">✔️</span></span></td>
        <td><span data-ttu-id="9751d-404">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-405">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-405">Quality criteria</span></span>

|  <span data-ttu-id="9751d-406">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-406">Best</span></span>  |  <span data-ttu-id="9751d-407">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-407">Meets</span></span> |  <span data-ttu-id="9751d-408">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9751d-409">輸入互動方法與 Windows Mixed Reality 提供的 [指導](../../design/interaction-fundamentals.md)方針一致。</span><span class="sxs-lookup"><span data-stu-id="9751d-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="9751d-410">任何自訂輸入都不應是標準輸入的多餘 (而是使用標準的互動) ，而且必須清楚地傳達並向使用者展示。</span><span class="sxs-lookup"><span data-stu-id="9751d-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="9751d-411">類似于最佳，但自訂輸入是具有標準輸入方法的多餘。</span><span class="sxs-lookup"><span data-stu-id="9751d-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="9751d-412">使用者仍然可以透過應用程式體驗來達成目標和進度。</span><span class="sxs-lookup"><span data-stu-id="9751d-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="9751d-413">難以瞭解輸入方法或按鈕對應。</span><span class="sxs-lookup"><span data-stu-id="9751d-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="9751d-414">輸入經過大量自訂，不支援標準輸入、沒有指示，或可能造成疲勞和緩和問題。</span><span class="sxs-lookup"><span data-stu-id="9751d-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9751d-415">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-415">How to measure</span></span>

* <span data-ttu-id="9751d-416">應用程式會使用一致的 [標準輸入方法。](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="9751d-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="9751d-417">如果應用程式具有自訂輸入，則會透過下列方式清楚地傳達：</span><span class="sxs-lookup"><span data-stu-id="9751d-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="9751d-418">首次執行體驗</span><span class="sxs-lookup"><span data-stu-id="9751d-418">First-run experience</span></span>
* <span data-ttu-id="9751d-419">簡介畫面</span><span class="sxs-lookup"><span data-stu-id="9751d-419">Introductory screens</span></span>
* <span data-ttu-id="9751d-420">工具提示</span><span class="sxs-lookup"><span data-stu-id="9751d-420">Tooltips</span></span>
* <span data-ttu-id="9751d-421">手勢指導</span><span class="sxs-lookup"><span data-stu-id="9751d-421">Hand coach</span></span>
* <span data-ttu-id="9751d-422">說明區段</span><span class="sxs-lookup"><span data-stu-id="9751d-422">Help section</span></span>
* <span data-ttu-id="9751d-423">旁白</span><span class="sxs-lookup"><span data-stu-id="9751d-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-424">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-424">Recommendations</span></span>

* <span data-ttu-id="9751d-425">盡可能使用標準輸入方法。</span><span class="sxs-lookup"><span data-stu-id="9751d-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="9751d-426">提供非標準輸入方法的示範、教學課程和工具提示。</span><span class="sxs-lookup"><span data-stu-id="9751d-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="9751d-427">在整個應用程式中使用一致的互動模型。</span><span class="sxs-lookup"><span data-stu-id="9751d-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-428">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9751d-429">文件</span><span class="sxs-lookup"><span data-stu-id="9751d-429">Documentation</span></span>

* [<span data-ttu-id="9751d-430">本能互動</span><span class="sxs-lookup"><span data-stu-id="9751d-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="9751d-431">互動物件</span><span class="sxs-lookup"><span data-stu-id="9751d-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="9751d-432">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="9751d-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="9751d-433">資料指標</span><span class="sxs-lookup"><span data-stu-id="9751d-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="9751d-434">緩和和注視</span><span class="sxs-lookup"><span data-stu-id="9751d-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="9751d-435">語音輸入</span><span class="sxs-lookup"><span data-stu-id="9751d-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="9751d-436">運動控制器</span><span class="sxs-lookup"><span data-stu-id="9751d-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="9751d-437">Unity 的輸入移植指南</span><span class="sxs-lookup"><span data-stu-id="9751d-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="9751d-438">Unity 中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="9751d-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="9751d-439">Unity 中的目光</span><span class="sxs-lookup"><span data-stu-id="9751d-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="9751d-440">Unity 中的動作控制器</span><span class="sxs-lookup"><span data-stu-id="9751d-440">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="9751d-441">Unity 中的手勢</span><span class="sxs-lookup"><span data-stu-id="9751d-441">Gestures in Unity</span></span>](../unity/gestures-in-unity.md)
* [<span data-ttu-id="9751d-442">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="9751d-442">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="9751d-443">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="9751d-443">Keyboard, mouse, and controller input in DirectX</span></span>](./keyboard-mouse-and-controller-input-in-directx.md)
* [<span data-ttu-id="9751d-444">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="9751d-444">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="9751d-445">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="9751d-445">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="9751d-446">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="9751d-446">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9751d-447">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="9751d-447">Tools and tutorials</span></span>

* [<span data-ttu-id="9751d-448">案例研究：追求更多個人運算的能力</span><span class="sxs-lookup"><span data-stu-id="9751d-448">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="9751d-449">Cast 研究： HoloStudio UI 和互動設計學習</span><span class="sxs-lookup"><span data-stu-id="9751d-449">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="9751d-450">範例應用程式：元素的定期資料表</span><span class="sxs-lookup"><span data-stu-id="9751d-450">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="9751d-451">範例應用程式：陰曆模組</span><span class="sxs-lookup"><span data-stu-id="9751d-451">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="9751d-452">互動物件</span><span class="sxs-lookup"><span data-stu-id="9751d-452">Interactable objects</span></span>

<span data-ttu-id="9751d-453">按鈕一直以來都是用來觸發2D 抽象世界中事件的比喻。</span><span class="sxs-lookup"><span data-stu-id="9751d-453">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="9751d-454">在三維混合現實世界中，我們不再需要局限于這種抽象概念。</span><span class="sxs-lookup"><span data-stu-id="9751d-454">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="9751d-455">任何專案都可以是觸發事件的互動物件。</span><span class="sxs-lookup"><span data-stu-id="9751d-455">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="9751d-456">互動物件可以表示為來自資料表咖啡杯的任何事物，以及浮動在空氣中的球形球。</span><span class="sxs-lookup"><span data-stu-id="9751d-456">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="9751d-457">無論表單為何，使用者都應該透過視覺和音訊提示清楚地辨識互動物件。</span><span class="sxs-lookup"><span data-stu-id="9751d-457">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-458">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-458">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-461">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-461">✔️</span></span></td>
        <td><span data-ttu-id="9751d-462">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-462">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-463">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-463">Quality criteria</span></span>

|  <span data-ttu-id="9751d-464">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-464">Best</span></span>  |  <span data-ttu-id="9751d-465">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-465">Meets</span></span> |  <span data-ttu-id="9751d-466">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-466">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9751d-467">無論何種形式，互動物件都可以透過視覺和音訊提示，在三種狀態中辨識：閒置、目標和選取。</span><span class="sxs-lookup"><span data-stu-id="9751d-467">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="9751d-468">「看起來」清楚且一致地在整個體驗中使用。</span><span class="sxs-lookup"><span data-stu-id="9751d-468">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="9751d-469">物件會進行調整並散佈，以允許無錯誤的目標。</span><span class="sxs-lookup"><span data-stu-id="9751d-469">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="9751d-470">使用者可以透過音訊或視覺效果的意見反應將物件辨識為互動，並且可以將物件設為目標並啟用。</span><span class="sxs-lookup"><span data-stu-id="9751d-470">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="9751d-471">由於沒有視覺效果或音訊提示，因此使用者無法辨識互動物件。</span><span class="sxs-lookup"><span data-stu-id="9751d-471">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="9751d-472">互動會因為物件之間的縮放或距離而容易出錯。</span><span class="sxs-lookup"><span data-stu-id="9751d-472">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9751d-473">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-473">How to measure</span></span>

* <span data-ttu-id="9751d-474">互動物件可辨識為 ' 互動 ';包括按鈕、功能表和應用程式特定的內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-474">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="9751d-475">根據經驗法則，在目標為互動物件時，應該會有視覺和音訊提示。</span><span class="sxs-lookup"><span data-stu-id="9751d-475">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-476">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-476">Recommendations</span></span>

* <span data-ttu-id="9751d-477">使用視覺效果和音訊意見反應進行互動。</span><span class="sxs-lookup"><span data-stu-id="9751d-477">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="9751d-478">您應針對每個輸入狀態， (閒置、目標、選取的) ，來區分視覺效果意見反應</span><span class="sxs-lookup"><span data-stu-id="9751d-478">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="9751d-479">互動物件應該調整並放置，以找出錯誤的目標。</span><span class="sxs-lookup"><span data-stu-id="9751d-479">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="9751d-480">群組互動物件 (例如功能表列或清單) 應該具有適當的目標間距。</span><span class="sxs-lookup"><span data-stu-id="9751d-480">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="9751d-481">支援 voice 命令的按鈕和功能表應該提供命令關鍵字的文字標籤 ( "見它，例如" ) </span><span class="sxs-lookup"><span data-stu-id="9751d-481">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-482">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-482">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9751d-483">文件</span><span class="sxs-lookup"><span data-stu-id="9751d-483">Documentation</span></span>

* [<span data-ttu-id="9751d-484">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="9751d-484">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="9751d-485">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="9751d-485">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="9751d-486">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="9751d-486">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="9751d-487">語音輸入</span><span class="sxs-lookup"><span data-stu-id="9751d-487">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9751d-488">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="9751d-488">Tools and tutorials</span></span>

* [<span data-ttu-id="9751d-489">混合現實工具組-UX</span><span class="sxs-lookup"><span data-stu-id="9751d-489">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="9751d-490">掃描房間</span><span class="sxs-lookup"><span data-stu-id="9751d-490">Room scanning</span></span>

<span data-ttu-id="9751d-491">需要空間對應資料的應用程式依賴裝置在一段時間內自動收集此資料，並在使用者探索其環境中使用中的裝置時，跨會話自動收集此資料。</span><span class="sxs-lookup"><span data-stu-id="9751d-491">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="9751d-492">這項資料的完整性和品質取決於許多因素，包括使用者已完成的探索量、從探索以來經過的時間，以及裝置掃描區域之後是否已移動傢俱和大門等物件。</span><span class="sxs-lookup"><span data-stu-id="9751d-492">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="9751d-493">許多應用程式會在體驗開始時分析空間對應資料，以判斷使用者是否應該執行額外的步驟，以改善空間地圖的完整性和品質。</span><span class="sxs-lookup"><span data-stu-id="9751d-493">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="9751d-494">如果使用者需要掃描環境，請在掃描體驗期間提供清楚的指引。</span><span class="sxs-lookup"><span data-stu-id="9751d-494">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-495">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-495">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-498">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-498">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-499">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-499">Quality criteria</span></span>

|  <span data-ttu-id="9751d-500">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-500">Best</span></span>  |  <span data-ttu-id="9751d-501">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-501">Meets</span></span> |  <span data-ttu-id="9751d-502">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-502">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9751d-503">空間網格的視覺效果可讓使用者掃描正在進行中。</span><span class="sxs-lookup"><span data-stu-id="9751d-503">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="9751d-504">使用者清楚知道要做什麼，以及何時開始和停止掃描。</span><span class="sxs-lookup"><span data-stu-id="9751d-504">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="9751d-505">提供空間網格的視覺效果，但使用者可能不清楚知道要執行的動作，也不會提供任何進度資訊。</span><span class="sxs-lookup"><span data-stu-id="9751d-505">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="9751d-506">沒有網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="9751d-506">No visualization of mesh.</span></span> <span data-ttu-id="9751d-507">未提供任何指引資訊給使用者，找出要查看的位置，或掃描何時啟動/停止。</span><span class="sxs-lookup"><span data-stu-id="9751d-507">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9751d-508">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-508">How to measure</span></span>

* <span data-ttu-id="9751d-509">在需要的房間掃描期間，會提供視覺和音訊指引來指出要查看的位置，以及開始和停止掃描的時機。</span><span class="sxs-lookup"><span data-stu-id="9751d-509">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-510">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-510">Recommendations</span></span>

* <span data-ttu-id="9751d-511">指出使用者鄰近區中的總數量必須是經驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="9751d-511">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="9751d-512">當掃描啟動並停止（例如進度指示器）時進行通訊。</span><span class="sxs-lookup"><span data-stu-id="9751d-512">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="9751d-513">在掃描期間使用網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="9751d-513">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="9751d-514">提供視覺和音訊提示，以鼓勵使用者查看和四處移動房間。</span><span class="sxs-lookup"><span data-stu-id="9751d-514">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="9751d-515">通知使用者移至何處以改善資料。</span><span class="sxs-lookup"><span data-stu-id="9751d-515">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="9751d-516">在許多情況下，最好讓使用者知道他們需要做什麼事 (例如查看最上方的 [傢俱]) ，以便取得所需的掃描品質。</span><span class="sxs-lookup"><span data-stu-id="9751d-516">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-517">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-517">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="9751d-518">文件</span><span class="sxs-lookup"><span data-stu-id="9751d-518">Documentation</span></span>

* [<span data-ttu-id="9751d-519">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="9751d-519">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="9751d-520">案例研究：擴充 HoloLens 的空間對應功能</span><span class="sxs-lookup"><span data-stu-id="9751d-520">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="9751d-521">案例研究： HoloTour 的空間音效設計</span><span class="sxs-lookup"><span data-stu-id="9751d-521">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="9751d-522">案例研究：在片段中建立沉浸式體驗</span><span class="sxs-lookup"><span data-stu-id="9751d-522">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="9751d-523">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="9751d-523">Tools and tutorials</span></span>

* [<span data-ttu-id="9751d-524">混合現實工具組-UX</span><span class="sxs-lookup"><span data-stu-id="9751d-524">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="9751d-525">方向指標</span><span class="sxs-lookup"><span data-stu-id="9751d-525">Directional indicators</span></span>

<span data-ttu-id="9751d-526">在混合現實應用程式中，內容可能會在真實世界物件的視野或 pixels occluded 之外。</span><span class="sxs-lookup"><span data-stu-id="9751d-526">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="9751d-527">設計完善的應用程式可讓使用者更容易找到不可見的內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-527">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="9751d-528">方向指標會將使用者警示至重要內容，並提供相對於使用者位置之內容的指引。</span><span class="sxs-lookup"><span data-stu-id="9751d-528">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="9751d-529">非可見內容的指引可以採用音效發射器、方向箭號或直接視覺提示的形式。</span><span class="sxs-lookup"><span data-stu-id="9751d-529">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-530">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-530">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-533">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-533">✔️</span></span></td>
        <td><span data-ttu-id="9751d-534">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-534">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-535">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-535">Quality criteria</span></span>

|  <span data-ttu-id="9751d-536">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-536">Best</span></span>  |  <span data-ttu-id="9751d-537">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-537">Meets</span></span> |  <span data-ttu-id="9751d-538">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-538">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9751d-539">視覺效果和音訊提示會直接引導使用者前往視野以外的相關內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-539">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="9751d-540">箭號或某些指標，可在內容的一般方向中指向使用者。</span><span class="sxs-lookup"><span data-stu-id="9751d-540">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="9751d-541">相關內容位於視野的範圍之外，且不佳或未提供任何位置指引給使用者。</span><span class="sxs-lookup"><span data-stu-id="9751d-541">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="9751d-542">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-542">How to measure</span></span>

* <span data-ttu-id="9751d-543">您可以透過視覺和/或音訊提示，探索使用者欄位外的相關內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-543">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-544">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-544">Recommendations</span></span>

* <span data-ttu-id="9751d-545">當相關內容不在使用者的 view 欄位之外時，請使用方向指標和音訊提示，將使用者引導至內容。</span><span class="sxs-lookup"><span data-stu-id="9751d-545">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="9751d-546">在許多情況下，直接的視覺效果指南優先于方向箭號。</span><span class="sxs-lookup"><span data-stu-id="9751d-546">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="9751d-547">方向指標不應內建在游標內。</span><span class="sxs-lookup"><span data-stu-id="9751d-547">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-548">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-548">Resources</span></span>

* [<span data-ttu-id="9751d-549">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="9751d-549">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="9751d-550">載入資料</span><span class="sxs-lookup"><span data-stu-id="9751d-550">Data loading</span></span>

<span data-ttu-id="9751d-551">進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。</span><span class="sxs-lookup"><span data-stu-id="9751d-551">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="9751d-552">這可能表示使用者無法在進度指標可見時與應用程式互動，也可以指出等候時間可能的時間長度。</span><span class="sxs-lookup"><span data-stu-id="9751d-552">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="9751d-553">裝置影響</span><span class="sxs-lookup"><span data-stu-id="9751d-553">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9751d-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9751d-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9751d-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9751d-556">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-556">✔️</span></span></td>
        <td><span data-ttu-id="9751d-557">✔️</span><span class="sxs-lookup"><span data-stu-id="9751d-557">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="9751d-558">品質準則</span><span class="sxs-lookup"><span data-stu-id="9751d-558">Quality criteria</span></span>

|  <span data-ttu-id="9751d-559">最佳</span><span class="sxs-lookup"><span data-stu-id="9751d-559">Best</span></span>  |  <span data-ttu-id="9751d-560">會見</span><span class="sxs-lookup"><span data-stu-id="9751d-560">Meets</span></span> |  <span data-ttu-id="9751d-561">失敗</span><span class="sxs-lookup"><span data-stu-id="9751d-561">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="9751d-562">以進度列或環形形式呈現的動畫視覺指標，顯示任何資料載入或處理期間的進度。</span><span class="sxs-lookup"><span data-stu-id="9751d-562">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="9751d-563">視覺指標會提供等待時間長度的指引。</span><span class="sxs-lookup"><span data-stu-id="9751d-563">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="9751d-564">使用者會收到資料載入進行中的通知，但不會指出等候的時間長度。</span><span class="sxs-lookup"><span data-stu-id="9751d-564">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="9751d-565">沒有任何資料載入或處理時間超過5秒的程式指示器。</span><span class="sxs-lookup"><span data-stu-id="9751d-565">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="9751d-566">如何測量</span><span class="sxs-lookup"><span data-stu-id="9751d-566">How to measure</span></span>

* <span data-ttu-id="9751d-567">在資料載入期間，請確認沒有任何空白狀態超過5秒。</span><span class="sxs-lookup"><span data-stu-id="9751d-567">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="9751d-568">建議</span><span class="sxs-lookup"><span data-stu-id="9751d-568">Recommendations</span></span>

* <span data-ttu-id="9751d-569">提供資料載入 animator，顯示當使用者可能會察覺到此應用程式停止或損毀時的進度。</span><span class="sxs-lookup"><span data-stu-id="9751d-569">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="9751d-570">合理的經驗法則是任何可能需要5秒以上的「載入」活動。</span><span class="sxs-lookup"><span data-stu-id="9751d-570">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="9751d-571">資源</span><span class="sxs-lookup"><span data-stu-id="9751d-571">Resources</span></span>

* [<span data-ttu-id="9751d-572">顯示進度</span><span class="sxs-lookup"><span data-stu-id="9751d-572">Displaying progress</span></span>](../../design/progress.md)