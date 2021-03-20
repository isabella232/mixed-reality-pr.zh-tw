---
title: README_MixedRealityKeyboard
description: 如何使用混合現實鍵盤的描述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: d636b40385d61c68c85c0f3e8600a903dfc103b1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692735"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="870ac-104">混合的現實和 HoloLens 鍵盤協助程式類別</span><span class="sxs-lookup"><span data-stu-id="870ac-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="870ac-105">MRTK 提供數個實驗性 helper 元件，可協助您從 [系統鍵盤](../../README_SystemKeyboard.md)啟動和讀取文字。</span><span class="sxs-lookup"><span data-stu-id="870ac-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../../README_SystemKeyboard.md).</span></span>

<span data-ttu-id="870ac-106">請注意，系統鍵盤會根據目標平臺的功能來運作，例如 HoloLens 2 上的鍵盤可支援直接互動，而 HoloLens 上的鍵盤 (第1代) 則會支援 GGV<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>。</span><span class="sxs-lookup"><span data-stu-id="870ac-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="870ac-107">此外，從編輯器將 [Unity 遠端](../../Tools/HolographicRemoting.md) 執行到 HoloLens 時，系統鍵盤也不會顯示。</span><span class="sxs-lookup"><span data-stu-id="870ac-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../../Tools/HolographicRemoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="870ac-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="870ac-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="870ac-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 是一種元件，可提供啟動和關閉系統鍵盤的方法，並與鍵盤輸入的文字互動。</span><span class="sxs-lookup"><span data-stu-id="870ac-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="870ac-110">如何使用</span><span class="sxs-lookup"><span data-stu-id="870ac-110">How to Use</span></span>

1. <span data-ttu-id="870ac-111">將 [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 元件附加至任何物件。</span><span class="sxs-lookup"><span data-stu-id="870ac-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="870ac-112">呼叫 `Show()` `Hide()` 以顯示和隱藏鍵盤，以及處理 `OnShowKeyboard` 、 `OnHideKeyboard` 和事件， `OnCommitText` 以在顯示、隱藏鍵盤及按下 enter 鍵時處理。</span><span class="sxs-lookup"><span data-stu-id="870ac-112">Call `Show()` `Hide()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="870ac-113">輸入欄位 TMP_KeyboardInputField 和 UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="870ac-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="870ac-114">[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField)和 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 類別是可以加入至文字輸入欄位的元件，以便在使用者輸入文字時，自動叫用系統鍵盤，並更新文字輸入欄位內容。</span><span class="sxs-lookup"><span data-stu-id="870ac-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="870ac-115">如何使用</span><span class="sxs-lookup"><span data-stu-id="870ac-115">How to use</span></span>

1. <span data-ttu-id="870ac-116">建立 UnityUI 或 TextMeshPro 的輸入欄位。</span><span class="sxs-lookup"><span data-stu-id="870ac-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="870ac-117">將對應的 [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) 或 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 元件新增至輸入欄位遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="870ac-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="870ac-118">UnityUI 輸入欄位和 TextMeshPro (TMPro) 輸入欄位的 Prefabs 可于 "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs" 取得</span><span class="sxs-lookup"><span data-stu-id="870ac-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="870ac-119">如何使用 TMP_KeyboardInputField 和 UI_KeyboardInputField 的範例位於 "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span><span class="sxs-lookup"><span data-stu-id="870ac-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>
