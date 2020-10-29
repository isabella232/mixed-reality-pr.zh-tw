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
# <a name="using-the-windows-mixed-reality-simulator"></a>使用 Windows Mixed Reality 模擬器

Windows Mixed Reality 模擬器可讓您在電腦上測試混合現實應用程式，而不需要 Windows Mixed Reality 的沉浸式耳機。 從 Windows 10 Creators Update 開始提供。 模擬器類似于 [HoloLens 模擬器](using-the-hololens-emulator.md)，不過模擬器不會使用虛擬機器。 在模擬器中執行的應用程式會在您的 Windows 10 desktop 使用者會話中執行，就像是使用沉浸式耳機一樣。 在沉浸式耳機上，感應器通常會讀取的人類和環境輸入，則是使用鍵盤、滑鼠或 Xbox 控制器來模擬。 應用程式不需要修改就能在模擬器中執行，也不知道它們不是在沉浸式耳機上執行。

## <a name="enabling-the-windows-mixed-reality-simulator"></a>啟用 Windows Mixed Reality 模擬器

1. 從設定 **啟用開發人員模式** -> 的更新和安全性-> 開發人員
2. 從桌面啟動 **混合實境入口**
3. 如果這是您第一次啟動入口網站，您將需要經過安裝體驗
   1. 按一下 [ **開始** 使用]
   2. 按一下 [ **我同意** 接受合約]
   3. 按一下 [ **設定] (，以供開發人員)** 在不使用實體裝置的情況下繼續進行安裝
   4. 按一下 [ **設定** ] 以確認您的選擇
4. 按一下混合實境入口左側的 [ **適用于開發人員** ] 按鈕
5. 將模擬切換開關變成 **開啟**
   * 啟用模擬時，預設會安裝並啟用左側的模擬 6 DOF 控制器。  在 Windows 10 2019 之前的更新版本中，安裝模擬的 6 DOF 控制器需要系統管理員許可權。  您必須接受 [使用者帳戶控制] 對話方塊（如果有的話）。

您現在應該正在使用模擬執行！

如果您想要在 [設定] 中停用開發人員模式，請先在混合實境入口的 [ **開發人員** ] 區段中，將模擬切換開關切換為 [ **關閉** ]。

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>將應用程式部署至混合現實模擬器

由於模擬器是在沒有虛擬機器的本機電腦上執行，因此您可以在進行偵錯工具時，直接將通用 Windows 應用程式部署到 **本機電腦** 。

## <a name="basic-simulator-input"></a>基本模擬器輸入

控制模擬器非常類似于許多常見的3D 視頻遊戲和 [HoloLens 模擬器](using-the-hololens-emulator.md)。 可用的輸入選項包括使用鍵盤、滑鼠或 Xbox 控制器。

您可以藉由將模擬使用者的動作帶到沉浸式耳機，來控制模擬器。 您的動作會移動模擬的使用者，並與在沉浸式耳機上回應的應用程式產生互動。
* **向前走、向後走、向左走和向右走** - 使用鍵盤上的 W、A、S 和 D 鍵或 Xbox 控制器上的左搖桿。
* **向上、向下、向左鍵，然後** 以滑鼠右鍵按一下並拖曳滑鼠、使用鍵盤上的方向鍵，或在 Xbox 控制器上使用右方鍵。
* **動作按鈕按下控制器** -以滑鼠右鍵按一下滑鼠，按鍵盤上的 enter 鍵，或使用 Xbox 控制器上的按鈕。
* **首頁按鈕按下控制器** -按鍵盤上的 Windows 鍵或 F2 鍵，或按下 Xbox 控制器上的 B 按鈕。
* **用於滾動的控制器移動** -按住 ALT 鍵、按住滑鼠右鍵，然後將滑鼠向上或向下拖曳，然後將滑鼠向下拖曳，然後將滑鼠向下拖曳，然後向下移動並向下移動。

## <a name="tracked-controllers"></a>追蹤的控制器

混合現實模擬器可以模擬最多兩個現成的追蹤移動控制器。 使用混合實境入口中的切換開關來啟用它們。 每個模擬控制器都有：
* 空間中的位置和方向
* 首頁按鈕
* 功能表按鈕
* 底框按鈕
* Touchpad
* 操縱杆
* 電池音量

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您是遵循我們所配置的 Unity 開發檢查點旅程，您就會在部署階段。 您可以從這裡繼續進行下一個 [主題](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) ，或直接跳到新增 advanced services。

> [!div class="nextstepaction"]
> [Advanced services](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>另請參閱
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
* [Advanced Mixed Reality 模擬器輸入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Unity 中的空間對應](../../develop/unity/spatial-mapping-in-unity.md)
* [DirectX 中的空間對應](../../develop/native/spatial-mapping-in-directx.md)
