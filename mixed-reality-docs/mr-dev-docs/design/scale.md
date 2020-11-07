---
title: 調整
description: 以全像攝影形式呈現看似逼真內容的關鍵，就是盡可能地模擬真實世界的視覺統計資料。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、樣式、設計
ms.openlocfilehash: 7d35da2d86d8d3b7f444974d87e5aa10e58ed2c8
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340656"
---
# <a name="scale"></a>調整

以全像攝影形式呈現看似逼真內容的關鍵，就是盡可能地模擬真實世界的視覺統計資料。 這表示我們可以盡可能地將多個視覺提示加以結合，協助我們 (在真實世界中) 了解物件的位置、大小以及其構成。 物件的小數位數是這些視覺提示最重要的其中一項，可讓檢視器瞭解物件的大小，以及其位置的提示 (特別是已知大小) 的物件。 此外，真實規模的觀看物件已經被視為混合現實的其中一個主要體驗差異，也就是在先前以螢幕為基礎的視圖上尚未可能發生的情況。

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>如何建議物件和環境的規模

有許多方式可以建議物件的小數位數，其中有些可能會影響其他可感知的因素。 關鍵是只要以「真實」大小顯示物件，並在使用者移動時維持實際大小。 這表示在使用者的視覺角度更近或更近的情況下，全像是在使用者的視覺角度，與實際物件的方式相同。

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>使用物件在呈現給使用者時的距離

其中一個常見的方法是在物件呈現給使用者時，利用物件的距離。 例如，請考慮將大型家庭車輛視覺化到使用者前方。 如果車輛直接在其前方，則在 arm 的長度內，會太大而無法納入使用者的觀點。 這會要求使用者移動其標頭和主體，以瞭解整個物件。 如果車輛 (在房間) 的周圍，則使用者可以在其視野中查看整個物件，然後將其放在更靠近的位置，以詳細檢查區域，藉此建立規模。

:::row:::
    :::column:::
        **[Volvo 使用這項技術來建立](https://www.youtube.com/watch?v=DilzwF90vec)** 新汽車的 showroom 體驗，利用全像全像直覺的方式，利用全像是對使用者來說非常直覺的方式來運用全像攝影車。 體驗是從實體資料表上的汽車全像投影開始，讓使用者瞭解模型的總大小和形狀。 稍後在此體驗中，汽車會擴充到更大的 (，而超出裝置欄位的大小) 但因為使用者已從較小的模型取得參考的畫面格，所以可充分地四處流覽車輛的各項功能。<br>
        <br>
        *影像： Volvo 適用于 HoloLens 的車輛體驗*
    :::column-end:::
        :::column:::
       ![HoloLens 的 Volvo Cars 體驗](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>使用全像影像來修改使用者的實際空間

另一種方法是使用全像影像來修改使用者的實際空間、將現有的牆或上限取代成環境或附加「洞」或「windows」，讓過度調整大小的物件看似「細分」實體空間。 例如，大型樹狀結構可能無法容納大部分使用者的客廳，但藉由將虛擬天空放在最高的位置，實體空間就會擴展到虛擬。 如此一來，使用者就可以逐步解說虛擬樹狀結構，並收集其在現實生活中的顯示方式，然後查閱以查看其延伸超過空間的實體空間。

:::row:::
    :::column:::
        Minecraft 使用類似的技巧 **[開發了概念體驗](https://minecraft.net/)** 。 藉由將虛擬視窗新增至房間內的實體介面，房間內的現有物件就會放在極大的環境內容中，而不是空間的實體規模限制。<br>
        <br>
        *影像： Minecraft 適用于 HoloLens 的概念體驗*
    :::column-end:::
        :::column:::
       ![HoloLens 的 Minecraft 概念體驗](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>使用 scale 進行實驗

在某些情況下，設計人員會實驗修改尺規 (，方法是變更顯示的物件) 的「實際」大小，同時維持物件的單一位置，以接近接近或更接近檢視器的物件，而不需要實際移動。 在某些情況下，這是在某些情況下進行測試，以模擬關閉專案的功能，同時仍遵守觀看虛擬內容的可能緩和限制，而接近「緩和區域」的建議。

不過，這可能會在體驗中建立一些可能的構件：
* 如果虛擬物件代表的某個物件具有「已知」大小的檢視器，則在不變更位置的情況下，變更縮放比例會導致視覺提示衝突，而眼睛可能仍會因為 vergence 提示而「查看」物件，但在 [)  (提示](comfort.md) 的情況下，可能仍會顯示物件，但大小會作為 monocular 提示，表示物件可能會更接近。 這些衝突的提示會導致混淆的理解，因此，檢視器通常會將物件視為保持 (，因為有常數深度的提示) 但很快就會成長。
* 在某些情況下，小數位數的變更會被視為「即將問世」提示，其中物件可能會或可能不會被檢視器變更，但似乎是直接移到檢視器的眼睛 (這可能是令人感到不安的刺痛) 。
* 在真實世界中的比較介面上，這類調整變更有時會被視為沿著多個軸變化的位置，在某些情況下，物件可能會顯得較低，而不是移動較接近的 (類似于3D 移動的2D 投影中) 。
* 最後，對於沒有已知「真實世界」大小的物件 (例如任意大小、UI 元素 ) 等等的任意形狀），變更尺規的功能可能會以模擬距離變更的方式運作，因此，檢視器不會有許多預先存在的由上而下的提示，可瞭解物件的真正大小或位置，因此可以將比例視為更重要的提示來處理。

<br>

---

## <a name="next-discovery-checkpoint"></a>下次探索檢查點

如果您正在關注我們所配置的 [探索旅程](../discover/get-started-with-mr.md) ，您將會結束形式突襲行動混合現實基礎的初始工作。 您可以看看產業合作夥伴在現實世界中的混合現實情況： 

> [!div class="nextstepaction"]
> [查看產業合作夥伴如何使用混合實境](../discover/get-started-with-mr.md#see-how-industry-partners-are-using-mixed-reality)

或繼續進行設計旅程：

> [!div class="nextstepaction"]
> [開始您的設計旅程](../design/design.md)

## <a name="see-also"></a>請參閱
* [色彩、光線和材質](../color,-light-and-materials.md)
* [印刷樣式](typography.md)
* [空間音效設計](spatial-sound-design.md)
