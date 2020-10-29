---
title: 使用 Windows Mixed Reality 常見問題
description: 取得使用 Windows Mixed Reality 時常見問題的解答。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，意見反應，意見反應中樞，bug
appliesto:
- Windows 10
ms.openlocfilehash: 62b6b61f74abfd77ba61563639ff719576551f07
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680236"
---
# <a name="using-windows-mixed-reality-faq"></a>使用 Windows Mixed Reality 常見問題

如果您在使用 Windows Mixed Reality 沉浸式耳機時需要協助，請參閱這些主題以取得一般資訊和疑難排解。

是否仍需要協助？ 如需 advanced 疑難排解的詳細說明，請參閱這篇文章。

## <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>我看到一則訊息，指出「遺失追蹤」或「我們沒有這個空間的界限」。

選取您桌面上的 [ **開始] > 混合實境入口** 。 選取 [ **功能表** ]，然後選取 [ **執行安裝程式** ] 以建立新的界限。 Windows Mixed Reality 支援多個位置，而且只要房間未大幅變更，就會識別您在啟動時所處的空間。  


## <a name="i-cant-hear-any-sound-or-the-sound-is-coming-from-my-computer-instead-of-my-headset"></a>我聽不到任何聲音，或音效來自我的電腦而不是我的耳機

如果您的沉浸式耳機未包含內建耳機，您必須將耳機連接到耳機上的音訊插孔。  (的插座通常位於耳機面板或鏡頭的後方;如果找不到您的耳機製造商，請洽詢。 )  

有些音訊耳機具有可控制音量的實體按鈕。 如果音訊無法運作，請檢查磁片區是否已關閉或靜音。

Windows Mixed Reality 是設計用來在您的沉浸式耳機上播放音效，並將其連接到耳機。 當您將耳機移開或翻轉面板時，音訊將切換至您的預設 Windows 播放裝置。 您可以在 [ **設定 > 混合現實 > 音訊和語音** ] 中變更此設定。

> [!NOTE]
> * Windows Mixed Reality 空間音訊最適合搭配內建或直接連線到您的沉浸式耳機的耳機。 連接到電腦的電腦喇叭或耳機可能無法正常適用于空間音訊。
> * Windows Mixed Reality 不支援藍牙音訊耳機。

## <a name="speech-commands-arent-working"></a>語音命令無法運作

若要使用語音命令，您電腦的語音和語言設定必須設定為 [支援的 Windows Mixed Reality 區域和語言](wmr-setup-faq.md#what-languages-are-supported-in-windows-mixed-reality)。 若要檢查您的 Windows 區域和語言，請選取 [ **設定 > 時間] & 語言 > 區域 & 語言** 。 若要檢查您的語音語言，請選取 [ **設定] > 時間 & 語言 > 語音** ]。

如果您的耳機沒有內建的 mic，請使用 mic 連接耳機或您的電腦。 當耳機直接連接到耳機時，若要自動將 mic 輸入切換到耳機，請選取 [ **設定] > 混合現實 > 音訊和語音** ，並確定 **當我磨損耳機時，切換到耳機 mic** 已開啟。

有些音訊耳機具有實體按鈕，可將麥克風靜音和取消靜音。 如果語音命令無法運作，請檢查您的 mic 是否已靜音。

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>界限一律可見。 如何讓它消失？

當您接近界限時，即會出現。 如果您的界限包含任何具有窄或不規則圖形的區段，您最後可能會接近它，並使其出現，比您想要的還多。 若要修正此問題，請嘗試使用更大且更一般的圖形再次建立界限。 選取您桌面上的 [ **開始] > 混合實境入口** ，然後選取 [ **執行安裝程式** ]。 

您也可以暫時關閉混合實境入口：選取 **功能表** 中的界限，然後使用切換開關關閉界限。 關閉界限時，您必須停留在單一位置，以避免阻礙。

## <a name="im-having-trouble-with-my-motion-controllers"></a>我的動作控制器發生問題

如果您的移動控制器未正常運作、未連線，或是當您在佩戴耳機時看不到控制器的影像，請嘗試下列動作：

* 請確定您的控制器已開啟。 若要開啟它們，請按住 [ **Windows** ] 按鈕2秒。
* 選取 [ **開始] > 混合實境入口** 在您的電腦上，然後選取 [ **功能表** ]，您應該會看到所列出的動作控制器，以及狀態訊息：
    * 就緒–控制器全都已設定。
    * 遺失追蹤–混合實境入口找不到您的控制器。 將它們放在耳機前方，然後按下 [ **Windows** ] 按鈕4秒，再重新開機，再按2秒。
    * 電力偏低–更換控制器電池。
* 如果使用 Wi-fi，請嘗試將您的電腦連接到5GHz 的 Wi-fi 網路，以減少無線干擾。 
* 針對直接與控制器配對的較新耳機，請選取 [ **...]** **混合實境入口** 按鈕，然後選擇 [ **設定控制器** ]。 這會將您帶到耳機應用程式，以便將控制器配對到耳機。  
* 適用于沒有內建藍牙可直接與控制器配對的舊耳機：  
    * 選取 [> 裝置的設定] > 藍牙 & 電腦上的其他裝置，並確定控制器列示為配對。如果不是，您必須將它們配對。 
    * 如果您有其他 Bluetooth 裝置與您的電腦配對，例如耳機或 gamepads，請嘗試移除部分。 選取 [ **> 裝置的設定] > 藍牙 &** 電腦上的其他裝置，選取裝置，然後選取 [ **移除裝置** ]。
    * 在 [設定] > 裝置中移除藍牙耳機和喇叭 **> 藍牙 & 其他裝置** ，然後關閉裝置。 
    * 如果您使用的是 USB Bluetooth 介面卡，請確定它已插入黑色 USB 2.0 埠，並已從任何其他無線發送器或 USB 快閃磁片磁碟機插入，包括耳機的 USB 連接器。 
    * 如果您的電腦有內建的藍牙，而您遇到連線問題，請嘗試改用 USB 藍牙介面卡。  (若要這樣做，您也必須關閉 [裝置管理員](https://support.microsoft.com/help/4026149)中的內建藍牙無線電，然後將其他 Bluetooth 裝置與新的介面卡配對。 ) 
* 如果 [設定] 應用程式已開啟至 [藍牙 & 其他裝置] 頁面，請將其關閉。

## <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>我在使用耳機時遇到不適感

如需在 Windows Mixed Reality 中緩和的一般資訊，請參閱 [Windows Mixed Reality 沉浸式耳機健康情況、安全和緩和](wmr-health-safety-comfort.md)。 如需特定耳機的詳細資訊，請洽詢耳機製造商。

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>我的視覺效果很慢、載入速度很慢，或看起來沒問題

如果您的混合現實視覺效果看起來不理想，請嘗試下列動作。

* 請確定您的耳機已插入您電腦上正確的圖形配接器。 有些電腦具有整合式和離散的圖形配接器。 離散卡片通常會提供最佳效能。 [深入瞭解電腦硬體](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。
* 關閉桌面上未使用的應用程式。
* 調整您的耳機大小：將它向下移動、靠左或向右移動，並確定它符合 snugly。
* 調整耳機的視覺設定 ( **設定 > 混合現實 > 耳機顯示** ) 。 當 [ **視覺品質** ] 設定為 [ **自動** ] 時，我們會為您的電腦選擇最佳的混合現實體驗。 如需更多視覺效果詳細資料，請將 **視覺品質** 設定為 [ **高** ]。 如果您的視覺效果斷斷續續，您可能會想要選取較低的設定。
* 請嘗試調整耳機的校正。 應調整鏡頭以符合您的 interpupillary 距離 (IPD) ，也就是瞳孔之間的距離。 如果您不知道您的 IPD，optometrist 應該能夠為您進行測量。 也有設計來測量 IPD 的網站。 知道您的 IPD 之後，請使用耳機的校正旋鈕來進行調整。 如果耳機沒有校正旋鈕，請選取 [ **設定 > 混合現實 > 耳機顯示** 並調整校正控制項。

## <a name="i-have-questions-about-my-headset-hardware"></a>我有關于耳機硬體的問題

如需有關耳機的詳細資訊，請洽詢製造商。 Box 中可能會有產品指南，您也可以嘗試製造商的網站。

## <a name="the-floor-in-mixed-reality-seems-to-be-in-the-wrong-spot"></a>混合現實的樓層似乎在錯誤的位置

如果地面看起來 (例如，您覺得您是浮動) ，請選取 [ **開始] > 空間調整** ，同時讓耳機進行變更。

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>我收到一則訊息，表示插入和收取電腦的費用。 為何會這樣？

如果您使用的是膝上型電腦，則在電腦同時完全收取和插入電源時，Windows Mixed Reality 的效果最佳。 

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>如何? 卸載 Windows Mixed Reality？

選取 [ **開始 > 設定 > Mixed reality** ]，然後選取 [ **卸載** ]。 請務必將您的耳機與電腦中斷連線，並在卸載前關閉混合實境入口。

當您準備好再次使用耳機時，請將其插入，混合實境入口將會帶您完成設定。

> [!NOTE]
> 如果您看到一則訊息，指出「我們無法完成移除 Windows Mixed Reality」，這表示某些檔案（包括您的環境相關資訊）仍可能在您的電腦上。 如果您決定稍後重新安裝 Windows Mixed Reality，這可能會造成問題。
> 
> 若要瞭解如何從您的電腦手動移除任何剩餘的 Windows Mixed Reality 資訊，請參閱 **[這篇文章](troubleshooting-windows-mixed-reality.md#how-to-uninstall-windows-mixed-reality)** 。 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>當我使用 Windows Mixed Reality 時，我的 Wi-fi 會變慢

如果您使用 2.4 GHz Wi-fi 連線，則您的移動控制器可能會減緩 Wi-fi。 請嘗試下列其中一項：

<!-- TODO: Use Windows Mixed Reality PC hardware guidelines interlink -->
* 切換至5GHz 的 Wi-fi 連線（如果有的話）。 [深入了解](https://support.microsoft.com/help/4000461)
* 使用個別的 Bluetooth 介面卡，將您的動作控制器連接到您的電腦。 [查看建議的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

## <a name="what-is-the-experience-options-setting"></a>何謂體驗選項設定？

體驗選項設定 ( **設定 > 混合現實 > 耳機顯示 > 體驗選項** ) 讓您能夠變更 Windows Mixed Reality 效能設定。 這可讓您在各種內容中選擇硬體設定的最佳可能體驗。 所有系統都可使用90Hz 體驗，但您可能會想要先試用自動，以查看您偏好的設定。

選項如下：

* 自動或讓 Windows 決定： Windows Mixed Reality 將決定硬體設定的最佳體驗。 對於大部分的人來說，這是開始使用的最佳選擇。
* 60Hz：將重新整理頻率設定為60Hz，並關閉特定功能，例如混合實境入口中的影片捕獲和預覽。
* 90Hz：如果您的耳機能以該速度執行，請將重新整理頻率設定為90Hz。 如果纜線問題導致耳機無法在90Hz 執行，您可能會在啟動時看到此模式已選取時發生錯誤。 

## <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>我看到一則訊息，指出「放在您的耳機」上，即使我有耳機

當您放入耳機時，Windows Mixed Reality 需要一些時間來重載您的空間。 這可能需要幾秒鐘的時間。 如果此訊息未消失，請確定已從鄰近性感應器（位於耳機內的鏡頭）移除保護不乾膠條。 如果已移除此貼紙，但您仍遇到問題，請洽詢您的耳機製造商。 在鍵盤上按 **Win + Y** 將會手動觸發耳機，以在鄰近感應器未自動觸發時執行。 

是否仍需要協助？ 如需 advanced 疑難排解的詳細說明，請參閱 [這篇文章](troubleshooting-windows-mixed-reality.md)。

## <a name="see-also"></a>另請參閱
* [詢問社群](https://answers.microsoft.com)
* [與我們聯繫以取得支援](https://support.microsoft.com/contactus/)