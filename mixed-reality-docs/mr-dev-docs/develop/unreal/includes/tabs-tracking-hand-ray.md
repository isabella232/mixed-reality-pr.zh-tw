---
ms.openlocfilehash: 23bba22801f61f6b4814991c8b3bde68d2c5f6b7
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002695"
---
# <a name="425"></a>[<span data-ttu-id="064d8-101">4.25</span><span class="sxs-lookup"><span data-stu-id="064d8-101">4.25</span></span>](#tab/425)

<span data-ttu-id="064d8-102">若要在藍圖中使用手片，請搜尋 **WINDOWS MIXED REALITY HMD** 下的任何動作：</span><span class="sxs-lookup"><span data-stu-id="064d8-102">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![手中的最佳光線](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="064d8-104">若要以 c + + 存取它們，請將加入 `WindowsMixedRealityFunctionLibrary.h` 至呼叫程式碼檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="064d8-104">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="064d8-105">列舉</span><span class="sxs-lookup"><span data-stu-id="064d8-105">Enum</span></span>

<span data-ttu-id="064d8-106">您也可以存取 **EHMDInputControllerButtons** 下的輸入案例，此案例可用於藍圖：</span><span class="sxs-lookup"><span data-stu-id="064d8-106">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![輸入控制器按鈕](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="064d8-108">若要在 c + + 中存取，請使用 `EHMDInputControllerButtons` 列舉類別：</span><span class="sxs-lookup"><span data-stu-id="064d8-108">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="064d8-109">以下是兩個適用列舉案例的明細：</span><span class="sxs-lookup"><span data-stu-id="064d8-109">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="064d8-110">**選取** 使用者觸發的選取事件。</span><span class="sxs-lookup"><span data-stu-id="064d8-110">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="064d8-111">在 HoloLens 2 中，藉由按下按鍵、注視和認可，或藉由在啟用 [語音輸入](../unreal-voice-input.md) 時說出「選取」來觸發。</span><span class="sxs-lookup"><span data-stu-id="064d8-111">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="064d8-112">**理解** 使用者觸發的理解事件。</span><span class="sxs-lookup"><span data-stu-id="064d8-112">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="064d8-113">在 HoloLens 2 中，藉由關閉使用者的手指來觸發。</span><span class="sxs-lookup"><span data-stu-id="064d8-113">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="064d8-114">您可以透過如下所示的列舉，在 c + + 中存取您的手形網格追蹤狀態 `EHMDTrackingStatus` ：</span><span class="sxs-lookup"><span data-stu-id="064d8-114">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="064d8-115">以下是兩個適用列舉案例的明細：</span><span class="sxs-lookup"><span data-stu-id="064d8-115">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="064d8-116">**NotTracked** –不可見的手</span><span class="sxs-lookup"><span data-stu-id="064d8-116">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="064d8-117">已 **追蹤**--已完整追蹤手</span><span class="sxs-lookup"><span data-stu-id="064d8-117">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="064d8-118">結構</span><span class="sxs-lookup"><span data-stu-id="064d8-118">Struct</span></span>

<span data-ttu-id="064d8-119">PointerPoseInfo 結構可以提供下列資料的資訊：</span><span class="sxs-lookup"><span data-stu-id="064d8-119">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="064d8-120">**原點** –手的原點</span><span class="sxs-lookup"><span data-stu-id="064d8-120">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="064d8-121">**方向** –手形方向</span><span class="sxs-lookup"><span data-stu-id="064d8-121">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="064d8-122">**向上** –向上向量</span><span class="sxs-lookup"><span data-stu-id="064d8-122">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="064d8-123">**方向** –方向四元數</span><span class="sxs-lookup"><span data-stu-id="064d8-123">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="064d8-124">**追蹤狀態** -目前的追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="064d8-124">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="064d8-125">您可以透過藍圖存取 PointerPoseInfo 結構，如下所示：</span><span class="sxs-lookup"><span data-stu-id="064d8-125">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![指標姿勢資訊 BP](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="064d8-127">或使用 c + +：</span><span class="sxs-lookup"><span data-stu-id="064d8-127">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="064d8-128">函式</span><span class="sxs-lookup"><span data-stu-id="064d8-128">Functions</span></span>

<span data-ttu-id="064d8-129">您可以在每個畫面上呼叫以下列出的所有函式，以允許連續監視。</span><span class="sxs-lookup"><span data-stu-id="064d8-129">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="064d8-130">**取得指標姿勢資訊** 會傳回目前框架中的手光線方向的完整資訊。</span><span class="sxs-lookup"><span data-stu-id="064d8-130">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="064d8-131">藍圖：</span><span class="sxs-lookup"><span data-stu-id="064d8-131">Blueprint:</span></span>

![取得指標姿勢資訊](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="064d8-133">C++：</span><span class="sxs-lookup"><span data-stu-id="064d8-133">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="064d8-134">如果在目前的框架中 Grasped 手， **Grasped 會** 傳回 true。</span><span class="sxs-lookup"><span data-stu-id="064d8-134">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="064d8-135">藍圖：</span><span class="sxs-lookup"><span data-stu-id="064d8-135">Blueprint:</span></span>

![為 Grasped BP](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="064d8-137">C++：</span><span class="sxs-lookup"><span data-stu-id="064d8-137">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="064d8-138">如果使用者在目前的框架中觸發了 Select，**則 [已按下] 會** 傳回 true。</span><span class="sxs-lookup"><span data-stu-id="064d8-138">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="064d8-139">藍圖：</span><span class="sxs-lookup"><span data-stu-id="064d8-139">Blueprint:</span></span>

![選取 [按下 BP]](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="064d8-141">C++：</span><span class="sxs-lookup"><span data-stu-id="064d8-141">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="064d8-142">**按一下按鈕時** ，如果在目前的框架中觸發事件或按鈕，則會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="064d8-142">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="064d8-143">藍圖：</span><span class="sxs-lookup"><span data-stu-id="064d8-143">Blueprint:</span></span>

![按鈕是否按下 BP](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="064d8-145">C++：</span><span class="sxs-lookup"><span data-stu-id="064d8-145">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="064d8-146">**取得控制器追蹤狀態** 會傳回目前框架中的追蹤狀態。</span><span class="sxs-lookup"><span data-stu-id="064d8-146">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="064d8-147">藍圖：</span><span class="sxs-lookup"><span data-stu-id="064d8-147">Blueprint:</span></span>

![取得控制器追蹤狀態 BP](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="064d8-149">C++：</span><span class="sxs-lookup"><span data-stu-id="064d8-149">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
# <a name="426"></a>[<span data-ttu-id="064d8-150">4.26</span><span class="sxs-lookup"><span data-stu-id="064d8-150">4.26</span></span>](#tab/426)

<span data-ttu-id="064d8-151">若要取得手片的資料，您應該使用上一節中的 Get 移動控制器資料函數。</span><span class="sxs-lookup"><span data-stu-id="064d8-151">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="064d8-152">傳回的結構包含兩個參數，您可以使用這兩個參數來建立手光線– **目標位置** 和 **目標旋轉**。</span><span class="sxs-lookup"><span data-stu-id="064d8-152">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="064d8-153">這些參數會形成您的肘線所導向的光線。</span><span class="sxs-lookup"><span data-stu-id="064d8-153">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="064d8-154">您應該採用它們，並尋找所指向的全像影像。</span><span class="sxs-lookup"><span data-stu-id="064d8-154">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="064d8-155">以下是判斷手光線是否叫用小工具和設定自訂命中結果的範例：</span><span class="sxs-lookup"><span data-stu-id="064d8-155">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![取得移動控制器資料函式的藍圖](../images/unreal-hand-tracking-img-04.png) 