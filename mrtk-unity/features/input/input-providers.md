---
title: 輸入提供者
description: MRTK 中不同類型的輸入提供者相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 134ab9304a9fb56ff67dd52e46d030dec2ca4b4c8e528e2c51046fc60c1918f7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207640"
---
# <a name="input-providers"></a>輸入提供者

輸入提供者會在 **已註冊的服務提供者設定檔** 中註冊，可在混合現實工具組元件中找到：

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

這些是現成可用的輸入提供者，以及其對應的控制器：

| 輸入提供者 | 控制器 |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | 模擬的手 |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | 滑鼠  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | 一般 OpenVR、Vive 棒、Vive Knuckles、Oculus Touch、Oculus Remote、Windows Mixed Reality OpenVR  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | 一般搖桿  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Unity 觸控控制器  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *無*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | WMR 清楚的手、WMR 控制器、WMR GGV (注視、手勢和 Voice) 手 |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *無* |

聽寫和語音提供者不會建立任何控制器，而是會直接引發自己的特製化輸入事件。

自訂輸入提供者可透過實作為 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 介面來建立。

如需詳細資訊，請參閱 [建立輸入系統資料提供者](create-data-provider.md)。
