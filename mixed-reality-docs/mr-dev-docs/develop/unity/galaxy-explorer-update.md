---
title: 適用于 HoloLens 2 的 Galaxy Explorer 製作
description: 瞭解我們的團隊如何在 GitHub 上更新適用于 HoloLens 2 的 Galaxy Explorer 開放原始碼專案。
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy explorer、案例研究、專案、範例、MRTK、混合現實工具組、Unity、範例應用程式、範例應用程式、開放原始碼、Microsoft Store、HoloLens、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 2d72e005bd955bbf2611f0724ba63b80c70f7dc1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759814"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a><span data-ttu-id="d0398-104">適用于 HoloLens 2 的 Galaxy Explorer 製作</span><span class="sxs-lookup"><span data-stu-id="d0398-104">The Making of Galaxy Explorer for HoloLens 2</span></span>

<span data-ttu-id="d0398-105">歡迎使用更新版的 Galaxy Explorer for HoloLens 2 應用程式！</span><span class="sxs-lookup"><span data-stu-id="d0398-105">Welcome to the updated Galaxy Explorer for HoloLens 2 application!</span></span> <span data-ttu-id="d0398-106">[Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "星系探險") 最初開發為 HoloLens 的開放原始碼應用程式 (第一代) 透過分享您的構想方案，而且是許多人的第一個混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="d0398-106">[Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "Galaxy Explorer") was originally developed as an open-source application for HoloLens (first gen) through the Share Your Idea program, and is one of the first mixed reality experiences many people had.</span></span> <span data-ttu-id="d0398-107">現在我們要更新它，以取得 [HoloLens 2 的新功能與令人興奮的功能](https://www.microsoft.com/hololens/hardware)。</span><span class="sxs-lookup"><span data-stu-id="d0398-107">Now we're updating it for the [new and exciting capabilities of HoloLens 2](https://www.microsoft.com/hololens/hardware).</span></span>

<span data-ttu-id="d0398-108">作為其中一個 [Microsoft Mixed Reality 工作室](galaxy-explorer-update.md#mixed-reality-studios)，我們通常會開發商業級的解決方案，並在整個創意和開發程式中開發 & 的目標平臺測試。</span><span class="sxs-lookup"><span data-stu-id="d0398-108">As one of the [Microsoft Mixed Reality Studios](galaxy-explorer-update.md#mixed-reality-studios), we usually develop commercial grade solutions and are developing & testing on target platforms throughout the creative and development process.</span></span> <span data-ttu-id="d0398-109">我們會使用登機的架構和 (工具來此專案，例如 [MRTK](mrtk-getting-started.md)) ，因為它們變成可供我們和社區使用，而我們想要讓您帶著。</span><span class="sxs-lookup"><span data-stu-id="d0398-109">We're embarking on this project using the frameworks and tools (like [MRTK](mrtk-getting-started.md)) as they become available to us and the community - and we want to bring you along for the ride.</span></span>

<span data-ttu-id="d0398-110">如同原始的 Galaxy Explorer， [我們的團隊](galaxy-explorer-update.md#meet-the-team) 會在 [GitHub 上開放專案](https://github.com/Microsoft/GalaxyExplorer) ，以確保該社區具有完整的存取權。</span><span class="sxs-lookup"><span data-stu-id="d0398-110">Just like the original Galaxy Explorer, [our team](galaxy-explorer-update.md#meet-the-team) will be [open sourcing the project on GitHub](https://github.com/Microsoft/GalaxyExplorer) to ensure the community has full access.</span></span> <span data-ttu-id="d0398-111">我們也將在此記錄我們的旅程，以完整的透明說明如何從 MRTK v1 移植至 MRTK v2、增強 HoloLens 2 中可用新功能的體驗，以及確保 Galaxy Explorer 保持多平臺體驗。</span><span class="sxs-lookup"><span data-stu-id="d0398-111">We'll also be documenting our journey here in complete transparency about how we ported from MRTK v1 to MRTK v2, enhanced the experience with new features available in HoloLens 2, and ensured that Galaxy Explorer remained a multi-platform experience.</span></span> <span data-ttu-id="d0398-112">無論您是在 HoloLens 上觀看 Galaxy Explorer (第一代) 、HoloLens 2、Windows Mixed Reality 耳機或您的 Windows 10 桌上型電腦，我們都想要確定您已盡可能享受旅程。</span><span class="sxs-lookup"><span data-stu-id="d0398-112">Whether you're viewing Galaxy Explorer on HoloLens (first gen), HoloLens 2, a Windows Mixed Reality headset or on your Windows 10 desktop, we want to make sure you're enjoying the journey as much as we are!</span></span>

<span data-ttu-id="d0398-113">此頁面將會隨著我們在專案中的進展而擴大，並提供更詳細的文章、程式碼、設計成品和其他 MRTK 檔的連結，以提供您 insider 的專案查看。</span><span class="sxs-lookup"><span data-stu-id="d0398-113">This page will expand as we progress through the project with links to more detailed articles, code, design artifacts, and additional MRTK documentation to provide you with an insider's look at the project.</span></span>

## <a name="unveiling-the-new-logo"></a><span data-ttu-id="d0398-114">揭露新的標誌</span><span class="sxs-lookup"><span data-stu-id="d0398-114">Unveiling the new logo</span></span>

<span data-ttu-id="d0398-115">我們很高興地開始使用新的 Galaxy Explorer 標誌的預覽！</span><span class="sxs-lookup"><span data-stu-id="d0398-115">We're excited to kick off with a preview of the new Galaxy Explorer logo!</span></span> <span data-ttu-id="d0398-116">藉由銀河的方式來以示敬意原始標誌，我們設計了真實的視覺效果，並更新印刷樣式，以提供更現代化的感覺。</span><span class="sxs-lookup"><span data-stu-id="d0398-116">While paying homage to the original logo by featuring the Milky Way, we've designed a realistic visualization and updated the typography to provide a more modern feel.</span></span> <span data-ttu-id="d0398-117">包含在標誌中的搶先查看其中一個新圖示。</span><span class="sxs-lookup"><span data-stu-id="d0398-117">Included in the logo is a sneak peek at one of the new icons.</span></span>

![新的 Galaxy Explorer 標誌](images/ge-update-app-icon.png)

<span data-ttu-id="d0398-119">標誌的設計和印刷方式將會為整個體驗中 UI 元素的整體外觀和風格設定語氣。</span><span class="sxs-lookup"><span data-stu-id="d0398-119">The design and typography of the logo will set the tone for the overall look and feel of UI elements throughout the experience.</span></span> 

## <a name="thinking-about-interactions"></a><span data-ttu-id="d0398-120">考慮互動</span><span class="sxs-lookup"><span data-stu-id="d0398-120">Thinking about interactions</span></span>

<span data-ttu-id="d0398-121">作為創意工作室，我們 ecstatic 了將 Galaxy Explorer 移植到 HoloLens 2 的許可權。</span><span class="sxs-lookup"><span data-stu-id="d0398-121">As a creative studio, we were ecstatic about the privilege to port Galaxy Explorer to HoloLens 2.</span></span> <span data-ttu-id="d0398-122">我們從一開始就知道，我們希望體驗成為新裝置的一小部分，並示範混合的現實能力只受到夢想的限制。</span><span class="sxs-lookup"><span data-stu-id="d0398-122">We knew from the start that we wanted the experience to be a celebration of the new device and to demonstrate that Mixed Reality empowerment is limited only by the imagination.</span></span>

<span data-ttu-id="d0398-123">HoloLens 2 可讓使用者以自然的方式來觸控、抓住和移動全息影像，它們的回應方式很類似真正的物件。</span><span class="sxs-lookup"><span data-stu-id="d0398-123">HoloLens 2 allows users to touch, grasp, and move holograms in ways that feel natural – they respond a lot like real objects.</span></span> <span data-ttu-id="d0398-124">完全表達的手模型很棒，因為它可讓使用者進行自然的操作。</span><span class="sxs-lookup"><span data-stu-id="d0398-124">Fully articulated hand models are amazing, because it lets users do what feels natural.</span></span> <span data-ttu-id="d0398-125">比方說，每個人都是以稍微不同的方式來挑選杯，而不是強制執行這項操作，而是由 HoloLens 2 讓您以自己的方式執行。</span><span class="sxs-lookup"><span data-stu-id="d0398-125">For example, everybody picks up a cup slightly differently – and instead of enforcing one particular way to do it, HoloLens 2 lets you do it your way.</span></span>

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

<span data-ttu-id="d0398-126">這是第一代 HoloLens 裝置上以點點為基礎之介面的重大變更。</span><span class="sxs-lookup"><span data-stu-id="d0398-126">This is a significant change from the Air Tap-based interfaces on first-generation HoloLens devices.</span></span> <span data-ttu-id="d0398-127">使用者現在可以「關閉」和「個人」，而不是從距離與全像全像之間的互動。</span><span class="sxs-lookup"><span data-stu-id="d0398-127">Instead of interacting with holograms from a distance, users can now get "up close and personal".</span></span> <span data-ttu-id="d0398-128">當您將現有的體驗移植到 HoloLens 2 或規劃新的體驗時，請務必熟悉直接操作的全像投影。</span><span class="sxs-lookup"><span data-stu-id="d0398-128">When porting existing experiences over to HoloLens 2 or planning new ones, it's important to make yourself familiar with the direct manipulation of holograms.</span></span>

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a><span data-ttu-id="d0398-129">直接操作與空間的大量距離</span><span class="sxs-lookup"><span data-stu-id="d0398-129">Direct manipulation vs. the vast distances in space</span></span>

<span data-ttu-id="d0398-130">這是神奇的體驗，可讓您抓住全球，並將其放在您手中。</span><span class="sxs-lookup"><span data-stu-id="d0398-130">It's a magical experience to reach out, grab a planet and hold it in your hand.</span></span> <span data-ttu-id="d0398-131">這種方法的挑戰是日光系統的大小–是很大的！</span><span class="sxs-lookup"><span data-stu-id="d0398-131">The challenge with this approach is the size of the solar system – it's huge!</span></span> <span data-ttu-id="d0398-132">使用者需要四處移動空間，以接近每個行星的互動。</span><span class="sxs-lookup"><span data-stu-id="d0398-132">The user would need to walk around their room to get close to each planet to interact with it.</span></span>

<span data-ttu-id="d0398-133">為了讓使用者能與更遠的物件互動，MRTK 提供了從使用者的手中走出的手片，作為手的延伸。</span><span class="sxs-lookup"><span data-stu-id="d0398-133">To allow users to interact with objects that are farther away, MRTK offers hand rays that shoot out from the center of the user's palm, acting as an extension of the hand.</span></span> <span data-ttu-id="d0398-134">環圈圖的游標會附加至光線的結尾，以指出光線與目標物件相交的位置。</span><span class="sxs-lookup"><span data-stu-id="d0398-134">A donut-shaped cursor is attached to the end of the ray to indicate where the ray intersects with a target object.</span></span> <span data-ttu-id="d0398-135">然後，游標所在的物件就能從手部接收手勢命令。</span><span class="sxs-lookup"><span data-stu-id="d0398-135">The object that the cursor lands on can then receive gestural commands from the hand.</span></span> 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

<span data-ttu-id="d0398-136">在原始版本的 Galaxy Explorer 中，使用者會以行星游標為地球，然後按下滑鼠來更接近。</span><span class="sxs-lookup"><span data-stu-id="d0398-136">In the original version of Galaxy Explorer, the user would target a planet with the gaze cursor and then air tap to call it closer.</span></span> <span data-ttu-id="d0398-137">將體驗移植到 HoloLens 2 最簡單的方式，就是採取這種行為，並使用手光線來選取行星。</span><span class="sxs-lookup"><span data-stu-id="d0398-137">The easiest way to port the experience to HoloLens 2 is to take this behavior and use hand rays to select planets.</span></span> <span data-ttu-id="d0398-138">雖然這是正常運作的，但仍會讓我們更有希望。</span><span class="sxs-lookup"><span data-stu-id="d0398-138">While this was functional, it left us wanting more.</span></span>

### <a name="back-to-the-drawing-board"></a><span data-ttu-id="d0398-139">從頭再來</span><span class="sxs-lookup"><span data-stu-id="d0398-139">Back to the drawing board</span></span>

<span data-ttu-id="d0398-140">我們一起構思可在現有的互動之上建立哪些內容。</span><span class="sxs-lookup"><span data-stu-id="d0398-140">We came together to ideate what could be built on top of the existing interactions.</span></span> <span data-ttu-id="d0398-141">思考方式是：雖然 HoloLens 2 可讓使用者以自然、實際的方式與全像影像互動，但不是真正的定義。</span><span class="sxs-lookup"><span data-stu-id="d0398-141">The thinking was: Although HoloLens 2 allows users to interact with holograms in natural, realistic ways, holograms are by definition not real.</span></span> <span data-ttu-id="d0398-142">只要對使用者進行互動合理，就不會有實際物件的互動，而是可以達成此目的。</span><span class="sxs-lookup"><span data-stu-id="d0398-142">So as long as an interaction is plausible for the user, it doesn't matter if that interaction would be possible with a real object or not – we can make it possible.</span></span>

<span data-ttu-id="d0398-143">我們探索的一個概念是以 telekinesis 為基礎，也就是處理物件的能力。</span><span class="sxs-lookup"><span data-stu-id="d0398-143">One concept that we explored was based on telekinesis – the power to manipulate objects with one's mind.</span></span> <span data-ttu-id="d0398-144">通常會出現在超級主圖的影片中，一人會與他們的想法聯繫，並將物件撥到其手中。</span><span class="sxs-lookup"><span data-stu-id="d0398-144">Often seen in super hero movies, a person would reach out with their mind and call an object into their open hand.</span></span> <span data-ttu-id="d0398-145">我們將更深入地探討此概念，並介紹概念如何運作的快速草圖。</span><span class="sxs-lookup"><span data-stu-id="d0398-145">We played around with the idea some more and came up with a quick sketch of how the concept could work.</span></span>

![強制抓取互動的概念](images/ge-update-interactions-concept-force-grab.png)

<span data-ttu-id="d0398-147">使用者會將手中的光線指向行星，以提供目標意見反應。</span><span class="sxs-lookup"><span data-stu-id="d0398-147">The user would point the hand ray at a planet, which would provide target feedback.</span></span> <span data-ttu-id="d0398-148">當使用者接著擴充他們的手中，就會由神奇強制將地球拉往使用者，直到它夠近才能抓取。</span><span class="sxs-lookup"><span data-stu-id="d0398-148">As the user then extends their open hand, the planet would be pulled towards the user by a magical force until it's close enough to grab it.</span></span> <span data-ttu-id="d0398-149">因此，我們的互動名稱：強制抓取。</span><span class="sxs-lookup"><span data-stu-id="d0398-149">Hence our name for the interaction: force grab.</span></span> <span data-ttu-id="d0398-150">當使用者以其手中的手離開全球時，它會再次回到其軌跡。</span><span class="sxs-lookup"><span data-stu-id="d0398-150">As the user would push away the planet with their open hand, it would return again to its orbit.</span></span>

### <a name="force-grab-prototyping"></a><span data-ttu-id="d0398-151">強制抓取原型設計</span><span class="sxs-lookup"><span data-stu-id="d0398-151">Force grab prototyping</span></span>

<span data-ttu-id="d0398-152">接著，我們建立了多個原型來測試概念：互動的整體外觀為何？</span><span class="sxs-lookup"><span data-stu-id="d0398-152">We then created multiple prototypes to test the concept: How does the interaction feel overall?</span></span> <span data-ttu-id="d0398-153">呼叫的物件是否應該在使用者之前停止，或繼續進行，直到放置為止？</span><span class="sxs-lookup"><span data-stu-id="d0398-153">Should the called object stop in front of the user or stick to their hands until placed?</span></span> <span data-ttu-id="d0398-154">呼叫的物件是否會在呼叫時變更大小或調整？</span><span class="sxs-lookup"><span data-stu-id="d0398-154">Should the called object change size or scale while being called?</span></span>

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a><span data-ttu-id="d0398-155">在應用程式中執行強制抓取</span><span class="sxs-lookup"><span data-stu-id="d0398-155">Implementing force grab into the application</span></span>

<span data-ttu-id="d0398-156">當我們嘗試在行星上取得強制抓取時，我們發現我們必須變更日光系統的規模。</span><span class="sxs-lookup"><span data-stu-id="d0398-156">When we tried the force grab on planets, we realized that we had to change the scale of the solar system.</span></span> <span data-ttu-id="d0398-157">這表示，系統很難讓使用者瞭解和流覽不清楚、中型的日光系統標記法。</span><span class="sxs-lookup"><span data-stu-id="d0398-157">It turned out that an accurate, medium-sized representation of the solar system is difficult for users to understand and navigate - they didn't know where to look.</span></span> <span data-ttu-id="d0398-158">不過，小尺寸表示讓某些行星變得太小而無法輕易選取。</span><span class="sxs-lookup"><span data-stu-id="d0398-158">However, a small-sized-representation made some planets too small to be easily selected.</span></span> <span data-ttu-id="d0398-159">如此一來，行星的大小和日光物體之間的間距，設計為在中型房間內感覺舒適，同時維持相對精確度。</span><span class="sxs-lookup"><span data-stu-id="d0398-159">As a result, the size of the planets and the spacing between solar objects was designed to feel comfortable within a medium-sized room while maintaining relative accuracy.</span></span>

<span data-ttu-id="d0398-160">在我們的開發短期衝刺的後續階段中，我們很幸運能擁有內部的 MSFT 混合現實專家，因此我們可以將他們的輸入做為專家的測試人員，並在強制抓取互動上進行快速的反覆運算。</span><span class="sxs-lookup"><span data-stu-id="d0398-160">During the later stages of our development sprint, we were lucky enough to have fellow MSFT Mixed Reality experts in-house, so we got to work getting their input as expert testers and doing quick iterations on the force grab interaction.</span></span>

![Jenny Kam 測試 Galaxy Explorer 的預覽組建](images/ge-update-user-testing.png)

<span data-ttu-id="d0398-162">圖： Jenny Kam 是資深設計負責人，測試 Galaxy Explorer 進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="d0398-162">In picture: Jenny Kam, Senior Design Lead, testing a work-in-progress of Galaxy Explorer.</span></span>

### <a name="adding-affordances-for-targeting"></a><span data-ttu-id="d0398-163">新增目標的 affordances</span><span class="sxs-lookup"><span data-stu-id="d0398-163">Adding affordances for targeting</span></span>

<span data-ttu-id="d0398-164">當我們在 HoloLens 2 上實驗時，我們發現即使新的互動是自然且直覺的，全像是：沒有權數或 tactile sensations。</span><span class="sxs-lookup"><span data-stu-id="d0398-164">As we experimented on HoloLens 2, we found that even though the new interactions are natural and intuitive, holograms remain the same: with no weight or tactile sensations.</span></span> <span data-ttu-id="d0398-165">由於全息全像是在與物件互動時，人類用來接收的自然意見反應，因此我們需要建立它們。</span><span class="sxs-lookup"><span data-stu-id="d0398-165">Since holograms don't provide natural feedback that humans are used to receiving when they interact with objects, we needed to create them.</span></span>

<span data-ttu-id="d0398-166">我們考慮到使用者會針對互動的各種階段提供視覺和音訊的意見反應，而且因為強制抓取機制是與 Galaxy Explorer 互動的核心，所以我們進行了許多反覆運算。</span><span class="sxs-lookup"><span data-stu-id="d0398-166">We thought about the visual and audio feedback that users would be provided for the various stages of their interactions, and since the force grab mechanism is central to interacting with Galaxy Explorer, we did many iterations.</span></span> <span data-ttu-id="d0398-167">其目標是要針對互動的每個階段，找出音訊和視覺效果的正確平衡：將焦點放在想要的物件上、將它呼叫給使用者，然後再放開。</span><span class="sxs-lookup"><span data-stu-id="d0398-167">The aim was to find the right balance of audio and visual feedback for each stage of the interaction: focusing on the intended object, calling it to the user, and then releasing it.</span></span> <span data-ttu-id="d0398-168">我們所學到的內容是，需要更多的音訊和視覺效果，才能將互動與我們過去針對 HoloLens (第一代) 的互動。</span><span class="sxs-lookup"><span data-stu-id="d0398-168">What we learned is that more audio and visual feedback was required to reinforce the interaction than we were used to for HoloLens (first gen).</span></span>

![行星上的視覺 affordances](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a><span data-ttu-id="d0398-170">新增 affordances 來強制抓取</span><span class="sxs-lookup"><span data-stu-id="d0398-170">Adding affordances for force grab</span></span>
 
<span data-ttu-id="d0398-171">一旦有了基本的強制抓取機制搭配音訊和 visual affordances，我們就看過如何讓選取行星更容易使用。</span><span class="sxs-lookup"><span data-stu-id="d0398-171">Once we had the basic force grab mechanism with audio and visual affordances, we looked at how to make selecting planets more user-friendly.</span></span> <span data-ttu-id="d0398-172">有兩個主要的原因要解決：因為日光系統是3D 移動介面，所以使用者會增加複雜性來瞭解如何以一致的方式鎖定物件。</span><span class="sxs-lookup"><span data-stu-id="d0398-172">There were two main things to address: Because the solar system is a 3D moving interface, there's added complexity for users to learn how to target objects consistently.</span></span> <span data-ttu-id="d0398-173">這是因為在選取物件時，光線很快就會變得更複雜，讓行星迅速移往使用者。</span><span class="sxs-lookup"><span data-stu-id="d0398-173">This was compounded by the fact that the hand ray is fast at selecting an object, making planets move towards the user incredibly quickly.</span></span>

<span data-ttu-id="d0398-174">我們採用三個面向的解決方案來達到這個效益。</span><span class="sxs-lookup"><span data-stu-id="d0398-174">We approached this with a three-pronged solution.</span></span> <span data-ttu-id="d0398-175">第一個是相當直覺：讓選取範圍變慢，讓行星以更自然的步調來處理使用者。</span><span class="sxs-lookup"><span data-stu-id="d0398-175">The first was fairly intuitive: slow down the selection process so that planets approach the user at a more natural pace.</span></span> <span data-ttu-id="d0398-176">調整速度之後，我們必須重新流覽音訊和視覺 affordances，將音訊意見反應新增至使用者所追蹤的地球。</span><span class="sxs-lookup"><span data-stu-id="d0398-176">Once the speed was adjusted, we had to revisit the audio and visual affordances, adding audio feedback as the planet tracked towards the user.</span></span>

<span data-ttu-id="d0398-177">解決方案的第二個部分是讓整個強制抓取互動的視覺效果成為有形。</span><span class="sxs-lookup"><span data-stu-id="d0398-177">The second part of the solution was to make the visualization of the entire force grab interaction tangible.</span></span> <span data-ttu-id="d0398-178">我們視覺化了一個粗線，在手邊的光線連接之後移往目標物件，然後將物件帶回使用者，就像套索一樣。</span><span class="sxs-lookup"><span data-stu-id="d0398-178">We visualized a thick line that moves towards the targeted object once the hand ray connects with it, and then brings the object back to the user - like a lasso.</span></span> 

![用於強制抓取的視覺效果「套索」 affordances](images/ge-update-lasso-affordances.png)

<span data-ttu-id="d0398-180">最後，我們將日光系統的規模優化，讓行星夠大，讓使用者的注視和手的光線成為目標。</span><span class="sxs-lookup"><span data-stu-id="d0398-180">Finally, we optimized the scale of the solar system so that the planets were large enough for the user's gaze and hand ray to target them.</span></span> 

<span data-ttu-id="d0398-181">這三項增強功能可讓使用者做出精確的選擇，以直覺的方式呼叫行星。</span><span class="sxs-lookup"><span data-stu-id="d0398-181">These three improvements allowed users to make accurate selections, calling planets to them in an intuitive way.</span></span> <span data-ttu-id="d0398-182">整體來說，最終的強制抓取效果在日光系統中是更沉浸且互動式的體驗。</span><span class="sxs-lookup"><span data-stu-id="d0398-182">Overall, the effect of the final force grab is a more immersive and interactive experience in the solar system.</span></span>

## <a name="spotlight-on-jupiter"></a><span data-ttu-id="d0398-183">在 Jupiter 上聚焦</span><span class="sxs-lookup"><span data-stu-id="d0398-183">Spotlight on Jupiter</span></span>

<span data-ttu-id="d0398-184">建立銀河方式的日光主體是 humbling 的體驗。</span><span class="sxs-lookup"><span data-stu-id="d0398-184">Creating the solar bodies of the Milky Way was a humbling experience.</span></span> <span data-ttu-id="d0398-185">尤其是，Jupiter 的獨特特性讓它耶。</span><span class="sxs-lookup"><span data-stu-id="d0398-185">In particular, the unique characteristics of Jupiter make it a sight to behold.</span></span> <span data-ttu-id="d0398-186">這是最大且最彩色的天然氣巨人，且包含的品質高於所有其他行星組合。</span><span class="sxs-lookup"><span data-stu-id="d0398-186">It's the largest and most colorful of the gas giants, and contains more mass than all other planets combined.</span></span> <span data-ttu-id="d0398-187">其廣泛的 turbulence 和雲端動態 mesmerizing 區，可 prefect 特別的藝術。</span><span class="sxs-lookup"><span data-stu-id="d0398-187">Its sheer size and mesmerizing bands of turbulence and cloud dynamics are prefect for special artistic attention.</span></span>

### <a name="geometry-and-meshes"></a><span data-ttu-id="d0398-188">幾何和網格</span><span class="sxs-lookup"><span data-stu-id="d0398-188">Geometry and meshes</span></span>

<span data-ttu-id="d0398-189">作為天然氣大型，Jupiter 的外部 shell 包含 gaseous 層。</span><span class="sxs-lookup"><span data-stu-id="d0398-189">As a gas giant, Jupiter's outer shells consists of gaseous layers.</span></span> <span data-ttu-id="d0398-190">其快速旋轉速度、內部熱度交換和 Coriolis 的組合，可建立彩色的圖層和串流，形成 swirling 的雲端皮帶和 vortices。</span><span class="sxs-lookup"><span data-stu-id="d0398-190">The combination of its fast rotational speed, inner heat exchange, and Coriolis forces creates colorful layers and streams that form into swirling cloud belts and vortices.</span></span> <span data-ttu-id="d0398-191">捕捉這個複雜的美式，是建立太陽系的關鍵。</span><span class="sxs-lookup"><span data-stu-id="d0398-191">Capturing this intricate beauty was key in creating our solar system.</span></span>

<span data-ttu-id="d0398-192">使用視覺化的技術（例如流暢模擬）和具有預先計算串流的動畫紋理都不會有問題。</span><span class="sxs-lookup"><span data-stu-id="d0398-192">It was immediately clear that using visualizing techniques like fluid simulations and animated textures with precomputed streams were out of question.</span></span> <span data-ttu-id="d0398-193">將這項功能與其他同時發生的其他專案一起模擬所需的運算能力，會對效能造成重大不利的影響。</span><span class="sxs-lookup"><span data-stu-id="d0398-193">The computing power required to simulate this in combination with everything else happening simultaneously would have had significant detrimental impacts on performance.</span></span> 

![Jupiter 物件總覽](images/ge-update-jupiter-shells-complete.jpg)

<span data-ttu-id="d0398-195">下一種方法是「冒煙和鏡像」的解決方案，其中包括覆迭透明材質圖層，每個都解決了面向移動的特定層面，並在旋轉網格的組合上進行編譯。</span><span class="sxs-lookup"><span data-stu-id="d0398-195">The next approach was a 'smoke-and-mirror' solution, consisting of overlaying transparent texture layers, each of which addressed a specific aspect of the atmospheric movement, compiled on a composition of rotating meshes.</span></span>

<span data-ttu-id="d0398-196">在下圖中，您可以在左側看到內部 shell。</span><span class="sxs-lookup"><span data-stu-id="d0398-196">In the image below, you can see the inner shell on the left.</span></span> <span data-ttu-id="d0398-197">此階層圖層提供了組合的背景，以防止組成雲端的多層之間的任何小間距。</span><span class="sxs-lookup"><span data-stu-id="d0398-197">This mat layer provided a background to the composition to guard against any small gaps between the multiple layers that made up the clouds.</span></span> <span data-ttu-id="d0398-198">由於圖層的旋轉速度很慢，因此它也會作為視覺化緩衝區來提供更快速的移動區間，以協助在各層中建立 visual unity。</span><span class="sxs-lookup"><span data-stu-id="d0398-198">Because of the layer's slow rotation, it also served as a visual buffer between the faster moving bands to help build visual unity throughout the layers.</span></span>

<span data-ttu-id="d0398-199">將此錨點設定為模型之後，移動的雲端層接著會投射在下方所示的中間和右側網格上。</span><span class="sxs-lookup"><span data-stu-id="d0398-199">After setting this anchor to the model, the moving cloud layers were then projected on the middle and right meshes seen below.</span></span>

![使用分隔 shell 的 Jupiter 物件總覽](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a><span data-ttu-id="d0398-201">紋理</span><span class="sxs-lookup"><span data-stu-id="d0398-201">Texturing</span></span>

<span data-ttu-id="d0398-202">現有的材質分為三個部分的材質塔：第三部主機具有間距的 motionless 層，可提供視差效果，中間區段包含快速移動的外部資料流，而下半部則包含緩慢旋轉的內部基底圖層。</span><span class="sxs-lookup"><span data-stu-id="d0398-202">The existing texture was separated into a three-part texture atlas: The upper third hosts a motionless layer of clouds with gaps to provide a parallax effect, the middle section contains the fast moving outer streams, and the lower third contains a slowly rotating inner base layer.</span></span>

<span data-ttu-id="d0398-203">特性良好的紅點也會分成不同的移動元件，然後插入材質的其他隱藏區域中。</span><span class="sxs-lookup"><span data-stu-id="d0398-203">The characteristic Great Red Spot was also separated into its various moving parts and then inserted into an otherwise invisible area of the texture.</span></span> <span data-ttu-id="d0398-204">這些元件可以被視為下圖中間區段中的 red toned 斑點予。</span><span class="sxs-lookup"><span data-stu-id="d0398-204">These components can be seen as the red-toned speckles in the middle section of the image below.</span></span>

<span data-ttu-id="d0398-205">因為每個波段都有特定的方向和速度，所以紋理會個別套用至每個網格。</span><span class="sxs-lookup"><span data-stu-id="d0398-205">Because each band has a specific direction and speed, the texture was applied to each mesh individually.</span></span> <span data-ttu-id="d0398-206">然後，網格會有一個通用的中心點和一個資料點，讓您可以 concentrically 整個表面的動畫。</span><span class="sxs-lookup"><span data-stu-id="d0398-206">The meshes then had a common center and pivot point, which made it possible to concentrically animate the whole surface.</span></span>

![Jupiter 紋理總覽](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a><span data-ttu-id="d0398-208">旋轉和材質行為</span><span class="sxs-lookup"><span data-stu-id="d0398-208">Rotation and texture behavior</span></span>

<span data-ttu-id="d0398-209">一旦設定了 Jupiter 的視覺效果組合之後，我們必須確定已正確地計算並套用旋轉和軌跡速度。</span><span class="sxs-lookup"><span data-stu-id="d0398-209">Once the the visual composition of Jupiter was set, we needed to ensure the rotation and orbit speeds were properly calculated and applied accordingly.</span></span> <span data-ttu-id="d0398-210">針對 Jupiter 完成完整輪替需要大約9小時的時間。</span><span class="sxs-lookup"><span data-stu-id="d0398-210">It takes roughly 9 hours for Jupiter to complete a full rotation.</span></span> <span data-ttu-id="d0398-211">這是因差異旋轉而產生的定義。</span><span class="sxs-lookup"><span data-stu-id="d0398-211">This is a matter of definition due to its Differential Rotation.</span></span> <span data-ttu-id="d0398-212">因此，會將赤道幾內亞資料流程設定為「主要串流」，並採用3600的框架進行完整的旋轉。</span><span class="sxs-lookup"><span data-stu-id="d0398-212">Therefore the equatorial stream has been set as a 'master stream', taking 3600 frames for a full rotation.</span></span> <span data-ttu-id="d0398-213">每一層都需要有旋轉速度作為3600，才能符合其初始位置，例如，600、900、1200、1800等等。</span><span class="sxs-lookup"><span data-stu-id="d0398-213">Every other layer needed to have a rotational speed as a factor of 3600 in order to match its initial position, allowing, e.g.,  600, 900, 1200, 1800 etc.</span></span>

![Jupiter shell 紋理](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a><span data-ttu-id="d0398-215">很棒的紅點</span><span class="sxs-lookup"><span data-stu-id="d0398-215">The Great Red Spot</span></span>

<span data-ttu-id="d0398-216">個別輪替的串流提供良好的視覺效果，但在觀察到接近範圍時，就不會有詳細的資料。</span><span class="sxs-lookup"><span data-stu-id="d0398-216">The individually rotating streams provided a good visual impression, but lacked in detail when observed at close range.</span></span>

<span data-ttu-id="d0398-217">最引人注目的部分是 Jupiter 的絕佳紅色點，因此我們特別建立了一組網格和紋理來展示。</span><span class="sxs-lookup"><span data-stu-id="d0398-217">The most eye-catching part was Jupiter's Great Red Spot, so we created a set of meshes and textures specifically to showcase it.</span></span>
 
<span data-ttu-id="d0398-218">我們使用的機制與 Jupiter 的波段類似：一組旋轉零件是由彼此組成，同時也會在其「主要圖層」下分組，以確保不論 rest 移動的速度有多快，都能保持在相同位置。</span><span class="sxs-lookup"><span data-stu-id="d0398-218">We used a similar mechanism as with Jupiter's bands: a set of rotating parts was composed on top of each other, while also being grouped under its 'master layer' to ensure they remain in position no matter how fast the rest moves.</span></span>

<span data-ttu-id="d0398-219">當網格已設定並準備就緒時，會套用不同層的 stormy vortex，然後每個光碟都會個別進行動畫處理，而其餘部分則會以最快的速度移動，而 rest 會逐漸降低。</span><span class="sxs-lookup"><span data-stu-id="d0398-219">When the meshes were set up and in place, different layers of the stormy vortex were applied and each disc was then animated individually, the center pieces moving fastest, with the rest progressively slowing down as it moving outwards.</span></span>

![Jupiter 絕佳的 Red 點網格](images/ge-update-great-red-spot-mesh.jpg)

<span data-ttu-id="d0398-221">組合也會與每個其他網格具有相同的 pivot，同時也會將其從原始 y 軸的傾斜 (！ ) ，以在動畫中自由旋轉。</span><span class="sxs-lookup"><span data-stu-id="d0398-221">The composition also had the same pivot as every other mesh, while also keeping its tilt from its original y-axis (!) to allow freedom in animating the rotation.</span></span> <span data-ttu-id="d0398-222">3600畫面格是基本費率，每個圖層都有這一段迴圈的因素。</span><span class="sxs-lookup"><span data-stu-id="d0398-222">3600 frames is the base rate, with each layer having a factor of this as a period of rotation.</span></span>

![Jupiter 絕佳的 Red 專色材質](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a><span data-ttu-id="d0398-224">直接在 Unity 中取得</span><span class="sxs-lookup"><span data-stu-id="d0398-224">Getting it right in Unity</span></span>

<span data-ttu-id="d0398-225">在 Unity 中執行這項作業時，有幾個重要的事項要牢記在心。</span><span class="sxs-lookup"><span data-stu-id="d0398-225">There are a couple of key things to keep in mind when implementing this in Unity.</span></span>

<span data-ttu-id="d0398-226">在處理大型透明層的集合時，Unity 很容易混淆。</span><span class="sxs-lookup"><span data-stu-id="d0398-226">Unity is easily confused when dealing with large sets of transparent layers.</span></span> <span data-ttu-id="d0398-227">解決方法是複製每個網格的材質材質，並將遞增的轉譯佇列值從內部逐漸逐漸套用到每個材質的外部。</span><span class="sxs-lookup"><span data-stu-id="d0398-227">The solution was to duplicate the texture material for each mesh and apply ascending Render Queue values progressively from the inner to the outer by 5 to each material.</span></span>

<span data-ttu-id="d0398-228">結果是內部 shell 的轉譯佇列值為 3000 (預設) ，靜態 red toned outer 的值為3005，而 fast 白色外部雲端則為3010。</span><span class="sxs-lookup"><span data-stu-id="d0398-228">The result was the inner shell had a Render Queue value of 3000 (default), the static red-toned outer later had a value of 3005, the fast white outer clouds had 3010.</span></span> <span data-ttu-id="d0398-229">很棒的紅點 (從內部到外部層) ，在此模型中已完成值為3025。</span><span class="sxs-lookup"><span data-stu-id="d0398-229">The Great Red Spot (progressing from inner to outer layer), finished with a value of 3025 in this model.</span></span>

![Jupiter 最終物件](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a><span data-ttu-id="d0398-231">最後的修飾</span><span class="sxs-lookup"><span data-stu-id="d0398-231">Final touches</span></span>

<span data-ttu-id="d0398-232">一開始就已設定紋理的 Jupiter 層，其證明不足以執行。</span><span class="sxs-lookup"><span data-stu-id="d0398-232">The textured Jupiter layers were set up at first, which proved to be insufficient for implementation.</span></span>

<span data-ttu-id="d0398-233">原始的全球標準著色器及其所有的變化，都會透過腳本 SunLightReceiver （MRTK 標準著色器不支援）接收其光源資訊。</span><span class="sxs-lookup"><span data-stu-id="d0398-233">The original Planet Standard shader, and all of its variations, receive their lighting information via a script, the SunLightReceiver, which is not supported by the MRTK Standard shader.</span></span>

<span data-ttu-id="d0398-234">單純地交換著色器並不是一種解決方案，因為地球標準著色器不支援使用投影片的材質地圖。</span><span class="sxs-lookup"><span data-stu-id="d0398-234">Simply swapping the shaders wasn't a solution because the Planet Standard shader doesn't support texture maps with transparencies.</span></span> <span data-ttu-id="d0398-235">我們已編輯此著色器，讓 Jupiter 組建如預期運作。</span><span class="sxs-lookup"><span data-stu-id="d0398-235">We edited this shader to make the Jupiter build work as intended.</span></span>

<span data-ttu-id="d0398-236">最後，您必須將來源 Blend 設定為10，並將目的地 Blend 設定為5，以設定 Alpha 融合。</span><span class="sxs-lookup"><span data-stu-id="d0398-236">Finally, the Alpha Blends needed to be set up by setting the Source Blend to 10 and the Destination Blend to 5.</span></span>

![Jupiter Unity 屬性](images/ge-update-jupiter-unity-render-queue.jpg)

<span data-ttu-id="d0398-238">您可以在 [Galaxy Explorer] 中看到 Jupiter 的最終呈現！</span><span class="sxs-lookup"><span data-stu-id="d0398-238">You can see the final rendering of Jupiter in Galaxy Explorer!</span></span>

## <a name="meet-the-team"></a><span data-ttu-id="d0398-239">認識團隊</span><span class="sxs-lookup"><span data-stu-id="d0398-239">Meet the team</span></span> 

<span data-ttu-id="d0398-240">我們的混合現實 studio 小組是由設計人員、3D 演出者、UX 專家、開發人員、程式經理和 studio 標頭所組成。</span><span class="sxs-lookup"><span data-stu-id="d0398-240">Our Mixed Reality studio team is made up of designers, 3D artists, UX specialists, developers, a program manager, and a studio head.</span></span> <span data-ttu-id="d0398-241">我們從全球各地 hail：比利時、加拿大、德國、以色列、日本、英國和美國。</span><span class="sxs-lookup"><span data-stu-id="d0398-241">We hail from all over the world: Belgium, Canada, Germany, Israel, Japan, the United Kingdom, and the United States.</span></span> <span data-ttu-id="d0398-242">我們是來自各種背景的豐富團隊：遊戲-傳統與獨立製作、數位行銷、醫療保健和科學。</span><span class="sxs-lookup"><span data-stu-id="d0398-242">We're a multidisciplinary team that comes from a diverse background: gaming - both traditional and indie, digital marketing, health care and science.</span></span>

<span data-ttu-id="d0398-243">我們很高興能建立 HoloLens 2 的 Galaxy Explorer，以及更新 HoloLens (第一代) 、VR 和桌上出版本。</span><span class="sxs-lookup"><span data-stu-id="d0398-243">We're excited to create Galaxy Explorer for HoloLens 2, and to update the HoloLens (first gen), VR, and desktop versions.</span></span> 

![Galaxy Explorer 小組](images/ge-update-team-image.png)

<span data-ttu-id="d0398-245">從左至右： Artemis Tsouflidou (Developer) 、Angie Teickner (Visual Designer) 、David Janer (UX 設計工具) 、劉娜 Garrett (交付 & 生產潛在客戶) 、Yasushi Zonno (創意領導人) 、Eline Ledent (開發人員) ，以及 Ben Turner (Sr-iov) 。</span><span class="sxs-lookup"><span data-stu-id="d0398-245">On top from left to right: Artemis Tsouflidou (Developer), Angie Teickner (Visual Designer), David Janer (UX Designer), Laura Garrett (Delivery & Production Lead), Yasushi Zonno (Creative Lead), Eline Ledent (Developer), and Ben Turner (Sr. Developer).</span></span>
<span data-ttu-id="d0398-246">從左至右： Amit Rojtblat (技術演出者) 、聖馬丁 Wettig (3D 演出者) 和 Dirk Songuer (Studio Head) 。</span><span class="sxs-lookup"><span data-stu-id="d0398-246">Bottom from left to right: Amit Rojtblat (Technical Artist), Martin Wettig (3D Artist), and Dirk Songuer (Studio Head).</span></span>
<span data-ttu-id="d0398-247">未精選： Tim Gerken (技術負責人) 和 Oscar Salandin (視覺化設計工具) 。</span><span class="sxs-lookup"><span data-stu-id="d0398-247">Not featured: Tim Gerken (Tech Lead) and Oscar Salandin (Visual Designer).</span></span>

## <a name="additional-information"></a><span data-ttu-id="d0398-248">其他資訊</span><span class="sxs-lookup"><span data-stu-id="d0398-248">Additional information</span></span>

### <a name="mixed-reality-studios"></a><span data-ttu-id="d0398-249">混合現實工作室</span><span class="sxs-lookup"><span data-stu-id="d0398-249">Mixed Reality Studios</span></span>

<span data-ttu-id="d0398-250">Microsoft Mixed Reality Studio 小組（位於美洲、歐洲和 Asia-Pacific）是使用者體驗設計、全像電腦運算、AR/VR 技術以及3D 開發的專家;包括建立3D 資產、DirectX、Unity 和 Unreal。</span><span class="sxs-lookup"><span data-stu-id="d0398-250">Microsoft Mixed Reality Studio teams - located in the Americas, Europe, and Asia-Pacific - are experts in user experience design, holographic computing, AR/VR technologies, and 3D development; including 3D asset creation, DirectX, Unity and Unreal.</span></span> <span data-ttu-id="d0398-251">我們會協助您構想所需的未來、設計、建立和提供解決方案，同時讓客戶能夠在其組織之間創造可測量的影響。</span><span class="sxs-lookup"><span data-stu-id="d0398-251">We help envision desired futures, design, build and deliver solutions, while enabling customers to create measurable impact across their organization.</span></span> <span data-ttu-id="d0398-252">工作室與超過22000的 Microsoft 服務專業人員密切合作，以進行企業應用程式整合、採用、操作及支援。</span><span class="sxs-lookup"><span data-stu-id="d0398-252">The studios work closely with over 22,000 Microsoft Services professionals for enterprise application integration, adoption, operations, and support.</span></span>