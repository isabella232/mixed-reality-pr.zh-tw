---
title: DirectX 中的鍵盤、滑鼠及控制器輸入
description: 說明如何為使用鍵盤、滑鼠和遊戲控制器的 Windows Mixed Reality 建立應用程式。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality、鍵盤、滑鼠、遊戲控制器、xbox 控制器、HoloLens、桌面、逐步解說、範例程式碼
ms.openlocfilehash: 47d5ac7c7517d607d29d004497f62ac0755c3051
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679940"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="e583a-104">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="e583a-104">Keyboard, mouse, and controller input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="e583a-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="e583a-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="e583a-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](../native/openxr-getting-started.md)** 。</span><span class="sxs-lookup"><span data-stu-id="e583a-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)** .</span></span>

<span data-ttu-id="e583a-107">鍵盤、滑鼠和遊戲控制器都可以為 Windows Mixed Reality 裝置輸入有用的形式。</span><span class="sxs-lookup"><span data-stu-id="e583a-107">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="e583a-108">HoloLens 支援藍牙鍵盤和滑鼠，可用於對您的應用程式進行偵錯工具或作為輸入的替代形式。</span><span class="sxs-lookup"><span data-stu-id="e583a-108">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="e583a-109">Windows Mixed Reality 也支援連接到電腦的沉浸式耳機，其中的滑鼠、鍵盤和遊戲控制器在過去是標準的。</span><span class="sxs-lookup"><span data-stu-id="e583a-109">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="e583a-110">若要在 HoloLens 上使用鍵盤輸入，請將藍牙鍵盤與您的裝置配對，或透過 Windows 裝置入口網站使用虛擬輸入。</span><span class="sxs-lookup"><span data-stu-id="e583a-110">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="e583a-111">若要在戴 Windows Mixed Reality 沉浸式耳機時使用鍵盤輸入，請將輸入焦點放在裝置上，或是使用 Windows 鍵 + Y 鍵盤組合，以將輸入焦點指派給混合的現實。</span><span class="sxs-lookup"><span data-stu-id="e583a-111">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="e583a-112">請記住，適用于 HoloLens 的應用程式必須提供未連接這些裝置的功能。</span><span class="sxs-lookup"><span data-stu-id="e583a-112">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="e583a-113">本文中的程式碼片段目前示範如何使用 c + + [/cx，而](../native/creating-a-holographic-directx-project.md)不是 c + + 全像 c + + 全像 c + + 的 + 17 相容 c + +/WinRT。</span><span class="sxs-lookup"><span data-stu-id="e583a-113">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="e583a-114">這些概念對 c + +/WinRT 專案而言是相等的，不過您必須轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="e583a-114">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="e583a-115">訂閱 CoreWindow 輸入事件</span><span class="sxs-lookup"><span data-stu-id="e583a-115">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="e583a-116">鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="e583a-116">Keyboard input</span></span>

<span data-ttu-id="e583a-117">在 Windows 全像應用程式範本中，我們包含鍵盤輸入的事件處理常式，就像任何其他 UWP 應用程式一樣。</span><span class="sxs-lookup"><span data-stu-id="e583a-117">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="e583a-118">在 Windows Mixed Reality 中，您的應用程式使用鍵盤輸入資料的方式相同。</span><span class="sxs-lookup"><span data-stu-id="e583a-118">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="e583a-119">從 AppView .cpp：</span><span class="sxs-lookup"><span data-stu-id="e583a-119">From AppView.cpp:</span></span>

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a><span data-ttu-id="e583a-120">虛擬鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="e583a-120">Virtual keyboard input</span></span>
<span data-ttu-id="e583a-121">針對沉浸式桌面耳機，您也可以支援 Windows 在您的沉浸式觀賞上轉譯的虛擬鍵盤。</span><span class="sxs-lookup"><span data-stu-id="e583a-121">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="e583a-122">為了支援這種情況，您的應用程式可以執行 **CoreTextEditCoNtext** 。</span><span class="sxs-lookup"><span data-stu-id="e583a-122">To support this, your app can implement **CoreTextEditContext** .</span></span> <span data-ttu-id="e583a-123">這可讓 Windows 瞭解您自己的應用程式轉譯文字方塊的狀態，讓虛擬鍵盤可以正確地參與該處的文字。</span><span class="sxs-lookup"><span data-stu-id="e583a-123">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="e583a-124">如需有關如何執行 CoreTextEditCoNtext 支援的詳細資訊，請參閱 [CoreTextEditCoNtext 範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。</span><span class="sxs-lookup"><span data-stu-id="e583a-124">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="e583a-125">滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="e583a-125">Mouse Input</span></span>

<span data-ttu-id="e583a-126">您也可以透過 UWP CoreWindow 輸入事件處理常式，再次使用滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="e583a-126">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="e583a-127">以下是如何修改 Windows 全像投影應用程式範本，以支援滑鼠點擊的方式，就像按下的手勢一樣。</span><span class="sxs-lookup"><span data-stu-id="e583a-127">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="e583a-128">進行這種修改之後，當您戴著沉浸式耳機裝置時，按一下滑鼠就會重新放置 cube。</span><span class="sxs-lookup"><span data-stu-id="e583a-128">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="e583a-129">請注意，UWP 應用程式也可以使用 [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API 取得滑鼠的原始 XY 資料。</span><span class="sxs-lookup"><span data-stu-id="e583a-129">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="e583a-130">首先，在 AppView 中宣告新的 OnPointerPressed 處理常式：</span><span class="sxs-lookup"><span data-stu-id="e583a-130">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="e583a-131">在 AppView .cpp 中，將下列程式碼新增至 SetWindow：</span><span class="sxs-lookup"><span data-stu-id="e583a-131">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="e583a-132">然後將 OnPointerPressed 的定義放在檔案底部：</span><span class="sxs-lookup"><span data-stu-id="e583a-132">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

<span data-ttu-id="e583a-133">我們剛剛加入的事件處理常式是通過範本主要類別的傳遞。</span><span class="sxs-lookup"><span data-stu-id="e583a-133">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="e583a-134">讓我們修改主要類別以支援此傳遞。</span><span class="sxs-lookup"><span data-stu-id="e583a-134">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="e583a-135">將這個公用方法宣告新增至標頭檔：</span><span class="sxs-lookup"><span data-stu-id="e583a-135">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="e583a-136">您也需要這個私用成員變數：</span><span class="sxs-lookup"><span data-stu-id="e583a-136">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="e583a-137">最後，我們將使用新的邏輯來更新主要類別，以支援滑鼠點擊。</span><span class="sxs-lookup"><span data-stu-id="e583a-137">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="e583a-138">首先，新增此事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e583a-138">Start by adding this event handler.</span></span> <span data-ttu-id="e583a-139">請務必更新類別名稱：</span><span class="sxs-lookup"><span data-stu-id="e583a-139">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="e583a-140">現在，在 Update 方法中，以下列內容取代現有的邏輯，以取得指標姿勢：</span><span class="sxs-lookup"><span data-stu-id="e583a-140">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="e583a-141">重新編譯和重新部署。</span><span class="sxs-lookup"><span data-stu-id="e583a-141">Recompile and redeploy.</span></span> <span data-ttu-id="e583a-142">您應該會注意到，按一下滑鼠後，就可以將 cube 重新放置在您的沉浸式耳機-或 HoloLens 中，並附加藍牙滑鼠。</span><span class="sxs-lookup"><span data-stu-id="e583a-142">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="e583a-143">遊戲控制器支援</span><span class="sxs-lookup"><span data-stu-id="e583a-143">Game controller support</span></span>

<span data-ttu-id="e583a-144">遊戲控制器可以是讓使用者控制沉浸式 Windows Mixed Reality 體驗的有趣且方便的方式。</span><span class="sxs-lookup"><span data-stu-id="e583a-144">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="e583a-145">將遊戲控制器的支援新增至 Windows 全像應用程式範本的第一步，是將下列私用成員宣告新增至您的主要檔案的標頭類別：</span><span class="sxs-lookup"><span data-stu-id="e583a-145">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

<span data-ttu-id="e583a-146">在主要類別的函式中，將遊戲系統事件和任何目前附加的 gamepads 初始化：</span><span class="sxs-lookup"><span data-stu-id="e583a-146">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

<span data-ttu-id="e583a-147">將這些事件處理常式新增至您的主要類別。</span><span class="sxs-lookup"><span data-stu-id="e583a-147">Add these event handlers to your main class.</span></span> <span data-ttu-id="e583a-148">請務必更新類別名稱：</span><span class="sxs-lookup"><span data-stu-id="e583a-148">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

<span data-ttu-id="e583a-149">最後，更新輸入邏輯以辨識控制器狀態中的變更。</span><span class="sxs-lookup"><span data-stu-id="e583a-149">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="e583a-150">在這裡，我們使用上一節中所討論的相同 m_pointerPressed 變數來新增滑鼠事件。</span><span class="sxs-lookup"><span data-stu-id="e583a-150">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="e583a-151">將此新增至 Update 方法，在它檢查 SpatialPointerPose 的位置之前：</span><span class="sxs-lookup"><span data-stu-id="e583a-151">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="e583a-152">清除主要類別時，別忘了取消註冊事件：</span><span class="sxs-lookup"><span data-stu-id="e583a-152">Don't forget to unregister the events when cleaning up the main class:</span></span>

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

<span data-ttu-id="e583a-153">重新編譯並重新部署。</span><span class="sxs-lookup"><span data-stu-id="e583a-153">Recompile, and redeploy.</span></span> <span data-ttu-id="e583a-154">您現在可以連接或配對遊戲控制器，並用它來調整旋轉 cube 的位置。</span><span class="sxs-lookup"><span data-stu-id="e583a-154">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="e583a-155">鍵盤和滑鼠輸入的重要指導方針</span><span class="sxs-lookup"><span data-stu-id="e583a-155">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="e583a-156">這段程式碼可以在 Microsoft HoloLens 上使用的一些主要差異，也就是主要依賴自然使用者輸入的裝置，而不是 Windows Mixed Reality 啟用的電腦上可用的裝置。</span><span class="sxs-lookup"><span data-stu-id="e583a-156">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="e583a-157">您無法依賴鍵盤或滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="e583a-157">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="e583a-158">您所有應用程式的功能都必須使用注視、手勢和語音輸入。</span><span class="sxs-lookup"><span data-stu-id="e583a-158">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="e583a-159">連接藍牙鍵盤時，針對您的應用程式可能會要求的任何文字啟用鍵盤輸入可能會很有説明。</span><span class="sxs-lookup"><span data-stu-id="e583a-159">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="e583a-160">例如，這可能是聽寫的絕佳補充。</span><span class="sxs-lookup"><span data-stu-id="e583a-160">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="e583a-161">當設計您的應用程式時，請不要依賴 (例如) WASD 和您遊戲的滑鼠外觀控制項。</span><span class="sxs-lookup"><span data-stu-id="e583a-161">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="e583a-162">HoloLens 的設計目的是要讓使用者在房間內四處進行。</span><span class="sxs-lookup"><span data-stu-id="e583a-162">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="e583a-163">在此情況下，使用者會直接控制相機。</span><span class="sxs-lookup"><span data-stu-id="e583a-163">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="e583a-164">使用移動/外觀控制項在房間周圍驅動攝影機的介面，不會提供相同的體驗。</span><span class="sxs-lookup"><span data-stu-id="e583a-164">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="e583a-165">鍵盤輸入可以很適合用來控制應用程式或遊戲引擎的偵錯工具，特別是因為使用者將不需要使用鍵盤。</span><span class="sxs-lookup"><span data-stu-id="e583a-165">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="e583a-166">使用 CoreWindow 事件 Api 時，與您所用的相同。</span><span class="sxs-lookup"><span data-stu-id="e583a-166">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="e583a-167">在此案例中，您可能會選擇執行一種方式，將您的應用程式設定為在您的偵錯工具期間將鍵盤事件路由傳送至「僅限偵錯工具輸入」模式。</span><span class="sxs-lookup"><span data-stu-id="e583a-167">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="e583a-168">藍牙控制器也可以運作。</span><span class="sxs-lookup"><span data-stu-id="e583a-168">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="e583a-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e583a-169">See also</span></span>
* [<span data-ttu-id="e583a-170">硬體配件</span><span class="sxs-lookup"><span data-stu-id="e583a-170">Hardware accessories</span></span>](../../discover/hardware-accessories.md)
