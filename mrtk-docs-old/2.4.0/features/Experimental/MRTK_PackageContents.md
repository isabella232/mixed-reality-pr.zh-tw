---
title: MRTK_PakageContents
description: 與 MRTK 和 XR SDK 相關的套件。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 28b6766eefbd782a232e5738b80095032c662e0b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780715"
---
# <a name="mixed-reality-toolkit-packages"></a><span data-ttu-id="4cb71-104">混合現實工具組套件</span><span class="sxs-lookup"><span data-stu-id="4cb71-104">Mixed Reality Toolkit packages</span></span>

<span data-ttu-id="4cb71-105">Microsoft Mixed Reality 工具組是以套件集合的形式提供。</span><span class="sxs-lookup"><span data-stu-id="4cb71-105">The Microsoft Mixed Reality Toolkit is provided as a collection of packages.</span></span> <span data-ttu-id="4cb71-106">下列各節將說明這些封裝的內容。</span><span class="sxs-lookup"><span data-stu-id="4cb71-106">The contents of these packages is described in the following sections.</span></span>

- [<span data-ttu-id="4cb71-107">基礎</span><span class="sxs-lookup"><span data-stu-id="4cb71-107">Foundation</span></span>](#foundation)
- [<span data-ttu-id="4cb71-108">擴充功能</span><span class="sxs-lookup"><span data-stu-id="4cb71-108">Extensions</span></span>](#extensions)
- [<span data-ttu-id="4cb71-109">工具</span><span class="sxs-lookup"><span data-stu-id="4cb71-109">Tools</span></span>](#tools)
- [<span data-ttu-id="4cb71-110">範例</span><span class="sxs-lookup"><span data-stu-id="4cb71-110">Examples</span></span>](#examples)

## <a name="foundation"></a><span data-ttu-id="4cb71-111">Foundation</span><span class="sxs-lookup"><span data-stu-id="4cb71-111">Foundation</span></span>

<span data-ttu-id="4cb71-112">MixedRealityToolkit 套件包含建立混合現實應用程式所需的核心元件。</span><span class="sxs-lookup"><span data-stu-id="4cb71-112">The Microsoft.MixedRealityToolkit.Unity.Foundation package includes the core components required to create a mixed reality application.</span></span>

| <span data-ttu-id="4cb71-113">資料夾</span><span class="sxs-lookup"><span data-stu-id="4cb71-113">Folder</span></span> | <span data-ttu-id="4cb71-114">元件</span><span class="sxs-lookup"><span data-stu-id="4cb71-114">Component</span></span> | <span data-ttu-id="4cb71-115">描述</span><span class="sxs-lookup"><span data-stu-id="4cb71-115">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="4cb71-116">MRTK/核心</span><span class="sxs-lookup"><span data-stu-id="4cb71-116">MRTK/Core</span></span> | | <span data-ttu-id="4cb71-117">介面和類型定義、基類、標準著色器。</span><span class="sxs-lookup"><span data-stu-id="4cb71-117">Interface and type definitions, base classes, standard shader.</span></span> |
| <span data-ttu-id="4cb71-118">MRTK/提供者</span><span class="sxs-lookup"><span data-stu-id="4cb71-118">MRTK/Providers</span></span> | | |
| | [<span data-ttu-id="4cb71-119">ObjectMeshObserver</span><span class="sxs-lookup"><span data-stu-id="4cb71-119">ObjectMeshObserver</span></span>](../features/SpatialAwareness/SpatialObjectMeshObserver.md) | <span data-ttu-id="4cb71-120">空間感知觀察者使用3D 模型做為資料。</span><span class="sxs-lookup"><span data-stu-id="4cb71-120">Spatial awareness observer using a 3D model as the data.</span></span> |
| | <span data-ttu-id="4cb71-121">OpenVR</span><span class="sxs-lookup"><span data-stu-id="4cb71-121">OpenVR</span></span> | <span data-ttu-id="4cb71-122">OpenVR 裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="4cb71-122">Support for OpenVR devices.</span></span> |
| | [<span data-ttu-id="4cb71-123">UnityAR</span><span class="sxs-lookup"><span data-stu-id="4cb71-123">UnityAR</span></span>](../features/CameraSystem/UnityArCameraSettings.md) | <span data-ttu-id="4cb71-124"> (實驗性) 攝影機設定提供者，讓 MRTK 與行動 AR 裝置搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4cb71-124">(Experimental) Camera settings provider enabling MRTK use with mobile AR devices.</span></span> |
| | <span data-ttu-id="4cb71-125">WindowsMixedReality</span><span class="sxs-lookup"><span data-stu-id="4cb71-125">WindowsMixedReality</span></span> | <span data-ttu-id="4cb71-126">Windows Mixed Reality 裝置的支援，包括 Microsoft HoloLens 和沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="4cb71-126">Support for Windows Mixed Reality devices, including Microsoft HoloLens and immersive headsets.</span></span> |
| | <span data-ttu-id="4cb71-127">WindowsVoiceInput</span><span class="sxs-lookup"><span data-stu-id="4cb71-127">WindowsVoiceInput</span></span> | <span data-ttu-id="4cb71-128">支援 Microsoft Windows 平臺上的語音和聽寫。</span><span class="sxs-lookup"><span data-stu-id="4cb71-128">Support for speech and dictation on Microsoft Windows platforms.</span></span> |
| | <span data-ttu-id="4cb71-129">XRSDK</span><span class="sxs-lookup"><span data-stu-id="4cb71-129">XRSDK</span></span> | <span data-ttu-id="4cb71-130"> (unity 2019.3 中 [unity 新 XR 架構](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的實驗性) 支援。</span><span class="sxs-lookup"><span data-stu-id="4cb71-130">(Experimental) Support for [Unity's new XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3.</span></span> |
| <span data-ttu-id="4cb71-131">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="4cb71-131">MRTK/SDK</span></span> | | |
| | <span data-ttu-id="4cb71-132">實驗</span><span class="sxs-lookup"><span data-stu-id="4cb71-132">Experimental</span></span> | <span data-ttu-id="4cb71-133">實驗性功能，包括著色器、使用者介面控制項和個別系統管理員。</span><span class="sxs-lookup"><span data-stu-id="4cb71-133">Experimental features, including shaders, user interface controls and individual system managers.</span></span> |
| | <span data-ttu-id="4cb71-134">功能</span><span class="sxs-lookup"><span data-stu-id="4cb71-134">Features</span></span> | <span data-ttu-id="4cb71-135">建基於基礎封裝的功能。</span><span class="sxs-lookup"><span data-stu-id="4cb71-135">Functionality that builds upon the Foundation package.</span></span> |
| | <span data-ttu-id="4cb71-136">Profiles</span><span class="sxs-lookup"><span data-stu-id="4cb71-136">Profiles</span></span> | <span data-ttu-id="4cb71-137">Microsoft Mixed Reality 工具組系統和服務的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="4cb71-137">Default profiles for the Microsoft Mixed Reality Toolkit systems and services.</span></span> |
| | <span data-ttu-id="4cb71-138">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="4cb71-138">StandardAssets</span></span> | <span data-ttu-id="4cb71-139">一般資產;模型、材質、材質等等。</span><span class="sxs-lookup"><span data-stu-id="4cb71-139">Common assets; models, textures, materials, etc.</span></span> |
| <span data-ttu-id="4cb71-140">MRTK/服務</span><span class="sxs-lookup"><span data-stu-id="4cb71-140">MRTK/Services</span></span> | | |
| | [<span data-ttu-id="4cb71-141">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="4cb71-141">BoundarySystem</span></span>](../features/Boundary/BoundarySystemGettingStarted.md) | <span data-ttu-id="4cb71-142">執行 VR 界限支援的系統。</span><span class="sxs-lookup"><span data-stu-id="4cb71-142">System implementing VR boundary support.</span></span> |
| | [<span data-ttu-id="4cb71-143">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="4cb71-143">CameraSystem</span></span>](../features/CameraSystem/CameraSystemOverview.md) | <span data-ttu-id="4cb71-144">系統執行攝影機設定和管理。</span><span class="sxs-lookup"><span data-stu-id="4cb71-144">System implementing camera configuration and management.</span></span> |
| | [<span data-ttu-id="4cb71-145">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="4cb71-145">DiagnosticsSystem</span></span>](../features/Diagnostics/DiagnosticsSystemGettingStarted.md) | <span data-ttu-id="4cb71-146">在 application diagnostics 中執行的系統，例如 visual profiler。</span><span class="sxs-lookup"><span data-stu-id="4cb71-146">System implementing in application diagnostics, for example a visual profiler.</span></span> |
| | [<span data-ttu-id="4cb71-147">InputAnimation</span><span class="sxs-lookup"><span data-stu-id="4cb71-147">InputAnimation</span></span>](../features/InputSimulation/InputAnimationRecording.md) | <span data-ttu-id="4cb71-148">支援錄製 head 移動和手追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="4cb71-148">Support for recording head movement and hand tracking data.</span></span> |
| | [<span data-ttu-id="4cb71-149">InputSimulation</span><span class="sxs-lookup"><span data-stu-id="4cb71-149">InputSimulation</span></span>](../features/InputSimulation/InputSimulationService.md) | <span data-ttu-id="4cb71-150">支援手形和眼睛輸入的編輯器內模擬。</span><span class="sxs-lookup"><span data-stu-id="4cb71-150">Support for in-editor simulation of hand and eye input.</span></span> |
| | [<span data-ttu-id="4cb71-151">InputSystem</span><span class="sxs-lookup"><span data-stu-id="4cb71-151">InputSystem</span></span>](../features/Input/Overview.md) | <span data-ttu-id="4cb71-152">系統，提供存取和處理使用者輸入的支援。</span><span class="sxs-lookup"><span data-stu-id="4cb71-152">System providing support for accessing and handling user input.</span></span> |
| | [<span data-ttu-id="4cb71-153">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="4cb71-153">SceneSystem</span></span>](../features/SceneSystem/SceneSystemGettingStarted.md) | <span data-ttu-id="4cb71-154">提供多場景應用程式支援的系統。</span><span class="sxs-lookup"><span data-stu-id="4cb71-154">System providing multi-scene application support.</span></span> |
| | [<span data-ttu-id="4cb71-155">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="4cb71-155">SpatialAwarenessSystem</span></span>](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md) | <span data-ttu-id="4cb71-156">提供使用者環境感知支援的系統。</span><span class="sxs-lookup"><span data-stu-id="4cb71-156">System providing support for awareness of the user's environment.</span></span> |
| | [<span data-ttu-id="4cb71-157">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="4cb71-157">TeleportSystem</span></span>](../features/TeleportSystem/Overview.md) | <span data-ttu-id="4cb71-158">提供 teleporting 支援的系統 (移至跳躍) 的體驗。</span><span class="sxs-lookup"><span data-stu-id="4cb71-158">System providing support for teleporting (moving about the experience in jumps).</span></span> |

## <a name="extensions"></a><span data-ttu-id="4cb71-159">延伸模組</span><span class="sxs-lookup"><span data-stu-id="4cb71-159">Extensions</span></span>

<span data-ttu-id="4cb71-160">選用的 MixedRealityToolkit 套件包含擴充 Microsoft Mixed Reality 工具組功能的其他服務。</span><span class="sxs-lookup"><span data-stu-id="4cb71-160">The optional Microsoft.MixedRealityToolkit.Unity.Extensions package includes additional services that extend the functionality of the Microsoft Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="4cb71-161">延伸模組套件需要 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="4cb71-161">The extensions package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="4cb71-162">資料夾</span><span class="sxs-lookup"><span data-stu-id="4cb71-162">Folder</span></span> | <span data-ttu-id="4cb71-163">元件</span><span class="sxs-lookup"><span data-stu-id="4cb71-163">Component</span></span> | <span data-ttu-id="4cb71-164">描述</span><span class="sxs-lookup"><span data-stu-id="4cb71-164">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="4cb71-165">MRTK/擴充功能</span><span class="sxs-lookup"><span data-stu-id="4cb71-165">MRTK/Extensions</span></span> | |
| | <span data-ttu-id="4cb71-166">HandPhysicsService</span><span class="sxs-lookup"><span data-stu-id="4cb71-166">HandPhysicsService</span></span> | <span data-ttu-id="4cb71-167">將物理支援新增至明確表述的服務。</span><span class="sxs-lookup"><span data-stu-id="4cb71-167">Service that adds physics support to articulated hands.</span></span> |
| | <span data-ttu-id="4cb71-168">LostTrackingService</span><span class="sxs-lookup"><span data-stu-id="4cb71-168">LostTrackingService</span></span> | <span data-ttu-id="4cb71-169">這項服務可簡化 Microsoft HoloLens 裝置上的追蹤遺失處理。</span><span class="sxs-lookup"><span data-stu-id="4cb71-169">Service that simplifies handing of tracking loss on Microsoft HoloLens devices.</span></span> |
| | [<span data-ttu-id="4cb71-170">SceneTransitionService</span><span class="sxs-lookup"><span data-stu-id="4cb71-170">SceneTransitionService</span></span>](../features/Extensions/SceneTransitionService/SceneTransitionServiceOverview.md) | <span data-ttu-id="4cb71-171">簡化加入平滑場景轉換的服務。</span><span class="sxs-lookup"><span data-stu-id="4cb71-171">Service that simplifies adding smooth scene transitions.</span></span> |

## <a name="tools"></a><span data-ttu-id="4cb71-172">工具</span><span class="sxs-lookup"><span data-stu-id="4cb71-172">Tools</span></span>

<span data-ttu-id="4cb71-173">選用的 MixedRealityToolkit 套件包含實用的工具，可使用 Microsoft Mixed Reality 工具組強化混合現實開發體驗。</span><span class="sxs-lookup"><span data-stu-id="4cb71-173">The optional Microsoft.MixedRealityToolkit.Unity.Tools package includes helpful tools that enhance the mixed reality development experience using the Microsoft Mixed Reality Toolkit.</span></span>
<span data-ttu-id="4cb71-174">這些工具位於 Unity 編輯器中的 **混合現實工具組 > 公用程式** 功能表。</span><span class="sxs-lookup"><span data-stu-id="4cb71-174">These tools are located in the **Mixed Reality Toolkit > Utilities** menu in the Unity Editor.</span></span>

> [!NOTE]
> <span data-ttu-id="4cb71-175">此工具套件需要 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="4cb71-175">The tools package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="4cb71-176">資料夾</span><span class="sxs-lookup"><span data-stu-id="4cb71-176">Folder</span></span> | <span data-ttu-id="4cb71-177">元件</span><span class="sxs-lookup"><span data-stu-id="4cb71-177">Component</span></span> | <span data-ttu-id="4cb71-178">描述</span><span class="sxs-lookup"><span data-stu-id="4cb71-178">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="4cb71-179">MRTK/工具</span><span class="sxs-lookup"><span data-stu-id="4cb71-179">MRTK/Tools</span></span> | |
| | [<span data-ttu-id="4cb71-180">DependencyWindow</span><span class="sxs-lookup"><span data-stu-id="4cb71-180">DependencyWindow</span></span>](../features/Tools/DependencyWindow.md) | <span data-ttu-id="4cb71-181">此工具會在專案中建立資產的相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="4cb71-181">Tool that creates a dependency graph of assets in a project.</span></span> |
| | [<span data-ttu-id="4cb71-182">ExtensionServiceCreator</span><span class="sxs-lookup"><span data-stu-id="4cb71-182">ExtensionServiceCreator</span></span>](../features/Tools/ExtensionServiceCreationWizard.md) | <span data-ttu-id="4cb71-183">協助建立延伸模組服務的 Wizard。</span><span class="sxs-lookup"><span data-stu-id="4cb71-183">Wizard to assist in creating extension services.</span></span> |
| | [<span data-ttu-id="4cb71-184">OptimizeWindow</span><span class="sxs-lookup"><span data-stu-id="4cb71-184">OptimizeWindow</span></span>](../features/Tools/OptimizeWindow.md) | <span data-ttu-id="4cb71-185">此公用程式可協助您自動設定混合現實專案，以獲得 Unity 的最佳效能。</span><span class="sxs-lookup"><span data-stu-id="4cb71-185">Utility to help automate configuring a mixed reality project for the best performance in Unity.</span></span> |
| | <span data-ttu-id="4cb71-186">ReserializeAssetsUtility</span><span class="sxs-lookup"><span data-stu-id="4cb71-186">ReserializeAssetsUtility</span></span> | <span data-ttu-id="4cb71-187">提供 reserializing 特定 Unity 檔案的支援。</span><span class="sxs-lookup"><span data-stu-id="4cb71-187">Provides support for reserializing specific Unity files.</span></span> |
| | [<span data-ttu-id="4cb71-188">RuntimeTools/Tools/ControllerMappingTool</span><span class="sxs-lookup"><span data-stu-id="4cb71-188">RuntimeTools/Tools/ControllerMappingTool</span></span>](../features/Tools/ControllerMappingTool.md) | <span data-ttu-id="4cb71-189">此公用程式可讓開發人員快速判斷硬體控制器的 Unity 對應。</span><span class="sxs-lookup"><span data-stu-id="4cb71-189">Utility enabling developers to quickly determine Unity mappings for hardware controllers.</span></span> |
| | <span data-ttu-id="4cb71-190">ScreenshotUtility</span><span class="sxs-lookup"><span data-stu-id="4cb71-190">ScreenshotUtility</span></span> | <span data-ttu-id="4cb71-191">在 Unity 編輯器中啟用捕獲應用程式映射。</span><span class="sxs-lookup"><span data-stu-id="4cb71-191">Enables capturing application images in the Unity editor.</span></span> |
| | <span data-ttu-id="4cb71-192">TextureCombinerWindow</span><span class="sxs-lookup"><span data-stu-id="4cb71-192">TextureCombinerWindow</span></span> | <span data-ttu-id="4cb71-193">結合圖形材質的公用程式。</span><span class="sxs-lookup"><span data-stu-id="4cb71-193">Utility to combine graphics textures.</span></span> |

## <a name="examples"></a><span data-ttu-id="4cb71-194">範例</span><span class="sxs-lookup"><span data-stu-id="4cb71-194">Examples</span></span>

<span data-ttu-id="4cb71-195">選擇性的 MixedRealityToolkit 範例套件包含說明 Microsoft Mixed Reality 工具組功能的示範專案。</span><span class="sxs-lookup"><span data-stu-id="4cb71-195">The optional Microsoft.MixedRealityToolkit.Unity.Examples package includes demonstration projects that illustrate the features of the Microsoft Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="4cb71-196">這些範例套件需要 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="4cb71-196">The examples package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="4cb71-197">資料夾</span><span class="sxs-lookup"><span data-stu-id="4cb71-197">Folder</span></span> | <span data-ttu-id="4cb71-198">元件</span><span class="sxs-lookup"><span data-stu-id="4cb71-198">Component</span></span> | <span data-ttu-id="4cb71-199">描述</span><span class="sxs-lookup"><span data-stu-id="4cb71-199">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="4cb71-200">MRTK/範例</span><span class="sxs-lookup"><span data-stu-id="4cb71-200">MRTK/Examples</span></span> | | |
| | <span data-ttu-id="4cb71-201">示範</span><span class="sxs-lookup"><span data-stu-id="4cb71-201">Demos</span></span> | <span data-ttu-id="4cb71-202">說明一或兩個相關功能的簡單場景。</span><span class="sxs-lookup"><span data-stu-id="4cb71-202">Simple scenes illustrating one or two related features.</span></span> |
| | <span data-ttu-id="4cb71-203">實驗</span><span class="sxs-lookup"><span data-stu-id="4cb71-203">Experimental</span></span> | <span data-ttu-id="4cb71-204">示範實驗性功能的示範場景。</span><span class="sxs-lookup"><span data-stu-id="4cb71-204">Demo scenes illustrating experimental features.</span></span> |
| | <span data-ttu-id="4cb71-205">督察</span><span class="sxs-lookup"><span data-stu-id="4cb71-205">Inspectors</span></span> | <span data-ttu-id="4cb71-206">示範場景所使用的 Unity 編輯器偵測器。</span><span class="sxs-lookup"><span data-stu-id="4cb71-206">Unity Editor inspectors used by demo scenes.</span></span> |
| | <span data-ttu-id="4cb71-207">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="4cb71-207">StandardAssets</span></span> | <span data-ttu-id="4cb71-208">多個示範場景所共用的常見資產。</span><span class="sxs-lookup"><span data-stu-id="4cb71-208">Common assets shared by multiple demo scenes.</span></span> |

## <a name="see-also"></a><span data-ttu-id="4cb71-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cb71-209">See also</span></span>

- [<span data-ttu-id="4cb71-210">歡迎使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="4cb71-210">Welcome to MRTK</span></span>](../WelcomeToMRTK.md)
- [<span data-ttu-id="4cb71-211">NuGet 封裝</span><span class="sxs-lookup"><span data-stu-id="4cb71-211">NuGet Packaging</span></span>](MRTKNuGetPackage.md)
