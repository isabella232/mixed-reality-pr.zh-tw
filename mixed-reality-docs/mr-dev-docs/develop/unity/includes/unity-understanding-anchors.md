---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719722"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="a352f-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="a352f-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="a352f-102">Mixed Reality OpenXR 外掛程式透過 Unity 的 ARFoundation **ARAnchorManager** 的執行，提供基本錨定功能。</span><span class="sxs-lookup"><span data-stu-id="a352f-102">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="a352f-103">若要瞭解 ARFoundation 中 ARAnchors 的基本概念，請造訪 [AR 錨點管理員的 ARFoundation 手冊](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。</span><span class="sxs-lookup"><span data-stu-id="a352f-103">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="a352f-104">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="a352f-104">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="a352f-105">Mixed Reality OpenXR 外掛程式透過 Unity 的 ARFoundation **ARAnchorManager** 的執行，提供基本錨定功能。</span><span class="sxs-lookup"><span data-stu-id="a352f-105">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="a352f-106">若要瞭解 ARFoundation 中 ARAnchors 的基本概念，請造訪 [AR 錨點管理員的 ARFoundation 手冊](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。</span><span class="sxs-lookup"><span data-stu-id="a352f-106">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="a352f-107">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="a352f-107">Legacy WSA</span></span>](#tab/wsa)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="a352f-108">打造全球規模的體驗</span><span class="sxs-lookup"><span data-stu-id="a352f-108">Building a world-scale experience</span></span>

<span data-ttu-id="a352f-109">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="a352f-109">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="a352f-110">**類型：** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="a352f-110">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="a352f-111">若要在 HoloLens 上讓使用者穿梭超過5個度量的真實 **世界規模體驗** ，您將需要新的技術，而不是用於會議室規模的體驗。</span><span class="sxs-lookup"><span data-stu-id="a352f-111">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="a352f-112">您將使用的一項重要技巧是建立 [空間錨點](../../../design/coordinate-systems.md#spatial-anchors) ，以在實體世界中精確地鎖定大量的全像位置，而不論使用者漫遊的程度為何，然後 [在後續的會話中再次找出這些影像](../../../design/coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="a352f-112">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="a352f-113">在 Unity 中，您可以藉由將 **WorldAnchor** Unity 元件新增至 GameObject 來建立空間錨點。</span><span class="sxs-lookup"><span data-stu-id="a352f-113">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="a352f-114">新增世界錨點</span><span class="sxs-lookup"><span data-stu-id="a352f-114">Adding a World Anchor</span></span>

<span data-ttu-id="a352f-115">若要加入世界錨點，請 `AddComponent<WorldAnchor>()` 使用您要錨定到真實世界的轉換來呼叫遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="a352f-115">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="a352f-116">大功告成！</span><span class="sxs-lookup"><span data-stu-id="a352f-116">That's it!</span></span> <span data-ttu-id="a352f-117">此遊戲物件現在會錨定在實體世界中的目前位置，您可能會看到其 Unity 全局座標在一段時間後會稍微調整，以確保實體對齊。</span><span class="sxs-lookup"><span data-stu-id="a352f-117">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="a352f-118">請參閱 [載入世界錨點](#loading-a-worldanchor) ，在未來的應用程式會話中再次尋找此錨定的位置。</span><span class="sxs-lookup"><span data-stu-id="a352f-118">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="a352f-119">移除世界錨點</span><span class="sxs-lookup"><span data-stu-id="a352f-119">Removing a World Anchor</span></span>

<span data-ttu-id="a352f-120">如果您不想再將 GameObject 鎖定到實體世界位置，也不想要將它移到此框架，您可以直接在世界錨點元件上呼叫摧毀。</span><span class="sxs-lookup"><span data-stu-id="a352f-120">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="a352f-121">如果您想要將 GameObject 移到這個畫面格，您必須改為呼叫 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="a352f-121">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="a352f-122">移動世界錨定的 GameObject</span><span class="sxs-lookup"><span data-stu-id="a352f-122">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="a352f-123">當世界錨點在其上時，無法移動 GameObject。</span><span class="sxs-lookup"><span data-stu-id="a352f-123">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="a352f-124">如果您需要將 GameObject 移到此框架，您需要：</span><span class="sxs-lookup"><span data-stu-id="a352f-124">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="a352f-125">DestroyImmediate 世界錨點元件</span><span class="sxs-lookup"><span data-stu-id="a352f-125">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="a352f-126">移動 GameObject</span><span class="sxs-lookup"><span data-stu-id="a352f-126">Move the GameObject</span></span>
3. <span data-ttu-id="a352f-127">將新的世界錨點元件新增至 GameObject。</span><span class="sxs-lookup"><span data-stu-id="a352f-127">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="a352f-128">處理 Locatability 變更</span><span class="sxs-lookup"><span data-stu-id="a352f-128">Handling Locatability Changes</span></span>

<span data-ttu-id="a352f-129">在某個時間點，實體世界可能無法找出 WorldAnchor。</span><span class="sxs-lookup"><span data-stu-id="a352f-129">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="a352f-130">如果發生這種情況，Unity 將不會更新錨定物件的轉換。</span><span class="sxs-lookup"><span data-stu-id="a352f-130">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="a352f-131">當應用程式正在執行時，這也可能會變更。</span><span class="sxs-lookup"><span data-stu-id="a352f-131">This also can change while an app is running.</span></span> <span data-ttu-id="a352f-132">無法處理 locatability 中的變更，會導致物件不會出現在世界中正確的實體位置。</span><span class="sxs-lookup"><span data-stu-id="a352f-132">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="a352f-133">若要收到有關 locatability 變更的通知：</span><span class="sxs-lookup"><span data-stu-id="a352f-133">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="a352f-134">訂閱 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="a352f-134">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="a352f-135">處理事件</span><span class="sxs-lookup"><span data-stu-id="a352f-135">Handle the event</span></span>

<span data-ttu-id="a352f-136">只要基礎空間錨點在所可定位的狀態與未被定位之間變更時，就會呼叫 **OnTrackingChanged** 事件。</span><span class="sxs-lookup"><span data-stu-id="a352f-136">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="a352f-137">然後處理事件：</span><span class="sxs-lookup"><span data-stu-id="a352f-137">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="a352f-138">有時會立即找到錨點。</span><span class="sxs-lookup"><span data-stu-id="a352f-138">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="a352f-139">在此情況下，當 AddComponent () 傳回時，錨點的這個 isLocated 屬性會設定為 true <WorldAnchor> 。</span><span class="sxs-lookup"><span data-stu-id="a352f-139">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="a352f-140">因此，將不會觸發 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="a352f-140">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="a352f-141">清除模式是在附加錨點之後，以初始 IsLocated 狀態呼叫您的 OnTrackingChanged 處理常式。</span><span class="sxs-lookup"><span data-stu-id="a352f-141">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```