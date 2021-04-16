---
title: Unity 中的世界鎖定和空間錨點
description: 瞭解如何在 Unity 混合現實應用程式中使用世界鎖定工具和空間錨點。
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity、空間錨點、錨定存放區、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、世界鎖定工具、全像影像
ms.openlocfilehash: 4fc982244a766bb34f15b356d608f2aad18f7a88
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528790"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a><span data-ttu-id="007b4-104">Unity 中的世界鎖定和空間錨點</span><span class="sxs-lookup"><span data-stu-id="007b4-104">World locking and spatial anchors in Unity</span></span>

![全球鎖定工具主圖影像](images/wlt-img-01.jpeg)

<span data-ttu-id="007b4-106">讓您的全像坐放在原處、與您一起移動，或是在某些情況下，相對於其他的全像是其他的全像是建立混合現實應用程式的一大部分。</span><span class="sxs-lookup"><span data-stu-id="007b4-106">Getting your holograms to stay in place, move with you, or in some cases position themselves relative to other holograms is a big part of creating Mixed Reality applications.</span></span> <span data-ttu-id="007b4-107">本文將引導您使用世界鎖定工具的建議解決方案，但我們也會討論如何在 Unity 專案中手動設定空間錨點。</span><span class="sxs-lookup"><span data-stu-id="007b4-107">This article will take you through our recommended solution using World Locking Tools, but we'll also cover manually setting up spatial anchors in your Unity projects.</span></span> <span data-ttu-id="007b4-108">在我們跳到任何程式碼之前，請務必先瞭解 Unity 如何處理其本身引擎中的座標空間和錨點。</span><span class="sxs-lookup"><span data-stu-id="007b4-108">Before we jump into any code, it's important to understand how Unity handles coordinate space and anchors in its own engine.</span></span>

## <a name="world-scale-coordinate-systems"></a><span data-ttu-id="007b4-109">全球規模座標系統</span><span class="sxs-lookup"><span data-stu-id="007b4-109">World-scale coordinate systems</span></span>

<span data-ttu-id="007b4-110">現在，在撰寫遊戲、資料視覺效果應用程式或虛擬實境應用程式時，一般的方法是建立一個絕對 **全局座標系統** ，讓所有其他座標都能可靠地對應回。</span><span class="sxs-lookup"><span data-stu-id="007b4-110">Today, when writing games, data visualization apps, or virtual reality apps, the typical approach is to establish one absolute **world coordinate system** that all other coordinates can reliably map back to.</span></span> <span data-ttu-id="007b4-111">在該環境中，您一律可以尋找穩定的轉換，以定義該世界中任何兩個物件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="007b4-111">In that environment, you can always find a stable transform that defines a relationship between any two objects in that world.</span></span> <span data-ttu-id="007b4-112">如果您未移動這些物件，其相對轉換一律會維持不變。</span><span class="sxs-lookup"><span data-stu-id="007b4-112">If you didn't move those objects, their relative transforms would always remain the same.</span></span> <span data-ttu-id="007b4-113">在轉譯單純的虛擬世界（您事先知道所有幾何）時，這種全域座標系統很容易就會出現。</span><span class="sxs-lookup"><span data-stu-id="007b4-113">This kind of global coordinate system is easy to get right when rendering a purely virtual world where you know all of the geometry in advance.</span></span> <span data-ttu-id="007b4-114">現今的房間規模的 VR 應用程式通常會建立這種絕對房間縮放座標系統及其原點。</span><span class="sxs-lookup"><span data-stu-id="007b4-114">Room-scale VR apps today typically establish this kind of absolute room-scale coordinate system with its origin on the floor.</span></span>

<span data-ttu-id="007b4-115">相反地，非網路共用的混合現實裝置（例如 HoloLens）對世界有動態的感應器驅動理解，會持續調整使用者周圍環境的知識，因為它們會在整個建築樓層中逐步進行許多計量。</span><span class="sxs-lookup"><span data-stu-id="007b4-115">In contrast, an untethered mixed reality device such as HoloLens has a dynamic sensor-driven understanding of the world, continuously adjusting its knowledge over time of the user's surroundings as they walk many meters across an entire floor of a building.</span></span> <span data-ttu-id="007b4-116">在全球規模的體驗中，如果您將所有的全像放在全面固定的座標系統中，這些的全像離開會在一段時間後結束。</span><span class="sxs-lookup"><span data-stu-id="007b4-116">In a world-scale experience, if you placed all your holograms in a naive rigid coordinate system, those holograms would end up drifting over time, either based on the world or relative to each other.</span></span>

<span data-ttu-id="007b4-117">例如，耳機目前可能會認為世界上有兩個位置彼此之間有4個度量，然後在稍後調整該瞭解，並瞭解這些位置其實是3.9 計量。</span><span class="sxs-lookup"><span data-stu-id="007b4-117">For example, the headset may currently believe two locations in the world to be 4 meters apart, and then later refine that understanding, learning that the locations are in fact 3.9 meters apart.</span></span> <span data-ttu-id="007b4-118">如果這些全息片一開始在單一固定座標系統中放置4個計量，則其中一個會從真實世界一直顯示0.1 計量。</span><span class="sxs-lookup"><span data-stu-id="007b4-118">If those holograms had initially been placed 4 meters apart in a single rigid coordinate system, one of them would then always appear 0.1 meters off from the real world.</span></span>

<span data-ttu-id="007b4-119">您可以手動將 **空間錨點** 放置在 Unity 中，以在使用者為行動裝置時，維持實體世界中的全息圖位置，而這犧牲虛擬世界內的自我一致性。</span><span class="sxs-lookup"><span data-stu-id="007b4-119">You can manually place **spatial anchors** in Unity to maintain a hologram's position in the physical world when the user is mobile - however, this sacrifices the self-consistency within the virtual world.</span></span> <span data-ttu-id="007b4-120">不同的錨點會不斷地彼此間移動，而且也會在全域座標空間中移動。</span><span class="sxs-lookup"><span data-stu-id="007b4-120">Different anchors are constantly moving in relation to one another, and are also moving through the global coordinate space.</span></span> <span data-ttu-id="007b4-121">在此案例中，像是版面配置這樣簡單的工作會變得很困難，而物理模擬也</span><span class="sxs-lookup"><span data-stu-id="007b4-121">In this scenario, simple tasks like layout become difficult and physics simulation problematic.</span></span>

<span data-ttu-id="007b4-122">**世界鎖定工具** 為您提供兩種世界的最佳選擇，在使用者四處移動的情況下，使用內部提供的空間錨點，在整個虛擬場景中進行穩定的固定座標系統。</span><span class="sxs-lookup"><span data-stu-id="007b4-122">**World Locking Tools** gets you the best of both worlds, stabilizing a single rigid coordinate system using an internal supply of spatial anchors spread throughout the virtual scene as the user moves around.</span></span> <span data-ttu-id="007b4-123">這些工具會分析相機的座標和每個畫面格的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="007b4-123">The tools analyze the coordinates of the camera and those spatial anchors every frame.</span></span> <span data-ttu-id="007b4-124">這些工具不會變更世界中所有專案的座標，以彌補使用者的標頭中的校正，而是改為修正標頭的座標。</span><span class="sxs-lookup"><span data-stu-id="007b4-124">Instead of changing the coordinates of everything in the world to compensate for the corrections in the coordinates of the user's head, the tools just fix the head's coordinates instead.</span></span>

## <a name="choosing-your-world-locking-approach"></a><span data-ttu-id="007b4-125">選擇您的世界鎖定方法</span><span class="sxs-lookup"><span data-stu-id="007b4-125">Choosing your world locking approach</span></span>

* <span data-ttu-id="007b4-126">**我們的建議** 是使用 **世界鎖定工具** ，來滿足您所有的全像全像位置需求。</span><span class="sxs-lookup"><span data-stu-id="007b4-126">**Our recommendation** is to use **World Locking Tools** for all your hologram positioning needs.</span></span> 
    * <span data-ttu-id="007b4-127">全球鎖定工具提供穩定的座標系統，可將虛擬與真實世界標記之間的明顯不一致範圍降至最低。</span><span class="sxs-lookup"><span data-stu-id="007b4-127">World Locking Tools provides a stable coordinate system that minimizes the visible inconsistencies between virtual and real world markers.</span></span> <span data-ttu-id="007b4-128">以另一種方式進行，它會以共用的錨點鎖定整個場景，而不是使用群組本身的個別錨點鎖定每個物件群組。</span><span class="sxs-lookup"><span data-stu-id="007b4-128">Put another way, it world-locks the entire scene with a shared pool of anchors, rather than locking each group of objects with the group's own individual anchor.</span></span>
* <span data-ttu-id="007b4-129">**針對使用 OpenXR 或 WINDOWS XR 外掛程式的 Unity 2019/2020**，您需要使用 **ARAnchorManager**</span><span class="sxs-lookup"><span data-stu-id="007b4-129">**For Unity 2019/2020 using OpenXR or the Windows XR Plugin**, you need to use **ARAnchorManager**</span></span>
* <span data-ttu-id="007b4-130">**針對較舊的 Unity 版本或 WSA** 專案，您需要使用 **WorldAnchor**</span><span class="sxs-lookup"><span data-stu-id="007b4-130">**For older Unity versions or WSA** projects, you need to use **WorldAnchor**</span></span>

## <a name="setting-up-world-locking"></a><span data-ttu-id="007b4-131">設定世界鎖定</span><span class="sxs-lookup"><span data-stu-id="007b4-131">Setting up world locking</span></span> 

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a><span data-ttu-id="007b4-132">持續性世界鎖定</span><span class="sxs-lookup"><span data-stu-id="007b4-132">Persistent world locking</span></span>

<span data-ttu-id="007b4-133">空間錨點會將影像儲存在應用程式會話之間的真實世界空間中。</span><span class="sxs-lookup"><span data-stu-id="007b4-133">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="007b4-134">一旦儲存在 HoloLens 的錨點存放區之後，就可以在不同的會話中找到和載入它們，而且當沒有網際網路連線時，就是理想的回復。</span><span class="sxs-lookup"><span data-stu-id="007b4-134">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="007b4-135">本機錨點會儲存在裝置上，而 Azure Spatial Anchors 會儲存在雲端。</span><span class="sxs-lookup"><span data-stu-id="007b4-135">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="007b4-136">如果您想要使用 Azure 雲端服務來儲存您的錨點，我們有一份文件可引導您整合 [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors)。</span><span class="sxs-lookup"><span data-stu-id="007b4-136">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="007b4-137">請注意，您在同一個專案中可以有本機和 Azure 錨點，而不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="007b4-137">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a><span data-ttu-id="007b4-138">共用座標空間</span><span class="sxs-lookup"><span data-stu-id="007b4-138">Sharing coordinate spaces</span></span> 

<span data-ttu-id="007b4-139">如果您想要共用世界鎖定的座標空間，請參閱我們的全方位 [共用體驗檔](shared-experiences-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="007b4-139">If you want to share a world locked coordinate space, check out our comprehensive [shared experience documentation](shared-experiences-in-unity.md).</span></span>

<span data-ttu-id="007b4-140">請注意，在全球鎖定工具中，尚未直接支援 Azure 空間錨點，因此共用體驗將會要求您手動建立空間錨點。</span><span class="sxs-lookup"><span data-stu-id="007b4-140">Note that Azure Spatial Anchors is not yet supported directly within World Locking Tools, and so shared experiences will require you to manually create spatial anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="007b4-141">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="007b4-141">Next Development Checkpoint</span></span>

<span data-ttu-id="007b4-142">如果您正在遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實核心構成要素。</span><span class="sxs-lookup"><span data-stu-id="007b4-142">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="007b4-143">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="007b4-143">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="007b4-144">空間對應</span><span class="sxs-lookup"><span data-stu-id="007b4-144">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="007b4-145">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="007b4-145">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="007b4-146">共用體驗</span><span class="sxs-lookup"><span data-stu-id="007b4-146">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="007b4-147">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="007b4-147">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="007b4-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="007b4-148">See Also</span></span>
* [<span data-ttu-id="007b4-149">全球鎖定工具簡介</span><span class="sxs-lookup"><span data-stu-id="007b4-149">World Locking Tools introduction</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [<span data-ttu-id="007b4-150">快速入門指南</span><span class="sxs-lookup"><span data-stu-id="007b4-150">Quickstart guides</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [<span data-ttu-id="007b4-151">教學課程</span><span class="sxs-lookup"><span data-stu-id="007b4-151">Tutorials</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [<span data-ttu-id="007b4-152">範例</span><span class="sxs-lookup"><span data-stu-id="007b4-152">Samples</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [<span data-ttu-id="007b4-153">空間錨點持續性</span><span class="sxs-lookup"><span data-stu-id="007b4-153">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="007b4-154"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="007b4-154"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="007b4-155"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="007b4-155"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="007b4-156">體驗規模調整</span><span class="sxs-lookup"><span data-stu-id="007b4-156">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="007b4-157">空間階段</span><span class="sxs-lookup"><span data-stu-id="007b4-157">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="007b4-158">Unity 中的追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="007b4-158">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="007b4-159">空間錨點</span><span class="sxs-lookup"><span data-stu-id="007b4-159">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="007b4-160">Unity 中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="007b4-160">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
