---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636281"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

使用 MRTK for Unity 中的 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 類別，並將 **目標縮放** 設定為 [已 **安裝**]：

![MRTK 設定視窗](../../images/mrtk-target-scale.png)

MRTK 應該會自動處理 playspace 和相機的位置，但最好再次檢查：

![MRTK playspace](../../images/mrtk-playspace.png)

1. 從 [階層 **] 面板中，展開 [** **MixedRealityPlayspace** ] GameObject，並尋找 [ **主要攝影機** ] 子物件
2. 在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 變更為 **(X：0，Y：0，Z： 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上設定追蹤原始模式。 取得子系統之後，請呼叫 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

並使用 Unity 的 [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)。

![階層中的 XR rig](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. 移至 **Windows Store Player 設定** 的 [**其他設定**] 區段
2. 選擇 [ **Windows Mixed Reality** ] 作為裝置，可能會列為舊版 Unity 的 **Windows** 全像攝影版
3. 選取 **支援的虛擬實境**

由於主攝影機物件會自動標記為相機，因此 Unity 可支援所有移動和轉譯。

>[!NOTE]
>這些設定必須套用至應用程式每個場景中的相機。
>
>依預設，當您在 Unity 中建立新場景時，它會包含階層中的主要攝影機 GameObject，其中包括相機元件，但未正確套用下列設定。

**命名空間：** *UnityEngine. XR*<br>
**類型：** *XRDevice*

若要建立 **僅限方向** 或內部 **規模的體驗**，您必須將 Unity 設定為「固定追蹤空間」類型。 固定追蹤空間會設定 Unity 的全局座標系統，以追蹤 [固定的參考框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。 在「固定追蹤」模式中，放在「相機」預設位置前方之編輯器中的內容 (轉寄是-Z) 將會在應用程式啟動時出現在使用者前面。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**命名空間：** *UnityEngine. XR*<br>
**類型：** *InputTracking*

若要取得純 **方向的體驗** （例如360度的影片檢視器） (其中的位置標頭更新會使假像) 損毀，您可以接著設定 [XR。InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 至 true：

```cs
InputTracking.disablePositionalTracking = true;
```

針對內部 **規模的體驗**，讓使用者稍後 recenter 已安裝的來源，您可以呼叫 [XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法：

```cs
InputTracking.Recenter();
```

如果您要建立 [大規模的體驗](../../../../design/coordinate-systems.md)，您可以藉由呼叫 XR，在使用者目前的標頭位置 recenter Unity 的世界原點 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。