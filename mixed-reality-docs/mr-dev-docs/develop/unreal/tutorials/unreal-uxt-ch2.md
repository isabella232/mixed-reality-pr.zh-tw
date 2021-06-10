---
title: 2. 初始化您的專案和第一個應用程式
description: 教學課程系列的第 2 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: f7cf43e8f1c040660b6a2688e234a271bc071b00
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712641"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="56854-104">2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="56854-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="56854-105">在第一個教學課程中，您將著手進行新的 Unreal 項目，並啟用 HoloLens 外掛程式、建立和亮顯層級，以及新增棋子。</span><span class="sxs-lookup"><span data-stu-id="56854-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="56854-106">您將對所有 3D 物件和材質使用預先製作的資產，因此無須擔心自行建立模型的問題。</span><span class="sxs-lookup"><span data-stu-id="56854-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="56854-107">在本教學課程結束時，您將會有一個可供混合實境使用的空白畫布。</span><span class="sxs-lookup"><span data-stu-id="56854-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56854-108">請確定您擁有[開始使用](/windows/mixed-reality/unreal-uxt-ch1)頁面中的所有必要項目。</span><span class="sxs-lookup"><span data-stu-id="56854-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="56854-109">目標</span><span class="sxs-lookup"><span data-stu-id="56854-109">Objectives</span></span>

* <span data-ttu-id="56854-110">設定 Unreal 專案以用於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="56854-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="56854-111">匯入資產和設定場景</span><span class="sxs-lookup"><span data-stu-id="56854-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="56854-112">使用藍圖建立動作項目和指令碼層級事件</span><span class="sxs-lookup"><span data-stu-id="56854-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="56854-113">建立新的 Unreal 專案</span><span class="sxs-lookup"><span data-stu-id="56854-113">Creating a new Unreal project</span></span>

<span data-ttu-id="56854-114">您需要的第一個項目是供您使用的專案。</span><span class="sxs-lookup"><span data-stu-id="56854-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="56854-115">如果您是首次接觸的 Unreal 開發人員，則需要從 Epic Launcher [下載支援檔案](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="56854-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="56854-116">啟動 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="56854-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="56854-117">在 [新增專案類別] 中選取 [遊戲]，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="56854-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![選取遊戲專案範本](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="56854-119">選取 **空白** 範本，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="56854-119">Select the **Blank** Template and click **Next**.</span></span> 

![選取空白範本](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="56854-121">將 [C++]、[可縮放 3D 或 2D]、[行動裝置/平板電腦] 及 [無起始內容] 設為您的 [專案設定]，然後選擇儲存位置並按一下 [建立專案]。</span><span class="sxs-lookup"><span data-stu-id="56854-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="56854-122">您必須選取 C++ 專案 (而非藍圖專案) 以建置 UX 工具外掛程式 (您稍後將在第 4 節設定此外掛程式)。</span><span class="sxs-lookup"><span data-stu-id="56854-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![初始專案設定](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="56854-124">專案應該會自動在 Unreal 編輯器中開啟，這表示您已準備好進行下一節。</span><span class="sxs-lookup"><span data-stu-id="56854-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="56854-125">啟用必要的外掛程式</span><span class="sxs-lookup"><span data-stu-id="56854-125">Enabling required plugins</span></span>

<span data-ttu-id="56854-126">若要使用可透過 Microsoft 的混合現實平臺取得的功能，您必須先安裝並啟用 Microsoft OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="56854-126">In order to use the features available via Microsoft's mixed reality platform, you'll first need to install and enable the Microsoft OpenXR plugin.</span></span> <span data-ttu-id="56854-127">若要深入瞭解此外掛程式，您可以在 [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal)上查看專案。</span><span class="sxs-lookup"><span data-stu-id="56854-127">To learn more about the plugin, you can check out the project on [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

1. <span data-ttu-id="56854-128">開啟 [長篇比賽] 啟動器。</span><span class="sxs-lookup"><span data-stu-id="56854-128">Open the Epic Games Launcher.</span></span> <span data-ttu-id="56854-129">流覽至 Unreal Engine Marketplace 並搜尋「[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)」。</span><span class="sxs-lookup"><span data-stu-id="56854-129">Navigate to Unreal Engine Marketplace and search for "[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)".</span></span> <span data-ttu-id="56854-130">將外掛程式安裝到您的引擎。</span><span class="sxs-lookup"><span data-stu-id="56854-130">Install the plugin to your engine.</span></span>

![Unreal Marketplace](images/unreal-uxt/2-openxr-plugin.PNG)

2. <span data-ttu-id="56854-132">回到 [Unreal 編輯器]，移至 [**專案設定**]  >  **外掛程式**，然後搜尋 "Microsoft OpenXR"。</span><span class="sxs-lookup"><span data-stu-id="56854-132">Back in the Unreal editor, go to **Project Settings** > **Plugins** and search for "Microsoft OpenXR".</span></span> <span data-ttu-id="56854-133">確定已啟用外掛程式，並在出現提示時重新開機編輯器。</span><span class="sxs-lookup"><span data-stu-id="56854-133">Ensure the plugin is enabled and restart the editor if prompted.</span></span>

![啟用 Microsoft OpenXR 外掛程式](images/unreal-uxt/2-enable-plugin.PNG)

<span data-ttu-id="56854-135">啟用 Microsoft OpenXR 外掛程式將會自動啟用混合現實開發所需的所有其他外掛程式。</span><span class="sxs-lookup"><span data-stu-id="56854-135">Enabling the Microsoft OpenXR plugin will automatically enable all the other plugins required for mixed reality development.</span></span> <span data-ttu-id="56854-136">請注意，必須停用 "Microsoft Windows Mixed Reality" 外掛程式，才能使用 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="56854-136">Note that the "Microsoft Windows Mixed Reality" plugin must be disabled in order to use OpenXR.</span></span> 

## <a name="creating-a-level"></a><span data-ttu-id="56854-137">建立層級</span><span class="sxs-lookup"><span data-stu-id="56854-137">Creating a level</span></span>
<span data-ttu-id="56854-138">您的下一個工作是建立玩家設定，其中包含一個起點和一個用於參考和調整的立方體。</span><span class="sxs-lookup"><span data-stu-id="56854-138">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="56854-139">選取 [檔案] > [新增層級]，然後選擇 [空白層級]。</span><span class="sxs-lookup"><span data-stu-id="56854-139">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="56854-140">檢視區中的預設場景現在應該是空白的。</span><span class="sxs-lookup"><span data-stu-id="56854-140">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="56854-141">從 [模式] 索引標籤中選取 [基本]，然後將 **PlayerStart** 拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="56854-141">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="56854-142">在 [詳細資料] 索引標籤中，將 [位置] 設定為 **X = 0**、**Y = 0** 和 **Z = 0**，這會在應用程式啟動時，將使用者設釘在場景中心。</span><span class="sxs-lookup"><span data-stu-id="56854-142">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![具有 PlayerStart 的檢視區](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="56854-144">將 [立方體] 從 [基本] 索引標籤拖曳到場景。</span><span class="sxs-lookup"><span data-stu-id="56854-144">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="56854-145">將 [位置] 設定為 **X = 50**、**Y = 0** 和 **Z = 0**。</span><span class="sxs-lookup"><span data-stu-id="56854-145">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="56854-146">在開始時將立方體放在離玩家 50 公分處。</span><span class="sxs-lookup"><span data-stu-id="56854-146">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="56854-147">將 [縮放] 變更為 **X = 0.2**、**Y = 0.2** 和 **Z = 0.2**，以縮小立方體。</span><span class="sxs-lookup"><span data-stu-id="56854-147">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="56854-148">您將無法看到立方體，除非您將光線新增至場景，這是測試場景前的最後一項工作。</span><span class="sxs-lookup"><span data-stu-id="56854-148">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="56854-149">切換至 [模式] 面板上的 [光線] 索引標籤，然後將 [定向光線] 拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="56854-149">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="56854-150">將光線放在 **PlayerStart** 上方，讓您可以看到。</span><span class="sxs-lookup"><span data-stu-id="56854-150">Position the light above **PlayerStart** so you can see it.</span></span>

![已新增光線的檢視區](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="56854-152">移至 [檔案] > [儲存目前的]、將您的層級命名為 **Main**，然後選取 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="56854-152">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="56854-153">設定場景後，請按下工具列中的 [播放]，以查看行動中的立方體！</span><span class="sxs-lookup"><span data-stu-id="56854-153">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="56854-154">當您完成工作的管理時，請按 **Esc** 以停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="56854-154">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![檢視區中的立方體](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="56854-156">場景現已完成設定，您可以開始加入棋盤和棋子，以完善應用程式環境。</span><span class="sxs-lookup"><span data-stu-id="56854-156">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="56854-157">匯入資產</span><span class="sxs-lookup"><span data-stu-id="56854-157">Importing assets</span></span>
<span data-ttu-id="56854-158">場景目前看起來有點空，但是您會將現成的資產匯入專案，以修正此情況。</span><span class="sxs-lookup"><span data-stu-id="56854-158">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="56854-159">使用 [7-zip](https://www.7-zip.org/) 下載並解壓縮 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 資產資料夾。</span><span class="sxs-lookup"><span data-stu-id="56854-159">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="56854-160">從 [內容瀏覽器] 中選取 [新增] > [新增資料夾]，並將其命名為 **ChessAssets**。</span><span class="sxs-lookup"><span data-stu-id="56854-160">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="56854-161">按兩下您將在其中匯入3D 資產的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="56854-161">Double-click the new folder where you'll import the 3D assets.</span></span>

![顯示或隱藏來源面板](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="56854-163">從 [內容瀏覽器] 中選取 [匯入]、選取解壓縮資產資料夾中的所有專案，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="56854-163">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="56854-164">資產包含適用於棋盤和棋子並採用 FBX 格式的 3D 物件網格，以及將用於材質並採用 TGA 格式的紋理圖。</span><span class="sxs-lookup"><span data-stu-id="56854-164">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="56854-165">當 [FBX 匯入選項] 視窗快顯時，請展開 [材質] 區段，然後將 [材質匯入方法] 變更為 [不要建立材質]。</span><span class="sxs-lookup"><span data-stu-id="56854-165">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="56854-166">選取 [全部匯入]。</span><span class="sxs-lookup"><span data-stu-id="56854-166">Select **Import All**.</span></span>

![匯入 FBX 選項](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="56854-168">您只需針對資產執行這個動作即可。</span><span class="sxs-lookup"><span data-stu-id="56854-168">That's all you need to do for the assets.</span></span> <span data-ttu-id="56854-169">您的下一組工作是使用藍圖來建立應用程式的建置區塊。</span><span class="sxs-lookup"><span data-stu-id="56854-169">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="56854-170">新增藍圖</span><span class="sxs-lookup"><span data-stu-id="56854-170">Adding blueprints</span></span>

1. <span data-ttu-id="56854-171">選取 [內容瀏覽器] 中的 [新增] > [新增資料夾]，並將其命名為 **Blueprints**。</span><span class="sxs-lookup"><span data-stu-id="56854-171">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="56854-172">如果您不熟悉[藍圖](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)，這些藍圖是特殊資產，可提供節點型介面，用於建立新類型的動作項目和指令碼層級事件。</span><span class="sxs-lookup"><span data-stu-id="56854-172">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="56854-173">按兩下 [藍圖] 資料夾，然後按一下滑鼠右鍵並選取 [藍圖類別]。</span><span class="sxs-lookup"><span data-stu-id="56854-173">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="56854-174">選取 [動作項目]，並將藍圖命名為 **Board**。</span><span class="sxs-lookup"><span data-stu-id="56854-174">Select **Actor** and name the blueprint **Board**.</span></span> 

![選取您藍圖的父類別](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="56854-176">新的 **Board** 藍圖現在會顯示在 **Blueprints** 資料夾中，如下列螢幕擷取畫面中所看到。</span><span class="sxs-lookup"><span data-stu-id="56854-176">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![新的棋盤藍圖](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="56854-178">您已準備好開始將材質新增至所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="56854-178">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="56854-179">使用材質</span><span class="sxs-lookup"><span data-stu-id="56854-179">Working with materials</span></span>
<span data-ttu-id="56854-180">您所建立的物件預設為灰色，這並不好查看。</span><span class="sxs-lookup"><span data-stu-id="56854-180">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="56854-181">將材質和網格新增至您的物件是本教學課程中的最後一組工作。</span><span class="sxs-lookup"><span data-stu-id="56854-181">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="56854-182">按兩下 **Board** 以開啟藍圖編輯器。</span><span class="sxs-lookup"><span data-stu-id="56854-182">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="56854-183">從 [元件] 面板中選取 [新增元件] > [場景]，並將其命名為 **Root**。</span><span class="sxs-lookup"><span data-stu-id="56854-183">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="56854-184">請注意，**Root** 會在下列螢幕擷取畫面中顯示為 **DefaultSceneRoot** 的子系：</span><span class="sxs-lookup"><span data-stu-id="56854-184">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![取代藍圖中的根項目](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="56854-186">按一下 **Root** 並將其拖曳至 **DefaultSceneRoot** 以進行取代，然後消除檢視區中的球體。</span><span class="sxs-lookup"><span data-stu-id="56854-186">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![取代根項目](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="56854-188">從 [元件] 面板中選取 [新增元件] > [靜態網格]，並將其命名為 **SM_Board**。</span><span class="sxs-lookup"><span data-stu-id="56854-188">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="56854-189">其會在 **Root** 底下顯示為子物件。</span><span class="sxs-lookup"><span data-stu-id="56854-189">It will appear as a child object under **Root**.</span></span>

![新增靜態網格](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="56854-191">選取 **SM_Board**、向下捲動至 [ 詳細資料] 面板的 [靜態網格] 區段，然後從下拉式清單中選取 **ChessBoard**。</span><span class="sxs-lookup"><span data-stu-id="56854-191">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![檢視區中的棋盤網格](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="56854-193">仍在 [詳細資料] 面板中，展開 [材質] 區段，然後從下拉式清單中選取 [建立新資產] > [材質]。</span><span class="sxs-lookup"><span data-stu-id="56854-193">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="56854-194">將材質命名為 **M_ChessBoard**，並將其儲存在 **ChessAssets** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="56854-194">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![建立新的材質](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="56854-196">按兩下 **M_ChessBoard** 材質影像以開啟材質編輯器。</span><span class="sxs-lookup"><span data-stu-id="56854-196">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![開啟材質編輯器](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="56854-198">在材質編輯器中，按一下滑鼠右鍵，然後搜尋 **紋理範例**。</span><span class="sxs-lookup"><span data-stu-id="56854-198">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="56854-199">展開 [詳細資料] 面板中的 [材質呈現紋理基底] 區段，然後將 [紋理] 設定為 **ChessBoard_Albedo**。</span><span class="sxs-lookup"><span data-stu-id="56854-199">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="56854-200">將 **RGB** 輸出釘選拖曳到 **M_ChessBoard** 的 [基本色彩] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-200">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![設定基本色彩](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="56854-202">再重複 4 次上述步驟，使用下列設定再建立四個 **紋理範例** 節點：</span><span class="sxs-lookup"><span data-stu-id="56854-202">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="56854-203">將 [材質] 設定為 **ChessBoard_AO**，並將 **RGB** 連結至 [環境光遮蔽] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-203">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="56854-204">將 [材質] 設定為 **ChessBoard_Metal**，並將 **RGB** 連結至 [金屬] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-204">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="56854-205">將 [材質] 設定為 **ChessBoard_Normal**，並將 **RGB** 連結至 [一般] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-205">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="56854-206">將 [材質] 設定為 **ChessBoard_Rough**，並將 **RGB** 連結至 [粗糙度] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-206">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="56854-207">按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="56854-207">Click **Save**.</span></span> 

![連結其餘紋理](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="56854-209">請先確定您的材質設定看起來像是上述螢幕擷取畫面，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="56854-209">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="56854-210">填入場景</span><span class="sxs-lookup"><span data-stu-id="56854-210">Populating the scene</span></span>
<span data-ttu-id="56854-211">如果回到 **Board** 藍圖，您會看到已套用您剛建立的材質。</span><span class="sxs-lookup"><span data-stu-id="56854-211">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="56854-212">剩下的就是設定場景！</span><span class="sxs-lookup"><span data-stu-id="56854-212">All that's left is setting up the scene!</span></span> <span data-ttu-id="56854-213">首先，變更下列屬性，以確保棋盤在放入場景時大小合理，且角度正確：</span><span class="sxs-lookup"><span data-stu-id="56854-213">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="56854-214">將 [縮放] 設定為 **(0.05, 0.05, 0.05)** ，並將 [Z 旋轉] 設定為 **90**。</span><span class="sxs-lookup"><span data-stu-id="56854-214">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="56854-215">按一下頂端工具列中的 [編譯]，然後按一下 [儲存] 並返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="56854-215">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![已套用材質的棋盤](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="56854-217">以滑鼠右鍵按一下 [立方體] > [編輯] > [刪除]，然後將 [棋盤] 從 [內容瀏覽器] 拖曳至檢視區。</span><span class="sxs-lookup"><span data-stu-id="56854-217">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="56854-218">將 [位置] 設定為 **X = 80**、**Y = 0** 和 **Z = 20**。</span><span class="sxs-lookup"><span data-stu-id="56854-218">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="56854-219">選取 [播放] 按鈕，以在層級中檢視您的新棋盤。</span><span class="sxs-lookup"><span data-stu-id="56854-219">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="56854-220">按 **Esc** 即可返回編輯器。</span><span class="sxs-lookup"><span data-stu-id="56854-220">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="56854-221">現在您將遵循相同的步驟來建立棋子，如同您建立棋盤一般：</span><span class="sxs-lookup"><span data-stu-id="56854-221">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="56854-222">移至 [藍圖] 資料夾、按一下滑鼠右鍵並選取 [藍圖類別]，然後選擇 [動作項目]。</span><span class="sxs-lookup"><span data-stu-id="56854-222">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="56854-223">將動作項目命名為 **WhiteKing**。</span><span class="sxs-lookup"><span data-stu-id="56854-223">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="56854-224">按兩下 **WhiteKing** 以在藍圖編輯器中將其開啟、選取 [新增元件] > [場景]，並將其命名為 **Root**。</span><span class="sxs-lookup"><span data-stu-id="56854-224">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="56854-225">將 **Root** 拖放至 **DefaultSceneRoot**，以將其取代。</span><span class="sxs-lookup"><span data-stu-id="56854-225">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="56854-226">按一下 [新增元件] > [靜態網格]，並將其命名為 **SM_King**。</span><span class="sxs-lookup"><span data-stu-id="56854-226">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="56854-227">在 [詳細資料] 面板中，將 [靜態網格] 設定為 **Chess_King**，將 [材質] 設定為名為 **M_ChessWhite** 的新材質。</span><span class="sxs-lookup"><span data-stu-id="56854-227">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="56854-228">在材質編輯器中開啟 **M_ChessWhite**，並將下列 **紋理範例** 節點連結至下列項目：</span><span class="sxs-lookup"><span data-stu-id="56854-228">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="56854-229">將 [紋理] 設定為 **ChessWhite_Albedo**，並將 **RGB** 連結至 [基本色彩] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-229">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="56854-230">將 [材質] 設定為 **ChessWhite_AO**，並將 **RGB** 連結至 [環境光遮蔽] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-230">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="56854-231">將 [材質] 設定為 **ChessWhite_Metal**，並將 **RGB** 連結至 [金屬] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-231">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="56854-232">將 [材質] 設定為 **ChessWhite_Normal**，並將 **RGB** 連結至 [一般] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-232">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="56854-233">將 [材質] 設定為 **ChessWhite_Rough**，並將 **RGB** 連結至 [粗糙度] 釘選。</span><span class="sxs-lookup"><span data-stu-id="56854-233">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="56854-234">按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="56854-234">Click **Save**.</span></span> 

<span data-ttu-id="56854-235">在繼續之前，您的 **M_ChessKing** 材質應該看起來像是下圖。</span><span class="sxs-lookup"><span data-stu-id="56854-235">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![為國王棋建立材質](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="56854-237">您幾乎只需將新的棋子加入場景中就大功告成了：</span><span class="sxs-lookup"><span data-stu-id="56854-237">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="56854-238">開啟 **WhiteKing** 藍圖，然後將 [縮放] 變更為 **(0.05, 0.05, 0.05)** ，並將 [Z 旋轉] 設定為 **90**。</span><span class="sxs-lookup"><span data-stu-id="56854-238">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="56854-239">編譯並儲存您的藍圖，然後回到主視窗。</span><span class="sxs-lookup"><span data-stu-id="56854-239">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="56854-240">將 **WhiteKing** 拖曳到檢視區、切換至 [世界大綱] 面板，然後將 **WhiteKing** 拖曳至 [棋盤]，使其成為子物件。</span><span class="sxs-lookup"><span data-stu-id="56854-240">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![世界大綱](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="56854-242">在 [變形] 底下的 [詳細資料] 面板中，將 **WhiteKing** 的 [位置] 設定為 **X = -26**、**Y = 4** 和 **Z = 0**。</span><span class="sxs-lookup"><span data-stu-id="56854-242">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="56854-243">收工了！</span><span class="sxs-lookup"><span data-stu-id="56854-243">That's a wrap!</span></span> <span data-ttu-id="56854-244">選取 [播放] 查看您填入的作用中層級，然後在您準備好要結束時，按 **Esc**。</span><span class="sxs-lookup"><span data-stu-id="56854-244">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="56854-245">您僅僅是建立簡單的專案就牽涉到許多層面，而現在您可以繼續進行本系列的下一個部分：設定混合實境。</span><span class="sxs-lookup"><span data-stu-id="56854-245">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="56854-246">下一節：3.設定您的專案以進行混合實境</span><span class="sxs-lookup"><span data-stu-id="56854-246">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)