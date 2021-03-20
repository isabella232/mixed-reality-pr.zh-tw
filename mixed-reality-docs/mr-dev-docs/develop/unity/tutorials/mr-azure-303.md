---
title: 'HoloLens (第1代) 和 Azure 303-自然語言理解 (LUIS) '
description: 完成本課程，以瞭解如何在混合現實應用程式中 (LUIS) 來實行 Azure Language Understanding 智慧服務。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合的現實，學術，unity，教學課程，api，語言理解智慧服務，luis，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 663ac44dbf15ce2db63d7ffe0ecc605d3555857f
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730555"
---
# <a name="hololens-1st-gen-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="88e26-104">HoloLens (第1代) 和 Azure 303：自然語言理解 (LUIS) </span><span class="sxs-lookup"><span data-stu-id="88e26-104">HoloLens (1st gen) and Azure 303: Natural language understanding (LUIS)</span></span>

<br>

>[!NOTE]
><span data-ttu-id="88e26-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="88e26-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="88e26-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="88e26-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="88e26-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="88e26-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="88e26-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="88e26-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="88e26-109">未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="88e26-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="88e26-110">當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。</span><span class="sxs-lookup"><span data-stu-id="88e26-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

<span data-ttu-id="88e26-111">在此課程中，您將瞭解如何使用 Azure 認知服務搭配 Language Understanding API，將 Language Understanding 整合至混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="88e26-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![實驗室結果](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="88e26-113">*Language Understanding (LUIS)* 是 Microsoft Azure 服務，可讓應用程式從使用者輸入中提出意義，例如透過以自己的單字來解壓縮人物可能想要的內容。</span><span class="sxs-lookup"><span data-stu-id="88e26-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="88e26-114">這是透過機器學習來達成，它會瞭解並學習輸入資訊，然後可以使用詳細、相關的資訊來回複。</span><span class="sxs-lookup"><span data-stu-id="88e26-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="88e26-115">如需詳細資訊，請造訪 [Azure Language Understanding (LUIS) 頁面](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。</span><span class="sxs-lookup"><span data-stu-id="88e26-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="88e26-116">完成本課程之後，您將會有一個混合現實的沉浸式耳機應用程式，可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="88e26-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="88e26-117">使用連接到沉浸式耳機的麥克風來捕捉使用者輸入語音。</span><span class="sxs-lookup"><span data-stu-id="88e26-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="88e26-118">將 *Azure Language Understanding 智慧型服務* 的已捕捉聽寫傳送 (*LUIS*) 。</span><span class="sxs-lookup"><span data-stu-id="88e26-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="88e26-119">讓 LUIS 從傳送資訊中解壓縮意義，這會進行分析，並嘗試判斷使用者要求的意圖。</span><span class="sxs-lookup"><span data-stu-id="88e26-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="88e26-120">開發過程中會建立應用程式，讓使用者能夠使用語音和/或注視來變更場景中物件的大小和色彩。</span><span class="sxs-lookup"><span data-stu-id="88e26-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="88e26-121">將不會涵蓋移動控制器的使用。</span><span class="sxs-lookup"><span data-stu-id="88e26-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="88e26-122">在您的應用程式中，您可以自行決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="88e26-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="88e26-123">本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="88e26-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="88e26-124">您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="88e26-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="88e26-125">準備訓練 LUIS 數次，其涵蓋于第 [12 章](#chapter-12--improving-your-luis-service)。</span><span class="sxs-lookup"><span data-stu-id="88e26-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="88e26-126">LUIS 定型的次數愈多，您將會得到更好的結果。</span><span class="sxs-lookup"><span data-stu-id="88e26-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="88e26-127">裝置支援</span><span class="sxs-lookup"><span data-stu-id="88e26-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="88e26-128">課程</span><span class="sxs-lookup"><span data-stu-id="88e26-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="88e26-129"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="88e26-129"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="88e26-130"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="88e26-130"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="88e26-131">MR 和 Azure 303：自然語言理解 (LUIS) </span><span class="sxs-lookup"><span data-stu-id="88e26-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="88e26-132">✔️</span><span class="sxs-lookup"><span data-stu-id="88e26-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="88e26-133">✔️</span><span class="sxs-lookup"><span data-stu-id="88e26-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="88e26-134">雖然本課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機，您也可以將在本課程中學到的內容套用至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="88e26-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="88e26-135">當您依照課程的指示進行時，您將會看到有關您可能需要採用以支援 HoloLens 的任何變更的注意事項。</span><span class="sxs-lookup"><span data-stu-id="88e26-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="88e26-136">使用 HoloLens 時，您可能會注意到語音捕捉期間的一些回應。</span><span class="sxs-lookup"><span data-stu-id="88e26-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88e26-137">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="88e26-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="88e26-138">本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="88e26-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="88e26-139">另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="88e26-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="88e26-140">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span><span class="sxs-lookup"><span data-stu-id="88e26-140">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="88e26-141">本課程建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="88e26-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="88e26-142">開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)</span><span class="sxs-lookup"><span data-stu-id="88e26-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="88e26-143">啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="88e26-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="88e26-144">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="88e26-144">The latest Windows 10 SDK</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="88e26-145">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="88e26-145">Unity 2017.4</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="88e26-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="88e26-146">Visual Studio 2017</span></span>](../../install-the-tools.md)
- <span data-ttu-id="88e26-147">[Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="88e26-147">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="88e26-148">一組具有內建麥克風的耳機 (如果耳機沒有內建的 mic 和喇叭) </span><span class="sxs-lookup"><span data-stu-id="88e26-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="88e26-149">適用于 Azure 設定和 LUIS 抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="88e26-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="88e26-150">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="88e26-150">Before you start</span></span>

1.  <span data-ttu-id="88e26-151">為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="88e26-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="88e26-152">若要允許您的電腦啟用聽寫，請移至 [ **Windows 設定] > 隱私權 > 語音]、筆墨 & 輸入** ，然後按下按鈕 **開啟語音服務和輸入建議**。</span><span class="sxs-lookup"><span data-stu-id="88e26-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="88e26-153">本教學課程中的程式碼可讓您從電腦上的 **預設麥克風裝置** 集錄製。</span><span class="sxs-lookup"><span data-stu-id="88e26-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="88e26-154">請確定預設的麥克風裝置已設定為您想要用來捕捉聲音的裝置。</span><span class="sxs-lookup"><span data-stu-id="88e26-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="88e26-155">如果您的耳機有內建的麥克風，請在 *混合實境入口* 設定中，確定已開啟 [*當我磨損耳機、切換到耳機 mic]* 選項。</span><span class="sxs-lookup"><span data-stu-id="88e26-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![設定沉浸式耳機](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="88e26-157">第1章-設定 Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="88e26-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="88e26-158">若要在 Azure 中使用 *Language Understanding* 服務，您必須將服務的實例設定為可供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="88e26-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="88e26-159">登入 [Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="88e26-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="88e26-160">如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="88e26-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="88e26-161">如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="88e26-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="88e26-162">登入後，按一下左上角的 [ **新增** ]，並搜尋 *Language Understanding*，然後按一下 **Enter 鍵**。</span><span class="sxs-lookup"><span data-stu-id="88e26-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![建立 LUIS 資源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="88e26-164">在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。</span><span class="sxs-lookup"><span data-stu-id="88e26-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="88e26-165">右側的新頁面將提供 Language Understanding 服務的描述。</span><span class="sxs-lookup"><span data-stu-id="88e26-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="88e26-166">在此頁面的左下方，選取 [ **建立** ] 按鈕，以建立此服務的實例。</span><span class="sxs-lookup"><span data-stu-id="88e26-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![LUIS 服務建立-法律注意事項](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="88e26-168">當您按一下 [建立] 之後：</span><span class="sxs-lookup"><span data-stu-id="88e26-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="88e26-169">為此服務實例插入您想要的 **名稱** 。</span><span class="sxs-lookup"><span data-stu-id="88e26-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="88e26-170">選取 [訂用帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="88e26-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="88e26-171">選取適合您的 **定價層** ，如果這是您第一次建立 *LUIS 服務*，您應該可以使用名為 F0) 的免費層 (。</span><span class="sxs-lookup"><span data-stu-id="88e26-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="88e26-172">在此課程中，免費配置應已足夠。</span><span class="sxs-lookup"><span data-stu-id="88e26-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="88e26-173">選擇資源群組，或建立一個新的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="88e26-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="88e26-174">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="88e26-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="88e26-175">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。</span><span class="sxs-lookup"><span data-stu-id="88e26-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="88e26-176">如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="88e26-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="88e26-177">如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。</span><span class="sxs-lookup"><span data-stu-id="88e26-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="88e26-178">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="88e26-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="88e26-179">某些 Azure 資產僅適用于某些區域。</span><span class="sxs-lookup"><span data-stu-id="88e26-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="88e26-180">您也必須確認您已瞭解套用到此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="88e26-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="88e26-181">選取 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="88e26-181">Select **Create**.</span></span>

        ![建立 LUIS 服務-使用者輸入](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="88e26-183">當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="88e26-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="88e26-184">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="88e26-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![新的 Azure 通知影像](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="88e26-186">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="88e26-186">Click on the notification to explore your new Service instance.</span></span>

    ![成功建立資源通知](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="88e26-188">按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。</span><span class="sxs-lookup"><span data-stu-id="88e26-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="88e26-189">您將會進入新的 LUIS 服務實例。</span><span class="sxs-lookup"><span data-stu-id="88e26-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![存取 LUIS 金鑰](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="88e26-191">在本教學課程中，您的應用程式將需要呼叫您的服務，這是透過使用服務的訂用帳戶金鑰來完成。</span><span class="sxs-lookup"><span data-stu-id="88e26-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="88e26-192">在 *LUIS API* 服務的 [*快速入門*] 頁面中，流覽至第一個步驟、*抓取您的金鑰*，然後按一下 [機 **碼**] (您也可以按一下位於 [服務] 導覽功能表中的藍色超連結鍵（以按鍵圖示) 表示）來達成此目的。</span><span class="sxs-lookup"><span data-stu-id="88e26-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="88e26-193">這會顯示您的服務 *金鑰*。</span><span class="sxs-lookup"><span data-stu-id="88e26-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="88e26-194">複製其中一個顯示的金鑰，您稍後會在專案中使用。</span><span class="sxs-lookup"><span data-stu-id="88e26-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="88e26-195">在 [ *服務* ] 頁面中，按一下 *Language Understanding 入口網站* ，以重新導向至您將在 LUIS 應用程式中用來建立新服務的網頁。</span><span class="sxs-lookup"><span data-stu-id="88e26-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="88e26-196">第2章-Language Understanding 入口網站</span><span class="sxs-lookup"><span data-stu-id="88e26-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="88e26-197">在本節中，您將瞭解如何在 LUIS 入口網站中建立 LUIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="88e26-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="88e26-198">請注意，在本章節中設定 *實體*、 *意圖* 和 *語句* 的第一個步驟是建立 LUIS 服務的第一個步驟：您也需要重新定型服務數次，以使其更精確。</span><span class="sxs-lookup"><span data-stu-id="88e26-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="88e26-199">本課程的 [最後一章](#chapter-12--improving-your-luis-service) 涵蓋了重新訓練您的服務，因此請確定您已完成。</span><span class="sxs-lookup"><span data-stu-id="88e26-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="88e26-200">到達 *Language Understanding 入口網站* 時，您可能需要登入（如果尚未登入），其認證與您的 Azure 入口網站相同。</span><span class="sxs-lookup"><span data-stu-id="88e26-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS 登入頁面](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="88e26-202">如果這是您第一次使用 LUIS，您將需要向下滾動至 [歡迎使用] 頁面的底部，以尋找並按一下 [ **建立 LUIS 應用程式** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="88e26-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![建立 LUIS 應用程式頁面](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="88e26-204">登入之後，如果您目前不在該區段中) ，請按一下 [ **我的應用程式** (。</span><span class="sxs-lookup"><span data-stu-id="88e26-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="88e26-205">然後，您可以按一下 [ **建立新的應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-205">You can then click on **Create new app**.</span></span>

    ![LUIS-我的應用程式影像](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="88e26-207">為您的應用程式 *命名*。</span><span class="sxs-lookup"><span data-stu-id="88e26-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="88e26-208">如果您的應用程式應該瞭解與英文不同的語言，您應該將 *文化* 特性變更為適當的語言。</span><span class="sxs-lookup"><span data-stu-id="88e26-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="88e26-209">您也可以在這裡新增新 LUIS 應用程式的 *描述* 。</span><span class="sxs-lookup"><span data-stu-id="88e26-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-建立新的應用程式](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="88e26-211">當您按下 [**完成**] 之後，您將會進入新 *LUIS* 應用程式的 [*組建*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="88e26-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="88e26-212">這裡有幾個重要的概念需要瞭解：</span><span class="sxs-lookup"><span data-stu-id="88e26-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="88e26-213">*意圖*，代表將在使用者的查詢之後呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="88e26-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="88e26-214">*意圖* 可能會有一或多個 *實體*。</span><span class="sxs-lookup"><span data-stu-id="88e26-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="88e26-215">*實體* 是查詢的元件，可描述與 *意圖* 相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="88e26-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="88e26-216">*語句* 是開發人員提供的查詢範例，LUIS 將使用它來定型本身。</span><span class="sxs-lookup"><span data-stu-id="88e26-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="88e26-217">如果這些概念並非完全清楚，請別擔心，因為本課程將在本章進一步說明這些概念。</span><span class="sxs-lookup"><span data-stu-id="88e26-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="88e26-218">首先，您會建立建立此課程所需的 *實體* 。</span><span class="sxs-lookup"><span data-stu-id="88e26-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="88e26-219">在頁面的左側，按一下 [ *實體*]，然後按一下 [ **建立新實體**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![建立新的實體](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="88e26-221">呼叫新的實體 *色彩*，將其類型設定為 *Simple*，然後按下 [ **完成**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![建立簡單實體-色彩](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="88e26-223">重複此程式，以建立三個 (3) 更簡單的實體，名為：</span><span class="sxs-lookup"><span data-stu-id="88e26-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="88e26-224">*將*</span><span class="sxs-lookup"><span data-stu-id="88e26-224">*upsize*</span></span>
    -   <span data-ttu-id="88e26-225">*縮小*</span><span class="sxs-lookup"><span data-stu-id="88e26-225">*downsize*</span></span>
    -   <span data-ttu-id="88e26-226">*目標*</span><span class="sxs-lookup"><span data-stu-id="88e26-226">*target*</span></span>

<span data-ttu-id="88e26-227">結果看起來應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="88e26-227">The result should look like the image below:</span></span>

![建立實體的結果](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="88e26-229">您現在可以開始建立 *意圖*。</span><span class="sxs-lookup"><span data-stu-id="88e26-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="88e26-230">請勿刪除「 **無** 」意圖。</span><span class="sxs-lookup"><span data-stu-id="88e26-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="88e26-231">在頁面左側按一下 [ **意圖**]，然後按一下 [ **建立新意圖**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![建立新的意圖](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="88e26-233">呼叫新 *意圖* **ChangeObjectColor**。</span><span class="sxs-lookup"><span data-stu-id="88e26-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="88e26-234">這個 *意圖* 名稱是在本課程稍後的程式碼中使用，因此為了獲得最佳結果，請完全依照提供的方式使用此名稱。</span><span class="sxs-lookup"><span data-stu-id="88e26-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="88e26-235">一旦您確認名稱，系統會將您導向 [意圖] 頁面。</span><span class="sxs-lookup"><span data-stu-id="88e26-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS-意圖頁面](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="88e26-237">您會發現有一個文字方塊要求您輸入5個以上的不同 *語句*。</span><span class="sxs-lookup"><span data-stu-id="88e26-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="88e26-238">LUIS 會將所有語句轉換成小寫。</span><span class="sxs-lookup"><span data-stu-id="88e26-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="88e26-239">在頂端的文字方塊中插入下列 *語句*， (目前具有 *大約5個範例* 的文字類型 .。。</span><span class="sxs-lookup"><span data-stu-id="88e26-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="88e26-240">) ，然後按 **enter**：</span><span class="sxs-lookup"><span data-stu-id="88e26-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="88e26-241">您將會注意到，新的 *語句* 會顯示在下方清單中。</span><span class="sxs-lookup"><span data-stu-id="88e26-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="88e26-242">遵循相同的程式，插入下列六個 (6) 語句：</span><span class="sxs-lookup"><span data-stu-id="88e26-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="88e26-243">針對您已建立的每個語句，您必須識別 LUIS 做為實體應使用哪些字組。</span><span class="sxs-lookup"><span data-stu-id="88e26-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="88e26-244">在此範例中，您必須將所有色彩標示為 *色彩* 實體，並將所有的可能參考標示為 *目標* 實體。</span><span class="sxs-lookup"><span data-stu-id="88e26-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="88e26-245">若要這樣做，請嘗試在第一個語句中按一下 [單字 *圓柱* ]，然後選取 [ *目標*]。</span><span class="sxs-lookup"><span data-stu-id="88e26-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![識別語句目標](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="88e26-247">現在按一下第一個語句中的 *紅色* 文字，然後選取 [ *色彩*]。</span><span class="sxs-lookup"><span data-stu-id="88e26-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![識別語句實體](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="88e26-249">為下一行加上標籤，其中 *cube* 應該是 *目標*，而 *黑色* 應為 *色彩*。</span><span class="sxs-lookup"><span data-stu-id="88e26-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="88e26-250">另外也請注意，我們所提供的「 *this*」、「 *it*」和「 *這個物件*」這幾個字，因此也有非特定的目標型別可供使用。</span><span class="sxs-lookup"><span data-stu-id="88e26-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="88e26-251">重複上述程式，直到所有語句都已標示實體為止。</span><span class="sxs-lookup"><span data-stu-id="88e26-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="88e26-252">如果您需要協助，請參閱下圖。</span><span class="sxs-lookup"><span data-stu-id="88e26-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="88e26-253">選取字組將其標示為實體時：</span><span class="sxs-lookup"><span data-stu-id="88e26-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="88e26-254">若為單一單字，請按一下它們。</span><span class="sxs-lookup"><span data-stu-id="88e26-254">For single words just click them.</span></span>
    > - <span data-ttu-id="88e26-255">針對一組兩個或多個字組，按一下開頭，然後在集合結尾。</span><span class="sxs-lookup"><span data-stu-id="88e26-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="88e26-256">您可以使用 [ *標記視圖* ] 切換按鈕，在 **實體/標記視圖** 之間切換！</span><span class="sxs-lookup"><span data-stu-id="88e26-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="88e26-257">結果應該如下列影像所示，顯示 [ **實體/權杖] 視圖**：</span><span class="sxs-lookup"><span data-stu-id="88e26-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![& 實體視圖的權杖](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="88e26-259">此時按下頁面右上方的 [ **定型** ] 按鈕，並等候其上的小圓形指標變成綠色。</span><span class="sxs-lookup"><span data-stu-id="88e26-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="88e26-260">這表示 LUIS 已成功定型以辨識此意圖。</span><span class="sxs-lookup"><span data-stu-id="88e26-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![訓練 LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="88e26-262">做為您的練習，使用實體 *目標*、*升遷* 和 *縮減*，建立名為 **ChangeObjectSize** 的新意圖。</span><span class="sxs-lookup"><span data-stu-id="88e26-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="88e26-263">遵循先前意圖的相同程式，插入下列八個 (8) 語句以進行 *大小* 變更：</span><span class="sxs-lookup"><span data-stu-id="88e26-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="88e26-264">結果應該類似下圖中的結果：</span><span class="sxs-lookup"><span data-stu-id="88e26-264">The result should be like the one in the image below:</span></span>

    ![設定 ChangeObjectSize 權杖/實體](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="88e26-266">一旦建立並定型了 **ChangeObjectColor** 和 **ChangeObjectSize** 這兩個意圖，請按一下頁面頂端的 [ **發行** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="88e26-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![發佈 LUIS 服務](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="88e26-268">在 [ *發佈* ] 頁面上，您將會完成併發布您的 LUIS 應用程式，讓您的程式碼可以存取它。</span><span class="sxs-lookup"><span data-stu-id="88e26-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="88e26-269">將 [ *發行* ] 下拉式清單設定為 [ **生產**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="88e26-270">將 *時區* 設定為時區。</span><span class="sxs-lookup"><span data-stu-id="88e26-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="88e26-271">核取 [ **包含所有預測的意圖分數**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="88e26-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="88e26-272">按一下 [ **發行至生產** 位置]。</span><span class="sxs-lookup"><span data-stu-id="88e26-272">Click on **Publish to Production Slot**.</span></span>

        ![發行設定](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="88e26-274">在 [ *資源和金鑰*] 區段中：</span><span class="sxs-lookup"><span data-stu-id="88e26-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="88e26-275">在 Azure 入口網站中，選取您為服務實例設定的區域。</span><span class="sxs-lookup"><span data-stu-id="88e26-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="88e26-276">您會注意到以下的 **Starter_Key** 元素，請忽略它。</span><span class="sxs-lookup"><span data-stu-id="88e26-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="88e26-277">按一下 [ **新增金鑰** ]，然後插入您在 Azure 入口網站中建立服務實例時所取得的 *金鑰* 。</span><span class="sxs-lookup"><span data-stu-id="88e26-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="88e26-278">如果您的 Azure 和 LUIS 入口網站已登入相同的使用者，您將會得到 *租使用者名稱*、訂用帳戶 *名稱* 和您想要使用之 *金鑰* 的下拉式功能表， (將會與您先前在 Azure 入口網站中提供的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="88e26-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="88e26-279">在 [ *端點*] 底下，取得對應至您所插入金鑰的端點複本，您很快就會在程式碼中使用它。</span><span class="sxs-lookup"><span data-stu-id="88e26-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="88e26-280">第3章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="88e26-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="88e26-281">以下是使用混合式開發進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="88e26-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="88e26-282">開啟 *Unity* ，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-282">Open *Unity* and click **New**.</span></span> 

    ![開始新的 Unity 專案。](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="88e26-284">您現在將需要提供 Unity 專案名稱、插入 **MR_LUIS**。</span><span class="sxs-lookup"><span data-stu-id="88e26-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="88e26-285">請確定專案類型設定為 **3d**。</span><span class="sxs-lookup"><span data-stu-id="88e26-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="88e26-286">將 **位置** 設定為適合您 (記住，較接近根目錄的) 。</span><span class="sxs-lookup"><span data-stu-id="88e26-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="88e26-287">然後，按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-287">Then, click **Create project**.</span></span>

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="88e26-289">在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="88e26-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="88e26-290">移至 [編輯] > 喜好設定，然後在新視窗中，流覽至 [ **外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="88e26-291">將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="88e26-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="88e26-292">關閉 [ **喜好** 設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="88e26-292">Close the **Preferences** window.</span></span>

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="88e26-294">接著，移至 [檔案 **> 組建設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至 **通用 Windows 平臺**。</span><span class="sxs-lookup"><span data-stu-id="88e26-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![[組建設定] 視窗，將平臺切換至 UWP。](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="88e26-296">移至 [檔案 **> 組建設定** ]，並確定：</span><span class="sxs-lookup"><span data-stu-id="88e26-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="88e26-297">**目標裝置** 已設定為 **任何裝置**</span><span class="sxs-lookup"><span data-stu-id="88e26-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="88e26-298">針對 Microsoft HoloLens，請將 **目標裝置** 設定為 *HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="88e26-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="88e26-299">**組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="88e26-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="88e26-300">**SDK** 已設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="88e26-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="88e26-301">**Visual Studio 版本** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="88e26-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="88e26-302">**組建並執行** 設定為 **本機電腦**</span><span class="sxs-lookup"><span data-stu-id="88e26-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="88e26-303">儲存場景，並將其新增至組建。</span><span class="sxs-lookup"><span data-stu-id="88e26-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="88e26-304">若要這麼做，請選取 [ **新增開啟的場景**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="88e26-305">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="88e26-305">A save window will appear.</span></span>
        
            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="88e26-307">為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。</span><span class="sxs-lookup"><span data-stu-id="88e26-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立新的腳本資料夾](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="88e26-309">開啟新建立的 **場景** 資料夾，然後在 [ *檔案名*：文字] 欄位中輸入 **MR_LuisScene**，然後按 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![提供新場景的名稱。](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="88e26-311">[ *組建設定*] 中的其餘設定，現在應該保持為預設值。</span><span class="sxs-lookup"><span data-stu-id="88e26-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="88e26-312">在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。</span><span class="sxs-lookup"><span data-stu-id="88e26-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![開啟 [播放玩家設定]。](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="88e26-314">在此面板中，需要驗證幾個設定：</span><span class="sxs-lookup"><span data-stu-id="88e26-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="88e26-315">在 [ **其他設定** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="88e26-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="88e26-316">**腳本執行階段版本** 應該是 **穩定** 的 ( .net 3.5 對等) 。</span><span class="sxs-lookup"><span data-stu-id="88e26-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="88e26-317">**腳本後端** 應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="88e26-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="88e26-318">**API 相容性層級** 應為 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="88e26-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他設定。](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="88e26-320">在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：</span><span class="sxs-lookup"><span data-stu-id="88e26-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="88e26-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="88e26-321">**InternetClient**</span></span>
        2. <span data-ttu-id="88e26-322">**麥克風**</span><span class="sxs-lookup"><span data-stu-id="88e26-322">**Microphone**</span></span>

            ![正在更新發行設定。](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="88e26-324">在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="88e26-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 設定。](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="88e26-326">回到 *組建設定*： _Unity c #_ 專案不再呈現灰色;勾選此方塊旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="88e26-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="88e26-327">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="88e26-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="88e26-328">將場景和專案儲存 (檔 **> 儲存場景/檔案 > 儲存專案**) 。</span><span class="sxs-lookup"><span data-stu-id="88e26-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="88e26-329">第4章-建立場景</span><span class="sxs-lookup"><span data-stu-id="88e26-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88e26-330">如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意下載 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，並將其匯入到您的專案中做為 [自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第5章](#chapter-5--create-the-microphonemanager-class)。</span><span class="sxs-lookup"><span data-stu-id="88e26-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="88e26-331">在 [階層] *面板* 的空白區域中，以滑鼠右鍵按一下 [ **3d 物件**] 下的 [加入 **平面**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![建立平面。](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="88e26-333">請注意，當您以滑鼠右鍵按一下階層內以建立更多物件時，如果您仍然選取最後一個物件，則選取的物件將會是新物件的父系。</span><span class="sxs-lookup"><span data-stu-id="88e26-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="88e26-334">請避免在階層內的空白處按一下滑鼠左鍵，然後以滑鼠右鍵按一下。</span><span class="sxs-lookup"><span data-stu-id="88e26-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="88e26-335">重複上述程式來新增下列物件：</span><span class="sxs-lookup"><span data-stu-id="88e26-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="88e26-336">*Sphere*</span><span class="sxs-lookup"><span data-stu-id="88e26-336">*Sphere*</span></span>
    2. <span data-ttu-id="88e26-337">*圓柱*</span><span class="sxs-lookup"><span data-stu-id="88e26-337">*Cylinder*</span></span>
    3. <span data-ttu-id="88e26-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="88e26-338">*Cube*</span></span>
    4. <span data-ttu-id="88e26-339">*3D 文字*</span><span class="sxs-lookup"><span data-stu-id="88e26-339">*3D Text*</span></span>

4.  <span data-ttu-id="88e26-340">產生 *的場景階層* 應如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="88e26-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![場景階層設定。](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="88e26-342">以滑鼠左鍵按一下 **主要攝影機** 來選取它，然後查看 [偵測 *器] 面板* ，您將會看到攝影機物件及其所有元件。</span><span class="sxs-lookup"><span data-stu-id="88e26-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="88e26-343">按一下位於 [偵測 *器] 面板* 最底部的 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="88e26-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![新增音訊來源](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="88e26-345">搜尋稱為 *音訊來源* 的元件，如上所示。</span><span class="sxs-lookup"><span data-stu-id="88e26-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="88e26-346">此外，請確定主要攝影機的 *轉換* 元件已設定為 (0、0、0) ，您可以按下相機 *轉換* 元件旁邊的 **齒輪** 圖示，然後選取 [**重設**] 來完成此操作。</span><span class="sxs-lookup"><span data-stu-id="88e26-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="88e26-347">接著， *轉換* 元件看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="88e26-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="88e26-348">*Position* 設定為 **0、0、0**。</span><span class="sxs-lookup"><span data-stu-id="88e26-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="88e26-349">*旋轉* 設定為 **0、0、0**。</span><span class="sxs-lookup"><span data-stu-id="88e26-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="88e26-350">針對 Microsoft HoloLens，您也必須變更下列內容，這是 **相機** 元件的一部分，也就是您的 **主要攝影機**：</span><span class="sxs-lookup"><span data-stu-id="88e26-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="88e26-351">**清除旗標：** 純色。</span><span class="sxs-lookup"><span data-stu-id="88e26-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="88e26-352">**背景** ' 黑色，Alpha 0 ' –十六進位色彩： #00000000。</span><span class="sxs-lookup"><span data-stu-id="88e26-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="88e26-353">以滑鼠左鍵按一下 **平面** 即可選取。</span><span class="sxs-lookup"><span data-stu-id="88e26-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="88e26-354">在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：</span><span class="sxs-lookup"><span data-stu-id="88e26-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |   <span data-ttu-id="88e26-355">X 軸</span><span class="sxs-lookup"><span data-stu-id="88e26-355">X Axis</span></span>    | <span data-ttu-id="88e26-356">Y 軸</span><span class="sxs-lookup"><span data-stu-id="88e26-356">Y Axis</span></span> |   <span data-ttu-id="88e26-357">Z 軸</span><span class="sxs-lookup"><span data-stu-id="88e26-357">Z Axis</span></span>    |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="88e26-358">0</span><span class="sxs-lookup"><span data-stu-id="88e26-358">0</span></span>     | <span data-ttu-id="88e26-359">-1</span><span class="sxs-lookup"><span data-stu-id="88e26-359">-1</span></span>                     | <span data-ttu-id="88e26-360">0</span><span class="sxs-lookup"><span data-stu-id="88e26-360">0</span></span>     |


10. <span data-ttu-id="88e26-361">以滑鼠左鍵按一下 **球體** 以選取它。</span><span class="sxs-lookup"><span data-stu-id="88e26-361">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="88e26-362">在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：</span><span class="sxs-lookup"><span data-stu-id="88e26-362">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |   <span data-ttu-id="88e26-363">X 軸</span><span class="sxs-lookup"><span data-stu-id="88e26-363">X Axis</span></span>    | <span data-ttu-id="88e26-364">Y 軸</span><span class="sxs-lookup"><span data-stu-id="88e26-364">Y Axis</span></span> |   <span data-ttu-id="88e26-365">Z 軸</span><span class="sxs-lookup"><span data-stu-id="88e26-365">Z Axis</span></span>    |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="88e26-366">2</span><span class="sxs-lookup"><span data-stu-id="88e26-366">2</span></span>     | <span data-ttu-id="88e26-367">1</span><span class="sxs-lookup"><span data-stu-id="88e26-367">1</span></span>                      | <span data-ttu-id="88e26-368">2</span><span class="sxs-lookup"><span data-stu-id="88e26-368">2</span></span>     |

11. <span data-ttu-id="88e26-369">以滑鼠左鍵按一下 **圓柱** 以選取它。</span><span class="sxs-lookup"><span data-stu-id="88e26-369">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="88e26-370">在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：</span><span class="sxs-lookup"><span data-stu-id="88e26-370">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |   <span data-ttu-id="88e26-371">X 軸</span><span class="sxs-lookup"><span data-stu-id="88e26-371">X Axis</span></span>    | <span data-ttu-id="88e26-372">Y 軸</span><span class="sxs-lookup"><span data-stu-id="88e26-372">Y Axis</span></span> |   <span data-ttu-id="88e26-373">Z 軸</span><span class="sxs-lookup"><span data-stu-id="88e26-373">Z Axis</span></span>    |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="88e26-374">-2</span><span class="sxs-lookup"><span data-stu-id="88e26-374">-2</span></span>    | <span data-ttu-id="88e26-375">1</span><span class="sxs-lookup"><span data-stu-id="88e26-375">1</span></span>                      | <span data-ttu-id="88e26-376">2</span><span class="sxs-lookup"><span data-stu-id="88e26-376">2</span></span>     |

12. <span data-ttu-id="88e26-377">在 **Cube** 上按一下滑鼠左鍵即可選取它。</span><span class="sxs-lookup"><span data-stu-id="88e26-377">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="88e26-378">在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：</span><span class="sxs-lookup"><span data-stu-id="88e26-378">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="88e26-379">轉換- *位置*</span><span class="sxs-lookup"><span data-stu-id="88e26-379">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="88e26-380">轉換- *旋轉*</span><span class="sxs-lookup"><span data-stu-id="88e26-380">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="88e26-381">**X**</span><span class="sxs-lookup"><span data-stu-id="88e26-381">**X**</span></span> | <span data-ttu-id="88e26-382">**Y**</span><span class="sxs-lookup"><span data-stu-id="88e26-382">**Y**</span></span>                   | <span data-ttu-id="88e26-383">**Z**</span><span class="sxs-lookup"><span data-stu-id="88e26-383">**Z**</span></span> |  \| | <span data-ttu-id="88e26-384">**X**</span><span class="sxs-lookup"><span data-stu-id="88e26-384">**X**</span></span> | <span data-ttu-id="88e26-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="88e26-385">**Y**</span></span>                  | <span data-ttu-id="88e26-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="88e26-386">**Z**</span></span> |
    | <span data-ttu-id="88e26-387">0</span><span class="sxs-lookup"><span data-stu-id="88e26-387">0</span></span>     | <span data-ttu-id="88e26-388">1</span><span class="sxs-lookup"><span data-stu-id="88e26-388">1</span></span>                       | <span data-ttu-id="88e26-389">4</span><span class="sxs-lookup"><span data-stu-id="88e26-389">4</span></span>     |  \| | <span data-ttu-id="88e26-390">45</span><span class="sxs-lookup"><span data-stu-id="88e26-390">45</span></span>    | <span data-ttu-id="88e26-391">45</span><span class="sxs-lookup"><span data-stu-id="88e26-391">45</span></span>                     | <span data-ttu-id="88e26-392">0</span><span class="sxs-lookup"><span data-stu-id="88e26-392">0</span></span>     | 

13. <span data-ttu-id="88e26-393">以滑鼠左鍵按一下 **新的文字** 物件，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="88e26-393">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="88e26-394">在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：</span><span class="sxs-lookup"><span data-stu-id="88e26-394">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="88e26-395">轉換- *位置*</span><span class="sxs-lookup"><span data-stu-id="88e26-395">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="88e26-396">轉換- *調整規模*</span><span class="sxs-lookup"><span data-stu-id="88e26-396">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="88e26-397">**X**</span><span class="sxs-lookup"><span data-stu-id="88e26-397">**X**</span></span> | <span data-ttu-id="88e26-398">**Y**</span><span class="sxs-lookup"><span data-stu-id="88e26-398">**Y**</span></span>                  | <span data-ttu-id="88e26-399">**Z**</span><span class="sxs-lookup"><span data-stu-id="88e26-399">**Z**</span></span> |  \| | <span data-ttu-id="88e26-400">**X**</span><span class="sxs-lookup"><span data-stu-id="88e26-400">**X**</span></span> | <span data-ttu-id="88e26-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="88e26-401">**Y**</span></span>               | <span data-ttu-id="88e26-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="88e26-402">**Z**</span></span> |
    | <span data-ttu-id="88e26-403">-2</span><span class="sxs-lookup"><span data-stu-id="88e26-403">-2</span></span>    | <span data-ttu-id="88e26-404">6</span><span class="sxs-lookup"><span data-stu-id="88e26-404">6</span></span>                      | <span data-ttu-id="88e26-405">9</span><span class="sxs-lookup"><span data-stu-id="88e26-405">9</span></span>     |  \| | <span data-ttu-id="88e26-406">0.1</span><span class="sxs-lookup"><span data-stu-id="88e26-406">0.1</span></span>   | <span data-ttu-id="88e26-407">0.1</span><span class="sxs-lookup"><span data-stu-id="88e26-407">0.1</span></span>                 | <span data-ttu-id="88e26-408">0.1</span><span class="sxs-lookup"><span data-stu-id="88e26-408">0.1</span></span>   | 

14. <span data-ttu-id="88e26-409">將 **文字網格** 元件中的 **字型大小** 變更為 **50**。</span><span class="sxs-lookup"><span data-stu-id="88e26-409">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="88e26-410">將 **文字網格** 物件的 *名稱* 變更為 **聽寫文字**。</span><span class="sxs-lookup"><span data-stu-id="88e26-410">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![建立3D 文字物件](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="88e26-412">階層面板結構現在看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="88e26-412">Your Hierarchy Panel structure should now look like this:</span></span>

    ![場景視圖中的文字網格](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="88e26-414">最後的場景看起來應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="88e26-414">The final scene should look like the image below:</span></span>

    ![場景視圖。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="88e26-416">第5章-建立 MicrophoneManager 類別</span><span class="sxs-lookup"><span data-stu-id="88e26-416">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="88e26-417">您即將建立的第一個腳本是 *MicrophoneManager* 類別。</span><span class="sxs-lookup"><span data-stu-id="88e26-417">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="88e26-418">接下來，您將建立 *LuisManager*、 *行為* 類別和最後一個 *注視* 類別 (歡迎您立即建立這些類別，不過您會在每一章) 討論。</span><span class="sxs-lookup"><span data-stu-id="88e26-418">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="88e26-419">*MicrophoneManager* 類別負責：</span><span class="sxs-lookup"><span data-stu-id="88e26-419">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="88e26-420">偵測連接到耳機或電腦的錄製裝置 (以預設的) 為准。</span><span class="sxs-lookup"><span data-stu-id="88e26-420">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="88e26-421">捕捉音訊 (語音) 並使用聽寫將其儲存為字串。</span><span class="sxs-lookup"><span data-stu-id="88e26-421">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="88e26-422">聲音暫停之後，請將聽寫提交至 *LuisManager* 類別。</span><span class="sxs-lookup"><span data-stu-id="88e26-422">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="88e26-423">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="88e26-423">To create this class:</span></span> 

1.  <span data-ttu-id="88e26-424">在 [ *專案] 面板* 中按一下滑鼠右鍵， **建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="88e26-424">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="88e26-425">呼叫資料夾 **腳本**。</span><span class="sxs-lookup"><span data-stu-id="88e26-425">Call the folder **Scripts**.</span></span> 

    ![建立腳本資料夾。](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="88e26-427">在 [ **腳本** ] 資料夾建立後，按兩下以開啟。</span><span class="sxs-lookup"><span data-stu-id="88e26-427">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="88e26-428">然後，在該資料夾中，以滑鼠右鍵按一下， **建立 > c # 腳本**。</span><span class="sxs-lookup"><span data-stu-id="88e26-428">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="88e26-429">將腳本命名為 *MicrophoneManager*。</span><span class="sxs-lookup"><span data-stu-id="88e26-429">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="88e26-430">按兩下 [ *MicrophoneManager* ] 以 *Visual Studio* 開啟。</span><span class="sxs-lookup"><span data-stu-id="88e26-430">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="88e26-431">將下列命名空間新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="88e26-431">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="88e26-432">然後，在 *MicrophoneManager* 類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="88e26-432">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="88e26-433">現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="88e26-433">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="88e26-434">當類別初始化時，就會呼叫這些內容：</span><span class="sxs-lookup"><span data-stu-id="88e26-434">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="88e26-435">現在您需要應用程式用來啟動和停止語音捕捉的方法，並將它傳遞給 *LuisManager* 類別，您很快就會建立。</span><span class="sxs-lookup"><span data-stu-id="88e26-435">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="88e26-436">新增語音暫停時將叫用的 *聽寫處理常式* 。</span><span class="sxs-lookup"><span data-stu-id="88e26-436">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="88e26-437">這個方法會將聽寫文字傳遞至 *LuisManager* 類別。</span><span class="sxs-lookup"><span data-stu-id="88e26-437">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="88e26-438">刪除 *更新 ()* 方法，因為此類別不會使用它。</span><span class="sxs-lookup"><span data-stu-id="88e26-438">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="88e26-439">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="88e26-439">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="88e26-440">此時您會注意到 *Unity 編輯器主控台面板* 中出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="88e26-440">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="88e26-441">這是因為程式碼會參考您將在下一章中建立的 *LuisManager* 類別。</span><span class="sxs-lookup"><span data-stu-id="88e26-441">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="88e26-442">第6章-建立 LUISManager 類別</span><span class="sxs-lookup"><span data-stu-id="88e26-442">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="88e26-443">您現在可以建立 *LuisManager* 類別，這會呼叫 Azure LUIS 服務。</span><span class="sxs-lookup"><span data-stu-id="88e26-443">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="88e26-444">此類別的目的是要接收來自 *MicrophoneManager* 類別的聽寫文字，並將它傳送到要分析的 *Azure Language Understanding API* 。</span><span class="sxs-lookup"><span data-stu-id="88e26-444">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="88e26-445">此類別會將 *JSON* 回應還原序列化，並呼叫 *行為* 類別的適當方法來觸發動作。</span><span class="sxs-lookup"><span data-stu-id="88e26-445">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="88e26-446">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="88e26-446">To create this class:</span></span> 

1.  <span data-ttu-id="88e26-447">按兩下 [ **腳本** ] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="88e26-447">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="88e26-448">在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-448">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="88e26-449">將腳本命名為 *LuisManager*。</span><span class="sxs-lookup"><span data-stu-id="88e26-449">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="88e26-450">按兩下腳本，以 Visual Studio 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="88e26-450">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="88e26-451">將下列命名空間新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="88e26-451">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="88e26-452">您一開始會在 *LuisManager* 類別 **內建立三個類別，** (在相同腳本檔中的相同腳本檔案內 *()* ，) 將代表從 Azure 還原序列化的 JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="88e26-452">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="88e26-453">接下來，在 *LuisManager* 類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="88e26-453">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="88e26-454">請務必將您的 LUIS 端點立即放入您的 LUIS 入口網站)  (。</span><span class="sxs-lookup"><span data-stu-id="88e26-454">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="88e26-455">現在需要新增 *喚醒 ()* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="88e26-455">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="88e26-456">當類別初始化時，會呼叫這個方法：</span><span class="sxs-lookup"><span data-stu-id="88e26-456">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="88e26-457">現在您需要此應用程式用來將接收自 *MicrophoneManager* 類別的聽寫傳送給 *LUIS*，然後接收和還原序列化回應的方法。</span><span class="sxs-lookup"><span data-stu-id="88e26-457">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="88e26-458">一旦決定意圖的值和相關聯的實體之後，就會將它們傳遞給 *行為* 類別的實例，以觸發預期的動作。</span><span class="sxs-lookup"><span data-stu-id="88e26-458">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="88e26-459">建立稱為 *AnalyseResponseElements ()* 的新方法，它會讀取產生的 *AnalysedQuery* 並判斷實體。</span><span class="sxs-lookup"><span data-stu-id="88e26-459">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="88e26-460">一旦決定這些實體，就會將它們傳遞給 *行為* 類別的實例，以在動作中使用。</span><span class="sxs-lookup"><span data-stu-id="88e26-460">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="88e26-461">刪除 *開始 ()* 並 *更新 ()* 方法，因為此類別不會使用它們。</span><span class="sxs-lookup"><span data-stu-id="88e26-461">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="88e26-462">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="88e26-462">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="88e26-463">此時您會注意到 *Unity 編輯器主控台面板* 中出現數個錯誤。</span><span class="sxs-lookup"><span data-stu-id="88e26-463">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="88e26-464">這是因為程式碼會參考您將在下一章中建立的 *行為* 類別。</span><span class="sxs-lookup"><span data-stu-id="88e26-464">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="88e26-465">第7章-建立行為類別</span><span class="sxs-lookup"><span data-stu-id="88e26-465">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="88e26-466">*行為* 類別會使用 *LuisManager* 類別所提供的實體來觸發動作。</span><span class="sxs-lookup"><span data-stu-id="88e26-466">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="88e26-467">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="88e26-467">To create this class:</span></span> 

1.  <span data-ttu-id="88e26-468">按兩下 [ **腳本** ] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="88e26-468">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="88e26-469">在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-469">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="88e26-470">將腳本命名為 *行為*。</span><span class="sxs-lookup"><span data-stu-id="88e26-470">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="88e26-471">按兩下腳本，以 *Visual Studio* 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="88e26-471">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="88e26-472">然後，在 *行為* 類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="88e26-472">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="88e26-473">新增 *喚醒的 ()* 方法程式碼。</span><span class="sxs-lookup"><span data-stu-id="88e26-473">Add the *Awake()* method code.</span></span> <span data-ttu-id="88e26-474">當類別初始化時，會呼叫這個方法：</span><span class="sxs-lookup"><span data-stu-id="88e26-474">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="88e26-475">您) 先前建立的 *LuisManager* 類別 (會呼叫下列方法，以判斷哪一個物件是查詢的目標，然後觸發適當的動作。</span><span class="sxs-lookup"><span data-stu-id="88e26-475">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="88e26-476">新增 *FindTarget ()* 方法，以判斷哪一個 *Gameobject* 是目前意圖的目標。</span><span class="sxs-lookup"><span data-stu-id="88e26-476">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="88e26-477">如果未在實體中定義明確的目標，則這個方法會將目標設為 "gazed" 的 *GameObject* 。</span><span class="sxs-lookup"><span data-stu-id="88e26-477">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="88e26-478">刪除 *開始 ()* 並 *更新 ()* 方法，因為此類別不會使用它們。</span><span class="sxs-lookup"><span data-stu-id="88e26-478">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="88e26-479">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="88e26-479">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="88e26-480">第8章-建立注視類別</span><span class="sxs-lookup"><span data-stu-id="88e26-480">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="88e26-481">完成此應用程式所需的最後一個類別是 *注視* 類別。</span><span class="sxs-lookup"><span data-stu-id="88e26-481">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="88e26-482">此類別會更新目前在使用者視覺效果焦點中之 *GameObject* 的參考。</span><span class="sxs-lookup"><span data-stu-id="88e26-482">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="88e26-483">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="88e26-483">To create this Class:</span></span> 

1.  <span data-ttu-id="88e26-484">按兩下 [ **腳本** ] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="88e26-484">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="88e26-485">在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-485">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="88e26-486">將腳本命名為 *注視*。</span><span class="sxs-lookup"><span data-stu-id="88e26-486">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="88e26-487">按兩下腳本，以 *Visual Studio* 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="88e26-487">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="88e26-488">針對此類別插入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="88e26-488">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="88e26-489">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="88e26-489">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="88e26-490">第9章–完成場景設定</span><span class="sxs-lookup"><span data-stu-id="88e26-490">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="88e26-491">若要完成場景的設定，請將您在 [腳本] 資料夾中建立的每個腳本拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。</span><span class="sxs-lookup"><span data-stu-id="88e26-491">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="88e26-492">選取 **主要攝影機** ，然後查看 [偵測 *器] 面板*，您應該可以看到您已附加的每個腳本，而您會發現每個尚未設定的腳本都有參數。</span><span class="sxs-lookup"><span data-stu-id="88e26-492">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![設定相機參考目標。](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="88e26-494">若要正確設定這些參數，請遵循下列指示：</span><span class="sxs-lookup"><span data-stu-id="88e26-494">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="88e26-495">*MicrophoneManager*：</span><span class="sxs-lookup"><span data-stu-id="88e26-495">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="88e26-496">從 [階層] *面板* 中，將 [ **聽寫文字** ] 物件拖曳到 [ **聽寫文字** 參數] 值方塊中。</span><span class="sxs-lookup"><span data-stu-id="88e26-496">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="88e26-497">*行為*，從 [階層] *面板*：</span><span class="sxs-lookup"><span data-stu-id="88e26-497">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="88e26-498">將 **球體** 物件拖曳到 [ *球體* 參考目標] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="88e26-498">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="88e26-499">將 **圓柱** 拖曳至 [ *圓柱* 參考目標] 方塊。</span><span class="sxs-lookup"><span data-stu-id="88e26-499">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="88e26-500">將 **cube** 拖曳至 [ *cube* 參考目標] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="88e26-500">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="88e26-501">*注視*：</span><span class="sxs-lookup"><span data-stu-id="88e26-501">*Gaze*:</span></span>

        - <span data-ttu-id="88e26-502">將 [ *注視最大距離* ] 設定為 [ **300** ] (如果尚未) 。</span><span class="sxs-lookup"><span data-stu-id="88e26-502">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="88e26-503">結果看起來應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="88e26-503">The result should look like the image below:</span></span>

    ![現在已設定相機參考目標。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="88e26-505">第10章-在 Unity 編輯器中測試</span><span class="sxs-lookup"><span data-stu-id="88e26-505">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="88e26-506">測試是否已正確實行場景設定。</span><span class="sxs-lookup"><span data-stu-id="88e26-506">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="88e26-507">請確定：</span><span class="sxs-lookup"><span data-stu-id="88e26-507">Ensure that:</span></span>

-   <span data-ttu-id="88e26-508">所有的腳本都會附加至 **主要攝影機** 物件。</span><span class="sxs-lookup"><span data-stu-id="88e26-508">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="88e26-509">*主要相機偵測器面板* 中的所有欄位都已正確指派。</span><span class="sxs-lookup"><span data-stu-id="88e26-509">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="88e26-510">按下 *Unity 編輯器* 中的 [**播放**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="88e26-510">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="88e26-511">應用程式應該在附加的沉浸式耳機內執行。</span><span class="sxs-lookup"><span data-stu-id="88e26-511">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="88e26-512">請嘗試幾個語句，例如：</span><span class="sxs-lookup"><span data-stu-id="88e26-512">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="88e26-513">如果您在 Unity 主控台中看到關於預設音訊裝置變更的錯誤，場景可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="88e26-513">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="88e26-514">這是因為混合現實入口網站處理有內建麥克風的方式。</span><span class="sxs-lookup"><span data-stu-id="88e26-514">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="88e26-515">如果您看到此錯誤，只需停止場景並重新啟動，就應該會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="88e26-515">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="88e26-516">第11章-建立並側載 UWP 解決方案</span><span class="sxs-lookup"><span data-stu-id="88e26-516">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="88e26-517">確定應用程式在 Unity 編輯器中運作之後，您就可以開始建立和部署。</span><span class="sxs-lookup"><span data-stu-id="88e26-517">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="88e26-518">若要建立：</span><span class="sxs-lookup"><span data-stu-id="88e26-518">To Build:</span></span>

1.  <span data-ttu-id="88e26-519">按一下 [檔案] **> 儲存**]，以儲存目前的場景。</span><span class="sxs-lookup"><span data-stu-id="88e26-519">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="88e26-520">移至 [檔案 **> 組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-520">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="88e26-521">勾選稱為「 **Unity c # 專案** 」的方塊 (在建立 UWP 專案之後，用來查看和偵錯工具代碼。</span><span class="sxs-lookup"><span data-stu-id="88e26-521">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="88e26-522">按一下 [ **新增開啟的場景**]，然後按一下 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-522">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![[組建設定] 視窗](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="88e26-524">系統會提示您選取要在其中建立解決方案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="88e26-524">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="88e26-525">建立 *組建* 資料夾，然後在該資料夾內使用您選擇的適當名稱建立另一個資料夾。</span><span class="sxs-lookup"><span data-stu-id="88e26-525">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="88e26-526">按一下 [ **選取資料夾** ]，在該位置開始組建。</span><span class="sxs-lookup"><span data-stu-id="88e26-526">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="88e26-527">![建立組建資料夾 ](images/AzureLabs-Lab3-44.png)
     ![ 選取組建資料夾](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="88e26-527">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="88e26-528">Unity 完成組建之後 (可能需要一些時間) ，它應該會在您的組建位置開啟 **檔案總管** 視窗。</span><span class="sxs-lookup"><span data-stu-id="88e26-528">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="88e26-529">若要在本機電腦上部署：</span><span class="sxs-lookup"><span data-stu-id="88e26-529">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="88e26-530">在 *Visual Studio* 中，開啟 [上一章](#chapter-10--test-in-the-unity-editor)所建立的方案檔。</span><span class="sxs-lookup"><span data-stu-id="88e26-530">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="88e26-531">在 [ **方案平臺**] 中，選取 [ **x86**]、[ **本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-531">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="88e26-532">在 [ **方案** 設定] 中選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-532">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="88e26-533">在 Microsoft HoloLens 中，您可能會發現將此設定為 *遠端電腦* 較容易，因此不會行動網卡到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="88e26-533">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="88e26-534">不過，您也必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="88e26-534">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="88e26-535">知道您 HoloLens 的 **IP 位址** ，您可以在 *設定 > 網路 & 網際網路 > Wi-Fi > Advanced 選項* 中找到此位址;IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="88e26-535">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="88e26-536">確定已 **開啟\*\*\*\*開發人員模式**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >*。</span><span class="sxs-lookup"><span data-stu-id="88e26-536">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![部署應用程式](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="88e26-538">移至 [ **組建] 功能表** ，然後按一下 [ **部署方案** ]，將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="88e26-538">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="88e26-539">您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好可供啟動！</span><span class="sxs-lookup"><span data-stu-id="88e26-539">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="88e26-540">啟動後，應用程式會提示您授權 _麥克風_ 的存取權。</span><span class="sxs-lookup"><span data-stu-id="88e26-540">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="88e26-541">使用 *移動控制器*、 *語音輸入* 或 *鍵盤* 按 [ **是]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="88e26-541">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="88e26-542">第12章–改善您的 LUIS 服務</span><span class="sxs-lookup"><span data-stu-id="88e26-542">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="88e26-543">這一章十分重要，而且可能需要反復執行數次，因為它可協助改善 LUIS 服務的精確度：請確定您已完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="88e26-543">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="88e26-544">若要改善 LUIS 所提供的理解層級，您需要捕捉新的語句，並使用它們來重新定型您的 LUIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="88e26-544">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="88e26-545">例如，您可能已訓練 LUIS 來瞭解「增加」和「升遷」，但您不希望應用程式也能瞭解「放大」這類的文字嗎？</span><span class="sxs-lookup"><span data-stu-id="88e26-545">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="88e26-546">一旦使用您的應用程式數次之後，您所說的所有專案都將由 LUIS 收集，並可在 LUIS 入口網站中取得。</span><span class="sxs-lookup"><span data-stu-id="88e26-546">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="88e26-547">移至您的入口網站應用程式，並在此 [連結](https://www.luis.ai/home)之後登入。</span><span class="sxs-lookup"><span data-stu-id="88e26-547">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="88e26-548">使用您的 MS 認證登入後，請按一下您的 *應用程式名稱*。</span><span class="sxs-lookup"><span data-stu-id="88e26-548">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="88e26-549">按一下頁面左側的 [ **審核端點語句** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="88e26-549">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![複習語句](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="88e26-551">您將會看到您的混合現實應用程式傳送給 LUIS 的語句清單。</span><span class="sxs-lookup"><span data-stu-id="88e26-551">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![語句清單](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="88e26-553">您將會注意到一些醒目提示的 *實體*。</span><span class="sxs-lookup"><span data-stu-id="88e26-553">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="88e26-554">藉由將滑鼠游標停留在每個醒目提示的單字上方，您就可以檢查每個語句並判斷正確辨識的實體、哪些實體錯誤，以及遺漏了哪些實體。</span><span class="sxs-lookup"><span data-stu-id="88e26-554">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="88e26-555">在上述範例中，發現 "魚叉式" 一字已反白顯示為目標，因此必須更正錯誤，方法是將滑鼠游標移到單字上，然後按一下 [ **移除標籤**]。</span><span class="sxs-lookup"><span data-stu-id="88e26-555">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="88e26-556">![檢查語句 ](images/AzureLabs-Lab3-49.png)
 ![ 移除標籤影像](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="88e26-556">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="88e26-557">如果您找到完全錯誤的語句，您可以使用畫面右側的 [ **刪除** ] 按鈕將它們刪除。</span><span class="sxs-lookup"><span data-stu-id="88e26-557">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![刪除錯誤的語句](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="88e26-559">或者，如果您覺得 LUIS 已正確地解讀語句，您可以使用 [ **加入至對齊意圖** ] 按鈕來驗證它的理解。</span><span class="sxs-lookup"><span data-stu-id="88e26-559">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![新增至對齊的意圖](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="88e26-561">當您將所有顯示的語句排序之後，請嘗試並重載頁面，以查看是否有更多可用。</span><span class="sxs-lookup"><span data-stu-id="88e26-561">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="88e26-562">請務必盡可能重複此程式，以改善您的應用程式理解。</span><span class="sxs-lookup"><span data-stu-id="88e26-562">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="88e26-563">**祝您順利！**</span><span class="sxs-lookup"><span data-stu-id="88e26-563">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="88e26-564">您完成的 LUIS 整合式應用程式</span><span class="sxs-lookup"><span data-stu-id="88e26-564">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="88e26-565">恭喜您，您建立了一個利用 Azure Language Understanding 智慧服務的混合現實應用程式，以瞭解使用者所說的內容，並對該資訊採取行動。</span><span class="sxs-lookup"><span data-stu-id="88e26-565">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![實驗室結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="88e26-567">額外練習</span><span class="sxs-lookup"><span data-stu-id="88e26-567">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="88e26-568">練習1</span><span class="sxs-lookup"><span data-stu-id="88e26-568">Exercise 1</span></span>

<span data-ttu-id="88e26-569">在使用此應用程式時，您可能會注意到，如果您看著 Floor 物件，並要求變更其色彩，則會這樣做。</span><span class="sxs-lookup"><span data-stu-id="88e26-569">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="88e26-570">您是否可以用來避免應用程式變更地面色彩？</span><span class="sxs-lookup"><span data-stu-id="88e26-570">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="88e26-571">練習2</span><span class="sxs-lookup"><span data-stu-id="88e26-571">Exercise 2</span></span>

<span data-ttu-id="88e26-572">嘗試擴充 LUIS 和應用程式功能，為場景中的物件新增額外的功能;例如，根據使用者顯示的內容，在注視的位置建立新的物件，然後透過現有的命令，將這些物件與目前的場景物件一起使用。</span><span class="sxs-lookup"><span data-stu-id="88e26-572">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span>