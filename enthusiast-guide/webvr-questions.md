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
# <a name="webvr-faqs"></a>WebVR 常見問題

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>為什麼我在從 Edge 查看 VR 內容時看不到我的控制器

並非所有 WebVR 內容都是為了支援移動控制器而撰寫的。 WebVR 可讓內容開發人員支援不同類型的輸入，例如遊戲控制器或動作控制器。 如果您在網站上看不到您的控制器，則可能沒有動作控制器支援。

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>為什麼我無法在沉浸式 WebVR 視圖中使用滑鼠

這是 WebVR 規格的選擇性功能。 並非所有瀏覽器都支援這項功能，而且並非所有 WebVR 內容都是為了支援滑鼠輸入而撰寫的。 WebVR 可讓內容開發人員支援不同類型的輸入，例如滑鼠、鍵盤、遊戲控制器或移動控制器。 滑鼠輸入行為會依瀏覽器而有所不同。 在 Microsoft Edge 中，網站作者必須確保在向耳機呈現時，會使用「pointerlock」來執行滑鼠輸入。

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>為什麼我無法從 Youtube/Facebook/Vimeo/守護者查看360度的影片，而是在 VR 中從 Edge 查看

有一種 WebVR 規格，可讓網站直接從瀏覽器啟動 VR 體驗，而這些網站的作者目前尚未執行此規格。 某些平臺上可能會有可下載的應用程式，可讓您從這些廠商查看 VR 內容。

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>為什麼我無法從 Firefox 或 Chrome 輸入 VR

目前只有 Edge Windows Mixed Reality 裝置才支援 WebVR。

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>當我從網站輸入 VR 時，為什麼我會在耳機中看到空白畫面

網站可能尚未支援多 GPU 機器 (包括混合式 GPU 膝上型電腦) 。 嘗試：

* 重新載入頁面。
* 在桌上型電腦上，將耳機插入與顯示 Microsoft Edge 的監視器相同的圖形介面卡中。 將兩者插入至較高的電源圖形配接器，而不是整合式圖形介面卡。

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>當我在從 Edge 觀看影片時結束 VR 時，音效會持續播放，但邊緣視窗會呈現灰色

這是在混合現實懸崖之屋中從邊緣執行 WebVR 時的已知問題。 若要解決此問題，請在鍵盤上按下 esc 鍵，而不是按下 [windows] 按鈕以結束 WebVR 體驗，或是選取它，然後停止影片來啟用灰色的邊緣視窗。

## <a name="can-i-use-webvr-on-the-hololens"></a>我可以在 HoloLens 上使用 WebVR

Microsoft 目前尚未在 HoloLens 上宣佈任何關於 WebVR 的資訊。

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>當您從邊緣觀看 WebVR 內容時，為什麼我的視圖位於樓層層級

網站未適當支援 Windows Mixed Reality 耳機。 若要解決這個問題︰

1. 將耳機放在您的空間地板上。
2. 使用桌面上的 Microsoft Edge 流覽至 [WebVR] 頁面， (不在混合現實) 內。
3. 選取 [輸入 VR]。
4. 等候五至10秒，讓體驗完全進入沉浸式模式。
5. 放在耳機上。

## <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>在某些 WebVR 體驗中，顯示器的解析度非常低

這些網站未適當支援高解析度耳機。 若要解決此問題：

* 如果從 (桌面啟動 WebVR，而不是懸崖之屋) 的混合現實，請在選取 [Enter VR] 之前，先確定已將視窗最大化。
* 請避免在您輸入 VR 之後調整 Microsoft Edge 視窗的大小。

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>為什麼當我變更瀏覽器索引標籤時，WebVR 沉浸式視圖結束

這是正常的現象。 基於安全性理由，只有作用中的瀏覽器索引標籤可以存取 connected 耳機。

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>為什麼我無法聆聽特定 WebVR 體驗的音訊

網站可能使用 OGG 音訊檔案格式，Microsoft Edge 目前不支援此格式。

您可以直接向 [問題追蹤](https://developer.microsoft.com/microsoft-edge/platform/issues/)程式中的 Microsoft Edge 瀏覽器小組報告已中斷的網站，或使用 [#EdgeBug](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)主題標籤，透過 twitter 來回報。

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>為什麼 haptic 意見反應無法在使用移動控制器的 WebVR 中運作

Microsoft Edge 目前不支援 WebVR 遊戲台 API 擴充功能上的 haptics。