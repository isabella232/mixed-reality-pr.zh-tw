---
title: OpenXR 效能
description: 將 OpenXR 應用程式的 GPU 效能進行偵錯工具。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體、效能、優化、GPU 偵錯工具、RenderDoc、PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679336"
---
# <a name="openxr-performance"></a><span data-ttu-id="7ccb5-104">OpenXR 效能</span><span class="sxs-lookup"><span data-stu-id="7ccb5-104">OpenXR performance</span></span>

<span data-ttu-id="7ccb5-105">在 HoloLens 2 上，有許多方法可以提交組合資料， `xrEndFrame` 而這會導致在處理後，將會對效能造成顯著的影響。</span><span class="sxs-lookup"><span data-stu-id="7ccb5-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>
<span data-ttu-id="7ccb5-106">若要避免效能 penalities，請使用下列特性[提交單一 `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer) ：</span><span class="sxs-lookup"><span data-stu-id="7ccb5-106">To avoid performance penalities, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="7ccb5-107">使用紋理陣列 swapchain</span><span class="sxs-lookup"><span data-stu-id="7ccb5-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="7ccb5-108">使用主要色彩 swapchain 格式</span><span class="sxs-lookup"><span data-stu-id="7ccb5-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="7ccb5-109">使用建議的視圖維度</span><span class="sxs-lookup"><span data-stu-id="7ccb5-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="7ccb5-110">請勿設定旗標 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`</span><span class="sxs-lookup"><span data-stu-id="7ccb5-110">Do not set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="7ccb5-111">將設 `XrCompositionLayerDepthInfoKHR` `minDepth` 為 0.0 f 和 `maxDepth` 1.0 f</span><span class="sxs-lookup"><span data-stu-id="7ccb5-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="7ccb5-112">其他考慮將會產生較佳的效能：</span><span class="sxs-lookup"><span data-stu-id="7ccb5-112">Additional considerations will result in better performance:</span></span>
* [<span data-ttu-id="7ccb5-113">使用16位深度格式</span><span class="sxs-lookup"><span data-stu-id="7ccb5-113">Use the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="7ccb5-114">進行實例繪製呼叫</span><span class="sxs-lookup"><span data-stu-id="7ccb5-114">Make instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
