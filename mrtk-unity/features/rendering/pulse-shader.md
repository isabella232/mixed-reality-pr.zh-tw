---
title: 脈衝著色器
description: MRTK 中的脈衝著色器描述。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 0b26242d71bbe080e440f9c52a009e29000ab00b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224206"
---
# <a name="pulse-shader"></a><span data-ttu-id="c70c5-104">脈衝著色器</span><span class="sxs-lookup"><span data-stu-id="c70c5-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="c70c5-106">您可以使用脈衝著色器，以動畫顯示視覺脈衝效果，而不是表面重建、明確表述的手網格或任何其他網格。</span><span class="sxs-lookup"><span data-stu-id="c70c5-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="c70c5-107">著色器和材質</span><span class="sxs-lookup"><span data-stu-id="c70c5-107">Shader and material</span></span>

<span data-ttu-id="c70c5-108">下列材質使用 **SR_Triangles** 著色器。</span><span class="sxs-lookup"><span data-stu-id="c70c5-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="c70c5-109">您可以設定各種選項，例如 [填滿色彩]、[線條色彩] 和 [脈衝色彩]。</span><span class="sxs-lookup"><span data-stu-id="c70c5-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="c70c5-110">**MRTK_Pulse_SpatialMeshBlue 的材料**</span><span class="sxs-lookup"><span data-stu-id="c70c5-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="c70c5-111">**MRTK_Pulse_SpatialMeshPurple 的材料**</span><span class="sxs-lookup"><span data-stu-id="c70c5-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="c70c5-112">**MRTK_Pulse_ArticulatedHandMeshBlue 的材料**</span><span class="sxs-lookup"><span data-stu-id="c70c5-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="c70c5-113">**MRTK_Pulse_ArticulatedHandMeshPurple 的材料**</span><span class="sxs-lookup"><span data-stu-id="c70c5-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="c70c5-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="c70c5-114">Prerequisites</span></span>

<span data-ttu-id="c70c5-115">針對空間網格範例，請確定已在 MixedRealityToolkit 物件 > 空間感知設定檔-> 顯示設定可見的材質上，指派 MRTK_Pulse_SpatialMeshBlue 的材質或 MRTK_Pulse_SpatialMeshPurple。</span><span class="sxs-lookup"><span data-stu-id="c70c5-115">For the spatial mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned under MixedRealityToolkit object -> Spatial Awareness Profile -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="c70c5-116">若為手寫範例，請確定已在 ArticulatedHandMesh 中指派 MRTK_Pulse_ArticulatedHandMeshBlue 的 MRTK_Pulse_ArticulatedHandMeshPurple。預製專案，其本身應指派于 MRTK 設定-> 輸入 > 手動追蹤-> 的手型網格預製專案。</span><span class="sxs-lookup"><span data-stu-id="c70c5-116">For the hand mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="c70c5-117">運作方式</span><span class="sxs-lookup"><span data-stu-id="c70c5-117">How it works</span></span>

<span data-ttu-id="c70c5-118">手上網格著色器會使用 UVs 來對應沿著手網格的脈衝，以及淡出手腕。</span><span class="sxs-lookup"><span data-stu-id="c70c5-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="c70c5-119">表面重建著色器會使用頂點位置來對應脈衝。</span><span class="sxs-lookup"><span data-stu-id="c70c5-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="c70c5-120">空間網格範例-PulseShaderSpatialMeshExample unity</span><span class="sxs-lookup"><span data-stu-id="c70c5-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="c70c5-121">類似于 HoloLens 2 的 shell 體驗，您可以用光點來點一下，以產生空間網格的閃爍效果。</span><span class="sxs-lookup"><span data-stu-id="c70c5-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="c70c5-122">範例場景包含 ExampleSpatialMesh 物件，此物件是 Unity 遊戲模式的測試空間網格資料。</span><span class="sxs-lookup"><span data-stu-id="c70c5-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="c70c5-123">此物件將會在裝置上停用並隱藏。</span><span class="sxs-lookup"><span data-stu-id="c70c5-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="c70c5-124">若為 true，則 **PulseShaderSpatialMeshHandler** 會在叫用點位置的空間網格上產生脈衝效果 `PulseOnSelect` 。</span><span class="sxs-lookup"><span data-stu-id="c70c5-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="c70c5-125">在  `Auto Pulse` 重複動畫的材質本身中，屬性也可以設定為 true。</span><span class="sxs-lookup"><span data-stu-id="c70c5-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="c70c5-126">在範例場景中，此腳本會附加至 PulseShaderSpatialMeshParent 預製專案。</span><span class="sxs-lookup"><span data-stu-id="c70c5-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="c70c5-127">空間感知設定檔會透過執行時間空間網格預製專案屬性來參考這個預製專案。</span><span class="sxs-lookup"><span data-stu-id="c70c5-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="c70c5-128">在執行時間期間，PulseShaderSpatialMeshParent 預製專案和會具現化，並新增至空間網狀階層 (只有在裝置上，在編輯器) 中無法觀察到此行為。</span><span class="sxs-lookup"><span data-stu-id="c70c5-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="c70c5-129">手形網格範例-PulseShaderHandMeshExample unity</span><span class="sxs-lookup"><span data-stu-id="c70c5-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="c70c5-130">這個範例場景示範使用脈衝著色器的手網格視覺效果。</span><span class="sxs-lookup"><span data-stu-id="c70c5-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="c70c5-131">當 HoloLens 裝置偵測到手時，會觸發脈衝動畫一次。</span><span class="sxs-lookup"><span data-stu-id="c70c5-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="c70c5-132">這種視覺效果的意見反應可以提高使用者的互動信賴度。</span><span class="sxs-lookup"><span data-stu-id="c70c5-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="c70c5-133">**PulseShaderHandMeshHandler .cs** 腳本會針對指派的材質產生脈衝效果。</span><span class="sxs-lookup"><span data-stu-id="c70c5-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="c70c5-134">預設會核取 [手動偵測到的脈衝]。</span><span class="sxs-lookup"><span data-stu-id="c70c5-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
