---
title: 資料指標
description: 目標向量的游標或指標，可為使用者提供持續的意見反應，以瞭解 HoloLens 對其意圖的瞭解程度。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (第1代) 、HoloLens 2、混合的現實、資料指標、目標、注視、手勢
ms.openlocfilehash: 6fb5f335e192ce7664eab0099dc5d6aa6ed2420d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680477"
---
# <a name="cursors"></a><span data-ttu-id="dd237-104">資料指標</span><span class="sxs-lookup"><span data-stu-id="dd237-104">Cursors</span></span>

![資料指標](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="dd237-106">指標或您目前目標向量的指標，可為使用者提供持續的意見反應，以瞭解耳機認為目前焦點在當時的位置。</span><span class="sxs-lookup"><span data-stu-id="dd237-106">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="dd237-107">資料指標可讓使用者瞭解其目前的目標點，並做為意見反應來指出哪些區域、全息圖或點將會回應輸入。</span><span class="sxs-lookup"><span data-stu-id="dd237-107">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="dd237-108">它是裝置瞭解使用者注意 (的數位標記法，但這可能不是決定其意圖) 的任何事物。</span><span class="sxs-lookup"><span data-stu-id="dd237-108">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="dd237-109">資料指標提供的意見反應可讓使用者預測系統的回應方式、使用該信號作為意見反應，以便更妥善地傳達裝置的意圖，並對其互動提供更自信的能力。</span><span class="sxs-lookup"><span data-stu-id="dd237-109">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="dd237-110">有3種資料指標： **手指、光線** 和 **頭部** 。</span><span class="sxs-lookup"><span data-stu-id="dd237-110">There are 3 kinds of cursors: **finger, ray** , and **head-gaze** .</span></span> <span data-ttu-id="dd237-111">這些指標資料指標在 HoloLens、HoloLens 2 和沉浸式耳機上，使用不同的輸入形式。</span><span class="sxs-lookup"><span data-stu-id="dd237-111">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="dd237-112">以下是要針對每種類型的耳機和互動模型使用哪一種資料指標類型的指引。</span><span class="sxs-lookup"><span data-stu-id="dd237-112">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="dd237-113">在 (MRTK) 的混合現實工具組中，我們建立了拖放資料指標模組，以協助您建立正確的指標體驗。</span><span class="sxs-lookup"><span data-stu-id="dd237-113">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="dd237-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="dd237-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dd237-115"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="dd237-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="dd237-116"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="dd237-116"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="dd237-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="dd237-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="dd237-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="dd237-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="dd237-119">手指游標</span><span class="sxs-lookup"><span data-stu-id="dd237-119">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="dd237-120">✔️</span><span class="sxs-lookup"><span data-stu-id="dd237-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="dd237-121">光線游標</span><span class="sxs-lookup"><span data-stu-id="dd237-121">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="dd237-122">✔️</span><span class="sxs-lookup"><span data-stu-id="dd237-122">✔️</span></span></td>
        <td><span data-ttu-id="dd237-123">✔️</span><span class="sxs-lookup"><span data-stu-id="dd237-123">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dd237-124">頭部指標</span><span class="sxs-lookup"><span data-stu-id="dd237-124">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="dd237-125">✔️</span><span class="sxs-lookup"><span data-stu-id="dd237-125">✔️</span></span></td>
        <td><span data-ttu-id="dd237-126">✔️</span><span class="sxs-lookup"><span data-stu-id="dd237-126">✔️</span></span></td>
        <td><span data-ttu-id="dd237-127">✔️</span><span class="sxs-lookup"><span data-stu-id="dd237-127">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="dd237-128">手指游標</span><span class="sxs-lookup"><span data-stu-id="dd237-128">Finger cursor</span></span>
<span data-ttu-id="dd237-129">手指游標僅適用于 HoloLens 2，以增強「[直接操作](direct-manipulation.md)」互動模式。</span><span class="sxs-lookup"><span data-stu-id="dd237-129">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="dd237-130">為了更清楚地瞭解手指指向的位置，我們已將環形連接至兩個索引手指的秘訣。</span><span class="sxs-lookup"><span data-stu-id="dd237-130">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="dd237-131">環形大小是根據手指與 UI 介面附近的距離 (越靠近手指，環形) 越小，就會在手指與 UI 聯繫時縮小為點形。</span><span class="sxs-lookup"><span data-stu-id="dd237-131">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="dd237-132">![手指游標](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="dd237-132">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="dd237-133">**手指游標1的視覺意見反應狀態** ：環形會縮小為點。</span><span class="sxs-lookup"><span data-stu-id="dd237-133">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="dd237-134">2：環形與 surface 對齊。</span><span class="sxs-lookup"><span data-stu-id="dd237-134">2: The ring aligns with surface.</span></span> <span data-ttu-id="dd237-135">3：環形與手指向量垂直。</span><span class="sxs-lookup"><span data-stu-id="dd237-135">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="dd237-136">4：無環形。</span><span class="sxs-lookup"><span data-stu-id="dd237-136">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="dd237-137">光線游標</span><span class="sxs-lookup"><span data-stu-id="dd237-137">Ray cursor</span></span>
<span data-ttu-id="dd237-138">光線指標會附加至最接近的光線，以允許操作不在手中的物件。</span><span class="sxs-lookup"><span data-stu-id="dd237-138">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="dd237-139">在沉浸式耳機中，光線會從運動控制器和以點指標結束。</span><span class="sxs-lookup"><span data-stu-id="dd237-139">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="dd237-140">在 HoloLens 2 中，我們會利用這些移動控制器光線的精神模型，以及源自手掌和 end in 環形指標，且與直接操作中使用的手指指標一致的光線。</span><span class="sxs-lookup"><span data-stu-id="dd237-140">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="dd237-141">![光線游標控制器](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="dd237-141">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="dd237-142">**移動控制器的光線指標**</span><span class="sxs-lookup"><span data-stu-id="dd237-142">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="dd237-143">![光線游標手](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="dd237-143">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="dd237-144">**手中的光線游標**</span><span class="sxs-lookup"><span data-stu-id="dd237-144">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="dd237-145">頭部指標</span><span class="sxs-lookup"><span data-stu-id="dd237-145">Head-gaze cursor</span></span>
<span data-ttu-id="dd237-146">前端指標是一個點，它會附加至不可見的標頭看式向量的結尾，該向量會使用標頭的位置和旋轉來指向點。</span><span class="sxs-lookup"><span data-stu-id="dd237-146">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="dd237-147">若要執行動作，此指標會與各種認可輸入配對，例如點擊點、語音命令、停留，然後按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="dd237-147">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="dd237-148">在 HoloLens 2 中，列印頭最適合與任何不是按下的認可輸入配對，因為在攻點與遠光線之間會有互動衝突。</span><span class="sxs-lookup"><span data-stu-id="dd237-148">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="dd237-149">![頭部注視游標手](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="dd237-149">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="dd237-150">**具有手形手勢的列印頭指標**</span><span class="sxs-lookup"><span data-stu-id="dd237-150">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="dd237-151">![頭部注視游標聲音](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="dd237-151">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="dd237-152">**使用 voice 命令的標頭指標**</span><span class="sxs-lookup"><span data-stu-id="dd237-152">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="dd237-153">資料指標自訂建議</span><span class="sxs-lookup"><span data-stu-id="dd237-153">Cursor customization recommendations</span></span>
<span data-ttu-id="dd237-154">如果您想要自訂資料指標的意見反應行為和外觀，以下是一些設計建議：</span><span class="sxs-lookup"><span data-stu-id="dd237-154">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="dd237-155">資料指標調整</span><span class="sxs-lookup"><span data-stu-id="dd237-155">Cursor scale</span></span>
* <span data-ttu-id="dd237-156">資料指標不應大於可用的目標，讓使用者可以輕鬆地與內容互動並加以查看。</span><span class="sxs-lookup"><span data-stu-id="dd237-156">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="dd237-157">根據您所建立的體驗，以使用者的外觀調整資料指標也是很重要的考慮。</span><span class="sxs-lookup"><span data-stu-id="dd237-157">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="dd237-158">例如，當使用者進一步探討您的體驗時，資料指標應該不會變得太小，所以會遺失。</span><span class="sxs-lookup"><span data-stu-id="dd237-158">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="dd237-159">調整游標時，請考慮將軟動畫套用至其調整規模，以提供一種隨機的感覺。</span><span class="sxs-lookup"><span data-stu-id="dd237-159">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="dd237-160">避免阻礙內容。</span><span class="sxs-lookup"><span data-stu-id="dd237-160">Avoid obstructing content.</span></span> <span data-ttu-id="dd237-161">全像全像是讓體驗更清楚，而且資料指標不應該離開。</span><span class="sxs-lookup"><span data-stu-id="dd237-161">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="dd237-162">Directionless 資料指標圖形</span><span class="sxs-lookup"><span data-stu-id="dd237-162">Directionless cursor shape</span></span>
* <span data-ttu-id="dd237-163">雖然沒有一個右資料指標圖形，但我們建議您使用 directionless 圖形，例如圓環形。</span><span class="sxs-lookup"><span data-stu-id="dd237-163">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="dd237-164">指向某個方向的游標 (例如，傳統的箭號游標) 可能會讓使用者混淆，使其一律看起來如此。</span><span class="sxs-lookup"><span data-stu-id="dd237-164">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="dd237-165">例外狀況是使用資料指標，將互動指令傳達給使用者。</span><span class="sxs-lookup"><span data-stu-id="dd237-165">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="dd237-166">例如，在混合現實作業系統中調整全像投影時，游標會暫時包含箭號，指示使用者如何移動其手以調整全像。</span><span class="sxs-lookup"><span data-stu-id="dd237-166">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="dd237-167">外觀與風格</span><span class="sxs-lookup"><span data-stu-id="dd237-167">Look and feel</span></span>
* <span data-ttu-id="dd237-168">環圈圖或環圈圖資料指標適用于許多應用程式。</span><span class="sxs-lookup"><span data-stu-id="dd237-168">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="dd237-169">挑選最能代表您所建立之體驗的色彩和圖形。</span><span class="sxs-lookup"><span data-stu-id="dd237-169">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="dd237-170">資料指標特別容易用來 [區分色彩](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)。</span><span class="sxs-lookup"><span data-stu-id="dd237-170">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="dd237-171">具有對稱不透明度的小型資料指標可保持資訊的資訊，而不需要支配視覺化階層。</span><span class="sxs-lookup"><span data-stu-id="dd237-171">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="dd237-172">請 cognizant 在游標後方使用陰影或反白顯示，因為它們可能會對內容和手中工作的注意力。</span><span class="sxs-lookup"><span data-stu-id="dd237-172">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="dd237-173">資料指標應該符合並將您應用程式中的表面分配給使用者，這可讓使用者感覺到系統可以看到他們在哪裡尋找，但系統也知道他們的環境。</span><span class="sxs-lookup"><span data-stu-id="dd237-173">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="dd237-174">例如，在混合現實 OS 中，資料指標會與使用者世界的表面保持一致，即使在使用者不直接查看全像的情況下，也能感受到世界的認知。</span><span class="sxs-lookup"><span data-stu-id="dd237-174">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="dd237-175">以磁性方式鎖定游標至接近近距離的互動式元素，可協助改善使用者在執行選取動作時與該專案互動的信心。</span><span class="sxs-lookup"><span data-stu-id="dd237-175">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="dd237-176">視覺提示</span><span class="sxs-lookup"><span data-stu-id="dd237-176">Visual cues</span></span>
* <span data-ttu-id="dd237-177">如果您的經驗著重于單一的全像投影，則當您離開該全像投影時，您的游標應該只靠全像是的全像成形和變化圖形。</span><span class="sxs-lookup"><span data-stu-id="dd237-177">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="dd237-178">這可以向使用者傳達可操作的全像影像，而且可以與其互動。</span><span class="sxs-lookup"><span data-stu-id="dd237-178">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="dd237-179">如果您的應用程式使用空間對應，則您的資料指標可能會對齊，並在它看到的每個介面上。</span><span class="sxs-lookup"><span data-stu-id="dd237-179">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="dd237-180">這會對 HoloLens 和您的應用程式可看到其空間的使用者提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="dd237-180">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="dd237-181">這可以強調全像是真實的全球化，並協助您填補真實與虛擬之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="dd237-181">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="dd237-182">瞭解當視野中沒有任何全息圖或表面時，游標應怎麼做。</span><span class="sxs-lookup"><span data-stu-id="dd237-182">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="dd237-183">將它放在使用者前方預先決定的距離就是其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="dd237-183">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="dd237-184">可能的動作</span><span class="sxs-lookup"><span data-stu-id="dd237-184">Possible actions</span></span>
* <span data-ttu-id="dd237-185">您可以使用不同的圖示來表示資料指標，以傳達可執行全息圖的可能動作，例如縮放或旋轉。</span><span class="sxs-lookup"><span data-stu-id="dd237-185">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="dd237-186">如果對使用者而言，只會在資料指標上加入額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="dd237-186">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="dd237-187">否則，使用者可能不會注意到狀態變更或資料指標混淆。</span><span class="sxs-lookup"><span data-stu-id="dd237-187">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="dd237-188">輸入狀態</span><span class="sxs-lookup"><span data-stu-id="dd237-188">Input state</span></span>
* <span data-ttu-id="dd237-189">我們可以使用游標來顯示使用者的輸入狀態或意圖。</span><span class="sxs-lookup"><span data-stu-id="dd237-189">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="dd237-190">例如，我們可以顯示一個圖示，告訴使用者系統看到其手上的狀態，而應用程式知道他們已經準備好採取行動。</span><span class="sxs-lookup"><span data-stu-id="dd237-190">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="dd237-191">我們也可以使用資料指標，向使用者顯示系統透過暫時色彩聽取聲音命令的使用者 chang</span><span class="sxs-lookup"><span data-stu-id="dd237-191">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="dd237-192">下列資料指標狀態可以用不同的方式來執行。</span><span class="sxs-lookup"><span data-stu-id="dd237-192">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="dd237-193">您可以藉由建立資料指標模型（例如狀態機器）來執行這些不同的狀態。</span><span class="sxs-lookup"><span data-stu-id="dd237-193">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="dd237-194">例如：</span><span class="sxs-lookup"><span data-stu-id="dd237-194">For example:</span></span>
    * <span data-ttu-id="dd237-195">閒置狀態是您顯示預設資料指標的位置。</span><span class="sxs-lookup"><span data-stu-id="dd237-195">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="dd237-196">[就緒] 狀態是當您在 [就緒] 位置偵測到使用者的手時。</span><span class="sxs-lookup"><span data-stu-id="dd237-196">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="dd237-197">互動狀態是使用者執行特定互動的時間。</span><span class="sxs-lookup"><span data-stu-id="dd237-197">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="dd237-198">可能的動作狀態或暫留狀態是當您傳達可在全像影像上執行的可能動作。</span><span class="sxs-lookup"><span data-stu-id="dd237-198">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="dd237-199">您也可以使用面板來實作為這些狀態，讓您可以在偵測到不同狀態時顯示不同的藝術資產。</span><span class="sxs-lookup"><span data-stu-id="dd237-199">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="dd237-200">進入「無資料指標」</span><span class="sxs-lookup"><span data-stu-id="dd237-200">Going "cursor-free"</span></span>
<span data-ttu-id="dd237-201">當深度的意義是體驗的重要元件，以及透過注視和手勢來指向互動 (時，建議您不要使用資料指標進行設計，) 不需要絕佳的精確度。</span><span class="sxs-lookup"><span data-stu-id="dd237-201">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="dd237-202">系統仍然必須符合資料指標通常符合的需求，方法是為使用者提供持續的意見反應，以瞭解系統對其指標的理解，並協助他們安心地與系統溝通其意圖。</span><span class="sxs-lookup"><span data-stu-id="dd237-202">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="dd237-203">這可以透過其他明顯的狀態變更來達成。</span><span class="sxs-lookup"><span data-stu-id="dd237-203">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="dd237-204">適用于 Unity 的 MRTK (混合現實工具組) 的游標</span><span class="sxs-lookup"><span data-stu-id="dd237-204">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="dd237-205">根據預設， [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) 會提供資料指標預製專案 ([DefaultCursor. 預製專案](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) 與 shell 的系統資料指標具有相同的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="dd237-205">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="dd237-206">它是在 MRTK 輸入設定檔的 [指標] 下進行指派。</span><span class="sxs-lookup"><span data-stu-id="dd237-206">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="dd237-207">您可以針對您的體驗取代/自訂此資料指標。</span><span class="sxs-lookup"><span data-stu-id="dd237-207">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="dd237-208">針對眼睛追蹤輸入的體驗，MRTK 也提供 EyeGazeCursor，其中具有微妙的視覺效果可將干擾降至最低。</span><span class="sxs-lookup"><span data-stu-id="dd237-208">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="dd237-209">MRTK - 指標設定檔</span><span class="sxs-lookup"><span data-stu-id="dd237-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="dd237-210">MRTK - 輸入系統</span><span class="sxs-lookup"><span data-stu-id="dd237-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="dd237-211">MRTK - 指標</span><span class="sxs-lookup"><span data-stu-id="dd237-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="dd237-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd237-212">See also</span></span>
* [<span data-ttu-id="dd237-213">軌跡</span><span class="sxs-lookup"><span data-stu-id="dd237-213">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="dd237-214">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="dd237-214">Head-gaze and commit</span></span>](gaze-and-commit.md)
