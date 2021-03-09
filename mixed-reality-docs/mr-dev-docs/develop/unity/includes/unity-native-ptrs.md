---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475070"
---
# <a name="mrtk"></a>[<span data-ttu-id="4534d-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="4534d-101">MRTK</span></span>](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a><span data-ttu-id="4534d-102">WindowsMixedRealityUtilities</span><span class="sxs-lookup"><span data-stu-id="4534d-102">WindowsMixedRealityUtilities</span></span>

<span data-ttu-id="4534d-103">**命名空間：** *MixedReality。 WindowsMixedReality*</span><span class="sxs-lookup"><span data-stu-id="4534d-103">**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*</span></span><br>
<span data-ttu-id="4534d-104">**類型：** *WindowsMixedRealityUtilities*</span><span class="sxs-lookup"><span data-stu-id="4534d-104">**Type:** *WindowsMixedRealityUtilities*</span></span>

<span data-ttu-id="4534d-105">MRTK 透過 **WindowsMixedRealityUtilities** 類別，在舊版的 WSA 和 XR SDK 之間提供已封送處理的類型。</span><span class="sxs-lookup"><span data-stu-id="4534d-105">MRTK provides already-marshalled types across both legacy WSA and XR SDK through the **WindowsMixedRealityUtilities** class.</span></span>

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[<span data-ttu-id="4534d-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="4534d-106">XR SDK</span></span>](#tab/xr)

## <a name="windowsmrenvironment"></a><span data-ttu-id="4534d-107">WindowsMREnvironment</span><span class="sxs-lookup"><span data-stu-id="4534d-107">WindowsMREnvironment</span></span>

<span data-ttu-id="4534d-108">**命名空間：** *UnityEngine. XR. WindowsMR*</span><span class="sxs-lookup"><span data-stu-id="4534d-108">**Namespace:** *UnityEngine.XR.WindowsMR*</span></span><br>
<span data-ttu-id="4534d-109">**類型：** *WindowsMREnvironment*</span><span class="sxs-lookup"><span data-stu-id="4534d-109">**Type:** *WindowsMREnvironment*</span></span>

<span data-ttu-id="4534d-110">靜態 **WindowsMREnvironment** 類別可讓您存取數個原生指標。</span><span class="sxs-lookup"><span data-stu-id="4534d-110">The static **WindowsMREnvironment** class provides access to several native pointers.</span></span>

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="4534d-111">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="4534d-111">Legacy WSA</span></span>](#tab/wsa)

## <a name="xrdevice"></a><span data-ttu-id="4534d-112">XRDevice</span><span class="sxs-lookup"><span data-stu-id="4534d-112">XRDevice</span></span>

<span data-ttu-id="4534d-113">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="4534d-113">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="4534d-114">**類型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="4534d-114">**Type:** *XRDevice*</span></span>

<span data-ttu-id="4534d-115"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a>型別可讓您使用 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法來存取基礎原生物件。</span><span class="sxs-lookup"><span data-stu-id="4534d-115">The <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="4534d-116">不同平臺之間的 GetNativePtr 傳回會有所不同。</span><span class="sxs-lookup"><span data-stu-id="4534d-116">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="4534d-117">在以 Windows Mixed Reality 為目標的通用 Windows 平臺上，XRDevice 會將指標 (IntPtr) 傳回至下列結構：</span><span class="sxs-lookup"><span data-stu-id="4534d-117">On the Universal Windows Platform when targeting Windows Mixed Reality, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span>

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame
    public IntPtr IHolographicCameraPtr; // Windows::Graphics::Holographic::IHolographicCamera
}
```

<span data-ttu-id="4534d-118">您可以使用 PtrToStructure 方法將它轉換成 HolographicFrameNativeData：</span><span class="sxs-lookup"><span data-stu-id="4534d-118">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

<span data-ttu-id="4534d-119">***IHolographicCameraPtr** 是已封送處理為 Unmanagedtype.lpwstr 的 IntPtr 陣列，其長度等於 MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="4534d-119">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span>
