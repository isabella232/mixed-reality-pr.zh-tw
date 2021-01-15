---
title: Unity 中的鍵盤輸入
description: Unity 提供 TouchScreenKeyboard 類別，可在沒有可用的實體鍵盤時接受鍵盤輸入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 鍵盤、輸入、unity、touchscreenkeyboard、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 90416f91a7de369ff97a2254fed4b3773724408b
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226407"
---
# <a name="keyboard-input-in-unity"></a>Unity 中的鍵盤輸入

**命名空間：** *UnityEngine*<br>
 **類型**： *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

雖然 HoloLens 支援許多形式的輸入，包括 Bluetooth 鍵盤，但大部分的應用程式都無法假設所有使用者都有可用的實體鍵盤。 如果您的應用程式需要文字輸入，則應該提供某種形式的螢幕小鍵盤。

Unity 提供 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 類別，可在沒有可用的實體鍵盤時接受鍵盤輸入。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>在 Unity 中的 HoloLens 系統鍵盤行為

在 HoloLens 上， *TouchScreenKeyboard* 會利用系統的螢幕小鍵盤。 系統的螢幕小鍵盤無法在體積型 view 上方重迭。 Unity 必須建立次要 2D XAML 視圖來顯示鍵盤，然後在送出輸入後回到體積型 view。 使用者流程如下所示：
1. 使用者執行的動作會導致應用程式程式碼呼叫 *TouchScreenKeyboard*
    * 應用程式會負責暫停應用程式狀態，然後再呼叫 *TouchScreenKeyboard*
    * 應用程式可能會在切換回體積型視圖之前終止
2. Unity 切換至世界上 autoplaced 的 2D XAML 視圖
3. 使用者使用系統鍵盤輸入文字，並提交或取消
4. Unity 切換回體積型視圖
    * *TouchScreenKeyboard* 完成時，應用程式會負責繼續應用程式狀態
5. 提交的文字可在 *TouchScreenKeyboard* 中取得

### <a name="available-keyboard-views"></a>可用的鍵盤流覽

有六個不同的鍵盤視圖可用：
* 單行文字方塊
* 包含標題的單行 textbox
* 多行文字方塊
* 具有標題的多行文字方塊
* 單行密碼方塊
* 具有標題的單行密碼方塊

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>如何在 Unity 中啟用系統鍵盤

HoloLens 系統鍵盤僅適用于使用 [UWP 組建類型] 設定為 [XAML] 匯出的 Unity 應用程式。 當您選擇 "XAML" 作為 "D3D" 的「UWP 組建類型」時，會產生取捨。 如果您不熟悉這些取捨，您可能想要探索系統鍵盤的 [替代輸入解決方案](#alternative-keyboard-options) 。
1. 開啟 [**檔案] 功能表，然後** 選取 [**組建設定 ...** ]。
2. 確定 **平臺** 已設定為 **Windows Store**、 **SDK** 設定為 **通用 10**，然後將 **UWP 組建類型** 設定為 **XAML**。
3. 在 [ **組建設定** ] 對話方塊中，選取 [ **播放機設定 ...** ] 按鈕
4. 選取 **Windows [存放區** ] 索引標籤的設定
5. 展開 [ **其他設定** ] 群組
6. **在 [轉譯] 區段中**，核取 [**支援虛擬實境**] 核取方塊以新增 **虛擬實境裝置** 清單
7. 確定 **Windows 全息** 版出現在虛擬實境 sdk 清單中

>[!NOTE]
>如果您未將組建標示為 HoloLens 裝置支援的虛擬實境，此專案會匯出為 2D XAML 應用程式。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>在 Unity 應用程式中使用系統鍵盤

### <a name="declare-the-keyboard"></a>宣告鍵盤

在類別中，宣告變數來儲存 *TouchScreenKeyboard* 和變數，以保存鍵盤所傳回的字串。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>叫用鍵盤

當要求鍵盤輸入的事件發生時，請根據您想要在 textPlaceholder 參數中使用標題的輸入類型，呼叫其中一個函式。

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a>取出具類型的內容

在更新迴圈中，檢查鍵盤是否已收到新的輸入，並將其儲存供其他地方使用。

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.status == TouchScreenKeyboard.Status.Done)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a>替代鍵盤選項

我們瞭解將體積型視圖切換至2D 視圖不是從使用者取得文字輸入的理想方式。

透過 Unity 利用系統鍵盤的最新替代方案包括：
* 針對輸入使用語音聽寫 (<b>注意：</b> 這通常是因為在字典中找不到且不適合密碼輸入的單字所造成的錯誤) 
* 建立可在您的應用程式專屬視圖中運作的鍵盤

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unity 開發旅程圖，您將會在探索混合現實平臺功能和 Api。 您可以從這裡繼續前往任何 [主題](unity-development-overview.md#3-advanced-features) ，或直接跳到在裝置或模擬器上部署您的應用程式。

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機](../platform-capabilities-and-apis/using-visual-studio.md)
