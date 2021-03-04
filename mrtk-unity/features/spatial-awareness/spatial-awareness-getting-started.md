---
title: SpatialAwareness
description: 描述 MRTK 中的空間感知
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 7a27f5eb63150b2521ea3471f50c2bbdeb886d90
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780126"
---
# <a name="spatial-awareness"></a><span data-ttu-id="50413-104">空間感知</span><span class="sxs-lookup"><span data-stu-id="50413-104">Spatial Awareness</span></span>

![空間感知](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="50413-106">空間感知系統可在混合現實應用程式中提供真實世界的環境感知。</span><span class="sxs-lookup"><span data-stu-id="50413-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="50413-107">當您在 Microsoft HoloLens 上引進時，空間感知會提供網格的集合，代表環境的幾何，可在全像全像全球的互動互動。</span><span class="sxs-lookup"><span data-stu-id="50413-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="50413-108">目前，「混合現實」工具組不會隨附空間理解演算法，如同最初封裝在 HoloToolkit 中。</span><span class="sxs-lookup"><span data-stu-id="50413-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="50413-109">空間理解通常涉及轉換空間網格資料，以建立簡化和/或群組的網格資料，例如平面、牆壁、樓層、上限等。</span><span class="sxs-lookup"><span data-stu-id="50413-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="50413-110">開始使用</span><span class="sxs-lookup"><span data-stu-id="50413-110">Getting started</span></span>

<span data-ttu-id="50413-111">新增空間感知的支援需要混合現實工具組的兩個主要元件：空間感知系統和支援的平臺提供者。</span><span class="sxs-lookup"><span data-stu-id="50413-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="50413-112">[啟用](#enable-the-spatial-awareness-system) 空間感知系統</span><span class="sxs-lookup"><span data-stu-id="50413-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="50413-113">[註冊](#register-observers) 並 [設定](configuring-spatial-awareness-mesh-observer.md) 一或多個空間觀察者，以提供網格資料</span><span class="sxs-lookup"><span data-stu-id="50413-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="50413-114">[建立並部署](#build-and-deploy) 至支援空間感知的平臺</span><span class="sxs-lookup"><span data-stu-id="50413-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="50413-115">啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="50413-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="50413-116">空間感知系統是由 MixedRealityToolkit 物件 (或另一個 [服務註冊機構](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 元件) 所管理。</span><span class="sxs-lookup"><span data-stu-id="50413-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="50413-117">遵循下列步驟來啟用或停用 *MixedRealityToolkit* 設定檔中的 *空間感知系統*。</span><span class="sxs-lookup"><span data-stu-id="50413-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="50413-118">混合現實工具組隨附一些預設預先設定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="50413-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="50413-119">其中有些是預設啟用或停用空間感知系統。</span><span class="sxs-lookup"><span data-stu-id="50413-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="50413-120">此預先設定的目的（特別是在停用時），是為了避免計算和轉譯網格的視覺負擔。</span><span class="sxs-lookup"><span data-stu-id="50413-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="50413-121">設定檔</span><span class="sxs-lookup"><span data-stu-id="50413-121">Profile</span></span> | <span data-ttu-id="50413-122">預設啟用的系統</span><span class="sxs-lookup"><span data-stu-id="50413-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="50413-123">`DefaultHoloLens1ConfigurationProfile` (資產/MRTK/SDK/設定檔/HoloLens1) </span><span class="sxs-lookup"><span data-stu-id="50413-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="50413-124">否</span><span class="sxs-lookup"><span data-stu-id="50413-124">False</span></span> |
| <span data-ttu-id="50413-125">`DefaultHoloLens2ConfigurationProfile` (資產/MRTK/SDK/設定檔/HoloLens2) </span><span class="sxs-lookup"><span data-stu-id="50413-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="50413-126">否</span><span class="sxs-lookup"><span data-stu-id="50413-126">False</span></span> |
| <span data-ttu-id="50413-127">`DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔) </span><span class="sxs-lookup"><span data-stu-id="50413-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="50413-128">是</span><span class="sxs-lookup"><span data-stu-id="50413-128">True</span></span> |

1. <span data-ttu-id="50413-129">在場景階層中選取要在 [偵測器] 面板中開啟的 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="50413-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="50413-131">流覽至 *空間感知系統* 區段，並檢查 *啟用空間感知系統*</span><span class="sxs-lookup"><span data-stu-id="50413-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![啟用空間感知](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="50413-133">選取所需的空間感知系統執行類型。</span><span class="sxs-lookup"><span data-stu-id="50413-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="50413-134">[`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)是提供的預設值。</span><span class="sxs-lookup"><span data-stu-id="50413-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![選取空間感知系統的執行](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="50413-136">註冊觀察者</span><span class="sxs-lookup"><span data-stu-id="50413-136">Register observers</span></span>

<span data-ttu-id="50413-137">「混合現實」工具組中的服務可以有 [資料提供者服務](../../architecture/systems-extensions-providers.md) ，可使用平臺專屬的資料和實行控制項來補充主要服務。</span><span class="sxs-lookup"><span data-stu-id="50413-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="50413-138">其中一個範例是混合的現實輸入系統，具有 [多個資料提供者](../input/input-providers.md) ，可從各種平臺特定 api 取得控制器和其他相關的輸入資訊。</span><span class="sxs-lookup"><span data-stu-id="50413-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="50413-139">空間感知系統很類似，因為資料提供者會為系統提供真實世界的網格資料。</span><span class="sxs-lookup"><span data-stu-id="50413-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="50413-140">空間感知設定檔至少必須註冊一個空間觀察者。</span><span class="sxs-lookup"><span data-stu-id="50413-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="50413-141">空間觀察者通常是平臺特定的元件，可作為提供者，從特定平臺的端點呈現各種類型的網格資料 (例如</span><span class="sxs-lookup"><span data-stu-id="50413-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="50413-142">HoloLens) 。</span><span class="sxs-lookup"><span data-stu-id="50413-142">HoloLens).</span></span>

1. <span data-ttu-id="50413-143">開啟或展開 *空間感知系統設定檔*</span><span class="sxs-lookup"><span data-stu-id="50413-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![空間感知系統設定檔](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="50413-145">按一下 [ *新增空間觀察者]* 按鈕</span><span class="sxs-lookup"><span data-stu-id="50413-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="50413-146">選取所需的 *空間觀察者實類型*</span><span class="sxs-lookup"><span data-stu-id="50413-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![選取空間觀察者的執行](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="50413-148">視需要[修改觀察者的設定屬性](configuring-spatial-awareness-mesh-observer.md)</span><span class="sxs-lookup"><span data-stu-id="50413-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="50413-149">`DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔) 的使用者將會為使用類別的 Windows Mixed Reality 平臺預先設定空間感知系統 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 。</span><span class="sxs-lookup"><span data-stu-id="50413-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="50413-150">建置及部署</span><span class="sxs-lookup"><span data-stu-id="50413-150">Build and deploy</span></span>

<span data-ttu-id="50413-151">一旦空間感知系統設定為所需的觀察者 (s) ，就可以建立專案，並將其部署至目標平臺。</span><span class="sxs-lookup"><span data-stu-id="50413-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50413-152">如果以 Windows Mixed Reality 平臺為目標 (例如： HoloLens) ，請務必確定已啟用 [空間感知功能](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity) ，才能在裝置上使用空間感知系統。</span><span class="sxs-lookup"><span data-stu-id="50413-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="50413-153">某些平臺（包括 Microsoft HoloLens）提供從 Unity 內遠端執行的支援。</span><span class="sxs-lookup"><span data-stu-id="50413-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="50413-154">這項功能可讓您快速開發和測試，而不需要建立和部署步驟。</span><span class="sxs-lookup"><span data-stu-id="50413-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="50413-155">請務必使用在目標硬體和平臺上執行的應用程式建立和部署版本，進行最終的接受度測試。</span><span class="sxs-lookup"><span data-stu-id="50413-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="50413-156">下一步</span><span class="sxs-lookup"><span data-stu-id="50413-156">Next steps</span></span>

<span data-ttu-id="50413-157">遵循上述程式來啟用空間感知系統之後，就可以更詳細地設定和控制系統。</span><span class="sxs-lookup"><span data-stu-id="50413-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="50413-158">在偵測器中設定觀察者的資訊：</span><span class="sxs-lookup"><span data-stu-id="50413-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="50413-159">設定裝置使用的觀察者</span><span class="sxs-lookup"><span data-stu-id="50413-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="50413-160">為編輯器中的使用方式設定觀察者</span><span class="sxs-lookup"><span data-stu-id="50413-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="50413-161">透過程式碼控制和延伸觀察者的資訊：</span><span class="sxs-lookup"><span data-stu-id="50413-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="50413-162">透過程式碼設定觀察者</span><span class="sxs-lookup"><span data-stu-id="50413-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="50413-163">建立自訂觀察者</span><span class="sxs-lookup"><span data-stu-id="50413-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="50413-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50413-164">See also</span></span>

- [<span data-ttu-id="50413-165">空間感知 API 檔</span><span class="sxs-lookup"><span data-stu-id="50413-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="50413-166">空間對應總覽 WMR</span><span class="sxs-lookup"><span data-stu-id="50413-166">Spatial Mapping Overview WMR</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="50413-167">Unity WMR 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="50413-167">Spatial Mapping in Unity WMR</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity)
