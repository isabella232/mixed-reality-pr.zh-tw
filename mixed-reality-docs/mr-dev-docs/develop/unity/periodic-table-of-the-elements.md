---
title: 元素週期表
description: 專案的定期資料表是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。 了解如何使用物件集合，透過各種介面類型在 3D 空間中配置物件陣列。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、範例應用程式、控制項、MRTK、混合現實工具組、Unity、範例應用程式、範例應用程式、開放原始碼、Microsoft Store、HoloLens、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: a4099c889fee886e63d3a8b773398a250621f26e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010179"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="ccb50-105">元素週期表</span><span class="sxs-lookup"><span data-stu-id="ccb50-105">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="ccb50-106">本文討論我們在 [混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例，這是我們分享學習的地方，並提供混合現實應用程式開發的建議。</span><span class="sxs-lookup"><span data-stu-id="ccb50-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="ccb50-107">我們的設計相關文章和程式碼將隨著我們進行新探索而演進。</span><span class="sxs-lookup"><span data-stu-id="ccb50-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="ccb50-108">專案的[定期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccb50-108">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="ccb50-109">瞭解如何使用 **[物件集合](../../design/object-collection.md)**，在3d 空間中配置具有各種介面類別型的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="ccb50-109">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="ccb50-110">同時瞭解如何建立互動物件，以回應 HoloLens 的標準輸入。</span><span class="sxs-lookup"><span data-stu-id="ccb50-110">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="ccb50-111">您可以使用此專案的元件來建立您自己的混合現實應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="ccb50-111">You can use this project's components to create your own mixed reality app experience.</span></span>

![Elements 應用程式的期間資料表](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="ccb50-113">示範影片</span><span class="sxs-lookup"><span data-stu-id="ccb50-113">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="ccb50-114">使用混合實境擷取 HoloLens 2 記錄</span><span class="sxs-lookup"><span data-stu-id="ccb50-114">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="ccb50-115">關於應用程式</span><span class="sxs-lookup"><span data-stu-id="ccb50-115">About the app</span></span>

<span data-ttu-id="ccb50-116">專案的定期資料表會以3D 空間將化學元素和每個屬性視覺化。</span><span class="sxs-lookup"><span data-stu-id="ccb50-116">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="ccb50-117">它結合了 HoloLens 的基本互動，例如注視和點擊。</span><span class="sxs-lookup"><span data-stu-id="ccb50-117">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="ccb50-118">使用者可以使用動畫3D 模型來瞭解這些元素。</span><span class="sxs-lookup"><span data-stu-id="ccb50-118">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="ccb50-119">他們可以透過視覺化方式瞭解元素的 electron shell 及其系統核心（由 protons 和 neutrons 組成）。</span><span class="sxs-lookup"><span data-stu-id="ccb50-119">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="ccb50-120">背景</span><span class="sxs-lookup"><span data-stu-id="ccb50-120">Background</span></span>

<span data-ttu-id="ccb50-121">在我第一次體驗 HoloLens 之後，我知道我想要在混合的情況下實驗定期資料表應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccb50-121">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="ccb50-122">由於每個專案都有許多以文字顯示的資料點，因此我認為在3D 空間中探索印刷樣式組合是很重要的主題。</span><span class="sxs-lookup"><span data-stu-id="ccb50-122">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="ccb50-123">讓使用者有機會將元素的 electron 模型視覺化是此專案的另一個有趣部分。</span><span class="sxs-lookup"><span data-stu-id="ccb50-123">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="ccb50-124">設計</span><span class="sxs-lookup"><span data-stu-id="ccb50-124">Design</span></span>

<span data-ttu-id="ccb50-125">針對定期資料表的預設視圖，我想要有三維方塊，其中包含每個元素的 electron 模型。</span><span class="sxs-lookup"><span data-stu-id="ccb50-125">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="ccb50-126">每個方塊的介面都是半透明的，讓使用者可以大致瞭解元素的音量。</span><span class="sxs-lookup"><span data-stu-id="ccb50-126">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="ccb50-127">使用者可以利用注視和空中來開啟每個元素的詳細觀點。</span><span class="sxs-lookup"><span data-stu-id="ccb50-127">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="ccb50-128">為了讓資料表視圖和詳細資料檢視之間的轉換變得順暢且自然，我將它與在實際生活中開啟的實際互動類似。</span><span class="sxs-lookup"><span data-stu-id="ccb50-128">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="ccb50-129">![設計草圖](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="ccb50-129">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="ccb50-130">*設計草圖*</span><span class="sxs-lookup"><span data-stu-id="ccb50-130">*Design sketches*</span></span>

<span data-ttu-id="ccb50-131">在詳細資料檢視中，我想要使用3D 空間中的美觀轉譯文字，將每個元素的資訊視覺化。</span><span class="sxs-lookup"><span data-stu-id="ccb50-131">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="ccb50-132">動畫的 3D electron 模型會顯示在中間區域，而且可以從不同的角度來查看。</span><span class="sxs-lookup"><span data-stu-id="ccb50-132">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![互動](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="ccb50-134">![原型](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="ccb50-134">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="ccb50-135">*互動原型*</span><span class="sxs-lookup"><span data-stu-id="ccb50-135">*Interaction prototypes*</span></span>

<span data-ttu-id="ccb50-136">使用者可以透過使用表格底部的按鈕來變更介面類別型-它們可以在平面、圓柱圖、球體圖和散佈圖之間切換。</span><span class="sxs-lookup"><span data-stu-id="ccb50-136">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="ccb50-137">此應用程式中使用的通用控制項和模式</span><span class="sxs-lookup"><span data-stu-id="ccb50-137">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="ccb50-138">互動物件 (按鈕) </span><span class="sxs-lookup"><span data-stu-id="ccb50-138">Interactable object (button)</span></span>

<span data-ttu-id="ccb50-139">[互動物件](../../design/interactable-object.md) 是物件，可回應基本的 HoloLens 輸入。</span><span class="sxs-lookup"><span data-stu-id="ccb50-139">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="ccb50-140">它是以預製專案/腳本的形式提供，您可以輕鬆地將它套用到任何物件。</span><span class="sxs-lookup"><span data-stu-id="ccb50-140">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="ccb50-141">例如，您可以在場景中製作咖啡杯互動，並回應像是注視、碰點、導覽和操作手勢等輸入。</span><span class="sxs-lookup"><span data-stu-id="ccb50-141">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="ccb50-142">深入了解</span><span class="sxs-lookup"><span data-stu-id="ccb50-142">Learn more</span></span>](../../design/interactable-object.md)

![nteractable 物件](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="ccb50-144">物件集合</span><span class="sxs-lookup"><span data-stu-id="ccb50-144">Object collection</span></span>

<span data-ttu-id="ccb50-145">[物件集合](../../design/object-collection.md) 是一種物件，可協助您配置各種不同圖形中的多個物件。</span><span class="sxs-lookup"><span data-stu-id="ccb50-145">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="ccb50-146">它支援平面、圓柱、球體和散佈圖。</span><span class="sxs-lookup"><span data-stu-id="ccb50-146">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="ccb50-147">您可以設定其他屬性，例如 radius、資料列數目和間距。</span><span class="sxs-lookup"><span data-stu-id="ccb50-147">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="ccb50-148">深入了解</span><span class="sxs-lookup"><span data-stu-id="ccb50-148">Learn more</span></span>](../../design/object-collection.md)

![物件集合](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="ccb50-150">技術詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ccb50-150">Technical details</span></span>

<span data-ttu-id="ccb50-151">您可以在 [混合式現實設計實驗室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上，找到專案應用程式的定期表格的腳本和 prefabs。</span><span class="sxs-lookup"><span data-stu-id="ccb50-151">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="ccb50-152">HoloLens 2 的移植案例</span><span class="sxs-lookup"><span data-stu-id="ccb50-152">Porting story for HoloLens 2</span></span>

<span data-ttu-id="ccb50-153">閱讀有關如何使用 HoloLens 2 的 instinctual 互動來更新專案應用程式之定期表格的案例。</span><span class="sxs-lookup"><span data-stu-id="ccb50-153">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="ccb50-154">元素週期表 2.0</span><span class="sxs-lookup"><span data-stu-id="ccb50-154">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="ccb50-155">關於作者</span><span class="sxs-lookup"><span data-stu-id="ccb50-155">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="ccb50-156"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="ccb50-156"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="ccb50-157">UX 設計者 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="ccb50-157">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="ccb50-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccb50-158">See also</span></span>

* <span data-ttu-id="ccb50-159">[MRTK 範例中樞](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="ccb50-159">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="ccb50-160">[表面](sampleapp-surfaces.md) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="ccb50-160">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="ccb50-161">元素週期表 2.0</span><span class="sxs-lookup"><span data-stu-id="ccb50-161">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="ccb50-162">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="ccb50-162">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)