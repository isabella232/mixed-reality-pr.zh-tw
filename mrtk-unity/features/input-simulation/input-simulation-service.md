---
title: 輸入模擬服務
description: MRTK 中輸入模擬服務的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 66b79c14bbd0ea8c188aba684b9bd1034de31bf9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176967"
---
# <a name="input-simulation-service"></a><span data-ttu-id="9d4b9-104">輸入模擬服務</span><span class="sxs-lookup"><span data-stu-id="9d4b9-104">Input simulation service</span></span>

![MRTK 輸入模擬](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

<span data-ttu-id="9d4b9-106">使用 MRTK 的輸入模擬，您可以在 Unity 編輯器中測試各種類型的互動，而不需要建立及部署到裝置。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-106">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="9d4b9-107">這可讓您快速地在設計和開發程式中反復查看您的想法。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-107">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="9d4b9-108">使用鍵盤和滑鼠組合來控制模擬的輸入。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-108">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="9d4b9-109">輸入模擬服務會模擬可能無法在 Unity 編輯器中使用的裝置和平臺行為。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-109">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="9d4b9-110">範例包括：</span><span class="sxs-lookup"><span data-stu-id="9d4b9-110">Examples include:</span></span>

* <span data-ttu-id="9d4b9-111">HoloLens 或 VR 裝置標頭追蹤</span><span class="sxs-lookup"><span data-stu-id="9d4b9-111">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="9d4b9-112">HoloLens 手勢</span><span class="sxs-lookup"><span data-stu-id="9d4b9-112">HoloLens hand gestures</span></span>
* <span data-ttu-id="9d4b9-113">HoloLens 2 明確的手追蹤</span><span class="sxs-lookup"><span data-stu-id="9d4b9-113">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="9d4b9-114">HoloLens 2 眼追蹤</span><span class="sxs-lookup"><span data-stu-id="9d4b9-114">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="9d4b9-115">VR 裝置控制器</span><span class="sxs-lookup"><span data-stu-id="9d4b9-115">VR device controllers</span></span>

> [!WARNING]
> <span data-ttu-id="9d4b9-116">使用 Unity 的 XR 全像 > 模擬模式 = 「在編輯器中模擬」時，這無法運作。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-116">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="9d4b9-117">Unity 的編輯器內模擬將從 MRTK 的輸入模擬中取得控制權。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-117">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="9d4b9-118">若要使用 MRTK 輸入模擬服務，您必須將 XR 全像模擬模式設定為模擬模式 = *"None"*</span><span class="sxs-lookup"><span data-stu-id="9d4b9-118">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="how-to-use-mrtk-input-simulation"></a><span data-ttu-id="9d4b9-119">如何使用 MRTK 輸入模擬</span><span class="sxs-lookup"><span data-stu-id="9d4b9-119">How to use MRTK Input simulation</span></span> 

<span data-ttu-id="9d4b9-120">在 MRTK 隨附的設定檔中，預設會啟用輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-120">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span> <span data-ttu-id="9d4b9-121">您只需按一下 [ **播放** ] 按鈕，就可以執行具有輸入模擬支援的場景。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-121">You can simply click **Play** button to run the scene with input simulation support.</span></span>

* <span data-ttu-id="9d4b9-122">按 **W、A、S、D、Q、E** 鍵以移動相機。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-122">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="9d4b9-123">按住滑鼠 **右鍵** ，並將滑鼠移至 [四處尋找]。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-123">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="9d4b9-124">若要啟動模擬的手，請按 **空格鍵 (右手)** 或 **左 Shift 鍵 (左邊)**</span><span class="sxs-lookup"><span data-stu-id="9d4b9-124">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="9d4b9-125">若要讓模擬手保持在視野中，請按 **T** 或 **Y** 鍵</span><span class="sxs-lookup"><span data-stu-id="9d4b9-125">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="9d4b9-126">若要旋轉模擬的手，請按住 **Ctrl 鍵** 並移動滑鼠</span><span class="sxs-lookup"><span data-stu-id="9d4b9-126">To rotate simulated hands, press and hold **Ctrl key** and move mouse</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="9d4b9-127">在編輯器中輸入模擬功能提要</span><span class="sxs-lookup"><span data-stu-id="9d4b9-127">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="9d4b9-128">在 HandInteractionExamples 場景中按 **左 Ctrl + H** ，以顯示具有輸入模擬控制項的提要表。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-128">Press **Left Ctrl + H** in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

> ![MRTK 輸入模擬功能提要](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="9d4b9-130">啟用輸入模擬服務</span><span class="sxs-lookup"><span data-stu-id="9d4b9-130">Enabling the input simulation service</span></span>

<span data-ttu-id="9d4b9-131">在輸入系統資料提供者設定下，可以使用下列設定輸入模擬服務。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-131">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="9d4b9-132">**類型** 必須是 *MixedReality。輸入 > InputSimulationService*。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-132">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="9d4b9-133">根據預設，**支援的平臺 (s)** 包含所有 *編輯器* 平臺，因為服務使用鍵盤和滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-133">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="9d4b9-134">輸入模擬服務可用於其他平臺端點（例如獨立式），方法是變更 **支援的平臺 (s)** 屬性，以包含所需的目標。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-134">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a><span data-ttu-id="9d4b9-135">攝影機控制項</span><span class="sxs-lookup"><span data-stu-id="9d4b9-135">Camera control</span></span>

<span data-ttu-id="9d4b9-136">輸入模擬服務可以模擬前端移動。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-136">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="9d4b9-137">旋轉相機</span><span class="sxs-lookup"><span data-stu-id="9d4b9-137">Rotating the camera</span></span>

1. <span data-ttu-id="9d4b9-138">將滑鼠停留在 [視口編輯器] 視窗上。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-138">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="9d4b9-139">*如果按鈕按下無法運作，您可能需要按一下視窗，以提供它的輸入焦點。*</span><span class="sxs-lookup"><span data-stu-id="9d4b9-139">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="9d4b9-140">按住 **滑鼠 [搜尋] 按鈕** (預設：) 滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-140">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="9d4b9-141">將滑鼠移至 [區] 視窗以旋轉相機。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-141">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="9d4b9-142">使用滾輪來圍繞視圖方向來旋轉相機。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-142">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="9d4b9-143">您可以藉由變更輸入模擬設定檔中的 **滑鼠外觀速度** 設定，來設定相機旋轉速度。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-143">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="9d4b9-144">或者，您也可以使用 [**外觀水準** / **外觀垂直** 軸]，將相機 (預設：遊戲控制器的右操縱杆) 。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-144">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="9d4b9-145">移動相機</span><span class="sxs-lookup"><span data-stu-id="9d4b9-145">Moving the camera</span></span>

<span data-ttu-id="9d4b9-146">使用 **移動水準** / **移動垂直** 軸將相機移動 (預設： WASD 鍵或遊戲控制器離開操縱杆) 。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-146">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="9d4b9-147">您也可以在 [工具] 視窗中明確設定相機位置和旋轉角度。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-147">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="9d4b9-148">您可以使用 [ **重設** ] 按鈕，將相機重設為其預設值。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-148">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="9d4b9-149">控制器模擬</span><span class="sxs-lookup"><span data-stu-id="9d4b9-149">Controller simulation</span></span>

<span data-ttu-id="9d4b9-150">輸入模擬支援模擬控制器裝置 (亦即移動控制器和手) 。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-150">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="9d4b9-151">這些虛擬控制器可以與任何支援一般控制器的物件互動，例如按鈕或 grabbable 物件。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-151">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="9d4b9-152">控制器模擬模式</span><span class="sxs-lookup"><span data-stu-id="9d4b9-152">Controller simulation mode</span></span>

<span data-ttu-id="9d4b9-153">在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中， **預設控制器模擬模式** 設定會在三個不同的輸入模型之間切換。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-153">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="9d4b9-154">您也可以在輸入模擬設定檔中設定此預設模式。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-154">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="9d4b9-155">明確表達的 *手：模擬* 具有聯合位置資料的全向裝置。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-155">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="9d4b9-156">模擬 HoloLens 2 互動模型。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-156">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="9d4b9-157">以確切定位或使用觸控為依據的互動，可在此模式中模擬。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-157">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="9d4b9-158">*手手勢*：利用點擊和基本手勢模擬簡化的模型。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-158">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="9d4b9-159">模擬[HoloLens 互動模型](/windows/mixed-reality/gestures)。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-159">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="9d4b9-160">焦點是使用注視指標來控制。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-160">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="9d4b9-161">「 *攻* 點」手勢用來與按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-161">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="9d4b9-162">*移動控制器*：模擬與 VR 耳機搭配使用的動作控制器，其運作方式類似于與明確表達的互動。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-162">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="9d4b9-163">使用控制器互動模型來模擬 VR 耳機。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-163">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="9d4b9-164">觸發程式、抓取和功能表鍵是透過鍵盤和滑鼠輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-164">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="9d4b9-165">模擬控制器移動</span><span class="sxs-lookup"><span data-stu-id="9d4b9-165">Simulating controller movement</span></span>

<span data-ttu-id="9d4b9-166">按住 **左/靠右控制器操作金鑰** (預設：左方控制器的 *左移位* 和右邊控制器的 *空間*) ，以取得任一控制器的控制權。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-166">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="9d4b9-167">當按下操作按鍵時，控制器將會出現在 [功能區] 中。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-167">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="9d4b9-168">一旦釋放操作金鑰之後，控制器會在短暫的 **控制器隱藏 Timeout** 之後消失。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-168">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="9d4b9-169">您可以透過 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中的相機來切換和凍結控制器，或按下 **切換左/向右控制器鍵** (預設值： *T* 代表左邊， *Y* 表示右邊的) 。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-169">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="9d4b9-170">再按一次切換鍵，再次隱藏控制器。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-170">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="9d4b9-171">若要操控控制器，必須保留 **左/右控制器操作金鑰** 。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-171">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="9d4b9-172">按兩下 **Left/Right 控制器操作金鑰** 也可以開啟/關閉控制器。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-172">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="9d4b9-173">滑鼠移動會將控制器移至 [視圖] 平面。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-173">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="9d4b9-174">您可以使用 **滑鼠滾輪**，更進一步或更接近相機來移動控制器。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-174">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="9d4b9-175">若要使用滑鼠旋轉控制器，請將 **左/右控制器操作金鑰** (*左移* 或 *空格*) *，然後* 將 **控制器旋轉按鈕** (預設： *左方 Ctrl* 按鈕) ，然後移動滑鼠以旋轉控制器。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-175">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="9d4b9-176">您可以藉由變更輸入模擬設定檔中的 **滑鼠控制器旋轉速度** 設定，來設定控制器旋轉速度。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-176">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="9d4b9-177">所有放置也都可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中變更，包括重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-177">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="9d4b9-178">其他設定檔設定</span><span class="sxs-lookup"><span data-stu-id="9d4b9-178">Additional profile settings</span></span>

* <span data-ttu-id="9d4b9-179">**控制器深度乘數** 控制滑鼠滾輪深度移動的敏感度。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-179">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="9d4b9-180">較大的數位會加速控制器縮放。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-180">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="9d4b9-181">**預設控制器距離** 是來自相機的控制器初始距離。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-181">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="9d4b9-182">按一下 [ **重設** ] 按鈕控制器也會將控制器放在這個距離。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-182">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="9d4b9-183">**控制器抖動量** 會將隨機動作新增至控制器。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-183">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="9d4b9-184">這項功能可用來模擬裝置上不正確的控制器追蹤，並確保互動適用于雜訊的輸入。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-184">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="9d4b9-185">手勢</span><span class="sxs-lookup"><span data-stu-id="9d4b9-185">Hand gestures</span></span>

<span data-ttu-id="9d4b9-186">捏合、抓取、刺探等手勢也可以模擬。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-186">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="9d4b9-187">使用 **left/Right 控制器操作金鑰** (*左移* 或 *空格*) 來啟用手形控制</span><span class="sxs-lookup"><span data-stu-id="9d4b9-187">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="9d4b9-188">在操作時，按住滑鼠按鍵以執行手勢手勢。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-188">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="9d4b9-189">您可以對應每個滑鼠按鍵，使用 *左/中/右滑鼠右鍵手勢* 設定，將手圖形轉換成不同的手勢。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-189">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="9d4b9-190">當未按下任何按鈕時， *預設手勢* 是手的形狀。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-190">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="9d4b9-191">縮小 *手勢是* 唯一執行「選取」動作的手勢。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-191">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="9d4b9-192">單次操作</span><span class="sxs-lookup"><span data-stu-id="9d4b9-192">One-hand manipulation</span></span>

1. <span data-ttu-id="9d4b9-193">按住 **left/Right 控制器操作金鑰** (*左移* 或 *空格*) </span><span class="sxs-lookup"><span data-stu-id="9d4b9-193">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="9d4b9-194">物件上的點</span><span class="sxs-lookup"><span data-stu-id="9d4b9-194">Point at object</span></span>
3. <span data-ttu-id="9d4b9-195">按住滑鼠按鍵以縮小</span><span class="sxs-lookup"><span data-stu-id="9d4b9-195">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="9d4b9-196">使用您的滑鼠移動物件</span><span class="sxs-lookup"><span data-stu-id="9d4b9-196">Use your mouse to move the object</span></span>
5. <span data-ttu-id="9d4b9-197">放開滑鼠按鍵以停止互動</span><span class="sxs-lookup"><span data-stu-id="9d4b9-197">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="9d4b9-198">雙手勢操作</span><span class="sxs-lookup"><span data-stu-id="9d4b9-198">Two-hand manipulation</span></span>

<span data-ttu-id="9d4b9-199">若要同時以兩種方式操作物件，建議使用持續性手動模式。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-199">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="9d4b9-200">按下切換鍵 (*T/Y*) 來切換。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-200">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="9d4b9-201">一次處理一個手勢：</span><span class="sxs-lookup"><span data-stu-id="9d4b9-201">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="9d4b9-202">按住 **空格鍵** 以控制右手邊</span><span class="sxs-lookup"><span data-stu-id="9d4b9-202">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="9d4b9-203">將手移至您要抓取物件的位置</span><span class="sxs-lookup"><span data-stu-id="9d4b9-203">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="9d4b9-204">按下 **滑鼠左鍵** 可啟動 *縮小手勢。*</span><span class="sxs-lookup"><span data-stu-id="9d4b9-204">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="9d4b9-205">釋放 **空間** 可停止控制右手邊。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-205">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="9d4b9-206">手將會凍結並 *鎖定到縮小手勢，* 因為它已不再被操作。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-206">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="9d4b9-207">以另一種方式重複此程式，在第二個位置抓取相同的物件。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-207">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="9d4b9-208">現在這兩個手都會抓取相同的物件，您可以將其中一個物件移至兩個執行中的操作。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-208">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="9d4b9-209">GGV (注視、手勢和語音) 互動</span><span class="sxs-lookup"><span data-stu-id="9d4b9-209">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="9d4b9-210">根據預設，GGV 互動會在編輯器中啟用，但場景中不會有明確的手。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-210">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="9d4b9-211">旋轉相機以指向互動物件上的注視游標 (滑鼠右鍵) </span><span class="sxs-lookup"><span data-stu-id="9d4b9-211">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="9d4b9-212">按一下並按住 **滑鼠** 左鍵以進行互動</span><span class="sxs-lookup"><span data-stu-id="9d4b9-212">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="9d4b9-213">再次旋轉相機以操作物件</span><span class="sxs-lookup"><span data-stu-id="9d4b9-213">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="9d4b9-214">您可以切換輸入模擬設定檔內的 [ *已啟用手動可用輸入* ] 選項來關閉此功能。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-214">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="9d4b9-215">此外，您可以使用模擬的手 GGV 互動</span><span class="sxs-lookup"><span data-stu-id="9d4b9-215">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="9d4b9-216">藉由將 **手動模擬模式** 切換至 [輸入模擬設定檔](#enabling-the-input-simulation-service)中的 *手勢* 來啟用 GGV 模擬</span><span class="sxs-lookup"><span data-stu-id="9d4b9-216">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="9d4b9-217">旋轉相機以指向互動物件上的注視游標 (滑鼠右鍵) </span><span class="sxs-lookup"><span data-stu-id="9d4b9-217">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="9d4b9-218">按住 **空格鍵** 以控制右手邊</span><span class="sxs-lookup"><span data-stu-id="9d4b9-218">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="9d4b9-219">按一下並按住 **滑鼠** 左鍵以進行互動</span><span class="sxs-lookup"><span data-stu-id="9d4b9-219">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="9d4b9-220">使用您的滑鼠移動物件</span><span class="sxs-lookup"><span data-stu-id="9d4b9-220">Use your mouse to move the object</span></span>
1. <span data-ttu-id="9d4b9-221">放開滑鼠按鍵以停止互動</span><span class="sxs-lookup"><span data-stu-id="9d4b9-221">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="9d4b9-222">引發傳送事件</span><span class="sxs-lookup"><span data-stu-id="9d4b9-222">Raising Teleport Events</span></span>

<span data-ttu-id="9d4b9-223">若要在輸入模擬中引發「傳送」事件，請在輸入模擬設定檔中設定手勢設定，使其在另一次執行「傳送」**結束** 手勢時，執行 **「傳送」開始** 手勢。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-223">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="9d4b9-224">**「傳送開始」** 手勢會顯示「傳送」指標，而「**傳送結束** gesure 將會完成傳送動作並移動使用者。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-224">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="9d4b9-225">產生的傳送的 y 位置取決於沿著 y 軸的相機位移。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-225">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="9d4b9-226">在編輯器中，預設值為0，因此請使用 **Q** 和 **E** 鍵將它調整為適當的高度。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-226">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![輸入模擬傳送設定](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="9d4b9-228">移動控制器互動</span><span class="sxs-lookup"><span data-stu-id="9d4b9-228">Motion controller interaction</span></span>

<span data-ttu-id="9d4b9-229">模擬的動作控制器可透過與明確表達的相同方式來操作。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-229">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="9d4b9-230">在觸發程式、抓取和功能表鍵分別對應至 *滑鼠左鍵*、 *G* 和 *M* 鍵的情況下，互動模型與明確的手互動很類似。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-230">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="9d4b9-231">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="9d4b9-231">Eye tracking</span></span>

<span data-ttu-id="9d4b9-232">您可以藉由檢查 [輸入模擬設定檔](#enabling-the-input-simulation-service)中的 [**模擬眼睛位置**] 選項來啟用 [眼睛追蹤模擬](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor)。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-232">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="9d4b9-233">這不應該與 GGV 或移動控制器樣式互動一起使用 (因此，請確定 **預設控制器模擬模式** 已設定為 [ *已) ]* 。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-233">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="9d4b9-234">輸入模擬工具視窗</span><span class="sxs-lookup"><span data-stu-id="9d4b9-234">Input simulation tools window</span></span>

<span data-ttu-id="9d4b9-235">從 **混合現實** 工具組  >    >  **公用程式**  >  **輸入模擬** 功能表啟用輸入模擬工具視窗。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-235">Enable the input simulation tools window from the  **Mixed Reality** > **Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="9d4b9-236">此視窗可讓您存取在播放模式期間的輸入模擬狀態。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-236">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons-optional"></a><span data-ttu-id="9d4b9-237">選擇區按鈕 (選用) </span><span class="sxs-lookup"><span data-stu-id="9d4b9-237">Viewport buttons (optional)</span></span>

<span data-ttu-id="9d4b9-238">在 [指標] **預製專案** 下的輸入模擬設定檔中，可以指定用於控制基本放置之編輯器中按鈕的預製專案。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-238">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="9d4b9-239">這是選擇性的公用程式，可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中存取相同的功能。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-239">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="9d4b9-240">依預設會停用視口指標，因為它們目前有時可能會干擾 Unity UI 互動。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-240">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="9d4b9-241">請參閱問題 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-241">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="9d4b9-242">若要啟用，請將 InputSimulationIndicators 預製專案新增至指標 **預製專案**。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-242">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="9d4b9-243">手圖示會顯示模擬手的狀態：</span><span class="sxs-lookup"><span data-stu-id="9d4b9-243">Hand icons show the state of the simulated hands:</span></span>

* ![未追蹤的手圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="9d4b9-245&quot;>手中沒有追蹤。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9d4b9-245&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;9d4b9-246&quot;>按一下以啟用手。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;9d4b9-246&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;9d4b9-247&quot;>![追蹤的手形圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;追蹤的手形圖示") 這會受到追蹤，但不是由使用者控制。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-247">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="9d4b9-248">按一下以隱藏手。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-248">Click to hide the hand.</span></span>
* <span data-ttu-id="9d4b9-249">![控制的手圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "控制的手圖示") 手由使用者追蹤及控制。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-249">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="9d4b9-250">按一下以隱藏手。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-250">Click to hide the hand.</span></span>
* <span data-ttu-id="9d4b9-251">![重設手形圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "重設手形圖示") 按一下可將手重設為預設位置。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-251">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>


## <a name="see-also"></a><span data-ttu-id="9d4b9-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d4b9-252">See also</span></span>

* <span data-ttu-id="9d4b9-253">[輸入系統設定檔](../input/input-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="9d4b9-253">[Input System profile](../input/input-providers.md).</span></span>
