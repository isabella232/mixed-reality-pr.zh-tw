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
# <a name="other-questions"></a>其他問題

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>我的圖形驅動程式不受支援 (我收到圖形驅動程式失敗錯誤) 。

搜尋並執行 "dxdiag"：

1.  如果結果為「基本轉譯器」，則不會安裝圖形驅動程式。 修正方法：
    * 移至 **裝置管理員 > 動作 > 掃描硬體變更**。
    * 使用 Windows Update 來更新驅動程式。
    * 如果這無法解決問題，請移至製造商的網站，並安裝最新的驅動程式更新。 
    * 如果您的 GPU 無法使用更新，您的裝置可能不支援 WMR。 如果您認為應該如此，請聯絡 [支援](https://support.microsoft.com)人員。
2.  如果您收到「WDDM 2.1」或較舊的版本，則會安裝圖形驅動程式，但它可能不是最新版本。 若要取得最新版本：
    * 使用 Windows Update 來更新驅動程式。
    * 如果該更新無法修正問題，請移至製造商的網站，並安裝最新的驅動程式更新。 
    * 如果您的 GPU 無法使用更新，您的裝置可能不支援 WMR。 如果您認為應該如此，請聯絡 [支援](https://support.microsoft.com)人員。

如果 Windows Mixed Reality 安裝程式指出您的圖形配接器不符合需求，而您認為它的確如此，請確定您的耳機已插入正確的卡片中。

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>我的 Samsung 電影對白或電影對白 + 耳機固件更新停滯。

Samsung 擁有併發布透過其 "Samsung HMD 電影對白 Setup" 和 "Samsung HMD 電影對白 + Setup" 裝置附屬應用程式所提供的耳機固件更新。 如需有關 Samsung 固件更新問題的詳細資訊和協助，請聯絡 Samsung customer service。

如果固件更新程式停滯，而且沒有超過五分鐘的進度：

* 暫時拔掉所有其他 USB 裝置，然後重試一次固件更新。
* 將 Samsung 耳機連接到您電腦上的其他 USB 3.0 埠。
* 停用或卸載任何可能幹擾固件更新的軟體，例如 Gb 的 AORUS App Center。
* 使用不同的電腦來更新 Samsung 耳機固件。

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>如何? 在混合的生活中存取我的電腦桌面？
從 Windows 的 [耳機] 按鈕啟動桌面應用程式 **> 所有應用程式 > 桌面** ，以混合的方式存取您的電腦桌面。

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>如何查看混合現實中的多個監視器

根據預設，桌面應用程式會自動切換為顯示具有焦點的監視器。 如果您想要在混合現實中看到所有的監視器：

* 選取應用程式左上角的 [監視] 圖示。
* 停用 [自動切換監視器]。
* 挑選您想要查看的監視器。
* 啟動桌面應用程式的另一個實例。
* 選擇您想要在該實例上看到的監視器。
* 針對所有實體監視器重複執行。
您必須在每次重新開機 mixed reality 時，重新選擇要在每個桌面應用程式上顯示的監視器。

## <a name="my-desktop-app-only-shows-a-black-screen"></a>我的桌面應用程式只會顯示黑色畫面

如果您的電腦有 Nvidia 混合式 GPU，則在離散 GPU （而不是整合的 GPU）上執行 runtimebroker.exe 的 Nvidia 裝置可能會是個原因。 若要修正此問題，請遵循「[如何? 建立新程式的 Optimus 設定](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)」底下的指示。 新增 C:\windows\system32\runtimebroker.exe 並強制它在「整合式圖形」處理器上執行。 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>當我使用 Windows Mixed Reality 時，我的 Wi-Fi 會變慢。

如果您使用 2.4-GHz Wi-Fi 連接，您的移動控制器可能會減緩您的 Wi-fi：

* 切換至 5 GHz Wi-Fi 連接（如果有的話）。 [深入了解](https://support.microsoft.com/help/4000461)。
* 使用個別的 Bluetooth 介面卡，將您的動作控制器連接到您的電腦。 請參閱 [建議的介面卡](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)。

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>我收到一則訊息，表示插入和收取電腦的費用。 原因為何？

如果您使用的是膝上型電腦，則在電腦同時完全收取和插入電源時，Windows Mixed Reality 的效果最佳。

## <a name="what-is-the-experience-options-setting"></a>何謂體驗選項設定？

**設定 > 混合現實 > 耳機顯示器 > 體驗選項** 可讓您變更 Windows Mixed Reality 的效能設定。 這可讓您在各種內容中選擇硬體設定的最佳體驗。 您有三個體驗選項可供選擇：
* 自動： Windows Mixed Reality 將決定硬體設定的最佳體驗。 對於大部分的人來說，這是開始使用的最佳選擇。
* 60 Hz：將重新整理頻率設定為 60 Hz，並關閉特定功能，例如混合實境入口中的影片捕獲和預覽。
* 90 Hz：將更新頻率設定為 90 Hz。

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality 支援哪些語言

Windows Mixed Reality 提供下列語言版本：

* 簡體中文 (中國)
* 英文 (澳大利亞)
* 英文 (加拿大)
* 英文 (英國)
* 英文 (美國)
* 法文 (加拿大)
* 法文 (法國)
* 德文 (德國)
* 義大利文 (義大利)
* 日文 (日本)
* 西班牙文 (墨西哥)
* 西班牙文 (西班牙)

如果您的電腦設定為不同的語言，您可以使用 Windows Mixed Reality。 不過，介面會以英文顯示 (美國) ，而語音命令和聽寫則無法使用。 Windows Mixed Reality 螢幕小鍵盤僅限英文 (美國) 。 若要以另一種語言輸入文字，請使用連接到您電腦的實體鍵盤。 您也可以使用上面所列的其中一種支援 Windows Mixed Reality 語言的聽寫，只要在螢幕小鍵盤上選取 [麥克風] 即可。

Windows Mixed Reality 也提供下列語言版本，不需要語音命令或聽寫功能：
* 繁體中文 (臺灣和香港特別行政區) 
* 荷蘭文 (荷蘭)
* 韓文 (韓國)
* 俄文 (俄羅斯)

## <a name="i-have-questions-about-my-headset-hardware"></a>我有關于耳機硬體的問題。

如需有關耳機的詳細資訊，請洽詢製造商。 Box 中可能會有產品指南，您也可以嘗試製造商的網站。

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>如何? 卸載 Windows Mixed Reality？

1. 中斷耳機與電腦的連線。
2. 關閉 Windows Mixed Reality 入口網站。
2. 移至 [  **開始] > 設定 > 混合現實** ，然後選取 [卸載]。

當您準備好要再次開始使用耳機時，請將其插入，Windows Mixed Reality 入口網站會引導您完成安裝程式。

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>我收到「我們無法完成卸載 Windows Mixed Reality」訊息。

有些檔案（包括您的環境相關資訊）仍可能在您的電腦上。 如果您決定稍後重新安裝 Windows Mixed Reality，這可能會造成問題。 您可以藉由修改登錄和使用 Windows PowerShell 來執行命令，以手動方式從電腦移除任何剩餘的 Windows Mixed Reality 資訊。 _如果您不正確地修改登錄，可能會發生嚴重的問題。請務必小心遵循這些步驟。為了增加保護，請先備份登錄再進行修改，以便在發生問題時進行還原。_ 如需詳細資訊，請參閱 [如何在 Windows 中備份和 restory 登錄](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)。 

若要使用下列命令卸載 Windows mixed reality：
1. 重新啟動電腦。
2. 在 **搜尋** 方塊中，輸入 "regedit"，然後選取 [是]。
3. 移除下列登錄值：
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>，然後刪除 "FirstRunSucceeded"。</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>，然後刪除 "PreferDesktopSpeaker" 和 "PreferDesktopMic"。</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>，然後刪除 "DisableSpeechInput"。 注意：您必須針對已使用 Windows Mixed Reality 之電腦上的每個使用者帳戶，刪除 HHKEY_CURRENT_USER 中的登錄專案。</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>，然後刪除「DeviceID」和「模式」。</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>，然後刪除 "OnDeviceLearningCompleted"。</li> 
   </ul>
4. 移除下列登錄機碼： <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. 關閉登錄編輯程式。
6. 移至 **C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** 並刪除「RoomBounds.js開啟」。 針對已使用 Windows Mixed Reality 的每個使用者重複此步驟。
7. 開啟系統管理員命令提示字元，並移至 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors**。 刪除 "HeadTracking data" 資料夾的內容 (但不) 資料夾本身。
8. 在 [搜尋方塊] 中輸入 "powershell"，以滑鼠右鍵按一下 [Windows PowerShell]，然後選取 [以系統管理員身分執行]。
9. 在 Windows PowerShell： <ul>
   <li>在命令提示字元中，複製並貼上 <b>Dism/Online/Get-Capabilities</b>，然後按 enter。</b></li> 
   <li>複製以類比........ Desktop 開頭的功能身分識別。 如果不存在，則不會安裝專案，而且您可以跳到步驟 10) 。</li> 
   <li>複製並貼上下列命令提示字元，然後按 Enter： <b>Dism/Online/Remove-Capability/CapabilityName：在最後一個步驟中複製的功能身分識別</b></li>
   </ul>
10. 重新開機您的電腦。

