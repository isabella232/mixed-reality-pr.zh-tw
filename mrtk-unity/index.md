---
title: MRTK-Unity 開發人員檔
description: 瞭解 Unity 的混合現實工具組。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK
ms.openlocfilehash: 85a203f22c62871265f7775c364f5388194b53a1
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550968"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="f45d3-104">何謂混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="f45d3-104">What is the Mixed Reality Toolkit</span></span>

![混合實境工具組](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="f45d3-106">MRTK-Unity 是由 Microsoft 所推動的專案，其提供一組元件與功能，可用來加快 Unity 中的跨平台 MR 應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="f45d3-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="f45d3-107">以下是其中的一些功能：</span><span class="sxs-lookup"><span data-stu-id="f45d3-107">Here are some of its functions:</span></span>

* <span data-ttu-id="f45d3-108">提供 **空間互動和 UI 的跨平臺輸入系統和建立區塊**。</span><span class="sxs-lookup"><span data-stu-id="f45d3-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="f45d3-109">透過可讓您立即查看變更的編輯器內模擬，讓您能夠 **快速建立原型** 。</span><span class="sxs-lookup"><span data-stu-id="f45d3-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="f45d3-110">以可擴充的 **架構** 運作，讓開發人員能夠交換核心元件。</span><span class="sxs-lookup"><span data-stu-id="f45d3-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="f45d3-111">**支援多種平臺**，包括</span><span class="sxs-lookup"><span data-stu-id="f45d3-111">**Supports a wide range of platforms**, including</span></span>
  * <span data-ttu-id="f45d3-112">OpenXR (Unity 2020.2 或更新版本) </span><span class="sxs-lookup"><span data-stu-id="f45d3-112">OpenXR (Unity 2020.2 or newer)</span></span>
    * <span data-ttu-id="f45d3-113">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f45d3-113">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="f45d3-114">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="f45d3-114">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="f45d3-115">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f45d3-115">Windows Mixed Reality</span></span>
    * <span data-ttu-id="f45d3-116">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="f45d3-116">Microsoft HoloLens</span></span>
    * <span data-ttu-id="f45d3-117">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f45d3-117">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="f45d3-118">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="f45d3-118">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="f45d3-119">Oculus (Unity 2019.3 或更新版本) </span><span class="sxs-lookup"><span data-stu-id="f45d3-119">Oculus (Unity 2019.3 or newer)</span></span>
    * <span data-ttu-id="f45d3-120">Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="f45d3-120">Oculus Quest</span></span>
  * <span data-ttu-id="f45d3-121">OpenVR</span><span class="sxs-lookup"><span data-stu-id="f45d3-121">OpenVR</span></span>
    * <span data-ttu-id="f45d3-122">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="f45d3-122">Windows Mixed Reality headsets</span></span>
    * <span data-ttu-id="f45d3-123">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="f45d3-123">HTC Vive</span></span>
    * <span data-ttu-id="f45d3-124">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="f45d3-124">Oculus Rift</span></span>
  * <span data-ttu-id="f45d3-125">Ultraleap 手部追蹤</span><span class="sxs-lookup"><span data-stu-id="f45d3-125">Ultraleap Hand Tracking</span></span>
  * <span data-ttu-id="f45d3-126">IOS 和 Android 等行動裝置</span><span class="sxs-lookup"><span data-stu-id="f45d3-126">Mobile devices such as iOS and Android</span></span>

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="f45d3-127">開始使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="f45d3-127">Getting started with MRTK</span></span>

<span data-ttu-id="f45d3-128">如果您不熟悉 Unity 中的 MRTK 或混合現實開發，建議您安裝必要的工具，然後遵循 HoloLens 2 的教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="f45d3-128">If you're new to MRTK or Mixed Reality development in Unity, we recommend you install the necessary tools and then follow the HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f45d3-129">安裝工具</span><span class="sxs-lookup"><span data-stu-id="f45d3-129">Install the Tools</span></span>](install-the-tools.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="f45d3-130">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="f45d3-130">HoloLens 2 Tutorial Series</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="f45d3-131">想要看看幕後的進展嗎？</span><span class="sxs-lookup"><span data-stu-id="f45d3-131">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f45d3-132">探索 GitHub 上的 MRTK</span><span class="sxs-lookup"><span data-stu-id="f45d3-132">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="f45d3-133">文件</span><span class="sxs-lookup"><span data-stu-id="f45d3-133">Documentation</span></span>

| <span data-ttu-id="f45d3-134">[![版本資訊](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-134">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="f45d3-135">版本資訊</span><span class="sxs-lookup"><span data-stu-id="f45d3-135">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="f45d3-136">[![MRTK 總覽](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-136">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="f45d3-137">MRTK 總覽</span><span class="sxs-lookup"><span data-stu-id="f45d3-137">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="f45d3-138">[![應用程式開發介面參考](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="f45d3-138">[![API Reference](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="f45d3-139">API 參考</span><span class="sxs-lookup"><span data-stu-id="f45d3-139">API Reference</span></span>](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="f45d3-140">組建狀態</span><span class="sxs-lookup"><span data-stu-id="f45d3-140">Build status</span></span>

| <span data-ttu-id="f45d3-141">分支</span><span class="sxs-lookup"><span data-stu-id="f45d3-141">Branch</span></span> | <span data-ttu-id="f45d3-142">CI 狀態</span><span class="sxs-lookup"><span data-stu-id="f45d3-142">CI Status</span></span> | <span data-ttu-id="f45d3-143">檔狀態</span><span class="sxs-lookup"><span data-stu-id="f45d3-143">Docs Status</span></span> |
|---|---|---|
| `mrtk_development` |<span data-ttu-id="f45d3-144">[![CI 狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="f45d3-144">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="f45d3-145">[![檔狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="f45d3-145">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="f45d3-146">功能範圍</span><span class="sxs-lookup"><span data-stu-id="f45d3-146">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-147">[![輸入系統](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-147">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="f45d3-148">**[輸入系統](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-148">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-149">[![手動追蹤 (HoloLens 2) ](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-149">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="f45d3-150">**[手動追蹤 <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-150">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-151">[![ (HoloLens 2) 的眼睛追蹤 ](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-151">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="f45d3-152">**[<br/> (HoloLens 2) 的眼睛追蹤](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-152">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-153">[![配置 檔](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-153">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="f45d3-154">**[配置 檔](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-154">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-155">[![ (Ultraleap) 的手動追蹤 ](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-155">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="f45d3-156">**[<br/> (Ultraleap) 的手動追蹤](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-156">**[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-157">[![UI 控制項](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="f45d3-157">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="f45d3-158">**[UI 控制項](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-158">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-159">[![解算器](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-159">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="f45d3-160">**[解算器](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-160">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-161">[![多場景管理員](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-161">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="f45d3-162">**[多場景 <br/> 管理員](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-162">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-163">[![空間感知](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-163">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="f45d3-164">**[空間 <br/> 感知](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-164">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-165">[![診斷工具](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-165">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="f45d3-166">**[診斷 <br/> 工具](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-166">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-167">[![MRTK 標準著色器視圖](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="f45d3-167">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="f45d3-168">**[MRTK 標準著色器範例視圖](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-168">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-169">[![語音 & 聽寫](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-169">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="f45d3-170">**[](features/input/speech.md) <br/> 語音  & [聽寫](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-170">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-171">[![界限系統](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-171">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="f45d3-172">**[界限 <br/> 系統](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-172">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-173">[![編輯器內模擬](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-173">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="f45d3-174">**[編輯器內 <br/> 模擬](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-174">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-175">[![實驗性功能](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-175">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="f45d3-176">**[實驗性 <br/> 功能](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-176">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="f45d3-177">UX 組建區塊</span><span class="sxs-lookup"><span data-stu-id="f45d3-177">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-178">[ ![ 按鈕](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[按鈕](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-178">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="f45d3-179">支援各種輸入方法的按鈕控制項，包括 HoloLens 2 的有向的手勢</span><span class="sxs-lookup"><span data-stu-id="f45d3-179">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-180">[ ![ 界限控制項](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[界限控制項](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-180">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="f45d3-181">在3D 空間中操作物件的標準 UI</span><span class="sxs-lookup"><span data-stu-id="f45d3-181">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-182">[ ![ 物件](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md)操作工具 **[物件](features/ux-building-blocks/object-manipulator.md)操作工具**</span><span class="sxs-lookup"><span data-stu-id="f45d3-182">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="f45d3-183">以一或兩個手中操作物件的腳本</span><span class="sxs-lookup"><span data-stu-id="f45d3-183">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-184">[ ![ 平板](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[平板](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-184">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="f45d3-185">2D 樣式平面，支援以已明確表達的手寫輸入進行滾動</span><span class="sxs-lookup"><span data-stu-id="f45d3-185">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-186">[ ![ 系統鍵盤](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[系統鍵盤](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-186">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="f45d3-187">在 Unity 中使用系統鍵盤的範例腳本</span><span class="sxs-lookup"><span data-stu-id="f45d3-187">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-188">[ ![ 互動](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[互動](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-188">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="f45d3-189">使用視覺狀態和主題支援讓物件互動的腳本</span><span class="sxs-lookup"><span data-stu-id="f45d3-189">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-190">[ ![ 規劃](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md)求解 **[規劃](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-190">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="f45d3-191">各種物件定位行為，例如標記-沿著標記、主體鎖定、常數視圖大小和表面磁性</span><span class="sxs-lookup"><span data-stu-id="f45d3-191">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-192">[ ![ 物件集合](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[物件集合](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-192">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="f45d3-193">在三維圖形中設定物件陣列的腳本</span><span class="sxs-lookup"><span data-stu-id="f45d3-193">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-194">[ ![ 工具](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md)提示 **[工具提示](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-194">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="f45d3-195">具有彈性錨點/pivot 系統的注釋 UI，可用來標記動作控制器和物件</span><span class="sxs-lookup"><span data-stu-id="f45d3-195">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-196">[ ![ 滑杆](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[滑杆](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-196">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="f45d3-197">調整支援直接追蹤互動之值的滑杆 UI</span><span class="sxs-lookup"><span data-stu-id="f45d3-197">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-198">[ ![ MRTK 標準著色器](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK 標準著色器](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-198">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="f45d3-199">MRTK 的標準著色器可支援各種流暢的設計項目與效能</span><span class="sxs-lookup"><span data-stu-id="f45d3-199">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-200">[ ![ 手形功能表](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[](features/ux-building-blocks/hand-menu.md)功能表**</span><span class="sxs-lookup"><span data-stu-id="f45d3-200">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="f45d3-201">使用手形條件約束規劃的手動鎖定 UI，以進行快速存取</span><span class="sxs-lookup"><span data-stu-id="f45d3-201">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-202">[ ![ 應用程式行](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[應用程式行](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-202">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="f45d3-203">界限控制項手動啟用的 UI</span><span class="sxs-lookup"><span data-stu-id="f45d3-203">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-204">[ ![ 指標](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[指標](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-204">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="f45d3-205">瞭解各種類型的指標</span><span class="sxs-lookup"><span data-stu-id="f45d3-205">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-206">[ ![ Fingertip 視覺效果](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip 視覺效果](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-206">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="f45d3-207">Fingertip 上的視覺效果 affordance，可改善直接互動的信賴度</span><span class="sxs-lookup"><span data-stu-id="f45d3-207">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-208">靠近功能表的 [ ![ 附近功能表](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-208">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="f45d3-209">接近互動的浮動功能表 UI</span><span class="sxs-lookup"><span data-stu-id="f45d3-209">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-210">[ ![ 空間感知入門入門](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[空間感知視圖](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-210">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="f45d3-211">讓您的全像攝影物件與實體環境互動</span><span class="sxs-lookup"><span data-stu-id="f45d3-211">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-212">[ ![ Voice 命令](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[voice 命令](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-212">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="f45d3-213">整合語音輸入的腳本和範例</span><span class="sxs-lookup"><span data-stu-id="f45d3-213">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-214">[ ![ 進度指示器](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[進度指標](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-214">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="f45d3-215">用於傳達資料處理或作業的視覺化指標</span><span class="sxs-lookup"><span data-stu-id="f45d3-215">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-216">[ ![ 對話方塊](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[對話方塊](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-216">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="f45d3-217">要求使用者確認或確認的 UI</span><span class="sxs-lookup"><span data-stu-id="f45d3-217">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-218">[ ![ 手動指導](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-218">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="f45d3-219">當手勢未教授時，可協助引導使用者的元件</span><span class="sxs-lookup"><span data-stu-id="f45d3-219">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-220">[ ![ 手物理服務](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md)的 **[物理服務 [實驗]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-220">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="f45d3-221">實際的物理服務可讓您透過明確的方式進行固定的內文衝突事件和互動</span><span class="sxs-lookup"><span data-stu-id="f45d3-221">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-222">[ ![ 滾動集合](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[滾動集合](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-222">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="f45d3-223">原生滾動3D 物件的物件集合</span><span class="sxs-lookup"><span data-stu-id="f45d3-223">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-224">[ ![](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md)停駐 **[固定 [實驗]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-224">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="f45d3-225">Dock 允許將物件移入和移出預定的位置</span><span class="sxs-lookup"><span data-stu-id="f45d3-225">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="f45d3-226">[ ![ 眼睛追蹤：目標選擇](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[眼睛追蹤：目標選取範圍](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-226">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="f45d3-227">結合眼睛、語音和手輸入，以快速且輕鬆地在場景中選取全像影像</span><span class="sxs-lookup"><span data-stu-id="f45d3-227">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-228">[ ![ 眼睛追蹤：導覽](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[眼睛追蹤：導覽](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-228">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="f45d3-229">瞭解如何根據您要查看的內容，自動滾動文字或流暢縮放至焦點內容</span><span class="sxs-lookup"><span data-stu-id="f45d3-229">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f45d3-230">[ ![ 眼睛追蹤：熱度圖](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[視覺追蹤：熱度圖](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="f45d3-230">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="f45d3-231">記錄、載入和視覺化使用者在您的應用程式中查看的範例</span><span class="sxs-lookup"><span data-stu-id="f45d3-231">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="f45d3-232">工具</span><span class="sxs-lookup"><span data-stu-id="f45d3-232">Tools</span></span>

|  <span data-ttu-id="f45d3-233">[ ![ 優化視窗](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md)[優化視窗](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-233">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="f45d3-234">相依性[ ![ 視窗](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md)相依性[視窗](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-234">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![組建視窗](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="f45d3-236">組建視窗</span><span class="sxs-lookup"><span data-stu-id="f45d3-236">Build Window</span></span> | <span data-ttu-id="f45d3-237">[ ![ 輸入錄製](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md)[輸入記錄](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-237">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="f45d3-238">自動設定混合現實專案以進行效能優化</span><span class="sxs-lookup"><span data-stu-id="f45d3-238">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="f45d3-239">分析資產之間的相依性，並找出未使用的資產</span><span class="sxs-lookup"><span data-stu-id="f45d3-239">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="f45d3-240">設定及執行混合現實應用程式的端對端組建程式</span><span class="sxs-lookup"><span data-stu-id="f45d3-240">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="f45d3-241">在編輯器中錄製並播放前端移動和手動追蹤資料</span><span class="sxs-lookup"><span data-stu-id="f45d3-241">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="f45d3-242">範例場景</span><span class="sxs-lookup"><span data-stu-id="f45d3-242">Example scenes</span></span>

<span data-ttu-id="f45d3-243">探索 MRTK 在 [此範例場景](features/example-scenes/hand-interaction-examples.md)中的各種互動和 UI 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="f45d3-243">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="f45d3-244">[![範例場景2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-244">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="f45d3-245">MRTK 範例中樞</span><span class="sxs-lookup"><span data-stu-id="f45d3-245">MRTK examples hub</span></span>

<span data-ttu-id="f45d3-246">您可以使用 MRTK 範例中樞來嘗試 MRTK 中的各種範例場景。</span><span class="sxs-lookup"><span data-stu-id="f45d3-246">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="f45d3-247">您可以在「 [MR」功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)中選取「混合現實工具組範例」套件，以下載預先建立的 HoloLens (x86) 、HOLOLENS 2 (ARM) 和 Windows Mixed Reality 沉浸式耳機 (x64) 。</span><span class="sxs-lookup"><span data-stu-id="f45d3-247">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="f45d3-248">請務必 [使用 Windows 裝置入口網站在 HoloLens (第1代) 上安裝應用程式 ](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)。</span><span class="sxs-lookup"><span data-stu-id="f45d3-248">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="f45d3-249">在 HoloLens 2 上，您可以 [透過 Microsoft Store 應用程式下載並安裝 MRTK 範例中樞](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)。</span><span class="sxs-lookup"><span data-stu-id="f45d3-249">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="f45d3-250">請參閱 [範例中樞的讀我檔案頁面](features/example-scenes/example-hub.md) ，以瞭解如何使用 MRTK 的場景系統和場景轉換服務建立多場景中樞的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f45d3-250">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="f45d3-251">[![範例場景中樞](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-251">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="f45d3-252">使用 MRTK 建立的範例應用程式</span><span class="sxs-lookup"><span data-stu-id="f45d3-252">Sample apps made with MRTK</span></span>

| <span data-ttu-id="f45d3-253">[![元素週期表](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="f45d3-253">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="f45d3-254">[![星系探險](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="f45d3-254">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="f45d3-255">[![表面範例應用程式](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="f45d3-255">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="f45d3-256">專案的[定期資料表](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)是開放原始碼範例應用程式，示範如何使用 MRTK 的輸入系統和建立區塊來建立 HoloLens 和沉浸式耳機的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="f45d3-256">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="f45d3-257">閱讀移植案例：將專案 [應用程式的定期資料表帶入 MRTK v2 以 HoloLens 2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="f45d3-257">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="f45d3-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) 是一種開放原始碼範例應用程式，最初是在2016年3月的「分享您的想法」活動中所開發。</span><span class="sxs-lookup"><span data-stu-id="f45d3-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="f45d3-259">已使用 MRTK v2，以 HoloLens 2 的新功能更新了 Galaxy Explorer。</span><span class="sxs-lookup"><span data-stu-id="f45d3-259">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="f45d3-260">閱讀這篇文章： [HoloLens 2 的 Galaxy Explorer](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="f45d3-260">Read the story: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="f45d3-261">介面是 HoloLens 2 的開放原始碼範例應用程式，[它會探索](https://github.com/microsoft/MRDL_Unity_Surfaces)如何使用視覺效果、音訊和完全帶清楚方式的手動追蹤來建立 tactile 刺痛。</span><span class="sxs-lookup"><span data-stu-id="f45d3-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="f45d3-262">查看 Microsoft MR Dev Days session [學習 from surface 應用程式](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) ，以取得詳細的設計和開發案例。</span><span class="sxs-lookup"><span data-stu-id="f45d3-262">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="f45d3-263">來自混合現實開發日2020的研討會影片</span><span class="sxs-lookup"><span data-stu-id="f45d3-263">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="f45d3-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="f45d3-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="f45d3-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="f45d3-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="f45d3-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="f45d3-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="f45d3-267">如何建立從開始到完成的簡單 MRTK 應用程式的教學課程。</span><span class="sxs-lookup"><span data-stu-id="f45d3-267">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="f45d3-268">瞭解互動概念和 MRTK 的多平臺功能。</span><span class="sxs-lookup"><span data-stu-id="f45d3-268">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="f45d3-269">深入探討 MRTK 的 UX 構成要素，協助您打造美觀的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="f45d3-269">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="f45d3-270">MRTK 和外部的效能工具簡介，以及 MRTK 標準著色器的總覽。</span><span class="sxs-lookup"><span data-stu-id="f45d3-270">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="f45d3-271">若要探索更多課程影片，請參閱 [混合現實開發日](/windows/mixed-reality/mr-dev-days-sessions) 。</span><span class="sxs-lookup"><span data-stu-id="f45d3-271">See [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="f45d3-272">與社區互動</span><span class="sxs-lookup"><span data-stu-id="f45d3-272">Engage with the community</span></span>

* <span data-ttu-id="f45d3-273">在 MRTK 上加入關於 [時差](https://holodevelopers.slack.com/)的交談。</span><span class="sxs-lookup"><span data-stu-id="f45d3-273">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="f45d3-274">您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。</span><span class="sxs-lookup"><span data-stu-id="f45d3-274">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="f45d3-275">使用 **MRTK** 標記詢問有關在 [STACK OVERFLOW](https://stackoverflow.com/questions/tagged/mrtk)上使用 MRTK 的問題。</span><span class="sxs-lookup"><span data-stu-id="f45d3-275">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="f45d3-276">如果您發現 MRTK 程式碼中有問題，請搜尋 [已知問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 或提出 [新問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 。</span><span class="sxs-lookup"><span data-stu-id="f45d3-276">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="f45d3-277">如有關于參與 MRTK 的問題，請移至「 [混合現實」工具](https://holodevelopers.slack.com/messages/C2H4HT858) 組頻道的時差。</span><span class="sxs-lookup"><span data-stu-id="f45d3-277">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="f45d3-278">此專案採用了 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="f45d3-278">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="f45d3-279">如需詳細資訊，請參閱[管理辦法常見問題集](https://opensource.microsoft.com/codeofconduct/faq/)，如有其他問題或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="f45d3-279">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="f45d3-280">混合現實開發人員中心上的實用資源</span><span class="sxs-lookup"><span data-stu-id="f45d3-280">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="f45d3-281">![探索 ](features/images/mrdevcenter/icon-discover.png) [探索](/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="f45d3-281">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](/windows/mixed-reality/)</span></span>| <span data-ttu-id="f45d3-282">![設計 ](features/images/mrdevcenter/icon-design.png) [設計](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="f45d3-282">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span></span>| <span data-ttu-id="f45d3-283">![開發 ](features/images/mrdevcenter/icon-develop.png) [開發](/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="f45d3-283">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](/windows/mixed-reality/development)</span></span>| <span data-ttu-id="f45d3-284">![散發) ](features/images/mrdevcenter/icon-distribute.png) [散發](/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="f45d3-284">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="f45d3-285">瞭解如何建立 HoloLens 和沉浸式耳機的混合現實體驗 (VR) 。</span><span class="sxs-lookup"><span data-stu-id="f45d3-285">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="f45d3-286">取得設計指南。</span><span class="sxs-lookup"><span data-stu-id="f45d3-286">Get design guides.</span></span> <span data-ttu-id="f45d3-287">建立使用者介面。</span><span class="sxs-lookup"><span data-stu-id="f45d3-287">Build user interface.</span></span> <span data-ttu-id="f45d3-288">瞭解互動和輸入。</span><span class="sxs-lookup"><span data-stu-id="f45d3-288">Learn interactions and input.</span></span>     | <span data-ttu-id="f45d3-289">取得開發指南。</span><span class="sxs-lookup"><span data-stu-id="f45d3-289">Get development guides.</span></span> <span data-ttu-id="f45d3-290">學習技術。</span><span class="sxs-lookup"><span data-stu-id="f45d3-290">Learn the technology.</span></span> <span data-ttu-id="f45d3-291">瞭解科學。</span><span class="sxs-lookup"><span data-stu-id="f45d3-291">Understand the science.</span></span>       | <span data-ttu-id="f45d3-292">準備好您的應用程式以供其他人使用，並考慮建立 3D 啟動器。</span><span class="sxs-lookup"><span data-stu-id="f45d3-292">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="f45d3-293">Azure 上的實用資源</span><span class="sxs-lookup"><span data-stu-id="f45d3-293">Useful resources on Azure</span></span>

| <span data-ttu-id="f45d3-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="f45d3-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="f45d3-295">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f45d3-295">Spatial Anchors</span></span>](/azure/spatial-anchors/)| <span data-ttu-id="f45d3-296">![語音服務](features/images/mrdevcenter/icon-azurespeechservices.png) [語音服務](/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="f45d3-296">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="f45d3-297">![視覺服務 ](features/images/mrdevcenter/icon-azurevisionservices.png) [視覺服務](/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="f45d3-297">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="f45d3-298">空間錨點是一種跨平臺服務，可讓您使用在一段時間內跨裝置保存其位置的物件，建立混合的現實體驗。</span><span class="sxs-lookup"><span data-stu-id="f45d3-298">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="f45d3-299">探索及整合 Azure 提供的語音功能，例如語音轉換文字、說話者辨識或語音翻譯至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f45d3-299">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="f45d3-300">使用視覺服務識別並分析您的影像或視訊內容，例如電腦視覺、臉部偵測、表情辨識或影片索引器。</span><span class="sxs-lookup"><span data-stu-id="f45d3-300">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="f45d3-301">如何參與</span><span class="sxs-lookup"><span data-stu-id="f45d3-301">How to contribute</span></span>

<span data-ttu-id="f45d3-302">瞭解您[如何參與 MRTK 的貢獻。](contributing/contributing.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-302">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="f45d3-303">取得說明</span><span class="sxs-lookup"><span data-stu-id="f45d3-303">Getting help</span></span>

<span data-ttu-id="f45d3-304">如果您遇到 MRTK 所造成的問題，或是有關于如何執行某些問題的問題，有一些資源可以提供協助：</span><span class="sxs-lookup"><span data-stu-id="f45d3-304">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="f45d3-305">針對錯誤報表，請在 GitHub 存放庫上提出 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) 。</span><span class="sxs-lookup"><span data-stu-id="f45d3-305">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="f45d3-306">如有任何問題，請在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 或「 [混合現實」工具組頻道](https://holodevelopers.slack.com/messages/C2H4HT858) 的時差上聯繫。</span><span class="sxs-lookup"><span data-stu-id="f45d3-306">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="f45d3-307">您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。</span><span class="sxs-lookup"><span data-stu-id="f45d3-307">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>