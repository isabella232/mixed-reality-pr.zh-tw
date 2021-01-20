---
title: 什麼是全像投影？
description: HoloLens 可讓您觀賞三維的全像影像，以及顯示在世界各地的燈光和音效物件。
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、全像投影、設計、互動、混合現實耳機、windows Mixed reality 耳機、什麼是增強的現實
ms.openlocfilehash: cc6b4a4838e7a275b1ef3a45e54c4b894a04b9c2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583347"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="be56f-104">什麼是全像投影？</span><span class="sxs-lookup"><span data-stu-id="be56f-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="be56f-105">HoloLens 可讓您建立全像 **影像**，也就是像真實物件一樣，在世界周圍出現的燈光和音效物件。</span><span class="sxs-lookup"><span data-stu-id="be56f-105">HoloLens lets you create **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="be56f-106">全像投影會回應您的 [注視](../design/gaze-and-commit.md)、 [手勢](../design/gaze-and-commit.md#composite-gestures)和 [語音命令](../design/voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="be56f-106">Holograms respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="be56f-107">他們甚至可以與您的 [真實世界表面](../design/spatial-mapping.md) 互動。</span><span class="sxs-lookup"><span data-stu-id="be56f-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="be56f-108">透過全像投影，您可以建立屬於自己世界的數位物件。</span><span class="sxs-lookup"><span data-stu-id="be56f-108">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="be56f-109">裝置支援</span><span class="sxs-lookup"><span data-stu-id="be56f-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="be56f-110"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="be56f-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="be56f-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="be56f-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="be56f-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="be56f-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="be56f-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="be56f-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="be56f-114">全像投影</span><span class="sxs-lookup"><span data-stu-id="be56f-114">Holograms</span></span></td>
        <td><span data-ttu-id="be56f-115">✔️</span><span class="sxs-lookup"><span data-stu-id="be56f-115">✔️</span></span></td>
        <td><span data-ttu-id="be56f-116">✔️</span><span class="sxs-lookup"><span data-stu-id="be56f-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="be56f-117">全像是由燈光和音效組成</span><span class="sxs-lookup"><span data-stu-id="be56f-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="be56f-118">[HoloLens 轉譯](../develop/platform-capabilities-and-apis/rendering.md)的全像是在使用者的眼睛前方，直接顯示于全像攝影框架中。</span><span class="sxs-lookup"><span data-stu-id="be56f-118">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="be56f-119">全像是將燈光添加到您的世界，這表示您可以看到顯示器的光線和周圍的光線。</span><span class="sxs-lookup"><span data-stu-id="be56f-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="be56f-120">HoloLens 不會從您的眼睛中移除光線，所以無法使用黑色色彩來轉譯全像影像。</span><span class="sxs-lookup"><span data-stu-id="be56f-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="be56f-121">相反地，黑色內容會顯示為透明。</span><span class="sxs-lookup"><span data-stu-id="be56f-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="be56f-122">全像影像可以有許多不同的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="be56f-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="be56f-123">有些是真實且穩固的，有些則是編排卡通和 ethereal。</span><span class="sxs-lookup"><span data-stu-id="be56f-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="be56f-124">您可以使用全像投影來醒目提示您的環境中的功能，或使用它們作為應用程式使用者介面中的元素。</span><span class="sxs-lookup"><span data-stu-id="be56f-124">You can use holograms to highlight features in your surroundings or use them as elements in your app's user interface.</span></span>

![操作全像手](images/hologram-hands-940px.jpg)

<span data-ttu-id="be56f-126">全像投影也 [可以製作音效，看起來就](../design/spatial-sound.md)像是來自您周圍的特定位置。</span><span class="sxs-lookup"><span data-stu-id="be56f-126">Holograms can also make [sounds](../design/spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="be56f-127">在 HoloLens 上，音效來自兩個位于您的耳上方的喇叭，而不會加以涵蓋。</span><span class="sxs-lookup"><span data-stu-id="be56f-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="be56f-128">就像顯示器一樣，喇叭是加總的，會在不封鎖環境音效的情況下引進新聲音。</span><span class="sxs-lookup"><span data-stu-id="be56f-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="be56f-129">您可以將全息圖放在世界或標記中</span><span class="sxs-lookup"><span data-stu-id="be56f-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="be56f-130">當您有特定的全息圖位置時，可以將它精確地 [放](../design/coordinate-systems.md) 在世界各地。</span><span class="sxs-lookup"><span data-stu-id="be56f-130">When you have a particular location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="be56f-131">當您四處解說時，會根據您的世界來看，全像是穩定的。</span><span class="sxs-lookup"><span data-stu-id="be56f-131">As you walk around, the hologram appears stable based on the world around you.</span></span> <span data-ttu-id="be56f-132">如果您使用 [空間錨點](../design/coordinate-systems.md#spatial-anchors) 來釘選物件，則當您稍後返回時，系統甚至可以記得您離開該物件的位置。</span><span class="sxs-lookup"><span data-stu-id="be56f-132">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![在零售空間中使用 Microsoft Dynamics 365 版面配置的兩個男性](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="be56f-134">有些全息圖案會改為遵循使用者，無論使用者在何處都能自行定位。</span><span class="sxs-lookup"><span data-stu-id="be56f-134">Some holograms follow the user instead, positioning themselves based on the user no matter where they walk.</span></span> <span data-ttu-id="be56f-135">您甚至可以選擇將一段時間帶到一段時間，然後在到達另一個房間之後，將它放在牆上。</span><span class="sxs-lookup"><span data-stu-id="be56f-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="be56f-136">**最佳作法**</span><span class="sxs-lookup"><span data-stu-id="be56f-136">**Best practices**</span></span>
* <span data-ttu-id="be56f-137">在某些案例中，您可能會要求在整個體驗中，全像全像的全像是，</span><span class="sxs-lookup"><span data-stu-id="be56f-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="be56f-138">這種定位有兩種高階方法。</span><span class="sxs-lookup"><span data-stu-id="be56f-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="be56f-139">讓我們將其稱為「 **顯示鎖定** 」和「 **主體鎖定**」。</span><span class="sxs-lookup"><span data-stu-id="be56f-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="be56f-140">顯示鎖定的內容會 positionally 「鎖定」至裝置顯示。</span><span class="sxs-lookup"><span data-stu-id="be56f-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="be56f-141">這種類型的內容很難處理，因為有許多原因，包括非自然的「clingyness」，讓許多使用者感到挫折，並且想要「搖動」。</span><span class="sxs-lookup"><span data-stu-id="be56f-141">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="be56f-142">一般情況下，許多設計師都發現更適合用來避免顯示鎖定的內容。</span><span class="sxs-lookup"><span data-stu-id="be56f-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="be56f-143">主體鎖定的方法遠 forgivable。</span><span class="sxs-lookup"><span data-stu-id="be56f-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="be56f-144">本文-鎖定是指您在3d 空間中 tether 使用者的內文或注視向量。</span><span class="sxs-lookup"><span data-stu-id="be56f-144">Body-locking is when you tether a hologram to the user's body or gaze vector in 3d space.</span></span> <span data-ttu-id="be56f-145">許多經驗都採用了內文鎖定行為，其中的全像是使用者注視的，這可讓使用者旋轉其內文，並在空間中移動，而不會遺失全像影像。</span><span class="sxs-lookup"><span data-stu-id="be56f-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="be56f-146">合併延遲有助於讓全息圖移動感覺更自然。</span><span class="sxs-lookup"><span data-stu-id="be56f-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="be56f-147">比方說，Windows 全像是 Windows 全像的時候，在使用者的外觀鎖定之後，會在使用者看起來像是一種非常有彈性的延遲，在使用者關閉其前端時使用變化。</span><span class="sxs-lookup"><span data-stu-id="be56f-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="be56f-148">將全像觀賞距離的全像是大約是1-2 的計量離 head。</span><span class="sxs-lookup"><span data-stu-id="be56f-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="be56f-149">針對必須持續在全像全像框架中的元素提供漂移量，或考慮在使用者變更其觀點時，將內容以動畫顯示到顯示器的一端。</span><span class="sxs-lookup"><span data-stu-id="be56f-149">Provide a drift amount for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="be56f-150">**將全像全區放在最理想的區域，介於 1.25 m 和 5 m 之間**</span><span class="sxs-lookup"><span data-stu-id="be56f-150">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="be56f-151">這兩個計量最適合，而且體驗將會降低從1計量取得的更接近程度。</span><span class="sxs-lookup"><span data-stu-id="be56f-151">Two meters is the most optimal, and the experience will degrade the closer you get from 1 meter.</span></span> <span data-ttu-id="be56f-152">在距離超過1個計量的距離中，定期移至深度的全像是很可能會造成問題，而不是固定的全像投影。</span><span class="sxs-lookup"><span data-stu-id="be56f-152">At distances nearer than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="be56f-153">當內容太近時，請考慮以適當的方式裁剪或淡化內容，如此您就不會讓使用者進入未預期的體驗。</span><span class="sxs-lookup"><span data-stu-id="be56f-153">Consider gracefully clipping or fading out your content when it gets too close so you don't jar the user into an unexpected experience.</span></span>

![從使用者處放置全像影像的最佳距離。](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="be56f-155">與您和您的世界互動的全像影像</span><span class="sxs-lookup"><span data-stu-id="be56f-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="be56f-156">全像全像光和音效;它們也是您世界上的有效部分。</span><span class="sxs-lookup"><span data-stu-id="be56f-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="be56f-157">以您手中的手中看看您的手中的手，然後您就可以開始使用全像投影。</span><span class="sxs-lookup"><span data-stu-id="be56f-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="be56f-158">提供聲音命令給全像影像，並可回復。</span><span class="sxs-lookup"><span data-stu-id="be56f-158">Give a voice command to a hologram, and it can reply.</span></span>

![使用 Microsoft HoloLens 2 在伺服器陣列開發專案上共同作業的政府公用程式工作者群組](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="be56f-160">全像是可讓您無法在別處進行個人互動。</span><span class="sxs-lookup"><span data-stu-id="be56f-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="be56f-161">由於 HoloLens 知道世界的所在位置，因此當您四處移動空間時，全像全像的字元可以直接在眼睛中看到。</span><span class="sxs-lookup"><span data-stu-id="be56f-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="be56f-162">全息圖也可以與您的環境互動。</span><span class="sxs-lookup"><span data-stu-id="be56f-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="be56f-163">例如，您可以將全息的彈跳球放在資料表上方。</span><span class="sxs-lookup"><span data-stu-id="be56f-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="be56f-164">然後，利用點 [一下，觀賞球彈，然後](../design/gaze-and-commit.md#composite-gestures)在到達表格時音效。</span><span class="sxs-lookup"><span data-stu-id="be56f-164">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound when it hits the table.</span></span>

<span data-ttu-id="be56f-165">實際的物件也可以 pixels occluded 全像影像。</span><span class="sxs-lookup"><span data-stu-id="be56f-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="be56f-166">例如，全像攝影的字元可能會讓您看不到幕後的大門。</span><span class="sxs-lookup"><span data-stu-id="be56f-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="be56f-167">**整合全像影像和真實世界的秘訣**</span><span class="sxs-lookup"><span data-stu-id="be56f-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="be56f-168">對齊 gravitational 規則可讓您更輕鬆地與可信相關的影像。</span><span class="sxs-lookup"><span data-stu-id="be56f-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="be56f-169">例如：將全像狗放在地面上 & 花瓶在資料表上，而不是讓它們浮在空間中。</span><span class="sxs-lookup"><span data-stu-id="be56f-169">for example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="be56f-170">許多設計人員發現，他們可以藉由在桌上的表面上建立「負陰影」來整合更可信的全像投影。</span><span class="sxs-lookup"><span data-stu-id="be56f-170">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="be56f-171">若要這麼做，您可以在全像是建立全像影像，然後從發光減去「陰影」。</span><span class="sxs-lookup"><span data-stu-id="be56f-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="be56f-172">軟性發光與真實世界的光線整合，其使用陰影來地面環境中的全像影像。</span><span class="sxs-lookup"><span data-stu-id="be56f-172">The soft glow integrates with the light from the real world, which uses the shadow to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="be56f-173">全像影像</span><span class="sxs-lookup"><span data-stu-id="be56f-173">A hologram is whatever</span></span> <br><span data-ttu-id="be56f-174">您可以夢想</span><span class="sxs-lookup"><span data-stu-id="be56f-174">you can dream up</span></span><br>
        <span data-ttu-id="be56f-175">作為全像攝影的開發人員，您可以將您的創意從2D 畫面移至世界各地。</span><span class="sxs-lookup"><span data-stu-id="be56f-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="be56f-176">*您* 會建立什麼？</span><span class="sxs-lookup"><span data-stu-id="be56f-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="be56f-177">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="be56f-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="be56f-178">![客廳的全像虛構世界](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="be56f-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="be56f-179">下一個探索檢查點</span><span class="sxs-lookup"><span data-stu-id="be56f-179">Next Discovery Checkpoint</span></span>

<span data-ttu-id="be56f-180">如果您有遵循我們安排的[探索旅程](get-started-with-mr.md)，則您正處於探索混合實境基本概念的途中。</span><span class="sxs-lookup"><span data-stu-id="be56f-180">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="be56f-181">您可以從這裡繼續進行下一個基本主題：</span><span class="sxs-lookup"><span data-stu-id="be56f-181">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="be56f-182">展開您的設計程序</span><span class="sxs-lookup"><span data-stu-id="be56f-182">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)