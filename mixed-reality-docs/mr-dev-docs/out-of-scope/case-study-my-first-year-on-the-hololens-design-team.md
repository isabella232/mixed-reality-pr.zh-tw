---
title: 個案研究-我在 HoloLens 設計團隊的第一年
description: 當我在2016年1月加入 HoloLens 設計小組時，從 2D flatland 到3D 世界的旅程已開始。
author: designnomad
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、設計、編輯、個人
ms.openlocfilehash: 3c6444094663498ef4b253df6ed8dd7e82cc8319
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91681124"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>個案研究-我在 HoloLens 設計團隊的第一年

當我在2016年1月加入 HoloLens 設計小組時，從 2D flatland 到3D 世界的旅程已開始。 加入小組之前，我的3D 設計經驗很少。 這就像是從單一步驟開始，數千英里旅程的中文句耳熟能詳諺語，除了我的案例中，第一個步驟是閏的！

![從2D 到3D 的飛躍](../develop/platform-capabilities-and-apis/images/2D_to_3D-800px.gif)<br>
*從2D 到3D 的飛躍*

> *「我覺得我一直跳到驅動程式基座，而不知道如何推動汽車。我有大量的害怕，但卻非常專注。」*<br>
> — Hae 金先生

在過去一年來，我的技能和知識越快越好，但我還是有許多學習。 在這裡，我使用影片教學課程撰寫了4個觀察，記錄從2D 到3D 互動設計工具的轉換。 我希望我的經驗將會激發其他設計工具，以使其成為3D。

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>良好的框架。 Hello 空間/diegetic UI

當我設計海報、雜誌、網站或應用程式畫面時，定義的框架 (通常會是每個問題的常數) 。 除非您是在 HoloLens 或其他的 VR 裝置中閱讀這篇文章，否則您會 *從外部* 透過2d 螢幕安全地保護框架。 內容不在您的外部。 不過，混合現實耳機可 *消除框架* ，因此您可以在內容空間中，查看並逐步解說內容。

我在概念上瞭解這一點，但在開始之前，我犯了錯誤，只是把2D 思考轉移到3D 空間。 這顯然無法正常運作，因為3D 空間有自己的唯一屬性，例如根據使用者的前端) 移動 (的視圖變更，而使用者可以使用) ，以裝置的屬性和人類的 [使用者緩和 (的不同需求](https://www.youtube.com/watch?v=-606oZKLa_s/) 。 例如，在 2D UI 設計空間中，鎖定螢幕角落的 UI 元素是一個非常常見的模式，但這個抬頭顯示器 (Head Up 顯示) 樣式 UI 在 MR/VR 體驗中並不自然，它會阻礙使用者深度空間並造成使用者不適感。 就像是在眼鏡上有令人討厭的灰塵，也就是您要定生死的。 經過一段時間之後，我瞭解到將內容放在3D 空間中，並新增以主體鎖定的行為，讓內容以相對固定的距離來追蹤使用者，是很自然的。

![主體-鎖定](../develop/platform-capabilities-and-apis/images/bodylockedtagalong.gif)<br>
*主體-鎖定*

<br>

![全球鎖定](../develop/platform-capabilities-and-apis/images/worldlocked.gif)<br>
*全球鎖定*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>片段：絕佳 Diegetic UI 的範例

[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)是 [Asobo Studio](https://www.asobostudio.com/) for HoloLens 所開發的第一個人犯罪 thriller，示範絕佳的 Diegetic UI。 在這個遊戲中，使用者會成為主要的字元，也就是嘗試解決謎題的偵探。 在使用者的實體室中解決這個謎試想的 pivotal 線索，通常是內嵌于虛構物件內，而不是本身的現有時間。 此 diegetic UI 比主體鎖定的 UI 更容易探索，因此 Asobo 小組巧妙地使用許多提示，包括虛擬字元的注視方向、音效、燈光和導軌 (例如，指向指示) 位置的箭號，以吸引使用者的注意力。

![片段-Diegetic UI 範例](../develop/platform-capabilities-and-apis/images/fragments-game-example-1.jpg)<br>
*片段-Diegetic UI 範例*

### <a name="observations-about-diegetic-ui"></a>Diegetic UI 的觀察

空間 UI (內文鎖定和世界鎖定的) 和 diegetic UI 都有自己的優點和缺點。 我鼓勵設計人員盡可能試用許多 MR/VR 應用程式，並針對各種 UI 定位方法開發自己的瞭解和 sensibility。

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Skeuomorphism 和神奇互動的傳回

Skeuomorphism，模仿真實世界物件圖形的數位介面，在設計產業的過去5–7年都是「uncool」。 當 Apple 最後提供了 iOS 7 的平面設計方式時，就好像 Skeuomorphism 終於成為介面設計方法。 然後，新的中型、MR/VR 耳機抵達市場，似乎 Skeuomorphism 再次傳回。 : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>作業模擬器： skeuomorphic VR 設計範例

[作業](https://jobsimulatorgame.com/)模擬器是 [Owlchemy Labs](https://owlchemylabs.com/) 所開發的比較古怪遊戲，是 skeuomorphic VR 設計最受歡迎的範例之一。 在此遊戲中，播放程式會傳輸到未來，機器人會將人們取代為在下列四項作業中的其中一項作業中執行的工作：自動技師修理、Gourmet Chef、商店職員或 Office Worker。

Skeuomorphism 的優點很清楚。 這項遊戲中熟悉的環境與物件可協助新的 VR 使用者感覺更舒適，並且在虛擬空間中呈現。 它也會將熟悉的知識和行為與物件及其對應的實體反應產生關聯，讓他們感覺像是控制。 例如，若要飲料咖啡，人們只需要走到咖啡機、按下按鈕、抓住杯把手，並將其朝向嘴，就像在現實世界中一樣。

![作業模擬器](../develop/platform-capabilities-and-apis/images/job-simulator.gif)<br>
*作業模擬器*

由於 MR/VR 仍是開發媒體，因此必須使用特定程度的 skeuomorphism 來解釋 MR/VR 技術，並將它引進給世界各地的大型物件。 此外，對於特定類型的應用程式（例如外科或飛行模擬），使用 skeuomorphism 或實際的標記法可能很有説明。 因為這些應用程式的目標是要開發和調整可直接在真實世界中套用的特定技能，所以更接近真實世界的模擬，也就是更能獲得知識的轉移。

請記住，skeuomorphism 只是一種方法。 MR/VR 世界的潛能遠高於這項功能，而設計人員應該致力於建立神奇的超自然互動，也就是 MR/VR 世界唯一可能的新 affordances。 一開始，請考慮將神奇的電源新增至一般物件，讓使用者能夠滿足其基本需求，包括遙傳和 omniscience。

![Doraemon 的神奇大門 (left) 和 Ruby slippers (right) ](../develop/platform-capabilities-and-apis/images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon 的神奇大門 (left) 和 ruby slippers (right)*

### <a name="observations-about-skeuomorphism-in-vr"></a>在 VR 中 skeuomorphism 的觀察

從 Doraemon 的「隨處大門」中，盎司的 Wizard 中的「Ruby Slippers」到 Harry 哈利波特中的「Maurader 的地圖」，這是在熱門神奇中使用為數眾多 power 小說的一般物件範例。 這些神奇物件可協助我們將真實世界與絕佳之間的連接視覺化，兩者之間有何關係。 請記住，在設計神奇或 surreal 物件時，必須在功能和娛樂之間取得平衡。 請注意，只針對新奇的目的，建立純粹神奇的誘惑。

## <a name="understanding-different-input-methods"></a>瞭解不同的輸入方法

當我設計2D 媒體時，必須專注于輸入的觸控、滑鼠和鍵盤互動。 在 MR/VR 設計空間中，我們的主體會變成介面，而使用者可以使用更廣泛的輸入方法：包括語音、注視、手勢、 [6 dof 控制器](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)和手套，以更直覺的方式和與虛擬物件的直接連接。

![HoloLens 中的可用輸入](../develop/platform-capabilities-and-apis/images/inputs.jpg)<br>
*HoloLens 中的可用輸入*

> *「最適合某些事物，而最糟的是其他專案。」*<br>
> — [帳單 Buxton](https://www.billbuxton.com/)

例如，在 HMD 裝置上使用「裸機」和「相機感應器」的手勢輸入，可讓使用者離開控制器或戴 sweaty 手套，但經常使用可能會導致實體疲勞 (gorilla arm) 。 此外，使用者還必須將他們的手保持在視線內;如果相機看不到手中，就無法使用手。

語音輸入在處理複雜的工作時很有説明，因為它可讓使用者使用一個命令來剪下多個嵌套功能表 (例如「顯示 Laika studio 所製作的電影」。) 在結合其他樣式時也非常經濟實惠 (例如，「臉部 me」命令會將使用者正在尋找的全像是使用者) 的影像排列方向。 不過，語音輸入可能無法在雜訊的環境中運作，或可能不適合在很安靜的空間中使用。

除了手勢和語音之外，手中的追蹤控制器 (例如，Oculus touch、Vive ) 等等，因為它們很容易使用、準確、充分運用人們的 [proprioception](https://en.wikipedia.org/wiki/Proprioception)，並提供被動式 haptic 提示。不過，這些優點的代價是無法實際操作，而且可以使用完整的手指追蹤。

![Senso (Left) 和 Manus VR (Right) ](../develop/platform-capabilities-and-apis/images/senso-and-manus-vr.jpg)<br>
*Senso (Left) 和 Manus VR (Right)*

因為 MR/VR wave，所以手套不像控制器一樣受歡迎。 最新的大腦/想法輸入已開始將 EEG 或 EMG 感應器整合到耳機 (（例如 [MINDMAZE VR](https://www.mindmaze.com/)) ），進而吸引虛擬環境的介面。

### <a name="observations-about-input-methods"></a>關於輸入方法的觀察

這些只是在 MR/VR 市場中提供的輸入裝置範例。 他們會持續增加，直到產業成熟並同意最佳作法為止。 在那之前，設計人員應該繼續留意新的輸入裝置，並在其特定專案的特定輸入方法中妥善精通。 設計人員必須尋找限制內的創意解決方案，同時也會扮演裝置的強項。

## <a name="sketch-the-scene-and-test-in-the-headset"></a>在耳機中草擬場景並測試

當我在2D 中工作時，大部分的內容都是直接草繪。 不過，在混合的現實空間中，並不夠。 我必須草擬整個場景，以充分想像使用者和虛擬物件之間的關聯性。 為了協助我的空間思考，我開始在 [電影院 4d](https://www.maxon.net/en/products/cinema-4d/overview/) 中草擬場景，有時會建立簡單的資產，以在 [Maya](https://www.autodesk.com/products/maya/overview/)中建立原型。 我從未在加入 HoloLens 團隊之前使用過這兩種程式，但仍是新手，但使用這些3D 程式絕對可説明我熟悉新術語，例如 [著色器](https://en.wikipedia.org/wiki/Shader) 和 [IK (反向運動) ](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)。

**「無論如何緊密地在3D 中描繪場景，耳機的實際體驗幾乎都不會與草圖一樣。這就是為什麼要在目標耳機中測試場景是很重要的。」— Hae 金**

針對 HoloLens 原型設計，我試著在 [混合現實教學](../develop/unity/tutorials.md) 課程中開始進行所有教學課程。 然後我開始使用 [HoloToolkit](https://github.com/Microsoft/HoloToolkit-Unity/) ，讓 Microsoft 提供給開發人員，以加速開發全息的應用程式。 當我遇到問題時，我將問題張貼到 [HoloLens 問題 & 回應論壇](https://forums.hololens.com/categories/questions-and-answers/)。

在取得 HoloLens 原型設計的基本概念之後，我想要讓其他非半截成為原型。 我製作了一段影片教學課程，教您如何使用 HoloLens 開發簡單的 projectile。 我會簡短說明基本概念，因此即使您在 HoloLens 開發中有零經驗，也應該能夠跟著做。

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*我為非程式設計人員建立了這個簡單的教學課程，像是自己。*

針對 VR 原型設計，我採用了在 [Vr 開發學校](https://learn.vrdev.school/) 的課程，也會在 Lynda.com 上 [建立虛擬實境的3d 內容建立](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) 。 VR 開發人員在撰寫程式碼方面提供更深入的知識，而且 Lynda.com 課程提供了建立適用于 VR 之資產的簡短簡介。

## <a name="take-the-leap"></a>採用閏

一年前，我覺得這一切都有點困難。 現在我可以告訴您，它的工作是100%。 MR/VR 仍然是非常年輕的媒體，而且有很多有趣的可能性正在等待實現。 我覺得靈感，幸運能夠在設計未來的一小部分玩。 我希望您會在3D 空間的旅程上加入我！

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="../develop/platform-capabilities-and-apis/images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae 金先生</b><br>UX 設計工具 @Microsoft</td>
</tr>
</table>

 
