---
title: 診斷系統總覽
description: 在 MRTK 中啟用和停用診斷的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 536a35a0af0c0d0190f2f423f4a39e0d89e92c1acaa105ab37e8cf7fdc37cbf5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221808"
---
# <a name="diagnostics-system-overview"></a>診斷系統總覽

混合現實工具組診斷系統提供在應用程式中執行的診斷工具，以啟用應用程式問題的分析。

診斷系統的第一個版本包含 [Visual Profiler](using-visual-profiler.md) ，可在使用應用程式時分析效能問題。

## <a name="getting-started"></a>使用者入門

> [!IMPORTANT]
> **_強烈_** 建議您在整個產品開發週期中啟用診斷系統，並在建立和發行最終版本之前停用為最後一項變更。

開始使用診斷系統有兩個主要步驟。

1. [啟用](#enable-diagnostics) 診斷系統
2. [設定](#configure-diagnostic-options) 診斷選項

### <a name="enable-diagnostics"></a>啟用診斷

診斷系統是由 MixedRealityToolkit 物件 (或另一個 [服務註冊機構](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 元件) 所管理。

下列步驟假設使用 MixedRealityToolkit 物件。 其他服務註冊機構所需的步驟可能會不同。

1. 選取場景階層中的 MixedRealityToolkit 物件。

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

1. 將 [偵測器] 面板移至 [診斷系統] 區段，然後勾選 [啟用]
1. 選取診斷系統執行

    ![選取診斷系統執行](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> 預設設定檔 `DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔) 的使用者，會將診斷系統預先設定為使用該 [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) 物件。

### <a name="configure-diagnostic-options"></a>設定診斷選項

診斷系統會使用設定檔來指定要顯示的元件，以及設定其設定。 請參閱設定 [診斷系統](configuring-diagnostics.md) ，以取得有關可用元件設定的詳細資訊。

> [!IMPORTANT]
> 雖然您可以在開發應用程式時使用 Unity 的播放模式，而不需要建立和部署步驟，但請務必使用在目標硬體和平臺上執行的已編譯應用程式來評估診斷系統結果。
>
> 效能診斷（例如 [Visual Profiler](using-visual-profiler.md)）在從編輯器中執行時，可能無法正確地反映實際的應用程式效能。

## <a name="see-also"></a>另請參閱

- [診斷 API 檔](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [設定診斷系統](configuring-diagnostics.md)
- [使用 Visual Profiler](using-visual-profiler.md)
