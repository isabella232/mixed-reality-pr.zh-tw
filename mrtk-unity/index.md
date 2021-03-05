---
title: MRTK-Unity 開發人員檔
description: 瞭解 Unity 的混合現實工具組。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK
ms.openlocfilehash: e763b603d7cbc1c0c07518126c26ad4efc8dbcc0
ms.sourcegitcommit: 5694cc472bde67c940204ebe6671b0598501e62a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2021
ms.locfileid: "102126651"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="aeebc-104">何謂混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="aeebc-104">What is the Mixed Reality Toolkit</span></span>

![混合實境工具組](features/images/Logo_MRTK_Unity_Banner.png)

<span data-ttu-id="aeebc-106">MRTK-Unity 是由 Microsoft 所推動的專案，其提供一組元件與功能，可用來加快 Unity 中的跨平台 MR 應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="aeebc-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="aeebc-107">以下是其中的一些功能：</span><span class="sxs-lookup"><span data-stu-id="aeebc-107">Here are some of its functions:</span></span>

* <span data-ttu-id="aeebc-108">提供 **空間互動和 UI 的跨平臺輸入系統和建立區塊**。</span><span class="sxs-lookup"><span data-stu-id="aeebc-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="aeebc-109">透過可讓您立即查看變更的編輯器內模擬，讓您能夠 **快速建立原型** 。</span><span class="sxs-lookup"><span data-stu-id="aeebc-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="aeebc-110">以可擴充的 **架構** 運作，讓開發人員能夠交換核心元件。</span><span class="sxs-lookup"><span data-stu-id="aeebc-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="aeebc-111">**支援多種平臺**，包括</span><span class="sxs-lookup"><span data-stu-id="aeebc-111">**Supports a wide range of platforms**, including</span></span>
  * <span data-ttu-id="aeebc-112">OpenXR (Unity 2020.2 或更新版本) </span><span class="sxs-lookup"><span data-stu-id="aeebc-112">OpenXR (Unity 2020.2 or newer)</span></span>
    * <span data-ttu-id="aeebc-113">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="aeebc-113">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="aeebc-114">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="aeebc-114">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="aeebc-115">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="aeebc-115">Windows Mixed Reality</span></span>
    * <span data-ttu-id="aeebc-116">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="aeebc-116">Microsoft HoloLens</span></span>
    * <span data-ttu-id="aeebc-117">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="aeebc-117">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="aeebc-118">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="aeebc-118">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="aeebc-119">Oculus (Unity 2019.3 或更新版本) </span><span class="sxs-lookup"><span data-stu-id="aeebc-119">Oculus (Unity 2019.3 or newer)</span></span>
    * <span data-ttu-id="aeebc-120">Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="aeebc-120">Oculus Quest</span></span>
  * <span data-ttu-id="aeebc-121">OpenVR</span><span class="sxs-lookup"><span data-stu-id="aeebc-121">OpenVR</span></span>
    * <span data-ttu-id="aeebc-122">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="aeebc-122">Windows Mixed Reality headsets</span></span>
    * <span data-ttu-id="aeebc-123">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="aeebc-123">HTC Vive</span></span>
    * <span data-ttu-id="aeebc-124">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="aeebc-124">Oculus Rift</span></span>
  * <span data-ttu-id="aeebc-125">Ultraleap 手部追蹤</span><span class="sxs-lookup"><span data-stu-id="aeebc-125">Ultraleap Hand Tracking</span></span>
  * <span data-ttu-id="aeebc-126">IOS 和 Android 等行動裝置</span><span class="sxs-lookup"><span data-stu-id="aeebc-126">Mobile devices such as iOS and Android</span></span>

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="aeebc-127">開始使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="aeebc-127">Getting started with MRTK</span></span>

<span data-ttu-id="aeebc-128">如果您不熟悉 Unity 中的 MRTK 或混合現實開發，建議您安裝必要的工具，然後遵循 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="aeebc-128">If you're new to MRTK or Mixed Reality development in Unity, we recommend you install the necessary tools and then follow the HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aeebc-129">安裝工具</span><span class="sxs-lookup"><span data-stu-id="aeebc-129">Install the Tools</span></span>](install-the-tools.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="aeebc-130">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="aeebc-130">HoloLens 2 Tutorial Series</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="aeebc-131">想要看看幕後的進展嗎？</span><span class="sxs-lookup"><span data-stu-id="aeebc-131">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="aeebc-132">探索 GitHub 上的 MRTK</span><span class="sxs-lookup"><span data-stu-id="aeebc-132">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="aeebc-133">文件</span><span class="sxs-lookup"><span data-stu-id="aeebc-133">Documentation</span></span>

| <span data-ttu-id="aeebc-134">[![版本資訊](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="aeebc-134">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="aeebc-135">版本資訊</span><span class="sxs-lookup"><span data-stu-id="aeebc-135">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="aeebc-136">[![MRTK 總覽](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="aeebc-136">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="aeebc-137">MRTK 總覽</span><span class="sxs-lookup"><span data-stu-id="aeebc-137">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="aeebc-138">[![API 參考](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="aeebc-138">[![API Reference](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="aeebc-139">API 參考</span><span class="sxs-lookup"><span data-stu-id="aeebc-139">API Reference</span></span>](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="aeebc-140">組建狀態</span><span class="sxs-lookup"><span data-stu-id="aeebc-140">Build status</span></span>

| <span data-ttu-id="aeebc-141">分支</span><span class="sxs-lookup"><span data-stu-id="aeebc-141">Branch</span></span> | <span data-ttu-id="aeebc-142">CI 狀態</span><span class="sxs-lookup"><span data-stu-id="aeebc-142">CI Status</span></span> | <span data-ttu-id="aeebc-143">檔狀態</span><span class="sxs-lookup"><span data-stu-id="aeebc-143">Docs Status</span></span> |
|---|---|---|
| `mrtk_development` |<span data-ttu-id="aeebc-144">[![CI 狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="aeebc-144">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="aeebc-145">[![檔狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="aeebc-145">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="aeebc-146">功能範圍</span><span class="sxs-lookup"><span data-stu-id="aeebc-146">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-147">[ ![ 輸入系統](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md) **[輸入系統](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-147">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md) **[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-148">[ ![ 手動追蹤 (hololens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md) **[手動追蹤 <br> (hololens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-148">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md) **[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-149">[ ![ 眼睛追蹤 (hololens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md) **[眼睛追蹤 <br/> (hololens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-149">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md) **[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-150">[ ![ 配置](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)檔 **[設定檔](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-150">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md) **[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-151">[ ![ 手動追蹤 (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md) **[手追蹤 <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-151">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md) **[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-152">[ ![ Ui 控制項](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks) **[ui 控制項](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-152">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks) **[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-153">[ ![ 解析器](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md) **[解析器](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-153">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md) **[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-154">[ ![ 多場景管理員](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md) **[多場景 <br/>](features/scene-system/scene-system-getting-started.md)管理員**</span><span class="sxs-lookup"><span data-stu-id="aeebc-154">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md) **[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-155">[ ![ 空間感知](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[空間 <br/> 感知](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-155">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-156">[ ![ 診斷工具](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md) **[診斷 <br/> 工具](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-156">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md) **[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-157">[ ![ MRTK 標準著色器視圖](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader) **[MRTK 標準著色器範例視圖](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-157">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader) **[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-158">[ ![ 語音 & 聽寫](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md) **[語音](features/input/speech.md) <br/>  &  [聽寫](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-158">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md) **[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-159">[ ![ 界限系統](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md) **[界限 <br/> 系統](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-159">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md) **[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-160">編輯器 [ ![ 內模擬](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)的 **[編輯器 <br/> 模擬](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-160">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md) **[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-161">[ ![ 實驗性功能](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md) **[實驗性 <br/> 功能](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-161">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md) **[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="aeebc-162">UX 組建區塊</span><span class="sxs-lookup"><span data-stu-id="aeebc-162">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-163">[ ![ 按鈕](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[按鈕](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-163">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="aeebc-164">支援各種輸入方法的按鈕控制項，包括 HoloLens 2 的明確表述</span><span class="sxs-lookup"><span data-stu-id="aeebc-164">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-165">[ ![ 界限控制項](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[界限控制項](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-165">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="aeebc-166">在3D 空間中操作物件的標準 UI</span><span class="sxs-lookup"><span data-stu-id="aeebc-166">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-167">[ ![ 物件](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md)操作工具 **[物件](features/ux-building-blocks/object-manipulator.md)操作工具**</span><span class="sxs-lookup"><span data-stu-id="aeebc-167">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="aeebc-168">以一或兩個手中操作物件的腳本</span><span class="sxs-lookup"><span data-stu-id="aeebc-168">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-169">[ ![ 平板](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[平板](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-169">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="aeebc-170">2D 樣式平面，支援以已明確表達的手寫輸入進行滾動</span><span class="sxs-lookup"><span data-stu-id="aeebc-170">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-171">[ ![ 系統鍵盤](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[系統鍵盤](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-171">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="aeebc-172">在 Unity 中使用系統鍵盤的範例腳本</span><span class="sxs-lookup"><span data-stu-id="aeebc-172">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-173">[ ![ 互動](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[互動](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-173">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="aeebc-174">使用視覺狀態和主題支援讓物件互動的腳本</span><span class="sxs-lookup"><span data-stu-id="aeebc-174">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-175">[ ![ 規劃](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md)求解 **[規劃](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-175">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="aeebc-176">各種物件定位行為，例如標記-沿著標記、主體鎖定、常數視圖大小和表面磁性</span><span class="sxs-lookup"><span data-stu-id="aeebc-176">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-177">[ ![ 物件集合](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[物件集合](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-177">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="aeebc-178">在三維圖形中設定物件陣列的腳本</span><span class="sxs-lookup"><span data-stu-id="aeebc-178">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-179">[ ![ 工具](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md)提示 **[工具提示](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-179">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="aeebc-180">具有彈性錨點/pivot 系統的注釋 UI，可用來標記動作控制器和物件</span><span class="sxs-lookup"><span data-stu-id="aeebc-180">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-181">[ ![ 滑杆](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[滑杆](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-181">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="aeebc-182">調整支援直接追蹤互動之值的滑杆 UI</span><span class="sxs-lookup"><span data-stu-id="aeebc-182">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-183">[ ![ MRTK 標準著色器](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK 標準著色器](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-183">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="aeebc-184">MRTK 的標準著色器可支援各種流暢的設計項目與效能</span><span class="sxs-lookup"><span data-stu-id="aeebc-184">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-185">[ ![ 手形功能表](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[](features/ux-building-blocks/hand-menu.md)功能表**</span><span class="sxs-lookup"><span data-stu-id="aeebc-185">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="aeebc-186">使用手形條件約束規劃的手動鎖定 UI，以進行快速存取</span><span class="sxs-lookup"><span data-stu-id="aeebc-186">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-187">[ ![ 應用程式行](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[應用程式行](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-187">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="aeebc-188">界限控制項手動啟用的 UI</span><span class="sxs-lookup"><span data-stu-id="aeebc-188">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-189">[ ![ 指標](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[指標](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-189">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="aeebc-190">瞭解各種類型的指標</span><span class="sxs-lookup"><span data-stu-id="aeebc-190">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-191">[ ![ Fingertip 視覺效果](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip 視覺效果](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-191">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="aeebc-192">Fingertip 上的視覺效果 affordance，可改善直接互動的信賴度</span><span class="sxs-lookup"><span data-stu-id="aeebc-192">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-193">靠近功能表的 [ ![ 附近功能表](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-193">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="aeebc-194">接近互動的浮動功能表 UI</span><span class="sxs-lookup"><span data-stu-id="aeebc-194">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-195">[ ![ 空間感知入門入門](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[空間感知視圖](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-195">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="aeebc-196">讓您的全像攝影物件與實體環境互動</span><span class="sxs-lookup"><span data-stu-id="aeebc-196">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-197">[ ![ Voice 命令](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[voice 命令](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-197">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="aeebc-198">整合語音輸入的腳本和範例</span><span class="sxs-lookup"><span data-stu-id="aeebc-198">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-199">[ ![ 進度指示器](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[進度指標](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-199">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="aeebc-200">用於傳達資料處理或作業的視覺化指標</span><span class="sxs-lookup"><span data-stu-id="aeebc-200">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-201">[ ![ 對話方塊](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[對話方塊](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-201">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="aeebc-202">要求使用者確認或確認的 UI</span><span class="sxs-lookup"><span data-stu-id="aeebc-202">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-203">[ ![ 手動指導](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-203">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="aeebc-204">當手勢未教授時，可協助引導使用者的元件</span><span class="sxs-lookup"><span data-stu-id="aeebc-204">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-205">[ ![ 手物理服務](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md)的 **[物理服務 [實驗]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-205">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="aeebc-206">實際的物理服務可讓您透過明確的方式進行固定的內文衝突事件和互動</span><span class="sxs-lookup"><span data-stu-id="aeebc-206">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-207">[ ![ 滾動集合](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[滾動集合](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-207">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="aeebc-208">原生滾動3D 物件的物件集合</span><span class="sxs-lookup"><span data-stu-id="aeebc-208">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-209">[ ![](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md)停駐 **[固定 [實驗]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-209">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="aeebc-210">Dock 允許將物件移入和移出預定的位置</span><span class="sxs-lookup"><span data-stu-id="aeebc-210">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="aeebc-211">[ ![ 眼睛追蹤：目標選擇](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[眼睛追蹤：目標選取範圍](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-211">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="aeebc-212">結合眼睛、語音和手輸入，以快速且輕鬆地在場景中選取全像影像</span><span class="sxs-lookup"><span data-stu-id="aeebc-212">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-213">[ ![ 眼睛追蹤：導覽](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[眼睛追蹤：導覽](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-213">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="aeebc-214">瞭解如何根據您要查看的內容，自動滾動文字或流暢縮放至焦點內容</span><span class="sxs-lookup"><span data-stu-id="aeebc-214">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="aeebc-215">[ ![ 眼睛追蹤：熱度圖](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[視覺追蹤：熱度圖](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="aeebc-215">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="aeebc-216">記錄、載入和視覺化使用者在您的應用程式中查看的範例</span><span class="sxs-lookup"><span data-stu-id="aeebc-216">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="aeebc-217">工具</span><span class="sxs-lookup"><span data-stu-id="aeebc-217">Tools</span></span>

|  <span data-ttu-id="aeebc-218">[ ![ 優化視窗](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md)[優化視窗](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="aeebc-218">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="aeebc-219">相依性[ ![ 視窗](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md)相依性[視窗](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="aeebc-219">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![組建視窗](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="aeebc-221">組建視窗</span><span class="sxs-lookup"><span data-stu-id="aeebc-221">Build Window</span></span> | <span data-ttu-id="aeebc-222">[ ![ 輸入錄製](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md)[輸入記錄](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="aeebc-222">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="aeebc-223">自動設定混合現實專案以進行效能優化</span><span class="sxs-lookup"><span data-stu-id="aeebc-223">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="aeebc-224">分析資產之間的相依性，並找出未使用的資產</span><span class="sxs-lookup"><span data-stu-id="aeebc-224">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="aeebc-225">設定及執行混合現實應用程式的端對端組建程式</span><span class="sxs-lookup"><span data-stu-id="aeebc-225">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="aeebc-226">在編輯器中錄製並播放前端移動和手動追蹤資料</span><span class="sxs-lookup"><span data-stu-id="aeebc-226">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="aeebc-227">範例場景</span><span class="sxs-lookup"><span data-stu-id="aeebc-227">Example scenes</span></span>

<span data-ttu-id="aeebc-228">探索 MRTK 在 [此範例場景](features/example-scenes/hand-interaction-examples.md)中的各種互動和 UI 控制項類型。</span><span class="sxs-lookup"><span data-stu-id="aeebc-228">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="aeebc-229">[![範例場景2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="aeebc-229">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="aeebc-230">MRTK 範例中樞</span><span class="sxs-lookup"><span data-stu-id="aeebc-230">MRTK examples hub</span></span>

<span data-ttu-id="aeebc-231">您可以使用 MRTK 範例中樞來嘗試 MRTK 中的各種範例場景。</span><span class="sxs-lookup"><span data-stu-id="aeebc-231">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="aeebc-232">您可以藉由選取 [MR 功能工具](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)中的「混合現實工具組範例」套件，下載預先建立的 HoloLens 應用程式套件， (x86) 、HoloLens 2 (ARM) 和 Windows Mixed reality 沉浸式耳機 (x64) 。</span><span class="sxs-lookup"><span data-stu-id="aeebc-232">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="aeebc-233">請務必 [使用 Windows 裝置入口網站，在 HoloLens (第1代) 上安裝應用程式 ](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)。</span><span class="sxs-lookup"><span data-stu-id="aeebc-233">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="aeebc-234">在 HoloLens 2 上，您可以 [透過 Microsoft Store 應用程式下載並安裝 MRTK 範例中樞](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)。</span><span class="sxs-lookup"><span data-stu-id="aeebc-234">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="aeebc-235">請參閱 [範例中樞的讀我檔案頁面](features/example-scenes/example-hub.md) ，以瞭解如何使用 MRTK 的場景系統和場景轉換服務建立多場景中樞的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="aeebc-235">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="aeebc-236">[![範例場景中樞](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="aeebc-236">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="aeebc-237">使用 MRTK 建立的範例應用程式</span><span class="sxs-lookup"><span data-stu-id="aeebc-237">Sample apps made with MRTK</span></span>

| <span data-ttu-id="aeebc-238">[![元素週期表](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="aeebc-238">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="aeebc-239">[![Galaxy Explorer 1](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="aeebc-239">[![Galaxy Explorer 1](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="aeebc-240">[![Galaxy Explorer 2](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="aeebc-240">[![Galaxy Explorer 2](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="aeebc-241">專案的[定期資料表](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)是開放原始碼範例應用程式，示範如何使用 MRTK 的輸入系統和建立區塊來建立 HoloLens 和沉浸式耳機的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="aeebc-241">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="aeebc-242">閱讀移植案例： [使用 MRTK v2 將專案應用程式的定期資料表帶入 HoloLens 2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="aeebc-242">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="aeebc-243">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) 是一種開放原始碼範例應用程式，最初是在2016年3月的「分享您的想法」活動中所開發。</span><span class="sxs-lookup"><span data-stu-id="aeebc-243">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="aeebc-244">已使用 MRTK v2 以 HoloLens 2 的新功能更新 Galaxy Explorer。</span><span class="sxs-lookup"><span data-stu-id="aeebc-244">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="aeebc-245">閱讀案例： [適用于 HoloLens 2 的 Galaxy Explorer 製作](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="aeebc-245">Read the story: [The Making of Galaxy Explorer for HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="aeebc-246">[表面](https://github.com/Microsoft/GalaxyExplorer) 是適用于 HoloLens 2 的開放原始碼範例應用程式，它會探索如何使用視覺效果、音訊和完全明確的手動追蹤來建立 tactile 刺痛。</span><span class="sxs-lookup"><span data-stu-id="aeebc-246">[Surfaces](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="aeebc-247">查看 Microsoft MR Dev Days session [學習 from surface 應用程式](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) ，以取得詳細的設計和開發案例。</span><span class="sxs-lookup"><span data-stu-id="aeebc-247">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="aeebc-248">來自混合現實開發日2020的研討會影片</span><span class="sxs-lookup"><span data-stu-id="aeebc-248">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="aeebc-249">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="aeebc-249">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="aeebc-250">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="aeebc-250">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="aeebc-251">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="aeebc-251">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="aeebc-252">如何建立從開始到完成的簡單 MRTK 應用程式的教學課程。</span><span class="sxs-lookup"><span data-stu-id="aeebc-252">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="aeebc-253">瞭解互動概念和 MRTK 的多平臺功能。</span><span class="sxs-lookup"><span data-stu-id="aeebc-253">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="aeebc-254">深入探討 MRTK 的 UX 構成要素，協助您打造美觀的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="aeebc-254">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="aeebc-255">MRTK 和外部的效能工具簡介，以及 MRTK 標準著色器的總覽。</span><span class="sxs-lookup"><span data-stu-id="aeebc-255">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="aeebc-256">若要探索更多課程影片，請參閱 [混合現實開發日](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) 。</span><span class="sxs-lookup"><span data-stu-id="aeebc-256">See [Mixed Reality Dev Days](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="aeebc-257">與社區互動</span><span class="sxs-lookup"><span data-stu-id="aeebc-257">Engage with the community</span></span>

* <span data-ttu-id="aeebc-258">在 MRTK 上加入關於 [時差](https://holodevelopers.slack.com/)的交談。</span><span class="sxs-lookup"><span data-stu-id="aeebc-258">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="aeebc-259">您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。</span><span class="sxs-lookup"><span data-stu-id="aeebc-259">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="aeebc-260">使用 **MRTK** 標記詢問有關使用 MRTK On [Stack 溢](https://stackoverflow.com/questions/tagged/mrtk)位的問題。</span><span class="sxs-lookup"><span data-stu-id="aeebc-260">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="aeebc-261">如果您發現 MRTK 程式碼中有問題，請搜尋 [已知問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 或提出 [新問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 。</span><span class="sxs-lookup"><span data-stu-id="aeebc-261">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="aeebc-262">如有關于參與 MRTK 的問題，請移至「 [混合現實」工具](https://holodevelopers.slack.com/messages/C2H4HT858) 組頻道的時差。</span><span class="sxs-lookup"><span data-stu-id="aeebc-262">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="aeebc-263">此專案採用了 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="aeebc-263">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="aeebc-264">如需詳細資訊，請參閱[管理辦法常見問題集](https://opensource.microsoft.com/codeofconduct/faq/)，如有其他問題或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="aeebc-264">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="aeebc-265">混合現實開發人員中心上的實用資源</span><span class="sxs-lookup"><span data-stu-id="aeebc-265">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="aeebc-266">![探索 ](features/images/mrdevcenter/icon-discover.png) [探索](https://docs.microsoft.com/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="aeebc-266">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](https://docs.microsoft.com/windows/mixed-reality/)</span></span>| <span data-ttu-id="aeebc-267">![設計 ](features/images/mrdevcenter/icon-design.png) [設計](https://docs.microsoft.com/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="aeebc-267">![Design](features/images/mrdevcenter/icon-design.png) [Design](https://docs.microsoft.com/windows/mixed-reality/design)</span></span>| <span data-ttu-id="aeebc-268">![開發 ](features/images/mrdevcenter/icon-develop.png) [開發](https://docs.microsoft.com/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="aeebc-268">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](https://docs.microsoft.com/windows/mixed-reality/development)</span></span>| <span data-ttu-id="aeebc-269">![散發) ](features/images/mrdevcenter/icon-distribute.png) [散發](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="aeebc-269">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="aeebc-270">瞭解如何建立 HoloLens 和沉浸式耳機的混合現實體驗 (VR) 。</span><span class="sxs-lookup"><span data-stu-id="aeebc-270">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="aeebc-271">取得設計指南。</span><span class="sxs-lookup"><span data-stu-id="aeebc-271">Get design guides.</span></span> <span data-ttu-id="aeebc-272">建立使用者介面。</span><span class="sxs-lookup"><span data-stu-id="aeebc-272">Build user interface.</span></span> <span data-ttu-id="aeebc-273">瞭解互動和輸入。</span><span class="sxs-lookup"><span data-stu-id="aeebc-273">Learn interactions and input.</span></span>     | <span data-ttu-id="aeebc-274">取得開發指南。</span><span class="sxs-lookup"><span data-stu-id="aeebc-274">Get development guides.</span></span> <span data-ttu-id="aeebc-275">學習技術。</span><span class="sxs-lookup"><span data-stu-id="aeebc-275">Learn the technology.</span></span> <span data-ttu-id="aeebc-276">瞭解科學。</span><span class="sxs-lookup"><span data-stu-id="aeebc-276">Understand the science.</span></span>       | <span data-ttu-id="aeebc-277">準備好您的應用程式以供其他人使用，並考慮建立 3D 啟動器。</span><span class="sxs-lookup"><span data-stu-id="aeebc-277">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="aeebc-278">Azure 上的實用資源</span><span class="sxs-lookup"><span data-stu-id="aeebc-278">Useful resources on Azure</span></span>

| <span data-ttu-id="aeebc-279">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="aeebc-279">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="aeebc-280">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="aeebc-280">Spatial Anchors</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)| <span data-ttu-id="aeebc-281">![語音服務](features/images/mrdevcenter/icon-azurespeechservices.png) [語音服務](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="aeebc-281">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="aeebc-282">![視覺服務 ](features/images/mrdevcenter/icon-azurevisionservices.png) [視覺服務](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="aeebc-282">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="aeebc-283">空間錨點是一種跨平臺服務，可讓您使用在一段時間內跨裝置保存其位置的物件，建立混合的現實體驗。</span><span class="sxs-lookup"><span data-stu-id="aeebc-283">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="aeebc-284">探索及整合 Azure 提供的語音功能，例如語音轉換文字、說話者辨識或語音翻譯至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="aeebc-284">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="aeebc-285">使用視覺服務識別並分析您的影像或視訊內容，例如電腦視覺、臉部偵測、表情辨識或影片索引器。</span><span class="sxs-lookup"><span data-stu-id="aeebc-285">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="aeebc-286">如何參與</span><span class="sxs-lookup"><span data-stu-id="aeebc-286">How to contribute</span></span>

<span data-ttu-id="aeebc-287">瞭解您[如何參與 MRTK 的貢獻。](contributing/contributing.md)</span><span class="sxs-lookup"><span data-stu-id="aeebc-287">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="aeebc-288">取得說明</span><span class="sxs-lookup"><span data-stu-id="aeebc-288">Getting help</span></span>

<span data-ttu-id="aeebc-289">如果您遇到 MRTK 所造成的問題，或是有關于如何執行某些問題的問題，有一些資源可以提供協助：</span><span class="sxs-lookup"><span data-stu-id="aeebc-289">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="aeebc-290">針對錯誤報表，請在 GitHub 存放庫上提出 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) 。</span><span class="sxs-lookup"><span data-stu-id="aeebc-290">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="aeebc-291">如有任何問題，請在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 或「 [混合現實」工具組頻道](https://holodevelopers.slack.com/messages/C2H4HT858) 的時差上聯繫。</span><span class="sxs-lookup"><span data-stu-id="aeebc-291">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="aeebc-292">您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。</span><span class="sxs-lookup"><span data-stu-id="aeebc-292">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>
