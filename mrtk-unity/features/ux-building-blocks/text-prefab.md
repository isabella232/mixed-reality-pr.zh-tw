---
title: 文字預製專案
description: MRTK 中的 TextPrefab 總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、TMP、
ms.openlocfilehash: 1839109043cfad9a20697c5d6526b349fd7ea2e4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175643"
---
# <a name="text-prefab"></a><span data-ttu-id="08ad8-104">文字預製專案</span><span class="sxs-lookup"><span data-stu-id="08ad8-104">Text prefab</span></span>

<span data-ttu-id="08ad8-105">這些 prefabs 已針對 Windows Mixed Reality 中的轉譯品質進行優化。</span><span class="sxs-lookup"><span data-stu-id="08ad8-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="08ad8-106">如需詳細資訊，請參閱 Microsoft Windows 開發人員中心上[Unity 中](/windows/mixed-reality/text-in-unity)的指導方針文字。</span><span class="sxs-lookup"><span data-stu-id="08ad8-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="08ad8-107">Prefabs</span><span class="sxs-lookup"><span data-stu-id="08ad8-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="08ad8-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="08ad8-108">3DTextPrefab</span></span>

<span data-ttu-id="08ad8-109">3D 文字網格預製專案 (資產/MRTK/SDK/StandardAssets/Prefabs/文字) ，並以雙計量距離的優化調整因數。</span><span class="sxs-lookup"><span data-stu-id="08ad8-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="08ad8-110"> (請閱讀下列指示) </span><span class="sxs-lookup"><span data-stu-id="08ad8-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="08ad8-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="08ad8-111">UITextPrefab</span></span>

<span data-ttu-id="08ad8-112">UI 文字網格預製專案 (資產/MRTK/SDK/StandardAssets/Prefabs/文字) ，其中具有在2個計量之間的優化調整係數。</span><span class="sxs-lookup"><span data-stu-id="08ad8-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="08ad8-113"> (請閱讀下列指示) </span><span class="sxs-lookup"><span data-stu-id="08ad8-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="08ad8-114">字型</span><span class="sxs-lookup"><span data-stu-id="08ad8-114">Fonts</span></span>

<span data-ttu-id="08ad8-115">開放原始碼字型 (資產/MRTK/核心/StandardAssets/字型) 包含在混合現實工具組中。</span><span class="sxs-lookup"><span data-stu-id="08ad8-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08ad8-116">文字預製專案使用開放原始碼字型 ' Selawik '。</span><span class="sxs-lookup"><span data-stu-id="08ad8-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="08ad8-117">若要使用具有不同字型的文字預製專案，請匯入字型檔案，然後遵循下列指示。</span><span class="sxs-lookup"><span data-stu-id="08ad8-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="08ad8-118">下列範例顯示如何使用 ' Segoe UI ' 字型搭配文字預製專案。</span><span class="sxs-lookup"><span data-stu-id="08ad8-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![匯入 Segoe UI 字型檔案](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="08ad8-120">指派字型材質給3DTextSegoeUI 材質。</span><span class="sxs-lookup"><span data-stu-id="08ad8-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![指派字型材質](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="08ad8-122">在 [3DTextSegoeUI] 材質上，選取著色器自訂/3DTextShader。</span><span class="sxs-lookup"><span data-stu-id="08ad8-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![指派著色器](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="08ad8-124">將 Segoe UI 字型和3DTextSegoeUI 材質指派給 prefabs 中的文字元件。</span><span class="sxs-lookup"><span data-stu-id="08ad8-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![指派字型檔案和材質](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="08ad8-126">使用 Unity 中的字型</span><span class="sxs-lookup"><span data-stu-id="08ad8-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="08ad8-127">當您將新的 3D TextMesh 新增至 Unity 中的場景時，有兩個視覺效果明顯的問題。</span><span class="sxs-lookup"><span data-stu-id="08ad8-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="08ad8-128">一個，字型出現很大，而兩個字型出現很模糊的外觀。</span><span class="sxs-lookup"><span data-stu-id="08ad8-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="08ad8-129">另外也請注意，在偵測器中，預設的字型大小值會設定為零。</span><span class="sxs-lookup"><span data-stu-id="08ad8-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="08ad8-130">將此零值取代為13，將不會顯示大小的差異，因為13實際上是預設值。</span><span class="sxs-lookup"><span data-stu-id="08ad8-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="08ad8-131">Unity 會假設新增至場景的所有新元素都是1個 Unity 單位，或100% 的轉換縮放比例，這會在 HoloLens 上轉譯為大約1個計量。</span><span class="sxs-lookup"><span data-stu-id="08ad8-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="08ad8-132">在字型的案例中，3D TextMesh 的周框方塊預設會出現在大約1個度量的高度。</span><span class="sxs-lookup"><span data-stu-id="08ad8-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="08ad8-133">字型比例和字型大小</span><span class="sxs-lookup"><span data-stu-id="08ad8-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="08ad8-134">大部分的視覺化設計工具會使用點來定義真實世界中的字型大小，以及其設計程式。</span><span class="sxs-lookup"><span data-stu-id="08ad8-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="08ad8-135">1計量中有大約 2835 (2，834.645666399962) 點。</span><span class="sxs-lookup"><span data-stu-id="08ad8-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="08ad8-136">根據指向1計量的點系統轉換，以及 Unity 的預設 TextMesh 字型大小13，13的簡單數學運算（13）除以2835等於 0.0046 (0.004586111116 是精確的) 提供良好的標準尺規來開始使用，但有些可能想要舍入至0.005。</span><span class="sxs-lookup"><span data-stu-id="08ad8-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="08ad8-137">無論何種方式，將文字物件或容器調整為這些值，不僅可讓您從設計程式轉換成1:1 的字型大小，也提供標準來維持整個應用程式或遊戲的一致性。</span><span class="sxs-lookup"><span data-stu-id="08ad8-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="08ad8-138">UI 文字</span><span class="sxs-lookup"><span data-stu-id="08ad8-138">UI Text</span></span>

<span data-ttu-id="08ad8-139">將 UI 或畫布型文字元素新增至場景時，大小差異仍會大於。</span><span class="sxs-lookup"><span data-stu-id="08ad8-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="08ad8-140">這兩種大小的差異大約是1000%，這會將以 UI 為基礎之文字元件的縮放比例帶到 0.00046 (0.0004586111116 為舍入值的精確) 或0.0005。</span><span class="sxs-lookup"><span data-stu-id="08ad8-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="08ad8-141">**免責聲明**：任何字型的預設值可能會受到該字型的材質大小或字型匯入 Unity 的影響。</span><span class="sxs-lookup"><span data-stu-id="08ad8-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="08ad8-142">這些測試是根據 Unity 中的預設 Arial 字型，還有另一個匯入的字型來執行。</span><span class="sxs-lookup"><span data-stu-id="08ad8-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![具有縮放比例的字型大小](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="08ad8-144">Text3DSelawik</span><span class="sxs-lookup"><span data-stu-id="08ad8-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="08ad8-145">具有遮蔽支援的3DTextPrefab 教材。</span><span class="sxs-lookup"><span data-stu-id="08ad8-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="08ad8-146">需要3DTextShader</span><span class="sxs-lookup"><span data-stu-id="08ad8-146">Requires 3DTextShader.shader</span></span>

![預設字型材質與3DTextSegoeUI 材質](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="08ad8-148">Text3DShader 著色器</span><span class="sxs-lookup"><span data-stu-id="08ad8-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="08ad8-149">具有遮蔽支援之3DTextPrefab 的著色器。</span><span class="sxs-lookup"><span data-stu-id="08ad8-149">Shader for 3DTextPrefab with occlusion support.</span></span>
