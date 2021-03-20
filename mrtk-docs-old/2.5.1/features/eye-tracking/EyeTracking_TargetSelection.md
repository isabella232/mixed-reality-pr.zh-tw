---
title: EyeTracking_TargetSelection
description: 如何在 MRTK 中存取眼睛資料和眼睛的特定事件以選取目標
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: a0131c882ee1677cfb2404208cfe8abb28a3c799
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684901"
---
# <a name="eye-supported-target-selection"></a>目視支援的目標選取範圍

![MRTK 目標選取](../images/eye-tracking/mrtk_et_targetselect.png)

此頁面討論存取眼睛資料的不同選項，以及在 MRTK 中選取目標的眼睛特定事件。 目視追蹤可讓您快速輕鬆地選擇目標，並使用與使用者所查看的內容有關的資訊組合，例如「 _手追蹤_ 」和「 _語音命令_」：

- & 說「 _Select_ 」 (預設的語音命令) 
- & _說 (_ 自訂語音命令的「分裂」或「 _Pop_ 」) 
- 查看 & 藍牙按鈕
- & 縮小 (，也就是將您的手放在最前面，並將您的 thumb 和索引指標結合在一起) 
  - 請注意，若要這樣做，必須 [停用光片](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray)

若要使用眼睛選取全像攝影內容，有幾個選項可供選擇：

[**1. 使用主要焦點指標：**](#1-use-generic-focus-and-pointer-handlers)

這可以被視為您優先的資料指標。
根據預設，如果手中的手中，這會是手中的光線。
如果沒有手中，則優先順序指標會是 head 或眼睛。
因此，請注意，如果使用了手的光線，根據目前的設計 head 或眼睛會隱藏為游標輸入。

例如：

使用者想要選取一個遙遠的全像全像全公司。
如果您是開發人員，您想要提供彈性的解決方案，讓使用者能夠在各種情況下達成這項工作：

- 往上移至按鈕並進行
- 從距離查看並說出「選取」
- 使用手光來鎖定按鈕，並在此情況下執行縮小時，最具彈性的解決方案是使用主要焦點處理常式，因為當目前優先排列的主要焦點指標觸發事件時，它會通知您。 請注意，如果已啟用 [手片]，則會在一開始觀看時立即停用 head 或眼睛的視覺焦點指標。

> [!IMPORTANT]
> 請注意，如果已啟用 [手片]，則會在一開始觀看時立即停用 head 或眼睛的視覺焦點指標。 如果您想要支援「 [_外觀和_ 縮小」的互動，您必須停用手光](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray)。 在我們的眼睛追蹤範例場景中，我們停用了光線，以允許使用眼睛 + 手運動展示更豐富的互動-請參閱，以瞭解 [支援的視覺定位](EyeTracking_Positioning.md)。

[**2. 同時使用眼睛焦點和手光線：**](#2-independent-eye-gaze-specific-eyetrackingtarget)

在某些情況下，您可能會想要更明確地瞭解哪些類型的焦點指標可觸發特定事件，並允許同時使用多個互動技巧。

例如：在您的應用程式中，使用者可以使用最多的光線來操作一些全像的機械設定，例如，抓住並保存一些遠處的全像攝影引擎零件，然後將它們放在原處。 當您這樣做時，使用者必須經過一些指示，並藉由標示一些核取方塊來記錄她/他的進度。 如果使用者有她/他的手 _不忙碌_，則 instinctual 只需觸碰該核取方塊，或使用手光來選取它即可。 不過，如果使用者有她/他的員工忙，就像在我們的案例中保存一些全像攝影引擎部分一樣，您想要讓使用者使用其眼睛來順暢地滾動指示，並只查看一個核取方塊，然後說「檢查！」。

若要啟用此功能，您必須使用獨立于核心 MRTK FocusHandlers 的眼睛特定 EyeTrackingTarget 腳本，並將于下方討論。

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. 使用泛型焦點和指標處理常式

如果已正確設定眼睛追蹤 (請參閱 [基本 MRTK 設定以使用眼睛追蹤](EyeTracking_BasicSetup.md)) ，讓使用者可以使用其眼睛來選取全像輸入一樣的其他焦點輸入 (例如，頭部注視或手形光線) 。這項功能可讓您根據使用者的需求，在 MRTK 輸入指標設定檔中定義主要焦點類型，並讓您的程式碼保持不變，以彈性地與您的全像的方式互動。 這可讓您在前端或眼睛之間切換，而不需要變更一行程式碼，也不需要以最多互動的視覺目標取代手光線。

### <a name="focusing-on-a-hologram"></a>專注于全息圖

若要偵測影像的焦點時間，請使用可提供您兩個介面成員的 _' IMixedRealityFocusHandler '_ 介面： _OnFocusEnter_ 和 _OnFocusExit_。

以下是 [ColorTap](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) 的簡單範例，可在查看時變更全像影像的色彩。

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a>選取焦點的全息圖

若要選取焦點的全息圖，請使用 _PointerHandler_ 來接聽輸入事件，以確認選取專案。
例如，新增 _IMixedRealityPointerHandler_ 會讓它們對簡單指標輸入做出回應。
_IMixedRealityPointerHandler_ 介面需要執行下列三個介面成員： _OnPointerUp_、 _OnPointerDown_ 和 _OnPointerClicked_。

在下列範例中，我們會藉由查看、捏合或說「選取」來變更全像影像的色彩。
觸發事件的必要動作是透過讓 `eventData.MixedRealityInputAction == selectAction` 我們可以在 Unity 編輯器中設定類型的方式來定義，預設為「 `selectAction` 選取」動作。 您可以透過 MRTK [](../Input/InputActions.md)設定配置 _檔_  ->  _輸入_  ->  _輸入動作_，在 MRTK 設定檔中設定可用的 MixedRealityInputActions 類型。

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a>眼睛相關的 BaseEyeFocusHandler

假設眼睛看起來與其他指標輸入非常不同，您可能會想要確定只有當焦點輸入是 _眼睛_ ，而且目前是主要的輸入指標時，才會對其做出反應。
基於這個目的，您會使用 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) 眼睛追蹤特有的，以及衍生自的 [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) 。
如先前所述，只有當眼睛的目標是主要指標 (輸入時才會觸發，也就是不會有作用中的) 的手光線。 如需詳細資訊，請參閱 [如何支援眼睛的眼睛 + 手勢](EyeTracking_EyesAndHands.md)。

以下是 `EyeTrackingDemo-03-Navigation` (資產/MRTK/範例/示範/EyeTracking/場景) 的範例。
在此示範中，有兩個3D 全息圖會根據物件的哪個部分而輪流：如果使用者查看全像影像的左邊，則該部分將會慢慢地移往使用者的前方。
如果查看右邊，那麼該部分將會慢慢移至前方。
這是一種行為，您可能不希望隨時都處於使用中狀態，也可能不會想要讓光線或頭部不小心觸發。
有了 [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) 附加的，GameObject 會在查看時旋轉。

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

如需完整的可用事件清單，請參閱 API 檔 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) ：

- **OnEyeFocusStart：** 當眼睛光線 *開始* 與此目標碰撞器交集時，即會觸發。
- **OnEyeFocusStay：** 當眼睛光線與此目標碰撞器相交 *時* 觸發。
- **OnEyeFocusStop：** 當眼睛光線 *停止* 與此目標碰撞器交集時，即會觸發。
- **OnEyeFocusDwell：** 當眼睛光線與此目標的碰撞器有一段指定的時間的交集時，即會觸發。

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. 獨立紅眼-特定 EyeTrackingTarget

最後，我們會為您提供一個解決方案，讓您能夠將眼睛型輸入與透過腳本的其他焦點指標完全獨立 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。

這有三個 _優點_：

- 您可以確定全像影像只會對使用者的眼睛進行回應。
- 這與目前使用中的主要輸入無關。 因此，您可以一次處理多個輸入，例如，將以手手勢為目標的快速眼睛結合在一起。
- 已設定數個 Unity 事件，讓您可以快速且方便地在 Unity 編輯器中或透過程式碼來處理和重複使用現有的行為。

另外還有一些 _缺點：_

- 個別處理個別輸入的工作更多。
- 沒有簡潔的效能降低：它只支援眼睛目標。 如果眼睛追蹤無法運作，您需要額外的回復。

類似于 _BaseFocusHandler_， _EyeTrackingTarget_ 已準備好一些眼睛相關的 unity 事件，您可以透過 Unity 編輯器輕鬆地透過 unity 編輯器接聽 (請參閱以下範例) 或在程式碼中使用 _AddListener ()_ ：

- OnLookAtStart () 
- WhileLookingAtTarget () 
- OnLookAway () 
- OnDwell () 
- OnSelected () 

在下列範例中，我們將逐步解說一些如何使用 _EyeTrackingTarget_ 的範例。

### <a name="example-1-eye-supported-smart-notifications"></a>範例 #1：眼睛支援的智慧型通知

在 `EyeTrackingDemo-02-TargetSelection` (資產/MRTK/範例/示範/EyeTracking/場景) 中，您可以找到回應眼睛的「 _智慧型用心通知_ 」範例。
這些是可放在場景中的3D 文字方塊，並會在查看以簡化可讀性時，順暢地放大並轉向使用者。 當使用者閱讀通知時，資訊會保持簡潔明瞭。 讀取並離開通知之後，會自動關閉通知並淡出。為了達成上述目的，有幾個一般的行為腳本並不特定于眼睛追蹤，例如：

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

這種方法的優點是，不同的事件可以重複使用相同的腳本。 例如，根據語音命令或按下虛擬按鈕之後，全像影像可能會開始面向使用者。 若要觸發這些事件，您可以直接參考應該在附加至 GameObject 的腳本中執行的方法 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。

在「 _智慧型用心通知_」的範例中，會發生下列情況：

- **OnLookAtStart ()**：通知開始于 .。。
  - *FaceUser。參與：* .。。轉向使用者。
  - *ChangeSize。參與：* .。。 _(增加到指定的最大刻度) 的_ 大小。
  - *BlendOut。參與：* .。。在 _(更微妙的閒置狀態) 之後_，開始 blend。  

- **OnDwell ()**：告知 _BlendOut_ 腳本已充分查看通知。

- **OnLookAway ()**：通知開始于 .。。
  - *FaceUser：* .。。回到其原始方向。
  - *ChangeSize：* .。。減少回其原始大小。
  - *BlendOut：* .。。開始 blend-如果已觸發 _OnDwell ()_ ，請將其全部混合出來，或回到其閒置狀態。

**設計考慮：** 您可以在這裡輕鬆地調整這些行為的速度，以避免因使用者的眼睛太快而迅速地回應使用者的眼睛，而導致不適感。
否則，這可能很快就會變得非常困難。

<img src="../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Eye Tracking Target">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>範例 #2：在查看全像全像的寶物時，會慢慢旋轉

就像範例 #1 一樣，我們可以輕鬆地在 `EyeTrackingDemo-02-TargetSelection` (資產/MRTK/範例/示範/EyeTracking/場景)  (場景中，為我們的全像是在查看時，以較高的) 旋轉範例為例。 您只需要在 _EyeTrackingTarget_ 的 _WhileLookingAtTarget ()_ 事件中觸發全像寶物的旋轉。 以下是更多詳細資料：

1. 建立泛型腳本，其中包含公開函式來旋轉其所連接的 GameObject。 以下是來自 _RotateWithConstSpeedDir_ 的範例，我們可以從 Unity 編輯器調整旋轉方向和速度。

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. 將 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 腳本新增至您的目標 GameObject，並在 UnityEvent 觸發程式中參考 _RotateTarget ()_ 函式，如下列螢幕擷取畫面所示：

    ![EyeTrackingTarget 範例](../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>範例 #3：將這些 gem 稱為 _多重強制回應的目標選擇_

在先前的範例中，我們顯示了偵測目標是否有多麼容易，以及如何觸發對該目標的反應。 接下來，讓我們使用的 _OnSelected ()_ 事件來讓 gem 爆炸 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。 有趣的部分是 *如何* 觸發選取專案。 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)可讓您快速指派不同的方法來叫用選取專案：

- 縮小 _手勢_：將 [選取動作] 設定為 [選取] 時，會使用預設手勢來觸發選取專案。
這表示使用者可以直接提高其手，並將其 thumb 和索引手指放在一起，以確認選取專案。

- 說「 _select_」：使用預設的語音命令「 _選取_ 」來選取全息圖。

- 說 _「_ 分裂」或「 _Pop_」：若要使用自訂語音命令，您需要遵循兩個步驟：
    1. 設定自訂動作，例如 _"DestroyTarget"_
        - 流覽至 _MRTK-> 輸入-> 輸入動作_
        - 按一下 [新增動作]

    2. 設定會觸發此動作的語音命令 _，例如「分裂」或_「 _Pop_ 」
        - 流覽至 _MRTK-> 輸入-> 語音_
        - 按一下 [新增語音命令]
            - 建立您剛才建立之動作的關聯
            - 指派 _KeyCode_ 以允許透過按下按鈕來觸發動作

![語音命令 EyeTrackingTarget 範例](../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

當 gem 被選取時，它會分裂，並使音效消失。 這是由腳本處理 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) 。 您有兩個選擇：

- **在 Unity 編輯器中：** 您可以直接將附加至每個 gem 範本的腳本連結到 Unity 編輯器中的 OnSelected () Unity 事件。
- **在程式碼中：** 如果您不想要拖放 Gameobject，您也可以直接將事件接聽程式新增至您的腳本。  
以下是我們在腳本中執行此動作的範例 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) ：

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>範例 #4：一起使用手片光線和眼睛的輸入

手光線優先于 head 和眼睛的目標。 這表示，如果已啟用「手片」，則手中的時刻會顯示為主要指標。
不過，在某些情況下，您可能會想要使用手片，同時又偵測到使用者是否正在查看特定的全像。 很容易！ 基本上，您需要兩個步驟：

**1. 啟用手形：** 若要啟用手光線，請移至 _Mixed Reality 工具組-> 輸入 > 指標_。
在 _EyeTrackingDemo-00-RootScene_ 中，混合現實工具組會針對所有的眼睛追蹤示範場景設定一次，您應該會看到 _EyeTrackingDemoPointerProfile_。
您可以從頭開始建立新的 _輸入設定檔_ ，或調整目前的眼睛追蹤之一：

- **從頭開始：** 在 [ _指標_ ] 索引標籤中，從內容功能表中選取 [ _DefaultMixedRealityInputPointerProfile_ ]。
這是預設的指標設定檔，已啟用「手」光線！
若要變更預設資料指標 (不透明的白點) ，只要複製設定檔並建立您自己的自訂指標設定檔即可。
然後以 _EyeGazeCursor_ 的 _指標預製專案_ 底下的 _DefaultCursor_ 取代。  
- **根據現有的 _EyeTrackingDemoPointerProfile_：** 按兩下 [ _EyeTrackingDemoPointerProfile_ ]，然後在 [ _指標選項_] 底下新增下列專案：
  - **控制器類型：** 「明確的手」、「Windows Mixed Reality」
  - **Handedness：** 任何
  - **指標預製專案：** DefaultControllerPointer

**2. 偵測是否已查看全像影像：** 使用 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 腳本來偵測是否已查看全像上面所述的全像影像。 您也可以看一下 `FollowEyeGaze` 靈感的範例腳本，因為這會在您的眼睛下顯示一個全息圖 (例如，游標) 是否啟用了手片。

現在，當您開始眼睛追蹤示範場景時，您應該會看到來自您手的光線。
例如，在眼睛追蹤目標選取示範中，半透明圓形仍在您的眼睛下，而 gem 則會回應是否有查看它們，而最上層場景功能表按鈕則改用主要輸入指標 (您的手) 。

---
[回到「MixedRealityToolkit 中的眼睛追蹤」](EyeTracking_Main.md)
