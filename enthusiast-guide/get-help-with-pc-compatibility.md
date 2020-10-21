---
title: 在 Windows Mixed Reality 中取得電腦相容性的協助
description: 使用 Windows Mixed Reality 時，協助電腦相容性問題的資源。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，意見反應，意見反應中樞，bug
appliesto:
- Windows 10
ms.openlocfilehash: b9b9d46e2ab71fa90960e403ceac94b95ba01440
ms.sourcegitcommit: d8f39c0b95d9e61d645d64f27baabc7a1c300dc1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92293072"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>在 Windows Mixed Reality 中取得電腦相容性的協助

當您在電腦上設定 Windows Mixed Reality 或執行 [Windows Mixed Reality PC Check](https://www.microsoft.com/p/windows-mixed-reality-pc-check/9nzvl19n7cnc?rtc=1#activetab=pivot:overviewtab) 應用程式時，您會收到一份報告，指出您的電腦是否已準備好執行。 以下是您可能會看到的一些詳細資料。

若要確定您可以執行混合的現實，請參閱 [最小的電腦硬體相容性需求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。

## <a name="youre-good-to-go"></a>您已經準備好了

好消息-您的電腦可以 Windows Mixed Reality 執行。 但是請記住，電腦硬體和設定之間仍有變化，因此每台電腦上的混合現實體驗可能不會相同。

## <a name="supports-some-features"></a>支援某些功能

您的電腦應該能夠執行某些 Windows Mixed Reality 經驗，但可能無法提供最佳體驗。 圖形可能會延隔，有些應用程式和遊戲可能無法正常運作，而有些則可能無法執行。 

以下是您可能會看到的訊息，以及如何處理這些訊息：

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>這部電腦有一個具有單一通道 RAM 的整合式圖形配接器

整合式圖形配接器可在具有雙重通道 RAM 的電腦上提供最佳的 Windows Mixed Reality 體驗。 如果您遇到效能問題，請嘗試下列其中一項：

* 安裝 [相容的離散圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)。
* 安裝額外的 RAM 來建立雙聲道 RAM。
* 切換至 [相容的電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>這部電腦具有混合式圖形設定與不相容的 PCIe 連結

PCIe 代表 *周邊元件連接 Express*。 這是電腦用來與圖形配接器通訊的連接。 您的設定可能會運作，但如果遇到問題，您必須切換到 [相容的電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>此電腦的圖形驅動程式可能無法搭配 Windows Mixed Reality

如果您遇到問題，請嘗試使用 Windows Update 下載新的圖形驅動程式 (**啟動 > 設定 > 更新 & 安全性 > 檢查更新**) -或移至您的電腦製造商或圖形配接器製造商的網站。

> [!div class="nextstepaction"]
> [檢查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果無法運作，您將需要新增 [相容的圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 或切換至 [相容的電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>此電腦的處理器可能無法搭配 Windows Mixed Reality

此電腦的處理器可能無法與 Windows Mixed Reality 搭配運作，因為它沒有足夠的核心。 如果 Windows Mixed Reality 無法順利執行，請以 [相容](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 的處理器取代，或切換至 [相容的電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>這部電腦可能沒有相容的 USB 設定

如果您遇到執行 Windows Mixed Reality 的問題，請嘗試下列步驟：

* 將您的耳機插入不同的 USB 埠（如果有的話）。
* 如果無法運作，請將您電腦的目前 USB 驅動程式卸載，然後重新安裝 Microsoft 驅動程式：

1. 選取 [開始]，然後在 [**搜尋**] 方塊中輸入「裝置管理員 **」**。
2. 從結果中選取 [ **裝置管理員** ]。
3. 展開 [通用序列匯流排控制器] 的類別，查看列出的裝置，然後卸載任何不相容的驅動程式。
    * 如果清單中包含「可延伸的主機控制器」專案，且該專案在裝置名稱的結尾沒有「Microsoft」，則該驅動程式與 Windows Mixed Reality 不相容。 您必須將它卸載。 若要卸載驅動程式，請在清單中的裝置上按一下滑鼠右鍵，然後選取 [ **卸載裝置**]。 選取 [ **刪除此裝置的驅動程式軟體** ] 核取方塊，然後選取 [ **卸載**]。
    * 如果清單包含名稱中包含 "Etron" 的「可延伸主機控制器」專案，表示該 USB 控制器與 Windows Mixed Reality 不相容。 您必須在電腦上使用不同的 USB 埠，或購買不同的 USB 3.0 主機控制器。
4. 重新啟動電腦。
5. 返回裝置管理員，然後再次找出可延伸的主機控制器專案。 如果您現在在裝置名稱的結尾看到「Microsoft」，您就可以開始了。 如果沒有，請重複執行卸載步驟，以移除任何其他非 Microsoft 版本的驅動程式。

* 如果仍然無法運作，請將 PCIe USB 卡新增至您的電腦。

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>這部電腦沒有藍牙4.0 適用于控制器

某些耳機上的混合現實運動控制器需要藍牙4.0。 您仍然可以使用 Windows Mixed Reality 搭配 Xbox 控制器或使用滑鼠和鍵盤，也可以使用 USB 藍牙介面卡將移動控制器連接到您的電腦。 [查看建議的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>根據您的耳機，您可能需要 Bluetooth 介面卡才能使用移動控制器

有些耳機有內建藍牙，讓控制器可以直接配對到耳機。 有些則需要電腦 (中的藍牙無線電或個別的轉換器) 使用移動控制器。 [查看建議的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>這部電腦沒有自我供電的 USB 埠

需要自我驅動的 USB 3.0 埠才能連接 Windows Mixed Reality 耳機。 將驅動的 USB 3.0 集線器連接到電腦，並使用它來連接耳機。

### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>此電腦應該可以運作，但您將擁有高效能 Intel®處理器的最佳體驗

此電腦應該可以運作，但高效能 Intel 處理器將提供最佳體驗。 我們建議使用第8代 Intel® Core™或7個 Gen Intel® Core™ i5 處理器。

## <a name="cant-run-windows-mixed-reality"></a>無法執行 Windows Mixed Reality

以下是您可能會看到的訊息，以及如何處理這些訊息：

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>此電腦的圖形配接器無法搭配 Windows Mixed Reality

這部電腦的圖形配接器與 Windows Mixed Reality 不相容。 您將需要新增相容的 [圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 或切換至相容的 [電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>這部電腦的圖形驅動程式無法使用 Windows Mixed Reality

此電腦的圖形驅動程式無法搭配 Windows Mixed Reality 使用。 請嘗試使用 Windows Update 下載新的圖形驅動程式 (**開始 > 設定 > 更新 & 安全性 > 檢查更新**) -或移至您的電腦製造商或圖形配接器製造商的網站。 

> [!div class="nextstepaction"]
> [檢查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果無法運作，您將需要新增 [相容的圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 或切換至 [相容的電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>此電腦的處理器無法搭配 Windows Mixed Reality

此電腦的處理器不會 supprot AVX/Popcnt 指令。 若要執行 Windows Mixed Reality，您必須將它取代為 [相容的圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ，或切換至 [相容的電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>這部電腦沒有足夠的可用磁碟空間來執行 Windows Mixed Reality

Windows Mixed Reality 需要10GB 的可用磁碟空間以進行安裝和最佳效能。 請清除磁片磁碟機上的一些空間，然後再次嘗試安裝程式。

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>這部電腦執行的 Windows 版本不支援 Windows Mixed Reality

Windows Mixed Reality 可在 Windows 10 家用版和 Windows 10 專業版上運作。 您必須安裝其中一個版本，才能使用 Windows Mixed Reality。

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>這部電腦未執行最新版本的 Windows 10

Windows Mixed Reality 需要 Windows 10 Fall Creators Update。 請[更新您的電腦](https://support.microsoft.com/help/4028685)，然後再試一次。

### <a name="this-pc-has-no-usb-30-port"></a>這部電腦沒有 USB 3.0 埠

您將需要 USB 3.0 埠來連接 Windows Mixed Reality 耳機。 如果您使用的是桌上型電腦，請新增 PCIe USB 卡。 如果您使用的是膝上型電腦，則必須切換至相容的 [電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="you-cant-run-this-app-via-remote-desktop"></a>您無法透過遠端桌面執行此應用程式

若要使用 Windows Mixed Reality，您將會有連接到監視器的電腦。 如果您使用虛擬機器或沒有監視，請嘗試使用虛擬顯示器介面卡。 這是一部裝置，會插入電腦的 DisplayPort 並模擬電腦顯示。 

## <a name="getting-the-best-performance"></a>取得最佳效能

某些硬體設定可能會導致 Windows Mixed Reality 的效能問題。 針對緩慢載入、不穩定的視覺效果或不良的視覺品質等問題，請嘗試下列常見的修正：

* 關閉在電腦桌面上執行的任何開啟的應用程式。
* 如果您使用的是 USB 或 DisplayPort 至 HDMI 介面卡，請試著另一個。 查看建議的介面卡
* 如果有額外的監視器連接到電腦的圖形配接器，請將它們中斷連接。
* 嘗試從 Windows 市集中下載一些不同的混合現實應用程式，有些應用程式可能更適合您的電腦設定。

> [!NOTE]
> 如果您看到一則訊息，指出「此硬體設定可能與 Windows Mixed Reality 搭配運作，但尚未經過測試」，您可能會在執行長時間的 Windows Mixed Reality 時遇到一些效能問題。

## <a name="see-also"></a>另請參閱

* [詢問社群](https://answers.microsoft.com)
* [與我們聯繫以取得支援](https://support.microsoft.com/contactus/)
* [疑難排解](troubleshooting-windows-mixed-reality.md)