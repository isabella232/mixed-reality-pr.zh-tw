---
title: HoloLens (第1代) 和 Azure 312-Bot 整合
description: 完成本課程，以瞭解如何使用 Microsoft Bot Framework v4 來建立和部署 bot，並在混合現實應用程式中與其通訊。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學術，unity，教學課程，api，電腦視覺，hololens，沉浸，vr，microsoft bot framework v4，web 應用程式 bot，bot framework，microsoft bot，Windows 10，Visual Studio
ms.openlocfilehash: 5bef129b9ccbbba6bf2bce835bd1567d4f596932
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730315"
---
# <a name="hololens-1st-gen-and-azure-312-bot-integration"></a><span data-ttu-id="d68b1-104">HoloLens (第1代) 和 Azure 312： Bot 整合</span><span class="sxs-lookup"><span data-stu-id="d68b1-104">HoloLens (1st gen) and Azure 312: Bot integration</span></span>

>[!NOTE]
><span data-ttu-id="d68b1-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="d68b1-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d68b1-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="d68b1-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d68b1-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="d68b1-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d68b1-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="d68b1-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d68b1-109">未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="d68b1-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d68b1-110">當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。</span><span class="sxs-lookup"><span data-stu-id="d68b1-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<span data-ttu-id="d68b1-111">在此課程中，您將瞭解如何使用 Microsoft Bot Framework V4 來建立和部署 bot，並透過 Windows Mixed Reality 應用程式與其進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d68b1-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="d68b1-112">**Microsoft Bot Framework V4** 是一組 api，旨在為開發人員提供工具，以建立可擴充且可調整的 Bot 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d68b1-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="d68b1-113">如需詳細資訊，請造訪 [Microsoft Bot Framework 頁面](https://dev.botframework.com/) 或 [V4 Git 儲存](https://github.com/Microsoft/botbuilder-dotnet/wiki)機制。</span><span class="sxs-lookup"><span data-stu-id="d68b1-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="d68b1-114">完成本課程之後，您將會建立 Windows Mixed Reality 的應用程式，讓您能夠執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d68b1-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="d68b1-115">使用點一下 **手勢** 來啟動接聽使用者語音的 bot。</span><span class="sxs-lookup"><span data-stu-id="d68b1-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="d68b1-116">當使用者已說過某個問題時，bot 會嘗試提供回應。</span><span class="sxs-lookup"><span data-stu-id="d68b1-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="d68b1-117">在 Unity 場景中，以文字（位於 bot 附近）顯示 bot 回復。</span><span class="sxs-lookup"><span data-stu-id="d68b1-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="d68b1-118">在您的應用程式中，您可以自行決定如何將結果與您的設計整合。</span><span class="sxs-lookup"><span data-stu-id="d68b1-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="d68b1-119">本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="d68b1-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="d68b1-120">您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="d68b1-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="d68b1-121">裝置支援</span><span class="sxs-lookup"><span data-stu-id="d68b1-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d68b1-122">課程</span><span class="sxs-lookup"><span data-stu-id="d68b1-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d68b1-123"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d68b1-123"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d68b1-124"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="d68b1-124"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d68b1-125">MR 和 Azure 312：Bot 整合</span><span class="sxs-lookup"><span data-stu-id="d68b1-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="d68b1-126">✔️</span><span class="sxs-lookup"><span data-stu-id="d68b1-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d68b1-127">✔️</span><span class="sxs-lookup"><span data-stu-id="d68b1-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="d68b1-128">雖然本課程主要著重于 HoloLens，您也可以將本課程中所學到的內容套用到 Windows Mixed Reality 沉浸式 (VR) 耳機。</span><span class="sxs-lookup"><span data-stu-id="d68b1-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="d68b1-129">因為沉浸式 (VR) 耳機沒有可存取的攝影機，所以您需要有連接到電腦的外部攝影機。</span><span class="sxs-lookup"><span data-stu-id="d68b1-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="d68b1-130">當您依照課程的指示，您將會看到有關您可能需要採用以支援沉浸式 (VR) 耳機的任何變更的注意事項。</span><span class="sxs-lookup"><span data-stu-id="d68b1-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d68b1-131">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d68b1-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="d68b1-132">本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。</span><span class="sxs-lookup"><span data-stu-id="d68b1-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="d68b1-133">另外也請注意，本檔中的必要條件和書面指示，代表在撰寫 (2018 年7月) 時已經過測試和驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="d68b1-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="d68b1-134">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span><span class="sxs-lookup"><span data-stu-id="d68b1-134">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="d68b1-135">本課程建議您採用下列硬體和軟體：</span><span class="sxs-lookup"><span data-stu-id="d68b1-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="d68b1-136">開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)</span><span class="sxs-lookup"><span data-stu-id="d68b1-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="d68b1-137">啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="d68b1-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d68b1-138">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="d68b1-138">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d68b1-139">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="d68b1-139">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d68b1-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d68b1-140">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="d68b1-141">[Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="d68b1-141">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="d68b1-142">適用于 Azure 的網際網路存取，以及適用于 Azure Bot 抓取的網際網路存取。</span><span class="sxs-lookup"><span data-stu-id="d68b1-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="d68b1-143">如需詳細資訊， [請遵循此連結](https://dev.botframework.com/)。</span><span class="sxs-lookup"><span data-stu-id="d68b1-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="d68b1-144">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="d68b1-144">Before you start</span></span>

1.  <span data-ttu-id="d68b1-145">為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。</span><span class="sxs-lookup"><span data-stu-id="d68b1-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="d68b1-146">設定及測試 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d68b1-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="d68b1-147">如果您需要設定 HoloLens 的支援， [請務必造訪 HoloLens 安裝文章](/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="d68b1-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="d68b1-148">開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助針對每個使用者) 執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="d68b1-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="d68b1-149">如需有關校正的說明，請遵循此 [與 HoloLens 校正文章相關的連結](/hololens/hololens-calibration#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="d68b1-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="d68b1-150">如需有關感應器微調的說明，請依照此 [連結來進行「HoloLens 感應器微調」文章](/hololens/hololens-updates)。</span><span class="sxs-lookup"><span data-stu-id="d68b1-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="d68b1-151">第1章-建立 Bot 應用程式</span><span class="sxs-lookup"><span data-stu-id="d68b1-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="d68b1-152">第一個步驟是將您的 bot 建立為本機 ASP.Net Core Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d68b1-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="d68b1-153">完成並測試之後，您會將它發佈至 Azure 入口網站。</span><span class="sxs-lookup"><span data-stu-id="d68b1-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="d68b1-154">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d68b1-154">Open Visual Studio.</span></span> <span data-ttu-id="d68b1-155">建立新的專案，選取 [ **ASP NET Core Web 應用程式** ] 作為專案類型 (您將會在 [.Net) Core] 子區段下找到它，並將其命名為 **MyBot**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="d68b1-156">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d68b1-156">Click **OK**.</span></span>

2.  <span data-ttu-id="d68b1-157">在將出現的視窗中，選取 [ **空白**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="d68b1-158">此外，請確定目標設定為 [ **ASP NET Core 2.0** ]，並將 [驗證] 設定為 [ **無驗證**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="d68b1-159">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d68b1-159">Click **OK**.</span></span>  

    ![建立 bot 應用程式](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="d68b1-161">方案現在將會開啟。</span><span class="sxs-lookup"><span data-stu-id="d68b1-161">The solution will now open.</span></span> <span data-ttu-id="d68b1-162">以滑鼠右鍵按一下 **方案總管** 中的 [方案 **Mybot** ]，然後按一下 [**管理方案的 NuGet 套件**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![建立 Bot 應用程式](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="d68b1-164">在 [ **流覽** ] 索引標籤中， **搜尋 (確定** 您已核取 [ **包含發行前版本** ]) 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="d68b1-165">選取套件版本 **4.0.1-preview**，然後將專案方塊勾選。</span><span class="sxs-lookup"><span data-stu-id="d68b1-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="d68b1-166">然後按一下 [ **安裝**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-166">Then click on **Install**.</span></span> <span data-ttu-id="d68b1-167">您現在已安裝 **Bot Framework v4** 所需的程式庫。</span><span class="sxs-lookup"><span data-stu-id="d68b1-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="d68b1-168">關閉 [NuGet] 頁面。</span><span class="sxs-lookup"><span data-stu-id="d68b1-168">Close the NuGet page.</span></span>

    ![建立 bot 應用程式](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="d68b1-170">以滑鼠右鍵按一下您在方案總管 **中的\*\**專案*， 然後按一下 [**加入\*\* **|** **類別**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![建立 Bot 應用程式](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="d68b1-172">將類別命名為 **MyBot** ，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![建立 bot 應用程式](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="d68b1-174">重複先前的點，以建立另一個名為 **ConversationCoNtext** 的類別。</span><span class="sxs-lookup"><span data-stu-id="d68b1-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="d68b1-175">以滑鼠右鍵按一下 **方案總管** 中的 **wwwroot** ，然後按一下 [**加入** **|** **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="d68b1-176">選取 [  **HTML 網頁** ] (您將會在 Web) 小節下找到它。</span><span class="sxs-lookup"><span data-stu-id="d68b1-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="d68b1-177">將檔案命名為 **default.html**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-177">Name the file **default.html**.</span></span> <span data-ttu-id="d68b1-178">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-178">Click **Add**.</span></span>

    ![建立 bot 應用程式](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="d68b1-180">**方案總管** 中的類別/物件清單應如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d68b1-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![建立 bot 應用程式](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="d68b1-182">按兩下 **ConversationCoNtext** 類別。</span><span class="sxs-lookup"><span data-stu-id="d68b1-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="d68b1-183">此類別負責保存 bot 用來維護交談內容的變數。</span><span class="sxs-lookup"><span data-stu-id="d68b1-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="d68b1-184">這些交談內容值會保留在這個類別的實例中，因為每次收到活動時， **MyBot** 類別的任何實例都會重新整理。</span><span class="sxs-lookup"><span data-stu-id="d68b1-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="d68b1-185">將下列程式碼新增至類別：</span><span class="sxs-lookup"><span data-stu-id="d68b1-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="d68b1-186">按兩下 **MyBot** 類別。</span><span class="sxs-lookup"><span data-stu-id="d68b1-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="d68b1-187">此類別會裝載客戶的任何傳入活動所呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="d68b1-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="d68b1-188">在此類別中，您將會新增用來建立 bot 與客戶之間交談的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d68b1-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="d68b1-189">如先前所述，每次收到活動時，就會初始化這個類別的實例。</span><span class="sxs-lookup"><span data-stu-id="d68b1-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="d68b1-190">將下列程式碼新增至此類別：</span><span class="sxs-lookup"><span data-stu-id="d68b1-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="d68b1-191">按兩下 **啟動** 類別。</span><span class="sxs-lookup"><span data-stu-id="d68b1-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="d68b1-192">此類別會初始化 bot。</span><span class="sxs-lookup"><span data-stu-id="d68b1-192">This class will initialize the bot.</span></span> <span data-ttu-id="d68b1-193">將下列程式碼新增至類別：</span><span class="sxs-lookup"><span data-stu-id="d68b1-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="d68b1-194">開啟 Program 類別檔案，並確認其中的 **程式** 代碼與下列相同：</span><span class="sxs-lookup"><span data-stu-id="d68b1-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="d68b1-195">請記得儲存您的變更 **，若要** 這樣做，請  >  從 Visual Studio 頂端的工具列中，移至 [**全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="d68b1-196">第2章-建立 Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="d68b1-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="d68b1-197">既然您已建立 bot 的程式碼，您必須將它發佈至 Azure 入口網站上的 *Web 應用程式 bot* 服務實例。</span><span class="sxs-lookup"><span data-stu-id="d68b1-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="d68b1-198">本章將示範如何在 Azure 上建立及設定 Bot 服務，然後將您的程式碼發佈至該服務。</span><span class="sxs-lookup"><span data-stu-id="d68b1-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="d68b1-199">首先，登入 Azure 入口網站 (https://portal.azure.com) 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="d68b1-200">如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。</span><span class="sxs-lookup"><span data-stu-id="d68b1-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="d68b1-201">如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d68b1-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="d68b1-202">登入後，按一下左上角的 [ **建立資源** ]，並搜尋 *Web 應用程式 bot*，然後按一下 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="d68b1-204">新頁面將提供 *Web 應用程式 Bot* 服務的描述。</span><span class="sxs-lookup"><span data-stu-id="d68b1-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="d68b1-205">在此頁面的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。</span><span class="sxs-lookup"><span data-stu-id="d68b1-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="d68b1-207">當您按一下 [ **建立**] 之後：</span><span class="sxs-lookup"><span data-stu-id="d68b1-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="d68b1-208">為此服務實例插入您想要的 **名稱** 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="d68b1-209">選取 [訂用帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="d68b1-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="d68b1-210">選擇資源群組，或建立一個新的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="d68b1-211">資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。</span><span class="sxs-lookup"><span data-stu-id="d68b1-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="d68b1-212">建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="d68b1-213">如果您想要閱讀更多有關 Azure 資源群組的資訊， [請遵循此連結](/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="d68b1-213">If you wish to read more about Azure Resource Groups, [please follow this link](/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="d68b1-214">如果您要建立新的資源群組) ，請判斷資源群組 (的位置。</span><span class="sxs-lookup"><span data-stu-id="d68b1-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="d68b1-215">位置最好是在應用程式執行所在的區域中。</span><span class="sxs-lookup"><span data-stu-id="d68b1-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="d68b1-216">某些 Azure 資產僅適用于某些區域。</span><span class="sxs-lookup"><span data-stu-id="d68b1-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="d68b1-217">選取適合您的 **定價層** ，如果這是您第一次建立 *Web 應用程式 Bot* 服務，則應可使用名為 F0) 的免費層 (</span><span class="sxs-lookup"><span data-stu-id="d68b1-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="d68b1-218">**應用程式名稱** 可以與 *Bot 名稱* 一樣保持不變。</span><span class="sxs-lookup"><span data-stu-id="d68b1-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="d68b1-219">將 *Bot 範本* 保留為 **基本 (c # )**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="d68b1-220">*App service 方案/位置* 應該已自動填入您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d68b1-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="d68b1-221">設定您想要用來裝載 Bot 的 **Azure 儲存體** 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="d68b1-222">如果您還沒有帳戶，可以在此建立。</span><span class="sxs-lookup"><span data-stu-id="d68b1-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="d68b1-223">您也必須確認您已瞭解套用到此服務的條款及條件。</span><span class="sxs-lookup"><span data-stu-id="d68b1-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="d68b1-224">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-224">Click Create.</span></span>
 
        ![建立 Azure Bot 服務](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="d68b1-226">當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="d68b1-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="d68b1-227">建立服務實例之後，入口網站中就會出現通知。</span><span class="sxs-lookup"><span data-stu-id="d68b1-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="d68b1-229">按一下通知以探索新的服務實例。</span><span class="sxs-lookup"><span data-stu-id="d68b1-229">Click on the notification to explore your new Service instance.</span></span> 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="d68b1-231">按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。</span><span class="sxs-lookup"><span data-stu-id="d68b1-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="d68b1-232">您將會進入新的 Azure 服務實例。</span><span class="sxs-lookup"><span data-stu-id="d68b1-232">You will be taken to your new Azure Service instance.</span></span> 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="d68b1-234">此時您必須設定稱為 **Direct Line** 的功能，讓您的用戶端應用程式能夠與此 Bot 服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d68b1-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="d68b1-235">按一下 [ **頻道**]，然後在 [ **新增精選頻道** ] 區段中，按一下 [ **設定 Direct Line 頻道**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="d68b1-237">在此頁面中，您會找到可讓用戶端應用程式使用 bot 進行驗證的 **秘密金鑰** 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="d68b1-238">按一下 [ **顯示** ] 按鈕並複製其中一個所顯示的按鍵，因為您稍後會在專案中使用。</span><span class="sxs-lookup"><span data-stu-id="d68b1-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="d68b1-240">第3章-將 Bot 發佈至 Azure Web 應用程式 Bot 服務</span><span class="sxs-lookup"><span data-stu-id="d68b1-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="d68b1-241">現在您的服務已準備就緒，您必須將先前建立的 Bot 程式碼發佈至新建立的 Web 應用程式 Bot 服務。</span><span class="sxs-lookup"><span data-stu-id="d68b1-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="d68b1-242">您必須在每次對 Bot 解決方案/程式碼進行變更時，將 Bot 發佈至 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="d68b1-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="d68b1-243">返回您先前建立的 Visual Studio 解決方案。</span><span class="sxs-lookup"><span data-stu-id="d68b1-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="d68b1-244">以滑鼠右鍵按一下 **MyBot** 專案，在 **方案總管** 中，按一下 [ **發行**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![將 Bot 發佈至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="d68b1-246">在 [ *挑選發行目標* ] 頁面上，按一下 [ **App Service**]，然後 **選取 [現有** 的]，最後按一下 [ **建立設定檔** ] (您可能需要按一下 [ *發佈* ] 按鈕旁的下拉式箭號（如果沒有顯示) ）。</span><span class="sxs-lookup"><span data-stu-id="d68b1-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![將 Bot 發佈至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="d68b1-248">如果您尚未登入您的 Microsoft 帳戶，您必須在此進行。</span><span class="sxs-lookup"><span data-stu-id="d68b1-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="d68b1-249">在 [**發佈**] 頁面上，您將會發現必須設定用於 *Web 應用程式 Bot* 服務建立的相同 **訂** 用帳戶。</span><span class="sxs-lookup"><span data-stu-id="d68b1-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="d68b1-250">然後，將 **View** 設定為 **資源群組** ，然後在下拉式資料夾結構中，選取您先前建立的 **資源群組** 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="d68b1-251">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d68b1-251">Click **OK**.</span></span> 

    ![將 Bot 發佈至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="d68b1-253">現在按一下 [ **發佈** ] 按鈕，並等候 Bot 發佈 (可能需要幾分鐘的時間) 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![將 Bot 發佈至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="d68b1-255">第4章-設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="d68b1-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="d68b1-256">以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。</span><span class="sxs-lookup"><span data-stu-id="d68b1-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="d68b1-257">開啟 *Unity* ，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-257">Open *Unity* and click **New**.</span></span> 

    ![設定 Unity 專案](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="d68b1-259">您現在將需要提供 Unity 專案名稱。</span><span class="sxs-lookup"><span data-stu-id="d68b1-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="d68b1-260">插入 **HoloLens Bot**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-260">Insert **HoloLens Bot**.</span></span> <span data-ttu-id="d68b1-261">請確定專案範本已設定為 **3d**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="d68b1-262">將 **位置** 設定為適合您 (記住，較接近根目錄的) 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="d68b1-263">然後，按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-263">Then, click **Create project**.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="d68b1-265">在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="d68b1-266">移至 [ **編輯] > 喜好** 設定，然後在新視窗中，流覽至 [ **外部工具**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="d68b1-267">將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="d68b1-268">關閉 [ **喜好** 設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="d68b1-268">Close the **Preferences** window.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="d68b1-270">接下來，移至 [檔案 **> 組建設定** ]，選取 [ **通用 Windows 平臺**]，然後按一下 [ **切換平臺** ] 按鈕以套用您的選取專案。</span><span class="sxs-lookup"><span data-stu-id="d68b1-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![設定 Unity 專案](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="d68b1-272">在檔案中仍 **> 組建設定** ，並確定：</span><span class="sxs-lookup"><span data-stu-id="d68b1-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="d68b1-273">**目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="d68b1-273">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="d68b1-274">針對沉浸式耳機，將 **目標裝置** 設為 *任何裝置*。</span><span class="sxs-lookup"><span data-stu-id="d68b1-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="d68b1-275">**組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="d68b1-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="d68b1-276">**SDK** 已設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="d68b1-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="d68b1-277">**Visual Studio 版本** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="d68b1-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="d68b1-278">**組建並執行** 設定為 **本機電腦**</span><span class="sxs-lookup"><span data-stu-id="d68b1-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="d68b1-279">儲存場景，並將其新增至組建。</span><span class="sxs-lookup"><span data-stu-id="d68b1-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="d68b1-280">若要這麼做，請選取 [ **新增開啟的場景**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="d68b1-281">[儲存] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d68b1-281">A save window will appear.</span></span>
        
            ![設定 Unity 專案](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="d68b1-283">為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![設定 Unity 專案](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="d68b1-285">開啟新建立的 **場景** 資料夾，然後在 [ *檔案名*：文字] 欄位中輸入 **BotScene**，然後按一下 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="d68b1-287">[ **組建設定**] 中的其餘設定，現在應該保持為預設值。</span><span class="sxs-lookup"><span data-stu-id="d68b1-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="d68b1-288">在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。</span><span class="sxs-lookup"><span data-stu-id="d68b1-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![設定 Unity 專案](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="d68b1-290">在此面板中，需要驗證幾個設定：</span><span class="sxs-lookup"><span data-stu-id="d68b1-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="d68b1-291">在 [ **其他設定** ] 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="d68b1-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="d68b1-292">**腳本執行階段版本** 應該是 **實驗 (NET 4.6 對等)**;變更此項將需要重新開機編輯器。</span><span class="sxs-lookup"><span data-stu-id="d68b1-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="d68b1-293">**腳本後端** 應該是 **.net**</span><span class="sxs-lookup"><span data-stu-id="d68b1-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="d68b1-294">**API 相容性層級** 應為 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="d68b1-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="d68b1-296">在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：</span><span class="sxs-lookup"><span data-stu-id="d68b1-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="d68b1-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="d68b1-297">**InternetClient**</span></span>
        - <span data-ttu-id="d68b1-298">**麥克風**</span><span class="sxs-lookup"><span data-stu-id="d68b1-298">**Microphone**</span></span>

            ![設定 Unity 專案](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="d68b1-300">在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![設定 Unity 專案](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="d68b1-302">回到 *組建設定*： _Unity c #_ 專案不再呈現灰色;勾選此方塊旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d68b1-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="d68b1-303">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="d68b1-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="d68b1-304">將場景和專案儲存 (檔 **> 儲存場景/檔案 > 儲存專案**) 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="d68b1-305">第5章-攝影機設定</span><span class="sxs-lookup"><span data-stu-id="d68b1-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d68b1-306">如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意下載此 [Azure-MR-312-unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)，將其匯入到您的專案中做為 [**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第7章](#chapter-8--create-the-botobjects-class)。</span><span class="sxs-lookup"><span data-stu-id="d68b1-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-8--create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="d68b1-307">在 [階層] *面板* 中，選取 [ **主要相機**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="d68b1-308">一旦選取之後，您就可以在 [偵測 *器] 面板* 中看到 **主要攝影機** 的所有元件。</span><span class="sxs-lookup"><span data-stu-id="d68b1-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="d68b1-309">**攝影機物件** 必須命名為 **主要攝影機** (注意拼寫) </span><span class="sxs-lookup"><span data-stu-id="d68b1-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="d68b1-310">主要攝影機 **標記** 必須設定為 **MainCamera** (注意拼寫) </span><span class="sxs-lookup"><span data-stu-id="d68b1-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="d68b1-311">請確定 **轉換位置** 設定為 **0、0、0**</span><span class="sxs-lookup"><span data-stu-id="d68b1-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="d68b1-312">將 [ **清除] 旗標** 設定為 [ **純色**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="d68b1-313">將相機元件的 **背景** 色彩設定為 **黑色、Alpha 0 (Hex 碼： #00000000)**</span><span class="sxs-lookup"><span data-stu-id="d68b1-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![攝影機設定](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="d68b1-315">第6章–匯入 Newtonsoft 程式庫</span><span class="sxs-lookup"><span data-stu-id="d68b1-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="d68b1-316">為了協助您還原序列化和序列化接收和傳送至 Bot 服務的物件，您需要下載 **Newtonsoft** 程式庫。</span><span class="sxs-lookup"><span data-stu-id="d68b1-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="d68b1-317">您會在 [這裡找到已使用正確 Unity 資料夾結構組織的相容版本](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="d68b1-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="d68b1-318">若要將 Newtonsoft 程式庫匯入您的專案，請使用本課程隨附的 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="d68b1-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="d68b1-319">使用 [  **資產** 匯  >  **入封裝**  >  **自訂套件**] 功能表選項，將 unitypackage 新增至 Unity。</span><span class="sxs-lookup"><span data-stu-id="d68b1-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![匯入 Newtonsoft 程式庫](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="d68b1-321">在彈出的 [匯 **入 Unity 套件** ] 方塊中，確定已選取 [ (] 下的所有專案，並包含) **外掛程式** 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![匯入 Newtonsoft 程式庫](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="d68b1-323">按一下 [匯 **入** ] 按鈕，將專案新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="d68b1-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="d68b1-324">移至專案視圖中 [**外掛程式**] 下的 [ **Newtonsoft** ] 資料夾，然後選取 Newtonsoft 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="d68b1-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="d68b1-325">選取 Newtonsoft 外掛程式之後，請確定已 **取消** 選取 **任何平臺**，然後確定也未 **選取**[ **WSAPlayer** ]，然後 **按一下 [** 套用]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="d68b1-326">這只是為了確認檔案已正確設定。</span><span class="sxs-lookup"><span data-stu-id="d68b1-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="d68b1-327">標記這些外掛程式會將它們設定為只在 Unity 編輯器中使用。</span><span class="sxs-lookup"><span data-stu-id="d68b1-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="d68b1-328">在 [WSA] 資料夾中有一組不同的集合，會在從 Unity 匯出專案之後使用。</span><span class="sxs-lookup"><span data-stu-id="d68b1-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="d68b1-329">接下來，您需要在 **Newtonsoft** 資料夾內開啟 [ **WSA** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d68b1-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="d68b1-330">您會看到您剛剛設定的相同檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="d68b1-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="d68b1-331">選取檔案，然後在偵測器中，確定</span><span class="sxs-lookup"><span data-stu-id="d68b1-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="d68b1-332">**未核** 取 **任何平臺**</span><span class="sxs-lookup"><span data-stu-id="d68b1-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="d68b1-333">**只\*\*\*\*檢查** **WSAPlayer**</span><span class="sxs-lookup"><span data-stu-id="d68b1-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="d68b1-334">不 **檢查\*\*\*\*進程**</span><span class="sxs-lookup"><span data-stu-id="d68b1-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="d68b1-335">第7章-建立 BotTag</span><span class="sxs-lookup"><span data-stu-id="d68b1-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="d68b1-336">建立名為 **BotTag** 的新 **標記** 物件。</span><span class="sxs-lookup"><span data-stu-id="d68b1-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="d68b1-337">選取場景中的主要攝影機。</span><span class="sxs-lookup"><span data-stu-id="d68b1-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="d68b1-338">按一下 [檢查] 面板中的 [標記] 下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="d68b1-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="d68b1-339">按一下 [ **新增標記**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-339">Click on **Add Tag**.</span></span>

    ![攝影機設定](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="d68b1-341">按一下 **+** 符號。</span><span class="sxs-lookup"><span data-stu-id="d68b1-341">Click on the **+** symbol.</span></span> <span data-ttu-id="d68b1-342">將新 **標記** 命名為 **BotTag**， *儲存*。</span><span class="sxs-lookup"><span data-stu-id="d68b1-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![攝影機設定](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="d68b1-344">**請勿** 將 **BotTag** 套用至主要攝影機。</span><span class="sxs-lookup"><span data-stu-id="d68b1-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="d68b1-345">如果您不小心這麼做，請務必將主要攝影機標記變更回 *MainCamera*。</span><span class="sxs-lookup"><span data-stu-id="d68b1-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="d68b1-346">第8章-建立 BotObjects 類別</span><span class="sxs-lookup"><span data-stu-id="d68b1-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="d68b1-347">您需要建立的第一個腳本是 **BotObjects** 類別，這是一個建立的空類別，可讓一系列的其他類別物件儲存在相同的腳本內，並由場景中的其他腳本存取。</span><span class="sxs-lookup"><span data-stu-id="d68b1-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="d68b1-348">建立此類別純粹是架構選擇，這些物件可以改為裝載在您稍後將在本課程中建立的 Bot 腳本中。</span><span class="sxs-lookup"><span data-stu-id="d68b1-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="d68b1-349">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="d68b1-349">To create this class:</span></span> 

1.  <span data-ttu-id="d68b1-350">在 [ *專案] 面板* 中按一下滑鼠右鍵，然後 **建立 > 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="d68b1-351">將資料夾命名為 **腳本**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-351">Name the folder **Scripts**.</span></span> 

    ![建立腳本資料夾。](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="d68b1-353">按兩下 [ **腳本** ] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="d68b1-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="d68b1-354">然後，在該資料夾中，以滑鼠右鍵按一下，然後選取 [ **建立 > c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="d68b1-355">將腳本命名為 **BotObjects**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="d68b1-356">按兩下新的 **BotObjects** 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="d68b1-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="d68b1-357">刪除腳本的內容，並將它取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d68b1-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="d68b1-358">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="d68b1-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="d68b1-359">第9章–建立 GazeInput 類別</span><span class="sxs-lookup"><span data-stu-id="d68b1-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="d68b1-360">您即將建立的下一個類別是 **GazeInput** 類別。</span><span class="sxs-lookup"><span data-stu-id="d68b1-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="d68b1-361">此類別負責：</span><span class="sxs-lookup"><span data-stu-id="d68b1-361">This class is responsible for:</span></span>

- <span data-ttu-id="d68b1-362">建立將表示播放程式 *注視* 的游標。</span><span class="sxs-lookup"><span data-stu-id="d68b1-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="d68b1-363">偵測播放程式注視的物件，並保存偵測到之物件的參考。</span><span class="sxs-lookup"><span data-stu-id="d68b1-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="d68b1-364">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="d68b1-364">To create this class:</span></span> 

1.  <span data-ttu-id="d68b1-365">移至您先前建立的 **腳本** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d68b1-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="d68b1-366">以滑鼠右鍵按一下資料夾內的， **建立 > c # 腳本**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="d68b1-367">呼叫腳本 **GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="d68b1-368">按兩下新的 **GazeInput** 腳本，以 **Visual Studio** 開啟。</span><span class="sxs-lookup"><span data-stu-id="d68b1-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="d68b1-369">在類別名稱的頂端插入下面這行：</span><span class="sxs-lookup"><span data-stu-id="d68b1-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="d68b1-370">然後，在 **GazeInput** 類別內，于 **Start ()** 方法的上方新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="d68b1-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="d68b1-371">應新增 **開始 ()** 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d68b1-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="d68b1-372">當類別初始化時，就會呼叫：</span><span class="sxs-lookup"><span data-stu-id="d68b1-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="d68b1-373">執行將會具現化並設定注視游標的方法：</span><span class="sxs-lookup"><span data-stu-id="d68b1-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="d68b1-374">執行會從主要攝影機設定 Raycast 的方法，並追蹤目前焦點的物件。</span><span class="sxs-lookup"><span data-stu-id="d68b1-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="d68b1-375">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="d68b1-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="d68b1-376">第10章-建立 Bot 類別</span><span class="sxs-lookup"><span data-stu-id="d68b1-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="d68b1-377">您要建立的腳本現在稱為 **Bot**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="d68b1-378">這是您應用程式的核心類別，它會儲存：</span><span class="sxs-lookup"><span data-stu-id="d68b1-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="d68b1-379">您的 Web 應用程式 Bot 認證</span><span class="sxs-lookup"><span data-stu-id="d68b1-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="d68b1-380">收集使用者心聲命令的方法</span><span class="sxs-lookup"><span data-stu-id="d68b1-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="d68b1-381">使用您的 Web 應用程式 Bot 起始交談所需的方法</span><span class="sxs-lookup"><span data-stu-id="d68b1-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="d68b1-382">將訊息傳送至 Web 應用程式 Bot 所需的方法</span><span class="sxs-lookup"><span data-stu-id="d68b1-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="d68b1-383">為了將訊息傳送至 Bot 服務， **SendMessageToBot ()** 協同程式會建立活動，此活動是由使用者所傳送的資料 Bot Framework 所辨識的物件。</span><span class="sxs-lookup"><span data-stu-id="d68b1-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="d68b1-384">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="d68b1-384">To create this class:</span></span> 

1. <span data-ttu-id="d68b1-385">按兩下 [ **腳本** ] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="d68b1-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="d68b1-386">在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="d68b1-387">為腳本 **Bot** 命名。</span><span class="sxs-lookup"><span data-stu-id="d68b1-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="d68b1-388">按兩下新的腳本，以 Visual Studio 開啟。</span><span class="sxs-lookup"><span data-stu-id="d68b1-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="d68b1-389">在 **Bot** 類別的頂端，將命名空間更新為與下列相同：</span><span class="sxs-lookup"><span data-stu-id="d68b1-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="d68b1-390">在 **Bot** 類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="d68b1-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="d68b1-391">請確定您將 **Bot 秘密金鑰** 插入 **botSecret** 變數中。</span><span class="sxs-lookup"><span data-stu-id="d68b1-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="d68b1-392">您將在本課程的開頭注明您的 **Bot 秘密金鑰**，第 **[2 章](#chapter-2---create-the-azure-bot-service)步驟 10**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="d68b1-393">現在需要新增 **喚醒 ()** 的程式碼，並 **開始 ()** 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="d68b1-394">當語音捕捉開始和結束時，新增兩個由語音程式庫呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="d68b1-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="d68b1-395">當使用者停止說話時， *DictationRecognizer* 會自動停止捕捉使用者心聲。</span><span class="sxs-lookup"><span data-stu-id="d68b1-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="d68b1-396">下列處理常式會收集使用者語音輸入的結果，並呼叫負責將訊息傳送至 Web 應用程式 Bot 服務的協同程式。</span><span class="sxs-lookup"><span data-stu-id="d68b1-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="d68b1-397">呼叫下列協同程式來開始與 Bot 的對話。</span><span class="sxs-lookup"><span data-stu-id="d68b1-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="d68b1-398">您將會注意到在對話呼叫完成後，它會藉由傳遞一系列的參數來呼叫 **SendMessageToCoroutine ()** ，這些參數會將活動設定為以空白訊息的形式傳送至 Bot 服務。</span><span class="sxs-lookup"><span data-stu-id="d68b1-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="d68b1-399">這麼做是為了提示 Bot 服務起始對話。</span><span class="sxs-lookup"><span data-stu-id="d68b1-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="d68b1-400">呼叫下列協同程式來建立要傳送至 Bot 服務的活動。</span><span class="sxs-lookup"><span data-stu-id="d68b1-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="d68b1-401">在將活動傳送至 Bot 服務之後，會呼叫下列協同程式來要求回應。</span><span class="sxs-lookup"><span data-stu-id="d68b1-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="d68b1-402">要加入這個類別的最後一個方法，必須在場景中顯示訊息：</span><span class="sxs-lookup"><span data-stu-id="d68b1-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="d68b1-403">您可能會在 Unity 編輯器主控台中看到錯誤，缺少 **SceneOrganiser** 類別。</span><span class="sxs-lookup"><span data-stu-id="d68b1-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="d68b1-404">請忽略此訊息，因為您稍後會在本教學課程中建立此類別。</span><span class="sxs-lookup"><span data-stu-id="d68b1-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="d68b1-405">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="d68b1-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="d68b1-406">第11章-建立互動類別</span><span class="sxs-lookup"><span data-stu-id="d68b1-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="d68b1-407">您即將建立的類別稱為 **互動**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="d68b1-408">此類別用來偵測來自使用者的 HoloLens 點擊輸入。</span><span class="sxs-lookup"><span data-stu-id="d68b1-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="d68b1-409">如果使用者在查看場景中的 *bot* 物件時點擊，且 bot 已準備好接聽語音輸入，則 bot 物件會將色彩變更為 **紅色** ，並開始接聽語音輸入。</span><span class="sxs-lookup"><span data-stu-id="d68b1-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="d68b1-410">這個類別繼承自 **GazeInput** 類別，因此可以從該類別參考 **開始 ()** 方法和變數，以使用 **base** 表示。</span><span class="sxs-lookup"><span data-stu-id="d68b1-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="d68b1-411">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="d68b1-411">To create this class:</span></span>

1.  <span data-ttu-id="d68b1-412">按兩下 [ **腳本** ] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="d68b1-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="d68b1-413">在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="d68b1-414">命名腳本的 **互動**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="d68b1-415">按兩下新的腳本，以 Visual Studio 開啟。</span><span class="sxs-lookup"><span data-stu-id="d68b1-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="d68b1-416">在 **互動** 類別的頂端，將命名空間和類別繼承更新為與下列相同：</span><span class="sxs-lookup"><span data-stu-id="d68b1-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="d68b1-417">在 [ **互動** ] 類別內新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="d68b1-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="d68b1-418">然後，新增 **Start ()** 方法：</span><span class="sxs-lookup"><span data-stu-id="d68b1-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="d68b1-419">新增當使用者在 HoloLens 攝影機前方執行點按手勢時，將觸發的處理常式</span><span class="sxs-lookup"><span data-stu-id="d68b1-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="d68b1-420">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="d68b1-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="d68b1-421">第12章-建立 SceneOrganiser 類別</span><span class="sxs-lookup"><span data-stu-id="d68b1-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="d68b1-422">此實驗室所需的最後一個類別稱為 **SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="d68b1-423">此類別會以程式設計方式設定場景，方法是將元件和腳本新增至主要相機，並在場景中建立適當的物件。</span><span class="sxs-lookup"><span data-stu-id="d68b1-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="d68b1-424">若要建立此類別：</span><span class="sxs-lookup"><span data-stu-id="d68b1-424">To create this class:</span></span>

1.  <span data-ttu-id="d68b1-425">按兩下 [ **腳本** ] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="d68b1-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="d68b1-426">在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="d68b1-427">將腳本命名為 **SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="d68b1-428">按兩下新的腳本，以 Visual Studio 開啟。</span><span class="sxs-lookup"><span data-stu-id="d68b1-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="d68b1-429">在 **SceneOrganiser** 類別中，新增下列變數：</span><span class="sxs-lookup"><span data-stu-id="d68b1-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="d68b1-430">然後，新增 **喚醒的 ()** 並 **啟動 ()** 方法：</span><span class="sxs-lookup"><span data-stu-id="d68b1-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="d68b1-431">新增下列方法，負責在場景中建立 Bot 物件，並設定參數和元件：</span><span class="sxs-lookup"><span data-stu-id="d68b1-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="d68b1-432">新增下列方法，負責在場景中建立 UI 物件，代表來自 Bot 的回應：</span><span class="sxs-lookup"><span data-stu-id="d68b1-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="d68b1-433">返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。</span><span class="sxs-lookup"><span data-stu-id="d68b1-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="d68b1-434">在 Unity 編輯器中，將 [腳本] 資料夾中的 **SceneOrganiser** 腳本拖曳至主要攝影機。</span><span class="sxs-lookup"><span data-stu-id="d68b1-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="d68b1-435">場景 Organiser 元件現在應該會出現在主要攝影機物件上，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d68b1-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="d68b1-437">第13章-建立之前</span><span class="sxs-lookup"><span data-stu-id="d68b1-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="d68b1-438">若要執行應用程式的完整測試，您必須將它側載到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d68b1-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="d68b1-439">在執行之前，請確定：</span><span class="sxs-lookup"><span data-stu-id="d68b1-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="d68b1-440">[**第4章**](#chapter-4--set-up-the-unity-project)中所述的所有設定都已正確設定。</span><span class="sxs-lookup"><span data-stu-id="d68b1-440">All the settings mentioned in the [**Chapter 4**](#chapter-4--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="d68b1-441">腳本 **SceneOrganiser** 會附加至 **主要攝影機** 物件。</span><span class="sxs-lookup"><span data-stu-id="d68b1-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="d68b1-442">在 **Bot** 類別中，請確定您已將 **Bot 秘密金鑰** 插入 **botSecret** 變數中。</span><span class="sxs-lookup"><span data-stu-id="d68b1-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="d68b1-443">第14章–組建並側載至 HoloLens</span><span class="sxs-lookup"><span data-stu-id="d68b1-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="d68b1-444">此專案的 Unity 區段所需的所有專案現在都已完成，因此您可以從 Unity 建立它。</span><span class="sxs-lookup"><span data-stu-id="d68b1-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="d68b1-445">流覽至 [ **組建設定**]、[檔案 **> 組建設定 ...**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="d68b1-446">從 [ **組建設定** ] 視窗中，按一下 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-446">From the **Build Settings** window, click **Build**.</span></span>

    ![從 Unity 建立應用程式](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="d68b1-448">如果尚未這麼做，請勾選 **Unity c # 專案**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="d68b1-449">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-449">Click **Build**.</span></span> <span data-ttu-id="d68b1-450">Unity 將會啟動一個 **檔案總管** 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d68b1-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="d68b1-451">立即建立該資料夾，並命名為 **應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="d68b1-452">然後選取 [ **應用程式** ] 資料夾，然後按一下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="d68b1-453">Unity 將開始將您的專案建立到 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d68b1-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="d68b1-454">Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。</span><span class="sxs-lookup"><span data-stu-id="d68b1-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="d68b1-455">第15章-部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="d68b1-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="d68b1-456">若要在 HoloLens 上部署：</span><span class="sxs-lookup"><span data-stu-id="d68b1-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="d68b1-457">您將需要 HoloLens (的 IP 位址，才能進行遠端部署) ，並確保 HoloLens 處於 **開發人員模式**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="d68b1-458">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="d68b1-458">To do this:</span></span>

    1. <span data-ttu-id="d68b1-459">在設置 HoloLens 的同時，開啟 **設定**。</span><span class="sxs-lookup"><span data-stu-id="d68b1-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="d68b1-460">前往 **Network & Internet > Wi-Fi > Advanced Options**</span><span class="sxs-lookup"><span data-stu-id="d68b1-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="d68b1-461">記下 **IPv4** 位址。</span><span class="sxs-lookup"><span data-stu-id="d68b1-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="d68b1-462">接下來，流覽回到 [ **設定**]，然後 **更新開發人員 & 的安全性 >**</span><span class="sxs-lookup"><span data-stu-id="d68b1-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="d68b1-463">設定 [開發人員模式]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="d68b1-464">流覽至您的新 Unity 組建 (**應用程式** 資料夾) ，然後以 **Visual Studio** 開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="d68b1-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="d68b1-465">在 [ **方案** 設定] 中選取 [ **Debug**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="d68b1-466">在 **解決方案平臺** 中，選取 [ **x86**]、[ **遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="d68b1-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![從 Visual Studio 部署方案。](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="d68b1-468">移至 [ **組建] 功能表** ，然後按一下 [ **部署方案**]，將應用程式側載至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d68b1-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="d68b1-469">您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中，準備好可供啟動！</span><span class="sxs-lookup"><span data-stu-id="d68b1-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="d68b1-470">若要部署到沉浸式耳機，請將 **解決方案平臺\*\*\*\*設定為 [** *本機電腦*]，並將 [設定] 設定為 [以 *x86* 作為 **平臺**] 來進行 *Debug*。</span><span class="sxs-lookup"><span data-stu-id="d68b1-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="d68b1-471">然後使用 [ **組建] 功能表** 選取 [ *部署方案*]，部署到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="d68b1-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="d68b1-472">第16章–在 HoloLens 上使用應用程式</span><span class="sxs-lookup"><span data-stu-id="d68b1-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="d68b1-473">當您啟動應用程式之後，您會在前方看到 Bot 成為藍色球體。</span><span class="sxs-lookup"><span data-stu-id="d68b1-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="d68b1-474">當您在球體上撥雲見日時，請使用點一下 **手勢** 來起始對話。</span><span class="sxs-lookup"><span data-stu-id="d68b1-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="d68b1-475">等候對話開始 (當) 發生訊息時，UI 會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="d68b1-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="d68b1-476">當您收到來自 Bot 的簡介訊息之後，請在 Bot 上再次點一下，讓它變成紅色並開始聆聽您的聲音。</span><span class="sxs-lookup"><span data-stu-id="d68b1-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="d68b1-477">當您停止交談之後，您的應用程式會將您的訊息傳送至 Bot，且您會立即收到將顯示在 UI 中的回應。</span><span class="sxs-lookup"><span data-stu-id="d68b1-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="d68b1-478">重複此程式，將更多訊息傳送至您的 Bot (您必須在每次想要 sen 訊息) 時按一下。</span><span class="sxs-lookup"><span data-stu-id="d68b1-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="d68b1-479">此交談會示範 Bot 如何保留 (您的名稱) 的資訊，同時也提供已知的資訊 (例如已儲存) 的專案。</span><span class="sxs-lookup"><span data-stu-id="d68b1-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="d68b1-480">要求 Bot 的一些問題：</span><span class="sxs-lookup"><span data-stu-id="d68b1-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="d68b1-481">您已完成的 Web 應用程式 Bot (v4) 應用程式</span><span class="sxs-lookup"><span data-stu-id="d68b1-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="d68b1-482">恭喜，您建立了一個利用 Azure Web 應用程式 Bot Microsoft Bot Framework v4 的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="d68b1-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![最終產品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="d68b1-484">額外練習</span><span class="sxs-lookup"><span data-stu-id="d68b1-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="d68b1-485">練習1</span><span class="sxs-lookup"><span data-stu-id="d68b1-485">Exercise 1</span></span>

<span data-ttu-id="d68b1-486">此實驗室中的交談結構非常基本。</span><span class="sxs-lookup"><span data-stu-id="d68b1-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="d68b1-487">使用 Microsoft LUIS 為您的 bot 提供自然語言理解功能。</span><span class="sxs-lookup"><span data-stu-id="d68b1-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="d68b1-488">練習2</span><span class="sxs-lookup"><span data-stu-id="d68b1-488">Exercise 2</span></span>

<span data-ttu-id="d68b1-489">此範例不包含終止交談並重新啟動新的交談。</span><span class="sxs-lookup"><span data-stu-id="d68b1-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="d68b1-490">若要讓 Bot 功能完成，請嘗試將結束的情況執行到交談。</span><span class="sxs-lookup"><span data-stu-id="d68b1-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>