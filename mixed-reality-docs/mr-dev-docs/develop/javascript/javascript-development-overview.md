---
title: JavaScript 開發總覽
description: 使用 JavaScript 進行 web、行動裝置和 windows 沉浸式耳機的混合現實開發總覽。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript、WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360影片、360影片、360相片、360相片、360內容、沉浸式網路、沉浸式 web、IW、immersiveweb
ms.openlocfilehash: 311241d9dec6f5d086a45766c040b1b2b9eb4128
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394342"
---
# <a name="javascript-development-overview"></a>JavaScript 開發概觀

JavaScript 是世界上最受歡迎的程式設計語言之一！ 它在網路上很簡單、輕量且廣泛使用。 利用 JavaScript 和 web 技能的強大功能，創造更吸引人的混合現實體驗。

## <a name="mixed-reality-applications-on-the-web"></a>Web 上的混合現實應用程式

混合的現實功能可透過使用 [WebXR](webxr-overview.md)在網站上取得。 您可以在不安裝任何其他軟體或外掛程式的情況下，于相容 WebXR 的瀏覽器中看到虛擬實境 (VR) 和增強的現實 (AR) 內容。 您可以使用相同的瀏覽器與實體裝置（例如 HoloLens 2）。 如需詳細資料，請參閱我們的 [WebXR](webxr-overview.md) 檔。

> [!NOTE]
> **WebVR** 已被取代，無法在目前的瀏覽器中使用，因此不應該用於任何新的開發。 您必須將任何現有的 **WebVR** 執行移至 **WebXR**。

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>我可以使用哪些功能來開發沉浸式 web 體驗？

下列清單顯示的 JavaScript 架構和 Api，可用於建立目前市場上的沉浸式體驗，並受到混合現實 JavaScript 開發人員的廣泛接受和採用：

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon 是 JavaScript 3D 引擎，可讓您輕鬆開發3D 內容和沉浸式應用程式。 開始使用沉浸式應用程式之前，建議您先瞭解 Babylon.js 開發的基本概念。<br/><br/>-瞭解如何使用 babylon.js [入門](https://doc.babylonjs.com/start)來建立3d 應用程式。<br/>-使用 babylon.js[遊樂場](https://doc.babylonjs.com/examples/)來播放3d 範例和其原始程式碼<br/>-深入探索 [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>-瞭解如何開始使用我們的教學課程， [建立您的第一個「Hello World！」應用程式](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![BabylonJS 標誌](images/babylon.js.example.png) |
|[**A 框架**](https://aframe.io/) <br/><br/>框架是一種宣告式的 JavaScript 架構，可讓您在網路中開始使用虛擬事實。 若要深入瞭解，請參閱 [框架檔](https://aframe.io/docs/1.2.0/introduction/) 。 |![A 框架](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js 是一種熱門的3D 程式庫，可讓您建立沉浸式體驗。 深入瞭解檔頁面中的 [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) ，以及探索 [範例](https://threejs.org/examples/#webgl_animation_cloth)。 |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>您可以使用 WebGL Api 直接存取 WebXR 裝置 Api。 WebGL (Web 圖形程式庫) 是一種 JavaScript API，可在任何相容的網頁瀏覽器內轉譯高效能的互動式3D 和2D 圖形，而不需要使用外掛程式。 |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>後續步驟

深入瞭解如何開始使用我們的教學課程。

> [!div class="nextstepaction"]
> [建立您的第一個 "Hello World！" 應用程式](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>另請參閱

* [WebXR 總覽](webxr-overview.md)
* [WebXR 裝置 API 規格](https://immersive-web.github.io/webxr/)
* [WebXR 裝置 API 檔](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [WebXR 範例](https://immersive-web.github.io/webxr-samples/)
* [使用 Babylon.js 建立 WebXR 體驗](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality 和新的 Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [沉浸式 Web W3C Github](https://github.com/immersive-web)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能
