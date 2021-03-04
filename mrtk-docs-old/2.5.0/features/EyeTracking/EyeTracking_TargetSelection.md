---
title: EyeTracking_TargetSelection
description: 如何在 MRTK 中存取眼睛資料和眼睛的特定事件以選取目標
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: 7c3b15fc1734564d26a64812fd1245834294244b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780609"
---
# <a name="eye-supported-target-selection"></a><span data-ttu-id="c41ee-104">目視支援的目標選取範圍</span><span class="sxs-lookup"><span data-stu-id="c41ee-104">Eye-supported target selection</span></span>

![MRTK](../Images/EyeTracking/mrtk_et_targetselect.png)

<span data-ttu-id="c41ee-106">此頁面討論存取眼睛資料的不同選項，以及在 MRTK 中選取目標的眼睛特定事件。</span><span class="sxs-lookup"><span data-stu-id="c41ee-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="c41ee-107">目視追蹤可讓您快速輕鬆地選擇目標，並使用與使用者所查看的內容有關的資訊組合，例如「 _手追蹤_ 」和「 _語音命令_」：</span><span class="sxs-lookup"><span data-stu-id="c41ee-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="c41ee-108">& 說「 _Select_ 」 (預設的語音命令) </span><span class="sxs-lookup"><span data-stu-id="c41ee-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="c41ee-109">& _說 (_ 自訂語音命令的「分裂」或「 _Pop_ 」) </span><span class="sxs-lookup"><span data-stu-id="c41ee-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="c41ee-110">查看 & 藍牙按鈕</span><span class="sxs-lookup"><span data-stu-id="c41ee-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="c41ee-111">& 縮小 (，也就是將您的手放在最前面，並將您的 thumb 和索引指標結合在一起) </span><span class="sxs-lookup"><span data-stu-id="c41ee-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="c41ee-112">請注意，若要這樣做，必須 [停用光片](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="c41ee-112">Please note that for this to work, the [hand rays need to be disabled](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="c41ee-113">若要使用眼睛選取全像攝影內容，有幾個選項可供選擇：</span><span class="sxs-lookup"><span data-stu-id="c41ee-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="c41ee-114">**1. 使用主要焦點指標：**</span><span class="sxs-lookup"><span data-stu-id="c41ee-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="c41ee-115">這可以被視為您優先的資料指標。</span><span class="sxs-lookup"><span data-stu-id="c41ee-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="c41ee-116">根據預設，如果手中的手中，這會是手中的光線。</span><span class="sxs-lookup"><span data-stu-id="c41ee-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="c41ee-117">如果沒有手中，則優先順序指標會是 head 或眼睛。</span><span class="sxs-lookup"><span data-stu-id="c41ee-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="c41ee-118">因此，請注意，如果使用了手的光線，根據目前的設計 head 或眼睛會隱藏為游標輸入。</span><span class="sxs-lookup"><span data-stu-id="c41ee-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="c41ee-119">例如：</span><span class="sxs-lookup"><span data-stu-id="c41ee-119">For example:</span></span>

<span data-ttu-id="c41ee-120">使用者想要選取一個遙遠的全像全像全公司。</span><span class="sxs-lookup"><span data-stu-id="c41ee-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="c41ee-121">如果您是開發人員，您想要提供彈性的解決方案，讓使用者能夠在各種情況下達成這項工作：</span><span class="sxs-lookup"><span data-stu-id="c41ee-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="c41ee-122">往上移至按鈕並進行</span><span class="sxs-lookup"><span data-stu-id="c41ee-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="c41ee-123">從距離查看並說出「選取」</span><span class="sxs-lookup"><span data-stu-id="c41ee-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="c41ee-124">使用手光來鎖定按鈕，並在此情況下執行縮小時，最具彈性的解決方案是使用主要焦點處理常式，因為當目前優先排列的主要焦點指標觸發事件時，它會通知您。</span><span class="sxs-lookup"><span data-stu-id="c41ee-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="c41ee-125">請注意，如果已啟用 [手片]，則會在一開始觀看時立即停用 head 或眼睛的視覺焦點指標。</span><span class="sxs-lookup"><span data-stu-id="c41ee-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c41ee-126">請注意，如果已啟用 [手片]，則會在一開始觀看時立即停用 head 或眼睛的視覺焦點指標。</span><span class="sxs-lookup"><span data-stu-id="c41ee-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="c41ee-127">如果您想要支援「 [_外觀和_ 縮小」的互動，您必須停用手光](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray)。</span><span class="sxs-lookup"><span data-stu-id="c41ee-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="c41ee-128">在我們的眼睛追蹤範例場景中，我們停用了光線，以允許使用眼睛 + 手運動展示更豐富的互動-請參閱，以瞭解 [支援的視覺定位](EyeTracking_Positioning.md)。</span><span class="sxs-lookup"><span data-stu-id="c41ee-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](EyeTracking_Positioning.md).</span></span>

[<span data-ttu-id="c41ee-129">**2. 同時使用眼睛焦點和手光線：**</span><span class="sxs-lookup"><span data-stu-id="c41ee-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="c41ee-130">在某些情況下，您可能會想要更明確地瞭解哪些類型的焦點指標可觸發特定事件，並允許同時使用多個互動技巧。</span><span class="sxs-lookup"><span data-stu-id="c41ee-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="c41ee-131">例如：在您的應用程式中，使用者可以使用最多的光線來操作一些全像的機械設定，例如，抓住並保存一些遠處的全像攝影引擎零件，然後將它們放在原處。</span><span class="sxs-lookup"><span data-stu-id="c41ee-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="c41ee-132">當您這樣做時，使用者必須經過一些指示，並藉由標示一些核取方塊來記錄她/他的進度。</span><span class="sxs-lookup"><span data-stu-id="c41ee-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="c41ee-133">如果使用者有她/他的手 _不忙碌_，則 instinctual 只需觸碰該核取方塊，或使用手光來選取它即可。</span><span class="sxs-lookup"><span data-stu-id="c41ee-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="c41ee-134">不過，如果使用者有她/他的員工忙，就像在我們的案例中保存一些全像攝影引擎部分一樣，您想要讓使用者使用其眼睛來順暢地滾動指示，並只查看一個核取方塊，然後說「檢查！」。</span><span class="sxs-lookup"><span data-stu-id="c41ee-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="c41ee-135">若要啟用此功能，您必須使用獨立于核心 MRTK FocusHandlers 的眼睛特定 EyeTrackingTarget 腳本，並將于下方討論。</span><span class="sxs-lookup"><span data-stu-id="c41ee-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="c41ee-136">1. 使用泛型焦點和指標處理常式</span><span class="sxs-lookup"><span data-stu-id="c41ee-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="c41ee-137">如果已正確設定眼睛追蹤 (請參閱 [基本 MRTK 設定以使用眼睛追蹤](EyeTracking_BasicSetup.md)) ，讓使用者可以使用其眼睛來選取全像輸入一樣的其他焦點輸入 (例如，頭部注視或手形光線) 。這項功能可讓您根據使用者的需求，在 MRTK 輸入指標設定檔中定義主要焦點類型，並讓您的程式碼保持不變，以彈性地與您的全像的方式互動。</span><span class="sxs-lookup"><span data-stu-id="c41ee-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](EyeTracking_BasicSetup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="c41ee-138">這可讓您在前端或眼睛之間切換，而不需要變更一行程式碼，也不需要以最多互動的視覺目標取代手光線。</span><span class="sxs-lookup"><span data-stu-id="c41ee-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="c41ee-139">專注于全息圖</span><span class="sxs-lookup"><span data-stu-id="c41ee-139">Focusing on a hologram</span></span>

<span data-ttu-id="c41ee-140">若要偵測影像的焦點時間，請使用可提供您兩個介面成員的 _' IMixedRealityFocusHandler '_ 介面： _OnFocusEnter_ 和 _OnFocusExit_。</span><span class="sxs-lookup"><span data-stu-id="c41ee-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="c41ee-141">以下是 [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) 的簡單範例，可在查看時變更全像影像的色彩。</span><span class="sxs-lookup"><span data-stu-id="c41ee-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

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

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="c41ee-142">選取焦點的全息圖</span><span class="sxs-lookup"><span data-stu-id="c41ee-142">Selecting a focused hologram</span></span>

<span data-ttu-id="c41ee-143">若要選取焦點的全息圖，請使用 _PointerHandler_ 來接聽輸入事件，以確認選取專案。</span><span class="sxs-lookup"><span data-stu-id="c41ee-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="c41ee-144">例如，新增 _IMixedRealityPointerHandler_ 會讓它們對簡單指標輸入做出回應。</span><span class="sxs-lookup"><span data-stu-id="c41ee-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="c41ee-145">_IMixedRealityPointerHandler_ 介面需要執行下列三個介面成員： _OnPointerUp_、 _OnPointerDown_ 和 _OnPointerClicked_。</span><span class="sxs-lookup"><span data-stu-id="c41ee-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="c41ee-146">在下列範例中，我們會藉由查看、捏合或說「選取」來變更全像影像的色彩。</span><span class="sxs-lookup"><span data-stu-id="c41ee-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="c41ee-147">觸發事件的必要動作是透過讓 `eventData.MixedRealityInputAction == selectAction` 我們可以在 Unity 編輯器中設定類型的方式來定義，預設為「 `selectAction` 選取」動作。</span><span class="sxs-lookup"><span data-stu-id="c41ee-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="c41ee-148">您可以透過 MRTK [](../Input/InputActions.md)設定配置 _檔_  ->  _輸入_  ->  _輸入動作_，在 MRTK 設定檔中設定可用的 MixedRealityInputActions 類型。</span><span class="sxs-lookup"><span data-stu-id="c41ee-148">The types of available [MixedRealityInputActions](../Input/InputActions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

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

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="c41ee-149">眼睛相關的 BaseEyeFocusHandler</span><span class="sxs-lookup"><span data-stu-id="c41ee-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="c41ee-150">假設眼睛看起來與其他指標輸入非常不同，您可能會想要確定只有當焦點輸入是 _眼睛_ ，而且目前是主要的輸入指標時，才會對其做出反應。</span><span class="sxs-lookup"><span data-stu-id="c41ee-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="c41ee-151">基於這個目的，您會使用 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) 眼睛追蹤特有的，以及衍生自的 [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) 。</span><span class="sxs-lookup"><span data-stu-id="c41ee-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="c41ee-152">如先前所述，只有當眼睛的目標是主要指標 (輸入時才會觸發，也就是不會有作用中的) 的手光線。</span><span class="sxs-lookup"><span data-stu-id="c41ee-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="c41ee-153">如需詳細資訊，請參閱 [如何支援眼睛的眼睛 + 手勢](EyeTracking_EyesAndHands.md)。</span><span class="sxs-lookup"><span data-stu-id="c41ee-153">For more information, see [How to support eye gaze + hand gestures](EyeTracking_EyesAndHands.md).</span></span>

<span data-ttu-id="c41ee-154">以下是 `EyeTrackingDemo-03-Navigation` (資產/MRTK/範例/示範/EyeTracking/場景) 的範例。</span><span class="sxs-lookup"><span data-stu-id="c41ee-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="c41ee-155">在此示範中，有兩個3D 全息圖會根據物件的哪個部分而輪流：如果使用者查看全像影像的左邊，則該部分將會慢慢地移往使用者的前方。</span><span class="sxs-lookup"><span data-stu-id="c41ee-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="c41ee-156">如果查看右邊，那麼該部分將會慢慢移至前方。</span><span class="sxs-lookup"><span data-stu-id="c41ee-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="c41ee-157">這是一種行為，您可能不希望隨時都處於使用中狀態，也可能不會想要讓光線或頭部不小心觸發。</span><span class="sxs-lookup"><span data-stu-id="c41ee-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="c41ee-158">有了 [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) 附加的，GameObject 會在查看時旋轉。</span><span class="sxs-lookup"><span data-stu-id="c41ee-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

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

<span data-ttu-id="c41ee-159">如需完整的可用事件清單，請參閱 API 檔 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) ：</span><span class="sxs-lookup"><span data-stu-id="c41ee-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="c41ee-160">**OnEyeFocusStart：** 當眼睛光線 *開始* 與此目標碰撞器交集時，即會觸發。</span><span class="sxs-lookup"><span data-stu-id="c41ee-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="c41ee-161">**OnEyeFocusStay：** 當眼睛光線與此目標碰撞器相交 *時* 觸發。</span><span class="sxs-lookup"><span data-stu-id="c41ee-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="c41ee-162">**OnEyeFocusStop：** 當眼睛光線 *停止* 與此目標碰撞器交集時，即會觸發。</span><span class="sxs-lookup"><span data-stu-id="c41ee-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="c41ee-163">**OnEyeFocusDwell：** 當眼睛光線與此目標的碰撞器有一段指定的時間的交集時，即會觸發。</span><span class="sxs-lookup"><span data-stu-id="c41ee-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="c41ee-164">2. 獨立紅眼-特定 EyeTrackingTarget</span><span class="sxs-lookup"><span data-stu-id="c41ee-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="c41ee-165">最後，我們會為您提供一個解決方案，讓您能夠將眼睛型輸入與透過腳本的其他焦點指標完全獨立 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。</span><span class="sxs-lookup"><span data-stu-id="c41ee-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="c41ee-166">這有三個 _優點_：</span><span class="sxs-lookup"><span data-stu-id="c41ee-166">This has three _advantages_:</span></span>

- <span data-ttu-id="c41ee-167">您可以確定全像影像只會對使用者的眼睛進行回應。</span><span class="sxs-lookup"><span data-stu-id="c41ee-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="c41ee-168">這與目前使用中的主要輸入無關。</span><span class="sxs-lookup"><span data-stu-id="c41ee-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="c41ee-169">因此，您可以一次處理多個輸入，例如，將以手手勢為目標的快速眼睛結合在一起。</span><span class="sxs-lookup"><span data-stu-id="c41ee-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="c41ee-170">已設定數個 Unity 事件，讓您可以快速且方便地在 Unity 編輯器中或透過程式碼來處理和重複使用現有的行為。</span><span class="sxs-lookup"><span data-stu-id="c41ee-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="c41ee-171">另外還有一些 _缺點：_</span><span class="sxs-lookup"><span data-stu-id="c41ee-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="c41ee-172">個別處理個別輸入的工作更多。</span><span class="sxs-lookup"><span data-stu-id="c41ee-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="c41ee-173">沒有簡潔的效能降低：它只支援眼睛目標。</span><span class="sxs-lookup"><span data-stu-id="c41ee-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="c41ee-174">如果眼睛追蹤無法運作，您需要額外的回復。</span><span class="sxs-lookup"><span data-stu-id="c41ee-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="c41ee-175">類似于 _BaseFocusHandler_， _EyeTrackingTarget_ 已準備好一些眼睛相關的 unity 事件，您可以透過 Unity 編輯器輕鬆地透過 unity 編輯器接聽 (請參閱以下範例) 或在程式碼中使用 _AddListener ()_ ：</span><span class="sxs-lookup"><span data-stu-id="c41ee-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="c41ee-176">OnLookAtStart () </span><span class="sxs-lookup"><span data-stu-id="c41ee-176">OnLookAtStart()</span></span>
- <span data-ttu-id="c41ee-177">WhileLookingAtTarget () </span><span class="sxs-lookup"><span data-stu-id="c41ee-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="c41ee-178">OnLookAway () </span><span class="sxs-lookup"><span data-stu-id="c41ee-178">OnLookAway()</span></span>
- <span data-ttu-id="c41ee-179">OnDwell () </span><span class="sxs-lookup"><span data-stu-id="c41ee-179">OnDwell()</span></span>
- <span data-ttu-id="c41ee-180">OnSelected () </span><span class="sxs-lookup"><span data-stu-id="c41ee-180">OnSelected()</span></span>

<span data-ttu-id="c41ee-181">在下列範例中，我們將逐步解說一些如何使用 _EyeTrackingTarget_ 的範例。</span><span class="sxs-lookup"><span data-stu-id="c41ee-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="c41ee-182">範例 #1：眼睛支援的智慧型通知</span><span class="sxs-lookup"><span data-stu-id="c41ee-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="c41ee-183">在 `EyeTrackingDemo-02-TargetSelection` (資產/MRTK/範例/示範/EyeTracking/場景) 中，您可以找到回應眼睛的「 _智慧型用心通知_ 」範例。</span><span class="sxs-lookup"><span data-stu-id="c41ee-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="c41ee-184">這些是可放在場景中的3D 文字方塊，並會在查看以簡化可讀性時，順暢地放大並轉向使用者。</span><span class="sxs-lookup"><span data-stu-id="c41ee-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="c41ee-185">當使用者閱讀通知時，資訊會保持簡潔明瞭。</span><span class="sxs-lookup"><span data-stu-id="c41ee-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="c41ee-186">讀取並離開通知之後，會自動關閉通知並淡出。為了達成上述目的，有幾個一般的行為腳本並不特定于眼睛追蹤，例如：</span><span class="sxs-lookup"><span data-stu-id="c41ee-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="c41ee-187">這種方法的優點是，不同的事件可以重複使用相同的腳本。</span><span class="sxs-lookup"><span data-stu-id="c41ee-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="c41ee-188">例如，根據語音命令或按下虛擬按鈕之後，全像影像可能會開始面向使用者。</span><span class="sxs-lookup"><span data-stu-id="c41ee-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="c41ee-189">若要觸發這些事件，您可以直接參考應該在附加至 GameObject 的腳本中執行的方法 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。</span><span class="sxs-lookup"><span data-stu-id="c41ee-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="c41ee-190">在「 _智慧型用心通知_」的範例中，會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="c41ee-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="c41ee-191">**OnLookAtStart ()**：通知開始于 .。。</span><span class="sxs-lookup"><span data-stu-id="c41ee-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="c41ee-192">*FaceUser。參與：* .。。轉向使用者。</span><span class="sxs-lookup"><span data-stu-id="c41ee-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="c41ee-193">*ChangeSize。參與：* .。。 _(增加到指定的最大刻度) 的_ 大小。</span><span class="sxs-lookup"><span data-stu-id="c41ee-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="c41ee-194">*BlendOut。參與：* .。。在 _(更微妙的閒置狀態) 之後_，開始 blend。</span><span class="sxs-lookup"><span data-stu-id="c41ee-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="c41ee-195">**OnDwell ()**：告知 _BlendOut_ 腳本已充分查看通知。</span><span class="sxs-lookup"><span data-stu-id="c41ee-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="c41ee-196">**OnLookAway ()**：通知開始于 .。。</span><span class="sxs-lookup"><span data-stu-id="c41ee-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="c41ee-197">*FaceUser：* .。。回到其原始方向。</span><span class="sxs-lookup"><span data-stu-id="c41ee-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="c41ee-198">*ChangeSize：* .。。減少回其原始大小。</span><span class="sxs-lookup"><span data-stu-id="c41ee-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="c41ee-199">*BlendOut：* .。。開始 blend-如果已觸發 _OnDwell ()_ ，請將其全部混合出來，或回到其閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="c41ee-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="c41ee-200">**設計考慮：** 您可以在這裡輕鬆地調整這些行為的速度，以避免因使用者的眼睛太快而迅速地回應使用者的眼睛，而導致不適感。</span><span class="sxs-lookup"><span data-stu-id="c41ee-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="c41ee-201">否則，這可能很快就會變得非常困難。</span><span class="sxs-lookup"><span data-stu-id="c41ee-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../../Documentation/Images/EyeTracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="MRTK">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="c41ee-202">範例 #2：在查看全像全像的寶物時，會慢慢旋轉</span><span class="sxs-lookup"><span data-stu-id="c41ee-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="c41ee-203">就像範例 #1 一樣，我們可以輕鬆地在 `EyeTrackingDemo-02-TargetSelection` (資產/MRTK/範例/示範/EyeTracking/場景)  (場景中，為我們的全像是在查看時，以較高的) 旋轉範例為例。</span><span class="sxs-lookup"><span data-stu-id="c41ee-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="c41ee-204">您只需要在 _EyeTrackingTarget_ 的 _WhileLookingAtTarget ()_ 事件中觸發全像寶物的旋轉。</span><span class="sxs-lookup"><span data-stu-id="c41ee-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="c41ee-205">以下是更多詳細資料：</span><span class="sxs-lookup"><span data-stu-id="c41ee-205">Here are a few more details:</span></span>

1. <span data-ttu-id="c41ee-206">建立泛型腳本，其中包含公開函式來旋轉其所連接的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="c41ee-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="c41ee-207">以下是來自 _RotateWithConstSpeedDir.cs_ 的範例，我們可以從 Unity 編輯器調整旋轉方向和速度。</span><span class="sxs-lookup"><span data-stu-id="c41ee-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

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

1. <span data-ttu-id="c41ee-208">將 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 腳本新增至您的目標 GameObject，並在 UnityEvent 觸發程式中參考 _RotateTarget ()_ 函式，如下列螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="c41ee-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![EyeTrackingTarget 範例](../Images/EyeTracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="c41ee-210">範例 #3：將這些 gem 稱為 _多重強制回應的目標選擇_</span><span class="sxs-lookup"><span data-stu-id="c41ee-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="c41ee-211">在先前的範例中，我們顯示了偵測目標是否有多麼容易，以及如何觸發對該目標的反應。</span><span class="sxs-lookup"><span data-stu-id="c41ee-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="c41ee-212">接下來，讓我們使用的 _OnSelected ()_ 事件來讓 gem 爆炸 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。</span><span class="sxs-lookup"><span data-stu-id="c41ee-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="c41ee-213">有趣的部分是 *如何* 觸發選取專案。</span><span class="sxs-lookup"><span data-stu-id="c41ee-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="c41ee-214">[`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)可讓您快速指派不同的方法來叫用選取專案：</span><span class="sxs-lookup"><span data-stu-id="c41ee-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="c41ee-215">縮小 _手勢_：將 [選取動作] 設定為 [選取] 時，會使用預設手勢來觸發選取專案。</span><span class="sxs-lookup"><span data-stu-id="c41ee-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="c41ee-216">這表示使用者可以直接提高其手，並將其 thumb 和索引手指放在一起，以確認選取專案。</span><span class="sxs-lookup"><span data-stu-id="c41ee-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="c41ee-217">說「 _select_」：使用預設的語音命令「 _選取_ 」來選取全息圖。</span><span class="sxs-lookup"><span data-stu-id="c41ee-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="c41ee-218">說 _「_ 分裂」或「 _Pop_」：若要使用自訂語音命令，您需要遵循兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="c41ee-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="c41ee-219">設定自訂動作，例如 _"DestroyTarget"_</span><span class="sxs-lookup"><span data-stu-id="c41ee-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="c41ee-220">流覽至 _MRTK-> 輸入-> 輸入動作_</span><span class="sxs-lookup"><span data-stu-id="c41ee-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="c41ee-221">按一下 [新增動作]</span><span class="sxs-lookup"><span data-stu-id="c41ee-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="c41ee-222">設定會觸發此動作的語音命令 _，例如「分裂」或_「 _Pop_ 」</span><span class="sxs-lookup"><span data-stu-id="c41ee-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="c41ee-223">流覽至 _MRTK-> 輸入-> 語音_</span><span class="sxs-lookup"><span data-stu-id="c41ee-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="c41ee-224">按一下 [新增語音命令]</span><span class="sxs-lookup"><span data-stu-id="c41ee-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="c41ee-225">建立您剛才建立之動作的關聯</span><span class="sxs-lookup"><span data-stu-id="c41ee-225">Associate the action you just created</span></span>
            - <span data-ttu-id="c41ee-226">指派 _KeyCode_ 以允許透過按下按鈕來觸發動作</span><span class="sxs-lookup"><span data-stu-id="c41ee-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![語音命令 EyeTrackingTarget 範例](../Images/EyeTracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="c41ee-228">當 gem 被選取時，它會分裂，並使音效消失。</span><span class="sxs-lookup"><span data-stu-id="c41ee-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="c41ee-229">這是由腳本處理 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) 。</span><span class="sxs-lookup"><span data-stu-id="c41ee-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="c41ee-230">您有兩個選擇：</span><span class="sxs-lookup"><span data-stu-id="c41ee-230">You have two options:</span></span>

- <span data-ttu-id="c41ee-231">**在 Unity 編輯器中：** 您可以直接將附加至每個 gem 範本的腳本連結到 Unity 編輯器中的 OnSelected () Unity 事件。</span><span class="sxs-lookup"><span data-stu-id="c41ee-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="c41ee-232">**在程式碼中：** 如果您不想要拖放 Gameobject，您也可以直接將事件接聽程式新增至您的腳本。</span><span class="sxs-lookup"><span data-stu-id="c41ee-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="c41ee-233">以下是我們在腳本中執行此動作的範例 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) ：</span><span class="sxs-lookup"><span data-stu-id="c41ee-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

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

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="c41ee-234">範例 #4：一起使用手片光線和眼睛的輸入</span><span class="sxs-lookup"><span data-stu-id="c41ee-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="c41ee-235">手光線優先于 head 和眼睛的目標。</span><span class="sxs-lookup"><span data-stu-id="c41ee-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="c41ee-236">這表示，如果已啟用「手片」，則手中的時刻會顯示為主要指標。</span><span class="sxs-lookup"><span data-stu-id="c41ee-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="c41ee-237">不過，在某些情況下，您可能會想要使用手片，同時又偵測到使用者是否正在查看特定的全像。</span><span class="sxs-lookup"><span data-stu-id="c41ee-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="c41ee-238">很容易！</span><span class="sxs-lookup"><span data-stu-id="c41ee-238">Easy!</span></span> <span data-ttu-id="c41ee-239">基本上，您需要兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="c41ee-239">Essentially you require two steps:</span></span>

<span data-ttu-id="c41ee-240">**1. 啟用手形：** 若要啟用手光線，請移至 _Mixed Reality 工具組-> 輸入 > 指標_。</span><span class="sxs-lookup"><span data-stu-id="c41ee-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="c41ee-241">在 _EyeTrackingDemo-00-RootScene_ 中，混合現實工具組會針對所有的眼睛追蹤示範場景設定一次，您應該會看到 _EyeTrackingDemoPointerProfile_。</span><span class="sxs-lookup"><span data-stu-id="c41ee-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="c41ee-242">您可以從頭開始建立新的 _輸入設定檔_ ，或調整目前的眼睛追蹤之一：</span><span class="sxs-lookup"><span data-stu-id="c41ee-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="c41ee-243">**從頭開始：** 在 [ _指標_ ] 索引標籤中，從內容功能表中選取 [ _DefaultMixedRealityInputPointerProfile_ ]。</span><span class="sxs-lookup"><span data-stu-id="c41ee-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="c41ee-244">這是預設的指標設定檔，已啟用「手」光線！</span><span class="sxs-lookup"><span data-stu-id="c41ee-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="c41ee-245">若要變更預設資料指標 (不透明的白點) ，只要複製設定檔並建立您自己的自訂指標設定檔即可。</span><span class="sxs-lookup"><span data-stu-id="c41ee-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="c41ee-246">然後以 _EyeGazeCursor_ 的 _指標預製專案_ 底下的 _DefaultCursor_ 取代。</span><span class="sxs-lookup"><span data-stu-id="c41ee-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="c41ee-247">**根據現有的 _EyeTrackingDemoPointerProfile_：** 按兩下 [ _EyeTrackingDemoPointerProfile_ ]，然後在 [ _指標選項_] 底下新增下列專案：</span><span class="sxs-lookup"><span data-stu-id="c41ee-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="c41ee-248">**控制器類型：** 「明確的手」，「Windows Mixed Reality」</span><span class="sxs-lookup"><span data-stu-id="c41ee-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="c41ee-249">**Handedness：** 任何</span><span class="sxs-lookup"><span data-stu-id="c41ee-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="c41ee-250">**指標預製專案：** DefaultControllerPointer</span><span class="sxs-lookup"><span data-stu-id="c41ee-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="c41ee-251">**2. 偵測是否已查看全像影像：** 使用 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 腳本來偵測是否已查看全像上面所述的全像影像。</span><span class="sxs-lookup"><span data-stu-id="c41ee-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="c41ee-252">您也可以看一下 `FollowEyeGaze` 靈感的範例腳本，因為這會在您的眼睛下顯示一個全息圖 (例如，游標) 是否啟用了手片。</span><span class="sxs-lookup"><span data-stu-id="c41ee-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="c41ee-253">現在，當您開始眼睛追蹤示範場景時，您應該會看到來自您手的光線。</span><span class="sxs-lookup"><span data-stu-id="c41ee-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="c41ee-254">例如，在眼睛追蹤目標選取示範中，半透明圓形仍在您的眼睛下，而 gem 則會回應是否有查看它們，而最上層場景功能表按鈕則改用主要輸入指標 (您的手) 。</span><span class="sxs-lookup"><span data-stu-id="c41ee-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="c41ee-255">回到「MixedRealityToolkit 中的眼睛追蹤」</span><span class="sxs-lookup"><span data-stu-id="c41ee-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](EyeTracking_Main.md)
