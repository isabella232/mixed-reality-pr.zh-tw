---
title: UsingVisualProfiler
description: 在 MRTK 中使用 Visual profiler 的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: f268bfe18cf44129f88ebdaf4cd56e442c458b59
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684661"
---
# <a name="using-the-visual-profiler"></a>使用 visual profiler

VisualProfiler 可讓您輕鬆地在應用程式內查看混合現實應用程式的效能。 所有混合現實工具組平臺都支援分析工具，包括：

- Microsoft HoloLens (第1代) 
- Microsoft HoloLens 2
- Windows Mixed Reality 沉浸式頭戴裝置
- OpenVR

開發應用程式時，請將焦點放在場景的多個部分，因為 Visual Profiler 會顯示相對於目前視圖的資料。

> [!IMPORTANT]
> 使用複雜物件、粒子效果或活動將注意力集中在場景的部分。 這些因素和其他因素通常有助於降低應用程式效能，而不是理想的使用者體驗。

## <a name="visual-profiler-interface"></a>Visual profiler 介面

![Visual Profiler 介面](../images/diagnostics/VisualProfiler.png)

Visual Profiler 介面包含下列元件：

- [畫面播放速率](#frame-rate)
- [畫面格時間](#frame-time)
- [框架圖形](#frame-graph)
- [記憶體使用率](#memory-utilization)

### <a name="frame-rate"></a>畫面播放速率

介面左上角是畫面播放速率，以每秒的畫面格速率來測量。 為了獲得最佳的使用者體驗和緩和，此值應該越高越好。

特定平臺和硬體設定在可達成的最大畫面播放速率中扮演著重要的角色。 一些常見的目標值包括：

- Microsoft HoloLens：60
- Windows Mixed Reality Ultra：90

> [!NOTE]
> 由於在 [預設的 MRC 為使用中時，在 HoloLens 上的畫面播放速率節流](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)，因此當影片和相片被捕獲時，visual profiler 會自行隱藏。 這項設定可以在診斷系統設定檔中覆寫。

### <a name="frame-time"></a>畫面格時間

畫面播放速率的右邊是花費在 CPU 的畫面格時間（以毫秒為單位）。 為了達到先前所述的目標畫面播放速率，應用程式可以在每個框架中花費下列時間長度：

- 60 fps：16.6 毫秒
- 90 fps：11.1 毫秒

已規劃在未來的版本中新增 GPU 時間。

### <a name="frame-graph"></a>框架圖形

框架圖形提供應用程式框架速率歷程記錄的圖形顯示。

![Visual Profiler 缺少框架圖形](../images/diagnostics/VisualProfilerMissedFrames.png)

使用應用程式時，請尋找遺漏的框架，指出應用程式未達到其目標畫面播放速率，而且可能需要優化工作。

### <a name="memory-utilization"></a>記憶體使用量

記憶體使用量顯示可讓您輕鬆瞭解目前的視圖如何影響應用程式的記憶體耗用量。

![Visual Profiler 記憶體圖表](../images/diagnostics/VisualProfilerMemory.png)

使用應用程式時，請尋找總記憶體使用量。 關鍵指標包括接近記憶體限制，以及快速變更使用方式。

## <a name="customizing-the-visual-profiler"></a>自訂 visual profiler

您可以透過診斷系統設定檔自訂 Visual Profiler 的外觀和行為。 如需詳細資訊，請參閱設定 [診斷系統](configuring-diagnostics.md) 。

## <a name="see-also"></a>另請參閱

- [診斷系統](diagnostics-system-getting-started.md)
- [設定診斷系統](configuring-diagnostics.md)
