---
ms.openlocfilehash: d30bf4b5c382ca953314996dd51087427224e872158b607fd1c5f4c85c62a124
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212236"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK 目前沒有 reprojection 模式的協助程式。 如需詳細資訊，請參閱其中一個其他索引標籤。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Reprojection 模式可透過將 [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) 設定為適當的值來進行設定。

例如，如果您要建立具有嚴格內文鎖定內容的 [僅限方向體驗](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) (例如，360度的影片內容) ，您只能將 reprojection 模式設定為 [ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)，以明確地將其設定為方向。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Reprojection 模式可透過將 [HolographicSettings](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 設定為適當的值來進行設定。

例如，如果您要建立具有嚴格內文鎖定內容的 [僅限方向體驗](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) (例如，360度的影片內容) ，您只能將 reprojection 模式設定為 [HolographicReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)，以明確地將其設定為方向。