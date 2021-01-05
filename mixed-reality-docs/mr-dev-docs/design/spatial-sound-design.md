---
title: 在混合現實應用程式中使用空間音效
description: 空間音效是深度、協助工具和 UX 設計在混合現實應用程式中的強大工具。
author: kegodin
ms.author: v-hferrone
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality、空間音效、設計、樣式、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、手勢、互動、衰減
ms.openlocfilehash: fe77d62bcdfc67579deee619fc7f4949676aaed6
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848182"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>如何在混合現實應用程式中使用音效

您可以使用音效來通知和強化使用者的應用程式狀態的精神模型。 適當時，請使用 spatialization 將聲音放在混合現實世界中。 當您以這種方式連接聽覺和視覺效果時，您可以加深互動的直覺本質，並提高使用者的信心。
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>新增聲音的時機

由於應用程式缺乏 tactile 介面，因此混合現實應用程式通常比2D 應用程式更需要音效。 當聲音通知使用者或強化互動時，請新增音效。

### <a name="inform-and-reinforce"></a>通知和強化

* 針對不是由使用者所起始的事件（例如通知），請使用音效通知使用者發生變更。
* 互動可能有數個階段。 使用音效強化階段轉換。

請參閱下列互動、事件和建議的音效特性範例。

### <a name="exercise-restraint"></a>克制

使用者沒有無限容量的音訊資訊。
* 每個音效都應該傳達特定、寶貴的資訊。
* 當您的應用程式播放音效來通知使用者時，請暫時減少其他音效的音量。
* 針對按鈕停留音效 (查看下列資訊) ，加入時間延遲以防止過多的音效觸發。

### <a name="dont-rely-solely-on-sounds"></a>不要完全依賴聲音

使用起來很重要的音效對您的使用者很有説明。 但請確定您的應用程式即使已關閉音效也可供使用。
* 使用者可能會被聽力受損。
* 您的應用程式可能會在較高的環境中使用。
* 使用者可能會有隱私權疑慮或其他停用裝置音訊的原因。

## <a name="how-to-sonify-interactions"></a>如何 sonify 互動

混合現實中的互動類型包括筆勢、直接操作和語音。 使用下列建議的特性來選取或設計這些互動的音效。

### <a name="gesture-interactions"></a>手勢互動

在混合的現實情況下，使用者可以使用滑鼠與按鈕互動。 按鈕動作通常會在使用者釋放時，而不是按下按鈕來讓使用者有機會取消互動。 使用音效來強化這些階段。 若要協助使用者以較遠的按鈕為目標，也請考慮使用指標停留音效。
* 按鈕-按下聲音應該是簡短的 tactile 「按一下」。<br/>範例： [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 按鈕-"unpress" 音效應該有類似的 tactile 風格。 比按音效更高的音調會強調完成的意義。<br/>範例： [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* 若為暫止音效，請考慮使用微妙且不危險的音效，例如低頻率的 thud 或凹凸效果。

### <a name="direct-manipulation"></a>直接操作

在 HoloLens 2 上，可說的手追蹤支援直接操作使用者介面元素。 當沒有其他實體意見反應時，音效就很重要。

*按鈕的按* 音效很重要，因為當使用者到達按鍵筆劃的底部時，不會收到任何其他指示。 關鍵旅遊的音效指標可能很小、微妙且 pixels occluded。 如同手勢互動，按下按鈕應該會得到短暫的 tactile 音效，像是按一下。 Unpresses 應該會有類似的點擊音效，但卻有凸起的音調。
* 範例： [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 範例： [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

很難以視覺化方式確認抓取或發行動作。 使用者的手通常會是任何視覺效果，而主體的物件缺乏真實的視覺類比「抓取」。 音效可以有效地傳達成功的抓取和發行互動。
* 抓取動作應該有簡短、有點 muffled 的 tactile 音效，以提示在物件周圍關閉手指的概念。 有時候也有一個「竊竊私語」音效，會導致抓取音效傳達手中的動作。<br/>範例： [MRTK_Move_Start .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* 發行動作應該會得到類似的簡短和 tactile 音效。 它通常會比抓取音效更低，而反向順序則會有影響，然後是「竊竊私語」，以傳達物件正在進行的程式。<br/>範例： [MRTK_Move_End .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

*繪圖* 互動應該會以使用者的移動量來取得持續的迴圈音效。 當使用者的手仍在移動時，當手 loudest 時，它應該是無訊息的。

### <a name="voice-interactions"></a>語音互動

語音互動通常有細微的視覺元素。 使用音效強化互動階段。 您可能會想要使用更音效的音效來區別它們與手勢和直接操作音效。

* 使用發音語氣來 *確認* 語音命令。 逐漸增加的聲音和主要的樂譜間隔都有效。
* 使用較短且較不正面發音的語音命令 *失敗* 語氣。 避免負聲音。 相反地，請使用更 percussive 的中性音效來與應用程式從互動中移動的通訊。
* 如果您的應用程式具有喚醒字，則在裝置 *開始接聽* 時，請使用短暫、溫和的語氣。 在 *應用程式接聽時使用* 微妙的迴圈音效。

### <a name="notifications"></a>通知

通知會通知應用程式狀態變更，以及使用者未起始的其他事件。 狀態變更可能包括處理常式完成、訊息和通話。

在混合的現實情況下，物件有時會移出使用者的觀點。 將移動 *動畫物件* 與 hrtf 音效（取決於物件類型和動作速度）配對。
* 它有助於在動畫結束時播放 hrtf 音效，以通知使用者物件的新位置。
* 針對漸進式移動，移動期間的「竊竊私語」音效可協助使用者追蹤物件。

*訊息通知* 音效可能會重複聽到，有時會快速地連續播放。 這一點很重要， 中等範圍正面的音效很有效率。

* 來電的音效應該與行動電話鈴聲具有類似的品質。 這些音效都是迴圈播放的音樂片語，直到使用者接聽電話為止。
* 語音通訊連線和中斷連接應該有短暫的音效音效。 連接音效應該是正面的語氣，表示連接成功。 中斷連線的音效應該是中性的音效，表示已完成通話。

## <a name="handle-spatialization"></a>處理 spatialization

Spatialization 使用身歷聲耳機或喇叭在混合現實世界中放置音效。

### <a name="which-sounds-to-spatialize"></a>要 spatialize 的音效

當音效與具有空間位置的事件相關聯時，就應該 hrtf 音效。 這包括 UI、所涵蓋的 AI 語音和視覺指標。

Spatialize *使用者介面* 元素，藉由限制發音音效的數目來協助清理使用者的「空間」。 在 hrtf 音訊意見反應時，操作互動（例如觸控、抓取及放開）感覺更自然。 請考慮下列有關這些元素的距離衰減資訊。

Spatialize *視覺* 指標和所指的 *AI 聲音* ，以直覺方式通知使用者這些專案位於視野之外。
    
相反地，請避免使用 spatialization 來 *FACELESS AI 語音* ，以及其他缺少妥善定義空間位置的元素。 Spatialization 如果沒有相關的視覺元素，可能會讓使用者在思考有一個視覺元素找不到。

Spatialization 會帶來一些 CPU 成本。 許多應用程式都有兩個同時播放的音效。 在該情況下，spatialization 的成本可能會是微不足道。 您可以使用 MRTK 畫面播放速率監視器來判斷新增 spatialization 的影響。

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>何時及如何套用以距離為基礎的衰減

在真實世界中，更不會的音效會更安靜。 您的音訊引擎可以根據來源距離來建立此衰減的模型。 使用以距離為基礎的衰減，以傳達相關資訊。

與 *視覺* 指標、 *動畫影像* 和其他資訊音效之間的距離，與使用者相關。 使用以距離為基礎的衰減，以直覺的形式提供提示。

調整每個來源的衰減曲線，以符合您的混合現實世界空間大小。 音訊引擎的預設曲線通常適用于大型的 (，最多可達半平方公里) 空間。

強化按鈕動作和其他互動 *之漸進階段* 的音效不應套用衰減。 這些音效的強化效果比傳達按鈕的距離更重要。 變化可能會受到干擾，尤其是鍵盤，可能會連續聽到許多按鈕點擊。

### <a name="which-spatialization-technology-to-use"></a>要使用的 spatialization 技術

使用耳機或 HoloLens 喇叭， (以) 為基礎的 spatialization 技術，請使用前端相關的轉移功能。 這些技術會針對實體世界中的標頭，建立音效傳播的模型。 即使音效來源位於某一端的一端，音效也會隨著衰減和延遲而散佈到遙遠的 ear。 說話者的移動只依賴衰減，並且在當音效位於右邊時，在左方的 ear 中套用總衰減。 這項技術對於「一般聽力」接聽程式很不舒服，而且在一個 ear 中有聽力障礙的接聽程式無法存取。

## <a name="next-steps"></a>後續步驟

* [在 Unity 中使用空間音效](../develop/unity/spatial-sound-in-unity.md)
* [Roboraid 案例研究](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour 案例研究](case-study-spatial-sound-design-for-holotour.md)
