---
title: SystemExtensionsProvider
description: MRTK 延伸模組和資料提供者
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、系統擴充功能、
ms.openlocfilehash: 37b1a98e0b8cccf377d2165cdcfb39b444e336e8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104701884"
---
# <a name="systems-extension-services-and-data-providers"></a>系統、延伸模組服務和資料提供者

在混合現實工具組中，許多功能都是以服務的形式傳遞。 服務分為三個主要類別：系統、延伸模組服務和資料提供者。

## <a name="systems"></a>認證的系統

系統是提供混合現實工具組核心功能的服務。 所有系統都是介面的實作為 [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 。

- [BoundarySystem](../features/boundary/boundary-system-getting-started.md)
- [CameraSystem](../features/camera-system/camera-system-overview.md)
- [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md)
- [InputSystem](../features/input/overview.md)
- [SceneSystem](../features/scene-system/scene-system-getting-started.md)
- [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [TeleportSystem](../features/teleport-system/teleport-system.md)

每個列出的系統都會出現在 MixedRealityToolkit 元件的配置 [檔](../features/profiles/profiles.md)中。

## <a name="extensions"></a>延伸模組

延伸模組服務是延伸混合現實工具組功能的元件。 所有擴充服務都必須指定它們執行 [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) 介面。

如需建立延伸模組服務的相關資訊，請參閱 [延伸模組服務](../features/extensions/extension-services.md) 文章。

為了可供 MRTK 存取，擴充功能會使用 MixedRealityToolkit 元件設定檔的延伸模組區段來註冊和設定。

![設定延伸模組服務](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>資料提供者

資料提供者是根據其名稱提供資料給混合現實工具組服務的元件。 所有資料提供者都必須指定它們要執行 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 介面。

> [!NOTE]
> 並非所有服務都需要資料提供者。 在混合現實工具組的系統中，輸入和空間感知系統是使用資料提供者的唯一服務。

資料提供者會在服務的設定檔中註冊，才能存取特定的 MRTK 服務。

應用程式程式碼會透過介面存取資料提供者 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 。 為了簡化存取，也可以透過 helper 類別來抓取資料提供者 `CoreServices` 。

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> 雖然 `IMixedRealityDataProvider` 繼承自 `IMixedRealityService` ，但不會向註冊資料提供者 `MixedRealityServiceRegistry` 。 若要存取資料提供者，應用程式程式碼必須查詢它們所註冊的服務實例 (例如：輸入系統) 。

### <a name="input"></a>輸入

MRTK 輸入系統只會利用實作為的資料提供者 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 。

![輸入系統資料提供者](../features/images/input/RegisteredServiceProviders.PNG)

下列範例示範如何存取輸入模擬提供者，以及切換 SmoothEyeTracking 屬性。

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

存取核心輸入系統的資料提供者也可以透過使用 `CoreServices` helper 類別來簡化。

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> 輸入系統只會傳回應用程式執行所在平臺所支援的資料提供者。

如需撰寫 MRTK 輸入系統之資料提供者的詳細資訊，請參閱 [建立輸入系統資料提供者](../features/input/create-data-provider.md)。

### <a name="spatial-awareness"></a>空間感知

MRTK 空間感知系統只會使用可執行介面的資料提供者 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 。

![空間感知系統資料提供者](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

下列範例示範如何存取已註冊的空間網格資料提供者，以及變更網格的可見度。

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

存取核心空間感知系統的資料提供者也可以透過使用 `CoreServices` helper 類別來簡化。

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> 空間感知系統只會傳回應用程式執行所在平臺所支援的資料提供者。

如需撰寫 MRTK 空間感知系統之資料提供者的相關資訊，請參閱 [建立空間感知系統資料提供者](../features/spatial-awareness/create-data-provider.md)。

## <a name="see-also"></a>另請參閱

- [擴充服務](../features/extensions/extension-services.md)
- [建立輸入系統資料提供者](../features/input/create-data-provider.md)
- [建立空間感知系統系統資料提供者](../features/spatial-awareness/create-data-provider.md)
- [IMixedRealityService 介面](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [IMixedRealityDataProvider 介面](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [IMixedRealityExtensionService 介面](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
