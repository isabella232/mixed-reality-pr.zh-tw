---
title: 使用 WebXR 搭配 Windows Mixed Reality
description: 瞭解針對 Windows Mixed Reality 沉浸式耳機上執行的 WebXR 應用程式，使用和開發的基本概念。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360影片、360影片、360相片、360相片、360內容、沉浸式 web、immersiveweb、IW
ms.openlocfilehash: e49f5f2422c9802f94b63943f8a38949a2969f83
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006938"
---
# <a name="webxr-overview"></a><span data-ttu-id="82298-104">WebXR 總覽</span><span class="sxs-lookup"><span data-stu-id="82298-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="82298-105">什麼是 WebXR</span><span class="sxs-lookup"><span data-stu-id="82298-105">What is WebXR</span></span>

<span data-ttu-id="82298-106">**WebXR 裝置 API** 適用于存取 **虛擬實境 (VR)** 和增強的 **現實 (AR)** 裝置，包括 **感應器** 和 **網路** 上的 **前端裝載顯示器**。</span><span class="sxs-lookup"><span data-stu-id="82298-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="82298-107">WebXR 裝置 API 目前適用于 Microsoft Edge，且 Chrome 79 版和更新版本支援以 WebXR 作為預設值。</span><span class="sxs-lookup"><span data-stu-id="82298-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="82298-108">您可以在 [caniuse.com](https://caniuse.com/#search=webxr)上檢查 WebXR 的最新瀏覽器支援狀態。</span><span class="sxs-lookup"><span data-stu-id="82298-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="82298-109">在[新功能](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide)一節中深入瞭解[Windows Mixed Reality 以及新的 Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)。</span><span class="sxs-lookup"><span data-stu-id="82298-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="82298-110">觀看 WebXR</span><span class="sxs-lookup"><span data-stu-id="82298-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82298-111">Microsoft Edge (舊版) 只支援 WebVR，也就是目前的瀏覽器中未提供的已淘汰 API。</span><span class="sxs-lookup"><span data-stu-id="82298-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="82298-112">不過，新的 **[Chromium 為基礎的 Edge 瀏覽器](../../whats-new/new-microsoft-edge.md)** 支援 WebXR，並且可用於 Windows Mixed Reality 中的 VR 原型設計。</span><span class="sxs-lookup"><span data-stu-id="82298-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="82298-113">新的 Chromium Edge 瀏覽器中將無法使用 WebVR。</span><span class="sxs-lookup"><span data-stu-id="82298-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="82298-114">如果您想要在今天 HoloLens 2 建立原型 WebXR 的方法，請查看 [Firefox 的實際](https://mixedreality.mozilla.org/firefox-reality/)情況。</span><span class="sxs-lookup"><span data-stu-id="82298-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="82298-115">若要測試您的瀏覽器是否支援 WebXR，您可以在瀏覽器中流覽至 [WebXR 範例](https://immersive-web.github.io/webxr-samples/) 。</span><span class="sxs-lookup"><span data-stu-id="82298-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="82298-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82298-116">See Also</span></span>

* [<span data-ttu-id="82298-117">WebXR 裝置 API 規格</span><span class="sxs-lookup"><span data-stu-id="82298-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="82298-118">WebXR 裝置 API 檔</span><span class="sxs-lookup"><span data-stu-id="82298-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="82298-119">Immersiveweb dev</span><span class="sxs-lookup"><span data-stu-id="82298-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="82298-120">WebXR 範例</span><span class="sxs-lookup"><span data-stu-id="82298-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="82298-121">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="82298-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="82298-122">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="82298-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="82298-123">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="82298-123">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="82298-124">[遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能</span><span class="sxs-lookup"><span data-stu-id="82298-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="82298-125">處理 WebGL 中遺失的內容</span><span class="sxs-lookup"><span data-stu-id="82298-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="82298-126">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="82298-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="82298-127">glTF</span><span class="sxs-lookup"><span data-stu-id="82298-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="82298-128">使用 Babylon.js 建立 WebXR 體驗</span><span class="sxs-lookup"><span data-stu-id="82298-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="82298-129">沉浸式 web 社區群組</span><span class="sxs-lookup"><span data-stu-id="82298-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
