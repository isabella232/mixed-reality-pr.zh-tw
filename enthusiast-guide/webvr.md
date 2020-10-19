---
title: 使用 WebVR 搭配 Windows Mixed Reality
description: 描述 WebVR 以及如何搭配 Windows Mixed Reality 耳機上的 Microsoft Edge 來使用它。
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，WebVR，Edge，Microsoft Edge，網頁流覽
ms.openlocfilehash: e57ad060a1a539e90631d1b9f1808d1e8466e669
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174349"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="75b0e-104">使用 WebVR 搭配 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="75b0e-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT] 
><span data-ttu-id="75b0e-105">大部分的新式網頁瀏覽器都已淘汰 WebVR 的支援，以促進 WebXR，這是建立 VR 耳機之沉浸式 web 體驗的新標準。</span><span class="sxs-lookup"><span data-stu-id="75b0e-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="75b0e-106">請安裝 [新的 Microsoft Edge](using-microsoft-edge.md) 以 WebXR 支援。</span><span class="sxs-lookup"><span data-stu-id="75b0e-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="75b0e-107">什麼是 WebVR？</span><span class="sxs-lookup"><span data-stu-id="75b0e-107">What is WebVR?</span></span>

<span data-ttu-id="75b0e-108">[WebVR](https://webvr.info) 是一種開放的規格，可以在瀏覽器中體驗 VR。</span><span class="sxs-lookup"><span data-stu-id="75b0e-108">[WebVR](https://webvr.info) is an open specification that makes it possible to experience VR in your browser.</span></span> <span data-ttu-id="75b0e-109">如果網站實行 WebVR 支援並提供3D 內容，它可以在耳機中顯示沉浸式內容，並提供使用者同意。</span><span class="sxs-lookup"><span data-stu-id="75b0e-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="75b0e-110">在 VR 中 WebVR 和流覽 web 有何不同？</span><span class="sxs-lookup"><span data-stu-id="75b0e-110">What is the difference between WebVR and browsing the web in VR?</span></span>

<span data-ttu-id="75b0e-111">WebVR 是一種技術，可讓網站作者將 VR 功能新增至網頁。</span><span class="sxs-lookup"><span data-stu-id="75b0e-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="75b0e-112">頁面會使用 WebVR API 來顯示3D 內容 (例如360度的影片、3D 模型，或整個耳機) 的3D 遊戲。</span><span class="sxs-lookup"><span data-stu-id="75b0e-112">The WebVR API is used by a page to display 3D content (such as 360 degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="75b0e-113">**範例：** 在 [cnn.com/vr](http://cnn.com/vr)上觀看360影片。</span><span class="sxs-lookup"><span data-stu-id="75b0e-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="75b0e-114">如果頁面支援 WebVR，則會新增按鈕或其他 UI 元素，您可以按一下以輸入 VR。</span><span class="sxs-lookup"><span data-stu-id="75b0e-114">If a page supports WebVR, it will add a button or other UI element that you can click to enter VR.</span></span>

<span data-ttu-id="75b0e-115">在 VR 中流覽 web 表示在您佩戴耳機時使用 Edge 瀏覽器，這是 Cliffhouse 內的2D 應用程式平板。</span><span class="sxs-lookup"><span data-stu-id="75b0e-115">Browsing the web in VR means using the Edge browser while you are wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="75b0e-116">所有網站都支援 WebVR 嗎？</span><span class="sxs-lookup"><span data-stu-id="75b0e-116">Do all websites support WebVR?</span></span>

<span data-ttu-id="75b0e-117">否。</span><span class="sxs-lookup"><span data-stu-id="75b0e-117">No.</span></span> <span data-ttu-id="75b0e-118">網站作者必須選擇使用 WebVR，而且他們可以建立針對特定瀏覽器、耳機和控制器優化的網站。</span><span class="sxs-lookup"><span data-stu-id="75b0e-118">Website authors must opt-in to use WebVR and furthermore they may create sites that are optimized for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="75b0e-119">例如，某些 WebVR 內容只針對 mobile VR 裝置優化。</span><span class="sxs-lookup"><span data-stu-id="75b0e-119">For example, some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="75b0e-120">此外，請記住，網站必須明確建立並提供 WebVR 內容。</span><span class="sxs-lookup"><span data-stu-id="75b0e-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="75b0e-121">有一些 WebVR 相容內容的網站數目每天都會成長。</span><span class="sxs-lookup"><span data-stu-id="75b0e-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="75b0e-122">我可以使用我的 Vive/Oculus 等來查看 Microsoft Edge 中的 WebVR 內容嗎？</span><span class="sxs-lookup"><span data-stu-id="75b0e-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge?</span></span>

<span data-ttu-id="75b0e-123">否。</span><span class="sxs-lookup"><span data-stu-id="75b0e-123">No.</span></span> <span data-ttu-id="75b0e-124">您必須使用 Windows Mixed Reality 耳機在 Edge 中使用 WebVR。</span><span class="sxs-lookup"><span data-stu-id="75b0e-124">You must use a Windows Mixed Reality headset to use WebVR in Edge.</span></span> <span data-ttu-id="75b0e-125">不過，您可以在另一個瀏覽器中存取 WebVR 內容;請參閱下列網址的完整相容裝置和瀏覽器清單： [WebVR. rocks](http://webvr.rocks/)。</span><span class="sxs-lookup"><span data-stu-id="75b0e-125">However, you may be able to access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="75b0e-126">我可以在哪裡找到 WebVR 開發人員檔？</span><span class="sxs-lookup"><span data-stu-id="75b0e-126">Where can I find the WebVR developer documentation?</span></span>

<span data-ttu-id="75b0e-127">開發人員檔位於此處： [WebVR 開發人員檔](https://docs.microsoft.com/microsoft-edge/webvr/)。</span><span class="sxs-lookup"><span data-stu-id="75b0e-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="75b0e-128">我發現有 WebVR 的網站在 Windows Mixed Reality 中無法運作。</span><span class="sxs-lookup"><span data-stu-id="75b0e-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="75b0e-129">該怎麼辦？</span><span class="sxs-lookup"><span data-stu-id="75b0e-129">What do I do?</span></span>

<span data-ttu-id="75b0e-130">您可以直接向 [問題追蹤](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)程式中的 Microsoft Edge 瀏覽器小組報告已中斷的網站，或使用 [#EdgeBug](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)主題標籤，透過 twitter 來回報。</span><span class="sxs-lookup"><span data-stu-id="75b0e-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="75b0e-131">您也可以使用類別目錄下的 Windows 意見反應中樞應用程式來記錄 bug：</span><span class="sxs-lookup"><span data-stu-id="75b0e-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="75b0e-132">Microsoft Edge > 網站問題</span><span class="sxs-lookup"><span data-stu-id="75b0e-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="75b0e-133">如果 WebVR 正在運作，要測試什麼是不錯的頁面？</span><span class="sxs-lookup"><span data-stu-id="75b0e-133">What is a good page to test if WebVR is working?</span></span>

<span data-ttu-id="75b0e-134">請參閱 [webvr.info 範例](http://webvr.info/samples/XX-vr-controllers.html)。</span><span class="sxs-lookup"><span data-stu-id="75b0e-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="75b0e-135">如何? 設定 WebVR？</span><span class="sxs-lookup"><span data-stu-id="75b0e-135">How do I set up WebVR?</span></span>

<span data-ttu-id="75b0e-136">若要在 Windows Mixed Reality 耳機 (使用硬體或模擬來體驗 WebVR 內容) 您必須：</span><span class="sxs-lookup"><span data-stu-id="75b0e-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation) you must:</span></span>
1. <span data-ttu-id="75b0e-137">確定您的耳機已連線。</span><span class="sxs-lookup"><span data-stu-id="75b0e-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="75b0e-138">在桌面上或在混合現實中啟動 Microsoft Edge。</span><span class="sxs-lookup"><span data-stu-id="75b0e-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="75b0e-139">流覽至已啟用 WebVR 的頁面。</span><span class="sxs-lookup"><span data-stu-id="75b0e-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="75b0e-140">按一下頁面內的 [輸入 VR] 按鈕 (此按鈕的位置和視覺標記法可能會因每個網站) 而有所不同。</span><span class="sxs-lookup"><span data-stu-id="75b0e-140">Click the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="75b0e-141">它看起來可能類似： </span><span class="sxs-lookup"><span data-stu-id="75b0e-141">It may look similar to:</span></span>\
   ![VR Goggles 映射](images/75px-enter-vr.png)
5. <span data-ttu-id="75b0e-143">當您第一次嘗試在特定網域上輸入 VR 時，瀏覽器會要求同意使用沉浸式視圖，請按一下 [是]：</span><span class="sxs-lookup"><span data-stu-id="75b0e-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, click yes:</span></span> ![第一次嘗試在特定網域上輸入 VR 時所顯示的同意 UI](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="75b0e-145">您的耳機應該會開始顯示 WebVR 內容。</span><span class="sxs-lookup"><span data-stu-id="75b0e-145">Your headset should begin displaying the WebVR content.</span></span>


## <a name="see-also"></a><span data-ttu-id="75b0e-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75b0e-146">See also</span></span>

* [<span data-ttu-id="75b0e-147">針對 > WebVR 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="75b0e-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="75b0e-148">如何進入您的第一個 WebVR 體驗</span><span class="sxs-lookup"><span data-stu-id="75b0e-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="75b0e-149">在 Windows Mixed Reality 中使用遊戲和應用程式</span><span class="sxs-lookup"><span data-stu-id="75b0e-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="75b0e-150">您的混合現實首頁</span><span class="sxs-lookup"><span data-stu-id="75b0e-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="75b0e-151">追蹤系統</span><span class="sxs-lookup"><span data-stu-id="75b0e-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="75b0e-152">移動控制器</span><span class="sxs-lookup"><span data-stu-id="75b0e-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="75b0e-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="75b0e-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="75b0e-154">歸檔意見反應</span><span class="sxs-lookup"><span data-stu-id="75b0e-154">Filing feedback</span></span>](filing-feedback.md)
