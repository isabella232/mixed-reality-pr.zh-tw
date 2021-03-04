---
title: InputSimulationServices
description: MRTK 中輸入模擬服務的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 8b11fbbaba30b6ba1126bc1e09a1ea5a277b1a1c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781231"
---
# <a name="input-simulation-service"></a><span data-ttu-id="23b18-104">輸入模擬服務</span><span class="sxs-lookup"><span data-stu-id="23b18-104">Input simulation service</span></span>

<span data-ttu-id="23b18-105">輸入模擬服務會模擬可能無法在 Unity 編輯器中使用的裝置和平臺行為。</span><span class="sxs-lookup"><span data-stu-id="23b18-105">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="23b18-106">範例包括：</span><span class="sxs-lookup"><span data-stu-id="23b18-106">Examples include:</span></span>

* <span data-ttu-id="23b18-107">HoloLens 或 VR 裝置標頭追蹤</span><span class="sxs-lookup"><span data-stu-id="23b18-107">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="23b18-108">HoloLens 手勢</span><span class="sxs-lookup"><span data-stu-id="23b18-108">HoloLens hand gestures</span></span>
* <span data-ttu-id="23b18-109">HoloLens 2 已明確追蹤</span><span class="sxs-lookup"><span data-stu-id="23b18-109">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="23b18-110">HoloLens 2 目視追蹤</span><span class="sxs-lookup"><span data-stu-id="23b18-110">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="23b18-111">VR 裝置控制器</span><span class="sxs-lookup"><span data-stu-id="23b18-111">VR device controllers</span></span>

<span data-ttu-id="23b18-112">使用者可以在執行時間使用傳統鍵盤和滑鼠組合來控制模擬的裝置。</span><span class="sxs-lookup"><span data-stu-id="23b18-112">Users can use a conventional keyboard and mouse combination to control simulated devices at runtime.</span></span> <span data-ttu-id="23b18-113">這種方法可讓您在 Unity 編輯器中測試互動，而不需要先部署到裝置。</span><span class="sxs-lookup"><span data-stu-id="23b18-113">This approach allows testing of interactions in the Unity editor without first deploying to a device.</span></span>

> [!WARNING]
> <span data-ttu-id="23b18-114">使用 Unity 的 XR 全像 > 模擬模式 = 「在編輯器中模擬」時，這無法運作。</span><span class="sxs-lookup"><span data-stu-id="23b18-114">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="23b18-115">Unity 的編輯器內模擬將從 MRTK 的輸入模擬中取得控制權。</span><span class="sxs-lookup"><span data-stu-id="23b18-115">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="23b18-116">若要使用 MRTK 輸入模擬服務，您必須將 XR 全像模擬模式設定為模擬模式 = *"None"*</span><span class="sxs-lookup"><span data-stu-id="23b18-116">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="23b18-117">啟用輸入模擬服務</span><span class="sxs-lookup"><span data-stu-id="23b18-117">Enabling the input simulation service</span></span>

<span data-ttu-id="23b18-118">在 MRTK 隨附的設定檔中，預設會啟用輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="23b18-118">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span>

<span data-ttu-id="23b18-119">但輸入模擬是選擇性的 [混合現實服務](../../architecture/MixedRealityServices.md) ，而且可以在 [輸入系統設定檔](../input/InputProviders.md)中移除為數據提供者。</span><span class="sxs-lookup"><span data-stu-id="23b18-119">Input simulation is an optional [Mixed Reality service](../../architecture/MixedRealityServices.md) though and can be removed as a data provider in the [Input System profile](../input/InputProviders.md).</span></span>

<span data-ttu-id="23b18-120">在輸入系統資料提供者設定下，可以使用下列設定輸入模擬服務。</span><span class="sxs-lookup"><span data-stu-id="23b18-120">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="23b18-121">**類型** 必須是 *MixedReality。輸入 > InputSimulationService*。</span><span class="sxs-lookup"><span data-stu-id="23b18-121">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="23b18-122">根據預設，**支援的平臺 (s)** 包含所有 *編輯器* 平臺，因為服務使用鍵盤和滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="23b18-122">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="23b18-123">輸入模擬服務可用於其他平臺端點（例如獨立式），方法是變更 **支援的平臺 (s)** 屬性，以包含所需的目標。</span><span class="sxs-lookup"><span data-stu-id="23b18-123">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <span data-ttu-id="23b18-124">![輸入模擬支援的平臺](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span><span class="sxs-lookup"><span data-stu-id="23b18-124">![Input Simulation Supported Platforms](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="23b18-125">輸入模擬工具視窗</span><span class="sxs-lookup"><span data-stu-id="23b18-125">Input simulation tools window</span></span>

<span data-ttu-id="23b18-126">從 **混合現實** 工具組  >  **公用程式**  >  **輸入模擬** 功能表啟用輸入模擬工具視窗。</span><span class="sxs-lookup"><span data-stu-id="23b18-126">Enable the input simulation tools window from the  **Mixed Reality Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="23b18-127">此視窗可讓您存取在播放模式期間的輸入模擬狀態。</span><span class="sxs-lookup"><span data-stu-id="23b18-127">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons"></a><span data-ttu-id="23b18-128">視口按鈕</span><span class="sxs-lookup"><span data-stu-id="23b18-128">Viewport buttons</span></span>

<span data-ttu-id="23b18-129">在 [指標] **預製專案** 下的輸入模擬設定檔中，可以指定用於控制基本放置之編輯器中按鈕的預製專案。</span><span class="sxs-lookup"><span data-stu-id="23b18-129">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="23b18-130">這是選擇性的公用程式，可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中存取相同的功能。</span><span class="sxs-lookup"><span data-stu-id="23b18-130">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="23b18-131">依預設會停用視口指標，因為它們目前有時可能會干擾 Unity UI 互動。</span><span class="sxs-lookup"><span data-stu-id="23b18-131">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="23b18-132">請參閱問題 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)。</span><span class="sxs-lookup"><span data-stu-id="23b18-132">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="23b18-133">若要啟用，請將 InputSimulationIndicators 預製專案新增至指標 **預製專案**。</span><span class="sxs-lookup"><span data-stu-id="23b18-133">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="23b18-134">手圖示會顯示模擬手的狀態：</span><span class="sxs-lookup"><span data-stu-id="23b18-134">Hand icons show the state of the simulated hands:</span></span>

* ![未追蹤的手圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="23b18-136">手中沒有追蹤。</span><span class="sxs-lookup"><span data-stu-id="23b18-136">The hand is not tracking.</span></span> <span data-ttu-id="23b18-137">按一下以啟用手。</span><span class="sxs-lookup"><span data-stu-id="23b18-137">Click to enable the hand.</span></span>
* <span data-ttu-id="23b18-138">![追蹤的手形圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "追蹤的手形圖示") 這會受到追蹤，但不是由使用者控制。</span><span class="sxs-lookup"><span data-stu-id="23b18-138">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="23b18-139">按一下以隱藏手。</span><span class="sxs-lookup"><span data-stu-id="23b18-139">Click to hide the hand.</span></span>
* <span data-ttu-id="23b18-140">![控制的手圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "控制的手圖示") 手由使用者追蹤及控制。</span><span class="sxs-lookup"><span data-stu-id="23b18-140">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="23b18-141">按一下以隱藏手。</span><span class="sxs-lookup"><span data-stu-id="23b18-141">Click to hide the hand.</span></span>
* <span data-ttu-id="23b18-142">![重設手形圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "重設手形圖示") 按一下可將手重設為預設位置。</span><span class="sxs-lookup"><span data-stu-id="23b18-142">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="23b18-143">在編輯器中輸入模擬功能提要</span><span class="sxs-lookup"><span data-stu-id="23b18-143">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="23b18-144">在 HandInteractionExamples 場景中按左 Ctrl + H，以顯示具有輸入模擬控制項的提要表。</span><span class="sxs-lookup"><span data-stu-id="23b18-144">Press Left Ctrl + H in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

![輸入模擬功能提要](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

## <a name="camera-control"></a><span data-ttu-id="23b18-146">攝影機控制項</span><span class="sxs-lookup"><span data-stu-id="23b18-146">Camera control</span></span>

<span data-ttu-id="23b18-147">輸入模擬服務可以模擬前端移動。</span><span class="sxs-lookup"><span data-stu-id="23b18-147">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="23b18-148">旋轉相機</span><span class="sxs-lookup"><span data-stu-id="23b18-148">Rotating the camera</span></span>

1. <span data-ttu-id="23b18-149">將滑鼠停留在 [視口編輯器] 視窗上。</span><span class="sxs-lookup"><span data-stu-id="23b18-149">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="23b18-150">*如果按鈕按下無法運作，您可能需要按一下視窗，以提供它的輸入焦點。*</span><span class="sxs-lookup"><span data-stu-id="23b18-150">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="23b18-151">按住 **滑鼠 [搜尋] 按鈕** (預設：) 滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="23b18-151">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="23b18-152">將滑鼠移至 [區] 視窗以旋轉相機。</span><span class="sxs-lookup"><span data-stu-id="23b18-152">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="23b18-153">使用滾輪來圍繞視圖方向來旋轉相機。</span><span class="sxs-lookup"><span data-stu-id="23b18-153">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="23b18-154">您可以藉由變更輸入模擬設定檔中的 **滑鼠外觀速度** 設定，來設定相機旋轉速度。</span><span class="sxs-lookup"><span data-stu-id="23b18-154">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="23b18-155">或者，您也可以使用 [**外觀水準** / **外觀垂直** 軸]，將相機 (預設：遊戲控制器的右操縱杆) 。</span><span class="sxs-lookup"><span data-stu-id="23b18-155">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="23b18-156">移動相機</span><span class="sxs-lookup"><span data-stu-id="23b18-156">Moving the camera</span></span>

<span data-ttu-id="23b18-157">使用 **移動水準** / **移動垂直** 軸將相機移動 (預設： WASD 鍵或遊戲控制器離開操縱杆) 。</span><span class="sxs-lookup"><span data-stu-id="23b18-157">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="23b18-158">您也可以在 [工具] 視窗中明確設定相機位置和旋轉角度。</span><span class="sxs-lookup"><span data-stu-id="23b18-158">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="23b18-159">您可以使用 [ **重設** ] 按鈕，將相機重設為其預設值。</span><span class="sxs-lookup"><span data-stu-id="23b18-159">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

## <a name="controller-simulation"></a><span data-ttu-id="23b18-160">控制器模擬</span><span class="sxs-lookup"><span data-stu-id="23b18-160">Controller simulation</span></span>

<span data-ttu-id="23b18-161">輸入模擬支援模擬控制器裝置 (亦即移動控制器和手) 。</span><span class="sxs-lookup"><span data-stu-id="23b18-161">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="23b18-162">這些虛擬控制器可以與任何支援一般控制器的物件互動，例如按鈕或 grabbable 物件。</span><span class="sxs-lookup"><span data-stu-id="23b18-162">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="23b18-163">控制器模擬模式</span><span class="sxs-lookup"><span data-stu-id="23b18-163">Controller simulation mode</span></span>

<span data-ttu-id="23b18-164">在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中， **預設控制器模擬模式** 設定會在三個不同的輸入模型之間切換。</span><span class="sxs-lookup"><span data-stu-id="23b18-164">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="23b18-165">您也可以在輸入模擬設定檔中設定此預設模式。</span><span class="sxs-lookup"><span data-stu-id="23b18-165">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="23b18-166">明確表達的 *手：模擬* 具有聯合位置資料的全向裝置。</span><span class="sxs-lookup"><span data-stu-id="23b18-166">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="23b18-167">模擬 HoloLens 2 互動模型。</span><span class="sxs-lookup"><span data-stu-id="23b18-167">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="23b18-168">以確切定位或使用觸控為依據的互動，可在此模式中模擬。</span><span class="sxs-lookup"><span data-stu-id="23b18-168">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="23b18-169">*手手勢*：利用點擊和基本手勢模擬簡化的模型。</span><span class="sxs-lookup"><span data-stu-id="23b18-169">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="23b18-170">模擬 [HoloLens 互動模型](https://docs.microsoft.com/windows/mixed-reality/gestures)。</span><span class="sxs-lookup"><span data-stu-id="23b18-170">Emulates [HoloLens interaction model](https://docs.microsoft.com/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="23b18-171">焦點是使用注視指標來控制。</span><span class="sxs-lookup"><span data-stu-id="23b18-171">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="23b18-172">「 *攻* 點」手勢用來與按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="23b18-172">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="23b18-173">*移動控制器*：模擬與 VR 耳機搭配使用的動作控制器，其運作方式類似于與明確表達的互動。</span><span class="sxs-lookup"><span data-stu-id="23b18-173">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="23b18-174">使用控制器互動模型來模擬 VR 耳機。</span><span class="sxs-lookup"><span data-stu-id="23b18-174">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="23b18-175">觸發程式、抓取和功能表鍵是透過鍵盤和滑鼠輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="23b18-175">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="23b18-176">模擬控制器移動</span><span class="sxs-lookup"><span data-stu-id="23b18-176">Simulating controller movement</span></span>

<span data-ttu-id="23b18-177">按住 **左/靠右控制器操作金鑰** (預設：左方控制器的 *左移位* 和右邊控制器的 *空間*) ，以取得任一控制器的控制權。</span><span class="sxs-lookup"><span data-stu-id="23b18-177">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="23b18-178">當按下操作按鍵時，控制器將會出現在 [功能區] 中。</span><span class="sxs-lookup"><span data-stu-id="23b18-178">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="23b18-179">一旦釋放操作金鑰之後，控制器會在短暫的 **控制器隱藏 Timeout** 之後消失。</span><span class="sxs-lookup"><span data-stu-id="23b18-179">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="23b18-180">您可以透過 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中的相機來切換和凍結控制器，或按下 **切換左/向右控制器鍵** (預設值： *T* 代表左邊， *Y* 表示右邊的) 。</span><span class="sxs-lookup"><span data-stu-id="23b18-180">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="23b18-181">再按一次切換鍵，再次隱藏控制器。</span><span class="sxs-lookup"><span data-stu-id="23b18-181">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="23b18-182">若要操控控制器，必須保留 **左/右控制器操作金鑰** 。</span><span class="sxs-lookup"><span data-stu-id="23b18-182">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="23b18-183">按兩下 **Left/Right 控制器操作金鑰** 也可以開啟/關閉控制器。</span><span class="sxs-lookup"><span data-stu-id="23b18-183">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="23b18-184">滑鼠移動會將控制器移至 [視圖] 平面。</span><span class="sxs-lookup"><span data-stu-id="23b18-184">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="23b18-185">您可以使用 **滑鼠滾輪**，更進一步或更接近相機來移動控制器。</span><span class="sxs-lookup"><span data-stu-id="23b18-185">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="23b18-186">若要使用滑鼠旋轉控制器，請將 **左/右控制器操作金鑰** (*左移* 或 *空格*) *，然後* 將 **控制器旋轉按鈕** (預設： *左方 Ctrl* 按鈕) ，然後移動滑鼠以旋轉控制器。</span><span class="sxs-lookup"><span data-stu-id="23b18-186">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="23b18-187">您可以藉由變更輸入模擬設定檔中的 **滑鼠控制器旋轉速度** 設定，來設定控制器旋轉速度。</span><span class="sxs-lookup"><span data-stu-id="23b18-187">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="23b18-188">所有放置也都可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中變更，包括重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="23b18-188">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="23b18-189">其他設定檔設定</span><span class="sxs-lookup"><span data-stu-id="23b18-189">Additional profile settings</span></span>

* <span data-ttu-id="23b18-190">**控制器深度乘數** 控制滑鼠滾輪深度移動的敏感度。</span><span class="sxs-lookup"><span data-stu-id="23b18-190">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="23b18-191">較大的數位會加速控制器縮放。</span><span class="sxs-lookup"><span data-stu-id="23b18-191">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="23b18-192">**預設控制器距離** 是來自相機的控制器初始距離。</span><span class="sxs-lookup"><span data-stu-id="23b18-192">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="23b18-193">按一下 [ **重設** ] 按鈕控制器也會將控制器放在這個距離。</span><span class="sxs-lookup"><span data-stu-id="23b18-193">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="23b18-194">**控制器抖動量** 會將隨機動作新增至控制器。</span><span class="sxs-lookup"><span data-stu-id="23b18-194">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="23b18-195">這項功能可用來模擬裝置上不正確的控制器追蹤，並確保互動適用于雜訊的輸入。</span><span class="sxs-lookup"><span data-stu-id="23b18-195">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="hand-gestures"></a><span data-ttu-id="23b18-196">手勢</span><span class="sxs-lookup"><span data-stu-id="23b18-196">Hand gestures</span></span>

<span data-ttu-id="23b18-197">捏合、抓取、刺探等手勢也可以模擬。</span><span class="sxs-lookup"><span data-stu-id="23b18-197">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="23b18-198">使用 **left/Right 控制器操作金鑰** (*左移* 或 *空格*) 來啟用手形控制</span><span class="sxs-lookup"><span data-stu-id="23b18-198">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="23b18-199">在操作時，按住滑鼠按鍵以執行手勢手勢。</span><span class="sxs-lookup"><span data-stu-id="23b18-199">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="23b18-200">您可以對應每個滑鼠按鍵，使用 *左/中/右滑鼠右鍵手勢* 設定，將手圖形轉換成不同的手勢。</span><span class="sxs-lookup"><span data-stu-id="23b18-200">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="23b18-201">當未按下任何按鈕時， *預設手勢* 是手的形狀。</span><span class="sxs-lookup"><span data-stu-id="23b18-201">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="23b18-202">縮小 *手勢是* 唯一執行「選取」動作的手勢。</span><span class="sxs-lookup"><span data-stu-id="23b18-202">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="23b18-203">單次操作</span><span class="sxs-lookup"><span data-stu-id="23b18-203">One-hand manipulation</span></span>

1. <span data-ttu-id="23b18-204">按住 **left/Right 控制器操作金鑰** (*左移* 或 *空格*) </span><span class="sxs-lookup"><span data-stu-id="23b18-204">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="23b18-205">物件上的點</span><span class="sxs-lookup"><span data-stu-id="23b18-205">Point at object</span></span>
3. <span data-ttu-id="23b18-206">按住滑鼠按鍵以縮小</span><span class="sxs-lookup"><span data-stu-id="23b18-206">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="23b18-207">使用您的滑鼠移動物件</span><span class="sxs-lookup"><span data-stu-id="23b18-207">Use your mouse to move the object</span></span>
5. <span data-ttu-id="23b18-208">放開滑鼠按鍵以停止互動</span><span class="sxs-lookup"><span data-stu-id="23b18-208">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="two-hand-manipulation"></a><span data-ttu-id="23b18-209">雙手勢操作</span><span class="sxs-lookup"><span data-stu-id="23b18-209">Two-hand manipulation</span></span>

<span data-ttu-id="23b18-210">若要同時以兩種方式操作物件，建議使用持續性手動模式。</span><span class="sxs-lookup"><span data-stu-id="23b18-210">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="23b18-211">按下切換鍵 (*T/Y*) 來切換。</span><span class="sxs-lookup"><span data-stu-id="23b18-211">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="23b18-212">一次處理一個手勢：</span><span class="sxs-lookup"><span data-stu-id="23b18-212">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="23b18-213">按住 **空格鍵** 以控制右手邊</span><span class="sxs-lookup"><span data-stu-id="23b18-213">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="23b18-214">將手移至您要抓取物件的位置</span><span class="sxs-lookup"><span data-stu-id="23b18-214">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="23b18-215">按下 **滑鼠左鍵** 可啟動 *縮小手勢。*</span><span class="sxs-lookup"><span data-stu-id="23b18-215">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="23b18-216">釋放 **空間** 可停止控制右手邊。</span><span class="sxs-lookup"><span data-stu-id="23b18-216">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="23b18-217">手將會凍結並 *鎖定到縮小手勢，* 因為它已不再被操作。</span><span class="sxs-lookup"><span data-stu-id="23b18-217">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="23b18-218">以另一種方式重複此程式，在第二個位置抓取相同的物件。</span><span class="sxs-lookup"><span data-stu-id="23b18-218">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="23b18-219">現在這兩個手都會抓取相同的物件，您可以將其中一個物件移至兩個執行中的操作。</span><span class="sxs-lookup"><span data-stu-id="23b18-219">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="23b18-220">GGV (注視、手勢和語音) 互動</span><span class="sxs-lookup"><span data-stu-id="23b18-220">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="23b18-221">根據預設，GGV 互動會在編輯器中啟用，但場景中不會有明確的手。</span><span class="sxs-lookup"><span data-stu-id="23b18-221">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="23b18-222">旋轉相機以指向互動物件上的注視游標 (滑鼠右鍵) </span><span class="sxs-lookup"><span data-stu-id="23b18-222">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="23b18-223">按一下並按住 **滑鼠** 左鍵以進行互動</span><span class="sxs-lookup"><span data-stu-id="23b18-223">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="23b18-224">再次旋轉相機以操作物件</span><span class="sxs-lookup"><span data-stu-id="23b18-224">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="23b18-225">您可以切換輸入模擬設定檔內的 [ *已啟用手動可用輸入* ] 選項來關閉此功能。</span><span class="sxs-lookup"><span data-stu-id="23b18-225">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="23b18-226">此外，您可以使用模擬的手 GGV 互動</span><span class="sxs-lookup"><span data-stu-id="23b18-226">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="23b18-227">藉由將 **手動模擬模式** 切換至 [輸入模擬設定檔](#enabling-the-input-simulation-service)中的 *手勢* 來啟用 GGV 模擬</span><span class="sxs-lookup"><span data-stu-id="23b18-227">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="23b18-228">旋轉相機以指向互動物件上的注視游標 (滑鼠右鍵) </span><span class="sxs-lookup"><span data-stu-id="23b18-228">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="23b18-229">按住 **空格鍵** 以控制右手邊</span><span class="sxs-lookup"><span data-stu-id="23b18-229">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="23b18-230">按一下並按住 **滑鼠** 左鍵以進行互動</span><span class="sxs-lookup"><span data-stu-id="23b18-230">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="23b18-231">使用您的滑鼠移動物件</span><span class="sxs-lookup"><span data-stu-id="23b18-231">Use your mouse to move the object</span></span>
1. <span data-ttu-id="23b18-232">放開滑鼠按鍵以停止互動</span><span class="sxs-lookup"><span data-stu-id="23b18-232">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="motion-controller-interaction"></a><span data-ttu-id="23b18-233">移動控制器互動</span><span class="sxs-lookup"><span data-stu-id="23b18-233">Motion controller interaction</span></span>

<span data-ttu-id="23b18-234">模擬的動作控制器可透過與明確表達的相同方式來操作。</span><span class="sxs-lookup"><span data-stu-id="23b18-234">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="23b18-235">在觸發程式、抓取和功能表鍵分別對應至 *滑鼠左鍵*、 *G* 和 *M* 鍵的情況下，互動模型與明確的手互動很類似。</span><span class="sxs-lookup"><span data-stu-id="23b18-235">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="23b18-236">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="23b18-236">Eye tracking</span></span>

<span data-ttu-id="23b18-237">您可以藉由檢查 [輸入模擬設定檔](#enabling-the-input-simulation-service)中的 [**模擬眼睛位置**] 選項來啟用 [眼睛追蹤模擬](../eye-tracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor)。</span><span class="sxs-lookup"><span data-stu-id="23b18-237">[Eye tracking simulation](../eye-tracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="23b18-238">這不應該與 GGV 或移動控制器樣式互動一起使用 (因此，請確定 **預設控制器模擬模式** 已設定為 [ *已) ]* 。</span><span class="sxs-lookup"><span data-stu-id="23b18-238">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="see-also"></a><span data-ttu-id="23b18-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23b18-239">See also</span></span>

* <span data-ttu-id="23b18-240">[輸入系統設定檔](../input/InputProviders.md)。</span><span class="sxs-lookup"><span data-stu-id="23b18-240">[Input System profile](../input/InputProviders.md).</span></span>
