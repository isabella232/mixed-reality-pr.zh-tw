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
# <a name="openxr-performance"></a>OpenXR 效能

在 HoloLens 2 上，有數種方式可透過提交撰寫資料 `xrEndFrame` ，而這可能會導致後續處理和顯著的效能受到影響。
若要避免效能不佳，請使用下列特性[提交單一 `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer) ：
* [使用紋理陣列 swapchain](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [使用主要色彩 swapchain 格式](openxr-best-practices.md#select-a-swapchain-format)
* [使用建議的視圖維度](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* 不要設定 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 旗標
* 將設 `XrCompositionLayerDepthInfoKHR` `minDepth` 為 0.0 f 和 `maxDepth` 1.0 f

為了獲得更好的效能，請考慮：
* [使用16位深度格式](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [進行實例繪製呼叫](openxr-best-practices.md#render-with-texture-array-and-vprt)
