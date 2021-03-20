---
title: ClippingPrimitive
description: 在 MRTK 中使用範例裁剪基本檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、裁剪基本、
ms.openlocfilehash: b6515990e00f85bac8b7ce48b81806fdf396ddca
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687138"
---
# <a name="clipping-primitive"></a>裁剪基本

這些 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 行為可讓您在搭配 [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) MRTK 著色器使用時，能夠針對 [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) (內部或外部) ，指定要剪下哪一端的基本物件。

![基本裁剪 gizmos](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 利用著色器內的 [剪切/捨棄](https://developer.download.nvidia.com/cg/clip.html) 指令，並停用 Unity 對批次處理裁剪轉譯器的功能。 利用裁剪基本專案時，請記住這些效能含意。

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane)、 [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) 和 [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 可以用來輕鬆地控制裁剪基本屬性。 使用這些元件搭配下列著色器，以利用剪切案例。

- *混合現實工具組/標準*
- *混合現實工具組/TextMeshPro*
- *混合現實工具組/Text3DShader*

## <a name="examples"></a>範例

**ClippingExamples** 和 **MaterialGallery** 場景示範行為的用法 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) ，您可以在下列位置找到： MRTK/範例/示範/StandardShader/場景/

## <a name="advanced-usage"></a>進階使用方式

依預設，一 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 次只能裁剪[](https://docs.unity3d.com/ScriptReference/Renderer.html)轉譯器。 如果您的專案需要一個以上 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 的來影響[](https://docs.unity3d.com/ScriptReference/Renderer.html)轉譯器，則下列範例程式碼示範如何達成此目的。

> [!NOTE]
> 有多個 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 剪輯[](https://docs.unity3d.com/ScriptReference/Renderer.html)轉譯器會增加圖元著色器的指示，而且會影響效能。 請在您的專案內分析這些變更。

*如何呈現兩個不同 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 的剪輯。例如 [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) ，和 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 同時：*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> 上述變更將會產生額外的著色器編譯時間。

*如何呈現兩個相同的 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 剪輯。例如，兩個 [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 相同的時間：*

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

最後，將 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 和 SecondClippingBox 元件新增至場景，並為這兩個方塊指定相同的轉譯器。 這兩個方塊現在應該會同時裁剪轉譯器。

## <a name="see-also"></a>另請參閱

- [MRTK 標準著色器](MRTKStandardShader.md)
