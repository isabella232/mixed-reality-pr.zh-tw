---
title: InputEvents
description: MRTK 中的 InputEvents 檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、事件、
ms.openlocfilehash: b08461d0e17bdbe14748d26d1f5b62e849521ea5
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780858"
---
# <a name="input-events"></a><span data-ttu-id="bad50-104">輸入事件</span><span class="sxs-lookup"><span data-stu-id="bad50-104">Input events</span></span>

<span data-ttu-id="bad50-105">下列清單概述自訂 MonoBehaviour 元件所要執行的所有可用輸入事件介面。</span><span class="sxs-lookup"><span data-stu-id="bad50-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="bad50-106">MRTK 輸入系統會呼叫這些介面，以根據使用者輸入互動來處理自訂應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="bad50-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="bad50-107">[指標輸入事件](pointers.md#pointer-event-interfaces) 的處理方式稍有不同，如下所示：標準輸入事件種類。</span><span class="sxs-lookup"><span data-stu-id="bad50-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bad50-108">根據預設，腳本只會在焦點為 GameObject 的指標或父系時，才會收到輸入事件。</span><span class="sxs-lookup"><span data-stu-id="bad50-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="bad50-109">處理常式</span><span class="sxs-lookup"><span data-stu-id="bad50-109">Handler</span></span> | <span data-ttu-id="bad50-110">事件</span><span class="sxs-lookup"><span data-stu-id="bad50-110">Events</span></span> | <span data-ttu-id="bad50-111">描述</span><span class="sxs-lookup"><span data-stu-id="bad50-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="bad50-112">偵測到來源/遺失</span><span class="sxs-lookup"><span data-stu-id="bad50-112">Source Detected / Lost</span></span> | <span data-ttu-id="bad50-113">當偵測到輸入來源時引發/遺失，例如，偵測到有向的手勢或遺失追蹤時。</span><span class="sxs-lookup"><span data-stu-id="bad50-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="bad50-114">來源姿勢變更</span><span class="sxs-lookup"><span data-stu-id="bad50-114">Source Pose Changed</span></span> | <span data-ttu-id="bad50-115">在來源姿勢變更時引發。</span><span class="sxs-lookup"><span data-stu-id="bad50-115">Raised on source pose changes.</span></span> <span data-ttu-id="bad50-116">來源姿勢代表輸入來源的一般姿勢。</span><span class="sxs-lookup"><span data-stu-id="bad50-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="bad50-117">您可以透過取得特定的姿勢，例如在六個 DOF 控制器中的把手或指標姿勢 `IMixedRealityInputHandler<MixedRealityPose>` 。</span><span class="sxs-lookup"><span data-stu-id="bad50-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="bad50-118">輸入向下/向上鍵</span><span class="sxs-lookup"><span data-stu-id="bad50-118">Input Down / Up</span></span> | <span data-ttu-id="bad50-119">在對二進位輸入（例如按鈕）的變更時引發。</span><span class="sxs-lookup"><span data-stu-id="bad50-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="bad50-120">輸入已變更</span><span class="sxs-lookup"><span data-stu-id="bad50-120">Input Changed</span></span> | <span data-ttu-id="bad50-121">在對指定類型的輸入變更時引發。</span><span class="sxs-lookup"><span data-stu-id="bad50-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="bad50-122">**T** 可以採用下列值：</span><span class="sxs-lookup"><span data-stu-id="bad50-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="bad50-123">- *float* (例如傳回類比觸發程式) </span><span class="sxs-lookup"><span data-stu-id="bad50-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="bad50-124">- *Vector2* (例如會傳回游戲杆杆方向) </span><span class="sxs-lookup"><span data-stu-id="bad50-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="bad50-125">- *Vector3* (例如追蹤裝置的傳回位置) </span><span class="sxs-lookup"><span data-stu-id="bad50-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="bad50-126">- *四元數* (例如會傳回追蹤裝置的方向) </span><span class="sxs-lookup"><span data-stu-id="bad50-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="bad50-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (例如會傳回完整追蹤的裝置) </span><span class="sxs-lookup"><span data-stu-id="bad50-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="bad50-128">語音關鍵字已辨認</span><span class="sxs-lookup"><span data-stu-id="bad50-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="bad50-129">在識別 *語音命令設定檔* 中所設定的其中一個關鍵字時引發。</span><span class="sxs-lookup"><span data-stu-id="bad50-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="bad50-130">聽寫</span><span class="sxs-lookup"><span data-stu-id="bad50-130">Dictation</span></span><br/> <span data-ttu-id="bad50-131">假設</span><span class="sxs-lookup"><span data-stu-id="bad50-131">Hypothesis</span></span> <br/> <span data-ttu-id="bad50-132">結果</span><span class="sxs-lookup"><span data-stu-id="bad50-132">Result</span></span> <br/> <span data-ttu-id="bad50-133">完成</span><span class="sxs-lookup"><span data-stu-id="bad50-133">Complete</span></span> <br/> <span data-ttu-id="bad50-134">錯誤</span><span class="sxs-lookup"><span data-stu-id="bad50-134">Error</span></span> | <span data-ttu-id="bad50-135">由聽寫系統引發，以報告聽寫會話的結果。</span><span class="sxs-lookup"><span data-stu-id="bad50-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="bad50-136">手勢事件：</span><span class="sxs-lookup"><span data-stu-id="bad50-136">Gesture events on:</span></span> <br/> <span data-ttu-id="bad50-137">已開始</span><span class="sxs-lookup"><span data-stu-id="bad50-137">Started</span></span> <br/> <span data-ttu-id="bad50-138">已更新</span><span class="sxs-lookup"><span data-stu-id="bad50-138">Updated</span></span> <br/> <span data-ttu-id="bad50-139">已完成</span><span class="sxs-lookup"><span data-stu-id="bad50-139">Completed</span></span> <br/> <span data-ttu-id="bad50-140">已取消</span><span class="sxs-lookup"><span data-stu-id="bad50-140">Canceled</span></span> | <span data-ttu-id="bad50-141">在筆勢偵測時引發。</span><span class="sxs-lookup"><span data-stu-id="bad50-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="bad50-142">已更新/完成手勢</span><span class="sxs-lookup"><span data-stu-id="bad50-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="bad50-143">在偵測包含指定類型之其他資料的手勢時引發。</span><span class="sxs-lookup"><span data-stu-id="bad50-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="bad50-144">如需 **T** 可能值的詳細資訊，請參閱 [**手勢事件**](Gestures.md#gesture-events)。</span><span class="sxs-lookup"><span data-stu-id="bad50-144">See [**gesture events**](Gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="bad50-145">手動接點已更新</span><span class="sxs-lookup"><span data-stu-id="bad50-145">Hand Joints Updated</span></span> | <span data-ttu-id="bad50-146">當手動接點更新時，透過明確的手控制器來引發。</span><span class="sxs-lookup"><span data-stu-id="bad50-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="bad50-147">已更新手形網格</span><span class="sxs-lookup"><span data-stu-id="bad50-147">Hand Mesh Updated</span></span> | <span data-ttu-id="bad50-148">在更新手勢時，透過明確的手勢控制器來引發。</span><span class="sxs-lookup"><span data-stu-id="bad50-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="bad50-149">動作已開始/結束</span><span class="sxs-lookup"><span data-stu-id="bad50-149">Action Started / Ended</span></span> | <span data-ttu-id="bad50-150">引發以表示對應至動作之輸入的動作開始和結束。</span><span class="sxs-lookup"><span data-stu-id="bad50-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="bad50-151">作用中的輸入事件</span><span class="sxs-lookup"><span data-stu-id="bad50-151">Input events in action</span></span>

<span data-ttu-id="bad50-152">在腳本層級，您可以藉由執行上表中所示的其中一個事件處理常式介面來取用輸入事件。</span><span class="sxs-lookup"><span data-stu-id="bad50-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="bad50-153">透過使用者互動引發輸入事件時，會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="bad50-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="bad50-154">MRTK 輸入系統會辨識出輸入事件已發生。</span><span class="sxs-lookup"><span data-stu-id="bad50-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="bad50-155">MRTK 輸入系統會將輸入事件的相關介面函式引發至所有 [已註冊的全域輸入處理常式](#register-for-global-input-events)</span><span class="sxs-lookup"><span data-stu-id="bad50-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="bad50-156">針對在輸入系統中註冊的每個作用中指標：</span><span class="sxs-lookup"><span data-stu-id="bad50-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="bad50-157">輸入系統會決定要將焦點放在目前指標的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="bad50-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="bad50-158">輸入系統會利用 [Unity 的事件系統](https://docs.unity3d.com/Manual/EventSystem.html) 來引發焦點 GameObject 上所有相符元件的相關介面函式。</span><span class="sxs-lookup"><span data-stu-id="bad50-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="bad50-159">如果您在任何時間點輸入事件已 [標示為已使用](#how-to-stop-input-events)，進程將會結束，且不會有進一步的 gameobject 接收回呼。</span><span class="sxs-lookup"><span data-stu-id="bad50-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="bad50-160">範例：辨識出語音命令時，將會搜尋執行介面的元件 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 。</span><span class="sxs-lookup"><span data-stu-id="bad50-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="bad50-161">注意：如果在目前的 GameObject 上找不到符合所需介面的元件，Unity 事件系統將會反升搜尋父 GameObject。</span><span class="sxs-lookup"><span data-stu-id="bad50-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="bad50-162">如果未註冊任何全域輸入處理常式，且找不到具有相符元件/介面的 GameObject，則輸入系統會呼叫每個已註冊的回溯輸入處理常式</span><span class="sxs-lookup"><span data-stu-id="bad50-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="bad50-163">[指標輸入事件](pointers.md#pointer-event-interfaces) 的處理方式與上面所列的輸入事件介面稍有不同。</span><span class="sxs-lookup"><span data-stu-id="bad50-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="bad50-164">尤其是，指標輸入事件只會由引發輸入事件的指標，以及任何全域輸入處理常式所專注的 GameObject 來處理。</span><span class="sxs-lookup"><span data-stu-id="bad50-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="bad50-165">一般輸入事件是由所有使用中指標的焦點 Gameobject 來處理。</span><span class="sxs-lookup"><span data-stu-id="bad50-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="bad50-166">輸入事件介面範例</span><span class="sxs-lookup"><span data-stu-id="bad50-166">Input event interface example</span></span>

<span data-ttu-id="bad50-167">下列程式碼示範如何使用 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 介面。</span><span class="sxs-lookup"><span data-stu-id="bad50-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="bad50-168">當使用者在將焦點放在具有這個類別的 GameObject 時，說出「較小」或「更大」的單字時 `ShowHideSpeechHandler` ，GameObject 將會以一半或兩倍的方式來調整其大小。</span><span class="sxs-lookup"><span data-stu-id="bad50-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="bad50-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 輸入事件需要在 [MRTK Speech 命令設定檔](Speech.md)中預先註冊所需的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bad50-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](Speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="bad50-170">註冊全域輸入事件</span><span class="sxs-lookup"><span data-stu-id="bad50-170">Register for global input events</span></span>

<span data-ttu-id="bad50-171">若要建立可接聽全域輸入事件的元件，並忽略 GameObject 可能的焦點，元件必須向輸入系統註冊本身。</span><span class="sxs-lookup"><span data-stu-id="bad50-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="bad50-172">註冊之後，此 MonoBehaviour 的任何實例都會收到輸入事件，以及任何 GameObject () 目前為焦點和其他全域註冊的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="bad50-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="bad50-173">如果輸入事件已 [標示為已使用](#how-to-stop-input-events)，則全域註冊的處理常式仍會接收回呼。</span><span class="sxs-lookup"><span data-stu-id="bad50-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="bad50-174">不過，沒有任何焦點的 Gameobject 會收到此事件。</span><span class="sxs-lookup"><span data-stu-id="bad50-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="bad50-175">全域輸入註冊範例</span><span class="sxs-lookup"><span data-stu-id="bad50-175">Global input registration example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="bad50-176">註冊 fallback 輸入事件</span><span class="sxs-lookup"><span data-stu-id="bad50-176">Register for fallback input events</span></span>

<span data-ttu-id="bad50-177">回溯輸入處理常式類似于已註冊的全域輸入處理常式，但會被視為輸入事件處理的最後手段。</span><span class="sxs-lookup"><span data-stu-id="bad50-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="bad50-178">只有在找不到任何全域輸入處理常式，且焦點沒有任何 Gameobject 時，才會利用回溯輸入處理常式。</span><span class="sxs-lookup"><span data-stu-id="bad50-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="bad50-179">Fallback 輸入處理常式範例</span><span class="sxs-lookup"><span data-stu-id="bad50-179">Fallback input handler example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a><span data-ttu-id="bad50-180">如何停止輸入事件</span><span class="sxs-lookup"><span data-stu-id="bad50-180">How to stop input events</span></span>

<span data-ttu-id="bad50-181">每個輸入事件介面都會提供一個 [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) 資料物件做為介面上每個函數的參數。</span><span class="sxs-lookup"><span data-stu-id="bad50-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="bad50-182">此事件資料物件會從 Unity 本身擴充 [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) 。</span><span class="sxs-lookup"><span data-stu-id="bad50-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="bad50-183">若要停止輸入事件，使其無法 [依照所述](#input-events-in-action)的執行傳播，元件可以呼叫， [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) 以將事件標示為已使用。</span><span class="sxs-lookup"><span data-stu-id="bad50-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="bad50-184">這會停止任何其他 Gameobject 接收目前的輸入事件，但全域輸入處理常式除外。</span><span class="sxs-lookup"><span data-stu-id="bad50-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="bad50-185">呼叫方法的元件 `Use()` 會阻止其他 gameobject 接收它。</span><span class="sxs-lookup"><span data-stu-id="bad50-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="bad50-186">不過，目前 GameObject 上的其他元件仍會收到輸入事件，並引發任何相關的介面函數。</span><span class="sxs-lookup"><span data-stu-id="bad50-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="bad50-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bad50-187">See also</span></span>

- [<span data-ttu-id="bad50-188">指標</span><span class="sxs-lookup"><span data-stu-id="bad50-188">Pointers</span></span>](Pointers.md)
- [<span data-ttu-id="bad50-189">語音</span><span class="sxs-lookup"><span data-stu-id="bad50-189">Speech</span></span>](Speech.md)
- [<span data-ttu-id="bad50-190">輸入狀態</span><span class="sxs-lookup"><span data-stu-id="bad50-190">Input State</span></span>](InputState.md)
