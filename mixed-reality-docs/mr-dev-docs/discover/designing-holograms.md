---
title: 設計全像投影
description: 透過 Microsoft 全新設計全像投影應用程式，瞭解混合的現實。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK，混合現實工具組，全像投影，設計全像投影，學習，範例應用程式，混合現實耳機，虛擬實境耳機，何謂虛擬實境
ms.openlocfilehash: fb60dabcd03d276a7d901ee5b2f061460fbfa05acfbdf226a8aee9325f160cff
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192370"
---
# <a name="the-making-of-designing-holograms"></a>設計全像投影

> [!NOTE]
> 請在此頁面上，允許小型載入視窗，以將所有酷炫的 Gif 和 embedded 影片全部考慮。

Learning 如何設計混合的現實可能很困難，因為媒體不一定會正確地轉譯成2d 設計流程。 在 Microsoft，我們為 HoloLens 2 建立了免費的應用程式，協助您瞭解混合現實 UX 設計第一手的基本概念。 設計全像投影應用程式的唯一方法是探討混合現實行為、秘訣和建議，以協助您建立吸引人且令人驚奇的 HoloLens 應用程式。 從 Microsoft Store 免費下載應用程式，並從 Microsoft 的混合現實設計小組學習！

> [!div class="nextstepaction"]
> [下載設計全像投影應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

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

設計全像投影是說明混合現實設計概念和建議的視覺體驗。 這只是您和一個示範混合現實設計概念的虛擬老師。 所有專案都是從第三個人的觀點來看，在您自己的空間中有很穩固的體驗。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*設計全像投影的尾端影片*

## <a name="exploring-the-doll-house"></a>探索娃娃房子

娃娃房子是我們在整個應用程式中使用的虛擬環境。 環境是 80 x 60 x 40-cm 的空間，其中包含大部分房間共通的基本元素，例如牆壁、燈、傢俱、表格和電視。 娃娃房子是應用程式體驗的主要 protagonist，因此我們需要確定它在任何環境中都能正常運作。 把它想像成一個小型的示範空間，用來視覺化各種混合現實概念。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Dollhouse 調整行為的影片*

### <a name="11-vs-110-prototypes"></a>1:1 與1:10 原型

我們最初的假設是，1:1 示範會很令人驚奇，看起來像是真實的老師。 使用者會看到老師在真實規模中看到的所有內容。 不過，我們會立即發現有幾個問題：

- 大部分的開發人員會在辦公室或房間以外的房間內執行其應用程式，因此無法容納。
- 顯示是加總的，這表示整個虛擬環境會在使用者的房間上重迭。 這可能會造成兩個數據表混淆（可能是雙 couches）和沒有對齊的牆。
- 而最糟的是，所有虛擬環境都受到視野的高度限制。

當我們嘗試迷你1:10 規模時，結果就是一個很棒的鳥，也就是實際的房間。 您可以同時看到所有從任何角度進入的內容。 最令人驚訝的是，大部分的測試人員發現它更能看到較小的版本，而不是切換回1:1 規模。 因此，我們決定實際報廢1:1 版，並避免需要額外的工作來調整 UI 和應用程式的其他層面。

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

此捕捉程式會產生 keyframed 網格、法線和材質，以供進一步的進入生產階段，或是準備好播放作為 h.264 壓縮的檔案。 這些檔案可以匯入 Unity、Unreal、Native 和 WebXR 專案中。 檔案可以在 Windows、iOS、Mac、Android、魔術 Leap 和 Playstation VR 上執行。

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

第二個是建立物件的動畫，以與捕捉的移動進行同步處理。 在應用程式的不同部分中，我們會每隔五個畫面匯入特定捕獲的連續 Obj。 然後，Obj 會在場景中以動畫顯示，以確保它們符合捕捉的相對應框架。 它是動畫處理和 keyframing 的繁瑣程式，但結果很棒。 您現在可以看到與非捕捉物件互動的混合實境擷取。

![混合實境擷取和 UI 面板之間的同步動畫](images/designing-holograms/synced-objects.gif)

*混合實境擷取和 UI 面板之間的同步動畫*

### <a name="ui-creative-process"></a>UI 創意流程

當我們開始進行 UI 設計時，我們想要示範一些像是「全息」所提供的魔術和可能性。 單純地顯示靜態2D 視窗和文字方塊，並不會直接在3D 世界中。 手中的許多可能性都不會顯示，因此從一開始，我們決定要從該位置移出，並充分利用全像立體空間。

一開始，我們開始將一些粗細新增至面板、圖示和文字資訊。 但是，以使用者的身份來看，我看到的是一個文字方塊。 具有影像的文字方塊，但不存在。 我們進一步利用混合現實工具組 (MRTK) 著色器。 MRTK 著色器變成一項強大的工具，並使用其樣板功能將負面深度新增至面板。 這表示，圖示現在會出現在透明面板後方，而不是在文字方塊前面加上專案。 我現在看到的就是使用者，這就是我在現實世界中無法再複寫的內容，而且這就是您開始進行全像攝影的地方。 此外，我還不太喜歡閱讀的使用者，而是在實體世界中做過許多事。

顯然圖示的運作方式比簡單的文字更好，為了提供更強大的指引，我接著開始建立一組動畫物件和虛擬人偶，每個物件都告訴您有關在個別案例中所做的事情，以及其使用方式的一小部分。

![互動式全息式功能表系統的動畫 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>核心概念

**Head 追蹤和眼睛追蹤**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

**手動追蹤**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

**空間感知**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

**全像攝影框架**

![使用者的動畫 GIF，以醒目提示的全像全像 dollhouse 來搜尋](images/designing-holograms/FOVandFOI.gif)

**座標系統**

![以反白顯示座標系統的方式 dollhouse 使用者的動畫 GIF](images/designing-holograms/CoordinateSystems.gif)

**眼球追蹤**

![使用者的動畫 GIF，查看已醒目提示眼睛光線的靜止全息影像](images/designing-holograms/EyeTracking.gif)

**房間掃描視覺效果和空間對應**

![正在對應之 dollhouse 內所有表面的動畫 GIF](images/designing-holograms/SpatialMapping.gif)

**場景理解**

![所辨識 dollhouse 中物件的動畫 GIF](images/designing-holograms/SceneUnderstanding.gif)

**使用手光線的點和認可**

![醒目提示手動光線之使用者的動畫 GIF](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>「立即試用」分鐘

設計全像投影教授混合的現實概念，但也可讓您在您的房間內試用。 在這些說明中，我們會暫停並讓您離開娃娃房子並進入互動式時刻。 以下是這些互動式時刻的一些範例：

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
<td style="border-style: none"><b>Daniel Escudero</b><br><i>首席技術設計人員</i><br>Dan 是設計全像投影的創意總監，目前以三藩市的 microsoft mixed reality 學術設計組長的形式運作，而且之前是 microsoft 在倫敦的混合現實工作室之一的設計工具。</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>聖馬丁 Wettig</b><br><i>資深3D 演出者</i><br>聖馬丁在設計全像投影時，會導致3d 藝術和 UI 設計，而且先前是在柏林的 Microsoft 混合現實工作室中的一位資深3d 演出者。</td>
</tr>
</table>

這項寶貴的感謝，讓您瞭解混合的現實設計小組，以分享更多的知識，以及 [物件理論](https://objecttheory.com/) 上令人驚奇的人，在專案的每個步驟中都是重要的成員。 感謝您的熱情，讓您在設計上有出色的關注。

> [!div class="nextstepaction"]
> [下載設計全像投影應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)