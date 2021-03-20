---
title: HoloLens (第1代) 和 Azure 302b-自訂視覺
description: 完成本課程，以瞭解如何訓練機器學習模型，然後使用定型的模型來辨識混合現實應用程式中類似的物件。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure，mixed reality，學院，unity，教學課程，api，自訂視覺，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 97fd0ae72401b67a83752cb2cf6799fa2b1ccc0c
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730525"
---
# <a name="hololens-1st-gen-and-azure-302b-custom-vision"></a><span data-ttu-id="ed4e5-104">HoloLens (第1代) 和 Azure 302b：自訂視覺</span><span class="sxs-lookup"><span data-stu-id="ed4e5-104">HoloLens (1st gen) and Azure 302b: Custom vision</span></span>

<br>

>[!NOTE]
><span data-ttu-id="ed4e5-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ed4e5-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ed4e5-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ed4e5-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ed4e5-109">未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ed4e5-110">當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>


<span data-ttu-id="ed4e5-111">在此課程中，您將瞭解如何在混合現實應用程式中使用 Azure 自訂視覺功能，以在提供的影像中辨識自訂視覺內容。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="ed4e5-112">這種服務可讓您使用物件影像來定型機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="ed4e5-113">然後，您將使用定型的模型來辨識類似的物件（Microsoft HoloLens 的相機捕捉，或連接到您的電腦以取得沉浸式 (VR) 耳機的相機）所提供的物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![課程結果](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="ed4e5-115">Azure 自訂視覺是一項 Microsoft 認知服務，可讓開發人員建立自訂影像分類器。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="ed4e5-116">這些分類器接著可以與新影像搭配使用，以辨識或分類該新影像內的物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="ed4e5-117">此服務提供簡單、容易使用的線上入口網站，以簡化程式。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="ed4e5-118">如需詳細資訊，請造訪 [Azure 自訂視覺服務頁面](/azure/cognitive-services/custom-vision-service/home)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-118">For more information, visit the [Azure Custom Vision Service page](/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="ed4e5-119">完成本課程之後，您將會有一個混合的現實應用程式，可以在兩種模式下運作：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="ed4e5-120">**分析模式**：以手動方式設定自訂視覺服務，方法是上傳影像、建立標記，以及將服務定型以辨識不同的物件 (在此案例中為滑鼠和鍵盤) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="ed4e5-121">然後，您將建立 HoloLens 應用程式，以使用相機來捕捉影像，並嘗試辨識真實世界中的那些物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="ed4e5-122">**定型模式**：您將會執行程式碼，以在您的應用程式中啟用「定型模式」。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="ed4e5-123">定型模式可讓您使用 HoloLens 的相機來捕捉影像、將捕獲的影像上傳至服務，以及定型自訂視覺模型。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="ed4e5-124">本課程將告訴您如何將自訂視覺服務的結果取得 Unity 型範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="ed4e5-125">您必須將這些概念套用至您可能正在建立的自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="ed4e5-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="ed4e5-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ed4e5-127">課程</span><span class="sxs-lookup"><span data-stu-id="ed4e5-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ed4e5-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ed4e5-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ed4e5-129"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="ed4e5-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ed4e5-130">MR 和 Azure 302b：自訂視覺</span><span class="sxs-lookup"><span data-stu-id="ed4e5-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="ed4e5-131">✔️</span><span class="sxs-lookup"><span data-stu-id="ed4e5-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ed4e5-132">✔️</span><span class="sxs-lookup"><span data-stu-id="ed4e5-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ed4e5-133">雖然本課程主要著重于 HoloLens，您也可以將本課程中所學到的內容套用到 Windows Mixed Reality 沉浸式 (VR) 耳機。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="ed4e5-134">因為沉浸式 (VR) 耳機沒有可存取的攝影機，所以您需要有連接到電腦的外部攝影機。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="ed4e5-135">當您依照課程的指示，您將會看到有關您可能需要採用以支援沉浸式 (VR) 耳機的任何變更的注意事項。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ed4e5-136">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ed4e5-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ed4e5-137">本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ed4e5-138">另外也請注意，本檔中的必要條件和書面指示，代表在撰寫 (2018 年7月) 時已經過測試和驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="ed4e5-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span><span class="sxs-lookup"><span data-stu-id="ed4e5-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="ed4e5-140">本課程建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ed4e5-141">開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)</span><span class="sxs-lookup"><span data-stu-id="ed4e5-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ed4e5-142">啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="ed4e5-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ed4e5-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="ed4e5-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ed4e5-144">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="ed4e5-144">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ed4e5-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ed4e5-145">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="ed4e5-146">[Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="ed4e5-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="ed4e5-147">連接到您 PC (的攝影機，適用于沉浸式耳機開發) </span><span class="sxs-lookup"><span data-stu-id="ed4e5-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="ed4e5-148">適用于 Azure 安裝程式和自訂視覺 API 抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="ed4e5-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="ed4e5-149">一系列至少五 (5) 映射 (10 (10) 建議) 服務辨識的每個物件自訂視覺。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="ed4e5-150">如果您想要的話，可以使用 [本課程中已提供的影像 (電腦滑鼠和鍵盤) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ed4e5-151">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="ed4e5-151">Before you start</span></span>

1.  <span data-ttu-id="ed4e5-152">為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="ed4e5-153">設定及測試 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="ed4e5-154">如果您需要設定 HoloLens 的支援， [請務必造訪 HoloLens 安裝文章](/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="ed4e5-155">開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助針對每個使用者) 執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="ed4e5-156">如需有關校正的說明，請遵循此 [與 HoloLens 校正文章相關的連結](/hololens/hololens-calibration#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="ed4e5-157">如需有關感應器微調的說明，請依照此 [連結來進行「HoloLens 感應器微調」文章](/hololens/hololens-updates)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="ed4e5-158">第1章-自訂視覺 Service 入口網站</span><span class="sxs-lookup"><span data-stu-id="ed4e5-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="ed4e5-159">若要在 Azure 中使用 *自訂視覺服務* ，您必須將服務的實例設定為可供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="ed4e5-160">首先， [流覽至 *自訂視覺服務* 主頁面](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="ed4e5-161">按一下 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-161">Click on the **Get Started** button.</span></span>

    ![開始使用自訂視覺服務](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="ed4e5-163">登入 *自訂視覺服務* 入口網站。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-163">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![登入入口網站](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="ed4e5-165">如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-165">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ed4e5-166">如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-166">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="ed4e5-167">當您第一次登入之後，系統會提示您提供 *服務條款* 面板。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-167">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="ed4e5-168">按一下核取方塊以同意條款。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-168">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="ed4e5-169">然後按一下 [ **我同意**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-169">Then click on **I agree**.</span></span>

    ![服務條款](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="ed4e5-171">同意條款之後，您將會流覽至入口網站的 [ *專案* ] 區段。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-171">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="ed4e5-172">按一下 [ **新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-172">Click on **New Project**.</span></span>

    ![建立新專案](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="ed4e5-174">右側將會出現一個索引標籤，提示您指定專案的某些欄位。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-174">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="ed4e5-175">插入專案的 *名稱* 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-175">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="ed4e5-176">為您的專案插入 *描述* (*選擇性*) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-176">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="ed4e5-177">選擇資源群組，或建立一個新的 *資源群組* 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-177">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="ed4e5-178">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-178">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ed4e5-179">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-179">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="ed4e5-180">將 *專案類型* 設定為 **分類**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-180">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="ed4e5-181">將 *網域* 設定為 **[一般**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-181">Set the *Domains* as **General**.</span></span>

        ![設定網域](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="ed4e5-183">如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-183">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="ed4e5-184">完成之後，按一下 [ **建立專案**]，系統會將您重新導向至自訂視覺服務的 [專案] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-184">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="ed4e5-185">第2章-訓練自訂視覺專案</span><span class="sxs-lookup"><span data-stu-id="ed4e5-185">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="ed4e5-186">在自訂視覺入口網站中，您的主要目標是將您的專案定型，以辨識影像中的特定物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-186">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="ed4e5-187">您需要至少五個 (5) 的映射，但最好是針對您希望應用程式辨識的每個物件都有10個 (10) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-187">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="ed4e5-188">[您可以使用本課程所提供的影像 (電腦滑鼠和鍵盤) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-188">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="ed4e5-189">定型您的自訂視覺服務專案：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-189">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="ed4e5-190">按一下 [ **+** 標記] 旁的 **按鈕。**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-190">Click on the **+** button next to **Tags.**</span></span>

    ![新增標籤](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="ed4e5-192">新增您想要辨識的物件 **名稱** 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-192">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="ed4e5-193">按一下 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-193">Click on **Save**.</span></span>

    ![新增物件名稱並儲存](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="ed4e5-195">您會注意到 **您的標籤已新增** (您可能需要重載頁面，才能讓它顯示) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-195">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="ed4e5-196">在新標記旁邊按一下核取方塊（如果尚未核取）。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-196">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![啟用新標記](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="ed4e5-198">按一下頁面中央的 [ **加入影像** ]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-198">Click on **Add Images** in the center of the page.</span></span>

    ![新增影像](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="ed4e5-200">按一下 **[流覽本機檔案]**，然後搜尋並選取您想要上傳的影像，其最少為五 (5) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-200">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="ed4e5-201">請記住，這些影像都應該包含您正在定型的物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-201">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ed4e5-202">您可以一次選取多個影像，以便上傳。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-202">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="ed4e5-203">當您可以在索引標籤中看到影像之後，請在 [ **我的標記** ] 方塊中選取適當的標籤。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-203">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![選取標記](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="ed4e5-205">按一下 **[上傳** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-205">Click on **Upload files**.</span></span> <span data-ttu-id="ed4e5-206">檔案將會開始上傳。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-206">The files will begin uploading.</span></span> <span data-ttu-id="ed4e5-207">確認上傳之後，請按一下 [ **完成**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-207">Once you have confirmation of the upload, click **Done**.</span></span>

    ![上傳檔案](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="ed4e5-209">重複相同的程式，建立名為 **鍵盤** 的新 **標記**，並為其上傳適當的相片。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-209">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="ed4e5-210">當您建立新標籤之後，請務必 **取消** 核取 *滑鼠* ，以顯示 [新增 *影像* ] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-210">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="ed4e5-211">當您設定這兩個標籤之後，請按一下 [ **定型**]，第一個定型反復專案將會開始建立。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-211">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![啟用定型反復專案](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="ed4e5-213">一旦建立之後，您就可以看到兩個按鈕，稱為「 **建立預設值** 和 **預測 URL**」。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-213">Once it's built, you'll be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="ed4e5-214">先按一下 [ **設為預設值** ]，然後按一下 [ **預測 URL**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-214">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![製作預設值和預測 URL](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="ed4e5-216">由此提供的端點 URL 會設定為已標示為預設值的任何 *反復* 專案。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-216">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="ed4e5-217">因此，如果您稍後建立新的 *反復* 專案，並將其更新為預設值，您就不需要變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-217">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="ed4e5-218">當您按一下 [ *預測 URL*] 之後，請開啟 [ *記事本*]，然後複製並貼上 **URL** 和 **預測金鑰**，以便稍後在程式碼中需要時加以取出。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-218">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![複製並貼上 URL 和 Prediction-Key](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="ed4e5-220">按一下畫面右上方的 [ **齒輪** ]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-220">Click on the **Cog** at the top right of the screen.</span></span>

    ![按一下 [齒輪] 圖示以開啟 [設定]](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="ed4e5-222">將 **定型金鑰** 複製並貼到 *記事本* 中，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-222">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![複製訓練金鑰](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="ed4e5-224">此外，也請複製您的 **專案 Id**，並將其貼到您的 *記事本* 檔案中，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-224">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![複製專案識別碼](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="ed4e5-226">第3章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="ed4e5-226">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="ed4e5-227">以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-227">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ed4e5-228">開啟 *Unity* ，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-228">Open *Unity* and click **New**.</span></span>

    ![建立新的 Unity 專案](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="ed4e5-230">您現在將需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-230">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="ed4e5-231">插入 **AzureCustomVision。**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-231">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="ed4e5-232">請確定專案範本已設定為 **3d**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-232">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="ed4e5-233">將 **位置** 設定為適合您 (記住，較接近根目錄的) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-233">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ed4e5-234">然後，按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-234">Then, click **Create project**.</span></span>

    ![設定專案設定](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="ed4e5-236">在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-236">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ed4e5-237">移至 [ **編輯*  >  *喜好** 設定]，然後在新視窗中，流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-237">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ed4e5-238">將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-238">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ed4e5-239">關閉 [ **喜好** 設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-239">Close the **Preferences** window.</span></span>

    ![設定外部工具](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="ed4e5-241">接下來，移至 [檔案 **> 組建設定** ]，選取 [ **通用 Windows 平臺**]，然後按一下 [ **切換平臺** ] 按鈕以套用您的選取專案。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-241">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![<span data-ttu-id="ed4e5-242">設定組建設定</span><span class="sxs-lookup"><span data-stu-id="ed4e5-242">Configure build settings</span></span> ](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="ed4e5-243">在檔案中仍 **> 組建設定** ，並確定：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-243">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="ed4e5-244">**目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-244">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="ed4e5-245">針對沉浸式耳機，將 **目標裝置** 設為 *任何裝置*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-245">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="ed4e5-246">**組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-246">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="ed4e5-247">**SDK** 已設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-247">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="ed4e5-248">**Visual Studio 版本** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-248">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="ed4e5-249">**組建並執行** 設定為 **本機電腦**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-249">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="ed4e5-250">儲存場景，並將其新增至組建。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-250">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="ed4e5-251">若要這麼做，請選取 [ **新增開啟的場景**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-251">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ed4e5-252">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-252">A save window will appear.</span></span>

            ![將開啟的場景新增至組建清單](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="ed4e5-254">為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-254">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的場景資料夾](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="ed4e5-256">開啟新建立的 **場景** 資料夾，然後在 [ *檔案名：* 文字] 欄位中輸入 **CustomVisionScene**，然後按一下 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-256">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![命名新的場景檔案](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="ed4e5-258">請注意，您必須將 Unity 場景儲存在 [ *資產* ] 資料夾中，因為它們必須與 Unity 專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-258">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="ed4e5-259">建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-259">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="ed4e5-260">[ *組建設定*] 中的其餘設定，現在應該保持為預設值。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-260">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![預設組建設定](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="ed4e5-262">在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-262">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="ed4e5-263">在此面板中，需要驗證幾個設定：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-263">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ed4e5-264">在 [ **其他設定** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-264">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ed4e5-265">**腳本執行階段版本** 應該是 **實驗 ( .Net 4.6 對等)**，這會觸發重新開機編輯器的需求。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-265">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="ed4e5-266">**腳本後端** 應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-266">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="ed4e5-267">**API 相容性層級** 應為 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-267">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![設定 API compantiblity](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="ed4e5-269">在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-269">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="ed4e5-270">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-270">**InternetClient**</span></span>

        2.  <span data-ttu-id="ed4e5-271">**網路攝影機**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-271">**Webcam**</span></span>

        3. <span data-ttu-id="ed4e5-272">**麥克風**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-272">**Microphone**</span></span>

        ![設定發佈設定](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="ed4e5-274">在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-274">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![設定 XR 設定](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="ed4e5-276">回到 *組建設定*： *Unity C \# 專案* 不再呈現灰色; 勾選此方塊旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-276">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="ed4e5-277">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-277">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="ed4e5-278">將場景和專案儲存 (檔 **> 儲存場景/檔案 > 儲存專案**) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-278">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="ed4e5-279">第4章-匯入 Unity 中的 Newtonsoft DLL</span><span class="sxs-lookup"><span data-stu-id="ed4e5-279">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed4e5-280">如果您想要跳過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，您可以下載此 [Azure-MR-302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)，將其匯入到您的專案中做為 [**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第6章](#chapter-6---create-the-customvisionanalyser-class)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-280">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="ed4e5-281">本課程需要使用 **Newtonsoft** 程式庫，您可以將其以 DLL 的形式新增至您的資產。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-281">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="ed4e5-282">您可以從此 [連結下載包含此程式庫](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)的套件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-282">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="ed4e5-283">若要將 Newtonsoft 程式庫匯入您的專案，請使用本課程隨附的 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-283">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="ed4e5-284">使用 [ **資產* 匯  >  *入\*\*封裝*  >  *自訂\*\*套件** ] 功能表選項，將 *unitypackage* 新增至 Unity。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-284">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="ed4e5-285">在彈出的 [匯 **入 Unity 套件** ] 方塊中，確定已選取 [ (] 下的所有專案，並包含) **外掛程式** 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-285">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![匯入所有封裝專案](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="ed4e5-287">按一下 [匯 **入** ] 按鈕，將專案新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-287">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="ed4e5-288">移至專案視圖中 [**外掛程式**] 下的 [ **Newtonsoft** ] 資料夾，然後選取 [*在外掛程式上Newtonsoft.Js*]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-288">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![選取 Newtonsoft 外掛程式](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="ed4e5-290">選取 *Newtonsoft.Json 外掛程式* 時，請確定已 **取消** 核取 **任何平臺**，然後確定 **WSAPlayer** **也未** 核取，然後 **按一下 [** 套用]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-290">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="ed4e5-291">這只是為了確認檔案已正確設定。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-291">This is just to confirm that the files are configured correctly.</span></span>

    ![設定 Newtonsoft 外掛程式](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="ed4e5-293">標記這些外掛程式會將它們設定為只在 Unity 編輯器中使用。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-293">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="ed4e5-294">在 [WSA] 資料夾中有一組不同的集合，會在從 Unity 匯出專案之後使用。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-294">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="ed4e5-295">接下來，您需要在 **Newtonsoft** 資料夾內開啟 [ **WSA** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-295">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="ed4e5-296">您會看到您剛剛設定的相同檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-296">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="ed4e5-297">選取檔案，然後在偵測器中，確定</span><span class="sxs-lookup"><span data-stu-id="ed4e5-297">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="ed4e5-298">**未核** 取 **任何平臺**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-298">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="ed4e5-299">**只\*\*\*\*檢查** **WSAPlayer**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-299">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="ed4e5-300">不 **檢查\*\*\*\*進程**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-300">**Dont process** is **checked**</span></span>

    ![設定 Newtonsoft 外掛程式平臺設定](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="ed4e5-302">第5章-攝影機設定</span><span class="sxs-lookup"><span data-stu-id="ed4e5-302">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="ed4e5-303">在 [階層] 面板中，選取 [ *主要相機*]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-303">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="ed4e5-304">一旦選取之後，您就可以在 [偵測 *器] 面板* 中看到 *主要攝影機* 的所有元件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-304">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="ed4e5-305">*攝影機* 物件必須命名為 **主要攝影機** (請注意拼寫！ ) </span><span class="sxs-lookup"><span data-stu-id="ed4e5-305">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="ed4e5-306">主要攝影機 **標記** 必須設定為 **MainCamera** (注意拼寫！ ) </span><span class="sxs-lookup"><span data-stu-id="ed4e5-306">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="ed4e5-307">請確定 **轉換位置** 設定為 **0、0、0**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-307">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="ed4e5-308">將 [ **清除旗標** ] 設定為 [ **純色** ] (針對沉浸式耳機) 略過此設定。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-308">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="ed4e5-309">將相機元件的 **背景** 色彩設定為 **黑色、Alpha 0 (Hex 碼： #00000000)** (略過此項，以取得沉浸式耳機) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-309">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![設定相機元件屬性](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="ed4e5-311">第6章-建立 CustomVisionAnalyser 類別。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-311">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="ed4e5-312">至此，您已準備好撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-312">At this point you are ready to write some code.</span></span>

<span data-ttu-id="ed4e5-313">您將開始使用 *CustomVisionAnalyser* 類別。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-313">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="ed4e5-314">下列程式碼中所示的 **自訂視覺服務** 呼叫會使用 **自訂視覺 REST API** 進行。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-314">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="ed4e5-315">透過這種方式，您將瞭解如何實行和使用此 API (有助於瞭解如何在您自己的) 上執行類似的操作。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-315">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="ed4e5-316">請注意，Microsoft 提供的 **自訂視覺服務 SDK** 也可以用來對服務進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-316">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="ed4e5-317">如需詳細資訊，請造訪 [自訂視覺 SERVICE SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) 文章。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-317">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="ed4e5-318">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-318">This class is responsible for:</span></span>

-   <span data-ttu-id="ed4e5-319">載入以位元組陣列形式捕獲的最新映射。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-319">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="ed4e5-320">將位元組陣列傳送至您的 Azure *自訂視覺服務* 實例以進行分析。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-320">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="ed4e5-321">以 JSON 字串的形式接收回應。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-321">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="ed4e5-322">將回應還原序列化，並將產生的 *預測* 傳遞給 *SceneOrganiser* 類別，這將會負責顯示回應的方式。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-322">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="ed4e5-323">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-323">To create this class:</span></span>

1.  <span data-ttu-id="ed4e5-324">以滑鼠右鍵按一下位於 [*專案] 面板* 中的 [*資產] 資料夾*，然後按一下 [**建立] > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-324">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="ed4e5-325">呼叫資料夾 **腳本**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-325">Call the folder **Scripts**.</span></span>

    ![建立腳本資料夾](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="ed4e5-327">按兩下剛才建立的資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-327">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="ed4e5-328">在資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-328">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ed4e5-329">將腳本命名為 *CustomVisionAnalyser*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-329">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="ed4e5-330">按兩下新的 *CustomVisionAnalyser* 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-330">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="ed4e5-331">更新檔案頂端的命名空間，以符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-331">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="ed4e5-332">在 *CustomVisionAnalyser* 類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-332">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="ed4e5-333">請務必將您的 **預測金鑰** 插入至 **predictionKey** 變數，並將 **預測端點** 插入至 **predictionEndpoint** 變數。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-333">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="ed4e5-334">您稍早在課程中將這些複製到 [ *記事本* ]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-334">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="ed4e5-335">現在需要新增 **喚醒 ()** 的程式碼，以初始化執行個體變數：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-335">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="ed4e5-336">刪除方法 **開始 ()** 和 **更新 ()**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-336">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="ed4e5-337">接下來，新增協同程式 (，並在其下方加入靜態 **GetImageAsByteArray ()** 方法) ，它會取得 *ImageCapture* 類別所捕獲之影像的分析結果。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-337">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ed4e5-338">在 [ **AnalyseImageCapture** ] 協同程式中，您還必須呼叫 *SceneOrganiser* 類別。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-338">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="ed4e5-339">因此，請 **暫時將這些行** 加上批註。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-339">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="ed4e5-340">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-340">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="ed4e5-341">第7章-建立 CustomVisionObjects 類別</span><span class="sxs-lookup"><span data-stu-id="ed4e5-341">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="ed4e5-342">您將建立的類別現在是 *CustomVisionObjects* 類別。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-342">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="ed4e5-343">此腳本包含其他類別用來序列化和還原序列化對 *自訂視覺服務* 進行之呼叫的物件數。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-343">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="ed4e5-344">請務必記下自訂視覺服務提供給您的端點，因為下列 JSON 結構已設定為可搭配 [*自訂視覺預測*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)v2.0 使用。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-344">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="ed4e5-345">如果您有不同的版本，您可能需要更新下列結構。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-345">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="ed4e5-346">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-346">To create this class:</span></span>

1.  <span data-ttu-id="ed4e5-347">在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-347">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ed4e5-348">呼叫腳本 *CustomVisionObjects*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-348">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="ed4e5-349">按兩下新的 **CustomVisionObjects** 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-349">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="ed4e5-350">將下列命名空間新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-350">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="ed4e5-351">刪除 [**開始 ()** ]，並更新 *CustomVisionObjects* 類別內的 **()** 方法;這個類別現在應該是空的。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-351">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="ed4e5-352">將下列類別新增至 *CustomVisionObjects* 類別 **之外**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-352">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="ed4e5-353">*Newtonsoft* 程式庫會使用這些物件，將回應資料序列化和還原序列化：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-353">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="ed4e5-354">第8章-建立 VoiceRecognizer 類別</span><span class="sxs-lookup"><span data-stu-id="ed4e5-354">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="ed4e5-355">此類別會辨識使用者的語音輸入。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-355">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="ed4e5-356">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-356">To create this class:</span></span>

1.  <span data-ttu-id="ed4e5-357">在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-357">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ed4e5-358">呼叫腳本 *VoiceRecognizer*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-358">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="ed4e5-359">按兩下新的 **VoiceRecognizer** 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-359">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="ed4e5-360">在 *VoiceRecognizer* 類別的上方新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-360">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="ed4e5-361">然後，在 *VoiceRecognizer* 類別內，于 *Start ()* 方法的上方新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-361">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="ed4e5-362">新增 **喚醒的 ()** 並 **啟動 ()** 方法，後者將會設定將標籤與影像建立關聯時要辨識的使用者 *關鍵字* ：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-362">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="ed4e5-363">刪除 **更新 ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-363">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="ed4e5-364">新增下列處理常式，每次辨識語音輸入時就會呼叫此處理程式：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-364">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="ed4e5-365">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-365">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="ed4e5-366">不要擔心可能出現錯誤的程式碼，因為您很快就會提供進一步的類別，這將會修正這些問題。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-366">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="ed4e5-367">第9章-建立 CustomVisionTrainer 類別</span><span class="sxs-lookup"><span data-stu-id="ed4e5-367">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="ed4e5-368">這個類別會建立一連串的 web 呼叫來訓練 *自訂視覺服務*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-368">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="ed4e5-369">在程式碼上方會詳細說明每個呼叫。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-369">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="ed4e5-370">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-370">To create this class:</span></span>

1.  <span data-ttu-id="ed4e5-371">在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-371">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ed4e5-372">呼叫腳本 *CustomVisionTrainer*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-372">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="ed4e5-373">按兩下新的 *CustomVisionTrainer* 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-373">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="ed4e5-374">在 *CustomVisionTrainer* 類別的上方新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-374">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="ed4e5-375">然後，在 *CustomVisionTrainer* 類別內，于 **Start ()** 方法的上方新增下列變數。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-375">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="ed4e5-376">此處所使用的定型 URL 是在 *自訂視覺訓練 1.2* 檔中提供，其結構如下： https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="ed4e5-376">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="ed4e5-377">如需詳細資訊，請流覽 [*自訂視覺訓練/1.2 參考 API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-377">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="ed4e5-378">請務必記下自訂視覺服務為您提供定型模式的端點，因為在 **CustomVisionObjects** 類別內使用 (的 JSON 結構) 已設定為使用 [*自訂視覺定型 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)版。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-378">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="ed4e5-379">如果您有不同的版本，您可能需要更新 *物件* 結構。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-379">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="ed4e5-380">請確定您將 **服務金鑰** 新增 (定型金鑰) 值和 **專案識別碼** 值（您先前記下的值）;這些是您稍 [早在課程中從入口網站收集的值 (第2章：步驟 10)](#chapter-2---training-your-custom-vision-project)。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-380">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-project).</span></span>

5.  <span data-ttu-id="ed4e5-381">新增下列 **開始 ()** 和 **喚醒的 ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-381">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="ed4e5-382">這些方法會在初始化時呼叫，並包含設定 UI 的呼叫：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-382">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="ed4e5-383">刪除 **更新 ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-383">Delete the **Update()** method.</span></span> <span data-ttu-id="ed4e5-384">此類別將不需要它。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-384">This class will not need it.</span></span>

7.  <span data-ttu-id="ed4e5-385">新增 **RequestTagSelection ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-385">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="ed4e5-386">當映射已被捕獲並儲存在裝置中，並且現在已準備好提交給 *自訂視覺服務* 來定型時，就會先呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-386">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="ed4e5-387">這個方法會在定型 UI 中顯示一組關鍵字，讓使用者用來標記已被捕獲的影像。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-387">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="ed4e5-388">它也會警示 *VoiceRecognizer* 類別，以開始接聽使用者進行語音輸入。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-388">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="ed4e5-389">新增 **VerifyTag ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-389">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="ed4e5-390">這個方法會接收 **VoiceRecognizer** 類別所辨識的語音輸入，並確認其有效性，然後開始定型程式。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-390">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="ed4e5-391">新增 **SubmitImageForTraining ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-391">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="ed4e5-392">此方法將開始自訂視覺服務訓練程式。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-392">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="ed4e5-393">第一個步驟是從與使用者驗證的語音輸入相關聯的服務中取出 **標記識別項** 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-393">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="ed4e5-394">然後，將會連同映射一起上傳 **標記識別項** 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-394">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="ed4e5-395">新增 **TrainCustomVisionProject ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-395">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="ed4e5-396">一旦提交並標記映射之後，就會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-396">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="ed4e5-397">它會建立新的反復專案，其會使用提交至服務的所有先前映射以及剛上傳的影像來定型。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-397">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="ed4e5-398">定型完成之後，這個方法會呼叫方法，將新建立的 **反復** 專案設定為 **預設值**，讓您用來進行分析的端點成為最新定型的反復專案。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-398">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="ed4e5-399">新增 **SetDefaultIteration ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-399">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="ed4e5-400">這個方法會將先前建立和定型的反復專案設定為 *預設值*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-400">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="ed4e5-401">完成之後，這個方法就必須刪除服務中現有的先前反復專案。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-401">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="ed4e5-402">在撰寫本課程時，最多可以在服務中同時存在 10 (10) 次反覆運算。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-402">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="ed4e5-403">新增 **DeletePreviousIteration ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-403">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="ed4e5-404">這個方法會尋找並刪除先前的非預設反復專案：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-404">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="ed4e5-405">要在這個類別中加入的最後一個方法是 **GetImageAsByteArray ()** 方法，用於 web 呼叫，以將捕獲的影像轉換成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-405">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="ed4e5-406">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-406">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="ed4e5-407">第10章-建立 SceneOrganiser 類別</span><span class="sxs-lookup"><span data-stu-id="ed4e5-407">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="ed4e5-408">此類別將會：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-408">This class will:</span></span>

-   <span data-ttu-id="ed4e5-409">建立要附加至主要攝影機的資料 **指標** 物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-409">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="ed4e5-410">建立會在服務辨識真實世界物件時出現的 **標籤** 物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-410">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="ed4e5-411">藉由將適當的元件附加至主要攝影機來設定。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-411">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="ed4e5-412">在 **分析模式** 中，會在執行時間產生標籤，在相對於主要攝影機位置的適當世界空間中產生標籤，並顯示從自訂視覺服務收到的資料。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-412">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="ed4e5-413">處於 **定型模式** 時，會產生 UI，以顯示定型流程的不同階段。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-413">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="ed4e5-414">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-414">To create this class:</span></span>

1.  <span data-ttu-id="ed4e5-415">在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-415">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="ed4e5-416">將腳本命名為 *SceneOrganiser*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-416">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="ed4e5-417">按兩下新的 *SceneOrganiser* 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-417">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="ed4e5-418">您只需要一個命名空間，請將其他命名空間從 *SceneOrganiser* 類別的上方移除：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-418">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="ed4e5-419">然後，在 *SceneOrganiser* 類別內，于 **Start ()** 方法的上方新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-419">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="ed4e5-420">刪除 [ **開始 ()** ]，並 **更新 ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-420">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="ed4e5-421">在變數下方，新增喚醒的 **()** 方法，這會初始化類別並設定場景。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-421">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="ed4e5-422">現在，請新增 **CreateCameraCursor ()** 方法，以建立並放置主要攝影機游標，以及 **CreateLabel ()** 方法來建立 **分析標籤** 物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-422">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="ed4e5-423">新增 **SetCameraStatus ()** 方法，這個方法會處理適用于提供相機狀態之文字網格的訊息。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-423">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="ed4e5-424">新增 **PlaceAnalysisLabel ()** 和 **SetTagsToLastLabel ()** 方法，這會產生自訂視覺服務中的資料，並將其顯示在場景中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-424">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="ed4e5-425">最後，新增 **CreateTrainingUI ()** 方法，這將會產生 UI，以在應用程式處於定型模式時，顯示定型程式的多個階段。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-425">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="ed4e5-426">此方法也會和轉型，以建立相機狀態物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-426">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="ed4e5-427">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-427">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed4e5-428">繼續之前，請先開啟 **CustomVisionAnalyser** 類別，然後在 **AnalyseLastImageCaptured ()** 方法中，將下列幾行 *取消* 批註：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-428">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="ed4e5-429">第11章-建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="ed4e5-429">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="ed4e5-430">您即將建立的下一個類別是 *ImageCapture* 類別。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-430">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="ed4e5-431">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-431">This class is responsible for:</span></span>

-   <span data-ttu-id="ed4e5-432">使用 HoloLens 攝影機來捕捉影像，並將它儲存在 *應用程式* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-432">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="ed4e5-433">處理使用者的點擊手勢。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-433">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="ed4e5-434">維護 *列舉* 值，以決定應用程式將會在 *分析* 模式或 *定型* 模式中執行。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-434">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="ed4e5-435">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-435">To create this class:</span></span>

1.  <span data-ttu-id="ed4e5-436">移至您先前建立的 **腳本** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-436">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="ed4e5-437">在資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-437">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="ed4e5-438">將腳本命名為 *ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-438">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="ed4e5-439">按兩下新的 **ImageCapture** 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-439">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="ed4e5-440">以下列內容取代檔案頂端的命名空間：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-440">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="ed4e5-441">然後，在 *ImageCapture* 類別內，于 **Start ()** 方法的上方新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-441">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="ed4e5-442">現在需要新增 **喚醒 ()** 和 **啟動 ()** 方法的程式碼：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-442">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="ed4e5-443">執行將在點一下手勢發生時呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-443">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="ed4e5-444">在 *分析* 模式中， **TapHandler** 方法會作為啟動或停止相片捕捉迴圈的參數。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-444">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="ed4e5-445">在 *定型* 模式中，它會從相機抓取影像。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-445">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="ed4e5-446">當游標為綠色時，表示相機可用來取得影像。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-446">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="ed4e5-447">當游標是紅色時，表示相機正在忙碌中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-447">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="ed4e5-448">新增應用程式用來啟動映射捕獲進程並儲存映射的方法。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-448">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="ed4e5-449">新增在拍攝相片時所要呼叫的處理常式，並在準備進行分析時進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-449">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="ed4e5-450">結果接著會根據程式碼的設定模式，傳遞給 *CustomVisionAnalyser* 或 *CustomVisionTrainer* 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-450">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="ed4e5-451">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-451">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="ed4e5-452">現在所有的腳本都已完成，請返回 Unity 編輯器，然後按一下 [**腳本**] 資料夾中的 [ **SceneOrganiser** ] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-452">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="ed4e5-453">第12章-建立前</span><span class="sxs-lookup"><span data-stu-id="ed4e5-453">Chapter 12 - Before building</span></span>

<span data-ttu-id="ed4e5-454">若要執行應用程式的完整測試，您必須將它側載到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-454">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="ed4e5-455">在執行之前，請確定：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-455">Before you do, ensure that:</span></span>

- <span data-ttu-id="ed4e5-456">[第2章](#chapter-2---training-your-custom-vision-project)中所述的所有設定都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-456">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="ed4e5-457">系統會正確指派 **主要攝影機**（偵測器面板）中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-457">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="ed4e5-458">腳本 **SceneOrganiser** 會附加至 **主要攝影機** 物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-458">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="ed4e5-459">請務必將您的 **預測索引鍵** 插入 **predictionKey** 變數中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-459">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="ed4e5-460">您已將 **預測端點** 插入至 **predictionEndpoint** 變數。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-460">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="ed4e5-461">您已將 **定型金鑰** 插入 *CustomVisionTrainer* 類別的 **trainingKey** 變數中。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-461">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="ed4e5-462">您已在 *CustomVisionTrainer* 類別的 **projectId** 變數中插入您的 **專案識別碼**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-462">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="ed4e5-463">第13章-建立並側載您的應用程式</span><span class="sxs-lookup"><span data-stu-id="ed4e5-463">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="ed4e5-464">若要開始 *建立* 程式：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-464">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="ed4e5-465">移至 [檔案 **> 組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-465">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="ed4e5-466">勾選 **Unity C \# 專案**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-466">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="ed4e5-467">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-467">Click **Build**.</span></span> <span data-ttu-id="ed4e5-468">Unity 將會啟動一個 **檔案總管** 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-468">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="ed4e5-469">立即建立該資料夾，並命名為 **應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-469">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="ed4e5-470">然後選取 [ **應用程式** ] 資料夾，然後按一下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-470">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="ed4e5-471">Unity 將開始將您的專案建立到 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-471">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="ed4e5-472">Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-472">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="ed4e5-473">若要在 HoloLens 上部署：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-473">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="ed4e5-474">您將需要 HoloLens (的 IP 位址，才能進行遠端部署) ，並確保 HoloLens 處於 **開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-474">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="ed4e5-475">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-475">To do this:</span></span>

    1.  <span data-ttu-id="ed4e5-476">在設置 HoloLens 的同時，開啟 **設定**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-476">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="ed4e5-477">前往 **Network & Internet**  >  **wi-fi**  >  **Advanced Options**</span><span class="sxs-lookup"><span data-stu-id="ed4e5-477">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="ed4e5-478">記下 **IPv4** 位址。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-478">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="ed4e5-479">接下來，流覽回到 [**設定**]，然後 **更新**  >  **開發人員 & 的** 安全性</span><span class="sxs-lookup"><span data-stu-id="ed4e5-479">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="ed4e5-480">設定 [ **開發人員模式]**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-480">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="ed4e5-481">流覽至您的新 Unity 組建 (**應用程式** 資料夾) ，然後以 **Visual Studio** 開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-481">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="ed4e5-482">在 [ *方案* 設定] 中選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-482">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="ed4e5-483">在 *解決方案平臺* 中，選取 [ **x86]、[遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-483">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="ed4e5-484">系統會提示您將遠端裝置的 **IP 位址** 插入 (HoloLens，在此案例中，您會記下) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-484">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![設定 IP 位址](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="ed4e5-486">移至 [ **組建** ] 功能表，然後按一下 [ **部署方案** ]，將應用程式側載至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-486">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="ed4e5-487">您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中，準備好可供啟動！</span><span class="sxs-lookup"><span data-stu-id="ed4e5-487">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="ed4e5-488">若要部署到沉浸式耳機，請將 **解決方案平臺\*\*\*\*設定為 [** *本機電腦*]，並將 [設定] 設定為 [以 *x86* 作為 **平臺**] 來進行 *Debug*。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-488">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="ed4e5-489">然後使用 [ **組建** ] 功能表項目選取 [ *部署方案*]，部署到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-489">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="ed4e5-490">若要使用應用程式：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-490">To use the application:</span></span>

<span data-ttu-id="ed4e5-491">若要在 *定型* 模式與 *預測* 模式之間切換應用程式功能，您必須更新位於 *ImageCapture* 類別內的 **喚醒 ()** 方法中的 **AppMode** 變數。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-491">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="ed4e5-492">或</span><span class="sxs-lookup"><span data-stu-id="ed4e5-492">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="ed4e5-493">在 *定型* 模式中：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-493">In *Training* mode:</span></span>

- <span data-ttu-id="ed4e5-494">查看 **滑鼠** 或 **鍵盤** ，然後使用 [點一下 **手勢**]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-494">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="ed4e5-495">接下來會出現文字，要求您提供標記。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-495">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="ed4e5-496">說的是 **滑鼠** 或 **鍵盤**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-496">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="ed4e5-497">在 *預測* 模式中：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-497">In *Prediction* mode:</span></span>

- <span data-ttu-id="ed4e5-498">查看物件，並使用 **點擊手勢**。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-498">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="ed4e5-499">文字將會出現，並提供偵測到的物件，機率最高 (這是正規化) 。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-499">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="ed4e5-500">第14章-評估及改善您的自訂視覺模型</span><span class="sxs-lookup"><span data-stu-id="ed4e5-500">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="ed4e5-501">若要讓您的服務更加精確，您必須繼續定型用於預測的模型。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-501">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="ed4e5-502">這是透過使用您的新應用程式（包含 *定型* 和 *預測* 模式）來完成，而後者則需要您造訪入口網站，這是本章所涵蓋的內容。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-502">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="ed4e5-503">準備重新流覽您的入口網站多次，以持續改善您的模型。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-503">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="ed4e5-504">再次前往您的 Azure 自訂視覺入口網站，並在您的專案中選取 [ *預測* ] 索引標籤， (從頁面的左上角開始) ：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-504">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![選取 [預測] 索引標籤](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="ed4e5-506">當您的應用程式執行時，您會看到所有已傳送至服務的影像。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-506">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="ed4e5-507">如果您將滑鼠停留在影像上，則會為您提供針對該影像所做的預測：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-507">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![預測影像清單](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="ed4e5-509">選取其中一個影像來開啟它。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-509">Select one of your images to open it.</span></span> <span data-ttu-id="ed4e5-510">開啟之後，您將會看到對該影像所做的預測是在右邊。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-510">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="ed4e5-511">如果您的預測正確無誤，而且您想要將此影像新增至服務的定型模型，請按一下 [ *我的標記* ] 輸入方塊，然後選取您想要建立關聯的標記。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-511">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="ed4e5-512">當您完成時，請按一下右下角的 [ *儲存並關閉* ] 按鈕，然後繼續進行下一個影像。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-512">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![選取要開啟的影像](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="ed4e5-514">回到影像的方格之後，您會注意到，您已將標記新增至 (並儲存) 的影像將會被移除。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-514">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="ed4e5-515">如果您找到任何您認為沒有標記的項目的影像，則可以將其刪除，方法是按一下該影像上的刻度， (可以針對數個影像進行這項作業) 然後按一下格線頁右上角的 [ *刪除* ]。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-515">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="ed4e5-516">在接下來的快顯視窗中，您可以按一下 *[是]、[刪除]* 或 [ *否*]，以分別確認刪除或取消。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-516">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![刪除映像](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="ed4e5-518">當您準備好繼續進行時，請按一下右上方的綠色 [ *定型* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-518">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="ed4e5-519">您的服務模型將會使用您現在提供的所有影像來定型， (如此可讓) 更準確。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-519">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="ed4e5-520">定型完成後，請務必按一下 [ *設為預設值* ] 按鈕，讓您的 *預測 URL* 繼續使用您服務的最新反復專案。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-520">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="ed4e5-521">![開始訓練服務模型 ](images/AzureLabs-Lab302b-39.png) ![ 選取 [設為預設值] 選項](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="ed4e5-521">![Start training service model](images/AzureLabs-Lab302b-39.png) ![Select make default option](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="ed4e5-522">您完成的自訂視覺 API 應用程式</span><span class="sxs-lookup"><span data-stu-id="ed4e5-522">Your finished Custom Vision API application</span></span>

<span data-ttu-id="ed4e5-523">恭喜，您已建立混合的現實應用程式，利用 Azure 自訂視覺 API 來辨識真實世界物件、訓練服務模型，以及顯示已看到內容的信心。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-523">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![完成的專案範例](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ed4e5-525">額外練習</span><span class="sxs-lookup"><span data-stu-id="ed4e5-525">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="ed4e5-526">練習1</span><span class="sxs-lookup"><span data-stu-id="ed4e5-526">Exercise 1</span></span>

<span data-ttu-id="ed4e5-527">訓練您的 **自訂視覺服務** ，以辨識更多物件。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-527">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="ed4e5-528">練習2</span><span class="sxs-lookup"><span data-stu-id="ed4e5-528">Exercise 2</span></span>

<span data-ttu-id="ed4e5-529">若要展開您學到的內容，請完成下列練習：</span><span class="sxs-lookup"><span data-stu-id="ed4e5-529">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="ed4e5-530">辨識物件時播放音效。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-530">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="ed4e5-531">練習3</span><span class="sxs-lookup"><span data-stu-id="ed4e5-531">Exercise 3</span></span>

<span data-ttu-id="ed4e5-532">使用 API 以您的應用程式所分析的相同影像來重新定型您的服務，以便讓服務更準確 (同時) 預測和定型。</span><span class="sxs-lookup"><span data-stu-id="ed4e5-532">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>