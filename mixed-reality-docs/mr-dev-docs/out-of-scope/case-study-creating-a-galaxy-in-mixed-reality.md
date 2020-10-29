---
title: 案例研究-在混合式事實下建立 galaxy
description: 在 Microsoft HoloLens 出貨之前，我們會要求開發人員小組想要看到新裝置有經驗的內部小組組建。 有超過5000的想法已共用，而在24小時的 Twitter 輪詢之後，優勝者就稱為「Galaxy Explorer」。
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer、HoloLens、Windows Mixed Reality、分享您的想法、個案研究
ms.openlocfilehash: 91e1c356d69d2b58795a0a0003dd5ffaf0ef1bdc
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91681181"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="9b276-105">案例研究-在混合式事實下建立 galaxy</span><span class="sxs-lookup"><span data-stu-id="9b276-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="9b276-106">在 Microsoft HoloLens 出貨之前，我們會要求開發人員小組想要看到新裝置有經驗的內部小組組建。</span><span class="sxs-lookup"><span data-stu-id="9b276-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="9b276-107">有超過5000的想法已共用，在24小時的 Twitter 輪詢之後，優勝者是稱為 [Galaxy Explorer](../develop/unity/galaxy-explorer.md)的概念。</span><span class="sxs-lookup"><span data-stu-id="9b276-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](../develop/unity/galaxy-explorer.md).</span></span>

<span data-ttu-id="9b276-108">Zibits 是專案的尖端領導人，而 Karim Luccin 是團隊的圖形工程師，討論藝術與工程之間的共同作業，這是在 Galaxy Explorer 中建立銀河方式的精確、互動式標記法。</span><span class="sxs-lookup"><span data-stu-id="9b276-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="9b276-109">技術</span><span class="sxs-lookup"><span data-stu-id="9b276-109">The Tech</span></span>

<span data-ttu-id="9b276-110">由兩個設計人員組成的[小組](../develop/unity/galaxy-explorer.md#meet-the-team)（三名開發人員、四個演出者、生產者和一個測試人員）有六周的時間來建立功能完整的應用程式，可讓人們瞭解及探索銀河的 Vastness 和方式的優點。</span><span class="sxs-lookup"><span data-stu-id="9b276-110">[Our team](../develop/unity/galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="9b276-111">我們想要充分利用 HoloLens 在您的生活空間中直接轉譯3D 物件的能力，因此我們決定要建立實際的查看 galaxy，讓人們可以放大並查看個別的星星，每一個都是各自的軌跡。</span><span class="sxs-lookup"><span data-stu-id="9b276-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="9b276-112">在第一周的開發過程中，我們提供了銀河方法的一些目標，也就是 Galaxy：需要有深度、移動和感覺體積型—全星形，可協助建立 Galaxy 的形式。</span><span class="sxs-lookup"><span data-stu-id="9b276-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="9b276-113">建立具有數十億顆星的動畫 galaxy 的問題，就是需要更新的大量單一元素會是每個畫面格太大的問題，以使用 CPU 建立動畫。</span><span class="sxs-lookup"><span data-stu-id="9b276-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="9b276-114">我們的解決方案牽涉到複雜的藝術與科學組合。</span><span class="sxs-lookup"><span data-stu-id="9b276-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="9b276-115">在幕後</span><span class="sxs-lookup"><span data-stu-id="9b276-115">Behind the scenes</span></span>

<span data-ttu-id="9b276-116">為了讓人們能夠探索個別的星星，我們的第一個步驟是瞭解我們可以一次轉譯的粒子數目。</span><span class="sxs-lookup"><span data-stu-id="9b276-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="9b276-117">轉譯粒子</span><span class="sxs-lookup"><span data-stu-id="9b276-117">Rendering particles</span></span>

<span data-ttu-id="9b276-118">目前的 Cpu 很適合用來處理序列工作，且一次最多可以進行一些平行工作 (視它們) 的核心數目而定，但 Gpu 在以平行方式處理上千個作業時更有效率。</span><span class="sxs-lookup"><span data-stu-id="9b276-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="9b276-119">不過，因為它們通常不會與 CPU 共用相同的記憶體，所以在 CPU<>GPU 之間交換資料可能很快就會變成瓶頸。</span><span class="sxs-lookup"><span data-stu-id="9b276-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="9b276-120">我們的解決方案是在 GPU 上建立 galaxy，而且必須完全存留在 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="9b276-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="9b276-121">我們開始使用各種模式的數千點粒子來進行壓力測試。</span><span class="sxs-lookup"><span data-stu-id="9b276-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="9b276-122">如此一來，我們就可以在 HoloLens 上取得 galaxy，看看有什麼作用和不是什麼。</span><span class="sxs-lookup"><span data-stu-id="9b276-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="9b276-123">建立星星的位置</span><span class="sxs-lookup"><span data-stu-id="9b276-123">Creating the position of the stars</span></span>

<span data-ttu-id="9b276-124">我們的其中一個小組成員已經撰寫了 c # 程式碼，該程式碼會在其初始位置產生星星。</span><span class="sxs-lookup"><span data-stu-id="9b276-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="9b276-125">星星位於橢圓形上，而其位置可以透過 ( **curveOffset** 、 **ellipseSize** 、提高 **許可權** ) 來描述，其中 **curveOffset** 是沿著橢圓形的星形角度， **ellipseSize** 是沿著 X 和 Z 的橢圓形的維度，而且會提高 galaxy 內星號的適當提高許可權。</span><span class="sxs-lookup"><span data-stu-id="9b276-125">The stars are on an ellipse and their position can be described by ( **curveOffset** , **ellipseSize** , **elevation** ) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="9b276-126">因此，我們可以建立 ([Unity 的 ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) 的緩衝區，它會使用每個星狀屬性來初始化，並將其傳送至 GPU，以供其餘體驗使用。</span><span class="sxs-lookup"><span data-stu-id="9b276-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="9b276-127">為了繪製這個緩衝區，我們會使用 [Unity 的 DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) ，以允許在任意一組點上的 GPU) 上執行著色器 (程式碼，而不會有代表 galaxy 的實際網格：</span><span class="sxs-lookup"><span data-stu-id="9b276-127">To draw this buffer, we use [Unity’s DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="9b276-128">**Cpu：**</span><span class="sxs-lookup"><span data-stu-id="9b276-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="9b276-129">**Gpu：**</span><span class="sxs-lookup"><span data-stu-id="9b276-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="9b276-130">我們開始使用具有上千個粒子的原始迴圈模式。</span><span class="sxs-lookup"><span data-stu-id="9b276-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="9b276-131">這讓我們能夠以較佳的速度來管理許多粒子，並以高效能的速度來執行，但我們不滿意 galaxy 的整體塑造。</span><span class="sxs-lookup"><span data-stu-id="9b276-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="9b276-132">為了改善圖形，我們嘗試使用旋轉的各種模式和物件系統。</span><span class="sxs-lookup"><span data-stu-id="9b276-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="9b276-133">這一開始是因為粒子的數目和效能維持一致，但圖形接近中央，而星星發出的外表並不切合實際。</span><span class="sxs-lookup"><span data-stu-id="9b276-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="9b276-134">我們需要一段時間，讓我們可以操作時間，並讓粒子實際移動，更接近 galaxy 的中心。</span><span class="sxs-lookup"><span data-stu-id="9b276-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![我們嘗試了各種不同的模式和粒子系統，如下所示。](images/galaxy-patterns-500px.png)

<span data-ttu-id="9b276-136">我們嘗試了各種不同的模式和粒子系統，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9b276-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="9b276-137">我們的團隊對 galaxies 函式進行了一些研究，而我們為 galaxy 建立了自訂的物件系統，讓我們可以根據「[密度 wave 理論](https://en.wikipedia.org/wiki/Density_wave_theory)」來移動有關省略號的粒子，如此一來，galaxy 的 arm 就是較高密度的區域，但在固定的 flux 中，例如交通堵塞。</span><span class="sxs-lookup"><span data-stu-id="9b276-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="9b276-138">它的外觀穩定且穩固，但星形在移動其各自的省略號時，會實際移入和移出 arm。</span><span class="sxs-lookup"><span data-stu-id="9b276-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="9b276-139">在我們的系統中，粒子絕不會存在於 CPU 上-我們會產生卡片並在 GPU 上將它們導向，讓整個系統只是初始狀態 + 時間。</span><span class="sxs-lookup"><span data-stu-id="9b276-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="9b276-140">它的進展如下：</span><span class="sxs-lookup"><span data-stu-id="9b276-140">It progressed like this:</span></span>

![具有 GPU 轉譯之粒子系統的進展](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="9b276-142">具有 GPU 轉譯之粒子系統的進展</span><span class="sxs-lookup"><span data-stu-id="9b276-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="9b276-143">一旦加入足夠的省略號並設定為旋轉，galaxies 就會開始形成「臂」，也就是星星的移動。</span><span class="sxs-lookup"><span data-stu-id="9b276-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="9b276-144">每個橢圓形路徑的星星間距都有一些隨機性，而且每顆星都有一些隨機新增的位置。</span><span class="sxs-lookup"><span data-stu-id="9b276-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="9b276-145">這建立了更自然的星狀移動和 arm 圖形分佈。</span><span class="sxs-lookup"><span data-stu-id="9b276-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="9b276-146">最後，我們新增了根據距離中心距離驅動色彩的能力。</span><span class="sxs-lookup"><span data-stu-id="9b276-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="9b276-147">建立星星的運動</span><span class="sxs-lookup"><span data-stu-id="9b276-147">Creating the motion of the stars</span></span>

<span data-ttu-id="9b276-148">若要建立一般星形運動的動畫，我們需要為每個框架新增常數角度，並以常數星形速度在其省略號之間移動星星。</span><span class="sxs-lookup"><span data-stu-id="9b276-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="9b276-149">這是使用 **curveOffset** 的主要原因。</span><span class="sxs-lookup"><span data-stu-id="9b276-149">This is the primary reason for using **curveOffset** .</span></span> <span data-ttu-id="9b276-150">這在技術上並不正確，因為星形會沿著省略號的最長邊移動，但一般動作覺得良好。</span><span class="sxs-lookup"><span data-stu-id="9b276-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![星星在長弧線的移動速度更快，邊緣的速度較慢。](images/ellipse-movement.jpg)

<span data-ttu-id="9b276-152">星星在長弧線的移動速度更快，邊緣的速度較慢。</span><span class="sxs-lookup"><span data-stu-id="9b276-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="9b276-153">如此一來，就會 ( **curveOffset** 、 **ellipseSize** 、提高 **許可權** 、 **年齡** ) 的完整描述每顆星，其中 **age** 是在載入場景之後所經過的總時間。</span><span class="sxs-lookup"><span data-stu-id="9b276-153">With that, each star is fully described by ( **curveOffset** , **ellipseSize** , **elevation** , **Age** ) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="9b276-154">如此一來，我們就可以在應用程式一開始就產生數萬顆星，然後在建立的曲線上以一組挑的星形為動畫。</span><span class="sxs-lookup"><span data-stu-id="9b276-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="9b276-155">由於所有專案都是在 GPU 上，因此系統可以平行地以平行方式建立所有星星的動畫，而不需支付 CPU 的成本。</span><span class="sxs-lookup"><span data-stu-id="9b276-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![以下是繪製白色四邊形時的樣子。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="9b276-157">以下是繪製白色四邊形時的樣子。</span><span class="sxs-lookup"><span data-stu-id="9b276-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="9b276-158">為了讓每個四顆人都臉部，我們使用幾何著色器，將每個星形位置轉換成螢幕上包含星狀材質的2D 矩形。</span><span class="sxs-lookup"><span data-stu-id="9b276-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![鑽石（而非四邊形）。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="9b276-160">鑽石（而非四邊形）。</span><span class="sxs-lookup"><span data-stu-id="9b276-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="9b276-161">因為我們想要限制過度繪製 (次圖元) 處理的次數，所以我們會旋轉四邊形，使其重迭。</span><span class="sxs-lookup"><span data-stu-id="9b276-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="9b276-162">新增雲端</span><span class="sxs-lookup"><span data-stu-id="9b276-162">Adding clouds</span></span>

<span data-ttu-id="9b276-163">有許多方式可以讓體積型感覺，從磁片區內的光線按照，到盡可能繪製最多的粒子來模擬雲端。</span><span class="sxs-lookup"><span data-stu-id="9b276-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="9b276-164">即時光線按照需要太多資源而且難以撰寫，因此我們先嘗試使用一種呈現遊戲中樹系的方法來建立冒名頂替的系統，並以許多2D 影像呈現相機的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="9b276-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="9b276-165">當我們在遊戲中進行這項操作時，就可以有從相機旋轉的樹狀結構、儲存所有影像，以及在執行時間為每個佈告欄卡片選取符合視圖方向的影像。</span><span class="sxs-lookup"><span data-stu-id="9b276-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="9b276-166">當映射是全息影像時，這也不適用。</span><span class="sxs-lookup"><span data-stu-id="9b276-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="9b276-167">左邊眼和右邊的差異讓它成為需要更高解析度的解析度，否則就只是平面、別名或重複。</span><span class="sxs-lookup"><span data-stu-id="9b276-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="9b276-168">在第二次嘗試時，我們嘗試盡可能地有最多的粒子。</span><span class="sxs-lookup"><span data-stu-id="9b276-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="9b276-169">當我們在將物件加入場景之前，額外繪製了它們並模糊它們之前，可以達到最佳的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="9b276-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="9b276-170">這種方法的典型問題，是與我們一次可以繪製的粒子數目，以及它們所涵蓋的畫面區域數目仍維持60fps 的程度有關。</span><span class="sxs-lookup"><span data-stu-id="9b276-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="9b276-171">模糊產生的影像，以取得此雲端感覺通常是非常昂貴的作業。</span><span class="sxs-lookup"><span data-stu-id="9b276-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![如果沒有紋理，這就是雲端看起來會像2% 不透明度的樣子。](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="9b276-173">如果沒有紋理，這就是雲端看起來會像2% 不透明度的樣子。</span><span class="sxs-lookup"><span data-stu-id="9b276-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="9b276-174">如果是加總且有很多，表示我們會將多個四邊形放在彼此的上方，並重複地將相同的圖元加上陰影。</span><span class="sxs-lookup"><span data-stu-id="9b276-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="9b276-175">在 galaxy 的中央，相同的圖元在彼此上具有數百個四邊形，而且在全螢幕完成時，會有相當大的成本。</span><span class="sxs-lookup"><span data-stu-id="9b276-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="9b276-176">進行全螢幕雲端，並嘗試將它們模糊會是個不錯的想法，因此我們決定讓硬體為我們執行工作。</span><span class="sxs-lookup"><span data-stu-id="9b276-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="9b276-177">先有一點內容</span><span class="sxs-lookup"><span data-stu-id="9b276-177">A bit of context first</span></span>

<span data-ttu-id="9b276-178">使用遊戲中的材質時，紋理大小很少會符合我們想要在其中使用的區域，但我們可以使用不同類型的材質篩選來取得圖形卡片，以從紋理的圖元 ([材質篩選](https://msdn.microsoft.com/library/dn642451.aspx)) 中插入所要的色彩。</span><span class="sxs-lookup"><span data-stu-id="9b276-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="9b276-179">感興趣的篩選是 [雙線性篩選](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) ，會使用4個最接近的鄰近專案來計算任何圖元的值。</span><span class="sxs-lookup"><span data-stu-id="9b276-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![在篩選之前的原始](images/texture-1.png)

![篩選後的結果](images/texture-2.png)

<span data-ttu-id="9b276-182">使用這個屬性，我們會看到每次嘗試將材質繪製到兩倍的區域時，都會使結果變得模糊。</span><span class="sxs-lookup"><span data-stu-id="9b276-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="9b276-183">我們不會轉譯成全螢幕，而且會遺失這些珍貴的毫秒數，因此我們會轉譯成螢幕的小版本。</span><span class="sxs-lookup"><span data-stu-id="9b276-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="9b276-184">然後，藉由複製此材質並以2倍的因數將它延展，我們會回到全螢幕，同時將進程中的內容模糊。</span><span class="sxs-lookup"><span data-stu-id="9b276-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 精密回到完整解析度。](images/galaxy-resolutions-300px.png)

<span data-ttu-id="9b276-186">x3 精密回到完整解析度。</span><span class="sxs-lookup"><span data-stu-id="9b276-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="9b276-187">如此一來，我們就能取得雲端部分，只剩下一小部分的原始成本。</span><span class="sxs-lookup"><span data-stu-id="9b276-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="9b276-188">我們不會在完整解析度上新增雲端，而是只繪製 1/第64次圖元，然後將材質延展回完整解析度。</span><span class="sxs-lookup"><span data-stu-id="9b276-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![從 1/8 精密至完整解析;沒錯，有3個精密使用2的乘冪。](images/stars-upscaled-300px.jpg)

<span data-ttu-id="9b276-190">從 1/8 精密至完整解析;沒錯，有3個精密使用2的乘冪。</span><span class="sxs-lookup"><span data-stu-id="9b276-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="9b276-191">請注意，嘗試從大小的 1/第64次到全尺寸的結果看起來完全不同，因為在我們的安裝程式中，圖形卡仍會使用4個圖元來陰影放大較大的區域，並開始顯示成品。</span><span class="sxs-lookup"><span data-stu-id="9b276-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="9b276-192">然後，如果我們以較小的卡片新增完整的解析度星星，我們會取得完整的 galaxy：</span><span class="sxs-lookup"><span data-stu-id="9b276-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![使用完整解析度星星的 galaxy 轉譯接近最終結果](images/full-galaxy-500px.png)

<span data-ttu-id="9b276-194">當我們在圖形上進行適當的追蹤之後，我們新增了一層雲端，將暫存點與我們在 Photoshop 中繪製的點交換，並新增一些其他色彩。</span><span class="sxs-lookup"><span data-stu-id="9b276-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="9b276-195">結果是一個銀河的方式，就是 Galaxy 我們的藝術和工程團隊都覺得很不錯，而且它符合我們的深度、數量和運動目標，全都不會讓 CPU 負擔。</span><span class="sxs-lookup"><span data-stu-id="9b276-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![這是在3D 中的最終銀河方式。](images/final-galaxy-500px.jpg)

<span data-ttu-id="9b276-197">這是在3D 中的最終銀河方式。</span><span class="sxs-lookup"><span data-stu-id="9b276-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="9b276-198">深入瞭解</span><span class="sxs-lookup"><span data-stu-id="9b276-198">More to explore</span></span>

<span data-ttu-id="9b276-199">我們已開放建立 Galaxy Explorer 應用程式的程式碼，並使其可在 [GitHub](https://github.com/Microsoft/GalaxyExplorer) 上提供，以供開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="9b276-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="9b276-200">有興趣找出有關 Galaxy Explorer 開發流程的詳細資訊嗎？</span><span class="sxs-lookup"><span data-stu-id="9b276-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="9b276-201">查看 [Microsoft HoloLens YouTube 頻道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)上所有過去的專案更新。</span><span class="sxs-lookup"><span data-stu-id="9b276-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="9b276-202">關於作者</span><span class="sxs-lookup"><span data-stu-id="9b276-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="9b276-203"><b>Karim Luccin</b> 是軟體工程師和別致的視覺愛好者愛好者。</span><span class="sxs-lookup"><span data-stu-id="9b276-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="9b276-204">他是「Galaxy Explorer 的圖形工程師」。</span><span class="sxs-lookup"><span data-stu-id="9b276-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="9b276-205"><b>Zibits</b> 是一種尖端的領導和空間愛好者，負責管理適用于 Galaxy Explorer 和曾的3d 模型化小組，以取得更多的粒子。</span><span class="sxs-lookup"><span data-stu-id="9b276-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="9b276-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b276-206">See also</span></span>
* [<span data-ttu-id="9b276-207">GitHub 上的 Galaxy Explorer</span><span class="sxs-lookup"><span data-stu-id="9b276-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="9b276-208">YouTube 上的 Galaxy Explorer 專案更新</span><span class="sxs-lookup"><span data-stu-id="9b276-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
