---
title: 3D 應用程式啟動程式設計指引
description: 3D 應用程式啟動器是使用者的混合現實房子中的「實體」物件，可選擇啟動應用程式。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、3D 應用程式啟動器、沉浸式耳機、即時立方體、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、UWP、Win32、光源、色彩
ms.openlocfilehash: a501b4bdc86df17f6d005c2f7ccf4fe6a94a4b43
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703474"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="4751e-104">3D 應用程式啟動程式設計指引</span><span class="sxs-lookup"><span data-stu-id="4751e-104">3D app launcher design guidance</span></span>

<span data-ttu-id="4751e-105">當您放入 Windows Mixed Reality 沉浸式 (VR) 耳機時，您會進入 Windows Mixed Reality 首頁，並以山脈和水 (的 cliff 來視覺化，不過您可以 [選擇其他環境，甚至建立自己的](../design/add-custom-home-environments.md)) 。</span><span class="sxs-lookup"><span data-stu-id="4751e-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](../design/add-custom-home-environments.md)).</span></span> <span data-ttu-id="4751e-106">在這個首頁的空間內，使用者可以自由排列和組織他們關心任何方式的3D 物件和應用程式。</span><span class="sxs-lookup"><span data-stu-id="4751e-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="4751e-107">**3d 應用程式啟動器** 是使用者的混合現實房子中的「實體」物件，可選擇啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="4751e-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="4751e-108">![範例： Floaty 鳥3D 應用程式啟動器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4751e-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4751e-109">*(虛構應用程式) 的 Floaty 鳥3D 應用程式啟動器範例*</span><span class="sxs-lookup"><span data-stu-id="4751e-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="4751e-110">3D 應用程式啟動器建立流程</span><span class="sxs-lookup"><span data-stu-id="4751e-110">3D app launcher creation process</span></span>

<span data-ttu-id="4751e-111">建立3D 應用程式啟動器有3個步驟：</span><span class="sxs-lookup"><span data-stu-id="4751e-111">There are 3 steps to creating a 3D app launcher:</span></span>

1. <span data-ttu-id="4751e-112">設計和 concepting (本文) </span><span class="sxs-lookup"><span data-stu-id="4751e-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="4751e-113">模型化和匯出</span><span class="sxs-lookup"><span data-stu-id="4751e-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="4751e-114">將它整合到您的應用程式中：</span><span class="sxs-lookup"><span data-stu-id="4751e-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="4751e-115">UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="4751e-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="4751e-116">Win32 應用程式</span><span class="sxs-lookup"><span data-stu-id="4751e-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="4751e-117">設計概念</span><span class="sxs-lookup"><span data-stu-id="4751e-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="4751e-118">太棒了</span><span class="sxs-lookup"><span data-stu-id="4751e-118">Fantastic yet familiar</span></span>

<span data-ttu-id="4751e-119">您的應用程式啟動器所居住的 Windows Mixed Reality 環境，是 fantastical/科幻的一部分。</span><span class="sxs-lookup"><span data-stu-id="4751e-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="4751e-120">最佳的啟動器會遵循此世界的規則。</span><span class="sxs-lookup"><span data-stu-id="4751e-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="4751e-121">您可以想要如何從您的應用程式中取得熟悉的代表性物件，但是將一些實際現實的規則折到最多。</span><span class="sxs-lookup"><span data-stu-id="4751e-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="4751e-122">魔術將會產生。</span><span class="sxs-lookup"><span data-stu-id="4751e-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="4751e-123">直觀</span><span class="sxs-lookup"><span data-stu-id="4751e-123">Intuitive</span></span>

<span data-ttu-id="4751e-124">當您查看您的應用程式啟動程式時，其目的是要啟動您的應用程式，應該很明顯且不會造成任何混淆。</span><span class="sxs-lookup"><span data-stu-id="4751e-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="4751e-125">例如，請確定您的啟動器是您應用程式的明確代表，不會與懸崖之屋中的某一段 décor 混淆。</span><span class="sxs-lookup"><span data-stu-id="4751e-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="4751e-126">您的應用程式啟動程式應邀請人員觸控/選取它。</span><span class="sxs-lookup"><span data-stu-id="4751e-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="4751e-127">![範例：全新附注3D 應用程式啟動器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4751e-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4751e-128">*全新附注3D 應用程式啟動器範例 (虛構應用程式)*</span><span class="sxs-lookup"><span data-stu-id="4751e-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="4751e-129">首頁規模</span><span class="sxs-lookup"><span data-stu-id="4751e-129">Home scale</span></span>

<span data-ttu-id="4751e-130">3D 應用程式啟動器會存留在懸崖之屋中，而且其預設大小應該與空間中的其他「實體」物件有意義。</span><span class="sxs-lookup"><span data-stu-id="4751e-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="4751e-131">如果您將啟動器放置在房屋工廠或某些傢俱旁邊，則應該在家裡、大小調整。</span><span class="sxs-lookup"><span data-stu-id="4751e-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="4751e-132">一個不錯的起點是查看它看起來如何查看30個三分，但是請記住，使用者可以視需要擴大或縮小。</span><span class="sxs-lookup"><span data-stu-id="4751e-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="4751e-133">擁有能力</span><span class="sxs-lookup"><span data-stu-id="4751e-133">Own-able</span></span>

<span data-ttu-id="4751e-134">應用程式啟動程式應該會像是某個人很高興在其空間中擁有的物件。</span><span class="sxs-lookup"><span data-stu-id="4751e-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="4751e-135">它們幾乎都是以這些專案為其本身，因此啟動器應該會像是使用者認為需要足夠的東西，以找出並保持在附近。</span><span class="sxs-lookup"><span data-stu-id="4751e-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="4751e-136">![範例： Astro 變形3D 應用程式啟動器](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4751e-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4751e-137">*Astro (虛構應用程式) 的變形3D 應用程式啟動器範例*</span><span class="sxs-lookup"><span data-stu-id="4751e-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="4751e-138">識別</span><span class="sxs-lookup"><span data-stu-id="4751e-138">Recognizable</span></span>

<span data-ttu-id="4751e-139">您的3D 應用程式啟動器應該會立即將「您的應用程式品牌」表達給看到該應用程式的人員。</span><span class="sxs-lookup"><span data-stu-id="4751e-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="4751e-140">如果您的應用程式中有星號字元或特別可識別的物件，我們建議您在設計中使用該字元。</span><span class="sxs-lookup"><span data-stu-id="4751e-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="4751e-141">在混合現實世界中，物件會比單獨的標誌更吸引使用者。</span><span class="sxs-lookup"><span data-stu-id="4751e-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="4751e-142">可辨識的物件會快速且清楚地傳達品牌。</span><span class="sxs-lookup"><span data-stu-id="4751e-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="4751e-143">體積</span><span class="sxs-lookup"><span data-stu-id="4751e-143">Volumetric</span></span>

<span data-ttu-id="4751e-144">您的應用程式不只是將您的標誌放在平面平面上，還需要一天的時間來呼叫它。</span><span class="sxs-lookup"><span data-stu-id="4751e-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="4751e-145">您的啟動器應該會像是使用者空間中令人興奮的立體實體物件。</span><span class="sxs-lookup"><span data-stu-id="4751e-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="4751e-146">最好的方法是想像您的應用程式在 Macy 的感恩節日行列中將會有一個球形球。</span><span class="sxs-lookup"><span data-stu-id="4751e-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="4751e-147">問您自己，為什麼會讓人們看到街道？</span><span class="sxs-lookup"><span data-stu-id="4751e-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="4751e-148">所有的觀賞角度看起來很棒嗎？</span><span class="sxs-lookup"><span data-stu-id="4751e-148">What would look great from all viewing angles?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="4751e-149">![僅限標誌 ](images/20171016-140436-mixedreality-640px.jpg) *標誌*</span><span class="sxs-lookup"><span data-stu-id="4751e-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4751e-150">![使用 ](images/20171016-140557-mixedreality-640px.jpg) *字元更容易辨識* 的字元更容易辨識</span><span class="sxs-lookup"><span data-stu-id="4751e-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="4751e-151">![一般方法（非驚訝）感覺一般一般 ](images/20171016-155101-mixedreality-640px.jpg) *方法，而非驚訝地感覺* 一般</span><span class="sxs-lookup"><span data-stu-id="4751e-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4751e-152">![體積型方法更能展現您的應用程式 ](images/20171016-161407-mixedreality-640px.jpg) *體積型方法，讓您的應用程式更清楚展示*</span><span class="sxs-lookup"><span data-stu-id="4751e-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a><span data-ttu-id="4751e-153">良好3D 模型的秘訣</span><span class="sxs-lookup"><span data-stu-id="4751e-153">Tips for good 3D models</span></span>

* <span data-ttu-id="4751e-154">規劃應用程式啟動程式的維度時，大約會針對 30cm cube 進行。</span><span class="sxs-lookup"><span data-stu-id="4751e-154">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="4751e-155">因此，1:1:1 大小的比率。</span><span class="sxs-lookup"><span data-stu-id="4751e-155">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="4751e-156">模型必須在10000多邊形下。</span><span class="sxs-lookup"><span data-stu-id="4751e-156">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="4751e-157">深入瞭解 (LODs 的三角形計數和詳細資料層級) </span><span class="sxs-lookup"><span data-stu-id="4751e-157">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="4751e-158">在沉浸式耳機上測試。</span><span class="sxs-lookup"><span data-stu-id="4751e-158">Test on an immersive headset.</span></span>
* <span data-ttu-id="4751e-159">盡可能在您的模型幾何中建立詳細資料–不依賴材質取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4751e-159">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="4751e-160">建立「水緊密」封閉幾何。</span><span class="sxs-lookup"><span data-stu-id="4751e-160">Build “water tight” closed geometry.</span></span> <span data-ttu-id="4751e-161">沒有任何未模型化的漏洞。</span><span class="sxs-lookup"><span data-stu-id="4751e-161">No holes that are not modeled in.</span></span>
* <span data-ttu-id="4751e-162">在您的物件中使用自然材質。</span><span class="sxs-lookup"><span data-stu-id="4751e-162">Use natural materials in your object.</span></span> <span data-ttu-id="4751e-163">想像一下在現實世界中製作它。</span><span class="sxs-lookup"><span data-stu-id="4751e-163">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="4751e-164">確定您的模型在不同的距離和大小都能妥善閱讀。</span><span class="sxs-lookup"><span data-stu-id="4751e-164">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="4751e-165">當您的模型已準備好開始時，請閱讀 [匯出資產的指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。</span><span class="sxs-lookup"><span data-stu-id="4751e-165">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="4751e-166">![材質中具有微妙詳細資料的模型](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4751e-166">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4751e-167">*材質中具有微妙詳細資料的模型*</span><span class="sxs-lookup"><span data-stu-id="4751e-167">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="4751e-168">避免事項</span><span class="sxs-lookup"><span data-stu-id="4751e-168">What to avoid</span></span>

* <span data-ttu-id="4751e-169">請勿使用高對比的詳細資料或小型、忙碌模式和紋理。</span><span class="sxs-lookup"><span data-stu-id="4751e-169">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="4751e-170">請勿使用精簡型幾何–它不會在某個距離正常運作，而且別名會不正確。</span><span class="sxs-lookup"><span data-stu-id="4751e-170">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="4751e-171">不要讓模型的某些部分延伸超過1:1:1 大小比例。</span><span class="sxs-lookup"><span data-stu-id="4751e-171">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="4751e-172">它會建立調整問題。</span><span class="sxs-lookup"><span data-stu-id="4751e-172">It will create scaling problems.</span></span>

<span data-ttu-id="4751e-173">![避免高對比、小型忙碌模式](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4751e-173">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4751e-174">*避免高對比、小型、忙碌模式*</span><span class="sxs-lookup"><span data-stu-id="4751e-174">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="4751e-175">如何處理類型</span><span class="sxs-lookup"><span data-stu-id="4751e-175">How to handle type</span></span>

* <span data-ttu-id="4751e-176">我們建議您的類型包含應用程式啟動器的 1/3 (或更) 。</span><span class="sxs-lookup"><span data-stu-id="4751e-176">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="4751e-177">型別是讓人們知道您的啟動器實際上是啟動程式的主要事物，所以如果它很大，就很好用。</span><span class="sxs-lookup"><span data-stu-id="4751e-177">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="4751e-178">避免將類型設為寬度-請嘗試將其保留在應用程式啟動器核心維度的範圍內 (更多或更少) 。</span><span class="sxs-lookup"><span data-stu-id="4751e-178">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="4751e-179">一般類型可以運作，但請注意，在某些環境中，可能很難查看。</span><span class="sxs-lookup"><span data-stu-id="4751e-179">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="4751e-180">您可以考慮將它放在其背後的穩固物件或背後，以協助進行此工作。</span><span class="sxs-lookup"><span data-stu-id="4751e-180">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="4751e-181">將維度加入至您的型別在3D 中感覺很不錯。</span><span class="sxs-lookup"><span data-stu-id="4751e-181">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="4751e-182">將類型的側邊著色為不同、較深色的色彩有助於可讀性。</span><span class="sxs-lookup"><span data-stu-id="4751e-182">Shading the sides of the type a different, darker color can help with readability.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="4751e-183">![沒有背景的平面類型可能難以從特定角度進行查看，而在某些環境中， ](images/flattype-640px.png) *沒有任何背景的平面類型可能難以從特定角度和某些環境中查看*</span><span class="sxs-lookup"><span data-stu-id="4751e-183">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4751e-184">![具有內建圖的型別可以正常運作 ](images/flattypeandbkg-640px.png) *，而且內建的背景可以正常運作*</span><span class="sxs-lookup"><span data-stu-id="4751e-184">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="4751e-185">![如果您將側邊的拉伸類型加上陰影，則 ](images/20171016-160221-mixedreality-640px.jpg) *如果您將側邊加上陰影*，則拉伸類型可以正常運作</span><span class="sxs-lookup"><span data-stu-id="4751e-185">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="4751e-186">**輸入可運作的色彩**</span><span class="sxs-lookup"><span data-stu-id="4751e-186">**Type colors that work**</span></span>

* <span data-ttu-id="4751e-187">白色</span><span class="sxs-lookup"><span data-stu-id="4751e-187">White</span></span>
* <span data-ttu-id="4751e-188">黑色</span><span class="sxs-lookup"><span data-stu-id="4751e-188">Black</span></span>
* <span data-ttu-id="4751e-189">亮色半形色彩</span><span class="sxs-lookup"><span data-stu-id="4751e-189">Bright semi-saturated color</span></span>

<span data-ttu-id="4751e-190">![輸入可運作的色彩。](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4751e-190">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4751e-191">*輸入可運作的色彩*</span><span class="sxs-lookup"><span data-stu-id="4751e-191">*Type colors that work*</span></span>

### <a name="colors-to-avoid"></a><span data-ttu-id="4751e-192">要避免的色彩</span><span class="sxs-lookup"><span data-stu-id="4751e-192">Colors to avoid</span></span>

<span data-ttu-id="4751e-193">造成問題的類型色彩包括：</span><span class="sxs-lookup"><span data-stu-id="4751e-193">Type colors that cause trouble include:</span></span>

* <span data-ttu-id="4751e-194">中音調</span><span class="sxs-lookup"><span data-stu-id="4751e-194">Mid-tones</span></span>
* <span data-ttu-id="4751e-195">灰色</span><span class="sxs-lookup"><span data-stu-id="4751e-195">Gray</span></span>
* <span data-ttu-id="4751e-196">過度飽和色彩或 desaturated 色彩</span><span class="sxs-lookup"><span data-stu-id="4751e-196">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="4751e-197">![造成問題的類型色彩。](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4751e-197">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4751e-198">*造成問題的類型色彩*</span><span class="sxs-lookup"><span data-stu-id="4751e-198">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="4751e-199">光源</span><span class="sxs-lookup"><span data-stu-id="4751e-199">Lighting</span></span>

<span data-ttu-id="4751e-200">應用程式啟動程式的光源來自懸崖之屋環境。</span><span class="sxs-lookup"><span data-stu-id="4751e-200">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="4751e-201">請務必在整個單元中的數個位置測試您的啟動程式，讓它在燈光和遮蔽中都能美觀。</span><span class="sxs-lookup"><span data-stu-id="4751e-201">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="4751e-202">好消息是，如果您已遵循本檔中的其他設計指導方針，則您的啟動程式應該會相當適合懸崖之屋中的大部分光源。</span><span class="sxs-lookup"><span data-stu-id="4751e-202">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="4751e-203">測試啟動程式如何在環境中的各種燈光中尋找的好地方，就是 Studio、媒體室、外部和後 Patio 的任何地方， (具有草坪) 的具體區域。</span><span class="sxs-lookup"><span data-stu-id="4751e-203">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="4751e-204">另一個不錯的測試是把它放在半淺色和半影子，看看它的樣子。</span><span class="sxs-lookup"><span data-stu-id="4751e-204">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="4751e-205">![確定您的啟動器在燈光和遮蔽中都看起來不錯。](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4751e-205">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4751e-206">*確定您的啟動器在燈光和遮蔽中都很美觀*</span><span class="sxs-lookup"><span data-stu-id="4751e-206">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="4751e-207">紋理</span><span class="sxs-lookup"><span data-stu-id="4751e-207">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="4751e-208">撰寫您的材質</span><span class="sxs-lookup"><span data-stu-id="4751e-208">Authoring your textures</span></span>

<span data-ttu-id="4751e-209">您3D 應用程式啟動器的結束格式將會是 glb 檔案，這是使用 .PBR (實際轉譯) 管線所建立。</span><span class="sxs-lookup"><span data-stu-id="4751e-209">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="4751e-210">這可能是一項複雜的程式，如果您還沒有這麼做，現在是使用技術演出者的好時機。</span><span class="sxs-lookup"><span data-stu-id="4751e-210">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="4751e-211">如果您是美麗 DIY-er，請花時間 [研究並學習 .pbr 的術語](https://wiki.polycount.com/wiki/PBR) ，以及開始之前的幕後工作，將可協助您避免常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4751e-211">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="4751e-212">![範例：全新的備註應用程式](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="4751e-212">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="4751e-213">*全新附注3D 應用程式啟動器範例 (虛構應用程式)*</span><span class="sxs-lookup"><span data-stu-id="4751e-213">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="recommended-authoring-tool"></a><span data-ttu-id="4751e-214">建議的 authoring tool</span><span class="sxs-lookup"><span data-stu-id="4751e-214">Recommended authoring tool</span></span>

<span data-ttu-id="4751e-215">我們建議 Allegorithmic 使用「 [物質刷](https://www.allegorithmic.com/products/substance-painter) 」來撰寫您的最終檔案。</span><span class="sxs-lookup"><span data-stu-id="4751e-215">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="4751e-216">如果您不熟悉如何在物質刷中撰寫 .PBR 著色器，請參閱以下 [教學](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)課程。</span><span class="sxs-lookup"><span data-stu-id="4751e-216">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="4751e-217">如果您更熟悉上述其中一項，則 ([Coat](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)或 [Marmoset Toolbag](https://www.marmoset.co/toolbag/) 也可以使用。 ) </span><span class="sxs-lookup"><span data-stu-id="4751e-217">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="4751e-218">最佳作法</span><span class="sxs-lookup"><span data-stu-id="4751e-218">Best practices</span></span>

* <span data-ttu-id="4751e-219">如果您的應用程式啟動器物件是針對 .PBR 而撰寫的，則將它轉換為懸崖之屋環境應該相當簡單。</span><span class="sxs-lookup"><span data-stu-id="4751e-219">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="4751e-220">我們的著色器預期會有金屬/粗糙度的工作流程– Unreal 的 .PBR 著色器是關閉的傳真。</span><span class="sxs-lookup"><span data-stu-id="4751e-220">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="4751e-221">匯出紋理時，請記住 [建議的材質大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 。</span><span class="sxs-lookup"><span data-stu-id="4751e-221">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="4751e-222">請務必為您的物件建立即時光源，這表示：</span><span class="sxs-lookup"><span data-stu-id="4751e-222">Make sure to build your objects for real-time lighting — this means:</span></span>
  * <span data-ttu-id="4751e-223">避免內建陰影-或繪製陰影</span><span class="sxs-lookup"><span data-stu-id="4751e-223">Avoid baked shadows – or painted shadows</span></span>
  * <span data-ttu-id="4751e-224">避免紋理中的內建光源</span><span class="sxs-lookup"><span data-stu-id="4751e-224">Avoid baked lighting in the textures</span></span>
  * <span data-ttu-id="4751e-225">使用其中一個 .PBR 材質撰寫套件來取得為著色器產生的正確對應</span><span class="sxs-lookup"><span data-stu-id="4751e-225">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="4751e-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4751e-226">See also</span></span>

* [<span data-ttu-id="4751e-227">建立要在混合實境首頁中使用的3D 模型</span><span class="sxs-lookup"><span data-stu-id="4751e-227">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="4751e-228">實作 3D 應用程式啟動器 (UWP 應用程式)</span><span class="sxs-lookup"><span data-stu-id="4751e-228">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="4751e-229">實作 3D 應用程式啟動器 (Win32 應用程式)</span><span class="sxs-lookup"><span data-stu-id="4751e-229">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
