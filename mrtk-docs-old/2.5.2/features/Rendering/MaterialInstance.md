---
title: MaterialInstance
description: MRTK 中的材質實例和其使用方式檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、MaterialInstance、
ms.openlocfilehash: 27f411b13e796c99b0b881bdf46c5825dd985a01
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104691325"
---
# <a name="material-instance"></a><span data-ttu-id="d413b-104">材質實例</span><span class="sxs-lookup"><span data-stu-id="d413b-104">Material instance</span></span>

<span data-ttu-id="d413b-105">[`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)行為有助於在追蹤實例材質存留期，並自動終結使用者的實例材料。</span><span class="sxs-lookup"><span data-stu-id="d413b-105">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior aides in tracking instance material lifetime and automatically destroys instanced materials for the user.</span></span> <span data-ttu-id="d413b-106">這個公用程式元件可以用來取代轉譯器[。材質](https://docs.unity3d.com/ScriptReference/Renderer-material.html)[或轉譯](https://docs.unity3d.com/ScriptReference/Renderer-material.html)器的材質。</span><span class="sxs-lookup"><span data-stu-id="d413b-106">This utility component can be used as a replacement to [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) or [Renderer.materials](https://docs.unity3d.com/ScriptReference/Renderer-material.html).</span></span>

> [!NOTE]
> <span data-ttu-id="d413b-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 優先于材質實例，但在所有案例中都不會提供。</span><span class="sxs-lookup"><span data-stu-id="d413b-107">[MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) are preferred over material instancing but are not always available  in all scenarios.</span></span>

<span data-ttu-id="d413b-108">為何要使用轉譯器 [。材質](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 有問題？</span><span class="sxs-lookup"><span data-stu-id="d413b-108">Why can using [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) be an issue?</span></span> <span data-ttu-id="d413b-109">如果您將下列程式碼新增至 Unity 場景，而點擊播放記憶體使用量將會繼續進行順向和順向：</span><span class="sxs-lookup"><span data-stu-id="d413b-109">If you add the below code to a Unity scene and hit play memory usage will continue to climb and climb:</span></span>

```c#
public class Leak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // Memory leak, the material allocated is not tracked & destroyed.
        cube.GetComponent<Renderer>().material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

> [!NOTE]
> <span data-ttu-id="d413b-110">如果執行太久，上述的洩漏行為 **將會損毀** 。</span><span class="sxs-lookup"><span data-stu-id="d413b-110">The above Leak behavior **will crash Unity** if ran for too long!</span></span>

<span data-ttu-id="d413b-111">另一種方法是使用 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 下列行為：</span><span class="sxs-lookup"><span data-stu-id="d413b-111">As an alternative try using the [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior:</span></span>

```c#
public class NoLeak : MonoBehaviour
{
    private void Update()
    {
        var cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        // No memory leak, the material allocated is tracked & destroyed by MaterialInstance.
        cube.EnsureComponent<MaterialInstance>().Material.color = Color.red;
        ...
        Destroy(cube);
    }
}
```

## <a name="usage"></a><span data-ttu-id="d413b-112">使用方式</span><span class="sxs-lookup"><span data-stu-id="d413b-112">Usage</span></span>

<span data-ttu-id="d413b-113">當叫用 Unity [的轉譯](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 器時， (s) ，Unity 會自動將新的資料具現化。</span><span class="sxs-lookup"><span data-stu-id="d413b-113">When invoking Unity's [Renderer.material](https://docs.unity3d.com/ScriptReference/Renderer-material.html)(s), Unity automatically instantiates new materials.</span></span> <span data-ttu-id="d413b-114">當不再需要材質或遊戲物件損毀時，呼叫者必須負責終結材質。</span><span class="sxs-lookup"><span data-stu-id="d413b-114">It is the caller's responsibility to destroy the materials when a material is no longer needed or the game object is destroyed.</span></span> <span data-ttu-id="d413b-115">此 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行為有助於避免材質流失，並在編輯和執行時間期間讓材質配置路徑保持一致。</span><span class="sxs-lookup"><span data-stu-id="d413b-115">The [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) behavior helps avoid material leaks and keeps material allocation paths consistent during edit and run time.</span></span>

<span data-ttu-id="d413b-116">當無法使用 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 且必須具現化資料時， [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 可以使用如下所示的內容：</span><span class="sxs-lookup"><span data-stu-id="d413b-116">When a [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) can not be used and a material must be instanced, [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) can be used as follows:</span></span>

```c#
public class MyBehaviour : MonoBehaviour
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().Material;
        material.color = Color.red;
        ...
    }
}
```

<span data-ttu-id="d413b-117">如果有多個物件需要材質實例的擁有權，最好是取得參考追蹤的明確擁有權。</span><span class="sxs-lookup"><span data-stu-id="d413b-117">If multiple objects need ownership of the material instance it's best to take explicit ownership for reference tracking.</span></span> <span data-ttu-id="d413b-118"> ([`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) 具有擁有權之且有助於的選擇性介面。以下 ) 範例使用方式：</span><span class="sxs-lookup"><span data-stu-id="d413b-118">(An optional interface called [`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) exists to aide with ownership.) Below is example usage:</span></span>

```c#
public class MyBehaviour : MonoBehaviour,  IMaterialInstanceOwner
{
    // Assigned via the inspector.
    public Renderer targetRenderer;

    private void OnEnable()
    {
        Material material = targetRenderer.EnsureComponent<MaterialInstance>().AcquireMaterial(this);
        material.color = Color.red;
        ...
    }

    private void OnDisable()
    {
        targetRenderer.GetComponent<MaterialInstance>()?.ReleaseMaterial(this)
    }

    public void OnMaterialChanged(MaterialInstance materialInstance)
    {
        // Optional method for when materials change outside of the MaterialInstance.
        ...
    }
}
```

<span data-ttu-id="d413b-119">如需詳細資訊，請參閱在行為中示範的範例使用 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 方式。</span><span class="sxs-lookup"><span data-stu-id="d413b-119">For more information please see the example usage demonstrated within the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behavior.</span></span>

## <a name="see-also"></a><span data-ttu-id="d413b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d413b-120">See also</span></span>

* [<span data-ttu-id="d413b-121">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="d413b-121">MRTK Standard Shader</span></span>](MRTKStandardShader.md)
