---
title: MRTK-Unity 開發人員檔
description: 瞭解 Unity 的混合現實工具組。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK
ms.openlocfilehash: 6576eaedbfba11fae62e59fa9777fe928f0c6a69
ms.sourcegitcommit: 728f4523188628950478cc03ec7145e89569e0d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2021
ms.locfileid: "108172560"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="b5001-104">何謂混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="b5001-104">What is the Mixed Reality Toolkit</span></span>

![混合實境工具組](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="b5001-106">MRTK-Unity 是由 Microsoft 所推動的專案，其提供一組元件與功能，可用來加快 Unity 中的跨平台 MR 應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="b5001-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="b5001-107">以下是其中的一些功能：</span><span class="sxs-lookup"><span data-stu-id="b5001-107">Here are some of its functions:</span></span>

* <span data-ttu-id="b5001-108">提供 **空間互動和 UI 的跨平臺輸入系統和建立區塊**。</span><span class="sxs-lookup"><span data-stu-id="b5001-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="b5001-109">透過可讓您立即查看變更的編輯器內模擬，讓您能夠 **快速建立原型** 。</span><span class="sxs-lookup"><span data-stu-id="b5001-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="b5001-110">以可擴充的 **架構** 運作，讓開發人員能夠交換核心元件。</span><span class="sxs-lookup"><span data-stu-id="b5001-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="b5001-111">**支援多種平臺**：</span><span class="sxs-lookup"><span data-stu-id="b5001-111">**Supports a wide range of platforms**:</span></span>

| <span data-ttu-id="b5001-112">平台</span><span class="sxs-lookup"><span data-stu-id="b5001-112">Platform</span></span> | <span data-ttu-id="b5001-113">支援的裝置</span><span class="sxs-lookup"><span data-stu-id="b5001-113">Supported Devices</span></span> |
|---|---|
| <span data-ttu-id="b5001-114">OpenXR (Unity 2020.2 或更新版本) </span><span class="sxs-lookup"><span data-stu-id="b5001-114">OpenXR (Unity 2020.2 or newer)</span></span> | <span data-ttu-id="b5001-115">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b5001-115">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="b5001-116">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="b5001-116">Windows Mixed Reality headsets</span></span> |
| <span data-ttu-id="b5001-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b5001-117">Windows Mixed Reality</span></span> | <span data-ttu-id="b5001-118">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="b5001-118">Microsoft HoloLens</span></span> <br> <span data-ttu-id="b5001-119">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b5001-119">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="b5001-120">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="b5001-120">Windows Mixed Reality headsets</span></span>  |
| <span data-ttu-id="b5001-121">Oculus (Unity 2019.3 或更新版本) </span><span class="sxs-lookup"><span data-stu-id="b5001-121">Oculus (Unity 2019.3 or newer)</span></span> | <span data-ttu-id="b5001-122">Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="b5001-122">Oculus Quest</span></span> |
| <span data-ttu-id="b5001-123">OpenVR</span><span class="sxs-lookup"><span data-stu-id="b5001-123">OpenVR</span></span> |  <span data-ttu-id="b5001-124">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="b5001-124">Windows Mixed Reality headsets</span></span> <br> <span data-ttu-id="b5001-125">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="b5001-125">HTC Vive</span></span> <br> <span data-ttu-id="b5001-126">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="b5001-126">Oculus Rift</span></span> |
| <span data-ttu-id="b5001-127">Ultraleap 手部追蹤</span><span class="sxs-lookup"><span data-stu-id="b5001-127">Ultraleap Hand Tracking</span></span> | <span data-ttu-id="b5001-128">Ultraleap Leap 移動控制器</span><span class="sxs-lookup"><span data-stu-id="b5001-128">Ultraleap Leap Motion controller</span></span> |
| <span data-ttu-id="b5001-129">行動</span><span class="sxs-lookup"><span data-stu-id="b5001-129">Mobile</span></span> | <span data-ttu-id="b5001-130">iOS 與 Android</span><span class="sxs-lookup"><span data-stu-id="b5001-130">iOS and Android</span></span> |

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="b5001-131">開始使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="b5001-131">Getting started with MRTK</span></span>

<span data-ttu-id="b5001-132">如果您不熟悉 Unity 中的 MRTK 或混合現實開發，建議您在裝置或模擬器上安裝和探索 MRTK 範例中樞範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="b5001-132">If you're new to MRTK or Mixed Reality development in Unity, we recommend installing and exploring the MRTK Examples Hub sample application on your device or emulator.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="b5001-133">下載 MRTK 範例中樞應用程式</span><span class="sxs-lookup"><span data-stu-id="b5001-133">Download the MRTK Examples Hub app</span></span>](running-examples-hub.md)

<span data-ttu-id="b5001-134">一旦您有了混合現實和 MRTK 所提供的功能，請安裝必要的工具，並遵循我們的初學者層級 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="b5001-134">Once you've got the hang of what Mixed Reality and MRTK has to offer, install the necessary tools and follow our beginner level HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b5001-135">安裝工具</span><span class="sxs-lookup"><span data-stu-id="b5001-135">Install the tools</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b5001-136">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="b5001-136">HoloLens 2 Tutorial Series</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="b5001-137">想要看看幕後的進展嗎？</span><span class="sxs-lookup"><span data-stu-id="b5001-137">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b5001-138">探索 GitHub 上的 MRTK</span><span class="sxs-lookup"><span data-stu-id="b5001-138">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="b5001-139">文件</span><span class="sxs-lookup"><span data-stu-id="b5001-139">Documentation</span></span>

| <span data-ttu-id="b5001-140">[![版本資訊](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-140">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="b5001-141">版本資訊</span><span class="sxs-lookup"><span data-stu-id="b5001-141">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="b5001-142">[![MRTK 總覽](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-142">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="b5001-143">MRTK 總覽</span><span class="sxs-lookup"><span data-stu-id="b5001-143">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="b5001-144">[![API 參考](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="b5001-144">[![API Reference](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="b5001-145">API 參考</span><span class="sxs-lookup"><span data-stu-id="b5001-145">API Reference</span></span>](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="b5001-146">組建狀態</span><span class="sxs-lookup"><span data-stu-id="b5001-146">Build status</span></span>

| <span data-ttu-id="b5001-147">分支</span><span class="sxs-lookup"><span data-stu-id="b5001-147">Branch</span></span> | <span data-ttu-id="b5001-148">CI 狀態</span><span class="sxs-lookup"><span data-stu-id="b5001-148">CI Status</span></span> | <span data-ttu-id="b5001-149">檔狀態</span><span class="sxs-lookup"><span data-stu-id="b5001-149">Docs Status</span></span> |
|---|---|---|
| `mrtk_development` |<span data-ttu-id="b5001-150">[![CI 狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="b5001-150">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="b5001-151">[![檔狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="b5001-151">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="b5001-152">功能範圍</span><span class="sxs-lookup"><span data-stu-id="b5001-152">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="b5001-153">[![輸入系統](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-153">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="b5001-154">**[輸入系統](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-154">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-155">[![手動追蹤 (HoloLens 2) ](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-155">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="b5001-156">**[手動追蹤 <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-156">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-157">[![ (HoloLens 2) 的眼睛追蹤 ](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-157">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="b5001-158">**[<br/> (HoloLens 2) 的眼睛追蹤](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-158">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-159">[![配置 檔](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-159">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="b5001-160">**[配置 檔](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-160">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-161">[![ (Ultraleap) 的手動追蹤 ](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-161">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="b5001-162">**[<br/> (Ultraleap) 的手動追蹤](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-162">**[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-163">[![UI 控制項](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="b5001-163">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="b5001-164">**[UI 控制項](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="b5001-164">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-165">[![解算器](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-165">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="b5001-166">**[解算器](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-166">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-167">[![多場景管理員](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-167">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b5001-168">**[多場景 <br/> 管理員](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-168">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-169">[![空間感知](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-169">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="b5001-170">**[空間 <br/> 感知](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-170">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-171">[![診斷工具](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-171">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b5001-172">**[診斷 <br/> 工具](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-172">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-173">[![MRTK 標準著色器視圖](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="b5001-173">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="b5001-174">**[MRTK 標準著色器範例視圖](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="b5001-174">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-175">[![語音 & 聽寫](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-175">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b5001-176">**[](features/input/speech.md) <br/> 語音  & [聽寫](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-176">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-177">[![界限系統](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-177">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b5001-178">**[界限 <br/> 系統](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-178">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-179">[![編輯器內模擬](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-179">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b5001-180">**[編輯器內 <br/> 模擬](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-180">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-181">[![實驗性功能](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-181">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="b5001-182">**[實驗性 <br/> 功能](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-182">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="b5001-183">UX 組建區塊</span><span class="sxs-lookup"><span data-stu-id="b5001-183">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="b5001-184">[ ![ 按鈕](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[按鈕](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-184">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="b5001-185">支援各種輸入方法的按鈕控制項，包括 HoloLens 2 的有向的手勢</span><span class="sxs-lookup"><span data-stu-id="b5001-185">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-186">[ ![ 界限控制項](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[界限控制項](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-186">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="b5001-187">在3D 空間中操作物件的標準 UI</span><span class="sxs-lookup"><span data-stu-id="b5001-187">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-188">[ ![ 物件](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md)操作工具 **[物件](features/ux-building-blocks/object-manipulator.md)操作工具**</span><span class="sxs-lookup"><span data-stu-id="b5001-188">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="b5001-189">以一或兩個手中操作物件的腳本</span><span class="sxs-lookup"><span data-stu-id="b5001-189">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-190">[ ![ 平板](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[平板](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-190">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="b5001-191">2D 樣式平面，支援以已明確表達的手寫輸入進行滾動</span><span class="sxs-lookup"><span data-stu-id="b5001-191">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-192">[ ![ 系統鍵盤](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[系統鍵盤](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-192">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="b5001-193">在 Unity 中使用系統鍵盤的範例腳本</span><span class="sxs-lookup"><span data-stu-id="b5001-193">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-194">[ ![ 互動](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[互動](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-194">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="b5001-195">使用視覺狀態和主題支援讓物件互動的腳本</span><span class="sxs-lookup"><span data-stu-id="b5001-195">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-196">[ ![ 規劃](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md)求解 **[規劃](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-196">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="b5001-197">各種物件定位行為，例如標記-沿著標記、主體鎖定、常數視圖大小和表面磁性</span><span class="sxs-lookup"><span data-stu-id="b5001-197">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-198">[ ![ 物件集合](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[物件集合](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-198">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="b5001-199">在三維圖形中設定物件陣列的腳本</span><span class="sxs-lookup"><span data-stu-id="b5001-199">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-200">[ ![ 工具](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md)提示 **[工具提示](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-200">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="b5001-201">具有彈性錨點/pivot 系統的注釋 UI，可用來標記動作控制器和物件</span><span class="sxs-lookup"><span data-stu-id="b5001-201">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-202">[ ![ 滑杆](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[滑杆](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-202">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="b5001-203">調整支援直接追蹤互動之值的滑杆 UI</span><span class="sxs-lookup"><span data-stu-id="b5001-203">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-204">[ ![ MRTK 標準著色器](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK 標準著色器](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-204">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="b5001-205">MRTK 的標準著色器可支援各種流暢的設計項目與效能</span><span class="sxs-lookup"><span data-stu-id="b5001-205">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-206">[ ![ 手形功能表](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[](features/ux-building-blocks/hand-menu.md)功能表**</span><span class="sxs-lookup"><span data-stu-id="b5001-206">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="b5001-207">使用手形條件約束規劃的手動鎖定 UI，以進行快速存取</span><span class="sxs-lookup"><span data-stu-id="b5001-207">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-208">[ ![ 應用程式行](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[應用程式行](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-208">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="b5001-209">界限控制項手動啟用的 UI</span><span class="sxs-lookup"><span data-stu-id="b5001-209">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-210">[ ![ 指標](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[指標](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-210">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="b5001-211">瞭解各種類型的指標</span><span class="sxs-lookup"><span data-stu-id="b5001-211">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-212">[ ![ Fingertip 視覺效果](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip 視覺效果](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-212">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="b5001-213">Fingertip 上的視覺效果 affordance，可改善直接互動的信賴度</span><span class="sxs-lookup"><span data-stu-id="b5001-213">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-214">靠近功能表的 [ ![ 附近功能表](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-214">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="b5001-215">接近互動的浮動功能表 UI</span><span class="sxs-lookup"><span data-stu-id="b5001-215">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-216">[ ![ 空間感知入門入門](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[空間感知視圖](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-216">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="b5001-217">讓您的全像攝影物件與實體環境互動</span><span class="sxs-lookup"><span data-stu-id="b5001-217">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-218">[ ![ Voice 命令](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[voice 命令](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-218">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="b5001-219">整合語音輸入的腳本和範例</span><span class="sxs-lookup"><span data-stu-id="b5001-219">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-220">[ ![ 進度指示器](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[進度指標](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-220">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="b5001-221">用於傳達資料處理或作業的視覺化指標</span><span class="sxs-lookup"><span data-stu-id="b5001-221">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-222">[ ![ 對話方塊](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[對話方塊](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-222">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="b5001-223">要求使用者確認或確認的 UI</span><span class="sxs-lookup"><span data-stu-id="b5001-223">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-224">[ ![ 手動指導](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-224">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="b5001-225">當手勢未教授時，可協助引導使用者的元件</span><span class="sxs-lookup"><span data-stu-id="b5001-225">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-226">[ ![ 手物理服務](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md)的 **[物理服務 [實驗]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-226">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="b5001-227">實際的物理服務可讓您透過明確的方式進行固定的內文衝突事件和互動</span><span class="sxs-lookup"><span data-stu-id="b5001-227">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-228">[ ![ 滾動集合](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[滾動集合](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-228">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="b5001-229">原生滾動3D 物件的物件集合</span><span class="sxs-lookup"><span data-stu-id="b5001-229">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-230">[ ![](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md)停駐 **[固定 [實驗]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-230">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="b5001-231">Dock 允許將物件移入和移出預定的位置</span><span class="sxs-lookup"><span data-stu-id="b5001-231">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b5001-232">[ ![ 眼睛追蹤：目標選擇](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[眼睛追蹤：目標選取範圍](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-232">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="b5001-233">結合眼睛、語音和手輸入，以快速且輕鬆地在場景中選取全像影像</span><span class="sxs-lookup"><span data-stu-id="b5001-233">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-234">[ ![ 眼睛追蹤：導覽](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[眼睛追蹤：導覽](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="b5001-234">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="b5001-235">瞭解如何根據您要查看的內容，自動滾動文字或流暢縮放至焦點內容</span><span class="sxs-lookup"><span data-stu-id="b5001-235">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b5001-236">[ ![ 眼睛追蹤：熱度圖](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[視覺追蹤：熱度圖](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="b5001-236">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="b5001-237">記錄、載入和視覺化使用者在您的應用程式中查看的範例</span><span class="sxs-lookup"><span data-stu-id="b5001-237">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="b5001-238">工具</span><span class="sxs-lookup"><span data-stu-id="b5001-238">Tools</span></span>

|  <span data-ttu-id="b5001-239">[ ![ 優化視窗](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md)[優化視窗](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-239">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="b5001-240">相依性[ ![ 視窗](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md)相依性[視窗](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-240">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![組建視窗](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="b5001-242">組建視窗</span><span class="sxs-lookup"><span data-stu-id="b5001-242">Build Window</span></span> | <span data-ttu-id="b5001-243">[ ![ 輸入錄製](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md)[輸入記錄](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-243">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="b5001-244">自動設定混合現實專案以進行效能優化</span><span class="sxs-lookup"><span data-stu-id="b5001-244">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="b5001-245">分析資產之間的相依性，並找出未使用的資產</span><span class="sxs-lookup"><span data-stu-id="b5001-245">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="b5001-246">設定及執行混合現實應用程式的端對端組建程式</span><span class="sxs-lookup"><span data-stu-id="b5001-246">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="b5001-247">在編輯器中錄製並播放前端移動和手動追蹤資料</span><span class="sxs-lookup"><span data-stu-id="b5001-247">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="b5001-248">範例場景</span><span class="sxs-lookup"><span data-stu-id="b5001-248">Example scenes</span></span>

<span data-ttu-id="b5001-249">探索 MRTK 在 [此範例場景](features/example-scenes/hand-interaction-examples.md)中的各種互動和 UI 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="b5001-249">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="b5001-250">[![範例場景2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-250">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="b5001-251">MRTK 範例中樞</span><span class="sxs-lookup"><span data-stu-id="b5001-251">MRTK examples hub</span></span>

<span data-ttu-id="b5001-252">您可以使用 MRTK 範例中樞來嘗試 MRTK 中的各種範例場景。</span><span class="sxs-lookup"><span data-stu-id="b5001-252">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="b5001-253">您可以在「 [MR」功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)中選取「混合現實工具組範例」套件，以下載預先建立的 HoloLens (x86) 、HOLOLENS 2 (ARM) 和 Windows Mixed Reality 沉浸式耳機 (x64) 。</span><span class="sxs-lookup"><span data-stu-id="b5001-253">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="b5001-254">請務必 [使用 Windows 裝置入口網站在 HoloLens (第1代) 上安裝應用程式 ](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)。</span><span class="sxs-lookup"><span data-stu-id="b5001-254">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="b5001-255">在 HoloLens 2 上，您可以 [透過 Microsoft Store 應用程式下載並安裝 MRTK 範例中樞](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)。</span><span class="sxs-lookup"><span data-stu-id="b5001-255">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="b5001-256">請參閱 [範例中樞的讀我檔案頁面](features/example-scenes/example-hub.md) ，以瞭解如何使用 MRTK 的場景系統和場景轉換服務建立多場景中樞的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b5001-256">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="b5001-257">[![範例場景中樞](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-257">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="b5001-258">使用 MRTK 建立的範例應用程式</span><span class="sxs-lookup"><span data-stu-id="b5001-258">Sample apps made with MRTK</span></span>

| <span data-ttu-id="b5001-259">[![元素週期表](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="b5001-259">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="b5001-260">[![星系探險](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="b5001-260">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="b5001-261">[![表面範例應用程式](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="b5001-261">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="b5001-262">專案的[定期資料表](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)是開放原始碼範例應用程式，示範如何使用 MRTK 的輸入系統和建立區塊來建立 HoloLens 和沉浸式耳機的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="b5001-262">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="b5001-263">閱讀移植案例：將專案 [應用程式的定期資料表帶入 MRTK v2 以 HoloLens 2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="b5001-263">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="b5001-264">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) 是一種開放原始碼範例應用程式，最初是在2016年3月的「分享您的想法」活動中所開發。</span><span class="sxs-lookup"><span data-stu-id="b5001-264">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="b5001-265">已使用 MRTK v2，以 HoloLens 2 的新功能更新了 Galaxy Explorer。</span><span class="sxs-lookup"><span data-stu-id="b5001-265">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="b5001-266">閱讀這篇文章： [HoloLens 2 的 Galaxy Explorer](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="b5001-266">Read the story: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="b5001-267">介面是 HoloLens 2 的開放原始碼範例應用程式，[它會探索](https://github.com/microsoft/MRDL_Unity_Surfaces)如何使用視覺效果、音訊和完全帶清楚方式的手動追蹤來建立 tactile 刺痛。</span><span class="sxs-lookup"><span data-stu-id="b5001-267">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="b5001-268">查看 Microsoft MR Dev Days session [學習 from surface 應用程式](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) ，以取得詳細的設計和開發案例。</span><span class="sxs-lookup"><span data-stu-id="b5001-268">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="b5001-269">來自混合現實開發日2020的研討會影片</span><span class="sxs-lookup"><span data-stu-id="b5001-269">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="b5001-270">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="b5001-270">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="b5001-271">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="b5001-271">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="b5001-272">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="b5001-272">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="b5001-273">如何建立從開始到完成的簡單 MRTK 應用程式的教學課程。</span><span class="sxs-lookup"><span data-stu-id="b5001-273">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="b5001-274">瞭解互動概念和 MRTK 的多平臺功能。</span><span class="sxs-lookup"><span data-stu-id="b5001-274">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="b5001-275">深入探討 MRTK 的 UX 構成要素，協助您打造美觀的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="b5001-275">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="b5001-276">MRTK 和外部的效能工具簡介，以及 MRTK 標準著色器的總覽。</span><span class="sxs-lookup"><span data-stu-id="b5001-276">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="b5001-277">若要探索更多課程影片，請參閱 [混合現實開發日](/windows/mixed-reality/mr-dev-days-sessions) 。</span><span class="sxs-lookup"><span data-stu-id="b5001-277">See [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="b5001-278">與社區互動</span><span class="sxs-lookup"><span data-stu-id="b5001-278">Engage with the community</span></span>

* <span data-ttu-id="b5001-279">在 MRTK 上加入關於 [時差](https://holodevelopers.slack.com/)的交談。</span><span class="sxs-lookup"><span data-stu-id="b5001-279">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="b5001-280">您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。</span><span class="sxs-lookup"><span data-stu-id="b5001-280">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="b5001-281">使用 **MRTK** 標記詢問有關在 [STACK OVERFLOW](https://stackoverflow.com/questions/tagged/mrtk)上使用 MRTK 的問題。</span><span class="sxs-lookup"><span data-stu-id="b5001-281">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="b5001-282">如果您發現 MRTK 程式碼中有問題，請搜尋 [已知問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 或提出 [新問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 。</span><span class="sxs-lookup"><span data-stu-id="b5001-282">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="b5001-283">如有關于參與 MRTK 的問題，請移至「 [混合現實」工具](https://holodevelopers.slack.com/messages/C2H4HT858) 組頻道的時差。</span><span class="sxs-lookup"><span data-stu-id="b5001-283">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="b5001-284">此專案採用了 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="b5001-284">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="b5001-285">如需詳細資訊，請參閱[管理辦法常見問題集](https://opensource.microsoft.com/codeofconduct/faq/)，如有其他問題或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="b5001-285">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="b5001-286">混合現實開發人員中心上的實用資源</span><span class="sxs-lookup"><span data-stu-id="b5001-286">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="b5001-287">![探索 ](features/images/mrdevcenter/icon-discover.png) [探索](/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="b5001-287">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](/windows/mixed-reality/)</span></span>| <span data-ttu-id="b5001-288">![設計 ](features/images/mrdevcenter/icon-design.png) [設計](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="b5001-288">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span></span>| <span data-ttu-id="b5001-289">![開發 ](features/images/mrdevcenter/icon-develop.png) [開發](/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="b5001-289">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](/windows/mixed-reality/development)</span></span>| <span data-ttu-id="b5001-290">![散發) ](features/images/mrdevcenter/icon-distribute.png) [散發](/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="b5001-290">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="b5001-291">瞭解如何建立 HoloLens 和沉浸式耳機的混合現實體驗 (VR) 。</span><span class="sxs-lookup"><span data-stu-id="b5001-291">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="b5001-292">取得設計指南。</span><span class="sxs-lookup"><span data-stu-id="b5001-292">Get design guides.</span></span> <span data-ttu-id="b5001-293">建立使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b5001-293">Build user interface.</span></span> <span data-ttu-id="b5001-294">瞭解互動和輸入。</span><span class="sxs-lookup"><span data-stu-id="b5001-294">Learn interactions and input.</span></span>     | <span data-ttu-id="b5001-295">取得開發指南。</span><span class="sxs-lookup"><span data-stu-id="b5001-295">Get development guides.</span></span> <span data-ttu-id="b5001-296">學習技術。</span><span class="sxs-lookup"><span data-stu-id="b5001-296">Learn the technology.</span></span> <span data-ttu-id="b5001-297">瞭解科學。</span><span class="sxs-lookup"><span data-stu-id="b5001-297">Understand the science.</span></span>       | <span data-ttu-id="b5001-298">準備好您的應用程式以供其他人使用，並考慮建立 3D 啟動器。</span><span class="sxs-lookup"><span data-stu-id="b5001-298">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="b5001-299">Azure 上的實用資源</span><span class="sxs-lookup"><span data-stu-id="b5001-299">Useful resources on Azure</span></span>

| <span data-ttu-id="b5001-300">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="b5001-300">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="b5001-301">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="b5001-301">Spatial Anchors</span></span>](/azure/spatial-anchors/)| <span data-ttu-id="b5001-302">![語音服務](features/images/mrdevcenter/icon-azurespeechservices.png) [語音服務](/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="b5001-302">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="b5001-303">![視覺服務 ](features/images/mrdevcenter/icon-azurevisionservices.png) [視覺服務](/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="b5001-303">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="b5001-304">空間錨點是一種跨平臺服務，可讓您使用在一段時間內跨裝置保存其位置的物件，建立混合的現實體驗。</span><span class="sxs-lookup"><span data-stu-id="b5001-304">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="b5001-305">探索及整合 Azure 提供的語音功能，例如語音轉換文字、說話者辨識或語音翻譯至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b5001-305">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="b5001-306">使用視覺服務識別並分析您的影像或視訊內容，例如電腦視覺、臉部偵測、表情辨識或影片索引器。</span><span class="sxs-lookup"><span data-stu-id="b5001-306">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="b5001-307">如何參與</span><span class="sxs-lookup"><span data-stu-id="b5001-307">How to contribute</span></span>

<span data-ttu-id="b5001-308">瞭解您[如何參與 MRTK 的貢獻。](contributing/contributing.md)</span><span class="sxs-lookup"><span data-stu-id="b5001-308">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="b5001-309">取得說明</span><span class="sxs-lookup"><span data-stu-id="b5001-309">Getting help</span></span>

<span data-ttu-id="b5001-310">如果您遇到 MRTK 所造成的問題，或是有關于如何執行某些問題的問題，有一些資源可以提供協助：</span><span class="sxs-lookup"><span data-stu-id="b5001-310">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="b5001-311">針對錯誤報表，請在 GitHub 存放庫上提出 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) 。</span><span class="sxs-lookup"><span data-stu-id="b5001-311">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="b5001-312">如有任何問題，請在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 或「 [混合現實」工具組頻道](https://holodevelopers.slack.com/messages/C2H4HT858) 的時差上聯繫。</span><span class="sxs-lookup"><span data-stu-id="b5001-312">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="b5001-313">您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。</span><span class="sxs-lookup"><span data-stu-id="b5001-313">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>