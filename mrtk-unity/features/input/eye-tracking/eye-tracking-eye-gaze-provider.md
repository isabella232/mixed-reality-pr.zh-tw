---
title: EyeTracking_EyeGazeProvider
description: MRTK 中的眼睛注視提供者檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、EyeGaze、
ms.openlocfilehash: 59bb981748eff5b50c10c74e346b7b3413e25843
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550568"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="0ca61-104">存取 Unity 腳本中的眼睛追蹤資料</span><span class="sxs-lookup"><span data-stu-id="0ca61-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="0ca61-105">本文假設您已瞭解如何在 MRTK 場景中設定眼睛追蹤 (請參閱 [基本的 MRTK 安裝程式以使用眼睛追蹤](eye-tracking-basic-setup.md)) 。</span><span class="sxs-lookup"><span data-stu-id="0ca61-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)).</span></span>
<span data-ttu-id="0ca61-106">存取 MonoBehaviour 腳本中的眼睛追蹤資料很簡單！</span><span class="sxs-lookup"><span data-stu-id="0ca61-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="0ca61-107">只要使用 *CoreServices. InputSystem. EyeGazeProvider*。</span><span class="sxs-lookup"><span data-stu-id="0ca61-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="0ca61-108">IMixedRealityEyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="0ca61-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="0ca61-109">MRTK 中的眼睛追蹤設定是透過介面進行設定 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 。</span><span class="sxs-lookup"><span data-stu-id="0ca61-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="0ca61-110">使用 [CoreServices](eye-tracking-eye-gaze-provider.md) 時，會提供在執行時間的工具組中註冊的預設注視提供者實作為。</span><span class="sxs-lookup"><span data-stu-id="0ca61-110">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="0ca61-111">的實用屬性 `EyeGazeProvider` 如下所述。</span><span class="sxs-lookup"><span data-stu-id="0ca61-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="0ca61-112">**IsEyeTrackingEnabled**：如果使用者已選擇使用眼睛追蹤，則為 True。</span><span class="sxs-lookup"><span data-stu-id="0ca61-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="0ca61-113">**IsEyeCalibrationValid**：指出使用者的眼睛追蹤校正是否有效。</span><span class="sxs-lookup"><span data-stu-id="0ca61-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="0ca61-114">如果值尚未收到來自眼睛追蹤系統的資料，它會傳回 ' null '。</span><span class="sxs-lookup"><span data-stu-id="0ca61-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="0ca61-115">這可能是不正確，因為使用者略過眼睛追蹤校正。</span><span class="sxs-lookup"><span data-stu-id="0ca61-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="0ca61-116">**IsEyeTrackingEnabledAndValid**：指出目前的眼睛追蹤資料是否目前用於注視。</span><span class="sxs-lookup"><span data-stu-id="0ca61-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="0ca61-117">**IsEyeTrackingDataValid**：如果有可用的眼睛追蹤資料，則為 True。</span><span class="sxs-lookup"><span data-stu-id="0ca61-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="0ca61-118">它可能因為超過 timeout 而無法使用 (在) 或缺乏追蹤硬體或許可權的情況之下，應能穩固地提供使用者閃爍。</span><span class="sxs-lookup"><span data-stu-id="0ca61-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="0ca61-119">查看我們 [遺漏的眼睛校正通知範例](eye-tracking-is-user-calibrated.md) ，其說明如何偵測使用者是否為眼睛的校正，並顯示適當的通知。</span><span class="sxs-lookup"><span data-stu-id="0ca61-119">Check out our [Missing eye calibration notification sample](eye-tracking-is-user-calibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="0ca61-120">**GazeOrigin**：注視光線的原點。</span><span class="sxs-lookup"><span data-stu-id="0ca61-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="0ca61-121">請注意，如果 ' IsEyeGazeValid ' 為 false，則會傳回 *標頭* 的原點。</span><span class="sxs-lookup"><span data-stu-id="0ca61-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="0ca61-122">**GazeDirection**：注視光線的方向。</span><span class="sxs-lookup"><span data-stu-id="0ca61-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="0ca61-123">如果 ' IsEyeGazeValid ' 為 false，則會傳回 *標頭* 。</span><span class="sxs-lookup"><span data-stu-id="0ca61-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="0ca61-124">**HitInfo**、 **HitPosition**、 **HitNormal** 等等：目前 Gazed 在目標上的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0ca61-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="0ca61-125">同樣地，如果 `IsEyeGazeValid` 是 false，則會以使用者的 *標頭* 為基礎。</span><span class="sxs-lookup"><span data-stu-id="0ca61-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="0ca61-126">使用 CoreServices 的範例 InputSystem. EyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="0ca61-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="0ca61-127">以下是來自 [FollowEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)的範例：</span><span class="sxs-lookup"><span data-stu-id="0ca61-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="0ca61-128">取得使用者所查看的全息圖點：</span><span class="sxs-lookup"><span data-stu-id="0ca61-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="0ca61-129">顯示與使用者目前正在尋找的固定距離的視覺資產：</span><span class="sxs-lookup"><span data-stu-id="0ca61-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="0ca61-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ca61-130">See also</span></span>

- [<span data-ttu-id="0ca61-131">MRTK 眼追蹤總覽</span><span class="sxs-lookup"><span data-stu-id="0ca61-131">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="0ca61-132">MRTK 眼睛追蹤設定</span><span class="sxs-lookup"><span data-stu-id="0ca61-132">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="0ca61-133">MRTK 眼睛追蹤校正</span><span class="sxs-lookup"><span data-stu-id="0ca61-133">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="0ca61-134">HoloLens 2 眼睛追蹤檔</span><span class="sxs-lookup"><span data-stu-id="0ca61-134">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)