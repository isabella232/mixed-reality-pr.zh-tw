---
title: SystemKeyBoard
description: MRTK 中的系統金鑰面板總覽
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、系統鍵盤、
ms.openlocfilehash: 2955febd45f04e9f43c768e29d138715c33d33c5
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686671"
---
# <a name="system-keyboard"></a>系統鍵盤

![系統鍵盤](../Images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Unity 應用程式可以在任何時間叫用系統鍵盤。 請注意，系統鍵盤會根據目標平臺的功能來運作，例如 HoloLens 2 上的鍵盤可支援直接互動，而 HoloLens 上的鍵盤 (第1代) 則會支援 GGV (注視、手勢和語音) <sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>。 此外，從編輯器將 [Unity 遠端](../tools/HolographicRemoting.md) 執行到 HoloLens 時，系統鍵盤也不會顯示。

## <a name="how-to-invoke-the-system-keyboard"></a>如何叫用系統鍵盤

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a>如何讀取輸入

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

## <a name="system-keyboard-example"></a>系統鍵盤範例

您可以看到一個簡單的範例，說明如何在 `MixedRealityKeyboard.cs` (資產/MRTK/SDK/實驗/功能/UX/MixedRealityKeyboard 中顯示系統鍵盤) 

## <a name="see-also"></a>另請參閱

- [混合現實鍵盤協助程式類別](../experimental/mixed-reality-keyboard/MixedRealityKeyboard.md)
