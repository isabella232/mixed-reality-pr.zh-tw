---
title: Windows Mixed Reality 安裝程式常見問題
description: 取得使用 Windows Mixed Reality 時的一般設定問題的解答。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，意見反應，意見反應中樞，bug
appliesto:
- Windows 10
ms.openlocfilehash: 2e7276e7d734770e29ce41db9a19ef40555fea30
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680204"
---
# <a name="windows-mixed-reality-setup-faq"></a>Windows Mixed Reality 安裝程式常見問題

以下是一些資訊，可協助您在設定 Windows Mixed Reality 沉浸式耳機時，對可能遇到的問題進行疑難排解。

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>我收到一則訊息，指出「我們無法下載 Windows Mixed Reality 軟體」，否則安裝程式會卡在「我們進行一些下載」頁面上，

嘗試下列作業：
* 移至 [ **設定] > 更新 & 安全性 > Windows Update** 並確認 Windows Update 已開啟。 然後，下載並安裝任何正在等待安裝的更新。
* 請確定您的電腦已連線到網際網路，且至少有2GB 的可用儲存空間。
* 請重新開機您的電腦，然後再試一次。 您可能需要重複數次，或執行 Windows Update 疑難排解員以清除暫止的更新。 

> [!NOTE]
> * 如果您是在企業管理的網路上，請洽詢您的系統管理員。 他們可能需要啟用 Windows Mixed Reality。 尋找 IT 專業人員指示嗎？ 請參閱 **[這篇文章](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)** 。
> * 如果您的 Wi-fi 網路連線設定為計量付費，請將它變更為「未計費」。 **[深入了解](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>我收到一則訊息，指出「發生問題，無法開始 Windows Mixed Reality」。

嘗試下列作業：
1. 將您的耳機從電腦撥出 (這兩個纜線) 。
2. 重新啟動您的電腦。
3. 前往 [ **設定] > 更新 & 安全性 > Windows Update** 並確定 Windows Update 已開啟。 然後，下載並安裝任何正在等待安裝的更新。
4. 將您的耳機重新連接到電腦上，然後再次嘗試安裝程式。

如果上述步驟沒有作用，請嘗試卸載 Windows Mixed Reality，然後再重新安裝。 移至 [ **設定 > Mixed reality] > 卸載** ]，然後選取 [ **卸載** ]。 重新啟動您的電腦。 若要再次啟動安裝程式，只需將您的耳機插入您的電腦。

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>我收到一則訊息，指出我的電腦無法 Windows Mixed Reality 執行。

如果您收到此訊息，則您的電腦不符合執行 Windows Mixed Reality 所需的 [最低需求](https://support.microsoft.com/help/4039260) 。 這可能是因為電腦的硬體安裝程式與 Windows Mixed Reality 不相容，或是因為您需要 [更新至最新版本的 Windows](https://support.microsoft.com/help/12373)。

圖形配接器的附注：

* 如果 Windows Mixed Reality 安裝程式指出您的圖形配接器不符合需求，而您認為它的確如此，請確定您的耳機已插入正確的卡片中。
* 請洽詢您的圖形配接器製造商，以取得最新的驅動程式更新。 Windows Mixed Reality 需要至少支援 WDDM 2.2 的圖形配接器驅動程式。

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>我收到一則訊息，告訴您：「您已經在這部電腦上，這台電腦不符合執行 Windows Mixed Reality 所需的最低需求。」

如果您收到此訊息，表示您的電腦不符合 Windows Mixed Reality 中最佳體驗所需的最低需求。 您的電腦可能可以執行沉浸式耳機，但可能無法執行某些應用程式，或可能發生效能問題。

## <a name="my-xbox-controller-isnt-working"></a>我的 Xbox 控制器無法運作。

嘗試下列作業：

* 確定您的控制器已開啟、完全收費，並連接到電腦。
* 更換控制器的電池。
* 如果您使用 Bluetooth 控制器，請移至電腦上的 [ **設定] > 裝置 > 藍牙 &** 電腦上的其他裝置，並確定它已配對 (您應該會看到它列在頁面) 上。

[深入瞭解 Xbox 控制器](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>我的動作控制器無法運作。
 
嘗試下列作業：

* 請確定您的控制器已開啟且已完全收費。
* 更換控制器的電池。
* 將控制器放在您面前之前，請關閉並重新開啟控制器。 按住 [Windows] 按鈕4秒，關閉控制器，然後再按一次，再按2秒鐘來開啟。 
* 移至 [ **設定] > 裝置 > 藍牙 &** 電腦上的其他裝置，並確定它們已配對 (您應該會看到它們列在頁面) 上。

[深入瞭解動作控制器](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>我收到一則訊息，指出「即使我已接上耳機，也可以連接您的耳機」

嘗試下列作業：

* 確定您的耳機連接到電腦上正確的埠。 它應該插入電腦的離散圖形配接器和 USB 3.0 埠。 以下說明如何識別正確的埠：
    * USB 3.0 埠具有特殊標誌，其 "SS" 標示 (表示 "SuperSpeed" ) 。 埠的內部部分通常是藍色，而較舊的 USB 2.0 埠通常是在內部的黑色或白色。
    * 如果您的電腦有兩個 HDMI 埠，請使用連接到圖形配接器的埠，而不是電腦的主機板。 這並不一定很明顯，但離散埠通常位於電腦的展開位置。 如果您嘗試一個埠但無法運作，請嘗試其他埠。
* 移至耳機製造商的網站，並更新您耳機的驅動程式和固件。

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>當我嘗試建立界限時，收到錯誤訊息。

以下是建立界限的一些指導方針：

* 切勿太接近牆或其他障礙物。
* 請務必將您的耳機保持 waist 高度，並在追蹤界限時面對您的電腦。
* 請確定感應器未遭到封鎖，且有足夠的光線。
* 您要追蹤的空間應大於3個正方形計量。
* 空間應該不會太大或太複雜，而是不需要訣竅和輪流的簡單幾何形狀。
* 當您進行追蹤時，請勿交叉回復自己的路徑。
* 如果您卡在角落，請從頭開始。

**如果我選擇「僅限站即坐」，會有何種體驗？**

「僅限站即用」表示您將在沒有界限的情況下使用耳機。 您需要留在同一處，因為您沒有界限可協助您避免實體障礙。 此外，某些應用程式和遊戲可能會設計為搭配界限使用，因此可能無法如預期運作。

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>我要如何在我的耳機中取得更清楚的觀點？

請嘗試調整您耳機的大小。 調整其在您臉部的位置，方法是將它向上或向下、向左和向右移動，然後調整母線使其感覺箱子。

如果您的耳機支援，您也可以調整其校正設定。 如果耳機有旋鈕來調整校正，請使用該旋鈕。 如果不是，請移至 [ **設定] > Mixed reality > 視覺品質** ，並在該處調整校正。 如需有關特定裝置的校正的詳細資訊，請洽詢您的耳機製造商。

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality 支援哪些語言？

Windows Mixed Reality 提供下列語言版本。 如果您的電腦設定為不同的語言，您仍然可以使用 Windows Mixed Reality，但介面會以英文 (顯示) ，而且語音命令和聽寫將無法使用。

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

您也可以使用上面所列的其中一種支援的 Windows Mixed Reality 語言的聽寫，只要在螢幕小鍵盤上選取 [ **麥克風**  ] 即可。

Windows Mixed Reality 也提供下列語言版本，不需要語音命令或聽寫功能：

* 繁體中文 (臺灣和香港特別行政區) 
* 荷蘭文 (荷蘭)
* 韓文 (韓國)
* 俄文 (俄羅斯)

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>當我插入耳機時，不會發生任何事，混合實境入口不會開啟。

混合實境入口，會將您帶到 Windows Mixed Reality 安裝程式的應用程式，設計為在插入相容的耳機時自動開啟。 如果未開啟，請移至 [ **開始** ]，然後在 [ **搜尋** ] 方塊中輸入 **混合實境入口** ，從該處開啟應用程式。 如果找不到混合實境入口，這可能表示您需要 [更新至最新版本的 Windows](https://support.microsoft.com/help/12373) ，或您的耳機未正確地連接到電腦。

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer"></a>我無法聽到耳機中的任何聲音，或音效正在電腦上播放。

如果您的沉浸式耳機未包含內建耳機，您必須將耳機連接到耳機上的音訊插孔。  (的插座通常位於耳機面板或鏡頭的後方;如果找不到您的耳機製造商，請洽詢。 )  

有些音訊耳機具有可控制音量的實體按鈕。 如果音訊無法運作，請檢查磁片區是否已關閉或靜音。

Windows Mixed Reality 是設計用來在您的沉浸式耳機上播放音效，並將其連接到耳機。 當您將耳機移開或翻轉面板時，音訊將切換至您的預設 Windows 播放裝置。 您可以在 [ **設定 > 混合現實 > 音訊和語音** ] 中變更此設定。

> [!NOTE]
> * Windows Mixed Reality 空間音訊最適合搭配內建或直接連線到您的沉浸式耳機的耳機。 連接到電腦的電腦喇叭或耳機可能無法正常適用于空間音訊。
> * Windows Mixed Reality 不支援藍牙音訊耳機。

## <a name="speech-commands-arent-working"></a>語音命令無法運作。

若要使用語音命令，您電腦的語音和語言設定必須設定為 Windows Mixed Reality 所支援的其中一種 [語言](#what-languages-are-supported-in-windows-mixed-reality) 。 若要檢查這一點，請移至 [ **設定 > 時間] & 語言 > 區域 & 語言** 和 **設定 > & 語言 > 語言** 。

如果您的耳機沒有內建的 mic，您將需要使用 mic 連接耳機或您的電腦。 當您磨損麥克風時，若要自動將 mic 輸入切換至您的耳機，請移至 [ **設定] > Mixed reality > 音訊和語音** ，並確定 **當我磨損耳機時，切換到耳機 mic** 已開啟。

有些音訊耳機具有實體按鈕，可將麥克風靜音和取消靜音。 如果語音命令無法運作，請查看您的 mic 是否已靜音。

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>我的前端掛接顯示在關閉並進行快速啟動之後無法運作。

試試看：

* 從前端掛接顯示中拔下顯示器纜線和 USB 纜線，然後將其插回。

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>當我使用 Windows Mixed Reality 時，我的 Wi-fi 會變慢

如果您使用的是 2.4 GHz Wi-fi 連線，移動控制器可能會減緩您的 Wi-fi。 請嘗試下列其中一項：

* 切換至 5 GHz Wi-fi 連線（如果有的話）。 深入了解
* 使用個別的 Bluetooth 介面卡，將您的動作控制器連接到您的電腦。 [查看建議的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> 透過內建藍牙晶片，將較新的耳機組直接配對至控制器，但不會遇到此問題。 

## <a name="see-also"></a>另請參閱
* [詢問社群](https://answers.microsoft.com)
* [與我們聯繫以取得支援](https://support.microsoft.com/contactus/)
* [疑難排解](troubleshooting-windows-mixed-reality.md)

