---
title: 元素週期表
description: 專案的定期資料表是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式，您可以在其中學習如何使用物件集合，在3D 空間中設定物件陣列，以及各種表面類型。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、範例應用程式、控制項
ms.openlocfilehash: 2f7120aaf92a6e3d7b6ace301aae7392b67fa00b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91682504"
---
# <a name="periodic-table-of-the-elements"></a>元素週期表

>[!NOTE]
>本文討論我們在 [混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例，這是我們分享學習的地方，並提供混合現實應用程式開發的建議。 我們的設計相關文章和程式碼將隨著我們進行新探索而演進。

專案的[定期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。 透過此專案，您可以瞭解如何使用 **[物件集合](../../design/object-collection.md)** ，在3d 空間中配置具有各種介面類別型的物件陣列。 同時瞭解如何建立互動物件，以回應 HoloLens 的標準輸入。 您可以使用此專案的元件來建立您自己的混合現實應用程式體驗。

![Elements 應用程式的期間資料表](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>關於應用程式

專案的定期資料表會以3D 空間將化學元素和每個屬性視覺化。 它結合了 HoloLens 的基本互動，例如注視和點擊。 使用者可以使用動畫3D 模型來瞭解這些元素。 他們可以透過視覺化方式瞭解元素的 electron shell 及其系統核心（由 protons 和 neutrons 組成）。

## <a name="background"></a>背景

在我第一次體驗 HoloLens 之後，定期資料表應用程式就是我知道我想要在混合現實中進行實驗的概念。 由於每個專案都有許多以文字顯示的資料點，因此我認為在3D 空間中探索印刷樣式組合是很重要的主題。 能夠以視覺化方式呈現專案的 electron 模型是這個專案的另一個有趣的部分。

## <a name="design"></a>設計

針對定期資料表的預設視圖，我想要有三維方塊，其中包含每個元素的 electron 模型。 每個方塊的介面都是半透明的，讓使用者可以大致瞭解元素的音量。 使用者可以利用注視和空中來開啟每個元素的詳細觀點。 為了讓資料表視圖和詳細資料檢視之間的轉換變得順暢且自然，我將它與在實際生活中開啟的實際互動類似。

![設計草圖](images/640px-sketch20170406.jpg)<br>
*設計草圖*

在詳細資料檢視中，我想要使用3D 空間中的美觀轉譯文字，將每個元素的資訊視覺化。 動畫的 3D electron 模型會顯示在中間區域，而且可以從不同的角度來查看。

![互動](images/640px-periodictable-interaction.jpg)

![原型](images/640px-periodictable-prototypes.jpg)<br>
*互動原型*

使用者可以透過使用表格底部的按鈕來變更介面型別，它們可以在平面、圓柱圖、球體圖和散佈圖之間切換。

## <a name="common-controls-and-patterns-used-in-this-app"></a>此應用程式中使用的通用控制項和模式

### <a name="interactable-object-button"></a>互動物件 (按鈕) 

[互動物件](../../design/interactable-object.md) 是可回應基本 HoloLens 輸入的物件。 它是以預製專案/腳本的形式提供，您可以輕鬆地將它套用到任何物件。 例如，您可以在場景中製作咖啡杯互動，並回應像是注視、碰點、導覽和操作手勢等輸入。 [深入了解](../../design/interactable-object.md)

![nteractable 物件](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>物件集合

[物件集合](../../design/object-collection.md) 是一個物件，可協助您配置各種不同圖形中的多個物件。 它支援平面、圓柱、球體和散佈圖。 您可以設定其他屬性，例如 radius、資料列數目和間距。 [深入了解](../../design/object-collection.md)

![物件集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

根據預設，在應用程式啟動時，會在使用者撥雲見日的位置放置全像影像。 這有時候會導致不想要的結果，例如，將影像放在牆後方或資料表的中間。 Fitbox 可讓使用者使用注視來判斷將放置全息圖的位置。 它會使用簡單的 PNG 影像材質進行自訂，您可以使用自己的影像或3D 物件輕鬆地加以自訂。

![Fitbox](../../design/images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>技術詳細資訊

您可以在 [混合式現實設計實驗室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上，找到專案應用程式的定期表格的腳本和 prefabs。

## <a name="application-examples"></a>應用程式範例

以下是您可以利用此專案中的元件來建立的一些概念。

### <a name="stock-data-visualization-app"></a>股票資料視覺效果應用程式

使用與專案範例的定期資料表相同的控制項和互動模型，您可以建立可哥視化股票市場資料的應用程式。 這個範例會使用物件集合控制項來配置球形圖形中的股票資料。 您可以想像出詳細資料，其中每個股票的其他相關資訊可能會以有趣的方式顯示。

![應用程式範例：財務 (1/3) ](images/640px-periodictable-applicationexamples-finance1.jpg)

![應用程式範例：三) 的財務 (2](images/640px-periodictable-applicationexamples-finance2.jpg)

![應用程式範例：財務 (3) ](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*如何在財務應用程式中使用元素範例應用程式的定期資料表中所使用的物件集合範例*

### <a name="sports-app"></a>運動應用程式

這是使用專案範例應用程式之定期資料表中的物件集合和其他元件來視覺化運動資料的範例。

![應用程式範例：運動 (1/3) ](images/640px-periodictable-applicationexamples-sports0.jpg)

![應用程式範例：運動 (2/3) ](images/640px-periodictable-applicationexamples-sports1.jpg)

![應用程式範例：運動 (3 之 3) ](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*如何在運動應用程式中使用 appcould 元素範例的定期資料表中所使用的物件集合範例*

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon 公園</b><br>UX 設計工具 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱

* [可互動的物件](../../design/interactable-object.md)
* [物件集合](../../design/object-collection.md)
