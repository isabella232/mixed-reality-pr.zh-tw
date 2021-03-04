---
title: README_ObjectCollection
description: MRTK 中的物件集合總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、物件集合、
ms.openlocfilehash: 9ac2ec51c7500e44a3b6b255496680c1c5df238c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781070"
---
# <a name="object-collection"></a><span data-ttu-id="aca03-104">物件集合</span><span class="sxs-lookup"><span data-stu-id="aca03-104">Object collection</span></span>

![物件集合主要](Images/ObjectCollection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="aca03-106">物件集合是一種腳本，可協助您配置預先定義之三維圖形中的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="aca03-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="aca03-107">它支援各種表面樣式，包括平面、圓柱、球體和放射狀。</span><span class="sxs-lookup"><span data-stu-id="aca03-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="aca03-108">由於它支援 Unity 中的任何物件，因此可以用來配置2D 和3D 物件。</span><span class="sxs-lookup"><span data-stu-id="aca03-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="aca03-109">物件集合腳本</span><span class="sxs-lookup"><span data-stu-id="aca03-109">Object collection scripts</span></span>

- <span data-ttu-id="aca03-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 支援圓柱圖、平面、球體、放射狀介面類別型</span><span class="sxs-lookup"><span data-stu-id="aca03-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="aca03-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) 支援散佈的樣式集合</span><span class="sxs-lookup"><span data-stu-id="aca03-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="aca03-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) 提供一些其他選項來 GridObjectCollection。</span><span class="sxs-lookup"><span data-stu-id="aca03-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="aca03-113">**注意：** TileGridObjectCollection 不會擴充 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) ，而且有數個 bug (請參閱 [問題 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)) 。</span><span class="sxs-lookup"><span data-stu-id="aca03-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="aca03-114">因此，建議使用 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 。</span><span class="sxs-lookup"><span data-stu-id="aca03-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![方格物件集合-圓柱圖](Images/ObjectCollection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="aca03-116">方格物件集合-圓柱圖</span><span class="sxs-lookup"><span data-stu-id="aca03-116">Grid Object Collection - Cylinder</span></span> | ![方格物件集合-球體](Images/ObjectCollection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="aca03-118">方格物件集合-球體</span><span class="sxs-lookup"><span data-stu-id="aca03-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![方格物件集合-放射狀](Images/ObjectCollection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="aca03-120">方格物件集合-放射狀</span><span class="sxs-lookup"><span data-stu-id="aca03-120">Grid Object Collection - Radial</span></span> | ![方格物件集合-平面](Images/ObjectCollection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="aca03-122">方格物件集合-平面</span><span class="sxs-lookup"><span data-stu-id="aca03-122">Grid Object Collection - Plane</span></span> |
|![散佈的物件集合](Images/ObjectCollection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="aca03-124">散佈的物件集合</span><span class="sxs-lookup"><span data-stu-id="aca03-124">Scattered Object Collection</span></span> | ![磚方格物件集合](Images/ObjectCollection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="aca03-126">磚方格物件集合</span><span class="sxs-lookup"><span data-stu-id="aca03-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="aca03-127">如何使用物件集合</span><span class="sxs-lookup"><span data-stu-id="aca03-127">How to use an object collection</span></span>

<span data-ttu-id="aca03-128">若要建立集合，請建立空白的 GameObject，並將其中一個物件集合腳本指派給它。</span><span class="sxs-lookup"><span data-stu-id="aca03-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="aca03-129">任何 (s) 的物件都可以新增為 GameObject 的子系。</span><span class="sxs-lookup"><span data-stu-id="aca03-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="aca03-130">完成加入子物件之後，請按一下 [檢查] 面板中的 [ *更新集合* ] 按鈕，以產生物件集合。</span><span class="sxs-lookup"><span data-stu-id="aca03-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="aca03-131">系統會根據集合參數，在場景中設定物件。</span><span class="sxs-lookup"><span data-stu-id="aca03-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="aca03-132">您也可以透過程式碼來存取更新集合。</span><span class="sxs-lookup"><span data-stu-id="aca03-132">Update Collection can be accessed through the code too.</span></span>

![物件集合腳本](Images/ObjectCollection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="aca03-134">`GridObjectCollection` 內容對齊</span><span class="sxs-lookup"><span data-stu-id="aca03-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="aca03-135">您可以對齊 GridObjectCollection 中的內容，讓父物件錨定至集合的上方/中間/下和左/上/下/右。</span><span class="sxs-lookup"><span data-stu-id="aca03-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="aca03-136">使用 **錨點** 屬性指定內容對齊。</span><span class="sxs-lookup"><span data-stu-id="aca03-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="aca03-137">`GridObjectCollection` 版面配置順序</span><span class="sxs-lookup"><span data-stu-id="aca03-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="aca03-138">使用 [ **配置** ] 欄位來指定子系配置的資料列/資料行順序：</span><span class="sxs-lookup"><span data-stu-id="aca03-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="aca03-139">**然後** ，資料行會先依資料行) 水準 (來配置資料行子系，然後) 依資料列垂直 (。</span><span class="sxs-lookup"><span data-stu-id="aca03-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="aca03-140">在程式碼) 中使用 **Num columns** (或 columns 屬性來指定方格中的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="aca03-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![資料行之後的資料列版面配置](Images/ObjectCollection/MRTK_ColumnThenRow.png)

<span data-ttu-id="aca03-142">**然後** ，資料列會先依資料列) 垂直配置 (資料行，然後) 依資料行水準 (。</span><span class="sxs-lookup"><span data-stu-id="aca03-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="aca03-143">在程式碼) 中使用 **Num rows** (或 rows 屬性來指定方格中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="aca03-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![資料列 then 資料行版面配置](Images/ObjectCollection/MRTK_RowThenColumn.png)

<span data-ttu-id="aca03-145">只有在使用資料行的單一資料列中配置了 **水準** 子系</span><span class="sxs-lookup"><span data-stu-id="aca03-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="aca03-146">**垂直** 子系只會在單一資料行中使用資料列進行配置。</span><span class="sxs-lookup"><span data-stu-id="aca03-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="aca03-147">物件集合範例</span><span class="sxs-lookup"><span data-stu-id="aca03-147">Object collection examples</span></span>

<span data-ttu-id="aca03-148">`ObjectCollectionExamples` (資產/MRTK/範例/示範/UX/collection/場景/ObjectCollectionExamples unity) 範例場景包含各種物件集合類型的範例。</span><span class="sxs-lookup"><span data-stu-id="aca03-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="aca03-149">專案的[定期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是範例應用程式，示範物件集合的運作方式。</span><span class="sxs-lookup"><span data-stu-id="aca03-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="aca03-150">它使用物件集合來配置不同圖形中的3D 元素方塊。</span><span class="sxs-lookup"><span data-stu-id="aca03-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="aca03-151">物件集合類型</span><span class="sxs-lookup"><span data-stu-id="aca03-151">Object collection types</span></span>

<span data-ttu-id="aca03-152">**3D 物件**</span><span class="sxs-lookup"><span data-stu-id="aca03-152">**3D objects**</span></span>

<span data-ttu-id="aca03-153">物件集合可以用來配置匯入的3D 物件。</span><span class="sxs-lookup"><span data-stu-id="aca03-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="aca03-154">下列範例顯示使用集合的3D 椅子模型物件的平面和圓柱版面配置。</span><span class="sxs-lookup"><span data-stu-id="aca03-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![物件集合](Images/ObjectCollection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="aca03-156">**2D 物件**</span><span class="sxs-lookup"><span data-stu-id="aca03-156">**2D Objects**</span></span>

<span data-ttu-id="aca03-157">您也可以從2D 影像建立物件集合。</span><span class="sxs-lookup"><span data-stu-id="aca03-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="aca03-158">例如，多個影像可以用格線樣式來放置。</span><span class="sxs-lookup"><span data-stu-id="aca03-158">For example, multiple images can be placed in a grid style.</span></span>

![物件集合](Images/ObjectCollection/MRTK_ObjectCollection_Layout_2DImages.jpg)
