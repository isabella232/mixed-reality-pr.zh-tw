---
title: InputSimulationServices
description: MRTK 中輸入模擬服務的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 7048be35a14dfd1c9c94c388119f1b7037ec3da1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688838"
---
# <a name="input-simulation-service"></a><span data-ttu-id="263be-104">輸入模擬服務</span><span class="sxs-lookup"><span data-stu-id="263be-104">Input simulation service</span></span>

<span data-ttu-id="263be-105">輸入模擬服務會模擬可能無法在 Unity 編輯器中使用的裝置和平臺行為。</span><span class="sxs-lookup"><span data-stu-id="263be-105">The Input Simulation Service emulates the behaviour of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="263be-106">範例包括：</span><span class="sxs-lookup"><span data-stu-id="263be-106">Examples include:</span></span>

* <span data-ttu-id="263be-107">HoloLens 或 VR 裝置標頭追蹤</span><span class="sxs-lookup"><span data-stu-id="263be-107">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="263be-108">HoloLens 手勢</span><span class="sxs-lookup"><span data-stu-id="263be-108">HoloLens hand gestures</span></span>
* <span data-ttu-id="263be-109">HoloLens 2 明確的手追蹤</span><span class="sxs-lookup"><span data-stu-id="263be-109">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="263be-110">HoloLens 2 眼追蹤</span><span class="sxs-lookup"><span data-stu-id="263be-110">HoloLens 2 eye tracking</span></span>

<span data-ttu-id="263be-111">使用者可以在執行時間使用傳統鍵盤和滑鼠組合來控制模擬的裝置。</span><span class="sxs-lookup"><span data-stu-id="263be-111">Users can use a conventional keyboard and mouse combination to control simulated devices at runtime.</span></span> <span data-ttu-id="263be-112">這種方法可讓您在 Unity 編輯器中測試互動，而不需要先部署到裝置。</span><span class="sxs-lookup"><span data-stu-id="263be-112">This approach allows testing of interactions in the Unity editor without first deploying to a device.</span></span>

> [!WARNING]
> <span data-ttu-id="263be-113">使用 Unity 的 XR 全像 > 模擬模式 = 「在編輯器中模擬」時，這無法運作。</span><span class="sxs-lookup"><span data-stu-id="263be-113">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="263be-114">Unity 的編輯器內模擬將從 MRTK 的輸入模擬中取得控制權。</span><span class="sxs-lookup"><span data-stu-id="263be-114">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="263be-115">若要使用 MRTK 輸入模擬服務，您必須將 XR 全像模擬模式設定為模擬模式 = *"None"*</span><span class="sxs-lookup"><span data-stu-id="263be-115">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="263be-116">啟用輸入模擬服務</span><span class="sxs-lookup"><span data-stu-id="263be-116">Enabling the input simulation service</span></span>

<span data-ttu-id="263be-117">在 MRTK 隨附的設定檔中，預設會啟用輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="263be-117">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span>

<span data-ttu-id="263be-118">但輸入模擬是選擇性的 [混合現實服務](../../out-of-scope/MixedRealityServices.md) ，而且可以在 [輸入系統設定檔](../Input/InputProviders.md)中移除為數據提供者。</span><span class="sxs-lookup"><span data-stu-id="263be-118">Input simulation is an optional [Mixed Reality service](../../out-of-scope/MixedRealityServices.md) though and can be removed as a data provider in the [Input System profile](../Input/InputProviders.md).</span></span>

<span data-ttu-id="263be-119">在輸入系統資料提供者設定下，可以使用下列設定輸入模擬服務。</span><span class="sxs-lookup"><span data-stu-id="263be-119">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="263be-120">**類型** 必須是 *MixedReality。輸入 > InputSimulationService*。</span><span class="sxs-lookup"><span data-stu-id="263be-120">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="263be-121">根據預設，**支援的平臺 (s)** 包含所有 *編輯器* 平臺，因為服務使用鍵盤和滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="263be-121">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="263be-122">輸入模擬服務可用於其他平臺端點（例如獨立式），方法是變更 **支援的平臺 (s)** 屬性，以包含所需的目標。</span><span class="sxs-lookup"><span data-stu-id="263be-122">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <span data-ttu-id="263be-123">![輸入模擬支援的平臺](../Images/InputSimulation/InputSimulationSupportedPlatforms.gif)</span><span class="sxs-lookup"><span data-stu-id="263be-123">![Input Simulation Supported Platforms](../Images/InputSimulation/InputSimulationSupportedPlatforms.gif)</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="263be-124">輸入模擬工具視窗</span><span class="sxs-lookup"><span data-stu-id="263be-124">Input simulation tools window</span></span>

<span data-ttu-id="263be-125">從 **混合現實** 工具組  >  **公用程式**  >  **輸入模擬** 功能表啟用輸入模擬工具視窗。</span><span class="sxs-lookup"><span data-stu-id="263be-125">Enable the input simulation tools window from the  **Mixed Reality Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="263be-126">此視窗可讓您存取在播放模式期間的輸入模擬狀態。</span><span class="sxs-lookup"><span data-stu-id="263be-126">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons"></a><span data-ttu-id="263be-127">視口按鈕</span><span class="sxs-lookup"><span data-stu-id="263be-127">Viewport buttons</span></span>

<span data-ttu-id="263be-128">在 [指標] **預製專案** 下的輸入模擬設定檔中，可以指定用於控制基本放置之編輯器中按鈕的預製專案。</span><span class="sxs-lookup"><span data-stu-id="263be-128">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="263be-129">這是選擇性的公用程式，可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中存取相同的功能。</span><span class="sxs-lookup"><span data-stu-id="263be-129">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="263be-130">依預設會停用視口指標，因為它們目前有時可能會干擾 Unity UI 互動。</span><span class="sxs-lookup"><span data-stu-id="263be-130">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="263be-131">請參閱問題 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)。</span><span class="sxs-lookup"><span data-stu-id="263be-131">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="263be-132">若要啟用，請將 InputSimulationIndicators 預製專案新增至指標 **預製專案**。</span><span class="sxs-lookup"><span data-stu-id="263be-132">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="263be-133">手圖示會顯示模擬手的狀態：</span><span class="sxs-lookup"><span data-stu-id="263be-133">Hand icons show the state of the simulated hands:</span></span>

* ![未追蹤的手圖示](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="263be-135">手中沒有追蹤。</span><span class="sxs-lookup"><span data-stu-id="263be-135">The hand is not tracking.</span></span> <span data-ttu-id="263be-136">按一下以啟用手。</span><span class="sxs-lookup"><span data-stu-id="263be-136">Click to enable the hand.</span></span>
* <span data-ttu-id="263be-137">![追蹤的手形圖示](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Tracked.png "追蹤的手形圖示") 這會受到追蹤，但不是由使用者控制。</span><span class="sxs-lookup"><span data-stu-id="263be-137">![Tracked hand icon](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="263be-138">按一下以隱藏手。</span><span class="sxs-lookup"><span data-stu-id="263be-138">Click to hide the hand.</span></span>
* <span data-ttu-id="263be-139">![控制的手圖示](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Controlled.png "控制的手圖示") 手由使用者追蹤及控制。</span><span class="sxs-lookup"><span data-stu-id="263be-139">![Controlled hand icon](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="263be-140">按一下以隱藏手。</span><span class="sxs-lookup"><span data-stu-id="263be-140">Click to hide the hand.</span></span>
* <span data-ttu-id="263be-141">![重設手形圖示](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Reset.png "重設手形圖示") 按一下可將手重設為預設位置。</span><span class="sxs-lookup"><span data-stu-id="263be-141">![Reset hand icon](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>

## <a name="camera-control"></a><span data-ttu-id="263be-142">攝影機控制項</span><span class="sxs-lookup"><span data-stu-id="263be-142">Camera control</span></span>

<span data-ttu-id="263be-143">輸入模擬服務可以模擬前端移動。</span><span class="sxs-lookup"><span data-stu-id="263be-143">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="263be-144">旋轉相機</span><span class="sxs-lookup"><span data-stu-id="263be-144">Rotating the camera</span></span>

1. <span data-ttu-id="263be-145">將滑鼠停留在 [視口編輯器] 視窗上。</span><span class="sxs-lookup"><span data-stu-id="263be-145">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="263be-146">*如果按鈕按下無法運作，您可能需要按一下視窗，以提供它的輸入焦點。*</span><span class="sxs-lookup"><span data-stu-id="263be-146">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="263be-147">按住 **滑鼠 [搜尋] 按鈕** (預設：) 滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="263be-147">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="263be-148">將滑鼠移至 [區] 視窗以旋轉相機。</span><span class="sxs-lookup"><span data-stu-id="263be-148">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="263be-149">使用滾輪來圍繞視圖方向來旋轉相機。</span><span class="sxs-lookup"><span data-stu-id="263be-149">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="263be-150">您可以藉由變更輸入模擬設定檔中的 **滑鼠外觀速度** 設定，來設定相機旋轉速度。</span><span class="sxs-lookup"><span data-stu-id="263be-150">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="263be-151">或者，您也可以使用 [**外觀水準** / **外觀垂直** 軸]，將相機 (預設：遊戲控制器的右操縱杆) 。</span><span class="sxs-lookup"><span data-stu-id="263be-151">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="263be-152">移動相機</span><span class="sxs-lookup"><span data-stu-id="263be-152">Moving the camera</span></span>

<span data-ttu-id="263be-153">使用 **移動水準** / **移動垂直** 軸將相機移動 (預設： WASD 鍵或遊戲控制器離開操縱杆) 。</span><span class="sxs-lookup"><span data-stu-id="263be-153">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="263be-154">您也可以在 [工具] 視窗中明確設定相機位置和旋轉角度。</span><span class="sxs-lookup"><span data-stu-id="263be-154">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="263be-155">您可以使用 [ **重設** ] 按鈕，將相機重設為其預設值。</span><span class="sxs-lookup"><span data-stu-id="263be-155">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

## <a name="hand-simulation"></a><span data-ttu-id="263be-156">手上模擬</span><span class="sxs-lookup"><span data-stu-id="263be-156">Hand simulation</span></span>

<span data-ttu-id="263be-157">輸入模擬支援模擬的裝置。</span><span class="sxs-lookup"><span data-stu-id="263be-157">The input simulation supports emulated hand devices.</span></span> <span data-ttu-id="263be-158">這些虛擬手可以與任何支援一般裝置的物件互動，例如按鈕或 grabbable 物件。</span><span class="sxs-lookup"><span data-stu-id="263be-158">These virtual hands can interact with any object that supports regular hand devices, such as buttons or grabbable objects.</span></span>

### <a name="hand-simulation-mode"></a><span data-ttu-id="263be-159">手動模擬模式</span><span class="sxs-lookup"><span data-stu-id="263be-159">Hand simulation mode</span></span>

<span data-ttu-id="263be-160">在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中，[ **手動模擬模式** ] 設定會在兩個不同的輸入模型之間切換。</span><span class="sxs-lookup"><span data-stu-id="263be-160">In the [input simulation tools window](#input-simulation-tools-window) the **Hand Simulation Mode** setting switches between two distinct input models.</span></span> <span data-ttu-id="263be-161">您也可以在輸入模擬設定檔中設定預設模式。</span><span class="sxs-lookup"><span data-stu-id="263be-161">The default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="263be-162">明確表達的 *手：模擬* 具有聯合位置資料的全向裝置。</span><span class="sxs-lookup"><span data-stu-id="263be-162">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="263be-163">模擬 HoloLens 2 互動模型。</span><span class="sxs-lookup"><span data-stu-id="263be-163">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="263be-164">以確切定位或使用觸控為依據的互動，可在此模式中模擬。</span><span class="sxs-lookup"><span data-stu-id="263be-164">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="263be-165">*手勢*：利用點擊和基本手勢模擬簡化的模型。</span><span class="sxs-lookup"><span data-stu-id="263be-165">*Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="263be-166">模擬 [HoloLens 互動模型](https://docs.microsoft.com/windows/mixed-reality/gestures)。</span><span class="sxs-lookup"><span data-stu-id="263be-166">Emulates [HoloLens interaction model](https://docs.microsoft.com/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="263be-167">焦點是使用注視指標來控制。</span><span class="sxs-lookup"><span data-stu-id="263be-167">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="263be-168">「 *攻* 點」手勢用來與按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="263be-168">The *Air Tap* gesture is used to interact with buttons.</span></span>

### <a name="controlling-hand-movement"></a><span data-ttu-id="263be-169">控制手間移動</span><span class="sxs-lookup"><span data-stu-id="263be-169">Controlling hand movement</span></span>

<span data-ttu-id="263be-170">按住 **左邊/右邊的 Control 鍵** (預設：左邊的左 *移* 和右邊的 *空格*) ，以取得任一手勢的控制權。</span><span class="sxs-lookup"><span data-stu-id="263be-170">Press and hold the **Left/Right Hand Control Key** (default: *Left Shift* for left hand and *Space* for right hand) to gain control of either hand.</span></span> <span data-ttu-id="263be-171">當按下操作鍵時，該手將會出現在區中。</span><span class="sxs-lookup"><span data-stu-id="263be-171">While the manipulation key is pressed, the hand will appear in the viewport.</span></span> <span data-ttu-id="263be-172">釋放操作金鑰後，就會在短 **手隱藏 Timeout** 之後消失。</span><span class="sxs-lookup"><span data-stu-id="263be-172">Once the manipulation key is released, the hands will disappear after a short **Hand Hide Timeout**.</span></span>

<span data-ttu-id="263be-173">您可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中永久切換，或按下 **切換左/右邊鍵** (預設： *T* 代表左邊， *Y* 表示右邊的) 。</span><span class="sxs-lookup"><span data-stu-id="263be-173">Hands can be toggled on permanently in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Hand Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="263be-174">再按一次切換鍵，以再次隱藏手。</span><span class="sxs-lookup"><span data-stu-id="263be-174">Press the toggle key again to hide the hands again.</span></span>

<span data-ttu-id="263be-175">滑鼠移動會將手移至 [view] 平面。</span><span class="sxs-lookup"><span data-stu-id="263be-175">Mouse movement will move the hand in the view plane.</span></span> <span data-ttu-id="263be-176">您可以使用 **滑鼠滾輪**，更進一步或更靠近相機移動手。</span><span class="sxs-lookup"><span data-stu-id="263be-176">Hands can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="263be-177">若要使用滑鼠旋轉手，請將 **左/右邊的控制項按鍵** (*左移* 或 *空格*) *，然後* 將滑鼠 **旋轉按鈕** (預設值： *ctrl* 鍵) 然後移動滑鼠以旋轉手。</span><span class="sxs-lookup"><span data-stu-id="263be-177">To rotate hands using the mouse, hold both the **Left/Right Hand Control Key** (*Left Shift* or *Space*) *and* the **Hand Rotate Button** (default: *ctrl* button) and then move the mouse to rotate the hand.</span></span> <span data-ttu-id="263be-178">您可以藉由變更輸入模擬設定檔中的 **滑鼠右鍵旋轉速度** 設定來設定手旋轉速度。</span><span class="sxs-lookup"><span data-stu-id="263be-178">Hand rotation speed can be configured by changing the **Mouse Hand Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="263be-179">所有放置也都可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中變更，包括重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="263be-179">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="263be-180">其他設定檔設定</span><span class="sxs-lookup"><span data-stu-id="263be-180">Additional profile settings</span></span>

* <span data-ttu-id="263be-181">**右深度乘數** 控制滑鼠滾輪深度移動的敏感度。</span><span class="sxs-lookup"><span data-stu-id="263be-181">**Hand Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="263be-182">較大的數位會加速縮放。</span><span class="sxs-lookup"><span data-stu-id="263be-182">A larger number will speed up hand zoom.</span></span>
* <span data-ttu-id="263be-183">[**預設距離**] 是從相機手上的初始距離。</span><span class="sxs-lookup"><span data-stu-id="263be-183">**Default Hand Distance** is the initial distance of hands from the camera.</span></span> <span data-ttu-id="263be-184">按一下 [ **重設** ] 按鈕也會將手放在這個距離。</span><span class="sxs-lookup"><span data-stu-id="263be-184">Clicking the **Reset** button hands will also place hands at this distance.</span></span>
* <span data-ttu-id="263be-185">**手抖動量** 會將隨機的動作新增至手中。</span><span class="sxs-lookup"><span data-stu-id="263be-185">**Hand Jitter Amount** adds random motion to hands.</span></span> <span data-ttu-id="263be-186">這項功能可用來模擬裝置上不正確的手追蹤，並確保互動適用于雜訊的輸入。</span><span class="sxs-lookup"><span data-stu-id="263be-186">This feature can be used to simulate inaccurate hand tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="hand-gestures"></a><span data-ttu-id="263be-187">手勢</span><span class="sxs-lookup"><span data-stu-id="263be-187">Hand gestures</span></span>

<span data-ttu-id="263be-188">捏合、抓取、刺探等手勢也可以模擬。</span><span class="sxs-lookup"><span data-stu-id="263be-188">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="263be-189">使用 **左側/右邊的控制項鍵** (*左移* 或 *空格*) 來啟用手形控制</span><span class="sxs-lookup"><span data-stu-id="263be-189">Enable hand control using the **Left/Right Hand Control Key** (*Left Shift* or *Space*)</span></span>

   <span data-ttu-id="263be-190">或者，使用切換鍵 (*T* 或 *Y*) 來切換實際操作。</span><span class="sxs-lookup"><span data-stu-id="263be-190">Alternatively, toggle the hands on/off using the toggle keys (*T* or *Y*).</span></span>

2. <span data-ttu-id="263be-191">在操作時，按住滑鼠按鍵以執行手勢手勢。</span><span class="sxs-lookup"><span data-stu-id="263be-191">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="263be-192">您可以對應每個滑鼠按鍵，使用 *左/中/右滑鼠右鍵手勢* 設定，將手圖形轉換成不同的手勢。</span><span class="sxs-lookup"><span data-stu-id="263be-192">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="263be-193">當未按下任何按鈕時， *預設手勢* 是手的形狀。</span><span class="sxs-lookup"><span data-stu-id="263be-193">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="263be-194">縮小 *手勢是* 唯一執行「選取」動作的手勢。</span><span class="sxs-lookup"><span data-stu-id="263be-194">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="263be-195">單次操作</span><span class="sxs-lookup"><span data-stu-id="263be-195">One-hand manipulation</span></span>

1. <span data-ttu-id="263be-196">按住 **左邊/右邊的控制項鍵** (*左移* 或 *空格*) </span><span class="sxs-lookup"><span data-stu-id="263be-196">Press and hold **Left/Right Hand Control Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="263be-197">物件上的點</span><span class="sxs-lookup"><span data-stu-id="263be-197">Point at object</span></span>
3. <span data-ttu-id="263be-198">按住滑鼠按鍵以縮小</span><span class="sxs-lookup"><span data-stu-id="263be-198">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="263be-199">使用您的滑鼠移動物件</span><span class="sxs-lookup"><span data-stu-id="263be-199">Use your mouse to move the object</span></span>
5. <span data-ttu-id="263be-200">放開滑鼠按鍵以停止互動</span><span class="sxs-lookup"><span data-stu-id="263be-200">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="two-hand-manipulation"></a><span data-ttu-id="263be-201">雙手勢操作</span><span class="sxs-lookup"><span data-stu-id="263be-201">Two-hand manipulation</span></span>

<span data-ttu-id="263be-202">若要同時以兩種方式操作物件，建議使用持續性手動模式。</span><span class="sxs-lookup"><span data-stu-id="263be-202">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="263be-203">按下切換鍵 (*T/Y*) 來切換。</span><span class="sxs-lookup"><span data-stu-id="263be-203">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="263be-204">一次處理一個手勢：</span><span class="sxs-lookup"><span data-stu-id="263be-204">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="263be-205">按住 **空格鍵** 以控制右手邊</span><span class="sxs-lookup"><span data-stu-id="263be-205">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="263be-206">將手移至您要抓取物件的位置</span><span class="sxs-lookup"><span data-stu-id="263be-206">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="263be-207">按下 **滑鼠左鍵** 可啟動 *縮小手勢。*</span><span class="sxs-lookup"><span data-stu-id="263be-207">Press the **left mouse button** to activate the *Pinch* gesture.</span></span> <span data-ttu-id="263be-208">在持續性模式中，當您放開滑鼠按鍵時，手勢將保持作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="263be-208">In persistent mode the gesture will remain active when you release the mouse button.</span></span>
1. <span data-ttu-id="263be-209">以另一種方式重複此程式，在第二個位置抓取相同的物件。</span><span class="sxs-lookup"><span data-stu-id="263be-209">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="263be-210">現在這兩個手都會抓取相同的物件，您可以將其中一個物件移至兩個執行中的操作。</span><span class="sxs-lookup"><span data-stu-id="263be-210">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="263be-211">GGV (注視、手勢和語音) 互動</span><span class="sxs-lookup"><span data-stu-id="263be-211">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="263be-212">根據預設，GGV 互動會在編輯器中啟用，但場景中不會有明確的手。</span><span class="sxs-lookup"><span data-stu-id="263be-212">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="263be-213">旋轉相機以指向互動物件上的注視游標 (滑鼠右鍵) </span><span class="sxs-lookup"><span data-stu-id="263be-213">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="263be-214">按一下並按住 **滑鼠** 左鍵以進行互動</span><span class="sxs-lookup"><span data-stu-id="263be-214">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="263be-215">再次旋轉相機以操作物件</span><span class="sxs-lookup"><span data-stu-id="263be-215">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="263be-216">您可以切換輸入模擬設定檔內的 [ *已啟用手動可用輸入* ] 選項來關閉此功能。</span><span class="sxs-lookup"><span data-stu-id="263be-216">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="263be-217">此外，您可以使用模擬的手 GGV 互動</span><span class="sxs-lookup"><span data-stu-id="263be-217">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="263be-218">藉由將 **手動模擬模式** 切換至 [輸入模擬設定檔](#enabling-the-input-simulation-service)中的 *手勢* 來啟用 GGV 模擬</span><span class="sxs-lookup"><span data-stu-id="263be-218">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="263be-219">旋轉相機以指向互動物件上的注視游標 (滑鼠右鍵) </span><span class="sxs-lookup"><span data-stu-id="263be-219">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="263be-220">按住 **空格鍵** 以控制右手邊</span><span class="sxs-lookup"><span data-stu-id="263be-220">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="263be-221">按一下並按住 **滑鼠** 左鍵以進行互動</span><span class="sxs-lookup"><span data-stu-id="263be-221">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="263be-222">使用您的滑鼠移動物件</span><span class="sxs-lookup"><span data-stu-id="263be-222">Use your mouse to move the object</span></span>
1. <span data-ttu-id="263be-223">放開滑鼠按鍵以停止互動</span><span class="sxs-lookup"><span data-stu-id="263be-223">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="eye-tracking"></a><span data-ttu-id="263be-224">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="263be-224">Eye tracking</span></span>

<span data-ttu-id="263be-225">您可以藉由檢查 [輸入模擬設定檔](#enabling-the-input-simulation-service)中的 [**模擬眼睛位置**] 選項來啟用 [眼睛追蹤模擬](../EyeTracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor)。</span><span class="sxs-lookup"><span data-stu-id="263be-225">[Eye tracking simulation](../EyeTracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="263be-226">這不應該與 GGV 的樣式互動一起使用 (因此，請確定 *已將 [* **手動模擬模式]** 設定為 [已) ]。</span><span class="sxs-lookup"><span data-stu-id="263be-226">This should not be used with GGV style interactions (so ensure that **Hand Simulation Mode** is set to *Articulated*).</span></span>

## <a name="see-also"></a><span data-ttu-id="263be-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="263be-227">See also</span></span>

* <span data-ttu-id="263be-228">[輸入系統設定檔](../Input/InputProviders.md)。</span><span class="sxs-lookup"><span data-stu-id="263be-228">[Input System profile](../Input/InputProviders.md).</span></span>
