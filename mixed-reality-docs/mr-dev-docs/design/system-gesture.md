---
title: 開始手勢
description: 瞭解如何使用開始手勢來呼叫 HoloLens 上的 [開始] 功能表，以及 Windows Mixed Reality 沉浸式耳機。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合的現實、手勢、互動、設計、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、bloom
ms.openlocfilehash: d0f3bd81cab945a01a523806ebaf4546752d74c1
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583229"
---
# <a name="start-gesture"></a>開始手勢

開始手勢是用來叫用 [開始] 功能表的手手勢。 這相當於按下鍵盤上的 Windows 鍵、Xbox 控制器上的 Xbox 按鈕，或沉浸式耳機移動控制器上的 Windows 按鈕。 請特別注意每個混合現實裝置上的保留系統手勢，以避免在設計互動時產生衝突。

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

我們設計了 "Bloom"，將 HoloLens 中的 [開始] 功能表 (第一代) ，也就是模擬花卉櫻花的符號手勢。 它是確定-footed 互動、簡單易用以及快速重新叫用的獨特方式。 若要使用手勢，請將您的手中的手朝您手上一處，然後散佈手指來開啟您的手。

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

在 HoloLens 2 中，我們將 Bloom 手勢取代為虛擬手腕按鈕，這對使用者來說更 instinctual。 藉由顯示使用者手腕上的按鈕，可以直覺地聯繫，並將其與他人一起按。

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

您也可以只使用一手勢來使用開始手勢。 將您手上的手向您手上，看看您的內部手腕上的 [ **開始] 圖示** 。 **當您隨時留意圖示時**，請將您的 thumb 和索引手指放在一起。<br>
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