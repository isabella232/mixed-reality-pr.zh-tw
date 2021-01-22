---
title: 什麼是混合實境？
description: 本文定義混合實境，並展示 AR 和 VR 裝置在混合實境頻譜中的位置。
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: 混合實境, 全像攝影, AR, VR, MR, XR, 擴增實境, 虛擬實境, 說明, 案例研究, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 什麼是虛擬實境, 什麼是擴增實境
ms.localizationpriority: high
ms.openlocfilehash: 2eac20b85ceeb9413dfc0b6820cceda2ddf335c5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583012"
---
# <a name="what-is-mixed-reality"></a>什麼是混合實境？

![在 HoloLens 2 上手部指向和行動](images/02_MixedRealitySlashMixedReality.png)

混合實境是實體和數位世界的融合，消除了人類、電腦和環境彼此互動的藩籬。 這種新型的實境功能奠基於電腦視覺、圖形處理能力、顯示器技術和輸入系統的強化。 不過，「混合實境」一詞最初是由 Paul Milgram 和 Fumio Kishino 在 1994 年的論文《[混合實境視覺顯示器分類法 (A Taxonomy of Mixed Reality Visual Displays)](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)》中提出。 他們的論文探討了 *Virtuality Continuum* 的概念，以及如何分類套用至顯示器的分類法。 從那時起，混合實境的應用就不再侷限於顯示器，而也包括：
* 環境輸入
* 空間音效
* 實際和虛擬空間中的位置和定位

![混合實境頻譜影像](images/mixedrealityspectrum-worlds.png)<br>
*影像：混合實境是實體環境與數位世界混合的結果。*

<br>

---

## <a name="environmental-input-and-perception"></a>環境輸入和認知

過去數十年來，眾人持續探索人類與電腦輸入之間的關聯性，因而造就了所謂的 *人機互動* (或簡稱 HCI) 的專業領域。 人類輸入會透過各種不同的方式進行，包括鍵盤、滑鼠、觸控、筆跡、語音，甚至是 Kinect 的框架追蹤。

在感應器和處理能力方面的提升，逐漸使環境中的電腦輸入形成新的區域。 電腦與環境之間的互動是環境理解或 *感知*，而正因如此，Windows 中顯示環境資訊的 API 名稱即稱為 [認知 API](/uwp/api/Windows.Perception)。 環境輸入會擷取諸多事物，像是使用者所處的位置 (例如[頭部追蹤](../design/coordinate-systems.md))、表面和界限 (例如[空間對應](../design/spatial-mapping.md)和[場景理解](../design/scene-understanding.md))、環境光源、環境音效、物件辨識和位置。

<br>

![顯示電腦、人類與環境之間互動的卞氏圖表](images/mixed-reality-venn-diagram-300px.png)<br> 
*影像：電腦、人類與環境之間的互動。*

<br>

**電腦處理、人類輸入和環境輸入** 這三者的組合，造就了建立真正混合實境體驗的舞台。 實體世界中的移動會轉譯成數位世界中的移動。 實體世界的界限會影響數位世界中的應用程式體驗，例如遊戲進行。 如果沒有環境輸入，體驗就無法在混合實體與數位實境間融合。<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>混合實境頻譜

因為混合實境融合了實際和數位世界，這兩個實境就定義了頻譜的兩極，稱為 Virtuality Continuum。 我們將實境的陣列稱為 *混合實境頻譜*。 左側是我們人類所在之處的實體實境。 右側則是對應的數位實境。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>擴增與虛擬實境

現今市場上大部分的行動電話幾乎都沒有環境理解功能。 他們所提供的體驗無法混合實體和數位實境。 在實體世界的影片串流上重疊圖形的體驗即為「擴增實境」  。 遮蔽您的檢視來呈現數位體驗的體驗即為「虛擬實境」  。 擴增實境與虛擬實境之間的體驗，形成了 *混合實境*：
* 從真實世界開始，放置數位物件 (例如全像投影)，如同真實存在一般。
* 從實體世界開始，另一個人的數位表示法 -- [頭像] -- 顯示他們在留言時所處的位置。 換句話說，即為不同時間點表示非同步共同作業的體驗。
* 從數位世界開始，實體世界 (例如牆和傢俱) 的實體界限會以數位方式出現在體驗中，以協助使用者避開實體物件。

<br>

![混合實境頻譜](images/mixedrealityspectrum.png)<br>
*影像：混合實境頻譜*

<br>

現今提供的多數擴增實境和虛擬實境產品，都代表此頻譜的一小部分，且被視為較大混合實境頻譜的子集。 Windows 10 以整個頻譜為基礎，並可將數位方式呈現的人員、環境和事物與真實世界混合。


## <a name="devices-and-experiences"></a>裝置和體驗

有兩種主要的裝置類型可提供 Windows Mixed Reality 體驗：
1. 裝置能夠將數位內容放在真實世界中，如同真實存在一般，是 **Holographic 裝置** 的特性。
2. 裝置能夠建立「存在感」，隱藏真實世界，而以數位體驗取而代之，是 **沉浸式裝置** 的特性。

<table>
<tr>
<th width="30%"> 特性</th><th width="35%"> 全像攝影裝置</th><th width="35%"> 沉浸式裝置</th>
</tr><tr>
<td><strong>範例裝置</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>顯示器</strong></td><td> 透明顯示器。 讓使用者在穿戴頭戴式裝置時可看到實體環境。</td><td> 不透明顯示器。 在穿戴頭戴式裝置時封鎖實體環境。</td>
</tr><tr>
<td><strong>移動</strong></td><td> 完整的六度自由移動，包括旋轉和轉譯。</td><td> 完整的六度自由移動，包括旋轉和轉譯。</td>
</tr>
</table> 


> [!NOTE]
> 無論裝置是連線到其他電腦或以行動網卡連線到其他電腦 (透過 USB 纜線或 Wi-Fi) 或是獨立的 (未連線)，都不會反映裝置是否為全像攝影還是沉浸式。 增加行動性的功能會帶來更好的體驗，且全像攝影和沉浸式裝置都可能是以行動網卡連線或是未連線的。

技術提升可實現混合實境的體驗，但目前沒有可在整個頻譜中執行體驗的任何裝置。 Windows 10 同時為裝置製造商和開發人員提供通用的混合實境平台。 現今的裝置可以支援混合實境頻譜內的特定範圍，而新型裝置則可擴大該範圍。 在未來，全像攝影裝置會變成沉浸式，而沉浸式裝置會變得更全像攝影。

<br>

![混合實境頻譜中的裝置類型](images/Final_WhatIsMixedReality07.png)<br>
*影像：裝置在混合實境頻譜上的位置*

最好能考量應用程式或遊戲開發人員想要建立的體驗類型。 這些體驗通常會以頻譜上的特定點或部分作為目標。 開發人員應考慮他們想要作為目標的裝置功能。 仰賴實體世界的體驗在 HoloLens 上的效果最佳。
* **向左 (接近實體實境)。** 使用者仍然存在於其實體環境中，且永遠不會相信他們已離開該環境。
* **中間 (完全混合實境)。** 這些體驗混合了真實世界與數位世界。 看過[野蠻遊戲](https://en.wikipedia.org/wiki/Jumanji)這部電影的觀看者，可以調整故事中所出現房屋的實體結構與叢林環境的混合方式。
* **向右 (接近數位實境)。** 使用者會體驗到數位環境，且不會察覺周遭實體環境發生的情況。

## <a name="next-discovery-checkpoint"></a>下一個探索檢查點

如果您有遵循我們安排的[探索旅程](get-started-with-mr.md)，則您正處於探索混合實境基本概念的途中。 您可以從這裡繼續進行下一個基本主題： 

> [!div class="nextstepaction"]
> [什麼是全像投影？](hologram.md)