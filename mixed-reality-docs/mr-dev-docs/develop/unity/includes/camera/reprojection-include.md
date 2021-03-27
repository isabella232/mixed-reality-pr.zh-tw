---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636278"
---
# <a name="mrtk"></a>[<span data-ttu-id="40569-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="40569-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="40569-102">MRTK 目前沒有 reprojection 模式的協助程式。</span><span class="sxs-lookup"><span data-stu-id="40569-102">MRTK doesn't currently have helpers for the reprojection mode.</span></span> <span data-ttu-id="40569-103">如需詳細資訊，請參閱其中一個其他索引標籤。</span><span class="sxs-lookup"><span data-stu-id="40569-103">Please see one of the other tabs for more information.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="40569-104">XR SDK</span><span class="sxs-lookup"><span data-stu-id="40569-104">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="40569-105">Reprojection 模式可透過將 [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) 設定為適當的值來進行設定。</span><span class="sxs-lookup"><span data-stu-id="40569-105">The reprojection mode is configurable by setting [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="40569-106">例如，如果您要建立具有嚴格內文鎖定內容的 [僅限方向體驗](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) (例如，360度的影片內容) ，您只能將 reprojection 模式設定為 [ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)，以明確地將其設定為方向。</span><span class="sxs-lookup"><span data-stu-id="40569-106">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="40569-107">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="40569-107">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="40569-108">Reprojection 模式可透過將 [HolographicSettings](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 設定為適當的值來進行設定。</span><span class="sxs-lookup"><span data-stu-id="40569-108">The reprojection mode is configurable by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="40569-109">例如，如果您要建立具有嚴格內文鎖定內容的 [僅限方向體驗](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) (例如，360度的影片內容) ，您只能將 reprojection 模式設定為 [HolographicReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)，以明確地將其設定為方向。</span><span class="sxs-lookup"><span data-stu-id="40569-109">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>