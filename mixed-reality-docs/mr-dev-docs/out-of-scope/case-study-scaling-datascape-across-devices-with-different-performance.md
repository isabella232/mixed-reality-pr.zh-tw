---
title: 案例研究-在具有不同效能的裝置間調整 Datascape
description: 此案例研究可讓您深入瞭解 Microsoft 開發人員如何將 Datascape 應用程式優化，以在具有各種效能功能的裝置上提供引人注目的體驗。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式耳機，效能優化，VR，個案研究
ms.openlocfilehash: 37a40a67dbe41ba9a53fccaff1dee76d56f7b178
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91681101"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="c9efc-104">案例研究-在具有不同效能的裝置間調整 Datascape</span><span class="sxs-lookup"><span data-stu-id="c9efc-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="c9efc-105">Datascape 是在 Microsoft 內部開發的 Windows Mixed Reality 應用程式，我們著重于將天氣資料顯示在地形資料上方。</span><span class="sxs-lookup"><span data-stu-id="c9efc-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="c9efc-106">應用程式會利用全像資料視覺效果，來探索使用者在混合現實中探索資料所得到的獨特見解。</span><span class="sxs-lookup"><span data-stu-id="c9efc-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="c9efc-107">針對 Datascape，我們想要以各種不同硬體功能為目標的平臺，範圍從 Microsoft HoloLens 到 Windows Mixed Reality 沉浸式耳機，以及從較低電源的電腦到具有高階 GPU 的最新電腦。</span><span class="sxs-lookup"><span data-stu-id="c9efc-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="c9efc-108">主要的挑戰是在以高幀速度執行的裝置上，以美觀的圖形功能來呈現場景，以視覺上吸引人的方式呈現。</span><span class="sxs-lookup"><span data-stu-id="c9efc-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="c9efc-109">本案例研究將逐步解說用來建立一些更多 GPU 密集型系統的程式和技術，以描述我們遇到的問題，以及我們如何克服了它們。</span><span class="sxs-lookup"><span data-stu-id="c9efc-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="c9efc-110">透明度和過度繪製</span><span class="sxs-lookup"><span data-stu-id="c9efc-110">Transparency and overdraw</span></span>

<span data-ttu-id="c9efc-111">我們的主要轉譯掙扎會處理透明度，因為透明度在 GPU 上可能很昂貴。</span><span class="sxs-lookup"><span data-stu-id="c9efc-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="c9efc-112">在寫入深度緩衝區時，可以將穩固幾何轉譯為正面，以停止在該圖元後方捨棄的任何未來圖元。</span><span class="sxs-lookup"><span data-stu-id="c9efc-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="c9efc-113">這可防止隱藏的圖元執行圖元著色器，大幅加快進程的速度。</span><span class="sxs-lookup"><span data-stu-id="c9efc-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="c9efc-114">如果幾何是以最佳方式排序，畫面上的每個圖元只會繪製一次。</span><span class="sxs-lookup"><span data-stu-id="c9efc-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="c9efc-115">透明幾何必須重新排序為 front，並且依賴將圖元著色器的輸出與螢幕上目前的圖元混合。</span><span class="sxs-lookup"><span data-stu-id="c9efc-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="c9efc-116">這可能會導致畫面上的每個圖元每個畫面格繪製到多次，稱為過度繪製。</span><span class="sxs-lookup"><span data-stu-id="c9efc-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="c9efc-117">對於 HoloLens 和主流電腦而言，畫面只能填滿幾次，使透明呈現有問題。</span><span class="sxs-lookup"><span data-stu-id="c9efc-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="c9efc-118">Datascape 場景元件簡介</span><span class="sxs-lookup"><span data-stu-id="c9efc-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="c9efc-119">我們的場景有三個主要元件; **UI、地圖** 和 **天氣** 。</span><span class="sxs-lookup"><span data-stu-id="c9efc-119">We had three major components to our scene; **the UI, the map** , and **the weather** .</span></span> <span data-ttu-id="c9efc-120">我們提早知道，我們的氣象效應會需要所有可能取得的 GPU 時間，因此我們刻意以可減少任何過度繪製的方式來設計 UI 和地形。</span><span class="sxs-lookup"><span data-stu-id="c9efc-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="c9efc-121">我們已修改 UI 數次，以將所產生的過度繪製量降至最低。</span><span class="sxs-lookup"><span data-stu-id="c9efc-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="c9efc-122">我們大錯特錯人了更複雜幾何的側邊，而不是針對發光按鈕和地圖總覽等元件，在彼此之上重迭透明圖案。</span><span class="sxs-lookup"><span data-stu-id="c9efc-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="c9efc-123">針對地圖，我們使用自訂著色器來去除標準 Unity 功能（例如陰影和複雜光源），並以簡單的單一 sun 光源模型和自訂的霧化計算來取代它們。</span><span class="sxs-lookup"><span data-stu-id="c9efc-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="c9efc-124">這會產生簡單的圖元著色器，並釋出 GPU 週期。</span><span class="sxs-lookup"><span data-stu-id="c9efc-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="c9efc-125">我們管理的是要讓 UI 和地圖在預算中轉譯，而不需要根據硬體進行任何變更;不過，特別是雲端轉譯的氣象視覺效果已證明是一項挑戰！</span><span class="sxs-lookup"><span data-stu-id="c9efc-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="c9efc-126">雲端資料的背景</span><span class="sxs-lookup"><span data-stu-id="c9efc-126">Background on cloud data</span></span>

<span data-ttu-id="c9efc-127">我們的雲端資料是從 NOAA 伺服器下載 (https://nomads.ncep.noaa.gov/) ，並在三個不同的2d 層中提供，每個都有雲端的最上層和下高度，以及格線的每個資料格的雲端密度。</span><span class="sxs-lookup"><span data-stu-id="c9efc-127">Our cloud data was downloaded from NOAA servers (https://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="c9efc-128">資料會被處理到雲端資訊材質中，其中每個元件都儲存在材質的紅色、綠色和藍色元件中，以方便在 GPU 上進行存取。</span><span class="sxs-lookup"><span data-stu-id="c9efc-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="c9efc-129">幾何雲端</span><span class="sxs-lookup"><span data-stu-id="c9efc-129">Geometry clouds</span></span>

<span data-ttu-id="c9efc-130">為了確保我們的較低電源電腦可以轉譯我們的雲端，我們決定以使用穩固幾何來將過度繪製降到最低的方法開始。</span><span class="sxs-lookup"><span data-stu-id="c9efc-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="c9efc-131">我們首先嘗試產生雲端，方法是使用每個頂點的雲端資訊材質半徑來產生圖形，以產生每個圖層的穩固 heightmap 網格。</span><span class="sxs-lookup"><span data-stu-id="c9efc-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="c9efc-132">我們使用幾何著色器在雲端的頂端和底部產生頂點，以產生穩固的雲端圖形。</span><span class="sxs-lookup"><span data-stu-id="c9efc-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="c9efc-133">我們使用紋理的密度值，以較深的色彩針對較密集的雲端來為雲端上色。</span><span class="sxs-lookup"><span data-stu-id="c9efc-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="c9efc-134">**用來建立頂點的著色器：**</span><span class="sxs-lookup"><span data-stu-id="c9efc-134">**Shader for creating the vertices:**</span></span>

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

<span data-ttu-id="c9efc-135">我們引進了一個小型的雜訊模式，以取得實際資料的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c9efc-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="c9efc-136">若要產生圓形的雲端邊緣，我們會在插補半徑值達到閾值時，裁剪圖元著色器中的圖元以捨棄接近零的值。</span><span class="sxs-lookup"><span data-stu-id="c9efc-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![幾何雲端](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="c9efc-138">由於雲端是穩固幾何，因此可以在地形之前轉譯，以在下方隱藏任何昂貴的地圖圖元，以進一步改善幀速度。</span><span class="sxs-lookup"><span data-stu-id="c9efc-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="c9efc-139">此解決方案在所有圖形配接器上都能順利執行，從最小規格到高階圖形卡片，以及 HoloLens，因為有固態的幾何轉譯方法。</span><span class="sxs-lookup"><span data-stu-id="c9efc-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="c9efc-140">穩固的粒子雲</span><span class="sxs-lookup"><span data-stu-id="c9efc-140">Solid particle clouds</span></span>

<span data-ttu-id="c9efc-141">我們現在有一個備份解決方案，可為雲端資料產生適當的標記法，但有點 lackluster 「wow」因素，而且無法傳達我們希望高階機器的體積型感覺。</span><span class="sxs-lookup"><span data-stu-id="c9efc-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="c9efc-142">下一步是以大約100000個粒子來建立雲端，以產生更具有機和體積型的外觀。</span><span class="sxs-lookup"><span data-stu-id="c9efc-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="c9efc-143">如果粒子維持穩固，而且是由前到上排序，我們仍然可以從先前轉譯之粒子背後圖元的深度緩衝區剔除獲益，減少過度繪製。</span><span class="sxs-lookup"><span data-stu-id="c9efc-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="c9efc-144">此外，使用以物件為基礎的解決方案時，我們可以改變用來鎖定不同硬體的粒子量。</span><span class="sxs-lookup"><span data-stu-id="c9efc-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="c9efc-145">不過，所有圖元仍然需要深度測試，這會導致額外的負荷。</span><span class="sxs-lookup"><span data-stu-id="c9efc-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="c9efc-146">首先，我們會在啟動時，于中心點周圍建立物件的位置。</span><span class="sxs-lookup"><span data-stu-id="c9efc-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="c9efc-147">我們在中心分佈了更多密集，而不是距離。</span><span class="sxs-lookup"><span data-stu-id="c9efc-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="c9efc-148">我們會從中心將所有粒子預先排序至背面，以便先轉譯最接近的粒子。</span><span class="sxs-lookup"><span data-stu-id="c9efc-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="c9efc-149">計算著色器會取樣雲端資訊材質，以正確的高度來定位每個物件，並根據密度來色彩。</span><span class="sxs-lookup"><span data-stu-id="c9efc-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="c9efc-150">我們使用 *DrawProcedural* 來呈現四個每個物件，讓物件資料隨時都能留在 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="c9efc-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="c9efc-151">每個物件都包含高度和半徑。</span><span class="sxs-lookup"><span data-stu-id="c9efc-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="c9efc-152">高度是以雲端資訊材質取樣的雲端資料為基礎，而半徑以初始分佈為基礎，其計算方式是將水準距離儲存到最接近的鄰近位置。</span><span class="sxs-lookup"><span data-stu-id="c9efc-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="c9efc-153">四邊形會使用這項資料，以高度作為高度方向，如此一來，當使用者水準查看時，就會顯示高度，而且當使用者從上往下查看時，會涵蓋其鄰近專案之間的區域。</span><span class="sxs-lookup"><span data-stu-id="c9efc-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![物件圖形](images/particle-shape-700px.png)

<span data-ttu-id="c9efc-155">**顯示分佈的著色器程式碼：**</span><span class="sxs-lookup"><span data-stu-id="c9efc-155">**Shader code showing the distribution:**</span></span>

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

<span data-ttu-id="c9efc-156">由於我們會將粒子向前排序，而我們仍然使用穩固的樣式著色器來裁剪 (而不是 blend) 透明圖元，這項技術會處理令人驚訝的粒子量，即使在較低的電腦上，也能避免過度耗用成本。</span><span class="sxs-lookup"><span data-stu-id="c9efc-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="c9efc-157">透明粒子雲端</span><span class="sxs-lookup"><span data-stu-id="c9efc-157">Transparent particle clouds</span></span>

<span data-ttu-id="c9efc-158">穩固的粒子提供了良好的雲端圖形外觀，但仍需要一些東西來銷售 fluffiness 的雲端。</span><span class="sxs-lookup"><span data-stu-id="c9efc-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="c9efc-159">我們決定嘗試自訂解決方案，讓我們可以在其中引進透明的高階圖形卡。</span><span class="sxs-lookup"><span data-stu-id="c9efc-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="c9efc-160">若要這樣做，我們只需切換粒子的初始排序次序，並將著色器變更為使用紋理 Alpha。</span><span class="sxs-lookup"><span data-stu-id="c9efc-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy 雲端](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="c9efc-162">它看起來很不錯，但卻證明太過繁重的機器，因為它會導致畫面上的每個圖元呈現數百次！</span><span class="sxs-lookup"><span data-stu-id="c9efc-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="c9efc-163">以較低的解析度呈現關閉畫面</span><span class="sxs-lookup"><span data-stu-id="c9efc-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="c9efc-164">為了減少雲端所呈現的圖元數目，我們開始將它們轉譯成四分之一解析度緩衝區 (相較于螢幕) ，並在繪製所有的粒子之後，將結束結果延展到畫面上。</span><span class="sxs-lookup"><span data-stu-id="c9efc-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="c9efc-165">這讓我們大致上有4x 的速度，但是有幾點需要注意。</span><span class="sxs-lookup"><span data-stu-id="c9efc-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="c9efc-166">**用來呈現非畫面的程式碼：**</span><span class="sxs-lookup"><span data-stu-id="c9efc-166">**Code for rendering off-screen:**</span></span>

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

<span data-ttu-id="c9efc-167">首先，當轉譯成非螢幕的緩衝區時，我們會遺失主要場景的所有深度資訊，導致山脈呈現在山區上方。</span><span class="sxs-lookup"><span data-stu-id="c9efc-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="c9efc-168">其次，延伸緩衝區也會在我們的雲端邊緣上引進瞭解決方式變更明顯的成品。</span><span class="sxs-lookup"><span data-stu-id="c9efc-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="c9efc-169">接下來的兩節將討論我們如何解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="c9efc-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="c9efc-170">粒子深度緩衝區</span><span class="sxs-lookup"><span data-stu-id="c9efc-170">Particle depth buffer</span></span>

<span data-ttu-id="c9efc-171">為了讓物件與世界幾何並存，其中的山或物件可以涵蓋其背後的粒子，我們已使用深度緩衝區（包含主要場景的幾何）來擴展非螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c9efc-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="c9efc-172">為了產生這樣的深度緩衝區，我們建立了第二個相機，只轉譯場景的穩固幾何和深度。</span><span class="sxs-lookup"><span data-stu-id="c9efc-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="c9efc-173">接著，我們會在雲端的圖元著色器中使用新材質來遮蔽圖元。</span><span class="sxs-lookup"><span data-stu-id="c9efc-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="c9efc-174">我們使用相同的材質來計算與雲端圖元背後幾何之間的距離。</span><span class="sxs-lookup"><span data-stu-id="c9efc-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="c9efc-175">藉由使用該距離並將其套用至圖元的 Alpha，我們現在會在接近地形的情況下，將雲端的效果淡出，以移除任何與粒子和地形符合的硬性剪下。</span><span class="sxs-lookup"><span data-stu-id="c9efc-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![混合到地形的雲端](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="c9efc-177">將邊緣銳化</span><span class="sxs-lookup"><span data-stu-id="c9efc-177">Sharpening the edges</span></span>

<span data-ttu-id="c9efc-178">向上延展的雲端幾乎與位於粒子中央或它們重迭的一般大小雲端完全相同，但會顯示在雲端邊緣的一些構件。</span><span class="sxs-lookup"><span data-stu-id="c9efc-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="c9efc-179">否則，當相機移動時，會出現清晰的邊緣，並引進別名效果。</span><span class="sxs-lookup"><span data-stu-id="c9efc-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="c9efc-180">我們藉由在非螢幕緩衝區上執行簡單的著色器來解決這種情況，以判斷在 (1) 中發生重大變更的情況。</span><span class="sxs-lookup"><span data-stu-id="c9efc-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="c9efc-181">我們會將大幅變更的圖元放入新的樣板緩衝區 (2) 。</span><span class="sxs-lookup"><span data-stu-id="c9efc-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="c9efc-182">然後，在將螢幕上的緩衝區套用回畫面時，我們會使用樣板緩衝區來將這些高對比區域遮罩，而導致雲端中的漏洞 (3) 。</span><span class="sxs-lookup"><span data-stu-id="c9efc-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="c9efc-183">接著，我們會以全螢幕模式再次轉譯所有的粒子，但這次會使用樣板緩衝區來遮蔽所有專案，但不包括邊緣， (4) 觸及最少量的圖元。</span><span class="sxs-lookup"><span data-stu-id="c9efc-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="c9efc-184">由於已為粒子建立命令緩衝區，因此我們只需要將它再次轉譯至新的相機。</span><span class="sxs-lookup"><span data-stu-id="c9efc-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![呈現雲端邊緣的進展](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="c9efc-186">最終結果是具有雲端便宜中心區段的尖邊緣。</span><span class="sxs-lookup"><span data-stu-id="c9efc-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="c9efc-187">雖然這比以全螢幕呈現所有的粒子更快，但仍有與針對樣板緩衝區測試圖元相關聯的成本，因此大量的過度繪製仍會產生費用。</span><span class="sxs-lookup"><span data-stu-id="c9efc-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="c9efc-188">剔除粒子</span><span class="sxs-lookup"><span data-stu-id="c9efc-188">Culling particles</span></span>

<span data-ttu-id="c9efc-189">針對我們的風效果，我們在計算著色器中產生了長三角形的停車線，並在世界各地建立許多 wisps。</span><span class="sxs-lookup"><span data-stu-id="c9efc-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="c9efc-190">雖然產生的訣竅會導致不高的填滿率，但它產生了數十萬個頂點，導致端點著色器的負載很高。</span><span class="sxs-lookup"><span data-stu-id="c9efc-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="c9efc-191">我們在計算著色器上引進了附加緩衝區，以饋送要繪製的風條紋子集。</span><span class="sxs-lookup"><span data-stu-id="c9efc-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="c9efc-192">有一些簡單的 view 圖分割可在計算著色器中剔除邏輯，我們可以判斷是否有一個帶狀位於相機視圖之外，並防止它新增至推播緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c9efc-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="c9efc-193">這會大幅減少停車量，以釋出 GPU 上的一些必要週期。</span><span class="sxs-lookup"><span data-stu-id="c9efc-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="c9efc-194">**示範附加緩衝區的程式碼：**</span><span class="sxs-lookup"><span data-stu-id="c9efc-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="c9efc-195">*計算著色器：*</span><span class="sxs-lookup"><span data-stu-id="c9efc-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="c9efc-196">*C # 程式碼：*</span><span class="sxs-lookup"><span data-stu-id="c9efc-196">*C# code:*</span></span>

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

<span data-ttu-id="c9efc-197">我們嘗試在雲端粒子上使用相同的技術，我們會在計算著色器上挑選它們，並且只推送要轉譯的可見粒子。</span><span class="sxs-lookup"><span data-stu-id="c9efc-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="c9efc-198">因為最大的瓶頸是螢幕上呈現的圖元量，而不是計算頂點的成本，所以這項技術實際上不會將我們的 GPU 儲存在 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="c9efc-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="c9efc-199">這項技術的另一個問題是，附加緩衝區是以隨機順序填入，因為它的平行處理本質是計算粒子，導致已排序的粒子未排序，進而導致雲端粒子閃爍。</span><span class="sxs-lookup"><span data-stu-id="c9efc-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="c9efc-200">有幾種方法可以排序推播緩衝區，但我們從「剔除」粒子得到的效能提升數量可能會與其他排序相比，因此我們決定不採用這項優化。</span><span class="sxs-lookup"><span data-stu-id="c9efc-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="c9efc-201">適應性呈現</span><span class="sxs-lookup"><span data-stu-id="c9efc-201">Adaptive rendering</span></span>

<span data-ttu-id="c9efc-202">為了確保具有不同轉譯條件的應用程式具有穩定的畫面播放速率，例如，像是模糊的應用程式，我們為應用程式引進了適應性呈現。</span><span class="sxs-lookup"><span data-stu-id="c9efc-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="c9efc-203">適應性呈現的第一個步驟是測量 GPU。</span><span class="sxs-lookup"><span data-stu-id="c9efc-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="c9efc-204">我們的做法是將自訂程式碼插入到轉譯框架開頭和結尾的 GPU 命令緩衝區，並同時捕捉左右的眼睛畫面時間。</span><span class="sxs-lookup"><span data-stu-id="c9efc-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="c9efc-205">藉由測量花費在轉譯的時間，並將它與我們所需的重新整理率進行比較，我們就能瞭解我們要如何接近畫面。</span><span class="sxs-lookup"><span data-stu-id="c9efc-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="c9efc-206">當您接近放置框架時，我們會調整轉譯以使其更快。</span><span class="sxs-lookup"><span data-stu-id="c9efc-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="c9efc-207">調整的一個簡單方式，就是變更畫面的區大小，需要較少的圖元來呈現。</span><span class="sxs-lookup"><span data-stu-id="c9efc-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="c9efc-208">藉由使用 *UnityEngine. XR. XRSettings. renderViewportScale* ，系統會壓縮目標的區隔，並自動將結果縮小以符合螢幕。</span><span class="sxs-lookup"><span data-stu-id="c9efc-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="c9efc-209">小規模的小小變更對世界幾何而言並沒有明顯的影響，而縮放比例為0.7 則需要呈現的圖元數一半。</span><span class="sxs-lookup"><span data-stu-id="c9efc-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% 的刻度，一半的圖元](images/datascape-scaling-700px.jpg)

<span data-ttu-id="c9efc-211">當我們偵測到我們即將卸載畫面格時，我們會以固定的數位減少尺規，並在執行速度夠快時將其增加回來。</span><span class="sxs-lookup"><span data-stu-id="c9efc-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="c9efc-212">雖然我們決定在啟動時以硬體的圖形功能為基礎所要使用的雲端技術，但您可以將它作為 GPU 測量資料的基礎，以防止系統長期保持低解析度，但這是我們沒有時間在 Datascape 中探索的問題。</span><span class="sxs-lookup"><span data-stu-id="c9efc-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="c9efc-213">最後的想法</span><span class="sxs-lookup"><span data-stu-id="c9efc-213">Final thoughts</span></span>

<span data-ttu-id="c9efc-214">以各種不同的硬體為目標是一項挑戰，需要進行一些規劃。</span><span class="sxs-lookup"><span data-stu-id="c9efc-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="c9efc-215">建議您以較低電源的電腦為目標，以熟悉問題空間並開發將在所有機器上執行的備份解決方案。</span><span class="sxs-lookup"><span data-stu-id="c9efc-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="c9efc-216">請考慮使用填滿率來設計您的解決方案，因為圖元會是您最珍貴的資源。</span><span class="sxs-lookup"><span data-stu-id="c9efc-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="c9efc-217">透明上的目標穩固幾何。</span><span class="sxs-lookup"><span data-stu-id="c9efc-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="c9efc-218">有了備份解決方案之後，您就可以在高階電腦上更複雜地開始分層，也可以增強備份解決方案的解析度。</span><span class="sxs-lookup"><span data-stu-id="c9efc-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="c9efc-219">設計最糟的案例，而且可能會考慮在繁重的情況下使用適應性呈現。</span><span class="sxs-lookup"><span data-stu-id="c9efc-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="c9efc-220">關於作者</span><span class="sxs-lookup"><span data-stu-id="c9efc-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="c9efc-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="c9efc-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="c9efc-222">軟體工程師 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="c9efc-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="c9efc-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="c9efc-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="c9efc-224">軟體工程師 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="c9efc-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="c9efc-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9efc-225">See also</span></span>
* [<span data-ttu-id="c9efc-226">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="c9efc-226">Understanding Performance for Mixed Reality</span></span>](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="c9efc-227">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="c9efc-227">Performance Recommendations for Unity</span></span>](../develop/unity/performance-recommendations-for-unity.md)

 
