---
title: 調整
description: 以全像攝影形式呈現看似逼真內容的關鍵，就是盡可能地模擬真實世界的視覺統計資料。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、樣式、設計、混合現實耳機、Windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、調整、全息影線
ms.openlocfilehash: 0b643b7f4b53795afa6bac9b54e55565233ac1d96a6a58d5389a8a4b7db8d7cc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223000"
---
# <a name="scale"></a>調整

顯示逼真的全像攝影內容的關鍵是盡可能地模擬真實世界的視覺統計資料。 納入視覺提示，以協助真實世界的使用者瞭解物件是什麼、它們有多大，以及它們的功能。 物件的小數位數是其中一個最重要的視覺提示，因為它可讓檢視器瞭解物件大小以及其位置的提示。 此外，大規模地觀看物件是混合現實的主要體驗差異之一，也就是先前的螢幕式觀賞尚未可能發生的情況。

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>如何建議物件和環境的規模

有許多方式可以建議物件的小數位數，其中有些可能會影響其他可感知的因素。 第一個按鍵是以「真實」大小顯示物件，並在使用者移動時維持實際大小。 當使用者的視覺角度更近或更近時，全像投影將會佔用不同的使用者視覺角度，與實際物件的方式相同。

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>使用物件在呈現給使用者時的距離

其中一個常見的方法是使用物件在呈現給使用者時的距離。 例如，請考慮將大型家庭車輛視覺化到使用者前方。 如果汽車在 arm 的長度內直接放在其前方，可能會太大而無法納入使用者的觀點。 關閉物件需要使用者移動其標頭和主體，才能瞭解整個物件。 如果車輛 (的房間) ，則使用者可以在其視野的欄位中查看整個物件，藉以建立規模的意義。 然後，使用者可以更接近物件，以進行更詳細的檢查。

:::row:::
    :::column:::
        **[Volvo 使用這項技術來建立](https://www.youtube.com/watch?v=DilzwF90vec)** 新車輛的 showroom 體驗，並使用全像全像直覺的方式，利用全像直覺的方式來為使用者提供體驗。 體驗是從實體資料表上的車輛全息表開始，讓使用者瞭解模型的總大小和形狀。 稍後在此體驗中，汽車會擴充至超出裝置視野的大小。 因為使用者已從較小的模型取得參考的畫面格，所以可充分地四處流覽車輛的功能。<br>
        <br>
        *影像： Volvo HoloLens 的車輛體驗*
    :::column-end:::
        :::column:::
       ![HoloLens 的車輛體驗 Volvo](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>使用全像影像來修改使用者的實際空間

另一種方法是使用「全像」來修改使用者的實際空間，以環境或附加「洞」或「windows」取代現有的牆或上限。 這可讓過度調整大小的物件看似「細分」實體空間。 例如，大型樹狀結構可能無法容納大部分使用者的客廳，但藉由將虛擬天空放在最高的位置，實體空間就會擴展到虛擬。 這可讓使用者流覽虛擬樹狀結構的基底，並收集規模和真實世界外觀的意義。 然後，使用者可以查詢，看看它的範圍遠超過空間的實體空間。

:::row:::
    :::column:::
        Minecraft 使用類似的技巧 **[開發了概念體驗](https://minecraft.net/)**。 藉由將虛擬視窗新增至實體介面，房間內的現有物件將會放在相當大的環境內容中，但不超過空間的實體規模限制。<br>
        <br>
        *影像： HoloLens 的 Minecraft 概念體驗*
    :::column-end:::
        :::column:::
       ![HoloLens 的 Minecraft 概念體驗](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>使用 scale 進行實驗

設計人員實驗由變更物件的顯示「實際」大小來修改尺規。 同時，他們會維護單一物件位置，以接近移至檢視器的物件，而不需要實際移動。 在某些情況下，這是在某些情況下進行測試，以模擬關閉專案的功能，同時仍遵守觀看虛擬內容的可能緩和限制，而接近「緩和區域」的建議。

不過，這可能會在體驗中建立一些可能的構件：
* 如果虛擬物件代表的某個物件具有「已知」大小的檢視器，則變更調整規模而不變更位置會導致衝突的視覺提示。眼睛可能仍會因為 vergence 提示而「看到」物件的深度。如需詳細資訊，請參閱 [緩和](comfort.md) 文章。 大小會作為 monocular 提示，表示物件可能會更接近。 這些衝突的提示會導致混淆的理解，因此，檢視器通常會將物件視為保持 (，因為會有常數深度的提示) 但很快就會成長。
* 在某些情況下，小數位數的變更會被視為「即將問世」提示，其中物件可能會或可能不會被檢視器變更，但似乎是直接移到檢視器的眼睛 (這可能是令人感到不安的刺痛) 。
* 在真實世界中的比較介面上，這類調整變更有時會被視為沿著多個軸變更位置，而在某些情況下，物件會顯得較低，而不是移動較接近的 (類似于3D 移動的2D 投影中) 。
* 最後，對於沒有已知「真實世界」大小的物件 (例如，具有任意大小、UI) 元素等等的任意圖案，變更調整的功能可能會以模擬距離變更的方式運作。 檢視器不會有太多預先存在的由上而下提示，以瞭解物件的真正大小或位置，因此可以將比例視為更重要的提示來處理。

<br>

---

## <a name="see-also"></a>另請參閱
* [色彩、光線和材質](./color-light-and-materials.md)
* [印刷樣式](typography.md)
* [空間音效設計](spatial-sound-design.md)