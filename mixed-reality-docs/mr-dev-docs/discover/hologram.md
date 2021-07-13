---
title: 什麼是全像投影？
description: HoloLens 可讓您在世界各地出現于世界各地的立體和音效物件，並與之互動。
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、全像影像、設計、互動、混合現實耳機、Windows Mixed reality 耳機、什麼是增強的現實
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634329"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="10625-104">什麼是全像投影？</span><span class="sxs-lookup"><span data-stu-id="10625-104">What is a hologram?</span></span>

<span data-ttu-id="10625-105">HoloLens 可讓您查看全像 **影像**，也就是像真實物件一樣，在世界周圍出現的燈光和音效物件。</span><span class="sxs-lookup"><span data-stu-id="10625-105">HoloLens lets you view **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="10625-106">全像投影可以回應您的[注視](../design/gaze-and-commit.md)、[手勢](../design/gaze-and-commit.md#composite-gestures)和[語音命令](../design/voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="10625-106">Holograms can respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="10625-107">他們甚至可以與您的 [真實世界表面](../design/spatial-mapping.md) 互動。</span><span class="sxs-lookup"><span data-stu-id="10625-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="10625-108">全像投影是您世界中的數位物件。</span><span class="sxs-lookup"><span data-stu-id="10625-108">Holograms are digital objects that are part of your world.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a><span data-ttu-id="10625-109">裝置支援</span><span class="sxs-lookup"><span data-stu-id="10625-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="10625-110"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="10625-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="10625-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="10625-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="10625-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="10625-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="10625-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="10625-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="10625-114">全像投影</span><span class="sxs-lookup"><span data-stu-id="10625-114">Holograms</span></span></td>
        <td><span data-ttu-id="10625-115">✔️</span><span class="sxs-lookup"><span data-stu-id="10625-115">✔️</span></span></td>
        <td><span data-ttu-id="10625-116">✔️</span><span class="sxs-lookup"><span data-stu-id="10625-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="10625-117">全像是由燈光和音效組成</span><span class="sxs-lookup"><span data-stu-id="10625-117">A hologram is made of light and sound</span></span>

### <a name="light"></a><span data-ttu-id="10625-118">淺色</span><span class="sxs-lookup"><span data-stu-id="10625-118">Light</span></span>

<span data-ttu-id="10625-119">[HoloLens 轉譯](../develop/platform-capabilities-and-apis/rendering.md)的全像影像，會直接出現在使用者眼睛之前的全像攝影框架中。</span><span class="sxs-lookup"><span data-stu-id="10625-119">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of users' eyes.</span></span> <span data-ttu-id="10625-120">全像投影將燈光添加到您的世界，這表示您會看到顯示器的光線和周圍世界的光線。</span><span class="sxs-lookup"><span data-stu-id="10625-120">Holograms add light to your world, which means that you see both the light from the display and the light from your surrounding world.</span></span> <span data-ttu-id="10625-121">由於 HoloLens 使用加上燈光的加法顯示，因此黑色色彩將會呈現為透明的。</span><span class="sxs-lookup"><span data-stu-id="10625-121">Since HoloLens uses an additive display that adds light, the black color will be rendered transparent.</span></span> 

<span data-ttu-id="10625-122">全像投影可能會有非常不同的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="10625-122">Holograms can have very different appearances and behaviors.</span></span> <span data-ttu-id="10625-123">有些是真實且穩固的，有些則是編排卡通和 ethereal。</span><span class="sxs-lookup"><span data-stu-id="10625-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="10625-124">您可以使用全像投影來反白顯示環境中的功能，或使用它們做為應用程式使用者介面中的元素。</span><span class="sxs-lookup"><span data-stu-id="10625-124">You can use holograms to highlight features in your environment or use them as elements in your app's user interface.</span></span>

![操作全像手](images/hologram-hands-940px.jpg)

### <a name="sound"></a><span data-ttu-id="10625-126">音效</span><span class="sxs-lookup"><span data-stu-id="10625-126">Sound</span></span>

<span data-ttu-id="10625-127">全像投影也[可能產生音效，看起來似乎](../design/spatial-sound.md)來自您環境中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="10625-127">Holograms can also produce [sounds](../design/spatial-sound.md), which appear to come from a specific place in your environment.</span></span> <span data-ttu-id="10625-128">在 HoloLens 上，音效來自兩個位于您的耳上方的喇叭。</span><span class="sxs-lookup"><span data-stu-id="10625-128">On HoloLens, sound comes from two speakers that are located directly above your ears.</span></span> <span data-ttu-id="10625-129">與全像全像全像全像全像全像一樣，喇叭也是一種新的音效，而不會封鎖環境的音效。</span><span class="sxs-lookup"><span data-stu-id="10625-129">Same as the holographic displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="10625-130">您可以將全息圖放在世界或標記中</span><span class="sxs-lookup"><span data-stu-id="10625-130">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="10625-131">當您有固定的影像位置時，可以將它精確地 [放](../design/coordinate-systems.md) 在世界各地。</span><span class="sxs-lookup"><span data-stu-id="10625-131">When you have a fixed location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="10625-132">當您四處解說時，像是實體物件一樣，全像世界上的全像是世界上的全像是固定的。</span><span class="sxs-lookup"><span data-stu-id="10625-132">As you walk around, the hologram appears stationary based on the world around you, just like a physical object.</span></span> <span data-ttu-id="10625-133">如果您使用 [空間錨點](../design/coordinate-systems.md#spatial-anchors) 來釘選物件，則當您稍後返回時，系統甚至可以記得您離開該物件的位置。</span><span class="sxs-lookup"><span data-stu-id="10625-133">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![在零售空間中使用 Microsoft Dynamics 365 版面配置的兩個男性](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="10625-135">部分的全像是以使用者為依據。</span><span class="sxs-lookup"><span data-stu-id="10625-135">Some holograms follow the user instead.</span></span> <span data-ttu-id="10625-136">他們會根據使用者自行定位。</span><span class="sxs-lookup"><span data-stu-id="10625-136">They position themselves based on the user.</span></span> <span data-ttu-id="10625-137">您可以選擇帶給您的全像投影，然後將它放在牆上的另一個房間。</span><span class="sxs-lookup"><span data-stu-id="10625-137">You can choose to bring a hologram with you, and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="10625-138">**最佳作法**</span><span class="sxs-lookup"><span data-stu-id="10625-138">**Best practices**</span></span>

* <span data-ttu-id="10625-139">在某些案例中，您需要在整個體驗中輕鬆地探索或顯示全像影像。</span><span class="sxs-lookup"><span data-stu-id="10625-139">Some scenarios demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="10625-140">這種定位有兩種高階方法。</span><span class="sxs-lookup"><span data-stu-id="10625-140">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="10625-141">讓我們將其稱為「 **鎖定** 」和「內文 **鎖住**」。</span><span class="sxs-lookup"><span data-stu-id="10625-141">Let's call them **display-locked** and **body-locked**.</span></span>
   * <span data-ttu-id="10625-142">**顯示鎖定** 的內容已鎖定到顯示裝置。</span><span class="sxs-lookup"><span data-stu-id="10625-142">**Display-locked** content is locked to the display device.</span></span> <span data-ttu-id="10625-143">這種類型的內容很難處理，因為有許多原因，包括非自然的「clingyness」，讓許多使用者感到挫折，並且想要「搖動」。</span><span class="sxs-lookup"><span data-stu-id="10625-143">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="10625-144">一般情況下，設計人員發現更適合用來避免顯示鎖定的內容。</span><span class="sxs-lookup"><span data-stu-id="10625-144">In general, designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="10625-145">**主體鎖定** 內容可能更容許。</span><span class="sxs-lookup"><span data-stu-id="10625-145">**Body-locked** content can be far more forgiving.</span></span> <span data-ttu-id="10625-146">本文-鎖定是指您在3D 空間中 tether 使用者的內文或注視向量。</span><span class="sxs-lookup"><span data-stu-id="10625-146">Body-locking is when you tether a hologram to the user's body or gaze vector in 3D space.</span></span> <span data-ttu-id="10625-147">許多經驗都採用了內文鎖定行為，其中的全像是使用者的注視，可讓使用者旋轉其內文，並在空間中移動，而不會遺失全像影像。</span><span class="sxs-lookup"><span data-stu-id="10625-147">Many experiences have adopted a body-locking behavior where the hologram follows the user's gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="10625-148">合併延遲有助於讓全息圖的移動感覺更自然。</span><span class="sxs-lookup"><span data-stu-id="10625-148">Incorporating a delay helps the hologram movements to feel more natural.</span></span> <span data-ttu-id="10625-149">例如，Windows 全像全球版作業系統的一些核心 UI 會使用本文鎖定的變化，在使用者關閉時，在使用者的注視之後，會有一個非常類似的彈性延遲。</span><span class="sxs-lookup"><span data-stu-id="10625-149">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="10625-150">將全像觀賞距離的全像是大約是1-2 的計量離 head。</span><span class="sxs-lookup"><span data-stu-id="10625-150">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="10625-151">如果專案必須持續于全像全像框架，或在使用者變更其觀點時，考慮將您的內容移至顯示器的一端，則可讓元素漂移。</span><span class="sxs-lookup"><span data-stu-id="10625-151">Allow elements to drift if they must be continually in the holographic frame, or consider moving your content to one side of the display when the user changes their point of view.</span></span> <span data-ttu-id="10625-152">如需詳細資訊，請參閱 [billboarding 和標記-沿著](../design/billboarding-and-tag-along.md) artilce。</span><span class="sxs-lookup"><span data-stu-id="10625-152">For more information, see the [billboarding and tag-along](../design/billboarding-and-tag-along.md) artilce.</span></span>

<span data-ttu-id="10625-153">**將全像全區放在最理想的區域，介於 1.25 m 和 5 m 之間**</span><span class="sxs-lookup"><span data-stu-id="10625-153">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="10625-154">雙計量是最理想的觀賞距離。</span><span class="sxs-lookup"><span data-stu-id="10625-154">Two meters is the most optimal viewing distance.</span></span> <span data-ttu-id="10625-155">當您接近1個計量時，就會開始降低體驗。</span><span class="sxs-lookup"><span data-stu-id="10625-155">The experience will start to degrade as you get closer than 1 meter.</span></span> <span data-ttu-id="10625-156">在距離小於1的度量時，定期移至深度的全像投影，會比固定的全像投影更有問題。</span><span class="sxs-lookup"><span data-stu-id="10625-156">At distances less than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="10625-157">當內容太近時，請考慮以適當的方式裁剪或漸離您的內容，因此您不會將使用者帶到不愉快的觀賞體驗。</span><span class="sxs-lookup"><span data-stu-id="10625-157">Consider gracefully clipping or fading out your content when it gets too close, so you don't jar the user into an unpleasant viewing experience.</span></span>

![從使用者處放置全像影像的最佳距離。](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="10625-159">與您和您的世界互動的全像影像</span><span class="sxs-lookup"><span data-stu-id="10625-159">A hologram interacts with you and your world</span></span>

<span data-ttu-id="10625-160">全像投影不僅適用于燈光和音效;它們也是您世界上的有效部分。</span><span class="sxs-lookup"><span data-stu-id="10625-160">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="10625-161">以您手中的手中看看您的手中的手，然後您就可以開始使用全像投影。</span><span class="sxs-lookup"><span data-stu-id="10625-161">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="10625-162">提供語音命令，並可回復全像影像。</span><span class="sxs-lookup"><span data-stu-id="10625-162">Give a voice command, and the hologram can reply.</span></span>

![使用 Microsoft HoloLens 2 在伺服器陣列開發專案上共同作業的政府公用程式工作者群組](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="10625-164">全像投影啟用無法在其他地方使用的個人互動。</span><span class="sxs-lookup"><span data-stu-id="10625-164">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="10625-165">因為 HoloLens 知道世界的位置，所以全像攝影的字元可以直接查看您的眼睛，並開始與您交談。</span><span class="sxs-lookup"><span data-stu-id="10625-165">Because the HoloLens knows where it is in the world, a holographic character can look at you directly in the eyes and start a conversation with you.</span></span>

<span data-ttu-id="10625-166">全息圖也可以與您的環境互動。</span><span class="sxs-lookup"><span data-stu-id="10625-166">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="10625-167">例如，您可以將全息的彈跳球放在資料表上方。</span><span class="sxs-lookup"><span data-stu-id="10625-167">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="10625-168">然後，利用點 [一下，觀賞](../design/gaze-and-commit.md#composite-gestures)球的彈跳，並在叫用資料表時，讓聲音變成音效。</span><span class="sxs-lookup"><span data-stu-id="10625-168">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound as it hits the table.</span></span>

<span data-ttu-id="10625-169">您也可以 pixels occluded 真實世界物件的全像投影。</span><span class="sxs-lookup"><span data-stu-id="10625-169">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="10625-170">例如，全像攝影的字元可能會讓您看不到幕後的大門。</span><span class="sxs-lookup"><span data-stu-id="10625-170">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="10625-171">**用於整合全像全球和真實世界的提示**</span><span class="sxs-lookup"><span data-stu-id="10625-171">**Tips for integrating holograms and the real world**</span></span>

* <span data-ttu-id="10625-172">對齊 gravitational 規則可讓您更輕鬆地與可信相關的影像。</span><span class="sxs-lookup"><span data-stu-id="10625-172">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="10625-173">例如：將全像狗放在地面上 & 花瓶在資料表上，而不是讓它們浮在空間中。</span><span class="sxs-lookup"><span data-stu-id="10625-173">For example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="10625-174">許多設計人員發現，他們可以藉由在桌上的表面上建立「負陰影」來整合更可信的全像投影。</span><span class="sxs-lookup"><span data-stu-id="10625-174">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="10625-175">若要這麼做，您可以在全像是建立全像影像，然後從發光減去「陰影」。</span><span class="sxs-lookup"><span data-stu-id="10625-175">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="10625-176">軟光暈與真實世界的光線整合。</span><span class="sxs-lookup"><span data-stu-id="10625-176">The soft glow integrates with the light from the real world.</span></span> <span data-ttu-id="10625-177">陰影是用來在環境中地面全像影像。</span><span class="sxs-lookup"><span data-stu-id="10625-177">The shadow is used to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a><span data-ttu-id="10625-178">全像影像</span><span class="sxs-lookup"><span data-stu-id="10625-178">A hologram is what</span></span> <br><span data-ttu-id="10625-179">您可以夢想</span><span class="sxs-lookup"><span data-stu-id="10625-179">you can dream up</span></span><br>
        <span data-ttu-id="10625-180">作為全像攝影的開發人員，您可以將您的創意從2D 畫面移至世界各地。</span><span class="sxs-lookup"><span data-stu-id="10625-180">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="10625-181">*您* 會建立什麼？</span><span class="sxs-lookup"><span data-stu-id="10625-181">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="10625-182">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="10625-182">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="10625-183">![客廳的全像虛構世界](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="10625-183">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="10625-184">下一個探索檢查點</span><span class="sxs-lookup"><span data-stu-id="10625-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="10625-185">您正在研究我們所配置的 [探索旅程](get-started-with-mr.md) ，並探索混合現實的基本概念。</span><span class="sxs-lookup"><span data-stu-id="10625-185">You're on the [discovery journey](get-started-with-mr.md) we've laid out, and exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="10625-186">您可以從這裡繼續進行下一個基本主題：</span><span class="sxs-lookup"><span data-stu-id="10625-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="10625-187">展開您的設計程序</span><span class="sxs-lookup"><span data-stu-id="10625-187">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)