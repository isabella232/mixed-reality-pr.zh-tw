---
title: 語音輸入
description: 語音輸入是 HoloLens 和 Windows Mixed Reality 沉浸式耳機的核心輸入。 語音可以用於命令、聽寫、Cortana 等等。
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv、語音、cortana、語音、輸入、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、注視
ms.openlocfilehash: f4f81383f942961857b088b05c4e8cac07ab7dfe
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703204"
---
# <a name="voice-input"></a>語音輸入

![語音輸入](images/UX_Hero_VoiceCommand.jpg)

語音是 HoloLens 輸入的其中一種主要形式。 它可讓您直接命令全息圖，而不需要使用 [手手勢](gaze-and-commit.md#composite-gestures)。 語音輸入是溝通意圖的一種自然方式。 語音在往返複雜介面時特別有用，因為它可讓使用者使用一個命令來剪下整個嵌套功能表。

語音輸入是由在所有其他 _通用 Windows 應用程式_ 中支援語音的 [相同引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)所驅動。 在 HoloLens 上，語音辨識一律會以設定中設定的 Windows 顯示語言運作。 

<br>

## <a name="voice-and-gaze"></a>語音和注視

使用語音命令時， (head 或眼睛) 眼通常會用來做為目的機制，不論是使用資料指標 ( 「選取」 ) 或將命令隱含地通道處理至您所查看的應用程式。 如此一來，甚至可能還不需要顯示任何 _看起來的游標 ( 「看起來」 )_。 當然，有些語音命令根本不需要目標，例如「移至開始」或「嗨 Cortana」。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>語音輸入</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>使用麥克風的✔️ () </td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select" 命令

**HoloLens (第 1 代)**

即使沒有特別為您的應用程式新增語音支援，您的使用者只要說出系統 voice 命令「select」就可以啟用全像。 這 [與在 hololens 上按](gaze-and-commit.md#composite-gestures) 下滑鼠的方式相同，在 [hololens clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上按下 [選取] 按鈕，或按 [Windows Mixed Reality 運動控制器](motion-controllers.md)上的觸發程式。 您將聽到音效，並看到具有 [選取] 的工具提示顯示為 [確認]。 「選取」是由低功率關鍵字偵測演算法所啟用，因此隨時都能以最少的電池生命週期來說，即使您手上也可以。

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        若要在 HoloLens 2 中使用 [選取] 語音命令，您必須先顯示要用來作為指標的注視游標。 要讓它啟動的命令很容易記住，只要說「select」就可以了。<br><br>
        若要結束此模式，只要使用您的手，就可以藉由按下滑鼠按鍵、使用手指接近按鈕，或使用系統手勢來退出。<br>
        <br>
        *影像：說「選取」以使用語音命令進行選取*
    :::column-end:::
        :::column:::
       ![使用者可以說「選取」以使用語音命令進行選取。](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a>嗨 Cortana

您也可以說「嗨 Cortana」以隨時帶出 Cortana。 您不必等待她繼續詢問您的問題，或為她提供指示，例如，嘗試說「嗨 Cortana，天氣是什麼？」。 作為單一句子。 如需 Cortana 和您可以做什麼的詳細資訊，請直接詢問她！ 說「嗨 Cortana，我可以說什麼？」 她將會提取一份工作和建議的命令清單。 如果您已經在 Cortana 應用程式中，也可以按一下 [ **？]。** 圖示，以提取這個相同的功能表。

**HoloLens 專用的命令**
* 「我可以說什麼？」
* 「移至開始」-而不是 [bloom](system-gesture.md#bloom) 來進入 [開始功能表](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)
* 「啟動 <app> 」
* 「移 <app> 至這裡」
* 「拍攝相片」
* 「開始錄製」
* 「停止錄製」
* 「顯示手邊的光線」
* 「隱藏手光線」
* 「提高亮度」
* 「降低亮度」
* 「增加磁片區」
* 「減少音量」
* 「靜音」或「取消靜音」
* 「關閉裝置」
* 「重新開機裝置」
* 「移至睡眠」
* 「這是什麼時候？」
* 「我剩下多少電池？」



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>「看它，說它」<br>
        HoloLens 具有語音輸入的「查看」模型，其中按鈕上的標籤會告訴使用者他們可以說的語音命令。 例如，查看 HoloLens 中的應用程式視窗時 (第1代) ，使用者可以說出他們在應用程式行中看到的「調整」命令，來調整世界上應用程式的位置。<br>
        <br>
        *影像：使用者可以說出他們在應用程式行中看到的「調整」命令，以調整應用程式的位置。*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![查看應用程式視窗或全像影像時，使用者可以說出他們在應用程式行中看到的「調整」命令，以調整應用程式在世界中的位置。](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        當應用程式遵循此規則時，使用者很容易就能瞭解如何控制系統。 若要強調這一點，在 HoloLens (第一代) 中的按鈕上撥雲見日時，如果按鈕為語音啟用，您將會看到「聲音停留」工具提示，並顯示「按下」所說的命令。 若要顯示 HoloLens 2 中的語音工具提示，請說「選取」或「我可以說什麼」來顯示語音游標 (請參閱影像) 。 <br>
        <br>
        *影像：「看到它，假設」命令出現在按鈕下方*
    :::column-end:::
        :::column:::
       ![查看它，假設命令出現在按鈕下方](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a>快速全息圖操作的語音命令

在撥雲見日時，您可以說一些語音命令，以快速執行操作工作。 這些語音命令適用于應用程式視窗，以及您放在世界各地的3D 物件。

**全息圖操作命令**
* 臉部
* 更大 |提高
* 小

在 HoloLens 2 上，您也可以結合眼睛來建立更自然的互動，以隱含的方式提供您所參考之內容的相關資訊。 例如，您可以只查看一個全息圖，然後說 _「放入_」，然後查看您要放置它的位置，然後說「在 _這裡_」。
或者，您可以在複雜的電腦上查看全像的部分，然後說：「給我更多關於 _這個_ 的資訊」。



## <a name="discovering-voice-commands"></a>探索語音命令

某些命令（例如上述快速操作的命令）可以隱藏。 若要瞭解您可以使用的命令，請在物件上看看，然後說「我可以怎麼說？」。 可能會快顯的命令清單。 您也可以使用前端指標來查看，並在您前面顯示每個按鈕的語音工具提示。 

如果您想要完整的清單，只要說「顯示所有命令」即可。 


## <a name="dictation"></a>聽寫

語音聽寫可以更有效率地在應用程式中輸入文字，而不是以 [空中](gaze-and-commit.md#composite-gestures)的方式輸入。 這可大幅加速輸入，讓使用者更不費力。

![語音聽寫會從選取麥克風按鈕開始](images/micbuttonfordictation.png)<br>
*語音聽寫的開頭是選取鍵盤上的麥克風按鈕*

任何時候全像全像鍵盤都處於使用中狀態時，您都可以切換到聽寫模式，而不是鍵入。 選取文字輸入方塊旁邊的麥克風，開始使用。


## <a name="adding-voice-commands-to-your-app"></a>將語音命令新增至您的應用程式

請考慮對您所建置的任何體驗新增語音命令。 語音是功能強大的方式，可方便您控制系統和應用程式。 因為使用者說話時的語調和口音各異，適當選擇語音關鍵字才能確保系統會分毫不差地解讀出使用者的命令。

### <a name="best-practices"></a>最佳作法

以下是有助於順利辨識語音的一些做法。
* **使用精簡的命令** - 盡可能選擇有兩個以上音節的關鍵字。 口音不同的人在說單音節的單字時往往會使用不同的元音。 範例：「播放影片」優於「播放目前選取的影片」
* **使用簡單詞彙** -範例：「顯示附注」優於「顯示牌子」
* **確定命令不具破壞性** - 確定可透過語音命令來採取的動作不具破壞性，如果使用者附近有其他人不小心觸發命令，也可以輕鬆地加以復原。
* **避免類似發音的命令** - 避免註冊多個聽起來非常類似的語音命令。 範例：「顯示更多」和「顯示存放區」可能非常類似的發音。
* **將未使用的應用程式取消註冊** - 當應用程式並非處在會讓特定語音命令生效的狀態時，請考慮將其取消註冊，以免該命令與其他命令混淆。
* **使用不同口音進行測試** - 請使用不同口音的使用者測試應用程式。
* **讓語音命令保持一致** - 如果 "Go back" 會回到上一頁，請在應用程式中保持這個行為。
* **避免使用系統命令** - 下列語音命令已保留給系統使用。 應用程式請勿使用這些命令。
   * "Hey Cortana"
   * "Select"
   * 「移至開始」

### <a name="advantages-of-voice-input"></a>語音輸入的優點

語音輸入是很自然的意圖溝通方式。 語音在介面 **周遊** 中特別有用，因為它可協助使用者切換介面的多個步驟， (使用者可能會在查看網頁時說「返回」，而不需要在應用程式) 中啟動並按 [上一頁] 按鈕。 這小段節省時間對使用者對體驗的認知有強大的 **情緒影響** ，並讓他們增強。 當我們無法騰出雙手或是在執行 **多工** 處理時，使用語音也是很方便的輸入方法。 在鍵盤上輸入的裝置上， **語音聽寫** 可以是輸入文字的有效替代方式。 最後，在某些情況下，當注視和手勢的 **精確度範圍** 有限時，語音有助於區分使用者的意圖。 

**使用語音如何讓使用者受益**
* 減少時間 - 語音應該會讓最終目標更有效率。
* 最不費力 - 語音應該會讓工作變得更為流暢且更不費力。
* 降低認知負荷 - 語音既直覺、易於了解且容易記住。
* 符合社交規範 - 語音應該會符合社會行為規範。
* 語音很平常 - 語音隨時可以變成慣常行為。

### <a name="challenges-for-voice-input"></a>語音輸入的挑戰

雖然語音輸入很適合用於許多不同的應用程式，但它也面臨數個挑戰。 瞭解語音輸入的優點和挑戰，可讓應用程式開發人員針對使用語音輸入的方式和時機，以及為使用者建立絕佳的體驗，提供更明智的選擇。

**連續輸入控制的語音輸入** 精細控制是其中之一。 例如，使用者可能會想要在其「音樂」應用程式中變更其磁片區。 她可以單純說「更高」，但不清楚系統應該如何提高磁片區數量。 使用者可以說：「讓它變得更大」，但很難量化。 使用聲音移動或調整全像影像也很困難。 

**語音輸入偵測的可靠性** 雖然語音輸入系統變得更好且更好，但有時它們可能會不正確地聆聽及解讀語音命令。
重要的是，在系統正在接聽時提供意見反應給使用者，以及系統如何理解，以明確地瞭解使用者的潛在問題，以解決應用程式中的這項挑戰。  

**共用空間中的語音輸入** 您與其他人共用的空格可能無法接受語音社交。
以下是一些範例：
* 使用者可能不會想要打擾他人 (例如，在安靜文件庫或共用的辦公室) 
* 使用者可能覺得很難在公眾的對話中看到
* 使用者可能會覺得不舒服地聽寫個人或機密郵件 (包括密碼) 而其他人正在接聽

**唯一或未知單字的語音輸入** 當使用者聽寫可能對系統不明的字詞（例如昵稱、某些俚語單字或縮寫）時，也會發生語音輸入的問題。 

**學習語音命令** 雖然最終目標是自然地與您的系統對話，但應用程式通常仍依賴特定的預先定義語音命令。
與大量語音命令相關的挑戰是，如何在不多載使用者的情況下教授這些問題，以及如何協助使用者進行保留。 

<br>

---

### <a name="voice-feedback-states"></a>語音反饋狀態

當語音正確套用時，使用者會了解 **他們能說什麼並獲得清楚的反饋** 而知道系統 **正確聽懂他們的語音**。 這兩個訊號會讓使用者有信心，確信他們可以使用語音作為主要輸入方式。 下圖顯示的是當系統辨識到語音輸入時會有什麼情形，以及系統會如何讓使用者知道這一點。


:::row:::
    :::column:::
       ![1. 一般資料指標狀態](images/voicefeedbackstates-regular.jpg)<br>
       **1. 一般資料指標狀態**<br>
    :::column-end:::
    :::column:::
       ![2. 傳達語音意見反應，然後消失](images/voicefeedbackstates-voice.jpg)<br>
        **2. 傳達語音意見反應，然後消失**<br>
    :::column-end:::
    :::column:::
       ![3. 一般資料指標狀態](images/voicefeedbackstates-regular.jpg)<br>
       **3. 返回一般資料指標狀態**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>針對混合實境中的「語音」，使用者最應該了解的事
* 在鎖定按鈕時說出 **"Select"** (您可以在任何地方使用這個命令來按一下按鈕)。
* 在某些應用程式中，您可以說出 **應用程式列按鈕的標籤名稱** 來採取動作。 例如，在查看應用程式的同時，使用者可以說出「Remove」命令來從該世界中移除應用程式 (這可省下必須用手按一下按鈕的時間)。
* 您可以說 **「嗨 Cortana」** 讓 Cortana 開始聽取命令。 您可以向她問問題 (「嗨 Cortana，艾菲爾鐵塔有多高」)、請她開啟應用程式 (「嗨 Cortana，開啟 Netflix」)，或請她顯示 [開始] 功能表 (「嗨 Cortana，回到首頁」) 等等。

## <a name="common-questions-and-concerns-users-have-about-voice"></a>使用者會有的語音相關常見問題和疑慮
* 我可以說什麼？
* 如何知道系統沒有聽錯？
   * 系統一直聽錯我的語音命令。
   * 我提供了語音命令，系統卻沒有反應。
* 我提供了語音命令，系統卻做出錯誤反應。
* 如何讓我的語音以特定應用程式或應用程式命令作為目標？
* 在 HoloLens 上的全像攝影畫面外，是否可以使用語音來命令物件？

## <a name="communication"></a>通訊

如果應用程式想要利用 HoloLens 提供的自訂音訊輸入處理選項，請務必瞭解您的應用程式可使用的各種 [音訊串流類別](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) 。 Windows 10 支援數種不同的串流類別和 HoloLens，可利用其中三種來啟用自訂處理，以優化專為語音提供的麥克風音訊品質、通訊，以及可用於環境音效音訊捕獲 (例如「攝影機」 ) 案例。
* 已針對通話品質和旁白案例自訂 AudioCategory_Communications 資料流程類別，並為用戶端提供使用者語音的 16kHz 24bit mono 音訊串流
* AudioCategory_Speech 串流類別是針對 HoloLens (Windows) 語音引擎自訂，並為其提供使用者語音的 16kHz 24bit mono 串流。 如有需要，協力廠商語音引擎可以使用此類別。
* AudioCategory_Other 串流類別目錄是針對環境環境音訊錄製自訂，並為用戶端提供48kHz 的24位身歷聲音訊串流。

所有的音訊處理都是硬體加速的，這表示在 HoloLens CPU 上執行相同的處理功能時，這些功能的耗電量會少很多。 避免在 CPU 上執行其他音訊輸入處理，以將系統電池壽命最大化，並充分利用內建的卸載音訊輸入處理。

## <a name="languages"></a>語言

HoloLens 2 [支援多種語言](https://docs.microsoft.com/hololens/hololens2-language-support)。 請記住，即使安裝了多個鍵盤或應用程式嘗試以不同的語言建立語音辨識器，語音命令一律會以系統的顯示語言執行。

## <a name="troubleshooting"></a>疑難排解

如果您在使用「選取」和「嗨 Cortana」時遇到任何問題，請嘗試移至更安靜的空間、關閉雜訊來源，或說出更遠。 目前，HoloLens 上的所有語音辨識都會專門針對美國英文的原生喇叭進行調整及優化。

針對 Windows Mixed Reality Developer Edition 2017 版，在初始 HMD 連線之後登出和重新登入電腦桌面之後，音訊端點管理邏輯將可正常運作 (永久) 。 在經過 WMR OOBE 之後第一次登出/進入事件之前，使用者可能會遇到各種音訊功能問題，範圍從沒有音訊到音訊切換，視系統在第一次連接 HMD 之前的設定方式而定。

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK 中的語音輸入 (適用于 Unity 的混合現實工具組) 
透過 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**，您可以輕鬆地對任何物件指派語音命令。 使用 MRTK 的 **語音輸入設定檔** 來定義關鍵字。 藉由指派 **SpeechInputHandler** 腳本，您可以讓任何物件回應語音輸入設定檔中定義的關鍵字。 SpeechInputHandler 也會提供語音確認標籤，以提升使用者的信心。

* [MRTK-Voice 命令](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a>另請參閱
* [目光和行動](gaze-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [DirectX 中的語音輸入](../develop/native/voice-input-in-directx.md)
* [Unity 中的語音輸入](../develop/unity/voice-input-in-unity.md)
