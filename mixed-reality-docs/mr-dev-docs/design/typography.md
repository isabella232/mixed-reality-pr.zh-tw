---
title: 印刷樣式
description: 文字是在您的應用程式體驗中傳遞資訊的重要元素。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、樣式、字型、印刷樣式、ui、ux、文字、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、HoloLens
ms.openlocfilehash: 09e0e6029011fdd7fda793f6b6645cb3744baa3b
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848142"
---
# <a name="typography"></a><span data-ttu-id="940ac-104">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="940ac-104">Typography</span></span>

![HoloLens 中的印刷樣式範例](images/typography-cover.png)<br>


<span data-ttu-id="940ac-106">文字是在您的應用程式體驗中傳遞資訊的重要元素。</span><span class="sxs-lookup"><span data-stu-id="940ac-106">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="940ac-107">就像2D 螢幕上的印刷樣式一樣，目標是要清楚易懂。</span><span class="sxs-lookup"><span data-stu-id="940ac-107">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="940ac-108">有了混合現實的三維層面，也有機會以更大的方式影響文字和整體使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="940ac-108">With the three-dimensional aspect of mixed reality, there's an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="940ac-109">當我們談到3D 中的型別時，我們傾向于將體積型的3D 文字視為已延伸。</span><span class="sxs-lookup"><span data-stu-id="940ac-109">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="940ac-110">除了部分商標設計和一些其他有限的應用程式以外，已拉伸的文字通常會降低文字的可讀性。</span><span class="sxs-lookup"><span data-stu-id="940ac-110">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="940ac-111">雖然我們正在設計3D 的體驗，但我們使用2D 作為型別，因為它比較清楚且更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="940ac-111">Even though we're designing experiences for 3D, we use 2D for the type because it's more legible and easier to read.</span></span>

<span data-ttu-id="940ac-112">在 HoloLens 中，類型是使用以加法色彩系統為基礎的輕量來建立。</span><span class="sxs-lookup"><span data-stu-id="940ac-112">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="940ac-113">就像其他的全像投影一樣，可以將型別放在實際的環境中，讓它可以從任何角度鎖定並觀察到。</span><span class="sxs-lookup"><span data-stu-id="940ac-113">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="940ac-114">型別和環境之間的 [視差](https://en.wikipedia.org/wiki/Parallax) 效果，也增加了體驗的深度。</span><span class="sxs-lookup"><span data-stu-id="940ac-114">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="940ac-115">混合現實中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="940ac-115">Typography in mixed reality</span></span>

<span data-ttu-id="940ac-116">混合現實中的印刷樣式規則與其他任何地方都沒有不同。</span><span class="sxs-lookup"><span data-stu-id="940ac-116">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="940ac-117">實體世界和虛擬世界中的文字都必須能夠清楚且容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="940ac-117">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="940ac-118">文字可以在牆上或在實體物件上重迭。</span><span class="sxs-lookup"><span data-stu-id="940ac-118">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="940ac-119">它可以與數位使用者介面一起浮動。</span><span class="sxs-lookup"><span data-stu-id="940ac-119">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="940ac-120">無論何種內容，我們都會套用相同的印刷樣式規則來進行讀取和辨識。</span><span class="sxs-lookup"><span data-stu-id="940ac-120">Whatever the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="940ac-121">建立明確階層</span><span class="sxs-lookup"><span data-stu-id="940ac-121">Create clear hierarchy</span></span>

<span data-ttu-id="940ac-122">使用不同的類型大小和加權來建立對比和階層。</span><span class="sxs-lookup"><span data-stu-id="940ac-122">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="940ac-123">在整個應用程式體驗中定義型別和之後，將可提供一致的資訊階層，提供絕佳的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="940ac-123">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="940ac-124">![輸入逐漸增加的範例](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="940ac-124">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="940ac-125">*定義您的型別，並在整個應用程式體驗中追蹤*</span><span class="sxs-lookup"><span data-stu-id="940ac-125">*Define your type ramp and follow it throughout the app experience*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="940ac-126">限制字型</span><span class="sxs-lookup"><span data-stu-id="940ac-126">Limit your fonts</span></span>

<span data-ttu-id="940ac-127">避免在單一內容中使用兩個以上的不同字型系列。</span><span class="sxs-lookup"><span data-stu-id="940ac-127">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="940ac-128">太多字型會中斷您的體驗的顏色與一致性，並使其更難以取用資訊。</span><span class="sxs-lookup"><span data-stu-id="940ac-128">Too many fonts will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="940ac-129">在 HoloLens 中，由於資訊是在實體環境的最上層進行重迭，因此使用太多字型樣式將會降低體驗。</span><span class="sxs-lookup"><span data-stu-id="940ac-129">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="940ac-130">Segoe UI 是所有 Microsoft 數位設計的字型。</span><span class="sxs-lookup"><span data-stu-id="940ac-130">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="940ac-131">它會在 Windows Mixed Reality shell 中一致地使用。</span><span class="sxs-lookup"><span data-stu-id="940ac-131">It's used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="940ac-132">您可以從 [Windows 設計工具組頁面](https://docs.microsoft.com/windows/uwp/design-downloads/)下載 Segoe UI 字型檔案。</span><span class="sxs-lookup"><span data-stu-id="940ac-132">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="940ac-133">Segoe UI 字樣的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="940ac-133">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="940ac-134">避免細字型粗細</span><span class="sxs-lookup"><span data-stu-id="940ac-134">Avoid thin font weights</span></span>

<span data-ttu-id="940ac-135">請避免針對 42 pt 的類型大小使用淺色或 semilight 做字型粗細，因為精簡型垂直筆觸會震動並降低可讀性。</span><span class="sxs-lookup"><span data-stu-id="940ac-135">Avoid using light or semilight font weights for type sizes under 42 pt because thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="940ac-136">具有足夠筆觸粗細的新式字型可正常運作。</span><span class="sxs-lookup"><span data-stu-id="940ac-136">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="940ac-137">例如，使用標準或粗體權數，HoloLens 中的 Helvetica 和 Arial 可以清晰地顯示。</span><span class="sxs-lookup"><span data-stu-id="940ac-137">For example, Helvetica and Arial are legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="940ac-138">Color</span><span class="sxs-lookup"><span data-stu-id="940ac-138">Color</span></span>

<span data-ttu-id="940ac-139">在 HoloLens 中，因為全像是以加總的燈光系統來建造全像系統，所以白色文字很清晰。</span><span class="sxs-lookup"><span data-stu-id="940ac-139">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="940ac-140">您可以在 [開始] 功能表和應用程式行中找到白色文字的範例。</span><span class="sxs-lookup"><span data-stu-id="940ac-140">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="940ac-141">即使白色文字在 HoloLens 沒有背面的情況下正常運作，但複雜的實體背景也可能使類型難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="940ac-141">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="940ac-142">我們建議您在深色或彩色背板上使用白色文字，以改善使用者的焦點，並將實體背景的干擾降至最低。</span><span class="sxs-lookup"><span data-stu-id="940ac-142">We recommend using white text on a dark or colored back plate to improve the user's focus and minimize the distraction from a physical background.</span></span>

<br>


<span data-ttu-id="940ac-143">![建議您在深色或彩色背板上使用白色文字。 ](images/typography-whiteonblack2-1000px.jpg)
*深色或彩色背板上的白色文字範例。*</span><span class="sxs-lookup"><span data-stu-id="940ac-143">![We recommend using white text on a dark or colored back plate.](images/typography-whiteonblack2-1000px.jpg)
*Examples of white text on a dark or colored back plate.*</span></span>
<br>

<span data-ttu-id="940ac-144">若要使用深色文字，您應該使用較佳的背板讓它變成可讀取。</span><span class="sxs-lookup"><span data-stu-id="940ac-144">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="940ac-145">在 [加法色彩系統] 中，黑色會顯示為透明。</span><span class="sxs-lookup"><span data-stu-id="940ac-145">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="940ac-146">這表示不會在沒有彩色背面的情況下看見黑色文字。</span><span class="sxs-lookup"><span data-stu-id="940ac-146">This means you won't see the black text without a colored back plate.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="940ac-147">![白色文字上黑色和黑色的白色範例](images/typography-whiteonblack.png)</span><span class="sxs-lookup"><span data-stu-id="940ac-147">![Examples of white on black and black on white text](images/typography-whiteonblack.png)</span></span><br>
        <span data-ttu-id="940ac-148">*白色文字上黑色和黑色的白色範例*</span><span class="sxs-lookup"><span data-stu-id="940ac-148">*Examples of white on black and black on white text*</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="940ac-149">![系統應用程式中的黑色文字範例-儲存和設定](images/640px-typography-blackonwhite.jpg)</span><span class="sxs-lookup"><span data-stu-id="940ac-149">![Examples of black text in the system apps - Store and Settings](images/640px-typography-blackonwhite.jpg)</span></span><br>
        <span data-ttu-id="940ac-150">*系統應用程式中的黑色文字範例-儲存和設定*</span><span class="sxs-lookup"><span data-stu-id="940ac-150">*Examples of black text in the system apps - Store and Settings*</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a><span data-ttu-id="940ac-151">建議的字型大小</span><span class="sxs-lookup"><span data-stu-id="940ac-151">Recommended font size</span></span>

<span data-ttu-id="940ac-152">如您所見，我們在電腦或 (平板電腦上使用的類型大小，通常是在12–32pt 填補) 在兩個度量之間的距離，通常介於12到。</span><span class="sxs-lookup"><span data-stu-id="940ac-152">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look small at a distance of 2 meters.</span></span> <span data-ttu-id="940ac-153">這取決於每個字型的特性，但在一般情況下，建議的最小觀賞角度和字型高度會根據我們的使用者研究研究，在0.35 °-0.4 °/12.21 13.97 mm 周圍。</span><span class="sxs-lookup"><span data-stu-id="940ac-153">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97 mm based on our user research studies.</span></span> <span data-ttu-id="940ac-154">這大約是 35-40 pt，且在 Unity 頁面的 [文字中](../develop/unity/text-in-unity.md) 引進了比例因素。</span><span class="sxs-lookup"><span data-stu-id="940ac-154">It's about 35-40 pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md) page.</span></span> 

<span data-ttu-id="940ac-155">針對在 0.45 m (45 cm) 的近距離互動，最小的可辨認字型的觀賞角度和高度是0.4 °-0.5 °/3.14 – 3.9 mm。</span><span class="sxs-lookup"><span data-stu-id="940ac-155">For the near interaction at 0.45 m(45 cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="940ac-156">這大約是在 [Unity 的文字中](../develop/unity/text-in-unity.md)引進的縮放因數 9-12 pt。</span><span class="sxs-lookup"><span data-stu-id="940ac-156">It's about 9-12 pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md).</span></span>

<span data-ttu-id="940ac-157">![近距離與遠距離互動範圍的互動範圍 ](images/typography-distance-1000px.jpg)
 *內容*</span><span class="sxs-lookup"><span data-stu-id="940ac-157">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="940ac-158">最小清晰度的字型大小</span><span class="sxs-lookup"><span data-stu-id="940ac-158">The minimum legible font size</span></span>

| <span data-ttu-id="940ac-159">距離</span><span class="sxs-lookup"><span data-stu-id="940ac-159">Distance</span></span> | <span data-ttu-id="940ac-160">視角</span><span class="sxs-lookup"><span data-stu-id="940ac-160">Viewing angle</span></span> | <span data-ttu-id="940ac-161">文字高度</span><span class="sxs-lookup"><span data-stu-id="940ac-161">Text height</span></span> | <span data-ttu-id="940ac-162">字型大小 \* \*</span><span class="sxs-lookup"><span data-stu-id="940ac-162">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="940ac-163">45 cm (直接操作距離) </span><span class="sxs-lookup"><span data-stu-id="940ac-163">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="940ac-164">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="940ac-164">0.4°-0.5°</span></span> | <span data-ttu-id="940ac-165">3.14 –3.9 分鐘</span><span class="sxs-lookup"><span data-stu-id="940ac-165">3.14–3.9mm</span></span> | <span data-ttu-id="940ac-166">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="940ac-166">8.9–11.13pt</span></span> |
| <span data-ttu-id="940ac-167">2分鐘</span><span class="sxs-lookup"><span data-stu-id="940ac-167">2 m</span></span> | <span data-ttu-id="940ac-168">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="940ac-168">0.35°-0.4°</span></span> | <span data-ttu-id="940ac-169">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="940ac-169">12.21–13.97mm</span></span> | <span data-ttu-id="940ac-170">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="940ac-170">34.63-39.58 pt</span></span> |

### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="940ac-171">方便閱讀的字型大小</span><span class="sxs-lookup"><span data-stu-id="940ac-171">The comfortably legible font size</span></span>

| <span data-ttu-id="940ac-172">距離</span><span class="sxs-lookup"><span data-stu-id="940ac-172">Distance</span></span> | <span data-ttu-id="940ac-173">視角</span><span class="sxs-lookup"><span data-stu-id="940ac-173">Viewing angle</span></span> | <span data-ttu-id="940ac-174">文字高度</span><span class="sxs-lookup"><span data-stu-id="940ac-174">Text height</span></span> | <span data-ttu-id="940ac-175">字型大小 \* \*</span><span class="sxs-lookup"><span data-stu-id="940ac-175">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="940ac-176">45 cm (直接操作距離) </span><span class="sxs-lookup"><span data-stu-id="940ac-176">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="940ac-177">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="940ac-177">0.65°-0.8°</span></span> | <span data-ttu-id="940ac-178">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="940ac-178">5.1-6.3 mm</span></span> | <span data-ttu-id="940ac-179">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="940ac-179">14.47-17.8 pt</span></span> |
| <span data-ttu-id="940ac-180">2分鐘</span><span class="sxs-lookup"><span data-stu-id="940ac-180">2 m</span></span> | <span data-ttu-id="940ac-181">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="940ac-181">0.6°-0.75°</span></span> | <span data-ttu-id="940ac-182">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="940ac-182">20.9-26.2 mm</span></span> | <span data-ttu-id="940ac-183">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="940ac-183">59.4-74.2 pt</span></span> |


<span data-ttu-id="940ac-184">Segoe UI (Windows) 的預設字型在大部分情況下都能順利運作。</span><span class="sxs-lookup"><span data-stu-id="940ac-184">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="940ac-185">請避免使用較小的淺色或半淺色字型系列，因為精簡型垂直筆觸會震動，而且會降低可讀性。</span><span class="sxs-lookup"><span data-stu-id="940ac-185">Avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="940ac-186">具有足夠筆觸粗細的新式字型可正常運作。</span><span class="sxs-lookup"><span data-stu-id="940ac-186">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="940ac-187">例如，Helvetica 和 Arial 外觀美觀，而且在 HoloLens 中會使用一般或粗體權數來辨認。</span><span class="sxs-lookup"><span data-stu-id="940ac-187">For example, Helvetica and Arial look gorgeous and are legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="940ac-188">**如需 Unity 中文字大小計算的詳細資訊，請參閱 [unity 中的文字](../develop/unity/text-in-unity.md)**</span><span class="sxs-lookup"><span data-stu-id="940ac-188">**For more detailed information about text size calculation in Unity, refer to [Text in Unity](../develop/unity/text-in-unity.md)**</span></span>

<span data-ttu-id="940ac-189">![視圖角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *觀賞距離、角度和文字高度*</span><span class="sxs-lookup"><span data-stu-id="940ac-189">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

<br>

---

## <a name="resources"></a><span data-ttu-id="940ac-190">資源</span><span class="sxs-lookup"><span data-stu-id="940ac-190">Resources</span></span>

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[<span data-ttu-id="940ac-191">Segoe 字型</span><span class="sxs-lookup"><span data-stu-id="940ac-191">Segoe fonts</span></span>](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    <span data-ttu-id="940ac-192"> (Zip 檔案) </span><span class="sxs-lookup"><span data-stu-id="940ac-192">(Zip file)</span></span><br>
    ### <a name="hololens-fontbr"></a>[<span data-ttu-id="940ac-193">HoloLens 字型</span><span class="sxs-lookup"><span data-stu-id="940ac-193">HoloLens font</span></span>](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    <span data-ttu-id="940ac-194"> (Zip 檔案) </span><span class="sxs-lookup"><span data-stu-id="940ac-194">(Zip file)</span></span><br>
    <br>
    <span data-ttu-id="940ac-195">*影像： HoloLens 字型提供 Windows Mixed Reality 中使用的符號圖像。*</span><span class="sxs-lookup"><span data-stu-id="940ac-195">*Image: The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.*</span></span>
    :::column-end:::
        :::column:::
        ![HoloLens 字型可提供您在 Windows Mixed Reality 中使用的符號字元](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a><span data-ttu-id="940ac-197">請參閱</span><span class="sxs-lookup"><span data-stu-id="940ac-197">See also</span></span>

* [<span data-ttu-id="940ac-198">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="940ac-198">Text in Unity</span></span>](../develop/unity/text-in-unity.md)
* [<span data-ttu-id="940ac-199">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="940ac-199">Color, light, and materials</span></span>](../color,-light-and-materials.md)
