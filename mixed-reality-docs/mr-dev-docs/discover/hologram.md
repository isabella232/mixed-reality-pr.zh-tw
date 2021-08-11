---
title: 什麼是全像投影？
description: HoloLens 可讓您在世界各地出現于世界各地的立體和音效物件，並與之互動。
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、全像影像、設計、互動、混合現實耳機、Windows Mixed reality 耳機、什麼是增強的現實
ms.openlocfilehash: e028fe6180bded26263fa47feb5acefc94570222e43f10fe85db5adf90307844
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202108"
---
# <a name="what-is-a-hologram"></a>什麼是全像投影？

HoloLens 可讓您查看全像 **影像**，也就是像真實物件一樣，在世界周圍出現的燈光和音效物件。 全像投影可以回應您的[注視](../design/gaze-and-commit.md)、[手勢](../design/gaze-and-commit.md#composite-gestures)和[語音命令](../design/voice-input.md)。 他們甚至可以與您的 [真實世界表面](../design/spatial-mapping.md) 互動。 全像投影是您世界中的數位物件。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
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

### <a name="light"></a>淺色

[HoloLens 轉譯](../develop/platform-capabilities-and-apis/rendering.md)的全像影像，會直接出現在使用者眼睛之前的全像攝影框架中。 全像投影將燈光添加到您的世界，這表示您會看到顯示器的光線和周圍世界的光線。 由於 HoloLens 使用加上燈光的加法顯示，因此黑色色彩將會呈現為透明的。 

全像投影可能會有非常不同的外觀和行為。 有些是真實且穩固的，有些則是編排卡通和 ethereal。 您可以使用全像投影來反白顯示環境中的功能，或使用它們做為應用程式使用者介面中的元素。

![操作全像手](images/hologram-hands-940px.jpg)

### <a name="sound"></a>音效

全像投影也[可能產生音效，看起來似乎](../design/spatial-sound.md)來自您環境中的特定位置。 在 HoloLens 上，音效來自兩個位于您的耳上方的喇叭。 與全像全像全像全像全像全像一樣，喇叭也是一種新的音效，而不會封鎖環境的音效。

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>您可以將全息圖放在世界或標記中

當您有固定的影像位置時，可以將它精確地 [放](../design/coordinate-systems.md) 在世界各地。 當您四處解說時，像是實體物件一樣，全像世界上的全像是世界上的全像是固定的。 如果您使用 [空間錨點](../design/coordinate-systems.md#spatial-anchors) 來釘選物件，則當您稍後返回時，系統甚至可以記得您離開該物件的位置。

![在零售空間中使用 Microsoft Dynamics 365 版面配置的兩個男性](images/HLS19_retailLayoutHologram_001-940px.jpg)

部分的全像是以使用者為依據。 他們會根據使用者自行定位。 您可以選擇帶給您的全像投影，然後將它放在牆上的另一個房間。

**最佳作法**

* 在某些案例中，您需要在整個體驗中輕鬆地探索或顯示全像影像。 這種定位有兩種高階方法。 讓我們將其稱為「 **鎖定** 」和「內文 **鎖住**」。
   * **顯示鎖定** 的內容已鎖定到顯示裝置。 這種類型的內容很難處理，因為有許多原因，包括非自然的「clingyness」，讓許多使用者感到挫折，並且想要「搖動」。 一般情況下，設計人員發現更適合用來避免顯示鎖定的內容。
   * **主體鎖定** 內容可能更容許。 本文-鎖定是指您在3D 空間中 tether 使用者的內文或注視向量。 許多經驗都採用了內文鎖定行為，其中的全像是使用者的注視，可讓使用者旋轉其內文，並在空間中移動，而不會遺失全像影像。 合併延遲有助於讓全息圖的移動感覺更自然。 例如，Windows 全像全球版作業系統的一些核心 UI 會使用本文鎖定的變化，在使用者關閉時，在使用者的注視之後，會有一個非常類似的彈性延遲。
* 將全像觀賞距離的全像是大約是1-2 的計量離 head。
* 如果專案必須持續于全像全像框架，或在使用者變更其觀點時，考慮將您的內容移至顯示器的一端，則可讓元素漂移。 如需詳細資訊，請參閱 [billboarding 和標記-沿著](../design/billboarding-and-tag-along.md) artilce。

**將全像全區放在最理想的區域，介於 1.25 m 和 5 m 之間**

雙計量是最理想的觀賞距離。 當您接近1個計量時，就會開始降低體驗。 在距離小於1的度量時，定期移至深度的全像投影，會比固定的全像投影更有問題。 當內容太近時，請考慮以適當的方式裁剪或漸離您的內容，因此您不會將使用者帶到不愉快的觀賞體驗。

![從使用者處放置全像影像的最佳距離。](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>與您和您的世界互動的全像影像

全像投影不僅適用于燈光和音效;它們也是您世界上的有效部分。 以您手中的手中看看您的手中的手，然後您就可以開始使用全像投影。 提供語音命令，並可回復全像影像。

![使用 Microsoft HoloLens 2 在伺服器陣列開發專案上共同作業的政府公用程式工作者群組](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

全像投影啟用無法在其他地方使用的個人互動。 因為 HoloLens 知道世界的位置，所以全像攝影的字元可以直接查看您的眼睛，並開始與您交談。

全息圖也可以與您的環境互動。 例如，您可以將全息的彈跳球放在資料表上方。 然後，利用點 [一下，觀賞](../design/gaze-and-commit.md#composite-gestures)球的彈跳，並在叫用資料表時，讓聲音變成音效。

您也可以 pixels occluded 真實世界物件的全像投影。 例如，全像攝影的字元可能會讓您看不到幕後的大門。

**用於整合全像全球和真實世界的提示**

* 對齊 gravitational 規則可讓您更輕鬆地與可信相關的影像。 例如：將全像狗放在地面上 & 花瓶在資料表上，而不是讓它們浮在空間中。
* 許多設計人員發現，他們可以藉由在桌上的表面上建立「負陰影」來整合更可信的全像投影。 若要這麼做，您可以在全像是建立全像影像，然後從發光減去「陰影」。 軟光暈與真實世界的光線整合。 陰影是用來在環境中地面全像影像。

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>全像影像 <br>您可以夢想<br>
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

您正在研究我們所配置的 [探索旅程](get-started-with-mr.md) ，並探索混合現實的基本概念。 您可以從這裡繼續進行下一個基本主題： 

> [!div class="nextstepaction"]
> [展開您的設計程序](case-study-expanding-the-design-process-for-mixed-reality.md)