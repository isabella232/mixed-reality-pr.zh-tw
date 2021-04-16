---
title: 適用於 VR 的 Unity 開發
description: 開始在 Unity 中建立適用於 VR 和 Windows Mixed Reality 沉浸式頭戴裝置的混合實境應用程式。
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合實境, 開發, 開始使用, 新專案, 移植, 功能, 相機, 模擬, 模擬, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 什麼是虛擬實境, 什麼是擴增實境, MRTK, 混合實境工具組, 語音輸入, 定位相機, 模擬器, Azure, 教學課程
ms.openlocfilehash: 50300ff08dd06c5fc250bc93979d537e10b38044
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528716"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="99f59-104">適用於 VR 和 Windows Mixed Reality 的 Unity 開發</span><span class="sxs-lookup"><span data-stu-id="99f59-104">Unity development for VR and Windows Mixed Reality</span></span>

![Unity 橫幅標誌](../images/unity_logo_banner.png)

<span data-ttu-id="99f59-106">如果您是首次接觸 Unity，建議您先探索 Unity 學習平台上的入門級[教學課程](https://unity3d.com/learn/tutorials)，再繼續操作。</span><span class="sxs-lookup"><span data-stu-id="99f59-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="99f59-107">您也可以造訪 [Unity Mixed Reality 論壇](https://forum.unity3d.com/forums/hololens.102/)，與建置混合實境應用程式的線上社群交流。</span><span class="sxs-lookup"><span data-stu-id="99f59-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="99f59-108">您絕對想不到在這裡會發現哪些絕佳的資產或解決方案。</span><span class="sxs-lookup"><span data-stu-id="99f59-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="99f59-109">當您準備好開始使用 MRTK 時，請前往以下開發檢查點！</span><span class="sxs-lookup"><span data-stu-id="99f59-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99f59-110">如果您想要將現有的 Unity 專案導入 Windows Mixed Reality 沉浸式頭戴裝置中，請參閱我們的 **[移植指南](../porting-apps/porting-overview.md)** 。</span><span class="sxs-lookup"><span data-stu-id="99f59-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="99f59-111">開發檢查點</span><span class="sxs-lookup"><span data-stu-id="99f59-111">Development checkpoints</span></span>

<span data-ttu-id="99f59-112">使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。</span><span class="sxs-lookup"><span data-stu-id="99f59-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="99f59-113">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="99f59-113">1. Getting started</span></span>

<span data-ttu-id="99f59-114">您需要針對 Windows Mixed Reality 和 VR 開發進行手動變更的一小部分 Unity 設定。</span><span class="sxs-lookup"><span data-stu-id="99f59-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR development.</span></span> <span data-ttu-id="99f59-115">這些設定分成兩個類別：每個專案和每個場景。</span><span class="sxs-lookup"><span data-stu-id="99f59-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="99f59-116">在本節結束時，您將具有工具和專案設定，可以開始建立自己的應用程式！</span><span class="sxs-lookup"><span data-stu-id="99f59-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="99f59-117">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="99f59-117">Checkpoint</span></span>  |  <span data-ttu-id="99f59-118">結果</span><span class="sxs-lookup"><span data-stu-id="99f59-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="99f59-119">安裝最新工具</span><span class="sxs-lookup"><span data-stu-id="99f59-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="99f59-120">下載並安裝最新的 Unity 套件，並設定您的混合實境專案</span><span class="sxs-lookup"><span data-stu-id="99f59-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="99f59-121">針對 WMR 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="99f59-121">Configuring your project for WMR</span></span>](windows-xr-plugin.md) | <span data-ttu-id="99f59-122">了解如何建置可在全像攝影和 VR 顯示裝置上呈現數位內容的應用程式</span><span class="sxs-lookup"><span data-stu-id="99f59-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="99f59-123">如需設定專案的詳細資訊，請參閱我們的 Unity 專案設定 [指南](choosing-unity-version.md) 。</span><span class="sxs-lookup"><span data-stu-id="99f59-123">Check out our Unity project [configuration guide](choosing-unity-version.md) for more information on setting up your projects.</span></span>

### <a name="2-core-building-blocks"></a><span data-ttu-id="99f59-124">2.核心基本要素</span><span class="sxs-lookup"><span data-stu-id="99f59-124">2. Core building blocks</span></span>

<span data-ttu-id="99f59-125">開始新的沉浸式專案之後，您需要一些基本的建構元素來開發沉浸式應用程式。</span><span class="sxs-lookup"><span data-stu-id="99f59-125">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="99f59-126">混合實境應用程式的所有核心建置組塊都會以與其他 Unity API 一致的方式公開。</span><span class="sxs-lookup"><span data-stu-id="99f59-126">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="99f59-127">您目前可能不需用到所有功能，但建議您及早探索。</span><span class="sxs-lookup"><span data-stu-id="99f59-127">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="99f59-128">深入探討下列核心建構元素後，您將了解如何將包含多樣化功能的工具箱整合到 VR 專案中。</span><span class="sxs-lookup"><span data-stu-id="99f59-128">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

|  <span data-ttu-id="99f59-129">功能</span><span class="sxs-lookup"><span data-stu-id="99f59-129">Feature</span></span>  |  <span data-ttu-id="99f59-130">功能</span><span class="sxs-lookup"><span data-stu-id="99f59-130">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="99f59-131">相機</span><span class="sxs-lookup"><span data-stu-id="99f59-131">Camera</span></span>](../unity/camera-in-unity.md) | <span data-ttu-id="99f59-132">完整最佳化混合實境應用程式中的視覺品質和全像攝影穩定性</span><span class="sxs-lookup"><span data-stu-id="99f59-132">Fully optimize visual quality and hologram stability in your Mixed Reality apps</span></span> |
| [<span data-ttu-id="99f59-133">世界鎖定和空間錨點</span><span class="sxs-lookup"><span data-stu-id="99f59-133">World locking and spatial anchors</span></span>](spatial-anchors-in-unity.md) | <span data-ttu-id="99f59-134">解決穩定問題、攝影機調整，以及整合穩定的座標系統解決方案</span><span class="sxs-lookup"><span data-stu-id="99f59-134">Solve stabilization issues, camera adjustment, and integrate a stable coordinate system solution</span></span> || [<span data-ttu-id="99f59-135">運動控制器</span><span class="sxs-lookup"><span data-stu-id="99f59-135">Motion controllers</span></span>](../unity/motion-controllers-in-unity.md) | <span data-ttu-id="99f59-136">將空間動作新增至混合實境應用程式</span><span class="sxs-lookup"><span data-stu-id="99f59-136">Add spatial actions to your Mixed Reality apps</span></span> |
| [<span data-ttu-id="99f59-137">手勢</span><span class="sxs-lookup"><span data-stu-id="99f59-137">Gestures</span></span>](../unity/gestures-in-unity.md) | <span data-ttu-id="99f59-138">在混合實境體驗中使用手勢作為輸入</span><span class="sxs-lookup"><span data-stu-id="99f59-138">Use hand gestures as input in your Mixed Reality experiences</span></span> |
| [<span data-ttu-id="99f59-139">空間音效</span><span class="sxs-lookup"><span data-stu-id="99f59-139">Spatial sound</span></span>](../unity/spatial-sound-in-unity.md) | <span data-ttu-id="99f59-140">利用沉浸式 3D 音訊增強您的應用程式</span><span class="sxs-lookup"><span data-stu-id="99f59-140">Enhance your apps with immersive 3D audio</span></span> |
| [<span data-ttu-id="99f59-141">Text</span><span class="sxs-lookup"><span data-stu-id="99f59-141">Text</span></span>](../unity/text-in-unity.md) | <span data-ttu-id="99f59-142">取得可管理大小且具有效轉譯的清晰、高品質文字</span><span class="sxs-lookup"><span data-stu-id="99f59-142">Get sharp, high-quality text that has a manageable size and quality rendering</span></span> |
| [<span data-ttu-id="99f59-143">語音輸入</span><span class="sxs-lookup"><span data-stu-id="99f59-143">Voice input</span></span>](../unity/voice-input-in-unity.md) | <span data-ttu-id="99f59-144">擷取使用者說出的關鍵字、片語和指令</span><span class="sxs-lookup"><span data-stu-id="99f59-144">Capture spoken keywords, phrases, and dictation from your users</span></span>|

### <a name="3-advanced-features"></a><span data-ttu-id="99f59-145">3.進階功能</span><span class="sxs-lookup"><span data-stu-id="99f59-145">3. Advanced features</span></span>

<span data-ttu-id="99f59-146">在沉浸式應用程式中各有作用的其他重要功能可透過 Unity API 來使用，不需要任何額外的封裝或設定。</span><span class="sxs-lookup"><span data-stu-id="99f59-146">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="99f59-147">深入了解 Unity 提供的進階功能後，您將能夠建置更有深度的複雜 VR 應用程式。</span><span class="sxs-lookup"><span data-stu-id="99f59-147">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="99f59-148">功能</span><span class="sxs-lookup"><span data-stu-id="99f59-148">Feature</span></span>  |  <span data-ttu-id="99f59-149">功能</span><span class="sxs-lookup"><span data-stu-id="99f59-149">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="99f59-150">追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="99f59-150">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="99f59-151">處理您的裝置無法在應用程式環境的空間中找到本身所在位置的狀況</span><span class="sxs-lookup"><span data-stu-id="99f59-151">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="99f59-152">鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="99f59-152">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="99f59-153">在您的應用程式中取得實際環境和混合實境鍵盤的輸入</span><span class="sxs-lookup"><span data-stu-id="99f59-153">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="99f59-154">4.部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="99f59-154">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="99f59-155">當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是匯出和建置 Unity Visual Studio 解決方案。</span><span class="sxs-lookup"><span data-stu-id="99f59-155">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="99f59-156">有了該 VS 解決方案，您就可以在真正或模擬的裝置上執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="99f59-156">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="99f59-157">在本節結束時，您將能夠在裝置或模擬器上部署您的應用程式，以符合您的開發需求。</span><span class="sxs-lookup"><span data-stu-id="99f59-157">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="99f59-158">Windows Mixed Reality 沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="99f59-158">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="99f59-159">Windows 混合實境沉浸式頭戴裝置模擬器</span><span class="sxs-lookup"><span data-stu-id="99f59-159">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="99f59-160">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="99f59-160">What's next?</span></span>

<span data-ttu-id="99f59-161">開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。</span><span class="sxs-lookup"><span data-stu-id="99f59-161">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="99f59-162">完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。</span><span class="sxs-lookup"><span data-stu-id="99f59-162">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="99f59-163">請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！</span><span class="sxs-lookup"><span data-stu-id="99f59-163">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="99f59-164">移植</span><span class="sxs-lookup"><span data-stu-id="99f59-164">Porting</span></span>

<span data-ttu-id="99f59-165">如果您有想要移植的現有應用程式，您接下來即應參考下列文章：</span><span class="sxs-lookup"><span data-stu-id="99f59-165">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="99f59-166">將 VR 應用程式移植到 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="99f59-166">Porting VR apps to Windows Mixed Reality</span></span>](../porting-apps/porting-guides.md?tabs=project)
* [<span data-ttu-id="99f59-167">更新 Windows Mixed Reality 的 SteamVR 應用程式</span><span class="sxs-lookup"><span data-stu-id="99f59-167">Updating SteamVR apps for Windows Mixed Reality</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a><span data-ttu-id="99f59-168">其他資源</span><span class="sxs-lookup"><span data-stu-id="99f59-168">Additional resources</span></span>

<span data-ttu-id="99f59-169">在您自行進入混合實境的世界之前，建議您先參閱下列額外文件。</span><span class="sxs-lookup"><span data-stu-id="99f59-169">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="99f59-170">VR 愛好者指南</span><span class="sxs-lookup"><span data-stu-id="99f59-170">VR enthusiast guide</span></span>](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="99f59-171">Unity Asset Store</span><span class="sxs-lookup"><span data-stu-id="99f59-171">Unity Asset Store</span></span>](https://assetstore.unity.com)

## <a name="see-also"></a><span data-ttu-id="99f59-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99f59-172">See also</span></span> 

* [<span data-ttu-id="99f59-173">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="99f59-173">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="99f59-174">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="99f59-174">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="99f59-175">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="99f59-175">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="99f59-176">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="99f59-176">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)