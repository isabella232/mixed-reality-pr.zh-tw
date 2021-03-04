---
title: ElasticSystem
description: MRTK 中彈性模擬的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、ElasticsSystem、
ms.openlocfilehash: 4538ad9df6bfd5e65ff0c91c61a24b17740da649
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779842"
---
# <a name="elastic-system-experimental"></a>彈性系統 (實驗性) 

![彈性系統](../images/elastics/Elastics_Main1.gif)

MRTK 隨附彈性的模擬系統，其中包含各種可延伸和彈性的子類別，並提供4維四元數、三維磁片區彈簧和簡單線性彈簧系統的系結。

目前支援 [彈性 manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 的下列 MRTK 元件可利用彈性功能：

- [界限控制項](../ux-building-blocks/bounds-control.md)
- [物件操作工具](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>彈性管理員

![彈性 System2](../images/elastics/Elastics_Main.gif)

彈性管理員會處理傳遞的轉換，並將其饋送至彈性系統。

您可以透過兩個步驟來啟用自訂群組件的彈性：

1. 在操作開始時呼叫 Initialize 方法，並以目前的主控制項轉換來更新系統。
1. 只要針對更新的目標轉換執行彈性計算時，就會查詢 ApplyHostTransform。

請注意，彈性會在操作結束 (透過彈性 manager 更新迴圈) 來繼續模擬。 若要封鎖此行為，彈性自動更新 [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) 可以設定為 false。

根據預設，彈性管理員元件在新增至遊戲物件時，不會針對任何轉換類型啟用彈性。
您必須 `Manipulation types using elastic feedback` 針對特定的轉換類型啟用欄位，才能建立所選類型的彈性設定和範圍。

### <a name="elastics-configurations"></a>彈性設定

彈性管理員類似于 [界限控制項](../ux-building-blocks/bounds-control.md#configuration-objects)設定，隨附一組設定物件，可儲存為可編寫腳本的物件，並在不同的實例或 prefabs 間共用。 設定可以共用和連結為個別可編寫腳本的資產檔案，或是 prefabs 內的可嵌套可編寫腳本的資產。 您也可以直接在實例上定義進一步的設定，而不需要連結至外部或嵌套可編寫腳本的資產。

彈性 manager 偵測器會藉由在屬性偵測器中顯示訊息，來指出是否要將設定共用或內嵌為目前實例的一部分。 此外，您無法直接在 [彈性管理員] 屬性視窗中編輯共用的實例，而是改為直接修改其連結的資產，以避免任何意外變更共用設定。

彈性 manager 提供下列轉換類型的設定物件選項，每個都以 [彈性設定物件](#elastic-configuration-object)表示：

- 彈性翻譯
- 輪替彈性
- 調整彈性

#### <a name="elastic-configuration-object"></a>彈性設定物件

彈性設定會定義禁止調和 oscillator 差異系統的屬性。
下列屬性可以調整，但在 MRTK 中已有一組預設值：

- **大量**：模擬 oscillator 元素的大量。
- **HandK**：手上彈簧常數。
- **EndK**：結束端點彈簧常數。
- **SnapK**：貼齊點彈簧常數。
- **拖曳**：拖曳/阻尼因素，與速度成正比。

### <a name="elastics-extents"></a>彈性範圍

彈性範圍設定會依操作的類型而有所不同。 轉譯和小數位數是由 [大量彈性範圍](#volume-elastic-extent) 所表示，旋轉是以 [四元數彈性範圍](#quaternion-elastic-extent)表示。

#### <a name="volume-elastic-extent"></a>大量彈性範圍

磁片區範圍定義了禁止調和 oscillator 可以自由移動的三個維度空間。

![彈性磁片區延展界限](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds**：代表彈性空間的下限。
- **UseBounds**：是否應由系統遵守延展界限。 若為 true，當目標位置的目前反復專案位於延展界限之外時，將會套用 end force。
- **快照點**：指向系統將貼齊的空間內部。
- **RepeatSnapPoints**：將貼齊點重複到無限大。 現有的貼齊點將作為模數，其中實際的貼齊點會對應到每個貼齊點的最接近整數倍數。
- **SnapRadius**：貼齊點開始強制彈簧的距離。

![彈性磁片區對齊格線](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>四元數彈性範圍

四元數範圍定義四個維度旋轉空間，讓禁止調和 oscillator 可以自由旋轉。

![彈性旋轉範例](../images/elastics/Elastics_Rotation.gif)

- **快照點**：系統將貼齊的歐拉角度。
- **RepeatSnapPoints**：重複對齊點。 現有的貼齊點將作為模數，其中實際的貼齊點會對應到每個貼齊點的最接近整數倍數。
- **SnapRadius**：貼齊點開始強制歐拉度的彈簧的弧形角度。

## <a name="elastics-example-scene"></a>彈性範例場景

您可以在場景中找到彈性設定的範例 `ElasticSystemExample` 。

![彈性範例場景](../images/elastics/Elastics_Example_Scene.png)
