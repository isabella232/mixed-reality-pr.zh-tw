---
title: Unity 中的文字
description: 若要在 Unity 中顯示文字，您可以使用兩種類型的文字元件： UI 文字和3D 文字網格。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、控制項、字型、印刷樣式、ui、ux、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: dde8989998cf422c40ada927c0d8462cb4cd97b9
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489278"
---
# <a name="text-in-unity"></a><span data-ttu-id="af028-104">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="af028-104">Text in Unity</span></span>

<span data-ttu-id="af028-105">文字是全像攝影應用程式中最重要的元件之一。</span><span class="sxs-lookup"><span data-stu-id="af028-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="af028-106">若要在 Unity 中顯示文字，有三種類型的文字元件可供您使用： UI 文字、3D 文字網格和文字網格 Pro。</span><span class="sxs-lookup"><span data-stu-id="af028-106">To display text in Unity, there are three types of text components you can use—UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="af028-107">根據預設，UI 文字和3D 文字網格會顯示為模糊且太大。</span><span class="sxs-lookup"><span data-stu-id="af028-107">By default, UI Text and 3D Text Mesh appear blurry and are too large.</span></span> <span data-ttu-id="af028-108">變更幾個變數會產生更清晰、品質較高的文字，並在 HoloLens 中提供可管理的大小。</span><span class="sxs-lookup"><span data-stu-id="af028-108">Changing a few variables results in sharper, higher-quality text with a manageable size in HoloLens.</span></span> <span data-ttu-id="af028-109">使用 UI 文字和3D 文字網格元件時，您可以套用縮放比例來取得適當的維度，以達到更佳的轉譯品質。</span><span class="sxs-lookup"><span data-stu-id="af028-109">You can achieve better rendering quality by applying a scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components.</span></span>

<span data-ttu-id="af028-110">![如何取得清晰且美觀的文字](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="af028-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="af028-111">*Unity 中的模糊預設文字*</span><span class="sxs-lookup"><span data-stu-id="af028-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a><span data-ttu-id="af028-112">使用 Unity 的3D 文字 (文字網格) 和 UI 文字</span><span class="sxs-lookup"><span data-stu-id="af028-112">Working with Unity's 3D Text (Text Mesh) and UI Text</span></span>

<span data-ttu-id="af028-113">Unity 假設所有新增至場景的新元素都是一個 Unity 單位，或100% 的轉換縮放比例。</span><span class="sxs-lookup"><span data-stu-id="af028-113">Unity assumes all new elements added to a scene are one Unity Unit in size, or 100% transform scale.</span></span> <span data-ttu-id="af028-114">一個 Unity 單位會在 HoloLens 上轉譯為約1個計量。</span><span class="sxs-lookup"><span data-stu-id="af028-114">One Unity unit translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="af028-115">若是字型，3D TextMesh 的周框方塊預設會以大約1計量的高度來提供。</span><span class="sxs-lookup"><span data-stu-id="af028-115">For fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="af028-116">![使用 Unity 中的字型](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="af028-116">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="af028-117">*預設的 Unity 3D 文字 (文字網格) 佔用一個 Unity 單位，也就是1個計量*</span><span class="sxs-lookup"><span data-stu-id="af028-117">*Default Unity 3D Text (Text Mesh) occupies one Unity Unit, which is 1 meter*</span></span>

<br>

<span data-ttu-id="af028-118">大部分的視覺化設計工具會使用點來定義真實世界中的字型大小。</span><span class="sxs-lookup"><span data-stu-id="af028-118">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="af028-119">1計量中有大約 2835 (2，834.645666399962) 點。</span><span class="sxs-lookup"><span data-stu-id="af028-119">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="af028-120">根據指向1計量的點系統轉換，以及 Unity 的預設文字網格字型大小13，13的簡單數學運算（13）除以2835等於 0.0046 (0.004586111116 為精確) ，可提供良好的標準尺規來開始 (有些可能想要舍入至 0.005) 。</span><span class="sxs-lookup"><span data-stu-id="af028-120">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) which provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="af028-121">將文字物件或容器調整為這些值並不只允許在設計程式中轉換字型大小的1:1，也提供標準，因此您可以在整個體驗中維持一致性。</span><span class="sxs-lookup"><span data-stu-id="af028-121">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="af028-122">![調整 Unity 3D 文字和 UI 文字的值](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="af028-122">![Scaling values for the Unity 3D Text and UI Text](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="af028-123">*調整 Unity 3D 文字和 UI 文字的值*</span><span class="sxs-lookup"><span data-stu-id="af028-123">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<br>

<span data-ttu-id="af028-124">![具有優化值的 Unity 3D 文字網格](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="af028-124">![Unity 3D Text Mesh with optimized values](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="af028-125">*具有優化值的 Unity 3D 文字網格*</span><span class="sxs-lookup"><span data-stu-id="af028-125">*Unity 3D Text Mesh with optimized values*</span></span>

<br>

<span data-ttu-id="af028-126">將 UI 或畫布型文字元素新增至場景時，大小差異仍會大於。</span><span class="sxs-lookup"><span data-stu-id="af028-126">When adding a UI or canvas-based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="af028-127">這兩種大小的差異大約是1000%，這會將以 UI 為基礎的文字元件的縮放因數帶到 0.00046 (0.0004586111116 為舍入值的精確) 或0.0005。</span><span class="sxs-lookup"><span data-stu-id="af028-127">The differences in the two sizes are about 1000%, which would bring the scale factor for UI-based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="af028-128">![具有優化值的 Unity UI 文字](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="af028-128">![Unity UI Text with optimized values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="af028-129">*具有優化值的 Unity UI 文字*</span><span class="sxs-lookup"><span data-stu-id="af028-129">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="af028-130">任何字型的預設值可能會受到該字型的材質大小或字型匯入 Unity 的影響。</span><span class="sxs-lookup"><span data-stu-id="af028-130">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="af028-131">這些測試是根據 Unity 中的預設 Arial 字型，還有另一個匯入的字型來執行。</span><span class="sxs-lookup"><span data-stu-id="af028-131">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="af028-132">使用文字網格 Pro</span><span class="sxs-lookup"><span data-stu-id="af028-132">Working with Text Mesh Pro</span></span>

<span data-ttu-id="af028-133">您可以使用 Unity 的文字網格 Pro 來保護文字轉譯品質。</span><span class="sxs-lookup"><span data-stu-id="af028-133">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="af028-134">無論使用 [ [帶正負號的距離] 欄位 (.sdf) ](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 技術的距離為何，它都支援清晰的文字外框。</span><span class="sxs-lookup"><span data-stu-id="af028-134">It supports crisp text outlines regardless of the distance using the [Signed Distance Field (SDF)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="af028-135">使用我們針對3D 文字網格和 UI 文字所使用的相同計算方法，我們可以找到適當的縮放比例值，以搭配傳統的印刷點使用。</span><span class="sxs-lookup"><span data-stu-id="af028-135">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find the proper scaling values to use with conventional typographic points.</span></span> <span data-ttu-id="af028-136">因為大小為36的預設3D 文字網格 Pro 字型，其周框大小為 2.5 Unity 單位 (2.5 m) ，所以我們可以使用0.005 值來取得點大小。</span><span class="sxs-lookup"><span data-stu-id="af028-136">Since the default 3D Text Mesh Pro font with the size of 36 has a bounding size of 2.5 Unity units (2.5 m), we can use a scaling value of 0.005 to get the point size.</span></span> <span data-ttu-id="af028-137">UI 功能表下的文字網格 Pro，預設的周框大小為25個 Unity 單位 (25 m) 。</span><span class="sxs-lookup"><span data-stu-id="af028-137">The Text Mesh Pro under the UI menu has a default bounding size of 25 Unity units (25 m).</span></span> <span data-ttu-id="af028-138">這可為我們提供0.0005 的調整值。</span><span class="sxs-lookup"><span data-stu-id="af028-138">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="af028-139">![調整 Unity 3D 文字和 UI 的值](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="af028-139">![Scaling values for the Unity 3D Text and UI](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="af028-140">*調整 Unity 3D 文字和 UI 的值*</span><span class="sxs-lookup"><span data-stu-id="af028-140">*Scaling values for the Unity 3D Text and UI*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="af028-141">建議的文字大小</span><span class="sxs-lookup"><span data-stu-id="af028-141">Recommended text size</span></span>

<span data-ttu-id="af028-142">如您所見，我們在電腦或 (平板電腦上使用的類型大小，通常是在12–32pt 填補) 在兩個度量之間的距離，通常介於12到。</span><span class="sxs-lookup"><span data-stu-id="af028-142">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look small at a distance of 2 meters.</span></span> <span data-ttu-id="af028-143">這取決於每個字型的特性，但在一般情況下，建議的最小觀賞角度和字型高度會根據我們的使用者研究研究，在0.35 °-0.4 °/12.21 13.97 mm 周圍。</span><span class="sxs-lookup"><span data-stu-id="af028-143">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97 mm based on our user research studies.</span></span> <span data-ttu-id="af028-144">這大約是 35-40 pt 和上面介紹的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="af028-144">It's about 35-40 pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="af028-145">針對在 0.45 m (45 cm) 的近距離互動，最小的可辨認字型的觀賞角度和高度是0.4 °-0.5 °/3.14 – 3.9 mm。</span><span class="sxs-lookup"><span data-stu-id="af028-145">For the near interaction at 0.45 m (45 cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="af028-146">這大約是 9-12 pt 和上面介紹的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="af028-146">It's about 9-12 pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="af028-147">![近距離與遠距離互動範圍的互動範圍 ](images/typography-distance-1000px.jpg)
 *內容*</span><span class="sxs-lookup"><span data-stu-id="af028-147">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="af028-148">最小清晰度的字型大小</span><span class="sxs-lookup"><span data-stu-id="af028-148">The minimum legible font size</span></span>

| <span data-ttu-id="af028-149">距離</span><span class="sxs-lookup"><span data-stu-id="af028-149">Distance</span></span> | <span data-ttu-id="af028-150">視角</span><span class="sxs-lookup"><span data-stu-id="af028-150">Viewing angle</span></span> | <span data-ttu-id="af028-151">文字高度</span><span class="sxs-lookup"><span data-stu-id="af028-151">Text height</span></span> | <span data-ttu-id="af028-152">字型大小</span><span class="sxs-lookup"><span data-stu-id="af028-152">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="af028-153">45 cm (直接操作距離) </span><span class="sxs-lookup"><span data-stu-id="af028-153">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="af028-154">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="af028-154">0.4°-0.5°</span></span> | <span data-ttu-id="af028-155">3.14 –3.9 分鐘</span><span class="sxs-lookup"><span data-stu-id="af028-155">3.14–3.9mm</span></span> | <span data-ttu-id="af028-156">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="af028-156">8.9–11.13pt</span></span> |
| <span data-ttu-id="af028-157">2分鐘</span><span class="sxs-lookup"><span data-stu-id="af028-157">2 m</span></span> | <span data-ttu-id="af028-158">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="af028-158">0.35°-0.4°</span></span> | <span data-ttu-id="af028-159">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="af028-159">12.21–13.97mm</span></span> | <span data-ttu-id="af028-160">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="af028-160">34.63-39.58 pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="af028-161">方便閱讀的字型大小</span><span class="sxs-lookup"><span data-stu-id="af028-161">The comfortably legible font size</span></span>

| <span data-ttu-id="af028-162">距離</span><span class="sxs-lookup"><span data-stu-id="af028-162">Distance</span></span> | <span data-ttu-id="af028-163">視角</span><span class="sxs-lookup"><span data-stu-id="af028-163">Viewing angle</span></span> | <span data-ttu-id="af028-164">文字高度</span><span class="sxs-lookup"><span data-stu-id="af028-164">Text height</span></span> | <span data-ttu-id="af028-165">字型大小</span><span class="sxs-lookup"><span data-stu-id="af028-165">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="af028-166">45 cm (直接操作距離) </span><span class="sxs-lookup"><span data-stu-id="af028-166">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="af028-167">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="af028-167">0.65°-0.8°</span></span> | <span data-ttu-id="af028-168">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="af028-168">5.1-6.3 mm</span></span> | <span data-ttu-id="af028-169">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="af028-169">14.47-17.8 pt</span></span> |
| <span data-ttu-id="af028-170">2分鐘</span><span class="sxs-lookup"><span data-stu-id="af028-170">2 m</span></span> | <span data-ttu-id="af028-171">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="af028-171">0.6°-0.75°</span></span> | <span data-ttu-id="af028-172">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="af028-172">20.9-26.2 mm</span></span> | <span data-ttu-id="af028-173">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="af028-173">59.4-74.2 pt</span></span> |

<span data-ttu-id="af028-174">Segoe UI (Windows) 的預設字型在大部分情況下都能順利運作。</span><span class="sxs-lookup"><span data-stu-id="af028-174">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="af028-175">不過，請避免使用較小的淺色或半淺色字型系列，因為精簡型垂直筆觸會震動，而且會降低可讀性。</span><span class="sxs-lookup"><span data-stu-id="af028-175">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="af028-176">具有足夠筆觸粗細的新式字型可正常運作。</span><span class="sxs-lookup"><span data-stu-id="af028-176">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="af028-177">例如，Helvetica 和 Arial 外觀美觀，而且在 HoloLens 中會使用一般或粗體權數來辨認。</span><span class="sxs-lookup"><span data-stu-id="af028-177">For example, Helvetica and Arial look gorgeous and are legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="af028-178">![視圖角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *觀賞距離、角度和文字高度*</span><span class="sxs-lookup"><span data-stu-id="af028-178">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="text-with-mixed-reality-toolkit-v2"></a><span data-ttu-id="af028-179">具有混合現實工具組 v2 的文字</span><span class="sxs-lookup"><span data-stu-id="af028-179">Text with Mixed Reality Toolkit v2</span></span>

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="af028-180">具有適當維度的清晰文字轉譯品質</span><span class="sxs-lookup"><span data-stu-id="af028-180">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="af028-181">根據這些調整因素，我們 [使用了 UI 文字和3D 文字網格來建立文字 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)。</span><span class="sxs-lookup"><span data-stu-id="af028-181">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="af028-182">開發人員可以使用這些 prefabs 來取得清晰的文字和一致的字型大小。</span><span class="sxs-lookup"><span data-stu-id="af028-182">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="af028-183">![具有適當維度的清晰文字轉譯品質](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="af028-183">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="af028-184">*具有適當維度的清晰文字轉譯品質*</span><span class="sxs-lookup"><span data-stu-id="af028-184">*Sharp text rendering quality with proper dimension*</span></span>

### <a name="shader-with-occlusion-support"></a><span data-ttu-id="af028-185">具有遮蔽支援的著色器</span><span class="sxs-lookup"><span data-stu-id="af028-185">Shader with occlusion support</span></span>

<span data-ttu-id="af028-186">Unity 的預設字型材質不支援遮蔽。</span><span class="sxs-lookup"><span data-stu-id="af028-186">Unity's default font material doesn't support occlusion.</span></span> <span data-ttu-id="af028-187">因此，根據預設，您會看到物件後面的文字。</span><span class="sxs-lookup"><span data-stu-id="af028-187">Because of this, you'll see the text behind the objects by default.</span></span> <span data-ttu-id="af028-188">我們已包含 [支援遮蔽的簡單著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader)。</span><span class="sxs-lookup"><span data-stu-id="af028-188">We've included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="af028-189">下圖顯示具有預設字型材質 (左) 的文字，以及具有適當遮蔽 (右邊) 的文字。</span><span class="sxs-lookup"><span data-stu-id="af028-189">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="af028-190">![具有遮蔽支援的著色器](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="af028-190">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="af028-191">*具有遮蔽支援的著色器*</span><span class="sxs-lookup"><span data-stu-id="af028-191">*Shader with occlusion support*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="af028-192">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="af028-192">Next Development Checkpoint</span></span>

<span data-ttu-id="af028-193">如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。</span><span class="sxs-lookup"><span data-stu-id="af028-193">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="af028-194">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="af028-194">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af028-195">語音輸入</span><span class="sxs-lookup"><span data-stu-id="af028-195">Voice input</span></span>](voice-input-in-unity.md)

<span data-ttu-id="af028-196">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="af028-196">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af028-197">共用體驗</span><span class="sxs-lookup"><span data-stu-id="af028-197">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="af028-198">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="af028-198">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="af028-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af028-199">See also</span></span>

* [<span data-ttu-id="af028-200">MRTK 中的文字預製專案</span><span class="sxs-lookup"><span data-stu-id="af028-200">Text Prefab in the MRTK</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="af028-201">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="af028-201">Typography</span></span>](../../design/typography.md)
