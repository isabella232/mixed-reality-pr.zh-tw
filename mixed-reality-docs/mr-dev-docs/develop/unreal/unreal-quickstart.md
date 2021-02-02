---
title: 建立您的第一個 HoloLens Unreal 應用程式
description: 瞭解如何使用場景物件正確設定 Unreal 專案，並針對 HoloLens 混合現實開發進行輸入互動。
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal、Unreal Engine 4、Unreal editor、UE4、HoloLens、HoloLens 2、mixed reality、開發、檔、指南、功能、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、移植、升級
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421427"
---
# <a name="creating-your-first-hololens-unreal-application"></a><span data-ttu-id="11895-104">建立您的第一個 HoloLens Unreal 應用程式</span><span class="sxs-lookup"><span data-stu-id="11895-104">Creating your first HoloLens Unreal application</span></span>

<span data-ttu-id="11895-105">本指南將逐步引導您在 Unreal 引擎中取得在 HoloLens 上執行的第一個混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="11895-105">This guide will walk you through getting your first Mixed Reality app running on the HoloLens in Unreal Engine.</span></span> <span data-ttu-id="11895-106">在 "Hello World" 的傳統中，您將建立簡單的應用程式，以在螢幕上顯示 cube。</span><span class="sxs-lookup"><span data-stu-id="11895-106">In the tradition of "Hello World", you'll create a simple app that displays a cube on the screen.</span></span> <span data-ttu-id="11895-107">為了讓它更有用，您也會建立第一個手勢來旋轉 cube，並結束應用程式。</span><span class="sxs-lookup"><span data-stu-id="11895-107">To make it more useful, you'll also create your first gesture to rotate the cube and quit the application.</span></span> 

## <a name="objectives"></a><span data-ttu-id="11895-108">目標</span><span class="sxs-lookup"><span data-stu-id="11895-108">Objectives</span></span>

* <span data-ttu-id="11895-109">開始 HoloLens 專案</span><span class="sxs-lookup"><span data-stu-id="11895-109">Start a HoloLens Project</span></span>
* <span data-ttu-id="11895-110">啟用正確的外掛程式</span><span class="sxs-lookup"><span data-stu-id="11895-110">Enable the correct plugins</span></span>
* <span data-ttu-id="11895-111">建立 ARSessionConfig 資料資產</span><span class="sxs-lookup"><span data-stu-id="11895-111">Create an ARSessionConfig Data Asset</span></span>
* <span data-ttu-id="11895-112">設定手勢輸入</span><span class="sxs-lookup"><span data-stu-id="11895-112">Set up gesture inputs</span></span>
* <span data-ttu-id="11895-113">建立基本層級</span><span class="sxs-lookup"><span data-stu-id="11895-113">Build a basic level</span></span>
* <span data-ttu-id="11895-114">執行縮小的手勢</span><span class="sxs-lookup"><span data-stu-id="11895-114">Implement a pinch gesture</span></span>

## <a name="creating-a-new-project"></a><span data-ttu-id="11895-115">建立新的專案</span><span class="sxs-lookup"><span data-stu-id="11895-115">Creating a new project</span></span>

<span data-ttu-id="11895-116">您需要的第一個項目是供您使用的專案。</span><span class="sxs-lookup"><span data-stu-id="11895-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="11895-117">如果您是首次接觸的 Unreal 開發人員，則需要從 Epic Launcher [下載支援檔案](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="11895-117">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="11895-118">啟動 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="11895-118">Launch Unreal Engine</span></span>
2. <span data-ttu-id="11895-119">在 **新的專案類別** 中，選取 [ **遊戲** ]，然後按一下 **[下一步]**：</span><span class="sxs-lookup"><span data-stu-id="11895-119">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![已反白顯示遊戲的 [最近使用的專案] 視窗開啟](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="11895-121">選取 **空白** 範本，然後按 **[下一步]**：</span><span class="sxs-lookup"><span data-stu-id="11895-121">Select the **Blank** template and click **Next**:</span></span>

![醒目提示空白範本的 Unreal 專案瀏覽器視窗](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="11895-123">在 **專案設定** 中，設定 **c + +、可擴充的3d 或2d、行動/平板** 電腦和 **無入門內容**，然後選擇 [儲存位置]，再按一下 [**建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="11895-123">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] 
> <span data-ttu-id="11895-124">您使用的是 c + +，而不是藍圖專案，以便稍後準備使用 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="11895-124">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="11895-125">本快速入門會使用 Unreal 引擎隨附的預設 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="11895-125">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="11895-126">不過，建議您下載並使用官方 Microsoft OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="11895-126">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="11895-127">這需要專案是 c + + 專案。</span><span class="sxs-lookup"><span data-stu-id="11895-127">That requires the project to be a C++ project.</span></span>

![醒目提示專案、效能、目標平臺和入門內容選項的 [專案設定] 視窗](images/unreal-quickstart-img-03.png)

<span data-ttu-id="11895-129">您的新專案應該會自動在 [Unreal 編輯器] 中開啟，這表示您已經準備好進行下一節。</span><span class="sxs-lookup"><span data-stu-id="11895-129">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="11895-130">啟用必要的外掛程式</span><span class="sxs-lookup"><span data-stu-id="11895-130">Enabling required plugins</span></span>

<span data-ttu-id="11895-131">在您開始將物件新增至場景之前，必須啟用兩個外掛程式。</span><span class="sxs-lookup"><span data-stu-id="11895-131">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="11895-132">開啟 [編輯] > [外掛程式]，然後從內建選項清單中選取 [擴增實境]。</span><span class="sxs-lookup"><span data-stu-id="11895-132">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="11895-133">向下滾動至 **HoloLens** 並勾選 [**啟用**]</span><span class="sxs-lookup"><span data-stu-id="11895-133">Scroll down to **HoloLens** and check **Enabled**</span></span>

![開啟並醒目提示 [增強的事實] 區段的 [外掛程式] 視窗](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="11895-135">在右上方的搜尋方塊中輸入 **OpenXR** ，並啟用 **OpenXR** 和 **OpenXRMsftHandInteraction** 外掛程式：</span><span class="sxs-lookup"><span data-stu-id="11895-135">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![已啟用 OpenXR 的外掛程式視窗](images/unreal-quickstart-img-05.jpg)

![啟用 Open XR Msft 手型互動的外掛程式視窗](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="11895-138">重新開機編輯器</span><span class="sxs-lookup"><span data-stu-id="11895-138">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="11895-139">本教學課程使用 OpenXR，但您先前安裝的兩個外掛程式目前未提供適用于 HoloLens 開發的完整功能集。</span><span class="sxs-lookup"><span data-stu-id="11895-139">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="11895-140">HandInteraction 外掛程式可滿足您稍後將會用到的「縮小」手勢，但如果您想要超越基本概念，您必須 [下載 OpenXR 外掛程式](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。</span><span class="sxs-lookup"><span data-stu-id="11895-140">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="11895-141">啟用外掛程式之後，您可以將焦點放在以內容填入。</span><span class="sxs-lookup"><span data-stu-id="11895-141">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="11895-142">建立層級</span><span class="sxs-lookup"><span data-stu-id="11895-142">Creating a level</span></span>

<span data-ttu-id="11895-143">您的下一個工作是建立玩家設定，其中包含一個起點和一個用於參考和調整的立方體。</span><span class="sxs-lookup"><span data-stu-id="11895-143">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="11895-144">選取 [檔案] > [新增層級]，然後選擇 [空白層級]。</span><span class="sxs-lookup"><span data-stu-id="11895-144">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="11895-145">區中的預設場景現在應該是空的</span><span class="sxs-lookup"><span data-stu-id="11895-145">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="11895-146">從 [ **模式** ] 索引標籤中選取 [ **基本** ]，然後將 **PlayerStart** 拖曳到場景中</span><span class="sxs-lookup"><span data-stu-id="11895-146">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="11895-147">在 [ **詳細資料** ] 索引標籤中，將 [ **位置** ] 設定為 **X = 0、Y = 0** 和 **Z = 0** ，以在應用程式啟動時將使用者置於場景的中心</span><span class="sxs-lookup"><span data-stu-id="11895-147">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![已開始新增位置和播放機的 Unreal 編輯器場景](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="11895-149">從 [ **基本** ] 索引標籤中，將 **Cube** 拖曳至場景</span><span class="sxs-lookup"><span data-stu-id="11895-149">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="11895-150">將 cube 的 **位置** 設定為 **X = 50、Y = 0** 和 **Z = 0** ，以在啟動時將 cube 50 cm 移離播放程式</span><span class="sxs-lookup"><span data-stu-id="11895-150">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="11895-151">將 cube 的 **刻度** 變更為 **X = 0.2、Y = 0.2** 和 **Z = 0.2**</span><span class="sxs-lookup"><span data-stu-id="11895-151">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="11895-152">您將無法看到立方體，除非您將光線新增至場景，這是測試場景前的最後一項工作。</span><span class="sxs-lookup"><span data-stu-id="11895-152">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="11895-153">在 [ **模式** ] 面板中，切換至 [ **燈** ] 索引標籤，並將 **方向光線** 拖曳至場景</span><span class="sxs-lookup"><span data-stu-id="11895-153">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="11895-154">將燈光放在 **PlayerStart** 上方，讓您可以看到它</span><span class="sxs-lookup"><span data-stu-id="11895-154">Position the light above **PlayerStart** so you can see it</span></span>

![已新增 cube 和方向光源的 Unreal 編輯器場景](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="11895-156">移至 [檔案] **> 另存新** 檔，將您的等級命名為 **主要**，然後選取 [ **儲存**</span><span class="sxs-lookup"><span data-stu-id="11895-156">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="11895-157">設定場景後，請按下工具列中的 [播放]，以查看行動中的立方體！</span><span class="sxs-lookup"><span data-stu-id="11895-157">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="11895-158">當您完成工作的管理時，請按 Esc 以停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="11895-158">When you're finished admiring your work, press Esc to stop the application.</span></span>

![螢幕中間的立方體在播放模式中的場景](images/unreal-quickstart-img-09.png)

<span data-ttu-id="11895-160">現在已設定場景，讓它準備好用於 AR 的一些基本互動。</span><span class="sxs-lookup"><span data-stu-id="11895-160">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="11895-161">首先，您必須建立 AR 會話，並且可以新增藍圖來啟用手互動。</span><span class="sxs-lookup"><span data-stu-id="11895-161">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="11895-162">新增會話資產</span><span class="sxs-lookup"><span data-stu-id="11895-162">Adding a session asset</span></span>

<span data-ttu-id="11895-163">Unreal 中的 AR 工作階段本身不會發生。</span><span class="sxs-lookup"><span data-stu-id="11895-163">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="11895-164">若要使用工作階段，您需要借助於 ARSessionConfig 資料資產，這就是您接下來的工作：</span><span class="sxs-lookup"><span data-stu-id="11895-164">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="11895-165">在 **內容瀏覽器** 中，選取 [ **加入新的 > 其他 > 資料資產** ]，並確定您是位於根內容資料夾層級</span><span class="sxs-lookup"><span data-stu-id="11895-165">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="11895-166">選取 [ **ARSessionConfig**]，按一下 [ **選取**]，然後將資產命名為 **ARSessionConfig**：</span><span class="sxs-lookup"><span data-stu-id="11895-166">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![已反白顯示 AR 會話設定資產的挑選資料資產類別視窗開啟](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="11895-168">按兩下 [ **ARSessionConfig** ] 將它開啟，並以所有預設設定 **儲存** 並返回主視窗：</span><span class="sxs-lookup"><span data-stu-id="11895-168">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![AR 會話設定資產詳細資料視窗](images/unreal-quickstart-img-11.png)

<span data-ttu-id="11895-170">完成後，您的下一個步驟是確保 AR 工作階段會在層級載入時啟動，並在層級結束時停止。</span><span class="sxs-lookup"><span data-stu-id="11895-170">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="11895-171">值得慶幸的是，Unreal 具有名為 **層級藍圖** 的特殊藍圖，可作為整個層級的全域事件圖形。</span><span class="sxs-lookup"><span data-stu-id="11895-171">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="11895-172">在層級藍圖中連線 ARSessionConfig 資產，保證 AR 工作階段會在遊戲開始玩時立即啟動。</span><span class="sxs-lookup"><span data-stu-id="11895-172">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="11895-173">從編輯器工具列中，選取 [ **藍圖] > 開啟層級藍圖**：</span><span class="sxs-lookup"><span data-stu-id="11895-173">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![已反白顯示開啟層級藍圖選項的藍圖功能表開啟](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="11895-175">將 [執行] 節點 (向左箭號圖示) 關閉 [ **事件 BeginPlay** ] 和 [發行]</span><span class="sxs-lookup"><span data-stu-id="11895-175">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="11895-176">搜尋 **開始 AR 會話節點** ，然後按 enter 鍵</span><span class="sxs-lookup"><span data-stu-id="11895-176">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="11895-177">按一下 [**會話** 設定] 下的 [**選取資產**] 下拉式清單，然後選擇 **ARSessionConfig** 資產</span><span class="sxs-lookup"><span data-stu-id="11895-177">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![具有連線到 start ar 會話函式之事件開始播放的藍圖圖形](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="11895-179">以滑鼠右鍵按一下 EventGraph 中的任一處，並建立新的 [事件 EndPlay] 節點。</span><span class="sxs-lookup"><span data-stu-id="11895-179">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="11895-180">拖曳執行 pin 和版本，然後搜尋 **停止 AR 會話** 節點，然後按 enter 鍵</span><span class="sxs-lookup"><span data-stu-id="11895-180">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="11895-181">點擊 **編譯**，然後 **儲存** 並返回主視窗</span><span class="sxs-lookup"><span data-stu-id="11895-181">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11895-182">如果 AR 工作階段在層級結束時仍在執行，若您在串流至頭戴式裝置時重新啟動應用程式，某些功能可能會停止運作。</span><span class="sxs-lookup"><span data-stu-id="11895-182">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![連接到停止 ar 會話函式的事件結束播放節點](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="11895-184">設定輸入</span><span class="sxs-lookup"><span data-stu-id="11895-184">Setting up inputs</span></span>

1. <span data-ttu-id="11895-185">選取 [ **編輯] > 專案設定** ，並移至 **引擎 > 輸入**</span><span class="sxs-lookup"><span data-stu-id="11895-185">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="11895-186">選取 [ **+** **動作** 對應] 旁的圖示，然後建立 **RightPinch** 和 **LeftPinch** 動作：</span><span class="sxs-lookup"><span data-stu-id="11895-186">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![醒目提示右邊和左方縮小動作對應的系結輸入設定](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="11895-188">將 **RightPinch** 和 **LeftPinch** 動作對應至個別的 **OpenXR Msft 手互動** 動作：</span><span class="sxs-lookup"><span data-stu-id="11895-188">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![醒目提示 Open XR Msft 手型互動選項的動作對應](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a><span data-ttu-id="11895-190">設定手勢</span><span class="sxs-lookup"><span data-stu-id="11895-190">Setting up gestures</span></span>

<span data-ttu-id="11895-191">現在我們已設定好輸入，接下來我們可以看到有趣的部分：加入手勢！</span><span class="sxs-lookup"><span data-stu-id="11895-191">Now that we have setup the inputs, we can get to the exciting part: Adding gestures!</span></span> <span data-ttu-id="11895-192">讓我們在右邊的縮小上旋轉 cube，並在剩餘的縮小時結束應用程式。</span><span class="sxs-lookup"><span data-stu-id="11895-192">Lets rotate the cube on the right pinch and quit the application on left pinch.</span></span>

1. <span data-ttu-id="11895-193">開啟 **層級藍圖** ，並新增 **InputAction RightPinch** 和 **InputAction LeftPinch**</span><span class="sxs-lookup"><span data-stu-id="11895-193">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="11895-194">將適當的縮小事件連接到 **AddActorLocalRotation** ，並 **將目標** 和 **差異旋轉** 設定為 **X = 0、Y = 0** 和 **Z = 20**。</span><span class="sxs-lookup"><span data-stu-id="11895-194">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="11895-195">Cube 現在會在您每次縮小時以20度旋轉</span><span class="sxs-lookup"><span data-stu-id="11895-195">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="11895-196">連接左方的縮小事件以結束 **遊戲**</span><span class="sxs-lookup"><span data-stu-id="11895-196">Connect the left pinch event to **Quit Game**</span></span>

![層級 bluprint 開啟，其中包含右和左縮小事件的輸入動作](images/unreal-quickstart-img-17.jpg)

2. <span data-ttu-id="11895-198">在 cube 的 **轉換** 設定中，將 **行動性** 設定為 **可移動** ，使其可以動態移動：</span><span class="sxs-lookup"><span data-stu-id="11895-198">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![已反白顯示行動性屬性的轉換設定](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="11895-200">您現在已準備好部署和測試應用程式！</span><span class="sxs-lookup"><span data-stu-id="11895-200">At this point, you're ready to deploy and test the application!</span></span>