---
title: 2. 初始化您的專案和第一個應用程式
description: 教學課程系列的第 2 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: e4fd7f69b3febec3997b13d7cb92579e9018e86cb3805b9a94dc76190affb34d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203879"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化您的專案和第一個應用程式

在第一個教學課程中，您將著手進行新的 Unreal 項目，並啟用 HoloLens 外掛程式、建立和亮顯層級，以及新增棋子。 您將對所有 3D 物件和材質使用預先製作的資產，因此無須擔心自行建立模型的問題。 在本教學課程結束時，您將會有一個可供混合實境使用的空白畫布。

> [!IMPORTANT]
> 請確定您擁有[開始使用](/windows/mixed-reality/unreal-uxt-ch1)頁面中的所有必要項目。

## <a name="objectives"></a>目標

* 設定 Unreal 專案以用於 HoloLens 開發
* 匯入資產和設定場景
* 使用藍圖建立動作項目和指令碼層級事件

## <a name="creating-a-new-unreal-project"></a>建立新的 Unreal 專案

您需要的第一個項目是供您使用的專案。 如果您是首次接觸的 Unreal 開發人員，則需要從 Epic Launcher [下載支援檔案](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。

1. 啟動 Unreal Engine

2. 在 [新增專案類別] 中選取 [遊戲]，然後按 [下一步]。 

![選取遊戲專案範本](images/unreal-uxt/2-gamestemplate.png)

3. 選取 **空白** 範本，然後按 [下一步]。 

![選取空白範本](images/unreal-uxt/2-template.PNG)

4. 將 [C++]、[可縮放 3D 或 2D]、[行動裝置/平板電腦] 及 [無起始內容] 設為您的 [專案設定]，然後選擇儲存位置並按一下 [建立專案]。 

> [!NOTE]
> 您必須選取 C++ 專案 (而非藍圖專案) 以建置 UX 工具外掛程式 (您稍後將在第 4 節設定此外掛程式)。

![初始專案設定](images/unreal-uxt/2-project-settings.PNG)

專案應該會自動在 Unreal 編輯器中開啟，這表示您已準備好進行下一節。

## <a name="enabling-required-plugins"></a>啟用必要的外掛程式

若要使用可透過 Microsoft 的混合現實平臺取得的功能，您必須先安裝並啟用 Microsoft OpenXR 外掛程式。 若要深入瞭解此外掛程式，您可以在[GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal)上查看專案。

1. Launcher 中開啟長篇的遊戲。 流覽至 Unreal Engine Marketplace 並搜尋「[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)」。 將外掛程式安裝到您的引擎。

![Unreal Marketplace](images/unreal-uxt/2-openxr-plugin.PNG)

2. 回到 [Unreal 編輯器]，移至 **Project 設定**  >  **外掛程式**，然後搜尋 "Microsoft OpenXR"。 確定已啟用外掛程式，並在出現提示時重新開機編輯器。

![啟用 Microsoft OpenXR 外掛程式](images/unreal-uxt/2-enable-plugin.PNG)

啟用 Microsoft OpenXR 外掛程式將會自動啟用混合現實開發所需的所有其他外掛程式。 請注意，必須停用 "Microsoft Windows Mixed Reality" 外掛程式，才能使用 OpenXR。 

## <a name="creating-a-level"></a>建立層級
您的下一個工作是建立玩家設定，其中包含一個起點和一個用於參考和調整的立方體。

1. 選取 [檔案] > [新增層級]，然後選擇 [空白層級]。 檢視區中的預設場景現在應該是空白的。

2. 從 [模式] 索引標籤中選取 [基本]，然後將 **PlayerStart** 拖曳至場景。 
    * 在 [詳細資料] 索引標籤中，將 [位置] 設定為 **X = 0**、**Y = 0** 和 **Z = 0**，這會在應用程式啟動時，將使用者設釘在場景中心。

![具有 PlayerStart 的檢視區](images/unreal-uxt/2-playerstart.PNG)

3. 將 [立方體] 從 [基本] 索引標籤拖曳到場景。 
    * 將 [位置] 設定為 **X = 50**、**Y = 0** 和 **Z = 0**。 在開始時將立方體放在離玩家 50 公分處。 
    * 將 [縮放] 變更為 **X = 0.2**、**Y = 0.2** 和 **Z = 0.2**，以縮小立方體。 

您將無法看到立方體，除非您將光線新增至場景，這是測試場景前的最後一項工作。

4. 切換至 [模式] 面板上的 [光線] 索引標籤，然後將 [定向光線] 拖曳至場景。 將光線放在 **PlayerStart** 上方，讓您可以看到。

![已新增光線的檢視區](images/unreal-uxt/2-light.PNG)

5. 移至 [檔案] > [儲存目前的]、將您的層級命名為 **Main**，然後選取 [儲存]。 

設定場景後，請按下工具列中的 [播放]，以查看行動中的立方體！ 當您完成工作的管理時，請按 **Esc** 以停止應用程式。

![檢視區中的立方體](images/unreal-uxt/2-cube.PNG)

場景現已完成設定，您可以開始加入棋盤和棋子，以完善應用程式環境。

## <a name="importing-assets"></a>匯入資產
場景目前看起來有點空，但是您會將現成的資產匯入專案，以修正此情況。

1. 使用 [7-zip](https://www.7-zip.org/) 下載並解壓縮 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 資產資料夾。

2. 從 [內容瀏覽器] 中選取 [新增] > [新增資料夾]，並將其命名為 **ChessAssets**。 
    * 按兩下您將在其中匯入3D 資產的新資料夾。

![顯示或隱藏來源面板](images/unreal-uxt/2-showhidesources.PNG)

3. 從 [內容瀏覽器] 中選取 [匯入]、選取解壓縮資產資料夾中的所有專案，然後按一下 [開啟]。 
    * 資產包含適用於棋盤和棋子並採用 FBX 格式的 3D 物件網格，以及將用於材質並採用 TGA 格式的紋理圖。  

4. 當 [FBX 匯入選項] 視窗快顯時，請展開 [材質] 區段，然後將 [材質匯入方法] 變更為 [不要建立材質]。
    * 選取 [全部匯入]。

![匯入 FBX 選項](images/unreal-uxt/2-nocreatemat.PNG)

您只需針對資產執行這個動作即可。 您的下一組工作是使用藍圖來建立應用程式的建置區塊。

## <a name="adding-blueprints"></a>新增藍圖

1. 選取 [內容瀏覽器] 中的 [新增] > [新增資料夾]，並將其命名為 **Blueprints**。 

> [!NOTE]
> 如果您不熟悉[藍圖](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)，這些藍圖是特殊資產，可提供節點型介面，用於建立新類型的動作項目和指令碼層級事件。 

2. 按兩下 [藍圖] 資料夾，然後按一下滑鼠右鍵並選取 [藍圖類別]。         
    * 選取 [動作項目]，並將藍圖命名為 **Board**。 

![選取您藍圖的父類別](images/unreal-uxt/2-bpparent.PNG)

新的 **Board** 藍圖現在會顯示在 **Blueprints** 資料夾中，如下列螢幕擷取畫面中所看到。 

![新的棋盤藍圖](images/unreal-uxt/2-bpboard.PNG)

您已準備好開始將材質新增至所建立的物件。

## <a name="working-with-materials"></a>使用材質
您所建立的物件預設為灰色，這並不好查看。 將材質和網格新增至您的物件是本教學課程中的最後一組工作。

1. 按兩下 **Board** 以開啟藍圖編輯器。 

2. 從 [元件] 面板中選取 [新增元件] > [場景]，並將其命名為 **Root**。 請注意，**Root** 會在下列螢幕擷取畫面中顯示為 **DefaultSceneRoot** 的子系：

![取代藍圖中的根項目](images/unreal-uxt/2-root-blueprint.PNG)


3. 按一下 **Root** 並將其拖曳至 **DefaultSceneRoot** 以進行取代，然後消除檢視區中的球體。 

![取代根項目](images/unreal-uxt/2-root.PNG)


4. 從 [元件] 面板中選取 [新增元件] > [靜態網格]，並將其命名為 **SM_Board**。 其會在 **Root** 底下顯示為子物件。

![新增靜態網格](images/unreal-uxt/2-sm-board.PNG)

4. 選取 **SM_Board**、向下捲動至 [ 詳細資料] 面板的 [靜態網格] 區段，然後從下拉式清單中選取 **ChessBoard**。 

![檢視區中的棋盤網格](images/unreal-uxt/2-sm-board-view.PNG)

5.  仍在 [詳細資料] 面板中，展開 [材質] 區段，然後從下拉式清單中選取 [建立新資產] > [材質]。 
    * 將材質命名為 **M_ChessBoard**，並將其儲存在 **ChessAssets** 資料夾中。 

![建立新的材質](images/unreal-uxt/2-newmat.PNG)

6.  按兩下 **M_ChessBoard** 材質影像以開啟材質編輯器。 

![開啟材質編輯器](images/unreal-uxt/2-material-editor.PNG)

7. 在材質編輯器中，按一下滑鼠右鍵，然後搜尋 **紋理範例**。 
    * 展開 [詳細資料] 面板中的 [材質呈現紋理基底] 區段，然後將 [紋理] 設定為 **ChessBoard_Albedo**。 
    * 將 **RGB** 輸出釘選拖曳到 **M_ChessBoard** 的 [基本色彩] 釘選。 

![設定基本色彩](images/unreal-uxt/2-boardalbedomat.PNG)

8.  再重複 4 次上述步驟，使用下列設定再建立四個 **紋理範例** 節點：
    * 將 [材質] 設定為 **ChessBoard_AO**，並將 **RGB** 連結至 [環境光遮蔽] 釘選。
    * 將 [材質] 設定為 **ChessBoard_Metal**，並將 **RGB** 連結至 [金屬] 釘選。 
    * 將 [材質] 設定為 **ChessBoard_Normal**，並將 **RGB** 連結至 [一般] 釘選。
    * 將 [材質] 設定為 **ChessBoard_Rough**，並將 **RGB** 連結至 [粗糙度] 釘選。 
    * 按一下 **[儲存]** 。 

![連結其餘紋理](images/unreal-uxt/2-boardmat.PNG)

請先確定您的材質設定看起來像是上述螢幕擷取畫面，再繼續進行。

## <a name="populating-the-scene"></a>填入場景
如果回到 **Board** 藍圖，您會看到已套用您剛建立的材質。 剩下的就是設定場景！ 首先，變更下列屬性，以確保棋盤在放入場景時大小合理，且角度正確：
1.  將 [縮放] 設定為 **(0.05, 0.05, 0.05)** ，並將 [Z 旋轉] 設定為 **90**。 
    * 按一下頂端工具列中的 [編譯]，然後按一下 [儲存] 並返回主視窗。 

![已套用材質的棋盤](images/unreal-uxt/2-chessboard.PNG)

2.  以滑鼠右鍵按一下 [立方體] > [編輯] > [刪除]，然後將 [棋盤] 從 [內容瀏覽器] 拖曳至檢視區。 
    * 將 [位置] 設定為 **X = 80**、**Y = 0** 和 **Z = 20**。 

3.  選取 [播放] 按鈕，以在層級中檢視您的新棋盤。 按 **Esc** 即可返回編輯器。 

現在您將遵循相同的步驟來建立棋子，如同您建立棋盤一般：

1. 移至 [藍圖] 資料夾、按一下滑鼠右鍵並選取 [藍圖類別]，然後選擇 [動作項目]。 將動作項目命名為 **WhiteKing**。

2. 按兩下 **WhiteKing** 以在藍圖編輯器中將其開啟、選取 [新增元件] > [場景]，並將其命名為 **Root**。 
    * 將 **Root** 拖放至 **DefaultSceneRoot**，以將其取代。 

3. 按一下 [新增元件] > [靜態網格]，並將其命名為 **SM_King**。 
    * 在 [詳細資料] 面板中，將 [靜態網格] 設定為 **Chess_King**，將 [材質] 設定為名為 **M_ChessWhite** 的新材質。 

4. 在材質編輯器中開啟 **M_ChessWhite**，並將下列 **紋理範例** 節點連結至下列項目：
   * 將 [紋理] 設定為 **ChessWhite_Albedo**，並將 **RGB** 連結至 [基本色彩] 釘選。
    * 將 [材質] 設定為 **ChessWhite_AO**，並將 **RGB** 連結至 [環境光遮蔽] 釘選。
    * 將 [材質] 設定為 **ChessWhite_Metal**，並將 **RGB** 連結至 [金屬] 釘選。 
    * 將 [材質] 設定為 **ChessWhite_Normal**，並將 **RGB** 連結至 [一般] 釘選。
    * 將 [材質] 設定為 **ChessWhite_Rough**，並將 **RGB** 連結至 [粗糙度] 釘選。 
    * 按一下 **[儲存]** 。 

在繼續之前，您的 **M_ChessKing** 材質應該看起來像是下圖。

![為國王棋建立材質](images/unreal-uxt/2-chesskingmat.PNG)

您幾乎只需將新的棋子加入場景中就大功告成了： 

1. 開啟 **WhiteKing** 藍圖，然後將 [縮放] 變更為 **(0.05, 0.05, 0.05)** ，並將 [Z 旋轉] 設定為 **90**。
    * 編譯並儲存您的藍圖，然後回到主視窗。 

2.  將 **WhiteKing** 拖曳到檢視區、切換至 [世界大綱] 面板，然後將 **WhiteKing** 拖曳至 [棋盤]，使其成為子物件。

![世界大綱](images/unreal-uxt/2-child.PNG)

3.  在 [變形] 底下的 [詳細資料] 面板中，將 **WhiteKing** 的 [位置] 設定為 **X = -26**、**Y = 4** 和 **Z = 0**。

收工了！ 選取 [播放] 查看您填入的作用中層級，然後在您準備好要結束時，按 **Esc**。 您僅僅是建立簡單的專案就牽涉到許多層面，而現在您可以繼續進行本系列的下一個部分：設定混合實境。 

[下一節：3.設定您的專案以進行混合實境](unreal-uxt-ch3.md)