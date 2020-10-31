---
title: Windows Mixed Reality 設定常見問題集
description: 取得使用 Windows Mixed Reality 時的一般設定問題的解答。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，意見反應，意見反應中樞，bug
appliesto:
- Windows 10
ms.openlocfilehash: c789fbb19f406c6dc355e326f2f12a5d64030e32
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131812"
---
# <a name="windows-mixed-reality-setup-faq"></a>Windows Mixed Reality 設定常見問題集

以下是一些資訊，可協助您在設定 Windows Mixed Reality 沉浸式耳機時，對可能遇到的問題進行疑難排解。

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>我收到一則訊息，指出「我們無法下載 Windows Mixed Reality 軟體」，否則安裝程式會卡在「我們進行一些下載」頁面

嘗試下列作業：

* 移至 [ **設定] > 更新 & 安全性 > Windows Update** 並確認 Windows Update 已開啟。 然後，下載並安裝任何正在等待安裝的更新。
* 請確定您的電腦已連線到網際網路，且至少有2GB 的可用儲存空間。
* 請重新開機您的電腦，然後再試一次。 您可能需要重複數次，或執行 Windows Update 疑難排解員以清除暫止的更新。

> [!NOTE]
> * 如果您是在企業管理的網路上，請洽詢您的系統管理員。 他們可能需要啟用 Windows Mixed Reality。 尋找 IT 專業人員指示嗎？ 請參閱 **[這篇文章](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)** 。
> * 如果您的 Wi-Fi 網路連線設定為 [計量付費]，請將其變更為 [未計費]。 **[深入了解](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>我收到一則訊息，指出「發生問題，無法開始 Windows Mixed Reality」。

嘗試下列作業：

1. 將您的耳機從電腦撥出 (這兩個纜線) 。
2. 重新啟動您的電腦。
3. 前往 [ **設定] > 更新 & 安全性 > Windows Update** 並確定 Windows Update 已開啟。 然後，下載並安裝任何正在等待安裝的更新。
4. 將您的耳機重新連接到電腦上，然後再次嘗試安裝程式。

如果上述步驟沒有作用，請嘗試卸載 Windows Mixed Reality，然後再重新安裝。 移至 [ **設定 > Mixed reality] > 卸載** ]，然後選取 [ **卸載** ]。 重新啟動您的電腦。 若要再次啟動安裝程式，只需將您的耳機插入您的電腦。

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>當我插入耳機時，不會開啟混合實境入口

混合實境入口，會將您帶到 Windows Mixed Reality 安裝程式的應用程式，設計為在插入相容的耳機時自動開啟。 如果未開啟，請移至 [開始]，然後在搜尋方塊中輸入 "混合實境入口" 以開啟應用程式。 如果找不到混合實境入口，這可能表示您需要 [更新至最新版本的 Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq)。

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>我收到一則訊息，指出我的電腦無法執行 Windows Mixed Reality

如果您收到此訊息，則您的電腦不符合執行 Windows Mixed Reality 所需的 [最低需求](https://support.microsoft.com/help/4039260) 。 這可能是因為電腦的硬體安裝程式與 Windows Mixed Reality 不相容，或是因為您需要 [更新至最新版本的 Windows](https://support.microsoft.com/help/12373)。

圖形配接器的附注：

* 如果 Windows Mixed Reality 安裝程式指出您的圖形配接器不符合需求，而您認為它的確如此，請確定您的耳機已插入正確的卡片中。
* 請洽詢您的圖形配接器製造商，以取得最新的驅動程式更新。 Windows Mixed Reality 需要至少支援 WDDM 2.2 的圖形配接器驅動程式。

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>我收到一則訊息，告訴您：「您已經在這部電腦上，這台電腦不符合執行 Windows Mixed Reality 所需的最低需求。」

如果您收到此訊息，表示您的電腦不符合 Windows Mixed Reality 中最佳體驗所需的最低需求。 您的電腦可能可以執行沉浸式耳機，但可能無法執行某些應用程式，或可能發生效能問題。

## <a name="my-xbox-controller-isnt-working"></a>我的 Xbox 控制器無法運作

嘗試下列作業：

* 確定您的控制器已開啟、完全收費，並連接到電腦。
* 更換控制器的電池。
* 如果您使用 Bluetooth 控制器，請移至電腦上的 [ **設定] > 裝置 > 藍牙 &** 電腦上的其他裝置，並確定它已配對 (您應該會看到它列在頁面) 上。

[深入瞭解 Xbox 控制器](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>我的動作控制器無法運作

嘗試下列作業：

* 請確定您的控制器已開啟且已完全收費。
* 更換控制器的電池。
* 將控制器放在您面前之前，請關閉並重新開啟控制器。 按住 [Windows] 按鈕4秒，關閉控制器，然後再按一次，再按2秒鐘來開啟。
* 移至 [ **設定] > 裝置 > 藍牙 &** 電腦上的其他裝置，並確定它們已配對 (您應該會看到它們列在頁面) 上。

[深入瞭解動作控制器](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>我收到一則訊息，指出「即使我已接上耳機，也可以連接您的耳機」

嘗試下列作業：

- 確定您的耳機連接到電腦上正確的埠。 它應該插入電腦的離散圖形配接器和 USB 3.0 埠。 以下說明如何識別正確的埠：
    - USB 3.0 埠具有特殊標誌，其 "SS" 標示 (表示 "SuperSpeed" ) 。 埠的內部部分通常是藍色，而較舊的 USB 2.0 埠通常是在內部的黑色或白色。
    - 如果您的電腦有兩個 HDMI 埠，請使用連接到圖形配接器的埠，而不是電腦的主機板。 這並不一定很明顯，但離散埠通常位於電腦的展開位置。 如果您嘗試一個埠但無法運作，請嘗試其他埠。
- 移至耳機製造商的網站，並更新您耳機的驅動程式和固件。

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>在混合現實的過程中，我會停滯在「將您的前端轉到一邊，然後在地面」

此步驟可讓您的耳機辨識您的空間，並還原任何現有的虛擬樓層和界限。 當您放入耳機時，此掃描程式最多可能需要10秒鐘的時間。 完成之後，您將會位於 Windows Mixed Reality home，否則系統會提示您再次設定界限。

如果掃描程式所花費的時間超過10秒，則耳機中的鄰近感應器可能會發生問題：

1. 檢查是否已從鄰近感應器移除不乾膠。 近接感應器位於耳機內，大約是您冷汗中心的位置。
2. 檢查您的鄰近感應器是否正在將輸入切換至您的耳機：使用手指，在確認輸入正在切換到耳機時，請先涵蓋並找出鄰近感應器數次。 您應該會在電腦頂端看到 **Windows 鍵 + Y** 橫幅。 您可以在鍵盤上輸入 **Windows 鍵 + Y** ，隨時手動將輸入切換到耳機。

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>我的 Windows Mixed Reality 首頁的樓層似乎不是正確的高度

選取 [ **開始 > 地面調整** ]，這會在您將應用程式放在世界中時啟動，以在戴耳機時進行變更。 在此應用程式中，系統會將您導向使用觸控板 (移動控制器) 或方向 (板) 來調整樓層高度。 當地面感覺正確時，請使用 [Windows] 按鈕返回您的首頁。

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>我無法在我的電腦上顯示我在耳機中看到的內容預覽

Windows Mixed Reality 入口網站的畫面底部有一個 [ **播放** ] 按鈕，可讓您在桌面畫面上預覽您在耳機中看到的內容。 基於效能考慮，只有在 Windows Mixed Reality Ultra (90Hz) 的電腦上才能使用此功能。

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>我要如何在我的耳機中取得更清楚的觀點

請嘗試調整您耳機的大小。 調整其在您臉部的位置，方法是將它向上或向下、向左和向右移動，然後調整母線使其感覺箱子。

如果您的耳機支援，您也可以調整其校正設定。 如果耳機有旋鈕來調整校正，請使用該旋鈕。 如果不是，請移至 [ **設定] > Mixed reality > 視覺品質** ，並在該處調整校正。 如需有關特定裝置的校正的詳細資訊，請洽詢您的耳機製造商。

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>當我插入耳機時，不會發生任何事，混合實境入口不會開啟

混合實境入口，會將您帶到 Windows Mixed Reality 安裝程式的應用程式，設計為在插入相容的耳機時自動開啟。 如果未開啟，請移至 [ **開始** ]，然後在 [ **搜尋** ] 方塊中輸入 **混合實境入口** ，從該處開啟應用程式。 如果找不到混合實境入口，這可能表示您需要 [更新至最新版本的 Windows](https://support.microsoft.com/help/12373) ，或您的耳機未正確地連接到電腦。

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>我的前端掛接顯示在關閉並快速啟動之後無法運作

試試看：

* 從前端掛接顯示中拔下顯示器纜線和 USB 纜線，然後將其插回。

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>我的 Wi-Fi 在使用 Windows Mixed Reality 時變慢

如果您使用 2.4 GHz Wi-Fi 連接，您的移動控制器可能會減緩您的 Wi-fi。 請嘗試下列其中一項：

* 切換至 5 GHz Wi-Fi 連接（如果有的話）。 深入了解
* 使用個別的 Bluetooth 介面卡，將您的動作控制器連接到您的電腦。 [查看建議的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> 透過內建藍牙晶片，將較新的耳機組直接配對至控制器，但不會遇到此問題。

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>我收到「發生錯誤」的錯誤訊息，或我遇到混合實境入口的問題

若要取得特定錯誤碼的詳細資訊，請參閱 [這裡](error-codes.md)。 您也可以嘗試：

重新開機 Windows Mixed Reality：

1. 從電腦中斷連接耳機纜線。
2. 重新啟動電腦。
3. 重新連接您的耳機。

確定您的電腦能夠辨識您的耳機：

1. 選取 [啟動]。
2. 在搜尋方塊中輸入 "裝置管理員"，然後在清單中選取它。
3. 展開 [混合現實裝置]，並查看是否已列出您的耳機。

如果未列出：

1. 將耳機插入電腦上的不同埠（如果有的話）。
2. 從 Windows Update 檢查是否有最新的軟體更新。
3. 卸載並重新安裝 Windows Mixed Reality：
    1. 從電腦中斷連接耳機纜線。
    2. 選取 [ **> 混合現實 > 卸載] 設定** 。
    3. 如果您的移動控制器已與您的電腦配對，請選取 [ **> 裝置] > 藍牙 & 其他裝置** 來將這些裝置的設定。 選取每個控制器，然後選取 [移除裝置]。 如果您的控制器與耳機配對，您可以略過此步驟。
    4. 將您的耳機插回電腦以重新安裝 Windows Mixed Reality。

## <a name="see-also"></a>另請參閱

* [詢問社群](https://answers.microsoft.com)
* [與我們聯繫以取得支援](https://support.microsoft.com/contactus/)
* [疑難排解](troubleshooting-windows-mixed-reality.md)