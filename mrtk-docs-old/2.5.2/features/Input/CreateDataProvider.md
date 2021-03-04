---
title: CreateInputDataProvider
description: 在 MRTK 中建立輸入系統與資料提供者的檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 757a434b3d9ff92080e220e4562a492ecf27f361
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781040"
---
# <a name="creating-an-input-system-data-provider"></a>建立輸入系統資料提供者

混合現實工具組輸入系統是可延伸的系統，可讓您啟用輸入裝置支援。 若要加入新硬體平臺的支援，可能需要自訂輸入資料提供者。

本文說明如何為輸入系統建立自訂資料提供者，也稱為「裝置管理員」。 此處顯示的範例程式碼來自 [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) 。

> 此範例中使用的完整程式碼可以在 MRTK/Providers/WindowsMixedReality 資料夾中找到。

## <a name="namespace-and-folder-structure"></a>命名空間和資料夾結構

資料提供者可以散發為協力廠商附加元件，或作為 Microsoft Mixed Reality 工具組的一部分。 將新資料提供者提交給 MRTK 的核准程式將依案例而有所不同，並會在初始提案時傳達。

> [!Important]
> 如果將輸入系統資料提供者提交至 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組存放庫，則命名空間 **必須** 以 MixedReality (例如 MixedReality. WindowsMixedReality) ，而且程式碼應該位於 MRTK/providers 底下的資料夾中 (例如： MRTK/providers/WindowsMixedReality) 。

### <a name="namespace"></a>命名空間

資料提供者必須具有命名空間，才能減少潛在的名稱衝突。 建議命名空間包含下列元件。

- 公司名稱
- 功能區域

例如，Contoso 公司所建立的輸入資料提供者可能是 "MixedReality"。

### <a name="recommended-folder-structure"></a>建議的資料夾結構

建議在資料夾階層中應資料提供者的原始程式碼，如下圖所示。

![範例資料夾結構](../images/input/ExampleProviderFolderStructure.png)

其中 ContosoInput 包含資料提供者的執行、編輯器資料夾包含偵測器 (以及任何其他 Unity 編輯器的特定程式碼) 、材質資料夾包含支援之控制器的影像，以及設定檔包含一或多個預先製作的設定檔。

> [!Note]
> 您可以在 MixedRealityToolkit\StandardAssets\Textures 資料夾中找到一些常見的控制器映射。

## <a name="implement-the-data-provider"></a>執行資料提供者

### <a name="specify-interface-andor-base-class-inheritance"></a>指定介面和/或基類繼承

所有輸入系統資料提供者都必須執行 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 介面，以指定輸入系統所需的最小功能。 MRTK foundation 包含 [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 可提供此必要功能之預設執行的類別。 針對以 Unity 的 UInput 類別為基礎的裝置， [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) 類別可以用來做為基類。

> [!Note]
> `BaseInputDeviceManager`和 `UnityJoystickManager` 類別會提供所需的實作為 `IMixedRealityInputDeviceManager` 。

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` 使用的， `WindowsMixedRealityDeviceManager` 表示它支援一組輸入功能，特別是明確地說，也就是說出的手、注視手勢、語音手和移動控制器。

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>套用 MixedRealityDataProvider 屬性

建立輸入系統資料提供者的主要步驟是將 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 屬性套用至類別。 此步驟可讓您在輸入系統設定檔中選取時，設定提供者的預設設定檔和平臺 (s) 。

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a>執行 IMixedRealityDataProvider 方法

一旦定義了類別之後，下一個步驟就是提供介面的實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。

> [!Note]
> 透過 `BaseInputDeviceManager` 類別的類別 `BaseService` ，只會為方法提供空白的實作為 `IMixedRealityDataProvider` 。 這些方法的詳細資料通常是資料提供者特有的。

由資料提供者所執行的方法如下：

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>執行資料提供者邏輯

下一步是新增管理輸入裝置的邏輯，包括支援的任何控制器。

### <a name="implement-the-controller-classes"></a>執行控制器類別

 的範例會 `WindowsMixedRealityDeviceManager` 定義並執行下列控制器類別。

> 您可以在 MRTK/Providers/WindowsMixedReality 資料夾中找到每個類別的原始程式碼。

- WindowsMixedRealityArticulatedHand.cs
- WindowsMixedRealityController.cs
- WindowsMixedRealityGGVHand.cs

> [!Note]
> 並非所有的裝置管理員都支援多個控制器類型。

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>套用 MixedRealityController 屬性

接下來，將 [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) 屬性套用至類別。 這個屬性會指定控制器的類型 (例如：明確的手) 、handedness (例如：左方或右方) 以及選用控制器映射。

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>設定互動對應

下一步是要定義控制器所支援的一組互動對應。 對於透過 Unity 的輸入類別接收其資料的裝置， [控制器對應工具](../tools/ControllerMappingTool.md) 是一個有用的資源，可確認要指派給互動的正確軸和按鈕對應。

下列範例是從 `GenericOpenVRController` 類別（位於 MRTK/provider/OpenVR 資料夾中）縮寫。

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
>[`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary)類別提供 Unity 輸入軸和按鈕定義的符號常數。

### <a name="raise-notification-events"></a>引發通知事件

為了讓應用程式能夠回應使用者的輸入，此資料提供者會引發與和介面中所定義之控制器狀態變更對應的通知事件 [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 。

針對數位 (按鈕) 類型控制項，請引發 OnInputDown 和 OnInputUp 事件。

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

針對類比控制項 (例如：) InputChanged 事件應產生的觸控板位置。

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>新增 Unity Profiler 檢測

效能在混合現實應用程式中是很重要的。 每個元件都會增加應用程式必須考慮的額外負荷。 至此，所有輸入資料提供者都必須在內部迴圈中包含 Unity Profiler 檢測，以及經常使用的程式碼路徑。

建議您在檢測自訂提供者時，執行 MRTK 所使用的模式。

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
> 用來識別 profiler 標記的名稱是任意的。 MRTK 會使用下列模式。
>
> "[product] className. 方法名稱-選擇性附注"
>
> 建議自訂資料提供者遵循類似的模式，以協助簡化分析追蹤時特定元件和方法的識別。

## <a name="create-the-profile-and-inspector"></a>建立設定檔和偵測器

在混合現實工具組中，資料提供者會使用 [設定檔](../profiles/Profiles.md)進行設定。

具有其他設定選項的資料提供者 (例如： [InputSimulationService](../input-simulation/InputSimulationService.md)) 應該建立設定檔和偵測器，以允許客戶修改行為，使其最符合應用程式的需求。

> 您可以在 MRTK 中找到本節範例的完整程式碼。Services/InputSimulation 資料夾。

### <a name="define-the-profile"></a>定義設定檔

設定檔內容應該鏡像觀察者的可存取屬性 (例如：更新間隔) 。 在每個介面中定義的所有使用者可設定屬性都應該包含在設定檔中。

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

您 `CreateAssetMenu` 可以將屬性套用至設定檔類別，讓客戶能夠使用 [ **建立 > 資產] > 混合現實工具組 > 設定檔** ] 功能表建立設定檔實例。

### <a name="implement-the-inspector"></a>執行偵測器

設定檔偵測器是用來設定和查看設定檔內容的使用者介面。 每個設定檔偵測器都應擴充 [' BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 類別。

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

`CustomEditor`屬性會通知 Unity 套用偵測器的資產類型。

## <a name="create-assembly-definitions"></a>建立元件定義 (s) 

混合現實工具組會使用元件定義 ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 檔案來指定元件之間的相依性，以及協助 Unity 減少編譯時間。

建議您為所有資料提供者及其編輯器元件建立元件定義檔。

使用先前範例中的 [資料夾結構](#recommended-folder-structure) 時，ContosoInput 資料提供者會有兩個 asmdef 檔案。

第一個元件定義適用于資料提供者。 在此範例中，它會被稱為 ContosoInput，而且會位於範例的 ContosoInput 資料夾中。
此元件定義必須指定 MixedReality 的相依性，以及它所相依的任何其他元件。

ContosoInputEditor 元件定義會指定設定檔偵測器和任何編輯器特定的程式碼。 這個檔案必須位於編輯器程式碼的根資料夾中。 在此範例中，檔案會位於 ContosoInput\Editor 資料夾中。 此元件定義會包含 ContosoInput 元件的參考，以及：

- MixedReality 工具組
- MixedReality。檢查工具
- MixedReality （工具組）

## <a name="register-the-data-provider"></a>註冊資料提供者

一旦建立之後，就可以向輸入系統註冊資料提供者，並在應用程式中使用該資料提供者。

![註冊的輸入系統資料提供者](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>封裝和散發

散發為協力廠商元件的資料提供者，會將封裝和散發的特定詳細資料提供給開發人員的喜好設定。 最常見的解決方案可能是透過 Unity 資產存放區產生 unitypackage 和散發。

如果資料提供者已提交並接受成為 Microsoft Mixed Reality 工具組套件的一部分，Microsoft MRTK 團隊將會將其封裝並散發為 MRTK 供應專案的一部分。

## <a name="see-also"></a>另請參閱

- [輸入系統](Overview.md)
- [`BaseInputDeviceManager` 類](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` 介面](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` 介面](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` 介面](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` 介面](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` 介面](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [控制器對應工具](../tools/ControllerMappingTool.md)
