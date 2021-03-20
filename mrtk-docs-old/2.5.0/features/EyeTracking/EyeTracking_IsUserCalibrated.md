---
title: EyeTracking_IsUserCalibrated
description: 如何在 MRTK 中設定使用者視覺校正
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、校正、
ms.openlocfilehash: 88448012ff4189cf6559a10bf401973d70cc7ee4
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689978"
---
# <a name="eye-calibration"></a><span data-ttu-id="d9623-104">眼睛校正</span><span class="sxs-lookup"><span data-stu-id="d9623-104">Eye calibration</span></span>

![眼睛校正通知的螢幕擷取畫面](../Images/EyeTracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="d9623-106">概觀</span><span class="sxs-lookup"><span data-stu-id="d9623-106">Overview</span></span>

<span data-ttu-id="d9623-107">如果您的應用程式體驗有基本的功能，您可能想要確定使用者的眼睛校正是否有效。</span><span class="sxs-lookup"><span data-stu-id="d9623-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="d9623-108">這是不正確主要原因，就是使用者在放入裝置時，選擇略過眼睛追蹤校正。</span><span class="sxs-lookup"><span data-stu-id="d9623-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="d9623-109">本頁涵蓋下列內容：</span><span class="sxs-lookup"><span data-stu-id="d9623-109">This page covers the following:</span></span>

- <span data-ttu-id="d9623-110">說明如何偵測使用者是否有眼睛的校正</span><span class="sxs-lookup"><span data-stu-id="d9623-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="d9623-111">提供範例，說明如何觸發使用者通知，以指示使用者進行眼睛校正</span><span class="sxs-lookup"><span data-stu-id="d9623-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="d9623-112">如果眼睛校正變為有效，則自動解除通知</span><span class="sxs-lookup"><span data-stu-id="d9623-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="d9623-113">如果使用者選擇在沒有校正的情況下繼續時，手動解除通知</span><span class="sxs-lookup"><span data-stu-id="d9623-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="d9623-114">如何偵測眼睛校正狀態</span><span class="sxs-lookup"><span data-stu-id="d9623-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="d9623-115">MRTK 中的眼睛追蹤設定是透過介面進行設定 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 。</span><span class="sxs-lookup"><span data-stu-id="d9623-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="d9623-116">使用 [CoreServices](EyeTracking_EyeGazeProvider.md) 時，會提供在執行時間的工具組中註冊的預設注視提供者實作為。</span><span class="sxs-lookup"><span data-stu-id="d9623-116">Using [CoreServices.InputSystem.EyeGazeProvider](EyeTracking_EyeGazeProvider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="d9623-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid``bool?`如果尚未提供來自眼睛追蹤器的資訊，則會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="d9623-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="d9623-118">收到資料之後，它會傳回 true 或 false，表示使用者的眼睛追蹤校正是有效的或不正確。</span><span class="sxs-lookup"><span data-stu-id="d9623-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="d9623-119">範例眼睛校正通知-逐步解說</span><span class="sxs-lookup"><span data-stu-id="d9623-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="d9623-120">開啟 MRTK 的眼睛追蹤範例套件 (資產/MRTK/範例/示範/EyeTracking) </span><span class="sxs-lookup"><span data-stu-id="d9623-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="d9623-121">Load _EyeTrackingDemo-00-RootScene unity_ 場景</span><span class="sxs-lookup"><span data-stu-id="d9623-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="d9623-122">查看 _EyeCalibrationChecker_：</span><span class="sxs-lookup"><span data-stu-id="d9623-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="d9623-123">在此場景中，我們已經有一個範例，可偵測目前的使用者是否已在 *_EyeCalibrationChecker_ 遊戲物件* 下校正。</span><span class="sxs-lookup"><span data-stu-id="d9623-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="d9623-124">這只是家長的一些文字網格，並且有一些額外的觸發程式來將通知和輸出混合。這包括在啟用時緩慢增加其大小和不透明度。</span><span class="sxs-lookup"><span data-stu-id="d9623-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="d9623-125">一旦關閉通知，將會減緩其大小並淡出。</span><span class="sxs-lookup"><span data-stu-id="d9623-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="d9623-126">附加至 *_EyeCalibrationChecker_ 遊戲物件* 的 [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker)腳本會公開兩個 Unity 事件：</span><span class="sxs-lookup"><span data-stu-id="d9623-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="d9623-127">這些事件只會在校正狀態變更時觸發。</span><span class="sxs-lookup"><span data-stu-id="d9623-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="d9623-128">因此，如果使用者選擇關閉通知，將不會再次顯示通知，直到</span><span class="sxs-lookup"><span data-stu-id="d9623-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="d9623-129">應用程式會重新開機</span><span class="sxs-lookup"><span data-stu-id="d9623-129">The app gets restarted</span></span>
      - <span data-ttu-id="d9623-130">偵測到有效的使用者，然後新的 uncalibrated 使用者將裝置放在</span><span class="sxs-lookup"><span data-stu-id="d9623-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="d9623-131">為了測試是否正確觸發動畫和事件，EyeCalibrationChecker 腳本會擁有 `bool editorTestUserIsCalibrated` 旗標。</span><span class="sxs-lookup"><span data-stu-id="d9623-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="d9623-132">例如，在 Unity 編輯器中執行時，可以測試：</span><span class="sxs-lookup"><span data-stu-id="d9623-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="d9623-133">當校正狀態從 true 變更為 false 時，是否自動顯示通知</span><span class="sxs-lookup"><span data-stu-id="d9623-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="d9623-134">當狀態從 false 變更為 true 時，是否會再次自動關閉通知。</span><span class="sxs-lookup"><span data-stu-id="d9623-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a><span data-ttu-id="d9623-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9623-135">See also</span></span>

- [<span data-ttu-id="d9623-136">MRTK 眼追蹤總覽</span><span class="sxs-lookup"><span data-stu-id="d9623-136">MRTK Eye Tracking Overview</span></span>](EyeTracking_Main.md)
- [<span data-ttu-id="d9623-137">MRTK 眼睛追蹤設定</span><span class="sxs-lookup"><span data-stu-id="d9623-137">MRTK Eye Tracking setup</span></span>](EyeTracking_BasicSetup.md)
- [<span data-ttu-id="d9623-138">透過程式碼 MRTK 眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="d9623-138">MRTK Eye Tracking via Code</span></span>](EyeTracking_EyeGazeProvider.md)
- [<span data-ttu-id="d9623-139">HoloLens 2 眼睛追蹤檔</span><span class="sxs-lookup"><span data-stu-id="d9623-139">HoloLens 2 Eye Tracking Documentation</span></span>](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)
