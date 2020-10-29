---
title: 調整
description: 以全像攝影形式呈現看似逼真內容的關鍵，就是盡可能地模擬真實世界的視覺統計資料。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、樣式、設計
ms.openlocfilehash: a9a02d681986df3d73c7990fc975e659e5326981
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679428"
---
# <a name="scale"></a><span data-ttu-id="3c78f-104">調整</span><span class="sxs-lookup"><span data-stu-id="3c78f-104">Scale</span></span>

<span data-ttu-id="3c78f-105">以全像攝影形式呈現看似逼真內容的關鍵，就是盡可能地模擬真實世界的視覺統計資料。</span><span class="sxs-lookup"><span data-stu-id="3c78f-105">A key to displaying content that looks realistic in holographic form is to mimic the visual statistics of the real world as closely as possible.</span></span> <span data-ttu-id="3c78f-106">這表示我們可以盡可能地將多個視覺提示加以結合，協助我們 (在真實世界中) 了解物件的位置、大小以及其構成。</span><span class="sxs-lookup"><span data-stu-id="3c78f-106">This means incorporating as many of the visual cues as we can that help us (in the real world) understand where objects are, how big they are, and what they’re made of.</span></span> <span data-ttu-id="3c78f-107">物件的小數位數是這些視覺提示最重要的其中一項，可讓檢視器瞭解物件的大小，以及其位置的提示 (特別是已知大小) 的物件。</span><span class="sxs-lookup"><span data-stu-id="3c78f-107">The scale of an object is one of the most important of those visual cues, giving a viewer a sense of the size of an object as well as cues to its location (especially for objects which have a known size).</span></span> <span data-ttu-id="3c78f-108">此外，真實規模的觀看物件已經被視為混合現實的其中一個主要體驗差異，也就是在先前以螢幕為基礎的視圖上尚未可能發生的情況。</span><span class="sxs-lookup"><span data-stu-id="3c78f-108">Further, viewing objects at real scale has been seen as one of the key experience differentiators for mixed reality in general – something that hasn’t been possible on screen-based viewing previously.</span></span>

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a><span data-ttu-id="3c78f-109">如何建議物件和環境的規模</span><span class="sxs-lookup"><span data-stu-id="3c78f-109">How to suggest the scale of objects and environments</span></span>

<span data-ttu-id="3c78f-110">有許多方式可以建議物件的小數位數，其中有些可能會影響其他可感知的因素。</span><span class="sxs-lookup"><span data-stu-id="3c78f-110">There are many ways to suggest the scale of an object, some of which have possible effects on other perceptual factors.</span></span> <span data-ttu-id="3c78f-111">關鍵是只要以「真實」大小顯示物件，並在使用者移動時維持實際大小。</span><span class="sxs-lookup"><span data-stu-id="3c78f-111">The key one is to simply display objects at a ‘real’ size, and maintain that realistic size as users move.</span></span> <span data-ttu-id="3c78f-112">這表示在使用者的視覺角度更近或更近的情況下，全像是在使用者的視覺角度，與實際物件的方式相同。</span><span class="sxs-lookup"><span data-stu-id="3c78f-112">This means holograms will take up a different amount of a user’s visual angle of a user as they come closer or further away, the same way that real objects do.</span></span>

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a><span data-ttu-id="3c78f-113">使用物件在呈現給使用者時的距離</span><span class="sxs-lookup"><span data-stu-id="3c78f-113">Utilize the distance of objects as they are presented to the user</span></span>

<span data-ttu-id="3c78f-114">其中一個常見的方法是在物件呈現給使用者時，利用物件的距離。</span><span class="sxs-lookup"><span data-stu-id="3c78f-114">One common method is to utilize the distance of objects as they are presented to the user.</span></span> <span data-ttu-id="3c78f-115">例如，請考慮將大型家庭車輛視覺化到使用者前方。</span><span class="sxs-lookup"><span data-stu-id="3c78f-115">For example, consider visualizing a large family car in front of the user.</span></span> <span data-ttu-id="3c78f-116">如果車輛直接在其前方，則在 arm 的長度內，會太大而無法納入使用者的觀點。</span><span class="sxs-lookup"><span data-stu-id="3c78f-116">If the car were directly in front of them, within arm’s length, it would be too large to fit in the user’s field of view.</span></span> <span data-ttu-id="3c78f-117">這會要求使用者移動其標頭和主體，以瞭解整個物件。</span><span class="sxs-lookup"><span data-stu-id="3c78f-117">This would require the user to move their head and body to understand the entirety of the object.</span></span> <span data-ttu-id="3c78f-118">如果車輛 (在房間) 的周圍，則使用者可以在其視野中查看整個物件，然後將其放在更靠近的位置，以詳細檢查區域，藉此建立規模。</span><span class="sxs-lookup"><span data-stu-id="3c78f-118">If the car were placed further away (across the room), the user can establish a sense of scale by seeing the entirety of the object in their field of view, then moving themselves closer to it to inspect areas in detail.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3c78f-119">**[Volvo 使用這項技術來建立](https://www.youtube.com/watch?v=DilzwF90vec)** 新汽車的 showroom 體驗，利用全像全像直覺的方式，利用全像是對使用者來說非常直覺的方式來運用全像攝影車。</span><span class="sxs-lookup"><span data-stu-id="3c78f-119">**[Volvo used this technique to create a showroom](https://www.youtube.com/watch?v=DilzwF90vec)** experience for a new car, utilizing the scale of the holographic car in a way that felt realistic and intuitive to the user.</span></span> <span data-ttu-id="3c78f-120">體驗是從實體資料表上的汽車全像投影開始，讓使用者瞭解模型的總大小和形狀。</span><span class="sxs-lookup"><span data-stu-id="3c78f-120">The experience begins with a hologram of the car on a physical table, allowing the user to understand the total size and shape of the model.</span></span> <span data-ttu-id="3c78f-121">稍後在此體驗中，汽車會擴充到更大的 (，而超出裝置欄位的大小) 但因為使用者已從較小的模型取得參考的畫面格，所以可充分地四處流覽車輛的各項功能。</span><span class="sxs-lookup"><span data-stu-id="3c78f-121">Later in the experience, the car expands to a larger scale (beyond the size of the device's field of view) but, since the user already acquired a frame of reference from the smaller model, they can adequately navigate around features of the car.</span></span><br>
        <br>
        <span data-ttu-id="3c78f-122">*影像： Volvo 適用于 HoloLens 的車輛體驗*</span><span class="sxs-lookup"><span data-stu-id="3c78f-122">*Image: Volvo Cars experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens 的 Volvo Cars 體驗](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a><span data-ttu-id="3c78f-124">使用全像影像來修改使用者的實際空間</span><span class="sxs-lookup"><span data-stu-id="3c78f-124">Use holograms to modify the user's real space</span></span>

<span data-ttu-id="3c78f-125">另一種方法是使用全像影像來修改使用者的實際空間、將現有的牆或上限取代成環境或附加「洞」或「windows」，讓過度調整大小的物件看似「細分」實體空間。</span><span class="sxs-lookup"><span data-stu-id="3c78f-125">Another method is to use holograms to modify the user's real space, replacing the existing walls or ceilings with environments or appending ‘holes’ or ‘windows’, allowing over-sized objects to seemingly 'break-through' the physical space.</span></span> <span data-ttu-id="3c78f-126">例如，大型樹狀結構可能無法容納大部分使用者的客廳，但藉由將虛擬天空放在最高的位置，實體空間就會擴展到虛擬。</span><span class="sxs-lookup"><span data-stu-id="3c78f-126">For example, a large tree might not fit in most users’ living rooms, but by putting a virtual sky on their ceiling, the physical space expands into the virtual.</span></span> <span data-ttu-id="3c78f-127">如此一來，使用者就可以逐步解說虛擬樹狀結構，並收集其在現實生活中的顯示方式，然後查閱以查看其延伸超過空間的實體空間。</span><span class="sxs-lookup"><span data-stu-id="3c78f-127">This allows the user to walk around the base of the virtual tree, and gather a sense of scale of how it would appear in real life, then look up to see it extend far beyond the physical space of the room.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3c78f-128">Minecraft 使用類似的技巧 **[開發了概念體驗](https://minecraft.net/)** 。</span><span class="sxs-lookup"><span data-stu-id="3c78f-128">**[Minecraft developed a concept experiences](https://minecraft.net/)** using a similar technique.</span></span> <span data-ttu-id="3c78f-129">藉由將虛擬視窗新增至房間內的實體介面，房間內的現有物件就會放在極大的環境內容中，而不是空間的實體規模限制。</span><span class="sxs-lookup"><span data-stu-id="3c78f-129">By adding a virtual window to a physical surface in a room, the existing objects in the room are placed in the context of a vastly larger environment, beyond the physical scale limitations of the room.</span></span><br>
        <br>
        <span data-ttu-id="3c78f-130">*影像： Minecraft 適用于 HoloLens 的概念體驗*</span><span class="sxs-lookup"><span data-stu-id="3c78f-130">*Image: Minecraft concept experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens 的 Minecraft 概念體驗](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a><span data-ttu-id="3c78f-132">使用 scale 進行實驗</span><span class="sxs-lookup"><span data-stu-id="3c78f-132">Experimenting with scale</span></span>

<span data-ttu-id="3c78f-133">在某些情況下，設計人員會實驗修改尺規 (，方法是變更顯示的物件) 的「實際」大小，同時維持物件的單一位置，以接近接近或更接近檢視器的物件，而不需要實際移動。</span><span class="sxs-lookup"><span data-stu-id="3c78f-133">In some cases, designers have experimented with modifying the scale (by changing the displayed ‘real’ size of the object) while maintaining a single position of the object, to approximate an object getting closer or further to a viewer without any actual movement.</span></span> <span data-ttu-id="3c78f-134">在某些情況下，這是在某些情況下進行測試，以模擬關閉專案的功能，同時仍遵守觀看虛擬內容的可能緩和限制，而接近「緩和區域」的建議。</span><span class="sxs-lookup"><span data-stu-id="3c78f-134">This was tested in some cases as a way to simulate up-close viewing of items while still respecting potential comfort limitations of viewing virtual content closer than the “zone of comfort” would suggest.</span></span>

<span data-ttu-id="3c78f-135">不過，這可能會在體驗中建立一些可能的構件：</span><span class="sxs-lookup"><span data-stu-id="3c78f-135">This can create a few possible artifacts in the experience however:</span></span>
* <span data-ttu-id="3c78f-136">如果虛擬物件代表的某個物件具有「已知」大小的檢視器，則在不變更位置的情況下，變更縮放比例會導致視覺提示衝突，而眼睛可能仍會因為 vergence 提示而「查看」物件，但在 [)  (提示](comfort.md) 的情況下，可能仍會顯示物件，但大小會作為 monocular 提示，表示物件可能會更接近。</span><span class="sxs-lookup"><span data-stu-id="3c78f-136">For virtual objects that represent some object with a ‘known’ size to the viewer, changing the scale without changing the position leads to conflicting visual cues – the eyes may still ‘see’ the object at some depth due to vergence cues (see the [Comfort](comfort.md) article for more on this), but the size acts as a monocular cue that the object might be getting closer.</span></span> <span data-ttu-id="3c78f-137">這些衝突的提示會導致混淆的理解，因此，檢視器通常會將物件視為保持 (，因為有常數深度的提示) 但很快就會成長。</span><span class="sxs-lookup"><span data-stu-id="3c78f-137">These conflicting cues lead to confused perceptions – viewers often see the object as staying in place (due to the constant depth cue) but growing rapidly.</span></span>
* <span data-ttu-id="3c78f-138">在某些情況下，小數位數的變更會被視為「即將問世」提示，其中物件可能會或可能不會被檢視器變更，但似乎是直接移到檢視器的眼睛 (這可能是令人感到不安的刺痛) 。</span><span class="sxs-lookup"><span data-stu-id="3c78f-138">In some cases, change of scale is seen as a ‘looming’ cue instead, where the object may or may not be seen to change scale by a viewer, but does appear to be moving directly toward the viewer’s eyes (which can be an uncomfortable sensation).</span></span>
* <span data-ttu-id="3c78f-139">在真實世界中的比較介面上，這類調整變更有時會被視為沿著多個軸變化的位置，在某些情況下，物件可能會顯得較低，而不是移動較接近的 (類似于3D 移動的2D 投影中) 。</span><span class="sxs-lookup"><span data-stu-id="3c78f-139">With comparison surfaces in the real world, such scaling changes are sometimes seen as changing position along multiple axes – objects may appear to drop lower instead of moving closer (similar in a 2D projection of 3D movement in some cases).</span></span>
* <span data-ttu-id="3c78f-140">最後，對於沒有已知「真實世界」大小的物件 (例如任意大小、UI 元素 ) 等等的任意形狀），變更尺規的功能可能會以模擬距離變更的方式運作，因此，檢視器不會有許多預先存在的由上而下的提示，可瞭解物件的真正大小或位置，因此可以將比例視為更重要的提示來處理。</span><span class="sxs-lookup"><span data-stu-id="3c78f-140">Finally, for objects without a known ‘real world’ size (e.g. arbitrary shapes with arbitrary sizes, UI elements, etc.), changing scale may act functionally as a way to mimic changes in distance – viewers do not have as many preexisting top-down cues by which to understand the object’s true size or location, so the scale can be processed as a more important cue.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="3c78f-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c78f-141">See also</span></span>
* [<span data-ttu-id="3c78f-142">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="3c78f-142">Color, light and materials</span></span>](../color,-light-and-materials.md)
* [<span data-ttu-id="3c78f-143">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="3c78f-143">Typography</span></span>](typography.md)
* [<span data-ttu-id="3c78f-144">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="3c78f-144">Spatial sound design</span></span>](spatial-sound-design.md)
