---
title: PefGettingStarted
description: 在 MRTK 中瞭解及調整效能的檔。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: d982de8e546585e254d47679944e4ba169136d67
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687438"
---
# <a name="performance"></a><span data-ttu-id="dd756-104">效能</span><span class="sxs-lookup"><span data-stu-id="dd756-104">Performance</span></span>

## <a name="getting-started"></a><span data-ttu-id="dd756-105">開始使用</span><span class="sxs-lookup"><span data-stu-id="dd756-105">Getting started</span></span>

<span data-ttu-id="dd756-106">將效能合理化的最簡單方式是透過畫面播放速率，或應用程式每秒可轉譯影像的次數。</span><span class="sxs-lookup"><span data-stu-id="dd756-106">The easiest way to rationalize performance is via framerate or how many times your application can render an image per second.</span></span> <span data-ttu-id="dd756-107">請務必符合目標的畫面播放速率，如目標平臺所述 (例如：</span><span class="sxs-lookup"><span data-stu-id="dd756-107">It is important to meet the target framerate, as outlined by the platform being targeted (i.e</span></span> <span data-ttu-id="dd756-108">[Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality)、 [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)等) 。</span><span class="sxs-lookup"><span data-stu-id="dd756-108">[Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/), etc).</span></span> <span data-ttu-id="dd756-109">例如，在 HoloLens 上，目標畫面播放速率是 60 FPS。</span><span class="sxs-lookup"><span data-stu-id="dd756-109">For example, on HoloLens, the target framerate is 60 FPS.</span></span> <span data-ttu-id="dd756-110">低幀率的應用程式可能會導致日益惡化使用者體驗， [例如惡化全](hologram-Stabilization.md)像、世界追蹤、手追蹤等。</span><span class="sxs-lookup"><span data-stu-id="dd756-110">Low framerate applications can result in deteriorated user experiences such as worsened [hologram stabilization](hologram-Stabilization.md), world tracking, hand tracking, and more.</span></span> <span data-ttu-id="dd756-111">為了協助開發人員追蹤和達成品質的畫面播放速率，Mixed Reality 工具組提供各種不同的工具和腳本。</span><span class="sxs-lookup"><span data-stu-id="dd756-111">To help developers track and achieve quality framerate, the Mixed Reality Toolkit provides a variety of tools and scripts.</span></span>

### <a name="visual-profiler"></a><span data-ttu-id="dd756-112">Visual profiler</span><span class="sxs-lookup"><span data-stu-id="dd756-112">Visual profiler</span></span>

<span data-ttu-id="dd756-113">若要在開發的存留期間持續追蹤效能，強烈建議您在執行 & 的應用程式偵錯工具時，一律顯示畫面播放速率的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="dd756-113">To continuously track performance over the lifetime of development, it is highly recommended to always show a framerate visual while running & debugging an application.</span></span> <span data-ttu-id="dd756-114">Mixed Reality 工具組提供的 [Visual Profiler](../features/Diagnostics/UsingVisualProfiler.md) 診斷工具，可提供應用程式視圖中目前 FPS 和記憶體使用量的即時資訊。</span><span class="sxs-lookup"><span data-stu-id="dd756-114">The Mixed Reality Toolkit provides the [Visual Profiler](../features/Diagnostics/UsingVisualProfiler.md) diagnostic tool which gives real-time information about the current FPS and memory usage in application view.</span></span> <span data-ttu-id="dd756-115">您可以透過 [ [MRTK 設定檔](../out-of-scope/MixedRealityConfigurationGuide.md)] 偵測器底下的 [[診斷系統] 設定](../features/Diagnostics/DiagnosticsSystemGettingStarted.md)來設定 Visual Profiler。</span><span class="sxs-lookup"><span data-stu-id="dd756-115">The Visual Profiler can be configured via the [Diagnostics System Settings](../features/Diagnostics/DiagnosticsSystemGettingStarted.md) under the [MRTK Profiles Inspector](../out-of-scope/MixedRealityConfigurationGuide.md).</span></span>

<span data-ttu-id="dd756-116">此外，在裝置上執行時，最好使用 Visual Profiler 來追蹤畫面播放速率，而不是在 Unity 編輯器或模擬器中執行。</span><span class="sxs-lookup"><span data-stu-id="dd756-116">Furthermore, it is particularly important to utilize the Visual Profiler to track framerate when running on the device as opposed to running in Unity editor or an emulator.</span></span> <span data-ttu-id="dd756-117">在具有 [發行設定組建](https://docs.microsoft.com/visualstudio/debugger/how-to-set-debug-and-release-configurations?view=vs-2019)的裝置上執行時，會描述最精確的效能結果。</span><span class="sxs-lookup"><span data-stu-id="dd756-117">The most accurate performance results will be depicted when running on the device with [Release configuration builds](https://docs.microsoft.com/visualstudio/debugger/how-to-set-debug-and-release-configurations?view=vs-2019).</span></span>

> [!NOTE]
> <span data-ttu-id="dd756-118">如果建立 Windows Mixed Reality，請使用[主要設定組建](https://docs.microsoft.com/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)進行部署</span><span class="sxs-lookup"><span data-stu-id="dd756-118">If building for Windows Mixed Reality, deploy with [MASTER configuration builds](https://docs.microsoft.com/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)</span></span>

![Visual Profiler 介面](../features/Images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a><span data-ttu-id="dd756-120">優化視窗</span><span class="sxs-lookup"><span data-stu-id="dd756-120">Optimize window</span></span>

<span data-ttu-id="dd756-121">[ [MRTK 優化] 視窗](../features/Tools/OptimizeWindow.md) 提供資訊和自動化工具，協助混合現實開發人員設定其環境以獲得效能最佳的結果，並找出場景 & 資產的潛在瓶頸。</span><span class="sxs-lookup"><span data-stu-id="dd756-121">The [MRTK Optimize Window](../features/Tools/OptimizeWindow.md) offers information and automation tools to help mixed reality developers set up their environment for the best performing results and identify potential bottlenecks in their scene & assets.</span></span> <span data-ttu-id="dd756-122">Unity 中的某些重要設定可協助提供大幅優化的混合現實專案結果。</span><span class="sxs-lookup"><span data-stu-id="dd756-122">Certain key configurations in Unity can help deliver substantially more optimized results for mixed reality projects.</span></span>

<span data-ttu-id="dd756-123">一般而言，這些設定牽涉到呈現適用于混合現實的設定。</span><span class="sxs-lookup"><span data-stu-id="dd756-123">Generally, these settings involve rendering configurations that are ideal for mixed reality.</span></span> <span data-ttu-id="dd756-124">相較于傳統的3D 圖形開發，混合現實應用程式是唯一的，因為有兩個畫面 (例如</span><span class="sxs-lookup"><span data-stu-id="dd756-124">Mixed reality applications are unique compared to traditional 3D graphics development in that there are two screens (i.e</span></span> <span data-ttu-id="dd756-125">針對整個場景呈現兩個眼睛) 。</span><span class="sxs-lookup"><span data-stu-id="dd756-125">two eyes) to render for the entire scene.</span></span>

<span data-ttu-id="dd756-126">您可以利用 [MRTK 優化] 視窗，在 Unity 專案中自動設定以下所述的建議設定。</span><span class="sxs-lookup"><span data-stu-id="dd756-126">The recommended settings referenced below can be auto-configured in a Unity project by leveraging the MRTK Optimize Window.</span></span>

![MRTK 優化視窗設定](../features/Images/Performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a><span data-ttu-id="dd756-128">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="dd756-128">Unity Profiler</span></span>

<span data-ttu-id="dd756-129">[Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html)是一個實用的工具，可在每個畫面格層級調查應用程式效能的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="dd756-129">The [Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html) is a useful tool to investigate details of application performance at a frame-by-frame level.</span></span>

#### <a name="time-spent-on-the-cpu"></a><span data-ttu-id="dd756-130">CPU 花費的時間</span><span class="sxs-lookup"><span data-stu-id="dd756-130">Time spent on the CPU</span></span>

![範例 Unity Profiler 圖形](../features/Images/Performance/UnityProfilerGraph.png)

<span data-ttu-id="dd756-132">若要維持理想的畫面播放速率 (通常是每秒60個畫面格) ，應用程式必須達到16.6 毫秒的 CPU 時間最大畫面格時間。</span><span class="sxs-lookup"><span data-stu-id="dd756-132">To maintain comfortable frame rates (typically 60 frames per second), applications need to achieve a maximum frame time of 16.6 milliseconds of CPU time.</span></span> <span data-ttu-id="dd756-133">為了協助識別 MRTK 功能的成本，Microsoft Mixed Reality 工具組包含每個畫面格 () 程式碼路徑的內部迴圈標記。</span><span class="sxs-lookup"><span data-stu-id="dd756-133">To help identify the cost of MRTK functionality, the Microsoft Mixed Reality Toolkit contains a markers for inner loop (per frame) code paths.</span></span> <span data-ttu-id="dd756-134">這些標記會使用下列格式，以協助您瞭解所使用的特定功能：</span><span class="sxs-lookup"><span data-stu-id="dd756-134">These markers use the following format, to assist in understanding the specific functionality being utilized:</span></span>

```
[MRTK] className.methodName
```

> [!Note]
> <span data-ttu-id="dd756-135">在方法名稱之後可能會有其他資料。</span><span class="sxs-lookup"><span data-stu-id="dd756-135">There may be additional data following the method name.</span></span> <span data-ttu-id="dd756-136">這是用來識別有條件地執行，可能會因為應用程式程式碼的小型變更而避免的昂貴功能。</span><span class="sxs-lookup"><span data-stu-id="dd756-136">This is used to identify conditionally executed, potentially expensive functionality that may be avoided by small changes to application code.</span></span>

![範例 Unity Profiler 階層](../features/Images/Performance/UnityProfilerHierarchy.png)

<span data-ttu-id="dd756-138">在此範例中，階層已展開，以顯示 WindowsMixedRealityArticulatedHand 類別的 UpdateHandData 方法在分析框架期間耗用0.44 毫秒的 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="dd756-138">In this example, the hierarchy has been expanded to show that the UpdateHandData method of WindowsMixedRealityArticulatedHand class is consuming 0.44 ms of CPU time during the frame being analyzed.</span></span> <span data-ttu-id="dd756-139">這項資料可以用來協助判斷效能問題是否與應用程式程式碼或系統中的其他位置有關。</span><span class="sxs-lookup"><span data-stu-id="dd756-139">This data can be used to help determine if a performance issue is related to application code or from elsewhere in the system.</span></span>

<span data-ttu-id="dd756-140">強烈建議開發人員以類似的方式檢測應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="dd756-140">It is highly recommended that developers instrument application code in a similar fashion.</span></span> <span data-ttu-id="dd756-141">應用程式程式碼檢測的主要焦點區域是在事件處理常式中，因為引發事件時，這些方法會向 MRTK 更新迴圈收取。</span><span class="sxs-lookup"><span data-stu-id="dd756-141">Primary areas of focus for application code instrumentation is within event handlers as these methods are charged to the MRTK update loop as events are raised.</span></span> <span data-ttu-id="dd756-142">MRTK 更新迴圈內的高框架時間可能是指事件處理常式方法中的昂貴程式碼。</span><span class="sxs-lookup"><span data-stu-id="dd756-142">High frame times within the MRTK update loop can be indicative of expensive code in event handler methods.</span></span>

## <a name="recommended-settings-for-unity"></a><span data-ttu-id="dd756-143">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="dd756-143">Recommended settings for Unity</span></span>

### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="dd756-144">Single-Pass 實例轉譯</span><span class="sxs-lookup"><span data-stu-id="dd756-144">Single-Pass Instanced rendering</span></span>

<span data-ttu-id="dd756-145">Unity 中 XR 的預設轉譯設定是 [多重傳遞](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html)。</span><span class="sxs-lookup"><span data-stu-id="dd756-145">The default rendering configuration for XR in Unity is [Multi-pass](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html).</span></span> <span data-ttu-id="dd756-146">這項設定會指示 Unity 執行整個轉譯管線兩次，每次都有一次。</span><span class="sxs-lookup"><span data-stu-id="dd756-146">This setting instructs Unity to execute the entire render pipeline twice, once for each eye.</span></span> <span data-ttu-id="dd756-147">您可以改為選取 [ [單一傳遞實例](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 轉譯] 來將其優化。</span><span class="sxs-lookup"><span data-stu-id="dd756-147">This can be optimized by selecting [Single Pass Instanced rendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) instead.</span></span> <span data-ttu-id="dd756-148">這項設定會利用轉譯 [目標陣列](https://en.wikipedia.org/wiki/Multiple_Render_Targets) 來執行單一繪製呼叫，將實例放入適當的 [呈現目標](https://en.wikipedia.org/wiki/Render_Target) 中。</span><span class="sxs-lookup"><span data-stu-id="dd756-148">This configuration leverages [render target arrays](https://en.wikipedia.org/wiki/Multiple_Render_Targets) to be able to perform a single draw call that instances into the appropriate [render target](https://en.wikipedia.org/wiki/Render_Target) for each eye.</span></span> <span data-ttu-id="dd756-149">此外，這個模式允許在轉譯管線的單一執行中完成所有轉譯。</span><span class="sxs-lookup"><span data-stu-id="dd756-149">Furthermore, this mode allows all rendering to be done in a single execution of the rendering pipeline.</span></span> <span data-ttu-id="dd756-150">因此，選取單一傳遞實例轉譯作為混合現實應用程式的轉譯路徑，可以 [在 CPU & GPU 上節省大量時間](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) ，而且這是建議的轉譯設定。</span><span class="sxs-lookup"><span data-stu-id="dd756-150">Thus, selecting Single Pass Instanced rendering as the rendering path for a mixed reality application can [save substantial time on both the CPU & GPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) and is the recommended rendering configuration.</span></span>

<span data-ttu-id="dd756-151">不過，若要對每個網格發出單一繪製呼叫每個網格，所有著色器都必須支援 [GPU 實例](https://docs.unity3d.com/Manual/GPUInstancing.html) 。</span><span class="sxs-lookup"><span data-stu-id="dd756-151">However, in order to issue a single draw call for each mesh to each eye, [GPU instancing](https://docs.unity3d.com/Manual/GPUInstancing.html) must be supported by all shaders.</span></span> <span data-ttu-id="dd756-152">實例可讓 GPU 跨兩個眼睛繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="dd756-152">Instancing allows the GPU to multiplex draw calls across both eyes.</span></span> <span data-ttu-id="dd756-153">Unity 內建著色器和 [MRTK 標準著色器](../features/README_MRTKStandardShader.md) 依預設會在著色器程式碼中包含必要的實例指示。</span><span class="sxs-lookup"><span data-stu-id="dd756-153">Unity built-in shaders as well as the [MRTK Standard shader](../features/README_MRTKStandardShader.md) by default contain the necessary instancing instructions in shader code.</span></span> <span data-ttu-id="dd756-154">如果是針對 Unity 撰寫自訂著色器，可能需要更新這些著色器，以支援單一傳遞實例轉譯。</span><span class="sxs-lookup"><span data-stu-id="dd756-154">If writing custom shaders though for Unity, these shaders may need to be updated to support Single Pass Instanced rendering.</span></span>

#### <a name="example-code-for-custom-shader"></a>[<span data-ttu-id="dd756-155">自訂著色器的範例程式碼</span><span class="sxs-lookup"><span data-stu-id="dd756-155">Example Code for Custom Shader</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a><span data-ttu-id="dd756-156">品質設定</span><span class="sxs-lookup"><span data-stu-id="dd756-156">Quality settings</span></span>

<span data-ttu-id="dd756-157">Unity 提供預設值 [來控制](https://docs.unity3d.com/Manual/class-QualitySettings.html) 每個平臺端點的轉譯品質。</span><span class="sxs-lookup"><span data-stu-id="dd756-157">Unity provides [presets to control quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) of rendering for each platform endpoint.</span></span> <span data-ttu-id="dd756-158">這些預設值可控制哪些圖形功能可以啟用，例如陰影、消除鋸齒、全球照明等等。</span><span class="sxs-lookup"><span data-stu-id="dd756-158">These presets control what graphical features can be enabled such as shadows, anti-aliasing, global illumination, and more.</span></span> <span data-ttu-id="dd756-159">建議您降低這些設定，並優化轉譯期間所執行的計算數目。</span><span class="sxs-lookup"><span data-stu-id="dd756-159">It is recommended to lower these settings and optimize the number of calculations performed during rendering.</span></span>

<span data-ttu-id="dd756-160">*步驟1：* 更新混合現實 Unity 專案以使用 *低品質* 層級設定</span><span class="sxs-lookup"><span data-stu-id="dd756-160">*Step 1:* Update mixed reality Unity projects to use the *Low Quality* level setting</span></span>  
<span data-ttu-id="dd756-161">**編輯**  > **專案設定**，然後選取 [**品質**] 類別 > 選取 UWP 平臺的 *低品質*</span><span class="sxs-lookup"><span data-stu-id="dd756-161">**Edit** > **Project Settings**, then select the **Quality** category >  Select *Low Quality* for the UWP Platform</span></span>

<span data-ttu-id="dd756-162">*步驟2：* 針對每個 Unity 場景檔案，停用 [即時全域照明](https://docs.unity3d.com/Manual/LightMode-Realtime.html)</span><span class="sxs-lookup"><span data-stu-id="dd756-162">*Step 2:* For every Unity scene file, disable [real-time Global Illumination](https://docs.unity3d.com/Manual/LightMode-Realtime.html)</span></span>  
<span data-ttu-id="dd756-163">**視窗**  > 轉譯  > **光源設定**  > [取消核取 *即時全域照明*](https://docs.unity3d.com/Manual/GlobalIllumination.html)</span><span class="sxs-lookup"><span data-stu-id="dd756-163">**Window** > **Rendering** > **Lighting Settings** > [Uncheck *Real-time Global Illumination*](https://docs.unity3d.com/Manual/GlobalIllumination.html)</span></span>

### <a name="depth-buffer-sharing-hololens"></a><span data-ttu-id="dd756-164"> (HoloLens) 的深度緩衝區共用</span><span class="sxs-lookup"><span data-stu-id="dd756-164">Depth buffer sharing (HoloLens)</span></span>

<span data-ttu-id="dd756-165">如果是針對 Windows Mixed Reality 平臺進行開發，而在特別的 HoloLens 中，啟用 *XR 設定* 下的 *深度緩衝區共用* 有助於進行全像 [影像穩定](../Performance/Hologram-Stabilization.md)。</span><span class="sxs-lookup"><span data-stu-id="dd756-165">If developing for the Windows Mixed Reality platform and in particular HoloLens, enabling *Depth Buffer Sharing* under *XR Settings* can help with [hologram stabilization](../Performance/Hologram-Stabilization.md).</span></span> <span data-ttu-id="dd756-166">不過，處理深度緩衝區可能會產生效能成本，特別是在使用 [24 位深度格式](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html)時。</span><span class="sxs-lookup"><span data-stu-id="dd756-166">However, processing of the depth buffer can incur a performance cost, particularly if using [24-bit depth format](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html).</span></span> <span data-ttu-id="dd756-167">因此， *強烈建議您* 將深度緩衝區設定為16位精確度。</span><span class="sxs-lookup"><span data-stu-id="dd756-167">Thus, it is *highly recommended* to configure the depth buffer to 16-bit precision.</span></span>

<span data-ttu-id="dd756-168">如果因為較低的位格式而發生 [z](https://en.wikipedia.org/wiki/Z-fighting) 操作，請確認所有相機的最大 [剪輯平面](https://docs.unity3d.com/Manual/class-Camera.html) 都設為應用程式的最小可能值。</span><span class="sxs-lookup"><span data-stu-id="dd756-168">If [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) occurs due to the lower bit format, confirm the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) of all cameras is set to the lowest possible value for the application.</span></span> <span data-ttu-id="dd756-169">Unity 預設會設定變更為1000m 的裁剪平面。</span><span class="sxs-lookup"><span data-stu-id="dd756-169">Unity by default sets a far clip plane of 1000m.</span></span> <span data-ttu-id="dd756-170">在 HoloLens 上，50m 的剪輯平面通常比大部分的應用程式案例還多。</span><span class="sxs-lookup"><span data-stu-id="dd756-170">On HoloLens, a far clip plane of 50m is generally more than enough for most application scenarios.</span></span>

> [!NOTE]
> <span data-ttu-id="dd756-171">如果使用 *16 位深度格式*，則樣板緩衝區所需的效果將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。</span><span class="sxs-lookup"><span data-stu-id="dd756-171">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="dd756-172">相反地，選取 *24 位深度格式* 通常會建立8位的樣板緩衝區（如果適用于端點圖形平台）。</span><span class="sxs-lookup"><span data-stu-id="dd756-172">Selecting *24-bit depth format* conversely will generally create an 8-bit stencil buffer, if applicable on the endpoint graphics platform.</span></span>
>
> <span data-ttu-id="dd756-173">如果使用需要樣板緩衝區的 [遮罩元件](https://docs.unity3d.com/Manual/script-Mask.html) ，請考慮改用 [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) ，這不需要樣板緩衝區，因此可與 *16 位深度格式* 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="dd756-173">If using a [Mask component](https://docs.unity3d.com/Manual/script-Mask.html) which requires the stencil buffer, consider using [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) instead, which does not require the stencil buffer and thus can be used in conjunction with a *16-bit depth format*.</span></span>

> [!NOTE]
> <span data-ttu-id="dd756-174">若要快速判斷場景中的哪些物件不會以視覺化方式寫入深度緩衝區，可以使用 MRTK 設定檔中 *編輯器設定* 下的轉譯 [*深度緩衝區* 公用程式](../out-of-scope/MixedRealityConfigurationGuide.md#editor-utilities)。</span><span class="sxs-lookup"><span data-stu-id="dd756-174">To quickly determine which objects in a scene do not write to the depth buffer visually, one can use the [*Render Depth Buffer* utility](../out-of-scope/MixedRealityConfigurationGuide.md#editor-utilities) under the *Editor Settings* in the MRTK Configuration profile.</span></span>

### <a name="optimize-mesh-data"></a><span data-ttu-id="dd756-175">優化網格資料</span><span class="sxs-lookup"><span data-stu-id="dd756-175">Optimize Mesh Data</span></span>

<span data-ttu-id="dd756-176">[優化網格資料](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html)設定會嘗試在您的應用程式中移除未使用的頂點屬性。</span><span class="sxs-lookup"><span data-stu-id="dd756-176">The [Optimize Mesh Data](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) settings tries to remove unused vertex attributes within your application.</span></span> <span data-ttu-id="dd756-177">這項設定會藉由在組建中每個網格上每個資料的每個著色器上執行，來執行這項設定。</span><span class="sxs-lookup"><span data-stu-id="dd756-177">The setting performs this by running over every shader pass in every material that is on every mesh in the build.</span></span> <span data-ttu-id="dd756-178">這適用于遊戲資料大小和執行時間效能，但可能會大幅阻礙組建時間。</span><span class="sxs-lookup"><span data-stu-id="dd756-178">This is good for game data size and runtime performance but can drastically hinder build times.</span></span>

<span data-ttu-id="dd756-179">建議您在開發期間停用此設定，並在建立「主要」組建期間重新啟用。</span><span class="sxs-lookup"><span data-stu-id="dd756-179">It is recommended to disable this setting during development and re-enable during "Master" build creation.</span></span> <span data-ttu-id="dd756-180">您可以在 [**編輯**  >  **專案設定**  >  **播放機**  >  **其他設定**  >  **優化網格資料**] 下找到此設定。</span><span class="sxs-lookup"><span data-stu-id="dd756-180">The setting can be found under **Edit** > **Project Settings** > **Player** > **Other Settings** > **Optimize Mesh Data**.</span></span>

## <a name="general-recommendations"></a><span data-ttu-id="dd756-181">一般建議</span><span class="sxs-lookup"><span data-stu-id="dd756-181">General recommendations</span></span>

<span data-ttu-id="dd756-182">對於混合的現實開發人員來說，效能可能是不明確且不斷變化的挑戰，以及將效能合理化的知識範圍很廣。</span><span class="sxs-lookup"><span data-stu-id="dd756-182">Performance can be an ambiguous and constantly changing challenge for mixed reality developers and the spectrum of knowledge to rationalize performance is vast.</span></span> <span data-ttu-id="dd756-183">但有一些一般建議可瞭解如何處理應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="dd756-183">There are some general recommendations for understanding how to approach performance for an application though.</span></span>

<span data-ttu-id="dd756-184">將應用程式的執行簡化為 *CPU* 或 *GPU* 上執行的片段，並據以識別應用程式是否由任一元件所限制，是很有用的。</span><span class="sxs-lookup"><span data-stu-id="dd756-184">It is useful to simplify the execution of an application into the pieces that run on the *CPU* or the *GPU* and thus identify whether an app is bounded by either component.</span></span>  <span data-ttu-id="dd756-185">可能會有瓶頸跨越處理單位以及必須仔細調查的一些獨特案例。</span><span class="sxs-lookup"><span data-stu-id="dd756-185">There can be bottlenecks that span both processing units and some unique scenarios that have to be carefully investigated.</span></span> <span data-ttu-id="dd756-186">不過，若要開始使用，最好先瞭解應用程式的執行時間。</span><span class="sxs-lookup"><span data-stu-id="dd756-186">However, for getting started, it is good to grasp where an application is executing for the most amount of time.</span></span>

### <a name="gpu-bounded"></a><span data-ttu-id="dd756-187">GPU 界限</span><span class="sxs-lookup"><span data-stu-id="dd756-187">GPU bounded</span></span>

<span data-ttu-id="dd756-188">由於混合現實應用程式大部分的平臺都是利用 [stereoscopic](https://en.wikipedia.org/wiki/Stereoscopy)轉譯，因此因為轉譯「全半寬」畫面的本質，所以通常是 GPU 限定的。</span><span class="sxs-lookup"><span data-stu-id="dd756-188">Since most platforms for mixed reality applications are utilizing [stereoscopic rendering](https://en.wikipedia.org/wiki/Stereoscopy), it is very common to be GPU-bounded due to the nature of rendering a "double-wide" screen.</span></span> <span data-ttu-id="dd756-189">Futhermore，行動混合現實平臺（例如 HoloLens 或 Oculus）會受到行動類別 CPU & GPU 處理能力的限制。</span><span class="sxs-lookup"><span data-stu-id="dd756-189">Futhermore, mobile mixed reality platforms such as HoloLens or Oculus Quest will be limited by mobile-class CPU & GPU processing power.</span></span>

<span data-ttu-id="dd756-190">將焦點放在 GPU 上時，通常會有兩個重要的階段，應用程式必須完成每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="dd756-190">When focusing on the GPU, there are generally two important stages that an application must complete every frame.</span></span>

1. <span data-ttu-id="dd756-191">執行 [頂點著色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)</span><span class="sxs-lookup"><span data-stu-id="dd756-191">Execute the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)</span></span>
2. <span data-ttu-id="dd756-192">執行 [圖元著色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (也稱為片段著色器) </span><span class="sxs-lookup"><span data-stu-id="dd756-192">Execute the [pixel shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (also known as the fragment shader)</span></span>

<span data-ttu-id="dd756-193">如果沒有深入探討電腦圖形 & 轉譯 [管線](https://en.wikipedia.org/wiki/Graphics_pipeline)的複雜欄位，每個著色器階段都是在 GPU 上執行的程式，以產生下列專案。</span><span class="sxs-lookup"><span data-stu-id="dd756-193">Without deep diving into the complex field of computer graphics & [rendering pipelines](https://en.wikipedia.org/wiki/Graphics_pipeline), each shader stage is a program that runs on the GPU to produce the following.</span></span>

1. <span data-ttu-id="dd756-194">頂點著色器會將網格頂點轉換成螢幕空間中的座標 (例如</span><span class="sxs-lookup"><span data-stu-id="dd756-194">Vertex shaders transform mesh vertices to coordinates in screen-space (i.e</span></span> <span data-ttu-id="dd756-195">每個頂點執行的程式碼) </span><span class="sxs-lookup"><span data-stu-id="dd756-195">code executed per vertex)</span></span>
2. <span data-ttu-id="dd756-196">圖元著色器會計算針對指定圖元和網格片段繪製的色彩 (例如</span><span class="sxs-lookup"><span data-stu-id="dd756-196">Pixel shaders calculate the color to draw for a given pixel and mesh fragment (i.e</span></span> <span data-ttu-id="dd756-197">每圖元執行的程式碼) </span><span class="sxs-lookup"><span data-stu-id="dd756-197">code execute per pixel)</span></span>

<span data-ttu-id="dd756-198">就效能微調而言，將焦點放在優化圖元著色器中的作業時，通常會更豐富。</span><span class="sxs-lookup"><span data-stu-id="dd756-198">In regards to performance tuning, it is usually more fruitful to focus on optimizing the operations in the pixel shader.</span></span> <span data-ttu-id="dd756-199">應用程式可能只需要繪製一個 cube，它只會是8個頂點。</span><span class="sxs-lookup"><span data-stu-id="dd756-199">An application may only need to draw a cube which will just be 8 vertices.</span></span> <span data-ttu-id="dd756-200">不過，cube 所佔用的螢幕空間可能是以上百萬圖元為單位。</span><span class="sxs-lookup"><span data-stu-id="dd756-200">However, the screen space that cube occupies is likely on the order of millions of pixels.</span></span> <span data-ttu-id="dd756-201">因此，如果在圖元著色器上減少了10個作業，減少著色器程式碼的速度會比頂點著色器更多。</span><span class="sxs-lookup"><span data-stu-id="dd756-201">Thus, reducing shader code by say 10 operations can save significantly more work if reduced on the pixel shader than the vertex shader.</span></span>

<span data-ttu-id="dd756-202">這是利用 [MRTK 標準著色器](../features/README_MRTKStandardShader.md) 的主要原因之一，因為此著色器通常會在每個圖元 & 頂點執行比 Unity 標準著色器更少的指令，同時達到可比較的美觀結果。</span><span class="sxs-lookup"><span data-stu-id="dd756-202">This is one of the primary reasons for leveraging the [MRTK Standard shader](../features/README_MRTKStandardShader.md) as this shader generally executes many less instructions per pixel & vertex than the Unity Standard shader while achieving comparable aesthetic results.</span></span>

|    <span data-ttu-id="dd756-203">CPU 優化</span><span class="sxs-lookup"><span data-stu-id="dd756-203">CPU Optimizations</span></span>      |             <span data-ttu-id="dd756-204">GPU 優化</span><span class="sxs-lookup"><span data-stu-id="dd756-204">GPU Optimizations</span></span>              |
|---------------------------|--------------------------------------------|
| <span data-ttu-id="dd756-205">應用程式模擬邏輯</span><span class="sxs-lookup"><span data-stu-id="dd756-205">App simulation logic</span></span>      | <span data-ttu-id="dd756-206">轉譯作業</span><span class="sxs-lookup"><span data-stu-id="dd756-206">Rendering operations</span></span> |
| <span data-ttu-id="dd756-207">簡化物理</span><span class="sxs-lookup"><span data-stu-id="dd756-207">Simplify Physics</span></span>          | <span data-ttu-id="dd756-208">減少照明計算</span><span class="sxs-lookup"><span data-stu-id="dd756-208">Reduce lighting calculations</span></span> |
| <span data-ttu-id="dd756-209">簡化動畫</span><span class="sxs-lookup"><span data-stu-id="dd756-209">Simplify Animations</span></span>       | <span data-ttu-id="dd756-210">減少繪製物件 & 數目的多邊形計數</span><span class="sxs-lookup"><span data-stu-id="dd756-210">Reduce polygon count & # of drawable objects</span></span> |
| <span data-ttu-id="dd756-211">管理垃圾收集</span><span class="sxs-lookup"><span data-stu-id="dd756-211">Manage Garbage Collection</span></span> | <span data-ttu-id="dd756-212">減少透明物件的數目</span><span class="sxs-lookup"><span data-stu-id="dd756-212">Reduce # of transparent objects</span></span> |
| <span data-ttu-id="dd756-213">快取參考</span><span class="sxs-lookup"><span data-stu-id="dd756-213">Cache References</span></span>          | <span data-ttu-id="dd756-214">避免後續處理/全螢幕效果</span><span class="sxs-lookup"><span data-stu-id="dd756-214">Avoid post-processing/full-screen effects</span></span>  |

### <a name="draw-call-instancing"></a><span data-ttu-id="dd756-215">繪製呼叫實例</span><span class="sxs-lookup"><span data-stu-id="dd756-215">Draw call instancing</span></span>

<span data-ttu-id="dd756-216">Unity 中可降低效能的最常見錯誤之一，就是在執行時間複製材質。</span><span class="sxs-lookup"><span data-stu-id="dd756-216">One of the most common mistakes in Unity that reduces performance is cloning materials at runtime.</span></span> <span data-ttu-id="dd756-217">如果 Gameobject 共用相同的材質和/或相同的網格，則可以透過 *[靜態批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)*、 *[動態批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)* 和 *[GPU 實例](https://docs.unity3d.com/Manual/GPUInstancing.html)* 等技術，將它們優化成單一繪圖呼叫。</span><span class="sxs-lookup"><span data-stu-id="dd756-217">If GameObjects share the same material and/or are the same mesh, they can be optimized into single draw calls via techniques such as *[static batching](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, *[dynamic batching](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, and *[GPU Instancing](https://docs.unity3d.com/Manual/GPUInstancing.html)*.</span></span> <span data-ttu-id="dd756-218">但是，如果開發人員在執行時間修改轉譯器 [材質](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 的屬性，Unity 將會建立所指派之材質的複製複本。</span><span class="sxs-lookup"><span data-stu-id="dd756-218">However, if developer's modify properties of a [Renderer's material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) at runtime, Unity will create a clone copy of the assigned material.</span></span>

<span data-ttu-id="dd756-219">例如，如果場景中有 100 cube，開發人員可能會想要在執行時間為每個 cube 指派唯一的色彩。</span><span class="sxs-lookup"><span data-stu-id="dd756-219">For example, if there are a 100 cubes in a scene, a developer may want to assign a unique color to each at runtime.</span></span> <span data-ttu-id="dd756-220">轉譯器的存取權。 c # 中的 [*color*](https://docs.unity3d.com/ScriptReference/Material-color.html) 將會讓 Unity 在記憶體中為這個特定的轉譯器/GameObject 建立新的材質。</span><span class="sxs-lookup"><span data-stu-id="dd756-220">The access of [*renderer.material.color*](https://docs.unity3d.com/ScriptReference/Material-color.html) in C# will make Unity create a new material in memory for this particular renderer/GameObject.</span></span> <span data-ttu-id="dd756-221">每個 100 cube 都有自己的資料，因此不能將它們合併成一個繪製呼叫，而是會成為100繪製從 CPU 到 GPU 的呼叫要求。</span><span class="sxs-lookup"><span data-stu-id="dd756-221">Each of the 100 cubes will have its own material and thus they cannot be merged together into one draw call, but instead will become 100 draw call requests from the CPU to the GPU.</span></span>

<span data-ttu-id="dd756-222">為了克服這種障礙，並且仍為每個 cube 指派獨特的色彩，開發人員應該利用 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)。</span><span class="sxs-lookup"><span data-stu-id="dd756-222">To overcome this obstacle and still assign a unique color per cube, developers should leverage [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span>

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a><span data-ttu-id="dd756-223">Unity 效能工具</span><span class="sxs-lookup"><span data-stu-id="dd756-223">Unity performance tools</span></span>

<span data-ttu-id="dd756-224">Unity 提供編輯器內建的絕佳效能工具。</span><span class="sxs-lookup"><span data-stu-id="dd756-224">Unity provides great performance tools that are built into the editor.</span></span>

- [<span data-ttu-id="dd756-225">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="dd756-225">Unity Profiler</span></span>](https://docs.unity3d.com/Manual//Profiler.html)
- [<span data-ttu-id="dd756-226">Unity 框架偵錯工具</span><span class="sxs-lookup"><span data-stu-id="dd756-226">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

<span data-ttu-id="dd756-227">如果評估一個著色器與另一個著色器之間的粗略效能取捨，則編譯每個著色器並查看每個著色器階段的作業數目會很有用。</span><span class="sxs-lookup"><span data-stu-id="dd756-227">If estimating the rough performance tradeoff between one shader and another, it is useful to compile each shader and view the number of operations per shader stage.</span></span> <span data-ttu-id="dd756-228">這可以藉由選取 [著色器資產](https://docs.unity3d.com/Manual/class-Shader.html) ，然後按一下 [ *編譯] 和 [顯示程式碼* ] 按鈕來完成。</span><span class="sxs-lookup"><span data-stu-id="dd756-228">This can be done by selecting a [shader asset](https://docs.unity3d.com/Manual/class-Shader.html) and clicking the *Compile and show code* button.</span></span> <span data-ttu-id="dd756-229">這會編譯所有著色器變異，並以結果開啟 visual studio。</span><span class="sxs-lookup"><span data-stu-id="dd756-229">This will compile all the shader variants and open visual studio with the results.</span></span> <span data-ttu-id="dd756-230">注意：所產生的統計資料結果可能會根據在使用指定著色器的材質上啟用了哪些功能而有所不同。</span><span class="sxs-lookup"><span data-stu-id="dd756-230">Note: The statistic results produced may vary depending on what features have been enabled on materials utilizing the given shader.</span></span> <span data-ttu-id="dd756-231">Unity 只會編譯目前專案中直接使用的著色器變數。</span><span class="sxs-lookup"><span data-stu-id="dd756-231">Unity will only compile the shader variants being directly used in the current project.</span></span>

<span data-ttu-id="dd756-232">Unity 標準著色器統計資料範例</span><span class="sxs-lookup"><span data-stu-id="dd756-232">Unity Standard shader statistics example</span></span>

![Unity 標準著色器統計資料](../features/Images/Performance/UnityStandardShader-Stats.PNG)

<span data-ttu-id="dd756-234">MRTK 標準著色器統計資料範例</span><span class="sxs-lookup"><span data-stu-id="dd756-234">MRTK Standard shader statistics example</span></span>

![MRTK 標準著色器統計資料](../features/Images/Performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a><span data-ttu-id="dd756-236">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd756-236">See also</span></span>

### <a name="unity"></a><span data-ttu-id="dd756-237">Unity</span><span class="sxs-lookup"><span data-stu-id="dd756-237">Unity</span></span>

- [<span data-ttu-id="dd756-238">適用于初學者的 Unity 效能優化</span><span class="sxs-lookup"><span data-stu-id="dd756-238">Unity Performance Optimization for Beginners</span></span>](https://www.youtube.com/watch?v=1e5WY2qf600)
- [<span data-ttu-id="dd756-239">Unity 效能優化教學課程</span><span class="sxs-lookup"><span data-stu-id="dd756-239">Unity Performance Optimization Tutorials</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [<span data-ttu-id="dd756-240">Unity 優化最佳做法</span><span class="sxs-lookup"><span data-stu-id="dd756-240">Unity Optimization Best Practices</span></span>](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [<span data-ttu-id="dd756-241">優化圖形效能</span><span class="sxs-lookup"><span data-stu-id="dd756-241">Optimizing graphics performance</span></span>](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [<span data-ttu-id="dd756-242">行動優化實用指南</span><span class="sxs-lookup"><span data-stu-id="dd756-242">Mobile Optimization Practical Guide</span></span>](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a><span data-ttu-id="dd756-243">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="dd756-243">Windows Mixed Reality</span></span>

- [<span data-ttu-id="dd756-244">適用于 Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="dd756-244">Recommended Settings for Unity</span></span>](https://docs.microsoft.com/windows/mixed-reality/recommended-settings-for-unity)
- [<span data-ttu-id="dd756-245">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="dd756-245">Understanding Performance for Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [<span data-ttu-id="dd756-246">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="dd756-246">Performance recommendations for Unity</span></span>](https://docs.microsoft.com/windows/mixed-reality/performance-recommendations-for-unity)
- [<span data-ttu-id="dd756-247">適用于 Windows Unity 的事件追蹤指南</span><span class="sxs-lookup"><span data-stu-id="dd756-247">Event Tracing for Windows Unity Guide</span></span>](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a><span data-ttu-id="dd756-248">Oculus</span><span class="sxs-lookup"><span data-stu-id="dd756-248">Oculus</span></span>

- [<span data-ttu-id="dd756-249">效能方針</span><span class="sxs-lookup"><span data-stu-id="dd756-249">Performance Guidelines</span></span>](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [<span data-ttu-id="dd756-250">效能工具</span><span class="sxs-lookup"><span data-stu-id="dd756-250">Performance Tools</span></span>](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a><span data-ttu-id="dd756-251">網格優化</span><span class="sxs-lookup"><span data-stu-id="dd756-251">Mesh optimization</span></span>

- [<span data-ttu-id="dd756-252">優化3D 模型</span><span class="sxs-lookup"><span data-stu-id="dd756-252">Optimize 3D models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [<span data-ttu-id="dd756-253">轉換和優化即時3D 模型的最佳作法</span><span class="sxs-lookup"><span data-stu-id="dd756-253">Best practices for converting and optimizing real-time 3D models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)
