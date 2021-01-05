---
ms.openlocfilehash: 6b9223481ed909961dbb88d03e4b55ef68448525
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2020
ms.locfileid: "97718124"
---
# <a name="426"></a>[<span data-ttu-id="8a611-101">4.26</span><span class="sxs-lookup"><span data-stu-id="8a611-101">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="8a611-102">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8a611-102">Windows Mixed Reality</span></span>

![事件開始播放的藍圖已連線到設定手勢函式](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="8a611-104">然後，您應該加入程式碼以訂閱下列事件：</span><span class="sxs-lookup"><span data-stu-id="8a611-104">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="8a611-105">![Windows 空間輸入的藍圖、點擊和左側操作手勢 ](../images/unreal/key-events.png)
 ![ 螢幕擷取畫面： [詳細資料] 面板中的 [windows 空間輸入] 點擊手勢選項](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="8a611-105">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="8a611-106">OpenXR</span><span class="sxs-lookup"><span data-stu-id="8a611-106">OpenXR</span></span>

<span data-ttu-id="8a611-107">在 OpenXR 中，手勢事件是透過輸入管線來追蹤。</span><span class="sxs-lookup"><span data-stu-id="8a611-107">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="8a611-108">裝置可以使用手邊互動，自動辨識點擊和按住手勢，而不是其他筆勢。</span><span class="sxs-lookup"><span data-stu-id="8a611-108">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="8a611-109">這些名稱會命名為 OpenXRMsftHandInteraction Select 和框對應。</span><span class="sxs-lookup"><span data-stu-id="8a611-109">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="8a611-110">您不需要啟用訂用帳戶，您應該在專案設定/引擎/輸入中宣告事件，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="8a611-110">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![OpenXR 動作對應的螢幕擷取畫面](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[<span data-ttu-id="8a611-112">4.25</span><span class="sxs-lookup"><span data-stu-id="8a611-112">4.25</span></span>](#tab/425)

<span data-ttu-id="8a611-113">您可以在 [ **Windows Mixed Reality 空間輸入**] 下找到藍圖函式，然後在呼叫程式碼檔案中加入 c + + 函式 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 。</span><span class="sxs-lookup"><span data-stu-id="8a611-113">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![捕捉手勢](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="8a611-115">列舉</span><span class="sxs-lookup"><span data-stu-id="8a611-115">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="8a611-116">藍圖：</span><span class="sxs-lookup"><span data-stu-id="8a611-116">Blueprint:</span></span>

![手勢類型](../images/unreal/gesture-type.png)

<span data-ttu-id="8a611-118">C++：</span><span class="sxs-lookup"><span data-stu-id="8a611-118">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="8a611-119">函數</span><span class="sxs-lookup"><span data-stu-id="8a611-119">Function</span></span>
<span data-ttu-id="8a611-120">您可以使用函數來啟用和停用手勢捕捉 `CaptureGestures` 。</span><span class="sxs-lookup"><span data-stu-id="8a611-120">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="8a611-121">當已啟用的手勢引發輸入事件時， `true` 如果手勢捕捉成功，則函式會傳回，如果發生錯誤，則會傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="8a611-121">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="8a611-122">藍圖：</span><span class="sxs-lookup"><span data-stu-id="8a611-122">Blueprint:</span></span>

![捕捉手勢 BP](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="8a611-124">C++：</span><span class="sxs-lookup"><span data-stu-id="8a611-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="8a611-125">以下是重要事件，您可以在藍圖和 c + +：關鍵事件中找到這些事件 ![](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="8a611-125">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

![關鍵事件2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

