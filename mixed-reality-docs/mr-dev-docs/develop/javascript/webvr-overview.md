---
title: WebVR 總覽
description: 瞭解針對 Windows Mixed Reality 沉浸式耳機上執行的 WebVR 應用程式，使用和開發的基本概念。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebVR、WebXR、WinMR、WebAR、web vr、web xr、web mr、web ar、360、360影片、360影片、360相片、360相片、360內容、沉浸式 web、immersiveweb、IW
ROBOTS: NOINDEX
ms.openlocfilehash: dba3ca6b0cb9404f488db0b69a5bd89d6093a3ef
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104909030"
---
# <a name="webvr-overview"></a><span data-ttu-id="f4ae2-104">WebVR 總覽</span><span class="sxs-lookup"><span data-stu-id="f4ae2-104">WebVR Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4ae2-105">**WebVR 1.1 api** s 已被取代，並由 **WebXR 裝置 API** s 取代。</span><span class="sxs-lookup"><span data-stu-id="f4ae2-105">**WebVR 1.1 API** s are deprecated and replaced by **WebXR Device API** s.</span></span>

<span data-ttu-id="f4ae2-106">WebVR 1.1 Api 已淘汰，且已從 Chrome 和新的 Microsoft Edge 中移除。</span><span class="sxs-lookup"><span data-stu-id="f4ae2-106">WebVR 1.1 APIs are deprecated and removed from Chrome and the new Microsoft Edge.</span></span> <span data-ttu-id="f4ae2-107">WebXR 裝置 Api 會取代 WebVR Api。</span><span class="sxs-lookup"><span data-stu-id="f4ae2-107">WebVR APIs are superseded by WebXR Device APIs.</span></span> <span data-ttu-id="f4ae2-108">您可以在 [caniuse.com](https://caniuse.com/#search=webvr)上檢查目前支援 WebVR api 的瀏覽器清單。</span><span class="sxs-lookup"><span data-stu-id="f4ae2-108">You can check the list of browsers currently supporting WebVR APIs on [caniuse.com](https://caniuse.com/#search=webvr).</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="f4ae2-109">在 Windows Mixed Reality 沉浸式耳機中觀看 WebVR 內容</span><span class="sxs-lookup"><span data-stu-id="f4ae2-109">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="f4ae2-110">如需使用 **舊版 Microsoft Edge (15-18)** 來存取沉浸式耳機中 WebVR 內容的指示，請參閱 [愛好者指南](/windows/mixed-reality/enthusiast-guide/webvr)。</span><span class="sxs-lookup"><span data-stu-id="f4ae2-110">Instructions for accessing WebVR content in your immersive headsets with **older versions of Microsoft Edge(15-18)** can be found in the [Enthusiast's Guide](/windows/mixed-reality/enthusiast-guide/webvr).</span></span> <span data-ttu-id="f4ae2-111">您可以在 Edge 瀏覽器的搜尋列中輸入 "edge://version/"，以檢查您的 edge 版本。</span><span class="sxs-lookup"><span data-stu-id="f4ae2-111">You can check your edge version by typing "edge://version/" in your Edge browsers search bar.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4ae2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4ae2-112">See Also</span></span>

* [<span data-ttu-id="f4ae2-113">WebXR 總覽</span><span class="sxs-lookup"><span data-stu-id="f4ae2-113">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="f4ae2-114">WebXR 裝置 API 規格</span><span class="sxs-lookup"><span data-stu-id="f4ae2-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="f4ae2-115">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f4ae2-115">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge)
* [<span data-ttu-id="f4ae2-116">WebVR 資訊</span><span class="sxs-lookup"><span data-stu-id="f4ae2-116">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="f4ae2-117">WebVR 規格</span><span class="sxs-lookup"><span data-stu-id="f4ae2-117">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="f4ae2-118">[WebVR API](/previous-versions//mt806281(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f4ae2-118">[WebVR API](/previous-versions//mt806281(v=vs.85))</span></span>
* <span data-ttu-id="f4ae2-119">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f4ae2-119">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="f4ae2-120">[遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能</span><span class="sxs-lookup"><span data-stu-id="f4ae2-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="f4ae2-121">處理 WebGL 中遺失的內容</span><span class="sxs-lookup"><span data-stu-id="f4ae2-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="f4ae2-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="f4ae2-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="f4ae2-123">glTF</span><span class="sxs-lookup"><span data-stu-id="f4ae2-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="f4ae2-124">使用 Babylon.js 啟用 WebVR</span><span class="sxs-lookup"><span data-stu-id="f4ae2-124">Using Babylon.js to enable WebVR</span></span>](/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)