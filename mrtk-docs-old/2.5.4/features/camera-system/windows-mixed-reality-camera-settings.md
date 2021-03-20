---
title: WindowsMixedRealityCameraSettings
description: 在 MRTK 中使用 Windows Mixed Reality 攝影機的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、攝影機、
ms.openlocfilehash: a5d261d7ccadcd47b1697dd78f74013a343d1bbc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683061"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality 相機設定提供者

Windows Mixed Reality 相機設定提供者會決定裝置的類型，應用程式會在該裝置上執行，並根據顯示 (透明或不透明) 來套用適當的設定。

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>啟用 Windows Mixed Reality 相機設定提供者

下列步驟假設使用 MixedRealityToolkit 物件。 其他服務註冊機構所需的步驟可能會不同。

1. 選取場景階層中的 MixedRealityToolkit 物件。

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

2. 將 [偵測器] 面板移至 [相機系統] 區段，然後展開 [ **相機設定提供者** ] 區段。

    ![展開設定提供者](../images/camera-system/ExpandProviders.png)

3. 按一下 [新增 **相機設定提供者** ]，並展開新加入的 **新相機設定** 專案。

    ![展開新的設定提供者](../images/camera-system/ExpandNewProvider.png)

4. 選取 Windows Mixed Reality 相機設定提供者

    ![選取 Windows Mixed Reality 設定提供者](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> 使用 Microsoft Mixed Reality 工具組預設設定檔時，將會啟用並設定 Windows Mixed Reality 相機設定提供者。

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>設定 Windows Mixed Reality 相機設定提供者

Windows Mixed Reality 攝影機設定也支援設定檔。 此設定檔提供下列選項：

![Windows Mixed Reality 攝影機設定](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>從相片/攝影機轉譯混合現實 capture

當 HoloLens 2 上的這項設定時，您可以在混合現實的捕獲中啟用全像對齊。 如果啟用，平臺會在進行混合現實的拍攝相片或影片時，為應用程式提供額外的 HolographicCamera。 此 HolographicCamera 會提供對應至相片/攝影機位置的視圖矩陣，並使用 [相片/攝影機] 欄位提供投射矩陣。 這可確保在影片輸出中保持一致的全像影像，例如手形網格。

### <a name="hololens-2-reprojection-method"></a>HoloLens 2 reprojection 方法

設定 HoloLens 2 reprojection 的初始方法。 預設的建議是使用深度 reprojection，因為場景的所有部分都會根據與使用者的距離而獨立地穩定。 如果不穩定的全像是，請嘗試確保所有物件都已正確地將其深度提交至深度緩衝區。 這有時是著色器設定。 如果深度看似正確提交，而且仍然存在不穩定的情況下，請嘗試使用深度緩衝區來計算穩定平面的 autoplanar 穩定。 如果應用程式無法為其中一個選項提交足夠的深度資料可供使用，則會提供平面 reprojection 做為回復。 這個方法會以應用程式透過 [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)提供的焦點資料為基礎。

若要在執行時間更新 reprojection 方法，請存取， `WindowsMixedRealityReprojectionUpdater` 如下所示：

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

這只需要更新一次，而且會針對所有後續的框架重複使用該值。 如果方法會經常更新，建議您快取的結果， `EnsureComponent` 而不是經常呼叫它。

## <a name="see-also"></a>另請參閱

- [攝影機系統總覽](camera-system-overview.md)
- [建立相機設定提供者](create-settings-provider.md)
- [從 PV 攝影機轉譯混合實境擷取](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [全像 reprojection](https://docs.microsoft.com/windows/mixed-reality/hologram-stability#reprojection)
