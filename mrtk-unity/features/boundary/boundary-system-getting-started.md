---
title: BoundarySystemGettingStarted
description: MRTK 中界限系統的登陸頁面
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、界限系統、
ms.openlocfilehash: fabc9a6c02edeeedbba2628864c72445077b61fb
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780063"
---
# <a name="boundary-system"></a><span data-ttu-id="31f2c-104">界限系統</span><span class="sxs-lookup"><span data-stu-id="31f2c-104">Boundary system</span></span>

<span data-ttu-id="31f2c-105">界限系統提供在混合現實應用程式中視覺化虛擬實境界限元件的支援。</span><span class="sxs-lookup"><span data-stu-id="31f2c-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="31f2c-106">界限定義使用者可以在佩戴 VR 耳機時安全地四處移動的區域。</span><span class="sxs-lookup"><span data-stu-id="31f2c-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="31f2c-107">界限是混合現實體驗的重要元件，可協助使用者在佩戴 VR 耳機時避免看不見的障礙。</span><span class="sxs-lookup"><span data-stu-id="31f2c-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="31f2c-108">許多虛擬實境平臺會提供自動顯示，例如，當使用者或其控制器接近界限時，在虛擬世界上重迭的白色輪廓。</span><span class="sxs-lookup"><span data-stu-id="31f2c-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="31f2c-109">混合現實工具組的界限系統會擴充這項功能，讓您能夠顯示追蹤區域的大綱、地面平面，以及可用來提供其他資訊給使用者的其他功能。</span><span class="sxs-lookup"><span data-stu-id="31f2c-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="31f2c-110">開始使用</span><span class="sxs-lookup"><span data-stu-id="31f2c-110">Getting started</span></span>

<span data-ttu-id="31f2c-111">新增界限的支援需要混合現實工具組的兩個主要元件：界限系統和使用界限設定的虛擬實境平臺。</span><span class="sxs-lookup"><span data-stu-id="31f2c-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="31f2c-112">[啟用](#enable-boundary-system) 界限系統</span><span class="sxs-lookup"><span data-stu-id="31f2c-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="31f2c-113">[設定](#configure-boundary-visualization) 界限視覺效果</span><span class="sxs-lookup"><span data-stu-id="31f2c-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="31f2c-114">使用已設定的界限來[建立並部署](#build-and-deploy)到 VR 平臺</span><span class="sxs-lookup"><span data-stu-id="31f2c-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="31f2c-115">啟用界限系統</span><span class="sxs-lookup"><span data-stu-id="31f2c-115">Enable boundary system</span></span>

<span data-ttu-id="31f2c-116">界限系統由 MixedRealityToolkit 物件 (或另一個 [服務註冊機構](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 元件) 管理。</span><span class="sxs-lookup"><span data-stu-id="31f2c-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="31f2c-117">下列步驟假設使用 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="31f2c-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="31f2c-118">其他服務註冊機構所需的步驟可能會不同。</span><span class="sxs-lookup"><span data-stu-id="31f2c-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="31f2c-119">選取場景階層中的 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="31f2c-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="31f2c-121">將 [偵測器] 面板移至 [界限系統] 區段，然後勾選 [啟用]</span><span class="sxs-lookup"><span data-stu-id="31f2c-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![啟用界限系統](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="31f2c-123">選取界限系統執行。</span><span class="sxs-lookup"><span data-stu-id="31f2c-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="31f2c-124">MRTK 提供的預設類別實作為 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="31f2c-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![選取界限系統執行](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="31f2c-126">所有界限系統的執行都必須擴充 [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="31f2c-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="31f2c-127">設定界限視覺效果</span><span class="sxs-lookup"><span data-stu-id="31f2c-127">Configure boundary visualization</span></span>

<span data-ttu-id="31f2c-128">[界限系統會使用設定檔](configuring-boundary-visualization.md)來指定要顯示的界限元件，並設定其外觀。</span><span class="sxs-lookup"><span data-stu-id="31f2c-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![界限視覺效果選項](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="31f2c-130">預設設定檔、 `DefaultMixedRealityBoundaryVisualizationProfile` (資產/MRTK/SDK/設定檔) 的使用者將會將界限系統預先設定為顯示樓層平面、播放區域和追蹤的區域。</span><span class="sxs-lookup"><span data-stu-id="31f2c-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="31f2c-131">建置及部署</span><span class="sxs-lookup"><span data-stu-id="31f2c-131">Build and deploy</span></span>

<span data-ttu-id="31f2c-132">使用所需的視覺效果選項設定界限系統之後，就可以將專案部署至目標平臺。</span><span class="sxs-lookup"><span data-stu-id="31f2c-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="31f2c-133">Unity Play 模式可讓您在編輯器中進行已設定界限的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="31f2c-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="31f2c-134">這項功能可讓您快速開發和測試，而不需要建立和部署步驟。</span><span class="sxs-lookup"><span data-stu-id="31f2c-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="31f2c-135">請務必使用在目標硬體和平臺上執行的應用程式建立和部署版本，進行最終的接受度測試。</span><span class="sxs-lookup"><span data-stu-id="31f2c-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="31f2c-136">透過程式碼存取界限系統</span><span class="sxs-lookup"><span data-stu-id="31f2c-136">Accessing boundary system via code</span></span>

<span data-ttu-id="31f2c-137">如果啟用並設定，則可以透過 CoreServices 靜態協助程式類別來存取界限系統。</span><span class="sxs-lookup"><span data-stu-id="31f2c-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="31f2c-138">然後，您可以使用該參考動態變更界限參數，並存取系統所管理的相關 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="31f2c-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="31f2c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31f2c-139">See also</span></span>

- [<span data-ttu-id="31f2c-140">界限 API 檔</span><span class="sxs-lookup"><span data-stu-id="31f2c-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="31f2c-141">設定界限視覺效果</span><span class="sxs-lookup"><span data-stu-id="31f2c-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
