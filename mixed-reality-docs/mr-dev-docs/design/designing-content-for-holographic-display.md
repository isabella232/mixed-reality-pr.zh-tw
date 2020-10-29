---
title: 設計全像顯示器的內容
description: 全像顯示器的設計方針和最佳作法
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 設計、全像顯示、內容設計、深色主題、淺色主題
ms.openlocfilehash: 627ffdd0a413ad3140c29e9b1c7bb69c9dc249cf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680476"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="0a82f-104">設計全像顯示器的內容</span><span class="sxs-lookup"><span data-stu-id="0a82f-104">Designing content for holographic display</span></span>

![Ulnar 側邊位置](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="0a82f-106">在設計全像顯示器的內容時，您必須考慮幾個元素，才能達到最佳體驗。</span><span class="sxs-lookup"><span data-stu-id="0a82f-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="0a82f-107">我們已在下方列出一些建議，而您可以在 [ [色彩]、[淺色] 和 [材質](color-light-and-materials.md) ] 頁面上深入瞭解全像攝影顯示器的特性。</span><span class="sxs-lookup"><span data-stu-id="0a82f-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="0a82f-108">在大型表面上具有亮色的挑戰</span><span class="sxs-lookup"><span data-stu-id="0a82f-108">Challenges with bright color on a large surface</span></span> 
<span data-ttu-id="0a82f-109">根據我們的使用者研究和測試各種類型的 HoloLens 體驗，我們發現在顯示的大型區域中使用亮色可能會導致數個問題：</span><span class="sxs-lookup"><span data-stu-id="0a82f-109">Based on our user research and testing on various types of HoloLens experiences, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="0a82f-110">**眼睛疲勞**</span><span class="sxs-lookup"><span data-stu-id="0a82f-110">**Eye fatigue**</span></span> 

<span data-ttu-id="0a82f-111">因為全像顯示是加總，所以明亮的色彩會使用較淺的光線來顯示全像。</span><span class="sxs-lookup"><span data-stu-id="0a82f-111">Since holographic display is additive, bright color uses more light to display holograms.</span></span> <span data-ttu-id="0a82f-112">在顯示的大型區域中，很亮的純色可能會讓使用者很容易就能疲勞。</span><span class="sxs-lookup"><span data-stu-id="0a82f-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="0a82f-113">**手遮蔽**</span><span class="sxs-lookup"><span data-stu-id="0a82f-113">**Hand occlusion**</span></span> 

<span data-ttu-id="0a82f-114">明亮的色彩讓使用者在直接與物件互動時，難以看到他們的手。</span><span class="sxs-lookup"><span data-stu-id="0a82f-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="0a82f-115">由於使用者看不到他們的手，因此難以觀察手指/指標與目標表面之間的深度/距離。</span><span class="sxs-lookup"><span data-stu-id="0a82f-115">Since the user cannot see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="0a82f-116">手指指標有助於彌補這個問題，但在亮白表面上仍然很有挑戰性。</span><span class="sxs-lookup"><span data-stu-id="0a82f-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="0a82f-117">![色彩和手遮蔽 ](images/color_handocclusion.jpg)
 *很難看到明亮的彩色內容 backplate*</span><span class="sxs-lookup"><span data-stu-id="0a82f-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="0a82f-118">**色彩一致性**</span><span class="sxs-lookup"><span data-stu-id="0a82f-118">**Color uniformity**</span></span>

<span data-ttu-id="0a82f-119">由於全息型顯示器的特性，顯示器上的大型區域可能會變成 blotchy。</span><span class="sxs-lookup"><span data-stu-id="0a82f-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="0a82f-120">藉由使用深色配置，您可以將此問題降至最低。</span><span class="sxs-lookup"><span data-stu-id="0a82f-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines"></a><span data-ttu-id="0a82f-121">設計指導方針</span><span class="sxs-lookup"><span data-stu-id="0a82f-121">Design guidelines</span></span>

<span data-ttu-id="0a82f-122">**針對 UI 背景使用深色色彩**</span><span class="sxs-lookup"><span data-stu-id="0a82f-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="0a82f-123">藉由使用深色色彩配置，您可以將眼睛疲勞降到最低，並改善直接互動的信賴度。</span><span class="sxs-lookup"><span data-stu-id="0a82f-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="0a82f-124">![深色 UI 範例， ](images/color_dark_examples.jpg)
 *用於內容背景的深色色彩*</span><span class="sxs-lookup"><span data-stu-id="0a82f-124">![Dark UI examples](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="0a82f-125">**使用 semibold 或粗體字型粗細**</span><span class="sxs-lookup"><span data-stu-id="0a82f-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="0a82f-126">HoloLens 可讓您的體驗顯示美觀的高解析度文字。</span><span class="sxs-lookup"><span data-stu-id="0a82f-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="0a82f-127">不過，建議您避免使用淺色或半淺色等細字型粗細，因為垂直筆觸可能會以小型字型大小來抖動。</span><span class="sxs-lookup"><span data-stu-id="0a82f-127">However, it is recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="0a82f-128">![深色 UI 範例 ](images/color_font_examples.jpg)
 *粗體或粗體字型粗細 (上方面板) 改善可讀性*</span><span class="sxs-lookup"><span data-stu-id="0a82f-128">![Dark UI examples](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="0a82f-129">**使用 MRTK 的 HolographicBackplate 材質**</span><span class="sxs-lookup"><span data-stu-id="0a82f-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="0a82f-130">HolographicBackplate 材質會套用至 HoloLens shell 中的數個 UI 面板。</span><span class="sxs-lookup"><span data-stu-id="0a82f-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="0a82f-131">它的其中一個功能是 iridescence 效果，使用者會在相對於面板的位置切換其位置時看到此效果。</span><span class="sxs-lookup"><span data-stu-id="0a82f-131">One of its features is an iridescence effect that is visible to users as they shift their position in relation to the panel.</span></span> <span data-ttu-id="0a82f-132">Backplate 色彩會在預先定義的頻譜之間稍微移動、建立吸引人且動態的視覺效果，而不會干擾內容的可讀性。</span><span class="sxs-lookup"><span data-stu-id="0a82f-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="0a82f-133">這種微妙的色彩變換也可彌補任何次要色彩的不規則。</span><span class="sxs-lookup"><span data-stu-id="0a82f-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="0a82f-134">透明或半透明 UI backplate 的挑戰</span><span class="sxs-lookup"><span data-stu-id="0a82f-134">Challenges with transparent or translucent UI backplate</span></span> 
<span data-ttu-id="0a82f-135">![透明 ui 的透明 ui 範例 ](images/color_transparent_examples.jpg)
 *backplate*</span><span class="sxs-lookup"><span data-stu-id="0a82f-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="0a82f-136">**視覺效果複雜性和協助工具**</span><span class="sxs-lookup"><span data-stu-id="0a82f-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="0a82f-137">由於全像全像實體環境的混合式物件，在透明或半透明視窗上，內容或 UI 的可讀性可能會降低。</span><span class="sxs-lookup"><span data-stu-id="0a82f-137">Since holographic objects are blended with the physical environment, the legibility of the content or UI on the transparent or translucent window could be degraded.</span></span> <span data-ttu-id="0a82f-138">此外，當透明的全像全像全像的物件彼此重迭時，它可能會讓使用者難以進行互動，因為這會造成混淆的深度。</span><span class="sxs-lookup"><span data-stu-id="0a82f-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="0a82f-139">**效能**</span><span class="sxs-lookup"><span data-stu-id="0a82f-139">**Performance**</span></span>

<span data-ttu-id="0a82f-140">若要正確轉譯透明或半透明的物件，必須使用存在於背景中的任何物件來排序和混合。</span><span class="sxs-lookup"><span data-stu-id="0a82f-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects which exist in the background.</span></span> <span data-ttu-id="0a82f-141">透明物件的排序具有適度的 CPU 成本，因此混合具有相當大的 GPU 成本，因為它不允許 GPU 透過 z 剔除來執行隱藏的介面移除 (例如</span><span class="sxs-lookup"><span data-stu-id="0a82f-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it does not allow the GPU to perform hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="0a82f-142">深度測試) 。</span><span class="sxs-lookup"><span data-stu-id="0a82f-142">depth testing).</span></span> <span data-ttu-id="0a82f-143">不允許隱藏的介面移除會增加需要針對最終轉譯圖元計算的作業數目，因此會對填滿率條件約束造成更大的壓力。</span><span class="sxs-lookup"><span data-stu-id="0a82f-143">Not allowing hidden surface removal increases the number of operations that need to be computed for the final rendered pixel, and thus puts more pressure on fill rate constraints.</span></span>

<span data-ttu-id="0a82f-144">**深度 LSR 技術的全像穩定性問題**</span><span class="sxs-lookup"><span data-stu-id="0a82f-144">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="0a82f-145">若要改善全像攝影 reprojection 或全像全像全像全像，應用程式可以為每個轉譯的畫面格提交深度緩衝區至系統。</span><span class="sxs-lookup"><span data-stu-id="0a82f-145">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="0a82f-146">當您使用 reprojection 的深度緩衝區時，其中一個規則是，每個呈現對應深度值的色彩圖元都必須寫入深度緩衝區 (而且具有深度值的任何圖元也都應該有色彩值) 。</span><span class="sxs-lookup"><span data-stu-id="0a82f-146">When using the depth buffer for reprojection one rule is that for every color pixel rendered a corresponding depth value must be written to the depth buffer (and any pixel with a depth value should also have color value).</span></span> <span data-ttu-id="0a82f-147">如果未遵循上述指導方針，則會以產生成品的方式 reprojected 已轉譯影像的區域，而產生成品 (通常會顯示為類似 wave 的扭曲) 。</span><span class="sxs-lookup"><span data-stu-id="0a82f-147">If the above guidance is not followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts (often visible as a wave-like distortion).</span></span>


## <a name="design-guidelines"></a><span data-ttu-id="0a82f-148">設計指導方針</span><span class="sxs-lookup"><span data-stu-id="0a82f-148">Design guidelines</span></span>
<span data-ttu-id="0a82f-149">**使用不透明的 UI 背景**</span><span class="sxs-lookup"><span data-stu-id="0a82f-149">**Use opaque UI background**</span></span>

<span data-ttu-id="0a82f-150">根據預設，透明或透明物件不會寫入深度來允許適當的混合。</span><span class="sxs-lookup"><span data-stu-id="0a82f-150">By default, transparent or translucent objects do not write depth to allow for proper blending.</span></span> <span data-ttu-id="0a82f-151">解決此問題的方法包括：使用不透明的物件，以確保透明物件出現在不透明的物件 (例如半透明按鈕（不透明的 backplate) ）、強制透明物件寫入深度 (不適用於) 的所有案例，或轉譯只在框架結尾提供深度值的 proxy 物件。</span><span class="sxs-lookup"><span data-stu-id="0a82f-151">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="0a82f-152">MRTK 中的解決方案-Unity： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="0a82f-152">Solutions within MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="0a82f-153">藉由使用穩固且不透明的 backplate，我們可以保障可讀性和互動的信賴度。</span><span class="sxs-lookup"><span data-stu-id="0a82f-153">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="0a82f-154">**將受影響的圖元數目降至最低**</span><span class="sxs-lookup"><span data-stu-id="0a82f-154">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="0a82f-155">如果您的專案必須使用透明物件，請儘量減少受影響的圖元數目。</span><span class="sxs-lookup"><span data-stu-id="0a82f-155">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="0a82f-156">例如，如果只有在特定條件下才會顯示物件 (例如加亮光暈效果) ，則在完全隱藏時，請停用該物件 (而不是將加法色彩設定為黑色) 。</span><span class="sxs-lookup"><span data-stu-id="0a82f-156">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it is fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="0a82f-157">針對使用具有 Alpha 遮罩之四色的簡單2D 圖形，請考慮改為使用不透明著色器來建立圖形的網格標記法。</span><span class="sxs-lookup"><span data-stu-id="0a82f-157">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="0a82f-158">適用于 Unity 的 MRTK (混合現實工具組) 的深色 UI 範例</span><span class="sxs-lookup"><span data-stu-id="0a82f-158">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="0a82f-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 會根據深色色彩配置提供許多 UI 建立區塊範例。</span><span class="sxs-lookup"><span data-stu-id="0a82f-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="0a82f-160">近端功能表</span><span class="sxs-lookup"><span data-stu-id="0a82f-160">Near Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [<span data-ttu-id="0a82f-161">對話方塊</span><span class="sxs-lookup"><span data-stu-id="0a82f-161">Dialog</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [<span data-ttu-id="0a82f-162">手形功能表</span><span class="sxs-lookup"><span data-stu-id="0a82f-162">Hand Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="0a82f-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a82f-163">See also</span></span>
* [<span data-ttu-id="0a82f-164">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="0a82f-164">Color, light and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="0a82f-165">游標</span><span class="sxs-lookup"><span data-stu-id="0a82f-165">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="0a82f-166">手部光線</span><span class="sxs-lookup"><span data-stu-id="0a82f-166">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="0a82f-167">Button</span><span class="sxs-lookup"><span data-stu-id="0a82f-167">Button</span></span>](button.md)
* [<span data-ttu-id="0a82f-168">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="0a82f-168">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="0a82f-169">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="0a82f-169">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="0a82f-170">操作</span><span class="sxs-lookup"><span data-stu-id="0a82f-170">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0a82f-171">手部功能表</span><span class="sxs-lookup"><span data-stu-id="0a82f-171">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="0a82f-172">近端功能表</span><span class="sxs-lookup"><span data-stu-id="0a82f-172">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="0a82f-173">物件集合</span><span class="sxs-lookup"><span data-stu-id="0a82f-173">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="0a82f-174">語音命令</span><span class="sxs-lookup"><span data-stu-id="0a82f-174">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="0a82f-175">鍵盤</span><span class="sxs-lookup"><span data-stu-id="0a82f-175">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="0a82f-176">工具提示</span><span class="sxs-lookup"><span data-stu-id="0a82f-176">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="0a82f-177">平板</span><span class="sxs-lookup"><span data-stu-id="0a82f-177">Slate</span></span>](slate.md)
* [<span data-ttu-id="0a82f-178">滑桿</span><span class="sxs-lookup"><span data-stu-id="0a82f-178">Slider</span></span>](slider.md)
* [<span data-ttu-id="0a82f-179">著色器</span><span class="sxs-lookup"><span data-stu-id="0a82f-179">Shader</span></span>](shader.md)
* [<span data-ttu-id="0a82f-180">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="0a82f-180">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="0a82f-181">顯示進度</span><span class="sxs-lookup"><span data-stu-id="0a82f-181">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="0a82f-182">表面磁性</span><span class="sxs-lookup"><span data-stu-id="0a82f-182">Surface magnetism</span></span>](surface-magnetism.md)
