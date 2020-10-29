---
title: Unity 中的座標系統
description: 瞭解如何在 Unity 中打造站上、站上、房間規模和世界級混合現實體驗。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系統、空間座標系統、僅限方向、固定大小、固定大小、會議室規模、世界規模、360度、上、位置、空間、世界、縮放、位置、方向、Unity、錨點、空間錨點、世界錨點、全球鎖定、世界鎖定、locatability、界限、recenter
ms.openlocfilehash: 59fae57f3ca5048f4027ed96fca03255683c1fe3
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91676926"
---
# <a name="coordinate-systems-in-unity"></a>Unity 中的座標系統

Windows Mixed Reality 透過房間規模的應用程式，支援橫跨各種 [體驗規模](../../design/coordinate-systems.md)的應用程式，從僅限方向和已安置規模的應用程式。 在 HoloLens 上，您可以進一步建立全球規模的應用程式，讓使用者超越5個計量，探索整個大樓的整個樓層。

在 Unity 中打造混合現實體驗的第一個步驟，是決定您的應用程式將設為目標的 [體驗規模](../../design/coordinate-systems.md) 。

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>打造僅限方向或內部規模的體驗

**命名空間：** *UnityEngine. XR*<br>
**類型：** *XRDevice*

若要建立 **僅限方向** 或內部 **規模的體驗** ，您必須將 Unity 設定為「固定追蹤空間」類型。 這會設定 Unity 的全局座標系統，以追蹤 [固定的參考框架](../../design/coordinate-systems.md#spatial-coordinate-systems)。 在「固定追蹤」模式中，放在「相機」預設位置前方之編輯器中的內容 (轉寄是-Z) 將會在應用程式啟動時出現在使用者前面。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**命名空間：** *UnityEngine. XR*<br>
**類型：** *InputTracking*

若要取得純 **方向的體驗** （例如360度的影片檢視器） (其中的位置標頭更新會使假像) 損毀，您可以接著設定 [XR。InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 至 true：

```cs
InputTracking.disablePositionalTracking = true;
```

針對內部 **規模的體驗** ，讓使用者稍後 recenter 已安裝的來源，您可以呼叫 [XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法：

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>打造大規模或房間規模的體驗

**命名空間：** *UnityEngine. XR*<br>
**類型：** *XRDevice*

若要獲得 **大規模** 或 **房間規模的體驗** ，您必須將內容放在地面的相對位置。 您可以使用 **[空間階段](../../design/coordinate-systems.md#spatial-coordinate-systems)** （代表使用者定義的樓層層級來源和選擇性的空間界限），在第一次執行期間設定使用者的樓層。

若要確保 Unity 在地面層級進行全局座標系統操作，您可以將 Unity 設定為 RoomScale 追蹤空間類型，並確定設定成功：

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* 如果 SetTrackingSpaceType 傳回 true，表示 Unity 已成功切換其全局座標系統，以追蹤 [參考的階段框架](../../design/coordinate-systems.md#spatial-coordinate-systems)。
* 如果 SetTrackingSpaceType 傳回 false，則 Unity 無法切換至參考的階段框架，可能是因為使用者尚未在其環境中設定。 這並不常見，但如果階段是在不同的房間內設定，而裝置已移至目前的房間，而沒有使用者設定新的階段，就可能發生這種情況。

一旦您的應用程式成功設定 RoomScale 追蹤空間類型，放在 y = 0 平面上的內容就會出現在樓層上。  (0、0、0) 的原點將會是使用者在房間設定期間勇敢面對考驗的特定位置，而-Z 代表在安裝期間所面對的正向方向。

**命名空間：** *UnityEngine。 XR*<br>
**類型：** *界限*

在腳本程式碼中，您可以呼叫 UnityEngine 的 TryGetGeometry 方法，以取得界限多邊形，並指定 TrackedArea 的界限類型。 如果使用者定義了界限 (您會收到一份頂點) 清單，您知道可以安全地將 **房間規模的體驗** 提供給使用者，讓他們可以在您所建立的場景周圍四處進行。

請注意，當使用者進行方法時，系統會自動呈現界限。 您的應用程式不需要使用此多邊形來呈現界限本身。 不過，您可以選擇使用此界限多邊形來配置場景物件，以確保使用者可以在不 teleporting 的情況下，實際觸及這些物件：

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>打造全球規模的體驗

**命名空間：** *UnityEngine. XR*<br>
**類型：** *WorldAnchor*

若要在 HoloLens 上讓使用者穿梭超過5個度量的真實 **世界規模體驗** ，您將需要新的技術，而不是用於會議室規模的體驗。 您將使用的一項重要技巧是建立 [空間錨點](../../design/coordinate-systems.md#spatial-anchors) ，以在實體世界中精確地鎖定全像地理位置的叢集，而不論使用者漫遊的程度為何，然後 [在後續的會話中再次尋找這些影像](../../design/coordinate-systems.md#spatial-anchor-persistence)。

在 Unity 中，您可以藉由將 **WorldAnchor** Unity 元件新增至 GameObject 來建立空間錨點。

### <a name="adding-a-world-anchor"></a>新增世界錨點

若要新增世界錨點，請 <WorldAnchor> 使用您要錨定到真實世界的轉換，在遊戲物件上呼叫 AddComponent ( # A1。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

這樣就完成了！ 此遊戲物件現在會錨定在實體世界中的目前位置，您可能會看到其 Unity 全局座標在一段時間後會稍微調整，以確保實體對齊。 使用 [持續](persistence-in-unity.md) 性，在未來的應用程式會話中再次尋找此錨定的位置。

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

有時會立即找到錨點。 在此情況下，當 AddComponent ( # A1 傳回時，錨點的這個 isLocated 屬性會設定為 true <WorldAnchor> 。 因此，將不會觸發 OnTrackingChanged 事件。 清除模式是在附加錨點之後，以初始 IsLocated 狀態呼叫您的 OnTrackingChanged 處理常式。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>跨裝置共用錨點

您可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> ，從本機 WorldAnchor 建立持久的雲端錨點，讓您的應用程式可在多個 HoloLens、IOS 和 Android 裝置上找到。  藉由在多個裝置上共用一般空間錨點，每個使用者都可以在相同的實體位置中看到相對於該錨點轉譯的內容。  這可提供即時共用體驗。

若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。

在您啟動並執行 Azure 空間錨點之後，您可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實核心構成要素。 您可以從這裡繼續進行下一個組建區塊：

> [!div class="nextstepaction"]
> [目光](gaze-in-unity.md)

或跳至混合的現實平臺功能和 Api：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您隨時都可以回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks) 。

## <a name="see-also"></a>另請參閱
* [體驗規模調整](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空間階段](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的追蹤遺失](tracking-loss-in-unity.md)
* [空間錨點](../../design/spatial-anchors.md)
* [Unity 中的持續性](persistence-in-unity.md)
* [Unity 中的共用體驗](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a>
