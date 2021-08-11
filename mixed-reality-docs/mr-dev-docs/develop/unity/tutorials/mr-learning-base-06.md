---
title: 建立使用者介面
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立靜態和動態使用者介面。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, prefab, 全像投影, 工具提示
ms.localizationpriority: high
ms.openlocfilehash: 605379be0e2f3238ddb5de5c47b6df005c4bf2eb82a2e04156f1317e0e7659fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227733"
---
# <a name="6-creating-user-interfaces"></a>6.建立使用者介面

在本教學課程中，您將了解如何使用 MRTK 的按鈕和功能表預製物件以及 Unity 的 TextMeshPro 元件來建立簡單的使用者介面。 您也將了解如何設定按鈕來觸發事件，並新增動態工具提示 UI 元素，以提供使用者其他資訊。

## <a name="objectives"></a>目標

* 了解如何組織集合中的按鈕
* 了解如何使用 MRTK 的功能表預製物件
* 了解如何使用 UI 功能表和按鈕來與全像投影互動
* 瞭解如何新增文字元素
* 了解如何動態產生物件的工具提示

## <a name="creating-a-static-panel-of-buttons"></a>建立按鈕的靜態面板

在階層視窗中，以滑鼠右鍵按一下 **RoverExplorer** 物件並選取 [建立空物件]，將空白物件新增為 RoverExplorer 的子系，然後將物件命名為 **Buttons**，並設定 **變形** 元件，如下所示：

* **位置**：X = -0.6、Y = 0.036、Z = -0.5
* **旋轉**：X = 90、Y = 0、Z = 0
* **縮放比例**：X = 1、Y = 1、Z = 1

![已選取並置放新建立 Buttons 物件的 Unity](images/mr-learning-base/base-06-section1-step1-1.png)

在 [專案] 視窗中，瀏覽至 **資產** > **MRTK.Tutorials.GettingStarted** > **預製物件** 資料夾，按一下並將 **PressableRoundButton** 預製物件拖曳到 **Buttons** 物件，然後以滑鼠右鍵按一下 PressableRoundButton 並選取 [複製] 建立複本，重覆上述步驟直到完成三個 PressableRoundButton 物件為止：

![具有新增 PressableRoundButton Prefabs 的 Unity](images/mr-learning-base/base-06-section1-step1-2.png)

在階層視窗中選取 **Buttons** 物件，然後在偵測器視窗中使用 [新增元件] 按鈕來新增 **GridObjectCollection** 元件，並進行以下設定：

* **排序類型**：子順序
* **版面配置**：水平
* **儲存格寬度**：0.2
* **錨點**：中間靠左對齊

然後按一下 [更新集合] 按鈕，以更新 Buttons 物件的子物件位置：

![已新增、設定和套用 GridObjectCollection 元件的 Unity Buttons 物件](images/mr-learning-base/base-06-section1-step1-3.png)

在階層視窗中，將按鈕命名為 **提示**、**分解** 和 **重設**。

為每個按鈕選取 **SeeItSayItLabel** > **TextMeshPro** 子物件，然後在 偵測器視窗中分別變更 **TextMeshPro - 文字** 元件文字以符合按鈕名稱：

![已設定按鈕文字標籤的 Unity](images/mr-learning-base/base-06-section1-step1-4.png)

完成後，摺疊 Buttons 物件的子物件。

在階層視窗中，選取 [提示] 按鈕物件，然後在偵測器視窗中，設定 **Interactable.OnClick ()** 事件，如下所示：

* 將 **RoverAssembly** 物件指派給 **無 (物件)** 欄位
* 從 **沒有函式** 下拉式清單中，選取 **PartAssemblyController** > **TogglePlacementHints ()** ，以將此函式設定為觸發事件時所要執行的動作

![已設定 [提示] 按鈕物件 OnClick 事件的 Unity](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> Interactable 元件是一個全方位容器，可讓任何物件輕鬆地進行互動及回應輸入。 Interactable 可作為所有輸入類型的概括，包括觸控、手部射線、語音等，並可將這些互動注入事件和視覺主題回應。 若要了解如何針對不同的輸入類型進行設定，並自訂其視覺化主題，您可參閱 [MRTK 文件入口網站](/windows/mixed-reality/mrtk-unity/)中的 [Interactable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) 指南。

在階層視窗中，選取 [分解] 按鈕物件，然後在偵測器視窗中，設定 **Interactable.OnClick ()** 事件，如下所示：

* 將 **RoverAssembly** 物件指派給 **無 (物件)** 欄位
* 從 **沒有函式** 下拉式清單中，選取 **ExplodedViewController** > **ToggleExplodedView ()** ，以將此函式設定為觸發事件時所要執行的動作

![已設定 [分解] 按鈕物件 OnClick 事件的 Unity](images/mr-learning-base/base-06-section1-step1-6.png)

按下開始遊戲按鈕進入遊戲模式，然後按住空格鍵按鈕來啟動手勢功能，並用滑鼠按下 [提示] 按鈕來切換放置提示物件的可見度：

![按下 [提示] 按鈕的 Unity 播放模式分割檢視](images/mr-learning-base/base-06-section1-step1-7.png)

而 **分解** 按鈕可開啟和關閉分解檢視功能：

![按下 [分解] 按鈕的 Unity 播放模式分割檢視](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>建立會跟隨使用者的動態功能表

在 [Project] 視窗中，流覽至 [**封裝**  >  **混合現實工具組 Foundation**  >  **SDK**  >  **功能**  >  **UX**  >  **Prefabs**  >  **功能表**] 資料夾，並按一下 [ **NearMenu4x1** 預製專案] 並將其拖曳到 [階層] 視窗中，將其轉換 **位置** 設定為 X = 0、Y =-0.4、Z = 0，並依照下列方式進行設定：

* 確認 **SolverHandler** 元件的 [追蹤目標類型] 設定為 **頭部**
* 核取 **RadialView** 規劃元件旁的核取方塊，使其預設為啟用

![已選取新增附近功能表 Prefab 的 Unity](images/mr-learning-base/base-06-section2-step1-1.png)

在階層視窗中，將物件重新命名為 **功能表**，然後展開其 **ButtonCollection** 子物件，以顯示四個按鈕：

![已選取 Menu 物件並展開 ButtonCollection 物件的 Unity](images/mr-learning-base/base-06-section2-step1-2.png)

將 ButtonCollection 中的第一個按鈕重新命名為指標，然後在 [偵測器] 視窗中，設定按鈕設定 Helper (腳本) 元件，如下所示：

* 將 **主要標籤文字** 變更為符合按鈕的名稱
* 將看起來像是箭號的指標物件指派給 None (物件) ] 欄位
* 從 **沒有函式** 下拉式清單中，選取 GameObject > SetActive (bool)，以將此函式設定為觸發事件時所要執行的動作
* 確認 **已核取** 引數核取方塊
* 將 **圖示** 變更為「搜尋」圖示

![已設定 [指標] 按鈕物件按鈕設定協助程式的 Unity](images/mr-learning-base/base-06-section2-step1-3.png)

若要停用箭號指標物件，請在 [階層] 視窗中，選取看起來像是箭號的指標物件，然後在 [偵測器] 視窗中：

* 取消核取其名稱旁的核取方塊，使其預設為非作用中
* 使用 [新增元件] 按鈕來新增 **Directional Indicator Controller (指令碼)** 元件

![已選取、停用 Indicator 物件並已新增 DirectionalIndicatorController 元件的 Unity](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> 現在，當應用程式啟動時，預設會停用箭號指標，而且可以按下指標按鈕來啟用。

> [!NOTE]
> Directional Indicator Controller (指令碼) 不是 MRTK 的一部分，但已包含在教學課程資產中。

將第二個按鈕重新命名為 **TapToPlace**，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件，如下所示：

* 將 **主要標籤文字** 變更為符合按鈕的名稱
* 將 RoverExplorer > **RoverAssembly** 物件指派給 **無 (物件)** 欄位
* 從 [沒有函式] 下拉式清單中，選取 **TapToPlace** > **bool enabled**，以在觸發事件時更新此屬性值
* 確認 **已核取** 引數核取方塊
* 將 **圖示** 變更為「手部發光」圖示

![已設定 TapToPlace 按鈕物件按鈕設定協助程式的 Unity](images/mr-learning-base/base-06-section2-step1-5.png)

在階層視窗中，選取 **RoverAssembly** 物件，然後在偵測器視窗中設定 **點選放置 (指令碼)** 元件，如下所示：

* 取消核取其名稱旁的核取方塊，使其預設為非作用中
* 在 **On Placing Stopped ()** 事件區段中，按一下 **+** 圖示，以新增新的事件：
* 將 RoverExplorer > **RoverAssembly** 物件指派給 **無 (物件)** 欄位
* 從 [沒有函式] 下拉式清單中，選取 **TapToPlace** > **bool enabled**，以在觸發事件時更新此屬性值
* 確認 **未核取** 引數核取方塊

![已重新設定 TapToPlace 元件的 Unity](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> 現在，當應用程式啟動時，預設會停用點選放置功能，而且只要按下 [點選放置] 按鈕就能啟用。 此外，當點選放置完成時，會自行停用。

## <a name="adding-text-to-the-scene"></a>將文字加入場景

在階層視窗中，以滑鼠右鍵按一下 **表格** 物件，然後選取 **3D 物件** > **文字 -TextMeshPro**，將文字物件當作表格物件的子系新增，然後在偵測器視窗中，設定 **矩形轉換** 元件，如下所示：

* 將 **Pos Y** 變更為 1
* 將 **寬度** 變更為 1
* 將 **高度** 變更為 1
* 將 **旋轉 X** 變更為 90

![已選取新建立 TextMeshPro 物件的 Unity](images/mr-learning-base/base-06-section3-step1-1.png)

然後設定 **TextMeshPro - 文字** 元件，如下所示：

* 將 **文字** 變更為 Rover Explorer
* 將 **字型樣式** 變更為粗體
* 將 **字型大小** 變更為 1
* 將其他設定 > **邊界** 變更為 0.03

![已設定 TextMeshPro 元件的 Unity](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>新增工具提示

在 [Project] 視窗中，流覽至 [**套件**  >  **混合現實工具組 Foundation**  >  **SDK**  >  **功能**  >  **UX**  >  **Prefabs**  >  **工具提示**] 資料夾，以找出工具提示 Prefabs：

![已選取 [工具提示] 資料夾的 Unity [專案] 視窗](images/mr-learning-base/base-06-section4-step1-1.png)

在階層視窗中，展開 RoverExplorer > **RoverParts** 物件，並選取其所有子 Rover 組件物件，然後在偵測器視窗中，使用 [新增元件] 按鈕新增 **ToolTipSpawner** 件並加以設定，如下所示：

* 確定已核取 [已啟用焦點] 核取方塊，以要求使用者看向要顯示工具提示的位置
* 將 Project 視窗中的 **簡單行工具提示** 預製專案指派給 **預製專案** 欄位
* 將工具提示覆寫設定 > **設定模式** 變更為 **覆寫**
* 將工具提示覆寫設定 > **手動樞紐分析表本機位置 Y** 變更為 **1.5**

![已選取所有 Rover 組件物件並已新增和設定 ToolTipSpawner 元件的 Unity](images/mr-learning-base/base-06-section4-step1-2.png)

在 [階層] 視窗中，選取 [Camera_Part]、[RoverParts > **Camera_Part**]，然後設定 **ToolTipSpawner** 元件，如下所示：

* 變更 **工具提示文字** 以反映組件的名稱，例如 **攝影機**

![已設定相機 ToolTipText 的 Unity](images/mr-learning-base/base-06-section4-step1-3.png)

針對每個 Rover 組件物件 **重複** 此步驟，以設定 **ToolTipSpawner** 元件，如下所示：

* 針對 **Generator_Part**，將 **工具提示文字** 變更為 **產生器**
* 針對 **Lights_Part**，將 **工具提示文字** 變更為 **光源**
* 針對 **UHFAntenna_Part**，將 **工具提示文字** 變更為 **UHF 天線** 欄位
* 針對 **Spectrometer_Part**，將 **工具提示文字** 變更為 **Spectrometer**

按下 [開始遊戲] 按鈕進入遊戲模式，然後在往下移動滑鼠時按住滑鼠右鍵，直到目光對到其中一個組件且該組件的工具提示出現為止：

![由注視觸發工具提示的 Unity 播放模式分割檢視](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何使用 MRTK 提供的按鈕和功能表預製物件和 Unity 的 TextMeshPro 元件來建立簡單的使用者介面，以及如何設定按鈕以在按下時觸發事件。 您也已了解如何新增動態工具提示 UI 元素，以提供使用者其他資訊。

> [!div class="nextstepaction"]
> [下一個教學課程：7.與 3D 物件互動](mr-learning-base-07.md)
