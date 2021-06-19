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
# <a name="javascript-development-overview"></a><span data-ttu-id="a4be9-104">JavaScript 開發概觀</span><span class="sxs-lookup"><span data-stu-id="a4be9-104">JavaScript development overview</span></span>

<span data-ttu-id="a4be9-105">JavaScript 是世界上最受歡迎的程式設計語言之一！</span><span class="sxs-lookup"><span data-stu-id="a4be9-105">JavaScript is one of the most popular programming languages in the world!</span></span> <span data-ttu-id="a4be9-106">它在網路上很簡單、輕量且廣泛使用。</span><span class="sxs-lookup"><span data-stu-id="a4be9-106">It's simple, lightweight, and widely used on the web.</span></span> <span data-ttu-id="a4be9-107">利用 JavaScript 和 web 技能的強大功能，創造更吸引人的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="a4be9-107">Leverage the power of your JavaScript and web skills to create more engaging Mixed Reality experiences.</span></span>

## <a name="mixed-reality-applications-on-the-web"></a><span data-ttu-id="a4be9-108">Web 上的混合現實應用程式</span><span class="sxs-lookup"><span data-stu-id="a4be9-108">Mixed Reality applications on the web</span></span>

<span data-ttu-id="a4be9-109">混合的現實功能可透過使用 [WebXR](webxr-overview.md)在網站上取得。</span><span class="sxs-lookup"><span data-stu-id="a4be9-109">Mixed Reality features are available on the web by the use of [WebXR](webxr-overview.md).</span></span> <span data-ttu-id="a4be9-110">您可以在不安裝任何其他軟體或外掛程式的情況下，于相容 WebXR 的瀏覽器中看到虛擬實境 (VR) 和增強的現實 (AR) 內容。</span><span class="sxs-lookup"><span data-stu-id="a4be9-110">You can see virtual reality (VR) and augmented reality (AR) content in a compatible WebXR-enabled browser without installing any additional software or plugins.</span></span> <span data-ttu-id="a4be9-111">您可以使用相同的瀏覽器與實體裝置（例如 HoloLens 2）。</span><span class="sxs-lookup"><span data-stu-id="a4be9-111">You can use that same browser with a physical device like the HoloLens 2.</span></span> <span data-ttu-id="a4be9-112">如需詳細資料，請參閱我們的 [WebXR](webxr-overview.md) 檔。</span><span class="sxs-lookup"><span data-stu-id="a4be9-112">Check out our [WebXR](webxr-overview.md) documentation for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="a4be9-113">**WebVR** 已被取代，無法在目前的瀏覽器中使用，因此不應該用於任何新的開發。</span><span class="sxs-lookup"><span data-stu-id="a4be9-113">**WebVR** is deprecated and is not available in current browsers, hence it should not be used for any new development.</span></span> <span data-ttu-id="a4be9-114">您必須將任何現有的 **WebVR** 執行移至 **WebXR**。</span><span class="sxs-lookup"><span data-stu-id="a4be9-114">You will need to migrate any existing **WebVR** implementations forward to **WebXR**.</span></span>

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a><span data-ttu-id="a4be9-115">我可以使用哪些功能來開發沉浸式 web 體驗？</span><span class="sxs-lookup"><span data-stu-id="a4be9-115">What can I use to develop immersive web experiences?</span></span>

<span data-ttu-id="a4be9-116">下列清單顯示的 JavaScript 架構和 Api，可用於建立目前市場上的沉浸式體驗，並受到混合現實 JavaScript 開發人員的廣泛接受和採用：</span><span class="sxs-lookup"><span data-stu-id="a4be9-116">The following list shows the JavaScript frameworks and APIs for building immersive experiences that currently dominate the market and are widely accepted and adopted by Mixed Reality JavaScript developers:</span></span>

|  |  |
| --- | --- |
|[<span data-ttu-id="a4be9-117">**Babylon.js**</span><span class="sxs-lookup"><span data-stu-id="a4be9-117">**Babylon.js**</span></span>](https://doc.babylonjs.com/)<br/><br/> <span data-ttu-id="a4be9-118">Babylon 是 JavaScript 3D 引擎，可讓您輕鬆開發3D 內容和沉浸式應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4be9-118">Babylon is a JavaScript 3D engine that makes developing 3D content and immersive applications easy.</span></span> <span data-ttu-id="a4be9-119">開始使用沉浸式應用程式之前，建議您先瞭解 Babylon.js 開發的基本概念。</span><span class="sxs-lookup"><span data-stu-id="a4be9-119">Before getting started with immersive applications, we recommend to learn the basics of Babylon.js development.</span></span><br/><br/><span data-ttu-id="a4be9-120">-瞭解如何使用 babylon.js [入門](https://doc.babylonjs.com/start)來建立3d 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4be9-120">- Learn how to build 3D applications with babylon.js [Getting started](https://doc.babylonjs.com/start).</span></span><br/><span data-ttu-id="a4be9-121">-使用 babylon.js[遊樂場](https://doc.babylonjs.com/examples/)來播放3d 範例和其原始程式碼</span><span class="sxs-lookup"><span data-stu-id="a4be9-121">- Play with 3D examples and their source code using babylon.js [Playground](https://doc.babylonjs.com/examples/)</span></span><br/><span data-ttu-id="a4be9-122">-深入探索 [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)</span><span class="sxs-lookup"><span data-stu-id="a4be9-122">- Dive deeper into [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)</span></span><br/><span data-ttu-id="a4be9-123">-瞭解如何開始使用我們的教學課程， [建立您的第一個「Hello World！」應用程式](tutorials/babylonjs-webxr-helloworld/introduction-01.md)</span><span class="sxs-lookup"><span data-stu-id="a4be9-123">- Learn how to get started with our tutorials [Create your first "Hello World!" app](tutorials/babylonjs-webxr-helloworld/introduction-01.md)</span></span>|![BabylonJS 標誌](images/babylon.js.example.png) |
|[<span data-ttu-id="a4be9-125">**A 框架**</span><span class="sxs-lookup"><span data-stu-id="a4be9-125">**A-Frame**</span></span>](https://aframe.io/) <br/><br/><span data-ttu-id="a4be9-126">框架是一種宣告式的 JavaScript 架構，可讓您在網路中開始使用虛擬事實。</span><span class="sxs-lookup"><span data-stu-id="a4be9-126">A-frame is a declarative JavaScript framework to get started with Virtual Reality in the web.</span></span> <span data-ttu-id="a4be9-127">若要深入瞭解，請參閱 [框架檔](https://aframe.io/docs/1.2.0/introduction/) 。</span><span class="sxs-lookup"><span data-stu-id="a4be9-127">Check out the [A-Frame documentation](https://aframe.io/docs/1.2.0/introduction/) to learn more.</span></span> |![A 框架](images/a-frame.example.png)  |
|[<span data-ttu-id="a4be9-129">**Three.js**</span><span class="sxs-lookup"><span data-stu-id="a4be9-129">**Three.js**</span></span>](https://threejs.org) <br/><br/><span data-ttu-id="a4be9-130">Three.js 是一種熱門的3D 程式庫，可讓您建立沉浸式體驗。</span><span class="sxs-lookup"><span data-stu-id="a4be9-130">Three.js is a popular 3D library for creating immersive experiences.</span></span> <span data-ttu-id="a4be9-131">深入瞭解檔頁面中的 [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) ，以及探索 [範例](https://threejs.org/examples/#webgl_animation_cloth)。</span><span class="sxs-lookup"><span data-stu-id="a4be9-131">Learn more about [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) in documentation page and by exploring [examples](https://threejs.org/examples/#webgl_animation_cloth).</span></span> |![Three.js](images/three.js.example.png)  |
|[<span data-ttu-id="a4be9-133">**WebGL**</span><span class="sxs-lookup"><span data-stu-id="a4be9-133">**WebGL**</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/><span data-ttu-id="a4be9-134">您可以使用 WebGL Api 直接存取 WebXR 裝置 Api。</span><span class="sxs-lookup"><span data-stu-id="a4be9-134">You can access the WebXR Device APIs directly by using WebGL APIs.</span></span> <span data-ttu-id="a4be9-135">WebGL (Web 圖形程式庫) 是一種 JavaScript API，可在任何相容的網頁瀏覽器內轉譯高效能的互動式3D 和2D 圖形，而不需要使用外掛程式。</span><span class="sxs-lookup"><span data-stu-id="a4be9-135">WebGL (Web Graphics Library) is a JavaScript API for rendering high-performance interactive 3D and 2D graphics within any compatible web browser without the use of plug-ins.</span></span> |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a><span data-ttu-id="a4be9-137">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a4be9-137">Next steps</span></span>

<span data-ttu-id="a4be9-138">深入瞭解如何開始使用我們的教學課程。</span><span class="sxs-lookup"><span data-stu-id="a4be9-138">Learn how to get started with our tutorials.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4be9-139">建立您的第一個 "Hello World！" 應用程式</span><span class="sxs-lookup"><span data-stu-id="a4be9-139">Create your first "Hello World!" app</span></span>](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a><span data-ttu-id="a4be9-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4be9-140">See Also</span></span>

* [<span data-ttu-id="a4be9-141">WebXR 總覽</span><span class="sxs-lookup"><span data-stu-id="a4be9-141">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="a4be9-142">WebXR 裝置 API 規格</span><span class="sxs-lookup"><span data-stu-id="a4be9-142">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="a4be9-143">WebXR 裝置 API 檔</span><span class="sxs-lookup"><span data-stu-id="a4be9-143">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="a4be9-144">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="a4be9-144">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="a4be9-145">WebXR 範例</span><span class="sxs-lookup"><span data-stu-id="a4be9-145">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="a4be9-146">使用 Babylon.js 建立 WebXR 體驗</span><span class="sxs-lookup"><span data-stu-id="a4be9-146">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="a4be9-147">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a4be9-147">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="a4be9-148">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="a4be9-148">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="a4be9-149">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="a4be9-149">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="a4be9-150">[遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能</span><span class="sxs-lookup"><span data-stu-id="a4be9-150">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
