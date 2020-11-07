---
title: 什麼是全像投影？
description: HoloLens 可讓您觀賞三維的全像影像，以及顯示在世界各地的燈光和音效物件。
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、全像影像、設計、互動
ms.openlocfilehash: 5e0ef2768b6e79136f8144492d6825107a6ed88e
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340696"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="c0a28-104">什麼是全像投影？</span><span class="sxs-lookup"><span data-stu-id="c0a28-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="c0a28-105">HoloLens 可讓您建立像是在世界各地出現在世界各地的全像 **影像** 、像是真實物件一樣的聲音和音效物件。</span><span class="sxs-lookup"><span data-stu-id="c0a28-105">HoloLens lets you create **holograms** , objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="c0a28-106">全像投影會回應您的 [注視](../design/gaze-and-commit.md)、 [手勢](../design/gaze-and-commit.md#composite-gestures) 和 [語音命令](../design/voice-input.md)，並且可以與您的 [真實世界表面](../design/spatial-mapping.md) 互動。</span><span class="sxs-lookup"><span data-stu-id="c0a28-106">Holograms respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures) and [voice commands](../design/voice-input.md), and can interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="c0a28-107">透過全像投影，您可以建立屬於自己世界的數位物件。</span><span class="sxs-lookup"><span data-stu-id="c0a28-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="c0a28-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c0a28-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c0a28-109"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="c0a28-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c0a28-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c0a28-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c0a28-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c0a28-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="c0a28-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="c0a28-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c0a28-113">全像投影</span><span class="sxs-lookup"><span data-stu-id="c0a28-113">Holograms</span></span></td>
        <td><span data-ttu-id="c0a28-114">✔️</span><span class="sxs-lookup"><span data-stu-id="c0a28-114">✔️</span></span></td>
        <td><span data-ttu-id="c0a28-115">✔️</span><span class="sxs-lookup"><span data-stu-id="c0a28-115">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="c0a28-116">全像是由燈光和音效組成</span><span class="sxs-lookup"><span data-stu-id="c0a28-116">A hologram is made of light and sound</span></span>

<span data-ttu-id="c0a28-117">[HoloLens 轉譯](../develop/platform-capabilities-and-apis/rendering.md)的全像是在使用者的眼睛前方，直接顯示于全像攝影框架中。</span><span class="sxs-lookup"><span data-stu-id="c0a28-117">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="c0a28-118">全像是將燈光添加到您的世界，這表示您可以看到顯示器的光線和周圍的光線。</span><span class="sxs-lookup"><span data-stu-id="c0a28-118">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="c0a28-119">HoloLens 不會從您的眼睛中移除光線，所以無法使用黑色色彩來轉譯全像影像。</span><span class="sxs-lookup"><span data-stu-id="c0a28-119">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="c0a28-120">相反地，黑色內容會顯示為透明。</span><span class="sxs-lookup"><span data-stu-id="c0a28-120">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="c0a28-121">全像影像可以有許多不同的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="c0a28-121">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="c0a28-122">有些是真實且穩固的，有些則是編排卡通和 ethereal。</span><span class="sxs-lookup"><span data-stu-id="c0a28-122">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="c0a28-123">全像投影可以反白顯示您的環境中的功能，也可以是應用程式使用者介面中的元素。</span><span class="sxs-lookup"><span data-stu-id="c0a28-123">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![操作全像手](images/hologram-hands-940px.jpg)

<span data-ttu-id="c0a28-125">全像投影也 [可以製作音效，看起來就](../design/spatial-sound.md)像是來自您周圍的特定位置。</span><span class="sxs-lookup"><span data-stu-id="c0a28-125">Holograms can also make [sounds](../design/spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="c0a28-126">在 HoloLens 上，音效來自兩個位于您的耳上方的喇叭，而不會加以涵蓋。</span><span class="sxs-lookup"><span data-stu-id="c0a28-126">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="c0a28-127">就像顯示器一樣，喇叭是加總的，會在不封鎖環境音效的情況下引進新聲音。</span><span class="sxs-lookup"><span data-stu-id="c0a28-127">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="c0a28-128">您可以將全息圖放在世界或標記中</span><span class="sxs-lookup"><span data-stu-id="c0a28-128">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="c0a28-129">當您有想要的特定位置時，您可以將它 [放](../design/coordinate-systems.md) 在世界中的精確位置。</span><span class="sxs-lookup"><span data-stu-id="c0a28-129">When you have a particular location where you want a hologram, you can [place](../design/coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="c0a28-130">當您四處解說該全像投影時，它將會與您周圍的世界相對穩定。</span><span class="sxs-lookup"><span data-stu-id="c0a28-130">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="c0a28-131">如果您使用 [空間錨點](../design/coordinate-systems.md#spatial-anchors) 將該物件牢牢釘選到世界，則在稍後返回時，系統甚至可以記得您離開該物件的位置。</span><span class="sxs-lookup"><span data-stu-id="c0a28-131">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![在零售空間中使用 Microsoft Dynamics 365 版面配置的兩個男性](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="c0a28-133">部分的全像是以使用者為依據。</span><span class="sxs-lookup"><span data-stu-id="c0a28-133">Some holograms follow the user instead.</span></span> <span data-ttu-id="c0a28-134">無論使用者在何處進行，這些都是相對於使用者的標記投影位置。</span><span class="sxs-lookup"><span data-stu-id="c0a28-134">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="c0a28-135">您甚至可以選擇將一段時間帶到一段時間，然後在到達另一個房間之後，將它放在牆上。</span><span class="sxs-lookup"><span data-stu-id="c0a28-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="c0a28-136">**最佳做法**</span><span class="sxs-lookup"><span data-stu-id="c0a28-136">**Best practices**</span></span>
* <span data-ttu-id="c0a28-137">在某些案例中，您可能會要求在整個體驗中，全像全像的全像是，</span><span class="sxs-lookup"><span data-stu-id="c0a28-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="c0a28-138">這種定位有兩種高階方法。</span><span class="sxs-lookup"><span data-stu-id="c0a28-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="c0a28-139">讓我們將其稱為「 **顯示鎖定** 」和「 **主體鎖定** 」。</span><span class="sxs-lookup"><span data-stu-id="c0a28-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="c0a28-140">顯示鎖定的內容會 positionally 「鎖定」至裝置顯示。</span><span class="sxs-lookup"><span data-stu-id="c0a28-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="c0a28-141">這很難處理許多原因，包括非自然感覺「clingyness」，讓許多使用者感到沮喪，並且想要「搖動」。</span><span class="sxs-lookup"><span data-stu-id="c0a28-141">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="c0a28-142">一般情況下，許多設計師都發現更適合用來避免顯示鎖定的內容。</span><span class="sxs-lookup"><span data-stu-id="c0a28-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="c0a28-143">主體鎖定的方法遠 forgivable。</span><span class="sxs-lookup"><span data-stu-id="c0a28-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="c0a28-144">本文-鎖定是指將全像行動網卡至使用者的內文或注視向量，但位於使用者周圍的3d 空間中。</span><span class="sxs-lookup"><span data-stu-id="c0a28-144">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="c0a28-145">許多經驗都採用了內文鎖定行為，其中的全像是使用者注視的，這可讓使用者旋轉其內文，並在空間中移動，而不會遺失全像影像。</span><span class="sxs-lookup"><span data-stu-id="c0a28-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="c0a28-146">合併延遲有助於讓全息圖移動感覺更自然。</span><span class="sxs-lookup"><span data-stu-id="c0a28-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="c0a28-147">比方說，Windows 全像是 Windows 全像的時候，在使用者的外觀鎖定之後，會在使用者看起來像是一種非常有彈性的延遲，在使用者關閉其前端時使用變化。</span><span class="sxs-lookup"><span data-stu-id="c0a28-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="c0a28-148">將全像觀賞距離的全像是大約是1-2 的計量離 head。</span><span class="sxs-lookup"><span data-stu-id="c0a28-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="c0a28-149">針對必須持續在全像全像框架中的元素提供漂移，或考慮在使用者變更其觀點時，將內容以動畫顯示到顯示的一端。</span><span class="sxs-lookup"><span data-stu-id="c0a28-149">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="c0a28-150">**將全像位置放在最理想的區域-介於 1.25 m 與5m 之間**</span><span class="sxs-lookup"><span data-stu-id="c0a28-150">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="c0a28-151">這兩個計量最適合，而且體驗將會降低您從單一計量取得的較接近程度。</span><span class="sxs-lookup"><span data-stu-id="c0a28-151">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="c0a28-152">在距離超過一種計量的距離中，定期移往深度的全像投影，更可能會有問題。</span><span class="sxs-lookup"><span data-stu-id="c0a28-152">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="c0a28-153">當內容太近時，請考慮以適當的方式裁剪或淡化內容，以免讓使用者進入未預期的體驗。</span><span class="sxs-lookup"><span data-stu-id="c0a28-153">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![從使用者處放置全像影像的最佳距離。](images/distanceguiderendering-950px.png)

<br>

---


## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="c0a28-155">與您和您的世界互動的全像影像</span><span class="sxs-lookup"><span data-stu-id="c0a28-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="c0a28-156">全像全像光和音效;它們也是您世界上的有效部分。</span><span class="sxs-lookup"><span data-stu-id="c0a28-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="c0a28-157">以您手中的手中看看您的手中的手，然後您就可以開始使用全像投影。</span><span class="sxs-lookup"><span data-stu-id="c0a28-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="c0a28-158">提供聲音命令給全像影像，並可回復。</span><span class="sxs-lookup"><span data-stu-id="c0a28-158">Give a voice command to a hologram, and it can reply.</span></span>

![使用 Microsoft HoloLens 2 在伺服器陣列開發專案上共同作業的政府公用程式工作者群組](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="c0a28-160">全像是可讓您無法在別處進行個人互動。</span><span class="sxs-lookup"><span data-stu-id="c0a28-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="c0a28-161">由於 HoloLens 知道世界的所在位置，因此當您四處移動空間時，全像全像的字元可以直接在眼睛中看到。</span><span class="sxs-lookup"><span data-stu-id="c0a28-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="c0a28-162">全息圖也可以與您的環境互動。</span><span class="sxs-lookup"><span data-stu-id="c0a28-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="c0a28-163">例如，您可以將全息的彈跳球放在資料表上方。</span><span class="sxs-lookup"><span data-stu-id="c0a28-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="c0a28-164">然後，利用點 [一下，觀賞](../design/gaze-and-commit.md#composite-gestures)球的彈跳，並在到達表格時音效。</span><span class="sxs-lookup"><span data-stu-id="c0a28-164">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="c0a28-165">實際的物件也可以 pixels occluded 全像影像。</span><span class="sxs-lookup"><span data-stu-id="c0a28-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="c0a28-166">例如，全像攝影的字元可能會讓您看不到幕後的大門。</span><span class="sxs-lookup"><span data-stu-id="c0a28-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="c0a28-167">**整合全像影像和真實世界的秘訣**</span><span class="sxs-lookup"><span data-stu-id="c0a28-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="c0a28-168">對齊 gravitational 規則可讓您更輕鬆地與可信相關的影像。</span><span class="sxs-lookup"><span data-stu-id="c0a28-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="c0a28-169">例如：在地面放置全像狗 & 花瓶，而不是讓它們浮在空間中。</span><span class="sxs-lookup"><span data-stu-id="c0a28-169">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="c0a28-170">許多設計人員發現，它們甚至可以更 believably 地整合全像投影，方法是在表面上建立「負陰影」。</span><span class="sxs-lookup"><span data-stu-id="c0a28-170">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="c0a28-171">若要這麼做，您可以在全像是建立全像影像，然後從發光減去「陰影」。</span><span class="sxs-lookup"><span data-stu-id="c0a28-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="c0a28-172">軟光暈會與真實世界的光線整合，並在環境中遮蔽影子。</span><span class="sxs-lookup"><span data-stu-id="c0a28-172">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="c0a28-173">全像影像</span><span class="sxs-lookup"><span data-stu-id="c0a28-173">A hologram is whatever</span></span> <br><span data-ttu-id="c0a28-174">您可以夢想</span><span class="sxs-lookup"><span data-stu-id="c0a28-174">you can dream up</span></span><br>
        <span data-ttu-id="c0a28-175">作為全像攝影的開發人員，您可以將您的創意從2D 畫面移至世界各地。</span><span class="sxs-lookup"><span data-stu-id="c0a28-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="c0a28-176">*您* 會建立什麼？</span><span class="sxs-lookup"><span data-stu-id="c0a28-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="c0a28-177">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="c0a28-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="c0a28-178">![客廳的全像虛構世界](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="c0a28-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="c0a28-179">下次探索檢查點</span><span class="sxs-lookup"><span data-stu-id="c0a28-179">Next Discovery Checkpoint</span></span>

<span data-ttu-id="c0a28-180">如果您正在關注我們所配置的 [探索旅程](get-started-with-mr.md) ，您將會在探索混合現實的基本概念。</span><span class="sxs-lookup"><span data-stu-id="c0a28-180">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="c0a28-181">您可以從這裡繼續進行下一個基本主題：</span><span class="sxs-lookup"><span data-stu-id="c0a28-181">From here, you can proceed to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="c0a28-182">工作的新願景</span><span class="sxs-lookup"><span data-stu-id="c0a28-182">A new vision for work</span></span>](https://dynamics.microsoft.com//mixed-reality/overview/)

<span data-ttu-id="c0a28-183">或跳至：</span><span class="sxs-lookup"><span data-stu-id="c0a28-183">Or jump to:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c0a28-184">追求更個人化的運算</span><span class="sxs-lookup"><span data-stu-id="c0a28-184">The pursuit of more personal computing</span></span>](../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md)

## <a name="see-also"></a><span data-ttu-id="c0a28-185">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0a28-185">See also</span></span>
* [<span data-ttu-id="c0a28-186">展開您的設計程序</span><span class="sxs-lookup"><span data-stu-id="c0a28-186">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)
* [<span data-ttu-id="c0a28-187">空間音效</span><span class="sxs-lookup"><span data-stu-id="c0a28-187">Spatial sound</span></span>](../design/spatial-sound.md)
* [<span data-ttu-id="c0a28-188">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="c0a28-188">Color, light and materials</span></span>](../color,-light-and-materials.md)
