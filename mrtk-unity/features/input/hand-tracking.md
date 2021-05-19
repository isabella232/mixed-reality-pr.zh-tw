---
title: 手動追蹤
description: 有關如何在 MRTK 中使用 HandTracking 的檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、手追蹤、
ms.openlocfilehash: 6cd55bc76d9fba42640954bcbf50e62f66454a94
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143356"
---
# <a name="hand-tracking"></a><span data-ttu-id="6ddd9-104">手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="6ddd9-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="6ddd9-105">手動追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="6ddd9-105">Hand tracking profile</span></span>

<span data-ttu-id="6ddd9-106">在 _輸入系統設定檔_ 下可找到 _手邊的追蹤設定檔_。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="6ddd9-107">它包含自訂手形表示的設定。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a><span data-ttu-id="6ddd9-108">聯合 prefabs</span><span class="sxs-lookup"><span data-stu-id="6ddd9-108">Joint prefabs</span></span>

<span data-ttu-id="6ddd9-109">聯合 prefabs 會使用簡單的 prefabs 來視覺化。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="6ddd9-110">_手掌_ 和 _食指_ 的接點具有特殊重要性，而且有自己的預製專案，而其他所有接點則共用相同的預製專案。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="6ddd9-111">根據預設，prefabs 是簡單的幾何基本專案。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="6ddd9-112">您可以視需要取代這些。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-112">These can be replaced if desired.</span></span> <span data-ttu-id="6ddd9-113">如果未指定任何預製專案，則會改為建立空的 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="6ddd9-114">避免在聯合 prefabs 中使用複雜的腳本或昂貴的轉譯，因為聯合物件會在每個框架上轉換，而且可能會有顯著的效能成本！</span><span class="sxs-lookup"><span data-stu-id="6ddd9-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="6ddd9-115">預設手聯合標記法</span><span class="sxs-lookup"><span data-stu-id="6ddd9-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="6ddd9-116">聯合標籤</span><span class="sxs-lookup"><span data-stu-id="6ddd9-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="6ddd9-117">手上網格預製專案</span><span class="sxs-lookup"><span data-stu-id="6ddd9-117">Hand mesh prefab</span></span>

<span data-ttu-id="6ddd9-118">如果手動定義的網格資料是由手形追蹤裝置所提供，就會使用手形網格。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="6ddd9-119">預製專案中的網狀呈現會由裝置中的資料所取代，因此虛擬網格（如 cube）即已足夠。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="6ddd9-120">預製專案的材質用於手形網格。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-120">The material of the prefab is used for the hand mesh.</span></span>

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

<span data-ttu-id="6ddd9-121">手顯示器顯示可能會對效能造成明顯的影響，因此可以透過取消核取 [ **啟用手形視覺效果** ] 選項來完全停用。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-121">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="6ddd9-122">手形視覺效果設定</span><span class="sxs-lookup"><span data-stu-id="6ddd9-122">Hand visualization settings</span></span>

<span data-ttu-id="6ddd9-123">您可以透過「 *手狀視覺效果模式* 」設定來關閉或開啟手邊網格和手入的視覺效果，並分別獲得 *聯合的視覺效果模式* 。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-123">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="6ddd9-124">這些設定是特定的應用程式模式，這表示在編輯器中可以開啟某些功能 (以查看與編輯器內模擬的接點，例如) ，同時在將播放程式組建中的裝置 (部署至裝置) 時，關閉相同的功能。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-124">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="6ddd9-125">請注意，一般而言，建議您在編輯器中開啟手動聯合視覺效果 (如此一來，編輯器內的模擬將會顯示) 的位置，並在播放程式 (中關閉手中的聯結視覺效果和手形視覺效果，因為它們會產生效能點擊) 。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-125">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="6ddd9-126">指令碼</span><span class="sxs-lookup"><span data-stu-id="6ddd9-126">Scripting</span></span>

<span data-ttu-id="6ddd9-127">您可以從輸入系統要求位置和旋轉，讓每個個別的手聯合成為 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-127">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="6ddd9-128">或者，系統允許存取遵循接點的 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-128">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="6ddd9-129">如果另一個 GameObject 應該持續追蹤聯合，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-129">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="6ddd9-130">可用的接點會列在 [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) 列舉中。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-130">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="6ddd9-131">當手動追蹤遺失時，會終結聯合物件！</span><span class="sxs-lookup"><span data-stu-id="6ddd9-131">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="6ddd9-132">確定任何使用聯合物件的腳本都會 `null` 正常處理案例，以避免發生錯誤！</span><span class="sxs-lookup"><span data-stu-id="6ddd9-132">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="6ddd9-133">存取指定的手型控制器</span><span class="sxs-lookup"><span data-stu-id="6ddd9-133">Accessing a given hand controller</span></span>

<span data-ttu-id="6ddd9-134">特定的站控制器通常可供使用，例如處理輸入事件時。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-134">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="6ddd9-135">在此情況下，您可以使用介面，直接從裝置要求聯合資料 [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-135">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="6ddd9-136">從控制器輪詢聯合姿勢</span><span class="sxs-lookup"><span data-stu-id="6ddd9-136">Polling joint pose from controller</span></span>

<span data-ttu-id="6ddd9-137">[`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) `false` 如果要求的聯合因為某些原因而無法使用，則函式會傳回。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-137">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="6ddd9-138">在這種情況下，結果會是 [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) 。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-138">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="6ddd9-139">從手形視覺化的聯合轉換</span><span class="sxs-lookup"><span data-stu-id="6ddd9-139">Joint transform from hand visualizer</span></span>

<span data-ttu-id="6ddd9-140">您可以從 [控制器視覺化](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)要求聯合物件。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-140">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a><span data-ttu-id="6ddd9-141">簡化的聯合資料存取</span><span class="sxs-lookup"><span data-stu-id="6ddd9-141">Simplified joint data access</span></span>

<span data-ttu-id="6ddd9-142">如果未指定特定的控制器，則會提供公用程式類別，方便您方便存取來取得聯合資料。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-142">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="6ddd9-143">這些函式會從目前追蹤的第一個可用裝置要求聯合資料。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-143">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="6ddd9-144">從 HandJointUtils 輪詢聯合姿勢</span><span class="sxs-lookup"><span data-stu-id="6ddd9-144">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="6ddd9-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) 是查詢第一個現用手裝置的靜態類別。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="6ddd9-146">來自手聯合服務的聯合轉換</span><span class="sxs-lookup"><span data-stu-id="6ddd9-146">Joint transform from hand joint service</span></span>

<span data-ttu-id="6ddd9-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) 保留一組持續性的 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 來追蹤接點。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="6ddd9-148">手動追蹤事件</span><span class="sxs-lookup"><span data-stu-id="6ddd9-148">Hand tracking events</span></span>

<span data-ttu-id="6ddd9-149">如果您不想要直接從控制器輪詢資料，輸入系統也會提供事件。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-149">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="6ddd9-150">聯合事件</span><span class="sxs-lookup"><span data-stu-id="6ddd9-150">Joint events</span></span>

<span data-ttu-id="6ddd9-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) 處理聯合位置的更新。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a><span data-ttu-id="6ddd9-152">網格事件</span><span class="sxs-lookup"><span data-stu-id="6ddd9-152">Mesh events</span></span>

<span data-ttu-id="6ddd9-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) 處理已被明確表達的手網格變更。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="6ddd9-154">請注意，預設並不會啟用手形網格。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-154">Note that hand meshes are not enabled by default.</span></span>

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a><span data-ttu-id="6ddd9-155">已知問題</span><span class="sxs-lookup"><span data-stu-id="6ddd9-155">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="6ddd9-156">.NET Native</span><span class="sxs-lookup"><span data-stu-id="6ddd9-156">.NET Native</span></span>

<span data-ttu-id="6ddd9-157">目前使用 .NET 後端的主要組建有已知的問題。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-157">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="6ddd9-158">在 .NET Native 中， `IInspectable` 無法使用將指標從原生封送處理至 managed 程式碼 `Marshal.GetObjectForIUnknown` 。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-158">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="6ddd9-159">MRTK 會使用這個來取得，以便 `SpatialCoordinateSystem` 從平臺接收手和眼睛資料。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-159">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="6ddd9-160">我們已在 [原生混合現實工具](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)組存放庫中，提供 DLL 來源作為此問題的因應措施。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-160">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="6ddd9-161">請遵循讀我檔案中的指示，並將產生的二進位檔複製到 Unity 資產中的 [外掛程式] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-161">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="6ddd9-162">之後，MRTK 中提供的 WindowsMixedRealityUtilities 腳本將為您解決因應措施。</span><span class="sxs-lookup"><span data-stu-id="6ddd9-162">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="6ddd9-163">如果您想要建立自己的 DLL，或在現有的 DLL 中包含此因應措施，解決方法的核心是：</span><span class="sxs-lookup"><span data-stu-id="6ddd9-163">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="6ddd9-164">而且在您的 c # Unity 程式碼中使用：</span><span class="sxs-lookup"><span data-stu-id="6ddd9-164">And its use in your C# Unity code:</span></span>

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```
