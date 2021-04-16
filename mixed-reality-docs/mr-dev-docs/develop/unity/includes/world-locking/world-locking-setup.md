---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528766"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="06a03-101"> (建議) 的世界鎖定工具 </span><span class="sxs-lookup"><span data-stu-id="06a03-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="06a03-102">建議您使用新的「混合現實」功能工具來安裝「全球鎖定」工具。</span><span class="sxs-lookup"><span data-stu-id="06a03-102">We recommend installing World Locking Tools using the new Mixed Reality Feature Tool.</span></span> <span data-ttu-id="06a03-103">當您從下方連結下載了「混合現實」功能工具之後，請從「**全球鎖定工具**」區段中選取最新版本的 **WLT Core** ：</span><span class="sxs-lookup"><span data-stu-id="06a03-103">Once you've downloaded the Mixed Reality Feature Tool from the link below, select the latest version of **WLT Core** from the **World Locking Tools** section:</span></span>

![已選取全球鎖定工具的混合現實功能工具功能選取視窗](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="06a03-105">使用 MR 功能工具安裝世界鎖定工具</span><span class="sxs-lookup"><span data-stu-id="06a03-105">Install World Locking Tools with the MR Feature Tool</span></span>](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a><span data-ttu-id="06a03-106">自動化設定</span><span class="sxs-lookup"><span data-stu-id="06a03-106">Automated setup</span></span>

<span data-ttu-id="06a03-107">當您的專案準備就緒時，請從混合現實工具組中執行設定場景公用程式 **> 公用程式 > 世界鎖定工具**：</span><span class="sxs-lookup"><span data-stu-id="06a03-107">When your project is ready to go, run the configure scene utility from **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span></span>

![已選取混合現實工具組功能表的 Unity 編輯器](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> <span data-ttu-id="06a03-109">您可以隨時重新執行設定場景公用程式。</span><span class="sxs-lookup"><span data-stu-id="06a03-109">The Configure scene utility can be rerun at any time.</span></span> <span data-ttu-id="06a03-110">例如，如果 AR 目標已從舊版變更為 XR SDK，則應該重新執行。</span><span class="sxs-lookup"><span data-stu-id="06a03-110">For example, it should be rerun if the AR target has been changed from Legacy to XR SDK.</span></span> <span data-ttu-id="06a03-111">如果場景已正確設定，則執行公用程式不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="06a03-111">If the scene is already properly configured, running the utility has no effect.</span></span>

### <a name="visualizers"></a><span data-ttu-id="06a03-112">視覺化工具</span><span class="sxs-lookup"><span data-stu-id="06a03-112">Visualizers</span></span>

<span data-ttu-id="06a03-113">在早期開發期間，新增視覺化檢視有助於確保 WLT 的設定和運作正常。</span><span class="sxs-lookup"><span data-stu-id="06a03-113">During early development, adding visualizers can be helpful to ensure WLT is setup and working properly.</span></span> <span data-ttu-id="06a03-114">您可以針對生產效能移除它們，或者，如果基於任何原因而不再需要，請使用「移除視覺化檢視」公用程式。</span><span class="sxs-lookup"><span data-stu-id="06a03-114">They can be removed for production performance, or if for any reason are no longer needed, using the Remove visualizers utility.</span></span> <span data-ttu-id="06a03-115">您可以在 [ [工具] 檔](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)中找到更多有關視覺化檢視的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="06a03-115">More details on the visualizers can be found in the [Tools documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="06a03-116">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="06a03-116">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="06a03-117">Mixed Reality OpenXR 外掛程式透過 Unity 的 ARFoundation **ARAnchorManager** 的執行，提供基本錨定功能。</span><span class="sxs-lookup"><span data-stu-id="06a03-117">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="06a03-118">若要瞭解 ARFoundation 中 ARAnchors 的基本概念，請造訪 [AR 錨點管理員的 ARFoundation 手冊](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。</span><span class="sxs-lookup"><span data-stu-id="06a03-118">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="worldanchor"></a>[<span data-ttu-id="06a03-119">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="06a03-119">WorldAnchor</span></span>](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="06a03-120">打造全球規模的體驗</span><span class="sxs-lookup"><span data-stu-id="06a03-120">Building a world-scale experience</span></span>

<span data-ttu-id="06a03-121">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="06a03-121">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="06a03-122">**類型：** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="06a03-122">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="06a03-123">若要在 HoloLens 上讓使用者穿梭超過5個度量的真實 **世界規模體驗** ，您將需要新的技術，而不是用於會議室規模的體驗。</span><span class="sxs-lookup"><span data-stu-id="06a03-123">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="06a03-124">您將使用的一項重要技巧是建立 [空間錨點](../../../../design/coordinate-systems.md#spatial-anchors) ，以在實體世界中精確地鎖定大量的全像位置，而不論使用者漫遊的程度為何，然後 [在後續的會話中再次找出這些影像](../../../../design/coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="06a03-124">One key technique you'll use is to create a [spatial anchor](../../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="06a03-125">在 Unity 中，您可以藉由將 **WorldAnchor** Unity 元件新增至 GameObject 來建立空間錨點。</span><span class="sxs-lookup"><span data-stu-id="06a03-125">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="06a03-126">新增世界錨點</span><span class="sxs-lookup"><span data-stu-id="06a03-126">Adding a World Anchor</span></span>

<span data-ttu-id="06a03-127">若要加入世界錨點，請 `AddComponent<WorldAnchor>()` 使用您要錨定到真實世界的轉換來呼叫遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="06a03-127">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="06a03-128">大功告成！</span><span class="sxs-lookup"><span data-stu-id="06a03-128">That's it!</span></span> <span data-ttu-id="06a03-129">此遊戲物件現在會錨定在實體世界中的目前位置，您可能會看到其 Unity 全局座標在一段時間後會稍微調整，以確保實體對齊。</span><span class="sxs-lookup"><span data-stu-id="06a03-129">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="06a03-130">請參閱 [載入世界錨點](#loading-a-worldanchor) ，在未來的應用程式會話中再次尋找此錨定的位置。</span><span class="sxs-lookup"><span data-stu-id="06a03-130">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="06a03-131">移除世界錨點</span><span class="sxs-lookup"><span data-stu-id="06a03-131">Removing a World Anchor</span></span>

<span data-ttu-id="06a03-132">如果您不想再將 GameObject 鎖定到實體世界位置，也不想要將它移到此框架，您可以直接在世界錨點元件上呼叫摧毀。</span><span class="sxs-lookup"><span data-stu-id="06a03-132">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="06a03-133">如果您想要將 GameObject 移到這個畫面格，您必須改為呼叫 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="06a03-133">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="06a03-134">移動世界錨定的 GameObject</span><span class="sxs-lookup"><span data-stu-id="06a03-134">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="06a03-135">當世界錨點在其上時，無法移動 GameObject。</span><span class="sxs-lookup"><span data-stu-id="06a03-135">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="06a03-136">如果您需要將 GameObject 移到此框架，您需要：</span><span class="sxs-lookup"><span data-stu-id="06a03-136">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="06a03-137">DestroyImmediate 世界錨點元件</span><span class="sxs-lookup"><span data-stu-id="06a03-137">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="06a03-138">移動 GameObject</span><span class="sxs-lookup"><span data-stu-id="06a03-138">Move the GameObject</span></span>
3. <span data-ttu-id="06a03-139">將新的世界錨點元件新增至 GameObject。</span><span class="sxs-lookup"><span data-stu-id="06a03-139">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="06a03-140">處理 Locatability 變更</span><span class="sxs-lookup"><span data-stu-id="06a03-140">Handling Locatability Changes</span></span>

<span data-ttu-id="06a03-141">在某個時間點，實體世界可能無法找出 WorldAnchor。</span><span class="sxs-lookup"><span data-stu-id="06a03-141">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="06a03-142">如果發生這種情況，Unity 將不會更新錨定物件的轉換。</span><span class="sxs-lookup"><span data-stu-id="06a03-142">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="06a03-143">當應用程式正在執行時，這也可能會變更。</span><span class="sxs-lookup"><span data-stu-id="06a03-143">This also can change while an app is running.</span></span> <span data-ttu-id="06a03-144">無法處理 locatability 中的變更，會導致物件不會出現在世界中正確的實體位置。</span><span class="sxs-lookup"><span data-stu-id="06a03-144">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="06a03-145">若要收到有關 locatability 變更的通知：</span><span class="sxs-lookup"><span data-stu-id="06a03-145">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="06a03-146">訂閱 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="06a03-146">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="06a03-147">處理事件</span><span class="sxs-lookup"><span data-stu-id="06a03-147">Handle the event</span></span>

<span data-ttu-id="06a03-148">只要基礎空間錨點在所可定位的狀態與未被定位之間變更時，就會呼叫 **OnTrackingChanged** 事件。</span><span class="sxs-lookup"><span data-stu-id="06a03-148">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="06a03-149">然後處理事件：</span><span class="sxs-lookup"><span data-stu-id="06a03-149">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="06a03-150">有時會立即找到錨點。</span><span class="sxs-lookup"><span data-stu-id="06a03-150">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="06a03-151">在此情況下，當 AddComponent () 傳回時，錨點的這個 isLocated 屬性會設定為 true <WorldAnchor> 。</span><span class="sxs-lookup"><span data-stu-id="06a03-151">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="06a03-152">因此，將不會觸發 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="06a03-152">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="06a03-153">清除模式是在附加錨點之後，以初始 IsLocated 狀態呼叫您的 OnTrackingChanged 處理常式。</span><span class="sxs-lookup"><span data-stu-id="06a03-153">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```