---
title: PulseShader
description: MRTK 中的脈衝著色器描述。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 3ee6c80f647569305b9dadbf81262156c3faf008
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779838"
---
# <a name="pulse-shader"></a><span data-ttu-id="ca42f-104">脈衝著色器</span><span class="sxs-lookup"><span data-stu-id="ca42f-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="ca42f-106">![MRTK_HandMesh_Pulse2 ](https://user-images.githubusercontent.com/13754172/68262035-e4f7e600-fff6-11e9-9858-796afd1cabc5.gif) 使用脈衝著色器，在表面重建、明確展示的手網格或任何其他網格上建立視覺脈衝效果的動畫。</span><span class="sxs-lookup"><span data-stu-id="ca42f-106">![MRTK_HandMesh_Pulse2](https://user-images.githubusercontent.com/13754172/68262035-e4f7e600-fff6-11e9-9858-796afd1cabc5.gif) Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="ca42f-107">著色器和材質</span><span class="sxs-lookup"><span data-stu-id="ca42f-107">Shader and material</span></span>

<span data-ttu-id="ca42f-108">**MRTK_SurfaceReconstruction 的材料** 和 **MRTK_ArticulatedHandMeshPulse** 會使用 **SR_Triangles** 著色器。</span><span class="sxs-lookup"><span data-stu-id="ca42f-108">**MRTK_SurfaceReconstruction.mat** and **MRTK_ArticulatedHandMeshPulse.mat** uses **SR_Triangles** shader.</span></span> <span data-ttu-id="ca42f-109">您可以設定各種選項，例如 [填滿色彩]、[線條色彩] 和 [脈衝色彩]。</span><span class="sxs-lookup"><span data-stu-id="ca42f-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

## <a name="example-scene"></a><span data-ttu-id="ca42f-110">範例場景</span><span class="sxs-lookup"><span data-stu-id="ca42f-110">Example scene</span></span>

<span data-ttu-id="ca42f-111">開啟 **PulseShaderExamples unity** 場景，並觀察球、表面重建和已說出之手形網格的影響。</span><span class="sxs-lookup"><span data-stu-id="ca42f-111">Open **PulseShaderExamples.unity** scene, and observe the pulsing effect on the spheres, surface reconstruction, and the articulated hand mesh.</span></span>

<span data-ttu-id="ca42f-112">使用 SurfacePulse.cs 腳本，以動畫顯示指派之材質的脈衝效果，或在材質本身開啟「自動脈衝」。</span><span class="sxs-lookup"><span data-stu-id="ca42f-112">Use the SurfacePulse.cs script to animate the pulse effect on the assigned material, or turn on "Auto Pulse" in the material itself.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca42f-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="ca42f-113">Prerequisites</span></span>

<span data-ttu-id="ca42f-114">針對 [表面重建]，請確定已在 [MRTK 設定] 下指派 MRTK_SurfaceReconstruction]-> 空間感知-> 顯示設定] > 可見的材質。</span><span class="sxs-lookup"><span data-stu-id="ca42f-114">For surface reconstruction, ensure that MRTK_SurfaceReconstruction.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="ca42f-115">針對明確的手，請確定已在 ArticulatedHandMesh 中指派 MRTK_ArticulatedHandMeshPulse。預製專案，其本身應指派于 MRTK 設定-> 輸入 > 手形追蹤-> 手勢網格預製專案。</span><span class="sxs-lookup"><span data-stu-id="ca42f-115">For articulated hand, ensure that MRTK_ArticulatedHandMeshPulse.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="ca42f-116">運作方式</span><span class="sxs-lookup"><span data-stu-id="ca42f-116">How it works</span></span>

<span data-ttu-id="ca42f-117">手上網格著色器會使用 UVs 來對應沿著手網格的脈衝，以及淡出手腕。</span><span class="sxs-lookup"><span data-stu-id="ca42f-117">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="ca42f-118">表面重建著色器會使用頂點位置來對應脈衝。</span><span class="sxs-lookup"><span data-stu-id="ca42f-118">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>
