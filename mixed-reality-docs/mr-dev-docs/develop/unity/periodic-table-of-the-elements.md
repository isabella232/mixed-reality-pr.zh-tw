---
title: 元素週期表
description: 瞭解如何使用具有專案範例應用程式之定期資料表的物件集合，來配置3D 空間中的物件陣列。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、範例應用程式、控制項、MRTK、混合現實工具組、Unity、範例應用程式、範例應用程式、開放原始碼、Microsoft Store、HoloLens、混合現實耳機、Windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 2856d9052f9e1d07b2f796cafeb96fb0cdef63e8
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757302"
---
# <a name="periodic-table-of-the-elements"></a>元素週期表
![Elements 應用程式的期間資料表](../images/MRDL_PeriodicTable_HL1.jpg)

>[!NOTE]
>本文討論我們在 [混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例，這是我們分享學習的地方，並提供混合現實應用程式開發的建議。 我們的設計相關文章和程式碼將隨著我們進行新探索而演進。

>[!NOTE]
>這個範例應用程式是針對 HoloLens 第1代所設計。 請參閱[元素2.0 的定期表格](periodic-table-of-the-elements-2.md)，以取得 HoloLens 2 版本。

專案的[定期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。 瞭解如何使用 **[物件集合](../../design/object-collection.md)**，在3d 空間中配置具有各種介面類別型的物件陣列。 同時瞭解如何建立互動物件，以回應 HoloLens 的標準輸入。 您可以使用此專案的元件來建立您自己的混合現實應用程式體驗。


## <a name="demo-video"></a>示範影片 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

使用混合實境擷取 HoloLens 2 記錄

## <a name="about-the-app"></a>關於應用程式

專案的定期資料表會以3D 空間將化學元素和每個屬性視覺化。 它結合了 HoloLens 的基本互動，例如注視和點擊。 使用者可以使用動畫3D 模型來瞭解這些元素。 他們可以透過視覺化方式瞭解元素的 electron shell 及其系統核心（由 protons 和 neutrons 組成）。

## <a name="background"></a>背景

在我第一次經驗 HoloLens 之後，我知道我想要在混合現實中試驗定期資料表應用程式。 由於每個專案都有許多以文字顯示的資料點，因此我認為在3D 空間中探索印刷樣式組合是很重要的主題。 讓使用者有機會將元素的 electron 模型視覺化是此專案的另一個有趣部分。

## <a name="design"></a>設計

針對定期資料表的預設視圖，我想要有三維方塊，其中包含每個元素的 electron 模型。 每個方塊的介面都是半透明的，讓使用者可以大致瞭解元素的音量。 使用者可以利用注視和空中來開啟每個元素的詳細觀點。 為了讓資料表視圖和詳細資料檢視之間的轉換變得順暢且自然，我將它與在實際生活中開啟的實際互動類似。

![設計草圖](images/640px-sketch20170406.jpg)<br>
*設計草圖*

在詳細資料檢視中，我想要使用3D 空間中的美觀轉譯文字，將每個元素的資訊視覺化。 動畫的 3D electron 模型會顯示在中間區域，而且可以從不同的角度來查看。

![互動](images/640px-periodictable-interaction.jpg)

![原型](images/640px-periodictable-prototypes.jpg)<br>
*互動原型*

使用者可以透過使用表格底部的按鈕來變更介面類別型-它們可以在平面、圓柱圖、球體圖和散佈圖之間切換。

## <a name="common-controls-and-patterns-used-in-this-app"></a>此應用程式中使用的通用控制項和模式

### <a name="interactable-object-button"></a>互動物件 (按鈕) 

[互動物件](../../design/interactable-object.md)是一個物件，可以回應基本的 HoloLens 輸入。 它是以預製專案/腳本的形式提供，您可以輕鬆地將它套用到任何物件。 例如，您可以在場景中製作咖啡杯互動，並回應像是注視、碰點、導覽和操作手勢等輸入。 [深入了解](../../design/interactable-object.md)

![nteractable 物件](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>物件集合

[物件集合](../../design/object-collection.md) 是一種物件，可協助您配置各種不同圖形中的多個物件。 它支援平面、圓柱、球體和散佈圖。 您可以設定其他屬性，例如 radius、資料列數目和間距。 [深入了解](../../design/object-collection.md)

![物件集合](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>技術詳細資訊

您可以在[混合現實設計實驗室的 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上，尋找專案應用程式的定期表格的腳本和 prefabs。

## <a name="porting-story-for-hololens-2"></a>HoloLens 2 的移植案例

閱讀有關如何使用 HoloLens 2 的 instinctual 互動來更新專案應用程式之定期表格的案例。

[元素週期表 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon 公園</b></a><br>UX 設計者 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱

* [MRTK 範例中樞](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [表面](sampleapp-surfaces.md) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [元素週期表 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)