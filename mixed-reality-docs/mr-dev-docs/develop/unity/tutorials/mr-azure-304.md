---
title: HoloLens (第1代) 和 Azure 304-臉部辨識
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學院，unity，教學課程，api，臉部辨識，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 6266cb206a0686745bcd7a92f64d78436c71a228
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730505"
---
# <a name="hololens-1st-gen-and-azure-304-face-recognition"></a><span data-ttu-id="500dc-104">HoloLens (第1代) 和 Azure 304：臉部辨識</span><span class="sxs-lookup"><span data-stu-id="500dc-104">HoloLens (1st gen) and Azure 304: Face recognition</span></span>

<br>

>[!NOTE]
><span data-ttu-id="500dc-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="500dc-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="500dc-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="500dc-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="500dc-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="500dc-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="500dc-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="500dc-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="500dc-109">未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="500dc-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="500dc-110">當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。</span><span class="sxs-lookup"><span data-stu-id="500dc-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

![完成本課程的結果](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="500dc-112">在此課程中，您將瞭解如何使用 Azure 認知服務搭配 Microsoft 臉部 API，將臉部辨識功能新增至混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="500dc-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="500dc-113">*Azure 臉部 API* 是一項 Microsoft 服務，可為開發人員提供最先進的臉部演算法，全都在雲端中。</span><span class="sxs-lookup"><span data-stu-id="500dc-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="500dc-114">*臉部 API* 有兩個主要功能：使用屬性進行臉部偵測，以及臉部辨識。</span><span class="sxs-lookup"><span data-stu-id="500dc-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="500dc-115">這可讓開發人員只為臉部設定一組群組，然後在稍後將查詢影像傳送至服務，以判斷臉部所屬的人。</span><span class="sxs-lookup"><span data-stu-id="500dc-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="500dc-116">如需詳細資訊，請造訪 [Azure 臉部辨識頁面](https://azure.microsoft.com/services/cognitive-services/face/)。</span><span class="sxs-lookup"><span data-stu-id="500dc-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="500dc-117">完成本課程之後，您將會有混合現實 HoloLens 應用程式，它將能夠執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="500dc-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="500dc-118">您可以使用點一下 **手勢** 來起始使用板載 HoloLens 攝影機的影像抓取。</span><span class="sxs-lookup"><span data-stu-id="500dc-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="500dc-119">將已捕獲的映射傳送至 *Azure 臉部 API* 服務。</span><span class="sxs-lookup"><span data-stu-id="500dc-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="500dc-120">接收 *臉部 API* 演算法的結果。</span><span class="sxs-lookup"><span data-stu-id="500dc-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="500dc-121">使用簡單的消費者介面，以顯示相符人員的名稱。</span><span class="sxs-lookup"><span data-stu-id="500dc-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="500dc-122">這將告訴您如何將臉部 API 服務的結果取得至 Unity 型混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="500dc-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="500dc-123">在您的應用程式中，您可以自行決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="500dc-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="500dc-124">本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="500dc-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="500dc-125">您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="500dc-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="500dc-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="500dc-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="500dc-127">課程</span><span class="sxs-lookup"><span data-stu-id="500dc-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="500dc-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="500dc-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="500dc-129"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="500dc-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="500dc-130">MR 和 Azure 304：臉部辨識</span><span class="sxs-lookup"><span data-stu-id="500dc-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="500dc-131">✔️</span><span class="sxs-lookup"><span data-stu-id="500dc-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="500dc-132">✔️</span><span class="sxs-lookup"><span data-stu-id="500dc-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="500dc-133">雖然本課程主要著重于 HoloLens，您也可以將本課程中所學到的內容套用到 Windows Mixed Reality 沉浸式 (VR) 耳機。</span><span class="sxs-lookup"><span data-stu-id="500dc-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="500dc-134">因為沉浸式 (VR) 耳機沒有可存取的攝影機，所以您需要有連接到電腦的外部攝影機。</span><span class="sxs-lookup"><span data-stu-id="500dc-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="500dc-135">當您依照課程的指示，您將會看到有關您可能需要採用以支援沉浸式 (VR) 耳機的任何變更的注意事項。</span><span class="sxs-lookup"><span data-stu-id="500dc-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="500dc-136">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="500dc-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="500dc-137">本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="500dc-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="500dc-138">另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="500dc-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="500dc-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span><span class="sxs-lookup"><span data-stu-id="500dc-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="500dc-140">本課程建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="500dc-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="500dc-141">開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)</span><span class="sxs-lookup"><span data-stu-id="500dc-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="500dc-142">啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="500dc-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="500dc-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="500dc-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="500dc-144">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="500dc-144">Unity 2017.4</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="500dc-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="500dc-145">Visual Studio 2017</span></span>](../../install-the-tools.md)
- <span data-ttu-id="500dc-146">[Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="500dc-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="500dc-147">連接到您 PC (的攝影機，適用于沉浸式耳機開發) </span><span class="sxs-lookup"><span data-stu-id="500dc-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="500dc-148">適用于 Azure 安裝程式和臉部 API 抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="500dc-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="500dc-149">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="500dc-149">Before you start</span></span>

1.  <span data-ttu-id="500dc-150">為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="500dc-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="500dc-151">設定及測試 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="500dc-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="500dc-152">如果您需要設定 HoloLens 的支援， [請務必造訪 HoloLens 安裝文章](/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="500dc-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="500dc-153">開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助針對每個使用者) 執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="500dc-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="500dc-154">如需有關校正的說明，請遵循此 [與 HoloLens 校正文章相關的連結](/hololens/hololens-calibration#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="500dc-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="500dc-155">如需有關感應器微調的說明，請依照此 [連結來進行「HoloLens 感應器微調」文章](/hololens/hololens-updates)。</span><span class="sxs-lookup"><span data-stu-id="500dc-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="500dc-156">第1章-Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="500dc-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="500dc-157">若要在 Azure 中使用 *臉部 API* 服務，您必須將服務的實例設定為可供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="500dc-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="500dc-158">首先，登入 [Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="500dc-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="500dc-159">如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="500dc-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="500dc-160">如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="500dc-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="500dc-161">登入後，按一下左上角的 [ **新增** ]，然後搜尋 *臉部 API*，按 **enter**。</span><span class="sxs-lookup"><span data-stu-id="500dc-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![搜尋臉部 api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="500dc-163">在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。</span><span class="sxs-lookup"><span data-stu-id="500dc-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="500dc-164">新頁面將提供 *臉部 API* 服務的描述。</span><span class="sxs-lookup"><span data-stu-id="500dc-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="500dc-165">在此提示的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="500dc-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![臉部 api 資訊](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="500dc-167">當您按一下 [ **建立**] 之後：</span><span class="sxs-lookup"><span data-stu-id="500dc-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="500dc-168">為此服務實例插入您想要的名稱。</span><span class="sxs-lookup"><span data-stu-id="500dc-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="500dc-169">選取一個訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="500dc-169">Select a subscription.</span></span>

    3. <span data-ttu-id="500dc-170">選取適合您的定價層，如果這是您第一次建立 *臉部 API 服務*，則應可使用名為 F0) 的免費層 (。</span><span class="sxs-lookup"><span data-stu-id="500dc-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="500dc-171">選擇資源群組，或建立一個新的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="500dc-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="500dc-172">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="500dc-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="500dc-173">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。</span><span class="sxs-lookup"><span data-stu-id="500dc-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="500dc-174">如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="500dc-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="500dc-175">您稍後使用的 UWP 應用程式（ **Person Maker**）需要使用「美國西部」作為位置。</span><span class="sxs-lookup"><span data-stu-id="500dc-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="500dc-176">您也必須確認您已瞭解套用到此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="500dc-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="500dc-177">選取 [ \**建立 *]。**</span><span class="sxs-lookup"><span data-stu-id="500dc-177">Select **Create\*.**</span></span>

        ![建立臉部 api 服務](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="500dc-179">按一下 [ **建立] \* 之後，** 您必須等候服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="500dc-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="500dc-180">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="500dc-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![服務建立通知](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="500dc-182">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="500dc-182">Click on the notifications to explore your new Service instance.</span></span>

    ![前往資源通知](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="500dc-184">當您準備好時，請按一下通知中的 [ **移至資源** ] 按鈕，以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="500dc-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![存取臉部 api 金鑰](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="500dc-186">在本教學課程中，您的應用程式必須呼叫您的服務，這是透過使用您服務的訂用帳戶「金鑰」來完成。</span><span class="sxs-lookup"><span data-stu-id="500dc-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="500dc-187">從您 *臉部 API* 服務的 [*快速入門*] 頁面中，第一個點是編號1，以 *抓取您的金鑰。*</span><span class="sxs-lookup"><span data-stu-id="500dc-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="500dc-188">在 [ *服務* ] 頁面上，選取 [快速入門] 頁面上的 [藍色 **按鍵** ] 超連結 (如果) ，或 (左邊的 [服務] 導覽功能表中的 [ **金鑰** ] 連結) ，則會顯示您的金鑰。</span><span class="sxs-lookup"><span data-stu-id="500dc-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="500dc-189">請記下其中一個金鑰並加以保護，因為您稍後將會用到。</span><span class="sxs-lookup"><span data-stu-id="500dc-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="500dc-190">第2章-使用「Person Maker」 UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="500dc-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="500dc-191">請務必下載稱為 [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)的預建 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="500dc-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="500dc-192">此應用程式不是此課程的結束產品，只是協助您建立 Azure 專案的工具，稍後的專案將會依賴此工具。</span><span class="sxs-lookup"><span data-stu-id="500dc-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="500dc-193">**Person Maker** 可讓您建立與人員和人員群組相關聯的 Azure 專案。</span><span class="sxs-lookup"><span data-stu-id="500dc-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="500dc-194">應用程式會將所有必要的資訊都放在稍後供 FaceAPI 使用的格式中，以便辨識您已新增的人員臉部。</span><span class="sxs-lookup"><span data-stu-id="500dc-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="500dc-195">須知 **Person Maker** 會使用一些基本的節流，以協助確保您不會超過 **免費訂** 用帳戶層的每分鐘服務呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="500dc-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="500dc-196">當節流發生時，頂端的綠色文字會變更為紅色，並更新為「作用中」。如果發生這種情況，只要等候應用程式 (它就會等到它可以繼續存取臉部辨識服務，然後在) 時更新為「主動」。</span><span class="sxs-lookup"><span data-stu-id="500dc-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="500dc-197">此應用程式會使用 *>microsoft.projectoxford.face* 程式庫，可讓您充分利用臉部 API。</span><span class="sxs-lookup"><span data-stu-id="500dc-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="500dc-198">此程式庫可免費作為 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="500dc-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="500dc-199">如需此程式和類似 Api 的詳細資訊， [請務必造訪 api 參考文章](/azure/cognitive-services/face/apireference)。</span><span class="sxs-lookup"><span data-stu-id="500dc-199">For more information about this, and similar, APIs [make sure to visit the API reference article](/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="500dc-200">這些只是所需的步驟，也就是如何執行這些作業的指示。</span><span class="sxs-lookup"><span data-stu-id="500dc-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="500dc-201">**Person Maker** 應用程式可讓您：</span><span class="sxs-lookup"><span data-stu-id="500dc-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="500dc-202">建立 *人員群組*，此群組是由數個您想要與其相關聯的人員所組成。</span><span class="sxs-lookup"><span data-stu-id="500dc-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="500dc-203">使用您的 Azure 帳戶，您可以裝載多個人員群組。</span><span class="sxs-lookup"><span data-stu-id="500dc-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="500dc-204">建立 *person*，這是 person 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="500dc-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="500dc-205">每個人都有許多相關聯的 *臉部* 影像。</span><span class="sxs-lookup"><span data-stu-id="500dc-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="500dc-206">將 *臉部影像* 指派給 *人員*，以允許您的 Azure 臉部 API 服務依據對應的 *臉部* 辨識 *人員*。</span><span class="sxs-lookup"><span data-stu-id="500dc-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="500dc-207">*訓練* 您的 *Azure 臉部 API 服務*。</span><span class="sxs-lookup"><span data-stu-id="500dc-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="500dc-208">請注意，若要將此應用程式定型以辨識人員，您將需要 10 (10) 您想要新增至人員群組的每個人的近接相片。</span><span class="sxs-lookup"><span data-stu-id="500dc-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="500dc-209">Windows 10 凸輪應用程式可協助您進行這些工作。</span><span class="sxs-lookup"><span data-stu-id="500dc-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="500dc-210">您必須確保每個相片都清楚明瞭 (避免模糊、遮蔽或太遠，從主題) ，以 jpg 或 png 檔案格式的相片，而且影像檔案的大小不會超過 **4 MB**，而且不小於 **1 KB**。</span><span class="sxs-lookup"><span data-stu-id="500dc-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="500dc-211">如果您遵循本教學課程，請勿使用您自己的臉部進行訓練，如同當您將 HoloLens 放在時一樣，您無法自行查看。</span><span class="sxs-lookup"><span data-stu-id="500dc-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="500dc-212">使用同事或學生的臉部。</span><span class="sxs-lookup"><span data-stu-id="500dc-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="500dc-213">正在執行 **Person Maker**：</span><span class="sxs-lookup"><span data-stu-id="500dc-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="500dc-214">開啟 [ **PersonMaker** ] 資料夾，然後按兩下 [ *PersonMaker] 方案* ，以 *Visual Studio* 開啟該資料夾。</span><span class="sxs-lookup"><span data-stu-id="500dc-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="500dc-215">*PersonMaker 解決方案* 開啟後，請確定：</span><span class="sxs-lookup"><span data-stu-id="500dc-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="500dc-216">*解決方案* 設定會設定為 **Debug**。</span><span class="sxs-lookup"><span data-stu-id="500dc-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="500dc-217">*解決方案平臺* 設定為 **x86**</span><span class="sxs-lookup"><span data-stu-id="500dc-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="500dc-218">*目標平臺* 是 **本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="500dc-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="500dc-219">您也可能需要 *還原 Nuget 套件* (在 *解決方案* 上按一下滑鼠右鍵，然後選取 [ **還原 nuget 套件** ]) 。</span><span class="sxs-lookup"><span data-stu-id="500dc-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="500dc-220">按一下 [ *本機電腦* ]，應用程式就會啟動。</span><span class="sxs-lookup"><span data-stu-id="500dc-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="500dc-221">請注意，在較小的螢幕上，所有內容都可能無法顯示，不過您可以進一步向下移動以查看。</span><span class="sxs-lookup"><span data-stu-id="500dc-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![person maker 使用者介面](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="500dc-223">從 Azure 內的 *臉部 API* 服務插入您的 **azure 驗證金鑰**。</span><span class="sxs-lookup"><span data-stu-id="500dc-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="500dc-224">插入：</span><span class="sxs-lookup"><span data-stu-id="500dc-224">Insert:</span></span>

    1. <span data-ttu-id="500dc-225">您要指派給 *Person 群組* 的 *識別碼*。</span><span class="sxs-lookup"><span data-stu-id="500dc-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="500dc-226">識別碼必須是小寫，而且沒有空格。</span><span class="sxs-lookup"><span data-stu-id="500dc-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="500dc-227">請記下此識別碼，因為稍後會在您的 Unity 專案中需要此識別碼。</span><span class="sxs-lookup"><span data-stu-id="500dc-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="500dc-228">您要指派給 *Person 群組* (的 *名稱* 可以有空格) 。</span><span class="sxs-lookup"><span data-stu-id="500dc-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="500dc-229">按下 [ **建立人員群組** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="500dc-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="500dc-230">確認訊息應該會出現在按鈕下方。</span><span class="sxs-lookup"><span data-stu-id="500dc-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="500dc-231">如果您有「拒絕存取」錯誤，請檢查您為 Azure 服務設定的位置。</span><span class="sxs-lookup"><span data-stu-id="500dc-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="500dc-232">如上所述，此應用程式是針對「美國西部」所設計。</span><span class="sxs-lookup"><span data-stu-id="500dc-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="500dc-233">您將會注意到，您也可以按一下 [ **提取已知的群組** ] 按鈕：如果您已經建立人員群組，且想要使用該群組，而不是建立新的群組，您也可以使用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="500dc-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="500dc-234">請注意，如果您按一下 [建立具有已知群組的 *人員群組* ]，這也會提取群組。</span><span class="sxs-lookup"><span data-stu-id="500dc-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="500dc-235">插入您想要建立之 *人員* 的 *名稱*。</span><span class="sxs-lookup"><span data-stu-id="500dc-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="500dc-236">按一下 [ **建立人員** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="500dc-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="500dc-237">確認訊息應該會出現在按鈕下方。</span><span class="sxs-lookup"><span data-stu-id="500dc-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="500dc-238">如果您想要刪除先前建立的人員，可以將名稱寫入文字方塊中，然後按 [**刪除人員**]</span><span class="sxs-lookup"><span data-stu-id="500dc-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="500dc-239">確定您知道想要新增至群組之人員的 10 (10) 相片的位置。</span><span class="sxs-lookup"><span data-stu-id="500dc-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="500dc-240">按下 [ **建立] 和 [開啟資料夾** ] 以開啟與該人員相關聯之資料夾的 Windows 檔案總管。</span><span class="sxs-lookup"><span data-stu-id="500dc-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="500dc-241">將 10 (10) 影像新增至資料夾。</span><span class="sxs-lookup"><span data-stu-id="500dc-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="500dc-242">這些必須是 *JPG* 或 *PNG* 檔案格式。</span><span class="sxs-lookup"><span data-stu-id="500dc-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="500dc-243">按一下 [ **提交至 Azure**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="500dc-244">計數器會顯示提交的狀態，後面接著訊息完成時的訊息。</span><span class="sxs-lookup"><span data-stu-id="500dc-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="500dc-245">一旦計數器完成，並顯示確認訊息，請按一下 [ **定型** ] 以定型您的服務。</span><span class="sxs-lookup"><span data-stu-id="500dc-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="500dc-246">程式完成之後，您就可以開始移至 Unity。</span><span class="sxs-lookup"><span data-stu-id="500dc-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="500dc-247">第3章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="500dc-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="500dc-248">以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="500dc-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="500dc-249">開啟 *Unity* ，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-249">Open *Unity* and click **New**.</span></span> 

    ![開始新的 Unity 專案。](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="500dc-251">您現在將需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="500dc-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="500dc-252">插入 **MR_FaceRecognition**。</span><span class="sxs-lookup"><span data-stu-id="500dc-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="500dc-253">請確定專案類型設定為 **3d**。</span><span class="sxs-lookup"><span data-stu-id="500dc-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="500dc-254">將 **位置** 設定為適合您 (記住，較接近根目錄的) 。</span><span class="sxs-lookup"><span data-stu-id="500dc-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="500dc-255">然後，按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-255">Then, click **Create project**.</span></span>

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="500dc-257">在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="500dc-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="500dc-258">移至 [ **編輯] > 喜好** 設定，然後在新視窗中，流覽至 [ **外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="500dc-259">將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="500dc-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="500dc-260">關閉 [ **喜好** 設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="500dc-260">Close the **Preferences** window.</span></span>

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="500dc-262">接著，移至 [檔案 **> 組建設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至 **通用 Windows 平臺**。</span><span class="sxs-lookup"><span data-stu-id="500dc-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![[組建設定] 視窗，將平臺切換至 UWP。](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="500dc-264">移至 [檔案 **> 組建設定** ]，並確定：</span><span class="sxs-lookup"><span data-stu-id="500dc-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="500dc-265">**目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="500dc-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="500dc-266">針對沉浸式耳機，將 **目標裝置** 設為 *任何裝置*。</span><span class="sxs-lookup"><span data-stu-id="500dc-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="500dc-267">**組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="500dc-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="500dc-268">**SDK** 已設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="500dc-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="500dc-269">**Visual Studio 版本** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="500dc-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="500dc-270">**組建並執行** 設定為 **本機電腦**</span><span class="sxs-lookup"><span data-stu-id="500dc-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="500dc-271">儲存場景，並將其新增至組建。</span><span class="sxs-lookup"><span data-stu-id="500dc-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="500dc-272">若要這麼做，請選取 [ **新增開啟的場景**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="500dc-273">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="500dc-273">A save window will appear.</span></span>

            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="500dc-275">選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。</span><span class="sxs-lookup"><span data-stu-id="500dc-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的腳本資料夾](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="500dc-277">開啟新建立的 **場景** 資料夾，然後在 [ **檔案名**：文字] 欄位中輸入 **FaceRecScene**，然後按 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![提供新場景的名稱。](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="500dc-279">[ *組建設定*] 中的其餘設定，現在應該保持為預設值。</span><span class="sxs-lookup"><span data-stu-id="500dc-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="500dc-280">在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。</span><span class="sxs-lookup"><span data-stu-id="500dc-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟 [播放玩家設定]。](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="500dc-282">在此面板中，需要驗證幾個設定：</span><span class="sxs-lookup"><span data-stu-id="500dc-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="500dc-283">在 [ **其他設定** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="500dc-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="500dc-284">**腳本\*\*\*\*執行階段版本** 應該是 **實驗** ( .net 4.6 對等) 。</span><span class="sxs-lookup"><span data-stu-id="500dc-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="500dc-285">變更此變更將會觸發重新開機編輯器的需求。</span><span class="sxs-lookup"><span data-stu-id="500dc-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="500dc-286">**腳本後端** 應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="500dc-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="500dc-287">**API 相容性層級** 應為 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="500dc-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="500dc-289">在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：</span><span class="sxs-lookup"><span data-stu-id="500dc-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="500dc-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="500dc-290">**InternetClient**</span></span>
        - <span data-ttu-id="500dc-291">**網路攝影機**</span><span class="sxs-lookup"><span data-stu-id="500dc-291">**Webcam**</span></span>

            ![正在更新發行設定。](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="500dc-293">在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="500dc-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 設定。](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="500dc-295">回到 *組建設定*， **Unity c # 專案** 不再呈現灰色;勾選此方塊旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="500dc-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="500dc-296">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="500dc-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="500dc-297">將場景和專案儲存 (檔 **> 儲存場景/檔案 > 儲存專案**) 。</span><span class="sxs-lookup"><span data-stu-id="500dc-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="500dc-298">第4章-主要攝影機設定</span><span class="sxs-lookup"><span data-stu-id="500dc-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="500dc-299">如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意 [下載 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)，並將它匯入至您的專案中做為 [自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="500dc-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="500dc-300">請注意，此套件也包含 *NEWTONSOFT DLL* 的匯入，如 [第5章](#chapter-5--import-the-newtonsoftjson-library)所述。</span><span class="sxs-lookup"><span data-stu-id="500dc-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoftjson-library).</span></span> <span data-ttu-id="500dc-301">匯入之後，您可以從 [第6章](#chapter-6---create-the-faceanalysis-class)繼續。</span><span class="sxs-lookup"><span data-stu-id="500dc-301">With this imported, you can continue from [Chapter 6](#chapter-6---create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="500dc-302">*在 [階層] 面板中*，選取 [**主要相機**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="500dc-303">一旦選取之後，您就可以在 [偵測 *器] 面板* 中看到 **主要攝影機** 的所有元件。</span><span class="sxs-lookup"><span data-stu-id="500dc-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="500dc-304">**攝影機物件** 必須命名為 **主要攝影機** (請注意拼寫！ ) </span><span class="sxs-lookup"><span data-stu-id="500dc-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="500dc-305">主要攝影機 **標記** 必須設定為 **MainCamera** (注意拼寫！ ) </span><span class="sxs-lookup"><span data-stu-id="500dc-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="500dc-306">請確定 **轉換位置** 設定為 **0、0、0**</span><span class="sxs-lookup"><span data-stu-id="500dc-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="500dc-307">將純文字 **旗標** 設為 **純色**</span><span class="sxs-lookup"><span data-stu-id="500dc-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="500dc-308">將相機元件的 **背景** 色彩設定為 **黑色、Alpha 0 (Hex 碼： #00000000)**</span><span class="sxs-lookup"><span data-stu-id="500dc-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![設定攝影機元件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="500dc-310">第5章–匯入程式庫上的 Newtonsoft.Js</span><span class="sxs-lookup"><span data-stu-id="500dc-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="500dc-311">如果您在 [上一章](#chapter-4---main-camera-setup)匯入了 '. unitypackage '，您可以跳過這一章。</span><span class="sxs-lookup"><span data-stu-id="500dc-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4---main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="500dc-312">為了協助您還原序列化和序列化接收和傳送至 Bot 服務的物件，您需要下載程式庫 *上的Newtonsoft.Js* 。</span><span class="sxs-lookup"><span data-stu-id="500dc-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="500dc-313">您會在此 [Unity 套件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)檔案中找到已使用正確 unity 資料夾結構組織的相容版本。</span><span class="sxs-lookup"><span data-stu-id="500dc-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="500dc-314">匯入程式庫：</span><span class="sxs-lookup"><span data-stu-id="500dc-314">To import the library:</span></span>

1.  <span data-ttu-id="500dc-315">下載 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="500dc-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="500dc-316">按一下 [ **資產**]、[匯 **入封裝**]、[ **自訂套件**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![匯入 Newtonsoft.Js開啟](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="500dc-318">尋找您已下載的 Unity 套件，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="500dc-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="500dc-319">請確定封裝的所有元件都是核取，然後按一下 [匯 **入**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![匯入資產上的 Newtonsoft.Js](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="500dc-321">第6章-建立 FaceAnalysis 類別</span><span class="sxs-lookup"><span data-stu-id="500dc-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="500dc-322">FaceAnalysis 類別的目的是裝載與您的 Azure 臉部辨識服務通訊所需的方法。</span><span class="sxs-lookup"><span data-stu-id="500dc-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="500dc-323">將服務傳送至 capture 映射之後，它會分析並識別其中的臉部，並判斷是否有任何人屬於已知人員。</span><span class="sxs-lookup"><span data-stu-id="500dc-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="500dc-324">如果找到已知人員，這個類別會將其名稱顯示為場景中的 UI 文字。</span><span class="sxs-lookup"><span data-stu-id="500dc-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="500dc-325">若要建立 *FaceAnalysis* 類別：</span><span class="sxs-lookup"><span data-stu-id="500dc-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="500dc-326">以滑鼠右鍵按一下位於 [專案] 面板中的 [*資產] 資料夾*，然後按一下 [**建立**  >  **資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="500dc-327">呼叫資料夾 **腳本**。</span><span class="sxs-lookup"><span data-stu-id="500dc-327">Call the folder **Scripts**.</span></span> 

    ![建立 FaceAnalysis 類別。](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="500dc-329">按兩下剛才建立的資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="500dc-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="500dc-330">在資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="500dc-331">呼叫腳本 *FaceAnalysis*。</span><span class="sxs-lookup"><span data-stu-id="500dc-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="500dc-332">按兩下新的 *FaceAnalysis* 腳本，以 Visual Studio 2017 開啟。</span><span class="sxs-lookup"><span data-stu-id="500dc-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="500dc-333">在 *FaceAnalysis* 類別上方輸入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="500dc-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="500dc-334">您現在需要新增 deserialising 所使用的所有物件。</span><span class="sxs-lookup"><span data-stu-id="500dc-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="500dc-335">這些物件必須加入至 *FaceAnalysis* 腳本 **之外**， (在下大括弧) 下。</span><span class="sxs-lookup"><span data-stu-id="500dc-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="500dc-336">[ *開始 ()* ] 和 [ *更新 ()* ] 方法將不會使用，因此請立即將其刪除。</span><span class="sxs-lookup"><span data-stu-id="500dc-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="500dc-337">在 *FaceAnalysis* 類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="500dc-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="500dc-338">將 **金鑰** 和 **personGroupId** 取代為您的服務金鑰，以及您先前建立之群組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="500dc-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="500dc-339">新增 *喚醒的 ()* 方法，initialises 類別、將 *ImageCapture* 類別新增至主要相機，並呼叫標籤建立方法：</span><span class="sxs-lookup"><span data-stu-id="500dc-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="500dc-340">新增 *CreateLabel ()* 方法，它會建立 *標籤* 物件來顯示分析結果：</span><span class="sxs-lookup"><span data-stu-id="500dc-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="500dc-341">新增 *DetectFacesFromImage ()* 和 *GetImageAsByteArray ()* 方法。</span><span class="sxs-lookup"><span data-stu-id="500dc-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="500dc-342">前者會要求臉部辨識服務偵測提交影像中的任何可能臉部，而後者則是將捕獲的影像轉換成位元組陣列的必要條件：</span><span class="sxs-lookup"><span data-stu-id="500dc-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="500dc-343">新增 *IdentifyFaces ()* 方法，這會要求 *臉部辨識服務* 識別先前在提交的影像中偵測到的任何已知臉部。</span><span class="sxs-lookup"><span data-stu-id="500dc-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="500dc-344">要求會傳回已識別之人員的識別碼，但不會傳回名稱：</span><span class="sxs-lookup"><span data-stu-id="500dc-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="500dc-345">新增 *GetPerson ()* 方法。</span><span class="sxs-lookup"><span data-stu-id="500dc-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="500dc-346">藉由提供人員識別碼，此方法接著會要求 *臉部辨識服務* 傳回已識別人員的名稱：</span><span class="sxs-lookup"><span data-stu-id="500dc-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="500dc-347">請記得先 **儲存** 變更，然後再返回 Unity 編輯器。</span><span class="sxs-lookup"><span data-stu-id="500dc-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="500dc-348">在 Unity 編輯器中，將 FaceAnalysis 腳本從 [專案] 面板中的 [腳本] 資料夾，拖曳至 [階層] *面板* 中的 [主要攝影機] 物件。</span><span class="sxs-lookup"><span data-stu-id="500dc-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="500dc-349">新的腳本元件將會新增到主要攝影機中。</span><span class="sxs-lookup"><span data-stu-id="500dc-349">The new script component will be so added to the Main Camera.</span></span> 

![將 FaceAnalysis 放在主要攝影機上](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="500dc-351">第7章-建立 ImageCapture 類別</span><span class="sxs-lookup"><span data-stu-id="500dc-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="500dc-352">*ImageCapture* 類別的目的是裝載與您的 *Azure 臉部辨識服務* 通訊所需的方法，以分析您將會捕捉的影像、識別其中的臉部，並判斷它是否屬於已知人員。</span><span class="sxs-lookup"><span data-stu-id="500dc-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="500dc-353">如果找到已知人員，這個類別會將其名稱顯示為場景中的 UI 文字。</span><span class="sxs-lookup"><span data-stu-id="500dc-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="500dc-354">若要建立 *ImageCapture* 類別：</span><span class="sxs-lookup"><span data-stu-id="500dc-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="500dc-355">以滑鼠右鍵按一下您先前建立的 **腳本** 資料夾內部，然後按一下 [ **建立**]、[ **c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="500dc-356">呼叫腳本 *ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="500dc-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="500dc-357">按兩下新的 *ImageCapture* 腳本，以 Visual Studio 2017 開啟。</span><span class="sxs-lookup"><span data-stu-id="500dc-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="500dc-358">在 ImageCapture 類別上方輸入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="500dc-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="500dc-359">在 *ImageCapture* 類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="500dc-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="500dc-360">新增 *喚醒的 ()* ，並啟動初始化類別所需的 *()* 方法，並允許 HoloLens 捕獲使用者的手勢：</span><span class="sxs-lookup"><span data-stu-id="500dc-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="500dc-361">新增 *TapHandler ()* ，這會在使用者執行點 *按手勢時* 呼叫：</span><span class="sxs-lookup"><span data-stu-id="500dc-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="500dc-362">新增 *ExecuteImageCaptureAndAnalysis ()* 方法，這將會開始進行映射捕獲：</span><span class="sxs-lookup"><span data-stu-id="500dc-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="500dc-363">新增在完成相片抓取程式時所呼叫的處理常式：</span><span class="sxs-lookup"><span data-stu-id="500dc-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="500dc-364">請記得先 **儲存** 變更，然後再返回 Unity 編輯器。</span><span class="sxs-lookup"><span data-stu-id="500dc-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="500dc-365">第8章-建立解決方案</span><span class="sxs-lookup"><span data-stu-id="500dc-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="500dc-366">若要執行應用程式的完整測試，您必須將它側載到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="500dc-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="500dc-367">在執行之前，請確定：</span><span class="sxs-lookup"><span data-stu-id="500dc-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="500dc-368">第3章中所述的所有設定都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="500dc-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="500dc-369">腳本 *FaceAnalysis* 會附加至主要攝影機物件。</span><span class="sxs-lookup"><span data-stu-id="500dc-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="500dc-370">**驗證金鑰** 和 **群組識別碼** 都是在 *FaceAnalysis* 腳本中設定。</span><span class="sxs-lookup"><span data-stu-id="500dc-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="500dc-371">答：現在您已準備好建立解決方案。</span><span class="sxs-lookup"><span data-stu-id="500dc-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="500dc-372">一旦建立解決方案之後，您就可以開始部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="500dc-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="500dc-373">若要開始建立程式：</span><span class="sxs-lookup"><span data-stu-id="500dc-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="500dc-374">按一下 [檔案]、[儲存]，以儲存目前的場景。</span><span class="sxs-lookup"><span data-stu-id="500dc-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="500dc-375">移至 [檔案]、[組建設定]，然後按一下 [新增開啟的場景]。</span><span class="sxs-lookup"><span data-stu-id="500dc-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="500dc-376">請務必勾選 Unity c # 專案。</span><span class="sxs-lookup"><span data-stu-id="500dc-376">Make sure to tick Unity C# Projects.</span></span>

    ![部署 Visual Studio 解決方案](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="500dc-378">按下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="500dc-378">Press Build.</span></span> <span data-ttu-id="500dc-379">當您這樣做時，Unity 將會啟動一個檔案總管視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="500dc-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="500dc-380">立即在 Unity 專案中建立該資料夾，並呼叫它應用程式。</span><span class="sxs-lookup"><span data-stu-id="500dc-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="500dc-381">然後選取 [應用程式] 資料夾，然後按 [選取資料夾]。</span><span class="sxs-lookup"><span data-stu-id="500dc-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="500dc-382">Unity 將會開始建立您的專案，並將其移至應用程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="500dc-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="500dc-383">Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="500dc-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![從 Visual Studio 部署解決方案](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="500dc-385">開啟您的應用程式資料夾，然後開啟 [新增專案方案] (如上所示，MR_FaceRecognition .sln) 。</span><span class="sxs-lookup"><span data-stu-id="500dc-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="500dc-386">第9章-部署應用程式</span><span class="sxs-lookup"><span data-stu-id="500dc-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="500dc-387">若要在 HoloLens 上部署：</span><span class="sxs-lookup"><span data-stu-id="500dc-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="500dc-388">您將需要 HoloLens (的 IP 位址，才能進行遠端部署) ，並確保 HoloLens 處於 **開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="500dc-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="500dc-389">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="500dc-389">To do this:</span></span>

    1. <span data-ttu-id="500dc-390">在設置 HoloLens 的同時，開啟 **設定**。</span><span class="sxs-lookup"><span data-stu-id="500dc-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="500dc-391">前往 **Network & Internet > Wi-Fi > Advanced Options**</span><span class="sxs-lookup"><span data-stu-id="500dc-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="500dc-392">記下 **IPv4** 位址。</span><span class="sxs-lookup"><span data-stu-id="500dc-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="500dc-393">接下來，流覽回到 [ **設定**]，然後 **更新開發人員 & 的安全性 >**</span><span class="sxs-lookup"><span data-stu-id="500dc-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="500dc-394">設定 [開發人員模式]。</span><span class="sxs-lookup"><span data-stu-id="500dc-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="500dc-395">流覽至您的新 Unity 組建 (*應用程式* 資料夾) ，然後以 *Visual Studio* 開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="500dc-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="500dc-396">在 [方案設定] 中選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="500dc-397">在解決方案平臺中，選取 [ **x86**]、[ **遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="500dc-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![變更解決方案設定](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="500dc-399">移至 [ **組建] 功能表** ，然後按一下 [ **部署方案**]，將應用程式側載至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="500dc-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="500dc-400">您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中，準備好可供啟動！</span><span class="sxs-lookup"><span data-stu-id="500dc-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="500dc-401">若要部署到沉浸式耳機，請將 **解決方案平臺\*\*\*\*設定為 [** *本機電腦*]，並將 [設定] 設定為 [以 *x86* 作為 **平臺**] 來進行 *Debug*。</span><span class="sxs-lookup"><span data-stu-id="500dc-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="500dc-402">然後使用 [ **組建] 功能表** 選取 [ *部署方案*]，部署到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="500dc-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="500dc-403">第10章-使用應用程式</span><span class="sxs-lookup"><span data-stu-id="500dc-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="500dc-404">戴上 HoloLens，啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="500dc-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="500dc-405">查看您向 *臉部 API* 註冊的人員。</span><span class="sxs-lookup"><span data-stu-id="500dc-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="500dc-406">請確認：</span><span class="sxs-lookup"><span data-stu-id="500dc-406">Make sure that:</span></span>

    -  <span data-ttu-id="500dc-407">人物的臉部不太遠，而且看得清楚</span><span class="sxs-lookup"><span data-stu-id="500dc-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="500dc-408">環境光源不太暗</span><span class="sxs-lookup"><span data-stu-id="500dc-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="500dc-409">使用 [點一下手勢] 來捕捉人員的圖片。</span><span class="sxs-lookup"><span data-stu-id="500dc-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="500dc-410">等待應用程式傳送分析要求並接收回應。</span><span class="sxs-lookup"><span data-stu-id="500dc-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="500dc-411">如果已成功辨識人員，該人員的名稱將會顯示為 UI 文字。</span><span class="sxs-lookup"><span data-stu-id="500dc-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="500dc-412">您可以使用每幾秒鐘的點一下手勢來重複執行捕捉程式。</span><span class="sxs-lookup"><span data-stu-id="500dc-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="500dc-413">您已完成的 Azure 臉部 API 應用程式</span><span class="sxs-lookup"><span data-stu-id="500dc-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="500dc-414">恭喜，您建立了一個混合現實應用程式，利用 Azure 臉部辨識服務來偵測影像中的臉部，並找出任何已知的臉部。</span><span class="sxs-lookup"><span data-stu-id="500dc-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![完成本課程的結果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="500dc-416">額外練習</span><span class="sxs-lookup"><span data-stu-id="500dc-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="500dc-417">練習1</span><span class="sxs-lookup"><span data-stu-id="500dc-417">Exercise 1</span></span>

<span data-ttu-id="500dc-418">**Azure 臉部 API** 的功能強大，足以偵測單一映射中最多64的臉部。</span><span class="sxs-lookup"><span data-stu-id="500dc-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="500dc-419">擴充應用程式，讓它能夠辨識出兩個或三個臉部，在其他許多人之間。</span><span class="sxs-lookup"><span data-stu-id="500dc-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="500dc-420">練習2</span><span class="sxs-lookup"><span data-stu-id="500dc-420">Exercise 2</span></span>

<span data-ttu-id="500dc-421">**Azure 臉部 API** 也可以提供回所有種類的屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="500dc-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="500dc-422">將此整合至應用程式。</span><span class="sxs-lookup"><span data-stu-id="500dc-422">Integrate this into the application.</span></span> <span data-ttu-id="500dc-423">相較于 [表情 API](https://azure.microsoft.com/services/cognitive-services/emotion/)，這可能更有趣。</span><span class="sxs-lookup"><span data-stu-id="500dc-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/services/cognitive-services/emotion/).</span></span>