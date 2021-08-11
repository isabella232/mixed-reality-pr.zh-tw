---
title: 4. 使場景成為互動式場景
description: 教學課程系列的第 4 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 74d4fb7ebab2f5ba2df477cc29d8787367c1f105cc7a65d87460ac1e033b0fbb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203776"
---
# <a name="4-making-your-scene-interactive"></a>4.使場景成為互動式場景

在上一個教學課程中，您已新增 ARSession、Pawn 和遊戲模式，來完成適用於國際象棋應用程式的混合實境設定。 本節著重於使用開放原始碼[混合實境工具組 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)外掛程式，其提供讓場景成為互動式場景的工具。 在本節結束時，您的棋子將透過使用者輸入而移動。

## <a name="objectives"></a>目標

* 安裝 Mixed Reality UX 工具外掛程式
* 將手部互動動作項目新增至您的指尖
* 建立操作工具並將其新增到場景中的物件
* 使用輸入模擬來驗證專案

## <a name="downloading-the-mixed-reality-ux-tools-plugin"></a>下載混合實境 UX 工具外掛程式
開始使用使用者輸入之前，您必須先將 Mixed Reality UX 工具外掛程式新增至專案。 若要深入瞭解 UX 工具，您可以查看[GitHub](https://aka.ms/uxt-unreal)上的專案。

1. Launcher 中開啟長篇的遊戲。 流覽至 Unreal Engine Marketplace 並搜尋「[混合現實 UX 工具](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)」。 將外掛程式安裝到您的引擎。

![Unreal Marketplace](images/unreal-uxt/2-uxt-plugin.PNG)

2. 回到 [Unreal 編輯器]，移至 **Project 設定**  >  **外掛程式**，並搜尋「混合現實 UX 工具」。 確定已啟用外掛程式，並在出現提示時重新開機編輯器。

![啟用混合式現實 UX 工具外掛程式](images/unreal-uxt/2-enable-uxt.PNG)

3.  UXTools 外掛程式的 Content 資料夾具有元件的子資料夾，包括 **按鈕**、 **XR 模擬** 和 **指標**，以及具有額外程式碼的 c + + 類別資料夾。  

> [!NOTE]
> 如果您在 **內容瀏覽器** 中看不到 [ **UXTools 內容**] 區段，請按一下 [**視圖選項] > 顯示引擎內容**]。

![顯示引擎內容](images/unreal-uxt/4-showenginecontent.PNG)

如需其他外掛程式文件，可以從混合實境 UX 工具 GitHub [存放庫](https://aka.ms/uxt-unreal)取得。

安裝外掛程式後，您就可以開始使用程式所提供的工具，從手部互動動作項目開始。

## <a name="spawning-hand-interaction-actors"></a>繁衍手部互動動作項目

與 UX 元素的手動互動是搭配手動互動動作項目來執行，此動作項目會建立及驅動指標和視覺效果，以進行遠近距離互動。
- *近距離互動* - 在食指與拇指之間捏合元素或用指尖點戳。
- *遠距離互動* - 將虛擬手發出的光線指向某個元素，並同時按下食指和拇指。

在我們的案例中，將手部互動動作項目新增至 **MRPawn** 將會：
- 新增游標至 Pawn 食指的指尖。
- 提供以關節連接的手部輸入事件，可透過 Pawn 操作。
- 允許透過從虛擬手掌延伸的手部光線，進行遠距離互動輸入事件。

建議您先閱讀手部互動的[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)，再繼續進行。

一旦準備好，就開啟 **MRPawn** 藍圖，然後移至 [事件圖形]。

1. 從 **Event BeginPlay** 拖曳並放開執行釘選，以放置新的節點。
    * 選取 [從類別繁衍動作項目]、按一下 [類別] 釘選旁的下拉式清單，然後搜尋 [Uxt 手部互動動作項目]。  

2. 繁衍第二個 [Uxt 手部互動動作項目]，這次會將 [手部] 設定為 [右手]。 當事件開始時，會在每個手部上繁衍 Uxt 手部互動動作項目。

您的 [事件圖形] 應該符合下列螢幕擷取畫面：

![繁衍 UXT 手部互動動作項目](images/unreal-uxt/4-spawnactor.PNG)

這兩個 Uxt 手部互動動作項目都需要擁有者和初始轉換位置。 在此情況下，初始轉換並不重要，因為 UX 工具會讓「手互動」動作專案在看到時立即跳到虛擬手。 不過，`SpawnActor` 函式需要轉換輸入來避免編譯器錯誤，因此您將使用預設值。

1. 從其中一個 [繁衍轉換] 釘選拖曳並放開釘選，以放置新的節點。
    * 搜尋 [進行轉換] 節點，然後將 [傳回值] 拖曳至另一手的 [繁衍轉換]，讓兩個 **SpawnActor** 節點連線。

2.  選取兩個 **SpawnActor** 節點底端的 **向下箭頭**，以顯示 [擁有者] 釘選。    
    * 從其中一個 **擁有者** 釘選拖曳釘選，然後放開以放置新的節點。
    * 搜尋 **本身**，然後選取 **取得本身的參考** 變數。
    * 在 **本身** 物件參考節點與另一個手部互動動作項目的 **擁有者** 釘選之間建立連結。
3. 最後，應對兩個手部互動動作項目都核取 [在抓取目標上顯示近處的游標] 方塊。 當您的食指靠近時，抓取目標上應該會出現游標，讓您能夠看出手指與目標的相對位置。
    * **編譯**、**儲存**，然後返回主視窗。

確定連線符合下列螢幕擷取畫面，但是您可以隨意拖曳節點，讓您的藍圖更容易閱讀。

![完成 UXT 手部互動動作項目設定](images/unreal-uxt/4-fingerptrs.PNG)

您可以在 [UX 工具文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)中找到關於手動互動動作項目的詳細資訊。

現在，專案中的虛擬手部有一種方式可以選取物件，但仍然無法進行操作。 測試應用程式前的最後一項工作是將操作工具元件新增至場景中的動作項目。

## <a name="attaching-manipulators"></a>附加操作工具

操作工具是一種元件，可回應以關節連接的手部輸入，而且可以抓取、旋轉和轉譯。 將操作工具的轉換套用至動作項目轉換可允許直接動作項目操作。

1. 開啟 [棋盤] 藍圖、按一下 [新增元件]，然後在 [元件] 面板中搜尋 [Uxt 一般操作工具]。

![新增一般操作工具](images/unreal-uxt/4-addmanip.PNG)

2. 展開 [詳細資料] 面板中的 [一般操作工具] 區段。 您可以從這裡設定單手或雙手操作、旋轉模式和其他等等。 請隨意選取您想要的任何模式，然後 [編譯] 及 [儲存] 棋盤。

![設定模式](images/unreal-uxt/4-setrotmode.PNG)

3. 針對 **WhiteKing** 動作項目重複上述步驟。

若要深入了解混合實境 UX 工具外掛程式中提供的操作工具元件，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html)。

## <a name="testing-the-scene"></a>測試場景

好消息！ 您已經準備好使用新的虛擬手部和使用者輸入來測試應用程式。 按下主視窗中的 [播放]，您會看到兩個網狀手部，以及從每一個手掌延伸的光線。 您可以控制手部及其互動，如下所示：
- 按住 **左 Alt** 鍵，以控制 **左手**，按住 **左 Shift** 鍵，以控制 **右手**。
- 移動您的滑鼠來移動手部，並使用您的 **滑鼠滾輪** 來捲動，將手部 **向前** 或 **向後** 移動。
- 使用滑鼠左鍵 **捏合**，使用滑鼠中間按鈕 **撥開**。

> [!NOTE]
> 如果您將多個頭戴式裝置插入電腦，輸入模擬可能無法正常運作。 如有問題，請嘗試拔掉其他頭戴式裝置。

![檢視區中的模擬手部](images/unreal-uxt/4-handsim.PNG)

試著使用模擬的手部來拾起、移動和放置白棋國王，並操作棋盤！ 實驗遠近距離互動 - 請注意，當您的手夠靠近可以直接抓取棋盤和國王時，食指指尖上的手指游標會取代手部光線。

若要深入了解 MRTK UX 工具外掛程式中所提供的模擬手部功能，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html)。

既然您的虛擬手部可以與物件互動，您就可以繼續進行下一個教學課程，並新增使用者介面和事件。

[下一節：5.新增按鈕並重設棋子位置](unreal-uxt-ch5.md)
