---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636279"
---
# <a name="mrtk"></a>[<span data-ttu-id="05daa-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="05daa-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="05daa-102">MRTK 會根據 [相機系統設定檔中](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)的設定，自動處理特定的相機設定。</span><span class="sxs-lookup"><span data-stu-id="05daa-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="05daa-103">**命名空間：** *MixedReality。 CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="05daa-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="05daa-104">**類型：** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="05daa-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="05daa-105">若要檢查攝影機的 opaqueness，MixedRealityCamera 系統有 [一個 `IsOpaque` 屬性](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)。</span><span class="sxs-lookup"><span data-stu-id="05daa-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="05daa-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="05daa-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="05daa-107">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="05daa-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="05daa-108">**類型：** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="05daa-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="05daa-109">您可以使用腳本，在執行時間判斷耳機是否為沉浸式或全像，方法是在主動執行的[XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)上檢查[displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) 。</span><span class="sxs-lookup"><span data-stu-id="05daa-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="05daa-110">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="05daa-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="05daa-111">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="05daa-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="05daa-112">**類型：** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="05daa-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="05daa-113">您可以藉由檢查 [HolographicSettings IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)，使用腳本來判斷耳機是否為沉浸式或全像攝影。</span><span class="sxs-lookup"><span data-stu-id="05daa-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>