---
title: 互動
description: MRTK 中的互動腳本元件總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、互動、Events、
ms.openlocfilehash: f6e13d893e89bac49abdfc7f565652cc3940109d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780146"
---
# <a name="interactable"></a><span data-ttu-id="6c131-104">互動</span><span class="sxs-lookup"><span data-stu-id="6c131-104">Interactable</span></span>

![互動](../images/interactable/InteractableExamples.png)

<span data-ttu-id="6c131-106">[`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable)元件是一個全功能的容器，可讓任何物件輕鬆地 *互動* 並回應輸入。</span><span class="sxs-lookup"><span data-stu-id="6c131-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="6c131-107">互動可作為所有輸入類型的全部捕捉，包括觸控、手寫光線、語音等，以及將這些互動加入 [事件](#events) 和 [視覺主題](../visualthemes.md) 回應中。</span><span class="sxs-lookup"><span data-stu-id="6c131-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](../visualthemes.md) responses.</span></span> <span data-ttu-id="6c131-108">此元件提供簡單的方式來建立按鈕、變更具有焦點的物件色彩等等。</span><span class="sxs-lookup"><span data-stu-id="6c131-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="6c131-109">如何設定互動</span><span class="sxs-lookup"><span data-stu-id="6c131-109">How to configure Interactable</span></span>

<span data-ttu-id="6c131-110">元件允許三個主要的設定區段：</span><span class="sxs-lookup"><span data-stu-id="6c131-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="6c131-111">一般輸入設定</span><span class="sxs-lookup"><span data-stu-id="6c131-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="6c131-112">以多個 Gameobject 為目標的[視覺主題](../VisualThemes.md)</span><span class="sxs-lookup"><span data-stu-id="6c131-112">[Visual Themes](../VisualThemes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="6c131-113">事件處理常式</span><span class="sxs-lookup"><span data-stu-id="6c131-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="6c131-114">一般輸入設定</span><span class="sxs-lookup"><span data-stu-id="6c131-114">General input settings</span></span>

![一般互動設定](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="6c131-116">**狀態**</span><span class="sxs-lookup"><span data-stu-id="6c131-116">**States**</span></span>

<span data-ttu-id="6c131-117">*狀態* 是一個 [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 參數，可定義 [互動設定檔](#interactable-profiles) 和 [視覺化主題](../VisualThemes.md)的互動階段，例如按下或觀察到。</span><span class="sxs-lookup"><span data-stu-id="6c131-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](../VisualThemes.md).</span></span>

<span data-ttu-id="6c131-118">**DefaultInteractableStates** (資產/MRTK/SDK/FEATURES/UX/互動/州/DefaultInteractableStates. 資產) 隨附于現成的 MRTK，而且是 *互動* 元件的預設參數。</span><span class="sxs-lookup"><span data-stu-id="6c131-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![偵測器中的狀態 ScriptableObject 範例](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="6c131-120">*DefaultInteractableStates* 資產包含四種狀態，並利用 [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) 狀態模型執行。</span><span class="sxs-lookup"><span data-stu-id="6c131-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="6c131-121">**預設值**：沒有任何專案發生，這是最隔離的基底狀態。</span><span class="sxs-lookup"><span data-stu-id="6c131-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="6c131-122">**焦點**：物件正在指向。</span><span class="sxs-lookup"><span data-stu-id="6c131-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="6c131-123">這是單一狀態，目前未設定任何其他狀態，但會將預設值設為預設值。</span><span class="sxs-lookup"><span data-stu-id="6c131-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="6c131-124">**按**：正在指向物件，且正在按下按鈕或手。</span><span class="sxs-lookup"><span data-stu-id="6c131-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="6c131-125">按下狀態會排列預設和焦點。</span><span class="sxs-lookup"><span data-stu-id="6c131-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="6c131-126">此狀態也會被設定為實體按下的狀態。</span><span class="sxs-lookup"><span data-stu-id="6c131-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="6c131-127">**已停用**：此按鈕不應該是互動式的，且視覺效果的意見反應會讓使用者知道是否因為某些原因而無法使用這個按鈕。</span><span class="sxs-lookup"><span data-stu-id="6c131-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="6c131-128">理論上，停用的狀態可能會包含所有其他狀態，但當啟用時，已停用的狀態就會優先于所有其他狀態。</span><span class="sxs-lookup"><span data-stu-id="6c131-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="6c131-129">視清單中的順序而定，會將位值 ( # ) 指派給狀態。</span><span class="sxs-lookup"><span data-stu-id="6c131-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="6c131-130">通常建議您在建立 *互動* 元件時，利用 **DefaultInteractableStates** (資產/MRTK/SDK/Features/UX/互動/州名/DefaultInteractableStates 資產) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="6c131-131">不過，有17種可用來驅動主題的互動狀態，但有些則是由其他元件所驅動。</span><span class="sxs-lookup"><span data-stu-id="6c131-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="6c131-132">以下是具有內建功能的清單。</span><span class="sxs-lookup"><span data-stu-id="6c131-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="6c131-133">造訪：已按一下互動。</span><span class="sxs-lookup"><span data-stu-id="6c131-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="6c131-134">切換：按鈕處於切換狀態，或維度索引為奇數。</span><span class="sxs-lookup"><span data-stu-id="6c131-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="6c131-135">手勢：已按下手或控制器，且已從原始位置移動。</span><span class="sxs-lookup"><span data-stu-id="6c131-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="6c131-136">VoiceCommand：用來觸發互動的語音命令。</span><span class="sxs-lookup"><span data-stu-id="6c131-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="6c131-137">PhysicalTouch：目前偵測到觸控輸入，用於 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 啟用。</span><span class="sxs-lookup"><span data-stu-id="6c131-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="6c131-138">抓取：手中目前已抓取物件的界限，用 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 來啟用</span><span class="sxs-lookup"><span data-stu-id="6c131-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="6c131-139">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="6c131-139">**Enabled**</span></span>

<span data-ttu-id="6c131-140">切換互動是否將開始啟用。</span><span class="sxs-lookup"><span data-stu-id="6c131-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="6c131-141">這會對應至程式 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 代碼中的。</span><span class="sxs-lookup"><span data-stu-id="6c131-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="6c131-142">*互動的* enabled 屬性與透過 GameObject/Component 設定的 enabled 屬性不同 (例如</span><span class="sxs-lookup"><span data-stu-id="6c131-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="6c131-143">Advanced.field.setactive 等) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-143">SetActive etc).</span></span> <span data-ttu-id="6c131-144">停用 GameObject 或 *互動* MonoBehaviour 將會停用類別中的所有專案，包括輸入、視覺主題、事件等等。停用 via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 將會停用大部分的輸入處理，並重設相關的輸入狀態。</span><span class="sxs-lookup"><span data-stu-id="6c131-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="6c131-145">不過，此類別仍會執行每個畫面格，並接收將會忽略的輸入事件。</span><span class="sxs-lookup"><span data-stu-id="6c131-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="6c131-146">這適用于將互動顯示為已停用狀態，可透過視覺化主題來完成。</span><span class="sxs-lookup"><span data-stu-id="6c131-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="6c131-147">其中一個常見的範例是 [提交] 按鈕，等候所有必要的輸入欄位都完成。</span><span class="sxs-lookup"><span data-stu-id="6c131-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="6c131-148">**輸入動作**</span><span class="sxs-lookup"><span data-stu-id="6c131-148">**Input Actions**</span></span>

<span data-ttu-id="6c131-149">從 *互動* 元件應該回應的輸入設定或控制器對應設定檔中，選取 [輸入動作](../input/InputActions.md)。</span><span class="sxs-lookup"><span data-stu-id="6c131-149">Select the [input action](../input/InputActions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="6c131-150">您可以在程式碼中，透過程式碼來設定這個屬性 [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="6c131-151">**IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="6c131-151">**IsGlobal**</span></span>

<span data-ttu-id="6c131-152">若為 true，則會將元件標示為所選 [輸入動作](../input/InputActions.md)的全域輸入接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6c131-152">If true, this will mark the component as a global input listener for the selected [input action](../input/InputActions.md).</span></span> <span data-ttu-id="6c131-153">預設行為是 false，它會將輸入限制為只有這個 *互動* 碰撞/GameObject。</span><span class="sxs-lookup"><span data-stu-id="6c131-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="6c131-154">您可以在程式碼中，透過程式碼來設定這個屬性 [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="6c131-155">**語音命令**</span><span class="sxs-lookup"><span data-stu-id="6c131-155">**Speech Command**</span></span>

<span data-ttu-id="6c131-156">[語音命令](../input/Speech.md)，從 MRTK 語音命令設定檔，用來觸發語音互動的 OnClick 事件。</span><span class="sxs-lookup"><span data-stu-id="6c131-156">[Speech command](../input/Speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="6c131-157">您可以在程式碼中，透過程式碼來設定這個屬性 [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="6c131-158">**需要焦點**</span><span class="sxs-lookup"><span data-stu-id="6c131-158">**Requires Focus**</span></span>

<span data-ttu-id="6c131-159">若為 true，則只有在已有指標的焦點時，voice 命令才會啟用 *互動* 。</span><span class="sxs-lookup"><span data-stu-id="6c131-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="6c131-160">如果為 false，則 *互動* 將作為所選語音命令的全域接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6c131-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="6c131-161">預設行為是 true，因為多個全域語音接聽程式很難在場景中組織。</span><span class="sxs-lookup"><span data-stu-id="6c131-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="6c131-162">您可以在程式碼中，透過程式碼來設定這個屬性 [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="6c131-163">**選取模式**</span><span class="sxs-lookup"><span data-stu-id="6c131-163">**Selection Mode**</span></span>

<span data-ttu-id="6c131-164">這個屬性會定義選取邏輯。</span><span class="sxs-lookup"><span data-stu-id="6c131-164">This property defines the selection logic.</span></span> <span data-ttu-id="6c131-165">當您按一下 *互動* 時，它會逐一查看至下一個 *維度* 層級。</span><span class="sxs-lookup"><span data-stu-id="6c131-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="6c131-166">*維度* 類似于排名，並定義輸入以外的狀態 (例如</span><span class="sxs-lookup"><span data-stu-id="6c131-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="6c131-167">焦點，按 etc) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-167">focus, press etc).</span></span> <span data-ttu-id="6c131-168">它們適用于定義切換狀態或與按鈕相關聯的其他多重排名狀態。</span><span class="sxs-lookup"><span data-stu-id="6c131-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="6c131-169">目前的維度層級是由追蹤 `Interactable.DimensionIndex` 。</span><span class="sxs-lookup"><span data-stu-id="6c131-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="6c131-170">可用的選取模式如下：</span><span class="sxs-lookup"><span data-stu-id="6c131-170">The selection modes available are:</span></span>

* <span data-ttu-id="6c131-171">**按鈕**  - *維度*= 1，簡單的可按式 *互動*</span><span class="sxs-lookup"><span data-stu-id="6c131-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="6c131-172">**切換**  - *維度*= 2，*互動* 會 *在* / *關閉* 狀態時交替</span><span class="sxs-lookup"><span data-stu-id="6c131-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="6c131-173">**多重維度**  - *維度*>= 3，每次按一下會增加目前的維度層級 + 1。</span><span class="sxs-lookup"><span data-stu-id="6c131-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="6c131-174">適用于定義清單的按鈕狀態等等。</span><span class="sxs-lookup"><span data-stu-id="6c131-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="6c131-175">*互動* 也可讓您定義每個 *維度* 的多個主題。</span><span class="sxs-lookup"><span data-stu-id="6c131-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="6c131-176">例如，當 *SelectionMode = 切換* 時，可以在 *取消選取\*\*互動* 時套用一個主題，並在 *選取* 元件時套用另一個主題。</span><span class="sxs-lookup"><span data-stu-id="6c131-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="6c131-177">您可以在執行時間透過來查詢目前的選取模式 [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="6c131-178">您可以藉由將  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) 屬性設定為符合所需的功能，來在執行時間更新模式。</span><span class="sxs-lookup"><span data-stu-id="6c131-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="6c131-179">此外，目前的維度適用于 *切換* 和 *多維度* 模式，可透過來存取 [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="6c131-180">互動設定檔</span><span class="sxs-lookup"><span data-stu-id="6c131-180">Interactable profiles</span></span>

<span data-ttu-id="6c131-181">*設定檔* 是在 GameObject 和 [視覺化主題](../VisualThemes.md)之間建立關聯性的專案。</span><span class="sxs-lookup"><span data-stu-id="6c131-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](../VisualThemes.md).</span></span> <span data-ttu-id="6c131-182">設定檔會定義當 [狀態變更發生](#general-input-settings)時，主題會操作哪些內容。</span><span class="sxs-lookup"><span data-stu-id="6c131-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="6c131-183">主題的運作方式很類似材質。</span><span class="sxs-lookup"><span data-stu-id="6c131-183">Themes work a lot like materials.</span></span> <span data-ttu-id="6c131-184">它們是可編寫腳本的物件，其中包含將根據目前狀態指派給物件的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="6c131-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="6c131-185">主題也可以重複使用，並可跨多個 *互動* UX 物件指派。</span><span class="sxs-lookup"><span data-stu-id="6c131-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="6c131-186">**損毀時重設**</span><span class="sxs-lookup"><span data-stu-id="6c131-186">**Reset On Destroy**</span></span>

<span data-ttu-id="6c131-187">視覺主題會修改目標 GameObject 上的各種屬性，取決於所選取的主題引擎類別和類型而定。</span><span class="sxs-lookup"><span data-stu-id="6c131-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="6c131-188">如果終結互動元件時，在終結時 *重設* 為 true，元件會將所有修改過的屬性從作用中主題重設為其原始值。</span><span class="sxs-lookup"><span data-stu-id="6c131-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="6c131-189">否則，當終結時，互動元件會保留任何修改過的屬性。</span><span class="sxs-lookup"><span data-stu-id="6c131-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="6c131-190">在後者的情況下，除非由另一個外部元件變更，否則值的最後一個狀態將會保留。</span><span class="sxs-lookup"><span data-stu-id="6c131-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="6c131-191">預設為 false。</span><span class="sxs-lookup"><span data-stu-id="6c131-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile Themes">

## <a name="events"></a><span data-ttu-id="6c131-192">事件</span><span class="sxs-lookup"><span data-stu-id="6c131-192">Events</span></span>

<span data-ttu-id="6c131-193">每個 *互動* 元件都有一個 *OnClick* 事件，此事件會在只選取元件時引發。</span><span class="sxs-lookup"><span data-stu-id="6c131-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="6c131-194">不過， *互動* 可以用來偵測除了 *OnClick* 以外的輸入事件。</span><span class="sxs-lookup"><span data-stu-id="6c131-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="6c131-195">按一下 [ *新增事件* ] 按鈕，以加入新的事件接收器定義類型。</span><span class="sxs-lookup"><span data-stu-id="6c131-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="6c131-196">新增之後，請選取所需的事件種類。</span><span class="sxs-lookup"><span data-stu-id="6c131-196">Once added, select the type of Event desired.</span></span>

![事件範例](../images/interactable/Events.png)<span data-ttu-id="6c131-198">)</span><span class="sxs-lookup"><span data-stu-id="6c131-198">)</span></span>

<span data-ttu-id="6c131-199">有不同類型的事件接收器可回應不同類型的輸入。</span><span class="sxs-lookup"><span data-stu-id="6c131-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="6c131-200">MRTK 隨附了下列一組現成的接收者。</span><span class="sxs-lookup"><span data-stu-id="6c131-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="6c131-201">您可以建立擴充的新類別來建立自訂接收器 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![事件切換接收器範例](../images/interactable/Event_toggle.png)

<span data-ttu-id="6c131-203">*切換事件接收器的範例*</span><span class="sxs-lookup"><span data-stu-id="6c131-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="6c131-204">互動接收者</span><span class="sxs-lookup"><span data-stu-id="6c131-204">Interactable receivers</span></span>

 <span data-ttu-id="6c131-205">元件可讓您在 [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) 來源 *互動* 元件之外定義事件。</span><span class="sxs-lookup"><span data-stu-id="6c131-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="6c131-206">*InteractableReceiver* 會接聽由另一個 *互動* 所引發的已篩選事件種類。</span><span class="sxs-lookup"><span data-stu-id="6c131-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="6c131-207">如果未直接指派 *互動* 屬性，則 [ *搜尋範圍* ] 屬性會定義 *InteractableReceiver* 接聽事件的方向，此方向本身、父系或子 GameObject。</span><span class="sxs-lookup"><span data-stu-id="6c131-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="6c131-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) 以類似的方式運作，但符合相符事件的清單。</span><span class="sxs-lookup"><span data-stu-id="6c131-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable Receiver">

### <a name="create-custom-events"></a><span data-ttu-id="6c131-209">建立自訂事件</span><span class="sxs-lookup"><span data-stu-id="6c131-209">Create custom events</span></span>

<span data-ttu-id="6c131-210">就像 [視覺主題](../VisualThemes.md#custom-theme-engines)一樣，可以擴充事件以偵測任何狀態模式或公開功能。</span><span class="sxs-lookup"><span data-stu-id="6c131-210">Like [Visual Themes](../VisualThemes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="6c131-211">您可以透過兩種主要方式來建立自訂事件：</span><span class="sxs-lookup"><span data-stu-id="6c131-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="6c131-212">擴充 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 類別以建立自訂事件，此事件會顯示在事件種類的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="6c131-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="6c131-213">依預設會提供 Unity 事件，但是可以加入其他 Unity 事件，也可以設定事件來隱藏 Unity 事件。</span><span class="sxs-lookup"><span data-stu-id="6c131-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="6c131-214">這項功能可讓設計工具與專案的工程師合作，以建立設計工具可以在編輯器中設定的自訂事件。</span><span class="sxs-lookup"><span data-stu-id="6c131-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="6c131-215">擴充 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) 類別以建立可位於 *互動* 或另一個物件上的完全自訂事件元件。</span><span class="sxs-lookup"><span data-stu-id="6c131-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="6c131-216">[`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)會參考 *互動* 來偵測狀態變更。</span><span class="sxs-lookup"><span data-stu-id="6c131-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="6c131-217">擴充的範例 `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="6c131-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="6c131-218">[`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI)類別會顯示有關 *互動* 的狀態資訊，以及如何建立自訂事件接收器的範例。</span><span class="sxs-lookup"><span data-stu-id="6c131-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="6c131-219">建立自訂事件接收器時，下列方法可用於覆寫/執行。</span><span class="sxs-lookup"><span data-stu-id="6c131-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="6c131-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 是可用於偵測狀態模式/轉換的抽象方法。</span><span class="sxs-lookup"><span data-stu-id="6c131-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="6c131-221">此外， [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 和 [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 方法適用于在選取 *互動* 時建立自訂事件邏輯。</span><span class="sxs-lookup"><span data-stu-id="6c131-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

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

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="6c131-222">在偵測器中顯示自訂事件接收器欄位</span><span class="sxs-lookup"><span data-stu-id="6c131-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="6c131-223">*ReceiverBase* 腳本會使用 [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) 屬性，在偵測器中公開自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="6c131-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="6c131-224">以下是 Vector3 的範例，其中包含工具提示和標籤資訊的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="6c131-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="6c131-225">當選取了 *互動* GameObject，且已加入相關聯的 *事件接收器* 類型時，這個屬性會在偵測器中顯示為可設定。</span><span class="sxs-lookup"><span data-stu-id="6c131-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="6c131-226">如何使用互動</span><span class="sxs-lookup"><span data-stu-id="6c131-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="6c131-227">建立簡單的按鈕</span><span class="sxs-lookup"><span data-stu-id="6c131-227">Building a simple button</span></span>

<span data-ttu-id="6c131-228">您可以藉由將 *互動* 元件新增至設定為接收輸入事件的 GameObject，來建立一個簡單的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6c131-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="6c131-229">它可能會在其上產生碰撞，或在子系上具有碰撞來接收輸入。</span><span class="sxs-lookup"><span data-stu-id="6c131-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="6c131-230">如果使用 *互動* 搭配以 Unity UI 為基礎的 gameobject，它應該位於 Canvas GameObject 下。</span><span class="sxs-lookup"><span data-stu-id="6c131-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="6c131-231">藉由建立新的設定檔、指派 GameObject 本身以及建立新的主題，讓按鈕一步更進一步。</span><span class="sxs-lookup"><span data-stu-id="6c131-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="6c131-232">此外，您也可以使用 *OnClick* 事件進行某些動作。</span><span class="sxs-lookup"><span data-stu-id="6c131-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="6c131-233">讓 [按鈕 pressable](Button.md) 需要 [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 元件。</span><span class="sxs-lookup"><span data-stu-id="6c131-233">Making a [button pressable](Button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="6c131-234">此外，還 [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) 需要元件才能將事件按到 *互動* 元件。</span><span class="sxs-lookup"><span data-stu-id="6c131-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="6c131-235">建立切換和多維度按鈕</span><span class="sxs-lookup"><span data-stu-id="6c131-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="6c131-236">切換按鈕</span><span class="sxs-lookup"><span data-stu-id="6c131-236">Toggle button</span></span>

<span data-ttu-id="6c131-237">若要讓按鈕可以切換，請將欄位變更 [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 為 [類型] `Toggle` 。</span><span class="sxs-lookup"><span data-stu-id="6c131-237">To make a button Toggle-able, change the the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="6c131-238">在 [ *設定檔* ] 區段中，會針對 *互動* 切換時使用的每個設定檔新增切換的主題。</span><span class="sxs-lookup"><span data-stu-id="6c131-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="6c131-239">當 [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 設定為切換時， *IsToggled* 核取方塊可以用來在執行時間初始化時設定控制項的預設值。</span><span class="sxs-lookup"><span data-stu-id="6c131-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="6c131-240">*CanSelect* 表示 *互動* 可以從 *off* 移至 *開啟* ，而 *CanDeselect* 表示反向。</span><span class="sxs-lookup"><span data-stu-id="6c131-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![設定檔切換視覺主題範例](../images/interactable/Profile_toggle.png)

<span data-ttu-id="6c131-242">開發人員可以利用 [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 和 [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 介面，透過程式碼取得/設定 *互動* 的切換狀態。</span><span class="sxs-lookup"><span data-stu-id="6c131-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="6c131-243">切換按鈕集合</span><span class="sxs-lookup"><span data-stu-id="6c131-243">Toggle button collection</span></span>

<span data-ttu-id="6c131-244">通常會有一份切換按鈕清單，其中只有一個可在任何指定時間處於作用中狀態，也稱為星形組或選項按鈕等等。</span><span class="sxs-lookup"><span data-stu-id="6c131-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="6c131-245">使用 [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) 元件來啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="6c131-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="6c131-246">此控制項可確保在任何指定時間都只會有一個 *互動* 切換。</span><span class="sxs-lookup"><span data-stu-id="6c131-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="6c131-247">*RadialSet* (資產/MRTK/SDK/FEATURES/UX/互動/Prefabs/RadialSet. 預製專案) 也是現成的絕佳起點。</span><span class="sxs-lookup"><span data-stu-id="6c131-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="6c131-248">若要建立自訂放射狀按鈕群組：</span><span class="sxs-lookup"><span data-stu-id="6c131-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="6c131-249">建立多個 *互動* gameobject/按鈕</span><span class="sxs-lookup"><span data-stu-id="6c131-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="6c131-250">使用 *SelectionMode* = 切換、 *CanSelect* = true 和 *CanDeselect* = false 來設定每個 *互動*</span><span class="sxs-lookup"><span data-stu-id="6c131-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="6c131-251">針對所有 *Interactables* 建立空白的父 GameObject，然後新增 *InteractableToggleCollection* 元件</span><span class="sxs-lookup"><span data-stu-id="6c131-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="6c131-252">將所有 *Interactables* 新增至 *InteractableToggleCollection* 上的 *ToggleList*</span><span class="sxs-lookup"><span data-stu-id="6c131-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="6c131-253">設定 *InteractableToggleCollection CurrentIndex* 屬性，以判斷在開始時預設選取的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6c131-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle Collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="6c131-254">多維度按鈕</span><span class="sxs-lookup"><span data-stu-id="6c131-254">Multi-dimensional button</span></span>

<span data-ttu-id="6c131-255">多重維度選取模式可用來建立連續按鈕，或具有兩個以上步驟的按鈕，例如以三個值控制速度、Fast (1x) 、更快 (2x) 或最快 (3 倍) 。</span><span class="sxs-lookup"><span data-stu-id="6c131-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="6c131-256">當維度是數值時，最多可以加入9個主題，以針對每個步驟使用不同的主題來控制每個速度設定之按鈕的文字標籤或紋理。</span><span class="sxs-lookup"><span data-stu-id="6c131-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="6c131-257">每個 click 事件都會 `DimensionIndex` 在執行時間前移1，直到 `Dimensions` 達到該值為止。</span><span class="sxs-lookup"><span data-stu-id="6c131-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="6c131-258">然後迴圈將重設為0。</span><span class="sxs-lookup"><span data-stu-id="6c131-258">Then the cycle will reset to 0.</span></span>

![多維度設定檔範例](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="6c131-260">開發人員可以評估， [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 以判斷哪個維度目前為使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="6c131-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="6c131-261">在執行時間建立互動</span><span class="sxs-lookup"><span data-stu-id="6c131-261">Create Interactable at runtime</span></span>

<span data-ttu-id="6c131-262">*互動* 可在執行時間輕鬆地新增至任何 GameObject。</span><span class="sxs-lookup"><span data-stu-id="6c131-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="6c131-263">下列範例示範如何指派具有 [視覺效果主題](../visualthemes.md)的設定檔。</span><span class="sxs-lookup"><span data-stu-id="6c131-263">The following example demonstrates how to assign a profile with a [visual theme](../visualthemes.md).</span></span>

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

### <a name="interactable-events-via-code"></a><span data-ttu-id="6c131-264">透過程式碼互動事件</span><span class="sxs-lookup"><span data-stu-id="6c131-264">Interactable events via code</span></span>

<span data-ttu-id="6c131-265">您可以使用下列範例，透過程式碼將動作新增至基底 [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) 事件。</span><span class="sxs-lookup"><span data-stu-id="6c131-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="6c131-266">使用函式 [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 在執行時間動態加入事件接收器。</span><span class="sxs-lookup"><span data-stu-id="6c131-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="6c131-267">下列範例程式碼示範如何新增 [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，以接聽焦點的進入/離開，以及定義事件實例引發時要執行的動作程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c131-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="6c131-268">下列範例程式碼示範如何新增 [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，以在切換能力 *Interactables* 上接聽選取/取消選取的狀態轉換，以及定義事件實例引發時要執行的動作程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c131-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6c131-269">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c131-269">See also</span></span>

* [<span data-ttu-id="6c131-270">視覺主題</span><span class="sxs-lookup"><span data-stu-id="6c131-270">Visual Themes</span></span>](../VisualThemes.md)
* [<span data-ttu-id="6c131-271">輸入動作</span><span class="sxs-lookup"><span data-stu-id="6c131-271">Input Actions</span></span>](../input/InputActions.md)
* [<span data-ttu-id="6c131-272">語音命令</span><span class="sxs-lookup"><span data-stu-id="6c131-272">Speech Commands</span></span>](../input/Speech.md)
* [<span data-ttu-id="6c131-273">按鈕</span><span class="sxs-lookup"><span data-stu-id="6c131-273">Buttons</span></span>](Button.md)
* [<span data-ttu-id="6c131-274">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="6c131-274">MRTK Standard Shader</span></span>](../rendering/MRTKStandardShader.md)
