---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603372"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="c530a-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="c530a-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

> [!NOTE]
> <span data-ttu-id="c530a-102">這些錨點會儲存並載入至相同的裝置。</span><span class="sxs-lookup"><span data-stu-id="c530a-102">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="c530a-103">未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。</span><span class="sxs-lookup"><span data-stu-id="c530a-103">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="c530a-104">為了載入 XRAnchorStore，外掛程式會在 XRAnchorSubsystem （ARAnchorManager 的子系統）上提供擴充方法：</span><span class="sxs-lookup"><span data-stu-id="c530a-104">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="c530a-105">若要使用此擴充方法，請從 ARAnchorManager 的子系統進行存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c530a-105">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="c530a-106">若要查看保存/unpersisting 錨點的完整範例，請查看 [混合現實 OpenXR 外掛程式範例場景](../openxr-getting-started.md#hololens-2-samples)中的錨點 > 錨點範例 GameObject 和 AnchorsSample.cs 腳本：</span><span class="sxs-lookup"><span data-stu-id="c530a-106">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![在 Unity 編輯器中開啟之 [階層] 面板的螢幕擷取畫面，其中已醒目提示錨點範例](../images/openxr-features-img-04.png)

![在 Unity 編輯器中開啟的 [偵測器] 面板的螢幕擷取畫面，其中已醒目提示錨點範例腳本](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="c530a-109">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="c530a-109">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

> [!NOTE]
> <span data-ttu-id="c530a-110">這些錨點會儲存並載入至相同的裝置。</span><span class="sxs-lookup"><span data-stu-id="c530a-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="c530a-111">未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。</span><span class="sxs-lookup"><span data-stu-id="c530a-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="c530a-112">為了載入 XRAnchorStore，外掛程式會在 XRReferencePointSubsystem (Unity 2019) 或 XRAnchorSubsystem (Unity 2020) （ARReferencePointManager/ARAnchorManager 的子系統）上提供擴充方法：</span><span class="sxs-lookup"><span data-stu-id="c530a-112">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="c530a-113">若要使用此擴充方法，請從 ARAnchorManager 的子系統進行存取，如下所示： Unity 2019：</span><span class="sxs-lookup"><span data-stu-id="c530a-113">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="c530a-114">或針對 Unity 2020：</span><span class="sxs-lookup"><span data-stu-id="c530a-114">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="c530a-115">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="c530a-115">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="c530a-116">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="c530a-116">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="c530a-117">**類別：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="c530a-117">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="c530a-118">WorldAnchorStore 可讓您跨會話保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="c530a-118">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="c530a-119">若要實際跨會話保存全像投影，您必須個別追蹤使用特定世界錨點的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="c530a-119">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="c530a-120">建立具有世界錨點的 GameObject 根目錄通常是合理的，並讓子影像以本機位置位移錨定。</span><span class="sxs-lookup"><span data-stu-id="c530a-120">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="c530a-121">若要從先前的會話載入全息影像：</span><span class="sxs-lookup"><span data-stu-id="c530a-121">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="c530a-122">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="c530a-122">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="c530a-123">載入與世界錨點相關的應用程式資料，以提供您世界錨點的識別碼</span><span class="sxs-lookup"><span data-stu-id="c530a-123">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="c530a-124">從識別碼載入世界錨點</span><span class="sxs-lookup"><span data-stu-id="c530a-124">Load a world anchor from its ID</span></span>

<span data-ttu-id="c530a-125">若要在未來的會話中儲存影像：</span><span class="sxs-lookup"><span data-stu-id="c530a-125">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="c530a-126">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="c530a-126">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="c530a-127">儲存指定識別碼的世界錨點</span><span class="sxs-lookup"><span data-stu-id="c530a-127">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="c530a-128">儲存與世界錨點相關的應用程式資料以及識別碼</span><span class="sxs-lookup"><span data-stu-id="c530a-128">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="c530a-129">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="c530a-129">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="c530a-130">您會想要保留 WorldAnchorStore 的參考，讓您知道它準備好執行作業的時間。</span><span class="sxs-lookup"><span data-stu-id="c530a-130">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="c530a-131">因為這是非同步呼叫，可能會在啟動時立即執行，您想要呼叫：</span><span class="sxs-lookup"><span data-stu-id="c530a-131">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="c530a-132">StoreLoaded 在此案例中是 WorldAnchorStore 完成載入時的處理常式：</span><span class="sxs-lookup"><span data-stu-id="c530a-132">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="c530a-133">我們現在已有 WorldAnchorStore 的參考，我們將用它來儲存和載入特定的世界錨點。</span><span class="sxs-lookup"><span data-stu-id="c530a-133">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="c530a-134">儲存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="c530a-134">Saving a WorldAnchor</span></span>

<span data-ttu-id="c530a-135">為了節省時間，我們只需要命名要儲存的內容，並將它傳遞到我們要儲存的 WorldAnchor 中。</span><span class="sxs-lookup"><span data-stu-id="c530a-135">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="c530a-136">注意：嘗試將兩個錨點儲存至相同的字串將會 (存放區失敗。Save 會傳回 false) 。</span><span class="sxs-lookup"><span data-stu-id="c530a-136">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="c530a-137">儲存新的儲存之前，請先刪除先前的儲存：</span><span class="sxs-lookup"><span data-stu-id="c530a-137">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="c530a-138">載入 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="c530a-138">Loading a WorldAnchor</span></span>

<span data-ttu-id="c530a-139">並載入：</span><span class="sxs-lookup"><span data-stu-id="c530a-139">And to load:</span></span>

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

<span data-ttu-id="c530a-140">此外，我們還可以使用 store。刪除 () 以移除先前儲存和儲存的錨點。清除 () 移除先前儲存的所有資料。</span><span class="sxs-lookup"><span data-stu-id="c530a-140">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="c530a-141">列舉現有錨點</span><span class="sxs-lookup"><span data-stu-id="c530a-141">Enumerating Existing Anchors</span></span>

<span data-ttu-id="c530a-142">若要探索先前儲存的錨點，請呼叫 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="c530a-142">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="c530a-143">打造全球規模的體驗</span><span class="sxs-lookup"><span data-stu-id="c530a-143">Building a world-scale experience</span></span>

<span data-ttu-id="c530a-144">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="c530a-144">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="c530a-145">**類型：** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="c530a-145">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="c530a-146">若要在 HoloLens 上讓使用者穿梭超過5個度量的真實 **世界規模體驗** ，您將需要新的技術，而不是用於會議室規模的體驗。</span><span class="sxs-lookup"><span data-stu-id="c530a-146">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="c530a-147">您將使用的一項重要技巧是建立 [空間錨點](../../../design/coordinate-systems.md#spatial-anchors) ，以在實體世界中精確地鎖定大量的全像位置，而不論使用者漫遊的程度為何，然後 [在後續的會話中再次找出這些影像](../../../design/coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="c530a-147">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="c530a-148">在 Unity 中，您可以藉由將 **WorldAnchor** Unity 元件新增至 GameObject 來建立空間錨點。</span><span class="sxs-lookup"><span data-stu-id="c530a-148">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="c530a-149">新增世界錨點</span><span class="sxs-lookup"><span data-stu-id="c530a-149">Adding a World Anchor</span></span>

<span data-ttu-id="c530a-150">若要加入世界錨點，請 `AddComponent<WorldAnchor>()` 使用您要錨定到真實世界的轉換來呼叫遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="c530a-150">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="c530a-151">大功告成！</span><span class="sxs-lookup"><span data-stu-id="c530a-151">That's it!</span></span> <span data-ttu-id="c530a-152">此遊戲物件現在會錨定在實體世界中的目前位置，您可能會看到其 Unity 全局座標在一段時間後會稍微調整，以確保實體對齊。</span><span class="sxs-lookup"><span data-stu-id="c530a-152">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="c530a-153">請參閱 [載入世界錨點](#loading-a-worldanchor) ，在未來的應用程式會話中再次尋找此錨定的位置。</span><span class="sxs-lookup"><span data-stu-id="c530a-153">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="c530a-154">移除世界錨點</span><span class="sxs-lookup"><span data-stu-id="c530a-154">Removing a World Anchor</span></span>

<span data-ttu-id="c530a-155">如果您不想再將 GameObject 鎖定到實體世界位置，也不想要將它移到此框架，您可以直接在世界錨點元件上呼叫摧毀。</span><span class="sxs-lookup"><span data-stu-id="c530a-155">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="c530a-156">如果您想要將 GameObject 移到這個畫面格，您必須改為呼叫 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="c530a-156">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="c530a-157">移動世界錨定的 GameObject</span><span class="sxs-lookup"><span data-stu-id="c530a-157">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="c530a-158">當世界錨點在其上時，無法移動 GameObject。</span><span class="sxs-lookup"><span data-stu-id="c530a-158">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="c530a-159">如果您需要將 GameObject 移到此框架，您需要：</span><span class="sxs-lookup"><span data-stu-id="c530a-159">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="c530a-160">DestroyImmediate 世界錨點元件</span><span class="sxs-lookup"><span data-stu-id="c530a-160">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="c530a-161">移動 GameObject</span><span class="sxs-lookup"><span data-stu-id="c530a-161">Move the GameObject</span></span>
3. <span data-ttu-id="c530a-162">將新的世界錨點元件新增至 GameObject。</span><span class="sxs-lookup"><span data-stu-id="c530a-162">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="c530a-163">處理 Locatability 變更</span><span class="sxs-lookup"><span data-stu-id="c530a-163">Handling Locatability Changes</span></span>

<span data-ttu-id="c530a-164">在某個時間點，實體世界可能無法找出 WorldAnchor。</span><span class="sxs-lookup"><span data-stu-id="c530a-164">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="c530a-165">如果發生這種情況，Unity 將不會更新錨定物件的轉換。</span><span class="sxs-lookup"><span data-stu-id="c530a-165">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="c530a-166">當應用程式正在執行時，這也可能會變更。</span><span class="sxs-lookup"><span data-stu-id="c530a-166">This also can change while an app is running.</span></span> <span data-ttu-id="c530a-167">無法處理 locatability 中的變更，會導致物件不會出現在世界中正確的實體位置。</span><span class="sxs-lookup"><span data-stu-id="c530a-167">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="c530a-168">若要收到有關 locatability 變更的通知：</span><span class="sxs-lookup"><span data-stu-id="c530a-168">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="c530a-169">訂閱 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="c530a-169">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="c530a-170">處理事件</span><span class="sxs-lookup"><span data-stu-id="c530a-170">Handle the event</span></span>

<span data-ttu-id="c530a-171">只要基礎空間錨點在所可定位的狀態與未被定位之間變更時，就會呼叫 **OnTrackingChanged** 事件。</span><span class="sxs-lookup"><span data-stu-id="c530a-171">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="c530a-172">然後處理事件：</span><span class="sxs-lookup"><span data-stu-id="c530a-172">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="c530a-173">有時會立即找到錨點。</span><span class="sxs-lookup"><span data-stu-id="c530a-173">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="c530a-174">在此情況下，當 AddComponent () 傳回時，錨點的這個 isLocated 屬性會設定為 true <WorldAnchor> 。</span><span class="sxs-lookup"><span data-stu-id="c530a-174">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="c530a-175">因此，將不會觸發 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="c530a-175">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="c530a-176">清除模式是在附加錨點之後，以初始 IsLocated 狀態呼叫您的 OnTrackingChanged 處理常式。</span><span class="sxs-lookup"><span data-stu-id="c530a-176">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="c530a-177">保存多個裝置的全像影像</span><span class="sxs-lookup"><span data-stu-id="c530a-177">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="c530a-178">您可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> ，從本機 WorldAnchor 建立持久的雲端錨點，讓您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上找到，即使這些裝置不會同時出現在同一時間。</span><span class="sxs-lookup"><span data-stu-id="c530a-178">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="c530a-179">由於雲端錨點是持續性的，因此每一段時間的多個裝置都可以看到相對於相同實體位置中錨點轉譯的內容。</span><span class="sxs-lookup"><span data-stu-id="c530a-179">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="c530a-180">若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="c530a-180">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="c530a-181">在您啟動並執行 Azure 空間錨點之後，您可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="c530a-181">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
