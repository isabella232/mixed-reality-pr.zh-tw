---
title: 軟體總覽和發行歷程記錄
description: 概述 Windows Mixed Reality、沉浸式耳機和其發行歷程記錄的主要軟體元件。
author: qianw211
ms.author: v-qianwen
ms.date: 09/30/2021
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，軟體元件，發行歷程記錄，版本資訊，版本歷程記錄
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: e20b2075e45620a7533dbb2d369d00e73b98f9c7
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436627"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>混合實境軟體概觀和發行歷程記錄

## <a name="introduction-to-mixed-reality-software"></a>混合現實軟體簡介

Windows Mixed Reality 是由下列主要軟體元件所組成：

1. **混合實境入口**，提供主要 Windows Mixed Reality 體驗
    * 在 Windows 10 1709 和1803版中，混合實境入口是透過 Windows Update 更新之 Windows 10 作業系統的主要元件。
    * 在 Windows 10 1809 版和更新版本中，混合實境入口會透過 Microsoft Store 應用程式更新。
    * 在 Windows 11 21H2 版中。
2. **混合現實隨選封裝** (FOD) ，在混合實境入口首次執行時自動下載並安裝。 您可以在[這裡](/windows/application-management/manage-windows-mixed-reality)找到 FOD 套件的詳細資訊
3. **混合現實耳機和移動控制器驅動程式**（也稱為 HoloLens 感應器驅動程式）是可讓 Windows Mixed Reality 耳機使用 Windows Mixed Reality 的重要驅動程式套件。 這項功能會在您第一次插入混合現實耳機時，透過 Windows Update 自動下載和安裝，並透過 Windows Update 定期更新
4. * * 混合式事實移動控制器模型驅動程式包含混合現實移動控制器的3D 模型，以及協力廠商混合現實體驗所需的模型。 這項功能會在您第一次將混合現實移動控制器配對至您的電腦時自動下載並安裝 Windows Update，並透過 Windows Update 進行更新
5. **Windows 10，版本 1709 (秋季建立者的更新) 或更新版本**，包含可啟用的主要作業系統元件和技術 Windows Mixed Reality

在 SteamVR 中使用 Windows Mixed Reality 需要下列軟體：

6. **SteamVR**，由閥門 Corporation 開發和維護，可在串流上啟用虛擬實境應用程式和遊戲。 您可以在[這裡](https://go.microsoft.com/fwlink/?linkid=862788)找到更多資訊
7. SteamVR 元件的 **Windows Mixed Reality** ，可橋接 SteamVR 與 Windows Mixed Reality。 如需此元件的詳細資訊，請參閱[Windows Mixed Reality for SteamVR 頁面。](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

管理您的 Windows Mixed Reality 耳機：

8. 每個耳機製造商開發和維護的 **裝置附屬應用程式**，提供您 Windows Mixed Reality 耳機的快速簡介。 在具有內建藍牙功能的耳機上，裝置附屬應用程式可讓您將動作控制器還原至其藍牙配對的工廠。 某些耳機 (例如 Samsung 電影對白和 Samsung 電影對白 +) 也會使用裝置附屬應用程式，從耳機製造商提供耳機固件更新。 此應用程式會在第一次插入耳機時自動下載，而且可以在 Windows 開始] 功能表中找到。

## <a name="windows-11-release-notes---october-2021"></a>Windows 11 版本資訊-2021 年10月

### <a name="infinite-expanse"></a>無限 Expanse

<img src="images\infinite-expanse-win11.png" alt="The Infinite Explanse environment">

<br>

* 新的虛擬家用環境適用于 Windows Mixed Reality 裝置，可大幅降低範圍和大小，以簡化為單一階段，而不是功能豐富的 Cliffhouse。 
* 以效能為基礎，無限 Expanse 的設計目的是針對較不具資源需求的虛擬家用環境，解決長期持續的客戶要求，讓客戶能夠從其遊戲和經驗中獲得最佳效能。 
* 您可以在 [**位置**] 功能表的 [釘選]**面板** 中找到這個新的虛擬 home 環境。 

### <a name="steamvr-boot-with-mixed-reality-portal-launch"></a>SteamVR boot 混合實境入口啟動

* 新設定可在 WMR 啟動時自動啟動 SteamVR，可讓您略過 WMR 首頁空間，並直接跳至 SteamVR。
   * 這項新設定可以在混合現實的 **設定** 應用程式中找到 **> 啟動和桌面 > 自動啟動**。
    
### <a name="new-startup-experience-settings"></a>新的啟動體驗設定

* 新的設定可讓您藉由在混合實境入口啟動時提高控制層級，來更妥善地設定您的理想啟動體驗。
* 您現在可以控制混合實境入口在裝置連線時或啟動狀態感應器啟動時是否啟動，以及控制虛擬桌面應用程式的開啟方式。
* 這些新設定可以在 **設定** 應用程式的 **混合現實 > 啟動和桌上型電腦** 上找到
    * 切換以啟動 HMD 外掛程式上的 MRP。
    * 當偵測到狀態時，切換以啟動 MRP。
    * 在桌面應用程式焦點上切換開啟桌面應用程式。

### <a name="prior-release-notes"></a>先前的版本資訊

* [版本資訊-2020 年5月](release-notes-may-2020.md)
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
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 2021年3月23日  | 與 Windows 10、1903版和更新版本相容。<br/><ul><li>更新「HP 回音」 G2 隱藏區網格的繞組順序，使其與其他耳機保持一致。</li><li>HP 回音的視覺效果品質改進。</li><li>Windows Mixed Reality 耳機平臺和可靠性改進。</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 2020年12月10日  | 與 Windows 10、1903版和更新版本相容。<br/><ul><li>適用于 HP 控制器的新控制器固件，可解決某些控制器具有非正常運作觸發程式的問題。</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 2020年10月8日  | 與 Windows 10、1903版和更新版本相容。<br/><ul><li>HP 殘響 G2、HP Omnicept 和新 HP 控制器的官方支援。</li><li>HP 回音和 Samsung 電影對白 + 耳機的次要顯示器校正。  (需要 [Os 組建 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) 或更高版本 [，或 os 組建18362.1110 和 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) 或更高版本的) 。</li><li>電腦電源狀態從睡眠轉換成減少 SWW 1-4 錯誤的改進。</li><li>Windows Mixed Reality 耳機平臺的次要修正和可靠性改進。|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 2020 5 月7日      | 與 Windows 10、1903版和更新版本相容。<br/><ul><li>Windows Mixed Reality 耳機平臺的次要修正和可靠性改進。</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10，1903版 (可能有2019更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 2019 年 10 月 14 日      | 與 Windows 10 版本1809和更新版本相容。<br/><ul><li>Windows Mixed Reality 耳機平臺次要修正。</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 2019 年 6 月 24 日      | 與 Windows 10 版本1809和更新版本相容。<br/><ul><li>Windows Mixed Reality 耳機平臺和休眠的電腦和電源狀態轉換的可靠性改進。</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 2019 年 5 月 1 日      | 與 Windows 10 版本1809和更新版本相容。<br/><ul><li>包含 2017 Acer、Asus、Dell、Fujitsu、HP、聯想和 Medion Windows Mixed Reality 耳機的固件更新。 此固件更新透過特定圖形介面卡或圖形驅動程式來改善耳機顯示相容性和可靠性。</li><li>Windows Mixed Reality 耳機平臺和可靠性改進</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10，版本 1803 (2018 年4月更新) 和版本 1809 (10 月2018更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2019年1月2日      | 與 Windows 10、1803版和更新版本相容。<br/><ul><li>耳機追蹤抖動和斷斷續續修正</li><li>先出模式可靠性修正</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 2018年10月1日      | Windows 10 版本1809之驅動程式的初始公開版本。<br/>與 Windows 10、1803版和更新版本相容。<br/><ul><li>在 Windows 10 版本1809中啟用新的 Windows Mixed Reality 功能，例如 [下] 模式</li><li>耳機追蹤和可靠性改進</li><li>移動控制器追蹤和效能改善</li><li>USB 效能和改進</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 2018 年 4 月 27 日      | Windows 10 之驅動程式的初始公開版本，版本1803<br/> <ul><li>耳機追蹤和可靠性改進</li><li>移動控制器追蹤和效能改善</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10，1709版 (秋季建立者更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 2018年2月6日    | <ul><li>3Glasses Blubur S2 Mixed Reality 耳機的官方支援</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 2017 年 12 月 19 日   | <ul><li>解決某些電腦上導致 *發生錯誤的錯誤代碼* 2181038087-7 的隱藏問題</li><li>各種穩定性與可靠性修正</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 2017 年 12 月 5 日    | <ul><li>改進耳機追蹤</li><li>移動控制器的觸控板回應性改進</li><li>解決驅動程式安裝有時會失敗的問題</li><li>各種穩定性與可靠性修正</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 2017年11月21日   | <ul><li>解決導致耳機顯示器的問題，在使用時有時會呈黑色</li><li>解決有時候會導致移動控制器消失的問題</li><li>Dell 面板耳機的狀態感應器效能改進</li><li>各種穩定性與可靠性修正</li></ul> |
   | 10.0.16299.1036  | 2017年11月7日    | <ul><li>移動控制器擲回技師修理改進：<ul><li>當位置精確度為近似值時，現在會正確回報速度，因此您現在可以在您的頭部背後擲出！</li><li>您可以在 [此處](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)的 "ThrowingStarter" unity 套件中找到擲回的範例程式碼。 開啟擲回的場景以開始使用</li></ul></li><li>改進的移動控制器電池報告</li><li>各種穩定性與可靠性修正</li></ul> |
   | 10.0.16299.1012  | 2017 年 10 月 17 日    | 驅動程式的初始公開版本                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>混合現實移動控制器模型驅動程式發行歷程記錄 ###

此驅動程式也會透過 Windows Update 自動下載並安裝，但會以內嵌方式提供下載連結：

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10，2004版 (可能有2020更新) 

| 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 2020年9月16日      | 新 HP 運動控制器之驅動程式的初始公開版本。 與 Windows 10、1903版和更新版本相容。 此驅動程式僅與新的 HP 運動控制器相容。  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10，版本 1803 (2018 年4月更新) 和版本 1809 (10 月2018更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 2018年10月1日      | Windows 10 版本1809之驅動程式的初始公開版本。 與 Windows 10、1803版和更新版本相容。  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 2018 年 4 月 17 日      | Windows 10 版本1803的驅動程式初始公開版本。  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10，1709版 (秋季建立者更新)  ####

   | 版本          | 發行日期          | 重大變更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 2017 年 10 月 17 日    | 驅動程式的初始公開版本                          |

### <a name="mixed-reality-portal-release-history"></a>混合實境入口發行歷程記錄 ###

在 Windows 10 版本1809和更新版本中，[混合實境入口](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)會透過 Microsoft Store 應用程式更新。

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10 版本1809和更新版本 ####

   | 版本            | 發行日期          | 重大變更                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 2021年6月8日          | <ul><li>將疑難排解連結新增至一般耳機錯誤的取得協助應用程式。</li><li>解決在初始安裝期間可能略過耳機裝置附屬應用程式的問題。</li><li>使用高解析度耳機的額外資訊來更新 [系統需求] 頁面。</li><li>以新的視覺效果更新啟動顯示畫面和登陸頁面。</li></ul>  |
   | 2000.21041.1051.0  | 2021年4月26日        | <ul><li>更新混合實境入口的應用程式圖示。</li></ul>  |
   | 2000.20111.1381.0  | 2020年12月10日     | <ul><li>更新混合實境入口的登陸頁面。</li><li>減少在固件更新期間的耳機連接錯誤。 </li></ul>  |
   | 2000.20071.1133.0  | 2020 年 8 月 5 日        | <ul><li>支援 [OpenXR](/windows/mixed-reality/openxr) 以暫停預覽視窗。</li></ul>  | 
   | 2000.20041.1212.0  | 2020 年 5 月 11 日          | <ul><li>解決造成不一致15-5 錯誤的計時問題。</li><li>改進了執行 Windows Mixed Reality 且沒有網際網路連線的支援。</li><li>改善透過 **安裝控制器** 配對動作控制器的支援。</li></ul>  | 
   | 2000.20031.1202.0  | 2020 年 4 月 14 日        | <ul><li>支援註冊 Windows Mixed Reality 的相關資訊、秘訣和優惠。</li></ul>  | 
   | 2000.20011.1312.0  | 2020 年 2 月 11 日     | <ul><li>針對在2019年5月更新的裝置上使用 [OpenXR](/windows/mixed-reality/openxr) 改善應用程式的支援。</li><li>解決存取範圍和鍵盤焦點問題</li></ul>  | 
   | 2000.19101.1211.0  | 2019年11月11日     | <ul><li>解決防止您切換房間界限視覺效果的問題。</li><li>解決防止您在房間界限設定期間將耳機置中的問題。</li></ul>  | 
   | 2000.19081.1301.0  | 2019 年 9 月 23 日    | <ul><li>解決耳機有硬體問題的問題顯示錯誤訊息。 在先前的版本上收到1-4 錯誤碼的使用者，現在可能會收到更明確的裝置狀態錯誤碼。</li></ul>  |
   | 2000.19071.1302.0  | 2019 年 8 月 13 日     | <ul><li>支援在5月2019更新的裝置上使用 [OpenXR](/windows/mixed-reality/openxr) 的應用程式。</li></ul>  | 
   | 2000.19061.1011.0  | 2019 年 7 月 16 日         | <ul><li>支援自訂應用程式行為的 JSON 設定選項。 在安裝時閱讀更多[Windows Mixed Reality 的位置型娛樂](/windows/mixed-reality/location-based-experiences#setup)。</li></ul>  | 

### <a name="steamvr-release-history"></a>SteamVR 發行歷程記錄 ###

您可以在這裡找到閥門的 SteamVR 版本資訊： [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>SteamVR 發行歷程記錄的 Windows Mixed Reality ###

您可以在這裡找到 SteamVR 元件 Windows Mixed Reality 的版本資訊：[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
