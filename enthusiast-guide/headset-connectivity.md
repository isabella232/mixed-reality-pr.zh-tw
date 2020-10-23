---
title: 耳機連接常見問題
description: 超越標準取用者支援檔的 Advanced Windows Mixed Reality 耳機連線疑難排解。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，疑難排解，錯誤，協助，支援，耳機
appliesto:
- Windows 10
ms.openlocfilehash: abdd0f04443e110f1eb19a31fb3d77e2f3bde929
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434556"
---
# <a name="headset-connectivity-faqs"></a>耳機連接常見問題

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>我的電腦沒有 HDMI 和/或顯示埠

您可能需要使用介面卡。 請前往 [這裡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 取得支援的介面卡清單。

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>我可以使用 USB 或 HDMI 及/或 DisplayPort 延伸模組纜線搭配 Windows Mixed Reality 耳機嗎？
Windows Mixed Reality 耳機未正式支援使用 USB、HDMI 或 DisplayPort 延伸模組纜線。 使用這些纜線可能會大幅影響您的混合現實體驗，原因是您電腦的 USB 控制器與混合現實耳機之間的信號完整性與匯流排電源之間的差異。 如果耳機顯示器短暫顯示藍色畫面，然後在使用時開啟黑色和混合實境入口重新開機或完全解除列舉，或是當耳機音訊剪出或變成 glitchy，或是耳機在黑色和正確顯示器之間閃爍時，請嘗試使用耳機，而不使用擴充纜線。

## <a name="i-am-getting-a-check-your-display-cable-error"></a>我收到「檢查您的顯示器纜線」錯誤

* 如果您使用任何介面卡將耳機連接到您的電腦，請確定其支援 Windows Mixed Reality (介面卡必須是支援4K 的) 。 此外，在將耳機連接至介面卡之前，請先嘗試將介面卡連線到電腦。
* 請嘗試使用不同的 HDMI 和/或 DisplayPort 埠。
* 將您的耳機連接至 DisplayPort 1.2 或更新版本，或 HDMI 1.4 或更新版本。 請確定埠與您電腦上最先進的圖形配接器相對應。
* 如果您的電腦同時具有整合式和離散圖形，請確定您使用的是使用中的圖形配接器上的 HDMI 和/或 DisplayPort 埠。 這可能表示您必須將您的電腦顯示器連接至非 HDMI 埠。
* 如果您的電腦同時具有整合式和離散圖形，且整合式圖形較舊且不支援 Windows Mixed Reality，請嘗試停用整合式 GPU。
* 將電腦監視器連接到電腦的 HDMI 和/或 DisplayPort 埠。 請確定您的圖形驅動程式是最新的。 直接從 AMD、Nvidia 或 Intel 下載並安裝，因為它們可能會比發行至 Windows Update 的版本還新。
* 如果您已將外部監視器插入至 HDMI 埠，請嘗試改為將其插入至 DisplayPort，並將 HDMI 埠用於耳機。
* 請確定您已將耳機的 HDMI 纜線插入電腦上的「HDMI 輸出」埠，而不是「HDMI」埠。
* Windows 可能無法偵測到顯示器纜線連接。 開啟裝置管理員，並查看耳機是否列在 [監視器] 之下。 如果沒有，請選取 [ **動作] > 掃描硬體變更**。 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>有一則訊息指出「放入您的耳機」，但我有耳機

當您放入耳機時，Windows Mixed Reality 可能需要幾秒鐘的時間才能重載您的空間。 如果這則訊息不會消失，請確定已從鄰近性感應器移除保護貼紙，其位於鏡頭之間的耳機內。 如果這無法解決問題，請洽詢您的耳機製造商。

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>有一則訊息顯示「連接您的耳機」，但我已接上耳機

1. 請確定耳機的 USB 和 HDMI 及/或 DisplayPort 纜線已連接到您電腦上的正確埠。 以下說明如何識別正確的埠：
    * USB 3.0 埠具有特殊標誌，其 "SS" 標示 (表示 "SuperSpeed" ) 。 埠的內部部分通常是藍色，而較舊的 USB 2.0 埠通常是在內部的黑色或白色。
    * 如果您的電腦有兩個 HDMI 和/或 DisplayPort 埠，請使用連接到圖形配接器的電腦，而不是電腦的主機板。 這並不一定很明顯，但離散埠通常位於電腦的展開位置。 如果您嘗試一個埠但無法運作，請嘗試其他埠。
2. 從您的耳機中拔下並插上 USB 與 HDMI 及/或 DisplayPort 纜線，以確定它們已安全地連線。 插入 USB 纜線時，請不要在插入 USB 纜線期間暫停。
3. 開啟裝置管理員並確認您的耳機列在 [混合式現實裝置] 下方。 當您選取耳機時，裝置狀態應該會顯示為「此裝置運作正常」。 裝置管理員中的裝置黃色驚嘆號表示錯誤。
    * 如果在裝置管理員中以黃色驚嘆號列出「Hololens 感應器」，請選取裝置。 如果您看到「代碼10：未安裝此裝置的驅動程式」。 此裝置沒有相容的驅動程式」，請 [手動安裝耳機驅動程式](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset)。
    * 如果您在電腦上使用多個混合現實耳機，並且手動安裝了混合現實耳機驅動程式，則手動驅動程式更新可能只會套用到目前連線的耳機，而不會套用到其他耳機。 在此情況下，您會看到「程式碼31：此裝置無法正常運作，因為 Windows 無法載入此裝置所需的驅動程式。  (代碼 31) 。 裝置管理員中已不再提供所要求的 ALPC 訊息」。 在 **裝置管理員 > 混合現實裝置**] 中，以滑鼠右鍵按一下您的耳機，然後選取 [卸載裝置]。 選取 [確定] 以確認並 replug 您的耳機。
4. 如果您看到耳機的部分列舉 (一系列 USB 裝置列舉，但裝置管理員) 中的「混合現實耳機」沒有任何內容，請嘗試使用外部電源的 USB 3.0 中樞。
5. 移至耳機製造商的網站，並更新您耳機的驅動程式和固件。
6. 將您的耳機連接至另一部電腦，然後開啟裝置管理員。 即使該電腦與 Windows Mixed Reality 不完全相容，您仍可查看耳機是否列舉。 如果您的耳機未在多部電腦上列舉，則可能發生硬體問題。

適用于 Surface 使用者：較舊版本的 Surface Dock 和 Surface Book USB Hub 固件更新軟體與混合現實耳機不相容。 如果您在 Surface PC 上收到「連接耳機」訊息，請查看裝置管理員中是否有任何裝置回報「程式碼10：裝置無法啟動」錯誤。 如果是，請 [移除衝突的驅動程式](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)。 您應該只需要做一次。

請注意，Windows 10 N 使用者：如果您的電腦執行 Windows 10 N，則在插入您的混合現實耳機之後，裝置管理員會看到「代碼28：安裝類別不存在或無效」錯誤。 Windows Mixed Reality 不支援 N 版的 Windows 10。 如需詳細資訊，請遵循下列 [指示](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 。

這項資訊也會顯示在 [疑難排解流程圖](headset-connectivity-flowchart.md)中。

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>訊息顯示「檢查 USB 纜線」或「USB 速度不足」。

* 確定您是在電腦上使用支援的 USB 3.0 埠：
    * 請確定您的耳機 USB 纜線已插入。
    * 執行 [Windows Mixed Reality 入口網站](install-windows-mixed-reality.md#launch-mixed-reality-portal) ，以確定您的電腦 USB 3.0 控制器受到支援。
    * 將您的耳機連接到電腦上的其他 USB 3.0 埠。 有些電腦有一個以上的 USB 3.0 控制器。
    * 暫時中斷連接到您電腦的所有 USB 裝置，並只連接您的耳機。
    * 在自訂的電腦上，即使埠可能標示為 USB 3.0 埠，它還是可能連接到 USB 2.0 控制器。 在您的耳機連接後，開啟裝置管理員，找出並按一下任何從您的耳機列舉的裝置，然後移至 [ **依連接查看 > 裝置**]。
* 試用另一台電腦上的耳機。 如果其他電腦與 Windows Mixed Reality 不完全相容，請簽入裝置管理員以查看是否看到「USB 速度不足」訊息。 如果未在多部電腦上正確列舉，則您的耳機可能會有問題。
* 移除耳機與電腦之間的任何擴充項或中樞。

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>插入耳機之後，混合實境入口並未啟動。

因為基礎問題，可能未正確偵測到耳機。 手動啟動混合實境入口，並尋找出現的任何錯誤訊息。 

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>當電腦進入睡眠或睡眠模式時，或在重新開機我的電腦時，如果已附加耳機，我的耳機會停止運作。

1. 開啟裝置管理員並確認您的耳機列在 [混合式現實裝置] 下方。
2. 在 [混合現實裝置] 下選取您的耳機，並確認裝置狀態指出「此裝置運作正常」。
3. 如果您看到「代碼43」錯誤指出裝置已停止運作，或您沒有看到您的耳機列在「混合式現實裝置」底下，請在耳機的 USB 纜線中拔下並 replug。 Microsoft 正在調查可能導致此錯誤的潛在軟體/驅動程式互通性問題。 此問題會影響少量的電腦，而且預期會在未來的混合現實耳機驅動程式更新中解決。

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>當我讓電腦進入睡眠狀態或處於睡眠模式時，我的耳機會導致電腦產生錯誤檢查 (藍色螢幕) 。
請確定您是在10.0.18362.1062 驅動程式或更新版本上。

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>當我插入耳機時，不會自動安裝耳機驅動程式。

在新電腦上，或具有新安裝 Windows 10 複本的電腦上，耳機驅動程式可能會排在其他 Windows 更新後方，而且可能不會立即安裝。 若要手動安裝：
1. 移至 [ **開始] > 裝置管理員** ，然後在 [其他裝置] 的 [hololens 感應器] 裝置中尋找黃色驚嘆號： ![ 裝置管理員 HoloLens 感應器的觀點](images/hololenssensors.png)
2. 在裝置上按一下滑鼠右鍵，然後選取 [屬性]。 如果裝置的內容讀取「此裝置的驅動程式未安裝 (Code 28) 」，請關閉該視窗，然後繼續。 如果有其他訊息，請遵循此頁面其餘部分的疑難排解步驟。
![裝置管理員中的 HoloLens 感應器的 Code 28](images/code28.png)
3. 再以滑鼠右鍵按一下裝置，然後選取 [更新驅動程式 ...]然後，在裝置更新之後，[自動搜尋更新的驅動程式軟體]，您應該會在裝置管理員： ![ Mixed Reality 裝置出現在 [混合的現實裝置] 下方看到您的耳機：裝置管理員](images/mixedrealitydevices.png)

如果手動安裝無法運作，或是您在其他裝置下找不到驅動程式，則您可能需要卸載現有的驅動程式並重新安裝。 若要這樣做：
1. 移至 [ **開始] > 裝置管理員** ，並查看耳機的 [混合的現實裝置]。 裝置狀態應該會指出「裝置運作正常」。
2. 在裝置上按一下滑鼠右鍵，然後選取 [卸載裝置]。
3. 在出現的新快顯視窗中，選取 [刪除此裝置的驅動程式軟體] 核取方塊，然後選取 [卸載]。
4. 完成時，請從您的電腦拔下耳機，然後將它插回。 Windows Update 現在將會下載並安裝新的驅動程式。

注意：如果您有 N 版的 Windows，就必須切換至一般版本的 Windows 10，才能使用 Windows Mixed Reality。


