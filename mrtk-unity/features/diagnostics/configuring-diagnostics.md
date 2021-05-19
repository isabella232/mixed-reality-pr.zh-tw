---
title: 設定診斷
description: 在 MRTK 中設定診斷的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 2ff761baa728017eb011cb9105cf203e6e3a72e4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144178"
---
# <a name="configuring-the-diagnostics-system"></a>設定診斷系統

## <a name="general-settings"></a>一般設定

![診斷一般設定](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>啟用詳細資訊記錄

指出是否將啟用詳細資訊 MRTK 記錄。 這會預設為 false，但可以開啟以取得詳細的追蹤，讓 MRTK 小組能夠進行偵測/深入探索問題。 例如，當您提出問題時，請從編輯器或從) 播放程式將 Unity player 記錄 (附加到，以協助縮小 bug 和問題的來源。

請注意，此選項獨立于診斷系統是否已啟用，這會顯示在診斷系統底下，因為它是記錄選項，但最終會以較高的層級運作，因為它會影響整個 MRTK 程式碼基底的記錄。

### <a name="show-diagnostics"></a>顯示診斷

指出診斷系統是否要顯示設定的診斷選項。

停用時，所有設定的診斷選項都會隱藏。

## <a name="profiler-settings"></a>Profiler 設定

![診斷 Profiler 設定](../images/diagnostics/DiagnosticsProfilerSettings.png)

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

- [診斷系統](diagnostics-system-getting-started.md)
- [使用 Visual Profiler](using-visual-profiler.md)
