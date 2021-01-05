---
title: WebVR 常見問題
description: 超越標準取用者支援檔的網路混合現實疑難排解。
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援、WebVR
ms.openlocfilehash: fd9906ca36c71b1bf959466d90c57e07be0eca5e
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725629"
---
# <a name="webvr-faqs"></a><span data-ttu-id="cc08a-104">WebVR 常見問題</span><span class="sxs-lookup"><span data-stu-id="cc08a-104">WebVR FAQs</span></span>

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a><span data-ttu-id="cc08a-105">為什麼我在從 Edge 查看 VR 內容時看不到我的控制器</span><span class="sxs-lookup"><span data-stu-id="cc08a-105">Why can’t I see my controllers when viewing VR content from Edge</span></span>

<span data-ttu-id="cc08a-106">並非所有 WebVR 內容都是為了支援移動控制器而撰寫的。</span><span class="sxs-lookup"><span data-stu-id="cc08a-106">Not all WebVR content is authored to support motion controllers.</span></span> <span data-ttu-id="cc08a-107">WebVR 可讓內容開發人員支援不同類型的輸入，例如遊戲控制器或動作控制器。</span><span class="sxs-lookup"><span data-stu-id="cc08a-107">WebVR allows content developers to support different types of input, such as game controllers or motion controllers.</span></span> <span data-ttu-id="cc08a-108">如果您在網站上看不到您的控制器，則可能沒有移動控制器支援。</span><span class="sxs-lookup"><span data-stu-id="cc08a-108">If you don't see your controllers on a site, it probably doesn’t have motion controller support.</span></span>

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a><span data-ttu-id="cc08a-109">為什麼我無法在沉浸式 WebVR 視圖中使用滑鼠</span><span class="sxs-lookup"><span data-stu-id="cc08a-109">Why can't I use the mouse in an immersive WebVR view</span></span>

<span data-ttu-id="cc08a-110">使用滑鼠是 WebVR 規格的選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="cc08a-110">Using a mouse is an optional feature of the WebVR specification.</span></span> <span data-ttu-id="cc08a-111">並非所有瀏覽器都支援這項功能，而且並非所有 WebVR 內容都是為了支援滑鼠輸入而撰寫的。</span><span class="sxs-lookup"><span data-stu-id="cc08a-111">Not all browsers support this feature, and not all WebVR content is authored to support mouse input.</span></span> <span data-ttu-id="cc08a-112">WebVR 可讓內容開發人員支援不同類型的輸入，例如滑鼠、鍵盤、遊戲控制器或移動控制器。</span><span class="sxs-lookup"><span data-stu-id="cc08a-112">WebVR allows content developers to support different types of input, such as mouse, keyboard, game controllers, or motion controllers.</span></span> <span data-ttu-id="cc08a-113">滑鼠輸入行為會依瀏覽器而有所不同。</span><span class="sxs-lookup"><span data-stu-id="cc08a-113">Mouse input behavior varies per browser.</span></span> <span data-ttu-id="cc08a-114">在 Microsoft Edge 中，網站作者必須確保在向耳機呈現時，會使用「pointerlock」來執行滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="cc08a-114">Within Microsoft Edge, website authors must ensure they take 'pointerlock' when presenting to the headset for mouse input to work.</span></span>

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a><span data-ttu-id="cc08a-115">為什麼我無法從 Youtube/Facebook/Vimeo/守護者在 VR 的邊緣查看360度的影片</span><span class="sxs-lookup"><span data-stu-id="cc08a-115">Why can’t I view 360-degree videos from Youtube/Facebook/Vimeo/The Guardian, etc. from Edge in VR</span></span>

<span data-ttu-id="cc08a-116">有一個 WebVR 規格，可讓網站直接從瀏覽器啟動 VR 體驗。</span><span class="sxs-lookup"><span data-stu-id="cc08a-116">There's a WebVR specification that lets websites launch VR experiences directly from the browser.</span></span> <span data-ttu-id="cc08a-117">這些網站的作者目前尚未執行此規格。</span><span class="sxs-lookup"><span data-stu-id="cc08a-117">The authors of these websites haven't implemented this specification at this time.</span></span> <span data-ttu-id="cc08a-118">某些平臺上可能會有可下載的應用程式，可讓您從這些廠商查看 VR 內容。</span><span class="sxs-lookup"><span data-stu-id="cc08a-118">There may be downloadable apps on some platforms that enable viewing of VR content from these vendors.</span></span>

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a><span data-ttu-id="cc08a-119">為什麼我無法從 Firefox 或 Chrome 輸入 VR</span><span class="sxs-lookup"><span data-stu-id="cc08a-119">Why can’t I enter VR from Firefox or Chrome</span></span>

<span data-ttu-id="cc08a-120">目前只有 Edge Windows Mixed Reality 裝置才支援 WebVR。</span><span class="sxs-lookup"><span data-stu-id="cc08a-120">WebVR is only supported by Windows Mixed Reality devices in Edge at this time.</span></span>

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a><span data-ttu-id="cc08a-121">當我從網站輸入 VR 時，為什麼我會在耳機中看到空白畫面</span><span class="sxs-lookup"><span data-stu-id="cc08a-121">When I enter VR from a website, why do I see a blank screen in my headset</span></span>

<span data-ttu-id="cc08a-122">網站可能尚未支援多 GPU 機器 (包括混合式 GPU 膝上型電腦) 。</span><span class="sxs-lookup"><span data-stu-id="cc08a-122">The website may not have implemented support for multi GPU machines (including hybrid GPU laptops).</span></span> <span data-ttu-id="cc08a-123">嘗試：</span><span class="sxs-lookup"><span data-stu-id="cc08a-123">Try to:</span></span>

* <span data-ttu-id="cc08a-124">重新載入頁面。</span><span class="sxs-lookup"><span data-stu-id="cc08a-124">Reload the page.</span></span>
* <span data-ttu-id="cc08a-125">在桌上型電腦上，將耳機插入與顯示 Microsoft Edge 的監視器相同的圖形介面卡中。</span><span class="sxs-lookup"><span data-stu-id="cc08a-125">On desktop machines, plug the headset into the same graphics adapter as the monitor that is displaying Microsoft Edge.</span></span> <span data-ttu-id="cc08a-126">將兩者插入至較高的電源圖形配接器，而不是整合式圖形介面卡。</span><span class="sxs-lookup"><span data-stu-id="cc08a-126">Plug both into the higher powered graphics card, not into the integrated graphics adapter.</span></span>

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a><span data-ttu-id="cc08a-127">當我在從 Edge 觀看影片時結束 VR 時，音效會持續播放，但邊緣視窗會呈現灰色</span><span class="sxs-lookup"><span data-stu-id="cc08a-127">When I exit VR when watching a video from Edge, the sound continues playing but the Edge window is grayed out</span></span>

<span data-ttu-id="cc08a-128">這是在混合現實懸崖之屋中從邊緣執行 WebVR 時的已知問題。</span><span class="sxs-lookup"><span data-stu-id="cc08a-128">This is a known issue when running WebVR from Edge in the Mixed Reality Cliff House.</span></span> <span data-ttu-id="cc08a-129">若要解決此問題，請在鍵盤上按 esc 鍵（而不是 [windows] 按鈕）以結束 WebVR 體驗，或是選取它，然後停止影片來啟用灰色的邊緣視窗。</span><span class="sxs-lookup"><span data-stu-id="cc08a-129">To resolve it, press escape on the keyboard instead of the windows button to exit the WebVR experience, or activate the greyed out Edge window by selecting it and then stop the video.</span></span>

## <a name="can-i-use-webvr-on-the-hololens"></a><span data-ttu-id="cc08a-130">我可以在 HoloLens 上使用 WebVR</span><span class="sxs-lookup"><span data-stu-id="cc08a-130">Can I use WebVR on the HoloLens</span></span>

<span data-ttu-id="cc08a-131">Microsoft 目前尚未在 HoloLens 上宣佈任何關於 WebVR 的資訊。</span><span class="sxs-lookup"><span data-stu-id="cc08a-131">Microsoft hasn't announced anything about WebVR on the HoloLens at this point.</span></span>

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a><span data-ttu-id="cc08a-132">當您從邊緣觀看 WebVR 內容時，為什麼我的視圖位於樓層層級</span><span class="sxs-lookup"><span data-stu-id="cc08a-132">Why is my view at floor level when viewing WebVR content from Edge</span></span>

<span data-ttu-id="cc08a-133">網站未適當支援 Windows Mixed Reality 耳機。</span><span class="sxs-lookup"><span data-stu-id="cc08a-133">The website doesn't properly support Windows Mixed Reality headsets.</span></span> <span data-ttu-id="cc08a-134">若要解決這個問題︰</span><span class="sxs-lookup"><span data-stu-id="cc08a-134">To work around this:</span></span>

1. <span data-ttu-id="cc08a-135">將耳機放在您的空間地板上。</span><span class="sxs-lookup"><span data-stu-id="cc08a-135">Place the headset on the floor of your space.</span></span>
2. <span data-ttu-id="cc08a-136">使用桌面上的 Microsoft Edge 流覽至 [WebVR] 頁面， (不在混合現實) 內。</span><span class="sxs-lookup"><span data-stu-id="cc08a-136">Navigate to the WebVR page using Microsoft Edge on your desktop (not within mixed reality).</span></span>
3. <span data-ttu-id="cc08a-137">選取 [輸入 VR]。</span><span class="sxs-lookup"><span data-stu-id="cc08a-137">Select "Enter VR".</span></span>
4. <span data-ttu-id="cc08a-138">等候五至10秒，讓體驗完全進入沉浸式模式。</span><span class="sxs-lookup"><span data-stu-id="cc08a-138">Wait five to 10 seconds for the experience to fully enter immersive mode.</span></span>
5. <span data-ttu-id="cc08a-139">放在耳機上。</span><span class="sxs-lookup"><span data-stu-id="cc08a-139">Put on the headset.</span></span>

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a><span data-ttu-id="cc08a-140">在某些 WebVR 體驗中，顯示器的解析度低</span><span class="sxs-lookup"><span data-stu-id="cc08a-140">The display is low resolution in some WebVR experiences</span></span>

<span data-ttu-id="cc08a-141">這些網站未適當支援高解析度耳機。</span><span class="sxs-lookup"><span data-stu-id="cc08a-141">Those websites don't properly support high-resolution headsets.</span></span> <span data-ttu-id="cc08a-142">若要解決這個問題︰</span><span class="sxs-lookup"><span data-stu-id="cc08a-142">To work around this:</span></span>

* <span data-ttu-id="cc08a-143">如果從 (桌面啟動 WebVR，而不是懸崖之屋) 的混合現實，請在選取 [Enter VR] 之前，先確定已將視窗最大化。</span><span class="sxs-lookup"><span data-stu-id="cc08a-143">If launching WebVR from the desktop (rather than the mixed reality Cliff House), ensure the window is maximized before selecting "Enter VR".</span></span>
* <span data-ttu-id="cc08a-144">請避免在您輸入 VR 之後調整 Microsoft Edge 視窗的大小。</span><span class="sxs-lookup"><span data-stu-id="cc08a-144">Avoid resizing the Microsoft Edge window after you have entered VR.</span></span>

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a><span data-ttu-id="cc08a-145">為什麼當我變更瀏覽器索引標籤時，WebVR 沉浸式視圖結束</span><span class="sxs-lookup"><span data-stu-id="cc08a-145">Why does the WebVR immersive view exit when I change browser tabs</span></span>

<span data-ttu-id="cc08a-146">這是正常的現象。</span><span class="sxs-lookup"><span data-stu-id="cc08a-146">This is expected behavior.</span></span> <span data-ttu-id="cc08a-147">基於安全性理由，只有作用中的瀏覽器索引標籤可以存取 connected 耳機。</span><span class="sxs-lookup"><span data-stu-id="cc08a-147">For security reasons, only the active browser tab can access connected headsets.</span></span>

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a><span data-ttu-id="cc08a-148">為什麼我無法聆聽特定 WebVR 體驗的音訊</span><span class="sxs-lookup"><span data-stu-id="cc08a-148">Why can't I hear audio on a particular WebVR experience</span></span>

<span data-ttu-id="cc08a-149">網站可能使用 OGG 音訊檔案格式，Microsoft Edge 目前不支援此格式。</span><span class="sxs-lookup"><span data-stu-id="cc08a-149">The website may be using the OGG audio file format, which Microsoft Edge doesn't currently support.</span></span>

<span data-ttu-id="cc08a-150">您可以直接向 [問題追蹤](https://developer.microsoft.com/microsoft-edge/platform/issues/)程式中的 Microsoft Edge 瀏覽器小組報告已中斷的網站，或使用 [#EdgeBug](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)主題標籤，透過 twitter 來回報。</span><span class="sxs-lookup"><span data-stu-id="cc08a-150">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a><span data-ttu-id="cc08a-151">為什麼 haptic 意見反應無法在使用移動控制器的 WebVR 中運作</span><span class="sxs-lookup"><span data-stu-id="cc08a-151">Why does haptic feedback not work in WebVR with motion controllers</span></span>

<span data-ttu-id="cc08a-152">Microsoft Edge 目前不支援 WebVR 遊戲台 API 擴充功能上的 haptics。</span><span class="sxs-lookup"><span data-stu-id="cc08a-152">Microsoft Edge doesn't currently support haptics on the WebVR gamepad API extensions.</span></span>