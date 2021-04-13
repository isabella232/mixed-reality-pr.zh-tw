---
title: 佈告板和常駐標籤
description: 瞭解如何搭配使用物件與 billboarding，這一律會將自己導向至混合現實應用程式中的使用者。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、billboarding、加上標籤、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、Mixed Reality 工具組
ms.openlocfilehash: 48c7aa28217a38c6c226b65a6e16ed7c950cec59
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299883"
---
# <a name="billboarding-and-tag-along"></a>佈告板和常駐標籤

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>什麼是 billboarding？

Billboarding 是一種行為概念，可套用至混合現實中的物件。 具有 billboarding 的物件一律會導向至臉部給使用者。 文字和功能表系統是常見的使用案例，也就是在使用者環境中放置的靜態物件 (世界鎖定的) 在使用者四處移動時，會隱藏或無法讀取。

啟用 billboarding 的物件可以在使用者的環境中自由旋轉。 根據設計考慮，也可以限制為單一軸。 請記住，billboarded 物件可能會在放置太接近其他物件的位置，或在 HoloLens 中太接近掃描的表面時，自行裁剪或遮蔽。 若要避免這種情況，請考慮物件在啟用軸旋轉以進行 billboarding 時，可能會產生的總使用量。

<br>

---
## <a name="what-is-a-tag-along"></a>什麼是標記？

標記-也是可以新增至全像影像的行為概念。 以標記為物件的物件會嘗試停留在某個範圍內，讓使用者能夠輕鬆互動。

![HoloLens 釘選面板是標記的運作方式的絕佳範例](images/tagalong-1000px.jpg)<br>
*HoloLens [開始] 功能表是標記與行為的絕佳範例*

加上標籤的物件有參數，可以微調其行為方式。 當使用者在其環境中四處移動時，內容可能會在使用者的看到行中或不存在。 當您移動時，內容會藉由滑動到視圖的邊緣來嘗試停留在使用者的其邊界中。 根據使用者的移動速度而定，內容可能會暫時無法觀看。 當使用者 gazes 到加上標籤的物件時，它會更完整地顯示。 您可以將內容視為「立即消失」，讓使用者永遠不會忘記其內容的方向。

額外的參數可讓以標記為依據的物件操作，透過橡膠波段連接到使用者的標頭。 抑制加速或減速可為物件提供權數，讓它更實際呈現。 這種彈簧行為是一種 affordance，可協助使用者建立標記與運作方式的精確精神模型。 當使用者在標記式模式中具有物件時，音訊有助於提供其他提示。 音訊必須強化移動的速度;快速的前端應該會提供更明顯的音效效果，而自然的速度應該會有最少量或沒有音訊效果。

就像真正的標頭鎖定內容一樣，標記物件可能會在使用者的觀點中變得太大或太多，而證明很大或 nauseating。 當使用者想要時，很快就會停止，並告訴他們已停止。 他們的平衡會通知他們其領導範圍已停止，且其願景會看到世界停止開啟。 但是，如果在使用者停止時將標籤與移動保持在一起，則可能會使其察覺混淆。

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Billboarding 和標記-沿著 MRTK (Unity 的混合現實工具組) 
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 會提供 Billboarding 的腳本，以及標記的行為。 將佈告欄腳本指派給任何物件，以新增 billboarding 行為，並讓物件永遠都有臉部。 若要加入標記的行為，請使用 RadialView .cs 腳本。 您可以調整各種選項，例如 lerping 時間、距離和角度。

* [MRTK-星形視圖求解](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK-佈告欄腳本](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>另請參閱

* [游標](cursors.md)
* [手部光線](point-and-commit.md)
* [Button](button.md)
* [可互動的物件](interactable-object.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手部功能表](hand-menu.md)
* [近端功能表](near-menu.md)
* [物件集合](object-collection.md)
* [語音命令](voice-input.md)
* [鍵盤](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑桿](slider.md)
* [著色器](shader.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [顯示進度](progress.md)
* [表面磁性](surface-magnetism.md)
