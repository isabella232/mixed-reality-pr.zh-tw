---
title: 耳機顯示器常見問題
description: 針對出現在標準取用者支援檔之外的耳機顯示器問題，顯示 Windows Mixed Reality 疑難排解。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援
appliesto:
- Windows 10
ms.openlocfilehash: df91b6d131a8c2ce0faeecc659842418ef03c7c1
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132082"
---
# <a name="headset-display-faqs"></a>耳機顯示器常見問題

## <a name="my-headset-displays-are-black"></a>我的耳機顯示器是黑色

* 檢查您的電腦效能和穩定性：
    * 使用工作管理員查看是否有任何進程提高電腦的 CPU、GPU 及/或磁片磁碟機。
    * 檢查 **事件檢視器 > Windows 記錄** 檔中的「應用程式」和「系統」記錄，以查看您的應用程式經常損毀，並產生 WINDOWS 錯誤報告 (WER) 報告。
    * 請檢查 Windows Update，確定您的 Windows 版本是最新的。 您可能必須選取 [檢查更新] 多次。
* 檢查應用程式和遊戲穩定性：
    * 確定您的電腦符合最低系統需求，才能執行任何未正確執行的應用程式或遊戲。
    * 確定您的 GPU 驅動程式版本是最新的，並檢查是否有新的效能和相容性問題，以及是否有新驅動程式的回歸。
    * 如果您使用 SteamVR apps 和遊戲，請確定 SteamVR 和 SteamVR 元件的 Windows Mixed Reality 都是最新的。
* 檢查 HDMI 介面卡相容性：
    * 請確定 HDMI 纜線已插入所有的方式。
    * 如果您使用的是 HDMI 介面卡 (例如，迷你 DisplayPort 至 HDMI 介面卡) ，請確定其與 Windows Mixed Reality 相容。 介面卡必須支援 HDMI 2.0，而且有許多較舊的介面卡只支援1080p。 請參閱 [建議的 Windows Mixed Reality 配接器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)。
    * 外掛程式可能很重要。 先將 HDMI 介面卡連線到您的電腦，再將耳機連接到介面卡，特別是當您使用的是 USB 至 HDMI 介面卡時。
    * 如果您正在使用延伸模組纜線，請嘗試移除它。
* 檢查圖形配接器和驅動程式相容性：
    * 使用電腦監視器來嘗試您電腦的 HDMI 埠。 有些電腦可能會有一個以上的 HDMI 埠，並非全部都在作用中。
    * 如果您的電腦同時具有整合式圖形處理器 (iGPU) 和離散圖形處理單元 (dGPU) ，請確定您已插入 dGPU 的 HDMI 埠。
    * 再次檢查您的 GPU 驅動程式版本。 請確定它是最新的，但也請注意任何新的效能和相容性問題，以及對全新驅動程式的回歸。
    * 如果您在膝上型電腦上使用 Mixed Reality，並且從圖形配接器製造商的網站安裝了較新的圖形驅動程式，請嘗試降級為電腦製造商網站或 Windows Update 上提供的最新圖形配接器驅動程式。
    * 如果您有多部電腦監視器連接到您的電腦，請嘗試暫時中斷所有的電腦監視器，而不是一台電腦。
    * 如果您已為電腦監視器設定自訂的重新整理頻率，請嘗試暫時還原為標準的重新整理頻率，例如60Hz。
    * 如果您最近變更了您的圖形配接器，但未重新安裝 Windows，請檢查耳機監視器是否仍安裝正確的驅動程式。 當您的耳機插入電源時，請確認裝置管理員中的 [監視] 節點底下已列出 [混合現實耳機]。
    * 如果您的電腦有 Nvidia 圖形卡，請確定 Nvidia 的3D 視覺軟體已停用。
    * 在某些圖形配接器上 (特別舊的卡片) ，HDMI 埠可能不支援 HDMI 2.0，或可能無法完全與 Windows Mixed Reality 相容。 請嘗試使用您的圖形配接器 DisplayPort 搭配 [DisplayPort 1.2 至 HDMI 2.0 適配](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)卡。
    * Hp product number 1RJ99EA # 阿布達比的 HP Omen Pc 具有與 Windows Mixed Reality 不相容的 HDMI 埠 (開啟 [HP 支援助理]，此數目將會列在應用程式) 的底部。
    * 如果您的電腦有 AMD Junos r 9 系列圖形配接器，而您使用的是 Samsung Mixed Reality 耳機，請將耳機的固件更新為版本1.0.8 或更新版本，以使用您的圖形配接器的 HDMI 埠與耳機。
    * 如果您使用 Surface Book 2，請確定您使用的是 [SURFACE USB-C 至 HDMI 介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)。
* 檢查是否有混合現實耳機硬體問題：
    * 若要確認或排除耳機的硬體問題，請將您的混合現實耳機連接至另一台電腦。
    * 請先檢查電腦相容性和安裝程式問題，因為徵兆很類似。
* 請確定 USB 纜線已插入 USB 3.0 或更快的埠。 USB 3.0 埠具有 SS (的高度) ，而且通常彩色藍色。

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>我的耳機顯示器偶爾會在一些使用之後變成黑色

* 請嘗試在您的電腦上停用任何 USB 暫止或省電功能。 例如，在 [ **設定] > 系統 > 電源 & 睡眠 > [USB 選擇性暫停](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend)** ]、[允許電腦關閉此裝置以節省電源] 裝置管理員設定，以及您電腦的固件中的任何 USB 省電設定。
* 暫時中斷連接到您電腦的任何其他 USB 裝置和週邊設備。
* 檢查您的 GPU 驅動程式版本是否為最新版本，並檢查新的驅動程式是否有任何新的效能和相容性問題和回歸。

## <a name="one-of-the-displays-on-my-headset-is-black"></a>耳機中的其中一個顯示為黑色

* 如果您使用的是 HDMI 介面卡，請確定它支援 HDMI 2.0。
* 移除任何您可能使用的 USB 和 HDMI 擴充纜線。
* 請確定您的圖形驅動程式是最新的。
* 在另一部電腦上嘗試混合現實耳機。

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-re-initializes"></a>我的耳機會顯示 blue，然後混合實境入口重新初始化

這通常表示您的電腦上發生偶爾的 USB 控制器可靠性問題：

* 嘗試其他 USB 埠。 您的電腦可能有多個 USB 3.0 控制器。
* 如果適用)  (移除任何擴充纜線。
* 從您的電腦拔下所有其他 USB 裝置。
* 將外部驅動的 USB 3.0 中樞連接到您的電腦，並將您的耳機連接至中樞。
* 如果您使用的是桌上型電腦，請考慮購買 USB 3.0 PCIe 卡，以將另一個 USB 控制器新增至您的電腦。

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>我的耳機會導致電腦停止回應，或在啟動時顯示黑色畫面

在某些電腦上，將您的耳機保持在開啟狀態，然後重新開機您的電腦，可能會干擾其啟動流程。 您的電腦可以選取耳機顯示為「主要監視器」以顯示電腦的啟動進度、無法正常啟動，或「停止回應」及/或產生嗶聲錯誤碼。 此行為取決於 PC 製作和型號以及圖形配接器的製作和型號。 修正方法：

* 將您的耳機連接到您圖形配接器上的不同埠 (您可能需要使用介面卡來) 使用其他埠。
* 請確定電腦的 BIOS/UEFI 固件是最新的 (但如果您很熟悉) ，只會更新您電腦的 BIOS/UEFI 固件。

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>使用 Surface PC 時，我的電腦或耳機顯示器閃爍、閃爍或保持黑色

* 請確定您使用的是支援 HDMI 2.0 的 HDMI 介面卡。 許多較舊的 HDMI 介面卡僅支援1080p 解析度，這對混合現實耳機沒有足夠的支援。
* 請確定您的圖形驅動程式是最新的。 請查看 Windows Update 以及電腦製造商的網站，以取得更新的圖形驅動程式。
* 某些表面裝置與 Windows Mixed Reality 不相容。 深入瞭解 [介面相容性和需求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)。

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>我的耳機顯示器在關閉並快速啟動之後無法運作

從耳機拔下 HDMI 纜線和 USB 纜線，然後將其插回。

## <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>我的耳機顯示器很穩定，但混合實境入口的預覽視窗看起來沒問題

* 確定您的電腦系統資源 (CPU、記憶體和硬碟) 可供其他應用程式或進程使用。
* 更新您的圖形驅動程式。

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>我收到裝置管理員中的「安裝類別不存在或無效」錯誤

如果您在裝置管理員中看到有黃色驚嘆號的「HoloLens 感應器」，請選取裝置以取得其他詳細資料。 如果您看到一則訊息，指出「未安裝此裝置的驅動程式。  (代碼 28) --安裝類別不存在或無效」，這通常是因為您的電腦正在 [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)執行。請注意，N 版的 Windows 10 不支援 Windows Mixed Reality，而且您必須安裝 Windows 10 的非 N 版。

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>我的 WMR 環境在移動前端並顯示雙重視覺時，會抖動或口吃

在具有整合式圖形和 Nvidia GPU 的膝上型電腦上，會在一段時間後發生錯誤，導致先前的畫面格在下一個畫面格之後顯示，導致雙重視覺效果加快偏擺、音調或變換移動頭部的速度。 問題似乎是 Nvidia Graphics Driver 436.48 之後的驅動程式。  安裝此驅動程式將會修正此問題，直到 Nvidia 解決更新驅動程式中的問題為止。 如需直接安裝 Nvidia Graphics Driver 436.48，請造訪 [nvidia](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)。

## <a name="im-uncomfortable-in-my-headset"></a>我在耳機中感到不舒服

如需在 Windows Mixed Reality 中緩和的一般資訊，請參閱 [Windows Mixed Reality 沉浸式耳機健康情況、安全和緩和](wmr-health-safety-comfort.md)。 如需特定耳機的詳細資訊，請洽詢耳機製造商。

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>我要如何在我的耳機中取得更清楚的觀點

請嘗試調整您耳機的大小。 在您的臉部上向上和向下移動，或向左和向右移動，然後調整母線使其感覺箱子。

如果您的耳機有調整校正的旋鈕，請調整其校正設定。 如果不是，請移至 [ **設定] > Mixed reality > 視覺品質** ，並在該處調整校正。 如需有關特定裝置的校正的詳細資訊，請洽詢您的耳機製造商。

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>我經常在耳機周圍看到黑色框線。 有時候我會覺得通道

這表示應用程式無法在您的電腦上叫用畫面播放速率，而且系統會使用舊的畫面格來呈現耳機中的視圖。 由於應用程式只會轉譯您正在查看的世界部分，如果它們不會一直碰到畫面播放速率，系統會嘗試從先前的觀點來呈現世界，並以黑色填滿遺漏的詳細資料。 如果經常發生這種情況：

1. 關閉或終止所有不必要的程式，以釋放記憶體和 CPU。
2. 減少應用程式中的詳細資料設定。
3. 移至 [ **設定] > Mixed Reality > 耳機顯示** ，以減少 Windows Mixed Reality 首頁顯示的詳細資料量。

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>耳機中的觀點是 jittering，間斷情形很多

系統可能無法轉譯內容到耳機，或追蹤系統可能發生問題。 檢查下列項目：

1. 開啟工作管理員，以確定您的電腦有足夠的計算資源。 您應該有80% 的 CPU 可用、400MB 的 RAM，而磁片 IO 應低於80%。
2. 確定您擁有最新的硬體圖形驅動程式。 請參閱 [ [圖形驅動程式] 區段](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver)。
3. 請確定房間有足夠的光線。
4. 拔掉裝置，關閉 Windows Mixed Reality，然後重新插入。
5. 重新啟動電腦。
6. 如果問題持續發生，請洽詢 [客戶支援](https://support.microsoft.com/)。
