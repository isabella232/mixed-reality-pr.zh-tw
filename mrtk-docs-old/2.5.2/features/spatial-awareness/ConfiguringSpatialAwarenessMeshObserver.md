---
title: ConfiguringSpatialAwarenessMeshObserver
description: 如何在 MRTK 中設定現成的空間網格觀察者
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: b87470f99fd7ed6d73f138ec607c1cab02170549
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780376"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="e5db2-104">設定裝置的網狀觀察器</span><span class="sxs-lookup"><span data-stu-id="e5db2-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="e5db2-105">本指南將逐步說明如何在 MRTK 中設定現成可用的空間網格觀察器，以支援 Windows Mixed Reality 平臺 (例如</span><span class="sxs-lookup"><span data-stu-id="e5db2-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="e5db2-106">HoloLens) 。</span><span class="sxs-lookup"><span data-stu-id="e5db2-106">HoloLens).</span></span> <span data-ttu-id="e5db2-107">混合現實工具組所提供的預設實作為 [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 類別。</span><span class="sxs-lookup"><span data-stu-id="e5db2-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="e5db2-108">不過，本文中的許多屬性都適用于其他 [自訂觀察](CreateDataProvider.md)者的實施。</span><span class="sxs-lookup"><span data-stu-id="e5db2-108">Many of the properties in this article though apply for other [custom Observer implementations](CreateDataProvider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="e5db2-109">設定檔設定</span><span class="sxs-lookup"><span data-stu-id="e5db2-109">Profile settings</span></span>

<span data-ttu-id="e5db2-110">針對 [空間感知系統](SpatialAwarenessGettingStarted.md)設定空間網格觀察者設定檔時，必須先定義下列兩個專案。</span><span class="sxs-lookup"><span data-stu-id="e5db2-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](SpatialAwarenessGettingStarted.md).</span></span>

1. <span data-ttu-id="e5db2-111">具體觀察者類型的實</span><span class="sxs-lookup"><span data-stu-id="e5db2-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="e5db2-112">執行此觀察者) 支援的平臺 (的清單</span><span class="sxs-lookup"><span data-stu-id="e5db2-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="e5db2-113">所有觀察者都必須延伸 [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 介面。</span><span class="sxs-lookup"><span data-stu-id="e5db2-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![網格觀察者一般設定檔設定](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="e5db2-115">一般設定</span><span class="sxs-lookup"><span data-stu-id="e5db2-115">General settings</span></span>

![網格觀察者一般設定](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="e5db2-117">**啟動行為**</span><span class="sxs-lookup"><span data-stu-id="e5db2-117">**Startup Behavior**</span></span>

<span data-ttu-id="e5db2-118">啟動行為會指定觀察者是否會在第一次具現化時開始執行。</span><span class="sxs-lookup"><span data-stu-id="e5db2-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="e5db2-119">這兩個選項是：</span><span class="sxs-lookup"><span data-stu-id="e5db2-119">The two options are:</span></span>

* <span data-ttu-id="e5db2-120">*自動啟動* -預設值，讓觀察者在初始化之後開始作業</span><span class="sxs-lookup"><span data-stu-id="e5db2-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="e5db2-121">*手動啟動* -觀察者將等候導向開始</span><span class="sxs-lookup"><span data-stu-id="e5db2-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="e5db2-122">如果使用 *手動啟動*，必須 [在執行時間透過程式碼繼續並暫停](UsageGuide.md#starting-and-stopping-mesh-observation)。</span><span class="sxs-lookup"><span data-stu-id="e5db2-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](UsageGuide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="e5db2-123">**更新間隔**</span><span class="sxs-lookup"><span data-stu-id="e5db2-123">**Update Interval**</span></span>

<span data-ttu-id="e5db2-124">對平臺提出更新空間網格資料的要求之間的時間（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="e5db2-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="e5db2-125">一般值落在0.1 和5.0 秒的範圍內。</span><span class="sxs-lookup"><span data-stu-id="e5db2-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="e5db2-126">**為固定觀察者**</span><span class="sxs-lookup"><span data-stu-id="e5db2-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="e5db2-127">指出觀察者是否要保持不變，或移動和更新使用者。</span><span class="sxs-lookup"><span data-stu-id="e5db2-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="e5db2-128">若為 true，觀察範圍所定義之磁片 *區* 的 *觀察者圖形* 將在啟動時保留在來源上。</span><span class="sxs-lookup"><span data-stu-id="e5db2-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="e5db2-129">如果為 false，觀察者空間將會遵循使用者的標頭做為圖形的來源。</span><span class="sxs-lookup"><span data-stu-id="e5db2-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="e5db2-130">系統不會針對觀察者空間以外的任何實體區域計算任何網格資料，如這些屬性所定義： *是固定的觀察* 者、\* 觀察者圖形 \* \*，以及 *觀察範圍*。</span><span class="sxs-lookup"><span data-stu-id="e5db2-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="e5db2-131">**觀察者圖形**</span><span class="sxs-lookup"><span data-stu-id="e5db2-131">**Observer Shape**</span></span>

<span data-ttu-id="e5db2-132">觀察者圖形會定義網格觀察器在觀察網格時將使用的磁片區類型。</span><span class="sxs-lookup"><span data-stu-id="e5db2-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="e5db2-133">支援的選項如下：</span><span class="sxs-lookup"><span data-stu-id="e5db2-133">The supported options are:</span></span>

* <span data-ttu-id="e5db2-134">*軸對齊 Cube* -矩形圖形，與全球座標系統的軸保持一致，如同在應用程式啟動時所決定。</span><span class="sxs-lookup"><span data-stu-id="e5db2-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="e5db2-135">*使用者對齊的 Cube* -矩形圖形，可旋轉以配合使用者的本機座標系統。</span><span class="sxs-lookup"><span data-stu-id="e5db2-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="e5db2-136">*球體* -中央位於世界空間原點的球形音量。</span><span class="sxs-lookup"><span data-stu-id="e5db2-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="e5db2-137">[ *觀察範圍* ] 屬性的 X 值將用作球體的半徑。</span><span class="sxs-lookup"><span data-stu-id="e5db2-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="e5db2-138">**觀察範圍**</span><span class="sxs-lookup"><span data-stu-id="e5db2-138">**Observation Extents**</span></span>

<span data-ttu-id="e5db2-139">觀察範圍會定義觀察到網格的觀察點距離。</span><span class="sxs-lookup"><span data-stu-id="e5db2-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="e5db2-140">物理設定</span><span class="sxs-lookup"><span data-stu-id="e5db2-140">Physics settings</span></span>

![網格觀察者物理設定](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="e5db2-142">**實體層**</span><span class="sxs-lookup"><span data-stu-id="e5db2-142">**Physics Layer**</span></span>

<span data-ttu-id="e5db2-143">將放置空間網格物件以與 Unity 物理學和 RayCast 系統互動的實體層。</span><span class="sxs-lookup"><span data-stu-id="e5db2-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="e5db2-144">混合現實工具組預設會保留 *第31層* ，供空間感知觀察者使用。</span><span class="sxs-lookup"><span data-stu-id="e5db2-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="e5db2-145">**重新計演算法線**</span><span class="sxs-lookup"><span data-stu-id="e5db2-145">**Recalculate Normals**</span></span>

<span data-ttu-id="e5db2-146">指定網格觀察者是否會在觀察之後重新計算網格的法線。</span><span class="sxs-lookup"><span data-stu-id="e5db2-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="e5db2-147">這項設定可用來確保應用程式在不會以網格傳回的平臺上，接收包含有效的法線資料的網格。</span><span class="sxs-lookup"><span data-stu-id="e5db2-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="e5db2-148">詳細資料設定層級</span><span class="sxs-lookup"><span data-stu-id="e5db2-148">Level of detail settings</span></span>

![詳細設定的網格觀察者層級](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="e5db2-150">**詳細資料層級**</span><span class="sxs-lookup"><span data-stu-id="e5db2-150">**Level of Detail**</span></span>

<span data-ttu-id="e5db2-151">指定空間網格資料 (」 LOD) 的詳細層級。</span><span class="sxs-lookup"><span data-stu-id="e5db2-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="e5db2-152">目前定義的值為粗略、精細和自訂。</span><span class="sxs-lookup"><span data-stu-id="e5db2-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="e5db2-153">*粗略* 地對應用程式效能產生較小的影響，這是導覽/平面尋找的絕佳選擇。</span><span class="sxs-lookup"><span data-stu-id="e5db2-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="e5db2-154">*適中* 的設定通常適用于持續掃描環境中的大型功能、地面和牆，以及遮蔽詳細資料的體驗。</span><span class="sxs-lookup"><span data-stu-id="e5db2-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="e5db2-155">一般 exacts 對應用程式效能的影響較高，而且是遮蔽網格的絕佳選項。</span><span class="sxs-lookup"><span data-stu-id="e5db2-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="e5db2-156">*自訂* -要求應用程式指定 *三角形/三次計量* 屬性，並讓應用程式調整精確度和空間網格觀察者的效能影響。</span><span class="sxs-lookup"><span data-stu-id="e5db2-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="e5db2-157">不保證所有的 *三角形/立方計量* 值都能由所有平臺接受。</span><span class="sxs-lookup"><span data-stu-id="e5db2-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="e5db2-158">使用自訂」 LOD 時，強烈建議使用測試和分析。</span><span class="sxs-lookup"><span data-stu-id="e5db2-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="e5db2-159">**每一立方計量的三角形**</span><span class="sxs-lookup"><span data-stu-id="e5db2-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="e5db2-160">在使用 **詳細資料屬性層級** 的 *自訂* 設定，並指定空間網格的三角形密度時有效。</span><span class="sxs-lookup"><span data-stu-id="e5db2-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="e5db2-161">顯示器設定</span><span class="sxs-lookup"><span data-stu-id="e5db2-161">Display settings</span></span>

![網格觀察者顯示設定](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="e5db2-163">**顯示選項**</span><span class="sxs-lookup"><span data-stu-id="e5db2-163">**Display Option**</span></span>

<span data-ttu-id="e5db2-164">指定觀察者如何顯示空間網格。</span><span class="sxs-lookup"><span data-stu-id="e5db2-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="e5db2-165">支援的值為：</span><span class="sxs-lookup"><span data-stu-id="e5db2-165">Supported values are:</span></span>

* <span data-ttu-id="e5db2-166">*無* -觀察者不會呈現網格</span><span class="sxs-lookup"><span data-stu-id="e5db2-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="e5db2-167">可見 *的資料* 會使用 *可見的材質* 顯示</span><span class="sxs-lookup"><span data-stu-id="e5db2-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="e5db2-168">*遮蔽*-網格資料會在場景中使用 *遮蔽材質* 遮蔽專案</span><span class="sxs-lookup"><span data-stu-id="e5db2-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![選取空間感知系統的執行](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="e5db2-170">空間觀察者可以透過程式 [代碼在執行時間繼續/暫停。](UsageGuide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="e5db2-170">Spatial Observers can be [resumed/suspended at runtime via code.](UsageGuide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="e5db2-171">將 *顯示選項* 設定為 [ *無* ] 時， **不** 會停止執行觀察器。</span><span class="sxs-lookup"><span data-stu-id="e5db2-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="e5db2-172">如果您想要停止所有觀察者，則應用程式必須透過 [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="e5db2-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="e5db2-173">**可見的材質**</span><span class="sxs-lookup"><span data-stu-id="e5db2-173">**Visible Material**</span></span>

<span data-ttu-id="e5db2-174">指出將空間網格視覺化時要使用的材質。</span><span class="sxs-lookup"><span data-stu-id="e5db2-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="e5db2-175">**遮蔽材質**</span><span class="sxs-lookup"><span data-stu-id="e5db2-175">**Occlusion Material**</span></span>

<span data-ttu-id="e5db2-176">指出要用來讓空間網格遮蔽全像影像的材質。</span><span class="sxs-lookup"><span data-stu-id="e5db2-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5db2-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5db2-177">See also</span></span>

* [<span data-ttu-id="e5db2-178">空間感知系統</span><span class="sxs-lookup"><span data-stu-id="e5db2-178">Spatial Awareness System</span></span>](SpatialAwarenessGettingStarted.md)
* [<span data-ttu-id="e5db2-179">透過程式碼設定空間感知系統</span><span class="sxs-lookup"><span data-stu-id="e5db2-179">Configuring Spatial Awareness system via Code</span></span>](UsageGuide.md)
* [<span data-ttu-id="e5db2-180">IMixedRealitySpatialAwarenessObserver API 檔</span><span class="sxs-lookup"><span data-stu-id="e5db2-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="e5db2-181">IMixedRealitySpatialAwarenessMeshObserver API 檔</span><span class="sxs-lookup"><span data-stu-id="e5db2-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="e5db2-182">BaseSpatialObserver API 檔</span><span class="sxs-lookup"><span data-stu-id="e5db2-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
