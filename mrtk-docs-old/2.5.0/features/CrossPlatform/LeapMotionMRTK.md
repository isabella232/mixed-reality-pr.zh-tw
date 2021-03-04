---
title: LeapMotionMRTK
description: 針對閏運動設定的檔
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、閏運動、
ms.openlocfilehash: d2378802fc0a5c54568b1a5c3a0316f7667e40c2
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780655"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>如何在 MRTK 中使用 Ultraleap) 手勢來設定 Leap 運動 (

需要 [Leap 移動控制器](https://www.ultraleap.com/product/leap-motion-controller/) 才能使用此資料提供者。

Leap 的移動資料提供者可針對 VR 進行明確的手動追蹤，而且在編輯器中快速建立原型時可能很有用。  您可以將資料提供者設定為使用在耳機上掛接的 Leap 運動控制器，或放在桌上的上架。

![LeapMotionIntroGif](../Images/CrossPlatform/LeapMotion/LeapHandsGif3.gif)

此提供者可在獨立平臺上的編輯器和裝置上使用。  它也可以在 UWP 平臺上的編輯器中使用，但不能在 UWP 組建中使用。

|支援的 Leap 動作 Unity 模組版本|
|---|
|4.5.0|
|4.5.1|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>在 MRTK 中使用 Ultraleap) 手動追蹤 (的 Leap 動作

1. 匯入 MRTK 和 Leap 動作 Unity 模組
    - 如果尚未安裝，請安裝「 [Leap 動作 SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) 」
    - 將 **MixedReality** 套件匯入 Unity 專案。
    - 下載最新版本的 [Leap 動作 Unity 模組](https://developer.leapmotion.com/unity) 並匯入到專案中
        - 僅在 Unity 模組內匯入 **核心** 套件

1. 整合 Leap 動作 Unity 模組與 MRTK
    - 在專案中有 Unity 模組之後，請流覽至 **混合現實工具** 組的  >  **leap 動作**  >  **整合閏動作 Unity 模組**
    > [!NOTE]
    > 將 Unity 模組整合至 MRTK 會將10個元件定義新增至專案，並加入 **MixedReality** 的參考。 LeapMotion 元件定義。 確認已關閉 Visual Studio。

     ![LeapMotionIntegration](../Images/CrossPlatform/LeapMotion/LeapMotionIntegrateMenu.png)

1. 新增 Leap 移動資料提供者
    - 建立新的 Unity 場景
    - 流覽至 **混合現實工具** 組  >  **新增至場景並設定**，以將 MRTK 新增至場景
    - 選取階層中的 MixedRealityToolkit 遊戲物件，然後選取 [ **複製和自訂** ] 以複製預設的混合現實設定檔。

    ![LeapMotionProfileClone](../Images/CrossPlatform/CloneProfile.png)

    - 選取 **輸入** 設定設定檔

    ![InputConfigurationProfile](../Images/CrossPlatform/InputConfigurationProfile.png)

    - 在輸入系統設定檔中選取 [ **複製** ]，以啟用修改。

    ![LeapMotionInputProfileClone](../Images/CrossPlatform/CloneInputSystemProfile.png)

    - 開啟 [ **輸入資料提供者** ] 區段，選取頂端的 [ **加入資料提供** 者]，就會在清單結尾加入新的資料提供者。  開啟新的資料提供者，並將類型設為 MixedReality，並將 **類型** 設定為 **LeapMotion，> LeapMotionDeviceManager**

    ![LeapAddDataProvider](../Images/CrossPlatform/LeapMotion/LeapAddDataProvider.png)

    - 選取 [ **複製** ] 以變更預設的 [Leap 移動] 設定。

    ![LeapDataProviderPreClone](../Images/CrossPlatform/LeapMotion/LeapMotionDeviceManagerProfile.png)

    - 「Leap 移動」資料提供者包含屬性，也 `LeapControllerOrientation` 就是「Leap 移動控制器」的位置。 `LeapControllerOrientation.Headset` 指出控制器已掛接在耳機上。 `LeapControllerOrientation.Desk` 指出控制器是在桌上平放置。 預設值會設定為 `LeapControllerOrientation.Headset` 。
    - 每個控制器方向都包含 offset 屬性：
      - **耳機** 方向位移屬性會鏡像 LeapXRServiceProvider 元件中的位移屬性。  `LeapVRDeviceOffsetMode`有三個選項：預設值、手動標頭位移和轉換。  如果位移模式是預設值，則不會將位移套用至 Leap 移動控制器。  手動標頭位移模式允許修改三個屬性： `LeapVRDeviceOffsetY` 、 `LeapVRDeviceOffsetZ` 和 `LeapVRDeviceTiltX` 。  然後，軸位移屬性值會套用至預設控制器放置。  [轉換位移] 模式包含 [轉換] 屬性，以 `LeapVRDeviceOrigin` 指定 Leap 移動控制器的新來源。
      - [ **桌** 上方向] 包含 `LeapControllerOffset` 屬性，可定義桌上的錨點位置。  位移的計算方式相對於主要攝影機位置，而預設值是 (0，-0.2，0.35) ，以確保手出現在相機的前方和視野中。

        > [!NOTE]
        > 當應用程式啟動時，設定檔中的位移屬性會套用一次。  若要在執行時間期間修改值，請從 [Leap 移動裝置管理員] 取得 [Leap 移動服務提供者]：
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` 而且 `ExitPinchDistance` 是縮小/飛行軌跡偵測的距離臨界值。  縮小手勢的計算方式是測量食指與 thumb 提示之間的距離。  若要在輸入關閉事件時引發，預設值 `EnterPinchDistance` 會設定為0.02。  若要在輸入時引發事件 (結束縮小) ，則索引手指提示與 thumb 提示之間的預設距離為0.05。

    `LeapControllerOrientation`：耳機 (預設)  |  `LeapControllerOrientation`：辦公桌
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../Images/CrossPlatform/LeapMotion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../Images/CrossPlatform/LeapMotion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../Images/CrossPlatform/LeapMotion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../Images/CrossPlatform/LeapMotion/LeapMotionDeviceManagerDesk.png)

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

1. 流覽至 **混合現實工具** 組的  >  **閏動作**  >  **個別的 leap 動作 Unity 模組**
    - 讓 Unity 重新整理為 MixedReality 中的參考，在此步驟中修改 **LeapMotion asmdef** 檔案
1. 關閉 Unity
1. 關閉 Visual Studio （如果已開啟）
1. 開啟檔案瀏覽器，並流覽至 MRTK Unity 專案的根目錄
    - 刪除 **UnityProjectName/Library** 目錄
    - 刪除 **UnityProjectName/資產/外掛程式/LeapMotion** 目錄
    - 刪除 **UnityProjectName/資產/外掛程式/LeapMotion 元** 檔案
1. 重新開啟 Unity

在 Unity 2018.4 中，您可能會注意到在刪除程式庫和閏運動核心資產之後，仍會在主控台中保留錯誤。
如果在重新開啟之後記錄錯誤，請重新開機 Unity。

## <a name="common-errors"></a>一般錯誤

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap 動作尚未與 MRTK 整合

若要測試閏運動 Unity 模組是否已與 MRTK 整合：

- 流覽至 **混合現實工具組 > 公用程式 > Leap 移動 > 檢查整合狀態**
  - 這將會顯示一個快顯視窗，其中顯示有關 Leap 的 Unity 模組是否已與 MRTK 整合的訊息。
- 如果訊息指出資產尚未整合：
  - 請確定在專案中有「Leap」動作 Unity 模組
  - 請確定已支援新增的版本，請參閱頁面頂端的表格，以取得支援的版本。
  - 嘗試 **混合現實工具組 > 公用程式 > > 整合 Leap 動作 Unity 模組**

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>複製元件多人 HLAPI 失敗

匯入閏動作 Unity 核心資產時，可能會記錄此錯誤：

```

Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**方案**

- 短期解決方案是重新開機 Unity。 如需詳細資訊，請參閱 [問題 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 。

## <a name="leap-motion-example-scene"></a>Leap 運動範例場景

範例場景會使用 DefaultLeapMotionConfiguration 設定檔，並判斷 Unity 專案是否已正確設定為使用閏運動資料提供者。

範例場景包含在 **MRTK/範例/示範/HandTracking/** 目錄中的 **MixedReality 範例** 套件中。  

## <a name="see-also"></a>另請參閱

- [輸入提供者](../Input/InputProviders.md)
- [手動追蹤](../Input/HandTracking.md)
