---
title: 整合 Azure Spatial Anchors
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, hololens 2, Azure 空間錨點, azure 雲端服務, azure 自訂視覺, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 0837ebd9d34ba12d660098fc765824da3c561d07
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590540"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="4f3cb-104">4.整合 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="4f3cb-104">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="4f3cb-105">在本教學課程中，您將了解如何使用 **Azure Spatial Anchors**。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-105">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="4f3cb-106">您會將 **追蹤物件** 儲存為 Azure Spatial Anchor。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-106">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="4f3cb-107">查詢錨點之後將會出現一個箭號，引導您前往該位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-107">Once you query for the anchor, an arrow will appear to guide you toward the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="4f3cb-108">目標</span><span class="sxs-lookup"><span data-stu-id="4f3cb-108">Objectives</span></span>

* <span data-ttu-id="4f3cb-109">了解 Azure Spatial Anchors 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-109">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="4f3cb-110">了解如何設定場景，以在此專案中使用 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-110">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="4f3cb-111">了解如何整合儲存和查詢位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-111">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="4f3cb-112">了解 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="4f3cb-112">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="4f3cb-113">**Azure Spatial Anchors** 是 Azure 雲端服務系列中的一部分，可用來儲存錨點位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-113">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="4f3cb-114">您可以根據雲端的「錨點識別碼」來擷取已儲存的錨點位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-114">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="4f3cb-115">此錨點位置可以由多平台裝置共用及存取，例如 HoloLens、iOS 和 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-115">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="4f3cb-116">深入了解 [Azure Spatial Anchors](/azure/spatial-anchors/overview)。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-116">Learn more about [Azure Spatial Anchors](/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="4f3cb-117">準備 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="4f3cb-117">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="4f3cb-118">開始之前，您必須在 Azure 入口網站中建立空間錨點資源。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-118">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="4f3cb-119">了解如何建立[空間錨點資源](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-119">Learn how to make a [spatial anchor resource](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="4f3cb-120">準備場景</span><span class="sxs-lookup"><span data-stu-id="4f3cb-120">Preparing the scene</span></span>

<span data-ttu-id="4f3cb-121">在本節中，您將了解如何設定場景，並進行必要的變更。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-121">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="4f3cb-122">在 [專案] 視窗中，瀏覽至 [資產] > [MRTKMRTK.Tutorials.AzureCloudServices] > [Prefabs] > [Manager]</span><span class="sxs-lookup"><span data-stu-id="4f3cb-122">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![已選取 AnchorManager Prefab 的 Unity](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="4f3cb-124">從 [Manager] 資料夾，將 Prefab **Anchor Manager** 拖放到場景階層中。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-124">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="4f3cb-125">選取階層中的 **Anchor Manager** GameObject，然後在 [偵測器] 區段中，您會看到 **Spatial Anchor Manager** (指令碼)。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-125">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="4f3cb-126">尋找 [帳戶識別碼] 和 [金鑰] 欄位，然後新增您在先前階段的必要條件中所建立的認證。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-126">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![已選取新增 AnchorManager Prefab 的 Unity](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="4f3cb-128">現在，在場景階層中尋找 **Scene Controller** 物件，然後加以選取。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-128">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="4f3cb-129">您會看到 **Scene Controller** 偵測器。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-129">You will see the **Scene Controller** Inspector.</span></span>

![已設定 SceneController 指令碼元件的 Unity](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="4f3cb-131">您會發現 **Scene Controller** 中的 **Anchor Manager** 欄位是空的，請將 **Anchor Manager** 從場景中的階層拖放到該欄位，然後儲存場景。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-131">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="4f3cb-132">建置應用程式，並將其部署至 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4f3cb-132">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="4f3cb-133">Azure Spatial Anchors 無法在 Unity 中執行，因此若要測試 Azure Spatial Anchors 功能，您必須將專案部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-133">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="4f3cb-134">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱 [對您的 HoloLens 2 建置應用程式] (mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) 的指示。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-134">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="4f3cb-135">在 HoloLens 2 上執行應用程式，並遵循應用程式內的指示</span><span class="sxs-lookup"><span data-stu-id="4f3cb-135">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="4f3cb-136">建立錨點以儲存位置</span><span class="sxs-lookup"><span data-stu-id="4f3cb-136">Create an anchor to store a location</span></span>

<span data-ttu-id="4f3cb-137">在本節中，您將了解如何儲存物件位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-137">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="4f3cb-138">執行應用程式，然後在體驗的主功能表中，按一下 [設定物件]。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-138">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="4f3cb-139">提供您想要儲存的物件 **名稱**，然後按一下 [設定物件] 以繼續。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-139">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="4f3cb-140">若要新增有關物件的詳細資訊，請選取 **影像**，並描述物件。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-140">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="4f3cb-141">若要儲存位置，請按一下 [儲存位置]</span><span class="sxs-lookup"><span data-stu-id="4f3cb-141">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="4f3cb-142">您會看到 **錨點指標**，您可以在想要儲存的位置上移動和放置該指標。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-142">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="4f3cb-143">之後，您會看到確認快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-143">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="4f3cb-144">如果您想要確認並儲存位置，請按一下 [是]；否則，您可以按一下 [否]，然後再次選取位置來變更位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-144">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="4f3cb-145">當您按一下 [是] 來確認位置之後，位置和錨點識別碼將會儲存在 Azure 雲端儲存體中。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-145">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="4f3cb-146">儲存之後，您會在錨點中看到具有物件名稱的 **物件標記**。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-146">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="4f3cb-147">現在已成功儲存物件位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-147">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="4f3cb-148">尋找錨點位置的查詢</span><span class="sxs-lookup"><span data-stu-id="4f3cb-148">Query for finding an anchor location</span></span>

<span data-ttu-id="4f3cb-149">成功儲存錨點位置之後，您現在可以在主功能表中選取 [搜尋物件] 來尋找錨點位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-149">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="4f3cb-150">按一下 [搜尋物件] 之後，新視窗會隨即出現，您應該在其中提供要搜尋的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-150">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="4f3cb-151">輸入物件的名稱，然後按一下 [搜尋物件]。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-151">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="4f3cb-152">如果先前已儲存物件，而且可在資料庫中找到，您將會取得物件卡片，其中包含您稍早所儲存物件的所有詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-152">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="4f3cb-153">現在您可以按一下 [顯示位置] 來尋找物件。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-153">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="4f3cb-154">按一下 [顯示位置] 之後，系統就會從雲端儲存體中查詢物件位址。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-154">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="4f3cb-155">成功擷取位置之後，**箭頭** 就會將您導向物件的位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-155">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="4f3cb-156">遵循箭頭標記，直到您找到物件的位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-156">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="4f3cb-157">您找到物件後，物件名稱就會出現在頂端，而箭頭將會消失，此時您可以按一下 [物件標記] 來查看物件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-157">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4f3cb-158">恭喜！</span><span class="sxs-lookup"><span data-stu-id="4f3cb-158">Congratulations</span></span>

<span data-ttu-id="4f3cb-159">在本教學課程中，您已了解 Azure Spatial Anchors 可以如何儲存和擷取 Hololense 2 上的物件位置。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-159">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="4f3cb-160">在最後一個教學課程中，您將了解如何使用 **Azure Bot Service**，將自然語言新增為我們應用程式的新互動方法。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-160">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4f3cb-161">下一個教學課程：5.整合 Azure Bot Service 與 LUIS</span><span class="sxs-lookup"><span data-stu-id="4f3cb-161">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)