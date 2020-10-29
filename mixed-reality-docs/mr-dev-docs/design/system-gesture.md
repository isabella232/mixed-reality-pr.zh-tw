---
title: 開始手勢
description: 開始手勢以呼叫 [開始] 功能表。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合的現實、手勢、互動、設計
ms.openlocfilehash: 909472abfec34f75a2f5fa810f87003978cc6a5e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680437"
---
# <a name="start-gesture"></a>開始手勢

開始手勢是用來叫用 [開始] 功能表的手手勢。 這相當於按下鍵盤上的 Windows 鍵、Xbox 控制器上的 Xbox 按鈕，或沉浸式耳機移動控制器上的 Windows 按鈕。 請務必瞭解哪些手勢會在每個混合現實裝置上保留給系統，以避免在設計互動時產生衝突。

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
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>盛開</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>手腕按鈕</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>眼睛和棕櫚</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>盛開
為了啟動 HoloLens (第1代) 中的 [開始] 功能表，我們設計了「Bloom」，這是模擬花卉櫻花的符號手勢。 它是 surefooted 互動、輕鬆執行和快速回收的獨特方式。 若要在 HoloLens (第一代) 上執行 bloom 手勢，請將您的手中的手上移一層，並將您的手合在一起，然後透過散佈手指來開啟您的手。

:::row:::
    :::column:::
        ![Bloom 關閉](images/bloom-close.png)<br>
        **步驟1：輕鬆搭配使用**<br>
    :::column-end:::
    :::column:::
        ![Bloom 開啟](images/bloom-open.png)<br>
        **步驟2：使用輕鬆散佈的掌上**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>開始手勢
在 HoloLens 2 中，我們將 Bloom 手勢取代為虛擬手腕按鈕，以允許不需要額外教學的更 instinctual 互動。 藉由顯示使用者手腕上的按鈕，可以直覺地聯繫，並將其與他人一起按。

:::row:::
    :::column:::
        ![手腕按鈕就緒](images/wrist-button-ready.png)<br>
        **步驟1：掌上一步，顯示手腕按鈕**<br>
    :::column-end:::
    :::column:::
        ![手腕按鈕按下](images/wrist-button-press.png)<br>
        **步驟2：按手腕按鈕**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a>單向開始手勢

> [!IMPORTANT]
> 若要讓右手開始手勢正常運作：
>
> 1. 您必須更新為2019年11月更新 (組建 18363.1039) 或更新版本。
> 1. 您的眼睛必須在裝置上校正，讓眼睛追蹤能夠正常運作。 如果您看不到 [開始] 圖示周圍的軌道點，則裝置上不會校正您的眼睛。

您也可以只使用一手勢來執行開始手勢。 若要這樣做，請向您的手中拿出手，並查看您內部手腕上的 [ **開始] 圖示** 。 **當您隨時留意圖示時** ，請將您的 thumb 和索引手指放在一起。<br>
:::row:::
    :::column:::
        ![手腕按鈕就緒](images/wrist-button-ready.png)<br>
        **步驟1：掌上一步，顯示手腕按鈕**<br>
    :::column-end:::
    :::column:::
        ![手腕按鈕縮小](images/wrist-button-pinch.png)<br>
        **步驟2：按鈕上的眼睛，然後縮小**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>另請參閱

* [本能互動](interaction-fundamentals.md)
* [眼睛](eye-tracking.md)
* [語音輸入](voice-input.md)
