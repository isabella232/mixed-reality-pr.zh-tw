---
title: BoundingBox
description: MRTK 中的周框方塊總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、周框方塊
ms.openlocfilehash: 9d3423aa4518e555d1eea9e0a9619b77998389c54683e4942a44a33eb43afb65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218998"
---
# <a name="bounding-box"></a>週框方塊

![週框方塊](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> 周框方塊已被取代，並由其後續 [界限控制項](bounds-control.md)取代。 使用 [其中一個遷移選項](#migrating-to-bounds-control) 升級現有的遊戲物件。

[`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox)腳本提供在混合現實中轉換物件的基本功能。 周框方塊會顯示全像影像周圍的立方體，表示它可以與互動。 Cube 角落和邊緣上的控點可讓您縮放或旋轉物件。 周框方塊也會對使用者輸入做出回應。 例如，在 HoloLens 2 上，周框方塊會回應手指附近，並提供視覺回饋以協助觀察物件的距離。 您可以輕鬆地自訂所有互動和視覺效果。

如需詳細資訊，請參閱 Windows 開發人員中心中的周[框方塊和應用程式行](https://docs.microsoft.com/windows/mixed-reality/app-bar-and-bounding-box)。

## <a name="example-scene"></a>範例場景

您可以在場景中找到周框方塊設定的範例 `BoundingBoxExamples` 。

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>如何使用 Unity 偵測器新增和設定周框方塊

1. 將 Box 碰撞新增至物件
2. 將 `BoundingBox` 腳本指派給物件
3. 設定選項，例如「啟動」方法 (請參閱下面的偵測 [器屬性](#inspector-properties) 一節) 
4.  (選擇性) 為 HoloLens 2 樣式周框方塊指派 prefabs 和材質 (請參閱下方的[控制碼樣式](#handle-styles)區段) 

> [!NOTE]
> 使用偵測器中的 [ *目標物件* 和 *界限覆寫* ] 欄位，即可指派具有多個子元件之物件中的特定物件和碰撞器。

![周框方塊1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>如何在程式碼中新增和設定周框方塊

1. 具現化 cube GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. `BoundingBox`使用 AddComponent<> () ，將腳本指派給具有碰撞的物件

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. 設定選項 (請參閱下方的偵測 [器屬性](#inspector-properties) 區段) 

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1.  (選擇性) 指派 HoloLens 2 樣式周框方塊的 prefabs 和材質。 這仍然需要透過偵測器進行指派，因為材質和 prefabs 應該以動態方式載入。

> [!NOTE]
> 使用 Unity 的 ' Resources ' 資料夾或 [著色器。]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 因為在執行時間可能遺失著色器排列，所以不建議尋找動態載入著色器。

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>範例：使用 MinMaxScaleConstraint 設定最小、最大周框方塊縮放比例

若要設定最小和最大刻度，請使用 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 。 您也可以使用 MinMaxScaleConstraint 來設定的最小和最大刻度 [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>範例：在遊戲物件周圍新增周框方塊

若要在物件周圍加入周框方塊，只要在 `BoundingBox` 其中加入一個元件即可：

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>偵測器屬性

### <a name="target-object"></a>目標物件

這個屬性會指定周框方塊操作將轉換的物件。 如果未設定物件，周框方塊會預設為擁有者物件。

### <a name="bounds-override"></a>界限覆寫

從物件設定界限計算的方塊碰撞。

### <a name="activation-behavior"></a>啟用行為

有幾個選項可啟用周框方塊介面。

* *啟動時啟用*：啟動場景之後，會顯示周框方塊。
* *依鄰近性啟動*：當有向物件接近的手中，周框方塊會變成可見。
* [*依指標啟動*]：當其以手型指標為目標時，會顯示周框方塊。
* *手動啟用*：周框方塊不會自動顯示。 您可以藉由存取 boundingBox 屬性，以手動方式透過腳本來啟用它。

### <a name="scale-minimum"></a>最小規模

允許的最小比例。 這個屬性已被取代，最好是加入 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 腳本。 如果加入此腳本，將會從它的最小縮放比例取得，而不是從周框方塊中取得。

### <a name="scale-maximum"></a>調整最大值

允許的最大刻度。 這個屬性已被取代，最好是加入 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 腳本。 如果加入此腳本，將會從該腳本中取得最大刻度，而不是從周框方塊中取得。

### <a name="box-display"></a>Box 顯示

不同的周框方塊視覺效果選項。

如果將 [簡維軸] 設定為 [ *自動* 簡維]，腳本將不允許在最小範圍內沿著軸操作。 這會產生2D 周框方塊，通常用於精簡型物件。

### <a name="handles"></a>處理

您可以指派材質和預製專案來覆寫控點樣式。 如果未指派控制碼，則會以預設樣式顯示。

## <a name="events"></a>事件

周框方塊提供下列事件。 此範例會使用這些事件來播放音訊意見反應。

* **輪替開始**：當旋轉開始時引發。
* **旋轉結束**：當旋轉結束時引發。
* **調整已開始**：調整開始時引發。
* **調整結束**：調整結束時引發。

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>處理樣式

依預設，當您只指派 [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) 腳本時，它會顯示 HoloLens 第一代樣式的控制碼。 若要使用 HoloLens 2 樣式控點，您必須指派適當的控制碼 prefabs 和材質。

![周框方塊控制碼樣式](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

以下是 HoloLens 2 樣式周框方塊控點的 prefabs、材質和縮放值。 您可以在場景中找到這個範例 `BoundingBoxExamples` 。

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>處理 HoloLens 2 樣式的 (設定) 

* **處理材質**： BoundingBoxHandleWhite
* **處理抓取材質**： BoundingBoxHandleBlueGrabbed
* **調整控點預製專案**： MRTK_BoundingBox_ScaleHandle. 預製專案
* **縮放控點的預製專案**： MRTK_BoundingBox_ScaleHandle_Slate. 預製專案
* **調整控點大小**： 0.016 (1.6 cm) 
* **縮放控點碰撞填補**： 0.016 (使 grabbable 的碰撞數稍微大於處理視覺效果) 
* **旋轉控點預製專案**： MRTK_BoundingBox_RotateHandle. 預製專案
* **旋轉控點大小**：0.016
* **旋轉柄碰撞碼填補**： 0.016 (使 grabbable 碰撞稍微大於處理視覺效果) 

### <a name="proximity-setup-for-hololens-2-style"></a>HoloLens 2 樣式的鄰近 (設定) 

以實際的距離來顯示及隱藏有動畫的控點。 它有兩個步驟的調整動畫。

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **作用中的相近效果**：啟用以鄰近性為基礎的控制碼啟用
* **處理中等** 距離：第1個步驟調整的距離
* **處理近** 距離：第2個步驟調整的距離
* 最大 **規模**：當手不在周框方塊互動的範圍內時，即為控制碼資產的預設縮放值， (距離以「處理中度相近」定義。 使用0可依預設隱藏控制碼) 
* **中度調整**：當手在周框方塊互動範圍內時，縮放比例值會在「處理接近相近」的上方定義 (距離。 使用1來顯示一般大小) 
* **接近比例**：當手置於抓取互動範圍內時，在「處理接近相近」所定義的抓取互動 (距離範圍內的縮放比例值。 使用1.x 顯示較大的大小) 

## <a name="making-an-object-movable-with-manipulation-handler"></a>使用操作處理常式使物件可移動

您可以使用周框方塊來結合， [`ManipulationHandler.cs`](manipulation-handler.md) 讓物件使用遠的互動來可移動。 操作處理常式同時支援一個和兩個的互動。 [手動追蹤](../input/hand-tracking.md) 可用來將物件與關閉的物件互動。

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

為了讓周框方塊邊緣在使用遠的互動進行移動時，會以相同的方式運作，建議您 [`ManipulationHandler`](manipulation-handler.md) 連接其事件，以 *在*  /  *操作結束* 時開始操作 `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` ，如上面的螢幕擷取畫面所示。

## <a name="migrating-to-bounds-control"></a>遷移至界限控制項

使用周 [框](bounding-box.md) 方塊的現有 prefabs 和實例，可以透過 [ [遷移] 視窗](../tools/migration-window.md) （屬於 MRTK 工具套件的一部分）升級為新的界限控制項。

針對升級個別周框方塊的實例，元件的屬性偵測器內也有一個遷移選項。

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
