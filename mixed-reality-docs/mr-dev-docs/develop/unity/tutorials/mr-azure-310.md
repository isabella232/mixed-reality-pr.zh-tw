---
title: HoloLens (第1代) 和 Azure 310-物件偵測
description: 完成本課程，以瞭解如何訓練和使用機器學習模型，以辨識類似的物件和其在真實世界中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，自訂視覺，物件偵測，混合現實，學院，unity，教學課程，api，hololens，Windows 10，Visual Studio
ms.openlocfilehash: 29b3622e510a0d97ee3f1dea04661b7d6ab51f9f
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730345"
---
# <a name="hololens-1st-gen-and-azure-310-object-detection"></a><span data-ttu-id="5cad2-104">HoloLens (第1代) 和 Azure 310：物件偵測</span><span class="sxs-lookup"><span data-stu-id="5cad2-104">HoloLens (1st gen) and Azure 310: Object detection</span></span>

>[!NOTE]
><span data-ttu-id="5cad2-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="5cad2-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5cad2-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="5cad2-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5cad2-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="5cad2-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5cad2-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="5cad2-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5cad2-109">未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="5cad2-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5cad2-110">當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。</span><span class="sxs-lookup"><span data-stu-id="5cad2-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

<span data-ttu-id="5cad2-111">在此課程中，您將瞭解如何在混合現實應用程式中使用 Azure 自訂視覺「物件偵測」功能，來辨識所提供映射內的自訂視覺效果內容和其空間位置。</span><span class="sxs-lookup"><span data-stu-id="5cad2-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="5cad2-112">這種服務可讓您使用物件影像來定型機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="5cad2-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="5cad2-113">然後，您將使用定型的模型來辨識類似的物件，並將其在真實世界中的位置（如 Microsoft HoloLens 的相機捕捉所提供）或攝影機連接到適用于沉浸式 (VR) 耳機的電腦。</span><span class="sxs-lookup"><span data-stu-id="5cad2-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![課程結果](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="5cad2-115">**Azure 自訂視覺，物件偵測** 是一項 Microsoft 服務，可讓開發人員建立自訂影像分類器。</span><span class="sxs-lookup"><span data-stu-id="5cad2-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="5cad2-116">然後，您可以在影像本身內提供方塊 **界限** ，將這些分類器用於新的影像，以偵測該新影像內的物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="5cad2-117">此服務提供簡單、容易使用的線上入口網站，以簡化此程式。</span><span class="sxs-lookup"><span data-stu-id="5cad2-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="5cad2-118">如需詳細資訊，請造訪下列連結：</span><span class="sxs-lookup"><span data-stu-id="5cad2-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="5cad2-119">Azure 自訂視覺頁面</span><span class="sxs-lookup"><span data-stu-id="5cad2-119">Azure Custom Vision page</span></span>](/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="5cad2-120">限制和配額</span><span class="sxs-lookup"><span data-stu-id="5cad2-120">Limits and Quotas</span></span>](/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="5cad2-121">完成本課程之後，您將會有一個混合現實應用程式，可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5cad2-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="5cad2-122">使用者可以使用 Azure 自訂視覺服務的物件偵測，來 *注視* 已定型的物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="5cad2-123">使用者會使用點一下 *手勢來* 捕捉其所查看內容的影像。</span><span class="sxs-lookup"><span data-stu-id="5cad2-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="5cad2-124">應用程式會將映射傳送至 Azure 自訂視覺服務。</span><span class="sxs-lookup"><span data-stu-id="5cad2-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="5cad2-125">服務會有回復，會將辨識結果顯示為世界空間文字。</span><span class="sxs-lookup"><span data-stu-id="5cad2-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="5cad2-126">這會透過使用 Microsoft HoloLens 的空間追蹤來完成，以瞭解辨識物件的世界位置，然後使用與影像中偵測到的相關聯的 *標記* 來提供標籤文字。</span><span class="sxs-lookup"><span data-stu-id="5cad2-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="5cad2-127">本課程也會說明如何手動上傳影像、建立標籤，以及訓練服務，以在所提供的範例中辨識不同的物件 (在所提供的範例中，這是杯) ，方法是在您提交的影像內設定 *界限* 方塊。</span><span class="sxs-lookup"><span data-stu-id="5cad2-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="5cad2-128">在建立和使用應用程式之後，開發人員應該流覽回 Azure 自訂視覺服務，並找出服務所做的預測，並判斷其是否正確或不 (透過標記服務遺漏的任何內容，以及調整周 *框方塊*) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="5cad2-129">然後，您可以重新定型服務，這會增加 it 識別真實世界物件的可能性。</span><span class="sxs-lookup"><span data-stu-id="5cad2-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="5cad2-130">本課程將指導您如何將 Azure 自訂視覺服務、物件偵測的結果，取得至 Unity 型範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cad2-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="5cad2-131">您必須將這些概念套用至您可能正在建立的自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cad2-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="5cad2-132">裝置支援</span><span class="sxs-lookup"><span data-stu-id="5cad2-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5cad2-133">課程</span><span class="sxs-lookup"><span data-stu-id="5cad2-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5cad2-134"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5cad2-134"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5cad2-135"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="5cad2-135"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="5cad2-136">MR 和 Azure 310：物件偵測</span><span class="sxs-lookup"><span data-stu-id="5cad2-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="5cad2-137">✔️</span><span class="sxs-lookup"><span data-stu-id="5cad2-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="5cad2-138">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5cad2-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="5cad2-139">本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="5cad2-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="5cad2-140">另外也請注意，本檔中的必要條件和書面指示，代表在撰寫 (2018 年7月) 時已經過測試和驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="5cad2-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="5cad2-141">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span><span class="sxs-lookup"><span data-stu-id="5cad2-141">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="5cad2-142">本課程建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="5cad2-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="5cad2-143">開發電腦</span><span class="sxs-lookup"><span data-stu-id="5cad2-143">A development PC</span></span>
- [<span data-ttu-id="5cad2-144">啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="5cad2-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="5cad2-145">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="5cad2-145">The latest Windows 10 SDK</span></span>](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="5cad2-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="5cad2-146">Unity 2017.4 LTS</span></span>](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="5cad2-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5cad2-147">Visual Studio 2017</span></span>](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="5cad2-148">啟用開發人員模式的[Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details)</span><span class="sxs-lookup"><span data-stu-id="5cad2-148">A [Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="5cad2-149">適用于 Azure 安裝和自訂視覺服務抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="5cad2-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="5cad2-150">針對您想要自訂視覺辨識的每個物件，至少) 需要一系列 15 (15) 映射。</span><span class="sxs-lookup"><span data-stu-id="5cad2-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="5cad2-151">如果您想要的話，可以使用本課程所提供的映射，也就 [是一系列的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="5cad2-152">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="5cad2-152">Before you start</span></span>

1.  <span data-ttu-id="5cad2-153">為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="5cad2-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="5cad2-154">設定及測試 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5cad2-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="5cad2-155">如果您需要設定 HoloLens 的支援， [請務必造訪 HoloLens 安裝文章](/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="5cad2-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="5cad2-156">開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助針對每個使用者) 執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="5cad2-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="5cad2-157">如需有關校正的說明，請遵循此 [與 HoloLens 校正文章相關的連結](/hololens/hololens-calibration#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="5cad2-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="5cad2-158">如需有關感應器微調的說明，請依照此 [連結來進行「HoloLens 感應器微調」文章](/hololens/hololens-updates)。</span><span class="sxs-lookup"><span data-stu-id="5cad2-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="5cad2-159">第1章-自訂視覺入口網站</span><span class="sxs-lookup"><span data-stu-id="5cad2-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="5cad2-160">若要使用 **Azure 自訂視覺服務**，您必須將它的實例設定為可供您的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="5cad2-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="5cad2-161">流覽 [至 **自訂視覺服務** 主頁面](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。</span><span class="sxs-lookup"><span data-stu-id="5cad2-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="5cad2-162">按一下 [ **開始使用**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="5cad2-163">登入自訂視覺入口網站。</span><span class="sxs-lookup"><span data-stu-id="5cad2-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="5cad2-164">如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="5cad2-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="5cad2-165">如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="5cad2-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="5cad2-166">當您第一次登入之後，系統會提示您提供 *服務條款* 面板。</span><span class="sxs-lookup"><span data-stu-id="5cad2-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="5cad2-167">按一下核取方塊以 *同意條款*。</span><span class="sxs-lookup"><span data-stu-id="5cad2-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="5cad2-168">然後按一下 [ **我同意**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="5cad2-169">同意條款之後，您現在就可以在 [ *我的專案* ] 區段中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="5cad2-170">按一下 [ **新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="5cad2-171">右側將會出現一個索引標籤，提示您指定專案的某些欄位。</span><span class="sxs-lookup"><span data-stu-id="5cad2-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="5cad2-172">為您的專案插入名稱</span><span class="sxs-lookup"><span data-stu-id="5cad2-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="5cad2-173">為您的專案插入描述 (**選擇性**) </span><span class="sxs-lookup"><span data-stu-id="5cad2-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="5cad2-174">選擇資源群組，或建立一個新的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5cad2-175">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="5cad2-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5cad2-176">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="5cad2-177">如果您想要[閱讀更多有關 Azure 資源群組的資訊，請流覽至相關聯的](/azure/azure-resource-manager/resource-group-portal)檔</span><span class="sxs-lookup"><span data-stu-id="5cad2-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="5cad2-178">將 **專案類型** 設定為 **物件偵測 (預覽)**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="5cad2-179">完成之後，按一下 [ **建立專案**]，系統就會將您重新導向至自訂視覺服務專案] 頁面。</span><span class="sxs-lookup"><span data-stu-id="5cad2-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="5cad2-180">第2章-訓練自訂視覺專案</span><span class="sxs-lookup"><span data-stu-id="5cad2-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="5cad2-181">在自訂視覺入口網站中，您的主要目標是將您的專案定型，以辨識影像中的特定物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="5cad2-182">針對您想要讓應用程式辨識的每個物件，至少需要 15 (15) 的影像。</span><span class="sxs-lookup"><span data-stu-id="5cad2-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="5cad2-183">您可以使用本課程所提供的影像 ([一連串的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="5cad2-184">定型您的自訂視覺專案：</span><span class="sxs-lookup"><span data-stu-id="5cad2-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="5cad2-185">按一下 [ **+** **標記**] 旁的按鈕。</span><span class="sxs-lookup"><span data-stu-id="5cad2-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="5cad2-186">針對將用來與您的影像建立關聯的標記新增 **名稱** 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="5cad2-187">在此範例中，我們會使用 cup 的影像進行辨識，因此請為這個 **杯杯** 命名標記。</span><span class="sxs-lookup"><span data-stu-id="5cad2-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="5cad2-188">按一下 [ **儲存** 完成]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="5cad2-189">您會注意到 **您的標籤已新增** (您可能需要重載頁面，才能讓它顯示) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="5cad2-190">按一下頁面中央的 [ **加入影像** ]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="5cad2-191">按一下 **[流覽本機檔案]**，然後流覽至您想要上傳一個物件的影像，其最少為 15 (15) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="5cad2-192">您可以一次選取多個影像，以便上傳。</span><span class="sxs-lookup"><span data-stu-id="5cad2-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="5cad2-193">當您選取要用來定型專案的所有影像之後，請按 **[上傳** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="5cad2-194">檔案將會開始上傳。</span><span class="sxs-lookup"><span data-stu-id="5cad2-194">The files will begin uploading.</span></span> <span data-ttu-id="5cad2-195">確認上傳之後，請按一下 [ **完成**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="5cad2-196">此時您的影像已上傳，但未標記。</span><span class="sxs-lookup"><span data-stu-id="5cad2-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="5cad2-197">若要標記您的映射，請使用滑鼠。</span><span class="sxs-lookup"><span data-stu-id="5cad2-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="5cad2-198">當您將滑鼠停留在影像上時，選取專案醒目提示將會透過自動在物件周圍繪製選取專案來協助您。</span><span class="sxs-lookup"><span data-stu-id="5cad2-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="5cad2-199">如果不正確，您可以自行繪製。</span><span class="sxs-lookup"><span data-stu-id="5cad2-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="5cad2-200">若要完成此動作，請按住滑鼠左鍵，然後拖曳選取區域以包含您的物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="5cad2-201">在影像中選取您的物件之後，小提示會要求您 *新增區域標記*。</span><span class="sxs-lookup"><span data-stu-id="5cad2-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="5cad2-202">選取先前建立的標籤 ( ' 杯 '，在上述範例中) ，或如果您要新增更多標籤，請在中輸入，然後按一下 **+ (再加)** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5cad2-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="5cad2-203">若要標記下一個影像，您可以按一下分頁右邊的箭號，或按一下分頁的右上) 角的 **X** ，關閉標記分頁 (，然後按一下下一個影像。</span><span class="sxs-lookup"><span data-stu-id="5cad2-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="5cad2-204">當您準備好下一個映射之後，請重複相同的程式。</span><span class="sxs-lookup"><span data-stu-id="5cad2-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="5cad2-205">針對您已上傳的所有影像進行此操作，直到全部標記為止。</span><span class="sxs-lookup"><span data-stu-id="5cad2-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="5cad2-206">您可以在同一個影像中選取數個物件，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="5cad2-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="5cad2-207">一旦您標記全部，請按一下畫面左側的 [ **標記** ] 按鈕，以顯示已標記的影像。</span><span class="sxs-lookup"><span data-stu-id="5cad2-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="5cad2-208">您現在已準備好定型您的服務。</span><span class="sxs-lookup"><span data-stu-id="5cad2-208">You are now ready to train your Service.</span></span> <span data-ttu-id="5cad2-209">按一下 [ **定型** ] 按鈕，就會開始第一個定型反復專案。</span><span class="sxs-lookup"><span data-stu-id="5cad2-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="5cad2-210">一旦建立之後，您就可以看到兩個按鈕，稱為「 **建立預設值** 和 **預測 URL**」。</span><span class="sxs-lookup"><span data-stu-id="5cad2-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="5cad2-211">先按一下 [ **設為預設值** ]，然後按一下 [ **預測 URL**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="5cad2-212">由此提供的端點會設定為已標示為預設值的任何 *反復* 專案。</span><span class="sxs-lookup"><span data-stu-id="5cad2-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="5cad2-213">因此，如果您稍後建立新的 *反復* 專案，並將其更新為預設值，您就不需要變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="5cad2-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="5cad2-214">當您按一下 [ **預測 URL**] 之後，請開啟 [ *記事本*]，然後複製並貼上 **URL** (也稱為您的 **預測端點**) 和 **服務預測金鑰**，讓您可以在稍後於程式碼中需要時加以取出。</span><span class="sxs-lookup"><span data-stu-id="5cad2-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="5cad2-215">第3章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="5cad2-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="5cad2-216">以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="5cad2-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="5cad2-217">開啟 **Unity** ，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="5cad2-218">您現在將需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="5cad2-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="5cad2-219">插入 **CustomVisionObjDetection**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="5cad2-220">請確定專案類型設定為 **3d**，並將 **位置** 設定為適合您 (記住，更接近根目錄的) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="5cad2-221">然後，按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="5cad2-222">在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="5cad2-223">移至 [ **編輯*  >  *喜好** 設定]，然後在新視窗中，流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="5cad2-224">將 **外部腳本編輯器** 變更為 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="5cad2-225">關閉 [ **喜好** 設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5cad2-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="5cad2-226">接下來，移至 [檔案 **> 組建設定** ]，並將 **平臺** 切換至 [ *通用 Windows 平臺*]，然後按一下 [ **切換平臺** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5cad2-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="5cad2-227">在相同的 [ **組建設定** ] 視窗中，確定已設定下列各項：</span><span class="sxs-lookup"><span data-stu-id="5cad2-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="5cad2-228">**目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5cad2-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="5cad2-229">**組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="5cad2-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="5cad2-230">**SDK** 已設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="5cad2-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="5cad2-231">**Visual Studio 版本** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="5cad2-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="5cad2-232">**組建並執行** 設定為 **本機電腦**</span><span class="sxs-lookup"><span data-stu-id="5cad2-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="5cad2-233">[ **組建設定**] 中的其餘設定，現在應該保持為預設值。</span><span class="sxs-lookup"><span data-stu-id="5cad2-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="5cad2-234">在相同的 [ **組建設定** ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 **器** 所在空間中的相關面板。</span><span class="sxs-lookup"><span data-stu-id="5cad2-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="5cad2-235">在此面板中，需要驗證幾個設定：</span><span class="sxs-lookup"><span data-stu-id="5cad2-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="5cad2-236">在 [ **其他設定** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="5cad2-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="5cad2-237">**腳本執行階段版本** 應該是 **實驗** ( .net 4.6 對等) ，這會觸發重新開機編輯器的需求。</span><span class="sxs-lookup"><span data-stu-id="5cad2-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="5cad2-238">**腳本後端** 應該是 **.net**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="5cad2-239">**API 相容性層級** 應為 **.net 4.6**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="5cad2-240">在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：</span><span class="sxs-lookup"><span data-stu-id="5cad2-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="5cad2-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="5cad2-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="5cad2-242">**網路攝影機**</span><span class="sxs-lookup"><span data-stu-id="5cad2-242">**Webcam**</span></span>

        3. <span data-ttu-id="5cad2-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="5cad2-243">**SpatialPerception**</span></span>

            <span data-ttu-id="5cad2-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="5cad2-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="5cad2-245">在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，並確定已新增 **Windows Mixed Reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="5cad2-246">回到 **組建設定**， *Unity C \# 專案* 不再呈現灰色：勾選這個旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5cad2-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="5cad2-247">關閉 [組建設定]  視窗。</span><span class="sxs-lookup"><span data-stu-id="5cad2-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="5cad2-248">在 **編輯器** 中，按一下 [**編輯**  >  **專案設定**  >  **圖形**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="5cad2-249">在 [偵測 **器] 面板** 中， *圖形設定* 將會開啟。</span><span class="sxs-lookup"><span data-stu-id="5cad2-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="5cad2-250">向下鍵，直到您看到名為 [ **永遠包含著色** 器] 的陣列為止。</span><span class="sxs-lookup"><span data-stu-id="5cad2-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="5cad2-251">在此範例中，藉由將 **大小** 變數增加一個 (來新增位置，這是8，因此我們將它設為 9) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="5cad2-252">新的位置會出現在陣列的最後一個位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5cad2-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="5cad2-253">在位置中，按一下位置旁的小目標圓形以開啟著色器清單。</span><span class="sxs-lookup"><span data-stu-id="5cad2-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="5cad2-254">尋找 **舊版著色器/透明/擴散** 著色器，然後按兩下它。</span><span class="sxs-lookup"><span data-stu-id="5cad2-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="5cad2-255">第4章-匯入 CustomVisionObjDetection Unity 套件</span><span class="sxs-lookup"><span data-stu-id="5cad2-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="5cad2-256">在此課程中，您會提供名為 **Azure-MR-310. unitypackage** 的 Unity 資產套件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="5cad2-257">提醒Unity 支援的任何物件（包括整個場景）都可以封裝至 **unitypackage** 檔案，並在其他專案中匯出/匯入。</span><span class="sxs-lookup"><span data-stu-id="5cad2-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="5cad2-258">這是在不同 **Unity 專案** 之間移動資產最安全且最有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="5cad2-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="5cad2-259">您可以在 [這裡找到您需要下載的 Azure-MR-310 套件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="5cad2-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="5cad2-260">使用 Unity 儀表板，在畫面頂端的功能表中按一下 [ **資產** ]，然後按一下 [匯 **入封裝 > 自訂套件**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="5cad2-261">使用檔案選擇器選取 **Azure-MR. unitypackage** 套件，然後按一下 [ **開啟**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="5cad2-262">系統會向您顯示此資產的元件清單。</span><span class="sxs-lookup"><span data-stu-id="5cad2-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="5cad2-263">按一下 [匯 **入** ] 按鈕以確認匯入。</span><span class="sxs-lookup"><span data-stu-id="5cad2-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="5cad2-264">匯入完成後，您會注意到套件中的資料夾現在已新增至 [ **資產** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5cad2-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="5cad2-265">這種資料夾結構一般適用于 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="5cad2-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="5cad2-266">[ **材質** ] 資料夾包含 **注視游標** 所使用的材質。</span><span class="sxs-lookup"><span data-stu-id="5cad2-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="5cad2-267">[ **外掛程式** ] 資料夾包含程式碼用來還原序列化服務 web 回應的 Newtonsoft DLL。</span><span class="sxs-lookup"><span data-stu-id="5cad2-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="5cad2-268">包含在資料夾和子資料夾中的兩個 (2) 不同的版本是必要的，可讓 Unity 編輯器和 UWP 組建使用和建立程式庫。</span><span class="sxs-lookup"><span data-stu-id="5cad2-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="5cad2-269">**Prefabs** 資料夾包含場景中包含的 Prefabs。</span><span class="sxs-lookup"><span data-stu-id="5cad2-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="5cad2-270">這些是：</span><span class="sxs-lookup"><span data-stu-id="5cad2-270">Those are:</span></span>

        1.  <span data-ttu-id="5cad2-271">**GazeCursor**，在應用程式中使用的資料指標。</span><span class="sxs-lookup"><span data-stu-id="5cad2-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="5cad2-272">將與 SpatialMapping 預製專案搭配運作，以將場景放在實體物件的上方。</span><span class="sxs-lookup"><span data-stu-id="5cad2-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="5cad2-273">**標籤**，這是在必要時用來在場景中顯示物件標記的 UI 物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="5cad2-274">**SpatialMapping**，這是可讓應用程式使用 Microsoft HoloLens 的空間追蹤來建立虛擬對應的物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="5cad2-275">目前包含此課程之預先建立場景的 **場景** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5cad2-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="5cad2-276">開啟 [ **場景** ] 資料夾，然後在 [ **專案] 面板** 中按兩下 **ObjDetectionScene**，載入您將在此課程中使用的場景。</span><span class="sxs-lookup"><span data-stu-id="5cad2-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="5cad2-277">**未包含任何程式碼**，您將遵循本課程來撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="5cad2-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="5cad2-278">第5章-建立 CustomVisionAnalyser 類別。</span><span class="sxs-lookup"><span data-stu-id="5cad2-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="5cad2-279">至此，您已準備好撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="5cad2-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="5cad2-280">您將開始使用 **CustomVisionAnalyser** 類別。</span><span class="sxs-lookup"><span data-stu-id="5cad2-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="5cad2-281">在如下所示的程式碼中，對 **自訂視覺服務** 的呼叫會使用 **自訂視覺 REST API** 進行。</span><span class="sxs-lookup"><span data-stu-id="5cad2-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="5cad2-282">透過這種方式，您將瞭解如何實行和使用此 API (有助於瞭解如何在您自己的) 上執行類似的操作。</span><span class="sxs-lookup"><span data-stu-id="5cad2-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="5cad2-283">請注意，Microsoft 提供的 **自訂視覺 SDK** 也可以用來對服務進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="5cad2-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="5cad2-284">如需詳細資訊，請造訪 [自訂視覺 SDK 文章](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。</span><span class="sxs-lookup"><span data-stu-id="5cad2-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="5cad2-285">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="5cad2-285">This class is responsible for:</span></span>

- <span data-ttu-id="5cad2-286">載入以位元組陣列形式捕獲的最新映射。</span><span class="sxs-lookup"><span data-stu-id="5cad2-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="5cad2-287">將位元組陣列傳送至您的 Azure **自訂視覺服務** 實例以進行分析。</span><span class="sxs-lookup"><span data-stu-id="5cad2-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="5cad2-288">以 JSON 字串的形式接收回應。</span><span class="sxs-lookup"><span data-stu-id="5cad2-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="5cad2-289">將回應還原序列化，並將產生的 **預測** 傳遞給 **SceneOrganiser** 類別，這將會負責顯示回應的方式。</span><span class="sxs-lookup"><span data-stu-id="5cad2-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="5cad2-290">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="5cad2-290">To create this class:</span></span>

1.  <span data-ttu-id="5cad2-291">以滑鼠右鍵按一下 [**資產] 資料夾**（位於 [**專案] 面板** 中），然後按一下 [**建立**  >  **資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="5cad2-292">呼叫資料夾 **腳本**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="5cad2-293">按兩下新建立的資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="5cad2-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="5cad2-294">在資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="5cad2-295">將腳本命名為 **CustomVisionAnalyser。**</span><span class="sxs-lookup"><span data-stu-id="5cad2-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="5cad2-296">按兩下新的 **CustomVisionAnalyser** 腳本，以 **Visual Studio 開啟。**</span><span class="sxs-lookup"><span data-stu-id="5cad2-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="5cad2-297">請確定您已在檔案頂端參考下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="5cad2-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="5cad2-298">在 **CustomVisionAnalyser** 類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="5cad2-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="5cad2-299">務必將您的 **服務預測金鑰** 插入至 **predictionKey** 變數，並將您的 **預測端點** 插入至 **predictionEndpoint** 變數。</span><span class="sxs-lookup"><span data-stu-id="5cad2-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="5cad2-300">您先前已將這些複製到「記事本」， [步驟14中的第2章](#chapter-2---training-your-custom-vision-project)。</span><span class="sxs-lookup"><span data-stu-id="5cad2-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="5cad2-301">現在需要新增 **喚醒 ()** 的程式碼，以初始化執行個體變數：</span><span class="sxs-lookup"><span data-stu-id="5cad2-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="5cad2-302">新增協同程式 (，並在其下方加入靜態 **GetImageAsByteArray ()** 方法) ，它會取得 **ImageCapture** 類別所捕捉的影像分析結果。</span><span class="sxs-lookup"><span data-stu-id="5cad2-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5cad2-303">在 [ **AnalyseImageCapture** ] 協同程式中，您還必須呼叫 **SceneOrganiser** 類別。</span><span class="sxs-lookup"><span data-stu-id="5cad2-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="5cad2-304">因此，請 **暫時將這些行** 加上批註。</span><span class="sxs-lookup"><span data-stu-id="5cad2-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. <span data-ttu-id="5cad2-305">刪除 [ **開始 ()** ] 並 **更新 ()** 方法，因為它們不會使用。</span><span class="sxs-lookup"><span data-stu-id="5cad2-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="5cad2-306">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cad2-307">如先前所述，請不要擔心可能出現錯誤的程式碼，因為您很快就會提供進一步的類別，這將會修正這些問題。</span><span class="sxs-lookup"><span data-stu-id="5cad2-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="5cad2-308">第6章-建立 CustomVisionObjects 類別</span><span class="sxs-lookup"><span data-stu-id="5cad2-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="5cad2-309">您將建立的類別現在是 **CustomVisionObjects** 類別。</span><span class="sxs-lookup"><span data-stu-id="5cad2-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="5cad2-310">此腳本包含其他類別用來序列化和還原序列化對自訂視覺服務進行之呼叫的物件數。</span><span class="sxs-lookup"><span data-stu-id="5cad2-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="5cad2-311">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="5cad2-311">To create this class:</span></span>

1.  <span data-ttu-id="5cad2-312">在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="5cad2-313">呼叫腳本 **CustomVisionObjects。**</span><span class="sxs-lookup"><span data-stu-id="5cad2-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="5cad2-314">按兩下新的 **CustomVisionObjects** 腳本，以 **Visual Studio 開啟。**</span><span class="sxs-lookup"><span data-stu-id="5cad2-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="5cad2-315">請確定您已在檔案頂端參考下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="5cad2-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="5cad2-316">刪除 **開始 ()** ，並 **更新** **CustomVisionObjects** 類別內的 () 方法，這個類別現在應該是空的。</span><span class="sxs-lookup"><span data-stu-id="5cad2-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="5cad2-317">請務必小心遵循下一個指示。</span><span class="sxs-lookup"><span data-stu-id="5cad2-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="5cad2-318">如果您將新的類別宣告放在 **CustomVisionObjects** 類別內，您將會在第 [10 章](#chapter-10---create-the-imagecapture-class)取得編譯錯誤，指出找不到 **AnalysisRootObject** 和 **BoundingBox** 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="5cad2-319">將下列類別新增至 **CustomVisionObjects** 類別 *之外*。</span><span class="sxs-lookup"><span data-stu-id="5cad2-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="5cad2-320">**Newtonsoft** 程式庫會使用這些物件，將回應資料序列化和還原序列化：</span><span class="sxs-lookup"><span data-stu-id="5cad2-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="5cad2-321">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="5cad2-322">第7章-建立 SpatialMapping 類別</span><span class="sxs-lookup"><span data-stu-id="5cad2-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="5cad2-323">這個類別會在場景中設定 **空間對應碰撞** ，以便能夠偵測虛擬物件與真實物件之間的衝突。</span><span class="sxs-lookup"><span data-stu-id="5cad2-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="5cad2-324">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="5cad2-324">To create this class:</span></span>

1.  <span data-ttu-id="5cad2-325">在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="5cad2-326">呼叫腳本 **SpatialMapping。**</span><span class="sxs-lookup"><span data-stu-id="5cad2-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="5cad2-327">按兩下新的 **SpatialMapping** 腳本，以 **Visual Studio 開啟。**</span><span class="sxs-lookup"><span data-stu-id="5cad2-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="5cad2-328">請確定您在 **SpatialMapping** 類別上方參考了下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="5cad2-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="5cad2-329">然後，在 **SpatialMapping** 類別內新增下列變數，並在 **Start ()** 方法的上方：</span><span class="sxs-lookup"><span data-stu-id="5cad2-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="5cad2-330">新增 **喚醒的 ()** 並 **開始 ()**：</span><span class="sxs-lookup"><span data-stu-id="5cad2-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="5cad2-331">刪除 **更新 ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="5cad2-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="5cad2-332">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="5cad2-333">第8章-建立 GazeCursor 類別</span><span class="sxs-lookup"><span data-stu-id="5cad2-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="5cad2-334">這個類別負責利用上一章所建立的 **SpatialMappingCollider**，在實際空間的正確位置設定資料指標。</span><span class="sxs-lookup"><span data-stu-id="5cad2-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="5cad2-335">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="5cad2-335">To create this class:</span></span>

1.  <span data-ttu-id="5cad2-336">在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="5cad2-337">呼叫腳本 **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="5cad2-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="5cad2-338">按兩下新的 **GazeCursor** 腳本，以 **Visual Studio 開啟。**</span><span class="sxs-lookup"><span data-stu-id="5cad2-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="5cad2-339">請確定您在 **GazeCursor** 類別上方參考了下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="5cad2-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="5cad2-340">然後，在 **GazeCursor** 類別內，于 **Start ()** 方法的上方新增下列變數。</span><span class="sxs-lookup"><span data-stu-id="5cad2-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="5cad2-341">以下列程式碼更新 **啟動 ()** 方法：</span><span class="sxs-lookup"><span data-stu-id="5cad2-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="5cad2-342">使用下列程式碼更新 **更新 ()** 方法：</span><span class="sxs-lookup"><span data-stu-id="5cad2-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="5cad2-343">請不要擔心找不到 **SceneOrganiser** 類別的錯誤，您將在下一章中建立它。</span><span class="sxs-lookup"><span data-stu-id="5cad2-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="5cad2-344">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="5cad2-345">第9章-建立 SceneOrganiser 類別</span><span class="sxs-lookup"><span data-stu-id="5cad2-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="5cad2-346">此類別將會：</span><span class="sxs-lookup"><span data-stu-id="5cad2-346">This class will:</span></span>

-   <span data-ttu-id="5cad2-347">藉由將適當的元件附加至 *主要攝影機* 來設定。</span><span class="sxs-lookup"><span data-stu-id="5cad2-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="5cad2-348">當偵測到物件時，它會負責計算其在真實世界中的位置，並使用適當的 **標記名稱** 將 **標記標籤** 放在其附近。</span><span class="sxs-lookup"><span data-stu-id="5cad2-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="5cad2-349">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="5cad2-349">To create this class:</span></span>

1.  <span data-ttu-id="5cad2-350">在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="5cad2-351">將腳本命名為 **SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="5cad2-352">按兩下新的 **SceneOrganiser** 腳本，以 **Visual Studio 開啟。**</span><span class="sxs-lookup"><span data-stu-id="5cad2-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="5cad2-353">請確定您在 **SceneOrganiser** 類別上方參考了下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="5cad2-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="5cad2-354">然後，在 **SceneOrganiser** 類別內，于 **Start ()** 方法的上方新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="5cad2-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="5cad2-355">刪除 [ **開始 ()** ]，並 **更新 ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="5cad2-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="5cad2-356">在變數底下，加入 **喚醒的 ()** 方法，這會初始化類別並設定場景。</span><span class="sxs-lookup"><span data-stu-id="5cad2-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="5cad2-357">新增 **PlaceAnalysisLabel ()** 方法，這個方法會在場景中具現 *化* 標籤 (這一點不會讓使用者) 看不見。</span><span class="sxs-lookup"><span data-stu-id="5cad2-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="5cad2-358">此外，它也會將四個 (也不可見，) 影像放置位置，並與真實世界重迭。</span><span class="sxs-lookup"><span data-stu-id="5cad2-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="5cad2-359">這點很重要，因為在分析之後從服務中取出的方塊座標會追溯到這個四個，以判定物件在真實世界中的大概位置。</span><span class="sxs-lookup"><span data-stu-id="5cad2-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="5cad2-360">新增 **FinaliseLabel ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="5cad2-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="5cad2-361">它負責：</span><span class="sxs-lookup"><span data-stu-id="5cad2-361">It is responsible for:</span></span>

    *   <span data-ttu-id="5cad2-362">以具有最高信賴度的預測 *標記* 來設定 *標籤* 文字。</span><span class="sxs-lookup"><span data-stu-id="5cad2-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="5cad2-363">呼叫四個物件的周 *框* 方塊計算，並在先前定位，並將標籤放置在場景中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="5cad2-364">使用 Raycast 朝向周 *框* 方塊來調整標籤深度，這應該會與真實世界中的物件發生衝突。</span><span class="sxs-lookup"><span data-stu-id="5cad2-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="5cad2-365">重設 capture 進程，讓使用者可以捕獲另一個映射。</span><span class="sxs-lookup"><span data-stu-id="5cad2-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="5cad2-366">新增 **CalculateBoundingBoxPosition ()** 方法，它會裝載一些需要的計算，以轉譯從服務抓取的周 *框* 方塊座標，並在四個按比例重新建立。</span><span class="sxs-lookup"><span data-stu-id="5cad2-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="5cad2-367">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5cad2-368">繼續之前，請先開啟 **CustomVisionAnalyser** 類別，然後在 **AnalyseLastImageCaptured ()** 方法中，將下列幾行 *取消* 批註：</span><span class="sxs-lookup"><span data-stu-id="5cad2-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="5cad2-369">不要擔心 **ImageCapture** 類別「找不到」訊息，您將在下一章中建立它。</span><span class="sxs-lookup"><span data-stu-id="5cad2-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="5cad2-370">第10章-建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="5cad2-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="5cad2-371">您即將建立的下一個類別是 **ImageCapture** 類別。</span><span class="sxs-lookup"><span data-stu-id="5cad2-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="5cad2-372">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="5cad2-372">This class is responsible for:</span></span>

*   <span data-ttu-id="5cad2-373">使用 HoloLens 攝影機來捕捉影像，並將它儲存在 *應用程式* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="5cad2-374">處理使用者的 *點擊* 手勢。</span><span class="sxs-lookup"><span data-stu-id="5cad2-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="5cad2-375">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="5cad2-375">To create this class:</span></span>

1.  <span data-ttu-id="5cad2-376">移至您先前建立的 **腳本** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5cad2-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="5cad2-377">在資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="5cad2-378">將腳本命名為 **ImageCapture**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="5cad2-379">按兩下新的 **ImageCapture** 腳本，以 **Visual Studio 開啟。**</span><span class="sxs-lookup"><span data-stu-id="5cad2-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="5cad2-380">以下列內容取代檔案頂端的命名空間：</span><span class="sxs-lookup"><span data-stu-id="5cad2-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="5cad2-381">然後，在 **ImageCapture** 類別內，于 **Start ()** 方法的上方新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="5cad2-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="5cad2-382">現在需要新增 **喚醒 ()** 和 **啟動 ()** 方法的程式碼：</span><span class="sxs-lookup"><span data-stu-id="5cad2-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="5cad2-383">執行將在點一下手勢發生時呼叫的處理常式：</span><span class="sxs-lookup"><span data-stu-id="5cad2-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="5cad2-384">當游標為 **綠色** 時，表示相機可用來取得影像。</span><span class="sxs-lookup"><span data-stu-id="5cad2-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="5cad2-385">當游標是 **紅色** 時，表示相機正在忙碌中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="5cad2-386">新增應用程式用來啟動映射捕獲進程的方法，並儲存映射：</span><span class="sxs-lookup"><span data-stu-id="5cad2-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  <span data-ttu-id="5cad2-387">新增在拍攝相片時所要呼叫的處理常式，並在準備進行分析時進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="5cad2-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="5cad2-388">結果接著會傳遞至 **CustomVisionAnalyser** 進行分析。</span><span class="sxs-lookup"><span data-stu-id="5cad2-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="5cad2-389">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="5cad2-390">第11章-在場景中設定腳本</span><span class="sxs-lookup"><span data-stu-id="5cad2-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="5cad2-391">既然您已撰寫此專案所需的所有程式碼，就可以開始在場景中設定腳本，並在 prefabs 上設定腳本，讓它們正常運作。</span><span class="sxs-lookup"><span data-stu-id="5cad2-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="5cad2-392">在 **Unity 編輯器** 中，選取 [階層] **面板** 中的 [ **主要相機**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="5cad2-393">在 [偵測 **器] 面板** 中，選取 **主要攝影機** ，然後按一下 [ **新增元件**]，然後搜尋 **SceneOrganiser** 腳本並按兩下，以將其新增。</span><span class="sxs-lookup"><span data-stu-id="5cad2-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="5cad2-394">在 [**專案] 面板** 中，開啟 [ **Prefabs] 資料夾**，將 **標籤** 預製專案拖曳到您剛剛新增至 *主要攝影機* 之 **SceneOrganiser** 腳本中的 *卷* 標空白參考目標輸入區域，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="5cad2-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="5cad2-395">在 [階層]**面板** 中，選取 **主要攝影機** 的 **GazeCursor** 子系。</span><span class="sxs-lookup"><span data-stu-id="5cad2-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="5cad2-396">在 [偵測 **器] 面板** 中，選取 [ **GazeCursor** ]，按一下 [ **新增元件**]，然後搜尋 **GazeCursor** 腳本並按兩下，以將其新增。</span><span class="sxs-lookup"><span data-stu-id="5cad2-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="5cad2-397">同樣地，在 [階層]**面板** 中，選取 **主要攝影機** 的 **SpatialMapping** 子系。</span><span class="sxs-lookup"><span data-stu-id="5cad2-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="5cad2-398">在 [偵測 **器] 面板** 中，選取 [ **SpatialMapping** ]，按一下 [ **新增元件**]，然後搜尋 **SpatialMapping** 腳本並按兩下，以將其新增。</span><span class="sxs-lookup"><span data-stu-id="5cad2-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="5cad2-399">**SceneOrganiser** 腳本中的程式碼會在執行時間期間，新增您未設定的其餘腳本。</span><span class="sxs-lookup"><span data-stu-id="5cad2-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="5cad2-400">第12章-建立前</span><span class="sxs-lookup"><span data-stu-id="5cad2-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="5cad2-401">若要執行應用程式的完整測試，您必須將它側載到您的 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5cad2-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="5cad2-402">在執行之前，請確定：</span><span class="sxs-lookup"><span data-stu-id="5cad2-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="5cad2-403">[第3章](#chapter-3---set-up-the-unity-project)中所述的所有設定都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="5cad2-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="5cad2-404">腳本 **SceneOrganiser** 會附加至 **主要攝影機** 物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="5cad2-405">腳本 **GazeCursor** 會附加到 **GazeCursor** 物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="5cad2-406">腳本 **SpatialMapping** 會附加到 **SpatialMapping** 物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="5cad2-407">在第 [5 章](#chapter-5---create-the-customvisionanalyser-class)步驟6：</span><span class="sxs-lookup"><span data-stu-id="5cad2-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="5cad2-408">請務必將您的 **服務預測金鑰** 插入 **predictionKey** 變數中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="5cad2-409">您已將 **預測端點** 插入至 **predictionEndpoint** 類別。</span><span class="sxs-lookup"><span data-stu-id="5cad2-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="5cad2-410">第13章-建立 UWP 解決方案並側載您的應用程式</span><span class="sxs-lookup"><span data-stu-id="5cad2-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="5cad2-411">您現在已準備好將您的應用程式建立為 UWP 解決方案，您將能夠部署至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5cad2-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="5cad2-412">若要開始建立程式：</span><span class="sxs-lookup"><span data-stu-id="5cad2-412">To begin the build process:</span></span>

1.  <span data-ttu-id="5cad2-413">移至 [檔案 **> 組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="5cad2-414">勾選 **Unity C \# 專案**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="5cad2-415">按一下 [ **新增開啟的場景**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="5cad2-416">這會將目前開啟的場景加入組建中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="5cad2-417">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-417">Click **Build**.</span></span> <span data-ttu-id="5cad2-418">Unity 將會啟動一個 *檔案總管* 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5cad2-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="5cad2-419">立即建立該資料夾，並命名為 **應用程式**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="5cad2-420">然後選取 [ **應用程式** ] 資料夾，然後按一下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="5cad2-421">Unity 將開始將您的專案建立到 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5cad2-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="5cad2-422">Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="5cad2-423">若要部署到 Microsoft HoloLens，您將需要該裝置的 IP 位址 (用於遠端部署) ，並確定它也已設定 **開發人員模式** 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="5cad2-424">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="5cad2-424">To do this:</span></span>

    1.  <span data-ttu-id="5cad2-425">在設置 HoloLens 的同時，開啟 **設定**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="5cad2-426">前往 **Network & Internet**  >  **wi-fi**  >  **Advanced Options**</span><span class="sxs-lookup"><span data-stu-id="5cad2-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="5cad2-427">記下 **IPv4** 位址。</span><span class="sxs-lookup"><span data-stu-id="5cad2-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="5cad2-428">接下來，流覽回到 [**設定**]，然後 **更新**  >  **開發人員 & 的** 安全性</span><span class="sxs-lookup"><span data-stu-id="5cad2-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="5cad2-429">設定 [**開發人員模式]** *。*</span><span class="sxs-lookup"><span data-stu-id="5cad2-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="5cad2-430">流覽至您的新 Unity 組建 (**應用程式** 資料夾) ，然後以 **Visual Studio** 開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="5cad2-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="5cad2-431">在 [方案設定] 中選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="5cad2-432">在解決方案平臺中，選取 [ **x86]、[遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="5cad2-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="5cad2-433">系統會提示您 (Microsoft HoloLens 中插入遠端裝置的 **IP 位址** ，在此案例中，您記) 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="5cad2-434">移至 [ **組建** ] 功能表，然後按一下 [ **部署方案** ]，將應用程式側載至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5cad2-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="5cad2-435">您的應用程式現在應該會出現在您 Microsoft HoloLens 上已安裝的應用程式清單中，準備好可供啟動！</span><span class="sxs-lookup"><span data-stu-id="5cad2-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="5cad2-436">若要使用應用程式：</span><span class="sxs-lookup"><span data-stu-id="5cad2-436">To use the application:</span></span>

* <span data-ttu-id="5cad2-437">查看您使用 **Azure 自訂視覺服務（物件偵測**）定型的物件，並使用 **點擊手勢**。</span><span class="sxs-lookup"><span data-stu-id="5cad2-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="5cad2-438">如果成功偵測到物件，則會出現具有標記名稱的全球空間 *標籤文字* 。</span><span class="sxs-lookup"><span data-stu-id="5cad2-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cad2-439">每次您捕獲相片並將其傳送至服務時，您可以返回 [服務] 頁面，然後以新捕獲的影像重新定型服務。</span><span class="sxs-lookup"><span data-stu-id="5cad2-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="5cad2-440">一開始，您可能也必須更正周 *框方塊* ，以更精確地重新定型服務。</span><span class="sxs-lookup"><span data-stu-id="5cad2-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="5cad2-441">當 Unity 中的 Microsoft HoloLens 感應器和/或 SpatialTrackingComponent 無法放置適當的 colliders （相對於真實世界的物件）時，放置的標籤文字可能不會出現在物件附近。</span><span class="sxs-lookup"><span data-stu-id="5cad2-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="5cad2-442">如果是這種情況，請嘗試在不同的介面上使用應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cad2-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="5cad2-443">您自訂視覺的物件偵測應用程式</span><span class="sxs-lookup"><span data-stu-id="5cad2-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="5cad2-444">恭喜，您已建立混合的現實應用程式，以利用 Azure 自訂視覺的物件偵測 API，該 API 可辨識影像中的物件，然後在3D 空間中為該物件提供大約的位置。</span><span class="sxs-lookup"><span data-stu-id="5cad2-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="5cad2-445">額外練習</span><span class="sxs-lookup"><span data-stu-id="5cad2-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="5cad2-446">練習1</span><span class="sxs-lookup"><span data-stu-id="5cad2-446">Exercise 1</span></span>

<span data-ttu-id="5cad2-447">加入至文字標籤時，請使用半透明 cube，將真實物件包裝在3D 周 *框* 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5cad2-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="5cad2-448">練習2</span><span class="sxs-lookup"><span data-stu-id="5cad2-448">Exercise 2</span></span>

<span data-ttu-id="5cad2-449">訓練您的自訂視覺服務，以辨識更多物件。</span><span class="sxs-lookup"><span data-stu-id="5cad2-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="5cad2-450">練習3</span><span class="sxs-lookup"><span data-stu-id="5cad2-450">Exercise 3</span></span>

<span data-ttu-id="5cad2-451">辨識物件時播放音效。</span><span class="sxs-lookup"><span data-stu-id="5cad2-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="5cad2-452">練習4</span><span class="sxs-lookup"><span data-stu-id="5cad2-452">Exercise 4</span></span>

<span data-ttu-id="5cad2-453">使用 API 以您的應用程式所分析的相同影像來重新定型您的服務，以便讓服務更準確 (同時) 預測和定型。</span><span class="sxs-lookup"><span data-stu-id="5cad2-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>