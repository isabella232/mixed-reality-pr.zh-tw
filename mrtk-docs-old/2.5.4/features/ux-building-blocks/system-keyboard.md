---
title: SystemKeyBoard
description: MRTK 中的系統金鑰面板總覽
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、系統鍵盤、
ms.openlocfilehash: fed51da13a58f61c3b1d1ea9e99a23b124da81c6268d5da64e98e986f138a583
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189238"
---
# <a name="system-keyboard"></a>系統鍵盤

![系統鍵盤](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Unity 應用程式可以在任何時間叫用系統鍵盤。 請注意，系統鍵盤會根據目標平臺的功能來運作，例如 HoloLens 2 上的鍵盤可支援直接互動，而 HoloLens (第一代) 上的鍵盤則支援 GGV (注視、手勢和語音) <sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>。 此外，從編輯器執行[Unity 遠端處理](../tools/holographic-remoting.md)至 HoloLens 時，不會顯示系統鍵盤。

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

- [混合現實鍵盤協助程式類別](../experimental/mixed-reality-keyboard.md)
