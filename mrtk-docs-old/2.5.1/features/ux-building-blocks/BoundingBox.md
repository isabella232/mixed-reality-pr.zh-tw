---
title: BoundingBox
description: MRTK 中的周框方塊總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、周框方塊
ms.openlocfilehash: a278679cfddfbd68e6d29f4b0dbeb88e3344e7b7
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781175"
---
# <a name="bounding-box"></a><span data-ttu-id="4afe8-104">週框方塊</span><span class="sxs-lookup"><span data-stu-id="4afe8-104">Bounding box</span></span>

![週框方塊](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="4afe8-106">周框方塊已被取代，並由其後續 [界限控制項](BoundsControl.md)取代。</span><span class="sxs-lookup"><span data-stu-id="4afe8-106">Bounding box is deprecated and replaced by its successor [bounds control](BoundsControl.md).</span></span> <span data-ttu-id="4afe8-107">使用 [其中一個遷移選項](#migrating-to-bounds-control) 升級現有的遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="4afe8-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="4afe8-108">[`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox)腳本提供在混合現實中轉換物件的基本功能。</span><span class="sxs-lookup"><span data-stu-id="4afe8-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="4afe8-109">周框方塊會顯示全像影像周圍的立方體，表示它可以與互動。</span><span class="sxs-lookup"><span data-stu-id="4afe8-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="4afe8-110">Cube 角落和邊緣上的控點可讓您縮放或旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="4afe8-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="4afe8-111">周框方塊也會對使用者輸入做出回應。</span><span class="sxs-lookup"><span data-stu-id="4afe8-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="4afe8-112">例如，在 HoloLens 2 上，周框方塊會回應手指附近，提供視覺回饋以協助觀察物件的距離。</span><span class="sxs-lookup"><span data-stu-id="4afe8-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="4afe8-113">您可以輕鬆地自訂所有互動和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="4afe8-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="4afe8-114">如需詳細資訊，請參閱 Windows 開發人員中心內的周 [框方塊和應用程式行](https://docs.microsoft.com/windows/mixed-reality/app-bar-and-bounding-box) 。</span><span class="sxs-lookup"><span data-stu-id="4afe8-114">For more information, see [Bounding box and App bar](https://docs.microsoft.com/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="4afe8-115">範例場景</span><span class="sxs-lookup"><span data-stu-id="4afe8-115">Example scene</span></span>

<span data-ttu-id="4afe8-116">您可以在場景中找到周框方塊設定的範例 `BoundingBoxExamples` 。</span><span class="sxs-lookup"><span data-stu-id="4afe8-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box example scene">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="4afe8-117">如何使用 Unity 偵測器新增和設定周框方塊</span><span class="sxs-lookup"><span data-stu-id="4afe8-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="4afe8-118">將 Box 碰撞新增至物件</span><span class="sxs-lookup"><span data-stu-id="4afe8-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="4afe8-119">將 `BoundingBox` 腳本指派給物件</span><span class="sxs-lookup"><span data-stu-id="4afe8-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="4afe8-120">設定選項，例如「啟動」方法 (請參閱下面的偵測 [器屬性](#inspector-properties) 一節) </span><span class="sxs-lookup"><span data-stu-id="4afe8-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="4afe8-121"> (選擇性) 指派 HoloLens 2 樣式周框方塊的 prefabs 和材質 (請參閱下方的 [控制碼樣式](#handle-styles) 區段) </span><span class="sxs-lookup"><span data-stu-id="4afe8-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="4afe8-122">使用偵測器中的 [ *目標物件* 和 *界限覆寫* ] 欄位，即可指派具有多個子元件之物件中的特定物件和碰撞器。</span><span class="sxs-lookup"><span data-stu-id="4afe8-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![周框方塊指派](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="4afe8-124">如何在程式碼中新增和設定周框方塊</span><span class="sxs-lookup"><span data-stu-id="4afe8-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="4afe8-125">具現化 cube GameObject</span><span class="sxs-lookup"><span data-stu-id="4afe8-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="4afe8-126">`BoundingBox`使用 AddComponent<> () ，將腳本指派給具有碰撞的物件</span><span class="sxs-lookup"><span data-stu-id="4afe8-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="4afe8-127">設定選項 (請參閱下方的偵測 [器屬性](#inspector-properties) 區段) </span><span class="sxs-lookup"><span data-stu-id="4afe8-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="4afe8-128"> (選擇性) 指派 HoloLens 2 樣式周框方塊的 prefabs 和材質。</span><span class="sxs-lookup"><span data-stu-id="4afe8-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="4afe8-129">這仍然需要透過偵測器進行指派，因為材質和 prefabs 應該以動態方式載入。</span><span class="sxs-lookup"><span data-stu-id="4afe8-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="4afe8-130">使用 Unity 的 ' Resources ' 資料夾或 [著色器。]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 因為在執行時間可能遺失著色器排列，所以不建議尋找動態載入著色器。</span><span class="sxs-lookup"><span data-stu-id="4afe8-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="4afe8-131">範例：使用 MinMaxScaleConstraint 設定最小、最大周框方塊縮放比例</span><span class="sxs-lookup"><span data-stu-id="4afe8-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="4afe8-132">若要設定最小和最大刻度，請使用 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 。</span><span class="sxs-lookup"><span data-stu-id="4afe8-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="4afe8-133">您也可以使用 MinMaxScaleConstraint 來設定的最小和最大刻度 [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。</span><span class="sxs-lookup"><span data-stu-id="4afe8-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="4afe8-134">範例：在遊戲物件周圍新增周框方塊</span><span class="sxs-lookup"><span data-stu-id="4afe8-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="4afe8-135">若要在物件周圍加入周框方塊，只要在 `BoundingBox` 其中加入一個元件即可：</span><span class="sxs-lookup"><span data-stu-id="4afe8-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="4afe8-136">偵測器屬性</span><span class="sxs-lookup"><span data-stu-id="4afe8-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="4afe8-137">目標物件</span><span class="sxs-lookup"><span data-stu-id="4afe8-137">Target object</span></span>

<span data-ttu-id="4afe8-138">這個屬性會指定周框方塊操作將轉換的物件。</span><span class="sxs-lookup"><span data-stu-id="4afe8-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="4afe8-139">如果未設定物件，周框方塊會預設為擁有者物件。</span><span class="sxs-lookup"><span data-stu-id="4afe8-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="4afe8-140">界限覆寫</span><span class="sxs-lookup"><span data-stu-id="4afe8-140">Bounds override</span></span>

<span data-ttu-id="4afe8-141">從物件設定界限計算的方塊碰撞。</span><span class="sxs-lookup"><span data-stu-id="4afe8-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="4afe8-142">啟用行為</span><span class="sxs-lookup"><span data-stu-id="4afe8-142">Activation behavior</span></span>

<span data-ttu-id="4afe8-143">有幾個選項可啟用周框方塊介面。</span><span class="sxs-lookup"><span data-stu-id="4afe8-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="4afe8-144">*啟動時啟用*：啟動場景之後，會顯示周框方塊。</span><span class="sxs-lookup"><span data-stu-id="4afe8-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="4afe8-145">*依鄰近性啟動*：當有向物件接近的手中，周框方塊會變成可見。</span><span class="sxs-lookup"><span data-stu-id="4afe8-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="4afe8-146">[*依指標啟動*]：當其以手型指標為目標時，會顯示周框方塊。</span><span class="sxs-lookup"><span data-stu-id="4afe8-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="4afe8-147">*手動啟用*：周框方塊不會自動顯示。</span><span class="sxs-lookup"><span data-stu-id="4afe8-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="4afe8-148">您可以藉由存取 boundingBox 屬性，以手動方式透過腳本來啟用它。</span><span class="sxs-lookup"><span data-stu-id="4afe8-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="4afe8-149">最小規模</span><span class="sxs-lookup"><span data-stu-id="4afe8-149">Scale minimum</span></span>

<span data-ttu-id="4afe8-150">允許的最小比例。</span><span class="sxs-lookup"><span data-stu-id="4afe8-150">The minimum allowed scale.</span></span> <span data-ttu-id="4afe8-151">這個屬性已被取代，最好是加入 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 腳本。</span><span class="sxs-lookup"><span data-stu-id="4afe8-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="4afe8-152">如果加入此腳本，將會從它的最小縮放比例取得，而不是從周框方塊中取得。</span><span class="sxs-lookup"><span data-stu-id="4afe8-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="4afe8-153">調整最大值</span><span class="sxs-lookup"><span data-stu-id="4afe8-153">Scale maximum</span></span>

<span data-ttu-id="4afe8-154">允許的最大刻度。</span><span class="sxs-lookup"><span data-stu-id="4afe8-154">The maximum allowed scale.</span></span> <span data-ttu-id="4afe8-155">這個屬性已被取代，最好是加入 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 腳本。</span><span class="sxs-lookup"><span data-stu-id="4afe8-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="4afe8-156">如果加入此腳本，將會從該腳本中取得最大刻度，而不是從周框方塊中取得。</span><span class="sxs-lookup"><span data-stu-id="4afe8-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="4afe8-157">Box 顯示</span><span class="sxs-lookup"><span data-stu-id="4afe8-157">Box display</span></span>

<span data-ttu-id="4afe8-158">不同的周框方塊視覺效果選項。</span><span class="sxs-lookup"><span data-stu-id="4afe8-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="4afe8-159">如果將 [簡維軸] 設定為 [ *自動* 簡維]，腳本將不允許在最小範圍內沿著軸操作。</span><span class="sxs-lookup"><span data-stu-id="4afe8-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="4afe8-160">這會產生2D 周框方塊，通常用於精簡型物件。</span><span class="sxs-lookup"><span data-stu-id="4afe8-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="4afe8-161">處理</span><span class="sxs-lookup"><span data-stu-id="4afe8-161">Handles</span></span>

<span data-ttu-id="4afe8-162">您可以指派材質和預製專案來覆寫控點樣式。</span><span class="sxs-lookup"><span data-stu-id="4afe8-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="4afe8-163">如果未指派控制碼，則會以預設樣式顯示。</span><span class="sxs-lookup"><span data-stu-id="4afe8-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="4afe8-164">事件</span><span class="sxs-lookup"><span data-stu-id="4afe8-164">Events</span></span>

<span data-ttu-id="4afe8-165">周框方塊提供下列事件。</span><span class="sxs-lookup"><span data-stu-id="4afe8-165">Bounding box provides the following events.</span></span> <span data-ttu-id="4afe8-166">此範例會使用這些事件來播放音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="4afe8-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="4afe8-167">**輪替開始**：當旋轉開始時引發。</span><span class="sxs-lookup"><span data-stu-id="4afe8-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="4afe8-168">**旋轉結束**：當旋轉結束時引發。</span><span class="sxs-lookup"><span data-stu-id="4afe8-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="4afe8-169">**調整已開始**：調整開始時引發。</span><span class="sxs-lookup"><span data-stu-id="4afe8-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="4afe8-170">**調整結束**：調整結束時引發。</span><span class="sxs-lookup"><span data-stu-id="4afe8-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Bounding Box Event">

## <a name="handle-styles"></a><span data-ttu-id="4afe8-171">處理樣式</span><span class="sxs-lookup"><span data-stu-id="4afe8-171">Handle styles</span></span>

<span data-ttu-id="4afe8-172">依預設，當您只指派 [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) 腳本時，它會顯示 HoloLens 1 代樣式的控制碼。</span><span class="sxs-lookup"><span data-stu-id="4afe8-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="4afe8-173">若要使用 HoloLens 2 樣式控制碼，您需要指派適當的控制碼 prefabs 和材質。</span><span class="sxs-lookup"><span data-stu-id="4afe8-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![周框方塊 HandelStyles 1](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="4afe8-175">以下是 HoloLens 2 樣式周框方塊控點的 prefabs、材質和縮放值。</span><span class="sxs-lookup"><span data-stu-id="4afe8-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="4afe8-176">您可以在場景中找到這個範例 `BoundingBoxExamples` 。</span><span class="sxs-lookup"><span data-stu-id="4afe8-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="bounding Box Handle Styles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="4afe8-177">處理 HoloLens 2 樣式的 (設定) </span><span class="sxs-lookup"><span data-stu-id="4afe8-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="4afe8-178">**處理材質**： BoundingBoxHandleWhite</span><span class="sxs-lookup"><span data-stu-id="4afe8-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="4afe8-179">**處理抓取材質**： BoundingBoxHandleBlueGrabbed</span><span class="sxs-lookup"><span data-stu-id="4afe8-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="4afe8-180">**調整控點預製專案**： MRTK_BoundingBox_ScaleHandle. 預製專案</span><span class="sxs-lookup"><span data-stu-id="4afe8-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="4afe8-181">**縮放控點的預製專案**： MRTK_BoundingBox_ScaleHandle_Slate. 預製專案</span><span class="sxs-lookup"><span data-stu-id="4afe8-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="4afe8-182">**調整控點大小**： 0.016 (1.6 cm) </span><span class="sxs-lookup"><span data-stu-id="4afe8-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="4afe8-183">**縮放控點碰撞填補**： 0.016 (使 grabbable 的碰撞數稍微大於處理視覺效果) </span><span class="sxs-lookup"><span data-stu-id="4afe8-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="4afe8-184">**旋轉控點預製專案**： MRTK_BoundingBox_RotateHandle. 預製專案</span><span class="sxs-lookup"><span data-stu-id="4afe8-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="4afe8-185">**旋轉控點大小**：0.016</span><span class="sxs-lookup"><span data-stu-id="4afe8-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="4afe8-186">**旋轉柄碰撞碼填補**： 0.016 (使 grabbable 碰撞稍微大於處理視覺效果) </span><span class="sxs-lookup"><span data-stu-id="4afe8-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="4afe8-187">HoloLens 2 樣式) 的鄰近 (設定</span><span class="sxs-lookup"><span data-stu-id="4afe8-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="4afe8-188">以實際的距離來顯示及隱藏有動畫的控點。</span><span class="sxs-lookup"><span data-stu-id="4afe8-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="4afe8-189">它有兩個步驟的調整動畫。</span><span class="sxs-lookup"><span data-stu-id="4afe8-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Bounding box proximity">

* <span data-ttu-id="4afe8-190">**作用中的相近效果**：啟用以鄰近性為基礎的控制碼啟用</span><span class="sxs-lookup"><span data-stu-id="4afe8-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="4afe8-191">**處理中等** 距離：第1個步驟調整的距離</span><span class="sxs-lookup"><span data-stu-id="4afe8-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="4afe8-192">**處理近** 距離：第2個步驟調整的距離</span><span class="sxs-lookup"><span data-stu-id="4afe8-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="4afe8-193">最大 **規模**：當手不在周框方塊互動的範圍內時，即為控制碼資產的預設縮放值， (距離以「處理中度相近」定義。</span><span class="sxs-lookup"><span data-stu-id="4afe8-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="4afe8-194">使用0可依預設隱藏控制碼) </span><span class="sxs-lookup"><span data-stu-id="4afe8-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="4afe8-195">**中度調整**：當手在周框方塊互動範圍內時，縮放比例值會在「處理接近相近」的上方定義 (距離。</span><span class="sxs-lookup"><span data-stu-id="4afe8-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="4afe8-196">使用1來顯示一般大小) </span><span class="sxs-lookup"><span data-stu-id="4afe8-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="4afe8-197">**接近比例**：當手置於抓取互動範圍內時，在「處理接近相近」所定義的抓取互動 (距離範圍內的縮放比例值。</span><span class="sxs-lookup"><span data-stu-id="4afe8-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="4afe8-198">使用1.x 顯示較大的大小) </span><span class="sxs-lookup"><span data-stu-id="4afe8-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="4afe8-199">使用操作處理常式使物件可移動</span><span class="sxs-lookup"><span data-stu-id="4afe8-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="4afe8-200">您可以使用周框方塊來結合， [`ManipulationHandler.cs`](ManipulationHandler.md) 讓物件使用遠的互動來可移動。</span><span class="sxs-lookup"><span data-stu-id="4afe8-200">A bounding box can be combined with [`ManipulationHandler.cs`](ManipulationHandler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="4afe8-201">操作處理常式同時支援一個和兩個的互動。</span><span class="sxs-lookup"><span data-stu-id="4afe8-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="4afe8-202">[手動追蹤](../input/HandTracking.md) 可用來將物件與關閉的物件互動。</span><span class="sxs-lookup"><span data-stu-id="4afe8-202">[Hand tracking](../input/HandTracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manpulation handler">

<span data-ttu-id="4afe8-203">為了讓周框方塊邊緣在使用遠的互動進行移動時，會以相同的方式運作，建議您 [`ManipulationHandler`](ManipulationHandler.md) 連接其事件，以 *在*  /  *操作結束* 時開始操作 `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` ，如上面的螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="4afe8-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](ManipulationHandler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="4afe8-204">遷移至界限控制項</span><span class="sxs-lookup"><span data-stu-id="4afe8-204">Migrating to bounds control</span></span>

<span data-ttu-id="4afe8-205">使用周 [框](BoundingBox.md) 方塊的現有 prefabs 和實例，可以透過 [ [遷移] 視窗](../tools/MigrationWindow.md) （屬於 MRTK 工具套件的一部分）升級為新的界限控制項。</span><span class="sxs-lookup"><span data-stu-id="4afe8-205">Existing prefabs and instances using [bounding box](BoundingBox.md) can be upgraded to the new bounds control via the [migration window](../tools/MigrationWindow.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="4afe8-206">針對升級個別周框方塊的實例，元件的屬性偵測器內也有一個遷移選項。</span><span class="sxs-lookup"><span data-stu-id="4afe8-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control migrate">
