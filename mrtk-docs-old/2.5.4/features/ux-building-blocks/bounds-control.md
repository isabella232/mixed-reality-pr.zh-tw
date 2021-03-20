---
title: BoundsControl
description: MRTK 中的界限控制項總覽
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、界限控制、
ms.openlocfilehash: 4c2607f9d1d5c064ec841493dbaaf21c0da0be7a
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682041"
---
# <a name="bounds-control"></a>界限控制項

![界限控制項](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl* 是操作行為的新元件，先前在 *BoundingBox* 中找到。 界限控制項可在安裝過程中進行許多改進和簡化，並加入新功能。 此元件是周框方塊的取代項，將被取代。

[`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl)腳本提供在混合現實中轉換物件的基本功能。 界限控制項將會在全像影像周圍顯示一個方塊，表示它可以與互動。 方塊角落和邊緣的控點可讓您縮放、旋轉或平移物件。 界限控制項也會對使用者輸入做出回應。 例如，在 HoloLens 2 上，界限控制項會回應手指附近，提供視覺回饋以協助觀察物件的距離。 您可以輕鬆地自訂所有互動和視覺效果。

## <a name="example-scene"></a>範例場景

您可以在場景中找到界限控制項設定的範例 `BoundsControlExamples` 。

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>偵測器屬性

### <a name="target-object"></a>目標物件

這個屬性會指定界限控制項操作要轉換的物件。 如果未 setit 物件，則預設為擁有者物件。

### <a name="activation-behavior"></a>啟用行為

有幾個選項可以啟動界限控制介面。

* *啟動時啟動*：啟動場景之後，就會顯示界限控制項。
* *依鄰近性啟動*：當有向物件接近的指標時，界限控制項就會變成可見。
* *依指標啟用*：當邊界控制項是由手形指標設為目標時，便會顯示界限控制項。
* *依鄰近性和指標啟動*：當其以手形指標為目標，或有向物件接近物件時，會顯示界限控制項。
* *手動啟用*：界限控制項不會自動顯示。 您可以藉由存取 boundsControl 屬性，以手動方式透過腳本來啟用它。

### <a name="bounds-override"></a>界限覆寫

從物件設定界限計算的方塊碰撞。

### <a name="box-padding"></a>方塊邊框距離

將填補加入至用來計算控制項範圍的碰撞界線。 這只會影響互動，但也會影響視覺效果。

### <a name="flatten-axis"></a>簡維軸

指出控制項是否在其中一個座標軸上簡維，使其成為2維度，而且不允許沿著該軸操作。 這項功能可用於精簡型物件（例如平板）。
如果 [簡維軸] 設定為 [壓 *平* 合併]，腳本會自動挑選最小範圍為簡維軸的軸。

### <a name="smoothing"></a>平滑處理

平滑區段可讓您設定控制項的縮放和旋轉平滑行為。

### <a name="visuals"></a>視覺效果

您可以藉由修改其中一個對應的視覺效果設定來設定界限控制項的外觀。
視覺效果設定可以連結或內嵌可編寫腳本的物件，並在設定 [物件一節](#configuration-objects)中更詳細地說明。

## <a name="configuration-objects"></a>設定物件

此控制項隨附一組設定物件，可儲存為可編寫腳本的物件，並在不同的實例或 prefabs 之間共用。 設定可以共用和連結為個別可編寫腳本的資產檔案，或是 prefabs 內的可嵌套可編寫腳本的資產。 您也可以直接在實例上定義進一步的設定，而不需要連結至外部或嵌套可編寫腳本的資產。

界限控制偵測器會藉由在屬性偵測器中顯示訊息，來指出是否要將設定共用或內嵌為目前實例的一部分。 此外，在界限控制項屬性視窗本身也無法直接編輯共用的實例，而是必須直接修改其連結的資產，以避免任何意外變更共用設定。

目前的界限控制項提供下列功能的設定物件選項：

* 處理
  * [縮放控點](#scale-handles-configuration)
  * [旋轉控點](#rotation-handles-configuration)
  * [轉譯控制碼](#translation-handles-configuration)
* [連結/線框](#links-configuration-wireframe)
* [Box 顯示](#box-configuration)
* [相近效果](#proximity-effect-configuration)

### <a name="box-configuration"></a>Box 設定

Box 設定會負責呈現一個具有透過碰撞器大小和方塊填補定義之界限的實心方塊。 您可以設定下列屬性：

* **盒材質**：定義未進行互動時，套用至轉譯方塊的材質。 只有在設定此材質時，才會轉譯 box。
* 方塊 **抓取材質**：當使用者透過接近或遠的互動抓取來與控制項互動時，適用于 box 的材質。
* 簡維 **軸顯示比例**：如果其中一個軸是簡維的，[則會套用](#flatten-axis)至方塊顯示的尺規。

### <a name="scale-handles-configuration"></a>調整控點設定

此屬性隱藏式選單可讓您修改界限控制項縮放控點的行為和視覺效果。

* **處理材質**：套用至控制碼的材質。
* **處理抓取的材質**：套用至抓取控制碼的材質。
* **處理預製專案**：調整控點的選擇性預製專案。 如果未設定 MRTK，則會使用 cube 作為預設值。
* **控制碼大小**：縮放控點的大小。
* **碰撞填補**：要加入至控制碼碰撞的填補。
* **操作時繪製 tether**：當作用中時，會從互動起點到目前的手或指標位置繪製 tether 線。
* **處理忽略碰撞碰撞**：如果在此連結碰撞，則控制碼會忽略與此碰撞碰撞的任何衝突。
* **處理預製專案** 控制項時，用於控點的預製專案。
* **顯示縮放控點**：控制控制碼的可見度。
* **調整行為**：可以設定為統一或非統一規模調整。

### <a name="rotation-handles-configuration"></a>旋轉控點設定

此設定會定義旋轉控點的行為。

* **處理材質**：套用至控制碼的材質。
* **處理抓取的材質**：套用至抓取控制碼的材質。
* **處理預製專案**：控制碼的選擇性預製專案。 如果未設定 MRTK，則會使用球體作為預設值。
* **控制碼大小**：控制碼的大小。
* **碰撞填補**：要加入至控制碼碰撞的填補。
* **操作時繪製 tether**：當作用中時，會從互動起點到目前的手或指標位置繪製 tether 線。
* **處理忽略碰撞碰撞**：如果在此連結碰撞，則控制碼會忽略與此碰撞碰撞的任何衝突。
* **處理預製專案碰撞類型**：要與建立的控制碼搭配使用的碰撞型別。
* 顯示 X 軸之控制碼之 **x 的控點**：控制項的可見度。
* **顯示 y 的控制碼**： y 軸的控制碼可見度控制項。
* 顯示 Z 軸控點之 Z 軸的 **控點**：控制項的可見度。

### <a name="translation-handles-configuration"></a>轉譯控點設定

允許啟用和設定界限控制項的轉譯控點。 請注意，每個預設都會停用轉譯控制碼。

* **處理材質**：套用至控制碼的材質。
* **處理抓取的材質**：套用至抓取控制碼的材質。
* **處理預製專案**：控制碼的選擇性預製專案。 如果未設定 MRTK，則會使用球體作為預設值。
* **控制碼大小**：控制碼的大小。
* **碰撞填補**：要加入至控制碼碰撞的填補。
* **操作時繪製 tether**：當作用中時，會從互動起點到目前的手或指標位置繪製 tether 線。
* **處理忽略碰撞碰撞**：如果在此連結碰撞，則控制碼會忽略與此碰撞碰撞的任何衝突。
* **處理預製專案碰撞類型**：要與建立的控制碼搭配使用的碰撞型別。
* 顯示 X 軸之控制碼之 **x 的控點**：控制項的可見度。
* **顯示 y 的控制碼**： y 軸的控制碼可見度控制項。
* 顯示 Z 軸控點之 Z 軸的 **控點**：控制項的可見度。

### <a name="links-configuration-wireframe"></a>連結設定 (線框) 

連結設定會啟用界限控制項的線框功能。 您可以設定下列屬性：

* **線框材質**：適用于線框網格的材質。
* **線框 edge 半徑**：線框的粗細。
* 框線 **圖形**：框線的形狀可以是三次或圓柱。
* **顯示** 框線：控制項線框的可見度。

### <a name="proximity-effect-configuration"></a>鄰近效果設定

以實際的距離來顯示及隱藏有動畫的控點。 它有兩個步驟的調整動畫。 預設值會設定為 HoloLens 2 樣式行為。

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **作用中的相近效果**：啟用以鄰近性為基礎的控制碼啟用
* **物件中近** 距離：第1個步驟調整的距離
* **物件近** 距離：第2個步驟調整的距離
* 最大 **規模**：當手超出界限控制互動的範圍時，即為「處理中度相近」所定義之界限控制互動 (距離的預設縮放值。 使用0可依預設隱藏控制碼) 
* **中位數**：當手落在範圍內的界限控制互動範圍內時，縮放比例值會以「處理接近相近」 (距離定義。 使用1來顯示一般大小) 
* **接近比例**：當手置於抓取互動範圍內時，在「處理接近相近」所定義的抓取互動 (距離範圍內的縮放比例值。 使用1.x 顯示較大的大小) 
* **目前的成長率**：當手移至最接近的範圍時，對鄰近比例的物件縮放比例。
* **中度成長率**：當手從中移至接近鄰近時，為鄰近比例的物件縮放比例。
* **關閉成長率**：當手移離接近物件中心時，對鄰近比例的物件縮放比例。

## <a name="constraint-system"></a>條件約束系統

界限控制項支援在使用界限控制控點時，使用 [條件約束管理員](constraint-manager.md) 來限制或修改平移、旋轉或縮放行為。

屬性偵測器會在下拉式清單中顯示所有附加至相同遊戲物件的可用條件約束管理員，其中有一個選項可以用來滾動並反白顯示選取的條件約束管理員。

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>事件

界限控制項提供下列事件。 此範例會使用這些事件來播放音訊意見反應。

* **輪替開始**：當旋轉開始時引發。
* **旋轉已停止**：當旋轉停止時引發。
* **調整已開始**：調整開始時引發。
* **調整已停止**：當調整停止時引發。
* **轉譯開始**：轉譯開始時引發。
* **轉譯已停止**：當轉譯停止時引發。

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>彈性 (實驗性) 

彈性可在透過界限控制項操作物件時使用。 請注意， [彈性系統](../elastics/elastic-system.md) 仍處於實驗性狀態。 若要啟用彈性，請連結現有的彈性 manager 元件，或透過按鈕建立並連結新的彈性管理員 `Add Elastics Manager` 。

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>處理樣式

依預設，當您只指派 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 腳本時，它會顯示 HoloLens 1 代樣式的控制碼。 若要使用 HoloLens 2 樣式控點，您必須指派適當的控制碼 prefabs 和材質。

![界限控制項控點樣式2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

以下是 HoloLens 2 樣式界限控制項控點的 prefabs、材質和縮放值。 您可以在場景中找到這個範例 `BoundsControlExamples` 。

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

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

## <a name="transformation-changes-with-object-manipulator"></a>使用物件操作工具進行轉換變更

界限控制項可以搭配使用 [`ObjectManipulator.cs`](object-manipulator.md) ，以允許特定類型的操作 (例如 在不使用控制碼的情況下移動物件) 。 操作處理常式同時支援一個和兩個的互動。 [手動追蹤](../input/hand-tracking.md) 可用來將物件與關閉的物件互動。

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

為了讓界限控制邊緣在使用遠的互動進行移動時以相同的方式運作，建議您 [`ObjectManipulator`](object-manipulator.md) 連接其事件，以 *在*  /  *操作結束* 時開始操作 `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` ，如上面的螢幕擷取畫面所示。

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>如何使用 Unity 偵測器新增和設定界限控制項

1. 將 Box 碰撞新增至物件
2. 將 `BoundsControl` 腳本指派給物件
3. 設定選項，例如「啟動」方法 (請參閱下面的偵測 [器屬性](#inspector-properties) 一節) 
4.  (選擇性) 指派 HoloLens 2 樣式界限控制項的 prefabs 和材質 (請參閱下方的 [控制碼樣式](#handle-styles) 區段) 

> [!NOTE]
> 使用偵測器中的 [ *目標物件* 和 *界限覆寫* ] 欄位，即可指派具有多個子元件之物件中的特定物件和碰撞器。

![界限控制項](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>如何在程式碼中新增和設定界限控制項

1. 具現化 cube GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. `BoundsControl`使用 AddComponent<> () ，將腳本指派給具有碰撞的物件

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. 您可以直接在控制項上或透過其中一個可編寫腳本的設定來設定選項 (請參閱下面的偵測[器屬性](#inspector-properties)和設定[一節) ](#configuration-objects)

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1.  (選擇性) 指派 HoloLens 2 樣式界限控制項的 prefabs 和材質。 這仍然需要透過偵測器進行指派，因為材質和 prefabs 應該以動態方式載入。

> [!NOTE]
> 使用 Unity 的 ' Resources ' 資料夾或 [著色器。]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 因為在執行時間可能遺失著色器排列，所以不建議尋找動態載入著色器。

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>範例：使用 MinMaxScaleConstraint 設定最小、最大界限控制小數位數

若要設定最小和最大刻度，請將加入 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 至您的控制項。 當界限控制項自動附加和啟用條件約束管理員時，MinMaxScaleConstraint 會在附加並設定之後，自動套用至轉換變更。

您也可以使用 MinMaxScaleConstraint 來設定的最小和最大刻度 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 。

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>範例：在遊戲物件周圍新增界限控制項

若要在物件周圍加入界限控制項，只要在 `BoundsControl` 其中加入元件即可：

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>從周框方塊進行遷移

使用周 [框](bounding-box.md) 方塊的現有 prefabs 和實例，可以透過 [ [遷移] 視窗](../tools/migration-window.md) （屬於 MRTK 工具套件的一部分）升級為新的界限控制項。

針對升級個別周框方塊的實例，元件的屬性偵測器內也有一個遷移選項。

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>另請參閱

* [物件操作工具](object-manipulator.md)
* [條件約束管理員](constraint-manager.md)
* [遷移視窗](../tools/migration-window.md)
* [彈性系統 (實驗性) ](../elastics/elastic-system.md)
