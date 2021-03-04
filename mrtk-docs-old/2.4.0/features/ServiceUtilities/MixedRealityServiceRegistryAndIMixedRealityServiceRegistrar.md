---
title: MixedRealityServiceRegistryAndIMixedRealityServiceRegistrar
description: MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar 的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 26e1506821c4300968c292d507c9ca395733405b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780330"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a><span data-ttu-id="7c5e2-104">MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar 有哪些？</span><span class="sxs-lookup"><span data-stu-id="7c5e2-104">What are the MixedRealityServiceRegistry and IMixedRealityServiceRegistrar?</span></span>

<span data-ttu-id="7c5e2-105">混合現實工具組有兩個類似的命名元件，可執行相關工作： MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="7c5e2-106">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="7c5e2-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="7c5e2-107">[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)是包含每個已註冊服務實例的元件， (核心系統和擴充服務) 。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="7c5e2-108">MixedRealityServiceRegistry 包含可執行 [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 介面之物件的實例，包括 [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="7c5e2-109">執行 [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 的物件 (IMixedRealityService) 的子類別會明確地未在 MixedRealityServiceRegistry 中註冊。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="7c5e2-110">這些物件是由個別服務所管理 (例如：空間感知) 。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="7c5e2-111">MixedRealityServiceRegistry 會實作為靜態 c # 類別，並且是在應用程式程式碼中用來取得服務實例的建議模式。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="7c5e2-112">下列程式碼片段示範如何取得 IMixedRealityInputSystem 實例。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="7c5e2-113">IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="7c5e2-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="7c5e2-114">[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)是一個介面，定義管理一或多個服務之註冊的元件所執行的功能。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="7c5e2-115">執行 IMixedRealityServiceRegistrar 的元件會負責新增和移除 MixedRealityServiceRegistry 中的資料。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="7c5e2-116">[MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)物件是一個這類元件。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="7c5e2-117">其他註冊機構可以在 MRTK/SDK/實驗/功能資料夾中找到。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="7c5e2-118">這些元件可以用來將單一服務 (例如：空間感知) 支援新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="7c5e2-119">以下列出這些單一服務管理員。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="7c5e2-120">BoundarySystemManager</span><span class="sxs-lookup"><span data-stu-id="7c5e2-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="7c5e2-121">CameraSystemManager</span><span class="sxs-lookup"><span data-stu-id="7c5e2-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="7c5e2-122">DiagnosticsSystemManager</span><span class="sxs-lookup"><span data-stu-id="7c5e2-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="7c5e2-123">InputSystemManager</span><span class="sxs-lookup"><span data-stu-id="7c5e2-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="7c5e2-124">SpatialAwarenessSystemManager</span><span class="sxs-lookup"><span data-stu-id="7c5e2-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="7c5e2-125">TeleportSystemManager</span><span class="sxs-lookup"><span data-stu-id="7c5e2-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="7c5e2-126">上述每個元件（InputSystemManager 除外）都會負責管理單一服務類型的註冊和狀態。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="7c5e2-127">InputSystem 需要一些額外的支援服務 (例如： FocusProvider) ，也是由 InputSystemManager 管理。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="7c5e2-128">一般來說，服務管理元件會在內部呼叫 IMixedRealityServiceRegistrar 所定義的方法，或由需要額外服務元件才能正常運作的服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="7c5e2-129">一般來說，應用程式程式碼應該不會呼叫這些方法，因為這樣可能會導致應用程式無法預期的行為 (例如：快取的服務實例可能會變成不正確) 。</span><span class="sxs-lookup"><span data-stu-id="7c5e2-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="7c5e2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c5e2-130">See also</span></span>

- [<span data-ttu-id="7c5e2-131">IMixedRealityServiceRegistrar API 檔</span><span class="sxs-lookup"><span data-stu-id="7c5e2-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="7c5e2-132">MixedRealityServiceRegistry API 檔</span><span class="sxs-lookup"><span data-stu-id="7c5e2-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
