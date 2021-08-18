---
ms.openlocfilehash: 271116683c94e051f61b78c0db3974ee843afdbd
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905699"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="spatial-awareness-system"></a>空間感知系統

在 MRTK 中，請參閱 [空間感知快速入門](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 指南，以取得設定各種空間網格觀察者的相關資訊。

如需有關裝置上觀察者的詳細資訊，請參閱設定 [適用于裝置的網格觀察](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/configuring-spatial-awareness-mesh-observer) 器指南。

如需場景理解觀察者的詳細資訊，請參閱 [場景理解觀察](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) 者指南。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="armeshmanager"></a>ARMeshManager

Unity 的 ARFoundation 會提供空間網格內建視覺效果的 ARMeshManager 元件。 如需使用方式的詳細資訊，請參閱 [Unity 的檔](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/mesh-manager.html) 。

## <a name="xrmeshsubsystem"></a>XRMeshSubsystem

如果您想要直接使用 Unity 的 [XRMeshSubsystem](https://docs.unity3d.com/ScriptReference/XR.XRMeshSubsystem.html) ，請參閱 [unity 的檔](https://docs.unity3d.com/Manual/xrsdk-meshing.html) ，以取得使用方式的詳細資訊。

## <a name="windows-xr-plugin"></a>WindowsXR 外掛程式

WindowsXR 外掛程式提供一些額外的擴充方法來設定 XRMeshSubsystem，例如設定周框球體或存取基礎平臺網狀標記法。 您可以 [在 Unity 的檔中](https://docs.unity3d.com/Packages/com.unity.xr.windowsmr@5.3/api/UnityEngine.XR.WindowsMR.WindowsMRExtensions.html)找到這些其他擴充功能。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>開始使用 Unity 的內建空間對應元件

Unity 提供兩個元件，可讓您輕鬆地將空間對應新增至您的應用程式、 **空間對應** 轉譯器和 **空間對應碰撞** 器。

### <a name="spatial-mapping-renderer"></a>空間對應轉譯器

空間對應轉譯器可讓空間對應網格的視覺效果。

![Unity 中的空間對應轉譯器](../images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>空間對應碰撞

空間對應碰撞程式可允許全像的內容 (或字元) 互動，例如物理，以及空間對應網格。

![Unity 中的空間對應碰撞](../images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>使用內建空間對應元件

如果您想要將這兩個元件視覺化並與實體介面互動，您可以將這兩個元件新增至您的應用程式。

若要在 Unity 應用程式中使用這兩個元件：

1. 在您想要偵測空間介面網格的區域中央選取 GameObject。
2. 在 [偵測器] 視窗中，**加入元件**  >  **XR**  >  **空間對應碰撞** 器   或 **空間對應** 轉譯器。

您可以在 <a href="https://docs.unity3d.com/2018.4/Documentation/Manual/SpatialMappingComponents.html" target="_blank">Unity 檔網站</a>找到更多有關如何使用這些元件的詳細資料。

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>超越內建空間對應元件

這些元件可讓您輕鬆地開始使用空間對應。 當您想要繼續進行時，有兩個主要的途徑可以探索：

* 若要進行您自己的較低層級網格處理，請參閱下一節有關低層級空間對應腳本 API 的資訊。
* 若要進行較高層級的網狀分析，請參閱下列有關 [MixedRealityToolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/SpatialUnderstanding)中 SpatialUnderstanding 程式庫的章節。

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>使用低層級 Unity 空間對應 API

如果您需要比空間對應轉譯器和空間對應碰撞器元件供應專案更多的控制，請使用低層級空間對應 Api。

**命名空間：** *UnityEngine. XR*<br>
**類型**： *SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*

我們概述了在下列各節中使用空間對應 Api 的應用程式所建議的流程。

### <a name="set-up-the-surfaceobservers"></a>設定 SurfaceObserver (s) 

針對需要空間對應資料的每個應用程式定義區域，將一個 SurfaceObserver 物件具現化。

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

藉由呼叫 SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox 或 SetVolumeAsFrustum，指定每個 SurfaceObserver 物件提供資料的空間區域。 您可以再次呼叫其中一個方法，以重新定義未來的空間區域。

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

當您呼叫 SurfaceObserver () 時，您必須針對空間對應系統具有新資訊的空間 SurfaceObserver 區域中的每個空間介面，提供一個處理常式。 處理常式會收到一個空間介面：

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>處理介面變更

有幾個主要案例要處理：加入和更新，可以使用相同的程式碼路徑，並移除。

* 在新增和更新的案例中，我們會在字典中加入或取得代表這個網格的 GameObject。 我們會使用必要的元件來建立 SurfaceData 結構，然後呼叫 RequestMeshDataAsync 以網格資料填入 GameObject，然後將它放在場景中。
* 在移除的案例中，我們會從字典中移除代表這個網格的 GameObject，並將它終結。

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
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
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

### <a name="handling-data-ready"></a>處理資料就緒

OnDataReady 處理常式會接收 SurfaceData 物件。 WorldAnchor、MeshFilter 和 (選擇性地) 它所包含的 MeshCollider 物件會反映相關聯空間介面的最新狀態。 （選擇性）藉由存取 MeshFilter 物件的網狀成員來分析及/或 [處理](../../../design/spatial-mapping.md#mesh-processing) 網格資料。 使用最新的網格轉譯空間介面，並 (選擇性地) 將它用於物理衝突和 raycasts。 請務必確認 SurfaceData 的內容不是 null。

### <a name="start-processing-on-updates"></a>開始處理更新

SurfaceObserver 應該在延遲而不是每個畫面上呼叫更新 () 。

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while (true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```
