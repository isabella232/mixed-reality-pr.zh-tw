---
title: 案例研究 - 在實境中的的透視技術
description: 此案例研究說明 HoloLens 上的「魔術視窗」效果，讓使用者可以在地板後方、在地面下，以及進入虛擬機器會。
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、魔術視窗、視差
ms.openlocfilehash: 018e45a79d88cbc8e28204f023106fbe5dae39bc
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010108"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>案例研究 - 在實境中的的透視技術

當人們思考混合的現實，以及他們可以如何運用 Microsoft HoloLens 時，通常會發生像是「我可以將哪些物件新增到我的房間？」之類的問題。 或「我可以在我的空間上方分層？」 我想要強調您可以考慮的另一個領域，基本上是一種魔術訣竅，也就是使用相同的技術來查看或透過真實的實體物件。

## <a name="the-tech"></a>技術

如果您已在 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 中曾外星人， **[而在](case-study-creating-an-immersive-experience-in-fragments.md)** 中，已將牆安全解除鎖定，或幸運于在 **[2015 的 E3 5 體驗](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 中查看 UNSC 無限大 hangar，則您已瞭解我所說的內容。 根據您的想像，此視覺效果可以用來將暫時性的洞放在您的幹，或隱藏在鬆散 floorboard 下的世界。

![RoboRaid 會在您的牆後方新增三維管道和其他結構，只會透過太空入侵者中斷時所建立的漏洞來顯示。](../develop/unity/images/roboraid-640px.png)

RoboRaid 會在您的牆後方新增三維管道和其他結構，只會透過太空入侵者中斷時所建立的漏洞來顯示。

在 HoloLens 上使用其中一個獨特的全息圖，應用程式可以提供您牆背後的內容，或透過您的樓層，以實際在實際視窗中呈現本身的相同方式。 將您自己移至左側，您可以在右側看到任何內容。 深入瞭解，您可以看到更多東西。 主要的差異在於，您的樓層 stubbornly 不會讓您通過神奇的全像內容。  (我要將工作新增至待處理專案。 ) 

## <a name="behind-the-scenes"></a>在幕後

這項技巧是兩種效果的組合。 首先，使用「空間錨點」將全息內容釘選到世界。 使用錨點將內容設為「世界鎖定」，表示您所要查看的內容不會以視覺化方式與附近的實體物件漂移，即使您移動或基礎空間對應系統會更新其房間的3D 模型。

其次，在視覺上，這種全像生活的內容會以視覺方式限制為非常特定的空間，因此您只會看到您實際的洞。 需要遮蔽，才能透過邏輯洞、視窗或閘口（其銷售訣竅）來查看。 如果未封鎖大部分的視圖，秘密 Jurassic 維度的空間破解可能就像是不良放置的恐龍。

![這並不是實際的螢幕擷取畫面，而是從 MR 基礎101的秘密 underworld 到 HoloLens 的說明。 黑色主機殼未顯示，但您可以透過虛擬洞看到內容。  (當您查看實際的裝置時，可能會因為您的眼睛焦點與甚至沒有的距離，而消失。 ) ](images/origamiholecomposited-640px.png)

這並不是實際的螢幕擷取畫面，而是從 [MR 基礎 101](../develop/unity/tutorials/holograms-101.md) underworld 秘密的說明，看看 HoloLens。 黑色主機殼未顯示，但您可以透過虛擬洞看到內容。  (當您查看實際的裝置時，可能會因為您的眼睛焦點與甚至沒有的距離，而消失。 ) 

### <a name="world-locking-holographic-content"></a>全球鎖定的全像內容

在 Unity 中，造成全像全球的內容保持全球鎖定，就像新增 WorldAnchor 元件一樣簡單：

```
myObject.AddComponent<WorldAnchor>();
```

WorldAnchor 元件會不斷地調整其 GameObject (的位置和旋轉，因此階層中該物件下的任何其他地方都會) ，使其相對於附近的實體物件保持穩定。 撰寫您的內容時，請以您物件的根軸在這個虛擬洞的中央來建立它。  (如果物件的資料透視是在牆中的深度，則在位置和旋轉方面稍微調整會更明顯，且洞看起來可能不穩定。 ) 

### <a name="occluding-everything-but-the-virtual-hole"></a>遮蔽虛擬洞以外的所有專案

有多種方式可以選擇性地將視圖封鎖在您的牆中隱藏的區域。 最簡單的方法是利用 HoloLens 使用加法顯示的事實，這表示完全黑色的物件會顯示為不可見。 您可以在 Unity 中執行這項操作，而不需要執行任何特殊的著色器或材質訣竅，只要建立黑色材質，然後將它指派給內容中的方塊。 如果您不喜歡進行3D 模型化，只需使用一些預設的四個物件，並稍微重迭它們。 這種方法有幾個缺點，不過它是讓工作變得最快的方式，而取得低精確度的概念證明是很棒的，即使您懷疑稍後可能會想要重構它。

上述「黑箱」方法的一個主要缺點是，它不會有很好的相片。 雖然您的效果可能會透過 HoloLens 的顯示結果看起來很完美，但您所採取的任何螢幕擷取畫面都會顯示大型的黑色物件，而不是您的牆或樓層。 原因是實體硬體和螢幕擷取畫面的複合全息圖和事實有不同。 讓我們繞道一點假的數學 .。。

*假的數學警示！這些數位和公式的目的是要說明某個點，而不是任何種類的精確度量！*

您透過 HoloLens 看到的內容：

```
( Reality * darkening_amount ) + Holograms
```

您在螢幕擷取畫面和影片中看到的內容：

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

英文：您透過 HoloLens 看到的內容是簡單的事實 (的組合，例如透過太陽眼鏡) ，以及應用程式想要顯示的任何影像。 但是，當您拍攝螢幕擷取畫面時，相機的影像會根據每個圖元的透明度值，與應用程式的全像混合。

解決此問題的方法之一是將「黑色方塊」材質變更為只寫入深度緩衝區，並使用所有其他不透明的材質進行排序。 如需相關範例，請參閱[GitHub 上 MixedRealityToolkit 中的 WindowOcclusion。](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader) 相關的程式碼會複製到此處：

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

 (請注意，「位移50，100」這一行是為了處理不相關的問題，因此，將它留出可能是合理的。 ) 

執行這類不可見的遮蔽資料，可讓您的應用程式在顯示和混合式事實螢幕擷取畫面中繪製出看起來正確的方塊。 針對額外的一點，您可以嘗試更進一步改善該方塊的效能，方法是執行聰明的事情來繪製更少的不可見圖元，但這可能真的會進入除去，而且通常不需要這麼做。

![以下是 Unity 基礎101中的秘密 underworld，因為 Unity 會將它繪製，除了遮蔽方塊的外部部分。 請注意，underworld 的 pivot 是在方塊的中央，可協助盡可能保持最穩定的洞相對於實際的樓層。](images/underworld-occluded-640px.png)

以下是 Unity [基礎 101](../develop/unity/tutorials/holograms-101.md) 中的秘密 underworld，因為 Unity 會將它繪製，除了遮蔽方塊的外部部分。 請注意，underworld 的 pivot 是在方塊的中央，可協助盡可能保持最穩定的洞相對於實際的樓層。

## <a name="do-it-yourself"></a>親自完成

有 HoloLens，想要親自試試看自己的效果嗎？  (不) 需要撰寫程式碼，最簡單的方式就是安裝免費的3D 檢視器應用程式，然後載入 [我在 GitHub 上提供的 fbx](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) 檔案，以在您的房間內查看花卉模型。 在 HoloLens 上載入它，您就可以查看工作中的假像。 當您在模型前面時，您只會看到輕微的部分，其他所有專案則不會顯示。 從其他任何一端查看模型，它會完全消失。 使用3D 檢視器的移動、旋轉和縮放控制項，將虛擬洞定位至您可以想像用來產生一些構想的任何垂直介面！

![在 Unity 編輯器中查看此模型，會在 flowerpot 周圍顯示大型的黑色方塊。 在 HoloLens 上，此方塊會消失，讓魔術視窗的效果更上一種。](images/magicwindowflowerpotineditor.png)

在 Unity 編輯器中查看此模型，會在 flowerpot 周圍顯示大型的黑色方塊。 在 HoloLens 上，此方塊會消失，讓魔術視窗的效果更上一種。

如果您想要建立使用這項技術的應用程式，請查看[混合現實教學](../develop/unity/tutorials.md)課程中的[MR 基本概念101教學](../develop/unity/tutorials/holograms-101.md)課程。 第7章以您的樓層進行爆炸，顯示隱藏的 underworld (，如上面所示) 。 誰說過教學課程必須很乏味？

以下是一些您可以在這裡採取這項構想的概念：
* 想辦法讓虛擬洞內的內容成為互動。 讓您的使用者在其牆之外有一些影響，可以真正改善這項技巧可以提供的意義。
* 想辦法將物件查看回已知區域。 例如，您要如何在咖啡表中放入全像地面？

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>資深軟體工程師 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>請參閱
* [MR Basics 101：使用裝置完成專案](../develop/unity/tutorials/holograms-101.md)
* [座標系統](../design/coordinate-systems.md)
* [空間錨點](../design/spatial-anchors.md)
* [空間對應](../design/spatial-mapping.md)
