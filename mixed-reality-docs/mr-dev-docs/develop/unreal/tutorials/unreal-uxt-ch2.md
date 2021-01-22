---
title: 2. 初始化您的專案和第一個應用程式
description: 教學課程系列的第 2 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 9e02ea6cb2710b4661e97dc8b0d5f4f48ab09fa7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583908"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="d35e6-104">2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="d35e6-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="d35e6-105">在第一個教學課程中，您將著手進行新的 Unreal 項目，並啟用 HoloLens 外掛程式、建立和亮顯層級，以及新增棋子。</span><span class="sxs-lookup"><span data-stu-id="d35e6-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="d35e6-106">您將對所有 3D 物件和材質使用預先製作的資產，因此無須擔心自行建立模型的問題。</span><span class="sxs-lookup"><span data-stu-id="d35e6-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="d35e6-107">在本教學課程結束時，您將會有一個可供混合實境使用的空白畫布。</span><span class="sxs-lookup"><span data-stu-id="d35e6-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d35e6-108">請確定您擁有[開始使用](/windows/mixed-reality/unreal-uxt-ch1)頁面中的所有必要項目。</span><span class="sxs-lookup"><span data-stu-id="d35e6-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="d35e6-109">目標</span><span class="sxs-lookup"><span data-stu-id="d35e6-109">Objectives</span></span>

* <span data-ttu-id="d35e6-110">設定 Unreal 專案以用於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="d35e6-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="d35e6-111">匯入資產和設定場景</span><span class="sxs-lookup"><span data-stu-id="d35e6-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="d35e6-112">使用藍圖建立動作項目和指令碼層級事件</span><span class="sxs-lookup"><span data-stu-id="d35e6-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="d35e6-113">建立新的 Unreal 專案</span><span class="sxs-lookup"><span data-stu-id="d35e6-113">Creating a new Unreal project</span></span>

<span data-ttu-id="d35e6-114">您需要的第一個項目是供您使用的專案。</span><span class="sxs-lookup"><span data-stu-id="d35e6-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="d35e6-115">如果您是首次接觸的 Unreal 開發人員，則需要從 Epic Launcher [下載支援檔案](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="d35e6-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="d35e6-116">啟動 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="d35e6-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="d35e6-117">在 [新增專案類別] 中選取 [遊戲]，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![選取遊戲專案範本](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="d35e6-119">選取 **空白** 範本，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-119">Select the **Blank** Template and click **Next**.</span></span> 

![選取空白範本](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="d35e6-121">將 [C++]、[可縮放 3D 或 2D]、[行動裝置/平板電腦] 及 [無起始內容] 設為您的 [專案設定]，然後選擇儲存位置並按一下 [建立專案]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="d35e6-122">您必須選取 C++ 專案 (而非藍圖專案) 以建置 UX 工具外掛程式 (您稍後將在第 4 節設定此外掛程式)。</span><span class="sxs-lookup"><span data-stu-id="d35e6-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![初始專案設定](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="d35e6-124">專案應該會自動在 Unreal 編輯器中開啟，這表示您已準備好進行下一節。</span><span class="sxs-lookup"><span data-stu-id="d35e6-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="d35e6-125">啟用必要的外掛程式</span><span class="sxs-lookup"><span data-stu-id="d35e6-125">Enabling required plugins</span></span>

<span data-ttu-id="d35e6-126">在您開始將物件新增至場景之前，必須啟用兩個外掛程式。</span><span class="sxs-lookup"><span data-stu-id="d35e6-126">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="d35e6-127">開啟 [編輯] > [外掛程式]，然後從內建選項清單中選取 [擴增實境]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-127">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="d35e6-128">向下捲動至 **HoloLens**，並勾選 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-128">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![啟用 HoloLens 外掛程式](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="d35e6-130">從內建選項清單中選取 [虛擬實境]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-130">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="d35e6-131">向下捲動至 **Microsoft Windows Mixed Reality**、勾選 [啟用]，然後重新啟動您的編輯器。</span><span class="sxs-lookup"><span data-stu-id="d35e6-131">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![啟用 Windows Mixed Reality 外掛程式](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="d35e6-133">這兩個外掛程式都是進行 HoloLens 2 開發的必要項目。</span><span class="sxs-lookup"><span data-stu-id="d35e6-133">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="d35e6-134">啟用外掛程式後，您的空白層級即可供公司使用。</span><span class="sxs-lookup"><span data-stu-id="d35e6-134">With the plugins enabled, your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="d35e6-135">建立層級</span><span class="sxs-lookup"><span data-stu-id="d35e6-135">Creating a level</span></span>
<span data-ttu-id="d35e6-136">您的下一個工作是建立玩家設定，其中包含一個起點和一個用於參考和調整的立方體。</span><span class="sxs-lookup"><span data-stu-id="d35e6-136">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="d35e6-137">選取 [檔案] > [新增層級]，然後選擇 [空白層級]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-137">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="d35e6-138">檢視區中的預設場景現在應該是空白的。</span><span class="sxs-lookup"><span data-stu-id="d35e6-138">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="d35e6-139">從 [模式] 索引標籤中選取 [基本]，然後將 **PlayerStart** 拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="d35e6-139">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="d35e6-140">在 [詳細資料] 索引標籤中，將 [位置] 設定為 **X = 0**、**Y = 0** 和 **Z = 0**，這會在應用程式啟動時，將使用者設釘在場景中心。</span><span class="sxs-lookup"><span data-stu-id="d35e6-140">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![具有 PlayerStart 的檢視區](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="d35e6-142">將 [立方體] 從 [基本] 索引標籤拖曳到場景。</span><span class="sxs-lookup"><span data-stu-id="d35e6-142">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="d35e6-143">將 [位置] 設定為 **X = 50**、**Y = 0** 和 **Z = 0**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-143">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="d35e6-144">在開始時將立方體放在離玩家 50 公分處。</span><span class="sxs-lookup"><span data-stu-id="d35e6-144">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="d35e6-145">將 [縮放] 變更為 **X = 0.2**、**Y = 0.2** 和 **Z = 0.2**，以縮小立方體。</span><span class="sxs-lookup"><span data-stu-id="d35e6-145">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="d35e6-146">您將無法看到立方體，除非您將光線新增至場景，這是測試場景前的最後一項工作。</span><span class="sxs-lookup"><span data-stu-id="d35e6-146">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="d35e6-147">切換至 [模式] 面板上的 [光線] 索引標籤，然後將 [定向光線] 拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="d35e6-147">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="d35e6-148">將光線放在 **PlayerStart** 上方，讓您可以看到。</span><span class="sxs-lookup"><span data-stu-id="d35e6-148">Position the light above **PlayerStart** so you can see it.</span></span>

![已新增光線的檢視區](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="d35e6-150">移至 [檔案] > [儲存目前的]、將您的層級命名為 **Main**，然後選取 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-150">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="d35e6-151">設定場景後，請按下工具列中的 [播放]，以查看行動中的立方體！</span><span class="sxs-lookup"><span data-stu-id="d35e6-151">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="d35e6-152">當您完成工作的管理時，請按 **Esc** 以停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="d35e6-152">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![檢視區中的立方體](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="d35e6-154">場景現已完成設定，您可以開始加入棋盤和棋子，以完善應用程式環境。</span><span class="sxs-lookup"><span data-stu-id="d35e6-154">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="d35e6-155">匯入資產</span><span class="sxs-lookup"><span data-stu-id="d35e6-155">Importing assets</span></span>
<span data-ttu-id="d35e6-156">場景目前看起來有點空，但是您會將現成的資產匯入專案，以修正此情況。</span><span class="sxs-lookup"><span data-stu-id="d35e6-156">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="d35e6-157">使用 [7-zip](https://www.7-zip.org/) 下載並解壓縮 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 資產資料夾。</span><span class="sxs-lookup"><span data-stu-id="d35e6-157">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="d35e6-158">從 [內容瀏覽器] 中選取 [新增] > [新增資料夾]，並將其命名為 **ChessAssets**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-158">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="d35e6-159">按兩下您將在其中匯入3D 資產的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="d35e6-159">Double-click the new folder where you'll import the 3D assets.</span></span>

![顯示或隱藏來源面板](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="d35e6-161">從 [內容瀏覽器] 中選取 [匯入]、選取解壓縮資產資料夾中的所有專案，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-161">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="d35e6-162">資產包含適用於棋盤和棋子並採用 FBX 格式的 3D 物件網格，以及將用於材質並採用 TGA 格式的紋理圖。</span><span class="sxs-lookup"><span data-stu-id="d35e6-162">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="d35e6-163">當 [FBX 匯入選項] 視窗快顯時，請展開 [材質] 區段，然後將 [材質匯入方法] 變更為 [不要建立材質]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-163">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="d35e6-164">選取 [全部匯入]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-164">Select **Import All**.</span></span>

![匯入 FBX 選項](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="d35e6-166">您只需針對資產執行這個動作即可。</span><span class="sxs-lookup"><span data-stu-id="d35e6-166">That's all you need to do for the assets.</span></span> <span data-ttu-id="d35e6-167">您的下一組工作是使用藍圖來建立應用程式的建置區塊。</span><span class="sxs-lookup"><span data-stu-id="d35e6-167">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="d35e6-168">新增藍圖</span><span class="sxs-lookup"><span data-stu-id="d35e6-168">Adding blueprints</span></span>

1. <span data-ttu-id="d35e6-169">選取 [內容瀏覽器] 中的 [新增] > [新增資料夾]，並將其命名為 **Blueprints**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-169">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="d35e6-170">如果您不熟悉[藍圖](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)，這些藍圖是特殊資產，可提供節點型介面，用於建立新類型的動作項目和指令碼層級事件。</span><span class="sxs-lookup"><span data-stu-id="d35e6-170">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="d35e6-171">按兩下 [藍圖] 資料夾，然後按一下滑鼠右鍵並選取 [藍圖類別]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-171">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="d35e6-172">選取 [動作項目]，並將藍圖命名為 **Board**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-172">Select **Actor** and name the blueprint **Board**.</span></span> 

![選取您藍圖的父類別](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="d35e6-174">新的 **Board** 藍圖現在會顯示在 **Blueprints** 資料夾中，如下列螢幕擷取畫面中所看到。</span><span class="sxs-lookup"><span data-stu-id="d35e6-174">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![新的棋盤藍圖](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="d35e6-176">您已準備好開始將材質新增至所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="d35e6-176">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="d35e6-177">使用材質</span><span class="sxs-lookup"><span data-stu-id="d35e6-177">Working with materials</span></span>
<span data-ttu-id="d35e6-178">您所建立的物件預設為灰色，這並不好查看。</span><span class="sxs-lookup"><span data-stu-id="d35e6-178">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="d35e6-179">將材質和網格新增至您的物件是本教學課程中的最後一組工作。</span><span class="sxs-lookup"><span data-stu-id="d35e6-179">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="d35e6-180">按兩下 **Board** 以開啟藍圖編輯器。</span><span class="sxs-lookup"><span data-stu-id="d35e6-180">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="d35e6-181">從 [元件] 面板中選取 [新增元件] > [場景]，並將其命名為 **Root**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-181">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="d35e6-182">請注意，**Root** 會在下列螢幕擷取畫面中顯示為 **DefaultSceneRoot** 的子系：</span><span class="sxs-lookup"><span data-stu-id="d35e6-182">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![取代藍圖中的根項目](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="d35e6-184">按一下 **Root** 並將其拖曳至 **DefaultSceneRoot** 以進行取代，然後消除檢視區中的球體。</span><span class="sxs-lookup"><span data-stu-id="d35e6-184">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![取代根項目](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="d35e6-186">從 [元件] 面板中選取 [新增元件] > [靜態網格]，並將其命名為 **SM_Board**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-186">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="d35e6-187">其會在 **Root** 底下顯示為子物件。</span><span class="sxs-lookup"><span data-stu-id="d35e6-187">It will appear as a child object under **Root**.</span></span>

![新增靜態網格](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="d35e6-189">選取 **SM_Board**、向下捲動至 [ 詳細資料] 面板的 [靜態網格] 區段，然後從下拉式清單中選取 **ChessBoard**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-189">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![檢視區中的棋盤網格](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="d35e6-191">仍在 [詳細資料] 面板中，展開 [材質] 區段，然後從下拉式清單中選取 [建立新資產] > [材質]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-191">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="d35e6-192">將材質命名為 **M_ChessBoard**，並將其儲存在 **ChessAssets** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d35e6-192">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![建立新的材質](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="d35e6-194">按兩下 **M_ChessBoard** 材質影像以開啟材質編輯器。</span><span class="sxs-lookup"><span data-stu-id="d35e6-194">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![開啟材質編輯器](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="d35e6-196">在材質編輯器中，按一下滑鼠右鍵，然後搜尋 **紋理範例**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-196">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="d35e6-197">展開 [詳細資料] 面板中的 [材質呈現紋理基底] 區段，然後將 [紋理] 設定為 **ChessBoard_Albedo**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-197">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="d35e6-198">將 **RGB** 輸出釘選拖曳到 **M_ChessBoard** 的 [基本色彩] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-198">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![設定基本色彩](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="d35e6-200">再重複 4 次上述步驟，使用下列設定再建立四個 **紋理範例** 節點：</span><span class="sxs-lookup"><span data-stu-id="d35e6-200">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="d35e6-201">將 [材質] 設定為 **ChessBoard_AO**，並將 **RGB** 連結至 [環境光遮蔽] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-201">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="d35e6-202">將 [材質] 設定為 **ChessBoard_Metal**，並將 **RGB** 連結至 [金屬] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-202">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="d35e6-203">將 [材質] 設定為 **ChessBoard_Normal**，並將 **RGB** 連結至 [一般] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-203">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="d35e6-204">將 [材質] 設定為 **ChessBoard_Rough**，並將 **RGB** 連結至 [粗糙度] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-204">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="d35e6-205">按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="d35e6-205">Click **Save**.</span></span> 

![連結其餘紋理](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="d35e6-207">請先確定您的材質設定看起來像是上述螢幕擷取畫面，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="d35e6-207">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="d35e6-208">填入場景</span><span class="sxs-lookup"><span data-stu-id="d35e6-208">Populating the scene</span></span>
<span data-ttu-id="d35e6-209">如果回到 **Board** 藍圖，您會看到已套用您剛建立的材質。</span><span class="sxs-lookup"><span data-stu-id="d35e6-209">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="d35e6-210">剩下的就是設定場景！</span><span class="sxs-lookup"><span data-stu-id="d35e6-210">All that's left is setting up the scene!</span></span> <span data-ttu-id="d35e6-211">首先，變更下列屬性，以確保棋盤在放入場景時大小合理，且角度正確：</span><span class="sxs-lookup"><span data-stu-id="d35e6-211">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="d35e6-212">將 [縮放] 設定為 **(0.05, 0.05, 0.05)** ，並將 [Z 旋轉] 設定為 **90**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-212">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="d35e6-213">按一下頂端工具列中的 [編譯]，然後按一下 [儲存] 並返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="d35e6-213">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![已套用材質的棋盤](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="d35e6-215">以滑鼠右鍵按一下 [立方體] > [編輯] > [刪除]，然後將 [棋盤] 從 [內容瀏覽器] 拖曳至檢視區。</span><span class="sxs-lookup"><span data-stu-id="d35e6-215">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="d35e6-216">將 [位置] 設定為 **X = 80**、**Y = 0** 和 **Z = 20**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-216">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="d35e6-217">選取 [播放] 按鈕，以在層級中檢視您的新棋盤。</span><span class="sxs-lookup"><span data-stu-id="d35e6-217">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="d35e6-218">按 **Esc** 即可返回編輯器。</span><span class="sxs-lookup"><span data-stu-id="d35e6-218">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="d35e6-219">現在您將遵循相同的步驟來建立棋子，如同您建立棋盤一般：</span><span class="sxs-lookup"><span data-stu-id="d35e6-219">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="d35e6-220">移至 [藍圖] 資料夾、按一下滑鼠右鍵並選取 [藍圖類別]，然後選擇 [動作項目]。</span><span class="sxs-lookup"><span data-stu-id="d35e6-220">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="d35e6-221">將動作項目命名為 **WhiteKing**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-221">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="d35e6-222">按兩下 **WhiteKing** 以在藍圖編輯器中將其開啟、選取 [新增元件] > [場景]，並將其命名為 **Root**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-222">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="d35e6-223">將 **Root** 拖放至 **DefaultSceneRoot**，以將其取代。</span><span class="sxs-lookup"><span data-stu-id="d35e6-223">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="d35e6-224">按一下 [新增元件] > [靜態網格]，並將其命名為 **SM_King**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-224">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="d35e6-225">在 [詳細資料] 面板中，將 [靜態網格] 設定為 **Chess_King**，將 [材質] 設定為名為 **M_ChessWhite** 的新材質。</span><span class="sxs-lookup"><span data-stu-id="d35e6-225">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="d35e6-226">在材質編輯器中開啟 **M_ChessWhite**，並將下列 **紋理範例** 節點連結至下列項目：</span><span class="sxs-lookup"><span data-stu-id="d35e6-226">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="d35e6-227">將 [紋理] 設定為 **ChessWhite_Albedo**，並將 **RGB** 連結至 [基本色彩] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-227">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="d35e6-228">將 [材質] 設定為 **ChessWhite_AO**，並將 **RGB** 連結至 [環境光遮蔽] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="d35e6-229">將 [材質] 設定為 **ChessWhite_Metal**，並將 **RGB** 連結至 [金屬] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="d35e6-230">將 [材質] 設定為 **ChessWhite_Normal**，並將 **RGB** 連結至 [一般] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="d35e6-231">將 [材質] 設定為 **ChessWhite_Rough**，並將 **RGB** 連結至 [粗糙度] 釘選。</span><span class="sxs-lookup"><span data-stu-id="d35e6-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="d35e6-232">按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="d35e6-232">Click **Save**.</span></span> 

<span data-ttu-id="d35e6-233">在繼續之前，您的 **M_ChessKing** 材質應該看起來像是下圖。</span><span class="sxs-lookup"><span data-stu-id="d35e6-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![為國王棋建立材質](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="d35e6-235">您幾乎只需將新的棋子加入場景中就大功告成了：</span><span class="sxs-lookup"><span data-stu-id="d35e6-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="d35e6-236">開啟 **WhiteKing** 藍圖，然後將 [縮放] 變更為 **(0.05, 0.05, 0.05)** ，並將 [Z 旋轉] 設定為 **90**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="d35e6-237">編譯並儲存您的藍圖，然後回到主視窗。</span><span class="sxs-lookup"><span data-stu-id="d35e6-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="d35e6-238">將 **WhiteKing** 拖曳到檢視區、切換至 [世界大綱] 面板，然後將 **WhiteKing** 拖曳至 [棋盤]，使其成為子物件。</span><span class="sxs-lookup"><span data-stu-id="d35e6-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![世界大綱](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="d35e6-240">在 [變形] 底下的 [詳細資料] 面板中，將 **WhiteKing** 的 [位置] 設定為 **X = -26**、**Y = 4** 和 **Z = 0**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="d35e6-241">收工了！</span><span class="sxs-lookup"><span data-stu-id="d35e6-241">That's a wrap!</span></span> <span data-ttu-id="d35e6-242">選取 [播放] 查看您填入的作用中層級，然後在您準備好要結束時，按 **Esc**。</span><span class="sxs-lookup"><span data-stu-id="d35e6-242">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="d35e6-243">您僅僅是建立簡單的專案就牽涉到許多層面，而現在您可以繼續進行本系列的下一個部分：設定混合實境。</span><span class="sxs-lookup"><span data-stu-id="d35e6-243">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="d35e6-244">下一節：3.設定您的專案以進行混合實境</span><span class="sxs-lookup"><span data-stu-id="d35e6-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)