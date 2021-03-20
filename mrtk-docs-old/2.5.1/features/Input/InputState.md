---
title: InputState
description: MRTK 中輸入狀態的相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、InputState、
ms.openlocfilehash: 8ff3af6bdcc63e633025836226d50dcf95943fe0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694055"
---
# <a name="accessing-input-state-in-mrtk"></a><span data-ttu-id="6bc8d-104">存取 MRTK 中的輸入狀態</span><span class="sxs-lookup"><span data-stu-id="6bc8d-104">Accessing input state in MRTK</span></span>

<span data-ttu-id="6bc8d-105">您可以逐一查看附加至輸入來源的控制器，以直接查詢 MRTK 中所有輸入的狀態。</span><span class="sxs-lookup"><span data-stu-id="6bc8d-105">It's possible to directly query the state of all inputs in MRTK by iterating over the controllers attached to the input sources.</span></span> <span data-ttu-id="6bc8d-106">MRTK 也提供便利的方法，讓您存取眼睛、手、head 和移動控制器的位置和旋轉。</span><span class="sxs-lookup"><span data-stu-id="6bc8d-106">MRTK also provides convenience methods for accessing the position and rotation of the eyes, hands, head, and motion controller.</span></span>

<span data-ttu-id="6bc8d-107">如需透過逐一查看控制器，以及使用類別來查詢輸入的範例，請參閱 InputDataExample 場景 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 。</span><span class="sxs-lookup"><span data-stu-id="6bc8d-107">See the InputDataExample scene for an example of querying input both via iterating over controllers, and by using the [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class.</span></span>

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a><span data-ttu-id="6bc8d-108">範例：存取位置、列印頭的旋轉、手 MRTK 中的眼睛</span><span class="sxs-lookup"><span data-stu-id="6bc8d-108">Example: Access position, rotation of head, hands, eyes in MRTK</span></span>

<span data-ttu-id="6bc8d-109">MRTK 的 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 類別提供便利的方法來存取手形、頭部光線、眼睛光線和移動控制器光線。</span><span class="sxs-lookup"><span data-stu-id="6bc8d-109">MRTK's [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class provides convenience methods for accessing the hand ray, head ray, eye gaze ray, and motion controller rays.</span></span>

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

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a><span data-ttu-id="6bc8d-110">範例：存取位置、場景中所有作用中6DOF 控制器的旋轉</span><span class="sxs-lookup"><span data-stu-id="6bc8d-110">Example: Access position, rotation of all 6DOF controllers active in scene</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6bc8d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bc8d-111">See also</span></span>

- [<span data-ttu-id="6bc8d-112">InputEvents</span><span class="sxs-lookup"><span data-stu-id="6bc8d-112">InputEvents</span></span>](InputEvents.md)
- [<span data-ttu-id="6bc8d-113">指標</span><span class="sxs-lookup"><span data-stu-id="6bc8d-113">Pointers</span></span>](Pointers.md)
- [<span data-ttu-id="6bc8d-114">HandTracking</span><span class="sxs-lookup"><span data-stu-id="6bc8d-114">HandTracking</span></span>](HandTracking.md)
