---
title: 資料指標
description: 目標向量的游標或指標，可為使用者提供持續的意見反應，以瞭解 HoloLens 對其意圖的瞭解程度。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (第1代) 、HoloLens 2、混合的現實、游標、目標、注視、手勢、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、放射片、輸入
ms.openlocfilehash: db895c7aad177d7ddd2eb371392812b1d7e4d039
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702644"
---
# <a name="cursors"></a>資料指標

![資料指標](images/UX_Hero_Cursor.jpg)

指標或您目前目標向量的指標，可為使用者提供持續的意見反應，以瞭解耳機認為目前焦點在當時的位置。 資料指標可讓使用者瞭解其目前的目標點，並做為意見反應來指出哪些區域、全息圖或點將會回應輸入。 它是裝置瞭解使用者注意 (的數位標記法，但這可能不是決定其意圖) 的任何事物。

資料指標提供的意見反應可讓使用者預測系統的回應方式、使用該信號作為意見反應，以便更妥善地傳達裝置的意圖，並對其互動提供更自信的能力。

有3種資料指標： **手指、光線** 和 **頭部**。 這些指標資料指標在 HoloLens、HoloLens 2 和沉浸式耳機上，使用不同的輸入形式。 以下是要針對每種類型的耳機和互動模型使用哪一種資料指標類型的指引。 在 (MRTK) 的混合現實工具組中，我們建立了拖放資料指標模組，以協助您建立正確的指標體驗。


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
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>手指游標</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>光線游標</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>頭部指標</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>手指游標
手指游標僅適用于 HoloLens 2，以增強「[直接操作](direct-manipulation.md)」互動模式。 為了更清楚地瞭解手指指向的位置，我們已將環形連接至兩個索引手指的秘訣。 環形大小是根據手指與 UI 介面附近的距離 (越靠近手指，環形) 越小，就會在手指與 UI 聯繫時縮小為點形。 <br>

![手指游標](images/finger-cursor.png)<br>
**手指游標1的視覺意見反應狀態** ：環形會縮小為點。 2：環形與 surface 對齊。 3：環形與手指向量垂直。 4：無環形。

## <a name="ray-cursor"></a>光線游標
光線指標會附加至最接近的光線，以允許操作不在手中的物件。 在沉浸式耳機中，光線會從運動控制器和以點指標結束。 在 HoloLens 2 中，我們會利用這些移動控制器光線的精神模型，以及源自手掌和 end in 環形指標，且與直接操作中使用的手指指標一致的光線。 <br>
:::row:::
    :::column:::
        ![光線游標控制器](images/ray-cursor-controller.png)<br>
        **移動控制器的光線指標**<br>
    :::column-end:::
    :::column:::
        ![光線游標手](images/ray-cursor-hand.png)<br>
        **手中的光線游標**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a>頭部指標
前端指標是一個點，它會附加至不可見的標頭看式向量的結尾，該向量會使用標頭的位置和旋轉來指向點。 若要執行動作，此指標會與各種認可輸入配對，例如點擊點、語音命令、停留，然後按下按鈕。 在 HoloLens 2 中，列印頭最適合與任何不是按下的認可輸入配對，因為在攻點與遠光線之間會有互動衝突。 <br>
:::row:::
    :::column:::
        ![頭部注視游標手](images/head-gaze-cursor-hand.png)<br>
        **具有手形手勢的列印頭指標**<br>
    :::column-end:::
    :::column:::
        ![頭部注視游標聲音](images/head-gaze-cursor-voice.png)<br>
        **使用 voice 命令的標頭指標**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a>資料指標自訂建議
如果您想要自訂資料指標的意見反應行為和外觀，以下是一些設計建議：

### <a name="cursor-scale"></a>資料指標調整
* 資料指標不應大於可用的目標，讓使用者可以輕鬆地與內容互動並加以查看。
* 根據您所建立的體驗，以使用者的外觀調整資料指標也是很重要的考慮。 例如，當使用者進一步探討您的體驗時，資料指標應該不會變得太小，所以會遺失。
* 調整游標時，請考慮將軟動畫套用至其調整規模，以提供一種隨機的感覺。
* 避免阻礙內容。 全像全像是讓體驗更清楚，而且資料指標不應該離開。

### <a name="directionless-cursor-shape"></a>Directionless 資料指標圖形
* 雖然沒有一個右資料指標圖形，但我們建議您使用 directionless 圖形，例如圓環形。 指向某個方向的游標 (例如，傳統的箭號游標) 可能會讓使用者混淆，使其一律看起來如此。
* 例外狀況是使用資料指標，將互動指令傳達給使用者。 例如，在混合現實作業系統中調整全像投影時，游標會暫時包含箭號，指示使用者如何移動其手以調整全像。

### <a name="look-and-feel"></a>外觀與風格
* 環圈圖或環圈圖資料指標適用于許多應用程式。
* 挑選最能代表您所建立之體驗的色彩和圖形。
* 資料指標特別容易用來 [區分色彩](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)。
* 具有對稱不透明度的小型資料指標可保持資訊的資訊，而不需要支配視覺化階層。
* 請 cognizant 在游標後方使用陰影或反白顯示，因為它們可能會對內容和手中工作的注意力。
* 資料指標應該符合並將您應用程式中的表面分配給使用者，這可讓使用者感覺到系統可以看到他們在哪裡尋找，但系統也知道他們的環境。 例如，在混合現實 OS 中，資料指標會與使用者世界的表面保持一致，即使在使用者不直接查看全像的情況下，也能感受到世界的認知。
* 以磁性方式鎖定游標至接近近距離的互動式元素，可協助改善使用者在執行選取動作時與該專案互動的信心。

### <a name="visual-cues"></a>視覺提示
* 如果您的經驗著重于單一的全像投影，則當您離開該全像投影時，您的游標應該只靠全像是的全像成形和變化圖形。 這可以向使用者傳達可操作的全像影像，而且可以與其互動。
* 如果您的應用程式使用空間對應，則您的資料指標可能會對齊，並在它看到的每個介面上。 這會對 HoloLens 和您的應用程式可看到其空間的使用者提供意見反應。 這可以強調全像是真實的全球化，並協助您填補真實與虛擬之間的橋樑。
* 瞭解當視野中沒有任何全息圖或表面時，游標應怎麼做。 將它放在使用者前方預先決定的距離就是其中一個選項。

### <a name="possible-actions"></a>可能的動作
* 您可以使用不同的圖示來表示資料指標，以傳達可執行全息圖的可能動作，例如縮放或旋轉。
* 如果對使用者而言，只會在資料指標上加入額外的資訊。 否則，使用者可能不會注意到狀態變更或資料指標混淆。

### <a name="input-state"></a>輸入狀態
* 我們可以使用游標來顯示使用者的輸入狀態或意圖。 例如，我們可以顯示一個圖示，告訴使用者系統看到其手上的狀態，而應用程式知道他們已經準備好採取行動。
* 我們也可以使用資料指標，向使用者顯示系統透過暫時色彩聽取聲音命令的使用者 chang

* 下列資料指標狀態可以用不同的方式來執行。 您可以藉由建立資料指標模型（例如狀態機器）來執行這些不同的狀態。 例如：
    * 閒置狀態是您顯示預設資料指標的位置。
    * [就緒] 狀態是當您在 [就緒] 位置偵測到使用者的手時。
    * 互動狀態是使用者執行特定互動的時間。
    * 可能的動作狀態或暫留狀態是當您傳達可在全像影像上執行的可能動作。

您也可以使用面板來實作為這些狀態，讓您可以在偵測到不同狀態時顯示不同的藝術資產。

<br>

---


## <a name="going-cursor-free"></a>進入「無資料指標」
當深度的意義是體驗的重要元件，以及透過注視和手勢來指向互動 (時，建議您不要使用資料指標進行設計，) 不需要絕佳的精確度。 系統仍然必須符合資料指標通常符合的需求，方法是為使用者提供持續的意見反應，以瞭解系統對其指標的理解，並協助他們安心地與系統溝通其意圖。 這可以透過其他明顯的狀態變更來達成。

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>適用于 Unity 的 MRTK (混合現實工具組) 的游標
根據預設， [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) 會提供資料指標預製專案 ([DefaultCursor. 預製專案](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) 與 shell 的系統資料指標具有相同的視覺狀態。 它是在 MRTK 輸入設定檔的 [指標] 下進行指派。 您可以針對您的體驗取代/自訂此資料指標。 針對眼睛追蹤輸入的體驗，MRTK 也提供 EyeGazeCursor，其中具有微妙的視覺效果可將干擾降至最低。

* [MRTK - 指標設定檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK - 輸入系統](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK - 指標](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a>另請參閱
* [軌跡](gaze-and-commit.md#composite-gestures)
* [頭部目光和行動](gaze-and-commit.md)
