---
title: UsingGuide
description: 描述可透過程式設計方式設定空間感知系統的主要機制和 Api
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 89a345f43a5133b8a99cabab1abc15a6e8770a4d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689718"
---
# <a name="configuring-mesh-observers-via-code"></a><span data-ttu-id="99ea0-104">透過程式碼設定網格觀察者</span><span class="sxs-lookup"><span data-stu-id="99ea0-104">Configuring mesh observers via code</span></span>

<span data-ttu-id="99ea0-105">本文將討論一些主要機制和 Api，以程式設計方式設定 [空間感知系統](SpatialAwarenessGettingStarted.md) 和相關的 *網格觀察* 者資料提供者。</span><span class="sxs-lookup"><span data-stu-id="99ea0-105">This article will discuss some of the key mechanisms and APIs to programmatically configure the [Spatial Awareness system](SpatialAwarenessGettingStarted.md) and related *Mesh Observer* data providers.</span></span>

## <a name="accessing-mesh-observers"></a><span data-ttu-id="99ea0-106">存取網格觀察者</span><span class="sxs-lookup"><span data-stu-id="99ea0-106">Accessing mesh observers</span></span>

<span data-ttu-id="99ea0-107">執行介面的網格觀察者類別 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 可提供平臺特定的網格資料給空間感知系統。</span><span class="sxs-lookup"><span data-stu-id="99ea0-107">Mesh Observer classes that implement the [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) interface provide platform-specific mesh data to the Spatial Awareness system.</span></span> <span data-ttu-id="99ea0-108">空間感知設定檔中可以設定多個觀察者。</span><span class="sxs-lookup"><span data-stu-id="99ea0-108">Multiple Observers can be configured in the Spatial Awareness profile.</span></span>

<span data-ttu-id="99ea0-109">存取空間感知系統的資料提供者，與其他任何混合現實工具組服務的存取方式大多相同。</span><span class="sxs-lookup"><span data-stu-id="99ea0-109">Accessing the data providers of the Spatial Awareness system is mostly the same as for any other Mixed Reality Toolkit service.</span></span> <span data-ttu-id="99ea0-110">空間感知服務必須轉換至 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 介面，才能透過 `GetDataProvider<T>` api 存取，然後在執行時間使用這些 api 直接存取網格觀察者物件。</span><span class="sxs-lookup"><span data-stu-id="99ea0-110">The Spatial Awareness service must be casted to the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface to access via the `GetDataProvider<T>` APIs, which can then be utilized to access the Mesh Observer objects directly at runtime.</span></span>

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

<span data-ttu-id="99ea0-111">`CoreServices.GetSpatialAwarenessSystemDataProvider<T>()`Helper 可簡化此存取模式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="99ea0-111">The `CoreServices.GetSpatialAwarenessSystemDataProvider<T>()` helper simplifies this access pattern as demonstrated below.</span></span>

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a><span data-ttu-id="99ea0-112">啟動和停止網格觀察</span><span class="sxs-lookup"><span data-stu-id="99ea0-112">Starting and stopping mesh observation</span></span>

<span data-ttu-id="99ea0-113">處理空間感知系統時最常見的工作之一，就是在執行時間動態地關閉/開啟此功能。</span><span class="sxs-lookup"><span data-stu-id="99ea0-113">One of the most common tasks when dealing with the Spatial Awareness system is turning the feature off/on dynamically at runtime.</span></span> <span data-ttu-id="99ea0-114">這會透過和 api 針對每個觀察者完成 [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) 。</span><span class="sxs-lookup"><span data-stu-id="99ea0-114">This is done per Observer via the [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) and [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) APIs.</span></span>

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

<span data-ttu-id="99ea0-115">這段程式碼功能也可以透過空間感知系統直接存取來簡化。</span><span class="sxs-lookup"><span data-stu-id="99ea0-115">This code functionality can also be simplified via access through the Spatial Awareness system directly.</span></span>

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a><span data-ttu-id="99ea0-116">啟動和停止所有網格觀察</span><span class="sxs-lookup"><span data-stu-id="99ea0-116">Starting and stopping all mesh observation</span></span>

<span data-ttu-id="99ea0-117">在應用程式中啟動/停止所有網格觀察通常很方便。</span><span class="sxs-lookup"><span data-stu-id="99ea0-117">It is generally convenient to start/stop all mesh observation in the application.</span></span> <span data-ttu-id="99ea0-118">這可以透過實用的空間感知系統 Api 和來達成 [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) 。</span><span class="sxs-lookup"><span data-stu-id="99ea0-118">This can be achieved through the helpful Spatial Awareness system APIs, [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) and [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers).</span></span>

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a><span data-ttu-id="99ea0-119">列舉和存取網格</span><span class="sxs-lookup"><span data-stu-id="99ea0-119">Enumerating and accessing the meshes</span></span>

<span data-ttu-id="99ea0-120">存取網格可以針對每個觀察者完成，然後透過 API 來列舉該網格觀察者已知的網格 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 。</span><span class="sxs-lookup"><span data-stu-id="99ea0-120">Accessing the meshes can be done per Observer and then enumerating through the meshes known to that Mesh Observer via the [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) API.</span></span>

<span data-ttu-id="99ea0-121">如果是在編輯器中執行，則可以使用將 [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) `Mesh` 物件儲存至資產檔案。</span><span class="sxs-lookup"><span data-stu-id="99ea0-121">If running in editor, one can use the [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) to save the `Mesh` object to an asset file.</span></span>

<span data-ttu-id="99ea0-122">如果在裝置上執行，有許多可用的社區和存放外掛程式可將 `MeshFilter` 資料序列化為模型檔案類型 ([OBJ 範例](http://wiki.unity3d.com/index.php/ObjExporter)) 。</span><span class="sxs-lookup"><span data-stu-id="99ea0-122">If running on device, there are many community and store plugins available to serialize the `MeshFilter` data into a model file type([OBJ Example](http://wiki.unity3d.com/index.php/ObjExporter)).</span></span>

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Loop through all known Meshes
foreach (SpatialAwarenessMeshObject meshObject in observer.Meshes.Values)
{
    Mesh mesh = meshObject.Filter.mesh;
    // Do something with the Mesh object
}
```

## <a name="showing-and-hiding-the-spatial-mesh"></a><span data-ttu-id="99ea0-123">顯示和隱藏空間網格</span><span class="sxs-lookup"><span data-stu-id="99ea0-123">Showing and hiding the spatial mesh</span></span>

<span data-ttu-id="99ea0-124">您可以使用下列範例程式碼，以程式設計方式隱藏/顯示網格：</span><span class="sxs-lookup"><span data-stu-id="99ea0-124">It's possible to programmatically hide/show meshes using the sample code below:</span></span>

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a><span data-ttu-id="99ea0-125">註冊網格觀察事件</span><span class="sxs-lookup"><span data-stu-id="99ea0-125">Registering for mesh observation events</span></span>

<span data-ttu-id="99ea0-126">元件可以執行 `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` ，然後向空間感知系統註冊以接收網狀觀察事件。</span><span class="sxs-lookup"><span data-stu-id="99ea0-126">Components can implement the `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` and then register with the Spatial Awareness system to receive Mesh Observation events.</span></span>

<span data-ttu-id="99ea0-127">`DemoSpatialMeshHandler` (資產/MRTK/範例/示範/SpatialAwareness/腳本) 腳本是接聽網格觀察者事件的實用範例和起點。</span><span class="sxs-lookup"><span data-stu-id="99ea0-127">The `DemoSpatialMeshHandler` (Assets/MRTK/Examples/Demos/SpatialAwareness/Scripts) script is a useful example and starting point for listening to Mesh Observer events.</span></span>

<span data-ttu-id="99ea0-128">這是 *DemoSpatialMeshHandler* 腳本和網格觀察事件接聽的簡化範例。</span><span class="sxs-lookup"><span data-stu-id="99ea0-128">This is a simplified example of *DemoSpatialMeshHandler* script and Mesh Observation event listening.</span></span>

```c#
// Simplify type
using SpatialAwarenessHandler = IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>;

public class MyMeshObservationExample : MonoBehaviour, SpatialAwarenessHandler
{
    private void OnEnable()
    {
        // Register component to listen for Mesh Observation events, typically done in OnEnable()
        CoreServices.SpatialAwarenessSystem.RegisterHandler<SpatialAwarenessHandler>(this);
    }

    private void OnDisable()
    {
        // Unregister component from Mesh Observation events, typically done in OnDisable()
        CoreServices.SpatialAwarenessSystem.UnregisterHandler<SpatialAwarenessHandler>(this);
    }

    public virtual void OnObservationAdded(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationUpdated(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationRemoved(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }
}
```

## <a name="see-also"></a><span data-ttu-id="99ea0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99ea0-129">See also</span></span>

- [<span data-ttu-id="99ea0-130">空間感知開始使用</span><span class="sxs-lookup"><span data-stu-id="99ea0-130">Spatial Awareness Getting Started</span></span>](SpatialAwarenessGettingStarted.md)
- [<span data-ttu-id="99ea0-131">設定空間感知網格觀察者</span><span class="sxs-lookup"><span data-stu-id="99ea0-131">Configuring the Spatial Awareness Mesh Observer</span></span>](ConfiguringSpatialAwarenessMeshObserver.md)
- [<span data-ttu-id="99ea0-132">空間感知 API 檔</span><span class="sxs-lookup"><span data-stu-id="99ea0-132">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
