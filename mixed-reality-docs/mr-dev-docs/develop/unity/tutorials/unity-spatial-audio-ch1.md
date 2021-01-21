---
title: 空間音訊教學課程-1。 在專案中新增空間音訊
description: 將 Microsoft 空間定位器外掛程式新增至您的 Unity 專案，以存取 HoloLens 2 HRTF 硬體卸載。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器
ms.openlocfilehash: cc7a4db5a3b4d853f2912a5e8e022fddd372e105
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635386"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="bc67c-105">1. 將空間音訊新增至 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="bc67c-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="bc67c-106">概觀</span><span class="sxs-lookup"><span data-stu-id="bc67c-106">Overview</span></span>

<span data-ttu-id="bc67c-107">歡迎使用 HoloLens2 上適用于 Unity 的空間音訊教學課程。</span><span class="sxs-lookup"><span data-stu-id="bc67c-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="bc67c-108">透過本教學課程系列，您將瞭解如何在 HoloLens 2 上使用 head 相關的傳送功能 (HRTF) 卸載，以及如何在使用 HRTF 卸載時啟用回音。</span><span class="sxs-lookup"><span data-stu-id="bc67c-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="bc67c-109">[Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)已完成此教學課程順序的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="bc67c-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="bc67c-110">若要瞭解使用以 HRTF 為基礎的 spatialization 技術來 spatialize 音效的意義，以及它可能有説明的建議，請參閱 [空間音效設計](/windows/mixed-reality/spatial-sound-design)。</span><span class="sxs-lookup"><span data-stu-id="bc67c-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="bc67c-111">什麼是 HRTF 卸載？</span><span class="sxs-lookup"><span data-stu-id="bc67c-111">What is HRTF offload?</span></span>

<span data-ttu-id="bc67c-112">使用以 HRTF 為基礎的演算法處理音訊需要大量的特製化計算。</span><span class="sxs-lookup"><span data-stu-id="bc67c-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="bc67c-113">HoloLens 2 包含專用硬體，可用來避免應用程式處理器額外負荷，進而「卸載」以 HRTF 為基礎的演算法處理。</span><span class="sxs-lookup"><span data-stu-id="bc67c-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="bc67c-114">Microsoft 空間定位器外掛程式提供簡單的方法，讓您的應用程式利用專用的 HRTF 硬體，讓您的應用程式可以使用更多應用程式處理器來執行空間音訊以外的作業。</span><span class="sxs-lookup"><span data-stu-id="bc67c-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="bc67c-115">目標</span><span class="sxs-lookup"><span data-stu-id="bc67c-115">Objectives</span></span>

* <span data-ttu-id="bc67c-116">匯入和啟用 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="bc67c-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="bc67c-117">在開發人員工作站上啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="bc67c-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bc67c-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="bc67c-118">Prerequisites</span></span>

* <span data-ttu-id="bc67c-119">已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="bc67c-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="bc67c-120">基本 C# 程式設計知識</span><span class="sxs-lookup"><span data-stu-id="bc67c-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="bc67c-121">已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="bc67c-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="bc67c-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已掛接 Unity 2019 LTS，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="bc67c-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="bc67c-123">我們 **強烈建議您** 先完成 [快速](mr-learning-base-01.md) 入門教學課程系列，或先利用 Unity 和 MRTK 的一些基本經驗，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="bc67c-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="bc67c-124">本教學課程系列的建議 Unity 版本是 Unity 2019 LTS。</span><span class="sxs-lookup"><span data-stu-id="bc67c-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="bc67c-125">這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="bc67c-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="bc67c-126">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="bc67c-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="bc67c-127">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="bc67c-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="bc67c-128">為此，請先遵循[初始化您的專案和第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bc67c-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="bc67c-129">[建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」</span><span class="sxs-lookup"><span data-stu-id="bc67c-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="bc67c-130">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="bc67c-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="bc67c-131">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="bc67c-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="bc67c-132">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="bc67c-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="bc67c-133">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="bc67c-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="bc67c-134">[建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene) ，並為場景提供適當的名稱，例如 *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="bc67c-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="bc67c-135">然後，遵循 [變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 的指示，以確定您場景的 MRTK 設定檔是 **DefaultHoloLens2ConfigurationProfile** ，並將空間感知網格的顯示選項變更為 **遮蔽**。</span><span class="sxs-lookup"><span data-stu-id="bc67c-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="bc67c-136">將 Microsoft 空間定位器新增至專案</span><span class="sxs-lookup"><span data-stu-id="bc67c-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="bc67c-137">下載並匯入 Microsoft 空間定位器  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">SpatialAudio. 空間定位器. 1.0.18. unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="bc67c-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="bc67c-138">如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 的指示。</span><span class="sxs-lookup"><span data-stu-id="bc67c-138">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="bc67c-139">啟用 Microsoft 空間定位器外掛程式</span><span class="sxs-lookup"><span data-stu-id="bc67c-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="bc67c-140">匯入 **Microsoft 空間定位器** 之後，您必須加以啟用。</span><span class="sxs-lookup"><span data-stu-id="bc67c-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="bc67c-141">開啟 [ **編輯-> 專案設定-> 音訊**]，然後將 **空間定位器外掛程式** 變更為 "Microsoft 空間定位器"。</span><span class="sxs-lookup"><span data-stu-id="bc67c-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![顯示空間定位器外掛程式的專案設定](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="bc67c-143">在您的工作站上啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="bc67c-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="bc67c-144">在桌上出版本的 Windows 上，預設會停用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="bc67c-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="bc67c-145">以滑鼠右鍵按一下工作列中的音量圖示來啟用它。</span><span class="sxs-lookup"><span data-stu-id="bc67c-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="bc67c-146">若要取得您在 HoloLens 2 上聽到的最佳表示，請選擇 [ **空間音效-> 耳機用 Windows Sonic**]。</span><span class="sxs-lookup"><span data-stu-id="bc67c-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![桌面空間音訊設定](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="bc67c-148">只有當您打算在 Unity 編輯器中測試專案時，才需要此設定。</span><span class="sxs-lookup"><span data-stu-id="bc67c-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="bc67c-149">恭喜！</span><span class="sxs-lookup"><span data-stu-id="bc67c-149">Congratulations</span></span>

<span data-ttu-id="bc67c-150">在本教學課程中，您已學會如何匯入和啟用 Microsoft 空間定位器外掛程式，也可以在您的工作站上啟用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="bc67c-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="bc67c-151">在下一個教學課程中，您將瞭解如何在 unity 專案中新增空間音訊。</span><span class="sxs-lookup"><span data-stu-id="bc67c-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bc67c-152">下一個教學課程： 2. Spatializing 按鈕互動音效</span><span class="sxs-lookup"><span data-stu-id="bc67c-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
