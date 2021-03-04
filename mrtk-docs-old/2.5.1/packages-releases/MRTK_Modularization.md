---
title: MRTK_Modularization
description: 描述 MRTK 中的元件化。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 26bb2d0d2eebb7c7450b3eb8ed29c05ab54e3e09
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780966"
---
# <a name="mixed-reality-toolkit-componentization"></a><span data-ttu-id="9acbe-104">混合現實工具組元件化</span><span class="sxs-lookup"><span data-stu-id="9acbe-104">Mixed Reality Toolkit componentization</span></span>

<span data-ttu-id="9acbe-105">混合現實工具組 v2 有一項絕佳的新功能，元件化改善。</span><span class="sxs-lookup"><span data-stu-id="9acbe-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="9acbe-106">可能的話，個別的元件會與所有基礎的核心層隔離。</span><span class="sxs-lookup"><span data-stu-id="9acbe-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="9acbe-107">最小化相關性</span><span class="sxs-lookup"><span data-stu-id="9acbe-107">Minimized dependencies</span></span>

<span data-ttu-id="9acbe-108">MRTK v2 刻意開發成模組化，並將系統服務之間的相依性降到最低， (例如：空間感知) 。</span><span class="sxs-lookup"><span data-stu-id="9acbe-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="9acbe-109">由於某些系統服務的本質 (例如：輸入和遙傳) ，因此存在少量的相依性。</span><span class="sxs-lookup"><span data-stu-id="9acbe-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="9acbe-110">雖然服務預期會需要一或多個資料提供者元件，但它們之間沒有直接連結。</span><span class="sxs-lookup"><span data-stu-id="9acbe-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="9acbe-111">SDK 功能也是如此， (例如：使用者介面元件) 。</span><span class="sxs-lookup"><span data-stu-id="9acbe-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="9acbe-112">元件通訊</span><span class="sxs-lookup"><span data-stu-id="9acbe-112">Component communication</span></span>

<span data-ttu-id="9acbe-113">為了確保元件之間沒有任何直接連結，MRTK v2 會利用服務、資料提供者和應用程式程式碼之間的介面來進行通訊。</span><span class="sxs-lookup"><span data-stu-id="9acbe-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="9acbe-114">這些介面是在中定義，而且所有通訊都是透過混合現實工具組核心元件來路由傳送。</span><span class="sxs-lookup"><span data-stu-id="9acbe-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![使用空間感知系統 via 介面](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="9acbe-116">最小化 MRTK 匯入使用量</span><span class="sxs-lookup"><span data-stu-id="9acbe-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="9acbe-117">目前，MRTK 會匯入為單一基礎封裝 (忽略範例套件是否存在，這是) 的完全選用套件。</span><span class="sxs-lookup"><span data-stu-id="9acbe-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="9acbe-118">您可以藉由手動將匯入的檔案剪下，讓這項耗用量變得較小，但這是高度手動的程式，它沒有妥善定義的指南。</span><span class="sxs-lookup"><span data-stu-id="9acbe-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="9acbe-119">您可以在匯入基礎封裝期間取消核取任意專案。</span><span class="sxs-lookup"><span data-stu-id="9acbe-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="9acbe-120">但是，不建議您在開發初期階段進行這項作業，因為它可能會中斷功能。</span><span class="sxs-lookup"><span data-stu-id="9acbe-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="9acbe-121">在瞭解應用程式的最後一個功能集之後，可以在下列資料夾中執行剪除不必要的提供者和服務：</span><span class="sxs-lookup"><span data-stu-id="9acbe-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="9acbe-122">MRTK/服務</span><span class="sxs-lookup"><span data-stu-id="9acbe-122">MRTK/Services</span></span>
- <span data-ttu-id="9acbe-123">MRTK/提供者</span><span class="sxs-lookup"><span data-stu-id="9acbe-123">MRTK/Providers</span></span>
- <span data-ttu-id="9acbe-124">MRTK/SDK/功能</span><span class="sxs-lookup"><span data-stu-id="9acbe-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="9acbe-125">MRTK v2 **_需要_** 資產/MRTK/核心資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="9acbe-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="9acbe-126">即將推出的功能</span><span class="sxs-lookup"><span data-stu-id="9acbe-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="9acbe-127">應用程式架構</span><span class="sxs-lookup"><span data-stu-id="9acbe-127">Application architecture</span></span>

<span data-ttu-id="9acbe-128">MRTK 將支援以各種不同的架構來建立應用程式，包括：</span><span class="sxs-lookup"><span data-stu-id="9acbe-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="9acbe-129">MixedRealityToolkit 服務定位器</span><span class="sxs-lookup"><span data-stu-id="9acbe-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="9acbe-130">個別服務</span><span class="sxs-lookup"><span data-stu-id="9acbe-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="9acbe-131">自訂服務定位器</span><span class="sxs-lookup"><span data-stu-id="9acbe-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="9acbe-132">混合式架構</span><span class="sxs-lookup"><span data-stu-id="9acbe-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="9acbe-133">選取應用程式架構時，請務必考慮設計彈性和應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="9acbe-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="9acbe-134">此處所述的架構不應該適用于每個應用程式。</span><span class="sxs-lookup"><span data-stu-id="9acbe-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="9acbe-135">MixedRealityToolkit 服務定位器</span><span class="sxs-lookup"><span data-stu-id="9acbe-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="9acbe-136">MRTK 可讓 (，並自動將) 應用程式場景設定為使用預設 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 服務定位器元件。</span><span class="sxs-lookup"><span data-stu-id="9acbe-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="9acbe-137">此元件包含透過設定偵測器設定 MRTK 系統和資料提供者，以及管理元件壽命和核心行為的支援， (例如：更新) 的時機。</span><span class="sxs-lookup"><span data-stu-id="9acbe-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="9acbe-138">所有系統都會以核心設定偵測器表示，不論它們是否存在於專案中或已啟用。</span><span class="sxs-lookup"><span data-stu-id="9acbe-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="9acbe-139">如需詳細資訊，請參閱 [混合式事實設定指南](../configuration/MixedRealityConfigurationGuide.md) 。</span><span class="sxs-lookup"><span data-stu-id="9acbe-139">Please see the [Mixed Reality Configuration Guide](../configuration/MixedRealityConfigurationGuide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="9acbe-140">個別的服務元件</span><span class="sxs-lookup"><span data-stu-id="9acbe-140">Individual service components</span></span>

<span data-ttu-id="9acbe-141">有些開發人員表示想要在應用程式場景階層中包含個別的服務元件。</span><span class="sxs-lookup"><span data-stu-id="9acbe-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="9acbe-142">若要啟用這種用法，服務將需要封裝在自訂註冊機構中，或自行註冊/自我管理。</span><span class="sxs-lookup"><span data-stu-id="9acbe-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="9acbe-143">自我註冊服務會執行 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 並註冊本身，讓應用程式程式碼可以透過登錄探索服務實例。</span><span class="sxs-lookup"><span data-stu-id="9acbe-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="9acbe-144">自我管理服務可以實作為場景階層中的單一物件。</span><span class="sxs-lookup"><span data-stu-id="9acbe-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="9acbe-145">這個物件會提供應用程式程式碼可以用來直接存取服務功能的實例屬性和實例屬性。</span><span class="sxs-lookup"><span data-stu-id="9acbe-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="9acbe-146">自訂服務定位器</span><span class="sxs-lookup"><span data-stu-id="9acbe-146">Custom service locator</span></span>

<span data-ttu-id="9acbe-147">某些開發人員已要求建立自訂服務定位器元件的能力。</span><span class="sxs-lookup"><span data-stu-id="9acbe-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="9acbe-148">自訂服務定位器會執行 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 介面，以及管理使用中服務的生命週期和核心行為。</span><span class="sxs-lookup"><span data-stu-id="9acbe-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="9acbe-149">混合式架構</span><span class="sxs-lookup"><span data-stu-id="9acbe-149">Hybrid architecture</span></span>

<span data-ttu-id="9acbe-150">MRTK 將支援混合式架構，讓開發人員可以視需要或想要的方式合併先前的方法。</span><span class="sxs-lookup"><span data-stu-id="9acbe-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="9acbe-151">例如，開發人員可以從 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 服務定位器開始，然後新增自我註冊服務。</span><span class="sxs-lookup"><span data-stu-id="9acbe-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="9acbe-152">選擇混合式架構時，請務必留意任何重複的工作 (例如：從多個元件) 取得控制器資料。</span><span class="sxs-lookup"><span data-stu-id="9acbe-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>
