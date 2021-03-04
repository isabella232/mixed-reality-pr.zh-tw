---
title: BoundsControl
description: MRTK 中的界限控制項總覽
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、界限控制、
ms.openlocfilehash: b41465483b485f1e6b58c8f2a395f304af410596
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780915"
---
# <a name="bounds-control"></a><span data-ttu-id="436ca-104">界限控制項</span><span class="sxs-lookup"><span data-stu-id="436ca-104">Bounds control</span></span>

![界限控制項](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="436ca-106">*BoundsControl* 是操作行為的新元件，先前在 *BoundingBox* 中找到。</span><span class="sxs-lookup"><span data-stu-id="436ca-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="436ca-107">界限控制項可在安裝過程中進行許多改進和簡化，並加入新功能。</span><span class="sxs-lookup"><span data-stu-id="436ca-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="436ca-108">此元件是周框方塊的取代項，將被取代。</span><span class="sxs-lookup"><span data-stu-id="436ca-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="436ca-109">[`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl)腳本提供在混合現實中轉換物件的基本功能。</span><span class="sxs-lookup"><span data-stu-id="436ca-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="436ca-110">界限控制項將會在全像影像周圍顯示一個方塊，表示它可以與互動。</span><span class="sxs-lookup"><span data-stu-id="436ca-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="436ca-111">方塊角落和邊緣的控點可讓您縮放、旋轉或平移物件。</span><span class="sxs-lookup"><span data-stu-id="436ca-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="436ca-112">界限控制項也會對使用者輸入做出回應。</span><span class="sxs-lookup"><span data-stu-id="436ca-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="436ca-113">例如，在 HoloLens 2 上，界限控制項會回應手指附近，提供視覺回饋以協助觀察物件的距離。</span><span class="sxs-lookup"><span data-stu-id="436ca-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="436ca-114">您可以輕鬆地自訂所有互動和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="436ca-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="436ca-115">範例場景</span><span class="sxs-lookup"><span data-stu-id="436ca-115">Example scene</span></span>

<span data-ttu-id="436ca-116">您可以在場景中找到界限控制項設定的範例 `BoundsControlExamples` 。</span><span class="sxs-lookup"><span data-stu-id="436ca-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds Contol">

## <a name="inspector-properties"></a><span data-ttu-id="436ca-117">偵測器屬性</span><span class="sxs-lookup"><span data-stu-id="436ca-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="436ca-118">目標物件</span><span class="sxs-lookup"><span data-stu-id="436ca-118">Target object</span></span>

<span data-ttu-id="436ca-119">這個屬性會指定界限控制項操作要轉換的物件。</span><span class="sxs-lookup"><span data-stu-id="436ca-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="436ca-120">如果未 setit 物件，則預設為擁有者物件。</span><span class="sxs-lookup"><span data-stu-id="436ca-120">If no object is setit defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="436ca-121">啟用行為</span><span class="sxs-lookup"><span data-stu-id="436ca-121">Activation behavior</span></span>

<span data-ttu-id="436ca-122">有幾個選項可以啟動界限控制介面。</span><span class="sxs-lookup"><span data-stu-id="436ca-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="436ca-123">*啟動時啟動*：啟動場景之後，就會顯示界限控制項。</span><span class="sxs-lookup"><span data-stu-id="436ca-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="436ca-124">*依鄰近性啟動*：當有向物件接近的指標時，界限控制項就會變成可見。</span><span class="sxs-lookup"><span data-stu-id="436ca-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="436ca-125">*依指標啟用*：當邊界控制項是由手形指標設為目標時，便會顯示界限控制項。</span><span class="sxs-lookup"><span data-stu-id="436ca-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="436ca-126">*依鄰近性和指標啟動*：當其以手形指標為目標，或有向物件接近物件時，會顯示界限控制項。</span><span class="sxs-lookup"><span data-stu-id="436ca-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="436ca-127">*手動啟用*：界限控制項不會自動顯示。</span><span class="sxs-lookup"><span data-stu-id="436ca-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="436ca-128">您可以藉由存取 boundsControl 屬性，以手動方式透過腳本來啟用它。</span><span class="sxs-lookup"><span data-stu-id="436ca-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="436ca-129">界限覆寫</span><span class="sxs-lookup"><span data-stu-id="436ca-129">Bounds override</span></span>

<span data-ttu-id="436ca-130">從物件設定界限計算的方塊碰撞。</span><span class="sxs-lookup"><span data-stu-id="436ca-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="436ca-131">方塊邊框距離</span><span class="sxs-lookup"><span data-stu-id="436ca-131">Box padding</span></span>

<span data-ttu-id="436ca-132">將填補加入至用來計算控制項範圍的碰撞界線。</span><span class="sxs-lookup"><span data-stu-id="436ca-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="436ca-133">這只會影響互動，但也會影響視覺效果。</span><span class="sxs-lookup"><span data-stu-id="436ca-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="436ca-134">簡維軸</span><span class="sxs-lookup"><span data-stu-id="436ca-134">Flatten axis</span></span>

<span data-ttu-id="436ca-135">指出控制項是否在其中一個座標軸上簡維，使其成為2維度，而且不允許沿著該軸操作。</span><span class="sxs-lookup"><span data-stu-id="436ca-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="436ca-136">這項功能可用於精簡型物件（例如平板）。</span><span class="sxs-lookup"><span data-stu-id="436ca-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="436ca-137">如果 [簡維軸] 設定為 [壓 *平* 合併]，腳本會自動挑選最小範圍為簡維軸的軸。</span><span class="sxs-lookup"><span data-stu-id="436ca-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="436ca-138">平滑處理</span><span class="sxs-lookup"><span data-stu-id="436ca-138">Smoothing</span></span>

<span data-ttu-id="436ca-139">平滑區段可讓您設定控制項的縮放和旋轉平滑行為。</span><span class="sxs-lookup"><span data-stu-id="436ca-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="436ca-140">視覺效果</span><span class="sxs-lookup"><span data-stu-id="436ca-140">Visuals</span></span>

<span data-ttu-id="436ca-141">您可以藉由修改其中一個對應的視覺效果設定來設定界限控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="436ca-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="436ca-142">視覺效果設定可以連結或內嵌可編寫腳本的物件，並在設定 [物件一節](#configuration-objects)中更詳細地說明。</span><span class="sxs-lookup"><span data-stu-id="436ca-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="436ca-143">設定物件</span><span class="sxs-lookup"><span data-stu-id="436ca-143">Configuration Objects</span></span>

<span data-ttu-id="436ca-144">此控制項隨附一組設定物件，可儲存為可編寫腳本的物件，並在不同的實例或 prefabs 之間共用。</span><span class="sxs-lookup"><span data-stu-id="436ca-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="436ca-145">設定可以共用和連結為個別可編寫腳本的資產檔案，或是 prefabs 內的可嵌套可編寫腳本的資產。</span><span class="sxs-lookup"><span data-stu-id="436ca-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="436ca-146">您也可以直接在實例上定義進一步的設定，而不需要連結至外部或嵌套可編寫腳本的資產。</span><span class="sxs-lookup"><span data-stu-id="436ca-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="436ca-147">界限控制偵測器會藉由在屬性偵測器中顯示訊息，來指出是否要將設定共用或內嵌為目前實例的一部分。</span><span class="sxs-lookup"><span data-stu-id="436ca-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="436ca-148">此外，在界限控制項屬性視窗本身也無法直接編輯共用的實例，而是必須直接修改其連結的資產，以避免任何意外變更共用設定。</span><span class="sxs-lookup"><span data-stu-id="436ca-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="436ca-149">目前的界限控制項提供下列功能的設定物件選項：</span><span class="sxs-lookup"><span data-stu-id="436ca-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="436ca-150">處理</span><span class="sxs-lookup"><span data-stu-id="436ca-150">Handles</span></span>
  * [<span data-ttu-id="436ca-151">縮放控點</span><span class="sxs-lookup"><span data-stu-id="436ca-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="436ca-152">旋轉控點</span><span class="sxs-lookup"><span data-stu-id="436ca-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="436ca-153">轉譯控制碼</span><span class="sxs-lookup"><span data-stu-id="436ca-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="436ca-154">連結/線框</span><span class="sxs-lookup"><span data-stu-id="436ca-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="436ca-155">Box 顯示</span><span class="sxs-lookup"><span data-stu-id="436ca-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="436ca-156">相近效果</span><span class="sxs-lookup"><span data-stu-id="436ca-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="436ca-157">Box 設定</span><span class="sxs-lookup"><span data-stu-id="436ca-157">Box configuration</span></span>

<span data-ttu-id="436ca-158">Box 設定會負責呈現一個具有透過碰撞器大小和方塊填補定義之界限的實心方塊。</span><span class="sxs-lookup"><span data-stu-id="436ca-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="436ca-159">您可以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="436ca-159">The following properties can be set up:</span></span>

* <span data-ttu-id="436ca-160">**盒材質**：定義未進行互動時，套用至轉譯方塊的材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="436ca-161">只有在設定此材質時，才會轉譯 box。</span><span class="sxs-lookup"><span data-stu-id="436ca-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="436ca-162">方塊 **抓取材質**：當使用者透過接近或遠的互動抓取來與控制項互動時，適用于 box 的材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="436ca-163">簡維 **軸顯示比例**：如果其中一個軸是簡維的，[則會套用](#flatten-axis)至方塊顯示的尺規。</span><span class="sxs-lookup"><span data-stu-id="436ca-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="436ca-164">調整控點設定</span><span class="sxs-lookup"><span data-stu-id="436ca-164">Scale handles configuration</span></span>

<span data-ttu-id="436ca-165">此屬性隱藏式選單可讓您修改界限控制項縮放控點的行為和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="436ca-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="436ca-166">**處理材質**：套用至控制碼的材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="436ca-167">**處理抓取的材質**：套用至抓取控制碼的材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="436ca-168">**處理預製專案**：調整控點的選擇性預製專案。</span><span class="sxs-lookup"><span data-stu-id="436ca-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="436ca-169">如果未設定 MRTK，則會使用 cube 作為預設值。</span><span class="sxs-lookup"><span data-stu-id="436ca-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="436ca-170">**控制碼大小**：縮放控點的大小。</span><span class="sxs-lookup"><span data-stu-id="436ca-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="436ca-171">**碰撞填補**：要加入至控制碼碰撞的填補。</span><span class="sxs-lookup"><span data-stu-id="436ca-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="436ca-172">**操作時繪製 tether**：當作用中時，會從互動起點到目前的手或指標位置繪製 tether 線。</span><span class="sxs-lookup"><span data-stu-id="436ca-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="436ca-173">**處理忽略碰撞碰撞**：如果在此連結碰撞，則控制碼會忽略與此碰撞碰撞的任何衝突。</span><span class="sxs-lookup"><span data-stu-id="436ca-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="436ca-174">**處理預製專案** 控制項時，用於控點的預製專案。</span><span class="sxs-lookup"><span data-stu-id="436ca-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="436ca-175">**顯示縮放控點**：控制控制碼的可見度。</span><span class="sxs-lookup"><span data-stu-id="436ca-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="436ca-176">**調整行為**：可以設定為統一或非統一規模調整。</span><span class="sxs-lookup"><span data-stu-id="436ca-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="436ca-177">旋轉控點設定</span><span class="sxs-lookup"><span data-stu-id="436ca-177">Rotation handles configuration</span></span>

<span data-ttu-id="436ca-178">此設定會定義旋轉控點的行為。</span><span class="sxs-lookup"><span data-stu-id="436ca-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="436ca-179">**處理材質**：套用至控制碼的材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="436ca-180">**處理抓取的材質**：套用至抓取控制碼的材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="436ca-181">**處理預製專案**：控制碼的選擇性預製專案。</span><span class="sxs-lookup"><span data-stu-id="436ca-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="436ca-182">如果未設定 MRTK，則會使用球體作為預設值。</span><span class="sxs-lookup"><span data-stu-id="436ca-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="436ca-183">**控制碼大小**：控制碼的大小。</span><span class="sxs-lookup"><span data-stu-id="436ca-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="436ca-184">**碰撞填補**：要加入至控制碼碰撞的填補。</span><span class="sxs-lookup"><span data-stu-id="436ca-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="436ca-185">**操作時繪製 tether**：當作用中時，會從互動起點到目前的手或指標位置繪製 tether 線。</span><span class="sxs-lookup"><span data-stu-id="436ca-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="436ca-186">**處理忽略碰撞碰撞**：如果在此連結碰撞，則控制碼會忽略與此碰撞碰撞的任何衝突。</span><span class="sxs-lookup"><span data-stu-id="436ca-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="436ca-187">**處理預製專案碰撞類型**：要與建立的控制碼搭配使用的碰撞型別。</span><span class="sxs-lookup"><span data-stu-id="436ca-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="436ca-188">顯示 X 軸之控制碼之 **x 的控點**：控制項的可見度。</span><span class="sxs-lookup"><span data-stu-id="436ca-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="436ca-189">**顯示 y 的控制碼**： y 軸的控制碼可見度控制項。</span><span class="sxs-lookup"><span data-stu-id="436ca-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="436ca-190">顯示 Z 軸控點之 Z 軸的 **控點**：控制項的可見度。</span><span class="sxs-lookup"><span data-stu-id="436ca-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="436ca-191">轉譯控點設定</span><span class="sxs-lookup"><span data-stu-id="436ca-191">Translation handles configuration</span></span>

<span data-ttu-id="436ca-192">允許啟用和設定界限控制項的轉譯控點。</span><span class="sxs-lookup"><span data-stu-id="436ca-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="436ca-193">請注意，每個預設都會停用轉譯控制碼。</span><span class="sxs-lookup"><span data-stu-id="436ca-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="436ca-194">**處理材質**：套用至控制碼的材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="436ca-195">**處理抓取的材質**：套用至抓取控制碼的材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="436ca-196">**處理預製專案**：控制碼的選擇性預製專案。</span><span class="sxs-lookup"><span data-stu-id="436ca-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="436ca-197">如果未設定 MRTK，則會使用球體作為預設值。</span><span class="sxs-lookup"><span data-stu-id="436ca-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="436ca-198">**控制碼大小**：控制碼的大小。</span><span class="sxs-lookup"><span data-stu-id="436ca-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="436ca-199">**碰撞填補**：要加入至控制碼碰撞的填補。</span><span class="sxs-lookup"><span data-stu-id="436ca-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="436ca-200">**操作時繪製 tether**：當作用中時，會從互動起點到目前的手或指標位置繪製 tether 線。</span><span class="sxs-lookup"><span data-stu-id="436ca-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="436ca-201">**處理忽略碰撞碰撞**：如果在此連結碰撞，則控制碼會忽略與此碰撞碰撞的任何衝突。</span><span class="sxs-lookup"><span data-stu-id="436ca-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="436ca-202">**處理預製專案碰撞類型**：要與建立的控制碼搭配使用的碰撞型別。</span><span class="sxs-lookup"><span data-stu-id="436ca-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="436ca-203">顯示 X 軸之控制碼之 **x 的控點**：控制項的可見度。</span><span class="sxs-lookup"><span data-stu-id="436ca-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="436ca-204">**顯示 y 的控制碼**： y 軸的控制碼可見度控制項。</span><span class="sxs-lookup"><span data-stu-id="436ca-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="436ca-205">顯示 Z 軸控點之 Z 軸的 **控點**：控制項的可見度。</span><span class="sxs-lookup"><span data-stu-id="436ca-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="436ca-206">連結設定 (線框) </span><span class="sxs-lookup"><span data-stu-id="436ca-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="436ca-207">連結設定會啟用界限控制項的線框功能。</span><span class="sxs-lookup"><span data-stu-id="436ca-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="436ca-208">您可以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="436ca-208">The following properties can be configured:</span></span>

* <span data-ttu-id="436ca-209">**線框材質**：適用于線框網格的材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="436ca-210">**線框 edge 半徑**：線框的粗細。</span><span class="sxs-lookup"><span data-stu-id="436ca-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="436ca-211">框線 **圖形**：框線的形狀可以是三次或圓柱。</span><span class="sxs-lookup"><span data-stu-id="436ca-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="436ca-212">**顯示** 框線：控制項線框的可見度。</span><span class="sxs-lookup"><span data-stu-id="436ca-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="436ca-213">鄰近效果設定</span><span class="sxs-lookup"><span data-stu-id="436ca-213">Proximity effect configuration</span></span>

<span data-ttu-id="436ca-214">以實際的距離來顯示及隱藏有動畫的控點。</span><span class="sxs-lookup"><span data-stu-id="436ca-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="436ca-215">它有兩個步驟的調整動畫。</span><span class="sxs-lookup"><span data-stu-id="436ca-215">It has two-step scaling animation.</span></span> <span data-ttu-id="436ca-216">預設值會設定為 HoloLens 2 樣式的行為。</span><span class="sxs-lookup"><span data-stu-id="436ca-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds Control Proximity" alt="Bounds Control Proximity">

* <span data-ttu-id="436ca-217">**作用中的相近效果**：啟用以鄰近性為基礎的控制碼啟用</span><span class="sxs-lookup"><span data-stu-id="436ca-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="436ca-218">**物件中近** 距離：第1個步驟調整的距離</span><span class="sxs-lookup"><span data-stu-id="436ca-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="436ca-219">**物件近** 距離：第2個步驟調整的距離</span><span class="sxs-lookup"><span data-stu-id="436ca-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="436ca-220">最大 **規模**：當手超出界限控制互動的範圍時，即為「處理中度相近」所定義之界限控制互動 (距離的預設縮放值。</span><span class="sxs-lookup"><span data-stu-id="436ca-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="436ca-221">使用0可依預設隱藏控制碼) </span><span class="sxs-lookup"><span data-stu-id="436ca-221">Use 0 to hide handle by default)</span></span>

* <span data-ttu-id="436ca-222">**中位數**：當手落在範圍內的界限控制互動範圍內時，縮放比例值會以「處理接近相近」 (距離定義。</span><span class="sxs-lookup"><span data-stu-id="436ca-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="436ca-223">使用1來顯示一般大小) </span><span class="sxs-lookup"><span data-stu-id="436ca-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="436ca-224">**接近比例**：當手置於抓取互動範圍內時，在「處理接近相近」所定義的抓取互動 (距離範圍內的縮放比例值。</span><span class="sxs-lookup"><span data-stu-id="436ca-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="436ca-225">使用1.x 顯示較大的大小) </span><span class="sxs-lookup"><span data-stu-id="436ca-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="436ca-226">**目前的成長率**：當手移至最接近的範圍時，對鄰近比例的物件縮放比例。</span><span class="sxs-lookup"><span data-stu-id="436ca-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="436ca-227">**中度成長率**：當手從中移至接近鄰近時，為鄰近比例的物件縮放比例。</span><span class="sxs-lookup"><span data-stu-id="436ca-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="436ca-228">**關閉成長率**：當手移離接近物件中心時，對鄰近比例的物件縮放比例。</span><span class="sxs-lookup"><span data-stu-id="436ca-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="436ca-229">條件約束系統</span><span class="sxs-lookup"><span data-stu-id="436ca-229">Constraint System</span></span>

<span data-ttu-id="436ca-230">界限控制項支援在使用界限控制控點時，使用 [條件約束管理員](ConstraintManager.md) 來限制或修改平移、旋轉或縮放行為。</span><span class="sxs-lookup"><span data-stu-id="436ca-230">Bounds control supports using the [constraint manager](ConstraintManager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="436ca-231">屬性偵測器會在下拉式清單中顯示所有附加至相同遊戲物件的可用條件約束管理員，其中有一個選項可以用來滾動並反白顯示選取的條件約束管理員。</span><span class="sxs-lookup"><span data-stu-id="436ca-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds Control Constraints">

## <a name="events"></a><span data-ttu-id="436ca-232">事件</span><span class="sxs-lookup"><span data-stu-id="436ca-232">Events</span></span>

<span data-ttu-id="436ca-233">界限控制項提供下列事件。</span><span class="sxs-lookup"><span data-stu-id="436ca-233">Bounds control provides the following events.</span></span> <span data-ttu-id="436ca-234">此範例會使用這些事件來播放音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="436ca-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="436ca-235">**輪替開始**：當旋轉開始時引發。</span><span class="sxs-lookup"><span data-stu-id="436ca-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="436ca-236">**旋轉已停止**：當旋轉停止時引發。</span><span class="sxs-lookup"><span data-stu-id="436ca-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="436ca-237">**調整已開始**：調整開始時引發。</span><span class="sxs-lookup"><span data-stu-id="436ca-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="436ca-238">**調整已停止**：當調整停止時引發。</span><span class="sxs-lookup"><span data-stu-id="436ca-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="436ca-239">**轉譯開始**：轉譯開始時引發。</span><span class="sxs-lookup"><span data-stu-id="436ca-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="436ca-240">**轉譯已停止**：當轉譯停止時引發。</span><span class="sxs-lookup"><span data-stu-id="436ca-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds Control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="436ca-241">彈性 (實驗性) </span><span class="sxs-lookup"><span data-stu-id="436ca-241">Elastics (Experimental)</span></span>

<span data-ttu-id="436ca-242">彈性可在透過界限控制項操作物件時使用。</span><span class="sxs-lookup"><span data-stu-id="436ca-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="436ca-243">請注意， [彈性系統](../Elastics/ElasticSystem.md) 仍處於實驗性狀態。</span><span class="sxs-lookup"><span data-stu-id="436ca-243">Note that the [elastics system](../Elastics/ElasticSystem.md) is still in experimental state.</span></span> <span data-ttu-id="436ca-244">若要啟用彈性，請連結現有的彈性 manager 元件，或透過按鈕建立並連結新的彈性管理員 `Add Elastics Manager` 。</span><span class="sxs-lookup"><span data-stu-id="436ca-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="436ca-245">處理樣式</span><span class="sxs-lookup"><span data-stu-id="436ca-245">Handle styles</span></span>

<span data-ttu-id="436ca-246">依預設，當您只指派 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 腳本時，它會顯示 HoloLens 1 代樣式的控制碼。</span><span class="sxs-lookup"><span data-stu-id="436ca-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="436ca-247">若要使用 HoloLens 2 樣式控制碼，您需要指派適當的控制碼 prefabs 和材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![界限控制項 Handdle Styles1](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="436ca-249">以下是 HoloLens 2 樣式界限控制項控點的 prefabs、材質和縮放值。</span><span class="sxs-lookup"><span data-stu-id="436ca-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="436ca-250">您可以在場景中找到這個範例 `BoundsControlExamples` 。</span><span class="sxs-lookup"><span data-stu-id="436ca-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds Control HandleStyles ">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="436ca-251">處理 HoloLens 2 樣式的 (設定) </span><span class="sxs-lookup"><span data-stu-id="436ca-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="436ca-252">**處理材質**： BoundingBoxHandleWhite</span><span class="sxs-lookup"><span data-stu-id="436ca-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="436ca-253">**處理抓取材質**： BoundingBoxHandleBlueGrabbed</span><span class="sxs-lookup"><span data-stu-id="436ca-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="436ca-254">**調整控點預製專案**： MRTK_BoundingBox_ScaleHandle. 預製專案</span><span class="sxs-lookup"><span data-stu-id="436ca-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="436ca-255">**縮放控點的預製專案**： MRTK_BoundingBox_ScaleHandle_Slate. 預製專案</span><span class="sxs-lookup"><span data-stu-id="436ca-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="436ca-256">**調整控點大小**： 0.016 (1.6 cm) </span><span class="sxs-lookup"><span data-stu-id="436ca-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="436ca-257">**縮放控點碰撞填補**： 0.016 (使 grabbable 的碰撞數稍微大於處理視覺效果) </span><span class="sxs-lookup"><span data-stu-id="436ca-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="436ca-258">**旋轉控點預製專案**： MRTK_BoundingBox_RotateHandle. 預製專案</span><span class="sxs-lookup"><span data-stu-id="436ca-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="436ca-259">**旋轉控點大小**：0.016</span><span class="sxs-lookup"><span data-stu-id="436ca-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="436ca-260">**旋轉柄碰撞碼填補**： 0.016 (使 grabbable 碰撞稍微大於處理視覺效果) </span><span class="sxs-lookup"><span data-stu-id="436ca-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="436ca-261">使用物件操作工具進行轉換變更</span><span class="sxs-lookup"><span data-stu-id="436ca-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="436ca-262">界限控制項可以搭配使用 [`ObjectManipulator.cs`](ObjectManipulator.md) ，以允許特定類型的操作 (例如</span><span class="sxs-lookup"><span data-stu-id="436ca-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](ObjectManipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="436ca-263">在不使用控制碼的情況下移動物件) 。</span><span class="sxs-lookup"><span data-stu-id="436ca-263">moving the object) without using handles.</span></span> <span data-ttu-id="436ca-264">操作處理常式同時支援一個和兩個的互動。</span><span class="sxs-lookup"><span data-stu-id="436ca-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="436ca-265">[手動追蹤](../input/HandTracking.md) 可用來將物件與關閉的物件互動。</span><span class="sxs-lookup"><span data-stu-id="436ca-265">[Hand tracking](../input/HandTracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds Control Object Manipulator">

<span data-ttu-id="436ca-266">為了讓界限控制邊緣在使用遠的互動進行移動時以相同的方式運作，建議您 [`ObjectManipulator`](ObjectManipulator.md) 連接其事件，以 *在*  /  *操作結束* 時開始操作 `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` ，如上面的螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="436ca-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](ObjectManipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="436ca-267">如何使用 Unity 偵測器新增和設定界限控制項</span><span class="sxs-lookup"><span data-stu-id="436ca-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="436ca-268">將 Box 碰撞新增至物件</span><span class="sxs-lookup"><span data-stu-id="436ca-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="436ca-269">將 `BoundsControl` 腳本指派給物件</span><span class="sxs-lookup"><span data-stu-id="436ca-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="436ca-270">設定選項，例如「啟動」方法 (請參閱下面的偵測 [器屬性](#inspector-properties) 一節) </span><span class="sxs-lookup"><span data-stu-id="436ca-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="436ca-271"> (選擇性) 指派 HoloLens 2 樣式界限控制項的 prefabs 和材質 (請參閱下方的 [控制碼樣式](#handle-styles) 一節) </span><span class="sxs-lookup"><span data-stu-id="436ca-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="436ca-272">使用偵測器中的 [ *目標物件* 和 *界限覆寫* ] 欄位，即可指派具有多個子元件之物件中的特定物件和碰撞器。</span><span class="sxs-lookup"><span data-stu-id="436ca-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![界限控制項指派影像](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="436ca-274">如何在程式碼中新增和設定界限控制項</span><span class="sxs-lookup"><span data-stu-id="436ca-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="436ca-275">具現化 cube GameObject</span><span class="sxs-lookup"><span data-stu-id="436ca-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="436ca-276">`BoundsControl`使用 AddComponent<> () ，將腳本指派給具有碰撞的物件</span><span class="sxs-lookup"><span data-stu-id="436ca-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="436ca-277">您可以直接在控制項上或透過其中一個可編寫腳本的設定來設定選項 (請參閱下面的偵測[器屬性](#inspector-properties)和設定[一節) ](#configuration-objects)</span><span class="sxs-lookup"><span data-stu-id="436ca-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="436ca-278"> (選擇性) 指派 HoloLens 2 樣式界限控制項的 prefabs 和材質。</span><span class="sxs-lookup"><span data-stu-id="436ca-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="436ca-279">這仍然需要透過偵測器進行指派，因為材質和 prefabs 應該以動態方式載入。</span><span class="sxs-lookup"><span data-stu-id="436ca-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="436ca-280">使用 Unity 的 ' Resources ' 資料夾或 [著色器。]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 因為在執行時間可能遺失著色器排列，所以不建議尋找動態載入著色器。</span><span class="sxs-lookup"><span data-stu-id="436ca-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="436ca-281">範例：使用 MinMaxScaleConstraint 設定最小、最大界限控制小數位數</span><span class="sxs-lookup"><span data-stu-id="436ca-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="436ca-282">若要設定最小和最大刻度，請將加入 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 至您的控制項。</span><span class="sxs-lookup"><span data-stu-id="436ca-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="436ca-283">當界限控制項自動附加和啟用條件約束管理員時，MinMaxScaleConstraint 會在附加並設定之後，自動套用至轉換變更。</span><span class="sxs-lookup"><span data-stu-id="436ca-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="436ca-284">您也可以使用 MinMaxScaleConstraint 來設定的最小和最大刻度 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 。</span><span class="sxs-lookup"><span data-stu-id="436ca-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="436ca-285">範例：在遊戲物件周圍新增界限控制項</span><span class="sxs-lookup"><span data-stu-id="436ca-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="436ca-286">若要在物件周圍加入界限控制項，只要在 `BoundsControl` 其中加入元件即可：</span><span class="sxs-lookup"><span data-stu-id="436ca-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="436ca-287">從周框方塊進行遷移</span><span class="sxs-lookup"><span data-stu-id="436ca-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="436ca-288">使用周 [框](BoundingBox.md) 方塊的現有 prefabs 和實例，可以透過 [ [遷移] 視窗](../tools/MigrationWindow.md) （屬於 MRTK 工具套件的一部分）升級為新的界限控制項。</span><span class="sxs-lookup"><span data-stu-id="436ca-288">Existing prefabs and instances using [bounding box](BoundingBox.md) can be upgraded to the new bounds control via the [migration window](../tools/MigrationWindow.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="436ca-289">針對升級個別周框方塊的實例，元件的屬性偵測器內也有一個遷移選項。</span><span class="sxs-lookup"><span data-stu-id="436ca-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">

## <a name="see-also"></a><span data-ttu-id="436ca-290">另請參閱</span><span class="sxs-lookup"><span data-stu-id="436ca-290">See also</span></span>

* [<span data-ttu-id="436ca-291">物件操作工具</span><span class="sxs-lookup"><span data-stu-id="436ca-291">Object manipulator</span></span>](ObjectManipulator.md)
* [<span data-ttu-id="436ca-292">條件約束管理員</span><span class="sxs-lookup"><span data-stu-id="436ca-292">Constraint manager</span></span>](ConstraintManager.md)
* [<span data-ttu-id="436ca-293">遷移視窗</span><span class="sxs-lookup"><span data-stu-id="436ca-293">Migration window</span></span>](../tools/MigrationWindow.md)
* [<span data-ttu-id="436ca-294">彈性系統 (實驗性) </span><span class="sxs-lookup"><span data-stu-id="436ca-294">Elastics system (Experimental)</span></span>](../elastics/ElasticSystem.md)