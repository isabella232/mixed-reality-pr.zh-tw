---
title: DirectX 中的鍵盤、滑鼠及控制器輸入
description: 說明如何為使用鍵盤、滑鼠和遊戲控制器的 Windows Mixed Reality 建立應用程式。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality、鍵盤、滑鼠、遊戲控制器、xbox 控制器、HoloLens、桌面、逐步解說、範例程式碼
ms.openlocfilehash: e7ae65e660fe0348205fabc1c292328912fb1cdc
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244166"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>DirectX 中的鍵盤、滑鼠及控制器輸入

> [!NOTE]
> 本文與舊版 WinRT 原生 Api 相關。  針對新的原生應用程式專案，建議使用 **[OPENXR API](../native/openxr-getting-started.md)**。

鍵盤、滑鼠和遊戲控制器都可以為 Windows Mixed Reality 裝置輸入有用的形式。 HoloLens 上支援藍牙鍵盤和滑鼠，可用於對應用程式進行偵錯工具或作為輸入的替代形式。 Windows Mixed Reality 也支援連接到電腦的沉浸式耳機，其中的滑鼠、鍵盤和遊戲控制器在過去是標準的。

若要在 HoloLens 上使用鍵盤輸入，請將藍牙鍵盤配對至您的裝置，或透過 Windows 裝置入口網站使用虛擬輸入。 若要在戴 Windows Mixed Reality 沉浸式耳機時使用鍵盤輸入，請將輸入焦點放在裝置上，或使用 Windows 鍵 + Y 鍵盤組合，以將輸入焦點指派給混合的現實。 請記住，適用于 HoloLens 的應用程式必須提供未連接這些裝置的功能。
<!--Unity Note: the paragraph below explains that the article provides C++ code snippets. -->
>[!NOTE]
>本文中的程式碼片段目前示範如何使用 c + + [/cx，而](../native/creating-a-holographic-directx-project.md)不是 c + + 全像 c + + 全像 c + + 的 + 17 相容 c + +/WinRT。  這些概念對 c + +/WinRT 專案而言是相等的，不過您必須轉譯程式碼。

## <a name="subscribe-for-corewindow-input-events"></a>訂閱 CoreWindow 輸入事件

### <a name="keyboard-input"></a>鍵盤輸入

在 Windows 的全像攝影應用程式範本中，我們包含鍵盤輸入的事件處理常式，就像任何其他 UWP 應用程式一樣。 在 Windows Mixed Reality 中，您的應用程式使用鍵盤輸入資料的方式相同。

從 AppView .cpp：

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

### <a name="virtual-keyboard-input"></a>虛擬鍵盤輸入
針對沉浸式桌上型耳機，您可以藉由執行 **CoreTextEditCoNtext**，支援以您的沉浸式觀點 Windows 呈現的虛擬鍵盤。 這可讓 Windows 瞭解您自己的應用程式轉譯文字方塊的狀態，讓虛擬鍵盤可以正確地參與該處的文字。

如需有關如何執行 CoreTextEditCoNtext 支援的詳細資訊，請參閱 [CoreTextEditCoNtext 範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。

### <a name="mouse-input"></a>滑鼠輸入

您也可以透過 UWP CoreWindow 輸入事件處理常式，再次使用滑鼠輸入。 以下說明如何修改 Windows 的全像攝影應用程式範本，以像是按下手勢一樣的方式來支援滑鼠點擊。 進行這種修改之後，當您戴著沉浸式耳機裝置時，按一下滑鼠就會重新放置 cube。

> [!NOTE]
> UWP 應用程式也可以使用 [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) API 取得滑鼠的原始 XY 資料。

首先，在 AppView 中宣告新的 OnPointerPressed 處理常式：

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

在 AppView .cpp 中，將下列程式碼新增至 SetWindow：

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

然後將 OnPointerPressed 的定義放在檔案底部：

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

我們剛剛加入的事件處理常式是通過範本主要類別的傳遞。 讓我們修改主要類別以支援此傳遞。 將這個公用方法宣告新增至標頭檔：

```
// Handle mouse input.
       void OnPointerPressed();
```

您也需要這個私用成員變數：

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

最後，我們將使用新的邏輯來更新主要類別，以支援滑鼠點擊。 首先，新增此事件處理常式。 請務必更新類別名稱：

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

現在，在 Update 方法中，以下列內容取代現有的邏輯，以取得指標姿勢：

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

重新編譯和重新部署。 請注意，按一下滑鼠後，現在會將 cube 重新放置在您的沉浸式耳機中，或在連接藍牙滑鼠的 HoloLens。

### <a name="game-controller-support"></a>遊戲控制器支援

遊戲控制器可以是讓使用者控制沉浸式 Windows Mixed Reality 體驗的有趣且方便的方式。

 將下列私用成員宣告加入至您的主要檔案的標頭類別：

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

在主要類別的函式中，將遊戲系統事件和任何目前附加的 gamepads 初始化：

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

將這些事件處理常式新增至您的主要類別。 請務必更新類別名稱：

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

最後，更新輸入邏輯以辨識控制器狀態中的變更。 在這裡，我們使用上一節中所討論的相同 m_pointerPressed 變數來新增滑鼠事件。 將此新增至 Update 方法，在它檢查 SpatialPointerPose 的位置之前：

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

清除主要類別時，別忘了取消註冊事件：

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

重新編譯並重新部署。 您現在可以連接或配對遊戲控制器，並用它來調整旋轉 cube 的位置。

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>鍵盤和滑鼠輸入的重要指導方針

這段程式碼可以在 Microsoft HoloLens 上使用的一些主要差異，也就是主要依賴自然使用者輸入的裝置，而不是 Windows Mixed Reality 啟用的電腦上可用的裝置。
* 您無法依賴鍵盤或滑鼠輸入。 您所有應用程式的功能都必須使用注視、手勢和語音輸入。
* 附加藍牙鍵盤時，針對您的應用程式可能會要求的任何文字啟用鍵盤輸入可能會很有説明。 例如，這可能是聽寫的絕佳補充。
* 當設計您的應用程式時，請不要依賴 (例如) WASD 和您遊戲的滑鼠外觀控制項。 HoloLens 的設計目的是要讓使用者四處前往房間。 在此情況下，使用者會直接控制相機。 使用移動/外觀控制項在房間周圍驅動攝影機的介面，不會提供相同的體驗。
* 鍵盤輸入是控制應用程式或遊戲引擎偵測的絕佳方法，尤其是因為使用者不需要使用鍵盤。 使用 CoreWindow 事件 Api 時，與您所用的相同。 在此案例中，您可能會選擇執行一種方式，將您的應用程式設定為在您的偵錯工具期間將鍵盤事件路由傳送至「僅限偵錯工具輸入」模式。
* 藍牙控制器也可以運作。

## <a name="see-also"></a>另請參閱
* [硬體配件](../../discover/hardware-accessories.md)