---
title: HandCoach
description: 手動指導的說明和範例。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: a145b449842c7e2ff9dacaf3c2bed56594d6ff72
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690578"
---
# <a name="hand-coach"></a>手勢指導

![主要指導](../../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

手上的教練是3D 模型化的手，當系統未偵測到使用者的手時，就會觸發此手。 這會實作為「教學」元件，可在未教授手勢時協助引導使用者。 如果使用者尚未針對某段時間完成指定的手勢，則手將會有延遲的迴圈。 手指導可用來代表按下按鈕或挑選全像影像。

目前的互動模型代表各式各樣的手勢控制項，例如滾動、遠選和近端點擊。 以下是現有的手動指導範例的完整清單：

- 近端點擊-用於按鈕或關閉互動物件
- 全選–用於遠離物件
- 移動–用來在空間中移動全息圖
- 旋轉–用來顯示如何旋轉全像影像或物件
- 調整-用來顯示如何操作大容量比較或更小的影像
- 手形-用來啟動 UI 開始面板或手形功能表
- 手掌–用於現成體驗中的 hummingbird 時間。 另一個建議是顯示 UI 啟動面板
- 捲軸-用於滾動清單或長檔

## <a name="example-scene"></a>範例場景

您可以在以下的 **HandCoachExample** 場景中找到範例： [MixedRealityToolkit. 範例/實驗/HandCoach/場景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Experimental/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>手上立體資產

您可以在下列檔中找到資產： [MixedRealityToolkit. SDK/實驗/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/Experimental/HandCoach)

## <a name="quality"></a>品質

如果您注意到 skinned 網格上的扭曲，您需要確定您的專案使用適當的接點數量。
移至 Unity 的 [編輯] > 專案設定 > 品質 > 其他 > Blend 加權。 確定已選取「4個骨骼」以查看平滑接點。
![專案設定](../../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>指令碼

### <a name="interaction-hint"></a>互動提示

`InteractionHint.cs`腳本提供用於觸發動畫的包裝函式功能，並讓您的工作機組淡化。

#### <a name="how-to-set-up-an-interaction-hint"></a>如何設定互動提示

若要設定互動提示，建議使用提供的 prefabs "StaticHandCoachRoot_L. 預製專案" 和 "StaticHandCoachRoot_R. 預製專案"。 此預製專案包含 InteractionHint 腳本和手邊的設備，以及適當的階層，以確保提供的提示動畫能如預期運作。
否則，您必須使用 animator，將腳本放在 gameObject 一個上層的父層級上。

#### <a name="inspector-properties"></a>偵測器屬性

- **HideIfHandTracked** 此布林值指定在追蹤使用者的手時，是否應使用「手動追蹤」狀態來隱藏視覺效果。 如果設定為 false，則只會使用腳本屬性 "customShouldHideVisuals" 來判斷是否要隱藏提示。

- **MinDelay** 這個屬性會指定顯示視覺效果的最小延遲。 根據預設，如果未追蹤使用者的手中，則會在這幾秒後出現該手的視覺效果。

- **MaxDelay** 這個屬性會指定顯示視覺效果的最大延遲。 根據預設，即使正在追蹤使用者的手中，該手的視覺效果也會出現在這幾秒之後。

- **UseMaxTimer** 如果這個布林值設定為 false，它會停用最大計時器，並只允許在使用者的手離開時顯示手形提示，或自訂條件傳回 false。

- **重複** 這個屬性會控制當最小或最大計時器超過時，提示動畫的播放次數。 提示接著會隱藏並等候延遲。

- **AutoActivate** 當這個布林值設定為 true 時，當腳本的 GameObject 在使用中，且腳本已啟用時，提示會自動執行計時器邏輯。 如果您想要透過程式碼手動控制提示外觀和消失，則應該將此設定為 false。

- **AnimationState** 當提示為作用中時，應播放之動畫狀態的名稱。 這必須在 OnEnable 期間呼叫 StartHintLoop () 函式之前設定 (如果) 檢查 AutoActivate。

#### <a name="controlling-interactionhint-via-script"></a>透過腳本控制 InteractionHint

- **StartHintLoop** 如果 AutoActivate 旗標設定為 true，則此函式會啟動顯示/隱藏迴圈，否則會啟動 OnEnable。
- **StopHintLoop** 如果目前沒有播放，此函式會呼叫淡出動畫狀態，然後停用顯示/隱藏迴圈，並將階層中非使用中的工作區設定為非作用中。
- **AnimationState** 這個字串會決定迴圈期間要播放的動畫狀態。 您可以變更此字串來變更要播放的狀態，但是在呼叫 StopHintLoop 之後必須這樣做，而且您必須在變更狀態之後再次呼叫 StartHintLoop。
- **CustomShouldHideVisuals** 您可以使用自己的函式來設定此設定，當您想要隱藏手的視覺效果時，應該會傳回 true (請特別注意 MinMaxTimer，尤其是 max 參數) 

#### <a name="custom-animation-considerations"></a>自訂動畫的考慮

淡化的預設值為0.5 秒，因此為了與 rig 一起使用而建立的任何自訂動畫，都應為任何要傳達的有意義資訊的1.5 秒

您可以藉由變更第二個主要畫面格的時間戳記來設定淡化長度，來調整所提供的預設淡入和淡出狀態、Fade_In 和 Fade_Out。

Animator 和腳本的設定方式應該盡可能簡化安裝程式。 若要加入新的動畫狀態，只需匯入您的 fbx，確定動畫名稱是以相異名稱設定，然後將該動畫拖曳至 animator 中。

### <a name="movetotarget"></a>MoveToTarget

MoveToTarget .cs 腳本提供了一段時間，將手提示從追蹤位置移至目標位置的功能。

#### <a name="how-to-set-up-movetotarget"></a>如何設定 MoveToTarget

提供的 prefabs "MovingHandCoachRoot_L. 預製專案" 和 "MovingHandCoachRoot_R. 預製專案" 包含其階層中的 MoveToTarget。 如果您想要在自己的安裝程式上使用此腳本，您必須將它放在包含您的 rig Animator 的根 gameobject。

#### <a name="inspector-properties"></a>偵測器屬性

- **TrackingObject** 使用您想要讓 rig 在開始其動作之前所要遵循的物件來設定此設定。 建議您建立空白的 GameObject，並將它移至特定位置，以協助您找出追蹤。
- **TargetObject** 使用您想要讓 rig 移至其移動期間的物件來設定此設定。 建議您建立空白的 GameObject，並將它移至特定位置，以協助您找出追蹤。
- **RootObject** 將此設定為追蹤與目標物件之間的共用父系，以便能夠正確計算相對位置。 包含的預製專案在其階層中有追蹤和目標物件，但您可以將目標物件設定為預製專案以外的 gameObject，並將根物件變更為共用父系。
- **持續時間** 從 TrackingObject 到 TargetObject （以秒為單位）進行移動所需的 (時間長度（以) 秒為單位）。
- **TargetOffset** 可調式位移，可讓 GameObject 到達正確的目標位置。 如果您的動畫在動畫期間包含位置位移，這就很有用。
- **AnimationCurve** 這會預設為線性曲線，但您可以在啟動和停止移動路徑時，改變曲線以提供緩時/放大。

#### <a name="controlling-movetotarget-via-script"></a>透過腳本控制 MoveToTarget

在您的自訂腳本中，進行下列 () ，並在您想要讓設備在 TrackingObject 之後進行呼叫，然後在您想要讓設備的 MoveToTargetPosition 開始移動到 TargetObject 時，呼叫 () 。

#### <a name="controlling-movetotarget-via-animations"></a>透過動畫控制 MoveToTarget

在需要移動的動畫中，設定兩個事件：一個是呼叫後面的 () ，另一個則是呼叫 MoveToTargetPosition () 。 您應該在第一個主要畫面格上設定下列各個，因為它會讓設備裝備符合您的 TrackingObject。 MoveToTargetPosition 應該設定在您要讓 rig 開始移至目標的主要畫面上。 這是在提供的 prefabs 中使用腳本功能的方式。

### <a name="rotatearoundpoint"></a>RotateAroundPoint

RotateAroundPoint 可提供在一段時間內旋轉旋轉點提示的功能。

#### <a name="how-to-set-up-rotatearoundpoint"></a>如何設定 RotateAroundPoint

提供的 prefabs "RotatingHandCoachRoot_L. 預製專案" 和 "RotatingHandCoachRoot_R. 預製專案" 包含其階層中的 RotateAroundPoint。 如果您想要在自己的安裝程式上使用此腳本，您必須將它放在包含您的 rig Animator 的根 gameobject。

#### <a name="inspector-properties"></a>偵測器屬性

- **CenteredParent** 使用您想要讓 rig 進行資料透視的父物件來設定此設定。
- **InverseParent** 將此設定為父代，以將反向旋轉至 centeredParent，以保持方向相同。 一般來說，這會是具有 InteractionHint 腳本的父物件。
- **PivotPosition** 將此設定為您希望提示開始移動的時間點。
- **持續時間** 以秒為單位來旋轉 CenteredParent 所需的 (時間量) （以秒為單位）。
- **AnimationCurve** 這會預設為線性曲線，但您可以在啟動和停止移動路徑時，改變曲線以提供緩時/放大。
- **RotationVector** 沿著每個軸旋轉的度數。

#### <a name="controlling-rotatearoundpoint-via-script"></a>透過腳本控制 RotateAroundPoint

在您的自訂腳本中，當您想要讓設備在 CenteredParent 周圍開始輪替時，請呼叫 RotateToTarget () 。 當您想要重設為原始 PivotPosition 的位置時，請呼叫 ResetAndDeterminePivot () 。

#### <a name="controlling-rotatearoundpoint-via-animations"></a>透過動畫控制 RotateAroundPoint

在需要移動的動畫中，設定兩個事件：一個是呼叫 ResetAndDeterminePivot () ，另一個呼叫 RotateToTarget () 。 ResetAndDeterminePivot 應該在第一個主要畫面格上設定，因為它會讓裝備的設備重設為 PivotPosition。 RotateToTarget 應該設定在您要讓 rig 開始在 CenteredParent 周圍旋轉的主要畫面上。 這是在提供的 prefabs 中使用腳本功能的方式。
