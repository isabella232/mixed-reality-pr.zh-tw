---
title: EyeTracking_EyeGazeProvider
description: MRTK 中的眼睛注視提供者檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、EyeGaze、
ms.openlocfilehash: b0941fed5801d7b6d9d1d1fde999a24a9d5adb6e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692635"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>存取 Unity 腳本中的眼睛追蹤資料

本文假設您已瞭解如何在 MRTK 場景中設定眼睛追蹤 (請參閱 [基本的 MRTK 安裝程式以使用眼睛追蹤](EyeTracking_BasicSetup.md)) 。
存取 MonoBehaviour 腳本中的眼睛追蹤資料很簡單！ 只要使用 *CoreServices. InputSystem. EyeGazeProvider*。

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

MRTK 中的眼睛追蹤設定是透過介面進行設定 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 。 使用 [CoreServices](EyeTracking_EyeGazeProvider.md) 時，會提供在執行時間的工具組中註冊的預設注視提供者實作為。
的實用屬性 `EyeGazeProvider` 如下所述。

- **IsEyeTrackingEnabled**：如果使用者已選擇使用眼睛追蹤，則為 True。

- **IsEyeCalibrationValid**：指出使用者的眼睛追蹤校正是否有效。
如果值尚未收到來自眼睛追蹤系統的資料，它會傳回 ' null '。
這可能是不正確，因為使用者略過眼睛追蹤校正。

- **IsEyeTrackingEnabledAndValid**：指出目前的眼睛追蹤資料是否目前用於注視。

- **IsEyeTrackingDataValid**：如果有可用的眼睛追蹤資料，則為 True。
它可能因為超過 timeout 而無法使用 (在) 或缺乏追蹤硬體或許可權的情況之下，應能穩固地提供使用者閃爍。
查看我們 [遺漏的眼睛校正通知範例](EyeTracking_IsUserCalibrated.md) ，其說明如何偵測使用者是否為眼睛的校正，並顯示適當的通知。

- **GazeOrigin**：注視光線的原點。
請注意，如果 ' IsEyeGazeValid ' 為 false，則會傳回 *標頭* 的原點。

- **GazeDirection**：注視光線的方向。
如果 ' IsEyeGazeValid ' 為 false，則會傳回 *標頭* 。

- **HitInfo**、 **HitPosition**、 **HitNormal** 等等：目前 Gazed 在目標上的相關資訊。
同樣地，如果 `IsEyeGazeValid` 是 false，則會以使用者的 *標頭* 為基礎。

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>使用 CoreServices 的範例 InputSystem. EyeGazeProvider

以下是來自 [FollowEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)的範例：

- 取得使用者所查看的全息圖點：

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- 顯示與使用者目前正在尋找的固定距離的視覺資產：

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a>另請參閱

- [MRTK 眼追蹤總覽](EyeTracking_Main.md)
- [MRTK 眼睛追蹤設定](EyeTracking_BasicSetup.md)
- [MRTK 眼睛追蹤校正](EyeTracking_IsUserCalibrated.md)
- [HoloLens 2 眼睛追蹤檔](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)
