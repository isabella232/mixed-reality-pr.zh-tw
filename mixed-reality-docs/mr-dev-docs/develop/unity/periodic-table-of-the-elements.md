---
title: 元素週期表
description: 專案的定期資料表是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式，您可以在其中學習如何使用物件集合，在3D 空間中設定物件陣列，以及各種表面類型。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、範例應用程式、控制項
ms.openlocfilehash: 2f7120aaf92a6e3d7b6ace301aae7392b67fa00b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91682504"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="a1211-104">元素週期表</span><span class="sxs-lookup"><span data-stu-id="a1211-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="a1211-105">本文討論我們在 [混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例，這是我們分享學習的地方，並提供混合現實應用程式開發的建議。</span><span class="sxs-lookup"><span data-stu-id="a1211-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="a1211-106">我們的設計相關文章和程式碼將隨著我們進行新探索而演進。</span><span class="sxs-lookup"><span data-stu-id="a1211-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="a1211-107">專案的[定期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1211-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="a1211-108">透過此專案，您可以瞭解如何使用 **[物件集合](../../design/object-collection.md)** ，在3d 空間中配置具有各種介面類別型的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="a1211-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)** .</span></span> <span data-ttu-id="a1211-109">同時瞭解如何建立互動物件，以回應 HoloLens 的標準輸入。</span><span class="sxs-lookup"><span data-stu-id="a1211-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="a1211-110">您可以使用此專案的元件來建立您自己的混合現實應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="a1211-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Elements 應用程式的期間資料表](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="a1211-112">關於應用程式</span><span class="sxs-lookup"><span data-stu-id="a1211-112">About the app</span></span>

<span data-ttu-id="a1211-113">專案的定期資料表會以3D 空間將化學元素和每個屬性視覺化。</span><span class="sxs-lookup"><span data-stu-id="a1211-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="a1211-114">它結合了 HoloLens 的基本互動，例如注視和點擊。</span><span class="sxs-lookup"><span data-stu-id="a1211-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="a1211-115">使用者可以使用動畫3D 模型來瞭解這些元素。</span><span class="sxs-lookup"><span data-stu-id="a1211-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="a1211-116">他們可以透過視覺化方式瞭解元素的 electron shell 及其系統核心（由 protons 和 neutrons 組成）。</span><span class="sxs-lookup"><span data-stu-id="a1211-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="a1211-117">背景</span><span class="sxs-lookup"><span data-stu-id="a1211-117">Background</span></span>

<span data-ttu-id="a1211-118">在我第一次體驗 HoloLens 之後，定期資料表應用程式就是我知道我想要在混合現實中進行實驗的概念。</span><span class="sxs-lookup"><span data-stu-id="a1211-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="a1211-119">由於每個專案都有許多以文字顯示的資料點，因此我認為在3D 空間中探索印刷樣式組合是很重要的主題。</span><span class="sxs-lookup"><span data-stu-id="a1211-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="a1211-120">能夠以視覺化方式呈現專案的 electron 模型是這個專案的另一個有趣的部分。</span><span class="sxs-lookup"><span data-stu-id="a1211-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="a1211-121">設計</span><span class="sxs-lookup"><span data-stu-id="a1211-121">Design</span></span>

<span data-ttu-id="a1211-122">針對定期資料表的預設視圖，我想要有三維方塊，其中包含每個元素的 electron 模型。</span><span class="sxs-lookup"><span data-stu-id="a1211-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="a1211-123">每個方塊的介面都是半透明的，讓使用者可以大致瞭解元素的音量。</span><span class="sxs-lookup"><span data-stu-id="a1211-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="a1211-124">使用者可以利用注視和空中來開啟每個元素的詳細觀點。</span><span class="sxs-lookup"><span data-stu-id="a1211-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="a1211-125">為了讓資料表視圖和詳細資料檢視之間的轉換變得順暢且自然，我將它與在實際生活中開啟的實際互動類似。</span><span class="sxs-lookup"><span data-stu-id="a1211-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="a1211-126">![設計草圖](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="a1211-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="a1211-127">*設計草圖*</span><span class="sxs-lookup"><span data-stu-id="a1211-127">*Design sketches*</span></span>

<span data-ttu-id="a1211-128">在詳細資料檢視中，我想要使用3D 空間中的美觀轉譯文字，將每個元素的資訊視覺化。</span><span class="sxs-lookup"><span data-stu-id="a1211-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="a1211-129">動畫的 3D electron 模型會顯示在中間區域，而且可以從不同的角度來查看。</span><span class="sxs-lookup"><span data-stu-id="a1211-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![互動](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="a1211-131">![原型](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="a1211-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="a1211-132">*互動原型*</span><span class="sxs-lookup"><span data-stu-id="a1211-132">*Interaction prototypes*</span></span>

<span data-ttu-id="a1211-133">使用者可以透過使用表格底部的按鈕來變更介面型別，它們可以在平面、圓柱圖、球體圖和散佈圖之間切換。</span><span class="sxs-lookup"><span data-stu-id="a1211-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="a1211-134">此應用程式中使用的通用控制項和模式</span><span class="sxs-lookup"><span data-stu-id="a1211-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="a1211-135">互動物件 (按鈕) </span><span class="sxs-lookup"><span data-stu-id="a1211-135">Interactable object (button)</span></span>

<span data-ttu-id="a1211-136">[互動物件](../../design/interactable-object.md) 是可回應基本 HoloLens 輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="a1211-136">[Interactable object](../../design/interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="a1211-137">它是以預製專案/腳本的形式提供，您可以輕鬆地將它套用到任何物件。</span><span class="sxs-lookup"><span data-stu-id="a1211-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="a1211-138">例如，您可以在場景中製作咖啡杯互動，並回應像是注視、碰點、導覽和操作手勢等輸入。</span><span class="sxs-lookup"><span data-stu-id="a1211-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="a1211-139">深入了解</span><span class="sxs-lookup"><span data-stu-id="a1211-139">Learn more</span></span>](../../design/interactable-object.md)

![nteractable 物件](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="a1211-141">物件集合</span><span class="sxs-lookup"><span data-stu-id="a1211-141">Object collection</span></span>

<span data-ttu-id="a1211-142">[物件集合](../../design/object-collection.md) 是一個物件，可協助您配置各種不同圖形中的多個物件。</span><span class="sxs-lookup"><span data-stu-id="a1211-142">[Object collection](../../design/object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="a1211-143">它支援平面、圓柱、球體和散佈圖。</span><span class="sxs-lookup"><span data-stu-id="a1211-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="a1211-144">您可以設定其他屬性，例如 radius、資料列數目和間距。</span><span class="sxs-lookup"><span data-stu-id="a1211-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="a1211-145">深入了解</span><span class="sxs-lookup"><span data-stu-id="a1211-145">Learn more</span></span>](../../design/object-collection.md)

![物件集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="a1211-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="a1211-147">Fitbox</span></span>

<span data-ttu-id="a1211-148">根據預設，在應用程式啟動時，會在使用者撥雲見日的位置放置全像影像。</span><span class="sxs-lookup"><span data-stu-id="a1211-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="a1211-149">這有時候會導致不想要的結果，例如，將影像放在牆後方或資料表的中間。</span><span class="sxs-lookup"><span data-stu-id="a1211-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="a1211-150">Fitbox 可讓使用者使用注視來判斷將放置全息圖的位置。</span><span class="sxs-lookup"><span data-stu-id="a1211-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="a1211-151">它會使用簡單的 PNG 影像材質進行自訂，您可以使用自己的影像或3D 物件輕鬆地加以自訂。</span><span class="sxs-lookup"><span data-stu-id="a1211-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](../../design/images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="a1211-153">技術詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a1211-153">Technical details</span></span>

<span data-ttu-id="a1211-154">您可以在 [混合式現實設計實驗室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上，找到專案應用程式的定期表格的腳本和 prefabs。</span><span class="sxs-lookup"><span data-stu-id="a1211-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="a1211-155">應用程式範例</span><span class="sxs-lookup"><span data-stu-id="a1211-155">Application examples</span></span>

<span data-ttu-id="a1211-156">以下是您可以利用此專案中的元件來建立的一些概念。</span><span class="sxs-lookup"><span data-stu-id="a1211-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="a1211-157">股票資料視覺效果應用程式</span><span class="sxs-lookup"><span data-stu-id="a1211-157">Stock data visualization app</span></span>

<span data-ttu-id="a1211-158">使用與專案範例的定期資料表相同的控制項和互動模型，您可以建立可哥視化股票市場資料的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1211-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="a1211-159">這個範例會使用物件集合控制項來配置球形圖形中的股票資料。</span><span class="sxs-lookup"><span data-stu-id="a1211-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="a1211-160">您可以想像出詳細資料，其中每個股票的其他相關資訊可能會以有趣的方式顯示。</span><span class="sxs-lookup"><span data-stu-id="a1211-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![應用程式範例：財務 (1/3) ](images/640px-periodictable-applicationexamples-finance1.jpg)

![應用程式範例：三) 的財務 (2](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="a1211-163">![應用程式範例：財務 (3) ](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="a1211-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="a1211-164">*如何在財務應用程式中使用元素範例應用程式的定期資料表中所使用的物件集合範例*</span><span class="sxs-lookup"><span data-stu-id="a1211-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="a1211-165">運動應用程式</span><span class="sxs-lookup"><span data-stu-id="a1211-165">Sports app</span></span>

<span data-ttu-id="a1211-166">這是使用專案範例應用程式之定期資料表中的物件集合和其他元件來視覺化運動資料的範例。</span><span class="sxs-lookup"><span data-stu-id="a1211-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![應用程式範例：運動 (1/3) ](images/640px-periodictable-applicationexamples-sports0.jpg)

![應用程式範例：運動 (2/3) ](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="a1211-169">![應用程式範例：運動 (3 之 3) ](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="a1211-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="a1211-170">*如何在運動應用程式中使用 appcould 元素範例的定期資料表中所使用的物件集合範例*</span><span class="sxs-lookup"><span data-stu-id="a1211-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="a1211-171">關於作者</span><span class="sxs-lookup"><span data-stu-id="a1211-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="a1211-172"><b>盾 Yoon 公園</b></span><span class="sxs-lookup"><span data-stu-id="a1211-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="a1211-173">UX 設計工具 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="a1211-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="a1211-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1211-174">See also</span></span>

* [<span data-ttu-id="a1211-175">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="a1211-175">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="a1211-176">物件集合</span><span class="sxs-lookup"><span data-stu-id="a1211-176">Object collection</span></span>](../../design/object-collection.md)
