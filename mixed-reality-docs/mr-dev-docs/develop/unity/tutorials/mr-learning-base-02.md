---
title: 初始化您的專案並部署您的第一個應用程式
description: 本課程說明如何為混合實境工具組 (MRTK) 設定 Unity 專案，以及如何將其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175714"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="dd995-104">2.初始化您的專案並部署您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="dd995-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="dd995-105">在本教學課程中，您將了解如何建立新的 Unity 專案、將其設定為混合實境工具組 (MRTK)開發之用，以及匯入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="dd995-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="dd995-106">您也將逐步了解如何設定和建置基本 Unity 場景，並將其從 Visual Studio 部署到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="dd995-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="dd995-107">將其部署到 HoloLens 2 之後，您應該會看到一個空間對應網格，其中涵蓋 HoloLens 所感知到的介面。</span><span class="sxs-lookup"><span data-stu-id="dd995-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="dd995-108">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="dd995-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="dd995-109">目標</span><span class="sxs-lookup"><span data-stu-id="dd995-109">Objectives</span></span>

* <span data-ttu-id="dd995-110">了解如何設定 Unity 以用於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="dd995-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="dd995-111">了解如何建置應用程式並部署至 HoloLens</span><span class="sxs-lookup"><span data-stu-id="dd995-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="dd995-112">體驗 HoloLens 2 裝置上的空間對應網格、手部網格和畫面播放速率計數器</span><span class="sxs-lookup"><span data-stu-id="dd995-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

### <a name="steps-overview"></a><span data-ttu-id="dd995-113">步驟總覽</span><span class="sxs-lookup"><span data-stu-id="dd995-113">Steps overview</span></span>
:::row:::
    :::column:::
       <span data-ttu-id="dd995-114">![概述步驟 1 ](images/mr-learning-base/base-02-overview-step1.png) **1。建立新的 Unity 專案**</span><span class="sxs-lookup"><span data-stu-id="dd995-114">![Overview Step 1](images/mr-learning-base/base-02-overview-step1.png) **1. Create a new Unity project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd995-115">![[總覽] 步驟 2 ](images/mr-learning-base/base-02-overview-step2.png) **。將 MRTK 匯入專案**</span><span class="sxs-lookup"><span data-stu-id="dd995-115">![Overview Step 2](images/mr-learning-base/base-02-overview-step2.png) **2. Import MRTK into the project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd995-116">![概述步驟 3 ](images/mr-learning-base/base-02-overview-step3.png) **：使用 MRTK 設定新場景**</span><span class="sxs-lookup"><span data-stu-id="dd995-116">![Overview Step 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configure a new scene with MRTK**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       <span data-ttu-id="dd995-117">![概述步驟 4 ](images/mr-learning-base/base-02-overview-step4.png) **。建立 Unity Project**</span><span class="sxs-lookup"><span data-stu-id="dd995-117">![Overview Step 4](images/mr-learning-base/base-02-overview-step4.png) **4. Build Unity Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd995-118">![概述步驟 5 ](images/mr-learning-base/base-02-overview-step5.png) **：建立 UWP Project**</span><span class="sxs-lookup"><span data-stu-id="dd995-118">![Overview Step 5](images/mr-learning-base/base-02-overview-step5.png) **5. Build UWP Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd995-119">![總覽步驟 6 ](images/mr-learning-base/base-02-overview-step6.png) **：在裝置上執行 Project**</span><span class="sxs-lookup"><span data-stu-id="dd995-119">![Overview Step 6](images/mr-learning-base/base-02-overview-step6.png) **6. Run Project on the Device**</span></span>
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a><span data-ttu-id="dd995-120">建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="dd995-120">Creating the Unity project</span></span>

<span data-ttu-id="dd995-121">啟動 **Unity Hub**，選取 [專案] 索引標籤，然後按一下 [新增] 按鈕旁的 **向下箭號**：</span><span class="sxs-lookup"><span data-stu-id="dd995-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

<span data-ttu-id="dd995-122">在下拉式清單中，選取 [必要條件](mr-learning-base-01.md#prerequisites)中所指定的 Unity **版本**：</span><span class="sxs-lookup"><span data-stu-id="dd995-122">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> <span data-ttu-id="dd995-123">如果 Unity Hub 中無法使用特定的 Unity 版本，您可以從 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下載封存</a>起始安裝。</span><span class="sxs-lookup"><span data-stu-id="dd995-123">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="dd995-124">在 [建立新專案] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="dd995-124">In the Create a new project window:</span></span>

* <span data-ttu-id="dd995-125">確定 [範本] 設定為 [3D]</span><span class="sxs-lookup"><span data-stu-id="dd995-125">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="dd995-126">輸入適當的 [專案名稱]，例如 MRTK Tutorials</span><span class="sxs-lookup"><span data-stu-id="dd995-126">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="dd995-127">選擇適當的 [位置] 來儲存您的專案，例如 D:\MixedRealityLearning</span><span class="sxs-lookup"><span data-stu-id="dd995-127">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="dd995-128">按一下 [建立] 按鈕，以建立並啟動新的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="dd995-128">Click the **Create** button to create and launch your new Unity project</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> <span data-ttu-id="dd995-129">在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="dd995-129">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="dd995-130">因此，您應該將 Unity 專案儲存在磁碟機的根目錄附近。</span><span class="sxs-lookup"><span data-stu-id="dd995-130">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="dd995-131">等候 Unity 建立專案：</span><span class="sxs-lookup"><span data-stu-id="dd995-131">Wait for Unity to create the project:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a><span data-ttu-id="dd995-132">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="dd995-132">Switching the build platform</span></span>

<span data-ttu-id="dd995-133">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="dd995-133">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity [建置設定] 功能表路徑](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="dd995-135">在 [組建設定] 視窗中，選取 **通用 Windows 平臺** 和：</span><span class="sxs-lookup"><span data-stu-id="dd995-135">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="dd995-136">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="dd995-136">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="dd995-137">將 **架構** 設定為 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="dd995-137">Set **Architecture** to **ARM 64**</span></span> 
3. <span data-ttu-id="dd995-138">將 [組建類型] 設定為 [D3D 專案]</span><span class="sxs-lookup"><span data-stu-id="dd995-138">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="dd995-139">將 **目標 SDK 版本** 設為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="dd995-139">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="dd995-140">將 **最低平臺版本** 設定為 **10.0.1024.0**</span><span class="sxs-lookup"><span data-stu-id="dd995-140">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="dd995-141">將 **Visual Studio 版本** 設為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="dd995-141">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="dd995-142">設定 **組建並在** **USB 裝置** 上執行</span><span class="sxs-lookup"><span data-stu-id="dd995-142">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="dd995-143">將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題</span><span class="sxs-lookup"><span data-stu-id="dd995-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="dd995-144">按一下 [切換平臺] 按鈕</span><span class="sxs-lookup"><span data-stu-id="dd995-144">Click the Switch Platform button</span></span>

![已設定通用 Windows 平臺設定的 Unity 組建設定](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="dd995-146">等候 Unity 完成平台的切換：</span><span class="sxs-lookup"><span data-stu-id="dd995-146">Wait for Unity to finish switching the platform:</span></span>

![Unity 正在切換平台](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="dd995-148">當 Unity 完成切換平臺時，請按一下 **x** 圖示以關閉組建設定視窗。</span><span class="sxs-lookup"><span data-stu-id="dd995-148">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="dd995-149">匯入混合現實工具組和設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="dd995-149">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="dd995-150">若要將 mixed reality 工具組匯入 unity Project 您必須使用[mixed reality 功能工具](../welcome-to-mr-feature-tool.md)，讓開發人員能夠探索、更新和新增混合現實功能套件至 unity 專案。</span><span class="sxs-lookup"><span data-stu-id="dd995-150">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="dd995-151">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="dd995-151">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="dd995-152">請從 [Microsoft 下載中心](https://aka.ms/MRFeatureTool)下載最新版本的混合現實功能工具，下載完成後，請將檔案解壓縮，並將其儲存到您的桌面。</span><span class="sxs-lookup"><span data-stu-id="dd995-152">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="dd995-153">在您可以執行混合現實功能工具之前，請先安裝[.net 5.0 運行](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)時間</span><span class="sxs-lookup"><span data-stu-id="dd995-153">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span></span>

<span data-ttu-id="dd995-154">從下載的資料夾開啟可執行檔 **MixedRealityFeatureTool** ，以啟動「混合現實」功能工具。</span><span class="sxs-lookup"><span data-stu-id="dd995-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="dd995-155">建立場景並設定 MRTK</span><span class="sxs-lookup"><span data-stu-id="dd995-155">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="dd995-156">在 Unity 功能表中，選取 [ **File**  >  **New 場景**：</span><span class="sxs-lookup"><span data-stu-id="dd995-156">In the Unity menu, select **File** > **New Scene**:</span></span>

![Unity [新增場景] 功能表路徑](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="dd995-158">在 [ **新場景** ] 視窗中，選取 [ **基本 (內建)** ，然後按一下 [ **建立** ] 以建立新場景：</span><span class="sxs-lookup"><span data-stu-id="dd995-158">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Unity 新場景視窗](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="dd995-160">上述螢幕擷取畫面是來自 Unity 2020 版，如果您在按一下 [ **建立** ] 時使用 unity 2019，則會建立新的空場景。</span><span class="sxs-lookup"><span data-stu-id="dd995-160">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="dd995-161">在 Unity 功能表中，選取 [**混合現實**  >  **工具** 組  >  **新增至場景]，並設定 ...** 將 MRTK 新增至您目前的場景：</span><span class="sxs-lookup"><span data-stu-id="dd995-161">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity [新增至場景並設定...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="dd995-163">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件後，在 [偵測器] 視窗中，驗證 **MixedRealityToolkit** 設定中的設定檔是否變更為 **DefaultMixedRealityToolkitConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="dd995-163">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![已選取 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="dd995-165">在 Unity 功能表中，選取 [檔案] >  [另存新檔 ...] 以開啟 [儲存場景] 視窗：</span><span class="sxs-lookup"><span data-stu-id="dd995-165">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity [另存新檔...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="dd995-167">將您專案中的場景儲存在 **資產**  >  **幕後**。</span><span class="sxs-lookup"><span data-stu-id="dd995-167">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Unity [儲存場景] 的 [儲存] 提示視窗](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a><span data-ttu-id="dd995-169">將手互動新增至物件</span><span class="sxs-lookup"><span data-stu-id="dd995-169">Adding hand interaction to an object</span></span>

<span data-ttu-id="dd995-170">在 Unity 功能表中，選取 [ **GameObject**  >  **3d 物件**  >  **Cube** ]，將 Cube 物件加入場景中。</span><span class="sxs-lookup"><span data-stu-id="dd995-170">In the Unity menu, select **GameObject** > **3D Object** > **Cube** to add a cube object to the scene.</span></span>

![將 cube 加入場景](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="dd995-172">按一下 [階層] 視窗中的 **Cube** 物件，然後在 [偵測器] 視窗中設定其 **轉換** 元件，如下所示</span><span class="sxs-lookup"><span data-stu-id="dd995-172">Click the **Cube** object in the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="dd995-173">**Position**： X = 0，Y =-0.1，Z = 0。5</span><span class="sxs-lookup"><span data-stu-id="dd995-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span></span>
* <span data-ttu-id="dd995-174">**旋轉**：X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="dd995-174">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="dd995-175">**Scale**： X = 0.1、Y = 0.1、Z = 0。1</span><span class="sxs-lookup"><span data-stu-id="dd995-175">**Scale**: X = 0.1, Y = 0.1, Z = 0.1</span></span>

<span data-ttu-id="dd995-176">1個 Unity 單位是1個計量。</span><span class="sxs-lookup"><span data-stu-id="dd995-176">1 Unity unit is 1 meter.</span></span> <span data-ttu-id="dd995-177">我們已將 cube 的大小更新為 10x10x10 cm，從耳機位置的50cm 放置 (0，0，0) 。</span><span class="sxs-lookup"><span data-stu-id="dd995-177">We have updated cube's size to 10x10x10 cm, placed at 50cm from the headset position (0,0,0).</span></span> <span data-ttu-id="dd995-178">10cm，以熟悉互動。</span><span class="sxs-lookup"><span data-stu-id="dd995-178">10cm below the eye level for comfortable interaction.</span></span> 

<span data-ttu-id="dd995-179">如果您使用預設小數位數 (1，1，1) ，cube 將會太大。</span><span class="sxs-lookup"><span data-stu-id="dd995-179">If you use the default scale (1,1,1), the cube will be too big.</span></span> <span data-ttu-id="dd995-180">如果您使用預設位置 (0、0、0) ，cube 將放置在與耳機相同的位置，而且您將無法看到它，直到您向前移動為止。</span><span class="sxs-lookup"><span data-stu-id="dd995-180">If you use the default position (0,0,0), the cube will be placed at the same position as your headset and you won't be able to see it until you move backward.</span></span>

![調整轉換資訊](images/mr-learning-base/base-02-section8-step1-1b.png)

<span data-ttu-id="dd995-182">若要將焦點放在場景中的物件上，您可以按兩下 **Cube** 物件，然後再稍微放大。</span><span class="sxs-lookup"><span data-stu-id="dd995-182">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again.</span></span> <span data-ttu-id="dd995-183">或者，您可以使用 F 鍵來縮放物件，並將焦點放在物件上。</span><span class="sxs-lookup"><span data-stu-id="dd995-183">Or you can use F key to zoom and focus on the object.</span></span>

<span data-ttu-id="dd995-184">若要與追蹤的手互動及抓取物件，物件必須有：</span><span class="sxs-lookup"><span data-stu-id="dd995-184">To interact and grab an object with tracked hands, the object must have:</span></span>
 * <span data-ttu-id="dd995-185">碰撞器元件（例如方塊 **碰撞** 器） (Unity 的 cube 預設已經有方塊碰撞器) </span><span class="sxs-lookup"><span data-stu-id="dd995-185">Collider component such as **Box Collider** (Unity's cube already has a Box Collider by default)</span></span>
 * <span data-ttu-id="dd995-186">**Object Manipulator (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="dd995-186">**Object Manipulator (Script)** component</span></span>
 * <span data-ttu-id="dd995-187">**NearInteractionGrabbable (腳本)** 元件</span><span class="sxs-lookup"><span data-stu-id="dd995-187">**NearInteractionGrabbable(Script)** component</span></span>

<span data-ttu-id="dd995-188">MRTK 的 **ObjectManipulator** 腳本會使用一或兩個手來讓物件可移動、可擴充和 rotatable。</span><span class="sxs-lookup"><span data-stu-id="dd995-188">MRTK's **ObjectManipulator** script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="dd995-189">此指令碼支援直接操作輸入模型，因為指令碼可讓使用者用手直接碰觸全像投影。</span><span class="sxs-lookup"><span data-stu-id="dd995-189">This script supports the direct manipulation input model as the script enables the user to touch holograms directly with their hands.</span></span>

<span data-ttu-id="dd995-190">當 **Cube** 仍在 [階層] 視窗中選取時，在 [偵測器] 視窗中，按一下 [ **加入元件** ] 按鈕，然後搜尋並選取 [ **物件** 操作工具腳本]，將物件操作工具腳本加入 Cube 物件中。</span><span class="sxs-lookup"><span data-stu-id="dd995-190">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![將物件 manupulator 加入至 cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="dd995-192">重複相同的步驟，將 **接近互動的 Grabbable 腳本** 新增至 cube</span><span class="sxs-lookup"><span data-stu-id="dd995-192">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![將近乎互動的 Grabable 新增至 cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="dd995-194">當您加入物件操作工具 (腳本時) ，在此情況下，會自動加入條件約束管理員 (腳本) ，因為物件操作工具 (腳本) 相依于它。</span><span class="sxs-lookup"><span data-stu-id="dd995-194">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a><span data-ttu-id="dd995-195">使用 MRTK 輸入模擬在 Unity 編輯器中測試您的應用程式</span><span class="sxs-lookup"><span data-stu-id="dd995-195">Testing your application in Unity editor with MRTK input simulation</span></span>

<span data-ttu-id="dd995-196">使用 MRTK 的輸入模擬，您可以在 Unity 編輯器中測試各種類型的互動，而不需要建立及部署到裝置。</span><span class="sxs-lookup"><span data-stu-id="dd995-196">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="dd995-197">這可讓您快速地在設計和開發程式中反復查看您的想法。</span><span class="sxs-lookup"><span data-stu-id="dd995-197">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="dd995-198">使用鍵盤和滑鼠組合來控制模擬的輸入。</span><span class="sxs-lookup"><span data-stu-id="dd995-198">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="dd995-199">按一下 [播放] 按鈕，然後輸入播放模式。</span><span class="sxs-lookup"><span data-stu-id="dd995-199">Click the play button and enter the play mode.</span></span> <span data-ttu-id="dd995-200">按住 **左 Shift** 鍵或 **空格鍵** ，讓控制器 (模擬的手) ，滑鼠移動會移動控制器，也可以使用滑鼠滾輪移至或靠近相機。</span><span class="sxs-lookup"><span data-stu-id="dd995-200">Hold the **Left Shift** or **Space** key to bring up the controller (simulated hands), Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="dd995-201">指標位於 Cube 上時，按住 **滑鼠** 左鍵以抓取 cube 物件。</span><span class="sxs-lookup"><span data-stu-id="dd995-201">Once the pointer is on the Cube press and hold **Left Mouse Button** to grab the Cube object.</span></span>

* <span data-ttu-id="dd995-202">按 **W、A、S、D、Q、E** 鍵以移動相機。</span><span class="sxs-lookup"><span data-stu-id="dd995-202">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="dd995-203">按住滑鼠 **右鍵** ，並將滑鼠移至 [四處尋找]。</span><span class="sxs-lookup"><span data-stu-id="dd995-203">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="dd995-204">若要啟動模擬的手，請按 **空格鍵 (右手)** 或 **左 Shift 鍵 (左邊)**</span><span class="sxs-lookup"><span data-stu-id="dd995-204">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="dd995-205">若要讓模擬手保持在視野中，請按 **T** 或 **Y** 鍵</span><span class="sxs-lookup"><span data-stu-id="dd995-205">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="dd995-206">若要旋轉模擬的手，請按住 **Ctrl** 鍵並移動滑鼠</span><span class="sxs-lookup"><span data-stu-id="dd995-206">To rotate simulated hands, press and hold **Ctrl** key and move mouse</span></span>

![遊戲模式](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="dd995-208">在您的 HoloLens 2 上建置應用程式</span><span class="sxs-lookup"><span data-stu-id="dd995-208">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="dd995-209">1.組建 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="dd995-209">1. Build the Unity project</span></span>

<span data-ttu-id="dd995-210">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="dd995-210">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="dd995-211">在 [組建設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至 [組建中的場景] 清單，然後按一下 [組建] 按鈕以開啟 [組建通用 Windows 平台] 視窗：</span><span class="sxs-lookup"><span data-stu-id="dd995-211">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![已選取 UWP 的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="dd995-213">在 [組建通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的組建，例如 D:\MixedRealityLearning\Builds，建立新的資料夾並指定適當的名稱，例如 GettingStarted，然後按一下 [選取資料夾] 按鈕開始組建程序：</span><span class="sxs-lookup"><span data-stu-id="dd995-213">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![具有 [選取資料夾] 提示視窗的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="dd995-215">等候 Unity 完成組建程序：</span><span class="sxs-lookup"><span data-stu-id="dd995-215">Wait for Unity to finish the build process:</span></span>

![Unity 正在進行建置程序](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="dd995-217">2.組建和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="dd995-217">2. Build and deploy the application</span></span>

<span data-ttu-id="dd995-218">當建置程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。</span><span class="sxs-lookup"><span data-stu-id="dd995-218">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="dd995-219">瀏覽該資料夾，按兩下解決方案的檔案即可在 Visual Studio 中開啟該檔案：</span><span class="sxs-lookup"><span data-stu-id="dd995-219">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Windows 檔案總管，其中已選取新建立的 Visual Studio 解決方案](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="dd995-221">如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同 **[安裝工具](../../install-the-tools.md)** 文件中所述。</span><span class="sxs-lookup"><span data-stu-id="dd995-221">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="dd995-222">設定 Visual Studio 以便用於 HoloLens，請選取 [Master] 或 [Release] 設定、[ARM64] 架構，選取 [裝置] 作為目標：</span><span class="sxs-lookup"><span data-stu-id="dd995-222">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![已針對要部署至 HoloLens 2 來設定 Visual Studio](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="dd995-224">如果您要部署至 HoloLens (第1代)，請選取 **x86** 架構。</span><span class="sxs-lookup"><span data-stu-id="dd995-224">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="dd995-225">若是 HoloLens，您通常會建立 ARM 架構。</span><span class="sxs-lookup"><span data-stu-id="dd995-225">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="dd995-226">不過，在 Visual Studio 中選取 ARM 作為建置架構時，Unity 2019.3 中的<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知問題</strong></a>會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="dd995-226">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="dd995-227">建議的解決方法是以 ARM64 建置。</span><span class="sxs-lookup"><span data-stu-id="dd995-227">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="dd995-228">如果無法這麼做，請移至 **編輯 > 專案設定 > 播放程式 > 其他設定** 並停用 **圖形作業**。</span><span class="sxs-lookup"><span data-stu-id="dd995-228">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="dd995-229">如果您看不到 [裝置為目標] 選項，可能需要將 Visual Studio 解決方案的啟始專案從 IL2CPP 專案變更為 UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="dd995-229">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="dd995-230">要這麼做，在方案總管中，以滑鼠右鍵按一下 YourProjectName (Universal Windows) 並選取 [設定為啟動專案]。</span><span class="sxs-lookup"><span data-stu-id="dd995-230">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="dd995-231">將 HoloLens 與電腦連線，然後選取 [偵錯] > [啟動但不進行偵錯]，以建置並部署至您的裝置：</span><span class="sxs-lookup"><span data-stu-id="dd995-231">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio [啟動但不進行偵錯] 功能表路徑](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="dd995-233">在組建您的裝置之前，裝置必須處於「開發人員模式」，並與開發電腦配對。</span><span class="sxs-lookup"><span data-stu-id="dd995-233">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="dd995-234">請遵循[這些指示](../../platform-capabilities-and-apis/using-visual-studio.md)來完成這兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="dd995-234">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="dd995-235">您也可以部署到 [HoloLens 模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或為側載建立[應用程式套件](/windows/uwp/packaging/packaging-uwp-apps)。</span><span class="sxs-lookup"><span data-stu-id="dd995-235">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="dd995-236">使用 [啟動但不進行偵測] 會自動啟動您裝置上的應用程式，而不會附加 Visual Studio 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="dd995-236">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="dd995-237">若要在不自動啟動應用程式的情況下部署裝置，選取 [組建] > [部署解決方案]。</span><span class="sxs-lookup"><span data-stu-id="dd995-237">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="dd995-238">您可能會注意到應用程式中的診斷 profiler，您可以使用語音命令「 **切換診斷**」來開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="dd995-238">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **"Toggle Diagnostics"**.</span></span> <span data-ttu-id="dd995-239">建議您在開發期間儘量讓分析工具保持可見，以了解應用程式的變更何時會對效能產生影響。</span><span class="sxs-lookup"><span data-stu-id="dd995-239">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="dd995-240">例如，HoloLens 應用程式應該[持續以 60 FPS 執行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="dd995-240">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="dd995-241">恭喜！</span><span class="sxs-lookup"><span data-stu-id="dd995-241">Congratulations</span></span>

<span data-ttu-id="dd995-242">您現在已部署了第一個 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dd995-242">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="dd995-243">開啟應用程式之後，您應該會看到 Cube 物件放在您面前，而且應該可以移動它來與 cube 互動，您應該會看到空間對應網格，其中涵蓋了 HoloLens 所察覺的介面。</span><span class="sxs-lookup"><span data-stu-id="dd995-243">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="dd995-244">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="dd995-244">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="dd995-245">這些功能只是 MRTK 所包含的幾個基本部分。</span><span class="sxs-lookup"><span data-stu-id="dd995-245">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="dd995-246">在接下來的教學課程中，您將會在場景中新增內容，以探索 HoloLens 和 MRTK 的功能。</span><span class="sxs-lookup"><span data-stu-id="dd995-246">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dd995-247">下一個教學課程：3.設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="dd995-247">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
