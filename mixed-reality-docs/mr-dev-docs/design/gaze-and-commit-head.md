---
title: 頭部注視並認可
description: 頭部注視並認可輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, 注視, 注視定向, 互動, 設計
ms.openlocfilehash: 76223dd375e76d943183bc745792e2cb9d3d0601
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679957"
---
# <a name="head-gaze-and-commit"></a>頭部注視並認可
_前端和認可_ 是 [注視和認可](gaze-and-commit.md) 輸入模型的特殊案例，其牽涉到將物件的方向指向順向 (前端方向) ，然後使用次要輸入（例如手勢的點擊點或語音命令「選取」）進行處理。 

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
        <td>頭部注視並認可</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</td>
        <td>➕ 替代選項</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>目標大小調整和回饋
前端圖向量已重複顯示，可供適當的目標使用，但通常最適合用於主要目標--取得較大的目標。 最小的目標大小為1到1.5 度，在大部分情況下允許成功的使用者動作，但以3度為目標的目標通常會有更高的速度。 請注意，使用者定向的大小實際上是 2D 區域 (即使是 3D 元素)，無論哪個投影面向他們都應該是可作為目標的區域。 提供某個元素為「作用中」的一些重要提示， (使用者以它為目標) 相當有用。 這可能包含像是可見的「暫止」效果、反白顯示或按下的處理，或清除資料指標與元素的對齊。

![距離 2 公尺的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*距離 2 公尺的最佳目標大小*

<br>

![醒目提示注視目標物件的範例](images/gazetargeting-highlighting-940px.jpg)<br>
*醒目提示注視目標物件的範例*

## <a name="target-placement"></a>目標位置
使用者通常會在其視野中找不到非常高或非常低的 UI 元素，著重在其主要焦點區域周圍（大約是眼睛）。 將大部分的目標放在眼部水平周圍的合理頻帶會有所幫助。 假設使用者傾向於隨時將焦點放在相對較小的視覺區域 (視覺的注意視錐大約是 10 度)，將概念上相關的 UI 元素聚集在一起，可以在使用者目光掃過區域時運用逐一項目的注意鏈結行為。 在設計 UI 時，請記住 HoloLens 與沉浸式頭戴裝置之間的視野可能有很大的變化。

![方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例](images/gazetargeting-grouping-1000px.jpg)<br>
*方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例*

## <a name="improving-targeting-behaviors"></a>改善定向行為
如果將目標設為目標的使用者意圖可 (或近似值緊密地) ，則在互動時接受近乎遺漏的嘗試，可能會很有説明，因為它們的目標正確。 以下是一些可在混合現實體驗中併入的成功方法：

### <a name="head-gaze-stabilization-gravity-wells"></a>頭部注視穩定 (「重力穴」)
這應該會在大部分或所有時間開啟。 這項技術會移除使用者可能因查看和說話行為而有所移動的自然頭部和頸部起伏快速變換。

### <a name="closest-link-algorithms"></a>最接近的連結演算法
這些最適合用於具有疏鬆互動式內容的區域。 如果您有很高的機率可以判斷使用者嘗試與其互動的內容，您可以藉由假設某種程度的意圖來補充其目標功能。

### <a name="backdating-and-postdating-actions"></a>Backdating 和 postdating 動作
這項機制對於要求速度的工作很實用。 當使用者在一系列的目標和啟用調動中快速移動時，假設有一些意圖，並允許錯過的步驟，讓使用者在執行早期測試) 之前或之後稍微或之後稍微或 50 (稍微。

### <a name="smoothing"></a>平滑處理
這項機制對於路徑移動很有説明，因為自然的標頭移動特性，減少了輕微的抖動和 wobble。 當平滑路徑移動時，會以移動的大小和距離，而不是經過一段時間來平滑。

### <a name="magnetism"></a>磁性
這項機制可視為最接近的連結演算法的最一般版本--將游標繪製到目標上，或單純地增加 hitboxes （無論是否可見），因為使用者可能會使用某些互動式版面配置知識，以更好的方式處理使用者意圖。 這對於小型目標特別有效果。

### <a name="focus-stickiness"></a>焦點黏著度
當您決定要將焦點放在哪個附近的互動式專案時，焦點會與目前焦點的元素提供偏差。 這有助於減少不穩定的焦點切換行為（當兩個專案之間的中間點有自然雜訊時）。


## <a name="see-also"></a>另請參閱
* [眼動式互動](eye-gaze-interaction.md)
* [目光和停駐](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)



