---
title: 設計全像影像
description: 透過 Microsoft 全新的設計全像影像應用程式，瞭解混合的現實。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK，混合的現實工具組，全像投影，設計全像投影、學習、範例應用程式、混合現實耳機、虛擬實境耳機、何謂虛擬實境
ms.openlocfilehash: 243b6f28da7b074b3ff6d48794d525ac08281fa7
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355338"
---
# <a name="the-making-of-designing-holograms"></a>設計全息製作

> [!NOTE]
> 請在此頁面上，允許小型載入視窗，以將所有酷炫的 Gif 和 embedded 影片全部考慮。

學習如何設計混合的現實可能很困難，特別是在視覺效果的情況下，這不一定會正確轉譯成2D 設計流程。 在 Microsoft，我們已建立可供您下載 HoloLens 2 的免費應用程式，可協助您透過第一手來瞭解混合現實 UX 設計的基本概念。 設計全像影像應用程式的獨特方法是探討混合現實行為、秘訣和建議，以協助您建立自己的吸引人和出色的 HoloLens 應用程式。 從 Microsoft Store 免費下載應用程式，並從 Microsoft 的混合現實設計小組學習！

> [!div class="nextstepaction"]
> [下載設計全像影像應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![設計全息圖的示範房間中的標頭追蹤場景動畫 GIF](images/designing-holograms/demo-room.gif)

*設計全息圖的示範房間 (也稱為娃娃房子)*

## <a name="designing-for-mixed-reality"></a>混合現實的設計

我和許多人一樣，都是用來設計行動應用程式。 從2D 設計世界開始，一直到目前為止都在世界各地的空間運算，一直都是很大的轉變。 在混合的現實情況下，應用程式不會再局限于2D 螢幕;事實上，它們幾乎是免費的，放在真實世界中，並與實際物件互動。

對我來說，將3D 體驗連接到傳統2D 設計程式是混合現實開發最具挑戰性的層面。 在與客戶對話的情況下，我會聽到像是「我知道要包含哪些功能，以及如何讓它們正常運作。 它是程式碼，我可以遵循檔和教學課程，但是使用者體驗？ 許多功能、不同的輸入選項、不同的案例和實體環境都很龐大」。

![來自三藩市的 HoloLens 2 設計研討會中的影像 ](images/designing-holograms/workshop.jpeg)
 *，從三藩市的 HoloLens 2 設計研討會*

## <a name="an-opportunity-to-teach"></a>教授的機會

它一開始並不明顯，但有一個絕佳的機會，可以使用 mixed reality 作為媒體來教授。

設計全像影像是一種視覺體驗，可解釋混合的現實設計概念和建議。 這只是您和一個示範混合現實設計概念的虛擬老師。 所有專案都是從第三個人的觀點來看，在您自己的空間中有很穩固的體驗。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*設計全像投影片影片*

## <a name="exploring-the-doll-house"></a>探索娃娃房子

娃娃房子是我們在整個應用程式中使用的虛擬環境，這是一個 80 x 60 x 40-cm 微型空間，其中包含大部分房間共通的基本元素，例如牆、燈、傢俱、表格和電視。 娃娃房子是應用程式體驗的主要 protagonist，因此我們需要確定它在任何環境中都能正常運作。 把它想像成一個小型的示範空間，用來視覺化各種混合現實概念。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Dollhouse 調整行為的影片*

### <a name="11-vs-110-prototypes"></a>1:1 與1:10 原型

我們最初的假設是，1:1 示範會很令人驚奇，看起來像是真實的老師。 使用者會看到老師在真實規模中看到的所有內容。 不過，我們會立即發現有幾個問題：

- 大部分的開發人員會在辦公室或房間以外的房間內執行其應用程式，因此無法容納。
- 顯示是加總的，這表示整個虛擬環境會在使用者的房間上重迭。 這可能會造成兩個數據表混淆，或許是雙 couches 和沒有對齊的牆。
- 而最糟的是，所有虛擬環境都受到視野的高度限制。

當我們嘗試迷你的1:10 規模時，結果就是一個很棒的鳥，也就是實際的房間，您可以從任何角度查看所有的東西 最令人驚訝的是，大部分的測試人員發現它更能看到較小的版本，而不是切換回1:1 規模。 因此，我們決定實際報廢1:1 版，並避免需要額外的工作來調整 UI 和應用程式的其他層面。

![使用1:1 調整規模 ](images/designing-holograms/1-1-scale.png)
 *欄位與 1:1* 級別的視圖模式

![使用1:10 調整規模 ](images/designing-holograms/1-10-scale.png)
 *欄位與 1:10* 級別的視圖模式

## <a name="using-mixed-reality-capture"></a>使用混合實境擷取

此應用程式的其中一項最特性功能是使用混合實境擷取來教授和展示混合的現實設計概念。

Microsoft 在三藩市有混合實境擷取 studio。 Microsoft 也會將這項技術授權給其他工作室，包括華盛頓特區的圖片、Metastage 在洛杉磯、倫敦的 Dimension 工作室、首爾的 SK 電信，以及柏林的 Volucap。 您可以在 [這裡找到混合實境擷取工作室](https://www.microsoft.com/mixed-reality/capture-studios)的詳細資訊。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Daniel Escudero 的原始素材，從三藩市的混合實境擷取 Studio 中的106攝影機之一。*

此捕捉程式會產生 keyframed 網格、法線和材質，以供進一步的進入生產階段，或是準備好播放作為 h.264 壓縮的檔案。 這些檔案可以匯入 Unity、Unreal、native 和 WebXR，並在 Windows、iOS、Mac、Android、魔術 Leap 和 Playstation VR 上執行。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*提供用來分析包含音訊和內嵌網格影片之 mp4 的捕獲播放機。*

## <a name="manipulating-captures-and-virtual-objects"></a>操作捕獲和虛擬物件

混合的事實捕獲會產生使用者或動物的虛擬標記法，但有時您可能需要這些字元與其他虛擬物件互動。 下列兩個範例示範我們操作幕後以達成此效果的不同方式。

### <a name="head-gaze-adjustment"></a>前端注視調整

Headgaze 調整可讓您在執行時間移動已捕捉的人員頭部，這表示您可能會有使用者的捕獲臉部。 在我們的案例中，我們使用它來顯示您感興趣的視圖欄位和欄位。 您在下面所見的是移動 gameobject，作為要查看的標題。 當我們將目標從側邊移至一邊時，捕捉的開頭會如下所示。

我們使用這個技巧來確定閒置的捕獲一律會面對放在娃娃房子不同部分的全像投影。 

![在 Unity 中的目標 gameobject 之後，于執行時間移動了 Capture 的標頭](images/designing-holograms/head-adjustment.gif)

*在 Unity 中的目標 gameobject 之後，會在執行時間移動 Capture 的開端。*

### <a name="syncing-animated-objects"></a>同步處理動畫物件

第二個是建立物件的動畫，以與捕捉的移動進行同步處理。 在應用程式的不同部分中，我們會每隔五個畫面匯入特定捕獲的連續 Obj。 然後，Obj 會在場景中以動畫顯示，以確保它們符合捕捉的相對應框架。 它是動畫和 keyframing 的繁瑣程式，但結果很棒，您現在可以看到與非捕捉物件的混合實境擷取互動。

![混合實境擷取和 UI 面板之間的同步動畫](images/designing-holograms/synced-objects.gif)

*混合實境擷取和 UI 面板之間的同步動畫*

### <a name="ui-creative-process"></a>UI 創意流程

當我們開始 ideating UI 設計時，除了傳輸資訊外，我們也想要展示一些魔術以及全息圖案提供的可能性。 只要顯示靜態2D 視窗和文字方塊並不會直接在3D 世界中，也不會顯示許多可能性，因此從一開始，我們決定要從該視窗中移除，並充分利用全像立體空間。

一開始，我們會先將一些粗細新增至面板和圖示，以及文字資訊。 但是，以使用者的身份來看，我看到的是一個文字方塊。 具有影像的文字方塊，但我們不在此。 我們進一步利用混合現實工具組 (MRTK) 著色器。 MRTK 著色器變成一項強大的工具，而且我們已使用其樣板功能，有些可能會將其視為入口網站效果，以將負面深度新增至面板。 這表示，圖示現在會出現在透明面板後方，而不是在文字方塊前面加上專案。 我現在看到的就是使用者，這就是我在現實世界中無法再複寫的內容，而且這就是您開始進行全像攝影的地方。 此外，我也不想要閱讀的使用者，就是在實體世界中這麼多。

顯然圖示的運作方式比簡單的文字更好，因此為了提供更強大的指引，我接著開始建立一組動畫物件和虛擬人偶，每個物件都告訴您有關在個別案例中所做的事情，以及其使用方式的一小部分。

![互動式全息式功能表系統的動畫 GIF](images/designing-holograms/creative-process.gif)

## <a name="try-it-out-moments"></a>「立即試用」分鐘

設計全像混合的現實概念，但也可讓您在您的房間內試用。 在這些說明中，我們會暫停並讓您離開娃娃房子並進入互動式時刻。 以下是這些互動式時刻的一些範例：

![手形追蹤框架的動畫 GIF，顯示當偵測到手時以及何時進入 view 欄位時](images/designing-holograms/try-out-1.gif)

*當偵測到手時，以及當他們進入 view 欄位時，所顯示的手追蹤框架。*

![與衝突 crystals 進行互動的動畫 GIF](images/designing-holograms/try-out-2.gif)

*透過互動方式與衝突 crystals 互動*

![探索近乎互動 affordances 的動畫 GIF](images/designing-holograms/try-out-3.gif)

*探索近距離互動 affordances*

## <a name="about-the-team"></a>關於小組

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>首席技術設計人員</i><br>Dan 是設計全像市的創意總監，目前也是在三藩市的 Microsoft Mixed Reality 學術設計組長的設計，而且之前是 Microsoft 在倫敦的混合現實工作室之一。</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>聖馬丁 Wettig</b><br><i>資深3D 演出者</i><br>當您在設計全像全像是 Microsoft 的混合現實工作室中，有一位資深的3D 演出者在柏林上，會導致3D 藝術和 UI 設計。</td>
</tr>
</table>

很棒的是，「混合的現實設計小組」可讓您在此專案的每個步驟中，將許多人的知識與重要的團隊分享給令人驚喜的 [物件](https://objecttheory.com/) 。 感謝您的熱情，讓您在設計上有出色的關注。

> [!div class="nextstepaction"]
> [下載設計全像影像應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)