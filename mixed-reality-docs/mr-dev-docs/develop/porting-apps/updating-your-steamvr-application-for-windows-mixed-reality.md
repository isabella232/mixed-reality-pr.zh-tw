---
title: 更新您的 SteamVR 應用程式
description: 更新 SteamVR 應用程式，以充分利用 Windows Mixed Reality 耳機進行相容性的最佳做法。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR，相容性
ms.openlocfilehash: 4a1439bed8743396cba13fa4d65debc62487ab46
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638504"
---
# <a name="updating-your-steamvr-application"></a><span data-ttu-id="93f99-104">更新您的 SteamVR 應用程式</span><span class="sxs-lookup"><span data-stu-id="93f99-104">Updating your SteamVR application</span></span>
<span data-ttu-id="93f99-105">我們鼓勵開發人員測試 SteamVR 體驗，並將其優化，以在 Windows Mixed Reality 耳機上執行。</span><span class="sxs-lookup"><span data-stu-id="93f99-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="93f99-106">本檔涵蓋開發人員可進行的一般改進，以確保他們的體驗在 Windows Mixed Reality 上執行得很棒。</span><span class="sxs-lookup"><span data-stu-id="93f99-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="93f99-107">初始安裝指示</span><span class="sxs-lookup"><span data-stu-id="93f99-107">Initial setup instructions</span></span>

<span data-ttu-id="93f99-108">若要開始在 Windows Mixed Reality 上測試您的遊戲或應用程式，請務必先遵循我們的 [快速入門手冊。](https://aka.ms/WindowsMixedRealitySteamVR)</span><span class="sxs-lookup"><span data-stu-id="93f99-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](https://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="93f99-109">控制器模型</span><span class="sxs-lookup"><span data-stu-id="93f99-109">Controller Models</span></span>
1. <span data-ttu-id="93f99-110">如果您的應用程式呈現控制器模型：</span><span class="sxs-lookup"><span data-stu-id="93f99-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="93f99-111">使用 [Windows Mixed Reality 運動控制器模型](../../design/motion-controllers.md#rendering-the-motion-controller-model)</span><span class="sxs-lookup"><span data-stu-id="93f99-111">Use the [Windows Mixed Reality motion controller models](../../design/motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="93f99-112">使用 IVRRenderModel：： GetComponentState 來取得元件部分的本機轉換 (例如</span><span class="sxs-lookup"><span data-stu-id="93f99-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="93f99-113">指標姿勢) </span><span class="sxs-lookup"><span data-stu-id="93f99-113">Pointer pose)</span></span>
2. <span data-ttu-id="93f99-114">具有 handedness 概念的體驗應從輸入 Api 取得提示，以區分控制器 [ (Unity 範例) ](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="93f99-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="93f99-115">控制項</span><span class="sxs-lookup"><span data-stu-id="93f99-115">Controls</span></span>

<span data-ttu-id="93f99-116">設計或調整控制項版面配置時，請記住下列保留的命令集：</span><span class="sxs-lookup"><span data-stu-id="93f99-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="93f99-117">按一下向下 **和向右類比操縱杆** 會保留給 **流儀表板** 。</span><span class="sxs-lookup"><span data-stu-id="93f99-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard** .</span></span>

> [!NOTE]
> <span data-ttu-id="93f99-118">如果您使用的是「HP 回音」 G2 控制器，則按一下右邊的功能表按鈕會保留給「 **流」儀表板** 。</span><span class="sxs-lookup"><span data-stu-id="93f99-118">If you're using an HP Reverb G2 controller, clicking the right menu button is reserved for the **Steam Dashboard** .</span></span>

2. <span data-ttu-id="93f99-119">**Windows 按鈕** 一律會將使用者傳回到 Windows Mixed Reality 首頁。</span><span class="sxs-lookup"><span data-stu-id="93f99-119">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="93f99-120">可能的話，預設為以 thumb 為基礎的遙傳，以符合 [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 遙傳行為</span><span class="sxs-lookup"><span data-stu-id="93f99-120">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="93f99-121">工具提示和 UI</span><span class="sxs-lookup"><span data-stu-id="93f99-121">Tooltips and UI</span></span>

<span data-ttu-id="93f99-122">許多的 VR 遊戲都利用移動控制器工具提示和覆迭，來告訴使用者他們的遊戲或應用程式最重要的命令。</span><span class="sxs-lookup"><span data-stu-id="93f99-122">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="93f99-123">當您調整應用程式的 Windows Mixed reality 時，建議您複習這部分的體驗，以確定工具提示會對應到 Windows 控制器模型。</span><span class="sxs-lookup"><span data-stu-id="93f99-123">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="93f99-124">此外，如果您的體驗中有任何點顯示控制器影像，請務必使用 Windows Mixed Reality 的動作控制器來提供更新的影像。</span><span class="sxs-lookup"><span data-stu-id="93f99-124">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="93f99-125">Haptics</span><span class="sxs-lookup"><span data-stu-id="93f99-125">Haptics</span></span>

<span data-ttu-id="93f99-126">從 [Windows 10 2018 年4月更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)開始，現在支援在 Windows Mixed Reality 上使用 Haptics 的 SteamVR 體驗。</span><span class="sxs-lookup"><span data-stu-id="93f99-126">Beginning with the [Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="93f99-127">如果您的 SteamVR 應用程式或遊戲已包含對 haptics 的支援，現在應該就能 (與 Windows Mixed Reality 的 [動作控制器](../../design/motion-controllers.md)沒有額外的工作) 。</span><span class="sxs-lookup"><span data-stu-id="93f99-127">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](../../design/motion-controllers.md).</span></span>

<span data-ttu-id="93f99-128">Windows Mixed Reality 移動控制器使用標準 haptics 馬達，而不是在其他某些 SteamVR 運動控制器中找到的線性傳動器，這可能會導致與預期的使用者體驗稍微不同。</span><span class="sxs-lookup"><span data-stu-id="93f99-128">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="93f99-129">因此，我們建議您使用 Windows Mixed Reality 的動作控制器來測試及調整您的 haptics 設計。</span><span class="sxs-lookup"><span data-stu-id="93f99-129">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="93f99-130">例如，有時候短 haptic 脈衝 (5-10 ms) 在 Windows Mixed Reality 的移動控制器上比較不明顯。</span><span class="sxs-lookup"><span data-stu-id="93f99-130">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="93f99-131">若要產生更顯著的脈衝，請試著傳送較長的「按一下」 (40 70ms) ，讓馬達更多時間啟動，然後再被告知電源關閉。</span><span class="sxs-lookup"><span data-stu-id="93f99-131">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="93f99-132">從 Windows Mixed Reality [開始] 功能表啟動 SteamVR 應用程式</span><span class="sxs-lookup"><span data-stu-id="93f99-132">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="93f99-133">針對透過串流散發的 VR 體驗，我們已 [更新 SteamVR Beta 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) ，以及最新的 [Windows 測試人員](https://insider.windows.com) RS5 航班，讓 SteamVR 標題現在會自動顯示在 [所有應用程式] 清單的 Windows Mixed Reality [開始] 功能表中。</span><span class="sxs-lookup"><span data-stu-id="93f99-133">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="93f99-134">安裝這些軟體版本之後，您的客戶現在可以直接從 Windows Mixed Reality 首頁內啟動 SteamVR 標題，而不需要移除其耳機。</span><span class="sxs-lookup"><span data-stu-id="93f99-134">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="93f99-135">Windows Mixed Reality 標誌</span><span class="sxs-lookup"><span data-stu-id="93f99-135">Windows Mixed Reality logo</span></span>

<span data-ttu-id="93f99-136">若要顯示標題的 Windows Mixed Reality 支援，請移至應用程式登陸頁面上的 [編輯存放區] 頁面，按一下 [基本資訊] 索引標籤，並向下移至 [虛擬實境]。</span><span class="sxs-lookup"><span data-stu-id="93f99-136">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="93f99-137">取消核取 [隱藏 Windows Mixed Reality]，然後發佈至存放區。</span><span class="sxs-lookup"><span data-stu-id="93f99-137">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="93f99-138">Bug 和意見反應</span><span class="sxs-lookup"><span data-stu-id="93f99-138">Bugs and feedback</span></span>

<span data-ttu-id="93f99-139">在改善 Windows Mixed Reality SteamVR 體驗時，您的意見反應非常寶貴。</span><span class="sxs-lookup"><span data-stu-id="93f99-139">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="93f99-140">請透過 [Windows 意見反應中樞](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)提交所有意見反應和 bug。</span><span class="sxs-lookup"><span data-stu-id="93f99-140">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="93f99-141">以下是一些有關 [如何讓您的 SteamVR 意見反應更有説明的秘訣](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)。</span><span class="sxs-lookup"><span data-stu-id="93f99-141">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="93f99-142">如果您有任何問題或意見可以共用，您也可以在我們的串流 [論壇](https://steamcommunity.com/app/719950/discussions/)上聯繫我們。</span><span class="sxs-lookup"><span data-stu-id="93f99-142">If you have questions or comments to share, you can also reach us on our [Steam forum](https://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="93f99-143">常見問題和疑難排解</span><span class="sxs-lookup"><span data-stu-id="93f99-143">FAQs and troubleshooting</span></span>

<span data-ttu-id="93f99-144">如果您遇到設定或播放體驗的一般問題，請 [參閱最新的疑難排解步驟](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。</span><span class="sxs-lookup"><span data-stu-id="93f99-144">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="93f99-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93f99-145">See also</span></span>
* [<span data-ttu-id="93f99-146">安裝工具</span><span class="sxs-lookup"><span data-stu-id="93f99-146">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="93f99-147">耳機和移動控制器驅動程式歷程記錄</span><span class="sxs-lookup"><span data-stu-id="93f99-147">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="93f99-148">Windows Mixed Reality 最小電腦硬體相容性指導方針</span><span class="sxs-lookup"><span data-stu-id="93f99-148">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
