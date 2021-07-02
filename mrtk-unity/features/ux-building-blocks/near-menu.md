---
title: 近端功能表
description: 總覽 MRTK 中的接近功能表類型
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、近端功能表、
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175648"
---
# <a name="near-menu"></a><span data-ttu-id="ec269-104">近端功能表</span><span class="sxs-lookup"><span data-stu-id="ec269-104">Near menu</span></span>

![近端功能表](../images/near-menu/MRTK_UX_NearMenu.png)

<span data-ttu-id="ec269-106">近端功能表是 UX 控制項，可提供按鈕或其他 UI 元件的集合。</span><span class="sxs-lookup"><span data-stu-id="ec269-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="ec269-107">它是以使用者的主體為中心，而且隨時都可以輕鬆存取。</span><span class="sxs-lookup"><span data-stu-id="ec269-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="ec269-108">由於它與使用者鬆散結合，因此不會干擾使用者與目標內容的互動。</span><span class="sxs-lookup"><span data-stu-id="ec269-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="ec269-109">使用者可以使用 [釘選] 按鈕，以世界鎖定/解除鎖定功能表。</span><span class="sxs-lookup"><span data-stu-id="ec269-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="ec269-110">您可以抓取功能表，並將其置於特定位置。</span><span class="sxs-lookup"><span data-stu-id="ec269-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="ec269-111">互動行為</span><span class="sxs-lookup"><span data-stu-id="ec269-111">Interaction behavior</span></span>

- <span data-ttu-id="ec269-112">**加** 上標籤：功能表會跟隨您，並保留在使用者的 30 60cm 範圍內，以進行近乎互動。</span><span class="sxs-lookup"><span data-stu-id="ec269-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="ec269-113">**Pin**：您可以使用 [釘選] 按鈕，以世界鎖定和釋出功能表。</span><span class="sxs-lookup"><span data-stu-id="ec269-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="ec269-114">**抓取和移動**：功能表一律為 grabbable 和可移動。</span><span class="sxs-lookup"><span data-stu-id="ec269-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="ec269-115">無論先前的狀態為何，在抓取和釋放時，功能表都會釘選 (世界鎖定的) 。</span><span class="sxs-lookup"><span data-stu-id="ec269-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="ec269-116">Grabbable 區域有視覺提示。</span><span class="sxs-lookup"><span data-stu-id="ec269-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="ec269-117">它們會顯示在手上。</span><span class="sxs-lookup"><span data-stu-id="ec269-117">They are revealed on hand proximity.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a><span data-ttu-id="ec269-118">Prefabs</span><span class="sxs-lookup"><span data-stu-id="ec269-118">Prefabs</span></span>

<span data-ttu-id="ec269-119">近端功能表 prefabs 的設計目的是要示範如何使用 MRTK 的各種元件來建立功能表以進行近乎互動。</span><span class="sxs-lookup"><span data-stu-id="ec269-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="ec269-120">**NearMenu2x4. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ec269-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="ec269-121">**NearMenu3x1. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ec269-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="ec269-122">**NearMenu3x2. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ec269-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="ec269-123">**NearMenu3x3. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ec269-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="ec269-124">**NearMenu4x1. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ec269-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="ec269-125">**NearMenu4x2. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ec269-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="ec269-126">範例場景</span><span class="sxs-lookup"><span data-stu-id="ec269-126">Example scene</span></span>

<span data-ttu-id="ec269-127">您可以在場景中找到接近功能表 prefabs 的範例 `NearMenuExamples` 。</span><span class="sxs-lookup"><span data-stu-id="ec269-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a><span data-ttu-id="ec269-128">結構</span><span class="sxs-lookup"><span data-stu-id="ec269-128">Structure</span></span>

<span data-ttu-id="ec269-129">附近的功能表 prefabs 會使用下列 MRTK 元件來進行。</span><span class="sxs-lookup"><span data-stu-id="ec269-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="ec269-130">[**PressableButtonHoloLens2**](button.md) 預製專案</span><span class="sxs-lookup"><span data-stu-id="ec269-130">[**PressableButtonHoloLens2**](button.md) prefab</span></span>
- <span data-ttu-id="ec269-131">[**方格物件集合**](object-collection.md)：方格中的多個按鈕版面配置</span><span class="sxs-lookup"><span data-stu-id="ec269-131">[**Grid Object Collection**](object-collection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="ec269-132">[**操作處理常式**](manipulation-handler.md)：抓取並移動功能表</span><span class="sxs-lookup"><span data-stu-id="ec269-132">[**Manipulation Handler**](manipulation-handler.md): Grab and move the menu</span></span>
- <span data-ttu-id="ec269-133">[**RadialView 規劃**](solvers/solver.md)：追蹤 (標記-沿著) 的行為</span><span class="sxs-lookup"><span data-stu-id="ec269-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior</span></span>

![鄰近功能表預製專案](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="ec269-135">如何自訂</span><span class="sxs-lookup"><span data-stu-id="ec269-135">How to customize</span></span>

<span data-ttu-id="ec269-136">**1. 新增/移除按鈕**</span><span class="sxs-lookup"><span data-stu-id="ec269-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="ec269-137">在 [物件] 下 `ButtonCollection` ，[加入] 或 [移除] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ec269-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

<span data-ttu-id="ec269-138">**2. 更新方格物件集合**</span><span class="sxs-lookup"><span data-stu-id="ec269-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="ec269-139">`Update Collection`在物件的偵測器中，按一下按鈕 `ButtonCollection` 。</span><span class="sxs-lookup"><span data-stu-id="ec269-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="ec269-140">它會更新格線版面配置。</span><span class="sxs-lookup"><span data-stu-id="ec269-140">It will update the grid layout.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

<span data-ttu-id="ec269-141">您可以使用方格物件集合的屬性來設定資料列的數目 `Rows` 。</span><span class="sxs-lookup"><span data-stu-id="ec269-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

<span data-ttu-id="ec269-142">**3. 調整 backplate 大小**</span><span class="sxs-lookup"><span data-stu-id="ec269-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="ec269-143">調整 [物件] 下的大小 `Quad` `Backplate` 。</span><span class="sxs-lookup"><span data-stu-id="ec269-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="ec269-144">Backplate 的寬度和高度應該是 `0.032 * [Number of the buttons + 1]` 。</span><span class="sxs-lookup"><span data-stu-id="ec269-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="ec269-145">例如，如果您有 3 x 2 個按鈕，則 backplate 的寬度為， `0.032 * 4` 而高度為 `0.032 * 3` 。</span><span class="sxs-lookup"><span data-stu-id="ec269-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="ec269-146">您可以直接將此運算式放入 Unity 的欄位中。</span><span class="sxs-lookup"><span data-stu-id="ec269-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- <span data-ttu-id="ec269-147">HoloLens 2 按鈕的預設大小為 3.2 x 3.2 cm (0.032 m) </span><span class="sxs-lookup"><span data-stu-id="ec269-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="ec269-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec269-148">See also</span></span>

- [<span data-ttu-id="ec269-149">**按鈕**</span><span class="sxs-lookup"><span data-stu-id="ec269-149">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="ec269-150">**界限控制項**</span><span class="sxs-lookup"><span data-stu-id="ec269-150">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="ec269-151">**滑桿**</span><span class="sxs-lookup"><span data-stu-id="ec269-151">**Slider**</span></span>](sliders.md)
- [<span data-ttu-id="ec269-152">**方格物件集合**</span><span class="sxs-lookup"><span data-stu-id="ec269-152">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="ec269-153">**操作處理常式**</span><span class="sxs-lookup"><span data-stu-id="ec269-153">**Manipulation Handler**</span></span>](manipulation-handler.md)
- [<span data-ttu-id="ec269-154">**RadialView 規劃**</span><span class="sxs-lookup"><span data-stu-id="ec269-154">**RadialView Solver**</span></span>](solvers/solver.md)
