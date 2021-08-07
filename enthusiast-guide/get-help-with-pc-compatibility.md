---
title: 取得電腦相容性的協助
description: 使用 Windows Mixed Reality 應用程式和裝置時，隨時掌握解決電腦相容性問題的最新資源。
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，意見反應，意見反應中樞，bug
appliesto:
- Windows 10
ms.openlocfilehash: cd5598147823670d1aa00eddda844bea21d7da262339624613f3724cbc5157fa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189210"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>在 Windows Mixed Reality 中取得電腦相容性的協助

當您設定 Windows Mixed Reality 或使用[混合實境入口](install-windows-mixed-reality.md)時，您將會收到一份報告，指出您的電腦是否已完成工作。 我們已細分您可能會在下列各節中看到的特定詳細資料。

繼續進行之前，請先嘗試下列最常見的修正： 

> [!div class="checklist"]
> * 請確定您的電腦符合 [最低的電腦硬體相容性需求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * 檢查您的 [圖形配接器和處理器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 是否相容
> * 檢查 [建議的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 清單
> * 選取 [**開始] > 設定 > 更新 & 安全性 > 檢查更新，以** 更新您的圖形驅動程式 

如果您想要取得連絡人，您可以 [詢問該社區](https://answers.microsoft.com)、 [聯絡支援](https://support.microsoft.com/contactus/)或移至 [疑難排解](troubleshooting-windows-mixed-reality.md) 資訊。

## <a name="youre-good-to-go"></a>您已經準備好了

好消息，如果您看到的 **是好** 消息，您的電腦就可以 Windows Mixed Reality 執行！ 電腦硬體和設定之間仍有變化，因此每台電腦上的混合現實體驗可能不會相同。

## <a name="supports-some-features"></a>支援某些功能

如果您看到 [**支援某些功能**] 訊息，則您的電腦可以執行某些 Windows Mixed Reality 經驗，但可能無法提供最佳體驗。 可能的缺點包括延遲圖形、效能點擊，以及一些您無法執行的應用程式和遊戲。 我們已列出您可能會看到的訊息，以及其處理方式：

* [這部電腦有一個具有單一通道 RAM 的整合式圖形配接器](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [這部電腦具有混合式圖形設定與不相容的 PCIe 連結](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [此電腦的圖形驅動程式可能無法搭配 Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [此電腦的處理器可能無法搭配 Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [這部電腦可能沒有相容的 USB 設定](#this-pc-might-not-have-a-compatible-usb-configuration)
* [這部電腦沒有適用于控制器的藍牙4。0](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [根據您的耳機，您可能需要藍牙介面卡才能使用移動控制器](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [這部電腦沒有自我供電的 USB 埠](#this-pc-doesnt-have-a-self-powered-usb-port)
* [此電腦的圖形配接器無法搭配 Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [這部電腦的圖形驅動程式無法使用 Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [此電腦的處理器無法搭配 Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [這部電腦沒有足夠的可用磁碟空間來執行 Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [這部電腦正在執行不支援的 Windows 版本 Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [這部電腦未執行最新版本的 Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [這部電腦沒有 USB 3.0 埠](#this-pc-has-no-usb-30-port)
* [您無法透過遠端桌面執行此應用程式](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>這部電腦有一個具有單一通道 RAM 的整合式圖形配接器

整合式圖形配接器可在具有雙重通道 RAM 的電腦上提供最佳的 Windows Mixed Reality 體驗。 如果您遇到效能問題：

> [!div class="checklist"]
> * 安裝 [相容的離散圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * 安裝額外的 RAM 杆以建立雙通道 RAM
> * 切換至 [相容的電腦](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>這部電腦具有混合式圖形設定與不相容的 PCIe 連結

PCIe 代表 *周邊元件連接 Express*，也就是電腦用來與圖形配接器通訊的連線。 您的設定可能會運作，但如果遇到問題，您必須切換至相容的 [電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>此電腦的圖形驅動程式可能無法搭配 Windows Mixed Reality

請嘗試使用 Windows Update 下載新的圖形驅動程式，方法如下：

> [!div class="checklist"]
> * 選取 [**開始] > 設定 > 更新 & 安全性] > 檢查更新** 或前往您的電腦或圖形配接器製造商的網站
> * [檢查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果無法運作，您必須：

> [!div class="checklist"]
> * 新增 [相容的圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切換至 [相容的電腦](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>此電腦的處理器可能無法搭配 Windows Mixed Reality

因為電腦的處理器沒有足夠的核心，所以 Windows Mixed Reality 可能無法正常運作。 如果 Windows Mixed Reality 無法正常執行：

> [!div class="checklist"]
> * 將處理器取代為[相容](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)的處理器 
> * 切換至 [相容的電腦](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>這部電腦可能沒有相容的 USB 設定

針對執行 Windows Mixed Reality 的問題：

> [!div class="checklist"]
> * 請參閱我們 [建議的介面卡檔](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) ，以取得常見相容性問題的解決方案
> * 考慮使用 [外部電源 USB 集線器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

如果問題持續發生：

> [!div class="checklist"]
> * 將您的耳機插入不同的 USB 埠（如果有的話）。
> * 如果無法運作，請將您電腦的目前 USB 驅動程式卸載，然後重新安裝 Microsoft 驅動程式：

1. 選取 [開始]，然後在 [**搜尋**] 方塊中輸入「裝置管理員 **」**。
2. 從結果中選取 [ **裝置管理員** ]。
3. 展開 [通用序列匯流排控制器] 的類別，查看列出的裝置，然後卸載任何不相容的驅動程式。
    * 如果清單中包含的「可延伸主機控制器」專案在裝置名稱的結尾沒有「Microsoft」，則該驅動程式與 Windows Mixed Reality 不相容。 您必須將它卸載。 若要卸載驅動程式，請在清單中的裝置上按一下滑鼠右鍵，然後選取 [ **卸載裝置**]。 選取 [ **刪除此裝置的驅動程式軟體** ] 核取方塊，然後選取 [ **卸載**]。
    * 如果清單包含名稱中包含 "Etron" 的「可延伸主機控制器」專案，表示該 USB 控制器與 Windows Mixed Reality 不相容。 您必須在電腦上使用不同的 USB 埠，或購買不同的 USB 3.0 主機控制器。
4. 重新啟動電腦。
5. 返回裝置管理員，然後再次找出可延伸的主機控制器專案。 如果您現在在裝置名稱的結尾看到「Microsoft」，您就可以開始了。 如果沒有，請重複卸載步驟來移除任何額外的非 Microsoft 版本的驅動程式。

> [!div class="checklist"]
> * 如果仍然無法運作，請將 PCIe USB 卡新增至您的電腦。

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>這部電腦沒有適用于控制器的藍牙4。0

2018和更新版本的 Windows Mixed Reality 耳機已經內建藍牙，但如果您有較舊的耳機，混合的現實運動控制器需要藍牙4.0。 您仍然可以[將 Windows Mixed Reality 與 Xbox 控制器](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)、[滑鼠和鍵盤](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)或[USB 藍牙介面卡搭配使用，以將動作控制器連接](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)到您的電腦。 [查看建議的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>根據您的耳機，您可能需要藍牙介面卡才能使用移動控制器

有些耳機有藍牙內建，因此控制器可以直接配對到耳機。 有些則需要電腦 (中的藍牙無線電或個別的轉換器) 才能使用移動控制器。 如需詳細資訊，請參閱 [建議的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) 頁面。

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>這部電腦沒有自我供電的 USB 埠

需要自我驅動的 USB 3.0 埠才能連接 Windows Mixed Reality 耳機。 連線[驅動的 USB 3.0 集線器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)連接到電腦上，並使用它來連接耳機。

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>此電腦的圖形配接器無法搭配 Windows Mixed Reality

這部電腦的圖形配接器與 Windows Mixed Reality 不相容。 您必須：

> [!div class="checklist"]
> * 新增 [相容的圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切換至 [相容的電腦](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>這部電腦的圖形驅動程式無法使用 Windows Mixed Reality

此電腦的圖形驅動程式無法搭配 Windows Mixed Reality 使用。 請嘗試使用 Windows Update 下載新的圖形驅動程式，方法如下：

> [!div class="checklist"]
> * 選取 [**開始] > 設定 > 更新 & 安全性] > 檢查更新** 或前往您的電腦或圖形配接器製造商的網站
> * [檢查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果無法運作，您必須：

> [!div class="checklist"]
> * 新增 [相容的圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切換至 [相容的電腦](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>此電腦的處理器無法搭配 Windows Mixed Reality

此電腦的處理器不支援 AVX/Popcnt 指示。 若要執行 Windows Mixed Reality，您必須：

> [!div class="checklist"]
> * 以[相容的圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)取代 
> * 切換至 [相容的電腦](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>這部電腦沒有足夠的可用磁碟空間來執行 Windows Mixed Reality

Windows Mixed Reality 需要 10 GB 的可用磁碟空間，才能安裝和獲得最佳效能。 清除磁片磁碟機上的一些空間，然後再次嘗試設定。

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>這部電腦正在執行不支援的 Windows 版本 Windows Mixed Reality

Windows Mixed Reality 可在[Windows 10 家用版](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab)和[Windows 10 專業版](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab)上運作。 您必須安裝其中一個版本，才能使用 Windows Mixed Reality。

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>這部電腦未執行最新版本的 Windows 10

Windows Mixed Reality 需要 Windows 10 Fall Creators Update。 請[更新您的電腦](https://support.microsoft.com/help/4028685)，然後再試一次。

### <a name="this-pc-has-no-usb-30-port"></a>這部電腦沒有 USB 3.0 埠

您將需要 USB 3.0 埠來連接 Windows Mixed Reality 耳機。 如果您使用的是桌上型電腦，請新增 PCIe USB 卡。 若為膝上型電腦，您必須切換至 [相容的電腦](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="you-cant-run-this-app-via-remote-desktop"></a>您無法透過遠端桌面執行此應用程式

若要使用 Windows Mixed Reality，您需要有連接到監視器的電腦。 如果您使用的是虛擬機器或沒有監視，請嘗試使用虛擬顯示器介面卡。 這是一部裝置，會插入電腦的 DisplayPort 並模擬電腦顯示。

## <a name="getting-the-best-performance"></a>取得最佳效能

某些硬體設定可能會導致 Windows Mixed Reality 的效能問題。 針對緩慢載入、不穩定的視覺效果或不良的視覺品質等問題，請嘗試下列常見的修正：

* 關閉任何在您電腦桌面上執行的開啟應用程式
* 如果您使用的是 USB 或 DisplayPort 至 HDMI 介面卡，請試著另一個。 查看建議的介面卡
* 如果有額外的監視器連接到電腦的圖形配接器，請將它們中斷連接
* 嘗試從 Windows 存放區下載一些不同的混合現實應用程式，有些應用程式可能更適合您的電腦設定
* 查看我們的 [效能問題檔](performance-questions.md)

如果您仍有效能問題，請更新下列[Windows Mixed Reality](set-up-windows-mixed-reality.md)設定，以獲得最佳的使用者體驗：

* 體驗
* 解決方法
* 畫面播放速率
* 校正

> [!NOTE]
> 如果您看到一則訊息，指出「此硬體設定可能與 Windows Mixed Reality 搭配運作，但尚未經過測試」，您可能會在執行長時間的 Windows Mixed Reality 時遇到一些效能問題。

## <a name="working-with-steamvr"></a>使用 SteamVR

享受 SteamVR 的遊戲是一個絕佳的方式，可體驗 VR 所提供的所有功能。 不過，您會想要確定您是從沉浸式裝置 [獲得最佳效能](performance-questions.md) 。 當 [您安裝了](https://store.steampowered.com/about)串流之後：

* 遵循[使用 SteamVR 搭配 Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)的指示
* 安裝 [SteamVR 效能測試](https://store.steampowered.com/app/323910/SteamVR_Performance_Test) 應用程式

## <a name="next-vr-checkpoint"></a>下一個 VR 檢查點

如果您正在遵循我們所配置的 VR 旅程圖，就幾乎準備好購買裝置。 從這裡開始，您可以在購買檢查點之前繼續進行最後一個步驟：

> [!div class="nextstepaction"]
> [購買常見問題](before-you-buy-faqs.md)

或直接跳到 [開始使用] 區段：

> [!div class="nextstepaction"]
> [設定 Windows Mixed Reality](set-up-windows-mixed-reality.md)

您隨時都可以回到 [VR 旅程](vr-journey.md) 。