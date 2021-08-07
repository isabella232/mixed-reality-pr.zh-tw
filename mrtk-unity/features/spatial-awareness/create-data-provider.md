---
title: 建立空間感知 Data Provider
description: 描述如何在 MRTK 中建立自訂資料提供者
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 05186c418a7b0b7b143abc58be6a6afb64cb69f5a1c90c73ed516d51c2a5d8ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188846"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a>建立空間感知系統資料提供者

空間感知系統是可延伸的系統，可為應用程式提供真實世界環境的相關資料。 若要加入新硬體平臺或新形式空間感知資料的支援，可能需要自訂資料提供者。

本文說明如何建立空間感知系統的 [自訂資料提供者](../../architecture/systems-extensions-providers.md)（也稱為空間觀察者）。 此處所示的範例程式碼是來自 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 類別執行，這 [對在編輯器中載入3d 網格資料很有用](spatial-object-mesh-observer.md)。

> [!NOTE]
> 此範例中使用的完整原始程式碼可以在資料夾中找到 `Assets/MRTK/Providers/ObjectMeshObserver` 。

## <a name="namespace-and-folder-structure"></a>命名空間和資料夾結構

資料提供者可透過下列其中一種方式散發：

1. 協力廠商附加元件
1. Microsoft Mixed Reality 工具組的一部分

將新資料提供者提交給 MRTK 的核准程式將依案例而有所不同，並會在初始提案時傳達。 您可以藉由建立新的 [*功能要求* 類型問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)來提交提案。

### <a name="third-party-add-on"></a>協力廠商附加元件

**Namespace**

資料提供者必須具有命名空間，才能減少潛在的名稱衝突。 建議命名空間包含下列元件。

- 產生附加元件的公司名稱
- 功能區域

例如，Contoso 公司所建立和出貨的空間感知資料提供者可能是 *"MixedReality. SpatialAwareness"*。

**資料夾結構**

建議在資料夾階層中應資料提供者的原始程式碼，如下圖所示。

![範例資料夾結構](../images/spatial-awareness/ExampleProviderFolderStructure.png)

其中 *ContosoSpatialAwareness* 資料夾包含資料提供者的執行、 *編輯器* 資料夾包含偵測器 (以及任何其他 Unity 編輯器的特定程式碼) ，而 *設定檔* 資料夾包含一或多個預先製作的設定檔可編寫腳本的物件。

### <a name="mrtk-submission"></a>MRTK 提交

**Namespace**

如果空間感知系統資料提供者提交至 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組存放庫，則命名空間 **必須** 以 (MixedReality 的開頭，例如： *MixedReality. SpatialObjectMeshObserver*) 

 程式碼應該位於 MRTK/Providers 底下的資料夾中， (例如： *MRTK/providers/ObjectMeshObserver*) 。

**資料夾結構**

所有程式碼都應該位於 MRTK/Provider 下的資料夾中， (例如： MRTK/Providers/ObjectMeshObserver) 。

## <a name="define-the-spatial-data-object"></a>定義空間資料物件

建立空間感知資料提供者的第一個步驟，是決定資料的類型 (例如：網格或平面，) 它會提供給應用程式。

所有空間資料物件都必須執行 [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) 介面。

Mixed Reality 工具組 foundation 提供下列空間物件，可在新的資料提供者中使用或擴充。

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>執行資料提供者

### <a name="specify-interface-andor-base-class-inheritance"></a>指定介面和/或基類繼承

所有空間感知資料提供者都必須執行 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 介面，以指定空間感知系統所需的最小功能。 MRTK foundation 包含 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 可提供此必要功能之預設執行的類別。

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)類別會使用介面 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 來表示它提供 SpatialAwarenessMesh 功能的支援。

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>套用 MixedRealityDataProvider 屬性

建立空間感知資料提供者的關鍵步驟是將 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 屬性套用至類別。 此步驟可讓您為數據提供者設定預設設定檔和平臺 (s) ，並在空間感知設定檔中選取，以及名稱、資料夾路徑等。

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>執行 IMixedRealityDataProvider 方法

一旦定義了類別之後，下一個步驟就是提供介面的實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。

> [!NOTE]
> 透過 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 類別的類別 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) ，只會為方法提供空白的實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。 這些方法的詳細資料通常是資料提供者特有的。

由資料提供者所執行的方法如下：

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>執行資料提供者邏輯

下一步是藉由執行特定的資料提供者介面，來新增資料提供者的邏輯 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 。 這部分的資料提供者通常會是平臺特定。

### <a name="observation-change-notifications"></a>觀察變更通知

為了讓應用程式能夠回應裝置對環境的瞭解變更，此資料提供者會依照介面中的定義來引發通知事件 [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) 。

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 範例中的下列程式碼 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 會示範在新增網格資料時引發和事件。

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) `OnObservationUpdated` 因為3d 模型只會載入一次，所以類別不會引發事件。 類別中的實作為 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) `OnObservationUpdated` 針對觀察到的網格引發事件的範例。

### <a name="add-unity-profiler-instrumentation"></a>新增 Unity Profiler 檢測

效能在混合現實應用程式中是很重要的。 每個元件都會增加應用程式必須考慮的額外負荷。 至此，所有空間感知資料提供者都必須在內部迴圈中包含 Unity Profiler 檢測，以及經常使用的程式碼路徑。

建議您在檢測自訂提供者時，執行 MRTK 所使用的模式。

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> 用來識別 profiler 標記的名稱是任意的。 MRTK 會使用下列模式。
>
> "[product] className. 方法名稱-選擇性附注"
>
> 建議自訂資料提供者遵循類似的模式，以協助簡化分析追蹤時特定元件和方法的識別。

## <a name="create-the-profile-and-inspector"></a>建立設定檔和偵測器

在混合現實工具組中，資料提供者會使用 [設定檔](../profiles/profiles.md)進行設定。

### <a name="define-the-profile"></a>定義設定檔

設定檔內容應該鏡像資料提供者的可存取屬性 (例如：更新間隔) 。 在每個介面中定義的所有使用者可設定屬性都應該包含在設定檔中。

如果新的資料提供者延伸了現有的提供者，則建議使用基類。 例如，會 [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) 擴充， [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) 讓客戶能夠提供要當做環境資料使用的3d 模型。

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

`CreateAssetMenu`屬性可以套用至設定檔類別，讓客戶能夠使用 [**建立**  >  **資產**  >  **混合現實工具** 組  >  **設定檔**] 功能表建立設定檔實例。

### <a name="implement-the-inspector"></a>執行偵測器

設定檔偵測器是用來設定和查看設定檔內容的使用者介面。 每個設定檔偵測器都應擴充 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 類別。

`CustomEditor`屬性會通知 Unity 套用偵測器的資產類型。

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>建立元件定義 (s) 

混合現實工具組會使用元件定義 ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 檔案來指定元件之間的相依性，以及協助 Unity 減少編譯時間。

建議您為所有資料提供者及其編輯器元件建立元件定義檔。

使用先前範例中的 [資料夾結構](#namespace-and-folder-structure) 時，ContosoSpatialAwareness 資料提供者會有兩個 asmdef 檔案。

第一個元件定義適用于資料提供者。 在此範例中，它會被稱為 ContosoSpatialAwareness，而且會位於範例的 *ContosoSpatialAwareness* 資料夾中。 此元件定義必須指定 MixedReality 的相依性，以及它所相依的任何其他元件。

ContosoInputEditor 元件定義會指定設定檔偵測器和任何編輯器特定的程式碼。 這個檔案必須位於編輯器程式碼的根資料夾中。 在此範例中，檔案會位於 *ContosoSpatialAwareness\Editor* 資料夾中。 此元件定義會包含 ContosoSpatialAwareness 元件的參考，以及：

- MixedReality 工具組
- MixedReality。檢查工具
- MixedReality （工具組）

## <a name="register-the-data-provider"></a>註冊資料提供者

一旦建立之後，就可以向空間感知系統註冊資料提供者，以便在應用程式中使用。

![選取空間物件網格觀察者](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>封裝和散發

散發為協力廠商元件的資料提供者，會將封裝和散發的特定詳細資料提供給開發人員的喜好設定。 最常見的解決方案可能是透過 Unity 資產存放區產生 unitypackage 和散發。

如果資料提供者已提交並接受成為 Microsoft Mixed Reality 工具組套件的一部分，Microsoft MRTK 團隊將會將其封裝並散發為 MRTK 供應專案的一部分。

## <a name="see-also"></a>另請參閱

- [空間感知系統](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` 介面](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [`BaseSpatialAwarenessObject` 類別](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject` 類別](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject` 類別](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` 介面](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [`BaseSpatialObserver` 類別](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` 介面](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` 介面](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` 介面](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
