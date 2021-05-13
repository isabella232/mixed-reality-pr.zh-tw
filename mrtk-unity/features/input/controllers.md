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
# <a name="controllers"></a><span data-ttu-id="dc3d2-104">控制器</span><span class="sxs-lookup"><span data-stu-id="dc3d2-104">Controllers</span></span>

<span data-ttu-id="dc3d2-105">[**輸入提供者**](input-providers.md)會自動建立和終結控制器。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="dc3d2-106">每個控制器類型都有一個由 *軸類型* 定義的 *實體輸入*，告訴我們輸入值的資料類型 (數位、單一軸、雙軸、六 Dof、... ) 和 *輸入類型* (按鈕按下、觸發、Thumb 等、空間指標 ... ) 描述輸入的來源。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="dc3d2-107">實體輸入會透過 **控制器輸入對應設定檔**，在混合現實工具組元件的 *輸入系統設定檔* 中，對應至 *輸入動作*。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

<span data-ttu-id="dc3d2-108">MRTK 會自動偵測 WMR 控制器，並在安裝 [**MixedReality. 輸入**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 套件時加以顯示。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-108">MRTK will automatically detect WMR controllers and display them when the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package is installed.</span></span> <span data-ttu-id="dc3d2-109">使用 OpenXR 管線時，控制器模型只會顯示在編輯器中。</span><span class="sxs-lookup"><span data-stu-id="dc3d2-109">Controllers models will only show up in the editor when using the OpenXR pipeline.</span></span> <span data-ttu-id="dc3d2-110">若要將 Oculus 控制器模型視覺化，請遵循 [Oculus 的部署指示](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="dc3d2-110">To visualize Oculus controller models, follow the [Oculus Quest deployment instructions](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span></span>

![控制器輸入對應](../images/input/ControllerInputMapping.png)