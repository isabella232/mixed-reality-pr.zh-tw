---
title: 輸入狀態
description: MRTK 中輸入狀態的相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、InputState、
ms.openlocfilehash: 4c1bd115c63e25decf73c082546e75b0f276a7ef
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145256"
---
# <a name="accessing-input-state-in-mrtk"></a>存取 MRTK 中的輸入狀態

您可以逐一查看附加至輸入來源的控制器，以直接查詢 MRTK 中所有輸入的狀態。 MRTK 也提供便利的方法，讓您存取眼睛、手、head 和移動控制器的位置和旋轉。

如需透過逐一查看控制器，以及使用類別來查詢輸入的範例，請參閱 InputDataExample 場景 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 。

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>範例：存取位置、列印頭的旋轉、手 MRTK 中的眼睛

MRTK 的 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 類別提供便利的方法來存取手形、頭部光線、眼睛光線和移動控制器光線。

```c#
// Get the head ray
var headRay = InputRayUtils.GetHeadGazeRay();

// Get the right hand ray
Ray rightHandRay;
if(InputRayUtils.TryGetHandRay(Handedness.right, rightHandRay))
{
    // Right hand ray is available
}
else
{
    // Right hand ray is not available
}
```

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>範例：存取位置、場景中所有作用中6DOF 控制器的旋轉

```c#
foreach(var controller in CoreServices.InputSystem.DetectedControllers)
{
    // Interactions for a controller is the list of inputs that this controller exposes
    foreach(MixedRealityInteractionMapping inputMapping in controller.Interactions)
    {
        // 6DOF controllers support the "SpatialPointer" type (pointing direction)
        // or "GripPointer" type (direction of the 6DOF controller)
        if (inputMapping.InputType == DeviceInputType.SpatialPointer)
        {
            Debug.Log("spatial pointer PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial pointer RotationData: " + inputMapping.RotationData);
        }

        if (inputMapping.InputType == DeviceInputType.SpatialGrip)
        {
            Debug.Log("spatial grip PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial grip RotationData: " + inputMapping.RotationData);
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- [InputEvents](input-events.md)
- [指標](pointers.md)
- [HandTracking](hand-tracking.md)
