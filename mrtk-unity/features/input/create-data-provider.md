---
title: 建立輸入系統資料提供者
description: 在 MRTK 中建立輸入系統與資料提供者的檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 0b6012871a4d4988fdb70336a3c33455f479bcac
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281929"
---
# <a name="creating-an-input-system-data-provider"></a><span data-ttu-id="15e95-104">建立輸入系統資料提供者</span><span class="sxs-lookup"><span data-stu-id="15e95-104">Creating an input system data provider</span></span>

<span data-ttu-id="15e95-105">混合現實工具組輸入系統是可延伸的系統，可讓您啟用輸入裝置支援。</span><span class="sxs-lookup"><span data-stu-id="15e95-105">The Mixed Reality Toolkit input system is an extensible system for enabling input device support.</span></span> <span data-ttu-id="15e95-106">若要加入新硬體平臺的支援，可能需要自訂輸入資料提供者。</span><span class="sxs-lookup"><span data-stu-id="15e95-106">To add support for a new hardware platform, a custom input data provider may be required.</span></span>

<span data-ttu-id="15e95-107">本文說明如何為輸入系統建立自訂資料提供者，也稱為「裝置管理員」。</span><span class="sxs-lookup"><span data-stu-id="15e95-107">This article describes how to create custom data providers, also called device managers, for the input system.</span></span> <span data-ttu-id="15e95-108">此處顯示的範例程式碼來自 [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) 。</span><span class="sxs-lookup"><span data-stu-id="15e95-108">The example code shown here is from the [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager).</span></span>

> <span data-ttu-id="15e95-109">此範例中使用的完整程式碼可以在 MRTK/Providers/WindowsMixedReality 資料夾中找到。</span><span class="sxs-lookup"><span data-stu-id="15e95-109">The complete code used in this example can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="15e95-110">命名空間和資料夾結構</span><span class="sxs-lookup"><span data-stu-id="15e95-110">Namespace and folder structure</span></span>

<span data-ttu-id="15e95-111">資料提供者可以散發為協力廠商附加元件，或作為 Microsoft Mixed Reality 工具組的一部分。</span><span class="sxs-lookup"><span data-stu-id="15e95-111">Data providers can be distributed as a third party add-on or as a part of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="15e95-112">將新資料提供者提交給 MRTK 的核准程式將依案例而有所不同，並會在初始提案時傳達。</span><span class="sxs-lookup"><span data-stu-id="15e95-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span>

> [!Important]
> <span data-ttu-id="15e95-113">如果將輸入系統資料提供者提交至 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組存放庫，則命名空間 **必須** 以 MixedReality (例如 MixedReality. WindowsMixedReality) ，而且程式碼應該位於 MRTK/providers 底下的資料夾中 (例如： MRTK/providers/WindowsMixedReality) 。</span><span class="sxs-lookup"><span data-stu-id="15e95-113">If an input system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: Microsoft.MixedReality.Toolkit.WindowsMixedReality) and the code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/WindowsMixedReality).</span></span>

### <a name="namespace"></a><span data-ttu-id="15e95-114">命名空間</span><span class="sxs-lookup"><span data-stu-id="15e95-114">Namespace</span></span>

<span data-ttu-id="15e95-115">資料提供者必須具有命名空間，才能減少潛在的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="15e95-115">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="15e95-116">建議命名空間包含下列元件。</span><span class="sxs-lookup"><span data-stu-id="15e95-116">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="15e95-117">公司名稱</span><span class="sxs-lookup"><span data-stu-id="15e95-117">Company name</span></span>
- <span data-ttu-id="15e95-118">功能區域</span><span class="sxs-lookup"><span data-stu-id="15e95-118">Feature area</span></span>

<span data-ttu-id="15e95-119">例如，Contoso 公司所建立的輸入資料提供者可能是 "MixedReality"。</span><span class="sxs-lookup"><span data-stu-id="15e95-119">For example, an input data provider created by the Contoso company may be "Contoso.MixedReality.Toolkit.Input".</span></span>

### <a name="recommended-folder-structure"></a><span data-ttu-id="15e95-120">建議的資料夾結構</span><span class="sxs-lookup"><span data-stu-id="15e95-120">Recommended folder structure</span></span>

<span data-ttu-id="15e95-121">建議在資料夾階層中應資料提供者的原始程式碼，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="15e95-121">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![範例資料夾結構](../images/input/ExampleProviderFolderStructure.png)

<span data-ttu-id="15e95-123">其中 ContosoInput 包含資料提供者的執行、編輯器資料夾包含偵測器 (以及任何其他 Unity 編輯器的特定程式碼) 、材質資料夾包含支援之控制器的影像，以及設定檔包含一或多個預先製作的設定檔。</span><span class="sxs-lookup"><span data-stu-id="15e95-123">Where ContosoInput contains the implementation of the data provider, the Editor folder contains the inspector (and any other Unity editor specific code), the Textures folder contains images of the supported controllers, and Profiles contains one or more pre-made profiles.</span></span>

> [!Note]
> <span data-ttu-id="15e95-124">您可以在 MixedRealityToolkit\StandardAssets\Textures 資料夾中找到一些常見的控制器映射。</span><span class="sxs-lookup"><span data-stu-id="15e95-124">Some common controller images can be found in the MixedRealityToolkit\StandardAssets\Textures folder.</span></span>

## <a name="implement-the-data-provider"></a><span data-ttu-id="15e95-125">執行資料提供者</span><span class="sxs-lookup"><span data-stu-id="15e95-125">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="15e95-126">指定介面和/或基類繼承</span><span class="sxs-lookup"><span data-stu-id="15e95-126">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="15e95-127">所有輸入系統資料提供者都必須執行 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 介面，以指定輸入系統所需的最小功能。</span><span class="sxs-lookup"><span data-stu-id="15e95-127">All input system data providers must implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, which specifies the minimum functionality required by the input system.</span></span> <span data-ttu-id="15e95-128">MRTK foundation 包含 [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 可提供此必要功能之預設執行的類別。</span><span class="sxs-lookup"><span data-stu-id="15e95-128">The MRTK foundation includes the [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) class which provides a default implementation of this required functionality.</span></span> <span data-ttu-id="15e95-129">針對以 Unity 的 UInput 類別為基礎的裝置， [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) 類別可以用來做為基類。</span><span class="sxs-lookup"><span data-stu-id="15e95-129">For devices that build upon Unity's UInput class, the [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) class can be used as a base class.</span></span>

> [!Note]
> <span data-ttu-id="15e95-130">`BaseInputDeviceManager`和 `UnityJoystickManager` 類別會提供所需的實作為 `IMixedRealityInputDeviceManager` 。</span><span class="sxs-lookup"><span data-stu-id="15e95-130">The `BaseInputDeviceManager` and `UnityJoystickManager` classes provide the required `IMixedRealityInputDeviceManager` implementation.</span></span>

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> <span data-ttu-id="15e95-131">`IMixedRealityCapabilityCheck` 使用的， `WindowsMixedRealityDeviceManager` 表示它支援一組輸入功能，特別是明確地說，也就是說出的手、注視手勢、語音手和移動控制器。</span><span class="sxs-lookup"><span data-stu-id="15e95-131">`IMixedRealityCapabilityCheck` is used by the `WindowsMixedRealityDeviceManager` to indicate that it provides support for a set of input capabilities, specifically; articulated hands, gaze-gesture-voice hands and motion controllers.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="15e95-132">套用 MixedRealityDataProvider 屬性</span><span class="sxs-lookup"><span data-stu-id="15e95-132">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="15e95-133">建立輸入系統資料提供者的主要步驟是將 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 屬性套用至類別。</span><span class="sxs-lookup"><span data-stu-id="15e95-133">A key step of creating an input system data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="15e95-134">此步驟可讓您在輸入系統設定檔中選取時，設定提供者的預設設定檔和平臺 (s) 。</span><span class="sxs-lookup"><span data-stu-id="15e95-134">This step enables setting the default profile and platform(s) for the provider, when selected in the input system profile.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="15e95-135">執行 IMixedRealityDataProvider 方法</span><span class="sxs-lookup"><span data-stu-id="15e95-135">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="15e95-136">一旦定義了類別之後，下一個步驟就是提供介面的實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="15e95-136">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!Note]
> <span data-ttu-id="15e95-137">透過 `BaseInputDeviceManager` 類別的類別 `BaseService` ，只會為方法提供空白的實作為 `IMixedRealityDataProvider` 。</span><span class="sxs-lookup"><span data-stu-id="15e95-137">The `BaseInputDeviceManager` class, via the `BaseService` class, provides only empty implementations for `IMixedRealityDataProvider` methods.</span></span> <span data-ttu-id="15e95-138">這些方法的詳細資料通常是資料提供者特有的。</span><span class="sxs-lookup"><span data-stu-id="15e95-138">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="15e95-139">由資料提供者所執行的方法如下：</span><span class="sxs-lookup"><span data-stu-id="15e95-139">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="15e95-140">執行資料提供者邏輯</span><span class="sxs-lookup"><span data-stu-id="15e95-140">Implement the data provider logic</span></span>

<span data-ttu-id="15e95-141">下一步是新增管理輸入裝置的邏輯，包括支援的任何控制器。</span><span class="sxs-lookup"><span data-stu-id="15e95-141">The next step is to add the logic for managing the input devices, including any controllers to be supported.</span></span>

### <a name="implement-the-controller-classes"></a><span data-ttu-id="15e95-142">執行控制器類別</span><span class="sxs-lookup"><span data-stu-id="15e95-142">Implement the controller classes</span></span>

 <span data-ttu-id="15e95-143">的範例會 `WindowsMixedRealityDeviceManager` 定義並執行下列控制器類別。</span><span class="sxs-lookup"><span data-stu-id="15e95-143">The example of the `WindowsMixedRealityDeviceManager` defines and implements the following controller classes.</span></span>

> <span data-ttu-id="15e95-144">您可以在 MRTK/Providers/WindowsMixedReality 資料夾中找到每個類別的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="15e95-144">The source code for each of these classes can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

- <span data-ttu-id="15e95-145">WindowsMixedRealityArticulatedHand .cs</span><span class="sxs-lookup"><span data-stu-id="15e95-145">WindowsMixedRealityArticulatedHand.cs</span></span>
- <span data-ttu-id="15e95-146">WindowsMixedRealityController .cs</span><span class="sxs-lookup"><span data-stu-id="15e95-146">WindowsMixedRealityController.cs</span></span>
- <span data-ttu-id="15e95-147">WindowsMixedRealityGGVHand .cs</span><span class="sxs-lookup"><span data-stu-id="15e95-147">WindowsMixedRealityGGVHand.cs</span></span>

> [!Note]
> <span data-ttu-id="15e95-148">並非所有的裝置管理員都支援多個控制器類型。</span><span class="sxs-lookup"><span data-stu-id="15e95-148">Not all device managers will support multiple controller types.</span></span>

#### <a name="apply-the-mixedrealitycontroller-attribute"></a><span data-ttu-id="15e95-149">套用 MixedRealityController 屬性</span><span class="sxs-lookup"><span data-stu-id="15e95-149">Apply the MixedRealityController attribute</span></span>

<span data-ttu-id="15e95-150">接下來，將 [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) 屬性套用至類別。</span><span class="sxs-lookup"><span data-stu-id="15e95-150">Next, apply the [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribute to the class.</span></span> <span data-ttu-id="15e95-151">這個屬性會指定控制器的類型 (例如：明確的手) 、handedness (例如：左方或右方) 以及選用控制器映射。</span><span class="sxs-lookup"><span data-stu-id="15e95-151">This attribute specifies the type of controller (ex: articulated hand), the handedness (ex: left or right) and an optional controller image.</span></span>

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a><span data-ttu-id="15e95-152">設定互動對應</span><span class="sxs-lookup"><span data-stu-id="15e95-152">Configure the interaction mappings</span></span>

<span data-ttu-id="15e95-153">下一步是要定義控制器所支援的一組互動對應。</span><span class="sxs-lookup"><span data-stu-id="15e95-153">The next step is to define the set of interaction mappings supported by the controller.</span></span> <span data-ttu-id="15e95-154">對於透過 Unity 的輸入類別接收其資料的裝置， [控制器對應工具](../tools/controller-mapping-tool.md) 是一個有用的資源，可確認要指派給互動的正確軸和按鈕對應。</span><span class="sxs-lookup"><span data-stu-id="15e95-154">For devices that receive their data via Unity's Input class, the [controller mapping tool](../tools/controller-mapping-tool.md) is a helpful resource to confirm the correct axis and button mappings to assign to interactions.</span></span>

<span data-ttu-id="15e95-155">下列範例是從 `GenericOpenVRController` 類別（位於 MRTK/provider/OpenVR 資料夾中）縮寫。</span><span class="sxs-lookup"><span data-stu-id="15e95-155">The following example is abbreviated from the `GenericOpenVRController` class, located in the MRTK/Providers/OpenVR folder.</span></span>

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
><span data-ttu-id="15e95-156">[`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary)類別提供 Unity 輸入軸和按鈕定義的符號常數。</span><span class="sxs-lookup"><span data-stu-id="15e95-156">The [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) class provides symbolic constants for the Unity input axis and button definitions.</span></span>

### <a name="raise-notification-events"></a><span data-ttu-id="15e95-157">引發通知事件</span><span class="sxs-lookup"><span data-stu-id="15e95-157">Raise notification events</span></span>

<span data-ttu-id="15e95-158">為了讓應用程式能夠回應使用者的輸入，此資料提供者會引發與和介面中所定義之控制器狀態變更對應的通知事件 [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 。</span><span class="sxs-lookup"><span data-stu-id="15e95-158">To enable applications to respond to input from the user, the data provider raises notification events corresponding to controller state changes as defined in the [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) and [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces.</span></span>

<span data-ttu-id="15e95-159">針對數位 (按鈕) 類型控制項，請引發 OnInputDown 和 OnInputUp 事件。</span><span class="sxs-lookup"><span data-stu-id="15e95-159">For digital (button) type controls, raise the OnInputDown and OnInputUp events.</span></span>

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

<span data-ttu-id="15e95-160">針對類比控制項 (例如：) InputChanged 事件應產生的觸控板位置。</span><span class="sxs-lookup"><span data-stu-id="15e95-160">For analog controls (ex: touchpad position) the InputChanged event should be raised.</span></span>

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="15e95-161">新增 Unity Profiler 檢測</span><span class="sxs-lookup"><span data-stu-id="15e95-161">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="15e95-162">效能在混合現實應用程式中是很重要的。</span><span class="sxs-lookup"><span data-stu-id="15e95-162">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="15e95-163">每個元件都會增加應用程式必須考慮的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="15e95-163">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="15e95-164">至此，所有輸入資料提供者都必須在內部迴圈中包含 Unity Profiler 檢測，以及經常使用的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="15e95-164">To this end, it is important that all input data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="15e95-165">建議您在檢測自訂提供者時，執行 MRTK 所使用的模式。</span><span class="sxs-lookup"><span data-stu-id="15e95-165">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="15e95-166">用來識別 profiler 標記的名稱是任意的。</span><span class="sxs-lookup"><span data-stu-id="15e95-166">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="15e95-167">MRTK 會使用下列模式。</span><span class="sxs-lookup"><span data-stu-id="15e95-167">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="15e95-168">"[product] className. 方法名稱-選擇性附注"</span><span class="sxs-lookup"><span data-stu-id="15e95-168">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="15e95-169">建議自訂資料提供者遵循類似的模式，以協助簡化分析追蹤時特定元件和方法的識別。</span><span class="sxs-lookup"><span data-stu-id="15e95-169">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="15e95-170">建立設定檔和偵測器</span><span class="sxs-lookup"><span data-stu-id="15e95-170">Create the profile and inspector</span></span>

<span data-ttu-id="15e95-171">在混合現實工具組中，資料提供者會使用 [設定檔](../profiles/profiles.md)進行設定。</span><span class="sxs-lookup"><span data-stu-id="15e95-171">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

<span data-ttu-id="15e95-172">具有其他設定選項的資料提供者 (例如： [InputSimulationService](../input-simulation/input-simulation-service.md)) 應該建立設定檔和偵測器，以允許客戶修改行為，使其最符合應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="15e95-172">Data providers with additional configuration options (ex: [InputSimulationService](../input-simulation/input-simulation-service.md)) should create a profile and inspector to allow customers to modify the behavior to best suit the needs of the application.</span></span>

> <span data-ttu-id="15e95-173">您可以在 MRTK 中找到本節範例的完整程式碼。Services/InputSimulation 資料夾。</span><span class="sxs-lookup"><span data-stu-id="15e95-173">The complete code for the example in this section can be found in the MRTK.Services/InputSimulation folder.</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="15e95-174">定義設定檔</span><span class="sxs-lookup"><span data-stu-id="15e95-174">Define the profile</span></span>

<span data-ttu-id="15e95-175">設定檔內容應該鏡像觀察者的可存取屬性 (例如：更新間隔) 。</span><span class="sxs-lookup"><span data-stu-id="15e95-175">Profile contents should mirror the accessible properties of the observer (ex: update interval).</span></span> <span data-ttu-id="15e95-176">在每個介面中定義的所有使用者可設定屬性都應該包含在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="15e95-176">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

<span data-ttu-id="15e95-177">您 `CreateAssetMenu` 可以將屬性套用至設定檔類別，讓客戶能夠使用 [ **建立 > 資產] > 混合現實工具組 > 設定檔** ] 功能表建立設定檔實例。</span><span class="sxs-lookup"><span data-stu-id="15e95-177">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create > Assets > Mixed Reality Toolkit > Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="15e95-178">執行偵測器</span><span class="sxs-lookup"><span data-stu-id="15e95-178">Implement the inspector</span></span>

<span data-ttu-id="15e95-179">設定檔偵測器是用來設定和查看設定檔內容的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="15e95-179">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="15e95-180">每個設定檔偵測器都應擴充 [' BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 類別。</span><span class="sxs-lookup"><span data-stu-id="15e95-180">Each profile inspector should extend the [\`BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

<span data-ttu-id="15e95-181">`CustomEditor`屬性會通知 Unity 套用偵測器的資產類型。</span><span class="sxs-lookup"><span data-stu-id="15e95-181">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

## <a name="create-assembly-definitions"></a><span data-ttu-id="15e95-182">建立元件定義 (s) </span><span class="sxs-lookup"><span data-stu-id="15e95-182">Create assembly definition(s)</span></span>

<span data-ttu-id="15e95-183">混合現實工具組會使用元件定義 ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 檔案來指定元件之間的相依性，以及協助 Unity 減少編譯時間。</span><span class="sxs-lookup"><span data-stu-id="15e95-183">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="15e95-184">建議您為所有資料提供者及其編輯器元件建立元件定義檔。</span><span class="sxs-lookup"><span data-stu-id="15e95-184">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="15e95-185">使用先前範例中的 [資料夾結構](#recommended-folder-structure) 時，ContosoInput 資料提供者會有兩個 asmdef 檔案。</span><span class="sxs-lookup"><span data-stu-id="15e95-185">Using the [folder structure](#recommended-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoInput data provider.</span></span>

<span data-ttu-id="15e95-186">第一個元件定義適用于資料提供者。</span><span class="sxs-lookup"><span data-stu-id="15e95-186">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="15e95-187">在此範例中，它會被稱為 ContosoInput，而且會位於範例的 ContosoInput 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="15e95-187">For this example, it will be called ContosoInput and will be located in the example's ContosoInput folder.</span></span>
<span data-ttu-id="15e95-188">此元件定義必須指定 MixedReality 的相依性，以及它所相依的任何其他元件。</span><span class="sxs-lookup"><span data-stu-id="15e95-188">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="15e95-189">ContosoInputEditor 元件定義會指定設定檔偵測器和任何編輯器特定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="15e95-189">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="15e95-190">這個檔案必須位於編輯器程式碼的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="15e95-190">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="15e95-191">在此範例中，檔案會位於 ContosoInput\Editor 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="15e95-191">In this example, the file will be located in the ContosoInput\Editor folder.</span></span> <span data-ttu-id="15e95-192">此元件定義會包含 ContosoInput 元件的參考，以及：</span><span class="sxs-lookup"><span data-stu-id="15e95-192">This assembly definition will contain a reference to the ContosoInput assembly as well as:</span></span>

- <span data-ttu-id="15e95-193">MixedReality 工具組</span><span class="sxs-lookup"><span data-stu-id="15e95-193">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="15e95-194">MixedReality。檢查工具</span><span class="sxs-lookup"><span data-stu-id="15e95-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="15e95-195">MixedReality （工具組）</span><span class="sxs-lookup"><span data-stu-id="15e95-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="15e95-196">註冊資料提供者</span><span class="sxs-lookup"><span data-stu-id="15e95-196">Register the data provider</span></span>

<span data-ttu-id="15e95-197">一旦建立之後，就可以向輸入系統註冊資料提供者，並在應用程式中使用該資料提供者。</span><span class="sxs-lookup"><span data-stu-id="15e95-197">Once created, the data provider can be registered with the input system and be used in the application.</span></span>

![註冊的輸入系統資料提供者](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a><span data-ttu-id="15e95-199">封裝和散發</span><span class="sxs-lookup"><span data-stu-id="15e95-199">Packaging and distribution</span></span>

<span data-ttu-id="15e95-200">散發為協力廠商元件的資料提供者，會將封裝和散發的特定詳細資料提供給開發人員的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="15e95-200">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="15e95-201">最常見的解決方案可能是透過 Unity 資產存放區產生 unitypackage 和散發。</span><span class="sxs-lookup"><span data-stu-id="15e95-201">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="15e95-202">如果資料提供者已提交並接受成為 Microsoft Mixed Reality 工具組套件的一部分，Microsoft MRTK 團隊將會將其封裝並散發為 MRTK 供應專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="15e95-202">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="15e95-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15e95-203">See also</span></span>

- [<span data-ttu-id="15e95-204">輸入系統</span><span class="sxs-lookup"><span data-stu-id="15e95-204">Input system</span></span>](overview.md)
- [<span data-ttu-id="15e95-205">`BaseInputDeviceManager` 類別</span><span class="sxs-lookup"><span data-stu-id="15e95-205">`BaseInputDeviceManager` class</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [<span data-ttu-id="15e95-206">`IMixedRealityInputDeviceManager` 介面</span><span class="sxs-lookup"><span data-stu-id="15e95-206">`IMixedRealityInputDeviceManager` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [<span data-ttu-id="15e95-207">`IMixedRealityInputHandler` 介面</span><span class="sxs-lookup"><span data-stu-id="15e95-207">`IMixedRealityInputHandler` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [<span data-ttu-id="15e95-208">`IMixedRealityInputHandler<T>` 介面</span><span class="sxs-lookup"><span data-stu-id="15e95-208">`IMixedRealityInputHandler<T>` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [<span data-ttu-id="15e95-209">`IMixedRealityDataProvider` 介面</span><span class="sxs-lookup"><span data-stu-id="15e95-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="15e95-210">`IMixedRealityCapabilityCheck` 介面</span><span class="sxs-lookup"><span data-stu-id="15e95-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="15e95-211">控制器對應工具</span><span class="sxs-lookup"><span data-stu-id="15e95-211">Controller Mapping Tool</span></span>](../tools/controller-mapping-tool.md)
