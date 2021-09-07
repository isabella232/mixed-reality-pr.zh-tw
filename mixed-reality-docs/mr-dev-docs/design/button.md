---
title: Button
description: 瞭解如何使用按鈕觸發立即動作，這是其中一個混合現實的基礎元件。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、ui、ux、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、按鈕
ms.openlocfilehash: 4b3a9bda852c7a83ee603c3f2340d44f4be89f4d
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2021
ms.locfileid: "122682962"
---
# <a name="button"></a>Button

![Button](images/UX_Hero_Button.jpg)

按鈕是混合現實中最基本且最重要的 UI 元素之一。 它可讓您的使用者觸發立即動作。 由於混合式事實沒有實際的意見反應，因此請務必提供足夠的視覺和音訊意見反應，以提升使用者的互動信賴度。 

在 HoloLens 2 按鈕設計中，以許多設計反復專案、prototypings 和使用者研究研究為基礎，我們整合了多個視覺 affordances 和音訊提示，以協助使用者深入瞭解並在空間中進行互動。 

## <a name="visual-affordances"></a>Visual affordances

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWJHgW]


:::row:::
    :::column:::
       ![顯示相近光線效果的按鈕](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **近亮光**<br>
    :::column-end:::
    :::column:::
       ![顯示焦點醒目提示效果的選取按鈕](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **焦點醒目提示**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![顯示具有壓縮箱效果的按鈕](images/UX_Button_Affordance_Compression.jpg)<br>
       **壓縮框架**<br>
    :::column-end:::
    :::column:::
       ![顯示觸發程式脈衝效果的按鍵](images/UX_Button_Affordance_Pulse.jpg)<br>
        **觸發程式上的脈衝**<br>
    :::column-end:::
:::row-end:::

<br>

## <a name="audio-cues"></a>音訊提示

適當的音訊意見反應可大幅改善使用者體驗。 HoloLens 2 的按鈕會提供音訊意見反應，以傳達下列提示：
* **連絡人開始**：觸控開始 (近距離互動時播放音效) 
* **連絡人** 端：在觸控結束時播放音效 (近距離互動) 
* 縮小 **開始**：在縮小選取 (與注視或放射線的互動時播放音效) 
* 縮小 **結束**：在縮小版本上播放音效 (與注視或放射線的互動) 

<br>

---

:::row:::
    :::column:::
        ## <a name="voice-commandingbr"></a>語音命令<br>
        針對混合現實中的任何按鈕，請務必支援替代的互動選項。 根據預設，我們建議針對任何按鈕支援語音命令。 在 HoloLens 2 的按鈕設計中，我們會在停留狀態期間提供工具提示，以改善可搜尋性。
    :::column-end:::
        :::column:::
       ![語音輸入](images/UX_Hero_VoiceCommand.jpg)<br>
        *影像： voice 命令的工具提示*
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

## <a name="design-guidelines"></a>設計指導方針

### <a name="avoid-transparent-backplate"></a>避免透明 backplate
當您使用按鈕來設計功能表 UI 時，建議使用不透明的 backplate。 基於下列原因，不建議使用透明 backplates：
* 難以與互動，因為很難瞭解如何按下按鈕來觸發事件
* 複雜實體環境的可讀性問題
* 透過透明板顯示的全像投影會在搭配深度 LSR 穩定技術使用時顯示游泳效果問題。

如需色彩選擇的詳細資料，以及全像顯示的指導方針，請參閱 [設計全息顯示的內容](designing-content-for-holographic-display.md) 。

![透明 ui 的透明 ui 範例 ](images/color_transparent_examples.jpg)
 *backplate*

<br>

### <a name="use-shared-backplate"></a>使用共用 backplate
針對多個按鈕，建議使用共用 backplate，而不是個別按鈕的 backplate。

* 減少視覺雜訊和複雜度
* 清除群組  

![共用 ](images/Button_Design_SharedBackplate.png
)
 *UI 的* 共用 backplate 範例 backplate

<br>

---

## <a name="button-in-mrtk-mixed-reality-toolkit"></a>MRTK (混合現實工具組的按鈕) 
適用于 **[Unity 的 MRTK](/windows/mixed-reality/mrtk-unity/)** 和 **[MRTK for Unreal](/windows/mixed-reality/develop/unreal/unreal-mrtk-introduction)** 提供各種類型的按鈕 prefabs，包括 HoloLens 2 樣式按鈕。 HoloLens 2 按鈕元件包含此頁面中引進的所有視覺效果意見反應和互動詳細資料。 藉由使用它，您可以利用我們的設計人員、開發人員、研究人員所做過的許多設計反覆運算和使用者研究的結果。

如需詳細指示和自訂的範例，請參閱 [MRTK 按鈕](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 。

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