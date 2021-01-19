---
title: MRTK 101 - 使用一般空間互動
description: 如何使用混合實境工具組 Unity 進行 HoloLens 2、HoloLens、Windows Mixed Reality 和 Open VR 的基本互動。
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, 混合實境工具組, Windows Mixed Reality, 設計, 範例應用程式, 控制項, 混合實境頭戴式裝置, Windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.localizationpriority: high
ms.openlocfilehash: 8b9af843dc059ef4d50aa5508356c7aeed968a4e
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98248052"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="84ff3-104">MRTK 101：如何使用混合實境工具組 Unity 進行常見的空間互動</span><span class="sxs-lookup"><span data-stu-id="84ff3-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="84ff3-106">了解如何使用 MRTK 來實現混合實境中一些最廣泛使用的常見互動模式。</span><span class="sxs-lookup"><span data-stu-id="84ff3-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="84ff3-107">如何在 Unity 編輯器中模擬輸入互動？</span><span class="sxs-lookup"><span data-stu-id="84ff3-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="84ff3-108">如何抓取和移動物件？</span><span class="sxs-lookup"><span data-stu-id="84ff3-108">How to grab and move an object?</span></span>
- <span data-ttu-id="84ff3-109">如何調整物件大小？</span><span class="sxs-lookup"><span data-stu-id="84ff3-109">How to resize an object?</span></span>
- <span data-ttu-id="84ff3-110">如何精確地移動或旋轉物件？</span><span class="sxs-lookup"><span data-stu-id="84ff3-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="84ff3-111">如何讓物件回應輸入事件？</span><span class="sxs-lookup"><span data-stu-id="84ff3-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="84ff3-112">如何新增視覺回饋？</span><span class="sxs-lookup"><span data-stu-id="84ff3-112">How to add visual feedback?</span></span>
- <span data-ttu-id="84ff3-113">如何新增音訊回饋？</span><span class="sxs-lookup"><span data-stu-id="84ff3-113">How to add audio feedback?</span></span>
- <span data-ttu-id="84ff3-114">如何使用 HoloLens 2 樣式的按鈕 Prefab？</span><span class="sxs-lookup"><span data-stu-id="84ff3-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="84ff3-115">如何讓物件跟著您移動？</span><span class="sxs-lookup"><span data-stu-id="84ff3-115">How to make an object follow you?</span></span>
- <span data-ttu-id="84ff3-116">如何讓物件面對您？</span><span class="sxs-lookup"><span data-stu-id="84ff3-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="84ff3-117">本文已更新，以便反映 [MRTK v2.5.1 版本](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)中的變更</span><span class="sxs-lookup"><span data-stu-id="84ff3-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="84ff3-118">您可以在 Unity 編輯器中，使用 MRTK 的輸入模擬來測試此頁面中的所有內容。</span><span class="sxs-lookup"><span data-stu-id="84ff3-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="84ff3-119">如果您尚未這麼做，請遵循 [MRTK 安裝指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 以安裝最新版的 MRTK。</span><span class="sxs-lookup"><span data-stu-id="84ff3-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="84ff3-120">如何在 Unity 編輯器中模擬輸入互動？</span><span class="sxs-lookup"><span data-stu-id="84ff3-120">How to simulate input interactions in Unity editor?</span></span>

<span data-ttu-id="84ff3-121">MRTK 支援編輯器內的輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="84ff3-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="84ff3-122">按一下 Unity 的 [播放] 按鈕來執行場景，然後使用下列按鍵來模擬輸入：</span><span class="sxs-lookup"><span data-stu-id="84ff3-122">Run your scene by clicking Unity's play button, then use the following keys to simulate input:</span></span>
- <span data-ttu-id="84ff3-123">按 W、A、S、D 鍵來移動相機。</span><span class="sxs-lookup"><span data-stu-id="84ff3-123">Press W, A, S, D keys to move the camera.</span></span>
- <span data-ttu-id="84ff3-124">按住滑鼠右鍵並移動滑鼠來瀏覽。</span><span class="sxs-lookup"><span data-stu-id="84ff3-124">Hold the right mouse button and move the mouse to look around.</span></span>
- <span data-ttu-id="84ff3-125">按空格鍵 (右手) 或左邊的 Shift 鍵 (左手) 來帶出模擬的雙手</span><span class="sxs-lookup"><span data-stu-id="84ff3-125">Press Space bar(Right hand) or left Shift key(Left hand) to bring up the simulated hands</span></span>
- <span data-ttu-id="84ff3-126">按 T 或 Y 鍵讓模擬的雙手保持在視線內</span><span class="sxs-lookup"><span data-stu-id="84ff3-126">Press T or Y keys to keep simulated hands in view</span></span>
- <span data-ttu-id="84ff3-127">按 Q 或 E (水平)/R 或 F (垂直) 來旋轉模擬的雙手</span><span class="sxs-lookup"><span data-stu-id="84ff3-127">Press Q or E(horizontal) / R or F(vertical) to rotate simulated hands</span></span>

<span data-ttu-id="84ff3-128">您可以在 [MRTK 文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)中深入了解輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="84ff3-128">You can learn more about Input Simulation in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span></span>

## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="84ff3-129">如何抓取和移動物件？</span><span class="sxs-lookup"><span data-stu-id="84ff3-129">How to grab and move an object?</span></span>

<span data-ttu-id="84ff3-130">附加 **ObjectManipulator.cs** 和 **NearInteractionGrabbable.cs** 指令碼即可讓物件可供抓取。</span><span class="sxs-lookup"><span data-stu-id="84ff3-130">Attach the **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** scripts to make an object grabbable.</span></span> <span data-ttu-id="84ff3-131">ObjectManipulator 同時支援遠近互動。</span><span class="sxs-lookup"><span data-stu-id="84ff3-131">ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="84ff3-132">您可以使用 HoloLens 2 的接合手部追蹤輸入 (近處)、手部射線 (遠處)、運動控制器的光束 (遠處)，以及 HoloLens 注視游標和空間點選 (遠處) 來抓取和移動物件。</span><span class="sxs-lookup"><span data-stu-id="84ff3-132">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), and HoloLens gaze cursor and air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="84ff3-133">如何調整物件大小？</span><span class="sxs-lookup"><span data-stu-id="84ff3-133">How to resize an object?</span></span>
<span data-ttu-id="84ff3-134">**ObjectManipulator.cs** 支援兩手的縮放/旋轉。</span><span class="sxs-lookup"><span data-stu-id="84ff3-134">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="84ff3-135">此指令碼適用於各種輸入類型，例如 HoloLens 2 的接合手部輸入、HoloLens 1 的注視 + 手勢輸入，以及 Windows Mixed Reality 沉浸式頭戴裝置的動作控制器輸入。</span><span class="sxs-lookup"><span data-stu-id="84ff3-135">The script works with various input types, such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="84ff3-136">在 MRTK 文件中深入了解 Object Manipulator</span><span class="sxs-lookup"><span data-stu-id="84ff3-136">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="84ff3-137">如何精確地移動或旋轉物件？</span><span class="sxs-lookup"><span data-stu-id="84ff3-137">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="84ff3-138">將 **BoundsControl.cs** 指派給物件以使用周框方塊，也就是用來縮放和旋轉物件的介面。</span><span class="sxs-lookup"><span data-stu-id="84ff3-138">Assign **BoundsControl.cs** to an object to use Bounding Box, which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="84ff3-139">根據預設，其會顯示 HoloLens 1 樣式的藍色控點和連接線。</span><span class="sxs-lookup"><span data-stu-id="84ff3-139">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="84ff3-140">若要使用 HoloLens 2 樣式的鄰近動畫控點，您必須指派 Prefab 和材質。</span><span class="sxs-lookup"><span data-stu-id="84ff3-140">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="84ff3-141">在 MRTK 文件中深入了解邊界控制項</span><span class="sxs-lookup"><span data-stu-id="84ff3-141">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="84ff3-142">如何讓物件回應輸入事件？</span><span class="sxs-lookup"><span data-stu-id="84ff3-142">How to make an object respond to input events?</span></span>
<span data-ttu-id="84ff3-143">將 **PointerHandler.cs** 指派給物件。</span><span class="sxs-lookup"><span data-stu-id="84ff3-143">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="84ff3-144">在偵測器中，您可以使用 OnPointerDown()、OnPointerUp()、OnPointerClicked()、OnPointerDragged() 事件。若要在指令碼中使用這些事件，請實作 **IMixedRealityPointerHandler**。</span><span class="sxs-lookup"><span data-stu-id="84ff3-144">In the inspector, you can use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="84ff3-145">在 MRTK 文件中深入了解輸入系統</span><span class="sxs-lookup"><span data-stu-id="84ff3-145">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="84ff3-146">如何新增視覺回饋？</span><span class="sxs-lookup"><span data-stu-id="84ff3-146">How to add visual feedback?</span></span>
<span data-ttu-id="84ff3-147">將 **Interactable.cs** 指派給物件。</span><span class="sxs-lookup"><span data-stu-id="84ff3-147">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="84ff3-148">在偵測器中新增目標物件並建立新的主題。</span><span class="sxs-lookup"><span data-stu-id="84ff3-148">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="84ff3-149">您可以使用 Interactable (可互動) 的主題設定檔，輕鬆地在所有可用的輸入互動狀態中新增視覺回饋。</span><span class="sxs-lookup"><span data-stu-id="84ff3-149">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="84ff3-150">Interactable 提供各種主題類型，包括著色器主題，該主題可讓您控制每個互動狀態的著色器屬性。</span><span class="sxs-lookup"><span data-stu-id="84ff3-150">Interactable provides various types of themes including the shader theme, which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="84ff3-151">在 MRTK 文件中深入了解 Interactable</span><span class="sxs-lookup"><span data-stu-id="84ff3-151">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="84ff3-152">視覺化回饋的另一個重要組成要素是 **MRTK 標準著色器**。</span><span class="sxs-lookup"><span data-stu-id="84ff3-152">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="84ff3-153">透過 MRTK 標準著色器，您可以輕鬆地加入視覺回饋效果，例如暫留光源和鄰近光源。</span><span class="sxs-lookup"><span data-stu-id="84ff3-153">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="84ff3-154">由於 MRTK 標準著色器執行的計算比 Unity 標準著色器少，因此可讓您建立高效能的體驗。</span><span class="sxs-lookup"><span data-stu-id="84ff3-154">Since MRTK Standard shader performs less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="84ff3-155">建立新的材質，然後選取著色器的 [混合實境工具組] > [標準]。</span><span class="sxs-lookup"><span data-stu-id="84ff3-155">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="84ff3-156">或者，您可以挑選其中一個使用 MRTK 標準著色器的現有材質。</span><span class="sxs-lookup"><span data-stu-id="84ff3-156">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="84ff3-157">在 MRTK 文件中深入了解 MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="84ff3-157">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="84ff3-158">如何新增音訊回饋？</span><span class="sxs-lookup"><span data-stu-id="84ff3-158">How to add audio feedback?</span></span>
<span data-ttu-id="84ff3-159">將 **AudioSource** 新增至物件。</span><span class="sxs-lookup"><span data-stu-id="84ff3-159">Add **AudioSource** to an object.</span></span> <span data-ttu-id="84ff3-160">然後，在公開輸入事件 (例如 Interactable.cs 或 PointerHandler.cs) 的指令碼中，將具有 AudioSource 的物件指派給事件，然後選取 [AudioSource.PlayOneShot()]。</span><span class="sxs-lookup"><span data-stu-id="84ff3-160">Then, in the scripts that expose input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="84ff3-161">您可以使用您的音訊片段，或從 MRTK 的音訊資產中選擇一個。</span><span class="sxs-lookup"><span data-stu-id="84ff3-161">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="84ff3-162">如何使用 HoloLens 2 樣式的按鈕 Prefab？</span><span class="sxs-lookup"><span data-stu-id="84ff3-162">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="84ff3-163">MRTK 提供各種類型的 HoloLens 2 命令介面 (OS) 樣式按鈕，其中包括視覺回饋，例如鄰近光源、壓縮方塊和按鈕表面上的漣波效果，可改善使用者的信賴度。</span><span class="sxs-lookup"><span data-stu-id="84ff3-163">MRTK provides various types of HoloLens 2's shell (OS) style buttons, including visual feedback like proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="84ff3-164">將其中一個 **HoloLens 2 樣式的可點按按鈕 Prefab** 拖放到您的場景中即可。</span><span class="sxs-lookup"><span data-stu-id="84ff3-164">Drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="84ff3-165">Prefab 會使用上方介紹的 Interactable.cs。</span><span class="sxs-lookup"><span data-stu-id="84ff3-165">The prefab uses Interactable.cs introduced above.</span></span> <span data-ttu-id="84ff3-166">您可以在 Interactable 中使用公開的事件 例如 (OnClick()) 來觸發動作。</span><span class="sxs-lookup"><span data-stu-id="84ff3-166">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="84ff3-167">在 MRTK 文件中深入了解按鈕 Prefab</span><span class="sxs-lookup"><span data-stu-id="84ff3-167">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="84ff3-168">如何讓物件跟著您移動？</span><span class="sxs-lookup"><span data-stu-id="84ff3-168">How to make an object follow you?</span></span>
<span data-ttu-id="84ff3-169">將 **RadialView.cs** 或 **Follow.cs** 指令碼指派給物件。</span><span class="sxs-lookup"><span data-stu-id="84ff3-169">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="84ff3-170">這是 Solver (解算器) 指令碼系列的一部分，可讓您在 3D 空間中實現各種物件類型的定位。</span><span class="sxs-lookup"><span data-stu-id="84ff3-170">It's part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="84ff3-171">**SolverHandler.cs** 將會自動新增。</span><span class="sxs-lookup"><span data-stu-id="84ff3-171">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="84ff3-172">以下是使用 RadialView 設定達到 'lazy follow' 常駐標籤行為的範例，就像是 HoloLens 命令介面中的 [開始] 功能表。</span><span class="sxs-lookup"><span data-stu-id="84ff3-172">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="84ff3-173">您可以指定最小/最大距離和最小/最大檢視角度。</span><span class="sxs-lookup"><span data-stu-id="84ff3-173">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="84ff3-174">下列範例顯示物件在 0.4 m 和 0.8 m 範圍之間的 15° 檢視。</span><span class="sxs-lookup"><span data-stu-id="84ff3-174">The example below shows positioning the object between 0.4 m and 0.8-m range within 15°.</span></span> <span data-ttu-id="84ff3-175">調整 Lerp 時間值，讓位置更新的速度更快或更慢。</span><span class="sxs-lookup"><span data-stu-id="84ff3-175">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="84ff3-176">在 MRTK 文件中深入了解 Solver</span><span class="sxs-lookup"><span data-stu-id="84ff3-176">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="84ff3-177">如何讓物件面對您？</span><span class="sxs-lookup"><span data-stu-id="84ff3-177">How to make an object face you?</span></span>
<span data-ttu-id="84ff3-178">將 **Billboard.cs** 指令碼指派給物件。</span><span class="sxs-lookup"><span data-stu-id="84ff3-178">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="84ff3-179">無論您的位置在哪，物件都會面對您。</span><span class="sxs-lookup"><span data-stu-id="84ff3-179">It will always face you, whatever your position.</span></span> <span data-ttu-id="84ff3-180">您可以指定樞紐軸選項。</span><span class="sxs-lookup"><span data-stu-id="84ff3-180">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="84ff3-181">準備好建立混合實境的絕佳體驗了嗎？</span><span class="sxs-lookup"><span data-stu-id="84ff3-181">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="84ff3-182">請瀏覽下列頁面，並深入了解 MRTK 和混合實境。</span><span class="sxs-lookup"><span data-stu-id="84ff3-182">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="84ff3-183">關於作者</span><span class="sxs-lookup"><span data-stu-id="84ff3-183">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="84ff3-184"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="84ff3-184"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="84ff3-185">UX 設計者 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="84ff3-185">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="84ff3-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84ff3-186">See also</span></span>
* [<span data-ttu-id="84ff3-187">MRTK 安裝指南 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="84ff3-187">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="84ff3-188">混合實境工具組-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="84ff3-188">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="84ff3-189">MRTK 文件入口網站 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="84ff3-189">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="84ff3-190">HoloToolkit 至 MRTK 的移植指導方針</span><span class="sxs-lookup"><span data-stu-id="84ff3-190">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
