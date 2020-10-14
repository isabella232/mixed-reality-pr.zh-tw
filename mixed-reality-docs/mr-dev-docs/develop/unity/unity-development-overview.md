---
title: Unity 開發概觀
description: 開始在 Unity 中建置混合實境應用程式。
author: thetuvix
ms.author: kurtie
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合實境, 開發, 開始使用, 新專案, 移植, 功能, 相機, 模擬, 模擬, 文件
ms.openlocfilehash: ed6e3482194b17ec3b6dfa2abe309f3519c64662
ms.sourcegitcommit: 9ab467e36d7d9fad51b0e93a56038a6421a7b09d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "91980309"
---
# <a name="unity-development-overview"></a><span data-ttu-id="018bb-104">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="018bb-104">Unity development overview</span></span>

![Unity 橫幅標誌](../images/unity_logo_banner.png)

<span data-ttu-id="018bb-106">要在 [Unity](https://unity.com) 中建置[混合實境應用程式](../../design/app-views.md)，使用混合實境工具組是最快速的途徑。</span><span class="sxs-lookup"><span data-stu-id="018bb-106">The fastest path to building a [mixed reality app](../../design/app-views.md) in [Unity](https://unity.com) is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="018bb-107">如果您是首次接觸 Unity，建議您先探索 Unity 學習平台上的入門級[教學課程](https://unity3d.com/learn/tutorials)，再繼續操作。</span><span class="sxs-lookup"><span data-stu-id="018bb-107">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="018bb-108">您也可以造訪內容豐富的[資產存放區](https://www.assetstore.unity3d.com/)和 [Unity 混合實境論壇](https://forum.unity3d.com/forums/hololens.102/)，與建置混合實境應用程式的線上社群交流。</span><span class="sxs-lookup"><span data-stu-id="018bb-108">It's also a good idea to visit the comprehensive [Asset Store](https://www.assetstore.unity3d.com/) and the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="018bb-109">您絕對想不到在這裡會發現哪些絕佳的資產或解決方案。</span><span class="sxs-lookup"><span data-stu-id="018bb-109">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="018bb-110">當您準備好開始使用 MRTK 時，請前往以下開發檢查點！</span><span class="sxs-lookup"><span data-stu-id="018bb-110">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="018bb-111">如果您想要將現有的 Unity 專案導入 HoloLens 2 中，請參閱我們的 **[移植指南](../porting-apps/porting-guides.md)** 。</span><span class="sxs-lookup"><span data-stu-id="018bb-111">Take a look at our **[porting guides](../porting-apps/porting-guides.md)** if you have an existing Unity project that you want to bring over to HoloLens 2.</span></span> <span data-ttu-id="018bb-112">對於使用 HTK、MRTK v1、SteamVR 的專案，或針對沉浸式頭戴裝置 (例如 Oculus Rift 或 HTC Vive) 開發的專案，我們都提供了相關指南。</span><span class="sxs-lookup"><span data-stu-id="018bb-112">We have guides for projects that are using HTK, MRTK v1, SteamVR or were developed for immersive headsets such as the Oculus Rift or HTC Vive.</span></span>

## <a name="development-checkpoints"></a><span data-ttu-id="018bb-113">開發檢查點</span><span class="sxs-lookup"><span data-stu-id="018bb-113">Development checkpoints</span></span>

<span data-ttu-id="018bb-114">使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。</span><span class="sxs-lookup"><span data-stu-id="018bb-114">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> <span data-ttu-id="018bb-115">如果您尚未探索 [設計全像投影範例應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，建議您下載並使用，以熟悉混合實境 UX 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="018bb-115">If you haven't already explored the [Designing Holograms sample application](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), we recommend downloading and using it to familiarize yourself with the basics of Mixed Reality UX.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="018bb-116">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="018bb-116">1. Getting started</span></span>
<span data-ttu-id="018bb-117">在 Unity 中開發最簡單的方式，就是使用混合實境工具組。</span><span class="sxs-lookup"><span data-stu-id="018bb-117">The easiest way to develop in Unity is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="018bb-118">MRTK 可協助您自動設定混合實境的專案，並提供一組功能協助您加速開發流程。</span><span class="sxs-lookup"><span data-stu-id="018bb-118">MRTK will help you automatically setup a project for Mixed Reality and provide a set of features to accelerate your development process.</span></span> <span data-ttu-id="018bb-119">閱讀本節的內容後，您大致上就已了解混合實境工具組、針對混合實境應用程式正確設定的開發環境，以及您自行建置且可在 Unity 中運作的 MRTK 專案。</span><span class="sxs-lookup"><span data-stu-id="018bb-119">By the end of this section, you'll have a basic understanding of the Mixed Reality Toolkit, a properly configured development environment for Mixed Reality apps, and a working MRTK project in Unity that you built yourself.</span></span>

|  <span data-ttu-id="018bb-120">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="018bb-120">Checkpoint</span></span>  |  <span data-ttu-id="018bb-121">結果</span><span class="sxs-lookup"><span data-stu-id="018bb-121">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="018bb-122">什麼是 MRTK？</span><span class="sxs-lookup"><span data-stu-id="018bb-122">What is MRTK?</span></span>](mrtk-getting-started.md) | <span data-ttu-id="018bb-123">熟悉混合實境工具組及其提供的功能，開始您的旅程</span><span class="sxs-lookup"><span data-stu-id="018bb-123">Begin your journey by getting acquainted with the Mixed Reality Toolkit and what it has to offer</span></span> |
| [<span data-ttu-id="018bb-124">安裝最新工具</span><span class="sxs-lookup"><span data-stu-id="018bb-124">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="018bb-125">下載並安裝最新的 Unity 套件，並設定您的混合實境專案</span><span class="sxs-lookup"><span data-stu-id="018bb-125">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="018bb-126">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="018bb-126">HoloLens 2 tutorial series</span></span>](tutorials/mr-learning-base-01.md) | <span data-ttu-id="018bb-127">進入 HoloLens 2 硬體的入門級 MRTK 教學課程</span><span class="sxs-lookup"><span data-stu-id="018bb-127">Dive into beginner level MRTK tutorials for HoloLens 2 hardware</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="018bb-128">如果您想要在未匯入混合實境工具組的情況下建立新的 Unity 專案，則您需要為 Windows Mixed Reality 手動變更一小組 Unity 設定。</span><span class="sxs-lookup"><span data-stu-id="018bb-128">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="018bb-129">這些設定分成兩個類別：每個專案和每個場景。</span><span class="sxs-lookup"><span data-stu-id="018bb-129">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="018bb-130">如需逐步程序，請參閱我們的設定指南。</span><span class="sxs-lookup"><span data-stu-id="018bb-130">Take a look at our configuration guide for the step-by-step process.</span></span>

> [!NOTE]
> <span data-ttu-id="018bb-131">在您的專案中設定 MRTK V2 後，標準 Unity 遊戲物件 (例如相機) 會立即亮起，以提供坐姿級別體驗。</span><span class="sxs-lookup"><span data-stu-id="018bb-131">Once you've setup MRTK V2 in your project, standard Unity game objects like the camera will light up immediately for a seated-scale experience.</span></span> <span data-ttu-id="018bb-132">您可以在 [座標系統] 頁面上找到變更應用程式體驗級別的指示。</span><span class="sxs-lookup"><span data-stu-id="018bb-132">You can find instructions on changing the experience scale of your application on the coordinate systems page.</span></span>

### <a name="2-core-building-blocks"></a><span data-ttu-id="018bb-133">2.核心基本要素</span><span class="sxs-lookup"><span data-stu-id="018bb-133">2. Core building blocks</span></span>

<span data-ttu-id="018bb-134">混合實境應用程式的所有核心建置組塊都會以與其他 Unity API 一致的方式公開。</span><span class="sxs-lookup"><span data-stu-id="018bb-134">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="018bb-135">這些建置組塊是透過混合實境工具組提供的獨立功能。</span><span class="sxs-lookup"><span data-stu-id="018bb-135">These building blocks are available as standalone features and through the Mixed Reality Toolkit.</span></span> <span data-ttu-id="018bb-136">您目前可能不需用到所有功能，但建議您及早探索。</span><span class="sxs-lookup"><span data-stu-id="018bb-136">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="018bb-137">深入探討下列核心建置組塊後，您將了解如何讓包含多樣化功能的工具箱自行或透過 MRTK 整合到混合實境專案中。</span><span class="sxs-lookup"><span data-stu-id="018bb-137">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a Mixed Reality project by themselves or through MRTK.</span></span>

[!INCLUDE[](../includes/unity-building-blocks.md)]

### <a name="3-platform-capabilities-and-apis"></a><span data-ttu-id="018bb-138">3.平台功能和 API</span><span class="sxs-lookup"><span data-stu-id="018bb-138">3. Platform capabilities and APIs</span></span>

<span data-ttu-id="018bb-139">在混合實境應用程式中各有作用的其他重要功能可透過 Unity API 來使用，不需要任何額外的封裝或設定。</span><span class="sxs-lookup"><span data-stu-id="018bb-139">Other key features that play a role in mixed reality applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="018bb-140">這些功能可以新增至 Unity 專案，且不一定需要先安裝 MRTK。</span><span class="sxs-lookup"><span data-stu-id="018bb-140">These features can be added to Unity projects with or without MRTK installed.</span></span> <span data-ttu-id="018bb-141">深入了解 Unity 提供的進階功能後，您將能夠建置更有深度的複雜混合實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="018bb-141">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex Mixed Reality apps.</span></span>

|  <span data-ttu-id="018bb-142">功能</span><span class="sxs-lookup"><span data-stu-id="018bb-142">Feature</span></span>  |  <span data-ttu-id="018bb-143">功能</span><span class="sxs-lookup"><span data-stu-id="018bb-143">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="018bb-144">共用體驗</span><span class="sxs-lookup"><span data-stu-id="018bb-144">Shared experiences</span></span>](shared-experiences-in-unity.md) | <span data-ttu-id="018bb-145">使用空間錨點共用，共同檢視空間中固定點上的相同全像投影，並與其互動</span><span class="sxs-lookup"><span data-stu-id="018bb-145">View and interact collectively with the same hologram at a fixed point in space using spatial anchor sharing</span></span> |
| [<span data-ttu-id="018bb-146">定位相機</span><span class="sxs-lookup"><span data-stu-id="018bb-146">Locatable camera</span></span>](locatable-camera-in-unity.md) | <span data-ttu-id="018bb-147">在您的混合實境應用程式中擷取相片和影片內容</span><span class="sxs-lookup"><span data-stu-id="018bb-147">Capture photos and video content in your Mixed Reality application</span></span> |
| [<span data-ttu-id="018bb-148">對焦點</span><span class="sxs-lookup"><span data-stu-id="018bb-148">Focus point</span></span>](focus-point-in-unity.md) | <span data-ttu-id="018bb-149">為 HoloLens 提供有關於如何對目前顯示的全像投影最有效地執行穩定性的提示</span><span class="sxs-lookup"><span data-stu-id="018bb-149">Provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed</span></span> |
| [<span data-ttu-id="018bb-150">追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="018bb-150">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="018bb-151">處理您的裝置無法在應用程式環境的空間中找到本身所在位置的狀況</span><span class="sxs-lookup"><span data-stu-id="018bb-151">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="018bb-152">鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="018bb-152">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="018bb-153">在您的應用程式中取得實際環境和混合實境鍵盤的輸入</span><span class="sxs-lookup"><span data-stu-id="018bb-153">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="018bb-154">4.部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="018bb-154">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="018bb-155">當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是匯出和建置 Unity Visual Studio 解決方案。</span><span class="sxs-lookup"><span data-stu-id="018bb-155">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="018bb-156">有了該 VS 解決方案，您就可以在真正或模擬的裝置上，以三種方式之一來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="018bb-156">With that VS solution in hand, you can run your application in one of three ways on a real or simulated device.</span></span> <span data-ttu-id="018bb-157">在本節結束時，您將能夠在任何裝置或模擬器上部署您的應用程式，以符合您的開發需求。</span><span class="sxs-lookup"><span data-stu-id="018bb-157">By the end of this section, you'll be able to deploy your application on whichever device or emulator fits your development needs.</span></span>

* [<span data-ttu-id="018bb-158">HoloLens 或 Windows 混合實境沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="018bb-158">HoloLens or Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="018bb-159">HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="018bb-159">HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [<span data-ttu-id="018bb-160">Windows 混合實境沉浸式頭戴裝置模擬器</span><span class="sxs-lookup"><span data-stu-id="018bb-160">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="5-adding-services"></a><span data-ttu-id="018bb-161">5.新增服務</span><span class="sxs-lookup"><span data-stu-id="018bb-161">5. Adding services</span></span>

<span data-ttu-id="018bb-162">到了開發旅程的這個階段，您可能會想要新增服務，或是需要商業部署方面的協助。</span><span class="sxs-lookup"><span data-stu-id="018bb-162">At this point in your development journey you might be looking to add services or for a helping hand with commercial deployment.</span></span> <span data-ttu-id="018bb-163">將 [Azure 雲端服務](../mixed-reality-cloud-services.md)與 Dynamics 365 功能整合，可以有效提升您的專案等級。</span><span class="sxs-lookup"><span data-stu-id="018bb-163">Integrating [Azure Cloud Services](../mixed-reality-cloud-services.md) and Dynamics 365 features can level up your projects in a major way.</span></span> <span data-ttu-id="018bb-164">我們編譯了一些方便您探索及擴充混合實境知識的起點。</span><span class="sxs-lookup"><span data-stu-id="018bb-164">We've compiled a few starting points for you to explore and expand your Mixed Reality knowledge.</span></span>

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

<span data-ttu-id="018bb-165">針對其他可供您以自助方式新增至 Unity 專案的其他 Azure 服務，我們也提供了[完整的支援文件清單](../mixed-reality-cloud-services.md#standalone-unity-services)。</span><span class="sxs-lookup"><span data-stu-id="018bb-165">We also have a [comprehensive list of support documentation for additional Azure services](../mixed-reality-cloud-services.md#standalone-unity-services) that you can add to your Unity projects on a self-serve basis.</span></span>

## <a name="whats-next"></a><span data-ttu-id="018bb-166">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="018bb-166">What's next?</span></span>

<span data-ttu-id="018bb-167">開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。</span><span class="sxs-lookup"><span data-stu-id="018bb-167">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="018bb-168">完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。</span><span class="sxs-lookup"><span data-stu-id="018bb-168">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="018bb-169">請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！</span><span class="sxs-lookup"><span data-stu-id="018bb-169">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="018bb-170">移植</span><span class="sxs-lookup"><span data-stu-id="018bb-170">Porting</span></span>

<span data-ttu-id="018bb-171">如果您有想要移植的現有應用程式，您接下來即應參考下列文章：</span><span class="sxs-lookup"><span data-stu-id="018bb-171">If you have existing apps that you'd like to port over, the articles listed below are your next stop/</span></span>

* [<span data-ttu-id="018bb-172">HoloToolkit/MRTK 至 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="018bb-172">HoloToolkit/MRTK to MRTK v2</span></span>](mrtk-porting-guide.md)
* [<span data-ttu-id="018bb-173">沈浸式應用程式的移植指南</span><span class="sxs-lookup"><span data-stu-id="018bb-173">Porting guide for immersive apps</span></span>](../porting-apps/porting-guides.md)
* [<span data-ttu-id="018bb-174">輸入移植指南</span><span class="sxs-lookup"><span data-stu-id="018bb-174">Input porting guide</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a><span data-ttu-id="018bb-175">教學課程</span><span class="sxs-lookup"><span data-stu-id="018bb-175">Tutorials</span></span>

<span data-ttu-id="018bb-176">如果您想要將特定的混合實境功能新增至應用程式，我們策劃了數個教學課程，可逐步引導您完成相關程序。</span><span class="sxs-lookup"><span data-stu-id="018bb-176">If you're looking to add specific Mixed Reality features to your applications, we have several curated tutorials that can run you through the process from end-to-end.</span></span> <span data-ttu-id="018bb-177">以下列出最多人使用的 HoloLens 2 和 HoloLens (第 1 代) 內容，但您可以瀏覽教學課程概觀以了解完整的系列。</span><span class="sxs-lookup"><span data-stu-id="018bb-177">Our most popular HoloLens 2 and HoloLens (1st Gen) content is listed below, but you can find the entire collection by visiting the tutorials overview.</span></span>

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a><span data-ttu-id="018bb-178">其他資源</span><span class="sxs-lookup"><span data-stu-id="018bb-178">Additional resources</span></span>

<span data-ttu-id="018bb-179">在您自行進入混合實境的世界之前，建議您先參閱下列 MRTK 相關文件。</span><span class="sxs-lookup"><span data-stu-id="018bb-179">Before going out into the world of mixed reality on your own, we recommend taking a look at the MRTK-related documentation listed below.</span></span> <span data-ttu-id="018bb-180">這些文章是您深入了解 MRTK 運作方式的絕佳切入點，同時也提供如何讓應用程式更具效能的深入解析。</span><span class="sxs-lookup"><span data-stu-id="018bb-180">These articles are great jumping off points for understanding how MRTK works in greater detail and will give you insight into making your app more performant.</span></span>

|  <span data-ttu-id="018bb-181">主題</span><span class="sxs-lookup"><span data-stu-id="018bb-181">Topic</span></span>  |  <span data-ttu-id="018bb-182">描述</span><span class="sxs-lookup"><span data-stu-id="018bb-182">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="018bb-183">MRTK 架構概觀</span><span class="sxs-lookup"><span data-stu-id="018bb-183">MRTK Architecture overview</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html) | <span data-ttu-id="018bb-184">深入了解 MRTK SDK 在您的專案中如何運作</span><span class="sxs-lookup"><span data-stu-id="018bb-184">Get a deeper understanding of how the MRTK SDK works in your projects</span></span> |
| [<span data-ttu-id="018bb-185">設定和效能</span><span class="sxs-lookup"><span data-stu-id="018bb-185">Settings and performance</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) | <span data-ttu-id="018bb-186">分析您的應用程式、更新 Unity 設定，並取得最理想的全像投影穩定效能</span><span class="sxs-lookup"><span data-stu-id="018bb-186">Profile your app, update your Unity settings, and get the best hologram stabilization performance available</span></span> |
| [<span data-ttu-id="018bb-187">開始使用 MRTK + XR</span><span class="sxs-lookup"><span data-stu-id="018bb-187">Getting started with MRTK + XR</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) | <span data-ttu-id="018bb-188">轉移至 Unity 所提供的替代 XR 管線</span><span class="sxs-lookup"><span data-stu-id="018bb-188">Transfer over to the alternative XR pipeline provided by Unity</span></span> |

### <a name="unity-resources"></a><span data-ttu-id="018bb-189">Unity 資源</span><span class="sxs-lookup"><span data-stu-id="018bb-189">Unity resources</span></span>

<span data-ttu-id="018bb-190">除了可以在 docs.microsoft.com 上取得的本文件之外，Unity 還會隨著 Unity 編輯器一起安裝 Windows Mixed Reality 功能的文件。</span><span class="sxs-lookup"><span data-stu-id="018bb-190">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="018bb-191">Unity 提供的文件包含兩個不同的部分。</span><span class="sxs-lookup"><span data-stu-id="018bb-191">The Unity provided documentation includes two separate sections.</span></span>

|  <span data-ttu-id="018bb-192">資源</span><span class="sxs-lookup"><span data-stu-id="018bb-192">Resource</span></span>  |  <span data-ttu-id="018bb-193">描述</span><span class="sxs-lookup"><span data-stu-id="018bb-193">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="018bb-194">指令碼參考</span><span class="sxs-lookup"><span data-stu-id="018bb-194">Scripting reference</span></span>](https://docs.unity3d.com/ScriptReference/) | <span data-ttu-id="018bb-195">這部分的文件包含 Unity 所提供之 API 指令碼的詳細資料，並且可從 Unity 編輯器線上存取，只要按一下 [說明] > [指令碼參考] 即可</span><span class="sxs-lookup"><span data-stu-id="018bb-195">This section of the documentation contains details of the scripting API that Unity provides and is accessible online from the Unity Editor by clicking **Help > Scripting Reference**</span></span> |
| [<span data-ttu-id="018bb-196">手動</span><span class="sxs-lookup"><span data-stu-id="018bb-196">Manual</span></span>](https://docs.unity3d.com/Manual/index.html) | <span data-ttu-id="018bb-197">此手冊旨在協助您了解如何使用 Unity (包括基本與進階技術)，並且可從 Unity 編輯器線上存取，只要按一下 [說明] > [指令碼參考] 即可</span><span class="sxs-lookup"><span data-stu-id="018bb-197">This manual is designed to help you learn how to use Unity, from basic to advanced techniques, and is accessible online or from the Unity Editor by clicking **Help > Manual**</span></span> |


> [!div class="nextstepaction"]
> [<span data-ttu-id="018bb-198">探索 MRTK</span><span class="sxs-lookup"><span data-stu-id="018bb-198">Explore MRTK</span></span>](mrtk-getting-started.md)

## <a name="see-also"></a><span data-ttu-id="018bb-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="018bb-199">See also</span></span>
* [<span data-ttu-id="018bb-200">混合實境工具組 v2</span><span class="sxs-lookup"><span data-stu-id="018bb-200">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="018bb-201">MR Basics 100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="018bb-201">MR Basics 100: Getting started with Unity</span></span>](tutorials/holograms-100.md)
* [<span data-ttu-id="018bb-202">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="018bb-202">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="018bb-203">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="018bb-203">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="018bb-204">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="018bb-204">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="018bb-205">搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式</span><span class="sxs-lookup"><span data-stu-id="018bb-205">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="018bb-206">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="018bb-206">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="018bb-207">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="018bb-207">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="018bb-208">移植指南</span><span class="sxs-lookup"><span data-stu-id="018bb-208">Porting guides</span></span>](../porting-apps/porting-guides.md)
