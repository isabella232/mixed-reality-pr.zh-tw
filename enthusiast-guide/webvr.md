---
title: 使用 WebVR 搭配 Windows Mixed Reality
description: 瞭解 WebVR 的基本概念、如何搭配 Windows Mixed Reality 耳機的 Microsoft Edge 以及常見的疑難排解問題。
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，WebVR，Edge，Microsoft Edge，網頁流覽
ms.openlocfilehash: 89d9e51bf4adb63e7836968a0112849f7ac403d0
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581757"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>使用 WebVR 搭配 Windows Mixed Reality

>[!IMPORTANT]
>大部分的新式網頁瀏覽器都已淘汰 WebVR 的支援，以促進 WebXR，這是建立 VR 耳機之沉浸式 web 體驗的新標準。 請安裝 [新的 Microsoft Edge](using-microsoft-edge.md) 以 WebXR 支援。

## <a name="what-is-webvr"></a>什麼是 WebVR

[WebVR](https://webvr.info) 是一種開放的規格，可讓您直接從瀏覽器體驗 VR。 如果網站實行 WebVR 支援並提供3D 內容，它可以在耳機中顯示沉浸式內容，並提供使用者同意。

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>在 VR 中 WebVR 和流覽 web 有何不同

WebVR 是一種技術，可讓網站作者將 VR 功能新增至網頁。 頁面會使用 WebVR API 來顯示3D 內容 (例如360度的影片、3D 模型，或整個耳機) 的3D 遊戲。 **範例：** 在 [cnn.com/vr](http://cnn.com/vr)上觀看360影片。 如果頁面支援 WebVR，則會新增按鈕或其他 UI 元素，讓您可以選取以輸入 VR。

在 VR 中流覽 web 表示在您佩戴耳機時使用 Edge 瀏覽器，這是 Cliffhouse 內的2D 應用程式平板。

## <a name="do-all-websites-support-webvr"></a>所有網站都支援 WebVR

不會。 網站作者必須選擇使用 WebVR，而且他們可以針對特定的瀏覽器、耳機和控制器建立優化的網站。 某些 WebVR 內容僅適用于 mobile VR 裝置。 此外，請記住，網站必須明確建立並提供 WebVR 內容。 有一些 WebVR 相容內容的網站數目每天都會成長。

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>我可以使用 Vive/Oculus 等來查看 Microsoft Edge 中的 WebVR 內容

不會。 需要 Windows Mixed Reality 耳機才能在 Edge 中使用 WebVR。 不過，您可以在另一個瀏覽器中存取 WebVR 內容;請參閱下列網址的完整相容裝置和瀏覽器清單： [WebVR. rocks](http://webvr.rocks/)。

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>我可以在哪裡找到 WebVR 開發人員檔

開發人員檔位於此處： [WebVR 開發人員檔](/microsoft-edge/webvr/)。

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>我發現有 WebVR 的網站在 Windows Mixed Reality 中無法運作。 我該怎麼辦

您可以直接向 [問題追蹤](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)程式中的 Microsoft Edge 瀏覽器小組報告已中斷的網站，或使用 [#EdgeBug](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)主題標籤，透過 twitter 來回報。

您也可以使用類別目錄下的 Windows 意見反應中樞應用程式來記錄 bug：

Microsoft Edge > 網站問題

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>如果 WebVR 正常運作，要測試什麼是不錯的頁面

請參閱 [webvr.info 範例](http://webvr.info/samples/XX-vr-controllers.html)。

## <a name="how-do-i-set-up-webvr"></a>如何? 設定 WebVR

若要在 Windows Mixed Reality 耳機 (使用硬體或模擬) 來體驗 WebVR 內容，您必須：

1. 確定您的耳機已連線。
2. 在桌面上或在混合現實中啟動 Microsoft Edge。
3. 流覽至已啟用 WebVR 的頁面。
4. 選取頁面中的 [輸入 VR] 按鈕 (此按鈕的位置和視覺標記法可能會因每個網站) 而有所不同。 它看起來可能類似： \
   ![VR Goggles 映射](images/75px-enter-vr.png)
5. 當您第一次嘗試在特定網域上輸入 VR 時，瀏覽器會要求同意使用沉浸式視圖，請選取 [是]： ![第一次嘗試在特定網域上輸入 VR 時所顯示的同意 UI](images/1053px-Webvr-consent-ui.png)
6. 您的耳機應該會開始顯示 WebVR 內容。

## <a name="see-also"></a>另請參閱

* [針對 > WebVR 進行疑難排解](webvr-questions.md)
* [如何進入您的第一個 WebVR 體驗](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [在 Windows Mixed Reality 中使用遊戲和應用程式](using-games-and-apps-in-windows-mixed-reality.md)
* [您的混合現實首頁](your-mixed-reality-home.md)
* [追蹤系統](tracking-system.md)
* [移動控制器](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [歸檔意見反應](filing-feedback.md)