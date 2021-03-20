---
title: UsingGuide
description: 描述可透過程式設計方式設定空間感知系統的主要機制和 Api
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: f1fd6620934c3936aa596eda52bab300a84a1acb
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104696075"
---
# <a name="configuring-mesh-observers-via-code"></a>透過程式碼設定網格觀察者

本文將討論一些主要機制和 Api，以程式設計方式設定 [空間感知系統](spatial-awareness-getting-started.md) 和相關的 *網格觀察* 者資料提供者。

## <a name="accessing-mesh-observers"></a>存取網格觀察者

執行介面的網格觀察者類別 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 可提供平臺特定的網格資料給空間感知系統。 空間感知設定檔中可以設定多個觀察者。

存取空間感知系統的資料提供者，與其他任何混合現實工具組服務的存取方式大多相同。 空間感知服務必須轉換至 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 介面，才能透過 `GetDataProvider<T>` api 存取，然後在執行時間使用這些 api 直接存取網格觀察者物件。

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

`CoreServices.GetSpatialAwarenessSystemDataProvider<T>()`Helper 可簡化此存取模式，如下所示。

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>啟動和停止網格觀察

處理空間感知系統時最常見的工作之一，就是在執行時間動態地關閉/開啟此功能。 這會透過和 api 針對每個觀察者完成 [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) 。

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

這段程式碼功能也可以透過空間感知系統直接存取來簡化。

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>啟動和停止所有網格觀察

在應用程式中啟動/停止所有網格觀察通常很方便。 這可以透過實用的空間感知系統 Api 和來達成 [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) 。

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>列舉和存取網格

存取網格可以針對每個觀察者完成，然後透過 API 來列舉該網格觀察者已知的網格 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 。

如果是在編輯器中執行，則可以使用將 [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) `Mesh` 物件儲存至資產檔案。

如果在裝置上執行，有許多可用的社區和存放外掛程式可將 `MeshFilter` 資料序列化為模型檔案類型 ([OBJ 範例](http://wiki.unity3d.com/index.php/ObjExporter)) 。

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

## <a name="showing-and-hiding-the-spatial-mesh"></a>顯示和隱藏空間網格

您可以使用下列範例程式碼，以程式設計方式隱藏/顯示網格：

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>註冊網格觀察事件

元件可以執行 `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` ，然後向空間感知系統註冊以接收網狀觀察事件。

`DemoSpatialMeshHandler` (資產/MRTK/範例/示範/SpatialAwareness/腳本) 腳本是接聽網格觀察者事件的實用範例和起點。

這是 *DemoSpatialMeshHandler* 腳本和網格觀察事件接聽的簡化範例。

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

## <a name="see-also"></a>另請參閱

- [空間感知開始使用](spatial-awareness-getting-started.md)
- [設定空間感知網格觀察者](configuring-spatial-awareness-mesh-observer.md)
- [空間感知 API 檔](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
