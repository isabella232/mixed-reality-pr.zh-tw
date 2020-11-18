---
title: 可互動的物件
description: 按鈕一直以來都是用來觸發2D 抽象世界中事件的比喻。 在三維混合現實世界中，我們不再需要局限于這種抽象概念。
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、提示、ui、ux、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、音訊
ms.openlocfilehash: e298ce7fa46688a734c55a6674c03b89a4e7b5f3
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703224"
---
# <a name="interactable-object"></a><span data-ttu-id="80940-105">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="80940-105">Interactable object</span></span>

![Interactible 物件](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="80940-107">按鈕一直以來都是用來觸發2D 抽象世界中事件的比喻。</span><span class="sxs-lookup"><span data-stu-id="80940-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="80940-108">在三維混合現實世界中，我們不再需要局限于這種抽象概念。</span><span class="sxs-lookup"><span data-stu-id="80940-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="80940-109">任何專案都可以是觸發事件的 **互動物件** 。</span><span class="sxs-lookup"><span data-stu-id="80940-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="80940-110">互動物件可以表示為來自資料表咖啡杯的任何事物，以及浮動在空氣中的球形球。</span><span class="sxs-lookup"><span data-stu-id="80940-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="80940-111">我們仍會在某些情況下（例如在對話方塊 UI 中）使用傳統按鈕。</span><span class="sxs-lookup"><span data-stu-id="80940-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="80940-112">按鈕的視覺標記法視內容而定。</span><span class="sxs-lookup"><span data-stu-id="80940-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="80940-113">互動物件的重要屬性</span><span class="sxs-lookup"><span data-stu-id="80940-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="80940-114">視覺提示</span><span class="sxs-lookup"><span data-stu-id="80940-114">Visual cues</span></span>

<span data-ttu-id="80940-115">視覺提示是視覺上視覺認知期間，以光線形式所收到的感應式提示，並由視覺效果系統處理。</span><span class="sxs-lookup"><span data-stu-id="80940-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="80940-116">由於視覺系統在許多物種中是主要的，尤其是人們的視覺提示，是世界的認知方式的一大來源資訊。</span><span class="sxs-lookup"><span data-stu-id="80940-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="80940-117">因為全像是混合的真實世界環境混合，所以很難瞭解您可以與哪些物件互動。</span><span class="sxs-lookup"><span data-stu-id="80940-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="80940-118">針對您體驗中的任何互動物件，請務必為每個輸入狀態提供差異的視覺提示。</span><span class="sxs-lookup"><span data-stu-id="80940-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="80940-119">這可協助使用者瞭解您的體驗的哪個部分是互動，並使用一致的互動方法來確保使用者的信心。</span><span class="sxs-lookup"><span data-stu-id="80940-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="80940-120">遠的互動</span><span class="sxs-lookup"><span data-stu-id="80940-120">Far interactions</span></span>

<span data-ttu-id="80940-121">對於使用者可以與注視、手光線和移動控制器光線互動的任何物件，建議您針對這三種輸入狀態使用不同的視覺提示：</span><span class="sxs-lookup"><span data-stu-id="80940-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="80940-122">![interactibleobject-狀態-預設值](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="80940-123">**預設 (觀察) 狀態**</span><span class="sxs-lookup"><span data-stu-id="80940-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="80940-124">物件的預設閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="80940-124">Default idle state of the object.</span></span>
    <span data-ttu-id="80940-125">資料指標不在物件上。</span><span class="sxs-lookup"><span data-stu-id="80940-125">The cursor is not on the object.</span></span> <span data-ttu-id="80940-126">未偵測到手。</span><span class="sxs-lookup"><span data-stu-id="80940-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80940-127">![interactibleobject-狀態-目標](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="80940-128">**目標 (將滑鼠停留) 狀態**</span><span class="sxs-lookup"><span data-stu-id="80940-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="80940-129">當物件以注視游標、手指鄰近或移動控制器的指標為目標時。</span><span class="sxs-lookup"><span data-stu-id="80940-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="80940-130">資料指標位於物件上。</span><span class="sxs-lookup"><span data-stu-id="80940-130">The cursor is on the object.</span></span> <span data-ttu-id="80940-131">偵測到手、準備就緒。</span><span class="sxs-lookup"><span data-stu-id="80940-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80940-132">![interactibleobject-狀態-已按下](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="80940-133">**已按下的狀態**</span><span class="sxs-lookup"><span data-stu-id="80940-133">**Pressed state**</span></span><br>
        <span data-ttu-id="80940-134">當您按下滑鼠按鍵時，按一下滑鼠右鍵或移動控制器的選取按鈕。</span><span class="sxs-lookup"><span data-stu-id="80940-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="80940-135">資料指標位於物件上。</span><span class="sxs-lookup"><span data-stu-id="80940-135">The cursor is on the object.</span></span> <span data-ttu-id="80940-136">偵測到手，以空調的方式進行。</span><span class="sxs-lookup"><span data-stu-id="80940-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="80940-137">您可以使用醒目提示或調整之類的技術，提供使用者輸入狀態的視覺提示。</span><span class="sxs-lookup"><span data-stu-id="80940-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="80940-138">在混合的現實情況下，您可以找到在 [開始] 功能表和使用應用程式列按鈕將不同輸入狀態視覺化的範例。</span><span class="sxs-lookup"><span data-stu-id="80940-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="80940-139">以下是這些狀態在「全像全像」 **按鈕** 上的外觀：</span><span class="sxs-lookup"><span data-stu-id="80940-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="80940-140">![interactibleobject-狀態-預設值](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="80940-141">**預設 (觀察) 狀態**</span><span class="sxs-lookup"><span data-stu-id="80940-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80940-142">![interactibleobject-狀態-目標](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="80940-143">**目標 (將滑鼠停留) 狀態**</span><span class="sxs-lookup"><span data-stu-id="80940-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="80940-144">![interactibleobject-狀態-已按下](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="80940-145">**已按下的狀態**</span><span class="sxs-lookup"><span data-stu-id="80940-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="80940-146">接近互動 (直接) </span><span class="sxs-lookup"><span data-stu-id="80940-146">Near interactions (direct)</span></span> 

<span data-ttu-id="80940-147">HoloLens 2 支援可讓您與物件互動的明確追蹤輸入。</span><span class="sxs-lookup"><span data-stu-id="80940-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="80940-148">如果沒有 haptic 的意見反應和深度的深度認知，有時可能很難分辨出您手中的手遠距離物件或您是否觸及。</span><span class="sxs-lookup"><span data-stu-id="80940-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="80940-149">請務必提供足夠的視覺提示，以傳達物件的狀態，以及特別與該物件相關的實際狀態。</span><span class="sxs-lookup"><span data-stu-id="80940-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="80940-150">使用視覺效果的意見反應來傳達下列內容：</span><span class="sxs-lookup"><span data-stu-id="80940-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="80940-151">**預設 (觀察)**：物件的預設閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="80940-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="80940-152">**停留**：當手近了全像影像時，變更視覺效果以傳達該手的目標是全像全像。</span><span class="sxs-lookup"><span data-stu-id="80940-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="80940-153">**距離和互動點**：當手進行全像投影時，設計意見反應以傳達預期的互動點，以及從物件到手指的距離</span><span class="sxs-lookup"><span data-stu-id="80940-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="80940-154">**連絡人開始**：變更視覺效果 (淺色、色彩) ，以傳達觸控已發生的情況</span><span class="sxs-lookup"><span data-stu-id="80940-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="80940-155">**Grasped**：在 Grasped 物件時，變更視覺效果 (淺色、色彩) </span><span class="sxs-lookup"><span data-stu-id="80940-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="80940-156">**連絡人結束**：當觸控結束時，變更視覺效果 (淺色、色彩) </span><span class="sxs-lookup"><span data-stu-id="80940-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="80940-157">![將游標暫留 () ](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="80940-158">**將游標暫留 ()**</span><span class="sxs-lookup"><span data-stu-id="80940-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="80940-159">根據手近距離的醒目提示。</span><span class="sxs-lookup"><span data-stu-id="80940-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="80940-160">![將滑鼠停留 (附近) ](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="80940-161">**將滑鼠停留 (附近)**</span><span class="sxs-lookup"><span data-stu-id="80940-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="80940-162">根據右邊的距離醒目提示大小變更。</span><span class="sxs-lookup"><span data-stu-id="80940-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="80940-163">![觸控/按下](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="80940-164">**觸控/按下**</span><span class="sxs-lookup"><span data-stu-id="80940-164">**Touch / press**</span></span><br>
        <span data-ttu-id="80940-165">視覺效果加上音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="80940-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="80940-166">![把握](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="80940-167">**把握**</span><span class="sxs-lookup"><span data-stu-id="80940-167">**Grasp**</span></span><br>
        <span data-ttu-id="80940-168">視覺效果加上音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="80940-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="80940-169">[HoloLens 2 上的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)是如何視覺化不同輸入互動狀態的範例：</span><span class="sxs-lookup"><span data-stu-id="80940-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="80940-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="80940-171">**預設值**</span><span class="sxs-lookup"><span data-stu-id="80940-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="80940-172">![暫留](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="80940-173">**暫留**</span><span class="sxs-lookup"><span data-stu-id="80940-173">**Hover**</span></span><br>
        <span data-ttu-id="80940-174">顯示以鄰近性為基礎的光源效果。</span><span class="sxs-lookup"><span data-stu-id="80940-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="80940-175">![觸控](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="80940-176">**觸控**</span><span class="sxs-lookup"><span data-stu-id="80940-176">**Touch**</span></span><br>
        <span data-ttu-id="80940-177">顯示 ripple 效果。</span><span class="sxs-lookup"><span data-stu-id="80940-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="80940-178">![按鍵](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="80940-179">**按鍵**</span><span class="sxs-lookup"><span data-stu-id="80940-179">**Press**</span></span><br>
        <span data-ttu-id="80940-180">移動 front 盤子。</span><span class="sxs-lookup"><span data-stu-id="80940-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="80940-181">HoloLens 2 上的「環形」視覺提示</span><span class="sxs-lookup"><span data-stu-id="80940-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="80940-182">在 HoloLens 2 上有一個額外的視覺提示，可協助使用者瞭解深度。</span><span class="sxs-lookup"><span data-stu-id="80940-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="80940-183">當 fingertip 接近物件時，靠近其 fingertip 的環形會顯示並縮小。</span><span class="sxs-lookup"><span data-stu-id="80940-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="80940-184">當觸達已按下的狀態時，環形最終會聚合成點。</span><span class="sxs-lookup"><span data-stu-id="80940-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="80940-185">此 visual affordance 可協助使用者瞭解它們與物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="80940-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="80940-186">*影片迴圈：根據鄰近範圍方塊的視覺效果意見反應範例*</span><span class="sxs-lookup"><span data-stu-id="80940-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="80940-187">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="80940-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="80940-188">![關於手近距離的視覺回饋](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="80940-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="80940-189">音訊提示</span><span class="sxs-lookup"><span data-stu-id="80940-189">Audio cues</span></span>

<span data-ttu-id="80940-190">針對直接互動，適當的音訊意見反應可大幅改善使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="80940-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="80940-191">使用音訊意見反應來傳達下列內容：</span><span class="sxs-lookup"><span data-stu-id="80940-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="80940-192">**連絡人開始**：觸控開始時播放音效</span><span class="sxs-lookup"><span data-stu-id="80940-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="80940-193">**連絡人結束**：觸控端播放音效</span><span class="sxs-lookup"><span data-stu-id="80940-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="80940-194">**抓取開始**：抓取開始時播放音效</span><span class="sxs-lookup"><span data-stu-id="80940-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="80940-195">**抓取結束**：抓取結束時播放音效</span><span class="sxs-lookup"><span data-stu-id="80940-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="80940-196">語音命令</span><span class="sxs-lookup"><span data-stu-id="80940-196">Voice commanding</span></span><br>
        <span data-ttu-id="80940-197">針對任何互動物件，請務必支援替代的互動選項。</span><span class="sxs-lookup"><span data-stu-id="80940-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="80940-198">根據預設，我們建議針對任何互動的物件支援 [語音命令](../out-of-scope/voice-design.md) 。</span><span class="sxs-lookup"><span data-stu-id="80940-198">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="80940-199">若要改善可搜尋性，您也可以在停留狀態期間提供工具提示。</span><span class="sxs-lookup"><span data-stu-id="80940-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="80940-200">*影像： voice 命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="80940-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![語音命令](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="80940-202">大小調整建議</span><span class="sxs-lookup"><span data-stu-id="80940-202">Sizing recommendations</span></span> 

<span data-ttu-id="80940-203">為了確保使用者可以輕鬆地觸及所有互動物件，建議您確定互動符合大小下限 (視覺角度通常是以視覺弧形的角度來測量，而視覺角度通常是根據其從使用者的距離來) 。</span><span class="sxs-lookup"><span data-stu-id="80940-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="80940-204">視覺角度取決於使用者的眼睛和物件之間的距離，並保持不變，而目標的實體大小可能會隨著使用者的距離變更而改變。</span><span class="sxs-lookup"><span data-stu-id="80940-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="80940-205">若要根據與使用者之間的距離來判斷物件的必要實體大小，請嘗試使用視覺角度計算機（如 [這一](https://elvers.us/perception/visualAngle/)）。</span><span class="sxs-lookup"><span data-stu-id="80940-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="80940-206">以下是互動內容的最小大小建議。</span><span class="sxs-lookup"><span data-stu-id="80940-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="80940-207">直接接觸互動的目標大小</span><span class="sxs-lookup"><span data-stu-id="80940-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="80940-208">距離</span><span class="sxs-lookup"><span data-stu-id="80940-208">Distance</span></span> | <span data-ttu-id="80940-209">視角</span><span class="sxs-lookup"><span data-stu-id="80940-209">Viewing angle</span></span> | <span data-ttu-id="80940-210">大小</span><span class="sxs-lookup"><span data-stu-id="80940-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="80940-211">45cm</span><span class="sxs-lookup"><span data-stu-id="80940-211">45cm</span></span>  | <span data-ttu-id="80940-212">小於2°</span><span class="sxs-lookup"><span data-stu-id="80940-212">no smaller than 2°</span></span> | <span data-ttu-id="80940-213">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="80940-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="80940-214">![直接接觸互動的目標大小](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="80940-215">*直接接觸互動的目標大小*</span><span class="sxs-lookup"><span data-stu-id="80940-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="80940-216">按鈕的目標大小</span><span class="sxs-lookup"><span data-stu-id="80940-216">Target size for buttons</span></span>

<span data-ttu-id="80940-217">建立直接互動的按鈕時，建議使用較大的大小（3.2 x 3.2 cm），以確保有足夠的空間可包含圖示且可能有一些文字。</span><span class="sxs-lookup"><span data-stu-id="80940-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="80940-218">距離</span><span class="sxs-lookup"><span data-stu-id="80940-218">Distance</span></span> | <span data-ttu-id="80940-219">最小大小</span><span class="sxs-lookup"><span data-stu-id="80940-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="80940-220">45cm</span><span class="sxs-lookup"><span data-stu-id="80940-220">45cm</span></span>  | <span data-ttu-id="80940-221">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="80940-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="80940-222">![按鈕的目標大小](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="80940-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="80940-223">*按鈕的目標大小*</span><span class="sxs-lookup"><span data-stu-id="80940-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="80940-224">手動光線或注視互動的目標大小</span><span class="sxs-lookup"><span data-stu-id="80940-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="80940-225">距離</span><span class="sxs-lookup"><span data-stu-id="80940-225">Distance</span></span> | <span data-ttu-id="80940-226">視角</span><span class="sxs-lookup"><span data-stu-id="80940-226">Viewing angle</span></span> | <span data-ttu-id="80940-227">大小</span><span class="sxs-lookup"><span data-stu-id="80940-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="80940-228">2m</span><span class="sxs-lookup"><span data-stu-id="80940-228">2m</span></span>  | <span data-ttu-id="80940-229">不小於1°</span><span class="sxs-lookup"><span data-stu-id="80940-229">no smaller than 1°</span></span> | <span data-ttu-id="80940-230">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="80940-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="80940-231">![手動光線或注視互動的目標大小](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="80940-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="80940-232">*手動光線或注視互動的目標大小*</span><span class="sxs-lookup"><span data-stu-id="80940-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="80940-233">MRTK 中的互動物件 (Unity 的混合現實工具組) </span><span class="sxs-lookup"><span data-stu-id="80940-233">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="80940-234">在 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 中，您可以使用腳本 [**互動**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 讓物件回應各種類型的輸入互動狀態。</span><span class="sxs-lookup"><span data-stu-id="80940-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="80940-235">它支援各種類型的主題，可讓您藉由控制物件屬性（例如色彩、大小、材質和著色器）來定義視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="80940-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="80940-236">互動</span><span class="sxs-lookup"><span data-stu-id="80940-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="80940-237">按鈕</span><span class="sxs-lookup"><span data-stu-id="80940-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="80940-238">手邊互動範例場景</span><span class="sxs-lookup"><span data-stu-id="80940-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="80940-239">MixedRealityToolkit 的標準著色器提供各種選項，例如可協助您建立視覺和音訊提示的 **相近光源** 。</span><span class="sxs-lookup"><span data-stu-id="80940-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="80940-240">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="80940-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="80940-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80940-241">See also</span></span>

* [<span data-ttu-id="80940-242">游標</span><span class="sxs-lookup"><span data-stu-id="80940-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="80940-243">手部光線</span><span class="sxs-lookup"><span data-stu-id="80940-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="80940-244">Button</span><span class="sxs-lookup"><span data-stu-id="80940-244">Button</span></span>](button.md)
* [<span data-ttu-id="80940-245">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="80940-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="80940-246">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="80940-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="80940-247">操作</span><span class="sxs-lookup"><span data-stu-id="80940-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="80940-248">手部功能表</span><span class="sxs-lookup"><span data-stu-id="80940-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="80940-249">近端功能表</span><span class="sxs-lookup"><span data-stu-id="80940-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="80940-250">物件集合</span><span class="sxs-lookup"><span data-stu-id="80940-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="80940-251">語音命令</span><span class="sxs-lookup"><span data-stu-id="80940-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="80940-252">鍵盤</span><span class="sxs-lookup"><span data-stu-id="80940-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="80940-253">工具提示</span><span class="sxs-lookup"><span data-stu-id="80940-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="80940-254">平板</span><span class="sxs-lookup"><span data-stu-id="80940-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="80940-255">滑桿</span><span class="sxs-lookup"><span data-stu-id="80940-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="80940-256">著色器</span><span class="sxs-lookup"><span data-stu-id="80940-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="80940-257">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="80940-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="80940-258">顯示進度</span><span class="sxs-lookup"><span data-stu-id="80940-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="80940-259">表面磁性</span><span class="sxs-lookup"><span data-stu-id="80940-259">Surface magnetism</span></span>](surface-magnetism.md)
