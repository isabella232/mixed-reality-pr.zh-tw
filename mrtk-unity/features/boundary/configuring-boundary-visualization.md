---
title: 設定界限視覺效果
description: 在 MRTK 中設定界限系統的詳細資料
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、界限系統、
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144489"
---
# <a name="configuring-the-boundary-visualization"></a>設定界限視覺效果

*界限視覺效果設定檔* 提供的選項可用來設定界限系統的視覺效果美學和其他相關參數。 界限視覺效果會附加至場景中的 Mixed Reality Playspace 物件，並隨使用者傳送。

## <a name="general-settings"></a>一般設定

![界限視覺效果一般設定](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>界限高度

界限高度表示應該呈現邊界上限之樓層平面的距離。 預設值為3個計量。

## <a name="floor-settings"></a>樓層設定

![界限視覺效果樓層設定](../images/boundary/BoundaryVisualizationFloorSettings.png)

**顯示**

指出是否要建立 floor 平面，並將其加入場景中。 預設值為 true。

**Material**

指出建立 floor 平面時應該使用的材質。

**縮放**

表示要建立之樓層平面的大小（以量值為單位）。 預設小數位數為3計量 x 3 計量方塊。

**實體層**

應設定 floor 平面的圖層。 預設值為 *預設* 的圖層。

## <a name="play-area-settings"></a>播放區域設定

![界限視覺效果播放區域設定](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**顯示**

指出是否要建立播放區域矩形並將其加入場景中。 預設值為 true。

**Material**

指出建立播放區域物件時應使用的材質。

**實體層**

應設定播放區域的圖層。 預設值為 [ *忽略 Raycast* 圖層]。

## <a name="tracked-area-settings"></a>追蹤區域設定

![界限視覺效果追蹤區域設定](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**顯示**

指出是否要建立追蹤區域的外框，並將其加入場景中。 預設值為 true。

**Material**

表示建立追蹤區域外框時應該使用的材質。

**實體層**

應設定追蹤區域的圖層。 預設值為 [ *忽略 Raycast* 圖層]。

## <a name="boundary-wall-settings"></a>界限牆設定

![界限視覺效果邊界牆設定](../images/boundary/BoundaryVisualizationWallSettings.png)

**顯示**

指出是否要建立界限牆平面，並將其加入場景中。 預設值為 false。

**Material**

指出建立邊界牆平面時應該使用的材質。

**實體層**

應設定界限牆的圖層。 預設值為 [ *忽略 Raycast* 圖層]。

> [!NOTE]
> 將界限牆元件設定為 [ *略過 Raycast* ] 以外的實體層，可能會讓使用者無法與場景內的物件互動。

## <a name="boundary-ceiling-settings"></a>界限上限設定

![界限視覺效果界限上限設定](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**顯示**

指出是否要建立界限上限平面，並將其加入場景中。 預設值為 false。

**Material**

指出建立界限上限平面時應使用的材質。

**實體層**

應設定界限牆的圖層。 預設值為 [ *忽略 Raycast* 圖層]。

> [!NOTE]
> 將界限上限元件設定為 [ *略過 Raycast* ] 以外的實體層，可能會讓使用者無法與場景內的物件互動。

## <a name="see-also"></a>另請參閱

- [界限 API 檔](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [界限系統](boundary-system-getting-started.md)
