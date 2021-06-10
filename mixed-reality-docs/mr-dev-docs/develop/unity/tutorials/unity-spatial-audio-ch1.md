---
title: 空間音訊教學課程-1。 在專案中新增空間音訊
description: 將 Microsoft 空間定位器外掛程式新增至您的 Unity 專案，以存取 HoloLens 2 HRTF 硬體卸載。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器
ms.openlocfilehash: 112531a3248461a5b380ad4b93de34545a2f2c3f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403359"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="4b851-105">1. 將空間音訊新增至 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="4b851-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="4b851-106">概觀</span><span class="sxs-lookup"><span data-stu-id="4b851-106">Overview</span></span>

<span data-ttu-id="4b851-107">歡迎使用 HoloLens2 上適用于 Unity 的空間音訊教學課程。</span><span class="sxs-lookup"><span data-stu-id="4b851-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="4b851-108">透過本教學課程系列，您將瞭解如何在 HoloLens 2 上使用 head 相關的傳送功能 (HRTF) 卸載，以及如何在使用 HRTF 卸載時啟用回音。</span><span class="sxs-lookup"><span data-stu-id="4b851-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="4b851-109">[Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)已完成此教學課程順序的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="4b851-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="4b851-110">若要瞭解使用以 HRTF 為基礎的 spatialization 技術來 spatialize 音效的意義，以及它可能有説明的建議，請參閱 [空間音效設計](/windows/mixed-reality/spatial-sound-design)。</span><span class="sxs-lookup"><span data-stu-id="4b851-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="4b851-111">什麼是 HRTF 卸載？</span><span class="sxs-lookup"><span data-stu-id="4b851-111">What is HRTF offload?</span></span>

<span data-ttu-id="4b851-112">使用以 HRTF 為基礎的演算法處理音訊需要大量的特製化計算。</span><span class="sxs-lookup"><span data-stu-id="4b851-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="4b851-113">HoloLens 2 包含專用硬體，可用來避免應用程式處理器額外負荷，進而「卸載」以 HRTF 為基礎的演算法處理。</span><span class="sxs-lookup"><span data-stu-id="4b851-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="4b851-114">Microsoft 空間定位器外掛程式提供簡單的方法，讓您的應用程式利用專用的 HRTF 硬體，讓您的應用程式可以使用更多應用程式處理器來執行空間音訊以外的作業。</span><span class="sxs-lookup"><span data-stu-id="4b851-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="4b851-115">目標</span><span class="sxs-lookup"><span data-stu-id="4b851-115">Objectives</span></span>

* <span data-ttu-id="4b851-116">匯入和啟用 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="4b851-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="4b851-117">在開發人員工作站上啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="4b851-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b851-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="4b851-118">Prerequisites</span></span>

* <span data-ttu-id="4b851-119">已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="4b851-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="4b851-120">基本 C# 程式設計知識</span><span class="sxs-lookup"><span data-stu-id="4b851-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="4b851-121">已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="4b851-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="4b851-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中樞</a> 已掛接 UNITY 2020/2019 LTS，並已新增通用 Windows 平臺組建支援模組</span><span class="sxs-lookup"><span data-stu-id="4b851-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="4b851-123">我們 **強烈建議您** 先完成 [快速](mr-learning-base-01.md) 入門教學課程系列，或先利用 Unity 和 MRTK 的一些基本經驗，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="4b851-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!Important]
> <span data-ttu-id="4b851-124">本教學課程系列支援 Unity 2020 LTS (目前的 2020.3) 如果您使用 Open XR 或 Windows XR 外掛程式，以及 Unity 2019 LTS (目前的 2019.4. x) 如果您使用舊版的 WSA 或 Windows XR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="4b851-124">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="4b851-125">這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求。</span><span class="sxs-lookup"><span data-stu-id="4b851-125">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="4b851-126">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="4b851-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="4b851-127">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="4b851-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="4b851-128">為此，請先遵循[初始化您的專案和第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4b851-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="4b851-129">[建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」</span><span class="sxs-lookup"><span data-stu-id="4b851-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="4b851-130">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="4b851-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="4b851-131">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="4b851-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="4b851-132">匯入混合現實工具組和設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="4b851-132">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)

1. <span data-ttu-id="4b851-133">[建立和設定場景](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) ，並為場景提供適當的名稱，例如 *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="4b851-133">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="4b851-134">然後，遵循 [變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 的指示，以確定您場景的 MRTK 設定檔是 **DefaultHoloLens2ConfigurationProfile** ，並將空間感知網格的顯示選項變更為 **遮蔽**。</span><span class="sxs-lookup"><span data-stu-id="4b851-134">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="4b851-135">將 Microsoft 空間定位器新增至專案</span><span class="sxs-lookup"><span data-stu-id="4b851-135">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="4b851-136">下載並匯入 Microsoft 空間定位器  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">SpatialAudio. 空間定位器. 1.0.18. unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="4b851-136">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="4b851-137">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](mr-learning-base-02.md#importing-the-tutorial-assets) 的指示。</span><span class="sxs-lookup"><span data-stu-id="4b851-137">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="4b851-138">啟用 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="4b851-138">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="4b851-139">將 Microsoft 空間定位器匯入您的 unity 專案之後，[ **MRTK 專案** 設定程式] 視窗隨即出現，請使用 [ **音訊空間定位器** ] 下拉式清單選取 **Microsoft 空間定位器**，然後按一下 [套用] 按鈕以套用設定：</span><span class="sxs-lookup"><span data-stu-id="4b851-139">Once you import the Microsoft Spatializer into your unity project, **MRTK Project Configurator** window will appear, use the **Audio spatializer** dropdown to select the **Microsoft Spatializer**, then click the Apply button to apply the setting:</span></span>

![MRTK 專案配置器](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

<span data-ttu-id="4b851-141">您也可以手動啟用 Microsoft 空間定位器：開啟 **編輯 > 專案設定-> 音訊**，然後將 **空間定位器外掛程式** 變更為 "Microsoft 空間定位器"。</span><span class="sxs-lookup"><span data-stu-id="4b851-141">you can also manually enable the Microsoft Spatializer: Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![顯示空間定位器外掛程式的專案設定](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="4b851-143">在您的工作站上啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="4b851-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="4b851-144">在桌上出版本的 Windows 上，預設會停用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="4b851-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="4b851-145">以滑鼠右鍵按一下工作列中的音量圖示來啟用它。</span><span class="sxs-lookup"><span data-stu-id="4b851-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="4b851-146">若要取得您在 HoloLens 2 上聽到的最佳表示，請選擇 [ **空間音效-> 耳機用 Windows Sonic**]。</span><span class="sxs-lookup"><span data-stu-id="4b851-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![桌面空間音訊設定](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="4b851-148">只有當您打算在 Unity 編輯器中測試專案時，才需要此設定。</span><span class="sxs-lookup"><span data-stu-id="4b851-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4b851-149">恭喜！</span><span class="sxs-lookup"><span data-stu-id="4b851-149">Congratulations</span></span>

<span data-ttu-id="4b851-150">在本教學課程中，您已學會如何匯入和啟用 Microsoft 空間定位器外掛程式，也可以在您的工作站上啟用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="4b851-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="4b851-151">在下一個教學課程中，您將瞭解如何在 unity 專案中新增空間音訊。</span><span class="sxs-lookup"><span data-stu-id="4b851-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b851-152">下一個教學課程： 2. Spatializing 按鈕互動音效</span><span class="sxs-lookup"><span data-stu-id="4b851-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
