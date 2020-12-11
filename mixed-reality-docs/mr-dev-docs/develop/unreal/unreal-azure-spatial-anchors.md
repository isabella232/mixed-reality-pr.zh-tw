---
title: Unreal 中的 Azure Spatial Anchors
description: 在 Unreal Engine 中建立 Azure Spatial Anchors 的概觀。
author: hferrone
ms.author: jacksonf
ms.date: 07/01/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, azure 開發, 空間錨點, 混合實境, 開發, 功能, 新專案, 模擬器, 文件, 指南, 全像投影, 遊戲開發, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 4714957c3ddab188a776c86f839208759c9d20de
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609739"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="1bcf3-104">Unreal 中的 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="1bcf3-104">Azure Spatial Anchors in Unreal</span></span>

<span data-ttu-id="1bcf3-105">Azure Spatial Anchors 是 Microsoft Mixed Reality 服務，可讓擴增實境裝置探索、共用及保存實體世界中的錨點。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-105">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="1bcf3-106">以下文件提供將 Azure Spatial Anchors 服務整合到 Unreal 專案中的指示。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-106">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="1bcf3-107">如果您要尋找更多資訊，請參閱 [Azure Spatial Anchors 服務](https://azure.microsoft.com/services/spatial-anchors/)。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-107">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="1bcf3-108">如果您以 iOS 或 Android 作為目標，則 Unreal Engine 4.26 現在有適用於 ARKit 和 ARCore 支援的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-108">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bcf3-109">本機錨點會儲存在裝置上，而 Azure Spatial Anchors 會儲存在雲端。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="1bcf3-110">如果您要將錨點儲存在裝置本機上，我們有[本機空間錨點](unreal-spatial-anchors.md)文件，可協助您逐步完成此程序。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="1bcf3-111">請注意，您在同一個專案中可以有本機和 Azure 錨點，而不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1bcf3-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="1bcf3-112">Prerequisites</span></span>

<span data-ttu-id="1bcf3-113">若要完成本指南，請確定您：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="1bcf3-114">已安裝 [Unreal 4.25 版](https://www.unrealengine.com/get-now)或更新版本</span><span class="sxs-lookup"><span data-stu-id="1bcf3-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="1bcf3-115">在 Unreal 中設定了 [HoloLens 2 專案](tutorials/unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="1bcf3-115">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="1bcf3-116">請參閱 [Azure Spatial Anchors 概觀](https://docs.microsoft.com/azure/spatial-anchors/overview)</span><span class="sxs-lookup"><span data-stu-id="1bcf3-116">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="1bcf3-117">C++ 和 Unreal 的基本知識</span><span class="sxs-lookup"><span data-stu-id="1bcf3-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="1bcf3-118">取得 Azure Spatial Anchors 帳戶資訊</span><span class="sxs-lookup"><span data-stu-id="1bcf3-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="1bcf3-119">在您的專案中使用 Azure Spatial Anchors 之前，您必須：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="1bcf3-120">[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)並複製下列帳戶欄位。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-120">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="1bcf3-121">這些值用來向您的應用程式帳戶驗證使用者：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="1bcf3-122">**帳戶識別碼**</span><span class="sxs-lookup"><span data-stu-id="1bcf3-122">**Account ID**</span></span>
    * <span data-ttu-id="1bcf3-123">**帳戶金鑰**</span><span class="sxs-lookup"><span data-stu-id="1bcf3-123">**Account Key**</span></span>

<span data-ttu-id="1bcf3-124">如需詳細資訊，請參閱 [Azure Spatial Anchors 驗證](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp)文件。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-124">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="1bcf3-125">Unreal 4.25 中的 Azure Spatial Anchors 不支援 Azure AD 驗證權杖，但這項功能的支援將會在後續版本中推出。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="1bcf3-126">新增 Azure Spatial Anchors 外掛程式</span><span class="sxs-lookup"><span data-stu-id="1bcf3-126">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="1bcf3-127">在 Unreal 編輯器中啟用 Azure Spatial Anchors 外掛程式，方法如下：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-127">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="1bcf3-128">按一下 [編輯] > [外掛程式] 並搜尋 **AzureSpatialAnchors** 和 **AzureSpatialAnchorsForWMR**。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-128">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="1bcf3-129">在兩個外掛程式中選取 [已啟用] 核取方塊，以允許存取您應用程式中的 Azure Spatial Anchors 藍圖程式庫。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-129">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Unreal 編輯器中的空間錨點外掛程式的螢幕擷取畫面](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="1bcf3-131">完成後，請重新啟動 Unreal 編輯器，讓外掛程式變更生效。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-131">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="1bcf3-132">專案現在已準備好使用 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-132">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="1bcf3-133">啟動空間錨點工作階段</span><span class="sxs-lookup"><span data-stu-id="1bcf3-133">Starting a Spatial Anchors session</span></span>

<span data-ttu-id="1bcf3-134">Azure Spatial Anchors 工作階段可讓用戶端應用程式與 Azure Spatial Anchors 服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-134">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="1bcf3-135">您必須建立並啟動 Azure Spatial Anchors 工作階段，才能建立、保存和共用 Azure Spatial Anchors：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-135">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="1bcf3-136">針對您在應用程式中使用的 Pawn 開啟藍圖。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-136">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="1bcf3-137">為 [帳戶識別碼] 和 [帳戶金鑰] 新增兩個字串變數，然後從您的 Azure Spatial Anchors 帳戶指派對應的值，以驗證工作階段。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-137">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![詳細資料面板的螢幕擷取畫面，其中已醒目提示 Azure Spatial Anchors 帳戶識別碼、金鑰和變數類型](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="1bcf3-139">啟動 Azure Spatial Anchors 工作階段，方法如下：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-139">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="1bcf3-140">檢查 [AR 工作階段] 是否正在 HoloLens 應用程式中執行，因為直到 AR 工作階段執行，才能啟動 Azure Spatial Anchors 工作階段。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-140">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="1bcf3-141">如果您尚未設定工作階段，請[建立 AR 工作階段資產](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-141">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="1bcf3-142">新增 [啟動 Azure Spatial Anchors 工作階段] 自訂事件並加以設定，如下列螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-142">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="1bcf3-143">建立工作階段時，依預設不會啟動工作階段，這可讓您使用 Azure Spatial Anchors 服務設定工作階段以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-143">Creating a session doesn't start the session by default, which allows you to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![開始 Azure Spatial Anchors 工作階段自訂事件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="1bcf3-145">設定 Azure Spatial Anchors 工作階段，以提供 [帳戶識別碼] 和 [帳戶金鑰]。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-145">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![已新增帳戶識別碼和金鑰的設定工作階段函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="1bcf3-147">啟動 Azure Spatial Anchors 工作階段，讓應用程式能夠建立及尋找 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-147">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Azure Spatial Anchors 工作階段啟動函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="1bcf3-149">當您不再使用該服務時，在事件圖形藍圖中清除 Azure Spatial Anchors 資源是很好的作法：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-149">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="1bcf3-150">停止 Azure Spatial Anchors 工作階段。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-150">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="1bcf3-151">工作階段將不再執行，但其相關聯的資源仍會存在於 Azure Spatial Anchors 外掛程式中。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-151">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![停止 Azure Spatial Anchors 工作階段自訂事件和停止工作階段函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="1bcf3-153">終結 Azure Spatial Anchors 工作階段，以清除 Azure Spatial Anchors 外掛程式仍知道的任何 Azure Spatial Anchors 工作階段資源。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-153">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![終結工作階段函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="1bcf3-155">您的事件圖形藍圖看起來應該類似下列螢幕擷取畫面：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-155">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Azure Spatial Anchors 工作階段設定的完整事件圖形的藍圖](images/asa-unreal/unreal-spatial-anchors-img-08.png)

## <a name="creating-an-anchor"></a><span data-ttu-id="1bcf3-157">建立錨點</span><span class="sxs-lookup"><span data-stu-id="1bcf3-157">Creating an anchor</span></span>

<span data-ttu-id="1bcf3-158">Azure Spatial Anchors 代表擴增實境應用程式空間中的實體世界姿態，會將擴增實境內容連結至實體位置。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-158">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to physical locations.</span></span> <span data-ttu-id="1bcf3-159">Azure Spatial Anchors 也可以在不同的使用者間共用。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-159">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="1bcf3-160">此共用可讓在不同裝置上繪製的擴增實境內容放置於實體世界中的相同位置。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-160">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="1bcf3-161">若要建立新的 Azure Spatial Anchors：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-161">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="1bcf3-162">檢查 Azure Spatial Anchors 工作階段是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-162">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="1bcf3-163">若沒有任何正在執行的 Azure Spatial Anchors 工作階段，應用程式就無法建立或保存 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-163">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![建立 Azure Spatial Anchors 自訂事件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="1bcf3-165">建立或取得應保存其位置的 Unreal **[場景元件](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** 。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-165">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="1bcf3-166">在下圖中，[需要錨點的場景元件] 元件會當作變數使用。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-166">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="1bcf3-167">需要 Unreal 場景元件才能建立 [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) 和 Azure Spatial Anchors 的應用程式世界轉換。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-167">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![建立 Azure Spatial Anchors 自訂事件與場景元件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="1bcf3-169">若要為 Unreal 場景元件建構並儲存 Azure Spatial Anchors：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-169">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="1bcf3-170">針對 Unreal 場景元件呼叫 [Pin 元件](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html)，並指定場景元件的 [世界轉換] 作為用於 AR Pin 的世界轉換。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-170">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="1bcf3-171">Unreal 會使用 AR Pin 來追蹤應用程式空間中的 AR 點，其用來建立 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-171">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="1bcf3-172">在 Unreal 中，AR Pin 類似於 HoloLens 上的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-172">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![連線至釘選元件函式之場景元件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="1bcf3-174">使用新建立的 AR Pin 呼叫 [建立雲端錨點]。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-174">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="1bcf3-175">「建立雲端錨點」會在本機建立 Azure Spatial Anchors，但不在 Azure Spatial Anchors 服務中。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-175">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="1bcf3-176">在透過服務建立 Azure Spatial Anchors 之前，可以設定 Azure Spatial Anchors 的參數 (例如到期日)。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-176">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![釘選元件函式連線至會傳回 ARPin 的建立雲端錨點函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="1bcf3-178">設定 Azure Spatial Anchors 到期。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-178">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="1bcf3-179">此函式的 Lifetime 參數可讓開發人員以秒為單位指定服務應維護錨點的時間長度。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-179">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="1bcf3-180">例如，為期一週的到期日會採用 60秒 x 60 分鐘 x 24 小時 x 7 天 = 604,800 秒的值。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-180">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![雲端錨點連線至設定到期函式 (存留期值設定為 604,800 秒) 的藍圖](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="1bcf3-182">設定錨點參數之後，請將錨點宣告為準備好儲存。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-182">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="1bcf3-183">在下列範例中，新建立的 Azure Spatial Anchors 會新增至需要儲存的一組 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-183">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="1bcf3-184">此集合會宣告為 Pawn 藍圖的變數。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-184">This set is declared as a variable for the Pawn blueprint.</span></span>

![錨點已準備好要儲存在設定變數中的藍圖](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="1bcf3-186">儲存錨點</span><span class="sxs-lookup"><span data-stu-id="1bcf3-186">Saving an Anchor</span></span>

<span data-ttu-id="1bcf3-187">使用您的參數設定 Azure Spatial Anchors 之後，請呼叫 [儲存雲端錨點]。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-187">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="1bcf3-188">「儲存雲端錨點」會對 Azure Spatial Anchors 服務宣告錨點。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-188">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="1bcf3-189">當「儲存雲端錨點」的呼叫成功時，Azure Spatial Anchors 可供 Azure Spatial Anchors 服務的其他使用者使用。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-189">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![呼叫的儲存雲端錨點函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="1bcf3-191">「儲存雲端錨點」是非同步函式，只能在遊戲執行緒事件 (例如 **EventTick**) 上呼叫。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-191">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="1bcf3-192">「儲存雲端錨點」可能不會顯示為自訂藍圖函式中可用的藍圖函式。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-192">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="1bcf3-193">不過，其應可在 Pawn 事件圖形藍圖編輯器中使用。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-193">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="1bcf3-194">在下列範例中，Azure Spatial Anchors 會在輸入事件回呼期間儲存在集合中。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-194">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="1bcf3-195">然後錨點會儲存在 EventTick 上。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-195">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="1bcf3-196">視您的 Azure Spatial Anchors 工作階段所建立的空間資料量而定，儲存 Azure Spatial Anchors 可能會進行多次嘗試。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-196">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="1bcf3-197">這就是為何檢查儲存呼叫是否成功是個好主意。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-197">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="1bcf3-198">若未儲存錨點，請將其重新新增至仍需要儲存的錨點集合。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-198">If the anchor doesn't save, readd it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="1bcf3-199">未來的 EventTicks 會繼續嘗試儲存錨點，直到成功儲存為止。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-199">Future EventTicks will keep trying to save the anchor until it's successfully stored.</span></span>

![未儲存的錨點再次儲存到設定變數中的藍圖](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="1bcf3-201">儲存錨點後，AR Pin 的轉換可作為參考轉換，以便將內容放在您的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-201">Once the anchor saves, the AR Pins' transform acts as a reference transform for placing content in your app.</span></span> <span data-ttu-id="1bcf3-202">其他使用者可以偵測此錨點，並針對實體世界中的不同裝置對齊 AR 內容。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-202">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="1bcf3-203">刪除錨點</span><span class="sxs-lookup"><span data-stu-id="1bcf3-203">Deleting an Anchor</span></span>

<span data-ttu-id="1bcf3-204">您可藉由呼叫 [刪除雲端錨點]，從 Azure Spatial Anchors 服務刪除錨點。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-204">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![呼叫的刪除雲端錨點函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="1bcf3-206">「刪除雲端錨點」是潛伏的函式，只能在遊戲執行緒事件 (例如 EventTick) 上呼叫。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-206">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="1bcf3-207">「刪除雲端錨點」可能不會顯示為自訂藍圖函式中可用的藍圖函式。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-207">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="1bcf3-208">不過，其應可在 Pawn 事件圖形藍圖編輯器中使用。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-208">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="1bcf3-209">在下列範例中，錨點會在自訂輸入事件上標示要刪除。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-209">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="1bcf3-210">然後會在 EventTick 上嘗試刪除。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-210">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="1bcf3-211">如果錨點刪除失敗，請將 Azure Spatial Anchors 新增至標示要刪除的錨點集合，然後在稍後的 EventTick 上再次嘗試。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-211">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="1bcf3-212">您的事件圖形藍圖現在看起來應該類似下列螢幕擷取畫面：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-212">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![用來處理雲端錨點的完整事件圖形的藍圖](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="1bcf3-214">尋找既有的錨點</span><span class="sxs-lookup"><span data-stu-id="1bcf3-214">Locating pre-existing anchors</span></span>

<span data-ttu-id="1bcf3-215">具有 Azure Spatial Anchors 服務的對等節點可以建立現有的錨點：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-215">Existing anchors can be created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="1bcf3-216">針對您想要偵測的錨點，取得 Azure Spatial Anchors 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-216">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="1bcf3-217">在先前的 Azure Spatial Anchors 工作階段中，可以為相同裝置所建立的錨點取得錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-217">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="1bcf3-218">其也可透過與 Azure Spatial Anchors 服務互動的對等裝置來建立及共用。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-218">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![使用取得 Azure 雲端識別碼函式的儲存 Azure Spatial Anchors 識別碼自訂事件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="1bcf3-220">將 **AzureSpatialAnchorsEvent** 元件新增至您的 Pawn 藍圖。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-220">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="1bcf3-221">此元件可讓您訂閱各種 Azure Spatial Anchors 事件，例如找到 Azure Spatial Anchors 時所呼叫的事件。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-221">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![在藍圖編輯器中開啟 BP_Pawn，且已開啟元件和詳細資料面板的螢幕擷取畫面](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="1bcf3-223">針對 [AzureSpatialAnchorsEvent] 元件訂閱 [ASAAnchor 找出的委派]。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-223">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="1bcf3-224">委派可讓應用程式知道何時找到與 Azure Spatial Anchors 帳戶相關聯的新錨點。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-224">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="1bcf3-225">透過事件回呼，使用 Azure Spatial Anchors 工作階段所建立對等節點的 Azure Spatial Anchors，預設不會建立 AR Pin。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-225">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="1bcf3-226">若要為偵測到的 Azure Spatial Anchors 建立 AR Pin，開發人員可以呼叫 [建立以 Azure Cloud Spatial Anchors 為主的 ARPin]。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-226">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![開始播放事件連線至 ASAAnchor 找出的委派的藍圖](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="1bcf3-228">若要使用 Azure Spatial Anchors 服務找出對等節點所建立的 Azure Spatial Anchors，應用程式必須建立 [Azure Spatial Anchors 監看員]：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-228">To locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="1bcf3-229">檢查 Azure Spatial Anchors 工作階段是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-229">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="1bcf3-230">建立 **AzureSpatialAnchorsLocateCriteria**。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-230">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="1bcf3-231">您可以指定各種位置參數，例如與使用者的距離或與另一個錨點的距離。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-231">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="1bcf3-232">在 **AzureSpatialAnchorsLocateCritieria** 中宣告您所尋找的 Azure Spatial Anchor 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-232">Declare the Azure Spatial Anchor identifier you're looking for in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="1bcf3-233">呼叫 [建立監看員]。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-233">Call **Create Watcher**.</span></span>

![啟動 Azure Spatial Anchors 監看員自訂事件的藍圖](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="1bcf3-235">應用程式現在會開始尋找 Azure Spatial Anchors 服務已知的 Azure Spatial Anchors，這表示使用者可以找出其對等節點所建立的 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-235">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="1bcf3-236">找出 Azure Spatial Anchor 之後，請呼叫 [停止監看員] 以停止 Azure Spatial Anchors 監看員並清除監看員資源。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-236">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![呼叫停止監看員函式的藍圖](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="1bcf3-238">您的最終事件圖形藍圖現在看起來應該類似下列螢幕擷取畫面：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-238">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![用來處理錨點委派事件的完整事件圖形的藍圖](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="1bcf3-240">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="1bcf3-240">Next Development Checkpoint</span></span>

<span data-ttu-id="1bcf3-241">依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-241">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="1bcf3-242">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-242">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="1bcf3-243">空間對應</span><span class="sxs-lookup"><span data-stu-id="1bcf3-243">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="1bcf3-244">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="1bcf3-244">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1bcf3-245">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="1bcf3-245">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="1bcf3-246">您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="1bcf3-246">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="1bcf3-247">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="1bcf3-247">Next steps</span></span>
* [<span data-ttu-id="1bcf3-248">本機空間錨點</span><span class="sxs-lookup"><span data-stu-id="1bcf3-248">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="1bcf3-249">空間錨點文件</span><span class="sxs-lookup"><span data-stu-id="1bcf3-249">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="1bcf3-250">空間錨點功能</span><span class="sxs-lookup"><span data-stu-id="1bcf3-250">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="1bcf3-251">有效的錨點體驗指導方針</span><span class="sxs-lookup"><span data-stu-id="1bcf3-251">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)