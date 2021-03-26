---
title: Unity 中的空間對應
description: 瞭解如何在 Unity 混合現實應用程式中，使用及管理與您有關的真實世界幾何呈現和衝突。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間對應、轉譯器、碰撞器、網格、掃描、元件、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: e2ef6ac43e81ff2b8e66a4bd197ea41c198a1626
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105549948"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="354c7-104">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="354c7-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="354c7-105">[空間對應](../../design/spatial-mapping.md) 可讓您取得代表 HoloLens 裝置周圍之表面的三角形網格。</span><span class="sxs-lookup"><span data-stu-id="354c7-105">[spatial mapping](../../design/spatial-mapping.md) lets you retrieve triangle meshes that represent the surfaces in the world around a HoloLens device.</span></span> <span data-ttu-id="354c7-106">您可以使用 surface 資料進行放置、遮蔽和房間分析，讓您的 Unity 專案有額外的深度劑量。</span><span class="sxs-lookup"><span data-stu-id="354c7-106">You can use surface data for placement, occlusion, and room analysis to give your Unity projects an extra dose of immersion.</span></span>

<span data-ttu-id="354c7-107">Unity 包含空間對應的完整支援，可透過下列方式公開給開發人員：</span><span class="sxs-lookup"><span data-stu-id="354c7-107">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="354c7-108">MixedRealityToolkit 中提供的空間對應元件，可為開始使用空間對應提供便利快速的路徑</span><span class="sxs-lookup"><span data-stu-id="354c7-108">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="354c7-109">較低層級的空間對應 Api，可提供完整控制權，並啟用更精密的應用程式特定自訂</span><span class="sxs-lookup"><span data-stu-id="354c7-109">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application-specific customization</span></span>

<span data-ttu-id="354c7-110">若要在您的應用程式中使用空間對應，必須在 Package.appxmanifest 中設定 >spatialperception 功能。</span><span class="sxs-lookup"><span data-stu-id="354c7-110">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="354c7-111">裝置支援</span><span class="sxs-lookup"><span data-stu-id="354c7-111">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="354c7-112"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="354c7-112"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="354c7-113"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第一代) </strong></a></span><span class="sxs-lookup"><span data-stu-id="354c7-113"><a href="/hololens/hololens1-hardware"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="354c7-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="354c7-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="354c7-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="354c7-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="354c7-116">空間對應</span><span class="sxs-lookup"><span data-stu-id="354c7-116">Spatial mapping</span></span></td>
        <td><span data-ttu-id="354c7-117">✔️</span><span class="sxs-lookup"><span data-stu-id="354c7-117">✔️</span></span></td>
        <td><span data-ttu-id="354c7-118">✔️</span><span class="sxs-lookup"><span data-stu-id="354c7-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="354c7-119">設定 >spatialperception 功能</span><span class="sxs-lookup"><span data-stu-id="354c7-119">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="354c7-120">為了讓應用程式使用空間對應資料，必須啟用 >spatialperception 功能。</span><span class="sxs-lookup"><span data-stu-id="354c7-120">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="354c7-121">如何啟用 >spatialperception 功能：</span><span class="sxs-lookup"><span data-stu-id="354c7-121">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="354c7-122">在 Unity 編輯器中，開啟 [ **播放機設定** ] 窗格 (編輯 > 專案設定 > 播放) </span><span class="sxs-lookup"><span data-stu-id="354c7-122">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="354c7-123">選取 [ **Windows 存放區** ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="354c7-123">Select on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="354c7-124">展開 [**發行設定]** ，並檢查 [**功能]** 清單中的 [ **>spatialperception]** 功能</span><span class="sxs-lookup"><span data-stu-id="354c7-124">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

> [!NOTE]
> <span data-ttu-id="354c7-125">如果您已將 Unity 專案匯出至 Visual Studio 的解決方案，您必須匯出至新資料夾，或在 [Visual Studio 的 package.appxmanifest 中手動設定這項功能](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。</span><span class="sxs-lookup"><span data-stu-id="354c7-125">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="354c7-126">空間對應也需要至少10.0.10586.0 的 MaxVersionTested：</span><span class="sxs-lookup"><span data-stu-id="354c7-126">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="354c7-127">在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的 **package.appxmanifest** ，然後選取 [ **View Code** ]</span><span class="sxs-lookup"><span data-stu-id="354c7-127">In Visual Studio, right-click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="354c7-128">找出指定 **y** 的行，並將 **MaxVersionTested = "10.0.10240.0"** 變更為 **MaxVersionTested = "10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="354c7-128">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="354c7-129">**儲存** package.appxmanifest。</span><span class="sxs-lookup"><span data-stu-id="354c7-129">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="354c7-130">開始使用 Unity 的內建空間對應元件</span><span class="sxs-lookup"><span data-stu-id="354c7-130">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="354c7-131">Unity 提供兩個元件，可讓您輕鬆地將空間對應新增至您的應用程式、 **空間對應** 轉譯器和 **空間對應碰撞** 器。</span><span class="sxs-lookup"><span data-stu-id="354c7-131">Unity offers two components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="354c7-132">空間對應轉譯器</span><span class="sxs-lookup"><span data-stu-id="354c7-132">Spatial Mapping Renderer</span></span>

<span data-ttu-id="354c7-133">空間對應轉譯器可讓空間對應網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="354c7-133">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Unity 中的空間對應轉譯器](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="354c7-135">空間對應碰撞</span><span class="sxs-lookup"><span data-stu-id="354c7-135">Spatial Mapping Collider</span></span>

<span data-ttu-id="354c7-136">空間對應碰撞程式可允許全像的內容 (或字元) 互動，例如物理，以及空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="354c7-136">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Unity 中的空間對應碰撞](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="354c7-138">使用內建空間對應元件</span><span class="sxs-lookup"><span data-stu-id="354c7-138">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="354c7-139">如果您想要將這兩個元件視覺化並與實體介面互動，您可以將這兩個元件新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="354c7-139">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="354c7-140">若要在 Unity 應用程式中使用這兩個元件：</span><span class="sxs-lookup"><span data-stu-id="354c7-140">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="354c7-141">在您想要偵測空間介面網格的區域中央選取 GameObject。</span><span class="sxs-lookup"><span data-stu-id="354c7-141">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="354c7-142">在 [偵測器] 視窗中，**加入元件**  >  **XR**  >  **空間對應碰撞** 器或 **空間對應** 轉譯器。</span><span class="sxs-lookup"><span data-stu-id="354c7-142">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="354c7-143">您可以在 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 檔網站</a>找到更多有關如何使用這些元件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="354c7-143">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="354c7-144">超越內建空間對應元件</span><span class="sxs-lookup"><span data-stu-id="354c7-144">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="354c7-145">這些元件可讓您輕鬆地開始使用空間對應。</span><span class="sxs-lookup"><span data-stu-id="354c7-145">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span>  <span data-ttu-id="354c7-146">當您想要繼續進行時，有兩個主要的途徑可以探索：</span><span class="sxs-lookup"><span data-stu-id="354c7-146">When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="354c7-147">若要進行您自己的較低層級網格處理，請參閱下一節有關低層級空間對應腳本 API 的資訊。</span><span class="sxs-lookup"><span data-stu-id="354c7-147">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="354c7-148">若要進行較高層級的網狀分析，請參閱下列有關 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>中 SpatialUnderstanding 程式庫的章節。</span><span class="sxs-lookup"><span data-stu-id="354c7-148">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="354c7-149">使用低層級 Unity 空間對應 API</span><span class="sxs-lookup"><span data-stu-id="354c7-149">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="354c7-150">如果您需要比空間對應轉譯器和空間對應碰撞器元件供應專案更多的控制，請使用低層級空間對應 Api。</span><span class="sxs-lookup"><span data-stu-id="354c7-150">If you need more control than the Spatial Mapping Renderer and Spatial Mapping Collider components offer, use the low-level Spatial Mapping APIs.</span></span>

<span data-ttu-id="354c7-151">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="354c7-151">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="354c7-152">**類型**： *SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="354c7-152">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="354c7-153">我們概述了在下列各節中使用空間對應 Api 的應用程式所建議的流程。</span><span class="sxs-lookup"><span data-stu-id="354c7-153">We've outlined the suggested flow for an application that uses the spatial mapping APIs in the sections below.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="354c7-154">設定 SurfaceObserver (s) </span><span class="sxs-lookup"><span data-stu-id="354c7-154">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="354c7-155">針對需要空間對應資料的每個應用程式定義區域，將一個 SurfaceObserver 物件具現化。</span><span class="sxs-lookup"><span data-stu-id="354c7-155">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="354c7-156">藉由呼叫 SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox 或 SetVolumeAsFrustum，指定每個 SurfaceObserver 物件將提供資料的空間區域。</span><span class="sxs-lookup"><span data-stu-id="354c7-156">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="354c7-157">您可以直接呼叫其中一個方法，在未來重新定義空間的區域。</span><span class="sxs-lookup"><span data-stu-id="354c7-157">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="354c7-158">當您呼叫 SurfaceObserver () 時，您必須針對空間對應系統具有新資訊的空間 SurfaceObserver 區域中的每個空間介面，提供一個處理常式。</span><span class="sxs-lookup"><span data-stu-id="354c7-158">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="354c7-159">處理常式會收到一個空間介面：</span><span class="sxs-lookup"><span data-stu-id="354c7-159">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="354c7-160">處理介面變更</span><span class="sxs-lookup"><span data-stu-id="354c7-160">Handling Surface Changes</span></span>

<span data-ttu-id="354c7-161">有幾個主要案例要處理-新增和更新，可以使用相同的程式碼路徑，並移除。</span><span class="sxs-lookup"><span data-stu-id="354c7-161">There are several main cases to handle - added and updated, which can use the same code path, and removed.</span></span>
* <span data-ttu-id="354c7-162">在新增和更新的案例中，我們會在字典中加入或取得代表這個網格的 GameObject、建立具有必要元件的 SurfaceData 結構，然後呼叫 RequestMeshDataAsync，以在場景中填入網格資料和位置的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="354c7-162">In the added and updated cases, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="354c7-163">在移除的案例中，我們會從字典中移除代表這個網格的 GameObject，並將它終結。</span><span class="sxs-lookup"><span data-stu-id="354c7-163">In the removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="354c7-164">處理資料就緒</span><span class="sxs-lookup"><span data-stu-id="354c7-164">Handling Data Ready</span></span>

<span data-ttu-id="354c7-165">OnDataReady 處理常式會接收 SurfaceData 物件。</span><span class="sxs-lookup"><span data-stu-id="354c7-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="354c7-166">WorldAnchor、MeshFilter 和 (選擇性地) 它所包含的 MeshCollider 物件會反映相關聯空間介面的最新狀態。</span><span class="sxs-lookup"><span data-stu-id="354c7-166">The WorldAnchor, MeshFilter, and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="354c7-167">（選擇性）藉由存取 MeshFilter 物件的網狀成員來分析及/或 [處理](../../design/spatial-mapping.md#mesh-processing) 網格資料。</span><span class="sxs-lookup"><span data-stu-id="354c7-167">Optionally, analyze and/or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="354c7-168">使用最新的網格轉譯空間介面，並 (選擇性地) 將它用於物理衝突和 raycasts。</span><span class="sxs-lookup"><span data-stu-id="354c7-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="354c7-169">請務必確認 SurfaceData 的內容不是 null。</span><span class="sxs-lookup"><span data-stu-id="354c7-169">It's important to confirm that the contents of the SurfaceData aren't null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="354c7-170">開始處理更新</span><span class="sxs-lookup"><span data-stu-id="354c7-170">Start processing on updates</span></span>

<span data-ttu-id="354c7-171">SurfaceObserver 應該在延遲而不是每個畫面上呼叫更新 () 。</span><span class="sxs-lookup"><span data-stu-id="354c7-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="354c7-172">較高層級的網狀分析： SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="354c7-172">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="354c7-173"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是以 Unity 的全像內嵌式 api 為基礎進行全像開發的公用程式程式碼集合。</span><span class="sxs-lookup"><span data-stu-id="354c7-173">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of utility code for holographic development built on Unity's holographic APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="354c7-174">空間理解</span><span class="sxs-lookup"><span data-stu-id="354c7-174">Spatial Understanding</span></span>

<span data-ttu-id="354c7-175">在實體世界中放置全像影像時，通常會想要超越空間對應的網格和表面平面。</span><span class="sxs-lookup"><span data-stu-id="354c7-175">When placing holograms in the physical world, it's often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="354c7-176">當放置完成 cti 時，需要較高層級的環境理解。</span><span class="sxs-lookup"><span data-stu-id="354c7-176">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="354c7-177">這通常需要做出有關樓層、上限和牆壁的決策。</span><span class="sxs-lookup"><span data-stu-id="354c7-177">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="354c7-178">您也可以針對一組放置條件約束進行優化，以判斷全像攝影物件最適合的實體位置。</span><span class="sxs-lookup"><span data-stu-id="354c7-178">You also have the ability to optimize against a set of placement constraints to determine the most best physical locations for holographic objects.</span></span>

<span data-ttu-id="354c7-179">在開發年輕 Conker 和片段的期間，Asobo 工作室藉由開發會議室規劃求解來面對這個問題。</span><span class="sxs-lookup"><span data-stu-id="354c7-179">During development of Young Conker and Fragments, Asobo Studios faced this problem head on by developing a room solver.</span></span> <span data-ttu-id="354c7-180">這些遊戲都有遊戲專屬的需求，但它們共用了核心空間的理解技術。</span><span class="sxs-lookup"><span data-stu-id="354c7-180">Each of these games had game-specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="354c7-181">HoloToolkit. SpatialUnderstanding 程式庫會封裝這項技術，可讓您快速找出牆上的空格、將物件放在最上方、找出放置的字元，以及許多其他空間理解查詢。</span><span class="sxs-lookup"><span data-stu-id="354c7-181">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="354c7-182">所有原始程式碼都包含在內，可讓您依據需求進行自訂，並與您的小組分享您的改進。</span><span class="sxs-lookup"><span data-stu-id="354c7-182">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="354c7-183">C + + 規劃的程式碼已經包裝成 UWP dll，並使用 MixedRealityToolkit 中包含的預製專案來公開給 Unity。</span><span class="sxs-lookup"><span data-stu-id="354c7-183">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="354c7-184">瞭解模組</span><span class="sxs-lookup"><span data-stu-id="354c7-184">Understanding Modules</span></span>

<span data-ttu-id="354c7-185">模組會公開三個主要介面：適用于簡單介面和空間查詢的拓撲、物件偵測的圖形，以及物件放置規劃求解的物件集合之條件約束的位置。</span><span class="sxs-lookup"><span data-stu-id="354c7-185">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint-based placement of object sets.</span></span> <span data-ttu-id="354c7-186">以下說明上述各方式。</span><span class="sxs-lookup"><span data-stu-id="354c7-186">Each of these is described below.</span></span> <span data-ttu-id="354c7-187">除了三個主要模組介面外，還可以使用光線轉型介面來取出標記的介面類別型，而且可以將自訂的防水 playspace 網格複製出來。</span><span class="sxs-lookup"><span data-stu-id="354c7-187">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="354c7-188">光線轉換</span><span class="sxs-lookup"><span data-stu-id="354c7-188">Ray Casting</span></span>

<span data-ttu-id="354c7-189">當房間掃描完成之後，就會在內部產生標籤，例如樓層、上限和牆。</span><span class="sxs-lookup"><span data-stu-id="354c7-189">After the room scan is completed, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="354c7-190">"PlayspaceRaycast" 函式會使用光線，並在光線與已知表面衝突時傳回，如果是，則以 "RaycastResult" 的形式呈現該介面的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="354c7-190">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="354c7-191">就內部而言，raycast 是針對 playspace 的計算出的 8-cm 立方體素標記法來計算。</span><span class="sxs-lookup"><span data-stu-id="354c7-191">Internally, the raycast is computed against the computed 8-cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="354c7-192">每個體素都包含一組介面元素，其中包含已處理的拓撲資料 (也稱為 surfels) 。</span><span class="sxs-lookup"><span data-stu-id="354c7-192">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="354c7-193">會比較交集體素資料格內所含的 surfels，以及用來查閱拓撲資訊的最佳相符項。</span><span class="sxs-lookup"><span data-stu-id="354c7-193">The surfels contained within the intersected voxel cell is compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="354c7-194">此拓撲資料包含以 "SurfaceTypes" 列舉的形式傳回的標籤，以及交集資料表面的介面區。</span><span class="sxs-lookup"><span data-stu-id="354c7-194">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="354c7-195">在 Unity 範例中，資料指標會將光線轉換成每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="354c7-195">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="354c7-196">首先，針對 Unity 的 colliders。</span><span class="sxs-lookup"><span data-stu-id="354c7-196">First, against Unity’s colliders.</span></span> <span data-ttu-id="354c7-197">第二，針對瞭解模組的世界標記法。</span><span class="sxs-lookup"><span data-stu-id="354c7-197">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="354c7-198">最後一個是 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="354c7-198">And finally, again UI elements.</span></span> <span data-ttu-id="354c7-199">在此應用程式中，UI 會獲得優先權、接下來的理解結果，最後是 Unity 的 colliders。</span><span class="sxs-lookup"><span data-stu-id="354c7-199">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="354c7-200">SurfaceType 會回報為數據指標旁的文字。</span><span class="sxs-lookup"><span data-stu-id="354c7-200">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="354c7-201">![介面類別型在游標旁邊標示](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="354c7-201">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="354c7-202">*介面類別型在游標旁邊標示*</span><span class="sxs-lookup"><span data-stu-id="354c7-202">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="354c7-203">拓撲查詢</span><span class="sxs-lookup"><span data-stu-id="354c7-203">Topology Queries</span></span>

<span data-ttu-id="354c7-204">在 DLL 內，拓撲管理員會處理環境的標籤。</span><span class="sxs-lookup"><span data-stu-id="354c7-204">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="354c7-205">如上所述，大部分的資料會儲存在 surfels 中，並包含在體素磁片區中。</span><span class="sxs-lookup"><span data-stu-id="354c7-205">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="354c7-206">此外，還會使用 "PlaySpaceInfos" 結構來儲存有關 playspace 的資訊，包括世界上的對齊 (更多有關以下) 、樓層和最高高度的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="354c7-206">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="354c7-207">啟發學習法可用來決定樓層、上限和牆。</span><span class="sxs-lookup"><span data-stu-id="354c7-207">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="354c7-208">例如，具有大於 1-m2 介面區的最大和最低水準介面會被視為樓層。</span><span class="sxs-lookup"><span data-stu-id="354c7-208">For example, the largest and lowest horizontal surface with greater than 1-m2 surface area is considered the floor.</span></span> 

> [!NOTE]
> <span data-ttu-id="354c7-209">掃描過程中的攝影機路徑也會在此程式中使用。</span><span class="sxs-lookup"><span data-stu-id="354c7-209">The camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="354c7-210">拓撲管理員公開的查詢子集會透過 dll 公開。</span><span class="sxs-lookup"><span data-stu-id="354c7-210">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="354c7-211">公開的拓撲查詢如下所示。</span><span class="sxs-lookup"><span data-stu-id="354c7-211">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="354c7-212">每個查詢都有一組參數，特定于查詢類型。</span><span class="sxs-lookup"><span data-stu-id="354c7-212">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="354c7-213">在下列範例中，使用者會指定所需磁片區的最小高度 & 寬度、地面上方的最小放置高度，以及磁片區前方的最小間隙量。</span><span class="sxs-lookup"><span data-stu-id="354c7-213">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="354c7-214">所有度量都是計量。</span><span class="sxs-lookup"><span data-stu-id="354c7-214">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="354c7-215">這些查詢都採用預先配置的 "TopologyResult" 結構陣列。</span><span class="sxs-lookup"><span data-stu-id="354c7-215">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="354c7-216">"LocationCount" 參數指定傳入陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="354c7-216">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="354c7-217">傳回值會回報傳回位置的數目。</span><span class="sxs-lookup"><span data-stu-id="354c7-217">The return value reports the number of returned locations.</span></span> <span data-ttu-id="354c7-218">此數位絕不會大於傳入的 "locationCount" 參數。</span><span class="sxs-lookup"><span data-stu-id="354c7-218">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="354c7-219">"TopologyResult" 包含傳回之磁片區的中心位置、面向方向 (例如正常) ，以及所找到空間的維度。</span><span class="sxs-lookup"><span data-stu-id="354c7-219">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

> [!NOTE]
> <span data-ttu-id="354c7-220">在 Unity 範例中，每個查詢都會連結到虛擬 UI 面板中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="354c7-220">In the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="354c7-221">此範例會將每個查詢的參數設為合理的值。</span><span class="sxs-lookup"><span data-stu-id="354c7-221">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="354c7-222">如需更多範例，請參閱範例程式碼中的 SpaceVisualizer。</span><span class="sxs-lookup"><span data-stu-id="354c7-222">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="354c7-223">圖形查詢</span><span class="sxs-lookup"><span data-stu-id="354c7-223">Shape Queries</span></span>

<span data-ttu-id="354c7-224">在 dll 中，圖形分析器 ( "ShapeAnalyzer_W" ) 使用拓朴分析器來比對使用者所定義的自訂圖形。</span><span class="sxs-lookup"><span data-stu-id="354c7-224">In the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="354c7-225">Unity 範例會定義一組圖形，並透過 [圖形] 索引標籤中的應用程式內查詢功能表來公開結果。其目的是讓使用者可以定義自己的物件圖形查詢，並視其應用程式的需要來使用這些查詢。</span><span class="sxs-lookup"><span data-stu-id="354c7-225">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="354c7-226">圖形分析僅適用于水準表面。</span><span class="sxs-lookup"><span data-stu-id="354c7-226">The shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="354c7-227">例如，一名沙發是由平面基座介面和沙發的一般頂端所定義。</span><span class="sxs-lookup"><span data-stu-id="354c7-227">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="354c7-228">圖形查詢會尋找特定大小、高度和外觀範圍的兩個表面，並將兩個表面對齊並連接。</span><span class="sxs-lookup"><span data-stu-id="354c7-228">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="354c7-229">使用 Api 術語時，沙發基座和上一頁是圖形元件，而對齊需求是圖形元件條件約束。</span><span class="sxs-lookup"><span data-stu-id="354c7-229">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="354c7-230">在 Unity 範例 () ShapeDefinition 中定義的範例查詢，"sittable" 物件如下所示。</span><span class="sxs-lookup"><span data-stu-id="354c7-230">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="354c7-231">每個圖形查詢都是由一組圖形元件所定義，每個都有一組元件條件約束，以及一組列出元件之間相依性的圖形條件約束。</span><span class="sxs-lookup"><span data-stu-id="354c7-231">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="354c7-232">此範例包含單一元件定義中的三個條件約束，而且元件之間沒有任何形狀條件約束 (因為只有一個元件) 。</span><span class="sxs-lookup"><span data-stu-id="354c7-232">This example includes three constraints in a single component definition and no shape constraints between components (as there's only one component).</span></span>

<span data-ttu-id="354c7-233">相反地，「沙發」圖形有兩個圖形元件和四個「形狀」條件約束。</span><span class="sxs-lookup"><span data-stu-id="354c7-233">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="354c7-234">元件是以使用者元件清單中的索引來識別， (0 和1在此範例中) 。</span><span class="sxs-lookup"><span data-stu-id="354c7-234">Components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="354c7-235">Unity 模組中提供包裝函式，可讓您輕鬆地建立自訂圖形定義。</span><span class="sxs-lookup"><span data-stu-id="354c7-235">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="354c7-236">您可以在 "ShapeComponentConstraint" 和 "ShapeConstraint" 結構內的 "SpatialUnderstandingDll" 中找到元件和圖形條件約束的完整清單。</span><span class="sxs-lookup"><span data-stu-id="354c7-236">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="354c7-237">![在此表面找到矩形圖形](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="354c7-237">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="354c7-238">*在此表面找到矩形圖形*</span><span class="sxs-lookup"><span data-stu-id="354c7-238">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="354c7-239">物件放置規劃求解</span><span class="sxs-lookup"><span data-stu-id="354c7-239">Object Placement Solver</span></span>

<span data-ttu-id="354c7-240">物件放置規劃求解可以用來識別實體房間中的理想位置，以放置您的物件。</span><span class="sxs-lookup"><span data-stu-id="354c7-240">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="354c7-241">根據物件規則和條件約束，規劃求解會找出最適合的位置。</span><span class="sxs-lookup"><span data-stu-id="354c7-241">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="354c7-242">此外，物件查詢會持續存在，直到以「Solver_RemoveObject」或「Solver_RemoveAllObjects」呼叫來移除物件為止，並允許受限的多重物件放置。</span><span class="sxs-lookup"><span data-stu-id="354c7-242">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="354c7-243">物件放置查詢包含三個部分：具有參數的放置類型、規則清單和條件約束清單。</span><span class="sxs-lookup"><span data-stu-id="354c7-243">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="354c7-244">若要執行查詢，請使用下列 API。</span><span class="sxs-lookup"><span data-stu-id="354c7-244">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="354c7-245">此函式會接受物件名稱、位置定義，以及規則和條件約束的清單。</span><span class="sxs-lookup"><span data-stu-id="354c7-245">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="354c7-246">C # 包裝函式提供了結構協助程式函式，讓規則和條件約束結構更容易。</span><span class="sxs-lookup"><span data-stu-id="354c7-246">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="354c7-247">放置定義包含查詢類型–也就是下列其中一項。</span><span class="sxs-lookup"><span data-stu-id="354c7-247">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="354c7-248">每個放置類型都有一組唯一類型的參數。</span><span class="sxs-lookup"><span data-stu-id="354c7-248">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="354c7-249">"ObjectPlacementDefinition" 結構包含一組靜態 helper 函式，可用於建立這些定義。</span><span class="sxs-lookup"><span data-stu-id="354c7-249">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="354c7-250">例如，若要尋找將物件放在樓層的位置，您可以使用下列函數。</span><span class="sxs-lookup"><span data-stu-id="354c7-250">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="354c7-251">公用靜態 ObjectPlacementDefinition Create_OnFloor (Vector3) halfDims 除了放置類型以外，您也可以提供一組規則和條件約束。</span><span class="sxs-lookup"><span data-stu-id="354c7-251">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="354c7-252">無法違反規則。</span><span class="sxs-lookup"><span data-stu-id="354c7-252">Rules cannot be violated.</span></span> <span data-ttu-id="354c7-253">接著，滿足型別和規則的可能放置位置會針對一組條件約束進行優化，以便選取最佳放置位置。</span><span class="sxs-lookup"><span data-stu-id="354c7-253">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="354c7-254">每個規則和條件約束都可以透過提供的靜態建立函式來建立。</span><span class="sxs-lookup"><span data-stu-id="354c7-254">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="354c7-255">以下提供範例規則和條件約束結構函數。</span><span class="sxs-lookup"><span data-stu-id="354c7-255">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="354c7-256">下列物件放置查詢正在尋找在介面邊緣放置半計量立方體的位置，而不是從其他先前放置的物件和靠近房間的中央。</span><span class="sxs-lookup"><span data-stu-id="354c7-256">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="354c7-257">如果成功，則會傳回包含放置位置、維度和方向的 "ObjectPlacementResult" 結構。</span><span class="sxs-lookup"><span data-stu-id="354c7-257">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions, and orientation is returned.</span></span> <span data-ttu-id="354c7-258">此外，會將放置新增至 dll 的已放置物件的內部清單。</span><span class="sxs-lookup"><span data-stu-id="354c7-258">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="354c7-259">後續的放置查詢會將此物件列入考慮。</span><span class="sxs-lookup"><span data-stu-id="354c7-259">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="354c7-260">Unity 範例中的 "LevelSolver .cs" 檔案包含更多範例查詢。</span><span class="sxs-lookup"><span data-stu-id="354c7-260">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="354c7-261">![物件放置的結果](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="354c7-261">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="354c7-262">*圖3：藍色方塊如何從三個位置查詢的結果，而不是相機位置規則*</span><span class="sxs-lookup"><span data-stu-id="354c7-262">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="354c7-263">當您針對層級或應用程式案例所需的多個物件進行放置位置的解決時，請先解決不可或缺和大型物件，以充分發揮可找到空間的機率。</span><span class="sxs-lookup"><span data-stu-id="354c7-263">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="354c7-264">放置順序很重要。</span><span class="sxs-lookup"><span data-stu-id="354c7-264">Placement order is important.</span></span> <span data-ttu-id="354c7-265">如果找不到物件放置，請嘗試較不受限制的設定。</span><span class="sxs-lookup"><span data-stu-id="354c7-265">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="354c7-266">擁有一組恢復設定對於跨許多房間設定支援功能非常重要。</span><span class="sxs-lookup"><span data-stu-id="354c7-266">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="354c7-267">會議室掃描流程</span><span class="sxs-lookup"><span data-stu-id="354c7-267">Room Scanning Process</span></span>

<span data-ttu-id="354c7-268">雖然 HoloLens 提供的空間對應解決方案設計成足以滿足整個問題空間的需求，但空間理解模組的設計是為了支援兩項特定遊戲的需求。</span><span class="sxs-lookup"><span data-stu-id="354c7-268">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="354c7-269">它的解決方案是以特定程式和假設集為依據，如下所摘要。</span><span class="sxs-lookup"><span data-stu-id="354c7-269">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="354c7-270">使用者導向 playspace 「繪製」–在掃描階段期間，使用者會四處移動並查看播放步調，有效地繪製應該包含的區域。</span><span class="sxs-lookup"><span data-stu-id="354c7-270">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas, which should be included.</span></span> <span data-ttu-id="354c7-271">產生的網格很重要，可在此階段提供使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="354c7-271">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="354c7-272">室內家用或 office 設定–查詢函式是以適當角度的平面和牆為中心設計的。</span><span class="sxs-lookup"><span data-stu-id="354c7-272">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="354c7-273">這是一項軟性限制。</span><span class="sxs-lookup"><span data-stu-id="354c7-273">This is a soft limitation.</span></span> <span data-ttu-id="354c7-274">不過，在掃描階段期間，主要軸分析已完成，可將網格鑲嵌沿著主要和次要軸優化。</span><span class="sxs-lookup"><span data-stu-id="354c7-274">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="354c7-275">內含的 SpatialUnderstanding .cs 檔案會管理掃描階段程式。</span><span class="sxs-lookup"><span data-stu-id="354c7-275">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="354c7-276">它會呼叫下列函數。</span><span class="sxs-lookup"><span data-stu-id="354c7-276">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="354c7-277">掃描流程（由 "SpatialUnderstanding" 行為驅動）會呼叫 InitScan，然後 UpdateScan 每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="354c7-277">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="354c7-278">當統計資料查詢報告合理的涵蓋範圍時，使用者就可以 airtap 呼叫 RequestFinish 來指出掃描階段結束。</span><span class="sxs-lookup"><span data-stu-id="354c7-278">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="354c7-279">UpdateScan 會繼續呼叫，直到其傳回值指出 dll 已完成處理。</span><span class="sxs-lookup"><span data-stu-id="354c7-279">UpdateScan continues to be called until its return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="354c7-280">瞭解網格</span><span class="sxs-lookup"><span data-stu-id="354c7-280">Understanding Mesh</span></span>

<span data-ttu-id="354c7-281">瞭解 dll 會在內部將 playspace 儲存為 8 cm 大小體素 cube 的方格。</span><span class="sxs-lookup"><span data-stu-id="354c7-281">The understanding dll internally stores the playspace as a grid of 8 cm sized voxel cubes.</span></span> <span data-ttu-id="354c7-282">在掃描的初始部分期間，主要元件分析完成以判斷房間的座標軸。</span><span class="sxs-lookup"><span data-stu-id="354c7-282">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="354c7-283">就內部而言，它會儲存其體素空間與這些軸對齊。</span><span class="sxs-lookup"><span data-stu-id="354c7-283">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="354c7-284">從體素磁片區解壓縮 isosurface，大約每秒會產生一個網狀。</span><span class="sxs-lookup"><span data-stu-id="354c7-284">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="354c7-285">![從體素磁片區產生的網狀](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="354c7-285">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="354c7-286">*從體素磁片區產生的網狀*</span><span class="sxs-lookup"><span data-stu-id="354c7-286">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="354c7-287">疑難排解</span><span class="sxs-lookup"><span data-stu-id="354c7-287">Troubleshooting</span></span>
* <span data-ttu-id="354c7-288">確定您已設定 [>spatialperception](#setting-the-spatialperception-capability) 功能</span><span class="sxs-lookup"><span data-stu-id="354c7-288">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="354c7-289">當追蹤遺失時，下一個 OnSurfaceChanged 事件將會移除所有的網格。</span><span class="sxs-lookup"><span data-stu-id="354c7-289">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="354c7-290">混合現實工具組中的空間對應</span><span class="sxs-lookup"><span data-stu-id="354c7-290">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="354c7-291">如需有關搭配使用空間對應與混合現實工具組 v2 的詳細資訊，請參閱 MRTK 檔的 <a href="/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">空間感知一節</a> 。</span><span class="sxs-lookup"><span data-stu-id="354c7-291">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="354c7-292">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="354c7-292">Next Development Checkpoint</span></span>

<span data-ttu-id="354c7-293">如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。</span><span class="sxs-lookup"><span data-stu-id="354c7-293">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="354c7-294">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="354c7-294">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="354c7-295">Text</span><span class="sxs-lookup"><span data-stu-id="354c7-295">Text</span></span>](text-in-unity.md)

<span data-ttu-id="354c7-296">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="354c7-296">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="354c7-297">共用體驗</span><span class="sxs-lookup"><span data-stu-id="354c7-297">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="354c7-298">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="354c7-298">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="354c7-299">另請參閱</span><span class="sxs-lookup"><span data-stu-id="354c7-299">See also</span></span>
* [<span data-ttu-id="354c7-300">座標系統</span><span class="sxs-lookup"><span data-stu-id="354c7-300">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="354c7-301">Unity 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="354c7-301">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="354c7-302"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="354c7-302"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="354c7-303"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="354c7-303"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="354c7-304"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="354c7-304"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="354c7-305"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine</a></span><span class="sxs-lookup"><span data-stu-id="354c7-305"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>