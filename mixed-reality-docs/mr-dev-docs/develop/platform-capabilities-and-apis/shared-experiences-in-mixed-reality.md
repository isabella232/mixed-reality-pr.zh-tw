---
title: 混合現實的共用體驗
description: 全像攝影應用程式可能會從某個 HoloLens 共用空間錨點，讓使用者能夠在真實世界中的相同位置，跨多個裝置轉譯全像投影。
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 共用體驗、混合現實、全息圖、空間錨點、多使用者、多重
ms.openlocfilehash: fe738d07e57bd2f62cab8036a09ca6ab31d6544bdd9b6dacc8dde3445fa58214
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193582"
---
# <a name="shared-experiences-in-mixed-reality"></a>混合現實的共用體驗

全像投影不需要只對一位使用者保持私用。 全像攝影應用程式可能會從一個 HoloLens、iOS 或 Android 裝置共用[空間錨點](../../design/spatial-anchors.md)到另一個裝置，讓使用者能夠在真實世界中的相同位置轉譯多個裝置。

## <a name="six-questions-to-define-shared-scenarios"></a>定義共用案例的六個問題

在您開始設計共用體驗之前，請務必定義目標案例。 這些案例有助於說明您所設計的內容，並建立共同詞彙來協助比較和對比您的體驗所需的功能。 瞭解核心問題和解決方案的不同途徑，是發現這個新媒體固有的機會的關鍵。

透過 HoloLens 夥伴機關的內部原型和探勘，我們建立了六個問題來協助您定義共用案例。 這些問題都是一種架構，而不是完整的架構，可協助您將您案例的重要屬性。

### <a name="1-how-are-they-sharing"></a>1. 它們共用的方式為何？

簡報可能是由單一虛擬使用者所造成，而多個使用者可以共同作業，或老師可以為使用虛擬資料的虛擬學生提供指引，因為體驗的複雜度會根據使用者在案例中所擁有或可能存在的機構層級而增加。

![Holograph 在資料表上的男人和女性](images/man-and-women-with-holograph-on-table-500px.png)

有許多方法可以共用，但我們發現大部分的方法都分成三個類別：

* **簡報**：當多個使用者看到相同的內容時。 例如：教授將課程提供給數個學生使用相同的全像個人資料。 不過，教授可能會有自己的提示，以及其他人看不到的附注。
* 共同 **作業：當人們共同合作以** 達成一些常見的目標時。 例如：教授提供專案，以瞭解如何進行核心外科。 學生們都能與您合作，並建立共同的技能實驗室體驗，讓醫療學生能夠在核心模型上共同作業並學習。
* **指導** 方針：當某個人協助他人解決更多一對一的樣式互動中的問題時。 例如：教授當學生在共用體驗中執行「核心外科」技能實驗室時，提供指導方針的教授。

### <a name="2-what-is-the-group-size"></a>2. 群組大小為何？

**一對一** 的共用體驗可以提供強大的基準，而且理想的概念證明可以在這個層級建立。 但要注意的是， (超過六個人的大型群組共用) 可能會導致技術 (資料和網路) ，以及社交 (有 [數個虛擬人偶](https://vimeo.com/160704056)) 空間的影響。 當您從 **小型** 到 **大型群組** 進行時，複雜度會以指數方式增加。

我們發現群組的需求可以分為三種大小的類別：
* 1:1
* Small < 7
* 大型 >= 7

群組大小會造成重要問題，因為它會影響：

* 全息空間中的人員表示
* 物件的小數位數
* 環境規模

### <a name="3-where-is-everyone"></a>3. 大家在哪裡？

當共用體驗可以發生在相同的位置時，混合現實的強度就會派上用場。 我們稱之為 **共存**。 相反地，當群組已散發，而且至少有一個參與者不在相同的實體空間中 (通常是使用 VR 的情況) 我們稱之為 **遠端體驗**。 通常，您的群組 **同時** 具有共置和遠端參與者 (例如，會議室中的兩個群組) 。

![Holograph 在資料表上的三人](images/three-people-with-holograph-on-table-500px.png)

下列類別有助於傳達使用者的所在位置：

* 共 **置：您** 所有的使用者都將位於相同的實體空間。
* **遠端**：您的所有使用者都將位於不同的實體空間。
* **兩者**：您的使用者將會混合共用和遠端空間。

這個問題很重要，因為它會影響：

* 人們如何溝通？
    * 例如：是否應該有虛擬人偶？
* 他們看到的物件。 所有物件都是共用的嗎？
* 是否需要調整其環境？

### <a name="4-when-are-they-sharing"></a>4. 他們何時共用？

我們通常會考慮共用體驗的 **同步** 體驗：我們會將它們全部一起執行。 但是，如果我們包含由其他人新增的單一虛擬元素，就會有 **非同步** 案例。 Imagine 在虛擬環境中留下的附注或語音備忘錄。 您要如何處理您的設計中剩餘的100虛擬備忘錄？ 如果他們來自具有不同隱私權等級的數十個人呢？

請考慮您的體驗，這是其中一種類別的時間：

* **同步**：同時共用全像攝影體驗。 例如：兩位學生同時執行技能實驗室的學生。
* **以非同步方式**：在不同的時間共用全像攝影體驗。 例如：兩位學生執行技能實驗室，但在不同的時間使用不同的區段。
* **兩者**：您的使用者有時會同步共用，但會以非同步方式共用。 例如：教授學生在稍後為學生完成的指派，並在下一天離開學生的筆記。

這個問題很重要，因為它會影響：

* 物件和環境持續性。 例如：儲存狀態，使其可供取出。
* 使用者的觀點。 例如：可能會記住使用者在離開便箋時所看到的內容。

### <a name="5-how-similar-are-their-physical-environments"></a>5. 它們的實體環境有何相似之處？

除非這些環境的設計都完全相同，否則兩個完全不同的真實生活環境（共置式體驗除外）的可能性很輕巧。 您較有可能會有 **類似** 的環境。 例如，會議室很類似，他們通常會有一個集中位置的資料表，並以椅子括住。 另一方面，生活中的房間是不同的 * *，而且可以在無限的版面配置陣列中包含任何數量的傢俱。

![資料表上的 Holograph](images/holograph-on-table-500px.png)

請考慮採用下列兩種類別之一的共用體驗：

* **類似**：通常會有類似傢俱、環境燈和音效、實體房間大小的環境。 例如：教授在演講廳 A 中，學生在演講廳 B。課程廳 A 可能會有比 B 更少的椅子，但兩者都可能有實體桌來放置全像桌。
* **不同：傢俱** 設定、房間大小、燈光和音效考慮中不同的環境。 例如：教授在焦點房間內，但學生在大型的課程廳中，並填寫了學生和老師。

請務必 [考慮環境](/hololens/hololens-environment-considerations)，因為它會影響：

* 人們將如何體驗這些物件。 例如：如果您的體驗在資料表上的效果最佳，而且使用者沒有資料表？ 或在平面表面，但使用者有雜亂的空間。
* 物件的小數位數。 例如：在資料表上放置六英尺的人類模型可能會是一項挑戰，但是說出的模型很好用。

### <a name="6-what-devices-are-they-using"></a>6. 他們使用哪些裝置？

現在您很可能會看到兩個 [**沉浸式裝置**](../../discover/immersive-headset-hardware-details.md) 之間的共用體驗 (這些裝置的按鈕和相對功能可能稍有不同，但無法大幅) **或兩部全像裝置的** 解決方案是以這些裝置為目標的解決方案。 但請考慮 (行動/桌面參與者或觀察者) 的 **2d 裝置** 是否為必要的考慮，特別是在 **混合2d 和3d 裝置** 的情況下。 瞭解您參與者將使用的裝置類型是很重要的，不僅是因為它們具有不同的精確度、資料限制和機會，但因為使用者對每個平臺都有獨特的期望。

## <a name="exploring-the-potential-of-shared-experiences"></a>探索共用體驗的潛能

您可以結合上述問題的答案，以進一步瞭解您的共用案例，並在擴充體驗時 crystallizing 挑戰。 針對 Microsoft 的團隊，這有助於建立藍圖，以改善我們目前使用的體驗、瞭解這些複雜問題的細微之處，以及如何在混合現實中利用共用體驗。

例如，請考慮 HoloLens 啟動中的其中一個 Skype 案例：使用者已完成[如何修正中斷的燈光切換](https://www.youtube.com/watch?v=iBfzs3G8BEA)，以及來自遠端位置的專家的協助。

![透過適用于 HoloLens 的 Skype，以協助修正燈光開關](images/fix-a-broken-switch-with-hololens-640px.jpg)

*專家提供從 **2d**、桌上型電腦到 **3d、混合式** 裝置使用者的 **1:1** 指引。這是 **同步** 的 **指導** 方針，而且實體環境是 **不同** 的。*

這類體驗是我們目前體驗的步驟變更，也就是將影片和語音的典範套用至新的媒體。 但在未來，我們必須更妥善地定義案例的商機，以及反映混合現實強度的組建體驗。

請考慮 [OnSight](https://www.youtube.com/watch?v=XtUyUJAVQ6w)共同作業工具，它是由 NASA 的 Jet 推進實驗室所開發。 處理來自 Mars rover 任務之資料的科學家，可以在 Martian 橫向的資料中即時與同事共同作業。

![以遠端方式在不同的同事之間共同作業，以規劃 Mars Rover 的工作](images/onsight-nasa-jpl.gif)

*科學家使用 3d **和 2d** 裝置，來探索使用 **3d、混合式** 的裝置 **與一小組****遠端** 同事的環境。共同 **作業** 是 **同步** 的 (但可透過非同步方式進行) ，而實體環境 (幾乎) **類似**。*

OnSight 等經驗提供了共同作業的新商機。 從實際指向虛擬環境中的元素，到同事的旁邊，並在說明其調查結果時分享其觀點。 OnSight 使用深度的鏡頭和存在性來重新思考混合現實的共用體驗。

互動式共同作業是對話的探源、共同作業，並瞭解我們如何將此直覺套用至混合現實的複雜性是很重要的。 如果我們不能只在混合的現實中重新建立共用體驗，但強化它們，就會成為工作未來的典範轉變。 混合現實的共用體驗設計是嶄新且令人興奮的空間，而且我們只是在一開始。

## <a name="get-started-building-shared-experiences"></a>開始打造共用體驗

視您的應用程式和案例而定，將會有各種不同的需求可達成您所需的體驗。 其中包含：

* 比對 **-建立** 會話、通告會話、探索及邀請特定人員（不論是本機或遠端）來加入您的會話。
* **錨定共用**：能夠在常見的本機空間中，將座標組齊多個裝置，因此所有人都能在相同的位置上顯示全像影像。
* **網路** 功能：能夠在所有參與者的情況下，即時同步處理人員的位置、互動和移動。
* **狀態儲存體**：能夠將內建的內容和位置儲存在中間會話加入的空間中，並于稍後重新叫用，並讓網路問題更加強大。

共用體驗的關鍵是讓多個使用者在自己的裝置上看到相同的全像全球，並藉由共用錨點來調整跨裝置的座標來進行。

若要共用錨點，請使用 [Azure 空間錨點](/azure/spatial-anchors)：

* 使用者會先放置全像影像。
* 應用程式會建立 [空間錨點](../../design/spatial-anchors.md)，以精確地在世界中釘選該全像影像。
* 您可以透過[Azure 空間錨點](/azure/spatial-anchors/)，將錨點共用至 HoloLens、iOS 和 Android 裝置。

使用共用空間錨點時，每個裝置上的應用程式現在都有 [共同的座標系統](../../design/coordinate-systems.md) ，可放置內容。 現在，應用程式可以確保在相同位置放置並定位全像投影。

在 HoloLens 裝置上，您也可以從某個裝置離線共用錨點到另一個裝置。  使用下列連結來決定最適合您的應用程式。

## <a name="evaluating-tech-options"></a>評估技術選項

有各種服務和技術選項可用來協助建立多使用者的混合現實體驗。  選擇路徑可能會很難，因此採取案例導向的觀點，以下將詳細說明一些選項。

## <a name="shared-static-holograms-no-interactions"></a>共用靜態全像 (沒有互動) 

在您的應用程式中運用 [Azure 空間錨點](/azure/spatial-anchors/) 。  在裝置上啟用和共用空間錨點，可讓您建立應用程式，讓使用者在相同的時間內看到全像位置。  需要跨裝置進行額外的同步處理，讓使用者能夠與全像影像互動，並查看影像的移動或狀態更新。

## <a name="share-first-person-perspective"></a>共用第一個人的觀點

當您有支援的 Miracast 接收器（例如電腦或電視）時，請為本機使用者利用內建的 Miracast 支援，而不需要額外的應用程式程式碼。

在您的應用程式中、遠端使用者或您想要共用的非 Miracast 裝置上，利用[MixedReality WebRTC](https://github.com/microsoft/mixedreality-webrtc) 。  啟用 WebRTC 連接可讓使用者之間的1:1 音訊/影片串流，以及跨裝置進行訊息的資料通道。  混合現實實行可針對 HoloLens 進行優化，方法是將 HoloLens 使用者的觀點，提供給其他人的混合現實捕獲影片串流。  如果您想要將影片串流擴充至多個遠端用戶端，通常會使用 [MCU 服務提供者](https://webrtcglossary.com/mcu/) (Multipoint 會議單位) ，例如 [SignalWire](https://signalwire.com/)。  單鍵 SignalWire 部署至 Azure 可透過 [Freeswitch](https://github.com/andywolk/azure-freeswitch-gpu-windows)取得。

> [!NOTE]
> 請注意，SignalWire 是付費服務，而且不是 Microsoft 擁有/附屬的服務。

## <a name="presenter-spectator-applications-and-demos"></a>Presenter-Spectator 的應用程式和示範

利用 [MixedReality SpectatorView](https://github.com/microsoft/MixedReality-SpectatorView) 將 [spectator view 功能](spectator-view.md) 帶到您的應用程式。  啟用 (HL、Android、iOS 和攝影機的其他裝置) 查看 HoloLens 從相同位置的不同觀點來看，以及接收主機互動的更新，HoloLens 使用者與全像全像的互動。  使用相同應用程式的 spectator 附屬，觀賞、拍攝圖片，並記錄主機從您自己的空間觀點來處理應用程式中的全像影像的影片。

**注意：** 圖片會透過 iOS/Android 裝置上的螢幕擷取畫面取得。

## <a name="multi-user-collaborative-experience"></a>多使用者協同作業體驗

從我們的 [多使用者學習教學課程](../unity/tutorials/mr-learning-sharing-02.md)開始，此教學課程會利用適用于本機使用者的 [Azure 空間錨點](/azure/spatial-anchors/) 和 [Photon SDK](https://www.photonengine.com/PUN) ，在場景中同步處理內容/狀態。 建立在本機共同作業的應用程式，其中每位使用者都有自己在場景中的全像投影，而且每一位使用者都可以與全像全像全像全像  系統會在所有裝置上提供更新，並由 Photon 處理互動衝突管理。

> [!NOTE]
> 請注意， [Photon](https://www.photonengine.com/) 不是 Microsoft 的產品，因此可能需要與 Photon 的計費關係，才能 productize 和調整以獲得較高的使用量。

## <a name="future-work"></a>未來的工作

元件功能和介面可協助提供各種案例和基礎技術的一般一致性和強大支援。  在那之前，請選擇符合您要在應用程式中達成之案例的最佳路徑。

不同的案例或想要使用不同的技術/服務？ 請在此頁面底部的對應存放庫中，提供意見反應作為 GitHub 問題，或在[HoloDevelopers 的閒置時間](https://holodevelopers.slack.com/)內觸及。

## <a name="see-also"></a>另請參閱

* [Azure Spatial Anchors](/azure/spatial-anchors)
* [DirectX 中的共用空間錨點](shared-spatial-anchors-in-directx.md)
* [Unity 中的共用體驗](../unity/shared-experiences-in-unity.md)
* [觀眾檢視](spectator-view.md)