---
title: Unity 中的鍵盤輸入
description: Unity 提供 TouchScreenKeyboard 類別，可在沒有可用的實體鍵盤時接受鍵盤輸入。
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: 鍵盤、輸入、unity、touchscreenkeyboard、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、HoloLens 2
ms.openlocfilehash: a7bd392036ca548fdd1f25581c8fc1910308909253f9c8df763e2039a32d3e9a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203850"
---
# <a name="keyboard-input-in-unity"></a>Unity 中的鍵盤輸入

**命名空間：** *UnityEngine*<br>
 **類型**： *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

雖然 HoloLens 支援許多形式的輸入，包括藍牙鍵盤，但大部分的應用程式都無法假設所有使用者都有可用的實體鍵盤。 如果您的應用程式需要文字輸入，則應該提供某種形式的螢幕小鍵盤。

Unity 提供 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 類別，可在沒有可用的實體鍵盤時接受鍵盤輸入。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Unity 中的 HoloLens 系統鍵盤行為

在 HoloLens 上， *TouchScreenKeyboard* 會利用系統的螢幕小鍵盤，並在您的 MR 應用程式的體積型視圖上方直接重迭。 此體驗類似于在 HoloLens 的內建應用程式中使用鍵盤。 請注意，系統鍵盤會根據目標平臺的功能來運作，例如 HoloLens 2 上的鍵盤可支援直接互動，而 HoloLens (第一代) 支援 GGV (注視、手勢和語音) 。 此外，從編輯器執行 Unity 遠端處理至 HoloLens 時，不會顯示系統鍵盤。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>在 Unity 應用程式中使用系統鍵盤

### <a name="declare-the-keyboard"></a>宣告鍵盤

在類別中，宣告變數來儲存 *TouchScreenKeyboard* 和變數，以保存鍵盤所傳回的字串。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>叫用鍵盤

當要求鍵盤輸入的事件發生時，請使用下列專案來顯示鍵盤。

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

您可以使用傳遞至函式的其他參數 `TouchScreenKeyboard.Open` 來控制鍵盤的行為 (例如設定預留位置文字或支援自動校正) 。 如需完整的參數清單，請參閱 [Unity 的檔](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)。

### <a name="retrieve-typed-contents"></a>取出具類型的內容

您可以藉由呼叫來直接取出內容 `keyboard.text` 。 您可能想要取得每個畫面格的內容，或只在鍵盤關閉時取得內容。

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>替代鍵盤選項

除了直接使用 *TouchScreenKeyboard* 類別，您也可以使用 Unity 的 *UI 輸入欄位* 或 *TextMeshPro 輸入欄位* 來取得使用者輸入。 此外，在 [MRTK](/windows/mixed-reality/mrtk-unity)的 [HandInteractionExamples 場景](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)中，有一個以 *TouchScreenKeyboard* 為基礎的實 (在左側) 有鍵盤互動範例。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unity 開發旅程圖，您將會在探索混合現實平臺功能和 Api。 您可以從這裡繼續前往任何 [主題](unity-development-overview.md#3-advanced-features) ，或直接跳到在裝置或模擬器上部署您的應用程式。

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機](../platform-capabilities-and-apis/using-visual-studio.md)
