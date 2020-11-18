---
title: 印刷樣式
description: 文字是在您的應用程式體驗中傳遞資訊的重要元素。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、樣式、字型、印刷樣式、ui、ux、文字、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、HoloLens
ms.openlocfilehash: c0e3b23c52925b6fe64dccc7087613e8cd49e851
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703244"
---
# <a name="typography"></a>印刷樣式

![HoloLens 中的印刷樣式範例](images/typography-cover.png)<br>


文字是在您的應用程式體驗中傳遞資訊的重要元素。 就像2D 螢幕上的印刷樣式一樣，目標是要清楚易懂。 有了混合實境的三維外觀比例，就有機會以更佳的方式來影響文字和整體使用者體驗。

當我們談到3D 中的型別時，我們傾向于將體積型的3D 文字視為已延伸。 除了部分商標設計和一些其他有限的應用程式以外，已拉伸的文字通常會降低文字的可讀性。 雖然我們正在設計3D 的體驗，但我們使用2D 作為型別，因為它比較清楚且更容易閱讀。

在 HoloLens 中，類型是使用以加法色彩系統為基礎的輕量來建立。 就像其他的全像投影一樣，可以將型別放在實際的環境中，讓它可以從任何角度鎖定並觀察到。 型別和環境之間的 [視差](https://en.wikipedia.org/wiki/Parallax) 效果，也增加了體驗的深度。

## <a name="typography-in-mixed-reality"></a>混合現實中的印刷樣式

混合現實中的印刷樣式規則與其他任何地方都沒有不同。 實體世界和虛擬世界中的文字都必須能夠清楚且容易閱讀。 文字可以在牆上或在實體物件上重迭。 它可以與數位使用者介面一起浮動。 不論內容為何，我們都會套用相同的印刷樣式規則來進行讀取和辨識。

### <a name="create-clear-hierarchy"></a>建立明確階層

使用不同的類型大小和加權來建立對比和階層。 在整個應用程式體驗中定義型別和之後，將可提供一致的資訊階層，提供絕佳的使用者體驗。

![輸入逐漸增加的範例](images/typography-ramp-1000px.jpg)<br>
*定義您的型別，並在整個應用程式體驗中追蹤*

### <a name="limit-your-fonts"></a>限制字型

避免在單一內容中使用兩個以上的不同字型系列。 這會中斷您的體驗的顏色與一致性，並使其更難以取用資訊。 在 HoloLens 中，由於資訊是在實體環境的最上層進行重迭，因此使用太多字型樣式將會降低體驗。 Segoe UI 是所有 Microsoft 數位設計的字型。 它會在 Windows Mixed Reality shell 中一致地使用。 您可以從 [Windows 設計工具組頁面](https://docs.microsoft.com/windows/uwp/design-downloads/)下載 Segoe UI 字型檔案。

[Segoe UI 字樣的詳細資訊](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>避免細字型粗細

請避免針對頁首建議42pt 下的類型大小使用淺色或 semilight 做字型粗細，因為精簡型垂直筆觸會震動並降低可讀性。 具有足夠筆觸粗細的新式字型可正常運作。 例如，使用一般或粗體字的 HoloLens 中的 Helvetica 和 Arial 非常清晰。

### <a name="color"></a>Color

在 HoloLens 中，因為全像是以加總的燈光系統來建造全像系統，所以白色文字很清晰。 您可以在 [開始] 功能表和應用程式行中找到白色文字的範例。 即使白色文字在 HoloLens 沒有背面的情況下正常運作，但複雜的實體背景也可能使類型難以閱讀。 若要改善使用者的焦點，並將實體背景的干擾降到最低，建議您在深色或彩色的背景板上使用白色文字。

<br>


![建議您在深色或彩色背板上使用白色文字。 ](images/typography-whiteonblack2-1000px.jpg)
*深色或彩色背板上的白色文字範例。*
<br>

若要使用深色文字，您應該使用較佳的背板讓它變成可讀取。 在 [加法色彩系統] 中，黑色會顯示為透明。 這表示您將無法在沒有彩色背板的情況下看見黑色文字。

:::row:::
    :::column:::
        ![黑色文字範例](images/typography-whiteonblack.png)<br>
        *白色文字上黑色和黑色的白色範例*<br>
    :::column-end:::
    :::column:::
        ![黑色文字範例](images/640px-typography-blackonwhite.jpg)<br>
        *系統應用程式中的黑色文字範例-儲存和設定*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>建議的字型大小

如您所見，我們在電腦或平板電腦裝置上使用的類型大小， (通常介於12–32pt 填補) 在2個計量之間的距離相當小。 這取決於每個字型的特性，但在一般情況下，建議的最小觀賞角度和字型高度都是以我們的使用者研究研究為基礎，0.35 °0.4 °/12.21-13.97mm。 它大約有35個40pt，其中包含在 Unity 頁面中的 [文字](../develop/unity/text-in-unity.md) 所引進的縮放因數。 

針對 0.45 m 的近乎互動 (45cm) ，最小的可辨認字型的觀賞角度和高度為0.4 °-0.5 °/3.14 – 3.9 mm。 這與在 [Unity 的文字中](../develop/unity/text-in-unity.md)引進的縮放因數大約是 9 12pt。

![近距離與遠距離互動範圍的互動範圍 ](images/typography-distance-1000px.jpg)
 *內容*

### <a name="the-minimum-legible-font-size"></a>最小清晰度的字型大小
| 距離 | 視角 | 文字高度 | 字型大小 * * |
|---------|---------|---------|---------|
| 45cm (直接操作距離)  | 0.4 °-0.5 ° | 3.14 –3.9 分鐘 | 8.9 – 11.13 pt |
| 2m | 0.35 °-0.4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>方便閱讀的字型大小
| 距離 | 視角 | 文字高度 | 字型大小 * * |
|---------|---------|---------|---------|
| 45cm (直接操作距離)  | 0.65 °-0.8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2m | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |


Segoe UI (Windows) 的預設字型在大部分情況下都能順利運作。 不過，請避免使用較小的淺色或半淺色字型系列，因為精簡型垂直筆觸會震動，而且會降低可讀性。 具有足夠筆觸粗細的新式字型可正常運作。 例如，Helvetica 和 Arial 外觀美觀，而且在 HoloLens 中會有一般或粗體權數的可讀性。

**如需 Unity 中文字大小計算的詳細資訊，請參閱 [unity 中的文字](../develop/unity/text-in-unity.md)**

![視圖角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *觀賞距離、角度和文字高度*

<br>

---

## <a name="resources"></a>資源

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Segoe 字型](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
     (Zip 檔案) <br>
    ### <a name="hololens-fontbr"></a>[HoloLens 字型](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
     (Zip 檔案) <br>
    <br>
    *影像： HoloLens 字型提供 Windows Mixed Reality 中使用的符號圖像。*
    :::column-end:::
        :::column:::
        ![HoloLens 字型可提供您在 Windows Mixed Reality 中使用的符號字元](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="see-also"></a>另請參閱
* [Unity 中的文字](../develop/unity/text-in-unity.md)
* [色彩、光線和材質](../color,-light-and-materials.md)
