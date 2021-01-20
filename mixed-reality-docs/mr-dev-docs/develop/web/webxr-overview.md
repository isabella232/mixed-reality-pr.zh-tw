---
title: 使用 WebXR 搭配 Windows Mixed Reality
description: 瞭解針對 Windows Mixed Reality 沉浸式耳機上執行的 WebXR 應用程式，使用和開發的基本概念。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360影片、360影片、360相片、360相片、360內容、沉浸式 web、immersiveweb、IW
ms.openlocfilehash: 99cf5cf151c41252e43c6051c0d6281d33fe695a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582901"
---
# <a name="webxr-overview"></a><span data-ttu-id="01d99-104">WebXR 總覽</span><span class="sxs-lookup"><span data-stu-id="01d99-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="01d99-105">什麼是 WebXR</span><span class="sxs-lookup"><span data-stu-id="01d99-105">What is WebXR</span></span>

<span data-ttu-id="01d99-106">**WebXR 裝置 API** 適用于存取 **虛擬實境 (VR)** 和增強的 **現實 (AR)** 裝置，包括 **感應器** 和 **網路** 上的 **前端裝載顯示器**。</span><span class="sxs-lookup"><span data-stu-id="01d99-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="01d99-107">WebXR 裝置 API 目前適用于 Microsoft Edge，且 Chrome 79 版和更新版本支援以 WebXR 作為預設值。</span><span class="sxs-lookup"><span data-stu-id="01d99-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="01d99-108">您可以在 [caniuse.com](https://caniuse.com/#search=webxr)上檢查 WebXR 的最新瀏覽器支援狀態。</span><span class="sxs-lookup"><span data-stu-id="01d99-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="01d99-109">在[新功能](/windows/mixed-reality/mrtk-porting-guide)一節中深入瞭解[Windows Mixed Reality 以及新的 Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)。</span><span class="sxs-lookup"><span data-stu-id="01d99-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="01d99-110">觀看 WebXR</span><span class="sxs-lookup"><span data-stu-id="01d99-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01d99-111">Microsoft Edge (舊版) 只支援 WebVR，也就是目前的瀏覽器中未提供的已淘汰 API。</span><span class="sxs-lookup"><span data-stu-id="01d99-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="01d99-112">不過，新的 **[Chromium 為基礎的 Edge 瀏覽器](../../whats-new/new-microsoft-edge.md)** 支援 WebXR，並且可用於 Windows Mixed Reality 中的 VR 原型設計。</span><span class="sxs-lookup"><span data-stu-id="01d99-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="01d99-113">新的 Chromium Edge 瀏覽器中將無法使用 WebVR。</span><span class="sxs-lookup"><span data-stu-id="01d99-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="01d99-114">如果您想要在今天 HoloLens 2 建立原型 WebXR 的方法，請查看 [Firefox 的實際](https://mixedreality.mozilla.org/firefox-reality/)情況。</span><span class="sxs-lookup"><span data-stu-id="01d99-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="01d99-115">若要測試您的瀏覽器是否支援 WebXR，您可以在瀏覽器中流覽至 [WebXR 範例](https://immersive-web.github.io/webxr-samples/) 。</span><span class="sxs-lookup"><span data-stu-id="01d99-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="01d99-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01d99-116">See Also</span></span>

* [<span data-ttu-id="01d99-117">WebXR 裝置 API 規格</span><span class="sxs-lookup"><span data-stu-id="01d99-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="01d99-118">WebXR 裝置 API 檔</span><span class="sxs-lookup"><span data-stu-id="01d99-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="01d99-119">Immersiveweb dev</span><span class="sxs-lookup"><span data-stu-id="01d99-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="01d99-120">WebXR 範例</span><span class="sxs-lookup"><span data-stu-id="01d99-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="01d99-121">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="01d99-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="01d99-122">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="01d99-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="01d99-123">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="01d99-123">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="01d99-124">[遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能</span><span class="sxs-lookup"><span data-stu-id="01d99-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="01d99-125">處理 WebGL 中遺失的內容</span><span class="sxs-lookup"><span data-stu-id="01d99-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="01d99-126">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="01d99-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="01d99-127">glTF</span><span class="sxs-lookup"><span data-stu-id="01d99-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="01d99-128">使用 Babylon.js 建立 WebXR 體驗</span><span class="sxs-lookup"><span data-stu-id="01d99-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="01d99-129">沉浸式 web 社區群組</span><span class="sxs-lookup"><span data-stu-id="01d99-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)