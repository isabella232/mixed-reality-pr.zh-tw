---
title: 什麼是混合實境？
description: 討論混合現實，demomstrating 在混合的現實範圍上使用 AR 和 VR 裝置。
author: qianw211
ms.author: v-qianwen
ms.date: 07/01/2021
ms.topic: article
keywords: 混合實境, 全像攝影, AR, VR, MR, XR, 擴增實境, 虛擬實境, 說明, 案例研究, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 什麼是虛擬實境, 什麼是擴增實境
ms.localizationpriority: high
ms.openlocfilehash: 088bc9a978bd236069ddc1beab40387c607b906e
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634319"
---
# <a name="what-is-mixed-reality"></a>什麼是混合實境？

混合的現實是運算的下一波，接著是大型主機、電腦和智慧型手機。 混合現實是消費者和企業的主流。  它從螢幕系結的體驗 liberates 我們，提供與我們生活空間中的資料互動，以及與我們的朋友互動的 instinctual 互動。  在全球各地的全球各地的線上流覽流覽，都能透過他們的掌上型裝置遇到混合的現實情況。  Mobile AR 今天在社交媒體上提供最主流的混合現實解決方案。 人們甚至可能不知道他們在 Instagram 上使用的 AR 篩選準則是混合的現實體驗。  Microsoft Mixed Reality 是將所有的使用者體驗都帶到下一個層級，並結合真正絕佳的全像攝影型3D 模型，以及其周圍的真實世界。

![在 HoloLens 2 上手部指向和行動](images/02_MixedRealitySlashMixedReality.png)

混合現實是實體和數位世界的融合，可將自然且直覺的3D 人類、電腦和環境互動解除鎖定。 這項新的現實是以電腦視覺、圖形處理、顯示技術、輸入系統和雲端運算的進展為基礎。 「混合現實」1994一詞是由 Paul Milgram 和 Fumio Kishino，也就是「[混合現實視覺效果顯示的分類法](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)」所引進。 他們的白皮書探討了 *virtuality 鮮 continuum* 的概念，以及視覺效果顯示的分類法。 從那時起，混合實境的應用就不再侷限於顯示器，而也包括：

* 環境理解：空間對應和錨點。
* 人為瞭解：手追蹤、眼睛追蹤和語音輸入。
* 空間音效。
* 實體和虛擬空間中的位置和定位。
* 在混合現實空間中對3D 資產進行共同作業。

![混合實境頻譜影像](images/mixedrealityspectrum-worlds.png)<br>
*影像：混合實境是實體環境與數位世界混合的結果。*

<br>

---

## <a name="environmental-input-and-perception"></a>環境輸入和認知

過去數十年來，人類和電腦之間的關係一直都是由輸入方法的方法來發展。  出現新的專業領域，也就是所謂的人為電腦互動或 HCI。 人類輸入現在可以包括鍵盤、滑鼠、觸控、筆墨、語音和 Kinect 框架追蹤。

感應器和處理能力的進展是根據先進的輸入方法，為環境建立新的電腦理解。 這就是為什麼 Windows 中顯示環境資訊的 API 名稱稱為[認知 api](/uwp/api/Windows.Perception)。 環境輸入可以捕獲： 

* 人在實體世界中的主體位置 (前端 [追蹤](../design/coordinate-systems.md))  
* 物件、表面和界限 ([空間對應](../design/spatial-mapping.md) 和 [場景理解](../design/scene-understanding.md))  
* 環境光源和音效
* 物件辨識
* 實體位置

<br>

![顯示電腦、人類與環境之間互動的卞氏圖表](images/mixed-reality-venn-diagram-300px.png)<br> 
*影像：電腦、人類與環境之間的互動。*

<br>

三個基本元素的組合會設定建立真正混合現實體驗的階段：

* 由雲端提供技術支援的電腦處理
* Advanced 輸入方法
* 環境理解

當我們在現實世界中移動時，我們的移動會在數位現實中進行對應。 實體界限會影響數位世界中的混合現實體驗，例如在製造設備中的遊戲或以工作為基礎的指引。 有了環境輸入和認知，就能開始在實體和數位現實之間進行 blend。

<br>

---

## <a name="the-mixed-reality-spectrum"></a>混合實境頻譜

Mixed Reality 混合了實體和數位世界。  這兩個現實會標示一系列的極座標，稱為 *virtuality 鮮連續*。 我們將這一系列的現實視為 *混合的現實頻譜*。  在此範圍結束時，我們就擁有像人類一樣的實體事實。 在色譜的另一端，我們有對應的數位事實。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>擴增與虛擬實境

現今市場上大部分的行動電話幾乎沒有環境認知功能。 這些電話提供的體驗無法混合實體和數位現實。 

在實體世界中重迭圖形、視頻串流或全像影像的體驗，稱為增強的現實。 遮蔽您的視圖以提供完全沉浸式數位體驗的體驗，是虛擬的。 可以在增強型和虛擬實境之間轉換的體驗形成混合現實，您可以在其中：

* 將數位物件（例如，影像）放在實體世界中，如同實際存在一樣。
* 以頭像的形式，以個人和數位的形式出現在實體世界中，以非同步方式在不同的時間點與其他人共同作業。
* 在虛擬實境中，背景牆和傢俱等實體界限會以數位方式出現在使用者的體驗內，以避免遇到實體障礙。

<br>

![混合實境頻譜](images/mixedrealityspectrum.png)<br>
*影像：混合實境頻譜*

<br>

現今提供的大部分增強型事實和虛擬實境體驗，都代表較大的混合現實範圍的小型子集。 Windows 10 以整個頻譜為基礎，並可將數位方式呈現的人員、環境和事物與真實世界混合。

## <a name="devices-and-experiences"></a>裝置和體驗

有兩種主要的裝置類型可提供 Windows Mixed Reality 體驗：
1. 裝置能夠將數位內容放在真實世界中，如同真實存在一般，是 **Holographic 裝置** 的特性。
2. **沉浸式的 VR 裝置** 的特性是，藉由封鎖實體世界並將其取代為完全沉浸式數位體驗，讓裝置能夠建立目前狀態的能力。

<table>
<tr>
<th width="30%"> 特性</th><th width="35%"> 全像攝影裝置</th><th width="35%"> 沉浸式裝置</th>
</tr><tr>
<td><strong>範例裝置</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>顯示器</strong></td><td> 透明顯示器。 允許使用者在戴耳機時查看實體環境。</td><td> 不透明顯示器。 在穿戴頭戴式裝置時封鎖實體環境。</td>
</tr><tr>
<td><strong>移動</strong></td><td> 完整的六度自由移動，包括旋轉和轉譯。</td><td> 完整的六度自由移動，包括旋轉和轉譯。</td>
</tr>
</table> 

> [!NOTE]
> 無論裝置是透過 USB 纜線還是 Wi-fi 行動網卡至個別的電腦 (，) 或非網路共用都不會反映裝置是否為全像全像是全像裝置或沉浸式裝置。 改善行動性的功能通常會提供更好的體驗。 全像是行動網卡或非網路共用的全像裝置。

混合的現實體驗是技術進步的結果。 目前沒有任何可在整個頻譜中執行體驗的裝置。 Windows 10 同時為裝置製造商和開發人員提供通用的混合實境平台。 現今任何指定的裝置都可支援混合現實範圍內的特定範圍。 未來，預期會有更廣泛範圍的新裝置：「全像」的裝置會更有沉浸式，而且沉浸式裝置會更有全像。

<br>

![混合實境頻譜中的裝置類型](images/Final_WhatIsMixedReality07.png)<br>
*影像：裝置在混合實境頻譜上的位置*

作為應用程式或遊戲開發人員，您想要建立何種體驗？ 這些體驗通常會以頻譜上的特定點或部分作為目標。 您將需要考慮裝置的目標功能。 仰賴實體世界的體驗在 HoloLens 上的效果最佳。

* **向左 (接近實體實境)。** 使用者會在其實體現實中保持存在，而不是相信他們已離開該事實。
* **中間 (完全混合實境)。** 這些體驗混合了真實世界與數位世界。 例如，在電影 [Jumanji](https://en.wikipedia.org/wiki/Jumanji)中，故事的實際結構是以蛙鳴的環境混合。
* **向右 (接近數位實境)。** 使用者會遇到數位現實，並且不知道其周圍的實體事實。

## <a name="next-discovery-checkpoint"></a>下一個探索檢查點

您正在開始探索我們為您打造的 [探索旅程](get-started-with-mr.md) ，並探索混合現實的基本概念。 您可以從這裡繼續進行下一個基本主題： 

> [!div class="nextstepaction"]
> [什麼是全像投影？](hologram.md)
