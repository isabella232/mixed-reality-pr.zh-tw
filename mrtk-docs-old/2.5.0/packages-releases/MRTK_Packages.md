---
title: MRTK_Pakages
description: MRTK 中的套件支援混合現實硬體和平臺。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Unity Pakage Manager、
ms.openlocfilehash: 7563a22cbb6241a694cc1394b8fa3ad9adc5c55f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685031"
---
# <a name="mixed-reality-toolkit-packages"></a><span data-ttu-id="b0f39-104">混合現實工具組套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-104">Mixed Reality Toolkit packages</span></span>

<span data-ttu-id="b0f39-105"> (MRTK) 的混合現實工具組是封裝的集合，可提供混合現實硬體和平臺的支援，藉此啟用跨平臺混合現實應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="b0f39-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms.</span></span>

<span data-ttu-id="b0f39-106">MRTK 可作為 [資產](#asset-packages) ( unitypackage) 套件和透過 [Unity 封裝管理員](#unity-package-manager)。</span><span class="sxs-lookup"><span data-stu-id="b0f39-106">MRTK is available as [asset](#asset-packages) (.unitypackage) packages and via the [Unity Package Manager](#unity-package-manager).</span></span>

## <a name="asset-packages"></a><span data-ttu-id="b0f39-107">資產套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-107">Asset packages</span></span>

<span data-ttu-id="b0f39-108">您可以從 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)下載 MRTK 資產 (. unitypackage) 。</span><span class="sxs-lookup"><span data-stu-id="b0f39-108">The MRTK asset (.unitypackage) can be downloaded from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span>

<span data-ttu-id="b0f39-109">使用資產套件的一些優點包括：</span><span class="sxs-lookup"><span data-stu-id="b0f39-109">Some of the benefits of using asset packages include:</span></span>

- <span data-ttu-id="b0f39-110">適用于 Unity 2018.4 和更新版本</span><span class="sxs-lookup"><span data-stu-id="b0f39-110">Available for Unity 2018.4 and newer</span></span>
- <span data-ttu-id="b0f39-111">輕鬆變更 MRTK</span><span class="sxs-lookup"><span data-stu-id="b0f39-111">Easy to make changes to MRTK</span></span>
  - <span data-ttu-id="b0f39-112">MRTK 在 [資產] 資料夾中</span><span class="sxs-lookup"><span data-stu-id="b0f39-112">MRTK is in the Assets folder</span></span>

<span data-ttu-id="b0f39-113">其中一些挑戰如下：</span><span class="sxs-lookup"><span data-stu-id="b0f39-113">Some of the challenges are:</span></span>

- <span data-ttu-id="b0f39-114">MRTK 是專案 [資產] 資料夾的一部分，</span><span class="sxs-lookup"><span data-stu-id="b0f39-114">MRTK is part of the project's Assets folder, leading to</span></span>
  - <span data-ttu-id="b0f39-115">較大型的專案</span><span class="sxs-lookup"><span data-stu-id="b0f39-115">Larger projects</span></span>
  - <span data-ttu-id="b0f39-116">較慢的編譯時間</span><span class="sxs-lookup"><span data-stu-id="b0f39-116">Slower compilation times</span></span>
- <span data-ttu-id="b0f39-117">無相依性管理</span><span class="sxs-lookup"><span data-stu-id="b0f39-117">No dependency management</span></span>
  - <span data-ttu-id="b0f39-118">客戶必須手動解析套件相依性</span><span class="sxs-lookup"><span data-stu-id="b0f39-118">Customers are required to resolve package dependencies manually</span></span>
- <span data-ttu-id="b0f39-119">手動更新程式</span><span class="sxs-lookup"><span data-stu-id="b0f39-119">Manual update process</span></span>
  - <span data-ttu-id="b0f39-120">多個步驟</span><span class="sxs-lookup"><span data-stu-id="b0f39-120">Multiple steps</span></span>
  - <span data-ttu-id="b0f39-121">大型 (3000 + 檔案) 原始檔控制更新</span><span class="sxs-lookup"><span data-stu-id="b0f39-121">Large (3000+ file) source control updates</span></span>
  - <span data-ttu-id="b0f39-122">遺失對 MRTK 進行變更的風險</span><span class="sxs-lookup"><span data-stu-id="b0f39-122">Risk of losing changes made to MRTK</span></span>
- <span data-ttu-id="b0f39-123">匯入範例封裝通常表示包含所有範例</span><span class="sxs-lookup"><span data-stu-id="b0f39-123">Importing the examples package typically means including all examples</span></span>

<span data-ttu-id="b0f39-124">可用的封裝如下：</span><span class="sxs-lookup"><span data-stu-id="b0f39-124">The available packages are:</span></span>

- [<span data-ttu-id="b0f39-125">基礎</span><span class="sxs-lookup"><span data-stu-id="b0f39-125">Foundation</span></span>](#foundation-package)
- [<span data-ttu-id="b0f39-126">擴充功能</span><span class="sxs-lookup"><span data-stu-id="b0f39-126">Extensions</span></span>](#extensions-package)
- [<span data-ttu-id="b0f39-127">工具</span><span class="sxs-lookup"><span data-stu-id="b0f39-127">Tools</span></span>](#tools-package)
- [<span data-ttu-id="b0f39-128">測試公用程式</span><span class="sxs-lookup"><span data-stu-id="b0f39-128">Test utilities</span></span>](#test-utilities-package)
- [<span data-ttu-id="b0f39-129">範例</span><span class="sxs-lookup"><span data-stu-id="b0f39-129">Examples</span></span>](#examples-package)

<span data-ttu-id="b0f39-130">Microsoft 會從 GitHub 上 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) 分支中的原始程式碼發行並支援這些套件。</span><span class="sxs-lookup"><span data-stu-id="b0f39-130">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

### <a name="foundation-package"></a><span data-ttu-id="b0f39-131">基礎封裝</span><span class="sxs-lookup"><span data-stu-id="b0f39-131">Foundation package</span></span>

<span data-ttu-id="b0f39-132">混合現實工具組基礎是一組程式碼，可讓您的應用程式跨混合現實平臺運用一般功能。</span><span class="sxs-lookup"><span data-stu-id="b0f39-132">The Mixed Reality Toolkit Foundation is the set of code that enables your application to leverage common functionality across Mixed Reality Platforms.</span></span>

<img src="../features/Images/Input/MRTK_Package_Foundation.png" width="350px" alt="MRTK Foundation pakage" style="display:block;">  
<span data-ttu-id="b0f39-133"><sup>MRTK 基礎封裝</sup></span><span class="sxs-lookup"><span data-stu-id="b0f39-133"><sup>MRTK Foundation Package</sup></span></span>

<span data-ttu-id="b0f39-134">MRTK Foundation 套件包含下列各項。</span><span class="sxs-lookup"><span data-stu-id="b0f39-134">The MRTK Foundation package contains the following.</span></span>

| <span data-ttu-id="b0f39-135">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-135">Folder</span></span> | <span data-ttu-id="b0f39-136">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-136">Component</span></span> | <span data-ttu-id="b0f39-137">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-137">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-138">MRTK/核心</span><span class="sxs-lookup"><span data-stu-id="b0f39-138">MRTK/Core</span></span> | | <span data-ttu-id="b0f39-139">介面和類型定義、基類、標準著色器。</span><span class="sxs-lookup"><span data-stu-id="b0f39-139">Interface and type definitions, base classes, standard shader.</span></span> |
| <span data-ttu-id="b0f39-140">MRTK/核心/提供者</span><span class="sxs-lookup"><span data-stu-id="b0f39-140">MRTK/Core/Providers</span></span> | | <span data-ttu-id="b0f39-141">平臺中立的資料提供者</span><span class="sxs-lookup"><span data-stu-id="b0f39-141">Platform agnostic data providers</span></span> |
| | <span data-ttu-id="b0f39-142">手</span><span class="sxs-lookup"><span data-stu-id="b0f39-142">Hands</span></span> | <span data-ttu-id="b0f39-143">用於手動追蹤的基類支援和服務。</span><span class="sxs-lookup"><span data-stu-id="b0f39-143">Base class support and services for hand tracking.</span></span> |
| | [<span data-ttu-id="b0f39-144">InputAnimation</span><span class="sxs-lookup"><span data-stu-id="b0f39-144">InputAnimation</span></span>](../features/InputSimulation/InputAnimationRecording.md) | <span data-ttu-id="b0f39-145">支援錄製 head 移動和手追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="b0f39-145">Support for recording head movement and hand tracking data.</span></span> |
| | [<span data-ttu-id="b0f39-146">InputSimulation</span><span class="sxs-lookup"><span data-stu-id="b0f39-146">InputSimulation</span></span>](../features/InputSimulation/InputSimulationService.md) | <span data-ttu-id="b0f39-147">支援手形和眼睛輸入的編輯器內模擬。</span><span class="sxs-lookup"><span data-stu-id="b0f39-147">Support for in-editor simulation of hand and eye input.</span></span> |
| | [<span data-ttu-id="b0f39-148">ObjectMeshObserver</span><span class="sxs-lookup"><span data-stu-id="b0f39-148">ObjectMeshObserver</span></span>](../features/SpatialAwareness/SpatialObjectMeshObserver.md) | <span data-ttu-id="b0f39-149">空間感知觀察者使用3D 模型做為資料。</span><span class="sxs-lookup"><span data-stu-id="b0f39-149">Spatial awareness observer using a 3D model as the data.</span></span> |
| | <span data-ttu-id="b0f39-150">UnityInput</span><span class="sxs-lookup"><span data-stu-id="b0f39-150">UnityInput</span></span> | <span data-ttu-id="b0f39-151">一般輸入裝置 (搖桿、滑鼠等 ) 透過 Unity 的輸入 API 來執行。</span><span class="sxs-lookup"><span data-stu-id="b0f39-151">Common input devices (joystick, mouse, etc.) implemented via Unity's input API.</span></span> |
| <span data-ttu-id="b0f39-152">MRTK/提供者</span><span class="sxs-lookup"><span data-stu-id="b0f39-152">MRTK/Providers</span></span> | | <span data-ttu-id="b0f39-153">平臺特定的資料提供者</span><span class="sxs-lookup"><span data-stu-id="b0f39-153">Platform specific data providers</span></span> |
| | <span data-ttu-id="b0f39-154">LeapMotion</span><span class="sxs-lookup"><span data-stu-id="b0f39-154">LeapMotion</span></span> | <span data-ttu-id="b0f39-155">UltraLeap Leap 移動控制器的支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-155">Support for the UltraLeap Leap Motion controller.</span></span> |
| | <span data-ttu-id="b0f39-156">OpenVR</span><span class="sxs-lookup"><span data-stu-id="b0f39-156">OpenVR</span></span> | <span data-ttu-id="b0f39-157">OpenVR 裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-157">Support for OpenVR devices.</span></span> |
| | <span data-ttu-id="b0f39-158">Oculus</span><span class="sxs-lookup"><span data-stu-id="b0f39-158">Oculus</span></span> | <span data-ttu-id="b0f39-159">Oculus 裝置的支援，例如尋找。</span><span class="sxs-lookup"><span data-stu-id="b0f39-159">Support for Oculus devices, such as the Quest.</span></span> |
| | [<span data-ttu-id="b0f39-160">UnityAR</span><span class="sxs-lookup"><span data-stu-id="b0f39-160">UnityAR</span></span>](../features/CameraSystem/UnityArCameraSettings.md) | <span data-ttu-id="b0f39-161"> (實驗性) 攝影機設定提供者，讓 MRTK 與行動 AR 裝置搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b0f39-161">(Experimental) Camera settings provider enabling MRTK use with mobile AR devices.</span></span> |
| | <span data-ttu-id="b0f39-162">WindowsMixedReality</span><span class="sxs-lookup"><span data-stu-id="b0f39-162">WindowsMixedReality</span></span> | <span data-ttu-id="b0f39-163">支援 Windows Mixed Reality 的裝置，包括 Microsoft HoloLens 和沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="b0f39-163">Support for Windows Mixed Reality devices, including Microsoft HoloLens and immersive headsets.</span></span> |
| | <span data-ttu-id="b0f39-164">Windows</span><span class="sxs-lookup"><span data-stu-id="b0f39-164">Windows</span></span> | <span data-ttu-id="b0f39-165">支援 Microsoft Windows 特定 Api，例如語音和聽寫。</span><span class="sxs-lookup"><span data-stu-id="b0f39-165">Support for Microsoft Windows specific APIs, for example speech and dictation.</span></span> |
| | <span data-ttu-id="b0f39-166">XR SDK</span><span class="sxs-lookup"><span data-stu-id="b0f39-166">XR SDK</span></span> | <span data-ttu-id="b0f39-167"> (unity 2019.3 和更新版本中 [unity 新 XR 架構](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的實驗性) 支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-167">(Experimental) Support for [Unity's new XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3 and newer.</span></span> |
| <span data-ttu-id="b0f39-168">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="b0f39-168">MRTK/SDK</span></span> | | |
| | <span data-ttu-id="b0f39-169">實驗</span><span class="sxs-lookup"><span data-stu-id="b0f39-169">Experimental</span></span> | <span data-ttu-id="b0f39-170">實驗性功能，包括著色器、使用者介面控制項和個別系統管理員。</span><span class="sxs-lookup"><span data-stu-id="b0f39-170">Experimental features, including shaders, user interface controls and individual system managers.</span></span> |
| | <span data-ttu-id="b0f39-171">功能</span><span class="sxs-lookup"><span data-stu-id="b0f39-171">Features</span></span> | <span data-ttu-id="b0f39-172">建基於基礎封裝的功能。</span><span class="sxs-lookup"><span data-stu-id="b0f39-172">Functionality that builds upon the Foundation package.</span></span> |
| | <span data-ttu-id="b0f39-173">Profiles</span><span class="sxs-lookup"><span data-stu-id="b0f39-173">Profiles</span></span> | <span data-ttu-id="b0f39-174">Microsoft Mixed Reality 工具組系統和服務的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="b0f39-174">Default profiles for the Microsoft Mixed Reality Toolkit systems and services.</span></span> |
| | <span data-ttu-id="b0f39-175">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="b0f39-175">StandardAssets</span></span> | <span data-ttu-id="b0f39-176">一般資產;模型、材質、材質等等。</span><span class="sxs-lookup"><span data-stu-id="b0f39-176">Common assets; models, textures, materials, etc.</span></span> |
| <span data-ttu-id="b0f39-177">MRTK/服務</span><span class="sxs-lookup"><span data-stu-id="b0f39-177">MRTK/Services</span></span> | | |
| | [<span data-ttu-id="b0f39-178">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-178">BoundarySystem</span></span>](../features/Boundary/BoundarySystemGettingStarted.md) | <span data-ttu-id="b0f39-179">執行 VR 界限支援的系統。</span><span class="sxs-lookup"><span data-stu-id="b0f39-179">System implementing VR boundary support.</span></span> |
| | [<span data-ttu-id="b0f39-180">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-180">CameraSystem</span></span>](../features/CameraSystem/CameraSystemOverview.md) | <span data-ttu-id="b0f39-181">系統執行攝影機設定和管理。</span><span class="sxs-lookup"><span data-stu-id="b0f39-181">System implementing camera configuration and management.</span></span> |
| | [<span data-ttu-id="b0f39-182">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-182">DiagnosticsSystem</span></span>](../features/Diagnostics/DiagnosticsSystemGettingStarted.md) | <span data-ttu-id="b0f39-183">在 application diagnostics 中執行的系統，例如 visual profiler。</span><span class="sxs-lookup"><span data-stu-id="b0f39-183">System implementing in application diagnostics, for example a visual profiler.</span></span> |
<span data-ttu-id="b0f39-184">?</span><span class="sxs-lookup"><span data-stu-id="b0f39-184">?</span></span> | [<span data-ttu-id="b0f39-185">InputSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-185">InputSystem</span></span>](../features/Input/Overview.md) | <span data-ttu-id="b0f39-186">系統，提供存取和處理使用者輸入的支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-186">System providing support for accessing and handling user input.</span></span> |
| | [<span data-ttu-id="b0f39-187">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-187">SceneSystem</span></span>](../features/SceneSystem/SceneSystemGettingStarted.md) | <span data-ttu-id="b0f39-188">提供多場景應用程式支援的系統。</span><span class="sxs-lookup"><span data-stu-id="b0f39-188">System providing multi-scene application support.</span></span> |
| | [<span data-ttu-id="b0f39-189">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-189">SpatialAwarenessSystem</span></span>](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md) | <span data-ttu-id="b0f39-190">提供使用者環境感知支援的系統。</span><span class="sxs-lookup"><span data-stu-id="b0f39-190">System providing support for awareness of the user's environment.</span></span> |
| | [<span data-ttu-id="b0f39-191">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-191">TeleportSystem</span></span>](../features/TeleportSystem/Overview.md) | <span data-ttu-id="b0f39-192">提供 teleporting 支援的系統 (移至跳躍) 的體驗。</span><span class="sxs-lookup"><span data-stu-id="b0f39-192">System providing support for teleporting (moving about the experience in jumps).</span></span> |
| <span data-ttu-id="b0f39-193">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="b0f39-193">MRTK/StandardAssets</span></span> | | <span data-ttu-id="b0f39-194">混合現實體驗的 MRTK 標準著色器、基本材質和其他標準資產</span><span class="sxs-lookup"><span data-stu-id="b0f39-194">MRTK Standard shader, basic materials and other standard assets for mixed reality experiences</span></span> |

### <a name="extensions-package"></a><span data-ttu-id="b0f39-195">擴充功能套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-195">Extensions package</span></span>

<span data-ttu-id="b0f39-196">選用的 MixedRealityToolkit 套件包含擴充 Microsoft Mixed Reality 工具組功能的其他服務。</span><span class="sxs-lookup"><span data-stu-id="b0f39-196">The optional Microsoft.MixedRealityToolkit.Unity.Extensions package includes additional services that extend the functionality of the Microsoft Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="b0f39-197">延伸模組套件需要 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="b0f39-197">The extensions package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="b0f39-198">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-198">Folder</span></span> | <span data-ttu-id="b0f39-199">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-199">Component</span></span> | <span data-ttu-id="b0f39-200">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-200">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-201">MRTK/擴充功能</span><span class="sxs-lookup"><span data-stu-id="b0f39-201">MRTK/Extensions</span></span> | |
| | [<span data-ttu-id="b0f39-202">HandPhysicsService</span><span class="sxs-lookup"><span data-stu-id="b0f39-202">HandPhysicsService</span></span>](../features/Extensions/HandPhysicsService/HandPhysicsServiceOverview.md) | <span data-ttu-id="b0f39-203">將物理支援新增至明確表述的服務。</span><span class="sxs-lookup"><span data-stu-id="b0f39-203">Service that adds physics support to articulated hands.</span></span> |
| | <span data-ttu-id="b0f39-204">LostTrackingService</span><span class="sxs-lookup"><span data-stu-id="b0f39-204">LostTrackingService</span></span> | <span data-ttu-id="b0f39-205">這項服務可簡化 Microsoft HoloLens 裝置上的追蹤遺失處理。</span><span class="sxs-lookup"><span data-stu-id="b0f39-205">Service that simplifies handling of tracking loss on Microsoft HoloLens devices.</span></span> |
| | [<span data-ttu-id="b0f39-206">SceneTransitionService</span><span class="sxs-lookup"><span data-stu-id="b0f39-206">SceneTransitionService</span></span>](../features/Extensions/SceneTransitionService/SceneTransitionServiceOverview.md) | <span data-ttu-id="b0f39-207">簡化加入平滑場景轉換的服務。</span><span class="sxs-lookup"><span data-stu-id="b0f39-207">Service that simplifies adding smooth scene transitions.</span></span> |

### <a name="tools-package"></a><span data-ttu-id="b0f39-208">工具套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-208">Tools package</span></span>

<span data-ttu-id="b0f39-209">選用的 MixedRealityToolkit 套件包含實用的工具，可使用 Microsoft Mixed Reality 工具組強化混合現實開發體驗。</span><span class="sxs-lookup"><span data-stu-id="b0f39-209">The optional Microsoft.MixedRealityToolkit.Unity.Tools package includes helpful tools that enhance the mixed reality development experience using the Microsoft Mixed Reality Toolkit.</span></span>
<span data-ttu-id="b0f39-210">這些工具位於 Unity 編輯器中的 **混合現實工具組 > 公用程式** 功能表。</span><span class="sxs-lookup"><span data-stu-id="b0f39-210">These tools are located in the **Mixed Reality Toolkit > Utilities** menu in the Unity Editor.</span></span>

> [!NOTE]
> <span data-ttu-id="b0f39-211">此工具套件需要 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="b0f39-211">The tools package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="b0f39-212">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-212">Folder</span></span> | <span data-ttu-id="b0f39-213">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-213">Component</span></span> | <span data-ttu-id="b0f39-214">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-214">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-215">MRTK/工具</span><span class="sxs-lookup"><span data-stu-id="b0f39-215">MRTK/Tools</span></span> | |
| | <span data-ttu-id="b0f39-216">BuildWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-216">BuildWindow</span></span> | <span data-ttu-id="b0f39-217">這項工具可協助簡化建立和部署 UWP 應用程式的流程。</span><span class="sxs-lookup"><span data-stu-id="b0f39-217">Tool that helps simplify the process of building and deploying UWP applications.</span></span> |
| | [<span data-ttu-id="b0f39-218">DependencyWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-218">DependencyWindow</span></span>](../features/Tools/DependencyWindow.md) | <span data-ttu-id="b0f39-219">此工具會在專案中建立資產的相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="b0f39-219">Tool that creates a dependency graph of assets in a project.</span></span> |
| | [<span data-ttu-id="b0f39-220">ExtensionServiceCreator</span><span class="sxs-lookup"><span data-stu-id="b0f39-220">ExtensionServiceCreator</span></span>](../features/Tools/ExtensionServiceCreationWizard.md) | <span data-ttu-id="b0f39-221">協助建立延伸模組服務的 Wizard。</span><span class="sxs-lookup"><span data-stu-id="b0f39-221">Wizard to assist in creating extension services.</span></span> |
| | [<span data-ttu-id="b0f39-222">MigrationWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-222">MigrationWindow</span></span>](../features/Tools/MigrationWindow.md) | <span data-ttu-id="b0f39-223">協助更新使用已淘汰 MRTK 元件之程式碼的工具。</span><span class="sxs-lookup"><span data-stu-id="b0f39-223">Tool that assists in updating code that uses deprecated MRTK components.</span></span>  |
| | [<span data-ttu-id="b0f39-224">OptimizeWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-224">OptimizeWindow</span></span>](../features/Tools/OptimizeWindow.md) | <span data-ttu-id="b0f39-225">此公用程式可協助您自動設定混合現實專案，以獲得 Unity 的最佳效能。</span><span class="sxs-lookup"><span data-stu-id="b0f39-225">Utility to help automate configuring a mixed reality project for the best performance in Unity.</span></span> |
| | <span data-ttu-id="b0f39-226">ReserializeAssetsUtility</span><span class="sxs-lookup"><span data-stu-id="b0f39-226">ReserializeAssetsUtility</span></span> | <span data-ttu-id="b0f39-227">提供 reserializing 特定 Unity 檔案的支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-227">Provides support for reserializing specific Unity files.</span></span> |
| | [<span data-ttu-id="b0f39-228">RuntimeTools/Tools/ControllerMappingTool</span><span class="sxs-lookup"><span data-stu-id="b0f39-228">RuntimeTools/Tools/ControllerMappingTool</span></span>](../features/Tools/ControllerMappingTool.md) | <span data-ttu-id="b0f39-229">此公用程式可讓開發人員快速判斷硬體控制器的 Unity 對應。</span><span class="sxs-lookup"><span data-stu-id="b0f39-229">Utility enabling developers to quickly determine Unity mappings for hardware controllers.</span></span> |
| | <span data-ttu-id="b0f39-230">ScreenshotUtility</span><span class="sxs-lookup"><span data-stu-id="b0f39-230">ScreenshotUtility</span></span> | <span data-ttu-id="b0f39-231">在 Unity 編輯器中啟用捕獲應用程式映射。</span><span class="sxs-lookup"><span data-stu-id="b0f39-231">Enables capturing application images in the Unity editor.</span></span> |
| | <span data-ttu-id="b0f39-232">TextureCombinerWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-232">TextureCombinerWindow</span></span> | <span data-ttu-id="b0f39-233">結合圖形材質的公用程式。</span><span class="sxs-lookup"><span data-stu-id="b0f39-233">Utility to combine graphics textures.</span></span> |
| | [<span data-ttu-id="b0f39-234">工具箱</span><span class="sxs-lookup"><span data-stu-id="b0f39-234">Toolbox</span></span>](../features/README_Toolbox.md) | <span data-ttu-id="b0f39-235">可讓您輕鬆地探索及使用 MRTK UX 元件的 UI。</span><span class="sxs-lookup"><span data-stu-id="b0f39-235">UI that makes it easy to discover and use MRTK UX components.</span></span> |

### <a name="test-utilities-package"></a><span data-ttu-id="b0f39-236">測試公用程式套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-236">Test utilities package</span></span>

<span data-ttu-id="b0f39-237">選擇性的 MixedRealityToolkit TestUtilities 套件是協助程式腳本的集合，可讓開發人員輕鬆地 [建立播放模式測試](../Contributing/UnitTests.md#play-mode-tests)。</span><span class="sxs-lookup"><span data-stu-id="b0f39-237">The optional Microsoft.MixedRealityToolkit.TestUtilities package is a collection of helper scripts that enable developers to easily [create play mode tests](../Contributing/UnitTests.md#play-mode-tests).</span></span> <span data-ttu-id="b0f39-238">這些公用程式特別適用于建立 MRTK 元件的開發人員。</span><span class="sxs-lookup"><span data-stu-id="b0f39-238">These utilities are especially useful for developers creating MRTK components.</span></span>

| <span data-ttu-id="b0f39-239">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-239">Folder</span></span> | <span data-ttu-id="b0f39-240">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-240">Component</span></span> | <span data-ttu-id="b0f39-241">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-241">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-242">MRTK/測試</span><span class="sxs-lookup"><span data-stu-id="b0f39-242">MRTK/Tests</span></span> | |
| | <span data-ttu-id="b0f39-243">TestUtilities</span><span class="sxs-lookup"><span data-stu-id="b0f39-243">TestUtilities</span></span> | <span data-ttu-id="b0f39-244">簡化播放模式測試建立的方法，包括手動模擬公用程式。</span><span class="sxs-lookup"><span data-stu-id="b0f39-244">Methods to simplify creation of play mode tests, including hand simulation utilities.</span></span> |

### <a name="examples-package"></a><span data-ttu-id="b0f39-245">範例套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-245">Examples package</span></span>

<span data-ttu-id="b0f39-246">範例套件包含的示範、範例腳本，以及可在基礎套件中執行功能的範例幕後。</span><span class="sxs-lookup"><span data-stu-id="b0f39-246">The examples package contains demos, sample scripts, and sample scenes that exercise functionality in the foundation package.</span></span> <span data-ttu-id="b0f39-247">此套件包含 [HandInteractionExample 場景](../features/README_HandInteractionExamples.md) (如下圖所示) 其中包含的範例物件可回應各種類型的手寫輸入 (清楚說明的) 。</span><span class="sxs-lookup"><span data-stu-id="b0f39-247">This package contains the [HandInteractionExample scene](../features/README_HandInteractionExamples.md) (pictured below) which contains sample objects that respond to various types of hand input (articulated and non-articulated).</span></span>

![HandInteractionExample 場景](../features/Images/MRTK_Examples.png)

<span data-ttu-id="b0f39-249">此套件也包含眼睛追蹤示範，其 [記載于此處](../features/EyeTracking/EyeTracking_ExamplesOverview.md)</span><span class="sxs-lookup"><span data-stu-id="b0f39-249">This package also contains eye tracking demos, which are [documented here](../features/EyeTracking/EyeTracking_ExamplesOverview.md)</span></span>

<span data-ttu-id="b0f39-250">更常見的情況是，MRTK 中的任何新功能都應該包含範例套件中的對應範例，大致遵循相同的資料夾結構和位置。</span><span class="sxs-lookup"><span data-stu-id="b0f39-250">More generally, any new feature in the MRTK should contain a corresponding example in the examples package, roughly following the same folder structure and location.</span></span>

> [!NOTE]
> <span data-ttu-id="b0f39-251">這些範例套件需要 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="b0f39-251">The examples package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="b0f39-252">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-252">Folder</span></span> | <span data-ttu-id="b0f39-253">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-253">Component</span></span> | <span data-ttu-id="b0f39-254">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-254">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-255">MRTK/範例</span><span class="sxs-lookup"><span data-stu-id="b0f39-255">MRTK/Examples</span></span> | | |
| | <span data-ttu-id="b0f39-256">示範</span><span class="sxs-lookup"><span data-stu-id="b0f39-256">Demos</span></span> | <span data-ttu-id="b0f39-257">說明一或兩個相關功能的簡單場景。</span><span class="sxs-lookup"><span data-stu-id="b0f39-257">Simple scenes illustrating one or two related features.</span></span> |
| | <span data-ttu-id="b0f39-258">實驗</span><span class="sxs-lookup"><span data-stu-id="b0f39-258">Experimental</span></span> | <span data-ttu-id="b0f39-259">示範實驗性功能的示範場景。</span><span class="sxs-lookup"><span data-stu-id="b0f39-259">Demo scenes illustrating experimental features.</span></span> |
| | <span data-ttu-id="b0f39-260">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="b0f39-260">StandardAssets</span></span> | <span data-ttu-id="b0f39-261">多個示範場景所共用的常見資產。</span><span class="sxs-lookup"><span data-stu-id="b0f39-261">Common assets shared by multiple demo scenes.</span></span> |

## <a name="unity-package-manager"></a><span data-ttu-id="b0f39-262">Unity 封裝管理員</span><span class="sxs-lookup"><span data-stu-id="b0f39-262">Unity Package Manager</span></span>

<span data-ttu-id="b0f39-263">針對使用 Unity 2019.4 和更新版本所建立的體驗，MRTK 可透過 [unity 封裝管理員](https://docs.unity3d.com/Manual/Packages.html)取得。</span><span class="sxs-lookup"><span data-stu-id="b0f39-263">For experiences being created using Unity 2019.4 and newer, the MRTK is available via the [Unity Package Manager](https://docs.unity3d.com/Manual/Packages.html).</span></span>

<span data-ttu-id="b0f39-264">使用資產套件的一些優點包括：</span><span class="sxs-lookup"><span data-stu-id="b0f39-264">Some of the benefits of using asset packages include:</span></span>

- <span data-ttu-id="b0f39-265">較小的專案</span><span class="sxs-lookup"><span data-stu-id="b0f39-265">Smaller projects</span></span>
  - <span data-ttu-id="b0f39-266">更清楚的 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="b0f39-266">Cleaner Visual Studio solutions</span></span>
  - <span data-ttu-id="b0f39-267">要簽入的檔案越少 (MRTK 是檔案中的簡單參考 `Packages/manifest.json`) </span><span class="sxs-lookup"><span data-stu-id="b0f39-267">Fewer files to check in (MRTK is a simple reference in the `Packages/manifest.json` file)</span></span>
- <span data-ttu-id="b0f39-268">更快速的編譯</span><span class="sxs-lookup"><span data-stu-id="b0f39-268">Faster compilation</span></span>
  - <span data-ttu-id="b0f39-269">Unity 不需要在建立期間重新編譯 MRTK</span><span class="sxs-lookup"><span data-stu-id="b0f39-269">Unity does not need to recompile MRTK during building</span></span>
- <span data-ttu-id="b0f39-270">相依性解析</span><span class="sxs-lookup"><span data-stu-id="b0f39-270">Dependency resolution</span></span>
  - <span data-ttu-id="b0f39-271">指定具有相依性的套件時，會自動安裝必要的 MRTK 套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-271">Required MRTK packages are automatically installed when specifying packages with dependencies</span></span>
- <span data-ttu-id="b0f39-272">簡易更新新的 MRTK 版本</span><span class="sxs-lookup"><span data-stu-id="b0f39-272">Easy update to new MRTK versions</span></span>
  - <span data-ttu-id="b0f39-273">變更檔案 `Packages/manifest.json` 中的版本</span><span class="sxs-lookup"><span data-stu-id="b0f39-273">Change the version in the `Packages/manifest.json` file</span></span>

<span data-ttu-id="b0f39-274">其中一些挑戰如下：</span><span class="sxs-lookup"><span data-stu-id="b0f39-274">Some of the challenges are:</span></span>

- <span data-ttu-id="b0f39-275">MRTK 不可變</span><span class="sxs-lookup"><span data-stu-id="b0f39-275">MRTK is immutable</span></span>
  - <span data-ttu-id="b0f39-276">無法進行變更，而無法在封裝解析期間移除變更</span><span class="sxs-lookup"><span data-stu-id="b0f39-276">Cannot make changes without them being removed during package resolution</span></span>
- <span data-ttu-id="b0f39-277">MRTK 不支援使用 Unity 2018.4 的 UPM 套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-277">MRTK does not support UPM packages with Unity 2018.4</span></span>

### <a name="foundation-package"></a><span data-ttu-id="b0f39-278">基礎封裝</span><span class="sxs-lookup"><span data-stu-id="b0f39-278">Foundation package</span></span>

<span data-ttu-id="b0f39-279">基礎封裝 (`com.microsoft.mixedreality.toolkit.foundation`) 形成混合現實工具組的基礎。</span><span class="sxs-lookup"><span data-stu-id="b0f39-279">The foundation package (`com.microsoft.mixedreality.toolkit.foundation`) forms the basis of the Mixed Reality Toolkit.</span></span>

| <span data-ttu-id="b0f39-280">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-280">Folder</span></span> | <span data-ttu-id="b0f39-281">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-281">Component</span></span> | <span data-ttu-id="b0f39-282">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-282">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-283">MRTK/核心</span><span class="sxs-lookup"><span data-stu-id="b0f39-283">MRTK/Core</span></span> | | <span data-ttu-id="b0f39-284">介面和類型定義、基類、標準著色器。</span><span class="sxs-lookup"><span data-stu-id="b0f39-284">Interface and type definitions, base classes, standard shader.</span></span> |
| <span data-ttu-id="b0f39-285">MRTK/核心/提供者</span><span class="sxs-lookup"><span data-stu-id="b0f39-285">MRTK/Core/Providers</span></span> | | <span data-ttu-id="b0f39-286">平臺中立的資料提供者</span><span class="sxs-lookup"><span data-stu-id="b0f39-286">Platform agnostic data providers</span></span> |
| | <span data-ttu-id="b0f39-287">手</span><span class="sxs-lookup"><span data-stu-id="b0f39-287">Hands</span></span> | <span data-ttu-id="b0f39-288">用於手動追蹤的基類支援和服務。</span><span class="sxs-lookup"><span data-stu-id="b0f39-288">Base class support and services for hand tracking.</span></span> |
| | [<span data-ttu-id="b0f39-289">InputAnimation</span><span class="sxs-lookup"><span data-stu-id="b0f39-289">InputAnimation</span></span>](../features/InputSimulation/InputAnimationRecording.md) | <span data-ttu-id="b0f39-290">支援錄製 head 移動和手追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="b0f39-290">Support for recording head movement and hand tracking data.</span></span> |
| | [<span data-ttu-id="b0f39-291">InputSimulation</span><span class="sxs-lookup"><span data-stu-id="b0f39-291">InputSimulation</span></span>](../features/InputSimulation/InputSimulationService.md) | <span data-ttu-id="b0f39-292">支援手形和眼睛輸入的編輯器內模擬。</span><span class="sxs-lookup"><span data-stu-id="b0f39-292">Support for in-editor simulation of hand and eye input.</span></span> |
| | [<span data-ttu-id="b0f39-293">ObjectMeshObserver</span><span class="sxs-lookup"><span data-stu-id="b0f39-293">ObjectMeshObserver</span></span>](../features/SpatialAwareness/SpatialObjectMeshObserver.md) | <span data-ttu-id="b0f39-294">空間感知觀察者使用3D 模型做為資料。</span><span class="sxs-lookup"><span data-stu-id="b0f39-294">Spatial awareness observer using a 3D model as the data.</span></span> |
| | <span data-ttu-id="b0f39-295">UnityInput</span><span class="sxs-lookup"><span data-stu-id="b0f39-295">UnityInput</span></span> | <span data-ttu-id="b0f39-296">一般輸入裝置 (搖桿、滑鼠等 ) 透過 Unity 的輸入 API 來執行。</span><span class="sxs-lookup"><span data-stu-id="b0f39-296">Common input devices (joystick, mouse, etc.) implemented via Unity's input API.</span></span> |
| <span data-ttu-id="b0f39-297">MRTK/提供者</span><span class="sxs-lookup"><span data-stu-id="b0f39-297">MRTK/Providers</span></span> | | <span data-ttu-id="b0f39-298">平臺特定的資料提供者</span><span class="sxs-lookup"><span data-stu-id="b0f39-298">Platform specific data providers</span></span> |
| | <span data-ttu-id="b0f39-299">LeapMotion</span><span class="sxs-lookup"><span data-stu-id="b0f39-299">LeapMotion</span></span> | <span data-ttu-id="b0f39-300">UltraLeap Leap 移動控制器的支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-300">Support for the UltraLeap Leap Motion controller.</span></span> |
| | <span data-ttu-id="b0f39-301">OpenVR</span><span class="sxs-lookup"><span data-stu-id="b0f39-301">OpenVR</span></span> | <span data-ttu-id="b0f39-302">OpenVR 裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-302">Support for OpenVR devices.</span></span> |
| | <span data-ttu-id="b0f39-303">Oculus</span><span class="sxs-lookup"><span data-stu-id="b0f39-303">Oculus</span></span> | <span data-ttu-id="b0f39-304">Oculus 裝置的支援，例如尋找。</span><span class="sxs-lookup"><span data-stu-id="b0f39-304">Support for Oculus devices, such as the Quest.</span></span> |
| | [<span data-ttu-id="b0f39-305">UnityAR</span><span class="sxs-lookup"><span data-stu-id="b0f39-305">UnityAR</span></span>](../features/CameraSystem/UnityArCameraSettings.md) | <span data-ttu-id="b0f39-306"> (實驗性) 攝影機設定提供者，讓 MRTK 與行動 AR 裝置搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b0f39-306">(Experimental) Camera settings provider enabling MRTK use with mobile AR devices.</span></span> |
| | <span data-ttu-id="b0f39-307">WindowsMixedReality</span><span class="sxs-lookup"><span data-stu-id="b0f39-307">WindowsMixedReality</span></span> | <span data-ttu-id="b0f39-308">支援 Windows Mixed Reality 的裝置，包括 Microsoft HoloLens 和沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="b0f39-308">Support for Windows Mixed Reality devices, including Microsoft HoloLens and immersive headsets.</span></span> |
| | <span data-ttu-id="b0f39-309">Windows</span><span class="sxs-lookup"><span data-stu-id="b0f39-309">Windows</span></span> | <span data-ttu-id="b0f39-310">支援 Microsoft Windows 特定 Api，例如語音和聽寫。</span><span class="sxs-lookup"><span data-stu-id="b0f39-310">Support for Microsoft Windows specific APIs, for example speech and dictation.</span></span> |
| | <span data-ttu-id="b0f39-311">XR SDK</span><span class="sxs-lookup"><span data-stu-id="b0f39-311">XR SDK</span></span> | <span data-ttu-id="b0f39-312"> (unity 2019.3 和更新版本中 [unity 新 XR 架構](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的實驗性) 支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-312">(Experimental) Support for [Unity's new XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3 and newer.</span></span> |
| <span data-ttu-id="b0f39-313">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="b0f39-313">MRTK/SDK</span></span> | | |
| | <span data-ttu-id="b0f39-314">實驗</span><span class="sxs-lookup"><span data-stu-id="b0f39-314">Experimental</span></span> | <span data-ttu-id="b0f39-315">實驗性功能，包括著色器、使用者介面控制項和個別系統管理員。</span><span class="sxs-lookup"><span data-stu-id="b0f39-315">Experimental features, including shaders, user interface controls and individual system managers.</span></span> |
| | <span data-ttu-id="b0f39-316">功能</span><span class="sxs-lookup"><span data-stu-id="b0f39-316">Features</span></span> | <span data-ttu-id="b0f39-317">建基於基礎封裝的功能。</span><span class="sxs-lookup"><span data-stu-id="b0f39-317">Functionality that builds upon the Foundation package.</span></span> |
| | <span data-ttu-id="b0f39-318">Profiles</span><span class="sxs-lookup"><span data-stu-id="b0f39-318">Profiles</span></span> | <span data-ttu-id="b0f39-319">Microsoft Mixed Reality 工具組系統和服務的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="b0f39-319">Default profiles for the Microsoft Mixed Reality Toolkit systems and services.</span></span> |
| | <span data-ttu-id="b0f39-320">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="b0f39-320">StandardAssets</span></span> | <span data-ttu-id="b0f39-321">一般資產;模型、材質、材質等等。</span><span class="sxs-lookup"><span data-stu-id="b0f39-321">Common assets; models, textures, materials, etc.</span></span> |
| <span data-ttu-id="b0f39-322">MRTK/服務</span><span class="sxs-lookup"><span data-stu-id="b0f39-322">MRTK/Services</span></span> | | |
| | [<span data-ttu-id="b0f39-323">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-323">BoundarySystem</span></span>](../features/Boundary/BoundarySystemGettingStarted.md) | <span data-ttu-id="b0f39-324">執行 VR 界限支援的系統。</span><span class="sxs-lookup"><span data-stu-id="b0f39-324">System implementing VR boundary support.</span></span> |
| | [<span data-ttu-id="b0f39-325">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-325">CameraSystem</span></span>](../features/CameraSystem/CameraSystemOverview.md) | <span data-ttu-id="b0f39-326">系統執行攝影機設定和管理。</span><span class="sxs-lookup"><span data-stu-id="b0f39-326">System implementing camera configuration and management.</span></span> |
| | [<span data-ttu-id="b0f39-327">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-327">DiagnosticsSystem</span></span>](../features/Diagnostics/DiagnosticsSystemGettingStarted.md) | <span data-ttu-id="b0f39-328">在 application diagnostics 中執行的系統，例如 visual profiler。</span><span class="sxs-lookup"><span data-stu-id="b0f39-328">System implementing in application diagnostics, for example a visual profiler.</span></span> |
<span data-ttu-id="b0f39-329">?</span><span class="sxs-lookup"><span data-stu-id="b0f39-329">?</span></span> | [<span data-ttu-id="b0f39-330">InputSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-330">InputSystem</span></span>](../features/Input/Overview.md) | <span data-ttu-id="b0f39-331">系統，提供存取和處理使用者輸入的支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-331">System providing support for accessing and handling user input.</span></span> |
| | [<span data-ttu-id="b0f39-332">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-332">SceneSystem</span></span>](../features/SceneSystem/SceneSystemGettingStarted.md) | <span data-ttu-id="b0f39-333">提供多場景應用程式支援的系統。</span><span class="sxs-lookup"><span data-stu-id="b0f39-333">System providing multi-scene application support.</span></span> |
| | [<span data-ttu-id="b0f39-334">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-334">SpatialAwarenessSystem</span></span>](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md) | <span data-ttu-id="b0f39-335">提供使用者環境感知支援的系統。</span><span class="sxs-lookup"><span data-stu-id="b0f39-335">System providing support for awareness of the user's environment.</span></span> |
| | [<span data-ttu-id="b0f39-336">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="b0f39-336">TeleportSystem</span></span>](../features/TeleportSystem/Overview.md) | <span data-ttu-id="b0f39-337">提供 teleporting 支援的系統 (移至跳躍) 的體驗。</span><span class="sxs-lookup"><span data-stu-id="b0f39-337">System providing support for teleporting (moving about the experience in jumps).</span></span> |

<span data-ttu-id="b0f39-338">相依性：</span><span class="sxs-lookup"><span data-stu-id="b0f39-338">Dependencies:</span></span>

- <span data-ttu-id="b0f39-339">標準資產 (`com.microsoft.mixedreality.toolkit.standardassets`) </span><span class="sxs-lookup"><span data-stu-id="b0f39-339">Standard Assets (`com.microsoft.mixedreality.toolkit.standardassets`)</span></span>

### <a name="standard-assets"></a><span data-ttu-id="b0f39-340">標準資產</span><span class="sxs-lookup"><span data-stu-id="b0f39-340">Standard Assets</span></span>

<span data-ttu-id="b0f39-341">標準資產套件 (`com.microsoft.mixedreality.toolkit.standardassets)` 是針對所有混合現實體驗所建議的元件集合，包括：</span><span class="sxs-lookup"><span data-stu-id="b0f39-341">The standard assets package (`com.microsoft.mixedreality.toolkit.standardassets)` is a collection of components that are recommended for all mixed reality experiences, including:</span></span>

- <span data-ttu-id="b0f39-342">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="b0f39-342">MRTK Standard shader</span></span>
- <span data-ttu-id="b0f39-343">使用 MRTK 標準著色器的基本材質</span><span class="sxs-lookup"><span data-stu-id="b0f39-343">Basic materials using the MRTK Standard shader</span></span>
- <span data-ttu-id="b0f39-344">音訊檔案</span><span class="sxs-lookup"><span data-stu-id="b0f39-344">Audio files</span></span>
- <span data-ttu-id="b0f39-345">字型</span><span class="sxs-lookup"><span data-stu-id="b0f39-345">Fonts</span></span>
- <span data-ttu-id="b0f39-346">紋理</span><span class="sxs-lookup"><span data-stu-id="b0f39-346">Textures</span></span>
- <span data-ttu-id="b0f39-347">圖示</span><span class="sxs-lookup"><span data-stu-id="b0f39-347">Icons</span></span>

> [!Note]
> <span data-ttu-id="b0f39-348">為了避免根據元件定義的重大變更，標準資產套件中不包含用來控制 MRTK 標準著色器某些功能的腳本。</span><span class="sxs-lookup"><span data-stu-id="b0f39-348">To avoid breaking changes based on assembly definitions, the scripts used to control some features of the MRTK Standard shader are not included in the standard assets package.</span></span> <span data-ttu-id="b0f39-349">您可以在資料夾的基礎套件中找到這些腳本 `MRTK/Core/Utilities/StandardShader` 。</span><span class="sxs-lookup"><span data-stu-id="b0f39-349">These scripts can be found in the foundation package in the `MRTK/Core/Utilities/StandardShader` folder.</span></span>

<span data-ttu-id="b0f39-350">相依性：無</span><span class="sxs-lookup"><span data-stu-id="b0f39-350">Dependencies: none</span></span>

### <a name="extension-packages"></a><span data-ttu-id="b0f39-351">擴充套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-351">Extension packages</span></span>

<span data-ttu-id="b0f39-352">選用的擴充套件 (`com.microsoft.mixedreality.toolkit.extensions)` 包含擴充 MRTK 功能的其他元件。</span><span class="sxs-lookup"><span data-stu-id="b0f39-352">The optional extensions package (`com.microsoft.mixedreality.toolkit.extensions)` contains additional components that expand the functionality of the MRTK.</span></span>

| <span data-ttu-id="b0f39-353">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-353">Folder</span></span> | <span data-ttu-id="b0f39-354">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-354">Component</span></span> | <span data-ttu-id="b0f39-355">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-355">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-356">MRTK/擴充功能</span><span class="sxs-lookup"><span data-stu-id="b0f39-356">MRTK/Extensions</span></span> | |
| | [<span data-ttu-id="b0f39-357">HandPhysicsService</span><span class="sxs-lookup"><span data-stu-id="b0f39-357">HandPhysicsService</span></span>](../features/Extensions/HandPhysicsService/HandPhysicsServiceOverview.md) | <span data-ttu-id="b0f39-358">將物理支援新增至明確表述的服務。</span><span class="sxs-lookup"><span data-stu-id="b0f39-358">Service that adds physics support to articulated hands.</span></span> |
| | <span data-ttu-id="b0f39-359">LostTrackingService</span><span class="sxs-lookup"><span data-stu-id="b0f39-359">LostTrackingService</span></span> | <span data-ttu-id="b0f39-360">這項服務可簡化 Microsoft HoloLens 裝置上的追蹤遺失處理。</span><span class="sxs-lookup"><span data-stu-id="b0f39-360">Service that simplifies handing of tracking loss on Microsoft HoloLens devices.</span></span> |
| | [<span data-ttu-id="b0f39-361">SceneTransitionService</span><span class="sxs-lookup"><span data-stu-id="b0f39-361">SceneTransitionService</span></span>](../features/Extensions/SceneTransitionService/SceneTransitionServiceOverview.md) | <span data-ttu-id="b0f39-362">簡化加入平滑場景轉換的服務。</span><span class="sxs-lookup"><span data-stu-id="b0f39-362">Service that simplifies adding smooth scene transitions.</span></span> |
| | <span data-ttu-id="b0f39-363">範例 ~</span><span class="sxs-lookup"><span data-stu-id="b0f39-363">Samples~</span></span> | <span data-ttu-id="b0f39-364">Unity 編輯器中隱藏的 () 資料夾，其中包含範例場景和資產。</span><span class="sxs-lookup"><span data-stu-id="b0f39-364">A hidden (in the Unity Editor) folder that contains the sample scenes and assets.</span></span> |

<span data-ttu-id="b0f39-365">如需使用包含範例專案之封裝的詳細資訊，請參閱 [混合現實工具組和 Unity 封裝管理員](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 文章。</span><span class="sxs-lookup"><span data-stu-id="b0f39-365">More details on the process of using packages containing example projects can be found in the [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) article.</span></span>

<span data-ttu-id="b0f39-366">相依性：</span><span class="sxs-lookup"><span data-stu-id="b0f39-366">Dependencies:</span></span>

- <span data-ttu-id="b0f39-367">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="b0f39-367">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="tools-package"></a><span data-ttu-id="b0f39-368">工具套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-368">Tools package</span></span>

<span data-ttu-id="b0f39-369">選用的工具套件 (`com.microsoft.mixedreality.toolkit.tools)` 包含適用于建立混合現實體驗的工具。</span><span class="sxs-lookup"><span data-stu-id="b0f39-369">The optional tools package (`com.microsoft.mixedreality.toolkit.tools)` contains tools that are useful for creating mixed reality experiences.</span></span> <span data-ttu-id="b0f39-370">一般而言，這些工具是編輯器元件，而其程式碼不會隨附于應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="b0f39-370">In general, these tools are editor components and their code does not ship as part of an application.</span></span>

| <span data-ttu-id="b0f39-371">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-371">Folder</span></span> | <span data-ttu-id="b0f39-372">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-372">Component</span></span> | <span data-ttu-id="b0f39-373">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-373">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-374">MRTK/工具</span><span class="sxs-lookup"><span data-stu-id="b0f39-374">MRTK/Tools</span></span> | |
| | <span data-ttu-id="b0f39-375">BuildWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-375">BuildWindow</span></span> | <span data-ttu-id="b0f39-376">這項工具可協助簡化建立和部署 UWP 應用程式的流程。</span><span class="sxs-lookup"><span data-stu-id="b0f39-376">Tool that helps simplify the process of building and deploying UWP applications.</span></span> |
| | [<span data-ttu-id="b0f39-377">DependencyWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-377">DependencyWindow</span></span>](../features/Tools/DependencyWindow.md) | <span data-ttu-id="b0f39-378">此工具會在專案中建立資產的相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="b0f39-378">Tool that creates a dependency graph of assets in a project.</span></span> |
| | [<span data-ttu-id="b0f39-379">ExtensionServiceCreator</span><span class="sxs-lookup"><span data-stu-id="b0f39-379">ExtensionServiceCreator</span></span>](../features/Tools/ExtensionServiceCreationWizard.md) | <span data-ttu-id="b0f39-380">協助建立延伸模組服務的 Wizard。</span><span class="sxs-lookup"><span data-stu-id="b0f39-380">Wizard to assist in creating extension services.</span></span> |
| | [<span data-ttu-id="b0f39-381">MigrationWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-381">MigrationWindow</span></span>](../features/Tools/MigrationWindow.md) | <span data-ttu-id="b0f39-382">協助更新使用已淘汰 MRTK 元件之程式碼的工具。</span><span class="sxs-lookup"><span data-stu-id="b0f39-382">Tool that assists in updating code that uses deprecated MRTK components.</span></span>  |
| | [<span data-ttu-id="b0f39-383">OptimizeWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-383">OptimizeWindow</span></span>](../features/Tools/OptimizeWindow.md) | <span data-ttu-id="b0f39-384">此公用程式可協助您自動設定混合現實專案，以獲得 Unity 的最佳效能。</span><span class="sxs-lookup"><span data-stu-id="b0f39-384">Utility to help automate configuring a mixed reality project for the best performance in Unity.</span></span> |
| | <span data-ttu-id="b0f39-385">ReserializeAssetsUtility</span><span class="sxs-lookup"><span data-stu-id="b0f39-385">ReserializeAssetsUtility</span></span> | <span data-ttu-id="b0f39-386">提供 reserializing 特定 Unity 檔案的支援。</span><span class="sxs-lookup"><span data-stu-id="b0f39-386">Provides support for reserializing specific Unity files.</span></span> |
| | [<span data-ttu-id="b0f39-387">RuntimeTools/Tools/ControllerMappingTool</span><span class="sxs-lookup"><span data-stu-id="b0f39-387">RuntimeTools/Tools/ControllerMappingTool</span></span>](../features/Tools/ControllerMappingTool.md) | <span data-ttu-id="b0f39-388">此公用程式可讓開發人員快速判斷硬體控制器的 Unity 對應。</span><span class="sxs-lookup"><span data-stu-id="b0f39-388">Utility enabling developers to quickly determine Unity mappings for hardware controllers.</span></span> |
| | <span data-ttu-id="b0f39-389">ScreenshotUtility</span><span class="sxs-lookup"><span data-stu-id="b0f39-389">ScreenshotUtility</span></span> | <span data-ttu-id="b0f39-390">在 Unity 編輯器中啟用捕獲應用程式映射。</span><span class="sxs-lookup"><span data-stu-id="b0f39-390">Enables capturing application images in the Unity editor.</span></span> |
| | <span data-ttu-id="b0f39-391">TextureCombinerWindow</span><span class="sxs-lookup"><span data-stu-id="b0f39-391">TextureCombinerWindow</span></span> | <span data-ttu-id="b0f39-392">結合圖形材質的公用程式。</span><span class="sxs-lookup"><span data-stu-id="b0f39-392">Utility to combine graphics textures.</span></span> |
| | [<span data-ttu-id="b0f39-393">工具箱</span><span class="sxs-lookup"><span data-stu-id="b0f39-393">Toolbox</span></span>](../features/README_Toolbox.md) | <span data-ttu-id="b0f39-394">可讓您輕鬆地探索及使用 MRTK UX 元件的 UI。</span><span class="sxs-lookup"><span data-stu-id="b0f39-394">UI that makes it easy to discover and use MRTK UX components.</span></span> |

<span data-ttu-id="b0f39-395">相依性：</span><span class="sxs-lookup"><span data-stu-id="b0f39-395">Dependencies:</span></span>

- <span data-ttu-id="b0f39-396">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="b0f39-396">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="test-utilities-package"></a><span data-ttu-id="b0f39-397">測試公用程式套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-397">Test utilities package</span></span>

<span data-ttu-id="b0f39-398">選用的測試公用程式套件 (`com.microsoft.mixedreality.toolkit.testutilities`) 包含協助程式腳本的集合，可讓開發人員輕鬆地建立播放模式測試。</span><span class="sxs-lookup"><span data-stu-id="b0f39-398">The optional test utilities package (`com.microsoft.mixedreality.toolkit.testutilities`) contains a collection of helper scripts that enable developers to easily create play mode tests.</span></span> <span data-ttu-id="b0f39-399">這些公用程式特別適用于建立 MRTK 元件的開發人員。</span><span class="sxs-lookup"><span data-stu-id="b0f39-399">These utilities are especially useful for developers creating MRTK components.</span></span>

| <span data-ttu-id="b0f39-400">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-400">Folder</span></span> | <span data-ttu-id="b0f39-401">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-401">Component</span></span> | <span data-ttu-id="b0f39-402">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-402">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-403">MRTK/測試</span><span class="sxs-lookup"><span data-stu-id="b0f39-403">MRTK/Tests</span></span> | |
| | <span data-ttu-id="b0f39-404">TestUtilities</span><span class="sxs-lookup"><span data-stu-id="b0f39-404">TestUtilities</span></span> | <span data-ttu-id="b0f39-405">簡化播放模式測試建立的方法，包括手動模擬公用程式。</span><span class="sxs-lookup"><span data-stu-id="b0f39-405">Methods to simplify creation of play mode tests, including hand simulation utilities.</span></span> |
<span data-ttu-id="b0f39-406">相依性：</span><span class="sxs-lookup"><span data-stu-id="b0f39-406">Dependencies:</span></span>

- <span data-ttu-id="b0f39-407">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="b0f39-407">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="examples-package"></a><span data-ttu-id="b0f39-408">範例套件</span><span class="sxs-lookup"><span data-stu-id="b0f39-408">Examples package</span></span>

<span data-ttu-id="b0f39-409">範例封裝 (`com.microsoft.mixedreality.toolkit.examples`) ，其結構化可讓開發人員只匯入感興趣的範例。</span><span class="sxs-lookup"><span data-stu-id="b0f39-409">The examples package (`com.microsoft.mixedreality.toolkit.examples`), is structured to allow developers to import only the examples of interest.</span></span>

<span data-ttu-id="b0f39-410">如需使用包含範例專案之封裝的詳細資訊，請參閱 [混合現實工具組和 Unity 封裝管理員](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 文章。</span><span class="sxs-lookup"><span data-stu-id="b0f39-410">More details on the process of using packages containing example projects can be found in the [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) article.</span></span>

| <span data-ttu-id="b0f39-411">資料夾</span><span class="sxs-lookup"><span data-stu-id="b0f39-411">Folder</span></span> | <span data-ttu-id="b0f39-412">元件</span><span class="sxs-lookup"><span data-stu-id="b0f39-412">Component</span></span> | <span data-ttu-id="b0f39-413">描述</span><span class="sxs-lookup"><span data-stu-id="b0f39-413">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b0f39-414">MRTK/範例</span><span class="sxs-lookup"><span data-stu-id="b0f39-414">MRTK/Examples</span></span> | | |
| | <span data-ttu-id="b0f39-415">範例 ~</span><span class="sxs-lookup"><span data-stu-id="b0f39-415">Samples~</span></span> | <span data-ttu-id="b0f39-416">Unity 編輯器中隱藏的 () 資料夾，其中包含範例場景和資產。</span><span class="sxs-lookup"><span data-stu-id="b0f39-416">A hidden (in the Unity Editor) folder that contains the sample scenes and assets.</span></span> |
| | <span data-ttu-id="b0f39-417">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="b0f39-417">StandardAssets</span></span> | <span data-ttu-id="b0f39-418">多個示範場景所共用的常見資產。</span><span class="sxs-lookup"><span data-stu-id="b0f39-418">Common assets shared by multiple demo scenes.</span></span> |

<span data-ttu-id="b0f39-419">相依性：</span><span class="sxs-lookup"><span data-stu-id="b0f39-419">Dependencies:</span></span>

- <span data-ttu-id="b0f39-420">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="b0f39-420">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>
- <span data-ttu-id="b0f39-421">擴充 (`com.microsoft.mixedreality.toolkit.extensions`)</span><span class="sxs-lookup"><span data-stu-id="b0f39-421">Extensions (`com.microsoft.mixedreality.toolkit.extensions`)</span></span>

## <a name="see-also"></a><span data-ttu-id="b0f39-422">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0f39-422">See also</span></span>

- [<span data-ttu-id="b0f39-423">架構概觀</span><span class="sxs-lookup"><span data-stu-id="b0f39-423">Architecture Overview</span></span>](../Architecture/Overview.md)
- [<span data-ttu-id="b0f39-424">系統、延伸模組服務和資料提供者</span><span class="sxs-lookup"><span data-stu-id="b0f39-424">Systems, Extension Services and Data Providers</span></span>](../Architecture/SystemsExtensionsProviders.md)
- [<span data-ttu-id="b0f39-425">混合現實工具組和 Unity 封裝管理員</span><span class="sxs-lookup"><span data-stu-id="b0f39-425">Mixed Reality Toolkit and Unity Package Manager</span></span>](../configuration/usingupm.md)
