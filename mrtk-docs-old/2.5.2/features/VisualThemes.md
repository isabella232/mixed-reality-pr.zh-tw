---
title: VisualThemes
description: 總覽視覺主題彈性地控制 MRTK 中的 UX 資產
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、MRTK 主題、
ms.openlocfilehash: 04a1b69b32846e235f8095c9018b7919971ab907
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682311"
---
# <a name="visual-themes"></a>視覺主題

主題可讓您彈性地控制 UX 資產，以回應各種狀態轉換。 這可能牽涉到變更按鈕的色彩、調整元素的大小以回應焦點等等。視覺化主題架構是由兩個主要部分所組成： 1) 設定和 2) 執行時間引擎。

[主題](#theme-configuration) 設定是屬性和類型的定義，而 [主題引擎](#theme-engines) 是使用設定的類別，並在執行時間執行邏輯以更新轉換、材質和其他。

## <a name="theme-configuration"></a>主題設定

主題設定是 [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) ，可定義如何在執行時間初始化主題引擎。 當應用程式正在執行時，它們會定義要使用哪些屬性和值來回應輸入或其他狀態變更。 作為 [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 資產，主題設定可以定義一次，然後在不同的 UX 元件之間重複使用。

若要建立新的 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 資產：

1) 以滑鼠右鍵按一下 [ *專案] 視窗*
1) 選取 [**建立**  >  **混合現實工具** 組]  >  **主題**

您可以在下方找到範例主題設定資產 `MRTK/SDK/Features/UX/Interactable/Themes` 。

![Inspector 中的主題 ScriptableObject 範例](images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>狀態

建立新的時 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ，要設定的第一件事就是可用的狀態。 [ *狀態* ] 屬性會指出主題設定需要定義多少個值，因為每個狀態都有一個值。 在上述的範例影像中， [針對互動元件定義的預設狀態](ux-building-blocks/Interactable.md#general-input-settings) 為 *預設*、 *焦點*、已 *按* 下和 *停用*。 這些是在 `DefaultInteractableStates` (資產/MRTK/SDK/Features/UX/互動/州) 資產檔案中定義。

若要建立新的 [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) 資產：

1) 以滑鼠右鍵按一下 [ *專案] 視窗*
1) 選取 [**建立**  >  **混合的實際工具** 組  >  **狀態**]

![偵測器中的狀態 ScriptableObject 範例](images/interactable/DefaultInteractableStates.png)

[`State`](xref:Microsoft.MixedReality.Toolkit.UI.States)ScriptableObject 會定義狀態清單以及要為這些狀態建立的 *StateModel* 類型。 *StateModel* 是一種類別，可延伸 [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) 和執行狀態機器邏輯，以在執行時間產生目前的狀態。 這個類別的目前狀態通常由主題引擎在執行時間使用，以指定要針對材質屬性、GameObject 轉換等設定哪些值。

### <a name="theme-engine-properties"></a>主題引擎屬性

在 *狀態* 以外， [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 資產也會定義主題引擎清單以及這些引擎的相關聯屬性。 [主題引擎](#theme-engines)會再次定義邏輯，以便在執行時間針對 GameObject 設定正確的值。

[`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme)資產可以定義多個主題引擎，以達到以多個 GameObject 屬性為目標的精密視覺狀態轉換。

**主題執行時間**

定義將建立之主題引擎的類別類型

**寬鬆**

某些 *主題引擎*（如果將其屬性 [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) 定義為 true）支援在狀態之間進行簡化。 例如，在狀態變更發生時，lerping 兩種色彩。 *持續時間* 會以秒為單位定義從開始值到結束值的最長時間，而 *動畫曲線* 會定義在該期間內的變化率。

**著色器屬性**

有些 *主題引擎*（如果將其屬性 [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) 定義為 true）將會在執行時間修改特定著色器屬性。 *著色器* 和 *屬性* 欄位會定義要設為目標的著色器屬性。

### <a name="create-a-theme-configuration-via-code"></a>透過程式碼建立主題設定

一般情況下，您可以透過 Unity inspector 更輕鬆地設計主題設定，但在某些情況下，主題必須透過程式碼在執行時間動態產生。 下列程式碼片段提供如何完成這項工作的範例。

為了協助加速開發，下列 helper 方法有助於簡化安裝程式。

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -使用 [互動](ux-building-blocks/Interactable.md) 元件中使用的四個預設狀態值，建立新的狀態 ScriptableObject。

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -每個主題引擎都會使用該主題執行時間類型所需的正確屬性來定義預設設定。 此協助程式會建立指定主題引擎類型的定義。

```c#
// This code example builds a Theme ScriptableObject that can be used with an Interactable component.
// A random color is selected for the on pressed state every time this code is executed.

// Use the default states utilized in the Interactable component
var defaultStates = Interactable.GetDefaultInteractableStates();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

// Create the Theme configuration asset
Theme testTheme = ScriptableObject.CreateInstance<Theme>();
testTheme.States = defaultStates;
testTheme.Definitions = new List<ThemeDefinition>() { newThemeType };
```

## <a name="theme-engines"></a>主題引擎

[主題引擎](#theme-engines)是延伸自類別的類別 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) 。 這些類別會在執行時間具現化，並使用稍 [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) 早所述的物件進行設定。

### <a name="default-theme-engines"></a>預設主題引擎

MRTK 隨附一組預設的主題引擎，如下所示：

- [`InteractableActivateTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableActivateTheme)
- [`InteractableAnimatorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAnimatorTheme)
- [`InteractableAudioTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioTheme)
- [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
- [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
- [`InteractableGrabScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableGrabScaleTheme)
- [`InteractableMaterialTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableMaterialTheme)
- [`InteractableOffsetTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOffsetTheme)
- [`InteractableRotationTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableRotationTheme)
- [`InteractableScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableScaleTheme)
- [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme)
- [`InteractableStringTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStringTheme)
- [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
- [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

您可以在底下找到預設主題引擎 `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` 。

### <a name="custom-theme-engines"></a>自訂主題引擎

如所述，主題引擎會定義為從類別延伸的類別 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) 。 因此，新的主題引擎只需要擴充此類別，並執行下列動作：

#### <a name="mandatory-implementations"></a>強制實施

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (x： MixedReality，InteractableThemeBase.. SetValue) 

針對可由識別的指定屬性， `ThemeStateProperty.Name` 請在目標 GameObject 主機上設定其目前的狀態值 (也就是 設定材質色彩等) 。 *索引* 會指出要存取的目前狀態值和 *百分比*（介於0和1之間的 float），以用於值之間的簡化/lerping。

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)` (x： MixedReality，InteractableThemeBase. GetProperty) 

針對可由識別的指定屬性，會傳回 `ThemeStateProperty.Name` 目標主機 (GameObject 上設定的目前值，亦即 目前的材質色彩、目前的本機位置位移等) 。 這主要是用來快取狀態之間的開始值。

`public abstract ThemeDefinition GetDefaultThemeDefinition()` (x： MixedReality，InteractableThemeBase. GetDefaultThemeDefinition) 

傳回 [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) 物件，該物件定義自訂主題所需的預設屬性和設定。

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

受保護的公用 `SetValue()` 定義變異，除了提供的 ThemePropertyValue 來設定，而不是使用索引和/或百分比設定。

#### <a name="recommended-overrides"></a>建議的覆寫

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

在這裡執行任何初始化步驟，並以提供的 *GameObject* 參數為目標，並使用 *ThemeDefinition* 參數中定義的屬性和設定。 建議您 `base.Init(host, settings)` 在覆寫的開頭呼叫。

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

如果自訂主題引擎可支援透過屬性設定的值，則可加以簡化 [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) 。

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

如果自訂主題引擎可以支援目標著色器屬性，則為。 建議您從 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 現有的基礎結構進行延伸，以透過 [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)有效率地設定/取得著色器屬性。 著色器屬性資訊會透過和儲存在每一個中 [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) 。

> [!NOTE]
> 如果延伸 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) ，則透過 *new* 覆寫 [InteractableShaderTheme DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty)也會很有用。
>
> 範例程式碼： `protected new const string DefaultShaderProperty = "_Color";`
>
> 此外，下列類別會擴充 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 類別，再次使用 [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 來修改著色器屬性值。 這種方法 [可協助效能](https://docs.unity3d.com/Manual/DrawCallBatching.html) ，因為當值變更時， *MaterialPropertyBlocks* 不會建立新的實例材質。 不過，存取一般 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 類別屬性不會傳回預期的值。 使用 *MaterialPropertyBlocks* 來取得並驗證目前的材質屬性值 (例如 *_Color* 或 *_MainTex*) 。
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

指示主題將任何修改過的屬性重設回其原始值，這些值是在此主題引擎初始化時于主機 GameObject 上設定的。  

### <a name="custom-theme-engine-example"></a>自訂主題引擎範例

以下類別是自訂新主題引擎的範例。 此實作為會在初始化的主機物件上找到 [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) 元件，並根據目前的狀態控制其可見度。

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

// This class demonstrates a custom theme to control a Host's MeshRenderer visibility
public class MeshVisibilityTheme : InteractableThemeBase
{
    // Bool visibility does not make sense for lerping
    public override bool IsEasingSupported => false;

    // No material or shaders are being modified
    public override bool AreShadersSupported => false;

    // Cache reference to the MeshRenderer component on our Host
    private MeshRenderer meshRenderer;

    public MeshVisibilityTheme()
    {
        Types = new Type[] { typeof(MeshRenderer) };
        Name = "Mesh Visibility Theme";
    }

    // Define a default configuration to simplify initialization of this theme engine
    // There is only one state property with a value per available state
    // This state property is a boolean that defines whether the renderer is enabled
    public override ThemeDefinition GetDefaultThemeDefinition()
    {
        return new ThemeDefinition()
        {
            ThemeType = GetType(),
            StateProperties = new List<ThemeStateProperty>()
            {
                new ThemeStateProperty()
                {
                    Name = "Mesh Visible",
                    Type = ThemePropertyTypes.Bool,
                    Values = new List<ThemePropertyValue>(),
                    Default = new ThemePropertyValue() { Bool = true }
                },
            },
            CustomProperties = new List<ThemeProperty>()
        };
    }

    // When initializing, cache a reference to the MeshRenderer component
    public override void Init(GameObject host, ThemeDefinition definition)
    {
        base.Init(host, definition);

        meshRenderer = host.GetComponent<MeshRenderer>();
    }

    // Get the current state of the MeshRenderer visibility
    public override ThemePropertyValue GetProperty(ThemeStateProperty property)
    {
        return new ThemePropertyValue()
        {
            Bool = meshRenderer.enabled
        };
    }

    // Update the MeshRenderer visibility based on the property state value data
    public override void SetValue(ThemeStateProperty property, int index, float percentage)
    {
        meshRenderer.enabled = property.Values[index].Bool;
    }
}
```

## <a name="end-to-end-example"></a>端對端範例

從先前章節中定義的自訂主題引擎延伸，下列程式碼範例示範如何在執行時間控制這個主題。 尤其是，如何設定主題的目前狀態，以便適當地更新 MeshRenderer 可見度。

> [!NOTE]
> `theme.OnUpdate(state,force)` 通常應該在 Update () 方法中呼叫，以支援在值之間使用緩時/lerping 的主題引擎。

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

public class MeshVisibilityController : MonoBehaviour
{
    private MeshVisibilityTheme themeEngine;
    private bool hideMesh = false;

    private void Start()
    {
        // Define the default configuration. State 0 will be on while State 1 will be off
        var themeDefinition = ThemeDefinition.GetDefaultThemeDefinition<MeshVisibilityTheme>().Value;
        themeDefinition.StateProperties[0].Values = new List<ThemePropertyValue>()
        {
            new ThemePropertyValue() { Bool = true }, // show state
            new ThemePropertyValue() { Bool = false }, // hide state
        };

        // Create the actual Theme engine and initialize it with the GameObject we are attached to
        themeEngine = (MeshVisibilityTheme)InteractableThemeBase.CreateAndInitTheme(themeDefinition, this.gameObject);
    }

    private void Update()
    {
        // Update the theme engine to set our MeshRenderer visibility
        // based on our current state (i.e the hideMesh variable)
        themeEngine.OnUpdate(Convert.ToInt32(hideMesh));
    }

    public void ToggleVisibility()
    {
        // Alternate state of visibility
        hideMesh = !hideMesh;
    }
}
```

## <a name="see-also"></a>另請參閱

- [互動](ux-building-blocks/Interactable.md)
