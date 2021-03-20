---
title: MRTKStandardShader
description: MRTKStandardShader 檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、材質著色器
ms.openlocfilehash: 608710296ec9bcf9dcb8a7672cbe356c3b1a0603
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702384"
---
# <a name="mrtk-standard-shader"></a><span data-ttu-id="f2762-104">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="f2762-104">MRTK Standard Shader</span></span>

![標準著色器範例](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

<span data-ttu-id="f2762-106">MRTK 標準陰影系統利用單一、彈性的著色器，其可達成與 Unity 標準著色器類似的視覺效果、實行 [Fluent Design 系統](https://www.microsoft.com/design/fluent/) 準則，並在混合現實裝置上維持效能。</span><span class="sxs-lookup"><span data-stu-id="f2762-106">MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implement [Fluent Design System](https://www.microsoft.com/design/fluent/) principles, and remain performant on mixed reality devices.</span></span>

## <a name="example-scenes"></a><span data-ttu-id="f2762-107">範例場景</span><span class="sxs-lookup"><span data-stu-id="f2762-107">Example scenes</span></span>

<span data-ttu-id="f2762-108">您可以在下的 **MaterialGallery** 場景中找到著色器材質範例 `MRTK/Examples/Demos/StandardShader/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="f2762-108">You can find the shader material examples in the **MaterialGallery** scene under `MRTK/Examples/Demos/StandardShader/Scenes/`.</span></span> <span data-ttu-id="f2762-109">此場景中的所有資料都是使用 MRTK/Standard 著色器。</span><span class="sxs-lookup"><span data-stu-id="f2762-109">All materials in this scene are using the MRTK/Standard shader.</span></span>

![材質資源庫](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

<span data-ttu-id="f2762-111">您可以在底下的 **StandardMaterialComparison** 場景中，找到比較場景，以針對 Unity/標準著色器範例來比較和測試 MRTK/標準著色器 `MRTK/Examples/Demos/StandardShader/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="f2762-111">You can find a comparison scene to compare and test the MRTK/Standard shader against the Unity/Standard shader example in the **StandardMaterialComparison** scene under `MRTK/Examples/Demos/StandardShader/Scenes/`.</span></span>

![材質比較](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a><span data-ttu-id="f2762-113">架構</span><span class="sxs-lookup"><span data-stu-id="f2762-113">Architecture</span></span>

<span data-ttu-id="f2762-114">MRTK/標準陰影系統是「uber 著色器」，其使用 [Unity 的著色器程式變異數功能](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) ，根據材質屬性自動產生最佳的著色器程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2762-114">The MRTK/Standard shading system is an "uber shader" that uses [Unity's shader program variant feature](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) to auto-generate optimal shader code based on material properties.</span></span> <span data-ttu-id="f2762-115">當使用者選取材質偵測器中的材質屬性時，它們只會對已啟用的功能產生效能成本。</span><span class="sxs-lookup"><span data-stu-id="f2762-115">When a user selects material properties in the material inspector, they only incur performance cost for features they have enabled.</span></span>

## <a name="material-inspector"></a><span data-ttu-id="f2762-116">材質檢查</span><span class="sxs-lookup"><span data-stu-id="f2762-116">Material inspector</span></span>

<span data-ttu-id="f2762-117">MRTK/標準著色器的自訂材質偵測器已被呼叫 [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) 。</span><span class="sxs-lookup"><span data-stu-id="f2762-117">A custom material inspector exists for the MRTK/Standard shader called [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI).</span></span> <span data-ttu-id="f2762-118">偵測器會根據使用者選取和設定轉譯狀態的有助於，自動啟用/停用著色器功能。</span><span class="sxs-lookup"><span data-stu-id="f2762-118">The inspector automatically enables/disables shader features, based on user selection and aides in setting up render state.</span></span> <span data-ttu-id="f2762-119">如需每項功能的詳細資訊， **請將滑鼠停留在 Unity 編輯器中的每個屬性上，以取得工具提示。**</span><span class="sxs-lookup"><span data-stu-id="f2762-119">For more information about each feature **please hover over each property in the Unity Editor for a tooltip.**</span></span>

![材質檢查](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

<span data-ttu-id="f2762-121">偵測器的第一個部分會控制材質的呈現狀態。</span><span class="sxs-lookup"><span data-stu-id="f2762-121">The first portion of the inspector controls the material's render state.</span></span> <span data-ttu-id="f2762-122">轉譯 *模式* 會決定呈現材質的時間和方式。</span><span class="sxs-lookup"><span data-stu-id="f2762-122">*Rendering Mode* determines when and how a material will be rendered.</span></span> <span data-ttu-id="f2762-123">MRTK/標準著色器的目的是要鏡像 [Unity/standard 著色器中所找到](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)的轉譯模式。</span><span class="sxs-lookup"><span data-stu-id="f2762-123">The aim of the MRTK/Standard shader is to mirror the [rendering modes found in the Unity/Standard shader](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html).</span></span> <span data-ttu-id="f2762-124">MRTK/Standard 著色器也包含完整使用者控制項的 *加法* 轉譯模式和 *自訂* 呈現模式。</span><span class="sxs-lookup"><span data-stu-id="f2762-124">The MRTK/Standard shader also includes an *Additive* rendering mode and *Custom* rendering mode for complete user control.</span></span>

| <span data-ttu-id="f2762-125">轉譯模式</span><span class="sxs-lookup"><span data-stu-id="f2762-125">Rendering Mode</span></span> |         <span data-ttu-id="f2762-126">Description</span><span class="sxs-lookup"><span data-stu-id="f2762-126">Description</span></span>                                                                                                                                                                                                                                                                                                                                                           |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f2762-127">Opaque</span><span class="sxs-lookup"><span data-stu-id="f2762-127">Opaque</span></span>         | <span data-ttu-id="f2762-128"> (預設) 適用于沒有透明區域的一般純色物件。</span><span class="sxs-lookup"><span data-stu-id="f2762-128">(Default) Suitable for normal solid objects with no transparent areas.</span></span>                                                                                                                                                                                                                                                                                             |
| <span data-ttu-id="f2762-129">剪影</span><span class="sxs-lookup"><span data-stu-id="f2762-129">Cutout</span></span>         | <span data-ttu-id="f2762-130">允許建立透明效果，其在不透明和透明區域之間具有固定邊緣。</span><span class="sxs-lookup"><span data-stu-id="f2762-130">Allows creation of transparent effects that have hard edges between the opaque and transparent areas.</span></span> <span data-ttu-id="f2762-131">在此模式中，沒有半透明的區域，材質可能是100% 不透明或不可見。</span><span class="sxs-lookup"><span data-stu-id="f2762-131">In this mode, there are no semi-transparent areas, the texture is either 100% opaque, or invisible.</span></span> <span data-ttu-id="f2762-132">使用透明度建立材質（例如植被指數）的形狀時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="f2762-132">This is useful when using transparency to create the shape of materials, such as vegetation.</span></span>                                                              |
| <span data-ttu-id="f2762-133">淡化</span><span class="sxs-lookup"><span data-stu-id="f2762-133">Fade</span></span>           | <span data-ttu-id="f2762-134">允許透明度值完全淡化物件，包括任何高光或可能具有的反射。</span><span class="sxs-lookup"><span data-stu-id="f2762-134">Allows the transparency values to entirely fade an object out, including any specular highlights or reflections it may have.</span></span> <span data-ttu-id="f2762-135">如果您想要建立物件的動畫，讓物件淡入或淡出，這個模式就很有用。它不適合用來呈現逼真的透明材質，例如清晰的塑膠或玻璃，因為反射和醒目顯示也會淡出。</span><span class="sxs-lookup"><span data-stu-id="f2762-135">This mode is useful if you want to animate an object fading in or out. It is not suitable for rendering realistic transparent materials such as clear plastic or glass because the reflections and highlights will also be faded out.</span></span> |
| <span data-ttu-id="f2762-136">透明</span><span class="sxs-lookup"><span data-stu-id="f2762-136">Transparent</span></span>    | <span data-ttu-id="f2762-137">適用于呈現逼真的透明材質，例如清晰的塑膠或玻璃。</span><span class="sxs-lookup"><span data-stu-id="f2762-137">Suitable for rendering realistic transparent materials such as clear plastic or glass.</span></span> <span data-ttu-id="f2762-138">在此模式中，材質本身會根據材質的 Alpha 色板和色調色彩) 的 Alpha，來取得透明度值 (。</span><span class="sxs-lookup"><span data-stu-id="f2762-138">In this mode, the material itself will take on transparency values (based on the texture’s alpha channel and the alpha of the tint colour).</span></span> <span data-ttu-id="f2762-139">不過，反射和光源醒目顯示會以完全清楚的方式保持可見，就像是實際的透明材質一樣。</span><span class="sxs-lookup"><span data-stu-id="f2762-139">However, reflections and lighting highlights will remain visible at full clarity as is the case with real transparent materials.</span></span> |
| <span data-ttu-id="f2762-140">加法</span><span class="sxs-lookup"><span data-stu-id="f2762-140">Additive</span></span>       | <span data-ttu-id="f2762-141">啟用加法混合模式，以目前的圖元色彩加總先前的圖元色彩。</span><span class="sxs-lookup"><span data-stu-id="f2762-141">Enables an additive blending mode, which sums the previous pixel color with the current pixel color.</span></span> <span data-ttu-id="f2762-142">這是慣用的透明度模式，可避免出現透明度排序問題。</span><span class="sxs-lookup"><span data-stu-id="f2762-142">This is the preferred transparency mode to avoid transparency sorting issues.</span></span>                                                                                                                                                                                  |
| <span data-ttu-id="f2762-143">自訂</span><span class="sxs-lookup"><span data-stu-id="f2762-143">Custom</span></span>         | <span data-ttu-id="f2762-144">允許以手動方式控制轉譯模式的每個層面。</span><span class="sxs-lookup"><span data-stu-id="f2762-144">Allows for every aspect of the rendering mode to be controlled manually.</span></span> <span data-ttu-id="f2762-145">僅適用于先進的使用量。</span><span class="sxs-lookup"><span data-stu-id="f2762-145">For advanced usage only.</span></span>                                                                                                                                                                                                                                                                  |                                                                                                                                            |

![轉譯模式](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| <span data-ttu-id="f2762-147">挑選模式</span><span class="sxs-lookup"><span data-stu-id="f2762-147">Cull Mode</span></span> |             <span data-ttu-id="f2762-148">Description</span><span class="sxs-lookup"><span data-stu-id="f2762-148">Description</span></span>                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f2762-149">關閉</span><span class="sxs-lookup"><span data-stu-id="f2762-149">Off</span></span>       | <span data-ttu-id="f2762-150">停用臉部剔除。</span><span class="sxs-lookup"><span data-stu-id="f2762-150">Disables face culling.</span></span> <span data-ttu-id="f2762-151">只有在需要雙側邊網格時，才應該將剔除設定為 Off。</span><span class="sxs-lookup"><span data-stu-id="f2762-151">Culling should only be set to Off when a two sided mesh is required.</span></span>                                                                                        |
| <span data-ttu-id="f2762-152">Front</span><span class="sxs-lookup"><span data-stu-id="f2762-152">Front</span></span>     | <span data-ttu-id="f2762-153">啟用 front 臉部剔除。</span><span class="sxs-lookup"><span data-stu-id="f2762-153">Enables front face culling.</span></span>                                                                                                                                                        |
| <span data-ttu-id="f2762-154">上一步</span><span class="sxs-lookup"><span data-stu-id="f2762-154">Back</span></span>      | <span data-ttu-id="f2762-155"> (預設值) 可讓您 [回頭挑選臉部](https://en.wikipedia.org/wiki/Back-face_culling)。</span><span class="sxs-lookup"><span data-stu-id="f2762-155">(Default) Enables [back face culling](https://en.wikipedia.org/wiki/Back-face_culling).</span></span> <span data-ttu-id="f2762-156">應該盡可能地啟用背景臉部剔除，以改善轉譯效能。</span><span class="sxs-lookup"><span data-stu-id="f2762-156">Back face culling should be enabled as often as possible to improve rendering performance.</span></span> |

## <a name="performance"></a><span data-ttu-id="f2762-157">效能</span><span class="sxs-lookup"><span data-stu-id="f2762-157">Performance</span></span>

<span data-ttu-id="f2762-158">透過 Unity 標準著色器使用 MRTK 標準著色器的主要優點之一，就是效能。</span><span class="sxs-lookup"><span data-stu-id="f2762-158">One of the primary advantages to using the MRTK Standard shader over the Unity standard shader is performance.</span></span> <span data-ttu-id="f2762-159">MRTK 標準著色器是可擴充的，只能使用啟用的功能。</span><span class="sxs-lookup"><span data-stu-id="f2762-159">The MRTK Standard Shader is extensible to only utilize the features enabled.</span></span> <span data-ttu-id="f2762-160">不過，MRTK 標準著色器也已撰寫成以 Unity 標準著色器的形式提供可比較的美觀結果，但成本更低。</span><span class="sxs-lookup"><span data-stu-id="f2762-160">However, the MRTK Standard shader has also been written to deliver comparable aesthetic results as the Unity Standard shader, but at a much lower cost.</span></span> <span data-ttu-id="f2762-161">比較著色器效能的一個簡單方式，就是透過在 GPU 上需要執行的作業數目。</span><span class="sxs-lookup"><span data-stu-id="f2762-161">One simple way to compare shader performance is via the number of operations that needs to be performed on the GPU.</span></span> <span data-ttu-id="f2762-162">當然，計算的大小可能會因為啟用的功能和其他轉譯設定而變動。</span><span class="sxs-lookup"><span data-stu-id="f2762-162">Of course, the magnitude of calculations may fluctuate by features enabled and other rendering configurations.</span></span> <span data-ttu-id="f2762-163">但一般而言，MRTK 標準著色器所執行的計算明顯比 Unity 標準著色器更少。</span><span class="sxs-lookup"><span data-stu-id="f2762-163">But, in general, the MRTK Standard shader performs significantly less computation than the Unity Standard shader.</span></span>

<span data-ttu-id="f2762-164">Unity 標準著色器統計資料範例</span><span class="sxs-lookup"><span data-stu-id="f2762-164">Unity Standard shader statistics example</span></span>

![Unity 標準著色器統計資料](../images/performance/UnityStandardShader-Stats.PNG)

<span data-ttu-id="f2762-166">MRTK 標準著色器統計資料範例</span><span class="sxs-lookup"><span data-stu-id="f2762-166">MRTK Standard shader statistics example</span></span>

![MRTK 標準著色器統計資料](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> <span data-ttu-id="f2762-168">您可以在 Unity 檢查程式中選取和查看 [著色器資產](https://docs.unity3d.com/Manual/class-Shader.html) ，然後按一下 [ *編譯和顯示程式碼* ] 按鈕，以產生這些結果。</span><span class="sxs-lookup"><span data-stu-id="f2762-168">These results can be generated by selecting and viewing a [shader asset](https://docs.unity3d.com/Manual/class-Shader.html) in the Unity inspector, then clicking the *Compile and show code* button.</span></span>

## <a name="lighting"></a><span data-ttu-id="f2762-169">光源</span><span class="sxs-lookup"><span data-stu-id="f2762-169">Lighting</span></span>

<span data-ttu-id="f2762-170">MRTK/Standard 會針對光源使用簡單的近似值。</span><span class="sxs-lookup"><span data-stu-id="f2762-170">The MRTK/Standard uses a simple approximation for lighting.</span></span> <span data-ttu-id="f2762-171">因為此著色器不會計算實體正確性和節能，所以會快速且有效率地呈現。</span><span class="sxs-lookup"><span data-stu-id="f2762-171">Because this shader does not calculate for physical correctness and energy conservation, it renders quickly and efficiently.</span></span> <span data-ttu-id="f2762-172">Blinn-Phong 是主要光源技術，其混合使用 Fresnel 和以影像為基礎的光源來近似以實體為基礎的光源。</span><span class="sxs-lookup"><span data-stu-id="f2762-172">Blinn-Phong is the primary lighting technique which is blended with Fresnel and image-based lighting to approximate physically-based lighting.</span></span> <span data-ttu-id="f2762-173">著色器支援下列光源技術：</span><span class="sxs-lookup"><span data-stu-id="f2762-173">The shader supports the following lighting techniques:</span></span>

### <a name="directional-light"></a><span data-ttu-id="f2762-174">定向光線</span><span class="sxs-lookup"><span data-stu-id="f2762-174">Directional light</span></span>

<span data-ttu-id="f2762-175">著色器會遵循場景中第一個 Unity 方向光線的方向、色彩和強度 (如果已啟用) 。</span><span class="sxs-lookup"><span data-stu-id="f2762-175">The shader will respect the direction, color, and intensity of the first Unity Directional Light in the scene (if enabled).</span></span> <span data-ttu-id="f2762-176">動態點燈、點燈或任何其他 Unity 燈光都不會被視為即時光源。</span><span class="sxs-lookup"><span data-stu-id="f2762-176">Dynamic point lights, spot lights, or any other Unity light will not be considered in real time lighting.</span></span>

### <a name="spherical-harmonics"></a><span data-ttu-id="f2762-177">球形諧波</span><span class="sxs-lookup"><span data-stu-id="f2762-177">Spherical harmonics</span></span>

<span data-ttu-id="f2762-178">著色器會使用淺探查，在場景中使用 [球面諧波](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html)來接近燈光（若已啟用）。</span><span class="sxs-lookup"><span data-stu-id="f2762-178">The shader will use Light Probes to approximate lights in the scene using [Spherical Harmonics](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html), if enabled.</span></span> <span data-ttu-id="f2762-179">會針對每個頂點執行球形諧波計算，以降低計算成本。</span><span class="sxs-lookup"><span data-stu-id="f2762-179">Spherical harmonics calculations are performed per vertex to reduce calculation cost.</span></span>

### <a name="lightmapping"></a><span data-ttu-id="f2762-180">Lightmapping</span><span class="sxs-lookup"><span data-stu-id="f2762-180">Lightmapping</span></span>

<span data-ttu-id="f2762-181">針對靜態光源，著色器會遵循 Unity 的 [Lightmapping 系統](https://docs.unity3d.com/Manual/Lightmapping.html)所建立的 lightmaps。</span><span class="sxs-lookup"><span data-stu-id="f2762-181">For static lighting, the shader will respect lightmaps built by Unity's [Lightmapping system](https://docs.unity3d.com/Manual/Lightmapping.html).</span></span> <span data-ttu-id="f2762-182">只要將轉譯器標示為靜態 (或 lightmap 靜態) ，即可使用 lightmaps。</span><span class="sxs-lookup"><span data-stu-id="f2762-182">Simply mark the renderer as static (or lightmap static) to use lightmaps.</span></span>

### <a name="hover-light"></a><span data-ttu-id="f2762-183">停留燈</span><span class="sxs-lookup"><span data-stu-id="f2762-183">Hover light</span></span>

* <span data-ttu-id="f2762-184">查看 [停留燈](hover-light.md)</span><span class="sxs-lookup"><span data-stu-id="f2762-184">See [Hover Light](hover-light.md)</span></span>

### <a name="proximity-light"></a><span data-ttu-id="f2762-185">近亮光</span><span class="sxs-lookup"><span data-stu-id="f2762-185">Proximity light</span></span>

* <span data-ttu-id="f2762-186">請參閱 [近亮燈](proximity-light.md)</span><span class="sxs-lookup"><span data-stu-id="f2762-186">See [Proximity Light](proximity-light.md)</span></span>

## <a name="lightweight-scriptable-render-pipeline-support"></a><span data-ttu-id="f2762-187">輕量可編寫腳本的轉譯管線支援</span><span class="sxs-lookup"><span data-stu-id="f2762-187">Lightweight Scriptable Render Pipeline support</span></span>

<span data-ttu-id="f2762-188">MRTK 包含的升級路徑，可讓開發人員利用 Unity 的輕量可編寫腳本轉譯管線 (LWRP) 搭配 MRTK 著色器。</span><span class="sxs-lookup"><span data-stu-id="f2762-188">The MRTK contains an upgrade path to allow developers to utilize Unity's Lightweight Scriptable Render Pipeline (LWRP) with MRTK shaders.</span></span> <span data-ttu-id="f2762-189">在 Unity m153.azuredevops2019.1.1 f1 和輕量 RP 5.7.2 封裝中進行測試。</span><span class="sxs-lookup"><span data-stu-id="f2762-189">Tested in Unity 2019.1.1f1 and Lightweight RP 5.7.2 package.</span></span> <span data-ttu-id="f2762-190">或者，如需開始使用 LWRP 的指示，請參閱 [此頁面](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)。</span><span class="sxs-lookup"><span data-stu-id="f2762-190">or instructions on getting started with the LWRP, see [this page](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html).</span></span>

<span data-ttu-id="f2762-191">若要執行 MRTK 升級，請針對 **輕量轉譯管線選取：混合現實工具組-> 公用程式-> UPGRADE MRTK Standard 著色器**</span><span class="sxs-lookup"><span data-stu-id="f2762-191">To perform the MRTK upgrade, select: **Mixed Reality Toolkit -> Utilities -> Upgrade MRTK Standard Shader for Lightweight Render Pipeline**</span></span>

![lwrp 升級](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

<span data-ttu-id="f2762-193">升級之後，MRTK/Standard 著色器將會改變，而任何洋紅色 (著色器錯誤) 材質應固定。</span><span class="sxs-lookup"><span data-stu-id="f2762-193">After the upgrade occurs, the MRTK/Standard shader will be altered and any magenta (shader error) materials should be fixed.</span></span> <span data-ttu-id="f2762-194">若要確認升級是否成功，請檢查主控台的：已 **升級的資產/MixedRealityToolkit/StandardAssets/著色器/MixedRealityStandard，以搭配輕量轉譯管線使用**。</span><span class="sxs-lookup"><span data-stu-id="f2762-194">To verify the upgrade successfully occurred, check the console for: **Upgraded Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader for use with the Lightweight Render Pipeline.**</span></span>

## <a name="ugui-support"></a><span data-ttu-id="f2762-195">UGUI 支援</span><span class="sxs-lookup"><span data-stu-id="f2762-195">UGUI support</span></span>

<span data-ttu-id="f2762-196">MRTK 標準陰影系統可與 Unity 的內建 [UI 系統](https://docs.unity3d.com/Manual/UISystem.html)搭配使用。</span><span class="sxs-lookup"><span data-stu-id="f2762-196">The MRTK Standard shading system works with Unity's built in [UI system](https://docs.unity3d.com/Manual/UISystem.html).</span></span> <span data-ttu-id="f2762-197">在 Unity UI 元件上，unity_ObjectToWorld 矩陣不是圖形元件所在之本機轉換的轉換矩陣，而是其父畫布的轉換矩陣。</span><span class="sxs-lookup"><span data-stu-id="f2762-197">On Unity UI components, the unity_ObjectToWorld matrix is not the transformation matrix of the local transform the Graphic component lives on but that of its parent Canvas.</span></span> <span data-ttu-id="f2762-198">許多 MRTK/標準著色器效果都需要知道物件規模。</span><span class="sxs-lookup"><span data-stu-id="f2762-198">Many MRTK/Standard shader effects require object scale to be known.</span></span> <span data-ttu-id="f2762-199">若要解決此問題， [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) 會在 UI 網格結構期間，將調整資訊儲存為 UV 通道屬性。</span><span class="sxs-lookup"><span data-stu-id="f2762-199">To solve this issue, the [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) will store scaling information into UV channel attributes during UI mesh construction.</span></span>

<span data-ttu-id="f2762-200">請注意，使用 Unity 映射元件時，建議您為來源影像指定「無 (Sprite) 」，以防止 Unity UI 產生額外的頂點。</span><span class="sxs-lookup"><span data-stu-id="f2762-200">Note, when using a Unity Image component, it is recommended to specify "None (Sprite)" for the Source Image to prevent Unity UI from generating extra vertices.</span></span>

<span data-ttu-id="f2762-201">當需要時，MRTK 中的畫布會提示您新增 a [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) ：</span><span class="sxs-lookup"><span data-stu-id="f2762-201">A Canvas within the MRTK will prompt for the addition of a [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) when one is required:</span></span>

![調整網格效果](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a><span data-ttu-id="f2762-203">材質結合器</span><span class="sxs-lookup"><span data-stu-id="f2762-203">Texture combiner</span></span>

<span data-ttu-id="f2762-204">若要改善每個圖元金屬的 Unity 標準著色器的同位，可透過 [通道封裝](http://wiki.polycount.com/wiki/ChannelPacking)來控制平滑度、放射和遮蔽值。</span><span class="sxs-lookup"><span data-stu-id="f2762-204">To improve parity with the Unity Standard shader per pixel metallic, smoothness, emissive, and occlusion values can all be controlled via [channel packing](http://wiki.polycount.com/wiki/ChannelPacking).</span></span> <span data-ttu-id="f2762-205">例如：</span><span class="sxs-lookup"><span data-stu-id="f2762-205">For example:</span></span>

![通道對應範例](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

<span data-ttu-id="f2762-207">當您使用通道封裝時，您只需要將一個材質取樣並載入到記憶體中，而不是四個不同的材質。</span><span class="sxs-lookup"><span data-stu-id="f2762-207">When you use channel packing, you only have to sample and load one texture into memory instead of four separate ones.</span></span> <span data-ttu-id="f2762-208">當您在諸如材質或 Photoshop 的程式中撰寫材質地圖時，您可以將它們封裝如下：</span><span class="sxs-lookup"><span data-stu-id="f2762-208">When you write your texture maps in a program like Substance or Photoshop, you can hand pack them like the following:</span></span>

| <span data-ttu-id="f2762-209">管道</span><span class="sxs-lookup"><span data-stu-id="f2762-209">Channel</span></span> | <span data-ttu-id="f2762-210">屬性</span><span class="sxs-lookup"><span data-stu-id="f2762-210">Property</span></span>             |
|---------|----------------------|
| <span data-ttu-id="f2762-211">紅色</span><span class="sxs-lookup"><span data-stu-id="f2762-211">Red</span></span>     | <span data-ttu-id="f2762-212">金屬</span><span class="sxs-lookup"><span data-stu-id="f2762-212">Metallic</span></span>             |
| <span data-ttu-id="f2762-213">綠色</span><span class="sxs-lookup"><span data-stu-id="f2762-213">Green</span></span>   | <span data-ttu-id="f2762-214">遮蔽</span><span class="sxs-lookup"><span data-stu-id="f2762-214">Occlusion</span></span>            |
| <span data-ttu-id="f2762-215">藍色</span><span class="sxs-lookup"><span data-stu-id="f2762-215">Blue</span></span>    | <span data-ttu-id="f2762-216">發出 (灰階) </span><span class="sxs-lookup"><span data-stu-id="f2762-216">Emission (Greyscale)</span></span> |
| <span data-ttu-id="f2762-217">Alpha</span><span class="sxs-lookup"><span data-stu-id="f2762-217">Alpha</span></span>   | <span data-ttu-id="f2762-218">平滑</span><span class="sxs-lookup"><span data-stu-id="f2762-218">Smoothness</span></span>           |

<span data-ttu-id="f2762-219">或者，您可以使用 MRTK 材質結合器工具。</span><span class="sxs-lookup"><span data-stu-id="f2762-219">Or, you can use the MRTK Texture Combiner Tool.</span></span> <span data-ttu-id="f2762-220">若要開啟工具，請選取： **混合現實工具組-> 公用程式-> 材質結合器** ，這會開啟下列視窗：</span><span class="sxs-lookup"><span data-stu-id="f2762-220">To open the tool, select: **Mixed Reality Toolkit -> Utilities -> Texture Combiner** which will open the below window:</span></span>

![紋理結合器範例](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

<span data-ttu-id="f2762-222">您可以選取 Unity 標準著色器，然後按一下 [從標準材質自動填入]，自動填寫此視窗。</span><span class="sxs-lookup"><span data-stu-id="f2762-222">This window can be automatically filled out by selecting a Unity Standard shader and clicking "Autopopulate from Standard Material."</span></span> <span data-ttu-id="f2762-223">或者，您可以手動指定每個紅色、綠色、藍色或 Alpha 色板的材質 (或常數值) 。</span><span class="sxs-lookup"><span data-stu-id="f2762-223">Or, you can manually specify a texture (or constant value) per red, green, blue, or alpha channel.</span></span> <span data-ttu-id="f2762-224">材質組合是 GPU 加速的，不需要輸入材質就可以存取 CPU。</span><span class="sxs-lookup"><span data-stu-id="f2762-224">The texture combination is GPU accelerated and does not require the input texture to be CPU accessible.</span></span>

## <a name="additional-feature-documentation"></a><span data-ttu-id="f2762-225">其他功能檔</span><span class="sxs-lookup"><span data-stu-id="f2762-225">Additional feature documentation</span></span>

<span data-ttu-id="f2762-226">以下是 MRTK/Standard 著色器提供的幾項功能詳細資料的額外詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f2762-226">Below are extra details on a handful of feature details available with the MRTK/Standard shader.</span></span>

### <a name="primitive-clipping"></a><span data-ttu-id="f2762-227">基本剪輯</span><span class="sxs-lookup"><span data-stu-id="f2762-227">Primitive clipping</span></span>

![基本剪輯](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* <span data-ttu-id="f2762-229">請參閱 [裁剪基本](clipping-primitive.md)</span><span class="sxs-lookup"><span data-stu-id="f2762-229">See [Clipping Primitive](clipping-primitive.md)</span></span>

### <a name="mesh-outlines"></a><span data-ttu-id="f2762-230">網狀大綱</span><span class="sxs-lookup"><span data-stu-id="f2762-230">Mesh outlines</span></span>

<span data-ttu-id="f2762-231">許多網狀大綱技巧都是使用 [後置處理](https://docs.unity3d.com/Manual/PostProcessingOverview.html) 技術來完成。</span><span class="sxs-lookup"><span data-stu-id="f2762-231">Many mesh outline techniques are done using a [post processing](https://docs.unity3d.com/Manual/PostProcessingOverview.html) technique.</span></span> <span data-ttu-id="f2762-232">後續處理可提供絕佳的品質大綱，但在許多混合現實裝置上可能會耗費大量資源。</span><span class="sxs-lookup"><span data-stu-id="f2762-232">Post processing provides great quality outlines, but can be prohibitively expensive on many Mixed Reality devices.</span></span> <span data-ttu-id="f2762-233">您可以在底下的  **OutlineExamples** 場景中找到示範網格輪廓使用方式的場景 `MRTK/Examples/Demos/StandardShader/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="f2762-233">You can find a scene that demonstrates usage of mesh outlines in the  **OutlineExamples** scene under `MRTK/Examples/Demos/StandardShader/Scenes/`.</span></span>

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

<span data-ttu-id="f2762-234">[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) 和 [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) 可以用來呈現網格轉譯器周圍的輪廓。</span><span class="sxs-lookup"><span data-stu-id="f2762-234">[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) and [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) can be used to render an outline around a mesh renderer.</span></span> <span data-ttu-id="f2762-235">啟用此元件會為所述的物件引進額外的轉譯行程，但其設計目的是在行動混合現實裝置上執行 gen2，而不會使用任何後置流程。</span><span class="sxs-lookup"><span data-stu-id="f2762-235">Enabling this component introduces an additional render pass of the object being outlined, but is designed to run performantly on mobile Mixed Reality devices and does not utilize any post processes.</span></span> <span data-ttu-id="f2762-236">這項效果的限制包括無法在不防水 (或必須是雙側) 的物件上運作，而且可能會在重迭的物件上發生深度排序問題。</span><span class="sxs-lookup"><span data-stu-id="f2762-236">Limitations of this effect include it not working well on objects which are not watertight (or required to be two sided) and depth sorting issues can occur on overlapping objects.</span></span>

<span data-ttu-id="f2762-237">大綱行為是設計用來搭配 MRTK/標準著色器。</span><span class="sxs-lookup"><span data-stu-id="f2762-237">The outline behaviors are designed to be used in conjunction with the MRTK/Standard shader.</span></span> <span data-ttu-id="f2762-238">外框材質通常是穩固的 unlit 色彩，但可以設定來達成各式各樣的效果。</span><span class="sxs-lookup"><span data-stu-id="f2762-238">Outline materials are usually a solid unlit color, but can be configured to achieve a wide array of effects.</span></span> <span data-ttu-id="f2762-239">外框材質的預設設定如下：</span><span class="sxs-lookup"><span data-stu-id="f2762-239">The default configuration of a outline material is as follows:</span></span>

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. <span data-ttu-id="f2762-240">深度寫入-應針對外框材質停用，以確保外框不會防止其他物件轉譯。</span><span class="sxs-lookup"><span data-stu-id="f2762-240">Depth Write - should be disabled for outline materials to make sure the outline does not prevent other objects from rendering.</span></span>
2. <span data-ttu-id="f2762-241">頂點延伸-必須啟用才能轉譯大綱。</span><span class="sxs-lookup"><span data-stu-id="f2762-241">Vertex Extrusion - needs to be enabled to render the outline.</span></span>
3. <span data-ttu-id="f2762-242">使用平滑法線-針對某些網格，此設定是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="f2762-242">Use Smooth Normals - this setting is optional for some meshes.</span></span> <span data-ttu-id="f2762-243">藉由將頂點沿著頂點垂直移動來進行，而在某些網格上沿著預設法線的方向，則會導致大綱中的不連續。</span><span class="sxs-lookup"><span data-stu-id="f2762-243">Extrusion occurs by moving a vertex along a vertex normal, on some meshes extruding along the default normals will cause discontinuities in the outline.</span></span> <span data-ttu-id="f2762-244">若要修正這些不連續，您可以核取此方塊，以使用另一組會產生的平滑法線 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)</span><span class="sxs-lookup"><span data-stu-id="f2762-244">To fix these discontinuities, you can check this box to use another set of smoothed normals which get generated by [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)</span></span>

<span data-ttu-id="f2762-245">[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 是可用來在網格上自動產生平滑法線的元件。</span><span class="sxs-lookup"><span data-stu-id="f2762-245">[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) is a component which can be used to automatically generate smoothed normals on a mesh.</span></span> <span data-ttu-id="f2762-246">這個方法會將網格中的頂點分組，並在空間中共用相同的位置，然後將這些頂點的法線平均。</span><span class="sxs-lookup"><span data-stu-id="f2762-246">This method groups vertices in a mesh that share the same location in space then averages the normals of those vertices.</span></span> <span data-ttu-id="f2762-247">此程式會建立基礎網格的複本，而且只在必要時才使用。</span><span class="sxs-lookup"><span data-stu-id="f2762-247">This process creates a copy of the underlying mesh and should be used only when required.</span></span>

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. <span data-ttu-id="f2762-248">經由產生的平滑法線 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 。</span><span class="sxs-lookup"><span data-stu-id="f2762-248">Smooth normals generated via [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother).</span></span>
2. <span data-ttu-id="f2762-249">預設使用的法線，請注意立方體周圍的構件。</span><span class="sxs-lookup"><span data-stu-id="f2762-249">Default normals used, notice the artifacts around the cube corners.</span></span>

### <a name="stencil-testing"></a><span data-ttu-id="f2762-250">樣板測試</span><span class="sxs-lookup"><span data-stu-id="f2762-250">Stencil testing</span></span>

<span data-ttu-id="f2762-251">內建的可設定範本測試支援，可達成各式各樣的效果。</span><span class="sxs-lookup"><span data-stu-id="f2762-251">Built in configurable stencil test support to achieve a wide array of effects.</span></span> <span data-ttu-id="f2762-252">例如入口網站：</span><span class="sxs-lookup"><span data-stu-id="f2762-252">Such as portals:</span></span>

![樣板測試](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a><span data-ttu-id="f2762-254">實例色彩支援</span><span class="sxs-lookup"><span data-stu-id="f2762-254">Instanced color support</span></span>

<span data-ttu-id="f2762-255">實例色彩支援，以提供數千個 GPU 實例網格獨特的材質屬性：</span><span class="sxs-lookup"><span data-stu-id="f2762-255">Instanced color support to give thousands of GPU instanced meshes unique material properties:</span></span>

![實例屬性](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a><span data-ttu-id="f2762-257">Triplanar 對應</span><span class="sxs-lookup"><span data-stu-id="f2762-257">Triplanar mapping</span></span>

<span data-ttu-id="f2762-258">Triplanar 對應是以程式設計方式為網格材質紋理的技巧。</span><span class="sxs-lookup"><span data-stu-id="f2762-258">Triplanar mapping is a technique to programmatically texture a mesh.</span></span> <span data-ttu-id="f2762-259">常用於地形、未 UVs 的網格，或難以解除包裝圖形。</span><span class="sxs-lookup"><span data-stu-id="f2762-259">Often used in terrain, meshes without UVs, or difficult to unwrap shapes.</span></span> <span data-ttu-id="f2762-260">這項實行支援世界或區域的空間投射、混合平滑的規格，以及正常的地圖支援。</span><span class="sxs-lookup"><span data-stu-id="f2762-260">This implementation supports world or local space projection, the specification of blending smoothness, and normal map support.</span></span> <span data-ttu-id="f2762-261">請注意，使用的每個材質都需要3個紋理範例，因此請在效能嚴重不足的情況下謹慎使用。</span><span class="sxs-lookup"><span data-stu-id="f2762-261">Note, each texture used requires 3 texture samples, so use sparingly in performance critical situations.</span></span>

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a><span data-ttu-id="f2762-263">頂點延伸</span><span class="sxs-lookup"><span data-stu-id="f2762-263">Vertex extrusion</span></span>

<span data-ttu-id="f2762-264">世界空間中的頂點延伸。</span><span class="sxs-lookup"><span data-stu-id="f2762-264">Vertex extrusion in world space.</span></span> <span data-ttu-id="f2762-265">適用于視覺化拉伸的周框磁片區或轉換 in/out 網格。</span><span class="sxs-lookup"><span data-stu-id="f2762-265">Useful for visualizing extruded bounding volumes or transitions in/out meshes.</span></span>

![一般地圖示尺1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a><span data-ttu-id="f2762-267">其他</span><span class="sxs-lookup"><span data-stu-id="f2762-267">Miscellaneous</span></span>

<span data-ttu-id="f2762-268">控制 >albedo 優化的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f2762-268">A checkbox to control albedo optimizations.</span></span> <span data-ttu-id="f2762-269">當未指定任何 >albedo 材質時，會停用優化 >albedo 作業。</span><span class="sxs-lookup"><span data-stu-id="f2762-269">As an optimization albedo operations are disabled when no albedo texture is specified.</span></span> <span data-ttu-id="f2762-270">這對控制 [遠端材質載入](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)很有用。</span><span class="sxs-lookup"><span data-stu-id="f2762-270">This is useful for controlling [remote texture loading](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html).</span></span>

<span data-ttu-id="f2762-271">只要勾選此方塊：</span><span class="sxs-lookup"><span data-stu-id="f2762-271">Simply check this box:</span></span>

![>albedo 指派](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

<span data-ttu-id="f2762-273">支援每圖元裁剪材質、區域邊緣型消除鋸齒和一般地圖縮放比例。</span><span class="sxs-lookup"><span data-stu-id="f2762-273">Per pixel clipping textures, local edge based anti aliasing, and normal map scaling are supported.</span></span>

![一般地圖縮放比例2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a><span data-ttu-id="f2762-275">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2762-275">See also</span></span>

* [<span data-ttu-id="f2762-276">互動</span><span class="sxs-lookup"><span data-stu-id="f2762-276">Interactable</span></span>](../ux-building-blocks/interactable.md)
* [<span data-ttu-id="f2762-277">停留燈</span><span class="sxs-lookup"><span data-stu-id="f2762-277">Hover Light</span></span>](hover-light.md)
* [<span data-ttu-id="f2762-278">近亮光</span><span class="sxs-lookup"><span data-stu-id="f2762-278">Proximity Light</span></span>](proximity-light.md)
* [<span data-ttu-id="f2762-279">裁剪基本</span><span class="sxs-lookup"><span data-stu-id="f2762-279">Clipping Primitive</span></span>](clipping-primitive.md)
