---
title: 3. 設定您的專案以進行混合實境
description: 教學課程系列的第 3 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 26bb874578e56b21d319741b8b1c1ff6decebe4b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609699"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="5c3ec-104">3.設定您的專案以進行混合實境</span><span class="sxs-lookup"><span data-stu-id="5c3ec-104">3. Setting up your project for mixed reality</span></span>

<span data-ttu-id="5c3ec-105">在上一個教學課程中，您已花費時間設定國際象棋應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-105">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="5c3ec-106">本節將逐步引導您設定應用程式以進行混合實境開發，這表示新增 AR 工作階段。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-106">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="5c3ec-107">您將會針對此工作使用 ARSessionConfig 資料資產，其中包括有用的 AR 設定，例如空間對應和遮蔽。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-107">You'll be using an ARSessionConfig data asset for this task, which has useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="5c3ec-108">您可以在 Unreal 的文件中找到關於 [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 資產和 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 類別的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-108">You can find more details about the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class in Unreal's documentation.</span></span>

## <a name="objectives"></a><span data-ttu-id="5c3ec-109">目標</span><span class="sxs-lookup"><span data-stu-id="5c3ec-109">Objectives</span></span>

* <span data-ttu-id="5c3ec-110">使用 Unreal Engine 的 AR 設定</span><span class="sxs-lookup"><span data-stu-id="5c3ec-110">Working with Unreal Engine's AR settings</span></span>
* <span data-ttu-id="5c3ec-111">使用 ARSessionConfig 資料資產</span><span class="sxs-lookup"><span data-stu-id="5c3ec-111">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="5c3ec-112">設定 Pawn 和遊戲模式</span><span class="sxs-lookup"><span data-stu-id="5c3ec-112">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="5c3ec-113">新增工作階段資產</span><span class="sxs-lookup"><span data-stu-id="5c3ec-113">Adding the session asset</span></span>

<span data-ttu-id="5c3ec-114">Unreal 中的 AR 工作階段本身不會發生。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-114">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="5c3ec-115">若要使用工作階段，您需要借助於 ARSessionConfig 資料資產，這就是您接下來的工作：</span><span class="sxs-lookup"><span data-stu-id="5c3ec-115">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="5c3ec-116">在 [內容瀏覽器] 中，按一下 [新增] > [其他] > [資料資產]。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-116">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="5c3ec-117">確定您是在根 **內容** 資料夾層級。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-117">Make sure you're at the root **Content** folder level.</span></span>
    * <span data-ttu-id="5c3ec-118">選取 **ARSessionConfig** 按一下 [選取]，然後將資產命名為 **ARSessionConfig**。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-118">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![建立資料資產](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="5c3ec-120">按兩下 **ARSessionConfig** 將其開啟、保留所有預設設定，然後點擊 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-120">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="5c3ec-121">返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-121">Return to the Main window.</span></span>

![AR 工作階段設定](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="5c3ec-123">完成後，您的下一個步驟是確保 AR 工作階段會在層級載入時啟動，並在層級結束時停止。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-123">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="5c3ec-124">值得慶幸的是，Unreal 具有名為 **層級藍圖** 的特殊藍圖，可作為整個層級的全域事件圖形。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-124">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="5c3ec-125">在 **層級藍圖** 中連線 ARSessionConfig 資產，保證 AR 工作階段會在遊戲開始玩時立即啟動。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-125">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="5c3ec-126">從編輯器工具列中按一下 [藍圖] > [開啟層級藍圖]：</span><span class="sxs-lookup"><span data-stu-id="5c3ec-126">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span>

![開啟層級藍圖](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="5c3ec-128">拖曳 **Event BeginPlay** 的執行節點 (向左箭號圖示) 並放開，然後搜尋 **啟動 AR 工作階段** 並按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-128">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release, then search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="5c3ec-129">按一下 [工作階段組態] 底下的 [選取資產] 下拉式清單，然後選擇 **ARSessionConfig** 資產。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-129">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span>

![啟動 AR 工作階段](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="5c3ec-131">以滑鼠右鍵按一下 EventGraph 中的任一處，並建立新的 [事件 EndPlay] 節點。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-131">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="5c3ec-132">拖曳執行釘選並放開，然後搜尋 [停止 AR 工作階段] 節點，並按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-132">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="5c3ec-133">如果 AR 工作階段在層級結束時仍在執行，若您在串流至頭戴式裝置時重新啟動應用程式，某些功能可能會停止運作。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-133">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>
    * <span data-ttu-id="5c3ec-134">依序點擊 [編譯]、[儲存]，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-134">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![停止 AR 工作階段](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="5c3ec-136">建立 Pawn</span><span class="sxs-lookup"><span data-stu-id="5c3ec-136">Create a Pawn</span></span>

<span data-ttu-id="5c3ec-137">此時，專案仍然需要玩家物件。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-137">At this point, the project still needs a player object.</span></span> <span data-ttu-id="5c3ec-138">在 Unreal 中，**Pawn** 代表遊戲中的使用者，或在此案例中，其將是 HoloLens 2 體驗。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-138">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="5c3ec-139">在 [內容] 資料夾中按一下 [新增] > [藍圖類別]，然後展開底端的 [所有類別] 區段。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-139">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span>
    * <span data-ttu-id="5c3ec-140">搜尋 **DefaultPawn**，按一下 [選取]，將其命名為 **MRPawn**，然後按兩下要開啟的資產。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-140">Search for **DefaultPawn**, click **Select**, name it **MRPawn**, and double-click the asset to open.</span></span>

![建立繼承自 DefaultPawn 的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

2. <span data-ttu-id="5c3ec-142">從 [元件] 面板中按一下 [新增元件] > [相機]，並將其命名為 **Camera**。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-142">Click **Add Component > Camera** from the **Components** panel and name it **Camera**.</span></span> <span data-ttu-id="5c3ec-143">確定 [相機] 元件是根元件的直接子系 (**CollisionComponent**)。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-143">Make sure that the **Camera** component is a direct child of the root (**CollisionComponent**).</span></span> <span data-ttu-id="5c3ec-144">這可讓播放器相機隨著 HoloLens 2 裝置一起移動。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-144">This allows the player camera to move with the HoloLens 2 device.</span></span>

> [!NOTE]
> <span data-ttu-id="5c3ec-145">根據預設，Pawn 具有網格和碰撞元件。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="5c3ec-146">在大部分的 Unreal 專案中，Pawn 是可與其他元件碰撞的固體物件。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="5c3ec-147">由於 Pawn 和使用者在混合實境中是相同的，因此您希望能夠在不發生任何碰撞的情況下通過全像投影。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span>

3. <span data-ttu-id="5c3ec-148">從 [元件] 面板中選取 **CollisionComponent**，然後向下捲動至 [詳細資料] 面板的 [碰撞] 區段。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span>
    * <span data-ttu-id="5c3ec-149">按一下 [碰撞預設] 下拉式清單，然後將值變更為 **NoCollision**。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span>
    * <span data-ttu-id="5c3ec-150">針對 **MeshComponent** 執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-150">Do the same for the **MeshComponent**</span></span>

![調整 Pawn 的衝突預設值](images/unreal-uxt/3-nocollision.PNG)

4. <span data-ttu-id="5c3ec-152">**編譯** 和 **儲存** 藍圖。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-152">**Compile** and **Save** the Blueprint.</span></span>

<span data-ttu-id="5c3ec-153">您在這裡的工作完成後，回到主視窗。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-153">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="5c3ec-154">建立遊戲模式</span><span class="sxs-lookup"><span data-stu-id="5c3ec-154">Create a Game Mode</span></span>

<span data-ttu-id="5c3ec-155">混合實境設定的最後一塊拼圖是遊戲模式。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-155">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="5c3ec-156">遊戲模式會決定遊戲或體驗的一些設定，包括要使用的預設 Pawn。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-156">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="5c3ec-157">在 [內容] 資料夾中按一下 [新增] > [藍圖類別]，然後選取 [遊戲模式基底] 作為父類別。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-157">Click **Add New > Blueprint Class** in the **Content** folder and select **Game Mode Base** as the parent class.</span></span> <span data-ttu-id="5c3ec-158">將其命名為 **MRGameMode**，然後按兩下加以開啟。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-158">Name it **MRGameMode** and double-click to open.</span></span>

![內容瀏覽器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="5c3ec-160">移至 [詳細資料] 面板中的 [類別] 區段，然後將 [預設 Pawn 類別] 變更為 **MRPawn**。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-160">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span>
    * <span data-ttu-id="5c3ec-161">依序點擊 [編譯]、[儲存]，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-161">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![設定預設的 Pawn 類別](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="5c3ec-163">選取 [編輯] > [專案設定]，然後按一下左側清單中的 [地圖與模式]。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-163">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span>
    * <span data-ttu-id="5c3ec-164">展開 [預設模式]，然後將 [預設遊戲模式] 變更為 **MRGameMode**。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-164">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span>
    * <span data-ttu-id="5c3ec-165">展開 [預設地圖]，然後同時將 **EditorStartupMap** 和 **GameDefaultMap** 變更為 **Main**。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-165">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="5c3ec-166">如此，當您關閉編輯器並重新開啟時，系統會預設為選取主要地圖。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-166">When you close and reopen the editor or play the game, the Main map will now be selected by default.</span></span>

![專案設定 - 地圖與模式](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="5c3ec-168">在混合實境的專案完全設定好之後，您就可以繼續進行下一個教學課程，並開始將使用者輸入新增到場景。</span><span class="sxs-lookup"><span data-stu-id="5c3ec-168">With the project fully set up for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span>

[<span data-ttu-id="5c3ec-169">下一節：4.使場景成為互動式場景</span><span class="sxs-lookup"><span data-stu-id="5c3ec-169">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
