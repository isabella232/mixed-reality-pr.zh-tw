---
title: 條件約束管理員
description: MRTK 中的條件約束管理員總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: f32f7321ec30f337e03d006f47fa92639796a74156483917331304811ea86a45
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198478"
---
# <a name="constraint-manager"></a>條件約束管理員

條件約束管理員可讓您將一組條件約束元件套用至轉換。 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint)附加至遊戲物件的類型元件可以納入考慮。
根據預設，條件約束管理員會自動收集所有附加至遊戲物件的 [條件約束元件](#transform-constraints) ，並將其套用至處理的轉換。
不過，使用者可以選擇手動設定套用的條件約束清單，而只允許套用附加條件約束的子集。

目前，下列 MRTK UX 元素支援條件約束管理員：

- [界限控制項](bounds-control.md)
- [物件操作工具](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>偵測器屬性和欄位

條件約束管理員可在兩種模式中運作：

- 自動條件約束選取
- 手動條件約束選取

### <a name="auto-constraint-selection"></a>自動條件約束選取

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

[條件約束管理員] 的預設模式是 [自動條件約束選取]，將會提供所有附加條件約束元件的清單，以及 [ [移至按鈕](#go-to-component) ] 和 [ [新增條件約束] 按鈕](#add-constraint-to-game-object)。

#### <a name="add-constraint-to-game-object"></a>將條件約束新增至遊戲物件

此按鈕可讓條件約束元件直接從條件約束管理員偵測器加入。 專案中應該會顯示專案中的所有條件約束類型。 如需詳細資訊，請參閱 [轉換條件約束](#transform-constraints) 。

#### <a name="go-to-component"></a>移至元件

在此物件上找到的所有條件約束，都會在這裡列出，並顯示 [ *移至元件* ] 按鈕。 此按鈕會讓偵測器滾動至選取的條件約束元件，以便進行設定。

### <a name="manual-constraint-selection"></a>手動條件約束選取

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

如果條件約束管理員設定為手動模式，則只會處理條件約束清單中連結的條件約束，並將其套用至轉換。 顯示的清單只會顯示使用者選取的條件約束，以及移 [至按鈕](#go-to-component) 或選項以移除或新增專案。
當第一次啟用手動模式時，條件約束管理員會將所有可用的元件填入清單，做為選取附加條件約束元件的起點。

### <a name="remove-entry"></a>移除專案

這會從手動選取的清單中移除專案。 請注意，這個選項不會從遊戲物件中移除條件約束元件。 條件約束元件一律需要手動移除，以確保不會意外中斷任何參考此元件的其他元件。

### <a name="add-entry"></a>新增專案

[新增專案] 會開啟下拉式清單，顯示尚未在手動清單中的所有可用條件約束元件。 按一下該元件將會新增至手動條件約束選取專案的任何專案。

### <a name="add-new-constraint"></a>新增條件約束

此選項會將所選類型的元件新增至遊戲物件，並將新建立的條件約束元件加入至手動條件約束清單。

## <a name="transform-constraints"></a>轉換條件約束

條件約束可以用來限制操作的方式。 例如，有些應用程式可能需要輪替，但物件也需要保持垂直。 在此情況下，您 `RotationAxisConstraint` 可以將加入至物件，並用來將旋轉限制為 y 軸旋轉。 MRTK 提供許多條件約束，如下所述。

您也可以定義新的條件約束，並使用它們來建立某些應用程式可能需要的獨特操作行為。 若要這樣做，請建立一個繼承自 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 的腳本，並執行抽象 `ConstraintType` 屬性和抽象 `ApplyConstraint` 方法。 將新的條件約束加入至物件時，它應該會以定義的方式來限制操作。 這個新的條件約束也應該顯示在 [條件約束管理員 [自動選取](#auto-constraint-selection) ] 或 [以手動模式 [加入專案](#add-entry) ] 下拉式清單中。

MRTK 提供的所有條件約束都會共用下列屬性：

#### <a name="hand-type"></a>手型別

指定是否要將條件約束用於一或兩種類型的操作。 因為這個屬性是一個旗標，所以可以選取兩個選項。

- *一個右手*：條件約束會在一次執行時使用，如果選取的話。
- *兩個右手*：條件約束將在兩個強制操作期間使用（如果選取）。

#### <a name="proximity-type"></a>鄰近型別

指定是否要將條件約束用於接近、遠或兩種類型的操作。 因為這個屬性是一個旗標，所以可以選取兩個選項。

- *Near*：若選取此選項，則會在接近操作期間使用條件約束。
- *目前為止*：如果選取，就會在目前的操作期間使用條件約束。

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

當這個條件約束附加到物件時，旋轉將會受到限制，因此物件一律會面對使用者。 這對平板或面板很有用。 的屬性如下所示 `FaceUserConstraint` ：

#### <a name="face-away"></a>臉部離開

若為 true，則物件會離開使用者。

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

這個條件約束會修正操作物件與操作啟動時的另一個物件轉換之間的距離。 這適用于將操作物件的距離修正至 head 轉換的行為。 的屬性如下所示 `FixedDistanceConstraint` ：

#### <a name="constraint-transform"></a>條件約束轉換

這是操作物件將會有固定距離的另一個轉換。 預設為相機轉換。

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

此條件約束會修正使用者與操作中物件之間的相對旋轉。 這對平板或面板很有用，因為它可確保操作物件一律會顯示相同的臉部給使用者，如同操作開始時一樣。 沒有 `FixedRotationToUserConstraint` 任何唯一的屬性。

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

此條件約束可修正操作物件在操作時的全域旋轉。 如果不應該透過操作來給予任何旋轉，這項功能就很有用。 沒有 `FixedRotationToWorldConstraint` 任何唯一的屬性：

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

當這個條件約束附加到物件時，無論物件與使用者之間的距離為何，它都會維持與使用者相同的明顯大小 (也就是，它所占的使用者欄位的比例) 。 這可以用來確保在操作時，平板或文字面板仍可讀取。 沒有 `MaintainApparentSizeConstraint` 任何唯一的屬性：

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

這個條件約束可以用來修正可以移動操作物件的座標軸。 當您在平面表面或線條上操作物件時，這會很有用。 的屬性如下所示 `MoveAxisConstraint` ：

#### <a name="constraint-on-movement"></a>移動時的條件約束

指定要防止移動的座標軸。 根據預設，這些軸會是全域的，而不是本機，但可在下方變更。 因為此屬性是旗標，所以可以選取任何數目的選項。

- *X 軸*：如果選取，沿著 X 軸移動會受到限制。
- *Y 軸*：如果選取，沿著 y 軸的移動會受到限制。
- *Z 軸*：如果選取，沿著 Z 軸的移動會受到限制。

#### <a name="use-local-space-for-constraint"></a>使用本機空間進行條件約束

會限制操作物件的本機轉換軸（如果為 true）。 預設為 False。

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

這個條件約束可以用來修正哪些軸可以旋轉可操作的物件。 這有助於讓操作物件保持垂直，但仍允許 y 軸旋轉（例如）。 的屬性如下所示 `RotationAxisConstraint` ：

#### <a name="constraint-on-rotation"></a>旋轉的條件約束

指定要防止旋轉的座標軸。 根據預設，這些軸會是全域的，而不是本機，但可在下方變更。 因為此屬性是旗標，所以可以選取任何數目的選項。

- *Y 軸*：如有選取，y 軸的旋轉會受到限制。
- *Z 軸*：若已選取，則會限制 Z 軸的旋轉。
- *X 軸*：若已選取，則會限制 X 軸的旋轉。

#### <a name="use-local-space-for-constraint"></a>使用本機空間進行條件約束

會限制操作物件的本機轉換軸（如果為 true）。 預設為 False。

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

這個條件約束允許為操作物件的小數位數設定最小值和最大值。 這有助於防止使用者調整太小或太大的物件。 的屬性如下所示 `MinMaxScaleConstraint` ：

#### <a name="scale-minimum"></a>最小規模

操作期間的最小縮放值。

#### <a name="scale-maximum"></a>調整最大值

操作期間的最大縮放值。

#### <a name="relative-to-initial-state"></a>相對於初始狀態

若為 true，則會將上述值轉譯為相對於物件初始縮放比例的值。 否則，它們會被視為絕對規模值。
