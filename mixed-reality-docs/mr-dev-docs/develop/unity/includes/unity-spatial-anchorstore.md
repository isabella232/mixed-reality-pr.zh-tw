---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719606"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="c53af-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="c53af-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="c53af-102">另一個稱為 **XRAnchorStore** 的 API 可讓錨點在會話之間保存。</span><span class="sxs-lookup"><span data-stu-id="c53af-102">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="c53af-103">XRAnchorStore 是裝置上已儲存錨點的標記法。</span><span class="sxs-lookup"><span data-stu-id="c53af-103">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="c53af-104">錨點可以從 Unity 場景中的 **ARAnchors** 保存、從儲存體載入至新的 **ARAnchors**，或從儲存體中刪除。</span><span class="sxs-lookup"><span data-stu-id="c53af-104">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="c53af-105">這些錨點會儲存並載入至相同的裝置。</span><span class="sxs-lookup"><span data-stu-id="c53af-105">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="c53af-106">未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。</span><span class="sxs-lookup"><span data-stu-id="c53af-106">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="c53af-107">為了載入 XRAnchorStore，外掛程式會在 XRAnchorSubsystem （ARAnchorManager 的子系統）上提供擴充方法：</span><span class="sxs-lookup"><span data-stu-id="c53af-107">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="c53af-108">若要使用此擴充方法，請從 ARAnchorManager 的子系統進行存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c53af-108">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="c53af-109">若要查看保存/unpersisting 錨點的完整範例，請查看 [混合現實 OpenXR 外掛程式範例場景](../openxr-getting-started.md#hololens-2-samples)中的錨點 > 錨點範例 GameObject 和 AnchorsSample .cs 腳本：</span><span class="sxs-lookup"><span data-stu-id="c53af-109">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![在 Unity 編輯器中開啟之 [階層] 面板的螢幕擷取畫面，其中已醒目提示錨點範例](../images/openxr-features-img-04.png)

![在 Unity 編輯器中開啟的 [偵測器] 面板的螢幕擷取畫面，其中已醒目提示錨點範例腳本](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="c53af-112">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="c53af-112">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="c53af-113">名為 **XRAnchorStore** 的 API 可讓錨點在會話之間保存。</span><span class="sxs-lookup"><span data-stu-id="c53af-113">An API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="c53af-114">XRAnchorStore 是裝置上已儲存錨點的標記法。</span><span class="sxs-lookup"><span data-stu-id="c53af-114">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="c53af-115">錨點可以從 Unity 場景中的 **ARAnchors** 保存、從儲存體載入至新的 **ARAnchors**，或從儲存體中刪除。</span><span class="sxs-lookup"><span data-stu-id="c53af-115">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="c53af-116">這些錨點會儲存並載入至相同的裝置。</span><span class="sxs-lookup"><span data-stu-id="c53af-116">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="c53af-117">未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。</span><span class="sxs-lookup"><span data-stu-id="c53af-117">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="c53af-118">為了載入 XRAnchorStore，外掛程式會在 XRReferencePointSubsystem (Unity 2019) 或 XRAnchorSubsystem (Unity 2020) （ARReferencePointManager/ARAnchorManager 的子系統）上提供擴充方法：</span><span class="sxs-lookup"><span data-stu-id="c53af-118">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="c53af-119">若要使用此擴充方法，請從 ARAnchorManager 的子系統進行存取，如下所示： Unity 2019：</span><span class="sxs-lookup"><span data-stu-id="c53af-119">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="c53af-120">或針對 Unity 2020：</span><span class="sxs-lookup"><span data-stu-id="c53af-120">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="c53af-121">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="c53af-121">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="c53af-122">**WorldAnchorStore** 是建立全像攝影體驗的關鍵，也就是在應用程式的各個實例上，全像地方都有特定的真實世界位置。</span><span class="sxs-lookup"><span data-stu-id="c53af-122">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="c53af-123">然後，使用者可以在想要的任何地方釘選個別的全像</span><span class="sxs-lookup"><span data-stu-id="c53af-123">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="c53af-124">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="c53af-124">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="c53af-125">**類別：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="c53af-125">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="c53af-126">WorldAnchorStore 可讓您跨會話保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="c53af-126">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="c53af-127">若要實際跨會話保存全像投影，您必須個別追蹤使用特定世界錨點的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="c53af-127">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="c53af-128">建立具有世界錨點的 GameObject 根目錄通常是合理的，並讓子影像以本機位置位移錨定。</span><span class="sxs-lookup"><span data-stu-id="c53af-128">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="c53af-129">若要從先前的會話載入全息影像：</span><span class="sxs-lookup"><span data-stu-id="c53af-129">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="c53af-130">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="c53af-130">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="c53af-131">載入與世界錨點相關的應用程式資料，以提供您世界錨點的識別碼</span><span class="sxs-lookup"><span data-stu-id="c53af-131">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="c53af-132">從識別碼載入世界錨點</span><span class="sxs-lookup"><span data-stu-id="c53af-132">Load a world anchor from its ID</span></span>

<span data-ttu-id="c53af-133">若要在未來的會話中儲存影像：</span><span class="sxs-lookup"><span data-stu-id="c53af-133">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="c53af-134">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="c53af-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="c53af-135">儲存指定識別碼的世界錨點</span><span class="sxs-lookup"><span data-stu-id="c53af-135">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="c53af-136">儲存與世界錨點相關的應用程式資料以及識別碼</span><span class="sxs-lookup"><span data-stu-id="c53af-136">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="c53af-137">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="c53af-137">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="c53af-138">您會想要保留 WorldAnchorStore 的參考，讓您知道它準備好執行作業的時間。</span><span class="sxs-lookup"><span data-stu-id="c53af-138">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="c53af-139">因為這是非同步呼叫，可能會在啟動時立即執行，您想要呼叫：</span><span class="sxs-lookup"><span data-stu-id="c53af-139">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="c53af-140">StoreLoaded 在此案例中是 WorldAnchorStore 完成載入時的處理常式：</span><span class="sxs-lookup"><span data-stu-id="c53af-140">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="c53af-141">我們現在已有 WorldAnchorStore 的參考，我們將用它來儲存和載入特定的世界錨點。</span><span class="sxs-lookup"><span data-stu-id="c53af-141">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="c53af-142">儲存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="c53af-142">Saving a WorldAnchor</span></span>

<span data-ttu-id="c53af-143">為了節省時間，我們只需要命名要儲存的內容，並將它傳遞到我們要儲存的 WorldAnchor 中。</span><span class="sxs-lookup"><span data-stu-id="c53af-143">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="c53af-144">注意：嘗試將兩個錨點儲存至相同的字串將會 (存放區失敗。Save 會傳回 false) 。</span><span class="sxs-lookup"><span data-stu-id="c53af-144">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="c53af-145">儲存新的儲存之前，請先刪除先前的儲存：</span><span class="sxs-lookup"><span data-stu-id="c53af-145">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="c53af-146">載入 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="c53af-146">Loading a WorldAnchor</span></span>

<span data-ttu-id="c53af-147">並載入：</span><span class="sxs-lookup"><span data-stu-id="c53af-147">And to load:</span></span>

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

<span data-ttu-id="c53af-148">此外，我們還可以使用 store。刪除 () 以移除先前儲存和儲存的錨點。清除 () 移除先前儲存的所有資料。</span><span class="sxs-lookup"><span data-stu-id="c53af-148">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="c53af-149">列舉現有錨點</span><span class="sxs-lookup"><span data-stu-id="c53af-149">Enumerating Existing Anchors</span></span>

<span data-ttu-id="c53af-150">若要探索先前儲存的錨點，請呼叫 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="c53af-150">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="c53af-151">保存多個裝置的全像影像</span><span class="sxs-lookup"><span data-stu-id="c53af-151">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="c53af-152">您可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> ，從本機 WorldAnchor 建立持久的雲端錨點，讓您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上找到，即使這些裝置不會同時出現在同一時間。</span><span class="sxs-lookup"><span data-stu-id="c53af-152">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="c53af-153">由於雲端錨點是持續性的，因此每一段時間的多個裝置都可以看到相對於相同實體位置中錨點轉譯的內容。</span><span class="sxs-lookup"><span data-stu-id="c53af-153">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="c53af-154">若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="c53af-154">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="c53af-155">在您啟動並執行 Azure 空間錨點之後，您可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="c53af-155">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
