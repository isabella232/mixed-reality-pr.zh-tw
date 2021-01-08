---
title: MRTK 教學課程 - 2. 初始化您的專案並部署您的第一個應用程式
description: 本課程說明如何為混合實境工具組 (MRTK) 設定 Unity 專案，以及如何將其部署到 HoloLens 2。
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859527"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="e73cf-105">2.初始化您的專案並部署您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="e73cf-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="e73cf-106">概觀</span><span class="sxs-lookup"><span data-stu-id="e73cf-106">Overview</span></span>

<span data-ttu-id="e73cf-107">在本教學課程中，您將了解如何建立新的 Unity 專案、將其設定為<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合實境工具組 (MRTK)</a>開發之用，以及匯入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="e73cf-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="e73cf-108">您也將逐步了解如何設定和建置基本 Unity 場景，並將其從 Visual Studio 部署到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e73cf-108">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="e73cf-109">將其部署到 HoloLens 2 之後，您應該會看到一個空間對應網格，其中涵蓋 HoloLens 所感知到的介面。</span><span class="sxs-lookup"><span data-stu-id="e73cf-109">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="e73cf-110">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="e73cf-110">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="e73cf-111">目標</span><span class="sxs-lookup"><span data-stu-id="e73cf-111">Objectives</span></span>

* <span data-ttu-id="e73cf-112">了解如何設定 Unity 以用於 HoloLens 開發。</span><span class="sxs-lookup"><span data-stu-id="e73cf-112">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="e73cf-113">了解如何建置應用程式並部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e73cf-113">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="e73cf-114">體驗 HoloLens 2 裝置上的空間對應網格、手部網格和畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="e73cf-114">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="e73cf-115">建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="e73cf-115">Creating the Unity project</span></span>

1. <span data-ttu-id="e73cf-116">啟動 **Unity Hub**，選取 [專案] 索引標籤，然後按一下 [新增] 按鈕旁的 **向下箭號**：</span><span class="sxs-lookup"><span data-stu-id="e73cf-116">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

![已反白顯示 [新增] 按鈕向下箭號的 Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="e73cf-118">在下拉式功能表中，選取[必要條件](mr-learning-base-01.md#prerequisites)中所指定的 Unity 版本：</span><span class="sxs-lookup"><span data-stu-id="e73cf-118">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![選取 Unity 版本](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="e73cf-120">如果 Unity Hub 中無法使用特定的 Unity 版本，您可以從 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下載封存</a>起始安裝。</span><span class="sxs-lookup"><span data-stu-id="e73cf-120">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="e73cf-121">在 [建立新專案] 視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e73cf-121">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="e73cf-122">確定 [範本] 設定為 [3D]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-122">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="e73cf-123">在 [專案名稱] 方塊中，為您的專案輸入適當的名稱 (例如「MRTK 教學課程」)。</span><span class="sxs-lookup"><span data-stu-id="e73cf-123">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="e73cf-124">按一下 [位置] 旁的三個點按鈕，然後瀏覽至您要儲存專案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e73cf-124">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="e73cf-125">在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="e73cf-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="e73cf-126">因此，您應該將 Unity 專案儲存在磁碟機的根目錄附近。</span><span class="sxs-lookup"><span data-stu-id="e73cf-126">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="e73cf-127">按一下 [ **建立** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e73cf-127">Click the **Create** button.</span></span> <span data-ttu-id="e73cf-128">這會建立並啟動新的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="e73cf-128">This creates and launches your new Unity project.</span></span>

![已填入 [建立新專案] 視窗的 Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="e73cf-130">狀態列會持續更新您的進度。</span><span class="sxs-lookup"><span data-stu-id="e73cf-130">The status bar keeps you updated on your progress.</span></span>

![Unity 進度列會持續更新您的「建立專案」狀態](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="e73cf-132">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="e73cf-132">Switching the build platform</span></span>

1. <span data-ttu-id="e73cf-133">在功能表列上，選取 [檔案] > [建置設定...]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-133">On the menu bar, select **File** > **Build Settings...**</span></span>

![Unity [建置設定] 功能表路徑](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="e73cf-135">在 [建置設定] 視窗中，選取 [通用 Windows 平台]，然後按一下 [切換平台] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="e73cf-135">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![已選取 UWP 以從 [獨立式] 平台進行切換的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="e73cf-137">等候 Unity 完成平台切換，然後關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e73cf-137">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="e73cf-138">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="e73cf-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="e73cf-139">MRTK 的 UI 元素需要 TextMeshPro 基本資源。</span><span class="sxs-lookup"><span data-stu-id="e73cf-139">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="e73cf-140">如果您不打算在專案中使用 MRTK 的 UI 元素，可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="e73cf-140">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="e73cf-141">在功能表列上，選取 [視窗] >  [TextMeshPro]  >  [匯入 TMP 基本資源]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-141">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Unity [匯入 TMP 基本資源] 功能表路徑](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="e73cf-143">在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：</span><span class="sxs-lookup"><span data-stu-id="e73cf-143">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Unity [TMP 基本資源] 匯入視窗](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="e73cf-145">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="e73cf-145">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="e73cf-146">下載 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="e73cf-146">Download the Unity custom package:</span></span>

    [<span data-ttu-id="e73cf-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="e73cf-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="e73cf-148">在功能表列上，選取 [資產] > [匯入套件] > [自訂套件...]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-148">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="e73cf-149">在 [匯入套件...] 對話方塊中，瀏覽至您剛下載套件的位置，加以選取，然後按一下 [開啟] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e73cf-149">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="e73cf-150">在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產。</span><span class="sxs-lookup"><span data-stu-id="e73cf-150">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="e73cf-151">選取 MRTK 和專案設定</span><span class="sxs-lookup"><span data-stu-id="e73cf-151">Selecting MRTK and project settings</span></span>

<span data-ttu-id="e73cf-152">Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e73cf-152">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="e73cf-153">如果沒有出現，請至 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 手動開啟視窗。</span><span class="sxs-lookup"><span data-stu-id="e73cf-153">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity [設定 Unity 專案] 功能表路徑](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="e73cf-155">在 [MRTK 專案設定程式] 視窗中，展開 [修改設定] 區段，(如有需要) 然後確定已選取所有選項。</span><span class="sxs-lookup"><span data-stu-id="e73cf-155">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![顯示 [修改設定] 的 Unity MRTK 專案配置器視窗](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="e73cf-157">若要套用設定，請按一下 [套用] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e73cf-157">To apply the settings, click the **Apply** button.</span></span>

![MRTK 中的 [套用] 按鈕](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="e73cf-159">您之所以使用 Unity 的內建舊版 XR，而不是新的 XR 外掛程式系統，是因為新系統與本教學課程系列的[建議的 Unity 和 MRTK 版本](mr-learning-base-01.md#prerequisites)未能完全相容。</span><span class="sxs-lookup"><span data-stu-id="e73cf-159">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="e73cf-160">如果您看到任何關於內建 XR 即將淘汰的警告，您可予以忽略。</span><span class="sxs-lookup"><span data-stu-id="e73cf-160">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="e73cf-161">您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：</span><span class="sxs-lookup"><span data-stu-id="e73cf-161">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="e73cf-162">啟用舊版 XR：為專案啟用 VR。</span><span class="sxs-lookup"><span data-stu-id="e73cf-162">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="e73cf-163">設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。</span><span class="sxs-lookup"><span data-stu-id="e73cf-163">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="e73cf-164">若要深入了解本主題，您可以參閱 MRTK [效能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文件中的[單一階段執行個體化轉譯](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)一節。</span><span class="sxs-lookup"><span data-stu-id="e73cf-164">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="e73cf-165">設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="e73cf-165">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="e73cf-166">若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。</span><span class="sxs-lookup"><span data-stu-id="e73cf-166">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="e73cf-167">在功能表列上，選取 [編輯] > [專案設定...]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-167">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="e73cf-168">在 [專案設定] 視窗中，選取 [播放程式]，然後按一下 [XR 設定] 下拉式清單，然後選取 [支援虛擬實境] 旁的方塊：</span><span class="sxs-lookup"><span data-stu-id="e73cf-168">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![顯示支援虛擬實境的 Unity XR 設定](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="e73cf-170">這會匯入 Windows Mixed Reality SDK：</span><span class="sxs-lookup"><span data-stu-id="e73cf-170">This imports the Windows Mixed Reality SDK:</span></span>

![顯示虛擬實境 SDK 的 Unity XR 設定](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="e73cf-172">Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e73cf-172">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="e73cf-173">如果沒有出現，請選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 加以開啟。</span><span class="sxs-lookup"><span data-stu-id="e73cf-173">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="e73cf-174">在 [MRTK 專案配置器] 視窗中，按一下 [音訊空間定位器] 下拉式清單，然後選取 [MS HRTF 空間定位器]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-174">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![顯示音訊空間定位器選項的專案設定](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="e73cf-176">按一下 [套用]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="e73cf-176">Click the **Apply** button.</span></span> <span data-ttu-id="e73cf-177">這會關閉 [MRTK 專案設定程式] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e73cf-177">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="e73cf-178">您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="e73cf-178">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="e73cf-179">如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="e73cf-179">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="e73cf-180">若要深入了解本主題，您可以參閱空間音訊教學課程。</span><span class="sxs-lookup"><span data-stu-id="e73cf-180">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="e73cf-181">在 [專案設定] 視窗中，按一下 [深度格式] 下拉式清單，然後選取 [16 位元深度]：</span><span class="sxs-lookup"><span data-stu-id="e73cf-181">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="已選取 [16 位元深度] 的 Unity XR 設定。":::

    > [!TIP]
    > <span data-ttu-id="e73cf-183">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="e73cf-183">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="e73cf-184">若要深入了解本主題，您可以參閱 MRTK [效能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文件中的[深度緩衝區共用 (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) 一節。</span><span class="sxs-lookup"><span data-stu-id="e73cf-184">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="e73cf-185">按一下 [發佈設定] 下拉式單，然後在 [套件名稱] 方塊中，輸入適當的名稱 (例如 "MRTK-Tutorials-Getting-Started")。</span><span class="sxs-lookup"><span data-stu-id="e73cf-185">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="已設定 [套件名稱] 的 Unity [發佈設定]。":::

    <span data-ttu-id="e73cf-187">**套件名稱和產品名稱**</span><span class="sxs-lookup"><span data-stu-id="e73cf-187">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="e73cf-188">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="e73cf-188">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="e73cf-189">您應該在部署應用程式之前建立此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e73cf-189">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="e73cf-190">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="e73cf-190">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="e73cf-191">若要在開發期間更容易找到應用程式，您可以在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="e73cf-191">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="已設定產品名稱的 Unity 專案設定。":::

9. <span data-ttu-id="e73cf-193">關閉 [專案設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e73cf-193">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="e73cf-194">建立和設定場景</span><span class="sxs-lookup"><span data-stu-id="e73cf-194">Creating and configuring the scene</span></span>

1. <span data-ttu-id="e73cf-195">在功能表列上，選取 [檔案] > [新場景]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-195">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="e73cf-196">若要將 MRTK 新增至場景，請在功能表上，選取 [混合實境工具組] > [新增至場景並設定...]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-196">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity [新增至場景並設定...] 功能表路徑。":::

3. <span data-ttu-id="e73cf-198">在 [階層] 視窗中，確定已選取 [MixedRealityToolkit]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-198">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="確定已選取 MixedRealityTookit。":::

4. <span data-ttu-id="e73cf-200">在 [偵測器] 視窗的 [MixedRealityToolkit] 區段中，確認組態設定檔已設為 [DefaultMixedRealityToolkitConfigurationProfile]：</span><span class="sxs-lookup"><span data-stu-id="e73cf-200">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="已選取 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 元件。":::

    > [!IMPORTANT]
    > <span data-ttu-id="e73cf-202">通常，在開發 HoloLens 時會使用 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="e73cf-202">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="e73cf-203">不過，在本教學課程中，您將使用 DefaultMixedRealityToolkitConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="e73cf-203">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="e73cf-204">在下一個教學課程[設定 MRTK 設定檔](mr-learning-base-03.md)中，您將變更為 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="e73cf-204">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="e73cf-205">在功能表列上，選取 [檔案] > [另存新檔...]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-205">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="e73cf-206">在 [儲存場景] 對話方塊中，瀏覽至專案的 [場景] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e73cf-206">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="e73cf-207">在 [檔案檔案] 方塊中，為您的場景提供適當的名稱 (例如 "\_GettingStarted\_")，然後按一下 [儲存] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e73cf-207">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Unity [儲存場景] 的 [儲存] 提示視窗。":::

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="e73cf-209">建立及部署至您的 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e73cf-209">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="e73cf-210">在建立到您的裝置之前，請確認下列事項：</span><span class="sxs-lookup"><span data-stu-id="e73cf-210">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="e73cf-211">您的裝置處於開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="e73cf-211">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="e73cf-212">您的裝置與您的開發電腦配對。</span><span class="sxs-lookup"><span data-stu-id="e73cf-212">Your device is paired with your development computer.</span></span> <span data-ttu-id="e73cf-213">如果沒有，您會在建置過程中，於 Visual Studio 中看到下列對話方塊：</span><span class="sxs-lookup"><span data-stu-id="e73cf-213">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![輸入配對裝置的 PIN](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="e73cf-215">若要深入了解這兩個步驟，請參閱[使用 Visual Studio 進行部署和偵錯](../../platform-capabilities-and-apis/using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e73cf-215">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="e73cf-216">在功能表列上，選取 [檔案] > [建置設定...]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-216">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="e73cf-217">在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至 [建置中的場景] 清單。</span><span class="sxs-lookup"><span data-stu-id="e73cf-217">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

![將您目前的場景新增至「建置中的場景」清單](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="e73cf-219">按一下 [組建] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e73cf-219">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="按一下 [組建] 按鈕。":::

4. <span data-ttu-id="e73cf-221">在 [建置通用 Windows 平台] 對話方塊中，選擇適當的位置來儲存您的組建 (例如，您可能想要在「MRTK 教學課程」資料夾中建立「組建」資料夾)。</span><span class="sxs-lookup"><span data-stu-id="e73cf-221">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="e73cf-222">建立新的資料夾並為其指定適當的名稱 (例如 "GettingStarted")，然後選取該資料夾，按一下 [選取資料夾] 按鈕來啟動建置程序。</span><span class="sxs-lookup"><span data-stu-id="e73cf-222">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="顯示您的組建資料夾的 [Unity 組建] 視窗。":::

    <span data-ttu-id="e73cf-224">狀態列隨即出現，並持續更新您的建置進度。</span><span class="sxs-lookup"><span data-stu-id="e73cf-224">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Unity 正在進行建置程序。":::

    > [!TIP]
    > <span data-ttu-id="e73cf-226">您也可以部署到 [HoloLens 模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或為側載建立[應用程式套件](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)。</span><span class="sxs-lookup"><span data-stu-id="e73cf-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="e73cf-227">當建置程序完成時，在 [檔案總管] 中，瀏覽至您儲存組建的位置，然後按兩下解決方案檔案以在 Visual Studio 中開啟：</span><span class="sxs-lookup"><span data-stu-id="e73cf-227">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Windows 檔案總管，其中已選取新建立的 Visual Studio 解決方案檔案。":::

    > [!NOTE]
    > <span data-ttu-id="e73cf-229">如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同 **[安裝工具](../../install-the-tools.md)** 文件中所述。</span><span class="sxs-lookup"><span data-stu-id="e73cf-229">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="e73cf-230">設定 Visual Studio 以便用於 HoloLens，請選取 [Master] 或 [Release] 設定、[ARM64] 架構，選取 [裝置] 作為目標。</span><span class="sxs-lookup"><span data-stu-id="e73cf-230">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="e73cf-231">如果您要部署至 HoloLens (第1代)，請選取 **x86** 架構。</span><span class="sxs-lookup"><span data-stu-id="e73cf-231">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="已針對要部署至 HoloLens 2 來設定 Visual Studio。":::

    > [!NOTE]
    > <span data-ttu-id="e73cf-233">若是 HoloLens，您通常會建立 ARM 架構。</span><span class="sxs-lookup"><span data-stu-id="e73cf-233">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="e73cf-234">不過，在 Visual Studio 中選取 ARM 作為建置架構時，Unity 2019.3 中的<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知問題</strong></a>會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="e73cf-234">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="e73cf-235">建議的解決方法是以 ARM64 建置。</span><span class="sxs-lookup"><span data-stu-id="e73cf-235">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="e73cf-236">如果無法這麼做，請移至 **編輯 > 專案設定 > 播放程式 > 其他設定** 並停用 **圖形作業**。</span><span class="sxs-lookup"><span data-stu-id="e73cf-236">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e73cf-237">如果您看不到 [裝置為目標] 選項，可能需要將 Visual Studio 解決方案的啟始專案從 IL2CPP 專案變更為 UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="e73cf-237">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="e73cf-238">要這麼做，在方案總管中，以滑鼠右鍵按一下 YourProjectName (Universal Windows)，然後選取 [設定為啟動專案]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-238">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="e73cf-239">將 HoloLens 連接到您的電腦，然後執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="e73cf-239">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="e73cf-240">若要建置應用程式、將其部署至您的 HoloLens，然後在不連結 Visual Studio 偵錯工具的情況下自動啟動，請在功能表列上選取 [偵錯] > [啟動但不偵錯]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-240">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Visual Studio [啟動但不偵錯] 功能表路徑。":::

- <span data-ttu-id="e73cf-242">若要建置應用程式並將其部署至 HoloLens，但不要自動啟動，請在功能表列上，選取 [建置] > [部署解決方案]。</span><span class="sxs-lookup"><span data-stu-id="e73cf-242">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="e73cf-243">您可能會注意到應用程式中的診斷分析工具，您可以使用 **Toggle Diagnostics** 語音命令開啟或關閉此工具。</span><span class="sxs-lookup"><span data-stu-id="e73cf-243">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="e73cf-244">建議您在開發期間儘量讓分析工具保持可見，以了解應用程式的變更何時會對效能產生影響。</span><span class="sxs-lookup"><span data-stu-id="e73cf-244">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="e73cf-245">例如，HoloLens 應用程式應該[持續以 60 FPS 執行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="e73cf-245">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="e73cf-246">恭喜！</span><span class="sxs-lookup"><span data-stu-id="e73cf-246">Congratulations</span></span>

<span data-ttu-id="e73cf-247">您現在已部署了第一個 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e73cf-247">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="e73cf-248">當您隨處走動時，應該會看到空間對應網格涵蓋了所有 HoloLens 所感知到的表面。</span><span class="sxs-lookup"><span data-stu-id="e73cf-248">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="e73cf-249">此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="e73cf-249">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="e73cf-250">這些功能只是 MRTK 所包含的幾個基本部分。</span><span class="sxs-lookup"><span data-stu-id="e73cf-250">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="e73cf-251">在接下來的教學課程中，您將會在場景中新增內容，以探索 HoloLens 和 MRTK 的功能。</span><span class="sxs-lookup"><span data-stu-id="e73cf-251">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e73cf-252">下一個教學課程：3.設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="e73cf-252">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
