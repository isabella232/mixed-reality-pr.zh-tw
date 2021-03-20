---
title: ObjectManipulator
description: 如何在 MRTK 中使用物件操作工具
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、物件操作、
ms.openlocfilehash: 1c65076c1e2bc97d5b3ed72fcfe2afcaafef0736
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689168"
---
# <a name="object-manipulator"></a><span data-ttu-id="0ed9d-104">物件操作工具</span><span class="sxs-lookup"><span data-stu-id="0ed9d-104">Object manipulator</span></span>

![物件操作工具](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="0ed9d-106">*ObjectManipulator* 是操作行為的新元件，先前在 *ManipulationHandler* 中找到。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="0ed9d-107">物件操作工具可進行許多改進和簡化。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="0ed9d-108">此元件取代了將被取代的操作處理常式。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="0ed9d-109">*ObjectManipulator* 腳本會使用一或兩個手來讓物件可移動、可擴充及 rotatable。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="0ed9d-110">物件操作工具可以設定為控制物件將如何回應各種輸入。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="0ed9d-111">此腳本應該適用于大部分的互動形式，例如 HoloLens 2 有明確的手勢、HoloLens 2 手片、HoloLens 1 注視和手勢和沉浸式耳機移動控制器輸入。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="0ed9d-112">如何使用物件操作工具</span><span class="sxs-lookup"><span data-stu-id="0ed9d-112">How to use the object manipulator</span></span>

<span data-ttu-id="0ed9d-113">若要使用物件操作工具，請先將 `ObjectManipulator` 腳本元件加入至 GameObject。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="0ed9d-114">請務必同時將碰撞新增至物件，以符合其 grabbable 界限。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="0ed9d-115">若要讓物件回應接近明確的手輸入，請新增 `NearInteractionGrabbable` 腳本。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="0ed9d-116">將 rigidbody 元件新增至物件，即可為物件操作工具啟用物理行為。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="0ed9d-117">新增此元件所啟用的物理行為會在 [*物理和衝突*](#physics-and-collisions)中更詳細地討論。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="0ed9d-118">如此一來，就可以將 [操作條件約束元件](constraint-manager.md#transform-constraints) 加入至物件，以限制操作。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](constraint-manager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="0ed9d-119">這些是使用操作的特殊元件，並以某種方式變更操作行為。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![在 Unity 編輯器中使用操作處理常式](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="0ed9d-121">偵測器屬性和欄位</span><span class="sxs-lookup"><span data-stu-id="0ed9d-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="0ed9d-122">一般屬性</span><span class="sxs-lookup"><span data-stu-id="0ed9d-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="0ed9d-123">主機轉換</span><span class="sxs-lookup"><span data-stu-id="0ed9d-123">Host transform</span></span>

<span data-ttu-id="0ed9d-124">將操作的物件轉換。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="0ed9d-125">預設為元件的物件。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="0ed9d-126">操作類型</span><span class="sxs-lookup"><span data-stu-id="0ed9d-126">Manipulation type</span></span>

<span data-ttu-id="0ed9d-127">指定是否可使用一或兩個手來操作物件。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="0ed9d-128">因為這個屬性是一個旗標，所以可以選取兩個選項。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="0ed9d-129">*一個右手*：如果選取，則會啟用一次操作。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="0ed9d-130">*兩個右手*：啟用兩個執行中的操作（如果有選取）。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="0ed9d-131">允許目前的操作</span><span class="sxs-lookup"><span data-stu-id="0ed9d-131">Allow far manipulation</span></span>

<span data-ttu-id="0ed9d-132">指定是否可以使用與指標互動的方式來執行操作。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="0ed9d-133">一個右手操作屬性</span><span class="sxs-lookup"><span data-stu-id="0ed9d-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="0ed9d-134">接近的一次旋轉模式</span><span class="sxs-lookup"><span data-stu-id="0ed9d-134">One hand rotation mode near</span></span>

<span data-ttu-id="0ed9d-135">指定當物件正在抓取時，物件的行為方式。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="0ed9d-136">這些選項僅適用于已表達的手。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="0ed9d-137">*旋轉物件中心*：物件使用旋轉旋轉，但關於物件中心點。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="0ed9d-138">物件會在旋轉時變得較小，但您可能會覺得手和物件之間的連接中斷。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="0ed9d-139">更適用于目前的互動。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-139">More useful for far interaction.</span></span>
- <span data-ttu-id="0ed9d-140">*旋轉大約抓取點*：旋轉物件，並將 thumb 與食指之間的抓取點旋轉。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="0ed9d-141">它應該會像是物件被手鎖起來。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="0ed9d-142">一種手邊的旋轉模式</span><span class="sxs-lookup"><span data-stu-id="0ed9d-142">One hand rotation mode far</span></span>

<span data-ttu-id="0ed9d-143">指定物件在一次抓取時，該物件將如何運作。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="0ed9d-144">這些選項僅適用于已表達的手。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="0ed9d-145">*旋轉物件中心*：使用手旋轉旋轉物件，但關於物件中心點。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="0ed9d-146">很適合用來檢查距離，而不會在物件中心隨著物件旋轉而移動。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="0ed9d-147">*旋轉大約抓取點*：使用手旋轉旋轉物件，但指標光線叫用點則會旋轉。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="0ed9d-148">適用于檢查。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="0ed9d-149">兩個右手操作屬性</span><span class="sxs-lookup"><span data-stu-id="0ed9d-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="0ed9d-150">兩個右手操作類型</span><span class="sxs-lookup"><span data-stu-id="0ed9d-150">Two handed manipulation type</span></span>

<span data-ttu-id="0ed9d-151">指定兩次手操作如何轉換物件。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="0ed9d-152">因為此屬性是旗標，所以可以選取任何數目的選項。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="0ed9d-153">*移動*：若已選取，則允許移動。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="0ed9d-154">*調整*：若已選取，則允許縮放。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="0ed9d-155">*旋轉*：若已選取，則允許旋轉。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-155">*Rotate*: Rotation is allowed if selected.</span></span>

![操作處理常式](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="0ed9d-157">條件約束</span><span class="sxs-lookup"><span data-stu-id="0ed9d-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="0ed9d-158">啟用條件約束</span><span class="sxs-lookup"><span data-stu-id="0ed9d-158">Enable constraints</span></span>

<span data-ttu-id="0ed9d-159">這種設定會啟用連結的 [條件約束管理員](constraint-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-159">This setting will enable the linked [constraint manager](constraint-manager.md).</span></span> <span data-ttu-id="0ed9d-160">轉換變更將由註冊至所選 [條件約束管理員](constraint-manager.md)的條件約束處理。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-160">Transform changes will be processed by constraints registered to the selected [constraint manager](constraint-manager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="0ed9d-161">條件約束管理員</span><span class="sxs-lookup"><span data-stu-id="0ed9d-161">Constraint manager</span></span>

<span data-ttu-id="0ed9d-162">下拉式清單可讓您選取任何附加的 [條件約束管理員](constraint-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-162">The dropdown allows to select any of the attached [constraint managers](constraint-manager.md).</span></span> <span data-ttu-id="0ed9d-163">物件操作工具可確保所有時間都有附加的 [條件約束管理員](constraint-manager.md) 。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-163">Object manipulator ensures there's a [constraint manager](constraint-manager.md) attached at all times.</span></span>
<span data-ttu-id="0ed9d-164">請注意，相同類型的多個元件會顯示在 unity 中的相同名稱下。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="0ed9d-165">為了讓您可以更輕鬆地分辨相同物件上的多個條件約束管理員，可用的選項會顯示所選條件約束管理員設定的提示 (手動或自動條件約束選取) 。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="0ed9d-166">移至元件</span><span class="sxs-lookup"><span data-stu-id="0ed9d-166">Go to component</span></span>

<span data-ttu-id="0ed9d-167">條件約束管理員選項會隨附 [ *移至元件* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="0ed9d-168">此按鈕會讓偵測器滾動至選取的元件，以便進行設定。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="0ed9d-169">物理特性</span><span class="sxs-lookup"><span data-stu-id="0ed9d-169">Physics</span></span>

<span data-ttu-id="0ed9d-170">只有當物件具有 RigidBody 元件時，才會顯示此區段中的設定。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="0ed9d-171">發行行為</span><span class="sxs-lookup"><span data-stu-id="0ed9d-171">Release behavior</span></span>

<span data-ttu-id="0ed9d-172">指定操作物件在發行時應保留的實體屬性。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="0ed9d-173">因為這個屬性是一個旗標，所以可以選取兩個選項。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="0ed9d-174">*保持速度*：當物件被選取時，如果選取此選項，則會保留其線性速度。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="0ed9d-175">*保持角度*：當物件被選取時，如果已選取此選項，則會維持其角度的速度。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="0ed9d-176">使用強制進行接近操作</span><span class="sxs-lookup"><span data-stu-id="0ed9d-176">Use forces for near manipulation</span></span>

<span data-ttu-id="0ed9d-177">執行接近操作時，是否使用物理強制來移動物件。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="0ed9d-178">將此設定為 *false* 會讓物件感覺更直接連線至使用者手。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="0ed9d-179">將此設定為 *true* 將會接受物件的大量和慣性，但可能會覺得物件是透過彈簧連接的。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="0ed9d-180">預設值為 *false*。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="0ed9d-181">平滑處理</span><span class="sxs-lookup"><span data-stu-id="0ed9d-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="0ed9d-182">平滑程度</span><span class="sxs-lookup"><span data-stu-id="0ed9d-182">Smoothing far</span></span>

<span data-ttu-id="0ed9d-183">是否針對大部分的互動啟用畫面播放速率獨立平滑處理。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="0ed9d-184">目前預設會啟用凹凸貼圖。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="0ed9d-185">近乎平滑</span><span class="sxs-lookup"><span data-stu-id="0ed9d-185">Smoothing near</span></span>

<span data-ttu-id="0ed9d-186">是否針對近乎互動啟用畫面播放速率獨立平滑處理。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="0ed9d-187">預設會停用近乎平滑處理，因為效果可能會被視為「已中斷連線」。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="0ed9d-188">啟用平滑</span><span class="sxs-lookup"><span data-stu-id="0ed9d-188">Smoothing active</span></span>

<span data-ttu-id="0ed9d-189">已淘汰，將會在未來版本中移除。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="0ed9d-190">應用程式應該使用 SmoothingFar、SmoothingNear 或兩者的組合。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="0ed9d-191">移動 lerp 時間</span><span class="sxs-lookup"><span data-stu-id="0ed9d-191">Move lerp time</span></span>

<span data-ttu-id="0ed9d-192">要套用至移動的凹凸貼圖數量。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="0ed9d-193">將0平滑表示無平滑。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="0ed9d-194">最大值表示不變更值。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="0ed9d-195">輪替 lerp 時間</span><span class="sxs-lookup"><span data-stu-id="0ed9d-195">Rotate lerp time</span></span>

<span data-ttu-id="0ed9d-196">要套用至旋轉的凹凸貼圖數量。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="0ed9d-197">將0平滑表示無平滑。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="0ed9d-198">最大值表示不變更值。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="0ed9d-199">調整 lerp 時間</span><span class="sxs-lookup"><span data-stu-id="0ed9d-199">Scale lerp time</span></span>

<span data-ttu-id="0ed9d-200">要套用至尺規的凹凸貼圖數量。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="0ed9d-201">將0平滑表示無平滑。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="0ed9d-202">最大值表示不變更值。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="0ed9d-203">操作事件</span><span class="sxs-lookup"><span data-stu-id="0ed9d-203">Manipulation events</span></span>

<span data-ttu-id="0ed9d-204">操作處理常式會提供下列事件：</span><span class="sxs-lookup"><span data-stu-id="0ed9d-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="0ed9d-205">*OnManipulationStarted*：在操作開始時引發。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="0ed9d-206">*OnManipulationEnded*：在操作結束時引發。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="0ed9d-207">*OnHoverStarted*：當手形/控制器停留在接近或遠的 manipulatable 時，就會引發。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="0ed9d-208">*OnHoverEnded*：當手形/控制器取消暫留 manipulatable 時（接近或遠）時，就會引發。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="0ed9d-209">操作的事件引發順序為：</span><span class="sxs-lookup"><span data-stu-id="0ed9d-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="0ed9d-210">*OnHoverStarted*  -> *OnManipulationStarted*  -> *OnManipulationEnded*  -> *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="0ed9d-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="0ed9d-211">如果沒有操作，您仍會收到具有下列引發順序的暫止事件：</span><span class="sxs-lookup"><span data-stu-id="0ed9d-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="0ed9d-212">*OnHoverStarted*  -> *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="0ed9d-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="0ed9d-213">物理與衝突</span><span class="sxs-lookup"><span data-stu-id="0ed9d-213">Physics and collisions</span></span>

<span data-ttu-id="0ed9d-214">將 rigidbody 元件新增至與物件操作工具相同的物件，即可啟用物理行為。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="0ed9d-215">這並不只可讓您設定上述的 [發行行為](#release-behavior) ，也會啟用衝突。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="0ed9d-216">如果沒有 rigidbody 元件，則在操作期間，衝突的運作方式不正確：</span><span class="sxs-lookup"><span data-stu-id="0ed9d-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="0ed9d-217">操作物件和靜態碰撞程式之間的衝突 (也就是具有碰撞程式但沒有 rigidbody) 的物件無法運作，操作的物件會直接透過靜態碰撞碰撞來傳遞，而不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="0ed9d-218">操作物件與 rigidbody 之間的衝突 (例如</span><span class="sxs-lookup"><span data-stu-id="0ed9d-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="0ed9d-219">具有碰撞器和 rigidbody 的物件) 會導致 rigidbody 有碰撞回應，但回應是跳動和非自然。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="0ed9d-220">在操作物件上也沒有衝突回應。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="0ed9d-221">新增 rigidbody 時，衝突應該會正常運作。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="0ed9d-222">沒有 rigidbody</span><span class="sxs-lookup"><span data-stu-id="0ed9d-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="0ed9d-223">使用 rigidbody</span><span class="sxs-lookup"><span data-stu-id="0ed9d-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="0ed9d-224">彈性 (實驗性) </span><span class="sxs-lookup"><span data-stu-id="0ed9d-224">Elastics (Experimental)</span></span>

<span data-ttu-id="0ed9d-225">透過物件操作工具操作物件時，可以使用彈性。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="0ed9d-226">請注意， [彈性系統](../elastics/elastic-system.md) 仍處於實驗性狀態。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-226">Note that the [elastics system](../elastics/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="0ed9d-227">若要啟用彈性，請連結現有的彈性 manager 元件，或透過按鈕建立並連結新的彈性管理員 `Add Elastics Manager` 。</span><span class="sxs-lookup"><span data-stu-id="0ed9d-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="0ed9d-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ed9d-228">See also</span></span>

- [<span data-ttu-id="0ed9d-229">界限控制項</span><span class="sxs-lookup"><span data-stu-id="0ed9d-229">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="0ed9d-230">條件約束管理員</span><span class="sxs-lookup"><span data-stu-id="0ed9d-230">Constraint manager</span></span>](constraint-manager.md)
- [<span data-ttu-id="0ed9d-231">遷移視窗</span><span class="sxs-lookup"><span data-stu-id="0ed9d-231">Migration window</span></span>](../tools/migration-window.md)
- [<span data-ttu-id="0ed9d-232">彈性系統 (實驗性) </span><span class="sxs-lookup"><span data-stu-id="0ed9d-232">Elastics system (Experimental)</span></span>](../elastics/elastic-system.md)
