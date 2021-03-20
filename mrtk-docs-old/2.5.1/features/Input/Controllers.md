---
title: 控制器
description: 如何在 MRTK 中使用控制器
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、控制器、
ms.openlocfilehash: 3c4566992f79c367e3693772386ca90a5e2505af
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104680791"
---
# <a name="controllers"></a><span data-ttu-id="12dc2-104">控制器</span><span class="sxs-lookup"><span data-stu-id="12dc2-104">Controllers</span></span>

<span data-ttu-id="12dc2-105">[**輸入提供者**](InputProviders.md)會自動建立和終結控制器。</span><span class="sxs-lookup"><span data-stu-id="12dc2-105">Controllers are created and destroyed automatically by [**input providers**](InputProviders.md).</span></span> <span data-ttu-id="12dc2-106">每個控制器類型都有一個由 *軸類型* 定義的 *實體輸入*，告訴我們輸入值的資料類型 (數位、單一軸、雙軸、六 Dof、... ) 和 *輸入類型* (按鈕按下、觸發、Thumb 等、空間指標 ... ) 描述輸入的來源。</span><span class="sxs-lookup"><span data-stu-id="12dc2-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="12dc2-107">實體輸入會透過 **控制器輸入對應設定檔**，在混合現實工具組元件的 *輸入系統設定檔* 中，對應至 *輸入動作*。</span><span class="sxs-lookup"><span data-stu-id="12dc2-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

<img src="../images/input/ControllerInputMapping.png" style="max-width:100%;" alt="Input maping">
