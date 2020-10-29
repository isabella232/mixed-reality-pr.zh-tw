---
title: 混合實境應用程式類型
description: 針對 Windows Mixed Reality 開發應用程式的其中一項優點是，平臺可透過使用者目前的 environmentl，從完全沉浸式的虛擬環境支援的各種體驗，到輕量資訊的分層。
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、應用程式模式
ms.openlocfilehash: 5d2fa3a5d83f878009f4574c3468719c9af17014
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680417"
---
# <a name="types-of-mixed-reality-apps"></a><span data-ttu-id="65edc-104">混合實境應用程式類型</span><span class="sxs-lookup"><span data-stu-id="65edc-104">Types of mixed reality apps</span></span>

<span data-ttu-id="65edc-105">開發 Windows Mixed Reality 應用程式的優點之一，是該平台可以支援各種頻譜體驗。</span><span class="sxs-lookup"><span data-stu-id="65edc-105">One of the advantages of developing apps for Windows Mixed Reality is that there is a spectrum of experiences that the platform can support.</span></span> <span data-ttu-id="65edc-106">從完全沉浸式虛擬環境到使用者目前環境下的輕量資訊分層，Windows Mixed Reality 提供了一組強大的工具，可將任何體驗變為現實。</span><span class="sxs-lookup"><span data-stu-id="65edc-106">From fully immersive, virtual environments, to light information layering over a user’s current environment, Windows Mixed Reality provides a robust set of tools to bring any experience to life.</span></span> <span data-ttu-id="65edc-107">應用程式製作者必須在開發過程中及早瞭解其體驗所在的範圍。</span><span class="sxs-lookup"><span data-stu-id="65edc-107">It is important for an app maker to understand early in their development process as to where along this spectrum their experience lies.</span></span> <span data-ttu-id="65edc-108">這項決策最終將會影響應用程式設計的組成，以及開發的技術途徑。</span><span class="sxs-lookup"><span data-stu-id="65edc-108">This decision will ultimately impact both the app design makeup and the technological path for development.</span></span>

## <a name="enhanced-environment-apps-hololens-only"></a><span data-ttu-id="65edc-109">增強的環境應用程式僅 (HoloLens) </span><span class="sxs-lookup"><span data-stu-id="65edc-109">Enhanced environment apps (HoloLens only)</span></span>

<span data-ttu-id="65edc-110">混合現實能為使用者帶來價值的其中一種最強大的方式，就是在使用者的目前環境中加速數位資訊或內容的位置。</span><span class="sxs-lookup"><span data-stu-id="65edc-110">One of the most powerful ways that mixed reality can bring value to users is by facilitating the placement of digital information or content in a user’s current environment.</span></span> <span data-ttu-id="65edc-111">這是增強的環境應用程式。</span><span class="sxs-lookup"><span data-stu-id="65edc-111">This is an enhanced environment app.</span></span> <span data-ttu-id="65edc-112">這種方法很常用於應用程式，在這種情況下，真實世界中數位內容的內容位置是最重要的，而且/或保持使用者的真實世界環境在其體驗中是關鍵的。</span><span class="sxs-lookup"><span data-stu-id="65edc-112">This approach is popular for apps where the contextual placement of digital content in the real world is paramount and/or keeping the user’s real world environment “present” during their experience is key.</span></span> <span data-ttu-id="65edc-113">這種方法也可以讓使用者輕鬆地從真實世界的工作移至數位工作，還可讓使用者更有 credence，以保證使用者看到的混合現實應用程式確實是其環境的一部分。</span><span class="sxs-lookup"><span data-stu-id="65edc-113">This approach also allows users to easily move from real world tasks to digital tasks and back easily, lending even more credence to promise that the mixed reality apps the user sees are truly a part of their environment.</span></span>

<span data-ttu-id="65edc-114">![增強的環境應用程式](images/enhancedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="65edc-114">![Enhanced environment apps](images/enhancedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="65edc-115">*增強的環境應用程式*</span><span class="sxs-lookup"><span data-stu-id="65edc-115">*Enhanced environment apps*</span></span>

<span data-ttu-id="65edc-116">**範例使用**</span><span class="sxs-lookup"><span data-stu-id="65edc-116">**Example uses**</span></span>
* <span data-ttu-id="65edc-117">混合現實記事本樣式應用程式，可讓使用者在其環境中建立並放置附注</span><span class="sxs-lookup"><span data-stu-id="65edc-117">A mixed reality notepad style app that allows users to create and place notes around their environment</span></span>
* <span data-ttu-id="65edc-118">混合現實電視應用程式放在方便觀賞的地方</span><span class="sxs-lookup"><span data-stu-id="65edc-118">A mixed reality television app placed in a comfortable spot for viewing</span></span>
* <span data-ttu-id="65edc-119">放在廚房島上方的混合現實烹飪應用程式，可協助您進行烹飪工作</span><span class="sxs-lookup"><span data-stu-id="65edc-119">A mixed reality cooking app placed above the kitchen island to assist in a cooking task</span></span>
* <span data-ttu-id="65edc-120">一種混合現實應用程式，讓使用者感覺「x 光線願景」 (也就是，放在最上層的全像影像，並模擬實際的物件，同時讓使用者看到「內部」 reality) </span><span class="sxs-lookup"><span data-stu-id="65edc-120">A mixed reality app that gives users the feeling of “x-ray vision” (i.e. a hologram placed on top of and mimics a real world object, while allowing the user to see “inside it” holographically)</span></span>
* <span data-ttu-id="65edc-121">整個工廠中的混合現實附注可提供工作者的必要資訊</span><span class="sxs-lookup"><span data-stu-id="65edc-121">Mixed reality annotations placed throughout a factory to give worker’s necessary information</span></span>
* <span data-ttu-id="65edc-122">辦公室空間中的混合現實導向</span><span class="sxs-lookup"><span data-stu-id="65edc-122">Mixed reality wayfinding in an office space</span></span>
* <span data-ttu-id="65edc-123">混合現實桌面體驗 (例如電路板遊戲樣式體驗) </span><span class="sxs-lookup"><span data-stu-id="65edc-123">Mixed reality tabletop experiences (i.e. board game style experiences)</span></span>
* <span data-ttu-id="65edc-124">像 Skype 這樣的混合現實通訊應用程式</span><span class="sxs-lookup"><span data-stu-id="65edc-124">Mixed reality communication apps like Skype</span></span>

## <a name="blended-environment-apps"></a><span data-ttu-id="65edc-125">混合式環境應用程式</span><span class="sxs-lookup"><span data-stu-id="65edc-125">Blended environment apps</span></span>

<span data-ttu-id="65edc-126">由於有 Windows Mixed Reality 辨識和對應使用者環境的能力，因此能夠建立可在使用者空間上完全重迭的數位層。</span><span class="sxs-lookup"><span data-stu-id="65edc-126">Given Windows Mixed Reality’s ability to recognize and map the user's environment, it is capable of creating a digital layer that can be completely overlaid on the user’s space.</span></span> <span data-ttu-id="65edc-127">精簡層會遵循使用者環境的圖形和界限，但應用程式可能會選擇轉換最適合在應用程式中 immerse 使用者的特定元素。</span><span class="sxs-lookup"><span data-stu-id="65edc-127">Thin layer respects the shape and boundaries of the user’s environment, but the app may choose to transform certain elements best suited to immerse the user in the app.</span></span> <span data-ttu-id="65edc-128">這稱為混合式環境應用程式。</span><span class="sxs-lookup"><span data-stu-id="65edc-128">This is called a blended environment app.</span></span> <span data-ttu-id="65edc-129">與增強的環境應用程式不同的是，混合式環境應用程式可能只在意環境的最大用途，以充分利用其構成專案來鼓勵特定的使用者行為 (例如鼓勵移動或探索) ，或藉由將元素取代為 (廚房計數器來顯示不同的磚模式) 。</span><span class="sxs-lookup"><span data-stu-id="65edc-129">Unlike an enhanced environment app, blended environment apps may only care enough about the environment to best use its makeup for encouraging specific user behavior (like encouraging movement or exploration) or by replacing elements with changes (a kitchen counter is virtually skinned to show a different tile pattern).</span></span> <span data-ttu-id="65edc-130">這種體驗甚至可能會將專案轉換成完全不同的物件，但是仍會將物件的粗略尺寸保留為其基底 (將廚房島轉換為犯罪 thriller 遊戲) 的 dumpster。</span><span class="sxs-lookup"><span data-stu-id="65edc-130">This type of experience may even transform an element into an entirely different object, but still retain the rough dimensions of the object as its base (a kitchen island is transformed into a dumpster for a crime thriller game).</span></span>

<span data-ttu-id="65edc-131">![混合式環境應用程式](images/blendedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="65edc-131">![Blended environment apps](images/blendedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="65edc-132">*混合式環境應用程式*</span><span class="sxs-lookup"><span data-stu-id="65edc-132">*Blended environment apps*</span></span>

<span data-ttu-id="65edc-133">**範例使用**</span><span class="sxs-lookup"><span data-stu-id="65edc-133">**Example uses**</span></span>
* <span data-ttu-id="65edc-134">混合現實內部設計應用程式，可以使用不同的色彩和模式來繪製牆、countertops 或地面</span><span class="sxs-lookup"><span data-stu-id="65edc-134">A mixed reality interior design app that can paint walls, countertops or floors in different colors and patterns</span></span>
* <span data-ttu-id="65edc-135">混合的現實應用程式，可讓汽車設計工具將新的設計反復專案分層，以在現有汽車上進行未來的汽車重新整理</span><span class="sxs-lookup"><span data-stu-id="65edc-135">A mixed reality app that allows an automotive designer to layer new design iterations for an upcoming car refresh on top of an existing car</span></span>
* <span data-ttu-id="65edc-136">床被「涵蓋」，並取代為兒童遊戲中的混合現實水果</span><span class="sxs-lookup"><span data-stu-id="65edc-136">A bed is “covered” and replaced by a mixed reality fruit stand in children’s game</span></span>
* <span data-ttu-id="65edc-137">在犯罪 thriller 遊戲中，會「涵蓋」辦公桌並取代為混合現實 dumpster</span><span class="sxs-lookup"><span data-stu-id="65edc-137">A desk is “covered” and replaced with a mixed reality dumpster in a crime thriller game</span></span>
* <span data-ttu-id="65edc-138">「已涵蓋」的懸掛 lantern 會使用大致相同的圖形和維度，取代為 signpost</span><span class="sxs-lookup"><span data-stu-id="65edc-138">A hanging lantern is “covered” and replaced with signpost using roughly the same shape and dimension</span></span>
* <span data-ttu-id="65edc-139">此應用程式可讓使用者在其真實或沉浸式的世界中，在神奇世界</span><span class="sxs-lookup"><span data-stu-id="65edc-139">An app that allows users to blast holes in their real or immersive world walls, which reveal a magical world</span></span>

## <a name="immersive-environment-apps"></a><span data-ttu-id="65edc-140">沉浸式環境應用程式</span><span class="sxs-lookup"><span data-stu-id="65edc-140">Immersive environment apps</span></span>

<span data-ttu-id="65edc-141">沉浸式環境應用程式是以完全變更使用者世界的環境為中心，並且可以將它們放在不同的時間和空間中。</span><span class="sxs-lookup"><span data-stu-id="65edc-141">Immersive environment apps are centered around an environment that completely changes the user’s world and can place them in a different time and space.</span></span> <span data-ttu-id="65edc-142">這些環境可能非常真實，建立只受應用程式建立者的夢想所限制的沉浸式和「驚心動魄」體驗。</span><span class="sxs-lookup"><span data-stu-id="65edc-142">These environments can feel very real, creating immersive and thrilling experiences that are only limited by the app creator’s imagination.</span></span> <span data-ttu-id="65edc-143">和混合式環境應用程式不同的是，當 Windows Mixed Reality 識別出使用者的空間之後，沉浸式環境應用程式可能會完全忽略使用者目前的環境，並以它自己的其中一個來取代整個股票。</span><span class="sxs-lookup"><span data-stu-id="65edc-143">Unlike blended environment apps, once Windows Mixed Reality identifies the user’s space, an immersive environment app may totally disregard the user’s current environment and replace it whole stock with one of its own.</span></span> <span data-ttu-id="65edc-144">這些經驗也可能會完全分開的時間和空間，這表示使用者可以在沉浸式體驗中，將羅馬的街道帶到最少，而剩下的也相當於真實世界的空間。</span><span class="sxs-lookup"><span data-stu-id="65edc-144">These experiences may also completely separate time and space, meaning a user could walk the streets of Rome in an immersive experience, while remaining relatively still in their real world space.</span></span> <span data-ttu-id="65edc-145">真實世界環境的內容對沉浸式環境應用程式而言可能不重要。</span><span class="sxs-lookup"><span data-stu-id="65edc-145">Context of the real world environment may not be important to an immersive environment app.</span></span>

<span data-ttu-id="65edc-146">![沉浸式環境應用程式](images/windows-mixed-reality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="65edc-146">![Immersive environment apps](images/windows-mixed-reality-640px.jpg)</span></span><br>
<span data-ttu-id="65edc-147">*沉浸式環境應用程式*</span><span class="sxs-lookup"><span data-stu-id="65edc-147">*Immersive environment apps*</span></span>

<span data-ttu-id="65edc-148">**範例使用**</span><span class="sxs-lookup"><span data-stu-id="65edc-148">**Example uses**</span></span>
* <span data-ttu-id="65edc-149">一個沉浸式應用程式，可讓使用者導覽與自己不同的空間 (例如，逐步解說知名大樓、博物館、熱門城市) </span><span class="sxs-lookup"><span data-stu-id="65edc-149">An immersive app that lets a user tour a space completely separate from their own (i.e. walk through a famous building, museum, popular city)</span></span>
* <span data-ttu-id="65edc-150">一個沉浸式應用程式，可協調使用者的事件或案例 (也就是一或一則效能) </span><span class="sxs-lookup"><span data-stu-id="65edc-150">An immersive app that orchestrates an event or scenario around the user (i.e. a battle or a performance)</span></span>

## <a name="see-also"></a><span data-ttu-id="65edc-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65edc-151">See also</span></span>
* [<span data-ttu-id="65edc-152">開發概觀</span><span class="sxs-lookup"><span data-stu-id="65edc-152">Development overview</span></span>](../develop/development.md)
* [<span data-ttu-id="65edc-153">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="65edc-153">App model</span></span>](app-model.md)
* [<span data-ttu-id="65edc-154">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="65edc-154">App views</span></span>](app-views.md)
