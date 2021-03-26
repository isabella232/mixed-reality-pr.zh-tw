---
title: 整合 Azure 儲存體
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中執行 Azure 表格儲存體和 Azure Blob 儲存體。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, hololens 2, azure 儲存體, azure 雲端服務, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 189fea44da6d2da7cd98629a4a67c2f7c9340d2b
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550328"
---
# <a name="2-integrating-azure-storage"></a><span data-ttu-id="eca97-104">2.整合 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="eca97-104">2. Integrating Azure storage</span></span>

<span data-ttu-id="eca97-105">在本教學課程中，您將了解如何將實體資料儲存至 Azure 表格儲存體，並將縮圖影像儲存至 Azure Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="eca97-105">In this tutorial, you will learn how to save entity data to Azure Table storage and thumbnail images to Azure Blob storage.</span></span> <span data-ttu-id="eca97-106">這項功能可讓我們使用識別碼、名稱、縮圖影像等資料，在工作階段和裝置之間將「追蹤物件」儲存和擷取至雲端。</span><span class="sxs-lookup"><span data-stu-id="eca97-106">This feature will allow us to store and retrieve *Tracked Objects* with data like ID, Name, Thumbnail Image, etc. across sessions and devices to the cloud.</span></span>

## <a name="objectives"></a><span data-ttu-id="eca97-107">目標</span><span class="sxs-lookup"><span data-stu-id="eca97-107">Objectives</span></span>

* <span data-ttu-id="eca97-108">了解 Azure 儲存體的基本概念</span><span class="sxs-lookup"><span data-stu-id="eca97-108">Learn the basics about Azure storage</span></span>
* <span data-ttu-id="eca97-109">了解如何從表格儲存體儲存、修改和擷取資料</span><span class="sxs-lookup"><span data-stu-id="eca97-109">Learn how to store, modify and retrieve data from Table storage</span></span>
* <span data-ttu-id="eca97-110">了解如何從 Blob 儲存體儲存和刪除影像</span><span class="sxs-lookup"><span data-stu-id="eca97-110">Learn how to store and delete images from Blob storage</span></span>

## <a name="understanding-azure-storage"></a><span data-ttu-id="eca97-111">了解 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="eca97-111">Understanding Azure storage</span></span>

<span data-ttu-id="eca97-112">**Azure 儲存體** 是 Microsoft 的雲端儲存體解決方案，可涵蓋許多案例和需求。</span><span class="sxs-lookup"><span data-stu-id="eca97-112">**Azure storage** is a Microsoft storage solution on the cloud that can cover many scenarios and requirements.</span></span> <span data-ttu-id="eca97-113">開發人員可以進行大規模調整並輕鬆運用。</span><span class="sxs-lookup"><span data-stu-id="eca97-113">It can scale massively and is easily approachable by developers.</span></span> <span data-ttu-id="eca97-114">所有服務都可以在 **Azure 儲存體帳戶** 之下使用。</span><span class="sxs-lookup"><span data-stu-id="eca97-114">All services can be consumed under the umbrella of an **Azure storage Account**.</span></span> <span data-ttu-id="eca97-115">在我們的使用案例中，將會使用「表格儲存體」和「Blob 儲存體」。</span><span class="sxs-lookup"><span data-stu-id="eca97-115">For our use case we will use *Table storage* and *Blob storage*.</span></span>

<span data-ttu-id="eca97-116">深入了解 [Azure 儲存體服務](/azure/storage/blobs/storage-blobs-overview)。</span><span class="sxs-lookup"><span data-stu-id="eca97-116">Learn more about [Azure storage services](/azure/storage/blobs/storage-blobs-overview).</span></span>

### <a name="azure-table-storage"></a><span data-ttu-id="eca97-117">Azure 表格儲存體</span><span class="sxs-lookup"><span data-stu-id="eca97-117">Azure Table storage</span></span>

<span data-ttu-id="eca97-118">這項服務可讓我們以 NoSQL 的方式儲存資料，在此專案中，我們將使用這種方式來儲存「追蹤物件」的相關資訊，例如：名稱、描述、空間錨點識別碼等等。</span><span class="sxs-lookup"><span data-stu-id="eca97-118">This services allows us to store data in a NoSQL fashion, in this project we will use it to store information about the *Tracked Object* such as: name, description, spatial anchor id, and more.</span></span>

<span data-ttu-id="eca97-119">在示範應用程式的內容中，您需要兩個表格，其中一個用來儲存專案的相關資訊，其中包含有關已定型模型狀態 ([整合 Azure 自訂視覺](mr-learning-azure-03.md)) 教學課程的詳細資訊；第二個表格用來儲存「追蹤物件」的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eca97-119">In context of the demo application, you need two Tables, one to store information about the project with information about the state of trained models more about that in the ([Integrating Azure Custom Vision](mr-learning-azure-03.md)) tutorial and a second table to store information about *Tracked Objects*.</span></span>

<span data-ttu-id="eca97-120">深入了解 [Azure 表格儲存體](/azure/storage/tables/table-storage-overview)。</span><span class="sxs-lookup"><span data-stu-id="eca97-120">Learn more about [Azure Table storage](/azure/storage/tables/table-storage-overview).</span></span>

### <a name="azure-blob-storage"></a><span data-ttu-id="eca97-121">Azure Blob 儲存體</span><span class="sxs-lookup"><span data-stu-id="eca97-121">Azure Blob storage</span></span>

<span data-ttu-id="eca97-122">此服務可讓您儲存大型二進位檔案，您將使用此檔案將針對「追蹤物件」所拍攝的相片儲存為縮圖。</span><span class="sxs-lookup"><span data-stu-id="eca97-122">This service allows to store large binary files, you will use this to store photos taken for *Tracked Objects* as thumbnail.</span></span>
<span data-ttu-id="eca97-123">針對示範應用程式，您需要一個 Blob 容器來儲存影像。</span><span class="sxs-lookup"><span data-stu-id="eca97-123">For of the demo application you need one Blob Container to store the images.</span></span>

<span data-ttu-id="eca97-124">深入了解 [Azure Blob 儲存體](/azure/storage/blobs/storage-blobs-introduction)。</span><span class="sxs-lookup"><span data-stu-id="eca97-124">Learn more about [Azure Blob storage](/azure/storage/blobs/storage-blobs-introduction).</span></span>

## <a name="preparing-azure-storage"></a><span data-ttu-id="eca97-125">準備 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="eca97-125">Preparing Azure Storage</span></span>

<span data-ttu-id="eca97-126">若要取用 Azure 儲存體服務，您需要 Azure 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="eca97-126">To consume the Azure storage services you will need an Azure storage account.</span></span> <span data-ttu-id="eca97-127">若要建立儲存體帳戶，請參閱[如何建立儲存體帳戶](/azure/storage/common/storage-account-create?tabs=azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="eca97-127">To create a storage account, see [Create a storage account](/azure/storage/common/storage-account-create?tabs=azure-portal).</span></span> <span data-ttu-id="eca97-128">若要深入瞭解儲存體帳戶，請參閱 [Azure 儲存體帳戶概觀](/azure/storage/common/storage-account-overview)。</span><span class="sxs-lookup"><span data-stu-id="eca97-128">To learn more about storage accounts, see [Azure storage account overview](/azure/storage/common/storage-account-overview).</span></span>

<span data-ttu-id="eca97-129">準備好儲存體帳戶後，您就可以從 **Azure 入口網站** 擷取連接字串，您會在本課程的下一節中用到此一資訊。</span><span class="sxs-lookup"><span data-stu-id="eca97-129">Once you have a storage account, you can retrieve the connection string from the **Azure Portal** which will be needed in the next section of this lesson.</span></span>

### <a name="optional-azure-storage-explorer"></a><span data-ttu-id="eca97-130">選用的 Azure 儲存體總管</span><span class="sxs-lookup"><span data-stu-id="eca97-130">Optional Azure Storage Explorer</span></span>

<span data-ttu-id="eca97-131">雖然您可以從應用程式內的 UI 查看及確認所有資料變更，但我們建議您安裝 [Azure 儲存體總管](https://azure.microsoft.com/features/storage-explorer/)。</span><span class="sxs-lookup"><span data-stu-id="eca97-131">While you can see and verify all data changes from the UI inside the application, we recommend to install [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="eca97-132">此工具可讓您以視覺化方式查看 Azure 儲存體中的資料，並在偵錯和學習時提供絕佳的協助。</span><span class="sxs-lookup"><span data-stu-id="eca97-132">This tool allows you to visually see the data in the Azure storage and is of great help when debugging and learning.</span></span>

> [!TIP]
> <span data-ttu-id="eca97-133">若要從 Unity 編輯器內部進行測試，您可以使用本機模擬器：</span><span class="sxs-lookup"><span data-stu-id="eca97-133">For testing from inside the Unity editor you can use a local emulator:</span></span>
>
> * <span data-ttu-id="eca97-134">在 Windows 10 上，您可以使用 [Azure 儲存體模擬器](/azure/storage/common/storage-use-emulator)</span><span class="sxs-lookup"><span data-stu-id="eca97-134">on Windows 10 you can use [Azure Storage Emulator](/azure/storage/common/storage-use-emulator)</span></span>
> * <span data-ttu-id="eca97-135">在 MacOS/Linux 上，您可以使用適用於 Docker 的 [Azurite Docker 影像](https://hub.docker.com/_/microsoft-azure-storage-azurite)</span><span class="sxs-lookup"><span data-stu-id="eca97-135">on MacOS/Linux you can use [Azurite Docker Image](https://hub.docker.com/_/microsoft-azure-storage-azurite) for Docker</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="eca97-136">準備場景</span><span class="sxs-lookup"><span data-stu-id="eca97-136">Preparing the scene</span></span>

<span data-ttu-id="eca97-137">在階層視窗中，找出 **DataManager** 物件並加以選取。</span><span class="sxs-lookup"><span data-stu-id="eca97-137">In the Hierarchy window, locate the **DataManager** object and select it.</span></span>

![在偵測器中顯示了 DataManager 指令碼元件設定欄位的 Unity](images/mr-learning-azure/tutorial2-section4-step1-1.png)

<span data-ttu-id="eca97-139">在偵測器視窗中，您會看到 **DataManager (指令碼)** 元件是保留所有 **Azure 儲存體** 相關設定的位置。</span><span class="sxs-lookup"><span data-stu-id="eca97-139">From the Inspector window you will see that the **DataManager (script)** component is where all **Azure storage** related settings are kept.</span></span> <span data-ttu-id="eca97-140">所有相關的設定都已設定完成，您只需要將「連接字串」欄位取代為您可以從 Azure 入口網站取得的值。</span><span class="sxs-lookup"><span data-stu-id="eca97-140">All relevant settings are already set, you just need to replace the *Connection String* field with the one you can retrieve from the Azure Portal.</span></span> <span data-ttu-id="eca97-141">如果您使用本機 Azure 儲存體模擬器解決方案，則可以保留已提供的「連接字串」。</span><span class="sxs-lookup"><span data-stu-id="eca97-141">If you are using a local Azure storage emulator solution, then you can keep the already provided *Connection String*.</span></span>

<span data-ttu-id="eca97-142">**DataManager (指令碼)** 負責與 **表格儲存體** 和 **Blob 儲存體** 溝通，這兩者是由 UI 元件上的其他控制器指令碼使用。</span><span class="sxs-lookup"><span data-stu-id="eca97-142">The **DataManager (script)** is responsible for talking to the **Table storage** and **Blob storage** which is consumed by other controller scripts on the UI components.</span></span>

## <a name="writing-and-reading-data-from-azure-table-storage"></a><span data-ttu-id="eca97-143">從 Azure 表格儲存體寫入和讀取資料</span><span class="sxs-lookup"><span data-stu-id="eca97-143">Writing and reading data from Azure Table storage</span></span>

<span data-ttu-id="eca97-144">一切準備就緒後，就可以建立「追蹤物件」。</span><span class="sxs-lookup"><span data-stu-id="eca97-144">With everything prepared it's time to create a *Tracked Object*.</span></span>

<span data-ttu-id="eca97-145">開啟 HoloLens 上的應用程式，按一下 [設定物件]，您就會看到 EnterObjectName 物件在階層中變成使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="eca97-145">Open the application on your HoloLens, click on the **Set Object** and you will see how the *EnterObjectName* object will become active in the hierarchy.</span></span> <span data-ttu-id="eca97-146">在此功能表中，按一下 [搜尋列]，然後輸入想要提供「追蹤物件」的名稱。</span><span class="sxs-lookup"><span data-stu-id="eca97-146">In this menu click on the *search bar* and type in the name you want to give the *Tracked Object*.</span></span> <span data-ttu-id="eca97-147">提供名稱之後，請按一下 [設定物件] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eca97-147">After providing a name click on the **Set object** button.</span></span> <span data-ttu-id="eca97-148">這會在 Azure 表格儲存體上建立「追蹤物件」，而您現在會看到 **物件卡**。</span><span class="sxs-lookup"><span data-stu-id="eca97-148">This will create the *Tracked Object* on the Azure Table storage and you will see now the **Object Card**.</span></span>

<span data-ttu-id="eca97-149">此 **物件卡** 是「追蹤物件」 的 UI 標記法，在本教學課程系列中多次扮演重要的角色。</span><span class="sxs-lookup"><span data-stu-id="eca97-149">This **Object Card** is a UI representation of the *Tracked Object* and will have an important role several times in this tutorial series.</span></span>

<span data-ttu-id="eca97-150">現在，按一下描述 [文字方塊] 並輸入 "Car"，然後按一下 [儲存] 按鈕以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="eca97-150">Now click on the description *text box* and type in "Car", after that click on the **Save** button to save the changes.</span></span> <span data-ttu-id="eca97-151">停止應用程式並重新執行。</span><span class="sxs-lookup"><span data-stu-id="eca97-151">Stop the application and rerun it.</span></span>

<span data-ttu-id="eca97-152">現在按一下 [搜尋物件]，然後在「搜尋列」中輸入您在建立「追蹤物件」時所使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="eca97-152">Now this time click on **Search Object** and type in the *search bar* the name you have used before when creating the *Tracked Object*.</span></span> <span data-ttu-id="eca97-153">您會看到 **物件卡**，其中包含所有從 **Azure 表格儲存體** 中擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="eca97-153">You will see that the **Object Card** with all the data is retrieved from the **Azure Table storage**.</span></span>

<span data-ttu-id="eca97-154">依需求關閉 **物件卡** 並建立新的「追蹤物件」｜然後編輯其資料。</span><span class="sxs-lookup"><span data-stu-id="eca97-154">Feel free to close the **Object Card** and create new *Tracked Objects* and edit their data.</span></span>

> [!TIP]
> <span data-ttu-id="eca97-155">如果您已安裝 [Azure 儲存體總管](https://azure.microsoft.com/features/storage-explorer/)，請查看「物件」資料表，您會看到已建立的「追蹤物件」。</span><span class="sxs-lookup"><span data-stu-id="eca97-155">If you have installed the [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) then look into the *objects* table and you will see there the created *Tracked Object*.</span></span>

## <a name="uploading-and-download-image-from-azure-blob-storage"></a><span data-ttu-id="eca97-156">從 Azure Blob 儲存體上傳和下載影像</span><span class="sxs-lookup"><span data-stu-id="eca97-156">Uploading and Download image from Azure Blob storage</span></span>

<span data-ttu-id="eca97-157">在本節中，您將使用 Azure Blob 儲存體上傳和下載會用作「追蹤物件」縮圖的影像。</span><span class="sxs-lookup"><span data-stu-id="eca97-157">In this section you will use the Azure Blob storage to upload and download images that will be used as thumbnails for *Tracked Objects*.</span></span>

> [!NOTE]
> <span data-ttu-id="eca97-158">在本教學課程中，應用程式會拍照以將影像上傳至 Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="eca97-158">In this tutorial the application will take photos to upload images to the Blob storage.</span></span> <span data-ttu-id="eca97-159">如果您是從 Unity 編輯器本機執行此程式，請確定已將網路攝影機與電腦連線。</span><span class="sxs-lookup"><span data-stu-id="eca97-159">If you are running this locally from the Unity editor, then make sure that you have a webcam connected to your computer.</span></span>

<span data-ttu-id="eca97-160">在 HoloLens 上開啟應用程式，按一下 [設定物件]，然後在「搜尋列」中輸入名稱 "Car"。</span><span class="sxs-lookup"><span data-stu-id="eca97-160">Open the application on your HoloLens, click on **Set Object** and type in the *search bar* the name "Car".</span></span> <span data-ttu-id="eca97-161">現在您應該會看到 **物件卡**，請按一下 [相機] 按鈕，系統會指示您使用 AirTap 拍照。</span><span class="sxs-lookup"><span data-stu-id="eca97-161">Now you should see the **Object Card**, click on the **Camera** button and you will be instructed to do an AirTap to take a photo.</span></span> <span data-ttu-id="eca97-162">拍攝相片後，您會看到一則訊息，通知您正在上傳資料；一段時間後，影像應該會出現在之前保留的預留位置。</span><span class="sxs-lookup"><span data-stu-id="eca97-162">After taking a photo you will see a message that informs you about the active upload and after a while the image should appear where the placeholder was before.</span></span>

<span data-ttu-id="eca97-163">現在重新執行應用程式，並搜尋「追蹤物件」，先前上傳的影像應該會顯示為縮圖。</span><span class="sxs-lookup"><span data-stu-id="eca97-163">Now rerun the application and search for the *Tracked Object* and the previously uploaded image should appear as thumbnail.</span></span>

## <a name="deleting-image-from-azure-blob-storage"></a><span data-ttu-id="eca97-164">從 Azure Blob 儲存體刪除影像</span><span class="sxs-lookup"><span data-stu-id="eca97-164">Deleting image from Azure Blob storage</span></span>

<span data-ttu-id="eca97-165">在上一節中，您已將新的影像上傳至 Azure Blob 儲存體；在本節中，您將會刪除「追蹤物件」的影像縮圖。</span><span class="sxs-lookup"><span data-stu-id="eca97-165">In the previous section you uploaded new images to Azure Blob storage, in this section you will delete an image thumbnail for *Tracked Objects*.</span></span>

<span data-ttu-id="eca97-166">在 HoloLens 上開啟應用程式，按一下 [設定物件]，然後在「搜尋列」中輸入名稱 "Car"。</span><span class="sxs-lookup"><span data-stu-id="eca97-166">Open the application on your HoloLens, click on **Set Object** and type in the *search bar* the name "Car".</span></span> <span data-ttu-id="eca97-167">現在您應該會看到 **物件卡** 與縮圖影像，請按一下 [刪除] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eca97-167">Now you should see the **Object Card** with the thumbnail image, click on the **Delete** button.</span></span> <span data-ttu-id="eca97-168">您會發現縮圖影像已由預留位置影像所取代。</span><span class="sxs-lookup"><span data-stu-id="eca97-168">You will notice that the thumbnail image is replaced by the placeholder image.</span></span>

<span data-ttu-id="eca97-169">現在重新執行應用程式，並搜尋先前已刪除其縮圖的「追蹤物件」，您應該只會看到預留位置影像。</span><span class="sxs-lookup"><span data-stu-id="eca97-169">Now rerun the application and search for the *Tracked Object* of the previously deleted thumbnail, you should only see the placeholder image.</span></span>

## <a name="congratulations"></a><span data-ttu-id="eca97-170">恭喜！</span><span class="sxs-lookup"><span data-stu-id="eca97-170">Congratulations</span></span>

<span data-ttu-id="eca97-171">在本教學課程中，您已了解如何使用 Azure 儲存體服務來保存非結構化資料；在我們的案例中為 **追蹤物件**，而雲端上的 **HoloLens 2** 示範應用程式的二進位檔則是以縮圖影像的形式出現。</span><span class="sxs-lookup"><span data-stu-id="eca97-171">In this tutorial you learned how Azure storage services can be used to persist unstructured data, like in our case **Tracked Objects** and binaries in form of thumbnail images for the **HoloLens 2** demo application on the cloud.</span></span>

<span data-ttu-id="eca97-172">在下一個教學課程中，您將了解如何使用 Azure 自訂視覺來偵測與「追蹤物件」相關聯的影像。</span><span class="sxs-lookup"><span data-stu-id="eca97-172">In the next tutorial you will learn how to use Azure Custom Vision to detect images associated with a *Tracked Object*.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eca97-173">下一個教學課程：3.整合 Azure 自訂視覺</span><span class="sxs-lookup"><span data-stu-id="eca97-173">Next tutorial: 3. Integrating Azure Custom Vision</span></span>](mr-learning-azure-03.md)