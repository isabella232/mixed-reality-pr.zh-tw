---
title: JavaScript 開發總覽
description: 使用 JavaScript 進行 web、行動裝置和 windows 沉浸式耳機的混合現實開發總覽。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript、WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360影片、360影片、360相片、360相片、360內容、沉浸式網路、沉浸式 web、IW、immersiveweb
ms.openlocfilehash: 573db6f739292b7e67148d260a5ba1880d24fb20
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580319"
---
# <a name="javascript-development-overview"></a>JavaScript 開發概觀

## <a name="mixed-reality-applications-on-the-web"></a>Web 上的混合現實應用程式

混合的現實功能可透過使用 [WebXR 裝置 api](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) 和已 [淘汰的 WebVR api](webxr-overview.md)，在網站上取得。 如果瀏覽器不支援完整的 WebXR 功能，您可以將 [WebXR polyfill](https://github.com/immersive-web/webxr-polyfill) 加入至您的網站。

## <a name="what-is-webxr-polyfill"></a>什麼是 WebXR Polyfill

WebXR 裝置 API 的 JavaScript 執行，以及 WebXR 遊戲台模組。 此 polyfill 可讓開發人員根據最新的規格來撰寫，以在執行 WebVR 1.1 規格的瀏覽器上執行，或是在沒有 WebVR/WebXR 支援的行動裝置上執行時提供支援。

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>在 web 上建立混合現實應用程式的 JavaScript 程式庫

## <a name="babylonjs"></a>Babylon.js

Babylon 是 JavaScript 3D 引擎，可讓您輕鬆開發3D 內容和沉浸式應用程式。 開始使用沉浸式應用程式之前，建議您先瞭解 Babylon.js 開發的基本概念。

在 [開始使用] [區段](https://doc.babylonjs.com/)中，瞭解如何使用 Babylon 建立混合現實應用程式。 使用 [Babylon 遊樂場](https://doc.babylonjs.com/examples/)來播放3d 範例和其原始程式碼。 在檔的 [WebXR 一節](https://doc.babylonjs.com/how_to/introduction_to_webxr) 中深入瞭解混合現實開發。 

## <a name="a-frame"></a>A 框架

框架是一種宣告式的 JavaScript 架構，可讓您在網路中開始使用虛擬事實。 若要深入瞭解，請參閱 [框架檔](https://aframe.io/) 。

## <a name="threejs"></a>Three.js

Three.js 是一種熱門的3D 程式庫，可讓您建立沉浸式體驗。 深入瞭解檔頁面中的 [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) ，以及探索 [範例](https://threejs.org/examples/#webgl_animation_cloth)。

## <a name="webgl"></a>WebGL

您可以使用 WebGL Api 直接存取 WebXR 裝置 Api。 WebGL (Web 圖形程式庫) 是一種 JavaScript API，可在任何相容的網頁瀏覽器內轉譯高效能的互動式3D 和2D 圖形，而不需要使用外掛程式。深入瞭解 [WebGL api](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)。

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>使用 JavaScript 的混合現實原生行動應用程式

透過少數 JavaScript 程式庫的協助，您可以撰寫混合現實體驗一次，並將其部署至 web 和原生平臺，例如 Windows Mixed Reality 耳機、Android 和 iOS 裝置。

## <a name="babylon-native"></a>Babylon 原生

[Babylon native](https://www.babylonjs.com/native/) platform 可讓任何人取得其 Babylon.js 程式碼，並使用它來建立原生應用程式，以充分發揮原生技術的威力。 您可以在 [github 上下載 Babylon native](https://github.com/BabylonJS/BabylonNative) ，並在Babylon.js 的 [ blog](https://medium.com/@babylonjs/babylon-native-821f1694fffc)上閱讀更多相關資訊。

## <a name="react-native"></a>React Native

[React Native](https://reactnative.dev/) 是另一個開放原始碼程式庫，可讓開發人員使用 JavaScript 建立並部署到多個平臺。 您可以下載 [Github 上的 React Native](https://github.com/facebook/react-native) ，並在 React Native 的 [Blog](https://reactnative.dev/blog/)中深入瞭解。

## <a name="see-also"></a>另請參閱

* [WebXR 總覽](webxr-overview.md)
* [WebXR 裝置 API 規格](https://immersive-web.github.io/webxr/)
* [WebXR 裝置 API 檔](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb dev](https://immersiveweb.dev/)
* [WebXR 範例](https://immersive-web.github.io/webxr-samples/)
* [使用 Babylon.js 建立 WebXR 體驗](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality 和新的 Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [沉浸式 Web W3C Github](https://github.com/immersive-web)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能
* [WebVR 總覽](webvr-overview.md)