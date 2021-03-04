---
title: 資料指標
description: 目標向量的游標或指標，可為使用者提供持續的意見反應，以瞭解 HoloLens 對其意圖的瞭解程度。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1 代) 、HoloLens 2、混合現實、游標、目標、注視、手勢、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、射線、輸入
ms.openlocfilehash: 0b35c832e6d13ff10d14686909754de60b83fa23
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759414"
---
# <a name="cursors"></a>資料指標

![資料指標](images/UX_Hero_Cursor.jpg)

資料指標會根據耳機認為使用者的最新焦點是在指定時間，提供持續的意見反應。 資料指標意見反應包括虛擬環境中的哪個區域、全息圖或點會回應輸入。 即使游標是裝置瞭解使用者注意的數位標記法，但這並不是判斷使用者的意圖。 資料指標意見反應也可讓使用者知道預期的系統回應。 您可以使用意見反應，將其意圖傳達給裝置，從而提高使用者的信心。

有3種資料指標： **手指、光線** 和 **頭部**。 這些指標會在 HoloLens、HoloLens 2 和沉浸式耳機上使用不同的輸入形式。 以下是要針對每種類型的耳機和互動模型使用哪一種資料指標類型的指引。 在 (MRTK) 的混合現實工具組中，我們建立了拖放資料指標模組，以協助您建立正確的指標體驗。

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></td>
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

手指游標僅適用于 HoloLens 2，以增強「[手動操作的直接操作](direct-manipulation.md)」互動模式。 我們已將環形連接至兩個索引手指的秘訣，以更清楚地瞭解手指指向的位置。 環形大小是以指向 UI 介面的手指近距離為基礎，這會在手指觸及 UI 時縮小為小點。 手指越接近，環形就越小。 <br>

![手指游標](images/finger-cursor.png)<br>
**手指游標1的視覺意見反應狀態** ：環形會縮小為點。 2：環形與 surface 對齊。 3：環形與手指向量垂直。 4：無環形。

## <a name="ray-cursor"></a>光線游標

光線指標會附加至最接近的光線，以允許操作不在手中的物件。 在沉浸式耳機中，光線會從運動控制器和以點指標結束。 在 HoloLens 2 中，我們會套用這些移動控制器光線的精神模型，以及源自手掌和 end in 環形指標，且與直接操作中使用的手指指標一致的光線。 <br>
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

前端指標是一個點，它會附加至不可見的標頭看式向量的結尾，該向量會使用標頭的位置和旋轉來指向點。 若要執行動作，此指標會與各種認可輸入配對，例如點擊點、語音命令、停留，然後按下按鈕。 在 HoloLens 2 中，列印頭最適合與任何未按下的認可輸入配對，因為空中點與遠光線之間會有互動衝突。 <br>
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
* 根據您所建立的體驗，以使用者的外觀調整資料指標也是很重要的考慮。 例如，當使用者進一步探討您的體驗時，資料指標應該會變得太小而無法遺失。
* 調整游標時，請考慮將軟動畫套用至其調整規模，以提供一種隨機的感覺。
* 避免阻礙內容。 全像全像是讓體驗更清楚，而且資料指標不應該遠離它們。

### <a name="directionless-cursor-shape"></a>Directionless 資料指標圖形

* 雖然沒有一個右資料指標圖形，但我們建議您使用 directionless 圖形，例如圓環形。 指向某個方向的游標 (例如，傳統的箭號游標) 可能會讓使用者混淆，使其一律看起來如此。
* 例外狀況是使用資料指標，將互動指令傳達給使用者。 例如，在混合現實作業系統中調整全像投影時，游標會暫時包含箭號，指示使用者如何移動其手以調整全像。

### <a name="look-and-feel"></a>外觀與風格

* 環圈圖或環圈圖的游標適用于許多應用程式。
* 挑選最能代表您正在建立之體驗的色彩和圖形。
* 資料指標特別容易用來 [區分色彩](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)。
* 具有對稱不透明度的小型資料指標可保持資訊的資訊，而不需要支配視覺化階層。
* 請 cognizant 在游標後方使用陰影或反白顯示，因為它們可能會對內容和手中工作的注意力。
* 資料指標應對齊並在您的應用程式中將這些表面上建。 使用者會覺得系統可以看到他們在哪裡尋找，但系統也知道他們的環境。 例如，混合現實作業系統中的資料指標會與使用者世界的表面一致，即使使用者未直接查看全像，也可以感覺到世界的認知。
* 當資料指標接近使用者時，以磁性方式鎖定游標至互動專案有助於提高使用者在使用選取動作時與該元素互動的信心。

### <a name="visual-cues"></a>視覺提示

* 如果您的經驗著重于單一的全像投影，則當您離開該全像投影時，您的游標應該只靠全像是的全像成形和變化圖形。 這可以向使用者傳達可操作的全像影像，而且可以與其互動。
* 如果您的應用程式使用空間對應，則您的資料指標可能會對齊，並在它看到的每個介面上。 這會對 HoloLens 和您的應用程式可看到其空間的使用者提供意見反應。 這可以強調全像是真實的全球化，並協助您填補真實與虛擬之間的橋樑。
* 瞭解當視野中沒有任何全息圖或表面時，游標應怎麼做。 將它放在使用者前方預先決定的距離就是其中一個選項。

### <a name="possible-actions"></a>可能的動作

* 您可以使用不同的圖示來表示資料指標，以傳達全息圖可執行檔可能動作，例如縮放或旋轉。
* 如果對使用者而言，只會在資料指標上加入額外的資訊。 否則，使用者可能不會注意到狀態變更或資料指標混淆。

### <a name="input-state"></a>輸入狀態

* 我們可以使用游標來顯示使用者的輸入狀態或意圖。 例如，我們可以顯示一個圖示，告訴使用者系統看到其手上的狀態，而應用程式知道他們已經準備好採取行動。
* 我們也可以使用資料指標來顯示使用者透過暫時的色彩變更聽到的聲音命令

* 下列資料指標狀態可以用不同的方式來執行。 您可以藉由建立資料指標模型（例如狀態機器）來執行這些不同的狀態。 例如：
    * 閒置狀態是您顯示預設資料指標的位置。
    * [就緒] 狀態是當您在 [就緒] 位置偵測到使用者的手時。
    * 互動狀態是使用者執行特定互動的時候。
    * 可能的動作狀態或暫留狀態是當您傳達可在全像影像上執行的可能動作。

您也可以在偵測到不同狀態時，以面板的方式來執行這些狀態，以顯示不同的藝術資產。

<br>

---

## <a name="going-cursor-free"></a>進入「無資料指標」

當深度的意義是體驗的重要元件，以及透過注視和手勢指向互動 (時，建議您不要使用資料指標進行設計，) 不需要絕佳的精確度。 系統仍然必須符合資料指標的一般需求：為使用者提供持續的意見反應，以瞭解對其指向的系統，並協助他們將其意圖傳達給系統。 這可以透過其他明顯的狀態變更來達成。

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>適用于 Unity 的 MRTK (混合現實工具組) 的游標

根據預設， [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) 會提供資料指標預製專案 ([DefaultCursor. 預製專案](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) 與 shell 的系統資料指標具有相同的視覺狀態。 其是在 MRTK 輸入設定檔的 [指標] 下進行指派。 您可以針對您的體驗取代/自訂此資料指標。 針對眼睛追蹤輸入的體驗，MRTK 也提供 EyeGazeCursor，其具有微妙的視覺效果可將干擾降至最低。

* [MRTK - 指標設定檔](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/mixed-reality-configuration-guide.md#pointer-configuration)
* [MRTK - 輸入系統](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)
* [MRTK - 指標](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md)

---

## <a name="see-also"></a>請參閱

* [手勢](gaze-and-commit.md#composite-gestures)
* [頭部目光和行動](gaze-and-commit.md)