---
title: 軌跡
description: 在 MRTK 中 Docummentation 手勢和其事件
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、手勢、
ms.openlocfilehash: 0e13c18e31135faf2752fd1f3b5f9f8b1c91b2b0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685861"
---
# <a name="gestures"></a><span data-ttu-id="e43b6-104">軌跡</span><span class="sxs-lookup"><span data-stu-id="e43b6-104">Gestures</span></span>

<span data-ttu-id="e43b6-105">手勢是根據人為手的輸入活動。</span><span class="sxs-lookup"><span data-stu-id="e43b6-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="e43b6-106">有兩種類型的裝置會在 MRTK 中引發手勢輸入事件：</span><span class="sxs-lookup"><span data-stu-id="e43b6-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="e43b6-107">Windows Mixed Reality 的裝置，例如 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e43b6-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="e43b6-108">這會描述捏合運動 ( 「點擊」 ) 和點擊和按住手勢。</span><span class="sxs-lookup"><span data-stu-id="e43b6-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="e43b6-109">如需 HoloLens 手勢的詳細資訊，請參閱 [Windows Mixed Reality 手勢檔](https://docs.microsoft.com/windows/mixed-reality/gestures)。</span><span class="sxs-lookup"><span data-stu-id="e43b6-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](https://docs.microsoft.com/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="e43b6-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) 包裝 [UNITY XR。Wsa。GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) ，以使用來自 HoloLens 裝置的 Unity 手勢事件。</span><span class="sxs-lookup"><span data-stu-id="e43b6-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="e43b6-111">觸控式螢幕裝置。</span><span class="sxs-lookup"><span data-stu-id="e43b6-111">Touch screen devices.</span></span>

  <span data-ttu-id="e43b6-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) 包裝支援實體觸控畫面的 [Unity 觸控類別](https://docs.unity3d.com/ScriptReference/Touch.html) 。</span><span class="sxs-lookup"><span data-stu-id="e43b6-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="e43b6-113">這兩個輸入來源都使用 _手勢設定_ 設定檔，分別將 Unity 的觸控和手勢事件轉譯成 MRTK 的 [輸入動作](InputActions.md)。</span><span class="sxs-lookup"><span data-stu-id="e43b6-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](InputActions.md).</span></span> <span data-ttu-id="e43b6-114">此設定檔可在 _輸入系統設定_ 設定檔下找到。</span><span class="sxs-lookup"><span data-stu-id="e43b6-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../Images/Input/GestureProfile.png" style="max-width:100%;" alt="Gesture Profile View">

## <a name="gesture-events"></a><span data-ttu-id="e43b6-115">手勢事件</span><span class="sxs-lookup"><span data-stu-id="e43b6-115">Gesture events</span></span>

<span data-ttu-id="e43b6-116">執行其中一個軌跡處理常式介面可接收手勢事件： [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) 或 [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (查看 [事件處理常式](InputEvents.md)) 的資料表。</span><span class="sxs-lookup"><span data-stu-id="e43b6-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](InputEvents.md)).</span></span>

<span data-ttu-id="e43b6-117">請參閱 [範例場景](#example-scene) ，以取得筆勢事件處理常式的範例執行。</span><span class="sxs-lookup"><span data-stu-id="e43b6-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="e43b6-118">在執行泛型版本時， *OnGestureCompleted* 和 *OnGestureUpdated* 事件可以接收下列類型的類型資料：</span><span class="sxs-lookup"><span data-stu-id="e43b6-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="e43b6-119">`Vector2` -2D 位置手勢。</span><span class="sxs-lookup"><span data-stu-id="e43b6-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="e43b6-120">由觸控畫面產生，以通知他們 [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) 。</span><span class="sxs-lookup"><span data-stu-id="e43b6-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="e43b6-121">`Vector3` -3D 位置手勢。</span><span class="sxs-lookup"><span data-stu-id="e43b6-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="e43b6-122">由 HoloLens 產生以通知：</span><span class="sxs-lookup"><span data-stu-id="e43b6-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="e43b6-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) 操作事件的</span><span class="sxs-lookup"><span data-stu-id="e43b6-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="e43b6-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) 流覽事件的</span><span class="sxs-lookup"><span data-stu-id="e43b6-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="e43b6-125">`Quaternion` -3D 旋轉手勢。</span><span class="sxs-lookup"><span data-stu-id="e43b6-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="e43b6-126">可供自訂輸入來源使用，但目前不是由任何現有專案所產生。</span><span class="sxs-lookup"><span data-stu-id="e43b6-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="e43b6-127">`MixedRealityPose` -合併的3D 位置/旋轉手勢。</span><span class="sxs-lookup"><span data-stu-id="e43b6-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="e43b6-128">可供自訂輸入來源使用，但目前不是由任何現有專案所產生。</span><span class="sxs-lookup"><span data-stu-id="e43b6-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="e43b6-129">事件順序</span><span class="sxs-lookup"><span data-stu-id="e43b6-129">Order of events</span></span>

<span data-ttu-id="e43b6-130">有兩個主要的事件鏈，視使用者輸入而定：</span><span class="sxs-lookup"><span data-stu-id="e43b6-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="e43b6-131">「保留」：</span><span class="sxs-lookup"><span data-stu-id="e43b6-131">"Hold":</span></span>
    1. <span data-ttu-id="e43b6-132">按住 ctrl：</span><span class="sxs-lookup"><span data-stu-id="e43b6-132">Hold tap:</span></span>
        - <span data-ttu-id="e43b6-133">開始 _操作_</span><span class="sxs-lookup"><span data-stu-id="e43b6-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="e43b6-134">按住 [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)：</span><span class="sxs-lookup"><span data-stu-id="e43b6-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="e43b6-135">開始 _保存_</span><span class="sxs-lookup"><span data-stu-id="e43b6-135">start _Hold_</span></span>
    1. <span data-ttu-id="e43b6-136">放開點：</span><span class="sxs-lookup"><span data-stu-id="e43b6-136">Release tap:</span></span>
        - <span data-ttu-id="e43b6-137">完成 _保存_</span><span class="sxs-lookup"><span data-stu-id="e43b6-137">complete _Hold_</span></span>
        - <span data-ttu-id="e43b6-138">完成 _操作_</span><span class="sxs-lookup"><span data-stu-id="e43b6-138">complete _Manipulation_</span></span>

- <span data-ttu-id="e43b6-139">「移動」：</span><span class="sxs-lookup"><span data-stu-id="e43b6-139">"Move":</span></span>
    1. <span data-ttu-id="e43b6-140">按住 ctrl：</span><span class="sxs-lookup"><span data-stu-id="e43b6-140">Hold tap:</span></span>
        - <span data-ttu-id="e43b6-141">開始 _操作_</span><span class="sxs-lookup"><span data-stu-id="e43b6-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="e43b6-142">按住 [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)：</span><span class="sxs-lookup"><span data-stu-id="e43b6-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="e43b6-143">開始 _保存_</span><span class="sxs-lookup"><span data-stu-id="e43b6-143">start _Hold_</span></span>
    1. <span data-ttu-id="e43b6-144">將手移至 [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)之外：</span><span class="sxs-lookup"><span data-stu-id="e43b6-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="e43b6-145">取消 _保存_</span><span class="sxs-lookup"><span data-stu-id="e43b6-145">cancel _Hold_</span></span>
        - <span data-ttu-id="e43b6-146">開始 _導覽_</span><span class="sxs-lookup"><span data-stu-id="e43b6-146">start _Navigation_</span></span>
    1. <span data-ttu-id="e43b6-147">放開點：</span><span class="sxs-lookup"><span data-stu-id="e43b6-147">Release tap:</span></span>
        - <span data-ttu-id="e43b6-148">完成 _操作_</span><span class="sxs-lookup"><span data-stu-id="e43b6-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="e43b6-149">完成 _導覽_</span><span class="sxs-lookup"><span data-stu-id="e43b6-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="e43b6-150">範例場景</span><span class="sxs-lookup"><span data-stu-id="e43b6-150">Example scene</span></span>

<span data-ttu-id="e43b6-151">**HandInteractionGestureEventsExample** (資產/MRTK/範例/示範/HandTracking/場景) 場景顯示如何使用指標結果，在叫用位置產生物件。</span><span class="sxs-lookup"><span data-stu-id="e43b6-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="e43b6-152">`GestureTester` (資產/MRTK/範例/示範/HandTracking/腳本) 腳本是透過 gameobject 將手勢事件視覺化的範例執行。</span><span class="sxs-lookup"><span data-stu-id="e43b6-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="e43b6-153">處理常式函式會變更指標物件的色彩，並在場景中的文字物件中顯示最後記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="e43b6-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>
