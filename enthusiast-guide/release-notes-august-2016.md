---
title: 版本資訊 - 2016 年 8 月
description: 'Windows 10 周年版本的 HoloLens 版本資訊 (2016) '
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、版本資訊、os、平臺、功能、商用套件
ms.openlocfilehash: 8df7f745e20d350d06945d2c1a9ead3564558439
ms.sourcegitcommit: 838bebf6bacac4047feff493c0847d4e6371976f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "91783934"
---
# <a name="release-notes---august-2016"></a><span data-ttu-id="5b465-104">版本資訊 - 2016 年 8 月</span><span class="sxs-lookup"><span data-stu-id="5b465-104">Release notes - August 2016</span></span>

<span data-ttu-id="5b465-105">HoloLens 團隊正在聆聽 Windows 測試人員計畫開發人員的意見反應，以排定工作的優先順序。</span><span class="sxs-lookup"><span data-stu-id="5b465-105">The HoloLens team is listening to feedback from developers in the Windows Insider Program to prioritize our work.</span></span> <span data-ttu-id="5b465-106">請繼續透過意見反應中樞、[開發人員論壇](https://forums.hololens.com) [ @HoloLens 和 Twitter ](https://twitter.com/hololens)[提供意見](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)反應給我們。</span><span class="sxs-lookup"><span data-stu-id="5b465-106">Please continue to [give us feedback](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span> <span data-ttu-id="5b465-107">由於 Windows 10 將周年年度更新，因此 HoloLens 團隊很高興能更能改進全像全像全像全像全像全像全像的</span><span class="sxs-lookup"><span data-stu-id="5b465-107">As Windows 10 embraces the Anniversary Update, the HoloLens team is happy to deliver further improve to the holographic experience.</span></span> <span data-ttu-id="5b465-108">在這項更新中，我們將焦點放在企業要求的主要修正、改進和推出功能，並可在 Microsoft HoloLens Commercial Suite 中使用。</span><span class="sxs-lookup"><span data-stu-id="5b465-108">In this update, we focused on major fixes, improvements, and introducing features requested by businesses and available in the Microsoft HoloLens Commercial Suite.</span></span>

<span data-ttu-id="5b465-109">**最新版本：** Windows 全像2016年8月更新 ( **10.0.14393.0** ，Windows 10 周年版) </span><span class="sxs-lookup"><span data-stu-id="5b465-109">**Latest release:** Windows Holographic August 2016 Update ( **10.0.14393.0** , Windows 10 Anniversary Release)</span></span>

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

<span data-ttu-id="5b465-110">若要 [更新為最新版本](https://docs.microsoft.com/windows/mixed-reality/updating-hololens)，請開啟 [ *設定* ] 應用程式，移至 [ *更新 & 安全性* ]，然後選取 [ *檢查更新* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5b465-110">To [update to the current release](https://docs.microsoft.com/windows/mixed-reality/updating-hololens), open the *Settings* app, go to *Update & Security* , then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="5b465-111">新功能</span><span class="sxs-lookup"><span data-stu-id="5b465-111">New features</span></span>

<span data-ttu-id="5b465-112">**附加至進程的調試** 程式HoloLens 現在支援附加至進程的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5b465-112">**Attach To Process Debugging** HoloLens now supports attach-to-process debugging.</span></span> <span data-ttu-id="5b465-113">您可以使用 Visual Studio 2015 Update 3 連接到 HoloLens 上的執行中應用程式，並 [開始進行調試](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app)程式。</span><span class="sxs-lookup"><span data-stu-id="5b465-113">You can use Visual Studio 2015 Update 3 to connect to a running app on a HoloLens and [start debugging it](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app).</span></span> <span data-ttu-id="5b465-114">這種運作方式不需要從 Visual Studio 專案進行部署。</span><span class="sxs-lookup"><span data-stu-id="5b465-114">This works without the need to deploy from a Visual Studio project.</span></span>

<span data-ttu-id="5b465-115">**已更新 HoloLens 模擬器** 我們也發行了 HoloLens 模擬器的更新版本。</span><span class="sxs-lookup"><span data-stu-id="5b465-115">**Updated HoloLens Emulator** We've also released an updated version of the HoloLens Emulator.</span></span>

<span data-ttu-id="5b465-116">**遊戲台支援** 您現在可以將藍牙 gamepads 與 HoloLens 配對！</span><span class="sxs-lookup"><span data-stu-id="5b465-116">**Gamepad Support** You can now pair and use Bluetooth gamepads with HoloLens!</span></span> <span data-ttu-id="5b465-117">新發行的 Xbox 無線控制器提供藍牙功能，可用來播放您最愛的遊戲和應用程式。</span><span class="sxs-lookup"><span data-stu-id="5b465-117">The newly released Xbox Wireless Controller S features Bluetooth capabilities and can be used to play your favorite gamepad-enabled games and apps.</span></span> <span data-ttu-id="5b465-118">必須先套用 [控制器更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) ，才能將 Xbox 無線控制器連線至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5b465-118">A [controller update](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) must be applied before you can connect the Xbox Wireless Controller S with HoloLens.</span></span> <span data-ttu-id="5b465-119">[XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)和 Windows 的支援 Xbox 無線控制器。請[輸入](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx)api。</span><span class="sxs-lookup"><span data-stu-id="5b465-119">The Xbox Wireless Controller S is supported by [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) and [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) APIs.</span></span> <span data-ttu-id="5b465-120">您可以透過 [Windows. 輸入](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API 來存取藍牙控制器的其他模型。</span><span class="sxs-lookup"><span data-stu-id="5b465-120">Additional models of Bluetooth controllers may be accessed through the [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.</span></span>

## <a name="improvements-and-fixes"></a><span data-ttu-id="5b465-121">改良功能與修正</span><span class="sxs-lookup"><span data-stu-id="5b465-121">Improvements and fixes</span></span>

<span data-ttu-id="5b465-122">我們會與其余的 Windows 10 周年更新進行同步處理，因此除了 HoloLens 專屬的修正之外，您也可以從 Windows update 獲得最高的效能，以提升平臺的可靠性和效能。</span><span class="sxs-lookup"><span data-stu-id="5b465-122">We are in sync with the rest of the Windows 10 Anniversary update, so in addition to the HoloLens specific fixes, you are also receiving all the goodness from the Windows update to increase platform reliability and performance.</span></span> <span data-ttu-id="5b465-123">您的意見反應對於發行中的修正具有高度價值和優先。</span><span class="sxs-lookup"><span data-stu-id="5b465-123">Your feedback is highly valued and prioritized for fixes in the release.</span></span>

<span data-ttu-id="5b465-124">我們已改善下列體驗：</span><span class="sxs-lookup"><span data-stu-id="5b465-124">We've improved the following experiences:</span></span>
* <span data-ttu-id="5b465-125">登入體驗。</span><span class="sxs-lookup"><span data-stu-id="5b465-125">log in experiences.</span></span>
* <span data-ttu-id="5b465-126">workplace join。</span><span class="sxs-lookup"><span data-stu-id="5b465-126">workplace join.</span></span>
* <span data-ttu-id="5b465-127">裝置電源狀態轉換的電源效率。</span><span class="sxs-lookup"><span data-stu-id="5b465-127">power efficiency for device power state transitions.</span></span>
* <span data-ttu-id="5b465-128">混合現實的穩定性。</span><span class="sxs-lookup"><span data-stu-id="5b465-128">stability with Mixed Reality Captures.</span></span>
* <span data-ttu-id="5b465-129">藍牙連線能力的可靠性</span><span class="sxs-lookup"><span data-stu-id="5b465-129">reliability for Bluetooth connectivity</span></span>
* <span data-ttu-id="5b465-130">多個應用程式案例中的全息圖持續性。</span><span class="sxs-lookup"><span data-stu-id="5b465-130">hologram persistence in multi app scenario.</span></span>

<span data-ttu-id="5b465-131">我們已修正下列問題：</span><span class="sxs-lookup"><span data-stu-id="5b465-131">We've fixed the following issues:</span></span>
* <span data-ttu-id="5b465-132">Visual Studio 分析工具和圖形偵錯工具無法連接。</span><span class="sxs-lookup"><span data-stu-id="5b465-132">the Visual Studio profilers and graphics debugger fail to connect.</span></span>
* <span data-ttu-id="5b465-133">相片 & 檔不會顯示在裝置入口網站的 [檔案瀏覽器] 中。</span><span class="sxs-lookup"><span data-stu-id="5b465-133">photos & documents do not show up in the file explorer in the device portal.</span></span>
* <span data-ttu-id="5b465-134">當游標放在調整模式時，應用程式行可以閃爍。</span><span class="sxs-lookup"><span data-stu-id="5b465-134">the App Bar can flash when the cursor is placed above it while in Adjust mode.</span></span>
* <span data-ttu-id="5b465-135">當處於調整模式時，眼睛的點游標會變更為4箭號的游標。</span><span class="sxs-lookup"><span data-stu-id="5b465-135">When in Adjust mode, the eye gaze dot cursor will change to the 4-arrow cursor sometime more slowly.</span></span>
* <span data-ttu-id="5b465-136">「嗨 Cortana 播放音樂」並不會啟動 Groove。</span><span class="sxs-lookup"><span data-stu-id="5b465-136">"Hey Cortana play music" does not launch Groove.</span></span>
* <span data-ttu-id="5b465-137">在上一次更新之後，說 "Go Home" 並不會正確地顯示釘選面板。</span><span class="sxs-lookup"><span data-stu-id="5b465-137">after the previous update, saying "Go Home" does not display the pins panel correctly.</span></span>

## <a name="introducing-microsoft-hololens-commercial-suite"></a><span data-ttu-id="5b465-138">Microsoft HoloLens Commercial Suite 簡介</span><span class="sxs-lookup"><span data-stu-id="5b465-138">Introducing Microsoft HoloLens Commercial Suite</span></span>

<span data-ttu-id="5b465-139">Microsoft HoloLens Commercial Suite 已準備好進行企業部署。</span><span class="sxs-lookup"><span data-stu-id="5b465-139">The Microsoft HoloLens Commercial Suite is ready for enterprise deployment.</span></span> <span data-ttu-id="5b465-140">我們為早期商務夥伴新增了數個高度要求的 [商業功能](https://docs.microsoft.com/windows/mixed-reality/commercial-features) 。</span><span class="sxs-lookup"><span data-stu-id="5b465-140">We've added several highly requested [commercial features](https://docs.microsoft.com/windows/mixed-reality/commercial-features) from our early business partners.</span></span>

<span data-ttu-id="5b465-141">請洽詢您的當地 Microsoft 帳戶經理購買 Microsoft HoloLens Commercial Suite。</span><span class="sxs-lookup"><span data-stu-id="5b465-141">Please contact your local Microsoft account manager to purchase the Microsoft HoloLens Commercial Suite.</span></span>

### <a name="key-commercial-features"></a><span data-ttu-id="5b465-142">重要的商業功能</span><span class="sxs-lookup"><span data-stu-id="5b465-142">Key Commercial Features</span></span> 

* <span data-ttu-id="5b465-143">**Kiosk 模式。**</span><span class="sxs-lookup"><span data-stu-id="5b465-143">**Kiosk mode.**</span></span> <span data-ttu-id="5b465-144">使用 HoloLens kiosk 模式，您可以限制要執行的應用程式，以啟用示範或展示體驗。</span><span class="sxs-lookup"><span data-stu-id="5b465-144">With HoloLens kiosk mode, you can limit which apps to run to enable demo or showcase experiences.</span></span><br>
  <span data-ttu-id="5b465-145">![在 kiosk 模式中，HoloLens 會直接在您選擇的應用程式中啟動。](images/201608-kioskmode-400px.png)</span><span class="sxs-lookup"><span data-stu-id="5b465-145">![With kiosk mode, HoloLens launches directly into the app of your choice.](images/201608-kioskmode-400px.png)</span></span>
* <span data-ttu-id="5b465-146">**適用于 HoloLens 的 Mobile 裝置管理 (MDM) 。**</span><span class="sxs-lookup"><span data-stu-id="5b465-146">**Mobile Device Management (MDM) for HoloLens.**</span></span> <span data-ttu-id="5b465-147">您的 IT 部門可以使用 Microsoft Intune 之類的解決方案，同時管理多個 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="5b465-147">Your IT department can manage multiple HoloLens devices simultaneously using solutions like Microsoft Intune.</span></span> <span data-ttu-id="5b465-148">您可以管理設定、選取要安裝的應用程式，並且設定針對您組織所需來量身訂做的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="5b465-148">You will be able to manage settings, select apps to install and set security configurations tailored to your organization's need.</span></span><br>
  <span data-ttu-id="5b465-149">![在 HoloLens 上的 Mobile 裝置管理可提供跨多個裝置的企業級裝置管理。](images/201608-enterprisemanagement-400px.png)</span><span class="sxs-lookup"><span data-stu-id="5b465-149">![Mobile Device Management on HoloLens provides enterprise grade device management across multiple devices.](images/201608-enterprisemanagement-400px.png)</span></span>
* <span data-ttu-id="5b465-150">**商務用 Windows Update。**</span><span class="sxs-lookup"><span data-stu-id="5b465-150">**Windows Update for Business.**</span></span> <span data-ttu-id="5b465-151">裝置的受控制作業系統更新和長期維護分支的支援。</span><span class="sxs-lookup"><span data-stu-id="5b465-151">Controlled operating system updates to devices and support for long term servicing branch.</span></span>
* <span data-ttu-id="5b465-152">**資料安全性。**</span><span class="sxs-lookup"><span data-stu-id="5b465-152">**Data security.**</span></span> <span data-ttu-id="5b465-153">在 HoloLens 上啟用 BitLocker 資料加密，以提供與任何其他 Windows 裝置相同等級的安全性保護。</span><span class="sxs-lookup"><span data-stu-id="5b465-153">BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.</span></span>
* <span data-ttu-id="5b465-154">**公司存取。**</span><span class="sxs-lookup"><span data-stu-id="5b465-154">**Work access.**</span></span> <span data-ttu-id="5b465-155">您組織中的任何人都可以透過 HoloLens 上的虛擬私人網路，從遠端連線到公司網路。</span><span class="sxs-lookup"><span data-stu-id="5b465-155">Anyone in your organization can remotely connect to the corporate network through virtual private network on a HoloLens.</span></span> <span data-ttu-id="5b465-156">HoloLens 也可以存取需要認證的 Wi-fi 網路。</span><span class="sxs-lookup"><span data-stu-id="5b465-156">HoloLens can also access Wi-Fi networks that require credentials.</span></span>
* <span data-ttu-id="5b465-157">**商務用 Microsoft Store。**</span><span class="sxs-lookup"><span data-stu-id="5b465-157">**Microsoft Store for Business.**</span></span> <span data-ttu-id="5b465-158">您的 IT 部門也可以設定企業私用存放區，其中只包含公司的應用程式，以符合您的特定 HoloLens 使用量。</span><span class="sxs-lookup"><span data-stu-id="5b465-158">Your IT department can also set up an enterprise private store, containing only your company’s apps for your specific HoloLens usage.</span></span> <span data-ttu-id="5b465-159">安全地將企業軟體散發給選定的企業使用者群組。</span><span class="sxs-lookup"><span data-stu-id="5b465-159">Securely distribute your enterprise software to selected group of enterprise users.</span></span>

### <a name="development-edition-vs-commercial-suite"></a><span data-ttu-id="5b465-160">開發版與商用套件</span><span class="sxs-lookup"><span data-stu-id="5b465-160">Development Edition vs. Commercial Suite</span></span>

<table>
<tr>
<th><span data-ttu-id="5b465-161">功能</span><span class="sxs-lookup"><span data-stu-id="5b465-161">Features</span></span></th><th><span data-ttu-id="5b465-162">Development 版</span><span class="sxs-lookup"><span data-stu-id="5b465-162">Development Edition</span></span></th><th><span data-ttu-id="5b465-163">商業套件</span><span class="sxs-lookup"><span data-stu-id="5b465-163">Commercial Suite</span></span></th>
</tr><tr>
<td><span data-ttu-id="5b465-164">裝置加密 (Bitlocker) </span><span class="sxs-lookup"><span data-stu-id="5b465-164">Device Encryption (Bitlocker)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="5b465-165">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-165">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-166">虛擬私人網路 (VPN)</span><span class="sxs-lookup"><span data-stu-id="5b465-166">Virtual Private Network (VPN)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="5b465-167">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-167">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-168"><a href="https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Kiosk 模式</a></span><span class="sxs-lookup"><span data-stu-id="5b465-168"><a href="https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Kiosk mode</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="5b465-169">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-169">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="5b465-170">管理和部署</span><span class="sxs-lookup"><span data-stu-id="5b465-170">Management and deployment</span></span></th>
</tr><tr>
<td><span data-ttu-id="5b465-171">行動裝置管理 (MDM)</span><span class="sxs-lookup"><span data-stu-id="5b465-171">Mobile Device Management (MDM)</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="5b465-172">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-172">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-173">封鎖取消註冊的能力</span><span class="sxs-lookup"><span data-stu-id="5b465-173">Ability to block un-enrollment</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="5b465-174">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-174">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-175">以憑證為基礎的公司 Wi-fi 存取</span><span class="sxs-lookup"><span data-stu-id="5b465-175">Cert Based Corporate Wi-Fi Access</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="5b465-176">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-176">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-177">Microsoft Store (取用者) </span><span class="sxs-lookup"><span data-stu-id="5b465-177">Microsoft Store (Consumer)</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-178">消費者</span><span class="sxs-lookup"><span data-stu-id="5b465-178">Consumer</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-179">透過 MDM 篩選</span><span class="sxs-lookup"><span data-stu-id="5b465-179">Filtering via MDM</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Business Store 入口網站</a></span><span class="sxs-lookup"><span data-stu-id="5b465-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Business Store Portal</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="5b465-181">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-181">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="5b465-182">安全性與身分識別</span><span class="sxs-lookup"><span data-stu-id="5b465-182">Security and Identity</span></span></th>
</tr><tr>
<td><span data-ttu-id="5b465-183">使用 Azure Active Directory (AAD) 登入</span><span class="sxs-lookup"><span data-stu-id="5b465-183">Login with Azure Active Directory (AAD)</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-184">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-184">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-185">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-185">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-186">使用 Microsoft 帳戶登入 (MSA) </span><span class="sxs-lookup"><span data-stu-id="5b465-186">Login with Microsoft Account (MSA)</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-187">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-187">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-188">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-188">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-189">使用 PIN 解除鎖定的新一代認證</span><span class="sxs-lookup"><span data-stu-id="5b465-189">Next Generation Credentials with PIN unlock</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-190">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-190">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-191">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-191">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">安全開機</a></span><span class="sxs-lookup"><span data-stu-id="5b465-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Secure boot</a></span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-193">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-193">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-194">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-194">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="5b465-195">服務與支援</span><span class="sxs-lookup"><span data-stu-id="5b465-195">Servicing and Support</span></span></th>
</tr><tr>
<td><span data-ttu-id="5b465-196">系統自動更新到達時</span><span class="sxs-lookup"><span data-stu-id="5b465-196">Automatic system updates as they arrive</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-197">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-197">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="5b465-198">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-198">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></span><span class="sxs-lookup"><span data-stu-id="5b465-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="5b465-200">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-200">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="5b465-201">長期維護分支</span><span class="sxs-lookup"><span data-stu-id="5b465-201">Long term servicing branch</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="5b465-202">✔️</span><span class="sxs-lookup"><span data-stu-id="5b465-202">✔️</span></span></td>
</tr>
</table>

## <a name="prior-release-notes"></a><span data-ttu-id="5b465-203">先前的版本資訊</span><span class="sxs-lookup"><span data-stu-id="5b465-203">Prior release notes</span></span>
* [<span data-ttu-id="5b465-204">版本資訊 - 2016 年 5 月</span><span class="sxs-lookup"><span data-stu-id="5b465-204">Release notes - May 2016</span></span>](release-notes-may-2016.md)
* [<span data-ttu-id="5b465-205">版本資訊 - 2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="5b465-205">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="5b465-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b465-206">See also</span></span>
* [<span data-ttu-id="5b465-207">HoloLens 的已知問題</span><span class="sxs-lookup"><span data-stu-id="5b465-207">HoloLens known issues</span></span>](https://docs.microsoft.com/windows/mixed-reality/hololens-known-issues)
* [<span data-ttu-id="5b465-208">商業功能</span><span class="sxs-lookup"><span data-stu-id="5b465-208">Commercial features</span></span>](https://docs.microsoft.com/windows/mixed-reality/commercial-features)
* [<span data-ttu-id="5b465-209">安裝工具</span><span class="sxs-lookup"><span data-stu-id="5b465-209">Install the tools</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools)
* [<span data-ttu-id="5b465-210">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="5b465-210">Using the HoloLens emulator</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)
