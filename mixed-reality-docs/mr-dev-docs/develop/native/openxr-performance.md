---
title: OpenXR 效能
description: 將 OpenXR 應用程式的 GPU 效能進行偵錯工具。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體、效能、優化、GPU 偵錯工具、RenderDoc、PIX
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613172"
---
# <a name="openxr-performance"></a><span data-ttu-id="42026-104">OpenXR 效能</span><span class="sxs-lookup"><span data-stu-id="42026-104">OpenXR performance</span></span>

<span data-ttu-id="42026-105">在 HoloLens 2 上，有數種方式可透過提交撰寫資料 `xrEndFrame` ，而這可能會導致後續處理和顯著的效能受到影響。</span><span class="sxs-lookup"><span data-stu-id="42026-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>
<span data-ttu-id="42026-106">若要避免效能不佳，請使用下列特性[提交單一 `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer) ：</span><span class="sxs-lookup"><span data-stu-id="42026-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="42026-107">使用紋理陣列 swapchain</span><span class="sxs-lookup"><span data-stu-id="42026-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="42026-108">使用主要色彩 swapchain 格式</span><span class="sxs-lookup"><span data-stu-id="42026-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="42026-109">使用建議的視圖維度</span><span class="sxs-lookup"><span data-stu-id="42026-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="42026-110">不要設定 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 旗標</span><span class="sxs-lookup"><span data-stu-id="42026-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="42026-111">將設 `XrCompositionLayerDepthInfoKHR` `minDepth` 為 0.0 f 和 `maxDepth` 1.0 f</span><span class="sxs-lookup"><span data-stu-id="42026-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="42026-112">為了獲得更好的效能，請考慮：</span><span class="sxs-lookup"><span data-stu-id="42026-112">For better performance, consider:</span></span>
* [<span data-ttu-id="42026-113">使用16位深度格式</span><span class="sxs-lookup"><span data-stu-id="42026-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="42026-114">進行實例繪製呼叫</span><span class="sxs-lookup"><span data-stu-id="42026-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
