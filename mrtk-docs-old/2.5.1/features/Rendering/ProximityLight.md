---
title: ProximityLight
description: 在 MRTK 中使用範例的相近淺色檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 9b29dc5f52180ae4251ab27455002cb18e3ea1f9
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684101"
---
# <a name="proximity-light"></a><span data-ttu-id="1ba76-104">近亮光</span><span class="sxs-lookup"><span data-stu-id="1ba76-104">Proximity Light</span></span>

<span data-ttu-id="1ba76-105">[`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)是一種[Fluent Design 系統](https://www.microsoft.com/design/fluent/)架構，它會在接近物件的介面上模擬「漸層反向點亮」。</span><span class="sxs-lookup"><span data-stu-id="1ba76-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="1ba76-106">通常用於近乎互動，應用程式可以透過元件控制近亮的屬性 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。</span><span class="sxs-lookup"><span data-stu-id="1ba76-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="1ba76-107">若要由 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *混合現實工具組/標準* 著色器所影響的材質，必須使用，且必須啟用 *鄰近性光線* 屬性。</span><span class="sxs-lookup"><span data-stu-id="1ba76-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="1ba76-108">預設支援最多兩個 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。</span><span class="sxs-lookup"><span data-stu-id="1ba76-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="1ba76-109">範例</span><span class="sxs-lookup"><span data-stu-id="1ba76-109">Examples</span></span>

<span data-ttu-id="1ba76-110">MRTK 內的大部分場景會利用 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。</span><span class="sxs-lookup"><span data-stu-id="1ba76-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="1ba76-111">最常見的使用案例可以在 MRTK/SDK/Features/UX/Prefabs/cursor/FingerCursor 上找到。預製專案</span><span class="sxs-lookup"><span data-stu-id="1ba76-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="1ba76-112">進階使用方式</span><span class="sxs-lookup"><span data-stu-id="1ba76-112">Advanced Usage</span></span>

<span data-ttu-id="1ba76-113">根據預設，一次只有兩個 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 會將 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 亮亮。</span><span class="sxs-lookup"><span data-stu-id="1ba76-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="1ba76-114">如果您的專案需要兩個以上的專案 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 來影響 [材質](https://docs.unity3d.com/ScriptReference/Material.html) ，下列範例程式碼示範如何達成此目的。</span><span class="sxs-lookup"><span data-stu-id="1ba76-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="1ba76-115">有許多 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 亮亮的 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 將會增加圖元著色器的指示，而且會影響效能。</span><span class="sxs-lookup"><span data-stu-id="1ba76-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="1ba76-116">請在您的專案內分析這些變更。</span><span class="sxs-lookup"><span data-stu-id="1ba76-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="1ba76-117">*如何增加 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 從二到四的可用數目。*</span><span class="sxs-lookup"><span data-stu-id="1ba76-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

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
> <span data-ttu-id="1ba76-118">如果 Unity 記錄類似下面的警告，您必須先重新開機 Unity，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="1ba76-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="1ba76-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ba76-119">See also</span></span>

* [<span data-ttu-id="1ba76-120">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="1ba76-120">MRTK Standard Shader</span></span>](MRTKStandardShader.md)
