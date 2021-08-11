---
title: 版本資訊 - 2018 年 10 月
description: 隨時掌握 HoloLens 的最新版本，並 Windows Mixed Reality Windows 10 十月 2018/RS5 Update 的版本資訊。
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: 版本資訊、版本、windows 10、組建、rs5、os
ms.openlocfilehash: e046025ff4952a6e8779545374ec59d9f49c907ad3174b188474ae040cb28ac7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219964"
---
# <a name="release-notes---october-2018"></a>版本資訊 - 2018 年 10 月

**[Windows 10 2018 年10月更新](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (也稱為 RS5) 包含 HoloLens 的新功能，以及連接到電腦的 Windows Mixed Reality 沉浸式耳機。 

若要更新至 HoloLens 或 PC 上的最新版本 (以 Windows Mixed Reality 沉浸式 (VR) 耳機) ，請開啟 **設定** 應用程式，移至 [**更新 & 安全性**]，然後選取 [**檢查更新**] 按鈕。 在 Windows 10 的電腦上，您也可以使用[Windows 媒體建立工具](https://www.microsoft.com/software-download/windows10)手動安裝 Windows 10 2018 年10月更新。

**Desktop 的最新版本：** Windows 10 2018 年10月更新 (**10.0.17763.107**) <br>
**HoloLens 的最新版本：** Windows 10 2018 年10月更新 (**10.0.17763.134**) <br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沉浸式耳機的新功能

Windows 10 2018 年10月更新包含許多對桌上型電腦使用 Windows Mixed Reality 沉浸式 (VR) 耳機的增強功能。

### <a name="for-everyone"></a>適用于每個人

* **混合現實** 的空間-在真實世界中開啟入口網站，以找出您的鍵盤、查看附近的人，或看看您的環境，而不需要移除耳機！ 您可以藉由在移動控制器上按 Windows + 抓取，或藉由說出「開/關」來開啟 [開始] 功能表的混合現實。 將您的控制器指向您想要查看的方向，例如使用深色的明暗。

    ![混合現實](images/mr-flashlight.png)

* **新應用程式以及在混合實境首頁中啟動內容的方法**
    * 如果您使用[Windows Mixed Reality 進行 SteamVR](./using-steamvr-with-windows-mixed-reality.md)，則您的 SteamVR 標題現在會顯示在 [開始] 功能表中，而每個專案的應用程式啟動器可放置在混合實境首頁中。
    
        ![SteamVR 應用程式啟動器](images/steamvr-launchers.png)
        
    * 新的 *360* 影片應用程式，可讓您探索定期策劃的360度影片選項。
    * 新的 *WebVR 展示* 應用程式，可讓您探索定期策劃的 WebVR 體驗選擇。
    * 第一次 Windows Mixed Reality 的客戶將會進入懸崖之屋，並找出以3d 應用程式啟動器預先填入的一些來自 Microsoft Store 的最愛沉浸式應用程式和遊戲。
    * Microsoft Edge windows 現在包含 [*共用*] 按鈕。
* **快速動作功能表**-從沉浸式混合現實應用程式內，您可以按 [Windows] 按鈕來存取新的 [快速動作] 功能表，讓您輕鬆存取 *SteamVR 功能表*、*相片/影片捕獲* *、快顯和**首頁*。
* **支援背包」 pc** -Windows Mixed Reality 沉浸式 (VR) 耳機在背包」電腦上執行，而不需要在安裝程式完成後顯示模擬器。
* **新的音訊功能**-您現在可以從 Windows Mixed Reality 體驗將音訊映射鏡像至耳機中的音訊插孔 (或耳機) *，以及* 連接到電腦的音訊裝置 (如外部喇叭) 。 我們也在您的耳機顯示器中新增了音量層級的視覺指標。
* **其他改進**
    * 混合實境入口更新現在已透過 Microsoft Store 提供，可讓您在主要 Windows 版本之間更快速地更新。 請注意，這只適用于桌面應用程式，而 Windows Mixed Reality 耳機體驗仍會隨作業系統更新。 
    * 當耳機進入睡眠狀態時，會暫停 Windows Mixed Reality 的應用程式，而不是終止 (直到混合實境入口關閉) 為止。
    
### <a name="for-developers"></a>開發人員

* **[QR 代碼追蹤](/windows/mixed-reality/develop/platform-capabilities-and-apis/qr-code-tracking)**-在您的混合現實應用程式中啟用 QR 代碼追蹤，讓 Windows Mixed Reality 沉浸式 (VR) 耳機來掃描 QR 代碼，並將其回報給感興趣的應用程式。
* **適用于沉浸式應用程式的硬體 DRM 支援** -開發人員現在可以要求硬體保護的背景緩衝區紋理（如果顯示器硬體支援），讓應用程式能夠使用來自 PlayReady 等來源的硬體保護內容。
* 將 **[mixed reality capture ui 整合到沉浸式應用程式中](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)**-開發人員可以使用內建的 Windows [攝影機 capture ui](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) ，只需幾行程式碼，就能將 mixed reality capture 整合到他們的應用程式中。

## <a name="new-features-for-hololens"></a>HoloLens 的新功能

Windows 10 2018 年10月更新可供所有 HoloLens 客戶公開使用，並包含一些改良功能，例如：

### <a name="for-everyone"></a>適用于每個人

* **快速動作功能表**-從沉浸式混合現實應用程式內，您可以按 [Windows] 按鈕存取新的 [快速動作] 功能表，讓您輕鬆存取以 *開始錄製影片*、*拍攝圖片*、*混合現實首頁*、*變更音量*，以及 *連線*。
* **從 [開始] 或 [快速動作] 功能表啟動/停止影片捕獲**-如果您從 [開始] 功能表或 [快速動作] 功能表啟動 [影片捕捉]，就可以從相同的位置停止錄製。  (別忘了，您也可以使用語音命令來這麼做。 ) 
* **Project 已啟用 Miracast 的裝置**-如果使用已啟用 Miracast 的顯示器或介面卡，Project HoloLens 內容到鄰近的表面裝置或電視/監視器。
* **新的通知**-在 HoloLens 上查看和回應通知，就像您在電腦上所做的一樣。  
* **沉浸式混合現實應用程式中的實用覆蓋** -您現在會在使用沉浸式混合現實應用程式時看到重迭，例如鍵盤、對話方塊、檔案選擇器等。
* **磁片區變更的視覺指標**-當您使用 HoloLens 上的 [音量向上/向下] 按鈕時，您會在耳機中看到音量層級的視覺指標。
* **裝置開機的新視覺效果** -在開機過程中新增了載入指標，以提供系統正在載入的視覺效果意見反應。
* **附近的共用**-Windows 附近的共用體驗，可讓您與附近的 Windows 裝置共用捕捉。  
* **從 Microsoft Edge 共用**-Microsoft Edge 現在包含 [*共用*] 按鈕。 

### <a name="for-developers"></a>開發人員

* 將 **[mixed reality capture ui 整合到沉浸式應用程式中](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)**-開發人員可以使用內建的 Windows [攝影機 capture ui](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) ，只需幾行程式碼，就能將 mixed reality capture 整合到他們的應用程式中。

### <a name="for-commercial-customers"></a>適用于商業客戶

* **啟用安裝後** 布建-您現在可以使用設定隨時套用執行時間布建套件。
* 使用 **Azure AD 群組指派存取權**-您現在可以使用 Azure AD 群組來設定 Windows 指派的存取權，以設定單一或多應用程式 kiosk 設定。
* 登入畫面上的「其他使用者」現在可以使用 pin 登入，在 **設定檔切換** 時使用 pin 登入。 
* **透過 mdm 讀取裝置硬體資訊**-IT 系統管理員可以在其 MDM 主控台中依裝置序號查看和追蹤 HoloLens。
* **透過 mdm 設定 HoloLens 裝置名稱 (重新命名)** -IT 系統管理員可以在其 MDM 主控台中查看及重新命名 HoloLens 裝置。

### <a name="for-international-customers"></a>適用于國際客戶

您現在可以搭配使用 HoloLens 與當地語系化的中文或日文的使用者介面，包括當地語系化的拼音鍵盤、聽寫、文字轉換語音 (TTS) 和語音命令。

## <a name="known-issues"></a>已知問題

我們努力提供絕佳的 Windows Mixed Reality 經驗，但仍在追蹤一些已知問題。 如果您發現其他人，請 [提供意見反應給我們](/windows/mixed-reality/give-us-feedback)。

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>更新之後
在 HoloLens 上使用 Windows 10 2018 年10月更新時，您可能會注意到下列問題：
* **從通知啟動時，應用程式可能會以登入迴圈的方式結束** –某些需要登入的應用程式在從通知啟動時，可能會在無限的登入迴圈中完成。 例如，從 Microsoft Store 安裝 Microsoft 公司入口網站應用程式之後，就會發生這種情況，並從安裝完成通知啟動它。
* **應用程式登入頁面可以用空白頁面完成** -在某些情況下，登入提示會顯示在您的應用程式上。完成後，登入頁面不會關閉，而會顯示空白的 (黑色) 頁面。 您可以關閉空白頁面，或移動它以找出下方的應用程式。 例如，在 MDM 註冊期間從設定應用程式進行登入時，可能會發生這種情況。 

## <a name="provide-feedback-and-report-issues"></a>提供意見反應和報告問題

請[在您的 HoloLens 或 Windows 10 電腦上使用意見反應中樞應用程式](/windows/mixed-reality/give-us-feedback)，以提供意見反應和報告問題。 使用意見反應中樞可確保包含所有必要的診斷資訊，以協助我們的工程師快速地偵測和解決問題。

>[!NOTE]
>請務必接受提示，詢問您是否要意見反應中樞存取您的 [檔] 資料夾， (在出現提示時選取 **[是]**) 。

## <a name="prior-release-notes"></a>先前的版本資訊

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