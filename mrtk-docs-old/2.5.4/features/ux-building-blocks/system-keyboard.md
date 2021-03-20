---
title: SystemKeyBoard
description: MRTK 中的系統金鑰面板總覽
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、系統鍵盤、
ms.openlocfilehash: bade7d1774b331ae7d58587f2691b96187cc2c79
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686121"
---
# <a name="system-keyboard"></a><span data-ttu-id="fa3b8-104">系統鍵盤</span><span class="sxs-lookup"><span data-stu-id="fa3b8-104">System keyboard</span></span>

![系統鍵盤](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="fa3b8-106">Unity 應用程式可以在任何時間叫用系統鍵盤。</span><span class="sxs-lookup"><span data-stu-id="fa3b8-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="fa3b8-107">請注意，系統鍵盤會根據目標平臺的功能來運作，例如 HoloLens 2 上的鍵盤可支援直接互動，而 HoloLens 上的鍵盤 (第1代) 則會支援 GGV (注視、手勢和語音) <sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>。</span><span class="sxs-lookup"><span data-stu-id="fa3b8-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="fa3b8-108">此外，從編輯器將 [Unity 遠端](../tools/holographic-remoting.md) 執行到 HoloLens 時，系統鍵盤也不會顯示。</span><span class="sxs-lookup"><span data-stu-id="fa3b8-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="fa3b8-109">如何叫用系統鍵盤</span><span class="sxs-lookup"><span data-stu-id="fa3b8-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="fa3b8-110">如何讀取輸入</span><span class="sxs-lookup"><span data-stu-id="fa3b8-110">How to read the input</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

private void Update()
{
    if (keyboard != null)
    {
        keyboardText = keyboard.text;
        // Do stuff with keyboardText
    }
}
```

## <a name="system-keyboard-example"></a><span data-ttu-id="fa3b8-111">系統鍵盤範例</span><span class="sxs-lookup"><span data-stu-id="fa3b8-111">System keyboard example</span></span>

<span data-ttu-id="fa3b8-112">您可以看到一個簡單的範例，說明如何在 `MixedRealityKeyboard.cs` (資產/MRTK/SDK/實驗/功能/UX/MixedRealityKeyboard 中顯示系統鍵盤) </span><span class="sxs-lookup"><span data-stu-id="fa3b8-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="fa3b8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa3b8-113">See Also</span></span>

- [<span data-ttu-id="fa3b8-114">混合現實鍵盤協助程式類別</span><span class="sxs-lookup"><span data-stu-id="fa3b8-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)
