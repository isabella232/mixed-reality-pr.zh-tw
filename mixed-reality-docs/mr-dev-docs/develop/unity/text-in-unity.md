---
title: Unity 中的文字
description: 若要在 Unity 中顯示文字，您可以使用兩種類型的文字元件： UI 文字和3D 文字網格。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、控制項、字型、印刷樣式、ui、ux、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: 04b62cd0989042856dbd15d467d042f67df69931
ms.sourcegitcommit: 5d6dbbb94e60cf10786d0fbbaf4239a1541e9e29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95008131"
---
# <a name="text-in-unity"></a><span data-ttu-id="21ec7-104">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="21ec7-104">Text in Unity</span></span>

<span data-ttu-id="21ec7-105">文字是全像攝影應用程式中最重要的元件之一。</span><span class="sxs-lookup"><span data-stu-id="21ec7-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="21ec7-106">若要在 Unity 中顯示文字，有三種類型的文字元件可供您使用： UI 文字、3D 文字網格和文字網格 Pro。</span><span class="sxs-lookup"><span data-stu-id="21ec7-106">To display text in Unity, there are three types of text components you can use — UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="21ec7-107">根據預設，UI 文字和3D 文字網格會顯示為模糊且太大。</span><span class="sxs-lookup"><span data-stu-id="21ec7-107">By default, UI Text and 3D Text Mesh appear blurry and are too big.</span></span> <span data-ttu-id="21ec7-108">您必須調整幾個變數，以取得在 HoloLens 中具有可管理大小的清晰高品質文字。</span><span class="sxs-lookup"><span data-stu-id="21ec7-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="21ec7-109">藉由套用調整因數以在使用 UI 文字和3D 文字網格元件時取得適當的維度，您可以達到更佳的轉譯品質。</span><span class="sxs-lookup"><span data-stu-id="21ec7-109">By applying a scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="21ec7-110">![如何取得清晰且美觀的文字](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="21ec7-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="21ec7-111">*Unity 中的模糊預設文字*</span><span class="sxs-lookup"><span data-stu-id="21ec7-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a><span data-ttu-id="21ec7-112">使用 Unity 的3D 文字 (文字網格) 和 UI 文字</span><span class="sxs-lookup"><span data-stu-id="21ec7-112">Working with Unity's 3D Text (Text Mesh) and UI Text</span></span>

<span data-ttu-id="21ec7-113">Unity 假設所有新增至場景的新元素都是大小為1個 Unity 單位，或100% 的轉換縮放比例，這會在 HoloLens 上轉譯為約1個計量。</span><span class="sxs-lookup"><span data-stu-id="21ec7-113">Unity assumes that all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="21ec7-114">在字型的案例中，3D TextMesh 的周框方塊預設會以大約1計量的高度來提供。</span><span class="sxs-lookup"><span data-stu-id="21ec7-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="21ec7-115">![使用 Unity 中的字型](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="21ec7-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="21ec7-116">*預設的 Unity 3D 文字 (文字網格) 佔用1個 Unity 單位，也就是1個計量*</span><span class="sxs-lookup"><span data-stu-id="21ec7-116">*Default Unity 3D Text (Text Mesh) occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="21ec7-117">大部分的視覺化設計工具會使用點來定義真實世界中的字型大小。</span><span class="sxs-lookup"><span data-stu-id="21ec7-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="21ec7-118">1計量中有大約 2835 (2，834.645666399962) 點。</span><span class="sxs-lookup"><span data-stu-id="21ec7-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="21ec7-119">根據指向1計量的點系統轉換，以及 Unity 的預設文字網格字型大小13，13的簡單數學運算（13）除以2835等於 0.0046 (0.004586111116 為精確) ，可提供良好的標準尺規來開始 (有些可能想要舍入至 0.005) 。</span><span class="sxs-lookup"><span data-stu-id="21ec7-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) which provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="21ec7-120">將文字物件或容器調整為這些值並不只允許在設計程式中轉換字型大小的1:1，也提供標準，因此您可以在整個體驗中維持一致性。</span><span class="sxs-lookup"><span data-stu-id="21ec7-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="21ec7-121">![調整 Unity 3D 文字和 UI 文字的值](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="21ec7-121">![Scaling values for the Unity 3D Text and UI Text](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="21ec7-122">*調整 Unity 3D 文字和 UI 文字的值*</span><span class="sxs-lookup"><span data-stu-id="21ec7-122">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<br>

<span data-ttu-id="21ec7-123">![具有優化值的 Unity 3D 文字網格](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="21ec7-123">![Unity 3D Text Mesh with optimized values](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="21ec7-124">*具有優化值的 Unity 3D 文字網格*</span><span class="sxs-lookup"><span data-stu-id="21ec7-124">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="21ec7-125">將 UI 或畫布型文字元素新增至場景時，大小差異仍會大於。</span><span class="sxs-lookup"><span data-stu-id="21ec7-125">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="21ec7-126">這兩種大小的差異大約是1000%，這會將以 UI 為基礎之文字元件的縮放比例帶到 0.00046 (0.0004586111116 為舍入值的精確) 或0.0005。</span><span class="sxs-lookup"><span data-stu-id="21ec7-126">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="21ec7-127">![具有優化值的 Unity UI 文字](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="21ec7-127">![Unity UI Text with optimized values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="21ec7-128">*具有優化值的 Unity UI 文字*</span><span class="sxs-lookup"><span data-stu-id="21ec7-128">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="21ec7-129">任何字型的預設值可能會受到該字型的材質大小或字型匯入 Unity 的影響。</span><span class="sxs-lookup"><span data-stu-id="21ec7-129">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="21ec7-130">這些測試是根據 Unity 中的預設 Arial 字型，還有另一個匯入的字型來執行。</span><span class="sxs-lookup"><span data-stu-id="21ec7-130">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="21ec7-131">使用文字網格 Pro</span><span class="sxs-lookup"><span data-stu-id="21ec7-131">Working with Text Mesh Pro</span></span>

<span data-ttu-id="21ec7-132">您可以使用 Unity 的文字網格 Pro 來保護文字轉譯品質。</span><span class="sxs-lookup"><span data-stu-id="21ec7-132">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="21ec7-133">無論使用 [ [帶正負號的距離] 欄位 (.sdf) ](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 技術的距離為何，它都支援清晰的文字外框。</span><span class="sxs-lookup"><span data-stu-id="21ec7-133">It supports crisp text outlines regardless of the distance using the [Signed Distance Field (SDF)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="21ec7-134">使用我們針對3D 文字網格和 UI 文字所使用的相同計算方法，我們可以找到適當的縮放比例值，以搭配傳統的印刷點使用。</span><span class="sxs-lookup"><span data-stu-id="21ec7-134">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find the proper scaling values to use with conventional typographic points.</span></span> <span data-ttu-id="21ec7-135">因為大小為36的預設3D 文字網格 Pro 字型，其周框大小為 2.5 Unity 單位 (2.5 m) ，所以我們可以使用調整值0.005 來取得點大小。</span><span class="sxs-lookup"><span data-stu-id="21ec7-135">Since the default 3D Text Mesh Pro font with the size of 36 has a bounding size of 2.5 Unity units (2.5m), we can use a scaling value of 0.005 to get the point size.</span></span> <span data-ttu-id="21ec7-136">UI 功能表下的文字網格專業人員預設的周框大小為25個 Unity 單位， (25m) 。</span><span class="sxs-lookup"><span data-stu-id="21ec7-136">The Text Mesh Pro under the UI menu has a default bounding size of 25 Unity units (25m).</span></span> <span data-ttu-id="21ec7-137">這可為我們提供0.0005 的調整值。</span><span class="sxs-lookup"><span data-stu-id="21ec7-137">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="21ec7-138">![調整 Unity 3D 文字和 UI 的值](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="21ec7-138">![Scaling values for the Unity 3D Text and UI](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="21ec7-139">*調整 Unity 3D 文字和 UI 的值*</span><span class="sxs-lookup"><span data-stu-id="21ec7-139">*Scaling values for the Unity 3D Text and UI*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="21ec7-140">建議的文字大小</span><span class="sxs-lookup"><span data-stu-id="21ec7-140">Recommended text size</span></span>
<span data-ttu-id="21ec7-141">如您所見，我們在電腦或平板電腦裝置上使用的類型大小， (通常介於12–32pt 填補) 在2個計量之間的距離相當小。</span><span class="sxs-lookup"><span data-stu-id="21ec7-141">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="21ec7-142">這取決於每個字型的特性，但在一般情況下，建議的最小觀賞角度和字型高度都是以我們的使用者研究研究為基礎，0.35 °0.4 °/12.21-13.97mm。</span><span class="sxs-lookup"><span data-stu-id="21ec7-142">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="21ec7-143">這與上述的縮放比例有大約35個40pt。</span><span class="sxs-lookup"><span data-stu-id="21ec7-143">It is about 35-40pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="21ec7-144">針對 0.45 m 的近乎互動 (45cm) ，最小的可辨認字型的觀賞角度和高度為0.4 °-0.5 °/3.14 – 3.9 mm。</span><span class="sxs-lookup"><span data-stu-id="21ec7-144">For the near interaction at 0.45m (45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="21ec7-145">這與上述的調整因數大約是 9 12pt。</span><span class="sxs-lookup"><span data-stu-id="21ec7-145">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="21ec7-146">![近距離與遠距離互動範圍的互動範圍 ](images/typography-distance-1000px.jpg)
 *內容*</span><span class="sxs-lookup"><span data-stu-id="21ec7-146">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="21ec7-147">最小清晰度的字型大小</span><span class="sxs-lookup"><span data-stu-id="21ec7-147">The minimum legible font size</span></span>
| <span data-ttu-id="21ec7-148">距離</span><span class="sxs-lookup"><span data-stu-id="21ec7-148">Distance</span></span> | <span data-ttu-id="21ec7-149">視角</span><span class="sxs-lookup"><span data-stu-id="21ec7-149">Viewing angle</span></span> | <span data-ttu-id="21ec7-150">文字高度</span><span class="sxs-lookup"><span data-stu-id="21ec7-150">Text height</span></span> | <span data-ttu-id="21ec7-151">字型大小</span><span class="sxs-lookup"><span data-stu-id="21ec7-151">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="21ec7-152">45cm (直接操作距離) </span><span class="sxs-lookup"><span data-stu-id="21ec7-152">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="21ec7-153">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="21ec7-153">0.4°-0.5°</span></span> | <span data-ttu-id="21ec7-154">3.14 –3.9 分鐘</span><span class="sxs-lookup"><span data-stu-id="21ec7-154">3.14–3.9mm</span></span> | <span data-ttu-id="21ec7-155">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="21ec7-155">8.9–11.13pt</span></span> |
| <span data-ttu-id="21ec7-156">2m</span><span class="sxs-lookup"><span data-stu-id="21ec7-156">2m</span></span> | <span data-ttu-id="21ec7-157">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="21ec7-157">0.35°-0.4°</span></span> | <span data-ttu-id="21ec7-158">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="21ec7-158">12.21–13.97mm</span></span> | <span data-ttu-id="21ec7-159">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="21ec7-159">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="21ec7-160">方便閱讀的字型大小</span><span class="sxs-lookup"><span data-stu-id="21ec7-160">The comfortably legible font size</span></span>
| <span data-ttu-id="21ec7-161">距離</span><span class="sxs-lookup"><span data-stu-id="21ec7-161">Distance</span></span> | <span data-ttu-id="21ec7-162">視角</span><span class="sxs-lookup"><span data-stu-id="21ec7-162">Viewing angle</span></span> | <span data-ttu-id="21ec7-163">文字高度</span><span class="sxs-lookup"><span data-stu-id="21ec7-163">Text height</span></span> | <span data-ttu-id="21ec7-164">字型大小</span><span class="sxs-lookup"><span data-stu-id="21ec7-164">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="21ec7-165">45cm (直接操作距離) </span><span class="sxs-lookup"><span data-stu-id="21ec7-165">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="21ec7-166">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="21ec7-166">0.65°-0.8°</span></span> | <span data-ttu-id="21ec7-167">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="21ec7-167">5.1-6.3mm</span></span> | <span data-ttu-id="21ec7-168">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="21ec7-168">14.47-17.8pt</span></span> |
| <span data-ttu-id="21ec7-169">2m</span><span class="sxs-lookup"><span data-stu-id="21ec7-169">2m</span></span> | <span data-ttu-id="21ec7-170">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="21ec7-170">0.6°-0.75°</span></span> | <span data-ttu-id="21ec7-171">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="21ec7-171">20.9-26.2mm</span></span> | <span data-ttu-id="21ec7-172">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="21ec7-172">59.4-74.2pt</span></span> |

<span data-ttu-id="21ec7-173">Segoe UI (Windows) 的預設字型在大部分情況下都能順利運作。</span><span class="sxs-lookup"><span data-stu-id="21ec7-173">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="21ec7-174">不過，請避免使用較小的淺色或半淺色字型系列，因為精簡型垂直筆觸會震動，而且會降低可讀性。</span><span class="sxs-lookup"><span data-stu-id="21ec7-174">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="21ec7-175">具有足夠筆觸粗細的新式字型可正常運作。</span><span class="sxs-lookup"><span data-stu-id="21ec7-175">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="21ec7-176">例如，Helvetica 和 Arial 外觀美觀，而且在 HoloLens 中會有一般或粗體權數的可讀性。</span><span class="sxs-lookup"><span data-stu-id="21ec7-176">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="21ec7-177">![視圖角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *觀賞距離、角度和文字高度*</span><span class="sxs-lookup"><span data-stu-id="21ec7-177">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="text-with-mixed-reality-toolkit-v2"></a><span data-ttu-id="21ec7-178">具有混合現實工具組 v2 的文字</span><span class="sxs-lookup"><span data-stu-id="21ec7-178">Text with Mixed Reality Toolkit v2</span></span>

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="21ec7-179">具有適當維度的清晰文字轉譯品質</span><span class="sxs-lookup"><span data-stu-id="21ec7-179">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="21ec7-180">根據這些調整因素，我們 [使用了 UI 文字和3D 文字網格來建立文字 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)。</span><span class="sxs-lookup"><span data-stu-id="21ec7-180">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="21ec7-181">開發人員可以使用這些 prefabs 來取得清晰的文字和一致的字型大小。</span><span class="sxs-lookup"><span data-stu-id="21ec7-181">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="21ec7-182">![具有適當維度的清晰文字轉譯品質](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="21ec7-182">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="21ec7-183">*具有適當維度的清晰文字轉譯品質*</span><span class="sxs-lookup"><span data-stu-id="21ec7-183">*Sharp text rendering quality with proper dimension*</span></span>

### <a name="shader-with-occlusion-support"></a><span data-ttu-id="21ec7-184">具有遮蔽支援的著色器</span><span class="sxs-lookup"><span data-stu-id="21ec7-184">Shader with occlusion support</span></span>

<span data-ttu-id="21ec7-185">Unity 的預設字型材質不支援遮蔽。</span><span class="sxs-lookup"><span data-stu-id="21ec7-185">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="21ec7-186">因此，依預設，您會看到物件後面的文字。</span><span class="sxs-lookup"><span data-stu-id="21ec7-186">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="21ec7-187">我們已包含 [支援遮蔽的簡單著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader)。</span><span class="sxs-lookup"><span data-stu-id="21ec7-187">We have included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="21ec7-188">下圖顯示具有預設字型材質 (左) 的文字，以及具有適當遮蔽 (右邊) 的文字。</span><span class="sxs-lookup"><span data-stu-id="21ec7-188">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="21ec7-189">![具有遮蔽支援的著色器](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="21ec7-189">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="21ec7-190">*具有遮蔽支援的著色器*</span><span class="sxs-lookup"><span data-stu-id="21ec7-190">*Shader with occlusion support*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="21ec7-191">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="21ec7-191">Next Development Checkpoint</span></span>

<span data-ttu-id="21ec7-192">依循我們配置的 Unity 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="21ec7-192">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="21ec7-193">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="21ec7-193">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="21ec7-194">語音輸入</span><span class="sxs-lookup"><span data-stu-id="21ec7-194">Voice input</span></span>](voice-input-in-unity.md)

<span data-ttu-id="21ec7-195">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="21ec7-195">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="21ec7-196">共用體驗</span><span class="sxs-lookup"><span data-stu-id="21ec7-196">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="21ec7-197">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="21ec7-197">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="21ec7-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21ec7-198">See also</span></span>
* [<span data-ttu-id="21ec7-199">MRTK 中的文字預製專案</span><span class="sxs-lookup"><span data-stu-id="21ec7-199">Text Prefab in the MRTK</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="21ec7-200">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="21ec7-200">Typography</span></span>](../../design/typography.md)
