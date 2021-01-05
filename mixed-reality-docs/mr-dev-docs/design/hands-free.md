---
title: 免持式
description: 深入瞭解使用者可能會面對的手入控制器介面，以及各種免參與的替代方案。
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality、免持手、注視、注視目標、互動、設計、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、語音輸入、可用性
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847679"
---
# <a name="hands-free"></a><span data-ttu-id="ac7c5-104">免持式</span><span class="sxs-lookup"><span data-stu-id="ac7c5-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="ac7c5-105">案例</span><span class="sxs-lookup"><span data-stu-id="ac7c5-105">Scenarios</span></span>

<span data-ttu-id="ac7c5-106">如 [互動模型](interaction-fundamentals.md)中所述，當您識別出使用者及其目標之後，請自問他們在完成其工作時可能面臨的環境或環境問題。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you've identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="ac7c5-107">例如，許多使用者都必須使用他們的手來完成其真實世界的目標，而這些使用者將難以與以操作站為基礎的介面互動。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-107">For example, many users need to use their hands to accomplish their real-world goals, and they'll have difficulty interacting with a hands-and-controllers based interface.</span></span>

<span data-ttu-id="ac7c5-108">部分特定案例包括：</span><span class="sxs-lookup"><span data-stu-id="ac7c5-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="ac7c5-109">當使用者的雙手忙碌時，可利用引導來完成工作</span><span class="sxs-lookup"><span data-stu-id="ac7c5-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="ac7c5-110">當使用者的雙手忙碌時參考資料</span><span class="sxs-lookup"><span data-stu-id="ac7c5-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="ac7c5-111">手部疲勞</span><span class="sxs-lookup"><span data-stu-id="ac7c5-111">Hand fatigue</span></span>
* <span data-ttu-id="ac7c5-112">無法追蹤的手套</span><span class="sxs-lookup"><span data-stu-id="ac7c5-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="ac7c5-113">手拿東西</span><span class="sxs-lookup"><span data-stu-id="ac7c5-113">Carrying something in their hands</span></span>
* <span data-ttu-id="ac7c5-114">使用大量手勢時的社交 awkwardness</span><span class="sxs-lookup"><span data-stu-id="ac7c5-114">Social awkwardness when using large hand gestures</span></span>
* <span data-ttu-id="ac7c5-115">空間狹窄</span><span class="sxs-lookup"><span data-stu-id="ac7c5-115">Tight spaces</span></span>

## <a name="hands-free-modalities"></a><span data-ttu-id="ac7c5-116">免手形式</span><span class="sxs-lookup"><span data-stu-id="ac7c5-116">Hands-free modalities</span></span>

### <a name="voice-input"></a>[<span data-ttu-id="ac7c5-117">語音輸入</span><span class="sxs-lookup"><span data-stu-id="ac7c5-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="ac7c5-118">使用您的語音來命令和控制介面可提供便利的方式來操作無人參與，並視需要使用快捷方式略過多個步驟。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to skip multiple steps if you want.</span></span> <span data-ttu-id="ac7c5-119">使用語音輸入時，使用者可以大聲朗讀任何按鈕的名稱來啟用它 _( 「查看它」 )_ 並與可為您完成工作的數位代理程式交談。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-119">With voice input, the user can read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>

### <a name="gaze-and-dwell"></a>[<span data-ttu-id="ac7c5-120">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="ac7c5-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="ac7c5-121">在某些免操作的情況下，使用您的聲音不是理想或甚至可能。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-121">In some hands-free situations, using your voice isn't ideal or even possible.</span></span> <span data-ttu-id="ac7c5-122">很高的工廠環境、隱私權或社會規範都可以是條件約束。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="ac7c5-123">「注視 + 停留」模型可讓使用者在不需要任何額外的輸入的情況下，流覽應用程式，而不需要任何額外的輸入，因為使用者只會在目標上保持撥雲見日)  (，並 lingers 一段時間來啟用它。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-123">The gaze + dwell model allows the user to navigate an app without any extra input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="ac7c5-124">若要深入瞭解「注視 + 停留」的個別設計考慮，請查看 [眼睛](gaze-and-dwell-eyes.md) 和中的眼睛 [+ 停留](gaze-and-dwell-head.md)。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="ac7c5-125">無人參與的轉換</span><span class="sxs-lookup"><span data-stu-id="ac7c5-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="ac7c5-126">在這些情況下，讓您的手與可進行命令和流覽的全像投影互動，可能是從端對端操作應用程式的絕對需求，一直到使用者可以隨時轉換的額外便利性。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="ac7c5-127">如果應用程式要求一律使用「停留」、「自訂語音命令」或「單一語音」命令（「選取」），請務必在您的 UI 中做出適當的住宿。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-127">If the application requires that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="ac7c5-128">如果您的目標使用者需要自行決定是否要親自切換，則請務必考慮下列準則。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-128">If your target user needs to switch from hands to hands-free at their discretion, then it's important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="ac7c5-129">假設使用者已經處於想要切換的模式</span><span class="sxs-lookup"><span data-stu-id="ac7c5-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="ac7c5-130">比方說，如果使用者是在工廠，在 HoloLens 上觀賞影片參考，並決定挑選扳手以開始工作，她最有可能開始操作，而不需要減少扳手來按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="ac7c5-131">她可以使用語音命令叫用語音會話、停留在已可見的 UI 上以開始停留，或說「選取」這個字。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-131">She can invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="ac7c5-132">使用者可以：</span><span class="sxs-lookup"><span data-stu-id="ac7c5-132">The user can:</span></span> 
* <span data-ttu-id="ac7c5-133">無人參與，請切換為無人參與</span><span class="sxs-lookup"><span data-stu-id="ac7c5-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="ac7c5-134">改用您的手</span><span class="sxs-lookup"><span data-stu-id="ac7c5-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="ac7c5-135">使用控制器切換至控制器</span><span class="sxs-lookup"><span data-stu-id="ac7c5-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="ac7c5-136">建立切換模式的重複方式</span><span class="sxs-lookup"><span data-stu-id="ac7c5-136">Create redundant ways to switch modes</span></span>

<span data-ttu-id="ac7c5-137">第一個原則是關於存取權，第二個原則是關於可用性。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="ac7c5-138">您不應該只是在模式中進行轉換的單一方法。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-138">There shouldn't just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="ac7c5-139">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="ac7c5-139">Some examples would be:</span></span> 
* <span data-ttu-id="ac7c5-140">開始語音互動的按鈕</span><span class="sxs-lookup"><span data-stu-id="ac7c5-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="ac7c5-141">要轉換成的聲音命令，使用前端和停留</span><span class="sxs-lookup"><span data-stu-id="ac7c5-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="ac7c5-142">新增戲劇的虛線</span><span class="sxs-lookup"><span data-stu-id="ac7c5-142">Add a dash of drama</span></span>

<span data-ttu-id="ac7c5-143">模式參數是一項很大的處理。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-143">A mode switch is a big deal.</span></span> <span data-ttu-id="ac7c5-144">當這些轉換發生明確（甚至是很大的參數）時，請務必讓使用者知道發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-144">It's important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 

## <a name="usability-checklist"></a><span data-ttu-id="ac7c5-145">可用性檢查清單</span><span class="sxs-lookup"><span data-stu-id="ac7c5-145">Usability checklist</span></span>

<span data-ttu-id="ac7c5-146">**使用者是否可以進行任何動作，而不需要端對端？**</span><span class="sxs-lookup"><span data-stu-id="ac7c5-146">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="ac7c5-147">每個互動都應該可無人參與</span><span class="sxs-lookup"><span data-stu-id="ac7c5-147">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="ac7c5-148">確定所有自訂手勢都有取代，例如調整大小、放置、撥動、點擊等。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-148">Ensure that there's a replacement for all custom gestures, such as resizing, placing, swipes, taps, and so on.</span></span>
* <span data-ttu-id="ac7c5-149">確定使用者可以永遠控制 UI 的出現、放置和詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ac7c5-149">Ensure that the user has confident control of UI presence, placement, and verbosity always</span></span>
    * <span data-ttu-id="ac7c5-150">無法取得 UI</span><span class="sxs-lookup"><span data-stu-id="ac7c5-150">Getting UI out of the way</span></span>
    * <span data-ttu-id="ac7c5-151">將不在視野內的 UI 定址 (FOV) </span><span class="sxs-lookup"><span data-stu-id="ac7c5-151">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="ac7c5-152">我看到的是多少，哪裡</span><span class="sxs-lookup"><span data-stu-id="ac7c5-152">How much I see, where, when</span></span>

<span data-ttu-id="ac7c5-153">**使用正確的 affordances 來教授和加強互動的機制？**</span><span class="sxs-lookup"><span data-stu-id="ac7c5-153">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="ac7c5-154">使用者是否瞭解 .。。</span><span class="sxs-lookup"><span data-stu-id="ac7c5-154">Does the user understand ...</span></span>
* <span data-ttu-id="ac7c5-155">...它們在哪個模式中？</span><span class="sxs-lookup"><span data-stu-id="ac7c5-155">... What mode they are in?</span></span>
* <span data-ttu-id="ac7c5-156">...在此模式中可以怎麼做？</span><span class="sxs-lookup"><span data-stu-id="ac7c5-156">... What they can do in this mode?</span></span>
* <span data-ttu-id="ac7c5-157">...目前的狀態為何？</span><span class="sxs-lookup"><span data-stu-id="ac7c5-157">... What is the current state?</span></span>
* <span data-ttu-id="ac7c5-158">...如何進行轉換？</span><span class="sxs-lookup"><span data-stu-id="ac7c5-158">... How they can transition out?</span></span>
    
<span data-ttu-id="ac7c5-159">**UI 是否已針對無人參與優化？**</span><span class="sxs-lookup"><span data-stu-id="ac7c5-159">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="ac7c5-160">範例：停留 affordances 未內建至一般2D 模式</span><span class="sxs-lookup"><span data-stu-id="ac7c5-160">Example: Dwell affordances aren't built in to typical 2D patterns</span></span>
* <span data-ttu-id="ac7c5-161">範例：使用物件反白顯示時，語音目標更好</span><span class="sxs-lookup"><span data-stu-id="ac7c5-161">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="ac7c5-162">範例：語音互動優於需要開啟的標題</span><span class="sxs-lookup"><span data-stu-id="ac7c5-162">Example: Voice interactions are better with captions that need to be turned on</span></span>

## <a name="see-also"></a><span data-ttu-id="ac7c5-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="ac7c5-163">See also</span></span>

* [<span data-ttu-id="ac7c5-164">HoloLens 2 的眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="ac7c5-164">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="ac7c5-165">目光和行動</span><span class="sxs-lookup"><span data-stu-id="ac7c5-165">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ac7c5-166">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="ac7c5-166">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="ac7c5-167">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="ac7c5-167">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ac7c5-168">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="ac7c5-168">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="ac7c5-169">手 - 指向和行動</span><span class="sxs-lookup"><span data-stu-id="ac7c5-169">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="ac7c5-170">本能互動</span><span class="sxs-lookup"><span data-stu-id="ac7c5-170">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="ac7c5-171">語音輸入</span><span class="sxs-lookup"><span data-stu-id="ac7c5-171">Voice input</span></span>](voice-input.md)
