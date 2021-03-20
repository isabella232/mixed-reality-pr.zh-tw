---
title: 整合 Azure 自訂視覺
description: 完成此課程，以了解如何在 HoloLens 2 混合實境應用程式中執行 Azure 自訂視覺。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, hololens 2, azure 自訂視覺, azure 認知服務, azure 雲端服務, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: cb391aa2cdb7944234cdeede7dd05825c008d0d8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590570"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="6e622-104">3.整合 Azure 自訂視覺</span><span class="sxs-lookup"><span data-stu-id="6e622-104">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="6e622-105">您將在本教學課程中了解如何使用 **Azure 自訂視覺**。您將上傳一組相片，將其與「追蹤物件」產生關聯，然後上傳至 **自訂視覺** 服務並開始訓練程序。</span><span class="sxs-lookup"><span data-stu-id="6e622-105">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="6e622-106">接著，您將使用該服務從網路攝影機摘要中捕捉相片，以偵測「追蹤物件」。</span><span class="sxs-lookup"><span data-stu-id="6e622-106">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="6e622-107">目標</span><span class="sxs-lookup"><span data-stu-id="6e622-107">Objectives</span></span>

* <span data-ttu-id="6e622-108">了解 Azure 自訂視覺的基本概念</span><span class="sxs-lookup"><span data-stu-id="6e622-108">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="6e622-109">了解如何設定場景，以在此專案中使用自訂視覺</span><span class="sxs-lookup"><span data-stu-id="6e622-109">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="6e622-110">了解如何整合上傳、訓練和偵測影像</span><span class="sxs-lookup"><span data-stu-id="6e622-110">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="6e622-111">了解 Azure 自訂視覺</span><span class="sxs-lookup"><span data-stu-id="6e622-111">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="6e622-112">**Azure 自訂視覺** 是 **認知服務** 系列中的一部分，可用來訓練影像分類器。</span><span class="sxs-lookup"><span data-stu-id="6e622-112">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="6e622-113">影像分類器是一種 AI 服務，會使用訓練的模型來套用相符的標記。</span><span class="sxs-lookup"><span data-stu-id="6e622-113">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="6e622-114">我們的應用程式會使用此分類功能來偵測「追蹤物件」。</span><span class="sxs-lookup"><span data-stu-id="6e622-114">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="6e622-115">深入了解 [Azure 自訂視覺](/azure/cognitive-services/custom-vision-service/home)。</span><span class="sxs-lookup"><span data-stu-id="6e622-115">Learn more about [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="6e622-116">準備 Azure 自訂視覺</span><span class="sxs-lookup"><span data-stu-id="6e622-116">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="6e622-117">開始之前，您必須建立自訂視覺專案，而最快的方式是使用入口網站。</span><span class="sxs-lookup"><span data-stu-id="6e622-117">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="6e622-118">在＜上傳和標記影像＞區段之前，請遵循此[快速入門教學課程](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images)來設定帳戶和專案。</span><span class="sxs-lookup"><span data-stu-id="6e622-118">Follow this [quickstart tutorial](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="6e622-119">若要訓練模型，您必須至少有 2 個標記，且每個標記應有 5 個影像。</span><span class="sxs-lookup"><span data-stu-id="6e622-119">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="6e622-120">若要使用此應用程式，您應至少建立一個包含 5 個影像的標記，如此之後的訓練程序才不會失敗。</span><span class="sxs-lookup"><span data-stu-id="6e622-120">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="6e622-121">準備場景</span><span class="sxs-lookup"><span data-stu-id="6e622-121">Preparing the scene</span></span>

<span data-ttu-id="6e622-122">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureCloudServices] > [Prefabs] > [Manager] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e622-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![具有 [專案] 視窗的 Unity，顯示 ObjectDetectionManager Prefab 的路徑](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="6e622-124">從該處，將 Prefab **ObjectDetectionManager** 拖曳到場景階層中。</span><span class="sxs-lookup"><span data-stu-id="6e622-124">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![在偵測器中顯示了 ObjectDetectionManager 指令碼元件設定欄位的 Unity](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="6e622-126">在 [階層] 視窗中，找出 **ObjectDetectionManager** 物件並加以選取。</span><span class="sxs-lookup"><span data-stu-id="6e622-126">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="6e622-127">**ObjectDetectionManager** 預製專案包含 **ObjectDetectionManager (腳本)** 元件，您可以從 [偵測器] 視窗看到它相依于 Azure 設定和專案設定。</span><span class="sxs-lookup"><span data-stu-id="6e622-127">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on Azure settings and Project settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="6e622-128">擷取 Azure API 資源認證</span><span class="sxs-lookup"><span data-stu-id="6e622-128">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="6e622-129">您可以從 Azure 入口網站和自訂視覺入口網站取得 **ObjectDetectionManager (指令碼)** 設定的必要認證。</span><span class="sxs-lookup"><span data-stu-id="6e622-129">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="retrieving-azure-settings-credentials"></a><span data-ttu-id="6e622-130">正在抓取 Azure 設定認證</span><span class="sxs-lookup"><span data-stu-id="6e622-130">Retrieving Azure Settings credentials</span></span>

<span data-ttu-id="6e622-131">尋找並找出您已在本教學課程的「*準備場景*」一節中建立的 **認知服務** 類型的自訂視覺資源 (選取自訂視覺資源名稱，然後按下 *預測*) 。</span><span class="sxs-lookup"><span data-stu-id="6e622-131">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial (select custom vision resources name followed by *-Prediction* ).</span></span> <span data-ttu-id="6e622-132">按一下 *[總覽* ] 或 [ *金鑰和端點* ]，以取得所需的認證。</span><span class="sxs-lookup"><span data-stu-id="6e622-132">There click on *Overview* or *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="retrieving-project-settings-credentials"></a><span data-ttu-id="6e622-133">正在抓取專案設定認證</span><span class="sxs-lookup"><span data-stu-id="6e622-133">Retrieving Project Settings credentials</span></span>

<span data-ttu-id="6e622-134">在[自訂視覺](https://www.customvision.ai/projects)儀表板中，開啟您在本教學課程中建立的專案，然後按一下頁面右上角的齒輪圖示，以開啟設定頁面。</span><span class="sxs-lookup"><span data-stu-id="6e622-134">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="6e622-135">您會在右側的＜資源＞區段中找到所需的認證。</span><span class="sxs-lookup"><span data-stu-id="6e622-135">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="6e622-136">現在，正確設定 **ObjectDetectionManager (指令碼)** 之後，請在場景階層中尋找 **的 SceneController** 物件，然後加以選取。</span><span class="sxs-lookup"><span data-stu-id="6e622-136">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![在偵測器中顯示了 SceneController 指令碼元件設定欄位的 Unity](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="6e622-138">您會在 **SceneController** 元件中看到 [物件偵測管理員] 欄位是空的，請將 **ObjectDetectionManager** 從階層拖曳至該欄位並儲存場景。</span><span class="sxs-lookup"><span data-stu-id="6e622-138">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![已設定 SceneController 指令碼元件的 Unity](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="6e622-140">拍攝影像並上傳</span><span class="sxs-lookup"><span data-stu-id="6e622-140">Take and upload images</span></span>

<span data-ttu-id="6e622-141">執行場景並按一下 [設定物件]，然後輸入您在 [上一課](mr-learning-azure-02.md)中建立的其中一個 **追蹤物件名稱**。</span><span class="sxs-lookup"><span data-stu-id="6e622-141">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="6e622-142">現在，按一下 **物件卡片** 底部的 [電腦視覺] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6e622-142">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="6e622-143">新的視窗會隨即開啟，而您必須在其中拍攝六張相片來訓練模型，以進行影像辨識。</span><span class="sxs-lookup"><span data-stu-id="6e622-143">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="6e622-144">當您看到想要追蹤的物件時，請按一下 [相機] 按鈕並執行 AirTap，請執行此動作六次。</span><span class="sxs-lookup"><span data-stu-id="6e622-144">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="6e622-145">若要改善模型訓練，請嘗試拍攝角度和光源條件各不相同的影像。</span><span class="sxs-lookup"><span data-stu-id="6e622-145">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="6e622-146">當您有足夠的影像之後，請按一下 [訓練] 按鈕，在雲端中啟動模型訓練程序。</span><span class="sxs-lookup"><span data-stu-id="6e622-146">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="6e622-147">啟動訓練將會上傳所有影像並開始訓練，這可能需要一分鐘或更長的時間。</span><span class="sxs-lookup"><span data-stu-id="6e622-147">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="6e622-148">功能表內的訊息會指出目前進度，當其指示已完成時，您就可以停止應用程式</span><span class="sxs-lookup"><span data-stu-id="6e622-148">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="6e622-149">**ObjectDetectionManager (指令碼)** 會直接將拍攝的影像上傳至自訂視覺服務。</span><span class="sxs-lookup"><span data-stu-id="6e622-149">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="6e622-150">另一種方式是使用自訂視覺 API 接受影像的 URL，作為練習，您可以修改 **ObjectDetectionManager (指令碼)** ，改為將影像上傳至 Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="6e622-150">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="6e622-151">偵測物件</span><span class="sxs-lookup"><span data-stu-id="6e622-151">Detect objects</span></span>

<span data-ttu-id="6e622-152">在偵測物件之前，我們必須在已使用自訂視覺金鑰指派的專案設定下，變更  **ObjectDetectionManager (腳本)** 中所存在的 Api 金鑰。</span><span class="sxs-lookup"><span data-stu-id="6e622-152">Before detecting the objects we have to change the Api key present in  **ObjectDetectionManager (script)** under project settings that already assign with custom vision key.</span></span>

<span data-ttu-id="6e622-153">在 Azure 入口網站中尋找並找出自訂視覺資源。在 [專案設定] 下，按一下 [ *金鑰和端點* ] 以取得 Api 金鑰，並以舊的 Api 金鑰取代。</span><span class="sxs-lookup"><span data-stu-id="6e622-153">Find and locate the custom vision resource in Azure portal.There click on *Keys and Endpoint* to retrieve the Api key and replace with old Api key under project settings.</span></span>

<span data-ttu-id="6e622-154">您現在可以將訓練的模型放到測試中、執行應用程式，然後從 [主功能表] 中按一下 [搜尋物件]，接著輸入有問題的 **追蹤物件** 名稱。</span><span class="sxs-lookup"><span data-stu-id="6e622-154">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="6e622-155">**物件卡片** 會隨即出現，然後請按一下 [自訂視覺] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6e622-155">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="6e622-156">在這裡，**ObjectDetectionManager** 會開始在背景中取得相機中的拍攝影像，並在功能表上顯示進度。</span><span class="sxs-lookup"><span data-stu-id="6e622-156">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="6e622-157">將相機指向您用來訓練模型的物件，您將在不久後看到其已偵測到該物件。</span><span class="sxs-lookup"><span data-stu-id="6e622-157">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6e622-158">恭喜！</span><span class="sxs-lookup"><span data-stu-id="6e622-158">Congratulations</span></span>

<span data-ttu-id="6e622-159">在本教學課程中，您已了解如何使用 Azure 自訂視覺來訓練影像，並使用分類服務來偵測符合相關 **追蹤物件** 的影像。</span><span class="sxs-lookup"><span data-stu-id="6e622-159">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="6e622-160">在下一個教學課程中，您將了解如何使用 Azure Spatial Anchors，將「追蹤物件」與實體世界中的位置連結，以及如何顯示箭號來引導使用者回到追蹤物件的連結位置。</span><span class="sxs-lookup"><span data-stu-id="6e622-160">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6e622-161">下一個教學課程：4.整合 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="6e622-161">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)