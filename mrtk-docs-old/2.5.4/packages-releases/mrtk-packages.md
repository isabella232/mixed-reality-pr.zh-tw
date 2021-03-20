---
title: MRTK_Pakages
description: MRTK 中的套件支援混合現實硬體和平臺。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Unity Pakage Manager、
ms.openlocfilehash: 7a3099342c7de3ac84df67737b6c7353e106dddc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686031"
---
# <a name="mixed-reality-toolkit-packages"></a><span data-ttu-id="08357-104">混合現實工具組套件</span><span class="sxs-lookup"><span data-stu-id="08357-104">Mixed Reality Toolkit packages</span></span>

<span data-ttu-id="08357-105"> (MRTK) 的混合現實工具組是封裝的集合，可提供混合現實硬體和平臺的支援，藉此啟用跨平臺混合現實應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="08357-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms.</span></span>

<span data-ttu-id="08357-106">MRTK 可作為 [資產](#asset-packages) ( unitypackage) 套件和透過 [Unity 封裝管理員](#unity-package-manager)。</span><span class="sxs-lookup"><span data-stu-id="08357-106">MRTK is available as [asset](#asset-packages) (.unitypackage) packages and via the [Unity Package Manager](#unity-package-manager).</span></span>

## <a name="asset-packages"></a><span data-ttu-id="08357-107">資產套件</span><span class="sxs-lookup"><span data-stu-id="08357-107">Asset packages</span></span>

<span data-ttu-id="08357-108">您可以從 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)下載 MRTK 資產 (. unitypackage) 。</span><span class="sxs-lookup"><span data-stu-id="08357-108">The MRTK asset (.unitypackage) can be downloaded from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span>

<span data-ttu-id="08357-109">使用資產套件的一些優點包括：</span><span class="sxs-lookup"><span data-stu-id="08357-109">Some of the benefits of using asset packages include:</span></span>

- <span data-ttu-id="08357-110">適用于 Unity 2018.4 和更新版本</span><span class="sxs-lookup"><span data-stu-id="08357-110">Available for Unity 2018.4 and newer</span></span>
- <span data-ttu-id="08357-111">輕鬆變更 MRTK</span><span class="sxs-lookup"><span data-stu-id="08357-111">Easy to make changes to MRTK</span></span>
  - <span data-ttu-id="08357-112">MRTK 在 [資產] 資料夾中</span><span class="sxs-lookup"><span data-stu-id="08357-112">MRTK is in the Assets folder</span></span>

<span data-ttu-id="08357-113">其中一些挑戰如下：</span><span class="sxs-lookup"><span data-stu-id="08357-113">Some of the challenges are:</span></span>

- <span data-ttu-id="08357-114">MRTK 是專案 [資產] 資料夾的一部分，</span><span class="sxs-lookup"><span data-stu-id="08357-114">MRTK is part of the project's Assets folder, leading to</span></span>
  - <span data-ttu-id="08357-115">較大型的專案</span><span class="sxs-lookup"><span data-stu-id="08357-115">Larger projects</span></span>
  - <span data-ttu-id="08357-116">較慢的編譯時間</span><span class="sxs-lookup"><span data-stu-id="08357-116">Slower compilation times</span></span>
- <span data-ttu-id="08357-117">無相依性管理</span><span class="sxs-lookup"><span data-stu-id="08357-117">No dependency management</span></span>
  - <span data-ttu-id="08357-118">客戶必須手動解析套件相依性</span><span class="sxs-lookup"><span data-stu-id="08357-118">Customers are required to resolve package dependencies manually</span></span>
- <span data-ttu-id="08357-119">手動更新程式</span><span class="sxs-lookup"><span data-stu-id="08357-119">Manual update process</span></span>
  - <span data-ttu-id="08357-120">多個步驟</span><span class="sxs-lookup"><span data-stu-id="08357-120">Multiple steps</span></span>
  - <span data-ttu-id="08357-121">大型 (3000 + 檔案) 原始檔控制更新</span><span class="sxs-lookup"><span data-stu-id="08357-121">Large (3000+ file) source control updates</span></span>
  - <span data-ttu-id="08357-122">遺失對 MRTK 進行變更的風險</span><span class="sxs-lookup"><span data-stu-id="08357-122">Risk of losing changes made to MRTK</span></span>
- <span data-ttu-id="08357-123">匯入範例封裝通常表示包含所有範例</span><span class="sxs-lookup"><span data-stu-id="08357-123">Importing the examples package typically means including all examples</span></span>

<span data-ttu-id="08357-124">可用的封裝如下：</span><span class="sxs-lookup"><span data-stu-id="08357-124">The available packages are:</span></span>

- [<span data-ttu-id="08357-125">基礎</span><span class="sxs-lookup"><span data-stu-id="08357-125">Foundation</span></span>](#foundation-package)
- [<span data-ttu-id="08357-126">擴充功能</span><span class="sxs-lookup"><span data-stu-id="08357-126">Extensions</span></span>](#extensions-package)
- [<span data-ttu-id="08357-127">工具</span><span class="sxs-lookup"><span data-stu-id="08357-127">Tools</span></span>](#tools-package)
- [<span data-ttu-id="08357-128">測試公用程式</span><span class="sxs-lookup"><span data-stu-id="08357-128">Test utilities</span></span>](#test-utilities-package)
- [<span data-ttu-id="08357-129">範例</span><span class="sxs-lookup"><span data-stu-id="08357-129">Examples</span></span>](#examples-package)

<span data-ttu-id="08357-130">Microsoft 會從 GitHub 上 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) 分支中的原始程式碼發行並支援這些套件。</span><span class="sxs-lookup"><span data-stu-id="08357-130">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

### <a name="foundation-package"></a><span data-ttu-id="08357-131">基礎封裝</span><span class="sxs-lookup"><span data-stu-id="08357-131">Foundation package</span></span>

<span data-ttu-id="08357-132">混合現實工具組基礎是一組程式碼，可讓您的應用程式跨混合現實平臺運用一般功能。</span><span class="sxs-lookup"><span data-stu-id="08357-132">The Mixed Reality Toolkit Foundation is the set of code that enables your application to leverage common functionality across Mixed Reality Platforms.</span></span>

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<span data-ttu-id="08357-133"><sup>MRTK 基礎封裝</sup></span><span class="sxs-lookup"><span data-stu-id="08357-133"><sup>MRTK Foundation Package</sup></span></span>

<span data-ttu-id="08357-134">MRTK Foundation 套件包含下列各項。</span><span class="sxs-lookup"><span data-stu-id="08357-134">The MRTK Foundation package contains the following.</span></span>

| <span data-ttu-id="08357-135">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-135">Folder</span></span> | <span data-ttu-id="08357-136">元件</span><span class="sxs-lookup"><span data-stu-id="08357-136">Component</span></span> | <span data-ttu-id="08357-137">描述</span><span class="sxs-lookup"><span data-stu-id="08357-137">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-138">MRTK/核心</span><span class="sxs-lookup"><span data-stu-id="08357-138">MRTK/Core</span></span> | | <span data-ttu-id="08357-139">介面和類型定義、基類、標準著色器。</span><span class="sxs-lookup"><span data-stu-id="08357-139">Interface and type definitions, base classes, standard shader.</span></span> |
| <span data-ttu-id="08357-140">MRTK/核心/提供者</span><span class="sxs-lookup"><span data-stu-id="08357-140">MRTK/Core/Providers</span></span> | | <span data-ttu-id="08357-141">平臺中立的資料提供者</span><span class="sxs-lookup"><span data-stu-id="08357-141">Platform agnostic data providers</span></span> |
| | <span data-ttu-id="08357-142">手</span><span class="sxs-lookup"><span data-stu-id="08357-142">Hands</span></span> | <span data-ttu-id="08357-143">用於手動追蹤的基類支援和服務。</span><span class="sxs-lookup"><span data-stu-id="08357-143">Base class support and services for hand tracking.</span></span> |
| | [<span data-ttu-id="08357-144">InputAnimation</span><span class="sxs-lookup"><span data-stu-id="08357-144">InputAnimation</span></span>](../features/input-simulation/input-animation-recording.md) | <span data-ttu-id="08357-145">支援錄製 head 移動和手追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="08357-145">Support for recording head movement and hand tracking data.</span></span> |
| | [<span data-ttu-id="08357-146">InputSimulation</span><span class="sxs-lookup"><span data-stu-id="08357-146">InputSimulation</span></span>](../features/input-simulation/input-simulation-service.md) | <span data-ttu-id="08357-147">支援手形和眼睛輸入的編輯器內模擬。</span><span class="sxs-lookup"><span data-stu-id="08357-147">Support for in-editor simulation of hand and eye input.</span></span> |
| | [<span data-ttu-id="08357-148">ObjectMeshObserver</span><span class="sxs-lookup"><span data-stu-id="08357-148">ObjectMeshObserver</span></span>](../features/spatial-awareness/spatial-object-mesh-observer.md) | <span data-ttu-id="08357-149">空間感知觀察者使用3D 模型做為資料。</span><span class="sxs-lookup"><span data-stu-id="08357-149">Spatial awareness observer using a 3D model as the data.</span></span> |
| | <span data-ttu-id="08357-150">UnityInput</span><span class="sxs-lookup"><span data-stu-id="08357-150">UnityInput</span></span> | <span data-ttu-id="08357-151">一般輸入裝置 (搖桿、滑鼠等 ) 透過 Unity 的輸入 API 來執行。</span><span class="sxs-lookup"><span data-stu-id="08357-151">Common input devices (joystick, mouse, etc.) implemented via Unity's input API.</span></span> |
| <span data-ttu-id="08357-152">MRTK/提供者</span><span class="sxs-lookup"><span data-stu-id="08357-152">MRTK/Providers</span></span> | | <span data-ttu-id="08357-153">平臺特定的資料提供者</span><span class="sxs-lookup"><span data-stu-id="08357-153">Platform specific data providers</span></span> |
| | <span data-ttu-id="08357-154">LeapMotion</span><span class="sxs-lookup"><span data-stu-id="08357-154">LeapMotion</span></span> | <span data-ttu-id="08357-155">UltraLeap Leap 移動控制器的支援。</span><span class="sxs-lookup"><span data-stu-id="08357-155">Support for the UltraLeap Leap Motion controller.</span></span> |
| | <span data-ttu-id="08357-156">OpenVR</span><span class="sxs-lookup"><span data-stu-id="08357-156">OpenVR</span></span> | <span data-ttu-id="08357-157">OpenVR 裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="08357-157">Support for OpenVR devices.</span></span> |
| | <span data-ttu-id="08357-158">Oculus</span><span class="sxs-lookup"><span data-stu-id="08357-158">Oculus</span></span> | <span data-ttu-id="08357-159">Oculus 裝置的支援，例如尋找。</span><span class="sxs-lookup"><span data-stu-id="08357-159">Support for Oculus devices, such as the Quest.</span></span> |
| | [<span data-ttu-id="08357-160">UnityAR</span><span class="sxs-lookup"><span data-stu-id="08357-160">UnityAR</span></span>](../features/camera-system/unity-ar-camera-settings.md) | <span data-ttu-id="08357-161"> (實驗性) 攝影機設定提供者，讓 MRTK 與行動 AR 裝置搭配使用。</span><span class="sxs-lookup"><span data-stu-id="08357-161">(Experimental) Camera settings provider enabling MRTK use with mobile AR devices.</span></span> |
| | <span data-ttu-id="08357-162">WindowsMixedReality</span><span class="sxs-lookup"><span data-stu-id="08357-162">WindowsMixedReality</span></span> | <span data-ttu-id="08357-163">支援 Windows Mixed Reality 的裝置，包括 Microsoft HoloLens 和沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="08357-163">Support for Windows Mixed Reality devices, including Microsoft HoloLens and immersive headsets.</span></span> |
| | <span data-ttu-id="08357-164">Windows</span><span class="sxs-lookup"><span data-stu-id="08357-164">Windows</span></span> | <span data-ttu-id="08357-165">支援 Microsoft Windows 特定 Api，例如語音和聽寫。</span><span class="sxs-lookup"><span data-stu-id="08357-165">Support for Microsoft Windows specific APIs, for example speech and dictation.</span></span> |
| | <span data-ttu-id="08357-166">XR SDK</span><span class="sxs-lookup"><span data-stu-id="08357-166">XR SDK</span></span> | <span data-ttu-id="08357-167"> (unity 2019.3 和更新版本中 [unity 新 XR 架構](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的實驗性) 支援。</span><span class="sxs-lookup"><span data-stu-id="08357-167">(Experimental) Support for [Unity's new XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3 and newer.</span></span> |
| <span data-ttu-id="08357-168">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="08357-168">MRTK/SDK</span></span> | | |
| | <span data-ttu-id="08357-169">實驗</span><span class="sxs-lookup"><span data-stu-id="08357-169">Experimental</span></span> | <span data-ttu-id="08357-170">實驗性功能，包括著色器、使用者介面控制項和個別系統管理員。</span><span class="sxs-lookup"><span data-stu-id="08357-170">Experimental features, including shaders, user interface controls and individual system managers.</span></span> |
| | <span data-ttu-id="08357-171">功能</span><span class="sxs-lookup"><span data-stu-id="08357-171">Features</span></span> | <span data-ttu-id="08357-172">建基於基礎封裝的功能。</span><span class="sxs-lookup"><span data-stu-id="08357-172">Functionality that builds upon the Foundation package.</span></span> |
| | <span data-ttu-id="08357-173">Profiles</span><span class="sxs-lookup"><span data-stu-id="08357-173">Profiles</span></span> | <span data-ttu-id="08357-174">Microsoft Mixed Reality 工具組系統和服務的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="08357-174">Default profiles for the Microsoft Mixed Reality Toolkit systems and services.</span></span> |
| | <span data-ttu-id="08357-175">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="08357-175">StandardAssets</span></span> | <span data-ttu-id="08357-176">一般資產;模型、材質、材質等等。</span><span class="sxs-lookup"><span data-stu-id="08357-176">Common assets; models, textures, materials, etc.</span></span> |
| <span data-ttu-id="08357-177">MRTK/SceneSystemResources</span><span class="sxs-lookup"><span data-stu-id="08357-177">MRTK/SceneSystemResources</span></span> | | <span data-ttu-id="08357-178">場景系統使用的資產和資源</span><span class="sxs-lookup"><span data-stu-id="08357-178">Assets and resources used by the Scene System</span></span> |
| <span data-ttu-id="08357-179">MRTK/服務</span><span class="sxs-lookup"><span data-stu-id="08357-179">MRTK/Services</span></span> | | |
| | [<span data-ttu-id="08357-180">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="08357-180">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md) | <span data-ttu-id="08357-181">執行 VR 界限支援的系統。</span><span class="sxs-lookup"><span data-stu-id="08357-181">System implementing VR boundary support.</span></span> |
| | [<span data-ttu-id="08357-182">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="08357-182">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md) | <span data-ttu-id="08357-183">系統執行攝影機設定和管理。</span><span class="sxs-lookup"><span data-stu-id="08357-183">System implementing camera configuration and management.</span></span> |
| | [<span data-ttu-id="08357-184">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="08357-184">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md) | <span data-ttu-id="08357-185">在 application diagnostics 中執行的系統，例如 visual profiler。</span><span class="sxs-lookup"><span data-stu-id="08357-185">System implementing in application diagnostics, for example a visual profiler.</span></span> |
| | [<span data-ttu-id="08357-186">InputSystem</span><span class="sxs-lookup"><span data-stu-id="08357-186">InputSystem</span></span>](../features/input/overview.md) | <span data-ttu-id="08357-187">系統，提供存取和處理使用者輸入的支援。</span><span class="sxs-lookup"><span data-stu-id="08357-187">System providing support for accessing and handling user input.</span></span> |
| | [<span data-ttu-id="08357-188">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="08357-188">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md) | <span data-ttu-id="08357-189">提供多場景應用程式支援的系統。</span><span class="sxs-lookup"><span data-stu-id="08357-189">System providing multi-scene application support.</span></span> |
| | [<span data-ttu-id="08357-190">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="08357-190">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md) | <span data-ttu-id="08357-191">提供使用者環境感知支援的系統。</span><span class="sxs-lookup"><span data-stu-id="08357-191">System providing support for awareness of the user's environment.</span></span> |
| | [<span data-ttu-id="08357-192">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="08357-192">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md) | <span data-ttu-id="08357-193">提供 teleporting 支援的系統 (移至跳躍) 的體驗。</span><span class="sxs-lookup"><span data-stu-id="08357-193">System providing support for teleporting (moving about the experience in jumps).</span></span> |
| <span data-ttu-id="08357-194">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="08357-194">MRTK/StandardAssets</span></span> | | <span data-ttu-id="08357-195">混合現實體驗的 MRTK 標準著色器、基本材質和其他標準資產</span><span class="sxs-lookup"><span data-stu-id="08357-195">MRTK Standard shader, basic materials and other standard assets for mixed reality experiences</span></span> |

### <a name="extensions-package"></a><span data-ttu-id="08357-196">擴充功能套件</span><span class="sxs-lookup"><span data-stu-id="08357-196">Extensions package</span></span>

<span data-ttu-id="08357-197">選用的 MixedRealityToolkit 套件包含擴充 Microsoft Mixed Reality 工具組功能的其他服務。</span><span class="sxs-lookup"><span data-stu-id="08357-197">The optional Microsoft.MixedRealityToolkit.Unity.Extensions package includes additional services that extend the functionality of the Microsoft Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="08357-198">延伸模組套件需要 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="08357-198">The extensions package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="08357-199">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-199">Folder</span></span> | <span data-ttu-id="08357-200">元件</span><span class="sxs-lookup"><span data-stu-id="08357-200">Component</span></span> | <span data-ttu-id="08357-201">描述</span><span class="sxs-lookup"><span data-stu-id="08357-201">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-202">MRTK/擴充功能</span><span class="sxs-lookup"><span data-stu-id="08357-202">MRTK/Extensions</span></span> | |
| | [<span data-ttu-id="08357-203">HandPhysicsService</span><span class="sxs-lookup"><span data-stu-id="08357-203">HandPhysicsService</span></span>](../features/extensions/hand-physics-service.md) | <span data-ttu-id="08357-204">將物理支援新增至明確表述的服務。</span><span class="sxs-lookup"><span data-stu-id="08357-204">Service that adds physics support to articulated hands.</span></span> |
| | <span data-ttu-id="08357-205">LostTrackingService</span><span class="sxs-lookup"><span data-stu-id="08357-205">LostTrackingService</span></span> | <span data-ttu-id="08357-206">這項服務可簡化 Microsoft HoloLens 裝置上的追蹤遺失處理。</span><span class="sxs-lookup"><span data-stu-id="08357-206">Service that simplifies handling of tracking loss on Microsoft HoloLens devices.</span></span> |
| | [<span data-ttu-id="08357-207">SceneTransitionService</span><span class="sxs-lookup"><span data-stu-id="08357-207">SceneTransitionService</span></span>](../features/extensions/scene-transition-service.md) | <span data-ttu-id="08357-208">簡化加入平滑場景轉換的服務。</span><span class="sxs-lookup"><span data-stu-id="08357-208">Service that simplifies adding smooth scene transitions.</span></span> |

### <a name="tools-package"></a><span data-ttu-id="08357-209">工具套件</span><span class="sxs-lookup"><span data-stu-id="08357-209">Tools package</span></span>

<span data-ttu-id="08357-210">選用的 MixedRealityToolkit 套件包含實用的工具，可使用 Microsoft Mixed Reality 工具組強化混合現實開發體驗。</span><span class="sxs-lookup"><span data-stu-id="08357-210">The optional Microsoft.MixedRealityToolkit.Unity.Tools package includes helpful tools that enhance the mixed reality development experience using the Microsoft Mixed Reality Toolkit.</span></span>
<span data-ttu-id="08357-211">這些工具位於 Unity 編輯器中的 **混合現實工具組 > 公用程式** 功能表。</span><span class="sxs-lookup"><span data-stu-id="08357-211">These tools are located in the **Mixed Reality Toolkit > Utilities** menu in the Unity Editor.</span></span>

> [!NOTE]
> <span data-ttu-id="08357-212">此工具套件需要 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="08357-212">The tools package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="08357-213">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-213">Folder</span></span> | <span data-ttu-id="08357-214">元件</span><span class="sxs-lookup"><span data-stu-id="08357-214">Component</span></span> | <span data-ttu-id="08357-215">描述</span><span class="sxs-lookup"><span data-stu-id="08357-215">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-216">MRTK/工具</span><span class="sxs-lookup"><span data-stu-id="08357-216">MRTK/Tools</span></span> | |
| | <span data-ttu-id="08357-217">BuildWindow</span><span class="sxs-lookup"><span data-stu-id="08357-217">BuildWindow</span></span> | <span data-ttu-id="08357-218">這項工具可協助簡化建立和部署 UWP 應用程式的流程。</span><span class="sxs-lookup"><span data-stu-id="08357-218">Tool that helps simplify the process of building and deploying UWP applications.</span></span> |
| | [<span data-ttu-id="08357-219">DependencyWindow</span><span class="sxs-lookup"><span data-stu-id="08357-219">DependencyWindow</span></span>](../features/tools/dependency-window.md) | <span data-ttu-id="08357-220">此工具會在專案中建立資產的相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="08357-220">Tool that creates a dependency graph of assets in a project.</span></span> |
| | [<span data-ttu-id="08357-221">ExtensionServiceCreator</span><span class="sxs-lookup"><span data-stu-id="08357-221">ExtensionServiceCreator</span></span>](../features/tools/extension-service-creation-wizard.md) | <span data-ttu-id="08357-222">協助建立延伸模組服務的 Wizard。</span><span class="sxs-lookup"><span data-stu-id="08357-222">Wizard to assist in creating extension services.</span></span> |
| | [<span data-ttu-id="08357-223">MigrationWindow</span><span class="sxs-lookup"><span data-stu-id="08357-223">MigrationWindow</span></span>](../features/tools/migration-window.md) | <span data-ttu-id="08357-224">協助更新使用已淘汰 MRTK 元件之程式碼的工具。</span><span class="sxs-lookup"><span data-stu-id="08357-224">Tool that assists in updating code that uses deprecated MRTK components.</span></span>  |
| | [<span data-ttu-id="08357-225">OptimizeWindow</span><span class="sxs-lookup"><span data-stu-id="08357-225">OptimizeWindow</span></span>](../features/tools/optimize-window.md) | <span data-ttu-id="08357-226">此公用程式可協助您自動設定混合現實專案，以獲得 Unity 的最佳效能。</span><span class="sxs-lookup"><span data-stu-id="08357-226">Utility to help automate configuring a mixed reality project for the best performance in Unity.</span></span> |
| | <span data-ttu-id="08357-227">ReserializeAssetsUtility</span><span class="sxs-lookup"><span data-stu-id="08357-227">ReserializeAssetsUtility</span></span> | <span data-ttu-id="08357-228">提供 reserializing 特定 Unity 檔案的支援。</span><span class="sxs-lookup"><span data-stu-id="08357-228">Provides support for reserializing specific Unity files.</span></span> |
| | [<span data-ttu-id="08357-229">RuntimeTools/Tools/ControllerMappingTool</span><span class="sxs-lookup"><span data-stu-id="08357-229">RuntimeTools/Tools/ControllerMappingTool</span></span>](../features/tools/controller-mapping-tool.md) | <span data-ttu-id="08357-230">此公用程式可讓開發人員快速判斷硬體控制器的 Unity 對應。</span><span class="sxs-lookup"><span data-stu-id="08357-230">Utility enabling developers to quickly determine Unity mappings for hardware controllers.</span></span> |
| | <span data-ttu-id="08357-231">ScreenshotUtility</span><span class="sxs-lookup"><span data-stu-id="08357-231">ScreenshotUtility</span></span> | <span data-ttu-id="08357-232">在 Unity 編輯器中啟用捕獲應用程式映射。</span><span class="sxs-lookup"><span data-stu-id="08357-232">Enables capturing application images in the Unity editor.</span></span> |
| | <span data-ttu-id="08357-233">TextureCombinerWindow</span><span class="sxs-lookup"><span data-stu-id="08357-233">TextureCombinerWindow</span></span> | <span data-ttu-id="08357-234">結合圖形材質的公用程式。</span><span class="sxs-lookup"><span data-stu-id="08357-234">Utility to combine graphics textures.</span></span> |
| | [<span data-ttu-id="08357-235">工具箱</span><span class="sxs-lookup"><span data-stu-id="08357-235">Toolbox</span></span>](../features/ux-building-blocks/toolbox.md) | <span data-ttu-id="08357-236">可讓您輕鬆地探索及使用 MRTK UX 元件的 UI。</span><span class="sxs-lookup"><span data-stu-id="08357-236">UI that makes it easy to discover and use MRTK UX components.</span></span> |

### <a name="test-utilities-package"></a><span data-ttu-id="08357-237">測試公用程式套件</span><span class="sxs-lookup"><span data-stu-id="08357-237">Test utilities package</span></span>

<span data-ttu-id="08357-238">選擇性的 MixedRealityToolkit TestUtilities 套件是協助程式腳本的集合，可讓開發人員輕鬆地 [建立播放模式測試](../contributing/unit-tests.md#play-mode-tests)。</span><span class="sxs-lookup"><span data-stu-id="08357-238">The optional Microsoft.MixedRealityToolkit.TestUtilities package is a collection of helper scripts that enable developers to easily [create play mode tests](../contributing/unit-tests.md#play-mode-tests).</span></span> <span data-ttu-id="08357-239">這些公用程式特別適用于建立 MRTK 元件的開發人員。</span><span class="sxs-lookup"><span data-stu-id="08357-239">These utilities are especially useful for developers creating MRTK components.</span></span>

| <span data-ttu-id="08357-240">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-240">Folder</span></span> | <span data-ttu-id="08357-241">元件</span><span class="sxs-lookup"><span data-stu-id="08357-241">Component</span></span> | <span data-ttu-id="08357-242">描述</span><span class="sxs-lookup"><span data-stu-id="08357-242">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-243">MRTK/測試</span><span class="sxs-lookup"><span data-stu-id="08357-243">MRTK/Tests</span></span> | |
| | <span data-ttu-id="08357-244">TestUtilities</span><span class="sxs-lookup"><span data-stu-id="08357-244">TestUtilities</span></span> | <span data-ttu-id="08357-245">簡化播放模式測試建立的方法，包括手動模擬公用程式。</span><span class="sxs-lookup"><span data-stu-id="08357-245">Methods to simplify creation of play mode tests, including hand simulation utilities.</span></span> |

### <a name="examples-package"></a><span data-ttu-id="08357-246">範例套件</span><span class="sxs-lookup"><span data-stu-id="08357-246">Examples package</span></span>

<span data-ttu-id="08357-247">範例套件包含的示範、範例腳本，以及可在基礎套件中執行功能的範例幕後。</span><span class="sxs-lookup"><span data-stu-id="08357-247">The examples package contains demos, sample scripts, and sample scenes that exercise functionality in the foundation package.</span></span> <span data-ttu-id="08357-248">此套件包含 [HandInteractionExample 場景](../features/example-scenes/hand-interaction-examples.md) (如下圖所示) 其中包含的範例物件可回應各種類型的手寫輸入 (清楚說明的) 。</span><span class="sxs-lookup"><span data-stu-id="08357-248">This package contains the [HandInteractionExample scene](../features/example-scenes/hand-interaction-examples.md) (pictured below) which contains sample objects that respond to various types of hand input (articulated and non-articulated).</span></span>

![HandInteractionExample 場景](../features/images/MRTK_Examples.png)

<span data-ttu-id="08357-250">此套件也包含眼睛追蹤示範，其 [記載于此處](../features/eye-tracking/eye-tracking-examples-overview.md)</span><span class="sxs-lookup"><span data-stu-id="08357-250">This package also contains eye tracking demos, which are [documented here](../features/eye-tracking/eye-tracking-examples-overview.md)</span></span>

<span data-ttu-id="08357-251">更常見的情況是，MRTK 中的任何新功能都應該包含範例套件中的對應範例，大致遵循相同的資料夾結構和位置。</span><span class="sxs-lookup"><span data-stu-id="08357-251">More generally, any new feature in the MRTK should contain a corresponding example in the examples package, roughly following the same folder structure and location.</span></span>

> [!NOTE]
> <span data-ttu-id="08357-252">這些範例套件需要 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="08357-252">The examples package requires Microsoft.MixedRealityToolkit.Unity.Foundation.</span></span>

| <span data-ttu-id="08357-253">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-253">Folder</span></span> | <span data-ttu-id="08357-254">元件</span><span class="sxs-lookup"><span data-stu-id="08357-254">Component</span></span> | <span data-ttu-id="08357-255">描述</span><span class="sxs-lookup"><span data-stu-id="08357-255">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-256">MRTK/範例</span><span class="sxs-lookup"><span data-stu-id="08357-256">MRTK/Examples</span></span> | | |
| | <span data-ttu-id="08357-257">示範</span><span class="sxs-lookup"><span data-stu-id="08357-257">Demos</span></span> | <span data-ttu-id="08357-258">說明一或兩個相關功能的簡單場景。</span><span class="sxs-lookup"><span data-stu-id="08357-258">Simple scenes illustrating one or two related features.</span></span> |
| | <span data-ttu-id="08357-259">實驗</span><span class="sxs-lookup"><span data-stu-id="08357-259">Experimental</span></span> | <span data-ttu-id="08357-260">示範實驗性功能的示範場景。</span><span class="sxs-lookup"><span data-stu-id="08357-260">Demo scenes illustrating experimental features.</span></span> |
| | <span data-ttu-id="08357-261">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="08357-261">StandardAssets</span></span> | <span data-ttu-id="08357-262">多個示範場景所共用的常見資產。</span><span class="sxs-lookup"><span data-stu-id="08357-262">Common assets shared by multiple demo scenes.</span></span> |

## <a name="unity-package-manager"></a><span data-ttu-id="08357-263">Unity 封裝管理員</span><span class="sxs-lookup"><span data-stu-id="08357-263">Unity Package Manager</span></span>

<span data-ttu-id="08357-264">針對使用 Unity 2019.4 和更新版本所建立的體驗，MRTK 可透過 [unity 封裝管理員](https://docs.unity3d.com/Manual/Packages.html)取得。</span><span class="sxs-lookup"><span data-stu-id="08357-264">For experiences being created using Unity 2019.4 and newer, the MRTK is available via the [Unity Package Manager](https://docs.unity3d.com/Manual/Packages.html).</span></span>

<span data-ttu-id="08357-265">使用資產套件的一些優點包括：</span><span class="sxs-lookup"><span data-stu-id="08357-265">Some of the benefits of using asset packages include:</span></span>

- <span data-ttu-id="08357-266">較小的專案</span><span class="sxs-lookup"><span data-stu-id="08357-266">Smaller projects</span></span>
  - <span data-ttu-id="08357-267">更清楚的 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="08357-267">Cleaner Visual Studio solutions</span></span>
  - <span data-ttu-id="08357-268">要簽入的檔案越少 (MRTK 是檔案中的簡單參考 `Packages/manifest.json`) </span><span class="sxs-lookup"><span data-stu-id="08357-268">Fewer files to check in (MRTK is a simple reference in the `Packages/manifest.json` file)</span></span>
- <span data-ttu-id="08357-269">更快速的編譯</span><span class="sxs-lookup"><span data-stu-id="08357-269">Faster compilation</span></span>
  - <span data-ttu-id="08357-270">Unity 不需要在建立期間重新編譯 MRTK</span><span class="sxs-lookup"><span data-stu-id="08357-270">Unity does not need to recompile MRTK during building</span></span>
- <span data-ttu-id="08357-271">相依性解析</span><span class="sxs-lookup"><span data-stu-id="08357-271">Dependency resolution</span></span>
  - <span data-ttu-id="08357-272">指定具有相依性的套件時，會自動安裝必要的 MRTK 套件</span><span class="sxs-lookup"><span data-stu-id="08357-272">Required MRTK packages are automatically installed when specifying packages with dependencies</span></span>
- <span data-ttu-id="08357-273">簡易更新新的 MRTK 版本</span><span class="sxs-lookup"><span data-stu-id="08357-273">Easy update to new MRTK versions</span></span>
  - <span data-ttu-id="08357-274">變更檔案 `Packages/manifest.json` 中的版本</span><span class="sxs-lookup"><span data-stu-id="08357-274">Change the version in the `Packages/manifest.json` file</span></span>

<span data-ttu-id="08357-275">其中一些挑戰如下：</span><span class="sxs-lookup"><span data-stu-id="08357-275">Some of the challenges are:</span></span>

- <span data-ttu-id="08357-276">MRTK 不可變</span><span class="sxs-lookup"><span data-stu-id="08357-276">MRTK is immutable</span></span>
  - <span data-ttu-id="08357-277">無法進行變更，而無法在封裝解析期間移除變更</span><span class="sxs-lookup"><span data-stu-id="08357-277">Cannot make changes without them being removed during package resolution</span></span>
- <span data-ttu-id="08357-278">MRTK 不支援使用 Unity 2018.4 的 UPM 套件</span><span class="sxs-lookup"><span data-stu-id="08357-278">MRTK does not support UPM packages with Unity 2018.4</span></span>

### <a name="foundation-package"></a><span data-ttu-id="08357-279">基礎封裝</span><span class="sxs-lookup"><span data-stu-id="08357-279">Foundation package</span></span>

<span data-ttu-id="08357-280">基礎封裝 (`com.microsoft.mixedreality.toolkit.foundation`) 形成混合現實工具組的基礎。</span><span class="sxs-lookup"><span data-stu-id="08357-280">The foundation package (`com.microsoft.mixedreality.toolkit.foundation`) forms the basis of the Mixed Reality Toolkit.</span></span>

| <span data-ttu-id="08357-281">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-281">Folder</span></span> | <span data-ttu-id="08357-282">元件</span><span class="sxs-lookup"><span data-stu-id="08357-282">Component</span></span> | <span data-ttu-id="08357-283">描述</span><span class="sxs-lookup"><span data-stu-id="08357-283">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-284">MRTK/核心</span><span class="sxs-lookup"><span data-stu-id="08357-284">MRTK/Core</span></span> | | <span data-ttu-id="08357-285">介面和類型定義、基類、標準著色器。</span><span class="sxs-lookup"><span data-stu-id="08357-285">Interface and type definitions, base classes, standard shader.</span></span> |
| <span data-ttu-id="08357-286">MRTK/核心/提供者</span><span class="sxs-lookup"><span data-stu-id="08357-286">MRTK/Core/Providers</span></span> | | <span data-ttu-id="08357-287">平臺中立的資料提供者</span><span class="sxs-lookup"><span data-stu-id="08357-287">Platform agnostic data providers</span></span> |
| | <span data-ttu-id="08357-288">手</span><span class="sxs-lookup"><span data-stu-id="08357-288">Hands</span></span> | <span data-ttu-id="08357-289">用於手動追蹤的基類支援和服務。</span><span class="sxs-lookup"><span data-stu-id="08357-289">Base class support and services for hand tracking.</span></span> |
| | [<span data-ttu-id="08357-290">InputAnimation</span><span class="sxs-lookup"><span data-stu-id="08357-290">InputAnimation</span></span>](../features/input-simulation/input-animation-recording.md) | <span data-ttu-id="08357-291">支援錄製 head 移動和手追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="08357-291">Support for recording head movement and hand tracking data.</span></span> |
| | [<span data-ttu-id="08357-292">InputSimulation</span><span class="sxs-lookup"><span data-stu-id="08357-292">InputSimulation</span></span>](../features/input-simulation/input-simulation-service.md) | <span data-ttu-id="08357-293">支援手形和眼睛輸入的編輯器內模擬。</span><span class="sxs-lookup"><span data-stu-id="08357-293">Support for in-editor simulation of hand and eye input.</span></span> |
| | [<span data-ttu-id="08357-294">ObjectMeshObserver</span><span class="sxs-lookup"><span data-stu-id="08357-294">ObjectMeshObserver</span></span>](../features/spatial-awareness/spatial-object-mesh-observer.md) | <span data-ttu-id="08357-295">空間感知觀察者使用3D 模型做為資料。</span><span class="sxs-lookup"><span data-stu-id="08357-295">Spatial awareness observer using a 3D model as the data.</span></span> |
| | <span data-ttu-id="08357-296">UnityInput</span><span class="sxs-lookup"><span data-stu-id="08357-296">UnityInput</span></span> | <span data-ttu-id="08357-297">一般輸入裝置 (搖桿、滑鼠等 ) 透過 Unity 的輸入 API 來執行。</span><span class="sxs-lookup"><span data-stu-id="08357-297">Common input devices (joystick, mouse, etc.) implemented via Unity's input API.</span></span> |
| <span data-ttu-id="08357-298">MRTK/提供者</span><span class="sxs-lookup"><span data-stu-id="08357-298">MRTK/Providers</span></span> | | <span data-ttu-id="08357-299">平臺特定的資料提供者</span><span class="sxs-lookup"><span data-stu-id="08357-299">Platform specific data providers</span></span> |
| | <span data-ttu-id="08357-300">LeapMotion</span><span class="sxs-lookup"><span data-stu-id="08357-300">LeapMotion</span></span> | <span data-ttu-id="08357-301">UltraLeap Leap 移動控制器的支援。</span><span class="sxs-lookup"><span data-stu-id="08357-301">Support for the UltraLeap Leap Motion controller.</span></span> |
| | <span data-ttu-id="08357-302">OpenVR</span><span class="sxs-lookup"><span data-stu-id="08357-302">OpenVR</span></span> | <span data-ttu-id="08357-303">OpenVR 裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="08357-303">Support for OpenVR devices.</span></span> |
| | <span data-ttu-id="08357-304">Oculus</span><span class="sxs-lookup"><span data-stu-id="08357-304">Oculus</span></span> | <span data-ttu-id="08357-305">Oculus 裝置的支援，例如尋找。</span><span class="sxs-lookup"><span data-stu-id="08357-305">Support for Oculus devices, such as the Quest.</span></span> |
| | [<span data-ttu-id="08357-306">UnityAR</span><span class="sxs-lookup"><span data-stu-id="08357-306">UnityAR</span></span>](../features/camera-system/unity-ar-camera-settings.md) | <span data-ttu-id="08357-307"> (實驗性) 攝影機設定提供者，讓 MRTK 與行動 AR 裝置搭配使用。</span><span class="sxs-lookup"><span data-stu-id="08357-307">(Experimental) Camera settings provider enabling MRTK use with mobile AR devices.</span></span> |
| | <span data-ttu-id="08357-308">WindowsMixedReality</span><span class="sxs-lookup"><span data-stu-id="08357-308">WindowsMixedReality</span></span> | <span data-ttu-id="08357-309">支援 Windows Mixed Reality 的裝置，包括 Microsoft HoloLens 和沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="08357-309">Support for Windows Mixed Reality devices, including Microsoft HoloLens and immersive headsets.</span></span> |
| | <span data-ttu-id="08357-310">Windows</span><span class="sxs-lookup"><span data-stu-id="08357-310">Windows</span></span> | <span data-ttu-id="08357-311">支援 Microsoft Windows 特定 Api，例如語音和聽寫。</span><span class="sxs-lookup"><span data-stu-id="08357-311">Support for Microsoft Windows specific APIs, for example speech and dictation.</span></span> |
| | <span data-ttu-id="08357-312">XR SDK</span><span class="sxs-lookup"><span data-stu-id="08357-312">XR SDK</span></span> | <span data-ttu-id="08357-313"> (unity 2019.3 和更新版本中 [unity 新 XR 架構](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的實驗性) 支援。</span><span class="sxs-lookup"><span data-stu-id="08357-313">(Experimental) Support for [Unity's new XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in Unity 2019.3 and newer.</span></span> |
| <span data-ttu-id="08357-314">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="08357-314">MRTK/SDK</span></span> | | |
| | <span data-ttu-id="08357-315">實驗</span><span class="sxs-lookup"><span data-stu-id="08357-315">Experimental</span></span> | <span data-ttu-id="08357-316">實驗性功能，包括著色器、使用者介面控制項和個別系統管理員。</span><span class="sxs-lookup"><span data-stu-id="08357-316">Experimental features, including shaders, user interface controls and individual system managers.</span></span> |
| | <span data-ttu-id="08357-317">功能</span><span class="sxs-lookup"><span data-stu-id="08357-317">Features</span></span> | <span data-ttu-id="08357-318">建基於基礎封裝的功能。</span><span class="sxs-lookup"><span data-stu-id="08357-318">Functionality that builds upon the Foundation package.</span></span> |
| | <span data-ttu-id="08357-319">Profiles</span><span class="sxs-lookup"><span data-stu-id="08357-319">Profiles</span></span> | <span data-ttu-id="08357-320">Microsoft Mixed Reality 工具組系統和服務的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="08357-320">Default profiles for the Microsoft Mixed Reality Toolkit systems and services.</span></span> |
| | <span data-ttu-id="08357-321">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="08357-321">StandardAssets</span></span> | <span data-ttu-id="08357-322">一般資產;模型、材質、材質等等。</span><span class="sxs-lookup"><span data-stu-id="08357-322">Common assets; models, textures, materials, etc.</span></span> |
| <span data-ttu-id="08357-323">MRTK/服務</span><span class="sxs-lookup"><span data-stu-id="08357-323">MRTK/Services</span></span> | | |
| | [<span data-ttu-id="08357-324">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="08357-324">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md) | <span data-ttu-id="08357-325">執行 VR 界限支援的系統。</span><span class="sxs-lookup"><span data-stu-id="08357-325">System implementing VR boundary support.</span></span> |
| | [<span data-ttu-id="08357-326">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="08357-326">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md) | <span data-ttu-id="08357-327">系統執行攝影機設定和管理。</span><span class="sxs-lookup"><span data-stu-id="08357-327">System implementing camera configuration and management.</span></span> |
| | [<span data-ttu-id="08357-328">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="08357-328">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md) | <span data-ttu-id="08357-329">在 application diagnostics 中執行的系統，例如 visual profiler。</span><span class="sxs-lookup"><span data-stu-id="08357-329">System implementing in application diagnostics, for example a visual profiler.</span></span> |
| | [<span data-ttu-id="08357-330">InputSystem</span><span class="sxs-lookup"><span data-stu-id="08357-330">InputSystem</span></span>](../features/input/overview.md) | <span data-ttu-id="08357-331">系統，提供存取和處理使用者輸入的支援。</span><span class="sxs-lookup"><span data-stu-id="08357-331">System providing support for accessing and handling user input.</span></span> |
| | [<span data-ttu-id="08357-332">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="08357-332">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md) | <span data-ttu-id="08357-333">提供多場景應用程式支援的系統。</span><span class="sxs-lookup"><span data-stu-id="08357-333">System providing multi-scene application support.</span></span> |
| | [<span data-ttu-id="08357-334">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="08357-334">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md) | <span data-ttu-id="08357-335">提供使用者環境感知支援的系統。</span><span class="sxs-lookup"><span data-stu-id="08357-335">System providing support for awareness of the user's environment.</span></span> |
| | [<span data-ttu-id="08357-336">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="08357-336">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md) | <span data-ttu-id="08357-337">提供 teleporting 支援的系統 (移至跳躍) 的體驗。</span><span class="sxs-lookup"><span data-stu-id="08357-337">System providing support for teleporting (moving about the experience in jumps).</span></span> |

<span data-ttu-id="08357-338">相依性：</span><span class="sxs-lookup"><span data-stu-id="08357-338">Dependencies:</span></span>

- <span data-ttu-id="08357-339">標準資產 (`com.microsoft.mixedreality.toolkit.standardassets`) </span><span class="sxs-lookup"><span data-stu-id="08357-339">Standard Assets (`com.microsoft.mixedreality.toolkit.standardassets`)</span></span>

### <a name="standard-assets"></a><span data-ttu-id="08357-340">標準資產</span><span class="sxs-lookup"><span data-stu-id="08357-340">Standard Assets</span></span>

<span data-ttu-id="08357-341">標準資產套件 (`com.microsoft.mixedreality.toolkit.standardassets)` 是針對所有混合現實體驗所建議的元件集合，包括：</span><span class="sxs-lookup"><span data-stu-id="08357-341">The standard assets package (`com.microsoft.mixedreality.toolkit.standardassets)` is a collection of components that are recommended for all mixed reality experiences, including:</span></span>

- <span data-ttu-id="08357-342">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="08357-342">MRTK Standard shader</span></span>
- <span data-ttu-id="08357-343">使用 MRTK 標準著色器的基本材質</span><span class="sxs-lookup"><span data-stu-id="08357-343">Basic materials using the MRTK Standard shader</span></span>
- <span data-ttu-id="08357-344">音訊檔案</span><span class="sxs-lookup"><span data-stu-id="08357-344">Audio files</span></span>
- <span data-ttu-id="08357-345">字型</span><span class="sxs-lookup"><span data-stu-id="08357-345">Fonts</span></span>
- <span data-ttu-id="08357-346">紋理</span><span class="sxs-lookup"><span data-stu-id="08357-346">Textures</span></span>
- <span data-ttu-id="08357-347">圖示</span><span class="sxs-lookup"><span data-stu-id="08357-347">Icons</span></span>

> [!Note]
> <span data-ttu-id="08357-348">為了避免根據元件定義的重大變更，標準資產套件中不包含用來控制 MRTK 標準著色器某些功能的腳本。</span><span class="sxs-lookup"><span data-stu-id="08357-348">To avoid breaking changes based on assembly definitions, the scripts used to control some features of the MRTK Standard shader are not included in the standard assets package.</span></span> <span data-ttu-id="08357-349">您可以在資料夾的基礎套件中找到這些腳本 `MRTK/Core/Utilities/StandardShader` 。</span><span class="sxs-lookup"><span data-stu-id="08357-349">These scripts can be found in the foundation package in the `MRTK/Core/Utilities/StandardShader` folder.</span></span>

<span data-ttu-id="08357-350">相依性：無</span><span class="sxs-lookup"><span data-stu-id="08357-350">Dependencies: none</span></span>

### <a name="extension-packages"></a><span data-ttu-id="08357-351">擴充套件</span><span class="sxs-lookup"><span data-stu-id="08357-351">Extension packages</span></span>

<span data-ttu-id="08357-352">選用的擴充套件 (`com.microsoft.mixedreality.toolkit.extensions)` 包含擴充 MRTK 功能的其他元件。</span><span class="sxs-lookup"><span data-stu-id="08357-352">The optional extensions package (`com.microsoft.mixedreality.toolkit.extensions)` contains additional components that expand the functionality of the MRTK.</span></span>

| <span data-ttu-id="08357-353">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-353">Folder</span></span> | <span data-ttu-id="08357-354">元件</span><span class="sxs-lookup"><span data-stu-id="08357-354">Component</span></span> | <span data-ttu-id="08357-355">描述</span><span class="sxs-lookup"><span data-stu-id="08357-355">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-356">MRTK/擴充功能</span><span class="sxs-lookup"><span data-stu-id="08357-356">MRTK/Extensions</span></span> | |
| | [<span data-ttu-id="08357-357">HandPhysicsService</span><span class="sxs-lookup"><span data-stu-id="08357-357">HandPhysicsService</span></span>](../features/extensions/hand-physics-service.md) | <span data-ttu-id="08357-358">將物理支援新增至明確表述的服務。</span><span class="sxs-lookup"><span data-stu-id="08357-358">Service that adds physics support to articulated hands.</span></span> |
| | <span data-ttu-id="08357-359">LostTrackingService</span><span class="sxs-lookup"><span data-stu-id="08357-359">LostTrackingService</span></span> | <span data-ttu-id="08357-360">這項服務可簡化 Microsoft HoloLens 裝置上的追蹤遺失處理。</span><span class="sxs-lookup"><span data-stu-id="08357-360">Service that simplifies handing of tracking loss on Microsoft HoloLens devices.</span></span> |
| | [<span data-ttu-id="08357-361">SceneTransitionService</span><span class="sxs-lookup"><span data-stu-id="08357-361">SceneTransitionService</span></span>](../features/extensions/scene-transition-service.md) | <span data-ttu-id="08357-362">簡化加入平滑場景轉換的服務。</span><span class="sxs-lookup"><span data-stu-id="08357-362">Service that simplifies adding smooth scene transitions.</span></span> |
| | <span data-ttu-id="08357-363">範例 ~</span><span class="sxs-lookup"><span data-stu-id="08357-363">Samples~</span></span> | <span data-ttu-id="08357-364">Unity 編輯器中隱藏的 () 資料夾，其中包含範例場景和資產。</span><span class="sxs-lookup"><span data-stu-id="08357-364">A hidden (in the Unity Editor) folder that contains the sample scenes and assets.</span></span> |

<span data-ttu-id="08357-365">如需使用包含範例專案之封裝的詳細資訊，請參閱 [混合現實工具組和 Unity 封裝管理員](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 文章。</span><span class="sxs-lookup"><span data-stu-id="08357-365">More details on the process of using packages containing example projects can be found in the [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) article.</span></span>

<span data-ttu-id="08357-366">相依性：</span><span class="sxs-lookup"><span data-stu-id="08357-366">Dependencies:</span></span>

- <span data-ttu-id="08357-367">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="08357-367">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="tools-package"></a><span data-ttu-id="08357-368">工具套件</span><span class="sxs-lookup"><span data-stu-id="08357-368">Tools package</span></span>

<span data-ttu-id="08357-369">選用的工具套件 (`com.microsoft.mixedreality.toolkit.tools)` 包含適用于建立混合現實體驗的工具。</span><span class="sxs-lookup"><span data-stu-id="08357-369">The optional tools package (`com.microsoft.mixedreality.toolkit.tools)` contains tools that are useful for creating mixed reality experiences.</span></span> <span data-ttu-id="08357-370">一般而言，這些工具是編輯器元件，而其程式碼不會隨附于應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="08357-370">In general, these tools are editor components and their code does not ship as part of an application.</span></span>

| <span data-ttu-id="08357-371">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-371">Folder</span></span> | <span data-ttu-id="08357-372">元件</span><span class="sxs-lookup"><span data-stu-id="08357-372">Component</span></span> | <span data-ttu-id="08357-373">描述</span><span class="sxs-lookup"><span data-stu-id="08357-373">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-374">MRTK/工具</span><span class="sxs-lookup"><span data-stu-id="08357-374">MRTK/Tools</span></span> | |
| | <span data-ttu-id="08357-375">BuildWindow</span><span class="sxs-lookup"><span data-stu-id="08357-375">BuildWindow</span></span> | <span data-ttu-id="08357-376">這項工具可協助簡化建立和部署 UWP 應用程式的流程。</span><span class="sxs-lookup"><span data-stu-id="08357-376">Tool that helps simplify the process of building and deploying UWP applications.</span></span> |
| | [<span data-ttu-id="08357-377">DependencyWindow</span><span class="sxs-lookup"><span data-stu-id="08357-377">DependencyWindow</span></span>](../features/tools/dependency-window.md) | <span data-ttu-id="08357-378">此工具會在專案中建立資產的相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="08357-378">Tool that creates a dependency graph of assets in a project.</span></span> |
| | [<span data-ttu-id="08357-379">ExtensionServiceCreator</span><span class="sxs-lookup"><span data-stu-id="08357-379">ExtensionServiceCreator</span></span>](../features/tools/extension-service-creation-wizard.md) | <span data-ttu-id="08357-380">協助建立延伸模組服務的 Wizard。</span><span class="sxs-lookup"><span data-stu-id="08357-380">Wizard to assist in creating extension services.</span></span> |
| | [<span data-ttu-id="08357-381">MigrationWindow</span><span class="sxs-lookup"><span data-stu-id="08357-381">MigrationWindow</span></span>](../features/tools/migration-window.md) | <span data-ttu-id="08357-382">協助更新使用已淘汰 MRTK 元件之程式碼的工具。</span><span class="sxs-lookup"><span data-stu-id="08357-382">Tool that assists in updating code that uses deprecated MRTK components.</span></span>  |
| | [<span data-ttu-id="08357-383">OptimizeWindow</span><span class="sxs-lookup"><span data-stu-id="08357-383">OptimizeWindow</span></span>](../features/tools/optimize-window.md) | <span data-ttu-id="08357-384">此公用程式可協助您自動設定混合現實專案，以獲得 Unity 的最佳效能。</span><span class="sxs-lookup"><span data-stu-id="08357-384">Utility to help automate configuring a mixed reality project for the best performance in Unity.</span></span> |
| | <span data-ttu-id="08357-385">ReserializeAssetsUtility</span><span class="sxs-lookup"><span data-stu-id="08357-385">ReserializeAssetsUtility</span></span> | <span data-ttu-id="08357-386">提供 reserializing 特定 Unity 檔案的支援。</span><span class="sxs-lookup"><span data-stu-id="08357-386">Provides support for reserializing specific Unity files.</span></span> |
| | [<span data-ttu-id="08357-387">RuntimeTools/Tools/ControllerMappingTool</span><span class="sxs-lookup"><span data-stu-id="08357-387">RuntimeTools/Tools/ControllerMappingTool</span></span>](../features/tools/controller-mapping-tool.md) | <span data-ttu-id="08357-388">此公用程式可讓開發人員快速判斷硬體控制器的 Unity 對應。</span><span class="sxs-lookup"><span data-stu-id="08357-388">Utility enabling developers to quickly determine Unity mappings for hardware controllers.</span></span> |
| | <span data-ttu-id="08357-389">ScreenshotUtility</span><span class="sxs-lookup"><span data-stu-id="08357-389">ScreenshotUtility</span></span> | <span data-ttu-id="08357-390">在 Unity 編輯器中啟用捕獲應用程式映射。</span><span class="sxs-lookup"><span data-stu-id="08357-390">Enables capturing application images in the Unity editor.</span></span> |
| | <span data-ttu-id="08357-391">TextureCombinerWindow</span><span class="sxs-lookup"><span data-stu-id="08357-391">TextureCombinerWindow</span></span> | <span data-ttu-id="08357-392">結合圖形材質的公用程式。</span><span class="sxs-lookup"><span data-stu-id="08357-392">Utility to combine graphics textures.</span></span> |
| | [<span data-ttu-id="08357-393">工具箱</span><span class="sxs-lookup"><span data-stu-id="08357-393">Toolbox</span></span>](../features/ux-building-blocks/toolbox.md) | <span data-ttu-id="08357-394">可讓您輕鬆地探索及使用 MRTK UX 元件的 UI。</span><span class="sxs-lookup"><span data-stu-id="08357-394">UI that makes it easy to discover and use MRTK UX components.</span></span> |

<span data-ttu-id="08357-395">相依性：</span><span class="sxs-lookup"><span data-stu-id="08357-395">Dependencies:</span></span>

- <span data-ttu-id="08357-396">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="08357-396">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="test-utilities-package"></a><span data-ttu-id="08357-397">測試公用程式套件</span><span class="sxs-lookup"><span data-stu-id="08357-397">Test utilities package</span></span>

<span data-ttu-id="08357-398">選用的測試公用程式套件 (`com.microsoft.mixedreality.toolkit.testutilities`) 包含協助程式腳本的集合，可讓開發人員輕鬆地建立播放模式測試。</span><span class="sxs-lookup"><span data-stu-id="08357-398">The optional test utilities package (`com.microsoft.mixedreality.toolkit.testutilities`) contains a collection of helper scripts that enable developers to easily create play mode tests.</span></span> <span data-ttu-id="08357-399">這些公用程式特別適用于建立 MRTK 元件的開發人員。</span><span class="sxs-lookup"><span data-stu-id="08357-399">These utilities are especially useful for developers creating MRTK components.</span></span>

| <span data-ttu-id="08357-400">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-400">Folder</span></span> | <span data-ttu-id="08357-401">元件</span><span class="sxs-lookup"><span data-stu-id="08357-401">Component</span></span> | <span data-ttu-id="08357-402">描述</span><span class="sxs-lookup"><span data-stu-id="08357-402">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-403">MRTK/測試</span><span class="sxs-lookup"><span data-stu-id="08357-403">MRTK/Tests</span></span> | |
| | <span data-ttu-id="08357-404">TestUtilities</span><span class="sxs-lookup"><span data-stu-id="08357-404">TestUtilities</span></span> | <span data-ttu-id="08357-405">簡化播放模式測試建立的方法，包括手動模擬公用程式。</span><span class="sxs-lookup"><span data-stu-id="08357-405">Methods to simplify creation of play mode tests, including hand simulation utilities.</span></span> |

<span data-ttu-id="08357-406">相依性：</span><span class="sxs-lookup"><span data-stu-id="08357-406">Dependencies:</span></span>

- <span data-ttu-id="08357-407">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="08357-407">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>

### <a name="examples-package"></a><span data-ttu-id="08357-408">範例套件</span><span class="sxs-lookup"><span data-stu-id="08357-408">Examples package</span></span>

<span data-ttu-id="08357-409">範例封裝 (`com.microsoft.mixedreality.toolkit.examples`) ，其結構化可讓開發人員只匯入感興趣的範例。</span><span class="sxs-lookup"><span data-stu-id="08357-409">The examples package (`com.microsoft.mixedreality.toolkit.examples`), is structured to allow developers to import only the examples of interest.</span></span>

<span data-ttu-id="08357-410">如需使用包含範例專案之封裝的詳細資訊，請參閱 [混合現實工具組和 Unity 封裝管理員](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 文章。</span><span class="sxs-lookup"><span data-stu-id="08357-410">More details on the process of using packages containing example projects can be found in the [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) article.</span></span>

| <span data-ttu-id="08357-411">資料夾</span><span class="sxs-lookup"><span data-stu-id="08357-411">Folder</span></span> | <span data-ttu-id="08357-412">元件</span><span class="sxs-lookup"><span data-stu-id="08357-412">Component</span></span> | <span data-ttu-id="08357-413">描述</span><span class="sxs-lookup"><span data-stu-id="08357-413">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="08357-414">MRTK/範例</span><span class="sxs-lookup"><span data-stu-id="08357-414">MRTK/Examples</span></span> | | |
| | <span data-ttu-id="08357-415">範例 ~</span><span class="sxs-lookup"><span data-stu-id="08357-415">Samples~</span></span> | <span data-ttu-id="08357-416">Unity 編輯器中隱藏的 () 資料夾，其中包含範例場景和資產。</span><span class="sxs-lookup"><span data-stu-id="08357-416">A hidden (in the Unity Editor) folder that contains the sample scenes and assets.</span></span> |
| | <span data-ttu-id="08357-417">StandardAssets</span><span class="sxs-lookup"><span data-stu-id="08357-417">StandardAssets</span></span> | <span data-ttu-id="08357-418">多個示範場景所共用的常見資產。</span><span class="sxs-lookup"><span data-stu-id="08357-418">Common assets shared by multiple demo scenes.</span></span> |

<span data-ttu-id="08357-419">相依性：</span><span class="sxs-lookup"><span data-stu-id="08357-419">Dependencies:</span></span>

- <span data-ttu-id="08357-420">Foundation (`com.microsoft.mixedreality.toolkit.foundation`) </span><span class="sxs-lookup"><span data-stu-id="08357-420">Foundation (`com.microsoft.mixedreality.toolkit.foundation`)</span></span>
- <span data-ttu-id="08357-421">擴充 (`com.microsoft.mixedreality.toolkit.extensions`)</span><span class="sxs-lookup"><span data-stu-id="08357-421">Extensions (`com.microsoft.mixedreality.toolkit.extensions`)</span></span>

## <a name="see-also"></a><span data-ttu-id="08357-422">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08357-422">See also</span></span>

- [<span data-ttu-id="08357-423">架構概觀</span><span class="sxs-lookup"><span data-stu-id="08357-423">Architecture Overview</span></span>](../architecture/overview.md)
- [<span data-ttu-id="08357-424">系統、延伸模組服務和資料提供者</span><span class="sxs-lookup"><span data-stu-id="08357-424">Systems, Extension Services and Data Providers</span></span>](../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="08357-425">混合現實工具組和 Unity 封裝管理員</span><span class="sxs-lookup"><span data-stu-id="08357-425">Mixed Reality Toolkit and Unity Package Manager</span></span>](../configuration/usingupm.md)
