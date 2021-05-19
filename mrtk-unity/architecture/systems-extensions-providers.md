---
title: 系統擴充提供者
description: MRTK 延伸模組和資料提供者
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、系統擴充功能、
ms.openlocfilehash: add1f443edb687edfc387a316d83443779e079f9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143504"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="0600c-104">系統、延伸模組服務和資料提供者</span><span class="sxs-lookup"><span data-stu-id="0600c-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="0600c-105">在混合現實工具組中，許多功能都是以服務的形式傳遞。</span><span class="sxs-lookup"><span data-stu-id="0600c-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="0600c-106">服務分為三個主要類別：系統、延伸模組服務和資料提供者。</span><span class="sxs-lookup"><span data-stu-id="0600c-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="0600c-107">認證的系統</span><span class="sxs-lookup"><span data-stu-id="0600c-107">Systems</span></span>

<span data-ttu-id="0600c-108">系統是提供混合現實工具組核心功能的服務。</span><span class="sxs-lookup"><span data-stu-id="0600c-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="0600c-109">所有系統都是介面的實作為 [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 。</span><span class="sxs-lookup"><span data-stu-id="0600c-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="0600c-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="0600c-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="0600c-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="0600c-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="0600c-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="0600c-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="0600c-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="0600c-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="0600c-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="0600c-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="0600c-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="0600c-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="0600c-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="0600c-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="0600c-117">每個列出的系統都會出現在 MixedRealityToolkit 元件的配置 [檔](../features/profiles/profiles.md)中。</span><span class="sxs-lookup"><span data-stu-id="0600c-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="0600c-118">延伸模組</span><span class="sxs-lookup"><span data-stu-id="0600c-118">Extensions</span></span>

<span data-ttu-id="0600c-119">延伸模組服務是延伸混合現實工具組功能的元件。</span><span class="sxs-lookup"><span data-stu-id="0600c-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="0600c-120">所有擴充服務都必須指定它們執行 [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) 介面。</span><span class="sxs-lookup"><span data-stu-id="0600c-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="0600c-121">如需建立延伸模組服務的相關資訊，請參閱 [延伸模組服務](../features/extensions/extension-services.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="0600c-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="0600c-122">為了可供 MRTK 存取，擴充功能會使用 MixedRealityToolkit 元件設定檔的延伸模組區段來註冊和設定。</span><span class="sxs-lookup"><span data-stu-id="0600c-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![設定延伸模組服務](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="0600c-124">資料提供者</span><span class="sxs-lookup"><span data-stu-id="0600c-124">Data providers</span></span>

<span data-ttu-id="0600c-125">資料提供者是根據其名稱提供資料給混合現實工具組服務的元件。</span><span class="sxs-lookup"><span data-stu-id="0600c-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="0600c-126">所有資料提供者都必須指定它們要執行 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 介面。</span><span class="sxs-lookup"><span data-stu-id="0600c-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="0600c-127">並非所有服務都需要資料提供者。</span><span class="sxs-lookup"><span data-stu-id="0600c-127">Not all services will require data providers.</span></span> <span data-ttu-id="0600c-128">在混合現實工具組的系統中，輸入和空間感知系統是使用資料提供者的唯一服務。</span><span class="sxs-lookup"><span data-stu-id="0600c-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="0600c-129">資料提供者會在服務的設定檔中註冊，才能存取特定的 MRTK 服務。</span><span class="sxs-lookup"><span data-stu-id="0600c-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="0600c-130">應用程式程式碼會透過介面存取資料提供者 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 。</span><span class="sxs-lookup"><span data-stu-id="0600c-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="0600c-131">為了簡化存取，也可以透過 helper 類別來抓取資料提供者 `CoreServices` 。</span><span class="sxs-lookup"><span data-stu-id="0600c-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="0600c-132">雖然 `IMixedRealityDataProvider` 繼承自 `IMixedRealityService` ，但不會向註冊資料提供者 `MixedRealityServiceRegistry` 。</span><span class="sxs-lookup"><span data-stu-id="0600c-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="0600c-133">若要存取資料提供者，應用程式程式碼必須查詢它們所註冊的服務實例 (例如：輸入系統) 。</span><span class="sxs-lookup"><span data-stu-id="0600c-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="0600c-134">輸入</span><span class="sxs-lookup"><span data-stu-id="0600c-134">Input</span></span>

<span data-ttu-id="0600c-135">MRTK 輸入系統只會利用實作為的資料提供者 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 。</span><span class="sxs-lookup"><span data-stu-id="0600c-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![輸入系統資料提供者](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="0600c-137">下列範例示範如何存取輸入模擬提供者，以及切換 SmoothEyeTracking 屬性。</span><span class="sxs-lookup"><span data-stu-id="0600c-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

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

<span data-ttu-id="0600c-138">存取核心輸入系統的資料提供者也可以透過使用 `CoreServices` helper 類別來簡化。</span><span class="sxs-lookup"><span data-stu-id="0600c-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="0600c-139">輸入系統只會傳回應用程式執行所在平臺所支援的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="0600c-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="0600c-140">如需撰寫 MRTK 輸入系統之資料提供者的詳細資訊，請參閱 [建立輸入系統資料提供者](../features/input/create-data-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="0600c-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="0600c-141">空間感知</span><span class="sxs-lookup"><span data-stu-id="0600c-141">Spatial awareness</span></span>

<span data-ttu-id="0600c-142">MRTK 空間感知系統只會使用可執行介面的資料提供者 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 。</span><span class="sxs-lookup"><span data-stu-id="0600c-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![空間感知系統資料提供者](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="0600c-144">下列範例示範如何存取已註冊的空間網格資料提供者，以及變更網格的可見度。</span><span class="sxs-lookup"><span data-stu-id="0600c-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

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

<span data-ttu-id="0600c-145">存取核心空間感知系統的資料提供者也可以透過使用 `CoreServices` helper 類別來簡化。</span><span class="sxs-lookup"><span data-stu-id="0600c-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="0600c-146">空間感知系統只會傳回應用程式執行所在平臺所支援的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="0600c-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="0600c-147">如需撰寫 MRTK 空間感知系統之資料提供者的相關資訊，請參閱 [建立空間感知系統資料提供者](../features/spatial-awareness/create-data-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="0600c-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0600c-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0600c-148">See also</span></span>

- [<span data-ttu-id="0600c-149">擴充服務</span><span class="sxs-lookup"><span data-stu-id="0600c-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="0600c-150">建立輸入系統資料提供者</span><span class="sxs-lookup"><span data-stu-id="0600c-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="0600c-151">建立空間感知系統系統資料提供者</span><span class="sxs-lookup"><span data-stu-id="0600c-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="0600c-152">IMixedRealityService 介面</span><span class="sxs-lookup"><span data-stu-id="0600c-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="0600c-153">IMixedRealityDataProvider 介面</span><span class="sxs-lookup"><span data-stu-id="0600c-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="0600c-154">IMixedRealityExtensionService 介面</span><span class="sxs-lookup"><span data-stu-id="0600c-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
