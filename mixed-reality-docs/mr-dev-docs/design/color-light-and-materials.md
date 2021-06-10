---
title: 色彩、光線和材質
description: 設計混合現實的內容時，必須仔細考慮所有視覺資產的色彩、光源和材質。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、色彩、燈光、材質、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 2e1626e72d49107c2a83bf1123b306d3ee5c8640
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600357"
---
# <a name="color-light-and-materials"></a>色彩、光線和材質

![色彩、燈光和材質](images/RemoteRendering.jpg)

設計混合現實的內容時，必須仔細考慮所有虛擬資產的色彩、光源和材質。 美觀用途可能包括使用燈光和材質來設定沉浸式環境的色調，而功能性用途可包含使用驚人的色彩來警示使用者即將發生的動作。 每個決策都必須根據您體驗的目標裝置的商機和限制進行權衡。

以下是在沉浸式和全像攝影耳機上轉譯資產的特定指導方針。 其中有許多與其他技術領域緊密相關，而相關的主題清單則可在本文結尾的 [ [另請參閱](color-light-and-materials.md#see-also) ] 區段中找到。

## <a name="rendering-on-immersive-vs-holographic-devices"></a>在沉浸式和全像攝影裝置上轉譯

相較于全像攝影耳機中轉譯的內容，在沉浸式耳機中轉譯的內容會以視覺化方式呈現。 雖然沉浸式耳機通常會像在2D 螢幕上一樣地轉譯內容，但 HoloLens 這類的全息耳機會使用色彩順序，請參閱-透過 RGB 顯示來轉譯全像投影。

永遠花時間在全像攝影耳機中測試您的全像攝影體驗。 即使是專門針對全像攝影裝置所建立的內容外觀，也會隨著次要監視器、快照和 spectator view 中的不同而有所不同。 請記住，您可以使用裝置的體驗、測試全像投影的燈光，以及觀察所有邊的 (以及上方和下方，) 內容呈現的方式。 請務必使用裝置上的一系列亮度設定進行測試。 所有使用者不太可能會共用假設的預設值，以及一組不同的光源條件。

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>在全像裝置上呈現的基本概念

* 全像 **裝置具有** 加總顯示器–將燈光從真實世界的光線中增加，以建立全像白色，白色會顯示為明亮，而黑色會顯示為透明。

* **色彩影響會隨著使用者的環境而有所不同** -使用者的房間內有許多不同的光源。 建立具有適當對比層級的內容，以利清楚說明。

* **避免動態照明** –在全像全像全像全像全像的全像全像全像全像全像 使用 advanced、動態光源可能會超過行動裝置的功能。 當需要動態光源時，建議使用 [混合現實工具組標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)。 

## <a name="designing-with-color"></a>使用色彩設計

由於加法顯示器的本質，某些色彩在全像全像顯示器上可能會不同。 某些色彩會在照明環境中顯示，有些則會顯示為較少的具影響力。 很酷的色彩通常會 recede 到背景，而暖色彩則會跳到前景。 當您在體驗中探索色彩時，請考慮下列因素：

* 轉譯 **淺色色彩**-白色的外觀很亮，應謹慎使用。 在大部分的情況下，請考慮有關 R 235 G 235 B 235 的白色值。 很亮的區域可能會導致使用者不適感。 針對 UI 視窗的 backplate，建議使用深色色彩。

* 轉譯 **深色色彩**-因為加法顯示器的本質，深色色彩會顯示為透明。 實心的黑色物件看起來與真實世界沒有不同。 請參閱下列 Alpha 通道。 若要提供「黑色」的外觀，請嘗試相當深的灰色 RGB 值（例如16、16、16）。

* **色彩一致性** ：通常會將全像影像呈現為明亮，使其維持色彩一致性，無論背景為何。 大型區域可能會變成 blotchy。 避免大型區域的明亮、單色。

* 從 **色彩的「** 寬範圍」來獲益，在概念上類似 Adobe RGB。 因此，某些色彩可能會在裝置中顯示不同的品質和標記法。

* **Gamma** -轉譯影像的亮度和對比在沉浸式和全像全像裝置之間會有所不同。 這些裝置的差異通常會讓色彩和陰影的暗區出現、更多或更不亮。

* **色彩分隔** -也稱為 "color 並劃分" 或 "color fringing"，最常見的色彩分隔是在使用者以眼睛追蹤物件時，將游標) 移動 (包括游標。

## <a name="technical-considerations"></a>技術考量

* **別名** -明智失真、不規則或「樓梯步驟」，其中全像是全像真實世界的影像。 使用具有高詳細資料的材質可以加劇此效果。 紋理應對應並啟用篩選。 請考慮淡化全像影像的邊緣，或新增紋理來建立物件周圍的黑色邊緣框線。 盡可能避免精簡型幾何。

* **Alpha** 色板-您必須針對未呈現全像影像的任何部分，清除您的 Alpha 色板以完全透明。 從裝置或使用 Spectator View 取得影像/影片時，讓 Alpha 未定義的會導致視覺構件。

* **紋理的軟化** -因為光線是在全像全像投影顯示器中的加法，所以最好避免較大的區域，因為通常不會產生預期的視覺效果。

## <a name="design-guidelines-for-holographic-display"></a>全像顯示器的設計方針

![色彩和手遮蔽](images/color_handocclusion.jpg)

在設計全像顯示器的內容時，有數個您需要考慮的元素，以達到最佳體驗。 請造訪 [設計內容以進行](designing-content-for-holographic-display.md) 全像展示，以取得指導方針和建議。

## <a name="storytelling-with-light-and-color"></a>具有淺色和色彩的故事行銷

Light 和 color 可協助讓您的全息體在使用者的環境中以更自然的方式出現，並提供使用者的指引和協助。 針對全像攝影經驗，請在探索光源和色彩時考慮這些因素：

:::row:::
    :::column:::
* **Vignetting** -將材質的「vignette」效果變暗有助於將使用者的注意力集中在視野的中心。 此效果會從使用者的注視向量中，以某些半徑來加深全息圖的材質。 當使用者從傾斜或 glancing 角度來觀看全息表時，這也會有效。

* **強調** -透過對比色彩、亮度和光源來吸引物件或互動點。 如需故事行銷中的燈光方法詳細資訊，請參閱 [圖元 Cinematography-電腦圖形的照明方法](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)。<br>
        <br>
        *影像：使用色彩來顯示故事行銷元素的強調，此處顯示于 [片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)的場景中。*
    :::column-end:::
        :::column:::
        ![使用色彩來顯示故事行銷元素的強調，此處顯示于片段中的場景。](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>材質

:::row:::
    :::column:::
材質是建立逼真全像影像的重要元素。 藉由提供適當的視覺特性，您可以建立吸引人的全像攝影物件，以便與實體環境完美結合。 對於為各種類型的使用者輸入互動提供視覺化意見反應，材質也很重要。  

[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) 提供具有各種視覺效果選項的 MRTK 標準著色器，可用於視覺效果的意見反應。 例如，您可以使用「近亮」屬性，在使用者的手指接近物件的介面時，提供光源效果。 深入瞭解 [MRTK 標準著色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)
    :::column-end:::
        :::column:::
    *影片迴圈：根據鄰近範圍* 
     ![ 方塊的視覺效果意見反應範例關於手近距離的視覺回饋](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>另請參閱
* [設計全像攝影顯示器的內容](designing-content-for-holographic-display.md)
* [色彩分隔](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [全像投影](../discover/hologram.md)
* [Microsoft 設計語言-色彩](https://www.microsoft.com/design/color)
* [通用 Windows 平臺-色彩](/windows/uwp/style/color)