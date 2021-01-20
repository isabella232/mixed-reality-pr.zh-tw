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
# <a name="javascript-development-overview"></a><span data-ttu-id="ea55a-104">JavaScript 開發概觀</span><span class="sxs-lookup"><span data-stu-id="ea55a-104">JavaScript development overview</span></span>

## <a name="mixed-reality-applications-on-the-web"></a><span data-ttu-id="ea55a-105">Web 上的混合現實應用程式</span><span class="sxs-lookup"><span data-stu-id="ea55a-105">Mixed Reality applications on the web</span></span>

<span data-ttu-id="ea55a-106">混合的現實功能可透過使用 [WebXR 裝置 api](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) 和已 [淘汰的 WebVR api](webxr-overview.md)，在網站上取得。</span><span class="sxs-lookup"><span data-stu-id="ea55a-106">Mixed Reality features are available on the web by the use of [WebXR Device APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) and [deprecated WebVR APIs](webxr-overview.md).</span></span> <span data-ttu-id="ea55a-107">如果瀏覽器不支援完整的 WebXR 功能，您可以將 [WebXR polyfill](https://github.com/immersive-web/webxr-polyfill) 加入至您的網站。</span><span class="sxs-lookup"><span data-stu-id="ea55a-107">For browsers that do not support full WebXR features, you can add [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill) to your website.</span></span>

## <a name="what-is-webxr-polyfill"></a><span data-ttu-id="ea55a-108">什麼是 WebXR Polyfill</span><span class="sxs-lookup"><span data-stu-id="ea55a-108">What is WebXR Polyfill</span></span>

<span data-ttu-id="ea55a-109">WebXR 裝置 API 的 JavaScript 執行，以及 WebXR 遊戲台模組。</span><span class="sxs-lookup"><span data-stu-id="ea55a-109">A JavaScript implementation of the WebXR Device API, as well as the WebXR Gamepad Module.</span></span> <span data-ttu-id="ea55a-110">此 polyfill 可讓開發人員根據最新的規格來撰寫，以在執行 WebVR 1.1 規格的瀏覽器上執行，或是在沒有 WebVR/WebXR 支援的行動裝置上執行時提供支援。</span><span class="sxs-lookup"><span data-stu-id="ea55a-110">This polyfill allows developers to write against the latest specification, providing support when run on browsers that implement the WebVR 1.1 spec, or on mobile devices with no WebVR/WebXR support at all.</span></span>

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a><span data-ttu-id="ea55a-111">在 web 上建立混合現實應用程式的 JavaScript 程式庫</span><span class="sxs-lookup"><span data-stu-id="ea55a-111">JavaScript libraries to build Mixed Reality applications on the web</span></span>

## <a name="babylonjs"></a><span data-ttu-id="ea55a-112">Babylon.js</span><span class="sxs-lookup"><span data-stu-id="ea55a-112">Babylon.js</span></span>

<span data-ttu-id="ea55a-113">Babylon 是 JavaScript 3D 引擎，可讓您輕鬆開發3D 內容和沉浸式應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea55a-113">Babylon is a JavaScript 3D engine that makes developing 3D content and immersive applications easy.</span></span> <span data-ttu-id="ea55a-114">開始使用沉浸式應用程式之前，建議您先瞭解 Babylon.js 開發的基本概念。</span><span class="sxs-lookup"><span data-stu-id="ea55a-114">Before getting started with immersive applications, we recommend to learn the basics of Babylon.js development.</span></span>

<span data-ttu-id="ea55a-115">在 [開始使用] [區段](https://doc.babylonjs.com/)中，瞭解如何使用 Babylon 建立混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea55a-115">Learn how to build a mixed reality application with Babylon in the [getting started section](https://doc.babylonjs.com/).</span></span> <span data-ttu-id="ea55a-116">使用 [Babylon 遊樂場](https://doc.babylonjs.com/examples/)來播放3d 範例和其原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea55a-116">Play with 3D examples and their source code using [Babylon Playground](https://doc.babylonjs.com/examples/).</span></span> <span data-ttu-id="ea55a-117">在檔的 [WebXR 一節](https://doc.babylonjs.com/how_to/introduction_to_webxr) 中深入瞭解混合現實開發。</span><span class="sxs-lookup"><span data-stu-id="ea55a-117">Dive into mixed reality development on the [WebXR section](https://doc.babylonjs.com/how_to/introduction_to_webxr) of the documentation.</span></span> 

## <a name="a-frame"></a><span data-ttu-id="ea55a-118">A 框架</span><span class="sxs-lookup"><span data-stu-id="ea55a-118">A-Frame</span></span>

<span data-ttu-id="ea55a-119">框架是一種宣告式的 JavaScript 架構，可讓您在網路中開始使用虛擬事實。</span><span class="sxs-lookup"><span data-stu-id="ea55a-119">A-frame is a declarative JavaScript framework to get started with Virtual Reality in the web.</span></span> <span data-ttu-id="ea55a-120">若要深入瞭解，請參閱 [框架檔](https://aframe.io/) 。</span><span class="sxs-lookup"><span data-stu-id="ea55a-120">Check out the [A-Frame documentation](https://aframe.io/) to learn more.</span></span>

## <a name="threejs"></a><span data-ttu-id="ea55a-121">Three.js</span><span class="sxs-lookup"><span data-stu-id="ea55a-121">Three.js</span></span>

<span data-ttu-id="ea55a-122">Three.js 是一種熱門的3D 程式庫，可讓您建立沉浸式體驗。</span><span class="sxs-lookup"><span data-stu-id="ea55a-122">Three.js is a popular 3D library for creating immersive experiences.</span></span> <span data-ttu-id="ea55a-123">深入瞭解檔頁面中的 [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) ，以及探索 [範例](https://threejs.org/examples/#webgl_animation_cloth)。</span><span class="sxs-lookup"><span data-stu-id="ea55a-123">Learn more about [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) in documentation page and by exploring [examples](https://threejs.org/examples/#webgl_animation_cloth).</span></span>

## <a name="webgl"></a><span data-ttu-id="ea55a-124">WebGL</span><span class="sxs-lookup"><span data-stu-id="ea55a-124">WebGL</span></span>

<span data-ttu-id="ea55a-125">您可以使用 WebGL Api 直接存取 WebXR 裝置 Api。</span><span class="sxs-lookup"><span data-stu-id="ea55a-125">You can access the WebXR Device APIs directly by using WebGL APIs.</span></span> <span data-ttu-id="ea55a-126">WebGL (Web 圖形程式庫) 是一種 JavaScript API，可在任何相容的網頁瀏覽器內轉譯高效能的互動式3D 和2D 圖形，而不需要使用外掛程式。深入瞭解 [WebGL api](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)。</span><span class="sxs-lookup"><span data-stu-id="ea55a-126">WebGL (Web Graphics Library) is a JavaScript API for rendering high-performance interactive 3D and 2D graphics within any compatible web browser without the use of plug-ins. Learn more about the [WebGL APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).</span></span>

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a><span data-ttu-id="ea55a-127">使用 JavaScript 的混合現實原生行動應用程式</span><span class="sxs-lookup"><span data-stu-id="ea55a-127">Mixed Reality native mobile applications using JavaScript</span></span>

<span data-ttu-id="ea55a-128">透過少數 JavaScript 程式庫的協助，您可以撰寫混合現實體驗一次，並將其部署至 web 和原生平臺，例如 Windows Mixed Reality 耳機、Android 和 iOS 裝置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-128">With the help of few JavaScript libraries you can write your mixed reality experiences once and deploy it to web and to native platforms like Windows Mixed Reality headsets, Android and iOS devices.</span></span>

## <a name="babylon-native"></a><span data-ttu-id="ea55a-129">Babylon 原生</span><span class="sxs-lookup"><span data-stu-id="ea55a-129">Babylon Native</span></span>

<span data-ttu-id="ea55a-130">[Babylon native](https://www.babylonjs.com/native/) platform 可讓任何人取得其 Babylon.js 程式碼，並使用它來建立原生應用程式，以充分發揮原生技術的威力。</span><span class="sxs-lookup"><span data-stu-id="ea55a-130">[Babylon Native](https://www.babylonjs.com/native/) platform allows anyone to take their Babylon.js code and build a native application with it, unlocking the power of native technologies.</span></span> <span data-ttu-id="ea55a-131">您可以在 [github 上下載 Babylon native](https://github.com/BabylonJS/BabylonNative) ，並在Babylon.js 的 [ blog](https://medium.com/@babylonjs/babylon-native-821f1694fffc)上閱讀更多相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ea55a-131">You can download [Babylon native on github](https://github.com/BabylonJS/BabylonNative) and read more about it on [Babylon.js blog](https://medium.com/@babylonjs/babylon-native-821f1694fffc).</span></span>

## <a name="react-native"></a><span data-ttu-id="ea55a-132">React Native</span><span class="sxs-lookup"><span data-stu-id="ea55a-132">React Native</span></span>

<span data-ttu-id="ea55a-133">[React Native](https://reactnative.dev/) 是另一個開放原始碼程式庫，可讓開發人員使用 JavaScript 建立並部署到多個平臺。</span><span class="sxs-lookup"><span data-stu-id="ea55a-133">[React Native](https://reactnative.dev/) is another open source library that allows developers to build using JavaScript and deploy to multiple platforms.</span></span> <span data-ttu-id="ea55a-134">您可以下載 [Github 上的 React Native](https://github.com/facebook/react-native) ，並在 React Native 的 [Blog](https://reactnative.dev/blog/)中深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="ea55a-134">You can download [React Native on Github](https://github.com/facebook/react-native) and learn more about it in [React Native Blog](https://reactnative.dev/blog/).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea55a-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea55a-135">See Also</span></span>

* [<span data-ttu-id="ea55a-136">WebXR 總覽</span><span class="sxs-lookup"><span data-stu-id="ea55a-136">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="ea55a-137">WebXR 裝置 API 規格</span><span class="sxs-lookup"><span data-stu-id="ea55a-137">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="ea55a-138">WebXR 裝置 API 檔</span><span class="sxs-lookup"><span data-stu-id="ea55a-138">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="ea55a-139">Immersiveweb dev</span><span class="sxs-lookup"><span data-stu-id="ea55a-139">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="ea55a-140">WebXR 範例</span><span class="sxs-lookup"><span data-stu-id="ea55a-140">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="ea55a-141">使用 Babylon.js 建立 WebXR 體驗</span><span class="sxs-lookup"><span data-stu-id="ea55a-141">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="ea55a-142">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ea55a-142">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="ea55a-143">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="ea55a-143">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="ea55a-144">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ea55a-144">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="ea55a-145">[遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能</span><span class="sxs-lookup"><span data-stu-id="ea55a-145">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="ea55a-146">WebVR 總覽</span><span class="sxs-lookup"><span data-stu-id="ea55a-146">WebVR Overview</span></span>](webvr-overview.md)