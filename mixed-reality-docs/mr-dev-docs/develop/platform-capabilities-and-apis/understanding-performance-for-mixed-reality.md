---
title: 瞭解混合現實的效能
description: 針對 Windows Mixed Reality 應用程式優化效能的 Advanced 主題和詳細資料
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，效能，優化，CPU，GPU
ms.openlocfilehash: c51f84a9814e946603e6dd750fedf0f6e6e78cc0
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679868"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="11c8e-104">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="11c8e-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="11c8e-105">本文是瞭解您的混合現實應用程式效能重要性的簡介。</span><span class="sxs-lookup"><span data-stu-id="11c8e-105">This article is an introduction to understanding the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="11c8e-106">如果您的應用程式不是以最佳畫面播放速率執行，則使用者體驗可能會大幅降低。</span><span class="sxs-lookup"><span data-stu-id="11c8e-106">User experience can be greatly degraded if your application does not run at optimal frame rate.</span></span> <span data-ttu-id="11c8e-107">全像是不穩定的，且環境的標頭追蹤將不穩定，而導致使用者體驗不佳。</span><span class="sxs-lookup"><span data-stu-id="11c8e-107">Holograms will appear unstable and head tracking of the environment will be inaccurate, leading to a poor experience for the user.</span></span> <span data-ttu-id="11c8e-108">您必須將效能視為混合現實開發的第一個類別功能，而不是波蘭文工作。</span><span class="sxs-lookup"><span data-stu-id="11c8e-108">Performance must be considered a first class feature for mixed reality development and not a polish task.</span></span>

<span data-ttu-id="11c8e-109">以下列出每個目標平臺的效能幀效能值。</span><span class="sxs-lookup"><span data-stu-id="11c8e-109">The performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="11c8e-110">平台</span><span class="sxs-lookup"><span data-stu-id="11c8e-110">Platform</span></span> | <span data-ttu-id="11c8e-111">目標畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="11c8e-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="11c8e-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="11c8e-112">HoloLens</span></span>](../../hololens-hardware-details.md) | <span data-ttu-id="11c8e-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="11c8e-113">60 FPS</span></span> |
| [<span data-ttu-id="11c8e-114">Windows Mixed Reality Ultra 電腦</span><span class="sxs-lookup"><span data-stu-id="11c8e-114">Windows Mixed Reality Ultra PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="11c8e-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="11c8e-115">90 FPS</span></span> |
| [<span data-ttu-id="11c8e-116">Windows Mixed Reality 電腦</span><span class="sxs-lookup"><span data-stu-id="11c8e-116">Windows Mixed Reality PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="11c8e-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="11c8e-117">60 FPS</span></span> |

<span data-ttu-id="11c8e-118">下列架構概述達到目標畫面播放速率的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="11c8e-118">The framework below outlines best practices for hitting target frame rates.</span></span> <span data-ttu-id="11c8e-119">如果在 Unity 中進行開發，請考慮閱讀 [unity 文章的效能建議](../unity/performance-recommendations-for-unity.md) ，以取得在 unity 環境中測量及改善畫面播放速率的秘訣。</span><span class="sxs-lookup"><span data-stu-id="11c8e-119">If developing in Unity, consider reading the [performance recommendations for Unity article](../unity/performance-recommendations-for-unity.md) for tips on measuring and improving framerate in the Unity environment.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="11c8e-120">瞭解效能瓶頸</span><span class="sxs-lookup"><span data-stu-id="11c8e-120">Understanding performance bottlenecks</span></span>

<span data-ttu-id="11c8e-121">如果您的應用程式有表現不佳的畫面播放速率，則第一個步驟是分析並瞭解應用程式的計算密集型位置。</span><span class="sxs-lookup"><span data-stu-id="11c8e-121">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="11c8e-122">有兩個主要的處理器負責呈現您場景的工作： CPU 和 GPU。</span><span class="sxs-lookup"><span data-stu-id="11c8e-122">There are two primary processors responsible for the work to render your scene: the CPU and the GPU.</span></span> <span data-ttu-id="11c8e-123">每個都處理您混合現實應用程式的不同層面。</span><span class="sxs-lookup"><span data-stu-id="11c8e-123">Each of these handle different aspects of your Mixed Reality app.</span></span> <span data-ttu-id="11c8e-124">有三個主要位置可能會發生瓶頸：</span><span class="sxs-lookup"><span data-stu-id="11c8e-124">There are three key places where bottlenecks may occur:</span></span> 

1. <span data-ttu-id="11c8e-125">**應用程式執行緒-CPU** -此執行緒負責您的應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="11c8e-125">**App Thread - CPU** - This thread is responsible for your app logic.</span></span> <span data-ttu-id="11c8e-126">這包括處理輸入、動畫、物理和其他應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="11c8e-126">This includes processing input, animations, physics, and other app logic.</span></span>
2. <span data-ttu-id="11c8e-127">將 **執行緒 CPU 轉譯為 gpu** -此執行緒負責將您的繪製呼叫提交給 gpu。</span><span class="sxs-lookup"><span data-stu-id="11c8e-127">**Render Thread - CPU to GPU** - This thread is responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="11c8e-128">當您的應用程式想要轉譯物件（例如 cube 或模型）時，此執行緒會將要求傳送至 GPU 以執行這些作業。</span><span class="sxs-lookup"><span data-stu-id="11c8e-128">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU to perform these operations.</span></span>
3. <span data-ttu-id="11c8e-129">**GPU** -此處理器最常處理您應用程式的圖形管線，將3d 資料 (模型、材質等 ) 轉換成圖元。</span><span class="sxs-lookup"><span data-stu-id="11c8e-129">**GPU** - This processor most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, etc.) into pixels.</span></span> <span data-ttu-id="11c8e-130">它最終會產生要提交到您裝置畫面的2D 影像。</span><span class="sxs-lookup"><span data-stu-id="11c8e-130">It ultimately produces a 2D image to submit to your device's screen.</span></span>

![框架的存留期](images/lifetime-of-a-frame.png)

<span data-ttu-id="11c8e-132">通常，HoloLens 應用程式將會有 GPU 界限，但不一定會。</span><span class="sxs-lookup"><span data-stu-id="11c8e-132">Generally, HoloLens applications will be GPU bound, but not always.</span></span> <span data-ttu-id="11c8e-133">您可以使用下列工具和技術，來瞭解您的特定應用程式瓶頸的位置。</span><span class="sxs-lookup"><span data-stu-id="11c8e-133">Use the tools and techniques below to understand where your particular app is bottlenecked.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="11c8e-134">如何分析您的應用程式</span><span class="sxs-lookup"><span data-stu-id="11c8e-134">How to analyze your application</span></span>

<span data-ttu-id="11c8e-135">有許多工具可讓您瞭解混合現實應用程式的效能設定檔。</span><span class="sxs-lookup"><span data-stu-id="11c8e-135">There are many tools that allow you to understand the performance profile of your mixed reality application.</span></span> <span data-ttu-id="11c8e-136">這些可讓您找出發生瓶頸的位置和原因，讓您可以解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="11c8e-136">These will enable you to find where and why you have bottlenecks, so you can address them.</span></span>

<span data-ttu-id="11c8e-137">以下是一些常見的工具，可為您的應用程式取得深入的程式碼剖析資訊：</span><span class="sxs-lookup"><span data-stu-id="11c8e-137">Below are some common tools to gain deep profiling information for your application:</span></span>
- [<span data-ttu-id="11c8e-138">Intel 圖形效能分析器</span><span class="sxs-lookup"><span data-stu-id="11c8e-138">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="11c8e-139">Visual Studio 圖形偵錯工具</span><span class="sxs-lookup"><span data-stu-id="11c8e-139">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [<span data-ttu-id="11c8e-140">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="11c8e-140">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="11c8e-141">Unity 框架偵錯工具</span><span class="sxs-lookup"><span data-stu-id="11c8e-141">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="11c8e-142">如何在任何環境中進行分析</span><span class="sxs-lookup"><span data-stu-id="11c8e-142">How to profile in any environment</span></span>

<span data-ttu-id="11c8e-143">判斷您的應用程式中是否有 GPU 系結或受 CPU 限制的其中一種方式，是減少轉譯目標輸出的解析度。</span><span class="sxs-lookup"><span data-stu-id="11c8e-143">One way to determine if you are GPU bound or CPU bound in your application is to decrease the resolution of the render target output.</span></span> <span data-ttu-id="11c8e-144">藉由減少要計算的圖元數，這將可減少您的 GPU 負載。</span><span class="sxs-lookup"><span data-stu-id="11c8e-144">By reducing the number of pixels to calculate, this will reduce your GPU load.</span></span> <span data-ttu-id="11c8e-145">裝置會轉譯成較小的材質，然後轉譯為顯示您最終影像的向上取樣。</span><span class="sxs-lookup"><span data-stu-id="11c8e-145">The device will render to a smaller texture, then up-sample to display your final image.</span></span>

<span data-ttu-id="11c8e-146">減少轉譯解析度之後，如果：</span><span class="sxs-lookup"><span data-stu-id="11c8e-146">After decreasing rendering resolution, if:</span></span>
1) <span data-ttu-id="11c8e-147">應用程式的畫面播放速率 **增加** 時，您可能會有 **GPU 界限**</span><span class="sxs-lookup"><span data-stu-id="11c8e-147">Application framerate **increases** , then you are likely **GPU Bound**</span></span>
1) <span data-ttu-id="11c8e-148">應用程式 **的畫面播放速率** 沒有變更，因此您可能會受到 **CPU 的限制**</span><span class="sxs-lookup"><span data-stu-id="11c8e-148">Application framerate **unchanged** , then you are likely **CPU Bound**</span></span>

>[!NOTE]
><span data-ttu-id="11c8e-149">Unity 能讓您在執行時間透過 *[XRSettings renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性，輕鬆修改應用程式的轉譯目標解析度。</span><span class="sxs-lookup"><span data-stu-id="11c8e-149">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="11c8e-150">裝置上顯示的最終映射具有固定的解析度。</span><span class="sxs-lookup"><span data-stu-id="11c8e-150">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="11c8e-151">平臺會取樣較低解析度的輸出，以建立較高的解析度影像，以便在顯示時呈現。</span><span class="sxs-lookup"><span data-stu-id="11c8e-151">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="11c8e-152">如何改進您的應用程式</span><span class="sxs-lookup"><span data-stu-id="11c8e-152">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="11c8e-153">CPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="11c8e-153">CPU performance recommendations</span></span>

<span data-ttu-id="11c8e-154">一般來說，在 CPU 上的混合現實應用程式中，大部分的工作都牽涉到執行場景的「模擬」，並處理您的應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="11c8e-154">Generally, most work in a mixed reality application on the CPU involves performing the "simulation" of the scene and processing your application logic.</span></span> <span data-ttu-id="11c8e-155">下欄區域通常會以優化為目標：</span><span class="sxs-lookup"><span data-stu-id="11c8e-155">The following areas are usually targeted for optimization:</span></span>

- <span data-ttu-id="11c8e-156">動畫</span><span class="sxs-lookup"><span data-stu-id="11c8e-156">Animations</span></span>
- <span data-ttu-id="11c8e-157">物理特性</span><span class="sxs-lookup"><span data-stu-id="11c8e-157">Physics</span></span>
- <span data-ttu-id="11c8e-158">記憶體配置</span><span class="sxs-lookup"><span data-stu-id="11c8e-158">Memory allocations</span></span>
- <span data-ttu-id="11c8e-159">複雜的演算法 (即</span><span class="sxs-lookup"><span data-stu-id="11c8e-159">Complex algorithms (i.e</span></span> <span data-ttu-id="11c8e-160">反向運動，路徑-尋找) </span><span class="sxs-lookup"><span data-stu-id="11c8e-160">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="11c8e-161">GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="11c8e-161">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="11c8e-162">瞭解頻寬與填滿率</span><span class="sxs-lookup"><span data-stu-id="11c8e-162">Understanding bandwidth vs. fill rate</span></span>
<span data-ttu-id="11c8e-163">在 GPU 上轉譯框架時，應用程式通常會受限於記憶體頻寬或填滿率。</span><span class="sxs-lookup"><span data-stu-id="11c8e-163">When rendering a frame on the GPU, an application is generally either bound by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="11c8e-164">**記憶體頻寬** 是 GPU 可從記憶體執行的讀取和寫入速率</span><span class="sxs-lookup"><span data-stu-id="11c8e-164">**Memory bandwidth** is the rate of reads and writes the GPU can perform from memory</span></span>
    - <span data-ttu-id="11c8e-165">若要找出頻寬限制，請減少材質品質，並檢查畫面播放速率是否已改善。</span><span class="sxs-lookup"><span data-stu-id="11c8e-165">To identify bandwidth limitations, reduce texture quality and check if the framerate has improved.</span></span>
    - <span data-ttu-id="11c8e-166">在 Unity 中，這可以藉由變更 [ **編輯** **Texture Quality**  >  **專案設定**  >  \*\*[品質] 設定](https://docs.unity3d.com/Manual/class-QualitySettings.html)\*\* 中的材質品質來完成。</span><span class="sxs-lookup"><span data-stu-id="11c8e-166">In Unity, this can be done by changing **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)** .</span></span>
- <span data-ttu-id="11c8e-167">**填滿率** 是指 GPU 每秒可繪製的圖元。</span><span class="sxs-lookup"><span data-stu-id="11c8e-167">**Fill rate** refers to the pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="11c8e-168">若要識別填滿速率限制，請減少顯示器解析度，並檢查是否已改善幀。</span><span class="sxs-lookup"><span data-stu-id="11c8e-168">To identify fill rate limitations, decrease the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="11c8e-169">在 Unity 中，這可以透過  *[XRSettings renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性來完成。</span><span class="sxs-lookup"><span data-stu-id="11c8e-169">In Unity, this can be done via the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="11c8e-170">記憶體頻寬通常牽涉到下列其中一項的優化：</span><span class="sxs-lookup"><span data-stu-id="11c8e-170">Memory bandwidth generally involves optimizations to either:</span></span>
1) <span data-ttu-id="11c8e-171">減少材質解析度</span><span class="sxs-lookup"><span data-stu-id="11c8e-171">Decrease texture resolutions</span></span>
2) <span data-ttu-id="11c8e-172">使用較少的材質 (法線、反射等等 ) </span><span class="sxs-lookup"><span data-stu-id="11c8e-172">Utilize fewer textures (normals, specular, etc.)</span></span>

<span data-ttu-id="11c8e-173">填滿率著重于減少需要針對最終轉譯圖元計算的作業數目。</span><span class="sxs-lookup"><span data-stu-id="11c8e-173">Fill rate is focused on reducing the number of operations that need to be computed for a final rendered pixel.</span></span> <span data-ttu-id="11c8e-174">這包括減少：</span><span class="sxs-lookup"><span data-stu-id="11c8e-174">This includes reducing:</span></span>
1) <span data-ttu-id="11c8e-175">要呈現/處理的物件數目</span><span class="sxs-lookup"><span data-stu-id="11c8e-175">Number of objects to render/process</span></span>
2) <span data-ttu-id="11c8e-176">每個著色器的作業數目</span><span class="sxs-lookup"><span data-stu-id="11c8e-176">Number of operations per shader</span></span>
3) <span data-ttu-id="11c8e-177">最終結果 (幾何著色器、後置處理效果等的 GPU 階段數目 ) </span><span class="sxs-lookup"><span data-stu-id="11c8e-177">Number of GPU stages to final result (geometry shaders, post-processing effects, etc.)</span></span>
4) <span data-ttu-id="11c8e-178">轉譯 (顯示解析度) 的圖元數</span><span class="sxs-lookup"><span data-stu-id="11c8e-178">Number of pixels to render (display resolution)</span></span>

#### <a name="reduce-polygon-count"></a><span data-ttu-id="11c8e-179">減少多邊形計數</span><span class="sxs-lookup"><span data-stu-id="11c8e-179">Reduce polygon count</span></span>

<span data-ttu-id="11c8e-180">較高的多邊形計數會導致 GPU 的更多作業;減少場景中的 [多邊形數目](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) 可減少轉譯時間。</span><span class="sxs-lookup"><span data-stu-id="11c8e-180">Higher polygon counts result in more operations for the GPU; [reducing the number of polygons](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in your scene will reduce the render time.</span></span> <span data-ttu-id="11c8e-181">有一些其他因素需要將可能很昂貴的幾何加上陰影，但是多邊形計數是最簡單的度量，可判斷場景轉譯的昂貴程度。</span><span class="sxs-lookup"><span data-stu-id="11c8e-181">There are other factors involved in shading the geometry that can be expensive, but polygon count is the simplest metric to determine how expensive a scene will be to render.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="11c8e-182">限制過度繪製</span><span class="sxs-lookup"><span data-stu-id="11c8e-182">Limit overdraw</span></span>

<span data-ttu-id="11c8e-183">當轉譯多個物件但未在螢幕上顯示，因為遮蔽物件隱藏了多個物件時，會發生高過度繪製。</span><span class="sxs-lookup"><span data-stu-id="11c8e-183">High overdraw occurs when multiple objects are rendered but not shown on screen as they are hidden by an occluding object.</span></span> <span data-ttu-id="11c8e-184">想像一下一下有物件背後的牆。</span><span class="sxs-lookup"><span data-stu-id="11c8e-184">Imagine looking at a wall that has objects behind it.</span></span> <span data-ttu-id="11c8e-185">所有幾何都會處理以進行轉譯，但只需要轉譯不透明的牆。</span><span class="sxs-lookup"><span data-stu-id="11c8e-185">All of the geometry would be processed for rendering, but only the opaque wall needs to be rendered.</span></span> <span data-ttu-id="11c8e-186">這會導致不必要的作業。</span><span class="sxs-lookup"><span data-stu-id="11c8e-186">This results in unnecessary operations.</span></span>

#### <a name="shaders"></a><span data-ttu-id="11c8e-187">著色器</span><span class="sxs-lookup"><span data-stu-id="11c8e-187">Shaders</span></span>

<span data-ttu-id="11c8e-188">著色器是在 GPU 上執行的小型程式，且會在轉譯時執行兩個重要的步驟：</span><span class="sxs-lookup"><span data-stu-id="11c8e-188">Shaders are small programs that run on the GPU and perform two important steps in rendering:</span></span>
1) <span data-ttu-id="11c8e-189">判斷應繪製哪些頂點，以及它們在螢幕空間 (頂點著色器的位置) </span><span class="sxs-lookup"><span data-stu-id="11c8e-189">Determining which vertices should be drawn and where they are in screen space (the Vertex shader)</span></span>
    - <span data-ttu-id="11c8e-190">頂點著色器通常會針對每個網格執行每個頂點。</span><span class="sxs-lookup"><span data-stu-id="11c8e-190">The Vertex shader is generally executed per vertex for every mesh.</span></span>
2) <span data-ttu-id="11c8e-191">判斷圖元著色器 (每個圖元的色彩) </span><span class="sxs-lookup"><span data-stu-id="11c8e-191">Determining the color of each pixel (the Pixel shader)</span></span>
    - <span data-ttu-id="11c8e-192">圖元著色器是依幾何轉譯成要轉譯之材質的圖元來執行。</span><span class="sxs-lookup"><span data-stu-id="11c8e-192">The Pixel shader is executed per pixel rendered by the geometry to the texture being rendered to.</span></span>

<span data-ttu-id="11c8e-193">一般而言，著色器會執行許多轉換和光源計算。</span><span class="sxs-lookup"><span data-stu-id="11c8e-193">Typically, shaders perform many transformations and lighting calculations.</span></span> <span data-ttu-id="11c8e-194">雖然複雜的光源模型、陰影和其他作業可以產生絕佳的結果，但它們也有價格。</span><span class="sxs-lookup"><span data-stu-id="11c8e-194">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="11c8e-195">減少著色器中計算的作業數目，可以大幅減少每個畫面的 GPU 所需的工作量。</span><span class="sxs-lookup"><span data-stu-id="11c8e-195">Reducing the number of operations computed in shaders can greatly reduce the work needed for the GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="11c8e-196">著色器編碼建議</span><span class="sxs-lookup"><span data-stu-id="11c8e-196">Shader coding recommendations</span></span>

- <span data-ttu-id="11c8e-197">盡可能使用雙線性篩選</span><span class="sxs-lookup"><span data-stu-id="11c8e-197">Use bilinear filtering, whenever possible</span></span>
- <span data-ttu-id="11c8e-198">重新排列運算式以使用 MAD 內建函式，以便同時執行乘法和 add</span><span class="sxs-lookup"><span data-stu-id="11c8e-198">Rearrange expressions to use MAD intrinsics in order to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="11c8e-199">在 CPU 上盡可能 Precalculate 並以常數形式傳遞至材質</span><span class="sxs-lookup"><span data-stu-id="11c8e-199">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="11c8e-200">**偏好將作業從圖元著色器移至頂點著色器**</span><span class="sxs-lookup"><span data-stu-id="11c8e-200">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="11c8e-201">一般來說，頂點的數目小於圖元數目 (720p 是921600圖元、1080p 是2073600圖元等等 ) </span><span class="sxs-lookup"><span data-stu-id="11c8e-201">Generally, the number of vertices is much smaller than the number of pixels (720p is 921,600 pixels, 1080p is 2,073,600 pixels, etc.)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="11c8e-202">移除 GPU 階段</span><span class="sxs-lookup"><span data-stu-id="11c8e-202">Remove GPU stages</span></span>

<span data-ttu-id="11c8e-203">後續處理效果可能很昂貴，而且會提高應用程式的填滿率。</span><span class="sxs-lookup"><span data-stu-id="11c8e-203">Post-processing effects can be very expensive and increase the fill rate of your application.</span></span> <span data-ttu-id="11c8e-204">這包括像是 MSAA 的消除鋸齒技術。</span><span class="sxs-lookup"><span data-stu-id="11c8e-204">This includes anti-aliasing techniques such as MSAA.</span></span> <span data-ttu-id="11c8e-205">在 HoloLens 上，建議您完全避免這些技術，以及其他著色器階段，例如幾何、輪廓和計算著色器。</span><span class="sxs-lookup"><span data-stu-id="11c8e-205">On HoloLens, it is recommended to avoid these techniques entirely, as well as additional shader stages such as geometry, hull, and compute shaders.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="11c8e-206">記憶體建議</span><span class="sxs-lookup"><span data-stu-id="11c8e-206">Memory recommendations</span></span>

<span data-ttu-id="11c8e-207">過度的記憶體配置和解除配置作業可能會導致效能不一致、凍結的框架和其他不利行為。</span><span class="sxs-lookup"><span data-stu-id="11c8e-207">Excessive memory allocation and deallocation operations can result in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="11c8e-208">在 Unity 中進行開發時，請務必瞭解記憶體考慮，因為記憶體管理是由垃圾收集行程所控制。</span><span class="sxs-lookup"><span data-stu-id="11c8e-208">It is especially important to understand memory considerations when developing in Unity, since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="11c8e-209">物件集區</span><span class="sxs-lookup"><span data-stu-id="11c8e-209">Object pooling</span></span>

<span data-ttu-id="11c8e-210">物件共用是一種常用的技巧，可降低持續配置和物件取消配置的成本。</span><span class="sxs-lookup"><span data-stu-id="11c8e-210">Object pooling is a popular technique to reduce the cost of continuous allocations and deallocations of objects.</span></span> <span data-ttu-id="11c8e-211">這是藉由配置相同物件的大型集區，並重複使用此集區中非使用中的可用實例來完成，而不是在一段時間內不斷產生和終結物件。</span><span class="sxs-lookup"><span data-stu-id="11c8e-211">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="11c8e-212">物件集區非常適合在應用程式期間有變數存留期的重複使用元件。</span><span class="sxs-lookup"><span data-stu-id="11c8e-212">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="11c8e-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11c8e-213">See also</span></span>
- [<span data-ttu-id="11c8e-214">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="11c8e-214">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
- [<span data-ttu-id="11c8e-215">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="11c8e-215">Recommended settings for Unity</span></span>](../unity/recommended-settings-for-unity.md)
- [<span data-ttu-id="11c8e-216">優化3D 模型</span><span class="sxs-lookup"><span data-stu-id="11c8e-216">Optimize 3D models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [<span data-ttu-id="11c8e-217">轉換和優化即時3D 模型的最佳作法</span><span class="sxs-lookup"><span data-stu-id="11c8e-217">Best practices for converting and optimizing real-time 3D Models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

