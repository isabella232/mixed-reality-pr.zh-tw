---
title: 開始使用 Azure Spatial Anchors
description: 完成此課程，以了解如何使用 Azure Spatial Anchors 來錨定混合實境應用程式中的物件。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, Azure 空間錨點
ms.localizationpriority: high
ms.openlocfilehash: 5f16d3c12e6dbb977ecedc1598a28073cfb39222
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105983141"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="cfe25-104">2.開始使用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="cfe25-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="cfe25-105">在此教學課程中，您將探索啟動和停止 Azure Spatial Anchors 工作階段，以及在單一裝置上建立、上傳和下載 Azure Spatial Anchors 所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="cfe25-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="cfe25-106">目標</span><span class="sxs-lookup"><span data-stu-id="cfe25-106">Objectives</span></span>

* <span data-ttu-id="cfe25-107">了解 HoloLens 2 的 Azure Spatial Anchors 開發基本概念</span><span class="sxs-lookup"><span data-stu-id="cfe25-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="cfe25-108">了解如何建立空間錨點，並從 Azure 提取這些錨點</span><span class="sxs-lookup"><span data-stu-id="cfe25-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="cfe25-109">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="cfe25-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="cfe25-110">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="cfe25-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="cfe25-111">首先，請遵循[初始化您的專案和部署第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cfe25-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="cfe25-112">[建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」</span><span class="sxs-lookup"><span data-stu-id="cfe25-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="cfe25-113">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="cfe25-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="cfe25-114">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="cfe25-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="cfe25-115">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="cfe25-115">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="cfe25-116">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="cfe25-116">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="cfe25-117">[建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如 AzureSpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="cfe25-117">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="cfe25-118">然後遵循[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)的指示，以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cfe25-118">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="cfe25-119">將 **MRTK 設定檔** 變更為 **DefaultHoloLens2ConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="cfe25-119">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="cfe25-120">將 **空間感知網格顯示選項** 變更為 **遮蔽**。</span><span class="sxs-lookup"><span data-stu-id="cfe25-120">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="cfe25-121">安裝內建的 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="cfe25-121">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="cfe25-122">在 Unity 功能表中，選取 視窗 >  **套件管理員** 以開啟 套件管理員 視窗，然後選取 AR 基本概念，並按一下 安裝 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="cfe25-122">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="cfe25-124">您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。</span><span class="sxs-lookup"><span data-stu-id="cfe25-124">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="cfe25-125">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="cfe25-125">Importing the tutorial assets</span></span>

<span data-ttu-id="cfe25-126">將 >azurespatialanchors.unitypackage SDK V 2.7.1 新增至 unity 專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="cfe25-126">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="cfe25-127">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="cfe25-127">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="cfe25-128">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cfe25-128">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="cfe25-129">MRTK.HoloLens2. >azurespatialanchors.unitypackage. 2.5.3. unitypackage</span><span class="sxs-lookup"><span data-stu-id="cfe25-129">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.5.3.unitypackage)

<span data-ttu-id="cfe25-130">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="cfe25-130">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="cfe25-132">如果您看到任何有關於 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' 已過時的 CS0618 警告，您可以忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="cfe25-132">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="cfe25-133">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](mr-learning-base-02.md#importing-the-tutorial-assets) 的指示。</span><span class="sxs-lookup"><span data-stu-id="cfe25-133">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="cfe25-134">準備場景</span><span class="sxs-lookup"><span data-stu-id="cfe25-134">Preparing the scene</span></span>

<span data-ttu-id="cfe25-135">在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。</span><span class="sxs-lookup"><span data-stu-id="cfe25-135">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="cfe25-136">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureSpatialAnchors] > [Prefabs] 資料夾，然後按一下下列 Prefab 並將其拖曳至 [階層] 視窗中，將其新增到您的場景中：</span><span class="sxs-lookup"><span data-stu-id="cfe25-136">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="cfe25-137">**ButtonParent** Prefab</span><span class="sxs-lookup"><span data-stu-id="cfe25-137">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="cfe25-138">**DebugWindow** Prefab</span><span class="sxs-lookup"><span data-stu-id="cfe25-138">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="cfe25-139">**Instructions** Prefab</span><span class="sxs-lookup"><span data-stu-id="cfe25-139">**Instructions** prefabs</span></span>
* <span data-ttu-id="cfe25-140">**ParentAnchor** Prefab</span><span class="sxs-lookup"><span data-stu-id="cfe25-140">**ParentAnchor** prefabs</span></span>

![已選取新增 Prefabs 的 Unity](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="cfe25-142">如果您發現場景中的大圖示 (例如大型邊框的 'T' 圖示) 會造成干擾，您可以藉由將 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmo 切換</a>到關閉位置來將其隱藏，如上圖所示。</span><span class="sxs-lookup"><span data-stu-id="cfe25-142">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="cfe25-143">設定按鈕以操作場景</span><span class="sxs-lookup"><span data-stu-id="cfe25-143">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="cfe25-144">在本節中，您將在場景中新增指令碼來建立一系列的按鈕事件，以示範本機錨點和 Azure Spatial Anchors 在應用程式中的行為基礎。</span><span class="sxs-lookup"><span data-stu-id="cfe25-144">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="cfe25-145">在 [階層] 視窗中，展開 **ButtonParent** 物件，並選取名為 **StartAzureSession** 的第一個子物件，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cfe25-145">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="cfe25-146">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="cfe25-146">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cfe25-147">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [StartAzureSession ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="cfe25-147">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![已設定 StartAzureSession 按鈕 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="cfe25-149">在 [階層] 視窗中，選取名為 **StopAzureSession** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cfe25-149">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="cfe25-150">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="cfe25-150">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cfe25-151">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [StopAzureSession ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="cfe25-151">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![已設定 StopAzureSession 按鈕 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="cfe25-153">在 [階層] 視窗中，選取名為 **CreateAzureAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cfe25-153">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="cfe25-154">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="cfe25-154">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cfe25-155">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [CreateAzureAnchor ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="cfe25-155">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="cfe25-156">將 **ParentAnchor** 物件指派給空的 [無 (遊戲物件)] 欄位，使其成為 CreateAzureAnchor () 函式的引數</span><span class="sxs-lookup"><span data-stu-id="cfe25-156">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![已設定 CreateAzureAnchor 按鈕 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="cfe25-158">在 [階層] 視窗中，選取名為 **RemoveLocalAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cfe25-158">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="cfe25-159">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="cfe25-159">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cfe25-160">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [RemoveLocalAnchor ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="cfe25-160">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="cfe25-161">將 **ParentAnchor** 物件指派給空的 [無 (遊戲物件)] 欄位，使其成為 RemoveLocalAnchor () 函式的引數</span><span class="sxs-lookup"><span data-stu-id="cfe25-161">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![已設定 RemoveLocalAnchor 按鈕 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="cfe25-163">在 [階層] 視窗中，選取名為 **FindAzureAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cfe25-163">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="cfe25-164">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="cfe25-164">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cfe25-165">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [FindAzureAnchor ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="cfe25-165">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![已設定 FindAzureAnchor 按鈕 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="cfe25-167">在 [階層] 視窗中，選取名為 **DeleteAzureAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cfe25-167">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="cfe25-168">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="cfe25-168">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cfe25-169">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [DeleteAzureAnchor ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="cfe25-169">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![已設定 DeleteAzureAnchor 按鈕 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="cfe25-171">將場景連線至 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="cfe25-171">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="cfe25-172">在 [階層] 視窗中，選取 **ParentAnchor** 物件，然後在 [偵測器] 視窗中尋找 **Spatial Anchor Manager (指令碼)** 元件。</span><span class="sxs-lookup"><span data-stu-id="cfe25-172">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="cfe25-173">使用 Azure Spatial Anchors 帳戶中的認證來設定 [認證] 區段，該帳戶會在本教學課程系列的[必要條件](mr-learning-asa-01.md#prerequisites)中建立：</span><span class="sxs-lookup"><span data-stu-id="cfe25-173">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="cfe25-174">在 [Spatial Anchors Account 識別碼] 欄位中，貼上 Azure Spatial Anchors 帳戶中的 **帳戶識別碼**</span><span class="sxs-lookup"><span data-stu-id="cfe25-174">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="cfe25-175">在 [Spatial Anchors 帳戶金鑰] 欄位中，貼上 Azure Spatial Anchors 帳戶中的主要或次要 **存取金鑰**</span><span class="sxs-lookup"><span data-stu-id="cfe25-175">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="cfe25-176">在 [**空間錨點帳戶網域**] 欄位中，貼上您 Azure 空間錨點帳戶的 **帳戶網域**</span><span class="sxs-lookup"><span data-stu-id="cfe25-176">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![已設定 Spatial Anchor Manager 的 Unity](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="cfe25-178">嘗試 Azure Spatial Anchors 的基本行為</span><span class="sxs-lookup"><span data-stu-id="cfe25-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="cfe25-179">Azure Spatial Anchors 無法在 Unity 中執行，因此若要測試 Azure Spatial Anchors 功能，您必須在裝置中建置專案並部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="cfe25-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="cfe25-180">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。</span><span class="sxs-lookup"><span data-stu-id="cfe25-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="cfe25-181">當應用程式在您的裝置上執行時，請遵循 Azure Spatial Anchor 教學課程指示面板上顯示的螢幕指示：</span><span class="sxs-lookup"><span data-stu-id="cfe25-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="cfe25-182">將立方體移至不同的位置</span><span class="sxs-lookup"><span data-stu-id="cfe25-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="cfe25-183">啟動 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="cfe25-183">Start Azure Session</span></span>
1. <span data-ttu-id="cfe25-184">建立 Azure 錨點 (在立方體的位置上建立錨點)。</span><span class="sxs-lookup"><span data-stu-id="cfe25-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="cfe25-185">停止 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="cfe25-185">Stop Azure Session</span></span>
1. <span data-ttu-id="cfe25-186">移除區域錨點 (允許使用者移動立方體)</span><span class="sxs-lookup"><span data-stu-id="cfe25-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="cfe25-187">將立方體移至其他地方</span><span class="sxs-lookup"><span data-stu-id="cfe25-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="cfe25-188">啟動 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="cfe25-188">Start Azure Session</span></span>
1. <span data-ttu-id="cfe25-189">尋找 Azure 錨點 (將立方體置於步驟 3 的位置)</span><span class="sxs-lookup"><span data-stu-id="cfe25-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="cfe25-190">刪除 Azure 錨點</span><span class="sxs-lookup"><span data-stu-id="cfe25-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="cfe25-191">停止 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="cfe25-191">Stop Azure session</span></span>

![已選取指示物件的 Unity](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="cfe25-193">Azure Spatial Anchors 會使用網際網路來儲存和載入錨點資料，因此請確定您的裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="cfe25-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="cfe25-194">錨點體驗</span><span class="sxs-lookup"><span data-stu-id="cfe25-194">Anchoring an experience</span></span>

<span data-ttu-id="cfe25-195">在前面幾節中，您已了解 Azure Spatial Anchors 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="cfe25-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="cfe25-196">我們使用了立方體和連結的錨點來呈現及視覺化父遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="cfe25-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="cfe25-197">在本節中，您將了解如何藉由將整個體驗放在 ParentAnchor 物件的子系，來為其建立錨點。</span><span class="sxs-lookup"><span data-stu-id="cfe25-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="cfe25-198">在 [階層] 視窗中，選取 **ParentAnchor** 物件，然後在 [偵測器] 視窗中設定 **變形** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cfe25-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="cfe25-199">將 [X 軸縮放] 變更為 1.1</span><span class="sxs-lookup"><span data-stu-id="cfe25-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="cfe25-200">將 [Z 軸縮放] 變更為 1.1</span><span class="sxs-lookup"><span data-stu-id="cfe25-200">Change **Scale Z** to 1.1</span></span>

![已選取、置放及縮放 ParentAnchor 物件的 Unity](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="cfe25-202">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.GettingStarted] > [Prefabs] > [Rover] 資料夾，然後按一下 **RoverExplorer_Complete** Prefab，並將其拖曳至 [階層] 視窗中來新增到您的場景中：</span><span class="sxs-lookup"><span data-stu-id="cfe25-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![已選取新增 RoverExplorer_Complete Prefab 的 Unity](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="cfe25-204">在 [階層] 視窗中，繼續選取新增的 RoverModule_Complete 物件，並將其拖曳至 **ParentAnchor** 物件，使其成為 ParentAnchor 物件的子系：</span><span class="sxs-lookup"><span data-stu-id="cfe25-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![RoverExplorer_Complete 物件設定為 ParentAnchor 子系的 Unity](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="cfe25-206">如果您現在重建專案，並將應用程式部署到您的裝置，您現在就可以藉由移動已調整大小的立方體來重新放置整個 Rover Explorer 體驗。</span><span class="sxs-lookup"><span data-stu-id="cfe25-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="cfe25-207">各種不同的使用者體驗，可用於重新放置體驗，包括使用重新置放的物件 (例如本教學課程中使用的 cube) 、使用按鈕來切換圍繞體驗的界限控制項、使用位置和旋轉 gizmos 等等。</span><span class="sxs-lookup"><span data-stu-id="cfe25-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="cfe25-208">恭喜！</span><span class="sxs-lookup"><span data-stu-id="cfe25-208">Congratulations</span></span>

<span data-ttu-id="cfe25-209">在本教學課程中，您已了解 Azure Spatial Anchors 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="cfe25-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="cfe25-210">本教學課程提供了您幾個按鈕，讓您探索啟動和停止 Azure Spatial Anchors 工作階段所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="cfe25-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="cfe25-211">此外，也可以在單一裝置上建立、上傳和下載 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="cfe25-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="cfe25-212">在下一個教學課程中，您將了解如何將 Azure 錨點識別碼儲存至 HoloLens 2 以便擷取 (即使在重新啟動應用程式之後)，以及如何在多個裝置之間傳輸錨點識別碼以達到空間對齊。</span><span class="sxs-lookup"><span data-stu-id="cfe25-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cfe25-213">下一個教學課程：3.儲存、擷取和共用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="cfe25-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)