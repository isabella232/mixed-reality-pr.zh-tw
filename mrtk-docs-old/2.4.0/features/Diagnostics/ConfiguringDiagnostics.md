---
title: ConfiguringDiagnostics
description: 在 MRTK 中設定診斷的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: bc84ab193d3c3233f2930dc955d8293af578348b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688158"
---
# <a name="configuring-the-diagnostics-system"></a>設定診斷系統

## <a name="general-settings"></a>一般設定

![診斷一般設定](../Images/Diagnostics/DiagnosticsGeneralSettings.png)

### <a name="show-diagnostics"></a>顯示診斷

指出診斷系統是否要顯示設定的診斷選項。

停用時，所有設定的診斷選項都會隱藏。

## <a name="profiler-settings"></a>Profiler 設定

![診斷 Profiler 設定](../Images/Diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>顯示 profiler

指出是否要顯示 Visual Profiler。

### <a name="frame-sample-rate"></a>框架取樣率

收集畫面播放速率計算框架的時間長度（以秒為單位）。 範圍為0到5秒。

### <a name="window-anchor"></a>視窗錨點

分析工具視窗應該錨定的視圖埠部分。 預設值為 [下置]。

### <a name="window-offset"></a>視窗位移

從 view 埠中央算出的位移，以放置 Visual Profiler。 位移將會以 *視窗錨點* 屬性的方向進行。

### <a name="window-scale"></a>視窗比例

套用至 profiler 視窗的大小乘數。 例如，將此值設定為2會將視窗大小加倍。

### <a name="window-follow-speed"></a>視窗遵循速度

移動分析工具視窗以維持查看埠內部可見度的速度。

## <a name="programmatically-controlling-the-diagnostics-system"></a>以程式設計方式控制診斷系統

您也可以在執行時間切換診斷系統和 profiler 的可見度。 例如，下列程式碼將會隱藏診斷系統和 profiler。

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>另請參閱

- [診斷系統](DiagnosticsSystemGettingStarted.md)
- [使用 Visual Profiler](UsingVisualProfiler.md)
