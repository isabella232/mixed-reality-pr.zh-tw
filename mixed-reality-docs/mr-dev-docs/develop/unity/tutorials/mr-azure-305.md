---
title: HoloLens (第1代) 和 Azure 305-功能和儲存體
description: 完成本課程，以瞭解如何在混合現實應用程式內實行 Azure 儲存體和功能。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學院，unity，教學課程，api，函式，儲存體，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: b55acaf003a1cdf50a5a78e48fdf05a9ab07d0d6
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730545"
---
# <a name="hololens-1st-gen-and-azure-305-functions-and-storage"></a><span data-ttu-id="c9259-104">HoloLens (第1代) 和 Azure 305：功能和儲存體</span><span class="sxs-lookup"><span data-stu-id="c9259-104">HoloLens (1st gen) and Azure 305: Functions and storage</span></span>

<br>

>[!NOTE]
><span data-ttu-id="c9259-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="c9259-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c9259-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="c9259-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c9259-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="c9259-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c9259-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="c9259-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c9259-109">未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="c9259-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c9259-110">當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。</span><span class="sxs-lookup"><span data-stu-id="c9259-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

![最終產品-開始](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="c9259-112">在此課程中，您將瞭解如何在混合現實應用程式中建立和使用 Azure Functions，並將資料與 Azure 儲存體資源儲存在一起。</span><span class="sxs-lookup"><span data-stu-id="c9259-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="c9259-113">*Azure Functions* 是一項 Microsoft 服務，可讓開發人員在 Azure 中執行一小段程式碼，也就是「函數」。</span><span class="sxs-lookup"><span data-stu-id="c9259-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="c9259-114">這可提供將工作委派給雲端的方法，而不是您的本機應用程式，這可能有許多優點。</span><span class="sxs-lookup"><span data-stu-id="c9259-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="c9259-115">*Azure Functions* 支援數種開發語言，包括 C \# 、F \# 、Node.js、JAVA 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="c9259-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="c9259-116">如需詳細資訊，請造訪 [Azure Functions 文章](/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="c9259-116">For more information, visit the [Azure Functions article](/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="c9259-117">*Azure 儲存體* 是一項 Microsoft 雲端服務，可讓開發人員儲存資料，並確保其高度可用、安全、持久、可調整和重複。</span><span class="sxs-lookup"><span data-stu-id="c9259-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="c9259-118">這表示 Microsoft 會為您處理所有維護和重大問題。</span><span class="sxs-lookup"><span data-stu-id="c9259-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="c9259-119">如需詳細資訊，請造訪 [Azure 儲存體文章](/azure/storage/common/storage-introduction)。</span><span class="sxs-lookup"><span data-stu-id="c9259-119">For more information, visit the [Azure Storage article](/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="c9259-120">完成本課程之後，您將會有一個混合現實的沉浸式耳機應用程式，可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c9259-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="c9259-121">允許使用者在場景周圍看著。</span><span class="sxs-lookup"><span data-stu-id="c9259-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="c9259-122">當使用者 gazes 于3D 「按鈕」時，觸發物件的產生。</span><span class="sxs-lookup"><span data-stu-id="c9259-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="c9259-123">衍生的物件將會由 Azure 函式選擇。</span><span class="sxs-lookup"><span data-stu-id="c9259-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="c9259-124">當產生每個物件時，應用程式會將物件類型儲存在 *Azure* 檔案中，該檔案位於 *Azure 儲存體* 中。</span><span class="sxs-lookup"><span data-stu-id="c9259-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="c9259-125">第二次載入時，將會抓取 *Azure* 檔案資料，並使用該資料從先前的應用程式實例重新執行產生動作。</span><span class="sxs-lookup"><span data-stu-id="c9259-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="c9259-126">在您的應用程式中，您可以自行決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="c9259-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c9259-127">本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="c9259-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="c9259-128">您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9259-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="c9259-129">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c9259-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c9259-130">課程</span><span class="sxs-lookup"><span data-stu-id="c9259-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c9259-131"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c9259-131"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c9259-132"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="c9259-132"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c9259-133">MR 和 Azure 305：功能與儲存空間</span><span class="sxs-lookup"><span data-stu-id="c9259-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="c9259-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c9259-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c9259-135">✔️</span><span class="sxs-lookup"><span data-stu-id="c9259-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c9259-136">雖然本課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機，您也可以將在本課程中學到的內容套用至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c9259-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="c9259-137">當您依照課程的指示進行時，您將會看到有關您可能需要採用以支援 HoloLens 的任何變更的注意事項。</span><span class="sxs-lookup"><span data-stu-id="c9259-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c9259-138">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c9259-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c9259-139">本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="c9259-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c9259-140">另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="c9259-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="c9259-141">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span><span class="sxs-lookup"><span data-stu-id="c9259-141">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="c9259-142">本課程建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="c9259-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c9259-143">開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)</span><span class="sxs-lookup"><span data-stu-id="c9259-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c9259-144">啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="c9259-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c9259-145">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c9259-145">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c9259-146">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="c9259-146">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c9259-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c9259-147">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="c9259-148">[Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="c9259-148">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="c9259-149">用來建立 Azure 資源之 Azure 帳戶的訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="c9259-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="c9259-150">適用于 Azure 設定和資料抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="c9259-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c9259-151">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="c9259-151">Before you start</span></span>

<span data-ttu-id="c9259-152">為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="c9259-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="c9259-153">第1章-Azure 入口網站</span><span class="sxs-lookup"><span data-stu-id="c9259-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="c9259-154">若要使用 **Azure 儲存體服務**，您將需要在 Azure 入口網站中建立及設定 **儲存體帳戶** 。</span><span class="sxs-lookup"><span data-stu-id="c9259-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="c9259-155">登入  [Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="c9259-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c9259-156">如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="c9259-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c9259-157">如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c9259-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c9259-158">登入後，按一下左上角的 [ **新增** ]，並搜尋 [ *儲存體帳戶*]，然後按一下 [ **輸入**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![azure 儲存體搜尋](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="c9259-160">在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。</span><span class="sxs-lookup"><span data-stu-id="c9259-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="c9259-161">新頁面將提供 *Azure 儲存體帳戶* 服務的描述。</span><span class="sxs-lookup"><span data-stu-id="c9259-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="c9259-162">在此提示的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="c9259-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![建立服務](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="c9259-164">當您按一下 [ **建立**] 之後：</span><span class="sxs-lookup"><span data-stu-id="c9259-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="c9259-165">為您的帳戶插入 *名稱* ，請注意，此欄位只接受數位和小寫字母。</span><span class="sxs-lookup"><span data-stu-id="c9259-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="c9259-166">在 [ *部署模型*] 中，選取 [ **資源管理員**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="c9259-167">針對 [ *帳戶類型*]，選取 **[儲存體 (一般用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="c9259-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="c9259-168">如果您要建立新的資源群組) ，請判斷資源群組 (的 *位置* 。</span><span class="sxs-lookup"><span data-stu-id="c9259-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c9259-169">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="c9259-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c9259-170">某些 Azure 資產僅適用于某些區域。</span><span class="sxs-lookup"><span data-stu-id="c9259-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="c9259-171">若 *為複寫* ，請選取 [ **讀取權限-異地-多餘儲存體] (GRS])**。</span><span class="sxs-lookup"><span data-stu-id="c9259-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="c9259-172">針對 [效能]，請選取 [標準]。</span><span class="sxs-lookup"><span data-stu-id="c9259-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="c9259-173">將 [ *需要安全傳輸* ] 保留為 **停用**。</span><span class="sxs-lookup"><span data-stu-id="c9259-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="c9259-174">選取 [訂用帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="c9259-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="c9259-175">選擇資源群組，或建立一個新的 *資源群組* 。</span><span class="sxs-lookup"><span data-stu-id="c9259-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="c9259-176">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="c9259-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c9259-177">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。</span><span class="sxs-lookup"><span data-stu-id="c9259-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="c9259-178">如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="c9259-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="c9259-179">您也必須確認您已瞭解套用到此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="c9259-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="c9259-180">選取 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="c9259-180">Select **Create**.</span></span>

        ![輸入服務資訊](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="c9259-182">當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="c9259-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="c9259-183">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="c9259-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![azure 入口網站中的新通知](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="c9259-185">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="c9259-185">Click on the notifications to explore your new Service instance.</span></span>

    ![移至資源](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="c9259-187">按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。</span><span class="sxs-lookup"><span data-stu-id="c9259-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="c9259-188">您將會進入新的 *儲存體帳戶* 服務實例。</span><span class="sxs-lookup"><span data-stu-id="c9259-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![access keys](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="c9259-190">按一下 [ *存取金鑰*]，以顯示此雲端服務的端點。</span><span class="sxs-lookup"><span data-stu-id="c9259-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="c9259-191">使用「 *記事本* 」或類似的，複製其中一個金鑰以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="c9259-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="c9259-192">此外，請記下 *連接字串* 值，因為它將用於 *AzureServices* 類別，您稍後將會建立此值。</span><span class="sxs-lookup"><span data-stu-id="c9259-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![複製連接字串](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="c9259-194">第2章-設定 Azure 函數</span><span class="sxs-lookup"><span data-stu-id="c9259-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="c9259-195">您現在會在 Azure 服務中撰寫 **azure** **函數** 。</span><span class="sxs-lookup"><span data-stu-id="c9259-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="c9259-196">您可以使用 **Azure** 函式來執行幾乎任何您在程式碼中使用傳統函式時所執行的作業，差別在於具有可存取 Azure 帳戶之認證的任何應用程式都可以存取此函式。</span><span class="sxs-lookup"><span data-stu-id="c9259-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="c9259-197">若要建立 Azure 函數：</span><span class="sxs-lookup"><span data-stu-id="c9259-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="c9259-198">從 *Azure 入口網站* 中，按一下左上角的 [ **新增** ]，並搜尋函式 *應用程式*，然後按一下 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="c9259-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![建立函數應用程式](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="c9259-200">在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。</span><span class="sxs-lookup"><span data-stu-id="c9259-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="c9259-201">新的頁面會提供 *Azure 函數應用程式* 服務的描述。</span><span class="sxs-lookup"><span data-stu-id="c9259-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="c9259-202">在此提示的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="c9259-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![函數應用程式資訊](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="c9259-204">當您按一下 [ **建立**] 之後：</span><span class="sxs-lookup"><span data-stu-id="c9259-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="c9259-205">提供 *應用程式名稱*。</span><span class="sxs-lookup"><span data-stu-id="c9259-205">Provide an *App name*.</span></span> <span data-ttu-id="c9259-206">此處只可使用字母和數位 () 允許大寫或小寫。</span><span class="sxs-lookup"><span data-stu-id="c9259-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="c9259-207">選取您偏好的 *訂* 用帳戶。</span><span class="sxs-lookup"><span data-stu-id="c9259-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="c9259-208">選擇資源群組，或建立一個新的 *資源群組* 。</span><span class="sxs-lookup"><span data-stu-id="c9259-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="c9259-209">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="c9259-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c9259-210">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。</span><span class="sxs-lookup"><span data-stu-id="c9259-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="c9259-211">如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="c9259-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="c9259-212">針對此練習，請選取 [ *Windows* ] 做為選擇的 **作業系統**。</span><span class="sxs-lookup"><span data-stu-id="c9259-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="c9259-213">選取 **主控方案** 的取用 *方案*。</span><span class="sxs-lookup"><span data-stu-id="c9259-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="c9259-214">如果您要建立新的資源群組) ，請判斷資源群組 (的 *位置* 。</span><span class="sxs-lookup"><span data-stu-id="c9259-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c9259-215">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="c9259-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c9259-216">某些 Azure 資產僅適用于某些區域。</span><span class="sxs-lookup"><span data-stu-id="c9259-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="c9259-217">為了達到最佳效能，請選取與儲存體帳戶相同的區域。</span><span class="sxs-lookup"><span data-stu-id="c9259-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="c9259-218">針對 [ *儲存體*]，選取 [ **使用現有** 的]，然後使用下拉式功能表來尋找您先前建立的儲存體。</span><span class="sxs-lookup"><span data-stu-id="c9259-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="c9259-219">請勿在此練習中 *Application Insights* 關閉。</span><span class="sxs-lookup"><span data-stu-id="c9259-219">Leave *Application Insights* off for this exercise.</span></span>

        ![輸入函數應用程式詳細資料](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="c9259-221">按一下 [ **建立** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9259-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="c9259-222">當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="c9259-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="c9259-223">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="c9259-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新的 azure 入口網站通知](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="c9259-225">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="c9259-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![移至資源函式應用程式](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="c9259-227">按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。</span><span class="sxs-lookup"><span data-stu-id="c9259-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="c9259-228">您將會進入新的 *函數應用程式* 服務實例。</span><span class="sxs-lookup"><span data-stu-id="c9259-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="c9259-229">在 [ *函數應用程式* ] 儀表板上，將滑鼠停留在左側面板中的 [函式 *] 上方，* 然後按一下 **+ (加號)** 符號]。</span><span class="sxs-lookup"><span data-stu-id="c9259-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![建立新函數](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="c9259-231">在下一個頁面上，確定已選取 [ **Webhook + API** ]，然後選取 *[* **CSharp**]，因為這會是本教學課程所使用的語言。</span><span class="sxs-lookup"><span data-stu-id="c9259-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="c9259-232">最後，按一下 [ **建立此函數** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9259-232">Lastly, click the **Create this function** button.</span></span>

    ![選取網路攔截 csharp](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="c9259-234">您應該會進入字碼頁 (.csx) ，如果沒有，請在左側面板中的 [函數] 清單中，按一下新建立的函數。</span><span class="sxs-lookup"><span data-stu-id="c9259-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![開啟新函數](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="c9259-236">將下列程式碼複製到您的函式中。</span><span class="sxs-lookup"><span data-stu-id="c9259-236">Copy the following code into your function.</span></span> <span data-ttu-id="c9259-237">呼叫時，此函式只會傳回0和2之間的隨機整數。</span><span class="sxs-lookup"><span data-stu-id="c9259-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="c9259-238">不要擔心現有的程式碼，您可以隨意貼到它的最上方。</span><span class="sxs-lookup"><span data-stu-id="c9259-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="c9259-239">選取 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="c9259-239">Select **Save**.</span></span>

14. <span data-ttu-id="c9259-240">結果看起來應該如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c9259-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="c9259-241">按一下 [ **取得** 函式 URL]，並記下顯示的 *端點* 。</span><span class="sxs-lookup"><span data-stu-id="c9259-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="c9259-242">您必須將它插入您稍後將在本課程中建立的 *AzureServices* 類別。</span><span class="sxs-lookup"><span data-stu-id="c9259-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![取得函式端點](images/AzureLabs-Lab5-16.png)

    ![插入函數端點](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="c9259-245">第3章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="c9259-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="c9259-246">以下是使用 Mixed Reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="c9259-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="c9259-247">設定及測試您的混合現實沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="c9259-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="c9259-248">在此課程中，您將 **不** 需要移動控制器。</span><span class="sxs-lookup"><span data-stu-id="c9259-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="c9259-249">如果您需要設定沉浸式耳機的支援，請 [造訪「混合現實設定」一文](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="c9259-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="c9259-250">開啟 Unity，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-250">Open Unity and click **New**.</span></span>

    ![建立新的 unity 專案](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="c9259-252">您現在將需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="c9259-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="c9259-253">插入 **MR_Azure_Functions**。</span><span class="sxs-lookup"><span data-stu-id="c9259-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="c9259-254">請確定專案類型設定為 **3d**。</span><span class="sxs-lookup"><span data-stu-id="c9259-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="c9259-255">將 *位置* 設定為適合您 (記住，較接近根目錄的) 。</span><span class="sxs-lookup"><span data-stu-id="c9259-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c9259-256">然後，按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-256">Then, click **Create project**.</span></span>

    ![提供新的 unity 專案名稱](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="c9259-258">在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="c9259-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c9259-259">移至 [**編輯**  >  **喜好** 設定]，然後在新視窗中，流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c9259-260">將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="c9259-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c9259-261">關閉 [ **喜好** 設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="c9259-261">Close the **Preferences** window.</span></span>

    ![將 visual studio 設定為腳本編輯器](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="c9259-263">接下來，移 **至 [** 檔案  >  **組建設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至 **通用 Windows 平臺**。</span><span class="sxs-lookup"><span data-stu-id="c9259-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![將平臺切換至 uwp](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="c9259-265">移至 **檔案**  >  **組建設定**，並確定：</span><span class="sxs-lookup"><span data-stu-id="c9259-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="c9259-266">**目標裝置** 設定為 **任何裝置**。</span><span class="sxs-lookup"><span data-stu-id="c9259-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="c9259-267">針對 Microsoft HoloLens，請將 **目標裝置** 設定為 *HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="c9259-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="c9259-268">**組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="c9259-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="c9259-269">**SDK** 已設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="c9259-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="c9259-270">**Visual Studio 版本** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="c9259-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="c9259-271">**組建並執行** 設定為 **本機電腦**</span><span class="sxs-lookup"><span data-stu-id="c9259-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="c9259-272">儲存場景，並將其新增至組建。</span><span class="sxs-lookup"><span data-stu-id="c9259-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="c9259-273">若要這麼做，請選取 [ **新增開啟的場景**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="c9259-274">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c9259-274">A save window will appear.</span></span>

            ![新增開啟的場景](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="c9259-276">為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。</span><span class="sxs-lookup"><span data-stu-id="c9259-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![建立場景資料夾](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="c9259-278">開啟新建立的 **場景** 資料夾，然後在 [ **檔案名：** 文字] 欄位中輸入 **FunctionsScene**，然後按 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![儲存函式場景](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="c9259-280">[ **組建設定**] 中的其餘設定，現在應該保持為預設值。</span><span class="sxs-lookup"><span data-stu-id="c9259-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![保留預設組建設定](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="c9259-282">在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。</span><span class="sxs-lookup"><span data-stu-id="c9259-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![偵測器中的播放機設定](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="c9259-284">在此面板中，需要驗證幾個設定：</span><span class="sxs-lookup"><span data-stu-id="c9259-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="c9259-285">在 [ **其他設定** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="c9259-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="c9259-286">**腳本執行階段版本** 應該是 **實驗** ( .net 4.6 對等) ，這會觸發重新開機編輯器的需求。</span><span class="sxs-lookup"><span data-stu-id="c9259-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="c9259-287">**腳本後端** 應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="c9259-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="c9259-288">**API 相容性層級** 應為 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="c9259-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="c9259-289">在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：</span><span class="sxs-lookup"><span data-stu-id="c9259-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="c9259-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c9259-290">**InternetClient**</span></span>

            ![設定功能](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="c9259-292">在面板的 [ **XR 設定** ] 中，在 [設定] () 的 [ **發佈設定** ] 下方找到 [支援的滴答 **虛擬事實**]，請確定已新增 **Windows Mixed Reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="c9259-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![設定 XR 設定](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="c9259-294">回到 *組建設定*： *Unity c # 專案* 不再呈現灰色;勾選此方塊旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c9259-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![刻度 c # 專案](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="c9259-296">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="c9259-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="c9259-297">儲存場景和專案 (**檔**  >  **儲存場景/** 檔案  >  **儲存專案**) 。</span><span class="sxs-lookup"><span data-stu-id="c9259-297">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="c9259-298">第4章-設定主要攝影機</span><span class="sxs-lookup"><span data-stu-id="c9259-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9259-299">如果您想要略過 *Unity 設定* 此課程的元件，並直接繼續進行程式碼，請隨意 [下載 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)，並將它匯入至您的專案中做為 [自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="c9259-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="c9259-300">這也會包含下一章中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="c9259-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="c9259-301">匯入之後，請繼續進行 [第7章](#chapter-7---create-the-azureservices-class)。</span><span class="sxs-lookup"><span data-stu-id="c9259-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="c9259-302">在 [階層] *面板* 中，您會找到一個稱為「 **主要攝影機**」的物件，此物件代表您在應用程式「內」之後的「頭部」觀點。</span><span class="sxs-lookup"><span data-stu-id="c9259-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="c9259-303">使用 Unity 儀表板，選取 **主要攝影機 GameObject**。</span><span class="sxs-lookup"><span data-stu-id="c9259-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="c9259-304">您將會注意到，在儀錶) 板內 (的 [偵測 *器] 面板* 通常會顯示該 *GameObject* 的各種元件，並在頂端、*相機* 和一些其他元件中顯示 *轉換*。</span><span class="sxs-lookup"><span data-stu-id="c9259-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="c9259-305">您必須重設主要攝影機的轉換，才能正確定位。</span><span class="sxs-lookup"><span data-stu-id="c9259-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="c9259-306">若要這樣做，請選取相機 *轉換* 元件旁邊的 **齒輪** 圖示，然後選取 [**重設**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![重設轉換](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="c9259-308">然後，將 **轉換** 元件更新為如下所示：</span><span class="sxs-lookup"><span data-stu-id="c9259-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="c9259-309">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="c9259-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="c9259-310">**X**</span><span class="sxs-lookup"><span data-stu-id="c9259-310">**X**</span></span>   | <span data-ttu-id="c9259-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="c9259-311">**Y**</span></span>                     | <span data-ttu-id="c9259-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="c9259-312">**Z**</span></span> |
    | <span data-ttu-id="c9259-313">0</span><span class="sxs-lookup"><span data-stu-id="c9259-313">0</span></span>       | <span data-ttu-id="c9259-314">1</span><span class="sxs-lookup"><span data-stu-id="c9259-314">1</span></span>                         | <span data-ttu-id="c9259-315">0</span><span class="sxs-lookup"><span data-stu-id="c9259-315">0</span></span>     |    

    |       | <span data-ttu-id="c9259-316">轉換-旋轉</span><span class="sxs-lookup"><span data-stu-id="c9259-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="c9259-317">**X**</span><span class="sxs-lookup"><span data-stu-id="c9259-317">**X**</span></span> | <span data-ttu-id="c9259-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="c9259-318">**Y**</span></span>                | <span data-ttu-id="c9259-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="c9259-319">**Z**</span></span> |
    | <span data-ttu-id="c9259-320">0</span><span class="sxs-lookup"><span data-stu-id="c9259-320">0</span></span>     | <span data-ttu-id="c9259-321">0</span><span class="sxs-lookup"><span data-stu-id="c9259-321">0</span></span>                    | <span data-ttu-id="c9259-322">0</span><span class="sxs-lookup"><span data-stu-id="c9259-322">0</span></span>     |

    |       | <span data-ttu-id="c9259-323">轉換-調整規模</span><span class="sxs-lookup"><span data-stu-id="c9259-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="c9259-324">**X**</span><span class="sxs-lookup"><span data-stu-id="c9259-324">**X**</span></span> | <span data-ttu-id="c9259-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="c9259-325">**Y**</span></span>             | <span data-ttu-id="c9259-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="c9259-326">**Z**</span></span> |
    | <span data-ttu-id="c9259-327">1</span><span class="sxs-lookup"><span data-stu-id="c9259-327">1</span></span>     | <span data-ttu-id="c9259-328">1</span><span class="sxs-lookup"><span data-stu-id="c9259-328">1</span></span>                 | <span data-ttu-id="c9259-329">1</span><span class="sxs-lookup"><span data-stu-id="c9259-329">1</span></span>     |

    ![設定相機轉換](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="c9259-331">第5章-設定 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="c9259-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="c9259-332">在 [階層] *面板* 的空白區域中，以滑鼠右鍵按一下 [ **3d 物件**] 下的 [加入 **平面**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![建立新的平面](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="c9259-334">選取 **平面** 物件之後，在 [偵測 *器] 面板* 中變更下列參數：</span><span class="sxs-lookup"><span data-stu-id="c9259-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="c9259-335">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="c9259-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="c9259-336">**X**</span><span class="sxs-lookup"><span data-stu-id="c9259-336">**X**</span></span> | <span data-ttu-id="c9259-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="c9259-337">**Y**</span></span>                | <span data-ttu-id="c9259-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="c9259-338">**Z**</span></span> |
    | <span data-ttu-id="c9259-339">0</span><span class="sxs-lookup"><span data-stu-id="c9259-339">0</span></span>     | <span data-ttu-id="c9259-340">0</span><span class="sxs-lookup"><span data-stu-id="c9259-340">0</span></span>                    | <span data-ttu-id="c9259-341">4</span><span class="sxs-lookup"><span data-stu-id="c9259-341">4</span></span>     |

    |       | <span data-ttu-id="c9259-342">轉換-調整規模</span><span class="sxs-lookup"><span data-stu-id="c9259-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="c9259-343">**X**</span><span class="sxs-lookup"><span data-stu-id="c9259-343">**X**</span></span> | <span data-ttu-id="c9259-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="c9259-344">**Y**</span></span>             | <span data-ttu-id="c9259-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="c9259-345">**Z**</span></span> |
    | <span data-ttu-id="c9259-346">10</span><span class="sxs-lookup"><span data-stu-id="c9259-346">10</span></span>    | <span data-ttu-id="c9259-347">1</span><span class="sxs-lookup"><span data-stu-id="c9259-347">1</span></span>                 | <span data-ttu-id="c9259-348">10</span><span class="sxs-lookup"><span data-stu-id="c9259-348">10</span></span>    |

    ![設定平面位置和小數位數](images/AzureLabs-Lab5-32.png)

    ![平面的場景視圖](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="c9259-351">在 [階層] *面板* 的空白區域中，以滑鼠右鍵按一下 [ **3d 物件**] 下的 [加入 **Cube**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="c9259-352">將 Cube 重新命名為 **GazeButton** (已選取 cube，請按 ' F2 ' ) 。</span><span class="sxs-lookup"><span data-stu-id="c9259-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="c9259-353">在 [偵測 *器] 面板* 中變更下列參數：</span><span class="sxs-lookup"><span data-stu-id="c9259-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="c9259-354">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="c9259-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="c9259-355">**X**</span><span class="sxs-lookup"><span data-stu-id="c9259-355">**X**</span></span> | <span data-ttu-id="c9259-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="c9259-356">**Y**</span></span>                | <span data-ttu-id="c9259-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="c9259-357">**Z**</span></span> |
        | <span data-ttu-id="c9259-358">0</span><span class="sxs-lookup"><span data-stu-id="c9259-358">0</span></span>     | <span data-ttu-id="c9259-359">3</span><span class="sxs-lookup"><span data-stu-id="c9259-359">3</span></span>                    | <span data-ttu-id="c9259-360">5</span><span class="sxs-lookup"><span data-stu-id="c9259-360">5</span></span>     |


        ![設定注視按鈕轉換](images/AzureLabs-Lab5-34.png)

        ![注視按鈕場景視圖](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="c9259-363">按一下 [ **標記** ] 下拉式按鈕，然後按一下 [ **新增** 標籤]，即可開啟 [ *標記 & 圖層] 窗格*。</span><span class="sxs-lookup"><span data-stu-id="c9259-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![新增標記](images/AzureLabs-Lab5-36.png)

        ![選取加號](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="c9259-366">選取 **+ (加號)** ] 按鈕，然後在 [ *新* 標籤名稱] 欄位中，輸入 **GazeButton**，然後按 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![命名新標記](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="c9259-368">按一下 [階層]*面板* 中的 [ **GazeButton** ] 物件，然後在 [偵測 *器] 面板* 中，指派新建立的 **GazeButton** 標記。</span><span class="sxs-lookup"><span data-stu-id="c9259-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![將新標籤指派給注視按鈕](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="c9259-370">以滑鼠右鍵按一下 [階層]*面板* 中的 [ **GazeButton** ] 物件，然後新增 **空白的 GameObject** (將會新增為 *子* 物件) 。</span><span class="sxs-lookup"><span data-stu-id="c9259-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="c9259-371">選取新的物件，並將它重新命名為 **ShapeSpawnPoint**。</span><span class="sxs-lookup"><span data-stu-id="c9259-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="c9259-372">在 [偵測 *器] 面板* 中變更下列參數：</span><span class="sxs-lookup"><span data-stu-id="c9259-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="c9259-373">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="c9259-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="c9259-374">**X**</span><span class="sxs-lookup"><span data-stu-id="c9259-374">**X**</span></span> |<span data-ttu-id="c9259-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="c9259-375">**Y**</span></span>                 | <span data-ttu-id="c9259-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="c9259-376">**Z**</span></span> |
        | <span data-ttu-id="c9259-377">0</span><span class="sxs-lookup"><span data-stu-id="c9259-377">0</span></span>     | <span data-ttu-id="c9259-378">-1</span><span class="sxs-lookup"><span data-stu-id="c9259-378">-1</span></span>                   | <span data-ttu-id="c9259-379">0</span><span class="sxs-lookup"><span data-stu-id="c9259-379">0</span></span>     |

        ![更新圖形產生點轉換](images/AzureLabs-Lab5-40.png)

        ![圖形產生點場景視圖](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="c9259-382">接下來，您將建立 **3D 文字** 物件，以提供 Azure 服務狀態的相關意見反應。</span><span class="sxs-lookup"><span data-stu-id="c9259-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="c9259-383">再以滑鼠右鍵按一下 [階層] 面板中的 [ **GazeButton** ]，並新增 **3d 物件**  >  **3d 文字** 物件做為 *子* 系。</span><span class="sxs-lookup"><span data-stu-id="c9259-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child*.</span></span>

    ![建立新的3D 文字物件](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="c9259-385">將 **3D 文字** 物件重新命名為 **AzureStatusText**。</span><span class="sxs-lookup"><span data-stu-id="c9259-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="c9259-386">變更 **AzureStatusText** 物件轉換，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c9259-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="c9259-387">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="c9259-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="c9259-388">**X**</span><span class="sxs-lookup"><span data-stu-id="c9259-388">**X**</span></span> | <span data-ttu-id="c9259-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="c9259-389">**Y**</span></span>                | <span data-ttu-id="c9259-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="c9259-390">**Z**</span></span> |
    | <span data-ttu-id="c9259-391">0</span><span class="sxs-lookup"><span data-stu-id="c9259-391">0</span></span>     | <span data-ttu-id="c9259-392">0</span><span class="sxs-lookup"><span data-stu-id="c9259-392">0</span></span>                    | <span data-ttu-id="c9259-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="c9259-393">-0.6</span></span>  |

    |       | <span data-ttu-id="c9259-394">轉換-調整規模</span><span class="sxs-lookup"><span data-stu-id="c9259-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="c9259-395">**X**</span><span class="sxs-lookup"><span data-stu-id="c9259-395">**X**</span></span> | <span data-ttu-id="c9259-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="c9259-396">**Y**</span></span>             | <span data-ttu-id="c9259-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="c9259-397">**Z**</span></span> |
    | <span data-ttu-id="c9259-398">0.1</span><span class="sxs-lookup"><span data-stu-id="c9259-398">0.1</span></span>   | <span data-ttu-id="c9259-399">0.1</span><span class="sxs-lookup"><span data-stu-id="c9259-399">0.1</span></span>               | <span data-ttu-id="c9259-400">0.1</span><span class="sxs-lookup"><span data-stu-id="c9259-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="c9259-401">如果看起來像是下層，請不要擔心，因為在更新下列文字網格元件時，將會修正此問題。</span><span class="sxs-lookup"><span data-stu-id="c9259-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="c9259-402">變更 **文字網格** 元件以符合下列各項：</span><span class="sxs-lookup"><span data-stu-id="c9259-402">Change the **Text Mesh** component to match the below:</span></span>

    ![設定文字網格元件](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="c9259-404">在這裡選取的色彩是十六進位色彩： **000000FF**，不過您可以自行選擇，只需確保它可供閱讀。</span><span class="sxs-lookup"><span data-stu-id="c9259-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="c9259-405">階層面板結構現在看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="c9259-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![階層中的文字網格](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="c9259-407">您的場景現在看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="c9259-407">Your scene should now look like this:</span></span>

    ![場景視圖中的文字網格](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="c9259-409">第6章-匯入 Unity 的 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="c9259-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="c9259-410">您將使用適用于 Unity (的 Azure 儲存體，其本身會利用 .Net SDK for Azure) 。</span><span class="sxs-lookup"><span data-stu-id="c9259-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="c9259-411">您可以在 [Unity 文章的 Azure 儲存體](/sandbox/gamedev/unity/azure-storage-unity)閱讀詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c9259-411">You can read more about this at the [Azure Storage for Unity article](/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="c9259-412">Unity 中目前有已知的問題，需要在匯入之後重新設定外掛程式。</span><span class="sxs-lookup"><span data-stu-id="c9259-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="c9259-413">在解決 bug 之後，將不再需要這一節中的這些步驟 (4-7) 。</span><span class="sxs-lookup"><span data-stu-id="c9259-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="c9259-414">若要將 SDK 匯入您自己的專案中，請確定您已從 GitHub 下載最新的 ['. unitypackage '](https://aka.ms/azstorage-unitysdk)。</span><span class="sxs-lookup"><span data-stu-id="c9259-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="c9259-415">然後執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c9259-415">Then, do the following:</span></span>

1.  <span data-ttu-id="c9259-416">使用 [  **資產** 匯  >  **入封裝**  >  **自訂套件**] 功能表選項，將 unitypackage 檔案新增至 Unity。</span><span class="sxs-lookup"><span data-stu-id="c9259-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="c9259-417">在快顯的 [匯 **入 Unity 套件**] 方塊中，您可以選取 **外掛程式**  >  **儲存體** 下的所有專案。</span><span class="sxs-lookup"><span data-stu-id="c9259-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span> <span data-ttu-id="c9259-418">取消核取其他所有專案，因為此課程不需要。</span><span class="sxs-lookup"><span data-stu-id="c9259-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![匯入至封裝](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="c9259-420">按一下 [匯 **入** ] 按鈕，將專案新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="c9259-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="c9259-421">移至 [*外掛程式*] 下的 [*儲存體*] 資料夾，在 [專案] 視圖中，*只* 選取下列外掛程式：</span><span class="sxs-lookup"><span data-stu-id="c9259-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="c9259-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="c9259-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="c9259-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="c9259-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="c9259-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="c9259-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="c9259-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="c9259-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="c9259-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="c9259-426">System.Spatial</span></span>

        ![取消核取任何平臺](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="c9259-428">選取 *這些特定的外掛程式* 之後， **取消** 核取 *任何平臺* ，然後 **取消** 核取 *WSAPlayer* ， **然後按一下 [** 套用]。</span><span class="sxs-lookup"><span data-stu-id="c9259-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![套用平臺 dll](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="c9259-430">我們會將這些特定外掛程式標示為僅用於 Unity 編輯器。</span><span class="sxs-lookup"><span data-stu-id="c9259-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="c9259-431">這是因為在 [WSA] 資料夾中有不同版本的相同外掛程式，在從 Unity 匯出專案之後，將會使用這些相同的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="c9259-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="c9259-432">在 [ *儲存體* 外掛程式] 資料夾中，只選取：</span><span class="sxs-lookup"><span data-stu-id="c9259-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="c9259-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="c9259-433">Microsoft.Data.Services.Client</span></span>

        ![set 不要處理 dll](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="c9259-435">勾選 [*平臺設定*] 下的 [**不處理**] 方塊，**然後按一下 [** 套用]。</span><span class="sxs-lookup"><span data-stu-id="c9259-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![套用無處理](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="c9259-437">因為 Unity 元件 patcher 在處理此外掛程式時遇到困難，所以我們將此外掛程式標示為「不要處理」。</span><span class="sxs-lookup"><span data-stu-id="c9259-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="c9259-438">雖然外掛程式不會進行處理，但仍可運作。</span><span class="sxs-lookup"><span data-stu-id="c9259-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="c9259-439">第7章-建立 AzureServices 類別</span><span class="sxs-lookup"><span data-stu-id="c9259-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="c9259-440">您即將建立的第一個類別是 *AzureServices* 類別。</span><span class="sxs-lookup"><span data-stu-id="c9259-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="c9259-441">*AzureServices* 類別將負責：</span><span class="sxs-lookup"><span data-stu-id="c9259-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="c9259-442">儲存 Azure 帳號憑證。</span><span class="sxs-lookup"><span data-stu-id="c9259-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="c9259-443">呼叫您的 Azure App 函數。</span><span class="sxs-lookup"><span data-stu-id="c9259-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="c9259-444">上傳和下載 Azure 雲端儲存體中的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="c9259-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="c9259-445">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="c9259-445">To create this Class:</span></span>

1.  <span data-ttu-id="c9259-446">以滑鼠右鍵按一下 [專案] 面板中的 [*資產*] 資料夾，然後 **建立**  >  **資料夾**。</span><span class="sxs-lookup"><span data-stu-id="c9259-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="c9259-447">將資料夾命名為 **腳本**。</span><span class="sxs-lookup"><span data-stu-id="c9259-447">Name the folder **Scripts**.</span></span>

    ![建立新資料夾](images/AzureLabs-Lab5-50.png)

    ![呼叫資料夾-腳本](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="c9259-450">按兩下剛才建立的資料夾，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="c9259-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="c9259-451">以滑鼠右鍵按一下資料夾內的 [**建立**  >  **c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-451">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="c9259-452">呼叫腳本 *AzureServices*。</span><span class="sxs-lookup"><span data-stu-id="c9259-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="c9259-453">按兩下新的 *AzureServices* 類別，以 *Visual Studio* 開啟。</span><span class="sxs-lookup"><span data-stu-id="c9259-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="c9259-454">將下列命名空間新增至 *AzureServices* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="c9259-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="c9259-455">在 *AzureServices* 類別內新增下列偵測器欄位：</span><span class="sxs-lookup"><span data-stu-id="c9259-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="c9259-456">然後，在 *AzureServices* 類別內新增下列成員變數：</span><span class="sxs-lookup"><span data-stu-id="c9259-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="c9259-457">請務必使用 azure 入口網站中的 Azure 儲存體值來取代 *端點* 和 *連接字串* 值</span><span class="sxs-lookup"><span data-stu-id="c9259-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="c9259-458">現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c9259-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="c9259-459">當類別初始化時，會呼叫這些方法：</span><span class="sxs-lookup"><span data-stu-id="c9259-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="c9259-460">我們將在 [未來的章節](#chapter-10---completing-the-azureservices-class)中，填入 *CallAzureFunctionForNextShape ()* 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c9259-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="c9259-461">刪除 *更新 ()* 方法，因為此類別不會使用它。</span><span class="sxs-lookup"><span data-stu-id="c9259-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="c9259-462">將您的變更儲存在 Visual Studio 中，然後回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="c9259-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="c9259-463">按一下 [腳本] 資料夾中的 [ *AzureServices* ] 類別，並將其拖曳至 [階層] *面板* 中的 [主要攝影機] 物件。</span><span class="sxs-lookup"><span data-stu-id="c9259-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="c9259-464">選取主要攝影機，然後從 **GazeButton** 物件底下抓取 **AzureStatusText** 子物件，並將它放在偵測 *器* 的 [ **AzureStatusText** 參考目標] 欄位中，以提供 *AzureServices* 腳本的參考。</span><span class="sxs-lookup"><span data-stu-id="c9259-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![指派 azure 狀態文字參考目標](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="c9259-466">第8章-建立 ShapeFactory 類別</span><span class="sxs-lookup"><span data-stu-id="c9259-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="c9259-467">下一個要建立的腳本是 *ShapeFactory* 類別。</span><span class="sxs-lookup"><span data-stu-id="c9259-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="c9259-468">此類別的角色是在要求時建立新的圖形，並保留在 *圖形歷程記錄清單* 中建立之圖形的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="c9259-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="c9259-469">每次建立圖形時，圖形歷程 *記錄清單* 都會在 *AzureService* 類別中更新，然後儲存在 *Azure 儲存體* 中。</span><span class="sxs-lookup"><span data-stu-id="c9259-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="c9259-470">當應用程式啟動時，如果在 *Azure 儲存體* 中找到儲存的檔案，則會取出並重新執行 *圖形歷程記錄清單* ，其中包含提供產生的圖形是從儲存體或新的 **3d 文字** 物件。</span><span class="sxs-lookup"><span data-stu-id="c9259-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="c9259-471">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="c9259-471">To create this class:</span></span>

1.  <span data-ttu-id="c9259-472">移至您先前建立的 **腳本** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9259-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="c9259-473">以滑鼠右鍵按一下資料夾內的 [**建立**  >  **c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-473">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="c9259-474">呼叫腳本 *ShapeFactory*。</span><span class="sxs-lookup"><span data-stu-id="c9259-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="c9259-475">按兩下新的 *ShapeFactory* 腳本，以 *Visual Studio* 開啟。</span><span class="sxs-lookup"><span data-stu-id="c9259-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="c9259-476">確定 *ShapeFactory* 類別包含下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="c9259-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="c9259-477">將如下所示的變數新增至 *ShapeFactory* 類別，並將 *Start ()* 和 *喚醒的 ()* 函式取代如下：</span><span class="sxs-lookup"><span data-stu-id="c9259-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="c9259-478">*CreateShape ()* 方法會根據提供的 *整數* 參數產生基本圖案。</span><span class="sxs-lookup"><span data-stu-id="c9259-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="c9259-479">布林值參數是用來指定目前建立的圖形是從儲存體或新的。</span><span class="sxs-lookup"><span data-stu-id="c9259-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="c9259-480">在您的 *ShapeFactory* 類別中，將下列程式碼放在先前的方法底下：</span><span class="sxs-lookup"><span data-stu-id="c9259-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="c9259-481">返回 Unity 之前，請務必將您的變更儲存在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="c9259-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="c9259-482">返回 Unity 編輯器中，按一下 [**腳本**] 資料夾中的 [ *ShapeFactory* ] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。</span><span class="sxs-lookup"><span data-stu-id="c9259-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="c9259-483">選取主要攝影機之後，您會注意到 *ShapeFactory* 腳本元件缺少產生 *點* 參考。</span><span class="sxs-lookup"><span data-stu-id="c9259-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="c9259-484">若要修正此問題，請將 [ **ShapeSpawnPoint** ] 物件從 [階層] *面板* 拖曳至 [產生 **點** 參考] 目標。</span><span class="sxs-lookup"><span data-stu-id="c9259-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![設定圖形 factory 參考目標](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="c9259-486">第9章-建立注視類別</span><span class="sxs-lookup"><span data-stu-id="c9259-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="c9259-487">您需要建立的最後一個腳本是 *注視* 類別。</span><span class="sxs-lookup"><span data-stu-id="c9259-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="c9259-488">此類別負責建立將從主要相機向前投影的 **Raycast** ，以偵測使用者所查看的物件。</span><span class="sxs-lookup"><span data-stu-id="c9259-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="c9259-489">在此情況下，Raycast 將需要識別使用者是否正在查看場景中的 **GazeButton** 物件，並觸發行為。</span><span class="sxs-lookup"><span data-stu-id="c9259-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="c9259-490">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="c9259-490">To create this Class:</span></span>

1.  <span data-ttu-id="c9259-491">移至您先前建立的 **腳本** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9259-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="c9259-492">以滑鼠右鍵按一下 [專案] 面板中的 [**建立**  >  **c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-492">Right-click in the Project Panel, **Create** > **C# Script**.</span></span> <span data-ttu-id="c9259-493">呼叫腳本 *注視*。</span><span class="sxs-lookup"><span data-stu-id="c9259-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="c9259-494">按兩下新的 *注視* 腳本，使用 *Visual Studio 開啟。*</span><span class="sxs-lookup"><span data-stu-id="c9259-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="c9259-495">確定腳本的頂端包含下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="c9259-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="c9259-496">然後，在 *注視* 類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="c9259-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="c9259-497">這些變數中有一些可以在 *編輯器* 中編輯。</span><span class="sxs-lookup"><span data-stu-id="c9259-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="c9259-498">現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c9259-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="c9259-499">新增下列程式碼，此程式碼會在開始時建立資料指標物件，以及 *更新 ()* 方法，這會執行 Raycast 方法，以及 GazeEnabled 布林值的切換位置：</span><span class="sxs-lookup"><span data-stu-id="c9259-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="c9259-500">接著，新增 *UpdateRaycast ()* 方法，它會投影 Raycast 並偵測點擊目標。</span><span class="sxs-lookup"><span data-stu-id="c9259-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="c9259-501">最後，加入 *ResetFocusedObject ()* 方法，這會切換 GazeButton 物件目前的色彩，指出是否正在建立新的圖形。</span><span class="sxs-lookup"><span data-stu-id="c9259-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="c9259-502">在回到 Unity 之前，請先將您的變更儲存在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="c9259-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="c9259-503">按一下 [腳本] 資料夾中的 [*注視*] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。</span><span class="sxs-lookup"><span data-stu-id="c9259-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="c9259-504">第10章-完成 AzureServices 類別</span><span class="sxs-lookup"><span data-stu-id="c9259-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="c9259-505">有了其他腳本之後，現在就可以 *完成* *AzureServices* 類別。</span><span class="sxs-lookup"><span data-stu-id="c9259-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="c9259-506">這可透過下列途徑達成：</span><span class="sxs-lookup"><span data-stu-id="c9259-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="c9259-507">新增名為 *CreateCloudIdentityAsync ()* 的新方法，以設定與 Azure 進行通訊所需的驗證變數。</span><span class="sxs-lookup"><span data-stu-id="c9259-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="c9259-508">這個方法也會檢查先前儲存的檔案是否包含圖形清單。</span><span class="sxs-lookup"><span data-stu-id="c9259-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="c9259-509">**如果找到該** 檔案，則會根據圖形模式（儲存在 **Azure 儲存體** 檔案中），停用使用者的 *注視* 和觸發圖形建立。</span><span class="sxs-lookup"><span data-stu-id="c9259-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="c9259-510">使用者可以看到這種情況，因為 **文字網格** 會提供顯示 [儲存] 或 [新增]，視圖形的來源而定。</span><span class="sxs-lookup"><span data-stu-id="c9259-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="c9259-511">**如果找不到任何** 檔案，則會啟用 *注視*，讓使用者在查看場景中的 **GazeButton** 物件時建立圖形。</span><span class="sxs-lookup"><span data-stu-id="c9259-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="c9259-512">下一個程式碼片段是來自 *Start ()* 方法內;其中會對 *CreateCloudIdentityAsync ()* 方法進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="c9259-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="c9259-513">您可以透過下列方式，隨意複製您目前的 *Start ()* 方法：</span><span class="sxs-lookup"><span data-stu-id="c9259-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="c9259-514">填入 *CallAzureFunctionForNextShape ()* 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c9259-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="c9259-515">您將使用先前建立的 *Azure 函數應用程式* 來要求圖形索引。</span><span class="sxs-lookup"><span data-stu-id="c9259-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="c9259-516">一旦收到新的圖形之後，這個方法會將圖形傳送至 *ShapeFactory* 類別，以便在場景中建立新的圖形。</span><span class="sxs-lookup"><span data-stu-id="c9259-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="c9259-517">使用下列程式碼來完成 *CallAzureFunctionForNextShape ()* 的主體。</span><span class="sxs-lookup"><span data-stu-id="c9259-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="c9259-518">藉由串連儲存在圖形歷程記錄清單中的整數，並將其儲存在 *Azure 儲存體* 檔案中，來新增方法來建立字串。</span><span class="sxs-lookup"><span data-stu-id="c9259-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="c9259-519">新增方法，以抓取 *Azure 儲存體* 檔案中儲存的檔案中所儲存的 *文字，並* 將其還原序列化為清單。</span><span class="sxs-lookup"><span data-stu-id="c9259-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="c9259-520">完成此程式之後，方法會重新啟用注視，讓使用者可以在場景中新增更多圖形。</span><span class="sxs-lookup"><span data-stu-id="c9259-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="c9259-521">在回到 Unity 之前，請先將您的變更儲存在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="c9259-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="c9259-522">第11章-打造 UWP 解決方案</span><span class="sxs-lookup"><span data-stu-id="c9259-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="c9259-523">若要開始建立程式：</span><span class="sxs-lookup"><span data-stu-id="c9259-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="c9259-524">移至 **[** 檔案  >  **組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-524">Go to **File** > **Build Settings**.</span></span>

    ![建立應用程式](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="c9259-526">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="c9259-526">Click **Build**.</span></span> <span data-ttu-id="c9259-527">Unity 將會啟動一個 *檔案總管* 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9259-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="c9259-528">立即建立該資料夾，並命名為 *應用程式*。</span><span class="sxs-lookup"><span data-stu-id="c9259-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="c9259-529">然後選取 [ *應用程式* ] 資料夾，然後按 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="c9259-530">Unity 將開始將您的專案建立到 *應用程式* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9259-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="c9259-531">Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 *檔案總管* 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。</span><span class="sxs-lookup"><span data-stu-id="c9259-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="c9259-532">第12章-部署應用程式</span><span class="sxs-lookup"><span data-stu-id="c9259-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="c9259-533">若要部署您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="c9259-533">To deploy your application:</span></span>

1.  <span data-ttu-id="c9259-534">流覽至 [上一章](#chapter-11---build-the-uwp-solution)所建立的 *應用程式* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9259-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="c9259-535">您會看到含有您應用程式名稱的檔案，其中包含 ' .sln ' 副檔名，您應按兩下該檔案，以便在 *Visual Studio* 中開啟。</span><span class="sxs-lookup"><span data-stu-id="c9259-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="c9259-536">在 [ **方案平臺**] 中，選取 [ **x86]、[本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="c9259-537">在 [ **方案** 設定] 中選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="c9259-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="c9259-538">在 Microsoft HoloLens 中，您可能會發現將此設定為 *遠端電腦* 較容易，因此不會行動網卡到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="c9259-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="c9259-539">不過，您也必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c9259-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="c9259-540">知道您 HoloLens 的 **IP 位址**，您可以在 **設定**  >  **網路 & 網際網路**  >  **wi-fi**  >  **Advanced Options** 中找到此位址; IPv4 是您應該使用的位址。</span><span class="sxs-lookup"><span data-stu-id="c9259-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options**; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="c9259-541">確定已 **開啟\*\*\*\*開發人員模式**;在「**設定** 更新」中找到  >    >  **開發人員的**& 安全性。</span><span class="sxs-lookup"><span data-stu-id="c9259-541">Ensure **Developer Mode** is **On**; found in **Settings** > **Update & Security** > **For developers**.</span></span>

    ![部署解決方案](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="c9259-543">移至 [ **組建** ] 功能表，然後按一下 [ **部署方案** ]，將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="c9259-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="c9259-544">您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好進行啟動及測試！</span><span class="sxs-lookup"><span data-stu-id="c9259-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="c9259-545">您完成的 Azure Functions 和儲存應用程式</span><span class="sxs-lookup"><span data-stu-id="c9259-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="c9259-546">恭喜您，您建立了一個同時運用 Azure Functions 和 Azure 儲存體服務的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9259-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="c9259-547">您的應用程式將能夠在儲存的資料上繪製，並根據該資料來提供動作。</span><span class="sxs-lookup"><span data-stu-id="c9259-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![最終產品-結束](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c9259-549">額外練習</span><span class="sxs-lookup"><span data-stu-id="c9259-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c9259-550">練習1</span><span class="sxs-lookup"><span data-stu-id="c9259-550">Exercise 1</span></span>

<span data-ttu-id="c9259-551">建立第二個產生點，並記錄建立物件的產生點。</span><span class="sxs-lookup"><span data-stu-id="c9259-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="c9259-552">當您載入資料檔案時，請重新執行從原本建立的位置產生的圖形。</span><span class="sxs-lookup"><span data-stu-id="c9259-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c9259-553">練習2</span><span class="sxs-lookup"><span data-stu-id="c9259-553">Exercise 2</span></span>

<span data-ttu-id="c9259-554">建立重新開機應用程式的方法，而不需要每次重新開啟應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9259-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="c9259-555">**載入場景** 是不錯的起點。</span><span class="sxs-lookup"><span data-stu-id="c9259-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="c9259-556">這麼做之後，請建立一個方法來清除 *Azure 儲存體* 中的已儲存清單，讓您可以輕鬆地從應用程式重設。</span><span class="sxs-lookup"><span data-stu-id="c9259-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span>