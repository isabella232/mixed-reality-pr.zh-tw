---
title: 頭部注視並佇留
description: 頭部注視並佇留輸入模型的概觀
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, 注視, 佇留, 互動, 設計
ms.openlocfilehash: 825623b00107eec400b4df926c8980c92b065902
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680925"
---
# <a name="head-gaze-and-dwell"></a>頭部注視並佇留

當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。 語音命令 (例如手勢) 在特定情境 (例如極度喧噪的情況) 中可能不大可靠。 此外，使用語音來控制電腦並不十分普遍，但的確可取得資料流！ 「頭部注視並佇留」提供最熟悉且容易掌握的機制，可在 HoloLens 上以抬頭和免持式運作。 此外，「頭部注視並佇留」 100% 可靠，完全不受雜訊干擾，而且在作業環境中也沒有靜音限制。

## <a name="scenarios"></a>案例

當人的手中有其他工作忙碌的情況下，您可以擅長，而語音也不是100% 的可靠性，或是因為環境或社交條件約束而無法使用。 穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。 他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。 車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。 前端和停留可讓使用 HoloLens 的人員安心地流覽其參考資料，而不會中斷其工作流程。 

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>輸入模型</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>頭部注視並佇留</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
    </tr>
</table>


## <a name="design-principles"></a>設計原則

**避免「使用注視作為手段」**

「頭部注視並佇留」需要直覺式視覺化回饋，但是太多回饋可能會引起焦慮。 回饋應協助使用者知道他們所定向的目標，但不會針對其意圖予以自動選取。 讀取文字、圖示和標籤需要額外的考量，在選取之前為人員提供吸收資訊的空間。
    
**追求 Goldilocks 速度**
    
佇留互動可根據瀏覽的影響而有不同的計時器 - 較多常用功能通常受益於更快速的填滿時間，而較多衍生性功能則可受益於較長的填滿時間。 使用填滿效果來顯示這些計時器時，填滿色彩的動畫曲線對於較快速填滿時間的感覺有正面影響。 應可慮讓使用者決定快速/中等/緩慢填滿速度覆寫。
    
**Say no-no to yo-yo 效應**

溜溜球效應是當內容和「頭部注視並佇留」控制項的放置方式強迫人們要不斷地重複仰視和俯視時，可能出現的不舒適頭部移動模式。 例如，底部的 [流覽] 和 [停留] 按鈕的清單導覽會引發停留的迴圈、在結果中查看、向下切入到停留等等。這種產生的模式不舒服，而且應該避免將導覽控制項放在需要較低的集中位置。 與效應相關的佇留按鈕放置方式，對於舒適度而言很重要。

<br>

---


## <a name="ux-guidelines-and-best-practices"></a>UX 指導方針和最佳作法

### <a name="target-sizes"></a>目標大小
  為了方便存取，前端和停留目標必須夠大，才能輕鬆地查看，並且在指定的時間為目標保持一個穩定的狀態。 我們建議的最小目標大小為2度，以達成最舒適的體驗。 

### <a name="visual-feedback"></a>視覺化回饋

使用放射狀填滿來表示佇留計時器時，從按鈕中心開始。 相較於不同按鈕上的所有不同方向，一致的回應比較不容易混淆。 

  * 有方向的互動 (例如，向上/向下/左/右瀏覽等) 可以打破此規則。 例如，Microsoft Dynamics 365 Guides 讓「下一頁/上一頁」成為左右填滿則屬例外狀況。
  * 在關閉按鈕等情境下，請考慮從外部反轉放射狀填滿。 按壓按鈕的反向感覺是可維護的良好視覺模式。 

### <a name="progressive-disclosure"></a>漸進式揭露

漸進式揭露表示只有盡可能詳細顯示與互動的每個階段相關。 對於佇留，這表示佇留目標會顯現於醒目提示 (例如，在清單控制項中)。

 ### <a name="oversized-targets"></a>過大的目標
佇留區域可大於非使用中的圖示，使其更容易使用，例如 Microsoft Dynamics 365 Guides 中的 [上一頁] 按鈕。

### <a name="prevent-flickering-with-delayed-feedback"></a>使用延遲回饋防止閃爍
在開始視覺化回饋前使用短暫延遲，可避免有人經過佇留目標時發生閃爍。
* 針對頻繁互動的按鈕，請將延遲保持在很短的時間，讓應用程式感覺很慢。
* 對於不常進行互動的按鈕而言，較長的延遲可能適合避免介面感覺 twitchy。


<br>

---

## <a name="ui-patterns"></a>UI 模式

### <a name="high-frequency-buttons"></a>高頻率按鈕

:::row:::
    :::column:::
        高頻率按鈕是常用於整個應用程式的按鈕。 Microsoft Dynamics 365 Guides 中的下一頁和上一頁按鈕都是不錯的範例。<br>
        <br>
        **建議**<br>
  * 高頻率按鈕應該很大，而且可以更輕鬆地使用列印頭
  * 保持近乎眼睛的高度，以避免人體工學緊張。<br>
        <br>
*影像： Microsoft Dynamics 365 指南 [下一步] 按鈕*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南 [下一步] 按鈕](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>低頻率按鈕
低頻率按鈕是整個應用程式中不會定期互動的按鈕。 可存取 [設定] 功能表的按鈕，或可清除所有工作的按鈕都是不錯的範例。

* 嘗試讓這些按鈕不在常用的頭部注視路徑中，以免意外啟動。 

<br>

---

### <a name="confirmations"></a>確認

:::row:::
    :::column:::
        當某個動作有重大影響時 (例如收費、刪除工作或開始長時間處理)，最好確認個人要選取按鈕。<br>
        <br>
        **建議**<br>
  * 在主要按鈕上顯示選取醒目提示。
  * 與選取醒目提示同時顯示佇留目標。
  * 對於次要按鈕，顯示頭部注視的佇留目標。<br>
        <br>
*影像： Microsoft Dynamics 365 指南確認對話方塊*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南確認對話方塊](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>切換按鈕
切換按鈕需要一些微妙的邏輯，才能正常運作。 當人員佇留在切換按鈕並啟動它時，他們需要結束按鈕，然後回頭重新啟動佇留邏輯。 切換按鈕會有清楚的作用與非作用中狀態很重要。 

<br>

---

### <a name="list-views"></a>清單檢視

:::row:::
    :::column:::
        列出視圖會針對前端和停留輸入提供特定挑戰。 人們需要能夠掃描內容，而不覺得必須偷偷摸摸地環顧佇留目標。<br>
        <br>
**建議**<br>
  * 當標頭 gazed 但不會開始停留時，請將整個資料列反白顯示，除非前端看著特定的停留目標。
  * 當資料列反白顯示以在視覺雜訊上剪下時，才會顯示停留目標。
  * 與停留目標的位置清楚且一致。
  * 請勿同時顯示所有停留目標，以避免重複的 UI。
  * 盡可能重複使用相同的模式，以建立 UX 熟悉度。<br>
        <br>
*影像： Microsoft Dynamics 365 指南清單*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南清單](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>另請參閱
* [目光和行動](gaze-and-commit.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)
