---
title: 調整
description: 以全像攝影形式呈現看似逼真內容的關鍵，就是盡可能地模擬真實世界的視覺統計資料。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、樣式、設計、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、調整、全像影像
ms.openlocfilehash: 12b1c96146f76274831c9bc3427cef93bb326f70
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583309"
---
# <a name="scale"></a><span data-ttu-id="1cc6d-104">調整</span><span class="sxs-lookup"><span data-stu-id="1cc6d-104">Scale</span></span>

<span data-ttu-id="1cc6d-105">顯示逼真的全像攝影內容的關鍵是盡可能地模擬真實世界的視覺統計資料。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-105">The key to displaying realistic holographic content is mimicking the visual statistics of the real world as closely as possible.</span></span> <span data-ttu-id="1cc6d-106">納入視覺提示，以協助真實世界的使用者瞭解物件是什麼、它們有多大，以及它們的功能。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-106">Incorporate visual cues to help real-world users understand where objects are, how big they are, and what they’re made of.</span></span> <span data-ttu-id="1cc6d-107">物件的小數位數是其中一個最重要的視覺提示，因為它可讓檢視器瞭解物件大小以及其位置的提示。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-107">The scale of an object is one of the most important visual cues because it gives viewer a sense of the objects size and cues to its location.</span></span> <span data-ttu-id="1cc6d-108">此外，大規模地觀看物件是混合現實的主要體驗差異之一，也就是先前的螢幕式觀賞尚未可能發生的情況。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-108">Further, viewing objects at real scale is one of the key experience differentiators for mixed reality in general – something that hasn’t been possible on previous screen-based viewing.</span></span>

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a><span data-ttu-id="1cc6d-109">如何建議物件和環境的規模</span><span class="sxs-lookup"><span data-stu-id="1cc6d-109">How to suggest the scale of objects and environments</span></span>

<span data-ttu-id="1cc6d-110">有許多方式可以建議物件的小數位數，其中有些可能會影響其他可感知的因素。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-110">There are many ways to suggest the scale of an object, some of which have possible effects on other perceptual factors.</span></span> <span data-ttu-id="1cc6d-111">第一個按鍵是以「真實」大小顯示物件，並在使用者移動時維持實際大小。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-111">The key one is to display objects at a ‘real’ size, and maintain that realistic size as users move.</span></span> <span data-ttu-id="1cc6d-112">在使用者的視覺角度更近或更近或更近的情況下，全像是真實物件的方式。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-112">Holograms will take up a different amount of a user’s visual angle of a user as they come closer or further away, the same way that real objects do.</span></span>

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a><span data-ttu-id="1cc6d-113">使用物件在呈現給使用者時的距離</span><span class="sxs-lookup"><span data-stu-id="1cc6d-113">Use the distance of objects as they're presented to the user</span></span>

<span data-ttu-id="1cc6d-114">其中一個常見的方法是使用物件在呈現給使用者時的距離。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-114">One common method is to use the distance of objects as they're presented to the user.</span></span> <span data-ttu-id="1cc6d-115">例如，請考慮將大型家庭車輛視覺化到使用者前方。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-115">For example, consider visualizing a large family car in front of the user.</span></span> <span data-ttu-id="1cc6d-116">如果汽車在 arm 的長度內直接放在其前方，可能會太大而無法納入使用者的觀點。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-116">If the car was directly in front of them within arm’s length, it would be too large to fit in the user’s field of view.</span></span> <span data-ttu-id="1cc6d-117">關閉物件需要使用者移動其標頭和主體，才能瞭解整個物件。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-117">Close objects require the user to move their head and body to understand the entirety of the object.</span></span> <span data-ttu-id="1cc6d-118">如果車輛 (的房間) ，則使用者可以在其視野的欄位中查看整個物件，藉以建立規模的意義。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-118">If the car is placed further away (across the room), the user can establish a sense of scale by seeing the entire object in their field of view.</span></span> <span data-ttu-id="1cc6d-119">然後，使用者可以更接近物件，以進行更詳細的檢查。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-119">Users could then move themselves closer to the object for a more detailed inspection.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1cc6d-120">**[Volvo 使用這項技術來建立](https://www.youtube.com/watch?v=DilzwF90vec)** 新車輛的 showroom 體驗，並使用全像全像直覺的方式，利用全像直覺的方式來為使用者提供體驗。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-120">**[Volvo used this technique to create a showroom](https://www.youtube.com/watch?v=DilzwF90vec)** experience for a new car, using the scale of the holographic car in a way that felt realistic and intuitive to the user.</span></span> <span data-ttu-id="1cc6d-121">體驗是從實體資料表上的車輛全息表開始，讓使用者瞭解模型的總大小和形狀。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-121">The experience begins with the car hologram on a physical table, allowing the user to understand the total size and shape of the model.</span></span> <span data-ttu-id="1cc6d-122">稍後在此體驗中，汽車會擴充至超出裝置視野的大小。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-122">Later in the experience, the car expands to a scale beyond the size of the device's field of view.</span></span> <span data-ttu-id="1cc6d-123">因為使用者已從較小的模型取得參考的畫面格，所以可充分地四處流覽車輛的功能。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-123">Since the user already acquired a frame of reference from the smaller model, they can adequately navigate around features of the car.</span></span><br>
        <br>
        <span data-ttu-id="1cc6d-124">*影像： Volvo 適用于 HoloLens 的車輛體驗*</span><span class="sxs-lookup"><span data-stu-id="1cc6d-124">*Image: Volvo Cars experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens 的 Volvo Cars 體驗](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a><span data-ttu-id="1cc6d-126">使用全像影像來修改使用者的實際空間</span><span class="sxs-lookup"><span data-stu-id="1cc6d-126">Use holograms to modify the user's real space</span></span>

<span data-ttu-id="1cc6d-127">另一種方法是使用「全像」來修改使用者的實際空間，以環境或附加「洞」或「windows」取代現有的牆或上限。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-127">Another method is to use holograms to modify the user's real space, replacing the existing walls or ceilings with environments or appending ‘holes’ or ‘windows’.</span></span> <span data-ttu-id="1cc6d-128">這可讓過度調整大小的物件看似「細分」實體空間。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-128">This allows over-sized objects to seemingly 'break-through' the physical space.</span></span> <span data-ttu-id="1cc6d-129">例如，大型樹狀結構可能無法容納大部分使用者的客廳，但藉由將虛擬天空放在最高的位置，實體空間就會擴展到虛擬。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-129">For example, a large tree might not fit in most users’ living rooms, but by putting a virtual sky on their ceiling, the physical space expands into the virtual.</span></span> <span data-ttu-id="1cc6d-130">這可讓使用者流覽虛擬樹狀結構的基底，並收集規模和真實世界外觀的意義。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-130">This allows the user to walk around the base of the virtual tree and gather a sense of scale and real-world appearance.</span></span> <span data-ttu-id="1cc6d-131">然後，使用者可以查詢，看看它的範圍遠超過空間的實體空間。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-131">Users can then look up to see it extend far beyond the physical space of the room.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1cc6d-132">Minecraft 使用類似的技巧 **[開發了概念體驗](https://minecraft.net/)**。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-132">**[Minecraft developed a concept experiences](https://minecraft.net/)** using a similar technique.</span></span> <span data-ttu-id="1cc6d-133">藉由將虛擬視窗新增至實體介面，房間內的現有物件將會放在相當大的環境內容中，但不超過空間的實體規模限制。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-133">By adding a virtual window to a physical surface, the existing objects in the room are placed in the context of a vastly larger environment, beyond the physical scale limitations of the room.</span></span><br>
        <br>
        <span data-ttu-id="1cc6d-134">*影像： Minecraft 適用于 HoloLens 的概念體驗*</span><span class="sxs-lookup"><span data-stu-id="1cc6d-134">*Image: Minecraft concept experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens 的 Minecraft 概念體驗](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a><span data-ttu-id="1cc6d-136">使用 scale 進行實驗</span><span class="sxs-lookup"><span data-stu-id="1cc6d-136">Experimenting with scale</span></span>

<span data-ttu-id="1cc6d-137">設計人員實驗由變更物件的顯示「實際」大小來修改尺規。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-137">Designers have experimented with modifying the scale by changing the displayed ‘real’ size of the object.</span></span> <span data-ttu-id="1cc6d-138">同時，他們會維護單一物件位置，以接近移至檢視器的物件，而不需要實際移動。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-138">At the same time, they maintain a single object position to approximate an object moving towards the viewer without any actual movement.</span></span> <span data-ttu-id="1cc6d-139">在某些情況下，這是在某些情況下進行測試，以模擬關閉專案的功能，同時仍遵守觀看虛擬內容的可能緩和限制，而接近「緩和區域」的建議。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-139">This was tested in some cases as a way to simulate up-close viewing of items while still respecting potential comfort limitations of viewing virtual content closer than the “zone of comfort” would suggest.</span></span>

<span data-ttu-id="1cc6d-140">不過，這可能會在體驗中建立一些可能的構件：</span><span class="sxs-lookup"><span data-stu-id="1cc6d-140">This can create a few possible artifacts in the experience however:</span></span>
* <span data-ttu-id="1cc6d-141">如果虛擬物件代表的某個物件具有「已知」大小的檢視器，則變更調整規模而不變更位置會導致衝突的視覺提示。眼睛可能仍會因為 vergence 提示而「看到」物件的深度。如需詳細資訊，請參閱 [緩和](comfort.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-141">For virtual objects that represent some object with a ‘known’ size to the viewer, changing the scale without changing the position leads to conflicting visual cues. The eyes may still ‘see’ the object at some depth because of vergence cues. For more information, see the [Comfort](comfort.md) article.</span></span> <span data-ttu-id="1cc6d-142">大小會作為 monocular 提示，表示物件可能會更接近。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-142">The size acts as a monocular cue that the object might be getting closer.</span></span> <span data-ttu-id="1cc6d-143">這些衝突的提示會導致混淆的理解，因此，檢視器通常會將物件視為保持 (，因為會有常數深度的提示) 但很快就會成長。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-143">These conflicting cues lead to confused perceptions – viewers often see the object as staying in place (because of the constant depth cue) but growing rapidly.</span></span>
* <span data-ttu-id="1cc6d-144">在某些情況下，小數位數的變更會被視為「即將問世」提示，其中物件可能會或可能不會被檢視器變更，但似乎是直接移到檢視器的眼睛 (這可能是令人感到不安的刺痛) 。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-144">In some cases, change of scale is seen as a ‘looming’ cue instead, where the object may or may not be seen to change scale by a viewer, but does appear to be moving directly toward the viewer’s eyes (which can be an uncomfortable sensation).</span></span>
* <span data-ttu-id="1cc6d-145">在真實世界中的比較介面上，這類調整變更有時會被視為沿著多個軸變更位置，而在某些情況下，物件會顯得較低，而不是移動較接近的 (類似于3D 移動的2D 投影中) 。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-145">With comparison surfaces in the real world, such scaling changes are sometimes seen as changing position along multiple axes – objects appear to drop lower instead of moving closer (similar in a 2D projection of 3D movement in some cases).</span></span>
* <span data-ttu-id="1cc6d-146">最後，對於沒有已知「真實世界」大小的物件 (例如，具有任意大小、UI) 元素等等的任意圖案，變更調整的功能可能會以模擬距離變更的方式運作。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-146">Finally, for objects without a known ‘real world’ size (for example, arbitrary shapes with arbitrary sizes, UI elements, and so on), changing scale may act functionally as a way to mimic changes in distance.</span></span> <span data-ttu-id="1cc6d-147">檢視器不會有太多預先存在的由上而下提示，以瞭解物件的真正大小或位置，因此可以將比例視為更重要的提示來處理。</span><span class="sxs-lookup"><span data-stu-id="1cc6d-147">Viewers don't have as many pre-existing top-down cues to understand the object’s true size or location, so the scale can be processed as a more important cue.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="1cc6d-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cc6d-148">See also</span></span>
* [<span data-ttu-id="1cc6d-149">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="1cc6d-149">Color, light, and materials</span></span>](./color-light-and-materials.md)
* [<span data-ttu-id="1cc6d-150">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="1cc6d-150">Typography</span></span>](typography.md)
* [<span data-ttu-id="1cc6d-151">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="1cc6d-151">Spatial sound design</span></span>](spatial-sound-design.md)