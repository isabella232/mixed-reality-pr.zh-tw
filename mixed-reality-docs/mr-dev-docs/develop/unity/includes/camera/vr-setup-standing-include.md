---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748505"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

使用 MRTK for Unity 的 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 類別，並將 **目標規模** 設定為 **房間** 或 **站**：

![MRTK 設定視窗](../../images/mrtk-target-scale.png)

MRTK 應該會自動處理 playspace 和相機的位置，但最好再次檢查：

![MRTK playspace](../../images/mrtk-playspace.png)

1. 從 [階層 **] 面板中，展開 [** **MixedRealityPlayspace** ] GameObject，並尋找 [ **主要攝影機** ] 子物件
2. 在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 變更為 **(X：0，Y：0，Z： 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上設定追蹤原始模式。 取得子系統之後，請呼叫 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
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

若要獲得 **大規模** 或 **房間規模的體驗**，您必須將內容放在地面的相對位置。 您可以使用 **[空間階段](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**（代表使用者定義的樓層層級來源和選擇性的空間界限），在第一次執行期間設定使用者的樓層。

為了確保 Unity 在地面層級的全局座標系統運作，您可以設定並測試 Unity 是否使用 RoomScale 追蹤空間類型：

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

* 如果 SetTrackingSpaceType 傳回 true，表示 Unity 已成功切換其全局座標系統，以追蹤 [參考的階段框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。
* 如果 SetTrackingSpaceType 傳回 false，則 Unity 無法切換至參考的階段框架，可能是因為使用者未在其環境中設定 floor。 雖然錯誤傳回值並不常見，但如果階段是在不同的房間內設定的，而且裝置會移至目前的房間，而沒有使用者設定新的階段，就可能發生此情況。

一旦您的應用程式成功設定 RoomScale 追蹤空間類型，放在 y = 0 平面上的內容就會出現在樓層上。 0、0、0的原點將是使用者在房間設定期間勇敢面對考驗的特定位置，而-Z 代表在安裝期間所面對的順向方向。