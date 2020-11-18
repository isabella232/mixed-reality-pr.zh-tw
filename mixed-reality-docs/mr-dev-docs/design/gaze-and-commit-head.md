---
title: 頭部注視並認可
description: 頭部注視並認可輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: 混合的現實、注視、注視目標、互動、設計、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、目標、焦點、平滑
ms.openlocfilehash: d913ac81e20962d38178223a050fdccfb51d8632
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702384"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="34289-104">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="34289-104">Head-gaze and commit</span></span>
<span data-ttu-id="34289-105">_前端和認可_ 是 [注視和認可](gaze-and-commit.md) 輸入模型的特殊案例，其牽涉到將物件的方向指向順向 (前端方向) ，然後使用次要輸入（例如手勢的點擊點或語音命令「選取」）進行處理。</span><span class="sxs-lookup"><span data-stu-id="34289-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with the direction of your head pointing forward (head-direction), and then acting on it with a secondary input, such as the hand gesture air tap or the voice command "Select".</span></span> 

## <a name="device-support"></a><span data-ttu-id="34289-106">裝置支援</span><span class="sxs-lookup"><span data-stu-id="34289-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="34289-107"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="34289-107"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="34289-108"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="34289-108"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="34289-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="34289-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="34289-110"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="34289-110"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="34289-111">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="34289-111">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="34289-112">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="34289-112">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="34289-113">✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</span><span class="sxs-lookup"><span data-stu-id="34289-113">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="34289-114">➕ 替代選項</span><span class="sxs-lookup"><span data-stu-id="34289-114">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="34289-115">目標大小調整和回饋</span><span class="sxs-lookup"><span data-stu-id="34289-115">Target sizing and feedback</span></span>
<span data-ttu-id="34289-116">前端圖向量已重複顯示，可供適當的目標使用，但通常最適合用於主要目標--取得較大的目標。</span><span class="sxs-lookup"><span data-stu-id="34289-116">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring somewhat larger targets.</span></span> <span data-ttu-id="34289-117">最小的目標大小為1到1.5 度，在大部分情況下允許成功的使用者動作，但以3度為目標的目標通常會有更高的速度。</span><span class="sxs-lookup"><span data-stu-id="34289-117">Minimum target sizes of 1 to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="34289-118">請注意，使用者定向的大小實際上是 2D 區域 (即使是 3D 元素)，無論哪個投影面向他們都應該是可作為目標的區域。</span><span class="sxs-lookup"><span data-stu-id="34289-118">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="34289-119">提供某個元素為「作用中」的一些重要提示， (使用者以它為目標) 相當有用。</span><span class="sxs-lookup"><span data-stu-id="34289-119">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful.</span></span> <span data-ttu-id="34289-120">這可能包含像是可見的「暫止」效果、反白顯示或按下的處理，或清除資料指標與元素的對齊。</span><span class="sxs-lookup"><span data-stu-id="34289-120">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="34289-121">![距離 2 公尺的最佳目標大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="34289-121">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="34289-122">*距離 2 公尺的最佳目標大小*</span><span class="sxs-lookup"><span data-stu-id="34289-122">*Optimal target size at 2 meter distance*</span></span>

<br>

<span data-ttu-id="34289-123">![醒目提示注視目標物件的範例](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="34289-123">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="34289-124">*醒目提示注視目標物件的範例*</span><span class="sxs-lookup"><span data-stu-id="34289-124">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="34289-125">目標位置</span><span class="sxs-lookup"><span data-stu-id="34289-125">Target placement</span></span>
<span data-ttu-id="34289-126">使用者通常會在其視野中找不到非常高或非常低的 UI 元素，著重在其主要焦點區域周圍（大約是眼睛）。</span><span class="sxs-lookup"><span data-stu-id="34289-126">Users often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="34289-127">將大部分的目標放在眼部水平周圍的合理頻帶會有所幫助。</span><span class="sxs-lookup"><span data-stu-id="34289-127">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="34289-128">假設使用者傾向於隨時將焦點放在相對較小的視覺區域 (視覺的注意視錐大約是 10 度)，將概念上相關的 UI 元素聚集在一起，可以在使用者目光掃過區域時運用逐一項目的注意鏈結行為。</span><span class="sxs-lookup"><span data-stu-id="34289-128">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="34289-129">在設計 UI 時，請記住 HoloLens 與沉浸式頭戴裝置之間的視野可能有很大的變化。</span><span class="sxs-lookup"><span data-stu-id="34289-129">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="34289-130">![方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="34289-130">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="34289-131">*方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例*</span><span class="sxs-lookup"><span data-stu-id="34289-131">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="34289-132">改善定向行為</span><span class="sxs-lookup"><span data-stu-id="34289-132">Improving targeting behaviors</span></span>
<span data-ttu-id="34289-133">如果將目標設為目標的使用者意圖可 (或近似值緊密地) ，則在互動時接受近乎遺漏的嘗試，可能會很有説明，因為它們的目標正確。</span><span class="sxs-lookup"><span data-stu-id="34289-133">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept near miss attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="34289-134">以下是一些可在混合現實體驗中併入的成功方法：</span><span class="sxs-lookup"><span data-stu-id="34289-134">Here are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="34289-135">頭部注視穩定 (「重力穴」)</span><span class="sxs-lookup"><span data-stu-id="34289-135">Head-gaze stabilization ("gravity wells")</span></span>
<span data-ttu-id="34289-136">這應該會在大部分或所有時間開啟。</span><span class="sxs-lookup"><span data-stu-id="34289-136">This should be turned on most or all of the time.</span></span> <span data-ttu-id="34289-137">這項技術會移除使用者可能因查看和說話行為而有所移動的自然頭部和頸部起伏快速變換。</span><span class="sxs-lookup"><span data-stu-id="34289-137">This technique removes the natural head and neck jitters that users might have as well movement due to looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="34289-138">最接近的連結演算法</span><span class="sxs-lookup"><span data-stu-id="34289-138">Closest link algorithms</span></span>
<span data-ttu-id="34289-139">這些最適合用於具有疏鬆互動式內容的區域。</span><span class="sxs-lookup"><span data-stu-id="34289-139">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="34289-140">如果您有很高的機率可以判斷使用者嘗試與其互動的內容，您可以藉由假設某種程度的意圖來補充其目標功能。</span><span class="sxs-lookup"><span data-stu-id="34289-140">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="34289-141">Backdating 和 postdating 動作</span><span class="sxs-lookup"><span data-stu-id="34289-141">Backdating and postdating actions</span></span>
<span data-ttu-id="34289-142">這項機制對於要求速度的工作很實用。</span><span class="sxs-lookup"><span data-stu-id="34289-142">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="34289-143">當使用者在一系列的目標和啟用調動中快速移動時，假設有一些意圖，並允許錯過的步驟，讓使用者在執行早期測試) 之前或之後稍微或之後稍微或 50 (稍微。</span><span class="sxs-lookup"><span data-stu-id="34289-143">When a user is moving through a series of targeting and activation maneuvers at speed, it is useful to assume some intent, and allow missed steps to act upon targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="34289-144">平滑處理</span><span class="sxs-lookup"><span data-stu-id="34289-144">Smoothing</span></span>
<span data-ttu-id="34289-145">這項機制對於路徑移動很有説明，因為自然的標頭移動特性，減少了輕微的抖動和 wobble。</span><span class="sxs-lookup"><span data-stu-id="34289-145">This mechanism is useful for pathing movements, reducing the slight jitter and wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="34289-146">當平滑路徑移動時，會以移動的大小和距離，而不是經過一段時間來平滑。</span><span class="sxs-lookup"><span data-stu-id="34289-146">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="34289-147">磁性</span><span class="sxs-lookup"><span data-stu-id="34289-147">Magnetism</span></span>
<span data-ttu-id="34289-148">這項機制可視為最接近的連結演算法的最一般版本--將游標繪製到目標上，或單純地增加 hitboxes （無論是否可見），因為使用者可能會使用某些互動式版面配置知識，以更好的方式處理使用者意圖。</span><span class="sxs-lookup"><span data-stu-id="34289-148">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="34289-149">這對於小型目標特別有效果。</span><span class="sxs-lookup"><span data-stu-id="34289-149">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="34289-150">焦點黏著度</span><span class="sxs-lookup"><span data-stu-id="34289-150">Focus stickiness</span></span>
<span data-ttu-id="34289-151">當您決定要將焦點放在哪個附近的互動式專案時，焦點會與目前焦點的元素提供偏差。</span><span class="sxs-lookup"><span data-stu-id="34289-151">When determining which nearby interactive elements to give focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="34289-152">這有助於減少不穩定的焦點切換行為（當兩個專案之間的中間點有自然雜訊時）。</span><span class="sxs-lookup"><span data-stu-id="34289-152">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>


## <a name="see-also"></a><span data-ttu-id="34289-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34289-153">See also</span></span>
* [<span data-ttu-id="34289-154">眼動式互動</span><span class="sxs-lookup"><span data-stu-id="34289-154">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="34289-155">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="34289-155">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="34289-156">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="34289-156">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="34289-157">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="34289-157">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="34289-158">手 - 指向和行動</span><span class="sxs-lookup"><span data-stu-id="34289-158">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="34289-159">本能互動</span><span class="sxs-lookup"><span data-stu-id="34289-159">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="34289-160">語音輸入</span><span class="sxs-lookup"><span data-stu-id="34289-160">Voice input</span></span>](voice-input.md)



