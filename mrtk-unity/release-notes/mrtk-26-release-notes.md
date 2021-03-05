---
title: MRTK 2.6 版本資訊
description: MRTK 2.6 版的版本資訊
author: polar-kev
ms.author: kesemple
ms.date: 02/28/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 41d7b2fd1f1991608a2e89b4c0d3f561fdb01660
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230729"
---
# <a name="microsoft-mixed-reality-toolkit-260-release-notes"></a><span data-ttu-id="c350a-104">Microsoft Mixed Reality 工具組2.6.0 版本資訊</span><span class="sxs-lookup"><span data-stu-id="c350a-104">Microsoft Mixed Reality Toolkit 2.6.0 Release Notes</span></span>

- [<span data-ttu-id="c350a-105">新功能</span><span class="sxs-lookup"><span data-stu-id="c350a-105">What's new</span></span>](#whats-new)
- [<span data-ttu-id="c350a-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="c350a-106">Breaking changes</span></span>](#breaking-changes)
- [<span data-ttu-id="c350a-107">更新指導方針</span><span class="sxs-lookup"><span data-stu-id="c350a-107">Updating guidance</span></span>](../updates-deployment/updating.md#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="c350a-108">已知問題</span><span class="sxs-lookup"><span data-stu-id="c350a-108">Known issues</span></span>](#known-issues)

> [!IMPORTANT]
> <span data-ttu-id="c350a-109">有一個已知的編譯器問題，會影響使用 ARM64 針對 Microsoft HoloLens 2 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c350a-109">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="c350a-110">將 Visual Studio 2019 更新至16.8 版或更新版本，即可修正此問題。</span><span class="sxs-lookup"><span data-stu-id="c350a-110">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="c350a-111">如果您無法更新 Visual Studio，請匯入套件以套用因應措施 `com.microsoft.mixedreality.toolkit.tools` 。</span><span class="sxs-lookup"><span data-stu-id="c350a-111">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new"></a><span data-ttu-id="c350a-112">最新消息</span><span class="sxs-lookup"><span data-stu-id="c350a-112">What's new</span></span>

### <a name="add-support-for-openxr"></a><span data-ttu-id="c350a-113">新增對 OpenXR 的支援</span><span class="sxs-lookup"><span data-stu-id="c350a-113">Add support for OpenXR</span></span>

<span data-ttu-id="c350a-114">已新增 Unity OpenXR preview 套件和 Microsoft Mixed Reality OpenXR 封裝的初始支援。</span><span class="sxs-lookup"><span data-stu-id="c350a-114">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="c350a-115">如需詳細資訊，請參閱 [MRTK/XRSDK 開始使用頁面](../configuration/getting-started-with-mrtk-and-xrsdk.md)、 [Unity 的論壇文章](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)或 [Microsoft 的檔](https://aka.ms/openxr-unity-install) 。</span><span class="sxs-lookup"><span data-stu-id="c350a-115">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](https://aka.ms/openxr-unity-install) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c350a-116">Unity 中的 OpenXR 僅支援 Unity 2020.2 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="c350a-116">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="c350a-117">目前它也只支援 x64 和 ARM64 組建。</span><span class="sxs-lookup"><span data-stu-id="c350a-117">Currently, it also only supports x64 and ARM64 builds.</span></span>

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a><span data-ttu-id="c350a-118">MRTK 現在支援 HP 動作控制器</span><span class="sxs-lookup"><span data-stu-id="c350a-118">HP Motion Controllers now supported with MRTK</span></span>

<span data-ttu-id="c350a-119">HP 殘響 G2 的控制器現在可在 MRTK 中以原生方式運作。</span><span class="sxs-lookup"><span data-stu-id="c350a-119">Controllers for the HP Reverb G2 now work natively with MRTK.</span></span>

### <a name="experimental-interactive-element--state-visualizer"></a><span data-ttu-id="c350a-120">實驗性互動式元素 + 狀態視覺化</span><span class="sxs-lookup"><span data-stu-id="c350a-120">Experimental Interactive Element + State Visualizer</span></span> 

<span data-ttu-id="c350a-121">互動式元素是 MRTK 輸入系統的簡化集中進入點。</span><span class="sxs-lookup"><span data-stu-id="c350a-121">Interactive Element is a simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="c350a-122">它包含狀態管理方法、事件管理，以及核心互動狀態的狀態設定邏輯。</span><span class="sxs-lookup"><span data-stu-id="c350a-122">It contains state management methods, event management and the state setting logic for Core Interaction States.</span></span> <span data-ttu-id="c350a-123">如需詳細資訊，請參閱 [互動式元素檔](../features/experimental/interactive-element.md)集。</span><span class="sxs-lookup"><span data-stu-id="c350a-123">For more information see [Interactive Element Documentation](../features/experimental/interactive-element.md).</span></span>

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

<span data-ttu-id="c350a-125">狀態視覺化是相依于互動式元素的動畫元件。</span><span class="sxs-lookup"><span data-stu-id="c350a-125">The State Visualizer is an animation component that depends on Interactive Element.</span></span>  <span data-ttu-id="c350a-126">此元件會建立動畫剪輯、設定主要畫面格，並產生 Animator 狀態機器。</span><span class="sxs-lookup"><span data-stu-id="c350a-126">This component creates Animation Clips, sets keyframes and generates an Animator State Machine.</span></span> <span data-ttu-id="c350a-127">如需詳細資訊，請參閱 [狀態視覺化檔](../features/experimental/interactive-element.md#state-visualizer-experimental)</span><span class="sxs-lookup"><span data-stu-id="c350a-127">For more information see [State Visualizer Documentation](../features/experimental/interactive-element.md#state-visualizer-experimental)</span></span>

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a><span data-ttu-id="c350a-129">所有平臺現在都支援使用「傳送」手勢進行遙傳</span><span class="sxs-lookup"><span data-stu-id="c350a-129">Teleportation with the teleport gesture now supported on all platforms</span></span>

<span data-ttu-id="c350a-130">使用者現在可以使用「傳送」手勢，在所有平臺上四處移動其播放空間。</span><span class="sxs-lookup"><span data-stu-id="c350a-130">Users can now use the teleport gesture to move around their play space across all platforms.</span></span> <span data-ttu-id="c350a-131">若要使用預設設定在 MR 裝置上傳送控制器，請使用操縱杆。</span><span class="sxs-lookup"><span data-stu-id="c350a-131">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="c350a-132">若要透過明確的手進行傳送，請與您的手朝外手勢，並將索引和捲動方塊朝外，以 curling 食指來完成傳送。</span><span class="sxs-lookup"><span data-stu-id="c350a-132">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="c350a-133">若要使用輸入模擬來傳送，請參閱更新的 [輸入模擬服務檔](../features/input-simulation/input-simulation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="c350a-133">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../features/input-simulation/input-simulation-service.md).</span></span>

  ![傳送手勢](images/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a><span data-ttu-id="c350a-135">場景理解現在可在 MRTK 中作為實驗空間感知觀察者</span><span class="sxs-lookup"><span data-stu-id="c350a-135">Scene Understanding now available in MRTK as an experimental spatial awareness observer</span></span>

<span data-ttu-id="c350a-136">[場景理解](https://docs.microsoft.com/windows/mixed-reality/scene-understanding)的實驗性支援是在 MRTK 2.6 中引進。</span><span class="sxs-lookup"><span data-stu-id="c350a-136">Experimental support of [Scene Understanding](https://docs.microsoft.com/windows/mixed-reality/scene-understanding) is introduced in MRTK 2.6.</span></span> <span data-ttu-id="c350a-137">使用者可以在以 MRTK 為基礎的專案中，將 HoloLens 2 的場景理解功能納入為空間感知觀察者。</span><span class="sxs-lookup"><span data-stu-id="c350a-137">Users can incorporate the scene understanding capabilities of HoloLens 2 as a spatial awareness observer in MRTK based projects.</span></span> <span data-ttu-id="c350a-138">如需詳細資訊，請參閱 [場景理解檔](../features/spatial-awareness/scene-understanding.md) 。</span><span class="sxs-lookup"><span data-stu-id="c350a-138">Please read the [Scene Understanding documentation](../features/spatial-awareness/scene-understanding.md) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c350a-139">只有 HoloLens 2 和 Unity 2019.4 和更新版本才支援場景理解。</span><span class="sxs-lookup"><span data-stu-id="c350a-139">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>
>
> <span data-ttu-id="c350a-140">這項功能需要場景理解套件，現在可透過「 [混合現實」功能工具](https://aka.ms/MRFeatureTool)取得。</span><span class="sxs-lookup"><span data-stu-id="c350a-140">This feature requires the Scene Understanding package, which is now available via the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

  ![場景理解](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a><span data-ttu-id="c350a-142">執行時間設定檔切換支援</span><span class="sxs-lookup"><span data-stu-id="c350a-142">Runtime profile switching support</span></span>

<span data-ttu-id="c350a-143">MRTK 現在可讓您在初始化 MRTK (實例之前切換設定檔（亦即，預先 MRTK 初始化設定檔切換) ，以及在設定檔已在使用中時使用 (也就是使用中設定檔參數) 。</span><span class="sxs-lookup"><span data-stu-id="c350a-143">MRTK now allows profile switching both before the initialization of the MRTK instance (i.e. Pre MRTK initialization profile switch) and after a profile has been in active use (i.e. Active profile switch).</span></span> <span data-ttu-id="c350a-144">先前的參數可用來根據硬體的功能來啟用選取元件，而後者可以用來在使用者輸入應用程式子元件時修改體驗。</span><span class="sxs-lookup"><span data-stu-id="c350a-144">The former switch can be used to enable select components based on capabilities of the hardware, while the latter can be used to modify experience as the user enters a subpart of the application.</span></span> <span data-ttu-id="c350a-145">如需詳細資訊和程式碼範例，請閱讀 [設定檔切換的相關](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) 檔。</span><span class="sxs-lookup"><span data-stu-id="c350a-145">Please read the [documentation on profile switching](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) for more information and code samples.</span></span>

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a><span data-ttu-id="c350a-146">方向指標，並遵循實驗的解析器</span><span class="sxs-lookup"><span data-stu-id="c350a-146">Directional Indicator and Follow Solvers Graduated from Experimental</span></span>

<span data-ttu-id="c350a-147">有兩個新的解析器可供搭配主線 MRTK 使用。</span><span class="sxs-lookup"><span data-stu-id="c350a-147">Two new solvers are ready for use with mainline MRTK.</span></span>

  ![方向性指標規劃求解](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a><span data-ttu-id="c350a-149">從實驗性開始的手勢</span><span class="sxs-lookup"><span data-stu-id="c350a-149">Hand Coach Graduated from Experimental</span></span>

<span data-ttu-id="c350a-150">這項功能現在已準備好搭配主線 MRTK 使用。</span><span class="sxs-lookup"><span data-stu-id="c350a-150">The Hand Coach feature is now ready for use with mainline MRTK.</span></span>
  <span data-ttu-id="c350a-151">![手動指導範例](https://docs.microsoft.com/windows/mixed-reality/design/images/handcoach/airtap.gif)</span><span class="sxs-lookup"><span data-stu-id="c350a-151">![Hand Coach Example](https://docs.microsoft.com/windows/mixed-reality/design/images/handcoach/airtap.gif)</span></span>

### <a name="pulse-shader-graduated-from-experimental"></a><span data-ttu-id="c350a-152">從實驗性分級的脈衝著色器</span><span class="sxs-lookup"><span data-stu-id="c350a-152">Pulse Shader Graduated from Experimental</span></span> 

<span data-ttu-id="c350a-153">脈衝著色器腳本已從實驗性進行分級。</span><span class="sxs-lookup"><span data-stu-id="c350a-153">The Pulse Shader scripts have graduated from experimental.</span></span> <span data-ttu-id="c350a-154">如需詳細資訊，請參閱： [脈衝著色器檔](../features/rendering/pulse-shader.md)</span><span class="sxs-lookup"><span data-stu-id="c350a-154">For more information see: [Pulse Shader Documentation](../features/rendering/pulse-shader.md)</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)


### <a name="input-recording-service-improvements"></a><span data-ttu-id="c350a-156">輸入記錄服務改進</span><span class="sxs-lookup"><span data-stu-id="c350a-156">Input Recording Service improvements</span></span>

<span data-ttu-id="c350a-157">`InputRecordingService` 而且 `InputPlaybackService` 現在可以錄製並播放眼睛的眼睛輸入。</span><span class="sxs-lookup"><span data-stu-id="c350a-157">`InputRecordingService` and `InputPlaybackService` can now record and play back eye gaze input.</span></span> <span data-ttu-id="c350a-158">錄製已經過優化，可確保整段記錄期間的資料幀大小都一致，而記錄檔大小和節省時間也會降低大約50%。</span><span class="sxs-lookup"><span data-stu-id="c350a-158">Recording has been optimized to ensure a consistent framerate throughout the recording period while recording file size and save time are also reduced by about 50%.</span></span> <span data-ttu-id="c350a-159">現在可以非同步方式執行錄製檔案的儲存和載入作業。</span><span class="sxs-lookup"><span data-stu-id="c350a-159">Saving and loading of recording files can now be performed asynchronously.</span></span> <span data-ttu-id="c350a-160">請注意此 MRTK 版本中記錄的檔案格式已經變更，請參閱 [這裡](../features/input-simulation/input-animation-file-format.md) 以取得新版本1.1 規格的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c350a-160">Note the file format of the recording has changed in this MRTK version, please see [here](../features/input-simulation/input-animation-file-format.md) for more information on the new version 1.1 specifications.</span></span>

### <a name="reading-mode"></a><span data-ttu-id="c350a-161">讀取模式</span><span class="sxs-lookup"><span data-stu-id="c350a-161">Reading mode</span></span>

<span data-ttu-id="c350a-162">已新增在 HoloLens 2 上 [讀取模式](https://docs.microsoft.com/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) 的支援。</span><span class="sxs-lookup"><span data-stu-id="c350a-162">Added support for [reading mode](https://docs.microsoft.com/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) on HoloLens 2.</span></span> <span data-ttu-id="c350a-163">[讀取] 模式可減少系統的顯示欄位，但會排除 Unity 輸出的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="c350a-163">Reading mode reduces the system's field of view but eliminates a scaling of Unity's output.</span></span> <span data-ttu-id="c350a-164">Unity 轉譯的圖元會對應到 HoloLens 2 上投射的圖元。</span><span class="sxs-lookup"><span data-stu-id="c350a-164">A pixel rendered by Unity will correspond to a projected pixel on HoloLens 2.</span></span> <span data-ttu-id="c350a-165">應用程式作者應該使用多個個人進行測試，以確保這是他們在應用程式中所需的取捨。</span><span class="sxs-lookup"><span data-stu-id="c350a-165">Application authors should do tests with multiple individuals to be sure this is a tradeoff they want in their app.</span></span>

  ![Windows Mixed Reality 閱讀模式](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a><span data-ttu-id="c350a-167">在 UWP 上支援3D 應用程式啟動器</span><span class="sxs-lookup"><span data-stu-id="c350a-167">Support for 3D app launchers on UWP</span></span>

<span data-ttu-id="c350a-168">新增為 UWP 設定 [3d 應用程式啟動器](https://docs.microsoft.com/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 的功能。</span><span class="sxs-lookup"><span data-stu-id="c350a-168">Adds the ability to set a [3D app launcher](https://docs.microsoft.com/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for UWP.</span></span> <span data-ttu-id="c350a-169">這項設定會在 [MRTK 組建] 視窗和 [MRTK] 專案設定的 [組建設定] 底下公開。</span><span class="sxs-lookup"><span data-stu-id="c350a-169">This setting is exposed both in the MRTK Build Window and the MRTK Project Settings, under Build Settings.</span></span> <span data-ttu-id="c350a-170">它會在 Unity 中的組建期間自動寫入至專案。</span><span class="sxs-lookup"><span data-stu-id="c350a-170">It's automatically written into the project during the build in Unity.</span></span>

  ![組建設定](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a><span data-ttu-id="c350a-172">重大變更</span><span class="sxs-lookup"><span data-stu-id="c350a-172">Breaking changes</span></span>

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a><span data-ttu-id="c350a-173">匯入之 GLTF 物件的某些欄位現在已大寫</span><span class="sxs-lookup"><span data-stu-id="c350a-173">Certain fields of imported GLTF objects are now capitalized</span></span>

<span data-ttu-id="c350a-174">由於還原序列化相關的問題，已匯入 GLTF 物件的某些欄位現在以大寫字母開頭。</span><span class="sxs-lookup"><span data-stu-id="c350a-174">Due to deserialization related issues some fields of imported GLTF objects are now starting with capital letters.</span></span> <span data-ttu-id="c350a-175">受影響的欄位會以新名稱 () ： `ComponentType` 、 `Path` 、 `Interpolation` 、、、、、、 `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` 、 `WrapT` 。</span><span class="sxs-lookup"><span data-stu-id="c350a-175">The affected fields are (in their new names): `ComponentType`, `Path`, `Interpolation`, `Target`, `Type`, `Mode`, `MagFilter`, `MinFilter`, `WrapS`, `WrapT`.</span></span>

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a><span data-ttu-id="c350a-176">輸入動畫二進位檔案具有更新版本1.1 格式</span><span class="sxs-lookup"><span data-stu-id="c350a-176">Input animation binary file has an updated version 1.1 format</span></span>

<span data-ttu-id="c350a-177">輸入動畫二進位檔（由 `InputRecordingService` 和使用 `InputPlaybackService` ）現在具有更新的檔案格式，可讓您對這兩個服務進行優化。</span><span class="sxs-lookup"><span data-stu-id="c350a-177">Input animation binary file, used by `InputRecordingService` and `InputPlaybackService`, now has an updated file format to enable the optimizations made to those two services.</span></span> <span data-ttu-id="c350a-178">如需新版本1.1 規格的詳細資訊，請參閱 [這裡](../features/input-simulation/input-animation-file-format.md) 。</span><span class="sxs-lookup"><span data-stu-id="c350a-178">Please see [here](../features/input-simulation/input-animation-file-format.md) for more information on the new version 1.1 specifications.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="c350a-179">適用于 Unity 的 MSBuild 支援</span><span class="sxs-lookup"><span data-stu-id="c350a-179">MSBuild for Unity support</span></span>

<span data-ttu-id="c350a-180">從2.5.2 版本開始，已移除對 MSBuild for Unity 的支援，以配合 [Unity 的新套件指引](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)。</span><span class="sxs-lookup"><span data-stu-id="c350a-180">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="known-issues"></a><span data-ttu-id="c350a-181">已知問題</span><span class="sxs-lookup"><span data-stu-id="c350a-181">Known issues</span></span>

### <a name="openxr"></a><span data-ttu-id="c350a-182">OpenXR</span><span class="sxs-lookup"><span data-stu-id="c350a-182">OpenXR</span></span>

<span data-ttu-id="c350a-183">目前有一個已知的全像是「全像」遠端和 OpenXR 的問題，也就是沒有一直可用的手接點。</span><span class="sxs-lookup"><span data-stu-id="c350a-183">There's currently a known issue with Holographic Remoting and OpenXR, where hand joints aren't consistently available.</span></span>
<span data-ttu-id="c350a-184">此外，眼睛追蹤範例場景目前不相容，不過眼睛追蹤 *的確* 可以運作。</span><span class="sxs-lookup"><span data-stu-id="c350a-184">Additionally, the eye tracking sample scenes aren't currently compatible, though eye tracking *does* work.</span></span>

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a><span data-ttu-id="c350a-185">部分混合現實工具組標準著色器功能需要基礎封裝</span><span class="sxs-lookup"><span data-stu-id="c350a-185">Some Mixed Reality Toolkit Standard Shader features require the Foundation package</span></span>

<span data-ttu-id="c350a-186">透過 Unity 套件管理員匯入時，MRTK 標準著色器公用程式腳本 (例如： HoverLight.cs) 不會與標準資產套件中的著色器共置。</span><span class="sxs-lookup"><span data-stu-id="c350a-186">When imported via the Unity Package Manager, the MRTK Standard Shader utilities scripts (ex: HoverLight.cs) are not co-located with the shader in the Standard Assets package.</span></span> <span data-ttu-id="c350a-187">若要存取此功能，應用程式將需要匯入基礎套件。</span><span class="sxs-lookup"><span data-stu-id="c350a-187">To access this functionality, applications will require the Foundation package to be imported.</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="c350a-188">CameraCache 可能會在關機時建立新的攝影機</span><span class="sxs-lookup"><span data-stu-id="c350a-188">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="c350a-189">在某些情況下 (例如在 Unity 編輯器) 中使用 LeapMotion 提供者時，CameraCache 可能會在關閉時重新建立 MainCamera。</span><span class="sxs-lookup"><span data-stu-id="c350a-189">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="c350a-190">如需詳細資訊，請參閱 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 。</span><span class="sxs-lookup"><span data-stu-id="c350a-190">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="c350a-191">透過 Unity 套件管理員匯入範例時的 FileNotFoundException</span><span class="sxs-lookup"><span data-stu-id="c350a-191">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="c350a-192">根據專案路徑的長度，透過 Unity 套件管理員匯入範例可能會在 Unity 主控台中產生 FileNotFoundException 訊息。</span><span class="sxs-lookup"><span data-stu-id="c350a-192">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="c350a-193">造成這種情況的原因是「遺失」檔案的路徑超過 MAX_PATH (256 個字元) 。</span><span class="sxs-lookup"><span data-stu-id="c350a-193">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="c350a-194">若要解決此問題，請縮短專案路徑的長度。</span><span class="sxs-lookup"><span data-stu-id="c350a-194">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="c350a-195">未指定空間定位器。</span><span class="sxs-lookup"><span data-stu-id="c350a-195">No spatializer was specified.</span></span> <span data-ttu-id="c350a-196">應用程式將不支援空間音效</span><span class="sxs-lookup"><span data-stu-id="c350a-196">The application will not support Spatial Sound</span></span>

<span data-ttu-id="c350a-197">如果未設定音訊空間定位器，則會出現「未指定任何空間定位器」警告。</span><span class="sxs-lookup"><span data-stu-id="c350a-197">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="c350a-198">如果未安裝 XR 套件，則會發生這種情況，因為 Unity 包含這些套件中的 spatializers。</span><span class="sxs-lookup"><span data-stu-id="c350a-198">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="c350a-199">若要解決此問題，請確定：</span><span class="sxs-lookup"><span data-stu-id="c350a-199">To resolve, please ensure that:</span></span>

- <span data-ttu-id="c350a-200">**視窗**  > **套件管理員** 已安裝一或多個 XR 套件</span><span class="sxs-lookup"><span data-stu-id="c350a-200">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="c350a-201">**混合現實工具**  >  組 **公用程式**  > **設定 Unity 專案** 並為 **音訊空間定位器** 進行選取</span><span class="sxs-lookup"><span data-stu-id="c350a-201">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![選取音訊空間定位器](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="c350a-203">NullReferenceException：物件參考未設定為物件的實例 (SceneTransitionService.Initialize) </span><span class="sxs-lookup"><span data-stu-id="c350a-203">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="c350a-204">在某些情況下，開啟 `EyeTrackingDemo-00-RootScene` 可能會在 SceneTransitionService 類別的 Initialize 方法中造成 NullReferenceException。</span><span class="sxs-lookup"><span data-stu-id="c350a-204">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="c350a-205">此錯誤是因為未設定場景轉換服務的設定檔。</span><span class="sxs-lookup"><span data-stu-id="c350a-205">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="c350a-206">若要解決此問題，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c350a-206">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="c350a-207">流覽至階層 `MixedRealityToolkit` 中的物件</span><span class="sxs-lookup"><span data-stu-id="c350a-207">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="c350a-208">在 [偵測器] 視窗中，選取 `Extensions`</span><span class="sxs-lookup"><span data-stu-id="c350a-208">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="c350a-209">如果未展開，請展開 `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="c350a-209">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="c350a-210">將的值設定 `Configuration Profile` 為 **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="c350a-210">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![修正場景轉換設定檔](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="c350a-212">Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="c350a-212">Oculus Quest</span></span>

<span data-ttu-id="c350a-213">目前在 [以獨立平臺為目標時，使用 OCULUS XR 外掛程式](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)的已知問題。</span><span class="sxs-lookup"><span data-stu-id="c350a-213">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span>  <span data-ttu-id="c350a-214">查看 Oculus bug 追蹤程式/論壇/版本資訊以取得更新。</span><span class="sxs-lookup"><span data-stu-id="c350a-214">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="c350a-215">Bug 會以這一組3個錯誤表示：</span><span class="sxs-lookup"><span data-stu-id="c350a-215">The bug is signified with this set of 3 errors:</span></span>

![Oculus XR 外掛程式錯誤](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="c350a-217">UnityUI 和 TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="c350a-217">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="c350a-218">較新版本的 TextMeshPro 有一個已知問題 (1.5.0 + 或 2.1.1 +) ，其中下拉式清單和粗體字字元間距的預設字型大小已改變。</span><span class="sxs-lookup"><span data-stu-id="c350a-218">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![TMP 映射](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="c350a-220">這可以透過降級至舊版的 TextMeshPro 來解決。</span><span class="sxs-lookup"><span data-stu-id="c350a-220">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="c350a-221">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span><span class="sxs-lookup"><span data-stu-id="c350a-221">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
