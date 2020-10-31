---
title: 移動控制器常見問題
description: 控制器 Windows Mixed Reality 的疑難排解超出標準取用者支援檔。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、說明、支援、動作控制器
appliesto:
- Windows 10
ms.openlocfilehash: 7d3cdae2e098504a755369e3c829c1d4a6142b9d
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132022"
---
# <a name="motion-controller-faqs"></a>移動控制器常見問題

## <a name="what-do-the-vibrations-and-lights-mean"></a>振動和燈光代表什麼意思

LED constellation 環形和 haptics 指出移動控制器的狀態。

| 狀態    | 與狀態相關聯的行為 | 如何進入/離開狀態 |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **開啟電源**               | Led 會開啟和控制器震動一次。 | 按住控制器上的 Windows 按鈕兩秒，以開啟控制器。  |
| **關閉電源**              |  Led 關閉和控制器震動兩次。 | 按住控制器上的 Windows 按鈕四秒，關閉控制器。   |
| **休眠中**               |  Led 會在睡眠狀態下每三秒關閉並閃爍。 | 當控制器 motionless 30 秒時，會自動進入睡眠狀態。 控制器偵測到動作時喚醒，除非裝置未與主機電腦配對。 在該情況下，按下按鈕將它喚醒。 |
| **配對**                |  當配對模式時，Led 會慢慢地進入脈衝狀態，並在結束配對模式時進入穩固。 如果配對成功，則控制器會震動一次，如果配對失敗，則會出現三次，但不成功。 | 按下並按住電池內的配對按鈕三秒鐘。     |
| **控制器連接/中斷與電腦的連線** |  控制器會在電腦連線或中斷連接時震動一次。 | 當控制器開啟電源之後，或在使用時，如果控制器與電腦中斷連線，就會發生這種情況。|
| **電力偏低等級**      | 當電池偏低 (不會) LED 指示時，會停用 Haptics。 當電池計量偏低時，耳機中控制器把手上的電池指示器圖示會顯示 1/4 full。 | 更換您的電池。 | 
| **電力不足等級** |  當您開啟控制器時，控制器會震動三次，然後自動關閉。 電池指示器圖示將會變成紅色。 | 更換電池。 如果問題持續發生，請將 [裝置還原為其原廠設定](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>我的動作控制器無法正常運作

如果您的 [動作控制器](controllers-in-wmr.md) 沒有作用、未連線，或是當您戴耳機時看不到控制器的影像，請嘗試下列動作：

1. 請確定您的控制器已開啟。 若要開啟它們，請按住 Windows 按鈕兩秒鐘。
2. 請確定控制器是完全收費的，如果不是，則更換電池。
3. 將控制器放在您面前之前，請關閉並重新開啟控制器。 按住 [Windows] 按鈕四秒鐘以關閉控制器，然後再按一次再按住兩秒鐘來開啟。
4. 檢查是否已 [正確配對](controllers-in-wmr.md#pair-motion-controllers)您的運動控制器。
5. 檢查動作控制器 Led：已配對並連接明亮的控制器，dimly 亮控制器未連線。
6. 移至 [ **開始] > 混合實境入口** 在您的電腦上，然後選取 [功能表]。 您應該會看到已列出您的動作控制器，以及狀態訊息：
    * 就緒–控制器全都已設定。
    * 遺失追蹤–混合實境入口找不到您的控制器。 將它們放在您的耳機前方，然後按下 [Windows] 按鈕四秒再重新開機，然後再按兩秒鐘。
    * 電力偏低–更換控制器電池。
7. 如果您使用的是外部 USB 藍牙介面卡，請確定它已插入 USB 2.0 埠， (通常不一定是黑色) 。 您也應該盡可能從任何其他無線發送器或 USB 快閃磁片磁碟機插入，包括耳機的 USB 連接器。 
8. 若要確認電腦上只有一個藍牙無線電，請移至 **裝置管理員 > 藍牙** ，並尋找一個介面卡。 如果您使用具有內建無線電的桌上型電腦設定，請檢查是否已連接外部天線。 如果沒有連線的外部天線，可能會導致追蹤問題。 或使用外部藍牙轉換器 (USB) 、停用內部藍牙功能，然後重試配對和連接。
9. 如果 [藍牙設定] 視窗在背景中開啟，則會對藍牙通訊協定進行許多額外的呼叫。 將它關閉。
10. 藉由在混合現實中開啟控制器來查看電池圖示，檢查移動控制器上的虛擬電池音量。 請等候約15秒再讀取層級，因為報告的層級高於連接控制器後立即的實際層級。 如果圖示為紅色，則更換電池。
11. 在 [設定] > 裝置中移除藍牙耳機和喇叭 **> 藍牙 & 其他裝置** ，然後關閉裝置。 在您的混合現實耳機上使用耳機插口或內建喇叭，以獲得最佳的音訊體驗。
12. 移除其他可能與您的電腦配對的藍牙裝置，例如耳機或 gamepads。 移至 [ **設定] > 裝置 > 藍牙 & 其他裝置** ，選取裝置，然後選取 [移除裝置]。
13. 拔掉耳機上的 USB 纜線，然後將它插回電腦以重新開機 Windows Mixed Reality。
14. 控制器燈在進行固件更新時閃爍。 等候更新完成，控制器應該會出現在混合的現實中。
15. 確定您的電腦已連線到 5GHz Wi-Fi 網路。 如果您的膝上型電腦連線到 2.4 GHz Wifi 網路，通常會共用藍牙連線。 這可能會對 Wifi 或藍牙效能造成負面影響，視產品設計而定。 在網路介面卡設定中，將慣用的頻外變更為5GHz。 如果您的網路不支援5GHz，則可以使用藍牙轉換器，而不是使用內部藍牙功能。
16. 如果您的藍牙設定已經配對，除非已將新的裝置移除，否則除非已使用特定的轉換器新增裝置，否則 Windows 將不會探索新裝置 (如果已使用特定的轉換器來新增裝置，則只能將其與該轉換器) 移除。
17. 如果您的電腦已內建藍牙，且您遇到連線問題，請嘗試使用 USB 藍牙介面卡。 若要這樣做，請關閉裝置管理員中的內建藍牙無線電，然後將其他 Bluetooth 裝置與新的介面卡配對。

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>我的控制器抖動、停滯或閃爍，並且在混合現實中消失

* 如果您的電腦是在 2.4 GHz wifi 上執行，請切換至 5 GHz wifi。 
* 如果您使用的是外部藍牙介面卡，請確定它已插入 USB 2.0 埠 (通常（但不一定）是黑色) ，而不是其他無線發送器或 USB 快閃磁片磁碟機。
* 在 [設定] 中執行藍牙疑難排解員 **> 更新 & 安全性 > 疑難排解 > 藍牙** 。

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>我的控制器停滯于無限重新開機

這是很重要的電池指標。 將新電池放在裝置中，如果問題持續發生，請將 [控制器重設為原廠設定](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)。

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>混合實境入口可正常運作，但我的控制器追蹤不佳 (飛出、搖動等等。 ) 

1. 燈光條件可能會影響追蹤。 請確定您不會暴露在直接照明的情況下，而且您的 (HMD 不會看到很多的點光源，例如，像是耶誕節樹狀結構的燈等字串) 。
2. 這些徵兆通常是因為控制器與主機電腦之間的通訊失敗，並指出藍牙連結品質不佳。 查看 [藍牙的相關問題](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>移動控制器 Led 不亮，但按鈕和操縱杆仍能在混合實境入口

移動控制器校正快取可能已損毀。 若要刪除快取，請在系統管理員命令提示字元中執行下列命令：

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

此資料夾無法在 Windows 檔案總管中存取，而且只能從系統管理員命令提示字元修改。 刪除資料夾之後，請重新開機您的電腦，然後重新連接您的動作控制器來還原校正檔案。

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>我的控制器看起來像是 Vive/Oculus，有奇怪的方向，或按鈕的對應不正確

網站可能沒有完整的移動控制器支援。

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>我的動畫控制器未出現在 SteamVR apps 和遊戲中

首先，請確定您的控制器電池已收費。 如果電池沒有作用或定生死，控制器將無法運作

如果您可以在懸崖之屋中看到您的控制器，但不在 SteamVR 應用程式和遊戲中，則可能無法正確安裝移動控制器模型驅動程式。 若要檢查是否已正確安裝移動控制器模型驅動程式：

1. 開啟這兩個動作控制器。 檢查是否已 [正確配對](controllers-in-wmr.md#pair-motion-controllers)您的運動控制器。
2. 移至 **裝置管理員 > 藍牙** ，並尋找「移動控制器」。
3. 選取裝置，然後移至 [ **依連接查看 > 裝置** ]。
4. 移至 [ **系統設定] > 裝置 > 藍牙 & 其他裝置 > 其他裝置** 以查看是否可見。 將會有兩個「Bluetooth HID 裝置」裝置，而且在每個藍牙隱藏裝置下都應該是名為「移動控制器」的裝置 (，並在與運動控制器相同的節點中) 灰色圖示。
5. 按兩下每個「移動控制器」裝置，然後移至 [驅動程式] 索引標籤。確認列出的驅動程式版本對應到其中一個 [版本](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history)。
6. 如果不是，請執行 Windows Update，這會自動下載並安裝驅動程式。 如果您是在具有企業原則的電腦上，或者如果 Windows Update 其他限制，則可能需要手動安裝動作控制器模型驅動程式。 若要這樣做，請造訪 [此頁面](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) ，並尋找與您的 Windows 10 版本對應的驅動程式版本。 您可以從下載頁面取得安裝指示。

## <a name="the-controller-firmware-update-takes-significantly-longer-than-two-minutes"></a>控制器固件更新花費的時間明顯超過兩分鐘

查看 [ [藍牙問題] 區段](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。 藍牙連結品質不佳通常會造成這些問題。

## <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>我剛剛插入了新電池，但控制器虛擬電池等級未指出完整層級

移動控制器電池音量已針對 AA 電池調整。 某些低電壓充電電池可能不會報告為已滿，但已完全收費。

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>我的 Samsung 移動控制器的觸控板已置中或有不正確位置

這可能是硬體瑕疵，您應回到零售商或設備製造商，以進行更換或交換。

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>如何將控制器還原為原廠設定

將它還原至原廠條件 (您將需要全新的電池) ：

1. 拔掉控制器電源並關閉電源。
2. 開啟電池蓋。
3. 插入新的電池。
4. 按住 [配對] 按鈕 (電池) 下底部的索引標籤。
5. 按住 [配對] 按鈕時，按住 [Windows] 按鈕五秒，即可開啟控制器電源， (保持兩個按鈕) 。
6. 釋放按鈕，並等候控制器開啟電源。 這最多需要15秒的時間，而且在裝置復原發生時不會有任何指標。 如果裝置在按鈕發行時立即開啟電源，修復按鈕序列就不會註冊，您必須再試一次。
7. 如果控制器已與您的電腦配對，請移至 [ **設定] > 藍牙 > 其他裝置** ]，然後選取 [移動控制器] 和 [移除裝置]，以從藍牙設定移除控制器關聯。
8. 再次將控制器與耳機或電腦[配對](controllers-in-wmr.md#pair-motion-controllers)。
9. 連接主機和耳機之後，裝置將會更新至最新的可用固件。

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>我可以將 Xbox 控制器與我的電腦配對，讓我可以在耳機中使用它

您可以依照下列 [指示](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)，將藍牙 Xbox 控制器與耳機搭配使用。

如果您有有線 Xbox 控制器，請將它插入您的電腦。

有些遊戲和應用程式使用 Xbox 控制器的方式不同于混合現實的使用方式。 若要在遊戲或應用程式中使用控制器，請在應用程式行上選取 [作為遊戲台]，或說「作為遊戲台」。 若要將控制器切換回混合的實際情況，請再次選取 [使用遊戲台]，或說「使用的是注視」。 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>如果電腦上已設定 Windows Mixed Reality，如何? 配對新的控制器

如果您要將控制器與耳機配對，請使用隨附的應用程式 ([混合實境入口](install-windows-mixed-reality.md#launch-mixed-reality-portal) 可協助您尋找隨附的應用程式來啟動，或提供您可以從) 中選取的隨附應用程式清單。

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>如何將控制器傳回到其原廠配對

若要將移動控制器歸還給站配對，或將它們與內建藍牙無線電的 Windows Mixed Reality 耳機配對，請執行耳機的裝置附屬應用程式 (例如，"Acer OJO 500" 應用程式或 "Samsung HMD 電影對白 + Setup" 應用程式，會在首次耳機插入) 時自動安裝，並遵循行動電話控制器配對的指示。

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>我的動畫控制器未配對到我的電腦

* 如果控制器未開啟，請插入新的電池。 如果這不會修正此問題，請在按住配對按鈕時開啟裝置，以將裝置還原為其原廠設定。 如需詳細資訊，請參閱 [裝置復原步驟](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) 。
* 如果控制器開啟，而您使用的是外部藍牙介面卡，請確定介面卡已插入 USB 2.0 埠， (通常（但不一定是黑色) ）離開其他無線發送器或 USB 快閃磁片磁碟機。 如果仍然無法運作，請在 [設定] 中執行藍牙疑難排解員 > 更新 & 安全性 > 疑難排解 > 藍牙。
* 如果您使用的是 Qualcomm 介面卡，而電腦剛剛損毀，請重新開機電腦。
* 請嘗試重新開機不配對的移動控制器（一次一個），然後重新開機電腦。
* 移動控制器快取可能已損毀。 若要修正此問題，請參閱下列 [步驟](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)。
* 如果這些步驟都無法解決問題，您應該洽詢製造商。

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>我的配對控制器不會顯示在混合實境入口

* 將控制器放在您的耳機前方，然後按下 [Windows] 按鈕四秒再重新開機，然後再按兩秒鐘。
* 如果您的控制器顯示為已連線，請將它們，然後再次執行 [配對](controllers-in-wmr.md#pair-motion-controllers) 程式。
* 如果控制器 Led 正在迴圈中，一次開啟一個光線象限，然後將它們關閉，則會進行固件更新。 等候更新完成，控制器應該會出現在混合的現實中。
* 如果使用外部藍牙介面卡，請確定介面卡已插入 USB 2.0 埠 (通常是黑色) ，而不是其他無線發送器或 USB 3.0 裝置。
* 如果電腦剛剛損毀，且正在使用 Qualcomm 介面卡，則重設可能無法運作。 若要修正此問題，請從電腦背面拔下電源 (或者，如果是在膝上型電腦上，請按住電源按鈕10秒) 然後重新開機電腦。
* 在 [設定] 中執行藍牙疑難排解員 **> 更新 & 安全性 > 疑難排解 > 藍牙** 。  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>我正在嘗試配對控制器，但它們永遠不會顯示在 [藍牙設定] 的 [新增裝置] 功能表中

檢查您是否已有未配對的控制器。 如果您這樣做，請將其移除，然後再試一次。 如果問題持續發生，請重新開機電腦。 如果失敗，請參閱藍牙的詳細 [資訊](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。

注意：如果另一組移動控制器與您的電腦配對，您必須先將這些控制器，然後再配對新的控制器。 如果您將一組運動控制器與您目前的電腦配對，然後將它們與第二部電腦配對，您必須先將並重新配對，才能再次使用電腦。

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>如何得知我是否使用藍牙技術

移動控制器使用許多消費者裝置中的相同藍牙技術，其設計目的是要與任何最近的電腦上所包含的藍牙功能搭配使用。 如果您的電腦通過了混合現實相容性檢查，則應該具有藍牙無線電。 若要確認：

* 開啟 [裝置管理員]。
* 展開 [藍牙] 區段，並尋找介面卡。

![範例裝置管理員的螢幕擷取畫面。 介面卡是藍牙無線電。](images/devicemanagerbtadapterpic.png)

如果您的電腦沒有藍牙，請使用 Plugable USB 藍牙4.0 低功耗微介面卡。

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>開啟動作控制器時，Wi-Fi 在筆記本上變慢

連線至 2.4 GHz 存取點時，您的筆記本可以與藍牙共用其 Wi-Fi 天線。 如果您可以將波段喜好設定切換為5GHz，請簽入裝置管理員。 如果無法使用5GHz 網路，而且效能受到嚴重的影響，請考慮使用藍牙轉換器。

![您可以透過 [裝置管理員] 找到 Wifi 波段選項設定](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>我的電腦具有藍牙技術，但我的控制器有問題

移動控制器應該與其他 Bluetooth 鍵盤、滑鼠和遊戲控制器搭配運作，但其體驗會依您使用的鍵盤、滑鼠或遊戲控制器的模型而有所不同。 以下是您可以用來改善效能的一些事項：

* 如果您的電腦具有藍牙，但仍有行動電話控制器的問題，請考慮將您的藍牙無線電取代為插入 USB 的 Plugable 外部藍牙介面卡。 您一次只能有一個使用中的藍牙無線電配接器。 如果除了現有的無線電之外，還插在外部電臺，您必須在裝置管理員中停用現有的藍牙無線電 (以滑鼠右鍵按一下介面卡，然後選取 [停用裝置] ) 並取消配對所有先前的藍牙裝置。
* 如果您使用的是 USB Bluetooth 介面卡，請將它連接到 USB 2.0 埠 (2.0 埠通常是黑色，而且沒有標示為 "SS" ) （如果有的話）。 埠應與下列實體分開：
    - HMD USB 連接器
    - 快閃磁碟機
    - 硬碟
    - 像是鍵盤/老鼠的無線 USB 接收器，理想的情況是將 USB Bluetooth 介面卡盡可能插入電腦的相反端。
* 關閉 [藍牙設定] 視窗（如果已開啟）。 讓它在背景中保持開啟，表示會對藍牙通訊協定進行許多額外的呼叫。
* 如果您的耳機與您的電腦配對，請使用 Windows 藍牙驅動程式堆疊，並不要安裝任何協力廠商藍牙驅動程式堆疊。 協力廠商軟體可能無法正常運作。
* 停用 [藍牙 & 其他裝置] 下的 [使用迅速配對顯示通知] 設定，以減少主機無線電掃描活動。
* 如果您使用的是內部藍牙卡，請確定您使用的是外部藍牙天線，否則可能會遇到追蹤問題。 如果無法運作，請在停用內部藍牙之後，使用外部藍牙轉換器 (USB) 。
* 裝置應該會出現在 [藍牙設定] 的 [滑鼠、鍵盤 & 畫筆] 類別之下。 如果它在 [其他裝置] 下，則將並配對裝置。
* 移除、將和關閉 Bluetooth 耳機和喇叭。 Windows Mixed Reality 不支援這些。 在您的混合現實耳機上使用耳機插口或內建喇叭，以獲得最佳的音訊體驗。

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>我的第二個控制器需要很長的時間才能重新連線

當移動控制器同時開啟時，某些較舊的 Intel 無線電波會遇到此問題。 避免同時開啟控制器。

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>我的 Qualcomm 藍牙無線電無法在電腦損毀之後配對控制器

Qualcomm (QCA) 之前的藍牙無線電驅動程式在 Windows 損毀之後可能會處於不良狀態。 完全關閉電腦的電源來解決這個問題。

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>我在使用 Marvell 無線電時遇到不良的控制器追蹤

移至 **裝置管理員 > 藍牙 > MARVELL AVASTAR 藍牙無線電介面卡 > 屬性 > 驅動程式** ，並確定您使用的是驅動程式15.68.9210.47 或更新版本。
