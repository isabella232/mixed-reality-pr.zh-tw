---
title: ObjectManipulator
description: 如何在 MRTK 中使用物件操作工具
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、物件操作、
ms.openlocfilehash: e5d54e2d4972ddd930efbe7e1006579531cb1722
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779894"
---
# <a name="object-manipulator"></a>物件操作工具

![物件操作工具](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ObjectManipulator* 是操作行為的新元件，先前在 *ManipulationHandler* 中找到。 物件操作工具可進行許多改進和簡化。 此元件取代了將被取代的操作處理常式。

*ObjectManipulator* 腳本會使用一或兩個手來讓物件可移動、可擴充及 rotatable。 物件操作工具可以設定為控制物件將如何回應各種輸入。 腳本應可搭配大部分的互動形式使用，例如 HoloLens 2 的有向的手勢、HoloLens 2 手片片、HoloLens 1 注視和手勢，以及沉浸式耳機移動控制器輸入。

## <a name="how-to-use-the-object-manipulator"></a>如何使用物件操作工具

若要使用物件操作工具，請先將 `ObjectManipulator` 腳本元件加入至 GameObject。 請務必同時將碰撞新增至物件，以符合其 grabbable 界限。

若要讓物件回應接近明確的手輸入，請新增 `NearInteractionGrabbable` 腳本。

將 rigidbody 元件新增至物件，即可為物件操作工具啟用物理行為。 新增此元件所啟用的物理行為會在 [*物理和衝突*](#physics-and-collisions)中更詳細地討論。

如此一來，就可以將 [操作條件約束元件](constraint-manager.md#transform-constraints) 加入至物件，以限制操作。 這些是使用操作的特殊元件，並以某種方式變更操作行為。

![操作處理常式](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>偵測器屬性和欄位

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

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

![操作處理常式](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>條件約束

#### <a name="enable-constraints"></a>啟用條件約束

這種設定會啟用連結的 [條件約束管理員](constraint-manager.md)。 轉換變更將由註冊至所選 [條件約束管理員](constraint-manager.md)的條件約束處理。

#### <a name="constraint-manager"></a>條件約束管理員

下拉式清單可讓您選取任何附加的 [條件約束管理員](constraint-manager.md)。 物件操作工具可確保所有時間都有附加的 [條件約束管理員](constraint-manager.md) 。
請注意，相同類型的多個元件會顯示在 unity 中的相同名稱下。 為了讓您可以更輕鬆地分辨相同物件上的多個條件約束管理員，可用的選項會顯示所選條件約束管理員設定的提示 (手動或自動條件約束選取) 。

#### <a name="go-to-component"></a>移至元件

條件約束管理員選項會隨附 [ *移至元件* ] 按鈕。 此按鈕會讓偵測器滾動至選取的元件，以便進行設定。

### <a name="physics"></a>物理特性

只有當物件具有 RigidBody 元件時，才會顯示此區段中的設定。

#### <a name="release-behavior"></a>發行行為

指定操作物件在發行時應保留的實體屬性。 因為這個屬性是一個旗標，所以可以選取兩個選項。

- *保持速度*：當物件被選取時，如果選取此選項，則會保留其線性速度。
- *保持角度*：當物件被選取時，如果已選取此選項，則會維持其角度的速度。

#### <a name="use-forces-for-near-manipulation"></a>使用強制進行接近操作

執行接近操作時，是否使用物理強制來移動物件。 將此設定為 *false* 會讓物件感覺更直接連線至使用者手。 將此設定為 *true* 將會接受物件的大量和慣性，但可能會覺得物件是透過彈簧連接的。 預設值為 *false*。

### <a name="smoothing"></a>平滑處理

#### <a name="smoothing-far"></a>平滑程度

是否針對大部分的互動啟用畫面播放速率獨立平滑處理。 目前預設會啟用凹凸貼圖。

#### <a name="smoothing-near"></a>近乎平滑

是否針對近乎互動啟用畫面播放速率獨立平滑處理。 預設會停用近乎平滑處理，因為效果可能會被視為「已中斷連線」。

#### <a name="smoothing-active"></a>啟用平滑

已淘汰，將會在未來版本中移除。 應用程式應該使用 SmoothingFar、SmoothingNear 或兩者的組合。

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

## <a name="physics-and-collisions"></a>物理與衝突

將 rigidbody 元件新增至與物件操作工具相同的物件，即可啟用物理行為。 這並不只可讓您設定上述的 [發行行為](#release-behavior) ，也會啟用衝突。 如果沒有 rigidbody 元件，則在操作期間，衝突的運作方式不正確：

- 操作物件和靜態碰撞程式之間的衝突 (也就是具有碰撞程式但沒有 rigidbody) 的物件無法運作，操作的物件會直接透過靜態碰撞碰撞來傳遞，而不會受到影響。
- 操作物件與 rigidbody 之間的衝突 (例如 具有碰撞器和 rigidbody 的物件) 會導致 rigidbody 有碰撞回應，但回應是跳動和非自然。 在操作物件上也沒有衝突回應。

新增 rigidbody 時，衝突應該會正常運作。

### <a name="without-rigidbody"></a>沒有 rigidbody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>使用 rigidbody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>彈性 (實驗性) 

透過物件操作工具操作物件時，可以使用彈性。 請注意， [彈性系統](../elastics/elastic-system.md) 仍處於實驗性狀態。 若要啟用彈性，請連結現有的彈性 manager 元件，或透過按鈕建立並連結新的彈性管理員 `Add Elastics Manager` 。

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>另請參閱

- [界限控制項](bounds-control.md)
- [條件約束管理員](constraint-manager.md)
- [遷移視窗](../tools/migration-window.md)
- [彈性系統 (實驗性) ](../elastics/elastic-system.md)
