---
title: HoloLens (第1代) 和 Azure 302-電腦視覺
description: 完成本課程，以瞭解如何在混合現實應用程式中使用 Azure 電腦視覺，以在提供的影像中辨識視覺內容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學院，unity，教學課程，api，電腦視覺，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 119d83ec9fef97b4e4017b2226a9593404847a71
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730535"
---
# <a name="hololens-1st-gen-and-azure-302-computer-vision"></a><span data-ttu-id="2f98c-104">HoloLens (第1代) 和 Azure 302：電腦視覺</span><span class="sxs-lookup"><span data-stu-id="2f98c-104">HoloLens (1st gen) and Azure 302: Computer vision</span></span>

<br>

>[!NOTE]
><span data-ttu-id="2f98c-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="2f98c-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="2f98c-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="2f98c-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="2f98c-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="2f98c-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="2f98c-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="2f98c-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="2f98c-109">未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="2f98c-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="2f98c-110">當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。</span><span class="sxs-lookup"><span data-stu-id="2f98c-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

<span data-ttu-id="2f98c-111">在此課程中，您將瞭解如何在混合現實應用程式中使用 Azure 電腦視覺功能，以在提供的影像中辨識視覺內容。</span><span class="sxs-lookup"><span data-stu-id="2f98c-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="2f98c-112">辨識結果會顯示為描述性標記。</span><span class="sxs-lookup"><span data-stu-id="2f98c-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="2f98c-113">您可以使用此服務，而不需要訓練機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="2f98c-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="2f98c-114">如果您的實行需要訓練機器學習模型，請參閱 [MR 和 Azure 302b](mr-azure-302b.md)。</span><span class="sxs-lookup"><span data-stu-id="2f98c-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![實驗室結果](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="2f98c-116">Microsoft 電腦視覺是一組 Api，其設計目的是要為開發人員提供影像處理和分析 (，其中包含從雲端使用的最先進演算法) 的傳回信息。</span><span class="sxs-lookup"><span data-stu-id="2f98c-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="2f98c-117">開發人員上傳影像或影像 URL，而 Microsoft 電腦視覺 API 演算法會根據輸入使用者的輸入，分析視覺內容，然後傳回信息，包括識別影像的類型和品質、偵測人臉 (傳回其座標) 、標記或分類影像。</span><span class="sxs-lookup"><span data-stu-id="2f98c-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="2f98c-118">如需詳細資訊，請造訪 [Azure 電腦視覺 API 頁面](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。</span><span class="sxs-lookup"><span data-stu-id="2f98c-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="2f98c-119">完成本課程之後，您將會有混合現實 HoloLens 應用程式，它將能夠執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="2f98c-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="2f98c-120">使用點一下手勢，HoloLens 的攝影機將會捕獲映射。</span><span class="sxs-lookup"><span data-stu-id="2f98c-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="2f98c-121">映射將會傳送至 Azure 電腦視覺 API 服務。</span><span class="sxs-lookup"><span data-stu-id="2f98c-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="2f98c-122">辨識的物件將會列在位於 Unity 場景中的簡單 UI 群組中。</span><span class="sxs-lookup"><span data-stu-id="2f98c-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="2f98c-123">在您的應用程式中，您可以自行決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="2f98c-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="2f98c-124">本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="2f98c-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="2f98c-125">您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f98c-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="2f98c-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="2f98c-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2f98c-127">課程</span><span class="sxs-lookup"><span data-stu-id="2f98c-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="2f98c-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2f98c-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2f98c-129"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="2f98c-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="2f98c-130">MR 和 Azure 302：電腦視覺</span><span class="sxs-lookup"><span data-stu-id="2f98c-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="2f98c-131">✔️</span><span class="sxs-lookup"><span data-stu-id="2f98c-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2f98c-132">✔️</span><span class="sxs-lookup"><span data-stu-id="2f98c-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="2f98c-133">雖然本課程主要著重于 HoloLens，您也可以將本課程中所學到的內容套用到 Windows Mixed Reality 沉浸式 (VR) 耳機。</span><span class="sxs-lookup"><span data-stu-id="2f98c-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="2f98c-134">因為沉浸式 (VR) 耳機沒有可存取的攝影機，所以您需要有連接到電腦的外部攝影機。</span><span class="sxs-lookup"><span data-stu-id="2f98c-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="2f98c-135">當您依照課程的指示，您將會看到有關您可能需要採用以支援沉浸式 (VR) 耳機的任何變更的注意事項。</span><span class="sxs-lookup"><span data-stu-id="2f98c-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f98c-136">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="2f98c-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="2f98c-137">本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="2f98c-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="2f98c-138">另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="2f98c-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="2f98c-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span><span class="sxs-lookup"><span data-stu-id="2f98c-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="2f98c-140">本課程建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="2f98c-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="2f98c-141">開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)</span><span class="sxs-lookup"><span data-stu-id="2f98c-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="2f98c-142">啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="2f98c-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2f98c-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="2f98c-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2f98c-144">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="2f98c-144">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2f98c-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2f98c-145">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="2f98c-146">[Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="2f98c-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="2f98c-147">連接到您 PC (的攝影機，適用于沉浸式耳機開發) </span><span class="sxs-lookup"><span data-stu-id="2f98c-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="2f98c-148">適用于 Azure 安裝程式和電腦視覺 API 抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="2f98c-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="2f98c-149">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="2f98c-149">Before you start</span></span>

1.  <span data-ttu-id="2f98c-150">為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="2f98c-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="2f98c-151">設定及測試 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="2f98c-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="2f98c-152">如果您需要設定 HoloLens 的支援， [請務必造訪 HoloLens 安裝文章](/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="2f98c-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="2f98c-153">開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助針對每個使用者) 執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="2f98c-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="2f98c-154">如需有關校正的說明，請遵循此 [與 HoloLens 校正文章相關的連結](/hololens/hololens-calibration#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="2f98c-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="2f98c-155">如需有關感應器微調的說明，請依照此 [連結來進行「HoloLens 感應器微調」文章](/hololens/hololens-updates)。</span><span class="sxs-lookup"><span data-stu-id="2f98c-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="2f98c-156">第1章-Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="2f98c-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="2f98c-157">若要在 Azure 中使用 *電腦視覺 API* 服務，您必須將服務的實例設定為可供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="2f98c-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="2f98c-158">首先，登入 [Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="2f98c-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="2f98c-159">如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="2f98c-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="2f98c-160">如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="2f98c-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="2f98c-161">登入後，按一下左上角的 [ **新增** ]，並搜尋 *電腦視覺 API*，然後按一下 [ **輸入**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![在 Azure 中建立新的資源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="2f98c-163">在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。</span><span class="sxs-lookup"><span data-stu-id="2f98c-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="2f98c-164">新頁面將提供 *電腦視覺 API* 服務的描述。</span><span class="sxs-lookup"><span data-stu-id="2f98c-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="2f98c-165">在此頁面的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="2f98c-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![關於電腦視覺 api 服務](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="2f98c-167">當您按一下 [ **建立**] 之後：</span><span class="sxs-lookup"><span data-stu-id="2f98c-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="2f98c-168">為此服務實例插入您想要的 **名稱** 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="2f98c-169">選取 [訂用帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="2f98c-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="2f98c-170">選取適合您的 **定價層** ，如果這是您第一次建立 *電腦視覺 API* 服務，則應可使用名為 F0) 的免費層 (。</span><span class="sxs-lookup"><span data-stu-id="2f98c-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="2f98c-171">選擇資源群組，或建立一個新的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="2f98c-172">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="2f98c-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="2f98c-173">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="2f98c-174">如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="2f98c-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="2f98c-175">如果您要建立新的資源群組) ，請判斷資源群組 (的位置。</span><span class="sxs-lookup"><span data-stu-id="2f98c-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="2f98c-176">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="2f98c-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="2f98c-177">某些 Azure 資產僅適用于某些區域。</span><span class="sxs-lookup"><span data-stu-id="2f98c-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="2f98c-178">您也必須確認您已瞭解套用到此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="2f98c-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="2f98c-179">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-179">Click Create.</span></span>

        ![服務建立資訊](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="2f98c-181">當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="2f98c-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="2f98c-182">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="2f98c-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![查看新服務的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="2f98c-184">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="2f98c-184">Click on the notification to explore your new Service instance.</span></span> 

    ![選取 [移至資源] 按鈕。](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="2f98c-186">按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。</span><span class="sxs-lookup"><span data-stu-id="2f98c-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="2f98c-187">您將會進入新的電腦視覺 API 服務實例。</span><span class="sxs-lookup"><span data-stu-id="2f98c-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![新的電腦視覺 API 服務映射](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="2f98c-189">在本教學課程中，您的應用程式將需要呼叫您的服務，這是透過使用服務的訂用帳戶金鑰來完成。</span><span class="sxs-lookup"><span data-stu-id="2f98c-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="2f98c-190">從 [ *快速入門* ] 頁面，在您的 *電腦視覺 API* 服務中，流覽至第一個步驟、 *抓取您的金鑰*，然後按一下 [機 **碼** ] (您也可以按一下位於 [服務] 導覽功能表中，以按鍵圖示) 表示的藍色超連結鍵，以達成此目的。</span><span class="sxs-lookup"><span data-stu-id="2f98c-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="2f98c-191">這會顯示您的服務 *金鑰*。</span><span class="sxs-lookup"><span data-stu-id="2f98c-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="2f98c-192">複製其中一個顯示的金鑰，您稍後會在專案中使用。</span><span class="sxs-lookup"><span data-stu-id="2f98c-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="2f98c-193">返回到 [ *快速入門* ] 頁面，然後從該處提取您的端點。</span><span class="sxs-lookup"><span data-stu-id="2f98c-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="2f98c-194">請注意，您可能會有不同的不同，視您的區域而定 (如果是的話，您稍後將需要變更程式碼) 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="2f98c-195">取得此端點的複本以供稍後使用：</span><span class="sxs-lookup"><span data-stu-id="2f98c-195">Take a copy of this endpoint for use later:</span></span>

    ![新的電腦視覺 API 服務](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="2f98c-197">您可以在 [這裡](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)檢查各種不同的端點。</span><span class="sxs-lookup"><span data-stu-id="2f98c-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="2f98c-198">第2章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="2f98c-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="2f98c-199">以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="2f98c-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="2f98c-200">開啟 *Unity* ，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-200">Open *Unity* and click **New**.</span></span> 

    ![開始新的 Unity 專案。](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="2f98c-202">您現在將需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="2f98c-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="2f98c-203">插入 **MR_ComputerVision**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="2f98c-204">請確定專案類型設定為 **3d**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="2f98c-205">將 **位置** 設定為適合您 (記住，較接近根目錄的) 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="2f98c-206">然後，按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-206">Then, click **Create project**.</span></span>

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="2f98c-208">在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="2f98c-209">移至 [ **編輯] > 喜好** 設定，然後在新視窗中，流覽至 [ **外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="2f98c-210">將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="2f98c-211">關閉 [ **喜好** 設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="2f98c-211">Close the **Preferences** window.</span></span>

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="2f98c-213">接下來，移至 [檔案 **> 組建設定** ]，選取 [ **通用 Windows 平臺**]，然後按一下 [ **切換平臺** ] 按鈕以套用您的選取專案。</span><span class="sxs-lookup"><span data-stu-id="2f98c-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![[組建設定] 視窗，將平臺切換至 UWP。](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="2f98c-215">在檔案中仍 **> 組建設定** ，並確定：</span><span class="sxs-lookup"><span data-stu-id="2f98c-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="2f98c-216">**目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="2f98c-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="2f98c-217">針對沉浸式耳機，將 **目標裝置** 設為 *任何裝置*。</span><span class="sxs-lookup"><span data-stu-id="2f98c-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="2f98c-218">**組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="2f98c-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="2f98c-219">**SDK** 已設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="2f98c-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="2f98c-220">**Visual Studio 版本** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="2f98c-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="2f98c-221">**組建並執行** 設定為 **本機電腦**</span><span class="sxs-lookup"><span data-stu-id="2f98c-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="2f98c-222">儲存場景，並將其新增至組建。</span><span class="sxs-lookup"><span data-stu-id="2f98c-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="2f98c-223">若要這麼做，請選取 [ **新增開啟的場景**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="2f98c-224">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2f98c-224">A save window will appear.</span></span>
        
            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="2f98c-226">為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的腳本資料夾](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="2f98c-228">開啟新建立的 **場景** 資料夾，然後在 [ *檔案名*：文字] 欄位中，輸入 **MR_ComputerVisionScene**，然後按一下 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![提供新場景的名稱。](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="2f98c-230">請注意，您必須將 Unity 場景儲存在 [ *資產* ] 資料夾中，因為它們必須與 Unity 專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="2f98c-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="2f98c-231">建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。</span><span class="sxs-lookup"><span data-stu-id="2f98c-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="2f98c-232">[ *組建設定*] 中的其餘設定，現在應該保持為預設值。</span><span class="sxs-lookup"><span data-stu-id="2f98c-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="2f98c-233">在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。</span><span class="sxs-lookup"><span data-stu-id="2f98c-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟 [播放玩家設定]。](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="2f98c-235">在此面板中，需要驗證幾個設定：</span><span class="sxs-lookup"><span data-stu-id="2f98c-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="2f98c-236">在 [ **其他設定** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="2f98c-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="2f98c-237">**腳本執行階段版本** 應該是 **穩定** 的 ( .net 3.5 對等) 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="2f98c-238">**腳本後端** 應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="2f98c-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="2f98c-239">**API 相容性層級** 應為 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="2f98c-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="2f98c-241">在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：</span><span class="sxs-lookup"><span data-stu-id="2f98c-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="2f98c-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="2f98c-242">**InternetClient**</span></span>
        2. <span data-ttu-id="2f98c-243">**網路攝影機**</span><span class="sxs-lookup"><span data-stu-id="2f98c-243">**Webcam**</span></span>

            ![正在更新發行設定。](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="2f98c-245">在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 設定。](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="2f98c-247">回到 *組建設定*： _Unity c #_ 專案不再呈現灰色;勾選此方塊旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2f98c-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="2f98c-248">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="2f98c-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="2f98c-249">將場景和專案儲存 (檔 **> 儲存場景/檔案 > 儲存專案**) 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="2f98c-250">第3章-主要攝影機設定</span><span class="sxs-lookup"><span data-stu-id="2f98c-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f98c-251">如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意下載 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)，並將其匯入到您的專案中做為 [自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第5章](#chapter-5--create-the-resultslabel-class)。</span><span class="sxs-lookup"><span data-stu-id="2f98c-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="2f98c-252">在 [階層] *面板* 中，選取 [ **主要相機**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="2f98c-253">一旦選取之後，您就可以在 [偵測 *器] 面板* 中看到 **主要攝影機** 的所有元件。</span><span class="sxs-lookup"><span data-stu-id="2f98c-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="2f98c-254">**攝影機物件** 必須命名為 **主要攝影機** (請注意拼寫！ ) </span><span class="sxs-lookup"><span data-stu-id="2f98c-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="2f98c-255">主要攝影機 **標記** 必須設定為 **MainCamera** (注意拼寫！ ) </span><span class="sxs-lookup"><span data-stu-id="2f98c-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="2f98c-256">請確定 **轉換位置** 設定為 **0、0、0**</span><span class="sxs-lookup"><span data-stu-id="2f98c-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="2f98c-257">將 [ **清除旗標** ] 設定為 [ **純色** ] (針對沉浸式耳機) 略過此設定。</span><span class="sxs-lookup"><span data-stu-id="2f98c-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="2f98c-258">將相機元件的 **背景** 色彩設定為 **黑色、Alpha 0 (Hex 碼： #00000000)** (略過此項，以取得沉浸式耳機) 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![更新相機元件。](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="2f98c-260">接下來，您必須建立連接到 **主要攝影機** 的簡單「游標」物件，這可協助您在應用程式執行時定位影像分析輸出。</span><span class="sxs-lookup"><span data-stu-id="2f98c-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="2f98c-261">此游標會決定相機焦點的中心點。</span><span class="sxs-lookup"><span data-stu-id="2f98c-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="2f98c-262">若要建立資料指標：</span><span class="sxs-lookup"><span data-stu-id="2f98c-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="2f98c-263">在 [階層] *面板* 中，以滑鼠右鍵按一下 **主要攝影機**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="2f98c-264">在 [ **3D 物件**] 下，按一下 [ **球體**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![選取資料指標物件。](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="2f98c-266">將 **球體** 重新命名為 **游標** (按兩下游標物件，或按下 [F2] 鍵盤按鈕並選取) 的物件，並確定它是位於 **主要攝影機** 的子系。</span><span class="sxs-lookup"><span data-stu-id="2f98c-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="2f98c-267">在 [階層] *面板* 中，以滑鼠左鍵按一下 **游標**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="2f98c-268">選取資料指標之後，請在 [偵測器] *面板* 中調整下列變數：</span><span class="sxs-lookup"><span data-stu-id="2f98c-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="2f98c-269">將 *轉換位置* 設定為 **0、0、5**</span><span class="sxs-lookup"><span data-stu-id="2f98c-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="2f98c-270">將 *刻度* 設定為 **0.02、0.02、0.02**</span><span class="sxs-lookup"><span data-stu-id="2f98c-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![更新轉換位置和小數位數。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="2f98c-272">第4章-設定標籤系統</span><span class="sxs-lookup"><span data-stu-id="2f98c-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="2f98c-273">一旦您已使用 HoloLens 的相機來取得映射，該映射將會傳送至您的 *Azure 電腦視覺 API* 服務實例進行分析。</span><span class="sxs-lookup"><span data-stu-id="2f98c-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="2f98c-274">該分析的結果將會是已辨識的物件清單，稱為 **標記**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="2f98c-275">您將會使用標籤 (作為世界空間中的3D 文字) 在拍攝相片的位置顯示這些標記。</span><span class="sxs-lookup"><span data-stu-id="2f98c-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="2f98c-276">下列步驟將示範如何設定 **Label** 物件。</span><span class="sxs-lookup"><span data-stu-id="2f98c-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="2f98c-277">以滑鼠右鍵按一下 [階層] 面板中的任何位置 (位置並不重要) 在 [ **3D 物件**] 下，加入 **3d 文字**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="2f98c-278">將它命名為 **LabelText**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-278">Name it **LabelText**.</span></span>

    ![建立3D 文字物件。](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="2f98c-280">在 [階層] *面板* 中，以滑鼠左鍵按一下 **LabelText**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="2f98c-281">選取 **LabelText** 之後，在 [偵測 *器] 面板* 中調整下列變數：</span><span class="sxs-lookup"><span data-stu-id="2f98c-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="2f98c-282">將 **位置** 設定為 **0、0、0**</span><span class="sxs-lookup"><span data-stu-id="2f98c-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="2f98c-283">將 **刻度** 設定為 **0.01、0.01、0.01**</span><span class="sxs-lookup"><span data-stu-id="2f98c-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="2f98c-284">在元件 **文字網格** 中：</span><span class="sxs-lookup"><span data-stu-id="2f98c-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="2f98c-285">以 "..." 取代 **文字** 內的所有文字</span><span class="sxs-lookup"><span data-stu-id="2f98c-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="2f98c-286">將 **錨點** 設定為 **中間中心**</span><span class="sxs-lookup"><span data-stu-id="2f98c-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="2f98c-287">將 **對齊方式** 設定為 **置** 中</span><span class="sxs-lookup"><span data-stu-id="2f98c-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="2f98c-288">將索引標籤 **大小** 設定為 **4**</span><span class="sxs-lookup"><span data-stu-id="2f98c-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="2f98c-289">將 **字型大小** 設定為 **50**</span><span class="sxs-lookup"><span data-stu-id="2f98c-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="2f98c-290">將 **色彩** 設定為 **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="2f98c-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![文字元件](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="2f98c-292">將 **LabelText** 從 [階層]*面板* 拖曳至 [*專案] 面板* 中的 [資產]*資料夾* 內。</span><span class="sxs-lookup"><span data-stu-id="2f98c-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="2f98c-293">這會使 **LabelText** 成為預製專案，讓它可以在程式碼中具現化。</span><span class="sxs-lookup"><span data-stu-id="2f98c-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![建立 LabelText 物件的預製專案。](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="2f98c-295">您應該從 [階層]*面板* 中刪除 **LabelText** ，使其不會顯示在開啟的場景中。</span><span class="sxs-lookup"><span data-stu-id="2f98c-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="2f98c-296">因為它現在是預製專案，所以您會在 [資產] 資料夾中針對個別的實例呼叫，而不需要將其保留在場景中。</span><span class="sxs-lookup"><span data-stu-id="2f98c-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="2f98c-297">階層 *面板* 中的最後一個物件結構應如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="2f98c-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![階層面板的最終結構。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="2f98c-299">第5章-建立 ResultsLabel 類別</span><span class="sxs-lookup"><span data-stu-id="2f98c-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="2f98c-300">您需要建立的第一個腳本是 *ResultsLabel* 類別，負責下列各項：</span><span class="sxs-lookup"><span data-stu-id="2f98c-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="2f98c-301">在適當的世界空間中建立標籤（相對於相機的位置）。</span><span class="sxs-lookup"><span data-stu-id="2f98c-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="2f98c-302">顯示影像擺脫中的標記。</span><span class="sxs-lookup"><span data-stu-id="2f98c-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="2f98c-303">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="2f98c-303">To create this class:</span></span> 

1.  <span data-ttu-id="2f98c-304">在 [ *專案] 面板* 中按一下滑鼠右鍵，然後 **建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="2f98c-305">將資料夾命名為 **腳本**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-305">Name the folder **Scripts**.</span></span> 

    ![建立腳本資料夾。](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="2f98c-307">在 [ **腳本** ] 資料夾建立後，按兩下以開啟。</span><span class="sxs-lookup"><span data-stu-id="2f98c-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="2f98c-308">然後，在該資料夾中，以滑鼠右鍵按一下，然後選取 [ **建立] >** 然後選取 [ **c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="2f98c-309">將腳本命名為 *ResultsLabel*。</span><span class="sxs-lookup"><span data-stu-id="2f98c-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="2f98c-310">按兩下新的 *ResultsLabel* 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="2f98c-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="2f98c-311">在類別中，將下列程式碼插入 *ResultsLabel* 類別中：</span><span class="sxs-lookup"><span data-stu-id="2f98c-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="2f98c-312">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="2f98c-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="2f98c-313">返回 *Unity 編輯器* 中，按一下 [**腳本**] 資料夾中的 [ *ResultsLabel* ] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。</span><span class="sxs-lookup"><span data-stu-id="2f98c-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="2f98c-314">按一下 **主要攝影機** ，然後查看 [偵測 *器] 面板*。</span><span class="sxs-lookup"><span data-stu-id="2f98c-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="2f98c-315">您會發現，從您剛剛拖曳至相機的腳本中，有兩個欄位： **Cursor** 和 **Label 預製專案**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="2f98c-316">將名為 **cursor** 的物件從階層 *面板* 拖曳至名為 **cursor** 的位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="2f98c-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="2f98c-317">從 [*專案] 面板* 中的 [*資產] 資料夾*，將名為 **LabelText** 的物件拖曳至名為 **Label 預製專案** 的位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="2f98c-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![設定 Unity 中的參考目標。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="2f98c-319">第6章-建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="2f98c-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="2f98c-320">您即將建立的下一個類別是 *ImageCapture* 類別。</span><span class="sxs-lookup"><span data-stu-id="2f98c-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="2f98c-321">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="2f98c-321">This class is responsible for:</span></span>

-   <span data-ttu-id="2f98c-322">使用 HoloLens 攝影機來捕捉影像，並將它儲存在應用程式資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2f98c-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="2f98c-323">捕獲使用者的點擊手勢。</span><span class="sxs-lookup"><span data-stu-id="2f98c-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="2f98c-324">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="2f98c-324">To create this class:</span></span> 

1.  <span data-ttu-id="2f98c-325">移至您先前建立的 **腳本** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2f98c-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="2f98c-326">以滑鼠右鍵按一下資料夾內的， **建立 > c # 腳本**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="2f98c-327">呼叫腳本 *ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="2f98c-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="2f98c-328">按兩下新的 *ImageCapture* 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="2f98c-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="2f98c-329">將下列命名空間新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="2f98c-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="2f98c-330">然後，在 *ImageCapture* 類別內，于 *Start ()* 方法的上方新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="2f98c-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="2f98c-331">**TapsCount** 變數會儲存從使用者所捕獲的點擊手勢數目。</span><span class="sxs-lookup"><span data-stu-id="2f98c-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="2f98c-332">此數位用於所捕捉的映射命名。</span><span class="sxs-lookup"><span data-stu-id="2f98c-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="2f98c-333">現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2f98c-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="2f98c-334">當類別初始化時，就會呼叫這些內容：</span><span class="sxs-lookup"><span data-stu-id="2f98c-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="2f98c-335">執行將在點一下手勢發生時呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="2f98c-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="2f98c-336">*TapHandler ()* 方法會遞增從使用者所捕獲的點擊次數，並使用目前的資料指標位置來決定新標籤的位置。</span><span class="sxs-lookup"><span data-stu-id="2f98c-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="2f98c-337">然後，這個方法會呼叫 *ExecuteImageCaptureAndAnalysis ()* 方法來開始此應用程式的核心功能。</span><span class="sxs-lookup"><span data-stu-id="2f98c-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="2f98c-338">一旦捕獲並儲存映射之後，就會呼叫下列處理常式。</span><span class="sxs-lookup"><span data-stu-id="2f98c-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="2f98c-339">如果程式成功，則會將結果傳遞至 *VisionManager* (，但您尚未建立) 進行分析。</span><span class="sxs-lookup"><span data-stu-id="2f98c-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="2f98c-340">然後新增應用程式用來啟動映射捕獲進程的方法，並儲存映射。</span><span class="sxs-lookup"><span data-stu-id="2f98c-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="2f98c-341">此時您會注意到 *Unity 編輯器主控台面板* 中出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="2f98c-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="2f98c-342">這是因為程式碼會參考您將在下一章中建立的 *VisionManager* 類別。</span><span class="sxs-lookup"><span data-stu-id="2f98c-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="2f98c-343">第7章-呼叫 Azure 和影像分析</span><span class="sxs-lookup"><span data-stu-id="2f98c-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="2f98c-344">您需要建立的最後一個腳本是 *VisionManager* 類別。</span><span class="sxs-lookup"><span data-stu-id="2f98c-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="2f98c-345">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="2f98c-345">This class is responsible for:</span></span>

-   <span data-ttu-id="2f98c-346">載入以位元組陣列形式捕獲的最新映射。</span><span class="sxs-lookup"><span data-stu-id="2f98c-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="2f98c-347">將位元組陣列傳送至您的 *Azure 電腦視覺 API* 服務實例以進行分析。</span><span class="sxs-lookup"><span data-stu-id="2f98c-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="2f98c-348">以 JSON 字串的形式接收回應。</span><span class="sxs-lookup"><span data-stu-id="2f98c-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="2f98c-349">將回應還原序列化，並將產生的標記傳遞至 *ResultsLabel* 類別。</span><span class="sxs-lookup"><span data-stu-id="2f98c-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="2f98c-350">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="2f98c-350">To create this class:</span></span>

1.  <span data-ttu-id="2f98c-351">按兩下 [ **腳本** ] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="2f98c-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="2f98c-352">在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="2f98c-353">將腳本命名為 *VisionManager*。</span><span class="sxs-lookup"><span data-stu-id="2f98c-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="2f98c-354">按兩下新的腳本，以 Visual Studio 開啟。</span><span class="sxs-lookup"><span data-stu-id="2f98c-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="2f98c-355">在 *VisionManager* 類別的頂端，將命名空間更新為與下列相同：</span><span class="sxs-lookup"><span data-stu-id="2f98c-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="2f98c-356">在腳本頂端的 *VisionManager* 類別 *中*， (*開始 ()* 方法) 的上方，您現在需要建立兩個 *類別*，以代表來自 Azure 的已還原序列化 JSON 回應：</span><span class="sxs-lookup"><span data-stu-id="2f98c-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="2f98c-357">*TagData* 和 *AnalysedObject* 類別必須在宣告之前新增 *[system.string]* 屬性，才能使用 Unity 程式庫將其還原序列化。</span><span class="sxs-lookup"><span data-stu-id="2f98c-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="2f98c-358">在 VisionManager 類別中，您應該新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="2f98c-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="2f98c-359">請確定您將 **驗證金鑰** 插入 **authorizationKey** 變數中。</span><span class="sxs-lookup"><span data-stu-id="2f98c-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="2f98c-360">您將在本課程 [第1章](#chapter-1--the-azure-portal)的開頭注明您的 **驗證金鑰**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="2f98c-361">**VisionAnalysisEndpoint** 變數可能與此範例中指定的變數不同。</span><span class="sxs-lookup"><span data-stu-id="2f98c-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="2f98c-362">**美國西部** 絕對是指標對美國西部區域所建立的服務實例。</span><span class="sxs-lookup"><span data-stu-id="2f98c-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="2f98c-363">使用您的 [端點 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)來更新此值;以下是一些可能看起來像這樣的範例：</span><span class="sxs-lookup"><span data-stu-id="2f98c-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="2f98c-364">西歐： `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="2f98c-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="2f98c-365">東南亞： `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="2f98c-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="2f98c-366">澳大利亞東部： `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="2f98c-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="2f98c-367">現在需要新增喚醒的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2f98c-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="2f98c-368">接下來，新增協同程式 (，並在其底下的靜態資料流程方法) ，它會取得 ImageCapture 類別所之影像的分析結果。</span><span class="sxs-lookup"><span data-stu-id="2f98c-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="2f98c-369">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="2f98c-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="2f98c-370">返回 Unity 編輯器中，按一下 [**腳本**] 資料夾中的 [ *VisionManager* ] 和 [ *ImageCapture* ] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。</span><span class="sxs-lookup"><span data-stu-id="2f98c-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="2f98c-371">第8章-建立之前</span><span class="sxs-lookup"><span data-stu-id="2f98c-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="2f98c-372">若要執行應用程式的完整測試，您必須將它側載到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="2f98c-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="2f98c-373">在執行之前，請確定：</span><span class="sxs-lookup"><span data-stu-id="2f98c-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="2f98c-374">[第2章](#chapter-2--set-up-the-unity-project)中所述的所有設定都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="2f98c-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="2f98c-375">所有的腳本都會附加至 **主要攝影機** 物件。</span><span class="sxs-lookup"><span data-stu-id="2f98c-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="2f98c-376">*主要相機偵測器面板* 中的所有欄位都已正確指派。</span><span class="sxs-lookup"><span data-stu-id="2f98c-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="2f98c-377">請確定您將 **驗證金鑰** 插入 **authorizationKey** 變數中。</span><span class="sxs-lookup"><span data-stu-id="2f98c-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="2f98c-378">確定您也已在 *VisionManager* 腳本中檢查您的端點，且該端點符合 *您* 的區域 (本檔預設會使用 *美國西部*) 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="2f98c-379">第9章–建立 UWP 解決方案並側載應用程式</span><span class="sxs-lookup"><span data-stu-id="2f98c-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="2f98c-380">此專案的 Unity 區段所需的所有專案現在都已完成，因此您可以從 Unity 建立它。</span><span class="sxs-lookup"><span data-stu-id="2f98c-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="2f98c-381">流覽至 *組建* 配置  -  **檔案 > 組建設定 ...**</span><span class="sxs-lookup"><span data-stu-id="2f98c-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="2f98c-382">從 [ *組建設定* ] 視窗中，按一下 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-382">From the *Build Settings* window, click **Build**.</span></span>

    ![從 Unity 建立應用程式](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="2f98c-384">如果尚未這麼做，請勾選 **Unity c # 專案**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="2f98c-385">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-385">Click **Build**.</span></span> <span data-ttu-id="2f98c-386">Unity 將會啟動一個 *檔案總管* 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2f98c-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="2f98c-387">立即建立該資料夾，並命名為 *應用程式*。</span><span class="sxs-lookup"><span data-stu-id="2f98c-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="2f98c-388">然後選取 [ *應用程式* ] 資料夾，然後按 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="2f98c-389">Unity 將開始將您的專案建立到 *應用程式* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2f98c-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="2f98c-390">Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 *檔案總管* 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。</span><span class="sxs-lookup"><span data-stu-id="2f98c-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="2f98c-391">第10章–部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="2f98c-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="2f98c-392">若要在 HoloLens 上部署：</span><span class="sxs-lookup"><span data-stu-id="2f98c-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="2f98c-393">您將需要 HoloLens (的 IP 位址，才能進行遠端部署) ，並確保 HoloLens 處於 **開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="2f98c-394">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="2f98c-394">To do this:</span></span>

    1. <span data-ttu-id="2f98c-395">在設置 HoloLens 的同時，開啟 **設定**。</span><span class="sxs-lookup"><span data-stu-id="2f98c-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="2f98c-396">前往 **Network & Internet > Wi-Fi > Advanced Options**</span><span class="sxs-lookup"><span data-stu-id="2f98c-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="2f98c-397">記下 **IPv4** 位址。</span><span class="sxs-lookup"><span data-stu-id="2f98c-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="2f98c-398">接下來，流覽回到 [ **設定**]，然後 **更新開發人員 & 的安全性 >**</span><span class="sxs-lookup"><span data-stu-id="2f98c-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="2f98c-399">設定 [開發人員模式]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="2f98c-400">流覽至您的新 Unity 組建 (*應用程式* 資料夾) ，然後以 *Visual Studio* 開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="2f98c-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="2f98c-401">在 [方案設定] 中選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="2f98c-402">在解決方案平臺中，選取 [ **x86**]、[ **遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="2f98c-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![從 Visual Studio 部署方案。](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="2f98c-404">移至 [ **組建] 功能表** ，然後按一下 [ **部署方案**]，將應用程式側載至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="2f98c-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="2f98c-405">您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中，準備好可供啟動！</span><span class="sxs-lookup"><span data-stu-id="2f98c-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="2f98c-406">若要部署到沉浸式耳機，請將 **解決方案平臺\*\*\*\*設定為 [** *本機電腦*]，並將 [設定] 設定為 [以 *x86* 作為 **平臺**] 來進行 *Debug*。</span><span class="sxs-lookup"><span data-stu-id="2f98c-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="2f98c-407">然後使用 [ **組建] 功能表** 選取 [ *部署方案*]，部署到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="2f98c-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="2f98c-408">您完成的電腦視覺 API 應用程式</span><span class="sxs-lookup"><span data-stu-id="2f98c-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="2f98c-409">恭喜，您已建立混合的現實應用程式，利用 Azure 電腦視覺 API 來辨識真實世界物件，並顯示已看到內容的可信度。</span><span class="sxs-lookup"><span data-stu-id="2f98c-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![實驗室結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="2f98c-411">額外練習</span><span class="sxs-lookup"><span data-stu-id="2f98c-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="2f98c-412">練習1</span><span class="sxs-lookup"><span data-stu-id="2f98c-412">Exercise 1</span></span>

<span data-ttu-id="2f98c-413">就像您在 *VisionManager*) 內使用的 *端點* 中使用 *標記* 參數 (為證明，請擴充應用程式以偵測其他資訊;看看您在 [這裡](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)可以存取的其他參數。</span><span class="sxs-lookup"><span data-stu-id="2f98c-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="2f98c-414">練習2</span><span class="sxs-lookup"><span data-stu-id="2f98c-414">Exercise 2</span></span>

<span data-ttu-id="2f98c-415">以更有對話、更容易閱讀的方式來顯示傳回的 Azure 資料，或許隱藏了數位。</span><span class="sxs-lookup"><span data-stu-id="2f98c-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="2f98c-416">如同 bot 可能對使用者說話。</span><span class="sxs-lookup"><span data-stu-id="2f98c-416">As though a bot might be speaking to the user.</span></span>