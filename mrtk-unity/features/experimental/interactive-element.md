---
title: InteractiveElement
description: InteractiveElement MRTK 的檔
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Interactive 元素、互動
ms.openlocfilehash: 7c3bc6810a6ac5b556384b2ab97bb3ecda783760
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694535"
---
# <a name="interactive-element-experimental"></a><span data-ttu-id="ea1cc-104">Interactive 元素 [實驗性]</span><span class="sxs-lookup"><span data-stu-id="ea1cc-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="ea1cc-105">MRTK 輸入系統的簡化集中進入點。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="ea1cc-106">包含狀態管理方法、事件管理和核心互動狀態的狀態設定邏輯。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="ea1cc-107">互動式元素是 Unity 2019.3 和更新功能所支援的實驗性功能，因為它利用 Unity 2019.3 的新功能： [序列化參考](https://docs.unity3d.com/ScriptReference/SerializeReference.html)。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="ea1cc-108">互動式元素偵測器</span><span class="sxs-lookup"><span data-stu-id="ea1cc-108">Interactive Element Inspector</span></span>

<span data-ttu-id="ea1cc-109">在播放模式中，互動式專案偵測器會提供視覺化意見反應，指出目前狀態是否為作用中。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="ea1cc-110">如果狀態為使用中，則會以青色的色彩反白顯示。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="ea1cc-111">如果狀態不是作用中，則不會變更色彩。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="ea1cc-112">偵測器中狀態旁的數位為狀態值，如果狀態為作用中，則值為1，如果狀態不是作用中，則值為0。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![具有虛擬手互動的互動式元素](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="ea1cc-114">核心狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-114">Core States</span></span>

<span data-ttu-id="ea1cc-115">互動式元素包含核心狀態，並支援新增 [自訂狀態](#custom-states)。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="ea1cc-116">核心狀態是一種已定義狀態設定邏輯的狀態 `BaseInteractiveElement` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="ea1cc-117">以下是目前輸入導向核心狀態的清單：</span><span class="sxs-lookup"><span data-stu-id="ea1cc-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="ea1cc-118">目前的核心狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-118">Current Core States</span></span>

- [<span data-ttu-id="ea1cc-119">預設值</span><span class="sxs-lookup"><span data-stu-id="ea1cc-119">Default</span></span>](#default-state) 

<span data-ttu-id="ea1cc-120">近和遠的互動核心狀態：</span><span class="sxs-lookup"><span data-stu-id="ea1cc-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="ea1cc-121">重點</span><span class="sxs-lookup"><span data-stu-id="ea1cc-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="ea1cc-122">近距離互動核心狀態：</span><span class="sxs-lookup"><span data-stu-id="ea1cc-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="ea1cc-123">將焦點放在附近</span><span class="sxs-lookup"><span data-stu-id="ea1cc-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="ea1cc-124">觸控</span><span class="sxs-lookup"><span data-stu-id="ea1cc-124">Touch</span></span>](#touch-state)

<span data-ttu-id="ea1cc-125">遠的互動核心狀態：</span><span class="sxs-lookup"><span data-stu-id="ea1cc-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="ea1cc-126">專注于最遠</span><span class="sxs-lookup"><span data-stu-id="ea1cc-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="ea1cc-127">全選</span><span class="sxs-lookup"><span data-stu-id="ea1cc-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="ea1cc-128">其他核心狀態：</span><span class="sxs-lookup"><span data-stu-id="ea1cc-128">Other Core States:</span></span>
- [<span data-ttu-id="ea1cc-129">已點擊</span><span class="sxs-lookup"><span data-stu-id="ea1cc-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="ea1cc-130">開啟和關閉切換</span><span class="sxs-lookup"><span data-stu-id="ea1cc-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="ea1cc-131">語音關鍵字</span><span class="sxs-lookup"><span data-stu-id="ea1cc-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="ea1cc-132">如何透過偵測器新增核心狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="ea1cc-133">在互動式元素的偵測器中，流覽以 **加入核心狀態** 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![透過偵測器新增核心狀態](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="ea1cc-135">選取 [ **選取狀態** ] 按鈕，選擇要新增的核心狀態。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="ea1cc-136">功能表中的狀態會依互動類型排序。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-136">The states in the menu are sorted by interaction type.</span></span>

    ![透過已選取狀態的偵測器新增核心狀態](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="ea1cc-138">開啟 [事件設定 foldout]，以查看與狀態相關聯的事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![透過具有事件設定的偵測器新增核心狀態](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="ea1cc-140">如何透過腳本新增核心狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="ea1cc-141">使用 `AddNewState(stateName)` 方法來新增核心狀態。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="ea1cc-142">如需可用核心狀態名稱的清單，請使用 `CoreInteractionState` 列舉。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="ea1cc-143">狀態內部結構</span><span class="sxs-lookup"><span data-stu-id="ea1cc-143">States Internal Structure</span></span> 

<span data-ttu-id="ea1cc-144">互動式元素中的狀態為類型 `InteractionState` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="ea1cc-145">`InteractionState`包含下列屬性：</span><span class="sxs-lookup"><span data-stu-id="ea1cc-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="ea1cc-146">**名稱**：狀態的名稱。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="ea1cc-147">**值**：狀態值。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-147">**Value**: The state value.</span></span>  <span data-ttu-id="ea1cc-148">如果狀態為 [開啟]，則狀態值為1。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="ea1cc-149">如果狀態為 off，則狀態值為0。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="ea1cc-150">作用 **中：狀態** 目前是否為使用中。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="ea1cc-151">當狀態為 on 時，使用中屬性的值為 true，如果狀態為 off，則為 false。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="ea1cc-152">**互動類型**：狀態的互動類型是指狀態適用的互動類型。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="ea1cc-153">`None`：不支援任何形式的輸入互動。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="ea1cc-154">`Near`：近乎互動支援。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="ea1cc-155">當有明確的手接觸到另一個遊戲物件時，即會將輸入視為接近互動，也就是已向下手勢的位置靠近世界空間中的遊戲物件位置。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="ea1cc-156">`Far`：目前的互動支援。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="ea1cc-157">當不需要直接接觸遊戲物件時，會將輸入視為遠的互動。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="ea1cc-158">例如，透過控制器光線或注視的輸入會被視為目前的互動輸入。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="ea1cc-159">`NearAndFar`：包含近乎遠的互動支援。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="ea1cc-160">`Other`：指標獨立互動支援。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="ea1cc-161">**事件** 設定：狀態的事件設定是序列化的事件設定檔進入點。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="ea1cc-162">所有這些屬性都是在內部的互動式元素所包含的內部設定 `State Manager` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="ea1cc-163">若要修改狀態，請使用下列 helper 方法：</span><span class="sxs-lookup"><span data-stu-id="ea1cc-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="ea1cc-164">**狀態設定 Helper 方法**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-164">**State Setting Helper Methods**</span></span>

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

<span data-ttu-id="ea1cc-165">取得狀態的事件設定是狀態本身的特定狀態。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="ea1cc-166">每個核心狀態都有特定的事件設定類型，如下所述，下圖說明每個核心狀態的各節。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="ea1cc-167">以下是取得狀態事件設定的一般化範例：</span><span class="sxs-lookup"><span data-stu-id="ea1cc-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="ea1cc-168">預設狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-168">Default State</span></span>

<span data-ttu-id="ea1cc-169">預設狀態一律存在於互動式元素上。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="ea1cc-170">只有在所有其他狀態都不在使用中時，才會啟用此狀態。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="ea1cc-171">如果任何其他狀態變成 [作用中]，則預設狀態將會在內部設定為 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="ea1cc-172">互動式元素會以狀態清單中出現的預設和焦點狀態進行初始化。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="ea1cc-173">預設狀態一律需要出現在 [狀態] 清單中。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="ea1cc-174">取得預設狀態事件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-174">Getting Default State Events</span></span>

<span data-ttu-id="ea1cc-175">預設狀態的事件設定類型： `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-175">Event configuration type for the Default State: `StateEvents`</span></span>

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

### <a name="focus-state"></a><span data-ttu-id="ea1cc-176">焦點狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-176">Focus State</span></span>

<span data-ttu-id="ea1cc-177">焦點狀態是接近且最遠的互動狀態，可視為混合現實與停留的相同。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="ea1cc-178">焦點狀態接近與遠互動之間的區別因素是目前作用中的指標類型。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="ea1cc-179">如果焦點狀態的指標類型是文字指標，則會將互動視為接近互動。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="ea1cc-180">如果主要指標不是正在進行的指標，則會將互動視為目前的互動。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="ea1cc-181">依預設，焦點狀態會出現在互動式元素中。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="ea1cc-182">**焦點狀態行為** 
 ![使用虛擬手互動的焦點狀態](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-182">**Focus State Behavior**
![Focus state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="ea1cc-183">**焦點狀態偵測器** 
 ![Inpsector 中的焦點狀態](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-183">**Focus State Inspector**
![Focus state in the Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events"></a><span data-ttu-id="ea1cc-184">取得焦點狀態事件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-184">Getting Focus State Events</span></span>

<span data-ttu-id="ea1cc-185">焦點狀態的事件設定類型： `FocusEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-185">Event configuration type for the Focus State: `FocusEvents`</span></span>

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>("Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="ea1cc-186">將焦點放在最接近 vs 焦點的行為</span><span class="sxs-lookup"><span data-stu-id="ea1cc-186">Focus Near vs Focus Far Behavior</span></span> 

![使用虛擬手互動專注于接近遠](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="ea1cc-188">關注接近狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-188">Focus Near State</span></span>

<span data-ttu-id="ea1cc-189">當焦點事件被引發，而主要指標為「進行中」指標時，就會設定接近狀態的焦點。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="ea1cc-190">將 **焦點放在接近狀態的行為** 
 ![使用虛擬手互動專注于接近狀態](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-190">**Focus Near State Behavior**
![Focus near state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="ea1cc-191">**專注于狀態檢查** 
 ![在偵測器中將焦點放在元件附近](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-191">**Focus Near State Inspector**
![Focus near component in the Inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events"></a><span data-ttu-id="ea1cc-192">取得 FocusNear 狀態事件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-192">Getting FocusNear State Events</span></span>

<span data-ttu-id="ea1cc-193">FocusNear 狀態的事件設定類型： `FocusEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-193">Event configuration type for the FocusNear State: `FocusEvents`</span></span>

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>("FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a><span data-ttu-id="ea1cc-194">專注于目前狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-194">Focus Far State</span></span>

<span data-ttu-id="ea1cc-195">當主要指標不是「進行中」指標時，就會設定焦點最遠的狀態。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="ea1cc-196">例如，預設控制器光線指標和 GGV (注視、手勢、Voice) 指標會被視為最遠的互動指標。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="ea1cc-197">**專注于目前狀態的行為** 
 ![使用虛擬手互動專注于最遠的狀態](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-197">**Focus Far State Behavior**
![Focus state far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="ea1cc-198">**專注于目前狀態檢查** 
 ![在偵測器中將焦點放在元件上](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-198">**Focus Far State Inspector**
![Focus far component in the Inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events"></a><span data-ttu-id="ea1cc-199">取得焦點到目前狀態的事件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-199">Getting Focus Far State Events</span></span>

<span data-ttu-id="ea1cc-200">FocusFar 狀態的事件設定類型： `FocusEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-200">Event configuration type for the FocusFar State: `FocusEvents`</span></span>

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>("FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a><span data-ttu-id="ea1cc-201">觸控狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-201">Touch State</span></span>

<span data-ttu-id="ea1cc-202">觸控狀態是一種近乎互動的狀態，會在有明確的手上直接接觸物件時設定。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="ea1cc-203">直接觸控表示說出的手形食指非常接近物件的世界位置。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="ea1cc-204">依預設，如果在 [狀態] 清單中加入了「觸控」狀態，則 `NearInteractionTouchableVolume` 會將元件附加至物件。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="ea1cc-205">偵測  `NearInteractionTouchableVolume` `NearInteractionTouchable` 觸控事件需要或元件存在。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="ea1cc-206">和之間的 `NearInteractionTouchableVolume` 差異 `NearInteractionTouchable` 是 `NearInteractionTouchableVolume` 根據物件的碰撞器偵測觸控，並在平面的 `NearInteractionTouchable` 定義區域中偵測觸控。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="ea1cc-207">**觸控狀態行為** 
 ![使用虛擬手互動的觸控狀態](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-207">**Touch State Behavior**
![Touch state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="ea1cc-208">**觸控狀態偵測器** 
 ![偵測器中的觸控狀態元件](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-208">**Touch State Inspector**
![Touch state component in the Inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events"></a><span data-ttu-id="ea1cc-209">取得觸控狀態事件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-209">Getting Touch State Events</span></span>

<span data-ttu-id="ea1cc-210">觸控狀態的事件設定類型： `TouchEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-210">Event configuration type for the Touch State: `TouchEvents`</span></span>

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>("Touch");

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

### <a name="select-far-state"></a><span data-ttu-id="ea1cc-211">選取目前的狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-211">Select Far State</span></span>

<span data-ttu-id="ea1cc-212">顯示的是最遠的狀態 `IMixedRealityPointerHandler` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="ea1cc-213">此狀態是最互動的狀態，可偵測到遠距離的互動點點擊 (的) ，並使用目前的互動指標，例如預設控制器光線指標或 GGV 指標。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="ea1cc-214">在 [事件設定 foldout] 底下，選取 [目前的狀態] 會有一個名為的選項 `Global` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="ea1cc-215">如果 `Global` 是 true，則 `IMixedRealityPointerHandler` 會註冊為全域輸入處理常式。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="ea1cc-216">如果處理常式已註冊為 global，則不需要將焦點放在物件上來觸發輸入系統事件。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="ea1cc-217">比方說，如果使用者想要在任何時候都知道，無論焦點是在哪一個物件上執行，請將設定 `Global` 為 true。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="ea1cc-218">**選取目前的狀態行為** 
 ![使用虛擬手互動選取遠](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-218">**Select Far State Behavior**
![Select far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="ea1cc-219">**選取目前的狀態偵測器** 
 ![在偵測器中選取目前的元件](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-219">**Select Far State Inspector**
![Select far component in the Inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events"></a><span data-ttu-id="ea1cc-220">取得全選狀態事件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-220">Getting Select Far State Events</span></span>

<span data-ttu-id="ea1cc-221">SelectFar 狀態的事件設定類型： `SelectFarEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-221">Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>("SelectFar");

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

### <a name="clicked-state"></a><span data-ttu-id="ea1cc-222">按一下狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-222">Clicked State</span></span>

<span data-ttu-id="ea1cc-223">按下的狀態是由目前為止的互動所觸發：依預設， (選取 [目前的狀態]) 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="ea1cc-224">此狀態在內部切換為開啟，會叫用 OnClicked 事件，然後立即切換為關閉。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="ea1cc-225">基於狀態活動之偵測器中的視覺效果意見反應不會出現在已按下的狀態，因為它會立即開啟，然後立即關閉。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="ea1cc-226">**按一下狀態行為** 
 ![點擊虛擬手互動的狀態](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-226">**Clicked State Behavior**
![Clicked state with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="ea1cc-227">**按一下狀態偵測器** 
 ![按一下偵測器中的狀態元件](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-227">**Clicked State Inspector**
![Click state component in the Inspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="ea1cc-228">**接近和離點的狀態範例**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="ea1cc-229">您可以使用方法，透過其他進入點來觸發按一下的狀態 `interactiveElement.TriggerClickedState()` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="ea1cc-230">例如，如果使用者想要在物件上同時觸發按一下，則會將 `TriggerClickedState()` 方法新增為觸控狀態中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![虛擬手互動的近乎和目前狀態](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events"></a><span data-ttu-id="ea1cc-232">取得按一下狀態事件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-232">Getting Clicked State Events</span></span>

<span data-ttu-id="ea1cc-233">已按下狀態的事件設定類型： `ClickedEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-233">Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>("Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="ea1cc-234">切換開啟和關閉狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="ea1cc-235">切換開啟和關閉狀態都是一組，而且兩者都必須存在以提供切換行為。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="ea1cc-236">依預設，[切換開啟] 和 [關閉狀態] 會透過最遠的互動來觸發，請按一下 [最 (選取 [目前狀態]) 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="ea1cc-237">依預設，啟動時關閉狀態為 [作用中]，表示切換將會初始化為關閉。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="ea1cc-238">如果使用者想要在開始時切換狀態為使用中狀態，請在 [切換開啟狀態] 設定 `IsSelectedOnStart` 為 [true]。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="ea1cc-239">**ToggleOn 和切換關閉狀態行為** 
 ![開啟和關閉虛擬手互動](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-239">**ToggleOn and Toggle Off State Behavior**
![Toggle on and off with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="ea1cc-240">**ToggleOn 和切換關閉狀態偵測器** 
 ![偵測器中的切換元件](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-240">**ToggleOn and Toggle Off State Inspector**
![Toggle component in the Inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="ea1cc-241">**近和遠切換狀態範例**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="ea1cc-242">類似于按下的狀態，切換狀態設定可以有多個使用方法的進入點 `interactiveElement.SetToggleStates()` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="ea1cc-243">例如，如果使用者想要讓觸控成為設定切換狀態的額外進入點，則會將 `SetToggleStates()` 方法新增至觸控狀態中的其中一個事件。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![使用虛擬手互動的近乎和遠切換](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events"></a><span data-ttu-id="ea1cc-245">開啟和關閉狀態事件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-245">Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id="ea1cc-246">ToggleOn 狀態的事件設定類型： `ToggleOnEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-246">Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id="ea1cc-247">ToggleOff 狀態的事件設定類型： `ToggleOffEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-247">Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>("ToggleOn");

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

### <a name="speech-keyword-state"></a><span data-ttu-id="ea1cc-248">語音關鍵字狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-248">Speech Keyword State</span></span>

<span data-ttu-id="ea1cc-249">語音關鍵字狀態會接聽混合現實語音設定檔中定義的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="ea1cc-250">在執行時間之前，必須先在語音命令設定檔中註冊任何新的關鍵字)  (步驟。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="ea1cc-251">**語音關鍵字狀態行為** 
 ![具有虛擬互動的語音關鍵字](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-251">**Speech Keyword State Behavior**
![Speech keyword with virtual interaction](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="ea1cc-252">**語音關鍵字狀態偵測器** 
 ![偵測器中的語音關鍵字元件](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-252">**Speech Keyword State Inspector**
![Speech keyword component in the Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="ea1cc-253">在編輯器中按下 gif 中的 F5 鍵，即可觸發語音關鍵字狀態。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="ea1cc-254">在編輯器的編輯器測試中進行設定的步驟如下所示。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="ea1cc-255">如何註冊語音命令/關鍵字</span><span class="sxs-lookup"><span data-stu-id="ea1cc-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="ea1cc-256">選取 **MixedRealityToolkit** 遊戲物件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="ea1cc-257">選取 [ **複製並自訂** 目前的設定檔]</span><span class="sxs-lookup"><span data-stu-id="ea1cc-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="ea1cc-258">流覽至 [輸入] 區段，並選取 [ **複製** ] 以啟用輸入設定檔的修改</span><span class="sxs-lookup"><span data-stu-id="ea1cc-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="ea1cc-259">向下滾動至輸入設定檔中的語音區段，並複製語音設定檔</span><span class="sxs-lookup"><span data-stu-id="ea1cc-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![MRTK 遊戲物件中的語音關鍵字設定檔](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="ea1cc-261">選取 [加入新的語音命令]</span><span class="sxs-lookup"><span data-stu-id="ea1cc-261">Select Add a New Speech Command</span></span>

    ![在 MRTK 設定檔中新增語音關鍵字](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="ea1cc-263">輸入新的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-263">Enter the new keyword.</span></span> <span data-ttu-id="ea1cc-264">選擇性：將 KeyCode 變更為 F5 (或另一個 KeyCode) ，以允許在編輯器中進行測試。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![在 MRTK 設定檔中設定語音關鍵字](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="ea1cc-266">返回至互動式元素語音關鍵字狀態偵測器，然後選取 [**新增關鍵字**]</span><span class="sxs-lookup"><span data-stu-id="ea1cc-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![將關鍵字加入至互動式元素元件](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![關鍵字驗證和註冊](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="ea1cc-269">輸入剛在語音設定檔中註冊的新關鍵字</span><span class="sxs-lookup"><span data-stu-id="ea1cc-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![輸入新的語音關鍵字](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="ea1cc-271">若要在編輯器中測試語音關鍵字狀態，請按步驟 6 (F5) 中定義的 KeyCode，以模擬語音關鍵字辨識的事件。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="ea1cc-272">取得語音關鍵字狀態事件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="ea1cc-273">SpeechKeyword 狀態的事件設定類型： `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="ea1cc-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>("SpeechKeyword");

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

## <a name="custom-states"></a><span data-ttu-id="ea1cc-274">自訂狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="ea1cc-275">如何透過偵測器建立自訂狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="ea1cc-276">透過偵測器建立的自訂狀態將會以預設狀態事件設定來初始化。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="ea1cc-277">自訂狀態的預設事件設定為類型 `StateEvents` ，並包含 OnStateOn 和 OnStateOff 事件。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="ea1cc-278">在互動式元素的偵測器中，流覽以 **建立自訂狀態** 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![建立自訂狀態](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="ea1cc-280">輸入新狀態的名稱。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-280">Enter the name of the new state.</span></span> <span data-ttu-id="ea1cc-281">這個名稱必須是唯一的，且不能與現有的核心狀態相同。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![輸入新自訂狀態的名稱](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="ea1cc-283">選取 [ **設定狀態名稱** ] 以新增至 [狀態] 清單。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![將自訂狀態新增至狀態清單](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="ea1cc-285">這個自訂狀態是使用 `StateEvents` 包含和事件的預設事件設定來初始化 `OnStateOn` `OnStateOff` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="ea1cc-286">若要建立新狀態的自訂事件設定，請參閱： [使用自訂事件設定建立自訂狀態](#creating-a-custom-state-with-a-custom-event-configuration)。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![互動式元素元件中顯示的新狀態](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script"></a><span data-ttu-id="ea1cc-288">如何透過腳本建立自訂狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-288">How to Create a Custom State via Script</span></span>

```c#
interactiveElement.AddNewState("MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="ea1cc-289">使用自訂事件設定建立自訂狀態</span><span class="sxs-lookup"><span data-stu-id="ea1cc-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="ea1cc-290">自訂狀態為 **鍵盤** 的範例檔案位於此處： MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span><span class="sxs-lookup"><span data-stu-id="ea1cc-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="ea1cc-291">下列步驟會逐步解說建立自訂狀態事件設定和接收器檔案的現有範例。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="ea1cc-292">請考慮狀態名稱。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-292">Think of a state name.</span></span>  <span data-ttu-id="ea1cc-293">這個名稱必須是唯一的，且不能與現有的核心狀態相同。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="ea1cc-294">基於此範例的目的，狀態名稱將會是 **鍵盤**。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="ea1cc-295">建立兩個名為 state name + "接收者" 和 state name + "Events" 的 .cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="ea1cc-296">這些檔案的命名會在內部納入考慮，而且必須遵循狀態名稱 + 事件/接收器慣例。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![鍵盤狀態腳本](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="ea1cc-298">如需檔案內容的詳細資訊，請參閱 KeyboardEvents .cs 和 KeyboardReceiver .cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="ea1cc-299">新的事件設定類別必須繼承自 `BaseInteractionEventConfiguration` ，而且新的事件接收器類別必須繼承自 `BaseEventReceiver` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="ea1cc-300">鍵盤狀態的狀態設定範例位於檔案中 `CustomStateSettingExample.cs` 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="ea1cc-301">使用狀態名稱將狀態加入至互動式元素，如果事件設定和事件接收器檔案存在，則會辨識狀態名稱。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="ea1cc-302">自訂事件設定檔中的屬性應該會出現在偵測器中。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="ea1cc-303">![將自訂狀態加入至互動式元素中辨識的互動式元素 ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ 自訂狀態](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="ea1cc-303">![Adding custom state to interactive element](../images/interactive-element/InEditor/AddKeyboardState.png) ![Custom state recognized in the interactive element](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="ea1cc-304">如需事件設定和事件接收器檔案的更多範例，請參閱這些路徑中的檔案：</span><span class="sxs-lookup"><span data-stu-id="ea1cc-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="ea1cc-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span><span class="sxs-lookup"><span data-stu-id="ea1cc-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="ea1cc-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span><span class="sxs-lookup"><span data-stu-id="ea1cc-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="ea1cc-307">範例場景</span><span class="sxs-lookup"><span data-stu-id="ea1cc-307">Example Scene</span></span> 

<span data-ttu-id="ea1cc-308">互動式元素 + 狀態視覺化的範例場景位於此處： MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span><span class="sxs-lookup"><span data-stu-id="ea1cc-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![具有互動式元素和狀態視覺化的範例場景](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="ea1cc-310">Compressable 按鈕</span><span class="sxs-lookup"><span data-stu-id="ea1cc-310">Compressable Button</span></span>

<span data-ttu-id="ea1cc-311">範例場景包含名為和的 prefabs `CompressableButton` `CompressableButtonToggle` ，這些 prefabs `PressableButtonHoloLens2` 會鏡像使用互動式元素和狀態視覺化程式所建立之按鈕的行為。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="ea1cc-312">`CompressableButton`元件目前是 `PressableButton`  +  `PressableButtonHoloLens2` 與 `BaseInteractiveElement` 做為基類的組合。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

## <a name="state-visualizer-experimental"></a><span data-ttu-id="ea1cc-313">狀態視覺化 [實驗]</span><span class="sxs-lookup"><span data-stu-id="ea1cc-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="ea1cc-314">狀態視覺化元件會根據連結的互動式元素元件中定義的狀態，將動畫新增至物件。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="ea1cc-315">此元件會建立動畫資產、將它們放在 MixedRealityToolkit 的資料夾中，並透過將 Animatable 屬性新增至目標遊戲物件來啟用簡化動畫主要畫面格的設定。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="ea1cc-316">若要啟用狀態之間的動畫轉換，則會建立 Animator 控制器資產，並使用相關聯的參數和任何狀態轉換來產生預設狀態電腦。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="ea1cc-317">您可以在 Unity 的 Animator 視窗中查看狀態機器。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-317">The state machine can be viewed in Unity's Animator window.</span></span>

### <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="ea1cc-318">狀態視覺化和 Unity 動畫系統</span><span class="sxs-lookup"><span data-stu-id="ea1cc-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="ea1cc-319">狀態視覺化檢視目前會利用 Unity 動畫系統。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="ea1cc-320">當您按下 [ **產生新的動畫剪輯** ] 按鈕時，系統會根據互動專案中的狀態名稱來產生新的動畫剪輯資產，並放在 [MixedRealityToolkit] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="ea1cc-321">每個狀態容器中的動畫剪輯屬性都會設定為相關聯的動畫剪輯。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![狀態視覺化元件中的動畫剪輯](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="ea1cc-323">也會產生 [Animator 狀態機器](https://docs.unity3d.com/Manual/AnimationOverview.html) ，以管理動畫剪輯之間的平滑轉換。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="ea1cc-324">根據預設，狀態機器會利用 [任何狀態](https://docs.unity3d.com/Manual/class-State.html) 來允許互動式元素中任何狀態之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="ea1cc-325">在[animator 中觸發的狀態視覺化](https://docs.unity3d.com/Manual/AnimationParameters.html)也會針對每個狀態產生，而在狀態視覺化中會使用觸發程式參數來觸發動畫。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-325">[State visualizers triggered in the animator](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![Unity 狀態機器](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="ea1cc-327">執行階段限制</span><span class="sxs-lookup"><span data-stu-id="ea1cc-327">Runtime Limitations</span></span> 

<span data-ttu-id="ea1cc-328">狀態視覺化必須透過偵測器加入至物件，而且無法透過腳本加入。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="ea1cc-329">修改 AnimatorStateMachine/AnimationController 的屬性會包含在編輯器命名空間 () 在 `UnityEditor.Animations` 建立應用程式時移除。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="ea1cc-330">如何使用狀態視覺化</span><span class="sxs-lookup"><span data-stu-id="ea1cc-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="ea1cc-331">建立 Cube</span><span class="sxs-lookup"><span data-stu-id="ea1cc-331">Create a Cube</span></span>
1. <span data-ttu-id="ea1cc-332">附加互動式元素</span><span class="sxs-lookup"><span data-stu-id="ea1cc-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="ea1cc-333">附加狀態視覺化</span><span class="sxs-lookup"><span data-stu-id="ea1cc-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="ea1cc-334">選取 [ **產生新的動畫] 剪輯**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-334">Select **Generate New Animation Clips**</span></span>

    ![產生新的動畫剪輯](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![在視覺化檢視和互動式元素元件中顯示產生的動畫剪輯](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="ea1cc-337">在焦點狀態容器中，選取 [**新增目標**]</span><span class="sxs-lookup"><span data-stu-id="ea1cc-337">In the Focus state container, select **Add Target**</span></span>

    ![正在加入狀態視覺化目標](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="ea1cc-339">將目前的遊戲物件拖曳至目標欄位</span><span class="sxs-lookup"><span data-stu-id="ea1cc-339">Drag the current game object to the target field</span></span> 

    ![設定狀態視覺化目標](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="ea1cc-341">開啟 Cube Animatable 屬性 foldout</span><span class="sxs-lookup"><span data-stu-id="ea1cc-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="ea1cc-342">選取 [Animatable] 屬性下拉式功能表，然後選取 [**色彩**]。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![設定狀態視覺化色彩](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="ea1cc-344">選取 **[新增色彩 Animatable] 屬性**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-344">Select **Add the Color Animatable Property**</span></span>

    ![選取 [視覺化] 色彩 animatable 屬性](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="ea1cc-346">選擇色彩</span><span class="sxs-lookup"><span data-stu-id="ea1cc-346">Choose a Color</span></span> 

    ![從色輪選擇視覺化色彩](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="ea1cc-348">按下 [播放] 並觀察過渡色彩變更</span><span class="sxs-lookup"><span data-stu-id="ea1cc-348">Press play and observe the transitional color change</span></span>

    ![使用虛擬手互動的過渡色彩變更範例](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="ea1cc-350">Animatable 屬性</span><span class="sxs-lookup"><span data-stu-id="ea1cc-350">Animatable Properties</span></span>

<span data-ttu-id="ea1cc-351">Animatable 屬性的主要目的是簡化動畫剪輯主要畫面格的設定。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="ea1cc-352">如果使用者熟悉 Unity 動畫系統，而且想要在產生的動畫剪輯上直接設定主要畫面格，則可以直接將 Animatable 屬性加入至目標物件，並在 Unity 的動畫視窗中開啟剪輯， (Windows > 動畫 > 動畫) 。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="ea1cc-353">如果使用動畫的 Animatable 屬性，則曲線類型會設定為 EaseInOut。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="ea1cc-354">**目前的 Animatable 屬性：**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="ea1cc-355">調整位移</span><span class="sxs-lookup"><span data-stu-id="ea1cc-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="ea1cc-356">位置位移</span><span class="sxs-lookup"><span data-stu-id="ea1cc-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="ea1cc-357">色彩</span><span class="sxs-lookup"><span data-stu-id="ea1cc-357">Color</span></span>](#color)
- [<span data-ttu-id="ea1cc-358">著色器色彩</span><span class="sxs-lookup"><span data-stu-id="ea1cc-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="ea1cc-359">著色器浮點數</span><span class="sxs-lookup"><span data-stu-id="ea1cc-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="ea1cc-360">著色器向量</span><span class="sxs-lookup"><span data-stu-id="ea1cc-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="ea1cc-361">調整位移</span><span class="sxs-lookup"><span data-stu-id="ea1cc-361">Scale Offset</span></span>

<span data-ttu-id="ea1cc-362">Scale Offset Animatable 屬性會取得物件目前的小數位數，並加入已定義的位移。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![使用虛擬手互動調整位移](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="ea1cc-364">位置位移</span><span class="sxs-lookup"><span data-stu-id="ea1cc-364">Position Offset</span></span>

<span data-ttu-id="ea1cc-365">Position Offset Animatable 屬性會取得物件的目前位置，並加入已定義的位移。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![使用虛擬手互動的位置位移](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="ea1cc-367">Color</span><span class="sxs-lookup"><span data-stu-id="ea1cc-367">Color</span></span>

<span data-ttu-id="ea1cc-368">如果材質有主要色彩屬性，Color Animatable 屬性代表材質的主要色彩。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="ea1cc-369">這個屬性會將 `material._Color` 屬性動畫。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-369">This property animates the `material._Color` property.</span></span>

![使用虛擬手互動的焦點色彩變更](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="ea1cc-371">著色器色彩</span><span class="sxs-lookup"><span data-stu-id="ea1cc-371">Shader Color</span></span>

<span data-ttu-id="ea1cc-372">著色器色彩 Animatable 屬性是指 Color 類型的著色器屬性。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="ea1cc-373">所有著色器屬性都需要屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="ea1cc-374">下列 gif 示範如何以動畫顯示名稱為 Fill_Color 但不是主要材質色彩的著色器色彩屬性。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="ea1cc-375">觀察材質偵測器中的變更值。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-375">Observe the changing values in the material inspector.</span></span>

![使用虛擬手互動的陰影色彩](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="ea1cc-377">著色器浮點數</span><span class="sxs-lookup"><span data-stu-id="ea1cc-377">Shader Float</span></span>

<span data-ttu-id="ea1cc-378">著色器 Float Animatable 屬性是指 Float 類型的著色器屬性。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="ea1cc-379">所有著色器屬性都需要屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="ea1cc-380">在下 gif 中，觀察材質屬性之材質偵測器中的變更值。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![具有虛擬手互動的著色器浮點數](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="ea1cc-382">著色器向量</span><span class="sxs-lookup"><span data-stu-id="ea1cc-382">Shader Vector</span></span>

<span data-ttu-id="ea1cc-383">著色器向量 Animatable 屬性指的是 Vector4 類型的著色器屬性。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="ea1cc-384">所有著色器屬性都需要屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="ea1cc-385">在下 gif 中，觀察 [材質偵測器] 中 [並排 (主要 Tex_ST) ] 屬性的變更值。</span><span class="sxs-lookup"><span data-stu-id="ea1cc-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![具有虛擬手互動的著色器向量](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="ea1cc-387">如何尋找 Animatable 著色器屬性名稱</span><span class="sxs-lookup"><span data-stu-id="ea1cc-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="ea1cc-388">導覽至視窗 > 動畫 > 動畫</span><span class="sxs-lookup"><span data-stu-id="ea1cc-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="ea1cc-389">確定已在階層中選取具有狀態視覺化的物件</span><span class="sxs-lookup"><span data-stu-id="ea1cc-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="ea1cc-390">在動畫視窗中選取任何動畫剪輯</span><span class="sxs-lookup"><span data-stu-id="ea1cc-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="ea1cc-391">選取 [ **新增屬性**]，開啟 [網狀轉譯器 foldout</span><span class="sxs-lookup"><span data-stu-id="ea1cc-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![在 Animator 視窗中新增動畫屬性](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="ea1cc-393">此清單包含所有 Animatable 屬性名稱的名稱</span><span class="sxs-lookup"><span data-stu-id="ea1cc-393">This list contains the names of all the Animatable property names</span></span> 

    ![Animator 視窗中的網格轉譯器動畫屬性](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="ea1cc-395">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea1cc-395">See also</span></span>

- [<span data-ttu-id="ea1cc-396">**按鈕**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-396">**Buttons**</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="ea1cc-397">**界限控制項**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-397">**Bounds Control**</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="ea1cc-398">**方格物件集合**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-398">**Grid Object Collection**</span></span>](../ux-building-blocks/object-collection.md)
- [<span data-ttu-id="ea1cc-399">**RadialView 規劃**</span><span class="sxs-lookup"><span data-stu-id="ea1cc-399">**RadialView Solver**</span></span>](../ux-building-blocks/solvers/solver.md)
