---
title: 色彩、光線和材質
description: 設計混合實境的內容時，必須仔細考慮您體驗中所使用的每個視覺資產的色彩、光源和材質。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、色彩、燈光、材質、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 9333be5316f5b3ba317aac3ef8591c0dd65370d4
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702784"
---
# <a name="color-light-and-materials"></a><span data-ttu-id="87b15-104">色彩、燈光和材質</span><span class="sxs-lookup"><span data-stu-id="87b15-104">Color, light and materials</span></span>
![色彩、光線和材質](images/RemoteRendering.jpg)

<span data-ttu-id="87b15-106">設計混合實境的內容時，必須仔細考慮您體驗中所使用的每個視覺資產的色彩、光源和材質。</span><span class="sxs-lookup"><span data-stu-id="87b15-106">Designing content for mixed reality requires careful consideration of color, lighting, and materials for each of the visual assets used in your experience.</span></span> <span data-ttu-id="87b15-107">這些決策適用于美觀用途，例如使用燈光和材質來設定沉浸式環境的色調，以及功能性用途，例如使用驚人的色彩來警示使用者即將發生的動作。</span><span class="sxs-lookup"><span data-stu-id="87b15-107">These decisions can be for both aesthetic purposes, like using light and material to set the tone of an immersive environment, and functional purposes, like using striking colors to alert users of an impending action.</span></span> <span data-ttu-id="87b15-108">每個決策都必須根據您體驗的目標裝置的商機和限制進行權衡。</span><span class="sxs-lookup"><span data-stu-id="87b15-108">Each of these decisions must be weighed against the opportunities and constraints of your experience’s target device.</span></span>

<span data-ttu-id="87b15-109">以下是在沉浸式和全像攝影耳機上轉譯資產的特定指導方針。</span><span class="sxs-lookup"><span data-stu-id="87b15-109">Below are guidelines specific to rendering assets on both immersive and holographic headsets.</span></span> <span data-ttu-id="87b15-110">其中有許多與其他技術領域緊密相關，而相關的主題清單則可在本文結尾的 [ [另請參閱](color-light-and-materials.md#see-also) ] 區段中找到。</span><span class="sxs-lookup"><span data-stu-id="87b15-110">Many of these are closely tied to other technical areas and a list of related subjects can be found in the [See also](color-light-and-materials.md#see-also) section at the end of this article.</span></span>

## <a name="rendering-on-immersive-vs-holographic-devices"></a><span data-ttu-id="87b15-111">在沉浸式和全像攝影裝置上轉譯</span><span class="sxs-lookup"><span data-stu-id="87b15-111">Rendering on immersive vs. holographic devices</span></span>

<span data-ttu-id="87b15-112">相較于全像攝影耳機中轉譯的內容，在沉浸式耳機中轉譯的內容會以視覺化方式呈現。</span><span class="sxs-lookup"><span data-stu-id="87b15-112">Content rendered in immersive headsets will appear visually different when compared to content rendered in holographic headsets.</span></span> <span data-ttu-id="87b15-113">雖然沉浸式耳機通常會像在2D 螢幕上一樣地轉譯內容，但 HoloLens 這類的全息耳機會使用色彩順序，請參閱-透過 RGB 顯示來轉譯全像投影。</span><span class="sxs-lookup"><span data-stu-id="87b15-113">While immersive headsets generally render content much as you would expect on a 2D screen, holographic headsets like HoloLens use color-sequential, see-through RGB displays to renders holograms.</span></span>

<span data-ttu-id="87b15-114">永遠花時間在全像攝影耳機中測試您的全像攝影體驗。</span><span class="sxs-lookup"><span data-stu-id="87b15-114">Always take time to test your holographic experiences in a holographic headset.</span></span> <span data-ttu-id="87b15-115">即使是針對全像全像裝置所建立的內容，其外觀也會隨著次要監視器、快照和 spectator view 中的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="87b15-115">The appearance of content, even if it is built specifically for holographic devices, will differ as seen on secondary monitors, snapshots, and in spectator view.</span></span> <span data-ttu-id="87b15-116">請記住，您可以使用裝置的體驗、測試全像投影的燈光，以及觀察所有邊的 (以及上方和下方，) 內容轉譯的方式。</span><span class="sxs-lookup"><span data-stu-id="87b15-116">Remember to walk around experiences with a device, testing the lighting of holograms and observing from all sides (as well as from above and below) how your content is rendered.</span></span> <span data-ttu-id="87b15-117">請務必在裝置上的一系列亮度設定上進行測試，因為不太可能所有的使用者都會共用假設的預設值，以及一組不同的光源條件。</span><span class="sxs-lookup"><span data-stu-id="87b15-117">Be sure to test at a range of brightness settings on the device, as it is unlikely all users will share an assumed default, as well as a diverse set of lighting conditions.</span></span>

## <a name="fundamentals-of-rendering-on-holographic-devices"></a><span data-ttu-id="87b15-118">在全像裝置上呈現的基本概念</span><span class="sxs-lookup"><span data-stu-id="87b15-118">Fundamentals of rendering on holographic devices</span></span>
* <span data-ttu-id="87b15-119">全像 **裝置具有** 加總顯示器–將燈光從真實世界的光線中增加，以建立全像白色，白色會顯示為明亮，而黑色會顯示為透明。</span><span class="sxs-lookup"><span data-stu-id="87b15-119">**Holographic devices have additive displays** – Holograms are created by adding light to the light from the real world – white will appear brightly, while black will appear transparent.</span></span>

* <span data-ttu-id="87b15-120">**色彩影響會隨著使用者的環境而有所不同** -使用者的房間內有許多不同的光源。</span><span class="sxs-lookup"><span data-stu-id="87b15-120">**Colors impact varies with the user’s environment** – There are many diverse lighting conditions in a user’s room.</span></span> <span data-ttu-id="87b15-121">建立具有適當對比層級的內容，以利清楚說明。</span><span class="sxs-lookup"><span data-stu-id="87b15-121">Create content with appropriate levels of contrast to help with clarity.</span></span>

* <span data-ttu-id="87b15-122">**避免動態照明** –在全像全像全像全像全像的全像全像全像全像全像</span><span class="sxs-lookup"><span data-stu-id="87b15-122">**Avoid dynamic lighting** – Holograms that are uniformly lit in holographic experiences are the most efficient.</span></span> <span data-ttu-id="87b15-123">使用 advanced、動態光源可能會超過行動裝置的功能。</span><span class="sxs-lookup"><span data-stu-id="87b15-123">Using advanced, dynamic lighting will likely exceed the capabilities of mobile devices.</span></span> <span data-ttu-id="87b15-124">當需要動態光源時，建議使用 [混合現實工具組標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)。</span><span class="sxs-lookup"><span data-stu-id="87b15-124">When dynamic lighting is required, it is recommended to use the [Mixed Reality Toolkit Standard shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md).</span></span> 

## <a name="designing-with-color"></a><span data-ttu-id="87b15-125">使用色彩設計</span><span class="sxs-lookup"><span data-stu-id="87b15-125">Designing with color</span></span>

<span data-ttu-id="87b15-126">由於加法顯示器的本質，某些色彩在全像全像顯示器上可能會不同。</span><span class="sxs-lookup"><span data-stu-id="87b15-126">Due to the nature of additive displays, certain colors can appear different on holographic displays.</span></span> <span data-ttu-id="87b15-127">某些色彩會在照明環境中顯示，有些則會顯示為較少的具影響力。</span><span class="sxs-lookup"><span data-stu-id="87b15-127">Some colors will pop in lighting environments while others will appear as less impactful.</span></span> <span data-ttu-id="87b15-128">很酷的色彩通常會 recede 到背景，而暖色彩則會跳到前景。</span><span class="sxs-lookup"><span data-stu-id="87b15-128">Cool colors tend to recede into the background while warm colors jump to the foreground.</span></span> <span data-ttu-id="87b15-129">當您在體驗中探索色彩時，請考慮下列因素：</span><span class="sxs-lookup"><span data-stu-id="87b15-129">Consider these factors as you explore color in your experiences:</span></span>

* <span data-ttu-id="87b15-130">轉譯 **淺色色彩**-白色顯示非常亮，應謹慎使用。</span><span class="sxs-lookup"><span data-stu-id="87b15-130">**Rendering light colors** - White appears very bright and should be used sparingly.</span></span> <span data-ttu-id="87b15-131">在大部分的情況下，請考慮有關 R 235 G 235 B 235 的白色值。</span><span class="sxs-lookup"><span data-stu-id="87b15-131">For most cases, consider a white value around R 235 G 235 B 235.</span></span> <span data-ttu-id="87b15-132">很亮的區域可能會導致使用者不適感。</span><span class="sxs-lookup"><span data-stu-id="87b15-132">Large bright areas may cause user discomfort.</span></span> <span data-ttu-id="87b15-133">針對 UI 視窗的 backplate，建議使用深色色彩。</span><span class="sxs-lookup"><span data-stu-id="87b15-133">For the UI window's backplate, it is recommended to use dark colors.</span></span>

* <span data-ttu-id="87b15-134">轉譯 **深色色彩**-由於加法顯示器的本質，深色色彩會顯示為透明。</span><span class="sxs-lookup"><span data-stu-id="87b15-134">**Rendering dark colors** - Due to the nature of additive displays, dark colors appear transparent.</span></span> <span data-ttu-id="87b15-135">實心的黑色物件看起來與真實世界沒有不同。</span><span class="sxs-lookup"><span data-stu-id="87b15-135">A solid black object will appear no different from the real world.</span></span> <span data-ttu-id="87b15-136">請參閱下列 Alpha 通道。</span><span class="sxs-lookup"><span data-stu-id="87b15-136">See Alpha channel below.</span></span> <span data-ttu-id="87b15-137">若要提供 "黑色" 的外觀，請嘗試相當深的灰色 RGB 值，例如16、16、16。</span><span class="sxs-lookup"><span data-stu-id="87b15-137">To give the appearance of “black” try a very dark grey RGB value such as 16,16,16.</span></span>

* <span data-ttu-id="87b15-138">**色彩一致性** ：通常會將全像影像轉譯為明亮，使其維持色彩一致性，不論背景為何。</span><span class="sxs-lookup"><span data-stu-id="87b15-138">**Color uniformity** - Typically holograms are rendered brightly enough so that they maintain color uniformity, regardless of the background.</span></span> <span data-ttu-id="87b15-139">大型區域可能會變成 blotchy。</span><span class="sxs-lookup"><span data-stu-id="87b15-139">Large areas may become blotchy.</span></span> <span data-ttu-id="87b15-140">避免大型區域的明亮、單色。</span><span class="sxs-lookup"><span data-stu-id="87b15-140">Avoid large regions of bright, solid color.</span></span>

* <span data-ttu-id="87b15-141">從 **色彩的「** 寬範圍」來獲益，在概念上類似 Adobe RGB。</span><span class="sxs-lookup"><span data-stu-id="87b15-141">**Gamut** - HoloLens benefits from a "wide gamut" of color, conceptually similar to Adobe RGB.</span></span> <span data-ttu-id="87b15-142">因此，某些色彩可能會顯示裝置中的不同品質和標記法。</span><span class="sxs-lookup"><span data-stu-id="87b15-142">As a result, some colors can exhibit different qualities and representation in the device.</span></span>

* <span data-ttu-id="87b15-143">**Gamma** -轉譯影像的亮度和對比在沉浸式和全像全像裝置之間會有所不同。</span><span class="sxs-lookup"><span data-stu-id="87b15-143">**Gamma** - The brightness and contrast of the rendered image will vary between immersive and holographic devices.</span></span> <span data-ttu-id="87b15-144">這些裝置的差異通常會讓色彩和陰影的暗區出現、更多或更不亮。</span><span class="sxs-lookup"><span data-stu-id="87b15-144">These device differences often appear to make dark areas of color and shadows, more or less bright.</span></span>

* <span data-ttu-id="87b15-145">**色彩分隔** -也稱為 "color 並劃分" 或 "color fringing"，最常見的色彩分隔是在使用者以眼睛追蹤物件時，將游標) 移動 (包括游標。</span><span class="sxs-lookup"><span data-stu-id="87b15-145">**Color separation** - Also called "color breakup" or "color fringing", color separation most commonly occurs with moving holograms (including cursor) when a user tracks objects with their eyes.</span></span>

## <a name="technical-considerations"></a><span data-ttu-id="87b15-146">技術考量</span><span class="sxs-lookup"><span data-stu-id="87b15-146">Technical considerations</span></span>
* <span data-ttu-id="87b15-147">**別名** -明智失真、不規則或「樓梯步驟」，其中全像是全像真實世界的影像。</span><span class="sxs-lookup"><span data-stu-id="87b15-147">**Aliasing** - Be considerate of aliasing, jagged or “stair steps” where the edge of a hologram’s geometry meets the real world.</span></span> <span data-ttu-id="87b15-148">使用具有高詳細資料的材質可以加劇此效果。</span><span class="sxs-lookup"><span data-stu-id="87b15-148">Using textures with high detail can aggravate this effect.</span></span> <span data-ttu-id="87b15-149">紋理應對應並啟用篩選。</span><span class="sxs-lookup"><span data-stu-id="87b15-149">Textures should be mapped and filtering enabled.</span></span> <span data-ttu-id="87b15-150">請考慮淡化全像影像的邊緣，或新增紋理來建立物件周圍的黑色邊緣框線。</span><span class="sxs-lookup"><span data-stu-id="87b15-150">Consider fading the edges of holograms or adding a texture that creates a black edge border around objects.</span></span> <span data-ttu-id="87b15-151">盡可能避免精簡型幾何。</span><span class="sxs-lookup"><span data-stu-id="87b15-151">Avoid thin geometry where possible.</span></span>

* <span data-ttu-id="87b15-152">**Alpha** 色板-您必須針對未呈現全像影像的任何部分，清除您的 Alpha 色板以完全透明。</span><span class="sxs-lookup"><span data-stu-id="87b15-152">**Alpha channel** - You must clear your alpha channel to fully transparent for any parts where you are not rendering a hologram.</span></span> <span data-ttu-id="87b15-153">從裝置或使用 Spectator View 取得影像/影片時，讓 Alpha 未定義的會導致視覺構件。</span><span class="sxs-lookup"><span data-stu-id="87b15-153">Leaving the alpha undefined leads to visual artifacts when taking images/videos from the device or with Spectator View.</span></span>

* <span data-ttu-id="87b15-154">**紋理的軟化** -因為光線是在全像全像投影上的加總，所以最好避免較大的區域，因為通常不會產生預期的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="87b15-154">**Texture softening** - Since light is additive in holographic displays, it is best to avoid large regions of bright, solid color as they often do not produce the intended visual effect.</span></span>

## <a name="design-guidelines-for-holographic-display"></a><span data-ttu-id="87b15-155">全像顯示器的設計方針</span><span class="sxs-lookup"><span data-stu-id="87b15-155">Design guidelines for holographic display</span></span>
![色彩和手遮蔽](images/color_handocclusion.jpg)

<span data-ttu-id="87b15-157">在設計全像顯示器的內容時，有數個您需要考慮的元素，以達到最佳體驗。</span><span class="sxs-lookup"><span data-stu-id="87b15-157">When designing content for holographic displays, there are several elements that you need to consider achieving the best experience.</span></span> <span data-ttu-id="87b15-158">如需指導方針和建議，請造訪 [設計內容以進行](designing-content-for-holographic-display.md) 全像顯示。</span><span class="sxs-lookup"><span data-stu-id="87b15-158">Please visit [Designing content for holographic display](designing-content-for-holographic-display.md) for the guidelines and recommendations.</span></span>

## <a name="storytelling-with-light-and-color"></a><span data-ttu-id="87b15-159">具有淺色和色彩的故事行銷</span><span class="sxs-lookup"><span data-stu-id="87b15-159">Storytelling with light and color</span></span>

<span data-ttu-id="87b15-160">Light 和 color 可協助讓您的全息體在使用者的環境中以更自然的方式出現，以及提供使用者的指引和協助。</span><span class="sxs-lookup"><span data-stu-id="87b15-160">Light and color can help make your holograms appear more naturally in a user's environment as well as offer guidance and help for the user.</span></span> <span data-ttu-id="87b15-161">針對全像攝影經驗，請在探索光源和色彩時考慮這些因素：</span><span class="sxs-lookup"><span data-stu-id="87b15-161">For holographic experiences, consider these factors as you explore lighting and color:</span></span>

:::row:::
    :::column:::
* <span data-ttu-id="87b15-162">**Vignetting** -將材質的「vignette」效果變暗有助於將使用者的注意力集中在視野的中心。</span><span class="sxs-lookup"><span data-stu-id="87b15-162">**Vignetting** - A 'vignette' effect to darken materials can help focus the user's attention on the center of the field of view.</span></span> <span data-ttu-id="87b15-163">此效果會從使用者的注視向量中，以某些半徑來加深全息圖的材質。</span><span class="sxs-lookup"><span data-stu-id="87b15-163">This effect darkens the hologram's material at some radius from the user's gaze vector.</span></span> <span data-ttu-id="87b15-164">請注意，當使用者從傾斜或 glancing 角度來查看全像投影時，這也會有效。</span><span class="sxs-lookup"><span data-stu-id="87b15-164">Note that this is also effective when the user views holograms from an oblique or glancing angle.</span></span>

* <span data-ttu-id="87b15-165">**強調** -透過對比色彩、亮度和光源來吸引物件或互動點。</span><span class="sxs-lookup"><span data-stu-id="87b15-165">**Emphasis** - Draw attention to objects or points of interaction by contrasting colors, brightness, and lighting.</span></span> <span data-ttu-id="87b15-166">如需故事行銷中的燈光方法詳細資訊，請參閱 [圖元 Cinematography-電腦圖形的照明方法](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)。</span><span class="sxs-lookup"><span data-stu-id="87b15-166">For a more detailed look at lighting methods in storytelling, see [Pixel Cinematography - A Lighting Approach for Computer Graphics](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).</span></span><br>
        <br>
        <span data-ttu-id="87b15-167">*影像：使用色彩來顯示故事行銷元素的強調，此處顯示于 [片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)的場景中。*</span><span class="sxs-lookup"><span data-stu-id="87b15-167">*Image: Use of color to show emphasis for storytelling elements, shown here in a scene from [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*</span></span>
    :::column-end:::
        :::column:::
        ![使用色彩來顯示故事行銷元素的強調，此處顯示于片段中的場景。](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a><span data-ttu-id="87b15-169">材質</span><span class="sxs-lookup"><span data-stu-id="87b15-169">Materials</span></span>

:::row:::
    :::column:::
<span data-ttu-id="87b15-170">材質是建立逼真全像影像的重要元素。</span><span class="sxs-lookup"><span data-stu-id="87b15-170">Materials are crucial elements for making realistic holograms.</span></span> <span data-ttu-id="87b15-171">藉由提供適當的視覺特性，您可以建立吸引人的全像攝影物件，以便與實體環境完美結合。</span><span class="sxs-lookup"><span data-stu-id="87b15-171">By providing proper visual characteristics, you can make compelling holographic objects that can blend well with the physical environment.</span></span> <span data-ttu-id="87b15-172">對於為各種類型的使用者輸入互動提供視覺化意見反應，材質也很重要。</span><span class="sxs-lookup"><span data-stu-id="87b15-172">Materials are also important for providing visual feedback for the various types of user input interactions.</span></span>  

<span data-ttu-id="87b15-173">[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) 提供具有各種視覺效果選項的 MRTK 標準著色器，可用於視覺效果的意見反應。</span><span class="sxs-lookup"><span data-stu-id="87b15-173">[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides an MRTK Standard Shader with various visual effect options that can be used for visual feedback.</span></span> <span data-ttu-id="87b15-174">例如，您可以使用「近亮」屬性，在使用者的手指接近物件的介面時，提供光源效果。</span><span class="sxs-lookup"><span data-stu-id="87b15-174">For example, you can use 'Proximity Light' property to provide a lighting effect when the user's finger is approaching the object's surface.</span></span> <span data-ttu-id="87b15-175">深入瞭解 [MRTK 標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)</span><span class="sxs-lookup"><span data-stu-id="87b15-175">Learn more about [MRTK Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)</span></span>
    :::column-end:::
        :::column:::
    <span data-ttu-id="87b15-176">*影片迴圈：根據鄰近範圍* 
     ![ 方塊的視覺效果意見反應範例關於手近距離的視覺回饋](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="87b15-176">*Video loop: Example of visual feedback based on proximity to a bounding box*
![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span>

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a><span data-ttu-id="87b15-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87b15-177">See also</span></span>
* [<span data-ttu-id="87b15-178">設計全像攝影顯示器的內容</span><span class="sxs-lookup"><span data-stu-id="87b15-178">Designing content for holographic display</span></span>](designing-content-for-holographic-display.md)
* [<span data-ttu-id="87b15-179">色彩分隔</span><span class="sxs-lookup"><span data-stu-id="87b15-179">Color Separation</span></span>](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [<span data-ttu-id="87b15-180">全像投影</span><span class="sxs-lookup"><span data-stu-id="87b15-180">Holograms</span></span>](../discover/hologram.md)
* [<span data-ttu-id="87b15-181">Microsoft 設計語言-色彩</span><span class="sxs-lookup"><span data-stu-id="87b15-181">Microsoft Design Language - color</span></span>](https://www.microsoft.com/design/color)
* [<span data-ttu-id="87b15-182">通用 Windows 平臺-色彩</span><span class="sxs-lookup"><span data-stu-id="87b15-182">Universal Windows Platform - color</span></span>](https://docs.microsoft.com/windows/uwp/style/color)
