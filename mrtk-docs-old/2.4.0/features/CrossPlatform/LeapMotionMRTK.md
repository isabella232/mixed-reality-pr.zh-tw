---
title: LeapMotionMRTK
description: 針對閏運動設定的檔
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、閏運動、
ms.openlocfilehash: 7d774cebaa46b201ea380cec9047f602f45f4b3c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780236"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="f842c-104">如何在 MRTK 中使用 Ultraleap 手動追蹤來設定 Leap 運動</span><span class="sxs-lookup"><span data-stu-id="f842c-104">How to Configure Leap Motion by Ultraleap Hand Tracking in MRTK</span></span>

<span data-ttu-id="f842c-105">需要 [Leap 移動控制器](https://www.ultraleap.com/product/leap-motion-controller/) 才能使用此資料提供者。</span><span class="sxs-lookup"><span data-stu-id="f842c-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="f842c-106">Leap 的移動資料提供者可針對 VR 進行明確的手動追蹤，而且在編輯器中快速建立原型時可能很有用。</span><span class="sxs-lookup"><span data-stu-id="f842c-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="f842c-107">您可以將資料提供者設定為使用在耳機上掛接的 Leap 運動控制器，或放在桌上的上架。</span><span class="sxs-lookup"><span data-stu-id="f842c-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../Images/CrossPlatform/LeapMotion/LeapHandsGif3.gif)

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="f842c-109">在 MRTK 中使用 Ultraleap 手動追蹤來使用 Leap 移動</span><span class="sxs-lookup"><span data-stu-id="f842c-109">Using Leap Motion by Ultraleap hand tracking in MRTK</span></span>

1. <span data-ttu-id="f842c-110">針對閏運動準備 MRTK 專案</span><span class="sxs-lookup"><span data-stu-id="f842c-110">Prepare MRTK project for Leap Motion</span></span>

    - <span data-ttu-id="f842c-111">**此步驟僅適用于「適用于 Leap 的 Unity 核心資產」版本4.4.0，以及是否從 git 存放庫複製 MRTK 來源，而不是從 Unity 套件複製。如果使用來自閏運動 Unity 模組版本4.5.0 的核心資產，則不需要執行此步驟。如果 MRTK 來源即將來自 Unity 套件，請從下一個步驟開始**</span><span class="sxs-lookup"><span data-stu-id="f842c-111">**This step only applies for the Leap Motion Unity Core Assets version 4.4.0 and if the source of MRTK is cloned from the git repo, NOT from the Unity packages. This step is not required if the Core Assets from Leap Motion Unity Modules version 4.5.0 are used. If the MRTK source is going to be from the Unity packages, start at the next step**</span></span>

    - <span data-ttu-id="f842c-112">流覽至 **混合現實工具組 > 公用程式 > Leap 移動 > 設定適用于閏運動的 CSC** 檔案。</span><span class="sxs-lookup"><span data-stu-id="f842c-112">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Configure CSC File for Leap Motion**.</span></span> <span data-ttu-id="f842c-113">更新 csc 檔案會篩選出由 Leap 動作 Unity 核心資產所產生的過時警告。</span><span class="sxs-lookup"><span data-stu-id="f842c-113">Updating the csc file filters out the obsolete warnings produced by the Leap Motion Unity Core Assets.</span></span>  <span data-ttu-id="f842c-114">MRTK 存放庫包含可將警告轉換成錯誤的 csc 檔案，這種轉換會停止「Leap 動作」 MRTK 設定程式。</span><span class="sxs-lookup"><span data-stu-id="f842c-114">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the Leap Motion MRTK configuration process.</span></span>  <span data-ttu-id="f842c-115">已淘汰的警告問題會在 [此](https://github.com/leapmotion/UnityModules/issues/1082)追蹤。</span><span class="sxs-lookup"><span data-stu-id="f842c-115">The obsolete warnings issue is tracked [here](https://github.com/leapmotion/UnityModules/issues/1082).</span></span>

    ![LeapMotionUpdateCSCFile](../Images/CrossPlatform/LeapMotion/LeapMotionConfigureCSCFile2.png)

1. <span data-ttu-id="f842c-117">從 Leap 動作 Unity 模組版本4.5.0 匯入 MRTK 和核心資產</span><span class="sxs-lookup"><span data-stu-id="f842c-117">Importing MRTK and the Core Assets from Leap Motion Unity Modules version 4.5.0</span></span>
    - <span data-ttu-id="f842c-118">將 **MixedReality** 套件匯入 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="f842c-118">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="f842c-119">安裝 [Leap 動作 SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion)</span><span class="sxs-lookup"><span data-stu-id="f842c-119">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion)</span></span>
    - <span data-ttu-id="f842c-120">[從 Leap 動作 Unity 模組版本 4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0)下載並匯入核心資產</span><span class="sxs-lookup"><span data-stu-id="f842c-120">Download and import the [Core Assets from Leap Motion Unity Modules version 4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0)</span></span>
        - <span data-ttu-id="f842c-121">「Leap 動作 Unity 核心資產」版本 [4.4.0](https://github.com/leapmotion/UnityModules/releases/tag/Release-CoreAsset-4.4.0) 和來自 Leap unity 模組版本 [4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0) 的核心資產都受到支援，但我們偏好從 leap 動作 unity 模組版本4.5.0 的核心資產。</span><span class="sxs-lookup"><span data-stu-id="f842c-121">Leap Motion Unity Core Assets version [4.4.0](https://github.com/leapmotion/UnityModules/releases/tag/Release-CoreAsset-4.4.0) and the Core Assets from Leap Motion Unity Modules version [4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0) are supported, but Core Assets from Leap Motion Unity Modules version 4.5.0 are preferred.</span></span>
        - <span data-ttu-id="f842c-122">如果使用來自 Leap Unity 模組版本4.5.0 的核心資產，請將 **核心** 封裝匯入 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="f842c-122">If using Core Assets from Leap Motion Unity Modules version 4.5.0, import the **Core** package into the Unity project.</span></span>
    > [!NOTE]
    > <span data-ttu-id="f842c-123">匯入核心資產時，會移除測試目錄，並將10個元件定義新增至專案。</span><span class="sxs-lookup"><span data-stu-id="f842c-123">On import of the Core Assets, test directories are removed and 10 assembly definitions are added to the project.</span></span> <span data-ttu-id="f842c-124">確認已關閉 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f842c-124">Make sure Visual Studio is closed.</span></span>
    - <span data-ttu-id="f842c-125">如果使用 Unity 2018.4. x</span><span class="sxs-lookup"><span data-stu-id="f842c-125">If using Unity 2018.4.x</span></span>
        - <span data-ttu-id="f842c-126">核心資產匯入之後，請流覽至 [ **資產/LeapMotion/**]，核心目錄旁邊應該會有 LeapMotion asmdef 檔案。</span><span class="sxs-lookup"><span data-stu-id="f842c-126">After the Core Assets import, navigate to **Assets/LeapMotion/**, there should be a LeapMotion.asmdef file next to the Core directory.</span></span>  <span data-ttu-id="f842c-127">如果 asmdef 檔案不存在，請移至 [ [Leap 動作] 常見錯誤](#leap-motion-has-not-integrated-with-mrtk)。</span><span class="sxs-lookup"><span data-stu-id="f842c-127">If the asmdef file is not present, go to the [Leap Motion Common Errors](#leap-motion-has-not-integrated-with-mrtk).</span></span> <span data-ttu-id="f842c-128">如果檔案存在，請移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="f842c-128">If the file is present, go to the next step.</span></span>

    - <span data-ttu-id="f842c-129">如果使用 Unity 2019.3，請移至下一個步驟</span><span class="sxs-lookup"><span data-stu-id="f842c-129">If using Unity 2019.3.x, go to the next step</span></span>

1. <span data-ttu-id="f842c-130">新增 Leap 移動資料提供者</span><span class="sxs-lookup"><span data-stu-id="f842c-130">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="f842c-131">建立新的 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="f842c-131">Create a new Unity scene</span></span>
    - <span data-ttu-id="f842c-132">流覽至 **混合現實工具** 組  >  **新增至場景並設定**，以將 MRTK 新增至場景</span><span class="sxs-lookup"><span data-stu-id="f842c-132">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="f842c-133">選取階層中的 MixedRealityToolkit 遊戲物件，然後選取 [ **複製和自訂** ] 以複製預設的混合現實設定檔。</span><span class="sxs-lookup"><span data-stu-id="f842c-133">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../Images/CrossPlatform/LeapMotion/LeapProfileClone.png)

    - <span data-ttu-id="f842c-135">選取 **輸入** 設定設定檔</span><span class="sxs-lookup"><span data-stu-id="f842c-135">Select the **Input** Configuration Profile</span></span>

    ![InputConfigurationProfile](../Images/CrossPlatform/LeapMotion/LeapInputConfigurationProfile.png)

    - <span data-ttu-id="f842c-137">在輸入系統設定檔中選取 [ **複製** ]，以啟用修改。</span><span class="sxs-lookup"><span data-stu-id="f842c-137">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../Images/CrossPlatform/LeapMotion/LeapCloneInputSystemProfile.png)

    - <span data-ttu-id="f842c-139">開啟 [ **輸入資料提供者** ] 區段，選取頂端的 [ **加入資料提供** 者]，就會在清單結尾加入新的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="f842c-139">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="f842c-140">開啟新的資料提供者，並將類型設為 MixedReality，並將 **類型** 設定為 **LeapMotion，> LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="f842c-140">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![LeapAddDataProvider](../Images/CrossPlatform/LeapMotion/LeapAddDataProvider.png)

    - <span data-ttu-id="f842c-142">選取 [ **複製** ] 以變更預設的 [Leap 移動] 設定。</span><span class="sxs-lookup"><span data-stu-id="f842c-142">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../Images/CrossPlatform/LeapMotion/LeapDeviceManagerProfileBeforeClone.png)

    - <span data-ttu-id="f842c-144">「Leap 移動」資料提供者包含屬性，也 `LeapControllerOrientation` 就是「Leap 移動控制器」的位置。</span><span class="sxs-lookup"><span data-stu-id="f842c-144">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="f842c-145">`LeapControllerOrientation.Headset` 指出控制器已掛接在耳機上。</span><span class="sxs-lookup"><span data-stu-id="f842c-145">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="f842c-146">`LeapControllerOrientation.Desk` 指出控制器是在桌上平放置。</span><span class="sxs-lookup"><span data-stu-id="f842c-146">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="f842c-147">預設值會設定為 `LeapControllerOrientation.Headset` 。</span><span class="sxs-lookup"><span data-stu-id="f842c-147">The default value is set to `LeapControllerOrientation.Headset`.</span></span>  <span data-ttu-id="f842c-148">如果方向是桌，則會出現額外的屬性 `LeapControllerOffset` 。</span><span class="sxs-lookup"><span data-stu-id="f842c-148">If the orientation is the desk, an extra property `LeapControllerOffset` will appear.</span></span>  <span data-ttu-id="f842c-149">`LeapControllerOffset` 是桌上位置的錨點。</span><span class="sxs-lookup"><span data-stu-id="f842c-149">`LeapControllerOffset` is the anchor for the position of the desk leap hands.</span></span>  <span data-ttu-id="f842c-150">位移的計算方式相對於主要攝影機位置，而預設值是 (0，-0.2，0.2) ，以確保手出現在相機的前方和視野中。</span><span class="sxs-lookup"><span data-stu-id="f842c-150">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.2) to make sure the hands appear in front and in view of the camera.</span></span>
    - <span data-ttu-id="f842c-151">`EnterPinchDistance` 而且 `ExitPinchDistance` 是縮小/飛行軌跡偵測的距離臨界值。</span><span class="sxs-lookup"><span data-stu-id="f842c-151">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="f842c-152">縮小手勢的計算方式是測量食指與 thumb 提示之間的距離。</span><span class="sxs-lookup"><span data-stu-id="f842c-152">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="f842c-153">若要在輸入關閉事件時引發，預設值 `EnterPinchDistance` 會設定為0.02。</span><span class="sxs-lookup"><span data-stu-id="f842c-153">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="f842c-154">若要在輸入時引發事件 (結束縮小) ，則索引手指提示與 thumb 提示之間的預設距離為0.05。</span><span class="sxs-lookup"><span data-stu-id="f842c-154">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="f842c-155">`LeapControllerOrientation`：耳機 (預設) </span><span class="sxs-lookup"><span data-stu-id="f842c-155">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="f842c-156">`LeapControllerOrientation`：辦公桌</span><span class="sxs-lookup"><span data-stu-id="f842c-156">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../Images/CrossPlatform/LeapMotion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../Images/CrossPlatform/LeapMotion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../Images/CrossPlatform/LeapMotion/LeapDeviceManagerHeadset.png) |     ![LeapDeskInspector](../Images/CrossPlatform/LeapMotion/LeapDeviceManagerDesk.png)

1. <span data-ttu-id="f842c-161">測試閏運動資料提供者</span><span class="sxs-lookup"><span data-stu-id="f842c-161">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="f842c-162">將 Leap 的移動資料提供者加入至輸入系統設定檔之後，請按下 [播放]，將您的手移至 [Leap] 移動控制器前面，您應該會看到該手的接點表示。</span><span class="sxs-lookup"><span data-stu-id="f842c-162">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="f842c-163">建立您的專案</span><span class="sxs-lookup"><span data-stu-id="f842c-163">Building your project</span></span>
    - <span data-ttu-id="f842c-164">流覽至檔案 **> 組建設定**</span><span class="sxs-lookup"><span data-stu-id="f842c-164">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="f842c-165">只有在使用 Leap 移動資料提供者時，才支援獨立組建。</span><span class="sxs-lookup"><span data-stu-id="f842c-165">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="f842c-166">如需有關如何使用適用于獨立組建的 Windows Mixed Reality 耳機的指示，請參閱 [組建和部署](../../updates-deployment/BuildAndDeploy.md#building-and-deploying-mrtk-to-a-windows-mixed-reality-headset)。</span><span class="sxs-lookup"><span data-stu-id="f842c-166">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Build and Deploy](../../updates-deployment/BuildAndDeploy.md#building-and-deploying-mrtk-to-a-windows-mixed-reality-headset).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="f842c-167">取得手接點</span><span class="sxs-lookup"><span data-stu-id="f842c-167">Getting the hand joints</span></span>

<span data-ttu-id="f842c-168">使用「Leap 運動」資料提供者的取得接點，與 MRTK 明確的手上的手入聯結相同。</span><span class="sxs-lookup"><span data-stu-id="f842c-168">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="f842c-169">如需詳細資訊，請參閱 [手動追蹤](../Input/HandTracking.md#polling-joint-pose-from-handjointutils)。</span><span class="sxs-lookup"><span data-stu-id="f842c-169">For more information, see [Hand Tracking](../Input/HandTracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="f842c-170">在 unity 場景中使用 MRTK，並在輸入系統設定檔中新增做為輸入資料提供者的 Leap 移動資料提供者時，請建立空白的遊戲物件，並附加下列範例腳本。</span><span class="sxs-lookup"><span data-stu-id="f842c-170">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="f842c-171">此腳本是一個簡單的範例，示範如何在閏運動手中取出棕櫚接合的姿勢。</span><span class="sxs-lookup"><span data-stu-id="f842c-171">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="f842c-172">當 cube 遵循正確的 Leap 時，球體會跟隨左方的閏年。</span><span class="sxs-lookup"><span data-stu-id="f842c-172">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="f842c-173">Unity 編輯器工作流程秘訣</span><span class="sxs-lookup"><span data-stu-id="f842c-173">Unity editor workflow tip</span></span>

<span data-ttu-id="f842c-174">使用「Leap 移動」資料提供者不需要 VR 耳機。</span><span class="sxs-lookup"><span data-stu-id="f842c-174">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="f842c-175">MRTK 應用程式的變更可在編輯器中，使用不帶耳機的飛躍進行測試。</span><span class="sxs-lookup"><span data-stu-id="f842c-175">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="f842c-176">如果未插入 VR 耳機，則會在編輯器中顯示 Leap 運動手。</span><span class="sxs-lookup"><span data-stu-id="f842c-176">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="f842c-177">如果設定為「耳機」，則必須將「 `LeapControllerOrientation` Leap」移動控制器的一端與相機朝前的一端保持在一起。 </span><span class="sxs-lookup"><span data-stu-id="f842c-177">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="f842c-178">如果相機是在編輯器中使用 WASD 按鍵移動，且 `LeapControllerOrientation` 是 **耳機**，則手不會跟隨相機。</span><span class="sxs-lookup"><span data-stu-id="f842c-178">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="f842c-179">如果在設定耳機的情況下插入 VR 耳機，則只會在相機移動之後進行 `LeapControllerOrientation` 。 </span><span class="sxs-lookup"><span data-stu-id="f842c-179">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="f842c-180">如果設定為 [桌上]，則會在編輯器中追蹤相機移動 `LeapControllerOrientation` 。 </span><span class="sxs-lookup"><span data-stu-id="f842c-180">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="f842c-181">從專案移除 Leap 動作</span><span class="sxs-lookup"><span data-stu-id="f842c-181">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="f842c-182">關閉 Unity</span><span class="sxs-lookup"><span data-stu-id="f842c-182">Close Unity</span></span>
1. <span data-ttu-id="f842c-183">關閉 Visual Studio （如果已開啟）</span><span class="sxs-lookup"><span data-stu-id="f842c-183">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="f842c-184">開啟檔案瀏覽器，並流覽至 MRTK Unity 專案的根目錄</span><span class="sxs-lookup"><span data-stu-id="f842c-184">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="f842c-185">刪除 **UnityProjectName/Library** 目錄</span><span class="sxs-lookup"><span data-stu-id="f842c-185">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="f842c-186">刪除 **UnityProjectName/資產/LeapMotion** 目錄</span><span class="sxs-lookup"><span data-stu-id="f842c-186">Delete the **UnityProjectName/Assets/LeapMotion** directory</span></span>
    - <span data-ttu-id="f842c-187">刪除 **UnityProjectName/資產/LeapMotion 元** 檔案</span><span class="sxs-lookup"><span data-stu-id="f842c-187">Delete the **UnityProjectName/Assets/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="f842c-188">重新開啟 Unity</span><span class="sxs-lookup"><span data-stu-id="f842c-188">Reopen Unity</span></span>

<span data-ttu-id="f842c-189">在 Unity 2018.4 中，您可能會注意到在刪除程式庫和閏運動核心資產之後，仍會在主控台中保留錯誤。</span><span class="sxs-lookup"><span data-stu-id="f842c-189">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="f842c-190">如果在重新開啟之後記錄錯誤，請重新開機 Unity。</span><span class="sxs-lookup"><span data-stu-id="f842c-190">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="f842c-191">一般錯誤</span><span class="sxs-lookup"><span data-stu-id="f842c-191">Common Errors</span></span>

### <a name="leap-motion-obsolete-errors"></a><span data-ttu-id="f842c-192">Leap 移動過時錯誤</span><span class="sxs-lookup"><span data-stu-id="f842c-192">Leap Motion Obsolete Errors</span></span>

<span data-ttu-id="f842c-193">如果 MRTK 來源是來自存放庫，而 Unity 版本是2019.3，則在匯入 Leap 動作 Unity 核心資產之後，主控台中可能會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="f842c-193">If the source of MRTK is from the repo and the Unity version is 2019.3.x, the following error might be in the console after the import of the Leap Motion Unity Core Assets:</span></span>

```
Assets\LeapMotion\Core\Scripts\EditorTools\LeapPreferences.cs(84,6): error CS0618: 'PreferenceItem' is obsolete: '[PreferenceItem] is deprecated. Use [SettingsProvider] instead.
```

<span data-ttu-id="f842c-194">在 Unity 版本2018.4 中，可能會記錄下列已淘汰的錯誤：</span><span class="sxs-lookup"><span data-stu-id="f842c-194">In Unity version 2018.4.x, the following obsolete errors might be logged:</span></span>

```
Assets\LeapMotion\Core\Scripts\Attachments\AttachmentHands.cs(105,7): error CS0618: 'PrefabType' is obsolete: 'PrefabType no longer tells everything about Prefab instance.'
```

```
Assets\LeapMotion\Core\Scripts\Attachments\AttachmentHands.cs(105,31): error CS0618: 'PrefabUtility.GetPrefabType(Object)' is obsolete: 'Use GetPrefabAssetType and GetPrefabInstanceStatus to get the full picture about Prefab types.'
```

<span data-ttu-id="f842c-195">如果 **混合現實工具組 > 公用程式 > 閏動作 > 設定 CSC 檔案以進行 Leap 動作** ，而不是在 [Leap 動作 Unity 核心資產匯入] 之前選取，就會出現這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="f842c-195">These errors appear if **Mixed Reality Toolkit > Utilities > Leap Motion > Configure CSC File for Leap Motion** was not selected BEFORE the Leap Motion Unity Core Assets import.</span></span>

#### <a name="solution"></a><span data-ttu-id="f842c-196">解決方法</span><span class="sxs-lookup"><span data-stu-id="f842c-196">Solution</span></span>

- <span data-ttu-id="f842c-197">流覽至 **混合現實工具組 > 公用程式 > Leap 移動 > 設定適用于閏運動的 csc** 檔案，這將會更新 csc 檔案，以篩選出轉換成 MRTK 存放庫中錯誤的 Leap 動作警告。</span><span class="sxs-lookup"><span data-stu-id="f842c-197">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Configure CSC File for Leap Motion**, this will update the csc file to filter out Leap Motion warnings that are converted to errors in MRTK repo.</span></span>
- <span data-ttu-id="f842c-198">關閉 Unity</span><span class="sxs-lookup"><span data-stu-id="f842c-198">Close Unity</span></span>
- <span data-ttu-id="f842c-199">重新開啟 Unity</span><span class="sxs-lookup"><span data-stu-id="f842c-199">Reopen Unity</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="f842c-200">Leap 動作尚未與 MRTK 整合</span><span class="sxs-lookup"><span data-stu-id="f842c-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="f842c-201">如果 Unity 版本是2018.4，則會發生此錯誤。 MRTK 來源來自 Unity 套件，以及在匯入閏動作 Unity 核心資產之後。</span><span class="sxs-lookup"><span data-stu-id="f842c-201">This error can occur if the Unity version is 2018.4.x, the MRTK source is from the Unity packages and after the import of the Leap Motion Unity Core Assets.</span></span>

<span data-ttu-id="f842c-202">若要測試 MRTK 是否可辨識是否有「Leap」 Unity 核心資產，請開啟位於 MRTK/範例/示範/HandTracking/中的 LeapMotionHandTrackingExample 場景，然後按下 [播放]。</span><span class="sxs-lookup"><span data-stu-id="f842c-202">To test if MRTK recognizes the presence of the Leap Motion Unity Core Assets, open the LeapMotionHandTrackingExample scene located in MRTK/Examples/Demos/HandTracking/ and press play.</span></span>  <span data-ttu-id="f842c-203">如果 [Leap 動作] Unity 核心資產被辨識，場景中的資訊面板上會出現綠色訊息。</span><span class="sxs-lookup"><span data-stu-id="f842c-203">If the Leap Motion Unity Core Assets are recognized a green message on the informational panel in the scene will appear.</span></span>  <span data-ttu-id="f842c-204">如果無法辨識閏動作 Unity 核心資產，則會出現紅色的訊息。</span><span class="sxs-lookup"><span data-stu-id="f842c-204">If the Leap Motion Unity Core Assets are not recognized a red message will appear.</span></span>

<span data-ttu-id="f842c-205">如果您的專案中有 Leap 動作 Unity 核心資產，而您在資訊面板上看到紅色的訊息，則必須設定專案。</span><span class="sxs-lookup"><span data-stu-id="f842c-205">If the Leap Motion Unity Core Assets are in your project and you see a red message on the informational panel, the project needs to be configured.</span></span>

#### <a name="solution"></a><span data-ttu-id="f842c-206">解決方法</span><span class="sxs-lookup"><span data-stu-id="f842c-206">Solution</span></span>

- <span data-ttu-id="f842c-207">流覽至 **混合現實工具組 > 公用程式 > Leap 移動 > 設定 Leap 移動**</span><span class="sxs-lookup"><span data-stu-id="f842c-207">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Configure Leap Motion**</span></span>
  - <span data-ttu-id="f842c-208">如果設定程式未在執行 Unity 動作 Unity 核心資產匯入之後啟動，這將會強制執行「執行」動作整合。</span><span class="sxs-lookup"><span data-stu-id="f842c-208">This will force Leap Motion integration if the configuration process was not started after the Leap Motion Unity Core Assets import.</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="f842c-209">複製元件多人 HLAPI 失敗</span><span class="sxs-lookup"><span data-stu-id="f842c-209">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="f842c-210">匯入閏動作 Unity 核心資產時，可能會記錄此錯誤：</span><span class="sxs-lookup"><span data-stu-id="f842c-210">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

#### <a name="solution"></a><span data-ttu-id="f842c-211">解決方法</span><span class="sxs-lookup"><span data-stu-id="f842c-211">Solution</span></span>

- <span data-ttu-id="f842c-212">短期解決方案是重新開機 Unity。</span><span class="sxs-lookup"><span data-stu-id="f842c-212">A short term solution is to restart Unity.</span></span> <span data-ttu-id="f842c-213">如需詳細資訊，請參閱 [問題 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 。</span><span class="sxs-lookup"><span data-stu-id="f842c-213">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="f842c-214">Leap 運動範例場景</span><span class="sxs-lookup"><span data-stu-id="f842c-214">Leap Motion Example Scene</span></span>

<span data-ttu-id="f842c-215">範例場景會使用 DefaultLeapMotionConfiguration 設定檔，並判斷 Unity 專案是否已正確設定為使用閏運動資料提供者。</span><span class="sxs-lookup"><span data-stu-id="f842c-215">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="f842c-216">範例場景包含在 **MRTK/範例/示範/HandTracking/** 目錄中的 **MixedReality 範例** 套件中。</span><span class="sxs-lookup"><span data-stu-id="f842c-216">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="f842c-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f842c-217">See also</span></span>

- [<span data-ttu-id="f842c-218">輸入提供者</span><span class="sxs-lookup"><span data-stu-id="f842c-218">Input Providers</span></span>](../Input/InputProviders.md)
- [<span data-ttu-id="f842c-219">手動追蹤</span><span class="sxs-lookup"><span data-stu-id="f842c-219">Hand Tracking</span></span>](../Input/HandTracking.md)
