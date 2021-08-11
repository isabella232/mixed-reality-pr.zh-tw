---
title: 混合現實鍵盤
description: 如何使用混合現實鍵盤的描述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 068d88483eff8db5466c6b5ff0d2ca8bbc0b5dddee549bb3d87c82fa740bc8fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197008"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Mixed Reality 和 HoloLens 鍵盤協助程式類別

MRTK 提供數個實驗性 helper 元件，可協助您從 [系統鍵盤](../ux-building-blocks/system-keyboard.md)啟動和讀取文字。

請注意，系統鍵盤會根據目標平臺的功能來運作，例如 HoloLens 2 上的鍵盤可支援直接互動，而 HoloLens (第一代) 上的鍵盤則支援 GGV<sup>[1](/windows/mixed-reality/gaze)</sup>。 此外，從編輯器執行[Unity 遠端處理](../tools/holographic-remoting.md)至 HoloLens 時，不會顯示系統鍵盤。

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 是一種元件，可提供啟動和關閉系統鍵盤的方法，並與鍵盤輸入的文字互動。  

### <a name="how-to-use"></a>如何使用

1. 將 [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 元件附加至任何物件。
2. 呼叫 `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` 以顯示和隱藏鍵盤，以及處理 `OnShowKeyboard` 、 `OnHideKeyboard` 和事件， `OnCommitText` 以在顯示、隱藏鍵盤及按下 enter 鍵時處理。

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>輸入欄位 TMP_KeyboardInputField 和 UI_KeyboardInputField

[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField)和 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 類別是可以加入至文字輸入欄位的元件，以便在使用者輸入文字時，自動叫用系統鍵盤，並更新文字輸入欄位內容。

### <a name="how-to-use"></a>如何使用

1. 建立 UnityUI 或 TextMeshPro 的輸入欄位。
2. 將對應的 [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) 或 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 元件新增至輸入欄位遊戲物件。

UnityUI 輸入欄位和 TextMeshPro (TMPro) 輸入欄位的 Prefabs 可于 "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs" 取得

如何使用 TMP_KeyboardInputField 和 UI_KeyboardInputField 的範例位於 "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"