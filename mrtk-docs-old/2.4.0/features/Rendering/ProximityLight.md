---
title: ProximityLight
description: 在 MRTK 中使用範例的相近淺色檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: e50db18eb48841fd910dc68c29a17cbf951406cb
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780342"
---
# <a name="proximity-light"></a>近亮光

[`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)是一種[流暢的設計系統](https://www.microsoft.com/design/fluent/)典範，它會在物件的表面上模擬「漸層反轉點燈」。 通常用於近乎互動，應用程式可以透過元件控制近亮的屬性 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。

若要由 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *混合現實工具組/標準* 著色器所影響的材質，必須使用，且必須啟用 *鄰近性光線* 屬性。

> [!NOTE]
> 預設支援最多兩個 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。

## <a name="examples"></a>範例

MRTK 內的大部分場景會利用 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。 最常見的使用案例可以在 MRTK/SDK/Features/UX/Prefabs/cursor/FingerCursor 上找到。預製專案

## <a name="advanced-usage"></a>進階使用方式

根據預設，一次只有兩個 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 會將 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 亮亮。 如果您的專案需要兩個以上的專案 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 來影響 [材質](https://docs.unity3d.com/ScriptReference/Material.html) ，下列範例程式碼示範如何達成此目的。

> [!NOTE]
> 有許多 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 亮亮的 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 將會增加圖元著色器的指示，而且會影響效能。 請在您的專案內分析這些變更。

*如何增加 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 從二到四的可用數目。*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> 如果 Unity 記錄類似下面的警告，您必須先重新開機 Unity，變更才會生效。
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>另請參閱

* [MRTK 標準著色器](../README_MRTKStandardShader.md)
