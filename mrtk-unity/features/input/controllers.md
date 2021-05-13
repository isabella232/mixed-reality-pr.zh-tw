---
title: 控制器
description: 如何在 MRTK 中使用控制器
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、控制器、
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850334"
---
# <a name="controllers"></a>控制器

[**輸入提供者**](input-providers.md)會自動建立和終結控制器。 每個控制器類型都有一個由 *軸類型* 定義的 *實體輸入*，告訴我們輸入值的資料類型 (數位、單一軸、雙軸、六 Dof、... ) 和 *輸入類型* (按鈕按下、觸發、Thumb 等、空間指標 ... ) 描述輸入的來源。 實體輸入會透過 **控制器輸入對應設定檔**，在混合現實工具組元件的 *輸入系統設定檔* 中，對應至 *輸入動作*。

MRTK 會自動偵測 WMR 控制器，並在安裝 [**MixedReality. 輸入**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 套件時加以顯示。 使用 OpenXR 管線時，控制器模型只會顯示在編輯器中。 若要將 Oculus 控制器模型視覺化，請遵循 [Oculus 的部署指示](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)

![控制器輸入對應](../images/input/ControllerInputMapping.png)