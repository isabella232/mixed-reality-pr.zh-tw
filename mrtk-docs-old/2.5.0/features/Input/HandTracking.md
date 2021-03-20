---
title: HandTracking
description: 有關如何在 MRTK 中使用 HandTracking 的檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、手追蹤、
ms.openlocfilehash: a0a4a24425cd174d0cae478e08538e8cc887d624
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695485"
---
# <a name="hand-tracking"></a>手勢追蹤

## <a name="hand-tracking-profile"></a>手動追蹤設定檔

在 _輸入系統設定檔_ 下可找到 _手邊的追蹤設定檔_。 它包含自訂手形表示的設定。

<img src="../Images/Input/HandTrackingProfile.png" width="650px" alt="Hand Tracking profile" style="display:block;">

## <a name="joint-prefabs"></a>聯合 prefabs

聯合 prefabs 會使用簡單的 prefabs 來視覺化。 _手掌_ 和 _食指_ 的接點具有特殊重要性，而且有自己的預製專案，而其他所有接點則共用相同的預製專案。

根據預設，prefabs 是簡單的幾何基本專案。 您可以視需要取代這些。 如果未指定任何預製專案，則會改為建立空的 [gameobject](href:https://docs.unity3d.com/ScriptReference/GameObject.html) 。

> [!WARNING]
> 避免在聯合 prefabs 中使用複雜的腳本或昂貴的轉譯，因為聯合物件會在每個框架上轉換，而且可能會有顯著的效能成本！

預設手聯合標記法 |  聯合標籤
:-------------------------:|:-------------------------:
<img src="../Images/InputSimulation/ArticulatedHandJoints.png" height="300px" alt="Architecture handjoints"  style="display:inline;">  | <img src="../Images/InputSimulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>手上網格預製專案

如果手動定義的網格資料是由手形追蹤裝置所提供，就會使用手形網格。 預製專案中的網狀呈現會由裝置中的資料所取代，因此虛擬網格（如 cube）即已足夠。 預製專案的材質用於手形網格。

<img src="../Images/InputSimulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Articulated HandMesh" style="display:block;">

手顯示器顯示可能會對效能造成明顯的影響，因此可以透過取消核取 [ **啟用手形視覺效果** ] 選項來完全停用。

## <a name="hand-visualization-settings"></a>手形視覺效果設定

您可以透過「 *手狀視覺效果模式* 」設定來關閉或開啟手邊網格和手入的視覺效果，並分別獲得 *聯合的視覺效果模式* 。 這些設定是特定的應用程式模式，這表示在編輯器中可以開啟某些功能 (以查看與編輯器內模擬的接點，例如) ，同時在將播放程式組建中的裝置 (部署至裝置) 時，關閉相同的功能。

請注意，一般而言，建議您在編輯器中開啟手動聯合視覺效果 (如此一來，編輯器內的模擬將會顯示) 的位置，並在播放程式 (中關閉手中的聯結視覺效果和手形視覺效果，因為它們會產生效能點擊) 。

## <a name="scripting"></a>指令碼

您可以從輸入系統要求位置和旋轉，讓每個個別的手聯合成為 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 。

或者，系統允許存取遵循接點的 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 。 如果另一個 GameObject 應該持續追蹤聯合，這會很有用。

可用的接點會列在 [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) 列舉中。

> [!NOTE]
> 當手動追蹤遺失時，會終結聯合物件！ 確定任何使用聯合物件的腳本都會 `null` 正常處理案例，以避免發生錯誤！

### <a name="accessing-a-given-hand-controller"></a>存取指定的手型控制器

特定的站控制器通常可供使用，例如處理輸入事件時。 在此情況下，您可以使用介面，直接從裝置要求聯合資料 [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 。

#### <a name="polling-joint-pose-from-controller"></a>從控制器輪詢聯合姿勢

[`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) `false` 如果要求的聯合因為某些原因而無法使用，則函式會傳回。 在這種情況下，結果會是 [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) 。

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

#### <a name="joint-transform-from-hand-visualizer"></a>從手形視覺化的聯合轉換

您可以從 [控制器視覺化](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)要求聯合物件。

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

### <a name="simplified-joint-data-access"></a>簡化的聯合資料存取

如果未指定特定的控制器，則會提供公用程式類別，方便您方便存取來取得聯合資料。 這些函式會從目前追蹤的第一個可用裝置要求聯合資料。

#### <a name="polling-joint-pose-from-handjointutils"></a>從 HandJointUtils 輪詢聯合姿勢

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) 是查詢第一個現用手裝置的靜態類別。

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>來自手聯合服務的聯合轉換

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) 保留一組持續性的 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 來追蹤接點。

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>手動追蹤事件

如果您不想要直接從控制器輪詢資料，輸入系統也會提供事件。

#### <a name="joint-events"></a>聯合事件

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) 處理聯合位置的更新。

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

#### <a name="mesh-events"></a>網格事件

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) 處理已被明確表達的手網格變更。

請注意，預設並不會啟用手形網格。

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

## <a name="known-issues"></a>已知問題

### <a name="net-native"></a>.NET Native

目前使用 .NET 後端的主要組建有已知的問題。 在 .NET Native 中， `IInspectable` 無法使用將指標從原生封送處理至 managed 程式碼 `Marshal.GetObjectForIUnknown` 。 MRTK 會使用這個來取得，以便 `SpatialCoordinateSystem` 從平臺接收手和眼睛資料。

我們已在 [原生混合現實工具](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)組存放庫中，提供 DLL 來源作為此問題的因應措施。 請遵循讀我檔案中的指示，並將產生的二進位檔複製到 Unity 資產中的 [外掛程式] 資料夾。 之後，MRTK 中提供的 WindowsMixedRealityUtilities 腳本將為您解決因應措施。

如果您想要建立自己的 DLL，或在現有的 DLL 中包含此因應措施，解決方法的核心是：

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

而且在您的 c # Unity 程式碼中使用：

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
