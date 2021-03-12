---
title: 初始化您的專案並部署您的第一個應用程式
description: 本課程說明如何為混合實境工具組 (MRTK) 設定 Unity 專案，以及如何將其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 8a1d93f4cd321c23410f537e0577192421ef3af1
ms.sourcegitcommit: daad3dcce6381e2967fab634313dc7b2ea26d2bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2021
ms.locfileid: "103234554"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="d58ee-104">2.初始化您的專案並部署您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="d58ee-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="d58ee-105">在本教學課程中，您將了解如何建立新的 Unity 專案、將其設定為<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合實境工具組 (MRTK)</a>開發之用，以及匯入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="d58ee-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="d58ee-106">您也將逐步了解如何設定和建置基本 Unity 場景，並將其從 Visual Studio 部署到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="d58ee-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="d58ee-107">將其部署到 HoloLens 2 之後，您應該會看到一個空間對應網格，其中涵蓋 HoloLens 所感知到的介面。</span><span class="sxs-lookup"><span data-stu-id="d58ee-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="d58ee-108">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="d58ee-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="d58ee-109">目標</span><span class="sxs-lookup"><span data-stu-id="d58ee-109">Objectives</span></span>

* <span data-ttu-id="d58ee-110">了解如何設定 Unity 以用於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="d58ee-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="d58ee-111">了解如何建置應用程式並部署至 HoloLens</span><span class="sxs-lookup"><span data-stu-id="d58ee-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="d58ee-112">體驗 HoloLens 2 裝置上的空間對應網格、手部網格和畫面播放速率計數器</span><span class="sxs-lookup"><span data-stu-id="d58ee-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="d58ee-113">建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="d58ee-113">Creating the Unity project</span></span>

<span data-ttu-id="d58ee-114">啟動 **Unity Hub**，選取 [專案] 索引標籤，然後按一下 [新增] 按鈕旁的 **向下箭號**：</span><span class="sxs-lookup"><span data-stu-id="d58ee-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![已醒目提示 [新增] 按鈕的 Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="d58ee-116">在下拉式清單中，選取 [必要條件](mr-learning-base-01.md#prerequisites)中所指定的 Unity **版本**：</span><span class="sxs-lookup"><span data-stu-id="d58ee-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![具有新版本選取器下拉式清單的 Unity Hub](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="d58ee-118">如果 Unity Hub 中無法使用特定的 Unity 版本，您可以從 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下載封存</a>起始安裝。</span><span class="sxs-lookup"><span data-stu-id="d58ee-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="d58ee-119">在 [建立新專案] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="d58ee-119">In the Create a new project window:</span></span>

* <span data-ttu-id="d58ee-120">確定 [範本] 設定為 [3D]</span><span class="sxs-lookup"><span data-stu-id="d58ee-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="d58ee-121">輸入適當的 [專案名稱]，例如 MRTK Tutorials</span><span class="sxs-lookup"><span data-stu-id="d58ee-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="d58ee-122">選擇適當的 [位置] 來儲存您的專案，例如 D:\MixedRealityLearning</span><span class="sxs-lookup"><span data-stu-id="d58ee-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="d58ee-123">按一下 [建立] 按鈕，以建立並啟動新的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="d58ee-123">Click the **Create** button to create and launch your new Unity project</span></span>

![已填入 [建立新專案] 視窗的 Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="d58ee-125">在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="d58ee-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="d58ee-126">因此，您應該將 Unity 專案儲存在磁碟機的根目錄附近。</span><span class="sxs-lookup"><span data-stu-id="d58ee-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="d58ee-127">等候 Unity 建立專案：</span><span class="sxs-lookup"><span data-stu-id="d58ee-127">Wait for Unity to create the project:</span></span>

![Unity 正在建立新專案](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="d58ee-129">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="d58ee-129">Switching the build platform</span></span>

<span data-ttu-id="d58ee-130">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="d58ee-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity [建置設定] 功能表路徑](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="d58ee-132">在 [組建設定] 視窗中，選取 [通用 Windows 平台]，然後按一下 [切換平台] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="d58ee-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![已選取 UWP 以從 [獨立式] 平台進行切換的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="d58ee-134">等候 Unity 完成平台的切換：</span><span class="sxs-lookup"><span data-stu-id="d58ee-134">Wait for Unity to finish switching the platform:</span></span>

![Unity 正在切換平台](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="d58ee-136">當 Unity 完成平台切換之後，按一下紅色 **x** 圖示以關閉 [組建設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="d58ee-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![已醒目提示 [關閉] 圖示的 Unity 建置視窗](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="d58ee-138">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="d58ee-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="d58ee-139">在 Unity 功能表中，選取 [視窗] >  [TextMeshPro]  >  [匯入 TMP 基本資源] 以開啟 [匯入 Unity 套件] 視窗：</span><span class="sxs-lookup"><span data-stu-id="d58ee-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity [匯入 TMP 基本資源] 功能表路徑](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="d58ee-141">在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：</span><span class="sxs-lookup"><span data-stu-id="d58ee-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity [TMP 基本資源] 匯入視窗](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="d58ee-143">MRTK 的 UI 元素需要 TextMeshPro 基本資源。</span><span class="sxs-lookup"><span data-stu-id="d58ee-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="d58ee-144">如果您不打算在專案中使用 MRTK 的 UI 元素，則可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="d58ee-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="d58ee-145">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="d58ee-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="d58ee-146">若要將混合現實工具組匯入 Unity 專案中，您必須使用「 [混合現實」功能工具](https://docs.microsoft.com//windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) ，讓開發人員能夠探索、更新和新增混合現實功能套件至 unity 專案。</span><span class="sxs-lookup"><span data-stu-id="d58ee-146">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](https://docs.microsoft.com//windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="d58ee-147">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="d58ee-147">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="d58ee-148">請從 [Microsoft 下載中心](https://aka.ms/MRFeatureTool)下載最新版本的混合現實功能工具，下載完成後，請將檔案解壓縮，並將其儲存到您的桌面。</span><span class="sxs-lookup"><span data-stu-id="d58ee-148">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="d58ee-149">在您可以執行混合現實功能工具之前，請先定[.net 5.0 運行](https://dotnet.microsoft.com/download/dotnet/5.0)時間</span><span class="sxs-lookup"><span data-stu-id="d58ee-149">Before you can run the Mixed Reality Feature Tool please instal [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="d58ee-150">混合現實功能工具目前只在 Windows 上執行，若為 MacOS，請依照此程式下載並匯入混合現實工具 [組至 unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) 專案。</span><span class="sxs-lookup"><span data-stu-id="d58ee-150">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="d58ee-151">您也可以從 [MRTK Github 的 [發行] 頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)手動下載 MRTK 套件。</span><span class="sxs-lookup"><span data-stu-id="d58ee-151">You can also manually download MRTK packages from [MRTK Github's release page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="d58ee-152">使用 Unity 的資產匯入 MRTK 套件-> 匯入套件-> 自訂套件] 功能表。</span><span class="sxs-lookup"><span data-stu-id="d58ee-152">Import MRTK packages using Unity's Asset -> Import Package -> Custom Package menu.</span></span> 


<span data-ttu-id="d58ee-153">從下載的資料夾開啟可執行檔 **MixedRealityFeatureTool** ，以啟動「混合現實」功能工具。</span><span class="sxs-lookup"><span data-stu-id="d58ee-153">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![開啟 MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="d58ee-155">開啟 **MixedRealityFeatureTool** 之後，請按一下 [開始] 以開始使用混合現實功能工具。</span><span class="sxs-lookup"><span data-stu-id="d58ee-155">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="d58ee-157">功能會依類別目錄分組，讓您更容易找到這些專案，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單，以尋找與混合現實工具組相關的套件。</span><span class="sxs-lookup"><span data-stu-id="d58ee-157">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![MixedRealityFeatureTool 視窗](images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="d58ee-159">檢查 **Mixed Reality 工具組 Foundation**，然後按一下其旁邊的下拉式清單，以選取所需的 MRTK 版本，在此教學課程系列中，請選取 [ **2.5.3**]。</span><span class="sxs-lookup"><span data-stu-id="d58ee-159">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the required MRTK version, for this tutorial series please select **2.5.3**.</span></span> <span data-ttu-id="d58ee-160">然後按一下 [ **取得功能** ] 按鈕，以下載選取的封裝。</span><span class="sxs-lookup"><span data-stu-id="d58ee-160">then click on **Get features** button to download the selected packages.</span></span>

![選取混合的現實基礎](images/mr-learning-base/base-02-section4-step1-4.png)

<span data-ttu-id="d58ee-162">在 [匯 **入功能**] 視窗中會顯示選取的套件 **混合現實工具組 Foundation 2.5.3** ，以及其相依套件 **混合現實工具組標準資產 2.5.3** 。</span><span class="sxs-lookup"><span data-stu-id="d58ee-162">Selected package **Mixed Reality Toolkit Foundation 2.5.3** is presented, along with its dependence package **Mixed Reality Toolkit Standard Assets 2.5.3** in the **Import Features** window.</span></span>

<span data-ttu-id="d58ee-163">您也需要設定目標 unity 專案的位置以提供 **專案路徑**，按一下專案路徑旁的 **三個點** ，然後在 explorer 中流覽至您的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。</span><span class="sxs-lookup"><span data-stu-id="d58ee-163">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="d58ee-164">流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。</span><span class="sxs-lookup"><span data-stu-id="d58ee-164">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="d58ee-165">檔案名必須有一個值，才能選取該資料夾。</span><span class="sxs-lookup"><span data-stu-id="d58ee-165">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="d58ee-166">接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d58ee-166">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![驗證混合的現實基礎](images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="d58ee-168">按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。</span><span class="sxs-lookup"><span data-stu-id="d58ee-168">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![核准混合的現實基礎](images/mr-learning-base/base-02-section4-step1-6.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="d58ee-170">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="d58ee-170">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="d58ee-171">1.套用 MRTK 專案配置器設定</span><span class="sxs-lookup"><span data-stu-id="d58ee-171">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="d58ee-172">Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="d58ee-172">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d58ee-173">如果沒有出現，請至 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 手動開啟視窗。</span><span class="sxs-lookup"><span data-stu-id="d58ee-173">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity [設定 Unity 專案] 功能表路徑](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="d58ee-175">在 [MRTK 專案設定程式] 視窗中，展開 [修改設定] 區段，確定已勾選所有其他選項，然後按一下 [套用] 按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="d58ee-175">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Unity [MRTK 專案設定程式] 視窗](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="d58ee-177">您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：</span><span class="sxs-lookup"><span data-stu-id="d58ee-177">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="d58ee-178">設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。</span><span class="sxs-lookup"><span data-stu-id="d58ee-178">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="d58ee-179">若要深入了解本主題，您可以參閱 MRTK [效能](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering)文件中的[單一階段執行個體化轉譯](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering)一節。</span><span class="sxs-lookup"><span data-stu-id="d58ee-179">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="d58ee-180">設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="d58ee-180">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="d58ee-181">若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。</span><span class="sxs-lookup"><span data-stu-id="d58ee-181">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="d58ee-182">2.設定其他專案設定</span><span class="sxs-lookup"><span data-stu-id="d58ee-182">2. Configure additional project settings</span></span>

<span data-ttu-id="d58ee-183">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="d58ee-183">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="d58ee-184">在 [專案設定] 視窗中，選取 [ **Player**  >  **XR 設定**] 並勾選 [**支援虛擬實境**] 核取方塊，然後按一下 **+** 圖示，然後選取 [windows mixed reality] 以新增 windows mixed reality SDK：</span><span class="sxs-lookup"><span data-stu-id="d58ee-184">In the Project Settings window, select **Player** > **XR Settings** and check the **Virtual Reality Supported** checkbox then click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![已選取新增 [Windows Mixed Reality] SDK 的 Unity XR 設定](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="d58ee-186">Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="d58ee-186">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="d58ee-187">如果沒有，您可以從 Unity 功能表手動開啟它，方法是前往 **混合現實工具** 組  >  **公用程式**  >  **設定 Unity 專案**</span><span class="sxs-lookup"><span data-stu-id="d58ee-187">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="d58ee-188">在 [MRTK 專案設定] 視窗中，使用 **Audio 空間定位器** 下拉式清單選取 [MS HRTF 空間定位器]，然後按一下 [套用] 按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="d58ee-188">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![已選取 [新增 Windows Mixed Reality SDK] 選項的 Unity XR 設定](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="d58ee-190">您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="d58ee-190">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="d58ee-191">如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="d58ee-191">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="d58ee-192">若要深入瞭解本主題，您可以參考  <a href="https://docs.microsoft.com//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。</span><span class="sxs-lookup"><span data-stu-id="d58ee-192">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="d58ee-193">在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，然後使用 **深度格式** 下拉式清單選取 **16 位元深度**：</span><span class="sxs-lookup"><span data-stu-id="d58ee-193">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 啟用16深度](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="d58ee-195">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="d58ee-195">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="d58ee-196">若要深入瞭解本主題，您可以參考 MRTK 的<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">效能</a>檔中的<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering#depth-buffer-sharing-hololens" target="_blank">深度緩衝區共用 (HoloLens) </a>一節。</span><span class="sxs-lookup"><span data-stu-id="d58ee-196">To learn more about this topic, you can refer to the   <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="d58ee-197">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="d58ee-197">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![已設定 [套件名稱] 的 Unity [發佈設定]](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="d58ee-199">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d58ee-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="d58ee-200">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d58ee-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="d58ee-201">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="d58ee-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="d58ee-202">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="d58ee-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="d58ee-203">建立和設定場景</span><span class="sxs-lookup"><span data-stu-id="d58ee-203">Creating and configuring the scene</span></span>

<span data-ttu-id="d58ee-204">在 Unity 功能表中，選取 [檔案] > [新增場景] 以建立新場景：</span><span class="sxs-lookup"><span data-stu-id="d58ee-204">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity [新增場景] 功能表路徑](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="d58ee-206">在 Unity 功能表中，選取 [混合實境工具組] >  [新增至場景並設定...] 來將 MRTK 新增至目前的場景：</span><span class="sxs-lookup"><span data-stu-id="d58ee-206">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity [新增至場景並設定...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="d58ee-208">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件後，在 [偵測器] 視窗中，驗證 **MixedRealityToolkit** 設定中的設定檔是否變更為 **DefaultMixedRealityToolkitConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="d58ee-208">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![已選取 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="d58ee-210">在 Unity 功能表中，選取 [檔案] >  [另存新檔 ...] 以開啟 [儲存場景] 視窗：</span><span class="sxs-lookup"><span data-stu-id="d58ee-210">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity [另存新檔...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="d58ee-212">在 [儲存場景] 視窗中，瀏覽至專案的 **Scenes** 資料夾，為您的場景取一個適當的名稱，例如 _GettingStarted_，然後按一下 [儲存] 按鈕以儲存場景：</span><span class="sxs-lookup"><span data-stu-id="d58ee-212">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Unity [儲存場景] 的 [儲存] 提示視窗](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="d58ee-214">在您的 HoloLens 2 上建置應用程式</span><span class="sxs-lookup"><span data-stu-id="d58ee-214">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="d58ee-215">1.組建 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="d58ee-215">1. Build the Unity project</span></span>

<span data-ttu-id="d58ee-216">在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="d58ee-216">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="d58ee-217">在 [組建設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至 [組建中的場景] 清單，然後按一下 [組建] 按鈕以開啟 [組建通用 Windows 平台] 視窗：</span><span class="sxs-lookup"><span data-stu-id="d58ee-217">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![已選取 UWP 的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="d58ee-219">在 [組建通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的組建，例如 D:\MixedRealityLearning\Builds，建立新的資料夾並指定適當的名稱，例如 GettingStarted，然後按一下 [選取資料夾] 按鈕開始組建程序：</span><span class="sxs-lookup"><span data-stu-id="d58ee-219">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![具有 [選取資料夾] 提示視窗的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="d58ee-221">等候 Unity 完成組建程序：</span><span class="sxs-lookup"><span data-stu-id="d58ee-221">Wait for Unity to finish the build process:</span></span>

![Unity 正在進行建置程序](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="d58ee-223">2.組建和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="d58ee-223">2. Build and deploy the application</span></span>

<span data-ttu-id="d58ee-224">當建置程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。</span><span class="sxs-lookup"><span data-stu-id="d58ee-224">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="d58ee-225">瀏覽該資料夾，按兩下解決方案的檔案即可在 Visual Studio 中開啟該檔案：</span><span class="sxs-lookup"><span data-stu-id="d58ee-225">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Windows 檔案總管，其中已選取新建立的 Visual Studio 解決方案](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d58ee-227">如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同 **[安裝工具](../../install-the-tools.md)** 文件中所述。</span><span class="sxs-lookup"><span data-stu-id="d58ee-227">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="d58ee-228">設定 Visual Studio 以便用於 HoloLens，請選取 [Master] 或 [Release] 設定、[ARM64] 架構，選取 [裝置] 作為目標：</span><span class="sxs-lookup"><span data-stu-id="d58ee-228">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![已針對要部署至 HoloLens 2 來設定 Visual Studio](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="d58ee-230">如果您要部署至 HoloLens (第1代)，請選取 **x86** 架構。</span><span class="sxs-lookup"><span data-stu-id="d58ee-230">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="d58ee-231">若是 HoloLens，您通常會建立 ARM 架構。</span><span class="sxs-lookup"><span data-stu-id="d58ee-231">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="d58ee-232">不過，在 Visual Studio 中選取 ARM 作為建置架構時，Unity 2019.3 中的<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知問題</strong></a>會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="d58ee-232">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="d58ee-233">建議的解決方法是以 ARM64 建置。</span><span class="sxs-lookup"><span data-stu-id="d58ee-233">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="d58ee-234">如果無法這麼做，請移至 **編輯 > 專案設定 > 播放程式 > 其他設定** 並停用 **圖形作業**。</span><span class="sxs-lookup"><span data-stu-id="d58ee-234">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="d58ee-235">如果您看不到 [裝置為目標] 選項，可能需要將 Visual Studio 解決方案的啟始專案從 IL2CPP 專案變更為 UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="d58ee-235">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="d58ee-236">要這麼做，在方案總管中，以滑鼠右鍵按一下 YourProjectName (Universal Windows) 並選取 [設定為啟動專案]。</span><span class="sxs-lookup"><span data-stu-id="d58ee-236">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="d58ee-237">將 HoloLens 與電腦連線，然後選取 [偵錯] > [啟動但不進行偵錯]，以建置並部署至您的裝置：</span><span class="sxs-lookup"><span data-stu-id="d58ee-237">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio [啟動但不進行偵錯] 功能表路徑](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="d58ee-239">在組建您的裝置之前，裝置必須處於「開發人員模式」，並與開發電腦配對。</span><span class="sxs-lookup"><span data-stu-id="d58ee-239">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="d58ee-240">請遵循[這些指示](../../platform-capabilities-and-apis/using-visual-studio.md)來完成這兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="d58ee-240">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="d58ee-241">您也可以部署到 [HoloLens 模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或為側載建立[應用程式套件](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)。</span><span class="sxs-lookup"><span data-stu-id="d58ee-241">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="d58ee-242">使用 [啟動但不進行偵測] 會自動啟動您裝置上的應用程式，而不會附加 Visual Studio 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d58ee-242">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="d58ee-243">若要在不自動啟動應用程式的情況下部署裝置，選取 [組建] > [部署解決方案]。</span><span class="sxs-lookup"><span data-stu-id="d58ee-243">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="d58ee-244">您可能會注意到應用程式中的診斷分析工具，您可以使用 **Toggle Diagnostics** 語音命令開啟或關閉此工具。</span><span class="sxs-lookup"><span data-stu-id="d58ee-244">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="d58ee-245">建議您在開發期間儘量讓分析工具保持可見，以了解應用程式的變更何時會對效能產生影響。</span><span class="sxs-lookup"><span data-stu-id="d58ee-245">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="d58ee-246">例如，HoloLens 應用程式應該[持續以 60 FPS 執行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="d58ee-246">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="d58ee-247">恭喜！</span><span class="sxs-lookup"><span data-stu-id="d58ee-247">Congratulations</span></span>

<span data-ttu-id="d58ee-248">您現在已部署了第一個 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d58ee-248">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="d58ee-249">當您隨處走動時，應該會看到空間對應網格涵蓋了所有 HoloLens 所感知到的表面。</span><span class="sxs-lookup"><span data-stu-id="d58ee-249">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="d58ee-250">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="d58ee-250">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="d58ee-251">這些功能只是 MRTK 所包含的幾個基本部分。</span><span class="sxs-lookup"><span data-stu-id="d58ee-251">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="d58ee-252">在接下來的教學課程中，您將會在場景中新增內容，以探索 HoloLens 和 MRTK 的功能。</span><span class="sxs-lookup"><span data-stu-id="d58ee-252">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d58ee-253">下一個教學課程：3.設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="d58ee-253">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
