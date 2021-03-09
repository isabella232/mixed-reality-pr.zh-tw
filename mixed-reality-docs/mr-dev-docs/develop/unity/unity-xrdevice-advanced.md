---
title: Unity 中的混合實境原生物件
description: 瞭解如何使用 XR 命名空間，取得 Unity 中基礎全像原生物件的存取權。
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: unity、mixed reality、native、xrdevice、spatialcoordinatesystem、holographicframe、holographiccamera、ispatialcoordinatesystem、iholographicframe、iholographiccamera、getnativeptr、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475069"
---
# <a name="mixed-reality-native-interop-in-unity"></a>Unity 中的混合現實原生 interop

每個混合現實應用程式都會在開始接收攝影機資料和轉譯畫面之前 [取得 HolographicSpace](../native/getting-a-holographicspace.md) 。 在 Unity 中，引擎會為您處理這些步驟，並在其轉譯迴圈中處理全像攝影物件和內部更新。

不過，在 advanced 案例中，您可能需要取得基礎原生物件的存取權，例如 <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> 和目前的 <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>。

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>封送原生指標

`IntPtr`從上述其中一個方法取得之後 (不需要 MRTK) ，請使用下列程式碼片段將其封送處理至 managed 物件。

如果您使用的是 [MixedReality DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)，您可以使用方法，從原生指標建立 managed 物件 `FromNativePtr()` ：

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

否則，請使用 `Marshal.GetObjectForIUnknown()` 並轉換成您想要的類型：

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
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
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(q.X, q.Y, -q.Z, -q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(q.x, q.y, -q.z, -q.w);
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

如果您需要存取原生介面以進行轉譯或偵錯工具，請使用原生外掛程式或 c # 程式碼中 HolographicFrameNativeData 的資料。

以下範例示範如何使用 HolographicFrameNativeData，以使用 XR SDK 延伸模組取得目前框架的 photon 時間預測。

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if ENABLE_WINMD_SUPPORT
    IntPtr holographicFramePtr = UnityEngine.XR.WindowsMR.WindowsMREnvironment.CurrentHolographicRenderFrame;

    if (holographicFramePtr != IntPtr.Zero)
    {
        var holographicFrame = Marshal.GetObjectForIUnknown(holographicFramePtr) as Windows.Graphics.Holographic.HolographicFrame;
        frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
        return true;
    }
#endif

    frameDateTime = DateTime.MinValue;
    return false;
}
```

## <a name="see-also"></a>另請參閱

* [搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [DirectX 中的呈現](../native/rendering-in-directx.md)
