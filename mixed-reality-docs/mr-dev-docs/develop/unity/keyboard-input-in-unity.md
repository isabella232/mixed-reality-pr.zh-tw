---
title: Unity 中的鍵盤輸入
description: Unity 提供 TouchScreenKeyboard 類別，可在沒有可用的實體鍵盤時接受鍵盤輸入。
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: 鍵盤、輸入、unity、touchscreenkeyboard、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、HoloLens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098270"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="30259-104">Unity 中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="30259-104">Keyboard input in Unity</span></span>

<span data-ttu-id="30259-105">**命名空間：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="30259-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="30259-106">**類型**： *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="30259-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="30259-107">雖然 HoloLens 支援許多形式的輸入，包括 Bluetooth 鍵盤，但大部分的應用程式都無法假設所有使用者都有可用的實體鍵盤。</span><span class="sxs-lookup"><span data-stu-id="30259-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="30259-108">如果您的應用程式需要文字輸入，則應該提供某種形式的螢幕小鍵盤。</span><span class="sxs-lookup"><span data-stu-id="30259-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="30259-109">Unity 提供 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 類別，可在沒有可用的實體鍵盤時接受鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="30259-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="30259-110">在 Unity 中的 HoloLens 系統鍵盤行為</span><span class="sxs-lookup"><span data-stu-id="30259-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="30259-111">在 HoloLens 上， *TouchScreenKeyboard* 會利用系統的螢幕小鍵盤，並在您的 MR 應用程式的體積型視圖上方直接重迭。</span><span class="sxs-lookup"><span data-stu-id="30259-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard and directly overlays on top of the volumetric view of your MR application.</span></span> <span data-ttu-id="30259-112">此體驗類似于在 HoloLens 的內建應用程式中使用鍵盤。</span><span class="sxs-lookup"><span data-stu-id="30259-112">The experience is similar to using keyboard in the built-in apps of HoloLens.</span></span> <span data-ttu-id="30259-113">請注意，系統鍵盤會根據目標平臺的功能來運作，例如 HoloLens 2 上的鍵盤可支援直接互動，而 HoloLens 上的鍵盤 (第一代) 則會支援 GGV (注視、手勢和語音) 。</span><span class="sxs-lookup"><span data-stu-id="30259-113">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice).</span></span> <span data-ttu-id="30259-114">此外，從編輯器將 Unity 遠端執行到 HoloLens 時，系統鍵盤也不會顯示。</span><span class="sxs-lookup"><span data-stu-id="30259-114">Additionally, the system keyboard will not show up when performing Unity Remoting from the editor to a HoloLens.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="30259-115">在 Unity 應用程式中使用系統鍵盤</span><span class="sxs-lookup"><span data-stu-id="30259-115">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="30259-116">宣告鍵盤</span><span class="sxs-lookup"><span data-stu-id="30259-116">Declare the keyboard</span></span>

<span data-ttu-id="30259-117">在類別中，宣告變數來儲存 *TouchScreenKeyboard* 和變數，以保存鍵盤所傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="30259-117">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="30259-118">叫用鍵盤</span><span class="sxs-lookup"><span data-stu-id="30259-118">Invoke the keyboard</span></span>

<span data-ttu-id="30259-119">當要求鍵盤輸入的事件發生時，請使用下列專案來顯示鍵盤。</span><span class="sxs-lookup"><span data-stu-id="30259-119">When an event occurs requesting keyboard input, use the following to show the keyboard.</span></span>

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

<span data-ttu-id="30259-120">您可以使用傳遞至函式的其他參數 `TouchScreenKeyboard.Open` 來控制鍵盤的行為 (例如設定預留位置文字或支援自動校正) 。</span><span class="sxs-lookup"><span data-stu-id="30259-120">You can use additional parameters passed into the `TouchScreenKeyboard.Open` function to control the behavior of the keyboard (e.g. setting placeholder text or supporting autocorrection).</span></span> <span data-ttu-id="30259-121">如需完整的參數清單，請參閱 [Unity 的檔](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)。</span><span class="sxs-lookup"><span data-stu-id="30259-121">For the full list of parameters please refer to [Unity's documentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span></span>

### <a name="retrieve-typed-contents"></a><span data-ttu-id="30259-122">取出具類型的內容</span><span class="sxs-lookup"><span data-stu-id="30259-122">Retrieve typed contents</span></span>

<span data-ttu-id="30259-123">您可以藉由呼叫來直接取出內容 `keyboard.text` 。</span><span class="sxs-lookup"><span data-stu-id="30259-123">The content can simply be retrieved by calling `keyboard.text`.</span></span> <span data-ttu-id="30259-124">您可能想要取得每個畫面格的內容，或只在鍵盤關閉時取得內容。</span><span class="sxs-lookup"><span data-stu-id="30259-124">You may want to retrieve the content per frame or only when the keyboard is closed.</span></span>

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="30259-125">替代鍵盤選項</span><span class="sxs-lookup"><span data-stu-id="30259-125">Alternative keyboard options</span></span>

<span data-ttu-id="30259-126">除了直接使用 *TouchScreenKeyboard* 類別，您也可以使用 Unity 的 *UI 輸入欄位* 或 *TextMeshPro 輸入欄位* 來取得使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="30259-126">Besides using the *TouchScreenKeyboard* class directly, you can also get user input by using Unity's *UI Input Field* or *TextMeshPro Input Field*.</span></span> <span data-ttu-id="30259-127">此外，在 [MRTK](/windows/mixed-reality/mrtk-unity)的 [HandInteractionExamples 場景](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)中，有一個以 *TouchScreenKeyboard* 為基礎的實 (在左側) 有鍵盤互動範例。</span><span class="sxs-lookup"><span data-stu-id="30259-127">Additionally, there is an implementation based on *TouchScreenKeyboard* in the [HandInteractionExamples scene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) of [MRTK](/windows/mixed-reality/mrtk-unity) (there is a keyboard interaction sample on the left hand side).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="30259-128">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="30259-128">Next Development Checkpoint</span></span>

<span data-ttu-id="30259-129">如果您正在遵循我們所配置的 Unity 開發旅程圖，您將會在探索混合現實平臺功能和 Api。</span><span class="sxs-lookup"><span data-stu-id="30259-129">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="30259-130">您可以從這裡繼續前往任何 [主題](unity-development-overview.md#3-advanced-features) ，或直接跳到在裝置或模擬器上部署您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="30259-130">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="30259-131">部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="30259-131">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
