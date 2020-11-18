---
title: 應用程式檢視
description: Windows Mixed Reality apps 中的兩種視圖都是沉浸式視圖和2D 視圖。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式觀賞、2D 視圖、平板、應用程式、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 1380c32dc89e472428c86be30b2fce82a946f3cc
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702915"
---
# <a name="app-views"></a>應用程式檢視

Windows 應用程式可包含兩種類型的視圖： **沉浸式視圖** 和 **2d 視圖**。 應用程式可以在其各種沉浸式視圖和2D 視圖之間切換，在監視器上以視窗或在耳機中顯示2D 的視圖。 至少有一個沉浸式視圖的應用程式會分類為 **混合現實應用程式**。 從未具有沉浸式觀賞的應用程式是 **2d 應用程式**。

## <a name="immersive-views"></a>沉浸式視圖

沈浸式檢視讓您的應用程式能夠在您周圍的世界中建立全像投影，或讓使用者沉浸於虛擬環境中。 當應用程式在沉浸式視圖中繪圖時，不會同時在多個應用程式的相同時間內同時繪製其他應用程式 &mdash; 。 藉由持續調整您的 [應用程式呈現](../develop/platform-capabilities-and-apis/rendering.md) 其場景的觀點，以符合使用者的前端移動，您的應用程式可以呈現 [全球鎖定](coordinate-systems.md) 的全像位置，並保留在真實世界中的固定點，也可以呈現在使用者移動時保存其位置的虛擬世界。

![當您在沉浸式觀賞時，可在世界各地放置全像移動。](images/designoverview-940px.jpg)<br>
*當您在沉浸式觀賞時，可以在世界各地放置全像*

在 [HoloLens](https://docs.microsoft.com/hololens/hololens1-hardware)上，您的應用程式會在使用者的真實世界周圍呈現其全像影像。 在 [Windows Mixed Reality 沉浸式耳機](../discover/immersive-headset-hardware-details.md)上，使用者看不到真正的世界，因此您的應用程式必須呈現使用者會看到的所有內容。

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) (包括您在環境中所放置的 [開始] 功能表和全像投影，) 不會在沉浸式觀看時轉譯。 在 HoloLens 上，在顯示沉浸式視圖時所發生的任何系統通知都會由 Cortana 語音轉送，而使用者可以使用語音輸入來回應。

在沉浸式視圖中，您的應用程式也會負責處理所有輸入。 Windows Mixed Reality 的輸入是由 [注視](gaze-and-commit.md)、 [手勢](gaze-and-commit.md#composite-gestures) (HoloLens 所組成，只有) 、 [語音](voice-input.md) 和 [動作控制器](motion-controllers.md) (沉浸式耳機) 。

## <a name="2d-views"></a>2D 視圖

![在 Windows Mixed Reality 首頁周圍設定的多個2D 視圖](images/teleportation-940px.png)<br>
*多個應用程式，並在 Windows Mixed Reality 首頁周圍放置2D 視圖*

具有2D 視圖的應用程式會出現在 [Windows Mixed Reality 首頁](../discover/navigating-the-windows-mixed-reality-home.md) (有時稱為「shell」 ) 作為虛擬平板，並隨著應用程式啟動器和使用者在世界各地的其他全息圖一起轉譯。 使用者可以調整這個小程式來移動和調整它的大小，但不論其大小為何，都維持固定的解析度。 如果您的應用程式第一個視圖是2D 視圖，您的2D 內容將會填滿用來啟動應用程式的相同平板電腦。

在桌上型耳機中，您現在可以執行任何通用 Windows 平臺在桌面監視器上執行的 (UWP) 應用程式。 這些應用程式現在已在繪製2D 視圖，而且其內容會在啟動時自動顯示在使用者世界的平板中。 2D UWP 應用程式可將目標設為 **Windows 通用** 裝置系列，以在桌上型耳機和 HoloLens 上以平板的形式執行。

2D 視圖的一個主要用途是顯示可利用系統鍵盤的文字輸入表單。 由於 shell 無法在沉浸式視圖上轉譯，因此應用程式必須切換至2D 視圖，以顯示系統鍵盤。 想要接受文字輸入的應用程式可以使用文字方塊切換至2D 視圖。 當該文字方塊具有焦點時，系統會顯示系統鍵盤，讓使用者輸入文字。

請注意，在桌上型電腦上，應用程式可以在桌上型電腦監視器和附加耳機中都有2D 的視圖。 例如，您可以使用主要2D 視圖來流覽桌面監視器上的邊緣，以找出360度的影片。 當您播放該影片時，Edge 將會在耳機內啟動次要的沉浸式觀賞，以顯示沉浸式影片內容。

## <a name="see-also"></a>另請參閱

* [應用程式模型](app-model.md)
* [更新混合實境的 2D UWP 應用程式](../develop/porting-apps/building-2d-apps.md)
* [取得 HolographicSpace](../develop/native/getting-a-holographicspace.md)
* [瀏覽 Windows Mixed Reality 住家](../discover/navigating-the-windows-mixed-reality-home.md)
* [混合實境應用程式類型](types-of-mixed-reality-apps.md)
