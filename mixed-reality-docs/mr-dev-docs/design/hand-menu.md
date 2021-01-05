---
title: 手部功能表
description: 手形功能表可讓使用者快速地為常用的函式顯示手動連接的 UI。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手、功能表、按鈕、快速存取、版面配置、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 77df5974f54323310a696ed6630fbdde0b0faeb0
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847802"
---
# <a name="hand-menu"></a><span data-ttu-id="8dd93-104">手部功能表</span><span class="sxs-lookup"><span data-stu-id="8dd93-104">Hand menu</span></span>

![Ulnar 側邊位置](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="8dd93-106">手形功能表是 HoloLens 2 中最獨特的 UX 模式之一。</span><span class="sxs-lookup"><span data-stu-id="8dd93-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="8dd93-107">它可讓您快速地顯示手動連接的 UI。</span><span class="sxs-lookup"><span data-stu-id="8dd93-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="8dd93-108">由於它可隨時存取，而且可以輕鬆地顯示和隱藏，因此非常適合快速動作。</span><span class="sxs-lookup"><span data-stu-id="8dd93-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="8dd93-109">您會在下列清單中找到使用手形功能表的建議最佳作法。</span><span class="sxs-lookup"><span data-stu-id="8dd93-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="8dd93-110">您也可以在 [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)中找到示範手形功能表的範例場景。</span><span class="sxs-lookup"><span data-stu-id="8dd93-110">You can also find an example scene demonstrating the hand menu in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="8dd93-111">最佳作法</span><span class="sxs-lookup"><span data-stu-id="8dd93-111">Best practices</span></span>

<span data-ttu-id="8dd93-112">**將按鈕數目維持在最小**</span><span class="sxs-lookup"><span data-stu-id="8dd93-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="8dd93-113">由於手鎖的功能表與眼睛之間的距離，以及使用者每次專注于相對較小的視覺區域，因此 (attentional 的願景大約是10度) ，因此建議您將按鈕數目保持在最小。</span><span class="sxs-lookup"><span data-stu-id="8dd93-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="8dd93-114">根據我們的探索，有三個按鈕的一個資料行，只要將所有內容都放在視野 (FOV) 內，即使使用者將手移至 FOV 的中心，也能妥善運作。</span><span class="sxs-lookup"><span data-stu-id="8dd93-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="8dd93-115">**使用快顯功能表進行快速動作**</span><span class="sxs-lookup"><span data-stu-id="8dd93-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="8dd93-116">引發 arm 並維護位置，可能很容易就會導致 arm 疲勞。</span><span class="sxs-lookup"><span data-stu-id="8dd93-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="8dd93-117">針對需要短暫互動的功能表，請使用手動鎖定的方法。</span><span class="sxs-lookup"><span data-stu-id="8dd93-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="8dd93-118">如果您的功能表很複雜，而且需要延伸互動時間，請考慮改為使用世界鎖定或主體鎖定。</span><span class="sxs-lookup"><span data-stu-id="8dd93-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="8dd93-119">**按鈕/面板角度**</span><span class="sxs-lookup"><span data-stu-id="8dd93-119">**Button / Panel angle**</span></span>

<span data-ttu-id="8dd93-120">功能表應該會朝向相反的肩和中間的部分：這可讓自然手移動以相反的方向與功能表互動，並避免在觸控按鈕時出現任何麻煩或不舒服的位置。</span><span class="sxs-lookup"><span data-stu-id="8dd93-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="8dd93-121">**考慮支援單次或無人參與的作業**</span><span class="sxs-lookup"><span data-stu-id="8dd93-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="8dd93-122">不要假設這兩個使用者的手都一律可供使用。</span><span class="sxs-lookup"><span data-stu-id="8dd93-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="8dd93-123">當一或兩個手中都無法使用時，請考慮各種不同的內容，並確定您的設計帳戶適用于這些情況。</span><span class="sxs-lookup"><span data-stu-id="8dd93-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="8dd93-124">若要支援右手邊的功能表，您可以嘗試將功能表位置從手鎖移至世界鎖定的位置， () 。</span><span class="sxs-lookup"><span data-stu-id="8dd93-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="8dd93-125">針對無人參與的案例，請考慮使用語音命令來叫用快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="8dd93-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="8dd93-126">**避免在手腕 (系統首頁按鈕附近新增按鈕)**</span><span class="sxs-lookup"><span data-stu-id="8dd93-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="8dd93-127">如果放置的功能表按鈕太靠近 [首頁] 按鈕，在與快顯功能表互動時可能會不小心觸發。</span><span class="sxs-lookup"><span data-stu-id="8dd93-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="8dd93-128">具有大型和複雜 UI 控制項的手功能表</span><span class="sxs-lookup"><span data-stu-id="8dd93-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="8dd93-129">建議您限制在手動連接功能表上的按鈕或 UI 控制項數目。</span><span class="sxs-lookup"><span data-stu-id="8dd93-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="8dd93-130">這是因為與大量 UI 元素的延伸互動可能會導致 arm 疲勞。</span><span class="sxs-lookup"><span data-stu-id="8dd93-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="8dd93-131">如果您的經驗需要大型的功能表，請提供簡單的方式讓使用者在世界上鎖定功能表。</span><span class="sxs-lookup"><span data-stu-id="8dd93-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="8dd93-132">我們建議的技巧之一，就是在手離開或跳離使用者時，以世界鎖的方式功能表。</span><span class="sxs-lookup"><span data-stu-id="8dd93-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="8dd93-133">第二種方法是讓使用者直接抓取功能表。</span><span class="sxs-lookup"><span data-stu-id="8dd93-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="8dd93-134">當使用者放開功能表時，功能表應該是「世界鎖定」。</span><span class="sxs-lookup"><span data-stu-id="8dd93-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="8dd93-135">如此一來，使用者就可以在一段長時間內輕鬆且安心地與各種 UI 元素互動。</span><span class="sxs-lookup"><span data-stu-id="8dd93-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="8dd93-136">當功能表被全球鎖定時，請務必提供移動功能表的方法，並在不再需要時關閉功能表。</span><span class="sxs-lookup"><span data-stu-id="8dd93-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="8dd93-137">藉由在功能表的側邊或上方提供控點，讓功能表成為可移動的。</span><span class="sxs-lookup"><span data-stu-id="8dd93-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="8dd93-138">新增 [關閉] 按鈕，讓功能表關閉。</span><span class="sxs-lookup"><span data-stu-id="8dd93-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="8dd93-139">允許功能表在使用者手上臉部時重新附加至手。</span><span class="sxs-lookup"><span data-stu-id="8dd93-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="8dd93-140">此外，我們也建議要求使用者眼看以防止啟用錯誤 (請參閱以下) 。</span><span class="sxs-lookup"><span data-stu-id="8dd93-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="8dd93-141">**顯示可用性問題的大型功能表**</span><span class="sxs-lookup"><span data-stu-id="8dd93-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="8dd93-142">**手上的世界鎖定功能表**</span><span class="sxs-lookup"><span data-stu-id="8dd93-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="8dd93-143">**手動抓取 & 提取至世界鎖定功能表**</span><span class="sxs-lookup"><span data-stu-id="8dd93-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="8dd93-144">如何防止啟用錯誤</span><span class="sxs-lookup"><span data-stu-id="8dd93-144">How to prevent false activation</span></span>

<span data-ttu-id="8dd93-145">如果您只是使用 [上移] 作為事件來觸發快顯功能表，則在不需要時，可能會不小心出現 () ，因為人們會 (刻意針對通訊和物件操作) 和無意地移動其手。</span><span class="sxs-lookup"><span data-stu-id="8dd93-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="8dd93-146">若要減少錯誤的啟用，請新增一個額外的步驟，除了用來叫用快顯功能表 (（例如完全開啟的手指），或使用者刻意撥雲見日手中) 。</span><span class="sxs-lookup"><span data-stu-id="8dd93-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="8dd93-147">**需要平直**</span><span class="sxs-lookup"><span data-stu-id="8dd93-147">**Require Flat Palm**</span></span>

<span data-ttu-id="8dd93-148">藉由要求一般開放手，您可以防止在使用者操作物件或手勢時，可能會在環境內進行通訊時發生的錯誤啟用。</span><span class="sxs-lookup"><span data-stu-id="8dd93-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="8dd93-149">**需要注視**</span><span class="sxs-lookup"><span data-stu-id="8dd93-149">**Require Gaze**</span></span>

<span data-ttu-id="8dd93-150">藉由要求使用者以眼睛 (來看看眼睛) ，它會防止啟用錯誤，因為使用者必須將他們的注意力視為次要啟用步驟， (具有可調式距離閾值以允許使用者緩和) 。</span><span class="sxs-lookup"><span data-stu-id="8dd93-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="8dd93-151">手形功能表位置最佳作法</span><span class="sxs-lookup"><span data-stu-id="8dd93-151">Hand menu placement best practices</span></span>

<span data-ttu-id="8dd93-152">在「人為結構」中，ulnar nerve 是在 ulna 骨骼附近執行的 nerve。</span><span class="sxs-lookup"><span data-stu-id="8dd93-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="8dd93-153">Ulna 是在 forearm 中找到的很長的骨骼，可從彎線伸展至最小的手指。</span><span class="sxs-lookup"><span data-stu-id="8dd93-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="8dd93-154">以下是根據我們的探勘所建議的兩個位置：</span><span class="sxs-lookup"><span data-stu-id="8dd93-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8dd93-155">![Ulnar 手中的側邊位置](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="8dd93-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="8dd93-156">**Ulnar 在 palm 內部**</span><span class="sxs-lookup"><span data-stu-id="8dd93-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="8dd93-157">這個位置是可靠的，因為手不會彼此重迭。</span><span class="sxs-lookup"><span data-stu-id="8dd93-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="8dd93-158">這對於正確的手動偵測和追蹤而言很重要。</span><span class="sxs-lookup"><span data-stu-id="8dd93-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8dd93-159">![Ulnar 手邊的側邊位置](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="8dd93-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="8dd93-160">**B. Ulnar 以上的手**</span><span class="sxs-lookup"><span data-stu-id="8dd93-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="8dd93-161">此位置很適合使用者，因為他們不需要使 arm 太多，就能與手形功能表互動。</span><span class="sxs-lookup"><span data-stu-id="8dd93-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="8dd93-162">建議您將功能表 **13 釐米** 放在掌上，並對齊 ulnar 掌內的按鈕。</span><span class="sxs-lookup"><span data-stu-id="8dd93-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="8dd93-163">深入瞭解最佳按鈕大小</span><span class="sxs-lookup"><span data-stu-id="8dd93-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="8dd93-164">基於技術的考慮，我們建議您在這個位置使用一個必要的實作為：當使用者的相對應接近其與其互動時，開發人員必須凍結功能表。</span><span class="sxs-lookup"><span data-stu-id="8dd93-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="8dd93-165">這可避免 jitteriness 重迭，也可讓您以更快的按鈕為目標。</span><span class="sxs-lookup"><span data-stu-id="8dd93-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="8dd93-166">HoloLens 2 攝影機會在彼此分開時，正確地識別手。</span><span class="sxs-lookup"><span data-stu-id="8dd93-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="8dd93-167">任何重迭的手都可能會導致手中的功能表移離錨點位置。</span><span class="sxs-lookup"><span data-stu-id="8dd93-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="8dd93-168">不建議的功能表位置</span><span class="sxs-lookup"><span data-stu-id="8dd93-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="8dd93-169">我們已使用不同的功能表版面配置和位置完成使用者研究， **不建議** 使用下列功能表位置，請找出下列各項研究的缺點：</span><span class="sxs-lookup"><span data-stu-id="8dd93-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8dd93-170">![上方 arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="8dd93-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="8dd93-171">**Arm 上方**</span><span class="sxs-lookup"><span data-stu-id="8dd93-171">**Above the arm**</span></span><br>
        <span data-ttu-id="8dd93-172">1-難以維護良好的手追蹤</span><span class="sxs-lookup"><span data-stu-id="8dd93-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="8dd93-173">2-因為非自然位置而導致使用者疲勞</span><span class="sxs-lookup"><span data-stu-id="8dd93-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8dd93-174">![上方手指](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="8dd93-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="8dd93-175">**上方手指**</span><span class="sxs-lookup"><span data-stu-id="8dd93-175">**Above fingers**</span></span><br>
        <span data-ttu-id="8dd93-176">1-手疲勞是因為長期保留的手</span><span class="sxs-lookup"><span data-stu-id="8dd93-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="8dd93-177">2-在索引和中間手指追蹤問題</span><span class="sxs-lookup"><span data-stu-id="8dd93-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="8dd93-178">![上方的棕櫚](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="8dd93-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="8dd93-179">**上方-中央棕櫚**</span><span class="sxs-lookup"><span data-stu-id="8dd93-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="8dd93-180">1-手動追蹤問題，因為有重迭的手</span><span class="sxs-lookup"><span data-stu-id="8dd93-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="8dd93-181">2-手疲勞是因為持續很長的時間與功能表互動</span><span class="sxs-lookup"><span data-stu-id="8dd93-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8dd93-182">![Top Fingertip ](images/TopFingerTip.gif) **top Fingertip**</span><span class="sxs-lookup"><span data-stu-id="8dd93-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="8dd93-183">1-手追蹤問題</span><span class="sxs-lookup"><span data-stu-id="8dd93-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="8dd93-184">2-手疲勞，不是以正常狀態的手</span><span class="sxs-lookup"><span data-stu-id="8dd93-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="8dd93-185">3-因手指之間的空間有限，而導致按下其他手指的按鈕時發生問題</span><span class="sxs-lookup"><span data-stu-id="8dd93-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="8dd93-186">![Arm 背面](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="8dd93-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="8dd93-187">**Arm 背面**</span><span class="sxs-lookup"><span data-stu-id="8dd93-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="8dd93-188">1-可能會意外觸發首頁按鈕</span><span class="sxs-lookup"><span data-stu-id="8dd93-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="8dd93-189">2-不是自然或舒適的位置</span><span class="sxs-lookup"><span data-stu-id="8dd93-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="8dd93-190">適用于 Unity 的 MRTK (混合現實工具組) 的手中功能表</span><span class="sxs-lookup"><span data-stu-id="8dd93-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="8dd93-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供快顯功能表的腳本和範例幕後。</span><span class="sxs-lookup"><span data-stu-id="8dd93-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="8dd93-192">HandConstraintPalmUp 求解腳本可讓您使用各種可設定的選項，將任何物件附加至手。</span><span class="sxs-lookup"><span data-stu-id="8dd93-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="8dd93-193">MRTK 的功能表範例包含實用的選項，例如，用來防止啟用錯誤的一般棕櫚和注視需求。</span><span class="sxs-lookup"><span data-stu-id="8dd93-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="8dd93-194">手形功能表檔</span><span class="sxs-lookup"><span data-stu-id="8dd93-194">Hand Menu Documentations</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [<span data-ttu-id="8dd93-195">手形功能表範例場景</span><span class="sxs-lookup"><span data-stu-id="8dd93-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="8dd93-196">您可以使用 MRTK 範例中樞應用程式，在 HoloLens 2 中試用手中的功能表範例。</span><span class="sxs-lookup"><span data-stu-id="8dd93-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="8dd93-197">MRTK 範例中樞中的手邊功能表場景</span><span class="sxs-lookup"><span data-stu-id="8dd93-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="8dd93-198">請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd93-198">See also</span></span>

* [<span data-ttu-id="8dd93-199">游標</span><span class="sxs-lookup"><span data-stu-id="8dd93-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8dd93-200">手部光線</span><span class="sxs-lookup"><span data-stu-id="8dd93-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8dd93-201">Button</span><span class="sxs-lookup"><span data-stu-id="8dd93-201">Button</span></span>](button.md)
* [<span data-ttu-id="8dd93-202">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="8dd93-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8dd93-203">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="8dd93-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8dd93-204">操作</span><span class="sxs-lookup"><span data-stu-id="8dd93-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8dd93-205">手部功能表</span><span class="sxs-lookup"><span data-stu-id="8dd93-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8dd93-206">近端功能表</span><span class="sxs-lookup"><span data-stu-id="8dd93-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8dd93-207">物件集合</span><span class="sxs-lookup"><span data-stu-id="8dd93-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8dd93-208">語音命令</span><span class="sxs-lookup"><span data-stu-id="8dd93-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8dd93-209">鍵盤</span><span class="sxs-lookup"><span data-stu-id="8dd93-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8dd93-210">工具提示</span><span class="sxs-lookup"><span data-stu-id="8dd93-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8dd93-211">平板</span><span class="sxs-lookup"><span data-stu-id="8dd93-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="8dd93-212">滑桿</span><span class="sxs-lookup"><span data-stu-id="8dd93-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="8dd93-213">著色器</span><span class="sxs-lookup"><span data-stu-id="8dd93-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="8dd93-214">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="8dd93-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8dd93-215">顯示進度</span><span class="sxs-lookup"><span data-stu-id="8dd93-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8dd93-216">表面磁性</span><span class="sxs-lookup"><span data-stu-id="8dd93-216">Surface magnetism</span></span>](surface-magnetism.md)
