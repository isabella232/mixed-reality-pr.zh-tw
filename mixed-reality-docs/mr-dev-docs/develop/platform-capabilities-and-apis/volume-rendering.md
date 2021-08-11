---
title: 磁碟區呈現
description: 瞭解如何在 Windows Mixed Reality 中有效率地轉譯具有不透明度和色彩的豐富體積型影像。
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 體積型映射，磁片區轉譯，效能，混合現實
ms.openlocfilehash: 3843f0f4e49a0564b41d834231630d281aa9e874df8d35c4feaa4fe5bba0ed68
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220925"
---
# <a name="volume-rendering"></a>磁碟區呈現

若為醫療 MRI 或工程量，請參閱 [維琪百科上的磁片](https://en.wikipedia.org/wiki/Volume_rendering)區轉譯。 這些「體積型影像」包含豐富的資訊，在整個磁片區中都不會有不透明度和色彩，而無法輕易地表示為 [多邊形網格](https://en.wikipedia.org/wiki/Polygon_mesh)之類的表面。

改善效能的關鍵解決方案
1. 錯誤：不完整的方法：顯示整個磁片區，通常執行速度太慢
2. 良好：剪下平面：只顯示磁片區的單一配量
3. 良好：剪下的子卷：只顯示磁片區的幾個圖層
4. 良好：降低磁片區轉譯的解析度 (請參閱「混合解析度場景轉譯」 ) 

只有特定數量的資訊可以從應用程式傳輸到任何特定畫面格的螢幕，也就是總記憶體頻寬。 此外，轉換資料以進行呈現所需的任何處理 (或「陰影」 ) 都需要時間。 進行磁片區轉譯時的主要考慮如下：
* Screen-Width * Screen-Height * Screen-Count * 磁片區-每個畫面的單位-圖元 = 總數量-樣本數
* 1028 * 720 * 2 * 256 = 378961920 (100% )  (完整 res 磁片區：太多樣本) 
* 1028 * 720 * 2 * 1 = 1480320 (0.3% 的完整)  (精簡配量：每圖元一個樣本，可順暢地執行) 
* 1028 * 720 * 2 * 10 = 14803200 (3.9% 的完整)  (subvolume 配量：每圖元10個樣本、相當順暢地執行，並以3d 顯示) 
* 200 * 200 * 2 * 256 = 20480000 (5% 的完整)  (較低的 res 磁片區：較少的圖元、完整磁片區，看起來是3d，但有點模糊) 

## <a name="representing-3d-textures"></a>代表3D 紋理

CPU：

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

在 GPU 上：

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>陰影和漸層

如何針對有用的視覺效果，為磁片區（例如 MRI）加上陰影。 主要方法是讓「濃度視窗」 (您想要在其中查看濃度的最小和最大) ，並只是調整到該空間以查看黑色和白色濃度。 然後，您可以將「色彩斜接」套用到該範圍內的值，並儲存為材質，讓濃度色譜的不同部分可以用陰影呈現不同的色彩：

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

在我們的許多應用程式中，我們會將原始強度值和「分割索引」 (儲存在分割不同部分（例如面板和骨骼）的磁片區中;這些區段是由專家在專用工具) 中建立的。 這可以與上面的方法結合，以針對每個區段索引放置不同的色彩，或甚至不同的顏色斜坡：

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>著色器中的磁片區切割

最好的第一個步驟是建立可在磁片區中移動的「切割平面」、「切割 it」，以及每個時間點的掃描值。 這假設有一個「VolumeSpace」 cube，代表磁片區位於世界空間的位置，可用來做為放置點數的參考：

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>著色器中的磁片區追蹤

如何使用 GPU 來執行 subvolume 追蹤 (會逐步解說幾個體素，然後將資料上的分層移回前端) ：

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>整個磁片區轉譯

修改上述的 subvolume 程式碼，我們取得：

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>混合解析度場景轉譯

如何呈現低解析度的場景部分，並將它放回原位：
1. 設定兩個非全螢幕攝影機，每個畫面都要跟著更新每個畫面格的每一眼
2. 設定兩個低解析度轉譯目標 (也就是200x200 攝影機轉譯的每個) 
3. 設定在使用者前方移動的四個四個

每個畫面格：
1. 在低解析度 (磁片區資料、昂貴的著色器等) 上繪製每個眼睛的呈現目標
2. 以完整解析度的方式繪製場景， (網格、UI 等等) 
3. 在使用者前方、場景上繪製四個四個專案，然後將低 res 轉譯至
4. 結果：具有低解析度但高密度磁片區資料的完整解析度元素的視覺化組合
