---
title: OpenXR 效能
description: 瞭解如何針對 OpenXR mixed reality 應用程式的 GPU 效能進行偵錯工具。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體、效能、優化、GPU 偵錯工具、RenderDoc、PIX
ms.openlocfilehash: 158bd2eef8f38f16a1fb5299d64335aca33a3b7f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006758"
---
# <a name="openxr-performance"></a><span data-ttu-id="6b0c5-104">OpenXR 效能</span><span class="sxs-lookup"><span data-stu-id="6b0c5-104">OpenXR performance</span></span>

<span data-ttu-id="6b0c5-105">在 HoloLens 2 上，有數種方式可透過提交撰寫資料 `xrEndFrame` ，而這可能會導致後續處理和顯著的效能受到影響。</span><span class="sxs-lookup"><span data-stu-id="6b0c5-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>

<span data-ttu-id="6b0c5-106">若要避免效能不佳，請使用下列特性[提交單一 `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer) ：</span><span class="sxs-lookup"><span data-stu-id="6b0c5-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>

* [<span data-ttu-id="6b0c5-107">使用紋理陣列 swapchain</span><span class="sxs-lookup"><span data-stu-id="6b0c5-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="6b0c5-108">使用主要色彩 swapchain 格式</span><span class="sxs-lookup"><span data-stu-id="6b0c5-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="6b0c5-109">使用建議的視圖維度</span><span class="sxs-lookup"><span data-stu-id="6b0c5-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="6b0c5-110">不要設定 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 旗標</span><span class="sxs-lookup"><span data-stu-id="6b0c5-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="6b0c5-111">將設 `XrCompositionLayerDepthInfoKHR` `minDepth` 為 0.0 f 和 `maxDepth` 1.0 f</span><span class="sxs-lookup"><span data-stu-id="6b0c5-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="6b0c5-112">為了獲得更好的效能，請考慮：</span><span class="sxs-lookup"><span data-stu-id="6b0c5-112">For better performance, consider:</span></span>

* [<span data-ttu-id="6b0c5-113">使用16位深度格式</span><span class="sxs-lookup"><span data-stu-id="6b0c5-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="6b0c5-114">進行實例繪製呼叫</span><span class="sxs-lookup"><span data-stu-id="6b0c5-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
