---
title: HoverLight
description: MRTK 中的 HoverLight 範例檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、停留燈、
ms.openlocfilehash: 129ba1fc0614e414d3f3a67a0e633e87279b7f6c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780907"
---
# <a name="hover-light"></a><span data-ttu-id="41c1e-104">停留燈</span><span class="sxs-lookup"><span data-stu-id="41c1e-104">Hover Light</span></span>

<span data-ttu-id="41c1e-105">[`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)是一種[流暢的設計系統](https://www.microsoft.com/design/fluent/)典範，它會模擬停留在物件介面附近的[點淺色](https://docs.unity3d.com/Manual/Lighting.html)。</span><span class="sxs-lookup"><span data-stu-id="41c1e-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="41c1e-106">通常用於遠離互動，應用程式可以透過元件來控制停留光的屬性 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。</span><span class="sxs-lookup"><span data-stu-id="41c1e-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="41c1e-107">您 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 必須使用「 *混合現實工具* 組」/「標準著色器」所影響的材質，而且必須啟用「暫止 *燈* 」屬性。</span><span class="sxs-lookup"><span data-stu-id="41c1e-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="41c1e-108">預設支援最多兩個 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。</span><span class="sxs-lookup"><span data-stu-id="41c1e-108">Up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="41c1e-109">範例</span><span class="sxs-lookup"><span data-stu-id="41c1e-109">Examples</span></span>

<span data-ttu-id="41c1e-110">MRTK 內的大部分場景會利用 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。</span><span class="sxs-lookup"><span data-stu-id="41c1e-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="41c1e-111">最常見的使用案例可以在 MRTK/SDK/Features/UX/Prefabs/cursor/DefaultCursor 上找到。預製專案</span><span class="sxs-lookup"><span data-stu-id="41c1e-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="41c1e-112">進階使用方式</span><span class="sxs-lookup"><span data-stu-id="41c1e-112">Advanced Usage</span></span>

<span data-ttu-id="41c1e-113">根據預設，一次只有兩個 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 會將 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 亮亮。</span><span class="sxs-lookup"><span data-stu-id="41c1e-113">By default only two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="41c1e-114">如果您的專案需要兩個以上的專案 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 來影響 [材質](https://docs.unity3d.com/ScriptReference/Material.html) ，下列範例程式碼示範如何達成此目的。</span><span class="sxs-lookup"><span data-stu-id="41c1e-114">If your project requires more than two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="41c1e-115">有許多 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 亮亮的 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 將會增加圖元著色器的指示，而且會影響效能。</span><span class="sxs-lookup"><span data-stu-id="41c1e-115">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="41c1e-116">請在您的專案內分析這些變更。</span><span class="sxs-lookup"><span data-stu-id="41c1e-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="41c1e-117">*如何增加 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 從二到四的可用數目。*</span><span class="sxs-lookup"><span data-stu-id="41c1e-117">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from two to four.*</span></span>

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
> <span data-ttu-id="41c1e-118">如果 Unity 記錄類似下面的警告，您必須先重新開機 Unity，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="41c1e-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (8 vs 4). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="41c1e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41c1e-119">See also</span></span>

* [<span data-ttu-id="41c1e-120">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="41c1e-120">MRTK Standard Shader</span></span>](../README_MRTKStandardShader.md)
