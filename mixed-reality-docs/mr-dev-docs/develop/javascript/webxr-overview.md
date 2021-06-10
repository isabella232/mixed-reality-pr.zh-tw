---
title: 使用 WebXR 搭配 Windows Mixed Reality
description: 瞭解針對 Windows Mixed Reality 沉浸式耳機上執行的 WebXR 應用程式，使用和開發的基本概念。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360影片、360影片、360相片、360相片、360內容、沉浸式 web、immersiveweb、IW
ms.openlocfilehash: fa4d11fac59e25f43d9d55de16d3b0c35e8166b7
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600107"
---
# <a name="webxr-overview"></a><span data-ttu-id="d2664-104">WebXR 總覽</span><span class="sxs-lookup"><span data-stu-id="d2664-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="d2664-105">什麼是 WebXR</span><span class="sxs-lookup"><span data-stu-id="d2664-105">What is WebXR</span></span>

<span data-ttu-id="d2664-106">[**WebXR 裝置 API**](https://www.w3.org/TR/webxr/)適用于存取 **虛擬實境 (VR)** 和增強的 **現實 (AR)** 裝置，包括 **感應器** 和 **網路** 上的 **前端裝載顯示器**。</span><span class="sxs-lookup"><span data-stu-id="d2664-106">The [**WebXR Device API**](https://www.w3.org/TR/webxr/) is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="d2664-107">WebXR 裝置 API 目前適用于 Microsoft Edge，且 Chrome 79 版和更新版本支援以 WebXR 作為預設值。</span><span class="sxs-lookup"><span data-stu-id="d2664-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="d2664-108">您可以在 [caniuse.com](https://caniuse.com/#search=webxr)上檢查 WebXR 的最新瀏覽器支援狀態。</span><span class="sxs-lookup"><span data-stu-id="d2664-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="d2664-109">觀看 WebXR</span><span class="sxs-lookup"><span data-stu-id="d2664-109">Viewing WebXR</span></span>

<span data-ttu-id="d2664-110">您可以在 Windows Mixed Reality 上查看 WebXR experinces， [以及新的 Microsoft Edge](../../whats-new/new-microsoft-edge.md) 和 [Firefox 事實](https://mixedreality.mozilla.org/firefox-reality/)。</span><span class="sxs-lookup"><span data-stu-id="d2664-110">You can view WebXR experinces on [Windows Mixed Reality and the new Microsoft Edge](../../whats-new/new-microsoft-edge.md) and [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>
<span data-ttu-id="d2664-111">若要測試您的瀏覽器是否支援 WebXR，您可以在瀏覽器中流覽至 [WebXR 範例](https://immersive-web.github.io/webxr-samples/) 。</span><span class="sxs-lookup"><span data-stu-id="d2664-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2664-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2664-112">See Also</span></span>

* [<span data-ttu-id="d2664-113">使用 Babylon.js 建立 WebXR 體驗</span><span class="sxs-lookup"><span data-stu-id="d2664-113">Using Babylon.js to create WebXR experiences</span></span>](./tutorials/babylonjs-webxr-helloworld/introduction-01.md)
* [<span data-ttu-id="d2664-114">WebXR 裝置 API 規格</span><span class="sxs-lookup"><span data-stu-id="d2664-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="d2664-115">WebXR 裝置 API 檔</span><span class="sxs-lookup"><span data-stu-id="d2664-115">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="d2664-116">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="d2664-116">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="d2664-117">WebXR 範例</span><span class="sxs-lookup"><span data-stu-id="d2664-117">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="d2664-118">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="d2664-118">Windows Mixed Reality and the new Microsoft Edge</span></span>](../../whats-new/new-microsoft-edge.md)
* [<span data-ttu-id="d2664-119">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="d2664-119">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="d2664-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d2664-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="d2664-121">[遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能</span><span class="sxs-lookup"><span data-stu-id="d2664-121">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="d2664-122">處理 WebGL 中遺失的內容</span><span class="sxs-lookup"><span data-stu-id="d2664-122">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="d2664-123">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="d2664-123">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="d2664-124">glTF</span><span class="sxs-lookup"><span data-stu-id="d2664-124">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="d2664-125">沉浸式 web 社區群組</span><span class="sxs-lookup"><span data-stu-id="d2664-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)