---
title: ManipulationHandler
description: MRTK 中操作處理常式的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、操作、
ms.openlocfilehash: d4bacb1da4eecdd7b6eabf3d97b3088bc5f950c3
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780193"
---
# <a name="manipulation-handler"></a><span data-ttu-id="ef70a-104">操作處理常式</span><span class="sxs-lookup"><span data-stu-id="ef70a-104">Manipulation handler</span></span>

![操作處理常式主](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="ef70a-106">*ManipulationHandler* 腳本可讓您使用一或兩個手將物件設為可移動、可擴充和 rotatable。</span><span class="sxs-lookup"><span data-stu-id="ef70a-106">The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="ef70a-107">可以限制操作，讓它只允許特定類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="ef70a-107">Manipulation can be restricted so that it only allows certain kinds of transformation.</span></span> <span data-ttu-id="ef70a-108">此腳本適用于各種類型的輸入，包括 HoloLens 2 的明確輸入、手片、HoloLens (第一代) 手勢輸入，以及沉浸式耳機移動控制器輸入。</span><span class="sxs-lookup"><span data-stu-id="ef70a-108">The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-manipulation-handler"></a><span data-ttu-id="ef70a-109">如何使用操作處理常式</span><span class="sxs-lookup"><span data-stu-id="ef70a-109">How to use the manipulation handler</span></span>

<span data-ttu-id="ef70a-110">將 `ManipulationHandler` 腳本元件新增至 GameObject。</span><span class="sxs-lookup"><span data-stu-id="ef70a-110">Add the `ManipulationHandler` script component to a GameObject.</span></span> <span data-ttu-id="ef70a-111">請務必同時將碰撞新增至物件，以符合其 grabbable 界限。</span><span class="sxs-lookup"><span data-stu-id="ef70a-111">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="ef70a-112">若要讓物件回應接近明確的手輸入，請新增 `NearInteractionGrabbable` 腳本。</span><span class="sxs-lookup"><span data-stu-id="ef70a-112">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

![操作處理常式詳細資料](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a><span data-ttu-id="ef70a-114">偵測器屬性</span><span class="sxs-lookup"><span data-stu-id="ef70a-114">Inspector properties</span></span>

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manupulation Handler Structure">

<span data-ttu-id="ef70a-115">**主機轉換** 將拖曳的轉換。</span><span class="sxs-lookup"><span data-stu-id="ef70a-115">**Host Transform** Transform that will be dragged.</span></span> <span data-ttu-id="ef70a-116">預設為元件的物件。</span><span class="sxs-lookup"><span data-stu-id="ef70a-116">Defaults to the object of the component.</span></span>

<span data-ttu-id="ef70a-117">**操作類型** 指定是否可以使用一或兩個手來操作物件。</span><span class="sxs-lookup"><span data-stu-id="ef70a-117">**Manipulation Type** Specifies whether the object can be manipulated using one hand, two hands, or both.</span></span>

* <span data-ttu-id="ef70a-118">*僅限一次*</span><span class="sxs-lookup"><span data-stu-id="ef70a-118">*One handed only*</span></span>
* <span data-ttu-id="ef70a-119">*僅限兩個右手*</span><span class="sxs-lookup"><span data-stu-id="ef70a-119">*Two handed only*</span></span>
* <span data-ttu-id="ef70a-120">*一和兩個右手*</span><span class="sxs-lookup"><span data-stu-id="ef70a-120">*One and Two handed*</span></span>

<span data-ttu-id="ef70a-121">**兩個右手操作類型**</span><span class="sxs-lookup"><span data-stu-id="ef70a-121">**Two Handed Manipulation Type**</span></span>

* <span data-ttu-id="ef70a-122">*調整*：只允許縮放。</span><span class="sxs-lookup"><span data-stu-id="ef70a-122">*Scale*: Only scaling is allowed.</span></span>
* <span data-ttu-id="ef70a-123">*旋轉*：只允許旋轉。</span><span class="sxs-lookup"><span data-stu-id="ef70a-123">*Rotate*: Only rotation is allowed.</span></span>
* <span data-ttu-id="ef70a-124">*移動縮放*：允許移動和調整。</span><span class="sxs-lookup"><span data-stu-id="ef70a-124">*Move Scale*: Moving and scaling is allowed.</span></span>
* <span data-ttu-id="ef70a-125">*移動旋轉*：允許移動和旋轉。</span><span class="sxs-lookup"><span data-stu-id="ef70a-125">*Move Rotate*: Moving and rotating is allowed.</span></span>
* <span data-ttu-id="ef70a-126">*旋轉比例*：允許旋轉和縮放。</span><span class="sxs-lookup"><span data-stu-id="ef70a-126">*Rotate Scale*: Rotating and scaling is allowed.</span></span>
* <span data-ttu-id="ef70a-127">*移動旋轉比例*：允許移動、旋轉和縮放。</span><span class="sxs-lookup"><span data-stu-id="ef70a-127">*Move Rotate Scale*: Moving, rotating and scaling is allowed.</span></span>

![操作處理常式](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

<span data-ttu-id="ef70a-129">**允許目前的操作** 指定是否可以使用與指標互動的方式來執行操作。</span><span class="sxs-lookup"><span data-stu-id="ef70a-129">**Allow Far Manipulation** Specifies whether manipulation can be done using far interaction with pointers.</span></span>

<span data-ttu-id="ef70a-130">**接近的一次旋轉模式** 指定當物件在接近的一端進行抓取時，該物件的行為。</span><span class="sxs-lookup"><span data-stu-id="ef70a-130">**One Hand Rotation Mode Near** Specifies how the object will behave when it is being grabbed with one hand / controller near.</span></span>

<span data-ttu-id="ef70a-131">**一種手邊的旋轉模式** 指定當物件以距離的一端抓取時，該物件的行為。</span><span class="sxs-lookup"><span data-stu-id="ef70a-131">**One Hand Rotation Mode Far** Specifies how the object will behave when it is being grabbed with one hand / controller at distance.</span></span>

<span data-ttu-id="ef70a-132">**一種旋轉模式選項** 指定當物件被抓取時，物件將如何旋轉。</span><span class="sxs-lookup"><span data-stu-id="ef70a-132">**One Hand Rotation Mode Options** Specifies how the object will rotate when it is being grabbed with one hand.</span></span>

* <span data-ttu-id="ef70a-133">*維護原始輪替*：不會在物件移動時旋轉物件</span><span class="sxs-lookup"><span data-stu-id="ef70a-133">*Maintain original rotation*: Does not rotate object as it is being moved</span></span>
* <span data-ttu-id="ef70a-134">*維護對使用者的旋轉*：為使用者維護 X/Y 軸的物件原始旋轉</span><span class="sxs-lookup"><span data-stu-id="ef70a-134">*Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user</span></span>
* <span data-ttu-id="ef70a-135">*引力對齊維護對使用者的旋轉*：將物件的原始旋轉維護給使用者，但讓物件垂直。</span><span class="sxs-lookup"><span data-stu-id="ef70a-135">*Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical.</span></span> <span data-ttu-id="ef70a-136">適用于具有界限控制項的物件。</span><span class="sxs-lookup"><span data-stu-id="ef70a-136">Useful for objects with a bounds control.</span></span>
* <span data-ttu-id="ef70a-137">*臉部使用者*：確保物件一律會臉部給使用者。</span><span class="sxs-lookup"><span data-stu-id="ef70a-137">*Face user*: Ensures object always faces the user.</span></span> <span data-ttu-id="ef70a-138">適用于平板/面板。</span><span class="sxs-lookup"><span data-stu-id="ef70a-138">Useful for slates/panels.</span></span>
* <span data-ttu-id="ef70a-139">*離開使用者的臉部*：確保物件永遠都不會離開使用者。</span><span class="sxs-lookup"><span data-stu-id="ef70a-139">*Face away from user*: Ensures object always faces away from user.</span></span> <span data-ttu-id="ef70a-140">適用于已設定反向的平板/面板。</span><span class="sxs-lookup"><span data-stu-id="ef70a-140">Useful for slates/panels that are configured backwards.</span></span>
* <span data-ttu-id="ef70a-141">*旋轉物件中心*：僅適用于已明確說明的手/控制器。</span><span class="sxs-lookup"><span data-stu-id="ef70a-141">*Rotate about object center*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="ef70a-142">使用手形/控制器的旋轉旋轉物件，但關於物件中心點。</span><span class="sxs-lookup"><span data-stu-id="ef70a-142">Rotate object using rotation of the hand/controller, but about the object center point.</span></span> <span data-ttu-id="ef70a-143">適用于檢查距離。</span><span class="sxs-lookup"><span data-stu-id="ef70a-143">Useful for inspecting at a distance.</span></span>
* <span data-ttu-id="ef70a-144">*旋轉大約抓取點*：僅適用于已明確說明的手/控制器。</span><span class="sxs-lookup"><span data-stu-id="ef70a-144">*Rotate about grab point*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="ef70a-145">旋轉物件，如同由手動/控制器持有一樣。</span><span class="sxs-lookup"><span data-stu-id="ef70a-145">Rotate object as if it was being held by hand/controller.</span></span> <span data-ttu-id="ef70a-146">適用于檢查。</span><span class="sxs-lookup"><span data-stu-id="ef70a-146">Useful for inspection.</span></span>

<span data-ttu-id="ef70a-147">**發行行為** 釋放物件時，請指定其實體移動行為。</span><span class="sxs-lookup"><span data-stu-id="ef70a-147">**Release Behavior** When an object is released, specify its physical movement behavior.</span></span> <span data-ttu-id="ef70a-148">要求 rigidbody 元件必須在該物件上。</span><span class="sxs-lookup"><span data-stu-id="ef70a-148">Requires a rigidbody component to be on that object.</span></span>

* <span data-ttu-id="ef70a-149">*Nothing*</span><span class="sxs-lookup"><span data-stu-id="ef70a-149">*Nothing*</span></span>
* <span data-ttu-id="ef70a-150">*所有項目*</span><span class="sxs-lookup"><span data-stu-id="ef70a-150">*Everything*</span></span>
* <span data-ttu-id="ef70a-151">*保持速度*</span><span class="sxs-lookup"><span data-stu-id="ef70a-151">*Keep Velocity*</span></span>
* <span data-ttu-id="ef70a-152">*保持角度速度*</span><span class="sxs-lookup"><span data-stu-id="ef70a-152">*Keep Angular Velocity*</span></span>

<span data-ttu-id="ef70a-153">**旋轉的條件約束** 指定當互動時，物件將旋轉的軸。</span><span class="sxs-lookup"><span data-stu-id="ef70a-153">**Constraints on Rotation** Specifies on which axis the object will rotate when interacted with.</span></span>

* <span data-ttu-id="ef70a-154">*None*</span><span class="sxs-lookup"><span data-stu-id="ef70a-154">*None*</span></span>
* <span data-ttu-id="ef70a-155">*僅限 X 軸*</span><span class="sxs-lookup"><span data-stu-id="ef70a-155">*X-Axis Only*</span></span>
* <span data-ttu-id="ef70a-156">*僅 Y 軸*</span><span class="sxs-lookup"><span data-stu-id="ef70a-156">*Y-Axis Only*</span></span>
* <span data-ttu-id="ef70a-157">*僅 Z 軸*</span><span class="sxs-lookup"><span data-stu-id="ef70a-157">*Z-Axis Only*</span></span>

<span data-ttu-id="ef70a-158">**使用本機空間進行條件約束** 切換在套用條件約束與全球空間軸或本機空間軸之間的切換。</span><span class="sxs-lookup"><span data-stu-id="ef70a-158">**Use Local Space For Constraint** A toggle to switch between applying constraints in respect to world-space axis, or local space axis.</span></span>

<span data-ttu-id="ef70a-159">**移動時的條件約束**</span><span class="sxs-lookup"><span data-stu-id="ef70a-159">**Constraints on Movement**</span></span>

* <span data-ttu-id="ef70a-160">*None*</span><span class="sxs-lookup"><span data-stu-id="ef70a-160">*None*</span></span>
* <span data-ttu-id="ef70a-161">*修正與 head 之間的距離*</span><span class="sxs-lookup"><span data-stu-id="ef70a-161">*Fix distance from head*</span></span>

<span data-ttu-id="ef70a-162">**啟用平滑** 指定是否啟用平滑處理。</span><span class="sxs-lookup"><span data-stu-id="ef70a-162">**Smoothing Active** Specifies whether smoothing is active.</span></span>

<span data-ttu-id="ef70a-163">**平滑量一手勢** 要套用到移動、縮放、旋轉的凹凸貼圖數量。</span><span class="sxs-lookup"><span data-stu-id="ef70a-163">**Smoothing Amount One Hand** Amount of smoothing to apply to the movement, scale, rotation.</span></span> <span data-ttu-id="ef70a-164">將0平滑表示無平滑。</span><span class="sxs-lookup"><span data-stu-id="ef70a-164">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="ef70a-165">最大值表示不變更值。</span><span class="sxs-lookup"><span data-stu-id="ef70a-165">Max value means no change to value.</span></span>

## <a name="events"></a><span data-ttu-id="ef70a-166">事件</span><span class="sxs-lookup"><span data-stu-id="ef70a-166">Events</span></span>

<span data-ttu-id="ef70a-167">操作處理常式會提供下列事件：</span><span class="sxs-lookup"><span data-stu-id="ef70a-167">Manipulation handler provides the following events:</span></span>

* <span data-ttu-id="ef70a-168">*OnManipulationStarted*：在操作開始時引發。</span><span class="sxs-lookup"><span data-stu-id="ef70a-168">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
* <span data-ttu-id="ef70a-169">*OnManipulationEnded*：在操作結束時引發。</span><span class="sxs-lookup"><span data-stu-id="ef70a-169">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
* <span data-ttu-id="ef70a-170">*OnHoverStarted*：當手形/控制器停留在接近或遠的 manipulatable 時，就會引發。</span><span class="sxs-lookup"><span data-stu-id="ef70a-170">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
* <span data-ttu-id="ef70a-171">*OnHoverEnded*：當手形/控制器取消暫留 manipulatable 時（接近或遠）時，就會引發。</span><span class="sxs-lookup"><span data-stu-id="ef70a-171">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>
