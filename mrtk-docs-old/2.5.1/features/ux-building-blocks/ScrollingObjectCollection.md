---
title: ScrolingObjectCollection
description: 總覽功能表類型 MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、滾動物件
ms.openlocfilehash: 86d0d79c2b9230beb84b8beda4ba488d857828a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683721"
---
# <a name="scrolling-object-collection"></a>滾動物件集合

![滾動物件集合](../images/scrolling-collection/ScrollingCollection_Main.jpg)

MRTK 滾動物件集合是 UX 元件，可透過包含的可見區域來滾動3D 內容。 滾動移動可透過接近或遠的輸入互動和離散分頁來觸發。 它同時支援互動式和非互動式物件。

## <a name="getting-started-with-the-scrolling-object-collection"></a>開始使用滾動物件集合

### <a name="setting-up-the-scene"></a>設定場景

1. 建立新的 unity 場景。
1. 藉由流覽至 **混合現實工具** 組  >  **加入場景並設定**，將 MRTK 加入場景。

### <a name="setting-up-the-scrolling-object"></a>設定滾動物件

1. 在場景中建立空白的遊戲物件，並將其位置變更為 (0、0、1) 。
1. 將 [滾動物件集合](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) 元件新增至遊戲物件。

    加入滾動物件集合時，會自動將方塊碰撞器和 [近端互動可觸式](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 元件附加至根遊戲物件。 這些元件可讓 scroll 物件接聽近距離互動輸入事件，例如指標觸控或按一下。  

    MRTK 滾動物件集合有兩個重要元素，這些元素會在根滾動物件階層下建立為子遊戲物件：
    * `Container` -所有滾動的內容物件都必須是容器遊戲物件的子系。
    * `Clipping bounds` -如果已啟用滾動內容遮罩，則裁剪界限元素可確保只會顯示其界限內的可滾動內容。 裁剪界限遊戲物件有兩個元件：停用的方塊碰撞器和 [裁剪](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)方塊。

![滾動物件集合元素](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>將內容加入至滾動物件

滾動物件集合可以與 [格線物件集合](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 結合，以便在具有統一大小和間距的對齊元素方格中配置內容。

1. 建立空的遊戲物件做為捲軸容器的子系。
1. 將方格物件集合元件新增至遊戲物件。
1. 若是垂直的單一資料行捲軸，請在 [偵測器] 索引標籤中，設定網格物件集合，如下所示：
    * **Num 資料行**：1
    * **版面** 配置：資料行 then 資料列
    * **錨點**：左上方
1. 根據內容物件的尺寸來變更 **儲存格的寬度** 和 **高度** 。
1. 將 content 物件新增為 grid 物件的子系。
1. 按下 [ **更新集合**]。

![格線版面配置](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> 任何滾動的內容物件材質都必須使用 [MRTK 標準著色器](../rendering/MRTKStandardShader.md) ，才能讓可見區域的剪切效果正常運作。

> [!NOTE]
> 如果已啟用滾動內容遮罩，則滾動物件集合會將 [材質實例](../rendering/MaterialInstance.md) 元件加入至已附加轉譯器的任何內容物件。 此元件可用來管理實例材質存留期，並改善記憶體效能。

### <a name="configuring-the-scrolling-viewable-area"></a>設定捲軸可見區域

1. 若要透過物件的單一資料行垂直捲動，請在 [偵測器] 索引標籤中，設定滾動物件集合，如下所示：
    * **每一層** 的資料格：1
    * 根據所需的可見資料列數目，選擇 **每頁的層級** 數目
1. 根據內容物件的尺寸，變更 **頁面儲存格寬度**、 **高度** 和 **深度** 。

請注意，在捲軸可見區域外的內容物件現在是停用的，而與捲軸線框相交的物件可能會由裁剪基本部分遮罩。

![可見區域](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>在編輯器中測試滾動物件集合

1. 按下 [播放] 並按住空格鍵以顯示輸入模擬手。
1. 移動手，直到滾動碰撞器或任何滾動的互動式內容都處於焦點狀態，然後按一下滑鼠左鍵並向下拖曳，以觸發滾動移動。

## <a name="controlling-the-scrolling-object-from-code"></a>從程式碼控制滾動物件

MRTK 滾動物件集合會公開一些公用方法，以允許移動滾動容器，方法是根據屬性設定來貼上其位置 `pagination` 。

如何存取滾動物件集合分頁介面的範例可用於 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` 資料夾之下。 可 [滾動分頁](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) 範例腳本可以連結至場景中任何現有的滾動物件集合。 然後，可透過公開 Unity 事件的場景元件參考腳本 (例如， [MRTK 按鈕](Button.md)) 。

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }       
}
```

## <a name="scrolling-object-collection-properties"></a>滾動物件集合屬性

| 一般                      |               Description                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 捲動方向             | 內容應滾動的方向。|

| 分頁                   |              Description                                                                                                                                                                                       |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 每一層的資料格               | 在上下捲軸上，資料列中的資料格數目，或是由左至右捲軸之資料行中的資料格數目。                                                                                                         |
| 每頁層級               | 捲動區域中可見層的數目。                                                                                                                                                                         |
| 頁面儲存格                    | 分頁資料格的維度。                  |

| 進階設定            |           Description                                                                                                                                                                                          |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 遮罩編輯模式               | 用來定義裁剪方塊遮罩界限的編輯模式。 選擇 [自動] 以自動使用分頁值。 選擇 [手動] 以啟用直接操作裁剪 box 物件。|
| 碰撞編輯模式           | 編輯模式，用於定義捲軸互動碰撞條界限。 選擇 [自動] 以自動使用分頁值。 選擇 [手動] 以啟用碰撞的直接操作。|
| 可滾動                   | 啟用/停用近乎/遠的互動的滾動。                  |
| 在預先呈現時使用            | 切換 scrollingObjectCollection 是否會使用相機 OnPreRender 事件來管理內容可見度。                  |
| 分頁曲線             | 分頁的動畫曲線。                  |
| 動畫長度             | PaginationCurve 進行評估所需的時間長度，以秒為) 單位 (。                  |
| 手動差異滾動閾值  | 目前指標的距離（以計量為單位）可以在觸發捲軸拖曳之前沿著捲軸方向移動。                  |
| 前端觸控距離         | 距離（以量為單位），用來確認在捲軸的前方是否已開始觸控互動的本機 xy 平面。                  |
| 釋放閾值            | 從所需的捲軸範圍，收回從觸控到已發行的轉換所需的提款量（單位為計量）。                  |

| 速度 |       Description                                                                                                                                                                             |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 速度的類型       | 所需的捲軸速度衰減類型。                                                                                        |
| 速度乘數     | 要套用到捲軸的 (額外) 速度。                                                                                                                                                        |
| 速度 dampen     | 套用至速度的衰減量。 |
| 彈跳乘數     | 乘數，以在使用每個畫面的衰減或每個專案的衰減時，將更多彈跳新增至清單的 overscroll。 |

| Debug 選項 |          Description                                                                                                                                                                          |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 遮罩已啟用       | 捲軸內容的可見度模式。 預設值會遮罩捲軸可見區域以外的所有物件。                                                                                        |
| 顯示臨界值平面     | 若為 true，則編輯器會在捲軸界限周圍轉譯觸控釋放閾值的平面。                                                                                                                                                        |
| 調試分頁     | 使用這個區段可在執行時間時，對捲軸分頁進行調試。 |

| 事件|     描述                                                                                                                                                                               |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 按一下時       | 當捲軸背景碰撞或其任何互動式內容收到點擊時，所觸發的事件。                                                                                        |
| 開始觸控時     | 捲軸背景碰撞項或其任何互動式內容收到接近互動觸控時所觸發的事件。                                                                                                                                                        |
| 在觸控結束時     | 當主動觸控互動結束時，透過將接近的互動指標移至其中一個版本閾值平面時，所觸發的事件。 |
| 開始使用時     | 當 scroll 容器以互動、速度 fallofff 或分頁開始移動時，所觸發的事件。 |
| 動力已結束     | 捲軸容器停止移動、速度 fallofff 或分頁時所觸發的事件。 |

## <a name="scrolling-example-scene"></a>滾動範例場景

**ScrollingObjectCollection** 範例場景是由3個可滾動的範例所組成，每一個都有不同的速度衰減設定。 範例場景包含牆壁，以顯示階層中依預設停用的表面放置行為。 範例場景可以在資料夾下找到 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` 。

![滾動物件集合範例場景](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>滾動範例 prefabs

為了方便起見，您可以使用兩個滾動物件集合 prefabs。 您可以在資料夾下找到範例 prefabs ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` 。

![滾動物件集合 prefabs](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>另請參閱

* [裁剪基本](../rendering/ClippingPrimitive.md)
* [材質實例](../rendering/MaterialInstance.md)
* [標準著色器](../rendering/MRTKStandardShader.md)
* [物件集合](ObjectCollection.md)
