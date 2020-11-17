---
title: 空間音訊教學課程-1。 在專案中新增空間音訊
description: 將 Microsoft 空間定位器外掛程式新增至您的 Unity 專案，以存取 HoloLens 2 HRTF 硬體卸載。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器
ms.openlocfilehash: fc657eb22034c1c3fd31aadedfe7b8ea7bb8447d
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679707"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="aa40e-105">將空間音訊新增至 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="aa40e-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="aa40e-106">歡迎使用 HoloLens2 上適用于 Unity 的空間音訊教學課程。</span><span class="sxs-lookup"><span data-stu-id="aa40e-106">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="aa40e-107">此教學課程順序顯示：</span><span class="sxs-lookup"><span data-stu-id="aa40e-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="aa40e-108">如何在 Unity 的 HoloLens 2 上使用 head 相關的傳送函式 (HRTF) 卸載</span><span class="sxs-lookup"><span data-stu-id="aa40e-108">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="aa40e-109">如何在使用 HRTF 卸載時啟用回音</span><span class="sxs-lookup"><span data-stu-id="aa40e-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="aa40e-110">[Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)已完成此教學課程順序的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="aa40e-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="aa40e-111">若要瞭解使用以 HRTF 為基礎的 spatialization 技術來 spatialize 音效的意義，以及如何使用它有説明的建議，請參閱 [空間音效設計](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)。</span><span class="sxs-lookup"><span data-stu-id="aa40e-111">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="aa40e-112">什麼是 HRTF 卸載？</span><span class="sxs-lookup"><span data-stu-id="aa40e-112">What is HRTF offload?</span></span>
<span data-ttu-id="aa40e-113">使用以 HRTF 為基礎的演算法處理音訊需要大量的特製化計算。</span><span class="sxs-lookup"><span data-stu-id="aa40e-113">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="aa40e-114">HoloLens 2 包含專用硬體，可用來避免應用程式處理器額外負荷，進而「卸載」以 HRTF 為基礎的演算法處理。</span><span class="sxs-lookup"><span data-stu-id="aa40e-114">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="aa40e-115">Microsoft 空間定位器外掛程式提供簡單的方法，讓您的應用程式利用專用的 HRTF 硬體，讓您的應用程式可以使用更多應用程式處理器來執行空間音訊以外的作業。</span><span class="sxs-lookup"><span data-stu-id="aa40e-115">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="aa40e-116">目標</span><span class="sxs-lookup"><span data-stu-id="aa40e-116">Objectives</span></span>
<span data-ttu-id="aa40e-117">在第一章中，您將會：</span><span class="sxs-lookup"><span data-stu-id="aa40e-117">In this first chapter, you'll:</span></span>
* <span data-ttu-id="aa40e-118">建立 Unity 專案並匯入 MRTK</span><span class="sxs-lookup"><span data-stu-id="aa40e-118">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="aa40e-119">匯入 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="aa40e-119">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="aa40e-120">啟用 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="aa40e-120">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="aa40e-121">在開發人員工作站上啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="aa40e-121">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="aa40e-122">建立專案並新增 Unity 的 NuGet</span><span class="sxs-lookup"><span data-stu-id="aa40e-122">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="aa40e-123">從空白的 Unity 專案開始，然後新增並設定適用于 Unity 的 NuGet：</span><span class="sxs-lookup"><span data-stu-id="aa40e-123">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="aa40e-124">下載最新的 [NuGetForUnity。 unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="aa40e-124">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="aa40e-125">在 Unity 功能表列中，按一下 [ **資產]-> 匯入封裝-> 自訂套件 ...** ]，然後安裝 NuGetForUnity 套件：</span><span class="sxs-lookup"><span data-stu-id="aa40e-125">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![匯入自訂套件](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="aa40e-127">新增 Windows Mixed Reality 套件</span><span class="sxs-lookup"><span data-stu-id="aa40e-127">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="aa40e-128">Unity 2019 和更新版本中的 Windows Mixed Reality 支援包含在選用套件中。</span><span class="sxs-lookup"><span data-stu-id="aa40e-128">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="aa40e-129">若要將它新增至您的專案，請從 Unity 功能表列開啟 **視窗 > 封裝管理員** ：</span><span class="sxs-lookup"><span data-stu-id="aa40e-129">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![封裝管理員功能表](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="aa40e-131">然後尋找並安裝 **Windows Mixed Reality** 套件：</span><span class="sxs-lookup"><span data-stu-id="aa40e-131">Then find and install the **Windows Mixed Reality** package:</span></span>

![套件管理員視窗](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="aa40e-133">安裝 MRTK 和 Microsoft 空間定位器</span><span class="sxs-lookup"><span data-stu-id="aa40e-133">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="aa40e-134">使用適用于 Unity 的 NuGet，安裝 MRTK 和 Microsoft 空間定位器外掛程式：</span><span class="sxs-lookup"><span data-stu-id="aa40e-134">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="aa40e-135">在 Unity 功能表列中，按一下 [ **nuget-> 管理 Nuget 套件**]。</span><span class="sxs-lookup"><span data-stu-id="aa40e-135">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![管理 NuGet 套件](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="aa40e-137">在 **搜尋** 方塊中，輸入 "MixedReality"，並安裝 MRTK core 套件： **MixedReality。**</span><span class="sxs-lookup"><span data-stu-id="aa40e-137">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![MRTK NuGet 套件](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="aa40e-139">[MRTK NuGet 套件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) 具有其他內容和詳細資料。</span><span class="sxs-lookup"><span data-stu-id="aa40e-139">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="aa40e-140">在 **搜尋** 方塊中，輸入 "SpatialAudio"，並安裝 microsoft 空間定位器 Package： **SpatialAudio. 空間定位器 Unity**</span><span class="sxs-lookup"><span data-stu-id="aa40e-140">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![空間定位器外掛程式 NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="aa40e-142">在您的專案中設定 MRTK</span><span class="sxs-lookup"><span data-stu-id="aa40e-142">Set up MRTK in your project</span></span>

1. <span data-ttu-id="aa40e-143">前往 [檔案 **-> 組建設定**]，開啟 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="aa40e-143">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="aa40e-144">選取 _通用 Windows 平臺_ 然後按一下 [ **切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="aa40e-144">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="aa40e-145">按一下 [**組建] 視窗** 中的 [**播放機設定**]，在 [偵測 **器**] 窗格中開啟 **player 設定** 屬性。</span><span class="sxs-lookup"><span data-stu-id="aa40e-145">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="aa40e-146">在 [ **XR 設定**] 下，勾選 [ **支援虛擬實境** ] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="aa40e-146">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="aa40e-147">在 [ **XR 設定**] 下，將 [ **身歷聲轉譯模式]** 變更為 [ **單一傳遞實例**]。</span><span class="sxs-lookup"><span data-stu-id="aa40e-147">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="aa40e-148">在 [**發行設定**] 下的 [**功能**] 區段中，選取 [**空間感知**] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="aa40e-148">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="aa40e-149">在功能表列上，按一下 [**混合現實工具組-> 加入場景並設定**]。</span><span class="sxs-lookup"><span data-stu-id="aa40e-149">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="aa40e-150">將 MRTK 新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="aa40e-150">to add MRTK to your scene.</span></span>

<span data-ttu-id="aa40e-151">如需其他指引，包括如何建立您的應用程式並部署至 HoloLens 2，請參閱 [MR 學習基底課程模組的第1章](../../../mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="aa40e-151">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="aa40e-152">啟用 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="aa40e-152">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="aa40e-153">啟用 **Microsoft 空間定位器** 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="aa40e-153">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="aa40e-154">開啟 [ **編輯-> 專案設定-> 音訊**]，然後將 **空間定位器外掛程式** 變更為 "Microsoft 空間定位器"。</span><span class="sxs-lookup"><span data-stu-id="aa40e-154">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="aa40e-155">**專案設定** 的 [**音訊**] 區段現在會如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa40e-155">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![顯示空間定位器外掛程式的專案設定](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="aa40e-157">在您的工作站上啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="aa40e-157">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="aa40e-158">在桌上出版本的 Windows 上，預設會停用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="aa40e-158">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="aa40e-159">以滑鼠右鍵按一下工作列中的音量圖示來啟用它。</span><span class="sxs-lookup"><span data-stu-id="aa40e-159">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="aa40e-160">若要取得您在 HoloLens 2 上聽到的最佳表示，請選擇 [ **空間音效-> 耳機用 Windows Sonic**]。</span><span class="sxs-lookup"><span data-stu-id="aa40e-160">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![桌面空間音訊設定](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="aa40e-162">只有當您打算在 Unity 編輯器中測試專案時，才需要此設定。</span><span class="sxs-lookup"><span data-stu-id="aa40e-162">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="aa40e-163">後續步驟</span><span class="sxs-lookup"><span data-stu-id="aa40e-163">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aa40e-164">Unity 空間音訊章節2</span><span class="sxs-lookup"><span data-stu-id="aa40e-164">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)

