---
title: Windows Mixed Reality電腦檢查應用程式
description: 如何在購買 Windows Mixed Reality 耳機之前，尋找並使用 Windows Mixed Reality pc 檢查應用程式來測試電腦的相容性。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、相容、相容性、電腦、系統需求
appliesto:
- Windows 10
ms.openlocfilehash: 463e7dfc2c95ed9efc70a87ebbb0dac08b134251401a1114f3b9a364aa197073
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188040"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality電腦檢查應用程式

**[Windows Mixed Reality pc 檢查](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** 應用程式是確保您的電腦已準備好執行 Windows Mixed Reality 的最佳方式。 Windows Mixed Reality PC 檢查應用程式僅適用于至少已安裝 Windows 10 1607 版的電腦。 若要檢查您的 Windows 版本，請在搜尋列中輸入 "winver"，然後執行命令。 針對早于1607的 Windows 10 版本，應用程式仍會顯示在存放區中，但您會在嘗試安裝時收到錯誤。

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

執行應用程式之後，您會收到下列其中一則訊息：

* **您已經準備好了。** 您的電腦有執行 Windows Mixed Reality 所需要的功能。
* **您幾乎在那裡。** 這台電腦可以執行 Windows Mixed Reality，但有些功能可能會受到限制。
* **無法執行混合的事實。** 此電腦不符合執行 Windows Mixed Reality 所需的最低需求。

然後，您將會針對所需的硬體、驅動程式和作業系統，取得電腦的分析。
![Windows Mixed Reality 電腦檢查的螢幕擷取畫面](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>圖示</th><th>代表的意義</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">您的電腦通過必要的專案。</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">您的電腦可能會因為指定的需求而發生問題。 如果遇到任何問題，您可能需要針對您的電腦進行疑難排解或升級。</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">您的電腦不符合指定專案的需求。</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>取得 Windows Mixed Reality 電腦檢查結果的協助

當您在電腦上設定 Windows Mixed Reality 或執行 Windows Mixed Reality PC 檢查應用程式時，將會收到相容性報告。 以下是您可能會看到的一些詳細資料。

### <a name="youre-good-to-go"></a>![您已經準備好了](images/glyph-succeeded.png)

好消息-您的電腦可以 Windows Mixed Reality 執行。 請記住，電腦硬體和設定之間仍有變化。 每台電腦上的混合現實體驗可能不相同。

>[!NOTE]
>如果您看到一則訊息，指出「此硬體設定可能與 Windows Mixed Reality 搭配運作，但尚未經過測試」，您可能會在執行長時間的 Windows Mixed Reality 時遇到一些效能問題。

### <a name="youre-nearly-there"></a>![您即將有](images/glyph-warning.png)

您的電腦應該可以執行 Windows Mixed Reality，但可能無法提供最佳體驗。 圖形可能會延遲，有些應用程式和遊戲可能無法正常執行，有些則可能無法執行。

以下是您可能會看到的訊息，以及如何處理這些訊息：

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>這部電腦有一個具有單一通道 RAM 的整合式圖形配接器

整合式圖形配接器可在具有雙重通道 RAM 的電腦上提供最佳的 Windows Mixed Reality 體驗。 如果您遇到效能問題：

* 安裝 [相容的離散圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。
* 安裝額外的 RAM 來建立雙聲道 RAM。
* 切換至 [相容的電腦](https://www.microsoft.com/windows/windows-mixed-reality-devices)。

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>這部電腦具有混合式圖形設定與不相容的 PCIe 連結

PCIe 代表 *周邊元件連接 Express*。 這是電腦用來與圖形配接器通訊的連接。 您的設定可能會運作，但如果遇到問題，您必須切換到 [相容的電腦](https://www.microsoft.com/windows/windows-mixed-reality-devices)。

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>此電腦的圖形驅動程式可能無法搭配 Windows Mixed Reality

如果您遇到問題，請嘗試使用 Windows Update 下載新的圖形驅動程式 (**開始 > 設定 > 更新 & 安全性 > 檢查更新**) -或移至您的電腦製造商或圖形配接器製造商的網站。

如果無法運作，您將需要新增 [相容的圖形配接器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 或切換至 [相容的電腦](https://www.microsoft.com/windows/windows-mixed-reality-devices)。

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>此電腦的處理器可能無法搭配 Windows Mixed Reality

此電腦的處理器可能無法與 Windows Mixed Reality 搭配運作，因為它沒有足夠的核心。 如果 Windows Mixed Reality 無法正常執行，請更新為[相容](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)的電腦，或切換至[相容的電腦](https://www.microsoft.com/windows/windows-mixed-reality-devices)。

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>這部電腦可能沒有相容的 USB 設定

如果您遇到執行 Windows Mixed Reality 的問題：

* 將您的耳機插入不同的 USB 埠（如果有的話）。
* 如果無法運作，請將您電腦的目前 USB 驅動程式卸載，然後重新安裝 Microsoft 驅動程式：

1. 選取 [開始]，然後在 [搜尋] 方塊中輸入「**裝置管理員** **」**。
1. 從結果中選取 [ **裝置管理員** ]。
1. 展開 [通用序列匯流排控制器] 的類別，查看列出的裝置，然後卸載任何不相容的驅動程式。 
 * 如果清單中包含「可延伸的主機控制器」專案，但裝置名稱結尾沒有 "Microsoft"，則驅動程式與 Windows Mixed Reality 不相容。 您必須將它卸載。 若要卸載驅動程式，請在清單中的裝置上按一下滑鼠右鍵，然後選取 [ **卸載裝置**]。 選取 [ **刪除此裝置的驅動程式軟體** ] 核取方塊，然後選取 [ **卸載**]。
 * 如果清單包含名稱中包含 "Etron" 的「可延伸主機控制器」專案，表示該 USB 控制器與 Windows Mixed Reality 不相容。 您必須在電腦上使用不同的 USB 埠，或購買不同的 USB 3.0 主機控制器。
1. 重新啟動電腦。 
1. 返回裝置管理員，然後再次找出可延伸的主機控制器專案。 如果您現在在裝置名稱的結尾看到「Microsoft」，您就可以開始了。 如果沒有，請重複執行卸載步驟，以移除任何其他非 Microsoft 版本的驅動程式。
* 如果仍然無法運作，請將 PCIe USB 卡新增至您的電腦。

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>這部電腦沒有適用于控制器的藍牙4.0。

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>這部電腦沒有自我供電的 USB 埠。

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>此電腦應該可以運作，但您將擁有高效能 Intel®處理器的最佳體驗。

### <a name="cant-run-mixed-reality"></a>![無法執行混合現實](images/glyph-error.png)

 [取得 Windows Mixed Reality 電腦檢查結果的協助](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
