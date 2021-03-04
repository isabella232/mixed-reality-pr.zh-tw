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
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>如何在 MRTK 中使用 Ultraleap 手動追蹤來設定 Leap 運動

需要 [Leap 移動控制器](https://www.ultraleap.com/product/leap-motion-controller/) 才能使用此資料提供者。

Leap 的移動資料提供者可針對 VR 進行明確的手動追蹤，而且在編輯器中快速建立原型時可能很有用。  您可以將資料提供者設定為使用在耳機上掛接的 Leap 運動控制器，或放在桌上的上架。

![LeapMotionIntroGif](../Images/CrossPlatform/LeapMotion/LeapHandsGif3.gif)

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>在 MRTK 中使用 Ultraleap 手動追蹤來使用 Leap 移動

1. 針對閏運動準備 MRTK 專案

    - **此步驟僅適用于「適用于 Leap 的 Unity 核心資產」版本4.4.0，以及是否從 git 存放庫複製 MRTK 來源，而不是從 Unity 套件複製。如果使用來自閏運動 Unity 模組版本4.5.0 的核心資產，則不需要執行此步驟。如果 MRTK 來源即將來自 Unity 套件，請從下一個步驟開始**

    - 流覽至 **混合現實工具組 > 公用程式 > Leap 移動 > 設定適用于閏運動的 CSC** 檔案。 更新 csc 檔案會篩選出由 Leap 動作 Unity 核心資產所產生的過時警告。  MRTK 存放庫包含可將警告轉換成錯誤的 csc 檔案，這種轉換會停止「Leap 動作」 MRTK 設定程式。  已淘汰的警告問題會在 [此](https://github.com/leapmotion/UnityModules/issues/1082)追蹤。

    ![LeapMotionUpdateCSCFile](../Images/CrossPlatform/LeapMotion/LeapMotionConfigureCSCFile2.png)

1. 從 Leap 動作 Unity 模組版本4.5.0 匯入 MRTK 和核心資產
    - 將 **MixedReality** 套件匯入 Unity 專案。
    - 安裝 [Leap 動作 SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion)
    - [從 Leap 動作 Unity 模組版本 4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0)下載並匯入核心資產
        - 「Leap 動作 Unity 核心資產」版本 [4.4.0](https://github.com/leapmotion/UnityModules/releases/tag/Release-CoreAsset-4.4.0) 和來自 Leap unity 模組版本 [4.5.0](https://github.com/leapmotion/UnityModules/releases/tag/UM-4.5.0) 的核心資產都受到支援，但我們偏好從 leap 動作 unity 模組版本4.5.0 的核心資產。
        - 如果使用來自 Leap Unity 模組版本4.5.0 的核心資產，請將 **核心** 封裝匯入 Unity 專案。
    > [!NOTE]
    > 匯入核心資產時，會移除測試目錄，並將10個元件定義新增至專案。 確認已關閉 Visual Studio。
    - 如果使用 Unity 2018.4. x
        - 核心資產匯入之後，請流覽至 [ **資產/LeapMotion/**]，核心目錄旁邊應該會有 LeapMotion asmdef 檔案。  如果 asmdef 檔案不存在，請移至 [ [Leap 動作] 常見錯誤](#leap-motion-has-not-integrated-with-mrtk)。 如果檔案存在，請移至下一個步驟。

    - 如果使用 Unity 2019.3，請移至下一個步驟

1. 新增 Leap 移動資料提供者
    - 建立新的 Unity 場景
    - 流覽至 **混合現實工具** 組  >  **新增至場景並設定**，以將 MRTK 新增至場景
    - 選取階層中的 MixedRealityToolkit 遊戲物件，然後選取 [ **複製和自訂** ] 以複製預設的混合現實設定檔。

    ![LeapMotionProfileClone](../Images/CrossPlatform/LeapMotion/LeapProfileClone.png)

    - 選取 **輸入** 設定設定檔

    ![InputConfigurationProfile](../Images/CrossPlatform/LeapMotion/LeapInputConfigurationProfile.png)

    - 在輸入系統設定檔中選取 [ **複製** ]，以啟用修改。

    ![LeapMotionInputProfileClone](../Images/CrossPlatform/LeapMotion/LeapCloneInputSystemProfile.png)

    - 開啟 [ **輸入資料提供者** ] 區段，選取頂端的 [ **加入資料提供** 者]，就會在清單結尾加入新的資料提供者。  開啟新的資料提供者，並將類型設為 MixedReality，並將 **類型** 設定為 **LeapMotion，> LeapMotionDeviceManager**

    ![LeapAddDataProvider](../Images/CrossPlatform/LeapMotion/LeapAddDataProvider.png)

    - 選取 [ **複製** ] 以變更預設的 [Leap 移動] 設定。

    ![LeapDataProviderPreClone](../Images/CrossPlatform/LeapMotion/LeapDeviceManagerProfileBeforeClone.png)

    - 「Leap 移動」資料提供者包含屬性，也 `LeapControllerOrientation` 就是「Leap 移動控制器」的位置。 `LeapControllerOrientation.Headset` 指出控制器已掛接在耳機上。 `LeapControllerOrientation.Desk` 指出控制器是在桌上平放置。 預設值會設定為 `LeapControllerOrientation.Headset` 。  如果方向是桌，則會出現額外的屬性 `LeapControllerOffset` 。  `LeapControllerOffset` 是桌上位置的錨點。  位移的計算方式相對於主要攝影機位置，而預設值是 (0，-0.2，0.2) ，以確保手出現在相機的前方和視野中。
    - `EnterPinchDistance` 而且 `ExitPinchDistance` 是縮小/飛行軌跡偵測的距離臨界值。  縮小手勢的計算方式是測量食指與 thumb 提示之間的距離。  若要在輸入關閉事件時引發，預設值 `EnterPinchDistance` 會設定為0.02。  若要在輸入時引發事件 (結束縮小) ，則索引手指提示與 thumb 提示之間的預設距離為0.05。

    `LeapControllerOrientation`：耳機 (預設)  |  `LeapControllerOrientation`：辦公桌
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../Images/CrossPlatform/LeapMotion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../Images/CrossPlatform/LeapMotion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../Images/CrossPlatform/LeapMotion/LeapDeviceManagerHeadset.png) |     ![LeapDeskInspector](../Images/CrossPlatform/LeapMotion/LeapDeviceManagerDesk.png)

1. 測試閏運動資料提供者
    - 將 Leap 的移動資料提供者加入至輸入系統設定檔之後，請按下 [播放]，將您的手移至 [Leap] 移動控制器前面，您應該會看到該手的接點表示。

1. 建立您的專案
    - 流覽至檔案 **> 組建設定**
    - 只有在使用 Leap 移動資料提供者時，才支援獨立組建。
    - 如需有關如何使用適用于獨立組建的 Windows Mixed Reality 耳機的指示，請參閱 [組建和部署](../../updates-deployment/BuildAndDeploy.md#building-and-deploying-mrtk-to-a-windows-mixed-reality-headset)。

## <a name="getting-the-hand-joints"></a>取得手接點

使用「Leap 運動」資料提供者的取得接點，與 MRTK 明確的手上的手入聯結相同。  如需詳細資訊，請參閱 [手動追蹤](../Input/HandTracking.md#polling-joint-pose-from-handjointutils)。

在 unity 場景中使用 MRTK，並在輸入系統設定檔中新增做為輸入資料提供者的 Leap 移動資料提供者時，請建立空白的遊戲物件，並附加下列範例腳本。

此腳本是一個簡單的範例，示範如何在閏運動手中取出棕櫚接合的姿勢。  當 cube 遵循正確的 Leap 時，球體會跟隨左方的閏年。

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

## <a name="unity-editor-workflow-tip"></a>Unity 編輯器工作流程秘訣

使用「Leap 移動」資料提供者不需要 VR 耳機。  MRTK 應用程式的變更可在編輯器中，使用不帶耳機的飛躍進行測試。

如果未插入 VR 耳機，則會在編輯器中顯示 Leap 運動手。  如果設定為「耳機」，則必須將「 `LeapControllerOrientation` Leap」移動控制器的一端與相機朝前的一端保持在一起。 

> [!NOTE]
> 如果相機是在編輯器中使用 WASD 按鍵移動，且 `LeapControllerOrientation` 是 **耳機**，則手不會跟隨相機。 如果在設定耳機的情況下插入 VR 耳機，則只會在相機移動之後進行 `LeapControllerOrientation` 。   如果設定為 [桌上]，則會在編輯器中追蹤相機移動 `LeapControllerOrientation` 。 

## <a name="removing-leap-motion-from-the-project"></a>從專案移除 Leap 動作

1. 關閉 Unity
1. 關閉 Visual Studio （如果已開啟）
1. 開啟檔案瀏覽器，並流覽至 MRTK Unity 專案的根目錄
    - 刪除 **UnityProjectName/Library** 目錄
    - 刪除 **UnityProjectName/資產/LeapMotion** 目錄
    - 刪除 **UnityProjectName/資產/LeapMotion 元** 檔案
1. 重新開啟 Unity

在 Unity 2018.4 中，您可能會注意到在刪除程式庫和閏運動核心資產之後，仍會在主控台中保留錯誤。
如果在重新開啟之後記錄錯誤，請重新開機 Unity。

## <a name="common-errors"></a>一般錯誤

### <a name="leap-motion-obsolete-errors"></a>Leap 移動過時錯誤

如果 MRTK 來源是來自存放庫，而 Unity 版本是2019.3，則在匯入 Leap 動作 Unity 核心資產之後，主控台中可能會發生下列錯誤：

```
Assets\LeapMotion\Core\Scripts\EditorTools\LeapPreferences.cs(84,6): error CS0618: 'PreferenceItem' is obsolete: '[PreferenceItem] is deprecated. Use [SettingsProvider] instead.
```

在 Unity 版本2018.4 中，可能會記錄下列已淘汰的錯誤：

```
Assets\LeapMotion\Core\Scripts\Attachments\AttachmentHands.cs(105,7): error CS0618: 'PrefabType' is obsolete: 'PrefabType no longer tells everything about Prefab instance.'
```

```
Assets\LeapMotion\Core\Scripts\Attachments\AttachmentHands.cs(105,31): error CS0618: 'PrefabUtility.GetPrefabType(Object)' is obsolete: 'Use GetPrefabAssetType and GetPrefabInstanceStatus to get the full picture about Prefab types.'
```

如果 **混合現實工具組 > 公用程式 > 閏動作 > 設定 CSC 檔案以進行 Leap 動作** ，而不是在 [Leap 動作 Unity 核心資產匯入] 之前選取，就會出現這些錯誤。

#### <a name="solution"></a>解決方法

- 流覽至 **混合現實工具組 > 公用程式 > Leap 移動 > 設定適用于閏運動的 csc** 檔案，這將會更新 csc 檔案，以篩選出轉換成 MRTK 存放庫中錯誤的 Leap 動作警告。
- 關閉 Unity
- 重新開啟 Unity

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap 動作尚未與 MRTK 整合

如果 Unity 版本是2018.4，則會發生此錯誤。 MRTK 來源來自 Unity 套件，以及在匯入閏動作 Unity 核心資產之後。

若要測試 MRTK 是否可辨識是否有「Leap」 Unity 核心資產，請開啟位於 MRTK/範例/示範/HandTracking/中的 LeapMotionHandTrackingExample 場景，然後按下 [播放]。  如果 [Leap 動作] Unity 核心資產被辨識，場景中的資訊面板上會出現綠色訊息。  如果無法辨識閏動作 Unity 核心資產，則會出現紅色的訊息。

如果您的專案中有 Leap 動作 Unity 核心資產，而您在資訊面板上看到紅色的訊息，則必須設定專案。

#### <a name="solution"></a>解決方法

- 流覽至 **混合現實工具組 > 公用程式 > Leap 移動 > 設定 Leap 移動**
  - 如果設定程式未在執行 Unity 動作 Unity 核心資產匯入之後啟動，這將會強制執行「執行」動作整合。

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>複製元件多人 HLAPI 失敗

匯入閏動作 Unity 核心資產時，可能會記錄此錯誤：

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

#### <a name="solution"></a>解決方法

- 短期解決方案是重新開機 Unity。 如需詳細資訊，請參閱 [問題 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 。

## <a name="leap-motion-example-scene"></a>Leap 運動範例場景

範例場景會使用 DefaultLeapMotionConfiguration 設定檔，並判斷 Unity 專案是否已正確設定為使用閏運動資料提供者。

範例場景包含在 **MRTK/範例/示範/HandTracking/** 目錄中的 **MixedReality 範例** 套件中。  

## <a name="see-also"></a>另請參閱

- [輸入提供者](../Input/InputProviders.md)
- [手動追蹤](../Input/HandTracking.md)
