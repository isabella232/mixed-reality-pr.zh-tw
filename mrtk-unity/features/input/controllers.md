---
title: 控制器
description: 如何在 MRTK 中使用控制器
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、控制器、
ms.openlocfilehash: ea3dbd11baa669750f3bccc09d6cd7ab3eb7688f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176923"
---
# <a name="controllers"></a>控制器

[**輸入提供者**](input-providers.md)會自動建立和終結控制器。 每個控制器類型都有一個由 *軸類型* 定義的 *實體輸入*，告訴我們輸入值的資料類型 (數位、單一軸、雙軸、六 Dof、... ) 和 *輸入類型* (按鈕按下、觸發、Thumb 等、空間指標 ... ) 描述輸入的來源。 實體輸入會透過 **控制器輸入對應設定檔**，在混合現實工具組元件的 *輸入系統設定檔* 中，對應至 *輸入動作*。

![控制器輸入對應](../images/input/ControllerInputMapping.png)
