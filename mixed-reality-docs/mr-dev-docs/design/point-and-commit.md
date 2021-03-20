---
title: 手部指向和行動
description: 了解混合實境應用程式中手勢支援的指向和行動輸入模型基本概念。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 互動, 設計, HoloLens, 手部, 遠方, 指向和行動, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, HoloLens, 手部射線, 物件操作, MRTK, 混合實境工具組, DoF
ms.openlocfilehash: 8196b67f103bae346ba4da065ee6045ff231b004
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "101759864"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="399e7-104">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="399e7-104">Point and commit with hands</span></span>

![游標](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="399e7-106">手部指向和行動是輸入模型，可讓使用者鎖定目標、選取和操控可及範圍之外的 2D 與 3D 內容。</span><span class="sxs-lookup"><span data-stu-id="399e7-106">Point and commit with hands is an input model that lets users target, select, and manipulate out of reach 2D and 3D content.</span></span> <span data-ttu-id="399e7-107">「遠方 (far)」互動技術是混合實境特有的技術，因為人類不會那樣與真實世界自然互動。</span><span class="sxs-lookup"><span data-stu-id="399e7-107">This "far" interaction technique is unique to mixed reality because humans don't naturally interact with the real world that way.</span></span> <span data-ttu-id="399e7-108">例如，在超級英雄電影「X 戰警」中，[萬磁王](https://en.wikipedia.org/wiki/Magneto_(comics))可以使用他的手操控遠方物件。</span><span class="sxs-lookup"><span data-stu-id="399e7-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) can manipulate far objects in the distance with his hands.</span></span> <span data-ttu-id="399e7-109">這不是人類在現實中可做到的事。</span><span class="sxs-lookup"><span data-stu-id="399e7-109">This isn't something humans can do in reality.</span></span> <span data-ttu-id="399e7-110">在 HoloLens (AR) 和混合實境 (MR) 中，我們會為使用者提供這項神奇功能，以中斷真實世界的實體限制。</span><span class="sxs-lookup"><span data-stu-id="399e7-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power to break the physical constraint of the real world.</span></span> <span data-ttu-id="399e7-111">這不僅是很有趣的全像攝影體驗，還能讓使用者互動更有效且效率更高。</span><span class="sxs-lookup"><span data-stu-id="399e7-111">Not only is it a fun holographic experience, but it also makes user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="399e7-112">裝置支援</span><span class="sxs-lookup"><span data-stu-id="399e7-112">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="399e7-113"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="399e7-113"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="399e7-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="399e7-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="399e7-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="399e7-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="399e7-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="399e7-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="399e7-117">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="399e7-117">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="399e7-118">❌ 未支援</span><span class="sxs-lookup"><span data-stu-id="399e7-118">❌ Not supported</span></span></td>
     <td><span data-ttu-id="399e7-119">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="399e7-119">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="399e7-120">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="399e7-120">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="399e7-121">「指向和行動」是使用新式關節手部追蹤系統的新功能之一。</span><span class="sxs-lookup"><span data-stu-id="399e7-121">_"Point and commit with hands"_ is one of the new features that use the new articulated hand-tracking system.</span></span> <span data-ttu-id="399e7-122">使用運動控制器的沈浸式耳機也是以此輸入模型作為主要輸入模型。</span><span class="sxs-lookup"><span data-stu-id="399e7-122">This input model is also the primary input model on immersive headsets by using motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="399e7-123">手部光線 (Hand Ray)</span><span class="sxs-lookup"><span data-stu-id="399e7-123">Hand rays</span></span>

<span data-ttu-id="399e7-124">在 HoloLens 2 上，我們已建立可從使用者手掌中央發射的手部光線。</span><span class="sxs-lookup"><span data-stu-id="399e7-124">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="399e7-125">此光線將視為手的延伸。</span><span class="sxs-lookup"><span data-stu-id="399e7-125">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="399e7-126">光線末端會附加環狀游標，以指出光線與目標物件交集的位置。</span><span class="sxs-lookup"><span data-stu-id="399e7-126">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="399e7-127">然後，游標所在的物件就能從手部接收手勢命令。</span><span class="sxs-lookup"><span data-stu-id="399e7-127">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="399e7-128">此基本手勢命令會藉由使用拇指與食指進行空中點選動作來觸發。</span><span class="sxs-lookup"><span data-stu-id="399e7-128">This basic gestural command is triggered by using the thumb and index finger to do the air-tap action.</span></span> <span data-ttu-id="399e7-129">藉由使用手部光線進行指向及空中點選來行動，使用者就可以啟用按鈕或超連結。</span><span class="sxs-lookup"><span data-stu-id="399e7-129">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="399e7-130">藉由更多的複合手勢，使用者可以從遠處瀏覽網頁內容和操作 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="399e7-130">With more composite gestures, users can navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="399e7-131">手動光線的視覺化設計也會反應這些指向和行動狀態，請見下列圖示和說明：</span><span class="sxs-lookup"><span data-stu-id="399e7-131">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="399e7-132">![手部光線指向](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-132">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="399e7-133">**指向狀態**</span><span class="sxs-lookup"><span data-stu-id="399e7-133">**Pointing state**</span></span><br>
        <span data-ttu-id="399e7-134">在「指向」  狀態時，光線呈虛線，而指標呈環狀。</span><span class="sxs-lookup"><span data-stu-id="399e7-134">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="399e7-135">![手部光線認可](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-135">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="399e7-136">**認可狀態**</span><span class="sxs-lookup"><span data-stu-id="399e7-136">**Commit state**</span></span><br>
        <span data-ttu-id="399e7-137">在「行動」  狀態時，光線變成一條實線，而游標會壓縮成一個點。</span><span class="sxs-lookup"><span data-stu-id="399e7-137">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a><span data-ttu-id="399e7-138">遠近轉換</span><span class="sxs-lookup"><span data-stu-id="399e7-138">Transition between near and far</span></span>

<span data-ttu-id="399e7-139">我們不會使用「以食指指向」之類的特定手勢來指引光線，而是將光線設計成從使用者的手掌中心射出來。</span><span class="sxs-lookup"><span data-stu-id="399e7-139">Instead of using specific gestures like "pointing with index finger" to direct the ray, we designed the ray to comout out from the center of the users' palm.</span></span> <span data-ttu-id="399e7-140">如此一來，我們空出並保留了五隻手指頭來進行更具操控性的手勢，例如捏取和抓取。</span><span class="sxs-lookup"><span data-stu-id="399e7-140">This way, we've released and reserved the Five Fingers for more manipulative gestures like pinch and grab.</span></span> <span data-ttu-id="399e7-141">透過這項設計，我們只需建立一個心智模型 - 針對遠近互動使用完全相同的一組手勢。</span><span class="sxs-lookup"><span data-stu-id="399e7-141">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="399e7-142">您可以使用相同的抓取手勢來操作不同距離的物件。</span><span class="sxs-lookup"><span data-stu-id="399e7-142">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="399e7-143">光線的引動過程會根據鄰近程度自動執行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="399e7-143">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="399e7-144">![近距操作](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-144">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="399e7-145">**近距操作**</span><span class="sxs-lookup"><span data-stu-id="399e7-145">**Near manipulation**</span></span><br>
        <span data-ttu-id="399e7-146">當物件位在手臂可及的範圍內 (大約 50 公分) 時，光線就會自動關閉，並建議您進行近距離互動。</span><span class="sxs-lookup"><span data-stu-id="399e7-146">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="399e7-147">![遠距操作](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-147">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="399e7-148">**遠距操作**</span><span class="sxs-lookup"><span data-stu-id="399e7-148">**Far manipulation**</span></span><br>
        <span data-ttu-id="399e7-149">物件距離超過 50 公分時，光線就會開啟。</span><span class="sxs-lookup"><span data-stu-id="399e7-149">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="399e7-150">此轉換會很順利且流暢。</span><span class="sxs-lookup"><span data-stu-id="399e7-150">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="399e7-151">2D 平板互動</span><span class="sxs-lookup"><span data-stu-id="399e7-151">2D slate interaction</span></span>

<span data-ttu-id="399e7-152">2D 平板是裝載 2D 應用程式內容 (例如網頁瀏覽器) 的全像攝影容器。</span><span class="sxs-lookup"><span data-stu-id="399e7-152">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="399e7-153">以 2D 平板進行遠端互動的設計概念是，使用手部光線來鎖定目標和使用空中點選來選取項目。</span><span class="sxs-lookup"><span data-stu-id="399e7-153">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="399e7-154">以手部光線鎖定目標後，使用者可以透過空中點選來觸發超連結或按鈕。</span><span class="sxs-lookup"><span data-stu-id="399e7-154">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="399e7-155">他們可使用一隻手來進行「空中點選和拖曳」，進而上下捲動平板內容。</span><span class="sxs-lookup"><span data-stu-id="399e7-155">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="399e7-156">使用兩隻手進行空中點選和拖曳的相對動作則可縮放平板內容。</span><span class="sxs-lookup"><span data-stu-id="399e7-156">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="399e7-157">將手部光線的目標鎖定在角落和邊緣會顯示最接近的操作能供性 (affordance)。</span><span class="sxs-lookup"><span data-stu-id="399e7-157">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="399e7-158">藉由「抓取並拖曳」操作能供性，使用者可以透過角落能供性進行統一的尺寸調整，以及可透過邊緣能供性來重排平板。</span><span class="sxs-lookup"><span data-stu-id="399e7-158">By "grab and drag" manipulation affordances, users can do uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="399e7-159">藉由抓取並拖曳 2D 平板上方的 holobar，使用者可以移動整個平板。</span><span class="sxs-lookup"><span data-stu-id="399e7-159">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="399e7-160">![2D 平板互動按一下](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-160">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="399e7-161">**按一下**</span><span class="sxs-lookup"><span data-stu-id="399e7-161">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="399e7-162">![2D 平板互動捲動](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-162">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="399e7-163">**捲動**</span><span class="sxs-lookup"><span data-stu-id="399e7-163">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="399e7-164">![2D 平板互動縮放](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-164">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="399e7-165">**縮放**</span><span class="sxs-lookup"><span data-stu-id="399e7-165">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="399e7-166">**操作 2D 平板**</span><span class="sxs-lookup"><span data-stu-id="399e7-166">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="399e7-167">使用者將手部光線指向角落或邊緣時，可顯示最接近的操作能供性。</span><span class="sxs-lookup"><span data-stu-id="399e7-167">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="399e7-168">藉由在能供性上套用操作手勢，使用者可以透過角落能供性進行統一的尺寸調整，以及可透過邊緣能供性來重排平板。</span><span class="sxs-lookup"><span data-stu-id="399e7-168">By applying a manipulation gesture on the affordance, users can do uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="399e7-169">藉由在 2D 平板頂端的 holobar 上套用操作手勢，使用者可以移動整個平板。</span><span class="sxs-lookup"><span data-stu-id="399e7-169">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="399e7-170">3D 物件操作</span><span class="sxs-lookup"><span data-stu-id="399e7-170">3D object manipulation</span></span>

<span data-ttu-id="399e7-171">在直接操作中，有兩種方法可讓使用者操作 3D 物件：能供性操作與非能供性操作。</span><span class="sxs-lookup"><span data-stu-id="399e7-171">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="399e7-172">在指向和行動模型中，使用者可以透過手部射線來完成完全相同的工作。</span><span class="sxs-lookup"><span data-stu-id="399e7-172">In the point and commit model, users can achieve exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="399e7-173">不需要額外的學習。</span><span class="sxs-lookup"><span data-stu-id="399e7-173">No extra learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="399e7-174">能供性操作</span><span class="sxs-lookup"><span data-stu-id="399e7-174">Affordance-based manipulation</span></span>

<span data-ttu-id="399e7-175">使用者使用手部光線來指向並顯示週框方塊和操作能供性。</span><span class="sxs-lookup"><span data-stu-id="399e7-175">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="399e7-176">使用者可以將操作手勢套用到週框方塊來移動整個物件，套用到邊緣能供性可旋轉物件，套用到角落能供性可統一調整物件大小。</span><span class="sxs-lookup"><span data-stu-id="399e7-176">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="399e7-177">![3D 物件操作遠距移動](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-177">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="399e7-178">**移動**</span><span class="sxs-lookup"><span data-stu-id="399e7-178">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="399e7-179">![3D 物件操作遠距旋轉](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-179">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="399e7-180">**旋轉**</span><span class="sxs-lookup"><span data-stu-id="399e7-180">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="399e7-181">![3D 物件操作遠距縮放](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-181">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="399e7-182">**縮放**</span><span class="sxs-lookup"><span data-stu-id="399e7-182">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="399e7-183">非能供性操作</span><span class="sxs-lookup"><span data-stu-id="399e7-183">Non-affordance-based manipulation</span></span>

<span data-ttu-id="399e7-184">使用者透過手部光線指向來顯示週框方塊，然後直接在其上方套用操作手勢。</span><span class="sxs-lookup"><span data-stu-id="399e7-184">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="399e7-185">若使用一隻手，物件的轉譯和旋轉會與手的動作和方向相關聯。</span><span class="sxs-lookup"><span data-stu-id="399e7-185">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="399e7-186">若使用兩隻手，使用者可以根據兩隻手的相對動作來轉譯、縮放及旋轉週框方塊。</span><span class="sxs-lookup"><span data-stu-id="399e7-186">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="399e7-187">本能手勢</span><span class="sxs-lookup"><span data-stu-id="399e7-187">Instinctual gestures</span></span>

<span data-ttu-id="399e7-188">指向和行動的本能手勢基本上類似於[手部直接操作](direct-manipulation.md)。</span><span class="sxs-lookup"><span data-stu-id="399e7-188">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="399e7-189">使用者在 3D 物件上進行的手勢，皆由 UI 能供性的設計來引導。</span><span class="sxs-lookup"><span data-stu-id="399e7-189">The gestures users do on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="399e7-190">例如，在使用者想使用五隻手指頭來抓取較大的物件時，小型控點可能會促使使用者運用其拇指與食指來捏取物件。</span><span class="sxs-lookup"><span data-stu-id="399e7-190">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to use all Five Fingers to grab a larger object.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="399e7-191">![本能手勢遠距小型物件](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-191">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="399e7-192">**小型物件**</span><span class="sxs-lookup"><span data-stu-id="399e7-192">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="399e7-193">![本能手勢遠距中型物件](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-193">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="399e7-194">**中型物件**</span><span class="sxs-lookup"><span data-stu-id="399e7-194">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="399e7-195">![本能手勢遠距大型物件](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-195">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="399e7-196">**大型物件**</span><span class="sxs-lookup"><span data-stu-id="399e7-196">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="399e7-197">手部與 6 DoF 控制器之間的對稱設計</span><span class="sxs-lookup"><span data-stu-id="399e7-197">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="399e7-198">針對混合實境入口網站 (MRP)，已建立並定義了遠方互動的指向和行動概念。</span><span class="sxs-lookup"><span data-stu-id="399e7-198">The concept of point and commit for far interaction was created and defined for the Mixed Reality Portal (MRP).</span></span> <span data-ttu-id="399e7-199">在此案例中，使用者會戴上沉浸式頭戴裝置，並透過動作控制器與 3D 物件互動。</span><span class="sxs-lookup"><span data-stu-id="399e7-199">In this scenario, a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="399e7-200">運動控制器會發射光線來指向及操作遠方物件。</span><span class="sxs-lookup"><span data-stu-id="399e7-200">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="399e7-201">控制器上有按鈕，可用來進一步執行不同動作。</span><span class="sxs-lookup"><span data-stu-id="399e7-201">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="399e7-202">我們會套用射線的互動模型，並將其連結至雙手。</span><span class="sxs-lookup"><span data-stu-id="399e7-202">We apply the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="399e7-203">透過此對稱設計，熟悉 MRP 的使用者在使用 HoloLens 2 時，不需要學習另一個用於遠端指向及操作的互動模型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="399e7-203">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLens 2, and the other way around.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="399e7-204">![使用控制器的光線對稱式設計](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-204">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="399e7-205">**控制器光線**</span><span class="sxs-lookup"><span data-stu-id="399e7-205">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="399e7-206">![使用手部的光線對稱式設計](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="399e7-206">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="399e7-207">**手部光線**</span><span class="sxs-lookup"><span data-stu-id="399e7-207">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="399e7-208">MRTK (混合實境工具組) 中適用於 Unity 的手部射線</span><span class="sxs-lookup"><span data-stu-id="399e7-208">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="399e7-209">根據預設，MRTK 會提供一個手部射線 prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers))，其與命令介面的系統手部射線具有相同視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="399e7-209">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="399e7-210">其是在 MRTK 輸入設定檔的 [指標] 下進行指派。</span><span class="sxs-lookup"><span data-stu-id="399e7-210">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="399e7-211">在沉浸式頭戴裝置中，相同的光線會用於運動控制器。</span><span class="sxs-lookup"><span data-stu-id="399e7-211">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="399e7-212">MRTK - 指標設定檔</span><span class="sxs-lookup"><span data-stu-id="399e7-212">MRTK - Pointer profile</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md#pointer-configuration)
* [<span data-ttu-id="399e7-213">MRTK - 輸入系統</span><span class="sxs-lookup"><span data-stu-id="399e7-213">MRTK - Input system</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)
* [<span data-ttu-id="399e7-214">MRTK - 指標</span><span class="sxs-lookup"><span data-stu-id="399e7-214">MRTK - Pointers</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md)

---

## <a name="see-also"></a><span data-ttu-id="399e7-215">請參閱</span><span class="sxs-lookup"><span data-stu-id="399e7-215">See also</span></span>
* [<span data-ttu-id="399e7-216">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="399e7-216">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="399e7-217">目光和行動</span><span class="sxs-lookup"><span data-stu-id="399e7-217">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="399e7-218">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="399e7-218">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="399e7-219">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="399e7-219">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="399e7-220">本能互動</span><span class="sxs-lookup"><span data-stu-id="399e7-220">Instinctual interactions</span></span>](interaction-fundamentals.md)