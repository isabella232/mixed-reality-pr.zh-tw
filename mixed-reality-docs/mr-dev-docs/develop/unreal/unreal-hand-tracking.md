---
title: Unreal 中的手勢追蹤
description: 瞭解如何在 Unreal 混合現實應用程式中使用手追蹤輸入、姿勢、手形網格和即時連結動畫。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、手形追蹤、Unreal、Unreal 引擎4、UE4、HoloLens、HoloLens 2、混合現實、開發、功能、檔、指南、全像投影、遊戲開發、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: e482c93233348325736d2c224788e9174c1f3b67
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010158"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="cf7eb-104">Unreal 中的手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="cf7eb-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="cf7eb-105">手追蹤系統會使用某人的手掌和手指做為輸入。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="cf7eb-106">每個手指的位置和旋轉、完整的掌上和手手勢的資料都可以使用。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="cf7eb-107">從 Unreal 4.26 開始，手動追蹤是以 Unreal HeadMountedDisplay 外掛程式為基礎，並在所有 XR 平臺和裝置上使用通用 API。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="cf7eb-108">Windows Mixed Reality 和 OpenXR 系統的功能都相同。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="cf7eb-109">手姿勢</span><span class="sxs-lookup"><span data-stu-id="cf7eb-109">Hand pose</span></span>

<span data-ttu-id="cf7eb-110">手姿勢可讓您追蹤並使用使用者的手和手指作為輸入，可在藍圖和 c + + 中存取。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="cf7eb-111">Unreal API 會將資料傳送為座標系統，並與 Unreal 引擎同步處理刻度。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

![手形基本架構](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="cf7eb-113">手實況連結動畫</span><span class="sxs-lookup"><span data-stu-id="cf7eb-113">Hand Live Link Animation</span></span>

<span data-ttu-id="cf7eb-114">使用 [即時連結外掛程式](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)可對動畫公開手。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="cf7eb-115">如果已啟用 Windows Mixed Reality 和即時連結外掛程式：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="cf7eb-116">選取 [ **Window > 即時連結** ] 以開啟 [即時連結編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="cf7eb-117">選取 **來源** 並啟用 **Windows Mixed Reality 手追蹤來源**</span><span class="sxs-lookup"><span data-stu-id="cf7eb-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![即時連結來源](images/unreal/live-link-source.png)

<span data-ttu-id="cf7eb-119">啟用來源並開啟動畫資產之後，展開 [**預覽場景**] 索引標籤中的 [**動畫**] 區段，也會看到其他選項。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![即時連結動畫](images/unreal/live-link-animation.png)

<span data-ttu-id="cf7eb-121">手形動畫階層與中的相同 `EWMRHandKeypoint` 。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="cf7eb-122">動畫可以使用 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 重定目標：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![即時連結動畫2](images/unreal/live-link-animation2.png)

<span data-ttu-id="cf7eb-124">它也可以在編輯器中進行子類別化：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-124">It can also be subclassed in the editor:</span></span>

![即時連結重新對應](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="cf7eb-126">手上網格</span><span class="sxs-lookup"><span data-stu-id="cf7eb-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="cf7eb-127">以手動方式作為追蹤幾何</span><span class="sxs-lookup"><span data-stu-id="cf7eb-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf7eb-128">在 OpenXR 中取得作為追蹤幾何的手勢需要您呼叫 Set 使用具有 **啟用追蹤幾何** 的 **手形網格**。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="cf7eb-129">若要啟用該模式，您應該呼叫 Set 使用具有 **啟用追蹤幾何** 的 **手形網格**：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![事件開始播放的藍圖已連線到 set use 手勢函式已啟用追蹤幾何模式](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="cf7eb-131">這兩種模式都不可能同時啟用。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="cf7eb-132">如果您啟用了一個，另一個會自動停用。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="cf7eb-133">存取手形網格資料</span><span class="sxs-lookup"><span data-stu-id="cf7eb-133">Accessing Hand Mesh Data</span></span>

![手上網格](images/unreal/hand-mesh.png)

<span data-ttu-id="cf7eb-135">在您可以存取手中的資料之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="cf7eb-136">選取您的 **ARSessionConfig** 資產，展開 [ **AR 設定-> 世界對應** 設定]，然後核取 [ **從追蹤的幾何產生網格資料**]。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="cf7eb-137">以下是預設的網格參數：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="cf7eb-138">使用網格資料進行遮蔽</span><span class="sxs-lookup"><span data-stu-id="cf7eb-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="cf7eb-139">產生網格資料的衝突</span><span class="sxs-lookup"><span data-stu-id="cf7eb-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="cf7eb-140">產生網格資料的 Nav 網格</span><span class="sxs-lookup"><span data-stu-id="cf7eb-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="cf7eb-141">轉譯線框中的網格資料-debug 參數，可顯示產生的網格</span><span class="sxs-lookup"><span data-stu-id="cf7eb-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="cf7eb-142">這些參數值會當做空間對應網格和手邊網格預設值使用。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="cf7eb-143">您可以隨時在任何網格的藍圖或程式碼中變更它們。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="cf7eb-144">C + + API 參考</span><span class="sxs-lookup"><span data-stu-id="cf7eb-144">C++ API Reference</span></span>
<span data-ttu-id="cf7eb-145">用 `EEARObjectClassification` 來尋找所有可追蹤物件中的手網格值。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="cf7eb-146">當系統偵測到任何可追蹤物件（包括手形網格）時，會呼叫下列委派。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

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

<span data-ttu-id="cf7eb-147">請確定您的委派處理常式遵循以下的函數簽章：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="cf7eb-148">您可以透過下列步驟存取網格資料  `UARTrackedGeometry::GetUnderlyingMesh` ：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="cf7eb-149">藍圖 API 參考</span><span class="sxs-lookup"><span data-stu-id="cf7eb-149">Blueprint API Reference</span></span>

<span data-ttu-id="cf7eb-150">若要在藍圖中使用手形網格：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="cf7eb-151">將 **ARTrackableNotify** 元件新增至藍圖執行者</span><span class="sxs-lookup"><span data-stu-id="cf7eb-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="cf7eb-153">移至 [ **詳細資料** ] 面板，然後展開 [ **事件** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="cf7eb-155">在事件圖中使用下列節點覆寫新增/更新/移除追蹤幾何：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![ARTrackable 通知時](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="cf7eb-157">OpenXR 中的手中視覺效果</span><span class="sxs-lookup"><span data-stu-id="cf7eb-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="cf7eb-158">將手上網格視覺化的建議方式，是使用長篇的 XRVisualization 外掛程式搭配 [Microsoft OpenXR 外掛程式](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="cf7eb-159">然後，在藍圖編輯器中，您應該使用來自 [Microsoft OpenXR 外掛程式](https://github.com/microsoft/Microsoft-OpenXR-Unreal)的 **Set use 手型** 函式，並搭配 **Enabled XRVisualization** 作為參數：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![事件開始播放的藍圖已連線到 set use 手型函式已啟用 xrvisualization 模式](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="cf7eb-161">若要管理轉譯程式，您應該使用 XRVisualization 的 **Render 移動控制器** ：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![連接到轉譯移動控制器函式的 get 運動控制器資料函式藍圖](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="cf7eb-163">結果：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-163">The result:</span></span>

![以真實人為重迭的數位手影像](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="cf7eb-165">如果您需要更複雜的資訊，例如繪製具有自訂著色器的手形網格，您需要取得網格作為追蹤幾何。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="cf7eb-166">手部光線 (Hand Ray)</span><span class="sxs-lookup"><span data-stu-id="cf7eb-166">Hand rays</span></span>

<span data-ttu-id="cf7eb-167">取得手姿勢適用于接近物件或按下按鈕的接近互動。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="cf7eb-168">但是，有時候您需要處理離您的使用者更遠的全像影像。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="cf7eb-169">這可以透過手光線來完成，這可以用來作為 c + + 和藍圖中的指標裝置。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="cf7eb-170">您可以從手中畫出光線到目前為止，並透過 Unreal 光線追蹤的一些協助，來選取不觸及的全像影像。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="cf7eb-171">因為所有的函式結果都會變更每個畫面格，所以全都變成可呼叫。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="cf7eb-172">如需有關純和 impure 或可呼叫函式的詳細資訊，請參閱「函 [式上的](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)藍圖使用者 guid」。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="cf7eb-173">軌跡</span><span class="sxs-lookup"><span data-stu-id="cf7eb-173">Gestures</span></span>

<span data-ttu-id="cf7eb-174">HoloLens 2 會追蹤空間手勢，這表示您可以將這些手勢捕捉為輸入。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="cf7eb-175">軌跡追蹤是以訂用帳戶模型為基礎。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="cf7eb-176">您應該使用「設定手勢」函式來告訴裝置您要追蹤的手勢。 您可以在 [HoloLens 2 基本使用](https://docs.microsoft.com/hololens/hololens2-basic-usage) 方式檔中找到手勢的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="cf7eb-177">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="cf7eb-177">Next Development Checkpoint</span></span>

<span data-ttu-id="cf7eb-178">依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="cf7eb-179">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf7eb-180">本機空間錨點</span><span class="sxs-lookup"><span data-stu-id="cf7eb-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="cf7eb-181">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="cf7eb-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf7eb-182">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="cf7eb-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="cf7eb-183">您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
