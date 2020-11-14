---
title: 元素週期表
description: 專案的定期資料表是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式，您可以在其中學習如何使用物件集合，在3D 空間中設定物件陣列，以及各種表面類型。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、範例應用程式、控制項
ms.openlocfilehash: 82ffa19b27c1d2687b67df659cb3bb50544748fc
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573262"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="279fa-104">元素週期表</span><span class="sxs-lookup"><span data-stu-id="279fa-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="279fa-105">本文討論我們在 [混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例，這是我們分享學習的地方，並提供混合現實應用程式開發的建議。</span><span class="sxs-lookup"><span data-stu-id="279fa-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="279fa-106">我們的設計相關文章和程式碼將隨著我們進行新探索而演進。</span><span class="sxs-lookup"><span data-stu-id="279fa-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="279fa-107">專案的[定期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="279fa-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="279fa-108">透過此專案，您可以瞭解如何使用 **[物件集合](../../design/object-collection.md)** ，在3d 空間中配置具有各種介面類別型的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="279fa-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="279fa-109">同時瞭解如何建立互動物件，以回應 HoloLens 的標準輸入。</span><span class="sxs-lookup"><span data-stu-id="279fa-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="279fa-110">您可以使用此專案的元件來建立您自己的混合現實應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="279fa-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Elements 應用程式的期間資料表](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="279fa-112">示範影片</span><span class="sxs-lookup"><span data-stu-id="279fa-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="279fa-113">使用混合實境擷取 HoloLens 2 記錄</span><span class="sxs-lookup"><span data-stu-id="279fa-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="279fa-114">關於應用程式</span><span class="sxs-lookup"><span data-stu-id="279fa-114">About the app</span></span>

<span data-ttu-id="279fa-115">專案的定期資料表會以3D 空間將化學元素和每個屬性視覺化。</span><span class="sxs-lookup"><span data-stu-id="279fa-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="279fa-116">它結合了 HoloLens 的基本互動，例如注視和點擊。</span><span class="sxs-lookup"><span data-stu-id="279fa-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="279fa-117">使用者可以使用動畫3D 模型來瞭解這些元素。</span><span class="sxs-lookup"><span data-stu-id="279fa-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="279fa-118">他們可以透過視覺化方式瞭解元素的 electron shell 及其系統核心（由 protons 和 neutrons 組成）。</span><span class="sxs-lookup"><span data-stu-id="279fa-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="279fa-119">背景</span><span class="sxs-lookup"><span data-stu-id="279fa-119">Background</span></span>

<span data-ttu-id="279fa-120">在我第一次體驗 HoloLens 之後，定期資料表應用程式就是我知道我想要在混合現實中進行實驗的概念。</span><span class="sxs-lookup"><span data-stu-id="279fa-120">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="279fa-121">由於每個專案都有許多以文字顯示的資料點，因此我認為在3D 空間中探索印刷樣式組合是很重要的主題。</span><span class="sxs-lookup"><span data-stu-id="279fa-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="279fa-122">能夠以視覺化方式呈現專案的 electron 模型是這個專案的另一個有趣的部分。</span><span class="sxs-lookup"><span data-stu-id="279fa-122">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="279fa-123">設計</span><span class="sxs-lookup"><span data-stu-id="279fa-123">Design</span></span>

<span data-ttu-id="279fa-124">針對定期資料表的預設視圖，我想要有三維方塊，其中包含每個元素的 electron 模型。</span><span class="sxs-lookup"><span data-stu-id="279fa-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="279fa-125">每個方塊的介面都是半透明的，讓使用者可以大致瞭解元素的音量。</span><span class="sxs-lookup"><span data-stu-id="279fa-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="279fa-126">使用者可以利用注視和空中來開啟每個元素的詳細觀點。</span><span class="sxs-lookup"><span data-stu-id="279fa-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="279fa-127">為了讓資料表視圖和詳細資料檢視之間的轉換變得順暢且自然，我將它與在實際生活中開啟的實際互動類似。</span><span class="sxs-lookup"><span data-stu-id="279fa-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="279fa-128">![設計草圖](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="279fa-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="279fa-129">*設計草圖*</span><span class="sxs-lookup"><span data-stu-id="279fa-129">*Design sketches*</span></span>

<span data-ttu-id="279fa-130">在詳細資料檢視中，我想要使用3D 空間中的美觀轉譯文字，將每個元素的資訊視覺化。</span><span class="sxs-lookup"><span data-stu-id="279fa-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="279fa-131">動畫的 3D electron 模型會顯示在中間區域，而且可以從不同的角度來查看。</span><span class="sxs-lookup"><span data-stu-id="279fa-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![互動](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="279fa-133">![原型](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="279fa-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="279fa-134">*互動原型*</span><span class="sxs-lookup"><span data-stu-id="279fa-134">*Interaction prototypes*</span></span>

<span data-ttu-id="279fa-135">使用者可以透過使用表格底部的按鈕來變更介面型別，它們可以在平面、圓柱圖、球體圖和散佈圖之間切換。</span><span class="sxs-lookup"><span data-stu-id="279fa-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="279fa-136">此應用程式中使用的通用控制項和模式</span><span class="sxs-lookup"><span data-stu-id="279fa-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="279fa-137">互動物件 (按鈕) </span><span class="sxs-lookup"><span data-stu-id="279fa-137">Interactable object (button)</span></span>

<span data-ttu-id="279fa-138">[互動物件](../../design/interactable-object.md) 是可回應基本 HoloLens 輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="279fa-138">[Interactable object](../../design/interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="279fa-139">它是以預製專案/腳本的形式提供，您可以輕鬆地將它套用到任何物件。</span><span class="sxs-lookup"><span data-stu-id="279fa-139">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="279fa-140">例如，您可以在場景中製作咖啡杯互動，並回應像是注視、碰點、導覽和操作手勢等輸入。</span><span class="sxs-lookup"><span data-stu-id="279fa-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="279fa-141">深入了解</span><span class="sxs-lookup"><span data-stu-id="279fa-141">Learn more</span></span>](../../design/interactable-object.md)

![nteractable 物件](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="279fa-143">物件集合</span><span class="sxs-lookup"><span data-stu-id="279fa-143">Object collection</span></span>

<span data-ttu-id="279fa-144">[物件集合](../../design/object-collection.md) 是一個物件，可協助您配置各種不同圖形中的多個物件。</span><span class="sxs-lookup"><span data-stu-id="279fa-144">[Object collection](../../design/object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="279fa-145">它支援平面、圓柱、球體和散佈圖。</span><span class="sxs-lookup"><span data-stu-id="279fa-145">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="279fa-146">您可以設定其他屬性，例如 radius、資料列數目和間距。</span><span class="sxs-lookup"><span data-stu-id="279fa-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="279fa-147">深入了解</span><span class="sxs-lookup"><span data-stu-id="279fa-147">Learn more</span></span>](../../design/object-collection.md)

![物件集合](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="279fa-149">技術詳細資訊</span><span class="sxs-lookup"><span data-stu-id="279fa-149">Technical details</span></span>

<span data-ttu-id="279fa-150">您可以在 [混合式現實設計實驗室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上，找到專案應用程式的定期表格的腳本和 prefabs。</span><span class="sxs-lookup"><span data-stu-id="279fa-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="279fa-151">HoloLens 2 的移植案例</span><span class="sxs-lookup"><span data-stu-id="279fa-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="279fa-152">閱讀有關如何使用 HoloLens 2 的 instinctual 互動來更新專案應用程式之定期表格的案例。</span><span class="sxs-lookup"><span data-stu-id="279fa-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="279fa-153">元素週期表 2.0</span><span class="sxs-lookup"><span data-stu-id="279fa-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="279fa-154">關於作者</span><span class="sxs-lookup"><span data-stu-id="279fa-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="279fa-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="279fa-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="279fa-156">UX 設計者 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="279fa-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="279fa-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="279fa-157">See also</span></span>

* <span data-ttu-id="279fa-158">[MRTK 範例中樞](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="279fa-158">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="279fa-159">[表面](sampleapp-surfaces.md) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="279fa-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="279fa-160">元素週期表 2.0</span><span class="sxs-lookup"><span data-stu-id="279fa-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="279fa-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="279fa-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)