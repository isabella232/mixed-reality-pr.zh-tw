---
title: README_Interactable
description: MRTK 中的互動腳本元件總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、互動、Events、
ms.openlocfilehash: 7b45181571dfc48fd3defa8847ba9ebe568d73c6
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779608"
---
# <a name="interactable"></a>互動

![互動](Images/Interactable/InteractableExamples.png)

[`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable)元件是一個全功能的容器，可讓任何物件輕鬆地 *互動* 並回應輸入。 互動可作為所有輸入類型的全部捕捉，包括觸控、手寫光線、語音等，以及將這些互動加入 [事件](#events) 和 [視覺主題](visualthemes.md) 回應中。 此元件提供簡單的方式來建立按鈕、變更具有焦點的物件色彩等等。

## <a name="how-to-configure-interactable"></a>如何設定互動

元件允許三個主要的設定區段：

1) [一般輸入設定](#general-input-settings)
1) 以多個 Gameobject 為目標的[視覺主題](VisualThemes.md)
1) [事件處理常式](#events)

### <a name="general-input-settings"></a>一般輸入設定

![一般互動設定](Images/Interactable/InputFeatures_short.png)

**狀態**

*狀態* 是一個 [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 參數，可定義 [互動設定檔](#interactable-profiles) 和 [視覺化主題](VisualThemes.md)的互動階段，例如按下或觀察到。

**DefaultInteractableStates** (資產/MRTK/SDK/FEATURES/UX/互動/州/DefaultInteractableStates. 資產) 隨附于現成的 MRTK，而且是 *互動* 元件的預設參數。

![偵測器中的狀態 ScriptableObject 範例](Images/Interactable/DefaultInteractableStates.png)

*DefaultInteractableStates* 資產包含四種狀態，並利用 [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) 狀態模型執行。

* **預設值**：沒有任何專案發生，這是最隔離的基底狀態。

* **焦點**：物件正在指向。 這是單一狀態，目前未設定任何其他狀態，但會將預設值設為預設值。

* **按**：正在指向物件，且正在按下按鈕或手。 按下狀態會排列預設和焦點。 此狀態也會被設定為實體按下的狀態。

* **已停用**：此按鈕不應該是互動式的，且視覺效果的意見反應會讓使用者知道是否因為某些原因而無法使用這個按鈕。 理論上，停用的狀態可能會包含所有其他狀態，但當啟用時，已停用的狀態就會優先于所有其他狀態。

視清單中的順序而定，會將位值 ( # ) 指派給狀態。

> [!NOTE]
> 通常建議您在建立 *互動* 元件時，利用 **DefaultInteractableStates** (資產/MRTK/SDK/Features/UX/互動/州名/DefaultInteractableStates 資產) 。
>
> 不過，有17種可用來驅動主題的互動狀態，但有些則是由其他元件所驅動。 以下是具有內建功能的清單。
>
> * 造訪：已按一下互動。
> * 切換：按鈕處於切換狀態，或維度索引為奇數。
> * 手勢：已按下手或控制器，且已從原始位置移動。
> * VoiceCommand：用來觸發互動的語音命令。
> * PhysicalTouch：目前偵測到觸控輸入，用於 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 啟用。
> * 抓取：手中目前已抓取物件的界限，用 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 來啟用

**Enabled**

切換互動是否將開始啟用。 這會對應至程式 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 代碼中的。

*互動的* enabled 屬性與透過 GameObject/Component 設定的 enabled 屬性不同 (例如 Advanced.field.setactive 等) 。 停用 GameObject 或 *互動* MonoBehaviour 將會停用類別中的所有專案，包括輸入、視覺主題、事件等等。停用 via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 將會停用大部分的輸入處理，並重設相關的輸入狀態。 不過，此類別仍會執行每個畫面格，並接收將會忽略的輸入事件。 這適用于將互動顯示為已停用狀態，可透過視覺化主題來完成。 其中一個常見的範例是 [提交] 按鈕，等候所有必要的輸入欄位都完成。

**輸入動作**

從 *互動* 元件應該回應的輸入設定或控制器對應設定檔中，選取 [輸入動作](./Input/InputActions.md)。

您可以在程式碼中，透過程式碼來設定這個屬性 [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) 。

**IsGlobal**

若為 true，則會將元件標示為所選 [輸入動作](./Input/InputActions.md)的全域輸入接聽程式。 預設行為是 false，它會將輸入限制為只有這個 *互動* 碰撞/GameObject。

您可以在程式碼中，透過程式碼來設定這個屬性 [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) 。

**語音命令**

[語音命令](./Input/Speech.md)，從 MRTK 語音命令設定檔，用來觸發語音互動的 OnClick 事件。

您可以在程式碼中，透過程式碼來設定這個屬性 [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) 。

**需要焦點**

若為 true，則只有在已有指標的焦點時，voice 命令才會啟用 *互動* 。 如果為 false，則 *互動* 將作為所選語音命令的全域接聽程式。 預設行為是 true，因為多個全域語音接聽程式很難在場景中組織。

您可以在程式碼中，透過程式碼來設定這個屬性 [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) 。

**選取模式**

這個屬性會定義選取邏輯。 當您按一下 *互動* 時，它會逐一查看至下一個 *維度* 層級。 *維度* 類似于排名，並定義輸入以外的狀態 (例如 焦點，按 etc) 。 它們適用于定義切換狀態或與按鈕相關聯的其他多重排名狀態。 目前的維度層級是由追蹤 `Interactable.DimensionIndex` 。

可用的選取模式如下：

* **按鈕**  - *維度*= 1，簡單的可按式 *互動*
* **切換**  - *維度*= 2，*互動* 會 *在* / *關閉* 狀態時交替
* **多重維度**  - *維度*>= 3，每次按一下會增加目前的維度層級 + 1。 適用于定義清單的按鈕狀態等等。

*互動* 也可讓您定義每個 *維度* 的多個主題。 例如，當 *SelectionMode = 切換* 時，可以在 *取消選取**互動* 時套用一個主題，並在 *選取* 元件時套用另一個主題。

您可以在執行時間透過來查詢目前的選取模式 [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) 。 您可以藉由將  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) 屬性設定為符合所需的功能，來在執行時間更新模式。 此外，目前的維度適用于 *切換* 和 *多維度* 模式，可透過來存取 [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) 。

### <a name="interactable-profiles"></a>互動設定檔

*設定檔* 是在 GameObject 和 [視覺化主題](VisualThemes.md)之間建立關聯性的專案。 設定檔會定義當 [狀態變更發生](#general-input-settings)時，主題會操作哪些內容。

主題的運作方式很類似材質。 它們是可編寫腳本的物件，其中包含將根據目前狀態指派給物件的屬性清單。 主題也可以重複使用，並可跨多個 *互動* UX 物件指派。

**損毀時重設**

視覺主題會修改目標 GameObject 上的各種屬性，取決於所選取的主題引擎類別和類型而定。 如果終結互動元件時，在終結時 *重設* 為 true，元件會將所有修改過的屬性從作用中主題重設為其原始值。 否則，當終結時，互動元件會保留任何修改過的屬性。 在後者的情況下，除非由另一個外部元件變更，否則值的最後一個狀態將會保留。 預設為 false。

<img src="Images/Interactable/Profiles_Themes.png" width="450" alt="Profile Themes">

## <a name="events"></a>事件

每個 *互動* 元件都有一個 *OnClick* 事件，此事件會在只選取元件時引發。 不過， *互動* 可以用來偵測除了 *OnClick* 以外的輸入事件。

按一下 [ *新增事件* ] 按鈕，以加入新的事件接收器定義類型。 新增之後，請選取所需的事件種類。

![事件範例](Images/Interactable/Events.png))

有不同類型的事件接收器可回應不同類型的輸入。 MRTK 隨附了下列一組現成的接收者。

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

您可以建立擴充的新類別來建立自訂接收器 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 。

![事件切換接收器範例](Images/Interactable/Event_toggle.png)

*切換事件接收器的範例*

### <a name="interactable-receivers"></a>互動接收者

 元件可讓您在 [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) 來源 *互動* 元件之外定義事件。 *InteractableReceiver* 會接聽由另一個 *互動* 所引發的已篩選事件種類。 如果未直接指派 *互動* 屬性，則 [ *搜尋範圍* ] 屬性會定義 *InteractableReceiver* 接聽事件的方向，此方向本身、父系或子 GameObject。

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) 以類似的方式運作，但符合相符事件的清單。

<img src="Images/Interactable/InteractableReceiver.png" width="450" alt="Interactable receivers">

### <a name="create-custom-events"></a>建立自訂事件

就像 [視覺主題](VisualThemes.md#custom-theme-engines)一樣，可以擴充事件以偵測任何狀態模式或公開功能。

您可以透過兩種主要方式來建立自訂事件：

1) 擴充 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 類別以建立自訂事件，此事件會顯示在事件種類的下拉式清單中。 依預設會提供 Unity 事件，但是可以加入其他 Unity 事件，也可以設定事件來隱藏 Unity 事件。 這項功能可讓設計工具與專案的工程師合作，以建立設計工具可以在編輯器中設定的自訂事件。

1) 擴充 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) 類別以建立可位於 *互動* 或另一個物件上的完全自訂事件元件。 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)會參考 *互動* 來偵測狀態變更。

#### <a name="example-of-extending-receiverbase"></a>擴充的範例 `ReceiverBase`

[`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI)類別會顯示有關 *互動* 的狀態資訊，以及如何建立自訂事件接收器的範例。

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

建立自訂事件接收器時，下列方法可用於覆寫/執行。 [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 是可用於偵測狀態模式/轉換的抽象方法。 此外， [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 和 [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 方法適用于在選取 *互動* 時建立自訂事件邏輯。

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>在偵測器中顯示自訂事件接收器欄位

*ReceiverBase* 腳本會使用 [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) 屬性，在偵測器中公開自訂屬性。 以下是 Vector3 的範例，其中包含工具提示和標籤資訊的自訂屬性。 當選取了 *互動* GameObject，且已加入相關聯的 *事件接收器* 類型時，這個屬性會在偵測器中顯示為可設定。

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>如何使用互動

### <a name="building-a-simple-button"></a>建立簡單的按鈕

您可以藉由將 *互動* 元件新增至設定為接收輸入事件的 GameObject，來建立一個簡單的按鈕。 它可能會在其上產生碰撞，或在子系上具有碰撞來接收輸入。 如果使用 *互動* 搭配以 Unity UI 為基礎的 gameobject，它應該位於 Canvas GameObject 下。

藉由建立新的設定檔、指派 GameObject 本身以及建立新的主題，讓按鈕一步更進一步。 此外，您也可以使用 *OnClick* 事件進行某些動作。

> [!NOTE]
> 讓 [按鈕 pressable](README_Button.md) 需要 [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 元件。 此外，還 [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) 需要元件才能將事件按到 *互動* 元件。

### <a name="creating-toggle-and-multi-dimension-buttons"></a>建立切換和多維度按鈕

#### <a name="toggle-button"></a>切換按鈕

若要讓按鈕可以切換，請將欄位變更 [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 為 [類型] `Toggle` 。 在 [ *設定檔* ] 區段中，會針對 *互動* 切換時使用的每個設定檔新增切換的主題。

當 [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 設定為切換時， *IsToggled* 核取方塊可以用來在執行時間初始化時設定控制項的預設值。

*CanSelect* 表示 *互動* 可以從 *off* 移至 *開啟* ，而 *CanDeselect* 表示反向。

![設定檔切換視覺主題範例](Images/Interactable/Profile_toggle.png)

開發人員可以利用 [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 和 [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 介面，透過程式碼取得/設定 *互動* 的切換狀態。

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>切換按鈕集合

通常會有一份切換按鈕清單，其中只有一個可在任何指定時間處於作用中狀態，也稱為星形組或選項按鈕等等。

使用 [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) 元件來啟用此功能。 此控制項可確保在任何指定時間都只會有一個 *互動* 切換。 *RadialSet* (資產/MRTK/SDK/FEATURES/UX/互動/Prefabs/RadialSet. 預製專案) 也是現成的絕佳起點。

若要建立自訂放射狀按鈕群組：

1) 建立多個 *互動* gameobject/按鈕
1) 使用 *SelectionMode* = 切換、 *CanSelect* = true 和 *CanDeselect* = false 來設定每個 *互動*
1) 針對所有 *Interactables* 建立空白的父 GameObject，然後新增 *InteractableToggleCollection* 元件
1) 將所有 *Interactables* 新增至 *InteractableToggleCollection* 上的 *ToggleList*
1) 設定 *InteractableToggleCollection CurrentIndex* 屬性，以判斷在開始時預設選取的按鈕。

<img src="Images/Interactable/InteractableToggleCollection.png" width="450" alt="Interactable toggle collection">

#### <a name="multi-dimensional-button"></a>多維度按鈕

多重維度選取模式可用來建立連續按鈕，或具有兩個以上步驟的按鈕，例如以三個值控制速度、Fast (1x) 、更快 (2x) 或最快 (3 倍) 。

當維度是數值時，最多可以加入9個主題，以針對每個步驟使用不同的主題來控制每個速度設定之按鈕的文字標籤或紋理。

每個 click 事件都會 `DimensionIndex` 在執行時間前移1，直到 `Dimensions` 達到該值為止。 然後迴圈將重設為0。

![多維度設定檔範例](Images/Interactable/Profile_multiDimensions.png)

開發人員可以評估， [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 以判斷哪個維度目前為使用中狀態。

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>在執行時間建立互動

*互動* 可在執行時間輕鬆地新增至任何 GameObject。 下列範例示範如何指派具有 [視覺效果主題](visualthemes.md)的設定檔。

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a>透過程式碼互動事件

您可以使用下列範例，透過程式碼將動作新增至基底 [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) 事件。

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

使用函式 [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 在執行時間動態加入事件接收器。

下列範例程式碼示範如何新增 [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，以接聽焦點的進入/離開，以及定義事件實例引發時要執行的動作程式碼。

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

下列範例程式碼示範如何新增 [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，以在切換能力 *Interactables* 上接聽選取/取消選取的狀態轉換，以及定義事件實例引發時要執行的動作程式碼。

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a>另請參閱

* [視覺主題](VisualThemes.md)
* [輸入動作](./Input/InputActions.md)
* [語音命令](./Input/Speech.md)
* [按鈕](README_Button.md)
* [MRTK 標準著色器](README_MRTKStandardShader.md)
