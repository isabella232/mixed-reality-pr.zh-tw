---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719722"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Mixed Reality OpenXR 外掛程式透過 Unity 的 ARFoundation **ARAnchorManager** 的執行，提供基本錨定功能。 若要瞭解 ARFoundation 中 ARAnchors 的基本概念，請造訪 [AR 錨點管理員的 ARFoundation 手冊](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。 

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 外掛程式](#tab/winxr)

Mixed Reality OpenXR 外掛程式透過 Unity 的 ARFoundation **ARAnchorManager** 的執行，提供基本錨定功能。 若要瞭解 ARFoundation 中 ARAnchors 的基本概念，請造訪 [AR 錨點管理員的 ARFoundation 手冊](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

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