---
title: Leap 運動 MRTK
description: 針對閏運動設定的檔
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、閏運動、
ms.openlocfilehash: 44593713f08a00fa53325eebfae2cf9042d386be
ms.sourcegitcommit: 62beb626b2db6ce7df86014bd22bf1946b8906b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2021
ms.locfileid: "110207470"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="b019c-104">如何在 MRTK 中使用 Ultraleap) 手勢來設定 Leap 運動 (</span><span class="sxs-lookup"><span data-stu-id="b019c-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="b019c-105">需要 [Leap 移動控制器](https://www.ultraleap.com/product/leap-motion-controller/) 才能使用此資料提供者。</span><span class="sxs-lookup"><span data-stu-id="b019c-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="b019c-106">閏運動 Data Provider 可針對 VR 進行明確的手動追蹤，而且在編輯器中快速建立原型時可能很有用。</span><span class="sxs-lookup"><span data-stu-id="b019c-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="b019c-107">您可以將資料提供者設定為使用在耳機上掛接的 Leap 運動控制器，或放在桌上的上架。</span><span class="sxs-lookup"><span data-stu-id="b019c-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="b019c-109">此提供者可在獨立平臺上的編輯器和裝置上使用。</span><span class="sxs-lookup"><span data-stu-id="b019c-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="b019c-110">它也可以在 UWP 平臺上的編輯器中使用，但不能在 UWP 組建中使用。</span><span class="sxs-lookup"><span data-stu-id="b019c-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="b019c-111">MRTK 版本</span><span class="sxs-lookup"><span data-stu-id="b019c-111">MRTK Version</span></span> | <span data-ttu-id="b019c-112">支援的 Leap 動作 Unity 模組版本</span><span class="sxs-lookup"><span data-stu-id="b019c-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="b019c-113">2.6. x</span><span class="sxs-lookup"><span data-stu-id="b019c-113">2.6.x</span></span> | <span data-ttu-id="b019c-114">4.5.0，4.5。1</span><span class="sxs-lookup"><span data-stu-id="b019c-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="b019c-115">2.7. x</span><span class="sxs-lookup"><span data-stu-id="b019c-115">2.7.x</span></span>| <span data-ttu-id="b019c-116">4.5.0、4.5.1、4.6.0、4.7.0、4.7。1</span><span class="sxs-lookup"><span data-stu-id="b019c-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="b019c-117">在 MRTK 中使用 Ultraleap) 手動追蹤 (的 Leap 動作</span><span class="sxs-lookup"><span data-stu-id="b019c-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="b019c-118">匯入 MRTK 和 Leap 動作 Unity 模組</span><span class="sxs-lookup"><span data-stu-id="b019c-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="b019c-119">安裝最新的 [Leap 動作 SDK](https://developer.leapmotion.com/releases/?category=orion) （如果尚未安裝）</span><span class="sxs-lookup"><span data-stu-id="b019c-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="b019c-120">將 **MixedReality** 套件匯入 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="b019c-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="b019c-121">下載最新版本的 [Leap 動作 Unity 模組](https://developer.leapmotion.com/unity) 並匯入到專案中</span><span class="sxs-lookup"><span data-stu-id="b019c-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="b019c-122">僅在 Unity 模組內匯入 **核心** 套件</span><span class="sxs-lookup"><span data-stu-id="b019c-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="b019c-123">整合 Leap 動作 Unity 模組與 MRTK</span><span class="sxs-lookup"><span data-stu-id="b019c-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="b019c-124">在專案中有 Unity 模組之後，請流覽至 **混合現實工具** 組的  >  **leap 動作**  >  **整合閏動作 Unity 模組**</span><span class="sxs-lookup"><span data-stu-id="b019c-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="b019c-125">將 Unity 模組整合至 MRTK 會將10個元件定義新增至專案，並加入 **MixedReality** 的參考。 LeapMotion 元件定義。</span><span class="sxs-lookup"><span data-stu-id="b019c-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="b019c-126">確認已關閉 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b019c-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="b019c-128">新增閏運動 Data Provider</span><span class="sxs-lookup"><span data-stu-id="b019c-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="b019c-129">建立新的 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="b019c-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="b019c-130">流覽至 **混合現實工具** 組  >  **新增至場景並設定**，以將 MRTK 新增至場景</span><span class="sxs-lookup"><span data-stu-id="b019c-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="b019c-131">選取階層中的 MixedRealityToolkit 遊戲物件，然後選取 [ **複製和自訂** ] 以複製預設的混合現實設定檔。</span><span class="sxs-lookup"><span data-stu-id="b019c-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="b019c-133">選取 **輸入** 設定設定檔</span><span class="sxs-lookup"><span data-stu-id="b019c-133">Select the **Input** Configuration Profile</span></span>

    ![輸入設定設定檔1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="b019c-135">在輸入系統設定檔中選取 [ **複製** ]，以啟用修改。</span><span class="sxs-lookup"><span data-stu-id="b019c-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="b019c-137">開啟 [ **輸入資料提供者** ] 區段，選取頂端的 [ **加入 Data Provider** ，將會在清單結尾加入新的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="b019c-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="b019c-138">開啟新的資料提供者，並將類型設為 MixedReality，並將 **類型** 設定為 **LeapMotion，> LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="b019c-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap 新增 Data Provider](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="b019c-140">選取 [ **複製** ] 以變更預設的 [Leap 移動] 設定。</span><span class="sxs-lookup"><span data-stu-id="b019c-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="b019c-142">閏運動 Data Provider 包含屬性，也 `LeapControllerOrientation` 就是 Leap 移動控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="b019c-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="b019c-143">`LeapControllerOrientation.Headset` 指出控制器已掛接在耳機上。</span><span class="sxs-lookup"><span data-stu-id="b019c-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="b019c-144">`LeapControllerOrientation.Desk` 指出控制器是在桌上平放置。</span><span class="sxs-lookup"><span data-stu-id="b019c-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="b019c-145">預設值會設定為 `LeapControllerOrientation.Headset` 。</span><span class="sxs-lookup"><span data-stu-id="b019c-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="b019c-146">每個控制器方向都包含 offset 屬性：</span><span class="sxs-lookup"><span data-stu-id="b019c-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="b019c-147">**耳機** 方向位移屬性會鏡像 LeapXRServiceProvider 元件中的位移屬性。</span><span class="sxs-lookup"><span data-stu-id="b019c-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="b019c-148">`LeapVRDeviceOffsetMode`有三個選項：預設值、手動標頭位移和轉換。</span><span class="sxs-lookup"><span data-stu-id="b019c-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="b019c-149">如果位移模式是預設值，則不會將位移套用至 Leap 移動控制器。</span><span class="sxs-lookup"><span data-stu-id="b019c-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="b019c-150">手動標頭位移模式允許修改三個屬性： `LeapVRDeviceOffsetY` 、 `LeapVRDeviceOffsetZ` 和 `LeapVRDeviceTiltX` 。</span><span class="sxs-lookup"><span data-stu-id="b019c-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="b019c-151">然後，軸位移屬性值會套用至預設控制器放置。</span><span class="sxs-lookup"><span data-stu-id="b019c-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="b019c-152">[轉換位移] 模式包含 [轉換] 屬性，以 `LeapVRDeviceOrigin` 指定 Leap 移動控制器的新來源。</span><span class="sxs-lookup"><span data-stu-id="b019c-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="b019c-153">[ **桌** 上方向] 包含 `LeapControllerOffset` 屬性，可定義桌上的錨點位置。</span><span class="sxs-lookup"><span data-stu-id="b019c-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="b019c-154">位移的計算方式相對於主要攝影機位置，而預設值是 (0，-0.2，0.35) ，以確保手出現在相機的前方和視野中。</span><span class="sxs-lookup"><span data-stu-id="b019c-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="b019c-155">當應用程式啟動時，設定檔中的位移屬性會套用一次。</span><span class="sxs-lookup"><span data-stu-id="b019c-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="b019c-156">若要在執行時間期間修改值，請從 Leap 移動裝置管理員取得閏運動服務提供者：</span><span class="sxs-lookup"><span data-stu-id="b019c-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="b019c-157">`EnterPinchDistance` 而且 `ExitPinchDistance` 是縮小/飛行軌跡偵測的距離臨界值。</span><span class="sxs-lookup"><span data-stu-id="b019c-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="b019c-158">縮小手勢的計算方式是測量食指與 thumb 提示之間的距離。</span><span class="sxs-lookup"><span data-stu-id="b019c-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="b019c-159">若要在輸入關閉事件時引發，預設值 `EnterPinchDistance` 會設定為0.02。</span><span class="sxs-lookup"><span data-stu-id="b019c-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="b019c-160">若要在輸入時引發事件 (結束縮小) ，則索引手指提示與 thumb 提示之間的預設距離為0.05。</span><span class="sxs-lookup"><span data-stu-id="b019c-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="b019c-161">`LeapControllerOrientation`：耳機 (預設) </span><span class="sxs-lookup"><span data-stu-id="b019c-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="b019c-162">`LeapControllerOrientation`：辦公桌</span><span class="sxs-lookup"><span data-stu-id="b019c-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="b019c-167">測試閏運動 Data Provider</span><span class="sxs-lookup"><span data-stu-id="b019c-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="b019c-168">將 Data Provider 新增至輸入系統設定檔之後，請按下 [播放]，將您的手移至 [Leap] 運動控制器前面，您應該會看到該手的接點表示。</span><span class="sxs-lookup"><span data-stu-id="b019c-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="b019c-169">建立您的專案</span><span class="sxs-lookup"><span data-stu-id="b019c-169">Building your project</span></span>
    - <span data-ttu-id="b019c-170">流覽至檔案 **> 組建設定**</span><span class="sxs-lookup"><span data-stu-id="b019c-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="b019c-171">如果使用 Data Provider 的 Leap 動作，只支援獨立組建。</span><span class="sxs-lookup"><span data-stu-id="b019c-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="b019c-172">如需有關如何使用獨立組建 Windows Mixed Reality 耳機的指示，請參閱 [建立和部署 MRTK (獨立) ](wmr-mrtk.md#building-and-deploying-mrtk-standalone)。</span><span class="sxs-lookup"><span data-stu-id="b019c-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="b019c-173">取得手接點</span><span class="sxs-lookup"><span data-stu-id="b019c-173">Getting the hand joints</span></span>

<span data-ttu-id="b019c-174">使用閏運動 Data Provider 取得接點等同于 MRTK 清楚的手上的聯合抓取。</span><span class="sxs-lookup"><span data-stu-id="b019c-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="b019c-175">如需詳細資訊，請參閱 [手動追蹤](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)。</span><span class="sxs-lookup"><span data-stu-id="b019c-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="b019c-176">在 unity 場景中使用 MRTK，Data Provider 並在輸入系統設定檔中將新增為輸入 Data Provider，請建立空白的遊戲物件，並附加下列範例腳本。</span><span class="sxs-lookup"><span data-stu-id="b019c-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="b019c-177">此腳本是一個簡單的範例，示範如何在閏運動手中取出棕櫚接合的姿勢。</span><span class="sxs-lookup"><span data-stu-id="b019c-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="b019c-178">當 cube 遵循正確的 Leap 時，球體會跟隨左方的閏年。</span><span class="sxs-lookup"><span data-stu-id="b019c-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="b019c-179">Unity 編輯器工作流程秘訣</span><span class="sxs-lookup"><span data-stu-id="b019c-179">Unity editor workflow tip</span></span>

<span data-ttu-id="b019c-180">使用閏運動 Data Provider 不需要使用 VR 耳機。</span><span class="sxs-lookup"><span data-stu-id="b019c-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="b019c-181">MRTK 應用程式的變更可在編輯器中，使用不帶耳機的飛躍進行測試。</span><span class="sxs-lookup"><span data-stu-id="b019c-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="b019c-182">如果未插入 VR 耳機，則會在編輯器中顯示 Leap 運動手。</span><span class="sxs-lookup"><span data-stu-id="b019c-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="b019c-183">如果設定為「耳機」，則必須將「 `LeapControllerOrientation` Leap」移動控制器的一端與相機朝前的一端保持在一起。 </span><span class="sxs-lookup"><span data-stu-id="b019c-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="b019c-184">如果相機是在編輯器中使用 WASD 按鍵移動，且 `LeapControllerOrientation` 是 **耳機**，則手不會跟隨相機。</span><span class="sxs-lookup"><span data-stu-id="b019c-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="b019c-185">如果在設定耳機的情況下插入 VR 耳機，則只會在相機移動之後進行 `LeapControllerOrientation` 。 </span><span class="sxs-lookup"><span data-stu-id="b019c-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="b019c-186">如果設定為 [桌上]，則會在編輯器中追蹤相機移動 `LeapControllerOrientation` 。 </span><span class="sxs-lookup"><span data-stu-id="b019c-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="b019c-187">從專案移除 Leap 動作</span><span class="sxs-lookup"><span data-stu-id="b019c-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="b019c-188">流覽至 **混合現實工具** 組的  >  **閏動作**  >  **個別的 leap 動作 Unity 模組**</span><span class="sxs-lookup"><span data-stu-id="b019c-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="b019c-189">讓 Unity 重新整理為 MixedReality 中的參考，在此步驟中修改 **LeapMotion asmdef** 檔案</span><span class="sxs-lookup"><span data-stu-id="b019c-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="b019c-190">關閉 Unity</span><span class="sxs-lookup"><span data-stu-id="b019c-190">Close Unity</span></span>
1. <span data-ttu-id="b019c-191">關閉 Visual Studio （如果已開啟）</span><span class="sxs-lookup"><span data-stu-id="b019c-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="b019c-192">開啟檔案總管並流覽至 MRTK Unity 專案的根目錄</span><span class="sxs-lookup"><span data-stu-id="b019c-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="b019c-193">刪除 **UnityProjectName/Library** 目錄</span><span class="sxs-lookup"><span data-stu-id="b019c-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="b019c-194">刪除 **UnityProjectName/資產/外掛程式/LeapMotion** 目錄</span><span class="sxs-lookup"><span data-stu-id="b019c-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="b019c-195">刪除 **UnityProjectName/資產/外掛程式/LeapMotion 元** 檔案</span><span class="sxs-lookup"><span data-stu-id="b019c-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="b019c-196">重新開啟 Unity</span><span class="sxs-lookup"><span data-stu-id="b019c-196">Reopen Unity</span></span>

<span data-ttu-id="b019c-197">在 Unity 2018.4 中，您可能會注意到在刪除程式庫和閏運動核心資產之後，仍會在主控台中保留錯誤。</span><span class="sxs-lookup"><span data-stu-id="b019c-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="b019c-198">如果在重新開啟之後記錄錯誤，請重新開機 Unity。</span><span class="sxs-lookup"><span data-stu-id="b019c-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="b019c-199">一般錯誤</span><span class="sxs-lookup"><span data-stu-id="b019c-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="b019c-200">Leap 動作尚未與 MRTK 整合</span><span class="sxs-lookup"><span data-stu-id="b019c-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="b019c-201">若要測試閏運動 Unity 模組是否已與 MRTK 整合：</span><span class="sxs-lookup"><span data-stu-id="b019c-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="b019c-202">流覽至 **混合現實工具組 > 公用程式 > Leap 移動 > 檢查整合狀態**</span><span class="sxs-lookup"><span data-stu-id="b019c-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="b019c-203">這將會顯示一個快顯視窗，其中顯示有關 Leap 的 Unity 模組是否已與 MRTK 整合的訊息。</span><span class="sxs-lookup"><span data-stu-id="b019c-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="b019c-204">如果訊息指出資產尚未整合：</span><span class="sxs-lookup"><span data-stu-id="b019c-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="b019c-205">請確定在專案中有「Leap」動作 Unity 模組</span><span class="sxs-lookup"><span data-stu-id="b019c-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="b019c-206">請確定已支援新增的版本，請參閱頁面頂端的表格，以取得支援的版本。</span><span class="sxs-lookup"><span data-stu-id="b019c-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="b019c-207">嘗試 **混合現實工具組 > 公用程式 > > 整合 Leap 動作 Unity 模組**</span><span class="sxs-lookup"><span data-stu-id="b019c-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="b019c-208">複製元件多人 HLAPI 失敗</span><span class="sxs-lookup"><span data-stu-id="b019c-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="b019c-209">匯入閏動作 Unity 核心資產時，可能會記錄此錯誤：</span><span class="sxs-lookup"><span data-stu-id="b019c-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="b019c-210">**方案**</span><span class="sxs-lookup"><span data-stu-id="b019c-210">**Solution**</span></span>

- <span data-ttu-id="b019c-211">短期解決方案是重新開機 Unity。</span><span class="sxs-lookup"><span data-stu-id="b019c-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="b019c-212">如需詳細資訊，請參閱 [問題 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 。</span><span class="sxs-lookup"><span data-stu-id="b019c-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="b019c-213">Leap 運動範例場景</span><span class="sxs-lookup"><span data-stu-id="b019c-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="b019c-214">範例場景會使用 DefaultLeapMotionConfiguration 設定檔，並判斷 Unity 專案是否已正確設定為使用 Data Provider 的 Leap 動作。</span><span class="sxs-lookup"><span data-stu-id="b019c-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="b019c-215">範例場景包含在 **MRTK/範例/示範/HandTracking/** 目錄中的 **MixedReality 範例** 套件中。</span><span class="sxs-lookup"><span data-stu-id="b019c-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="b019c-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b019c-216">See also</span></span>

- [<span data-ttu-id="b019c-217">輸入提供者</span><span class="sxs-lookup"><span data-stu-id="b019c-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="b019c-218">手動追蹤</span><span class="sxs-lookup"><span data-stu-id="b019c-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
