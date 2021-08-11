---
title: 案例研究-在具有不同效能的裝置間調整 Datascape
description: 此案例研究可讓您深入瞭解 Microsoft 開發人員如何將 Datascape 應用程式優化，以在具有各種效能功能的裝置上提供引人注目的體驗。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式耳機，效能優化，VR，個案研究
ms.openlocfilehash: d1c54f5fbe6843f9bf61af20b611c6aeb22b0704c209bfdb555fe57b95805cf9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195756"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>案例研究-在具有不同效能的裝置間調整 Datascape

Datascape 是在 Microsoft 內部開發的 Windows Mixed Reality 應用程式，我們著重于將天氣資料顯示在地形資料上方。 應用程式會利用全像資料視覺效果，來探索使用者在混合現實中探索資料所得到的獨特見解。

針對 Datascape，我們想要以各種不同硬體功能為目標的平臺，範圍從 Microsoft HoloLens 到 Windows Mixed Reality 沉浸式耳機，以及從較低電源的電腦到具有高階 GPU 的最新電腦。 主要的挑戰是在以高幀速度執行的裝置上，以美觀的圖形功能來呈現場景，以視覺上吸引人的方式呈現。

本案例研究將逐步解說用來建立一些更多 GPU 密集型系統的程式和技術，以描述我們遇到的問題，以及我們如何克服了它們。

## <a name="transparency-and-overdraw"></a>透明度和過度繪製

我們的主要轉譯掙扎會處理透明度，因為透明度在 GPU 上可能很昂貴。

在寫入深度緩衝區時，可以將穩固幾何轉譯為正面，以停止在該圖元後方捨棄的任何未來圖元。 這可防止隱藏的圖元執行圖元著色器，大幅加快進程的速度。 如果幾何是以最佳方式排序，畫面上的每個圖元只會繪製一次。

透明幾何必須重新排序為 front，並且依賴將圖元著色器的輸出與螢幕上目前的圖元混合。 這可能會導致畫面上的每個圖元每個畫面格繪製到多次，稱為過度繪製。

針對 HoloLens 和主流的電腦，畫面只能填滿幾次，使透明呈現有問題。

## <a name="introduction-to-datascape-scene-components"></a>Datascape 場景元件簡介

我們的場景有三個主要元件; **UI、地圖** 和 **天氣**。 我們提早知道，我們的氣象效應會需要所有可能取得的 GPU 時間，因此我們刻意以可減少任何過度繪製的方式來設計 UI 和地形。

我們已修改 UI 數次，以將所產生的過度繪製量降至最低。 我們大錯特錯人了更複雜幾何的側邊，而不是針對發光按鈕和地圖總覽等元件，在彼此之上重迭透明圖案。

針對地圖，我們使用自訂著色器來去除標準 Unity 功能（例如陰影和複雜光源），並以簡單的單一 sun 光源模型和自訂的霧化計算來取代它們。 這會產生簡單的圖元著色器，並釋出 GPU 週期。

我們管理的是要讓 UI 和地圖在預算中轉譯，而不需要根據硬體進行任何變更;不過，特別是雲端轉譯的氣象視覺效果已證明是一項挑戰！

## <a name="background-on-cloud-data"></a>雲端資料的背景

我們的雲端資料是從 NOAA 伺服器下載 (https://nomads.ncep.noaa.gov/) ，並在三個不同的2d 層中提供，每個都有雲端的最上層和下高度，以及格線的每個資料格的雲端密度。 資料會被處理到雲端資訊材質中，其中每個元件都儲存在材質的紅色、綠色和藍色元件中，以方便在 GPU 上進行存取。

## <a name="geometry-clouds"></a>幾何雲端

為了確保我們的較低電源電腦可以轉譯我們的雲端，我們決定以使用穩固幾何來將過度繪製降到最低的方法開始。

我們首先嘗試產生雲端，方法是使用每個頂點的雲端資訊材質半徑來產生圖形，以產生每個圖層的穩固 heightmap 網格。 我們使用幾何著色器在雲端的頂端和底部產生頂點，以產生穩固的雲端圖形。 我們使用紋理的密度值，以較深的色彩針對較密集的雲端來為雲端上色。

**用來建立頂點的著色器：**

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

我們引進了一個小型的雜訊模式，以取得實際資料的詳細資料。 若要產生圓形的雲端邊緣，我們會在插補半徑值達到閾值時，裁剪圖元著色器中的圖元以捨棄接近零的值。

![幾何雲端](images/datascape-geometry-clouds-700px.jpg)

由於雲端是穩固幾何，因此可以在地形之前轉譯，以在下方隱藏任何昂貴的地圖圖元，以進一步改善幀速度。 此解決方案可在最小規格至高端圖形卡片的所有圖形卡上執行，以及在 HoloLens 上，因為有固態的幾何呈現方法。

## <a name="solid-particle-clouds"></a>穩固的粒子雲

我們現在有一個備份解決方案，可為雲端資料產生適當的標記法，但有點 lackluster 「wow」因素，而且無法傳達我們希望高階機器的體積型感覺。

下一步是以大約100000個粒子來建立雲端，以產生更具有機和體積型的外觀。

如果粒子維持穩固，而且是由前到上排序，我們仍然可以從先前轉譯之粒子背後圖元的深度緩衝區剔除獲益，減少過度繪製。 此外，使用以物件為基礎的解決方案時，我們可以改變用來鎖定不同硬體的粒子量。 不過，所有圖元仍然需要深度測試，這會導致額外的負荷。

首先，我們會在啟動時，于中心點周圍建立物件的位置。 我們在中心分佈了更多密集，而不是距離。 我們會從中心將所有粒子預先排序至背面，以便先轉譯最接近的粒子。

計算著色器會取樣雲端資訊材質，以正確的高度來定位每個物件，並根據密度來色彩。

我們使用 *DrawProcedural* 來呈現四個每個物件，讓物件資料隨時都能留在 GPU 上。

每個物件都包含高度和半徑。 高度是以雲端資訊材質取樣的雲端資料為基礎，而半徑以初始分佈為基礎，其計算方式是將水準距離儲存到最接近的鄰近位置。 四邊形會使用這項資料，以高度作為高度方向，如此一來，當使用者水準查看時，就會顯示高度，而且當使用者從上往下查看時，會涵蓋其鄰近專案之間的區域。

![物件圖形](images/particle-shape-700px.png)

**顯示分佈的著色器程式碼：**

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

由於我們會將粒子向前排序，而我們仍然使用穩固的樣式著色器來裁剪 (而不是 blend) 透明圖元，這項技術會處理令人驚訝的粒子量，即使在較低的電腦上，也能避免過度耗用成本。

## <a name="transparent-particle-clouds"></a>透明粒子雲端

穩固的粒子提供了良好的雲端圖形外觀，但仍需要一些東西來銷售 fluffiness 的雲端。 我們決定嘗試自訂解決方案，讓我們可以在其中引進透明的高階圖形卡。

若要這樣做，我們只需切換粒子的初始排序次序，並將著色器變更為使用紋理 Alpha。

![Fluffy 雲端](images/fluffy-clouds-700px.jpg)

它看起來很不錯，但卻證明太過繁重的機器，因為它會導致畫面上的每個圖元呈現數百次！

## <a name="render-off-screen-with-lower-resolution"></a>以較低的解析度呈現關閉畫面

為了減少雲端所呈現的圖元數目，我們開始將它們轉譯成四分之一解析度緩衝區 (相較于螢幕) ，並在繪製所有的粒子之後，將結束結果延展到畫面上。 這讓我們大致上有4x 的速度，但是有幾點需要注意。

**用來呈現非畫面的程式碼：**

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

首先，當轉譯成非螢幕的緩衝區時，我們會遺失主要場景的所有深度資訊，導致山脈呈現在山區上方。

其次，延伸緩衝區也會在我們的雲端邊緣上引進瞭解決方式變更明顯的成品。 接下來的兩節將討論我們如何解決這些問題。

## <a name="particle-depth-buffer"></a>粒子深度緩衝區

為了讓物件與世界幾何並存，其中的山或物件可以涵蓋其背後的粒子，我們已使用深度緩衝區（包含主要場景的幾何）來擴展非螢幕緩衝區。 為了產生這樣的深度緩衝區，我們建立了第二個相機，只轉譯場景的穩固幾何和深度。

接著，我們會在雲端的圖元著色器中使用新材質來遮蔽圖元。 我們使用相同的材質來計算與雲端圖元背後幾何之間的距離。 藉由使用該距離並將其套用至圖元的 Alpha，我們現在會在接近地形的情況下，將雲端的效果淡出，以移除任何與粒子和地形符合的硬性剪下。

![混合到地形的雲端](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>將邊緣銳化

向上延展的雲端幾乎與位於粒子中央或它們重迭的一般大小雲端完全相同，但會顯示在雲端邊緣的一些構件。 否則，當相機移動時，會出現清晰的邊緣，並引進別名效果。

我們藉由在非螢幕緩衝區上執行簡單的著色器來解決這種情況，以判斷在 (1) 中發生重大變更的情況。 我們會將大幅變更的圖元放入新的樣板緩衝區 (2) 。 然後，在將螢幕上的緩衝區套用回畫面時，我們會使用樣板緩衝區來將這些高對比區域遮罩，而導致雲端中的漏洞 (3) 。

接著，我們會以全螢幕模式再次轉譯所有的粒子，但這次會使用樣板緩衝區來遮蔽所有專案，但不包括邊緣， (4) 觸及最少量的圖元。 由於已為粒子建立命令緩衝區，因此我們只需要將它再次轉譯至新的相機。

![呈現雲端邊緣的進展](images/cloud-steps-1-4-700px.jpg)

最終結果是具有雲端便宜中心區段的尖邊緣。

雖然這比以全螢幕呈現所有的粒子更快，但仍有與針對樣板緩衝區測試圖元相關聯的成本，因此大量的過度繪製仍會產生費用。

## <a name="culling-particles"></a>剔除粒子

針對我們的風效果，我們在計算著色器中產生了長三角形的停車線，並在世界各地建立許多 wisps。 雖然產生的訣竅會導致不高的填滿率，但它產生了數十萬個頂點，導致端點著色器的負載很高。

我們在計算著色器上引進了附加緩衝區，以饋送要繪製的風條紋子集。 有一些簡單的 view 圖分割可在計算著色器中剔除邏輯，我們可以判斷是否有一個帶狀位於相機視圖之外，並防止它新增至推播緩衝區。 這會大幅減少停車量，以釋出 GPU 上的一些必要週期。

**示範附加緩衝區的程式碼：**

*計算著色器：*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C # 程式碼：*

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

我們嘗試在雲端粒子上使用相同的技術，我們會在計算著色器上挑選它們，並且只推送要轉譯的可見粒子。 因為最大的瓶頸是螢幕上呈現的圖元量，而不是計算頂點的成本，所以這項技術實際上不會將我們的 GPU 儲存在 GPU 上。

這項技術的另一個問題是，附加緩衝區是以隨機順序填入，因為它的平行處理本質是計算粒子，導致已排序的粒子未排序，進而導致雲端粒子閃爍。

有幾種方法可以排序推播緩衝區，但我們從「剔除」粒子得到的效能提升數量可能會與其他排序相比，因此我們決定不採用這項優化。

## <a name="adaptive-rendering"></a>適應性呈現

為了確保具有不同轉譯條件的應用程式具有穩定的畫面播放速率，例如，像是模糊的應用程式，我們為應用程式引進了適應性呈現。

適應性呈現的第一個步驟是測量 GPU。 我們的做法是將自訂程式碼插入到轉譯框架開頭和結尾的 GPU 命令緩衝區，並同時捕捉左右的眼睛畫面時間。

藉由測量花費在轉譯的時間，並將它與我們所需的重新整理率進行比較，我們就能瞭解我們要如何接近畫面。

當您接近放置框架時，我們會調整轉譯以使其更快。 調整的一個簡單方式，就是變更畫面的區大小，需要較少的圖元來呈現。

藉由使用 *UnityEngine. XR. XRSettings. renderViewportScale* ，系統會壓縮目標的區隔，並自動將結果縮小以符合螢幕。 小規模的小小變更對世界幾何而言並沒有明顯的影響，而縮放比例為0.7 則需要呈現的圖元數一半。

![70% 的刻度，一半的圖元](images/datascape-scaling-700px.jpg)

當我們偵測到我們即將卸載畫面格時，我們會以固定的數位減少尺規，並在執行速度夠快時將其增加回來。

雖然我們決定在啟動時以硬體的圖形功能為基礎所要使用的雲端技術，但您可以將它作為 GPU 測量資料的基礎，以防止系統長期保持低解析度，但這是我們沒有時間在 Datascape 中探索的問題。

## <a name="final-thoughts"></a>最後的想法

以各種不同的硬體為目標是一項挑戰，需要進行一些規劃。

建議您以較低電源的電腦為目標，以熟悉問題空間並開發將在所有機器上執行的備份解決方案。 請考慮使用填滿率來設計您的解決方案，因為圖元會是您最珍貴的資源。 透明上的目標穩固幾何。

有了備份解決方案之後，您就可以在高階電腦上更複雜地開始分層，也可以增強備份解決方案的解析度。

設計最糟的案例，而且可能會考慮在繁重的情況下使用適應性呈現。

## <a name="about-the-authors"></a>關於作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>軟體工程師 @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>軟體工程師 @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>另請參閱
* [瞭解混合現實的效能](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity 的效能建議](../develop/unity/performance-recommendations-for-unity.md)

 
