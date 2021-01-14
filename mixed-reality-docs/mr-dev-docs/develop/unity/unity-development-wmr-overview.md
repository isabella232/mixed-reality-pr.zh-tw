---
title: 適用於 VR 的 Unity 開發
description: 開始在 Unity 中建立適用於 VR 和 Windows Mixed Reality 沉浸式頭戴裝置的混合實境應用程式。
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合實境, 開發, 開始使用, 新專案, 移植, 功能, 相機, 模擬, 模擬, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 什麼是虛擬實境, 什麼是擴增實境, MRTK, 混合實境工具組, 語音輸入, 定位相機, 模擬器, Azure, 教學課程
ms.openlocfilehash: ba63f137e90b68345f3e5bbb831aba6abd6fe538
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040567"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="caea2-104">適用於 VR 和 Windows Mixed Reality 的 Unity 開發</span><span class="sxs-lookup"><span data-stu-id="caea2-104">Unity development for VR and Windows Mixed Reality</span></span>

![Unity 橫幅標誌](../images/unity_logo_banner.png)

<span data-ttu-id="caea2-106">如果您是首次接觸 Unity，建議您先探索 Unity 學習平台上的入門級[教學課程](https://unity3d.com/learn/tutorials)，再繼續操作。</span><span class="sxs-lookup"><span data-stu-id="caea2-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="caea2-107">您也可以造訪 [Unity Mixed Reality 論壇](https://forum.unity3d.com/forums/hololens.102/)，與建置混合實境應用程式的線上社群交流。</span><span class="sxs-lookup"><span data-stu-id="caea2-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="caea2-108">您絕對想不到在這裡會發現哪些絕佳的資產或解決方案。</span><span class="sxs-lookup"><span data-stu-id="caea2-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="caea2-109">當您準備好開始使用 MRTK 時，請前往以下開發檢查點！</span><span class="sxs-lookup"><span data-stu-id="caea2-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="caea2-110">如果您想要將現有的 Unity 專案導入 Windows Mixed Reality 沉浸式頭戴裝置中，請參閱我們的 **[移植指南](../porting-apps/porting-overview.md)** 。</span><span class="sxs-lookup"><span data-stu-id="caea2-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="caea2-111">開發檢查點</span><span class="sxs-lookup"><span data-stu-id="caea2-111">Development checkpoints</span></span>

<span data-ttu-id="caea2-112">使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。</span><span class="sxs-lookup"><span data-stu-id="caea2-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="caea2-113">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="caea2-113">1. Getting started</span></span>

<span data-ttu-id="caea2-114">您需要針對 Windows Mixed Reality 和 VR 開發手動變更一小組 Unity 設定。</span><span class="sxs-lookup"><span data-stu-id="caea2-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR developoment.</span></span> <span data-ttu-id="caea2-115">這些設定分成兩個類別：每個專案和每個場景。</span><span class="sxs-lookup"><span data-stu-id="caea2-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="caea2-116">在本節結束時，您將具有工具和專案設定，可以開始建立自己的應用程式！</span><span class="sxs-lookup"><span data-stu-id="caea2-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="caea2-117">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="caea2-117">Checkpoint</span></span>  |  <span data-ttu-id="caea2-118">結果</span><span class="sxs-lookup"><span data-stu-id="caea2-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="caea2-119">安裝最新工具</span><span class="sxs-lookup"><span data-stu-id="caea2-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="caea2-120">下載並安裝最新的 Unity 套件，並設定您的混合實境專案</span><span class="sxs-lookup"><span data-stu-id="caea2-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="caea2-121">針對 WMR 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="caea2-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="caea2-122">了解如何建置可在全像攝影和 VR 顯示裝置上呈現數位內容的應用程式</span><span class="sxs-lookup"><span data-stu-id="caea2-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="caea2-123">2.核心基本要素</span><span class="sxs-lookup"><span data-stu-id="caea2-123">2. Core building blocks</span></span>

<span data-ttu-id="caea2-124">開始新的沉浸式專案之後，您需要一些基本的建構元素來開發沉浸式應用程式。</span><span class="sxs-lookup"><span data-stu-id="caea2-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="caea2-125">混合實境應用程式的所有核心建置組塊都會以與其他 Unity API 一致的方式公開。</span><span class="sxs-lookup"><span data-stu-id="caea2-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="caea2-126">您目前可能不需用到所有功能，但建議您及早探索。</span><span class="sxs-lookup"><span data-stu-id="caea2-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="caea2-127">深入探討下列核心建構元素後，您將了解如何將包含多樣化功能的工具箱整合到 VR 專案中。</span><span class="sxs-lookup"><span data-stu-id="caea2-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-platform-capabilities-and-apis"></a><span data-ttu-id="caea2-128">3.平台功能和 API</span><span class="sxs-lookup"><span data-stu-id="caea2-128">3. Platform capabilities and APIs</span></span>

<span data-ttu-id="caea2-129">在沉浸式應用程式中各有作用的其他重要功能可透過 Unity API 來使用，不需要任何額外的封裝或設定。</span><span class="sxs-lookup"><span data-stu-id="caea2-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="caea2-130">深入了解 Unity 提供的進階功能後，您將能夠建置更有深度的複雜 VR 應用程式。</span><span class="sxs-lookup"><span data-stu-id="caea2-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="caea2-131">功能</span><span class="sxs-lookup"><span data-stu-id="caea2-131">Feature</span></span>  |  <span data-ttu-id="caea2-132">功能</span><span class="sxs-lookup"><span data-stu-id="caea2-132">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="caea2-133">追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="caea2-133">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="caea2-134">處理您的裝置無法在應用程式環境的空間中找到本身所在位置的狀況</span><span class="sxs-lookup"><span data-stu-id="caea2-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="caea2-135">鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="caea2-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="caea2-136">在您的應用程式中取得實際環境和混合實境鍵盤的輸入</span><span class="sxs-lookup"><span data-stu-id="caea2-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="caea2-137">4.部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="caea2-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="caea2-138">當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是匯出和建置 Unity Visual Studio 解決方案。</span><span class="sxs-lookup"><span data-stu-id="caea2-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="caea2-139">有了該 VS 解決方案，您就可以在真正或模擬的裝置上執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="caea2-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="caea2-140">在本節結束時，您將能夠在裝置或模擬器上部署您的應用程式，以符合您的開發需求。</span><span class="sxs-lookup"><span data-stu-id="caea2-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="caea2-141">Windows Mixed Reality 沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="caea2-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="caea2-142">Windows 混合實境沉浸式頭戴裝置模擬器</span><span class="sxs-lookup"><span data-stu-id="caea2-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="caea2-143">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="caea2-143">What's next?</span></span>

<span data-ttu-id="caea2-144">開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。</span><span class="sxs-lookup"><span data-stu-id="caea2-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="caea2-145">完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。</span><span class="sxs-lookup"><span data-stu-id="caea2-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="caea2-146">請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！</span><span class="sxs-lookup"><span data-stu-id="caea2-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="caea2-147">移植</span><span class="sxs-lookup"><span data-stu-id="caea2-147">Porting</span></span>

<span data-ttu-id="caea2-148">如果您有想要移植的現有應用程式，您接下來即應參考下列文章：</span><span class="sxs-lookup"><span data-stu-id="caea2-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="caea2-149">將 VR 應用程式移植到 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="caea2-149">Porting VR apps to Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project)
* [<span data-ttu-id="caea2-150">更新 Windows Mixed Reality 的 SteamVR 應用程式</span><span class="sxs-lookup"><span data-stu-id="caea2-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)

### <a name="additional-resources"></a><span data-ttu-id="caea2-151">其他資源</span><span class="sxs-lookup"><span data-stu-id="caea2-151">Additional resources</span></span>

<span data-ttu-id="caea2-152">在您自行進入混合實境的世界之前，建議您先參閱下列額外文件。</span><span class="sxs-lookup"><span data-stu-id="caea2-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="caea2-153">VR 愛好者指南</span><span class="sxs-lookup"><span data-stu-id="caea2-153">VR enthusiast guide</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="caea2-154">Unity Asset Store</span><span class="sxs-lookup"><span data-stu-id="caea2-154">Unity Asset Store</span></span>](https://www.assetstore.unity3d.com)

## <a name="see-also"></a><span data-ttu-id="caea2-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caea2-155">See also</span></span> 

* [<span data-ttu-id="caea2-156">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="caea2-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="caea2-157">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="caea2-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="caea2-158">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="caea2-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="caea2-159">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="caea2-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
