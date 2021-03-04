---
title: README_ObjectManipulator
description: 如何在 MRTK 中使用物件操作工具
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、物件操作、
ms.openlocfilehash: 0e315c62261febd535452fb21bde4d56a585b295
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780971"
---
# <a name="object-manipulator"></a>物件操作工具

![物件操作工具主](Images/ManipulationHandler/MRTK_Manipulation_Main.png)

*ObjectManipulator* 是操作行為的新元件，先前在 *ManipulationHandler* 中找到。 物件操作工具可進行許多改進和簡化。 此元件取代了將被取代的操作處理常式。

*ObjectManipulator* 腳本會使用一或兩個手來讓物件可移動、可擴充及 rotatable。 物件操作工具可以設定為控制物件將如何回應各種輸入。 腳本應可搭配大部分的互動形式使用，例如 HoloLens 2 的有向的手勢、HoloLens 2 手片片、HoloLens 1 注視和手勢，以及沉浸式耳機移動控制器輸入。

## <a name="how-to-use-the-object-manipulator"></a>如何使用物件操作工具

若要使用物件操作工具，請先將 `ObjectManipulator` 腳本元件加入至 GameObject。 請務必同時將碰撞新增至物件，以符合其 grabbable 界限。

若要讓物件回應接近明確的手輸入，請新增 `NearInteractionGrabbable` 腳本。

將 rigidbody 元件新增至物件，即可為物件操作工具啟用物理行為。 新增此元件所啟用的物理行為會在 [*物理和衝突*](#physics-and-collisions)中更詳細地討論。

如此一來，就可以將 [操作條件約束元件](#transform-constraints) 加入至物件，以限制操作。 這些是使用操作的特殊元件，並以某種方式變更操作行為。

![操作處理常式](Images/ObjectManipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>偵測器屬性和欄位

<img src="Images/ObjectManipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>一般屬性

#### <a name="host-transform"></a>主機轉換

將操作的物件轉換。 預設為元件的物件。

#### <a name="manipulation-type"></a>操作類型

指定是否可使用一或兩個手來操作物件。 因為這個屬性是一個旗標，所以可以選取兩個選項。

- *一個右手*：如果選取，則會啟用一次操作。
- *兩個右手*：啟用兩個執行中的操作（如果有選取）。

#### <a name="allow-far-manipulation"></a>允許目前的操作

指定是否可以使用與指標互動的方式來執行操作。

### <a name="one-handed-manipulation-properties"></a>一個右手操作屬性

#### <a name="one-hand-rotation-mode-near"></a>接近的一次旋轉模式

指定當物件正在抓取時，物件的行為方式。 這些選項僅適用于已表達的手。

- *旋轉物件中心*：物件使用旋轉旋轉，但關於物件中心點。 物件會在旋轉時變得較小，但您可能會覺得手和物件之間的連接中斷。 更適用于目前的互動。
- *旋轉大約抓取點*：旋轉物件，並將 thumb 與食指之間的抓取點旋轉。 它應該會像是物件被手鎖起來。

#### <a name="one-hand-rotation-mode-far"></a>一種手邊的旋轉模式

指定物件在一次抓取時，該物件將如何運作。 這些選項僅適用于已表達的手。

- *旋轉物件中心*：使用手旋轉旋轉物件，但關於物件中心點。 很適合用來檢查距離，而不會在物件中心隨著物件旋轉而移動。
- *旋轉大約抓取點*：使用手旋轉旋轉物件，但指標光線叫用點則會旋轉。 適用于檢查。

### <a name="two-handed-manipulation-properties"></a>兩個右手操作屬性

#### <a name="two-handed-manipulation-type"></a>兩個右手操作類型

指定兩次手操作如何轉換物件。 因為此屬性是旗標，所以可以選取任何數目的選項。

- *移動*：若已選取，則允許移動。
- *調整*：若已選取，則允許縮放。
- *旋轉*：若已選取，則允許旋轉。

![操作處理常式](Images/ManipulationHandler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>條件約束

#### <a name="add-constraint"></a>新增條件約束

此按鈕可讓您直接從物件操作工具偵測器加入條件約束元件。 專案中應該會顯示專案中的所有條件約束。 如需詳細資訊，請參閱 [轉換條件約束](#transform-constraints) 。

#### <a name="go-to-component"></a>移至元件

在此物件上找到的所有條件約束，都會在這裡列出，並顯示 [ *移至元件* ] 按鈕。 此按鈕會讓偵測器滾動至選取的條件約束元件，以便進行設定。

### <a name="physics"></a>物理特性

#### <a name="release-behavior"></a>發行行為

指定操作物件在發行時應保留的實體屬性。 要求 rigidbody 元件必須在該物件上。 因為這個屬性是一個旗標，所以可以選取兩個選項。

- *保持速度*：當物件被選取時，如果選取此選項，則會保留其線性速度。
- *保持角度*：當物件被選取時，如果已選取此選項，則會維持其角度的速度。

### <a name="smoothing"></a>平滑處理

#### <a name="smoothing-active"></a>啟用平滑

指定是否啟用平滑處理。

#### <a name="move-lerp-time"></a>移動 lerp 時間

要套用至移動的凹凸貼圖數量。 將0平滑表示無平滑。 最大值表示不變更值。

#### <a name="rotate-lerp-time"></a>輪替 lerp 時間

要套用至旋轉的凹凸貼圖數量。 將0平滑表示無平滑。 最大值表示不變更值。

#### <a name="scale-lerp-time"></a>調整 lerp 時間

要套用至尺規的凹凸貼圖數量。 將0平滑表示無平滑。 最大值表示不變更值。

### <a name="manipulation-events"></a>操作事件

操作處理常式會提供下列事件：

- *OnManipulationStarted*：在操作開始時引發。
- *OnManipulationEnded*：在操作結束時引發。
- *OnHoverStarted*：當手形/控制器停留在接近或遠的 manipulatable 時，就會引發。
- *OnHoverEnded*：當手形/控制器取消暫留 manipulatable 時（接近或遠）時，就會引發。

操作的事件引發順序為：

*OnHoverStarted*  -> *OnManipulationStarted*  -> *OnManipulationEnded*  -> *OnHoverEnded*

如果沒有操作，您仍會收到具有下列引發順序的暫止事件：

*OnHoverStarted*  -> *OnHoverEnded*

## <a name="transform-constraints"></a>轉換條件約束

條件約束可以用來限制操作的方式。 例如，有些應用程式可能需要輪替，但物件也需要保持垂直。 在此情況下，您 `RotationAxisConstraint` 可以將加入至物件，並用來將旋轉限制為 y 軸旋轉。 MRTK 提供許多條件約束，如下所述。

您也可以定義新的條件約束，並使用它們來建立某些應用程式可能需要的獨特操作行為。 若要這樣做，請建立一個繼承自 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 的腳本，並執行抽象 `ConstraintType` 屬性和抽象 `ApplyConstraint` 方法。 將新的條件約束加入至物件時，它應該會以定義的方式來限制操作。 這個新的條件約束也應該顯示在物件操作工具 [條件限制欄位](#constraints)中。

MRTK 提供的所有條件約束都會共用下列屬性：

#### <a name="target-transform"></a>目標轉換

受限制的操作物件轉換。 這應該與 ObjectManipulator [*主機轉換*](#host-transform)相同。 預設為元件的物件。

#### <a name="hand-type"></a>手型別

指定是否要將條件約束用於一或兩種類型的操作。 因為這個屬性是一個旗標，所以可以選取兩個選項。

- *一個右手*：條件約束會在一次執行時使用，如果選取的話。
- *兩個右手*：條件約束將在兩個強制操作期間使用（如果選取）。

#### <a name="proximity-type"></a>鄰近型別

指定是否要將條件約束用於接近、遠或兩種類型的操作。 因為這個屬性是一個旗標，所以可以選取兩個選項。

- *Near*：若選取此選項，則會在接近操作期間使用條件約束。
- *目前為止*：如果選取，就會在目前的操作期間使用條件約束。

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint face user">

當這個條件約束附加到物件時，旋轉將會受到限制，因此物件一律會面對使用者。 這對平板或面板很有用。 的屬性如下所示 `FaceUserConstraint` ：

#### <a name="face-away"></a>臉部離開

若為 true，則物件會離開使用者。

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="constraintt fixed distance">

這個條件約束會修正操作物件與操作啟動時的另一個物件轉換之間的距離。 這適用于將操作物件的距離修正至 head 轉換的行為。 的屬性如下所示 `FixedDistanceConstraint` ：

#### <a name="constraint-transform"></a>條件約束轉換

這是操作物件將會有固定距離的另一個轉換。 預設為相機轉換。

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed rotation to user">

此條件約束會修正使用者與操作中物件之間的相對旋轉。 這對平板或面板很有用，因為它可確保操作物件一律會顯示相同的臉部給使用者，如同操作開始時一樣。 沒有 `FixedRotationToUserConstraint` 任何唯一的屬性。

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to world">

此條件約束可修正操作物件在操作時的全域旋轉。 如果不應該透過操作來給予任何旋轉，這項功能就很有用。 沒有 `FixedRotationToWorldConstraint` 任何唯一的屬性：

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent Size">

當這個條件約束附加到物件時，無論物件與使用者之間的距離為何，它都會維持與使用者相同的明顯大小 (也就是，它所占的使用者欄位的比例) 。 這可以用來確保在操作時，平板或文字面板仍可讀取。 沒有 `MaintainApparentSizeConstraint` 任何唯一的屬性：

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

這個條件約束可以用來修正可以移動操作物件的座標軸。 當您在平面表面或線條上操作物件時，這會很有用。 的屬性如下所示 `MoveAxisConstraint` ：

#### <a name="constraint-on-movement"></a>移動時的條件約束

指定要防止移動的座標軸。 依預設，這些軸會是全域的，而不是本機，但可在下方變更。 因為此屬性是旗標，所以可以選取任何數目的選項。

- *X 軸*：如果選取，沿著 X 軸移動會受到限制。
- *Y 軸*：如果選取，沿著 y 軸的移動會受到限制。
- *Z 軸*：如果選取，沿著 Z 軸的移動會受到限制。

#### <a name="use-local-space-for-constraint"></a>使用本機空間進行條件約束

會限制操作物件的本機轉換軸（如果為 true）。 預設為 False。

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

這個條件約束可以用來修正哪些軸可以旋轉可操作的物件。 這有助於讓操作物件保持垂直，但仍允許 y 軸旋轉（例如）。 的屬性如下所示 `RotationAxisConstraint` ：

#### <a name="constraint-on-rotation"></a>旋轉的條件約束

指定要防止旋轉的座標軸。 依預設，這些軸會是全域的，而不是本機，但可在下方變更。 因為此屬性是旗標，所以可以選取任何數目的選項。

- *Y 軸*：如有選取，y 軸的旋轉會受到限制。
- *Z 軸*：若已選取，則會限制 Z 軸的旋轉。
- *X 軸*：若已選取，則會限制 X 軸的旋轉。

#### <a name="use-local-space-for-constraint"></a>使用本機空間進行條件約束

會限制操作物件的本機轉換軸（如果為 true）。 預設為 False。

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="MinMax Scale">

這個條件約束允許為操作物件的小數位數設定最小值和最大值。 這有助於防止使用者調整太小或太大的物件。 的屬性如下所示 `MinMaxScaleConstraint` ：

#### <a name="scale-minimum"></a>最小規模

操作期間的最小縮放值。

#### <a name="scale-maximum"></a>調整最大值

操作期間的最大縮放值。

#### <a name="relative-to-initial-state"></a>相對於初始狀態

若為 true，則會將上述值轉譯為相對於物件初始縮放比例的值。 否則，它們會被視為絕對規模值。

## <a name="physics-and-collisions"></a>物理與衝突

將 rigidbody 元件新增至與物件操作工具相同的物件，即可啟用物理行為。 這並不只可讓您設定上述的 [發行行為](#release-behavior) ，也會啟用衝突。 如果沒有 rigidbody 元件，則在操作期間，衝突的運作方式不正確：

- 操作物件和靜態碰撞程式之間的衝突 (也就是具有碰撞程式但沒有 rigidbody) 的物件無法運作，操作的物件會直接透過靜態碰撞碰撞來傳遞，而不會受到影響。
- 操作物件與 rigidbody 之間的衝突 (例如 具有碰撞器和 rigidbody 的物件) 會導致 rigidbody 有碰撞回應，但回應是跳動和非自然。 在操作物件上也沒有衝突回應。

新增 rigidbody 時，衝突應該會正常運作。

### <a name="without-rigidbody"></a>沒有 rigidbody

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>使用 rigidbody

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">
