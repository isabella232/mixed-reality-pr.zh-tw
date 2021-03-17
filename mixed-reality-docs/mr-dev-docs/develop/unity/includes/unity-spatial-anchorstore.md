---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603372"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

> [!NOTE]
> 這些錨點會儲存並載入至相同的裝置。 未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
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
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

為了載入 XRAnchorStore，外掛程式會在 XRAnchorSubsystem （ARAnchorManager 的子系統）上提供擴充方法：

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

若要使用此擴充方法，請從 ARAnchorManager 的子系統進行存取，如下所示：

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

若要查看保存/unpersisting 錨點的完整範例，請查看 [混合現實 OpenXR 外掛程式範例場景](../openxr-getting-started.md#hololens-2-samples)中的錨點 > 錨點範例 GameObject 和 AnchorsSample.cs 腳本：

![在 Unity 編輯器中開啟之 [階層] 面板的螢幕擷取畫面，其中已醒目提示錨點範例](../images/openxr-features-img-04.png)

![在 Unity 編輯器中開啟的 [偵測器] 面板的螢幕擷取畫面，其中已醒目提示錨點範例腳本](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 外掛程式](#tab/winxr)

> [!NOTE]
> 這些錨點會儲存並載入至相同的裝置。 未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。

``` cs
public class UnityEngine.XR.WindowsMR.XRAnchorStore
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

為了載入 XRAnchorStore，外掛程式會在 XRReferencePointSubsystem (Unity 2019) 或 XRAnchorSubsystem (Unity 2020) （ARReferencePointManager/ARAnchorManager 的子系統）上提供擴充方法：

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

若要使用此擴充方法，請從 ARAnchorManager 的子系統進行存取，如下所示： Unity 2019：

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

或針對 Unity 2020：

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

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

## <a name="building-a-world-scale-experience"></a>打造全球規模的體驗

**命名空間：** *UnityEngine. XR*<br>
**類型：** *WorldAnchor*

若要在 HoloLens 上讓使用者穿梭超過5個度量的真實 **世界規模體驗** ，您將需要新的技術，而不是用於會議室規模的體驗。 您將使用的一項重要技巧是建立 [空間錨點](../../../design/coordinate-systems.md#spatial-anchors) ，以在實體世界中精確地鎖定大量的全像位置，而不論使用者漫遊的程度為何，然後 [在後續的會話中再次找出這些影像](../../../design/coordinate-systems.md#spatial-anchor-persistence)。

在 Unity 中，您可以藉由將 **WorldAnchor** Unity 元件新增至 GameObject 來建立空間錨點。

### <a name="adding-a-world-anchor"></a>新增世界錨點

若要加入世界錨點，請 `AddComponent<WorldAnchor>()` 使用您要錨定到真實世界的轉換來呼叫遊戲物件。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

大功告成！ 此遊戲物件現在會錨定在實體世界中的目前位置，您可能會看到其 Unity 全局座標在一段時間後會稍微調整，以確保實體對齊。 請參閱 [載入世界錨點](#loading-a-worldanchor) ，在未來的應用程式會話中再次尋找此錨定的位置。

### <a name="removing-a-world-anchor"></a>移除世界錨點

如果您不想再將 GameObject 鎖定到實體世界位置，也不想要將它移到此框架，您可以直接在世界錨點元件上呼叫摧毀。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

如果您想要將 GameObject 移到這個畫面格，您必須改為呼叫 DestroyImmediate。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>移動世界錨定的 GameObject

當世界錨點在其上時，無法移動 GameObject。 如果您需要將 GameObject 移到此框架，您需要：

1. DestroyImmediate 世界錨點元件
2. 移動 GameObject
3. 將新的世界錨點元件新增至 GameObject。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>處理 Locatability 變更

在某個時間點，實體世界可能無法找出 WorldAnchor。 如果發生這種情況，Unity 將不會更新錨定物件的轉換。 當應用程式正在執行時，這也可能會變更。 無法處理 locatability 中的變更，會導致物件不會出現在世界中正確的實體位置。

若要收到有關 locatability 變更的通知：

1. 訂閱 OnTrackingChanged 事件
2. 處理事件

只要基礎空間錨點在所可定位的狀態與未被定位之間變更時，就會呼叫 **OnTrackingChanged** 事件。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

然後處理事件：

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

有時會立即找到錨點。 在此情況下，當 AddComponent () 傳回時，錨點的這個 isLocated 屬性會設定為 true <WorldAnchor> 。 因此，將不會觸發 OnTrackingChanged 事件。 清除模式是在附加錨點之後，以初始 IsLocated 狀態呼叫您的 OnTrackingChanged 處理常式。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a>保存多個裝置的全像影像

您可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> ，從本機 WorldAnchor 建立持久的雲端錨點，讓您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上找到，即使這些裝置不會同時出現在同一時間。  由於雲端錨點是持續性的，因此每一段時間的多個裝置都可以看到相對於相同實體位置中錨點轉譯的內容。

若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。

在您啟動並執行 Azure 空間錨點之後，您可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。
