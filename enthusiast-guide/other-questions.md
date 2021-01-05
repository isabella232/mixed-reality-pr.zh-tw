---
title: 其他問題
description: 其他 Windows Mixed Reality 超越標準取用者支援檔的疑難排解秘訣。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援、卸載 Windows Mixed Reality、支援的語言
appliesto:
- Windows 10
ms.openlocfilehash: cf23d52fc72fa3b499b32d3770151306111afaa4
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726009"
---
# <a name="other-questions"></a><span data-ttu-id="01da2-104">其他問題</span><span class="sxs-lookup"><span data-stu-id="01da2-104">Other questions</span></span>

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a><span data-ttu-id="01da2-105">我的圖形驅動程式不受支援 (我收到圖形驅動程式失敗錯誤) 。</span><span class="sxs-lookup"><span data-stu-id="01da2-105">My graphics driver isn't supported (I'm getting graphics driver failure errors).</span></span>

<span data-ttu-id="01da2-106">搜尋並執行 "dxdiag"：</span><span class="sxs-lookup"><span data-stu-id="01da2-106">Search for and run "dxdiag":</span></span>

1.  <span data-ttu-id="01da2-107">如果結果為「基本轉譯器」，則不會安裝圖形驅動程式。</span><span class="sxs-lookup"><span data-stu-id="01da2-107">If the result is “Basic Renderer”, the graphics driver isn't installed.</span></span> <span data-ttu-id="01da2-108">修正方法：</span><span class="sxs-lookup"><span data-stu-id="01da2-108">To fix this:</span></span>
    * <span data-ttu-id="01da2-109">移至 **裝置管理員 > 動作 > 掃描硬體變更**。</span><span class="sxs-lookup"><span data-stu-id="01da2-109">Go to **Device Manager > Action > Scan for Hardware Changes**.</span></span>
    * <span data-ttu-id="01da2-110">使用 Windows Update 來更新驅動程式。</span><span class="sxs-lookup"><span data-stu-id="01da2-110">Use Windows Update to update the driver.</span></span>
    * <span data-ttu-id="01da2-111">如果這無法解決問題，請移至製造商的網站，並安裝最新的驅動程式更新。</span><span class="sxs-lookup"><span data-stu-id="01da2-111">If this doesn't fix the problem, go to the manufacturer’s website and install the latest driver update.</span></span> 
    * <span data-ttu-id="01da2-112">如果您的 GPU 無法使用更新，您的裝置可能不支援 WMR。</span><span class="sxs-lookup"><span data-stu-id="01da2-112">If an update isn't available for your GPU, WMR may not be supported on your device.</span></span> <span data-ttu-id="01da2-113">如果您認為應該如此，請聯絡 [支援](https://support.microsoft.com)人員。</span><span class="sxs-lookup"><span data-stu-id="01da2-113">If you think it should be, contact [support](https://support.microsoft.com).</span></span>
2.  <span data-ttu-id="01da2-114">如果您收到「WDDM 2.1」或較舊的版本，則會安裝圖形驅動程式，但它可能不是最新版本。</span><span class="sxs-lookup"><span data-stu-id="01da2-114">If you get a “WDDM 2.1” or lower version, the graphics driver is installed but it might not be the latest version.</span></span> <span data-ttu-id="01da2-115">若要取得最新版本：</span><span class="sxs-lookup"><span data-stu-id="01da2-115">To get the latest version:</span></span>
    * <span data-ttu-id="01da2-116">使用 Windows Update 來更新驅動程式。</span><span class="sxs-lookup"><span data-stu-id="01da2-116">Use Windows Update to update the driver.</span></span>
    * <span data-ttu-id="01da2-117">如果該更新無法修正問題，請移至製造商的網站，並安裝最新的驅動程式更新。</span><span class="sxs-lookup"><span data-stu-id="01da2-117">If that update doesn't fix the problem, go to the manufacturer’s website and install the latest driver update.</span></span> 
    * <span data-ttu-id="01da2-118">如果您的 GPU 無法使用更新，您的裝置可能不支援 WMR。</span><span class="sxs-lookup"><span data-stu-id="01da2-118">If an update isn't available for your GPU, WMR may not be supported on your device.</span></span> <span data-ttu-id="01da2-119">如果您認為應該如此，請聯絡 [支援](https://support.microsoft.com)人員。</span><span class="sxs-lookup"><span data-stu-id="01da2-119">If you think it should be, contact [support](https://support.microsoft.com).</span></span>

<span data-ttu-id="01da2-120">如果 Windows Mixed Reality 安裝程式指出您的圖形配接器不符合需求，而您認為它的確如此，請確定您的耳機已插入正確的卡片中。</span><span class="sxs-lookup"><span data-stu-id="01da2-120">If Windows Mixed Reality setup says your graphics card doesn’t meet the requirements and you think it does, make sure your headset is plugged into the correct card.</span></span>

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a><span data-ttu-id="01da2-121">我的 Samsung 電影對白或電影對白 + 耳機固件更新停滯。</span><span class="sxs-lookup"><span data-stu-id="01da2-121">My Samsung Odyssey or Odyssey+ headset firmware update is stuck.</span></span>

<span data-ttu-id="01da2-122">Samsung 擁有併發布透過其 "Samsung HMD 電影對白 Setup" 和 "Samsung HMD 電影對白 + Setup" 裝置附屬應用程式所提供的耳機固件更新。</span><span class="sxs-lookup"><span data-stu-id="01da2-122">Samsung owns and publishes headset firmware updates delivered via their "Samsung HMD Odyssey Setup" and "Samsung HMD Odyssey+ Setup" device companion apps.</span></span> <span data-ttu-id="01da2-123">如需有關 Samsung 固件更新問題的詳細資訊和協助，請聯絡 Samsung customer service。</span><span class="sxs-lookup"><span data-stu-id="01da2-123">For more details and for help with Samsung firmware update issues, contact Samsung customer service.</span></span>

<span data-ttu-id="01da2-124">如果固件更新程式停滯，而且沒有超過五分鐘的進度：</span><span class="sxs-lookup"><span data-stu-id="01da2-124">If the firmware update process is getting stuck, and there has been no progress for more than five minutes:</span></span>

* <span data-ttu-id="01da2-125">暫時拔掉所有其他 USB 裝置，然後重試一次固件更新。</span><span class="sxs-lookup"><span data-stu-id="01da2-125">Unplug all of your other USB devices temporarily and retry the firmware update.</span></span>
* <span data-ttu-id="01da2-126">將 Samsung 耳機連接到您電腦上的其他 USB 3.0 埠。</span><span class="sxs-lookup"><span data-stu-id="01da2-126">Connect your Samsung headset to a different USB 3.0 port on your PC.</span></span>
* <span data-ttu-id="01da2-127">停用或卸載任何可能幹擾固件更新的軟體，例如 Gb 的 AORUS App Center。</span><span class="sxs-lookup"><span data-stu-id="01da2-127">Disable or uninstall any software installed that may interfere with firmware updates, like Gigabyte's AORUS App Center.</span></span>
* <span data-ttu-id="01da2-128">使用不同的電腦來更新 Samsung 耳機固件。</span><span class="sxs-lookup"><span data-stu-id="01da2-128">Use a different PC to update the Samsung headset firmware.</span></span>

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a><span data-ttu-id="01da2-129">如何? 在混合的生活中存取我的電腦桌面？</span><span class="sxs-lookup"><span data-stu-id="01da2-129">How do I access my PC desktop in mixed reality?</span></span>
<span data-ttu-id="01da2-130">從 Windows 的 [耳機] 按鈕啟動桌面應用程式 **> 所有應用程式 > 桌面** ，以混合的方式存取您的電腦桌面。</span><span class="sxs-lookup"><span data-stu-id="01da2-130">Launch the Desktop app in the headset from **Windows Button > All apps > Desktop** to access your PC desktop in mixed reality.</span></span>

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a><span data-ttu-id="01da2-131">如何查看混合現實中的多個監視器</span><span class="sxs-lookup"><span data-stu-id="01da2-131">How can I see multiple monitors in Mixed Reality</span></span>

<span data-ttu-id="01da2-132">根據預設，桌面應用程式會自動切換為顯示具有焦點的監視器。</span><span class="sxs-lookup"><span data-stu-id="01da2-132">By default, Desktop app automatically switches to display the monitor with focus.</span></span> <span data-ttu-id="01da2-133">如果您想要在混合現實中看到所有的監視器：</span><span class="sxs-lookup"><span data-stu-id="01da2-133">If you want to see all of your monitors in mixed reality:</span></span>

* <span data-ttu-id="01da2-134">選取應用程式左上角的 [監視] 圖示。</span><span class="sxs-lookup"><span data-stu-id="01da2-134">Select the monitor icon on the top-left corner of the app.</span></span>
* <span data-ttu-id="01da2-135">停用 [自動切換監視器]。</span><span class="sxs-lookup"><span data-stu-id="01da2-135">Disable "Automatically Switch Monitor".</span></span>
* <span data-ttu-id="01da2-136">挑選您想要查看的監視器。</span><span class="sxs-lookup"><span data-stu-id="01da2-136">Pick the monitor you want to see.</span></span>
* <span data-ttu-id="01da2-137">啟動桌面應用程式的另一個實例。</span><span class="sxs-lookup"><span data-stu-id="01da2-137">Launch another instance of the Desktop app.</span></span>
* <span data-ttu-id="01da2-138">選擇您想要在該實例上看到的監視器。</span><span class="sxs-lookup"><span data-stu-id="01da2-138">Pick the monitor you want to see on that instance.</span></span>
* <span data-ttu-id="01da2-139">針對所有實體監視器重複執行。</span><span class="sxs-lookup"><span data-stu-id="01da2-139">Repeat for all of your physical monitors.</span></span>
<span data-ttu-id="01da2-140">您必須在每次重新開機 mixed reality 時，重新選擇要在每個桌面應用程式上顯示的監視器。</span><span class="sxs-lookup"><span data-stu-id="01da2-140">You'll have to reselect the monitor to show on each Desktop app every time you restart mixed reality.</span></span>

## <a name="my-desktop-app-only-shows-a-black-screen"></a><span data-ttu-id="01da2-141">我的桌面應用程式只會顯示黑色畫面</span><span class="sxs-lookup"><span data-stu-id="01da2-141">My Desktop app only shows a black screen</span></span>

<span data-ttu-id="01da2-142">如果您的電腦有 Nvidia 混合式 GPU，則在離散 GPU （而不是整合的 GPU）上執行 runtimebroker.exe 的 Nvidia 裝置可能會是個原因。</span><span class="sxs-lookup"><span data-stu-id="01da2-142">If your PC has a Nvidia hybrid GPU, the Nvidia device running the runtimebroker.exe on the discrete GPU instead of the integrated one may be the culprit.</span></span> <span data-ttu-id="01da2-143">若要修正此問題，請遵循「[如何? 建立新程式的 Optimus 設定](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)」底下的指示。</span><span class="sxs-lookup"><span data-stu-id="01da2-143">To fix this issue, follow these instructions under "[How do I create Optimus settings for a new program?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)"</span></span> <span data-ttu-id="01da2-144">新增 C:\windows\system32\runtimebroker.exe 並強制它在「整合式圖形」處理器上執行。</span><span class="sxs-lookup"><span data-stu-id="01da2-144">to add C:\windows\system32\runtimebroker.exe and force it to run on the "Integrated graphics" processor.</span></span> 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a><span data-ttu-id="01da2-145">當我使用 Windows Mixed Reality 時，我的 Wi-Fi 會變慢。</span><span class="sxs-lookup"><span data-stu-id="01da2-145">My Wi-Fi slows down when I'm using Windows Mixed Reality.</span></span>

<span data-ttu-id="01da2-146">如果您使用 2.4-GHz Wi-Fi 連接，您的移動控制器可能會減緩您的 Wi-fi：</span><span class="sxs-lookup"><span data-stu-id="01da2-146">If you're using a 2.4-GHz Wi-Fi connection, your motion controllers might slow down your Wi-Fi:</span></span>

* <span data-ttu-id="01da2-147">切換至 5 GHz Wi-Fi 連接（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="01da2-147">Switch to a 5-GHz Wi-Fi connection, if one is available.</span></span> <span data-ttu-id="01da2-148">[深入了解](https://support.microsoft.com/help/4000461)。</span><span class="sxs-lookup"><span data-stu-id="01da2-148">[Learn more](https://support.microsoft.com/help/4000461).</span></span>
* <span data-ttu-id="01da2-149">使用個別的 Bluetooth 介面卡，將您的動作控制器連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="01da2-149">Use a separate Bluetooth adapter to connect your motion controllers to your PC.</span></span> <span data-ttu-id="01da2-150">請參閱 [建議的介面卡](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)。</span><span class="sxs-lookup"><span data-stu-id="01da2-150">See [recommended adapters](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).</span></span>

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a><span data-ttu-id="01da2-151">我收到一則訊息，表示插入和收取電腦的費用。</span><span class="sxs-lookup"><span data-stu-id="01da2-151">I got a message that said to plug in and charge my PC.</span></span> <span data-ttu-id="01da2-152">原因為何？</span><span class="sxs-lookup"><span data-stu-id="01da2-152">Why?</span></span>

<span data-ttu-id="01da2-153">如果您使用的是膝上型電腦，則在電腦同時完全收取和插入電源時，Windows Mixed Reality 的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="01da2-153">If you're using a laptop, Windows Mixed Reality works best when the PC is both fully charged and plugged in.</span></span>

## <a name="what-is-the-experience-options-setting"></a><span data-ttu-id="01da2-154">何謂體驗選項設定？</span><span class="sxs-lookup"><span data-stu-id="01da2-154">What is the Experience options setting?</span></span>

<span data-ttu-id="01da2-155">**設定 > 混合現實 > 耳機顯示器 > 體驗選項** 可讓您變更 Windows Mixed Reality 的效能設定。</span><span class="sxs-lookup"><span data-stu-id="01da2-155">**Settings > Mixed reality > Headset display > Experience options** allows you to change the Windows Mixed Reality performance settings.</span></span> <span data-ttu-id="01da2-156">這可讓您在各種內容中選擇硬體設定的最佳體驗。</span><span class="sxs-lookup"><span data-stu-id="01da2-156">This enables you to choose the best experience for your hardware configuration across a range of content.</span></span> <span data-ttu-id="01da2-157">您有三個體驗選項可供選擇：</span><span class="sxs-lookup"><span data-stu-id="01da2-157">You have three experience options to choose from:</span></span>
* <span data-ttu-id="01da2-158">自動： Windows Mixed Reality 將決定硬體設定的最佳體驗。</span><span class="sxs-lookup"><span data-stu-id="01da2-158">Automatic: Windows Mixed Reality will determine the best experience for your hardware configuration.</span></span> <span data-ttu-id="01da2-159">對於大部分的人來說，這是開始使用的最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="01da2-159">For most people, this is the best choice to start with.</span></span>
* <span data-ttu-id="01da2-160">60 Hz：將重新整理頻率設定為 60 Hz，並關閉特定功能，例如混合實境入口中的影片捕獲和預覽。</span><span class="sxs-lookup"><span data-stu-id="01da2-160">60 Hz: Sets the refresh rate to 60 Hz and turns off certain features, such as video capture and preview in Mixed Reality Portal.</span></span>
* <span data-ttu-id="01da2-161">90 Hz：將更新頻率設定為 90 Hz。</span><span class="sxs-lookup"><span data-stu-id="01da2-161">90 Hz: Sets the refresh rate to 90 Hz.</span></span>

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a><span data-ttu-id="01da2-162">Windows Mixed Reality 支援哪些語言</span><span class="sxs-lookup"><span data-stu-id="01da2-162">What languages are supported in Windows Mixed Reality</span></span>

<span data-ttu-id="01da2-163">Windows Mixed Reality 提供下列語言版本：</span><span class="sxs-lookup"><span data-stu-id="01da2-163">Windows Mixed Reality is available in the following languages:</span></span>

* <span data-ttu-id="01da2-164">簡體中文 (中國)</span><span class="sxs-lookup"><span data-stu-id="01da2-164">Chinese Simplified (China)</span></span>
* <span data-ttu-id="01da2-165">英文 (澳大利亞)</span><span class="sxs-lookup"><span data-stu-id="01da2-165">English (Australia)</span></span>
* <span data-ttu-id="01da2-166">英文 (加拿大)</span><span class="sxs-lookup"><span data-stu-id="01da2-166">English (Canada)</span></span>
* <span data-ttu-id="01da2-167">英文 (英國)</span><span class="sxs-lookup"><span data-stu-id="01da2-167">English (Great Britain)</span></span>
* <span data-ttu-id="01da2-168">英文 (美國)</span><span class="sxs-lookup"><span data-stu-id="01da2-168">English (United States)</span></span>
* <span data-ttu-id="01da2-169">法文 (加拿大)</span><span class="sxs-lookup"><span data-stu-id="01da2-169">French (Canada)</span></span>
* <span data-ttu-id="01da2-170">法文 (法國)</span><span class="sxs-lookup"><span data-stu-id="01da2-170">French (France)</span></span>
* <span data-ttu-id="01da2-171">德文 (德國)</span><span class="sxs-lookup"><span data-stu-id="01da2-171">German (Germany)</span></span>
* <span data-ttu-id="01da2-172">義大利文 (義大利)</span><span class="sxs-lookup"><span data-stu-id="01da2-172">Italian (Italy)</span></span>
* <span data-ttu-id="01da2-173">日文 (日本)</span><span class="sxs-lookup"><span data-stu-id="01da2-173">Japanese (Japan)</span></span>
* <span data-ttu-id="01da2-174">西班牙文 (墨西哥)</span><span class="sxs-lookup"><span data-stu-id="01da2-174">Spanish (Mexico)</span></span>
* <span data-ttu-id="01da2-175">西班牙文 (西班牙)</span><span class="sxs-lookup"><span data-stu-id="01da2-175">Spanish (Spain)</span></span>

<span data-ttu-id="01da2-176">如果您的電腦設定為不同的語言，您可以使用 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="01da2-176">You can use Windows Mixed Reality if your PC is set to a different language.</span></span> <span data-ttu-id="01da2-177">不過，介面會以英文顯示 (美國) ，而語音命令和聽寫則無法使用。</span><span class="sxs-lookup"><span data-stu-id="01da2-177">However, the interface will appear in English (United States), and speech commands and dictation won't be available.</span></span> <span data-ttu-id="01da2-178">Windows Mixed Reality 螢幕小鍵盤僅限英文 (美國) 。</span><span class="sxs-lookup"><span data-stu-id="01da2-178">The Windows Mixed Reality onscreen keyboard is English (United States) only.</span></span> <span data-ttu-id="01da2-179">若要以另一種語言輸入文字，請使用連接到您電腦的實體鍵盤。</span><span class="sxs-lookup"><span data-stu-id="01da2-179">To enter text in another language, use a physical keyboard connected to your PC.</span></span> <span data-ttu-id="01da2-180">您也可以使用上面所列的其中一種支援 Windows Mixed Reality 語言的聽寫，只要在螢幕小鍵盤上選取 [麥克風] 即可。</span><span class="sxs-lookup"><span data-stu-id="01da2-180">You can also use dictation in one of the supported Windows Mixed Reality languages listed above—just select microphone on the onscreen keyboard.</span></span>

<span data-ttu-id="01da2-181">Windows Mixed Reality 也提供下列語言版本，不需要語音命令或聽寫功能：</span><span class="sxs-lookup"><span data-stu-id="01da2-181">Windows Mixed Reality is also available in the following languages without speech commands or dictation features:</span></span>
* <span data-ttu-id="01da2-182">繁體中文 (臺灣和香港特別行政區) </span><span class="sxs-lookup"><span data-stu-id="01da2-182">Chinese Traditional (Taiwan and Hong Kong)</span></span>
* <span data-ttu-id="01da2-183">荷蘭文 (荷蘭)</span><span class="sxs-lookup"><span data-stu-id="01da2-183">Dutch (Netherlands)</span></span>
* <span data-ttu-id="01da2-184">韓文 (韓國)</span><span class="sxs-lookup"><span data-stu-id="01da2-184">Korean (Korea)</span></span>
* <span data-ttu-id="01da2-185">俄文 (俄羅斯)</span><span class="sxs-lookup"><span data-stu-id="01da2-185">Russian (Russia)</span></span>

## <a name="i-have-questions-about-my-headset-hardware"></a><span data-ttu-id="01da2-186">我有關于耳機硬體的問題。</span><span class="sxs-lookup"><span data-stu-id="01da2-186">I have questions about my headset hardware.</span></span>

<span data-ttu-id="01da2-187">如需有關耳機的詳細資訊，請洽詢製造商。</span><span class="sxs-lookup"><span data-stu-id="01da2-187">For details about your headset, check with the manufacturer.</span></span> <span data-ttu-id="01da2-188">Box 中可能會有產品指南，您也可以嘗試製造商的網站。</span><span class="sxs-lookup"><span data-stu-id="01da2-188">There may be a product guide in the box, or you can try the manufacturer’s website.</span></span>

## <a name="how-do-i-uninstall-windows-mixed-reality"></a><span data-ttu-id="01da2-189">如何? 卸載 Windows Mixed Reality？</span><span class="sxs-lookup"><span data-stu-id="01da2-189">How do I uninstall Windows Mixed Reality?</span></span>

1. <span data-ttu-id="01da2-190">中斷耳機與電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="01da2-190">Disconnect your headset from your PC.</span></span>
2. <span data-ttu-id="01da2-191">關閉 Windows Mixed Reality 入口網站。</span><span class="sxs-lookup"><span data-stu-id="01da2-191">Close Windows Mixed Reality Portal.</span></span>
2. <span data-ttu-id="01da2-192">移至 [  **開始] > 設定 > 混合現實** ，然後選取 [卸載]。</span><span class="sxs-lookup"><span data-stu-id="01da2-192">Go to  **Start > Settings > Mixed Reality** and select "Uninstall".</span></span>

<span data-ttu-id="01da2-193">當您準備好要再次開始使用耳機時，請將其插入，Windows Mixed Reality 入口網站會引導您完成安裝程式。</span><span class="sxs-lookup"><span data-stu-id="01da2-193">When you're ready to start using your headset again, plug it in, and Windows Mixed Reality Portal will take you through setup.</span></span>

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a><span data-ttu-id="01da2-194">我收到「我們無法完成卸載 Windows Mixed Reality」訊息。</span><span class="sxs-lookup"><span data-stu-id="01da2-194">I got a "We couldn't finish uninstalling Windows Mixed Reality" message.</span></span>

<span data-ttu-id="01da2-195">有些檔案（包括您的環境相關資訊）仍可能在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="01da2-195">Some files, including information about your environment, might still be on your computer.</span></span> <span data-ttu-id="01da2-196">如果您決定稍後重新安裝 Windows Mixed Reality，這可能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="01da2-196">This can cause problems if you decide to reinstall Windows Mixed Reality later.</span></span> <span data-ttu-id="01da2-197">您可以藉由修改登錄和使用 Windows PowerShell 來執行命令，以手動方式從電腦移除任何剩餘的 Windows Mixed Reality 資訊。</span><span class="sxs-lookup"><span data-stu-id="01da2-197">You can manually remove any remaining Windows Mixed Reality info from your PC by modifying the registry and using Windows PowerShell to run commands.</span></span> <span data-ttu-id="01da2-198">_如果您不正確地修改登錄，可能會發生嚴重的問題。請務必小心遵循這些步驟。為了增加保護，請先備份登錄再進行修改，以便在發生問題時進行還原。_</span><span class="sxs-lookup"><span data-stu-id="01da2-198">_If you modify the registry incorrectly, serious problems might occur. Make sure to follow these steps carefully. For added protection, back up your registry before you modify it so you can restore it if a problem occurs._</span></span> <span data-ttu-id="01da2-199">如需詳細資訊，請參閱 [如何在 Windows 中備份和 restory 登錄](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)。</span><span class="sxs-lookup"><span data-stu-id="01da2-199">For more information, see [How to back up and restory the registry in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows).</span></span> 

<span data-ttu-id="01da2-200">若要使用下列命令卸載 Windows mixed reality：</span><span class="sxs-lookup"><span data-stu-id="01da2-200">To uninstall Windows mixed reality using these commands:</span></span>
1. <span data-ttu-id="01da2-201">重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="01da2-201">Restart your PC.</span></span>
2. <span data-ttu-id="01da2-202">在 **搜尋** 方塊中，輸入 "regedit"，然後選取 [是]。</span><span class="sxs-lookup"><span data-stu-id="01da2-202">In the **Search** box, type "regedit" and then select "Yes".</span></span>
3. <span data-ttu-id="01da2-203">移除下列登錄值：</span><span class="sxs-lookup"><span data-stu-id="01da2-203">Remove these registry values:</span></span>
   <ul>
    <li><span data-ttu-id="01da2-204"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>，然後刪除 "FirstRunSucceeded"。</span><span class="sxs-lookup"><span data-stu-id="01da2-204"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, then delete "FirstRunSucceeded".</span></span></li> 
    <li><span data-ttu-id="01da2-205"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>，然後刪除 "PreferDesktopSpeaker" 和 "PreferDesktopMic"。</span><span class="sxs-lookup"><span data-stu-id="01da2-205"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, then delete "PreferDesktopSpeaker" and "PreferDesktopMic".</span></span></li> 
    <li><span data-ttu-id="01da2-206"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>，然後刪除 "DisableSpeechInput"。</span><span class="sxs-lookup"><span data-stu-id="01da2-206"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>, then delete "DisableSpeechInput".</span></span> <span data-ttu-id="01da2-207">注意：您必須針對已使用 Windows Mixed Reality 之電腦上的每個使用者帳戶，刪除 HHKEY_CURRENT_USER 中的登錄專案。</span><span class="sxs-lookup"><span data-stu-id="01da2-207">Note: The registry items in HHKEY_CURRENT_USER must be deleted for every user account on the PC that has used Windows Mixed Reality.</span></span></li> 
    <li><span data-ttu-id="01da2-208"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>，然後刪除「DeviceID」和「模式」。</span><span class="sxs-lookup"><span data-stu-id="01da2-208"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, then delete "DeviceID" and "Mode".</span></span></li> 
    <li><span data-ttu-id="01da2-209"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>，然後刪除 "OnDeviceLearningCompleted"。</span><span class="sxs-lookup"><span data-stu-id="01da2-209"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, then delete "OnDeviceLearningCompleted".</span></span></li> 
   </ul><span data-ttu-id="01da2-210">
4. 移除下列登錄機碼：</span><span class="sxs-lookup"><span data-stu-id="01da2-210">
4. Remove the following registry keys:</span></span> <ul>
   <li> <span data-ttu-id="01da2-211"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span><span class="sxs-lookup"><span data-stu-id="01da2-211"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span></span></li> 
   <li> <span data-ttu-id="01da2-212"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span><span class="sxs-lookup"><span data-stu-id="01da2-212"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span></span></li> 
   <li> <span data-ttu-id="01da2-213"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></span><span class="sxs-lookup"><span data-stu-id="01da2-213"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></span></span></li><br/></ul><span data-ttu-id="01da2-214">
5. 關閉登錄編輯程式。</span><span class="sxs-lookup"><span data-stu-id="01da2-214">
5. Close the Registry Editor.</span></span>
<span data-ttu-id="01da2-215">6. 移至 **C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** 並刪除「RoomBounds.js開啟」。</span><span class="sxs-lookup"><span data-stu-id="01da2-215">6. Go to **C:\Users\user name\AppData\Local\Packages\Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy\LocalState** and delete "RoomBounds.json".</span></span> <span data-ttu-id="01da2-216">針對已使用 Windows Mixed Reality 的每個使用者重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="01da2-216">Repeat this for each user who has used Windows Mixed Reality.</span></span>
<span data-ttu-id="01da2-217">7. 開啟系統管理員命令提示字元，並移至 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors**。</span><span class="sxs-lookup"><span data-stu-id="01da2-217">7. Open admin cmd prompt and go to **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors**.</span></span> <span data-ttu-id="01da2-218">刪除 "HeadTracking data" 資料夾的內容 (但不) 資料夾本身。</span><span class="sxs-lookup"><span data-stu-id="01da2-218">Delete the contents of the "HeadTracking data" folder (but not the folder itself).</span></span>
<span data-ttu-id="01da2-219">8. 在 [搜尋方塊] 中輸入 "powershell"，以滑鼠右鍵按一下 [Windows PowerShell]，然後選取 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="01da2-219">8. Type "powershell" in the "Search box", right-click "Windows PowerShell", and then select "Run as administrator".</span></span>
<span data-ttu-id="01da2-220">9. 在 Windows PowerShell：</span><span class="sxs-lookup"><span data-stu-id="01da2-220">9. In Windows PowerShell:</span></span> <ul>
   <li><span data-ttu-id="01da2-221">在命令提示字元中，複製並貼上 <b>Dism/Online/Get-Capabilities</b>，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="01da2-221">At the command prompt, copy and paste <b>Dism /online /Get-Capabilities</b>, then press Enter.</span></span></b></li> 
   <li><span data-ttu-id="01da2-222">複製以類比........ Desktop 開頭的功能身分識別。</span><span class="sxs-lookup"><span data-stu-id="01da2-222">Copy the Capability Identity that begins with Analog.Holographic.Desktop.</span></span> <span data-ttu-id="01da2-223">如果不存在，則不會安裝專案，而且您可以跳到步驟 10) 。</span><span class="sxs-lookup"><span data-stu-id="01da2-223">If it isn't there, the item isn't installed and you can skip to step 10).</span></span></li> 
   <li><span data-ttu-id="01da2-224">複製並貼上下列命令提示字元，然後按 Enter： <b>Dism/Online/Remove-Capability/CapabilityName：在最後一個步驟中複製的功能身分識別</b></span><span class="sxs-lookup"><span data-stu-id="01da2-224">Copy and paste the following command prompt, then press Enter: <b>Dism /online /Remove-Capability /CapabilityName: the Capability Identity copied in the last step</b></span></span></li>
   </ul><span data-ttu-id="01da2-225">
10. 重新開機您的電腦。</span><span class="sxs-lookup"><span data-stu-id="01da2-225">
10. Restart your PC.</span></span>

