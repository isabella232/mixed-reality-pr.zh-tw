---
title: 版本資訊 - 2016 年 8 月
description: 針對2016年秋季的 Windows 10 周年版本，隨時掌握 HoloLens 版本資訊。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、版本資訊、os、平臺、功能、商用套件
ms.openlocfilehash: c70da10043cfbcfa88105635f2467c8feaadbedf
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581642"
---
# <a name="release-notes---august-2016"></a><span data-ttu-id="7a42e-104">版本資訊 - 2016 年 8 月</span><span class="sxs-lookup"><span data-stu-id="7a42e-104">Release notes - August 2016</span></span>

<span data-ttu-id="7a42e-105">HoloLens 團隊正在聆聽 Windows 測試人員計畫開發人員的意見反應，以排定工作的優先順序。</span><span class="sxs-lookup"><span data-stu-id="7a42e-105">The HoloLens team is listening to feedback from developers in the Windows Insider Program to prioritize our work.</span></span> <span data-ttu-id="7a42e-106">繼續透過意見反應中樞、[開發人員論壇](https://forums.hololens.com) [ @HoloLens 和 Twitter ](https://twitter.com/hololens)[提供意見](/windows/mixed-reality/give-us-feedback)反應給我們。</span><span class="sxs-lookup"><span data-stu-id="7a42e-106">Continue to [give us feedback](/windows/mixed-reality/give-us-feedback) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span> <span data-ttu-id="7a42e-107">由於 Windows 10 將周年年度更新，因此 HoloLens 團隊很高興能更能改進全像全像全像全像全像全像全像的</span><span class="sxs-lookup"><span data-stu-id="7a42e-107">As Windows 10 embraces the Anniversary Update, the HoloLens team is happy to deliver further improve to the holographic experience.</span></span> <span data-ttu-id="7a42e-108">在這項更新中，我們將焦點放在企業要求的主要修正、改進和推出功能，並可在 Microsoft HoloLens Commercial Suite 中使用。</span><span class="sxs-lookup"><span data-stu-id="7a42e-108">In this update, we focused on major fixes, improvements, and introducing features requested by businesses and available in the Microsoft HoloLens Commercial Suite.</span></span>

<span data-ttu-id="7a42e-109">**最新版本：** Windows 全像2016年8月更新 (**10.0.14393.0**，Windows 10 周年版) </span><span class="sxs-lookup"><span data-stu-id="7a42e-109">**Latest release:** Windows Holographic August 2016 Update (**10.0.14393.0**, Windows 10 Anniversary Release)</span></span>

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

<span data-ttu-id="7a42e-110">若要 [更新為最新版本](/windows/mixed-reality/updating-hololens)，請開啟 [ *設定* ] 應用程式，移至 [ *更新 & 安全性*]，然後選取 [ *檢查更新* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7a42e-110">To [update to the current release](/windows/mixed-reality/updating-hololens), open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="7a42e-111">新功能</span><span class="sxs-lookup"><span data-stu-id="7a42e-111">New features</span></span>

<span data-ttu-id="7a42e-112">**附加至進程的調試** 程式HoloLens 現在支援附加至進程的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7a42e-112">**Attach To Process Debugging** HoloLens now supports attach-to-process debugging.</span></span> <span data-ttu-id="7a42e-113">您可以使用 Visual Studio 2015 Update 3 連接到 HoloLens 上的執行中應用程式，並 [開始進行調試](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app)程式。</span><span class="sxs-lookup"><span data-stu-id="7a42e-113">You can use Visual Studio 2015 Update 3 to connect to a running app on a HoloLens and [start debugging it](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app).</span></span> <span data-ttu-id="7a42e-114">這種運作方式不需要從 Visual Studio 專案進行部署。</span><span class="sxs-lookup"><span data-stu-id="7a42e-114">This works without the need to deploy from a Visual Studio project.</span></span>

<span data-ttu-id="7a42e-115">**已更新 HoloLens 模擬器** 我們也發行了 HoloLens 模擬器的更新版本。</span><span class="sxs-lookup"><span data-stu-id="7a42e-115">**Updated HoloLens Emulator** We've also released an updated version of the HoloLens Emulator.</span></span>

<span data-ttu-id="7a42e-116">**遊戲台支援** 您現在可以將藍牙 gamepads 與 HoloLens 配對！</span><span class="sxs-lookup"><span data-stu-id="7a42e-116">**Gamepad Support** You can now pair and use Bluetooth gamepads with HoloLens!</span></span> <span data-ttu-id="7a42e-117">新發行的 Xbox 無線控制器提供藍牙功能，可用來播放您最愛的遊戲和應用程式。</span><span class="sxs-lookup"><span data-stu-id="7a42e-117">The newly released Xbox Wireless Controller S features Bluetooth capabilities and can be used to play your favorite gamepad-enabled games and apps.</span></span> <span data-ttu-id="7a42e-118">必須先套用 [控制器更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) ，才能將 Xbox 無線控制器連線至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="7a42e-118">A [controller update](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) must be applied before you can connect the Xbox Wireless Controller S with HoloLens.</span></span> <span data-ttu-id="7a42e-119">[XInput](/windows/win32/xinput/xinput-game-controller-apis-portal)和 Windows 的支援 Xbox 無線控制器。請[輸入](/uwp/api/Windows.Gaming.Input)api。</span><span class="sxs-lookup"><span data-stu-id="7a42e-119">The Xbox Wireless Controller S is supported by [XInput](/windows/win32/xinput/xinput-game-controller-apis-portal) and [Windows.Gaming.Input](/uwp/api/Windows.Gaming.Input) APIs.</span></span> <span data-ttu-id="7a42e-120">您可以透過 [Windows. 輸入](/uwp/api/Windows.Gaming.Input) API 存取更多藍牙控制器模型。</span><span class="sxs-lookup"><span data-stu-id="7a42e-120">You can access more Bluetooth controllers models through the [Windows.Gaming.Input](/uwp/api/Windows.Gaming.Input) API.</span></span>

## <a name="improvements-and-fixes"></a><span data-ttu-id="7a42e-121">改良功能與修正</span><span class="sxs-lookup"><span data-stu-id="7a42e-121">Improvements and fixes</span></span>

<span data-ttu-id="7a42e-122">我們會與其余的 Windows 10 周年更新進行同步處理，因此除了 HoloLens 專屬的修正之外，您還可以從 Windows update 獲得最高的效能，以提升平臺的可靠性和效能。</span><span class="sxs-lookup"><span data-stu-id="7a42e-122">We're in sync with the rest of the Windows 10 Anniversary update, so in addition to the HoloLens specific fixes, you're also receiving all the goodness from the Windows update to increase platform reliability and performance.</span></span> <span data-ttu-id="7a42e-123">您的意見反應對於發行中的修正具有高度價值和優先。</span><span class="sxs-lookup"><span data-stu-id="7a42e-123">Your feedback is highly valued and prioritized for fixes in the release.</span></span>

<span data-ttu-id="7a42e-124">我們已改善下列體驗：</span><span class="sxs-lookup"><span data-stu-id="7a42e-124">We've improved the following experiences:</span></span>
* <span data-ttu-id="7a42e-125">登入體驗。</span><span class="sxs-lookup"><span data-stu-id="7a42e-125">log in experiences.</span></span>
* <span data-ttu-id="7a42e-126">工作場所聯結。</span><span class="sxs-lookup"><span data-stu-id="7a42e-126">workplaces join.</span></span>
* <span data-ttu-id="7a42e-127">裝置電源狀態轉換的電源效率。</span><span class="sxs-lookup"><span data-stu-id="7a42e-127">power efficiency for device power state transitions.</span></span>
* <span data-ttu-id="7a42e-128">混合現實的穩定性。</span><span class="sxs-lookup"><span data-stu-id="7a42e-128">stability with Mixed Reality Captures.</span></span>
* <span data-ttu-id="7a42e-129">藍牙連線能力的可靠性</span><span class="sxs-lookup"><span data-stu-id="7a42e-129">reliability for Bluetooth connectivity</span></span>
* <span data-ttu-id="7a42e-130">多個應用程式案例中的全息圖持續性。</span><span class="sxs-lookup"><span data-stu-id="7a42e-130">hologram persistence in multi app scenario.</span></span>

<span data-ttu-id="7a42e-131">我們已修正下列問題：</span><span class="sxs-lookup"><span data-stu-id="7a42e-131">We've fixed the following issues:</span></span>
* <span data-ttu-id="7a42e-132">Visual Studio 分析工具和圖形偵錯工具無法連接。</span><span class="sxs-lookup"><span data-stu-id="7a42e-132">the Visual Studio profilers and graphics debugger fail to connect.</span></span>
* <span data-ttu-id="7a42e-133">相片 & 檔不會顯示在裝置入口網站的 [檔案瀏覽器] 中。</span><span class="sxs-lookup"><span data-stu-id="7a42e-133">photos & documents don't show up in the file explorer in the device portal.</span></span>
* <span data-ttu-id="7a42e-134">當游標放在調整模式時，應用程式行可以閃爍。</span><span class="sxs-lookup"><span data-stu-id="7a42e-134">the App Bar can flash when the cursor is placed above it while in Adjust mode.</span></span>
* <span data-ttu-id="7a42e-135">當處於調整模式時，眼睛的點游標會變更為4箭號的游標。</span><span class="sxs-lookup"><span data-stu-id="7a42e-135">When in Adjust mode, the eye gaze dot cursor will change to the 4-arrow cursor sometime more slowly.</span></span>
* <span data-ttu-id="7a42e-136">「嗨 Cortana 播放音樂」不會啟動 Groove。</span><span class="sxs-lookup"><span data-stu-id="7a42e-136">"Hey Cortana play music" doesn't launch Groove.</span></span>
* <span data-ttu-id="7a42e-137">在上一次更新之後，「Go Home」就不會正確地顯示釘選面板。</span><span class="sxs-lookup"><span data-stu-id="7a42e-137">after the previous update, saying "Go Home" doesn't display the pins panel correctly.</span></span>

## <a name="introducing-microsoft-hololens-commercial-suite"></a><span data-ttu-id="7a42e-138">Microsoft HoloLens Commercial Suite 簡介</span><span class="sxs-lookup"><span data-stu-id="7a42e-138">Introducing Microsoft HoloLens Commercial Suite</span></span>

<span data-ttu-id="7a42e-139">Microsoft HoloLens Commercial Suite 已準備好進行企業部署。</span><span class="sxs-lookup"><span data-stu-id="7a42e-139">The Microsoft HoloLens Commercial Suite is ready for enterprise deployment.</span></span> <span data-ttu-id="7a42e-140">我們為早期商務夥伴新增了數個高度要求的 [商業功能](/windows/mixed-reality/commercial-features) 。</span><span class="sxs-lookup"><span data-stu-id="7a42e-140">We've added several highly requested [commercial features](/windows/mixed-reality/commercial-features) from our early business partners.</span></span>

<span data-ttu-id="7a42e-141">請洽詢您的當地 Microsoft 帳戶管理員，購買 Microsoft HoloLens Commercial Suite。</span><span class="sxs-lookup"><span data-stu-id="7a42e-141">Contact your local Microsoft account manager to purchase the Microsoft HoloLens Commercial Suite.</span></span>

### <a name="key-commercial-features"></a><span data-ttu-id="7a42e-142">重要的商業功能</span><span class="sxs-lookup"><span data-stu-id="7a42e-142">Key Commercial Features</span></span> 

* <span data-ttu-id="7a42e-143">**Kiosk 模式。**</span><span class="sxs-lookup"><span data-stu-id="7a42e-143">**Kiosk mode.**</span></span> <span data-ttu-id="7a42e-144">使用 HoloLens kiosk 模式，您可以限制要執行的應用程式，以啟用示範或展示體驗。</span><span class="sxs-lookup"><span data-stu-id="7a42e-144">With HoloLens kiosk mode, you can limit which apps to run to enable demo or showcase experiences.</span></span><br>
  <span data-ttu-id="7a42e-145">![在 kiosk 模式中，HoloLens 會直接在您選擇的應用程式中啟動。](images/201608-kioskmode-400px.png)</span><span class="sxs-lookup"><span data-stu-id="7a42e-145">![With kiosk mode, HoloLens launches directly into the app of your choice.](images/201608-kioskmode-400px.png)</span></span>
* <span data-ttu-id="7a42e-146">**適用于 HoloLens 的 Mobile 裝置管理 (MDM) 。**</span><span class="sxs-lookup"><span data-stu-id="7a42e-146">**Mobile Device Management (MDM) for HoloLens.**</span></span> <span data-ttu-id="7a42e-147">您的 IT 部門可以使用 Microsoft Intune 之類的解決方案，同時管理多個 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="7a42e-147">Your IT department can manage multiple HoloLens devices simultaneously using solutions like Microsoft Intune.</span></span> <span data-ttu-id="7a42e-148">您可以管理設定、選取要安裝的應用程式，以及設定專為組織需求量身打造的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7a42e-148">You can manage settings, select apps to install and set security configurations tailored to your organization's need.</span></span><br>
  <span data-ttu-id="7a42e-149">![在 HoloLens 上的 Mobile 裝置管理可提供跨多個裝置的企業級裝置管理。](images/201608-enterprisemanagement-400px.png)</span><span class="sxs-lookup"><span data-stu-id="7a42e-149">![Mobile Device Management on HoloLens provides enterprise grade device management across multiple devices.](images/201608-enterprisemanagement-400px.png)</span></span>
* <span data-ttu-id="7a42e-150">**商務用 Windows Update。**</span><span class="sxs-lookup"><span data-stu-id="7a42e-150">**Windows Update for Business.**</span></span> <span data-ttu-id="7a42e-151">裝置的受控作業系統更新和長期維護分支的支援。</span><span class="sxs-lookup"><span data-stu-id="7a42e-151">Controlled operating system updates to devices and support for long-term servicing branch.</span></span>
* <span data-ttu-id="7a42e-152">**資料安全性。**</span><span class="sxs-lookup"><span data-stu-id="7a42e-152">**Data security.**</span></span> <span data-ttu-id="7a42e-153">在 HoloLens 上啟用 BitLocker 資料加密，以提供與任何其他 Windows 裝置相同等級的安全性保護。</span><span class="sxs-lookup"><span data-stu-id="7a42e-153">BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.</span></span>
* <span data-ttu-id="7a42e-154">**公司存取。**</span><span class="sxs-lookup"><span data-stu-id="7a42e-154">**Work access.**</span></span> <span data-ttu-id="7a42e-155">您組織中的任何人都可以透過 HoloLens 上的虛擬私人網路，從遠端連線到公司網路。</span><span class="sxs-lookup"><span data-stu-id="7a42e-155">Anyone in your organization can remotely connect to the corporate network through virtual private network on a HoloLens.</span></span> <span data-ttu-id="7a42e-156">HoloLens 也可以存取 Wi-Fi 需要認證的網路。</span><span class="sxs-lookup"><span data-stu-id="7a42e-156">HoloLens can also access Wi-Fi networks that require credentials.</span></span>
* <span data-ttu-id="7a42e-157">**商務用 Microsoft Store。**</span><span class="sxs-lookup"><span data-stu-id="7a42e-157">**Microsoft Store for Business.**</span></span> <span data-ttu-id="7a42e-158">您的 IT 部門也可以設定企業私用存放區，其中只包含公司的應用程式，以符合您的特定 HoloLens 使用量。</span><span class="sxs-lookup"><span data-stu-id="7a42e-158">Your IT department can also set up an enterprise private store, containing only your company’s apps for your specific HoloLens usage.</span></span> <span data-ttu-id="7a42e-159">安全地將企業軟體散發給選定的企業使用者群組。</span><span class="sxs-lookup"><span data-stu-id="7a42e-159">Securely distribute your enterprise software to selected group of enterprise users.</span></span>

### <a name="development-edition-vs-commercial-suite"></a><span data-ttu-id="7a42e-160">開發版與商用套件</span><span class="sxs-lookup"><span data-stu-id="7a42e-160">Development Edition vs. Commercial Suite</span></span>

<table>
<tr>
<th><span data-ttu-id="7a42e-161">特性</span><span class="sxs-lookup"><span data-stu-id="7a42e-161">Features</span></span></th><th><span data-ttu-id="7a42e-162">Development 版</span><span class="sxs-lookup"><span data-stu-id="7a42e-162">Development Edition</span></span></th><th><span data-ttu-id="7a42e-163">商業套件</span><span class="sxs-lookup"><span data-stu-id="7a42e-163">Commercial Suite</span></span></th>
</tr><tr>
<td><span data-ttu-id="7a42e-164">裝置加密 (Bitlocker) </span><span class="sxs-lookup"><span data-stu-id="7a42e-164">Device Encryption (Bitlocker)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="7a42e-165">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-165">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-166">虛擬私人網路 (VPN)</span><span class="sxs-lookup"><span data-stu-id="7a42e-166">Virtual Private Network (VPN)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="7a42e-167">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-167">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-168"><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Kiosk 模式</a></span><span class="sxs-lookup"><span data-stu-id="7a42e-168"><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Kiosk mode</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="7a42e-169">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-169">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="7a42e-170">管理和部署</span><span class="sxs-lookup"><span data-stu-id="7a42e-170">Management and deployment</span></span></th>
</tr><tr>
<td><span data-ttu-id="7a42e-171">行動裝置管理 (MDM)</span><span class="sxs-lookup"><span data-stu-id="7a42e-171">Mobile Device Management (MDM)</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="7a42e-172">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-172">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-173">封鎖取消註冊的功能</span><span class="sxs-lookup"><span data-stu-id="7a42e-173">Ability to block unenrollment</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="7a42e-174">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-174">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-175">以憑證為基礎的公司 Wi-Fi 存取</span><span class="sxs-lookup"><span data-stu-id="7a42e-175">Cert Based Corporate Wi-Fi Access</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="7a42e-176">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-176">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-177">Microsoft Store (取用者) </span><span class="sxs-lookup"><span data-stu-id="7a42e-177">Microsoft Store (Consumer)</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-178">消費者</span><span class="sxs-lookup"><span data-stu-id="7a42e-178">Consumer</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-179">透過 MDM 篩選</span><span class="sxs-lookup"><span data-stu-id="7a42e-179">Filtering via MDM</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-180"><a href="/microsoft-store/working-with-line-of-business-apps">Business Store 入口網站</a></span><span class="sxs-lookup"><span data-stu-id="7a42e-180"><a href="/microsoft-store/working-with-line-of-business-apps">Business Store Portal</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="7a42e-181">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-181">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="7a42e-182">安全性及身分識別</span><span class="sxs-lookup"><span data-stu-id="7a42e-182">Security and Identity</span></span></th>
</tr><tr>
<td><span data-ttu-id="7a42e-183">使用 Azure Active Directory (AAD) 登入</span><span class="sxs-lookup"><span data-stu-id="7a42e-183">Log in with Azure Active Directory (AAD)</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-184">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-184">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-185">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-185">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-186">使用 Microsoft 帳戶登入 (MSA) </span><span class="sxs-lookup"><span data-stu-id="7a42e-186">Log in with Microsoft Account (MSA)</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-187">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-187">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-188">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-188">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-189">使用 PIN 解除鎖定的新一代認證</span><span class="sxs-lookup"><span data-stu-id="7a42e-189">Next Generation Credentials with PIN unlock</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-190">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-190">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-191">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-191">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-192"><a href="/windows-hardware/design/device-experiences/oem-secure-boot">安全開機</a></span><span class="sxs-lookup"><span data-stu-id="7a42e-192"><a href="/windows-hardware/design/device-experiences/oem-secure-boot">Secure boot</a></span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-193">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-193">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-194">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-194">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="7a42e-195">服務與支援</span><span class="sxs-lookup"><span data-stu-id="7a42e-195">Servicing and Support</span></span></th>
</tr><tr>
<td><span data-ttu-id="7a42e-196">系統自動更新到達時</span><span class="sxs-lookup"><span data-stu-id="7a42e-196">Automatic system updates as they arrive</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-197">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-197">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="7a42e-198">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-198">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-199"><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></span><span class="sxs-lookup"><span data-stu-id="7a42e-199"><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="7a42e-200">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-200">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="7a42e-201">長期維護分支</span><span class="sxs-lookup"><span data-stu-id="7a42e-201">Long-term servicing branch</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="7a42e-202">✔️</span><span class="sxs-lookup"><span data-stu-id="7a42e-202">✔️</span></span></td>
</tr>
</table>

## <a name="prior-release-notes"></a><span data-ttu-id="7a42e-203">先前的版本資訊</span><span class="sxs-lookup"><span data-stu-id="7a42e-203">Prior release notes</span></span>
* [<span data-ttu-id="7a42e-204">版本資訊 - 2016 年 5 月</span><span class="sxs-lookup"><span data-stu-id="7a42e-204">Release notes - May 2016</span></span>](release-notes-may-2016.md)
* [<span data-ttu-id="7a42e-205">版本資訊 - 2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="7a42e-205">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="7a42e-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a42e-206">See also</span></span>
* [<span data-ttu-id="7a42e-207">HoloLens 的已知問題</span><span class="sxs-lookup"><span data-stu-id="7a42e-207">HoloLens known issues</span></span>](/windows/mixed-reality/hololens-known-issues)
* [<span data-ttu-id="7a42e-208">商業功能</span><span class="sxs-lookup"><span data-stu-id="7a42e-208">Commercial features</span></span>](/windows/mixed-reality/commercial-features)
* [<span data-ttu-id="7a42e-209">安裝工具</span><span class="sxs-lookup"><span data-stu-id="7a42e-209">Install the tools</span></span>](/windows/mixed-reality/develop/install-the-tools)
* [<span data-ttu-id="7a42e-210">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="7a42e-210">Using the HoloLens emulator</span></span>](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)