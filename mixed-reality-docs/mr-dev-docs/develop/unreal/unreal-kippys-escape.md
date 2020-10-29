---
title: 製作 Kippy 的 Escape
description: 當我們探索在 Unreal 引擎中進行 HoloLens 2 的 Kippy Escape 時，請遵循我們的指示。
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、部署至裝置、電腦、檔
appliesto:
- HoloLens 2
ms.openlocfilehash: 5c029e91bb33192b02dd32aca224a23fc4b5289d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679685"
---
# <a name="the-making-of-kippys-escape"></a>製作 Kippy 的 Escape

Kippy 機器人喚醒以找出自己在島上的孤立狀態。 您可以自行專注于問題解決 hat，以協助 it 尋找 rocket 出貨的途徑！ 在您的 HoloLens 2 上，從 Microsoft Store [下載應用程式](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) ，或從 GitHub 複製存放 [庫](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) ，並取得 Kippy 家用安全！  

> [!IMPORTANT]
> 如果您是從 GitHub 存放庫建立 Kippy 的 Escape，請確定您使用的是 **Unreal Engine 4.25 或更新版本** 。

## <a name="overview"></a>概觀

Kippy 的 Escape 是一個開放原始碼 [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware) 範例應用程式，使用 Unreal Engine 4 和 [混合現實 UX 工具進行 Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)。 在這篇文章中，我們將逐步引導您完成將 Kippy 的轉換至生命的程式，從第一項原則和視覺化設計，到實施和優化體驗。 您可以在 [Unreal 開發總覽](unreal-development-overview.md)中找到使用 MRTK UX 工具開發混合現實應用程式的詳細資訊。

## <a name="first-principles"></a>第一個原則 

在設定以建立 Kippy 的轉型時，我們的目標是要建立一項體驗來強調 [Unreal 引擎的 HoloLens 2 支援](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)、HoloLens 2 的功能，以及混合現實工具組。 我們想要讓開發人員能夠想像他們可以使用 Unreal 和 HoloLens 2 來建立的功能。  

我們針對此體驗有三個指導準則：它需要有趣、互動，而且進入的障礙很低。 我們希望體驗的視覺效果足夠，即使是首次的混合現實使用者也不需要教學課程。  

## <a name="designing-the-game"></a>設計遊戲 

HoloLens 2 可以存取設計功能，目前在遊戲中有其他地方。 您可以使用您的手或以眼睛追蹤作為目標，直接推送或操作物件。 這些主要功能的背後，是我們在 Kippy 的轉換程式中所建立的一些有趣的部分。  

使用獨特的 HoloLens 2 功能做為遊戲設計的指導方針，我們已將一些小型環境案例的範圍限定在其中。 孤島有很大的意義，因為可以針對不同的播放程式高度進行調整，並提供一些有趣的橋樑想法。 從這裡開始，我們進入了古文明的主題與科幻-fi 技術的比較，也就是有人在毀損上建立的機械，利用了每個島所提供的奇怪能源。 每個孤島都有各自的外觀和操作，這是協助您建立視覺興趣的詳細資料。 模型化和紋理之間的平衡很重要，因為這是為了讓繪製呼叫的效能降低，以呈現效能，因此設計風格的外觀。 

![早期遊戲設計 ](images/kippys-escape/kippys-escape-img-01.png)
 *會針對體驗的外觀進行一些早期的草圖*

![](images/kippys-escape/kippys-escape-img-02.png)
*第二島* 的第二個島轉譯轉譯

為了維持在短期的生產環境中，我們同意浮動字元可能會在沒有嚴格動畫迴圈的情況下捕捉意圖和表情。 所以 Kippy 是出生的！ 它會透過其眼睛 emotes 幾個不同的運算式，並透過 minimalistic 關切這個領域音效，協助引導玩家體驗整個體驗。 

![Kippy 透過其眼睛顯示不同的運算式](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy 透過其眼睛顯示不同的運算式*

![如果使用者花太多時間來解決謎題，Kippy 會為使用者提供提示](images/kippys-escape/kippys-escape-img-04.gif)

*如果使用者花太多時間來解決謎題，Kippy 會為使用者提供提示*

除了字元和環境設計之外，我們也一致了讓遊戲感到有趣的工作。 眼睛追蹤可讓我們引發材質和音效屬性，這些屬性強調遊戲的重要部分。 空間音訊可協助您在玩家的環境中，讓這些層級在家裡的外觀。 能夠抓取物件、推播按鈕和操作滑杆推動創新的玩家參與，所以請務必確定這些連接點都覺得自然。 

![橋接器纜線的尾端會在使用者的手上進行時發光](images/kippys-escape/kippys-escape-img-05.gif)

*橋接器纜線的尾端會在使用者的手上進行時發光*

## <a name="building-the-game-mechanics"></a>打造遊戲機制 

Kippy 的 Escape 高度依賴混合現實 UX 工具元件，讓遊戲成為互動的互動動作專案、界限控制項、操作工具、滑杆和按鈕。   

「 [手上互動](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) 」動作專案可讓您直接操作或同時管理全像。 在 Kippy 的 Escape 開始時，使用者有機會設定遊戲的位置。 從使用者的掌上字形狀延伸，可讓您輕鬆地操作距離較遠的大型全息圖，如下圖所示。  

![手邊互動執行者 gif](images/kippys-escape/kippys-escape-img-06.gif)

您可以使用 UX 工具的 [界限控制項](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) 元件來拖曳和旋轉預留位置場景本身。  

在第二個島上，使用者必須挑選 gem，並將它們放在其相符的位置。 Gem 已附加操作工具， [可讓使用者](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) 挑選它們並將其放在下方。 

![操作工具範例 gif](images/kippys-escape/kippys-escape-img-07.gif)

[Pressable 按鈕](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html)是讓炸彈在第三島上使用的關鍵。  

![Pressable 按鈕範例 gif](images/kippys-escape/kippys-escape-img-08.gif)

[滑杆](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html)元件會出現在第四個島上，觸發最後一個要引發的橋接器。  

![滑杆元件範例 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>HoloLens 2 的優化 

在行動裝置上建立的任何體驗中，請注意效能很重要。 Unreal 4.25 包含支援行動多重視圖的重大更新，可大幅減少轉譯的負荷並提高畫面播放速率。 建議您在優化時，查看其他 [建議的效能設定](performance-recommendations-for-unreal.md) ，以使用 Unreal 進行 HoloLens 2 開發。  

物理物件的效能仍維持昂貴，因此使用了一些聰明的因應措施。 比方說，第三個「橋接器」需要吹出一些阻礙 stairway 的碎屑。 因為炸彈引爆會觸發交換、切換靜態石子以進行爆炸式物件效果，而不會強制將石子視為物理物件。 

![HoloLens 2 gif 的優化範例](images/kippys-escape/kippys-escape-img-10.gif) 

我們也會將我們的繪製呼叫從400減少到 ~ 260，方法如下： 
* 降低網格複雜度
* 組合網格
* 移除一些初始動態光源元素

雖然我們可能會有更多工作，但我們認為這在效能與視覺品質之間是一個良好的平衡。  

## <a name="try-it-out"></a>試試看！ 

啟動您的 HoloLens 2 並從 Microsoft Store [下載](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) 應用程式，或從 GitHub 複製存放 [庫](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) ，自行建立應用程式！  

## <a name="about-the-team"></a>關於小組

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>插座</b><br><i>領導遊戲設計工具</i><br>目前的「插座」適用于 Microsoft 的混合現實體驗，包括 HoloLens 2 專案和 AltspaceVR，而且之前是 HoloLens 平臺小組的設計工具。</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>夏天 Wu</b><br><i>產生器 (producer)</i><br>夏天在混合現實開發人員平臺上運作，並且與小組 Unreal 引擎的相關工作進行領導。</td>
</tr>
</table>

特別感謝我們的朋友 [Framestore](https://www.framestore.com/) ，協助我們將 Kippy 的轉換至下一個層級。 從字元開發到資產設計，到遊戲程式設計，在此專案上進行共同作業的 pivotal。  