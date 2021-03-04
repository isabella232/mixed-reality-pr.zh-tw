---
title: README_ObjectManipulator
description: 如何在 MRTK 中使用物件操作工具
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、物件操作、
ms.openlocfilehash: 0e315c62261febd535452fb21bde4d56a585b295
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780971"
---
# <a name="object-manipulator"></a><span data-ttu-id="d6913-104">物件操作工具</span><span class="sxs-lookup"><span data-stu-id="d6913-104">Object manipulator</span></span>

![物件操作工具主](Images/ManipulationHandler/MRTK_Manipulation_Main.png)

<span data-ttu-id="d6913-106">*ObjectManipulator* 是操作行為的新元件，先前在 *ManipulationHandler* 中找到。</span><span class="sxs-lookup"><span data-stu-id="d6913-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="d6913-107">物件操作工具可進行許多改進和簡化。</span><span class="sxs-lookup"><span data-stu-id="d6913-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="d6913-108">此元件取代了將被取代的操作處理常式。</span><span class="sxs-lookup"><span data-stu-id="d6913-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="d6913-109">*ObjectManipulator* 腳本會使用一或兩個手來讓物件可移動、可擴充及 rotatable。</span><span class="sxs-lookup"><span data-stu-id="d6913-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="d6913-110">物件操作工具可以設定為控制物件將如何回應各種輸入。</span><span class="sxs-lookup"><span data-stu-id="d6913-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="d6913-111">腳本應可搭配大部分的互動形式使用，例如 HoloLens 2 的有向的手勢、HoloLens 2 手片片、HoloLens 1 注視和手勢，以及沉浸式耳機移動控制器輸入。</span><span class="sxs-lookup"><span data-stu-id="d6913-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="d6913-112">如何使用物件操作工具</span><span class="sxs-lookup"><span data-stu-id="d6913-112">How to use the object manipulator</span></span>

<span data-ttu-id="d6913-113">若要使用物件操作工具，請先將 `ObjectManipulator` 腳本元件加入至 GameObject。</span><span class="sxs-lookup"><span data-stu-id="d6913-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="d6913-114">請務必同時將碰撞新增至物件，以符合其 grabbable 界限。</span><span class="sxs-lookup"><span data-stu-id="d6913-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="d6913-115">若要讓物件回應接近明確的手輸入，請新增 `NearInteractionGrabbable` 腳本。</span><span class="sxs-lookup"><span data-stu-id="d6913-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="d6913-116">將 rigidbody 元件新增至物件，即可為物件操作工具啟用物理行為。</span><span class="sxs-lookup"><span data-stu-id="d6913-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="d6913-117">新增此元件所啟用的物理行為會在 [*物理和衝突*](#physics-and-collisions)中更詳細地討論。</span><span class="sxs-lookup"><span data-stu-id="d6913-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="d6913-118">如此一來，就可以將 [操作條件約束元件](#transform-constraints) 加入至物件，以限制操作。</span><span class="sxs-lookup"><span data-stu-id="d6913-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](#transform-constraints) to the object.</span></span> <span data-ttu-id="d6913-119">這些是使用操作的特殊元件，並以某種方式變更操作行為。</span><span class="sxs-lookup"><span data-stu-id="d6913-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![操作處理常式](Images/ObjectManipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="d6913-121">偵測器屬性和欄位</span><span class="sxs-lookup"><span data-stu-id="d6913-121">Inspector properties and fields</span></span>

<img src="Images/ObjectManipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="d6913-122">一般屬性</span><span class="sxs-lookup"><span data-stu-id="d6913-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="d6913-123">主機轉換</span><span class="sxs-lookup"><span data-stu-id="d6913-123">Host transform</span></span>

<span data-ttu-id="d6913-124">將操作的物件轉換。</span><span class="sxs-lookup"><span data-stu-id="d6913-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="d6913-125">預設為元件的物件。</span><span class="sxs-lookup"><span data-stu-id="d6913-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="d6913-126">操作類型</span><span class="sxs-lookup"><span data-stu-id="d6913-126">Manipulation type</span></span>

<span data-ttu-id="d6913-127">指定是否可使用一或兩個手來操作物件。</span><span class="sxs-lookup"><span data-stu-id="d6913-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="d6913-128">因為這個屬性是一個旗標，所以可以選取兩個選項。</span><span class="sxs-lookup"><span data-stu-id="d6913-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="d6913-129">*一個右手*：如果選取，則會啟用一次操作。</span><span class="sxs-lookup"><span data-stu-id="d6913-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="d6913-130">*兩個右手*：啟用兩個執行中的操作（如果有選取）。</span><span class="sxs-lookup"><span data-stu-id="d6913-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="d6913-131">允許目前的操作</span><span class="sxs-lookup"><span data-stu-id="d6913-131">Allow far manipulation</span></span>

<span data-ttu-id="d6913-132">指定是否可以使用與指標互動的方式來執行操作。</span><span class="sxs-lookup"><span data-stu-id="d6913-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="d6913-133">一個右手操作屬性</span><span class="sxs-lookup"><span data-stu-id="d6913-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="d6913-134">接近的一次旋轉模式</span><span class="sxs-lookup"><span data-stu-id="d6913-134">One hand rotation mode near</span></span>

<span data-ttu-id="d6913-135">指定當物件正在抓取時，物件的行為方式。</span><span class="sxs-lookup"><span data-stu-id="d6913-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="d6913-136">這些選項僅適用于已表達的手。</span><span class="sxs-lookup"><span data-stu-id="d6913-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="d6913-137">*旋轉物件中心*：物件使用旋轉旋轉，但關於物件中心點。</span><span class="sxs-lookup"><span data-stu-id="d6913-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="d6913-138">物件會在旋轉時變得較小，但您可能會覺得手和物件之間的連接中斷。</span><span class="sxs-lookup"><span data-stu-id="d6913-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="d6913-139">更適用于目前的互動。</span><span class="sxs-lookup"><span data-stu-id="d6913-139">More useful for far interaction.</span></span>
- <span data-ttu-id="d6913-140">*旋轉大約抓取點*：旋轉物件，並將 thumb 與食指之間的抓取點旋轉。</span><span class="sxs-lookup"><span data-stu-id="d6913-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="d6913-141">它應該會像是物件被手鎖起來。</span><span class="sxs-lookup"><span data-stu-id="d6913-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="d6913-142">一種手邊的旋轉模式</span><span class="sxs-lookup"><span data-stu-id="d6913-142">One hand rotation mode far</span></span>

<span data-ttu-id="d6913-143">指定物件在一次抓取時，該物件將如何運作。</span><span class="sxs-lookup"><span data-stu-id="d6913-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="d6913-144">這些選項僅適用于已表達的手。</span><span class="sxs-lookup"><span data-stu-id="d6913-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="d6913-145">*旋轉物件中心*：使用手旋轉旋轉物件，但關於物件中心點。</span><span class="sxs-lookup"><span data-stu-id="d6913-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="d6913-146">很適合用來檢查距離，而不會在物件中心隨著物件旋轉而移動。</span><span class="sxs-lookup"><span data-stu-id="d6913-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="d6913-147">*旋轉大約抓取點*：使用手旋轉旋轉物件，但指標光線叫用點則會旋轉。</span><span class="sxs-lookup"><span data-stu-id="d6913-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="d6913-148">適用于檢查。</span><span class="sxs-lookup"><span data-stu-id="d6913-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="d6913-149">兩個右手操作屬性</span><span class="sxs-lookup"><span data-stu-id="d6913-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="d6913-150">兩個右手操作類型</span><span class="sxs-lookup"><span data-stu-id="d6913-150">Two handed manipulation type</span></span>

<span data-ttu-id="d6913-151">指定兩次手操作如何轉換物件。</span><span class="sxs-lookup"><span data-stu-id="d6913-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="d6913-152">因為此屬性是旗標，所以可以選取任何數目的選項。</span><span class="sxs-lookup"><span data-stu-id="d6913-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="d6913-153">*移動*：若已選取，則允許移動。</span><span class="sxs-lookup"><span data-stu-id="d6913-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="d6913-154">*調整*：若已選取，則允許縮放。</span><span class="sxs-lookup"><span data-stu-id="d6913-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="d6913-155">*旋轉*：若已選取，則允許旋轉。</span><span class="sxs-lookup"><span data-stu-id="d6913-155">*Rotate*: Rotation is allowed if selected.</span></span>

![操作處理常式](Images/ManipulationHandler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="d6913-157">條件約束</span><span class="sxs-lookup"><span data-stu-id="d6913-157">Constraints</span></span>

#### <a name="add-constraint"></a><span data-ttu-id="d6913-158">新增條件約束</span><span class="sxs-lookup"><span data-stu-id="d6913-158">Add constraint</span></span>

<span data-ttu-id="d6913-159">此按鈕可讓您直接從物件操作工具偵測器加入條件約束元件。</span><span class="sxs-lookup"><span data-stu-id="d6913-159">This button allows a constraint component to be added directly from the object manipulator inspector.</span></span> <span data-ttu-id="d6913-160">專案中應該會顯示專案中的所有條件約束。</span><span class="sxs-lookup"><span data-stu-id="d6913-160">All constraints in a project should be visible here.</span></span> <span data-ttu-id="d6913-161">如需詳細資訊，請參閱 [轉換條件約束](#transform-constraints) 。</span><span class="sxs-lookup"><span data-stu-id="d6913-161">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="d6913-162">移至元件</span><span class="sxs-lookup"><span data-stu-id="d6913-162">Go to component</span></span>

<span data-ttu-id="d6913-163">在此物件上找到的所有條件約束，都會在這裡列出，並顯示 [ *移至元件* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d6913-163">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="d6913-164">此按鈕會讓偵測器滾動至選取的條件約束元件，以便進行設定。</span><span class="sxs-lookup"><span data-stu-id="d6913-164">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="d6913-165">物理特性</span><span class="sxs-lookup"><span data-stu-id="d6913-165">Physics</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="d6913-166">發行行為</span><span class="sxs-lookup"><span data-stu-id="d6913-166">Release behavior</span></span>

<span data-ttu-id="d6913-167">指定操作物件在發行時應保留的實體屬性。</span><span class="sxs-lookup"><span data-stu-id="d6913-167">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="d6913-168">要求 rigidbody 元件必須在該物件上。</span><span class="sxs-lookup"><span data-stu-id="d6913-168">Requires a rigidbody component to be on that object.</span></span> <span data-ttu-id="d6913-169">因為這個屬性是一個旗標，所以可以選取兩個選項。</span><span class="sxs-lookup"><span data-stu-id="d6913-169">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="d6913-170">*保持速度*：當物件被選取時，如果選取此選項，則會保留其線性速度。</span><span class="sxs-lookup"><span data-stu-id="d6913-170">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="d6913-171">*保持角度*：當物件被選取時，如果已選取此選項，則會維持其角度的速度。</span><span class="sxs-lookup"><span data-stu-id="d6913-171">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

### <a name="smoothing"></a><span data-ttu-id="d6913-172">平滑處理</span><span class="sxs-lookup"><span data-stu-id="d6913-172">Smoothing</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="d6913-173">啟用平滑</span><span class="sxs-lookup"><span data-stu-id="d6913-173">Smoothing active</span></span>

<span data-ttu-id="d6913-174">指定是否啟用平滑處理。</span><span class="sxs-lookup"><span data-stu-id="d6913-174">Specifies whether smoothing is active.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="d6913-175">移動 lerp 時間</span><span class="sxs-lookup"><span data-stu-id="d6913-175">Move lerp time</span></span>

<span data-ttu-id="d6913-176">要套用至移動的凹凸貼圖數量。</span><span class="sxs-lookup"><span data-stu-id="d6913-176">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="d6913-177">將0平滑表示無平滑。</span><span class="sxs-lookup"><span data-stu-id="d6913-177">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="d6913-178">最大值表示不變更值。</span><span class="sxs-lookup"><span data-stu-id="d6913-178">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="d6913-179">輪替 lerp 時間</span><span class="sxs-lookup"><span data-stu-id="d6913-179">Rotate lerp time</span></span>

<span data-ttu-id="d6913-180">要套用至旋轉的凹凸貼圖數量。</span><span class="sxs-lookup"><span data-stu-id="d6913-180">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="d6913-181">將0平滑表示無平滑。</span><span class="sxs-lookup"><span data-stu-id="d6913-181">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="d6913-182">最大值表示不變更值。</span><span class="sxs-lookup"><span data-stu-id="d6913-182">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="d6913-183">調整 lerp 時間</span><span class="sxs-lookup"><span data-stu-id="d6913-183">Scale lerp time</span></span>

<span data-ttu-id="d6913-184">要套用至尺規的凹凸貼圖數量。</span><span class="sxs-lookup"><span data-stu-id="d6913-184">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="d6913-185">將0平滑表示無平滑。</span><span class="sxs-lookup"><span data-stu-id="d6913-185">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="d6913-186">最大值表示不變更值。</span><span class="sxs-lookup"><span data-stu-id="d6913-186">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="d6913-187">操作事件</span><span class="sxs-lookup"><span data-stu-id="d6913-187">Manipulation events</span></span>

<span data-ttu-id="d6913-188">操作處理常式會提供下列事件：</span><span class="sxs-lookup"><span data-stu-id="d6913-188">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="d6913-189">*OnManipulationStarted*：在操作開始時引發。</span><span class="sxs-lookup"><span data-stu-id="d6913-189">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="d6913-190">*OnManipulationEnded*：在操作結束時引發。</span><span class="sxs-lookup"><span data-stu-id="d6913-190">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="d6913-191">*OnHoverStarted*：當手形/控制器停留在接近或遠的 manipulatable 時，就會引發。</span><span class="sxs-lookup"><span data-stu-id="d6913-191">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="d6913-192">*OnHoverEnded*：當手形/控制器取消暫留 manipulatable 時（接近或遠）時，就會引發。</span><span class="sxs-lookup"><span data-stu-id="d6913-192">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="d6913-193">操作的事件引發順序為：</span><span class="sxs-lookup"><span data-stu-id="d6913-193">The event fire order for manipulation is:</span></span>

<span data-ttu-id="d6913-194">*OnHoverStarted*  -> *OnManipulationStarted*  -> *OnManipulationEnded*  -> *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="d6913-194">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="d6913-195">如果沒有操作，您仍會收到具有下列引發順序的暫止事件：</span><span class="sxs-lookup"><span data-stu-id="d6913-195">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="d6913-196">*OnHoverStarted*  -> *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="d6913-196">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="d6913-197">轉換條件約束</span><span class="sxs-lookup"><span data-stu-id="d6913-197">Transform constraints</span></span>

<span data-ttu-id="d6913-198">條件約束可以用來限制操作的方式。</span><span class="sxs-lookup"><span data-stu-id="d6913-198">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="d6913-199">例如，有些應用程式可能需要輪替，但物件也需要保持垂直。</span><span class="sxs-lookup"><span data-stu-id="d6913-199">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="d6913-200">在此情況下，您 `RotationAxisConstraint` 可以將加入至物件，並用來將旋轉限制為 y 軸旋轉。</span><span class="sxs-lookup"><span data-stu-id="d6913-200">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="d6913-201">MRTK 提供許多條件約束，如下所述。</span><span class="sxs-lookup"><span data-stu-id="d6913-201">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="d6913-202">您也可以定義新的條件約束，並使用它們來建立某些應用程式可能需要的獨特操作行為。</span><span class="sxs-lookup"><span data-stu-id="d6913-202">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="d6913-203">若要這樣做，請建立一個繼承自 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 的腳本，並執行抽象 `ConstraintType` 屬性和抽象 `ApplyConstraint` 方法。</span><span class="sxs-lookup"><span data-stu-id="d6913-203">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="d6913-204">將新的條件約束加入至物件時，它應該會以定義的方式來限制操作。</span><span class="sxs-lookup"><span data-stu-id="d6913-204">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="d6913-205">這個新的條件約束也應該顯示在物件操作工具 [條件限制欄位](#constraints)中。</span><span class="sxs-lookup"><span data-stu-id="d6913-205">This new constraint should also show in the object manipulator [constraint fields](#constraints).</span></span>

<span data-ttu-id="d6913-206">MRTK 提供的所有條件約束都會共用下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d6913-206">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="target-transform"></a><span data-ttu-id="d6913-207">目標轉換</span><span class="sxs-lookup"><span data-stu-id="d6913-207">Target Transform</span></span>

<span data-ttu-id="d6913-208">受限制的操作物件轉換。</span><span class="sxs-lookup"><span data-stu-id="d6913-208">Transform of the manipulated object being constrained.</span></span> <span data-ttu-id="d6913-209">這應該與 ObjectManipulator [*主機轉換*](#host-transform)相同。</span><span class="sxs-lookup"><span data-stu-id="d6913-209">This should be the same as the ObjectManipulator [*Host transform*](#host-transform).</span></span> <span data-ttu-id="d6913-210">預設為元件的物件。</span><span class="sxs-lookup"><span data-stu-id="d6913-210">Defaults to the object of the component.</span></span>

#### <a name="hand-type"></a><span data-ttu-id="d6913-211">手型別</span><span class="sxs-lookup"><span data-stu-id="d6913-211">Hand Type</span></span>

<span data-ttu-id="d6913-212">指定是否要將條件約束用於一或兩種類型的操作。</span><span class="sxs-lookup"><span data-stu-id="d6913-212">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="d6913-213">因為這個屬性是一個旗標，所以可以選取兩個選項。</span><span class="sxs-lookup"><span data-stu-id="d6913-213">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="d6913-214">*一個右手*：條件約束會在一次執行時使用，如果選取的話。</span><span class="sxs-lookup"><span data-stu-id="d6913-214">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="d6913-215">*兩個右手*：條件約束將在兩個強制操作期間使用（如果選取）。</span><span class="sxs-lookup"><span data-stu-id="d6913-215">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="d6913-216">鄰近型別</span><span class="sxs-lookup"><span data-stu-id="d6913-216">Proximity Type</span></span>

<span data-ttu-id="d6913-217">指定是否要將條件約束用於接近、遠或兩種類型的操作。</span><span class="sxs-lookup"><span data-stu-id="d6913-217">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="d6913-218">因為這個屬性是一個旗標，所以可以選取兩個選項。</span><span class="sxs-lookup"><span data-stu-id="d6913-218">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="d6913-219">*Near*：若選取此選項，則會在接近操作期間使用條件約束。</span><span class="sxs-lookup"><span data-stu-id="d6913-219">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="d6913-220">*目前為止*：如果選取，就會在目前的操作期間使用條件約束。</span><span class="sxs-lookup"><span data-stu-id="d6913-220">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="d6913-221">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="d6913-221">FaceUserConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint face user">

<span data-ttu-id="d6913-222">當這個條件約束附加到物件時，旋轉將會受到限制，因此物件一律會面對使用者。</span><span class="sxs-lookup"><span data-stu-id="d6913-222">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="d6913-223">這對平板或面板很有用。</span><span class="sxs-lookup"><span data-stu-id="d6913-223">This is useful for slates or panels.</span></span> <span data-ttu-id="d6913-224">的屬性如下所示 `FaceUserConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="d6913-224">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="d6913-225">臉部離開</span><span class="sxs-lookup"><span data-stu-id="d6913-225">Face away</span></span>

<span data-ttu-id="d6913-226">若為 true，則物件會離開使用者。</span><span class="sxs-lookup"><span data-stu-id="d6913-226">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="d6913-227">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="d6913-227">FixedDistanceConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="constraintt fixed distance">

<span data-ttu-id="d6913-228">這個條件約束會修正操作物件與操作啟動時的另一個物件轉換之間的距離。</span><span class="sxs-lookup"><span data-stu-id="d6913-228">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="d6913-229">這適用于將操作物件的距離修正至 head 轉換的行為。</span><span class="sxs-lookup"><span data-stu-id="d6913-229">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="d6913-230">的屬性如下所示 `FixedDistanceConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="d6913-230">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="d6913-231">條件約束轉換</span><span class="sxs-lookup"><span data-stu-id="d6913-231">Constraint transform</span></span>

<span data-ttu-id="d6913-232">這是操作物件將會有固定距離的另一個轉換。</span><span class="sxs-lookup"><span data-stu-id="d6913-232">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="d6913-233">預設為相機轉換。</span><span class="sxs-lookup"><span data-stu-id="d6913-233">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="d6913-234">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="d6913-234">FixedRotationToUserConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed rotation to user">

<span data-ttu-id="d6913-235">此條件約束會修正使用者與操作中物件之間的相對旋轉。</span><span class="sxs-lookup"><span data-stu-id="d6913-235">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="d6913-236">這對平板或面板很有用，因為它可確保操作物件一律會顯示相同的臉部給使用者，如同操作開始時一樣。</span><span class="sxs-lookup"><span data-stu-id="d6913-236">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="d6913-237">沒有 `FixedRotationToUserConstraint` 任何唯一的屬性。</span><span class="sxs-lookup"><span data-stu-id="d6913-237">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="d6913-238">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="d6913-238">FixedRotationToWorldConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to world">

<span data-ttu-id="d6913-239">此條件約束可修正操作物件在操作時的全域旋轉。</span><span class="sxs-lookup"><span data-stu-id="d6913-239">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="d6913-240">如果不應該透過操作來給予任何旋轉，這項功能就很有用。</span><span class="sxs-lookup"><span data-stu-id="d6913-240">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="d6913-241">沒有 `FixedRotationToWorldConstraint` 任何唯一的屬性：</span><span class="sxs-lookup"><span data-stu-id="d6913-241">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="d6913-242">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="d6913-242">MaintainApparentSizeConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent Size">

<span data-ttu-id="d6913-243">當這個條件約束附加到物件時，無論物件與使用者之間的距離為何，它都會維持與使用者相同的明顯大小 (也就是，它所占的使用者欄位的比例) 。</span><span class="sxs-lookup"><span data-stu-id="d6913-243">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="d6913-244">這可以用來確保在操作時，平板或文字面板仍可讀取。</span><span class="sxs-lookup"><span data-stu-id="d6913-244">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="d6913-245">沒有 `MaintainApparentSizeConstraint` 任何唯一的屬性：</span><span class="sxs-lookup"><span data-stu-id="d6913-245">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="d6913-246">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="d6913-246">MoveAxisConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="d6913-247">這個條件約束可以用來修正可以移動操作物件的座標軸。</span><span class="sxs-lookup"><span data-stu-id="d6913-247">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="d6913-248">當您在平面表面或線條上操作物件時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="d6913-248">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="d6913-249">的屬性如下所示 `MoveAxisConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="d6913-249">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="d6913-250">移動時的條件約束</span><span class="sxs-lookup"><span data-stu-id="d6913-250">Constraint on movement</span></span>

<span data-ttu-id="d6913-251">指定要防止移動的座標軸。</span><span class="sxs-lookup"><span data-stu-id="d6913-251">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="d6913-252">依預設，這些軸會是全域的，而不是本機，但可在下方變更。</span><span class="sxs-lookup"><span data-stu-id="d6913-252">By default these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="d6913-253">因為此屬性是旗標，所以可以選取任何數目的選項。</span><span class="sxs-lookup"><span data-stu-id="d6913-253">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="d6913-254">*X 軸*：如果選取，沿著 X 軸移動會受到限制。</span><span class="sxs-lookup"><span data-stu-id="d6913-254">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="d6913-255">*Y 軸*：如果選取，沿著 y 軸的移動會受到限制。</span><span class="sxs-lookup"><span data-stu-id="d6913-255">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="d6913-256">*Z 軸*：如果選取，沿著 Z 軸的移動會受到限制。</span><span class="sxs-lookup"><span data-stu-id="d6913-256">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="d6913-257">使用本機空間進行條件約束</span><span class="sxs-lookup"><span data-stu-id="d6913-257">Use local space for constraint</span></span>

<span data-ttu-id="d6913-258">會限制操作物件的本機轉換軸（如果為 true）。</span><span class="sxs-lookup"><span data-stu-id="d6913-258">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="d6913-259">預設為 False。</span><span class="sxs-lookup"><span data-stu-id="d6913-259">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="d6913-260">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="d6913-260">RotationAxisConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="d6913-261">這個條件約束可以用來修正哪些軸可以旋轉可操作的物件。</span><span class="sxs-lookup"><span data-stu-id="d6913-261">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="d6913-262">這有助於讓操作物件保持垂直，但仍允許 y 軸旋轉（例如）。</span><span class="sxs-lookup"><span data-stu-id="d6913-262">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="d6913-263">的屬性如下所示 `RotationAxisConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="d6913-263">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="d6913-264">旋轉的條件約束</span><span class="sxs-lookup"><span data-stu-id="d6913-264">Constraint on rotation</span></span>

<span data-ttu-id="d6913-265">指定要防止旋轉的座標軸。</span><span class="sxs-lookup"><span data-stu-id="d6913-265">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="d6913-266">依預設，這些軸會是全域的，而不是本機，但可在下方變更。</span><span class="sxs-lookup"><span data-stu-id="d6913-266">By default these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="d6913-267">因為此屬性是旗標，所以可以選取任何數目的選項。</span><span class="sxs-lookup"><span data-stu-id="d6913-267">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="d6913-268">*Y 軸*：如有選取，y 軸的旋轉會受到限制。</span><span class="sxs-lookup"><span data-stu-id="d6913-268">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="d6913-269">*Z 軸*：若已選取，則會限制 Z 軸的旋轉。</span><span class="sxs-lookup"><span data-stu-id="d6913-269">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="d6913-270">*X 軸*：若已選取，則會限制 X 軸的旋轉。</span><span class="sxs-lookup"><span data-stu-id="d6913-270">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="d6913-271">使用本機空間進行條件約束</span><span class="sxs-lookup"><span data-stu-id="d6913-271">Use local space for constraint</span></span>

<span data-ttu-id="d6913-272">會限制操作物件的本機轉換軸（如果為 true）。</span><span class="sxs-lookup"><span data-stu-id="d6913-272">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="d6913-273">預設為 False。</span><span class="sxs-lookup"><span data-stu-id="d6913-273">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="d6913-274">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="d6913-274">MinMaxScaleConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="MinMax Scale">

<span data-ttu-id="d6913-275">這個條件約束允許為操作物件的小數位數設定最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="d6913-275">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="d6913-276">這有助於防止使用者調整太小或太大的物件。</span><span class="sxs-lookup"><span data-stu-id="d6913-276">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="d6913-277">的屬性如下所示 `MinMaxScaleConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="d6913-277">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="d6913-278">最小規模</span><span class="sxs-lookup"><span data-stu-id="d6913-278">Scale minimum</span></span>

<span data-ttu-id="d6913-279">操作期間的最小縮放值。</span><span class="sxs-lookup"><span data-stu-id="d6913-279">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="d6913-280">調整最大值</span><span class="sxs-lookup"><span data-stu-id="d6913-280">Scale maximum</span></span>

<span data-ttu-id="d6913-281">操作期間的最大縮放值。</span><span class="sxs-lookup"><span data-stu-id="d6913-281">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="d6913-282">相對於初始狀態</span><span class="sxs-lookup"><span data-stu-id="d6913-282">Relative to initial state</span></span>

<span data-ttu-id="d6913-283">若為 true，則會將上述值轉譯為相對於物件初始縮放比例的值。</span><span class="sxs-lookup"><span data-stu-id="d6913-283">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="d6913-284">否則，它們會被視為絕對規模值。</span><span class="sxs-lookup"><span data-stu-id="d6913-284">Otherwise they will be interpreted as absolute scale values.</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="d6913-285">物理與衝突</span><span class="sxs-lookup"><span data-stu-id="d6913-285">Physics and collisions</span></span>

<span data-ttu-id="d6913-286">將 rigidbody 元件新增至與物件操作工具相同的物件，即可啟用物理行為。</span><span class="sxs-lookup"><span data-stu-id="d6913-286">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="d6913-287">這並不只可讓您設定上述的 [發行行為](#release-behavior) ，也會啟用衝突。</span><span class="sxs-lookup"><span data-stu-id="d6913-287">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="d6913-288">如果沒有 rigidbody 元件，則在操作期間，衝突的運作方式不正確：</span><span class="sxs-lookup"><span data-stu-id="d6913-288">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="d6913-289">操作物件和靜態碰撞程式之間的衝突 (也就是具有碰撞程式但沒有 rigidbody) 的物件無法運作，操作的物件會直接透過靜態碰撞碰撞來傳遞，而不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="d6913-289">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="d6913-290">操作物件與 rigidbody 之間的衝突 (例如</span><span class="sxs-lookup"><span data-stu-id="d6913-290">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="d6913-291">具有碰撞器和 rigidbody 的物件) 會導致 rigidbody 有碰撞回應，但回應是跳動和非自然。</span><span class="sxs-lookup"><span data-stu-id="d6913-291">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="d6913-292">在操作物件上也沒有衝突回應。</span><span class="sxs-lookup"><span data-stu-id="d6913-292">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="d6913-293">新增 rigidbody 時，衝突應該會正常運作。</span><span class="sxs-lookup"><span data-stu-id="d6913-293">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="d6913-294">沒有 rigidbody</span><span class="sxs-lookup"><span data-stu-id="d6913-294">Without rigidbody</span></span>

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="d6913-295">使用 rigidbody</span><span class="sxs-lookup"><span data-stu-id="d6913-295">With rigidbody</span></span>

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">
