---
title: DiagnosticsSystemGettingStarted
description: 在 MRTK 中啟用和停用診斷的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 452e01aa1df1e5fdfe96cf1e5eef810dadcb0ded
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779850"
---
# <a name="diagnostic-system"></a><span data-ttu-id="3feef-104">診斷系統</span><span class="sxs-lookup"><span data-stu-id="3feef-104">Diagnostic system</span></span>

<span data-ttu-id="3feef-105">混合現實工具組診斷系統提供在應用程式中執行的診斷工具，以啟用應用程式問題的分析。</span><span class="sxs-lookup"><span data-stu-id="3feef-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="3feef-106">診斷系統的第一個版本包含 [Visual Profiler](using-visual-profiler.md) ，可在使用應用程式時分析效能問題。</span><span class="sxs-lookup"><span data-stu-id="3feef-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="3feef-107">開始使用</span><span class="sxs-lookup"><span data-stu-id="3feef-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3feef-108">**_強烈_** 建議您在整個產品開發週期中啟用診斷系統，並在建立和發行最終版本之前停用為最後一項變更。</span><span class="sxs-lookup"><span data-stu-id="3feef-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="3feef-109">開始使用診斷系統有兩個主要步驟。</span><span class="sxs-lookup"><span data-stu-id="3feef-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="3feef-110">[啟用](#enable-diagnostics) 診斷系統</span><span class="sxs-lookup"><span data-stu-id="3feef-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="3feef-111">[設定](#configure-diagnostic-options) 診斷選項</span><span class="sxs-lookup"><span data-stu-id="3feef-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="3feef-112">啟用診斷</span><span class="sxs-lookup"><span data-stu-id="3feef-112">Enable diagnostics</span></span>

<span data-ttu-id="3feef-113">診斷系統是由 MixedRealityToolkit 物件 (或另一個 [服務註冊機構](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 元件) 所管理。</span><span class="sxs-lookup"><span data-stu-id="3feef-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="3feef-114">下列步驟假設使用 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="3feef-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="3feef-115">其他服務註冊機構所需的步驟可能會不同。</span><span class="sxs-lookup"><span data-stu-id="3feef-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="3feef-116">選取場景階層中的 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="3feef-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="3feef-118">將 [偵測器] 面板移至 [診斷系統] 區段，然後勾選 [啟用]</span><span class="sxs-lookup"><span data-stu-id="3feef-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="3feef-119">選取診斷系統執行</span><span class="sxs-lookup"><span data-stu-id="3feef-119">Select the Diagnostics System implementation</span></span>

    ![選取診斷系統執行](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="3feef-121">預設設定檔 `DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔) 的使用者，會將診斷系統預先設定為使用該 [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) 物件。</span><span class="sxs-lookup"><span data-stu-id="3feef-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="3feef-122">設定診斷選項</span><span class="sxs-lookup"><span data-stu-id="3feef-122">Configure diagnostic options</span></span>

<span data-ttu-id="3feef-123">診斷系統會使用設定檔來指定要顯示的元件，以及設定其設定。</span><span class="sxs-lookup"><span data-stu-id="3feef-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="3feef-124">請參閱設定 [診斷系統](configuring-diagnostics.md) ，以取得有關可用元件設定的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="3feef-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3feef-125">雖然您可以在開發應用程式時使用 Unity 的播放模式，而不需要建立和部署步驟，但請務必使用在目標硬體和平臺上執行的已編譯應用程式來評估診斷系統結果。</span><span class="sxs-lookup"><span data-stu-id="3feef-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="3feef-126">效能診斷（例如 [Visual Profiler](using-visual-profiler.md)）在從編輯器中執行時，可能無法正確地反映實際的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="3feef-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="3feef-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3feef-127">See also</span></span>

- [<span data-ttu-id="3feef-128">診斷 API 檔</span><span class="sxs-lookup"><span data-stu-id="3feef-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="3feef-129">設定診斷系統</span><span class="sxs-lookup"><span data-stu-id="3feef-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="3feef-130">使用 Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="3feef-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)
