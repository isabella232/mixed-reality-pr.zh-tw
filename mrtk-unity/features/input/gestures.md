---
title: 軌跡
description: 在 MRTK 中 Docummentation 手勢和其事件
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、手勢、
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176878"
---
# <a name="gestures"></a>軌跡

手勢是根據人為手的輸入活動。 有兩種類型的裝置會在 MRTK 中引發手勢輸入事件：

- Windows Mixed Reality 裝置，例如 HoloLens。 這會描述捏合運動 ( 「點擊」 ) 和點擊和按住手勢。

  如需 HoloLens 手勢的詳細資訊，請參閱[Windows Mixed Reality 手勢檔](/windows/mixed-reality/gestures)。

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)包裝[UNITY XR。Wsa。GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html)從 HoloLens 裝置取用 Unity 的手勢事件。

- 觸控式螢幕裝置。

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) 包裝支援實體觸控畫面的 [Unity 觸控類別](https://docs.unity3d.com/ScriptReference/Touch.html) 。

這兩個輸入來源都使用 _手勢設定_ 設定檔，分別將 Unity 的觸控和手勢事件轉譯成 MRTK 的 [輸入動作](input-actions.md)。 您可以在 _輸入系統設定_ 設定檔中找到此設定檔。

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>手勢事件

執行其中一個軌跡處理常式介面可接收手勢事件： [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) 或 [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (查看 [事件處理常式](input-events.md)) 的資料表。

請參閱 [範例場景](#example-scene) ，以取得筆勢事件處理常式的範例執行。

在執行泛型版本時， *OnGestureCompleted* 和 *OnGestureUpdated* 事件可以接收下列類型的類型資料：

- `Vector2` -2D 位置手勢。 由觸控畫面產生，以通知他們 [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) 。
- `Vector3` -3D 位置手勢。 由 HoloLens 所產生，告知：
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) 操作事件的
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) 流覽事件的
- `Quaternion` -3D 旋轉手勢。 可供自訂輸入來源使用，但目前不是由任何現有專案所產生。
- `MixedRealityPose` -合併的3D 位置/旋轉手勢。 可供自訂輸入來源使用，但目前不是由任何現有專案所產生。

## <a name="order-of-events"></a>事件順序

有兩個主要的事件鏈，視使用者輸入而定：

- 「保留」：
    1. 按住 ctrl：
        - 開始 _操作_
    1. 按住 [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)：
        - 開始 _保存_
    1. 放開點：
        - 完成 _保存_
        - 完成 _操作_

- 「移動」：
    1. 按住 ctrl：
        - 開始 _操作_
    1. 按住 [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)：
        - 開始 _保存_
    1. 將手移至 [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)之外：
        - 取消 _保存_
        - 開始 _導覽_
    1. 放開點：
        - 完成 _操作_
        - 完成 _導覽_

## <a name="example-scene"></a>範例場景

**HandInteractionGestureEventsExample** (資產/MRTK/範例/示範/HandTracking/場景) 場景顯示如何使用指標結果，在叫用位置產生物件。

`GestureTester` (資產/MRTK/範例/示範/HandTracking/腳本) 腳本是透過 gameobject 將手勢事件視覺化的範例執行。 處理常式函式會變更指標物件的色彩，並在場景中的文字物件中顯示最後記錄的事件。
