---
ms.openlocfilehash: 25e42ba872764a98d4cb966b5a4922cc1dea0dc9
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528773"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="f23fa-101"> (建議) 的世界鎖定工具 </span><span class="sxs-lookup"><span data-stu-id="f23fa-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="f23fa-102">根據預設，全球鎖定工具會跨會話還原 Unity 的座標系統，相對於實體世界。</span><span class="sxs-lookup"><span data-stu-id="f23fa-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="f23fa-103">這表示，在結束並重新執行應用程式之後，若要讓全像地方在實體世界中出現相同的位置，則全像投影一樣必須再次具有相同的姿勢。</span><span class="sxs-lookup"><span data-stu-id="f23fa-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Unity inspector 中的世界鎖定內容元件](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="f23fa-105">如果應用程式需要更細微的控制，則在偵測器中可能會停用 **自動儲存** 和 **自動載入** ，以及從腳本的持續性部分（如 [檔的持續性區段](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)中所述）進行管理。</span><span class="sxs-lookup"><span data-stu-id="f23fa-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="f23fa-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="f23fa-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="f23fa-107">另一個稱為 **XRAnchorStore** 的 API 可讓錨點在會話之間保存。</span><span class="sxs-lookup"><span data-stu-id="f23fa-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="f23fa-108">XRAnchorStore 是裝置上已儲存錨點的標記法。</span><span class="sxs-lookup"><span data-stu-id="f23fa-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="f23fa-109">錨點可以從 Unity 場景中的 **ARAnchors** 保存、從儲存體載入至新的 **ARAnchors**，或從儲存體中刪除。</span><span class="sxs-lookup"><span data-stu-id="f23fa-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="f23fa-110">這些錨點會儲存並載入至相同的裝置。</span><span class="sxs-lookup"><span data-stu-id="f23fa-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="f23fa-111">未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。</span><span class="sxs-lookup"><span data-stu-id="f23fa-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="f23fa-112">命名空間</span><span class="sxs-lookup"><span data-stu-id="f23fa-112">Namespaces</span></span>

<span data-ttu-id="f23fa-113">針對 **Unity 2020 和 OpenXR**：</span><span class="sxs-lookup"><span data-stu-id="f23fa-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="f23fa-114">或 **Unity 2019/2020 + WINDOWS XR 外掛程式**：</span><span class="sxs-lookup"><span data-stu-id="f23fa-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="f23fa-115">公用方法</span><span class="sxs-lookup"><span data-stu-id="f23fa-115">Public methods</span></span>

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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="f23fa-116">取得錨點存放區參考</span><span class="sxs-lookup"><span data-stu-id="f23fa-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="f23fa-117">若要使用 **Unity 2020 和 OpenXR** 載入 XRAnchorStore，請在 XRAnchorSubsystem （ARAnchorManager 的子系統）上使用擴充方法：</span><span class="sxs-lookup"><span data-stu-id="f23fa-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="f23fa-118">若要使用 **unity 2019/2020 和 WINDOWS XR 外掛程式** 載入 XRAnchorStore，請在 XRReferencePointSubsystem (unity 2019) 或 XRAnchorSubsystem (unity 2020) （ARReferencePointManager/ARAnchorManager 的子系統）上使用擴充方法：</span><span class="sxs-lookup"><span data-stu-id="f23fa-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="f23fa-119">載入錨點存放區</span><span class="sxs-lookup"><span data-stu-id="f23fa-119">Loading an anchor store</span></span>

<span data-ttu-id="f23fa-120">若要在 **Unity 2020 和 OpenXR** 中載入錨點存放區，請從 ARAnchorManager 的子系統進行存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f23fa-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="f23fa-121">或使用 **Unity 2019/2020 和 WINDOWS XR 外掛程式**：</span><span class="sxs-lookup"><span data-stu-id="f23fa-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="f23fa-122">若要查看保存/unpersisting 錨點的完整範例，請查看 [混合現實 OpenXR 外掛程式範例場景](../../openxr-getting-started.md#hololens-2-samples)中的錨點 > 錨點範例 GameObject 和 AnchorsSample .cs 腳本：</span><span class="sxs-lookup"><span data-stu-id="f23fa-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#hololens-2-samples):</span></span>

![在 Unity 編輯器中開啟之 [階層] 面板的螢幕擷取畫面，其中已醒目提示錨點範例](../../images/openxr-features-img-04.png)

![在 Unity 編輯器中開啟的 [偵測器] 面板的螢幕擷取畫面，其中已醒目提示錨點範例腳本](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="f23fa-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f23fa-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="f23fa-126">**WorldAnchorStore** 是建立全像攝影體驗的關鍵，也就是在應用程式的各個實例上，全像地方都有特定的真實世界位置。</span><span class="sxs-lookup"><span data-stu-id="f23fa-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="f23fa-127">然後，使用者可以在想要的任何地方釘選個別的全像</span><span class="sxs-lookup"><span data-stu-id="f23fa-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="f23fa-128">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="f23fa-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="f23fa-129">**類別：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="f23fa-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="f23fa-130">WorldAnchorStore 可讓您跨會話保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="f23fa-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="f23fa-131">若要實際跨會話保存全像投影，您必須個別追蹤使用特定世界錨點的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="f23fa-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="f23fa-132">建立具有世界錨點的 GameObject 根目錄通常是合理的，並讓子影像以本機位置位移錨定。</span><span class="sxs-lookup"><span data-stu-id="f23fa-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="f23fa-133">若要從先前的會話載入全息影像：</span><span class="sxs-lookup"><span data-stu-id="f23fa-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="f23fa-134">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f23fa-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f23fa-135">載入與世界錨點相關的應用程式資料，以提供您世界錨點的識別碼</span><span class="sxs-lookup"><span data-stu-id="f23fa-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="f23fa-136">從識別碼載入世界錨點</span><span class="sxs-lookup"><span data-stu-id="f23fa-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="f23fa-137">若要在未來的會話中儲存影像：</span><span class="sxs-lookup"><span data-stu-id="f23fa-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="f23fa-138">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f23fa-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f23fa-139">儲存指定識別碼的世界錨點</span><span class="sxs-lookup"><span data-stu-id="f23fa-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="f23fa-140">儲存與世界錨點相關的應用程式資料以及識別碼</span><span class="sxs-lookup"><span data-stu-id="f23fa-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="f23fa-141">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f23fa-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="f23fa-142">您會想要保留 WorldAnchorStore 的參考，讓您知道它準備好執行作業的時間。</span><span class="sxs-lookup"><span data-stu-id="f23fa-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="f23fa-143">因為這是非同步呼叫，可能會在啟動時立即執行，您想要呼叫：</span><span class="sxs-lookup"><span data-stu-id="f23fa-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="f23fa-144">StoreLoaded 在此案例中是 WorldAnchorStore 完成載入時的處理常式：</span><span class="sxs-lookup"><span data-stu-id="f23fa-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="f23fa-145">我們現在已有 WorldAnchorStore 的參考，我們將用它來儲存和載入特定的世界錨點。</span><span class="sxs-lookup"><span data-stu-id="f23fa-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="f23fa-146">儲存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f23fa-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="f23fa-147">為了節省時間，我們只需要命名要儲存的內容，並將它傳遞到我們要儲存的 WorldAnchor 中。</span><span class="sxs-lookup"><span data-stu-id="f23fa-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="f23fa-148">注意：嘗試將兩個錨點儲存至相同的字串將會 (存放區失敗。Save 會傳回 false) 。</span><span class="sxs-lookup"><span data-stu-id="f23fa-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="f23fa-149">儲存新的儲存之前，請先刪除先前的儲存：</span><span class="sxs-lookup"><span data-stu-id="f23fa-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="f23fa-150">載入 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f23fa-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="f23fa-151">並載入：</span><span class="sxs-lookup"><span data-stu-id="f23fa-151">And to load:</span></span>

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

<span data-ttu-id="f23fa-152">此外，我們還可以使用 store。刪除 () 以移除先前儲存和儲存的錨點。清除 () 移除先前儲存的所有資料。</span><span class="sxs-lookup"><span data-stu-id="f23fa-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="f23fa-153">列舉現有錨點</span><span class="sxs-lookup"><span data-stu-id="f23fa-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="f23fa-154">若要探索先前儲存的錨點，請呼叫 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="f23fa-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="f23fa-155">保存多個裝置的全像影像</span><span class="sxs-lookup"><span data-stu-id="f23fa-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="f23fa-156">您可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> ，從本機 WorldAnchor 建立持久的雲端錨點，讓您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上找到，即使這些裝置不會同時出現在同一時間。</span><span class="sxs-lookup"><span data-stu-id="f23fa-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="f23fa-157">由於雲端錨點是持續性的，因此每一段時間的多個裝置都可以看到相對於相同實體位置中錨點轉譯的內容。</span><span class="sxs-lookup"><span data-stu-id="f23fa-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="f23fa-158">若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="f23fa-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="f23fa-159">在您啟動並執行 Azure 空間錨點之後，您可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="f23fa-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
