---
title: 案例研究-在 RoboRaid 中使用空間音效
description: 空間音效是 Microsoft HoloLens 的最令人興奮的功能之一，可讓使用者在物件不可見時觀察到它們的周圍內容。
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、RoboRaid、空間音效、混合現實耳機、Windows Mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、cpu
ms.openlocfilehash: f4a47fe119dffbd32d264cc8e21ae2b3ade7cfcccef8e7e18fbb4491783d0542
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208992"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>案例研究-在 RoboRaid 中使用空間音效

本文說明在針對[RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) mixed reality first person 射擊建立音訊時，小組面臨的 Microsoft HoloLens 體驗挑戰。

## <a name="the-tech"></a>技術

[空間音效](spatial-sound.md)是 Microsoft HoloLens 最令人興奮的功能之一，可讓使用者在沒有物件的情況下，察覺到他們的工作。

在 RoboRaid 中，最明顯且有效的空間音效用途，是提醒播放程式發生在其周邊視覺以外的地方。 例如，Breacher 可以輸入房間內掃描的任何牆。 如果您不想知道其進入的位置，可能會錯過。 若要向您發出此目睹的警示，您會聽到來自 Breacher 輸入位置的相異音訊，讓您知道您需要快速採取行動來停止。

## <a name="behind-the-scenes"></a>在幕後

為 HoloLens 應用程式建立空間音效的原因很新，而且獨特的問題可能很難解決，因為沒有任何過去的專案需要參考。 希望這些在進行 RoboRaid 時所面臨的音效挑戰範例，可協助您建立自己應用程式的音訊。

### <a name="be-mindful-of-taxing-the-cpu"></a>留意 CPU 的負擔

空間音效可能會要求 CPU。 對於忙碌的 RoboRaid，在任何指定時間將空間音效實例的數目維持在八個底下是很重要的。 通常，它就像設定不同音訊事件的實例限制一樣簡單。 在達到限制之後發生的任何實例都會被終止。 例如，無人機產生時，在任何指定時間，其 screams 會限制為三個實例。 只考慮有四個無人機可以產生一次，三個 screams 很多，因為您的大腦無法追蹤許多類似發音的音訊事件。 這會釋出其他空間音效事件的資源，例如敵人爆炸或敵人準備進行。

### <a name="rewarding-a-successful-dodge"></a>獎勵成功的減減

躲過技師修理是 RoboRaid 中最重要的遊戲機制之一，也是我們認為真正獨特的 HoloLens 體驗。 因此，我們想要讓玩家順利 dodges。 我們 Doppler 「whizz 者」在開發過程中的初期很吸引人。 一開始，我的計畫是使用迴圈，並使用音量、音調和篩選來即時操作它。 這項作業的執行非常複雜。 在認可資源以建立這項功能之前，我們使用了 Doppler 效果內建的資產建立了一個便宜的原型，以找出它的感覺。 我們的優秀開發人員讓此 whizz 的資產在 projectile 通過播放程式的 ear 之前，會播放正好0.7 秒，而結果則令人驚奇！ 不用說，我們拋棄了更複雜的方案，並實作為原型。

*(如需有關使用內建 Doppler 效果建立音訊資產的詳細資訊，請參閱 [2 分鐘內的 100 Whooshes](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/)。 )* 
<br>
![成功躲過敵人的 projectile 利用符合 whizz 的音效來獎勵玩家。](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>拋棄失效音效

一開始，我們想要在播放程式成功 dodged 敵人 projectile 後播放爆炸音效，但我們決定基於數個原因來揚棄。 首先，它並不像我們用來進行減至 whizz 的 SFX 一樣有效率。 當 projectile 碰到您背後的牆時，遊戲中的其他東西可能會遮罩該音效。 其次，我們的樓層沒有任何衝突，因此當 projectile 碰到地面而非牆壁時，我們就無法讓您播放激增。 最後，空間音效的 CPU 成本也是如此。 Scorpion 敵人 (可以在牆內進行編目的資訊，) 有一項特殊攻擊，寄大約八炮彈。 這並不只是造成混合的巨大改變，也引進了一種劈啪聲，因為它的 CPU 太困難。

### <a name="communicating-a-hit"></a>傳達命中

我們在 HoloLens 上遇到的一個有趣問題，就是能夠有效地傳達玩家的通訊難度。 混合現實體驗的成功之處，就是您覺得案例正在發生。 這表示您必須在自己的客廳中，相信您正在對抗一間的機器人目睹。

當玩家遇到問題時，他們顯然不會覺得任何東西，因此我們必須找出一種方法來說服玩家發生錯誤。 在傳統遊戲中，您可能會看到一個動畫，讓您知道您的字元已被叫用，或螢幕可能會閃爍紅色，而您的字元可能有點 grunt。 由於這些類型的提示在混合的現實體驗中無法運作，因此我們決定將視覺提示與放大的音效合併，以指出您已損毀。 我建立了一個很大的音效，讓它在混合 ducked 所有專案的情況下變得很明顯。 然後，為了讓它更有意義，我們新增了一個短暫的警告音效，就像是要接收到一個 
<br>
![當播放程式在 RoboRaid 中叫用時，會看到視覺提示，但也會收到放大的音訊提示，告知他們已損毀。](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>從小型喇叭取得大音效

HoloLens 的喇叭很小，且符合裝置的需求，因此您無法預期會聽到太多的低終端。 類似于為智慧型手機或掌上型遊戲裝置進行開發，音效設計工具和作曲家必須留意音訊的頻率內容。 我總是設計音效或以完整頻率範圍撰寫音樂，因為戴耳機是使用者的選項。 不過，為了確保與 HoloLens 喇叭的相容性，我偶爾會在進行工作的任何白苗文的主伺服器上放置 EQ，以執行測試。 EQ 設定是由大約 600 Hz 到 700 Hz 的高通過篩選器所組成 () 和低傳遞篩選器，大約是1萬 (陡) 。 這應該能讓您大致瞭解聲音在裝置上的播放方式。

如果您想要使用低音來提供您的音樂中的弦變更，您可能會發現當您套用此 EQ 設定時，您的音樂完全失去了根目錄的意義。 為了解決這個情況，我將另一層新增至低音，也就是一個 octave (有一些豐富的諧波) ，並混用它來瞭解 root 的意義。 有時候，使用失真來 amp 諧波，會在上半部提供足夠的頻率內容，讓我們的大腦覺得它下有一些東西。 這適用于 SFX、爆炸或音效等的特殊時刻（例如老闆的超級攻擊）。 您真的無法依賴低端來讓玩家有影響或權數的意義。 與音樂一樣，使用失真讓某些 crunch 絕對有説明。

### <a name="making-your-audio-cues-stand-out"></a>讓您的音訊提示更醒目

當然，小組中的每個人都想要 bombastic 音樂、大聲主張和奇怪的爆炸;但是他們也希望能夠聽到 voiceover 或任何其他遊戲關鍵的音訊提示。

在具有完整頻率範圍的主控台遊戲中，您有更多選項可以根據音效的重要性來劃分頻率。 對 RoboRaid 來說，我的頻率範圍有限，我可以從音效曲線。 如果您在範圍較高的範圍內使用低通過篩選和曲線，您將不會有任何剩餘的聲音，因為沒有太多的低端。

若要讓 RoboRaid 音效盡可能地在裝置上變得很大，我們必須降低整個體驗的動態範圍，並藉由為不同類型的音效建立明確的重要性階層，來廣泛使用回避。 我根據重要性將回避從-2 dB 設定為-6 dB。 我個人並不喜歡遊戲中的明顯回避，所以我花了很多時間來微調淡入/退出時間以及音量衰減量。 我們針對空間音效、非空間音效、VO 和幹匯流排設定個別的匯流排，而不會有音樂的回音。 然後，我們建立了高優先順序、關鍵和非關鍵的匯流排，讓資產設定為進入適當的匯流排。

我希望音訊專業人員在處理自己的應用程式時，會有很多有趣和驚喜，因為我在 RoboRaid 上工作。 我無法再看看 (並聽聽！ ) Microsoft 的共同員工將如何 HoloLens。

## <a name="do-it-yourself"></a>親自完成

我發現要讓特定事件 (（例如，爆炸) 音效「更大」）（像是填滿房間）的一個訣竅，就是為空間音效建立 mono 資產，並混用2D 身歷聲資產，以3D 播放。 它的確需要進行一些調整，因為身歷聲內容中有太多資訊會減少 mono 資產的方向。 不過，取得餘額將會產生很大的音效，讓玩家以正確方向來轉換其標頭。

您可以使用下列音訊資產自行試用音效：

**案例 1**
1. 下載 [roboraid_enemy_explo_mono .wav](images/roboraid-enemy-explo-mono.wav) ，並設定為透過空間音效播放，並將其指派給事件。
2. 下載 [roboraid_enemy_explo_stereo .wav](images/roboraid-enemy-explo-stereo.wav) ，並將其設定為在2d 身歷聲中播放，並指派給上述的相同事件。 因為這些資產會正規化為 Unity，所以 attenuate 兩個資產的數量，使其不會被裁剪。
3. 同時玩這兩個音效。 移動您的頭部，以感受空間的音效。

**案例 2**
1. 下載 [roboraid_enemy_explo_summed .wav](images/roboraid-enemy-explo-summed.wav) ，並設定為透過空間音效播放並指派給事件。
2. 自行播放此資產，然後將其與案例1中的事件進行比較。
3. 試用 mono 和身歷聲檔案的不同餘額。

## <a name="see-also"></a>另請參閱

* [空間音效](spatial-sound.md)
* [Microsoft HoloLens 的 RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
