---
title: Unity 中的手勢
description: 瞭解如何使用 XR 和一般按鈕和軸 Api，在您的電腦上對您的注視進行手勢動作。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 手勢、unity、注視、輸入、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: 523f05f9b3dd05a140bb40168b654a2dc0b00bb5
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299713"
---
# <a name="gestures-in-unity"></a><span data-ttu-id="48d62-104">Unity 中的手勢</span><span class="sxs-lookup"><span data-stu-id="48d62-104">Gestures in Unity</span></span>

<span data-ttu-id="48d62-105">您可以透過兩種主要方式，在您 [的 [Unity](gaze-in-unity.md)]、[ [手手勢](../../design/gaze-and-commit.md#composite-gestures) ] 和 [ [運動] 控制器](../../design/motion-controllers.md) 中針對 HoloLens 和沉浸式 HMD 採取行動。</span><span class="sxs-lookup"><span data-stu-id="48d62-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="48d62-106">您可以透過 Unity 中的相同 Api，存取兩個空間輸入來源的資料。</span><span class="sxs-lookup"><span data-stu-id="48d62-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="48d62-107">Unity 提供兩種主要方式來存取 Windows Mixed Reality 的空間輸入資料。</span><span class="sxs-lookup"><span data-stu-id="48d62-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="48d62-108">常見的 *GetButton/GetAxis* api 可跨多個 Unity XR sdk 運作，而 Windows Mixed Reality 特定的 *InteractionManager/GestureRecognizer* api 會公開一組完整的空間輸入資料。</span><span class="sxs-lookup"><span data-stu-id="48d62-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="48d62-109">高層級複合手勢 Api (GestureRecognizer) </span><span class="sxs-lookup"><span data-stu-id="48d62-109">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="48d62-110">**命名空間：** *UnityEngine. XR。輸入*</span><span class="sxs-lookup"><span data-stu-id="48d62-110">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="48d62-111">**類型**： *GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="48d62-111">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="48d62-112">您的應用程式也可以辨識空間輸入來源、點擊、按住、操作和導覽手勢的較高層級複合手勢。</span><span class="sxs-lookup"><span data-stu-id="48d62-112">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation, and Navigation gestures.</span></span> <span data-ttu-id="48d62-113">您可以使用 GestureRecognizer，跨 [手](../../design/gaze-and-commit.md#composite-gestures) 和 [移動控制器](../../design/motion-controllers.md) 辨識這些複合手勢。</span><span class="sxs-lookup"><span data-stu-id="48d62-113">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="48d62-114">GestureRecognizer 上的每個手勢事件都會提供輸入的 SourceKind，以及事件時的目標 head 光線。</span><span class="sxs-lookup"><span data-stu-id="48d62-114">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="48d62-115">某些事件提供其他內容特定的資訊。</span><span class="sxs-lookup"><span data-stu-id="48d62-115">Some events provide additional context-specific information.</span></span>

<span data-ttu-id="48d62-116">使用手勢辨識器來捕捉手勢時，只需要執行幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="48d62-116">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="48d62-117">建立新的手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="48d62-117">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="48d62-118">指定要監看的手勢</span><span class="sxs-lookup"><span data-stu-id="48d62-118">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="48d62-119">訂閱這些手勢的事件</span><span class="sxs-lookup"><span data-stu-id="48d62-119">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="48d62-120">開始捕獲手勢</span><span class="sxs-lookup"><span data-stu-id="48d62-120">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="48d62-121">建立新的手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="48d62-121">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="48d62-122">若要使用 *GestureRecognizer*，您必須建立 *GestureRecognizer*：</span><span class="sxs-lookup"><span data-stu-id="48d62-122">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="48d62-123">指定要監看的手勢</span><span class="sxs-lookup"><span data-stu-id="48d62-123">Specify which gestures to watch for</span></span>

<span data-ttu-id="48d62-124">透過 *SetRecognizableGestures ()* 指定您感興趣的手勢：</span><span class="sxs-lookup"><span data-stu-id="48d62-124">Specify which gestures you're interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="48d62-125">訂閱這些手勢的事件</span><span class="sxs-lookup"><span data-stu-id="48d62-125">Subscribe to events for those gestures</span></span>

<span data-ttu-id="48d62-126">針對您感興趣的手勢訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="48d62-126">Subscribe to events for the gestures you're interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="48d62-127">導覽和操作手勢在 *GestureRecognizer* 的實例上是互斥的。</span><span class="sxs-lookup"><span data-stu-id="48d62-127">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="48d62-128">開始捕獲手勢</span><span class="sxs-lookup"><span data-stu-id="48d62-128">Start capturing gestures</span></span>

<span data-ttu-id="48d62-129">根據預設， *GestureRecognizer* 在呼叫 *StartCapturingGestures ()* 之前不會監視輸入。</span><span class="sxs-lookup"><span data-stu-id="48d62-129">By default, a *GestureRecognizer* doesn't monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="48d62-130">如果在處理 *StopCapturingGestures ()* 的框架之前執行輸入，可能會在呼叫 *StopCapturingGestures ()* 後產生手勢事件。</span><span class="sxs-lookup"><span data-stu-id="48d62-130">It's possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="48d62-131">*GestureRecognizer* 會記得在先前的畫面格進行實際發生的情況下，它是開啟或關閉，因此可以根據此框架的監看式目標來開始和停止手勢監視。</span><span class="sxs-lookup"><span data-stu-id="48d62-131">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it's reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="48d62-132">停止捕捉手勢</span><span class="sxs-lookup"><span data-stu-id="48d62-132">Stop capturing gestures</span></span>

<span data-ttu-id="48d62-133">若要停止手勢辨識：</span><span class="sxs-lookup"><span data-stu-id="48d62-133">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="48d62-134">移除手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="48d62-134">Removing a gesture recognizer</span></span>

<span data-ttu-id="48d62-135">請記得在終結 *GestureRecognizer* 物件之前取消訂閱的事件。</span><span class="sxs-lookup"><span data-stu-id="48d62-135">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="48d62-136">在 Unity 中轉譯移動控制器模型</span><span class="sxs-lookup"><span data-stu-id="48d62-136">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="48d62-137">![移動控制器模型和遙傳](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="48d62-137">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="48d62-138">*移動控制器模型和遙傳*</span><span class="sxs-lookup"><span data-stu-id="48d62-138">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="48d62-139">若要在您的應用程式中轉譯與您的使用者所持有的實體控制器相符的移動控制站，並在按下各種按鈕時表達清楚，您可以在 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity/)組中使用 **MotionController 預製專案**。</span><span class="sxs-lookup"><span data-stu-id="48d62-139">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="48d62-140">這個預製專案會從系統已安裝的移動控制器驅動程式，在執行時間動態載入正確的 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="48d62-140">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="48d62-141">請務必以動態方式載入這些模型，而不是在編輯器中手動匯入這些模型，如此您的應用程式就會針對使用者可能擁有的任何目前和未來控制器顯示實際精確的3D 模型。</span><span class="sxs-lookup"><span data-stu-id="48d62-141">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="48d62-142">遵循 [開始使用](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 指示下載 Mixed Reality 工具組，並將它新增至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="48d62-142">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="48d62-143">如果您在開始使用步驟中將相機替換成 *MixedRealityCameraParent* 預製專案，您就可以開始使用！</span><span class="sxs-lookup"><span data-stu-id="48d62-143">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="48d62-144">該預製專案包括移動控制器轉譯。</span><span class="sxs-lookup"><span data-stu-id="48d62-144">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="48d62-145">否則，請從 [專案] 窗格將 *資產/HoloToolkit/Input/Prefabs/MotionControllers* 加入場景中。</span><span class="sxs-lookup"><span data-stu-id="48d62-145">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="48d62-146">當使用者在場景中 teleports 時，您會想要將該預製專案新增為您用來移動攝影機之任何父物件的子系，以便讓控制器與使用者一起使用。</span><span class="sxs-lookup"><span data-stu-id="48d62-146">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="48d62-147">如果您的應用程式不需要 teleporting，只要在場景的根目錄新增預製專案即可。</span><span class="sxs-lookup"><span data-stu-id="48d62-147">If your app doesn't involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="48d62-148">擲回物件</span><span class="sxs-lookup"><span data-stu-id="48d62-148">Throwing objects</span></span>

<span data-ttu-id="48d62-149">在虛擬實境中擲回物件，是比一開始可能更困難的問題。</span><span class="sxs-lookup"><span data-stu-id="48d62-149">Throwing objects in virtual reality is a harder problem than it may at first seem.</span></span> <span data-ttu-id="48d62-150">如同大部分的實際互動，在遊戲中擲回時，它會以非預期的方式運作，並中斷深度。</span><span class="sxs-lookup"><span data-stu-id="48d62-150">As with most physically based interactions, when throwing in game acts in an unexpected way, it's immediately obvious and breaks immersion.</span></span> <span data-ttu-id="48d62-151">我們花了一些時間來思考如何表示實體正確的擲回行為，並提供一些指導方針，讓我們想要與您分享，並透過我們的平臺更新來啟用。</span><span class="sxs-lookup"><span data-stu-id="48d62-151">We've spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="48d62-152">您可以在 [這裡](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到建議如何執行擲回的範例。</span><span class="sxs-lookup"><span data-stu-id="48d62-152">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="48d62-153">此範例會遵循下列四個指導方針：</span><span class="sxs-lookup"><span data-stu-id="48d62-153">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="48d62-154">**使用控制器的 *速度* ，而不是位置**。</span><span class="sxs-lookup"><span data-stu-id="48d62-154">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="48d62-155">在 Windows 的11月更新中，我們引進了「 [近似」位置追蹤狀態](../../design/motion-controllers.md#controller-tracking-state)時的行為變更。</span><span class="sxs-lookup"><span data-stu-id="48d62-155">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="48d62-156">處於此狀態時，系統會繼續回報控制器的相關速度資訊，只要我們相信其高精確度，通常會比位置維持高準確度更長。</span><span class="sxs-lookup"><span data-stu-id="48d62-156">When in this state, velocity information about the controller will continue to be reported for as long as we believe its high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="48d62-157">\*\*納入控制器的 \*角度速度\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="48d62-157">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="48d62-158">此邏輯全部包含在靜態方法的檔案中，該檔案 `throwing.cs` 位於 `GetThrownObjectVelAngVel` 上述連結的封裝內：</span><span class="sxs-lookup"><span data-stu-id="48d62-158">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="48d62-159">由於 conserved 的角度速度，擲回的物件必須維持與擲回時相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="48d62-159">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="48d62-160">因為擲回物件的中央可能不是在底框姿勢的原點，所以它的速度可能與使用者參考框架中控制器的速度不同。</span><span class="sxs-lookup"><span data-stu-id="48d62-160">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity than that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="48d62-161">以這種方式產生的物件速度的部分，就是在控制器原點周圍擲回物件的最大中心的瞬間相切速度。</span><span class="sxs-lookup"><span data-stu-id="48d62-161">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="48d62-162">這種相切速度是控制器角度速度的交叉乘積，向量表示控制器原點與擲回物件的中央之間的距離。</span><span class="sxs-lookup"><span data-stu-id="48d62-162">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="48d62-163">擲回之物件的總速度是控制器速度和這個相切速度的總和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="48d62-163">The total velocity of the thrown object is the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="48d62-164">請密切 \*\*注意我們應用速度的 \*時間\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="48d62-164">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="48d62-165">按下按鈕時，該事件最多可能需要20毫秒的時間，才能透過藍牙向上到作業系統。</span><span class="sxs-lookup"><span data-stu-id="48d62-165">When a button is pressed, it can take up to 20 ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="48d62-166">這表示，如果您輪詢控制器狀態變更，而不是按下的狀態或其他方式，則控制器會引發您所取得的資訊。</span><span class="sxs-lookup"><span data-stu-id="48d62-166">This means that if you poll for a controller state change from pressed to not pressed or the other way around, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="48d62-167">此外，我們的輪詢 API 所呈現的控制器會向前預測，以反映畫面上顯示的可能原因，未來可能會超過20毫秒。</span><span class="sxs-lookup"><span data-stu-id="48d62-167">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more than 20 ms in the future.</span></span> <span data-ttu-id="48d62-168">這適合用來 *呈現* 保留的物件，但是會在計算使用者釋出擲回的軌跡時，將我們的時間問題轉譯為 *目標* 物件。</span><span class="sxs-lookup"><span data-stu-id="48d62-168">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released the throw.</span></span> <span data-ttu-id="48d62-169">幸運的是，在11月更新中，當傳送 *InteractionSourcePressed* 或 *InteractionSourceReleased* 這類 Unity 事件時，狀態包括在按下或放開按鈕時，會從背面提出資料。</span><span class="sxs-lookup"><span data-stu-id="48d62-169">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was pressed or released.</span></span>  <span data-ttu-id="48d62-170">若要在擲回期間取得最精確的控制器轉譯和控制器目標，您必須適當地正確地使用輪詢和事件：</span><span class="sxs-lookup"><span data-stu-id="48d62-170">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="48d62-171">針對每個畫面格的 **控制器呈現** ，您的應用程式應該將控制器的 *GameObject* 放在向前預測的控制器上，以表示目前畫面格的 photon 時間。</span><span class="sxs-lookup"><span data-stu-id="48d62-171">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="48d62-172">您可以從 Unity 輪詢 Api （例如 XR）取得此資料 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。Wsa。輸入. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。</span><span class="sxs-lookup"><span data-stu-id="48d62-172">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="48d62-173">針對以按下或放開的 **控制器為目標的控制器** ，您的應用程式應該根據該按下或釋放事件的歷程控制器姿勢來 raycast 和計算軌跡。</span><span class="sxs-lookup"><span data-stu-id="48d62-173">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="48d62-174">您可以從 Unity 事件 Api 取得這類資料，例如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。</span><span class="sxs-lookup"><span data-stu-id="48d62-174">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="48d62-175">**使用** 底框姿勢。</span><span class="sxs-lookup"><span data-stu-id="48d62-175">**Use the grip pose**.</span></span> <span data-ttu-id="48d62-176">相對於底框姿勢（而不是指標姿勢）回報角度速度和速度。</span><span class="sxs-lookup"><span data-stu-id="48d62-176">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="48d62-177">未來的 Windows 更新將持續改善擲回，而您可以預期在此找到更多資訊。</span><span class="sxs-lookup"><span data-stu-id="48d62-177">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk"></a><span data-ttu-id="48d62-178">MRTK 中的手勢和移動控制器</span><span class="sxs-lookup"><span data-stu-id="48d62-178">Gesture and Motion Controllers in MRTK</span></span>

<span data-ttu-id="48d62-179">您可以從輸入管理員存取手勢和移動控制器。</span><span class="sxs-lookup"><span data-stu-id="48d62-179">You can access gesture and motion controller from the input Manager.</span></span>

* [<span data-ttu-id="48d62-180">MRTK 中的手勢</span><span class="sxs-lookup"><span data-stu-id="48d62-180">Gesture in MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [<span data-ttu-id="48d62-181">MRTK 中的動作控制器</span><span class="sxs-lookup"><span data-stu-id="48d62-181">Motion Controller in MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="48d62-182">遵循教學課程</span><span class="sxs-lookup"><span data-stu-id="48d62-182">Follow along with tutorials</span></span>

<span data-ttu-id="48d62-183">混合現實學術中提供逐步教學課程，包含更詳細的自訂範例：</span><span class="sxs-lookup"><span data-stu-id="48d62-183">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="48d62-184">MR Input 211：筆勢</span><span class="sxs-lookup"><span data-stu-id="48d62-184">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="48d62-185">MR Input 213：運動控制器</span><span class="sxs-lookup"><span data-stu-id="48d62-185">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="48d62-186">[![MR 輸入 213-移動控制器](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="48d62-186">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="48d62-187">*MR 輸入 213-移動控制器*</span><span class="sxs-lookup"><span data-stu-id="48d62-187">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="48d62-188">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="48d62-188">Next Development Checkpoint</span></span>

<span data-ttu-id="48d62-189">如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。</span><span class="sxs-lookup"><span data-stu-id="48d62-189">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="48d62-190">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="48d62-190">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="48d62-191">手部和眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="48d62-191">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="48d62-192">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="48d62-192">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="48d62-193">共用體驗</span><span class="sxs-lookup"><span data-stu-id="48d62-193">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="48d62-194">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="48d62-194">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="48d62-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48d62-195">See also</span></span>

* [<span data-ttu-id="48d62-196">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="48d62-196">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="48d62-197">運動控制器</span><span class="sxs-lookup"><span data-stu-id="48d62-197">Motion controllers</span></span>](../../design/motion-controllers.md)