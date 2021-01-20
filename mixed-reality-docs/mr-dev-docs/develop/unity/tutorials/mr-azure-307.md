---
title: MR 和 Azure 307-機器學習
description: 完成本課程，以瞭解如何在混合現實應用程式內執行 Azure Machine Learning Studio (傳統) 。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學術，unity，教學課程，api，機器學習，ml，machine learning studio，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 95213c3d17bbe0f0f81438d4808db142ad21c595
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583394"
---
# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="10471-104">MR 和 Azure 307：機器學習</span><span class="sxs-lookup"><span data-stu-id="10471-104">MR and Azure 307: Machine learning</span></span>

<br>

>[!NOTE]
><span data-ttu-id="10471-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="10471-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="10471-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="10471-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="10471-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="10471-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="10471-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="10471-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="10471-109">未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="10471-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="10471-110">當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。</span><span class="sxs-lookup"><span data-stu-id="10471-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

![最終產品-開始](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="10471-112">在此課程中，您將瞭解如何使用 Azure Machine Learning Studio (傳統) ，將 Machine Learning (ML) 功能新增至混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="10471-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio (classic).</span></span>

<span data-ttu-id="10471-113">*Azure Machine Learning Studio (傳統)* 是一項 Microsoft 服務，可為開發人員提供大量的機器學習演算法，協助您進行資料輸入、輸出、準備和視覺化。</span><span class="sxs-lookup"><span data-stu-id="10471-113">*Azure Machine Learning Studio (classic)* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="10471-114">您可以從這些元件開發預測性分析實驗、逐一查看，並使用它來定型您的模型。</span><span class="sxs-lookup"><span data-stu-id="10471-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="10471-115">在訓練之後，您可以讓您的模型在 Azure 雲端中運作，讓它可以對新資料進行評分。</span><span class="sxs-lookup"><span data-stu-id="10471-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="10471-116">如需詳細資訊，請造訪 [Azure Machine Learning Studio (傳統) 頁面](https://azure.microsoft.com/services/machine-learning-studio/)。</span><span class="sxs-lookup"><span data-stu-id="10471-116">For more information, visit the [Azure Machine Learning Studio (classic) page](https://azure.microsoft.com/services/machine-learning-studio/).</span></span>

<span data-ttu-id="10471-117">完成本課程之後，您將會有混合現實的沉浸式耳機應用程式，並已瞭解如何執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="10471-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="10471-118">提供 *Azure Machine Learning Studio (傳統)* 入口網站的銷售資料表格，並設計演算法來預測熱門專案的未來銷售。</span><span class="sxs-lookup"><span data-stu-id="10471-118">Provide a table of sales data to the *Azure Machine Learning Studio (classic)* portal, and design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="10471-119">建立 **Unity 專案**，它可以接收和解讀來自 ML 服務的預測資料。</span><span class="sxs-lookup"><span data-stu-id="10471-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="10471-120">透過在貨架上提供最受歡迎的銷售專案，以視覺化方式在 **Unity 專案** 中顯示 predication 的資料。</span><span class="sxs-lookup"><span data-stu-id="10471-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="10471-121">在您的應用程式中，您可以自行決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="10471-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="10471-122">本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="10471-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="10471-123">您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="10471-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="10471-124">本課程是獨立的教學課程，不會直接牽涉到任何其他混合的現實實驗室。</span><span class="sxs-lookup"><span data-stu-id="10471-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="10471-125">裝置支援</span><span class="sxs-lookup"><span data-stu-id="10471-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="10471-126">課程</span><span class="sxs-lookup"><span data-stu-id="10471-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="10471-127"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="10471-127"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="10471-128"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="10471-128"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="10471-129">MR 和 Azure 307：機器學習</span><span class="sxs-lookup"><span data-stu-id="10471-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="10471-130">✔️</span><span class="sxs-lookup"><span data-stu-id="10471-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="10471-131">✔️</span><span class="sxs-lookup"><span data-stu-id="10471-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="10471-132">雖然本課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機，您也可以將在本課程中學到的內容套用至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="10471-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="10471-133">當您依照課程的指示進行時，您將會看到有關您可能需要採用以支援 HoloLens 的任何變更的注意事項。</span><span class="sxs-lookup"><span data-stu-id="10471-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="10471-134">使用 HoloLens 時，您可能會注意到語音捕捉期間的一些回應。</span><span class="sxs-lookup"><span data-stu-id="10471-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10471-135">必要條件</span><span class="sxs-lookup"><span data-stu-id="10471-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="10471-136">本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="10471-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="10471-137">另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="10471-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="10471-138">您可以隨意使用最新的軟體（如 [ 安裝工具文章](../../install-the-tools.md)中所列），但不應假設此課程中的資訊會完全符合您在較新軟體中找到的資訊，而不是以下所列的資訊。</span><span class="sxs-lookup"><span data-stu-id="10471-138">You are free to use the latest software, as listed within the [install the tools article](../../install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="10471-139">本課程建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="10471-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="10471-140">開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)</span><span class="sxs-lookup"><span data-stu-id="10471-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="10471-141">啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="10471-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10471-142">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="10471-142">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10471-143">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="10471-143">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10471-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="10471-144">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="10471-145">[Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="10471-145">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="10471-146">適用于 Azure 設定和 ML 資料抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="10471-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="10471-147">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="10471-147">Before you start</span></span>

<span data-ttu-id="10471-148">為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="10471-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="10471-149">第1章-Azure 儲存體帳戶設定</span><span class="sxs-lookup"><span data-stu-id="10471-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="10471-150">若要使用 Azure Translator API，您必須將服務的實例設定為可供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="10471-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="10471-151">登入  [Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="10471-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="10471-152">如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="10471-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="10471-153">如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="10471-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="10471-154">登入後，按一下左側功能表中的 [ **儲存體帳戶** ]。</span><span class="sxs-lookup"><span data-stu-id="10471-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="10471-156">在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。</span><span class="sxs-lookup"><span data-stu-id="10471-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="10471-157">在 [ **儲存體帳戶** ] 索引標籤上，按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="10471-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="10471-159">在 [ **建立儲存體帳戶** ] 面板中：</span><span class="sxs-lookup"><span data-stu-id="10471-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="10471-160">為您的帳戶插入 **名稱** ，請注意，此欄位只接受數位和小寫字母。</span><span class="sxs-lookup"><span data-stu-id="10471-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="10471-161">在 [ **部署模型] 中，** 選取 [ **資源管理員**]。</span><span class="sxs-lookup"><span data-stu-id="10471-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="10471-162">針對 [ **帳戶類型**]，選取 **[儲存體 (一般用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="10471-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="10471-163">針對 [效能]，請選取 [標準]。</span><span class="sxs-lookup"><span data-stu-id="10471-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="10471-164">若 **為複寫** ，請選取 [ **讀取權限-異地-多餘儲存體] (GRS])**。</span><span class="sxs-lookup"><span data-stu-id="10471-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="10471-165">將 [ **需要安全傳輸** ] 保留為 **停用**。</span><span class="sxs-lookup"><span data-stu-id="10471-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="10471-166">選取 [訂用帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="10471-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="10471-167">選擇資源群組，或建立一個新的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="10471-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="10471-168">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="10471-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="10471-169">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。</span><span class="sxs-lookup"><span data-stu-id="10471-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="10471-170">如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="10471-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="10471-171">如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。</span><span class="sxs-lookup"><span data-stu-id="10471-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="10471-172">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="10471-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="10471-173">某些 Azure 資產僅適用于某些區域。</span><span class="sxs-lookup"><span data-stu-id="10471-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="10471-174">您也必須確認您已瞭解套用到此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="10471-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="10471-176">當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="10471-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="10471-177">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="10471-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio--classic"></a><span data-ttu-id="10471-179">第2章-Azure Machine Learning Studio (傳統) </span><span class="sxs-lookup"><span data-stu-id="10471-179">Chapter 2 - The Azure Machine Learning Studio  (classic)</span></span>

<span data-ttu-id="10471-180">若要使用 *Azure Machine Learning*，您必須將 Machine Learning 服務的實例設定為可供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="10471-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="10471-181">在 Azure 入口網站中，按一下左上角的 [ **新增** ]，然後搜尋 **Machine Learning Studio 工作區**，按 **enter**。</span><span class="sxs-lookup"><span data-stu-id="10471-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="10471-183">新頁面將提供 **Machine Learning Studio 工作區**  服務的描述。</span><span class="sxs-lookup"><span data-stu-id="10471-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="10471-184">在此提示的左下方，按一下 [ **建立** ] 按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="10471-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="10471-185">當您按一下 [ **建立**] 之後，就會出現一個面板，您必須在其中提供有關新 **Machine Learning Studio 服務** 的一些詳細資料：</span><span class="sxs-lookup"><span data-stu-id="10471-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="10471-186">為此服務實例插入您想要的 **工作區名稱** 。</span><span class="sxs-lookup"><span data-stu-id="10471-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="10471-187">選取 [訂用帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="10471-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="10471-188">選擇資源群組，或建立一個新的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="10471-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="10471-189">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="10471-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="10471-190">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。</span><span class="sxs-lookup"><span data-stu-id="10471-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="10471-191">如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="10471-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="10471-192">如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。</span><span class="sxs-lookup"><span data-stu-id="10471-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="10471-193">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="10471-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="10471-194">某些 Azure 資產僅適用于某些區域。</span><span class="sxs-lookup"><span data-stu-id="10471-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="10471-195">您應該使用您在上一章中用來建立 Azure 儲存體的相同資源群組。</span><span class="sxs-lookup"><span data-stu-id="10471-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="10471-196">在 [ **儲存體帳戶** ] 區段中，按一下 [ **使用現有** 的]，然後按一下下拉式功能表，然後按一下您在上一章所建立的 **儲存體帳戶** 。</span><span class="sxs-lookup"><span data-stu-id="10471-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="10471-197">從下拉式功能表中，為您選取適當的 **工作區定價層** 。</span><span class="sxs-lookup"><span data-stu-id="10471-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="10471-198">在 [ **Web 服務方案**] 區段中，按一下 [**建立\*\*\*\*新** 的]，然後在文字欄位中插入它的名稱。</span><span class="sxs-lookup"><span data-stu-id="10471-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="10471-199">從 [ **Web 服務方案定價層** ] 區段中，選取您選擇的定價層。</span><span class="sxs-lookup"><span data-stu-id="10471-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="10471-200">您可以免費使用稱為 **DEVTEST Standard** 的開發測試層。</span><span class="sxs-lookup"><span data-stu-id="10471-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="10471-201">您也必須確認您已瞭解套用到此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="10471-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="10471-202">按一下頁面底部的 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="10471-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="10471-204">當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="10471-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="10471-205">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="10471-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="10471-207">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="10471-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="10471-209">按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。</span><span class="sxs-lookup"><span data-stu-id="10471-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="10471-210">在顯示的頁面中，按一下 [ **其他連結** ] 區段下的 [ **啟動 Machine Learning Studio**]，這會將您的瀏覽器導向 **Machine Learning studio** 入口網站。</span><span class="sxs-lookup"><span data-stu-id="10471-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="10471-212">使用右上角或中央的 [登 **入** ] 按鈕，登入您的 Machine Learning Studio (傳統) 。</span><span class="sxs-lookup"><span data-stu-id="10471-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio (classic).</span></span>

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-classic-dataset-setup"></a><span data-ttu-id="10471-214">第3章-Machine Learning Studio (傳統) ：資料集設定</span><span class="sxs-lookup"><span data-stu-id="10471-214">Chapter 3 - The Machine Learning Studio (classic): Dataset setup</span></span>

<span data-ttu-id="10471-215">Machine Learning 演算法的其中一種方式就是分析現有的資料，然後根據現有的資料集嘗試預測未來的結果。</span><span class="sxs-lookup"><span data-stu-id="10471-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="10471-216">這通常表示您擁有的資料愈多，演算法在預測未來結果時的效能就越好。</span><span class="sxs-lookup"><span data-stu-id="10471-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="10471-217">系統會為您提供範例資料表，在此課程中稱為 [ProductsTableCSV，可在此下載](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。</span><span class="sxs-lookup"><span data-stu-id="10471-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10471-218">上述 .zip 檔案包含 **ProductsTableCSV** 和 **unitypackage**，您將在 [第6章](#chapter-6---importing-the-mlproducts-unity-package)中所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="10471-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="10471-219">這一章也會提供此封裝，但與 csv 檔案分開。</span><span class="sxs-lookup"><span data-stu-id="10471-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="10471-220">此範例資料集會在2017年每天的每個小時，包含最佳銷售物件的記錄。</span><span class="sxs-lookup"><span data-stu-id="10471-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio (傳統) ：資料集設定](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="10471-222">例如，在2017的第1天，下午 (小時 13) ，最暢銷的專案是 salt 和辣椒。</span><span class="sxs-lookup"><span data-stu-id="10471-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="10471-223">此範例資料表包含9998個專案。</span><span class="sxs-lookup"><span data-stu-id="10471-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="10471-224">回到 **Machine Learning Studio (傳統)** 入口網站，並新增此資料表作為 ML 的 **資料集** 。</span><span class="sxs-lookup"><span data-stu-id="10471-224">Head back to the **Machine Learning Studio (classic)** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="10471-225">若要這麼做，請按一下螢幕左下角的 [ **+ 新增** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="10471-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio (傳統) ：資料集設定](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="10471-227">區段會從底端開始，而左側會有導覽面板。</span><span class="sxs-lookup"><span data-stu-id="10471-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="10471-228">按一下 [資料集]，然後按一下 [**本機** 檔案] 中的 [**資料集**]。</span><span class="sxs-lookup"><span data-stu-id="10471-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio (傳統) ：資料集設定](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="10471-230">遵循下列步驟來上傳新的 **資料集** ：</span><span class="sxs-lookup"><span data-stu-id="10471-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="10471-231">[上傳] 視窗隨即出現，您可以在其中 **流覽** 硬碟以取得新的資料集。</span><span class="sxs-lookup"><span data-stu-id="10471-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio (傳統) ：資料集設定](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="10471-233">一旦選取後，再返回 [上傳] 視窗，請將核取方塊保留為未核取。</span><span class="sxs-lookup"><span data-stu-id="10471-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="10471-234">在下方的文字欄位中，輸入 **ProductsTableCSV.csv** 作為資料集的名稱， (不過應該自動新增) 。</span><span class="sxs-lookup"><span data-stu-id="10471-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="10471-235">使用 [ **類型**] 的下拉式功能表，選取 **標頭 ( .csv) 的 [一般 csv** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="10471-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="10471-236">按下 [上傳] 視窗右下角的刻度，將會上傳您的 **資料集** 。</span><span class="sxs-lookup"><span data-stu-id="10471-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-classic-the-experiment"></a><span data-ttu-id="10471-237">第4章-Machine Learning Studio (傳統) ：實驗</span><span class="sxs-lookup"><span data-stu-id="10471-237">Chapter 4 - The Machine Learning Studio (classic): The Experiment</span></span>

<span data-ttu-id="10471-238">建立您的機器學習系統之前，您必須先建立實驗，以驗證您的資料理論。</span><span class="sxs-lookup"><span data-stu-id="10471-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="10471-239">有了結果，您將知道您是否需要更多資料，或是資料和可能的結果之間沒有相互關聯。</span><span class="sxs-lookup"><span data-stu-id="10471-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="10471-240">若要開始建立實驗：</span><span class="sxs-lookup"><span data-stu-id="10471-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="10471-241">再次按一下頁面左下方的 [ **+ 新增**] 按鈕，然後按一下 [**實驗**  >  **空白實驗**]。</span><span class="sxs-lookup"><span data-stu-id="10471-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="10471-243">新的頁面會顯示為空白實驗：</span><span class="sxs-lookup"><span data-stu-id="10471-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="10471-244">從左側面板中，展開 [**儲存的資料集**  >  **我的資料集**]，並將 [ **ProductsTableCSV** ] 拖曳至 **實驗畫布**。</span><span class="sxs-lookup"><span data-stu-id="10471-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="10471-246">在左側面板中，展開 [**資料轉換**  >  **範例和分割**]。</span><span class="sxs-lookup"><span data-stu-id="10471-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="10471-247">然後將 **分割資料** 專案拖曳至 **實驗畫布**。</span><span class="sxs-lookup"><span data-stu-id="10471-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="10471-248">分割資料項目會將資料集分割成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="10471-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="10471-249">您將用來定型機器學習演算法的一個部分。</span><span class="sxs-lookup"><span data-stu-id="10471-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="10471-250">第二個部分將用來評估所產生之演算法的精確度。</span><span class="sxs-lookup"><span data-stu-id="10471-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="10471-252">在右面板中， (選取畫布上的分割資料項目時) ，將 **第一個輸出資料集中的資料列分數** 編輯為 **0.7**。</span><span class="sxs-lookup"><span data-stu-id="10471-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="10471-253">這會將資料分割成兩個部分，第一個部分會是70% 的資料，而第二個部分則是剩餘的30%。</span><span class="sxs-lookup"><span data-stu-id="10471-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="10471-254">若要確保資料會隨機分割，請確定已核取 [ **隨機分割** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="10471-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="10471-256">將連接從畫布上的 **ProductsTableCSV** 專案基底拖曳至分割資料項目頂端。</span><span class="sxs-lookup"><span data-stu-id="10471-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="10471-257">這會連接專案，並將 **ProductsTableCSV** 資料集輸出 (資料) 傳送至分割資料輸入。</span><span class="sxs-lookup"><span data-stu-id="10471-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="10471-259">在左側的 **實驗** 面板中，展開 [ **Machine Learning**  >  **訓練**]。</span><span class="sxs-lookup"><span data-stu-id="10471-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="10471-260">將 [ **定型模型** ] 專案拖曳至實驗畫布。</span><span class="sxs-lookup"><span data-stu-id="10471-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="10471-261">您的畫布看起來應該像下面這樣。</span><span class="sxs-lookup"><span data-stu-id="10471-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="10471-263">從 **_ 分割資料項目的 _左下方_\*_**\* 將連接拖曳至 **定型模型** 專案的 **右上方**。</span><span class="sxs-lookup"><span data-stu-id="10471-263">From the **_bottom left_*_ of the _\* Split Data*\* item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="10471-264">定型模型會使用資料集的前70% 分割來訓練演算法。</span><span class="sxs-lookup"><span data-stu-id="10471-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="10471-266">選取畫布上的 [ **定型模型** ] 專案，然後在瀏覽器視窗右側的 [ **屬性** ] 面板中 () 按一下 [啟動資料 **行選取器** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="10471-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="10471-267">在文字方塊中輸入 **product** ，然後按下 **enter**， *product* 將設定為數據行來定型預測。</span><span class="sxs-lookup"><span data-stu-id="10471-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="10471-268">在此之後，請按一下右下角的 **刻度** ，以關閉選取對話方塊。</span><span class="sxs-lookup"><span data-stu-id="10471-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="10471-270">您將定型 **多元羅吉斯回歸** 演算法，以根據當天的小時和日期來預測最暢銷的 **產品** 。</span><span class="sxs-lookup"><span data-stu-id="10471-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="10471-271">這份檔涵蓋了 Azure Machine Learning studio 所提供之不同演算法的詳細資料，但您可以從[Machine Learning 演算法](/azure/machine-learning/studio/algorithm-cheat-sheet)的功能提要中找到更多詳細資料</span><span class="sxs-lookup"><span data-stu-id="10471-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="10471-272">從左側的實驗專案面板中，展開 [ **Machine Learning**  >  **初始化模型**  >  **分類**]，然後將 [**多元羅吉斯回歸**] 專案拖曳至實驗畫布。</span><span class="sxs-lookup"><span data-stu-id="10471-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="10471-273">將 **多元羅吉斯回歸** 底部的輸出連接到 **定型模型** 專案的左上角輸入。</span><span class="sxs-lookup"><span data-stu-id="10471-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="10471-275">在左側面板中的實驗專案清單中，展開 [ **Machine Learning**  >  **分數**]，然後將 [**評分模型**] 專案拖曳至畫布上。</span><span class="sxs-lookup"><span data-stu-id="10471-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="10471-276">將 **定型模型** 底部的輸出連接到 **評分模型** 的左上角輸入。</span><span class="sxs-lookup"><span data-stu-id="10471-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="10471-277">將 **分割資料** 的右下角輸出連接到 **評分模型** 專案的右上角輸入。</span><span class="sxs-lookup"><span data-stu-id="10471-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="10471-279">在左側面板中的 **實驗** 專案清單中，展開 [ **Machine Learning**  >  **評估**]，然後將 [**評估模型**] 專案拖曳至畫布上。</span><span class="sxs-lookup"><span data-stu-id="10471-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="10471-280">將 **評分模型** 的輸出連接到 **評估模型** 的左上角輸入。</span><span class="sxs-lookup"><span data-stu-id="10471-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="10471-282">您已建立第一個 Machine Learning 實驗。</span><span class="sxs-lookup"><span data-stu-id="10471-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="10471-283">您現在可以儲存並執行實驗。</span><span class="sxs-lookup"><span data-stu-id="10471-283">You can now save and run the experiment.</span></span> <span data-ttu-id="10471-284">在頁面底部的功能表中，按一下 [ **儲存** ] 按鈕以儲存您的實驗，然後按一下 [ **執行** ] 以開始實驗。</span><span class="sxs-lookup"><span data-stu-id="10471-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="10471-286">您可以在畫布右上方看到實驗的 **狀態** 。</span><span class="sxs-lookup"><span data-stu-id="10471-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="10471-287">等候幾分鐘，讓實驗完成。</span><span class="sxs-lookup"><span data-stu-id="10471-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="10471-288">如果您有很大的 (實際) 資料集，可能是實驗可能需要數小時的時間才能執行。</span><span class="sxs-lookup"><span data-stu-id="10471-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="10471-290">以滑鼠右鍵按一下畫布中的 [ **評估模型** ] 專案，然後從內容功能表中將滑鼠停留在 **評估結果** 上方，然後選取 [ **視覺化**]。</span><span class="sxs-lookup"><span data-stu-id="10471-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="10471-292">將會顯示評估結果，顯示預測的結果與實際結果。</span><span class="sxs-lookup"><span data-stu-id="10471-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="10471-293">這會使用先前分割的原始資料集30% 來評估模型。</span><span class="sxs-lookup"><span data-stu-id="10471-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="10471-294">您可以看到結果並不理想，最好是每個資料列中的最大數位都是資料行中反白顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="10471-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="10471-296">關閉 **結果**。</span><span class="sxs-lookup"><span data-stu-id="10471-296">Close the **Results**.</span></span>

24. <span data-ttu-id="10471-297">若要使用新定型的 Machine Learning 模型，您需要將它公開為 **Web 服務**。</span><span class="sxs-lookup"><span data-stu-id="10471-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="10471-298">若要這樣做，請在頁面底部的功能表中按一下 [ **設定 Web 服務** ] 功能表項目，然後按一下 [預測性 **Web 服務**]。</span><span class="sxs-lookup"><span data-stu-id="10471-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="10471-300">將會建立新的索引標籤，併合並定型模型來建立新的 web 服務。</span><span class="sxs-lookup"><span data-stu-id="10471-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="10471-301">在頁面底部的功能表中，按一下 [ **儲存**]，然後按一下 [ **執行**]。</span><span class="sxs-lookup"><span data-stu-id="10471-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="10471-302">您會看到實驗畫布右上角的狀態更新。</span><span class="sxs-lookup"><span data-stu-id="10471-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="10471-304">完成執行之後，頁面底部會出現 [ **部署 Web 服務** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="10471-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="10471-305">您可以開始部署 web 服務。</span><span class="sxs-lookup"><span data-stu-id="10471-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="10471-306">按一下頁面底部功能表中的 [ **部署 Web 服務** (傳統) 。</span><span class="sxs-lookup"><span data-stu-id="10471-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="10471-308">您的瀏覽器可能會提示您允許快顯視窗，您應該 **允許** 該快顯視窗，但如果 [部署] 頁面未顯示，您可能需要再次按 [ **部署 Web 服務** ]。</span><span class="sxs-lookup"><span data-stu-id="10471-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="10471-309">一旦建立實驗之後，您會被重新導向至您將在其中顯示 **API 金鑰** 的 **儀表板** 頁面。</span><span class="sxs-lookup"><span data-stu-id="10471-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="10471-310">現在將它複製到「記事本」中，您很快就會在程式碼中需要它。</span><span class="sxs-lookup"><span data-stu-id="10471-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="10471-311">記下您的 API 金鑰之後，請在金鑰底下的 [**預設端點**] 區段中，按一下 [**要求/回應**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="10471-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="10471-313">如果您按一下此頁面中的 [測試]，就可以輸入輸入資料並查看輸出。</span><span class="sxs-lookup"><span data-stu-id="10471-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="10471-314">輸入 **日** 和 **小時**。</span><span class="sxs-lookup"><span data-stu-id="10471-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="10471-315">將 **產品** 專案保留空白。</span><span class="sxs-lookup"><span data-stu-id="10471-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="10471-316">然後按一下 [ **確認** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="10471-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="10471-317">頁面底部的輸出會顯示 JSON，代表每項產品選擇的可能性。</span><span class="sxs-lookup"><span data-stu-id="10471-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="10471-318">新的網頁隨即開啟，其中會顯示 Machine Learning Studio (傳統) 所需之要求結構的指示和一些範例。</span><span class="sxs-lookup"><span data-stu-id="10471-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio (classic).</span></span> <span data-ttu-id="10471-319">將此頁面中顯示的 **要求 URI** 複製到您的 [記事本] 中。</span><span class="sxs-lookup"><span data-stu-id="10471-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="10471-321">您現在已建立機器學習系統，以根據歷程記錄購買資料提供最可能的產品，並與一年中的時間和日的時間產生關聯。</span><span class="sxs-lookup"><span data-stu-id="10471-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="10471-322">若要呼叫 web 服務，您將需要服務端點的 URL 和服務的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="10471-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="10471-323">從頂端功能表 **中，按一下 [取用] 索引** 標籤。</span><span class="sxs-lookup"><span data-stu-id="10471-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="10471-324">[ **取用** 資訊] 頁面會顯示從您的程式碼呼叫 web 服務所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="10471-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="10471-325">取得 **主要金鑰** 和 **要求-回應** URL 的複本。</span><span class="sxs-lookup"><span data-stu-id="10471-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="10471-326">您將在下一章中需要這些功能。</span><span class="sxs-lookup"><span data-stu-id="10471-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="10471-327">第5章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="10471-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="10471-328">設定及測試您的混合現實沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="10471-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="10471-329">在此課程中，您將 **不** 需要移動控制器。</span><span class="sxs-lookup"><span data-stu-id="10471-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="10471-330">如果您需要設定沉浸式耳機的支援，請按一下 [這裡](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="10471-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="10471-331">開啟 **unity** ，然後建立名為 **MR \_ MachineLearning** 的新 unity 專案。</span><span class="sxs-lookup"><span data-stu-id="10471-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="10471-332">請確定專案類型設定為 **3d**。</span><span class="sxs-lookup"><span data-stu-id="10471-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="10471-333">在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="10471-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="10471-334">移至 [**編輯**  >  **喜好** 設定]，然後在新視窗中，流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="10471-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="10471-335">將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="10471-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="10471-336">關閉 [ **喜好** 設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="10471-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="10471-337">接下來，移 **至 [** 檔案  >  **組建設定**]，然後按一下 [*_切換平臺_* _] 按鈕，將平臺切換至 **通用 Windows 平臺**。</span><span class="sxs-lookup"><span data-stu-id="10471-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the \**_Switch Platform_* _ button.</span></span>

4.  <span data-ttu-id="10471-338">也請確定：</span><span class="sxs-lookup"><span data-stu-id="10471-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="10471-339">_ *目標裝置*\* 設定為 **任何裝置**。</span><span class="sxs-lookup"><span data-stu-id="10471-339">_ *Target Device*\* is set to **Any Device**.</span></span>

        > <span data-ttu-id="10471-340">針對 Microsoft HoloLens，請將 **目標裝置** 設定為 *HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="10471-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="10471-341">**組建類型** 設定為 **D3D**。</span><span class="sxs-lookup"><span data-stu-id="10471-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="10471-342">**SDK** 設定為 [ **最新安裝**]。</span><span class="sxs-lookup"><span data-stu-id="10471-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="10471-343">**Visual Studio 版本** 設定為 [ **最新安裝**]。</span><span class="sxs-lookup"><span data-stu-id="10471-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="10471-344">**組建並執行** 設定為 [ **本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="10471-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="10471-345">請不要擔心立即設定 **幕後** ，因為稍後會提供。</span><span class="sxs-lookup"><span data-stu-id="10471-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="10471-346">其餘設定應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="10471-346">The remaining settings should be left as default for now.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="10471-348">在 [ **組建設定** ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 **器** 所在空間中的相關面板。</span><span class="sxs-lookup"><span data-stu-id="10471-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="10471-349">在此面板中，需要驗證幾個設定：</span><span class="sxs-lookup"><span data-stu-id="10471-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="10471-350">在 [ **其他設定** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="10471-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="10471-351">**腳本\*\*\*\*執行階段版本** 應該是 **實驗** ( .net 4.6 對等) </span><span class="sxs-lookup"><span data-stu-id="10471-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="10471-352">**腳本後端** 應該是 \**_.net_* _</span><span class="sxs-lookup"><span data-stu-id="10471-352">**Scripting Backend** should be \**_.NET_* _</span></span>

        3. <span data-ttu-id="10471-353">_ *API 相容性層級*\* 應為 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="10471-353">_ *API Compatibility Level*\* should be **.NET 4.6**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="10471-355">在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：</span><span class="sxs-lookup"><span data-stu-id="10471-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="10471-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="10471-356">**InternetClient**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="10471-358">在面板的 [ **XR 設定**] 中，在 [設定] (找到的 [**發佈設定**]) 、[支援的滴答 **虛擬事實**]，確定已新增 **Windows Mixed Reality SDK**</span><span class="sxs-lookup"><span data-stu-id="10471-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="10471-360">回到 **組建設定**： *Unity c #* 專案不再呈現灰色;勾選此方塊旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="10471-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="10471-361">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="10471-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="10471-362">將專案儲存 (檔 **> 儲存專案**) 。</span><span class="sxs-lookup"><span data-stu-id="10471-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="10471-363">第6章-匯入 MLProducts Unity 套件</span><span class="sxs-lookup"><span data-stu-id="10471-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="10471-364">在此課程中，您將需要下載名為 [**Azure-MR-307. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)的 Unity 資產套件。</span><span class="sxs-lookup"><span data-stu-id="10471-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="10471-365">這個套件會在場景中完成，其中包含該預建中的所有物件，因此您可以專注于讓它全部運作。</span><span class="sxs-lookup"><span data-stu-id="10471-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="10471-366">由於場景設定結構的目的，只會保留公用變數，因此會提供 **ShelfKeeper** 腳本。</span><span class="sxs-lookup"><span data-stu-id="10471-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="10471-367">您將需要進行其他所有章節。</span><span class="sxs-lookup"><span data-stu-id="10471-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="10471-368">若要匯入此套件：</span><span class="sxs-lookup"><span data-stu-id="10471-368">To import this package:</span></span>

1.  <span data-ttu-id="10471-369">使用 Unity 儀表板，然後在畫面頂端的功能表中按一下 [ **資產** ]，再按一下 [匯 **入封裝]、[自訂套件**]。</span><span class="sxs-lookup"><span data-stu-id="10471-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![匯入 MLProducts Unity 套件](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="10471-371">使用檔案選擇器選取 **Azure unitypackage** 套件，然後按一下 [ **開啟**]。</span><span class="sxs-lookup"><span data-stu-id="10471-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="10471-372">系統會向您顯示此資產的元件清單。</span><span class="sxs-lookup"><span data-stu-id="10471-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="10471-373">按一下 [匯 **入**] 以確認匯入。</span><span class="sxs-lookup"><span data-stu-id="10471-373">Confirm the import by clicking **Import**.</span></span>

    ![匯入 MLProducts Unity 套件](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="10471-375">匯入完成後，您會注意到您的 Unity **專案面板** 中出現一些新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="10471-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="10471-376">這些是3D 模型，以及屬於您將使用之預先製作場景一部分的個別材質。</span><span class="sxs-lookup"><span data-stu-id="10471-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="10471-377">您將在本課程中撰寫大部分的程式碼。</span><span class="sxs-lookup"><span data-stu-id="10471-377">You will write the majority of the code in this course.</span></span>

    ![匯入 MLProducts Unity 套件](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="10471-379">在 [ **專案面板** ] 資料夾中，按一下 [ **場景** ] 資料夾，然後按兩下 (中稱為 **MR_MachineLearningScene**) 的場景。</span><span class="sxs-lookup"><span data-stu-id="10471-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="10471-380">場景會開啟 (請參閱下圖) 。</span><span class="sxs-lookup"><span data-stu-id="10471-380">The scene will open (see image below).</span></span> <span data-ttu-id="10471-381">如果紅色菱形遺失，只要按一下 [**遊戲] 面板** 右上方的 [ **Gizmos** ] 按鈕即可。</span><span class="sxs-lookup"><span data-stu-id="10471-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![匯入 MLProducts Unity 套件](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="10471-383">第7章-在 Unity 中檢查 Dll</span><span class="sxs-lookup"><span data-stu-id="10471-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="10471-384">若要利用 JSON 程式庫 (用於序列化和還原序列化) ，Newtonsoft DLL 已使用您帶入的封裝來執行。</span><span class="sxs-lookup"><span data-stu-id="10471-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="10471-385">程式庫應該具有正確的設定，但值得檢查 (特別是當您遇到無法) 的程式碼問題時。</span><span class="sxs-lookup"><span data-stu-id="10471-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="10471-386">操作方法：</span><span class="sxs-lookup"><span data-stu-id="10471-386">To do so:</span></span>

-  <span data-ttu-id="10471-387">以滑鼠左鍵按一下 [外掛程式] 資料夾內的 Newtonsoft 檔案，然後查看 [偵測 **器] 面板**。</span><span class="sxs-lookup"><span data-stu-id="10471-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="10471-388">請確定 **任何平臺** 都核取。</span><span class="sxs-lookup"><span data-stu-id="10471-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="10471-389">移至 [ **UWP]** 索引標籤，並確定 [ **不處理** ] 為 [核取]。</span><span class="sxs-lookup"><span data-stu-id="10471-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![匯入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="10471-391">第8章-建立 ShelfKeeper 類別</span><span class="sxs-lookup"><span data-stu-id="10471-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="10471-392">**ShelfKeeper** 類別裝載的方法會控制在場景中衍生的 UI 和產品。</span><span class="sxs-lookup"><span data-stu-id="10471-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="10471-393">在匯入的套件中，您將被授與這個類別，但它並不完整。</span><span class="sxs-lookup"><span data-stu-id="10471-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="10471-394">現在完成該類別的時機：</span><span class="sxs-lookup"><span data-stu-id="10471-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="10471-395">按兩下 [**腳本**] 資料夾中的 **ShelfKeeper** 腳本，以 **Visual Studio 2017** 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="10471-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="10471-396">將腳本中的所有程式碼取代為下列程式碼，此程式碼會設定時間和日期，並且具有可顯示產品的方法。</span><span class="sxs-lookup"><span data-stu-id="10471-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="10471-397">返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。</span><span class="sxs-lookup"><span data-stu-id="10471-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="10471-398">回到 Unity 編輯器，確認 **ShelfKeeper** 類別看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="10471-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="10471-400">如果您的腳本沒有參考目標 (亦即 *日期 (文字網格)*) ，只要將對應的物件從 [階層] **面板** 拖曳到目標欄位即可。</span><span class="sxs-lookup"><span data-stu-id="10471-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="10471-401">如有需要，請參閱下面的說明：</span><span class="sxs-lookup"><span data-stu-id="10471-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="10471-402">在 **ShelfKeeper** 元件腳本內，以滑鼠左鍵按一下產生 **點** 陣列來開啟它。</span><span class="sxs-lookup"><span data-stu-id="10471-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="10471-403">子區段會顯示為 [ **大小**]，指出陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="10471-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="10471-404">在 [**大小**] 旁的文字方塊中輸入 **3** ，然後按 **enter** 鍵，即可在下方建立三個位置。</span><span class="sxs-lookup"><span data-stu-id="10471-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="10471-405">**在階層** 中，以滑鼠左鍵按一下) 旁邊的箭號，以展開 **時間顯示** 物件 (。</span><span class="sxs-lookup"><span data-stu-id="10471-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="10471-406">接著按一下 _ 階層中的 \**_主要攝影機_*_\*\*\*，讓偵測 **器** 顯示其資訊。</span><span class="sxs-lookup"><span data-stu-id="10471-406">Next click the \**_Main Camera_*_ from within the _\* Hierarchy\*\*, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="10471-407">在 [階層]**面板** 中選取 **主要攝影機**。</span><span class="sxs-lookup"><span data-stu-id="10471-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="10471-408">將 [**日期**] 和 [**時間**] 物件從 [階層]**面板** 拖曳到 **ShelfKeeper** 元件中的 **主攝影機** 偵測 **器** 內的 **日期文字** 和 **時間文字** 位置。</span><span class="sxs-lookup"><span data-stu-id="10471-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="10471-409">將 [階層]**面板** 中的 [產生 **點**] (從 [*貨架*] 物件底下，) 到產生 **點** 陣列底下的 **3** 個 **專案參考目標**，如影像所示。</span><span class="sxs-lookup"><span data-stu-id="10471-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="10471-411">第9章-建立 ProductPrediction 類別</span><span class="sxs-lookup"><span data-stu-id="10471-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="10471-412">您即將建立的下一個類別是 **ProductPrediction** 類別。</span><span class="sxs-lookup"><span data-stu-id="10471-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="10471-413">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="10471-413">This class is responsible for:</span></span>

-   <span data-ttu-id="10471-414">查詢 **Machine Learning 服務** 實例，並提供目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="10471-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="10471-415">將 JSON 回應還原序列化成可用的資料。</span><span class="sxs-lookup"><span data-stu-id="10471-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="10471-416">解讀資料，並抓取3個建議的產品。</span><span class="sxs-lookup"><span data-stu-id="10471-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="10471-417">呼叫 **ShelfKeeper** 類別方法來顯示場景中的資料。</span><span class="sxs-lookup"><span data-stu-id="10471-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="10471-418">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="10471-418">To create this class:</span></span>

1.  <span data-ttu-id="10471-419">移至 [**專案] 面板** 中的 [**腳本**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="10471-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="10471-420">以滑鼠右鍵按一下資料夾內的 [**建立**  >  **c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="10471-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="10471-421">呼叫腳本 **ProductPrediction**。</span><span class="sxs-lookup"><span data-stu-id="10471-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="10471-422">按兩下新的 **ProductPrediction** 腳本，以 **Visual Studio 2017** 開啟。</span><span class="sxs-lookup"><span data-stu-id="10471-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="10471-423">如果出現 [偵測 **到檔案修改** ] 對話方塊，請按一下 [*_重載方案_*]。</span><span class="sxs-lookup"><span data-stu-id="10471-423">If the **File Modification Detected** dialog pops up, click \**_Reload Solution_*.</span></span>

5.  <span data-ttu-id="10471-424">將下列命名空間新增至 ProductPrediction 類別的頂端：</span><span class="sxs-lookup"><span data-stu-id="10471-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="10471-425">在 **ProductPrediction** 類別內插入下列兩個物件，這些物件是由一些嵌套類別所組成。</span><span class="sxs-lookup"><span data-stu-id="10471-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="10471-426">這些類別是用來將 Machine Learning 服務的 JSON 序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="10471-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="10471-427">然後，將下列變數新增至上述程式碼的上方 (，讓 JSON 相關程式碼位於腳本底部、所有其他程式碼底下，而不是) ：</span><span class="sxs-lookup"><span data-stu-id="10471-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="10471-428">請務必將 Machine Learning 入口網站中的 **主要金鑰** 和 **要求-回應端點** 插入這裡的變數中。</span><span class="sxs-lookup"><span data-stu-id="10471-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="10471-429">下列影像顯示您從哪裡取得金鑰和端點的位置。</span><span class="sxs-lookup"><span data-stu-id="10471-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="10471-432">在 **Start ( # B1** 方法中插入此程式碼。</span><span class="sxs-lookup"><span data-stu-id="10471-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="10471-433">當類別初始化時，會呼叫 **Start ( # B1** 方法：</span><span class="sxs-lookup"><span data-stu-id="10471-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="10471-434">以下是從 Windows 收集日期和時間的方法，並將它轉換成我們的 Machine Learning 實驗可以用來與資料表中儲存的資料進行比較的格式。</span><span class="sxs-lookup"><span data-stu-id="10471-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="10471-435">您可以 **刪除** **( # B1** 方法的更新，因為此類別將不會使用它。</span><span class="sxs-lookup"><span data-stu-id="10471-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="10471-436">新增下列方法，以將目前的日期和時間傳達給 Machine Learning 端點，並接收 JSON 格式的回應。</span><span class="sxs-lookup"><span data-stu-id="10471-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="10471-437">新增下列方法，其負責將 JSON 回應還原序列化，並將還原序列化的結果傳達給 **ShelfKeeper** 類別。</span><span class="sxs-lookup"><span data-stu-id="10471-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="10471-438">此結果將會是預測為最新日期和時間銷售的三個專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="10471-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="10471-439">將下列程式碼插入至 **ProductPrediction** 類別，在先前的方法下方。</span><span class="sxs-lookup"><span data-stu-id="10471-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="10471-440">儲存 **Visual Studio** 並回到 **Unity**。</span><span class="sxs-lookup"><span data-stu-id="10471-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="10471-441">將 [ **ProductPrediction** ] 類別腳本從 [ **腳本** ] 資料夾拖曳至 [ **主要攝影機** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="10471-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="10471-442">儲存場景和專案 **檔**  >  **儲存場景/** 檔案  >  **儲存專案**。</span><span class="sxs-lookup"><span data-stu-id="10471-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="10471-443">第10章-建立 UWP 解決方案</span><span class="sxs-lookup"><span data-stu-id="10471-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="10471-444">現在將您的專案建立為 UWP 解決方案，讓它可以獨立應用程式的形式執行。</span><span class="sxs-lookup"><span data-stu-id="10471-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="10471-445">若要建立：</span><span class="sxs-lookup"><span data-stu-id="10471-445">To Build:</span></span>

1.  <span data-ttu-id="10471-446">按一下 [檔案  >  **儲存場景**] 以儲存目前的場景。</span><span class="sxs-lookup"><span data-stu-id="10471-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="10471-447">移至 **檔案**  >  **組建設定**</span><span class="sxs-lookup"><span data-stu-id="10471-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="10471-448">核取稱為 **Unity c # 專案** 的方塊 (這很重要，因為它可讓您在組建完成) 之後編輯類別。</span><span class="sxs-lookup"><span data-stu-id="10471-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="10471-449">按一下 [ **新增開啟的場景**]，</span><span class="sxs-lookup"><span data-stu-id="10471-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="10471-450">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="10471-450">Click **Build**.</span></span>

    ![打造 UWP 解決方案](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="10471-452">系統會提示您選取要在其中建立解決方案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="10471-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="10471-453">建立 **組建** 資料夾，然後在該資料夾內使用您選擇的適當名稱建立另一個資料夾。</span><span class="sxs-lookup"><span data-stu-id="10471-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="10471-454">按一下新資料夾，然後按一下 [ **選取資料夾**]，在該位置開始組建。</span><span class="sxs-lookup"><span data-stu-id="10471-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![打造 UWP 解決方案](images/AzureLabs-Lab7-55.png)

    ![打造 UWP 解決方案](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="10471-457">Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。</span><span class="sxs-lookup"><span data-stu-id="10471-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="10471-458">第11章-部署應用程式</span><span class="sxs-lookup"><span data-stu-id="10471-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="10471-459">若要部署您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="10471-459">To deploy your application:</span></span>

1.  <span data-ttu-id="10471-460">流覽至您的新 Unity 組建 (**應用程式** 資料夾) ，然後以 **Visual Studio** 開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="10471-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="10471-461">當 Visual Studio 開啟時，您需要還原 NuGet 套件，只要以滑鼠右鍵按一下您的 MachineLearningLab_Build 解決方案，從 Visual Studio) 右邊的方案總管 (，然後按一下 [還原 NuGet 套件] 即可完成：</span><span class="sxs-lookup"><span data-stu-id="10471-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![新增 NuGet 套件](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="10471-463">在 [方案設定] 中選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="10471-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="10471-464">在 [方案平臺] 中，選取 [ **x86**]、[ **本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="10471-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="10471-465">在 Microsoft HoloLens 中，您可能會發現將此設定為 *遠端電腦* 較容易，因此不會行動網卡到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="10471-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="10471-466">不過，您也必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="10471-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="10471-467">知道您 HoloLens 的 **IP 位址** ，您可以在 *設定 > 網路 & 網際網路 > Wi-Fi > Advanced 選項* 中找到此位址;IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="10471-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="10471-468">確定已 **開啟\*\*\*\*開發人員模式**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >*。</span><span class="sxs-lookup"><span data-stu-id="10471-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![新增 NuGet 套件](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="10471-470">移至 [ **組建] 功能表** ，然後按一下 [ **部署方案** ]，將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="10471-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="10471-471">您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好要啟動。</span><span class="sxs-lookup"><span data-stu-id="10471-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="10471-472">當您執行混合現實應用程式時，您將會看到在 Unity 場景中設定的基準，而且從初始化，將會提取您在 Azure 中設定的資料。</span><span class="sxs-lookup"><span data-stu-id="10471-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="10471-473">資料將會在您的應用程式中還原序列化，而您目前日期和時間的三個主要結果將以視覺化方式提供，做為三種模型。</span><span class="sxs-lookup"><span data-stu-id="10471-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="10471-474">您完成的 Machine Learning 應用程式</span><span class="sxs-lookup"><span data-stu-id="10471-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="10471-475">恭喜您，您建立了一個混合現實應用程式，利用 Azure Machine Learning 進行資料預測並顯示在您的場景中。</span><span class="sxs-lookup"><span data-stu-id="10471-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![新增 NuGet 套件](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="10471-477">練習</span><span class="sxs-lookup"><span data-stu-id="10471-477">Exercise</span></span>

<span data-ttu-id="10471-478">**練習1**</span><span class="sxs-lookup"><span data-stu-id="10471-478">**Exercise 1**</span></span>

<span data-ttu-id="10471-479">以您應用程式的排序次序進行實驗，並在貨架上顯示三個最下方的預測，因為這項資料可能也很有用。</span><span class="sxs-lookup"><span data-stu-id="10471-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="10471-480">**練習2**</span><span class="sxs-lookup"><span data-stu-id="10471-480">**Exercise 2**</span></span>

<span data-ttu-id="10471-481">使用 **Azure 資料表** 會以氣象資訊填入新的資料表，並使用資料來建立新的實驗。</span><span class="sxs-lookup"><span data-stu-id="10471-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>