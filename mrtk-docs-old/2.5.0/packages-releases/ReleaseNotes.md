---
title: ReleaseNotes
description: 目前 MRTK 版本的發行 nots
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 08f3c7cb3baacc74f65723de9a74fe2c56829804
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684921"
---
# <a name="microsoft-mixed-reality-toolkit-250-release-notes"></a><span data-ttu-id="1e25b-104">Microsoft Mixed Reality 工具組2.5.0 版本資訊</span><span class="sxs-lookup"><span data-stu-id="1e25b-104">Microsoft Mixed Reality Toolkit 2.5.0 release notes</span></span>

- [<span data-ttu-id="1e25b-105">新功能</span><span class="sxs-lookup"><span data-stu-id="1e25b-105">What's new</span></span>](#whats-new)
- [<span data-ttu-id="1e25b-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="1e25b-106">Breaking changes</span></span>](#breaking-changes)
- [<span data-ttu-id="1e25b-107">更新指導方針</span><span class="sxs-lookup"><span data-stu-id="1e25b-107">Updating guidance</span></span>](../updates-deployment/Updating.md#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="1e25b-108">已知問題</span><span class="sxs-lookup"><span data-stu-id="1e25b-108">Known issues</span></span>](#known-issues)

## <a name="whats-new"></a><span data-ttu-id="1e25b-109">最新消息</span><span class="sxs-lookup"><span data-stu-id="1e25b-109">What's new</span></span>

### <a name="unity-package-manager-upm-support"></a><span data-ttu-id="1e25b-110">Unity 封裝管理員 (UPM) 支援</span><span class="sxs-lookup"><span data-stu-id="1e25b-110">Unity Package Manager (UPM) support</span></span>

<span data-ttu-id="1e25b-111">混合現實工具組現在可以使用 Unity 封裝管理員進行管理。</span><span class="sxs-lookup"><span data-stu-id="1e25b-111">The Mixed Reality Toolkit can now be managed using the Unity Package Manager.</span></span>

![MRTK Foundation UPM 套件](../features/Images/Packaging/MRTK_FoundationUPM.png)

> [!Note]
> <span data-ttu-id="1e25b-113">匯入 MRTK UPM 套件需要一些手動步驟。</span><span class="sxs-lookup"><span data-stu-id="1e25b-113">There are some manual steps required to import the MRTK UPM packages.</span></span> <span data-ttu-id="1e25b-114">如需詳細資訊，請參閱 [混合現實工具組和 Unity 封裝管理員](usingupm.md) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-114">Please review [Mixed Reality Toolkit and Unity Package Manager](usingupm.md) for more information.</span></span>

### <a name="oculus-quest-xrsdk-support"></a><span data-ttu-id="1e25b-115">Oculus 追求 XRSDK 支援</span><span class="sxs-lookup"><span data-stu-id="1e25b-115">Oculus Quest XRSDK support</span></span>

<span data-ttu-id="1e25b-116">MRTK 現在支援使用原生 XR SDK 管線執行 Oculus 的執行耳機和控制器。</span><span class="sxs-lookup"><span data-stu-id="1e25b-116">MRTK now supports running Oculus Quest Headsets and Controllers using the native XR SDK pipeline.</span></span> <span data-ttu-id="1e25b-117">[Oculus Integration Unity 套件](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)也支援手動追蹤，感謝[ERIC Provencher](https://twitter.com/prvncher)在 MRTK 上的工作！</span><span class="sxs-lookup"><span data-stu-id="1e25b-117">Hand tracking is also supported with the [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) thanks to [Eric Provencher's](https://twitter.com/prvncher) work on MRTK-Quest!</span></span>

<span data-ttu-id="1e25b-118">如需如何使用新的管線在 Oculus 上部署裝置的指示，請參閱 Oculus 操作 [設定指南](../features/CrossPlatform/OculusQuestMRTK.md)</span><span class="sxs-lookup"><span data-stu-id="1e25b-118">For instructions on how to deploy your device on the Oculus Quest using the new pipeline, see the [Oculus Quest Setup Guide](../features/CrossPlatform/OculusQuestMRTK.md)</span></span>

### <a name="scrolling-object-collection"></a><span data-ttu-id="1e25b-119">滾動物件集合</span><span class="sxs-lookup"><span data-stu-id="1e25b-119">Scrolling Object Collection</span></span>

<span data-ttu-id="1e25b-120">MRTK UX 元件已從實驗性功能進行升級，並可讓您更自由地 layouting 不同大小的3D 內容，並新增對尚未附加 colliders 之物件的支援。</span><span class="sxs-lookup"><span data-stu-id="1e25b-120">The MRTK UX component has been upgraded from an experimental feature and offers more freedom for layouting 3D content of different sizes with added support for objects that have no colliders attached.</span></span> <span data-ttu-id="1e25b-121">另外也加入了停用內容遮罩的新選項，讓原型設計更容易。</span><span class="sxs-lookup"><span data-stu-id="1e25b-121">A new option for disabling content masking was also added, making prototyping easier.</span></span>

<span data-ttu-id="1e25b-122">如需詳細資訊，請參閱 [滾動物件集合](../features/README_ScrollingObjectCollection.md) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-122">See [Scrolling Object Collection](../features/README_ScrollingObjectCollection.md) for more information.</span></span>

![滾動物件集合](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a><span data-ttu-id="1e25b-124">傳送指標動畫、處理和音效改進</span><span class="sxs-lookup"><span data-stu-id="1e25b-124">Teleport pointer animation, handling, and sound improvements</span></span>

<span data-ttu-id="1e25b-125">傳送指標現在已改善動畫和音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="1e25b-125">The teleport pointer now has improved animations and audio feedback.</span></span> <span data-ttu-id="1e25b-126">我們也改善了「傳送」指標的處理方式，以便在從附近表面轉換到更遠的表面時處理更平滑的處理。</span><span class="sxs-lookup"><span data-stu-id="1e25b-126">We also improved the handling of the teleport pointer so it handles smoother when transitioning from pointing at nearby surfaces to farther away surfaces.</span></span>

[https://streamable.com/3f222q](https://streamable.com/3f222q)

### <a name="input-simulation-cheat-sheet"></a><span data-ttu-id="1e25b-127">輸入模擬功能提要</span><span class="sxs-lookup"><span data-stu-id="1e25b-127">Input Simulation Cheat Sheet</span></span>

<span data-ttu-id="1e25b-128">HandInteractionExamples 場景現在具有可設定的快捷方式，可顯示輸入模擬的說明頁面</span><span class="sxs-lookup"><span data-stu-id="1e25b-128">The HandInteractionExamples scene now has a configurable shortcut to show a help page for input simulation</span></span>

![輸入模擬功能提要](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a><span data-ttu-id="1e25b-130">使用滑鼠輸入模擬眼睛</span><span class="sxs-lookup"><span data-stu-id="1e25b-130">Input Simulation Eye Gaze with mouse</span></span>

<span data-ttu-id="1e25b-131">使用者現在可以使用滑鼠來模擬眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="1e25b-131">Users can now use the Mouse for simulating eye tracking.</span></span> <span data-ttu-id="1e25b-132">查看 `Eye Simulation Mode` 輸入模擬設定檔中的欄位，並將它設定為滑鼠。</span><span class="sxs-lookup"><span data-stu-id="1e25b-132">See the `Eye Simulation Mode` field in the input simulation profile and set it to Mouse.</span></span> <span data-ttu-id="1e25b-133">這會取代前一個 `Simulate Eye Position` 欄位</span><span class="sxs-lookup"><span data-stu-id="1e25b-133">This replaces the previous `Simulate Eye Position` field</span></span>

![眼睛的老鼠](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a><span data-ttu-id="1e25b-135">編輯器播放模式下的輸入模擬移動控制器</span><span class="sxs-lookup"><span data-stu-id="1e25b-135">Input Simulation Motion Controller in Editor Play Mode</span></span>

<span data-ttu-id="1e25b-136">使用者現在可以模擬移動控制器，就像手入編輯器播放模式一樣。</span><span class="sxs-lookup"><span data-stu-id="1e25b-136">Users can now simulate motion controller just like hands in editor play mode.</span></span> <span data-ttu-id="1e25b-137">目前支援觸發程式、抓取和功能表按鈕。</span><span class="sxs-lookup"><span data-stu-id="1e25b-137">The trigger, grab and menu buttons are currently supported.</span></span>

### <a name="conical-grab-pointer"></a><span data-ttu-id="1e25b-138">圓錐抓取指標</span><span class="sxs-lookup"><span data-stu-id="1e25b-138">Conical Grab Pointer</span></span>

<span data-ttu-id="1e25b-139">您現在可以將抓取指標設定為使用來自抓取點的錐形來查詢附近的物件，而不是球體。</span><span class="sxs-lookup"><span data-stu-id="1e25b-139">Grab pointers can now be configured to query for nearby objects using a cone from the grab point rather than a sphere.</span></span> <span data-ttu-id="1e25b-140">這與預設 Hololens 2 介面中的行為更相似，後者會使用錐形來查詢附近的物件。</span><span class="sxs-lookup"><span data-stu-id="1e25b-140">This more closely resembles the behavior from the default Hololens 2 interface, which queries for nearby objects using a cone.</span></span> <span data-ttu-id="1e25b-141">DefaultHoloLens2InputSystemProfile 也已調整為使用新的 `ConicalGrabPointer` 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-141">The DefaultHoloLens2InputSystemProfile has also been adjusted to use the new `ConicalGrabPointer`.</span></span>

![圓錐抓取指標](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a><span data-ttu-id="1e25b-143">TestUtilities 套件</span><span class="sxs-lookup"><span data-stu-id="1e25b-143">TestUtilities package</span></span>

<span data-ttu-id="1e25b-144">現在有一個套件 (MixedReality) ，其中包含 PlayMode 和 TestMode 測試基礎結構，MRTK 會使用該基礎結構來建立端對端測試。</span><span class="sxs-lookup"><span data-stu-id="1e25b-144">There is now a package (Microsoft.MixedReality.Toolkit.Unity.TestUtilities.2.5.0.unitypackage) that contains the PlayMode and TestMode test infrastructure that the MRTK uses to create end-to-end tests.</span></span> <span data-ttu-id="1e25b-145">此基礎結構對 MRTK 小組本身來說非常方便，而我們很高興能讓取用者使用這個基礎結構，將測試涵蓋範圍新增至自己的專案。</span><span class="sxs-lookup"><span data-stu-id="1e25b-145">This infrastructure has been extremely handy for the MRTK team itself, and we're excited to have consumers use this to add test coverage to their own projects.</span></span>

<span data-ttu-id="1e25b-146">下列程式碼示範如何建立測試手、將它顯示在特定位置、四處移動，然後進行縮小並開啟。</span><span class="sxs-lookup"><span data-stu-id="1e25b-146">The following code shows how to create a test hand, show it at a certain location, move it around, and then pinch and open.</span></span>

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

<span data-ttu-id="1e25b-147">如需如何使用這些 TestUtilities 撰寫測試的指示，請參閱這一節有關[撰寫測試](../Contributing/UnitTests.md#writing-tests)的資訊。</span><span class="sxs-lookup"><span data-stu-id="1e25b-147">For instructions on how to write a test using these TestUtilities, see this section on [writing tests](../Contributing/UnitTests.md#writing-tests)</span></span>

<span data-ttu-id="1e25b-148">如需使用此基礎結構的現有測試範例，請參閱 MRTK 的 [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)</span><span class="sxs-lookup"><span data-stu-id="1e25b-148">For examples of existing tests that use this infrastructure, see MRTK's [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)</span></span>

### <a name="support-for-the-leap-motion-451-unity-modules"></a><span data-ttu-id="1e25b-149">支援閏運動 4.5.1 Unity 模組</span><span class="sxs-lookup"><span data-stu-id="1e25b-149">Support for the Leap Motion 4.5.1 Unity Modules</span></span>

<span data-ttu-id="1e25b-150">已新增對閏運動 Unity 模組4.5.1 版的支援，且已移除對4.4.0 資產的支援。</span><span class="sxs-lookup"><span data-stu-id="1e25b-150">Support for the Leap Motion Unity Modules version 4.5.1 has been added and support for the 4.4.0 assets has been removed.</span></span> <span data-ttu-id="1e25b-151">目前支援的 Leap Unity 模組版本為4.5.0 和4.5.1。</span><span class="sxs-lookup"><span data-stu-id="1e25b-151">The current supported versions of the Leap Motion Unity Modules are 4.5.0 and 4.5.1.</span></span>

<span data-ttu-id="1e25b-152">另外還有一項額外的步驟來進行初始的 Leap 移動整合，如需詳細資訊，請參閱 [如何在 MRTK 中設定 Leap 的追蹤動作](../features/CrossPlatform/LeapMotionMRTK.md) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-152">There is also an additional step for initial Leap Motion integration, see [How to Configure the Leap Motion Hand Tracking in MRTK](../features/CrossPlatform/LeapMotionMRTK.md) for more information.</span></span>

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a><span data-ttu-id="1e25b-153">空間感知網格觀察者更妥善處理自訂的材質</span><span class="sxs-lookup"><span data-stu-id="1e25b-153">Spatial Awareness Mesh Observer better handles customization of materials</span></span>

<span data-ttu-id="1e25b-154">在此版本中， `Windows Mixed Reality Spatial Mesh Observer` 和 `Generic XR SDK Spatial Mesh Observer` 元件已改進視覺材質處理。</span><span class="sxs-lookup"><span data-stu-id="1e25b-154">With this release, the `Windows Mixed Reality Spatial Mesh Observer` and the `Generic XR SDK Spatial Mesh Observer` components have improved visual material handling.</span></span> <span data-ttu-id="1e25b-155">當觀察者更新了網格，而這些資料在先前已重設為設定檔中所設定的預設 VisibleMaterial 時，現在會保留材質。</span><span class="sxs-lookup"><span data-stu-id="1e25b-155">Materials are now preserved when a mesh has been updated by the observer where, previously, they were reset to the default VisibleMaterial as configured in the profile.</span></span>

<span data-ttu-id="1e25b-156">這可讓開發人員改變網格材質，而不會意外覆寫變更。</span><span class="sxs-lookup"><span data-stu-id="1e25b-156">This enables developers to alter the mesh material and not have the changes overwritten unexpectedly.</span></span>

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a><span data-ttu-id="1e25b-157">Link.xml 在 MixedRealityToolkit 產生的資料夾中建立</span><span class="sxs-lookup"><span data-stu-id="1e25b-157">Link.xml created in the MixedRealityToolkit.Generated folder</span></span>

<span data-ttu-id="1e25b-158">隨著 Unity 套件管理員 MRTK 的推出，MRTK 現在會將檔案寫入 `link.xml` `Assets/MixedRealityToolkit.Generated` 資料夾中（如果沒有的話）。</span><span class="sxs-lookup"><span data-stu-id="1e25b-158">With the introduction of Unity Package Manger MRTK, MRTK now writes a `link.xml` file to the `Assets/MixedRealityToolkit.Generated` folder, if none is present.</span></span> <span data-ttu-id="1e25b-159">建議您將這個檔案加入 (， `link.xml.meta`) 加入原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="1e25b-159">It is recommended to add this file (and `link.xml.meta`) be added to source control.</span></span> <span data-ttu-id="1e25b-160">Link.xml 是用來影響 Unity 連結器的 [managed 程式碼去除](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) 功能。</span><span class="sxs-lookup"><span data-stu-id="1e25b-160">Link.xml is used to influence the [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) functionality of the Unity linker.</span></span>

<span data-ttu-id="1e25b-161">如需 MRTK link.xml 檔案的詳細資訊，請參閱 [MRTK 和 managed code 抽出](../out-of-scope/MRTK_and_managed_code_stripping.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="1e25b-161">More information on the MRTK link.xml file can be found in the [MRTK and managed code stripping](../out-of-scope/MRTK_and_managed_code_stripping.md) article.</span></span>

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a><span data-ttu-id="1e25b-162">Unity 2019.3 +： MRTK configuration 對話方塊不再嘗試啟用舊版 XR 支援</span><span class="sxs-lookup"><span data-stu-id="1e25b-162">Unity 2019.3+: MRTK configuration dialog no longer attempts to enable legacy XR support</span></span>

<span data-ttu-id="1e25b-163">為了避免在使用 Unity 的 XR 平臺時可能發生衝突，已從 [MRTK 設定] 對話方塊中移除啟用舊版 XR 支援的選項。</span><span class="sxs-lookup"><span data-stu-id="1e25b-163">To avoid potential conflicts when using Unity's XR Platform, the option to enable legacy XR support has been removed from the MRTK configuration dialog.</span></span> <span data-ttu-id="1e25b-164">如有需要，您可以在 Unity 2019 中使用 [**編輯**  >  **專案設定**  >
 **播放機**]  >  **XR 設定**  >  **虛擬實境支援** 的舊版 XR 支援。</span><span class="sxs-lookup"><span data-stu-id="1e25b-164">If desired, legacy XR support can be enabled, in Unity 2019, using **Edit** > **Project Settings** >
**Player** > **XR Settings** > **Virtual Reality Supported**.</span></span>

### <a name="reduction-in-initializeonload-overhead"></a><span data-ttu-id="1e25b-165">減少 InitializeOnLoad 額外負荷</span><span class="sxs-lookup"><span data-stu-id="1e25b-165">Reduction in InitializeOnLoad overhead</span></span>

<span data-ttu-id="1e25b-166">我們已執行工作來減少在 InitializeOnLoad 處理常式中執行的工作量，而這應該會導致內部迴圈開發速度的改進。</span><span class="sxs-lookup"><span data-stu-id="1e25b-166">We've been doing work to reduce the amount of work that runs in InitializeOnLoad handlers, which should lead to improvements in inner loop development speed.</span></span> <span data-ttu-id="1e25b-167">InitializeOnLoad 處理常式會在每次編譯腳本、進入播放模式之前，以及在編輯器啟動時執行。</span><span class="sxs-lookup"><span data-stu-id="1e25b-167">InitializeOnLoad handlers run every time a script is compiled, prior to entering play mode, and also at editor launch.</span></span> <span data-ttu-id="1e25b-168">這些處理常式現在會在較少的情況下執行，進而改善一般 Unity 回應性。</span><span class="sxs-lookup"><span data-stu-id="1e25b-168">These handlers now run in far fewer cases, resulting in general Unity responsiveness improvements.</span></span>

<span data-ttu-id="1e25b-169">在某些情況下，必須進行取捨：</span><span class="sxs-lookup"><span data-stu-id="1e25b-169">In some cases there was a tradeoff that had to be made:</span></span>

- <span data-ttu-id="1e25b-170">若要進行額外的整合步驟，請參閱 [Leap 動作手追蹤](../features/CrossPlatform/LeapMotionMRTK.md) 設定。</span><span class="sxs-lookup"><span data-stu-id="1e25b-170">See [Leap Motion Hand Tracking Configuration](../features/CrossPlatform/LeapMotionMRTK.md) for the extra integration step.</span></span>
- <span data-ttu-id="1e25b-171">針對使用 ARFoundation 的使用者，現在可以在其快速入門步驟中進行額外的手動步驟。</span><span class="sxs-lookup"><span data-stu-id="1e25b-171">For those who are using ARFoundation, there's now an additional manual step in its getting started steps.</span></span>
<span data-ttu-id="1e25b-172">如需新步驟，請參閱 [ARFoundation](../features/CrossPlatform/UsingARFoundation.md#install-required-packages) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-172">See [ARFoundation](../features/CrossPlatform/UsingARFoundation.md#install-required-packages) for the new steps.</span></span>
- <span data-ttu-id="1e25b-173">對於將在 HoloLens 2 上使用 [舊版 XR 管線](../features/Tools/HolographicRemoting.md#legacy-xr-setup-instructions) 的使用者，現在有一個 [手動步驟](../features/Tools/HolographicRemoting.md#dotnetwinrt_present-define-written-into-player-settings) 可以執行。</span><span class="sxs-lookup"><span data-stu-id="1e25b-173">For those who will be using [Holographic Remoting with legacy XR pipeline](../features/Tools/HolographicRemoting.md#legacy-xr-setup-instructions) on HoloLens 2, there is now a [manual step](../features/Tools/HolographicRemoting.md#dotnetwinrt_present-define-written-into-player-settings) to perform.</span></span>

### <a name="bounds-control-graduated"></a><span data-ttu-id="1e25b-174">界限控制分級</span><span class="sxs-lookup"><span data-stu-id="1e25b-174">Bounds control graduated</span></span>

<span data-ttu-id="1e25b-175">![系結控制 ](../features/Images/BoundsControl/MRTK_BoundsControl_Main.png)
 [界限控制項](../features/README_BoundsControl.md)從實驗中開始，並提供一大堆新功能和大量的 bug 修正。</span><span class="sxs-lookup"><span data-stu-id="1e25b-175">![Bounds control](../features/Images/BoundsControl/MRTK_BoundsControl_Main.png)
[Bounds control](../features/README_BoundsControl.md) graduated out of experimental and comes with a bunch of new features and tons of bug fixes.</span></span>
<span data-ttu-id="1e25b-176">此更新的重點清單如下：</span><span class="sxs-lookup"><span data-stu-id="1e25b-176">Here a list of the highlights of this update:</span></span>

- <span data-ttu-id="1e25b-177">屬性分為設定，可讓您更輕鬆地設定界限控制項</span><span class="sxs-lookup"><span data-stu-id="1e25b-177">properties are split into configurations which makes it easier to set up bounds control</span></span>
- <span data-ttu-id="1e25b-178">設定可以透過可編寫腳本的物件共用</span><span class="sxs-lookup"><span data-stu-id="1e25b-178">configurations can be shared through scriptable objects</span></span>
- <span data-ttu-id="1e25b-179">每個屬性/可編寫腳本的屬性都可設定執行時間</span><span class="sxs-lookup"><span data-stu-id="1e25b-179">every property / scriptable property is runtime configurable</span></span>
- <span data-ttu-id="1e25b-180">不再于屬性變更時重新建立界限控制設備</span><span class="sxs-lookup"><span data-stu-id="1e25b-180">bounds control rig isn't recreated on property changes anymore</span></span>
- <span data-ttu-id="1e25b-181">轉譯控制碼支援</span><span class="sxs-lookup"><span data-stu-id="1e25b-181">translation handles support</span></span>
- <span data-ttu-id="1e25b-182">透過條件約束管理員的完整條件約束支援</span><span class="sxs-lookup"><span data-stu-id="1e25b-182">full constraint support through constraint manager</span></span>
- <span data-ttu-id="1e25b-183">彈性系統整合 (實驗性) </span><span class="sxs-lookup"><span data-stu-id="1e25b-183">elastics system integration (experimental)</span></span>

<span data-ttu-id="1e25b-184">舊的周框方塊現在已被取代，而且使用周框方塊的現有遊戲物件可以 [使用「遷移工具](../features/Tools/MigrationWindow.md) 」或「周框方塊」偵測 [器](../features/README_BoundingBox.md#migrating-to-bounds-control)進行升級。</span><span class="sxs-lookup"><span data-stu-id="1e25b-184">The old bounding box is now deprecated and existing game objects using bounding box can be [upgraded using the migration tool](../features/Tools/MigrationWindow.md) or the [bounding box inspector](../features/README_BoundingBox.md#migrating-to-bounds-control).</span></span>

### <a name="constraint-manager-component"></a><span data-ttu-id="1e25b-185">條件約束管理員元件</span><span class="sxs-lookup"><span data-stu-id="1e25b-185">Constraint manager component</span></span>

<span data-ttu-id="1e25b-186">條件約束現在可透過新的 [條件約束管理員元件](../features/README_ConstraintManager.md)，用於界限控制項和物件操作工具。</span><span class="sxs-lookup"><span data-stu-id="1e25b-186">Constraints can now be used by both, bounds control and object manipulator via the new [constraint manager component](../features/README_ConstraintManager.md).</span></span> <span data-ttu-id="1e25b-187">這兩個元件都會建立每個預設的條件約束管理員，並自動處理任何附加的條件約束。</span><span class="sxs-lookup"><span data-stu-id="1e25b-187">Both components will create a constraint manager per default and process any attached constraints automatically.</span></span>

<span data-ttu-id="1e25b-188">此外，自動行為條件約束管理員也會隨附手動模式，讓使用者決定應處理的條件約束。</span><span class="sxs-lookup"><span data-stu-id="1e25b-188">Additionally to the automatic behavior constraint manager also comes with a manual mode that lets users decide which constraint should be processed.</span></span>
<span data-ttu-id="1e25b-189">基於這個理由，我們在屬性偵測器中顯示條件約束的方式改變了一點。</span><span class="sxs-lookup"><span data-stu-id="1e25b-189">For this reason the way we display constraints in the property inspector changed a bit.</span></span>

<img src="../features/Images/ConstraintManager/ManualSelection.png" width="600" alt="Manual selection">

<span data-ttu-id="1e25b-190">套用至元件的條件約束現在會顯示為條件約束管理員元件中的清單，而使用條件約束管理員 ([界限控制項](../features/README_BoundsControl.md#constraint-system) 或 [物件](../features/README_ObjectManipulator.md#constraint-manager) 操作工具的元件) 現在會顯示選取的條件約束管理員和模式 (自動或手動) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-190">The constraints that are applied to the component are now shown as a list in the constraint manager component whereas the component using the constraint manager (either [bounds control](../features/README_BoundsControl.md#constraint-system) or [object manipulator](../features/README_ObjectManipulator.md#constraint-manager)) will now show the selected constraint manager and mode (auto or manual).</span></span>
<span data-ttu-id="1e25b-191">如需詳細資訊，請參閱檔中的「 [條件約束管理員](../features/README_ConstraintManager.md) 」一節。</span><span class="sxs-lookup"><span data-stu-id="1e25b-191">For more information read the [constraint manager](../features/README_ConstraintManager.md) section in our docs.</span></span>

### <a name="hololens-2-button-material-update"></a><span data-ttu-id="1e25b-192">HoloLens 2 按鈕材質更新</span><span class="sxs-lookup"><span data-stu-id="1e25b-192">HoloLens 2 Button material update</span></span>

<span data-ttu-id="1e25b-193">已更新 HoloLens 2 按鈕的 front 籠材質，以移除 MRC 中的黑色色彩。</span><span class="sxs-lookup"><span data-stu-id="1e25b-193">Updated HoloLens 2 Button's front cage material to remove black color in MRC.</span></span>

![HoloLens 2 按鈕材質更新](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a><span data-ttu-id="1e25b-195">描述面板更新、可移動範例場景</span><span class="sxs-lookup"><span data-stu-id="1e25b-195">Description panel update, movable example scene</span></span>

<span data-ttu-id="1e25b-196">更新的描述面板。</span><span class="sxs-lookup"><span data-stu-id="1e25b-196">Updated description panel.</span></span> <span data-ttu-id="1e25b-197"> (SceneDescriptionPanelRev. 預製專案) 新的設計提供 grabbable 的頂線，可讓使用者調整/移動整個場景。</span><span class="sxs-lookup"><span data-stu-id="1e25b-197">(SceneDescriptionPanelRev.prefab) New design provides a grabbable top bar which allows the user to adjust/move the entire scene.</span></span>

![描述面板更新](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a><span data-ttu-id="1e25b-199">空間網格視覺效果-敲擊時的脈衝</span><span class="sxs-lookup"><span data-stu-id="1e25b-199">Spatial mesh visualization - Pulse on air-tap</span></span>

<span data-ttu-id="1e25b-200">已更新空間網格的脈衝著色器範例，以符合 HoloLens 2 的 shell 行為。</span><span class="sxs-lookup"><span data-stu-id="1e25b-200">Updated pulse shader example for the spatial mesh to match HoloLens 2's shell behavior.</span></span>

![按兩下時的脈衝](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system---experimental"></a><span data-ttu-id="1e25b-202">彈性系統-實驗性</span><span class="sxs-lookup"><span data-stu-id="1e25b-202">Elastic system - Experimental</span></span>

![彈性 System2](../features/Images/Elastics/Elastics_Main.gif)

<span data-ttu-id="1e25b-204">MRTK 現在隨附彈性的 [模擬系統](../features/Elastics/ElasticSystem.md) ，其中包含各種可延伸和彈性的子類別，提供4維四元數的系結、三維的成交量彈簧和簡單線性彈簧系統。</span><span class="sxs-lookup"><span data-stu-id="1e25b-204">MRTK now comes with an [elastic simulation system](../features/Elastics/ElasticSystem.md) that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="1e25b-205">目前支援 [彈性 manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 的下列 MRTK 元件可利用彈性功能：</span><span class="sxs-lookup"><span data-stu-id="1e25b-205">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="1e25b-206">界限控制項</span><span class="sxs-lookup"><span data-stu-id="1e25b-206">Bounds control</span></span>](../features/README_BoundsControl.md#elastics-experimental)
- [<span data-ttu-id="1e25b-207">物件操作工具</span><span class="sxs-lookup"><span data-stu-id="1e25b-207">Object manipulator</span></span>](../features/README_ObjectManipulator.md#elastics-experimental)  

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Bounds control">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Boject manupulator">

### <a name="joystick-experimental"></a><span data-ttu-id="1e25b-208">實驗性)  (搖桿</span><span class="sxs-lookup"><span data-stu-id="1e25b-208">Joystick (Experimental)</span></span>

<span data-ttu-id="1e25b-209">可以控制大型目標物件的搖桿介面範例。</span><span class="sxs-lookup"><span data-stu-id="1e25b-209">An example of joystick interface that can control a large target object.</span></span>

![操縱 杆](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a><span data-ttu-id="1e25b-211">色彩選擇器 (實驗性) </span><span class="sxs-lookup"><span data-stu-id="1e25b-211">Color picker (Experimental)</span></span>

<span data-ttu-id="1e25b-212">實驗性控制項，可讓您輕鬆地在執行時間變更任何物件的材質色彩。</span><span class="sxs-lookup"><span data-stu-id="1e25b-212">An experimental control that makes it easy to change material colors on any object at runtime.</span></span>
<span data-ttu-id="1e25b-213">![色彩選擇器](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)</span><span class="sxs-lookup"><span data-stu-id="1e25b-213">![Color picker](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)</span></span>

![色彩選擇器](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

<br/><br/>

## <a name="breaking-changes"></a><span data-ttu-id="1e25b-215">重大變更</span><span class="sxs-lookup"><span data-stu-id="1e25b-215">Breaking changes</span></span>

### <a name="assembly-definition-files-changes"></a><span data-ttu-id="1e25b-216">元件定義檔變更</span><span class="sxs-lookup"><span data-stu-id="1e25b-216">Assembly Definition Files Changes</span></span>

<span data-ttu-id="1e25b-217">有些 asmdef 檔案已變更，現在僅支援 Unity 2018.4.13 f1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1e25b-217">Some asmdef files are changed and are now only supporting Unity 2018.4.13f1 or later.</span></span> <span data-ttu-id="1e25b-218">在舊版 Unity 中 upating 至 MRTK 2.5 時，將會顯示編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e25b-218">Compilation errors will show up when upating to MRTK 2.5 in earlier versions of Unity.</span></span> <span data-ttu-id="1e25b-219">若要修正此問題，請 `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` 移至 [專案] 視窗，並移除偵測器中遺漏的參考。</span><span class="sxs-lookup"><span data-stu-id="1e25b-219">This can be fixed by going to `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` in the project window and removing the missing reference in the inspector.</span></span> <span data-ttu-id="1e25b-220">使用和重複執行這些步驟 `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-220">Repeat those steps with `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` and `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef`.</span></span> <span data-ttu-id="1e25b-221">請注意，您必須將這三個 asmdef 檔案取代為原始 (（亦即，升級至 Unity 2019 時未修改的) ），以還原變更。</span><span class="sxs-lookup"><span data-stu-id="1e25b-221">Note you must revert the changes by replacing those three asmdef files with original (i.e. unmodified) ones when upgrading to Unity 2019.</span></span>

### <a name="imixedrealitypointermediator"></a><span data-ttu-id="1e25b-222">IMixedRealityPointerMediator</span><span class="sxs-lookup"><span data-stu-id="1e25b-222">IMixedRealityPointerMediator</span></span>

<span data-ttu-id="1e25b-223">此介面已更新為具有新的函式：</span><span class="sxs-lookup"><span data-stu-id="1e25b-223">This interface has been updated to have a new function:</span></span>

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

<span data-ttu-id="1e25b-224">如果您有不具子類別 DefaultPointerMediator 的自訂指標中繼程式，您必須執行這個新的函式。</span><span class="sxs-lookup"><span data-stu-id="1e25b-224">If you have a custom pointer mediator that doesn't subclass DefaultPointerMediator, you will need to implement this new function.</span></span> <span data-ttu-id="1e25b-225">如需這種新增原因的詳細背景，請參閱 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-225">See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) for more background on why this was added.</span></span> <span data-ttu-id="1e25b-226">這是為了確保指標喜好設定會明確地傳遞至中繼程式，而不是根據採用 IPointerPreferences 的函式是否存在而隱含地完成。</span><span class="sxs-lookup"><span data-stu-id="1e25b-226">This was added to ensure that pointer preferences would be explicitly passed to the mediator, rather than having it be implicitly done based on the presence of a constructor that took a IPointerPreferences.</span></span>

### <a name="rest--device-portal-api"></a><span data-ttu-id="1e25b-227">Rest/裝置入口網站 API</span><span class="sxs-lookup"><span data-stu-id="1e25b-227">Rest / Device Portal API</span></span>

<span data-ttu-id="1e25b-228">`UseSSL`靜態屬性已從移 `Rest` 至 `DevicePortal` 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-228">The `UseSSL` static property has been moved from `Rest` to `DevicePortal`.</span></span>

<span data-ttu-id="1e25b-229">如果您先前已執行此操作 .。。</span><span class="sxs-lookup"><span data-stu-id="1e25b-229">If you did this previously...</span></span>

```csharp
Rest.UseSSL = true
```

<span data-ttu-id="1e25b-230">現在就完成了 .。。</span><span class="sxs-lookup"><span data-stu-id="1e25b-230">Do this now...</span></span>

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a><span data-ttu-id="1e25b-231">Link.xml</span><span class="sxs-lookup"><span data-stu-id="1e25b-231">Link.xml</span></span>

<span data-ttu-id="1e25b-232">如果應用程式先前使用 MRTK 的 NuGet 散發套件，則已 `link.xml` 從基礎封裝中移除該檔案。</span><span class="sxs-lookup"><span data-stu-id="1e25b-232">If an application was previously using the NuGet distribution of the MRTK, the `link.xml` file has been removed from the Foundation package.</span></span> <span data-ttu-id="1e25b-233">若要還原程式碼保留規則，請在 Unity 中開啟專案一次，並在中建立預設檔案 `link.xml` `Assets/MixedRealityToolkit.Generated` 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-233">To restore code preservation rules, opening the project in Unity once will create a default `link.xml` file in `Assets/MixedRealityToolkit.Generated`.</span></span> <span data-ttu-id="1e25b-234">建議將此檔案 (，並 `link.xml.meta`) 新增至原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="1e25b-234">It is recommended that this file (and `link.xml.meta`) be added to source control.</span></span>

### <a name="transform-constraint-changes"></a><span data-ttu-id="1e25b-235">轉換條件約束變更</span><span class="sxs-lookup"><span data-stu-id="1e25b-235">Transform Constraint Changes</span></span>

<span data-ttu-id="1e25b-236">TargetTransform 屬性已標示為過時，因為條件約束系統未使用它。</span><span class="sxs-lookup"><span data-stu-id="1e25b-236">TargetTransform property has been marked as obsolete as it wasn't used by constraint system.</span></span> <span data-ttu-id="1e25b-237">條件約束邏輯是以傳遞至 Initialize 和 Apply 方法的轉換為基礎。</span><span class="sxs-lookup"><span data-stu-id="1e25b-237">Constraint logic is based on the transform passed into Initialize and Apply methods.</span></span> <span data-ttu-id="1e25b-238">依賴這個屬性的衍生使用者條件約束，可以藉由儲存條件約束元件的轉換，來快取其實 TargetTransform，以達成相同的行為。</span><span class="sxs-lookup"><span data-stu-id="1e25b-238">Derived user constraints that rely on this property can cache the TargetTransform in their implementation by storing the transform of the constraint component to achieve the same behavior.</span></span>

<span data-ttu-id="1e25b-239">預存的初始世界姿勢 `worldPoseOnManipulationStart` 資料類型已從 MixedRealityPose 變更為 MixedRealityTransform，其中包含操作物件的本機縮放值。</span><span class="sxs-lookup"><span data-stu-id="1e25b-239">The stored initial world pose `worldPoseOnManipulationStart` data type has been changed from MixedRealityPose to MixedRealityTransform, which includes the local scale value of the manipulated object.</span></span> <span data-ttu-id="1e25b-240">有了這種變更，就不需要再另行快取任何初始調整值。</span><span class="sxs-lookup"><span data-stu-id="1e25b-240">With this change it's not necessary to separately cache any initial scale values anymore.</span></span>

### <a name="new-property-in-imixedrealitydictationsystem"></a><span data-ttu-id="1e25b-241">IMixedRealityDictationSystem 中的新屬性</span><span class="sxs-lookup"><span data-stu-id="1e25b-241">New Property in IMixedRealityDictationSystem</span></span>

<span data-ttu-id="1e25b-242">已將新的屬性 `AudioClip` 新增至 IMixedRealityDictationSystem 介面。</span><span class="sxs-lookup"><span data-stu-id="1e25b-242">A new property `AudioClip` has been added to the IMixedRealityDictationSystem interface.</span></span> <span data-ttu-id="1e25b-243">`AudioClip`屬性可讓您存取與目前聽寫會話相關聯的音訊剪輯。</span><span class="sxs-lookup"><span data-stu-id="1e25b-243">The `AudioClip` property enables access to the audio clip associated with the current dictation session.</span></span> <span data-ttu-id="1e25b-244">使用者必須在其執行介面的腳本中執行屬性。</span><span class="sxs-lookup"><span data-stu-id="1e25b-244">Users must implement the property in their scripts implementing the interface.</span></span>

### <a name="service-facades-turn-down"></a><span data-ttu-id="1e25b-245">服務 Facade 關機</span><span class="sxs-lookup"><span data-stu-id="1e25b-245">Service Facades turn down</span></span>

<span data-ttu-id="1e25b-246">[服務 facade](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/06a06778e38da622b37cc299a93f16e143b7bdeb/Assets/MRTK/Core/Inspectors/MixedRealityToolkitFacadeHandler.cs) 會在2.5 中關閉。</span><span class="sxs-lookup"><span data-stu-id="1e25b-246">[Services facades](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/06a06778e38da622b37cc299a93f16e143b7bdeb/Assets/MRTK/Core/Inspectors/MixedRealityToolkitFacadeHandler.cs) are being turned down in 2.5.</span></span> <span data-ttu-id="1e25b-247">這項功能最初是為了讓 MRTK 設定檔的設定變得更容易 (藉由建立假的場景內 Gameobject 來表示每個 MRTK 的服務) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-247">This feature was originally added to make configuration of the MRTK profiles easier (by creating fake in-scene GameObjects that represented each of MRTK's services).</span></span> <span data-ttu-id="1e25b-248">在長時間執行的情況下，我們想要避免建立假的遊戲中物件，並嘗試將它們同步 (因為資料同步和「真實事實」問題很難調整規模，並能正確) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-248">In the long run, we want to avoid creating fake in-game objects and trying to keep them in sync (as data sync and "source of truth" issues are notoriously difficult to scale and get right).</span></span>

<span data-ttu-id="1e25b-249">在2.5 中，服務外觀處理常式會保持不變，以確保專案升級順暢，服務外觀處理常式會刪除專案中的任何 facade，以確保在2.5 中開啟的場景會自動修正。</span><span class="sxs-lookup"><span data-stu-id="1e25b-249">In 2.5, the service facade handlers are kept around to ensure that project upgrade goes smoothly - any facades that exist in the project will be deleted by the service facade handler to ensure that scenes opened up in 2.5 get automatically fixed.</span></span>

<span data-ttu-id="1e25b-250">未來的版本將移除與服務外觀功能相關聯的其餘程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e25b-250">The remaining code associated with the service facade feature will be removed in a future release.</span></span>

### <a name="addition-of-motion-controller-to-input-simulation-service"></a><span data-ttu-id="1e25b-251">將移動控制器新增至輸入模擬服務</span><span class="sxs-lookup"><span data-stu-id="1e25b-251">Addition of Motion Controller to Input Simulation Service</span></span>

<span data-ttu-id="1e25b-252">動畫控制器模擬現在以編輯器播放模式提供，以及現有的手模擬。</span><span class="sxs-lookup"><span data-stu-id="1e25b-252">Motion Controller simulation is now offered in editor play mode along side the existing hand simulation.</span></span> <span data-ttu-id="1e25b-253">為了啟用這項變更，許多目前的函式/欄位/屬性現在已標示為過時， `InputSimulationService.cs` 並會 `MixedRealityInputSimulationProfile.cs` 取得最重要的變更。</span><span class="sxs-lookup"><span data-stu-id="1e25b-253">To enable this change, many current functions/fields/properties are now marked obsolete, with `InputSimulationService.cs` and `MixedRealityInputSimulationProfile.cs` getting the most significant changes.</span></span> <span data-ttu-id="1e25b-254">相關程式碼的邏輯和行為大多保持不變，而大部分的過時函式與將 "手形" 的參考取代為較泛型詞彙 "controller" (例如從 `DefaultHandSimulationMode` 到 `DefaultControllerSimulationMode`) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-254">The logic and behavior of relevant code largely remain the same, and the majority of obsoleted functions etc. are related to replacing reference to "hand" to the more generic term "controller" (e.g. from `DefaultHandSimulationMode` to `DefaultControllerSimulationMode`).</span></span> <span data-ttu-id="1e25b-255">除了取得新的名稱之外，某些新函式的傳回型別也會更新，以符合名稱/行為變更 (例如 `GetControllerDevice` ，根據原始的，現在會傳回 `GetHandDevice` `BaseController` 而不是 `SimulatedHand`) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-255">Besides getting new names, the return type of certain new functions are updated to match the name/behavior change (e.g. `GetControllerDevice` based on the original `GetHandDevice` now returns `BaseController` instead of `SimulatedHand`).</span></span>

<span data-ttu-id="1e25b-256">`IInputSimulationService` 現在有新的屬性 `MotionControllerDataLeft` 和 `MotionControllerDataRight` 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-256">`IInputSimulationService` now has new properties `MotionControllerDataLeft` and `MotionControllerDataRight`.</span></span> <span data-ttu-id="1e25b-257">`MixedRealityInputSimulationProfile` 現在包含特定移動控制器按鈕之鍵盤對應的新欄位。</span><span class="sxs-lookup"><span data-stu-id="1e25b-257">`MixedRealityInputSimulationProfile` now includes new fields for the keyboard mapping of certain motion controller buttons.</span></span>

## <a name="known-issues"></a><span data-ttu-id="1e25b-258">已知問題</span><span class="sxs-lookup"><span data-stu-id="1e25b-258">Known issues</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="1e25b-259">CameraCache 可能會在關機時建立新的攝影機</span><span class="sxs-lookup"><span data-stu-id="1e25b-259">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="1e25b-260">在某些情況下 (例如在 Unity 編輯器) 中使用 LeapMotion 提供者時，CameraCache 可能會在關閉時重新建立 MainCamera。</span><span class="sxs-lookup"><span data-stu-id="1e25b-260">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="1e25b-261">如需詳細資訊，請參閱 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-261">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="1e25b-262">FileNotFoundException 透過 Unity 匯入範例的時機封裝管理員</span><span class="sxs-lookup"><span data-stu-id="1e25b-262">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="1e25b-263">視專案路徑的長度而定，透過 Unity 匯入範例封裝管理員可能會在 Unity 主控台中產生 FileNotFoundException 訊息。</span><span class="sxs-lookup"><span data-stu-id="1e25b-263">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="1e25b-264">造成這種情況的原因是「遺失」檔案的路徑超過 MAX_PATH (256 個字元) 。</span><span class="sxs-lookup"><span data-stu-id="1e25b-264">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="1e25b-265">若要解決此問題，請縮短專案路徑的長度。</span><span class="sxs-lookup"><span data-stu-id="1e25b-265">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="1e25b-266">未指定空間定位器。</span><span class="sxs-lookup"><span data-stu-id="1e25b-266">No spatializer was specified.</span></span> <span data-ttu-id="1e25b-267">應用程式將不支援空間音效</span><span class="sxs-lookup"><span data-stu-id="1e25b-267">The application will not support Spatial Sound</span></span>

<span data-ttu-id="1e25b-268">如果未設定音訊空間定位器，則會出現「未指定任何空間定位器」警告。</span><span class="sxs-lookup"><span data-stu-id="1e25b-268">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="1e25b-269">如果未安裝 XR 套件，則會發生這種情況，因為 Unity 包含這些套件中的 spatializers。</span><span class="sxs-lookup"><span data-stu-id="1e25b-269">This can occur if no XR package is installed, as Unity includes spatializers in these pacakges.</span></span>

<span data-ttu-id="1e25b-270">若要解決此問題，請確定：</span><span class="sxs-lookup"><span data-stu-id="1e25b-270">To resolve, please ensure that:</span></span>

- <span data-ttu-id="1e25b-271">**視窗**  > **封裝管理員** 已安裝一或多個 XR 套件</span><span class="sxs-lookup"><span data-stu-id="1e25b-271">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="1e25b-272">**混合現實工具**  >  組 **公用程式**  > **設定 Unity 專案** 並為 **音訊空間定位器** 進行選取</span><span class="sxs-lookup"><span data-stu-id="1e25b-272">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![選取音訊 Apatializer](../features/Images/ReleaseNotes/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="1e25b-274">NullReferenceException：物件參考未設定為物件的實例 (SceneTransitionService.Initialize) </span><span class="sxs-lookup"><span data-stu-id="1e25b-274">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="1e25b-275">在某些情況下，開啟 `EyeTrackingDemo-00-RootScene` 可能會在 SceneTransitionService 類別的 Initialize 方法中造成 NullReferenceException。</span><span class="sxs-lookup"><span data-stu-id="1e25b-275">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="1e25b-276">此錯誤是因為未設定場景轉換服務的設定檔。</span><span class="sxs-lookup"><span data-stu-id="1e25b-276">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="1e25b-277">若要解決此問題，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1e25b-277">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="1e25b-278">流覽至階層 `MixedRealityToolkit` 中的物件</span><span class="sxs-lookup"><span data-stu-id="1e25b-278">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="1e25b-279">在 [偵測器] 視窗中，選取 `Extensions`</span><span class="sxs-lookup"><span data-stu-id="1e25b-279">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="1e25b-280">如果未展開，請展開 `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="1e25b-280">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="1e25b-281">將的值設定 `Configuration Profile` 為 **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="1e25b-281">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

<img src="../features/Images/ReleaseNotes/FixSceneTransitionProfile.png" width="500px" alt="Fix scene transition">

### <a name="oculus-quest"></a><span data-ttu-id="1e25b-282">Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="1e25b-282">Oculus Quest</span></span>

<span data-ttu-id="1e25b-283">目前在 [以獨立平臺為目標時，使用 OCULUS XR 外掛程式](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)的已知問題。</span><span class="sxs-lookup"><span data-stu-id="1e25b-283">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span>  <span data-ttu-id="1e25b-284">查看 Oculus bug 追蹤程式/論壇/版本資訊以取得更新。</span><span class="sxs-lookup"><span data-stu-id="1e25b-284">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="1e25b-285">Bug 會以這一組3個錯誤表示：</span><span class="sxs-lookup"><span data-stu-id="1e25b-285">The bug is signified with this set of 3 errors:</span></span>

![Oculus XR 外掛程式錯誤](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="1e25b-287">UnityUI 和 TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="1e25b-287">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="1e25b-288">較新版本的 TextMeshPro 有一個已知問題 (1.5.0 + 或 2.1.1 +) ，其中下拉式清單和粗體字字元間距的預設字型大小已改變。</span><span class="sxs-lookup"><span data-stu-id="1e25b-288">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![TMP 映射](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="1e25b-290">這可以透過降級至舊版的 TextMeshPro 來解決。</span><span class="sxs-lookup"><span data-stu-id="1e25b-290">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="1e25b-291">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span><span class="sxs-lookup"><span data-stu-id="1e25b-291">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
