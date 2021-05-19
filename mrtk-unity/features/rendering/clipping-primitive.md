---
title: 裁剪基本
description: 在 MRTK 中使用範例裁剪基本檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、裁剪基本、
ms.openlocfilehash: 35b7166045986df34eaf2c23161efc6379160ead
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145202"
---
# <a name="clipping-primitive"></a><span data-ttu-id="e6a55-104">裁剪基本</span><span class="sxs-lookup"><span data-stu-id="e6a55-104">Clipping Primitive</span></span>

<span data-ttu-id="e6a55-105">這些 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 行為可讓您在搭配 [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) MRTK 著色器使用時，能夠針對 [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) (內部或外部) ，指定要剪下哪一端的基本物件。</span><span class="sxs-lookup"><span data-stu-id="e6a55-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![基本裁剪 gizmos](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="e6a55-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 利用著色器內的 [剪切/捨棄](https://developer.download.nvidia.com/cg/clip.html) 指令，並停用 Unity 對批次處理裁剪轉譯器的功能。</span><span class="sxs-lookup"><span data-stu-id="e6a55-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="e6a55-108">利用裁剪基本專案時，請記住這些效能含意。</span><span class="sxs-lookup"><span data-stu-id="e6a55-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="e6a55-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane)、 [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) 和 [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 可以用來輕鬆地控制裁剪基本屬性。</span><span class="sxs-lookup"><span data-stu-id="e6a55-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="e6a55-110">使用這些元件搭配下列著色器，以利用剪切案例。</span><span class="sxs-lookup"><span data-stu-id="e6a55-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="e6a55-111">*混合現實工具組/標準*</span><span class="sxs-lookup"><span data-stu-id="e6a55-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="e6a55-112">*混合現實工具組/TextMeshPro*</span><span class="sxs-lookup"><span data-stu-id="e6a55-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="e6a55-113">*混合現實工具組/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="e6a55-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="e6a55-114">範例</span><span class="sxs-lookup"><span data-stu-id="e6a55-114">Examples</span></span>

<span data-ttu-id="e6a55-115">**ClippingExamples** 和 **MaterialGallery** 場景示範行為的用法 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) ，您可以在下列位置找到： MRTK/範例/示範/StandardShader/場景/</span><span class="sxs-lookup"><span data-stu-id="e6a55-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="e6a55-116">進階使用方式</span><span class="sxs-lookup"><span data-stu-id="e6a55-116">Advanced Usage</span></span>

<span data-ttu-id="e6a55-117">依預設，一 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 次只能裁剪[](https://docs.unity3d.com/ScriptReference/Renderer.html)轉譯器。</span><span class="sxs-lookup"><span data-stu-id="e6a55-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="e6a55-118">如果您的專案需要一個以上 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 的來影響[](https://docs.unity3d.com/ScriptReference/Renderer.html)轉譯器，則下列範例程式碼示範如何達成此目的。</span><span class="sxs-lookup"><span data-stu-id="e6a55-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="e6a55-119">有多個 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 剪輯[](https://docs.unity3d.com/ScriptReference/Renderer.html)轉譯器會增加圖元著色器的指示，而且會影響效能。</span><span class="sxs-lookup"><span data-stu-id="e6a55-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="e6a55-120">請在您的專案內分析這些變更。</span><span class="sxs-lookup"><span data-stu-id="e6a55-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="e6a55-121">*如何呈現兩個不同 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 的剪輯。例如 [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) ，和 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 同時：*</span><span class="sxs-lookup"><span data-stu-id="e6a55-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="e6a55-122">上述變更將會產生額外的著色器編譯時間。</span><span class="sxs-lookup"><span data-stu-id="e6a55-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="e6a55-123">*如何呈現兩個相同的 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 剪輯。例如，兩個 [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 相同的時間：*</span><span class="sxs-lookup"><span data-stu-id="e6a55-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// 1) Add the below MonoBehaviour to your project:

[ExecuteInEditMode]
public class SecondClippingBox : ClippingBox
{
    /// <inheritdoc />
    protected override string Keyword
    {
        get { return "_CLIPPING_BOX2"; }
    }

    /// <inheritdoc />
    protected override string ClippingSideProperty
    {
        get { return "_ClipBoxSide2"; }
    }

    /// <inheritdoc />
    protected override void Initialize()
    {
        base.Initialize();

        clipBoxSizeID = Shader.PropertyToID("_ClipBoxSize2");
        clipBoxInverseTransformID = Shader.PropertyToID("_ClipBoxInverseTransform2");
    }
}

// 2) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) add the following multi_compile pragma:

#pragma multi_compile _ _CLIPPING_BOX2

// 3) In the same shader change:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX)

// to:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX) || defined(_CLIPPING_BOX2)

// 4) In the same shader add the following shader variables:

#if defined(_CLIPPING_BOX2)
    fixed _ClipBoxSide2;
    float4 _ClipBoxSize2;
    float4x4 _ClipBoxInverseTransform2;
#endif

// 5) In the same shader change:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif

// to:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif
#if defined(_CLIPPING_BOX2)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize2.xyz, _ClipBoxInverseTransform2) * _ClipBoxSide2);
#endif
```

<span data-ttu-id="e6a55-124">最後，將 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 和 SecondClippingBox 元件新增至場景，並為這兩個方塊指定相同的轉譯器。</span><span class="sxs-lookup"><span data-stu-id="e6a55-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="e6a55-125">這兩個方塊現在應該會同時裁剪轉譯器。</span><span class="sxs-lookup"><span data-stu-id="e6a55-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6a55-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6a55-126">See also</span></span>

- [<span data-ttu-id="e6a55-127">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="e6a55-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
