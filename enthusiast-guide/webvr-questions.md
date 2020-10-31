---
title: WebVR 常見問題
description: 超越標準取用者支援檔的網路混合現實疑難排解。
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援、WebVR
ms.openlocfilehash: e03051008921f87e18cae3a9f6db369e54c56b94
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131932"
---
# <a name="webvr-faqs"></a><span data-ttu-id="3221b-104">WebVR 常見問題</span><span class="sxs-lookup"><span data-stu-id="3221b-104">WebVR FAQs</span></span>

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a><span data-ttu-id="3221b-105">為什麼我在從 Edge 查看 VR 內容時看不到我的控制器</span><span class="sxs-lookup"><span data-stu-id="3221b-105">Why can’t I see my controllers when viewing VR content from Edge</span></span>

<span data-ttu-id="3221b-106">並非所有 WebVR 內容都是為了支援移動控制器而撰寫的。</span><span class="sxs-lookup"><span data-stu-id="3221b-106">Not all WebVR content is authored to support motion controllers.</span></span> <span data-ttu-id="3221b-107">WebVR 可讓內容開發人員支援不同類型的輸入，例如遊戲控制器或動作控制器。</span><span class="sxs-lookup"><span data-stu-id="3221b-107">WebVR allows content developers to support different types of input, such as game controllers or motion controllers.</span></span> <span data-ttu-id="3221b-108">如果您在網站上看不到您的控制器，則可能沒有動作控制器支援。</span><span class="sxs-lookup"><span data-stu-id="3221b-108">If you do not see your controllers on a site, it probably doesn’t have motion controller support.</span></span>

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a><span data-ttu-id="3221b-109">為什麼我無法在沉浸式 WebVR 視圖中使用滑鼠</span><span class="sxs-lookup"><span data-stu-id="3221b-109">Why can't I use the mouse in an immersive WebVR view</span></span>

<span data-ttu-id="3221b-110">這是 WebVR 規格的選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="3221b-110">This is an optional feature of the WebVR specification.</span></span> <span data-ttu-id="3221b-111">並非所有瀏覽器都支援這項功能，而且並非所有 WebVR 內容都是為了支援滑鼠輸入而撰寫的。</span><span class="sxs-lookup"><span data-stu-id="3221b-111">Not all browsers support this feature, and not all WebVR content is authored to support mouse input.</span></span> <span data-ttu-id="3221b-112">WebVR 可讓內容開發人員支援不同類型的輸入，例如滑鼠、鍵盤、遊戲控制器或移動控制器。</span><span class="sxs-lookup"><span data-stu-id="3221b-112">WebVR allows content developers to support different types of input, such as mouse, keyboard, game controllers or motion controllers.</span></span> <span data-ttu-id="3221b-113">滑鼠輸入行為會依瀏覽器而有所不同。</span><span class="sxs-lookup"><span data-stu-id="3221b-113">Mouse input behavior varies per browser.</span></span> <span data-ttu-id="3221b-114">在 Microsoft Edge 中，網站作者必須確保在向耳機呈現時，會使用「pointerlock」來執行滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="3221b-114">Within Microsoft Edge, website authors must ensure they take 'pointerlock' when presenting to the headset for mouse input to work.</span></span>

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a><span data-ttu-id="3221b-115">為什麼我無法從 Youtube/Facebook/Vimeo/守護者查看360度的影片，而是在 VR 中從 Edge 查看</span><span class="sxs-lookup"><span data-stu-id="3221b-115">Why can’t I view 360 degree videos from Youtube/Facebook/Vimeo/The Guardian, etc. from Edge in VR</span></span>

<span data-ttu-id="3221b-116">有一種 WebVR 規格，可讓網站直接從瀏覽器啟動 VR 體驗，而這些網站的作者目前尚未執行此規格。</span><span class="sxs-lookup"><span data-stu-id="3221b-116">There is a WebVR specification that allows websites to launch VR experiences directly from the browser and the authors of these websites have not implemented this specification at this time.</span></span> <span data-ttu-id="3221b-117">某些平臺上可能會有可下載的應用程式，可讓您從這些廠商查看 VR 內容。</span><span class="sxs-lookup"><span data-stu-id="3221b-117">There may be downloadable apps on some platforms that enable viewing of VR content from these vendors.</span></span>

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a><span data-ttu-id="3221b-118">為什麼我無法從 Firefox 或 Chrome 輸入 VR</span><span class="sxs-lookup"><span data-stu-id="3221b-118">Why can’t I enter VR from Firefox or Chrome</span></span>

<span data-ttu-id="3221b-119">目前只有 Edge Windows Mixed Reality 裝置才支援 WebVR。</span><span class="sxs-lookup"><span data-stu-id="3221b-119">WebVR is only supported by Windows Mixed Reality devices in Edge at this time.</span></span>

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a><span data-ttu-id="3221b-120">當我從網站輸入 VR 時，為什麼我會在耳機中看到空白畫面</span><span class="sxs-lookup"><span data-stu-id="3221b-120">When I enter VR from a website, why do I see a blank screen in my headset</span></span>

<span data-ttu-id="3221b-121">網站可能尚未支援多 GPU 機器 (包括混合式 GPU 膝上型電腦) 。</span><span class="sxs-lookup"><span data-stu-id="3221b-121">The website may not have implemented support for multi GPU machines (including hybrid GPU laptops).</span></span> <span data-ttu-id="3221b-122">嘗試：</span><span class="sxs-lookup"><span data-stu-id="3221b-122">Try to:</span></span>

* <span data-ttu-id="3221b-123">重新載入頁面。</span><span class="sxs-lookup"><span data-stu-id="3221b-123">Reload the page.</span></span>
* <span data-ttu-id="3221b-124">在桌上型電腦上，將耳機插入與顯示 Microsoft Edge 的監視器相同的圖形介面卡中。</span><span class="sxs-lookup"><span data-stu-id="3221b-124">On desktop machines, plug the headset into the same graphics adapter as the monitor that is displaying Microsoft Edge.</span></span> <span data-ttu-id="3221b-125">將兩者插入至較高的電源圖形配接器，而不是整合式圖形介面卡。</span><span class="sxs-lookup"><span data-stu-id="3221b-125">Plug both into the higher powered graphics card, not into the integrated graphics adapter.</span></span>

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a><span data-ttu-id="3221b-126">當我在從 Edge 觀看影片時結束 VR 時，音效會持續播放，但邊緣視窗會呈現灰色</span><span class="sxs-lookup"><span data-stu-id="3221b-126">When I exit VR when watching a video from Edge, the sound continues playing but the Edge window is grayed out</span></span>

<span data-ttu-id="3221b-127">這是在混合現實懸崖之屋中從邊緣執行 WebVR 時的已知問題。</span><span class="sxs-lookup"><span data-stu-id="3221b-127">This is a known issue when running WebVR from Edge in the Mixed Reality Cliff House.</span></span> <span data-ttu-id="3221b-128">若要解決此問題，請在鍵盤上按下 esc 鍵，而不是按下 [windows] 按鈕以結束 WebVR 體驗，或是選取它，然後停止影片來啟用灰色的邊緣視窗。</span><span class="sxs-lookup"><span data-stu-id="3221b-128">To resolve it, press escape on the keyboard rather than pressing the windows button to exit the WebVR experience, or activate the greyed out Edge window by selecting it and then stop the video.</span></span>

## <a name="can-i-use-webvr-on-the-hololens"></a><span data-ttu-id="3221b-129">我可以在 HoloLens 上使用 WebVR</span><span class="sxs-lookup"><span data-stu-id="3221b-129">Can I use WebVR on the HoloLens</span></span>

<span data-ttu-id="3221b-130">Microsoft 目前尚未在 HoloLens 上宣佈任何關於 WebVR 的資訊。</span><span class="sxs-lookup"><span data-stu-id="3221b-130">Microsoft has not announced anything about WebVR on the HoloLens at this point.</span></span>

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a><span data-ttu-id="3221b-131">當您從邊緣觀看 WebVR 內容時，為什麼我的視圖位於樓層層級</span><span class="sxs-lookup"><span data-stu-id="3221b-131">Why is my view at floor level when viewing WebVR content from Edge</span></span>

<span data-ttu-id="3221b-132">網站未適當支援 Windows Mixed Reality 耳機。</span><span class="sxs-lookup"><span data-stu-id="3221b-132">The website does not properly support Windows Mixed Reality headsets.</span></span> <span data-ttu-id="3221b-133">若要解決這個問題︰</span><span class="sxs-lookup"><span data-stu-id="3221b-133">To work around this:</span></span>

1. <span data-ttu-id="3221b-134">將耳機放在您的空間地板上。</span><span class="sxs-lookup"><span data-stu-id="3221b-134">Place the headset on the floor of your space.</span></span>
2. <span data-ttu-id="3221b-135">使用桌面上的 Microsoft Edge 流覽至 [WebVR] 頁面， (不在混合現實) 內。</span><span class="sxs-lookup"><span data-stu-id="3221b-135">Navigate to the WebVR page using Microsoft Edge on your desktop (not within mixed reality).</span></span>
3. <span data-ttu-id="3221b-136">選取 [輸入 VR]。</span><span class="sxs-lookup"><span data-stu-id="3221b-136">Select "Enter VR".</span></span>
4. <span data-ttu-id="3221b-137">等候五至10秒，讓體驗完全進入沉浸式模式。</span><span class="sxs-lookup"><span data-stu-id="3221b-137">Wait five to 10 seconds for the experience to fully enter immersive mode.</span></span>
5. <span data-ttu-id="3221b-138">放在耳機上。</span><span class="sxs-lookup"><span data-stu-id="3221b-138">Put on the headset.</span></span>

## <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a><span data-ttu-id="3221b-139">在某些 WebVR 體驗中，顯示器的解析度非常低</span><span class="sxs-lookup"><span data-stu-id="3221b-139">The display is very low resolution in some WebVR experiences</span></span>

<span data-ttu-id="3221b-140">這些網站未適當支援高解析度耳機。</span><span class="sxs-lookup"><span data-stu-id="3221b-140">Those websites do not properly support high resolution headsets.</span></span> <span data-ttu-id="3221b-141">若要解決此問題：</span><span class="sxs-lookup"><span data-stu-id="3221b-141">To workaround this:</span></span>

* <span data-ttu-id="3221b-142">如果從 (桌面啟動 WebVR，而不是懸崖之屋) 的混合現實，請在選取 [Enter VR] 之前，先確定已將視窗最大化。</span><span class="sxs-lookup"><span data-stu-id="3221b-142">If launching WebVR from the desktop (rather than the mixed reality Cliff House), ensure the window is maximized before selecting "Enter VR".</span></span>
* <span data-ttu-id="3221b-143">請避免在您輸入 VR 之後調整 Microsoft Edge 視窗的大小。</span><span class="sxs-lookup"><span data-stu-id="3221b-143">Avoid resizing the Microsoft Edge window after you have entered VR.</span></span>

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a><span data-ttu-id="3221b-144">為什麼當我變更瀏覽器索引標籤時，WebVR 沉浸式視圖結束</span><span class="sxs-lookup"><span data-stu-id="3221b-144">Why does the WebVR immersive view exit when I change browser tabs</span></span>

<span data-ttu-id="3221b-145">這是正常的現象。</span><span class="sxs-lookup"><span data-stu-id="3221b-145">This is expected behavior.</span></span> <span data-ttu-id="3221b-146">基於安全性理由，只有作用中的瀏覽器索引標籤可以存取 connected 耳機。</span><span class="sxs-lookup"><span data-stu-id="3221b-146">For security reasons, only the active browser tab can access connected headsets.</span></span>

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a><span data-ttu-id="3221b-147">為什麼我無法聆聽特定 WebVR 體驗的音訊</span><span class="sxs-lookup"><span data-stu-id="3221b-147">Why can't I hear audio on a particular WebVR experience</span></span>

<span data-ttu-id="3221b-148">網站可能使用 OGG 音訊檔案格式，Microsoft Edge 目前不支援此格式。</span><span class="sxs-lookup"><span data-stu-id="3221b-148">The website may be using the OGG audio file format, which Microsoft Edge does not currently support.</span></span>

<span data-ttu-id="3221b-149">您可以直接向 [問題追蹤](https://developer.microsoft.com/microsoft-edge/platform/issues/)程式中的 Microsoft Edge 瀏覽器小組報告已中斷的網站，或使用 [#EdgeBug](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)主題標籤，透過 twitter 來回報。</span><span class="sxs-lookup"><span data-stu-id="3221b-149">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a><span data-ttu-id="3221b-150">為什麼 haptic 意見反應無法在使用移動控制器的 WebVR 中運作</span><span class="sxs-lookup"><span data-stu-id="3221b-150">Why does haptic feedback not work in WebVR with motion controllers</span></span>

<span data-ttu-id="3221b-151">Microsoft Edge 目前不支援 WebVR 遊戲台 API 擴充功能上的 haptics。</span><span class="sxs-lookup"><span data-stu-id="3221b-151">Microsoft Edge does not currently support haptics on the WebVR gamepad API extensions.</span></span>