---
title: 控制器
description: 如何在 MRTK 中使用控制器
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、控制器、
ms.openlocfilehash: 3a1651d381d729341a48c7563a74ffe87a584a8b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682851"
---
# <a name="controllers"></a>控制器

[**輸入提供者**](InputProviders.md)會自動建立和終結控制器。 每個控制器類型都有一個由 *軸類型* 定義的 *實體輸入*，告訴我們輸入值的資料類型 (數位、單一軸、雙軸、六 Dof、... ) 和 *輸入類型* (按鈕按下、觸發、Thumb 等、空間指標 ... ) 描述輸入的來源。 實體輸入會透過 **控制器輸入對應設定檔**，在混合現實工具組元件的 *輸入系統設定檔* 中，對應至 *輸入動作*。

<img src="../Images/Input/ControllerInputMapping.png" style="max-width:100%;" alt="Controller Input Mapping">
