---
title: 效能常見問題集
description: 超越標準取用者支援檔的效能 Windows Mixed Reality 疑難排解。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援、效能
appliesto:
- Windows 10
ms.openlocfilehash: 6754923a07d4c75c6f0f44aad07c5d3c55c28ae4673900531d8a4af663d9e7c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219414"
---
# <a name="performance-faqs"></a>效能常見問題集

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60-hz-or-90-hz-framerate"></a>我的 Windows Mixed Reality 耳機轉譯是以 60 Hz 或 90-Hz 的畫面播放速率呈現

如果您的獨立 GPU 具有 HDMI 2.0 埠，而 CPU 有四個以上的實體核心，則應該取得 90 Hz。 若要確認，請檢查 **裝置入口網站 > 效能** ] 索引標籤。

注意：如果您的 GPU 只有 HDMI 1.4 輸出，您可以使用 DisplayPort 至 [HDMI 2.0 介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 作為因應措施。

注意：「耳機顯示器」中的視覺品質設定只會影響 Windows Mixed Reality 首頁體驗的呈現。

## <a name="my-pc-is-running-slowly"></a>我的電腦執行速度很慢

系統可能會因為許多原因而變慢，通常只需要幾秒鐘的時間。 如果您在一段長時間內遇到此問題：

1. 關閉桌面上所有未使用的應用程式。
2. 確定您的膝上型電腦已插入電源來源。
3. 請確定電腦未準備好。
4. 降低 Windows Mixed Reality 首頁的視覺品質。
5. 確定您的電腦具有最新的 [圖形驅動程式](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) 。

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>我的電腦在執行混合現實體驗時正在準備。 如何? 保持很酷

1. 檢查電池是否已收費，以及電源是否插電。
2. 請確定電腦風扇未遭到封鎖。
3. 在相當酷炫的環境中使用電腦。
4. 請確定沒有任何熱度來源 (例如，在電腦上) 的太陽或熱度通風。

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>我的視覺效果很慢、載入速度很慢，或看起來沒問題

* 請確定您的耳機已插入您電腦上正確的圖形配接器。 有些電腦具有整合式和離散的圖形配接器。 離散卡片通常會提供最佳效能。 [深入瞭解電腦硬體](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。
* 關閉桌面上未使用的應用程式。
* 確定您的耳機適合 snugly (將它移到較低或更高的位置，或靠左和向右調整) 。
* 在 **設定 > 混合現實 > 耳機顯示** 中調整耳機的視覺效果設定。 當「視覺品質」設定為「自動」時，將會自動選擇您電腦的混合現實體驗。 如需更多視覺效果的詳細資訊，請將「視覺品質」設定為「高」。 如果您的視覺效果斷斷續續，請選取較低的設定。
* 調整耳機校正旋鈕，以確定鏡頭設定為瞳孔 (（稱為 IPD) ）之間的正確距離。 如果您不知道 IPD，optometrist 可以為您測量，或使用設計來測量 IPD 的網站。 如果耳機沒有校正旋鈕，請選取 **設定 > 混合現實 > 耳機顯示** 並調整「校正控制項」。
* 如果您使用的是 USB 或 DisplayPort 至 HDMI 介面卡，請試著另一個。 請參閱 [建議的介面卡。](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* 中斷任何可能連接到電腦圖形配接器的額外監視器。
* 從 Windows 存放區嘗試一些不同的混合現實應用程式，有些應用程式可能更適合您的電腦設定。
