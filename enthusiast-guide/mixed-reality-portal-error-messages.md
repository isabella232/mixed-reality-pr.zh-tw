---
title: 混合實境入口錯誤訊息
description: 超越標準取用者支援檔的 Advanced Windows Mixed Reality 入口網站訊息疑難排解。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援、混合實境入口
appliesto:
- Windows 10
ms.openlocfilehash: c85030da129d90bb0a150ad50a6990e30b68c21bc7a3899c4182e87acd4b4fa5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186868"
---
# <a name="mixed-reality-portal-error-messages"></a>混合實境入口錯誤訊息

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>我收到「錯誤」的錯誤訊息，或混合實境入口發生問題。

重新開機 Windows Mixed Reality：
1. 從電腦中斷連接耳機纜線。
2. 重新啟動電腦。
3. 重新連接您的耳機。

如果無法運作，請確定您的電腦能夠辨識您的耳機：
1. 選取 [啟動]。
2. 在搜尋方塊中輸入「裝置管理員」，並在清單中選取它。 
3. 展開 [混合現實裝置]，並查看是否已列出您的耳機。 

如果未列出：
1. 將耳機插入電腦上的不同埠（如果有的話）。
2. 從 Windows Update 檢查是否有最新的軟體更新。
3. 卸載並重新安裝 Windows Mixed Reality：
    1. 從電腦中斷連接耳機纜線。
    2. 選取 **設定 > 混合現實 > 卸載**]。
    3. 選取 **設定 > 裝置 > 藍牙 & 其他裝置** 將您的動作控制器。 選取每個控制器，然後選取 [移除裝置]。
    4. 將您的耳機插回電腦以重新安裝 Windows Mixed Reality。
    
## <a name="im-getting-a-check-your-usb-cable-error-message"></a>我收到「檢查您的 USB 纜線」錯誤訊息。

連線您的耳機至不同的 USB 埠 (，並確定它是 SuperSpeed USB 3.0) 。 此外，請嘗試移除耳機與電腦之間的任何擴充項或中樞。

## <a name="im-getting-a-check-your-display-cable-error-message"></a>我收到 [檢查您的顯示器纜線] 錯誤訊息。

使用下列步驟來針對問題進行疑難排解：
* 連線您的耳機至 DisplayPort 1.2 或更新版本，或 HDMI 1.4 或更新版本。 請確定埠與您電腦上最先進的圖形配接器相對應。
* 如果您使用介面卡，請確定其4K 能夠使用。
* 請嘗試使用不同的 HDMI 埠。
* 如果您已將外部監視器插入至 HDMI 埠，請嘗試改為將其插入至 DisplayPort，並將 HDMI 埠用於耳機。
