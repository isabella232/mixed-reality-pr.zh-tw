---
title: 開始設計並建立原型
description: 如果您已準備好要建立一些東西，請學習所需的基本概念以開始設計並建立原型。
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 探索, 散發, 索引, 登陸頁面, 設計, 開發, 教學課程, 範例應用程式, 基本, 案例研究, 資源, HoloLens 操作說明, 開放原始碼專案, 核心概念, 互動, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, HoloLens, MRTK, 混合實境工具組
ms.openlocfilehash: 3c28991fa35052a8b5cf5a071899ec14f2fec226
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702714"
---
# <a name="start-designing-and-prototyping"></a>開始設計並建立原型

![混合實境設計抽象](images/design-hero-image.png)

混合實境應用程式不同於現今既有的任何技術，其設計是很困難的工作。 您不僅必須將考量您所建立的實際和虛擬環境之間全新的組合，也必須考量隨之而來的全新使用者體驗。 由於混合實境牽涉領域很廣，我們僅選擇了若干重點及其設計頻譜，並將以一系列檢查點的形式列於下方。 這些檢查點通常應依序執行，但如果您有把握，則可以隨意跳到下列任何一節。

## <a name="design-checkpoints"></a>設計檢查點

使用下列檢查點，將您的應用程式構想和概念融入混合實境的世界中。

### <a name="1-getting-started"></a>1.開始使用

和所有的旅程一樣，在探索如何設計混合實境應用程式時，您也應從基本概念開始著手。 建議您詳閱[什麼是混合實境](../discover/mixed-reality.md)和[什麼是全像投影？](../discover/hologram.md)這兩篇文章，以取得沉浸式設計的概念。 閱讀完成後，您即可展開混合實境設計旅程！

![從 Designing Holograms 應用程式開始使用 GIF](images/HandTracking2.gif)

|  Checkpoint  |  結果  |
| --- | --- |
| [展開您的設計程序](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | 從 Microsoft 內部和外部的設計師收集有關混合實境的設計過程第一手資料 |
| [混合實境應用程式的類型](types-of-mixed-reality-apps.md) | 決定您的應用程式體驗在混合實境頻譜上的位置 |
| [Designing Holograms 應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | 深入了解混合實境 UX 設計的基本概念，方法是探討如何建立絕佳的 HoloLens 應用程式 (可從 HoloLens 2 的 Microsoft Store 下載) 的混合實境行為、秘訣和建議 |
| [MRTK 範例中樞](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | 體驗適用於混合實境的一般空間互動和 UX 建構元素 (可從 HoloLens 2 中的 Microsoft Store 下載) |
### <a name="2-core-concepts"></a>2.核心概念

無論您進行 VR 還是 AR 的開發，為了設計流暢的沉浸式體驗，有幾個核心概念是務必牢記在心的。 了解使用者的觀點、定位物件，以及確保每個人都感到安心舒適，是您在這個階段的旅程首先要考量的。 在本節結束時，您就已打好堅實的基礎，可繼續進入互動設計階段。

![核心概念範例影像](images/fragments-750px.jpg)

|  概念  |  結果  |
| --- | --- |
| [全像攝影框架](holographic-frame.md) | 了解使用者在配戴頭戴式裝置看您覆疊在實際環境上的內容時，是什麼情形 |
| [座標系統](coordinate-systems.md) | 了解如何將全像投影放置在世界上對使用者有意義的地方，不論是他們所在的實際空間或您所建立的虛擬領域 |
| [空間對應](spatial-mapping.md) | 錨定使用者世界中的物件，並利用真實世界的實體介面 |
| [舒適度考量](comfort.md) | 以模仿自然環境的方式建立和呈現沉浸式內容，以確保使用者的舒適度和安全性 |

### <a name="3-interaction-design"></a>3.互動設計

無論虛擬體驗有多美好、多讓人投入，若沒有互動，一切都是枉然。 本節將逐步引導您了解基本互動模型、手部和運動控制器，並了解如何使用語音輸入，以及收集使用者的眼睛追蹤資料。 本節結束後，您即可進入設計旅程的最後一個重要主題：使用者體驗。

![互動設計因素](images/UX_Hero_Manipulation.jpg)

|  概念  |  結果  |
| --- | --- |
| [互動模型](interaction-fundamentals.md) | 透過手部、眼睛和語音輸入，為您的使用者提供本能互動 |
| [手部和運動控制器](hands-and-tools.md) | 了解如何以使用者的手部近距離觸碰和操控全像投影，或透過精確的互動長距離操控 |
| [語音輸入](voice-input.md) | 在您的沉浸式應用程式中使用語音命令作為輸入，以控制全像投影和環境  |
| [眼睛追蹤](eye-tracking.md) | 以使用者所見景象的相關資訊，在全像攝影體驗中加入新一層的內容和人類理解 |

### <a name="4-user-experience-elements"></a>4.使用者體驗元素

在您已熟知基本的互動後，接下來即可專注於使用者體驗元素更細微的部分，並針對混合實境的獨特環境進行調整。 常見的行為、資產設計、物件調整和印刷樣式都應涵蓋在內，且應設法讓您的應用程式盡可能供使用者直覺使用。 本節完成後，正式的混合實境設計旅程即告終，但您可以參考[下一步是什麼？](#whats-next)一節，繼續深入探索。

![UX 元素](images/UX_Hero_BoundingBox.jpg)

|  概念  |  結果  |
| --- | --- |
| [通用控制項和行為](app-patterns-landingpage.md) | 了解常用的空間互動和 UI 建置組塊 |
| [色彩、光線和材質](color-light-and-materials.md) | 為混合實境設計將色彩、光源和材質納入考量的高品質資產 |
| [物件縮放比例](scale.md) | 盡可能整合較多的實際環境視覺提示，以協助使用者了解物件的位置、物件的大小，及其組成元素 |
| [印刷樣式](typography.md) | 在三維空間中使用清楚、可讀的文字，讓您的使用者獲得所需的重要資訊 |

## <a name="whats-next"></a>接下來要做什麼？

設計人員的工作無止境，在學習以新的開發架構建立沉浸式體驗時，尤其如此。 完成入門級設計教學後，以下各節將帶領您進一步深入混合實境開發的領域。 這些主題和資源無須依序使用，您可以隨意來回探索！

### <a name="choose-a-prototyping-option"></a>選擇原型設計選項  

:::row:::   
    :::column:::    
       [![學習 Unity](images/logo-unity.png)](https://learn.unity.com/)<br>
        **[學習 Unity](https://learn.unity.com/)**<br>
        瞭解如何使用 Unity 建立互動式體驗。 邊做邊學，從開始到完成。
    :::column-end:::    
    :::column:::    
        [![混合實境工具組 (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[混合實境工具組 (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        透過混合實境工具組的空間互動和 UI 基本要素，您可以使用 Unity 快速進行混合實境的設計和開發。   
    :::column-end:::
    :::column:::    
        [![混合實境設計實驗室](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[混合實境設計實驗室](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        取得範例應用程式，示範如何使用 MRTK 的建置元素來建立美觀的混合實境體驗。
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        為 VR 而設計。 Microsoft Maquette 讓空間原型設計變得簡單、快速、身歷其境。 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="additional-resources"></a>其他資源

:::row:::
    :::column:::
       [![了解基本概念](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)<br>
        **[了解基本概念](../discover/get-started-with-mr.md#understand-the-basics)**<br>
        進一步瞭解混合實境的定義以及其使用方式。
    :::column-end:::
    :::column:::
        [![參加活動](images/74-16.png)](../whats-new/sf-academy-events.md)<br>
         **[參加活動](../whats-new/sf-academy-events.md)**<br>
        參觀硬體並取得實際操作教學課程，製作您的第一個 HoloLens 2 應用程式。
    :::column-end:::
    :::column:::
        [![安裝工具](images/74-17.png)](../develop/install-the-tools.md)<br>
         **[安裝工具](../develop/install-the-tools.md)**<br>
        使用安裝檢查清單來取得建置 HoloLens 和混合實境應用程式所需的工具。
    :::column-end:::
    :::column:::
        [![開始進行開發](images/74-18.png)](../develop/development.md)<br>
        **[開始進行開發](../develop/development.md)**<br>
        根據您的技能層級、工作風格或感興趣的平台，選擇開發路徑。
    :::column-end:::
:::row-end:::

<br>

<br>