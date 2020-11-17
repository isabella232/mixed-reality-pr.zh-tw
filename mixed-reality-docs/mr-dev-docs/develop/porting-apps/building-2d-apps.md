---
title: 針對混合現實更新 2D UWP 應用程式
description: 本文概述如何更新您現有的2D 通用 Windows 平臺應用程式，以在 HoloLens 和 Windows Mixed Reality 沉浸式耳機上執行。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 應用程式、UWP、平面應用程式、HoloLens、沉浸式耳機、應用程式模型、上一頁按鈕、應用程式行、DPI、解析度、縮放、移植、HoloLens 1 代、HoloLens 2、混合現實耳機、windows mixed reality 耳機、遷移、Windows 10
ms.openlocfilehash: 4103ee1e5a7169759dfd823b41b5e3fd18011956
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677797"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a><span data-ttu-id="7ce81-104">針對混合現實更新 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="7ce81-104">Updating 2D UWP apps for mixed reality</span></span>

<span data-ttu-id="7ce81-105">Windows Mixed Reality 可讓使用者在您的實體或數位世界中看到像是您一樣的全像投影。</span><span class="sxs-lookup"><span data-stu-id="7ce81-105">Windows Mixed Reality enables a user to see holograms as if they are right around you, in your physical or digital world.</span></span> <span data-ttu-id="7ce81-106">在其核心中，您將沉浸式耳機配件附加至的 HoloLens 和桌上型電腦都是 Windows 10 的裝置;這表示您可以在存放區中執行幾乎所有通用 Windows 平臺 (UWP) 應用程式作為2D 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-106">At its core, both HoloLens and the Desktop PCs you attach immersive headset accessories to are Windows 10 devices; this means that you're able to run almost all of the Universal Windows Platform (UWP) apps in the Store as 2D apps.</span></span>

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a><span data-ttu-id="7ce81-107">為混合的現實建立 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="7ce81-107">Creating a 2D UWP app for mixed reality</span></span>

<span data-ttu-id="7ce81-108">將2D 應用程式帶入混合現實耳機的第一個步驟，是讓您的應用程式在桌面監視器上以標準2D 應用程式的形式執行。</span><span class="sxs-lookup"><span data-stu-id="7ce81-108">The first step to bringing a 2D app to mixed reality headsets is to get your app running as a standard 2D app on your desktop monitor.</span></span>

### <a name="building-a-new-2d-uwp-app"></a><span data-ttu-id="7ce81-109">建立新的 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="7ce81-109">Building a new 2D UWP app</span></span>

<span data-ttu-id="7ce81-110">若要建立混合現實的新2D 應用程式，您只需建立標準2D 通用 Windows 平臺 (UWP) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-110">To build a new 2D app for mixed reality, you simply build a standard 2D Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="7ce81-111">應用程式不需要進行任何其他應用程式變更，就可以在混合現實中以平板的形式執行。</span><span class="sxs-lookup"><span data-stu-id="7ce81-111">No other app changes are required for that app to then run as a slate in mixed reality.</span></span>

<span data-ttu-id="7ce81-112">若要開始建立 2D UWP 應用程式，請參閱 [建立您的第一個應用程式](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) 文章。</span><span class="sxs-lookup"><span data-stu-id="7ce81-112">To get started building a 2D UWP app, check out the [Create your first app](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) article.</span></span>

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a><span data-ttu-id="7ce81-113">將現有的2D 存放區應用程式帶入 UWP</span><span class="sxs-lookup"><span data-stu-id="7ce81-113">Bringing an existing 2D Store app to UWP</span></span>

<span data-ttu-id="7ce81-114">如果您在存放區中已經有 2D Windows 應用程式，必須先確定它的目標是 Windows 10 通用 Windows 平臺 (UWP) 。</span><span class="sxs-lookup"><span data-stu-id="7ce81-114">If you already have a 2D Windows app in the Store, you must first ensure it is targeting the Windows 10 Universal Windows Platform (UWP).</span></span> <span data-ttu-id="7ce81-115">以下是您目前的 Store 應用程式可能會有的所有可能起點：</span><span class="sxs-lookup"><span data-stu-id="7ce81-115">Here are all the potential starting points you may have with your Store app today:</span></span>
<br>

|  <span data-ttu-id="7ce81-116">起點</span><span class="sxs-lookup"><span data-stu-id="7ce81-116">Starting Point</span></span>  |  <span data-ttu-id="7ce81-117">AppX 資訊清單平臺目標</span><span class="sxs-lookup"><span data-stu-id="7ce81-117">AppX Manifest Platform Target</span></span>  |  <span data-ttu-id="7ce81-118">如何將此通用？</span><span class="sxs-lookup"><span data-stu-id="7ce81-118">How to make this Universal?</span></span> | 
|----------|----------|----------|
|  <span data-ttu-id="7ce81-119">Windows Phone (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="7ce81-119">Windows Phone (Silverlight)</span></span>  |  <span data-ttu-id="7ce81-120">Silverlight 應用程式資訊清單</span><span class="sxs-lookup"><span data-stu-id="7ce81-120">Silverlight App Manifest</span></span> |  <span data-ttu-id="7ce81-121">[遷移至 WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span><span class="sxs-lookup"><span data-stu-id="7ce81-121">[Migrate to WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span></span> | 
|  <span data-ttu-id="7ce81-122">Windows Phone 8.1 通用</span><span class="sxs-lookup"><span data-stu-id="7ce81-122">Windows Phone 8.1 Universal</span></span>  |  <span data-ttu-id="7ce81-123">不包含平臺目標的 8.1 AppX 資訊清單</span><span class="sxs-lookup"><span data-stu-id="7ce81-123">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="7ce81-124">將您的應用程式遷移至通用 Windows 平臺</span><span class="sxs-lookup"><span data-stu-id="7ce81-124">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="7ce81-125">Windows Store 8</span><span class="sxs-lookup"><span data-stu-id="7ce81-125">Windows Store 8</span></span>  |  <span data-ttu-id="7ce81-126">8個不包含平臺目標的 AppX 資訊清單</span><span class="sxs-lookup"><span data-stu-id="7ce81-126">8 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="7ce81-127">將您的應用程式遷移至通用 Windows 平臺</span><span class="sxs-lookup"><span data-stu-id="7ce81-127">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="7ce81-128">Windows Store 8.1 通用</span><span class="sxs-lookup"><span data-stu-id="7ce81-128">Windows Store 8.1 Universal</span></span>  |  <span data-ttu-id="7ce81-129">不包含平臺目標的 8.1 AppX 資訊清單</span><span class="sxs-lookup"><span data-stu-id="7ce81-129">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="7ce81-130">將您的應用程式遷移至通用 Windows 平臺</span><span class="sxs-lookup"><span data-stu-id="7ce81-130">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 

<span data-ttu-id="7ce81-131">如果您現在以 Win32 應用程式的形式建立 2D Unity 應用程式 (「電腦、Mac & Linux 獨立」組建目標) ，您可以改為將 Unity 切換至「通用 Windows 平臺」組建目標，以將混合現實的目標設為目標。</span><span class="sxs-lookup"><span data-stu-id="7ce81-131">If you have a 2D Unity app today built as a Win32 app (the "PC, Mac & Linux Standalone" build target), you can target mixed reality by switching Unity to the "Universal Windows Platform" build target instead.</span></span>

<span data-ttu-id="7ce81-132">我們會討論您可以使用 [以下](#publish-and-maintain-your-universal-app)的 Windows 全像裝置系列，將您的應用程式明確限制為 HoloLens 的方式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-132">We'll talk about ways that you can restrict your app specifically to HoloLens using the Windows.Holographic device family [below](#publish-and-maintain-your-universal-app).</span></span>

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a><span data-ttu-id="7ce81-133">在 Windows Mixed Reality 沉浸式耳機中執行2D 應用程式</span><span class="sxs-lookup"><span data-stu-id="7ce81-133">Run your 2D app in a Windows Mixed Reality immersive headset</span></span>

<span data-ttu-id="7ce81-134">如果您已將2D 應用程式部署到您在監視器上開發和試用的桌上型電腦，您已經準備好在沉浸式桌面耳機中試用！</span><span class="sxs-lookup"><span data-stu-id="7ce81-134">If you've deployed your 2D app to the desktop machine where you are developing and tried it out on your monitor, you're already ready to try it out in an immersive desktop headset!</span></span>

<span data-ttu-id="7ce81-135">請移至混合現實耳機內的 [開始] 功能表，然後從該處啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-135">Just go to the Start menu within the mixed reality headset and launch the app from there.</span></span> <span data-ttu-id="7ce81-136">Desktop shell 和全像全像全像一樣，都共用一組 UWP 應用程式，因此當您從 Visual Studio 部署之後，應用程式應該就已經存在。</span><span class="sxs-lookup"><span data-stu-id="7ce81-136">The desktop shell and the holographic shell both share the same set of UWP apps, and so the app should already be present once you've deployed from Visual Studio.</span></span>

## <a name="targeting-both-immersive-headsets-and-hololens"></a><span data-ttu-id="7ce81-137">以沉浸式耳機和 HoloLens 為目標</span><span class="sxs-lookup"><span data-stu-id="7ce81-137">Targeting both immersive headsets and HoloLens</span></span>

<span data-ttu-id="7ce81-138">恭喜！</span><span class="sxs-lookup"><span data-stu-id="7ce81-138">Congratulations!</span></span> <span data-ttu-id="7ce81-139">您的應用程式現在使用 Windows 10 通用 Windows 平臺 (UWP) 。</span><span class="sxs-lookup"><span data-stu-id="7ce81-139">Your app is now using the Windows 10 Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="7ce81-140">您的應用程式現在可以在現今的 Windows 裝置上執行，例如桌面、行動、Xbox、Windows Mixed Reality 沉浸式耳機和 HoloLens，以及未來的 Windows 裝置。</span><span class="sxs-lookup"><span data-stu-id="7ce81-140">Your app is now capable of running on today's Windows devices like Desktop, Mobile, Xbox, Windows Mixed Reality immersive headsets, and HoloLens, as well as future Windows devices.</span></span> <span data-ttu-id="7ce81-141">不過，若要實際將所有裝置設為目標，您必須確定您的應用程式是以 Windows 通用裝置系列為目標。</span><span class="sxs-lookup"><span data-stu-id="7ce81-141">However, to actually target all of those devices, you will need to ensure your app is targeting the Windows.Universal device family.</span></span>

### <a name="change-your-device-family-to-windowsuniversal"></a><span data-ttu-id="7ce81-142">將您的裝置系列變更為 Windows 通用</span><span class="sxs-lookup"><span data-stu-id="7ce81-142">Change your device family to Windows.Universal</span></span>

<span data-ttu-id="7ce81-143">現在，讓我們跳到您的 AppX 資訊清單，以確保您的 Windows 10 UWP 應用程式可以在 HoloLens 上執行：</span><span class="sxs-lookup"><span data-stu-id="7ce81-143">Now let's jump into your AppX manifest to ensure your Windows 10 UWP app can run on HoloLens:</span></span>
* <span data-ttu-id="7ce81-144">使用 **Visual Studio** 開啟您的應用程式解決方案檔，然後流覽至應用程式套件資訊清單</span><span class="sxs-lookup"><span data-stu-id="7ce81-144">Open your app's solution file with **Visual Studio** and navigate to the app package manifest</span></span>
* <span data-ttu-id="7ce81-145">以滑鼠右鍵按一下方案中的 **package.appxmanifest** 檔案，然後移至 [ **View Code** ]</span><span class="sxs-lookup"><span data-stu-id="7ce81-145">Right click the **Package.appxmanifest** file in your Solution and go to **View Code**</span></span><br>
  <span data-ttu-id="7ce81-146">![方案總管中的 package.appxmanifest](images/openappxmanifest-500px.png)</span><span class="sxs-lookup"><span data-stu-id="7ce81-146">![package.appxmanifest in Solution Explorer](images/openappxmanifest-500px.png)</span></span><br>
* <span data-ttu-id="7ce81-147">確定您的目標平臺為 Windows 通用的 [相依性] 區段</span><span class="sxs-lookup"><span data-stu-id="7ce81-147">Ensure your Target Platform is Windows.Universal in the dependencies section</span></span>
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* <span data-ttu-id="7ce81-148">救！</span><span class="sxs-lookup"><span data-stu-id="7ce81-148">Save!</span></span>

<span data-ttu-id="7ce81-149">如果您沒有針對開發環境使用 Visual Studio，可以在您選擇的文字編輯器中開啟 **AppXManifest.xml** ，以確保您的目標是 **Windows 通用** *y*。</span><span class="sxs-lookup"><span data-stu-id="7ce81-149">If you do not use Visual Studio for your development environment, you can open **AppXManifest.xml** in the text editor of your choice to ensure you're targeting the **Windows.Universal** *TargetDeviceFamily*.</span></span>

### <a name="run-in-the-hololens-emulator"></a><span data-ttu-id="7ce81-150">在 HoloLens 模擬器中執行</span><span class="sxs-lookup"><span data-stu-id="7ce81-150">Run in the HoloLens Emulator</span></span>

<span data-ttu-id="7ce81-151">現在，您的 UWP 應用程式是以 "Windows 通用" 為目標，讓我們建立您的應用程式，並在 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)中執行它。</span><span class="sxs-lookup"><span data-stu-id="7ce81-151">Now that your UWP app targets "Windows.Universal", let's build your app and run it in the [HoloLens Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>
* <span data-ttu-id="7ce81-152">請確定您已 [安裝 HoloLens 模擬器](../install-the-tools.md) 。</span><span class="sxs-lookup"><span data-stu-id="7ce81-152">Make sure you have [installed the HoloLens Emulator](../install-the-tools.md).</span></span>
* <span data-ttu-id="7ce81-153">在 Visual Studio 中，選取應用程式的 **x86** 組建設定</span><span class="sxs-lookup"><span data-stu-id="7ce81-153">In Visual Studio, select the **x86** build configuration for your app</span></span>

  ![Visual Studio 中的 x86 組建設定](../platform-capabilities-and-apis/images/x86setting.png)<br>
* <span data-ttu-id="7ce81-155">在 [部署目標] 下拉式功能表中，選取 [HoloLens 模擬器] </span><span class="sxs-lookup"><span data-stu-id="7ce81-155">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span>

  ![部署目標清單中的 HoloLens 模擬器](images/deployemulator-500px.png)<br>
* <span data-ttu-id="7ce81-157">選取 [ **Debug] > 開始調試** 程式，以部署您的應用程式並啟動偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7ce81-157">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="7ce81-158">模擬器將會啟動並執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-158">The emulator will start and run your app.</span></span>
* <span data-ttu-id="7ce81-159">使用鍵盤、滑鼠及/或 Xbox 控制器，將您的應用程式放在世界中以啟動。</span><span class="sxs-lookup"><span data-stu-id="7ce81-159">With a keyboard, mouse, and/or an Xbox controller, place your app in the world to launch it.</span></span>

  ![使用 UWP 範例載入 HoloLens 模擬器](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a><span data-ttu-id="7ce81-161">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7ce81-161">Next steps</span></span>

<span data-ttu-id="7ce81-162">此時，可能會發生下列其中一種情況：</span><span class="sxs-lookup"><span data-stu-id="7ce81-162">At this point, one of two things can happen:</span></span>
1. <span data-ttu-id="7ce81-163">您的應用程式將會顯示它的啟動狀態，並在將它放置在模擬器之後開始執行！</span><span class="sxs-lookup"><span data-stu-id="7ce81-163">Your app will show its splash and start running after it is placed in the Emulator!</span></span> <span data-ttu-id="7ce81-164">好極了！</span><span class="sxs-lookup"><span data-stu-id="7ce81-164">Awesome!</span></span>
2. <span data-ttu-id="7ce81-165">或者，在您看到適用于2D 全息圖的載入動畫之後，載入將會停止，而且您只會在其啟動顯示畫面上看到您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-165">Or after you see a loading animation for a 2D hologram, loading will stop and you will just see your app at its splash screen.</span></span> <span data-ttu-id="7ce81-166">這表示發生了錯誤，且會進行更多調查，以瞭解如何讓您的應用程式在混合現實生活中保持存留。</span><span class="sxs-lookup"><span data-stu-id="7ce81-166">This means that something went wrong and it will take more investigation to understand how to bring your app to life in Mixed Reality.</span></span>

<span data-ttu-id="7ce81-167">若要深入瞭解可能導致 UWP 應用程式無法在 HoloLens 上啟動的原因，您必須進行調試。</span><span class="sxs-lookup"><span data-stu-id="7ce81-167">To get to the bottom of what may be causing your UWP app not to start on HoloLens, you'll have to debug.</span></span>

### <a name="running-your-uwp-app-in-the-debugger"></a><span data-ttu-id="7ce81-168">在偵錯工具中執行 UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="7ce81-168">Running your UWP app in the debugger</span></span>

<span data-ttu-id="7ce81-169">這些步驟將逐步引導您使用 Visual Studio 偵錯工具來偵測 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-169">These steps will walk you through debugging your UWP app using the Visual Studio debugger.</span></span>
* <span data-ttu-id="7ce81-170">如果您尚未這麼做，請在 Visual Studio 中開啟您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7ce81-170">If you haven't already done so, open your solution in Visual Studio.</span></span> <span data-ttu-id="7ce81-171">將目標變更為 **HoloLens 模擬器** ，並將組建設定變更為 **x86**。</span><span class="sxs-lookup"><span data-stu-id="7ce81-171">Change the target to the **HoloLens Emulator** and the build configuration to **x86**.</span></span>
* <span data-ttu-id="7ce81-172">選取 [ **Debug] > 開始調試** 程式，以部署您的應用程式並啟動偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7ce81-172">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="7ce81-173">使用滑鼠、鍵盤或 Xbox 控制器將應用程式放在世界各地。</span><span class="sxs-lookup"><span data-stu-id="7ce81-173">Place the app in the world with your mouse, keyboard, or Xbox controller.</span></span>
* <span data-ttu-id="7ce81-174">Visual Studio 現在應該會在應用程式程式碼中的某處中斷。</span><span class="sxs-lookup"><span data-stu-id="7ce81-174">Visual Studio should now break somewhere in your app code.</span></span>
  - <span data-ttu-id="7ce81-175">如果您的應用程式不會因為發生未處理的錯誤而立即損毀或中斷偵錯工具，則請進行應用程式核心功能的測試階段，以確定一切都在執行且正常運作。</span><span class="sxs-lookup"><span data-stu-id="7ce81-175">If your app doesn't immediately crash or break into the debugger because of an unhandled error, then go through a test pass of the core features of your app to make sure everything is running and functional.</span></span> <span data-ttu-id="7ce81-176">您可能會看到如下圖所示的錯誤 () 處理的內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7ce81-176">You may see errors like pictured below (internal exceptions that are being handled).</span></span> <span data-ttu-id="7ce81-177">為了確保您不會錯過影響應用程式體驗的內部錯誤，請執行您的自動化測試和單元測試，以確定一切都如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="7ce81-177">To ensure you don't miss internal errors that impact the experience of your app, run through your automated tests and unit tests to make sure everything behaves as expected.</span></span>

![使用 UWP 範例載入的 HoloLens 模擬器顯示系統例外狀況](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a><span data-ttu-id="7ce81-179">更新您的 UI</span><span class="sxs-lookup"><span data-stu-id="7ce81-179">Update your UI</span></span>

<span data-ttu-id="7ce81-180">現在您的 UWP 應用程式是以沉浸式耳機和/或 HoloLens 作為2D 全息圖來執行，接下來我們要確定它看起來美觀。</span><span class="sxs-lookup"><span data-stu-id="7ce81-180">Now that your UWP app is running on immersive headsets and/or HoloLens as a 2D hologram, next we'll make sure it looks beautiful.</span></span> <span data-ttu-id="7ce81-181">以下是要考量的一些事項：</span><span class="sxs-lookup"><span data-stu-id="7ce81-181">Here are some things to consider:</span></span>
* <span data-ttu-id="7ce81-182">Windows Mixed Reality 將會以固定的解析度和 DPI （相當於853x480 有效的圖元）執行所有2D 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-182">Windows Mixed Reality will run all 2D apps at a fixed resolution and DPI that equates to 853x480 effective pixels.</span></span> <span data-ttu-id="7ce81-183">請考慮您的設計是否需要依此規模進行調整，並查看下列設計指引，以改善您的 HoloLens 和沉浸式耳機體驗。</span><span class="sxs-lookup"><span data-stu-id="7ce81-183">Consider if your design needs refinement at this scale and review the design guidance below to improve your experience on HoloLens and immersive headsets.</span></span>
* <span data-ttu-id="7ce81-184">Windows Mixed Reality 不 [支援](../../design/app-model.md) 2d 動態磚。</span><span class="sxs-lookup"><span data-stu-id="7ce81-184">Windows Mixed Reality [does not support](../../design/app-model.md) 2D live tiles.</span></span> <span data-ttu-id="7ce81-185">如果您的核心功能顯示動態磚上的資訊，請考慮將該資訊移回您的應用程式，或探索 [3d 應用程式啟動器](../../distribute/3d-app-launcher-design-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce81-185">If your core functionality is showing information on a live tile, consider moving that information back into your app or explore [3D app launchers](../../distribute/3d-app-launcher-design-guidance.md).</span></span>

### <a name="2d-app-view-resolution-and-scale-factor"></a><span data-ttu-id="7ce81-186">2D 應用程式視圖解析度和縮放因數</span><span class="sxs-lookup"><span data-stu-id="7ce81-186">2D app view resolution and scale factor</span></span>

![從回應式設計](images/scale-500px.png)

<span data-ttu-id="7ce81-188">Windows 10 將所有視覺效果設計從真實螢幕圖元移至 **有效的圖元**。</span><span class="sxs-lookup"><span data-stu-id="7ce81-188">Windows 10 moves all visual design from real screen pixels to **effective pixels**.</span></span> <span data-ttu-id="7ce81-189">這表示，開發人員會依照 Windows 10 的人類介面指導方針來設計其 UI，以獲得有效的圖元，而 Windows 調整可確保這些有效的圖元在各裝置、解析度、DPI 等方面都是正確的大小。若要深入瞭解此[組建簡報](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)，請參閱[MSDN 上的這篇絕佳的閱讀](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7ce81-189">That means, developers design their UI following the Windows 10 Human Interface Guidelines for effective pixels, and Windows scaling ensures those effective pixels are the right size for usability across devices, resolutions, DPI, etc. See this [great read on MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) to learn more as well as this [BUILD presentation](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).</span></span>

<span data-ttu-id="7ce81-190">即使有獨特的能力可將世界各地的應用程式放在不同的距離，建議使用類似電視的觀賞距離，以產生最佳的可讀性，並與注視/手勢互動。</span><span class="sxs-lookup"><span data-stu-id="7ce81-190">Even with the unique ability to place apps in your world at a range of distances, TV-like viewing distances are recommended to produce the best readability and interaction with gaze/gesture.</span></span> <span data-ttu-id="7ce81-191">因此，Mixed Reality 首頁中的虛擬平板會在下列位置顯示您的平面 UWP 視圖：</span><span class="sxs-lookup"><span data-stu-id="7ce81-191">Because of that, a virtual slate in the Mixed Reality Home will display your flat UWP view at:</span></span>

<span data-ttu-id="7ce81-192">**1280x720，150% DPI** (853x480 有效圖元) </span><span class="sxs-lookup"><span data-stu-id="7ce81-192">**1280x720, 150%DPI** (853x480 effective pixels)</span></span>

<span data-ttu-id="7ce81-193">此解決方法有幾個優點：</span><span class="sxs-lookup"><span data-stu-id="7ce81-193">This resolution has several advantages:</span></span>
* <span data-ttu-id="7ce81-194">此有效的圖元配置將與 tablet 或 small desktop 具有相同的資訊密度。</span><span class="sxs-lookup"><span data-stu-id="7ce81-194">This effective pixel layout will have about the same information density as a tablet or small desktop.</span></span>
* <span data-ttu-id="7ce81-195">它會針對在 Xbox One 上執行的 UWP 應用程式，符合固定 DPI 和有效的圖元，讓裝置之間能無縫體驗。</span><span class="sxs-lookup"><span data-stu-id="7ce81-195">It matches the fixed DPI and effective pixels for UWP apps running on Xbox One, enabling seamless experiences across devices.</span></span>
* <span data-ttu-id="7ce81-196">當您在世界各地的應用程式之間調整規模時，此大小會良好。</span><span class="sxs-lookup"><span data-stu-id="7ce81-196">This size looks good when scaled across our range of operating distances for apps in the world.</span></span>

### <a name="2d-app-view-interface-design-best-practices"></a><span data-ttu-id="7ce81-197">2D 應用程式視圖介面設計最佳作法</span><span class="sxs-lookup"><span data-stu-id="7ce81-197">2D app view interface design best practices</span></span>

<span data-ttu-id="7ce81-198">**任務**</span><span class="sxs-lookup"><span data-stu-id="7ce81-198">**Do:**</span></span>
* <span data-ttu-id="7ce81-199">遵循 [Windows 10 的人體介面指導方針 (HIG) ](https://dev.windows.com/design) 樣式、字型大小和按鈕大小。</span><span class="sxs-lookup"><span data-stu-id="7ce81-199">Follow the [Windows 10 Human Interface Guidelines (HIG)](https://dev.windows.com/design) for styles, font sizes and button sizes.</span></span> <span data-ttu-id="7ce81-200">HoloLens 將會執行工作，以確保您的應用程式會有相容的應用程式模式、可讀取的文字大小，以及適當的點擊目標大小。</span><span class="sxs-lookup"><span data-stu-id="7ce81-200">HoloLens will do the work to ensure your app will have compatible app patterns, readable text sizes, and appropriate hit target sizing.</span></span>
* <span data-ttu-id="7ce81-201">確定您的 UI 遵循最佳作法，讓 [回應式設計](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) 在 HoloLen 的獨特解析度和 DPI 上看起來最佳。</span><span class="sxs-lookup"><span data-stu-id="7ce81-201">Ensure your UI follows best practices for [responsive design](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) to look best at HoloLen's unique resolution and DPI.</span></span>
* <span data-ttu-id="7ce81-202">使用來自 Windows 的「淺色」色彩主題建議。</span><span class="sxs-lookup"><span data-stu-id="7ce81-202">Use the "light" color theme recommendations from Windows.</span></span>

<span data-ttu-id="7ce81-203">**不要：**</span><span class="sxs-lookup"><span data-stu-id="7ce81-203">**Don't:**</span></span>
* <span data-ttu-id="7ce81-204">在混合的現實情況下變更您的 UI，以確保使用者在耳機中有熟悉的體驗。</span><span class="sxs-lookup"><span data-stu-id="7ce81-204">Change your UI too drastically when in mixed reality, to ensure users have a familiar experience in and out of the headset.</span></span>

### <a name="understand-the-app-model"></a><span data-ttu-id="7ce81-205">瞭解應用程式模型</span><span class="sxs-lookup"><span data-stu-id="7ce81-205">Understand the app model</span></span>

<span data-ttu-id="7ce81-206">混合現實的 [應用程式模型](../../design/app-model.md) 是設計用來使用混合現實首頁，其中許多應用程式會一起運作。</span><span class="sxs-lookup"><span data-stu-id="7ce81-206">The [app model](../../design/app-model.md) for mixed reality is designed to use the Mixed Reality Home, where many apps live together.</span></span> <span data-ttu-id="7ce81-207">您可以把它想成是桌上型電腦的混合現實，也就是一次執行許多2D 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-207">Think of this as the mixed reality equivalent of the desktop, where you run many 2D apps at once.</span></span> <span data-ttu-id="7ce81-208">這會影響應用程式的生命週期、圖格和其他重要功能。</span><span class="sxs-lookup"><span data-stu-id="7ce81-208">This has implications on app life cycle, Tiles, and other key features of your app.</span></span>

### <a name="app-bar-and-back-button"></a><span data-ttu-id="7ce81-209">應用程式行和上一頁按鈕</span><span class="sxs-lookup"><span data-stu-id="7ce81-209">App bar and back button</span></span>

<span data-ttu-id="7ce81-210">2D 視圖是以應用程式列在其內容之上裝飾。</span><span class="sxs-lookup"><span data-stu-id="7ce81-210">2D views are decorated with a app bar above their content.</span></span> <span data-ttu-id="7ce81-211">應用程式行有兩個應用程式特定的個人化點：</span><span class="sxs-lookup"><span data-stu-id="7ce81-211">The app bar has two points of app-specific personalization:</span></span>

<span data-ttu-id="7ce81-212">**標題：** 顯示與應用程式實例相關聯之磚的 *displayname*</span><span class="sxs-lookup"><span data-stu-id="7ce81-212">**Title:** displays the *displayname* of the Tile associated with the app instance</span></span>

<span data-ttu-id="7ce81-213">[**上一頁] 按鈕：** 按下時，會引發 *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 事件。</span><span class="sxs-lookup"><span data-stu-id="7ce81-213">**Back Button:** raises the *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* event when pressed.</span></span> <span data-ttu-id="7ce81-214">[上一頁] 按鈕可見度是由 *[SystemNavigationManager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* 所控制。</span><span class="sxs-lookup"><span data-stu-id="7ce81-214">Back Button visibility is controlled by *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*.</span></span>

<span data-ttu-id="7ce81-215">![2D 應用程式視圖中的應用程式行 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7ce81-215">![App bar UI in 2D app view](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span></span><br>
<span data-ttu-id="7ce81-216">*2D 應用程式視圖中的應用程式行 UI*</span><span class="sxs-lookup"><span data-stu-id="7ce81-216">*App bar UI in 2D app view*</span></span>

### <a name="test-your-2d-apps-design"></a><span data-ttu-id="7ce81-217">測試2D 應用程式的設計</span><span class="sxs-lookup"><span data-stu-id="7ce81-217">Test your 2D app's design</span></span>

<span data-ttu-id="7ce81-218">請務必測試您的應用程式，以確定文字可以讀取、按鈕目標設為，且整體應用程式看起來正確。</span><span class="sxs-lookup"><span data-stu-id="7ce81-218">It is important to test your app to make sure the text is readable, the buttons are targetable, and the overall app looks correct.</span></span> <span data-ttu-id="7ce81-219">您可以在桌上型耳機、HoloLens、模擬器，或解析度設定為1280x720% 的觸控裝置上進行 [測試](../platform-capabilities-and-apis/testing-your-app-on-hololens.md) @150 。</span><span class="sxs-lookup"><span data-stu-id="7ce81-219">You can [test](../platform-capabilities-and-apis/testing-your-app-on-hololens.md) on a desktop headset, a HoloLens, an emulator, or a touch device with resolution set to 1280x720 @150%.</span></span>

## <a name="new-input-possibilities"></a><span data-ttu-id="7ce81-220">新的輸入可能性</span><span class="sxs-lookup"><span data-stu-id="7ce81-220">New input possibilities</span></span>

<span data-ttu-id="7ce81-221">HoloLens 使用 advanced depth 感應器來查看世界並查看使用者。</span><span class="sxs-lookup"><span data-stu-id="7ce81-221">HoloLens uses advanced depth sensors to see the world and see users.</span></span> <span data-ttu-id="7ce81-222">這可啟用先進手勢，例如 [bloom](../../design/system-gesture.md#bloom) 和 [敲擊](../../design/gaze-and-commit.md#composite-gestures)。</span><span class="sxs-lookup"><span data-stu-id="7ce81-222">This enables advanced hand gestures like [bloom](../../design/system-gesture.md#bloom) and [air-tap](../../design/gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="7ce81-223">強大的麥克風也可以提供 [語音體驗](../../design/voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce81-223">Powerful microphones also enable [voice experiences](../../design/voice-input.md).</span></span>

<span data-ttu-id="7ce81-224">使用桌上型耳機時，使用者可以使用移動控制器來指向應用程式並採取動作。</span><span class="sxs-lookup"><span data-stu-id="7ce81-224">With Desktop headsets, users can use motion controllers to point at apps and take action.</span></span> <span data-ttu-id="7ce81-225">他們也可以使用遊戲台，以物件作為其注視。</span><span class="sxs-lookup"><span data-stu-id="7ce81-225">They can also use a gamepad, targeting objects with their gaze.</span></span>

<span data-ttu-id="7ce81-226">Windows 會為 UWP 應用程式處理這種複雜性，並將您的 [注視](../../design/gaze-and-commit.md)、手勢、語音和動作控制器輸入轉譯為可抽象化輸入機制的 [指標事件](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) 。</span><span class="sxs-lookup"><span data-stu-id="7ce81-226">Windows takes care of all of this complexity for UWP apps, translating your [gaze](../../design/gaze-and-commit.md), gestures, voice and motion controller input to [pointer events](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) that abstract away the input mechanism.</span></span> <span data-ttu-id="7ce81-227">比方說，使用者可能已在移動控制站上使用手或提取 Select 觸發程式，但是2D 應用程式不需要知道輸入的來源-它們只會看到2D 觸控按，如同在觸控式螢幕上一樣。</span><span class="sxs-lookup"><span data-stu-id="7ce81-227">For example, a user may have done an air-tap with their hand or pulled the Select trigger on a motion controller, but 2D applications don't need to know where the input came from - they just see a 2D touch press, as if on a touchscreen.</span></span>

<span data-ttu-id="7ce81-228">以下是將 UWP 應用程式帶入 HoloLens 時，應瞭解輸入的高階概念/案例：</span><span class="sxs-lookup"><span data-stu-id="7ce81-228">Here are the high level concepts/scenarios you should understand for input when bringing your UWP app to HoloLens:</span></span>
* <span data-ttu-id="7ce81-229">[Gaze](../../design/gaze-and-commit.md)您可以透過在應用程式周圍撥雲見日，以非預期地觸發功能表、flyouts 或其他使用者介面元素，來切換到暫止事件。</span><span class="sxs-lookup"><span data-stu-id="7ce81-229">[Gaze](../../design/gaze-and-commit.md) turns into hover events, which can unexpectedly trigger menus, flyouts or other user interface elements to pop up just by gazing around your app.</span></span>
* <span data-ttu-id="7ce81-230">注視不像滑鼠輸入一樣精確。</span><span class="sxs-lookup"><span data-stu-id="7ce81-230">Gaze is not as precise as mouse input.</span></span> <span data-ttu-id="7ce81-231">針對 HoloLens 使用適當大小的點擊目標，類似于便於觸控的行動應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ce81-231">Use appropriately sized hit targets for HoloLens, similar to touch-friendly mobile applications.</span></span> <span data-ttu-id="7ce81-232">接近應用程式邊緣的小元素，特別難以與互動。</span><span class="sxs-lookup"><span data-stu-id="7ce81-232">Small elements near the edges of the app are especially hard to interact with.</span></span>
* <span data-ttu-id="7ce81-233">使用者必須切換輸入模式，才能從滾動至拖曳至兩個手指移動。</span><span class="sxs-lookup"><span data-stu-id="7ce81-233">Users must switch input modes to go from scrolling to dragging to two finger panning.</span></span> <span data-ttu-id="7ce81-234">如果您的應用程式是針對觸控輸入而設計，請考慮確定不會在兩個手指移動之後鎖定任何主要功能。</span><span class="sxs-lookup"><span data-stu-id="7ce81-234">If your app was designed for touch input, consider ensuring that no major functionality is locked behind two finger panning.</span></span> <span data-ttu-id="7ce81-235">若是如此，請考慮採用替代輸入機制，例如可起始兩個手指移動的按鈕。</span><span class="sxs-lookup"><span data-stu-id="7ce81-235">If so, consider having alternative input mechanisms like buttons that can initiate two finger panning.</span></span> <span data-ttu-id="7ce81-236">例如，地圖應用程式可以使用兩個手指移動來縮放，但是有加號、減號和旋轉按鈕，只要按一下就能模擬相同的縮放互動。</span><span class="sxs-lookup"><span data-stu-id="7ce81-236">For example, the Maps app can zoom with two finger panning but has a plus, minus, and rotate button to simulate the same zoom interactions with single clicks.</span></span>

<span data-ttu-id="7ce81-237">[語音輸入](../../design/voice-input.md) 是混合現實體驗的重要部分。</span><span class="sxs-lookup"><span data-stu-id="7ce81-237">[Voice input](../../design/voice-input.md) is a critical part of the mixed reality experience.</span></span> <span data-ttu-id="7ce81-238">我們已啟用在使用耳機時，Windows 10 為 Cortana 提供的所有語音 Api。</span><span class="sxs-lookup"><span data-stu-id="7ce81-238">We've enabled all of the speech APIs that are in Windows 10 powering Cortana when using a headset.</span></span>

## <a name="publish-and-maintain-your-universal-app"></a><span data-ttu-id="7ce81-239">發佈和維護您的通用應用程式</span><span class="sxs-lookup"><span data-stu-id="7ce81-239">Publish and Maintain your Universal app</span></span>

<span data-ttu-id="7ce81-240">當您的應用程式啟動並執行之後，請封裝您的應用程式，以將 [它提交至 Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce81-240">Once your app is up and running, package your app to [submit it to the Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ce81-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ce81-241">See also</span></span>
* [<span data-ttu-id="7ce81-242">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="7ce81-242">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="7ce81-243">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="7ce81-243">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="7ce81-244">運動控制器</span><span class="sxs-lookup"><span data-stu-id="7ce81-244">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="7ce81-245">語音輸入</span><span class="sxs-lookup"><span data-stu-id="7ce81-245">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="7ce81-246">將應用程式提交到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="7ce81-246">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="7ce81-247">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="7ce81-247">Using the HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
