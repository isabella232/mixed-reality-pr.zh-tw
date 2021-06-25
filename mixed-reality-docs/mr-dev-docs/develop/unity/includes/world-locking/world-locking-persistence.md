---
ms.openlocfilehash: f937b705f10cc4a287600349283ecaed4ae44666
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112908112"
---
# <a name="world-locking-tools-recommended"></a>[ (建議) 的世界鎖定工具 ](#tab/wlt)

根據預設，全球鎖定工具會跨會話還原 Unity 的座標系統，相對於實體世界。 這表示，在結束並重新執行應用程式之後，若要讓全像地方在實體世界中出現相同的位置，則全像投影一樣必須再次具有相同的姿勢。

![Unity inspector 中的世界鎖定內容元件](../../images/world-locking-tools-img-02.png)

如果應用程式需要更細微的控制，則在偵測器中可能會停用 **自動儲存** 和 **自動載入** ，以及從腳本的持續性部分（如 [檔的持續性區段](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)中所述）進行管理。

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

另一個稱為 **XRAnchorStore** 的 API 可讓錨點在會話之間保存。 XRAnchorStore 是裝置上已儲存錨點的標記法。 錨點可以從 Unity 場景中的 **ARAnchors** 保存、從儲存體載入至新的 **ARAnchors**，或從儲存體中刪除。

> [!NOTE]
> 這些錨點會儲存並載入至相同的裝置。 未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。

### <a name="namespaces"></a>命名空間

針對 **Unity 2020 和 OpenXR**： 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

或 **Unity 2019/2020 + WINDOWS XR 外掛程式**： 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a>公用方法

```cs 
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

### <a name="getting-an-anchor-store-reference"></a>取得錨點存放區參考 

若要使用 **Unity 2020 和 OpenXR** 載入 XRAnchorStore，請在 XRAnchorSubsystem （ARAnchorManager 的子系統）上使用擴充方法：

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

若要使用 **unity 2019/2020 和 WINDOWS XR 外掛程式** 載入 XRAnchorStore，請在 XRReferencePointSubsystem (unity 2019) 或 XRAnchorSubsystem (unity 2020) （ARReferencePointManager/ARAnchorManager 的子系統）上使用擴充方法：

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>載入錨點存放區

若要在 **Unity 2020 和 OpenXR** 中載入錨點存放區，請從 ARAnchorManager 的子系統進行存取，如下所示：

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

或使用 **Unity 2019/2020 和 WINDOWS XR 外掛程式**：

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

若要查看保存/unpersisting 錨點的完整範例，請查看 [混合現實 OpenXR 外掛程式範例場景](../../xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2)中的錨點 > 錨點範例 GameObject 和 AnchorsSample .cs 腳本：

![在 Unity 編輯器中開啟之 [階層] 面板的螢幕擷取畫面，其中已醒目提示錨點範例](../../images/openxr-features-img-04.png)

![在 Unity 編輯器中開啟的 [偵測器] 面板的螢幕擷取畫面，其中已醒目提示錨點範例腳本](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

**WorldAnchorStore** 是建立全像攝影體驗的關鍵，也就是在應用程式的各個實例上，全像地方都有特定的真實世界位置。 然後，使用者可以在想要的任何地方釘選個別的全像

**命名空間：** *UnityEngine. XR*<br>
**類別：** *WorldAnchorStore*

WorldAnchorStore 可讓您跨會話保存 WorldAnchor 的位置。 若要實際跨會話保存全像投影，您必須個別追蹤使用特定世界錨點的 Gameobject。 建立具有世界錨點的 GameObject 根目錄通常是合理的，並讓子影像以本機位置位移錨定。

若要從先前的會話載入全息影像：

1. 取得 WorldAnchorStore
2. 載入與世界錨點相關的應用程式資料，以提供您世界錨點的識別碼
3. 從識別碼載入世界錨點

若要在未來的會話中儲存影像：

1. 取得 WorldAnchorStore
2. 儲存指定識別碼的世界錨點
3. 儲存與世界錨點相關的應用程式資料以及識別碼

### <a name="getting-the-worldanchorstore"></a>取得 WorldAnchorStore

您會想要保留 WorldAnchorStore 的參考，讓您知道它準備好執行作業的時間。 因為這是非同步呼叫，可能會在啟動時立即執行，您想要呼叫：

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded 在此案例中是 WorldAnchorStore 完成載入時的處理常式：

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

我們現在已有 WorldAnchorStore 的參考，我們將用它來儲存和載入特定的世界錨點。

### <a name="saving-a-worldanchor"></a>儲存 WorldAnchor

為了節省時間，我們只需要命名要儲存的內容，並將它傳遞到我們要儲存的 WorldAnchor 中。 注意：嘗試將兩個錨點儲存至相同的字串將會 (存放區失敗。Save 會傳回 false) 。 儲存新的儲存之前，請先刪除先前的儲存：

```cs
private void SaveGame()
{
    // Save data about holograms positioned by this world anchor
    if (!this.savedRoot) // Only Save the root once
    {
           this.savedRoot = this.store.Save("rootGameObject", anchor);
           Assert(this.savedRoot);
    }
}
```

### <a name="loading-a-worldanchor"></a>載入 WorldAnchor

並載入：

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

此外，我們還可以使用 store。刪除 () 以移除先前儲存和儲存的錨點。清除 () 移除先前儲存的所有資料。

### <a name="enumerating-existing-anchors"></a>列舉現有錨點

若要探索先前儲存的錨點，請呼叫 GetAllIds。

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>保存多個裝置的全像影像

您可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> ，從本機 WorldAnchor 建立持久的雲端錨點，讓您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上找到，即使這些裝置不會同時出現在同一時間。  由於雲端錨點是持續性的，因此每一段時間的多個裝置都可以看到相對於相同實體位置中錨點轉譯的內容。

若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。

在您啟動並執行 Azure 空間錨點之後，您可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。