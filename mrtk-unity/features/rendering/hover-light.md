---
title: HoverLight
description: MRTK 中的 HoverLight 範例檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、停留燈、
ms.openlocfilehash: 60662245111abe39285b3b8ac2cfb9d71e1300ed
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702284"
---
# <a name="hover-light"></a><span data-ttu-id="0a1fb-104">停留燈</span><span class="sxs-lookup"><span data-stu-id="0a1fb-104">Hover Light</span></span>

<span data-ttu-id="0a1fb-105">[`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)是一種[Fluent Design 系統](https://www.microsoft.com/design/fluent/)範例，會模擬停留在物件介面附近的[點光線](https://docs.unity3d.com/Manual/Lighting.html)。</span><span class="sxs-lookup"><span data-stu-id="0a1fb-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="0a1fb-106">通常用於遠離互動，應用程式可以透過元件來控制停留光的屬性 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。</span><span class="sxs-lookup"><span data-stu-id="0a1fb-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="0a1fb-107">您 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 必須使用「 *混合現實工具* 組」/「標準著色器」所影響的材質，而且必須啟用「暫止 *燈* 」屬性。</span><span class="sxs-lookup"><span data-stu-id="0a1fb-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="0a1fb-108">MRTK/Standard 著色器預設支援最多兩個 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) ，但將會調整為支援四個，然後在場景中新增更多燈光時調整為10。</span><span class="sxs-lookup"><span data-stu-id="0a1fb-108">The MRTK/Standard shader supports up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) by default, but will scale to support four and then ten as more lights are added to the scene.</span></span>

## <a name="examples"></a><span data-ttu-id="0a1fb-109">範例</span><span class="sxs-lookup"><span data-stu-id="0a1fb-109">Examples</span></span>

<span data-ttu-id="0a1fb-110">MRTK 內的大部分場景會利用 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。</span><span class="sxs-lookup"><span data-stu-id="0a1fb-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="0a1fb-111">最常見的使用案例可以在 MRTK/SDK/Features/UX/Prefabs/cursor/DefaultCursor 上找到。預製專案</span><span class="sxs-lookup"><span data-stu-id="0a1fb-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

<span data-ttu-id="0a1fb-112">**HoverLightExamples** 場景也會示範行為的用法 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) ，您可以在下列位置找到： MRTK/範例/示範/StandardShader/場景/</span><span class="sxs-lookup"><span data-stu-id="0a1fb-112">The **HoverLightExamples** scene also demonstrates usage of [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="0a1fb-113">進階使用方式</span><span class="sxs-lookup"><span data-stu-id="0a1fb-113">Advanced Usage</span></span>

<span data-ttu-id="0a1fb-114">[`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight)一次只能對一個[材質](https://docs.unity3d.com/ScriptReference/Material.html)進行一次亮妥。</span><span class="sxs-lookup"><span data-stu-id="0a1fb-114">Only ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="0a1fb-115">如果您的專案需要十個以上的資料 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 來影響 [材質](https://docs.unity3d.com/ScriptReference/Material.html) ，下列範例程式碼示範如何達成此目的。</span><span class="sxs-lookup"><span data-stu-id="0a1fb-115">If your project requires more than ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="0a1fb-116">有許多 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 亮亮的 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 將會增加圖元著色器的指示，而且會影響效能。</span><span class="sxs-lookup"><span data-stu-id="0a1fb-116">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="0a1fb-117">**請在您的專案內分析這些變更。**</span><span class="sxs-lookup"><span data-stu-id="0a1fb-117">**Please profile these changes within your project.**</span></span>

<span data-ttu-id="0a1fb-118">*如何將可用的數目增加 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 至12個。*</span><span class="sxs-lookup"><span data-stu-id="0a1fb-118">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from ten to twelve.*</span></span>

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
> <span data-ttu-id="0a1fb-119">如果 Unity 記錄類似下面的警告，您必須先重新開機 Unity，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="0a1fb-119">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="0a1fb-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a1fb-120">See also</span></span>

* [<span data-ttu-id="0a1fb-121">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="0a1fb-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
