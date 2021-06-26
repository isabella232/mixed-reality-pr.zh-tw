---
title: 使用 Windows 裝置入口網站
description: 了解如何使用 Windows 裝置入口網站從遠端透過 Wi-Fi 或 USB 來設定及管理您的裝置。
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Windows 裝置入口網站, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d772175683208ac0e3ed4b3163ca561da416c1cf
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112919809"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="fffba-104">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="fffba-104">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="fffba-105">功能</span><span class="sxs-lookup"><span data-stu-id="fffba-105">Feature</span></span></th><th style="width:150px"><span data-ttu-id="fffba-106"><a href="/hololens/hololens1-hardware">HoloLens (第 1 代)</a></span><span class="sxs-lookup"><span data-stu-id="fffba-106"><a href="/hololens/hololens1-hardware">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="fffba-107">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fffba-107">HoloLens 2</span></span></th><th style="width:150px">
</tr><tr>
<td> <span data-ttu-id="fffba-108">Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="fffba-108">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="fffba-109">✔️</span><span class="sxs-lookup"><span data-stu-id="fffba-109">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="fffba-110">✔️</span><span class="sxs-lookup"><span data-stu-id="fffba-110">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="fffba-111">HoloLens 的 Windows 裝置入口網站能讓您從遠端透 Wi-Fi 或 USB 來設定及管理您的裝置。</span><span class="sxs-lookup"><span data-stu-id="fffba-111">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="fffba-112">Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。</span><span class="sxs-lookup"><span data-stu-id="fffba-112">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="fffba-113">裝置入口網站包含許多工具，可協助您管理 HoloLens，並對應用程式進行偵錯及最佳化。</span><span class="sxs-lookup"><span data-stu-id="fffba-113">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="fffba-114">本文件特別說明適用於 HoloLens 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="fffba-114">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="fffba-115">若要使用適用於傳統型 Windows 裝置入口網站 (包括 Windows Mixed Reality)，請參閱 [Windows 裝置入口網站概觀](/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="fffba-115">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="fffba-116">設定 HoloLens 以使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="fffba-116">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="fffba-117">開啟您的 HoloLens 並將裝置戴上。</span><span class="sxs-lookup"><span data-stu-id="fffba-117">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="fffba-118">使用 HoloLens2 的[開始手勢](/hololens/hololens2-basic-usage#start-gesture)或 HoloLens (第 1 代) 的[綻開](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)，以啟動主功能表。</span><span class="sxs-lookup"><span data-stu-id="fffba-118">Use the [Start gesture](/hololens/hololens2-basic-usage#start-gesture) for HoloLens2 or [Bloom](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (1st Gen) to launch the main menu.</span></span> 
3. <span data-ttu-id="fffba-119">注視 [設定] 圖格，並在 HoloLens (第一代) 上進行[空中點選](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)手勢。</span><span class="sxs-lookup"><span data-stu-id="fffba-119">Gaze at the **Settings** tile and do an [air-tap](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) gesture on HoloLens (1st Gen).</span></span> <span data-ttu-id="fffba-120">[加以觸控或使用手部射線](/hololens/hololens2-basic-usage)，也可以在 HoloLens 2 上進行選取。</span><span class="sxs-lookup"><span data-stu-id="fffba-120">You can also select it on HoloLens 2 by [touching it or using a Hand ray](/hololens/hololens2-basic-usage).</span></span> 
4. <span data-ttu-id="fffba-121">選取 [更新] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="fffba-121">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="fffba-122">選取 [適用於開發人員]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="fffba-122">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="fffba-123">啟用 [開發人員模式]。</span><span class="sxs-lookup"><span data-stu-id="fffba-123">Enable **Developer Mode**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fffba-124">如果目前處於多重使用者模式，且您不是系統管理員，進入開發人員模式的功能可能會呈現為灰色。請確定您是 **[裝置的系統管理員](/hololens/security-adminless-os)** 。</span><span class="sxs-lookup"><span data-stu-id="fffba-124">If you're in multi-user and not an admin, the ability to enter Developer Mode may be grayed out. Please ensure that you are an **[admin on the device](/hololens/security-adminless-os)**.</span></span>

7. <span data-ttu-id="fffba-125">[向下捲動](../../design/gaze-and-commit.md#composite-gestures)並啟用 **裝置入口網站**。</span><span class="sxs-lookup"><span data-stu-id="fffba-125">[Scroll down](../../design/gaze-and-commit.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="fffba-126">如果您要設定 Windows 裝置入口網站，以便透過 USB 或 Wi-Fi 將應用程式部署到此 HoloLens，請選取 [配對] 以[產生配對 PIN](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="fffba-126">If you're setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, select **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="fffba-127">將 [設定] 應用程式保留在 [PIN] 快顯視窗中，直到您在第一次部署期間，將 PIN 輸入 Visual Studio 為止。</span><span class="sxs-lookup"><span data-stu-id="fffba-127">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

![在 Windows 全像攝影版的 [設定] 應用程式中啟用開發人員模式](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="fffba-129">透過 Wi-Fi 連線</span><span class="sxs-lookup"><span data-stu-id="fffba-129">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="fffba-130">[將您的 HoloLens 連線到 Wi-Fi](/hololens/hololens-network)。</span><span class="sxs-lookup"><span data-stu-id="fffba-130">[Connect your HoloLens to Wi-Fi](/hololens/hololens-network).</span></span>
2. <span data-ttu-id="fffba-131">尋找裝置的 IP 位址，可行方式如下：</span><span class="sxs-lookup"><span data-stu-id="fffba-131">Look up your device's IP address by either:</span></span>
  * <span data-ttu-id="fffba-132">移至 [設定] > [網路和網際網路] > [Wi-Fi] > [進階選項]。</span><span class="sxs-lookup"><span data-stu-id="fffba-132">Going to **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
  * <span data-ttu-id="fffba-133">移至 [設定] > [網路和網際網路]，然後選取 [硬體屬性]。</span><span class="sxs-lookup"><span data-stu-id="fffba-133">Going to **Settings > Network & Internet** and selecting **Hardware properties**.</span></span>
  * <span data-ttu-id="fffba-134">使用「我的 IP 位址是什麼？」</span><span class="sxs-lookup"><span data-stu-id="fffba-134">Using the "What's my IP address?"</span></span> <span data-ttu-id="fffba-135">語音命令。</span><span class="sxs-lookup"><span data-stu-id="fffba-135">voice command.</span></span>

![HoloLens 2 設定](images/using-windows-portal-img-02.jpg)

3. <span data-ttu-id="fffba-137">從您電腦上的網頁瀏覽器，移至 https://<YOUR_HOLOLENS_IP_ADDRESS></span><span class="sxs-lookup"><span data-stu-id="fffba-137">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="fffba-138">瀏覽器將會顯示下列訊息：「此網站的安全性憑證有問題」，因為發給裝置入口網站的憑證是測試憑證。</span><span class="sxs-lookup"><span data-stu-id="fffba-138">The browser will display the following message: "There's a problem with this website's security certificate" because the certificate, which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="fffba-139">您可以暫時略過這個憑證錯誤並繼續。</span><span class="sxs-lookup"><span data-stu-id="fffba-139">You can ignore this certificate error for now and continue.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="fffba-140">透過 USB 連線</span><span class="sxs-lookup"><span data-stu-id="fffba-140">Connecting over USB</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fffba-141">基於新的瀏覽器標準，不再建議使用 IpOverUsb，因為它需要使用埠10080。</span><span class="sxs-lookup"><span data-stu-id="fffba-141">IpOverUsb is no longer recommended per new browser standards as it requires the use of port 10080.</span></span> <span data-ttu-id="fffba-142">如果您仍然想要使用 IpOverUsb，請在 Visual Studio 安裝期間檢查 [USB 裝置連線能力] 方塊（預設不會核取）。</span><span class="sxs-lookup"><span data-stu-id="fffba-142">If you still wish to use IpOverUsb, check the 'USB Device Connectivity' box during Visual Studio installation, which isn't checked by default.</span></span> <span data-ttu-id="fffba-143">相反地，我們建議使用 UsbNcm 連接，HoloLens 2 上預設支援此功能。</span><span class="sxs-lookup"><span data-stu-id="fffba-143">Instead, we recommend connecting with UsbNcm, which is supported by default on HoloLens 2.</span></span> <span data-ttu-id="fffba-144">如果您使用 HoloLens 1，建議您使用 WiFi 連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="fffba-144">If you are using a HoloLens 1, we recommend connecting to your PC using WiFi.</span></span>

1. <span data-ttu-id="fffba-145">如果您的 HoloLens 2 正在執行 Windows 全像21H1 版或更高版本，請移至 [設定] 應用程式中的 [適用于開發人員]，並確定已開啟 [裝置探索]。</span><span class="sxs-lookup"><span data-stu-id="fffba-145">If your HoloLens 2 is running Windows Holographic version 21H1 or higher, go to 'For developers' in the Settings app and make sure that 'Device discovery' is toggled ON.</span></span> 
2. <span data-ttu-id="fffba-146">使用 USB 纜線將您的 HoloLens 2 連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="fffba-146">Connect your HoloLens 2 to your PC with a USB-C cable.</span></span>
3. <span data-ttu-id="fffba-147">尋找您的 UsbNcm IP。</span><span class="sxs-lookup"><span data-stu-id="fffba-147">Find your UsbNcm IP.</span></span> <span data-ttu-id="fffba-148">有幾種方式可以執行此作業：</span><span class="sxs-lookup"><span data-stu-id="fffba-148">There are a few ways to do this:</span></span>
  * <span data-ttu-id="fffba-149">在裝置上的 [設定] 應用程式中 (此方法僅適用于執行 Windows 全像21H1 或更高版本的 HoloLenses，並開啟 [裝置探索]。 ) </span><span class="sxs-lookup"><span data-stu-id="fffba-149">In the Settings app on the device (This method only works for HoloLenses running Windows Holographic version 21H1 or higher, with 'Device discovery' toggled ON.)</span></span>
    1. <span data-ttu-id="fffba-150">移至裝置上的 [設定] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fffba-150">Go into the Settings app on the device.</span></span>
    2. <span data-ttu-id="fffba-151">移至開發人員的「更新 & 安全性」 >」。</span><span class="sxs-lookup"><span data-stu-id="fffba-151">Go to "Update & Security" > "For developers."</span></span> <span data-ttu-id="fffba-152">這是您裝置入口網站啟用的相同位置。</span><span class="sxs-lookup"><span data-stu-id="fffba-152">This is the same place you enabled Device Portal.</span></span>
    3. <span data-ttu-id="fffba-153">在頁面底部複製您的 **乙太** 網路 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="fffba-153">At the bottom of the page, copy your **Ethernet** IP address.</span></span> <span data-ttu-id="fffba-154">這是您的 UsbNcm IP。</span><span class="sxs-lookup"><span data-stu-id="fffba-154">This is your UsbNcm IP.</span></span> 
    <span data-ttu-id="fffba-155">![HoloLens 2 設定-UsbNcm IP](images/deviceportal_usbncm_ipaddress.jpg)</span><span class="sxs-lookup"><span data-stu-id="fffba-155">![HoloLens 2 settings - UsbNcm IP](images/deviceportal_usbncm_ipaddress.jpg)</span></span>

  * <span data-ttu-id="fffba-156">在裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="fffba-156">In Device Portal</span></span> 
    1. <span data-ttu-id="fffba-157">在您的裝置上，使用 HoloLens 的 WiFi 位址開啟裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="fffba-157">On your device, open Device Portal using your HoloLens' WiFi address.</span></span> <span data-ttu-id="fffba-158">如果您不知道 HoloLens 的 WiFi 位址，可以使用語音命令「我的 IP 位址為何？」</span><span class="sxs-lookup"><span data-stu-id="fffba-158">If you don't know your HoloLens' WiFi address, you can use the voice command "What's my IP address?"</span></span>
    2. <span data-ttu-id="fffba-159">移至系統 > 網路</span><span class="sxs-lookup"><span data-stu-id="fffba-159">Go to System > Networking</span></span>
    3. <span data-ttu-id="fffba-160">在 [IP 設定] 面板中頁面的最右側，找出開頭為 "Description： UsbNcm Function" 的區段。</span><span class="sxs-lookup"><span data-stu-id="fffba-160">On the far right side of the page in the "IP Configuration" panel, locate the section that starts with "Description: UsbNcm Function."</span></span>
    4. <span data-ttu-id="fffba-161">您的 UsbNcm IP 是 [IPv4 位址] 行。</span><span class="sxs-lookup"><span data-stu-id="fffba-161">Your UsbNcm IP is the "IPv4 address" line.</span></span> <span data-ttu-id="fffba-162">您可以複製位址或直接按一下位址-它是超連結，會使用 UsbNcm IP 重新開啟裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="fffba-162">You can copy the address or just click on the address - it is a hyperlink which will reopen Device Portal using the UsbNcm IP.</span></span>
  
  * <span data-ttu-id="fffba-163">在命令提示字元中</span><span class="sxs-lookup"><span data-stu-id="fffba-163">In a command prompt</span></span>
    1. <span data-ttu-id="fffba-164">在任何命令提示字元中，流覽至 \<SDK version> 安裝 WINDOWS 10 SDK 的 bin \x86 資料夾，例如 C:\Program Files (x86) \Windows Kits\10\bin\10.0.19041.0\x86。</span><span class="sxs-lookup"><span data-stu-id="fffba-164">In any command prompt, navigate to the bin\<SDK version>\x86 folder where your Windows 10 SDK is installed, such as C:\Program Files (x86)\Windows Kits\10\bin\10.0.19041.0\x86.</span></span>
    2. <span data-ttu-id="fffba-165">輸入 "winappdeploycmd.exe devices"，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="fffba-165">Type "winappdeploycmd devices" and press Enter.</span></span>
    3. <span data-ttu-id="fffba-166">在輸出中，尋找模型/名稱資料行是 HoloLens 裝置名稱的專案，例如 HOLOLENS-xxxxxx。</span><span class="sxs-lookup"><span data-stu-id="fffba-166">In the output, look for the entry where the Model/Name column is your HoloLens device name, such as HOLOLENS-xxxxxx.</span></span> <span data-ttu-id="fffba-167">UsbNcm IP 位於這一行的開頭，且將會是 169.254.. x.x. 格式的自動私人 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="fffba-167">The UsbNcm IP is at the start of this line and will be an Automatic Private IP address in the form of 169.254.x.x.</span></span> <span data-ttu-id="fffba-168">複製此位址。</span><span class="sxs-lookup"><span data-stu-id="fffba-168">Copy this address.</span></span> 
 
4. <span data-ttu-id="fffba-169">如果您複製了 UsbNcm IP，請從您電腦上的網頁瀏覽器移至 HTTPs://，然後再移至您的 UsbNcm IP。</span><span class="sxs-lookup"><span data-stu-id="fffba-169">If you copied your UsbNcm IP, from a web browser on your PC go to https:// followed by your UsbNcm IP.</span></span>

### <a name="moving-files-over-usb"></a><span data-ttu-id="fffba-170">透過 USB 移動檔案</span><span class="sxs-lookup"><span data-stu-id="fffba-170">Moving files over USB</span></span>

<span data-ttu-id="fffba-171">您可以直接將檔案從電腦移至 HoloLens，而無須進行任何額外的設定。</span><span class="sxs-lookup"><span data-stu-id="fffba-171">You can move files from your PC to your HoloLens without any additional setup.</span></span>
1. <span data-ttu-id="fffba-172">使用 USB 線將您的電腦連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="fffba-172">Connect your PC to your HoloLens with a USB cord</span></span>
2. <span data-ttu-id="fffba-173">將檔案拖曳到桌面上的 **PC\\[Your_HoloLens_Device_Name]\Internal Storage** 中</span><span class="sxs-lookup"><span data-stu-id="fffba-173">Drag your files into **PC\\[Your_HoloLens_Device_Name]\Internal Storage** on your desktop</span></span>
3. <span data-ttu-id="fffba-174">開啟 [開始] 功能表，然後在 HoloLens上選取 [所有應用程式] > [檔案總管]</span><span class="sxs-lookup"><span data-stu-id="fffba-174">Open the **Start Menu** and select **All apps > File Explorer** on your HoloLens</span></span>

> [!NOTE]
> <span data-ttu-id="fffba-175">您可能需要選取面板左側的 [此裝置]，從 [最近使用] 瀏覽至他處以找出您的檔案。</span><span class="sxs-lookup"><span data-stu-id="fffba-175">You may need to select **This device** on the left side of the panel to navigate away from "Recently used" to locate your files.</span></span> 

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="fffba-176">連線到模擬器</span><span class="sxs-lookup"><span data-stu-id="fffba-176">Connecting to an emulator</span></span>

<span data-ttu-id="fffba-177">您也可以透過模擬器使用 Device Portal。</span><span class="sxs-lookup"><span data-stu-id="fffba-177">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="fffba-178">若要連線到裝置入口網站，請使用[工具列](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="fffba-178">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="fffba-179">選取此圖示：![開啟裝置入口網站圖示](images/emulator-deviceportal.png) **開啟裝置入口網站**：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="fffba-179">Select this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="fffba-180">建立使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="fffba-180">Creating a Username and Password</span></span>

<span data-ttu-id="fffba-181">![設定 Windows 裝置入口網站的存取權](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-181">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="fffba-182">設定 Windows 裝置入口網站的存取權</span><span class="sxs-lookup"><span data-stu-id="fffba-182">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="fffba-183">首次在 HoloLens 上連線到 Device Portal 時，您必須建立使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="fffba-183">The first time you connect to the Device Portal on your HoloLens, you'll need to create a username and password.</span></span>
1. <span data-ttu-id="fffba-184">在您電腦上的網頁瀏覽器中，輸入 HoloLens 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="fffba-184">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="fffba-185">[設定存取] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="fffba-185">The Setup access page opens.</span></span>
2. <span data-ttu-id="fffba-186">選取或點選 [要求 PIN]，並查看 HoloLens 顯示畫面以取得產生的 PIN。</span><span class="sxs-lookup"><span data-stu-id="fffba-186">Select or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="fffba-187">輸入 [您裝置上顯示的 PIN] 文字方塊中的 PIN。</span><span class="sxs-lookup"><span data-stu-id="fffba-187">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="fffba-188">輸入您會用來連線到 Device Portal 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="fffba-188">Enter the user name you'll use to connect to the Device Portal.</span></span> <span data-ttu-id="fffba-189">它並不需要是 Microsoft 帳戶 (MSA) 或網域名稱。</span><span class="sxs-lookup"><span data-stu-id="fffba-189">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="fffba-190">輸入密碼並確認它。</span><span class="sxs-lookup"><span data-stu-id="fffba-190">Enter a password and confirm it.</span></span> <span data-ttu-id="fffba-191">密碼長度必須至少為七個字元。</span><span class="sxs-lookup"><span data-stu-id="fffba-191">The password must be at least seven characters in length.</span></span> <span data-ttu-id="fffba-192">它並不需要是 MSA 或網域密碼。</span><span class="sxs-lookup"><span data-stu-id="fffba-192">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="fffba-193">按一下 [配對]，在 HoloLens 上連線到 Windows 裝置入口網站。</span><span class="sxs-lookup"><span data-stu-id="fffba-193">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="fffba-194">如果您想在任何時候變更此使用者名稱或密碼，可以造訪裝置安全性頁面來重複此程序，方法是瀏覽到： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm。</span><span class="sxs-lookup"><span data-stu-id="fffba-194">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="fffba-195">安全性憑證</span><span class="sxs-lookup"><span data-stu-id="fffba-195">Security certificate</span></span>

<span data-ttu-id="fffba-196">如果您在瀏覽器中看見「憑證錯誤」，可透過與裝置建立信任關係來加以修正。</span><span class="sxs-lookup"><span data-stu-id="fffba-196">If you see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="fffba-197">每個 HoloLens 都會為其 SSL 連線產生自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="fffba-197">Each HoloLens generates a self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="fffba-198">根據預設，此憑證並不會受到您電腦的網頁瀏覽器信任，因此您可能會收到「憑證錯誤」。</span><span class="sxs-lookup"><span data-stu-id="fffba-198">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="fffba-199">透過 USB 或您信任的 Wi-Fi 網路，從您的 HoloLens 下載此憑證，並在電腦上信任該憑證，您便可安全地連線到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="fffba-199">You can securely connect to your device by downloading this certificate from your HoloLens over USB or a Wi-Fi network you trust and trusting it on your PC.</span></span>
1. <span data-ttu-id="fffba-200">**請確保您是在安全的網路上 (USB 或您信任的 Wi-Fi 網路)。**</span><span class="sxs-lookup"><span data-stu-id="fffba-200">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="fffba-201">從裝置入口網站上的 [安全性] 頁面下載此裝置的憑證。</span><span class="sxs-lookup"><span data-stu-id="fffba-201">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="fffba-202">瀏覽到： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="fffba-202">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
   * <span data-ttu-id="fffba-203">開啟 [系統] > [喜好設定] 的節點。</span><span class="sxs-lookup"><span data-stu-id="fffba-203">Open the node for System > Preferences.</span></span> 
   * <span data-ttu-id="fffba-204">向下捲動至 [裝置安全性]，選取 [下載此裝置的憑證] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fffba-204">Scroll down to Device Security, select the "Download this device's certificate" button.</span></span>
3. <span data-ttu-id="fffba-205">安裝您電腦上「信任的根憑證授權」存放區中的憑證。</span><span class="sxs-lookup"><span data-stu-id="fffba-205">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="fffba-206">從 [Windows] 功能表中，輸入：管理電腦憑證並啟動 applet。</span><span class="sxs-lookup"><span data-stu-id="fffba-206">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="fffba-207">展開 [信任的根憑證授權] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fffba-207">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="fffba-208">選取 [憑證] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fffba-208">Select the **Certificates** folder.</span></span>
   * <span data-ttu-id="fffba-209">從 [動作] 功能表中，選取：[所有工作] > [匯入]...</span><span class="sxs-lookup"><span data-stu-id="fffba-209">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="fffba-210">使用您從 Device Portal 下載的憑證檔案完成憑證匯入精靈。</span><span class="sxs-lookup"><span data-stu-id="fffba-210">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="fffba-211">重新啟動瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="fffba-211">Restart the browser.</span></span>

>[!NOTE]
> <span data-ttu-id="fffba-212">僅在裝置刷新時，才會信任此裝置的憑證，且使用者才必須再次執行此程序。</span><span class="sxs-lookup"><span data-stu-id="fffba-212">This certificate will only be trusted for the device and the user will have to go through the process again if the device is flashed.</span></span>

## <a name="sideloading-applications"></a><span data-ttu-id="fffba-213">側載應用程式</span><span class="sxs-lookup"><span data-stu-id="fffba-213">Sideloading applications</span></span>

### <a name="installing-a-certificate"></a><span data-ttu-id="fffba-214">安裝憑證</span><span class="sxs-lookup"><span data-stu-id="fffba-214">Installing a certificate</span></span>

1. <span data-ttu-id="fffba-215">在 Windows 裝置入口網站中，瀏覽至 [應用程式管理員] 頁面</span><span class="sxs-lookup"><span data-stu-id="fffba-215">In Windows Device Portal, navigate to the **Apps** manager page</span></span>
2. <span data-ttu-id="fffba-216">在 [部署應用程式] 區段中，選取 [安裝憑證]</span><span class="sxs-lookup"><span data-stu-id="fffba-216">In the Deploy apps section, select **Install Certificate**</span></span>
3. <span data-ttu-id="fffba-217">在 [選取用於簽署應用程式套件的憑證檔案 (.cer)] 下，選取 [選擇檔案]，並瀏覽至與您要側載的應用程式套件相關聯的憑證</span><span class="sxs-lookup"><span data-stu-id="fffba-217">Under Select certificate file (.cer) used to sign an app package, select Choose File and browse to the certificate associated with the app package that you want to sideload</span></span>
4. <span data-ttu-id="fffba-218">選取 [安裝] 可開始進行安裝</span><span class="sxs-lookup"><span data-stu-id="fffba-218">Select **Install** to start the installation</span></span>

![螢幕擷取畫面：在 Windows 裝置入口網站中開啟的 [應用程式管理員] 頁面](images/sideloading-1.png)

### <a name="installing-an-app"></a><span data-ttu-id="fffba-220">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="fffba-220">Installing an app</span></span>

> [!NOTE]
> <span data-ttu-id="fffba-221">為了讓應用程式能夠透過裝置入口網站成功完成安裝，其必須經過憑證的簽署，您必須先將此憑證安裝到裝置上，然後才能嘗試安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="fffba-221">In order for an app to install successfully via Device Portal it must be signed by a certificate, this certificate must be installed to the device prior to attempting to install the app.</span></span> <span data-ttu-id="fffba-222">如需相關指示，請參閱[上一節](#installing-a-certificate)。</span><span class="sxs-lookup"><span data-stu-id="fffba-222">See the [previous section](#installing-a-certificate) for instructions.</span></span>

1. <span data-ttu-id="fffba-223">當您[從 Visual Studio 建立了應用程式套件](using-visual-studio.md)後，就可以將套件從產生的檔案遠端安裝到您的裝置上：</span><span class="sxs-lookup"><span data-stu-id="fffba-223">When you've [created an app package from Visual Studio](using-visual-studio.md), you can remotely install it onto your device from the generated files:</span></span>

![螢幕擷取畫面：應用程式套件的檔案內容](images/sideloading-2.png)

2. <span data-ttu-id="fffba-225">在 Windows 裝置入口網站中，瀏覽至 [應用程式管理員] 頁面</span><span class="sxs-lookup"><span data-stu-id="fffba-225">In Windows Device Portal, navigate to the **Apps** manager page</span></span>
3. <span data-ttu-id="fffba-226">在 [部署應用程式] 區段中，選取 [本機存放區]</span><span class="sxs-lookup"><span data-stu-id="fffba-226">In the **Deploy** apps section, select **Local Storage**</span></span>
4. <span data-ttu-id="fffba-227">在 [選取應用程式套件] 下，選取 [選擇檔案]，並瀏覽至您要側載的應用程式套件</span><span class="sxs-lookup"><span data-stu-id="fffba-227">Under Select the application package, select Choose File and browse to the app package that you want to sideload</span></span>
5. <span data-ttu-id="fffba-228">如果您在安裝應用程式時，要一起安裝選用項目或架構套件，請勾選對應的方塊，然後選取 [下一步]：</span><span class="sxs-lookup"><span data-stu-id="fffba-228">Check the respective boxes if you want to install optional or framework packages along with the app installation and select **Next**:</span></span>

![螢幕擷取畫面：在 Windows 裝置入口網站中開啟的 [應用程式管理員] 頁面，其中已醒目提示 [本機儲存體] 索引標籤](images/sideloading-3.png)

6. <span data-ttu-id="fffba-230">選取 [安裝] 可開始進行安裝</span><span class="sxs-lookup"><span data-stu-id="fffba-230">Select **Install** to start the installation</span></span>
 
![螢幕擷取畫面：在 Windows 裝置入口網站中開啟的 [應用程式管理員] 頁面，且安裝已成功完成](images/sideloading-4.png) 

<span data-ttu-id="fffba-232">安裝完成後，回到 HoloLens 上的 [所有應用程式] 頁面，然後啟動新安裝的應用程式！</span><span class="sxs-lookup"><span data-stu-id="fffba-232">Once the installation is complete, go back to the **All apps** page on your HoloLens and launch your newly installed application!</span></span>

## <a name="device-portal-pages"></a><span data-ttu-id="fffba-233">Device Portal 頁面</span><span class="sxs-lookup"><span data-stu-id="fffba-233">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="fffba-234">首頁</span><span class="sxs-lookup"><span data-stu-id="fffba-234">Home</span></span>

<span data-ttu-id="fffba-235">![Microsoft HoloLens 上的 Windows 裝置入口網站首頁](images/using-windows-portal-img-04.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-235">![Windows Device Portal home page on Microsoft HoloLens](images/using-windows-portal-img-04.png)</span></span><br>
<span data-ttu-id="fffba-236">*Microsoft HoloLens 上的 Windows 裝置入口網站首頁*</span><span class="sxs-lookup"><span data-stu-id="fffba-236">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-237">您的 Device Portal 工作階段從首頁開始。</span><span class="sxs-lookup"><span data-stu-id="fffba-237">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="fffba-238">從首頁左側的瀏覽列中存取其他頁面。</span><span class="sxs-lookup"><span data-stu-id="fffba-238">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="fffba-239">頁面頂端的工具列能讓您存取常用狀態與功能。</span><span class="sxs-lookup"><span data-stu-id="fffba-239">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="fffba-240">**線上**：指出裝置是否已連線到 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="fffba-240">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="fffba-241">**關機**：關閉裝置。</span><span class="sxs-lookup"><span data-stu-id="fffba-241">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="fffba-242">**重新啟動**：關閉裝置電源並重新開啟。</span><span class="sxs-lookup"><span data-stu-id="fffba-242">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="fffba-243">**安全性**：開啟 [裝置安全性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="fffba-243">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="fffba-244">**冷卻**：指出裝置的溫度。</span><span class="sxs-lookup"><span data-stu-id="fffba-244">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="fffba-245">**A/C**：指出裝置是否已插上電源並且正在充電。</span><span class="sxs-lookup"><span data-stu-id="fffba-245">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="fffba-246">**說明**：開啟 REST 介面文件頁面。</span><span class="sxs-lookup"><span data-stu-id="fffba-246">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="fffba-247">首頁將顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="fffba-247">The home page shows the following info:</span></span>
* <span data-ttu-id="fffba-248">**裝置狀態：** 監視裝置的健康狀況並報告嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="fffba-248">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="fffba-249">**Windows 資訊：** 顯示 HoloLens 的名稱，以及目前安裝的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="fffba-249">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="fffba-250">[喜好設定] 區段包含下列設定：</span><span class="sxs-lookup"><span data-stu-id="fffba-250">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="fffba-251">**IPD**：設定瞳孔間距 (IPD) - 這是使用者雙眼注視前方時，兩個瞳孔中心點之間的距離 (以公釐為單位)。</span><span class="sxs-lookup"><span data-stu-id="fffba-251">**IPD**: Sets the interpupillary distance (IPD) - the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="fffba-252">此設定會立即生效。</span><span class="sxs-lookup"><span data-stu-id="fffba-252">The setting takes effect immediately.</span></span> <span data-ttu-id="fffba-253">預設值會在您設定裝置時自動計算。</span><span class="sxs-lookup"><span data-stu-id="fffba-253">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="fffba-254">**裝置名稱**：為 HoloLens 指派名稱。</span><span class="sxs-lookup"><span data-stu-id="fffba-254">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="fffba-255">在變更此值之後，重新啟動裝置才能生效。</span><span class="sxs-lookup"><span data-stu-id="fffba-255">eboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="fffba-256">按一下 [儲存] 之後，將會有對話方塊詢問您是否要立即重新啟動裝置，或稍後再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="fffba-256">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="fffba-257">**睡眠設定**：設定裝置在接上電源及使用電池的情況下，在進入睡眠之前所需等待的時間長度。</span><span class="sxs-lookup"><span data-stu-id="fffba-257">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="fffba-258">3D 檢視</span><span class="sxs-lookup"><span data-stu-id="fffba-258">3D View</span></span>

<span data-ttu-id="fffba-259">![Microsoft HoloLens 上 Windows 裝置入口網站的 3D 檢視頁面](images/using-windows-portal-img-05.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-259">![3D View page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-05.png)</span></span><br>
<span data-ttu-id="fffba-260">*Microsoft HoloLens 上 Windows 裝置入口網站的 3D 檢視頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-260">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-261">使用 [3D 檢視] 頁面來查看 HoloLens 解譯您周遭環境的方式。</span><span class="sxs-lookup"><span data-stu-id="fffba-261">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="fffba-262">使用滑鼠來瀏覽檢視：</span><span class="sxs-lookup"><span data-stu-id="fffba-262">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="fffba-263">旋轉：按下滑鼠左鍵 + 移動滑鼠；</span><span class="sxs-lookup"><span data-stu-id="fffba-263">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="fffba-264">平移：按下滑鼠右鍵 + 移動滑鼠；</span><span class="sxs-lookup"><span data-stu-id="fffba-264">Pan: right click + mouse;</span></span>
* <span data-ttu-id="fffba-265">縮放：滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="fffba-265">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="fffba-266">**追蹤選項**</span><span class="sxs-lookup"><span data-stu-id="fffba-266">**Tracking options**</span></span>
   * <span data-ttu-id="fffba-267">選取 [強制視覺追蹤] 來開啟持續性視覺追蹤。</span><span class="sxs-lookup"><span data-stu-id="fffba-267">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="fffba-268">**暫停** 將會停止視覺追蹤。</span><span class="sxs-lookup"><span data-stu-id="fffba-268">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="fffba-269">**檢視選項**：設定 3D 視圖上的選項：</span><span class="sxs-lookup"><span data-stu-id="fffba-269">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="fffba-270">**追蹤**：指出視覺追蹤是否為作用中。</span><span class="sxs-lookup"><span data-stu-id="fffba-270">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="fffba-271">**顯示樓面**：顯示棋盤式的樓面規劃。</span><span class="sxs-lookup"><span data-stu-id="fffba-271">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="fffba-272">**顯示範圍**：顯示檢視範圍。</span><span class="sxs-lookup"><span data-stu-id="fffba-272">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="fffba-273">**顯示穩定平面**：顯示 HoloLens 用來穩定動作的平面。</span><span class="sxs-lookup"><span data-stu-id="fffba-273">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="fffba-274">**顯示網格**：顯示代表您周遭環境的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="fffba-274">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="fffba-275">**顯示空間錨點**：顯示作用中應用程式的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="fffba-275">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="fffba-276">選取 [更新] 按鈕，才能取得並重新整理錨點。</span><span class="sxs-lookup"><span data-stu-id="fffba-276">Select the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="fffba-277">**顯示詳細資料**：隨著下列數據變更，即時顯示雙手位置、頭部旋轉四元數，以及裝置原點向量。</span><span class="sxs-lookup"><span data-stu-id="fffba-277">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="fffba-278">**全螢幕按鈕**：以全螢幕模式顯示 3D 檢視。</span><span class="sxs-lookup"><span data-stu-id="fffba-278">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="fffba-279">按下 ESC 以離開全螢幕檢視。</span><span class="sxs-lookup"><span data-stu-id="fffba-279">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="fffba-280">**表面重建**：選取或點選 [更新] 以顯示裝置中最新的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="fffba-280">**Surface reconstruction**: Select or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="fffba-281">可能需要花費一些時間 (最多幾秒鐘) 才能完成完整作業。</span><span class="sxs-lookup"><span data-stu-id="fffba-281">A full pass may take some time to complete (up to a few seconds).</span></span> <span data-ttu-id="fffba-282">網格並不會在 3D 檢視中自動更新，您必須手動選取 [更新] 以取得來自裝置的最新網格。</span><span class="sxs-lookup"><span data-stu-id="fffba-282">The mesh doesn't update automatically in the 3D view, and you must manually select **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="fffba-283">選取 [儲存] 以將目前的空間對應網格在您的電腦上儲存為 obj 檔案。</span><span class="sxs-lookup"><span data-stu-id="fffba-283">Select **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="fffba-284">**空間錨點**：選取 [更新] 以顯示或更新作用中應用程式的空間錨點。</span><span class="sxs-lookup"><span data-stu-id="fffba-284">**Spatial anchors**: Select Update to display or update the spatial anchors for the active app.</span></span>

### <a name="map-manager"></a><span data-ttu-id="fffba-285">地圖管理員</span><span class="sxs-lookup"><span data-stu-id="fffba-285">Map Manager</span></span>

<span data-ttu-id="fffba-286">地圖管理員可讓您跨裝置共用地圖，藉以設定實景娛樂客戶的共用體驗。</span><span class="sxs-lookup"><span data-stu-id="fffba-286">Map Manager allows you to share maps across devices, which can be used to set up shared experiences for Location-Based Entertainment customers.</span></span> <span data-ttu-id="fffba-287">此工具可讓您匯入及匯出系統地圖和錨點。</span><span class="sxs-lookup"><span data-stu-id="fffba-287">The tool allows you to import and export system maps and anchors.</span></span>  

<span data-ttu-id="fffba-288">若要存取地圖管理員，請登入裝置入口網站，然後選取 [混合實境] -> [地圖管理員]：</span><span class="sxs-lookup"><span data-stu-id="fffba-288">To access the Map Manager, log into the Device Portal and select **Mixed Reality -> Map Manager**:</span></span> 

<span data-ttu-id="fffba-289">![Windows 裝置入口網站中的地圖管理員頁面](images/using-windows-portal-img-06.png)
*Microsoft HoloLens 上的 Windows 裝置入口網站中的地圖管理員頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-289">![Map manager page in Windows Device Portal](images/using-windows-portal-img-06.png)
*Map Manager page in Windows Device Portal on Microsoft HoloLens*</span></span>

#### <a name="exporting-and-importing-maps"></a><span data-ttu-id="fffba-290">匯出和匯入地圖</span><span class="sxs-lookup"><span data-stu-id="fffba-290">Exporting and importing maps</span></span>

<span data-ttu-id="fffba-291">若要匯出地圖，請選取 [匯出系統地圖和錨點]。</span><span class="sxs-lookup"><span data-stu-id="fffba-291">To export maps, select **Export System Map & Anchors**.</span></span> <span data-ttu-id="fffba-292">這可能需要一些時間，請等候 30-60 秒，讓地圖完成匯出。</span><span class="sxs-lookup"><span data-stu-id="fffba-292">This could take a while so be prepared to wait for 30-60 seconds while the map is exported.</span></span> <span data-ttu-id="fffba-293">完成後，檔案就會下載到您的瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="fffba-293">Once it’s complete, the file will be downloaded in your browser.</span></span>  

<span data-ttu-id="fffba-294">若要匯入地圖和錨點，請分別選取 [上傳地圖檔案] 和 [上傳錨點檔案]，然後選取您已匯出的地圖或錨點檔案。</span><span class="sxs-lookup"><span data-stu-id="fffba-294">To import maps and anchors, select **Upload a map file** and **Upload an anchor file** respectively and select a map or anchor file that you've already exported.</span></span> <span data-ttu-id="fffba-295">上傳的地圖或錨點檔案可來自任何其他的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="fffba-295">The uploaded map or anchor file can come from any other HoloLens device.</span></span> 

> [!NOTE]
> <span data-ttu-id="fffba-296">在 HoloLens 上，您也可以匯入和匯出空間對應資料基底。</span><span class="sxs-lookup"><span data-stu-id="fffba-296">On HoloLens, it's also possible to import and export the spatial mapping data base.</span></span> <span data-ttu-id="fffba-297">不過，這並不適用於非 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="fffba-297">However, this doesn't work on non-HoloLens devices.</span></span>  


### <a name="mixed-reality-capture"></a><span data-ttu-id="fffba-298">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="fffba-298">Mixed Reality Capture</span></span>

<span data-ttu-id="fffba-299">![Microsoft HoloLens 上 Windows 裝置入口網站的混合實境擷取頁面](images/using-windows-portal-img-07.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-299">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-07.png)</span></span><br>
<span data-ttu-id="fffba-300">*Microsoft HoloLens 上 Windows 裝置入口網站的混合實境擷取頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-300">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-301">使用 [混合實境擷取] 頁面來儲存來自 HoloLens 的媒體串流。</span><span class="sxs-lookup"><span data-stu-id="fffba-301">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="fffba-302">**擷取設定**：藉由檢查下列設定來控制所擷取的媒體串流：</span><span class="sxs-lookup"><span data-stu-id="fffba-302">**Capture Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="fffba-303">**全像投影**：在影片串流中擷取全像投影內容。</span><span class="sxs-lookup"><span data-stu-id="fffba-303">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="fffba-304">全像投影是以單聲道進行轉譯，而非立體聲。</span><span class="sxs-lookup"><span data-stu-id="fffba-304">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="fffba-305">**PV 相機**：擷取來自相片/攝影機的影片串流。</span><span class="sxs-lookup"><span data-stu-id="fffba-305">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="fffba-306">**麥克風音訊**：擷取來自麥克風陣列的音訊。</span><span class="sxs-lookup"><span data-stu-id="fffba-306">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="fffba-307">**App 音訊**：擷取來自目前執行中 App 的音訊。</span><span class="sxs-lookup"><span data-stu-id="fffba-307">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="fffba-308">**從相機呈現**：如果 [受執行中應用程式支援](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (僅限 HoloLens 2)，則將要從相片/攝影機角度進行的擷取對齊。</span><span class="sxs-lookup"><span data-stu-id="fffba-308">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="fffba-309">**即時預覽品質**：選取即時預覽的螢幕解析度、畫面播放速率，以及串流速率。</span><span class="sxs-lookup"><span data-stu-id="fffba-309">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="fffba-310">**音訊設定** (僅限 HoloLens 2)：</span><span class="sxs-lookup"><span data-stu-id="fffba-310">**Audio Settings** (HoloLens 2 only):</span></span>
  * <span data-ttu-id="fffba-311">**音訊媒體類別**：選取要在處理麥克風時使用的類別。</span><span class="sxs-lookup"><span data-stu-id="fffba-311">**Audio Media Category**: Select the category is used when processing the microphone.</span></span> <span data-ttu-id="fffba-312">[預設值] 會包含部分環境，而 [通訊] 會套用背景噪音消除。</span><span class="sxs-lookup"><span data-stu-id="fffba-312">**Default**  will include some of the environment, while **Communications** applies background noise cancellation.</span></span>
  * <span data-ttu-id="fffba-313">**App 音訊增益**：套用至 App 音訊音量的增益。</span><span class="sxs-lookup"><span data-stu-id="fffba-313">**App Audio Gain**: The gain applied to app audio's volume.</span></span>
  * <span data-ttu-id="fffba-314">**麥克風音訊增益**：套用至麥克風音訊音量的增益。</span><span class="sxs-lookup"><span data-stu-id="fffba-314">**Mic Audio Gain**: The gain applied to mic audio's volume.</span></span>
* <span data-ttu-id="fffba-315">**相片和影片設定** (HoloLens 2，2004 版或更新版本)：</span><span class="sxs-lookup"><span data-stu-id="fffba-315">**Photo and Video Settings** (HoloLens 2, version 2004 or later):</span></span>
  * <span data-ttu-id="fffba-316">**擷取設定檔**：選取拍攝相片和影片時所使用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="fffba-316">**Capture Profile**: Select the profile used when taking photos and videos.</span></span> <span data-ttu-id="fffba-317">此設定檔會決定可用的解析度和畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="fffba-317">The profile determines which resolutions and frame-rates are available.</span></span>
  * <span data-ttu-id="fffba-318">**相片解析度**：相片將採用的解析度。</span><span class="sxs-lookup"><span data-stu-id="fffba-318">**Photo Resolution**: The resolution the photo will be taken with.</span></span>
  * <span data-ttu-id="fffba-319">**影片解析度和畫面播放速率**：影片將採用的解析度和畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="fffba-319">**Video Resolution and Frame-rate**: The resolution and frame-rate the video will be taken with.</span></span>
  * <span data-ttu-id="fffba-320">**影片防震緩衝區**：拍攝影片時使用的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="fffba-320">**Video Stabilization Buffer**: The buffer size used when taking a video.</span></span> <span data-ttu-id="fffba-321">值愈高，快速移動時的補償效果愈好。</span><span class="sxs-lookup"><span data-stu-id="fffba-321">The higher the value, the better it can compensate for quick movements.</span></span>
* <span data-ttu-id="fffba-322">選取或點選 [即時預覽] 按鈕以顯示擷取串流。</span><span class="sxs-lookup"><span data-stu-id="fffba-322">Select or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="fffba-323">**停止即時預覽** 將會停止擷取串流。</span><span class="sxs-lookup"><span data-stu-id="fffba-323">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="fffba-324">選取或點選 [錄製] 來開始使用指定的設定錄製混合實境串流。</span><span class="sxs-lookup"><span data-stu-id="fffba-324">Select or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="fffba-325">**停止錄製** 將會中止並儲存錄製內容。</span><span class="sxs-lookup"><span data-stu-id="fffba-325">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="fffba-326">選取或點選 [拍攝相片] 來從擷取串流中拍攝靜止影像。</span><span class="sxs-lookup"><span data-stu-id="fffba-326">Select or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="fffba-327">選取或點選 [還原預設設定] 以還原音訊、相片和影片設定的預設設定。</span><span class="sxs-lookup"><span data-stu-id="fffba-327">Select or tap **Restore Default Settings** to restore the default settings for audio, photo, and video settings.</span></span>
* <span data-ttu-id="fffba-328">**影片與相片**：顯示在裝置上所拍攝影片和相片擷取的清單。</span><span class="sxs-lookup"><span data-stu-id="fffba-328">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

<span data-ttu-id="fffba-329">此頁面上的所有設定都適用於使用 Windows 裝置入口網站取得的擷取。</span><span class="sxs-lookup"><span data-stu-id="fffba-329">All settings on this page apply to captures taken using Windows Device Portal.</span></span> <span data-ttu-id="fffba-330">有些則額外適用於系統 MRC，包括 [開始] 功能表、硬體按鈕、全域語音命令、Miracast 和自訂 MRC 錄製器。</span><span class="sxs-lookup"><span data-stu-id="fffba-330">Some additionally apply to System MRC, including start menu, hardware buttons, global voice commands, Miracast, and custom MRC Recorders.</span></span>

|  <span data-ttu-id="fffba-331">設定</span><span class="sxs-lookup"><span data-stu-id="fffba-331">Setting</span></span>  |  <span data-ttu-id="fffba-332">適用於系統 MRC</span><span class="sxs-lookup"><span data-stu-id="fffba-332">Applies to System MRC</span></span>  |  <span data-ttu-id="fffba-333">適用於自訂 MRC 錄製器</span><span class="sxs-lookup"><span data-stu-id="fffba-333">Applies to Custom MRC Recorders</span></span> |
|----------|----------|----------|
|  <span data-ttu-id="fffba-334">全像投影</span><span class="sxs-lookup"><span data-stu-id="fffba-334">Holograms</span></span>  |  <span data-ttu-id="fffba-335">否</span><span class="sxs-lookup"><span data-stu-id="fffba-335">No</span></span>  |  <span data-ttu-id="fffba-336">否</span><span class="sxs-lookup"><span data-stu-id="fffba-336">No</span></span> |
|  <span data-ttu-id="fffba-337">PV 相機</span><span class="sxs-lookup"><span data-stu-id="fffba-337">PV camera</span></span>  |  <span data-ttu-id="fffba-338">否</span><span class="sxs-lookup"><span data-stu-id="fffba-338">No</span></span>  |  <span data-ttu-id="fffba-339">否</span><span class="sxs-lookup"><span data-stu-id="fffba-339">No</span></span> |
|  <span data-ttu-id="fffba-340">麥克風音訊</span><span class="sxs-lookup"><span data-stu-id="fffba-340">Mic Audio</span></span>  |  <span data-ttu-id="fffba-341">否</span><span class="sxs-lookup"><span data-stu-id="fffba-341">No</span></span>  |  <span data-ttu-id="fffba-342">否</span><span class="sxs-lookup"><span data-stu-id="fffba-342">No</span></span> |
|  <span data-ttu-id="fffba-343">App 音訊</span><span class="sxs-lookup"><span data-stu-id="fffba-343">App Audio</span></span>  |  <span data-ttu-id="fffba-344">否</span><span class="sxs-lookup"><span data-stu-id="fffba-344">No</span></span>  |  <span data-ttu-id="fffba-345">否</span><span class="sxs-lookup"><span data-stu-id="fffba-345">No</span></span> |
|  <span data-ttu-id="fffba-346">從相機呈現</span><span class="sxs-lookup"><span data-stu-id="fffba-346">Render from Camera</span></span>  |  <span data-ttu-id="fffba-347">是</span><span class="sxs-lookup"><span data-stu-id="fffba-347">Yes</span></span>    |  <span data-ttu-id="fffba-348">是 (可以覆寫)</span><span class="sxs-lookup"><span data-stu-id="fffba-348">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="fffba-349">即時預覽品質</span><span class="sxs-lookup"><span data-stu-id="fffba-349">Live preview quality</span></span>  |  <span data-ttu-id="fffba-350">否</span><span class="sxs-lookup"><span data-stu-id="fffba-350">No</span></span>  |  <span data-ttu-id="fffba-351">否</span><span class="sxs-lookup"><span data-stu-id="fffba-351">No</span></span> |
|  <span data-ttu-id="fffba-352">音訊媒體類別</span><span class="sxs-lookup"><span data-stu-id="fffba-352">Audio Media Category</span></span>  |  <span data-ttu-id="fffba-353">是</span><span class="sxs-lookup"><span data-stu-id="fffba-353">Yes</span></span>  |  <span data-ttu-id="fffba-354">否</span><span class="sxs-lookup"><span data-stu-id="fffba-354">No</span></span> |
|  <span data-ttu-id="fffba-355">App 音訊增益</span><span class="sxs-lookup"><span data-stu-id="fffba-355">App Audio Gain</span></span>  |  <span data-ttu-id="fffba-356">是</span><span class="sxs-lookup"><span data-stu-id="fffba-356">Yes</span></span>  |  <span data-ttu-id="fffba-357">是 (可以覆寫)</span><span class="sxs-lookup"><span data-stu-id="fffba-357">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="fffba-358">麥克風音訊增益</span><span class="sxs-lookup"><span data-stu-id="fffba-358">Mic Audio Gain</span></span>  |  <span data-ttu-id="fffba-359">是</span><span class="sxs-lookup"><span data-stu-id="fffba-359">Yes</span></span>  |  <span data-ttu-id="fffba-360">是 (可以覆寫)</span><span class="sxs-lookup"><span data-stu-id="fffba-360">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="fffba-361">擷取設定檔</span><span class="sxs-lookup"><span data-stu-id="fffba-361">Capture Profile</span></span>  |  <span data-ttu-id="fffba-362">是</span><span class="sxs-lookup"><span data-stu-id="fffba-362">Yes</span></span>  |  <span data-ttu-id="fffba-363">否</span><span class="sxs-lookup"><span data-stu-id="fffba-363">No</span></span> |
|  <span data-ttu-id="fffba-364">相片解析度</span><span class="sxs-lookup"><span data-stu-id="fffba-364">Photo Resolution</span></span>  |  <span data-ttu-id="fffba-365">是</span><span class="sxs-lookup"><span data-stu-id="fffba-365">Yes</span></span>  |  <span data-ttu-id="fffba-366">否</span><span class="sxs-lookup"><span data-stu-id="fffba-366">No</span></span> |
|  <span data-ttu-id="fffba-367">影片解析度和畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="fffba-367">Video Resolution and Frame-rate</span></span>  |  <span data-ttu-id="fffba-368">是</span><span class="sxs-lookup"><span data-stu-id="fffba-368">Yes</span></span>  |  <span data-ttu-id="fffba-369">否</span><span class="sxs-lookup"><span data-stu-id="fffba-369">No</span></span> |
|  <span data-ttu-id="fffba-370">影片防震緩衝區</span><span class="sxs-lookup"><span data-stu-id="fffba-370">Video Stabilization Buffer</span></span>  |  <span data-ttu-id="fffba-371">是</span><span class="sxs-lookup"><span data-stu-id="fffba-371">Yes</span></span>  |  <span data-ttu-id="fffba-372">是 (可以覆寫)</span><span class="sxs-lookup"><span data-stu-id="fffba-372">Yes (can be overridden)</span></span> |

> [!NOTE]
> <span data-ttu-id="fffba-373">[同步 MRC 有以下限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)：</span><span class="sxs-lookup"><span data-stu-id="fffba-373">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="fffba-374">如果應用程式在 Windows 裝置入口網站錄製影片時嘗試存取相片/攝影機，將會停止影片錄製。</span><span class="sxs-lookup"><span data-stu-id="fffba-374">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="fffba-375">如果應用程式透過 SharedReadOnly 模式存取相片/攝影機，則 HoloLens 2 不會停止錄製影片。</span><span class="sxs-lookup"><span data-stu-id="fffba-375">HoloLens 2 will not stop recording video if the app accesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="fffba-376">如果應用程式主動使用相片/攝影機，Windows 裝置入口網站就能夠拍攝相片或錄製影片。</span><span class="sxs-lookup"><span data-stu-id="fffba-376">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="fffba-377">即時串流：</span><span class="sxs-lookup"><span data-stu-id="fffba-377">Live streaming:</span></span>
>   * <span data-ttu-id="fffba-378">HoloLens (第 1 代) 可避免應用程式在從 Windows 裝置入口網站即時串流時存取相片/攝影機。</span><span class="sxs-lookup"><span data-stu-id="fffba-378">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="fffba-379">如果應用程式主動使用相片/攝影機，HoloLens (第 1 代) 將無法即時串流。</span><span class="sxs-lookup"><span data-stu-id="fffba-379">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="fffba-380">當應用程式嘗試以 ExclusiveControl 模式存取相片/攝影機時，HoloLens 2 會自動停止即時串流。</span><span class="sxs-lookup"><span data-stu-id="fffba-380">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="fffba-381">當應用程式主動使用 PV 相機時，HoloLens 2 可以啟動即時串流。</span><span class="sxs-lookup"><span data-stu-id="fffba-381">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="fffba-382">效能追蹤</span><span class="sxs-lookup"><span data-stu-id="fffba-382">Performance Tracing</span></span>

<span data-ttu-id="fffba-383">![Microsoft HoloLens 上 Windows 裝置入口網站的效能追蹤頁面](images/using-windows-portal-img-08.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-383">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-08.png)</span></span><br>
<span data-ttu-id="fffba-384">*Microsoft HoloLens 上 Windows 裝置入口網站的效能追蹤頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-384">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-385">從您的 HoloLens 擷取 [Windows Performance Recorder](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR) 追蹤。</span><span class="sxs-lookup"><span data-stu-id="fffba-385">Capture [Windows Performance Recorder](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="fffba-386">**可用的設定檔**：從下拉式清單選取 WPR 設定檔，然後選取或點選 [開始] 以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="fffba-386">**Available profiles**: Select the WPR profile from the dropdown, and select or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="fffba-387">**自訂設定檔**：選取或點選 [瀏覽]，以從您的電腦選擇 WPR 設定檔。</span><span class="sxs-lookup"><span data-stu-id="fffba-387">**Custom profiles**: Select or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="fffba-388">選取或點選 [上傳並開始] 以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="fffba-388">Select or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="fffba-389">若要停止追蹤，請選取 [停止] 連結。</span><span class="sxs-lookup"><span data-stu-id="fffba-389">To stop the trace, select the stop link.</span></span> <span data-ttu-id="fffba-390">留在此頁面上，直到追蹤檔案下載完成。</span><span class="sxs-lookup"><span data-stu-id="fffba-390">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="fffba-391">擷取的 ETL 檔案可以在 [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)) 中開啟以進行分析。</span><span class="sxs-lookup"><span data-stu-id="fffba-391">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)).</span></span>

### <a name="processes"></a><span data-ttu-id="fffba-392">處理程序</span><span class="sxs-lookup"><span data-stu-id="fffba-392">Processes</span></span>

<span data-ttu-id="fffba-393">![Microsoft HoloLens 上 Windows 裝置入口網站中的程序頁面](images/using-windows-portal-img-09.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-393">![Processes page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-09.png)</span></span><br>
<span data-ttu-id="fffba-394">*Microsoft HoloLens 上 Windows 裝置入口網站中的程序頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-394">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-395">顯示有關目前正在執行之處理程序的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fffba-395">Shows details about currently running processes.</span></span> <span data-ttu-id="fffba-396">這包括 App 與系統處理程序。</span><span class="sxs-lookup"><span data-stu-id="fffba-396">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="fffba-397">系統效能</span><span class="sxs-lookup"><span data-stu-id="fffba-397">System Performance</span></span>

<span data-ttu-id="fffba-398">![Microsoft HoloLens 上 Windows 裝置入口網站中的系統效能頁面](images/using-windows-portal-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-398">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-10.png)</span></span><br>
<span data-ttu-id="fffba-399">*Microsoft HoloLens 上 Windows 裝置入口網站中的系統效能頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-399">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-400">顯示系統診斷資訊的即時圖表，例如電源使用量、畫面播放速率與 CPU 負載。</span><span class="sxs-lookup"><span data-stu-id="fffba-400">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="fffba-401">下列為可用的衡量標準：</span><span class="sxs-lookup"><span data-stu-id="fffba-401">These are the available metrics:</span></span>
* <span data-ttu-id="fffba-402">**SoC 電源**：系統單晶片電源瞬間使用量 (一分鐘內的平均值)</span><span class="sxs-lookup"><span data-stu-id="fffba-402">**SoC power**: Instantaneous system-on-chip power usage, averaged over one minute</span></span>
* <span data-ttu-id="fffba-403">**系統電源**：系統電源瞬間使用量 (一分鐘內的平均值)</span><span class="sxs-lookup"><span data-stu-id="fffba-403">**System power**: Instantaneous system power usage, averaged over one minute</span></span>
* <span data-ttu-id="fffba-404">**畫面播放速率**：每秒畫面格數、每秒遺失的 VBlanks 數，以及連續遺失的 VBlanks 數</span><span class="sxs-lookup"><span data-stu-id="fffba-404">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="fffba-405">**GPU**：GPU 引擎使用量、可用總計的百分比</span><span class="sxs-lookup"><span data-stu-id="fffba-405">**GPU**: GPU engine usage, percent of total available</span></span>
* <span data-ttu-id="fffba-406">**CPU**︰可用總計的百分比</span><span class="sxs-lookup"><span data-stu-id="fffba-406">**CPU**: percent of total available</span></span>
* <span data-ttu-id="fffba-407">**I/O**：讀取與寫入</span><span class="sxs-lookup"><span data-stu-id="fffba-407">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="fffba-408">**網路**：已接收與已傳送</span><span class="sxs-lookup"><span data-stu-id="fffba-408">**Network**: Received and sent</span></span>
* <span data-ttu-id="fffba-409">**記憶體**：總計、使用中、已認可的、分頁與非分頁</span><span class="sxs-lookup"><span data-stu-id="fffba-409">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="fffba-410">[App]</span><span class="sxs-lookup"><span data-stu-id="fffba-410">Apps</span></span>

<span data-ttu-id="fffba-411">![Microsoft HoloLens 上 Windows 裝置入口網站的應用程式頁面](images/using-windows-portal-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-411">![Apps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-11.png)</span></span><br>
<span data-ttu-id="fffba-412">*Microsoft HoloLens 上 Windows 裝置入口網站的應用程式頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-412">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-413">管理安裝在 HoloLens 上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fffba-413">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="fffba-414">**已安裝的應用程式**：移除並啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="fffba-414">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="fffba-415">**執行中應用程式**：列出目前執行中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fffba-415">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="fffba-416">**安裝應用程式**：從電腦/網路上的資料夾，選取安裝的應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="fffba-416">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="fffba-417">**相依性**：新增所要安裝應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="fffba-417">**Dependency**: Add dependencies for the app you're going to install.</span></span>
* <span data-ttu-id="fffba-418">**部署**：將選取的應用程式 + 相依性部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fffba-418">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="fffba-419">應用程式損毀傾印頁面</span><span class="sxs-lookup"><span data-stu-id="fffba-419">App Crash Dumps</span></span>

<span data-ttu-id="fffba-420">![Microsoft HoloLens 上 Windows 裝置入口網站的應用程式損毀傾印頁面](images/using-windows-portal-img-12.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-420">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-12.png)</span></span><br>
<span data-ttu-id="fffba-421">*Microsoft HoloLens 上 Windows 裝置入口網站的應用程式損毀傾印頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-421">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-422">此頁面可讓您收集側載 App 的損毀傾印。</span><span class="sxs-lookup"><span data-stu-id="fffba-422">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="fffba-423">請針對您想要收集損毀傾印的應用程式，選取其 [啟用的損毀傾印] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fffba-423">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="fffba-424">返回此頁面以收集損毀傾印。</span><span class="sxs-lookup"><span data-stu-id="fffba-424">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="fffba-425">傾印檔案可以在 [Visual Studio 中開啟以進行偵錯](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files)。</span><span class="sxs-lookup"><span data-stu-id="fffba-425">Dump files can be [opened in Visual Studio for debugging](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="fffba-426">檔案總管</span><span class="sxs-lookup"><span data-stu-id="fffba-426">File Explorer</span></span>

<span data-ttu-id="fffba-427">![Microsoft HoloLens 上 Windows 裝置入口網站的檔案總管頁面](images/using-windows-portal-img-13.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-427">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-13.png)</span></span><br>
<span data-ttu-id="fffba-428">*Microsoft HoloLens 上 Windows 裝置入口網站的檔案總管頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-428">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-429">使用檔案總管來瀏覽、上傳和下載檔案。</span><span class="sxs-lookup"><span data-stu-id="fffba-429">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="fffba-430">您可以針對從 Visual Studio 或裝置入口網站部署的應用程式，使用 [文件] 資料夾、[圖片] 資料夾和 [本機儲存體] 資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="fffba-430">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="fffba-431">Kiosk 模式</span><span class="sxs-lookup"><span data-stu-id="fffba-431">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="fffba-432">Kiosk 模式僅適用於 [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features)。</span><span class="sxs-lookup"><span data-stu-id="fffba-432">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features).</span></span>

![Microsoft HoloLens 上的 Windows 裝置入口網站中的 Kiosk 模式頁面](images/using-windows-portal-img-14.png)

<span data-ttu-id="fffba-434">如需透過 Windows 裝置入口網站啟用 Kiosk 模式的最新指示，請參閱 Windows IT Pro 中心的[以 Kiosk 模式設定 HoloLens](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 文章。</span><span class="sxs-lookup"><span data-stu-id="fffba-434">Check the [Set up HoloLens in kiosk mode](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="fffba-435">記錄</span><span class="sxs-lookup"><span data-stu-id="fffba-435">Logging</span></span>

<span data-ttu-id="fffba-436">![Microsoft HoloLens 上 Windows 裝置入口網站的記錄頁面](images/using-windows-portal-img-15.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-436">![Logging page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-15.png)</span></span><br>
<span data-ttu-id="fffba-437">*Microsoft HoloLens 上 Windows 裝置入口網站的記錄頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-437">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-438">管理 HoloLens 上的即時 Windows 事件追蹤 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="fffba-438">Manages real-time Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="fffba-439">選取 [隱藏提供者]，以只顯示 [事件] 清單。</span><span class="sxs-lookup"><span data-stu-id="fffba-439">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="fffba-440">**已註冊的提供者**：選取 ETW 提供者與追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="fffba-440">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="fffba-441">追蹤等級是下列其中一個值 ︰</span><span class="sxs-lookup"><span data-stu-id="fffba-441">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="fffba-442">異常結束或終止</span><span class="sxs-lookup"><span data-stu-id="fffba-442">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="fffba-443">嚴重錯誤</span><span class="sxs-lookup"><span data-stu-id="fffba-443">Severe errors</span></span>
   3. <span data-ttu-id="fffba-444">警告</span><span class="sxs-lookup"><span data-stu-id="fffba-444">Warnings</span></span>
   4. <span data-ttu-id="fffba-445">非錯誤警告</span><span class="sxs-lookup"><span data-stu-id="fffba-445">Non-error warnings</span></span>

<span data-ttu-id="fffba-446">選取或點選 [啟用] 以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="fffba-446">Select or tap **Enable** to start tracing.</span></span> <span data-ttu-id="fffba-447">提供者已新增到 [啟用的提供者] 下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="fffba-447">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="fffba-448">**自訂提供者**：選取自訂 ETW 提供者與追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="fffba-448">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="fffba-449">依 GUID 識別提供者。</span><span class="sxs-lookup"><span data-stu-id="fffba-449">Identify the provider by its GUID.</span></span> <span data-ttu-id="fffba-450">不要在 GUID 中包含括號。</span><span class="sxs-lookup"><span data-stu-id="fffba-450">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="fffba-451">**啟用的提供者**：列出已啟用的提供者。</span><span class="sxs-lookup"><span data-stu-id="fffba-451">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="fffba-452">從下拉式清單選取提供者，然後按一下或點選 [停用] 以停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="fffba-452">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="fffba-453">按一下或點選 [全部停止] 以暫停所有追蹤。</span><span class="sxs-lookup"><span data-stu-id="fffba-453">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="fffba-454">**提供者歷程記錄**：顯示目前工作階段期間已啟用的 ETW 提供者。</span><span class="sxs-lookup"><span data-stu-id="fffba-454">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="fffba-455">按一下或點選 [啟用] 以啟用已停用的提供者。</span><span class="sxs-lookup"><span data-stu-id="fffba-455">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="fffba-456">按一下或點選 [清除] 以清除歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="fffba-456">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="fffba-457">**事件**：以表格格式列出所選提供者的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="fffba-457">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="fffba-458">此表格會即時更新。</span><span class="sxs-lookup"><span data-stu-id="fffba-458">This table is updated in real time.</span></span> <span data-ttu-id="fffba-459">在表格下方，按一下 [清除] 按鈕，以刪除表格中的所有 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="fffba-459">Beneath the table, click the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="fffba-460">這不會停用任何提供者。</span><span class="sxs-lookup"><span data-stu-id="fffba-460">This doesn't disable any providers.</span></span> <span data-ttu-id="fffba-461">您可以按一下 [儲存到檔案]，在本機將目前收集的 ETW 事件匯出到 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="fffba-461">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="fffba-462">**篩選**：可讓您篩選由識別碼、關鍵字、層級、提供者名稱、工作名稱或文字所收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="fffba-462">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="fffba-463">您可以將數個準則結合在一起：</span><span class="sxs-lookup"><span data-stu-id="fffba-463">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="fffba-464">針對套用至相同屬性的準則，會顯示可滿足任一準則的事件。</span><span class="sxs-lookup"><span data-stu-id="fffba-464">For criteria applying to the same property, events that can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="fffba-465">針對套用至不同屬性的準則，事件必須滿足所有準則</span><span class="sxs-lookup"><span data-stu-id="fffba-465">For criteria applying to a different property, events must satisfy all of the criteria</span></span>

<span data-ttu-id="fffba-466">例如，您可以指定準則 *(工作名稱包含 'Foo' 或 'Bar') AND (文字包含 'error' 或 'warning')*</span><span class="sxs-lookup"><span data-stu-id="fffba-466">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="fffba-467">模擬</span><span class="sxs-lookup"><span data-stu-id="fffba-467">Simulation</span></span>

<span data-ttu-id="fffba-468">![Microsoft HoloLens 上 Windows 裝置入口網站的模擬頁面](images/using-windows-portal-img-16.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-468">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-16.png)</span></span><br>
<span data-ttu-id="fffba-469">*Microsoft HoloLens 上 Windows 裝置入口網站的模擬頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-469">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-470">允許您記錄並播放輸入資料以進行測試。</span><span class="sxs-lookup"><span data-stu-id="fffba-470">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="fffba-471">**擷取房間**：用來下載模擬的房間檔案，其中包含針對使用者周遭環境的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="fffba-471">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="fffba-472">為房間命名，然後按一下 [擷取] 來將資料在您的電腦上儲存為 .xef 檔案。</span><span class="sxs-lookup"><span data-stu-id="fffba-472">Name the room and then click **Capture** to save the data as an .xef file on your PC.</span></span> <span data-ttu-id="fffba-473">此房間檔案可以載入 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="fffba-473">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="fffba-474">**錄製**：檢查要錄製的串流、為錄製命名，然後按一下或點選 [錄製] 開始錄製。</span><span class="sxs-lookup"><span data-stu-id="fffba-474">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="fffba-475">使用您的 HoloLens 執行動作，然後按一下 [停止] 來將資料在您的電腦上儲存為 .xef 檔案。</span><span class="sxs-lookup"><span data-stu-id="fffba-475">Perform actions with your HoloLens and then click **Stop** to save the data as an .xef file on your PC.</span></span> <span data-ttu-id="fffba-476">此檔案可以載入 HoloLens 模擬器或裝置。</span><span class="sxs-lookup"><span data-stu-id="fffba-476">This file can be loaded on the HoloLens emulator or device.</span></span>
  >[!NOTE]
  ><span data-ttu-id="fffba-477">錄製功能目前僅適用于 HoloLens 第1代。</span><span class="sxs-lookup"><span data-stu-id="fffba-477">The Recording feature is currently only available on the HoloLens 1st gen.</span></span> <span data-ttu-id="fffba-478">HoloLens 2 尚不支援錄製，但支援播放現有錄製。</span><span class="sxs-lookup"><span data-stu-id="fffba-478">Recording is not yet supported on HoloLens 2, but Playback of existing recordings is supported.</span></span>
* <span data-ttu-id="fffba-479">**播放**：按一下或點選 [上傳錄製]，從電腦中選取 xef 檔案，並將資料傳送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fffba-479">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="fffba-480">**控制模式**：從下拉式清單中選取 [預設] 或 [模擬]，然後按一下或點選 [設定] 按鈕來選取 HoloLens 上的模式。</span><span class="sxs-lookup"><span data-stu-id="fffba-480">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="fffba-481">選擇 [模擬] 將會停用 HoloLens 上實際的感應器，並改為使用已上傳的模擬資料。</span><span class="sxs-lookup"><span data-stu-id="fffba-481">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="fffba-482">如果您切換到 [模擬]，您的 HoloLens 不會對真實使用者做出回應，直到您切換回 [預設] 為止。</span><span class="sxs-lookup"><span data-stu-id="fffba-482">If you switch to "Simulation", your HoloLens won't respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="fffba-483">網路功能</span><span class="sxs-lookup"><span data-stu-id="fffba-483">Networking</span></span>

<span data-ttu-id="fffba-484">![Microsoft HoloLens 上 Windows 裝置入口網站的網路功能頁面](images/using-windows-portal-img-17.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-484">![Networking page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-17.png)</span></span><br>
<span data-ttu-id="fffba-485">*Microsoft HoloLens 上 Windows 裝置入口網站的網路功能頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-485">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-486">管理 HoloLens 上的 Wi-Fi 連線。</span><span class="sxs-lookup"><span data-stu-id="fffba-486">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="fffba-487">**WiFi 介面卡**：使用下拉式清單控制項選取 Wi-Fi 介面卡和設定檔。</span><span class="sxs-lookup"><span data-stu-id="fffba-487">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="fffba-488">按一下或點擊 [連線] 以使用選取的介面卡。</span><span class="sxs-lookup"><span data-stu-id="fffba-488">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="fffba-489">**可用網路**：列出 HoloLens 可以連線的 Wi-Fi 網路。</span><span class="sxs-lookup"><span data-stu-id="fffba-489">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="fffba-490">按一下或點選 [重新整理] 以更新清單。</span><span class="sxs-lookup"><span data-stu-id="fffba-490">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="fffba-491">**IP 設定**：顯示網路連線的 IP 位址和其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fffba-491">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="fffba-492">虛擬輸入</span><span class="sxs-lookup"><span data-stu-id="fffba-492">Virtual Input</span></span>

<span data-ttu-id="fffba-493">![Microsoft HoloLens 上 Windows 裝置入口網站的虛擬輸入頁面](images/using-windows-portal-img-18.png)</span><span class="sxs-lookup"><span data-stu-id="fffba-493">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-18.png)</span></span><br>
<span data-ttu-id="fffba-494">*Microsoft HoloLens 上 Windows 裝置入口網站的虛擬輸入頁面*</span><span class="sxs-lookup"><span data-stu-id="fffba-494">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fffba-495">從遠端電腦傳送鍵盤輸入到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fffba-495">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="fffba-496">按一下或點選 [虛擬鍵盤] 下方的區域，來啟用傳送按鍵輸入到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fffba-496">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="fffba-497">在 [輸入文字] 文字方塊中輸入，然後按一下或點選 [傳送]，將按鍵輸入傳送到使用中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fffba-497">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="fffba-498">裝置入口網站 REST API</span><span class="sxs-lookup"><span data-stu-id="fffba-498">Device Portal REST APIs</span></span>

<span data-ttu-id="fffba-499">裝置入口網站中所有的項目都是以 [REST API](device-portal-api-reference.md) (可選擇性地讓您用來存取資料，並以程式設計方式控制裝置) 為基礎所建置。</span><span class="sxs-lookup"><span data-stu-id="fffba-499">Everything in the device portal is built on top of [REST APIs](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="fffba-500">疑難排解</span><span class="sxs-lookup"><span data-stu-id="fffba-500">Troubleshooting</span></span>

### <a name="how-to-fix-the-its-lonely-here-message"></a><span data-ttu-id="fffba-501">如何修正「此處暫無任何項目」訊息</span><span class="sxs-lookup"><span data-stu-id="fffba-501">How to fix the "It's lonely here" message</span></span>

> [!NOTE]
> <span data-ttu-id="fffba-502">如果在 Hololens 2 上使用之前在 HoloLens (第一代) 上使用，則從 HoloLens 2 移轉到 HoloLens (第一代) 可能會導致頁面變得空無一物。</span><span class="sxs-lookup"><span data-stu-id="fffba-502">Going from a HoloLens 2 to HoloLens (1st gen) may cause the pages to become lonely if used on the HoloLens 2 prior to use on the HoloLens (1st gen).</span></span>

![裝置入口網站頁面中的「此處暫無任何項目」訊息](images/using-windows-portal-img-19.png)

1. <span data-ttu-id="fffba-504">從左上角的功能表中，選取 [重設版面配置]：</span><span class="sxs-lookup"><span data-stu-id="fffba-504">Select **Reset layout** from the top-left Menu:</span></span>

![從裝置入口網站功能表中，選取 [重設版面配置]](images/using-windows-portal-img-20.png)

2. <span data-ttu-id="fffba-506">按一下 [重設工作區] 標題下的 [重設版面配置]。</span><span class="sxs-lookup"><span data-stu-id="fffba-506">Click **Reset layout** under the **Reset workspace** heading.</span></span> <span data-ttu-id="fffba-507">入口網站頁面會自動重新整理並顯示您的內容。</span><span class="sxs-lookup"><span data-stu-id="fffba-507">The portal page will automatically refresh and display your content.</span></span>

![從 [重設工作區] 頁面選取 [重設版面配置]](images/using-windows-portal-img-21.png)
