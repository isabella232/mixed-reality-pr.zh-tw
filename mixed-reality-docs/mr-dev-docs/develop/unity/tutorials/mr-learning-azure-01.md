---
title: 適用於 HoloLens 2 的 Azure 雲端服務
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中執行各種 Azure 服務。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: azure, 混合實境, unity, 教學課程, hololens, hololens 2, azure blob 儲存體, azure 表格儲存體，azure spatial anchors, azure bot framework, azure 雲端服務, azure 自訂視覺, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: fbb48cfd3c2c9d5c48099f3dfe8ddca8c6136c87
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550388"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="25c4c-104">1.適用於 HoloLens 2 的 Azure 雲端服務</span><span class="sxs-lookup"><span data-stu-id="25c4c-104">1. Azure Cloud Services for HoloLens 2</span></span>

<span data-ttu-id="25c4c-105">歡迎參與這系列的教學課程，本系列課程內容著重於將 **Azure 雲端** 服務帶入 **HoloLens 2** 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="25c4c-105">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="25c4c-106">在此五部分的教學課程系列中，您將了解如何將數個 **Azure 雲端** 服務整合至 **HoloLens 2** 的 **Unity** 專案中。</span><span class="sxs-lookup"><span data-stu-id="25c4c-106">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="25c4c-107">在每個連續章節中，您將新增新的 **Azure 雲端** 服務以擴充應用程式功能和使用者體驗，同時了解每個 **Azure 雲端** 服務的基本概念。</span><span class="sxs-lookup"><span data-stu-id="25c4c-107">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="25c4c-108">本教學課程系列著重於 **HoloLens 2**，但由於 Unity 的跨平台性質，您的學習內容也適用於桌面和智慧型手機應用程式。</span><span class="sxs-lookup"><span data-stu-id="25c4c-108">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="25c4c-109">這是第一個教學課程，將為您介紹此系列的目標，以及您將使用的每個 Azure 雲端服務，和設定初始 Unity 專案的方式。</span><span class="sxs-lookup"><span data-stu-id="25c4c-109">In this first tutorial, you'll be introduced to the goals of the series and each Azure Cloud service you'll be using, as well as setting up the initial Unity project.</span></span>

<span data-ttu-id="25c4c-110">在第二個教學課程[整合 Azure 儲存體](mr-learning-azure-02.md)中，首先您將了解如何整合 Azure 儲存體，作為示範應用程式的持續性解決方案。</span><span class="sxs-lookup"><span data-stu-id="25c4c-110">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you'll start off by integrating Azure Storage as the persistence solution for the demo application.</span></span> <span data-ttu-id="25c4c-111">您也將了解 Blob 儲存體與資料表儲存體之間的差異，以及如何準備所需的專案資源和設定場景。</span><span class="sxs-lookup"><span data-stu-id="25c4c-111">You'll also learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene.</span></span> <span data-ttu-id="25c4c-112">最後，您將了解如何驗證讀取、更新和刪除資料作業。</span><span class="sxs-lookup"><span data-stu-id="25c4c-112">Finally, you'll learn how to verify the read, update, and delete data operations.</span></span>

<span data-ttu-id="25c4c-113">繼續進行第三個教學課程，[整合 Azure 自訂視覺](mr-learning-azure-03.md)，您將使用 Azure 自訂視覺來定型和偵測 HoloLens 2 應用程式中的影像。</span><span class="sxs-lookup"><span data-stu-id="25c4c-113">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="25c4c-114">本章一開始會先設定您自己的 Azure 自訂視覺資源、準備場景元件，並從應用程式內部定型和偵測您自己的影像開始。</span><span class="sxs-lookup"><span data-stu-id="25c4c-114">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="25c4c-115">接下來，您會前進到第四個教學課程[整合 Azure Spatial Anchors](mr-learning-azure-04.md)，並探索 Azure Spatial Anchors 服務來儲存和尋找位置、了解核心概念、準備必要資源、設定場景，以及開始使用應用程式中的新功能。</span><span class="sxs-lookup"><span data-stu-id="25c4c-115">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="25c4c-116">在第五個教學課程[將 Azure Bot 服務與 LUIS 整合](mr-learning-azure-05.md)中，您可以為應用程式提供新的使用者互動方法，也就是自然語言！</span><span class="sxs-lookup"><span data-stu-id="25c4c-116">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="25c4c-117">這項功能會透過搭配 Language Understanding (LUIS) 使用 Azure Bot Framework 來實現。</span><span class="sxs-lookup"><span data-stu-id="25c4c-117">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="25c4c-118">最後一章會教您 Azure Bot 服務的基本概念，並加速您使用 Bot Framework 編輯器作為零程式碼解決方案的程序。</span><span class="sxs-lookup"><span data-stu-id="25c4c-118">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="25c4c-119">建立 Bot 之後，您會將其整合到場景中，並執行 HoloLens 2 應用程式的最後階段。</span><span class="sxs-lookup"><span data-stu-id="25c4c-119">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="25c4c-120">應用程式目標</span><span class="sxs-lookup"><span data-stu-id="25c4c-120">Application goals</span></span>

<span data-ttu-id="25c4c-121">在此教學課程系列中，您將建置一個 **HoloLens 2** 應用程式，以偵測影像中的物件並尋找其空間位置。</span><span class="sxs-lookup"><span data-stu-id="25c4c-121">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="25c4c-122">若要設定網域語言，您可以從現有的 **追蹤物件** 呼叫這類實體。</span><span class="sxs-lookup"><span data-stu-id="25c4c-122">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="25c4c-123">使用者可以建立 **追蹤物件**，透過電腦視覺和 (或) 空間位置將其中一組或二組影像加以關聯。</span><span class="sxs-lookup"><span data-stu-id="25c4c-123">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="25c4c-124">所有資料都必須保存到雲端。</span><span class="sxs-lookup"><span data-stu-id="25c4c-124">All data must be persisted into the cloud.</span></span> <span data-ttu-id="25c4c-125">此外，應用程式的某些層面會選擇性地透過 Bot 以自然語言來控制。</span><span class="sxs-lookup"><span data-stu-id="25c4c-125">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="25c4c-126">功能</span><span class="sxs-lookup"><span data-stu-id="25c4c-126">Features</span></span>

* <span data-ttu-id="25c4c-127">資料和影像的基本管理</span><span class="sxs-lookup"><span data-stu-id="25c4c-127">Basic managing of data and images</span></span>
* <span data-ttu-id="25c4c-128">影像訓練和偵測</span><span class="sxs-lookup"><span data-stu-id="25c4c-128">Image training and detection</span></span>
* <span data-ttu-id="25c4c-129">儲存空間位置和操作方式指南</span><span class="sxs-lookup"><span data-stu-id="25c4c-129">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="25c4c-130">透過自然語言使用部分功能的 Bot 輔助程式</span><span class="sxs-lookup"><span data-stu-id="25c4c-130">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="25c4c-131">Azure 雲端服務</span><span class="sxs-lookup"><span data-stu-id="25c4c-131">Azure Cloud services</span></span>

<span data-ttu-id="25c4c-132">您將使用下列 **Azure 雲端** 服務來實作上述功能：</span><span class="sxs-lookup"><span data-stu-id="25c4c-132">You'll use the following **Azure Cloud** services to implement the above features:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="25c4c-133">Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="25c4c-133">Azure Storage</span></span>

<span data-ttu-id="25c4c-134">您會使用 [Azure 儲存體](https://azure.microsoft.com/services/storage/)作為持續性解決方案。</span><span class="sxs-lookup"><span data-stu-id="25c4c-134">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="25c4c-135">如可讓您將資料儲存在表格中，並上傳例如影像等的大型二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="25c4c-135">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="25c4c-136">Azure 自訂視覺</span><span class="sxs-lookup"><span data-stu-id="25c4c-136">Azure Custom Vision</span></span>

<span data-ttu-id="25c4c-137">有了 [Azure 自訂視覺](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) ([Azure 認知服務](https://azure.microsoft.com/services/cognitive-services/)的一部分)，您可以建立一組影像與「追蹤物件」的關聯、將機器學習模型定型，並偵測「追蹤物件」。</span><span class="sxs-lookup"><span data-stu-id="25c4c-137">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="25c4c-138">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="25c4c-138">Azure Spatial Anchors</span></span>

<span data-ttu-id="25c4c-139">若要儲存「追蹤物件」位置，並提供引導式指示以方便尋找，您可以使用 [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/)。</span><span class="sxs-lookup"><span data-stu-id="25c4c-139">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="25c4c-140">Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="25c4c-140">Azure Bot Service</span></span>

<span data-ttu-id="25c4c-141">應用程式主要是由傳統的 UI 驅動，因此您可以使用 [Azure Bot 服務](https://azure.microsoft.com/services/bot-service/)新增一些特性，並作為新的互動方法。</span><span class="sxs-lookup"><span data-stu-id="25c4c-141">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="25c4c-142">必要條件</span><span class="sxs-lookup"><span data-stu-id="25c4c-142">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="25c4c-143">如果您尚未完成[入門教學課程](mr-learning-base-01.md)系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="25c4c-143">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="25c4c-144">已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="25c4c-144">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="25c4c-145">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="25c4c-145">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="25c4c-146">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="25c4c-146">Some basic C# programming ability</span></span>
* <span data-ttu-id="25c4c-147">已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="25c4c-147">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="25c4c-148">連線的網路攝影機 (如果想要從 Unity 編輯器進行測試)</span><span class="sxs-lookup"><span data-stu-id="25c4c-148">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="25c4c-149">已安裝 Unity 2019 LTS 的 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="25c4c-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="25c4c-150">本教學課程系列的建議 Unity 版本是 Unity 2019 LTS。</span><span class="sxs-lookup"><span data-stu-id="25c4c-150">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="25c4c-151">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="25c4c-151">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="25c4c-152">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="25c4c-152">Creating and preparing the Unity project</span></span>

<span data-ttu-id="25c4c-153">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="25c4c-153">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="25c4c-154">首先，請遵循[初始化您的專案和第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="25c4c-154">First, follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="25c4c-155">[建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「Azure 雲端教學課程」</span><span class="sxs-lookup"><span data-stu-id="25c4c-155">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="25c4c-156">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="25c4c-156">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="25c4c-157">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="25c4c-157">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="25c4c-158">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="25c4c-158">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="25c4c-159">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="25c4c-159">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="25c4c-160">[建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如 AzureCloudServices</span><span class="sxs-lookup"><span data-stu-id="25c4c-160">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="25c4c-161">然後，遵循 [變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 的指示，以確定您場景的 MRTK 設定檔是 **DefaultXRSDKConfigurationProfile** ，並將空間感知網格的顯示選項變更為 **遮蔽**。</span><span class="sxs-lookup"><span data-stu-id="25c4c-161">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultXRSDKConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="25c4c-162">安裝內建的 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="25c4c-162">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="25c4c-163">在 Unity 功能表中，選取 視窗 >  **套件管理員** 以開啟 套件管理員 視窗，然後選取 AR 基本概念，並按一下 安裝 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="25c4c-163">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![已選取 AR Foundation 的 Unity 套件管理員視窗](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="25c4c-165">您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。</span><span class="sxs-lookup"><span data-stu-id="25c4c-165">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="25c4c-166">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="25c4c-166">Importing the tutorial assets</span></span>

<span data-ttu-id="25c4c-167">將 >azurespatialanchors.unitypackage SDK V 2.7.1 新增至 unity 專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="25c4c-167">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="25c4c-168">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="25c4c-168">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="25c4c-169">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="25c4c-169">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="25c4c-170">MRTK.Tutorials.AzureCloudServices.unitypackage</span><span class="sxs-lookup"><span data-stu-id="25c4c-170">MRTK.Tutorials.AzureCloudServices.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="25c4c-171">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](mr-learning-base-04.md#importing-the-tutorial-assets) 的指示。</span><span class="sxs-lookup"><span data-stu-id="25c4c-171">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

<span data-ttu-id="25c4c-172">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="25c4c-172">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](images/mr-learning-azure/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="25c4c-174">如果您看到任何有關於 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' 和 'WorldAnchor.GetNativeSpatialAnchorPtr()' 已過時的 CS0618 警告，則可以忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="25c4c-174">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' and 'WorldAnchor.GetNativeSpatialAnchorPtr()' being obsolete, you can ignore these warnings.</span></span>

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="25c4c-175">建立和準備場景</span><span class="sxs-lookup"><span data-stu-id="25c4c-175">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="25c4c-176">在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。</span><span class="sxs-lookup"><span data-stu-id="25c4c-176">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="25c4c-177">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureCloudServices] > [預製物件] > [管理員] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="25c4c-177">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="25c4c-178">按住 CTRL 鍵時，按一下 [SceneController]、**RootMenu** 和 **DataManager** 以選取三個預製物件：</span><span class="sxs-lookup"><span data-stu-id="25c4c-178">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![已選取 SceneController、RootMenu 和 DataManager prefabs 的 Unity](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="25c4c-180">**SceneController (預製物件)** 包含兩個指令碼，也就是 **SceneController (指令碼)** 和 **UnityDispatcher (指令碼)** 。</span><span class="sxs-lookup"><span data-stu-id="25c4c-180">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="25c4c-181">**SceneController** 指令碼元件包含數個 UX 函式，並可協助相片擷取功能，而 **UnityDispatcher** 是允許 Unity 主執行緒執行動作的協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="25c4c-181">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="25c4c-182">**RootMenu (預製物件)** 是主要的 UI 預製物件，其中包含透過各種小型指令碼元件彼此連繫的所有 UI 視窗，並會控制應用程式的一般 UX 流程。</span><span class="sxs-lookup"><span data-stu-id="25c4c-182">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="25c4c-183">**DataManager (預製物件)** 負責與 Azure 儲存體溝通，我們會在下一個教學課程中進一步說明。</span><span class="sxs-lookup"><span data-stu-id="25c4c-183">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="25c4c-184">選取三個預製物件之後，將其拖曳到階層視窗中，即可新增至場景：</span><span class="sxs-lookup"><span data-stu-id="25c4c-184">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![仍選取新增 SceneController、RootMenu 和 DataManager prefabs 的 Unity](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="25c4c-186">若要將焦點放在場景中的物件上，您可以按兩下 **RootMenu** 物件，然後再次將場景稍微縮小：</span><span class="sxs-lookup"><span data-stu-id="25c4c-186">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![已選取 RootMenu 物件的 Unity](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="25c4c-188">如果您發現場景中的大圖示 (例如大型邊框的 'T' 圖示) 會造成干擾，您可以藉由將 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmo 切換</a>到關閉位置來將其隱藏。</span><span class="sxs-lookup"><span data-stu-id="25c4c-188">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="25c4c-189">設定場景</span><span class="sxs-lookup"><span data-stu-id="25c4c-189">Configuring the scene</span></span>

<span data-ttu-id="25c4c-190">在本節中，您會將 SceneManager、DataManager 和 RootMenu 連接在一起，讓適用於下列[整合 Azure 儲存體](mr-learning-azure-01.md)教學課程的工作場景準備就緒。</span><span class="sxs-lookup"><span data-stu-id="25c4c-190">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="25c4c-191">連接物件</span><span class="sxs-lookup"><span data-stu-id="25c4c-191">Connect the objects</span></span>

<span data-ttu-id="25c4c-192">在階層視窗中，選取 [DataManager] 物件：</span><span class="sxs-lookup"><span data-stu-id="25c4c-192">In the Hierarchy window, select the **DataManager** object:</span></span>

![已選取 DataManager 物件的 Unity](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="25c4c-194">在偵測器視窗中，找出 **DataManager (指令碼)** 元件，接著您會在 **On Data Manager Ready ()** 事件的上看到空位。</span><span class="sxs-lookup"><span data-stu-id="25c4c-194">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="25c4c-195">現在，從階層視窗將 **SceneController** 物件拖曳到 **On Data Manager Ready ()** 事件中。</span><span class="sxs-lookup"><span data-stu-id="25c4c-195">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![已新增 DataManager 事件接聽程式的 Unity](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="25c4c-197">您會注意到事件的下拉式功能表已變成作用中，請按一下下拉式功能表並瀏覽至 **SceneController**，然後在子功能表中選取 **Init ()** 選項：</span><span class="sxs-lookup"><span data-stu-id="25c4c-197">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![已新增 DataManager 事件動作的 Unity](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="25c4c-199">從階層視窗中，選取 **SceneController** 物件，您會在該處的偵測器中找到 **SceneController** (指令碼) 元件。</span><span class="sxs-lookup"><span data-stu-id="25c4c-199">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![已選取 SceneController 的 Unity](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="25c4c-201">您會看到有數個未填入的欄位等待您填入資訊。</span><span class="sxs-lookup"><span data-stu-id="25c4c-201">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="25c4c-202">將階層中的 **DataManager** 物件移至「資料管理員」欄位，並將階層中的 **RootMenu** GameObject 移至「主功能表」欄位。</span><span class="sxs-lookup"><span data-stu-id="25c4c-202">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![已設定 SceneController 的 Unity](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="25c4c-204">現在您的場景已準備就緒，可供未來的教學課程使用。</span><span class="sxs-lookup"><span data-stu-id="25c4c-204">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="25c4c-205">別忘了儲存到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="25c4c-205">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="25c4c-206">準備專案建置管線</span><span class="sxs-lookup"><span data-stu-id="25c4c-206">Prepare project build pipeline</span></span>

<span data-ttu-id="25c4c-207">雖然專案還必須填入內容，但您必須執行一些準備工作，讓專案準備好建置 **HoloLens 2**。</span><span class="sxs-lookup"><span data-stu-id="25c4c-207">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="25c4c-208">1.新增額外的必要功能</span><span class="sxs-lookup"><span data-stu-id="25c4c-208">1. Add additional required capabilities</span></span>

<span data-ttu-id="25c4c-209">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="25c4c-209">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity 開啟專案設定](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="25c4c-211">在專案設定視窗中選取 [玩家]，然後選取 [發佈設定]：</span><span class="sxs-lookup"><span data-stu-id="25c4c-211">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![Unity 發行設定](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="25c4c-213">在 [發佈設定] 中，向下捲動至 [功能] 區段，然後再次確認您在教學課程開頭建立專案時所啟用的 **InternetClient**、**Microphone** 和 **SpatialPerception** 功能是否皆已啟用。</span><span class="sxs-lookup"><span data-stu-id="25c4c-213">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="25c4c-214">然後，啟用 **InternetClientServer**、**PrivateNetworkClientServer** 和 **Webcam** 功能：</span><span class="sxs-lookup"><span data-stu-id="25c4c-214">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![Unity 功能](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="25c4c-216">2.將應用程式部署至 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="25c4c-216">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="25c4c-217">您將在此教學課程系列中使用的所有功能並非都可以在 Unity 編輯器中執行，這表示您必須熟悉如何將應用程式部署至 HoloLens 2 裝置。</span><span class="sxs-lookup"><span data-stu-id="25c4c-217">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="25c4c-218">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提示，您可以參閱[入門教學課程 - 對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。</span><span class="sxs-lookup"><span data-stu-id="25c4c-218">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="25c4c-219">3.在 HoloLens 2 上執行應用程式，並遵循應用程式內的指示</span><span class="sxs-lookup"><span data-stu-id="25c4c-219">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="25c4c-220">所有 Azure 服務都會使用網際網路，因此請確定您的裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="25c4c-220">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="25c4c-221">當應用程式在您的裝置上執行時，請接受下列所要求功能的存取權：</span><span class="sxs-lookup"><span data-stu-id="25c4c-221">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="25c4c-222">麥克風</span><span class="sxs-lookup"><span data-stu-id="25c4c-222">Microphone</span></span>
* <span data-ttu-id="25c4c-223">相機</span><span class="sxs-lookup"><span data-stu-id="25c4c-223">Camera</span></span>

<span data-ttu-id="25c4c-224">這類服務需要像是「聊天機器人」和「自訂視覺」才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="25c4c-224">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="25c4c-225">恭喜！</span><span class="sxs-lookup"><span data-stu-id="25c4c-225">Congratulations</span></span>

<span data-ttu-id="25c4c-226">在本教學課程中，我們介紹了教學課程系列，您也了解各項即將實作的功能，以及如何繫結 **Azure 雲端**，進而實現您的 *HoloLens 2* 應用程式。</span><span class="sxs-lookup"><span data-stu-id="25c4c-226">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="25c4c-227">您已將必要的元件新增至專案，並備妥此教學課程系列的場景。</span><span class="sxs-lookup"><span data-stu-id="25c4c-227">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="25c4c-228">在下一課中，您將使用 Azure 儲存體作為雲端式持續性解決方案，以儲存資料和影像。</span><span class="sxs-lookup"><span data-stu-id="25c4c-228">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="25c4c-229">下一個教學課程：2.整合 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="25c4c-229">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)