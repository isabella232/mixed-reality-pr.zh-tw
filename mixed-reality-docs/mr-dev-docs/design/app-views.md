---
title: 應用程式檢視
description: 瞭解如何在 Windows Mixed Reality apps 中使用兩種類型的視圖-沉浸式視圖和2d 視圖。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式觀賞、2d 視圖、平板、應用程式、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 1f779749938bfc8893f0e1f1f60c97549d30a24075b5b0926af61e2f88625b9c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191504"
---
# <a name="app-views"></a>應用程式檢視

Windows 應用程式可包含兩種視圖：**沉浸式視圖** 和 **2d 視圖**。 應用程式可以在其各種沉浸式和2D 視圖之間切換，在監視器上以視窗或在耳機中顯示2D 的視圖。 至少有一個沉浸式視圖的應用程式會分類為 **混合現實應用程式**。 絕對不具沈浸式檢視的應用程式則為 **2D 應用程式**。

## <a name="immersive-views"></a>沉浸式視圖

沈浸式檢視讓您的應用程式能夠在您周圍的世界中建立全像投影，或讓使用者沉浸於虛擬環境中。 當應用程式在沉浸式視圖中繪圖時，不會同時在多個應用程式的相同時間內同時繪製其他應用程式 &mdash; 。 藉由持續調整您的 [應用程式呈現](../develop/platform-capabilities-and-apis/rendering.md) 其場景的觀點，以符合使用者的前端移動，您的應用程式可以呈現 [世界鎖定](coordinate-systems.md) 的全像。 全球鎖定的全像是在真實世界中的固定點，也可以呈現在使用者移動時保存其位置的虛擬世界。

![當您在沉浸式觀賞時，可在世界各地放置全像移動。](images/designoverview-940px.jpg)<br>
*當您在沉浸式觀賞時，可以在世界各地放置全像*

在[HoloLens](/hololens/hololens1-hardware)上，您的應用程式會在使用者的真實世界周圍呈現其全像投影。 在[Windows Mixed Reality 的沉浸式耳機](../discover/immersive-headset-hardware-details.md)上，使用者看不到真實的世界，因此您的應用程式必須呈現使用者會看到的所有內容。

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) (包括您在環境中所放置的 [開始] 功能表和全像投影，) 不會在沉浸式觀賞的情況下呈現。 在 HoloLens 上，Cortana 會轉送沉浸式視圖顯示時所發生的任何系統通知，讓使用者可以用語音輸入回應。

在沉浸式視圖中，您的應用程式也會負責處理所有輸入。 Windows Mixed Reality 中的輸入是由[注視](gaze-and-commit.md)、[手勢](gaze-and-commit.md#composite-gestures) (HoloLens 只) 、[語音和[移動控制器](motion-controllers.md) (僅限沉浸式耳機) 。

## <a name="2d-views"></a>2D 視圖

![在 Windows Mixed Reality 首頁周圍設定的多個2d 視圖](images/teleportation-940px.png)<br>
*多個應用程式，並在 Windows Mixed Reality 首頁周圍放置2d 視圖*

具有2d 視圖的應用程式會出現在[Windows Mixed Reality 首頁](../discover/navigating-the-windows-mixed-reality-home.md) (有時稱為「shell」 ) 作為虛擬平板，並隨著應用程式啟動器和使用者在世界各地的其他全息圖一起轉譯。 使用者可以調整此一小平板，以移動和調整其大小，不過它會維持固定的解析度（無論其大小為何）。 如果您的應用程式第一個視圖是2D 視圖，您的2D 內容將會填滿用來啟動應用程式的相同平板電腦。

在桌上型耳機中，您現在可以執行任何通用 Windows 平臺在桌面監視器上執行的 (UWP) 應用程式。 這些應用程式現在已在繪製2D 視圖，而且其內容會在啟動時自動顯示在使用者世界的平板中。 2D UWP 應用程式可將目標設為 **Windows。通用** 裝置系列可在桌上型耳機和 HoloLens 上以平板的形式執行。

2D 視圖的一個主要用途是顯示使用系統鍵盤的文字輸入表單。 由於 shell 無法在沉浸式視圖上轉譯，因此應用程式必須切換至2D 視圖，以顯示系統鍵盤。 想要接受文字輸入的應用程式，必須使用文字方塊切換至2D 視圖。 當該文字方塊具有焦點時，系統會顯示系統鍵盤，讓使用者輸入文字。

應用程式可以在桌上型電腦監視器和桌上型電腦上的連接耳機中，擁有2D 的視圖。 例如，您可以使用主要2D 視圖來流覽桌面監視器上的邊緣，以找出360度的影片。 當您播放該影片時，Edge 將會在耳機內啟動次要的沉浸式觀賞，以顯示沉浸式影片內容。

## <a name="see-also"></a>另請參閱

* [應用程式模型](app-model.md)
* [更新混合實境的 2D UWP 應用程式](../develop/porting-apps/building-2d-apps.md)
* [取得 HolographicSpace](../develop/native/getting-a-holographicspace.md)
* [瀏覽 Windows Mixed Reality 住家](../discover/navigating-the-windows-mixed-reality-home.md)
* [混合實境應用程式類型](types-of-mixed-reality-apps.md)