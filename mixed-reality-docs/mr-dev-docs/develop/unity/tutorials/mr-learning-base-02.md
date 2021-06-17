---
title: 初始化您的專案並部署您的第一個應用程式
description: 本課程說明如何為混合實境工具組 (MRTK) 設定 Unity 專案，以及如何將其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: fad4b389dc1aef2085b212404c7e17dfcf017701
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110284"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="b3684-104">2.初始化您的專案並部署您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="b3684-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="b3684-105">在本教學課程中，您將了解如何建立新的 Unity 專案、將其設定為混合實境工具組 (MRTK)開發之用，以及匯入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="b3684-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="b3684-106">您也將逐步了解如何設定和建置基本 Unity 場景，並將其從 Visual Studio 部署到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="b3684-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="b3684-107">將其部署到 HoloLens 2 之後，您應該會看到一個空間對應網格，其中涵蓋 HoloLens 所感知到的介面。</span><span class="sxs-lookup"><span data-stu-id="b3684-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="b3684-108">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="b3684-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a><span data-ttu-id="b3684-110">目標</span><span class="sxs-lookup"><span data-stu-id="b3684-110">Objectives</span></span>

* <span data-ttu-id="b3684-111">了解如何設定 Unity 以用於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="b3684-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="b3684-112">了解如何建置應用程式並部署至 HoloLens</span><span class="sxs-lookup"><span data-stu-id="b3684-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="b3684-113">體驗 HoloLens 2 裝置上的空間對應網格、手部網格和畫面播放速率計數器</span><span class="sxs-lookup"><span data-stu-id="b3684-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="b3684-114">建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="b3684-114">Creating the Unity project</span></span>

<span data-ttu-id="b3684-115">啟動 **Unity Hub**，選取 [專案] 索引標籤，然後按一下 [新增] 按鈕旁的 **向下箭號**：</span><span class="sxs-lookup"><span data-stu-id="b3684-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![已醒目提示 [新增] 按鈕的 Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="b3684-117">在下拉式清單中，選取 [必要條件](mr-learning-base-01.md#prerequisites)中所指定的 Unity **版本**：</span><span class="sxs-lookup"><span data-stu-id="b3684-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![具有新版本選取器下拉式清單的 Unity Hub](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="b3684-119">如果 Unity Hub 中無法使用特定的 Unity 版本，您可以從 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下載封存</a>起始安裝。</span><span class="sxs-lookup"><span data-stu-id="b3684-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="b3684-120">在 [建立新專案] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="b3684-120">In the Create a new project window:</span></span>

* <span data-ttu-id="b3684-121">確定 [範本] 設定為 [3D]</span><span class="sxs-lookup"><span data-stu-id="b3684-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="b3684-122">輸入適當的 [專案名稱]，例如 MRTK Tutorials</span><span class="sxs-lookup"><span data-stu-id="b3684-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="b3684-123">選擇適當的 [位置] 來儲存您的專案，例如 D:\MixedRealityLearning</span><span class="sxs-lookup"><span data-stu-id="b3684-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="b3684-124">按一下 [建立] 按鈕，以建立並啟動新的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="b3684-124">Click the **Create** button to create and launch your new Unity project</span></span>

![已填入 [建立新專案] 視窗的 Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="b3684-126">在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="b3684-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="b3684-127">因此，您應該將 Unity 專案儲存在磁碟機的根目錄附近。</span><span class="sxs-lookup"><span data-stu-id="b3684-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="b3684-128">等候 Unity 建立專案：</span><span class="sxs-lookup"><span data-stu-id="b3684-128">Wait for Unity to create the project:</span></span>

![Unity 正在建立新專案](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="b3684-130">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="b3684-130">Switching the build platform</span></span>

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="b3684-131">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="b3684-131">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="b3684-132">在 Unity 功能表中，選取 [視窗] >  [TextMeshPro]  >  [匯入 TMP 基本資源] 以開啟 [匯入 Unity 套件] 視窗：</span><span class="sxs-lookup"><span data-stu-id="b3684-132">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity [匯入 TMP 基本資源] 功能表路徑](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="b3684-134">在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：</span><span class="sxs-lookup"><span data-stu-id="b3684-134">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity [TMP 基本資源] 匯入視窗](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="b3684-136">MRTK 的 UI 元素需要 TextMeshPro 基本資源。</span><span class="sxs-lookup"><span data-stu-id="b3684-136">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="b3684-137">如果您不打算在專案中使用 MRTK 的 UI 元素，則可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="b3684-137">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="b3684-138">匯入混合現實工具組和設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="b3684-138">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="b3684-139">若要將混合現實工具組匯入 Unity 專案中，您必須使用「 [混合現實」功能工具](../welcome-to-mr-feature-tool.md) ，讓開發人員能夠探索、更新和新增混合現實功能套件至 unity 專案。</span><span class="sxs-lookup"><span data-stu-id="b3684-139">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="b3684-140">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="b3684-140">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="b3684-141">請從 [Microsoft 下載中心](https://aka.ms/MRFeatureTool)下載最新版本的混合現實功能工具，下載完成後，請將檔案解壓縮，並將其儲存到您的桌面。</span><span class="sxs-lookup"><span data-stu-id="b3684-141">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="b3684-142">在您可以執行混合現實功能工具之前，請先安裝[.net 5.0 運行](https://dotnet.microsoft.com/download/dotnet/5.0)時間</span><span class="sxs-lookup"><span data-stu-id="b3684-142">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="b3684-143">混合現實功能工具目前只在 Windows 上執行，若為 MacOS，請依照此程式下載並匯入混合現實工具 [組至 unity](/windows/mixed-reality/mrtk-unity/configuration/usingupm) 專案。</span><span class="sxs-lookup"><span data-stu-id="b3684-143">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](/windows/mixed-reality/mrtk-unity/configuration/usingupm) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="b3684-144">從下載的資料夾開啟可執行檔 **MixedRealityFeatureTool** ，以啟動「混合現實」功能工具。</span><span class="sxs-lookup"><span data-stu-id="b3684-144">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![開啟 MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="b3684-146">建立場景並設定 MRTK</span><span class="sxs-lookup"><span data-stu-id="b3684-146">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="b3684-147">在 Unity 功能表中，選取 [ **File**  >  **New 場景**：</span><span class="sxs-lookup"><span data-stu-id="b3684-147">In the Unity menu, select **File** > **New Scene**:</span></span>

![Unity [新增場景] 功能表路徑](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="b3684-149">在 [ **新場景** ] 視窗中，選取 [ **基本 (內建)** ，然後按一下 [ **建立** ] 以建立新場景：</span><span class="sxs-lookup"><span data-stu-id="b3684-149">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Unity 新場景視窗](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="b3684-151">上述螢幕擷取畫面是來自 Unity 2020 版，如果您在按一下 [ **建立** ] 時使用 unity 2019，則會建立新的空場景。</span><span class="sxs-lookup"><span data-stu-id="b3684-151">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="b3684-152">在 Unity 功能表中，選取 [**混合現實**  >  **工具** 組  >  **新增至場景]，並設定 ...** 將 MRTK 新增至您目前的場景：</span><span class="sxs-lookup"><span data-stu-id="b3684-152">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity [新增至場景並設定...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="b3684-154">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件後，在 [偵測器] 視窗中，驗證 **MixedRealityToolkit** 設定中的設定檔是否變更為 **DefaultMixedRealityToolkitConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="b3684-154">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![已選取 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="b3684-156">在 Unity 功能表中，選取 [檔案] >  [另存新檔 ...] 以開啟 [儲存場景] 視窗：</span><span class="sxs-lookup"><span data-stu-id="b3684-156">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity [另存新檔...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="b3684-158">將您專案中的場景儲存在 **資產**  >  **幕後**。</span><span class="sxs-lookup"><span data-stu-id="b3684-158">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Unity [儲存場景] 的 [儲存] 提示視窗](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b3684-160">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="b3684-160">Importing the tutorial assets</span></span>

<span data-ttu-id="b3684-161">下載下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="b3684-161">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="b3684-162">MRTK.HoloLens2. GettingStarted. 2.5.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="b3684-162">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="b3684-163">若要匯入 unity 自訂套件，請在 Unity 功能表中，選取 [**資產** 匯  >  **入套件**  >  **自訂套件 ...** ] 開啟 [匯入封裝 ...]視窗：</span><span class="sxs-lookup"><span data-stu-id="b3684-163">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![匯入自訂套件](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="b3684-165">在 [匯入封裝 ...]視窗中，選取 **MRTK。HoloLens2** 您下載的 GettingStarted，然後按一下 [開啟] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="b3684-165">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![選取資產套件](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="b3684-167">在 [匯入 Unity 封裝] 視窗中，按一下 [全部] 按鈕以確保所有資產都已選取，然後按一下 [匯入] 按鈕以匯入資產：</span><span class="sxs-lookup"><span data-stu-id="b3684-167">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![選取要匯入的所有資產](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="b3684-169">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="b3684-169">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入資產後的 Unity 專案視窗](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a><span data-ttu-id="b3684-171">設定場景</span><span class="sxs-lookup"><span data-stu-id="b3684-171">Configuring the Scene</span></span>

<span data-ttu-id="b3684-172">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.GettingStarted] > [Prefabs] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b3684-172">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

<span data-ttu-id="b3684-173">在 [專案] 視窗中，按一下 [ **Cube** 預製專案] 並將其拖曳至 [階層] 視窗，然後在 [偵測器] 視窗中設定其 **轉換** 元件，如下所示</span><span class="sxs-lookup"><span data-stu-id="b3684-173">From the Project window, click-and-drag the **Cube** prefab on to the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="b3684-174">**Position**： X = 0、Y = 0、Z = 0。5</span><span class="sxs-lookup"><span data-stu-id="b3684-174">**Position**: X = 0, Y = 0, Z = 0.5</span></span>
* <span data-ttu-id="b3684-175">**旋轉**：X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="b3684-175">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="b3684-176">**縮放**：X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="b3684-176">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![將 cube 加入場景](images/mr-learning-base/base-02-section8-step1-1.PNG)

<span data-ttu-id="b3684-178">若要將焦點放在場景中的物件上，您可以按兩下 **Cube** 物件，然後再稍微放大：</span><span class="sxs-lookup"><span data-stu-id="b3684-178">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again:</span></span>

<span data-ttu-id="b3684-179">若要與追蹤的手互動及抓取物件，物件必須具有碰撞元件，例如方塊 **碰撞**、物件操作工具  **(腳本)** 元件和 **NearInteractionGrabbable (腳本)** 元件。</span><span class="sxs-lookup"><span data-stu-id="b3684-179">To interact and grab an object with tracked hands, the object must have Collider component for example a **Box Collider**,  **Object Manipulator (Script)** component and **NearInteractionGrabbable(Script)** component.</span></span>

<span data-ttu-id="b3684-180">當 **Cube** 仍在 [階層] 視窗中選取時，在 [偵測器] 視窗中，按一下 [ **加入元件** ] 按鈕，然後搜尋並選取 [ **物件** 操作工具腳本]，將物件操作工具腳本加入 Cube 物件中。</span><span class="sxs-lookup"><span data-stu-id="b3684-180">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![將物件 manupulator 加入至 cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="b3684-182">重複相同的步驟，將 **接近互動的 Grabbable 腳本** 新增至 cube</span><span class="sxs-lookup"><span data-stu-id="b3684-182">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![將近乎互動的 Grabable 新增至 cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="b3684-184">當您加入物件操作工具 (腳本時) ，在此情況下，會自動加入條件約束管理員 (腳本) ，因為物件操作工具 (腳本) 相依于它。</span><span class="sxs-lookup"><span data-stu-id="b3684-184">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="b3684-185">基於本教學課程的目的，colliders 已經加入 Cube 物件中。</span><span class="sxs-lookup"><span data-stu-id="b3684-185">For the purpose of this tutorial, colliders have already been added to the Cube Object.</span></span> <span data-ttu-id="b3684-186">若要深入了解碰撞器，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞器 (Collider)</a> 文件。</span><span class="sxs-lookup"><span data-stu-id="b3684-186">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

<span data-ttu-id="b3684-187">若要在 Unity 編輯器中測試此項，您可以進入 [播放] 模式，並按住 **LeftShift** 或 **空格鍵** 以啟用控制器，滑鼠移動會移動控制器，也可以使用滑鼠滾輪移至或接近相機。</span><span class="sxs-lookup"><span data-stu-id="b3684-187">To test this in the Unity editor, you can enter the play mode and hold the **LeftShift** or **Space** key to enable the controller, Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="b3684-188">指標位於 Cube 上時，按住 **滑鼠** 左鍵以移動 cube 物件。</span><span class="sxs-lookup"><span data-stu-id="b3684-188">Once the pointer is on the Cube  press and hold **Left Mouse Button** to move the the Cube object.</span></span>

![遊戲模式](images/mr-learning-base/base-02-section8-step1-4.PNG)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="b3684-190">在您的 HoloLens 2 上建置應用程式</span><span class="sxs-lookup"><span data-stu-id="b3684-190">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="b3684-191">1.組建 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="b3684-191">1. Build the Unity project</span></span>

<span data-ttu-id="b3684-192">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b3684-192">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="b3684-193">在 [組建設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至 [組建中的場景] 清單，然後按一下 [組建] 按鈕以開啟 [組建通用 Windows 平台] 視窗：</span><span class="sxs-lookup"><span data-stu-id="b3684-193">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![已選取 UWP 的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="b3684-195">在 [組建通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的組建，例如 D:\MixedRealityLearning\Builds，建立新的資料夾並指定適當的名稱，例如 GettingStarted，然後按一下 [選取資料夾] 按鈕開始組建程序：</span><span class="sxs-lookup"><span data-stu-id="b3684-195">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![具有 [選取資料夾] 提示視窗的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="b3684-197">等候 Unity 完成組建程序：</span><span class="sxs-lookup"><span data-stu-id="b3684-197">Wait for Unity to finish the build process:</span></span>

![Unity 正在進行建置程序](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="b3684-199">2.組建和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="b3684-199">2. Build and deploy the application</span></span>

<span data-ttu-id="b3684-200">當建置程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。</span><span class="sxs-lookup"><span data-stu-id="b3684-200">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="b3684-201">瀏覽該資料夾，按兩下解決方案的檔案即可在 Visual Studio 中開啟該檔案：</span><span class="sxs-lookup"><span data-stu-id="b3684-201">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Windows 檔案總管，其中已選取新建立的 Visual Studio 解決方案](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b3684-203">如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同 **[安裝工具](../../install-the-tools.md)** 文件中所述。</span><span class="sxs-lookup"><span data-stu-id="b3684-203">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="b3684-204">設定 Visual Studio 以便用於 HoloLens，請選取 [Master] 或 [Release] 設定、[ARM64] 架構，選取 [裝置] 作為目標：</span><span class="sxs-lookup"><span data-stu-id="b3684-204">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![已針對要部署至 HoloLens 2 來設定 Visual Studio](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="b3684-206">如果您要部署至 HoloLens (第1代)，請選取 **x86** 架構。</span><span class="sxs-lookup"><span data-stu-id="b3684-206">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="b3684-207">若是 HoloLens，您通常會建立 ARM 架構。</span><span class="sxs-lookup"><span data-stu-id="b3684-207">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="b3684-208">不過，在 Visual Studio 中選取 ARM 作為建置架構時，Unity 2019.3 中的<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知問題</strong></a>會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="b3684-208">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="b3684-209">建議的解決方法是以 ARM64 建置。</span><span class="sxs-lookup"><span data-stu-id="b3684-209">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="b3684-210">如果無法這麼做，請移至 **編輯 > 專案設定 > 播放程式 > 其他設定** 並停用 **圖形作業**。</span><span class="sxs-lookup"><span data-stu-id="b3684-210">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="b3684-211">如果您看不到 [裝置為目標] 選項，可能需要將 Visual Studio 解決方案的啟始專案從 IL2CPP 專案變更為 UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="b3684-211">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="b3684-212">要這麼做，在方案總管中，以滑鼠右鍵按一下 YourProjectName (Universal Windows) 並選取 [設定為啟動專案]。</span><span class="sxs-lookup"><span data-stu-id="b3684-212">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="b3684-213">將 HoloLens 與電腦連線，然後選取 [偵錯] > [啟動但不進行偵錯]，以建置並部署至您的裝置：</span><span class="sxs-lookup"><span data-stu-id="b3684-213">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio [啟動但不進行偵錯] 功能表路徑](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="b3684-215">在組建您的裝置之前，裝置必須處於「開發人員模式」，並與開發電腦配對。</span><span class="sxs-lookup"><span data-stu-id="b3684-215">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="b3684-216">請遵循[這些指示](../../platform-capabilities-and-apis/using-visual-studio.md)來完成這兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="b3684-216">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="b3684-217">您也可以部署到 [HoloLens 模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或為側載建立[應用程式套件](/windows/uwp/packaging/packaging-uwp-apps)。</span><span class="sxs-lookup"><span data-stu-id="b3684-217">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="b3684-218">使用 [啟動但不進行偵測] 會自動啟動您裝置上的應用程式，而不會附加 Visual Studio 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="b3684-218">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="b3684-219">若要在不自動啟動應用程式的情況下部署裝置，選取 [組建] > [部署解決方案]。</span><span class="sxs-lookup"><span data-stu-id="b3684-219">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="b3684-220">您可能會注意到應用程式中的診斷分析工具，您可以使用 **Toggle Diagnostics** 語音命令開啟或關閉此工具。</span><span class="sxs-lookup"><span data-stu-id="b3684-220">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="b3684-221">建議您在開發期間儘量讓分析工具保持可見，以了解應用程式的變更何時會對效能產生影響。</span><span class="sxs-lookup"><span data-stu-id="b3684-221">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="b3684-222">例如，HoloLens 應用程式應該[持續以 60 FPS 執行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="b3684-222">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="b3684-223">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b3684-223">Congratulations</span></span>

<span data-ttu-id="b3684-224">您現在已部署了第一個 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3684-224">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="b3684-225">開啟應用程式之後，您應該會看到 Cube 物件放在您面前，而且應該可以移動它來與 cube 互動，您應該也會看到一個空間對應網格，其中涵蓋 HoloLens 所察覺的表面。</span><span class="sxs-lookup"><span data-stu-id="b3684-225">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="b3684-226">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="b3684-226">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="b3684-227">這些功能只是 MRTK 所包含的幾個基本部分。</span><span class="sxs-lookup"><span data-stu-id="b3684-227">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="b3684-228">在接下來的教學課程中，您將會在場景中新增內容，以探索 HoloLens 和 MRTK 的功能。</span><span class="sxs-lookup"><span data-stu-id="b3684-228">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b3684-229">下一個教學課程：3.設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="b3684-229">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
