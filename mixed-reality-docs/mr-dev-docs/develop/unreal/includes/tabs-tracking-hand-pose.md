---
ms.openlocfilehash: 21c29b2c8d540378259200cc834f7a36065f8ab3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581112"
---
# <a name="426"></a>[<span data-ttu-id="aff30-101">4.26</span><span class="sxs-lookup"><span data-stu-id="aff30-101">4.26</span></span>](#tab/426)

<span data-ttu-id="aff30-102">階層是由列舉所描述 `EHandKeypoint` ：</span><span class="sxs-lookup"><span data-stu-id="aff30-102">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![手 keypoint bluprint 選項的影像](../images/hand-keypoint-bp.png)

<span data-ttu-id="aff30-104">您可以使用 **Get 移動控制器資料** 函式，從使用者的手中取得所有資料。</span><span class="sxs-lookup"><span data-stu-id="aff30-104">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="aff30-105">該函數會傳回 **XRMotionControllerData** 結構。</span><span class="sxs-lookup"><span data-stu-id="aff30-105">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="aff30-106">以下是範例藍圖腳本，它會剖析 XRMotionControllerData 結構以取得手入位置，並在每個聯合的位置繪製一個 debug 座標系統。</span><span class="sxs-lookup"><span data-stu-id="aff30-106">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![依通道函數連接到行追蹤的 get 注視資料函式藍圖](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="aff30-108">請務必檢查結構是否有效，以及是否正確。</span><span class="sxs-lookup"><span data-stu-id="aff30-108">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="aff30-109">否則，您可能會在存取位置、旋轉和半徑陣列時取得未定義的行為。</span><span class="sxs-lookup"><span data-stu-id="aff30-109">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>

# <a name="425"></a>[<span data-ttu-id="aff30-110">4.25</span><span class="sxs-lookup"><span data-stu-id="aff30-110">4.25</span></span>](#tab/425)

<span data-ttu-id="aff30-111">`EWMRHandKeypoint`列舉會描述手形的骨骼階層。</span><span class="sxs-lookup"><span data-stu-id="aff30-111">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="aff30-112">您可以找到藍圖中列出的每個 keypoint：</span><span class="sxs-lookup"><span data-stu-id="aff30-112">You can find each hand keypoint listed in your Blueprints:</span></span>

![手 Keypoint BP](../images/hand-keypoint-bp.png)

<span data-ttu-id="aff30-114">完整的 c + + 列舉如下所示：</span><span class="sxs-lookup"><span data-stu-id="aff30-114">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="aff30-115">您可以在 [HandJointKind](/uwp/api/windows.perception.people.handjointkind) 資料表中找到每個列舉案例的數值。</span><span class="sxs-lookup"><span data-stu-id="aff30-115">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="aff30-116">支援手動追蹤</span><span class="sxs-lookup"><span data-stu-id="aff30-116">Supporting Hand Tracking</span></span>

<span data-ttu-id="aff30-117">您可以藉由新增 **支援** 手動追蹤 **> Windows Mixed Reality**，在藍圖中使用手邊追蹤：</span><span class="sxs-lookup"><span data-stu-id="aff30-117">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![手動追蹤 BP](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="aff30-119">`true`如果裝置上支援手形追蹤，而且 `false` 無法使用手形追蹤，此函式就會傳回。</span><span class="sxs-lookup"><span data-stu-id="aff30-119">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![支援手動追蹤 BP](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="aff30-121">C++：</span><span class="sxs-lookup"><span data-stu-id="aff30-121">C++:</span></span>

<span data-ttu-id="aff30-122">包含 `WindowsMixedRealityHandTrackingFunctionLibrary.h`。</span><span class="sxs-lookup"><span data-stu-id="aff30-122">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="aff30-123">取得追蹤</span><span class="sxs-lookup"><span data-stu-id="aff30-123">Getting Hand Tracking</span></span>

<span data-ttu-id="aff30-124">您可以使用 **GetHandJointTransform** 來傳回手中的空間資料。</span><span class="sxs-lookup"><span data-stu-id="aff30-124">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="aff30-125">資料會每個畫面格更新，但如果您在框架內，則會快取傳回的值。</span><span class="sxs-lookup"><span data-stu-id="aff30-125">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="aff30-126">基於效能考慮，不建議在此函式中使用繁重的邏輯。</span><span class="sxs-lookup"><span data-stu-id="aff30-126">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![取得手聯合轉換](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="aff30-128">C++：</span><span class="sxs-lookup"><span data-stu-id="aff30-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="aff30-129">以下是 GetHandJointTransform 函數參數的細目：</span><span class="sxs-lookup"><span data-stu-id="aff30-129">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="aff30-130">**手** –可以是使用者的左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="aff30-130">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="aff30-131">**Keypoint** –手形的骨骼。</span><span class="sxs-lookup"><span data-stu-id="aff30-131">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="aff30-132">**轉換** –骨骼基底的座標和方向。</span><span class="sxs-lookup"><span data-stu-id="aff30-132">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="aff30-133">您可以要求下一個骨骼的基底，以取得適用于骨骼結尾的轉換資料。</span><span class="sxs-lookup"><span data-stu-id="aff30-133">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="aff30-134">特殊的秘訣骨骼可提供 distal 的結尾。</span><span class="sxs-lookup"><span data-stu-id="aff30-134">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="aff30-135">\* \* 半徑：骨骼基底的半徑。</span><span class="sxs-lookup"><span data-stu-id="aff30-135">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="aff30-136">\* \* 傳回值-如果已追蹤此框架，則為 true; 如果未追蹤此骨骼，則為 false。</span><span class="sxs-lookup"><span data-stu-id="aff30-136">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>