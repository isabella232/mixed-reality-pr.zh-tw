---
title: DirectX 中的空間對應
description: 瞭解如何在您的 DirectX 應用程式中執行空間對應，以及如何在通用 Windows 平臺 SDK 中使用空間對應範例應用程式。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows mixed reality、空間對應、環境、互動、directx、winrt、api、範例程式碼、UWP、SDK、逐步解說
ms.openlocfilehash: bcd78487e96aaf09707aa4bf58917223cc2e8583
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006708"
---
# <a name="spatial-mapping-in-directx"></a>DirectX 中的空間對應

> [!NOTE]
> 本文與舊版 WinRT 原生 Api 相關。  針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)**。

本主題說明如何在 DirectX 應用程式中執行 [空間對應](../../design/spatial-mapping.md) ，包括使用通用 Windows 平臺 SDK 封裝的空間對應範例應用程式的詳細說明。

本主題使用 [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 程式碼範例中的程式碼。

>[!NOTE]
>本文中的程式碼片段目前示範如何使用 c + + [/cx，而](creating-a-holographic-directx-project.md)不是 c + + 全像 c + + 全像 c + + 的 + 17 相容 c + +/WinRT。  這些概念對 c + +/WinRT 專案而言是相等的，不過您必須轉譯程式碼。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>空間對應</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>DirectX 開發概觀

空間對應的原生應用程式開發會使用 [Windows](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) 中的 api。空間命名空間。 這些 Api 可讓您完全掌控空間對應功能，與 [Unity](../unity/spatial-mapping-in-unity.md)公開空間對應 api 的方式相同。

### <a name="perception-apis"></a>認知 Api

針對空間對應開發提供的主要類型如下所示：
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) 會以 SpatialSurfaceInfo 物件的形式，提供使用者附近空間的應用程式指定區域相關資訊。
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) 描述單一現存空間介面，包括唯一識別碼、周框磁片區和最後一次變更的時間。 它會在要求時以非同步方式提供 SpatialSurfaceMesh。
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) 包含用來自訂 SpatialSurfaceInfo 所要求之 SpatialSurfaceMesh 物件的參數。
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) 代表單一空間介面的網格資料。 頂點位置、頂點法線和三角形索引的資料會包含在成員 SpatialSurfaceMeshBuffer 物件中。
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) 會包裝單一類型的網格資料。

使用這些 Api 開發應用程式時，您的基本程式流程看起來會像這樣 (如以下所述的範例應用程式所示) ：
- **設定您的 SpatialSurfaceObserver**
  - 呼叫 [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)，以確定使用者已為您的應用程式指定許可權，以使用裝置的空間對應功能。
  - 具現化 SpatialSurfaceObserver 物件。
  - 呼叫 [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) ，以指定您要在其中指定空間介面相關資訊的區域。 您可以在未來再次呼叫此函式，以修改這些區域。 每個區域都是使用 [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)來指定。
  - 註冊 [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) 事件，當您所指定空間區域中的空間表面有新資訊可用時，就會引發此事件。
- **處理 ObservedSurfacesChanged 事件**
  - 在您的事件處理常式中，呼叫 [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) 以接收 SpatialSurfaceInfo 物件的對應。 您可以使用此對應，更新 [使用者環境中有](../../design/spatial-mapping.md#mesh-caching)哪些空間表面的記錄。
  - 您可以針對每個 SpatialSurfaceInfo 物件來查詢 [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) ，以判斷介面的空間範圍，以您選擇的 [空間座標系統](../../design/coordinate-systems.md) 表示。
  - 如果您決定要求、網格空間介面，請呼叫 [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)。 您可以提供指定三角形密度的選項，以及傳回之網格資料的格式。
- **接收和處理網格**
  - 每次呼叫 TryComputeLatestMeshAsync 時，都會以非同步方式傳回一個 SpatialSurfaceMesh 物件。
  - 您可以從這個物件存取包含的 SpatialSurfaceMeshBuffer 物件，這可讓您存取三角形索引、頂點位置，以及網格的頂點法線（如果您要求的話）。 這項資料的格式會與用來呈現網格的 [Direct3D 11 api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) 直接相容。
  - 從這裡，您的應用程式可以選擇性地分析或 [處理](../../design/spatial-mapping.md#mesh-processing) 網格資料，並將 [其用於轉譯和物理](../../design/spatial-mapping.md#rendering) [raycasting 和碰撞](../../design/spatial-mapping.md#raycasting-and-collision)。
  - 要注意的一個重要細節是，您必須將刻度套用至網格頂點位置 (例如，用於呈現網格) 的頂點著色器中，以將它們從緩衝區中儲存的優化整數單位轉換成計量。 您可以藉由呼叫 [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)來取得此規模。

### <a name="troubleshooting"></a>疑難排解
* 別忘了使用 SpatialSurfaceMesh 所傳回的小數位數，在頂點著色器中調整網格頂點位置 [。 VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>空間對應程式碼範例逐步解說

全像 [空間對應](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 程式碼範例包含的程式碼，可讓您開始將 surface 網格載入您的應用程式中，包括用來管理和呈現介面網格的基礎結構。

現在，我們將逐步解說如何將介面對應功能新增至您的 DirectX 應用程式。 您可以將此程式碼新增至您的 Windows 全像 [應用程式範本](creating-a-holographic-directx-project.md) 專案，也可以依照上述的程式碼範例流覽。 這個程式碼範例是以 Windows 全像應用程式範本為基礎。

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>設定您的應用程式以使用 >spatialperception 功能

您的應用程式可以使用空間對應功能。 這是必要的，因為空間網格表示使用者的環境，可能會被視為私用資料。 在您應用程式的 package.appxmanifest 檔案中宣告這項功能。 以下為範例：

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

這項功能來自 **uap2** 命名空間。 若要在您的資訊清單中取得這個命名空間的存取權，請將它包含在封裝> 專案中的 *xlmns* 屬性 &lt; 。 以下為範例：

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>檢查空間對應功能支援

Windows Mixed Reality 支援各式各樣的裝置，包括不支援空間對應的裝置。 如果您的應用程式可以使用空間對應，或必須使用空間對應來提供功能，則應該先檢查以確定支援空間對應，然後再嘗試使用它。 例如，如果您的混合現實應用程式需要空間對應，當使用者嘗試在沒有空間對應的裝置上執行時，它應該會顯示一則訊息。 或者，您的應用程式可以轉譯自己的虛擬環境來取代使用者的環境，以提供類似空間對應可用時所發生的體驗。 在任何事件中，此 API 可讓您的應用程式知道其何時無法取得空間對應資料，並以適當的方式回應。

若要檢查目前的裝置是否支援空間對應，請先確認 UWP 合約位於層級4或更高，然後呼叫 SpatialSurfaceObserver：： IsSupported ( # A1。 以下是如何在全像 [空間對應](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 程式碼範例的內容中進行這項操作。 在要求存取之前，只會檢查支援。

從 SDK 15063 版開始，可以使用 SpatialSurfaceObserver：： IsSupported ( # A1 API。 如有必要，請在使用此 API 之前，將專案的目標重定為平臺15063版。

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

當 UWP 合約小於層級4時，應用程式應該可以繼續執行，就像裝置能夠執行空間對應一樣。

### <a name="request-access-to-spatial-mapping-data"></a>要求存取空間對應資料

您的應用程式必須先要求存取空間對應資料的許可權，然後再嘗試建立任何介面觀察者。 以下是以我們的介面對應程式碼範例為基礎的範例，此頁面稍後會提供更多詳細資料：

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

### <a name="create-a-surface-observer"></a>建立介面觀察者

**Windows：:P erception：： namespace：：** surface 命名空間包含 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)類別，它會觀察您在 [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)中指定的一或多個磁片區。 使用 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) 實例即時存取 surface 網格資料。

從 **AppMain .h**：

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

如上一節所述，您必須先要求存取空間對應資料，您的應用程式才能使用它。 此存取權會在 HoloLens 上自動授與。

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

接下來，您必須設定介面觀察器，以觀察特定的周框磁片區。 在這裡，我們觀察到20x20x5 計量的方塊，並以座標系統的原點為中心。

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

您可以改為設定多個周框磁片區。

*這是虛擬程式碼：*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

您也可以使用其他周框圖形（例如，視圖的分隔）或未對齊軸的周框方塊。

*這是虛擬程式碼：*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

如果您的應用程式在表面對應資料無法使用時，需要以不同的方式執行任何動作，您可以撰寫程式碼來回應 [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) 不 **允許** 的情況-例如，因為這些裝置沒有空間對應的硬體，所以不允許在已連接沉浸式裝置的電腦上使用。 針對這些裝置，您應該改為依賴空間階段來取得使用者環境和裝置設定的相關資訊。

### <a name="initialize-and-update-the-surface-mesh-collection"></a>初始化和更新 surface 網狀集合

如果已成功建立介面觀察器，我們可以繼續初始化介面網狀集合。 在這裡，我們會使用提取模型 API 來立即取得目前觀察到的表面集：

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

您也可以使用推播模型來取得介面網格資料。 如果您選擇，您可以自由地設計應用程式來使用提取模型，在這種情況下，您將每隔一段時間（例如，每個畫面次）或在特定期間（例如遊戲設定期間），輪詢一次資料。 如果是的話，上述程式碼就是您所需的程式碼。

在我們的程式碼範例中，我們選擇示範這兩種模型的使用方式，以供 pedagogical 之用。 在此，我們會訂閱事件，以在系統辨識變更時接收最新的介面網格資料。

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

我們的程式碼範例也會設定為回應這些事件。 讓我們逐步解說一下。

**注意：** 這可能不是您的應用程式處理網格資料的最有效方式。 這段程式碼是為了清楚起見而撰寫的，並不會優化。

介面網格資料會在唯讀對應中提供，此對應會使用[Platform：： guid](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)做為索引鍵值來儲存[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)物件。

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

為了處理這項資料，我們先看看不在集合中的索引鍵值。 本主題稍後將會說明如何將資料儲存在我們的範例應用程式中的詳細資料。

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

我們也必須移除 surface 網狀集合中的介面網格，但不在系統集合中。 若要這樣做，我們必須做一些像是剛才針對新增和更新網格所顯示的相反內容。我們會對應用程式的集合進行迴圈，並檢查是否有系統集合中的 **Guid** 。 如果它不在系統集合中，我們會將它從我們移除。

從 AppMain 中的事件處理常式：

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

RealtimeSurfaceMeshRenderer .cpp 中的網格剪除執行：

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>取得和使用介面網格資料緩衝區

取得介面網格資訊就像提取資料收集和處理該集合的更新一樣簡單。 現在，我們將詳細說明您可以如何使用資料。

在我們的程式碼範例中，我們選擇使用介面網格來呈現。 這是在真實世界表面上遮蔽全息的常見案例。 您也可以轉譯網格或轉譯處理過的版本，以在您開始提供應用程式或遊戲功能之前，向使用者顯示要掃描的房間區域。

程式碼範例會在從上一節所描述的事件處理常式收到 surface 網狀更新時啟動程式。 此函式中的重要程式程式碼是更新介面 *網格* 的呼叫：這次我們已經處理格線資訊，而我們即將取得頂點和索引資料，以供我們使用。

從 RealtimeSurfaceMeshRenderer .cpp：

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

我們的範例程式碼是設計成讓資料類別 **SurfaceMesh** 處理網格資料處理和轉譯。 這些網格是 **RealtimeSurfaceMeshRenderer** 實際保留的地圖。 每一個都有其來源 SpatialSurfaceMesh 的參考，因此您可以在需要存取網格頂點或索引緩衝區，或取得網格轉換時使用它。 目前，我們會將網格標示為需要更新。

從 SurfaceMesh .cpp：

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

下次要求網格來繪製本身時，它會先檢查旗標。 如果需要更新，則會在 GPU 上更新頂點和索引緩衝區。

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

首先，我們會取得原始資料緩衝區：

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

然後，我們會使用 HoloLens 提供的網格資料來建立 Direct3D 裝置緩衝區：

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

**注意：** 如需上一個程式碼片段中所使用的 CreateDirectXBuffer helper 函式，請參閱介面對應程式碼範例： SurfaceMesh .cpp、GetDataFromIBuffer .h。 現在裝置資源建立已完成，並將網格視為已載入並準備好進行更新和轉譯。

### <a name="update-and-render-surface-meshes"></a>更新和呈現介面網格

我們的 SurfaceMesh 類別具有特製化的 update 函數。 每個 [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) 都有自己的轉換，而我們的範例會使用目前的座標系統，讓我們的 **SpatialStationaryReferenceFrame** 取得轉換。 然後，它會更新 GPU 上的模型常數緩衝區。

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

在呈現 surface 網格的時候，我們會在轉譯集合之前執行一些準備工作。 我們會為目前的轉譯設定設定著色器管線，並設定輸入組合語言階段。 **CameraResources** 的全像相機協助程式類別，現在已經設定了 view/投射常數緩衝區。

從 **RealtimeSurfaceMeshRenderer：： Render**：

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

完成這項操作之後，我們會在我們的網格上進行迴圈，並告訴每一個都能自行繪製。 **注意：** 此範例程式碼未經過優化，無法使用任何種類的截量剔除，但您應該在您的應用程式中包含這項功能。

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

個別網格必須負責設定頂點和索引緩衝區、跨距和模型轉換常數緩衝區。 就像 Windows 全像應用程式範本中的旋轉 cube 一樣，我們會使用實例轉譯為 stereoscopic 緩衝區。

從 **SurfaceMesh：:D raw**：

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

### <a name="rendering-choices-with-surface-mapping"></a>使用介面對應的呈現選項

介面對應程式碼範例提供適用于遮蔽的介面網格資料轉譯，以及介面網格資料的螢幕呈現程式碼。 您選擇的路徑（或兩者）取決於您的應用程式。 我們將逐步解說這份檔中的這兩個設定。

**轉譯遮蔽緩衝區以進行全像攝影效果**

從清除目前虛擬攝影機的呈現目標視圖開始。

從 AppMain .cpp：

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

這是「預先轉譯」階段。 在這裡，我們會要求網格轉譯器只轉譯深度，藉以建立遮蔽緩衝區。 在這項設定中，我們不會附加轉譯目標視圖，而網格轉譯器會將圖元著色器階段設定為 **nullptr** ，如此 GPU 就不需要繪製圖元。 幾何將會被柵格化至深度緩衝區，而圖形管線將會停止。

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

我們可以針對介面對應遮蔽緩衝區，利用額外的深度測試來繪製全像影像。 在此程式碼範例中，我們會在 cube 的後方呈現不同色彩的圖元。

從 AppMain .cpp：

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

根據 SpecialEffectPixelShader 的程式碼 hlsl：

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

**注意：** 針對我們的 **GatherDepthLess** 常式，請參閱介面對應程式碼範例： SpecialEffectPixelShader. hlsl。

**將介面網格資料呈現給顯示器**

我們也可以直接將介面網格繪製到身歷聲顯示器緩衝區。 我們選擇繪製具有光源的完整臉部，但您可以自由繪製框線、在轉譯之前處理網格、套用材質對應等等。

在此，我們的程式碼範例會告知網狀轉譯器繪製集合。 這次我們不會指定僅深度傳遞，它會附加圖元著色器，並使用我們為目前虛擬攝影機指定的目標來完成轉譯管線。

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

## <a name="see-also"></a>請參閱
* [建立全像攝影 DirectX 專案](creating-a-holographic-directx-project.md)
* [Windows 感知空間 API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
