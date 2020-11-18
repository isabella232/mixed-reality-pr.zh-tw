---
title: 手部功能表
description: 手形功能表可讓使用者快速地為常用的函式顯示手動連接的 UI。 這些是我們的最佳作法和建議，適用于手邊的功能表。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手、功能表、按鈕、快速存取、版面配置、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 8f9adbdbebb826a79db037f48b233e3bc5e049de
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702294"
---
# <a name="hand-menu"></a>手部功能表

![Ulnar 側邊位置](images/UX_Hero_HandMenu.jpg)

手形功能表是 HoloLens 2 中最獨特的 UX 模式之一。 它可讓您快速地顯示手動連接的 UI。 由於它可隨時存取，而且可以輕鬆地顯示和隱藏，因此非常適合快速動作。

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

您會在下列清單中找到使用手形功能表的建議最佳作法。 您也可以在 [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)中找到示範手形功能表的範例場景。

<br>


---

## <a name="best-practices"></a>最佳作法
**將按鈕數目維持在最小** 

由於手鎖的功能表與眼睛之間的距離，以及使用者傾向于隨時專注于相對較小的視覺區域 (視覺效果大約是10度) ，因此我們建議您將按鈕數目保持在最小。 根據我們的探索，有三個按鈕的一個資料行，只要將所有內容都放在視野 (FOV) 內，即使使用者將手移至 FOV 的中心，也能妥善運作。 

**利用快顯功能表進行快速動作** 

引發 arm 並維護位置，可能很容易就會導致 arm 疲勞。 針對需要短暫互動的功能表，請使用手動鎖定的方法。 如果您的功能表很複雜，而且需要延伸互動時間，請考慮改為使用世界鎖定或主體鎖定。 

**按鈕/面板角度**

功能表應該會朝向相反的肩和中間的部分：這可讓自然手移動以相反的方向與功能表互動，並避免在觸控按鈕時出現任何麻煩或不舒服的位置。 

**考慮支援單次或無人參與的作業**

請勿假設這兩個使用者的手都一律可供使用。 當一或兩個手都無法使用時，請考慮各種不同的內容，並確定您的設計帳戶會在這些情況下執行。 若要支援右手邊的功能表，您可以嘗試將功能表位置從手鎖移至世界鎖定的位置， () 。 針對無人參與的案例，請考慮使用語音命令來叫用快顯功能表。

**避免在手腕 (系統首頁按鈕附近新增按鈕)**

如果放置的功能表按鈕太靠近 [首頁] 按鈕，在與快顯功能表互動時可能會不小心觸發。

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>具有大型和複雜 UI 控制項的手功能表
<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
建議您限制在手動連接功能表上的按鈕或 UI 控制項數目。 這是因為與大量 UI 元素的延伸互動可能會導致 arm 疲勞。 如果您的經驗需要大型的功能表，請提供簡單的方式讓使用者在世界上鎖定功能表。 我們建議的技巧之一，就是在手離開或跳離使用者時，以世界鎖的方式功能表。 第二種方法是讓使用者直接抓取功能表。 當使用者放開功能表時，功能表應該是「世界鎖定」。 如此一來，使用者就可以在一段長時間內輕鬆且安心地與各種 UI 元素互動。 

當功能表被全球鎖定時，請務必提供移動功能表的方法，並在不再需要時關閉功能表。 藉由在功能表的側邊或上方提供控點，讓功能表成為可移動的。 新增 [關閉] 按鈕，讓功能表關閉。 允許功能表在使用者手上臉部時重新附加至手。 我們也建議您要求使用者 gazes，以防止啟用錯誤 (請參閱下面) 。

**顯示可用性問題的大型功能表**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**手上的世界鎖定功能表**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**手動抓取 & 提取至世界鎖定功能表**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a>如何防止啟用錯誤

如果您只是使用 [上移] 作為事件來觸發快顯功能表，則在不需要時，可能會不小心出現 () ，因為人們會 (刻意針對通訊和物件操作) 和無意地移動其手。 若要減少錯誤的啟用，請新增一個額外的步驟，除了用來叫用快顯功能表 (（例如完全開啟的手指），或使用者刻意撥雲見日手中) 。

**需要平直**

藉由要求一般開放手，您可以防止在使用者操作物件或手勢時，可能會在環境內進行通訊時發生的錯誤啟用。 

**需要注視**

藉由要求使用者以眼睛 (來看看眼睛或前端) ，它會防止啟用錯誤，因為使用者必須刻意以可調式的距離閾值（可讓使用者緩和)  (）來刻意將注意力導向手。  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>手形功能表位置最佳作法

在「人為結構」中，ulnar nerve 是在 ulna 骨骼附近執行的 nerve。 Ulna 是在 forearm 中找到的很長的骨骼，可從彎線伸展至最小的手指。

以下是以我們的探勘為基礎的2個建議位置：


:::row:::
    :::column:::
        ![Ulnar 側邊位置](images/UlnarSideHandMenu.gif)<br>
        **Ulnar 在 palm 內部**<br>
        這個位置是可靠的，因為手不會彼此重迭。 這對於正確的手動偵測和追蹤而言很重要。
    :::column-end:::
    :::column:::
        ![Ulnar 側邊位置](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar 以上的手**<br>
        此位置很適合使用者，因為他們不需要使 arm 太多，就能與手形功能表互動。 建議您將功能表 **13cm** 在掌上，並對齊 ulnar 棕櫚內的按鈕。 [深入瞭解最佳按鈕大小](interactable-object.md)<br>
        <br>
        基於技術原因，我們建議您在此位置使用一個必要的實作為：當使用者的相反方向接近與其互動時，開發人員將需要凍結功能表。 這可避免 jitteriness 重迭，也可讓您以更快的按鈕為目標。<br>
        <br>
        HoloLens 2 攝影機會在彼此分開時，正確地識別手。 任何重迭的手都可能會導致手中的功能表移離錨點位置。<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>不建議的功能表位置
我們已使用不同的功能表版面配置和位置完成使用者研究， **不建議** 使用下列功能表位置，請找出下列各項研究的缺點：


:::row:::
    :::column:::
        ![上方 arm](images/AboveArm.gif)<br>
        **Arm 上方**<br>
        1-難以維護良好的手追蹤<br>
        2-導致使用者疲勞，原因是非自然位置
    :::column-end:::
    :::column:::
        ![上方手指](images/AboveFingers.gif)<br>
        **上方手指**<br>
        1-手疲勞是因為長期持有手長時間<br>
        2-在索引和中間手指追蹤問題
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![上方的棕櫚](images/handCenter.gif)<br>
        **上方-中央棕櫚**<br>
        1-因手重迭而發生的追蹤問題<br>
        雙手疲勞是因為長期保持手，以便與功能表互動
    :::column-end:::
    :::column:::
        ![Top Fingertip ](images/TopFingerTip.gif) **top Fingertip**<br>
        1-手追蹤問題<br>
        2-手疲勞，不是以正常狀態的手<br>
        3-因手指之間的空間有限，而意外地按下按鈕並使用其他手指
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Arm 背面](images/BackOfTheArm.gif)<br>
        **Arm 背面**<br>
        1-可能會意外觸發首頁按鈕<br>
        2-不是自然或舒適的位置
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>適用于 Unity 的 MRTK (混合現實工具組) 的手中功能表
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供快顯功能表的腳本和範例幕後。 HandConstraintPalmUp 求解腳本可讓您使用各種可設定的選項，將任何物件附加至手。 MRTK 的功能表範例包含實用的選項，例如，用來防止啟用錯誤的一般棕櫚和注視需求。

* [手形功能表檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [手形功能表範例場景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

您可以使用 MRTK 範例中樞應用程式，在 HoloLens 2 中試用手中的功能表範例。 
* [MRTK 範例中樞中的手邊功能表場景](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a>另請參閱

* [游標](cursors.md)
* [手部光線](point-and-commit.md)
* [Button](button.md)
* [可互動的物件](interactable-object.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手部功能表](hand-menu.md)
* [近端功能表](near-menu.md)
* [物件集合](object-collection.md)
* [語音命令](voice-input.md)
* [鍵盤](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑桿](slider.md)
* [著色器](shader.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [顯示進度](progress.md)
* [表面磁性](surface-magnetism.md)
