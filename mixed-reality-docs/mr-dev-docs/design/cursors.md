---
title: 資料指標
description: 目標向量的游標或指標，可為使用者提供持續的意見反應，以瞭解 HoloLens 對其意圖的瞭解程度。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (第1代) 、HoloLens 2、混合的現實、游標、目標、注視、手勢、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、放射片、輸入
ms.openlocfilehash: 744e75f4212046b7c237a6c6634a4980e9148b0e
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300083"
---
# <a name="cursors"></a><span data-ttu-id="9ad12-104">資料指標</span><span class="sxs-lookup"><span data-stu-id="9ad12-104">Cursors</span></span>

![資料指標](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="9ad12-106">資料指標會根據耳機認為使用者的最新焦點是在指定時間，提供持續的意見反應。</span><span class="sxs-lookup"><span data-stu-id="9ad12-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="9ad12-107">資料指標意見反應包括虛擬環境中的哪個區域、全息圖或點會回應輸入。</span><span class="sxs-lookup"><span data-stu-id="9ad12-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="9ad12-108">即使游標是裝置瞭解使用者注意的數位標記法，但這並不是判斷使用者的意圖。</span><span class="sxs-lookup"><span data-stu-id="9ad12-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="9ad12-109">資料指標意見反應也可讓使用者知道預期的系統回應。</span><span class="sxs-lookup"><span data-stu-id="9ad12-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="9ad12-110">您可以使用意見反應，將其意圖傳達給裝置，從而提高使用者的信心。</span><span class="sxs-lookup"><span data-stu-id="9ad12-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="9ad12-111">有3種資料指標： **手指、光線** 和 **頭部**。</span><span class="sxs-lookup"><span data-stu-id="9ad12-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="9ad12-112">這些指標資料指標在 HoloLens、HoloLens 2 和沉浸式耳機上，使用不同的輸入形式。</span><span class="sxs-lookup"><span data-stu-id="9ad12-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="9ad12-113">以下是要針對每種類型的耳機和互動模型使用哪一種資料指標類型的指引。</span><span class="sxs-lookup"><span data-stu-id="9ad12-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="9ad12-114">在 (MRTK) 的混合現實工具組中，我們建立了拖放資料指標模組，以協助您建立正確的指標體驗。</span><span class="sxs-lookup"><span data-stu-id="9ad12-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="9ad12-115">裝置支援</span><span class="sxs-lookup"><span data-stu-id="9ad12-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9ad12-116"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="9ad12-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="9ad12-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="9ad12-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="9ad12-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="9ad12-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="9ad12-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="9ad12-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9ad12-120">手指游標</span><span class="sxs-lookup"><span data-stu-id="9ad12-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="9ad12-121">✔️</span><span class="sxs-lookup"><span data-stu-id="9ad12-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="9ad12-122">光線游標</span><span class="sxs-lookup"><span data-stu-id="9ad12-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="9ad12-123">✔️</span><span class="sxs-lookup"><span data-stu-id="9ad12-123">✔️</span></span></td>
        <td><span data-ttu-id="9ad12-124">✔️</span><span class="sxs-lookup"><span data-stu-id="9ad12-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9ad12-125">頭部指標</span><span class="sxs-lookup"><span data-stu-id="9ad12-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="9ad12-126">✔️</span><span class="sxs-lookup"><span data-stu-id="9ad12-126">✔️</span></span></td>
        <td><span data-ttu-id="9ad12-127">✔️</span><span class="sxs-lookup"><span data-stu-id="9ad12-127">✔️</span></span></td>
        <td><span data-ttu-id="9ad12-128">✔️</span><span class="sxs-lookup"><span data-stu-id="9ad12-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="9ad12-129">手指游標</span><span class="sxs-lookup"><span data-stu-id="9ad12-129">Finger cursor</span></span>

<span data-ttu-id="9ad12-130">手指游標只能在 HoloLens 2 上使用，以增強「[直接操作](direct-manipulation.md)」互動模式。</span><span class="sxs-lookup"><span data-stu-id="9ad12-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="9ad12-131">我們已將環形連接至兩個索引手指的秘訣，以更清楚地瞭解手指指向的位置。</span><span class="sxs-lookup"><span data-stu-id="9ad12-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="9ad12-132">環形大小是以指向 UI 介面的手指近距離為基礎，這會在手指觸及 UI 時縮小為小點。</span><span class="sxs-lookup"><span data-stu-id="9ad12-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="9ad12-133">手指越接近，環形就越小。</span><span class="sxs-lookup"><span data-stu-id="9ad12-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="9ad12-134">![手指游標](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="9ad12-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="9ad12-135">**手指游標1的視覺意見反應狀態** ：環形會縮小為點。</span><span class="sxs-lookup"><span data-stu-id="9ad12-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="9ad12-136">2：環形與 surface 對齊。</span><span class="sxs-lookup"><span data-stu-id="9ad12-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="9ad12-137">3：環形與手指向量垂直。</span><span class="sxs-lookup"><span data-stu-id="9ad12-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="9ad12-138">4：無環形。</span><span class="sxs-lookup"><span data-stu-id="9ad12-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="9ad12-139">光線游標</span><span class="sxs-lookup"><span data-stu-id="9ad12-139">Ray cursor</span></span>

<span data-ttu-id="9ad12-140">光線指標會附加至最接近的光線，以允許操作不在手中的物件。</span><span class="sxs-lookup"><span data-stu-id="9ad12-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="9ad12-141">在沉浸式耳機中，光線會從運動控制器和以點指標結束。</span><span class="sxs-lookup"><span data-stu-id="9ad12-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="9ad12-142">在 HoloLens 2 中，我們會套用這些移動控制器光線的精神模型，以及源自手掌和結尾的環形指標，而這些指標與直接操作中使用的手指指標一致。</span><span class="sxs-lookup"><span data-stu-id="9ad12-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="9ad12-143">![光線游標控制器](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="9ad12-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="9ad12-144">**移動控制器的光線指標**</span><span class="sxs-lookup"><span data-stu-id="9ad12-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9ad12-145">![光線游標手](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="9ad12-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="9ad12-146">**手中的光線游標**</span><span class="sxs-lookup"><span data-stu-id="9ad12-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="9ad12-147">頭部指標</span><span class="sxs-lookup"><span data-stu-id="9ad12-147">Head-gaze cursor</span></span>

<span data-ttu-id="9ad12-148">前端指標是一個點，它會附加至不可見的標頭看式向量的結尾，該向量會使用標頭的位置和旋轉來指向點。</span><span class="sxs-lookup"><span data-stu-id="9ad12-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="9ad12-149">若要執行動作，此指標會與各種認可輸入配對，例如點擊點、語音命令、停留，然後按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="9ad12-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="9ad12-150">在 HoloLens 2 中，列印頭最適合與任何未按下的認可輸入配對，因為在攻點與遠光線之間會有互動衝突。</span><span class="sxs-lookup"><span data-stu-id="9ad12-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="9ad12-151">![頭部注視游標手](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="9ad12-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="9ad12-152">**具有手形手勢的列印頭指標**</span><span class="sxs-lookup"><span data-stu-id="9ad12-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9ad12-153">![頭部注視游標聲音](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="9ad12-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="9ad12-154">**使用 voice 命令的標頭指標**</span><span class="sxs-lookup"><span data-stu-id="9ad12-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="9ad12-155">資料指標自訂建議</span><span class="sxs-lookup"><span data-stu-id="9ad12-155">Cursor customization recommendations</span></span>

<span data-ttu-id="9ad12-156">如果您想要自訂資料指標的意見反應行為和外觀，以下是一些設計建議：</span><span class="sxs-lookup"><span data-stu-id="9ad12-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="9ad12-157">資料指標調整</span><span class="sxs-lookup"><span data-stu-id="9ad12-157">Cursor scale</span></span>

* <span data-ttu-id="9ad12-158">資料指標不應大於可用的目標，讓使用者可以輕鬆地與內容互動並加以查看。</span><span class="sxs-lookup"><span data-stu-id="9ad12-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="9ad12-159">根據您所建立的體驗，以使用者的外觀調整資料指標也是很重要的考慮。</span><span class="sxs-lookup"><span data-stu-id="9ad12-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="9ad12-160">例如，當使用者進一步探討您的體驗時，資料指標應該會變得太小而無法遺失。</span><span class="sxs-lookup"><span data-stu-id="9ad12-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="9ad12-161">調整游標時，請考慮將軟動畫套用至其調整規模，以提供一種隨機的感覺。</span><span class="sxs-lookup"><span data-stu-id="9ad12-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="9ad12-162">避免阻礙內容。</span><span class="sxs-lookup"><span data-stu-id="9ad12-162">Avoid obstructing content.</span></span> <span data-ttu-id="9ad12-163">全像全像是讓體驗更清楚，而且資料指標不應該遠離它們。</span><span class="sxs-lookup"><span data-stu-id="9ad12-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="9ad12-164">Directionless 資料指標圖形</span><span class="sxs-lookup"><span data-stu-id="9ad12-164">Directionless cursor shape</span></span>

* <span data-ttu-id="9ad12-165">雖然沒有一個右資料指標圖形，但我們建議您使用 directionless 圖形，例如圓環形。</span><span class="sxs-lookup"><span data-stu-id="9ad12-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="9ad12-166">指向某個方向的游標 (例如，傳統的箭號游標) 可能會讓使用者混淆，使其一律看起來如此。</span><span class="sxs-lookup"><span data-stu-id="9ad12-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="9ad12-167">例外狀況是使用資料指標，將互動指令傳達給使用者。</span><span class="sxs-lookup"><span data-stu-id="9ad12-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="9ad12-168">例如，在混合現實作業系統中調整全像投影時，游標會暫時包含箭號，指示使用者如何移動其手以調整全像。</span><span class="sxs-lookup"><span data-stu-id="9ad12-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="9ad12-169">外觀與風格</span><span class="sxs-lookup"><span data-stu-id="9ad12-169">Look and feel</span></span>

* <span data-ttu-id="9ad12-170">環圈圖或環圈圖的游標適用于許多應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ad12-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="9ad12-171">挑選最能代表您正在建立之體驗的色彩和圖形。</span><span class="sxs-lookup"><span data-stu-id="9ad12-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="9ad12-172">資料指標特別容易用來 [區分色彩](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)。</span><span class="sxs-lookup"><span data-stu-id="9ad12-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="9ad12-173">具有對稱不透明度的小型資料指標可保持資訊的資訊，而不需要支配視覺化階層。</span><span class="sxs-lookup"><span data-stu-id="9ad12-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="9ad12-174">請 cognizant 在游標後方使用陰影或反白顯示，因為它們可能會對內容和手中工作的注意力。</span><span class="sxs-lookup"><span data-stu-id="9ad12-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="9ad12-175">資料指標應對齊並在您的應用程式中將這些表面上建。</span><span class="sxs-lookup"><span data-stu-id="9ad12-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="9ad12-176">使用者會覺得系統可以看到他們在哪裡尋找，但系統也知道他們的環境。</span><span class="sxs-lookup"><span data-stu-id="9ad12-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="9ad12-177">例如，混合現實作業系統中的資料指標會與使用者世界的表面一致，即使使用者未直接查看全像，也可以感覺到世界的認知。</span><span class="sxs-lookup"><span data-stu-id="9ad12-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="9ad12-178">當資料指標接近使用者時，以磁性方式鎖定游標至互動專案有助於提高使用者在使用選取動作時與該元素互動的信心。</span><span class="sxs-lookup"><span data-stu-id="9ad12-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="9ad12-179">視覺提示</span><span class="sxs-lookup"><span data-stu-id="9ad12-179">Visual cues</span></span>

* <span data-ttu-id="9ad12-180">如果您的經驗著重于單一的全像投影，則當您離開該全像投影時，您的游標應該只靠全像是的全像成形和變化圖形。</span><span class="sxs-lookup"><span data-stu-id="9ad12-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="9ad12-181">這可以向使用者傳達可操作的全像影像，而且可以與其互動。</span><span class="sxs-lookup"><span data-stu-id="9ad12-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="9ad12-182">如果您的應用程式使用空間對應，則您的資料指標可能會對齊，並在它看到的每個介面上。</span><span class="sxs-lookup"><span data-stu-id="9ad12-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="9ad12-183">這會對 HoloLens 和您的應用程式可看到其空間的使用者提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="9ad12-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="9ad12-184">這可以強調全像是真實的全球化，並協助您填補真實與虛擬之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="9ad12-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="9ad12-185">瞭解當視野中沒有任何全息圖或表面時，游標應怎麼做。</span><span class="sxs-lookup"><span data-stu-id="9ad12-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="9ad12-186">將它放在使用者前方預先決定的距離就是其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="9ad12-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="9ad12-187">可能的動作</span><span class="sxs-lookup"><span data-stu-id="9ad12-187">Possible actions</span></span>

* <span data-ttu-id="9ad12-188">您可以使用不同的圖示來表示資料指標，以傳達全息圖可執行檔可能動作，例如縮放或旋轉。</span><span class="sxs-lookup"><span data-stu-id="9ad12-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="9ad12-189">如果對使用者而言，只會在資料指標上加入額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="9ad12-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="9ad12-190">否則，使用者可能不會注意到狀態變更或資料指標混淆。</span><span class="sxs-lookup"><span data-stu-id="9ad12-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="9ad12-191">輸入狀態</span><span class="sxs-lookup"><span data-stu-id="9ad12-191">Input state</span></span>

* <span data-ttu-id="9ad12-192">我們可以使用游標來顯示使用者的輸入狀態或意圖。</span><span class="sxs-lookup"><span data-stu-id="9ad12-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="9ad12-193">例如，我們可以顯示一個圖示，告訴使用者系統看到其手上的狀態，而應用程式知道他們已經準備好採取行動。</span><span class="sxs-lookup"><span data-stu-id="9ad12-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="9ad12-194">我們也可以使用資料指標來顯示使用者透過暫時的色彩變更聽到的聲音命令</span><span class="sxs-lookup"><span data-stu-id="9ad12-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="9ad12-195">下列資料指標狀態可以用不同的方式來執行。</span><span class="sxs-lookup"><span data-stu-id="9ad12-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="9ad12-196">您可以藉由建立資料指標模型（例如狀態機器）來執行這些不同的狀態。</span><span class="sxs-lookup"><span data-stu-id="9ad12-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="9ad12-197">例如：</span><span class="sxs-lookup"><span data-stu-id="9ad12-197">For example:</span></span>
    * <span data-ttu-id="9ad12-198">閒置狀態是您顯示預設資料指標的位置。</span><span class="sxs-lookup"><span data-stu-id="9ad12-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="9ad12-199">[就緒] 狀態是當您在 [就緒] 位置偵測到使用者的手時。</span><span class="sxs-lookup"><span data-stu-id="9ad12-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="9ad12-200">互動狀態是使用者執行特定互動的時候。</span><span class="sxs-lookup"><span data-stu-id="9ad12-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="9ad12-201">可能的動作狀態或暫留狀態是當您傳達可在全像影像上執行的可能動作。</span><span class="sxs-lookup"><span data-stu-id="9ad12-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="9ad12-202">您也可以在偵測到不同狀態時，以面板的方式來執行這些狀態，以顯示不同的藝術資產。</span><span class="sxs-lookup"><span data-stu-id="9ad12-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="9ad12-203">進入「無資料指標」</span><span class="sxs-lookup"><span data-stu-id="9ad12-203">Going "cursor-free"</span></span>

<span data-ttu-id="9ad12-204">當深度的意義是體驗的重要元件，以及透過注視和手勢指向互動 (時，建議您不要使用資料指標進行設計，) 不需要絕佳的精確度。</span><span class="sxs-lookup"><span data-stu-id="9ad12-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="9ad12-205">系統仍然必須符合資料指標的一般需求：為使用者提供持續的意見反應，以瞭解對其指向的系統，並協助他們將其意圖傳達給系統。</span><span class="sxs-lookup"><span data-stu-id="9ad12-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="9ad12-206">這可以透過其他明顯的狀態變更來達成。</span><span class="sxs-lookup"><span data-stu-id="9ad12-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="9ad12-207">適用于 Unity 的 MRTK (混合現實工具組) 的游標</span><span class="sxs-lookup"><span data-stu-id="9ad12-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="9ad12-208">根據預設， [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) 會提供資料指標預製專案 ([DefaultCursor. 預製專案](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) 與 shell 的系統資料指標具有相同的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="9ad12-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="9ad12-209">其是在 MRTK 輸入設定檔的 [指標] 下進行指派。</span><span class="sxs-lookup"><span data-stu-id="9ad12-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="9ad12-210">您可以針對您的體驗取代/自訂此資料指標。</span><span class="sxs-lookup"><span data-stu-id="9ad12-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="9ad12-211">針對眼睛追蹤輸入的體驗，MRTK 也提供 EyeGazeCursor，其具有微妙的視覺效果可將干擾降至最低。</span><span class="sxs-lookup"><span data-stu-id="9ad12-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="9ad12-212">MRTK - 指標設定檔</span><span class="sxs-lookup"><span data-stu-id="9ad12-212">MRTK - Pointer profile</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [<span data-ttu-id="9ad12-213">MRTK - 輸入系統</span><span class="sxs-lookup"><span data-stu-id="9ad12-213">MRTK - Input system</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview)
* [<span data-ttu-id="9ad12-214">MRTK - 指標</span><span class="sxs-lookup"><span data-stu-id="9ad12-214">MRTK - Pointers</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a><span data-ttu-id="9ad12-215">請參閱</span><span class="sxs-lookup"><span data-stu-id="9ad12-215">See also</span></span>

* [<span data-ttu-id="9ad12-216">手勢</span><span class="sxs-lookup"><span data-stu-id="9ad12-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="9ad12-217">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="9ad12-217">Head-gaze and commit</span></span>](gaze-and-commit.md)