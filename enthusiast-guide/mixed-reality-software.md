---
title: 混合實境軟體概觀和發行歷程記錄
description: 概述 Windows Mixed Reality 的主要軟體元件及其發行歷程記錄
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，軟體元件，發行歷程記錄，版本資訊，版本歷程記錄
appliesto:
- Windows 10
ms.openlocfilehash: 0dd2ef30252189d006bfaf5702c47dce72f2798d
ms.sourcegitcommit: d8db38647cf45f05b9445ceaf057d4cd01721ee6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97091302"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>混合實境軟體概觀和發行歷程記錄

## <a name="introduction-to-mixed-reality-software"></a>混合現實軟體簡介

Windows Mixed Reality 是由下列主要軟體元件所組成：

1. **混合實境入口**，提供主要 Windows Mixed Reality 體驗
    * 在 Windows 10，1709和1803版中，混合實境入口是 Windows 10 作業系統的重要元件，並透過 Windows Update 進行更新。
    * 在 Windows 10 版本1809和更新版本中，混合實境入口會透過 Microsoft Store 應用程式更新。
2. **混合現實隨選封裝** (FOD) ，在混合實境入口首次執行時自動下載並安裝。 您可以在[這裡](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)找到 FOD 套件的詳細資訊
3. **混合現實耳機和移動控制器驅動程式**（也稱為 HoloLens 感應器驅動程式）是可讓 Windows Mixed Reality 耳機使用 Windows Mixed Reality 的重要驅動程式套件。 這項功能會在您第一次插入混合現實耳機時，透過 Windows Update 自動下載和安裝，並透過 Windows Update 定期更新
4. **混合現實移動控制器模型驅動程式** 包含混合現實移動控制器的3d 模型，以及協力廠商混合現實體驗所需的模型。 這項功能會在您第一次將混合現實移動控制器配對至您的電腦時自動下載並安裝 Windows Update，並透過 Windows Update 進行更新
5. **Windows 10，版本 1709 (秋季建立者的更新) 或更新版本** ，包含可啟用的主要作業系統元件和技術 Windows Mixed Reality

此外，在 SteamVR 中使用 Windows Mixed Reality 需要下列軟體：

6. **SteamVR**，由閥門 Corporation 開發和維護，可在串流上啟用虛擬實境應用程式和遊戲。 您可以在[這裡](https://go.microsoft.com/fwlink/?linkid=862788)找到更多資訊
7. SteamVR 元件的 **Windows Mixed Reality** ，可橋接 SteamVR 與 Windows Mixed Reality。 如需此元件的詳細資訊，請參閱 [Windows Mixed Reality For SteamVR 頁面。](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

管理您的 Windows Mixed Reality 耳機：

8. 每個耳機製造商開發和維護的 **裝置附屬應用程式**，提供您 Windows Mixed Reality 耳機的快速簡介。 在具有內建藍牙功能的耳機上，裝置附屬應用程式可讓您將動作控制器還原為其原廠藍牙配對。 某些耳機 (例如 Samsung 電影對白和 Samsung 電影對白 +) 也會使用裝置附屬應用程式，從耳機製造商提供耳機固件更新。 此應用程式會在第一次插入耳機時自動下載，而且可以在 Windows [開始] 功能表中找到。

## <a name="windows-10-release-notes---may-2020"></a>Windows 10 版本資訊-5 月2020

**Windows 10 5 月2020更新 (v2004)** 包含 WINDOWS MIXED REALITY (VR) 耳機的新功能，例如在混合實境首頁中啟動 Win32 應用程式的能力。 HoloLens (第1代) 長期維護 (LTS) ，每月發行服務更新。

若要更新為電腦上的最新版本 Windows Mixed Reality 沉浸式 (VR) 耳機，請開啟 [ **設定** ] 應用程式，移至 [ **更新 & 安全性**]，然後選取 [ **檢查更新** ] 按鈕。 在 Windows 10 的電腦上，您也可以使用 [Windows media 建立工具](https://www.microsoft.com/software-download/windows10)，以手動方式安裝 **Windows 10 2020 更新**。

**Desktop 的最新版本**： Windows 10 v2004 (10.0.19041.264) 

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沉浸式耳機的更新

#### <a name="introducing-the-new-microsoft-edge"></a>新 Microsoft Edge 簡介
如 [先前所宣佈](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge)，我們已使用 Windows Mixed Reality 中的新 Microsoft Edge 瀏覽器進行更新，以提供更好的支援。 新的 Microsoft Edge 採用 Chromium 的開放原始碼專案，為客戶建立更好的 web 相容性，並為所有 網頁程式開發人員提供更好的 web 片段。 它也支援 WebXR，這是用來建立適用于 VR 耳機之沉浸式 web 體驗的新標準，取代 WebVR。

#### <a name="improved-settings-for-wmr"></a>改良的 WMR 設定
感謝您的意見反應，我們已新增並闡明耳機顯示頁面上的設定：

* **我的家用的視覺品質** 變更這些設定只會影響 (懸崖之屋和 Skyloft) 的混合實境首頁環境：

* **調整混合實境首頁中的詳細資料層級和效果品質** -這會變更我們在家裡使用的部分轉譯。 尤其是，不同材質的視覺品質 (木頭、具體等 ) 將會隨著您將此設定從低變更為高而調整。

* **變更應用程式視窗解析度** -根據預設，在首頁中啟動的大部分2d 視窗都會以720p 解析度啟動。 雖然您可以手動手動調整它們的大小 &，您也可以選擇讓它們全都以1080p 的方式啟動。 先前，此選項是以視覺品質 (搶鮮版（Beta）) 選項的形式提供。 我們已適當地將它分割為個別設定。

* **體驗選項** -這些選項會調整混合現實體驗，以降低硬體可能難以跟上不受限制 90 fps 的系統負載。 您可以選擇明確啟用或停用這些額外的設定，或選擇 [讓 Windows 決定]，讓啟發學習法繼續決定何時要切換這些設定。

* **解決方案** -如果您有高解析度耳機（如 HP 的回音），我們支援以原生解析度執行，或基於效能考慮減少解析度。 先前的耳機（像是 Samsung 電影對白和電影對白 +）只支援單一解析度，因此您將無法在那些耳機上變更此設定。

* **畫面播放速率** -您現在可以手動設定耳機顯示器的畫面播放速率，或繼續讓 Windows 使用其啟發學習法來判斷 60 hz 或 90 Hz 是否更適當。

* **校正** -如同之前，如果您的耳機支援，您可以調整 IPD (interpupillary 距離) 。

* **輸入切換** -切換輸入焦點切換 (Win + Y) 行為，根據狀態感應器回饋) 或手動 (自動。

#### <a name="new-cortana-app"></a>新 Cortana 應用程式
Windows 的這項更新包含最新版本的 Cortana 應用程式（目前僅限英文），不再支援特定的混合現實特定命令，例如「拍攝相片」和「拍攝影片」。 您仍然可以使用新的 Cortana 來啟動應用程式，而且它也支援以生產力為焦點的新命令，例如「我的下一個會議是什麼時候」。 或「傳送電子郵件給 <name> 我遲到的時候。」
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>19041.546 2020 年10月10日發行 (推出的其他更新) 
此桌面每月服務更新包括下列 Windows Mixed Reality 裝置的變更： 
* 減少 Windows Mixed Reality 前端掛載顯示器 (HMD) 的扭曲和 aberrations。 
* 新增即將推出之 HP Windows Mixed Reality 移動控制器的支援。 
* 在某些情況下，當無法達到90Hz 時，將 Windows Mixed Reality 中的 [90Hz 重新整理頻率] 設定的行為變更為 [不會再自動切換回 60Hz]。 

#### <a name="please-help-us-improve"></a>請協助我們改進！
我們會持續尋找改善相容性。  如果您認為慣用的傳統 Win32 應用程式在 Windows Mixed Reality 時無法正常運作，請透過我們的 [意見反應中樞](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)提交意見反應。

### <a name="prior-release-notes"></a>先前的版本資訊

* [版本資訊-2019 年5月](release-notes-may-2019.md)
* [版本資訊 - 2018 年 10 月](release-notes-october-2018.md)
* [版本資訊-2018 年4月](release-notes-april-2018.md)
* [版本資訊 - 2017 年 10 月](release-notes-october-2017.md)
* [版本資訊 - 2016 年 8 月](release-notes-august-2016.md)
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>混合現實耳機和移動控制器驅動程式發行歷程記錄 ###

此驅動程式會透過 Windows Update 自動下載並安裝，但會以內嵌方式提供下載連結：

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10，2004版 (可能有2020更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 2020年12月10日  | 與 Windows 10、1903版和更新版本相容。<br/><ul><li>適用于 HP 控制器的新控制器固件，可解決某些控制器具有非正常運作觸發程式的問題。</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 2020年10月8日  | 與 Windows 10、1903版和更新版本相容。<br/><ul><li>HP 殘響 G2、HP Omnicept 和新 HP 控制器的官方支援。</li><li>HP 回音和 Samsung 電影對白 + 耳機的次要顯示器校正。  (需要 [Os 組建 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) 或更高版本 [，或 os 組建18362.1110 和 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) 或更高版本的) 。</li><li>電腦電源狀態從睡眠轉換成減少 SWW 1-4 錯誤的增強功能。</li><li>Windows Mixed Reality 耳機平臺的次要修正和可靠性改進。|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 2020 5 月7日      | 與 Windows 10、1903版和更新版本相容。<br/><ul><li>Windows Mixed Reality 耳機平臺的次要修正和可靠性改進。</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10，1903版 (可能有2019更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 2019年10月14日      | 與 Windows 10 版本1809和更新版本相容。<br/><ul><li>Windows Mixed Reality 耳機平臺次要修正。</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 6月24日，2019      | 與 Windows 10 版本1809和更新版本相容。<br/><ul><li>Windows Mixed Reality 耳機平臺和休眠的電腦和電源狀態轉換的可靠性改進。</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 2019 年 5 月 1 日      | 與 Windows 10 版本1809和更新版本相容。<br/><ul><li>包含 2017 Acer、Asus、Dell、Fujitsu、HP、聯想和 Medion Windows Mixed Reality 耳機的固件更新。 此固件更新透過特定圖形介面卡和/或圖形驅動程式來改善耳機顯示相容性和可靠性。</li><li>Windows Mixed Reality 耳機平臺和可靠性改進</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10，版本 1803 (2018 年4月更新) 和版本 1809 (年10月2018更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2019年1月2日      | 與 Windows 10、1803版和更新版本相容。<br/><ul><li>耳機追蹤抖動和斷斷續續修正</li><li>先出模式可靠性修正</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 2018年10月1日      | Windows 10 版本1809之驅動程式的初始公開版本。<br/>與 Windows 10、1803版和更新版本相容。<br/><ul><li>在 Windows 10 版本1809中啟用新的 Windows Mixed Reality 功能，例如 [下] 模式</li><li>耳機追蹤和可靠性改進</li><li>移動控制器追蹤和效能改善</li><li>USB 效能和改進</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 4月27日、2018      | Windows 10 之驅動程式的初始公開版本，版本1803<br/> <ul><li>耳機追蹤和可靠性改進</li><li>移動控制器追蹤和效能改善</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10，1709版 (秋季建立者更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 2018年2月6日    | <ul><li>3Glasses Blubur S2 Mixed Reality 耳機的官方支援</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 2017年12月19日   | <ul><li>解決某些電腦上導致 *發生錯誤的錯誤代碼* 2181038087-7 的隱藏問題</li><li>各種穩定性與可靠性修正</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 2017年12月5日    | <ul><li>改進耳機追蹤</li><li>移動控制器的觸控板回應性改進</li><li>解決驅動程式安裝有時會失敗的問題</li><li>各種穩定性與可靠性修正</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 2017年11月21日   | <ul><li>解決導致耳機顯示器的問題，在使用時有時會呈黑色</li><li>解決有時候會導致移動控制器消失的問題</li><li>Dell 面板耳機的狀態感應器效能改進</li><li>各種穩定性與可靠性修正</li></ul> |
   | 10.0.16299.1036  | 2017年11月7日    | <ul><li>移動控制器擲回技師修理改進：<ul><li>當位置精確度為近似值時，現在會正確回報速度，因此您現在可以在您的頭部背後擲出！</li><li>您可以在 [此處](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)的 "ThrowingStarter" unity 套件中找到擲回的範例程式碼。 開啟擲回的場景以開始使用</li></ul></li><li>改進的移動控制器電池報告</li><li>各種穩定性與可靠性修正</li></ul> |
   | 10.0.16299.1012  | 2017年10月17日    | 驅動程式的初始公開版本                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>混合現實移動控制器模型驅動程式發行歷程記錄 ###

此驅動程式也會透過 Windows Update 自動下載並安裝，但會以內嵌方式提供下載連結：

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10，2004版 (可能有2020更新) 

| 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 2020年9月16日      | 新 HP 運動控制器之驅動程式的初始公開版本。 與 Windows 10、1903版和更新版本相容。 此驅動程式僅與新的 HP 運動控制器相容。  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10，版本 1803 (2018 年4月更新) 和版本 1809 (年10月2018更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 2018年10月1日      | Windows 10 版本1809之驅動程式的初始公開版本。 與 Windows 10、1803版和更新版本相容。  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 2018年4月17日      | Windows 10 版本1803的驅動程式初始公開版本。  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10，1709版 (秋季建立者更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 2017年10月17日    | 驅動程式的初始公開版本                          |

### <a name="mixed-reality-portal-release-history"></a>混合實境入口發行歷程記錄 ###

在 Windows 10 版本1809和更新版本中， [混合實境入口](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) 會透過 Microsoft Store 應用程式更新。

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10 版本1809和更新版本 ####

   | 版本            | 發行日期          | 重大變更                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.20071.1133.0  | 2020 年 8 月 5 日        | <ul><li>支援 [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) 以暫停預覽視窗。</li></ul>  | 
   | 2000.20041.1212.0  | 2020 年 5 月 11 日          | <ul><li>解決造成不一致15-5 錯誤的計時問題。</li><li>改進了執行 Windows Mixed Reality 且沒有網際網路連線的支援。</li><li>改善透過 **設定控制器** 配對動作控制器的支援。</li></ul>  | 
   | 2000.20031.1202.0  | 2020 年 4 月 14 日        | <ul><li>支援註冊 Windows Mixed Reality 的相關資訊、秘訣和優惠。</li></ul>  | 
   | 2000.20011.1312.0  | 2020 年 2 月 11 日     | <ul><li>針對在2019年5月更新的裝置上使用 [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) 改善應用程式的支援。</li><li>解決存取範圍和鍵盤焦點問題</li></ul>  | 
   | 2000.19101.1211.0  | 2019年11月11日     | <ul><li>解決防止您切換房間界限視覺效果的問題。</li><li>解決防止您在房間界限設定期間將耳機置中的問題。</li></ul>  | 
   | 2000.19081.1301.0  | 2019 年 9 月 23 日    | <ul><li>解決耳機遇到硬體問題的問題，並顯示錯誤的錯誤訊息。 在先前的版本上收到1-4 錯誤碼的使用者，現在可能會收到更明確的裝置狀態錯誤碼。</li></ul>  |
   | 2000.19071.1302.0  | 2019年8月13日     | <ul><li>支援在5月2019更新的裝置上使用 [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) 的應用程式。</li></ul>  | 
   | 2000.19061.1011.0  | 2019 年 7 月 16 日         | <ul><li>支援自訂應用程式行為的 JSON 設定選項。 深入瞭解 https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup 。</li></ul>  | 

### <a name="steamvr-release-history"></a>SteamVR 發行歷程記錄 ###

您可以在這裡找到閥門的 SteamVR 版本資訊： [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>SteamVR 發行歷程記錄的 Windows Mixed Reality ###

您可以在這裡找到 SteamVR 元件 Windows Mixed Reality 的版本資訊： [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
