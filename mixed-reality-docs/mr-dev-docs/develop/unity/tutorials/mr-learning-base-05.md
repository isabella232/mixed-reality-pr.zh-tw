---
title: 使用解算器建立動態內容
description: 本課程說明如何使用混合實境工具組 (MRTK) 解算器來建立動態內容。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, 解算器
ms.localizationpriority: high
ms.openlocfilehash: 5e231fe91c96dc8b6a7c07c6fdbc2c07286d6ab2
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982981"
---
# <a name="5-creating-dynamic-content-using-solvers"></a><span data-ttu-id="c76d3-104">5.使用解算器建立動態內容</span><span class="sxs-lookup"><span data-stu-id="c76d3-104">5. Creating dynamic content using Solvers</span></span>

<span data-ttu-id="c76d3-105">在本教學課程中，您將會探索如何使用 MRTK 的可用放置工具 (也就是解算器) 來動態地放置全像投影，以解決複雜的空間放置案例。</span><span class="sxs-lookup"><span data-stu-id="c76d3-105">In this tutorial, you will explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="c76d3-106">在 MRTK 中，解算器是指令碼和行為的系統，用來允許物件在場景中追蹤您、使用者或其他遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="c76d3-106">In the MRTK, Solvers are a system of scripts and behaviors used to allow objects to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="c76d3-107">也可用來對齊特定位置，讓您的應用程式更具直覺性。</span><span class="sxs-lookup"><span data-stu-id="c76d3-107">They can also be used to snap to certain positions, making your app more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="c76d3-108">目標</span><span class="sxs-lookup"><span data-stu-id="c76d3-108">Objectives</span></span>

* <span data-ttu-id="c76d3-109">導入 MRTK 的解算器</span><span class="sxs-lookup"><span data-stu-id="c76d3-109">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="c76d3-110">了解如何使用解算器將使用者引導至物件</span><span class="sxs-lookup"><span data-stu-id="c76d3-110">Learn how to use Solvers to direct the user to objects</span></span>
* <span data-ttu-id="c76d3-111">了解如何使用解算器來重新放置物件</span><span class="sxs-lookup"><span data-stu-id="c76d3-111">Learn how to use Solvers to reposition objects</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="c76d3-112">MRTK 中的解算器位置</span><span class="sxs-lookup"><span data-stu-id="c76d3-112">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="c76d3-113">MRTK 的解算器位於 MRTK SDK 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c76d3-113">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="c76d3-114">若要查看專案中的可用解析器，請在 [專案] 視窗中，流覽至 [**封裝**  >  **混合現實工具組 Foundation**  >  **SDK**  >  **功能**  >  **公用程式**  >  **解析器**：</span><span class="sxs-lookup"><span data-stu-id="c76d3-114">To see the available Solvers in your project, in the Project window, navigate to **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![已選取 [解算器] 資料夾的 Unity [專案] 視窗](images/mr-learning-base/base-05-section1-step1-1.png)

<span data-ttu-id="c76d3-116">在本教學課程中，我們將檢閱「方向性指標解算器」和「點選放置解算器」的實作。</span><span class="sxs-lookup"><span data-stu-id="c76d3-116">In this tutorial, we will review the implementation of the Directional Indicator Solver and the Tap To Place Solver.</span></span> <span data-ttu-id="c76d3-117">若要深入了解 MRTK 中可用的完整解算器範圍，您可以參閱 [MRTK 文件入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的[解算器](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md)指南。</span><span class="sxs-lookup"><span data-stu-id="c76d3-117">To learn more about the full range of Solvers available in the MRTK, you can refer to the [Solvers](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

> [!NOTE]
> <span data-ttu-id="c76d3-118">方向性指標的求解器不在上述的解析器資料夾中，但在套件 > 混合現實工具組 Foundation > SDK > 實驗性 > 功能 > 公用程式資料夾，因為這是實驗性的功能。</span><span class="sxs-lookup"><span data-stu-id="c76d3-118">The Directional Indicator Solver is not located in the Solvers folders referenced above, but in the Packages > Mixed Reality Toolkit Foundation > SDK > Experimental > Features > Utilities folders, because it is an experimental feature.</span></span>

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a><span data-ttu-id="c76d3-119">使用「方向性指標解算器」將使用者導向至物件</span><span class="sxs-lookup"><span data-stu-id="c76d3-119">Using the Directional Indicator Solver to direct the user to objects</span></span>

<span data-ttu-id="c76d3-120">在 [專案] 視窗中，瀏覽至 [資產]  >  [MRTK.Tutorials.GettingStarted]  >  [Prefabs] 資料夾，按一下 [Chevron] Prefab 並將其拖曳至 [階層] 視窗，將其轉換 [位置] 設定為 X = 0、Y = 0、Z = 2，以將其放在 RoverExplorer 物件附近：</span><span class="sxs-lookup"><span data-stu-id="c76d3-120">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **Chevron** prefab into the Hierarchy window, and set it's Transform **Position** to X = 0, Y = 0, Z = 2 to position it near the RoverExplorer object:</span></span>

![已選取新加入 Chevron Prefab 的 Unity](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="c76d3-122">如果您發現場景中的相機或任何其他圖示隱藏了物件，或造成混亂，您可以藉由<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切換 Gizmos</a> 為關閉位置來隱藏這些物件，如上圖所示。</span><span class="sxs-lookup"><span data-stu-id="c76d3-122">If you find that the camera or any other icons in your scene are hiding the objects or are distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span> <span data-ttu-id="c76d3-123">若要深入了解 Gizmos 功能表，以及如何使用其來最佳化場景檢視，您可以參閱 Unity 的 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos 功能表</a>文件。</span><span class="sxs-lookup"><span data-stu-id="c76d3-123">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>

<span data-ttu-id="c76d3-124">將新增的 Chevron 物件 **Indicator** 重新命名，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增 **DirectionalIndicator**：</span><span class="sxs-lookup"><span data-stu-id="c76d3-124">Rename the newly added Chevron object **Indicator**, then in the Inspector window, use the **Add Component** button to add the **DirectionalIndicator**:</span></span>

![已新增 DirectionalIndicator 解算器元件的 Unity](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="c76d3-126">當您新增解算器時 (在此案例中為 DirectionalIndicator 元件)，Solver Handler 元件也會自動新增，因為解算器需要此元件。</span><span class="sxs-lookup"><span data-stu-id="c76d3-126">When you add a Solver, in this case, the DirectionalIndicator component, the SolverHandler component is automatically added because Solvers require it.</span></span>

> [!NOTE]
> <span data-ttu-id="c76d3-127">Directional Indicator Controller (指令碼) 不是 MRTK 的一部分，但已包含在教學課程資產中。</span><span class="sxs-lookup"><span data-stu-id="c76d3-127">The Directional Indicator Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="c76d3-128">設定 DirectionalIndicator 和 SolverHandler 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c76d3-128">Configure the DirectionalIndicator and SolverHandler components as follows:</span></span>

* <span data-ttu-id="c76d3-129">確認 **SolverHandler** 元件的 [追蹤目標類型] 設定為 [頭部]</span><span class="sxs-lookup"><span data-stu-id="c76d3-129">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="c76d3-130">藉由將其從 [階層] 視窗拖曳至 [無 (轉換)]  欄位，將 **RoverExplorer** 指派至 **DirectionalIndicator** 元件的 **方向目標**</span><span class="sxs-lookup"><span data-stu-id="c76d3-130">Assign the **RoverExplorer** to the **DirectionalIndicator** component's **Directional Target** by dragging it from the Hierarchy window into the **None (Transform)** field</span></span>
* <span data-ttu-id="c76d3-131">將 [檢視位移] 變更為 0.2</span><span class="sxs-lookup"><span data-stu-id="c76d3-131">Change the **View Offset** to 0.2</span></span>

![已設定 DirectionalIndicator 解算器元件的 Unity](images/mr-learning-base/base-05-section2-step1-3.png)

<span data-ttu-id="c76d3-133">按下 [開始遊戲] 按鈕進入遊戲模式，在向左或向右移動滑鼠時按住滑鼠右鍵來旋轉您的注視方向，同時注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="c76d3-133">Press the Play button to enter Game mode, press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="c76d3-134">當您查看 RoverExplorer 物件時，指標物件會出現並指向 RoverExplorer 物件</span><span class="sxs-lookup"><span data-stu-id="c76d3-134">When you look away from the RoverExplorer object, the Indicator object will appear and point towards the RoverExplorer object</span></span>

![正在使用 DirectionalIndicator 解算器的 Unity 播放模式分割檢視](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="c76d3-136">如果您沒有在場景視窗中看到相機光線，請確定您已啟用 [Gizmos] 功能表，如上圖中所示。</span><span class="sxs-lookup"><span data-stu-id="c76d3-136">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled, as shown in the image above.</span></span>

> [!TIP]
> <span data-ttu-id="c76d3-137">若要了解如何使用編輯器內的輸入模擬，您可以參考 [MRTK 文件入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的[使用編輯器內的手動輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。</span><span class="sxs-lookup"><span data-stu-id="c76d3-137">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

> [!TIP]
> <span data-ttu-id="c76d3-138">如果您的電腦有麥克風，您可以使用語音命令「切換診斷」，輕鬆地切換出現在 [遊戲] 視窗中的 [診斷] 面板作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="c76d3-138">If your computer has a microphone, you can easily toggle the active state of the Diagnostics panel that appears in the Game window by using the speech command "toggle diagnostics."</span></span> <span data-ttu-id="c76d3-139">或者，您也可以在 [MRTK 組態設定檔] > [診斷] > [啟用診斷系統] 中加以停用。</span><span class="sxs-lookup"><span data-stu-id="c76d3-139">Alternatively, you can disable it in the MRTK Configuration Profile > Diagnostics > Enable Diagnostics System.</span></span> <span data-ttu-id="c76d3-140">不過，通常建議您在開發期間讓診斷系統保持作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="c76d3-140">However, it is generally recommended to keep the Diagnostics System active during development.</span></span>

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a><span data-ttu-id="c76d3-141">使用「點選放置解算器」來調整物件的位置</span><span class="sxs-lookup"><span data-stu-id="c76d3-141">Using the Tap to Place Solver to reposition objects</span></span>

<span data-ttu-id="c76d3-142">在 [階層] 視窗中選取 [RoverExplorer] > **RoverAssembly** 物件，然後在 [偵測器] 視窗中使用 [新增元件] 按鈕來新增 **Tap To Place (指令碼)** 元件，並進行以下設定：</span><span class="sxs-lookup"><span data-stu-id="c76d3-142">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **Tap To Place (Script)** component, and configure it as follows:</span></span>

* <span data-ttu-id="c76d3-143">確認 **SolverHandler** 元件的 [追蹤目標類型] 設定為 [頭部]</span><span class="sxs-lookup"><span data-stu-id="c76d3-143">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="c76d3-144">取消核取 [ **使用預設介面正常位移** ]，並確定 [ **表面一般位移** ] 設定為0。</span><span class="sxs-lookup"><span data-stu-id="c76d3-144">Uncheck the **Use Default Surface Normal Offset** and ensure **Surface Normal Offset** is set to 0</span></span>
* <span data-ttu-id="c76d3-145">勾選 [保持垂直方向] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="c76d3-145">Check the **Keep Orientation Vertical** checkbox</span></span>
* <span data-ttu-id="c76d3-146">從 [磁性表面]  >  [元素 0] 下拉式清單中，取消選取 [空間感知] 以外的所有選項</span><span class="sxs-lookup"><span data-stu-id="c76d3-146">From the **Magnetic Surfaces** > **Element 0** dropdown, uncheck all options expect **Spatial Awareness**</span></span>

![已新增和設定 TapToPlace 解算器元件的 Unity](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="c76d3-148">[磁性表面] 設定會決定放置物件時，Tap To Place (指令碼) 元件可以偵測哪些物件。</span><span class="sxs-lookup"><span data-stu-id="c76d3-148">The Magnetic Surfaces setting determines which objects the Tap To Place (Script) component can detect when placing an object.</span></span> <span data-ttu-id="c76d3-149">藉由將設定變更為僅限 [空間感知]，Tap To Place (指令碼) 元件就只能將 Rover 放在名為「空間感知」的 Unity 層物件上，其預設為 HoloLens 所產生的空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="c76d3-149">By changing the setting to only Spatial Awareness, the Tap To Place (Script) component will only be able to place the Rover on objects on the Unity Layer named Spatial Awareness, which by default is the Spatial Awareness Mesh generated by the HoloLens.</span></span>
>
><span data-ttu-id="c76d3-150">若要深入了解層級，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">層</a>文件。</span><span class="sxs-lookup"><span data-stu-id="c76d3-150">To learn more about Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Layers</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="c76d3-151">如果您想要在 HoloLens 上測試「點選放置」功能時查看「空間感知網格」，您可以暫時將空間網格觀察器的顯示選項設定為 [可見]。</span><span class="sxs-lookup"><span data-stu-id="c76d3-151">If you want to see the Spatial Awareness Mesh when testing the Tap To Place functionality on your HoloLens, you can temporarily set the Spatial Mesh Observer's Display Option to Visible.</span></span> <span data-ttu-id="c76d3-152">如需有關如何變更顯示選項的提醒，您可以參閱[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)指示。</span><span class="sxs-lookup"><span data-stu-id="c76d3-152">For a reminder on how to change the Display Option, you can refer to the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="c76d3-153">在 [階層] 視窗中，保持選取 RoverAssembly 物件，在 [偵測器] 視窗中，找出 [On Placing Started ()] 事件，然後按一下 **+** 圖示，以新增新的事件：</span><span class="sxs-lookup"><span data-stu-id="c76d3-153">With the RoverAssembly object still selected in the Hierarchy window, in the Inspector window, locate the **On Placing Started ()** event and click the **+** icon to add a new event:</span></span>

![已新增 TapToPlace OnPlacingStarted 事件的 Unity](images/mr-learning-base/base-05-section3-step1-2.png)

<span data-ttu-id="c76d3-155">設定事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c76d3-155">Configure the event as follows:</span></span>

* <span data-ttu-id="c76d3-156">藉由從 [階層] 視窗將 **RoverAssembly** 物件拖曳至 [無 (物件)] 欄位，將其指派為 On Placing Started () 事件的接聽程式</span><span class="sxs-lookup"><span data-stu-id="c76d3-156">Assign the **RoverAssembly** object as a listener for the On Placing Started () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="c76d3-157">從 [沒有函式] 下拉式清單中，選取 [TapToPlace]  >  [float SurfaceNormalOffset]，以在觸發事件時更新 SurfaceNormalOffset 屬性值</span><span class="sxs-lookup"><span data-stu-id="c76d3-157">From the **No Function** dropdown, select **TapToPlace** > **float SurfaceNormalOffset** to update the SurfaceNormalOffset property value when the event is triggered</span></span>
* <span data-ttu-id="c76d3-158">確認引數已設定為 **0**</span><span class="sxs-lookup"><span data-stu-id="c76d3-158">Verify that the argument is set to **0**</span></span>

![已設定 TapToPlace OnPlacingStarted 事件的 Unity](images/mr-learning-base/base-05-section3-step1-3.png)

<span data-ttu-id="c76d3-160">在 [階層] 視窗中，以滑鼠右鍵按一下空的位置，然後選取 [3D 物件]  >  [Cube]，以建立代表地面的暫存物件，並設定 [Transform] 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c76d3-160">In the Hierarchy window, right-click on an empty spot and select **3D Object** > **Cube**, to create a temporary object representing the ground, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="c76d3-161">**位置**：X = 0、Y = -1.65、Z = 6</span><span class="sxs-lookup"><span data-stu-id="c76d3-161">**Position**: X = 0, Y = -1.65, Z = 6</span></span>
* <span data-ttu-id="c76d3-162">**旋轉**：X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="c76d3-162">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="c76d3-163">**縮放比例**：X = 10、Y = 0.2、Z = 10</span><span class="sxs-lookup"><span data-stu-id="c76d3-163">**Scale**: X = 10, Y = 0.2, Z = 10</span></span>

![已新增並置放暫存地面 Cube 物件的 Unity](images/mr-learning-base/base-05-section3-step1-4.png)

<span data-ttu-id="c76d3-165">在 [階層] 視窗中保持選取暫存 Cube，在 [偵測器] 視窗中使用 [層] 下拉式清單，將 Cube 的圖層設定變更為包含 **空間感知** 層：</span><span class="sxs-lookup"><span data-stu-id="c76d3-165">With the temporary Cube still selected in the Hierarchy window, in the Inspector window, use the **Layers** dropdown to change the Cube's Layer setting only to include the **Spatial Awareness** layer:</span></span>

![將暫存地面 Cube 物件圖層設定為 [空間感知] 的 Unity](images/mr-learning-base/base-05-section3-step1-5.png)

<span data-ttu-id="c76d3-167">按下 [開始遊戲] 按鈕進入遊戲模式，然後在往下移動滑鼠時按住滑鼠右鍵，直到注視 RoverAssembly 物件為止：</span><span class="sxs-lookup"><span data-stu-id="c76d3-167">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse down until the gaze hit's the RoverAssembly object:</span></span>

![具有注視點擊 RoverAssembly 物件的 Unity 播放模式分割檢視](images/mr-learning-base/base-05-section3-step1-6.png)

<span data-ttu-id="c76d3-169">按一下滑鼠左鍵以啟動點選放置程序：</span><span class="sxs-lookup"><span data-stu-id="c76d3-169">Click the left mouse button to start the tap-to-place process:</span></span>

![已開始放置 TapToPlace 的 Unity 播放模式分割檢視](images/mr-learning-base/base-05-section3-step1-7.png)

<span data-ttu-id="c76d3-171">在向左或向右移動滑鼠時按住滑鼠右鍵來旋轉您的注視方向，當您對放置位置感到滿意時，按一下滑鼠左鍵：</span><span class="sxs-lookup"><span data-stu-id="c76d3-171">Press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, when you are happy with the placement, click the left mouse button:</span></span>

![已結束放置 TapToPlace 的 Unity 播放模式分割檢視](images/mr-learning-base/base-05-section3-step1-8.png)

<span data-ttu-id="c76d3-173">在遊戲模式中完成功能的測試之後，以滑鼠右鍵按一下 Cube 物件，然後選取 [刪除] 將其從場景中移除：</span><span class="sxs-lookup"><span data-stu-id="c76d3-173">Once you are done testing the feature in the Game mode, right-click on the Cube object and select **Delete** to remove it from the scene:</span></span>

![已選取暫存地面 Cube 和 [刪除] 內容相關快顯功能表的 Unity](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a><span data-ttu-id="c76d3-175">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c76d3-175">Congratulations</span></span>

<span data-ttu-id="c76d3-176">在本教學課程中，您已了解如何使用 MRTK 的方向性指標解算器，讓 UI 元素以直覺方式將使用者導向至物件。</span><span class="sxs-lookup"><span data-stu-id="c76d3-176">In this tutorial, you learned how to use the MRTK's Directional Indicator Solver to have a UI element intuitively direct the user to objects.</span></span> <span data-ttu-id="c76d3-177">您也了解如何使用點選放置解算器，輕易地調整物件的位置。</span><span class="sxs-lookup"><span data-stu-id="c76d3-177">You also learned how to use the Tap To Place Solver to reposition objects easily.</span></span>

<span data-ttu-id="c76d3-178">若要深入了解 MRTK 隨附的這些解算器和其他解算器，您可以參閱 [MRTK 文件入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/)的[解算器](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md)指南。</span><span class="sxs-lookup"><span data-stu-id="c76d3-178">To learn more about these and other solvers included with the MRTK,  you can refer to the [Solvers](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver.md) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/).</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="c76d3-179">下一個教學課程：6.建立使用者介面</span><span class="sxs-lookup"><span data-stu-id="c76d3-179">Next Tutorial: 6. Creating user interfaces</span></span>](mr-learning-base-06.md)
