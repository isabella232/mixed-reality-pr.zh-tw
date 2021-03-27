---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636279"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK 會根據 [相機系統設定檔中](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)的設定，自動處理特定的相機設定。

**命名空間：** *MixedReality。 CameraSystem*<br>
**類型：** *MixedRealityCameraSystem*

若要檢查攝影機的 opaqueness，MixedRealityCamera 系統有 [一個 `IsOpaque` 屬性](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)。

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**命名空間：** *UnityEngine. XR*<br>
**類型：** *XRDisplaySubsystem*

您可以使用腳本，在執行時間判斷耳機是否為沉浸式或全像，方法是在主動執行的[XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)上檢查[displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) 。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**命名空間：** *UnityEngine. XR*<br>
**類型：** *HolographicSettings*

您可以藉由檢查 [HolographicSettings IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)，使用腳本來判斷耳機是否為沉浸式或全像攝影。