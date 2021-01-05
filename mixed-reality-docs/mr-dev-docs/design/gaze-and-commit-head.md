---
title: 頭部注視並認可
description: 前端注視和認可輸入模型的總覽。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: 混合的現實、注視、注視目標、互動、設計、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、目標、焦點、平滑
ms.openlocfilehash: cc12c349704a63c5b95c9eede91d0486f56787a2
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847878"
---
# <a name="head-gaze-and-commit"></a>頭部注視並認可

「注視」_和「認可_」是「注視」[和「認可](gaze-and-commit.md)」輸入模型的特殊案例，其中牽涉到以使用者為目標的物件。 您可以使用次要輸入來處理目標，例如手勢的點擊或「選取」語音命令。 

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

前端圖向量已重複顯示，可供適當的目標使用，但通常最適合用於主要目標--取得較大的目標。 在大部分的情況下，1度到1.5 度的最小目標大小可允許成功的使用者動作，但通常會有3度的目標，以提供更快的速度。 使用者的目標大小實際上是2D 區域（即使是3D 專案），無論是哪一個投射都應該是目標設為區域。 提供專案為「作用中」的一些重要提示， (使用者以它為目標) 會很有説明。 這可能包含像是可見的「暫止」效果、反白顯示或按下的處理，或清除資料指標與元素的對齊。

![距離 2 公尺的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*雙計量距離的最佳目標大小*

<br>

![醒目提示注視目標物件的範例](images/gazetargeting-highlighting-940px.jpg)<br>
*醒目提示注視目標物件的範例*

## <a name="target-placement"></a>目標位置

使用者通常會在其 view 欄位中找不到太高或太低的 UI 元素。 他們大部分的注意力都是在其主要焦點周圍，大約是眼睛。 將大部分的目標放在眼部水平周圍的合理頻帶會有所幫助。 由於使用者傾向于隨時專注于相對較小的視覺區域 (的視覺範圍大約是10度) ，因此將 UI 元素群組在一起，就能在概念上將 UI 元素群組在一起，以便使用者在區域中移動其外觀時，可以使用專案與專案的醒目連結行為。 在設計 UI 時，請記住 HoloLens 與沉浸式頭戴裝置之間的視野可能有很大的變化。

![方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例](images/gazetargeting-grouping-1000px.jpg)<br>
*方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例*

## <a name="improving-targeting-behaviors"></a>改善定向行為

如果將目標設為目標的使用者意圖可以判斷或近似值，則接受近乎遺漏的互動嘗試就會很有説明，就像是正確的目標一樣。 以下是一些成功的方法，這些方法可以併入混合現實體驗中：

### <a name="head-gaze-stabilization-gravity-wells"></a>頭部注視穩定 (「重力穴」)

這應該會在大部分或所有時間開啟。 這項技術會移除使用者可能因說話和說話行為而有移動的自然頭部和頸部起伏快速變換。

### <a name="closest-link-algorithms"></a>最接近的連結演算法

這些演算法在具有稀疏互動式內容的區域中最適合使用。 如果您有很高的機率可以判斷使用者嘗試與其互動的內容，您可以藉由假設某種程度的意圖來補充其目標功能。

### <a name="backdating-and-postdating-actions"></a>Backdating 和 postdating 動作

這項機制對於要求速度的工作很實用。 當使用者在一系列的目標和啟用調動中快速移動時，假設有一些意圖。 這也適用于允許錯過的步驟，讓使用者在執行早期測試) 之前或之後稍微或之後稍微或之後稍微稍微或 50 (稍微點一下的目標上，採取動作。

### <a name="smoothing"></a>平滑處理

這項機制適用于路徑移動，因為自然的 head 移動特性而減少輕微的抖動和 wobbles。 當平滑路徑移動時，會以移動的大小和距離，而不是經過一段時間來平滑。

### <a name="magnetism"></a>磁性

這項機制可視為最接近的連結演算法的最一般版本--將游標繪製到目標上，或單純地增加 hitboxes （無論是否可見），因為使用者可能會使用某些互動式版面配置知識，以更好的方式處理使用者意圖。 這對小型目標來說很強大。

### <a name="focus-stickiness"></a>焦點黏著度

當您決定要提供哪些鄰近的互動式元素、將焦點放在焦點時，焦點會對目前焦點的元素提供偏差。 這有助於減少不穩定的焦點切換行為（當兩個專案之間的中間點有自然雜訊時）。

## <a name="see-also"></a>請參閱

* [眼動式互動](eye-gaze-interaction.md)
* [目光和停駐](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)



