---
title: 材質實例
description: MRTK 中的材質實例和其使用方式檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、MaterialInstance、
ms.openlocfilehash: 216fa72af6bb6caaf47e30c156f7caf1b1dab71e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145214"
---
# <a name="material-instance"></a>材質實例

[`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance)行為有助於在追蹤實例材質存留期，並自動終結使用者的實例材料。 這個公用程式元件可以用來取代轉譯器[。材質](https://docs.unity3d.com/ScriptReference/Renderer-material.html)[或轉譯](https://docs.unity3d.com/ScriptReference/Renderer-materials.html)器的材質。

> [!NOTE]
> [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 優先于材質實例，但在所有案例中都不會提供。

為何要使用轉譯器 [。材質](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 有問題？ 如果您將下列程式碼新增至 Unity 場景，而點擊播放記憶體使用量將會繼續進行順向和順向：

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
> 如果執行太久，上述的洩漏行為 **將會損毀** 。

另一種方法是使用 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 下列行為：

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

## <a name="usage"></a>使用方式

當叫用 Unity [的轉譯](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 器時， (s) ，Unity 會自動將新的資料具現化。 當不再需要材質或遊戲物件損毀時，呼叫者必須負責終結材質。 此 [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 行為有助於避免材質流失，並在編輯和執行時間期間讓材質配置路徑保持一致。

當無法使用 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 且必須具現化資料時， [`MaterialInstance`](xref:Microsoft.MixedReality.Toolkit.Rendering.MaterialInstance) 可以使用如下所示的內容：

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

如果有多個物件需要材質實例的擁有權，最好是取得參考追蹤的明確擁有權。  ([`IMaterialInstanceOwner`](xref:Microsoft.MixedReality.Toolkit.Rendering.IMaterialInstanceOwner) 具有擁有權之且有助於的選擇性介面。以下 ) 範例使用方式：

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

如需詳細資訊，請參閱在行為中示範的範例使用 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 方式。

## <a name="see-also"></a>另請參閱

* [MRTK 標準著色器](mrtk-standard-shader.md)
