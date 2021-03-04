---
title: ObjectCollection
description: MRTK 中的物件集合總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、物件集合、
ms.openlocfilehash: db4622da96c074a41d1042be6570b0d67bce2859
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780164"
---
# <a name="object-collection"></a>物件集合

![物件集合主要](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

物件集合是一種腳本，可協助您配置預先定義之三維圖形中的物件陣列。 它支援各種表面樣式，包括平面、圓柱、球體和放射狀。 由於它支援 Unity 中的任何物件，因此可以用來配置2D 和3D 物件。

## <a name="object-collection-scripts"></a>物件集合腳本

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 支援圓柱圖、平面、球體、放射狀介面類別型
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) 支援散佈的樣式集合  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) 提供一些其他選項來 GridObjectCollection。 **注意：** TileGridObjectCollection 不會擴充 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) ，而且有數個 bug (請參閱 [問題 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)) 。 因此，建議使用 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 。

|![方格物件集合-圓柱圖](../images/object-collection/MRTK_ObjectCollectionCylinder.png) 方格物件集合-圓柱圖 | ![方格物件集合-球體](../images/object-collection/MRTK_ObjectCollectionSphere.png) 方格物件集合-球體 |
|:--- | :--- |
|![方格物件集合-放射狀](../images/object-collection/MRTK_ObjectCollectionRadial.png) 方格物件集合-放射狀 | ![方格物件集合-平面](../images/object-collection/MRTK_ObjectCollectionPlane.png) 方格物件集合-平面 |
|![散佈的物件集合](../images/object-collection/MRTK_ObjectCollectionScattered.png) 散佈的物件集合 | ![磚方格物件集合](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) 磚方格物件集合 |

## <a name="how-to-use-an-object-collection"></a>如何使用物件集合

若要建立集合，請建立空白的 GameObject，並將其中一個物件集合腳本指派給它。 任何 (s) 的物件都可以新增為 GameObject 的子系。 完成加入子物件之後，請按一下 [檢查] 面板中的 [ *更新集合* ] 按鈕，以產生物件集合。 系統會根據集合參數，在場景中設定物件。 您也可以透過程式碼來存取更新集合。

![物件集合腳本](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` 內容對齊

您可以對齊 GridObjectCollection 中的內容，讓父物件錨定至集合的上方/中間/下和左/上/下/右。 使用 **錨點** 屬性指定內容對齊。

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` 版面配置順序

使用 [ **配置** ] 欄位來指定子系配置的資料列/資料行順序：

**然後** ，資料行會先依資料行) 水準 (來配置資料行子系，然後) 依資料列垂直 (。 在程式碼) 中使用 **Num columns** (或 columns 屬性來指定方格中的資料行數目。

![資料行之後的資料列版面配置](../images/object-collection/MRTK_ColumnThenRow.png)

**然後** ，資料列會先依資料列) 垂直配置 (資料行，然後) 依資料行水準 (。 在程式碼) 中使用 **Num rows** (或 rows 屬性來指定方格中的資料列數目。

![資料列 then 資料行版面配置](../images/object-collection/MRTK_RowThenColumn.png)

只有在使用資料行的單一資料列中配置了 **水準** 子系

**垂直** 子系只會在單一資料行中使用資料列進行配置。

## <a name="object-collection-examples"></a>物件集合範例

`ObjectCollectionExamples` (資產/MRTK/範例/示範/UX/collection/場景/ObjectCollectionExamples unity) 範例場景包含各種物件集合類型的範例。

專案的[定期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是範例應用程式，示範物件集合的運作方式。 它使用物件集合來配置不同圖形中的3D 元素方塊。

## <a name="object-collection-types"></a>物件集合類型

**3D 物件**

物件集合可以用來配置匯入的3D 物件。 下列範例顯示使用集合的3D 椅子模型物件的平面和圓柱版面配置。

![物件集合3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**2D 物件**

您也可以從2D 影像建立物件集合。 例如，多個影像可以用格線樣式來放置。

![物件集合2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
