---
title: 什麼是混合實境？
description: 本文定義混合實境，並展示 AR 和 VR 裝置在混合實境頻譜中的位置。
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: 混合實境, 全像攝影, AR, VR, MR, XR, 擴增實境, 虛擬實境, 說明, 案例研究, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 什麼是虛擬實境, 什麼是擴增實境
ms.localizationpriority: high
ms.openlocfilehash: 5f4e41c04206eb5ca1a0d2e0dac914a1b3b1052d
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703124"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="e3797-104">什麼是混合實境？</span><span class="sxs-lookup"><span data-stu-id="e3797-104">What is Mixed Reality?</span></span>

![在 HoloLens 2 上手部指向和行動](images/02_MixedRealitySlashMixedReality.png)

<span data-ttu-id="e3797-106">混合實境是實體和數位世界的融合，消除了人類、電腦和環境彼此互動的藩籬。</span><span class="sxs-lookup"><span data-stu-id="e3797-106">Mixed Reality is a blend of physical and digital worlds, unlocking the links between human, computer, and environment interaction.</span></span> <span data-ttu-id="e3797-107">這種新型的實境功能奠基於電腦視覺、圖形處理能力、顯示器技術和輸入系統的強化。</span><span class="sxs-lookup"><span data-stu-id="e3797-107">This new reality is based on advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="e3797-108">不過，「混合實境」一詞最初是由 Paul Milgram 和 Fumio Kishino 在 1994 年的論文《[混合實境視覺顯示器分類法 (A Taxonomy of Mixed Reality Visual Displays)](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)》中提出。</span><span class="sxs-lookup"><span data-stu-id="e3797-108">However, the term *Mixed Reality* was introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)."</span></span> <span data-ttu-id="e3797-109">他們的論文探討了 *Virtuality Continuum* 的概念，以及如何分類套用至顯示器的分類法。</span><span class="sxs-lookup"><span data-stu-id="e3797-109">Their paper explored the concept of the *virtuality continuum* and the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="e3797-110">從那時起，混合實境的應用就不再侷限於顯示器，而也包括：</span><span class="sxs-lookup"><span data-stu-id="e3797-110">Since then, the application of Mixed Reality has gone beyond displays to include:</span></span>
* <span data-ttu-id="e3797-111">環境輸入</span><span class="sxs-lookup"><span data-stu-id="e3797-111">Environmental input</span></span>
* <span data-ttu-id="e3797-112">空間音效</span><span class="sxs-lookup"><span data-stu-id="e3797-112">Spatial sound</span></span>
* <span data-ttu-id="e3797-113">實際和虛擬空間中的位置和定位</span><span class="sxs-lookup"><span data-stu-id="e3797-113">Locations and positioning in both real and virtual spaces</span></span>

<span data-ttu-id="e3797-114">![混合實境頻譜影像](images/mixedrealityspectrum-worlds.png)</span><span class="sxs-lookup"><span data-stu-id="e3797-114">![The Mixed Reality spectrum image](images/mixedrealityspectrum-worlds.png)</span></span><br>
<span data-ttu-id="e3797-115">*影像：混合實境是實體環境與數位世界混合的結果。*</span><span class="sxs-lookup"><span data-stu-id="e3797-115">*Image: Mixed Reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="e3797-116">環境輸入和認知</span><span class="sxs-lookup"><span data-stu-id="e3797-116">Environmental input and perception</span></span>

<span data-ttu-id="e3797-117">過去數十年來，眾人持續探索人類與電腦輸入之間的關聯性，因而造就了所謂的 *人機互動* (或簡稱 HCI) 的專業領域。</span><span class="sxs-lookup"><span data-stu-id="e3797-117">Over the past several decades, exploration into the relationship between human and computer input has continued, leading to the discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="e3797-118">人類輸入會透過各種不同的方式進行，包括鍵盤、滑鼠、觸控、筆跡、語音，甚至是 Kinect 的框架追蹤。</span><span class="sxs-lookup"><span data-stu-id="e3797-118">Human input happens through different means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="e3797-119">在感應器和處理方面的提升，逐漸使環境中的電腦輸入形成新的區域。</span><span class="sxs-lookup"><span data-stu-id="e3797-119">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="e3797-120">電腦與環境之間的互動是有效的環境理解或 *感知*，而正因如此，Windows 中顯示環境資訊的 API 名稱即稱為 [認知 API](https://docs.microsoft.com/uwp/api/Windows.Perception)。</span><span class="sxs-lookup"><span data-stu-id="e3797-120">The interaction between computers and environments is effectively environmental understanding or *perception*, which is why the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="e3797-121">環境輸入會擷取諸多事物，像是使用者所處的位置 (例如[頭部追蹤](../design/coordinate-systems.md))、表面和界限 (例如[空間對應](../design/spatial-mapping.md)和[場景理解](../design/scene-understanding.md))、環境光源、環境音效、物件辨識和位置。</span><span class="sxs-lookup"><span data-stu-id="e3797-121">Environmental input captures things like a person's position in the world ([head tracking](../design/coordinate-systems.md)), surfaces and boundaries ([spatial mapping](../design/spatial-mapping.md) and [scene understanding](../design/scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>

<span data-ttu-id="e3797-122">![顯示電腦、人類與環境之間互動的卞氏圖表](images/mixed-reality-venn-diagram-300px.png)</span><span class="sxs-lookup"><span data-stu-id="e3797-122">![Venn diagram showing interactions between computers, humans and environments](images/mixed-reality-venn-diagram-300px.png)</span></span><br><span data-ttu-id="e3797-123"> \
*影像：電腦、人類與環境之間的互動。*</span><span class="sxs-lookup"><span data-stu-id="e3797-123"> \
*Image: The interactions between computers, humans, and environments.*</span></span>

<br>

<span data-ttu-id="e3797-124">**電腦處理、人類輸入和環境輸入** 這三者的組合，造就了建立真正混合實境體驗的舞台。</span><span class="sxs-lookup"><span data-stu-id="e3797-124">The combination of all three - **computer processing, human input, and environmental input** - sets the stage for creating true Mixed Reality experiences.</span></span> <span data-ttu-id="e3797-125">實體世界中的移動可以轉譯成數位世界中的移動。</span><span class="sxs-lookup"><span data-stu-id="e3797-125">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="e3797-126">實體世界的界限可能會影響數位世界中的應用程式體驗，例如遊戲進行。</span><span class="sxs-lookup"><span data-stu-id="e3797-126">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="e3797-127">如果沒有環境輸入，體驗就無法在混合實體與數位實境間融合。</span><span class="sxs-lookup"><span data-stu-id="e3797-127">Without environmental input, experiences can't blend between physical and digital realities.</span></span><br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="e3797-128">混合實境頻譜</span><span class="sxs-lookup"><span data-stu-id="e3797-128">The Mixed Reality spectrum</span></span>

<span data-ttu-id="e3797-129">因為混合實境融合了實際和數位世界，這兩個實境就定義了頻譜的兩極，稱為 Virtuality Continuum。</span><span class="sxs-lookup"><span data-stu-id="e3797-129">Since Mixed Reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="e3797-130">我們將實境的陣列稱為 *混合實境頻譜*。</span><span class="sxs-lookup"><span data-stu-id="e3797-130">We refer to the array of realities as the *Mixed Reality spectrum*.</span></span> <span data-ttu-id="e3797-131">左側是我們人類所在之處的實體實境。</span><span class="sxs-lookup"><span data-stu-id="e3797-131">On the left-hand side, we have the physical reality that we as humans exist in.</span></span> <span data-ttu-id="e3797-132">右側則是對應的數位實境。</span><span class="sxs-lookup"><span data-stu-id="e3797-132">On the right-hand side, we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="e3797-133">擴增與虛擬實境</span><span class="sxs-lookup"><span data-stu-id="e3797-133">Augmented vs. virtual reality</span></span>

<span data-ttu-id="e3797-134">現今市場上大部分的行動電話幾乎都沒有環境理解功能。</span><span class="sxs-lookup"><span data-stu-id="e3797-134">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="e3797-135">他們所提供的體驗無法混合實體和數位實境。</span><span class="sxs-lookup"><span data-stu-id="e3797-135">The experiences they offer can't mix physical and digital realities.</span></span> <span data-ttu-id="e3797-136">在實體世界的影片串流上重疊圖形的體驗即為「擴增實境」  。</span><span class="sxs-lookup"><span data-stu-id="e3797-136">The experiences that overlay graphics on video streams of the physical world are *augmented reality*.</span></span> <span data-ttu-id="e3797-137">遮蔽您的檢視來呈現數位體驗的體驗即為「虛擬實境」  。</span><span class="sxs-lookup"><span data-stu-id="e3797-137">The experiences that occlude your view to present a digital experience are *virtual reality*.</span></span> <span data-ttu-id="e3797-138">擴增實境與虛擬實境之間的體驗，形成了 *混合實境*：</span><span class="sxs-lookup"><span data-stu-id="e3797-138">The experiences enabled between augmented and virtual reality form *Mixed Reality*:</span></span>
* <span data-ttu-id="e3797-139">從真實世界開始，放置數位物件 (例如全像投影)，如同真實存在一般。</span><span class="sxs-lookup"><span data-stu-id="e3797-139">Starting with the physical world, placing a digital object, such as a hologram, as if it was there.</span></span>
* <span data-ttu-id="e3797-140">從實體世界開始，另一個人的數位表示法 -- [頭像] -- 顯示他們在留言時所處的位置。</span><span class="sxs-lookup"><span data-stu-id="e3797-140">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="e3797-141">換句話說，即為不同時間點表示非同步共同作業的體驗。</span><span class="sxs-lookup"><span data-stu-id="e3797-141">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="e3797-142">從數位世界開始，實體世界 (例如牆和傢俱) 的實體界限會以數位方式出現在體驗中，以協助使用者避免實體物件。</span><span class="sxs-lookup"><span data-stu-id="e3797-142">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>


<br>

<span data-ttu-id="e3797-143">![混合實境頻譜](images/mixedrealityspectrum.png)</span><span class="sxs-lookup"><span data-stu-id="e3797-143">![The Mixed Reality spectrum](images/mixedrealityspectrum.png)</span></span><br>
<span data-ttu-id="e3797-144">*影像：混合實境頻譜*</span><span class="sxs-lookup"><span data-stu-id="e3797-144">*Image: The Mixed Reality spectrum*</span></span>

<br>

<span data-ttu-id="e3797-145">現今提供的多數擴增實境和虛擬實境產品，都代表此頻譜的一小部分，且被視為較大混合實境頻譜的子集。</span><span class="sxs-lookup"><span data-stu-id="e3797-145">Most augmented reality and virtual reality offerings available today represent a small part of this spectrum and are considered subsets of the larger Mixed Reality spectrum.</span></span> <span data-ttu-id="e3797-146">Windows 10 以整個頻譜為基礎，並可將數位方式呈現的人員、環境和事物與真實世界混合。</span><span class="sxs-lookup"><span data-stu-id="e3797-146">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>


## <a name="devices-and-experiences"></a><span data-ttu-id="e3797-147">裝置和體驗</span><span class="sxs-lookup"><span data-stu-id="e3797-147">Devices and experiences</span></span>

<span data-ttu-id="e3797-148">有兩種主要的裝置類型可提供 Windows Mixed Reality 體驗：</span><span class="sxs-lookup"><span data-stu-id="e3797-148">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="e3797-149">裝置能夠將數位內容放在真實世界中，如同真實存在一般，是 **Holographic 裝置** 的特性。</span><span class="sxs-lookup"><span data-stu-id="e3797-149">**Holographic devices** are characterized by the device's ability to place digital content in the real world as if it were there.</span></span>
2. <span data-ttu-id="e3797-150">裝置能夠建立「存在感」，隱藏真實世界，而以數位體驗取而代之，是 **沉浸式裝置** 的特性。</span><span class="sxs-lookup"><span data-stu-id="e3797-150">**Immersive devices** are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="30%"> <span data-ttu-id="e3797-151">特性</span><span class="sxs-lookup"><span data-stu-id="e3797-151">Characteristic</span></span></th><th width="35%"> <span data-ttu-id="e3797-152">全像攝影裝置</span><span class="sxs-lookup"><span data-stu-id="e3797-152">Holographic devices</span></span></th><th width="35%"> <span data-ttu-id="e3797-153">沉浸式裝置</span><span class="sxs-lookup"><span data-stu-id="e3797-153">Immersive devices</span></span></th>
</tr><tr>
<td><span data-ttu-id="e3797-154"><strong>範例裝置</strong></span><span class="sxs-lookup"><span data-stu-id="e3797-154"><strong>Example device</strong></span></span></td><td> <span data-ttu-id="e3797-155">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="e3797-155">Microsoft HoloLens</span></span><br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> <span data-ttu-id="e3797-156">Samsung HMD Odyssey+</span><span class="sxs-lookup"><span data-stu-id="e3797-156">Samsung HMD Odyssey+</span></span><br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><span data-ttu-id="e3797-157"><strong>顯示器</strong></span><span class="sxs-lookup"><span data-stu-id="e3797-157"><strong>Display</strong></span></span></td><td> <span data-ttu-id="e3797-158">透明顯示器。</span><span class="sxs-lookup"><span data-stu-id="e3797-158">See-through display.</span></span> <span data-ttu-id="e3797-159">讓使用者在穿戴頭戴式裝置時可看到實體環境。</span><span class="sxs-lookup"><span data-stu-id="e3797-159">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="e3797-160">不透明顯示器。</span><span class="sxs-lookup"><span data-stu-id="e3797-160">Opaque display.</span></span> <span data-ttu-id="e3797-161">在穿戴頭戴式裝置時封鎖實體環境。</span><span class="sxs-lookup"><span data-stu-id="e3797-161">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td><span data-ttu-id="e3797-162"><strong>移動</strong></span><span class="sxs-lookup"><span data-stu-id="e3797-162"><strong>Movement</strong></span></span></td><td> <span data-ttu-id="e3797-163">完整的六度自由移動，包括旋轉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="e3797-163">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="e3797-164">完整的六度自由移動，包括旋轉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="e3797-164">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table> 


> [!NOTE]
> <span data-ttu-id="e3797-165">無論裝置是連線到其他電腦或以行動網卡連線到其他電腦 (透過 USB 纜線或 Wi-Fi) 或是獨立的 (未連線)，都不會反映裝置是否為全像攝影還是沉浸式。</span><span class="sxs-lookup"><span data-stu-id="e3797-165">Whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) doesn't reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="e3797-166">增加行動性的功能會帶來更好的體驗，且全像攝影和沉浸式裝置都可能是以行動網卡連線或是未連線的。</span><span class="sxs-lookup"><span data-stu-id="e3797-166">Features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>

<span data-ttu-id="e3797-167">技術提升是已啟用混合實境體驗的功能。</span><span class="sxs-lookup"><span data-stu-id="e3797-167">Technological advancement is what has enabled Mixed Reality experiences.</span></span> <span data-ttu-id="e3797-168">目前沒有任何裝置可在整個頻譜中執行體驗。</span><span class="sxs-lookup"><span data-stu-id="e3797-168">There are no devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="e3797-169">Windows 10 同時為裝置製造商和開發人員提供通用的混合實境平台。</span><span class="sxs-lookup"><span data-stu-id="e3797-169">Windows 10 provides a common Mixed Reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="e3797-170">現今的裝置可以支援混合實境頻譜內的特定範圍，而新型裝置則可擴大該範圍。</span><span class="sxs-lookup"><span data-stu-id="e3797-170">Devices today can support a specific range within the Mixed Reality spectrum, with new devices expanding that range.</span></span> <span data-ttu-id="e3797-171">在未來，全像攝影裝置會變得更沉浸式，而沉浸式裝置會變得更全像攝影。</span><span class="sxs-lookup"><span data-stu-id="e3797-171">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

<br>

<span data-ttu-id="e3797-172">![混合實境頻譜中的裝置類型](images/Final_WhatIsMixedReality07.png)</span><span class="sxs-lookup"><span data-stu-id="e3797-172">![Device types in the Mixed Reality spectrum](images/Final_WhatIsMixedReality07.png)</span></span><br>
<span data-ttu-id="e3797-173">*影像：裝置在混合實境頻譜上的位置*</span><span class="sxs-lookup"><span data-stu-id="e3797-173">*Image: Where devices exist on the Mixed Reality spectrum*</span></span>

<span data-ttu-id="e3797-174">最好能考量應用程式或遊戲開發人員想要建立的體驗類型。</span><span class="sxs-lookup"><span data-stu-id="e3797-174">It's best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="e3797-175">這些體驗通常會以頻譜上的特定點或部分作為目標。</span><span class="sxs-lookup"><span data-stu-id="e3797-175">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="e3797-176">開發人員應考慮他們想要作為目標的裝置功能。</span><span class="sxs-lookup"><span data-stu-id="e3797-176">Developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="e3797-177">仰賴實體世界的體驗在 HoloLens 上的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="e3797-177">Experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="e3797-178">**向左 (接近實體實境)。**</span><span class="sxs-lookup"><span data-stu-id="e3797-178">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="e3797-179">使用者仍然存在於其實體環境中，且永遠不會相信他們已離開該環境。</span><span class="sxs-lookup"><span data-stu-id="e3797-179">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="e3797-180">**中間 (完全混合實境)。**</span><span class="sxs-lookup"><span data-stu-id="e3797-180">**In the middle (fully Mixed Reality).**</span></span> <span data-ttu-id="e3797-181">這些體驗混合了真實世界與數位世界。</span><span class="sxs-lookup"><span data-stu-id="e3797-181">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="e3797-182">看過[野蠻遊戲](https://en.wikipedia.org/wiki/Jumanji)這部電影的觀看者，可以調整故事中所出現房屋的實體結構與叢林環境的混合方式。</span><span class="sxs-lookup"><span data-stu-id="e3797-182">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="e3797-183">**向右 (接近數位實境)。**</span><span class="sxs-lookup"><span data-stu-id="e3797-183">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="e3797-184">使用者會體驗到數位環境，且不會察覺周遭實體環境發生的情況。</span><span class="sxs-lookup"><span data-stu-id="e3797-184">Users experience a digital environment, and are unaware of what occurs in the physical environment around them.</span></span>

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="e3797-185">下一個探索檢查點</span><span class="sxs-lookup"><span data-stu-id="e3797-185">Next Discovery Checkpoint</span></span>

<span data-ttu-id="e3797-186">如果您有遵循我們安排的[探索旅程](get-started-with-mr.md)，則您正處於探索混合實境基本概念的途中。</span><span class="sxs-lookup"><span data-stu-id="e3797-186">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="e3797-187">您可以從這裡繼續進行下一個基本主題：</span><span class="sxs-lookup"><span data-stu-id="e3797-187">From here, you can proceed to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="e3797-188">什麼是全像投影？</span><span class="sxs-lookup"><span data-stu-id="e3797-188">What is a hologram?</span></span>](hologram.md)


