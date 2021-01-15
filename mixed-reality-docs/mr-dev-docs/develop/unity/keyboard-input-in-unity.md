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
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="90866-104">Unity 中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="90866-104">Keyboard input in Unity</span></span>

<span data-ttu-id="90866-105">**命名空間：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="90866-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="90866-106">**類型**： *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="90866-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="90866-107">雖然 HoloLens 支援許多形式的輸入，包括 Bluetooth 鍵盤，但大部分的應用程式都無法假設所有使用者都有可用的實體鍵盤。</span><span class="sxs-lookup"><span data-stu-id="90866-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="90866-108">如果您的應用程式需要文字輸入，則應該提供某種形式的螢幕小鍵盤。</span><span class="sxs-lookup"><span data-stu-id="90866-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="90866-109">Unity 提供 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 類別，可在沒有可用的實體鍵盤時接受鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="90866-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="90866-110">在 Unity 中的 HoloLens 系統鍵盤行為</span><span class="sxs-lookup"><span data-stu-id="90866-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="90866-111">在 HoloLens 上， *TouchScreenKeyboard* 會利用系統的螢幕小鍵盤。</span><span class="sxs-lookup"><span data-stu-id="90866-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard.</span></span> <span data-ttu-id="90866-112">系統的螢幕小鍵盤無法在體積型 view 上方重迭。</span><span class="sxs-lookup"><span data-stu-id="90866-112">The system's on-screen keyboard can't overlay on top of a volumetric view.</span></span> <span data-ttu-id="90866-113">Unity 必須建立次要 2D XAML 視圖來顯示鍵盤，然後在送出輸入後回到體積型 view。</span><span class="sxs-lookup"><span data-stu-id="90866-113">Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="90866-114">使用者流程如下所示：</span><span class="sxs-lookup"><span data-stu-id="90866-114">The user flow goes like this:</span></span>
1. <span data-ttu-id="90866-115">使用者執行的動作會導致應用程式程式碼呼叫 *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="90866-115">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="90866-116">應用程式會負責暫停應用程式狀態，然後再呼叫 *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="90866-116">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="90866-117">應用程式可能會在切換回體積型視圖之前終止</span><span class="sxs-lookup"><span data-stu-id="90866-117">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="90866-118">Unity 切換至世界上 autoplaced 的 2D XAML 視圖</span><span class="sxs-lookup"><span data-stu-id="90866-118">Unity switches to a 2D XAML view, which is autoplaced in the world</span></span>
3. <span data-ttu-id="90866-119">使用者使用系統鍵盤輸入文字，並提交或取消</span><span class="sxs-lookup"><span data-stu-id="90866-119">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="90866-120">Unity 切換回體積型視圖</span><span class="sxs-lookup"><span data-stu-id="90866-120">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="90866-121">*TouchScreenKeyboard* 完成時，應用程式會負責繼續應用程式狀態</span><span class="sxs-lookup"><span data-stu-id="90866-121">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="90866-122">提交的文字可在 *TouchScreenKeyboard* 中取得</span><span class="sxs-lookup"><span data-stu-id="90866-122">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="90866-123">可用的鍵盤流覽</span><span class="sxs-lookup"><span data-stu-id="90866-123">Available keyboard views</span></span>

<span data-ttu-id="90866-124">有六個不同的鍵盤視圖可用：</span><span class="sxs-lookup"><span data-stu-id="90866-124">There are six different keyboard views available:</span></span>
* <span data-ttu-id="90866-125">單行文字方塊</span><span class="sxs-lookup"><span data-stu-id="90866-125">Single-line textbox</span></span>
* <span data-ttu-id="90866-126">包含標題的單行 textbox</span><span class="sxs-lookup"><span data-stu-id="90866-126">Single-line textbox with title</span></span>
* <span data-ttu-id="90866-127">多行文字方塊</span><span class="sxs-lookup"><span data-stu-id="90866-127">Multi-line textbox</span></span>
* <span data-ttu-id="90866-128">具有標題的多行文字方塊</span><span class="sxs-lookup"><span data-stu-id="90866-128">Multi-line textbox with title</span></span>
* <span data-ttu-id="90866-129">單行密碼方塊</span><span class="sxs-lookup"><span data-stu-id="90866-129">Single-line password box</span></span>
* <span data-ttu-id="90866-130">具有標題的單行密碼方塊</span><span class="sxs-lookup"><span data-stu-id="90866-130">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="90866-131">如何在 Unity 中啟用系統鍵盤</span><span class="sxs-lookup"><span data-stu-id="90866-131">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="90866-132">HoloLens 系統鍵盤僅適用于使用 [UWP 組建類型] 設定為 [XAML] 匯出的 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="90866-132">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="90866-133">當您選擇 "XAML" 作為 "D3D" 的「UWP 組建類型」時，會產生取捨。</span><span class="sxs-lookup"><span data-stu-id="90866-133">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="90866-134">如果您不熟悉這些取捨，您可能想要探索系統鍵盤的 [替代輸入解決方案](#alternative-keyboard-options) 。</span><span class="sxs-lookup"><span data-stu-id="90866-134">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="90866-135">開啟 [**檔案] 功能表，然後** 選取 [**組建設定 ...** ]。</span><span class="sxs-lookup"><span data-stu-id="90866-135">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="90866-136">確定 **平臺** 已設定為 **Windows Store**、 **SDK** 設定為 **通用 10**，然後將 **UWP 組建類型** 設定為 **XAML**。</span><span class="sxs-lookup"><span data-stu-id="90866-136">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="90866-137">在 [ **組建設定** ] 對話方塊中，選取 [ **播放機設定 ...** ] 按鈕</span><span class="sxs-lookup"><span data-stu-id="90866-137">In the **Build Settings** dialog, select the **Player Settings...** button</span></span>
4. <span data-ttu-id="90866-138">選取 **Windows [存放區** ] 索引標籤的設定</span><span class="sxs-lookup"><span data-stu-id="90866-138">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="90866-139">展開 [ **其他設定** ] 群組</span><span class="sxs-lookup"><span data-stu-id="90866-139">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="90866-140">**在 [轉譯] 區段中**，核取 [**支援虛擬實境**] 核取方塊以新增 **虛擬實境裝置** 清單</span><span class="sxs-lookup"><span data-stu-id="90866-140">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="90866-141">確定 **Windows 全息** 版出現在虛擬實境 sdk 清單中</span><span class="sxs-lookup"><span data-stu-id="90866-141">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="90866-142">如果您未將組建標示為 HoloLens 裝置支援的虛擬實境，此專案會匯出為 2D XAML 應用程式。</span><span class="sxs-lookup"><span data-stu-id="90866-142">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="90866-143">在 Unity 應用程式中使用系統鍵盤</span><span class="sxs-lookup"><span data-stu-id="90866-143">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="90866-144">宣告鍵盤</span><span class="sxs-lookup"><span data-stu-id="90866-144">Declare the keyboard</span></span>

<span data-ttu-id="90866-145">在類別中，宣告變數來儲存 *TouchScreenKeyboard* 和變數，以保存鍵盤所傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="90866-145">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="90866-146">叫用鍵盤</span><span class="sxs-lookup"><span data-stu-id="90866-146">Invoke the keyboard</span></span>

<span data-ttu-id="90866-147">當要求鍵盤輸入的事件發生時，請根據您想要在 textPlaceholder 參數中使用標題的輸入類型，呼叫其中一個函式。</span><span class="sxs-lookup"><span data-stu-id="90866-147">When an event occurs requesting keyboard input, call one of these functions depending on the type of input you want using the title in the textPlaceholder parameter.</span></span>

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

### <a name="retrieve-typed-contents"></a><span data-ttu-id="90866-148">取出具類型的內容</span><span class="sxs-lookup"><span data-stu-id="90866-148">Retrieve typed contents</span></span>

<span data-ttu-id="90866-149">在更新迴圈中，檢查鍵盤是否已收到新的輸入，並將其儲存供其他地方使用。</span><span class="sxs-lookup"><span data-stu-id="90866-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

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

## <a name="alternative-keyboard-options"></a><span data-ttu-id="90866-150">替代鍵盤選項</span><span class="sxs-lookup"><span data-stu-id="90866-150">Alternative keyboard options</span></span>

<span data-ttu-id="90866-151">我們瞭解將體積型視圖切換至2D 視圖不是從使用者取得文字輸入的理想方式。</span><span class="sxs-lookup"><span data-stu-id="90866-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="90866-152">透過 Unity 利用系統鍵盤的最新替代方案包括：</span><span class="sxs-lookup"><span data-stu-id="90866-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="90866-153">針對輸入使用語音聽寫 (<b>注意：</b> 這通常是因為在字典中找不到且不適合密碼輸入的單字所造成的錯誤) </span><span class="sxs-lookup"><span data-stu-id="90866-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and isn't suitable for password entry)</span></span>
* <span data-ttu-id="90866-154">建立可在您的應用程式專屬視圖中運作的鍵盤</span><span class="sxs-lookup"><span data-stu-id="90866-154">Create a keyboard that works in your applications exclusive view</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="90866-155">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="90866-155">Next Development Checkpoint</span></span>

<span data-ttu-id="90866-156">如果您正在遵循我們所配置的 Unity 開發旅程圖，您將會在探索混合現實平臺功能和 Api。</span><span class="sxs-lookup"><span data-stu-id="90866-156">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="90866-157">您可以從這裡繼續前往任何 [主題](unity-development-overview.md#3-advanced-features) ，或直接跳到在裝置或模擬器上部署您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="90866-157">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="90866-158">部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="90866-158">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
