---
title: VisualThemes
description: 總覽視覺主題彈性地控制 MRTK 中的 UX 資產
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、MRTK 主題、
ms.openlocfilehash: 319859a935989bb8890cc87199672b5cbbd32987
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686051"
---
# <a name="visual-themes"></a><span data-ttu-id="00a1c-104">視覺主題</span><span class="sxs-lookup"><span data-stu-id="00a1c-104">Visual themes</span></span>

<span data-ttu-id="00a1c-105">主題可讓您彈性地控制 UX 資產，以回應各種狀態轉換。</span><span class="sxs-lookup"><span data-stu-id="00a1c-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="00a1c-106">這可能牽涉到變更按鈕的色彩、調整元素的大小以回應焦點等等。視覺化主題架構是由兩個主要部分所組成： 1) 設定和 2) 執行時間引擎。</span><span class="sxs-lookup"><span data-stu-id="00a1c-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="00a1c-107">[主題](#theme-configuration) 設定是屬性和類型的定義，而 [主題引擎](#theme-engines) 是使用設定的類別，並在執行時間執行邏輯以更新轉換、材質和其他。</span><span class="sxs-lookup"><span data-stu-id="00a1c-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="00a1c-108">主題設定</span><span class="sxs-lookup"><span data-stu-id="00a1c-108">Theme configuration</span></span>

<span data-ttu-id="00a1c-109">主題設定是 [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) ，可定義如何在執行時間初始化主題引擎。</span><span class="sxs-lookup"><span data-stu-id="00a1c-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="00a1c-110">當應用程式正在執行時，它們會定義要使用哪些屬性和值來回應輸入或其他狀態變更。</span><span class="sxs-lookup"><span data-stu-id="00a1c-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="00a1c-111">作為 [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 資產，主題設定可以定義一次，然後在不同的 UX 元件之間重複使用。</span><span class="sxs-lookup"><span data-stu-id="00a1c-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="00a1c-112">若要建立新的 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 資產：</span><span class="sxs-lookup"><span data-stu-id="00a1c-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="00a1c-113">以滑鼠右鍵按一下 [ *專案] 視窗*</span><span class="sxs-lookup"><span data-stu-id="00a1c-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="00a1c-114">選取 [**建立**  >  **混合現實工具** 組]  >  **主題**</span><span class="sxs-lookup"><span data-stu-id="00a1c-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="00a1c-115">您可以在下方找到範例主題設定資產 `MRTK/SDK/Features/UX/Interactable/Themes` 。</span><span class="sxs-lookup"><span data-stu-id="00a1c-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Inspector 中的主題 ScriptableObject 範例](images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="00a1c-117">狀態</span><span class="sxs-lookup"><span data-stu-id="00a1c-117">States</span></span>

<span data-ttu-id="00a1c-118">建立新的時 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ，要設定的第一件事就是可用的狀態。</span><span class="sxs-lookup"><span data-stu-id="00a1c-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="00a1c-119">[ *狀態* ] 屬性會指出主題設定需要定義多少個值，因為每個狀態都有一個值。</span><span class="sxs-lookup"><span data-stu-id="00a1c-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="00a1c-120">在上述的範例影像中， [針對互動元件定義的預設狀態](ux-building-blocks/interactable.md#general-input-settings) 為 *預設*、 *焦點*、已 *按* 下和 *停用*。</span><span class="sxs-lookup"><span data-stu-id="00a1c-120">In the example image above, the [default states defined for the Interactable](ux-building-blocks/interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="00a1c-121">這些是在 `DefaultInteractableStates` (資產/MRTK/SDK/Features/UX/互動/州) 資產檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="00a1c-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="00a1c-122">若要建立新的 [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) 資產：</span><span class="sxs-lookup"><span data-stu-id="00a1c-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="00a1c-123">以滑鼠右鍵按一下 [ *專案] 視窗*</span><span class="sxs-lookup"><span data-stu-id="00a1c-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="00a1c-124">選取 [**建立**  >  **混合的實際工具** 組  >  **狀態**]</span><span class="sxs-lookup"><span data-stu-id="00a1c-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![偵測器中的狀態 ScriptableObject 範例](images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="00a1c-126">[`State`](xref:Microsoft.MixedReality.Toolkit.UI.States)ScriptableObject 會定義狀態清單以及要為這些狀態建立的 *StateModel* 類型。</span><span class="sxs-lookup"><span data-stu-id="00a1c-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="00a1c-127">*StateModel* 是一種類別，可延伸 [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) 和執行狀態機器邏輯，以在執行時間產生目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="00a1c-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="00a1c-128">這個類別的目前狀態通常由主題引擎在執行時間使用，以指定要針對材質屬性、GameObject 轉換等設定哪些值。</span><span class="sxs-lookup"><span data-stu-id="00a1c-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="00a1c-129">主題引擎屬性</span><span class="sxs-lookup"><span data-stu-id="00a1c-129">Theme engine properties</span></span>

<span data-ttu-id="00a1c-130">在 *狀態* 以外， [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 資產也會定義主題引擎清單以及這些引擎的相關聯屬性。</span><span class="sxs-lookup"><span data-stu-id="00a1c-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="00a1c-131">[主題引擎](#theme-engines)會再次定義邏輯，以便在執行時間針對 GameObject 設定正確的值。</span><span class="sxs-lookup"><span data-stu-id="00a1c-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="00a1c-132">[`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme)資產可以定義多個主題引擎，以達到以多個 GameObject 屬性為目標的精密視覺狀態轉換。</span><span class="sxs-lookup"><span data-stu-id="00a1c-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="00a1c-133">**主題執行時間**</span><span class="sxs-lookup"><span data-stu-id="00a1c-133">**Theme Runtime**</span></span>

<span data-ttu-id="00a1c-134">定義將建立之主題引擎的類別類型</span><span class="sxs-lookup"><span data-stu-id="00a1c-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="00a1c-135">**寬鬆**</span><span class="sxs-lookup"><span data-stu-id="00a1c-135">**Easing**</span></span>

<span data-ttu-id="00a1c-136">某些 *主題引擎*（如果將其屬性 [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) 定義為 true）支援在狀態之間進行簡化。</span><span class="sxs-lookup"><span data-stu-id="00a1c-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="00a1c-137">例如，在狀態變更發生時，lerping 兩種色彩。</span><span class="sxs-lookup"><span data-stu-id="00a1c-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="00a1c-138">*持續時間* 會以秒為單位定義從開始值到結束值的最長時間，而 *動畫曲線* 會定義在該期間內的變化率。</span><span class="sxs-lookup"><span data-stu-id="00a1c-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="00a1c-139">**著色器屬性**</span><span class="sxs-lookup"><span data-stu-id="00a1c-139">**Shader properties**</span></span>

<span data-ttu-id="00a1c-140">有些 *主題引擎*（如果將其屬性 [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) 定義為 true）將會在執行時間修改特定著色器屬性。</span><span class="sxs-lookup"><span data-stu-id="00a1c-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="00a1c-141">*著色器* 和 *屬性* 欄位會定義要設為目標的著色器屬性。</span><span class="sxs-lookup"><span data-stu-id="00a1c-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="00a1c-142">透過程式碼建立主題設定</span><span class="sxs-lookup"><span data-stu-id="00a1c-142">Create a theme configuration via code</span></span>

<span data-ttu-id="00a1c-143">一般情況下，您可以透過 Unity inspector 更輕鬆地設計主題設定，但在某些情況下，主題必須透過程式碼在執行時間動態產生。</span><span class="sxs-lookup"><span data-stu-id="00a1c-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="00a1c-144">下列程式碼片段提供如何完成這項工作的範例。</span><span class="sxs-lookup"><span data-stu-id="00a1c-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="00a1c-145">為了協助加速開發，下列 helper 方法有助於簡化安裝程式。</span><span class="sxs-lookup"><span data-stu-id="00a1c-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="00a1c-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -使用 [互動](ux-building-blocks/interactable.md) 元件中使用的四個預設狀態值，建立新的狀態 ScriptableObject。</span><span class="sxs-lookup"><span data-stu-id="00a1c-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](ux-building-blocks/interactable.md) component.</span></span>

<span data-ttu-id="00a1c-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -每個主題引擎都會使用該主題執行時間類型所需的正確屬性來定義預設設定。</span><span class="sxs-lookup"><span data-stu-id="00a1c-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="00a1c-148">此協助程式會建立指定主題引擎類型的定義。</span><span class="sxs-lookup"><span data-stu-id="00a1c-148">This helper creates a definition for the given Theme Engine type.</span></span>

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

## <a name="theme-engines"></a><span data-ttu-id="00a1c-149">主題引擎</span><span class="sxs-lookup"><span data-stu-id="00a1c-149">Theme engines</span></span>

<span data-ttu-id="00a1c-150">[主題引擎](#theme-engines)是延伸自類別的類別 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) 。</span><span class="sxs-lookup"><span data-stu-id="00a1c-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="00a1c-151">這些類別會在執行時間具現化，並使用稍 [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) 早所述的物件進行設定。</span><span class="sxs-lookup"><span data-stu-id="00a1c-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="00a1c-152">預設主題引擎</span><span class="sxs-lookup"><span data-stu-id="00a1c-152">Default theme engines</span></span>

<span data-ttu-id="00a1c-153">MRTK 隨附一組預設的主題引擎，如下所示：</span><span class="sxs-lookup"><span data-stu-id="00a1c-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

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

<span data-ttu-id="00a1c-154">您可以在底下找到預設主題引擎 `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` 。</span><span class="sxs-lookup"><span data-stu-id="00a1c-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="00a1c-155">自訂主題引擎</span><span class="sxs-lookup"><span data-stu-id="00a1c-155">Custom theme engines</span></span>

<span data-ttu-id="00a1c-156">如所述，主題引擎會定義為從類別延伸的類別 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) 。</span><span class="sxs-lookup"><span data-stu-id="00a1c-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="00a1c-157">因此，新的主題引擎只需要擴充此類別，並執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="00a1c-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="00a1c-158">強制實施</span><span class="sxs-lookup"><span data-stu-id="00a1c-158">Mandatory implementations</span></span>

<span data-ttu-id="00a1c-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (x： MixedReality，InteractableThemeBase.. SetValue) </span><span class="sxs-lookup"><span data-stu-id="00a1c-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="00a1c-160">針對可由識別的指定屬性， `ThemeStateProperty.Name` 請在目標 GameObject 主機上設定其目前的狀態值 (也就是</span><span class="sxs-lookup"><span data-stu-id="00a1c-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="00a1c-161">設定材質色彩等) 。</span><span class="sxs-lookup"><span data-stu-id="00a1c-161">set the material color, etc).</span></span> <span data-ttu-id="00a1c-162">*索引* 會指出要存取的目前狀態值和 *百分比*（介於0和1之間的 float），以用於值之間的簡化/lerping。</span><span class="sxs-lookup"><span data-stu-id="00a1c-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="00a1c-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)` (x： MixedReality，InteractableThemeBase. GetProperty) </span><span class="sxs-lookup"><span data-stu-id="00a1c-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="00a1c-164">針對可由識別的指定屬性，會傳回 `ThemeStateProperty.Name` 目標主機 (GameObject 上設定的目前值，亦即</span><span class="sxs-lookup"><span data-stu-id="00a1c-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="00a1c-165">目前的材質色彩、目前的本機位置位移等) 。</span><span class="sxs-lookup"><span data-stu-id="00a1c-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="00a1c-166">這主要是用來快取狀態之間的開始值。</span><span class="sxs-lookup"><span data-stu-id="00a1c-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="00a1c-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()` (x： MixedReality，InteractableThemeBase. GetDefaultThemeDefinition) </span><span class="sxs-lookup"><span data-stu-id="00a1c-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="00a1c-168">傳回 [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) 物件，該物件定義自訂主題所需的預設屬性和設定。</span><span class="sxs-lookup"><span data-stu-id="00a1c-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="00a1c-169">受保護的公用 `SetValue()` 定義變異，除了提供的 ThemePropertyValue 來設定，而不是使用索引和/或百分比設定。</span><span class="sxs-lookup"><span data-stu-id="00a1c-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="00a1c-170">建議的覆寫</span><span class="sxs-lookup"><span data-stu-id="00a1c-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="00a1c-171">在這裡執行任何初始化步驟，並以提供的 *GameObject* 參數為目標，並使用 *ThemeDefinition* 參數中定義的屬性和設定。</span><span class="sxs-lookup"><span data-stu-id="00a1c-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="00a1c-172">建議您 `base.Init(host, settings)` 在覆寫的開頭呼叫。</span><span class="sxs-lookup"><span data-stu-id="00a1c-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="00a1c-173">如果自訂主題引擎可支援透過屬性設定的值，則可加以簡化 [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) 。</span><span class="sxs-lookup"><span data-stu-id="00a1c-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="00a1c-174">如果自訂主題引擎可以支援目標著色器屬性，則為。</span><span class="sxs-lookup"><span data-stu-id="00a1c-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="00a1c-175">建議您從 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 現有的基礎結構進行延伸，以透過 [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)有效率地設定/取得著色器屬性。</span><span class="sxs-lookup"><span data-stu-id="00a1c-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="00a1c-176">著色器屬性資訊會透過和儲存在每一個中 [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) 。</span><span class="sxs-lookup"><span data-stu-id="00a1c-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="00a1c-177">如果延伸 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) ，則透過 *new* 覆寫 [InteractableShaderTheme DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty)也會很有用。</span><span class="sxs-lookup"><span data-stu-id="00a1c-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="00a1c-178">範例程式碼： `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="00a1c-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="00a1c-179">此外，下列類別會擴充 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 類別，再次使用 [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 來修改著色器屬性值。</span><span class="sxs-lookup"><span data-stu-id="00a1c-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="00a1c-180">這種方法 [可協助效能](https://docs.unity3d.com/Manual/DrawCallBatching.html) ，因為當值變更時， *MaterialPropertyBlocks* 不會建立新的實例材質。</span><span class="sxs-lookup"><span data-stu-id="00a1c-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="00a1c-181">不過，存取一般 [材質](https://docs.unity3d.com/ScriptReference/Material.html) 類別屬性不會傳回預期的值。</span><span class="sxs-lookup"><span data-stu-id="00a1c-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="00a1c-182">使用 *MaterialPropertyBlocks* 來取得並驗證目前的材質屬性值 (例如</span><span class="sxs-lookup"><span data-stu-id="00a1c-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="00a1c-183">*_Color* 或 *_MainTex*) 。</span><span class="sxs-lookup"><span data-stu-id="00a1c-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="00a1c-184">指示主題將任何修改過的屬性重設回其原始值，這些值是在此主題引擎初始化時于主機 GameObject 上設定的。</span><span class="sxs-lookup"><span data-stu-id="00a1c-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="00a1c-185">自訂主題引擎範例</span><span class="sxs-lookup"><span data-stu-id="00a1c-185">Custom theme engine example</span></span>

<span data-ttu-id="00a1c-186">以下類別是自訂新主題引擎的範例。</span><span class="sxs-lookup"><span data-stu-id="00a1c-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="00a1c-187">此實作為會在初始化的主機物件上找到 [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) 元件，並根據目前的狀態控制其可見度。</span><span class="sxs-lookup"><span data-stu-id="00a1c-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="00a1c-188">端對端範例</span><span class="sxs-lookup"><span data-stu-id="00a1c-188">End-to-end example</span></span>

<span data-ttu-id="00a1c-189">從先前章節中定義的自訂主題引擎延伸，下列程式碼範例示範如何在執行時間控制這個主題。</span><span class="sxs-lookup"><span data-stu-id="00a1c-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="00a1c-190">尤其是，如何設定主題的目前狀態，以便適當地更新 MeshRenderer 可見度。</span><span class="sxs-lookup"><span data-stu-id="00a1c-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="00a1c-191">`theme.OnUpdate(state,force)` 通常應該在 Update () 方法中呼叫，以支援在值之間使用緩時/lerping 的主題引擎。</span><span class="sxs-lookup"><span data-stu-id="00a1c-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="00a1c-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00a1c-192">See also</span></span>

- [<span data-ttu-id="00a1c-193">互動</span><span class="sxs-lookup"><span data-stu-id="00a1c-193">Interactable</span></span>](ux-building-blocks/interactable.md)
