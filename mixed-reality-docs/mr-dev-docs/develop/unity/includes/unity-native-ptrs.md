---
ms.openlocfilehash: 78296dd4e6667c34926c954774547b21a223c5f4b6635476c51046c7ca22cdc3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208396"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**命名空間：** *MixedReality。 WindowsMixedReality*<br>
**類型：** *WindowsMixedRealityUtilities*

MRTK 透過 **WindowsMixedRealityUtilities** 類別，在舊版的 WSA 和 XR SDK 之間提供已封送處理的類型。

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**命名空間：** *UnityEngine. XR. WindowsMR*<br>
**類型：** *WindowsMREnvironment*

靜態 **WindowsMREnvironment** 類別可讓您存取數個原生指標。

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**命名空間：** *UnityEngine. XR*<br>
**類型：** *XRDevice*

<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a>型別可讓您使用 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法來存取基礎原生物件。 不同平臺之間的 GetNativePtr 傳回會有所不同。 在以 Windows Mixed Reality 為目標的通用 Windows 平臺上，XRDevice. GetNativePtr 會傳回指標 (IntPtr) 至下列結構：

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

您可以使用 PtrToStructure 方法將它轉換成 HolographicFrameNativeData：

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** 是已封送處理為 Unmanagedtype.lpwstr 的 IntPtr 陣列，其長度等於 MaxNumberOfCameras*
