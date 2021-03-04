---
title: 手部直接操作
description: 深入了解直接操作，這是一種讓使用者直接用手觸摸全像投影的輸入模型。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 注視, 注視定向, 互動, 設計, 手部接近, HoloLens, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, MRTK, 混合實境工具組, 按鈕, 碰撞器, 週框方塊, 2D, 本能手勢
ms.openlocfilehash: 8316452b8308e159612a81d097c352cf1d935362
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759320"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="c4a63-104">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="c4a63-104">Direct manipulation with hands</span></span>

![按鈕](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="c4a63-106">直接操作是直接以雙手觸控全像投影的輸入模型。</span><span class="sxs-lookup"><span data-stu-id="c4a63-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="c4a63-107">這個概念背後的構想是要讓物件如同在真實環境中作動。</span><span class="sxs-lookup"><span data-stu-id="c4a63-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="c4a63-108">按鈕只要按下即可啟用、物件可藉由抓取來選取，2D 內容的行為則類似於虛擬觸控螢幕。</span><span class="sxs-lookup"><span data-stu-id="c4a63-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="c4a63-109">直接操作以能供性為基礎，這表示它很容易使用。</span><span class="sxs-lookup"><span data-stu-id="c4a63-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="c4a63-110">使用者不需學習任何象徵性的手勢。</span><span class="sxs-lookup"><span data-stu-id="c4a63-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="c4a63-111">所有互動都是以您可觸摸或抓取的視覺化元素為基礎。</span><span class="sxs-lookup"><span data-stu-id="c4a63-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="c4a63-112">我們將直接操作視為「近距離」輸入模型，因為它最適合用於伸手可及範圍內的內容互動。</span><span class="sxs-lookup"><span data-stu-id="c4a63-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="c4a63-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c4a63-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="c4a63-114"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="c4a63-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="c4a63-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c4a63-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="c4a63-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="c4a63-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="c4a63-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="c4a63-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="c4a63-118">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="c4a63-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="c4a63-119">❌ 未支援</span><span class="sxs-lookup"><span data-stu-id="c4a63-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="c4a63-120">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="c4a63-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="c4a63-121">➕ 支援。</span><span class="sxs-lookup"><span data-stu-id="c4a63-121">➕ Supported.</span></span>  <span data-ttu-id="c4a63-122">針對 UI，建議您改為使用<a href="point-and-commit.md">手部指向和行動</a>。</span><span class="sxs-lookup"><span data-stu-id="c4a63-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="c4a63-123">直接操作是 HoloLens 2 的主要輸入模型，HoloLens 2 使用新式連貫手部追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="c4a63-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="c4a63-124">您也可使用運動控制器，搭配沉浸式頭戴裝置來操作輸入模型，但對於物件操作以外的互動，不建議以此作為主要機制。</span><span class="sxs-lookup"><span data-stu-id="c4a63-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="c4a63-125">在 HoloLens (第 1 代) 上無法進行直接操作。</span><span class="sxs-lookup"><span data-stu-id="c4a63-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="c4a63-126">可碰撞的指尖</span><span class="sxs-lookup"><span data-stu-id="c4a63-126">Collidable fingertip</span></span>

<span data-ttu-id="c4a63-127">在 HoloLens 2 上，使用者的雙手會被辨識和解譯為左右兩手的架構模型。</span><span class="sxs-lookup"><span data-stu-id="c4a63-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="c4a63-128">若要實作直接以雙手觸控全像投影的概念，在理想情況下，五個 collider 可以連結至左右兩手架構模型的五個指尖。</span><span class="sxs-lookup"><span data-stu-id="c4a63-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="c4a63-129">但由於缺少觸覺反饋能力，10 個可碰撞的指尖可能對全像投影造成非預期且無法預測的衝突。</span><span class="sxs-lookup"><span data-stu-id="c4a63-129">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="c4a63-130">我們建議僅將 collider 放在兩手的食指上。</span><span class="sxs-lookup"><span data-stu-id="c4a63-130">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="c4a63-131">可碰撞的食指指尖仍可作為使用中的觸控點，用於涉及其他手指的各種觸控手勢。</span><span class="sxs-lookup"><span data-stu-id="c4a63-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="c4a63-132">觸控手勢包括一指點按、一指點選、兩指點按和五指點按，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4a63-132">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c4a63-133">![可碰撞的指尖](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="c4a63-134">**可碰撞的指尖**</span><span class="sxs-lookup"><span data-stu-id="c4a63-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-135">![一指點按](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="c4a63-136">**一指點按**</span><span class="sxs-lookup"><span data-stu-id="c4a63-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-137">![一指點選](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="c4a63-138">**一指點選**</span><span class="sxs-lookup"><span data-stu-id="c4a63-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-139">![五指點按](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="c4a63-140">**五指點按**</span><span class="sxs-lookup"><span data-stu-id="c4a63-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="c4a63-141">球體 collider</span><span class="sxs-lookup"><span data-stu-id="c4a63-141">Sphere collider</span></span>

<span data-ttu-id="c4a63-142">建議您不要使用隨機的一般形狀，而應使用球體 collider。</span><span class="sxs-lookup"><span data-stu-id="c4a63-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="c4a63-143">然後，您可以用視覺化的方式加以呈現，為近距離目標鎖定提供明確的提示。</span><span class="sxs-lookup"><span data-stu-id="c4a63-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="c4a63-144">球體的直徑應符合食指的粗細，以提高觸控的正確性。</span><span class="sxs-lookup"><span data-stu-id="c4a63-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="c4a63-145">呼叫手部 API，更容易擷取手指粗細的變數。</span><span class="sxs-lookup"><span data-stu-id="c4a63-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="c4a63-146">指尖游標</span><span class="sxs-lookup"><span data-stu-id="c4a63-146">Fingertip cursor</span></span>

<span data-ttu-id="c4a63-147">除了在食指指尖上顯示可碰撞的球體以外，我們也建立了進階的指尖游標，以提供更好的近距離目標鎖定體驗。</span><span class="sxs-lookup"><span data-stu-id="c4a63-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="c4a63-148">這是連結至食指指尖的一個環狀游標。</span><span class="sxs-lookup"><span data-stu-id="c4a63-148">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="c4a63-149">此游標會根據鄰近性，在方向和大小方面動態回應目標，詳述如下：</span><span class="sxs-lookup"><span data-stu-id="c4a63-149">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="c4a63-150">當食指移向全像投影時，游標一律會與全像投影的表面平行，且其大小會逐漸縮減。</span><span class="sxs-lookup"><span data-stu-id="c4a63-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="c4a63-151">當手指接觸到表面時，游標會縮減為一個點，並發出觸控事件。</span><span class="sxs-lookup"><span data-stu-id="c4a63-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="c4a63-152">透過互動式反饋，使用者可執行高精確度的近距離目標鎖定工作，例如觸發超連結或按下按鈕，如下所示。</span><span class="sxs-lookup"><span data-stu-id="c4a63-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="c4a63-153">![指尖游標遠距](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="c4a63-154">**指尖游標遠距**</span><span class="sxs-lookup"><span data-stu-id="c4a63-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-155">![指尖游標近距](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="c4a63-156">**指尖游標近距**</span><span class="sxs-lookup"><span data-stu-id="c4a63-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-157">![指尖游標接觸](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="c4a63-158">**指尖游標接觸**</span><span class="sxs-lookup"><span data-stu-id="c4a63-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="c4a63-159">週框方塊與近接著色器</span><span class="sxs-lookup"><span data-stu-id="c4a63-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="c4a63-160">全像投影本身也須具備提供視覺和聽覺反饋的能力，以彌補觸覺反饋能力的不足。</span><span class="sxs-lookup"><span data-stu-id="c4a63-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="c4a63-161">為此，我們設計了週框方塊與近接著色器的概念。</span><span class="sxs-lookup"><span data-stu-id="c4a63-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="c4a63-162">週框方塊是足以包覆一個 3D 物件的最小體積區域。</span><span class="sxs-lookup"><span data-stu-id="c4a63-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="c4a63-163">週框方塊具有互動式呈現機制，名為近接著色器。</span><span class="sxs-lookup"><span data-stu-id="c4a63-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="c4a63-164">近接著色器的行為如下：</span><span class="sxs-lookup"><span data-stu-id="c4a63-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c4a63-165">![暫留 (遠距) 視覺化回饋](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="c4a63-166">**暫留 (遠距)**</span><span class="sxs-lookup"><span data-stu-id="c4a63-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="c4a63-167">當食指進入範圍內時，手指焦點即會投射在週框方塊的表面。</span><span class="sxs-lookup"><span data-stu-id="c4a63-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-168">![暫留 (近距) 視覺化回饋](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="c4a63-169">**暫留 (近距)**</span><span class="sxs-lookup"><span data-stu-id="c4a63-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="c4a63-170">當指尖越來越接近表面時，焦點會縮小。</span><span class="sxs-lookup"><span data-stu-id="c4a63-170">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-171">![接觸開始](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="c4a63-172">**接觸開始**</span><span class="sxs-lookup"><span data-stu-id="c4a63-172">**Contact begins**</span></span><br>
       <span data-ttu-id="c4a63-173">手指一碰到表面時，整個週框方塊就會變色，或產生視覺效果以反映觸碰狀態。</span><span class="sxs-lookup"><span data-stu-id="c4a63-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-174">![接觸結束](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="c4a63-175">**接觸結束**</span><span class="sxs-lookup"><span data-stu-id="c4a63-175">**Contact ends**</span></span><br>
       <span data-ttu-id="c4a63-176">此外也可以啟用音效來補強視覺的觸碰反饋。</span><span class="sxs-lookup"><span data-stu-id="c4a63-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="c4a63-177">可點按的按鈕</span><span class="sxs-lookup"><span data-stu-id="c4a63-177">Pressable button</span></span>

<span data-ttu-id="c4a63-178">有了可碰撞的指尖，使用者即可與基本的全像攝影 UI 元件互動，例如可點按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4a63-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="c4a63-179">可點按的按鈕是專為直接手指點按設計的全像攝影按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4a63-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="c4a63-180">同樣地，由於缺少觸覺反饋能力，可點按的按鈕也設有若干機制，來處理觸覺反饋能力的相關問題。</span><span class="sxs-lookup"><span data-stu-id="c4a63-180">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="c4a63-181">第一項機制是具有近接著色器的週框方塊，其詳細說明請見上一節。</span><span class="sxs-lookup"><span data-stu-id="c4a63-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="c4a63-182">它可讓使用者在接近及觸碰按鈕時更能清楚感知鄰近性。</span><span class="sxs-lookup"><span data-stu-id="c4a63-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="c4a63-183">第二項機制是下壓。</span><span class="sxs-lookup"><span data-stu-id="c4a63-183">The second mechanism is depression.</span></span> <span data-ttu-id="c4a63-184">下壓會在指尖接觸到按鈕後，產生按下的感覺。</span><span class="sxs-lookup"><span data-stu-id="c4a63-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="c4a63-185">此機制能確保按鈕會緊隨著指尖沿深度軸移動。</span><span class="sxs-lookup"><span data-stu-id="c4a63-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="c4a63-186">在按鈕達到所選的深度 (按下) 或離開該深度 (放開) 之後，就會觸發按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4a63-186">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="c4a63-187">在觸發按鈕時應加上音效以增強反饋。</span><span class="sxs-lookup"><span data-stu-id="c4a63-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c4a63-188">![可點按的按鈕遠距](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="c4a63-189">**手指遠離**</span><span class="sxs-lookup"><span data-stu-id="c4a63-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-190">![可點按的按鈕近距](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="c4a63-191">**手指靠近**</span><span class="sxs-lookup"><span data-stu-id="c4a63-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-192">![可點按的按鈕接觸開始](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="c4a63-193">**接觸開始**</span><span class="sxs-lookup"><span data-stu-id="c4a63-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-194">![可點按的按鈕點按](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="c4a63-195">**按下**</span><span class="sxs-lookup"><span data-stu-id="c4a63-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="c4a63-196">2D 平板互動</span><span class="sxs-lookup"><span data-stu-id="c4a63-196">2D slate interaction</span></span>

<span data-ttu-id="c4a63-197">2D [平板](slate.md)是用來裝載 2D 應用程式內容 (例如網頁瀏覽器) 的全像攝影容器。</span><span class="sxs-lookup"><span data-stu-id="c4a63-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="c4a63-198">透過直接操作與 2D 平板互動的設計概念，和與實體觸控螢幕互動的設計概念相同。</span><span class="sxs-lookup"><span data-stu-id="c4a63-198">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="c4a63-199">與觸控平板互動</span><span class="sxs-lookup"><span data-stu-id="c4a63-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c4a63-200">![觸控](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="c4a63-201">**觸控**</span><span class="sxs-lookup"><span data-stu-id="c4a63-201">**Touch**</span></span><br>
       <span data-ttu-id="c4a63-202">以食指按下超連結或按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4a63-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-203">![捲動](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="c4a63-204">**捲動**</span><span class="sxs-lookup"><span data-stu-id="c4a63-204">**Scroll**</span></span><br>
        <span data-ttu-id="c4a63-205">以食指向上和向下捲動平板內容。</span><span class="sxs-lookup"><span data-stu-id="c4a63-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-206">![縮放](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="c4a63-207">**縮放**</span><span class="sxs-lookup"><span data-stu-id="c4a63-207">**Zoom**</span></span><br>
       <span data-ttu-id="c4a63-208">使用者可用兩根食指，根據手指的相對移動來放大和縮小平板內容。</span><span class="sxs-lookup"><span data-stu-id="c4a63-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="c4a63-209">操作 2D 平板本身</span><span class="sxs-lookup"><span data-stu-id="c4a63-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c4a63-210">![顯示抓取和拖曳功能的圖形](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-210">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="c4a63-211">**移動**</span><span class="sxs-lookup"><span data-stu-id="c4a63-211">**Move**</span></span><br>
       <span data-ttu-id="c4a63-212">將手靠近角落或邊緣時，可顯示最接近的操作能供性。</span><span class="sxs-lookup"><span data-stu-id="c4a63-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="c4a63-213">抓取 2D 平板上方的 holobar，可以移動整個平板。</span><span class="sxs-lookup"><span data-stu-id="c4a63-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-214">![顯示縮放功能的圖形](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-214">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="c4a63-215">**縮放比例**</span><span class="sxs-lookup"><span data-stu-id="c4a63-215">**Scale**</span></span><br>
        <span data-ttu-id="c4a63-216">抓取操作能供性，並透過角落能供性進行統一縮放。</span><span class="sxs-lookup"><span data-stu-id="c4a63-216">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-217">![自動重排](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="c4a63-218">**自動重排**</span><span class="sxs-lookup"><span data-stu-id="c4a63-218">**Reflow**</span></span><br>
       <span data-ttu-id="c4a63-219">抓取操作能供性，透過邊緣能供性進行自動重排。</span><span class="sxs-lookup"><span data-stu-id="c4a63-219">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="c4a63-220">3D 物件操作</span><span class="sxs-lookup"><span data-stu-id="c4a63-220">3D object manipulation</span></span>

<span data-ttu-id="c4a63-221">HoloLens 2 可讓使用者將週框方塊套用至每個 3D 物件，以便用手指引及操作 3D 全像攝影物件。</span><span class="sxs-lookup"><span data-stu-id="c4a63-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="c4a63-222">週框方塊可透過其近接著色器提供更確切的深度認知。</span><span class="sxs-lookup"><span data-stu-id="c4a63-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="c4a63-223">週框方塊衍生出兩種 3D 物件操作方法。</span><span class="sxs-lookup"><span data-stu-id="c4a63-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="c4a63-224">能供性操作</span><span class="sxs-lookup"><span data-stu-id="c4a63-224">Affordance-based manipulation</span></span>

<span data-ttu-id="c4a63-225">能供性操作可讓您透過週框方塊及其周圍的操作能供性來操作 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="c4a63-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="c4a63-226">![顯示物件週框方塊和移動功能的圖形](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-226">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="c4a63-227">**移動**</span><span class="sxs-lookup"><span data-stu-id="c4a63-227">**Move**</span></span><br>
       <span data-ttu-id="c4a63-228">當使用者的手接近 3D 物件時，就會顯示週框方塊和最接近的能供性。</span><span class="sxs-lookup"><span data-stu-id="c4a63-228">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="c4a63-229">使用者可以抓取週框方塊來移動整個物件。</span><span class="sxs-lookup"><span data-stu-id="c4a63-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-230">![顯示抓取物件邊緣以旋轉的使用者圖形](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-230">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="c4a63-231">**旋轉**</span><span class="sxs-lookup"><span data-stu-id="c4a63-231">**Rotate**</span></span><br>
        <span data-ttu-id="c4a63-232">使用者可以抓取邊緣能供性來進行旋轉。</span><span class="sxs-lookup"><span data-stu-id="c4a63-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-233">![顯示抓取物件角落以縮放的使用者圖形](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-233">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="c4a63-234">**縮放比例**</span><span class="sxs-lookup"><span data-stu-id="c4a63-234">**Scale**</span></span><br>
       <span data-ttu-id="c4a63-235">使用者可以抓取角落能供性來執行統一尺寸調整。</span><span class="sxs-lookup"><span data-stu-id="c4a63-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="c4a63-236">非能供性操作</span><span class="sxs-lookup"><span data-stu-id="c4a63-236">Non-affordance-based manipulation</span></span>

<span data-ttu-id="c4a63-237">非能供性操作不會將能供性連結至週框方塊。</span><span class="sxs-lookup"><span data-stu-id="c4a63-237">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="c4a63-238">使用者只能顯示週框方塊，然後直接與它互動。</span><span class="sxs-lookup"><span data-stu-id="c4a63-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="c4a63-239">若以一隻手抓住週框方塊，物件的轉譯和旋轉會與那隻手的動作和方向相關聯。</span><span class="sxs-lookup"><span data-stu-id="c4a63-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="c4a63-240">以雙手抓住物件時，使用者可以根據兩隻手的相對動作來轉譯、縮放及旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="c4a63-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="c4a63-241">特定操作需要精確度。</span><span class="sxs-lookup"><span data-stu-id="c4a63-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="c4a63-242">建議您使用 **能供性操作**，因為它可提供高層級的細微性。</span><span class="sxs-lookup"><span data-stu-id="c4a63-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="c4a63-243">針對彈性操作，建議您使用 **非能供性操作**，因為它可帶來即時而有趣的體驗。</span><span class="sxs-lookup"><span data-stu-id="c4a63-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="c4a63-244">本能手勢</span><span class="sxs-lookup"><span data-stu-id="c4a63-244">Instinctual gestures</span></span>

<span data-ttu-id="c4a63-245">在 HoloLens (第 1 代) 推出時，我們曾教過使用者幾個預先定義的手勢，例如綻開和空中點選。</span><span class="sxs-lookup"><span data-stu-id="c4a63-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="c4a63-246">而在使用 HoloLens 2 時，使用者並不需要記住任何象徵性的手勢。</span><span class="sxs-lookup"><span data-stu-id="c4a63-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="c4a63-247">使用者與全像投影和內容互動時所需使用的所有必要手勢，都是符合本能的。</span><span class="sxs-lookup"><span data-stu-id="c4a63-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="c4a63-248">協助使用者透過 UI 能供性的設計執行手勢，他們就能學會本能手勢。</span><span class="sxs-lookup"><span data-stu-id="c4a63-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="c4a63-249">例如，如果我們引導使用者以兩指捏合抓取某個物件或控制點，表示該物件或控制點應該很小。</span><span class="sxs-lookup"><span data-stu-id="c4a63-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="c4a63-250">如果我們要使用者進行五指抓取，表示該物件或控制點應相對較大。</span><span class="sxs-lookup"><span data-stu-id="c4a63-250">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="c4a63-251">與按鈕類似，微小的按鈕會使得使用者只能用單一手指進行按壓。</span><span class="sxs-lookup"><span data-stu-id="c4a63-251">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="c4a63-252">較大的按鈕會促使使用者使用手掌進行按壓。</span><span class="sxs-lookup"><span data-stu-id="c4a63-252">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="c4a63-253">![顯示抓取小型物件以移動的使用者圖形](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-253">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="c4a63-254">**小型物件**</span><span class="sxs-lookup"><span data-stu-id="c4a63-254">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-255">![顯示抓取中型物件以移動的使用者圖形](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-255">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="c4a63-256">**中型物件**</span><span class="sxs-lookup"><span data-stu-id="c4a63-256">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c4a63-257">![顯示抓取大型物件以移動的使用者圖形](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="c4a63-257">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="c4a63-258">**大型物件**</span><span class="sxs-lookup"><span data-stu-id="c4a63-258">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="c4a63-259">手部與 6 DoF 控制器之間的對稱設計</span><span class="sxs-lookup"><span data-stu-id="c4a63-259">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="c4a63-260">您可能已經注意到，AR 中的手勢與 VR 中的運動控制器在互動方式上有其相似之處。</span><span class="sxs-lookup"><span data-stu-id="c4a63-260">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="c4a63-261">這兩種輸入在其各自的環境中都可用來觸發直接操作。</span><span class="sxs-lookup"><span data-stu-id="c4a63-261">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="c4a63-262">在 HoloLens 2 中，近距離以手抓取並拖曳的效用，非常類似於 WMR 運動控制器上的抓取按鈕所能做到的。</span><span class="sxs-lookup"><span data-stu-id="c4a63-262">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="c4a63-263">這種相似性可讓使用者在兩種平台上都能採用熟悉的互動方式，且若您決定在這兩個平台之間移轉應用程式，這一點可能也有幫助。</span><span class="sxs-lookup"><span data-stu-id="c4a63-263">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="c4a63-264">透過眼球追蹤達到最佳效果</span><span class="sxs-lookup"><span data-stu-id="c4a63-264">Optimize with eye tracking</span></span>

<span data-ttu-id="c4a63-265">直接操作若能如預期運作，將可達到奇妙的效果。</span><span class="sxs-lookup"><span data-stu-id="c4a63-265">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="c4a63-266">但若無法順利將手移到想要的位置，而老是無意中觸發全像投影，就會出現挫敗感。</span><span class="sxs-lookup"><span data-stu-id="c4a63-266">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="c4a63-267">眼球追蹤或許有助於判斷使用者真正的意圖。</span><span class="sxs-lookup"><span data-stu-id="c4a63-267">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="c4a63-268">**時機**：避免無意中觸發操作回應。</span><span class="sxs-lookup"><span data-stu-id="c4a63-268">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="c4a63-269">眼球追蹤有助於了解使用者目前從事的活動。</span><span class="sxs-lookup"><span data-stu-id="c4a63-269">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="c4a63-270">例如，想像您在閱讀全像攝影 (指示) 文字時，您伸手要去拿實際環境中的工具。</span><span class="sxs-lookup"><span data-stu-id="c4a63-270">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="c4a63-271">此時，您的手不小心劃過某個您根本沒留意過的互動式全像攝影按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4a63-271">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="c4a63-272">例如，該按鈕可能不在使用者的視野 (FoV) 內。</span><span class="sxs-lookup"><span data-stu-id="c4a63-272">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="c4a63-273">如果使用者已有一段時間未注視某個全像投影，但仍偵測到觸碰或抓取事件，表示此互動很可能是無意的。</span><span class="sxs-lookup"><span data-stu-id="c4a63-273">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="c4a63-274">**標的**：除了處理誤判的啟用以外，它還有助於判斷所應抓取或觸碰的全像投影，因為從您的視角可能無法看出精準的交叉點，尤其是有數個全像投影的位置彼此十分靠近時。</span><span class="sxs-lookup"><span data-stu-id="c4a63-274">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="c4a63-275">雖然 HoloLens 2 的眼球追蹤在判斷眼部注視時會因其精準度而有所限制，但對近距離互動而言仍不失為有利的工具，因為透過手部輸入互動時，會有深度的差異。</span><span class="sxs-lookup"><span data-stu-id="c4a63-275">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="c4a63-276">舉例而言，要判斷您的手是在全像投影的後面還是前面，以精確地抓取操作工具，有時是很困難的。</span><span class="sxs-lookup"><span data-stu-id="c4a63-276">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="c4a63-277">**目的地**：運用使用者在執行快速拋投手勢時看往何處的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c4a63-277">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="c4a63-278">抓取全像投影並約略拋向您要的目的地。</span><span class="sxs-lookup"><span data-stu-id="c4a63-278">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="c4a63-279">雖然這有時行得通，但快速執行手勢可能會導致目的地嚴重失準。</span><span class="sxs-lookup"><span data-stu-id="c4a63-279">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="c4a63-280">不過，同時運用眼球追蹤或可改善手勢的準確度。</span><span class="sxs-lookup"><span data-stu-id="c4a63-280">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c4a63-281">MRTK (混合實境工具組) 中適用於 Unity 的操作</span><span class="sxs-lookup"><span data-stu-id="c4a63-281">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="c4a63-282">透過 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，您可以使用指令碼 **ObjectManipulator** 輕鬆執行常見的操作行為。</span><span class="sxs-lookup"><span data-stu-id="c4a63-282">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="c4a63-283">使用 ObjectManipulator，您可以直接用手或透過手部射線來抓取和移動物件。</span><span class="sxs-lookup"><span data-stu-id="c4a63-283">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="c4a63-284">它也支援雙手操作來縮放和旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="c4a63-284">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="c4a63-285">MRTK - 操作</span><span class="sxs-lookup"><span data-stu-id="c4a63-285">MRTK - Manipulation</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-manipulator.md)

---

## <a name="see-also"></a><span data-ttu-id="c4a63-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4a63-286">See also</span></span>

* [<span data-ttu-id="c4a63-287">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="c4a63-287">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="c4a63-288">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="c4a63-288">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="c4a63-289">本能互動</span><span class="sxs-lookup"><span data-stu-id="c4a63-289">Instinctual interactions</span></span>](interaction-fundamentals.md)