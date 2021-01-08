---
title: 案例研究 - 在實境中的的透視技術
description: 此案例研究說明 HoloLens 上的「魔術視窗」效果，讓使用者可以在地板後方、在地面下，以及進入虛擬機器會。
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、魔術視窗、視差
ms.openlocfilehash: 018e45a79d88cbc8e28204f023106fbe5dae39bc
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010108"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="d0e56-104">案例研究 - 在實境中的的透視技術</span><span class="sxs-lookup"><span data-stu-id="d0e56-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="d0e56-105">當人們思考混合的現實，以及他們可以如何運用 Microsoft HoloLens 時，通常會發生像是「我可以將哪些物件新增到我的房間？」之類的問題。</span><span class="sxs-lookup"><span data-stu-id="d0e56-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="d0e56-106">或「我可以在我的空間上方分層？」</span><span class="sxs-lookup"><span data-stu-id="d0e56-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="d0e56-107">我想要強調您可以考慮的另一個領域，基本上是一種魔術訣竅，也就是使用相同的技術來查看或透過真實的實體物件。</span><span class="sxs-lookup"><span data-stu-id="d0e56-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="d0e56-108">技術</span><span class="sxs-lookup"><span data-stu-id="d0e56-108">The tech</span></span>

<span data-ttu-id="d0e56-109">如果您已在 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 中曾外星人， **[而在](case-study-creating-an-immersive-experience-in-fragments.md)** 中，已將牆安全解除鎖定，或幸運于在 **[2015 的 E3 5 體驗](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 中查看 UNSC 無限大 hangar，則您已瞭解我所說的內容。</span><span class="sxs-lookup"><span data-stu-id="d0e56-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="d0e56-110">根據您的想像，此視覺效果可以用來將暫時性的洞放在您的幹，或隱藏在鬆散 floorboard 下的世界。</span><span class="sxs-lookup"><span data-stu-id="d0e56-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid 會在您的牆後方新增三維管道和其他結構，只會透過太空入侵者中斷時所建立的漏洞來顯示。](../develop/unity/images/roboraid-640px.png)

<span data-ttu-id="d0e56-112">RoboRaid 會在您的牆後方新增三維管道和其他結構，只會透過太空入侵者中斷時所建立的漏洞來顯示。</span><span class="sxs-lookup"><span data-stu-id="d0e56-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="d0e56-113">在 HoloLens 上使用其中一個獨特的全息圖，應用程式可以提供您牆背後的內容，或透過您的樓層，以實際在實際視窗中呈現本身的相同方式。</span><span class="sxs-lookup"><span data-stu-id="d0e56-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="d0e56-114">將您自己移至左側，您可以在右側看到任何內容。</span><span class="sxs-lookup"><span data-stu-id="d0e56-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="d0e56-115">深入瞭解，您可以看到更多東西。</span><span class="sxs-lookup"><span data-stu-id="d0e56-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="d0e56-116">主要的差異在於，您的樓層 stubbornly 不會讓您通過神奇的全像內容。</span><span class="sxs-lookup"><span data-stu-id="d0e56-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="d0e56-117"> (我要將工作新增至待處理專案。 ) </span><span class="sxs-lookup"><span data-stu-id="d0e56-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="d0e56-118">在幕後</span><span class="sxs-lookup"><span data-stu-id="d0e56-118">Behind the scenes</span></span>

<span data-ttu-id="d0e56-119">這項技巧是兩種效果的組合。</span><span class="sxs-lookup"><span data-stu-id="d0e56-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="d0e56-120">首先，使用「空間錨點」將全息內容釘選到世界。</span><span class="sxs-lookup"><span data-stu-id="d0e56-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="d0e56-121">使用錨點將內容設為「世界鎖定」，表示您所要查看的內容不會以視覺化方式與附近的實體物件漂移，即使您移動或基礎空間對應系統會更新其房間的3D 模型。</span><span class="sxs-lookup"><span data-stu-id="d0e56-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="d0e56-122">其次，在視覺上，這種全像生活的內容會以視覺方式限制為非常特定的空間，因此您只會看到您實際的洞。</span><span class="sxs-lookup"><span data-stu-id="d0e56-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="d0e56-123">需要遮蔽，才能透過邏輯洞、視窗或閘口（其銷售訣竅）來查看。</span><span class="sxs-lookup"><span data-stu-id="d0e56-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="d0e56-124">如果未封鎖大部分的視圖，秘密 Jurassic 維度的空間破解可能就像是不良放置的恐龍。</span><span class="sxs-lookup"><span data-stu-id="d0e56-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![這並不是實際的螢幕擷取畫面，而是從 MR 基礎101的秘密 underworld 到 HoloLens 的說明。](images/origamiholecomposited-640px.png)

<span data-ttu-id="d0e56-128">這並不是實際的螢幕擷取畫面，而是從 [MR 基礎 101](../develop/unity/tutorials/holograms-101.md) underworld 秘密的說明，看看 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d0e56-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](../develop/unity/tutorials/holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="d0e56-129">黑色主機殼未顯示，但您可以透過虛擬洞看到內容。</span><span class="sxs-lookup"><span data-stu-id="d0e56-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="d0e56-130"> (當您查看實際的裝置時，可能會因為您的眼睛焦點與甚至沒有的距離，而消失。 ) </span><span class="sxs-lookup"><span data-stu-id="d0e56-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="d0e56-131">全球鎖定的全像內容</span><span class="sxs-lookup"><span data-stu-id="d0e56-131">World-locking holographic content</span></span>

<span data-ttu-id="d0e56-132">在 Unity 中，造成全像全球的內容保持全球鎖定，就像新增 WorldAnchor 元件一樣簡單：</span><span class="sxs-lookup"><span data-stu-id="d0e56-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="d0e56-133">WorldAnchor 元件會不斷地調整其 GameObject (的位置和旋轉，因此階層中該物件下的任何其他地方都會) ，使其相對於附近的實體物件保持穩定。</span><span class="sxs-lookup"><span data-stu-id="d0e56-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="d0e56-134">撰寫您的內容時，請以您物件的根軸在這個虛擬洞的中央來建立它。</span><span class="sxs-lookup"><span data-stu-id="d0e56-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="d0e56-135"> (如果物件的資料透視是在牆中的深度，則在位置和旋轉方面稍微調整會更明顯，且洞看起來可能不穩定。 ) </span><span class="sxs-lookup"><span data-stu-id="d0e56-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="d0e56-136">遮蔽虛擬洞以外的所有專案</span><span class="sxs-lookup"><span data-stu-id="d0e56-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="d0e56-137">有多種方式可以選擇性地將視圖封鎖在您的牆中隱藏的區域。</span><span class="sxs-lookup"><span data-stu-id="d0e56-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="d0e56-138">最簡單的方法是利用 HoloLens 使用加法顯示的事實，這表示完全黑色的物件會顯示為不可見。</span><span class="sxs-lookup"><span data-stu-id="d0e56-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="d0e56-139">您可以在 Unity 中執行這項操作，而不需要執行任何特殊的著色器或材質訣竅，只要建立黑色材質，然後將它指派給內容中的方塊。</span><span class="sxs-lookup"><span data-stu-id="d0e56-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="d0e56-140">如果您不喜歡進行3D 模型化，只需使用一些預設的四個物件，並稍微重迭它們。</span><span class="sxs-lookup"><span data-stu-id="d0e56-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="d0e56-141">這種方法有幾個缺點，不過它是讓工作變得最快的方式，而取得低精確度的概念證明是很棒的，即使您懷疑稍後可能會想要重構它。</span><span class="sxs-lookup"><span data-stu-id="d0e56-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="d0e56-142">上述「黑箱」方法的一個主要缺點是，它不會有很好的相片。</span><span class="sxs-lookup"><span data-stu-id="d0e56-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="d0e56-143">雖然您的效果可能會透過 HoloLens 的顯示結果看起來很完美，但您所採取的任何螢幕擷取畫面都會顯示大型的黑色物件，而不是您的牆或樓層。</span><span class="sxs-lookup"><span data-stu-id="d0e56-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="d0e56-144">原因是實體硬體和螢幕擷取畫面的複合全息圖和事實有不同。</span><span class="sxs-lookup"><span data-stu-id="d0e56-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="d0e56-145">讓我們繞道一點假的數學 .。。</span><span class="sxs-lookup"><span data-stu-id="d0e56-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="d0e56-146">*假的數學警示！這些數位和公式的目的是要說明某個點，而不是任何種類的精確度量！*</span><span class="sxs-lookup"><span data-stu-id="d0e56-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="d0e56-147">您透過 HoloLens 看到的內容：</span><span class="sxs-lookup"><span data-stu-id="d0e56-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="d0e56-148">您在螢幕擷取畫面和影片中看到的內容：</span><span class="sxs-lookup"><span data-stu-id="d0e56-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="d0e56-149">英文：您透過 HoloLens 看到的內容是簡單的事實 (的組合，例如透過太陽眼鏡) ，以及應用程式想要顯示的任何影像。</span><span class="sxs-lookup"><span data-stu-id="d0e56-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="d0e56-150">但是，當您拍攝螢幕擷取畫面時，相機的影像會根據每個圖元的透明度值，與應用程式的全像混合。</span><span class="sxs-lookup"><span data-stu-id="d0e56-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="d0e56-151">解決此問題的方法之一是將「黑色方塊」材質變更為只寫入深度緩衝區，並使用所有其他不透明的材質進行排序。</span><span class="sxs-lookup"><span data-stu-id="d0e56-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="d0e56-152">如需相關範例，請參閱[GitHub 上 MixedRealityToolkit 中的 WindowOcclusion。](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)</span><span class="sxs-lookup"><span data-stu-id="d0e56-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="d0e56-153">相關的程式碼會複製到此處：</span><span class="sxs-lookup"><span data-stu-id="d0e56-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="d0e56-154"> (請注意，「位移50，100」這一行是為了處理不相關的問題，因此，將它留出可能是合理的。 ) </span><span class="sxs-lookup"><span data-stu-id="d0e56-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="d0e56-155">執行這類不可見的遮蔽資料，可讓您的應用程式在顯示和混合式事實螢幕擷取畫面中繪製出看起來正確的方塊。</span><span class="sxs-lookup"><span data-stu-id="d0e56-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="d0e56-156">針對額外的一點，您可以嘗試更進一步改善該方塊的效能，方法是執行聰明的事情來繪製更少的不可見圖元，但這可能真的會進入除去，而且通常不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="d0e56-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![以下是 Unity 基礎101中的秘密 underworld，因為 Unity 會將它繪製，除了遮蔽方塊的外部部分。](images/underworld-occluded-640px.png)

<span data-ttu-id="d0e56-159">以下是 Unity [基礎 101](../develop/unity/tutorials/holograms-101.md) 中的秘密 underworld，因為 Unity 會將它繪製，除了遮蔽方塊的外部部分。</span><span class="sxs-lookup"><span data-stu-id="d0e56-159">Here is the secret underworld from [MR Basics 101](../develop/unity/tutorials/holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="d0e56-160">請注意，underworld 的 pivot 是在方塊的中央，可協助盡可能保持最穩定的洞相對於實際的樓層。</span><span class="sxs-lookup"><span data-stu-id="d0e56-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="d0e56-161">親自完成</span><span class="sxs-lookup"><span data-stu-id="d0e56-161">Do it yourself</span></span>

<span data-ttu-id="d0e56-162">有 HoloLens，想要親自試試看自己的效果嗎？</span><span class="sxs-lookup"><span data-stu-id="d0e56-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="d0e56-163"> (不) 需要撰寫程式碼，最簡單的方式就是安裝免費的3D 檢視器應用程式，然後載入 [我在 GitHub 上提供的 fbx](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) 檔案，以在您的房間內查看花卉模型。</span><span class="sxs-lookup"><span data-stu-id="d0e56-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="d0e56-164">在 HoloLens 上載入它，您就可以查看工作中的假像。</span><span class="sxs-lookup"><span data-stu-id="d0e56-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="d0e56-165">當您在模型前面時，您只會看到輕微的部分，其他所有專案則不會顯示。</span><span class="sxs-lookup"><span data-stu-id="d0e56-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="d0e56-166">從其他任何一端查看模型，它會完全消失。</span><span class="sxs-lookup"><span data-stu-id="d0e56-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="d0e56-167">使用3D 檢視器的移動、旋轉和縮放控制項，將虛擬洞定位至您可以想像用來產生一些構想的任何垂直介面！</span><span class="sxs-lookup"><span data-stu-id="d0e56-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![在 Unity 編輯器中查看此模型，會在 flowerpot 周圍顯示大型的黑色方塊。](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="d0e56-170">在 Unity 編輯器中查看此模型，會在 flowerpot 周圍顯示大型的黑色方塊。</span><span class="sxs-lookup"><span data-stu-id="d0e56-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="d0e56-171">在 HoloLens 上，此方塊會消失，讓魔術視窗的效果更上一種。</span><span class="sxs-lookup"><span data-stu-id="d0e56-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="d0e56-172">如果您想要建立使用這項技術的應用程式，請查看[混合現實教學](../develop/unity/tutorials.md)課程中的[MR 基本概念101教學](../develop/unity/tutorials/holograms-101.md)課程。</span><span class="sxs-lookup"><span data-stu-id="d0e56-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](../develop/unity/tutorials/holograms-101.md) in the [Mixed Reality tutorials](../develop/unity/tutorials.md).</span></span> <span data-ttu-id="d0e56-173">第7章以您的樓層進行爆炸，顯示隱藏的 underworld (，如上面所示) 。</span><span class="sxs-lookup"><span data-stu-id="d0e56-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="d0e56-174">誰說過教學課程必須很乏味？</span><span class="sxs-lookup"><span data-stu-id="d0e56-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="d0e56-175">以下是一些您可以在這裡採取這項構想的概念：</span><span class="sxs-lookup"><span data-stu-id="d0e56-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="d0e56-176">想辦法讓虛擬洞內的內容成為互動。</span><span class="sxs-lookup"><span data-stu-id="d0e56-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="d0e56-177">讓您的使用者在其牆之外有一些影響，可以真正改善這項技巧可以提供的意義。</span><span class="sxs-lookup"><span data-stu-id="d0e56-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="d0e56-178">想辦法將物件查看回已知區域。</span><span class="sxs-lookup"><span data-stu-id="d0e56-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="d0e56-179">例如，您要如何在咖啡表中放入全像地面？</span><span class="sxs-lookup"><span data-stu-id="d0e56-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="d0e56-180">關於作者</span><span class="sxs-lookup"><span data-stu-id="d0e56-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d0e56-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="d0e56-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="d0e56-182">資深軟體工程師 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d0e56-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="d0e56-183">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0e56-183">See also</span></span>
* [<span data-ttu-id="d0e56-184">MR Basics 101：使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="d0e56-184">MR Basics 101: Complete project with device</span></span>](../develop/unity/tutorials/holograms-101.md)
* [<span data-ttu-id="d0e56-185">座標系統</span><span class="sxs-lookup"><span data-stu-id="d0e56-185">Coordinate systems</span></span>](../design/coordinate-systems.md)
* [<span data-ttu-id="d0e56-186">空間錨點</span><span class="sxs-lookup"><span data-stu-id="d0e56-186">Spatial anchors</span></span>](../design/spatial-anchors.md)
* [<span data-ttu-id="d0e56-187">空間對應</span><span class="sxs-lookup"><span data-stu-id="d0e56-187">Spatial mapping</span></span>](../design/spatial-mapping.md)
