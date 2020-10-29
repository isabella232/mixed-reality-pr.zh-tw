---
title: 案例研究-針對 HoloTour 建立不可能的觀點
description: 我們希望您的 HoloTour 體驗成為難忘的 Microsoft HoloLens。 除了傳統旅遊停止時，我們還計畫了一些「不可能的觀點」。
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour、HoloLens、Windows Mixed Reality
ms.openlocfilehash: f3ca07dfab1e4477039481c268e418aac9034bc5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91682889"
---
# <a name="case-study---creating-impossible-perspectives-for-holotour"></a>案例研究-針對 HoloTour 建立不可能的觀點

我們希望您的 HoloTour 體驗成為難忘的 Microsoft HoloLens。 除了傳統的旅遊以外，我們還規劃了一些「不可能的觀點」，也就是不可能在任何導覽上體驗，而是透過 HoloLens 中的技術，可以直接帶到您的客廳。 建立這些體驗的內容需要一些不同的技術，而不是標準的捕獲程式。

## <a name="the-content-challenge"></a>內容挑戰

在 HoloTour 體驗中有某些場景（例如，在現代日期羅馬的熱空氣球，以及古羅馬 Colosseum 的 gladiatorial），提供您在其他地方都不會看到的獨特觀點。 這些時刻旨在激發和 amaze 您，而不只是教育經驗，讓您的旅程獲得 HoloTour。 這是我們想要記住的時刻，很高興能告訴其他人。 由於我們無法讓我們的攝影機設備進入天空，也沒有 () 主要旅程，因此每個「不可能的觀點」都是針對建立內容的特殊方法所呼叫。

## <a name="behind-the-scenes"></a>在幕後

建立這些獨特的時間和觀點，不僅需要 filming 和編輯而已。 這需要大量的時間、具有許多不同技能的人，以及稍微 Hollywood 魔術。

### <a name="viewing-rome-from-a-hot-air-balloon"></a>從熱的氣球觀賞羅馬

從我們早期的規劃日開始，我們知道我們想要在 HoloTour 中進行空出的觀點。 從天空觀看羅馬可提供您一種觀點，讓大部分的人都無法看到，以及瞭解熱門地標在空間上的位置。 試圖以我們現有的攝影機和麥克風 rig 來自我抓住，會很難處理，但幸好我們並不需要這麼做。

首先，請務必說明您在 HoloTour 中流覽的所有位置都有移動。 我們的目標是讓您「感覺像你真正的一樣」，因為您在現實生活中的任何地方都有移動，所以我們的虛擬目的地也需要傳達環境移動。 比方說，當您造訪 Pantheon 時，您會看到 wandering 在 plaza 中的人員，並整體性這些步驟。 背景動作可協助您感覺像是在位置，而不是暫存的靜態環境。

為了建立球形的空照圖，我們與 Microsoft 的其他小組合作，以存取羅馬的空照圖像。 這些影像的品質很棒，而且看起來很出色，但是當我們在幕後使用這些影像而不進行修改時，他們認為 lifeless 與導覽的其他部分不同，而缺乏的動作則不會造成干擾。 


![熱的氣球籃，浮動在羅馬上方。](images/hotairballoon1-300px.png)<br>
*熱的氣球形球籃，浮動于羅馬*

為了確保空的位置符合與其他目的地相同的品質，我們決定將靜態照片轉換成不斷變化的場景。 第一個步驟是在其中編輯影像和複合動作。 我們已為視覺效果建立了視覺效果，以協助我們進行此工作。 完成編輯是為了顯示雲端慢慢離開、鳥飛行，以及直升機到天際線的偶爾平面或。 在地面上，有許多車輛用來推動街道。 如果您已經在 HoloTour 的羅馬教學課程中，就不太可能明確地察覺這項移動。 其實很棒！ 微妙的動作並不是要吸引您的眼睛，但是如果沒有這一點，人們會立即注意到它是場景中的靜態影像。

我們所做的第二件事就是提供您一個有利點，從中查看場景。 如果您似乎只是浮動在 midair 中，就不會覺得您真正的樣子，因此我們建立了一個球的3D 模型，並將您放在裡面。 這可讓您逐一查看此氣球並查看邊緣，以取得更好的觀點。 我們發現這是體驗空拍影像的自然且有趣的方式。

熱音效球體驗為我們的音訊團隊帶來了獨特的挑戰，因為物流讓我們無法讓麥克風將數以千計的腳移到羅馬。 幸運的是，我們的所有城市都有大量的環境音效捕捉，我們可以在進入生產階段之後使用。 我們將音訊發射器放在從地面捕捉它們的相對位置。 然後，音訊會篩選成更遠的音效，就好像您是從騎在熱氣球的觀點來看，為場景提供真實的方向 soundscape。

### <a name="time-traveling-to-ancient-rome"></a>到達古羅馬的時間

在每個羅馬期間，歷史遺跡和大樓的其餘部分，在其建築之後會變得相當令人印象2000深刻，但我們知道我們有一份獨特的機會來告訴您，這會讓您回頭查看這些結構，並在古羅馬中看到這些結構。

當然，在 Colosseum 時看不到任何影片或靜態圖像) ，所以我們需要建立自己的影片。 我們必須進行許多研究，以深入瞭解結構的最大意義;瞭解它所做的教材、審視架構圖表，以及閱讀歷程記錄描述，以取得足夠的資訊來進行虛擬化。 

![Colosseum 的新式日毀損，其中的重迭顯示了在古的羅馬中所查看的樓層。](images/rome-colosseum-overlay-500px.png)<br>
*Colosseum 的新式日毀損，其中的重迭顯示在古羅馬中所查看的場地*

我們想要做的第一件事，就是使用教育重迭來增強傳統的導覽。 在 HoloTour 中，當您造訪 Colosseum 的毀損時，將會轉換為展示其在使用期間的樣子，包括精密的地下臨時區域。 在一般導覽中，您可能會有這項資訊，您可以嘗試想像它，但是在 HoloTour 中，您實際上可以看到它。

就像這樣的重迭，我們的演出者與我們的「捕捉」素材的觀點相符，並以手動方式建立重迭影像。 此觀點需要相符，因此當我們以影像取代影片時，兩者都會適當對齊。

### <a name="staging-the-gladiator-fight"></a>暫存 gladiator 打擊

雖然重迭是吸引人們參與歷程記錄的吸引人，但我們最興奮的是，我們會將您的資料傳輸回來。 覆迭只是來自特定觀點的靜止影像，但需要進行整個 Colosseum 模型化時，我們需要在場景中執行動作，才能讓它保持運作。 達到此目的需要相當多的精力。

這種情況對我們的團隊來說太大，因此我們的藝術團隊會使用 Whiskytree，這是一家通常適用于 Hollywood 電影視覺效果的外部效應公司。 Whiskytree 可協助我們在其 heyday 中重新建立 Colosseum，讓我們可以在您的場地間學習結構，並從天皇的箱建立 gladiator 打擊的觀點。 歡呼 crowds 和揮手橫幅會新增所需的微妙動作，使其感覺像是真正的地點，而不是影像。

![重新建立的 Colosseum，如從場地樓層所見。 當您在 HoloTour 中查看時，橫幅 flutter 在簡單的情況下，讓您感受到動作。](images/recreated-colosseum-holotour-500px.png)<br>
*重新建立的 Colosseum，如從場地樓層所見。當您在 HoloTour 中查看時，橫幅 flutter 在簡單的情況下，讓您感受到動作。*

使用 gladiator 對抗的羅馬最後導覽。 Whiskytree 為我們提供了轉譯為影片的場地和3D 對等模擬，但我們需要在各場所的 gladiators 中新增。 這部分的程式看起來更像是 Hollywood video 生產環境，而不是 incubation 遊戲工作室的專案。 我們團隊的成員對應了粗略的打擊順序，然後以 choreographer 進行調整。 我們雇用了執行者來暫存 mock 和購買的盔甲，使其看起來像這樣。 最後，我們會針對綠色畫面 filmed 整個場景。

![我們的 gladiators，取得之間的指示。](images/green-screen-gladiators-holotour-500px.jpg)<br>
*我們的 gladiatiors，取得之間的指示*

這個場景會將您放在天皇的方塊中，這表示所有所需的素材都必須從該觀點來看。 如果我們從 gladiators 在 filmed 中的哪一個位置開始，我們就無法在稍後正確地將對抗順序組成，所以我們將攝影機運算子放在高度剪下的剪下，以找出 filming 的對抗順序。

![取得正確的觀點：從剪增益 filming。](images/scissor-lift-holotour-500px.jpg)<br>
*取得正確的觀點：從剪增益 filming*

在生產環境中，gladiators 已合成至場地樓層，且觀點正確，但仍有一個問題： gladiators 在綠色畫面上的陰影已移除成為撰寫程式的一部分。 如果沒有遮蔽，則看起來像是 gladiators 在空氣中浮動。 幸好，Whiskytree 很適合用來解決這類問題，而是使用有點技術性的 wizardry 將陰影新增回場景中。 結果就是您今天在導覽中看到的結果。

## <a name="about-the-authors"></a>關於作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> 是一位資深開發人員，他們學到更多有關相機 rig 和影片播放的資訊，而不是他想像過 HoloTour。</td>

<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> 是一種音訊設計工具，可確保您可以體驗您所造訪之每個目的地的 soundscape，即使您回頭回來也是如此。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> 是一位影片演出者，可確保您的羅馬進度盡可能完美。</td>

<td style="border:0" width="60px"></td>
<td style="border:0" width="408"></td>
</tr>
</table>


## <a name="see-also"></a>另請參閱
* [影片： Microsoft HoloLens： HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
