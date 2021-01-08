---
title: 版本資訊 - 2016 年 5 月
description: 隨時掌握 Windows 全像2016版更新版的 HoloLens 版本資訊。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，版本資訊，作業系統，功能，組建，平臺
ms.openlocfilehash: db5e3b87eaf619a0f25e07d0698499a89a1b4b12
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009498"
---
# <a name="release-notes---may-2016"></a><span data-ttu-id="7ecd9-104">版本資訊 - 2016 年 5 月</span><span class="sxs-lookup"><span data-stu-id="7ecd9-104">Release notes - May 2016</span></span>

<span data-ttu-id="7ecd9-105">HoloLens 團隊致力於提供您透過 Windows 測試人員計畫的最新功能更新和主要修正。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-105">The HoloLens team is committed to providing you with the latest feature updates and major fixes through the Windows Insider Program.</span></span> <span data-ttu-id="7ecd9-106">感謝您所有的建議，我們會將您的意見反應帶給您。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-106">Thanks to all your suggestions, we take your feedback to heart.</span></span> <span data-ttu-id="7ecd9-107">繼續透過意見反應中樞、[開發人員論壇](https://forums.hololens.com) [ @HoloLens 和 Twitter ](https://twitter.com/hololens)[提供意見](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)反應給我們。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-107">Continue to [give us feedback](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span>

<span data-ttu-id="7ecd9-108">**發行版本：** Windows 全像2016更新 (**10.0.14342.1016**) </span><span class="sxs-lookup"><span data-stu-id="7ecd9-108">**Release version:** Windows Holographic May 2016 Update (**10.0.14342.1016**)</span></span>

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

<span data-ttu-id="7ecd9-109">若要更新為最新版本，請開啟 [ *設定* ] 應用程式，移至 [ *更新 & 安全性*]，然後選取 [ *檢查更新* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-109">To update to the current release, open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="7ecd9-110">新功能</span><span class="sxs-lookup"><span data-stu-id="7ecd9-110">New features</span></span>

* <span data-ttu-id="7ecd9-111">您現在可以 **在 2d view 中同時執行最多三個應用程式**，這可讓您在 HoloLens 中進行多工處理的無限使用案例。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-111">You can now **run up to three apps in 2D view simultaneously**, which enables endless use cases for multi-tasking in HoloLens.</span></span> <span data-ttu-id="7ecd9-112">在探索此航班上的新功能時，讓新的意見反應中樞探索」開啟清單。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-112">Have the new Feedback Hub with the list of Quests open while exploring the new features on this flight.</span></span>

  <span data-ttu-id="7ecd9-113">![HoloLens 可以同時執行三個應用程式](images/img-3625-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7ecd9-113">![HoloLens can run three apps at the same time](images/img-3625-400px.jpg)</span></span><br>
  <span data-ttu-id="7ecd9-114">同時在 2D view 中執行最多三個應用程式</span><span class="sxs-lookup"><span data-stu-id="7ecd9-114">Run up to three apps in 2D view simultaneously</span></span>

* <span data-ttu-id="7ecd9-115">我們新增了 **語音命令**：</span><span class="sxs-lookup"><span data-stu-id="7ecd9-115">We've added new **voice commands**:</span></span>
   * <span data-ttu-id="7ecd9-116">請嘗試查看全像，然後說「臉部我」來旋轉</span><span class="sxs-lookup"><span data-stu-id="7ecd9-116">Try looking at a hologram and rotate it by saying "face me"</span></span>
   * <span data-ttu-id="7ecd9-117">藉由說出「更大」或「較小」來變更其大小</span><span class="sxs-lookup"><span data-stu-id="7ecd9-117">Change its size by saying "bigger" or "smaller"</span></span>
   * <span data-ttu-id="7ecd9-118">藉由說出「嗨 Cortana，將 *應用程式名稱* 移至這裡」來移動應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-118">Move an app by saying "Hey Cortana, move *app name* here."</span></span>
* <span data-ttu-id="7ecd9-119">我們已 **在 HoloLens 上更輕鬆地進行開發**。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-119">We've made **developing on HoloLens easier**.</span></span> <span data-ttu-id="7ecd9-120">您現在可以透過 [Windows 裝置入口網站](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)流覽、上傳和下載檔案。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-120">You can now browse, upload, and download files through the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span> <span data-ttu-id="7ecd9-121">您可以透過 Visual Studio，存取您側載或部署之任何應用程式的 [檔] 資料夾、[圖片] 資料夾和本機儲存體。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-121">You can access the Documents folder, Pictures folder, and the local storage for any app you side-loaded or deployed through Visual Studio.</span></span>
* <span data-ttu-id="7ecd9-122">**模擬器現在支援使用 Microsoft 帳戶進行登入**，就像您在實際 HoloLens 上的方式一樣，您可以從 [其他工具] 功能表的 [>>] 啟用。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-122">The **emulator now supports log-in with a Microsoft Account** just like you would on a real HoloLens, which you can enable from the Additional Tools menu ">>".</span></span>
* <span data-ttu-id="7ecd9-123">**2D 應用程式現在會在監看影片全螢幕時隱藏應用程式列和游標** ，以避免干擾。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-123">**2D Apps now hide the app bar and cursor when watching video full screen** to avoid distraction.</span></span> <span data-ttu-id="7ecd9-124">您的影片監看體驗在 HoloLens 上將會更有樂趣。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-124">Your video watching experience will be even more enjoyable on HoloLens.</span></span>
* <span data-ttu-id="7ecd9-125">您也可以在 **沒有應用程式行的情況下釘選相片** 。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-125">You can also **pin photos without the app bar** in your world.</span></span>

  <span data-ttu-id="7ecd9-126">![您可以針對2D 應用程式（例如相片）隱藏應用程式行](images/img-3626-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7ecd9-126">![The app bar can be hidden for 2D apps like photos](images/img-3626-400px.jpg)</span></span><br>
  <span data-ttu-id="7ecd9-127">應用程式行可以針對具有2D 視圖的應用程式隱藏，例如相片</span><span class="sxs-lookup"><span data-stu-id="7ecd9-127">The app bar can be hidden for apps with a 2D view, like Photos</span></span>

* <span data-ttu-id="7ecd9-128">檔案 **選擇器** 的運作方式就像您在 HoloLens 上所預期的一樣。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-128">**File picker** works just like you expect it to on HoloLens.</span></span>
* <span data-ttu-id="7ecd9-129">已更新 **Edge 瀏覽器** ，以使用桌上型電腦和手機來對應整合使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-129">Updated **Edge browser** to map unified user experience with desktop and phone.</span></span> <span data-ttu-id="7ecd9-130">我們啟用了多個瀏覽器實例、自訂 HoloLens 新索引標籤頁面、索引標籤查看，以及在新視窗中開啟，以及 power & 效能改進。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-130">We enabled multiple instances of your browser, custom HoloLens new tab page, tab peek, and open in new windows, along with power & performance improvements.</span></span>
* <span data-ttu-id="7ecd9-131">**Groove 音樂** 應用程式現在已在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-131">**Groove Music** app is now on HoloLens.</span></span> <span data-ttu-id="7ecd9-132">請造訪商店進行下載，然後在背景中嘗試播放。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-132">Visit the store to download it and try playing in the background.</span></span>
* <span data-ttu-id="7ecd9-133">您可以輕鬆地自訂應用程式在世界中的相片順序。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-133">You can easily customize how apps are arranged in your world.</span></span> <span data-ttu-id="7ecd9-134">只要按一下並拖曳中間垂直框線中的圓形，即可嘗試在調整模式中 **旋轉您** 的全像投影。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-134">Try **rotating your holograms** in adjust mode by simply click and drag on circle in the middle vertical wireframes.</span></span> <span data-ttu-id="7ecd9-135">您可能會注意到，全像全像周 **框方塊** ，以確保最大化的互動。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-135">You might notice holograms have **tighter fitted bounding boxes** to ensure maximized interaction.</span></span> <span data-ttu-id="7ecd9-136">您也可以將所有平面應用程式垂直調整 (但) 的相片和全像影像應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-136">You can also resize all flat apps vertically (except Photos and Hologram apps).</span></span>

  <span data-ttu-id="7ecd9-137">![將全像放在世界各地之後，可以旋轉全像影像](images/img-3627-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7ecd9-137">![Holograms can be rotated after you place them in the world](images/img-3627-400px.jpg)</span></span><br>
  <span data-ttu-id="7ecd9-138">將影像放在世界各地後旋轉</span><span class="sxs-lookup"><span data-stu-id="7ecd9-138">Rotate holograms after you place them in your world</span></span>

* <span data-ttu-id="7ecd9-139">我們已在此航班中進行數個 **輸入改進** 。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-139">We've made several **input improvement** in this flight.</span></span> <span data-ttu-id="7ecd9-140">您可以將一般藍牙滑鼠連接到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-140">You can connect a regular Bluetooth mouse to HoloLens.</span></span> <span data-ttu-id="7ecd9-141">Clicker 已經過微調，可讓您使用 clicker 來調整 & 移動全息的大小。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-141">The clicker has been fine-tuned to enable resizing & moving holograms with a clicker.</span></span> <span data-ttu-id="7ecd9-142">鍵盤的執行效能也比以往更好。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-142">Keyboard is also running better than ever.</span></span>
* <span data-ttu-id="7ecd9-143">現在您可以將音量向上 + 向下音量，來取得 **混合的現實圖片** 。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-143">Now you can take **mixed reality pictures** by pressing down the volume up + volume down simultaneously.</span></span> <span data-ttu-id="7ecd9-144">您也可以將您的混合現實影片 & 影片分享至 Facebook、Twitter 和 YouTube。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-144">You can also share your mixed reality captured photos & videos to Facebook, Twitter, and YouTube.</span></span>
* <span data-ttu-id="7ecd9-145">**混合現實** 影片的錄製長度上限已增加到五分鐘。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-145">The maximum recording length of **mixed reality videos** has been increased to five minutes.</span></span>
* <span data-ttu-id="7ecd9-146">**相片應用程式** 現在會從 OneDrive 串流影片，而不需要在播放前下載整部影片。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-146">**Photos app** now streams videos from OneDrive instead of having to download the entire video before playback.</span></span>
* <span data-ttu-id="7ecd9-147">我們改進了您的全像 **是您離開的地方**。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-147">We've improved how your **holograms will be right where you left them**.</span></span> <span data-ttu-id="7ecd9-148">您也會看到重新連線至 Wi-Fi 的選項，如果 HoloLens 無法偵測到您的位置，請再試一次。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-148">You'll also be presented the option to reconnect to Wi-Fi and try again if HoloLens can't detect where they are.</span></span>
* <span data-ttu-id="7ecd9-149">鍵盤具有改良的版面配置，可讓您輸入具有金鑰的 **電子郵件地址** ，讓您只要按一下，就能輸入最受歡迎的電子郵件網域。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-149">The keyboard has an **improved layout for entering email address** with keys that allow you to enter the most popular email domains with a single click.</span></span>
* <span data-ttu-id="7ecd9-150">在 OOBE 期間讓 **應用程式註冊** 速度更快，並 **自動偵測** 時區，讓您獲得最佳的第一個使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-150">Faster **app registration** and **auto detection of time zone** during OOBE, giving you the best first user experience.</span></span>
* <span data-ttu-id="7ecd9-151">**儲存體感知** 可讓您透過 [設定] 應用程式中的系統和應用程式，來查看剩餘和使用的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-151">**Storage sense** allows you to view remaining and used disk space by the system and apps in the settings app.</span></span>
* <span data-ttu-id="7ecd9-152">我們已將意見反應應用程式和內建整合至單一應用程式 **意見反應中樞**，這是可讓我們對您喜愛的功能 **提供意見** 反應、哪些是需要改進的功能，以及您可以執行哪些作業的工具。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-152">We've converged Feedback App and Inside Hub into a single app **Feedback Hub**, which is the go-to tool for **giving us feedback** on features you love, which ones need improvement, and which ones you could do without.</span></span> <span data-ttu-id="7ecd9-153">當您加入測試人員計畫時，您可以趕上 **取得最新的 Insider 新聞**、 **費率組建** ，以及前往意見反應中樞的 **意見反應探索」** 。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-153">When you join the Insider Program, you can keep up on **get latest Insider news**, **rate builds** and go on **feedback quests** from Feedback Hub.</span></span>
* <span data-ttu-id="7ecd9-154">我們也 [發行了更新的 HoloLens 模擬器](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools) 組建。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-154">We've also [published an updated HoloLens Emulator](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools) build.</span></span>
* <span data-ttu-id="7ecd9-155">您的混合現實影片現在看起來更好，因為會有自動 **影片穩定**。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-155">Your mixed reality videos now look better because of automatic **video stabilization**.</span></span>

## <a name="major-fixes"></a><span data-ttu-id="7ecd9-156">主要修正</span><span class="sxs-lookup"><span data-stu-id="7ecd9-156">Major fixes</span></span>

<span data-ttu-id="7ecd9-157">我們修正了空格可能會變慢或偵測不正確的全息圖空間的問題。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-157">We fixed issues with hologram spaces where the spaces would be slow or incorrectly detected.</span></span> <span data-ttu-id="7ecd9-158">我們已修正關機問題，可在關機期間繼續嘗試啟動 shell。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-158">We fixed a shutdown issue that could continue to try launching the shell during shutdown.</span></span>

<span data-ttu-id="7ecd9-159">修正了問題</span><span class="sxs-lookup"><span data-stu-id="7ecd9-159">We fixed an issue</span></span>
* <span data-ttu-id="7ecd9-160">這會封鎖繼續 XAML 應用程式的能力。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-160">that blocks the ability to resume a XAML application.</span></span>
* <span data-ttu-id="7ecd9-161">發生損毀的情況下，會離開黑色畫面和一些不規則線條。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-161">where a crash would leave a black screen and some jagged lines.</span></span>
* <span data-ttu-id="7ecd9-162">使用某些應用程式時，滾動有時候會有錯誤的方向。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-162">scrolling would sometimes stick in the wrong direction when using some apps.</span></span>
* <span data-ttu-id="7ecd9-163">電源 Led 可能指出裝置仍在開啟時的關閉狀態。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-163">the power LEDs could indicate an off state when the device was still on.</span></span>
* <span data-ttu-id="7ecd9-164">從待命恢復之後，WiFi 可能會關閉。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-164">WiFi could get turned off after resuming from standby.</span></span>
* <span data-ttu-id="7ecd9-165">Xbox 身分識別提供者會提供玩家代號設定，然後卡在迴圈中。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-165">the Xbox identity provider offers gamertag setup and then gets stuck in a loop.</span></span>
* <span data-ttu-id="7ecd9-166">在 OneDrive 檔案選擇器中選取下載的檔案時，Shell 偶爾會損毀。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-166">the Shell occasionally crashes when selecting a downloaded file in the OneDrive File Picker.</span></span>
* <span data-ttu-id="7ecd9-167">按住連結有時會開啟新的、中斷的索引標籤，並開啟內容功能表。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-167">pressing and holding on a link sometimes both opens a new, broken tab and opens a context menu.</span></span>
* <span data-ttu-id="7ecd9-168">windows 裝置入口網站不允許從50到80的 IPD 調整</span><span class="sxs-lookup"><span data-stu-id="7ecd9-168">where windows device portal didn’t allow IPD adjustments from 50 to 80</span></span>

<span data-ttu-id="7ecd9-169">我們修正了相片的問題，其中</span><span class="sxs-lookup"><span data-stu-id="7ecd9-169">We fixed issues with Photos where</span></span>
* <span data-ttu-id="7ecd9-170">影像偶爾會顯示旋轉，因為忽略了 [略過 EXIF 方向] 屬性。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-170">an image would occasionally display rotated because ignoring EXIF orientation property was ignored.</span></span>
* <span data-ttu-id="7ecd9-171">它可能會在已釘選的相片上啟動時損毀。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-171">it could crash during start-up on pinned Photos.</span></span>
* <span data-ttu-id="7ecd9-172">影片會在暫停後重新開機，而不是從上次暫停的位置繼續進行。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-172">videos would restart after pausing instead of continuing from where last paused.</span></span>
* <span data-ttu-id="7ecd9-173">如果共用的影片在播放時共用，可能會防止重新播放。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-173">replay of a shared video could be prevented if it was shared while playing.</span></span>
* <span data-ttu-id="7ecd9-174">混合實境擷取錄製的開頭為 0.5-1 秒的僅限音訊摘要。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-174">Mixed Reality Capture recordings would begin with 0.5-1 second of audio only feed.</span></span>
* <span data-ttu-id="7ecd9-175">[同步] 按鈕會在初始 OneDrive 同步處理期間消失。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-175">the Sync button disappears during initial OneDrive sync.</span></span>

<span data-ttu-id="7ecd9-176">我們修正了設定的問題，其中</span><span class="sxs-lookup"><span data-stu-id="7ecd9-176">We fixed issues with settings where</span></span>
* <span data-ttu-id="7ecd9-177">當環境變更時，需要重新整理。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-177">a refresh was needed when the environment changes.</span></span>
* <span data-ttu-id="7ecd9-178">鍵盤上的「輸入」不像在某些對話方塊中按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-178">'Enter' on keyboard wouldn't behave like clicking Next in some dialogs.</span></span>
* <span data-ttu-id="7ecd9-179">clicker 無法配對時，很難得知。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-179">it was hard to know when the clicker failed pairing.</span></span>
* <span data-ttu-id="7ecd9-180">它可能會因為 WiFi 中斷連線和連線而沒有回應。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-180">it could become unresponsive with WiFi disconnect and connect.</span></span>

<span data-ttu-id="7ecd9-181">我們修正了 Cortana 的問題，其中</span><span class="sxs-lookup"><span data-stu-id="7ecd9-181">We fixed issues with Cortana where</span></span>
* <span data-ttu-id="7ecd9-182">它可能會卡在顯示接聽的 UI。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-182">it could get stuck displaying the Listening UI.</span></span>
* <span data-ttu-id="7ecd9-183">如果您對離開應用程式的要求回答了可能的話，請詢問「嗨 Cortana，我可以從獨佔模式應用程式取得什麼」。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-183">asking "Hey Cortana, what can I say" from an exclusive mode app would get stuck if you answered maybe rather yes/no to the request to exit the app.</span></span>
* <span data-ttu-id="7ecd9-184">如果您要求 Cortana 進入睡眠狀態，然後再繼續，Cortana 接聽 UI 就不會正確地繼續。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-184">the Cortana listening UI doesn't resume correctly if you ask Cortana to go to sleep and then resume.</span></span>
* <span data-ttu-id="7ecd9-185">「我連接到什麼網路？」查詢</span><span class="sxs-lookup"><span data-stu-id="7ecd9-185">the queries "What network am I connected to?"</span></span> <span data-ttu-id="7ecd9-186">「我連接了嗎？」</span><span class="sxs-lookup"><span data-stu-id="7ecd9-186">and the "Am I connected?"</span></span> <span data-ttu-id="7ecd9-187">當第一個網路設定檔案修復沒有連線能力時，可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-187">could fail when the first network profile comes back with no connectivity.</span></span>
* <span data-ttu-id="7ecd9-188">UI 旁邊在「正在接聽」上，但在結束應用程式時，會立即開始執行語音辨識。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-188">the UI froze on "Listening" but upon exiting an app would immediately began doing speech recognition again.</span></span>
* <span data-ttu-id="7ecd9-189">當您登出 Cortana 應用程式時，不會讓您重新登入，直到重新開機為止。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-189">where signing out of the Cortana app wouldn't let you sign back into it until a reboot.</span></span>
* <span data-ttu-id="7ecd9-190">當混合實境擷取 UI 處於作用中狀態時，它不會啟動。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-190">it wouldn't launch when Mixed Reality Capture UI was active.</span></span>

<span data-ttu-id="7ecd9-191">我們已修正 Visual Studio 的問題，其中</span><span class="sxs-lookup"><span data-stu-id="7ecd9-191">We fixed issues with Visual Studio where</span></span>
* <span data-ttu-id="7ecd9-192">背景工作調試無法運作。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-192">background task debugging didn't work.</span></span>
* <span data-ttu-id="7ecd9-193">圖形偵錯工具中的畫面格分析無法運作。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-193">frame analysis in the graphics debugger didn't work.</span></span>
* <span data-ttu-id="7ecd9-194">HoloLens 模擬器不會出現在 Visual Studio 的下拉式清單中，除非您的專案 TargetPlatformVersion 設定為10240。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-194">the HoloLens Emulator didn't' appear in the drop-down list for Visual Studio unless your project's TargetPlatformVersion was set to 10240.</span></span>

## <a name="changes-from-previous-release"></a><span data-ttu-id="7ecd9-195">先前版本的變更</span><span class="sxs-lookup"><span data-stu-id="7ecd9-195">Changes from previous release</span></span>
* <span data-ttu-id="7ecd9-196">Cortana 命令 **嗨 Cortana，重新開機裝置** 無法運作。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-196">The Cortana command **Hey Cortana, reboot the device** doesn't work.</span></span> <span data-ttu-id="7ecd9-197">使用者可以說 **嗨 Cortana、重新開機** 或 **嗨 Cortana，重新開機裝置**。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-197">User can say **Hey Cortana, restart** or **Hey Cortana, restart the device**.</span></span>
* <span data-ttu-id="7ecd9-198">已從產品中移除 Kiosk 模式。</span><span class="sxs-lookup"><span data-stu-id="7ecd9-198">Kiosk mode has been removed from the product.</span></span>

## <a name="prior-release-notes"></a><span data-ttu-id="7ecd9-199">先前的版本資訊</span><span class="sxs-lookup"><span data-stu-id="7ecd9-199">Prior release notes</span></span>
* [<span data-ttu-id="7ecd9-200">版本資訊 - 2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="7ecd9-200">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="7ecd9-201">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ecd9-201">See also</span></span>
* [<span data-ttu-id="7ecd9-202">HoloLens 的已知問題</span><span class="sxs-lookup"><span data-stu-id="7ecd9-202">HoloLens known issues</span></span>](https://docs.microsoft.com/windows/mixed-reality/hololens-known-issues)
* [<span data-ttu-id="7ecd9-203">安裝工具</span><span class="sxs-lookup"><span data-stu-id="7ecd9-203">Install the tools</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools)
* [<span data-ttu-id="7ecd9-204">Shell</span><span class="sxs-lookup"><span data-stu-id="7ecd9-204">Shell</span></span>](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)
* [<span data-ttu-id="7ecd9-205">更新混合實境的 2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="7ecd9-205">Updating 2D UWP apps for mixed reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/building-2d-apps)
* [<span data-ttu-id="7ecd9-206">硬體配件</span><span class="sxs-lookup"><span data-stu-id="7ecd9-206">Hardware accessories</span></span>](https://docs.microsoft.com/windows/mixed-reality/discover/hardware-accessories)
* [<span data-ttu-id="7ecd9-207">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="7ecd9-207">Mixed reality capture</span></span>](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture)
* [<span data-ttu-id="7ecd9-208">語音輸入</span><span class="sxs-lookup"><span data-stu-id="7ecd9-208">Voice input</span></span>](https://docs.microsoft.com/windows/mixed-reality/design/voice-input)
* [<span data-ttu-id="7ecd9-209">將應用程式提交到 Windows Store</span><span class="sxs-lookup"><span data-stu-id="7ecd9-209">Submitting an app to the Windows Store</span></span>](https://docs.microsoft.com/windows/mixed-reality/distribute/submitting-an-app-to-the-microsoft-store)
* [<span data-ttu-id="7ecd9-210">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="7ecd9-210">Using the HoloLens emulator</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)
