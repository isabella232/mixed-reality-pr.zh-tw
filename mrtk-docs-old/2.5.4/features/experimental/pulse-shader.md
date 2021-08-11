---
title: PulseShader
description: MRTK 中的脈衝著色器描述。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 6a8979b42af9ce8e12875c8bd24ecc4fdc20df46650192fceb8b7a25707571ac
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197031"
---
# <a name="pulse-shader"></a>脈衝著色器

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

![MRTK_HandMesh_Pulse2 ](https://user-images.githubusercontent.com/13754172/68262035-e4f7e600-fff6-11e9-9858-796afd1cabc5.gif) 使用脈衝著色器，在表面重建、明確展示的手網格或任何其他網格上建立視覺脈衝效果的動畫。

## <a name="shader-and-material"></a>著色器和材質

**MRTK_SurfaceReconstruction 的材料** 和 **MRTK_ArticulatedHandMeshPulse** 會使用 **SR_Triangles** 著色器。 您可以設定各種選項，例如 [填滿色彩]、[線條色彩] 和 [脈衝色彩]。

## <a name="example-scene"></a>範例場景

開啟 **PulseShaderExamples unity** 場景，並觀察球、表面重建和已說出之手形網格的影響。

使用 SurfacePulse .cs 腳本對指派的材質產生脈衝效果的動畫，或在材質本身開啟「自動脈衝」。

## <a name="prerequisites"></a>必要條件

針對 [表面重建]，請確定已在 [MRTK] 設定 > 空間感知-> 顯示設定可見的材質中指派 MRTK_SurfaceReconstruction。

針對明確的手，請確定已在 ArticulatedHandMesh 中指派 MRTK_ArticulatedHandMeshPulse。預製專案，其本身應指派于 MRTK 設定-> 輸入-> 手動追蹤-> 手型網格預製專案。

## <a name="how-it-works"></a>運作方式

手上網格著色器會使用 UVs 來對應沿著手網格的脈衝，以及淡出手腕。 表面重建著色器會使用頂點位置來對應脈衝。
