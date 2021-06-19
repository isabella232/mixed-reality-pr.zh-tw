---
title: 適用於 HoloLens 的 Unity 開發
description: 透過我們策劃的檢查點旅程，開始在 Unity 和 HoloLens 中建置混合實境應用程式。
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合實境, 開發, 開始使用, 新專案, 移植, 功能, 相機, 模擬, 模擬, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 什麼是虛擬實境, 什麼是擴增實境, MRTK, 混合實境工具組, 空間對應, 語音輸入, 定位相機, 模擬器, Azure, 教學課程
ms.openlocfilehash: b6d8d44851813f340997c41b2f25104b51dee2fa
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394292"
---
# <a name="unity-development-for-hololens"></a><span data-ttu-id="3807a-104">適用於 HoloLens 的 Unity 開發</span><span class="sxs-lookup"><span data-stu-id="3807a-104">Unity development for HoloLens</span></span>

![Unity 橫幅標誌](../images/unity_logo_banner.png)

<span data-ttu-id="3807a-106">Unity 是市場上領先的即時開發平臺之一，其基礎執行時間程式碼是以 c + + 撰寫，而所有開發腳本都是在 c # 中完成。</span><span class="sxs-lookup"><span data-stu-id="3807a-106">Unity is one of the leading real-time development platforms on the market, with underlying runtime code written in C++ and all development scripting is done in C#.</span></span> <span data-ttu-id="3807a-107">無論您想要打造遊戲、電影和動畫電影藝術，甚至要在虛擬世界中轉譯架構或工程概念，Unity 都有可支援您的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="3807a-107">Whether you're looking to build games, movies and animation cinematics, or even render architectural or engineering concepts in a virtual world, Unity has the infrastructure to support you.</span></span> <span data-ttu-id="3807a-108">當您準備好開始使用時，請前往下面的開發檢查點！</span><span class="sxs-lookup"><span data-stu-id="3807a-108">When you're ready to get started, head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3807a-109">如果您想要將現有的 Unity 專案導入 HoloLens 2 中，請參閱我們的 **[移植指南](../porting-apps/porting-overview.md)** 。</span><span class="sxs-lookup"><span data-stu-id="3807a-109">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to HoloLens 2.</span></span> <span data-ttu-id="3807a-110">我們針對使用 HTK、MRTK v1 或 SteamVR 的專案提供了指南。</span><span class="sxs-lookup"><span data-stu-id="3807a-110">We have guides for projects that are using HTK, MRTK v1, or SteamVR.</span></span>

## <a name="development-checkpoints"></a><span data-ttu-id="3807a-111">開發檢查點</span><span class="sxs-lookup"><span data-stu-id="3807a-111">Development checkpoints</span></span>

<span data-ttu-id="3807a-112">使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。</span><span class="sxs-lookup"><span data-stu-id="3807a-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> <span data-ttu-id="3807a-113">如果您尚未探索 [設計全像投影範例應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，建議您下載並使用，以熟悉混合實境 UX 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="3807a-113">If you haven't already explored the [Designing Holograms sample application](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), we recommend downloading and using it to familiarize yourself with the basics of Mixed Reality UX.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="3807a-114">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="3807a-114">1. Getting started</span></span>

<span data-ttu-id="3807a-115">在 Unity 中開發最簡單的方式，就是使用混合實境工具組。</span><span class="sxs-lookup"><span data-stu-id="3807a-115">The easiest way to develop in Unity is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="3807a-116">MRTK 可協助您自動設定混合實境的專案，並提供一組功能協助您加速開發流程。</span><span class="sxs-lookup"><span data-stu-id="3807a-116">MRTK will help you automatically setup a project for Mixed Reality and provide a set of features to accelerate your development process.</span></span> <span data-ttu-id="3807a-117">閱讀本節的內容後，您大致上就已了解混合實境工具組、針對混合實境應用程式正確設定的開發環境，以及您自行建置且可在 Unity 中運作的 MRTK 專案。</span><span class="sxs-lookup"><span data-stu-id="3807a-117">By the end of this section, you'll have a basic understanding of the Mixed Reality Toolkit, a properly configured development environment for Mixed Reality apps, and a working MRTK project in Unity that you built yourself.</span></span>

|  <span data-ttu-id="3807a-118">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="3807a-118">Checkpoint</span></span>  |  <span data-ttu-id="3807a-119">結果</span><span class="sxs-lookup"><span data-stu-id="3807a-119">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="3807a-120">混合現實工具組簡介</span><span class="sxs-lookup"><span data-stu-id="3807a-120">Introducing the Mixed Reality Toolkit</span></span>](mrtk-getting-started.md) | <span data-ttu-id="3807a-121">熟悉混合實境工具組及其提供的功能，開始您的旅程</span><span class="sxs-lookup"><span data-stu-id="3807a-121">Begin your journey by getting acquainted with the Mixed Reality Toolkit and what it has to offer</span></span> |
| [<span data-ttu-id="3807a-122">下載 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="3807a-122">Download the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md) | <span data-ttu-id="3807a-123">新的開發人員工具，可用於探索、更新和新增混合現實功能套件至 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="3807a-123">A new developer tool for discovering, updating, and adding Mixed Reality feature packages to your Unity projects</span></span> |
| [<span data-ttu-id="3807a-124">設定開發人員環境</span><span class="sxs-lookup"><span data-stu-id="3807a-124">Setup your developer environment</span></span>](../install-the-tools.md) | <span data-ttu-id="3807a-125">下載並安裝最新的 Unity 套件，並設定您的混合實境專案</span><span class="sxs-lookup"><span data-stu-id="3807a-125">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="3807a-126">完成 HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="3807a-126">Complete the HoloLens 2 tutorial series</span></span>](tutorials/mr-learning-base-01.md) | <span data-ttu-id="3807a-127">進入 HoloLens 2 硬體的入門級 MRTK 教學課程</span><span class="sxs-lookup"><span data-stu-id="3807a-127">Dive into beginner level MRTK tutorials for HoloLens 2 hardware</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="3807a-128">如果您想要在未匯入混合實境工具組的情況下建立新的 Unity 專案，則您需要為 Windows Mixed Reality 手動變更一小組 Unity 設定。</span><span class="sxs-lookup"><span data-stu-id="3807a-128">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="3807a-129">如需詳細資訊，請參閱我們的設定 [指南](choosing-unity-version.md) 。</span><span class="sxs-lookup"><span data-stu-id="3807a-129">Take a look at our [configuration guide](choosing-unity-version.md) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="3807a-130">當您在專案中設定 MRTK 之後，像是相機的標準 Unity 遊戲物件就會立即立即獲得大規模的體驗。</span><span class="sxs-lookup"><span data-stu-id="3807a-130">Once you've setup MRTK in your project, standard Unity game objects like the camera will light up immediately for a seated-scale experience.</span></span> <span data-ttu-id="3807a-131">您可以在[座標系統](coordinate-systems-in-unity.md)頁面上找到變更應用程式體驗級別的指示。</span><span class="sxs-lookup"><span data-stu-id="3807a-131">You can find instructions on changing the experience scale of your application on the [coordinate systems](coordinate-systems-in-unity.md) page.</span></span>

## <a name="2-core-building-blocks"></a><span data-ttu-id="3807a-132">2.核心基本要素</span><span class="sxs-lookup"><span data-stu-id="3807a-132">2. Core building blocks</span></span>

<span data-ttu-id="3807a-133">混合實境應用程式的所有核心建置組塊都會以與其他 Unity API 一致的方式公開。</span><span class="sxs-lookup"><span data-stu-id="3807a-133">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="3807a-134">這些建置組塊是透過混合實境工具組提供的獨立功能。</span><span class="sxs-lookup"><span data-stu-id="3807a-134">These building blocks are available as standalone features and through the Mixed Reality Toolkit.</span></span> <span data-ttu-id="3807a-135">您目前可能不需用到所有功能，但建議您及早探索。</span><span class="sxs-lookup"><span data-stu-id="3807a-135">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="3807a-136">深入探討下列核心建置組塊後，您將了解如何讓包含多樣化功能的工具箱自行或透過 MRTK 整合到混合實境專案中。</span><span class="sxs-lookup"><span data-stu-id="3807a-136">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a Mixed Reality project by themselves or through MRTK.</span></span>

|  <span data-ttu-id="3807a-137">功能</span><span class="sxs-lookup"><span data-stu-id="3807a-137">Feature</span></span>  |  <span data-ttu-id="3807a-138">功能</span><span class="sxs-lookup"><span data-stu-id="3807a-138">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="3807a-139">相機</span><span class="sxs-lookup"><span data-stu-id="3807a-139">Camera</span></span>](../unity/camera-in-unity.md) | <span data-ttu-id="3807a-140">完整最佳化混合實境應用程式中的視覺品質和全像攝影穩定性</span><span class="sxs-lookup"><span data-stu-id="3807a-140">Fully optimize visual quality and hologram stability in your Mixed Reality apps</span></span> |
| [<span data-ttu-id="3807a-141">世界鎖定和空間錨點</span><span class="sxs-lookup"><span data-stu-id="3807a-141">World locking and spatial anchors</span></span>](spatial-anchors-in-unity.md) | <span data-ttu-id="3807a-142">解決穩定問題、攝影機調整，以及整合穩定的座標系統解決方案</span><span class="sxs-lookup"><span data-stu-id="3807a-142">Solve stabilization issues, camera adjustment, and integrate a stable coordinate system solution</span></span> |
| [<span data-ttu-id="3807a-143">共用體驗</span><span class="sxs-lookup"><span data-stu-id="3807a-143">Shared experiences</span></span>](shared-experiences-in-unity.md) | <span data-ttu-id="3807a-144">使用空間錨點共用，共同檢視空間中固定點上的相同全像投影，並與其互動</span><span class="sxs-lookup"><span data-stu-id="3807a-144">View and interact collectively with the same hologram at a fixed point in space using spatial anchor sharing</span></span> |
| [<span data-ttu-id="3807a-145">目光</span><span class="sxs-lookup"><span data-stu-id="3807a-145">Gaze</span></span>](../unity/gaze-in-unity.md) | <span data-ttu-id="3807a-146">讓使用者藉由注視全像投影而將其定為目標</span><span class="sxs-lookup"><span data-stu-id="3807a-146">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="3807a-147">運動控制器</span><span class="sxs-lookup"><span data-stu-id="3807a-147">Motion controllers</span></span>](../unity/motion-controllers-in-unity.md) | <span data-ttu-id="3807a-148">將空間動作新增至混合實境應用程式</span><span class="sxs-lookup"><span data-stu-id="3807a-148">Add spatial actions to your Mixed Reality apps</span></span> |
| [<span data-ttu-id="3807a-149">手勢</span><span class="sxs-lookup"><span data-stu-id="3807a-149">Gestures</span></span>](../unity/gestures-in-unity.md) | <span data-ttu-id="3807a-150">在混合實境體驗中使用手勢作為輸入</span><span class="sxs-lookup"><span data-stu-id="3807a-150">Use hand gestures as input in your Mixed Reality experiences</span></span> |
| [<span data-ttu-id="3807a-151">手部和眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="3807a-151">Hand and eye tracking</span></span>](../unity/hand-eye-in-unity.md) | <span data-ttu-id="3807a-152">將關節手部和眼睛追蹤輸入整合到您的使用者體驗中</span><span class="sxs-lookup"><span data-stu-id="3807a-152">Integrate articulated hand and eye tracking input into your user experience</span></span> |
| [<span data-ttu-id="3807a-153">空間對應</span><span class="sxs-lookup"><span data-stu-id="3807a-153">Spatial mapping</span></span>](../unity/spatial-mapping-in-unity.md) | <span data-ttu-id="3807a-154">透過虛擬網格重疊對應您的實體空間，以標示環境的界限</span><span class="sxs-lookup"><span data-stu-id="3807a-154">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="3807a-155">空間音效</span><span class="sxs-lookup"><span data-stu-id="3807a-155">Spatial sound</span></span>](../unity/spatial-sound-in-unity.md) | <span data-ttu-id="3807a-156">利用沉浸式 3D 音訊增強您的應用程式</span><span class="sxs-lookup"><span data-stu-id="3807a-156">Enhance your apps with immersive 3D audio</span></span> |
| [<span data-ttu-id="3807a-157">Text</span><span class="sxs-lookup"><span data-stu-id="3807a-157">Text</span></span>](../unity/text-in-unity.md) | <span data-ttu-id="3807a-158">取得可管理大小且具有效轉譯的清晰、高品質文字</span><span class="sxs-lookup"><span data-stu-id="3807a-158">Get sharp, high-quality text that has a manageable size and quality rendering</span></span> |
| [<span data-ttu-id="3807a-159">語音輸入</span><span class="sxs-lookup"><span data-stu-id="3807a-159">Voice input</span></span>](../unity/voice-input-in-unity.md) | <span data-ttu-id="3807a-160">擷取使用者說出的關鍵字、片語和指令</span><span class="sxs-lookup"><span data-stu-id="3807a-160">Capture spoken keywords, phrases, and dictation from your users</span></span>|

## <a name="3-advanced-features"></a><span data-ttu-id="3807a-161">3.進階功能</span><span class="sxs-lookup"><span data-stu-id="3807a-161">3. Advanced features</span></span>

<span data-ttu-id="3807a-162">在混合實境應用程式中各有作用的其他重要功能可透過 Unity API 來使用，不需要任何額外的封裝或設定。</span><span class="sxs-lookup"><span data-stu-id="3807a-162">Other key features that play a role in mixed reality applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="3807a-163">這些功能可以新增至 Unity 專案，且不一定需要先安裝 MRTK。</span><span class="sxs-lookup"><span data-stu-id="3807a-163">These features can be added to Unity projects with or without MRTK installed.</span></span> <span data-ttu-id="3807a-164">深入了解 Unity 提供的進階功能後，您將能夠建置更有深度的複雜混合實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="3807a-164">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex Mixed Reality apps.</span></span>

|  <span data-ttu-id="3807a-165">功能</span><span class="sxs-lookup"><span data-stu-id="3807a-165">Feature</span></span>  |  <span data-ttu-id="3807a-166">功能</span><span class="sxs-lookup"><span data-stu-id="3807a-166">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="3807a-167">相片攝影機</span><span class="sxs-lookup"><span data-stu-id="3807a-167">Photo video camera</span></span>](locatable-camera-in-unity.md) | <span data-ttu-id="3807a-168">在您的混合實境應用程式中擷取相片和影片內容</span><span class="sxs-lookup"><span data-stu-id="3807a-168">Capture photos and video content in your Mixed Reality application</span></span> |
| [<span data-ttu-id="3807a-169">對焦點</span><span class="sxs-lookup"><span data-stu-id="3807a-169">Focus point</span></span>](focus-point-in-unity.md) | <span data-ttu-id="3807a-170">為 HoloLens 提供有關於如何對目前顯示的全像投影最有效地執行穩定性的提示</span><span class="sxs-lookup"><span data-stu-id="3807a-170">Provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed</span></span> |
| [<span data-ttu-id="3807a-171">追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="3807a-171">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="3807a-172">處理您的裝置無法在應用程式環境的空間中找到本身所在位置的狀況</span><span class="sxs-lookup"><span data-stu-id="3807a-172">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="3807a-173">鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="3807a-173">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="3807a-174">在您的應用程式中取得實際環境和混合實境鍵盤的輸入</span><span class="sxs-lookup"><span data-stu-id="3807a-174">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

## <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="3807a-175">4.部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="3807a-175">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="3807a-176">當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是匯出和建置 Unity Visual Studio 解決方案。</span><span class="sxs-lookup"><span data-stu-id="3807a-176">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="3807a-177">有了該 VS 解決方案，您就可以在真正或模擬的裝置上，以三種方式之一來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="3807a-177">With that VS solution in hand, you can run your application in one of three ways on a real or simulated device.</span></span> <span data-ttu-id="3807a-178">在本節結束時，您將能夠在任何裝置或模擬器上部署您的應用程式，以符合您的開發需求。</span><span class="sxs-lookup"><span data-stu-id="3807a-178">By the end of this section, you'll be able to deploy your application on whichever device or emulator fits your development needs.</span></span>

* [<span data-ttu-id="3807a-179">HoloLens 或 Windows 混合實境沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="3807a-179">HoloLens or Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="3807a-180">HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="3807a-180">HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [<span data-ttu-id="3807a-181">Windows 混合實境沉浸式頭戴裝置模擬器</span><span class="sxs-lookup"><span data-stu-id="3807a-181">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="5-adding-services"></a><span data-ttu-id="3807a-182">5.新增服務</span><span class="sxs-lookup"><span data-stu-id="3807a-182">5. Adding services</span></span>

<span data-ttu-id="3807a-183">到了開發旅程的這個階段，您可能會想要新增服務，或是需要商業部署方面的協助。</span><span class="sxs-lookup"><span data-stu-id="3807a-183">At this point in your development journey you might be looking to add services or for a helping hand with commercial deployment.</span></span> <span data-ttu-id="3807a-184">整合 [Azure 雲端服務](../mixed-reality-cloud-services.md) 可讓您以主要方式來設定專案的等級。</span><span class="sxs-lookup"><span data-stu-id="3807a-184">Integrating [Azure Cloud Services](../mixed-reality-cloud-services.md) can level up your projects in a major way.</span></span> <span data-ttu-id="3807a-185">我們編譯了一些方便您探索及擴充混合實境知識的起點。</span><span class="sxs-lookup"><span data-stu-id="3807a-185">We've compiled a few starting points for you to explore and expand your Mixed Reality knowledge.</span></span>

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

<span data-ttu-id="3807a-186">針對其他可供您以自助方式新增至 Unity 專案的其他 Azure 服務，我們也提供了[完整的支援文件清單](../mixed-reality-cloud-services.md#standalone-unity-services)。</span><span class="sxs-lookup"><span data-stu-id="3807a-186">We also have a [comprehensive list of support documentation for additional Azure services](../mixed-reality-cloud-services.md#standalone-unity-services) that you can add to your Unity projects on a self-serve basis.</span></span>

## <a name="6-low-code-alternatives"></a><span data-ttu-id="3807a-187">6. 低程式碼替代方案</span><span class="sxs-lookup"><span data-stu-id="3807a-187">6. Low-code alternatives</span></span>

[!INCLUDE[](../includes/unity-low-code.md)]

## <a name="whats-next"></a><span data-ttu-id="3807a-188">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="3807a-188">What's next?</span></span>

<span data-ttu-id="3807a-189">開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。</span><span class="sxs-lookup"><span data-stu-id="3807a-189">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="3807a-190">完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。</span><span class="sxs-lookup"><span data-stu-id="3807a-190">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="3807a-191">請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！</span><span class="sxs-lookup"><span data-stu-id="3807a-191">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="3807a-192">移植</span><span class="sxs-lookup"><span data-stu-id="3807a-192">Porting</span></span>

<span data-ttu-id="3807a-193">如果您有想要移植的現有應用程式，您接下來即應參考下列文章：</span><span class="sxs-lookup"><span data-stu-id="3807a-193">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="3807a-194">HoloToolkit/MRTK 至 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="3807a-194">HoloToolkit/MRTK to MRTK v2</span></span>](../porting-apps/porting-hl1-hl2.md)
* [<span data-ttu-id="3807a-195">沈浸式應用程式的移植指南</span><span class="sxs-lookup"><span data-stu-id="3807a-195">Porting guide for immersive apps</span></span>](../porting-apps/porting-guides.md)
* [<span data-ttu-id="3807a-196">輸入移植指南</span><span class="sxs-lookup"><span data-stu-id="3807a-196">Input porting guide</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a><span data-ttu-id="3807a-197">教學課程</span><span class="sxs-lookup"><span data-stu-id="3807a-197">Tutorials</span></span>

<span data-ttu-id="3807a-198">如果您想要將特定的混合實境功能新增至應用程式，我們策劃了數個教學課程，可逐步引導您完成相關程序。</span><span class="sxs-lookup"><span data-stu-id="3807a-198">If you're looking to add specific Mixed Reality features to your applications, we have several curated tutorials that can run you through the process from end-to-end.</span></span> <span data-ttu-id="3807a-199">以下列出最多人使用的 HoloLens 2 和 HoloLens (第 1 代) 內容，但您可以瀏覽教學課程概觀以了解完整的系列。</span><span class="sxs-lookup"><span data-stu-id="3807a-199">Our most popular HoloLens 2 and HoloLens (1st Gen) content is listed below, but you can find the entire collection by visiting the tutorials overview.</span></span>

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a><span data-ttu-id="3807a-200">其他資源</span><span class="sxs-lookup"><span data-stu-id="3807a-200">Additional resources</span></span>

<span data-ttu-id="3807a-201">在您自行進入混合實境的世界之前，建議您先參閱下列 MRTK 相關文件。</span><span class="sxs-lookup"><span data-stu-id="3807a-201">Before going out into the world of mixed reality on your own, we recommend taking a look at the MRTK-related documentation listed below.</span></span> <span data-ttu-id="3807a-202">這些文章是您深入了解 MRTK 運作方式的絕佳切入點，同時也提供如何讓應用程式更具效能的深入解析。</span><span class="sxs-lookup"><span data-stu-id="3807a-202">These articles are great jumping off points for understanding how MRTK works in greater detail and will give you insight into making your app more performant.</span></span>

|  <span data-ttu-id="3807a-203">主題</span><span class="sxs-lookup"><span data-stu-id="3807a-203">Topic</span></span>  |  <span data-ttu-id="3807a-204">描述</span><span class="sxs-lookup"><span data-stu-id="3807a-204">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="3807a-205">MRTK 架構概觀</span><span class="sxs-lookup"><span data-stu-id="3807a-205">MRTK Architecture overview</span></span>](/windows/mixed-reality/mrtk-unity/architecture/overview) | <span data-ttu-id="3807a-206">深入了解 MRTK SDK 在您的專案中如何運作</span><span class="sxs-lookup"><span data-stu-id="3807a-206">Get a deeper understanding of how the MRTK SDK works in your projects</span></span> |
| [<span data-ttu-id="3807a-207">設定和效能</span><span class="sxs-lookup"><span data-stu-id="3807a-207">Settings and performance</span></span>](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started) | <span data-ttu-id="3807a-208">分析您的應用程式、更新 Unity 設定，並取得最理想的全像投影穩定效能</span><span class="sxs-lookup"><span data-stu-id="3807a-208">Profile your app, update your Unity settings, and get the best hologram stabilization performance available</span></span> |
| [<span data-ttu-id="3807a-209">開始使用 MRTK + XR</span><span class="sxs-lookup"><span data-stu-id="3807a-209">Getting started with MRTK + XR</span></span>](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk) | <span data-ttu-id="3807a-210">轉移至 Unity 所提供的替代 XR 管線</span><span class="sxs-lookup"><span data-stu-id="3807a-210">Transfer over to the alternative XR pipeline provided by Unity</span></span> |

### <a name="unity-resources"></a><span data-ttu-id="3807a-211">Unity 資源</span><span class="sxs-lookup"><span data-stu-id="3807a-211">Unity resources</span></span>

<span data-ttu-id="3807a-212">除了可以在 docs.microsoft.com 上取得的本文件之外，Unity 還會隨著 Unity 編輯器一起安裝 Windows Mixed Reality 功能的文件。</span><span class="sxs-lookup"><span data-stu-id="3807a-212">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="3807a-213">Unity 提供的文件包含兩個不同的部分。</span><span class="sxs-lookup"><span data-stu-id="3807a-213">The Unity provided documentation includes two separate sections.</span></span>

|  <span data-ttu-id="3807a-214">資源</span><span class="sxs-lookup"><span data-stu-id="3807a-214">Resource</span></span>  |  <span data-ttu-id="3807a-215">描述</span><span class="sxs-lookup"><span data-stu-id="3807a-215">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="3807a-216">指令碼參考</span><span class="sxs-lookup"><span data-stu-id="3807a-216">Scripting reference</span></span>](https://docs.unity3d.com/ScriptReference/) | <span data-ttu-id="3807a-217">這部分的文件包含 Unity 所提供之 API 指令碼的詳細資料，並且可從 Unity 編輯器線上存取，只要按一下 [說明] > [指令碼參考] 即可</span><span class="sxs-lookup"><span data-stu-id="3807a-217">This section of the documentation contains details of the scripting API that Unity provides and is accessible online from the Unity Editor by clicking **Help > Scripting Reference**</span></span> |
| [<span data-ttu-id="3807a-218">手動</span><span class="sxs-lookup"><span data-stu-id="3807a-218">Manual</span></span>](https://docs.unity3d.com/Manual/index.html) | <span data-ttu-id="3807a-219">此手冊旨在協助您了解如何使用 Unity (包括基本與進階技術)，並且可從 Unity 編輯器線上存取，只要按一下 [說明] > [指令碼參考] 即可</span><span class="sxs-lookup"><span data-stu-id="3807a-219">This manual is designed to help you learn how to use Unity, from basic to advanced techniques, and is accessible online or from the Unity Editor by clicking **Help > Manual**</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="3807a-220">探索 MRTK</span><span class="sxs-lookup"><span data-stu-id="3807a-220">Explore MRTK</span></span>](mrtk-getting-started.md)

## <a name="have-feedback"></a><span data-ttu-id="3807a-221">有任何意見嗎？</span><span class="sxs-lookup"><span data-stu-id="3807a-221">Have feedback?</span></span>

<span data-ttu-id="3807a-222">您可以在 [Unity 論壇](https://aka.ms/unityforums)藉由標記 **Microsoft** 和下列標籤組合來找到我們，進而協助我們了解您提供意見反應的外掛程式：</span><span class="sxs-lookup"><span data-stu-id="3807a-222">You can find us on the [Unity Forums](https://aka.ms/unityforums) by tagging **Microsoft** and a combination of the following tags to help us understand what plugin you're providing feedback for:</span></span>

* <span data-ttu-id="3807a-223">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3807a-223">HoloLens 2</span></span> 
* <span data-ttu-id="3807a-224">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3807a-224">Windows Mixed Reality</span></span>
* <span data-ttu-id="3807a-225">OpenXR</span><span class="sxs-lookup"><span data-stu-id="3807a-225">OpenXR</span></span>
* <span data-ttu-id="3807a-226">XRSDK</span><span class="sxs-lookup"><span data-stu-id="3807a-226">XRSDK</span></span>
* <span data-ttu-id="3807a-227">傳統 XR</span><span class="sxs-lookup"><span data-stu-id="3807a-227">Legacy XR</span></span>

## <a name="see-also"></a><span data-ttu-id="3807a-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3807a-228">See also</span></span>

* [<span data-ttu-id="3807a-229">混合實境工具組 v2</span><span class="sxs-lookup"><span data-stu-id="3807a-229">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="3807a-230">MR Basics 100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="3807a-230">MR Basics 100: Getting started with Unity</span></span>](tutorials/holograms-100.md)
* [<span data-ttu-id="3807a-231">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="3807a-231">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="3807a-232">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="3807a-232">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="3807a-233">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="3807a-233">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="3807a-234">搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式</span><span class="sxs-lookup"><span data-stu-id="3807a-234">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="3807a-235">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3807a-235">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="3807a-236">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="3807a-236">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="3807a-237">移植指南</span><span class="sxs-lookup"><span data-stu-id="3807a-237">Porting guides</span></span>](../porting-apps/porting-guides.md)
