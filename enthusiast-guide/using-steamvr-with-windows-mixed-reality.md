---
title: 使用 SteamVR 搭配 Windows Mixed Reality
description: 瞭解如何在使用相容電腦的 Windows Mixed Reality 耳機和控制器上設定及播放 SteamVR 遊戲。
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、遊戲、SteamVR、流、系統需求
ms.openlocfilehash: 0d79b0c2079875b32387d616e77c5f497ab4aa59
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110141"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a><span data-ttu-id="e5bf2-104">使用 SteamVR 搭配 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e5bf2-104">Using SteamVR with Windows Mixed Reality</span></span>

<span data-ttu-id="e5bf2-105">適用于 SteamVR 的 Windows Mixed Reality 可讓使用者在 Windows Mixed Reality 的沉浸式耳機上執行 SteamVR 體驗。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-105">Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="e5bf2-106">安裝適用于 SteamVR 的 Windows Mixed Reality 之後，使用者可以從其桌面或串流庫啟動其最愛的 SteamVR 應用程式，並直接在其 Windows 耳機上播放。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-106">After installing the Windows Mixed Reality for SteamVR, users can launch their favorite SteamVR applications from their desktop or Steam library and play them directly on their Windows headset.</span></span>

## <a name="get-your-pc-ready"></a><span data-ttu-id="e5bf2-107">讓您的電腦準備就緒</span><span class="sxs-lookup"><span data-stu-id="e5bf2-107">Get your PC ready</span></span>

* <span data-ttu-id="e5bf2-108">確定您沒有任何擱置中的更新：選取 [ **開始 > 設定] > 更新 & 安全性 > Windows Update**。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-108">Make sure you have no pending updates: Select **Start > Settings > Update & Security > Windows Update**.</span></span> <span data-ttu-id="e5bf2-109">如果有可用的更新，請選取 [ **立即安裝**]。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-109">If updates are available, select **Install now**.</span></span> <span data-ttu-id="e5bf2-110">如果沒有可用的更新，請選取 [ **檢查更新**]，然後安裝任何新的更新。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-110">If no updates are available, select **Check for updates**, and then install any new ones.</span></span>
* <span data-ttu-id="e5bf2-111">電腦需求會因流上的應用程式和內容而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-111">PC requirements vary for the apps and content on Steam.</span></span> <span data-ttu-id="e5bf2-112">查看每個標題的最低需求。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-112">See the minimum requirements per title.</span></span> <span data-ttu-id="e5bf2-113">具有 GTX 1070 圖形配接器 (或對等) 的電腦，以及 Intel® Core™ i7 處理器都應為廣泛的標題提供良好的體驗。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-113">A PC with a GTX 1070 graphics card (or equivalent) and an Intel® Core™ i7 processor should offer a good experience for a broad range of titles.</span></span>
* <span data-ttu-id="e5bf2-114">設定 [Windows Mixed Reality](set-up-windows-mixed-reality.md) （如果您尚未安裝）。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-114">Set up up [Windows Mixed Reality](set-up-windows-mixed-reality.md) if you haven't already.</span></span> 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a><span data-ttu-id="e5bf2-115">設定 SteamVR 的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e5bf2-115">Set up Windows Mixed Reality for SteamVR</span></span>

1. [<span data-ttu-id="e5bf2-116">下載並安裝 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-116">Download and install SteamVR.</span></span>](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. <span data-ttu-id="e5bf2-117">準備好時，請啟動 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-117">When ready, start SteamVR.</span></span> <span data-ttu-id="e5bf2-118">SteamVR 教學課程應該會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-118">The SteamVR Tutorial should start automatically.</span></span>

> <span data-ttu-id="e5bf2-119">**注意：** 若要進行 SteamVR 設定的 advanced 疑難排解，請確定您已安裝下列軟體元件：</span><span class="sxs-lookup"><span data-stu-id="e5bf2-119">**Note:** For advanced troubleshooting of your SteamVR setup, make sure you have the following software components installed:</span></span>
> 1. <span data-ttu-id="e5bf2-120">安裝 [串流](http://store.steampowered.com/about/) 和 **登** 入，或 **建立新的帳戶。**</span><span class="sxs-lookup"><span data-stu-id="e5bf2-120">Install [Steam](http://store.steampowered.com/about/) and **login** or **create a new account.**</span></span>
> 2. <span data-ttu-id="e5bf2-121">安裝 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-121">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).</span></span> <span data-ttu-id="e5bf2-122">當您的耳機插入電源時，啟動串流，您應該會看到一個對話方塊，提示您安裝 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-122">With your headset plugged in, launch Steam and you should see a dialog prompting you to install SteamVR.</span></span> <span data-ttu-id="e5bf2-123">依照對話方塊上的提示進行安裝。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-123">Follow the prompts on the dialog to install it.</span></span>
    * <span data-ttu-id="e5bf2-124">如果您沒有看到快顯視窗，請流覽至 *媒體* 櫃的 [*工具*] 區段來安裝 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-124">If you don't see the popup, install SteamVR by navigating to the *Tools* section of your *library*.</span></span> <span data-ttu-id="e5bf2-125">在清單中找出 SteamVR，然後以滑鼠右鍵按一下並選取 [ *安裝遊戲*]。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-125">Locate SteamVR in the list and then right-click and select *Install Game*.</span></span>
> 3. <span data-ttu-id="e5bf2-126">安裝 [適用于 SteamVR 的 Windows Mixed Reality](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-126">Install [Windows Mixed Reality for SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).</span></span>

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a><span data-ttu-id="e5bf2-127">在沒有網際網路存取的環境中設定 SteamVR 的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e5bf2-127">Set up Windows Mixed Reality for SteamVR in an environment without internet access</span></span>

<span data-ttu-id="e5bf2-128">**將必要的媒體儲存在便攜儲存裝置上**</span><span class="sxs-lookup"><span data-stu-id="e5bf2-128">**Store the necessary media on a portable storage device**</span></span>
1. <span data-ttu-id="e5bf2-129">如上面所述[，使用具有](http://store.steampowered.com/about/)完整網際網路存取權的電腦上的串流，安裝[適用于 SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)的[SteamVR](https://store.steampowered.com/app/250820/SteamVR/)和 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-129">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/) and [Windows Mixed Reality for SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) as directed above using [Steam](http://store.steampowered.com/about/) on a PC with full internet access.</span></span>
2. <span data-ttu-id="e5bf2-130">在 [串流] 中，開啟 [程式庫] 區段，並尋找標示為「工具」的元件。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-130">In Steam, open the Library section and find the part labeled "Tools".</span></span>
3. <span data-ttu-id="e5bf2-131">SteamVR 安裝完成後，以滑鼠右鍵按一下 [SteamVR] 專案，然後在產生的快顯視窗中，按一下 [屬性] 專案。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-131">Once SteamVR is installed, right-click the entry "SteamVR" and in the resulting popup menu, click on the entry "Properties".</span></span>
4. <span data-ttu-id="e5bf2-132">將會開啟具有多個索引標籤的新視窗。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-132">A new window with multiple tabs will open.</span></span> <span data-ttu-id="e5bf2-133">選取 [本機檔案] 索引標籤，然後按一下標示為 [流覽本機檔案] 的按鈕。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-133">Select the tab "LOCAL FILES" and click on the button labeled "BROWSE LOCAL FILES".</span></span>
5. <span data-ttu-id="e5bf2-134">將會開啟包含 SteamVR 執行時間的目錄。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-134">The directory containing the SteamVR Runtime will open.</span></span> <span data-ttu-id="e5bf2-135">將 (名為 SteamVR) 的整個目錄複寫到您選擇的便攜媒體 (例如 USB 拇指磁片磁碟機) 。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-135">Copy this entire directory (named SteamVR) onto a portable medium of your choice (e.g. a USB thumb drive).</span></span>
6. <span data-ttu-id="e5bf2-136">使用 SteamVR 的 Windows Mixed Reality，以及您想要在目的電腦上安裝的任何 SteamVR 相容應用程式來進行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-136">Do the same with Windows Mixed Reality for SteamVR, and any SteamVR-compatible apps you would like to install on the target PC.</span></span>

<span data-ttu-id="e5bf2-137">**在目的電腦上執行 SteamVR**</span><span class="sxs-lookup"><span data-stu-id="e5bf2-137">**Run SteamVR on the target PC**</span></span>
1. <span data-ttu-id="e5bf2-138">將便攜存放裝置插入目的電腦之後，請將 SteamVR、MixedRealityVRDriver 及其他資料夾移至目的電腦上方便使用的位置。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-138">After plugging the portable storage device into the target PC, move the SteamVR, MixedRealityVRDriver, and other folders to a convenient place on the target PC.</span></span>
<span data-ttu-id="e5bf2-139">![目的電腦上安裝之 SteamVR 的 SteamVR 和 Windows Mixed Reality](images/steamvr-install-files.png)</span><span class="sxs-lookup"><span data-stu-id="e5bf2-139">![SteamVR and Windows Mixed Reality for SteamVR installed on target PC](images/steamvr-install-files.png)</span></span>

2. <span data-ttu-id="e5bf2-140">確保 SteamVR 和 MixedRealityVRDriver 位於相同的資料夾中，然後開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-140">Ensuring SteamVR and MixedRealityVRDriver are in the same folder, open a command prompt.</span></span> <span data-ttu-id="e5bf2-141">基於這個範例，我們會假設包含資料夾位於 *C:\SteamVRInstall*。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-141">For the sake of this example, we will assume the containing folder is at *C:\SteamVRInstall*.</span></span> <span data-ttu-id="e5bf2-142">在此情況下，您應該在命令提示字元中執行：</span><span class="sxs-lookup"><span data-stu-id="e5bf2-142">In that case, in the command prompt you should run:</span></span>
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
<span data-ttu-id="e5bf2-143"> (請注意，如果您執行的是32位版本的 Windows，則 `win64` 應該改為使用上述路徑的部分 `win32` 。 ) </span><span class="sxs-lookup"><span data-stu-id="e5bf2-143">(Note that if you're running a 32-bit version of Windows, the `win64` part of the path above should be `win32` instead.)</span></span>

<span data-ttu-id="e5bf2-144">這可讓執行時間在您的自訂安裝中尋找 SteamVR 驅動程式的 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-144">This will allow the runtime to find the Windows Mixed Reality for SteamVR driver in your custom installation.</span></span>

4. <span data-ttu-id="e5bf2-145">若要執行 SteamVR，您應該按兩下位於 *SteamVR\bin\win64\vrstartup.exe* 的檔案 "vrstartup.exe"，或 *SteamVR\bin\win32\vrstartup.exe* 如果目的電腦執行的是32位版本的 Windows。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-145">In order to run SteamVR you should double-click the file "vrstartup.exe" located at *SteamVR\bin\win64\vrstartup.exe*, or *SteamVR\bin\win32\vrstartup.exe* if the target PC is running a 32-bit version of Windows.</span></span>

<span data-ttu-id="e5bf2-146">如需 [詳細資訊和疑難排解，請參閱 Steamworks 檔頁面](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-146">See the [Steamworks documentation page for more information and troubleshooting](https://partner.steamgames.com/doc/features/steamvr/enterprise#2).</span></span>

## <a name="play-steamvr-games"></a><span data-ttu-id="e5bf2-147">Play SteamVR 遊戲</span><span class="sxs-lookup"><span data-stu-id="e5bf2-147">Play SteamVR games</span></span>

1. <span data-ttu-id="e5bf2-148">將您的耳機連接到您的電腦，然後開啟您的動作控制器。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-148">Connect your headset to your PC and turn on your motion controllers.</span></span>
2. <span data-ttu-id="e5bf2-149">一旦載入 Windows Mixed Reality 首頁，並顯示您的控制器，請在您的桌面上開啟串流應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-149">Once the Windows Mixed Reality home has loaded and your controllers are visible, open the Steam app on your desktop.</span></span>
3. <span data-ttu-id="e5bf2-150">使用流應用程式從您的串流庫啟動 SteamVR 遊戲。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-150">Use the Steam app to launch a SteamVR game from your Steam library.</span></span>

<span data-ttu-id="e5bf2-151">**秘訣**：若要在不離開耳機的情況下啟動 SteamVR 遊戲，請使用桌面應用程式 (**啟動 > 桌面**) 在 Windows Mixed Reality 內查看您的電腦桌面並與其互動。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-151">**Tip**: To launch SteamVR games without taking off your headset, use the Desktop app (**Start > Desktop**) to view and interact with your PC desktop inside Windows Mixed Reality.</span></span>

## <a name="using-motion-controllers-with-steamvr"></a><span data-ttu-id="e5bf2-152">搭配 SteamVR 使用移動控制器</span><span class="sxs-lookup"><span data-stu-id="e5bf2-152">Using Motion Controllers with SteamVR</span></span>

<span data-ttu-id="e5bf2-153">您將在不同的遊戲中以不同的方式使用移動控制器。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-153">You'll use your motion controllers differently in different games.</span></span> <span data-ttu-id="e5bf2-154">以下是一些可協助您開始使用的基本概念：</span><span class="sxs-lookup"><span data-stu-id="e5bf2-154">Here are a few basics to help you get started:</span></span>

* <span data-ttu-id="e5bf2-155">若要開啟 [串流] 儀表板，請在左側或右側的操縱杆上按直向下。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-155">To open the Steam dashboard, press straight down on the left or right thumbstick.</span></span>
* <span data-ttu-id="e5bf2-156">若要結束 SteamVR 遊戲並回到 Windows Mixed Reality 首頁，請按 [Windows] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-156">To exit a SteamVR game and return to the Windows Mixed Reality home, press the Windows button.</span></span>

## <a name="changing-the-resolution"></a><span data-ttu-id="e5bf2-157">變更解析度</span><span class="sxs-lookup"><span data-stu-id="e5bf2-157">Changing the resolution</span></span>

<span data-ttu-id="e5bf2-158">如果您想要以較高的解析度播放遊戲，您隨時都可以在 [SteamVR-> 設定-> 應用程式] 視窗中調整應用程式解析度滑杆。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-158">You can adjust the Application Resolution slider in the SteamVR -> Settings -> Applications window at any time if you'd like to play games at a higher resolution.</span></span> <span data-ttu-id="e5bf2-159">\* \* 使用較高的解析度乘數時，您可能會想要讓遊戲對您的電腦造成更多的壓力。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-159">\*\*When using a higher resolution multiplier you can expect the game to put more strain on your PC.</span></span> <span data-ttu-id="e5bf2-160">如果您增加乘數並看到效能降低，請將滑杆重新調整為預設層級並重新啟動遊戲，以確保變更生效。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-160">If you increase the multiplier and see degraded performance, readjust the slider to the default level and restart the game to ensure that the change takes effect.</span></span>![調整應用程式解析度](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a><span data-ttu-id="e5bf2-162">使用多個耳機</span><span class="sxs-lookup"><span data-stu-id="e5bf2-162">Using multiple headsets</span></span>

<span data-ttu-id="e5bf2-163">如果您是 VR 愛好者，您可能會在同一部電腦上定期使用一個以上的 VR 耳機。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-163">If you're a VR enthusiast, you might regularly use more than one VR headset on the same PC.</span></span> <span data-ttu-id="e5bf2-164">如果是這種情況，請注意，當 Windows Mixed Reality 耳機插入電源時，SteamVR 遊戲一律會啟動 Windows Mixed Reality 耳機。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-164">If that's the case note that when a Windows Mixed Reality headset is plugged in, SteamVR games will always launch to the Windows Mixed Reality headset.</span></span> <span data-ttu-id="e5bf2-165">如果您想要在另一個耳機上啟動 SteamVR 遊戲，請務必先拔掉 Windows Mixed Reality 耳機，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-165">If you'd like to launch SteamVR games on another headset make sure to first unplug the Windows Mixed Reality headset before continuing.</span></span>

## <a name="preview-programs"></a><span data-ttu-id="e5bf2-166">預覽程式</span><span class="sxs-lookup"><span data-stu-id="e5bf2-166">Preview programs</span></span>

<span data-ttu-id="e5bf2-167">我們會發行定期更新，以改善在 Windows Mixed Reality 沉浸式耳機上使用 SteamVR 的效能、可靠性和整體體驗。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-167">We release regular updates to improve the performance, reliability, and overall experience of using SteamVR on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="e5bf2-168">雖然這些預覽版程式都不是必要的，但如果您想要更快且更頻繁地 (更新，並提供意見反應給我們這些更新！ ) ，建議您加入這些程式。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-168">While none of these preview programs are required, we encourage you to join them if you would like to get updates sooner and more frequently (and give us feedback on those updates!).</span></span>

### <a name="windows-mixed-reality-for-steamvr-beta"></a><span data-ttu-id="e5bf2-169">適用于 SteamVR Beta 的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e5bf2-169">Windows Mixed Reality for SteamVR Beta</span></span>

<span data-ttu-id="e5bf2-170">SteamVR 的 Windows Mixed Reality 是您從串流存放區安裝的元件，可讓 SteamVR 使用您的 Windows Mixed Reality 耳機。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-170">Windows Mixed Reality for SteamVR is the component you install from the Steam Store that enables SteamVR to work with your Windows Mixed Reality headset.</span></span>  <span data-ttu-id="e5bf2-171">我們會定期將更新發佈到此「橋接器」，並自動將其安裝。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-171">We publish updates to this "bridge" regularly and Steam installs them automatically.</span></span>

<span data-ttu-id="e5bf2-172">如果您想要更頻繁地取得更新，建議您加入我們的公用搶鮮版（Beta）。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-172">If you want to get updates more frequently, we encourage you to join our public Beta.</span></span>  <span data-ttu-id="e5bf2-173">更新會先移至我們的搶鮮版（Beta）物件，並在將更新發佈給所有使用者之前，使用他們的意見反應來確定更新為高品質。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-173">Updates go to our Beta audience first, and we use their feedback to make sure the updates are high quality before publishing them to all users.</span></span>  <span data-ttu-id="e5bf2-174">如果您不在我們的測試計劃中，最終將會取得所有相同的修正和功能，但經過 Beta 版使用者的測試之後也是如此。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-174">If you’re not in our Beta program, you’ll eventually get all of the same fixes and features, but after they've been tested by our Beta users.</span></span>

<span data-ttu-id="e5bf2-175">若要加入：</span><span class="sxs-lookup"><span data-stu-id="e5bf2-175">To join:</span></span>

  1. <span data-ttu-id="e5bf2-176">在 [流] 中，使用 [連結 **庫** ] 功能表底下的下拉式清單來篩選 **軟體**。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-176">In Steam, use the drop-down under the **Library** menu to filter to **Software**.</span></span>
  2. <span data-ttu-id="e5bf2-177">在清單中，以滑鼠右鍵按一下 **SteamVR 的 [Windows Mixed Reality** ]，然後選取 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-177">In the list, right-click **Windows Mixed Reality for SteamVR** and select **Properties**.</span></span>
  3. <span data-ttu-id="e5bf2-178">選取 [ **Beta** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-178">Select the **Betas** tab.</span></span>
  4. <span data-ttu-id="e5bf2-179">選擇 **[Beta-public Beta]** ，然後選取 [ **關閉** ] 以確認。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-179">Opt in to **"beta - public beta"** and select **Close** to confirm.</span></span> <span data-ttu-id="e5bf2-180">[Beta 存取程式碼] 欄位應該保留空白。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-180">The beta access code field should be left blank.</span></span>
  
### <a name="steamvr-beta"></a><span data-ttu-id="e5bf2-181">SteamVR Beta 版</span><span class="sxs-lookup"><span data-stu-id="e5bf2-181">SteamVR Beta</span></span>

<span data-ttu-id="e5bf2-182">SteamVR 是由閥門建立和發行，而且在所有 SteamVR 耳機都很常見。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-182">SteamVR is built and released by Valve and is common across all SteamVR headsets.</span></span>  <span data-ttu-id="e5bf2-183">它會遵循類似的模型，將更新發行至搶鮮版（Beta）成員，再發佈給所有使用者。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-183">It follows a similar model of releasing updates to Beta members before publishing to all users.</span></span>

<span data-ttu-id="e5bf2-184">若要加入：</span><span class="sxs-lookup"><span data-stu-id="e5bf2-184">To join:</span></span>

  1. <span data-ttu-id="e5bf2-185">在 [流] 中，使用 [連結 **庫** ] 功能表底下的下拉式清單來篩選 **工具**。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-185">In Steam, use the drop-down under the **Library** menu to filter to **Tools**.</span></span>
  2. <span data-ttu-id="e5bf2-186">在清單中，以滑鼠右鍵按一下 [ **SteamVR** ]，然後選取 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-186">In the list, right-click **SteamVR** and select **Properties**.</span></span>
  3. <span data-ttu-id="e5bf2-187">選取 [ **Beta** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-187">Select the **Betas** tab.</span></span>
  4. <span data-ttu-id="e5bf2-188">選擇 **[Beta-public Beta]** ，然後選取 [ **關閉** ] 以確認。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-188">Opt in to **"beta - public beta"** and select **Close** to confirm.</span></span>  <span data-ttu-id="e5bf2-189">[Beta 存取程式碼] 欄位應該保留空白。 ![在 SteamVR 的 [屬性] 對話方塊中，切換至 SteamVR Beta](images/steamvr-beta.png)</span><span class="sxs-lookup"><span data-stu-id="e5bf2-189">The beta access code field should be left blank.![Switch to the SteamVR beta in the properties dialog for SteamVR](images/steamvr-beta.png)</span></span>

### <a name="windows-insider-program"></a><span data-ttu-id="e5bf2-190">Windows 測試人員計畫</span><span class="sxs-lookup"><span data-stu-id="e5bf2-190">Windows Insider Program</span></span>

<span data-ttu-id="e5bf2-191">Windows Mixed Reality 是 Windows 10 的一部分。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-191">Windows Mixed Reality is a part of Windows 10.</span></span>  <span data-ttu-id="e5bf2-192">許多影響 SteamVR 使用者的修正和功能都隨附于 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-192">Many fixes and features that affect SteamVR users come with the Windows OS.</span></span>  <span data-ttu-id="e5bf2-193">如果您想要試用最新的 Windows 10 preview 組建，建議您加入 [Windows 測試人員計畫](https://insider.windows.com)。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-193">If you want to try the latest Windows 10 preview builds, we encourage you to join the [Windows Insider Program](https://insider.windows.com).</span></span>

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a><span data-ttu-id="e5bf2-194">啟用 SteamVR Apps 的動作 reprojection</span><span class="sxs-lookup"><span data-stu-id="e5bf2-194">Enabling motion reprojection for SteamVR Apps</span></span>

<span data-ttu-id="e5bf2-195">SteamVR 的 Windows Mixed Reality 具有實驗性動作 reprojection 功能，可讓 90 FPS reprojection 更順暢。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-195">Windows Mixed Reality for SteamVR has an experimental motion reprojection feature to make 90 FPS reprojection more smooth.</span></span>

<span data-ttu-id="e5bf2-196">啟用 [動作] reprojection 時，所有的串流 VR 遊戲都會以1/2 畫面播放速率轉譯名義上 (45 fps，而非 90 FPS) ，而 Windows Mixed Reality for SteamVR 會使用 GPU 所產生的動態向量來推斷下一個畫面格。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-196">When motion reprojection is enabled, all Steam VR games will render nominally at ½ frame rate (45 fps instead of 90 FPS) while Windows Mixed Reality for SteamVR uses motion vectors generated by the GPU to extrapolate the next frame.</span></span> <span data-ttu-id="e5bf2-197">針對在指定的電腦上可靠地達到 60 FPS + 的 SteamVR 遊戲，這應該會產生具有偶爾構件的穩固 90 FPS 體驗，同時維持舒適的體驗。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-197">For SteamVR games that reliably hit 60 FPS+ on a given PC, this should result in a solid 90 FPS experience with occasional artifacts while maintaining a comfortable experience.</span></span>

<span data-ttu-id="e5bf2-198">可用的動作 reprojection 模式如下所示：</span><span class="sxs-lookup"><span data-stu-id="e5bf2-198">The available motion reprojection modes are as follows:</span></span>

* <span data-ttu-id="e5bf2-199">**SteamVR 每個應用程式的設定**：可讓您透過 STEAMVR 設定 UI 控制動作 reprojection。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-199">**SteamVR per-app setting**: Allows you to control motion reprojection through the SteamVR Settings UI.</span></span> <span data-ttu-id="e5bf2-200">然後，您可以開啟 [SteamVR 設定]、移至 [影片] > Per-Application 影片設定]，然後選取 [動作平滑] 的選項。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-200">You can then open SteamVR Settings, go to Video > Per-Application Video Settings, and select an option for "Motion Smoothing."</span></span>
* <span data-ttu-id="e5bf2-201">**Auto**：讓運動 reprojection 在遊戲轉譯太慢時自動開啟，以維護 90 FPS。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-201">**Auto**: Enables motion reprojection to turn on automatically when a game is rendering too slowly to maintain 90 FPS.</span></span> <span data-ttu-id="e5bf2-202">當遊戲開始維護 90 FPS 或在低於 45 FPS 的時候開始轉譯時，移動 reprojection 將會關閉。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-202">When a game begins to maintain 90 FPS or starts rendering at less than 45 FPS, motion reprojection will turn off.</span></span> <span data-ttu-id="e5bf2-203">非同步旋轉 reprojection 一律為啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-203">Asynchronous rotational reprojection is enabled always.</span></span>
* <span data-ttu-id="e5bf2-204">**動作向量**：強制應用程式一律以具有動作向量 reprojection 的半畫面播放速率執行。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-204">**Motion Vector**: Forces the application to always run at half-framerate with motion vector reprojection.</span></span>
* <span data-ttu-id="e5bf2-205">**None**：停用運動 reprojection。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-205">**None**: Disables motion reprojection.</span></span>

<span data-ttu-id="e5bf2-206">**預期的視覺構件**</span><span class="sxs-lookup"><span data-stu-id="e5bf2-206">**Expected Visual Artifacts**</span></span> 

1. <span data-ttu-id="e5bf2-207">使用大於150% 的應用程式解析時，您可能會遇到模糊的情況。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-207">When using an application resolution greater than 150%, you may experience blurring.</span></span> <span data-ttu-id="e5bf2-208">使用移動 reprojection 時，建議使用小於150% 的值。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-208">When using motion reprojection, we recommend using a value less than 150%.</span></span>
2. <span data-ttu-id="e5bf2-209">清晰對比度的邊緣或文字（特別是在遊戲 HUDs 或功能表上）可能會因為 disocclusion 而暫時扭曲或失真。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-209">Sharp contrast edges or text, especially on in-game HUDs or menus, may look temporarily warped or distorted because of disocclusion.</span></span>
3. <span data-ttu-id="e5bf2-210">SteamVR 家用及許多其他不可靠地在您的電腦上達到 50-60 FPS 的遊戲，將會繼續在此模式下使用不佳的體驗。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-210">SteamVR Home and many other games that don't reliably hit 50-60 FPS on your PC will continue to have a poor experience with this mode.</span></span>
4. <span data-ttu-id="e5bf2-211">某些遊戲已回報為以50% 速度執行，或延遲)  (延遲增加。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-211">Some games have been reported to run at 50% speed or with increased latency (lag).</span></span> <span data-ttu-id="e5bf2-212">請透過下列 [Windows 意見反應中樞](filing-feedback.md) 指示來報告這些遊戲。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-212">Report these games through the [Windows Feedback Hub](filing-feedback.md) instructions below.</span></span>

<span data-ttu-id="e5bf2-213">一開始，我們會對最新世代的 NVidia Gpu 進行實驗性支援。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-213">Initially we have experimental support for recent generation NVidia GPUs.</span></span> <span data-ttu-id="e5bf2-214">我們會持續在更多 Gpu 上反復查看和改善我們的運動 reprojection 支援，並積極聆聽您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-214">We're continuing to iterate and improve our motion reprojection support on more GPUs, and we’re eager to hear your feedback.</span></span>

<span data-ttu-id="e5bf2-215">**支援的 gpu：** Nvidia GeForce GTX1060、AMD RX470 或更高版本，並安裝 Windows Mixed Reality 相容的圖形驅動程式。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-215">**Supported GPUs:** Nvidia GeForce GTX1060, AMD RX470 or better, with Windows Mixed Reality compatible graphics drivers installed.</span></span>

<span data-ttu-id="e5bf2-216">若要啟用動作 reprojection：</span><span class="sxs-lookup"><span data-stu-id="e5bf2-216">To enable motion reprojection:</span></span>

1. <span data-ttu-id="e5bf2-217">請確定您已使用上述指示加入宣告 **SteamVR Beta 的 Windows Mixed Reality** 。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-217">Make sure you've opted into the **Windows Mixed Reality for SteamVR Beta** using the instructions above.</span></span>
2. <span data-ttu-id="e5bf2-218">開啟 SteamVR 儀表板。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-218">Open the SteamVR dashboard.</span></span>
3. <span data-ttu-id="e5bf2-219">選取左邊的按鈕，並使用 Windows Mixed Reality 標誌來開啟 [SteamVR] 設定 **Windows Mixed Reality** 。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-219">Select the button on the left side with the Windows Mixed Reality logo to open **Windows Mixed Reality for SteamVR** Settings.</span></span>
4. <span data-ttu-id="e5bf2-220">在彈出的 UI 中，選取 [圖形] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-220">In the UI that pops up, select the Graphics tab.</span></span>
5. <span data-ttu-id="e5bf2-221">選取 [預設 SteamVR 應用程式動作 reprojection 模式] 的 [自動]，以啟用自動動作 reprojection。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-221">Select "Auto" for "Default SteamVR app motion reprojection mode" to enable automatic motion reprojection.</span></span>

![使用 SettingsUX 啟用 LSR & LSR 指標](images/settingsux-enable-lsr.gif)

<span data-ttu-id="e5bf2-223">**運動 Reprojection 指標**</span><span class="sxs-lookup"><span data-stu-id="e5bf2-223">**Motion Reprojection Indicator**</span></span>

<span data-ttu-id="e5bf2-224">動作 reprojection 指標可協助診斷實驗性自動移動 reprojection 功能的問題。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-224">The motion reprojection indicator helps diagnose issues with the experimental automatic motion reprojection feature.</span></span> <span data-ttu-id="e5bf2-225">當設為 true 時，您會在自動移動 reprojection 期間，在耳機顯示的左上角看到指標。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-225">When set to true, you'll see an indicator in the top-left of your headset display during automatic motion reprojection.</span></span> <span data-ttu-id="e5bf2-226">這個指標的色彩和位置對應到目前的動作 reprojection 模式-請參閱下圖以取得範例。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-226">The color and position of this indicator corresponds to the current motion reprojection mode - see the diagram below for examples.</span></span>

![mvLSR 指標](images/mvLSRIndicator.png)

<span data-ttu-id="e5bf2-228">綠色 = 移動 reprojection 是關閉的，因為應用程式可以用完整的畫面播放速率轉譯。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-228">Green = motion reprojection is off because the application can render at full framerate.</span></span>

<span data-ttu-id="e5bf2-229">青色 = 動作 reprojection 是開啟的，因為應用程式已受 cpu 限制。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-229">Cyan = motion reprojection is on because the application is cpu bound.</span></span>

<span data-ttu-id="e5bf2-230">Blue = 動作 reprojection 是開啟的，因為應用程式是 gpu 系結的。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-230">Blue = motion reprojection is on because the application is gpu bound.</span></span>

<span data-ttu-id="e5bf2-231">Red = 動作 reprojection 是關閉的，因為應用程式的執行速度低於一半的速率;如果啟用的話，請嘗試減少超取樣。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-231">Red = motion reprojection is off because the application is running at less than half framerate; try reducing super sampling if enabled.</span></span>

<span data-ttu-id="e5bf2-232">綠色 + 青色 + 藍色 = 運動 reprojection 是以半畫面播放速率模式或應用程式要求的移動 reprojection。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-232">Green + Cyan + Blue = motion reprojection is in half-framerate mode or the application requested motion reprojection.</span></span>

## <a name="sharing-feedback-on-steamvr"></a><span data-ttu-id="e5bf2-233">SteamVR 上的分享意見反應</span><span class="sxs-lookup"><span data-stu-id="e5bf2-233">Sharing feedback on SteamVR</span></span>

<span data-ttu-id="e5bf2-234">在改善 Windows Mixed Reality SteamVR 體驗時，您的意見反應非常寶貴。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-234">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="e5bf2-235">透過 [Windows 意見反應中樞](filing-feedback.md)提交所有意見反應和 bug。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-235">Submit all feedback and bugs through the [Windows Feedback Hub](filing-feedback.md).</span></span> <span data-ttu-id="e5bf2-236">請遵循下列建議，以協助我們充分利用您的意見反應：</span><span class="sxs-lookup"><span data-stu-id="e5bf2-236">Follow these suggestions to help us get the most from your feedback:</span></span>

1. <span data-ttu-id="e5bf2-237">在意見反應中樞中，表示您回報的是「這是哪一種意見反應？」的新問題。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-237">In Feedback Hub, indicate that you're reporting a new Problem in the "What kind of feedback is it?"</span></span> <span data-ttu-id="e5bf2-238">區段。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-238">section at the top.</span></span>
2. <span data-ttu-id="e5bf2-239">選取 **混合現實** 類別和 **應用程式** 子類別。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-239">Select the **Mixed Reality** category and the **Apps** subcategory.</span></span>
3. <span data-ttu-id="e5bf2-240">在問題摘要中放入 "SteamVR" 一字。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-240">Put the word "SteamVR" in the problem summary.</span></span> <span data-ttu-id="e5bf2-241">這可協助我們找到您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-241">That helps us find your feedback.</span></span>
4. <span data-ttu-id="e5bf2-242">描述當您遇到問題時，所使用的 SteamVR 遊戲或應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-242">Describe what SteamVR game or application you were using when you come across the issue.</span></span>
5. <span data-ttu-id="e5bf2-243">請考慮將 SteamVR 系統報告附加至您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-243">Consider attaching a SteamVR System Report to your feedback.</span></span> <span data-ttu-id="e5bf2-244">這會提供更多記錄，以協助我們診斷您的問題。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-244">This provides more logs that can help us diagnose your problem.</span></span>
    1. <span data-ttu-id="e5bf2-245">在 [SteamVR] 視窗 (顯示控制器狀態的小視窗) 選取標題以開啟功能表。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-245">On the SteamVR Window (the small windows that shows your controller status) select on the title to open the menu.</span></span>
    2. <span data-ttu-id="e5bf2-246">選取 [建立系統報告]。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-246">Select "Create System Report".</span></span>
    3. <span data-ttu-id="e5bf2-247">儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-247">Save to File.</span></span>
    4. <span data-ttu-id="e5bf2-248">直接將產生的檔案附加到您的意見反應中樞專案。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-248">Attach the generated file to your Feedback Hub entry directly.</span></span>
6. <span data-ttu-id="e5bf2-249">如果您的意見反應是關於 SteamVR 效能，請收集混合現實效能追蹤：</span><span class="sxs-lookup"><span data-stu-id="e5bf2-249">If your feedback is about SteamVR performance, collect a Mixed Reality Performance trace:</span></span> 
    1. <span data-ttu-id="e5bf2-250">選取 [ **重新建立我的問題** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-250">Select the **Recreate my Problem** button.</span></span>
    2. <span data-ttu-id="e5bf2-251">在 [包含相關資料] 旁的下拉式清單中，選取 [ **混合的現實效能**]。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-251">In the drop-down next to "include data about", select **Mixed Reality Performance**.</span></span>
    3. <span data-ttu-id="e5bf2-252">確定遊戲正在執行，然後選取 [ **開始捕獲**]。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-252">Make sure the game is running and select **Start Capture**.</span></span>
    4. <span data-ttu-id="e5bf2-253">花幾秒鐘的時間玩遊戲來捕捉追蹤。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-253">Spend a few seconds playing the game to capture the trace.</span></span> <span data-ttu-id="e5bf2-254">請勿捕獲超過10-15 秒的追蹤，否則將會太大而無法提交。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-254">Don't capture the trace for more than 10-15 seconds, or it will be too large to submit.</span></span>
    5. <span data-ttu-id="e5bf2-255">選取 [ **停止捕捉**]。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-255">Select **Stop Capture**.</span></span>
7. <span data-ttu-id="e5bf2-256">當您完成其餘欄位之後，請選取 [ **提交** ]。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-256">Select **Submit** once you've completed the rest of the fields.</span></span>

<span data-ttu-id="e5bf2-257">如果您有任何問題或意見可以共用，您也可以在我們的串流 [論壇](http://steamcommunity.com/app/719950/discussions/)上聯繫我們。</span><span class="sxs-lookup"><span data-stu-id="e5bf2-257">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5bf2-258">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5bf2-258">See also</span></span>

* [<span data-ttu-id="e5bf2-259">使用 Windows Mixed Reality 針對 SteamVR 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="e5bf2-259">Troubleshooting SteamVR with Windows Mixed Reality</span></span>](steamvr-questions.md)
* [<span data-ttu-id="e5bf2-260">在 Windows Mixed Reality 中使用遊戲和應用程式</span><span class="sxs-lookup"><span data-stu-id="e5bf2-260">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="e5bf2-261">使用 Unity 中的 HP 控制器</span><span class="sxs-lookup"><span data-stu-id="e5bf2-261">Using HP Controllers in Unity</span></span>](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [<span data-ttu-id="e5bf2-262">在 Unreal 中使用 HP 控制器</span><span class="sxs-lookup"><span data-stu-id="e5bf2-262">Using HP Controllers in Unreal</span></span>](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [<span data-ttu-id="e5bf2-263">提出錯誤及意見反應</span><span class="sxs-lookup"><span data-stu-id="e5bf2-263">Filing bugs and feedback</span></span>](filing-feedback.md)
