---
title: 混合現實應用程式的類型
description: 瞭解混合現實平臺所支援的體驗，從沉浸式環境到使用者環境中的輕量資訊分層。
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、應用程式模式、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens
ms.openlocfilehash: 795d8733b9f509a79d9429f75dff2f88a2a63c93
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007618"
---
# <a name="types-of-mixed-reality-apps"></a><span data-ttu-id="47a69-104">混合現實應用程式的類型</span><span class="sxs-lookup"><span data-stu-id="47a69-104">Types of mixed reality apps</span></span>

<span data-ttu-id="47a69-105">針對 Windows Mixed Reality 開發應用程式的優點之一，就是平臺可支援的體驗。</span><span class="sxs-lookup"><span data-stu-id="47a69-105">One of the advantages of developing apps for Windows Mixed Reality is the spectrum of experiences the platform can support.</span></span> <span data-ttu-id="47a69-106">從完全沉浸式虛擬環境到使用者目前環境下的輕量資訊分層，Windows Mixed Reality 提供了一組強大的工具，可將任何體驗變為現實。</span><span class="sxs-lookup"><span data-stu-id="47a69-106">From fully immersive, virtual environments, to light information layering over a user’s current environment, Windows Mixed Reality provides a robust set of tools to bring any experience to life.</span></span> <span data-ttu-id="47a69-107">應用程式製作者必須在開發過程中及早瞭解其體驗所在的範圍。</span><span class="sxs-lookup"><span data-stu-id="47a69-107">It's important for an app maker to understand early in their development process as to where along this spectrum their experience lies.</span></span> <span data-ttu-id="47a69-108">這項決策最終將會影響應用程式設計的組成，以及開發的技術途徑。</span><span class="sxs-lookup"><span data-stu-id="47a69-108">This decision will ultimately impact both the app design makeup and the technological path for development.</span></span>

## <a name="enhanced-environment-apps-hololens-only"></a><span data-ttu-id="47a69-109">增強的環境應用程式僅 (HoloLens) </span><span class="sxs-lookup"><span data-stu-id="47a69-109">Enhanced environment apps (HoloLens only)</span></span>

<span data-ttu-id="47a69-110">混合現實可能帶來價值的其中一種最強大的方式，就是讓開發人員將數位資訊或內容放在使用者目前的環境中。</span><span class="sxs-lookup"><span data-stu-id="47a69-110">One of the most powerful ways that mixed reality can bring value is letting developers place digital information or content in a user’s current environment.</span></span> <span data-ttu-id="47a69-111">這種方法最受歡迎的應用程式，是指真實世界中數位內容的內容位置是最重要的，而且在其體驗期間讓使用者的真實世界環境「呈現」相當重要。</span><span class="sxs-lookup"><span data-stu-id="47a69-111">This approach is popular for apps where the contextual placement of digital content in the real world is paramount and keeping the user’s real world environment “present” during their experience is key.</span></span> <span data-ttu-id="47a69-112">使用者也可以輕鬆地在真實世界的數位工作之間移動。</span><span class="sxs-lookup"><span data-stu-id="47a69-112">Users can also move between real world digital tasks with ease.</span></span> <span data-ttu-id="47a69-113">這可讓使用者所看到的混合現實應用程式真正成為其環境的一部分，以更 credence 的承諾。</span><span class="sxs-lookup"><span data-stu-id="47a69-113">This lends even more credence to the promise that the mixed reality apps the user sees are truly a part of their environment.</span></span>

<span data-ttu-id="47a69-114">![增強的環境應用程式](images/enhancedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="47a69-114">![Enhanced environment apps](images/enhancedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="47a69-115">*增強的環境應用程式*</span><span class="sxs-lookup"><span data-stu-id="47a69-115">*Enhanced environment apps*</span></span>

<span data-ttu-id="47a69-116">**範例使用**</span><span class="sxs-lookup"><span data-stu-id="47a69-116">**Example uses**</span></span>
* <span data-ttu-id="47a69-117">混合現實記事本樣式應用程式，可讓使用者在其環境中建立並放置附注</span><span class="sxs-lookup"><span data-stu-id="47a69-117">A mixed reality notepad style app that allows users to create and place notes around their environment</span></span>
* <span data-ttu-id="47a69-118">混合現實電視應用程式放在方便觀賞的地方</span><span class="sxs-lookup"><span data-stu-id="47a69-118">A mixed reality television app placed in a comfortable spot for viewing</span></span>
* <span data-ttu-id="47a69-119">混合的現實烹飪應用程式放在廚房島之上，以協助烹飪工作</span><span class="sxs-lookup"><span data-stu-id="47a69-119">A mixed reality cooking app placed above the kitchen island to help a cooking task</span></span>
* <span data-ttu-id="47a69-120">一種混合現實應用程式，讓使用者感覺「x 光線願景」 (也就是，放在最上層的全像 reality，並模擬實際的物件，同時讓使用者看到「內部」的) </span><span class="sxs-lookup"><span data-stu-id="47a69-120">A mixed reality app that gives users the feeling of “x-ray vision” (that is, a hologram placed on top of and mimics a real world object, while allowing the user to see “inside it” holographically)</span></span>
* <span data-ttu-id="47a69-121">整個工廠中的混合現實附注可提供工作者的必要資訊</span><span class="sxs-lookup"><span data-stu-id="47a69-121">Mixed reality annotations placed throughout a factory to give worker’s necessary information</span></span>
* <span data-ttu-id="47a69-122">在辦公室空間中尋找的混合現實方式</span><span class="sxs-lookup"><span data-stu-id="47a69-122">Mixed reality way finding in an office space</span></span>
* <span data-ttu-id="47a69-123">混合現實桌面體驗 (也就是電路板遊戲樣式的體驗) </span><span class="sxs-lookup"><span data-stu-id="47a69-123">Mixed reality tabletop experiences (that is, board game style experiences)</span></span>
* <span data-ttu-id="47a69-124">像 Skype 這樣的混合現實通訊應用程式</span><span class="sxs-lookup"><span data-stu-id="47a69-124">Mixed reality communication apps like Skype</span></span>

## <a name="blended-environment-apps"></a><span data-ttu-id="47a69-125">混合式環境應用程式</span><span class="sxs-lookup"><span data-stu-id="47a69-125">Blended environment apps</span></span>

<span data-ttu-id="47a69-126">假設 Windows Mixed Reality 能夠辨識和對應使用者的環境，就能建立可在使用者空間上重迭的數位層。</span><span class="sxs-lookup"><span data-stu-id="47a69-126">Given Windows Mixed Reality’s ability to recognize and map the user's environment, it's able to create a digital layer that can be overlaid on the user’s space.</span></span> <span data-ttu-id="47a69-127">精簡層會遵循使用者環境的圖形和界限，但應用程式可能會選擇轉換最適合在應用程式中 immerse 使用者的特定元素。</span><span class="sxs-lookup"><span data-stu-id="47a69-127">Thin layer respects the shape and boundaries of the user’s environment, but the app may choose to transform certain elements best suited to immerse the user in the app.</span></span> <span data-ttu-id="47a69-128">這稱為混合式環境應用程式。</span><span class="sxs-lookup"><span data-stu-id="47a69-128">This is called a blended environment app.</span></span> <span data-ttu-id="47a69-129">與增強的環境應用程式不同的是，混合式環境應用程式可能只在意環境的最大用途，以充分利用其構成專案來鼓勵特定的使用者行為 (例如鼓勵移動或探索) ，或藉由將 (廚房計數器的元素取代為 skinned 來顯示不同的磚模式) 。</span><span class="sxs-lookup"><span data-stu-id="47a69-129">Unlike an enhanced environment app, blended environment apps may only care enough about the environment to best use its makeup for encouraging specific user behavior (like encouraging movement or exploration) or by replacing elements with changes (a kitchen counter is skinned to show a different tile pattern).</span></span> <span data-ttu-id="47a69-130">這種體驗甚至可能會將專案轉換成完全不同的物件，但是仍會將物件的粗略尺寸保留為其基底 (將廚房島轉換為犯罪 thriller 遊戲) 的 dumpster。</span><span class="sxs-lookup"><span data-stu-id="47a69-130">This type of experience may even transform an element into an entirely different object, but still keep the rough dimensions of the object as its base (a kitchen island is transformed into a dumpster for a crime thriller game).</span></span>

<span data-ttu-id="47a69-131">![混合式環境應用程式](images/blendedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="47a69-131">![Blended environment apps](images/blendedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="47a69-132">*混合式環境應用程式*</span><span class="sxs-lookup"><span data-stu-id="47a69-132">*Blended environment apps*</span></span>

<span data-ttu-id="47a69-133">**範例使用**</span><span class="sxs-lookup"><span data-stu-id="47a69-133">**Example uses**</span></span>
* <span data-ttu-id="47a69-134">混合現實內部設計應用程式，可以使用不同的色彩和模式來繪製牆、countertops 或地面</span><span class="sxs-lookup"><span data-stu-id="47a69-134">A mixed reality interior design app that can paint walls, countertops, or floors in different colors and patterns</span></span>
* <span data-ttu-id="47a69-135">混合的現實應用程式，可讓汽車設計工具將新的設計反復專案分層，以在現有汽車上進行未來的汽車重新整理</span><span class="sxs-lookup"><span data-stu-id="47a69-135">A mixed reality app that allows an automotive designer to layer new design iterations for an upcoming car refresh on top of an existing car</span></span>
* <span data-ttu-id="47a69-136">床被「涵蓋」，並取代為兒童遊戲中的混合現實水果</span><span class="sxs-lookup"><span data-stu-id="47a69-136">A bed is “covered” and replaced by a mixed reality fruit stand in children’s game</span></span>
* <span data-ttu-id="47a69-137">在犯罪 thriller 遊戲中，會「涵蓋」辦公桌並取代為混合現實 dumpster</span><span class="sxs-lookup"><span data-stu-id="47a69-137">A desk is “covered” and replaced with a mixed reality dumpster in a crime thriller game</span></span>
* <span data-ttu-id="47a69-138">「已涵蓋」的懸掛 lantern 會使用大致相同的圖形和維度，取代為 signpost</span><span class="sxs-lookup"><span data-stu-id="47a69-138">A hanging lantern is “covered” and replaced with signpost using roughly the same shape and dimension</span></span>
* <span data-ttu-id="47a69-139">此應用程式可讓使用者在其真實或沉浸式的世界中，在神奇世界</span><span class="sxs-lookup"><span data-stu-id="47a69-139">An app that allows users to blast holes in their real or immersive world walls, which reveal a magical world</span></span>

## <a name="immersive-environment-apps"></a><span data-ttu-id="47a69-140">沉浸式環境應用程式</span><span class="sxs-lookup"><span data-stu-id="47a69-140">Immersive environment apps</span></span>

<span data-ttu-id="47a69-141">沉浸式環境應用程式是以完全變更使用者世界的環境為中心，並且可以將它們放在不同的時間和空間中。</span><span class="sxs-lookup"><span data-stu-id="47a69-141">Immersive environment apps are centered around an environment that completely changes the user’s world and can place them in a different time and space.</span></span> <span data-ttu-id="47a69-142">這些環境可感受到真正的效果，建立只受應用程式建立者的夢想所限制的沉浸式和「驚心動魄」體驗。</span><span class="sxs-lookup"><span data-stu-id="47a69-142">These environments can feel real, creating immersive and thrilling experiences that are only limited by the app creator’s imagination.</span></span> <span data-ttu-id="47a69-143">和混合式環境應用程式不同的是，當 Windows Mixed Reality 識別出使用者的空間之後，沉浸式環境應用程式可能會完全忽略使用者目前的環境，並以它自己的其中一個來取代整個股票。</span><span class="sxs-lookup"><span data-stu-id="47a69-143">Unlike blended environment apps, once Windows Mixed Reality identifies the user’s space, an immersive environment app may totally disregard the user’s current environment and replace it whole stock with one of its own.</span></span> <span data-ttu-id="47a69-144">這些經驗也可以區隔時間和空間，這表示使用者可以在沉浸式體驗中將羅馬的街道帶到最少，而剩下的也相當於真實世界的空間。</span><span class="sxs-lookup"><span data-stu-id="47a69-144">These experiences may also separate time and space, meaning a user could walk the streets of Rome in an immersive experience, while remaining relatively still in their real world space.</span></span> <span data-ttu-id="47a69-145">真實世界環境的內容對沉浸式環境應用程式而言可能不重要。</span><span class="sxs-lookup"><span data-stu-id="47a69-145">Context of the real world environment may not be important to an immersive environment app.</span></span>

<span data-ttu-id="47a69-146">![沉浸式環境應用程式](images/windows-mixed-reality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="47a69-146">![Immersive environment apps](images/windows-mixed-reality-640px.jpg)</span></span><br>
<span data-ttu-id="47a69-147">*沉浸式環境應用程式*</span><span class="sxs-lookup"><span data-stu-id="47a69-147">*Immersive environment apps*</span></span>

<span data-ttu-id="47a69-148">**範例使用**</span><span class="sxs-lookup"><span data-stu-id="47a69-148">**Example uses**</span></span>
* <span data-ttu-id="47a69-149">一個沉浸式應用程式，可讓使用者導覽不同的空間 (也就是，逐步解說知名大樓、博物館、熱門城市) </span><span class="sxs-lookup"><span data-stu-id="47a69-149">An immersive app that lets a user tour a space separate from their own (that is, walk through a famous building, museum, popular city)</span></span>
* <span data-ttu-id="47a69-150">一個沉浸式應用程式，可協調使用者 (的事件或案例，也就是一項工作或效能) </span><span class="sxs-lookup"><span data-stu-id="47a69-150">An immersive app that orchestrates an event or scenario around the user (that is, a battle or a performance)</span></span>

## <a name="see-also"></a><span data-ttu-id="47a69-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47a69-151">See also</span></span>

* [<span data-ttu-id="47a69-152">開發概觀</span><span class="sxs-lookup"><span data-stu-id="47a69-152">Development overview</span></span>](../develop/development.md)
* [<span data-ttu-id="47a69-153">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="47a69-153">App model</span></span>](app-model.md)
* [<span data-ttu-id="47a69-154">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="47a69-154">App views</span></span>](app-views.md)
