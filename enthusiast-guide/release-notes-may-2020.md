---
title: 版本資訊-2020 年5月
description: 隨時掌握最新的 Windows Mixed Reality 版本資訊，以取得 Windows 10 的2020更新。
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: 版本資訊、版本、windows 10、組建、19h1、os、5月2020
ms.openlocfilehash: 462fcbfa10cfff8df23c970fd54ee0754a4d9472
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439159"
---
# <a name="windows-10-release-notes---may-2020"></a>Windows 10 版本資訊-5 月2020

**Windows 10 5 月2020更新 (v2004)** 包含 Windows Mixed Reality (VR) 耳機的新功能，例如在混合實境首頁中啟動 Win32 應用程式的能力。 HoloLens (第1代) 長期維護 (LTS) ，每月發行服務更新。

升級至 Windows Mixed Reality 沉浸式 (VR) 耳機的最新電腦版本、開啟 **設定 > 更新 & 安全性**，然後選取 [**檢查更新**]。 在 Windows 10 的電腦上，您也可以使用 [Windows 媒體建立工具](https://www.microsoft.com/software-download/windows10)，以手動方式安裝 **Windows 10 2020 更新**。

**Desktop 的最新版本**： Windows 10 v2004 (10.0.19041.264) 

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沉浸式耳機的更新

### <a name="introducing-the-new-microsoft-edge"></a>新 Microsoft Edge 簡介

如[先前所宣佈](/windows/mixed-reality/new-microsoft-edge)，我們已使用 Windows Mixed Reality 中的新 Microsoft Edge 瀏覽器進行更新，以提供更好的支援。 新的 Microsoft Edge 採用 Chromium 的開放原始碼專案，為客戶建立更好的 web 相容性，並為所有 網頁程式開發人員建立較少的 web 片段。 它也支援 WebXR，這是用來建立適用于 VR 耳機之沉浸式 web 體驗的新標準，取代 WebVR。

### <a name="improved-settings-for-wmr"></a>改善 WMR 的設定

感謝您的意見反應，我們已新增並闡明耳機顯示頁面上的設定：

* **我的家用的視覺品質** 變更這些設定只會影響 (懸崖之屋和 Skyloft) 的混合實境首頁環境：

* **調整混合實境首頁中的詳細資料層級和效果品質** -這會變更我們在家裡使用的部分轉譯。 尤其是，不同材質的視覺品質 (木頭、具體等等) 將會隨著您將此設定從低變更為高而調整。

* **變更應用程式視窗解析度** -根據預設，在首頁中啟動的大部分2d 視窗都會以 720-p 解析度啟動。 雖然您可以手動手動調整它們的大小 &，您也可以選擇讓它們全都以1080p 的方式啟動。 先前，此選項是以視覺品質 (搶鮮版（Beta）) 選項的形式提供。 我們已適當地將它分割為個別設定。

* **體驗選項** -這些選項會調整混合現實體驗，以降低硬體可能難以跟上不受限制 90 fps 的系統負載。 您可以明確地啟用或停用這些額外的設定，或選擇 [Let Windows 決定]，並讓啟發學習法繼續決定何時要切換這些設定。

* **解決方案** -如果您有高解析度耳機（如 HP 的回音），我們支援以原生解析度執行，或基於效能考慮減少解析度。 先前的耳機（像是 Samsung 電影對白和電影對白 +）只支援單一解析度，因此您無法在那些耳機上變更此設定。

* **畫面播放速率**-您現在可以手動設定耳機顯示器的畫面播放速率，或繼續讓 Windows 使用其啟發學習法來判斷 60 hz 或 90 Hz 是否更適合。

* **校正** -如同之前，如果您的耳機支援，您可以調整 IPD (interpupillary 距離) 。

* **輸入切換** -切換輸入焦點切換 (Win + Y) 行為，根據狀態感應器回饋) 或手動 (自動。

### <a name="new-cortana-app"></a>新增 Cortana 應用程式

Windows 的這項更新包含最新版本的 Cortana 應用程式（目前僅限英文），不再支援特定的混合現實特定命令，例如「拍攝相片」和「拍攝影片」。 您可以使用新的 Cortana 來啟動應用程式，而且它也支援以生產力為焦點的新命令，例如「我的下一個會議是什麼時候」。 或「傳送電子郵件給 \< name \> 我遲到的時候。」
    
### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>19041.546 2020 年10月10日發行 (推出的其他更新) 

此桌面每月服務更新包括下列 Windows Mixed Reality 裝置的變更： 
* 減少 Windows Mixed Reality 前端掛載顯示器 (HMD) 的扭曲和 aberrations。 
* 新增即將推出之 HP Windows Mixed Reality 移動控制器的支援。 
* 將 Windows Mixed Reality 中的 90-Hz 重新整理頻率設定的行為變更為，在無法達到 90 Hz 的特定情況下，不會再自動切換回 60 Hz。 

### <a name="help-us-improve"></a>協助我們改進！

我們會持續尋找改善相容性。  如果您認為慣用的傳統 Win32 應用程式在 Windows Mixed Reality 時無法正常運作，請透過我們的[意見反應中樞](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)提交意見反應。

## <a name="prior-release-notes"></a>先前的版本資訊

* [版本資訊-2019 年5月](release-notes-may-2019.md)
* [版本資訊 - 2018 年 10 月](release-notes-october-2018.md)
* [版本資訊-2018 年4月](release-notes-april-2018.md)
* [版本資訊 - 2017 年 10 月](release-notes-october-2017.md)
* [版本資訊 - 2016 年 8 月](release-notes-august-2016.md)
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [ (外部連結的沉浸式耳機支援) ](./troubleshooting-windows-mixed-reality.md)
* [HoloLens 支援 (外部連結) ](https://support.microsoft.com/products/hololens)
* [安裝工具](/windows/mixed-reality/develop/install-the-tools)
* [提供意見反應](/windows/mixed-reality/give-us-feedback)