---
title: Windows Mixed Reality電腦相容性指導方針
description: 總覽圖表列出與 Windows Mixed Reality 相容性的最低電腦系統需求。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，Ultra，相容，相容性，系統需求，電腦
appliesto:
- Windows 10
ms.openlocfilehash: b7c2b4b84440e7cdd22c2c0cd7d5f9830d55625f
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757028"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality 最小電腦硬體相容性指導方針

![電腦相容性主圖影像](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>功能和經驗

Windows 10 在一組不同的電腦硬體上，Windows Mixed Reality 各種耳機。  您電腦的威力將決定您可以擁有的體驗。
在較高的終端機中，您可以取得一些額外的功能和功能：

* 更鮮亮的視覺效果和更新率更高。
* 更多應用程式和體驗，包括最需要大量圖形的遊戲。
* 桌面上的「' 鏡像 '」視窗，顯示您在混合現實中看到的內容。
* 記錄及分享您混合現實體驗的影片和相片。

## <a name="minimum-pc-hardware-guidelines"></a>最低電腦硬體指導方針

查看下列硬體指導方針並執行[混合實境入口](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)應用程式，以查看您的電腦是否可以執行 Windows Mixed Reality。

請記住，您的效能將視確切的設定而有所不同。 您也必須確定您的電腦具有適用于您所使用之 Windows Mixed Reality 沉浸式耳機的[正確埠](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)。

>[!NOTE]
>開發電腦的指導方針高於執行混合現實應用程式之取用者電腦的指導方針。 如果您是混合現實開發人員， [請參閱建議的開發電腦規格](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)。

## <a name="mixed-reality-portal-app"></a>混合實境入口應用程式

[混合實境入口](https://www.microsoft.com/store/productid/9ng1h8b3zc7m)是確保您的電腦已準備好執行 Windows Mixed Reality 的最佳方式。

執行應用程式之後，您會收到下列其中一則訊息：

* **您已經準備好了。**  您的電腦已準備好執行混合的現實遊戲和體驗。
* **支援某些功能。** 您的電腦可以執行一些混合的現實體驗。
* **無法執行混合的事實。** 此電腦不符合執行 Windows Mixed Reality 所需的最低需求。

然後，您將會針對所需的硬體、驅動程式和作業系統，取得電腦的分析。
![Windows Mixed Reality 電腦檢查的螢幕擷取畫面](images/screenshot-mr-pc-check.jpg)

<table>
<tr>
<th>圖示</th><th>代表的意義</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">您的電腦通過必要的專案。</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">您的電腦可能會因為指定的需求而發生問題。 如果您遇到問題，您可能需要針對您的電腦進行疑難排解或升級。</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">您的電腦不符合指定專案的需求。</td>
</tr>
</table>

 [取得混合實境入口結果的協助](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>相容性指導方針

> [!IMPORTANT]
> 我們將會更新，並新增至，而且可能會修訂這些 Windows Mixed Reality 電腦相容性指導方針。 請定期回來查看最新的指導方針和需求。

### <a name="high-resolution-headset-requirements"></a>高解析度耳機需求

因為解析度較高，所以下列需求適用于 HP 的「回音」 G1、G2 和 Omnicept 產品線，以確保最佳的 90 Hz、完整的解析度體驗：

<ul>
<li> Intel Core i5、i7、Intel （r） E3-1240 v5，相當於或更好。 AMD Ryzen 5 等於或更好。 </li>
<li> NVIDIA GeForce GTX 1080、AMD Radeon RX 5700、等於或更佳 </li>
<li> 記憶體： 8 GB RAM 或更多 </li>
<li> 1x 顯示埠1。3 </li>
<li> 具有電源傳遞的 1x USB 3.0 類型-C (或包含的電源配接器) </li>
<li> Windows 105月2019更新或更新版本 </li>
</ul>

**所有其他 WMR 相容的耳機** <br>
針對所有其他 Hmd，請參閱下列需求：

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 90Hz 的電腦</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 60hz 電腦</th>
</tr><tr>
    <td style="vertical-align: middle">作業系統</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) 或更新版本-首頁、Pro、商務、教育。<br/>     (<b>附注</b>： N 版或 S 模式中的 Windows 10 專業版不支援) </td>
</tr><tr>
    <td style="vertical-align: middle">處理器</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (第4代) 、四核心 (或更好的)  <br>AMD Ryzen 5 1400 3.4 Ghz (桌面) 、四核心 (或更好的) </td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (第7代的行動) 、已啟用 Intel Hyper-Threading 技術的雙核心 (或更好的)  <br>AMD Ryzen 5 1400 3.4 Ghz (桌面) 、四核心 (或更好的) </td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (或更佳) </td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 雙重通道 (或更佳) </td>
</tr><tr>
    <td style="vertical-align: middle">可用磁碟空間</td>
    <td style="vertical-align: middle; text-align: center;">至少 10 GB</td>
    <td style="vertical-align: middle; text-align: center;">至少 10 GB</td>
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
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows顯示驅動程式模型 (WDDM) 2。2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">圖形顯示埠</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2.0 或 DisplayPort 1。2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1.4 或 DisplayPort 1。2</td>
</tr><tr>
    <td style="vertical-align: middle">顯示</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">連接的外部或整合式 VGA (800x600) 顯示 (或更好的) </td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">USB 連線能力</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 </td>
</tr><tr>
    <td style="vertical-align: middle">藍牙<a href="controllers-in-wmr.md">動作控制器</a>的連接 () </td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">藍牙4。0</td>
</tr><tr>
    <td style="vertical-align: middle">預期的耳機幀率</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">電源</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 埠</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 埠</td>
</tr>
</table>

**其他資訊:**

* 具有至少15個畫面的較大型膝上型電腦最適合。
* 混合式圖形設定只與 Windows Mixed Reality 90Hz 相容。 任何混合式設定中的離散圖形介面卡，都必須符合在個別圖形介面卡的 Windows Mixed Reality 指導方針中列出的所有需求。
* 如果您有不應該執行 Windows Mixed Reality 90Hz 的離散圖形配接器，但預設為每秒 60hz (60 畫面格) 重新整理頻率，請使用 DisplayPort 到 HDMI 2.0 介面卡的全形來插上耳機並啟用90Hz 重新整理頻率。
* 不同的耳機可能需要不同的硬體埠，因此請確定您的電腦具有正確的埠或 [需要的介面卡](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) ，才能連接到您的耳機。

>[!NOTE]
>不符合最低確認規格的離散與整合式圖形硬體尚未針對 Windows Mixed Reality 進行測試、確認或優化，而且可能無法正常運作或完全無法正常運作。

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality 和介面

為了在 Surface 裝置上獲得最佳 Windows Mixed Reality 體驗，我們建議使用最新的 SurfaceBook (15」 ) 至少設定 NVIDIA GeForce GTX 1060 GB 和 16 GB 的 RAM。  此設定支援所有 Windows Mixed Reality 功能，並已針對 Windows Mixed Reality 進行測試。  最新的 Surface Book (13.5」 ) 、Surface Studio、Surface Laptop 和 Surface Pro (2017) 在使用 Intel Core i5 CPU 進行設定時，將會支援一些 Windows Mixed Reality 功能 (或更好的) 和至少 8 GB 的 RAM。

**需求：**

* Surface 產品需要驅動程式更新，才能與 Windows Mixed Reality 相容。 您可以在介面上安裝這些驅動程式，方法是前往 **設定 > 更新和安全性 > 檢查是否有更新**。
* surface 產品需要從影片埠 (迷你 DisplayPort 或 USB-C 的[介面卡](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md)，視 surface PC) 至 Windows Mixed Reality 耳機的 HDMI 2.0 而定。 最新版本的介面 Mini-DisplayPort 至 HDMI AV 介面卡與 HDMI 2.0 相容 (舊版不) 。 同樣地， <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB-C 至 Hdmi 介面卡</a> 也與 hdmi 2.0 相容。

## <a name="see-also"></a>另請參閱

* [詢問社群](https://answers.microsoft.com)
* [與我們聯繫以取得支援](https://support.microsoft.com/contactus/)
* [適用于 Windows Mixed Reality 功能的電腦的建議介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
