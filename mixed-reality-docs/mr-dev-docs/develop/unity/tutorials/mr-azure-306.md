---
title: HoloLens (第1代) 和 Azure 306-串流影片
description: 完成本課程，以瞭解如何在混合現實應用程式內執行 Azure 媒體服務。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合的現實，學術，unity，教學課程，api，媒體服務，串流影片，360，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: c6afedfd2dae9da3bcd6b044381a6dc20604ded8
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730565"
---
# <a name="hololens-1st-gen-and-azure-306-streaming-video"></a><span data-ttu-id="14d9b-104">HoloLens (第1代) 和 Azure 306：串流影片</span><span class="sxs-lookup"><span data-stu-id="14d9b-104">HoloLens (1st gen) and Azure 306: Streaming video</span></span>

<br>

>[!NOTE]
><span data-ttu-id="14d9b-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="14d9b-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="14d9b-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="14d9b-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="14d9b-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="14d9b-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="14d9b-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="14d9b-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="14d9b-109">未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="14d9b-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="14d9b-110">當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。</span><span class="sxs-lookup"><span data-stu-id="14d9b-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

<span data-ttu-id="14d9b-111">![最終產品-開始 ](images/AzureLabs-Lab6-00.png)
 ![ 最終產品-開始](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="14d9b-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="14d9b-112">在此課程中，您將瞭解如何將您的 Azure 媒體服務連線到 Windows Mixed Reality 的 VR 體驗，以允許在沉浸式耳機上播放串流360度的影片。</span><span class="sxs-lookup"><span data-stu-id="14d9b-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="14d9b-113">**Azure 媒體服務** 是一組服務，可為您提供廣播品質的影片串流服務，以觸及現今最受歡迎的行動裝置上的更大觀眾。</span><span class="sxs-lookup"><span data-stu-id="14d9b-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="14d9b-114">如需詳細資訊，請造訪 [Azure 媒體服務頁面](https://azure.microsoft.com/services/media-services)。</span><span class="sxs-lookup"><span data-stu-id="14d9b-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="14d9b-115">完成本課程之後，您將會有一個混合現實的沉浸式耳機應用程式，它將能夠執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="14d9b-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="14d9b-116">透過 **Azure 媒體服務**，從 **Azure 儲存體** 取出360度的影片。</span><span class="sxs-lookup"><span data-stu-id="14d9b-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="14d9b-117">顯示 Unity 場景內的已抓取360度影片。</span><span class="sxs-lookup"><span data-stu-id="14d9b-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="14d9b-118">使用兩個不同的影片在兩個場景之間流覽。</span><span class="sxs-lookup"><span data-stu-id="14d9b-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="14d9b-119">在您的應用程式中，您可以自行決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="14d9b-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="14d9b-120">本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="14d9b-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="14d9b-121">您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="14d9b-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="14d9b-122">裝置支援</span><span class="sxs-lookup"><span data-stu-id="14d9b-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="14d9b-123">課程</span><span class="sxs-lookup"><span data-stu-id="14d9b-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="14d9b-124"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="14d9b-124"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="14d9b-125"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="14d9b-125"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="14d9b-126">MR 和 Azure 306：串流視訊</span><span class="sxs-lookup"><span data-stu-id="14d9b-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="14d9b-127">✔️</span><span class="sxs-lookup"><span data-stu-id="14d9b-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="14d9b-128">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="14d9b-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="14d9b-129">本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="14d9b-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="14d9b-130">另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="14d9b-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="14d9b-131">您可以隨意使用最新的軟體（如 [ 安裝工具文章](../../install-the-tools.md)中所列），但不應假設此課程中的資訊會完全符合您在較新軟體中找到的資訊，而不是以下所列的資訊。</span><span class="sxs-lookup"><span data-stu-id="14d9b-131">You are free to use the latest software, as listed within the [install the tools article](../../install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="14d9b-132">本課程建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="14d9b-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="14d9b-133">開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)</span><span class="sxs-lookup"><span data-stu-id="14d9b-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="14d9b-134">啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="14d9b-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="14d9b-135">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="14d9b-135">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="14d9b-136">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="14d9b-136">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="14d9b-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="14d9b-137">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="14d9b-138">[Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="14d9b-138">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="14d9b-139">適用于 Azure 設定和資料抓取的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="14d9b-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="14d9b-140">2 360 度影片採用的格式為， (您可以 [在此下載頁面](https://www.mettle.com/360vr-master-series-free-360-downloads-page) 找到一些免權利的影片) </span><span class="sxs-lookup"><span data-stu-id="14d9b-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="14d9b-141">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="14d9b-141">Before you start</span></span>

1.  <span data-ttu-id="14d9b-142">為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="14d9b-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="14d9b-143">設定及測試您的混合現實沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="14d9b-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="14d9b-144">在此課程中，您將 **不** 需要移動控制器。</span><span class="sxs-lookup"><span data-stu-id="14d9b-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="14d9b-145">如果您需要設定沉浸式耳機的支援，請按一下 [如何設定 Windows Mixed Reality 的連結](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="14d9b-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="14d9b-146">第1章-Azure 入口網站：建立 Azure 儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="14d9b-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="14d9b-147">若要使用 **Azure 儲存體服務**，您將需要在 Azure 入口網站中建立及設定 **儲存體帳戶** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="14d9b-148">登入 [Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="14d9b-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="14d9b-149">如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="14d9b-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="14d9b-150">如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="14d9b-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="14d9b-151">登入後，按一下左側功能表中的 [ **儲存體帳戶** ]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="14d9b-153">在 [ **儲存體帳戶** ] 索引標籤上，按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="14d9b-155">在 [ **建立儲存體帳戶** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="14d9b-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="14d9b-156">為您的帳戶插入 **名稱** ，請注意，此欄位只接受數位和小寫字母。</span><span class="sxs-lookup"><span data-stu-id="14d9b-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="14d9b-157">在 [ **部署模型] 中，** 選取 [ **資源管理員**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="14d9b-158">針對 [ **帳戶類型**]，選取 **[儲存體 (一般用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="14d9b-159">針對 [ **效能**]，請選取 [ \**標準 *]。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="14d9b-160">針對 **複寫** ，請選取 **本機-多餘的儲存體 (LRS)**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="14d9b-161">將 [ **需要安全傳輸** ] 保留為 **停用**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="14d9b-162">選取 [訂用帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="14d9b-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="14d9b-163">選擇資源群組，或建立一個新的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="14d9b-164">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="14d9b-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="14d9b-165">如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="14d9b-166">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="14d9b-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="14d9b-167">某些 Azure 資產僅適用于某些區域。</span><span class="sxs-lookup"><span data-stu-id="14d9b-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="14d9b-168">您必須確認您已瞭解套用到此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="14d9b-170">當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="14d9b-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="14d9b-171">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="14d9b-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="14d9b-173">此時您不需要遵循資源，只要移至下一章即可。</span><span class="sxs-lookup"><span data-stu-id="14d9b-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="14d9b-174">第2章-Azure 入口網站：建立媒體服務</span><span class="sxs-lookup"><span data-stu-id="14d9b-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="14d9b-175">若要使用 Azure 媒體服務，您必須將服務的實例設定為可供您的應用程式使用 (其中帳戶持有者必須是系統管理員) 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="14d9b-176">在 Azure 入口網站中，按一下左上角的 [ **建立資源** ]，並搜尋 **媒體服務，** 然後按 **enter**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="14d9b-177">您目前想要的資源有粉紅色圖示;按一下此，以顯示新的頁面。</span><span class="sxs-lookup"><span data-stu-id="14d9b-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="14d9b-179">新頁面將提供 **媒體服務** 的描述。</span><span class="sxs-lookup"><span data-stu-id="14d9b-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="14d9b-180">在此提示的左下方，按一下 [ **建立** ] 按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="14d9b-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="14d9b-182">當您按一下 [ **建立** 面板] 之後，就會出現您需要提供有關新媒體服務的一些詳細資料的位置：</span><span class="sxs-lookup"><span data-stu-id="14d9b-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="14d9b-183">為此服務實例插入您想要的 **帳戶名稱** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="14d9b-184">選取 [訂用帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="14d9b-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="14d9b-185">選擇資源群組，或建立一個新的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="14d9b-186">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="14d9b-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="14d9b-187">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="14d9b-188">如果您想要深入瞭解 Azure 資源群組，請遵循此 [連結，以瞭解如何管理 Azure 資源群組](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="14d9b-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="14d9b-189">如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="14d9b-190">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="14d9b-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="14d9b-191">某些 Azure 資產僅適用于某些區域。</span><span class="sxs-lookup"><span data-stu-id="14d9b-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="14d9b-192">在 [ **儲存體帳戶** ] 區段中，按一下 [ **請選取 ...** ] 區段，然後按一下您在上一章建立的 **儲存體帳戶** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="14d9b-193">您也必須確認您已瞭解套用到此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="14d9b-194">按一下頁面底部的 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="14d9b-194">Click **Create**.</span></span>

        ![Azure 入口網站](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="14d9b-196">當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="14d9b-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="14d9b-197">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="14d9b-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="14d9b-199">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="14d9b-199">Click on the notification to explore your new Service instance.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="14d9b-201">按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。</span><span class="sxs-lookup"><span data-stu-id="14d9b-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="14d9b-202">在 [新的媒體服務] 頁面中，按一下左側面板中的 [ **資產** ] 連結，這是大約的一半。</span><span class="sxs-lookup"><span data-stu-id="14d9b-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="14d9b-203">在下一個頁面的頁面左上角，按一下 [ **上傳**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="14d9b-205">按一下 **資料夾** 圖示以流覽您的檔案，然後選取您想要串流的第一部360影片。</span><span class="sxs-lookup"><span data-stu-id="14d9b-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="14d9b-206">您可以遵循此 [連結下載影片範例](https://vimeo.com/214401712)。</span><span class="sxs-lookup"><span data-stu-id="14d9b-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="14d9b-208">長檔名可能會造成編碼器的問題：為了確保影片沒有問題，請考慮縮短影片檔案名的長度。</span><span class="sxs-lookup"><span data-stu-id="14d9b-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="14d9b-209">當影片完成上傳時，進度列就會變成綠色。</span><span class="sxs-lookup"><span data-stu-id="14d9b-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="14d9b-211">按一下上方的文字 (**yourservicename-資產** ]) 返回 [ **資產** ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="14d9b-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="14d9b-212">您將會注意到您的影片已成功上傳。</span><span class="sxs-lookup"><span data-stu-id="14d9b-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="14d9b-213">按一下它。</span><span class="sxs-lookup"><span data-stu-id="14d9b-213">Click on it.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="14d9b-215">您要重新導向的頁面會顯示有關您影片的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="14d9b-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="14d9b-216">若要能夠使用您的影片，您必須按一下頁面左上角的 [ **編碼** ] 按鈕進行編碼。</span><span class="sxs-lookup"><span data-stu-id="14d9b-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="14d9b-218">新的面板會顯示在右側，您可以在其中設定檔案的編碼選項。</span><span class="sxs-lookup"><span data-stu-id="14d9b-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="14d9b-219">設定下列屬性 (有些預設值已設定) ：</span><span class="sxs-lookup"><span data-stu-id="14d9b-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="14d9b-220">**媒體編碼器名稱 *媒體編碼器標準***</span><span class="sxs-lookup"><span data-stu-id="14d9b-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="14d9b-221">**編碼預設 *內容自動調整多重位元速率* 的值**</span><span class="sxs-lookup"><span data-stu-id="14d9b-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="14d9b-222">***Video1.mp4的作業名稱媒體編碼器標準處理***</span><span class="sxs-lookup"><span data-stu-id="14d9b-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="14d9b-223">**輸出媒體資產名稱 *Video1.mp4--媒體編碼器標準編碼***</span><span class="sxs-lookup"><span data-stu-id="14d9b-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Azure 入口網站](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="14d9b-225">按一下 [ **建立** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="14d9b-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="14d9b-226">您會看到 **已新增編碼作業** 的橫條，請按一下該列，隨即會出現一個面板，其中顯示編碼進度。</span><span class="sxs-lookup"><span data-stu-id="14d9b-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-17.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="14d9b-229">等候作業完成。</span><span class="sxs-lookup"><span data-stu-id="14d9b-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="14d9b-230">完成之後，您可以使用該面板右上方的 ' X ' 來關閉面板。</span><span class="sxs-lookup"><span data-stu-id="14d9b-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-19.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="14d9b-233">所需的時間取決於您的影片檔案大小。</span><span class="sxs-lookup"><span data-stu-id="14d9b-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="14d9b-234">此程式可能需要相當長的時間。</span><span class="sxs-lookup"><span data-stu-id="14d9b-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="14d9b-235">現在已建立影片的編碼版本，您可以將其發佈，使其可供存取。</span><span class="sxs-lookup"><span data-stu-id="14d9b-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="14d9b-236">若要這樣做，請按一下藍色連結 **資產** 以返回 [資產] 頁面。</span><span class="sxs-lookup"><span data-stu-id="14d9b-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="14d9b-238">您將會看到您的影片與另一個，也就是 **_多位元率_ 的資產類型**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-238">You will see your video along with another, which is of **Asset Type _Multi-Bitrate MP4_**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="14d9b-240">您可能會注意到，新的資產與您的初始影片是 *未知* 的，且其 **大小** 為 ' 0 ' 個位元組，只要重新整理您的視窗，即可進行更新。</span><span class="sxs-lookup"><span data-stu-id="14d9b-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="14d9b-241">按一下此新資產。</span><span class="sxs-lookup"><span data-stu-id="14d9b-241">Click this new asset.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="14d9b-243">您將會看到與先前所用的面板類似的面板，只是這是不同的資產。</span><span class="sxs-lookup"><span data-stu-id="14d9b-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="14d9b-244">按一下位於頁面頂端的 [ **發佈** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="14d9b-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="14d9b-246">系統會提示您將 **定位器**（即進入點）設定為您資產中的檔案。</span><span class="sxs-lookup"><span data-stu-id="14d9b-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="14d9b-247">針對您的案例，請設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="14d9b-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="14d9b-248">**定位器類型**  > **漸進式**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="14d9b-249">在此案例中，會將您的 **日期** 和 **時間** 設定為您目前的日期，到未來的時間 (100 年) 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="14d9b-250">保持原狀，或將它變更為 [符合]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="14d9b-251">如需定位器的詳細資訊，以及您可以選擇的內容，請造訪 [Azure 媒體服務檔](/azure/media-services/media-services-concepts)。</span><span class="sxs-lookup"><span data-stu-id="14d9b-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="14d9b-252">在該面板的底部，按一下 [ **新增** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="14d9b-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="14d9b-254">您的影片現在已發佈，可以使用其端點進行串流處理。</span><span class="sxs-lookup"><span data-stu-id="14d9b-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="14d9b-255">頁面上的下一頁是 [檔案 **] 區段。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="14d9b-256">這是您影片的不同編碼版本的位置。</span><span class="sxs-lookup"><span data-stu-id="14d9b-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="14d9b-257">選取下圖中的最高可能解析度一個 (在下圖中，它是1920x960 檔案) ，然後將會出現右側面板。</span><span class="sxs-lookup"><span data-stu-id="14d9b-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="14d9b-258">您會在該處找到 **下載 URL**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="14d9b-259">複製此 **端點** ，因為您稍後會在程式碼中使用它。</span><span class="sxs-lookup"><span data-stu-id="14d9b-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-26.png)    

    ![Azure 入口網站](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="14d9b-262">您也可以按下 [ **播放** ] 按鈕播放影片並進行測試。</span><span class="sxs-lookup"><span data-stu-id="14d9b-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="14d9b-263">您現在必須上傳您將在此實驗中使用的第二部影片。</span><span class="sxs-lookup"><span data-stu-id="14d9b-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="14d9b-264">遵循上述步驟，為第二部影片重複相同的程式。</span><span class="sxs-lookup"><span data-stu-id="14d9b-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="14d9b-265">請確定您也複製了第二個 **端點** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="14d9b-266">使用下列 [連結下載第二部影片](https://vimeo.com/214402865)。</span><span class="sxs-lookup"><span data-stu-id="14d9b-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="14d9b-267">這兩個影片都發佈之後，您就可以開始進行下一章。</span><span class="sxs-lookup"><span data-stu-id="14d9b-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="14d9b-268">第3章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="14d9b-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="14d9b-269">以下是使用混合式開發進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="14d9b-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="14d9b-270">開啟 **Unity** ，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-270">Open **Unity** and click **New**.</span></span> 

    ![Azure 入口網站](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="14d9b-272">您現在將需要提供 Unity 專案名稱，請插入 **MR \_ 360VideoStreaming。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="14d9b-273">請確定專案類型設定為 **3d**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="14d9b-274">將位置設定為適合您 (記住，較接近根目錄的) 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="14d9b-275">然後，按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-275">Then, click **Create project**.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="14d9b-277">在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="14d9b-278">移至 [ **_編輯_\*喜好**\* 設定]，然後在新視窗中，流覽至 [**外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-278">Go to **_Edit_ *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="14d9b-279">將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="14d9b-280">關閉 [ **喜好** 設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="14d9b-280">Close the **Preferences** window.</span></span>

    ![Azure 入口網站](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="14d9b-282">接下來，移至 [檔案 ***組建設定*** ]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至 **通用 Windows 平臺**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="14d9b-283">也請確定：</span><span class="sxs-lookup"><span data-stu-id="14d9b-283">Also make sure that:</span></span>

    1. <span data-ttu-id="14d9b-284">**目標裝置** 設定為 **任何裝置。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="14d9b-285">**組建類型** 設定為 **D3D。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="14d9b-286">**SDK** 設定為 [ **最新安裝]。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="14d9b-287">**Visual Studio 版本** 設定為 [ **最新安裝]。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="14d9b-288">**組建並執行** 設定為 [ **本機電腦]。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="14d9b-289">請不要擔心立即設定 **幕後** 的工作，因為您稍後將會進行設定。</span><span class="sxs-lookup"><span data-stu-id="14d9b-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="14d9b-290">其餘設定應該保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="14d9b-290">The remaining settings should be left as default for now.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="14d9b-292">在 [ **組建設定** ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 **器** 所在空間中的相關面板。</span><span class="sxs-lookup"><span data-stu-id="14d9b-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="14d9b-293">在此面板中，需要驗證幾個設定：</span><span class="sxs-lookup"><span data-stu-id="14d9b-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="14d9b-294">在 [ **其他設定** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="14d9b-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="14d9b-295">**腳本\*\*\*\*執行階段版本** 應該是 **穩定** 的 ( .net 3.5 對等) 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="14d9b-296">**腳本後端** 應該是 **.net。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="14d9b-297">**API 相容性層級** 應為 **.net 4.6。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="14d9b-299">在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="14d9b-301">在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：</span><span class="sxs-lookup"><span data-stu-id="14d9b-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="14d9b-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="14d9b-302">**InternetClient**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="14d9b-304">進行這些變更之後，請關閉 [ **組建設定** ] 視窗。</span><span class="sxs-lookup"><span data-stu-id="14d9b-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="14d9b-305">儲存您的專案 \**File* \* save project \* \*。</span><span class="sxs-lookup"><span data-stu-id="14d9b-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="14d9b-306">第4章-匯入 InsideOutSphere Unity 套件</span><span class="sxs-lookup"><span data-stu-id="14d9b-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14d9b-307">如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意下載 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)，並將其匯入到您的專案中做為 [**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 **第5章**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="14d9b-308">您仍然需要建立 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="14d9b-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="14d9b-309">在此課程中，您將需要下載名為 [**InsideOutSphere. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)的 Unity 資產套件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="14d9b-310">如何匯入 **unitypackage**：</span><span class="sxs-lookup"><span data-stu-id="14d9b-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="14d9b-311">使用 Unity 儀表板，在畫面頂端的功能表中按一下 [ **資產** ]，然後按一下 [匯 **入封裝 > 自訂套件**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="14d9b-313">使用檔案選擇器選取 **InsideOutSphere unitypackage** 封裝，然後按一下 [ **開啟**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="14d9b-314">系統會向您顯示此資產的元件清單。</span><span class="sxs-lookup"><span data-stu-id="14d9b-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="14d9b-315">按一下 [匯 **入**] 以確認匯入。</span><span class="sxs-lookup"><span data-stu-id="14d9b-315">Confirm the import by clicking **Import**.</span></span>

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="14d9b-317">匯入完成後，您會注意到您的 **資產** 資料夾中有三個新的資料夾、**材質**、**模型** 和 **Prefabs**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="14d9b-318">這種資料夾結構一般適用于 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="14d9b-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="14d9b-320">開啟 [ **模型** ] 資料夾，您會看到 **InsideOutSphere** 模型已匯入。</span><span class="sxs-lookup"><span data-stu-id="14d9b-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="14d9b-321">在 [ **材質] 資料夾內** ，您會發現 **InsideOutSpheres** 材質  *Lambert1*，以及一個稱為 *ButtonMaterial* 的材質，這是 GazeButton 所使用的資料，您很快就會看到。</span><span class="sxs-lookup"><span data-stu-id="14d9b-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="14d9b-322">**Prefabs** 資料夾包含 **InsideOutSphere** 預製專案，其中包含 **InsideOutSphere** *模型* 和 *GazeButton*。</span><span class="sxs-lookup"><span data-stu-id="14d9b-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="14d9b-323">**未包含任何程式碼**，您將遵循本課程來撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="14d9b-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="14d9b-324">**在階層中，選取\*\*\*\*主要攝影機** 物件，並更新下列元件：</span><span class="sxs-lookup"><span data-stu-id="14d9b-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="14d9b-325">**轉換**</span><span class="sxs-lookup"><span data-stu-id="14d9b-325">**Transform**</span></span>

        1.  <span data-ttu-id="14d9b-326">Position = **X**：0， **Y**：0， **Z**：0。</span><span class="sxs-lookup"><span data-stu-id="14d9b-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="14d9b-327">旋轉 = **X**：0， **Y**：0， **Z**：0。</span><span class="sxs-lookup"><span data-stu-id="14d9b-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="14d9b-328">Scale **X**：1， **Y**：1， **Z**：1。</span><span class="sxs-lookup"><span data-stu-id="14d9b-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="14d9b-329">**相機**</span><span class="sxs-lookup"><span data-stu-id="14d9b-329">**Camera**</span></span>

        1. <span data-ttu-id="14d9b-330">**清除旗標**：單色。</span><span class="sxs-lookup"><span data-stu-id="14d9b-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="14d9b-331">**裁剪平面**：近：0.1，遠：6。</span><span class="sxs-lookup"><span data-stu-id="14d9b-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="14d9b-333">流覽至 [ **預製專案** ] 資料夾，然後將 [ **InsideOutSphere** 預製專案] 拖曳至 [階層 **] 面板中** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="14d9b-335">按一下其旁邊的小箭號，以展開階層 **內的** **InsideOutSphere** 物件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="14d9b-336">您將會在其底下看到稱為 **GazeButton** 的 **子** 物件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="14d9b-337">這會用來變更幕後和影片。</span><span class="sxs-lookup"><span data-stu-id="14d9b-337">This will be used to change scenes and thus videos.</span></span>

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="14d9b-339">在 [偵測器] 視窗中，按一下 **InsideOutSphere** 的 [轉換] 元件，確定已設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="14d9b-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="14d9b-340">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="14d9b-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="14d9b-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-341">**X** 0</span></span>  |          <span data-ttu-id="14d9b-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-342">**Y** 0</span></span>          |  <span data-ttu-id="14d9b-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="14d9b-344">轉換-旋轉</span><span class="sxs-lookup"><span data-stu-id="14d9b-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="14d9b-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-345">**X** 0</span></span>  |          <span data-ttu-id="14d9b-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="14d9b-346">**Y** -50</span></span>        |  <span data-ttu-id="14d9b-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="14d9b-348">轉換-調整規模</span><span class="sxs-lookup"><span data-stu-id="14d9b-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="14d9b-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="14d9b-349">**X** 1</span></span>   |          <span data-ttu-id="14d9b-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="14d9b-350">**Y** 1</span></span>          |  <span data-ttu-id="14d9b-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="14d9b-351">**Z** 1</span></span>  |

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="14d9b-353">按一下 [ **GazeButton** ] 子物件，並設定其 **轉換** ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="14d9b-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="14d9b-354">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="14d9b-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="14d9b-355">**X** 3。6</span><span class="sxs-lookup"><span data-stu-id="14d9b-355">**X** 3.6</span></span>|          <span data-ttu-id="14d9b-356">**Y** 1。3</span><span class="sxs-lookup"><span data-stu-id="14d9b-356">**Y** 1.3</span></span>        |  <span data-ttu-id="14d9b-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="14d9b-358">轉換-旋轉</span><span class="sxs-lookup"><span data-stu-id="14d9b-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="14d9b-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-359">**X** 0</span></span>  |          <span data-ttu-id="14d9b-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-360">**Y** 0</span></span>          |  <span data-ttu-id="14d9b-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="14d9b-362">轉換-調整規模</span><span class="sxs-lookup"><span data-stu-id="14d9b-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="14d9b-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="14d9b-363">**X** 1</span></span>   |          <span data-ttu-id="14d9b-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="14d9b-364">**Y** 1</span></span>          |  <span data-ttu-id="14d9b-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="14d9b-365">**Z** 1</span></span>  |

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="14d9b-367">第5章-建立 VideoController 類別</span><span class="sxs-lookup"><span data-stu-id="14d9b-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="14d9b-368">**VideoController** 類別裝載兩個將用來從 Azure 媒體服務串流內容的影片端點。</span><span class="sxs-lookup"><span data-stu-id="14d9b-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="14d9b-369">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="14d9b-369">To create this class:</span></span>

1.  <span data-ttu-id="14d9b-370">在 [**專案**] 面板中的 [**資產] 資料夾** 上按一下滑鼠右鍵，然後按一下 [**建立] > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="14d9b-371">將資料夾命名為 **腳本**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-371">Name the folder **Scripts**.</span></span>

    ![建立 VideoController 類別](images/AzureLabs-Lab6-43.png)

    ![建立 VideoController 類別](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="14d9b-374">按兩下 [ **腳本** ] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="14d9b-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="14d9b-375">在資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > C \# 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="14d9b-376">將腳本命名為 **VideoController**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-376">Name the script **VideoController**.</span></span>

    ![建立 VideoController 類別](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="14d9b-378">按兩下新的 **VideoController** 腳本，以 **Visual Studio 2017 開啟。**</span><span class="sxs-lookup"><span data-stu-id="14d9b-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![建立 VideoController 類別](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="14d9b-380">更新程式碼檔案頂端的命名空間，如下所示：</span><span class="sxs-lookup"><span data-stu-id="14d9b-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="14d9b-381">在 **VideoController** 類別中輸入下列變數，以及 **喚醒的 ()** 方法：</span><span class="sxs-lookup"><span data-stu-id="14d9b-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="14d9b-382">現在是從您的 Azure 媒體服務影片進入端點的時間：</span><span class="sxs-lookup"><span data-stu-id="14d9b-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="14d9b-383">*Video1endpoint* 變數中的第一個。</span><span class="sxs-lookup"><span data-stu-id="14d9b-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="14d9b-384">*Video2endpoint* 變數中的第二個。</span><span class="sxs-lookup"><span data-stu-id="14d9b-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="14d9b-385">在 Unity 中使用 *HTTPs* 的已知問題，版本 2017.4.1 f1。</span><span class="sxs-lookup"><span data-stu-id="14d9b-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="14d9b-386">如果影片在播放時發生錯誤，請嘗試改為使用 ' HTTP '。</span><span class="sxs-lookup"><span data-stu-id="14d9b-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="14d9b-387">接下來，必須編輯 **開始 ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="14d9b-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="14d9b-388">每次使用者切換場景時都會觸發這個方法， (藉由查看注視按鈕來切換影片) 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="14d9b-389">在 **Start ()** 方法之後，插入 **>playvideo ()** *IEnumerator* 方法，此方法將用來順暢地啟動影片 (因此) 不會出現任何斷斷續續。</span><span class="sxs-lookup"><span data-stu-id="14d9b-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="14d9b-390">這個類別所需的最後一個方法是 **ChangeScene ()** 方法，它會用來在場景之間交換。</span><span class="sxs-lookup"><span data-stu-id="14d9b-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="14d9b-391">**ChangeScene ()** 方法會使用一個方便 \# 的 C 功能，稱為 *條件運算子*。</span><span class="sxs-lookup"><span data-stu-id="14d9b-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="14d9b-392">如此一來，就可以檢查條件，然後根據檢查結果傳回值，全都在單一語句內。</span><span class="sxs-lookup"><span data-stu-id="14d9b-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="14d9b-393">請遵循此 [連結來深入瞭解條件運算子](/dotnet/csharp/language-reference/operators/conditional-operator)。</span><span class="sxs-lookup"><span data-stu-id="14d9b-393">Follow this [link to learn more about Conditional Operator](/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="14d9b-394">在回到 Unity 之前，請先將您的變更儲存在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="14d9b-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="14d9b-395">回到 Unity 編輯器中，按一下 [from] {. 底線} [ **VideoController** ] 類別，然後將 [ **Scripts** ] 資料夾拖曳至 [階層]**面板中** 的 [**主要攝影機**] 物件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="14d9b-396">按一下 **主要攝影機** ，然後查看 [偵測 **器] 面板**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="14d9b-397">您會發現，在新加入的腳本元件中，有一個具有空白值的欄位。</span><span class="sxs-lookup"><span data-stu-id="14d9b-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="14d9b-398">這是參考欄位，以程式碼中的公用變數為目標。</span><span class="sxs-lookup"><span data-stu-id="14d9b-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="14d9b-399">將 **InsideOutSphere** 物件從 [階層] **面板** 拖曳至 **球體** 位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="14d9b-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="14d9b-400">![建立 VideoController 類別 ](images/AzureLabs-Lab6-47.png)
     ![ 建立 VideoController 類別](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="14d9b-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="14d9b-401">第6章-建立注視類別</span><span class="sxs-lookup"><span data-stu-id="14d9b-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="14d9b-402">此類別負責建立將從 **主要相機** 向前投影的 **Raycast** ，以偵測使用者所查看的物件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-402">This class is responsible for creating a **Raycast** that will be projected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="14d9b-403">在此情況下， **Raycast** 將需要識別使用者是否正在查看場景中的 **GazeButton** 物件，並觸發行為。</span><span class="sxs-lookup"><span data-stu-id="14d9b-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="14d9b-404">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="14d9b-404">To create this Class:</span></span>

1.  <span data-ttu-id="14d9b-405">移至您先前建立的 **腳本** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="14d9b-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="14d9b-406">以滑鼠右鍵按一下 [ **專案** ] 面板中的 [*建立* \* C \# 腳本]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="14d9b-407">將腳本命名為 **注視**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="14d9b-408">按兩下新的 ***注視** _ 腳本，使用 _ *Visual Studio 2017* 來開啟它。*</span><span class="sxs-lookup"><span data-stu-id="14d9b-408">Double click on the new ***Gaze** _ script to open it with _ *Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="14d9b-409">請確定下列命名空間位於腳本頂端，並移除任何其他命名空間：</span><span class="sxs-lookup"><span data-stu-id="14d9b-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="14d9b-410">然後，在 **注視** 類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="14d9b-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="14d9b-411">現在需要新增 **喚醒 ()** 和 **啟動 ()** 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="14d9b-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="14d9b-412">在 **Update ()** 方法中新增下列程式碼，以投影 Raycast 並偵測目標點擊：</span><span class="sxs-lookup"><span data-stu-id="14d9b-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="14d9b-413">在回到 Unity 之前，請先將您的變更儲存在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="14d9b-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="14d9b-414">按一下 [腳本] 資料夾中的 [ **注視** ] 類別，並將其拖曳至 [階層 **] 面板中** 的 [主要攝影機] 物件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="14d9b-415">第7章-設定兩個 Unity 場景</span><span class="sxs-lookup"><span data-stu-id="14d9b-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="14d9b-416">本章的目的是要設定兩個場景，每個都裝載要串流的影片。</span><span class="sxs-lookup"><span data-stu-id="14d9b-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="14d9b-417">您將複製已建立的場景，如此您就不需要再設定一次，不過您接著會編輯新的場景，讓 *GazeButton* 物件位於不同的位置，並具有不同的外觀。</span><span class="sxs-lookup"><span data-stu-id="14d9b-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="14d9b-418">這是為了示範如何在幕後變更。</span><span class="sxs-lookup"><span data-stu-id="14d9b-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="14d9b-419">若要這麼做，請前往 [檔案 **> 將場景另存為**...]。[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="14d9b-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="14d9b-420">按一下 [ **新增資料夾** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="14d9b-420">Click the **New folder** button.</span></span>

    ![第7章-設定兩個 Unity 場景](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="14d9b-422">將資料夾命名為 **幕後**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="14d9b-423">[ **儲存場景** ] 視窗仍會開啟。</span><span class="sxs-lookup"><span data-stu-id="14d9b-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="14d9b-424">開啟新建立的 **場景** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="14d9b-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="14d9b-425">在 [ **檔案名：** 文字] 欄位中，輸入 **VideoScene1**，然後按 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="14d9b-426">回到 Unity，開啟您的 **場景** 資料夾，然後以滑鼠左鍵按一下您的 **VideoScene1** 檔案。</span><span class="sxs-lookup"><span data-stu-id="14d9b-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="14d9b-427">使用鍵盤，然後按 **Ctrl + D** ，即可複製該場景</span><span class="sxs-lookup"><span data-stu-id="14d9b-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="14d9b-428">您也可以藉由流覽來 **編輯 > 複製** 來執行 **重複** 的命令。</span><span class="sxs-lookup"><span data-stu-id="14d9b-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="14d9b-429">Unity 會自動遞增場景名稱，但仍請檢查，以確保它符合先前插入的程式碼。</span><span class="sxs-lookup"><span data-stu-id="14d9b-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="14d9b-430">您應具備 **VideoScene1** 和 **VideoScene2**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="14d9b-431">在您的兩個場景中，移至 [檔案 **> 組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="14d9b-432">在 [ **組建設定** ] 視窗開啟的情況下，將您的場景拖曳至 [組建] 區段 **中的場景** 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="14d9b-434">您可以透過按住 **Ctrl** 鍵，然後在每個場景上按一下滑鼠左鍵，然後將兩者拖曳，以從您的 **場景** 資料夾選取這兩個場景。</span><span class="sxs-lookup"><span data-stu-id="14d9b-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="14d9b-435">關閉 [ **組建設定** ] 視窗，然後按兩下 [ **VideoScene2**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="14d9b-436">開啟第二個場景時，按一下 **InsideOutSphere** 的 **GazeButton** 子物件，並設定其轉換，如下所示：</span><span class="sxs-lookup"><span data-stu-id="14d9b-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="14d9b-437">轉換-位置</span><span class="sxs-lookup"><span data-stu-id="14d9b-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="14d9b-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-438">**X** 0</span></span>  |         <span data-ttu-id="14d9b-439">**Y** 1。3</span><span class="sxs-lookup"><span data-stu-id="14d9b-439">**Y** 1.3</span></span>         | <span data-ttu-id="14d9b-440">**Z** 3。6</span><span class="sxs-lookup"><span data-stu-id="14d9b-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="14d9b-441">轉換-旋轉</span><span class="sxs-lookup"><span data-stu-id="14d9b-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="14d9b-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-442">**X** 0</span></span>  |          <span data-ttu-id="14d9b-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-443">**Y** 0</span></span>          |  <span data-ttu-id="14d9b-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="14d9b-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="14d9b-445">轉換-調整規模</span><span class="sxs-lookup"><span data-stu-id="14d9b-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="14d9b-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="14d9b-446">**X** 1</span></span>   |          <span data-ttu-id="14d9b-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="14d9b-447">**Y** 1</span></span>          |  <span data-ttu-id="14d9b-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="14d9b-448">**Z** 1</span></span>  |

10. <span data-ttu-id="14d9b-449">在仍選取 **GazeButton** 子 **系的情況** 下，查看偵測器和 **網格篩選**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="14d9b-450">按一下 **網格** 參考欄位旁的小小目標：</span><span class="sxs-lookup"><span data-stu-id="14d9b-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="14d9b-452">[ **選取網格** ] 快顯視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="14d9b-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="14d9b-453">按兩下 **資產** 清單中的 **Cube** 網格。</span><span class="sxs-lookup"><span data-stu-id="14d9b-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="14d9b-455">**網格篩選器** 將會更新，現在是一個 **Cube**。</span><span class="sxs-lookup"><span data-stu-id="14d9b-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="14d9b-456">現在，按一下 [**球體碰撞**] 旁的 **齒輪** 圖示，然後按一下 [**移除元件**]，即可從這個物件中刪除碰撞。</span><span class="sxs-lookup"><span data-stu-id="14d9b-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="14d9b-458">在仍選取 **GazeButton** 的情況下，按一下位於偵測 **器** 底部的 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="14d9b-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="14d9b-459">在 [搜尋] 欄位中 **，輸入方塊**，方塊 **碰撞** 者將會是選項，請按一下此選項，將方塊 **碰撞** 程式新增至您的 **GazeButton** 物件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="14d9b-461">**GazeButton** 現在已部分更新，看起來會不同，不過，您現在會建立新的 **材質**，讓它看起來完全不同，而且比第一個場景中的物件更容易辨識為不同的物件。</span><span class="sxs-lookup"><span data-stu-id="14d9b-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="14d9b-462">流覽至 [**專案] 面板** 中的 [**材質**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="14d9b-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="14d9b-463">複製 **ButtonMaterial** 材質 (按下鍵盤上的 **Ctrl**  +  **D** ，或以滑鼠左鍵按一下 **材質**，然後從 [**編輯** 檔案] 功能表選項中，選取 [**複製**) 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="14d9b-464">![第7章--設定兩個 Unity 場景 ](images/AzureLabs-Lab6-55.png)
     ![ 第7章--設定兩個 unity 場景](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="14d9b-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="14d9b-465">選取名為 **ButtonMaterial 1**) 的新 **ButtonMaterial** 材質 (，然後在 [偵測 **器**] 中，按一下 [ **>albedo** 色彩] 視窗。</span><span class="sxs-lookup"><span data-stu-id="14d9b-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="14d9b-466">快顯視窗隨即出現，您可以在其中選取另一種色彩 (選擇任何您喜歡的) ，然後關閉快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="14d9b-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="14d9b-467">材質將會是自己的實例，而且不同于原始的實例。</span><span class="sxs-lookup"><span data-stu-id="14d9b-467">The Material will be its own instance, and different to the original.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="14d9b-469">將新的 **材質** 拖曳至 **GazeButton** 子系上，以完整更新其外觀，以便從第一個場景按鈕輕鬆地辨別。</span><span class="sxs-lookup"><span data-stu-id="14d9b-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="14d9b-471">至此，您可以在建立 UWP 專案之前，先在編輯器中測試專案。</span><span class="sxs-lookup"><span data-stu-id="14d9b-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="14d9b-472">在 **編輯器** 中按下 [**播放**] 按鈕，並磨損您的耳機。</span><span class="sxs-lookup"><span data-stu-id="14d9b-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="14d9b-474">查看兩個 **GazeButton** 物件，以在第一和第二部影片之間切換。</span><span class="sxs-lookup"><span data-stu-id="14d9b-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="14d9b-475">第8章-建立 UWP 解決方案</span><span class="sxs-lookup"><span data-stu-id="14d9b-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="14d9b-476">確定編輯器沒有任何錯誤之後，您就可以開始建立。</span><span class="sxs-lookup"><span data-stu-id="14d9b-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="14d9b-477">若要建立：</span><span class="sxs-lookup"><span data-stu-id="14d9b-477">To Build:</span></span>

1.  <span data-ttu-id="14d9b-478">按一下 [檔案] **> 儲存**]，以儲存目前的場景。</span><span class="sxs-lookup"><span data-stu-id="14d9b-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="14d9b-479">核取稱為 **Unity C \# Projects** 的方塊 (這很重要，因為它可讓您在組建完成) 之後編輯類別。</span><span class="sxs-lookup"><span data-stu-id="14d9b-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="14d9b-480">移至 [檔案 **> 組建設定**] 中，按一下 [ **組建**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="14d9b-481">系統會提示您選取要在其中建立解決方案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="14d9b-481">You will be prompted to select the folder where you want to build the Solution.</span></span>

5.  <span data-ttu-id="14d9b-482">建立 **組建** 資料夾，然後在該資料夾內使用您選擇的適當名稱建立另一個資料夾。</span><span class="sxs-lookup"><span data-stu-id="14d9b-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="14d9b-483">按一下新資料夾，然後按一下 [ **選取資料夾**]，選擇該資料夾，在該位置開始組建。</span><span class="sxs-lookup"><span data-stu-id="14d9b-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="14d9b-484">![第8章--建立 UWP 解決方案 ](images/AzureLabs-Lab6-60.png)
     ![ 第8章--建立 uwp 解決方案](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="14d9b-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="14d9b-485">Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗。</span><span class="sxs-lookup"><span data-stu-id="14d9b-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="14d9b-486">第9章-在本機電腦上部署</span><span class="sxs-lookup"><span data-stu-id="14d9b-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="14d9b-487">組建完成後， **檔案總管** 視窗會出現在組建的位置。</span><span class="sxs-lookup"><span data-stu-id="14d9b-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="14d9b-488">開啟您命名和建立的資料夾，然後按兩下該資料夾內的方案 ( .sln) 檔案，以 Visual Studio 2017 開啟您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="14d9b-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="14d9b-489">唯一要做的事，就是將您的應用程式部署到電腦 (或 *本機電腦*) 。</span><span class="sxs-lookup"><span data-stu-id="14d9b-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="14d9b-490">若要部署到本機電腦：</span><span class="sxs-lookup"><span data-stu-id="14d9b-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="14d9b-491">在 **Visual Studio 2017** 中，開啟剛建立的方案檔。</span><span class="sxs-lookup"><span data-stu-id="14d9b-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="14d9b-492">在 [ **方案平臺**] 中，選取 [ **x86]、[本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="14d9b-493">在 [ **方案** 設定] 中選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![第9章--在本機電腦上部署](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="14d9b-495">您現在需要將任何套件還原至您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="14d9b-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="14d9b-496">以滑鼠右鍵按一下您的 **方案**，然後按一下 [**還原解決方案的 NuGet 套件**]。</span><span class="sxs-lookup"><span data-stu-id="14d9b-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="14d9b-497">這是因為 Unity 所建立的套件必須以您的本機電腦參考為目標。</span><span class="sxs-lookup"><span data-stu-id="14d9b-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="14d9b-498">移至 [ **組建] 功能表** ，然後按一下 [ **部署方案** ]，將應用程式側載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="14d9b-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="14d9b-499">Visual Studio 將會先建立您的應用程式，然後再加以部署。</span><span class="sxs-lookup"><span data-stu-id="14d9b-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="14d9b-500">您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好要啟動。</span><span class="sxs-lookup"><span data-stu-id="14d9b-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![第9章--在本機電腦上部署](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="14d9b-502">當您執行混合現實應用程式時，您會在應用程式中使用的 **InsideOutSphere** 模型內。</span><span class="sxs-lookup"><span data-stu-id="14d9b-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="14d9b-503">此球體將是影片串流處理的位置，可提供 filmed 的內送影片的360度觀點， (這種) 的觀點。</span><span class="sxs-lookup"><span data-stu-id="14d9b-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="14d9b-504">如果影片需要幾秒鐘的時間才能載入，您的應用程式會受到您的可用網際網路速度的要求，因為影片需要先取出再下載，以串流至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="14d9b-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="14d9b-505">當您準備好時，請以紅色球體撥雲見日來變更場景，並開啟第二個影片！</span><span class="sxs-lookup"><span data-stu-id="14d9b-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="14d9b-506">然後，您可以在第二個場景中使用藍色立方體來自由返回！</span><span class="sxs-lookup"><span data-stu-id="14d9b-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="14d9b-507">您已完成的 Azure 媒體服務應用程式</span><span class="sxs-lookup"><span data-stu-id="14d9b-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="14d9b-508">恭喜，您建立了一個混合現實應用程式，利用 Azure 媒體服務來串流360的影片。</span><span class="sxs-lookup"><span data-stu-id="14d9b-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![實驗室結果](images/AzureLabs-Lab6-00.png)

![實驗室結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="14d9b-511">額外練習</span><span class="sxs-lookup"><span data-stu-id="14d9b-511">Bonus Exercises</span></span>

<span data-ttu-id="14d9b-512">**練習1**</span><span class="sxs-lookup"><span data-stu-id="14d9b-512">**Exercise 1**</span></span>

<span data-ttu-id="14d9b-513">您可以在本教學課程中，只使用單一場景來變更影片。</span><span class="sxs-lookup"><span data-stu-id="14d9b-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="14d9b-514">試驗您的應用程式，並使其進入單一場景！</span><span class="sxs-lookup"><span data-stu-id="14d9b-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="14d9b-515">或許甚至可以將另一部影片新增至混合。</span><span class="sxs-lookup"><span data-stu-id="14d9b-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="14d9b-516">**練習2**</span><span class="sxs-lookup"><span data-stu-id="14d9b-516">**Exercise 2**</span></span>

<span data-ttu-id="14d9b-517">使用 Azure 和 Unity 進行實驗，並嘗試執行應用程式自動選取不同檔案大小的影片，視網際網路連線的強度而定。</span><span class="sxs-lookup"><span data-stu-id="14d9b-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>