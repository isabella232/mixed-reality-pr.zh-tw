---
title: 開始之前
description: 如何確定您的電腦與 Windows Mixed Reality 相容，且可供使用。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、相容、相容性、入門、安裝程式、電腦、系統需求
appliesto:
- Windows 10
ms.openlocfilehash: b10fc9962d899b0a2c2ee15e6d039fc6bfb6d503
ms.sourcegitcommit: d8f39c0b95d9e61d645d64f27baabc7a1c300dc1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92293061"
---
# <a name="before-you-start"></a>在您開始使用 Intune 之前

## <a name="what-youll-need-to-run-windows-mixed-reality"></a>您需要執行的工作 Windows Mixed Reality

* Windows [Mixed Reality 前端裝載的顯示器 (HMD) ](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices)。
* Windows 10 1709 版或更新版本執行的新 [Windows Mixed Reality READY pc](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 或 Windows Mixed Reality 相容的電腦。
* 網際網路連接
* 如果未內建在耳機或電腦中，則顯示、USB 和藍牙介面卡 () 
* 移動控制器、Xbox 控制器或滑鼠和鍵盤
* 具有麥克風的耳機 (如果您的 HMD 沒有內建) 
* 大型的開放空間

## <a name="make-sure-your-pc-is-compatible-with-windows-mixed-reality"></a>請確定您的電腦與 Windows Mixed Reality 相容

若要查看您的電腦是否 Windows Mixed Reality 相容，請檢查 [Windows Mixed Reality 的最小電腦硬體需求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ，或在您的電腦上執行 [Windows Mixed Reality 入口網站](install-windows-mixed-reality.md#launch-mixed-reality-portal) 。

如需有關電腦相容性問題的詳細資訊，請移至 [這裡](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)。

## <a name="make-sure-you-have-the-windows-10-version-1709-or-newer-installed"></a>請確定您已安裝 Windows 10 1709 版或更新版本

您必須執行 Windows 10 版本 1709 (「建立建立者」更新) 或更新版本，才能使用 Windows Mixed Reality。 Windows 10 的相容版本包括：
* Windows 10 1709 版 (秋季建立者更新、組建 16299) 
* Windows 10 1803 版 (春季 Update，組建 17134) 
* Windows 10 1809 版 (10 月更新，組建 17763) 

若要查看您的裝置目前執行的 Windows 10 版本，請選取 [ **開始** ] 按鈕，然後選取 [ **系統 > > 的設定**。

若要確保電腦上的 Windows 10 為最新狀態，請選取 [ **開始** ] 按鈕，然後選取 [ **設定] > 更新 & 安全性 > Windows Update**。  選取 [檢查更新]。 如果有可用的更新，請加以安裝。

如需如何讓電腦保持在最新狀態的詳細資訊，請移至 [這裡](https://support.microsoft.com/en-us/help/12373/windows-update-faq)

## <a name="make-sure-your-pc-is-connected-to-the-internet"></a>確定您的電腦已連線到網際網路

檢查您的電腦是否已連線到網際網路。 您將需要下載驅動程式和一些額外的軟體，才能讓 Windows Mixed Reality 啟動並執行。  如果您的 Wi-Fi 網路連線設定為 [計量付費]，請將其變更為 [未計量]。 [深入了解](https://support.microsoft.com/en-us/help/4028458/windows-metered-connections-in-windows-10)。

## <a name="make-sure-you-have-a-compatible-graphics-driver"></a>確定您有相容的圖形驅動程式

您的電腦必須有 WDDM 2.2 或更新版本的圖形驅動程式，才能完成 Windows Mixed Reality 安裝程式。 如果它還沒有相容的圖形驅動程式，請嘗試下列來源：

* 使用 Windows Update 檢查是否有最新的重要驅動程式更新 (**開始 > Windows 設定 > 更新和安全性 > 檢查更新**) 
* 檢查是否有最新的選用驅動程式更新：
    1. 以滑鼠右鍵按一下 [ **開始] > 裝置管理員**]。
    2. 展開 [ **顯示介面卡**]。
    3. 以滑鼠右鍵按一下圖形配接器，然後選擇 [ **更新驅動程式] > 自動搜尋更新的驅動程式軟體**。
* 檢查您電腦的製造商 (OEM) 的網站。
* 請在您的電腦上查看圖形配接器製造商的網站 (例如 AMD、Intel 或 NVIDIA) 。

## <a name="make-sure-that-you-have-any-required-adapters"></a>請確定您有任何必要的介面卡

您 Windows Mixed Reality 相容的電腦可能沒有連線到沉浸式耳機所需的全尺寸 HDMI 和 USB 3.0 埠。 或者，您可能需要藍牙介面卡，才能符合 Windows Mixed Reality 入口網站需求。  如果是這種情況，您將需要介面卡來連接耳機和移動控制器。 請務必檢查 [您可能需要的介面卡類型清單，以及特定介面卡型號的一些建議](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)。

## <a name="make-sure-that-you-have-input-devices"></a>請確定您有輸入裝置

Windows Mixed Reality 的設計最適合搭配 Windows Mixed Reality 的動作控制器使用，可提供自然、精確的互動，而不需要在您的牆上安裝硬體。 但是您也可以使用 Xbox 控制器或滑鼠和鍵盤。

## <a name="get-headphones-if-your-headset-didnt-come-with-them"></a>如果您的耳機未隨附耳機，請取得耳機

除非您購買了 Samsung HMD 電影對白、HP 回音或 (HP 吐，且已整合 AKG 耳機和整合的雙重陣列麥克風) ，否則您將需要取得一組耳機的音訊耳機，以插入 HMD 的 headset's 3.5 mm 音訊插孔。

## <a name="make-sure-that-you-have-a-large-open-space"></a>確定您有很大的開放空間

如果您想要在使用 Windows Mixed Reality 時四處移動，您需要有一個大型的開放空間。  在安裝期間，系統會要求您選擇「坐即站」或「所有體驗」。 如果您想要四處移動，請選擇 [所有體驗] 並設定界限。 請參閱 [沉浸式耳機健康狀態、安全和緩和方針，](wmr-health-safety-comfort.md) 以瞭解空間需求。

### <a name="seated-and-standing-no-boundary"></a>固定 (沒有界限) 

如果您選取 [站上和站上]，將會使用沒有界限的耳機。 這表示當您使用耳機時，必須保持在一個位置，如此您就可以避免發生實體障礙並產生風險。 您可以坐住或保持在一起，但不應該四處移動。 某些應用程式可能是設計來搭配界限使用，因此您可能無法使用它們，如果您不使用界限，則可能不會有相同的體驗。

### <a name="all-experiences-boundary"></a> (界限的所有體驗) 

如果您選擇 [所有體驗]，您將會設定界限，而且您將可以四處移動和使用應用程式和體驗，而這些應用程式和使用的界限以及不需要使用的體驗。 您將需要準備空間，以確保您將使用的區域中沒有阻礙、危險或脆弱的專案 (包括在您的 head) 的上方。 請勿在樓梯的頂端，或在額外的低上限風扇下設定。 從區域中移除 breakables 和阻礙，並確定您和使用耳機的任何人都能閱讀並瞭解 [安全指導方針](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)。

## <a name="see-also"></a>另請參閱

* [插入您的 HMD](plug-in-your-headset.md)
* [最小電腦硬體需求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* [建議的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)