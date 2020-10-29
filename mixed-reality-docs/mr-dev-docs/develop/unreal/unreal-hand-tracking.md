---
title: Unreal 中的手勢追蹤
description: 說明如何在 Unreal 中使用手動追蹤
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、手追蹤、Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、混合現實、開發、功能、檔、指南、全息全像遊戲開發
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91676901"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="1615d-104">Unreal 中的手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="1615d-104">Hand tracking in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="1615d-105">概觀</span><span class="sxs-lookup"><span data-stu-id="1615d-105">Overview</span></span>

<span data-ttu-id="1615d-106">手追蹤系統會使用某人的手掌和手指做為輸入。</span><span class="sxs-lookup"><span data-stu-id="1615d-106">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="1615d-107">您可以在程式碼中取得每個手指的位置和旋轉、整個掌，甚至手手勢。</span><span class="sxs-lookup"><span data-stu-id="1615d-107">You can get the position and rotation of every finger, the entire palm, and even hand gestures to use in your code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="1615d-108">手姿勢</span><span class="sxs-lookup"><span data-stu-id="1615d-108">Hand Pose</span></span>

<span data-ttu-id="1615d-109">手姿勢可讓您追蹤作用中使用者的手和手指，並將其作為輸入，您可以透過藍圖和 c + + 來存取。</span><span class="sxs-lookup"><span data-stu-id="1615d-109">Hand pose lets you track the hands and fingers of the active user and use it as input, which you can access through Blueprints and C++.</span></span> <span data-ttu-id="1615d-110">您可以在 Unreal 的 [HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API 中找到更多的技術詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1615d-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="1615d-111">Unreal API 會將資料傳送為座標系統，並與 Unreal 引擎同步處理刻度。</span><span class="sxs-lookup"><span data-stu-id="1615d-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="1615d-112">瞭解骨骼階層</span><span class="sxs-lookup"><span data-stu-id="1615d-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="1615d-113">`EWMRHandKeypoint`列舉會描述手形的骨骼階層。</span><span class="sxs-lookup"><span data-stu-id="1615d-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="1615d-114">您可以找到藍圖中列出的每個 keypoint：</span><span class="sxs-lookup"><span data-stu-id="1615d-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![手 Keypoint BP](images/hand-keypoint-bp.png)

<span data-ttu-id="1615d-116">完整的 c + + 列舉如下所示：</span><span class="sxs-lookup"><span data-stu-id="1615d-116">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="1615d-117">您可以在 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 資料表中找到每個列舉案例的數值。</span><span class="sxs-lookup"><span data-stu-id="1615d-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="1615d-118">下圖顯示具有相符列舉案例的整個手姿勢配置：</span><span class="sxs-lookup"><span data-stu-id="1615d-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![手形基本架構](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="1615d-120">支援手動追蹤</span><span class="sxs-lookup"><span data-stu-id="1615d-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="1615d-121">您可以藉由新增 **支援** 手動追蹤 **> Windows Mixed Reality** ，在藍圖中使用手邊追蹤：</span><span class="sxs-lookup"><span data-stu-id="1615d-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality** :</span></span>

![手動追蹤 BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="1615d-123">`true`如果裝置上支援手形追蹤，而且 `false` 無法使用手動追蹤，此函式就會傳回。</span><span class="sxs-lookup"><span data-stu-id="1615d-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking is not available.</span></span>

![支援手動追蹤 BP](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="1615d-125">C++：</span><span class="sxs-lookup"><span data-stu-id="1615d-125">C++:</span></span> 

<span data-ttu-id="1615d-126">包含 `WindowsMixedRealityHandTrackingFunctionLibrary.h`。</span><span class="sxs-lookup"><span data-stu-id="1615d-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="1615d-127">取得追蹤</span><span class="sxs-lookup"><span data-stu-id="1615d-127">Getting Hand Tracking</span></span>
<span data-ttu-id="1615d-128">您可以使用 **GetHandJointTransform** 來傳回手中的空間資料。</span><span class="sxs-lookup"><span data-stu-id="1615d-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="1615d-129">資料會每個畫面格更新，但如果您在框架內，則會快取傳回的值。</span><span class="sxs-lookup"><span data-stu-id="1615d-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="1615d-130">基於效能考慮，不建議在此函式中使用繁重的邏輯。</span><span class="sxs-lookup"><span data-stu-id="1615d-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![取得手聯合轉換](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="1615d-132">C++：</span><span class="sxs-lookup"><span data-stu-id="1615d-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="1615d-133">函數參數細目：</span><span class="sxs-lookup"><span data-stu-id="1615d-133">Function parameter breakdown:</span></span>

* <span data-ttu-id="1615d-134">**手形** –是使用者的左邊或右邊</span><span class="sxs-lookup"><span data-stu-id="1615d-134">**Hand** – an be the left or right hand of the user</span></span>
* <span data-ttu-id="1615d-135">**Keypoint** –手形的骨骼。</span><span class="sxs-lookup"><span data-stu-id="1615d-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="1615d-136">**轉換** –骨骼基底的座標和方向。</span><span class="sxs-lookup"><span data-stu-id="1615d-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="1615d-137">您可以要求下一個骨骼的基底，以取得適用于骨骼結尾的轉換資料。</span><span class="sxs-lookup"><span data-stu-id="1615d-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="1615d-138">特殊的秘訣骨骼可提供 distal 的結尾。</span><span class="sxs-lookup"><span data-stu-id="1615d-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="1615d-139">**半徑** ：骨骼基底的半徑。</span><span class="sxs-lookup"><span data-stu-id="1615d-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="1615d-140">傳回 **值** -如果已追蹤此框架，則為 true; 如果未追蹤此骨骼，則為 false。</span><span class="sxs-lookup"><span data-stu-id="1615d-140">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="1615d-141">手實況連結動畫</span><span class="sxs-lookup"><span data-stu-id="1615d-141">Hand Live Link Animation</span></span>
<span data-ttu-id="1615d-142">使用 [即時連結外掛程式](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)可對動畫公開手。</span><span class="sxs-lookup"><span data-stu-id="1615d-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="1615d-143">如果已啟用 Windows Mixed Reality 和即時連結外掛程式：</span><span class="sxs-lookup"><span data-stu-id="1615d-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="1615d-144">選取 [ **Window > 即時連結** ] 以開啟 [即時連結編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="1615d-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="1615d-145">按一下 [ **來源** ] 並啟用 **Windows Mixed Reality 手追蹤來源**</span><span class="sxs-lookup"><span data-stu-id="1615d-145">Click **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![即時連結來源](images/unreal/live-link-source.png)
 
<span data-ttu-id="1615d-147">啟用來源並開啟動畫資產之後，展開 [ **預覽場景** ] 索引標籤中的 [ **動畫** ] 區段，也會看到其他選項 (詳細資料位於 Unreal 的即時連結檔中-當外掛程式在 Beta 版中，此程式可能會在稍後) 變更。</span><span class="sxs-lookup"><span data-stu-id="1615d-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options (the details are in Unreal’s Live Link documentation - as the plugin is in beta, the process may change later).</span></span>

![即時連結動畫](images/unreal/live-link-animation.png)
 
<span data-ttu-id="1615d-149">手形動畫階層與中的相同 `EWMRHandKeypoint` 。</span><span class="sxs-lookup"><span data-stu-id="1615d-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="1615d-150">動畫可以使用 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 重定目標：</span><span class="sxs-lookup"><span data-stu-id="1615d-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** :</span></span>

![即時連結動畫2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="1615d-152">它也可以在編輯器中進行子類別化：</span><span class="sxs-lookup"><span data-stu-id="1615d-152">It can also be subclassed in the editor:</span></span>

![即時連結重新對應](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="1615d-154">存取手形網格資料</span><span class="sxs-lookup"><span data-stu-id="1615d-154">Accessing Hand Mesh Data</span></span>

![手上網格](images/unreal/hand-mesh.png)

<span data-ttu-id="1615d-156">在您可以存取手中的資料之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="1615d-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="1615d-157">選取您的 **ARSessionConfig** 資產，展開 [ **AR 設定-> 世界對應** 設定]，然後核取 [ **從追蹤的幾何產生網格資料** ]。</span><span class="sxs-lookup"><span data-stu-id="1615d-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry** .</span></span> 

<span data-ttu-id="1615d-158">以下是預設的網格參數：</span><span class="sxs-lookup"><span data-stu-id="1615d-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="1615d-159">使用網格資料進行遮蔽</span><span class="sxs-lookup"><span data-stu-id="1615d-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="1615d-160">產生網格資料的衝突</span><span class="sxs-lookup"><span data-stu-id="1615d-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="1615d-161">產生網格資料的 Nav 網格</span><span class="sxs-lookup"><span data-stu-id="1615d-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="1615d-162">轉譯線框中的網格資料-debug 參數，可顯示產生的網格</span><span class="sxs-lookup"><span data-stu-id="1615d-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="1615d-163">這些參數值會當做空間對應網格和手邊網格預設值使用。</span><span class="sxs-lookup"><span data-stu-id="1615d-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="1615d-164">您可以隨時在任何網格的藍圖或程式碼中變更它們。</span><span class="sxs-lookup"><span data-stu-id="1615d-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="1615d-165">C + + API 參考</span><span class="sxs-lookup"><span data-stu-id="1615d-165">C++ API Reference</span></span> 
<span data-ttu-id="1615d-166">用 `EEARObjectClassification` 來尋找所有可追蹤物件中的手網格值。</span><span class="sxs-lookup"><span data-stu-id="1615d-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="1615d-167">當系統偵測到任何可追蹤物件（包括手形網格）時，會呼叫下列委派。</span><span class="sxs-lookup"><span data-stu-id="1615d-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="1615d-168">請確定您的委派處理常式遵循以下的函數簽章：</span><span class="sxs-lookup"><span data-stu-id="1615d-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="1615d-169">您可以透過下列步驟存取網格資料  `UARTrackedGeometry::GetUnderlyingMesh` ：</span><span class="sxs-lookup"><span data-stu-id="1615d-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="1615d-170">藍圖 API 參考</span><span class="sxs-lookup"><span data-stu-id="1615d-170">Blueprint API Reference</span></span>

<span data-ttu-id="1615d-171">若要在藍圖中使用手形網格：</span><span class="sxs-lookup"><span data-stu-id="1615d-171">In order to work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="1615d-172">將 **ARTrackableNotify** 元件新增至藍圖執行者</span><span class="sxs-lookup"><span data-stu-id="1615d-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="1615d-174">移至 [ **詳細資料** ] 面板，然後展開 [ **事件** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="1615d-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="1615d-176">在事件圖中使用下列節點覆寫新增/更新/移除追蹤幾何：</span><span class="sxs-lookup"><span data-stu-id="1615d-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![ARTrackable 通知時](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="1615d-178">手光</span><span class="sxs-lookup"><span data-stu-id="1615d-178">Hand Rays</span></span>

<span data-ttu-id="1615d-179">您可以在 c + + 和藍圖中使用手光線作為指標裝置，以公開 [SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API。</span><span class="sxs-lookup"><span data-stu-id="1615d-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

<span data-ttu-id="1615d-180">請務必注意，因為所有函式的結果都會變更每個畫面格，所以它們全都變成可呼叫。</span><span class="sxs-lookup"><span data-stu-id="1615d-180">It’s important to mention that since the results of all the functions change every frame, they're all made callable.</span></span> <span data-ttu-id="1615d-181">如需有關純和 impure 或可呼叫函式的詳細資訊，請參閱藍圖的使用者 guid [功能](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span><span class="sxs-lookup"><span data-stu-id="1615d-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="1615d-182">若要在藍圖中使用手片，請搜尋 **WINDOWS MIXED REALITY HMD** 下的任何動作：</span><span class="sxs-lookup"><span data-stu-id="1615d-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD** :</span></span>

![手中的最佳光線](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="1615d-184">若要以 c + + 存取它們，請將加入 `WindowsMixedRealityFunctionLibrary.h` 至呼叫程式碼檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="1615d-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="1615d-185">列舉</span><span class="sxs-lookup"><span data-stu-id="1615d-185">Enum</span></span>
<span data-ttu-id="1615d-186">您也可以存取 **EHMDInputControllerButtons** 下的輸入案例，此案例可用於藍圖：</span><span class="sxs-lookup"><span data-stu-id="1615d-186">You also have access to input cases under **EHMDInputControllerButtons** , which can be used in Blueprints:</span></span>

![輸入控制器按鈕](images/unreal/input-controller-buttons.png)

<span data-ttu-id="1615d-188">若要在 c + + 中存取，請使用 `EHMDInputControllerButtons` 列舉類別：</span><span class="sxs-lookup"><span data-stu-id="1615d-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="1615d-189">以下是兩個適用列舉案例的明細：</span><span class="sxs-lookup"><span data-stu-id="1615d-189">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="1615d-190">**選取** 使用者觸發的選取事件。</span><span class="sxs-lookup"><span data-stu-id="1615d-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="1615d-191">您可以藉由點一下、注視和認可，或藉由在啟用 [語音輸入](unreal-voice-input.md) 的情況下說出「選取」，在 HoloLens 2 中觸發事件。</span><span class="sxs-lookup"><span data-stu-id="1615d-191">The event can be triggered in HoloLens 2 by air-tap, gaze and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="1615d-192">**理解** 使用者觸發的理解事件。</span><span class="sxs-lookup"><span data-stu-id="1615d-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="1615d-193">在 HoloLens 2 中，您可以關閉使用者的手指，以觸發此事件。</span><span class="sxs-lookup"><span data-stu-id="1615d-193">This event can be triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="1615d-194">您可以透過如下所示的列舉，在 c + + 中存取您的手形網格追蹤狀態 `EHMDTrackingStatus` ：</span><span class="sxs-lookup"><span data-stu-id="1615d-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="1615d-195">以下是兩個適用列舉案例的明細：</span><span class="sxs-lookup"><span data-stu-id="1615d-195">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="1615d-196">**NotTracked** –不可見的手</span><span class="sxs-lookup"><span data-stu-id="1615d-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="1615d-197">已 **追蹤** --已完整追蹤手</span><span class="sxs-lookup"><span data-stu-id="1615d-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="1615d-198">結構</span><span class="sxs-lookup"><span data-stu-id="1615d-198">Struct</span></span>
<span data-ttu-id="1615d-199">PointerPoseInfo 結構可以提供下列資料的資訊：</span><span class="sxs-lookup"><span data-stu-id="1615d-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>
* <span data-ttu-id="1615d-200">**原點** –手的原點</span><span class="sxs-lookup"><span data-stu-id="1615d-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="1615d-201">**方向** –手形方向</span><span class="sxs-lookup"><span data-stu-id="1615d-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="1615d-202">**向上** –向上向量</span><span class="sxs-lookup"><span data-stu-id="1615d-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="1615d-203">**方向** –方向四元數</span><span class="sxs-lookup"><span data-stu-id="1615d-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="1615d-204">**追蹤狀態** -目前的追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="1615d-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="1615d-205">您可以透過藍圖來存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1615d-205">You can access this through Blueprints, as shown below:</span></span>

![指標姿勢資訊 BP](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="1615d-207">或使用 c + +：</span><span class="sxs-lookup"><span data-stu-id="1615d-207">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="1615d-208">函式</span><span class="sxs-lookup"><span data-stu-id="1615d-208">Functions</span></span>

<span data-ttu-id="1615d-209">您可以在每個畫面上呼叫以下列出的所有函式，以允許連續監視。</span><span class="sxs-lookup"><span data-stu-id="1615d-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="1615d-210">**取得指標姿勢資訊** 會傳回目前框架中的手光線方向的完整資訊。</span><span class="sxs-lookup"><span data-stu-id="1615d-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="1615d-211">藍圖：</span><span class="sxs-lookup"><span data-stu-id="1615d-211">Blueprint:</span></span>

![取得指標姿勢資訊](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="1615d-213">C++：</span><span class="sxs-lookup"><span data-stu-id="1615d-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="1615d-214">如果在目前的框架中 Grasped 手， **Grasped 會** 傳回 true。</span><span class="sxs-lookup"><span data-stu-id="1615d-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="1615d-215">藍圖：</span><span class="sxs-lookup"><span data-stu-id="1615d-215">Blueprint:</span></span>

![為 Grasped BP](images/unreal/is-grasped-bp.png)

<span data-ttu-id="1615d-217">C++：</span><span class="sxs-lookup"><span data-stu-id="1615d-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="1615d-218">如果使用者在目前的框架中觸發了 Select， **則 [已按下] 會** 傳回 true。</span><span class="sxs-lookup"><span data-stu-id="1615d-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="1615d-219">藍圖：</span><span class="sxs-lookup"><span data-stu-id="1615d-219">Blueprint:</span></span>

![選取 [按下 BP]](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="1615d-221">C++：</span><span class="sxs-lookup"><span data-stu-id="1615d-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="1615d-222">**按一下按鈕時** ，如果在目前的框架中觸發事件或按鈕，則會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="1615d-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="1615d-223">藍圖：</span><span class="sxs-lookup"><span data-stu-id="1615d-223">Blueprint:</span></span>

![按鈕是否按下 BP](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="1615d-225">C++：</span><span class="sxs-lookup"><span data-stu-id="1615d-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="1615d-226">**取得控制器追蹤狀態** 會傳回目前框架中的追蹤狀態。</span><span class="sxs-lookup"><span data-stu-id="1615d-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="1615d-227">藍圖：</span><span class="sxs-lookup"><span data-stu-id="1615d-227">Blueprint:</span></span>

![取得控制器追蹤狀態 BP](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="1615d-229">C++：</span><span class="sxs-lookup"><span data-stu-id="1615d-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="1615d-230">軌跡</span><span class="sxs-lookup"><span data-stu-id="1615d-230">Gestures</span></span>

<span data-ttu-id="1615d-231">Hololens 2 可以追蹤空間手勢，這表示您可以將這些手勢視為輸入。</span><span class="sxs-lookup"><span data-stu-id="1615d-231">The Hololens 2 can track spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="1615d-232">您可以在 [HoloLens 2 基本使用](https://docs.microsoft.com/hololens/hololens2-basic-usage) 方式檔中找到手勢的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1615d-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="1615d-233">您可以在 [ **Windows Mixed Reality 空間輸入** ] 下找到藍圖函式，然後在呼叫程式碼檔案中加入 c + + 函式 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 。</span><span class="sxs-lookup"><span data-stu-id="1615d-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input** , and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![捕捉手勢](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="1615d-235">列舉</span><span class="sxs-lookup"><span data-stu-id="1615d-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="1615d-236">藍圖：</span><span class="sxs-lookup"><span data-stu-id="1615d-236">Blueprint:</span></span> 

![手勢類型](images/unreal/gesture-type.png)

<span data-ttu-id="1615d-238">C++：</span><span class="sxs-lookup"><span data-stu-id="1615d-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="1615d-239">函式</span><span class="sxs-lookup"><span data-stu-id="1615d-239">Function</span></span>
<span data-ttu-id="1615d-240">您可以使用函數來啟用和停用手勢捕捉 `CaptureGestures` 。</span><span class="sxs-lookup"><span data-stu-id="1615d-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="1615d-241">當已啟用的手勢引發輸入事件時， `true` 如果手勢捕捉成功，則函式會傳回，如果發生錯誤，則會傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="1615d-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="1615d-242">藍圖：</span><span class="sxs-lookup"><span data-stu-id="1615d-242">Blueprint:</span></span>

![捕捉手勢 BP](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="1615d-244">C++：</span><span class="sxs-lookup"><span data-stu-id="1615d-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="1615d-245">以下是重要事件，您可以在藍圖和 c + +：關鍵事件中找到這些事件 ![](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="1615d-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

![關鍵事件2](images/unreal/key-events2.png)
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

## <a name="next-development-checkpoint"></a><span data-ttu-id="1615d-247">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="1615d-247">Next Development Checkpoint</span></span>

<span data-ttu-id="1615d-248">如果您正在遵循我們所配置的 Unreal 開發檢查點旅程，您將在探索 MRTK 核心構成要素。</span><span class="sxs-lookup"><span data-stu-id="1615d-248">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="1615d-249">您可以從這裡繼續進行下一個組建區塊：</span><span class="sxs-lookup"><span data-stu-id="1615d-249">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="1615d-250">本機空間錨點</span><span class="sxs-lookup"><span data-stu-id="1615d-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="1615d-251">或跳至混合的現實平臺功能和 Api：</span><span class="sxs-lookup"><span data-stu-id="1615d-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1615d-252">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="1615d-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="1615d-253">您隨時都可以回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks) 。</span><span class="sxs-lookup"><span data-stu-id="1615d-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>