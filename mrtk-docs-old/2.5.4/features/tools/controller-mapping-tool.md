---
title: ControllerMappingTool
description: MRTK 中的控制器對應工具檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 4a2ad67916d2fb9dd5fb3f4061934a27e3aa8763d64c5561a6e1b178a708069a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199796"
---
# <a name="controller-mapping-tool"></a>控制器對應工具

控制器對應工具是裝置上的執行時間 (或編輯器) 工具，可讓開發人員快速判斷硬體控制器的 Unity 輸入軸和按鈕對應 (例如：移動控制器) 。

當您針對新的硬體控制器開發支援時，此工具非常有用。 它也可以協助確認現有控制器的支援類別中可疑的控制項對應問題。

![控制器對應工具](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>使用控制器對應工具

若要開始使用控制器對應工具，請流覽至 **MRTK/tools/RuntimeTools/tools/ControllerMappingTool** ，然後開啟 **ControllerMappingTool** 場景。 載入場景之後，您可以在編輯器中使用播放模式來執行專案，或在裝置上建立並執行專案。

檢查控制器的 Unity 對應：

- 連線控制器
- 按下每個按鈕並移動每個軸
- 請注意顯示中的對應
- 更新控制器的輸入系統資料提供者中的控制項對應

> [!NOTE]
> 控制器對應工具不會利用 Microsoft Mixed Reality 工具組元件。 它會直接與 Unity 通訊，以決定並顯示控制項對應。

### <a name="all-controls-display"></a>所有控制項顯示

大型顯示面板會報告所有已定義 Unity 輸入軸和按鈕的狀態， (例如：軸10、按鈕 3) 。 此面板會提供控制器狀態的完整觀點。

![所有控制項顯示](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>現用控制項顯示

較小、窄的顯示面板會顯示 Unity 輸入 axed 以及處於作用中狀態的按鈕 (例如：按下按鈕) 。 作用中的控制項顯示提供控制器狀態的簡單讀取摘要視圖。

![現用控制項顯示](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>另請參閱

- [建立輸入系統資料提供者](../input/create-data-provider.md)
- [InputFeatureUsage 工具](input-feature-usage-tool.md)
