---
title: 混合現實的音效
description: 混合現實中的音訊可以提高 UI 互動的使用者信心，並 immerse 使用者體驗。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空間音效、環繞音效、3d 音訊、3d 音效、空間音訊、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、個案研究、聲場
ms.openlocfilehash: 50a5b4a634eec5a326158975f70fa385ce7af6a8
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703254"
---
# <a name="audio-in-mixed-reality"></a>混合現實的音效
音訊是設計和生產力在混合現實中不可或缺的一部分。 音效可以：
* 提高筆勢和語音互動的使用者信賴度。
* 引導使用者進行後續步驟。
* 有效地結合虛擬物件與真實世界。

混合現實耳機的低延遲 head 追蹤（包括 HoloLens）支援高品質的 HRTF 型 spatialization。 您可以在應用程式中 spatialize 音訊，以：
* 注意視覺元素。
* 協助使用者維護其真實世界周圍的認知。

聲場更深入地連接全像混合現實世界的影像。 它會提供有關環境和物件狀態的提示。

請參閱 [使用音訊之設計](spatial-sound-design.md)的詳細範例。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第一代) </strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>空間化</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Spatialization 硬體加速</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>在混合現實中使用音效
[在混合現實中使用](spatial-sound-design.md) 音效需要的方法與觸控和鍵盤和滑鼠應用程式不同。 主要的音效設計決策包括要 spatialize 的音效，以及要 sonify 的互動。 這些決策會大幅影響使用者信賴度、生產力和學習曲線。

### <a name="case-studies"></a>案例研究
HoloTour 幾乎會讓使用者在世界各地旅遊和歷程記錄網站。 請參閱 HoloTour 案例研究的 [音效設計](case-study-spatial-sound-design-for-holotour.md) 。 用來捕捉主體空間的特殊麥克風和轉譯設定。

RoboRaid 是適用于 HoloLens 的高能源射擊。 RoboRaid 案例研究的 [音效設計](case-study-using-spatial-sound-in-roboraid.md) 說明了可確保使用空間音訊來發揮最大效果的設計選擇。

## <a name="spatialization"></a>空間化
Spatialization 是空間音訊的方向元件。 若為7.1 家用劇院設定，spatialization 就像在 loudspeakers 之間移動一樣簡單。 但對於混合式的耳機，使用 HRTF 型技術很重要且舒適。 Windows 提供以 HRTF 為基礎的 spatialization，這項支援在 HoloLens 2 的硬體加速。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>我應該 spatialize 嗎？
Spatialization 可以改善混合現實應用程式中的許多音效。 Spatialization 會從接聽程式的頭部取出聲音，將它放在世界各地。 如需在應用程式中有效使用 spatialization 的建議，請參閱 [空間音效設計](spatial-sound-design.md)。

### <a name="spatializer-personalization"></a>空間定位器個人化
Hrtf 會操控各頻間的耳之間的層級和階段差異。 它們是以人類 head、torso 和 ear (pinnae) 的實體模型和測量為基礎。 我們的大腦會回應這些差異，以提供音效的觀察方向。

每個人都有獨特的 ear 形狀、前端大小和 ear 定位。 因此最適合您的 Hrtf。 為了提高 spatialization 準確度，HoloLens 會使用您的 pupilary 距離，從耳機顯示器 (IPD) ，以調整您的前端大小 Hrtf。

### <a name="spatializer-platform-support"></a>空間定位器平臺支援
Windows 透過 [ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 hrtf。 此 API 會向應用程式公開 HoloLens 2 HRTF 硬體加速。

### <a name="spatializer-middleware-support"></a>空間定位器中介軟體支援
下列協力廠商音訊引擎可使用 Windows 的 Hrtf 支援。
* [Unity 音訊引擎外掛程式](../develop/unity/spatial-sound-in-unity.md)
* [Wwise 音訊引擎外掛程式](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>聲學
空間音訊大約是方向。 其他維度包括遮蔽、障礙物、回音、portalling 和來源模型。 這些維度 *統稱為聲場。* 在沒有聲場的情況下，hrtf 音效缺乏認知距離。

聲場的治療範圍從簡單到非常複雜。 您可以使用任何音訊引擎所支援的簡單回音，將 hrtf 音效推送至接聽程式的環境。 聲場系統（例如 [聲場專案](https://aka.ms/acoustics)  ）提供更豐富且更吸引人的聲場處理。 聲場專案可以建立音效上牆、大門和其他場景幾何的效果模型。 在開發階段已知相關場景幾何的情況下，這是有效的選項。

## <a name="next-steps"></a>後續步驟
- [Unity 中的空間音效](../develop/unity/spatial-sound-in-unity.md)
- [如何在混合現實應用程式中使用音效](spatial-sound-design.md)
