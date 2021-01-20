---
title: 頭部注視並認可
description: 開始使用前端和認可輸入模型，包括目標大小調整、放置和穩定。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: 混合的現實、注視、注視目標、互動、設計、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、目標、焦點、平滑
ms.openlocfilehash: a69b855e2246327affeeb0f771f565b94ea65cb2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582284"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="e3c80-104">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="e3c80-104">Head-gaze and commit</span></span>

<span data-ttu-id="e3c80-105">「注視」_和「認可_」是「注視」[和「認可](gaze-and-commit.md)」輸入模型的特殊案例，其中牽涉到以使用者為目標的物件。</span><span class="sxs-lookup"><span data-stu-id="e3c80-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="e3c80-106">您可以使用次要輸入來處理目標，例如手勢的點擊或「選取」語音命令。</span><span class="sxs-lookup"><span data-stu-id="e3c80-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="e3c80-107">裝置支援</span><span class="sxs-lookup"><span data-stu-id="e3c80-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e3c80-108"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="e3c80-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="e3c80-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e3c80-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e3c80-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e3c80-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e3c80-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="e3c80-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e3c80-112">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="e3c80-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="e3c80-113">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="e3c80-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="e3c80-114">✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</span><span class="sxs-lookup"><span data-stu-id="e3c80-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="e3c80-115">➕ 替代選項</span><span class="sxs-lookup"><span data-stu-id="e3c80-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="e3c80-116">目標大小調整和回饋</span><span class="sxs-lookup"><span data-stu-id="e3c80-116">Target sizing and feedback</span></span>

<span data-ttu-id="e3c80-117">前端圖向量已重複顯示，可供適當的目標使用，但通常最適合用於主要目標--取得較大的目標。</span><span class="sxs-lookup"><span data-stu-id="e3c80-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="e3c80-118">在大部分的情況下，1度到1.5 度的最小目標大小可允許成功的使用者動作，但通常會有3度的目標，以提供更快的速度。</span><span class="sxs-lookup"><span data-stu-id="e3c80-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="e3c80-119">使用者的目標大小實際上是2D 區域（即使是3D 專案），無論是哪一個投射都應該是目標設為區域。</span><span class="sxs-lookup"><span data-stu-id="e3c80-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="e3c80-120">提供專案為「作用中」的一些重要提示， (使用者以它為目標) 會很有説明。</span><span class="sxs-lookup"><span data-stu-id="e3c80-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="e3c80-121">這可能包含像是可見的「暫止」效果、反白顯示或按下的處理，或清除資料指標與元素的對齊。</span><span class="sxs-lookup"><span data-stu-id="e3c80-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="e3c80-122">![距離 2 公尺的最佳目標大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3c80-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="e3c80-123">*雙計量距離的最佳目標大小*</span><span class="sxs-lookup"><span data-stu-id="e3c80-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="e3c80-124">![醒目提示注視目標物件的範例](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3c80-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="e3c80-125">*醒目提示注視目標物件的範例*</span><span class="sxs-lookup"><span data-stu-id="e3c80-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="e3c80-126">目標位置</span><span class="sxs-lookup"><span data-stu-id="e3c80-126">Target placement</span></span>

<span data-ttu-id="e3c80-127">使用者通常會在其 view 欄位中找不到太高或太低的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="e3c80-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="e3c80-128">他們大部分的注意力都是在其主要焦點周圍，大約是眼睛。</span><span class="sxs-lookup"><span data-stu-id="e3c80-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="e3c80-129">將大部分的目標放在眼部水平周圍的合理頻帶會有所幫助。</span><span class="sxs-lookup"><span data-stu-id="e3c80-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="e3c80-130">由於使用者傾向于隨時專注于相對較小的視覺區域 (的視覺範圍大約是10度) ，因此將 UI 元素群組在一起，就能在概念上將 UI 元素群組在一起，以便使用者在區域中移動其外觀時，可以使用專案與專案的醒目連結行為。</span><span class="sxs-lookup"><span data-stu-id="e3c80-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="e3c80-131">在設計 UI 時，請記住 HoloLens 與沉浸式頭戴裝置之間的視野可能有很大的變化。</span><span class="sxs-lookup"><span data-stu-id="e3c80-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="e3c80-132">![方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3c80-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="e3c80-133">*方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例*</span><span class="sxs-lookup"><span data-stu-id="e3c80-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="e3c80-134">改善定向行為</span><span class="sxs-lookup"><span data-stu-id="e3c80-134">Improving targeting behaviors</span></span>

<span data-ttu-id="e3c80-135">如果將目標設為目標的使用者意圖可以判斷或近似值，則接受近乎遺漏的互動嘗試就會很有説明，就像是正確的目標一樣。</span><span class="sxs-lookup"><span data-stu-id="e3c80-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="e3c80-136">以下是一些成功的方法，這些方法可以併入混合現實體驗中：</span><span class="sxs-lookup"><span data-stu-id="e3c80-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="e3c80-137">頭部注視穩定 (「重力穴」)</span><span class="sxs-lookup"><span data-stu-id="e3c80-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="e3c80-138">這應該會在大部分或所有時間開啟。</span><span class="sxs-lookup"><span data-stu-id="e3c80-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="e3c80-139">這項技術會移除使用者可能因說話和說話行為而有移動的自然頭部和頸部起伏快速變換。</span><span class="sxs-lookup"><span data-stu-id="e3c80-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="e3c80-140">最接近的連結演算法</span><span class="sxs-lookup"><span data-stu-id="e3c80-140">Closest link algorithms</span></span>

<span data-ttu-id="e3c80-141">這些演算法在具有稀疏互動式內容的區域中最適合使用。</span><span class="sxs-lookup"><span data-stu-id="e3c80-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="e3c80-142">如果您有很高的機率可以判斷使用者嘗試與其互動的內容，您可以藉由假設某種程度的意圖來補充其目標功能。</span><span class="sxs-lookup"><span data-stu-id="e3c80-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="e3c80-143">Backdating 和 postdating 動作</span><span class="sxs-lookup"><span data-stu-id="e3c80-143">Backdating and postdating actions</span></span>

<span data-ttu-id="e3c80-144">這項機制對於要求速度的工作很實用。</span><span class="sxs-lookup"><span data-stu-id="e3c80-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="e3c80-145">當使用者在一系列的目標和啟用調動中快速移動時，假設有一些意圖。</span><span class="sxs-lookup"><span data-stu-id="e3c80-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="e3c80-146">這也適用于允許錯過的步驟，讓使用者在執行早期測試) 之前或之後稍微或之後稍微或之後稍微稍微或 50 (稍微點一下的目標上，採取動作。</span><span class="sxs-lookup"><span data-stu-id="e3c80-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="e3c80-147">平滑處理</span><span class="sxs-lookup"><span data-stu-id="e3c80-147">Smoothing</span></span>

<span data-ttu-id="e3c80-148">這項機制適用于路徑移動，因為自然的 head 移動特性而減少輕微的抖動和 wobbles。</span><span class="sxs-lookup"><span data-stu-id="e3c80-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="e3c80-149">當平滑路徑移動時，會以移動的大小和距離，而不是經過一段時間來平滑。</span><span class="sxs-lookup"><span data-stu-id="e3c80-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="e3c80-150">磁性</span><span class="sxs-lookup"><span data-stu-id="e3c80-150">Magnetism</span></span>

<span data-ttu-id="e3c80-151">這項機制可視為最接近的連結演算法的最一般版本--將游標繪製到目標上，或單純地增加 hitboxes （無論是否可見），因為使用者可能會使用某些互動式版面配置知識，以更好的方式處理使用者意圖。</span><span class="sxs-lookup"><span data-stu-id="e3c80-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="e3c80-152">這對小型目標來說很強大。</span><span class="sxs-lookup"><span data-stu-id="e3c80-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="e3c80-153">焦點黏著度</span><span class="sxs-lookup"><span data-stu-id="e3c80-153">Focus stickiness</span></span>

<span data-ttu-id="e3c80-154">當您決定要提供哪些鄰近的互動式元素、將焦點放在焦點時，焦點會對目前焦點的元素提供偏差。</span><span class="sxs-lookup"><span data-stu-id="e3c80-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="e3c80-155">這有助於減少不穩定的焦點切換行為（當兩個專案之間的中間點有自然雜訊時）。</span><span class="sxs-lookup"><span data-stu-id="e3c80-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3c80-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3c80-156">See also</span></span>

* [<span data-ttu-id="e3c80-157">眼動式互動</span><span class="sxs-lookup"><span data-stu-id="e3c80-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="e3c80-158">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="e3c80-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e3c80-159">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="e3c80-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e3c80-160">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="e3c80-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="e3c80-161">手 - 指向和行動</span><span class="sxs-lookup"><span data-stu-id="e3c80-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="e3c80-162">本能互動</span><span class="sxs-lookup"><span data-stu-id="e3c80-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="e3c80-163">語音輸入</span><span class="sxs-lookup"><span data-stu-id="e3c80-163">Voice input</span></span>](voice-input.md)