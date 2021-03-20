---
title: InputProviders
description: MRTK 中不同類型的輸入提供者相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 56b182f81e2dd1277050b8b1b3f7a7d7434ac92a
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683391"
---
# <a name="input-providers"></a>輸入提供者

輸入提供者會在 **已註冊的服務提供者設定檔** 中註冊，可在混合現實工具組元件中找到：

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Registerd Service">

這些是現成可用的輸入提供者，以及其對應的控制器：

| 輸入提供者 | 控制器 |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | 模擬的手 |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | 滑鼠  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | 一般 OpenVR、Vive 棒、Vive Knuckles、Oculus Touch、Oculus Remote、Windows Mixed Reality OpenVR  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | 一般搖桿  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Unity 觸控控制器  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *None*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | WMR 清楚的手、WMR 控制器、WMR GGV (注視、手勢和 Voice) 手 |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *None* |

聽寫和語音提供者不會建立任何控制器，而是會直接引發自己的特製化輸入事件。

自訂輸入提供者可透過實作為 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 介面來建立。

如需詳細資訊，請參閱 [建立輸入系統資料提供者](CreateDataProvider.md)。
