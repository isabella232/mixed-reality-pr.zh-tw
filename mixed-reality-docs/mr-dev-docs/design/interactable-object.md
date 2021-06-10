---
title: 可互動的物件
description: 瞭解如何在您的混合現實應用程式中觸發事件、提供視覺提示，以及與物件互動。
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、提示、ui、ux、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、音訊
ms.openlocfilehash: 8a68006d68b985f8d26a3d1a11e4d52fcfb5acb5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600437"
---
# <a name="interactable-object"></a><span data-ttu-id="886c0-104">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="886c0-104">Interactable object</span></span>

![Interactible 物件](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="886c0-106">按鈕一直以來都是用來觸發2D 抽象世界中事件的比喻。</span><span class="sxs-lookup"><span data-stu-id="886c0-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="886c0-107">在三維混合現實世界中，我們不再需要局限于這種抽象概念。</span><span class="sxs-lookup"><span data-stu-id="886c0-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="886c0-108">任何專案都可以是觸發事件的 **互動物件** 。</span><span class="sxs-lookup"><span data-stu-id="886c0-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="886c0-109">互動物件可以是來自資料表咖啡杯的任何事物，以及 midair 中的氣球。</span><span class="sxs-lookup"><span data-stu-id="886c0-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="886c0-110">我們仍會在某些情況下（例如在對話方塊 UI 中）使用傳統按鈕。</span><span class="sxs-lookup"><span data-stu-id="886c0-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="886c0-111">按鈕的視覺標記法視內容而定。</span><span class="sxs-lookup"><span data-stu-id="886c0-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="886c0-112">互動物件的重要屬性</span><span class="sxs-lookup"><span data-stu-id="886c0-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="886c0-113">視覺提示</span><span class="sxs-lookup"><span data-stu-id="886c0-113">Visual cues</span></span>

<span data-ttu-id="886c0-114">視覺提示是從燈光感應式的提示，由眼睛所接收，並由視覺效果系統在視覺感知期間處理。</span><span class="sxs-lookup"><span data-stu-id="886c0-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="886c0-115">由於視覺系統在許多物種中是主要的，尤其是人們的視覺提示，是世界的認知方式的一大來源資訊。</span><span class="sxs-lookup"><span data-stu-id="886c0-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="886c0-116">因為全像是混合的真實世界環境混合，所以很難瞭解您可以與哪些物件互動。</span><span class="sxs-lookup"><span data-stu-id="886c0-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="886c0-117">針對您體驗中的任何互動物件，請務必為每個輸入狀態提供差異的視覺提示。</span><span class="sxs-lookup"><span data-stu-id="886c0-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="886c0-118">這可協助使用者瞭解您的體驗的哪個部分是互動，並使用一致的互動方法來確保使用者的信心。</span><span class="sxs-lookup"><span data-stu-id="886c0-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="886c0-119">遠的互動</span><span class="sxs-lookup"><span data-stu-id="886c0-119">Far interactions</span></span>

<span data-ttu-id="886c0-120">對於使用者可以與注視、手光線和移動控制器光線互動的任何物件，建議您對這三種輸入狀態使用不同的視覺提示：</span><span class="sxs-lookup"><span data-stu-id="886c0-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="886c0-121">![具有預設狀態的互動物件](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="886c0-122">**預設 (觀察) 狀態**</span><span class="sxs-lookup"><span data-stu-id="886c0-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="886c0-123">物件的預設閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="886c0-123">Default idle state of the object.</span></span>
    <span data-ttu-id="886c0-124">資料指標不在物件上。</span><span class="sxs-lookup"><span data-stu-id="886c0-124">The cursor isn't on the object.</span></span> <span data-ttu-id="886c0-125">未偵測到手。</span><span class="sxs-lookup"><span data-stu-id="886c0-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="886c0-126">![具有目標和停留狀態的互動物件](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="886c0-127">**目標 (將滑鼠停留) 狀態**</span><span class="sxs-lookup"><span data-stu-id="886c0-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="886c0-128">當物件以注視游標、手指鄰近或移動控制器的指標為目標時。</span><span class="sxs-lookup"><span data-stu-id="886c0-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="886c0-129">資料指標位於物件上。</span><span class="sxs-lookup"><span data-stu-id="886c0-129">The cursor is on the object.</span></span> <span data-ttu-id="886c0-130">偵測到手、準備就緒。</span><span class="sxs-lookup"><span data-stu-id="886c0-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="886c0-131">![具有已按下狀態的互動物件](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="886c0-132">**已按下的狀態**</span><span class="sxs-lookup"><span data-stu-id="886c0-132">**Pressed state**</span></span><br>
        <span data-ttu-id="886c0-133">當您按下滑鼠按鍵時，按一下滑鼠右鍵或移動控制器的選取按鈕。</span><span class="sxs-lookup"><span data-stu-id="886c0-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="886c0-134">資料指標位於物件上。</span><span class="sxs-lookup"><span data-stu-id="886c0-134">The cursor is on the object.</span></span> <span data-ttu-id="886c0-135">偵測到手，以空調的方式進行。</span><span class="sxs-lookup"><span data-stu-id="886c0-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="886c0-136">您可以使用醒目提示或調整之類的技術，提供使用者輸入狀態的視覺提示。</span><span class="sxs-lookup"><span data-stu-id="886c0-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="886c0-137">在混合的現實情況下，您可以在 [開始] 功能表和使用應用程式列按鈕的情況下，找到將不同輸入狀態視覺化的範例。</span><span class="sxs-lookup"><span data-stu-id="886c0-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="886c0-138">以下是這些狀態在「全像全像」 **按鈕** 上的樣子：</span><span class="sxs-lookup"><span data-stu-id="886c0-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="886c0-139">![預設狀態的全像全像按鈕](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="886c0-140">**預設 (觀察) 狀態**</span><span class="sxs-lookup"><span data-stu-id="886c0-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="886c0-141">![目標和暫留狀態的全像按鈕](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="886c0-142">**目標 (將滑鼠停留) 狀態**</span><span class="sxs-lookup"><span data-stu-id="886c0-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="886c0-143">![處於已按下狀態的全像按鈕](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="886c0-144">**已按下的狀態**</span><span class="sxs-lookup"><span data-stu-id="886c0-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="886c0-145">接近互動 (直接) </span><span class="sxs-lookup"><span data-stu-id="886c0-145">Near interactions (direct)</span></span> 

<span data-ttu-id="886c0-146">HoloLens 2 支援明確的手追蹤輸入，可讓您與物件互動。</span><span class="sxs-lookup"><span data-stu-id="886c0-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="886c0-147">如果沒有 haptic 的意見反應和完美的深度感知，就很難分辨出您手中的手離物件或您是否觸及。</span><span class="sxs-lookup"><span data-stu-id="886c0-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="886c0-148">請務必提供足夠的視覺提示來傳達物件的狀態，特別是以該物件為依據的實際狀態。</span><span class="sxs-lookup"><span data-stu-id="886c0-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="886c0-149">使用視覺效果意見反應來傳達下列狀態：</span><span class="sxs-lookup"><span data-stu-id="886c0-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="886c0-150">**預設 (觀察)**：物件的預設閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="886c0-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="886c0-151">**停留**：當手近了全像影像時，變更視覺效果以傳達該手的目標是全像全像。</span><span class="sxs-lookup"><span data-stu-id="886c0-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="886c0-152">**距離和互動點**：當手進行全像投影、設計意見反應以傳達預期的互動時間點，以及物件與手指之間的距離</span><span class="sxs-lookup"><span data-stu-id="886c0-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="886c0-153">**連絡人開始**：變更視覺效果 (淺色、色彩) ，以傳達觸控已發生的情況</span><span class="sxs-lookup"><span data-stu-id="886c0-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="886c0-154">**Grasped**：在 Grasped 物件時，變更視覺效果 (淺色、色彩) </span><span class="sxs-lookup"><span data-stu-id="886c0-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="886c0-155">**連絡人結束**：當觸控結束時，變更視覺效果 (淺色、色彩) </span><span class="sxs-lookup"><span data-stu-id="886c0-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="886c0-156">![將游標暫留 () ](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="886c0-157">**將游標暫留 ()**</span><span class="sxs-lookup"><span data-stu-id="886c0-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="886c0-158">根據手近距離的醒目提示。</span><span class="sxs-lookup"><span data-stu-id="886c0-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="886c0-159">![將滑鼠停留 (附近) ](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="886c0-160">**將滑鼠停留 (附近)**</span><span class="sxs-lookup"><span data-stu-id="886c0-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="886c0-161">根據右邊的距離醒目提示大小變更。</span><span class="sxs-lookup"><span data-stu-id="886c0-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="886c0-162">![觸控/按下](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="886c0-163">**觸控/按下**</span><span class="sxs-lookup"><span data-stu-id="886c0-163">**Touch / press**</span></span><br>
        <span data-ttu-id="886c0-164">視覺效果加上音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="886c0-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="886c0-165">![把握](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="886c0-166">**把握**</span><span class="sxs-lookup"><span data-stu-id="886c0-166">**Grasp**</span></span><br>
        <span data-ttu-id="886c0-167">視覺效果加上音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="886c0-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="886c0-168">[HoloLens 2 上的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)是如何視覺化不同輸入互動狀態的範例：</span><span class="sxs-lookup"><span data-stu-id="886c0-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="886c0-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="886c0-170">**預設值**</span><span class="sxs-lookup"><span data-stu-id="886c0-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="886c0-171">![暫留](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="886c0-172">**暫留**</span><span class="sxs-lookup"><span data-stu-id="886c0-172">**Hover**</span></span><br>
        <span data-ttu-id="886c0-173">顯示以鄰近性為基礎的光源效果。</span><span class="sxs-lookup"><span data-stu-id="886c0-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="886c0-174">![觸控](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="886c0-175">**觸控**</span><span class="sxs-lookup"><span data-stu-id="886c0-175">**Touch**</span></span><br>
        <span data-ttu-id="886c0-176">顯示 ripple 效果。</span><span class="sxs-lookup"><span data-stu-id="886c0-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="886c0-177">![按鍵](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="886c0-178">**按鍵**</span><span class="sxs-lookup"><span data-stu-id="886c0-178">**Press**</span></span><br>
        <span data-ttu-id="886c0-179">移動 front 盤子。</span><span class="sxs-lookup"><span data-stu-id="886c0-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="886c0-180">HoloLens 2 上的「環形」視覺提示</span><span class="sxs-lookup"><span data-stu-id="886c0-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="886c0-181">在 HoloLens 2 上有一個額外的視覺提示，可協助使用者深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="886c0-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="886c0-182">當 fingertip 接近物件時，靠近其 fingertip 的環形會顯示並縮小。</span><span class="sxs-lookup"><span data-stu-id="886c0-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="886c0-183">當觸達已按下的狀態時，環形最終會聚合成點。</span><span class="sxs-lookup"><span data-stu-id="886c0-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="886c0-184">此 visual affordance 可協助使用者瞭解它們與物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="886c0-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="886c0-185">*影片迴圈：根據鄰近範圍方塊的視覺效果意見反應範例*</span><span class="sxs-lookup"><span data-stu-id="886c0-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="886c0-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="886c0-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="886c0-187">![關於手近距離的視覺回饋](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="886c0-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="886c0-188">音訊提示</span><span class="sxs-lookup"><span data-stu-id="886c0-188">Audio cues</span></span>

<span data-ttu-id="886c0-189">針對直接互動，適當的音訊意見反應可大幅改善使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="886c0-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="886c0-190">使用音訊意見反應來傳達下列提示：</span><span class="sxs-lookup"><span data-stu-id="886c0-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="886c0-191">**連絡人開始**：觸控開始時播放音效</span><span class="sxs-lookup"><span data-stu-id="886c0-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="886c0-192">**連絡人結束**：觸控端播放音效</span><span class="sxs-lookup"><span data-stu-id="886c0-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="886c0-193">**抓取開始**：抓取開始時播放音效</span><span class="sxs-lookup"><span data-stu-id="886c0-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="886c0-194">**抓取結束**：抓取結束時播放音效</span><span class="sxs-lookup"><span data-stu-id="886c0-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="886c0-195">語音命令</span><span class="sxs-lookup"><span data-stu-id="886c0-195">Voice commanding</span></span><br>
        <span data-ttu-id="886c0-196">針對任何互動物件，請務必支援替代的互動選項。</span><span class="sxs-lookup"><span data-stu-id="886c0-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="886c0-197">根據預設，我們建議針對任何互動的物件支援 [語音命令](../out-of-scope/voice-design.md) 。</span><span class="sxs-lookup"><span data-stu-id="886c0-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="886c0-198">若要改善可搜尋性，您也可以在停留狀態期間提供工具提示。</span><span class="sxs-lookup"><span data-stu-id="886c0-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="886c0-199">*影像： voice 命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="886c0-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![語音命令](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a><span data-ttu-id="886c0-201">大小調整建議</span><span class="sxs-lookup"><span data-stu-id="886c0-201">Sizing recommendations</span></span>

<span data-ttu-id="886c0-202">為了確保所有的互動物件都能輕易地觸及，建議您確定互動符合其與使用者的距離，以符合最小的大小。</span><span class="sxs-lookup"><span data-stu-id="886c0-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="886c0-203">視覺角度通常是以視覺弧線的角度來測量。視覺角度取決於使用者的眼睛和物件之間的距離，並保持不變，而目標的實體大小可能會隨著使用者的距離變更而改變。</span><span class="sxs-lookup"><span data-stu-id="886c0-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="886c0-204">若要根據與使用者之間的距離來判斷物件的必要實體大小，請嘗試使用視覺角度計算機（如 [這一](https://elvers.us/perception/visualAngle/)）。</span><span class="sxs-lookup"><span data-stu-id="886c0-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="886c0-205">以下是互動內容的最小大小建議。</span><span class="sxs-lookup"><span data-stu-id="886c0-205">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="886c0-206">直接接觸互動的目標大小</span><span class="sxs-lookup"><span data-stu-id="886c0-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="886c0-207">距離</span><span class="sxs-lookup"><span data-stu-id="886c0-207">Distance</span></span> | <span data-ttu-id="886c0-208">視角</span><span class="sxs-lookup"><span data-stu-id="886c0-208">Viewing angle</span></span> | <span data-ttu-id="886c0-209">大小</span><span class="sxs-lookup"><span data-stu-id="886c0-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="886c0-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="886c0-210">45 cm</span></span>  | <span data-ttu-id="886c0-211">小於2°</span><span class="sxs-lookup"><span data-stu-id="886c0-211">no smaller than 2°</span></span> | <span data-ttu-id="886c0-212">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="886c0-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="886c0-213">![直接接觸互動的目標大小](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="886c0-214">*直接接觸互動的目標大小*</span><span class="sxs-lookup"><span data-stu-id="886c0-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="886c0-215">按鈕的目標大小</span><span class="sxs-lookup"><span data-stu-id="886c0-215">Target size for buttons</span></span>

<span data-ttu-id="886c0-216">建立直接互動的按鈕時，建議使用較大的大小（3.2 x 3.2 cm），以確保有足夠的空間可包含圖示且可能有一些文字。</span><span class="sxs-lookup"><span data-stu-id="886c0-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="886c0-217">距離</span><span class="sxs-lookup"><span data-stu-id="886c0-217">Distance</span></span> | <span data-ttu-id="886c0-218">最小大小</span><span class="sxs-lookup"><span data-stu-id="886c0-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="886c0-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="886c0-219">45 cm</span></span>  | <span data-ttu-id="886c0-220">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="886c0-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="886c0-221">![按鈕的目標大小](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="886c0-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="886c0-222">*按鈕的目標大小*</span><span class="sxs-lookup"><span data-stu-id="886c0-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="886c0-223">手動光線或注視互動的目標大小</span><span class="sxs-lookup"><span data-stu-id="886c0-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="886c0-224">距離</span><span class="sxs-lookup"><span data-stu-id="886c0-224">Distance</span></span> | <span data-ttu-id="886c0-225">視角</span><span class="sxs-lookup"><span data-stu-id="886c0-225">Viewing angle</span></span> | <span data-ttu-id="886c0-226">大小</span><span class="sxs-lookup"><span data-stu-id="886c0-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="886c0-227">2分鐘</span><span class="sxs-lookup"><span data-stu-id="886c0-227">2 m</span></span>  | <span data-ttu-id="886c0-228">不小於1°</span><span class="sxs-lookup"><span data-stu-id="886c0-228">no smaller than 1°</span></span> | <span data-ttu-id="886c0-229">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="886c0-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="886c0-230">![手動光線或注視互動的目標大小](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="886c0-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="886c0-231">*手動光線或注視互動的目標大小*</span><span class="sxs-lookup"><span data-stu-id="886c0-231">*Target size for hand ray or gaze interaction*</span></span>

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="886c0-232">MRTK 中的互動物件 (Unity 的混合現實工具組) </span><span class="sxs-lookup"><span data-stu-id="886c0-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="886c0-233">在 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 中，您可以使用腳本 [**互動**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 讓物件回應各種類型的輸入互動狀態。</span><span class="sxs-lookup"><span data-stu-id="886c0-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="886c0-234">它支援各種類型的主題，可讓您藉由控制物件屬性（例如色彩、大小、材質和著色器）來定義視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="886c0-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="886c0-235">互動</span><span class="sxs-lookup"><span data-stu-id="886c0-235">Interactable</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [<span data-ttu-id="886c0-236">按鈕</span><span class="sxs-lookup"><span data-stu-id="886c0-236">Button</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [<span data-ttu-id="886c0-237">手邊互動範例場景</span><span class="sxs-lookup"><span data-stu-id="886c0-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="886c0-238">MixedRealityToolkit 的標準著色器提供各種選項，例如可協助您建立視覺和音訊提示的 **相近光源** 。</span><span class="sxs-lookup"><span data-stu-id="886c0-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>

* [<span data-ttu-id="886c0-239">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="886c0-239">MRTK Standard Shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="886c0-240">另請參閱</span><span class="sxs-lookup"><span data-stu-id="886c0-240">See also</span></span>

* [<span data-ttu-id="886c0-241">游標</span><span class="sxs-lookup"><span data-stu-id="886c0-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="886c0-242">手部光線</span><span class="sxs-lookup"><span data-stu-id="886c0-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="886c0-243">Button</span><span class="sxs-lookup"><span data-stu-id="886c0-243">Button</span></span>](button.md)
* [<span data-ttu-id="886c0-244">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="886c0-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="886c0-245">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="886c0-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="886c0-246">操作</span><span class="sxs-lookup"><span data-stu-id="886c0-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="886c0-247">手部功能表</span><span class="sxs-lookup"><span data-stu-id="886c0-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="886c0-248">近端功能表</span><span class="sxs-lookup"><span data-stu-id="886c0-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="886c0-249">物件集合</span><span class="sxs-lookup"><span data-stu-id="886c0-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="886c0-250">語音命令</span><span class="sxs-lookup"><span data-stu-id="886c0-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="886c0-251">鍵盤</span><span class="sxs-lookup"><span data-stu-id="886c0-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="886c0-252">工具提示</span><span class="sxs-lookup"><span data-stu-id="886c0-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="886c0-253">平板</span><span class="sxs-lookup"><span data-stu-id="886c0-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="886c0-254">滑桿</span><span class="sxs-lookup"><span data-stu-id="886c0-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="886c0-255">著色器</span><span class="sxs-lookup"><span data-stu-id="886c0-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="886c0-256">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="886c0-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="886c0-257">顯示進度</span><span class="sxs-lookup"><span data-stu-id="886c0-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="886c0-258">表面磁性</span><span class="sxs-lookup"><span data-stu-id="886c0-258">Surface magnetism</span></span>](surface-magnetism.md)