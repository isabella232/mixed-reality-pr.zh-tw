---
title: 使用 WebVR 搭配 Windows Mixed Reality
description: 瞭解 WebVR 的基本概念、如何搭配 Windows Mixed Reality 耳機的 Microsoft Edge 以及常見的疑難排解問題。
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，WebVR，Edge，Microsoft Edge，網頁流覽
ms.openlocfilehash: 0b0d07383b43feaa11fb9bfac2b071d8d4d80b19
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009438"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="cbf3b-104">使用 WebVR 搭配 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="cbf3b-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT]
><span data-ttu-id="cbf3b-105">大部分的新式網頁瀏覽器都已淘汰 WebVR 的支援，以促進 WebXR，這是建立 VR 耳機之沉浸式 web 體驗的新標準。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="cbf3b-106">請安裝 [新的 Microsoft Edge](using-microsoft-edge.md) 以 WebXR 支援。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="cbf3b-107">什麼是 WebVR</span><span class="sxs-lookup"><span data-stu-id="cbf3b-107">What is WebVR</span></span>

<span data-ttu-id="cbf3b-108">[WebVR](https://webvr.info) 是一種開放的規格，可讓您直接從瀏覽器體驗 VR。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-108">[WebVR](https://webvr.info) is an open specification that lets you experience VR right from a browser.</span></span> <span data-ttu-id="cbf3b-109">如果網站實行 WebVR 支援並提供3D 內容，它可以在耳機中顯示沉浸式內容，並提供使用者同意。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="cbf3b-110">在 VR 中 WebVR 和流覽 web 有何不同</span><span class="sxs-lookup"><span data-stu-id="cbf3b-110">What is the difference between WebVR and browsing the web in VR</span></span>

<span data-ttu-id="cbf3b-111">WebVR 是一種技術，可讓網站作者將 VR 功能新增至網頁。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="cbf3b-112">頁面會使用 WebVR API 來顯示3D 內容 (例如360度的影片、3D 模型，或整個耳機) 的3D 遊戲。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-112">The WebVR API is used by a page to display 3D content (such as 360-degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="cbf3b-113">**範例：** 在 [cnn.com/vr](http://cnn.com/vr)上觀看360影片。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="cbf3b-114">如果頁面支援 WebVR，則會新增按鈕或其他 UI 元素，讓您可以選取以輸入 VR。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-114">If a page supports WebVR, it will add a button or other UI element that you can select to enter VR.</span></span>

<span data-ttu-id="cbf3b-115">在 VR 中流覽 web 表示在您佩戴耳機時使用 Edge 瀏覽器，這是 Cliffhouse 內的2D 應用程式平板。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-115">Browsing the web in VR means using the Edge browser while you're wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="cbf3b-116">所有網站都支援 WebVR</span><span class="sxs-lookup"><span data-stu-id="cbf3b-116">Do all websites support WebVR</span></span>

<span data-ttu-id="cbf3b-117">不會。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-117">No.</span></span> <span data-ttu-id="cbf3b-118">網站作者必須選擇使用 WebVR，而且他們可以針對特定的瀏覽器、耳機和控制器建立優化的網站。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-118">Website authors must opt in to use WebVR and they may create optimized sites for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="cbf3b-119">某些 WebVR 內容僅適用于 mobile VR 裝置。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-119">Some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="cbf3b-120">此外，請記住，網站必須明確建立並提供 WebVR 內容。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="cbf3b-121">有一些 WebVR 相容內容的網站數目每天都會成長。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="cbf3b-122">我可以使用 Vive/Oculus 等來查看 Microsoft Edge 中的 WebVR 內容</span><span class="sxs-lookup"><span data-stu-id="cbf3b-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge</span></span>

<span data-ttu-id="cbf3b-123">不會。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-123">No.</span></span> <span data-ttu-id="cbf3b-124">需要 Windows Mixed Reality 耳機才能在 Edge 中使用 WebVR。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-124">A Windows Mixed Reality headset is required to use WebVR in Edge.</span></span> <span data-ttu-id="cbf3b-125">不過，您可以在另一個瀏覽器中存取 WebVR 內容;請參閱下列網址的完整相容裝置和瀏覽器清單： [WebVR. rocks](http://webvr.rocks/)。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-125">However, you can access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="cbf3b-126">我可以在哪裡找到 WebVR 開發人員檔</span><span class="sxs-lookup"><span data-stu-id="cbf3b-126">Where can I find the WebVR developer documentation</span></span>

<span data-ttu-id="cbf3b-127">開發人員檔位於此處： [WebVR 開發人員檔](https://docs.microsoft.com/microsoft-edge/webvr/)。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="cbf3b-128">我發現有 WebVR 的網站在 Windows Mixed Reality 中無法運作。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="cbf3b-129">我該怎麼辦</span><span class="sxs-lookup"><span data-stu-id="cbf3b-129">What do I do</span></span>

<span data-ttu-id="cbf3b-130">您可以直接向 [問題追蹤](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)程式中的 Microsoft Edge 瀏覽器小組報告已中斷的網站，或使用 [#EdgeBug](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)主題標籤，透過 twitter 來回報。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="cbf3b-131">您也可以使用類別目錄下的 Windows 意見反應中樞應用程式來記錄 bug：</span><span class="sxs-lookup"><span data-stu-id="cbf3b-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="cbf3b-132">Microsoft Edge > 網站問題</span><span class="sxs-lookup"><span data-stu-id="cbf3b-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="cbf3b-133">如果 WebVR 正常運作，要測試什麼是不錯的頁面</span><span class="sxs-lookup"><span data-stu-id="cbf3b-133">What is a good page to test if WebVR is working</span></span>

<span data-ttu-id="cbf3b-134">請參閱 [webvr.info 範例](http://webvr.info/samples/XX-vr-controllers.html)。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="cbf3b-135">如何? 設定 WebVR</span><span class="sxs-lookup"><span data-stu-id="cbf3b-135">How do I set up WebVR</span></span>

<span data-ttu-id="cbf3b-136">若要在 Windows Mixed Reality 耳機 (使用硬體或模擬) 來體驗 WebVR 內容，您必須：</span><span class="sxs-lookup"><span data-stu-id="cbf3b-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation), you must:</span></span>

1. <span data-ttu-id="cbf3b-137">確定您的耳機已連線。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="cbf3b-138">在桌面上或在混合現實中啟動 Microsoft Edge。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="cbf3b-139">流覽至已啟用 WebVR 的頁面。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="cbf3b-140">選取頁面中的 [輸入 VR] 按鈕 (此按鈕的位置和視覺標記法可能會因每個網站) 而有所不同。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-140">Select the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="cbf3b-141">它看起來可能類似： </span><span class="sxs-lookup"><span data-stu-id="cbf3b-141">It may look similar to:</span></span>\
   ![VR Goggles 映射](images/75px-enter-vr.png)
5. <span data-ttu-id="cbf3b-143">當您第一次嘗試在特定網域上輸入 VR 時，瀏覽器會要求同意使用沉浸式視圖，請選取 [是]：</span><span class="sxs-lookup"><span data-stu-id="cbf3b-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, select yes:</span></span> ![第一次嘗試在特定網域上輸入 VR 時所顯示的同意 UI](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="cbf3b-145">您的耳機應該會開始顯示 WebVR 內容。</span><span class="sxs-lookup"><span data-stu-id="cbf3b-145">Your headset should begin displaying the WebVR content.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbf3b-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf3b-146">See also</span></span>

* [<span data-ttu-id="cbf3b-147">針對 > WebVR 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="cbf3b-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="cbf3b-148">如何進入您的第一個 WebVR 體驗</span><span class="sxs-lookup"><span data-stu-id="cbf3b-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="cbf3b-149">在 Windows Mixed Reality 中使用遊戲和應用程式</span><span class="sxs-lookup"><span data-stu-id="cbf3b-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="cbf3b-150">您的混合現實首頁</span><span class="sxs-lookup"><span data-stu-id="cbf3b-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="cbf3b-151">追蹤系統</span><span class="sxs-lookup"><span data-stu-id="cbf3b-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="cbf3b-152">移動控制器</span><span class="sxs-lookup"><span data-stu-id="cbf3b-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="cbf3b-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="cbf3b-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="cbf3b-154">歸檔意見反應</span><span class="sxs-lookup"><span data-stu-id="cbf3b-154">Filing feedback</span></span>](filing-feedback.md)
