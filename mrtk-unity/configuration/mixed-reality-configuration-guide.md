---
title: MixedRealityConfigurationGuide
description: 將 MRTK 設定為 unity 的檔。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 9b4db83af7236c78978cf329ebdf96d49c50afa6
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236999"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="cfbf4-104">混合現實工具組設定檔設定指南</span><span class="sxs-lookup"><span data-stu-id="cfbf4-104">Mixed Reality Toolkit profile configuration guide</span></span>

![MRTK 標誌](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="cfbf4-106">「混合現實」工具組盡可能集中管理工具組所需的設定， (除了真正的「事物」 ) 。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="cfbf4-107">本指南是針對工具組目前可用的每個設定設定檔畫面的簡單逐步解說。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="cfbf4-108">主要混合現實工具組設定檔</span><span class="sxs-lookup"><span data-stu-id="cfbf4-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="cfbf4-109">主要設定檔（附加至您場景中的 *MixedRealityToolkit* GameObject）會提供專案中工具組的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="cfbf4-110">Mixed Reality 工具組會「鎖定」預設設定畫面，以確保您的專案一律會有一個共同的起點，而且建議您在專案發展時開始定義自己的設定。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="cfbf4-111">在播放模式中，無法編輯 MRTK 設定。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-111">The MRTK configuration is not editable during play-mode.</span></span>

![MRTK 設定檔](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="cfbf4-113">「混合現實」工具組的所有「預設」設定檔都可以在 [資產/MRTK/SDK/設定檔] 的 SDK 專案中找到。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cfbf4-114">DefaultHoloLens2ConfigurationProfile 已針對 HoloLens 2 優化。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="cfbf4-115">請參閱 [設定檔](../features/profiles/profiles.md) 以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-115">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="cfbf4-116">當您開啟主要混合現實工具組設定檔時，您會在偵測器中看到下列畫面：</span><span class="sxs-lookup"><span data-stu-id="cfbf4-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="cfbf4-117">如果您選取場景中沒有 MixedRealityToolkit 的 MixedRealityToolkitConfigurationProfile 資產，則會詢問您是否要讓 MRTK 為您自動設定場景。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="cfbf4-118">這是選擇性的，不過，場景中必須有作用中的 MixedRealityToolkit 物件，才能存取所有設定畫面。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="cfbf4-119">這會裝載專案目前的使用中執行時間設定。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="cfbf4-120">您可以從這裡流覽至 MRTK 的所有設定設定檔，包括：</span><span class="sxs-lookup"><span data-stu-id="cfbf4-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="cfbf4-121">混合現實工具組設定檔設定指南</span><span class="sxs-lookup"><span data-stu-id="cfbf4-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="cfbf4-122">主要混合現實工具組設定檔</span><span class="sxs-lookup"><span data-stu-id="cfbf4-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="cfbf4-123">體驗設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="cfbf4-124">攝影機設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="cfbf4-125">輸入系統設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="cfbf4-126">界限視覺效果設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="cfbf4-127">遙傳系統選擇</span><span class="sxs-lookup"><span data-stu-id="cfbf4-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="cfbf4-128">空間感知設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="cfbf4-129">診斷設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="cfbf4-130">場景系統設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="cfbf4-131">其他服務設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="cfbf4-132">輸入動作設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="cfbf4-133">輸入動作規則</span><span class="sxs-lookup"><span data-stu-id="cfbf4-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="cfbf4-134">指標設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="cfbf4-135">手勢設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="cfbf4-136">語音命令</span><span class="sxs-lookup"><span data-stu-id="cfbf4-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="cfbf4-137">控制器對應設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="cfbf4-138">控制器視覺效果設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="cfbf4-139">編輯器公用程式</span><span class="sxs-lookup"><span data-stu-id="cfbf4-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="cfbf4-140">服務偵測器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="cfbf4-141">深度緩衝區轉譯器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="cfbf4-142">在執行時間變更設定檔</span><span class="sxs-lookup"><span data-stu-id="cfbf4-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="cfbf4-143">預先 MRTK 初始化設定檔參數</span><span class="sxs-lookup"><span data-stu-id="cfbf4-143">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="cfbf4-144">主動設定檔參數</span><span class="sxs-lookup"><span data-stu-id="cfbf4-144">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="cfbf4-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfbf4-145">See also</span></span>](#see-also)

<span data-ttu-id="cfbf4-146">這些設定檔的詳細資訊如下：</span><span class="sxs-lookup"><span data-stu-id="cfbf4-146">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="cfbf4-147">體驗設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-147">Experience settings</span></span>

<span data-ttu-id="cfbf4-148">在 [主要混合現實工具組設定] 頁面上，此設定會定義您專案的 [混合現實環境規模](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity) 的預設操作。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-148">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="cfbf4-149">攝影機設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-149">Camera settings</span></span>

<span data-ttu-id="cfbf4-150">攝影機設定會定義如何為您的混合現實專案設定相機，定義一般剪輯、品質和透明度設定。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-150">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="cfbf4-151">輸入系統設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-151">Input system settings</span></span>

<span data-ttu-id="cfbf4-152">Mixed Reality 專案提供健全且妥善定型的輸入系統，以路由傳送預設選取之專案周圍的所有輸入事件。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-152">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="cfbf4-153">在 MRTK 所提供的輸入系統背後有數個其他系統，這些系統可協助您推動和管理複雜的 weavings，以抽象化多平臺/混合現實架構的複雜度。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-153">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="cfbf4-154">每個個別設定檔詳述如下：</span><span class="sxs-lookup"><span data-stu-id="cfbf4-154">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="cfbf4-155">焦點設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-155">Focus Settings</span></span>
- [<span data-ttu-id="cfbf4-156">輸入動作設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-156">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="cfbf4-157">輸入動作規則</span><span class="sxs-lookup"><span data-stu-id="cfbf4-157">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="cfbf4-158">指標設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-158">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="cfbf4-159">手勢設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-159">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="cfbf4-160">語音命令</span><span class="sxs-lookup"><span data-stu-id="cfbf4-160">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="cfbf4-161">控制器對應設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-161">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="cfbf4-162">控制器視覺效果設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-162">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="cfbf4-163">界限視覺效果設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-163">Boundary visualization settings</span></span>

<span data-ttu-id="cfbf4-164">界限系統會轉譯基礎平臺界限/守護者系統所報告的認知界限。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-164">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="cfbf4-165">界限視覺化設定可讓您在相對於使用者位置的場景中，自動顯示記錄的界限。界限也會根據使用者在場景中 teleports 的位置做出反應/更新。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-165">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="cfbf4-166">遙傳系統選擇</span><span class="sxs-lookup"><span data-stu-id="cfbf4-166">Teleportation system selection</span></span>

<span data-ttu-id="cfbf4-167">Mixed Reality 專案提供一個功能完整的遙傳系統，可用於管理專案中依預設選取的遙傳事件。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-167">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="cfbf4-168">空間感知設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-168">Spatial awareness settings</span></span>

<span data-ttu-id="cfbf4-169">Mixed Reality 專案提供重建的空間感知系統，以便在預設選取的專案中使用空間掃描系統。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-169">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="cfbf4-170">混合現實工具組空間感知設定可讓您自訂系統啟動的方式，不論是在應用程式以程式設計方式啟動或稍後以程式設計的方式，以及設定視野的範圍。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="cfbf4-171">它也可讓您設定網格和介面設定，進一步自訂您的專案如何理解您的環境。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="cfbf4-172">這僅適用于可提供掃描環境的裝置。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="cfbf4-173">診斷設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-173">Diagnostics settings</span></span>

<span data-ttu-id="cfbf4-174">MRTK 的選擇性但非常實用的功能是外掛程式診斷功能。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="cfbf4-175">診斷設定檔提供數個簡單的系統，讓您在專案執行時進行監視，包括方便的開啟/關閉參數，以啟用/停用場景中的顯示面板。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="cfbf4-176">場景系統設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-176">Scene system settings</span></span>

<span data-ttu-id="cfbf4-177">MRTK 會提供此選用服務，協助您管理複雜的加法場景載入/卸載。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="cfbf4-178">若要判斷場景系統是否適合您的專案，請閱讀「 [場景系統入門指南」。](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="cfbf4-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="cfbf4-179">其他服務設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-179">Additional services settings</span></span>

<span data-ttu-id="cfbf4-180">混合現實工具組的其中一個更先進區域是其 [服務定位器模式](https://en.wikipedia.org/wiki/Service_locator_pattern) 的執行，可讓您向架構註冊任何「服務」。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="cfbf4-181">這可讓您輕鬆地以新的功能/系統擴充架構，但也可讓專案利用這些功能來註冊自己的執行時間元件。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="cfbf4-182">任何已註冊的服務仍會獲得所有 Unity 事件的完整優點，而不會有執行 MonoBehaviour 或相當笨拙單一模式的額外負荷和成本。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="cfbf4-183">這可讓單純的 c # 元件執行前景和背景進程（例如，產生系統、執行時間遊戲邏輯或幾乎任何其他作業），而不會有場景額外負荷。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="cfbf4-184">輸入動作設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-184">Input actions settings</span></span>

<span data-ttu-id="cfbf4-185">輸入動作提供一種方法，可從執行時間專案中抽象化任何實體互動和輸入。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="cfbf4-186">控制器/手/滑鼠/等) 的所有實體輸入 (都會轉譯成邏輯輸入動作，以便在執行時間專案中使用。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="cfbf4-187">無論輸入的位置為何，您的專案都只會在您的場景中將這些動作實作為「要做的事」或「互動」。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="cfbf4-188">若要建立新的輸入動作，只需按一下 [新增動作] 按鈕，然後為其代表的內容輸入易記的文字名稱。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="cfbf4-189">然後，您只需要選取一個座標軸， (動作要傳達的資料類型) ，或在實體控制器的情況下，可以附加的實體輸入類型，例如：</span><span class="sxs-lookup"><span data-stu-id="cfbf4-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="cfbf4-190">軸條件約束</span><span class="sxs-lookup"><span data-stu-id="cfbf4-190">Axis Constraint</span></span> | <span data-ttu-id="cfbf4-191">資料類型</span><span class="sxs-lookup"><span data-stu-id="cfbf4-191">Data Type</span></span> | <span data-ttu-id="cfbf4-192">描述</span><span class="sxs-lookup"><span data-stu-id="cfbf4-192">Description</span></span> | <span data-ttu-id="cfbf4-193">範例用法</span><span class="sxs-lookup"><span data-stu-id="cfbf4-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="cfbf4-194">無</span><span class="sxs-lookup"><span data-stu-id="cfbf4-194">None</span></span> | <span data-ttu-id="cfbf4-195">無資料</span><span class="sxs-lookup"><span data-stu-id="cfbf4-195">No data</span></span> | <span data-ttu-id="cfbf4-196">用於空的動作或事件</span><span class="sxs-lookup"><span data-stu-id="cfbf4-196">Used for an empty action or event</span></span> | <span data-ttu-id="cfbf4-197">事件觸發程式</span><span class="sxs-lookup"><span data-stu-id="cfbf4-197">Event Trigger</span></span> |
| <span data-ttu-id="cfbf4-198">原始 (保留) </span><span class="sxs-lookup"><span data-stu-id="cfbf4-198">Raw (reserved)</span></span> | <span data-ttu-id="cfbf4-199">物件 (object)</span><span class="sxs-lookup"><span data-stu-id="cfbf4-199">object</span></span> | <span data-ttu-id="cfbf4-200">保留供日後使用</span><span class="sxs-lookup"><span data-stu-id="cfbf4-200">Reserved for future use</span></span> | <span data-ttu-id="cfbf4-201">N/A</span><span class="sxs-lookup"><span data-stu-id="cfbf4-201">N/A</span></span> |
| <span data-ttu-id="cfbf4-202">Digital</span><span class="sxs-lookup"><span data-stu-id="cfbf4-202">Digital</span></span> | <span data-ttu-id="cfbf4-203">bool</span><span class="sxs-lookup"><span data-stu-id="cfbf4-203">bool</span></span> | <span data-ttu-id="cfbf4-204">布林值 on 或 off 型別資料</span><span class="sxs-lookup"><span data-stu-id="cfbf4-204">A boolean on or off type data</span></span> | <span data-ttu-id="cfbf4-205">控制器按鈕</span><span class="sxs-lookup"><span data-stu-id="cfbf4-205">A controller button</span></span> |
| <span data-ttu-id="cfbf4-206">單一軸</span><span class="sxs-lookup"><span data-stu-id="cfbf4-206">Single Axis</span></span> | <span data-ttu-id="cfbf4-207">FLOAT</span><span class="sxs-lookup"><span data-stu-id="cfbf4-207">float</span></span> | <span data-ttu-id="cfbf4-208">單一精確度資料值</span><span class="sxs-lookup"><span data-stu-id="cfbf4-208">A single precision data value</span></span> | <span data-ttu-id="cfbf4-209">範圍輸入，例如觸發程式</span><span class="sxs-lookup"><span data-stu-id="cfbf4-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="cfbf4-210">雙軸</span><span class="sxs-lookup"><span data-stu-id="cfbf4-210">Dual Axis</span></span> | <span data-ttu-id="cfbf4-211">Vector2</span><span class="sxs-lookup"><span data-stu-id="cfbf4-211">Vector2</span></span> | <span data-ttu-id="cfbf4-212">多軸的雙重 float 類型日期</span><span class="sxs-lookup"><span data-stu-id="cfbf4-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="cfbf4-213">Dpad 或操縱杆</span><span class="sxs-lookup"><span data-stu-id="cfbf4-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="cfbf4-214">三個 Dof 位置</span><span class="sxs-lookup"><span data-stu-id="cfbf4-214">Three Dof Position</span></span> | <span data-ttu-id="cfbf4-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="cfbf4-215">Vector3</span></span> | <span data-ttu-id="cfbf4-216">具有3個 float 軸的位置型別資料</span><span class="sxs-lookup"><span data-stu-id="cfbf4-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="cfbf4-217">僅限3D 位置樣式控制器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-217">3D position style only controller</span></span> |
| <span data-ttu-id="cfbf4-218">三個 Dof 旋轉</span><span class="sxs-lookup"><span data-stu-id="cfbf4-218">Three Dof Rotation</span></span> | <span data-ttu-id="cfbf4-219">四元數</span><span class="sxs-lookup"><span data-stu-id="cfbf4-219">Quaternion</span></span> | <span data-ttu-id="cfbf4-220">只旋轉具有4個 float 軸的輸入</span><span class="sxs-lookup"><span data-stu-id="cfbf4-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="cfbf4-221">三度樣式的控制器，例如 Oculus Go 控制器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="cfbf4-222">六 Dof</span><span class="sxs-lookup"><span data-stu-id="cfbf4-222">Six Dof</span></span> | <span data-ttu-id="cfbf4-223">Mixed 事實會造成 (Vector3，四元數) </span><span class="sxs-lookup"><span data-stu-id="cfbf4-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="cfbf4-224">具有 Vector3 和四元陣列件的位置和旋轉樣式輸入</span><span class="sxs-lookup"><span data-stu-id="cfbf4-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="cfbf4-225">移動控制器或指標</span><span class="sxs-lookup"><span data-stu-id="cfbf4-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="cfbf4-226">使用輸入動作的事件不限於實體控制器，而且仍可在專案中使用，讓執行時間效果產生新的動作。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="cfbf4-227">輸入動作是在執行時間無法編輯的幾個元件之一，它們只是設計階段的設定。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="cfbf4-228">當專案因為架構 (而執行時，不應該將此設定檔交換，而您的專案) 相依于每個動作所產生的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="cfbf4-229">輸入動作規則</span><span class="sxs-lookup"><span data-stu-id="cfbf4-229">Input actions rules</span></span>

<span data-ttu-id="cfbf4-230">輸入動作規則可讓您根據其資料值，自動將一個輸入動作所引發的事件轉譯成不同的動作。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="cfbf4-231">這些都是在架構內無縫管理的，而且不會產生任何效能成本。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="cfbf4-232">例如，將單一雙重軸輸入事件從 DPad 中轉換為4對應的 "Dpad Up"/"DPad Down"/"Dpad Left"/"Dpad Right" 動作 (如下圖所示) 。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="cfbf4-233">這也可以在您自己的程式碼中完成。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-233">This could also be done in your own code.</span></span> <span data-ttu-id="cfbf4-234">不過，因為這是一種非常常見的模式，架構會提供一種機制來執行這項「現成」</span><span class="sxs-lookup"><span data-stu-id="cfbf4-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="cfbf4-235">您可以針對任何可用的輸入軸設定輸入動作規則。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="cfbf4-236">不過，您可以將一個軸類型的輸入動作轉譯為相同座標軸類型的另一個輸入動作。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="cfbf4-237">您可以將雙重軸動作對應至另一個雙重軸動作，而不是數位或無動作。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![輸入動作規則設定檔](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="cfbf4-239">指標設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-239">Pointer configuration</span></span>

<span data-ttu-id="cfbf4-240">指標是用來從任何輸入裝置驅動場景中的互動性，同時提供方向和點擊測試與場景 (中已附加碰撞器的任何物件，或是) 的 UI 元件。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="cfbf4-241">預設會自動為控制器、耳機 (注視/焦點) 和滑鼠/觸控輸入設定指標。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="cfbf4-242">指標也可以在作用中場景內視覺化，方法是使用混合現實工具組所提供的許多線條元件之一，或者，如果它們執行 MRTK IMixedRealityPointer 介面，則為您自己的介面。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="cfbf4-243">指向範圍：決定所有指標的全域指向範圍，包括注視。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="cfbf4-244">指向 Raycast 圖層遮罩：決定將 Raycast 的圖層指標。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="cfbf4-245">Debug Draw 指標放射：用來視覺化 raycasting 所使用之光線的 debug helper。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="cfbf4-246">偵錯工具繪製指向放射片色彩：用來視覺化的一組色彩。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="cfbf4-247">注視游標預製專案：可讓您輕鬆地指定任何場景的全球注視游標。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="cfbf4-248">還有另一個協助程式按鈕，可快速跳至注視提供者，視需要覆寫一些特定的值。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="cfbf4-249">手勢設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-249">Gestures configuration</span></span>

<span data-ttu-id="cfbf4-250">手勢是系統特定的執行，可讓您將輸入動作指派給各種 Sdk 所提供的各種「手勢」輸入方法 (例如 HoloLens) 。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="cfbf4-251">目前的手勢實作為僅適用于 HoloLens，並且將在未來新增至工具組的其他系統中增強， (沒有任何日期) 。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="cfbf4-252">語音命令</span><span class="sxs-lookup"><span data-stu-id="cfbf4-252">Speech commands</span></span>

<span data-ttu-id="cfbf4-253">就像手勢一樣，某些執行時間平臺也提供智慧型的「語音轉換文字」功能，讓您能夠產生可由 Unity 專案接收的命令。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="cfbf4-254">此設定檔可讓您設定下列各項：</span><span class="sxs-lookup"><span data-stu-id="cfbf4-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="cfbf4-255">一般設定-設為自動啟動或手動啟動的 [啟動行為] 決定是否要在輸入系統啟動時初始化 KeywordRecognizer，或讓專案決定何時要初始化 KeywordRecognizer。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="cfbf4-256">「辨識信賴等級」用來初始化 Unity 的 [KEYWORDRECOGNIZER API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span><span class="sxs-lookup"><span data-stu-id="cfbf4-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="cfbf4-257">語音命令-註冊「單字」，並將其轉譯成可由您的專案接收的輸入動作。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="cfbf4-258">如有需要，也可以附加至鍵盤動作。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cfbf4-259">系統目前只支援在 Windows 10 平臺（例如 HoloLens 和 Windows 10 desktop）上執行時的語音，並將在未來新增至 MRTK 的其他系統進行增強， (沒有任何日期) 。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="cfbf4-260">控制器對應設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-260">Controller mapping configuration</span></span>

<span data-ttu-id="cfbf4-261">混合現實工具組的其中一個核心設定畫面是能夠設定和對應可供專案使用的各種控制器類型。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="cfbf4-262">下方的 [設定] 畫面可讓您設定工具組目前所辨識的任何控制器。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="cfbf4-263">MRTK 會提供下列控制器/系統的預設設定：</span><span class="sxs-lookup"><span data-stu-id="cfbf4-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="cfbf4-264">滑鼠 (包括3D 空間滑鼠支援) </span><span class="sxs-lookup"><span data-stu-id="cfbf4-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="cfbf4-265">觸控式螢幕</span><span class="sxs-lookup"><span data-stu-id="cfbf4-265">Touch Screen</span></span>
- <span data-ttu-id="cfbf4-266">Xbox 控制器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-266">Xbox controllers</span></span>
- <span data-ttu-id="cfbf4-267">Windows Mixed Reality 控制器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="cfbf4-268">HoloLens 手勢</span><span class="sxs-lookup"><span data-stu-id="cfbf4-268">HoloLens Gestures</span></span>
- <span data-ttu-id="cfbf4-269">HTC Vive 杆控制器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="cfbf4-270">Oculus 觸控控制器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="cfbf4-271">Oculus 遠端控制器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-271">Oculus Remote controller</span></span>
- <span data-ttu-id="cfbf4-272">一般 OpenVR 裝置只 (advanced 使用者) </span><span class="sxs-lookup"><span data-stu-id="cfbf4-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="cfbf4-273">按一下任何預先建立之控制器系統的映射，可讓您為其所有對應的輸入設定單一輸入動作，例如，請參閱下方的 Oculus Touch controller 設定畫面：</span><span class="sxs-lookup"><span data-stu-id="cfbf4-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="cfbf4-274">另外還有一個可設定其他 OpenVR 或 Unity 輸入控制器（未在上方識別）的 advanced 畫面。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="cfbf4-275">控制器視覺效果設定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-275">Controller visualization settings</span></span>

<span data-ttu-id="cfbf4-276">除了控制器對應之外，還會提供個別的設定檔來自訂您的控制器在幕後的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="cfbf4-277">這可以設定在「全域」 (特定手) 或個別控制器類型/手特定的控制器實例。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="cfbf4-278">MRTK 也支援適用于 Windows Mixed Reality 和 OpenVR 的原生 SDK 控制器模型。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="cfbf4-279">這些會以 Gameobject 的形式載入場景，並使用平臺的控制器追蹤來定位。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="cfbf4-280">如果場景中的控制器表示需要從實體控制器位置位移，則只要針對控制器模型的預製專案設定該位移 (例如，將控制器預製專案的轉換位置設定為位移位置) 。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="cfbf4-281">編輯器公用程式</span><span class="sxs-lookup"><span data-stu-id="cfbf4-281">Editor utilities</span></span>

<span data-ttu-id="cfbf4-282">下列公用程式只適用于編輯器，而且有助於改善開發生產力。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![MRTK 編輯器設定公用程式](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="cfbf4-284">服務偵測器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-284">Service inspectors</span></span>

<span data-ttu-id="cfbf4-285">服務偵測器是一種僅限編輯器的功能，可產生代表作用中服務的場景物件。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="cfbf4-286">選取這些物件會顯示提供檔連結的偵測器、控制編輯器視覺效果，以及深入瞭解服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="cfbf4-287">您可以勾選設定設定檔中的 [*編輯器設定*] 下的 [*使用服務* 偵測器]，以啟用服務偵測器。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="cfbf4-288">深度緩衝區轉譯器</span><span class="sxs-lookup"><span data-stu-id="cfbf4-288">Depth buffer renderer</span></span>

<span data-ttu-id="cfbf4-289">與一些混合的現實平臺共用深度緩衝區可以改善全像 [影像的穩定](../performance/hologram-stabilization.md)。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="cfbf4-290">例如，Windows Mixed Reality 平臺可以修改每圖元轉譯的場景，以在轉譯框架所需的時間內進行微妙的移動。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="cfbf4-291">不過，這些技術需要具有精確資料的深度緩衝區，以瞭解幾何與使用者之間的位置和距離。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="cfbf4-292">為了確保場景會將所有必要的資料轉譯至深度緩衝區，開發人員可以在設定檔中的 *編輯器設定* 下切換轉譯 *深度緩衝區* 功能。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="cfbf4-293">這將會採用目前的深度緩衝區，並藉由將後置處理效果套用 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) 至主要攝影機，將其轉譯為場景視圖的色彩。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="cfbf4-294">![轉譯深度緩衝區公用程式 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>場景中的藍色圓柱具有 ZWrite 關閉的材質，因此未寫入任何深度資料</sup></span><span class="sxs-lookup"><span data-stu-id="cfbf4-294">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="cfbf4-295">在執行時間變更設定檔</span><span class="sxs-lookup"><span data-stu-id="cfbf4-295">Changing profiles at runtime</span></span>

<span data-ttu-id="cfbf4-296">您可以在執行時間更新設定檔，而且在這種情況下，通常有兩個不同的案例和時間會有説明：</span><span class="sxs-lookup"><span data-stu-id="cfbf4-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="cfbf4-297">**預先 MRTK 的初始化設定檔參數**：啟動時，在 MRTK 初始化且設定檔變成作用中之前，請取代尚未使用的設定檔，以根據裝置功能啟用/停用不同的功能。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-297">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="cfbf4-298">例如，如果在 VR 中執行的體驗沒有空間對應硬體，則啟用空間對應元件可能並不合理。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="cfbf4-299">使用中 **設定檔參數**：啟動後，在 MRTK 初始化且設定檔變成作用中之後，請將目前使用中的設定檔交換，以變更特定功能的行為方式。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-299">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="cfbf4-300">例如，在應用程式中，可能會有想要完全移除的手指標的特定子體驗。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="cfbf4-301">預先 MRTK 初始化設定檔參數</span><span class="sxs-lookup"><span data-stu-id="cfbf4-301">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="cfbf4-302">若要完成這項作業，請將 MonoBehaviour (範例附加在 MRTK 初始化之前執行的) ， (也就是喚醒 () ) 。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-302">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="cfbf4-303">請注意，腳本 (例如，呼叫 `SetProfileBeforeInitialization`) 必須比腳本早執行 `MixedRealityToolkit` ，這可以藉由設定 [腳本執行順序設定](https://docs.unity3d.com/Manual/class-MonoManager.html)來達成。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-303">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

<span data-ttu-id="cfbf4-304">不是 "profileToUse"，您可以有一組適用于特定平臺的任意設定檔 (例如，一個適用于 HoloLens 1、一個用於 VR、一個適用于 HoloLens 2 等) 。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-304">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="cfbf4-305">您可以使用各種其他指標 (例如 https://docs.unity3d.com/ScriptReference/SystemInfo.html ，或是攝影機是否為不透明/透明) ，以找出要載入的設定檔。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-305">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="cfbf4-306">主動設定檔參數</span><span class="sxs-lookup"><span data-stu-id="cfbf4-306">Active profile switch</span></span>

<span data-ttu-id="cfbf4-307">這可以藉由將屬性設定 `MixedRealityToolkit.Instance.ActiveProfile` 為取代使用中設定檔的新設定檔來完成。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-307">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="cfbf4-308">注意：在執行時間期間進行設定時 `ActiveProfile` ，在所有服務的最後一個 LateUpdate () 之後，將會發生目前正在執行之服務的終結，以及與新設定檔相關聯之服務的具現化和初始化，將在所有服務的第一次更新 () 之前發生。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-308">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="cfbf4-309">在此程式期間，可能會發生明顯的應用程式 hesitation。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-309">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="cfbf4-310">此外，任何優先順序高於腳本的腳本 `MixedRealityToolkit` 都可以先輸入更新，然後才能正確設定新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-310">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="cfbf4-311">如需腳本優先順序的詳細資訊，請參閱 [腳本執行順序設定](https://docs.unity3d.com/Manual/class-MonoManager.html) 。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-311">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="cfbf4-312">在設定檔切換程式中，現有的 UI 相機將保持不變，以確保需要 canvas 的 Unity UI 元件在切換之後仍能運作。</span><span class="sxs-lookup"><span data-stu-id="cfbf4-312">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfbf4-313">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfbf4-313">See also</span></span>

- [<span data-ttu-id="cfbf4-314">全像穩定</span><span class="sxs-lookup"><span data-stu-id="cfbf4-314">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)
