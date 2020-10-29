---
title: MR 分享 250-HoloLens 和沉浸式耳機
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio、HoloLens 和 Windows Mixed Reality 耳機來瞭解在混合現實裝置之間共用全像投影的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、沉浸式、移動控制器、共用、xbox 控制器、網路、跨裝置
ms.openlocfilehash: a980441ee73cd8f45afff446d9315eaf08549575
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680085"
---
# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR Sharing 250：HoloLens 和沉浸式頭戴裝置

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](../mr-learning-base-01.md)。

利用通用 Windows 平臺 (UWP) 的彈性，您可以輕鬆地建立跨多個裝置的應用程式。 有了這種彈性，我們可以建立利用每部裝置優勢的體驗。 本教學課程將涵蓋在 HoloLens 和 Windows Mixed Reality 沉浸式耳機上執行的基本共用體驗。 這項內容最初是在華盛頓州西雅圖的 Microsoft Build 2017 會議中提供。

**在此教學課程中，我們將：**

* 使用 UNET 設定網路。
* 跨混合現實裝置共用全像影像。
* 根據所使用的混合現實裝置，建立不同的應用程式視圖。
* 建立共用體驗，讓 HoloLens 使用者透過一些簡單的謎題引導沉浸式耳機使用者。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Sharing 250：HoloLens 和沉浸式頭戴裝置</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>Prerequisites

* 具有 [必要開發工具](../develop/install-the-tools.md) 並 [設定為支援 Windows Mixed Reality 沉浸式耳機](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的 Windows 10 PC。
* 適用于您電腦的 Xbox 控制器。
* 至少一個 HoloLens 裝置和一個沉浸式耳機。
* 允許 UDP 廣播進行探索的網路。

### <a name="project-files"></a>專案檔

* 下載專案 [所需的](https://github.com/Microsoft/MixedReality250/archive/master.zip) 檔案。 將檔案解壓縮至容易記住的位置。
* 此專案需要 [Windows Mixed Reality 支援的 Unity 建議版本](../develop/install-the-tools.md)。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/MixedReality250)取得。

## <a name="chapter-1---holo-world"></a>第1章-Hololens World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>目標

請確定開發環境已準備好使用簡單的專案。

### <a name="what-we-will-build"></a>我們將建立的內容

一種應用程式，會在 HoloLens 或 Windows Mixed Reality 沉浸式耳機上顯示全像投影。

### <a name="steps"></a>步驟

* 開啟 Unity。
    * 選取 [開啟]。
    * 流覽至您解壓縮專案檔的位置。
    * 按一下 [選擇資料夾]  。
    * *Unity 需要一些時間才會第一次處理專案。*
* 檢查 Unity 中是否已啟用 Mixed Reality。
    * 開啟 [組建設定] 對話方塊， ( **Control + Shift + B** 或 **File > 組建設定 ...** ]) 。
    * 選取 **通用 Windows 平臺** 然後按一下 [ **切換平臺** ]。
    * 選取 [ **編輯>播放機設定** ]。
    * 在右側的 [偵測 **器** ] 面板中，展開 [ **XR 設定** ]。
    * 勾選 [ **支援虛擬實境** ] 方塊。
    * *Windows Mixed Reality 應為虛擬實境 SDK。*
* 建立場景。
    * 在階層中， **以滑鼠右鍵** 按一下 [ **主要攝影機** ] 選取 [ **刪除** ]。
    * 從 **HoloToolkit > 輸入 > Prefabs** 將 **MixedRealityCameraParent** 拖曳至 **階層。**
* 將全像影像新增至場景
    * 從 **AppPrefabs** 將 **Skybox** 拖曳至 **場景視圖** 。
    * 從 **AppPrefabs** 將 **管理員** 拖曳至 **階層。**
    * 從 **AppPrefabs** 將 **島** 拖曳至 **階層。**
* 儲存並建立
    * 儲存 ( **Control + S** 或 **File > 儲存場景** ) 
    * 因為這是新的場景，所以您需要為它命名。 名稱並不重要，但我們使用 SharedMixedReality。
* 匯出至 Visual Studio
    * 開啟 [組建] 功能表 ( **Control + Shift + B** 或 **File > 組建設定** ) 
    * 按一下 [ **新增開啟的場景]。**
    * 檢查 **Unity c # 專案**
    * 按一下 [建置]  。
    * 在出現的 [檔案瀏覽器] 視窗中，建立名為 **App** 的新資料夾。
    * 按一下 **應用程式** 資料夾。
    * 按下 [ **選取資料夾]。**
    * **等候組建完成**
    * 在出現的 [檔案瀏覽器] 視窗中，流覽至 **應用程式** 資料夾。
    * 按兩下 **SharedMixedReality .sln** 以啟動 Visual Studio
* 從 Visual Studio 建立
    * 使用頂端工具列變更目標為 **Release** 和 **x86** 。
    * 按一下 [ **本機電腦** ] 旁邊的箭號，然後選取要部署到 HoloLens 的 **裝置**
    * 按一下 [ **裝置** ] 旁的箭號，然後選取 [ **本機電腦** ] 以部署混合現實耳機。
    * 按一下 [ **Debug->啟動但不調試** ] 或 [ **Control + F5** ] 以啟動應用程式。

### <a name="digging-into-the-code"></a>深入探討至程式碼

在 [專案] 面板中，流覽至 [ **Assets\HoloToolkit\Input\Scripts\Utilities** ]，然後按兩下 [ **MixedRealityCameraManager.cs** ] 將它開啟。

**總覽：** MixedRealityCameraManager.cs 是一個簡單的腳本，可根據裝置來調整品質層級和背景設定。 這裡的金鑰是 HolographicSettings IsDisplayOpaque，可讓腳本偵測裝置是否為 HoloLens (IsDisplayOpaque 會傳回 false) 或沉浸式耳機 (IsDisplayOpaque 會傳回 true) 。

### <a name="enjoy-your-progress"></a>享受您的進度

此時，應用程式只會轉譯一個全像影像。 我們稍後會將互動新增至影像。 這兩個裝置都會轉譯相同的全像投影。 沉浸式耳機也會呈現藍色天空和雲端背景。

## <a name="chapter-2---interaction"></a>第2章-互動

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>目標

示範如何處理 Windows Mixed Reality 應用程式的輸入。

### <a name="what-we-will-build"></a>我們將建立的內容

以第1章的應用程式為基礎，我們將新增功能，讓使用者能夠挑選全像，然後將它放在 HoloLens 的真實世界表面，或放在沉浸式耳機的虛擬資料表中。

**輸入複習：** 在 HoloLens 上，選取手勢是 **點擊** 。 在沉浸式耳機上，我們將使用 Xbox 控制器上 **的按鈕。** 如需詳細資訊，請參閱 [互動模型的總覽](../design/interaction-fundamentals.md)。

### <a name="steps"></a>步驟

* 新增輸入管理員
    * 從 **HoloToolkit > 輸入 > Prefabs** 將 **InputManager** 拖曳 **到階層** 作為 **經理** 的子系。
    * 從 **HoloToolkit > 輸入 > Prefabs > 資料指標** 將 **游標** 拖曳至 **階層。**
* 新增空間對應
    * 從 **HoloToolkit > SpatialMapping > Prefabs** 將 **SpatialMapping** 拖曳至 **階層。**
* 新增虛擬 Playspace
    * 在 **階層** 中展開 **MixedRealityCameraParent** 選取 **界限**
    * 在 [偵測 **器** ] 面板中，核取 [啟用 **界限** ] 核取方塊
    * 從 **AppPrefabs** 將 **VRRoom** 拖曳至 **階層。**
* 新增 WorldAnchorManager
    * 在 **[階層] 中選取** [ **管理員** ]。
    * 在 [偵測 **器** ] 中，按一下 [ **新增元件** ]。
    * 輸入 **World 錨點管理員** 。
    * 選取 [ **世界錨點管理員** ] 將它加入。
* 將 TapToPlace 新增至島
    * 在 **[階層] 中，** 展開 [ **島** ]。
    * 選取 [ **MixedRealityLand** ]。
    * 在 [偵測 **器** ] 中，按一下 [ **新增元件** ]。
    * 輸入點一下 **以放置** 並選取它。
    * 選取 **[在點處放置父系** ]。
    * 將 **放置位移** 設定為 **(0、0.1、0)** 。
* 儲存並建立成先前的

### <a name="digging-into-the-code"></a>深入探討至程式碼

**腳本 1-GamepadInput.cs**

在 [專案] 面板中，流覽至 [ **Assets\HoloToolkit\Input\Scripts\InputSources** ]，然後按兩下 [ **GamepadInput.cs** ] 將它開啟。 在 [專案] 面板中的相同路徑中，也按兩下 [ **InteractionSourceInputSource.cs** ]。

請注意，這兩個腳本都有一個通用的基類 BaseInputSource。

BaseInputSource 會保留對 InputManager 的參考，讓腳本能夠觸發事件。 在此情況下，InputClicked 事件是相關的。 當我們進入腳本2時，請務必記住這一點 TapToPlace。 在 GamePadInput 的案例中，我們會輪詢控制器上要按下的按鈕，然後引發 InputClicked 事件。 在 InteractionSourceInputSource 的案例中，我們會引發 InputClicked 事件以回應 TappedEvent。

**腳本 2-TapToPlace.cs**

在 [專案] 面板中，流覽至 [ **Assets\HoloToolkit\SpatialMapping\Scripts** ]，然後按兩下 [ **TapToPlace.cs** ] 將它開啟。

許多開發人員想要在建立全像的應用程式時執行的第一件事，就是移動帶有手勢輸入的全息影像 因此，我們已 endeavored 徹底批註此腳本。 在本教學課程中，有一些值得注意的事項。

首先，請注意，TapToPlace 會執行 IInputClickHandler。 IInputClickHandler 會公開函式，這些函式會處理 GamePadInput.cs 或 InteractionSourceInputSource.cs 所引發的 InputClicked 事件。 當 BaseInputSource 偵測到 click，而具有 TapToPlace 的物件處於焦點時，就會呼叫 OnInputClicked。 Airtapping 在 HoloLens 上或按下 Xbox 控制器上的按鈕將會觸發事件。

其次是在 update 中執行程式碼，以查看是否正在查看介面，因此我們可以將遊戲物件放在介面上，例如資料表。 沉浸式耳機沒有實際表面的概念，因此代表資料表 top (隆隆 > TableThingy > Cube) 的物件已標記 SpatialMapping 實體層，因此更新中的光線轉換將會與虛擬資料表上的資料衝突。

### <a name="enjoy-your-progress"></a>享受您的進度

這次您可以選取島來移動它。 在 HoloLens 上，您可以將島移至真實表面。 在沉浸式耳機中，您可以將島移至我們所加入的虛擬資料表。

## <a name="chapter-3---sharing"></a>第3章-共用

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>目標

確定已正確設定網路，並詳細說明如何在裝置之間共用空間錨點。

### <a name="what-we-will-build"></a>我們將建立的內容

我們會將專案轉換成多人的專案。 我們會將 UI 和邏輯新增至主機或加入會話。 HoloLens 使用者會在與雲端一起的會話中看到彼此，而且沉浸式耳機使用者在錨點附近有雲端。 沉浸式耳機中的使用者會看到 HoloLens 使用者相對於場景的原點。 HoloLens 使用者將會在同一處看到島的全息圖。 要注意的是，沉浸式耳機中的使用者不會在這一章的島上，而是與 HoloLens 一樣的行為，而且會有鳥的鳥觀點。

### <a name="steps"></a>步驟

* 移除島和 VRRoom
    * 在 **階層中，以** 滑鼠右鍵按一下 [ **島** ] 選取 [ **刪除** ]
    * 在 **階層中，以** 滑鼠右鍵按一下 **VRRoom** 選取 [ **刪除** ]
* 新增 Usland
    * 從 **AppPrefabs** 將 **Usland** 拖曳至 **階層。**
* 從 **AppPrefabs** 將下列各項拖曳至 **階層：**
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* 儲存並建立成先前的

### <a name="digging-into-the-code"></a>深入探討至程式碼

在 [專案] 面板中，流覽至 [ **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** ]，然後按兩下 [ **UnetAnchorManager.cs** ]。 一個 HoloLens 與另一個 HoloLens 共用追蹤資訊的能力，使得這兩個裝置都可以共用相同的空間，幾乎神奇。 當有兩個以上的人員可以使用相同的數位資料共同作業時，混合現實的威力就會保持運作。

這段腳本中有幾點要指出：

在 start 函數中，請注意 **IsDisplayOpaque** 的檢查。 在此情況下，我們會假設已建立錨點。 這是因為沉浸式耳機未公開匯入或匯出錨點的方式。 但是，如果我們是在 HoloLens 上執行，此腳本會在裝置之間執行共用錨點。 啟動會話的裝置將會建立用於匯出的錨點。 加入會話的裝置將會從啟動會話的裝置要求錨點。

**出口：**

當使用者建立會話時，NetworkDiscoveryWithAnchors 會呼叫 UNETAnchorManagers CreateAnchor 函數。 讓我們遵循 CreateAnchor flow。

我們一開始會先進行一些維護，並清除我們針對先前錨點收集到的任何資料。 然後檢查是否有要載入的快取錨點。 錨定資料的長度通常是5到 20 MB，因此重複使用快取的錨點可以節省透過網路傳輸所需的資料量。 稍後我們會看到其運作方式。 即使我們要重複使用錨點，但如果新的用戶端聯結沒有錨點，就需要讓錨點資料備妥。

說到準備錨點資料，WorldAnchorTransferBatch 類別會公開準備錨點資料以傳送至另一個裝置或應用程式的功能，以及匯入錨點資料的功能。 由於我們是在匯出路徑上，因此我們會將錨點新增至 WorldAnchorTransferBatch，並呼叫 ExportAsync 函式。 然後，ExportAsync 會在產生要匯出的資料時呼叫 WriteBuffer 回呼。 當匯出所有資料時，會呼叫 ExportComplete。 在 WriteBuffer 中，我們會將資料區塊新增至我們保留的匯出清單。 在 ExportComplete 中，我們會將清單轉換成陣列。 此外也會設定 AnchorName 變數，以觸發其他裝置要求錨點（如果沒有的話）。

在某些情況下，錨點將不會匯出或建立少量的資料，我們會再試一次。 我們在這裡直接呼叫 CreateAnchor。

匯出路徑中的最後一個函數是 AnchorFoundRemotely。 當另一部裝置找到錨點時，該裝置將會告訴主機，而主機會使用它作為信號，讓錨點成為「良好錨點」並可進行快取。

**進口：**

當 HoloLens 加入會話時，它需要匯入錨點。 在 UNETAnchorManager 的 Update 函數中，會輪詢 AnchorName。 當錨點名稱變更時，匯入程式就會開始。 首先，我們會嘗試從本機錨點存放區載入具有指定名稱的錨點。 如果已經有，我們可以使用它，而不需要再次下載資料。 如果沒有，則會呼叫 WaitForAnchor，以起始下載。

當下載完成時，會呼叫 NetworkTransmitter_dataReadyEvent。 這會通知更新迴圈使用下載的資料來呼叫 ImportAsync。 當匯入程式完成時，ImportAsync 會呼叫 ImportComplete。 如果匯入成功，錨點將會儲存在本機播放程式存放區中。 PlayerController.cs 實際上會呼叫 AnchorFoundRemotely，讓主機知道已建立良好的錨點。

### <a name="enjoy-your-progress"></a>享受您的進度

這次具有 HoloLens 的使用者將使用 UI 中的 [ **啟動會話** ] 按鈕來裝載會話。 其他使用者（在 HoloLens 或沉浸式耳機上）會選取會話，然後在 UI 中選取 [ **加入會話** ] 按鈕。 如果您有多人使用 HoloLens 裝置，他們的標頭將會有 red cloud。 每個沉浸式耳機也會有一個藍色的雲端，但藍色的雲端不會在耳機上方，因為耳機不會嘗試尋找與 HoloLens 裝置相同的全局座標空間。

專案中的這個點是包含的共用應用程式;它並不會有太大的作用，而且可以作為基準。 在下一章中，我們將開始打造體驗，讓人們享受體驗。 若要取得有關共用體驗設計的進一步指引，請移至這裡。

## <a name="chapter-4---immersion-and-teleporting"></a>第4章-深度和 teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>目標

滿足每種混合現實裝置的體驗。

### <a name="what-we-will-build"></a>我們將建立的內容

我們將會更新應用程式，將沉浸式耳機使用者放在島上（具有沉浸式視圖）。 HoloLens 使用者仍會有此島的鳥眼睛。 每種裝置類型的使用者都可以看到出現在世界中的其他使用者。 比方說，沉浸式耳機使用者可以看到其他虛擬人偶在島上的其他路徑，並將 HoloLens 使用者視為大型雲端。 如果 HoloLens 使用者正在查看島，則沉浸式耳機使用者也會看到 HoloLens 使用者的注視光線游標。 HoloLens 使用者會看到島上的圖片，代表每個沉浸式耳機使用者。

**已更新沉浸式裝置的輸入：**

* Xbox 控制器上的左緩衝和右緩衝按鈕會旋轉玩家
* 按住 Xbox 控制器上的 Y 按鈕將會啟用 [傳送](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 游標。 當您放開 Y 按鈕時，如果游標具有旋轉箭號指標，則會傳送至游標的位置。

### <a name="steps"></a>步驟

* 將 MixedRealityTeleport 新增至 MixedRealityCameraParent
    * 在 **[階層] 中選取** [ **Usland** ]。
    * 在 [偵測 **器** ] 中，啟用 **層級控制** 。
    * 在 **[階層] 中選取** [ **MixedRealityCameraParent** ]。
    * 在 [偵測 **器** ] 中，按一下 [ **新增元件** ]。
    * 輸入 **Mixed Reality 傳送** ，然後選取它。

### <a name="digging-into-the-code"></a>深入探討至程式碼

沉浸式耳機使用者將使用纜線行動網卡到他們的電腦，但我們的島大於纜線的長度。 為了彌補這一點，我們需要能夠在使用者的動作之外獨立移動相機。 請參閱 [ [緩和] 頁面](../design/comfort.md) ，以取得設計混合現實應用程式 (特定的自我運動和 locomotion) 的詳細資訊。

為了說明此程式，定義兩個詞彙將會很有説明。 首先， **dolly** 會是與使用者分開移動相機的物件。 **Dolly** 的子遊戲物件將會是 **主相機** 。 主要相機會附加至使用者的標頭。

在 [專案] 面板中，流覽至 [ **Assets\AppPrefabs\Support\Scripts\GameLogic** ]，然後按兩下 [ **MixedRealityTeleport.cs** ]。

MixedRealityTeleport 有兩個作業。 首先，它會使用緩衝器來處理旋轉。 在 update 函數中，我們會在 LeftBumper 和 RightBumper 上輪詢 ' ButtonUp '。 GetButtonUp 只會在第一個畫面格上傳回 true。 如果已引發任一個按鈕，則我們知道使用者需要輪替。

當我們輪替時，請使用稱為「淡化控制項」的簡單腳本，淡出並淡出。 這麼做是為了防止使用者看見可能導致不適感的非自然移動。 淡入和淡出效果相當簡單。 在 **主要攝影機** 前面有黑色的間隙。 當您淡出時，會將 Alpha 值從0轉換成1。 這會逐漸產生四的黑色圖元來呈現和遮蔽背後的任何專案。 當您淡出時，我們會將 Alpha 值轉換回零。

當我們計算旋轉時，請注意我們會旋轉 **dolly** ，但會計算 **主要攝影機** 的旋轉。 這點很重要，因為 **主要相機** 離0、0、0愈遠，dolly 的旋轉就會從使用者的觀點來看，不精確。 事實上，如果您沒有繞著相機位置旋轉，則使用者會在 **dolly** 前後移動弧形，而不是旋轉。

MixedRealityTeleport 的第二個工作是處理 **dolly** 的移動。 這是在 SetWorldPosition 中完成。 SetWorldPosition 會採用所需的世界位置，也就是使用者想要 percieve 占的位置。 我們需要將 **dolly** 放在該位置減去 **主要攝影機** 的本機位置，因為該位移將會新增至每個畫面格。

第二個腳本會呼叫 SetWorldPosition。 讓我們來看看那個腳本。 在 [專案] 面板中，流覽至 [ **Assets\AppPrefabs\Support\Scripts\GameLogic** ]，然後按兩下 [ **TeleportScript.cs** ]。

此腳本比 MixedRealityTeleport 更簡單。 腳本正在檢查 Xbox 控制器上的 Y 按鈕是否已關閉。 當按鈕關閉時，會轉譯傳送游標，而且腳本會將光線從使用者的注視位置轉換出來。 如果該光線與較多或較少指標的表面衝突，則會將介面視為適合用來傳送的介面，並且會啟用傳送游標上的動畫。 如果光線未與某個介面相較或更低，則會停用游標上的動畫。 當您放開 Y 按鈕，且光線的計算點是有效的位置時，腳本會使用與光線交集的位置來呼叫 SetWorldPosition。

### <a name="enjoy-your-progress"></a>享受您的進度

這次您將需要尋找 friend。

同樣地，具有 HoloLens 的使用者將會裝載一個會話。 其他使用者將加入會話。 應用程式會將前三位使用者從島的三個路徑中的其中一個上的沉浸式耳機加入。 您可以隨時流覽這一節中的孤島。

要注意的詳細資料：

1. 您可以看到雲端中的臉部，以協助可以沉浸使用者查看 HoloLens 使用者的期望方向。
2. 島上的虛擬人偶具有旋轉的 necks。 他們不會遵循使用者正在做的事， (我們沒有這項資訊) 但可提供絕佳的體驗。
3. 如果 HoloLens 使用者正在查看島，可以沉浸使用者可以看到他們的游標。
4. 代表 HoloLens 使用者轉換陰影的雲端。

## <a name="chapter-5---finale"></a>第5章-Finale

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>目標

建立兩個裝置類型之間的共同作業互動體驗。

### <a name="what-we-will-build"></a>我們將建立的內容

以第4章為基礎，當具有沉浸式耳機的使用者接近島上的拼圖時，HoloLens 使用者將會取得工具提示，其中包含謎題的線索。 一旦所有的沉浸式耳機使用者都超過其謎題，並放到 rocket 室中的「就緒板」之後，rocket 就會啟動。

### <a name="steps"></a>步驟

* 在 **[階層] 中選取** [ **Usland** ]。
* 在 [ **檢查** ] 的 [ **層級控制** ] 中，勾選 [ **啟用** 共同作業]。

### <a name="digging-into-the-code"></a>深入探討至程式碼

現在讓我們看看 LevelControl.cs。 此腳本是遊戲邏輯的核心，可維持遊戲狀態。 由於這是使用 UNET 的多人遊戲，我們需要瞭解資料流程的運作方式，而且至少要有足夠的時間來修改本教學課程。 如需更完整的 UNET 總覽，請參閱 Unity 的檔。

在 [專案] 面板中，流覽至 [ **Assets\AppPrefabs\Support\Scripts\GameLogic** ]，然後按兩下 [ **LevelControl.cs** ]。

請讓我們瞭解沉浸式耳機如何表示已準備好開始 rocket。 Rocket 啟動準備工作的方式，是在對應到島上三個路徑的 bool 清單中設定三個 bool 的其中一個。 當指派給路徑的使用者位於 rocket 房間內棕色板的上方時，就會設定路徑的 bool。 好的，現在的詳細資料。

我們將從 Update ( # A1 函數開始。 您將會注意到有「功能提要」功能。 我們在開發過程中使用此功能來測試 rocket 的啟動和重設順序。 它無法在多使用者體驗中使用。 希望您旨在下列資訊的時間，您可以讓它正常運作。 在我們檢查看看是否有任何功能時，我們會檢查本機播放機是否可以沉浸。 我們希望專注于我們的目標。 在中，如果 (可以沉浸) 檢查，則會呼叫 CheckGoal 在 **EnableCollaboration** bool 後方隱藏。 這會對應到您在完成本章的步驟時所檢查的核取方塊。 在 EnableCollaboration 中，我們會看到 CheckGoal ( # A1 的呼叫。

CheckGoal 會進行一些數學運算，以查看是否有更多或更少的站在板上。 當我們在進行時，我們會將「抵達目標」記錄檔，然後呼叫「SendAtGoalMessage ( # A1」。 在 SendAtGoalMessage 中，我們稱之為 >playercontroller. SendAtGoal。 為了節省時間，以下是程式碼：

```cs
private void CmdSendAtGoal(int GoalIndex)
{
    levelState.SetGoalIndex(GoalIndex);
}
```

```cs
public void SendAtGoal(int GoalIndex)
{
    if (isLocalPlayer)
    {
        Debug.Log("sending at goal " + GoalIndex);
        CmdSendAtGoal(GoalIndex);
    }
}
```

請注意，SendAtGoalMessage 會呼叫 CmdSendAtGoal，其會呼叫 levelState SetGoalIndex，這會傳回 LevelControl.cs。 乍看之下，這似乎很奇怪。 為什麼不直接呼叫 SetGoalIndex，而不是透過 player 控制器來進行這種奇怪的路由？ 原因是我們符合資料模型 UNET 用來保持資料同步。為了避免作弊並使其失效，UNET 要求每個物件都有一個具有變更已同步變數之許可權的使用者。 此外，只有主控制項 (啟動會話) 的使用者可以直接變更資料。 如果使用者不是主機，但具有授權單位，則必須將「命令」傳送至將變更變數的主控制項。 依預設，主機具有所有物件的許可權，但衍生來代表使用者的物件除外。 在我們的案例中，此物件具有 >playercontroller 腳本。 有一種方法可以要求物件的授權單位，然後進行變更，但我們選擇利用播放程式控制器具有自我授權，並透過 player 控制器路由傳送命令的事實。

另一種方式是，當我們找到自己的目標時，玩家需要告訴主機，而主機會告訴大家其他人。

回到 LevelControl.cs 查看 SetGoalIndex。 在這裡，我們要設定 synclist (AtGoal) 中值的值。 請記住，我們會在主機的內容中進行這項作業。 類似于命令，RPC 是主機可發出的內容，會導致所有用戶端執行一些程式碼。 在這裡，我們稱之為「RpcCheckAllGoals」。 每個用戶端都會個別檢查是否已設定全部三個 AtGoals，如果是，則啟動 rocket。

### <a name="enjoy-your-progress"></a>享受您的進度

在上一章中，我們將依之前的方式啟動會話。 這次，當沉浸式耳機中的使用者到達其路徑上的「門」時，就會出現只有 HoloLens 使用者可以看到的工具提示。 HoloLens 使用者負責將這個線索傳達給沉浸式耳機中的使用者。 一旦每個頭像在火山內的對應棕色板上進行了 rocket，就會啟動空間。 場景會在60秒後重設，以便您可以再次進行。

## <a name="see-also"></a>另請參閱

* [MR Input 213：運動控制器](mixed-reality-213.md)
