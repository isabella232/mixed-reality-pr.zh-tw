---
title: Unity 中的混合實境原生物件
description: 取得 Unity 中基礎全息型原生物件的存取權。
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: unity、mixed reality、native、xrdevice、spatialcoordinatesystem、holographicframe、holographiccamera、ispatialcoordinatesystem、iholographicframe、iholographiccamera、getnativeptr、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: a64deb46db82e6d0401a803e45dcbbd854476745
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679927"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Unity 中的混合實境原生物件

[取得 HolographicSpace](../native/getting-a-holographicspace.md) 是每個混合現實應用程式開始接收攝影機資料和轉譯畫面格之前的作用。 在 Unity 中，引擎會為您處理這些步驟，並在其轉譯迴圈中于內部處理全像攝影物件和更新。

不過，在 advanced 案例中，您可能需要取得基礎原生物件的存取權，例如 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> 和目前的 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>。 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> 是提供這些原生物件存取權的物件。

## <a name="xrdevice"></a>XRDevice 

**命名空間：** *UnityEngine. XR*<br>
**類型：** *XRDevice*

*XRDevice* 型別可讓您使用 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法來存取基礎原生物件。 不同平臺之間的 GetNativePtr 傳回會有所不同。 在通用 Windows 平臺上，以 Windows Mixed Reality XR SDK 為目標時，XRDevice. GetNativePtr 會將指標 (IntPtr) 傳回到下列結構： 

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
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
您可以使用 PtrToStructure 方法將它轉換成 HolographicFrameNativeData：
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** 是已封送處理為 Unmanagedtype.lpwstr 的 IntPtr 陣列，其長度等於 MaxNumberOfCameras* 

### <a name="unmarshaling-native-pointers"></a>封送原生指標

如果您使用的是 [MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) ，您可以使用方法，從原生指標建立 managed 物件 `FromNativePtr()` ：

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

否則，請使用 `Marshal.GetObjectForIUnknown()` 並轉換成所需的類型：

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a>在座標系統之間轉換

Unity 使用左手型座標系統，而 Windows 感知 Api 則使用右手座標系統。 若要在這兩個慣例之間轉換，您可以使用下列協助程式：

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a>使用 HolographicFrame 的原生資料

> [!NOTE]
> 變更透過 HolographicFrameNativeData 接收之原生物件的狀態，可能會導致無法預期的行為和轉譯成品，特別是當 Unity 也有相同狀態的原因。  例如，您不應該呼叫 HolographicFrame UpdateCurrentPrediction，否則 Unity 以該畫面格呈現的姿勢預測將會與 Windows 預期的姿勢不同步，這 [會減少全](../platform-capabilities-and-apis/hologram-stability.md)像全像的情況。

當您在原生外掛程式或 c # 程式碼中進行轉譯或偵錯工具時，您可以使用 HolographicFrameNativeData 中的資料來存取原生介面。 

以下範例示範如何使用 HolographicFrameNativeData 取得目前框架的 photon 時間預測。 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a>另請參閱
* [搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [DirectX 中的呈現](../native/rendering-in-directx.md)
