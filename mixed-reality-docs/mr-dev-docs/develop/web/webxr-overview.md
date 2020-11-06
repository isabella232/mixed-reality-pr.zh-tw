---
title: 使用 WebXR 搭配 Windows Mixed Reality
description: 在 Windows Mixed Reality 中使用和開發 WebXR 的總覽
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360影片、360影片、360相片、360相片、360內容、沉浸式 web、immersiveweb、IW
ms.openlocfilehash: b72d4968e59e3e631138b1ecfd17ca9bbdd95c84
ms.sourcegitcommit: 8fd127aff85b77778bd7a75c5ec5215d27ecf21a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "93416869"
---
# <a name="webxr-overview"></a>WebXR 總覽

## <a name="what-is-webxr"></a>什麼是 WebXR

**WebXR 裝置 API** 適用于存取 **虛擬實境 (VR)** 和增強的 **現實 (AR)** 裝置，包括 **感應器** 和 **網路** 上的 **前端裝載顯示器** 。 WebXR 裝置 API 目前適用于 Microsoft Edge，且 Chrome 79 版和更新版本支援以 WebXR 作為預設值。 您可以在 [caniuse.com](https://caniuse.com/#search=webxr)上檢查 WebXR 的最新瀏覽器支援狀態。

在[新功能](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide)一節中深入瞭解[Windows Mixed Reality 以及新的 Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)。

## <a name="viewing-webxr"></a>觀看 WebXR

> [!IMPORTANT]
> Microsoft Edge (舊版) 只支援 WebVR，也就是目前的瀏覽器中未提供的已淘汰 API。 不過，新的 **[Chromium 為基礎的 Edge 瀏覽器](../../whats-new/new-microsoft-edge.md)** 支援 WebXR，並且可用於 Windows Mixed Reality 中的 VR 原型設計。 新的 Chromium Edge 瀏覽器中將無法使用 WebVR。
> 
> 如果您想要在今天 HoloLens 2 建立原型 WebXR 的方法，請查看 [Firefox 的實際](https://mixedreality.mozilla.org/firefox-reality/)情況。

若要測試您的瀏覽器是否支援 WebXR，您可以在瀏覽器中流覽至 [WebXR 範例](https://immersive-web.github.io/webxr-samples/) 。

## <a name="see-also"></a>另請參閱

* [WebXR 裝置 API 規格](https://immersive-web.github.io/webxr/)
* [WebXR 裝置 API 檔](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb dev](https://immersiveweb.dev/)
* [WebXR 範例](https://immersive-web.github.io/webxr-samples/)
* [Windows Mixed Reality 和新的 Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [沉浸式 Web W3C Github](https://github.com/immersive-web)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能
* [處理 WebGL 中遺失的內容](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [使用 Babylon.js 建立 WebXR 體驗](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [沉浸式 web 社區群組](https://www.w3.org/community/immersive-web/)
