---
title: 目光和停駐
description: 取得混合現實應用程式的眼睛和前端和停留輸入模型的一般總覽。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合的現實、注視、停留、互動、設計、眼睛追蹤、head 追蹤、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: c65c13b06df70ed5471b283ad349dd72e1575018a98913177983d7a13571d666
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213672"
---
# <a name="gaze-and-dwell"></a>目光和停駐

當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。
在某些內容中，語音命令也可能不可靠，例如在過高的情況下。
「注視」和「停留」提供了一種熟悉且簡單的主要機制，讓您在 HoloLens 上運作並無人參與。
此外，「注視」和「停留」是很棒的回復，與操作環境中的雜訊干擾或無回應條件無關。
我們將看看兩種不同的眼睛 _和停留_： [前端和停留](gaze-and-dwell-head.md) ，以及 [眼睛和停留](gaze-and-dwell-eyes.md)。

## <a name="scenarios"></a>案例

當某人的手中有其他工作忙碌的情況下，看看並停留擅長，因為環境或社交條件約束，所以語音不是100% 可靠或無法使用。
穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。
他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。
車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。
注視和停留可讓使用 HoloLens 的人員安心地流覽其參考資料，而不會中斷其工作流程。

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>頭部注視並佇留</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
    </tr>
     <tr>
        <td>眼部目光和停駐</td>
        <td>❌ 無法使用</td>
        <td>✔️ 建議使用</td>
        <td>❌ 無法使用</td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a>另請參閱

* [眼動式互動](eye-gaze-interaction.md)
* [HoloLens 2 的眼球追蹤](eye-tracking.md)
* [目光和行動](gaze-and-commit.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)