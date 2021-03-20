---
title: ElasticSystem
description: MRTK 中彈性模擬的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、ElasticsSystem、
ms.openlocfilehash: 92be1cb2dfbe9ee19adacc46c09f9e7b77f7219c
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684781"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="28546-104">彈性系統 (實驗性) </span><span class="sxs-lookup"><span data-stu-id="28546-104">Elastic system (experimental)</span></span>

![彈性系統](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="28546-106">MRTK 隨附彈性的模擬系統，其中包含各種可延伸和彈性的子類別，並提供4維四元數、三維磁片區彈簧和簡單線性彈簧系統的系結。</span><span class="sxs-lookup"><span data-stu-id="28546-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="28546-107">目前支援 [彈性 manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 的下列 MRTK 元件可利用彈性功能：</span><span class="sxs-lookup"><span data-stu-id="28546-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="28546-108">界限控制項</span><span class="sxs-lookup"><span data-stu-id="28546-108">Bounds control</span></span>](../ux-building-blocks/BoundsControl.md)
- [<span data-ttu-id="28546-109">物件操作工具</span><span class="sxs-lookup"><span data-stu-id="28546-109">Object manipulator</span></span>](../ux-building-blocks/ObjectManipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="28546-110">彈性管理員</span><span class="sxs-lookup"><span data-stu-id="28546-110">Elastics manager</span></span>

![彈性 System2](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="28546-112">彈性管理員會處理傳遞的轉換，並將其饋送至彈性系統。</span><span class="sxs-lookup"><span data-stu-id="28546-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="28546-113">您可以透過兩個步驟來啟用自訂群組件的彈性：</span><span class="sxs-lookup"><span data-stu-id="28546-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="28546-114">在操作開始時呼叫 Initialize 方法，並以目前的主控制項轉換來更新系統。</span><span class="sxs-lookup"><span data-stu-id="28546-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="28546-115">只要針對更新的目標轉換執行彈性計算時，就會查詢 ApplyHostTransform。</span><span class="sxs-lookup"><span data-stu-id="28546-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="28546-116">請注意，彈性會在操作結束 (透過彈性 manager 更新迴圈) 來繼續模擬。</span><span class="sxs-lookup"><span data-stu-id="28546-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="28546-117">若要封鎖此行為，彈性自動更新 [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) 可以設定為 false。</span><span class="sxs-lookup"><span data-stu-id="28546-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="28546-118">根據預設，彈性管理員元件在新增至遊戲物件時，不會針對任何轉換類型啟用彈性。</span><span class="sxs-lookup"><span data-stu-id="28546-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="28546-119">您必須 `Manipulation types using elastic feedback` 針對特定的轉換類型啟用欄位，才能建立所選類型的彈性設定和範圍。</span><span class="sxs-lookup"><span data-stu-id="28546-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="28546-120">彈性設定</span><span class="sxs-lookup"><span data-stu-id="28546-120">Elastics configurations</span></span>

<span data-ttu-id="28546-121">彈性管理員類似于 [界限控制項](../ux-building-blocks/BoundsControl.md#configuration-objects)設定，隨附一組設定物件，可儲存為可編寫腳本的物件，並在不同的實例或 prefabs 間共用。</span><span class="sxs-lookup"><span data-stu-id="28546-121">Similar to [bounds control configurations](../ux-building-blocks/BoundsControl.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="28546-122">設定可以共用和連結為個別可編寫腳本的資產檔案，或是 prefabs 內的可嵌套可編寫腳本的資產。</span><span class="sxs-lookup"><span data-stu-id="28546-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="28546-123">您也可以直接在實例上定義進一步的設定，而不需要連結至外部或嵌套可編寫腳本的資產。</span><span class="sxs-lookup"><span data-stu-id="28546-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="28546-124">彈性 manager 偵測器會藉由在屬性偵測器中顯示訊息，來指出是否要將設定共用或內嵌為目前實例的一部分。</span><span class="sxs-lookup"><span data-stu-id="28546-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="28546-125">此外，您無法直接在 [彈性管理員] 屬性視窗中編輯共用的實例，而是改為直接修改其連結的資產，以避免任何意外變更共用設定。</span><span class="sxs-lookup"><span data-stu-id="28546-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="28546-126">彈性 manager 提供下列轉換類型的設定物件選項，每個都以 [彈性設定物件](#elastic-configuration-object)表示：</span><span class="sxs-lookup"><span data-stu-id="28546-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="28546-127">彈性翻譯</span><span class="sxs-lookup"><span data-stu-id="28546-127">Translation Elastic</span></span>
- <span data-ttu-id="28546-128">輪替彈性</span><span class="sxs-lookup"><span data-stu-id="28546-128">Rotation Elastic</span></span>
- <span data-ttu-id="28546-129">調整彈性</span><span class="sxs-lookup"><span data-stu-id="28546-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="28546-130">彈性設定物件</span><span class="sxs-lookup"><span data-stu-id="28546-130">Elastic configuration object</span></span>

<span data-ttu-id="28546-131">彈性設定會定義禁止調和 oscillator 差異系統的屬性。</span><span class="sxs-lookup"><span data-stu-id="28546-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="28546-132">下列屬性可以調整，但在 MRTK 中已有一組預設值：</span><span class="sxs-lookup"><span data-stu-id="28546-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="28546-133">**大量**：模擬 oscillator 元素的大量。</span><span class="sxs-lookup"><span data-stu-id="28546-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="28546-134">**HandK**：手上彈簧常數。</span><span class="sxs-lookup"><span data-stu-id="28546-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="28546-135">**EndK**：結束端點彈簧常數。</span><span class="sxs-lookup"><span data-stu-id="28546-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="28546-136">**SnapK**：貼齊點彈簧常數。</span><span class="sxs-lookup"><span data-stu-id="28546-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="28546-137">**拖曳**：拖曳/阻尼因素，與速度成正比。</span><span class="sxs-lookup"><span data-stu-id="28546-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="28546-138">彈性範圍</span><span class="sxs-lookup"><span data-stu-id="28546-138">Elastics extents</span></span>

<span data-ttu-id="28546-139">彈性範圍設定會依操作的類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="28546-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="28546-140">轉譯和小數位數是由 [大量彈性範圍](#volume-elastic-extent) 所表示，旋轉是以 [四元數彈性範圍](#quaternion-elastic-extent)表示。</span><span class="sxs-lookup"><span data-stu-id="28546-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="28546-141">大量彈性範圍</span><span class="sxs-lookup"><span data-stu-id="28546-141">Volume elastic extent</span></span>

<span data-ttu-id="28546-142">磁片區範圍定義了禁止調和 oscillator 可以自由移動的三個維度空間。</span><span class="sxs-lookup"><span data-stu-id="28546-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![彈性磁片區延展界限](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="28546-144">**StretchBounds**：代表彈性空間的下限。</span><span class="sxs-lookup"><span data-stu-id="28546-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="28546-145">**UseBounds**：是否應由系統遵守延展界限。</span><span class="sxs-lookup"><span data-stu-id="28546-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="28546-146">若為 true，當目標位置的目前反復專案位於延展界限之外時，將會套用 end force。</span><span class="sxs-lookup"><span data-stu-id="28546-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="28546-147">**快照點**：指向系統將貼齊的空間內部。</span><span class="sxs-lookup"><span data-stu-id="28546-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="28546-148">**RepeatSnapPoints**：將貼齊點重複到無限大。</span><span class="sxs-lookup"><span data-stu-id="28546-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="28546-149">現有的貼齊點將作為模數，其中實際的貼齊點會對應到每個貼齊點的最接近整數倍數。</span><span class="sxs-lookup"><span data-stu-id="28546-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="28546-150">**SnapRadius**：貼齊點開始強制彈簧的距離。</span><span class="sxs-lookup"><span data-stu-id="28546-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![彈性磁片區對齊格線](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="28546-152">四元數彈性範圍</span><span class="sxs-lookup"><span data-stu-id="28546-152">Quaternion elastic extent</span></span>

<span data-ttu-id="28546-153">四元數範圍定義四個維度旋轉空間，讓禁止調和 oscillator 可以自由旋轉。</span><span class="sxs-lookup"><span data-stu-id="28546-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![彈性旋轉範例](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="28546-155">**快照點**：系統將貼齊的歐拉角度。</span><span class="sxs-lookup"><span data-stu-id="28546-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="28546-156">**RepeatSnapPoints**：重複對齊點。</span><span class="sxs-lookup"><span data-stu-id="28546-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="28546-157">現有的貼齊點將作為模數，其中實際的貼齊點會對應到每個貼齊點的最接近整數倍數。</span><span class="sxs-lookup"><span data-stu-id="28546-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="28546-158">**SnapRadius**：貼齊點開始強制歐拉度的彈簧的弧形角度。</span><span class="sxs-lookup"><span data-stu-id="28546-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="28546-159">彈性範例場景</span><span class="sxs-lookup"><span data-stu-id="28546-159">Elastics example scene</span></span>

<span data-ttu-id="28546-160">您可以在場景中找到彈性設定的範例 `ElasticSystemExample` 。</span><span class="sxs-lookup"><span data-stu-id="28546-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![彈性範例場景](../images/elastics/Elastics_Example_Scene.png)
