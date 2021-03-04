---
title: MRTK_Pakages
description: MRTK 中的套件支援混合現實硬體和平臺。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Unity Pakage Manager、
ms.openlocfilehash: e55077df9f6415b50b0dd6b614696914c49e702e
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781088"
---
# <a name="mixed-reality-toolkit-packages"></a><span data-ttu-id="a178e-104">混合現實工具組套件</span><span class="sxs-lookup"><span data-stu-id="a178e-104">Mixed Reality Toolkit packages</span></span>

<span data-ttu-id="a178e-105"> (MRTK) 的混合現實工具組是封裝的集合，可提供混合現實硬體和平臺的支援，藉此啟用跨平臺混合現實應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="a178e-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms.</span></span>

<span data-ttu-id="a178e-106">MRTK 隨附于下列 Unity 套件：</span><span class="sxs-lookup"><span data-stu-id="a178e-106">The MRTK ships via the following Unity packages:</span></span>

- [<span data-ttu-id="a178e-107">基礎</span><span class="sxs-lookup"><span data-stu-id="a178e-107">Foundation</span></span>](#foundation-package)
- [<span data-ttu-id="a178e-108">擴充功能</span><span class="sxs-lookup"><span data-stu-id="a178e-108">Extensions</span></span>](#extensions-package)
- [<span data-ttu-id="a178e-109">範例</span><span class="sxs-lookup"><span data-stu-id="a178e-109">Examples</span></span>](#examples-package)
- [<span data-ttu-id="a178e-110">工具</span><span class="sxs-lookup"><span data-stu-id="a178e-110">Tools</span></span>](#tools-package)

<span data-ttu-id="a178e-111">Microsoft 會從 GitHub 上 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) 分支中的原始程式碼發行並支援這些套件。</span><span class="sxs-lookup"><span data-stu-id="a178e-111">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

## <a name="foundation-package"></a><span data-ttu-id="a178e-112">基礎封裝</span><span class="sxs-lookup"><span data-stu-id="a178e-112">Foundation package</span></span>

<span data-ttu-id="a178e-113">混合現實工具組基礎是一組程式碼，可讓您的應用程式跨混合現實平臺運用一般功能。</span><span class="sxs-lookup"><span data-stu-id="a178e-113">The Mixed Reality Toolkit Foundation is the set of code that enables your application to leverage common functionality across Mixed Reality Platforms.</span></span>

<img src="../features//Images/Input/MRTK_Package_Foundation.png" width="350px" alt="Pakage Foundation" style="display:block;">  
<span data-ttu-id="a178e-114"><sup>MRTK 基礎封裝</sup></span><span class="sxs-lookup"><span data-stu-id="a178e-114"><sup>MRTK Foundation Package</sup></span></span>

<span data-ttu-id="a178e-115">MRTK 基礎是由下列各項所組成：</span><span class="sxs-lookup"><span data-stu-id="a178e-115">The MRTK Foundation is comprised of:</span></span>

- <span data-ttu-id="a178e-116">**核心套件**</span><span class="sxs-lookup"><span data-stu-id="a178e-116">**Core Package**</span></span>

<span data-ttu-id="a178e-117">核心封裝包含所有其他元件使用的所有通用介面、類別和資料類型的定義。</span><span class="sxs-lookup"><span data-stu-id="a178e-117">The Core Package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="a178e-118">強烈建議應用程式透過定義的介面，以獨佔方式存取 MRTK 元件，以啟用跨平臺的最高層級相容性。</span><span class="sxs-lookup"><span data-stu-id="a178e-118">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

- <span data-ttu-id="a178e-119">**平臺提供者**</span><span class="sxs-lookup"><span data-stu-id="a178e-119">**Platform Providers**</span></span>

<span data-ttu-id="a178e-120">MRTK Platform Provider 套件是可讓 Mixed Reality 工具組以混合現實硬體和平臺功能為目標的元件。</span><span class="sxs-lookup"><span data-stu-id="a178e-120">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="a178e-121">支援的平臺包括：</span><span class="sxs-lookup"><span data-stu-id="a178e-121">Supported platforms include:</span></span>

- <span data-ttu-id="a178e-122">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a178e-122">Windows Mixed Reality</span></span>
- <span data-ttu-id="a178e-123">OpenVR</span><span class="sxs-lookup"><span data-stu-id="a178e-123">OpenVR</span></span>
- <span data-ttu-id="a178e-124">Windows 語音</span><span class="sxs-lookup"><span data-stu-id="a178e-124">Windows Voice</span></span>

- <span data-ttu-id="a178e-125">**系統服務**</span><span class="sxs-lookup"><span data-stu-id="a178e-125">**System Services**</span></span>

<span data-ttu-id="a178e-126">核心服務會為核心套件中定義的系統服務介面提供預設的執行方式。</span><span class="sxs-lookup"><span data-stu-id="a178e-126">Core services provide the default implementations for the system service interfaces, defined in the core package.</span></span>

<span data-ttu-id="a178e-127">MRTK foundation 包含下列系統服務：</span><span class="sxs-lookup"><span data-stu-id="a178e-127">The MRTK foundation includes the following system services:</span></span>

- [<span data-ttu-id="a178e-128">界限系統</span><span class="sxs-lookup"><span data-stu-id="a178e-128">Boundary System</span></span>](../features/Boundary/BoundarySystemGettingStarted.md)
- [<span data-ttu-id="a178e-129">診斷系統</span><span class="sxs-lookup"><span data-stu-id="a178e-129">Diagnostic System</span></span>](../features/Diagnostics/DiagnosticsSystemGettingStarted.md)
- [<span data-ttu-id="a178e-130">輸入系統</span><span class="sxs-lookup"><span data-stu-id="a178e-130">Input System</span></span>](../features/Input/Overview.md)
- [<span data-ttu-id="a178e-131">空間感知系統</span><span class="sxs-lookup"><span data-stu-id="a178e-131">Spatial Awareness System</span></span>](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md)
- [<span data-ttu-id="a178e-132">傳送系統</span><span class="sxs-lookup"><span data-stu-id="a178e-132">Teleport System</span></span>](../features/TeleportSystem/Overview.md)

- <span data-ttu-id="a178e-133">**功能資產**</span><span class="sxs-lookup"><span data-stu-id="a178e-133">**Feature Assets**</span></span>

<span data-ttu-id="a178e-134">功能資產是以 Unity 資產和腳本（包括使用者介面控制項、標準資產等等）提供的相關功能集合。</span><span class="sxs-lookup"><span data-stu-id="a178e-134">Feature Assets are collections of related functionality delivered as Unity assets and scripts including user interface controls, Standard assets, and more.</span></span>

## <a name="extensions-package"></a><span data-ttu-id="a178e-135">擴充功能套件</span><span class="sxs-lookup"><span data-stu-id="a178e-135">Extensions package</span></span>

<span data-ttu-id="a178e-136">擴充套件包含額外的服務和元件，可延伸基礎套件的功能。</span><span class="sxs-lookup"><span data-stu-id="a178e-136">The extensions package contains additional services and components that extend the functionality of the foundation package.</span></span>

- [<span data-ttu-id="a178e-137">場景轉換服務</span><span class="sxs-lookup"><span data-stu-id="a178e-137">Scene Transition Service</span></span>](../features/Extensions/SceneTransitionService/SceneTransitionServiceOverview.md)

## <a name="examples-package"></a><span data-ttu-id="a178e-138">範例套件</span><span class="sxs-lookup"><span data-stu-id="a178e-138">Examples package</span></span>

<span data-ttu-id="a178e-139">範例套件包含的示範、範例腳本，以及可在基礎套件中執行功能的範例幕後。</span><span class="sxs-lookup"><span data-stu-id="a178e-139">The examples package contains demos, sample scripts, and sample scenes that exercise functionality in the foundation package.</span></span> <span data-ttu-id="a178e-140">此套件包含 [HandInteractionExample 場景](../features/README_HandInteractionExamples.md) (如下圖所示) 其中包含的範例物件可回應各種類型的手寫輸入 (清楚說明的) 。</span><span class="sxs-lookup"><span data-stu-id="a178e-140">This package contains the [HandInteractionExample scene](../features/README_HandInteractionExamples.md) (pictured below) which contains sample objects that respond to various types of hand input (articulated and non-articulated).</span></span>

![HandInteractionExample 場景](../features/Images/MRTK_Examples.png)

<span data-ttu-id="a178e-142">此套件也包含眼睛追蹤示範，其 [記載于此處](../features/EyeTracking/EyeTracking_ExamplesOverview.md)</span><span class="sxs-lookup"><span data-stu-id="a178e-142">This package also contains eye tracking demos, which are [documented here](../features/EyeTracking/EyeTracking_ExamplesOverview.md)</span></span>

<span data-ttu-id="a178e-143">更常見的情況是，MRTK 中的任何新功能都應該包含範例套件中的對應範例，大致遵循相同的資料夾結構和位置。</span><span class="sxs-lookup"><span data-stu-id="a178e-143">More generally, any new feature in the MRTK should contain a corresponding example in the examples package, roughly following the same folder structure and location.</span></span>

## <a name="tools-package"></a><span data-ttu-id="a178e-144">工具套件</span><span class="sxs-lookup"><span data-stu-id="a178e-144">Tools package</span></span>

<span data-ttu-id="a178e-145">工具套件包含的工具，可用於建立混合的現實體驗，而其程式碼最終不會隨附于應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="a178e-145">The tools package contains tools that are useful for creating mixed reality experiences whose code will ultimately not ship as part of an application.</span></span>

- [<span data-ttu-id="a178e-146">相依性視窗</span><span class="sxs-lookup"><span data-stu-id="a178e-146">Dependency Window</span></span>](../features/Tools/DependencyWindow.md)
- [<span data-ttu-id="a178e-147">延伸模組服務建立嚮導</span><span class="sxs-lookup"><span data-stu-id="a178e-147">Extension Service Creation Wizard</span></span>](../features/Tools/ExtensionServiceCreationWizard.md)
- [<span data-ttu-id="a178e-148">優化視窗</span><span class="sxs-lookup"><span data-stu-id="a178e-148">Optimize Window</span></span>](../features/Tools/OptimizeWindow.md)
- [<span data-ttu-id="a178e-149">螢幕擷取畫面公用程式</span><span class="sxs-lookup"><span data-stu-id="a178e-149">Screenshot Utility</span></span>](../features/Tools/ScreenshotUtility.md)

## <a name="see-also"></a><span data-ttu-id="a178e-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a178e-150">See also</span></span>

- [<span data-ttu-id="a178e-151">架構概觀</span><span class="sxs-lookup"><span data-stu-id="a178e-151">Architecture Overview</span></span>](../Architecture/Overview.md)
- [<span data-ttu-id="a178e-152">系統、延伸模組服務和資料提供者</span><span class="sxs-lookup"><span data-stu-id="a178e-152">Systems, Extension Services and Data Providers</span></span>](../Architecture/SystemsExtensionsProviders.md)
