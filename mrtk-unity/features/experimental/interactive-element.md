---
title: 互動式元素
description: InteractiveElement MRTK 的檔
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Interactive 元素、互動
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144764"
---
# <a name="interactive-element-experimental"></a>Interactive 元素 [實驗性]

MRTK 輸入系統的簡化集中進入點。 包含狀態管理方法、事件管理和核心互動狀態的狀態設定邏輯。

互動式元素是 Unity 2019.3 和更新功能所支援的實驗性功能，因為它利用 Unity 2019.3 的新功能： [序列化參考](https://docs.unity3d.com/ScriptReference/SerializeReference.html)。

### <a name="interactive-element-inspector"></a>互動式元素偵測器

在播放模式中，互動式專案偵測器會提供視覺化意見反應，指出目前狀態是否為作用中。 如果狀態為使用中，則會以青色的色彩反白顯示。  如果狀態不是作用中，則不會變更色彩。 偵測器中狀態旁的數位為狀態值，如果狀態為作用中，則值為1，如果狀態不是作用中，則值為0。

![具有虛擬手互動的互動式元素](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>核心狀態

互動式元素包含核心狀態，並支援新增 [自訂狀態](#custom-states)。  核心狀態是一種已定義狀態設定邏輯的狀態 `BaseInteractiveElement` 。 以下是目前輸入導向核心狀態的清單： 

### <a name="current-core-states"></a>目前的核心狀態

- [預設值](#default-state) 

近和遠的互動核心狀態：
- [重點](#focus-state) 

近距離互動核心狀態：

- [將焦點放在附近](#focus-near-state)
- [觸控](#touch-state)

遠的互動核心狀態：
- [專注于最遠](#focus-far-state)
- [全選](#select-far-state)

其他核心狀態：
- [已點擊](#clicked-state)
- [開啟和關閉切換](#toggle-on-and-toggle-off-state)
- [語音關鍵字](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>如何透過偵測器新增核心狀態

1. 在互動式元素的偵測器中，流覽以 **加入核心狀態** 。

    ![透過偵測器新增核心狀態](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. 選取 [ **選取狀態** ] 按鈕，選擇要新增的核心狀態。 功能表中的狀態會依互動類型排序。

    ![透過已選取狀態的偵測器新增核心狀態](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. 開啟 [事件設定 foldout]，以查看與狀態相關聯的事件和屬性。

    ![透過具有事件設定的偵測器新增核心狀態](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>如何透過腳本新增核心狀態

使用 `AddNewState(stateName)` 方法來新增核心狀態。 如需可用核心狀態名稱的清單，請使用 `CoreInteractionState` 列舉。

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>狀態內部結構 

互動式元素中的狀態為類型 `InteractionState` 。  `InteractionState`包含下列屬性：

- **名稱**：狀態的名稱。
- **值**：狀態值。  如果狀態為 [開啟]，則狀態值為1。 如果狀態為 off，則狀態值為0。
- 作用 **中：狀態** 目前是否為使用中。 當狀態為 on 時，使用中屬性的值為 true，如果狀態為 off，則為 false。 
- **互動類型**：狀態的互動類型是指狀態適用的互動類型。 
  - `None`：不支援任何形式的輸入互動。
  - `Near`：近乎互動支援。 當有明確的手接觸到另一個遊戲物件時，即會將輸入視為接近互動，也就是已向下手勢的位置靠近世界空間中的遊戲物件位置。
  - `Far`：目前的互動支援。 當不需要直接接觸遊戲物件時，會將輸入視為遠的互動。 例如，透過控制器光線或注視的輸入會被視為目前的互動輸入。
  - `NearAndFar`：包含近乎遠的互動支援。 
  - `Other`：指標獨立互動支援。
- **事件** 設定：狀態的事件設定是序列化的事件設定檔進入點。 

所有這些屬性都是在內部的互動式元素所包含的內部設定 `State Manager` 。 若要修改狀態，請使用下列 helper 方法：

**狀態設定 Helper 方法**

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

取得狀態的事件設定是狀態本身的特定狀態。 每個核心狀態都有特定的事件設定類型，如下所述，下圖說明每個核心狀態的各節。

以下是取得狀態事件設定的一般化範例：

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>預設狀態

預設狀態一律存在於互動式元素上。  只有在所有其他狀態都不在使用中時，才會啟用此狀態。  如果任何其他狀態變成 [作用中]，則預設狀態將會在內部設定為 [關閉]。 

互動式元素會以狀態清單中出現的預設和焦點狀態進行初始化。 預設狀態一律需要出現在 [狀態] 清單中。 

#### <a name="getting-default-state-events"></a>取得預設狀態事件

預設狀態的事件設定類型： `StateEvents`

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a>焦點狀態

焦點狀態是接近且最遠的互動狀態，可視為混合現實與停留的相同。 焦點狀態接近與遠互動之間的區別因素是目前作用中的指標類型。  如果焦點狀態的指標類型是文字指標，則會將互動視為接近互動。  如果主要指標不是正在進行的指標，則會將互動視為目前的互動。 依預設，焦點狀態會出現在互動式元素中。

**焦點狀態行為** 
 ![使用虛擬手互動的焦點狀態](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

**焦點狀態偵測器** 
 ![Inpsector 中的焦點狀態](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>取得焦點狀態事件

焦點狀態的事件設定類型： `FocusEvents`

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a>將焦點放在最接近 vs 焦點的行為 

![使用虛擬手互動專注于接近遠](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>關注接近狀態

當焦點事件被引發，而主要指標為「進行中」指標時，就會設定接近狀態的焦點。 

將 **焦點放在接近狀態的行為** 
 ![使用虛擬手互動專注于接近狀態](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**專注于狀態檢查** 
 ![在偵測器中將焦點放在元件附近](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>取得 FocusNear 狀態事件

FocusNear 狀態的事件設定類型： `FocusEvents`

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a>專注于目前狀態

當主要指標不是「進行中」指標時，就會設定焦點最遠的狀態。  例如，預設控制器光線指標和 GGV (注視、手勢、Voice) 指標會被視為最遠的互動指標。

**專注于目前狀態的行為** 
 ![使用虛擬手互動專注于最遠的狀態](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

**專注于目前狀態檢查** 
 ![在偵測器中將焦點放在元件上](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>取得焦點到目前狀態的事件

FocusFar 狀態的事件設定類型： `FocusEvents`

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a>觸控狀態

觸控狀態是一種近乎互動的狀態，會在有明確的手上直接接觸物件時設定。  直接觸控表示說出的手形食指非常接近物件的世界位置。 依預設，如果在 [狀態] 清單中加入了「觸控」狀態，則 `NearInteractionTouchableVolume` 會將元件附加至物件。  偵測  `NearInteractionTouchableVolume` `NearInteractionTouchable` 觸控事件需要或元件存在。  和之間的 `NearInteractionTouchableVolume` 差異 `NearInteractionTouchable` 是 `NearInteractionTouchableVolume` 根據物件的碰撞器偵測觸控，並在平面的 `NearInteractionTouchable` 定義區域中偵測觸控。

**觸控狀態行為** 
 ![使用虛擬手互動的觸控狀態](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

**觸控狀態偵測器** 
 ![偵測器中的觸控狀態元件](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>取得觸控狀態事件

觸控狀態的事件設定類型： `TouchEvents`

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a>選取目前的狀態

顯示的是最遠的狀態 `IMixedRealityPointerHandler` 。  此狀態是最互動的狀態，可偵測到遠距離的互動點點擊 (的) ，並使用目前的互動指標，例如預設控制器光線指標或 GGV 指標。  在 [事件設定 foldout] 底下，選取 [目前的狀態] 會有一個名為的選項 `Global` 。 如果 `Global` 是 true，則 `IMixedRealityPointerHandler` 會註冊為全域輸入處理常式。  如果處理常式已註冊為 global，則不需要將焦點放在物件上來觸發輸入系統事件。  比方說，如果使用者想要在任何時候都知道，無論焦點是在哪一個物件上執行，請將設定 `Global` 為 true。 

**選取目前的狀態行為** 
 ![使用虛擬手互動選取遠](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**選取目前的狀態偵測器** 
 ![在偵測器中選取目前的元件](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>取得全選狀態事件

SelectFar 狀態的事件設定類型： `SelectFarEvents`

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a>按一下狀態

按下的狀態是由目前為止的互動所觸發：依預設， (選取 [目前的狀態]) 。  此狀態在內部切換為開啟，會叫用 OnClicked 事件，然後立即切換為關閉。 

> [!NOTE]
> 基於狀態活動之偵測器中的視覺效果意見反應不會出現在已按下的狀態，因為它會立即開啟，然後立即關閉。 

**按一下狀態行為** 
 ![點擊虛擬手互動的狀態](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

**按一下狀態偵測器** 
 ![按一下偵測器中的狀態元件](../images/interactive-element/InEditor/ClickedStateInspector.png)

**接近和離點的狀態範例**  
您可以使用方法，透過其他進入點來觸發按一下的狀態 `interactiveElement.TriggerClickedState()` 。  例如，如果使用者想要在物件上同時觸發按一下，則會將 `TriggerClickedState()` 方法新增為觸控狀態中的接聽程式。   

![虛擬手互動的近乎和目前狀態](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>取得按一下狀態事件

已按下狀態的事件設定類型： `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>切換開啟和關閉狀態

切換開啟和關閉狀態都是一組，而且兩者都必須存在以提供切換行為。  依預設，[切換開啟] 和 [關閉狀態] 會透過最遠的互動來觸發，請按一下 [最 (選取 [目前狀態]) 。  依預設，啟動時關閉狀態為 [作用中]，表示切換將會初始化為關閉。  如果使用者想要在開始時切換狀態為使用中狀態，請在 [切換開啟狀態] 設定 `IsSelectedOnStart` 為 [true]。

**ToggleOn 和切換關閉狀態行為** 
 ![開啟和關閉虛擬手互動](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**ToggleOn 和切換關閉狀態偵測器** 
 ![偵測器中的切換元件](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**近和遠切換狀態範例**  
類似于按下的狀態，切換狀態設定可以有多個使用方法的進入點 `interactiveElement.SetToggleStates()` 。 例如，如果使用者想要讓觸控成為設定切換狀態的額外進入點，則會將 `SetToggleStates()` 方法新增至觸控狀態中的其中一個事件。 

![使用虛擬手互動的近乎和遠切換](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>開啟和關閉狀態事件

ToggleOn 狀態的事件設定類型： `ToggleOnEvents`  
ToggleOff 狀態的事件設定類型： `ToggleOffEvents`

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a>語音關鍵字狀態

語音關鍵字狀態會接聽混合現實語音設定檔中定義的關鍵字。 在執行時間之前，必須先在語音命令設定檔中註冊任何新的關鍵字)  (步驟。 

**語音關鍵字狀態行為** 
 ![具有虛擬互動的語音關鍵字](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

**語音關鍵字狀態偵測器** 
 ![偵測器中的語音關鍵字元件](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> 在編輯器中按下 gif 中的 F5 鍵，即可觸發語音關鍵字狀態。 在編輯器的編輯器測試中進行設定的步驟如下所示。 

#### <a name="how-to-register-a-speech-commandkeyword"></a>如何註冊語音命令/關鍵字

1. 選取 **MixedRealityToolkit** 遊戲物件

1. 選取 [ **複製並自訂** 目前的設定檔]

1. 流覽至 [輸入] 區段，並選取 [ **複製** ] 以啟用輸入設定檔的修改

1. 向下滾動至輸入設定檔中的語音區段，並複製語音設定檔

    ![MRTK 遊戲物件中的語音關鍵字設定檔](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. 選取 [加入新的語音命令]

    ![在 MRTK 設定檔中新增語音關鍵字](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. 輸入新的關鍵字。 選擇性：將 KeyCode 變更為 F5 (或另一個 KeyCode) ，以允許在編輯器中進行測試。 

    ![在 MRTK 設定檔中設定語音關鍵字](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. 返回至互動式元素語音關鍵字狀態偵測器，然後選取 [**新增關鍵字**] 

    ![將關鍵字加入至互動式元素元件](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![關鍵字驗證和註冊](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. 輸入剛在語音設定檔中註冊的新關鍵字

    ![輸入新的語音關鍵字](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


若要在編輯器中測試語音關鍵字狀態，請按步驟 6 (F5) 中定義的 KeyCode，以模擬語音關鍵字辨識的事件。

#### <a name="getting-speech-keyword-state-events&quot;></a>取得語音關鍵字狀態事件

SpeechKeyword 狀態的事件設定類型： `SpeechKeywordEvents`

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>(&quot;SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a>自訂狀態

### <a name="how-to-create-a-custom-state-via-inspector"></a>如何透過偵測器建立自訂狀態 

透過偵測器建立的自訂狀態將會以預設狀態事件設定來初始化。 自訂狀態的預設事件設定為類型 `StateEvents` ，並包含 OnStateOn 和 OnStateOff 事件。

1. 在互動式元素的偵測器中，流覽以 **建立自訂狀態** 。
    
    ![建立自訂狀態](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. 輸入新狀態的名稱。 這個名稱必須是唯一的，且不能與現有的核心狀態相同。 
    
    ![輸入新自訂狀態的名稱](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. 選取 [ **設定狀態名稱** ] 以新增至 [狀態] 清單。
    
    ![將自訂狀態新增至狀態清單](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   這個自訂狀態是使用 `StateEvents` 包含和事件的預設事件設定來初始化 `OnStateOn` `OnStateOff` 。 若要建立新狀態的自訂事件設定，請參閱： [使用自訂事件設定建立自訂狀態](#creating-a-custom-state-with-a-custom-event-configuration)。
    
    ![互動式元素元件中顯示的新狀態](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a>如何透過腳本建立自訂狀態

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>使用自訂事件設定建立自訂狀態 

自訂狀態為 **鍵盤** 的範例檔案位於此處： MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

下列步驟會逐步解說建立自訂狀態事件設定和接收器檔案的現有範例。

1. 請考慮狀態名稱。  這個名稱必須是唯一的，且不能與現有的核心狀態相同。 基於此範例的目的，狀態名稱將會是 **鍵盤**。

1. 建立兩個名為 state name + "接收者" 和 state name + "Events" 的 .cs 檔案。 這些檔案的命名會在內部納入考慮，而且必須遵循狀態名稱 + 事件/接收器慣例。 

    ![鍵盤狀態腳本](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. 如需檔案內容的詳細資訊，請參閱 KeyboardEvents .cs 和 KeyboardReceiver .cs 檔案。 新的事件設定類別必須繼承自 `BaseInteractionEventConfiguration` ，而且新的事件接收器類別必須繼承自 `BaseEventReceiver` 。  鍵盤狀態的狀態設定範例位於檔案中 `CustomStateSettingExample.cs` 。 

1. 使用狀態名稱將狀態加入至互動式元素，如果事件設定和事件接收器檔案存在，則會辨識狀態名稱。  自訂事件設定檔中的屬性應該會出現在偵測器中。

    ![將自訂狀態加入至互動式元素中辨識的互動式元素 ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ 自訂狀態](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. 如需事件設定和事件接收器檔案的更多範例，請參閱這些路徑中的檔案：    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>範例場景 

互動式元素 + 狀態視覺化的範例場景位於此處： MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![具有互動式元素和狀態視覺化的範例場景](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Compressable 按鈕

範例場景包含名為和的 prefabs `CompressableButton` `CompressableButtonToggle` ，這些 prefabs `PressableButtonHoloLens2` 會鏡像使用互動式元素和狀態視覺化程式所建立之按鈕的行為。 `CompressableButton`元件目前是 `PressableButton`  +  `PressableButtonHoloLens2` 與 `BaseInteractiveElement` 做為基類的組合。 

## <a name="state-visualizer-experimental"></a>狀態視覺化 [實驗]

狀態視覺化元件會根據連結的互動式元素元件中定義的狀態，將動畫新增至物件。 此元件會建立動畫資產、將它們放在 MixedRealityToolkit 的資料夾中，並透過將 Animatable 屬性新增至目標遊戲物件來啟用簡化動畫主要畫面格的設定。 若要啟用狀態之間的動畫轉換，則會建立 Animator 控制器資產，並使用相關聯的參數和任何狀態轉換來產生預設狀態電腦。  您可以在 Unity 的 Animator 視窗中查看狀態機器。

### <a name="state-visualizer-and-unity-animation-system"></a>狀態視覺化和 Unity 動畫系統

狀態視覺化檢視目前會利用 Unity 動畫系統。 

當您按下 [ **產生新的動畫剪輯** ] 按鈕時，系統會根據互動專案中的狀態名稱來產生新的動畫剪輯資產，並放在 [MixedRealityToolkit] 資料夾中。 每個狀態容器中的動畫剪輯屬性都會設定為相關聯的動畫剪輯。

![狀態視覺化元件中的動畫剪輯](../images/interactive-element/StateVisualizer/AnimationClips.png)

也會產生 [Animator 狀態機器](https://docs.unity3d.com/Manual/AnimationOverview.html) ，以管理動畫剪輯之間的平滑轉換。  根據預設，狀態機器會利用 [任何狀態](https://docs.unity3d.com/Manual/class-State.html) 來允許互動式元素中任何狀態之間的轉換。 

在[animator 中觸發的狀態視覺化](https://docs.unity3d.com/Manual/AnimationParameters.html)也會針對每個狀態產生，而在狀態視覺化中會使用觸發程式參數來觸發動畫。

![Unity 狀態機器](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>執行階段限制 

狀態視覺化必須透過偵測器加入至物件，而且無法透過腳本加入。  修改 AnimatorStateMachine/AnimationController 的屬性會包含在編輯器命名空間 () 在 `UnityEditor.Animations` 建立應用程式時移除。

## <a name="how-to-use-the-state-visualizer"></a>如何使用狀態視覺化

1. 建立 Cube
1. 附加互動式元素
1. 附加狀態視覺化
1. 選取 [ **產生新的動畫] 剪輯**

    ![產生新的動畫剪輯](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![在視覺化檢視和互動式元素元件中顯示產生的動畫剪輯](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. 在焦點狀態容器中，選取 [**新增目標**]

    ![正在加入狀態視覺化目標](../images/interactive-element/StateVisualizer/AddTarget.png)

1. 將目前的遊戲物件拖曳至目標欄位 

    ![設定狀態視覺化目標](../images/interactive-element/StateVisualizer/SetTarget.png)

1. 開啟 Cube Animatable 屬性 foldout
1. 選取 [Animatable] 屬性下拉式功能表，然後選取 [**色彩**]。

    ![設定狀態視覺化色彩](../images/interactive-element/StateVisualizer/SetColor.png)

1. 選取 **[新增色彩 Animatable] 屬性**

    ![選取 [視覺化] 色彩 animatable 屬性](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. 選擇色彩 

    ![從色輪選擇視覺化色彩](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. 按下 [播放] 並觀察過渡色彩變更

    ![使用虛擬手互動的過渡色彩變更範例](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>Animatable 屬性

Animatable 屬性的主要目的是簡化動畫剪輯主要畫面格的設定。  如果使用者熟悉 Unity 動畫系統，而且想要在產生的動畫剪輯上直接設定主要畫面格，則可以直接將 Animatable 屬性加入至目標物件，並在 Unity 的動畫視窗中開啟剪輯， (Windows > 動畫 > 動畫) 。 

如果使用動畫的 Animatable 屬性，則曲線類型會設定為 EaseInOut。

**目前的 Animatable 屬性：**
- [調整位移](#scale-offset)
- [位置位移](#position-offset)
- [色彩](#color)
- [著色器色彩](#shader-color)
- [著色器浮點數](#shader-float)
- [著色器向量](#shader-vector)

### <a name="scale-offset"></a>調整位移

Scale Offset Animatable 屬性會取得物件目前的小數位數，並加入已定義的位移。

![使用虛擬手互動調整位移](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>位置位移

Position Offset Animatable 屬性會取得物件的目前位置，並加入已定義的位移。

![使用虛擬手互動的位置位移](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Color

如果材質有主要色彩屬性，Color Animatable 屬性代表材質的主要色彩。 這個屬性會將 `material._Color` 屬性動畫。

![使用虛擬手互動的焦點色彩變更](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>著色器色彩

著色器色彩 Animatable 屬性是指 Color 類型的著色器屬性。 所有著色器屬性都需要屬性名稱。 下列 gif 示範如何以動畫顯示名稱為 Fill_Color 但不是主要材質色彩的著色器色彩屬性。  觀察材質偵測器中的變更值。

![使用虛擬手互動的陰影色彩](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>著色器浮點數

著色器 Float Animatable 屬性是指 Float 類型的著色器屬性。 所有著色器屬性都需要屬性名稱。 在下 gif 中，觀察材質屬性之材質偵測器中的變更值。 

![具有虛擬手互動的著色器浮點數](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>著色器向量

著色器向量 Animatable 屬性指的是 Vector4 類型的著色器屬性。 所有著色器屬性都需要屬性名稱。 在下 gif 中，觀察 [材質偵測器] 中 [並排 (主要 Tex_ST) ] 屬性的變更值。 

![具有虛擬手互動的著色器向量](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>如何尋找 Animatable 著色器屬性名稱

1. 導覽至視窗 > 動畫 > 動畫
1. 確定已在階層中選取具有狀態視覺化的物件
1. 在動畫視窗中選取任何動畫剪輯
1. 選取 [ **新增屬性**]，開啟 [網狀轉譯器 foldout 

    ![在 Animator 視窗中新增動畫屬性](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. 此清單包含所有 Animatable 屬性名稱的名稱 

    ![Animator 視窗中的網格轉譯器動畫屬性](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>另請參閱

- [**按鈕**](../ux-building-blocks/button.md)
- [**界限控制項**](../ux-building-blocks/bounds-control.md)
- [**方格物件集合**](../ux-building-blocks/object-collection.md)
- [**RadialView 規劃**](../ux-building-blocks/solvers/solver.md)
