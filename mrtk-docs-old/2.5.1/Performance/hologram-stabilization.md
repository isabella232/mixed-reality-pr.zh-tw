---
title: 全像影像-穩定
description: 不同環境和畫面播放速率條件下的全像影像效能。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、環境追蹤、TMP、
ms.openlocfilehash: e6aeb93c8c79a0e79ef043d7c4171f36af2de194
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781000"
---
# <a name="hologram-stabilization"></a><span data-ttu-id="9392b-104">全像穩定</span><span class="sxs-lookup"><span data-stu-id="9392b-104">Hologram stabilization</span></span>

## <a name="performance"></a><span data-ttu-id="9392b-105">效能</span><span class="sxs-lookup"><span data-stu-id="9392b-105">Performance</span></span>

<span data-ttu-id="9392b-106">為了讓基礎混合現實平臺和裝置產生最佳結果，請務必達到執行畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="9392b-106">In order for the underlying mixed reality platform and device to produce the best results, it is important to achieve performing frame rates.</span></span> <span data-ttu-id="9392b-107">目標畫面播放速率 (例如： 60 FPS 或 90 FPS) 會因不同的平臺和裝置而有所不同。</span><span class="sxs-lookup"><span data-stu-id="9392b-107">The target framerate (ex: 60 FPS or 90 FPS) will vary across platforms and devices.</span></span> <span data-ttu-id="9392b-108">不過，混合現實應用程式的符合幀率將會有穩定的全像投影，以及有效率的標頭追蹤、手動追蹤等等。</span><span class="sxs-lookup"><span data-stu-id="9392b-108">However, mixed reality applications meeting framerate will have stable holograms as well as efficient head tracking, hand tracking and more.</span></span>  

## <a name="environment-tracking"></a><span data-ttu-id="9392b-109">環境追蹤</span><span class="sxs-lookup"><span data-stu-id="9392b-109">Environment tracking</span></span>

<span data-ttu-id="9392b-110">穩定的全像攝影轉譯非常依賴平臺 & 裝置的 head 姿勢追蹤。</span><span class="sxs-lookup"><span data-stu-id="9392b-110">Stable holographic rendering heavily relies on head-pose tracking by the platform & device.</span></span> <span data-ttu-id="9392b-111">Unity 將會從相機中的每個畫面格呈現每個畫面格，並由基礎平臺進行預估和提供。</span><span class="sxs-lookup"><span data-stu-id="9392b-111">Unity will render the scene every frame from the camera pose estimated and supplied by the underlying platform.</span></span> <span data-ttu-id="9392b-112">如果此追蹤未正確遵循實際的 head 移動，則會以視覺化方式呈現全像影像。</span><span class="sxs-lookup"><span data-stu-id="9392b-112">If this tracking does not correctly follow actual head movement, then holograms will appear visually inaccurate.</span></span> <span data-ttu-id="9392b-113">這對 AR 裝置（例如 HoloLens）來說特別明顯，也很重要，因為使用者可以將虛擬全像是真實世界的關聯性。</span><span class="sxs-lookup"><span data-stu-id="9392b-113">This is especially evident and important for AR devices like HoloLens where users can relate virtual holograms to the real world.</span></span> <span data-ttu-id="9392b-114">效能對於可靠的標頭追蹤很重要，但也有 [其他重要功能](https://docs.microsoft.com/windows/mixed-reality/environment-considerations-for-hololens)。</span><span class="sxs-lookup"><span data-stu-id="9392b-114">Performance is significant for reliable head tracking, but there can be [other important features](https://docs.microsoft.com/windows/mixed-reality/environment-considerations-for-hololens), as well.</span></span> <span data-ttu-id="9392b-115">影響使用者體驗的環境元素類型將取決於目標平臺細節。</span><span class="sxs-lookup"><span data-stu-id="9392b-115">The types of environment elements impacting user experience will depend on the targeted platform specifics.</span></span>

## <a name="windows-mixed-reality"></a><span data-ttu-id="9392b-116">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9392b-116">Windows Mixed Reality</span></span>

<span data-ttu-id="9392b-117">Windows Mixed Reality 平臺提供一些在平臺上穩定全息的 [參考](https://docs.microsoft.com/windows/mixed-reality/hologram-stability) 資料。</span><span class="sxs-lookup"><span data-stu-id="9392b-117">The Windows Mixed Reality platform provides some [reference material](https://docs.microsoft.com/windows/mixed-reality/hologram-stability) for stabilizing holograms on the platform.</span></span> <span data-ttu-id="9392b-118">不過，開發人員可以利用一些重要的工具來改善使用者的全像影像視覺體驗。</span><span class="sxs-lookup"><span data-stu-id="9392b-118">There are a handful of key tools though that developers can utilize to improve the hologram visual experience for users.</span></span>

### <a name="depth-buffer-sharing"></a><span data-ttu-id="9392b-119">深度緩衝區共用</span><span class="sxs-lookup"><span data-stu-id="9392b-119">Depth buffer sharing</span></span>

<span data-ttu-id="9392b-120">Unity 開發人員可以選擇將應用程式的深度緩衝區與平臺共用。</span><span class="sxs-lookup"><span data-stu-id="9392b-120">Unity developers have the option of sharing the application's depth buffer with the platform.</span></span> <span data-ttu-id="9392b-121">這會提供目前畫面格所在的全像投影的資訊，平臺可透過硬體輔助的程式（稱為 Late-Stage Reprojection）來利用穩定的全像影像。</span><span class="sxs-lookup"><span data-stu-id="9392b-121">This provides information, where holograms exist for a current frame, that the platform can utilize to stabilize holograms via a hardware-assisted process known as Late-Stage Reprojection.</span></span>

#### <a name="late-stage-reprojection"></a><span data-ttu-id="9392b-122">延遲階段 reprojection</span><span class="sxs-lookup"><span data-stu-id="9392b-122">Late-stage reprojection</span></span>

<span data-ttu-id="9392b-123">在轉譯畫面格結束時，Windows Mixed Reality 平臺會採用應用程式所產生的色彩 & 深度轉譯目標，並轉換最後的畫面輸出，以考慮自從最後一個 head 姿勢預測之後的任何輕微移動。</span><span class="sxs-lookup"><span data-stu-id="9392b-123">At the end of rendering a frame, the Windows Mixed Reality platform takes the color & depth render targets produced by the application and transforms the final screen output to account for any slight head movement since the last head pose prediction.</span></span> <span data-ttu-id="9392b-124">應用程式的遊戲迴圈需要一些時間才能執行。</span><span class="sxs-lookup"><span data-stu-id="9392b-124">An application's game loop takes time to execute.</span></span> <span data-ttu-id="9392b-125">例如，在 60 FPS，這表示應用程式會採用 ~ 16.667 ms 來呈現畫面格。</span><span class="sxs-lookup"><span data-stu-id="9392b-125">For example, at 60 FPS, this means the application is taking ~16.667ms to render a frame.</span></span> <span data-ttu-id="9392b-126">雖然這看起來可能像是相比簡直小巫見大巫的時間，但使用者的位置和方向也會改變，而導致投影的新投射矩陣。</span><span class="sxs-lookup"><span data-stu-id="9392b-126">Even though this may seem like a miniscule amount of time, the user's position and orientation of their head will change resulting in new projection matrices for the camera in rendering.</span></span> <span data-ttu-id="9392b-127">延遲階段 reprojection 會轉換最終影像中的圖元，以考慮這個新的觀點。</span><span class="sxs-lookup"><span data-stu-id="9392b-127">Late-stage reprojection transforms the pixels in the final image to account for this new perspective.</span></span>

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a><span data-ttu-id="9392b-128">每個圖元與穩定平面 LSR</span><span class="sxs-lookup"><span data-stu-id="9392b-128">Per-pixel vs stabilization plane LSR</span></span>

<span data-ttu-id="9392b-129">根據在 Windows Mixed Reality 裝置上執行的裝置端點和作業系統版本，Late-Stage 的 Reprojection 演算法會以圖元為單位執行，或經由 [穩定平面](https://docs.microsoft.com/windows/mixed-reality/hologram-stability#stabilization-plane)執行。</span><span class="sxs-lookup"><span data-stu-id="9392b-129">Depending on the device endpoint and OS version running on a Windows Mixed Reality device, the Late-Stage Reprojection algorithm will either be performed per-pixel or via a [stabilization plane](https://docs.microsoft.com/windows/mixed-reality/hologram-stability#stabilization-plane).</span></span>

##### <a name="per-pixel-depth-based"></a><span data-ttu-id="9392b-130">依圖元深度為基礎</span><span class="sxs-lookup"><span data-stu-id="9392b-130">Per-pixel depth-based</span></span>

<span data-ttu-id="9392b-131">每圖元深度型 reprojection 牽涉到利用深度緩衝區來修改每個圖元的影像輸出，進而在不同的距離進行穩定的全像投影。</span><span class="sxs-lookup"><span data-stu-id="9392b-131">Per-pixel depth-based reprojection involves utilizing the depth buffer to modify the image output per pixel and thus stabilize holograms at various distances.</span></span> <span data-ttu-id="9392b-132">例如，球體的1m 可能會在1千萬個離開的要件前面。</span><span class="sxs-lookup"><span data-stu-id="9392b-132">For example, a sphere 1m away may be in front of a pillar that is 10m away.</span></span> <span data-ttu-id="9392b-133">代表球體的圖元會有不同的轉換，而不是代表要件的圖元，如果使用者稍微略過它們的標頭。</span><span class="sxs-lookup"><span data-stu-id="9392b-133">The pixels representing the sphere will have a different transform than the far away pixels representing the pillar if the user has tilted their head slightly.</span></span> <span data-ttu-id="9392b-134">每個圖元的 reprojection 會將每個圖元的距離差異納入考慮，以取得更精確的 reprojection。</span><span class="sxs-lookup"><span data-stu-id="9392b-134">Per-pixel reprojection will take into account this distance difference at every pixel for more accurate reprojection.</span></span>

##### <a name="stabilization-plane"></a><span data-ttu-id="9392b-135">穩定平面</span><span class="sxs-lookup"><span data-stu-id="9392b-135">Stabilization plane</span></span>

<span data-ttu-id="9392b-136">如果無法建立要與平臺共用的精確深度緩衝區，則另一種形式的 LSR 會利用穩定平面。</span><span class="sxs-lookup"><span data-stu-id="9392b-136">If it is not possible to create an accurate depth buffer to share with the platform, another form of LSR utilizes a stabilization plane.</span></span> <span data-ttu-id="9392b-137">場景中的所有全像全像都能獲得一些穩定的情況，但在所需的平面中的全像投影，將會獲得最大硬體穩定</span><span class="sxs-lookup"><span data-stu-id="9392b-137">All holograms in a scene will receive some stabilization, but holograms lying in the desired plane will receive the maximum hardware stabilization.</span></span> <span data-ttu-id="9392b-138">您可以透過 [Unity 提供](https://docs.microsoft.com/windows/mixed-reality/focus-point-in-unity)的 *HolographicSettings SetFocusPointForFrame* API，將平面的點和法線提供給平臺。</span><span class="sxs-lookup"><span data-stu-id="9392b-138">The point and normal for the plane can be supplied to the platform via the *HolographicSettings.SetFocusPointForFrame* [API provided by Unity](https://docs.microsoft.com/windows/mixed-reality/focus-point-in-unity).</span></span>

#### <a name="depth-buffer-format"></a><span data-ttu-id="9392b-139">深度緩衝區格式</span><span class="sxs-lookup"><span data-stu-id="9392b-139">Depth buffer format</span></span>

<span data-ttu-id="9392b-140">如果以 HoloLens 為目標以進行開發，強烈建議使用16位深度緩衝區格式（相較于24位）。</span><span class="sxs-lookup"><span data-stu-id="9392b-140">If targeting HoloLens for development, it is highly recommended to utilize the 16-bit depth buffer format compared to 24-bit.</span></span> <span data-ttu-id="9392b-141">這可節省效能，但深度值的精確度較低。</span><span class="sxs-lookup"><span data-stu-id="9392b-141">This can save tremendously on performance although depth values will have less precision.</span></span> <span data-ttu-id="9392b-142">若要補償較低的精確度，並避免進行 [z 對](https://en.wikipedia.org/wiki/Z-fighting)，建議您從 Unity 所設定的變更為1000m 預設值減少最 [遠的剪輯平面](https://docs.unity3d.com/Manual/class-Camera.html) 。</span><span class="sxs-lookup"><span data-stu-id="9392b-142">To compensate for the lower precision and avoid [z-fighting](https://en.wikipedia.org/wiki/Z-fighting), it is recommended to reduce the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) from the 1000m default value set by Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="9392b-143">如果使用 *16 位深度格式*，則樣板緩衝區所需的效果將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。</span><span class="sxs-lookup"><span data-stu-id="9392b-143">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="9392b-144">相反地，選取 *24 位深度格式* 通常會建立 [8 位的樣板緩衝區](https://docs.unity3d.com/Manual/SL-Stencil.html)（如果適用于端點圖形平台）。</span><span class="sxs-lookup"><span data-stu-id="9392b-144">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html), if applicable on the endpoint graphics platform.</span></span>

#### <a name="depth-buffer-sharing-in-unity"></a><span data-ttu-id="9392b-145">Unity 中的深度緩衝區共用</span><span class="sxs-lookup"><span data-stu-id="9392b-145">Depth buffer sharing in Unity</span></span>

<span data-ttu-id="9392b-146">為了利用深度型 LSR，開發人員必須採取兩個重要的步驟。</span><span class="sxs-lookup"><span data-stu-id="9392b-146">In order to utilize depth-based LSR, there are two important steps that developers need to take.</span></span>

1. <span data-ttu-id="9392b-147">在 [**編輯**  >  **專案設定**  >  **播放機**  >  **XR 設定**  >  **虛擬實境 sdk** ] 下，> 啟用 **深度緩衝區共用**</span><span class="sxs-lookup"><span data-stu-id="9392b-147">Under **Edit** > **Project Settings** > **Player** > **XR Settings** > **Virtual Reality SDKs** > Enable **Depth Buffer Sharing**</span></span>
    1. <span data-ttu-id="9392b-148">如果以 HoloLens 為目標，建議您也選取 **16 位深度格式** 。</span><span class="sxs-lookup"><span data-stu-id="9392b-148">If targeting HoloLens, it is recommended to select **16-bit depth format** as well.</span></span>
1. <span data-ttu-id="9392b-149">在螢幕上轉譯色彩時，也會呈現深度</span><span class="sxs-lookup"><span data-stu-id="9392b-149">When rendering color on screen, render depth as well</span></span>

<span data-ttu-id="9392b-150">Unity 中的不[透明 gameobject](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)通常會自動寫入深度。</span><span class="sxs-lookup"><span data-stu-id="9392b-150">[Opaque GameObjects](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) in Unity will generally write to depth automatically.</span></span> <span data-ttu-id="9392b-151">不過，透明的 & 文字物件通常不會根據預設寫入深度。</span><span class="sxs-lookup"><span data-stu-id="9392b-151">However, transparent & text objects will generally not write to depth by default.</span></span> <span data-ttu-id="9392b-152">如果使用 MRTK 標準著色器或文字網格 Pro，可以輕鬆地補救。</span><span class="sxs-lookup"><span data-stu-id="9392b-152">If utilizing the MRTK Standard Shader or Text Mesh Pro, this can be easily remedied.</span></span>

> [!NOTE]
> <span data-ttu-id="9392b-153">若要快速判斷場景中的哪些物件不會以視覺化方式寫入深度緩衝區，可以使用 MRTK 設定檔中 *編輯器設定* 下的轉譯 [*深度緩衝區* 公用程式](../configuration/MixedRealityConfigurationGuide.md#editor-utilities)。</span><span class="sxs-lookup"><span data-stu-id="9392b-153">To quickly determine which objects in a scene do not write to the depth buffer visually, one can use the [*Render Depth Buffer* utility](../configuration/MixedRealityConfigurationGuide.md#editor-utilities) under the *Editor Settings* in the MRTK Configuration profile.</span></span>

##### <a name="transparent-mrtk-standard-shader"></a><span data-ttu-id="9392b-154">透明 MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="9392b-154">Transparent MRTK Standard shader</span></span>

<span data-ttu-id="9392b-155">針對使用 [MRTK 標準著色器](../features/rendering/MRTKStandardShader.md)的透明材質，請在 [偵測 *器* ] 視窗中選取要查看的材質。</span><span class="sxs-lookup"><span data-stu-id="9392b-155">For transparent materials using the [MRTK Standard shader](../features/rendering/MRTKStandardShader.md), select the material to view it in the *Inspector* window.</span></span> <span data-ttu-id="9392b-156">然後按一下 [ *立即修正* ] 按鈕，將材質轉換成深度 (例如</span><span class="sxs-lookup"><span data-stu-id="9392b-156">Then click the *Fix Now* button to convert the material to write to depth (i.e</span></span> <span data-ttu-id="9392b-157">) 上的 Z-寫入。</span><span class="sxs-lookup"><span data-stu-id="9392b-157">Z-Write On).</span></span>

<span data-ttu-id="9392b-158">之前</span><span class="sxs-lookup"><span data-stu-id="9392b-158">Before</span></span>

![修正 MRTK 標準著色器之前的深度緩衝區](../features/images/performance/DepthBufferFixNow_Before.PNG)

<span data-ttu-id="9392b-160">After</span><span class="sxs-lookup"><span data-stu-id="9392b-160">After</span></span>

![深度緩衝區固定 MRTK 標準著色器](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a><span data-ttu-id="9392b-162">文字網格 Pro</span><span class="sxs-lookup"><span data-stu-id="9392b-162">Text Mesh Pro</span></span>

<span data-ttu-id="9392b-163">若為文字網格 Pro 物件，請選取 TMP GameObject 以在偵測器中加以查看。</span><span class="sxs-lookup"><span data-stu-id="9392b-163">For Text Mesh Pro objects, select the TMP GameObject to view it in the inspector.</span></span> <span data-ttu-id="9392b-164">在 [材質] 元件下，將指派之材質的著色器切換為使用 MRTK TextMeshPro 著色器。</span><span class="sxs-lookup"><span data-stu-id="9392b-164">Under the material component, switch the shader for the assigned material to use the MRTK TextMeshPro shader.</span></span>

![文字網格 Pro 深度緩衝區修正](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a><span data-ttu-id="9392b-166">自訂著色器</span><span class="sxs-lookup"><span data-stu-id="9392b-166">Custom shader</span></span>

<span data-ttu-id="9392b-167">如果撰寫自訂著色器，請將 [ZWrite 旗](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) 標加入至 *傳遞* 區塊定義的頂端，以設定要寫入深度緩衝區的著色器。</span><span class="sxs-lookup"><span data-stu-id="9392b-167">If writing a custom shader, add the [ZWrite flag](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) to the top of the *Pass* block definition to configure the shader to write to the depth buffer.</span></span>

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a><span data-ttu-id="9392b-168">不透明 backings</span><span class="sxs-lookup"><span data-stu-id="9392b-168">Opaque backings</span></span>

<span data-ttu-id="9392b-169">如果上述方法不適用於指定的案例 (即</span><span class="sxs-lookup"><span data-stu-id="9392b-169">If the above methods do not work for a given scenario (i.e</span></span> <span data-ttu-id="9392b-170">您可以使用 Unity UI) ，將另一個物件寫入深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9392b-170">using Unity UI), it is possible to have another object write to the depth buffer.</span></span> <span data-ttu-id="9392b-171">常見的範例是在場景中的浮動面板上使用 Unity UI 文字。</span><span class="sxs-lookup"><span data-stu-id="9392b-171">A common example is using Unity UI Text on a floating panel in a scene.</span></span> <span data-ttu-id="9392b-172">藉由讓面板不透明或至少寫入深度，此面板 & 的文字將會由平臺穩定，因為它們的 z 值彼此接近。</span><span class="sxs-lookup"><span data-stu-id="9392b-172">By making the panel opaque or at least writing to depth, then both the text & the panel will be stabilized by the platform since their z-values are so close to each other.</span></span>

### <a name="worldanchors-hololens"></a><span data-ttu-id="9392b-173">WorldAnchors (HoloLens) </span><span class="sxs-lookup"><span data-stu-id="9392b-173">WorldAnchors (HoloLens)</span></span>

<span data-ttu-id="9392b-174">除了確保符合正確的設定，以確保視覺穩定性，請務必確保全像地理位置在正確的實體位置維持穩定。</span><span class="sxs-lookup"><span data-stu-id="9392b-174">Along with ensuring the correct configurations are met to ensure visual stability, it is important to ensure holograms remain stable at their correct physical locations.</span></span> <span data-ttu-id="9392b-175">若要在實體空間中通知平臺的重要位置，開發人員可以在需要保持在同一處的 Gameobject 上利用 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 。</span><span class="sxs-lookup"><span data-stu-id="9392b-175">To inform the platform on important locations in a physical space, developers can leverage [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) on GameObjects that need to stay in one place.</span></span> <span data-ttu-id="9392b-176">[WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html)是新增至 GameObject 的元件，可對該物件的轉換取得絕對控制權。</span><span class="sxs-lookup"><span data-stu-id="9392b-176">A [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) is a component added to a GameObject that takes absolute control over that object's transform.</span></span>

<span data-ttu-id="9392b-177">HoloLens 這類裝置會不斷地掃描和學習環境。</span><span class="sxs-lookup"><span data-stu-id="9392b-177">Devices such as HoloLens are constantly scanning and learning about the environment.</span></span> <span data-ttu-id="9392b-178">因此，當 HoloLens 追蹤移動 & 空間中的位置時，將會更新其估價，並 [調整 Unity 座標系統](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity)。</span><span class="sxs-lookup"><span data-stu-id="9392b-178">Thus, as the HoloLens tracks movement & position in space, its estimates will be updated and the [Unity coordinate system adjusted](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity).</span></span> <span data-ttu-id="9392b-179">例如，如果在一開始就將 GameObject 從相機放置1百萬個，則在 HoloLens 追蹤環境時，可能會發現 GameObject 所在的實體點實際上是 1.1 m。</span><span class="sxs-lookup"><span data-stu-id="9392b-179">For example, if a GameObject is placed 1m from the camera at start, as the HoloLens tracks the environment, it may realize the physical point where the GameObject is located is actually 1.1m away.</span></span> <span data-ttu-id="9392b-180">這會導致全息全像離開。</span><span class="sxs-lookup"><span data-stu-id="9392b-180">This would result in the hologram drifting.</span></span> <span data-ttu-id="9392b-181">將 WorldAnchor 套用至 GameObject，可讓錨點控制物件的轉換，讓物件保持在正確的實體位置 (也就是</span><span class="sxs-lookup"><span data-stu-id="9392b-181">Applying a WorldAnchor to a GameObject will enable the anchor to control the object's transform so that the object will remain at the correct physical location (i.e</span></span> <span data-ttu-id="9392b-182">在執行時間) 更新為 1.1 m 而不是1m。</span><span class="sxs-lookup"><span data-stu-id="9392b-182">update to 1.1m away instead of 1m at runtime).</span></span> <span data-ttu-id="9392b-183">若要跨應用程式會話保存 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) ，開發人員可以使用 [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) 來 [儲存和載入 WorldAnchors](https://docs.microsoft.com/windows/mixed-reality/persistence-in-unity)。</span><span class="sxs-lookup"><span data-stu-id="9392b-183">To persist [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) across app sessions, developers can employ the [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) to [save and load WorldAnchors](https://docs.microsoft.com/windows/mixed-reality/persistence-in-unity).</span></span>

> [!NOTE]
> <span data-ttu-id="9392b-184">將 WorldAnchor 元件新增至 GameObject 之後，就無法修改該 GameObject 的轉換 (例如</span><span class="sxs-lookup"><span data-stu-id="9392b-184">Once a WorldAnchor component has been added to a GameObject, it is not possible to modify that GameObject's transform (i.e</span></span> <span data-ttu-id="9392b-185">transform。 position = x) 。</span><span class="sxs-lookup"><span data-stu-id="9392b-185">transform.position = x).</span></span> <span data-ttu-id="9392b-186">開發人員必須移除 WorldAnchor 來編輯轉換。</span><span class="sxs-lookup"><span data-stu-id="9392b-186">A developer must remove the WorldAnchor to edit the transform.</span></span>

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

## <a name="see-also"></a><span data-ttu-id="9392b-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9392b-187">See also</span></span>

- [<span data-ttu-id="9392b-188">效能</span><span class="sxs-lookup"><span data-stu-id="9392b-188">Performance</span></span>](PerfGettingStarted.md)
- [<span data-ttu-id="9392b-189">HoloLens 的環境考慮</span><span class="sxs-lookup"><span data-stu-id="9392b-189">Environment Considerations for HoloLens</span></span>](https://docs.microsoft.com/windows/mixed-reality/environment-considerations-for-hololens)
- [<span data-ttu-id="9392b-190">全像 Windows 混合式的穩定性</span><span class="sxs-lookup"><span data-stu-id="9392b-190">Hologram Stability Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/hologram-stability)
- [<span data-ttu-id="9392b-191">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="9392b-191">Focus point in Unity</span></span>](https://docs.microsoft.com/windows/mixed-reality/focus-point-in-unity)
- [<span data-ttu-id="9392b-192">Unity 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="9392b-192">Coordinate systems in Unity</span></span>](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity)
- [<span data-ttu-id="9392b-193">Unity 中的持續性</span><span class="sxs-lookup"><span data-stu-id="9392b-193">Persistence in Unity</span></span>](https://docs.microsoft.com/windows/mixed-reality/persistence-in-unity)
- [<span data-ttu-id="9392b-194">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="9392b-194">Understanding Performance for Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [<span data-ttu-id="9392b-195">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="9392b-195">Performance recommendations for Unity</span></span>](https://docs.microsoft.com/windows/mixed-reality/performance-recommendations-for-unity)
