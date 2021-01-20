---
title: 什麼是全像投影？
description: HoloLens 可讓您觀賞三維的全像影像，以及顯示在世界各地的燈光和音效物件。
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、全像投影、設計、互動、混合現實耳機、windows Mixed reality 耳機、什麼是增強的現實
ms.openlocfilehash: cc6b4a4838e7a275b1ef3a45e54c4b894a04b9c2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583347"
---
# <a name="what-is-a-hologram"></a>什麼是全像投影？

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


HoloLens 可讓您建立全像 **影像**，也就是像真實物件一樣，在世界周圍出現的燈光和音效物件。 全像投影會回應您的 [注視](../design/gaze-and-commit.md)、 [手勢](../design/gaze-and-commit.md#composite-gestures)和 [語音命令](../design/voice-input.md)。 他們甚至可以與您的 [真實世界表面](../design/spatial-mapping.md) 互動。 透過全像投影，您可以建立屬於自己世界的數位物件。

<br>

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
        <td>全像投影</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>全像是由燈光和音效組成

[HoloLens 轉譯](../develop/platform-capabilities-and-apis/rendering.md)的全像是在使用者的眼睛前方，直接顯示于全像攝影框架中。 全像是將燈光添加到您的世界，這表示您可以看到顯示器的光線和周圍的光線。 HoloLens 不會從您的眼睛中移除光線，所以無法使用黑色色彩來轉譯全像影像。 相反地，黑色內容會顯示為透明。

全像影像可以有許多不同的外觀和行為。 有些是真實且穩固的，有些則是編排卡通和 ethereal。 您可以使用全像投影來醒目提示您的環境中的功能，或使用它們作為應用程式使用者介面中的元素。

![操作全像手](images/hologram-hands-940px.jpg)

全像投影也 [可以製作音效，看起來就](../design/spatial-sound.md)像是來自您周圍的特定位置。 在 HoloLens 上，音效來自兩個位于您的耳上方的喇叭，而不會加以涵蓋。 就像顯示器一樣，喇叭是加總的，會在不封鎖環境音效的情況下引進新聲音。

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>您可以將全息圖放在世界或標記中

當您有特定的全息圖位置時，可以將它精確地 [放](../design/coordinate-systems.md) 在世界各地。 當您四處解說時，會根據您的世界來看，全像是穩定的。 如果您使用 [空間錨點](../design/coordinate-systems.md#spatial-anchors) 來釘選物件，則當您稍後返回時，系統甚至可以記得您離開該物件的位置。

![在零售空間中使用 Microsoft Dynamics 365 版面配置的兩個男性](images/HLS19_retailLayoutHologram_001-940px.jpg)

有些全息圖案會改為遵循使用者，無論使用者在何處都能自行定位。 您甚至可以選擇將一段時間帶到一段時間，然後在到達另一個房間之後，將它放在牆上。

**最佳作法**
* 在某些案例中，您可能會要求在整個體驗中，全像全像的全像是， 這種定位有兩種高階方法。 讓我們將其稱為「 **顯示鎖定** 」和「 **主體鎖定**」。
   * 顯示鎖定的內容會 positionally 「鎖定」至裝置顯示。 這種類型的內容很難處理，因為有許多原因，包括非自然的「clingyness」，讓許多使用者感到挫折，並且想要「搖動」。 一般情況下，許多設計師都發現更適合用來避免顯示鎖定的內容。
   * 主體鎖定的方法遠 forgivable。 本文-鎖定是指您在3d 空間中 tether 使用者的內文或注視向量。 許多經驗都採用了內文鎖定行為，其中的全像是使用者注視的，這可讓使用者旋轉其內文，並在空間中移動，而不會遺失全像影像。 合併延遲有助於讓全息圖移動感覺更自然。 比方說，Windows 全像是 Windows 全像的時候，在使用者的外觀鎖定之後，會在使用者看起來像是一種非常有彈性的延遲，在使用者關閉其前端時使用變化。
* 將全像觀賞距離的全像是大約是1-2 的計量離 head。
* 針對必須持續在全像全像框架中的元素提供漂移量，或考慮在使用者變更其觀點時，將內容以動畫顯示到顯示器的一端。

**將全像全區放在最理想的區域，介於 1.25 m 和 5 m 之間**

這兩個計量最適合，而且體驗將會降低從1計量取得的更接近程度。 在距離超過1個計量的距離中，定期移至深度的全像是很可能會造成問題，而不是固定的全像投影。 當內容太近時，請考慮以適當的方式裁剪或淡化內容，如此您就不會讓使用者進入未預期的體驗。

![從使用者處放置全像影像的最佳距離。](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>與您和您的世界互動的全像影像

全像全像光和音效;它們也是您世界上的有效部分。 以您手中的手中看看您的手中的手，然後您就可以開始使用全像投影。 提供聲音命令給全像影像，並可回復。

![使用 Microsoft HoloLens 2 在伺服器陣列開發專案上共同作業的政府公用程式工作者群組](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

全像是可讓您無法在別處進行個人互動。 由於 HoloLens 知道世界的所在位置，因此當您四處移動空間時，全像全像的字元可以直接在眼睛中看到。

全息圖也可以與您的環境互動。 例如，您可以將全息的彈跳球放在資料表上方。 然後，利用點 [一下，觀賞球彈，然後](../design/gaze-and-commit.md#composite-gestures)在到達表格時音效。

實際的物件也可以 pixels occluded 全像影像。 例如，全像攝影的字元可能會讓您看不到幕後的大門。

**整合全像影像和真實世界的秘訣**
* 對齊 gravitational 規則可讓您更輕鬆地與可信相關的影像。 例如：將全像狗放在地面上 & 花瓶在資料表上，而不是讓它們浮在空間中。
* 許多設計人員發現，他們可以藉由在桌上的表面上建立「負陰影」來整合更可信的全像投影。 若要這麼做，您可以在全像是建立全像影像，然後從發光減去「陰影」。 軟性發光與真實世界的光線整合，其使用陰影來地面環境中的全像影像。

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a>全像影像 <br>您可以夢想<br>
        作為全像攝影的開發人員，您可以將您的創意從2D 畫面移至世界各地。<br><br>
        *您* 會建立什麼？
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![客廳的全像虛構世界](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>下一個探索檢查點

如果您有遵循我們安排的[探索旅程](get-started-with-mr.md)，則您正處於探索混合實境基本概念的途中。 您可以從這裡繼續進行下一個基本主題： 

> [!div class="nextstepaction"]
> [展開您的設計程序](case-study-expanding-the-design-process-for-mixed-reality.md)