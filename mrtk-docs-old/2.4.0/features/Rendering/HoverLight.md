---
title: HoverLight
description: MRTK 中的 HoverLight 範例檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、停留燈、
ms.openlocfilehash: 98090cbb9cc7a18806df710078f8ba19a5f31240
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681231"
---
# <a name="hover-light"></a>停留燈

[`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)是一種[Fluent Design 系統](https://www.microsoft.com/design/fluent/)範例，會模擬停留在物件介面附近的[點光線](https://docs.unity3d.com/Manual/Lighting.html)。 通常用於遠離互動，應用程式可以透過元件來控制停留光的屬性 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。

您 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 必須使用「 *混合現實工具* 組」/「標準著色器」所影響的材質，而且必須啟用「暫止 *燈* 」屬性。

> [!Note]
> 預設支援最多兩個 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。

## <a name="examples"></a>範例

MRTK 內的大部分場景會利用 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。 最常見的使用案例可以在 MRTK/SDK/Features/UX/Prefabs/cursor/DefaultCursor 上找到。預製專案

## <a name="advanced-usage"></a>進階使用方式

根據預設，一次只有兩個 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 會將 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 亮亮。 如果您的專案需要兩個以上的專案 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 來影響 [材質](https://docs.unity3d.com/ScriptReference/Material.html) ，下列範例程式碼示範如何達成此目的。

> [!Note]
> 有許多 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 亮亮的 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 將會增加圖元著色器的指示，而且會影響效能。 請在您的專案內分析這些變更。

*如何增加 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 從二到四的可用數目。*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define HOVER_LIGHT_COUNT 2

// to:

#define HOVER_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCount = 2;

// to:

private const int hoverLightCount = 4;
```

> [!NOTE]
> 如果 Unity 記錄類似下面的警告，您必須先重新開機 Unity，變更才會生效。
>
> `Property (_HoverLightData) exceeds previous array size (8 vs 4). Cap to previous >size.`

## <a name="see-also"></a>另請參閱

* [MRTK 標準著色器](../README_MRTKStandardShader.md)
