---
title: HoverLight
description: MRTK 中的 HoverLight 範例檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、停留燈、
ms.openlocfilehash: af99c84684dd8b50e81ecd27b86e2be5f473e954
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780219"
---
# <a name="hover-light"></a>停留燈

[`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)是一種[流暢的設計系統](https://www.microsoft.com/design/fluent/)典範，它會模擬停留在物件介面附近的[點淺色](https://docs.unity3d.com/Manual/Lighting.html)。 通常用於遠離互動，應用程式可以透過元件來控制停留光的屬性 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。

您 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 必須使用「 *混合現實工具* 組」/「標準著色器」所影響的材質，而且必須啟用「暫止 *燈* 」屬性。

> [!Note]
> MRTK/Standard 著色器預設支援最多兩個 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) ，但將會調整為支援四個，然後在場景中新增更多燈光時調整為10。

## <a name="examples"></a>範例

MRTK 內的大部分場景會利用 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。 最常見的使用案例可以在 MRTK/SDK/Features/UX/Prefabs/cursor/DefaultCursor 上找到。預製專案

**HoverLightExamples** 場景也會示範行為的用法 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) ，您可以在下列位置找到： MRTK/範例/示範/StandardShader/場景/

## <a name="advanced-usage"></a>進階使用方式

[`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)一次只能對一個[材質](https://docs.unity3d.com/ScriptReference/Material.html)進行一次亮妥。 如果您的專案需要十個以上的資料 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 來影響 [材質](https://docs.unity3d.com/ScriptReference/Material.html) ，下列範例程式碼示範如何達成此目的。

> [!Note]
> 有許多 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 亮亮的 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 將會增加圖元著色器的指示，而且會影響效能。 **請在您的專案內分析這些變更。**

*如何將可用的數目增加 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 至12個。*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> 如果 Unity 記錄類似下面的警告，您必須先重新開機 Unity，變更才會生效。
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>另請參閱

* [MRTK 標準著色器](MRTKStandardShader.md)
