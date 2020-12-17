---
title: DirectX 中的空間對應
description: 瞭解如何在您的 DirectX 應用程式中執行空間對應，包括通用 Windows 平臺 SDK 隨附的空間對應範例應用程式。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows mixed reality、空間對應、環境、互動、directx、winrt、api、範例程式碼、UWP、SDK、逐步解說
ms.openlocfilehash: fa372473939222ef4be7ca36076a17241173c441
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612912"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="326db-104">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="326db-104">Spatial mapping in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="326db-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="326db-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="326db-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)**。</span><span class="sxs-lookup"><span data-stu-id="326db-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="326db-107">本主題說明如何在 DirectX 應用程式中執行 [空間對應](../../design/spatial-mapping.md) ，包括使用通用 Windows 平臺 SDK 封裝的空間對應範例應用程式的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="326db-107">This topic describes how to implement [spatial mapping](../../design/spatial-mapping.md) in your DirectX app, including a detailed explanation of the spatial mapping sample application packaged with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="326db-108">本主題使用 [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 程式碼範例中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="326db-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="326db-109">本文中的程式碼片段目前示範如何使用 c + + [/cx，而](creating-a-holographic-directx-project.md)不是 c + + 全像 c + + 全像 c + + 的 + 17 相容 c + +/WinRT。</span><span class="sxs-lookup"><span data-stu-id="326db-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="326db-110">這些概念對 c + +/WinRT 專案而言是相等的，不過您必須轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="326db-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="326db-111">裝置支援</span><span class="sxs-lookup"><span data-stu-id="326db-111">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="326db-112"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="326db-112"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="326db-113"><a href="../../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="326db-113"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="326db-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="326db-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="326db-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="326db-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="326db-116">空間對應</span><span class="sxs-lookup"><span data-stu-id="326db-116">Spatial mapping</span></span></td>
        <td><span data-ttu-id="326db-117">✔️</span><span class="sxs-lookup"><span data-stu-id="326db-117">✔️</span></span></td>
        <td><span data-ttu-id="326db-118">✔️</span><span class="sxs-lookup"><span data-stu-id="326db-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a><span data-ttu-id="326db-119">DirectX 開發概觀</span><span class="sxs-lookup"><span data-stu-id="326db-119">DirectX development overview</span></span>

<span data-ttu-id="326db-120">空間對應的原生應用程式開發會使用 [Windows](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) 中的 api。空間命名空間。</span><span class="sxs-lookup"><span data-stu-id="326db-120">Native application development for spatial mapping uses the APIs in the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="326db-121">這些 Api 可讓您完全掌控空間對應功能，與 [Unity](../unity/spatial-mapping-in-unity.md)公開空間對應 api 的方式相同。</span><span class="sxs-lookup"><span data-stu-id="326db-121">These APIs give you full control of spatial mapping functionality, in the same way that spatial mapping APIs are exposed by [Unity](../unity/spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="326db-122">認知 Api</span><span class="sxs-lookup"><span data-stu-id="326db-122">Perception APIs</span></span>

<span data-ttu-id="326db-123">針對空間對應開發提供的主要類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="326db-123">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="326db-124">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) 會以 SpatialSurfaceInfo 物件的形式，提供使用者附近空間的應用程式指定區域相關資訊。</span><span class="sxs-lookup"><span data-stu-id="326db-124">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="326db-125">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) 描述單一現存空間介面，包括唯一識別碼、周框磁片區和最後一次變更的時間。</span><span class="sxs-lookup"><span data-stu-id="326db-125">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="326db-126">它會在要求時以非同步方式提供 SpatialSurfaceMesh。</span><span class="sxs-lookup"><span data-stu-id="326db-126">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="326db-127">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) 包含用來自訂 SpatialSurfaceInfo 所要求之 SpatialSurfaceMesh 物件的參數。</span><span class="sxs-lookup"><span data-stu-id="326db-127">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="326db-128">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) 代表單一空間介面的網格資料。</span><span class="sxs-lookup"><span data-stu-id="326db-128">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="326db-129">頂點位置、頂點法線和三角形索引的資料會包含在成員 SpatialSurfaceMeshBuffer 物件中。</span><span class="sxs-lookup"><span data-stu-id="326db-129">The data for vertex positions, vertex normals, and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="326db-130">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) 會包裝單一類型的網格資料。</span><span class="sxs-lookup"><span data-stu-id="326db-130">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="326db-131">使用這些 Api 開發應用程式時，您的基本程式流程看起來會像這樣 (如以下所述的範例應用程式所示) ：</span><span class="sxs-lookup"><span data-stu-id="326db-131">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="326db-132">**設定您的 SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="326db-132">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="326db-133">呼叫 [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)，以確定使用者已為您的應用程式指定許可權，以使用裝置的空間對應功能。</span><span class="sxs-lookup"><span data-stu-id="326db-133">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="326db-134">具現化 SpatialSurfaceObserver 物件。</span><span class="sxs-lookup"><span data-stu-id="326db-134">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="326db-135">呼叫 [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) ，以指定您要在其中指定空間介面相關資訊的區域。</span><span class="sxs-lookup"><span data-stu-id="326db-135">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="326db-136">您可以在未來再次呼叫此函式，以修改這些區域。</span><span class="sxs-lookup"><span data-stu-id="326db-136">You may modify these regions in the future by calling this function again.</span></span> <span data-ttu-id="326db-137">每個區域都是使用 [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)來指定。</span><span class="sxs-lookup"><span data-stu-id="326db-137">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="326db-138">註冊 [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) 事件，當您所指定空間區域中的空間表面有新資訊可用時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="326db-138">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you've specified.</span></span>
- <span data-ttu-id="326db-139">**處理 ObservedSurfacesChanged 事件**</span><span class="sxs-lookup"><span data-stu-id="326db-139">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="326db-140">在您的事件處理常式中，呼叫 [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) 以接收 SpatialSurfaceInfo 物件的對應。</span><span class="sxs-lookup"><span data-stu-id="326db-140">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="326db-141">您可以使用此對應，更新 [使用者環境中有](../../design/spatial-mapping.md#mesh-caching)哪些空間表面的記錄。</span><span class="sxs-lookup"><span data-stu-id="326db-141">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](../../design/spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="326db-142">您可以針對每個 SpatialSurfaceInfo 物件來查詢 [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) ，以判斷介面的空間範圍，以您選擇的 [空間座標系統](../../design/coordinate-systems.md) 表示。</span><span class="sxs-lookup"><span data-stu-id="326db-142">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](../../design/coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="326db-143">如果您決定要求、網格空間介面，請呼叫 [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)。</span><span class="sxs-lookup"><span data-stu-id="326db-143">If you decide to request,  mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="326db-144">您可以提供指定三角形密度的選項，以及傳回之網格資料的格式。</span><span class="sxs-lookup"><span data-stu-id="326db-144">You may provide options specifying the density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="326db-145">**接收和處理網格**</span><span class="sxs-lookup"><span data-stu-id="326db-145">**Receive and process mesh**</span></span>
  - <span data-ttu-id="326db-146">每次呼叫 TryComputeLatestMeshAsync 時，都會以非同步方式傳回一個 SpatialSurfaceMesh 物件。</span><span class="sxs-lookup"><span data-stu-id="326db-146">Each call to TryComputeLatestMeshAsync will asynchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="326db-147">您可以從這個物件存取包含的 SpatialSurfaceMeshBuffer 物件，這可讓您存取三角形索引、頂點位置，以及網格的頂點法線（如果您要求的話）。</span><span class="sxs-lookup"><span data-stu-id="326db-147">From this object, you can access the contained SpatialSurfaceMeshBuffer objects, which gives you access to the triangle indices, vertex positions, and vertex normals of the mesh if you request them.</span></span> <span data-ttu-id="326db-148">這項資料的格式會與用來呈現網格的 [Direct3D 11 api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) 直接相容。</span><span class="sxs-lookup"><span data-stu-id="326db-148">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="326db-149">從這裡，您的應用程式可以選擇性地分析或 [處理](../../design/spatial-mapping.md#mesh-processing) 網格資料，並將 [其用於轉譯和物理](../../design/spatial-mapping.md#rendering) [raycasting 和碰撞](../../design/spatial-mapping.md#raycasting-and-collision)。</span><span class="sxs-lookup"><span data-stu-id="326db-149">From here your application can optionally analyze or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data, and use it for [rendering](../../design/spatial-mapping.md#rendering) and physics [raycasting and collision](../../design/spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="326db-150">要注意的一個重要細節是，您必須將刻度套用至網格頂點位置 (例如，用於呈現網格) 的頂點著色器中，以將它們從緩衝區中儲存的優化整數單位轉換成計量。</span><span class="sxs-lookup"><span data-stu-id="326db-150">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they're stored in the buffer, to meters.</span></span> <span data-ttu-id="326db-151">您可以藉由呼叫 [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)來取得此規模。</span><span class="sxs-lookup"><span data-stu-id="326db-151">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="326db-152">疑難排解</span><span class="sxs-lookup"><span data-stu-id="326db-152">Troubleshooting</span></span>
* <span data-ttu-id="326db-153">別忘了使用 SpatialSurfaceMesh 所傳回的小數位數，在頂點著色器中調整網格頂點位置 [。 VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="326db-153">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="326db-154">空間對應程式碼範例逐步解說</span><span class="sxs-lookup"><span data-stu-id="326db-154">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="326db-155">全像 [空間對應](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 程式碼範例包含的程式碼，可讓您開始將 surface 網格載入您的應用程式中，包括用來管理和呈現介面網格的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="326db-155">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="326db-156">現在，我們將逐步解說如何將介面對應功能新增至您的 DirectX 應用程式。</span><span class="sxs-lookup"><span data-stu-id="326db-156">Now, we walk through how to add surface-mapping capability to your DirectX app.</span></span> <span data-ttu-id="326db-157">您可以將此程式碼新增至您的 Windows 全像 [應用程式範本](creating-a-holographic-directx-project.md) 專案，也可以依照上述的程式碼範例流覽。</span><span class="sxs-lookup"><span data-stu-id="326db-157">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="326db-158">這個程式碼範例是以 Windows 全像應用程式範本為基礎。</span><span class="sxs-lookup"><span data-stu-id="326db-158">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="326db-159">設定您的應用程式以使用 >spatialperception 功能</span><span class="sxs-lookup"><span data-stu-id="326db-159">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="326db-160">您的應用程式可以使用空間對應功能。</span><span class="sxs-lookup"><span data-stu-id="326db-160">Your app can use the spatial mapping capability.</span></span> <span data-ttu-id="326db-161">這是必要的，因為空間網格表示使用者的環境，可能會被視為私用資料。</span><span class="sxs-lookup"><span data-stu-id="326db-161">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="326db-162">在您應用程式的 package.appxmanifest 檔案中宣告這項功能。</span><span class="sxs-lookup"><span data-stu-id="326db-162">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="326db-163">以下是範例：</span><span class="sxs-lookup"><span data-stu-id="326db-163">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="326db-164">這項功能來自 **uap2** 命名空間。</span><span class="sxs-lookup"><span data-stu-id="326db-164">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="326db-165">若要在您的資訊清單中取得這個命名空間的存取權，請將它包含在封裝> 專案中的 *xlmns* 屬性 &lt; 。</span><span class="sxs-lookup"><span data-stu-id="326db-165">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="326db-166">以下是範例：</span><span class="sxs-lookup"><span data-stu-id="326db-166">Here's an example:</span></span>

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="326db-167">檢查空間對應功能支援</span><span class="sxs-lookup"><span data-stu-id="326db-167">Check for spatial mapping feature support</span></span>

<span data-ttu-id="326db-168">Windows Mixed Reality 支援各式各樣的裝置，包括不支援空間對應的裝置。</span><span class="sxs-lookup"><span data-stu-id="326db-168">Windows Mixed Reality supports a wide range of devices, including devices, which don't support spatial mapping.</span></span> <span data-ttu-id="326db-169">如果您的應用程式可以使用空間對應，或必須使用空間對應來提供功能，則應該先檢查以確定支援空間對應，然後再嘗試使用它。</span><span class="sxs-lookup"><span data-stu-id="326db-169">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="326db-170">例如，如果您的混合現實應用程式需要空間對應，當使用者嘗試在沒有空間對應的裝置上執行時，它應該會顯示一則訊息。</span><span class="sxs-lookup"><span data-stu-id="326db-170">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="326db-171">或者，您的應用程式可以轉譯自己的虛擬環境來取代使用者的環境，以提供類似空間對應可用時所發生的體驗。</span><span class="sxs-lookup"><span data-stu-id="326db-171">Or, your app can render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="326db-172">在任何事件中，此 API 可讓您的應用程式知道其何時無法取得空間對應資料，並以適當的方式回應。</span><span class="sxs-lookup"><span data-stu-id="326db-172">In any event, this API allows your app to be aware of when it won't get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="326db-173">若要檢查目前的裝置是否支援空間對應，請先確認 UWP 合約位於層級4或更高，然後呼叫 SpatialSurfaceObserver：： IsSupported ( # A1。</span><span class="sxs-lookup"><span data-stu-id="326db-173">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="326db-174">以下是如何在全像 [空間對應](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 程式碼範例的內容中進行這項操作。</span><span class="sxs-lookup"><span data-stu-id="326db-174">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="326db-175">在要求存取之前，只會檢查支援。</span><span class="sxs-lookup"><span data-stu-id="326db-175">Support is checked just before requesting access.</span></span>

<span data-ttu-id="326db-176">從 SDK 15063 版開始，可以使用 SpatialSurfaceObserver：： IsSupported ( # A1 API。</span><span class="sxs-lookup"><span data-stu-id="326db-176">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="326db-177">如有必要，請在使用此 API 之前，將專案的目標重定為平臺15063版。</span><span class="sxs-lookup"><span data-stu-id="326db-177">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

<span data-ttu-id="326db-178">當 UWP 合約小於層級4時，應用程式應該可以繼續執行，就像裝置能夠執行空間對應一樣。</span><span class="sxs-lookup"><span data-stu-id="326db-178">When the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="326db-179">要求存取空間對應資料</span><span class="sxs-lookup"><span data-stu-id="326db-179">Request access to spatial mapping data</span></span>

<span data-ttu-id="326db-180">您的應用程式必須先要求存取空間對應資料的許可權，然後再嘗試建立任何介面觀察者。</span><span class="sxs-lookup"><span data-stu-id="326db-180">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="326db-181">以下是以我們的介面對應程式碼範例為基礎的範例，此頁面稍後會提供更多詳細資料：</span><span class="sxs-lookup"><span data-stu-id="326db-181">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a><span data-ttu-id="326db-182">建立介面觀察者</span><span class="sxs-lookup"><span data-stu-id="326db-182">Create a surface observer</span></span>

<span data-ttu-id="326db-183">**Windows：:P erception：： namespace：：** surface 命名空間包含 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)類別，它會觀察您在 [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)中指定的一或多個磁片區。</span><span class="sxs-lookup"><span data-stu-id="326db-183">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="326db-184">使用 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) 實例即時存取 surface 網格資料。</span><span class="sxs-lookup"><span data-stu-id="326db-184">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="326db-185">從 **AppMain .h**：</span><span class="sxs-lookup"><span data-stu-id="326db-185">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="326db-186">如上一節所述，您必須先要求存取空間對應資料，您的應用程式才能使用它。</span><span class="sxs-lookup"><span data-stu-id="326db-186">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="326db-187">此存取權會在 HoloLens 上自動授與。</span><span class="sxs-lookup"><span data-stu-id="326db-187">This access is granted automatically on the HoloLens.</span></span>

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

<span data-ttu-id="326db-188">接下來，您必須設定介面觀察器，以觀察特定的周框磁片區。</span><span class="sxs-lookup"><span data-stu-id="326db-188">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="326db-189">在這裡，我們觀察到20x20x5 計量的方塊，並以座標系統的原點為中心。</span><span class="sxs-lookup"><span data-stu-id="326db-189">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

<span data-ttu-id="326db-190">您可以改為設定多個周框磁片區。</span><span class="sxs-lookup"><span data-stu-id="326db-190">You can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="326db-191">*這是虛擬程式碼：*</span><span class="sxs-lookup"><span data-stu-id="326db-191">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="326db-192">您也可以使用其他周框圖形（例如，視圖的分隔）或未對齊軸的周框方塊。</span><span class="sxs-lookup"><span data-stu-id="326db-192">It's also possible to use other bounding shapes - such as a view frustum, or a bounding box that isn't axis aligned.</span></span>

<span data-ttu-id="326db-193">*這是虛擬程式碼：*</span><span class="sxs-lookup"><span data-stu-id="326db-193">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="326db-194">如果您的應用程式在表面對應資料無法使用時，需要以不同的方式執行任何動作，您可以撰寫程式碼來回應 [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) 不 **允許** 的情況-例如，因為這些裝置沒有空間對應的硬體，所以不允許在已連接沉浸式裝置的電腦上使用。</span><span class="sxs-lookup"><span data-stu-id="326db-194">If your app needs to do anything differently when surface mapping data isn't available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) isn't **Allowed** - for example, it won't be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="326db-195">針對這些裝置，您應該改為依賴空間階段來取得使用者環境和裝置設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="326db-195">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="326db-196">初始化和更新 surface 網狀集合</span><span class="sxs-lookup"><span data-stu-id="326db-196">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="326db-197">如果已成功建立介面觀察器，我們可以繼續初始化介面網狀集合。</span><span class="sxs-lookup"><span data-stu-id="326db-197">If the surface observer was successfully created, we can continue to initialize our surface mesh collection.</span></span> <span data-ttu-id="326db-198">在這裡，我們會使用提取模型 API 來立即取得目前觀察到的表面集：</span><span class="sxs-lookup"><span data-stu-id="326db-198">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

<span data-ttu-id="326db-199">您也可以使用推播模型來取得介面網格資料。</span><span class="sxs-lookup"><span data-stu-id="326db-199">There's also a push model available to get surface mesh data.</span></span> <span data-ttu-id="326db-200">如果您選擇，您可以自由地設計應用程式來使用提取模型，在這種情況下，您將每隔一段時間（例如，每個畫面次）或在特定期間（例如遊戲設定期間），輪詢一次資料。</span><span class="sxs-lookup"><span data-stu-id="326db-200">You're free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="326db-201">如果是的話，上述程式碼就是您所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="326db-201">If so, the above code is what you need.</span></span>

<span data-ttu-id="326db-202">在我們的程式碼範例中，我們選擇示範這兩種模型的使用方式，以供 pedagogical 之用。</span><span class="sxs-lookup"><span data-stu-id="326db-202">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="326db-203">在此，我們會訂閱事件，以在系統辨識變更時接收最新的介面網格資料。</span><span class="sxs-lookup"><span data-stu-id="326db-203">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="326db-204">我們的程式碼範例也會設定為回應這些事件。</span><span class="sxs-lookup"><span data-stu-id="326db-204">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="326db-205">讓我們逐步解說一下。</span><span class="sxs-lookup"><span data-stu-id="326db-205">Let's walk through how we do this.</span></span>

<span data-ttu-id="326db-206">**注意：** 這可能不是您的應用程式處理網格資料的最有效方式。</span><span class="sxs-lookup"><span data-stu-id="326db-206">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="326db-207">這段程式碼是為了清楚起見而撰寫的，並不會優化。</span><span class="sxs-lookup"><span data-stu-id="326db-207">This code is written for clarity and isn't optimized.</span></span>

<span data-ttu-id="326db-208">介面網格資料會在唯讀對應中提供，此對應會使用[Platform：： guid](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)做為索引鍵值來儲存[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)物件。</span><span class="sxs-lookup"><span data-stu-id="326db-208">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="326db-209">為了處理這項資料，我們先看看不在集合中的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="326db-209">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="326db-210">本主題稍後將會說明如何將資料儲存在我們的範例應用程式中的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="326db-210">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

<span data-ttu-id="326db-211">我們也必須移除 surface 網狀集合中的介面網格，但不在系統集合中。</span><span class="sxs-lookup"><span data-stu-id="326db-211">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="326db-212">若要這樣做，我們必須做一些像是剛才針對新增和更新網格所顯示的相反內容。我們會對應用程式的集合進行迴圈，並檢查是否有系統集合中的 **Guid** 。</span><span class="sxs-lookup"><span data-stu-id="326db-212">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="326db-213">如果它不在系統集合中，我們會將它從我們移除。</span><span class="sxs-lookup"><span data-stu-id="326db-213">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="326db-214">從 AppMain 中的事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="326db-214">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="326db-215">RealtimeSurfaceMeshRenderer .cpp 中的網格剪除執行：</span><span class="sxs-lookup"><span data-stu-id="326db-215">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="326db-216">取得和使用介面網格資料緩衝區</span><span class="sxs-lookup"><span data-stu-id="326db-216">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="326db-217">取得介面網格資訊就像提取資料收集和處理該集合的更新一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="326db-217">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="326db-218">現在，我們將詳細說明您可以如何使用資料。</span><span class="sxs-lookup"><span data-stu-id="326db-218">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="326db-219">在我們的程式碼範例中，我們選擇使用介面網格來呈現。</span><span class="sxs-lookup"><span data-stu-id="326db-219">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="326db-220">這是在真實世界表面上遮蔽全息的常見案例。</span><span class="sxs-lookup"><span data-stu-id="326db-220">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="326db-221">您也可以轉譯網格或轉譯處理過的版本，以在您開始提供應用程式或遊戲功能之前，向使用者顯示要掃描的房間區域。</span><span class="sxs-lookup"><span data-stu-id="326db-221">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="326db-222">程式碼範例會在從上一節所描述的事件處理常式收到 surface 網狀更新時啟動程式。</span><span class="sxs-lookup"><span data-stu-id="326db-222">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="326db-223">此函式中的重要程式程式碼是更新介面 *網格* 的呼叫：這次我們已經處理格線資訊，而我們即將取得頂點和索引資料，以供我們使用。</span><span class="sxs-lookup"><span data-stu-id="326db-223">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we're about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="326db-224">從 RealtimeSurfaceMeshRenderer .cpp：</span><span class="sxs-lookup"><span data-stu-id="326db-224">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

<span data-ttu-id="326db-225">我們的範例程式碼是設計成讓資料類別 **SurfaceMesh** 處理網格資料處理和轉譯。</span><span class="sxs-lookup"><span data-stu-id="326db-225">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="326db-226">這些網格是 **RealtimeSurfaceMeshRenderer** 實際保留的地圖。</span><span class="sxs-lookup"><span data-stu-id="326db-226">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="326db-227">每一個都有其來源 SpatialSurfaceMesh 的參考，因此您可以在需要存取網格頂點或索引緩衝區，或取得網格轉換時使用它。</span><span class="sxs-lookup"><span data-stu-id="326db-227">Each one has a reference to the SpatialSurfaceMesh it came from, so you can use it anytime you need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="326db-228">目前，我們會將網格標示為需要更新。</span><span class="sxs-lookup"><span data-stu-id="326db-228">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="326db-229">從 SurfaceMesh .cpp：</span><span class="sxs-lookup"><span data-stu-id="326db-229">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="326db-230">下次要求網格來繪製本身時，它會先檢查旗標。</span><span class="sxs-lookup"><span data-stu-id="326db-230">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="326db-231">如果需要更新，則會在 GPU 上更新頂點和索引緩衝區。</span><span class="sxs-lookup"><span data-stu-id="326db-231">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

<span data-ttu-id="326db-232">首先，我們會取得原始資料緩衝區：</span><span class="sxs-lookup"><span data-stu-id="326db-232">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="326db-233">然後，我們會使用 HoloLens 提供的網格資料來建立 Direct3D 裝置緩衝區：</span><span class="sxs-lookup"><span data-stu-id="326db-233">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

<span data-ttu-id="326db-234">**注意：** 如需上一個程式碼片段中所使用的 CreateDirectXBuffer helper 函式，請參閱介面對應程式碼範例： SurfaceMesh .cpp、GetDataFromIBuffer .h。</span><span class="sxs-lookup"><span data-stu-id="326db-234">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="326db-235">現在裝置資源建立已完成，並將網格視為已載入並準備好進行更新和轉譯。</span><span class="sxs-lookup"><span data-stu-id="326db-235">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="326db-236">更新和呈現介面網格</span><span class="sxs-lookup"><span data-stu-id="326db-236">Update and render surface meshes</span></span>

<span data-ttu-id="326db-237">我們的 SurfaceMesh 類別具有特製化的 update 函數。</span><span class="sxs-lookup"><span data-stu-id="326db-237">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="326db-238">每個 [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) 都有自己的轉換，而我們的範例會使用目前的座標系統，讓我們的 **SpatialStationaryReferenceFrame** 取得轉換。</span><span class="sxs-lookup"><span data-stu-id="326db-238">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="326db-239">然後，它會更新 GPU 上的模型常數緩衝區。</span><span class="sxs-lookup"><span data-stu-id="326db-239">Then it updates the model constant buffer on the GPU.</span></span>

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

<span data-ttu-id="326db-240">在呈現 surface 網格的時候，我們會在轉譯集合之前執行一些準備工作。</span><span class="sxs-lookup"><span data-stu-id="326db-240">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="326db-241">我們會為目前的轉譯設定設定著色器管線，並設定輸入組合語言階段。</span><span class="sxs-lookup"><span data-stu-id="326db-241">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="326db-242">**CameraResources** 的全像相機協助程式類別，現在已經設定了 view/投射常數緩衝區。</span><span class="sxs-lookup"><span data-stu-id="326db-242">The holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="326db-243">從 **RealtimeSurfaceMeshRenderer：： Render**：</span><span class="sxs-lookup"><span data-stu-id="326db-243">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

<span data-ttu-id="326db-244">完成這項操作之後，我們會在我們的網格上進行迴圈，並告訴每一個都能自行繪製。</span><span class="sxs-lookup"><span data-stu-id="326db-244">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="326db-245">**注意：** 此範例程式碼未經過優化，無法使用任何種類的截量剔除，但您應該在您的應用程式中包含這項功能。</span><span class="sxs-lookup"><span data-stu-id="326db-245">**NOTE:** This sample code isn't optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

<span data-ttu-id="326db-246">個別網格必須負責設定頂點和索引緩衝區、跨距和模型轉換常數緩衝區。</span><span class="sxs-lookup"><span data-stu-id="326db-246">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="326db-247">就像 Windows 全像應用程式範本中的旋轉 cube 一樣，我們會使用實例轉譯為 stereoscopic 緩衝區。</span><span class="sxs-lookup"><span data-stu-id="326db-247">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="326db-248">從 **SurfaceMesh：:D raw**：</span><span class="sxs-lookup"><span data-stu-id="326db-248">From **SurfaceMesh::Draw**:</span></span>

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="326db-249">使用介面對應的呈現選項</span><span class="sxs-lookup"><span data-stu-id="326db-249">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="326db-250">介面對應程式碼範例提供適用于遮蔽的介面網格資料轉譯，以及介面網格資料的螢幕呈現程式碼。</span><span class="sxs-lookup"><span data-stu-id="326db-250">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="326db-251">您選擇的路徑（或兩者）取決於您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="326db-251">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="326db-252">我們將逐步解說這份檔中的這兩個設定。</span><span class="sxs-lookup"><span data-stu-id="326db-252">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="326db-253">**轉譯遮蔽緩衝區以進行全像攝影效果**</span><span class="sxs-lookup"><span data-stu-id="326db-253">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="326db-254">從清除目前虛擬攝影機的呈現目標視圖開始。</span><span class="sxs-lookup"><span data-stu-id="326db-254">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="326db-255">從 AppMain .cpp：</span><span class="sxs-lookup"><span data-stu-id="326db-255">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="326db-256">這是「預先轉譯」階段。</span><span class="sxs-lookup"><span data-stu-id="326db-256">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="326db-257">在這裡，我們會要求網格轉譯器只轉譯深度，藉以建立遮蔽緩衝區。</span><span class="sxs-lookup"><span data-stu-id="326db-257">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="326db-258">在這項設定中，我們不會附加轉譯目標視圖，而網格轉譯器會將圖元著色器階段設定為 **nullptr** ，如此 GPU 就不需要繪製圖元。</span><span class="sxs-lookup"><span data-stu-id="326db-258">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="326db-259">幾何將會被柵格化至深度緩衝區，而圖形管線將會停止。</span><span class="sxs-lookup"><span data-stu-id="326db-259">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

<span data-ttu-id="326db-260">我們可以針對介面對應遮蔽緩衝區，利用額外的深度測試來繪製全像影像。</span><span class="sxs-lookup"><span data-stu-id="326db-260">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="326db-261">在此程式碼範例中，我們會在 cube 的後方呈現不同色彩的圖元。</span><span class="sxs-lookup"><span data-stu-id="326db-261">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="326db-262">從 AppMain .cpp：</span><span class="sxs-lookup"><span data-stu-id="326db-262">From AppMain.cpp:</span></span>

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

<span data-ttu-id="326db-263">根據 SpecialEffectPixelShader 的程式碼 hlsl：</span><span class="sxs-lookup"><span data-stu-id="326db-263">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

<span data-ttu-id="326db-264">**注意：** 針對我們的 **GatherDepthLess** 常式，請參閱介面對應程式碼範例： SpecialEffectPixelShader. hlsl。</span><span class="sxs-lookup"><span data-stu-id="326db-264">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="326db-265">**將介面網格資料呈現給顯示器**</span><span class="sxs-lookup"><span data-stu-id="326db-265">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="326db-266">我們也可以直接將介面網格繪製到身歷聲顯示器緩衝區。</span><span class="sxs-lookup"><span data-stu-id="326db-266">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="326db-267">我們選擇繪製具有光源的完整臉部，但您可以自由繪製框線、在轉譯之前處理網格、套用材質對應等等。</span><span class="sxs-lookup"><span data-stu-id="326db-267">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="326db-268">在此，我們的程式碼範例會告知網狀轉譯器繪製集合。</span><span class="sxs-lookup"><span data-stu-id="326db-268">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="326db-269">這次我們不會指定僅深度傳遞，它會附加圖元著色器，並使用我們為目前虛擬攝影機指定的目標來完成轉譯管線。</span><span class="sxs-lookup"><span data-stu-id="326db-269">This time we don't specify a depth-only pass, it'll attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a><span data-ttu-id="326db-270">另請參閱</span><span class="sxs-lookup"><span data-stu-id="326db-270">See also</span></span>
* [<span data-ttu-id="326db-271">建立全像攝影 DirectX 專案</span><span class="sxs-lookup"><span data-stu-id="326db-271">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="326db-272">Windows 感知空間 API</span><span class="sxs-lookup"><span data-stu-id="326db-272">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
