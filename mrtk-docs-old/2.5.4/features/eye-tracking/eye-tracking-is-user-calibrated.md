---
title: EyeTracking_IsUserCalibrated
description: 如何在 MRTK 中設定使用者視覺校正
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、校正、
ms.openlocfilehash: 69a8882b6b90af6610b6d7a4d77cc016730e0f18df161c1ffb28f908b986ca5f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211636"
---
# <a name="eye-calibration"></a>眼睛校正

![眼睛校正通知的螢幕擷取畫面](../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>概觀

如果您的應用程式體驗有基本的功能，您可能想要確定使用者的眼睛校正是否有效。
這是不正確主要原因，就是使用者在放入裝置時，選擇略過眼睛追蹤校正。

本頁涵蓋下列內容：

- 說明如何偵測使用者是否有眼睛的校正
- 提供範例，說明如何觸發使用者通知，以指示使用者進行眼睛校正
  - 如果眼睛校正變為有效，則自動解除通知
  - 如果使用者選擇在沒有校正的情況下繼續時，手動解除通知

### <a name="how-to-detect-the-eye-calibration-state"></a>如何偵測眼睛校正狀態

MRTK 中的眼睛追蹤設定是透過介面進行設定 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 。

使用 [CoreServices](eye-tracking-eye-gaze-provider.md) 時，會提供在執行時間的工具組中註冊的預設注視提供者實作為。 `IMixedRealityEyeGazeProvider.IsEyeGazeValid``bool?`如果尚未提供來自眼睛追蹤器的資訊，則會傳回 null。
收到資料之後，它會傳回 true 或 false，表示使用者的眼睛追蹤校正是有效的或不正確。

### <a name="sample-eye-calibration-notification---step-by-step"></a>範例眼睛校正通知-逐步解說

1. 開啟 MRTK 的眼睛追蹤範例套件 (資產/MRTK/範例/示範/EyeTracking) 

2. Load _EyeTrackingDemo-00-RootScene unity_ 場景

3. 查看 _EyeCalibrationChecker_：
   - 在此場景中，我們已經有一個範例，可偵測目前的使用者是否已在 *_EyeCalibrationChecker_ 遊戲物件* 下校正。
這只是家長的一些文字網格，並且有一些額外的觸發程式來將通知和輸出混合。這包括在啟用時緩慢增加其大小和不透明度。
一旦關閉通知，將會減緩其大小並淡出。

   - 附加至 *_EyeCalibrationChecker_ 遊戲物件* 的 [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker)腳本會公開兩個 Unity 事件：
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - 這些事件只會在校正狀態變更時觸發。 因此，如果使用者選擇關閉通知，將不會再次顯示通知，直到
      - 應用程式會重新開機
      - 偵測到有效的使用者，然後新的 uncalibrated 使用者將裝置放在

   - 為了測試是否正確觸發動畫和事件，EyeCalibrationChecker 腳本會擁有 `bool editorTestUserIsCalibrated` 旗標。 例如，在 Unity 編輯器中執行時，可以測試：
      1. 當校正狀態從 true 變更為 false 時，是否自動顯示通知
      1. 當狀態從 false 變更為 true 時，是否會再次自動關閉通知。

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a>另請參閱

- [MRTK 眼追蹤總覽](eye-tracking-main.md)
- [MRTK 眼睛追蹤設定](eye-tracking-basic-setup.md)
- [透過程式碼 MRTK 眼睛追蹤](eye-tracking-eye-gaze-provider.md)
- [HoloLens 2目視追蹤檔](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)
