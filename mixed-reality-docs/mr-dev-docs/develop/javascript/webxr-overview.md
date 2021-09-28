---
title: 使用 WebXR 搭配 Windows Mixed Reality
description: 瞭解針對 Windows Mixed Reality 沉浸式耳機上執行的 WebXR 應用程式，使用和開發的基本概念。
author: yonet
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360影片、360影片、360相片、360相片、360內容、沉浸式 web、immersiveweb、IW
ms.openlocfilehash: b0ab1eab5f1c3e546dde367c2cdb992fba7b452d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148693"
---
# <a name="javascript-development-with-webxr"></a>使用 WebXR 進行 JavaScript 開發

JavaScript 是世界上最受歡迎的程式設計語言之一！ 它在網路上很簡單、輕量且廣泛使用。 利用 JavaScript 和 Web 技能的強大功能，創造更吸引人的混合現實體驗。

## <a name="mixed-reality-applications-on-the-web"></a>Web 上的混合現實應用程式

混合的現實功能可透過 [WebXR](webxr-overview.md)在網站上取得。 您可以在不安裝任何其他軟體或外掛程式的情況下，于相容 WebXR 的瀏覽器中看到虛擬實境 (VR) 和增強的現實 (AR) 內容。 您可以使用相同的瀏覽器與實體裝置（例如 HoloLens 2）。

[**WebXR 裝置**](https://www.w3.org/TR/webxr/)應用程式開發介面是用來存取虛擬實境 (VR) 和增強現實 (AR) 裝置（包括感應器和前端掛接的顯示器）在網路上。 WebXR 裝置 API 適用于 Microsoft Edge 和 Chrome 79 版，而較新版本則支援 WebXR 作為預設值。 您可以在 [caniuse.com](https://caniuse.com/#search=webxr)上檢查 WebXR 的最新瀏覽器支援狀態。

> [!NOTE]
> **WebVR** 已被取代，無法在目前的瀏覽器中使用，因此不應該用於任何新的開發。 您必須將任何現有的 **WebVR** 執行遷移至 **WebXR**。

| WebXR 功能 | 可用性 |
|---------|---------|
|[WebXR 裝置 API (w3.org) ](https://www.w3.org/TR/webxr/) | Windows 桌面上的 Edge 81 <br>Hololens 2 上的 Edge 91|
|[WebXR 增強的現實課程模組-層級 1 (w3.org) ](https://www.w3.org/TR/webxr-ar-module-1/)|Edge 91。 僅限 Hololens 2|
|[WebXR 手輸入模組-層級 1 (w3.org) ](https://www.w3.org/TR/webxr-hand-input-1/)|Edge 93。 僅限 Hololens 2|
|[WebXR 錨點模組 (immersive-web.github.io) ](https://immersive-web.github.io/anchors/)|Edge 93。 僅限 Hololens 2|
|[WebXR 點擊測試模組 (immersive-web.github.io) ](https://immersive-web.github.io/hit-test/)|Edge 93。 僅限 Hololens 2 |

### <a name="viewing-webxr"></a>觀看 WebXR

您可以使用[新的 Microsoft Edge](../../whats-new/new-microsoft-edge.md)和[Firefox 的實際](https://mixedreality.mozilla.org/firefox-reality/)瀏覽器來觀看 Windows Mixed Reality 中的 WebXR 體驗。
若要測試您的瀏覽器是否支援 WebXR，您可以在瀏覽器中流覽至 [WebXR 範例](https://immersive-web.github.io/webxr-samples/) 。

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>我可以使用哪些功能來開發沉浸式 Web 體驗？

下列清單顯示的 JavaScript 架構和 Api，可用於建立目前市場上的沉浸式體驗，並受到混合現實 JavaScript 開發人員的廣泛接受和採用：

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon 是 JavaScript 3D 引擎，可讓您輕鬆開發3D 內容和沉浸式應用程式。 開始使用沉浸式應用程式之前，建議您先瞭解 Babylon.js 開發的基本概念。<br/><br/>-瞭解如何使用 babylon.js 建立3D 應用程式： [快速入門](https://doc.babylonjs.com/start)<br/>-使用 babylon.js：[遊樂場](https://doc.babylonjs.com/examples/)來播放3d 範例和其原始程式碼<br/>-深入探索 [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>-瞭解如何開始使用我們的教學課程： [建立您的第一個 "Hello World！" 應用程式](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![BabylonJS 標誌](images/babylon.js.example.png) |
|[**A 框架**](https://aframe.io/) <br/><br/>框架是一種宣告式的 JavaScript 架構，可讓您在 Web 上開始使用虛擬實境。 若要深入瞭解，請參閱 [框架檔](https://aframe.io/docs/1.2.0/introduction/) |![A 框架](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js 是一種熱門的3D 程式庫，可讓您建立沉浸式體驗。 深入瞭解 [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) 及 [探索範例](https://threejs.org/examples/#webgl_animation_cloth)。 |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>您可以使用 WebGL Api 直接存取 WebXR 裝置 Api。 WebGL (Web 圖形程式庫) 是一種 JavaScript API，可在任何相容的網頁瀏覽器內轉譯高效能的互動式3D 和2D 圖形，而不需要使用外掛程式。 |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>另請參閱

* [WebXR 裝置 API 規格](https://immersive-web.github.io/webxr/)
* [WebXR 裝置 API 檔](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [WebXR 範例](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [使用 Babylon.js 建立 WebXR 體驗](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能
* [Windows Mixed Reality 和新的 Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [處理 WebGL 中遺失的內容](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [沉浸式 web 社區群組](https://www.w3.org/community/immersive-web/)
* [沉浸式 Web W3C Github](https://github.com/immersive-web)

## <a name="next-steps--tutorials"></a>後續步驟--教學課程

> [!div class="nextstepaction"]
> [使用 Babylon.js建立您的第一個 WebXR 應用程式 ](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

> [!div class="nextstepaction"]
> [使用 Babylon.js在 WebXR 中建立鋼琴 ](tutorials/babylonjs-webxr-piano/introduction-01.md)
