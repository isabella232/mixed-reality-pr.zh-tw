---
title: 使用 Windows Mixed Reality 模擬器
description: Windows Mixed Reality 模擬器可讓您在電腦上測試混合現實應用程式，而不需要 Windows Mixed Reality 的沉浸式耳機。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality，模擬器，測試
ms.openlocfilehash: 72ce82770f80b6c22837ac9484d88a4497d6b8f8
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679200"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="b75a0-104">使用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="b75a0-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="b75a0-105">Windows Mixed Reality 模擬器可讓您在電腦上測試混合現實應用程式，而不需要 Windows Mixed Reality 的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="b75a0-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="b75a0-106">從 Windows 10 Creators Update 開始提供。</span><span class="sxs-lookup"><span data-stu-id="b75a0-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="b75a0-107">模擬器類似于 [HoloLens 模擬器](using-the-hololens-emulator.md)，不過模擬器不會使用虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="b75a0-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="b75a0-108">在模擬器中執行的應用程式會在您的 Windows 10 desktop 使用者會話中執行，就像是使用沉浸式耳機一樣。</span><span class="sxs-lookup"><span data-stu-id="b75a0-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="b75a0-109">在沉浸式耳機上，感應器通常會讀取的人類和環境輸入，則是使用鍵盤、滑鼠或 Xbox 控制器來模擬。</span><span class="sxs-lookup"><span data-stu-id="b75a0-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="b75a0-110">應用程式不需要修改就能在模擬器中執行，也不知道它們不是在沉浸式耳機上執行。</span><span class="sxs-lookup"><span data-stu-id="b75a0-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="b75a0-111">啟用 Windows Mixed Reality 模擬器</span><span class="sxs-lookup"><span data-stu-id="b75a0-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="b75a0-112">從設定 **啟用開發人員模式** -> 的更新和安全性-> 開發人員</span><span class="sxs-lookup"><span data-stu-id="b75a0-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="b75a0-113">從桌面啟動 **混合實境入口**</span><span class="sxs-lookup"><span data-stu-id="b75a0-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="b75a0-114">如果這是您第一次啟動入口網站，您將需要經過安裝體驗</span><span class="sxs-lookup"><span data-stu-id="b75a0-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="b75a0-115">按一下 [ **開始** 使用]</span><span class="sxs-lookup"><span data-stu-id="b75a0-115">Click **Get started**</span></span>
   2. <span data-ttu-id="b75a0-116">按一下 [ **我同意** 接受合約]</span><span class="sxs-lookup"><span data-stu-id="b75a0-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="b75a0-117">按一下 [ **設定] (，以供開發人員)** 在不使用實體裝置的情況下繼續進行安裝</span><span class="sxs-lookup"><span data-stu-id="b75a0-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="b75a0-118">按一下 [ **設定** ] 以確認您的選擇</span><span class="sxs-lookup"><span data-stu-id="b75a0-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="b75a0-119">按一下混合實境入口左側的 [ **適用于開發人員** ] 按鈕</span><span class="sxs-lookup"><span data-stu-id="b75a0-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="b75a0-120">將模擬切換開關變成 **開啟**</span><span class="sxs-lookup"><span data-stu-id="b75a0-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="b75a0-121">啟用模擬時，預設會安裝並啟用左側的模擬 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="b75a0-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="b75a0-122">在 Windows 10 2019 之前的更新版本中，安裝模擬的 6 DOF 控制器需要系統管理員許可權。</span><span class="sxs-lookup"><span data-stu-id="b75a0-122">Prior to the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="b75a0-123">您必須接受 [使用者帳戶控制] 對話方塊（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="b75a0-123">You must accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="b75a0-124">您現在應該正在使用模擬執行！</span><span class="sxs-lookup"><span data-stu-id="b75a0-124">You should now be running with simulation!</span></span>

<span data-ttu-id="b75a0-125">如果您想要在 [設定] 中停用開發人員模式，請先在混合實境入口的 [ **開發人員** ] 區段中，將模擬切換開關切換為 [ **關閉** ]。</span><span class="sxs-lookup"><span data-stu-id="b75a0-125">If you want to disable Developer mode in Settings, you should first turn the Simulation toggle switch to **Off** in the **For developers** section of the Mixed Reality Portal.</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="b75a0-126">將應用程式部署至混合現實模擬器</span><span class="sxs-lookup"><span data-stu-id="b75a0-126">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="b75a0-127">由於模擬器是在沒有虛擬機器的本機電腦上執行，因此您可以在進行偵錯工具時，直接將通用 Windows 應用程式部署到 **本機電腦** 。</span><span class="sxs-lookup"><span data-stu-id="b75a0-127">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="b75a0-128">基本模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="b75a0-128">Basic simulator input</span></span>

<span data-ttu-id="b75a0-129">控制模擬器非常類似于許多常見的3D 視頻遊戲和 [HoloLens 模擬器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="b75a0-129">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="b75a0-130">可用的輸入選項包括使用鍵盤、滑鼠或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="b75a0-130">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="b75a0-131">您可以藉由將模擬使用者的動作帶到沉浸式耳機，來控制模擬器。</span><span class="sxs-lookup"><span data-stu-id="b75a0-131">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="b75a0-132">您的動作會移動模擬的使用者，並與在沉浸式耳機上回應的應用程式產生互動。</span><span class="sxs-lookup"><span data-stu-id="b75a0-132">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="b75a0-133">**向前走、向後走、向左走和向右走** - 使用鍵盤上的 W、A、S 和 D 鍵或 Xbox 控制器上的左搖桿。</span><span class="sxs-lookup"><span data-stu-id="b75a0-133">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="b75a0-134">**向上、向下、向左鍵，然後** 以滑鼠右鍵按一下並拖曳滑鼠、使用鍵盤上的方向鍵，或在 Xbox 控制器上使用右方鍵。</span><span class="sxs-lookup"><span data-stu-id="b75a0-134">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="b75a0-135">**動作按鈕按下控制器** -以滑鼠右鍵按一下滑鼠，按鍵盤上的 enter 鍵，或使用 Xbox 控制器上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="b75a0-135">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="b75a0-136">**首頁按鈕按下控制器** -按鍵盤上的 Windows 鍵或 F2 鍵，或按下 Xbox 控制器上的 B 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b75a0-136">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="b75a0-137">**用於滾動的控制器移動** -按住 ALT 鍵、按住滑鼠右鍵，然後將滑鼠向上或向下拖曳，然後將滑鼠向下拖曳，然後將滑鼠向下拖曳，然後向下移動並向下移動。</span><span class="sxs-lookup"><span data-stu-id="b75a0-137">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="b75a0-138">追蹤的控制器</span><span class="sxs-lookup"><span data-stu-id="b75a0-138">Tracked controllers</span></span>

<span data-ttu-id="b75a0-139">混合現實模擬器可以模擬最多兩個現成的追蹤移動控制器。</span><span class="sxs-lookup"><span data-stu-id="b75a0-139">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="b75a0-140">使用混合實境入口中的切換開關來啟用它們。</span><span class="sxs-lookup"><span data-stu-id="b75a0-140">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="b75a0-141">每個模擬控制器都有：</span><span class="sxs-lookup"><span data-stu-id="b75a0-141">Each simulated controller has:</span></span>
* <span data-ttu-id="b75a0-142">空間中的位置和方向</span><span class="sxs-lookup"><span data-stu-id="b75a0-142">Position and orientation in space</span></span>
* <span data-ttu-id="b75a0-143">首頁按鈕</span><span class="sxs-lookup"><span data-stu-id="b75a0-143">Home button</span></span>
* <span data-ttu-id="b75a0-144">功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="b75a0-144">Menu button</span></span>
* <span data-ttu-id="b75a0-145">底框按鈕</span><span class="sxs-lookup"><span data-stu-id="b75a0-145">Grip button</span></span>
* <span data-ttu-id="b75a0-146">Touchpad</span><span class="sxs-lookup"><span data-stu-id="b75a0-146">Touchpad</span></span>
* <span data-ttu-id="b75a0-147">操縱杆</span><span class="sxs-lookup"><span data-stu-id="b75a0-147">Thumbstick</span></span>
* <span data-ttu-id="b75a0-148">電池音量</span><span class="sxs-lookup"><span data-stu-id="b75a0-148">Battery level</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b75a0-149">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="b75a0-149">Next Development Checkpoint</span></span>

<span data-ttu-id="b75a0-150">如果您是遵循我們所配置的 Unity 開發檢查點旅程，您就會在部署階段。</span><span class="sxs-lookup"><span data-stu-id="b75a0-150">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="b75a0-151">您可以從這裡繼續進行下一個 [主題](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) ，或直接跳到新增 advanced services。</span><span class="sxs-lookup"><span data-stu-id="b75a0-151">From here, you can proceed to the next [topic](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) or jump directly to adding advanced services.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b75a0-152">Advanced services</span><span class="sxs-lookup"><span data-stu-id="b75a0-152">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a><span data-ttu-id="b75a0-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b75a0-153">See also</span></span>
* [<span data-ttu-id="b75a0-154">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="b75a0-154">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="b75a0-155">Advanced Mixed Reality 模擬器輸入</span><span class="sxs-lookup"><span data-stu-id="b75a0-155">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="b75a0-156">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="b75a0-156">Spatial mapping in Unity</span></span>](../../develop/unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="b75a0-157">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="b75a0-157">Spatial mapping in DirectX</span></span>](../../develop/native/spatial-mapping-in-directx.md)
