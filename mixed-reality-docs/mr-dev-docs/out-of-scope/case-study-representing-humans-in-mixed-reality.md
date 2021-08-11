---
title: 個案研究-以混合現實表示人類
description: 當我們無法只建立絕佳的元素，但在混合現實中使用最實際的環境、物件和人員的功能時，會出現何種機會？
author: mavitazk
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、人類、頭像、Mixed Reality capture、體積型影片
ms.openlocfilehash: db21b6b02ce76403c2c59e37384c1c1602d8a63e003a8b5b6601c5daf7b9c2a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228520"
---
# <a name="case-study---representing-humans-in-mixed-reality"></a>個案研究-以混合現實表示人類

使用 light 的 James Turrell 設計。 逐步執行他的工作，使其深度和焦點都有意義。 牆壁看起來都是封閉且無限的，亮度提供了陰影的方式。 藉由仔細平衡光線的色彩和擴散來設計陌生的認知。 [Turrell 將這些 sensations 描述](https://www.sculpture.org/documents/scmag02/nov02/turrell/turrell.shtml) 為「 *感受您的眼睛*」，這是一種擴充其實際瞭解的方法。 很棒的世界（像是 Turrell imagines）是強大的工具，可利用我們的想法，而不像現今混合現實的沉浸式環境。

![Wide Out-James Turrell (1998) ](../develop/platform-capabilities-and-apis/images/wide-out-james-turrell.jpg)

## <a name="how-do-you-represent-complex-real-world-environments-in-mixed-reality"></a>您如何在混合現實中代表複雜的真實世界環境？

以沉浸式體驗表示 Turrell 的工作，讓您令人信服的挑戰。 光源、尺規和空間音訊帶來了表示工作的機會。 雖然展示的幾何周圍會需要相當簡單的3D 模型，但它們是演出者焦點的輔助：光對檢測的影響。

Turrell 的 stark、surreal minimalism 是其工作的特徵，但如果我們想要以混合現實中的複雜資料呈現展示，該怎麼辦？

![驚嘆號-Ai Weiwei (2013) ](../develop/platform-capabilities-and-apis/images/bang-ai-weiwie.jpg)

在2013中，「演出者 Ai Weiwei 會揭曉 tangling 在 Venice Biennale 上 [具有](https://www.designboom.com/art/ai-weiwei-bang-installation-at-venice-art-biennale-2013/) 886 古典 stools 的作品。 每個木制 stool 都來自中國熱情技術具高度價值的時代，而這些 stools 會在世代之間傳遞。 Stools 本身—在 Ai 對新式文化的評論方面來說，像是木材的複雜部分，也就是他們的審慎定位。

古典 stools 會透過其真實性來提供演出者的訊息。 實際的標記法對於體驗來說很重要，因為這是一項技術挑戰： Sculpting 每個 886 stools，都是大幅的詳盡且昂貴。 模型和定位需要多久的時間？ 您要如何維護材質的真實性？ 從頭開始重新建立這些物件，將會以許多方式來轉譯作品本身。 您要如何保存演出者的意圖？

## <a name="methods-of-capturing-mixed-reality-assets"></a>捕獲混合現實資產的方法

從頭開始建立某個事物的替代方法，就是捕捉真正的事物。 透過一組向前推進的捕獲方法，我們可以在混合現實 (環境、物件和人員) 中，開發出每個核心資產類型的真實標記法。

廣泛的分類範圍從妥善建立的2D 影片到最新形式的體積型影片。 在 Ai Weiwei 的表現案例中，掃描 (通常是由其基本技巧來參考，攝影測量) 可在建立展示時採用，並掃描每個 stools 本身。 360的相片和影片捕捉是另一種虛擬化體驗的方法，在整個展示中使用高品質的全方向攝影機。 使用這些技術，一開始就能瞭解規模的意義，理想的細節是查看每個部分的熱情技術。 這一切都是以數位形式提供，但實際上並不可能有新的絢爛和觀點。

![2D 至體積型影片](../develop/platform-capabilities-and-apis/images/2d-to-volumetric-video.png)

當我們無法只建立絕佳的元素，但在混合現實中使用最實際的環境、物件和人員的功能時，會出現何種機會？ 探索這些方法之間的重迭，有助於照亮媒體的趨勢。

針對環境和物件，360°映射軟體正在發展，以包含攝影測量的元素。 從場景隔離深度資訊，advanced 360 °影片可協助您在尋找虛擬場景時，減輕 fishbowl 的感覺。

對於人們而言，新的方法是結合及擴充動作捕捉和掃描的新方法：「移動捕捉」已經成為基礎，可將詳細的人力移動帶入視覺效果和 cinematic 的字元，而掃描也有先進的經驗，可捕獲臉部和手等詳細的人類視覺效果。 有了轉譯技術的進步，稱為體積型 video 的新方法會建立這些技術，並結合視覺效果和深度資訊，以建立新一代的3D 人類捕捉。

## <a name="volumetric-video-and-the-pursuit-of-authentic-human-capture"></a>體積型影片，並追求真正的人工捕捉

人類是故事行銷的核心，最常說的意義：人們說、執行或作為故事的主旨。 現今早期的沉浸式體驗的一些最吸引人和引人注目的時刻是社交的。 在您的客廳共用混合現實體驗，以在 unbelievable 新環境時看到您的朋友。 人力元素甚至是最棒的事實。

![在 VR 中 Mindshow](../develop/platform-capabilities-and-apis/images/mindshow-in-vr-640px.jpg)

虛擬人偶在沉浸式體驗中，可在故事行銷中啟用一種新的 embodiment。 最新的應用程式會重新思考虛擬主體擁有權的概念，並設定新一代的飛躍，以消除人們之間的距離。 像 [Mindshow](https://mindshow.com/) 這樣的公司開發了可利用虛擬人偶的創意工具，讓使用者完全採用新的角色和字元。 其他人正在探索 [藝術運算式的方法](https://en.wikipedia.org/wiki/Uncanny_valley)，這是一項可能無限制的創意機會，可以探索本質 (以及類似人類的屬性) 。 目前，這種缺乏的真實性有助於避免 [人類 likeness 的 uncanny](https://en.wikipedia.org/wiki/Uncanny_valley) ，以及針對日常開發人員提供的技術問題。 基於這些理由 (和更) ，很可能非實際的虛擬人偶會成為可預見的未來的預設值。 此外，雖然真實性對於混合的現實有很大的挑戰，但還是 *需要在3d 空間中真正表示人類的重要案例*。

在 Microsoft，從 Microsoft Research 中散播的小型團隊花了過去幾年的時間，透過體積型影片的形式來開發學習人類的方法。 今日的程式類似于影片生產： sculpted 資產是完整的3D 錄製。 效能和影像會以即時方式進行，這並不是演出者的工作，而是真實的標記法。 雖然這項技術剛開始擴展到商業應用程式，但體積型影片的含意對 [Microsoft 對更個人](https://www.youtube.com/watch?v=tcyj-_IEWt8)化運算的願景很重要。

![體積型 video SIGGRAPH 2015](../develop/platform-capabilities-and-apis/images/volumetric-video-siggraph-2015.gif)

真實的人工捕捉會在混合現實中解除新的獨特體驗類別。 看看您所辨識的人，不論是名人、同事或愛，都能在數位媒體中建立熟悉度的深度。 他們的臉部、其運算式、其移動中的細微之處，都屬於他們的身分。 當我們可以在3D 空間中抓住這些人類品質時，有哪些機會解除鎖定？

現今團隊將把重點放在娛樂和教育之類的磁區，來推動體積型影片的範圍： [Actiongram](https://www.microsoft.com/p/actiongram/9nblggh5ftmt) 有創意的字元和 [名人](https://www.youtube.com/watch?v=BwWueXlsOrA) 來建立混合的現實故事。 [目的地： Mars 展示](https://www.jpl.nasa.gov/news/news.php?feature=6220)，現在在 NASA 的甘迺迪空間中心，有體積型的傳說太空人影片 Aldrin 影片。 這項體驗可讓訪客在 Mars 的表面上四處解說，因為他在 Mars 上引進了人類 colonization 的追求。

## <a name="humans-are-fundamental-to-mixed-reality"></a>人類是混合現實的基礎

設計讓這些影片看起來很自然的方法是一項挑戰，但團隊卻發現很大的潛力。 當技術變得更容易存取，並從錄音移至即時捕獲時，這些商機將會擴充。

[Holoportation](https://www.microsoft.com/research/project/holoportation-3/) 是以相同的基本技術為基礎的研究工作，authentically 捕獲視覺效果和深度資訊，以及即時轉譯結果。 小組正在探索實際人類表示的能力，對於交談和分享體驗的未來有何意義。 當您從世界各地的某個人可以加入至您的環境時，會發生什麼事？

![交談的未來](../develop/platform-capabilities-and-apis/images/girl-with-dress.jpg)

從將新的深度層級分層到日常的應用程式（例如 Skype），到徹底改變數字會議和企業旅遊的概念—體積型影片開啟了獨特的案例：一位專家，是一位各地的大陸或數位朋友，坐在您生活中的 couches 和椅。 將真實的人類標記法新增至混合現實體驗，將會徹底改變數字會議和企業旅遊的概念。

就像 James Turrell 的抽象藝術和 Ai Weiwei 的重大真實感一樣，它也提供自己獨特的技術挑戰，因此，將人類視為創意的虛擬人偶和實際的捕獲方法。 您無法在另一種情況下略過，並探索每一項的潛能，以協助我們瞭解這個新空間中的人為互動。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Mark Vitazko" width="60" height="60" src="images/mark-vitazko.jpg"></td>
<td style="border-style: none"><b>Mark Vitazko</b><br>UX 設計者 @Microsoft</td>
</tr>
</table>
