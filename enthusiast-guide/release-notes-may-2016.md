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
# <a name="release-notes---may-2016"></a>版本資訊 - 2016 年 5 月

HoloLens 團隊致力於提供您透過 Windows 測試人員計畫的最新功能更新和主要修正。 感謝您所有的建議，我們會將您的意見反應帶給您。 繼續透過意見反應中樞、[開發人員論壇](https://forums.hololens.com) [ @HoloLens 和 Twitter ](https://twitter.com/hololens)[提供意見](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)反應給我們。

**發行版本：** Windows 全像2016更新 (**10.0.14342.1016**) 

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

若要更新為最新版本，請開啟 [ *設定* ] 應用程式，移至 [ *更新 & 安全性*]，然後選取 [ *檢查更新* ] 按鈕。

## <a name="new-features"></a>新功能

* 您現在可以 **在 2d view 中同時執行最多三個應用程式**，這可讓您在 HoloLens 中進行多工處理的無限使用案例。 在探索此航班上的新功能時，讓新的意見反應中樞探索」開啟清單。

  ![HoloLens 可以同時執行三個應用程式](images/img-3625-400px.jpg)<br>
  同時在 2D view 中執行最多三個應用程式

* 我們新增了 **語音命令**：
   * 請嘗試查看全像，然後說「臉部我」來旋轉
   * 藉由說出「更大」或「較小」來變更其大小
   * 藉由說出「嗨 Cortana，將 *應用程式名稱* 移至這裡」來移動應用程式。
* 我們已 **在 HoloLens 上更輕鬆地進行開發**。 您現在可以透過 [Windows 裝置入口網站](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)流覽、上傳和下載檔案。 您可以透過 Visual Studio，存取您側載或部署之任何應用程式的 [檔] 資料夾、[圖片] 資料夾和本機儲存體。
* **模擬器現在支援使用 Microsoft 帳戶進行登入**，就像您在實際 HoloLens 上的方式一樣，您可以從 [其他工具] 功能表的 [>>] 啟用。
* **2D 應用程式現在會在監看影片全螢幕時隱藏應用程式列和游標** ，以避免干擾。 您的影片監看體驗在 HoloLens 上將會更有樂趣。
* 您也可以在 **沒有應用程式行的情況下釘選相片** 。

  ![您可以針對2D 應用程式（例如相片）隱藏應用程式行](images/img-3626-400px.jpg)<br>
  應用程式行可以針對具有2D 視圖的應用程式隱藏，例如相片

* 檔案 **選擇器** 的運作方式就像您在 HoloLens 上所預期的一樣。
* 已更新 **Edge 瀏覽器** ，以使用桌上型電腦和手機來對應整合使用者體驗。 我們啟用了多個瀏覽器實例、自訂 HoloLens 新索引標籤頁面、索引標籤查看，以及在新視窗中開啟，以及 power & 效能改進。
* **Groove 音樂** 應用程式現在已在 HoloLens 上。 請造訪商店進行下載，然後在背景中嘗試播放。
* 您可以輕鬆地自訂應用程式在世界中的相片順序。 只要按一下並拖曳中間垂直框線中的圓形，即可嘗試在調整模式中 **旋轉您** 的全像投影。 您可能會注意到，全像全像周 **框方塊** ，以確保最大化的互動。 您也可以將所有平面應用程式垂直調整 (但) 的相片和全像影像應用程式。

  ![將全像放在世界各地之後，可以旋轉全像影像](images/img-3627-400px.jpg)<br>
  將影像放在世界各地後旋轉

* 我們已在此航班中進行數個 **輸入改進** 。 您可以將一般藍牙滑鼠連接到 HoloLens。 Clicker 已經過微調，可讓您使用 clicker 來調整 & 移動全息的大小。 鍵盤的執行效能也比以往更好。
* 現在您可以將音量向上 + 向下音量，來取得 **混合的現實圖片** 。 您也可以將您的混合現實影片 & 影片分享至 Facebook、Twitter 和 YouTube。
* **混合現實** 影片的錄製長度上限已增加到五分鐘。
* **相片應用程式** 現在會從 OneDrive 串流影片，而不需要在播放前下載整部影片。
* 我們改進了您的全像 **是您離開的地方**。 您也會看到重新連線至 Wi-Fi 的選項，如果 HoloLens 無法偵測到您的位置，請再試一次。
* 鍵盤具有改良的版面配置，可讓您輸入具有金鑰的 **電子郵件地址** ，讓您只要按一下，就能輸入最受歡迎的電子郵件網域。
* 在 OOBE 期間讓 **應用程式註冊** 速度更快，並 **自動偵測** 時區，讓您獲得最佳的第一個使用者體驗。
* **儲存體感知** 可讓您透過 [設定] 應用程式中的系統和應用程式，來查看剩餘和使用的磁碟空間。
* 我們已將意見反應應用程式和內建整合至單一應用程式 **意見反應中樞**，這是可讓我們對您喜愛的功能 **提供意見** 反應、哪些是需要改進的功能，以及您可以執行哪些作業的工具。 當您加入測試人員計畫時，您可以趕上 **取得最新的 Insider 新聞**、 **費率組建** ，以及前往意見反應中樞的 **意見反應探索」** 。
* 我們也 [發行了更新的 HoloLens 模擬器](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools) 組建。
* 您的混合現實影片現在看起來更好，因為會有自動 **影片穩定**。

## <a name="major-fixes"></a>主要修正

我們修正了空格可能會變慢或偵測不正確的全息圖空間的問題。 我們已修正關機問題，可在關機期間繼續嘗試啟動 shell。

修正了問題
* 這會封鎖繼續 XAML 應用程式的能力。
* 發生損毀的情況下，會離開黑色畫面和一些不規則線條。
* 使用某些應用程式時，滾動有時候會有錯誤的方向。
* 電源 Led 可能指出裝置仍在開啟時的關閉狀態。
* 從待命恢復之後，WiFi 可能會關閉。
* Xbox 身分識別提供者會提供玩家代號設定，然後卡在迴圈中。
* 在 OneDrive 檔案選擇器中選取下載的檔案時，Shell 偶爾會損毀。
* 按住連結有時會開啟新的、中斷的索引標籤，並開啟內容功能表。
* windows 裝置入口網站不允許從50到80的 IPD 調整

我們修正了相片的問題，其中
* 影像偶爾會顯示旋轉，因為忽略了 [略過 EXIF 方向] 屬性。
* 它可能會在已釘選的相片上啟動時損毀。
* 影片會在暫停後重新開機，而不是從上次暫停的位置繼續進行。
* 如果共用的影片在播放時共用，可能會防止重新播放。
* 混合實境擷取錄製的開頭為 0.5-1 秒的僅限音訊摘要。
* [同步] 按鈕會在初始 OneDrive 同步處理期間消失。

我們修正了設定的問題，其中
* 當環境變更時，需要重新整理。
* 鍵盤上的「輸入」不像在某些對話方塊中按一下 [下一步]。
* clicker 無法配對時，很難得知。
* 它可能會因為 WiFi 中斷連線和連線而沒有回應。

我們修正了 Cortana 的問題，其中
* 它可能會卡在顯示接聽的 UI。
* 如果您對離開應用程式的要求回答了可能的話，請詢問「嗨 Cortana，我可以從獨佔模式應用程式取得什麼」。
* 如果您要求 Cortana 進入睡眠狀態，然後再繼續，Cortana 接聽 UI 就不會正確地繼續。
* 「我連接到什麼網路？」查詢 「我連接了嗎？」 當第一個網路設定檔案修復沒有連線能力時，可能會失敗。
* UI 旁邊在「正在接聽」上，但在結束應用程式時，會立即開始執行語音辨識。
* 當您登出 Cortana 應用程式時，不會讓您重新登入，直到重新開機為止。
* 當混合實境擷取 UI 處於作用中狀態時，它不會啟動。

我們已修正 Visual Studio 的問題，其中
* 背景工作調試無法運作。
* 圖形偵錯工具中的畫面格分析無法運作。
* HoloLens 模擬器不會出現在 Visual Studio 的下拉式清單中，除非您的專案 TargetPlatformVersion 設定為10240。

## <a name="changes-from-previous-release"></a>先前版本的變更
* Cortana 命令 **嗨 Cortana，重新開機裝置** 無法運作。 使用者可以說 **嗨 Cortana、重新開機** 或 **嗨 Cortana，重新開機裝置**。
* 已從產品中移除 Kiosk 模式。

## <a name="prior-release-notes"></a>先前的版本資訊
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>請參閱
* [HoloLens 的已知問題](https://docs.microsoft.com/windows/mixed-reality/hololens-known-issues)
* [安裝工具](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools)
* [Shell](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)
* [更新混合實境的 2D UWP 應用程式](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/building-2d-apps)
* [硬體配件](https://docs.microsoft.com/windows/mixed-reality/discover/hardware-accessories)
* [混合實境擷取](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture)
* [語音輸入](https://docs.microsoft.com/windows/mixed-reality/design/voice-input)
* [將應用程式提交到 Windows Store](https://docs.microsoft.com/windows/mixed-reality/distribute/submitting-an-app-to-the-microsoft-store)
* [使用 HoloLens 模擬器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)
