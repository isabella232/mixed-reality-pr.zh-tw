---
title: 輸入功能使用方式工具
description: MRTK 中的檔 InputFeatureUsage 工具
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 0f2d3d3eb07d8b631f3f11a8b497a22a028a2f24
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145010"
---
# <a name="inputfeatureusage-tool"></a>InputFeatureUsage 工具

InputFeatureUsage 工具是裝置上的執行時間 (或編輯器) 工具，可讓開發人員快速判斷所偵測到之輸入來源的可用 Unity InputFeatureUsages， (例如：移動控制器或明確的) 。

> [!NOTE]
> 此場景僅適用于 Unity 2019.3 或更新版本。

當您針對新的硬體控制器開發支援時，此工具非常有用。 它也可以協助確認現有控制器的支援類別中可疑的控制項對應問題。

![InputFeatureUsage 工具](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>使用 InputFeatureUsage 工具

若要開始使用 InputFeatureUsage 工具，請流覽至 [ **MRTK]/[工具]/[RuntimeTools]/[工具]/[InputFeatureUsageTool** ]，然後開啟 **InputFeatureUsageTool** 場景。 載入場景之後，您可以在編輯器中使用播放模式來執行專案，或在裝置上建立並執行專案。

檢查控制器的 Unity 對應：

- 連接控制器
- 按下每個按鈕並移動每個軸
- 請注意顯示中的功能使用方式
- 更新控制器的輸入系統資料提供者中的控制項對應

> [!NOTE]
> InputFeatureUsage 工具不會利用 Microsoft Mixed Reality 工具組元件。 它會直接與 Unity 通訊，以決定並顯示功能的使用方式。

### <a name="panels"></a>窗格

面板會顯示所有已偵測到之 Unity 輸入來源上所有回報 InputFeatureUsages 的目前狀態。

頂端較小的面板會列出所有偵測到的來源名稱。

## <a name="see-also"></a>另請參閱

- [建立輸入系統資料提供者](../input/create-data-provider.md)
- [控制器對應工具](controller-mapping-tool.md)
