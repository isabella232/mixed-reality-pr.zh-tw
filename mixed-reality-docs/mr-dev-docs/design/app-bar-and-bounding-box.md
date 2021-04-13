---
title: 週框方塊和應用程式列
description: 應用程式行是一個物件層級的功能表，其中包含一系列的按鈕，可顯示在全像影像的範圍下邊緣。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality，應用程式橫條，周框方塊，混合現實耳機，windows Mixed Reality 耳機，虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 0ccec5240854de9a7db6a79d5b90b97f1e6b81de
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299903"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="6f4c5-104">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="6f4c5-104">Bounding box and App bar</span></span>
<span data-ttu-id="6f4c5-105">![「周框」是混合現實物件操作的標準介面。](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="6f4c5-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="6f4c5-106">什麼是周框方塊？</span><span class="sxs-lookup"><span data-stu-id="6f4c5-106">What is the Bounding box?</span></span>

<span data-ttu-id="6f4c5-107">「周框」是混合現實物件操作的標準介面。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="6f4c5-108">這項功能可為使用者提供視覺提示，指出物件目前是可調整的。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="6f4c5-109">在 HoloLens 2 上，周框方塊適用于直接操作，而且會回應使用者的 finger's 鄰近性。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="6f4c5-110">它會顯示視覺效果的意見反應，以協助使用者感知與物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="6f4c5-111">調整物件</span><span class="sxs-lookup"><span data-stu-id="6f4c5-111">Scaling an object</span></span><br>
        <span data-ttu-id="6f4c5-112">周框方塊的邊角會告訴使用者物件可以調整的範圍。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="6f4c5-113">控點會遵循廣泛瞭解的調整規模模式。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="6f4c5-114">此視覺提示會顯示使用者物件的總區域，即使在調整模式之外看不到它。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="6f4c5-115">如果沒有這項功能，則會有一個物件（貼齊至另一個物件或介面）的行為，就像是在不應該出現的位置周圍一樣。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="6f4c5-116">*影片迴圈：透過周框方塊調整物件*</span><span class="sxs-lookup"><span data-stu-id="6f4c5-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="6f4c5-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="6f4c5-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="6f4c5-118">![HoloLens 透過周框方塊調整物件的觀點](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="6f4c5-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="6f4c5-119">旋轉物件</span><span class="sxs-lookup"><span data-stu-id="6f4c5-119">Rotating an object</span></span><br>
        <span data-ttu-id="6f4c5-120">周框方塊邊緣的垂直矩形 affordances 是旋轉指示器。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="6f4c5-121">如此可讓使用者更精細地調整其放置的全像投影。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="6f4c5-122">他們不僅能調整規模，還能調整規模，現在也可以旋轉。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="6f4c5-123">*影片迴圈：透過周框方塊旋轉物件*</span><span class="sxs-lookup"><span data-stu-id="6f4c5-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="6f4c5-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="6f4c5-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="6f4c5-125">![HoloLens 透過周框方塊旋轉物件的觀點](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="6f4c5-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="6f4c5-126">HoloLens 2 上的手近距離視覺回饋</span><span class="sxs-lookup"><span data-stu-id="6f4c5-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="6f4c5-127">在 HoloLens 2 上有一個額外的視覺提示，可協助使用者深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="6f4c5-128">當 fingertip 接近物件時，靠近其 fingertip 的環形會顯示並縮小。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="6f4c5-129">當觸達已按下的狀態時，環形最終會聚合成點。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="6f4c5-130">此 visual affordance 可協助使用者瞭解它們與物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="6f4c5-131">*影片迴圈：根據鄰近範圍方塊的視覺效果意見反應範例*</span><span class="sxs-lookup"><span data-stu-id="6f4c5-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="6f4c5-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="6f4c5-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="6f4c5-133">![關於手近距離的視覺回饋](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="6f4c5-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="6f4c5-134">**針對 Unity 應用程式開發，請參閱 [混合現實工具組-Unity 中的周框方塊。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="6f4c5-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="6f4c5-135">什麼是應用程式行？</span><span class="sxs-lookup"><span data-stu-id="6f4c5-135">What is the App bar?</span></span>

<span data-ttu-id="6f4c5-136">應用程式行是一個物件層級的功能表，其中包含一系列顯示在全像全像全像在全像是在全像影像的邊界下邊緣的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="6f4c5-137">此模式通常用來讓使用者移除及調整全像投影。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="6f4c5-138">應用程式行的設計主要是在使用者的環境中管理放置物件的方式。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="6f4c5-139">結合周框方塊，使用者可以完全掌控物件在混合現實中的位置和方式。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="6f4c5-140">應用程式行會跟隨使用者</span><span class="sxs-lookup"><span data-stu-id="6f4c5-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="6f4c5-141">由於這個模式會與全球鎖定的物件一起使用，因此當使用者四處移動物件時，應用程式行一律會顯示在最接近使用者的物件端。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="6f4c5-142">雖然在技術上並不 billboarding，但這項功能實際上也達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="6f4c5-143">防止使用者的位置遮蔽或封鎖可從環境中的不同位置取得的功能。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="6f4c5-144">*影片迴圈：流覽全像投影，應用程式行*</span><span class="sxs-lookup"><span data-stu-id="6f4c5-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="6f4c5-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="6f4c5-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="6f4c5-146">![四處移動全像投影。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-146">![Walking around a hologram.</span></span> <span data-ttu-id="6f4c5-147">應用程式行如下。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="6f4c5-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="6f4c5-148">Unity 的 MRTK (混合現實工具組) 中的周框方塊</span><span class="sxs-lookup"><span data-stu-id="6f4c5-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="6f4c5-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供周框方塊和應用程式行的腳本和 prefabs。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="6f4c5-150">您可以藉由將 BoundingBox .cs 腳本指派給任何物件，來新增周框方塊。</span><span class="sxs-lookup"><span data-stu-id="6f4c5-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="6f4c5-151">MRTK 周框方塊</span><span class="sxs-lookup"><span data-stu-id="6f4c5-151">MRTK - Bounding Box</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a><span data-ttu-id="6f4c5-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f4c5-152">See also</span></span>

* [<span data-ttu-id="6f4c5-153">游標</span><span class="sxs-lookup"><span data-stu-id="6f4c5-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6f4c5-154">手部光線</span><span class="sxs-lookup"><span data-stu-id="6f4c5-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="6f4c5-155">Button</span><span class="sxs-lookup"><span data-stu-id="6f4c5-155">Button</span></span>](button.md)
* [<span data-ttu-id="6f4c5-156">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="6f4c5-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6f4c5-157">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="6f4c5-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6f4c5-158">操作</span><span class="sxs-lookup"><span data-stu-id="6f4c5-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6f4c5-159">手部功能表</span><span class="sxs-lookup"><span data-stu-id="6f4c5-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="6f4c5-160">近端功能表</span><span class="sxs-lookup"><span data-stu-id="6f4c5-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="6f4c5-161">物件集合</span><span class="sxs-lookup"><span data-stu-id="6f4c5-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6f4c5-162">語音命令</span><span class="sxs-lookup"><span data-stu-id="6f4c5-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="6f4c5-163">鍵盤</span><span class="sxs-lookup"><span data-stu-id="6f4c5-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="6f4c5-164">工具提示</span><span class="sxs-lookup"><span data-stu-id="6f4c5-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="6f4c5-165">平板</span><span class="sxs-lookup"><span data-stu-id="6f4c5-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="6f4c5-166">滑桿</span><span class="sxs-lookup"><span data-stu-id="6f4c5-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="6f4c5-167">著色器</span><span class="sxs-lookup"><span data-stu-id="6f4c5-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="6f4c5-168">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="6f4c5-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6f4c5-169">顯示進度</span><span class="sxs-lookup"><span data-stu-id="6f4c5-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="6f4c5-170">表面磁性</span><span class="sxs-lookup"><span data-stu-id="6f4c5-170">Surface magnetism</span></span>](surface-magnetism.md)
