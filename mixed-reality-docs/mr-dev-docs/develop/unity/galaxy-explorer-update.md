---
title: 進行 HoloLens 2 的 Galaxy Explorer
description: 深入瞭解我們的小組如何更新 GitHub 上 HoloLens 2 的 Galaxy Explorer 開放原始碼專案。
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy explorer、案例研究、專案、範例、MRTK、混合現實工具組、Unity、範例應用程式、範例應用程式、開放原始碼、Microsoft Store、HoloLens、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: c3d9c6da13446816f3fd75f83e5a9088661c9604ef4d86ea805202f538d395b5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200464"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>進行 HoloLens 2 的 Galaxy Explorer

![新的 Galaxy Explorer 標誌](../images/GalaxyExplorer2.jpg)


歡迎使用 HoloLens 2 應用程式更新的 Galaxy Explorer！ [Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "星系探險")最初是以開放原始碼應用程式的形式開發，可透過共用您的想法方案，HoloLens (第一代) ，也是許多人的第一個混合現實體驗。 現在我們要更新它，以獲得[HoloLens 2 的全新且令人興奮的功能](https://www.microsoft.com/hololens/hardware)。

作為其中一個 [Microsoft Mixed Reality 工作室](galaxy-explorer-update.md#mixed-reality-studios)，我們通常會開發商業級的解決方案，並在整個創意和開發程式中開發 & 的目標平臺測試。 我們會使用登機的架構和 (工具來此專案，例如 [MRTK](mrtk-getting-started.md)) ，因為它們變成可供我們和社區使用，而我們想要讓您帶著。

就像原始的 Galaxy Explorer 一樣，[我們的小組](galaxy-explorer-update.md#meet-the-team)也會[開放 GitHub 的專案](https://github.com/Microsoft/GalaxyExplorer)，以確保該社區具有完整的存取權。 我們也將在此記錄我們的旅程，以完整的透明說明如何從 MRTK v1 移植到 MRTK v2、如何增強 HoloLens 2 中可用的新功能，以及確保 Galaxy Explorer 保持多平臺的體驗。 無論您是在 HoloLens 上 (第一代) 、HoloLens 2、Windows Mixed Reality 耳機或 Windows 10 桌上型電腦上觀看 Galaxy Explorer，我們都想要確定您已盡可能地享受旅程。

此頁面將會隨著我們在專案中的進展而擴大，並提供更詳細的文章、程式碼、設計成品和其他 MRTK 檔的連結，以提供您 insider 的專案查看。

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>從 HoloLens 2 的 Microsoft Store 下載應用程式
如果您有 HoloLens 2 的裝置，您可以直接在裝置中下載並安裝應用程式。

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>考慮互動

作為創意工作室，我們 ecstatic 了將 Galaxy Explorer 移植到 HoloLens 2 的許可權。 我們從一開始就知道，我們希望體驗成為新裝置的一小部分，並示範混合的現實能力只受到夢想的限制。

HoloLens 2 可讓使用者以自然的方式來觸控、抓住和移動全息影像，它們的回應方式很類似真正的物件。 完全表達的手模型很棒，因為它可讓使用者進行自然的操作。 例如，每個人都以稍微不同的方式來挑選杯，而不是強制執行這項工作，HoloLens 2 可讓您以自己的方式進行。

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

這是第一代 HoloLens 裝置上，以以點為基礎之介面的重大變更。 使用者現在可以「關閉」和「個人」，而不是從距離與全像全像之間的互動。 當您將現有的經驗移植到 HoloLens 2 或規劃新的體驗時，請務必讓自己熟悉全像投影的直接操作。

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>直接操作與空間的大量距離

這是神奇的體驗，可讓您抓住全球，並將其放在您手中。 這種方法的挑戰是日光系統的大小–是很大的！ 使用者需要四處移動空間，以接近每個行星的互動。

為了讓使用者能與更遠的物件互動，MRTK 提供了從使用者的手中走出的手片，作為手的延伸。 環圈圖的游標會附加至光線的結尾，以指出光線與目標物件相交的位置。 然後，游標所在的物件就能從手部接收手勢命令。 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

在原始版本的 Galaxy Explorer 中，使用者會以行星游標為地球，然後按下滑鼠來更接近。 將體驗移植到 HoloLens 2 的最簡單方式，就是採取這種行為，並使用手光線來選取行星。 雖然這是正常運作的，但仍會讓我們更有希望。

### <a name="back-to-the-drawing-board"></a>從頭再來

我們一起構思可在現有的互動之上建立哪些內容。 思考方式是：雖然 HoloLens 2 可讓使用者以自然、實際的方式與全像影像互動，但不是真正的定義。 只要對使用者進行互動合理，就不會有實際物件的互動，而是可以達成此目的。

我們探索的一個概念是以 telekinesis 為基礎，也就是處理物件的能力。 通常會出現在超級主圖的影片中，一人會與他們的想法聯繫，並將物件撥到其手中。 我們將更深入地探討此概念，並介紹概念如何運作的快速草圖。

![強制抓取互動的概念](images/ge-update-interactions-concept-force-grab.png)

使用者會將手中的光線指向行星，以提供目標意見反應。 當使用者接著擴充他們的手中，就會由神奇強制將地球拉往使用者，直到它夠近才能抓取。 因此，我們的互動名稱：強制抓取。 當使用者以其手中的手離開全球時，它會再次回到其軌跡。

### <a name="force-grab-prototyping"></a>強制抓取原型設計

接著，我們建立了多個原型來測試概念：互動的整體外觀為何？ 呼叫的物件是否應該在使用者之前停止，或繼續進行，直到放置為止？ 呼叫的物件是否會在呼叫時變更大小或調整？

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>在應用程式中執行強制抓取

當我們嘗試在行星上取得強制抓取時，我們發現我們必須變更日光系統的規模。 這表示，系統很難讓使用者瞭解和流覽不清楚、中型的日光系統標記法。 不過，小尺寸表示讓某些行星變得太小而無法輕易選取。 如此一來，行星的大小和日光物體之間的間距，設計為在中型房間內感覺舒適，同時維持相對精確度。

在我們的開發短期衝刺的後續階段中，我們很幸運能擁有內部的 MSFT 混合現實專家，因此我們可以將他們的輸入做為專家的測試人員，並在強制抓取互動上進行快速的反覆運算。

![Jenny Kam 測試 Galaxy Explorer 的預覽組建](images/ge-update-user-testing.png)

圖： Jenny Kam 是資深設計負責人，測試 Galaxy Explorer 進行中的工作。

### <a name="adding-affordances-for-targeting"></a>新增目標的 affordances

當我們在 HoloLens 2 上實驗時，我們發現即使新的互動是自然且直覺的，全像是：沒有權數或 tactile sensations。 由於全息全像是在與物件互動時，人類用來接收的自然意見反應，因此我們需要建立它們。

我們考慮到使用者會針對互動的各種階段提供視覺和音訊的意見反應，而且因為強制抓取機制是與 Galaxy Explorer 互動的核心，所以我們進行了許多反覆運算。 其目標是要針對互動的每個階段，找出音訊和視覺效果的正確平衡：將焦點放在想要的物件上、將它呼叫給使用者，然後再放開。 我們所學到的內容是，需要更多的音訊和視覺效果來強化互動，而不是我們用來 HoloLens (第一代) 。

![行星上的視覺 affordances](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>新增 affordances 來強制抓取
 
一旦有了基本的強制抓取機制搭配音訊和 visual affordances，我們就看過如何讓選取行星更容易使用。 有兩個主要的原因要解決：因為日光系統是3D 移動介面，所以使用者會增加複雜性來瞭解如何以一致的方式鎖定物件。 這是因為在選取物件時，光線很快就會變得更複雜，讓行星迅速移往使用者。

我們採用三個面向的解決方案來達到這個效益。 第一個是相當直覺：讓選取範圍變慢，讓行星以更自然的步調來處理使用者。 調整速度之後，我們必須重新流覽音訊和視覺 affordances，將音訊意見反應新增至使用者所追蹤的地球。

解決方案的第二個部分是讓整個強制抓取互動的視覺效果成為有形。 我們視覺化了一個粗線，在手邊的光線連接之後移往目標物件，然後將物件帶回使用者，就像套索一樣。 

![用於強制抓取的視覺效果「套索」 affordances](images/ge-update-lasso-affordances.png)

最後，我們將日光系統的規模優化，讓行星夠大，讓使用者的注視和手的光線成為目標。 

這三項增強功能可讓使用者做出精確的選擇，以直覺的方式呼叫行星。 整體來說，最終的強制抓取效果在日光系統中是更沉浸且互動式的體驗。

## <a name="spotlight-on-jupiter"></a>在 Jupiter 上聚焦

建立銀河方式的日光主體是 humbling 的體驗。 尤其是，Jupiter 的獨特特性讓它耶。 這是最大且最彩色的天然氣巨人，且包含的品質高於所有其他行星組合。 其廣泛的 turbulence 和雲端動態 mesmerizing 區，可 prefect 特別的藝術。

### <a name="geometry-and-meshes"></a>幾何和網格

作為天然氣大型，Jupiter 的外部 shell 包含 gaseous 層。 其快速旋轉速度、內部熱度交換和 Coriolis 的組合，可建立彩色的圖層和串流，形成 swirling 的雲端皮帶和 vortices。 捕捉這個複雜的美式，是建立太陽系的關鍵。

使用視覺化的技術（例如流暢模擬）和具有預先計算串流的動畫紋理都不會有問題。 將這項功能與其他同時發生的其他專案一起模擬所需的運算能力，會對效能造成重大不利的影響。 

![Jupiter 物件總覽](images/ge-update-jupiter-shells-complete.jpg)

下一種方法是「冒煙和鏡像」的解決方案，其中包括覆迭透明材質圖層，每個都解決了面向移動的特定層面，並在旋轉網格的組合上進行編譯。

在下圖中，您可以在左側看到內部 shell。 此階層圖層提供了組合的背景，以防止組成雲端的多層之間的任何小間距。 由於圖層的旋轉速度很慢，因此它也會作為視覺化緩衝區來提供更快速的移動區間，以協助在各層中建立 visual unity。

將此錨點設定為模型之後，移動的雲端層接著會投射在下方所示的中間和右側網格上。

![使用分隔 shell 的 Jupiter 物件總覽](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>紋理

現有的材質分為三個部分的材質塔：第三部主機具有間距的 motionless 層，可提供視差效果，中間區段包含快速移動的外部資料流，而下半部則包含緩慢旋轉的內部基底圖層。

特性良好的紅點也會分成不同的移動元件，然後插入材質的其他隱藏區域中。 這些元件可以被視為下圖中間區段中的 red toned 斑點予。

因為每個波段都有特定的方向和速度，所以紋理會個別套用至每個網格。 然後，網格會有一個通用的中心點和一個資料點，讓您可以 concentrically 整個表面的動畫。

![Jupiter 紋理總覽](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>旋轉和材質行為

一旦設定了 Jupiter 的視覺效果組合之後，我們必須確定已正確地計算並套用旋轉和軌跡速度。 針對 Jupiter 完成完整輪替需要大約9小時的時間。 這是因差異旋轉而產生的定義。 因此，會將赤道幾內亞資料流程設定為「主要串流」，並採用3600的框架進行完整的旋轉。 每一層都需要有旋轉速度作為3600，才能符合其初始位置，例如，600、900、1200、1800等等。

![Jupiter shell 紋理](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>很棒的紅點

個別輪替的串流提供良好的視覺效果，但在觀察到接近範圍時，就不會有詳細的資料。

最引人注目的部分是 Jupiter 的絕佳紅色點，因此我們特別建立了一組網格和紋理來展示。
 
我們使用的機制與 Jupiter 的波段類似：一組旋轉零件是由彼此組成，同時也會在其「主要圖層」下分組，以確保不論 rest 移動的速度有多快，都能保持在相同位置。

當網格已設定並準備就緒時，會套用不同層的 stormy vortex，然後每個光碟都會個別進行動畫處理，而其餘部分則會以最快的速度移動，而 rest 會逐漸降低。

![Jupiter 絕佳的 Red 點網格](images/ge-update-great-red-spot-mesh.jpg)

組合也會與每個其他網格具有相同的 pivot，同時也會將其從原始 y 軸的傾斜 (！ ) ，以在動畫中自由旋轉。 3600畫面格是基本費率，每個圖層都有這一段迴圈的因素。

![Jupiter 絕佳的 Red 專色材質](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>直接在 Unity 中取得

在 Unity 中執行這項作業時，有幾個重要的事項要牢記在心。

在處理大型透明層的集合時，Unity 很容易混淆。 解決方法是複製每個網格的材質材質，並將遞增的轉譯佇列值從內部逐漸逐漸套用到每個材質的外部。

結果是內部 shell 的轉譯佇列值為 3000 (預設) ，靜態 red toned outer 的值為3005，而 fast 白色外部雲端則為3010。 很棒的紅點 (從內部到外部層) ，在此模型中已完成值為3025。

![Jupiter 最終物件](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>最後的修飾

一開始就已設定紋理的 Jupiter 層，其證明不足以執行。

原始的全球標準著色器及其所有的變化，都會透過腳本 SunLightReceiver （MRTK 標準著色器不支援）接收其光源資訊。

單純地交換著色器並不是一種解決方案，因為地球標準著色器不支援使用投影片的材質地圖。 我們已編輯此著色器，讓 Jupiter 組建如預期運作。

最後，您必須將來源 Blend 設定為10，並將目的地 Blend 設定為5，以設定 Alpha 融合。

![Jupiter Unity 屬性](images/ge-update-jupiter-unity-render-queue.jpg)

您可以在 [Galaxy Explorer] 中看到 Jupiter 的最終呈現！

## <a name="meet-the-team"></a>認識團隊 

我們的混合現實 studio 小組是由設計人員、3D 演出者、UX 專家、開發人員、程式經理和 studio 標頭所組成。 我們從全球各地 hail：比利時、加拿大、德國、以色列、日本、英國和美國。 我們是來自各種背景的豐富團隊：遊戲-傳統與獨立製作、數位行銷、醫療保健和科學。

我們很高興能為 HoloLens 2 建立 Galaxy Explorer，並更新 HoloLens (第一代) 、VR 和桌上出版。 

![Galaxy Explorer 小組](images/ge-update-team-image.png)

從左至右： Artemis Tsouflidou (Developer) 、Angie Teickner (Visual Designer) 、David Janer (UX 設計工具) 、劉娜 Garrett (交付 & 生產潛在客戶) 、Yasushi Zonno (創意領導人) 、Eline Ledent (開發人員) ，以及 Ben Turner (Sr-iov) 。
從左至右： Amit Rojtblat (技術演出者) 、聖馬丁 Wettig (3D 演出者) 和 Dirk Songuer (Studio Head) 。
未精選： Tim Gerken (技術負責人) 和 Oscar Salandin (視覺化設計工具) 。

## <a name="additional-information"></a>其他資訊

### <a name="mixed-reality-studios"></a>混合現實工作室

Microsoft Mixed Reality Studio 小組（位於美洲、歐洲和 Asia-Pacific）是使用者體驗設計、全像電腦運算、AR/VR 技術以及3D 開發的專家;包括建立3D 資產、DirectX、Unity 和 Unreal。 我們會協助您構想所需的未來、設計、建立和提供解決方案，同時讓客戶能夠在其組織之間創造可測量的影響。 工作室與超過22000的 Microsoft 服務專業人員密切合作，以進行企業應用程式整合、採用、操作及支援。