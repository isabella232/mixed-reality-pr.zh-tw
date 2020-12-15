---
title: 使用 Windows Mixed Reality 模擬器
description: Windows Mixed Reality 模擬器可讓您在電腦上測試混合現實應用程式，而不需要 Windows Mixed Reality 的沉浸式耳機。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality，模擬器，測試
ms.openlocfilehash: 4ed3355df242f1df35c009e53149d834ea113e1f
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530302"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="6d1d5-104">使用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="6d1d5-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="6d1d5-105">Windows Mixed Reality 模擬器可讓您在電腦上測試混合現實應用程式，而不需要 Windows Mixed Reality 的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="6d1d5-106">模擬器可用於 Windows 10 Creators Update。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-106">The simulator is available with the Windows 10 Creators Update.</span></span> <span data-ttu-id="6d1d5-107">模擬器類似于 [HoloLens 模擬器](using-the-hololens-emulator.md)，不過模擬器不會使用虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator doesn't use a virtual machine.</span></span> <span data-ttu-id="6d1d5-108">模擬應用程式會在您的 Windows 10 desktop 使用者會話中執行，就像是使用沉浸式耳機一樣。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-108">Simulated apps run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="6d1d5-109">在沉浸式耳機上，感應器所讀取的人類和環境輸入，則是使用鍵盤、滑鼠或 Xbox 控制器來模擬。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-109">The human and environmental inputs read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="6d1d5-110">應用程式不需要任何修改，就能在模擬器中執行，也不知道它們不是在沉浸式耳機上執行。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-110">Apps don't need any modification to run in the simulator, and don't know they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="6d1d5-111">啟用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="6d1d5-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="6d1d5-112">從設定 **啟用開發人員模式**-> 的更新和安全性-> 開發人員</span><span class="sxs-lookup"><span data-stu-id="6d1d5-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="6d1d5-113">從桌面啟動 **混合實境入口**</span><span class="sxs-lookup"><span data-stu-id="6d1d5-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="6d1d5-114">如果這是您第一次啟動入口網站，您將需要經過安裝體驗</span><span class="sxs-lookup"><span data-stu-id="6d1d5-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="6d1d5-115">選取 [**開始** 使用]</span><span class="sxs-lookup"><span data-stu-id="6d1d5-115">Select **Get started**</span></span>
   2. <span data-ttu-id="6d1d5-116">選取 [ **我同意** 接受合約]</span><span class="sxs-lookup"><span data-stu-id="6d1d5-116">Select **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="6d1d5-117">**針對開發人員選取 [設定] 以模擬 (，)** 在沒有實體裝置的情況下繼續進行安裝</span><span class="sxs-lookup"><span data-stu-id="6d1d5-117">Select **Set up for simulation (for developers)** to continue through setup without a physical device</span></span>
   4. <span data-ttu-id="6d1d5-118">選取 [ **設定** ] 以確認您的選擇</span><span class="sxs-lookup"><span data-stu-id="6d1d5-118">Select **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="6d1d5-119">選取混合實境入口左側的 [ **適用于開發人員** ] 按鈕</span><span class="sxs-lookup"><span data-stu-id="6d1d5-119">Select the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="6d1d5-120">將模擬切換開關變成 **開啟**</span><span class="sxs-lookup"><span data-stu-id="6d1d5-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="6d1d5-121">啟用模擬時，預設會安裝並啟用左側的模擬 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="6d1d5-122">在 Windows 10 可能2019更新之前，安裝模擬的 6 DOF 控制器需要系統管理員許可權。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-122">Before the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="6d1d5-123">接受 [使用者帳戶控制] 對話方塊（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-123">Accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="6d1d5-124">您現在應該正在使用模擬執行！</span><span class="sxs-lookup"><span data-stu-id="6d1d5-124">You should now be running with simulation!</span></span>

<span data-ttu-id="6d1d5-125">如果您想要在 [設定] 中停用開發人員模式，請先在混合實境入口的 [**開發人員**] 區段中，將模擬切換開關切換為 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-125">If you want to disable Developer mode in Settings, you should first turn the Simulation toggle switch to **Off** in the **For developers** section of the Mixed Reality Portal.</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="6d1d5-126">將應用程式部署至混合現實模擬器</span><span class="sxs-lookup"><span data-stu-id="6d1d5-126">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="6d1d5-127">由於模擬器是在沒有虛擬機器的本機電腦上執行，因此您可以在進行偵錯工具時，將通用 Windows 應用程式部署至 **本機電腦** 。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-127">Since the simulator runs on your local PC without a Virtual Machine, you can deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="6d1d5-128">基本模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="6d1d5-128">Basic simulator input</span></span>

<span data-ttu-id="6d1d5-129">控制模擬器類似于許多常見的3D 視頻遊戲和 [HoloLens 模擬器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-129">Controlling the simulator is similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="6d1d5-130">可用的輸入選項包括使用鍵盤、滑鼠或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-130">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="6d1d5-131">您可以藉由將模擬使用者的動作帶到沉浸式耳機，來控制模擬器。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-131">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="6d1d5-132">您的動作會移動模擬的使用者，並與在沉浸式耳機上回應的應用程式產生互動。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-132">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="6d1d5-133">**向前走、向後走、向左走和向右走** - 使用鍵盤上的 W、A、S 和 D 鍵或 Xbox 控制器上的左搖桿。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-133">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="6d1d5-134">**向上、向下、向下** 、向右鍵選取並拖曳滑鼠、使用鍵盤上的方向鍵，或在 Xbox 控制器上使用右邊的箭號。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-134">**Look up, down, left, and right** - Select and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="6d1d5-135">**動作按鈕按下控制器** -以滑鼠右鍵按一下滑鼠，按鍵盤上的 enter 鍵，或使用 Xbox 控制器上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-135">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="6d1d5-136">**首頁按鈕按下控制器** -按鍵盤上的 Windows 鍵或 F2 鍵，或按下 Xbox 控制器上的 B 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-136">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="6d1d5-137">**用於滾動的控制器移動** -按住 ALT 鍵和滑鼠右鍵，然後將滑鼠向上/向下拖曳。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-137">**Controller movement for scrolling** - Hold the Alt key and the right mouse button, then drag the mouse up / down.</span></span> <span data-ttu-id="6d1d5-138">在 Xbox 控制器中，按住右邊的觸發程式和按鈕，然後向下和向下移動。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-138">In an Xbox controller, hold down the right trigger and A button and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="6d1d5-139">追蹤的控制器</span><span class="sxs-lookup"><span data-stu-id="6d1d5-139">Tracked controllers</span></span>

<span data-ttu-id="6d1d5-140">混合現實模擬器可以模擬最多兩個現成的追蹤移動控制器。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-140">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="6d1d5-141">使用混合實境入口中的切換開關來啟用它們。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-141">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="6d1d5-142">每個模擬控制器都有：</span><span class="sxs-lookup"><span data-stu-id="6d1d5-142">Each simulated controller has:</span></span>
* <span data-ttu-id="6d1d5-143">空間中的位置和方向</span><span class="sxs-lookup"><span data-stu-id="6d1d5-143">Position and orientation in space</span></span>
* <span data-ttu-id="6d1d5-144">首頁按鈕</span><span class="sxs-lookup"><span data-stu-id="6d1d5-144">Home button</span></span>
* <span data-ttu-id="6d1d5-145">功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="6d1d5-145">Menu button</span></span>
* <span data-ttu-id="6d1d5-146">底框按鈕</span><span class="sxs-lookup"><span data-stu-id="6d1d5-146">Grip button</span></span>
* <span data-ttu-id="6d1d5-147">Touchpad</span><span class="sxs-lookup"><span data-stu-id="6d1d5-147">Touchpad</span></span>
* <span data-ttu-id="6d1d5-148">操縱杆</span><span class="sxs-lookup"><span data-stu-id="6d1d5-148">Thumbstick</span></span>
* <span data-ttu-id="6d1d5-149">電池音量</span><span class="sxs-lookup"><span data-stu-id="6d1d5-149">Battery level</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="6d1d5-150">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="6d1d5-150">Next Development Checkpoint</span></span>

<span data-ttu-id="6d1d5-151">依循我們配置的 Unity 開發檢查點旅程，此時您會進入部署階段。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-151">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="6d1d5-152">您可以從這裡繼續前往下一個 [主題](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) ，或直接跳到新增 advanced services。</span><span class="sxs-lookup"><span data-stu-id="6d1d5-152">From here, you can continue to the next [topic](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) or jump directly to adding advanced services.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6d1d5-153">進階服務</span><span class="sxs-lookup"><span data-stu-id="6d1d5-153">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a><span data-ttu-id="6d1d5-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d1d5-154">See also</span></span>
* [<span data-ttu-id="6d1d5-155">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="6d1d5-155">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="6d1d5-156">Advanced Mixed Reality 模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="6d1d5-156">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="6d1d5-157">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="6d1d5-157">Spatial mapping in Unity</span></span>](../../develop/unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="6d1d5-158">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="6d1d5-158">Spatial mapping in DirectX</span></span>](../../develop/native/spatial-mapping-in-directx.md)
