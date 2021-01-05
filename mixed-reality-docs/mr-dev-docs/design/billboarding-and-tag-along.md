---
title: 佈告板和常駐標籤
description: 具有 billboarding 的物件一律會導向至臉部給使用者。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、billboarding、加上標籤、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、Mixed Reality 工具組
ms.openlocfilehash: 44f2678fe2f8e4be071086f46037749d1df61ae4
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848027"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="9f275-104">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="9f275-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="9f275-105">什麼是 billboarding？</span><span class="sxs-lookup"><span data-stu-id="9f275-105">What is billboarding?</span></span>

<span data-ttu-id="9f275-106">Billboarding 是一種行為概念，可套用至混合現實中的物件。</span><span class="sxs-lookup"><span data-stu-id="9f275-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="9f275-107">具有 billboarding 的物件一律會導向至臉部給使用者。</span><span class="sxs-lookup"><span data-stu-id="9f275-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="9f275-108">文字和功能表系統是常見的使用案例，也就是在使用者環境中放置的靜態物件 (世界鎖定的) 在使用者四處移動時，會隱藏或無法讀取。</span><span class="sxs-lookup"><span data-stu-id="9f275-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="9f275-109">啟用 billboarding 的物件可以在使用者的環境中自由旋轉。</span><span class="sxs-lookup"><span data-stu-id="9f275-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="9f275-110">根據設計考慮，也可以限制為單一軸。</span><span class="sxs-lookup"><span data-stu-id="9f275-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="9f275-111">請記住，billboarded 物件可能會在放置太接近其他物件的位置，或在 HoloLens 中太接近掃描的表面時，自行裁剪或遮蔽。</span><span class="sxs-lookup"><span data-stu-id="9f275-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="9f275-112">若要避免這種情況，請考慮物件在啟用軸旋轉以進行 billboarding 時，可能會產生的總使用量。</span><span class="sxs-lookup"><span data-stu-id="9f275-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="9f275-113">什麼是標記？</span><span class="sxs-lookup"><span data-stu-id="9f275-113">What is a tag-along?</span></span>

<span data-ttu-id="9f275-114">標記-也是可以新增至全像影像的行為概念。</span><span class="sxs-lookup"><span data-stu-id="9f275-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="9f275-115">以標記為物件的物件會嘗試停留在某個範圍內，讓使用者能夠輕鬆互動。</span><span class="sxs-lookup"><span data-stu-id="9f275-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="9f275-116">![HoloLens 釘選面板是標記的運作方式的絕佳範例](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9f275-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="9f275-117">*HoloLens [開始] 功能表是標記與行為的絕佳範例*</span><span class="sxs-lookup"><span data-stu-id="9f275-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="9f275-118">加上標籤的物件有參數，可以微調其行為方式。</span><span class="sxs-lookup"><span data-stu-id="9f275-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="9f275-119">當使用者在其環境中四處移動時，內容可能會在使用者的看到行中或不存在。</span><span class="sxs-lookup"><span data-stu-id="9f275-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="9f275-120">當您移動時，內容會藉由滑動到視圖的邊緣來嘗試停留在使用者的其邊界中。</span><span class="sxs-lookup"><span data-stu-id="9f275-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="9f275-121">根據使用者的移動速度而定，內容可能會暫時無法觀看。</span><span class="sxs-lookup"><span data-stu-id="9f275-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="9f275-122">當使用者 gazes 到加上標籤的物件時，它會更完整地顯示。</span><span class="sxs-lookup"><span data-stu-id="9f275-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="9f275-123">您可以將內容視為「立即消失」，讓使用者永遠不會忘記其內容的方向。</span><span class="sxs-lookup"><span data-stu-id="9f275-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="9f275-124">額外的參數可讓以標記為依據的物件操作，透過橡膠波段連接到使用者的標頭。</span><span class="sxs-lookup"><span data-stu-id="9f275-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="9f275-125">抑制加速或減速可為物件提供權數，讓它更實際呈現。</span><span class="sxs-lookup"><span data-stu-id="9f275-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="9f275-126">這種彈簧行為是一種 affordance，可協助使用者建立標記與運作方式的精確精神模型。</span><span class="sxs-lookup"><span data-stu-id="9f275-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="9f275-127">當使用者在標記式模式中具有物件時，音訊有助於提供其他提示。</span><span class="sxs-lookup"><span data-stu-id="9f275-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="9f275-128">音訊必須強化移動的速度;快速的前端應該會提供更明顯的音效效果，而自然的速度應該會有最少量或沒有音訊效果。</span><span class="sxs-lookup"><span data-stu-id="9f275-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="9f275-129">就像真正的標頭鎖定內容一樣，標記物件可能會在使用者的觀點中變得太大或太多，而證明很大或 nauseating。</span><span class="sxs-lookup"><span data-stu-id="9f275-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="9f275-130">當使用者想要時，很快就會停止，並告訴他們已停止。</span><span class="sxs-lookup"><span data-stu-id="9f275-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="9f275-131">他們的平衡會通知他們其領導範圍已停止，且其願景會看到世界停止開啟。</span><span class="sxs-lookup"><span data-stu-id="9f275-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="9f275-132">但是，如果在使用者停止時將標籤與移動保持在一起，則可能會使其察覺混淆。</span><span class="sxs-lookup"><span data-stu-id="9f275-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="9f275-133">Billboarding 和標記-沿著 MRTK (Unity 的混合現實工具組) </span><span class="sxs-lookup"><span data-stu-id="9f275-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="9f275-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 會提供 Billboarding 的腳本，以及標記的行為。</span><span class="sxs-lookup"><span data-stu-id="9f275-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="9f275-135">將 Billboard.cs 腳本指派給任何物件以新增 billboarding 行為，並讓物件永遠都有臉部。</span><span class="sxs-lookup"><span data-stu-id="9f275-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="9f275-136">若要加入標記的行為，請使用 RadialView.cs 腳本。</span><span class="sxs-lookup"><span data-stu-id="9f275-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="9f275-137">您可以調整各種選項，例如 lerping 時間、距離和角度。</span><span class="sxs-lookup"><span data-stu-id="9f275-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="9f275-138">MRTK-星形視圖求解</span><span class="sxs-lookup"><span data-stu-id="9f275-138">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="9f275-139">MRTK-佈告欄腳本</span><span class="sxs-lookup"><span data-stu-id="9f275-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="9f275-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="9f275-140">See also</span></span>

* [<span data-ttu-id="9f275-141">游標</span><span class="sxs-lookup"><span data-stu-id="9f275-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9f275-142">手部光線</span><span class="sxs-lookup"><span data-stu-id="9f275-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="9f275-143">Button</span><span class="sxs-lookup"><span data-stu-id="9f275-143">Button</span></span>](button.md)
* [<span data-ttu-id="9f275-144">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="9f275-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9f275-145">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="9f275-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9f275-146">操作</span><span class="sxs-lookup"><span data-stu-id="9f275-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9f275-147">手部功能表</span><span class="sxs-lookup"><span data-stu-id="9f275-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="9f275-148">近端功能表</span><span class="sxs-lookup"><span data-stu-id="9f275-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="9f275-149">物件集合</span><span class="sxs-lookup"><span data-stu-id="9f275-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9f275-150">語音命令</span><span class="sxs-lookup"><span data-stu-id="9f275-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="9f275-151">鍵盤</span><span class="sxs-lookup"><span data-stu-id="9f275-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="9f275-152">工具提示</span><span class="sxs-lookup"><span data-stu-id="9f275-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="9f275-153">平板</span><span class="sxs-lookup"><span data-stu-id="9f275-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="9f275-154">滑桿</span><span class="sxs-lookup"><span data-stu-id="9f275-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="9f275-155">著色器</span><span class="sxs-lookup"><span data-stu-id="9f275-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="9f275-156">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="9f275-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9f275-157">顯示進度</span><span class="sxs-lookup"><span data-stu-id="9f275-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="9f275-158">表面磁性</span><span class="sxs-lookup"><span data-stu-id="9f275-158">Surface magnetism</span></span>](surface-magnetism.md)
