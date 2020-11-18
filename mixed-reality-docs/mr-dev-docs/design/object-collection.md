---
title: 物件集合
description: 物件集合是版面配置控制項，可協助您配置預先定義之三維圖形中的物件陣列。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、控制項、設計、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、物件集合、2D、3D、MRTK、混合現實工具組
ms.openlocfilehash: 41087c4a09e72b199c1ab03f504343bf7d6b1ba8
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703404"
---
# <a name="object-collection"></a><span data-ttu-id="7d4d6-104">物件集合</span><span class="sxs-lookup"><span data-stu-id="7d4d6-104">Object collection</span></span>

![專案應用程式的定期資料表中所使用的物件集合](images/UX_Hero_ObjectCollection.jpg)<br>


<span data-ttu-id="7d4d6-106">物件集合是版面配置控制項，可協助您配置預先定義之三維圖形中的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="7d4d6-107">它支援各種表面樣式- **平面、圓柱、球體** 和 **放射狀**。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="7d4d6-108">您可以調整物件的半徑和大小，以及兩者之間的空間。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="7d4d6-109">物件集合支援 Unity （2D 和3D）中的任何物件。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="7d4d6-110">在 **[混合現實工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** 組中，我們建立了 Unity 腳本和範例，可協助您建立物件集合。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="7d4d6-111">物件集合範例</span><span class="sxs-lookup"><span data-stu-id="7d4d6-111">Object collection examples</span></span>

<span data-ttu-id="7d4d6-112">專案的[定期資料表](../develop/unity/periodic-table-of-the-elements.md)是範例應用程式，可示範物件集合的運作方式。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="7d4d6-113">它使用物件集合來配置不同圖形中的3D 化學元素方塊。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="7d4d6-114">![在專案應用程式的定期表格中顯示的物件集合範例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d4d6-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="7d4d6-115">*元素範例應用程式的定期表格中顯示的物件集合範例*</span><span class="sxs-lookup"><span data-stu-id="7d4d6-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="7d4d6-116">3D 物件</span><span class="sxs-lookup"><span data-stu-id="7d4d6-116">3D objects</span></span>

<span data-ttu-id="7d4d6-117">您可以使用物件集合來配置已匯入的3D 物件。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="7d4d6-118">下列範例顯示某些3D 椅子物件的平面和圓柱版面配置。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="7d4d6-119">![3D 物件的平面和圓柱版面配置範例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d4d6-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="7d4d6-120">*3D 物件的平面和圓柱版面配置範例*</span><span class="sxs-lookup"><span data-stu-id="7d4d6-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="7d4d6-121">2D 物件</span><span class="sxs-lookup"><span data-stu-id="7d4d6-121">2D objects</span></span>

<span data-ttu-id="7d4d6-122">您也可以使用2D 映射搭配物件集合。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="7d4d6-123">下列範例會示範如何在方格中顯示2D 影像。</span><span class="sxs-lookup"><span data-stu-id="7d4d6-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![具有物件集合的2D 影像範例](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="7d4d6-125">![具有物件集合的2D 影像範例](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d4d6-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="7d4d6-126">*使用物件集合搭配2D 影像的範例*</span><span class="sxs-lookup"><span data-stu-id="7d4d6-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="7d4d6-127">Unity 的 MRTK (混合現實工具組) 的物件集合</span><span class="sxs-lookup"><span data-stu-id="7d4d6-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="7d4d6-128">MRTK-物件集合</span><span class="sxs-lookup"><span data-stu-id="7d4d6-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="7d4d6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d4d6-129">See also</span></span>

* [<span data-ttu-id="7d4d6-130">游標</span><span class="sxs-lookup"><span data-stu-id="7d4d6-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="7d4d6-131">手部光線</span><span class="sxs-lookup"><span data-stu-id="7d4d6-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="7d4d6-132">Button</span><span class="sxs-lookup"><span data-stu-id="7d4d6-132">Button</span></span>](button.md)
* [<span data-ttu-id="7d4d6-133">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="7d4d6-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="7d4d6-134">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="7d4d6-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="7d4d6-135">操作</span><span class="sxs-lookup"><span data-stu-id="7d4d6-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7d4d6-136">手部功能表</span><span class="sxs-lookup"><span data-stu-id="7d4d6-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="7d4d6-137">近端功能表</span><span class="sxs-lookup"><span data-stu-id="7d4d6-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="7d4d6-138">物件集合</span><span class="sxs-lookup"><span data-stu-id="7d4d6-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="7d4d6-139">語音命令</span><span class="sxs-lookup"><span data-stu-id="7d4d6-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="7d4d6-140">鍵盤</span><span class="sxs-lookup"><span data-stu-id="7d4d6-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="7d4d6-141">工具提示</span><span class="sxs-lookup"><span data-stu-id="7d4d6-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="7d4d6-142">平板</span><span class="sxs-lookup"><span data-stu-id="7d4d6-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="7d4d6-143">滑桿</span><span class="sxs-lookup"><span data-stu-id="7d4d6-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="7d4d6-144">著色器</span><span class="sxs-lookup"><span data-stu-id="7d4d6-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="7d4d6-145">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="7d4d6-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="7d4d6-146">顯示進度</span><span class="sxs-lookup"><span data-stu-id="7d4d6-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="7d4d6-147">表面磁性</span><span class="sxs-lookup"><span data-stu-id="7d4d6-147">Surface magnetism</span></span>](surface-magnetism.md)
