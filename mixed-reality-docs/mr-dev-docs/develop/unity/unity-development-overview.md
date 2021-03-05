---
title: 適用於 HoloLens 的 Unity 開發
description: 透過我們策劃的檢查點旅程，開始在 Unity 和 HoloLens 中建置混合實境應用程式。
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合實境, 開發, 開始使用, 新專案, 移植, 功能, 相機, 模擬, 模擬, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 什麼是虛擬實境, 什麼是擴增實境, MRTK, 混合實境工具組, 空間對應, 語音輸入, 定位相機, 模擬器, Azure, 教學課程
ms.openlocfilehash: ed0f27822ab83baa2c1de6575067bdbd6b00a5e6
ms.sourcegitcommit: 5694cc472bde67c940204ebe6671b0598501e62a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2021
ms.locfileid: "102126611"
---
# <a name="unity-development-for-hololens"></a><span data-ttu-id="8500e-104">適用於 HoloLens 的 Unity 開發</span><span class="sxs-lookup"><span data-stu-id="8500e-104">Unity development for HoloLens</span></span>

![Unity 橫幅標誌](../images/unity_logo_banner.png)

<span data-ttu-id="8500e-106">要在 [Unity](https://unity.com) 中建置 HoloLens [混合實境應用程式](../../design/app-views.md)，使用混合實境工具組是最快速的途徑。</span><span class="sxs-lookup"><span data-stu-id="8500e-106">The fastest path to building a HoloLens [mixed reality app](../../design/app-views.md) in [Unity](https://unity.com) is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="8500e-107">如果您是首次接觸 Unity，建議您先探索 Unity 學習平台上的入門級[教學課程](https://unity3d.com/learn/tutorials)，再繼續操作。</span><span class="sxs-lookup"><span data-stu-id="8500e-107">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="8500e-108">您也可以造訪內容豐富的[資產存放區](https://assetstore.unity.com)和 [Unity 混合實境論壇](https://forum.unity3d.com/forums/hololens.102/)，與建置混合實境應用程式的線上社群交流。</span><span class="sxs-lookup"><span data-stu-id="8500e-108">It's also a good idea to visit the comprehensive [Asset Store](https://assetstore.unity.com) and the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="8500e-109">您絕對想不到在這裡會發現哪些絕佳的資產或解決方案。</span><span class="sxs-lookup"><span data-stu-id="8500e-109">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="8500e-110">當您準備好開始使用 MRTK 時，請前往以下開發檢查點！</span><span class="sxs-lookup"><span data-stu-id="8500e-110">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8500e-111">如果您想要將現有的 Unity 專案導入 HoloLens 2 中，請參閱我們的 **[移植指南](../porting-apps/porting-overview.md)** 。</span><span class="sxs-lookup"><span data-stu-id="8500e-111">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to HoloLens 2.</span></span> <span data-ttu-id="8500e-112">我們針對使用 HTK、MRTK v1 或 SteamVR 的專案提供了指南。</span><span class="sxs-lookup"><span data-stu-id="8500e-112">We have guides for projects that are using HTK, MRTK v1, or SteamVR.</span></span>

## <a name="development-checkpoints"></a><span data-ttu-id="8500e-113">開發檢查點</span><span class="sxs-lookup"><span data-stu-id="8500e-113">Development checkpoints</span></span>

<span data-ttu-id="8500e-114">使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。</span><span class="sxs-lookup"><span data-stu-id="8500e-114">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> <span data-ttu-id="8500e-115">如果您尚未探索 [設計全像投影範例應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，建議您下載並使用，以熟悉混合實境 UX 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="8500e-115">If you haven't already explored the [Designing Holograms sample application](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), we recommend downloading and using it to familiarize yourself with the basics of Mixed Reality UX.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="8500e-116">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="8500e-116">1. Getting started</span></span>

<span data-ttu-id="8500e-117">在 Unity 中開發最簡單的方式，就是使用混合實境工具組。</span><span class="sxs-lookup"><span data-stu-id="8500e-117">The easiest way to develop in Unity is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="8500e-118">MRTK 可協助您自動設定混合實境的專案，並提供一組功能協助您加速開發流程。</span><span class="sxs-lookup"><span data-stu-id="8500e-118">MRTK will help you automatically setup a project for Mixed Reality and provide a set of features to accelerate your development process.</span></span> <span data-ttu-id="8500e-119">閱讀本節的內容後，您大致上就已了解混合實境工具組、針對混合實境應用程式正確設定的開發環境，以及您自行建置且可在 Unity 中運作的 MRTK 專案。</span><span class="sxs-lookup"><span data-stu-id="8500e-119">By the end of this section, you'll have a basic understanding of the Mixed Reality Toolkit, a properly configured development environment for Mixed Reality apps, and a working MRTK project in Unity that you built yourself.</span></span>

|  <span data-ttu-id="8500e-120">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="8500e-120">Checkpoint</span></span>  |  <span data-ttu-id="8500e-121">結果</span><span class="sxs-lookup"><span data-stu-id="8500e-121">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="8500e-122">什麼是 MRTK？</span><span class="sxs-lookup"><span data-stu-id="8500e-122">What is MRTK?</span></span>](mrtk-getting-started.md) | <span data-ttu-id="8500e-123">熟悉混合實境工具組及其提供的功能，開始您的旅程</span><span class="sxs-lookup"><span data-stu-id="8500e-123">Begin your journey by getting acquainted with the Mixed Reality Toolkit and what it has to offer</span></span> |
| [<span data-ttu-id="8500e-124">安裝最新工具</span><span class="sxs-lookup"><span data-stu-id="8500e-124">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="8500e-125">下載並安裝最新的 Unity 套件，並設定您的混合實境專案</span><span class="sxs-lookup"><span data-stu-id="8500e-125">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="8500e-126">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="8500e-126">HoloLens 2 tutorial series</span></span>](tutorials/mr-learning-base-01.md) | <span data-ttu-id="8500e-127">進入 HoloLens 2 硬體的入門級 MRTK 教學課程</span><span class="sxs-lookup"><span data-stu-id="8500e-127">Dive into beginner level MRTK tutorials for HoloLens 2 hardware</span></span> |
| <span data-ttu-id="8500e-128">**選擇性**[下載 Mixed Reality 功能工具](welcome-to-mr-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="8500e-128">**Optional** [Download the Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)</span></span> | <span data-ttu-id="8500e-129">新的開發人員工具，可用於探索、更新和新增混合現實功能套件至 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="8500e-129">A new developer tool for discovering, updating, and adding Mixed Reality feature packages to your Unity projects</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="8500e-130">如果您想要在未匯入混合實境工具組的情況下建立新的 Unity 專案，則您需要為 Windows Mixed Reality 手動變更一小組 Unity 設定。</span><span class="sxs-lookup"><span data-stu-id="8500e-130">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="8500e-131">這些設定分成兩個類別：每個專案和每個場景。</span><span class="sxs-lookup"><span data-stu-id="8500e-131">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="8500e-132">如需逐步程序，請參閱我們的[設定指南](configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="8500e-132">Take a look at our [configuration guide](configure-unity-project.md) for the step-by-step process.</span></span>

> [!NOTE]
> <span data-ttu-id="8500e-133">在您的專案中設定 MRTK V2 後，標準 Unity 遊戲物件 (例如相機) 會立即亮起，以提供坐姿級別體驗。</span><span class="sxs-lookup"><span data-stu-id="8500e-133">Once you've setup MRTK V2 in your project, standard Unity game objects like the camera will light up immediately for a seated-scale experience.</span></span> <span data-ttu-id="8500e-134">您可以在[座標系統](coordinate-systems-in-unity.md)頁面上找到變更應用程式體驗級別的指示。</span><span class="sxs-lookup"><span data-stu-id="8500e-134">You can find instructions on changing the experience scale of your application on the [coordinate systems](coordinate-systems-in-unity.md) page.</span></span>

### <a name="2-core-building-blocks"></a><span data-ttu-id="8500e-135">2.核心基本要素</span><span class="sxs-lookup"><span data-stu-id="8500e-135">2. Core building blocks</span></span>

<span data-ttu-id="8500e-136">混合實境應用程式的所有核心建置組塊都會以與其他 Unity API 一致的方式公開。</span><span class="sxs-lookup"><span data-stu-id="8500e-136">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="8500e-137">這些建置組塊是透過混合實境工具組提供的獨立功能。</span><span class="sxs-lookup"><span data-stu-id="8500e-137">These building blocks are available as standalone features and through the Mixed Reality Toolkit.</span></span> <span data-ttu-id="8500e-138">您目前可能不需用到所有功能，但建議您及早探索。</span><span class="sxs-lookup"><span data-stu-id="8500e-138">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="8500e-139">深入探討下列核心建置組塊後，您將了解如何讓包含多樣化功能的工具箱自行或透過 MRTK 整合到混合實境專案中。</span><span class="sxs-lookup"><span data-stu-id="8500e-139">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a Mixed Reality project by themselves or through MRTK.</span></span>

[!INCLUDE[](../includes/unity-building-blocks.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="8500e-140">3.進階功能</span><span class="sxs-lookup"><span data-stu-id="8500e-140">3. Advanced features</span></span>

<span data-ttu-id="8500e-141">在混合實境應用程式中各有作用的其他重要功能可透過 Unity API 來使用，不需要任何額外的封裝或設定。</span><span class="sxs-lookup"><span data-stu-id="8500e-141">Other key features that play a role in mixed reality applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="8500e-142">這些功能可以新增至 Unity 專案，且不一定需要先安裝 MRTK。</span><span class="sxs-lookup"><span data-stu-id="8500e-142">These features can be added to Unity projects with or without MRTK installed.</span></span> <span data-ttu-id="8500e-143">深入了解 Unity 提供的進階功能後，您將能夠建置更有深度的複雜混合實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="8500e-143">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex Mixed Reality apps.</span></span>

|  <span data-ttu-id="8500e-144">功能</span><span class="sxs-lookup"><span data-stu-id="8500e-144">Feature</span></span>  |  <span data-ttu-id="8500e-145">功能</span><span class="sxs-lookup"><span data-stu-id="8500e-145">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="8500e-146">共用體驗</span><span class="sxs-lookup"><span data-stu-id="8500e-146">Shared experiences</span></span>](shared-experiences-in-unity.md) | <span data-ttu-id="8500e-147">使用空間錨點共用，共同檢視空間中固定點上的相同全像投影，並與其互動</span><span class="sxs-lookup"><span data-stu-id="8500e-147">View and interact collectively with the same hologram at a fixed point in space using spatial anchor sharing</span></span> |
| [<span data-ttu-id="8500e-148">定位相機</span><span class="sxs-lookup"><span data-stu-id="8500e-148">Locatable camera</span></span>](locatable-camera-in-unity.md) | <span data-ttu-id="8500e-149">在您的混合實境應用程式中擷取相片和影片內容</span><span class="sxs-lookup"><span data-stu-id="8500e-149">Capture photos and video content in your Mixed Reality application</span></span> |
| [<span data-ttu-id="8500e-150">對焦點</span><span class="sxs-lookup"><span data-stu-id="8500e-150">Focus point</span></span>](focus-point-in-unity.md) | <span data-ttu-id="8500e-151">為 HoloLens 提供有關於如何對目前顯示的全像投影最有效地執行穩定性的提示</span><span class="sxs-lookup"><span data-stu-id="8500e-151">Provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed</span></span> |
| [<span data-ttu-id="8500e-152">追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="8500e-152">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="8500e-153">處理您的裝置無法在應用程式環境的空間中找到本身所在位置的狀況</span><span class="sxs-lookup"><span data-stu-id="8500e-153">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="8500e-154">鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="8500e-154">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="8500e-155">在您的應用程式中取得實際環境和混合實境鍵盤的輸入</span><span class="sxs-lookup"><span data-stu-id="8500e-155">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="8500e-156">4.部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="8500e-156">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="8500e-157">當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是匯出和建置 Unity Visual Studio 解決方案。</span><span class="sxs-lookup"><span data-stu-id="8500e-157">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="8500e-158">有了該 VS 解決方案，您就可以在真正或模擬的裝置上，以三種方式之一來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="8500e-158">With that VS solution in hand, you can run your application in one of three ways on a real or simulated device.</span></span> <span data-ttu-id="8500e-159">在本節結束時，您將能夠在任何裝置或模擬器上部署您的應用程式，以符合您的開發需求。</span><span class="sxs-lookup"><span data-stu-id="8500e-159">By the end of this section, you'll be able to deploy your application on whichever device or emulator fits your development needs.</span></span>

* [<span data-ttu-id="8500e-160">HoloLens 或 Windows 混合實境沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="8500e-160">HoloLens or Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="8500e-161">HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="8500e-161">HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [<span data-ttu-id="8500e-162">Windows 混合實境沉浸式頭戴裝置模擬器</span><span class="sxs-lookup"><span data-stu-id="8500e-162">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="5-adding-services"></a><span data-ttu-id="8500e-163">5.新增服務</span><span class="sxs-lookup"><span data-stu-id="8500e-163">5. Adding services</span></span>

<span data-ttu-id="8500e-164">到了開發旅程的這個階段，您可能會想要新增服務，或是需要商業部署方面的協助。</span><span class="sxs-lookup"><span data-stu-id="8500e-164">At this point in your development journey you might be looking to add services or for a helping hand with commercial deployment.</span></span> <span data-ttu-id="8500e-165">將 [Azure 雲端服務](../mixed-reality-cloud-services.md)與 Dynamics 365 功能整合，可以有效提升您的專案等級。</span><span class="sxs-lookup"><span data-stu-id="8500e-165">Integrating [Azure Cloud Services](../mixed-reality-cloud-services.md) and Dynamics 365 features can level up your projects in a major way.</span></span> <span data-ttu-id="8500e-166">我們編譯了一些方便您探索及擴充混合實境知識的起點。</span><span class="sxs-lookup"><span data-stu-id="8500e-166">We've compiled a few starting points for you to explore and expand your Mixed Reality knowledge.</span></span>

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

<span data-ttu-id="8500e-167">針對其他可供您以自助方式新增至 Unity 專案的其他 Azure 服務，我們也提供了[完整的支援文件清單](../mixed-reality-cloud-services.md#standalone-unity-services)。</span><span class="sxs-lookup"><span data-stu-id="8500e-167">We also have a [comprehensive list of support documentation for additional Azure services](../mixed-reality-cloud-services.md#standalone-unity-services) that you can add to your Unity projects on a self-serve basis.</span></span>

## <a name="whats-next"></a><span data-ttu-id="8500e-168">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="8500e-168">What's next?</span></span>

<span data-ttu-id="8500e-169">開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。</span><span class="sxs-lookup"><span data-stu-id="8500e-169">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="8500e-170">完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。</span><span class="sxs-lookup"><span data-stu-id="8500e-170">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="8500e-171">請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！</span><span class="sxs-lookup"><span data-stu-id="8500e-171">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="8500e-172">移植</span><span class="sxs-lookup"><span data-stu-id="8500e-172">Porting</span></span>

<span data-ttu-id="8500e-173">如果您有想要移植的現有應用程式，您接下來即應參考下列文章：</span><span class="sxs-lookup"><span data-stu-id="8500e-173">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="8500e-174">HoloToolkit/MRTK 至 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="8500e-174">HoloToolkit/MRTK to MRTK v2</span></span>](../porting-apps/porting-hl1-hl2.md)
* [<span data-ttu-id="8500e-175">沈浸式應用程式的移植指南</span><span class="sxs-lookup"><span data-stu-id="8500e-175">Porting guide for immersive apps</span></span>](../porting-apps/porting-guides.md)
* [<span data-ttu-id="8500e-176">輸入移植指南</span><span class="sxs-lookup"><span data-stu-id="8500e-176">Input porting guide</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a><span data-ttu-id="8500e-177">教學課程</span><span class="sxs-lookup"><span data-stu-id="8500e-177">Tutorials</span></span>

<span data-ttu-id="8500e-178">如果您想要將特定的混合實境功能新增至應用程式，我們策劃了數個教學課程，可逐步引導您完成相關程序。</span><span class="sxs-lookup"><span data-stu-id="8500e-178">If you're looking to add specific Mixed Reality features to your applications, we have several curated tutorials that can run you through the process from end-to-end.</span></span> <span data-ttu-id="8500e-179">以下列出最多人使用的 HoloLens 2 和 HoloLens (第 1 代) 內容，但您可以瀏覽教學課程概觀以了解完整的系列。</span><span class="sxs-lookup"><span data-stu-id="8500e-179">Our most popular HoloLens 2 and HoloLens (1st Gen) content is listed below, but you can find the entire collection by visiting the tutorials overview.</span></span>

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a><span data-ttu-id="8500e-180">其他資源</span><span class="sxs-lookup"><span data-stu-id="8500e-180">Additional resources</span></span>

<span data-ttu-id="8500e-181">在您自行進入混合實境的世界之前，建議您先參閱下列 MRTK 相關文件。</span><span class="sxs-lookup"><span data-stu-id="8500e-181">Before going out into the world of mixed reality on your own, we recommend taking a look at the MRTK-related documentation listed below.</span></span> <span data-ttu-id="8500e-182">這些文章是您深入了解 MRTK 運作方式的絕佳切入點，同時也提供如何讓應用程式更具效能的深入解析。</span><span class="sxs-lookup"><span data-stu-id="8500e-182">These articles are great jumping off points for understanding how MRTK works in greater detail and will give you insight into making your app more performant.</span></span>

|  <span data-ttu-id="8500e-183">主題</span><span class="sxs-lookup"><span data-stu-id="8500e-183">Topic</span></span>  |  <span data-ttu-id="8500e-184">描述</span><span class="sxs-lookup"><span data-stu-id="8500e-184">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="8500e-185">MRTK 架構概觀</span><span class="sxs-lookup"><span data-stu-id="8500e-185">MRTK Architecture overview</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html) | <span data-ttu-id="8500e-186">深入了解 MRTK SDK 在您的專案中如何運作</span><span class="sxs-lookup"><span data-stu-id="8500e-186">Get a deeper understanding of how the MRTK SDK works in your projects</span></span> |
| [<span data-ttu-id="8500e-187">設定和效能</span><span class="sxs-lookup"><span data-stu-id="8500e-187">Settings and performance</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) | <span data-ttu-id="8500e-188">分析您的應用程式、更新 Unity 設定，並取得最理想的全像投影穩定效能</span><span class="sxs-lookup"><span data-stu-id="8500e-188">Profile your app, update your Unity settings, and get the best hologram stabilization performance available</span></span> |
| [<span data-ttu-id="8500e-189">開始使用 MRTK + XR</span><span class="sxs-lookup"><span data-stu-id="8500e-189">Getting started with MRTK + XR</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/getting-started-with-mrtk-and-xrsdk.md) | <span data-ttu-id="8500e-190">轉移至 Unity 所提供的替代 XR 管線</span><span class="sxs-lookup"><span data-stu-id="8500e-190">Transfer over to the alternative XR pipeline provided by Unity</span></span> |

### <a name="unity-resources"></a><span data-ttu-id="8500e-191">Unity 資源</span><span class="sxs-lookup"><span data-stu-id="8500e-191">Unity resources</span></span>

<span data-ttu-id="8500e-192">除了可以在 docs.microsoft.com 上取得的本文件之外，Unity 還會隨著 Unity 編輯器一起安裝 Windows Mixed Reality 功能的文件。</span><span class="sxs-lookup"><span data-stu-id="8500e-192">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="8500e-193">Unity 提供的文件包含兩個不同的部分。</span><span class="sxs-lookup"><span data-stu-id="8500e-193">The Unity provided documentation includes two separate sections.</span></span>

|  <span data-ttu-id="8500e-194">資源</span><span class="sxs-lookup"><span data-stu-id="8500e-194">Resource</span></span>  |  <span data-ttu-id="8500e-195">描述</span><span class="sxs-lookup"><span data-stu-id="8500e-195">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="8500e-196">指令碼參考</span><span class="sxs-lookup"><span data-stu-id="8500e-196">Scripting reference</span></span>](https://docs.unity3d.com/ScriptReference/) | <span data-ttu-id="8500e-197">這部分的文件包含 Unity 所提供之 API 指令碼的詳細資料，並且可從 Unity 編輯器線上存取，只要按一下 [說明] > [指令碼參考] 即可</span><span class="sxs-lookup"><span data-stu-id="8500e-197">This section of the documentation contains details of the scripting API that Unity provides and is accessible online from the Unity Editor by clicking **Help > Scripting Reference**</span></span> |
| [<span data-ttu-id="8500e-198">手動</span><span class="sxs-lookup"><span data-stu-id="8500e-198">Manual</span></span>](https://docs.unity3d.com/Manual/index.html) | <span data-ttu-id="8500e-199">此手冊旨在協助您了解如何使用 Unity (包括基本與進階技術)，並且可從 Unity 編輯器線上存取，只要按一下 [說明] > [指令碼參考] 即可</span><span class="sxs-lookup"><span data-stu-id="8500e-199">This manual is designed to help you learn how to use Unity, from basic to advanced techniques, and is accessible online or from the Unity Editor by clicking **Help > Manual**</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="8500e-200">探索 MRTK</span><span class="sxs-lookup"><span data-stu-id="8500e-200">Explore MRTK</span></span>](mrtk-getting-started.md)

## <a name="have-feedback"></a><span data-ttu-id="8500e-201">有任何意見嗎？</span><span class="sxs-lookup"><span data-stu-id="8500e-201">Have feedback?</span></span>

<span data-ttu-id="8500e-202">您可以在 [Unity 論壇](https://aka.ms/unityforums)藉由標記 **Microsoft** 和下列標籤組合來找到我們，進而協助我們了解您提供意見反應的外掛程式：</span><span class="sxs-lookup"><span data-stu-id="8500e-202">You can find us on the [Unity Forums](https://aka.ms/unityforums) by tagging **Microsoft** and a combination of the following tags to help us understand what plugin you're providing feedback for:</span></span>

* <span data-ttu-id="8500e-203">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8500e-203">HoloLens 2</span></span> 
* <span data-ttu-id="8500e-204">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8500e-204">Windows Mixed Reality</span></span>
* <span data-ttu-id="8500e-205">OpenXR</span><span class="sxs-lookup"><span data-stu-id="8500e-205">OpenXR</span></span>
* <span data-ttu-id="8500e-206">XRSDK</span><span class="sxs-lookup"><span data-stu-id="8500e-206">XRSDK</span></span>
* <span data-ttu-id="8500e-207">傳統 XR</span><span class="sxs-lookup"><span data-stu-id="8500e-207">Legacy XR</span></span> 

## <a name="see-also"></a><span data-ttu-id="8500e-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8500e-208">See also</span></span>

* [<span data-ttu-id="8500e-209">混合實境工具組 v2</span><span class="sxs-lookup"><span data-stu-id="8500e-209">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="8500e-210">MR Basics 100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="8500e-210">MR Basics 100: Getting started with Unity</span></span>](tutorials/holograms-100.md)
* [<span data-ttu-id="8500e-211">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="8500e-211">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="8500e-212">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="8500e-212">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="8500e-213">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="8500e-213">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="8500e-214">搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式</span><span class="sxs-lookup"><span data-stu-id="8500e-214">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="8500e-215">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="8500e-215">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="8500e-216">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="8500e-216">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="8500e-217">移植指南</span><span class="sxs-lookup"><span data-stu-id="8500e-217">Porting guides</span></span>](../porting-apps/porting-guides.md)