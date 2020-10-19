---
title: Windows Mixed Reality 最小電腦硬體相容性指導方針
description: 此圖表概述與 Windows Mixed Reality 相容性的最小電腦系統需求。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，Ultra，相容，相容性，系統需求，電腦
appliesto:
- Windows 10
ms.openlocfilehash: e21d2d18edbf2c94d156f14fa8c2598822a8bc7a
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174368"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality 最小電腦硬體相容性指導方針

## <a name="features-and-experiences"></a>功能和經驗

Windows 10 Windows Mixed Reality 和 Windows Mixed Reality Ultra。 您所體驗的版本取決於您的電腦硬體。

有了 Windows Mixed Reality Ultra，您就可以取得一些額外的功能和功能：

* 更鮮亮的視覺效果和較高的重新整理頻率 (每秒90個畫面格) 。
* 更多應用程式和體驗，包括最需要大量圖形的遊戲。
* 桌面上的「' 鏡像 '」視窗，顯示您在混合現實中看到的內容。
* 記錄和分享影片 (以及混合現實體驗的相片) 。

## <a name="minimum-pc-hardware-guidelines"></a>最低電腦硬體指導方針

為了獲得 Windows Mixed Reality 的最佳體驗，請從可提供 Windows Mixed Reality Ultra 體驗的新 [Windows Mixed Reality 就緒電腦](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 或 Windows Mixed Reality 相容的電腦開始。 Windows Mixed Reality Ultra 以較高的重新整理率提供更佳的視覺效果、更多應用程式和體驗，包括最需要大量圖形的遊戲、在桌上型電腦上鏡像您的 Windows Mixed Reality 體驗，以及能夠錄製和共用 (的相片和影片，) 您與他人的體驗。 

若要查看您的電腦是否可以執行 Windows Mixed Reality 請參閱下方的硬體指導方針，並執行 [混合實境入口應用程式](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)。

請記住，您的效能將視確切的設定而有所不同。 您也必須確定您的電腦具有適用于您所使用之 Windows Mixed Reality 沉浸式耳機的 [正確埠](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 。

>[!NOTE]
>開發電腦的指導方針高於執行混合現實應用程式之取用者電腦的指導方針。 如果您是混合現實開發人員， [請參閱建議的開發電腦規格](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)。


## <a name="mixed-reality-portal-app"></a>混合實境入口應用程式

混合實境入口是確保您的電腦已準備好執行 Windows Mixed Reality 的最佳方式。 

<a href="https://www.microsoft.com/store/productid/9ng1h8b3zc7m"><img alt="Download Mixed Reality Portal" src="images/WMR-PC-Check-app.png"/></a>

執行應用程式之後，您會收到下列其中一則訊息：
* **您已經準備好了。** 您的電腦有執行 Windows Mixed Reality 所需要的功能。
* **支援某些功能。** 這台電腦可以執行 Windows Mixed Reality，但有些功能可能會受到限制。
* **無法執行混合的事實。** 此電腦不符合執行 Windows Mixed Reality 所需的最低需求。

然後，您將會針對所需的硬體、驅動程式和作業系統，取得電腦的分析。
![Windows Mixed Reality PC Check 的螢幕擷取畫面](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>圖示</th><th>代表的意義</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">您的電腦通過必要的專案。</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">您的電腦可能會因為指定的需求而發生問題。 如果您遇到問題，可能需要針對您的電腦進行疑難排解或升級。</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">您的電腦不符合指定專案的需求。</td>
</tr>
</table>

 [取得混合實境入口結果的協助](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

## <a name="compatibility-guidelines"></a>相容性指導方針
> [!IMPORTANT]
> 我們將會更新，並新增至，而且可能會修訂這些 Windows Mixed Reality 電腦相容性指導方針。 請定期回來查看最新的指導方針和需求。

**HP 回音相容規格**<br>
由於解析度更高，因此下列需求適用于 HP 回條 G1 & G2 產品線，以確保最佳90Hz、完整解析度體驗： 

<ul>
<li> Intel Core i5、i7、Intel Xenon E3-1240 v5，相當於或更好。 AMD Ryzen 5 等於或更好。 </li>
<li> NVIDIA GeForce GTX 1080、AMD Radeon RX 5700、等於或更佳 </li> 
<li> 記憶體： 8 GB RAM 或更多 </li> 
<li> 1x 顯示埠1。3 </li> 
<li> 具有電源傳遞的 1x USB 3.0 類型-C (或包含的電源配接器) </li>
<li> Windows 10 可能是2019更新或更新版本 </li>
</ul>

**所有其他 WMR 相容的耳機** <br>
針對所有其他 HMD，請參閱下列需求： 

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality Ultra 電腦</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 電腦</th>
</tr><tr>
    <td style="vertical-align: middle">作業系統</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) 或更新版本-家用版、專業版、商務版、教育版。<br/>     (<b>附注</b>： N 版或 S 模式中的 Windows 10 專業版不支援) </td>
</tr><tr>
    <td style="vertical-align: middle">處理器</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (第4代) 、四核心 (或更好的)  <br>AMD Ryzen 5 1400 3.4 Ghz (桌面) 、四核心 (或更好的) </td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (第7代的行動) 、已啟用 Intel Hyper-Threading 技術的雙核心 (或更好的)  <br>AMD Ryzen 5 1400 3.4 Ghz (桌面) 、四核心 (或更好的) </td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8GB DDR3 (或更佳) </td>
    <td style="vertical-align: middle; text-align: center;">8GB DDR3 雙重通道 (或更佳) </td>
</tr><tr>
    <td style="vertical-align: middle">可用磁碟空間</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">至少 10 GB</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">至少 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">顯卡</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul> 
            <li>NVIDIA GTX 1060 (或更高) 具有 DX12 功能的離散 GPU</li>
            <li>AMD RX 470/570 (或更高) DX12 支援的離散 GPU </li>
            </ul>     
            <b>注意：</b> GPU 必須裝載于 PCIe 3.0 x4 + 連結插槽 </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>整合 Intel HD 圖形 620 (或更高) DX12 支援的整合 GPU <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units"> (檢查您的模型是否更大) </a></li>
        <li>NVIDIA MX150 (或更高) 離散 GPU</li>
        <li>Nvidia GeForce GTX 1050 離散 GPU</li>
        <li>Nvidia 965M 離散 GPU</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>注意：</b> 不支援較舊的 Intel Gpu，例如 HD 圖形4xx、5xx、2xxx、3xxx、4xxx、5xxx 和6xxx。
    </td>
</tr><tr>
    <td style="vertical-align: middle">圖形驅動程式</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows 顯示驅動程式模型 (WDDM) 2。2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">圖形顯示埠</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2.0 或 DisplayPort 1。2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1.4 或 DisplayPort 1。2</td>
</tr><tr>
    <td style="vertical-align: middle">顯示</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">連接的外部或整合式 VGA (800x600) 顯示 (或更好的) </td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">USB 連線能力</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 類型-A </td>
</tr><tr>
    <td style="vertical-align: middle">適用于 <a href="controllers-in-wmr.md">動作控制器</a> 的藍牙連線 () </td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">藍牙4。0</td>
</tr><tr>
    <td style="vertical-align: middle">預期的耳機幀率</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">電源</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 (輸入) 埠</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 (輸入) 埠</td>
</tr>
</table>



**其他資訊:**
* 較大的膝上型電腦 (至少有15個的畫面 ) 執行效能最佳。
* 為了獲得最佳體驗，我們建議使用第8代 Intel® Core™或7個 Gen Intel® Core™ i5 處理器。
* 混合式圖形設定只與 Windows Mixed Reality Ultra 相容。 任何混合式設定中的離散圖形介面卡，都必須符合在個別圖形介面卡的 Windows Mixed Reality 指導方針中列出的所有需求。
* 如果您有不應該執行 Windows Mixed Reality Ultra 的離散圖形配接器，但預設為 60 Hz (60 每秒畫面格) 重新整理頻率，請使用完整大小的 DisplayPort 至 HDMI 2.0 介面卡，以插上耳機並啟用 90 Hz 的更新速率。
* 不同的耳機可能需要不同的硬體埠，因此請確定您的電腦具有正確的埠或 [需要的介面卡](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) ，才能連接到您的耳機。

>[!NOTE]
>不符合最低確認規格的離散與整合式圖形硬體尚未針對 Windows Mixed Reality 進行測試、確認或優化，而且可能無法正常運作或完全無法正常運作。

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality 和介面

為了在 Surface 裝置上獲得最佳 Windows Mixed Reality 體驗，我們建議使用 NVIDIA GeForce GTX 1060 和 RAM 的設定 SurfaceBook 2 () 15」。  此設定支援所有的 Windows Mixed Reality 功能90Hz，並已針對 Windows Mixed Reality Ultra 進行測試和徽章。  Surface Book 2 (13 ") 、Surface Studio、Surface Laptop 和 Surface Pro (2017) 將在設定 Intel Core i5 CPU Windows Mixed Reality 或更好的 (，以及至少有 8 GB 的 RAM 時，支援一些) 功能。

**需求：**
* Surface 產品需要驅動程式更新，才能與 Windows Mixed Reality 相容。 您可以前往 [ **設定] > 更新和安全性] > 檢查是否有更新，** 將這些驅動程式安裝在您的介面上。
* Surface 產品需要從影片埠 (迷你 DisplayPort 或 USB-C 的 [介面卡](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) ，視 surface PC) 至 Windows Mixed Reality 耳機的 HDMI 2.0 而定。 最新版本的介面 Mini-DisplayPort 至 HDMI AV 介面卡與 HDMI 2.0 相容 (舊版不) 。 同樣地， <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB-C 至 Hdmi 介面卡</a> 也與 hdmi 2.0 相容。

>[!WARNING]
>並非所有迷你 DisplayPort 或 USB 至 HDMI 介面卡都可支援 HDMI 2.0。 請考慮在任何介面卡上檢查是否有明確的「HDMI 2.0」相容性或「4K」相容性。

下表提供與 Windows Mixed Reality 介面相容性的詳細資訊：

<table>
    <tr>
        <th> Surface 裝置 </th><th> Windows Mixed Reality 功能支援？ </th><th> 建議組態 </th><th> 注意</th>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (原始) /Surface Pro 2 </td><td style="vertical-align: middle"> 無 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro 3 </td><td style="vertical-align: middle"> 無 </td><td> </td><td></td>
    </tr>
 (已安裝 Windows 10 專業版)  <tr>
        <td style="vertical-align: middle"> Surface Pro 4 </td><td style="vertical-align: middle"> 無 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface 3 </td><td style="vertical-align: middle"> 無 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book </td><td style="vertical-align: middle"> 無 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> 使用效能基底的 Surface Book </td><td style="vertical-align: middle"> 無 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Go </td><td style="vertical-align: middle"> 無 </td><td> </td><td></td>
    </tr>
<tr>
        <td style="vertical-align: middle"> Surface Book 2 (15 &quot;)  </td><td style="vertical-align: middle"> 完整 </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1060/4 GB 的 RAM </td>
        <td>
            <ul>
                <li><b>建議</b>：若要在 Surface 裝置上獲得最佳 Windows Mixed Reality 體驗，建議您將 SurfaceBook 2 15」設定為 NVIDIA GeForce GTX 1060 和 RAM 的 16 gb。  這項設定經過測試並徽章為 Windows Mixed Reality Ultra 因此將支援所有 Windows Mixed Reality 功能，並可讓您享受最廣泛的相容應用程式和遊戲陣列。</li>
                <li>NVIDIA GeForce GTX 1060 離散 GPU 將提供 Windows Mixed Reality Ultra @ 90Hz 體驗</li><br/>                <li>為了達到最佳效能，請使用特別針對 Surface Book 2 發行的 Nvidia 圖形驅動程式。 新的驅動程式可能適用于 Nvidia&#39;的網站，但尚未測試。</li><br/>                <li>需要 <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB-C 至 HDMI 介面卡</a> (其他介面卡可能可以運作，但尚未測試) </li>
                <li><b>注意：在 Surface dock 上</b>：由於介面停駐的電源供應限制，Windows Mixed Reality 不會正式支援使用 Surface Book 2 的 Surface dock。</li><br/>                <li><b>請注意 Windows 10 版本 1803</b>：如果您&#39;重新執行 Windows 10 1803 版，請確定您&#39;重新開啟 KB4284848 (所安裝的 OS 組建17134.137 或更新版本) ，以確保您有最新的效能修正。 如需詳細資訊，請參閱 <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>的版本資訊。</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book 2 (13.5 &quot;)  </td><td style="vertical-align: middle"> Partial </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1050/4 GB 的 RAM </td>
        <td>
            <ul>
                <li><b>注意</b>： Surface Book 2 (13 ") 不會針對 Windows Mixed Reality 徽章，但會支援一些 Windows Mixed Reality 功能，可讓您使用有限數目的相容應用程式和遊戲。  效能將視您的設定而定。</li>
                <li>具有 Intel Core i5/Intel HD Graphics 620 整合式 GPU 的設定將提供 Windows Mixed Reality @ 60Hz 體驗</li>
                <li>具有 Intel 核心 i7/NVIDIA GeForce GTX 1050 離散 GPU 的設定將會提供 Windows Mixed Reality @ 90Hz 體驗</li>                       <li>為了達到最佳效能，請使用特別針對 Surface Book 2 發行的 Nvidia 圖形驅動程式。 新的驅動程式可能適用于 Nvidia&#39;的網站，但尚未測試。</li>
                <li>需要 <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB-C 至 HDMI 介面卡</a> (其他介面卡可能可以運作，但尚未測試) </li>
                <li><b>注意：在 Surface dock 上</b>：由於介面停駐的電源供應限制，Windows Mixed Reality 不會正式支援使用 Surface Book 2 的 Surface dock。</li>
                <li><b>請注意 Windows 10 版本 1803</b>：如果您&#39;重新執行 Windows 10 1803 版，請確定您&#39;重新開啟 KB4284848 (所安裝的 OS 組建17134.137 或更新版本) ，以確保您有最新的效能修正。 如需詳細資訊，請參閱 <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>的版本資訊。</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Studio </td><td style="vertical-align: middle"> Partial </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GeForce GTX 980m/4 GB 的 RAM </td>
        <td>
            <ul>
                <li><b>注意</b>： Surface Studio 不會針對 Windows Mixed Reality 徽章，但會支援一些 Windows Mixed Reality 功能，讓您可以使用有限數目的相容應用程式和遊戲。  效能將視您的設定而定。</li>
                <li>具有 NVIDIA GeForce GTX 965m 的設定將會提供 Windows Mixed Reality @ 60Hz 體驗。</li>
                <li>NVIDIA GeForce GTX 980m 的設定將會提供 Windows Mixed Reality @ 90Hz 體驗。</li>
                <li>Surface 迷你 DisplayPort 至 HDMI 2.0 介面卡 (其他介面卡可能可以運作，但未經過測試) </li>
                <li>Windows Mixed Reality 耳機必須連接到具有 "+" 符號的 USB 埠</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (2017)  </td><td style="vertical-align: middle"> Partial </td><td style="vertical-align: middle"> Intel Core i7/Intel®鳶尾花™外加圖形 640/16 GB 的 RAM </td>
        <td>
            <ul>
                <li><b>注意</b>： Surface Pro (2017) 不會針對 Windows Mixed Reality 徽章，但會支援一些 Windows Mixed Reality 功能，可讓您使用有限數目的相容應用程式和遊戲。  效能將視您的設定而定。</li>
                <li><b>不支援</b>使用 Intel Core M3/Intel HD Graphics 615 整合式 GPU 的設定</li>
                <li>具有 Intel Core i5/Intel HD Graphics 620 整合式 GPU 的設定將提供 Windows Mixed Reality @ 60Hz 體驗</li>
                <li>具有 Intel 核心 i7/Intel®鳶尾花™加上圖形640整合式 GPU 的設定將提供 Windows Mixed Reality @ 60Hz 體驗</li><br/><li>需要 Surface 迷你 DisplayPort 至 HDMI 2.0 介面卡 (其他介面卡仍可運作，但未經過測試) </li>
                <li>使用期間，需要將 <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">效能滑杆</a> 設定為「最佳效能」</li>
            </ul>
        </td>
    </tr><br/>    <tr>
        <td style="vertical-align: middle"> Surface Laptop </td><td style="vertical-align: middle"> Partial </td><td style="vertical-align: middle"> Intel Core i7/Intel®鳶尾花™外加圖形 640/16 GB 的 RAM </td>
        <td>
            <ul>
                <li><b>注意</b>： Surface Laptop 不會針對 Windows Mixed Reality 徽章，但會支援一些 Windows Mixed Reality 功能，讓您可以使用有限數目的相容應用程式和遊戲。  效能將視您的設定而定。</li>
                <li><b>不支援</b>使用 Intel Core M3/Intel HD Graphics 615 整合式 GPU 的設定</li>
                <li>具有 Intel Core i5/Intel HD Graphics 620 整合式 GPU 的設定將提供 Windows Mixed Reality @ 60Hz 體驗</li>
                <li>具有 Intel 核心 i7/Intel®鳶尾花™加上圖形640整合式 GPU 的設定將提供 Windows Mixed Reality @ 60Hz 體驗</li><br/><li>需要 Surface 迷你 DisplayPort 至 HDMI 2.0 介面卡 (其他介面卡仍可運作，但未經過測試) </li>
                <li>使用期間，需要將 <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">效能滑杆</a> 設定為「最佳效能」</li>
            </ul>
        </td>
    </tr>
</table>

## <a name="see-also"></a>另請參閱
* [詢問社群](https://answers.microsoft.com)
* [與我們聯繫以取得支援](https://support.microsoft.com/contactus/)
* [適用于 Windows Mixed Reality 功能的電腦的建議介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
