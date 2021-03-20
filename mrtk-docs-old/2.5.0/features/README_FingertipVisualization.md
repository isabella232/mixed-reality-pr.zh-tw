---
title: README_FingertipVisualization
description: MRTK 中的 FingerTip 視覺效果總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Fingertip
ms.openlocfilehash: a1217cd765632d71153e8c094dd7abe61af607c8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695125"
---
# <a name="fingertip-visualization"></a><span data-ttu-id="8d626-104">Fingertip 視覺效果</span><span class="sxs-lookup"><span data-stu-id="8d626-104">Fingertip visualization</span></span>

![Fingertip 視覺效果](Images/Fingertip/MRTK_FingertipVisualization_Main.png)

<span data-ttu-id="8d626-106">Fingertip affordance 可協助使用者辨識來自目標物件的距離。</span><span class="sxs-lookup"><span data-stu-id="8d626-106">The fingertip affordance helps the user recognize the distance from the target object.</span></span> <span data-ttu-id="8d626-107">「環形」圖形視覺效果會根據從 fingertip 到物件的距離來調整其大小。</span><span class="sxs-lookup"><span data-stu-id="8d626-107">The ring shape visual adjusts its size based on the distance from the fingertip to the object.</span></span> <span data-ttu-id="8d626-108">Fingertip 視覺效果主要是由 (的 `FingerCursor` 資產/MRTK/SDK/Features/UX/Prefabs/cursor/FingerCursor. 預製專案)  (和腳本) 所控制，這會以 *預製專案* 的資料指標 PokePointer 來產生。</span><span class="sxs-lookup"><span data-stu-id="8d626-108">The fingertip visualization is primarily controlled by the `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab) (and script) which is spawned as the cursor prefab of the *PokePointer*.</span></span> <span data-ttu-id="8d626-109">視覺效果的其他元件包括 *ProximityLight* 腳本和 *MixedRealityStandard* 著色器。</span><span class="sxs-lookup"><span data-stu-id="8d626-109">Other components of the visualization include the *ProximityLight* script, and *MixedRealityStandard* shader.</span></span>

## <a name="how-to-use-the-fingertip-visualization"></a><span data-ttu-id="8d626-110">如何使用 fingertip 視覺效果</span><span class="sxs-lookup"><span data-stu-id="8d626-110">How to use the fingertip visualization</span></span>

<span data-ttu-id="8d626-111">根據預設，fingertip 視覺效果會在設定為產生 FingerCursor 的任何 Unity 場景中運作。</span><span class="sxs-lookup"><span data-stu-id="8d626-111">By default the fingertip visualization will work in any Unity scene that is configured to spawn a FingerCursor.</span></span> <span data-ttu-id="8d626-112">FingerCursor 的產生會出現在 *DefaultMixedRealityToolkitConfigurationProfile* 底下：</span><span class="sxs-lookup"><span data-stu-id="8d626-112">Spawning of the FingerCursor occurs in the *DefaultMixedRealityToolkitConfigurationProfile* under:</span></span>

<span data-ttu-id="8d626-113">*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*</span><span class="sxs-lookup"><span data-stu-id="8d626-113">*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*</span></span>

<span data-ttu-id="8d626-114">概括而言，fingertip 視覺效果的運作方式是使用相近光線，在接受鄰近燈的任何鄰近表面上投影彩色漸層。</span><span class="sxs-lookup"><span data-stu-id="8d626-114">At a high level the fingertip visualization works by using a proximity light to project a colored gradient on any nearby surfaces that accept proximity lights.</span></span> <span data-ttu-id="8d626-115">手指游標接著會尋找任何附近的互動介面（由父系決定 `IMixedRealityNearPointer(s)` ），以在手指移至表面時對齊手指環形。</span><span class="sxs-lookup"><span data-stu-id="8d626-115">The finger cursor then looks for any nearby interactable surfaces, which are determined by parent `IMixedRealityNearPointer(s)`, to align the finger ring with a surface as the finger moves towards a surface.</span></span> <span data-ttu-id="8d626-116">手指的方法是使用 MixedRealityStandard 著色器的圓角屬性，動態地將手指環形動畫。</span><span class="sxs-lookup"><span data-stu-id="8d626-116">As a finger approaches a surface the finger ring is also dynamically animated using the round corner properties of the MixedRealityStandard shader.</span></span>

## <a name="example-scene"></a><span data-ttu-id="8d626-117">範例場景</span><span class="sxs-lookup"><span data-stu-id="8d626-117">Example scene</span></span>

<span data-ttu-id="8d626-118">您可以在幾乎任何適用于已表達手的場景中找到 fingertip 的視覺效果範例，但在 [HandInteractionExample 場景](README_HandInteractionExamples.md)中很明顯。</span><span class="sxs-lookup"><span data-stu-id="8d626-118">You can find fingertip visualization examples in almost any scene that works with articulated hands, but is prominent in the [HandInteractionExample scene](README_HandInteractionExamples.md).</span></span>

![Fingertip 視覺效果狀態](Images/Fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a><span data-ttu-id="8d626-120">偵測器屬性</span><span class="sxs-lookup"><span data-stu-id="8d626-120">Inspector properties</span></span>

<span data-ttu-id="8d626-121">**FingerCursor** 許多手指指標屬性都是繼承自基底資料指標類別。</span><span class="sxs-lookup"><span data-stu-id="8d626-121">**FingerCursor** Many of the finger cursor properties are inherited from the base cursor class.</span></span> <span data-ttu-id="8d626-122">重要屬性包括在 MixedRealityStandard 著色器中驅動手指環形動畫的最遠/接近面邊界和寬度。</span><span class="sxs-lookup"><span data-stu-id="8d626-122">Important properties include the far / near surface margins and widths which drive the finger ring animation in the MixedRealityStandard shader.</span></span> <span data-ttu-id="8d626-123">針對其他屬性，請將滑鼠停留在偵測器工具提示上。</span><span class="sxs-lookup"><span data-stu-id="8d626-123">For other properties please hover over the inspector tool tips.</span></span>

<img src="Images/Fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Finger Cursor">

<span data-ttu-id="8d626-124">**ProximityLight** 近亮光源設定會控制在表面接近或遠的光線外觀。</span><span class="sxs-lookup"><span data-stu-id="8d626-124">**ProximityLight** The proximity light settings control how the light looks when near and far from a surface.</span></span> <span data-ttu-id="8d626-125">中央、中間和外部色彩會控制光線的漸層外觀，並且可以針對應用程式的色彩選擇區量身打造。</span><span class="sxs-lookup"><span data-stu-id="8d626-125">The center, middle, and outer colors control the gradient look of the light and can be custom tailored for the color palette of your application.</span></span> <span data-ttu-id="8d626-126">請注意，色彩為 HDR (高動態範圍) 可讓使用者將接近的光線調至上方的值。</span><span class="sxs-lookup"><span data-stu-id="8d626-126">Note, the colors are HDR (High Dynamic Range) to allow users to brighten the proximity light to values above one.</span></span> <span data-ttu-id="8d626-127">針對其他屬性，請將滑鼠停留在偵測器工具提示上。</span><span class="sxs-lookup"><span data-stu-id="8d626-127">For other properties please hover over the inspector tool tips.</span></span>

<span data-ttu-id="8d626-128">**MixedRealityStandard 著色器** MixedRealityStandard 著色器用於 MRTK 中的許多效果。</span><span class="sxs-lookup"><span data-stu-id="8d626-128">**MixedRealityStandard Shader** The MixedRealityStandard shader is used for many effects in the MRTK.</span></span> <span data-ttu-id="8d626-129">Fingertip 視覺效果的兩項設定是「近乎淡化」和「近亮」。</span><span class="sxs-lookup"><span data-stu-id="8d626-129">The two settings important for fingertip visualization are "Near Fade" and "Proximity Light."</span></span> <span data-ttu-id="8d626-130">近乎淡化可讓物件在相機或光線接近時淡入/放大。</span><span class="sxs-lookup"><span data-stu-id="8d626-130">Near Fade allows objects to fade in / out as a camera or light nears them.</span></span> <span data-ttu-id="8d626-131">請務必核取 [淺色]，以允許鄰近燈來推動淡化 (而不是相機) 。</span><span class="sxs-lookup"><span data-stu-id="8d626-131">Make sure to check "Light" to allow proximity lights to drive the fade (rather than the camera).</span></span> <span data-ttu-id="8d626-132">您可以反轉「淡化開始」和「淡化完成」的值，以反轉淡出的值。</span><span class="sxs-lookup"><span data-stu-id="8d626-132">You can reverse the values of "Fade Begin" and "Fade Complete" to reverse a fade.</span></span> <span data-ttu-id="8d626-133">針對您想要讓鄰近光線亮亮的任何表面，請檢查「近亮」。</span><span class="sxs-lookup"><span data-stu-id="8d626-133">Check "Proximity Light" for any surface you would like the proximity light to brighten.</span></span> <span data-ttu-id="8d626-134">針對其他屬性，請將滑鼠停留在偵測器工具提示上。</span><span class="sxs-lookup"><span data-stu-id="8d626-134">For other properties please hover over the inspector tool tips.</span></span>

<img src="Images/Fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Mixed Reality Standerd Shader">
