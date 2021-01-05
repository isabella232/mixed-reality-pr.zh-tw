---
title: 可互動的物件
description: 按鈕一直以來都是用來觸發2D 抽象世界中事件的比喻。 在三維混合現實世界中，我們不再需要局限于這種抽象概念。
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、提示、ui、ux、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、音訊
ms.openlocfilehash: fb7004c22602683e4edb1e38784cac5c0b7479c4
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847865"
---
# <a name="interactable-object"></a>可互動的物件

![Interactible 物件](images/UX_Hero_Interactable.jpg)

按鈕一直以來都是用來觸發2D 抽象世界中事件的比喻。 在三維混合現實世界中，我們不再需要局限于這種抽象概念。 任何專案都可以是觸發事件的 **互動物件** 。 互動物件可以是來自資料表咖啡杯的任何事物，以及 midair 中的氣球。 我們仍會在某些情況下（例如在對話方塊 UI 中）使用傳統按鈕。 按鈕的視覺標記法視內容而定。

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>互動物件的重要屬性

### <a name="visual-cues"></a>視覺提示

視覺提示是從燈光感應式的提示，由眼睛所接收，並由視覺效果系統在視覺感知期間處理。 由於視覺系統在許多物種中是主要的，尤其是人們的視覺提示，是世界的認知方式的一大來源資訊。

因為全像是混合的真實世界環境混合，所以很難瞭解您可以與哪些物件互動。 針對您體驗中的任何互動物件，請務必為每個輸入狀態提供差異的視覺提示。 這可協助使用者瞭解您的體驗的哪個部分是互動，並使用一致的互動方法來確保使用者的信心。

<br>

---

### <a name="far-interactions"></a>遠的互動

對於使用者可以與注視、手光線和移動控制器光線互動的任何物件，建議您對這三種輸入狀態使用不同的視覺提示：

:::row:::
    :::column:::
       ![interactibleobject-狀態-預設值](images/interactibleobject-states-default.jpg)<br>
       **預設 (觀察) 狀態**<br>
        物件的預設閒置狀態。
    資料指標不在物件上。 未偵測到手。
    :::column-end:::
    :::column:::
       ![interactibleobject-狀態-目標](images/interactibleobject-states-targeted.jpg)<br>
        **目標 (將滑鼠停留) 狀態**<br>
        當物件以注視游標、手指鄰近或移動控制器的指標為目標時。
    資料指標位於物件上。 偵測到手、準備就緒。
    :::column-end:::
    :::column:::
       ![interactibleobject-狀態-已按下](images/interactibleobject-states-pressed.jpg)<br>
       **已按下的狀態**<br>
        當您按下滑鼠按鍵時，按一下滑鼠右鍵或移動控制器的選取按鈕。
    資料指標位於物件上。 偵測到手，以空調的方式進行。
    :::column-end:::
:::row-end:::

<br>

---

您可以使用醒目提示或調整之類的技術，提供使用者輸入狀態的視覺提示。 在混合的現實情況下，您可以在 [開始] 功能表和使用應用程式列按鈕的情況下，找到將不同輸入狀態視覺化的範例。 

以下是這些狀態在「全像全像」 **按鈕** 上的樣子：

:::row:::
    :::column:::
       ![interactibleobject-狀態-預設值](images/MRTK_InteractableState-default.jpg)<br>
       **預設 (觀察) 狀態**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-狀態-目標](images/MRTK_InteractableState-targeted.jpg)<br>
        **目標 (將滑鼠停留) 狀態**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-狀態-已按下](images/MRTK_InteractableState-pressed.jpg)<br>
       **已按下的狀態**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>接近互動 (直接)  

HoloLens 2 支援明確的手追蹤輸入，可讓您與物件互動。 如果沒有 haptic 的意見反應和完美的深度感知，就很難分辨出您手中的手離物件或您是否觸及。 請務必提供足夠的視覺提示來傳達物件的狀態，特別是以該物件為依據的實際狀態。

使用視覺效果意見反應來傳達下列狀態：
* **預設 (觀察)**：物件的預設閒置狀態。
* **停留**：當手近了全像影像時，變更視覺效果以傳達該手的目標是全像全像。 
* **距離和互動點**：當手進行全像投影、設計意見反應以傳達預期的互動時間點，以及物件與手指之間的距離
* **連絡人開始**：變更視覺效果 (淺色、色彩) ，以傳達觸控已發生的情況
* **Grasped**：在 Grasped 物件時，變更視覺效果 (淺色、色彩) 
* **連絡人結束**：當觸控結束時，變更視覺效果 (淺色、色彩) 

<br>

---

:::row:::
    :::column:::
        ![將游標暫留 () ](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **將游標暫留 ()**<br>
        根據手近距離的醒目提示。
    :::column-end:::
    :::column:::
        ![將滑鼠停留 (附近) ](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **將滑鼠停留 (附近)**<br>
        根據右邊的距離醒目提示大小變更。
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![觸控/按下](images/640px-interactibleobject-states-near-press.jpg)<br>
        **觸控/按下**<br>
        視覺效果加上音訊意見反應。
    :::column-end:::
    :::column:::
        ![把握](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **把握**<br>
        視覺效果加上音訊意見反應。
    :::column-end:::
:::row-end:::

<br>

<br>

---

[HoloLens 2 上的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)是如何視覺化不同輸入互動狀態的範例：

:::row:::
    :::column:::
        ![Default](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **預設值**<br>
    :::column-end:::
    :::column:::
        ![暫留](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **暫留**<br>
        顯示以鄰近性為基礎的光源效果。
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![觸控](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **觸控**<br>
        顯示 ripple 效果。
    :::column-end:::
    :::column:::
        ![按鍵](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **按鍵**<br>
        移動 front 盤子。
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>HoloLens 2 上的「環形」視覺提示<br>
        在 HoloLens 2 上有一個額外的視覺提示，可協助使用者深入瞭解。 當 fingertip 接近物件時，靠近其 fingertip 的環形會顯示並縮小。 當觸達已按下的狀態時，環形最終會聚合成點。 此 visual affordance 可協助使用者瞭解它們與物件之間的距離。<br>
        <br>
        *影片迴圈：根據鄰近範圍方塊的視覺效果意見反應範例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![關於手近距離的視覺回饋](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>音訊提示

針對直接互動，適當的音訊意見反應可大幅改善使用者體驗。 使用音訊意見反應來傳達下列提示：
* **連絡人開始**：觸控開始時播放音效
* **連絡人結束**：觸控端播放音效
* **抓取開始**：抓取開始時播放音效
* **抓取結束**：抓取結束時播放音效

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>語音命令<br>
        針對任何互動物件，請務必支援替代的互動選項。 根據預設，我們建議針對任何互動的物件支援 [語音命令](../out-of-scope/voice-design.md) 。 若要改善可搜尋性，您也可以在停留狀態期間提供工具提示。<br>
        <br>
        *影像： voice 命令的工具提示*
    :::column-end:::
        :::column:::
       ![語音命令](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>大小調整建議 

為了確保所有的互動物件都能輕易地觸及，建議您確定互動符合其與使用者的距離，以符合最小的大小。 視覺角度通常是以視覺弧線的角度來測量。視覺角度取決於使用者的眼睛和物件之間的距離，並保持不變，而目標的實體大小可能會隨著使用者的距離變更而改變。 若要根據與使用者之間的距離來判斷物件的必要實體大小，請嘗試使用視覺角度計算機（如 [這一](https://elvers.us/perception/visualAngle/)）。

以下是互動內容的最小大小建議。


### <a name="target-size-for-direct-hand-interaction"></a>直接接觸互動的目標大小

| 距離 | 視角 | 大小 |
|---------|---------|---------|
| 45 cm  | 小於2° | 1.6 x 1.6 cm |

![直接接觸互動的目標大小](images/TargetSizingNear.jpg)<br>
*直接接觸互動的目標大小*

<br>

### <a name="target-size-for-buttons"></a>按鈕的目標大小

建立直接互動的按鈕時，建議使用較大的大小（3.2 x 3.2 cm），以確保有足夠的空間可包含圖示且可能有一些文字。

| 距離 | 最小大小 |
|---------|---------|
| 45 cm  | 3.2 x 3.2 cm |

![按鈕的目標大小](images/TargetSizingButtons.png)<br>
*按鈕的目標大小*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>手動光線或注視互動的目標大小
| 距離 | 視角 | 大小 |
|---------|---------|---------|
| 2分鐘  | 不小於1° | 3.5 x 3.5 cm |

![手動光線或注視互動的目標大小](images/TargetSizingFar.jpg)<br>
*手動光線或注視互動的目標大小*


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK 中的互動物件 (Unity 的混合現實工具組) 

在 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 中，您可以使用腳本 [**互動**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 讓物件回應各種類型的輸入互動狀態。 它支援各種類型的主題，可讓您藉由控制物件屬性（例如色彩、大小、材質和著色器）來定義視覺狀態。

* [互動](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [手邊互動範例場景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit 的標準著色器提供各種選項，例如可協助您建立視覺和音訊提示的 **相近光源** 。
* [MRTK 標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a>請參閱

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
