---
title: 3. 設定您的專案以進行混合實境
description: 教學課程系列的第 3 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 491e17c5a85ed05f2e324a4f346cc82d207440469fae97fc88fee7065fae0495
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226807"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3.設定您的專案以進行混合實境

在上一個教學課程中，您已花費時間設定國際象棋應用程式專案。 本節將逐步引導您設定應用程式以進行混合實境開發，這表示新增 AR 工作階段。 您將會針對此工作使用 ARSessionConfig 資料資產，其中包括有用的 AR 設定，例如空間對應和遮蔽。 您可以在 Unreal 的文件中找到關於 [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 資產和 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 類別的詳細資料。

## <a name="objectives"></a>目標

* 使用 Unreal Engine 的 AR 設定
* 使用 ARSessionConfig 資料資產
* 設定 Pawn 和遊戲模式

## <a name="adding-the-session-asset"></a>新增工作階段資產

Unreal 中的 AR 工作階段本身不會發生。 若要使用工作階段，您需要借助於 ARSessionConfig 資料資產，這就是您接下來的工作：

1. 在 [內容瀏覽器] 中，按一下 [新增] > [其他] > [資料資產]。 確定您是在根 **內容** 資料夾層級。
    * 選取 **ARSessionConfig** 按一下 [選取]，然後將資產命名為 **ARSessionConfig**。

![建立資料資產](images/unreal-uxt/3-createasset.PNG)

3. 按兩下 **ARSessionConfig** 將其開啟、保留所有預設設定，然後點擊 [儲存]。 返回主視窗。

![AR 工作階段設定](images/unreal-uxt/3-arsessionconfig.PNG)

完成後，您的下一個步驟是確保 AR 工作階段會在層級載入時啟動，並在層級結束時停止。 值得慶幸的是，Unreal 具有名為 **層級藍圖** 的特殊藍圖，可作為整個層級的全域事件圖形。 在 **層級藍圖** 中連線 ARSessionConfig 資產，保證 AR 工作階段會在遊戲開始玩時立即啟動。

1. 從編輯器工具列中按一下 [藍圖] > [開啟層級藍圖]：

![開啟層級藍圖](images/unreal-uxt/3-level-blueprint.PNG)

5. 拖曳 **Event BeginPlay** 的執行節點 (向左箭號圖示) 並放開，然後搜尋 **啟動 AR 工作階段** 並按 Enter 鍵。  
    * 按一下 [工作階段組態] 底下的 [選取資產] 下拉式清單，然後選擇 **ARSessionConfig** 資產。

![啟動 AR 工作階段](images/unreal-uxt/3-start-ar-session.PNG)

6. 以滑鼠右鍵按一下 EventGraph 中的任一處，並建立新的 [事件 EndPlay] 節點。 拖曳執行釘選並放開，然後搜尋 [停止 AR 工作階段] 節點，並按 Enter 鍵。 如果 AR 工作階段在層級結束時仍在執行，若您在串流至頭戴式裝置時重新啟動應用程式，某些功能可能會停止運作。
    * 依序點擊 [編譯]、[儲存]，然後返回主視窗。

![停止 AR 工作階段](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>建立 Pawn

此時，專案仍然需要玩家物件。 在 Unreal 中，**Pawn** 代表遊戲中的使用者，或在此案例中，其將是 HoloLens 2 體驗。

1. 在 [內容] 資料夾中按一下 [新增] > [藍圖類別]，然後展開底端的 [所有類別] 區段。
    * 搜尋 **DefaultPawn**，按一下 [選取]，將其命名為 **MRPawn**，然後按兩下要開啟的資產。

![建立繼承自 DefaultPawn 的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

2. 從 [元件] 面板中按一下 [新增元件] > [相機]，並將其命名為 **Camera**。 確定 [相機] 元件是根元件的直接子系 (**CollisionComponent**)。 這可讓播放器相機隨著 HoloLens 2 裝置一起移動。

> [!NOTE]
> 根據預設，Pawn 具有網格和碰撞元件。 在大部分的 Unreal 專案中，Pawn 是可與其他元件碰撞的固體物件。 由於 Pawn 和使用者在混合實境中是相同的，因此您希望能夠在不發生任何碰撞的情況下通過全像投影。

3. 從 [元件] 面板中選取 **CollisionComponent**，然後向下捲動至 [詳細資料] 面板的 [碰撞] 區段。
    * 按一下 [碰撞預設] 下拉式清單，然後將值變更為 **NoCollision**。
    * 針對 **MeshComponent** 執行相同的動作。

![調整 Pawn 的衝突預設值](images/unreal-uxt/3-nocollision.PNG)

4. **編譯** 和 **儲存** 藍圖。

您在這裡的工作完成後，回到主視窗。

## <a name="create-a-game-mode"></a>建立遊戲模式

混合實境設定的最後一塊拼圖是遊戲模式。 遊戲模式會決定遊戲或體驗的一些設定，包括要使用的預設 Pawn。

1.  在 [內容] 資料夾中按一下 [新增] > [藍圖類別]，然後選取 [遊戲模式基底] 作為父類別。 將其命名為 **MRGameMode**，然後按兩下加以開啟。

![內容瀏覽器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  移至 [詳細資料] 面板中的 [類別] 區段，然後將 [預設 Pawn 類別] 變更為 **MRPawn**。
    * 依序點擊 [編譯]、[儲存]，然後返回主視窗。

![設定預設的 Pawn 類別](images/unreal-uxt/3-setpawn.PNG)

3.  選取 [編輯] > [專案設定]，然後按一下左側清單中的 [地圖與模式]。
    * 展開 [預設模式]，然後將 [預設遊戲模式] 變更為 **MRGameMode**。
    * 展開 [預設地圖]，然後同時將 **EditorStartupMap** 和 **GameDefaultMap** 變更為 **Main**。 如此，當您關閉編輯器並重新開啟時，系統會預設為選取主要地圖。

![專案設定 - 地圖與模式](images/unreal-uxt/3-mapsandmodes.PNG)

在混合實境的專案完全設定好之後，您就可以繼續進行下一個教學課程，並開始將使用者輸入新增到場景。

[下一節：4.使場景成為互動式場景](unreal-uxt-ch4.md)
