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
# <a name="pulse-shader"></a>脈衝著色器

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

您可以使用脈衝著色器，以動畫顯示視覺脈衝效果，而不是表面重建、明確表述的手網格或任何其他網格。

## <a name="shader-and-material"></a>著色器和材質

下列材質使用 **SR_Triangles** 著色器。 您可以設定各種選項，例如 [填滿色彩]、[線條色彩] 和 [脈衝色彩]。

- **MRTK_Pulse_SpatialMeshBlue 的材料** 
- **MRTK_Pulse_SpatialMeshPurple 的材料** 
- **MRTK_Pulse_ArticulatedHandMeshBlue 的材料** 
- **MRTK_Pulse_ArticulatedHandMeshPurple 的材料** 

## <a name="prerequisites"></a>必要條件

針對空間網格範例，請確定已在 MixedRealityToolkit 物件 > 空間感知設定檔-> 顯示設定可見的材質上，指派 MRTK_Pulse_SpatialMeshBlue 的材質或 MRTK_Pulse_SpatialMeshPurple。

若為手寫範例，請確定已在 ArticulatedHandMesh 中指派 MRTK_Pulse_ArticulatedHandMeshBlue 的 MRTK_Pulse_ArticulatedHandMeshPurple。預製專案，其本身應指派于 MRTK 設定-> 輸入 > 手動追蹤-> 的手型網格預製專案。

## <a name="how-it-works"></a>運作方式

手上網格著色器會使用 UVs 來對應沿著手網格的脈衝，以及淡出手腕。 表面重建著色器會使用頂點位置來對應脈衝。

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>空間網格範例-PulseShaderSpatialMeshExample unity

類似于 HoloLens 2 的 shell 體驗，您可以用光點來點一下，以產生空間網格的閃爍效果。 範例場景包含 ExampleSpatialMesh 物件，此物件是 Unity 遊戲模式的測試空間網格資料。 此物件將會在裝置上停用並隱藏。

若為 true，則 **PulseShaderSpatialMeshHandler** 會在叫用點位置的空間網格上產生脈衝效果 `PulseOnSelect` 。 在  `Auto Pulse` 重複動畫的材質本身中，屬性也可以設定為 true。  在範例場景中，此腳本會附加至 PulseShaderSpatialMeshParent 預製專案。  空間感知設定檔會透過執行時間空間網格預製專案屬性來參考這個預製專案。 在執行時間期間，PulseShaderSpatialMeshParent 預製專案和會具現化，並新增至空間網狀階層 (只有在裝置上，在編輯器) 中無法觀察到此行為。

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>手形網格範例-PulseShaderHandMeshExample unity

這個範例場景示範使用脈衝著色器的手網格視覺效果。 當 HoloLens 裝置偵測到手時，會觸發脈衝動畫一次。 這種視覺效果的意見反應可以提高使用者的互動信賴度。 

**PulseShaderHandMeshHandler .cs** 腳本會針對指派的材質產生脈衝效果。 預設會核取 [手動偵測到的脈衝]。
