---
ms.openlocfilehash: 78596197af6c2e7c329e7a7c99281f8debee13b973a212709f5be1ec34e04eea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212230"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

遵循這個 [逐步教學](../../tutorials/mr-learning-base-01.md) 課程，在您的 Unity 專案中新增和自動設定混合現實工具組。 您也可以直接從 MRTK for Unity 使用 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 類別，並將 **目標規模** 設定為 **World**：

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
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

您可以使用[ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation)進行 HoloLens 的應用程式，其可搭配錨點和 ARKit/ARCore 更好用。

![階層中的 AR 會話](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> AR 會話和相關功能需要已安裝 AR Foundation。

您也可以手動套用相機變更，而不需要使用 ARSession：

1. 選取 **[階層**] 面板中的 [**主要攝影機**]
1. 在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 變更為 **(X：0，Y：0，Z： 0)**

   ![Unity 中的 [偵測器] 窗格中的相機](../../images/maincamera-350px.png)  
   *Unity 中的 [偵測器] 窗格中的相機*

1. 將 **TrackedPoseDriver** 新增至 **主要攝影機**

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. 選取 **[階層**] 面板中的 [**主要攝影機**]
1. 在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 變更為 **(X：0，Y：0，Z： 0)**

   ![Unity 中的 [偵測器] 窗格中的相機](../../images/maincamera-350px.png)  
   *Unity 中的 [偵測器] 窗格中的相機*

1. 移至 **Windows 存放區播放** 程式的 **其他設定** 區段設定
1. 選擇 [ **Windows Mixed Reality** ] 作為裝置，可能會列為舊版 Unity 中的 **Windows 全息** 版
1. 選取 **支援的虛擬實境**

由於主攝影機物件會自動標記為相機，因此 Unity 可支援所有移動和轉譯。

>[!NOTE]
>這些設定必須套用至應用程式每個場景中的相機。
>
>依預設，當您在 Unity 中建立新場景時，它會包含階層中的主要攝影機 GameObject，其中包括相機元件，但可能未正確套用設定。