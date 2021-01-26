---
title: 全像攝影遠端播放程式
description: 深入瞭解全像是全像您的 HoloLens，從電腦到 HoloLens 的全像攝影遠端播放機，以及將全像攝影內容串流處理。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、遠端、全像全像遠端、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、診斷、效能
ms.openlocfilehash: 768ac55bdd117648977c64a1947254540ec7306a
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810149"
---
# <a name="holographic-remoting-player"></a>全像攝影遠端播放程式

>[!IMPORTANT]
>HoloLens 2 的全像是主要版本變更。 [ **HoloLens (第1代)** 的遠端應用程式](add-holographic-remoting.md)必須使用 NuGet 套件 1.x. x 和 [遠端應用程式， **HoloLens 2**](holographic-remoting-create-remote-wmr.md) **必須使用 2.x**. x. x. x. x. x. x. x 版。 這表示針對 HoloLens 2 所撰寫的遠端應用程式與 HoloLens (第1代) 並不相容，反之亦然。

全像 [遠端播放機](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) 是一個附屬應用程式，可連線到支援全像攝影的電腦應用程式和遊戲。 全像攝影的遠端處理會使用 Wi-Fi 連線，即時將電腦上的全像攝影內容串流處理至您的 Microsoft HoloLens。

全像「全像」遠端播放程式只能搭配設計用來支援全像攝影遠端的電腦應用程式使用。

「全像」 (第一代) 和 HoloLens 2 都可使用全像遠端播放機。  支援 HoloLens 的電腦應用程式必須進行更新，以支援使用 HoloLens 2 的全像全像進行遠端處理。 如果您有關于支援哪些版本的問題，請洽詢您的應用程式提供者。

>[!TIP]
>從版本 [2.2.0](holographic-remoting-version-history.md#v2.2.0) 開始，您也可以在執行 [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)的 Windows 電腦上使用全像遠端播放機。

>[!TIP]
>從版本 [2.4.0](holographic-remoting-version-history.md#v2.4.0) 使用 [OpenXR API](../native/openxr.md) 的遠端應用程式可以建立。 若要開始使用，請參閱 [使用 OpenXR Api 撰寫全像遠端處理遠端應用程式](holographic-remoting-create-remote-openxr.md)。

## <a name="connecting-to-the-holographic-remoting-player"></a>連接到全像遠端播放機

依照您應用程式的指示，連接到全像遠端播放機。 您必須輸入 HoloLens 裝置的 IP 位址，您可以在遠端播放程式的主畫面上看到該位址，如下所示：

![全像攝影遠端播放程式](images/holographicremotingplayer.png)

當您看到主畫面時，您會知道您沒有連接的應用程式。

全像「全像遠端」連接未 **加密**。 您應該一律透過您信任的安全 Wi-Fi 連接來使用全像遠端功能。

## <a name="quality-and-performance"></a>品質和效能

您體驗的品質和效能會因三個因素而異：
* **您** 正在執行的全像攝影體驗-轉譯高解析度或高度詳細內容的應用程式，可能需要更快的電腦或更快的無線連接。
* **您電腦的硬體** -您的電腦必須能夠以每秒60個畫面格的方式執行並編碼您的全像您的全像攝影體驗。 若為圖形配接器，我們通常建議使用 GeForce GTX 970 或 AMD Radeon Junos r 9 290 或更好的。 同樣地，您的特定體驗可能需要較高或較低的介面卡。
* **您的 Wi-Fi** 連線-您的全像攝影體驗會透過 wi-fi 進行串流。 使用具有低擁塞的快速網路來最大化品質。 使用透過乙太網路纜線（而非 Wi-fi）連接的電腦，也可能改善品質。

## <a name="diagnostics"></a>診斷

若要測量您的連線品質，請在全像全像的遠端播放播放程式的主畫面上，說「 **啟用診斷** 」。 啟用診斷時，在 **HoloLens (第一代)** 應用程式將會顯示：

* **FPS** -遠端播放程式每秒接收和轉譯的平均轉譯框架數目。 理想的情況是 60 FPS。
* **延遲** -框架從電腦移到 HoloLens 所花費的平均時間量。 愈小越好。 這主要取決於您的 Wi-Fi 網路。

在 **HoloLens 2** 應用程式將會顯示：

![全像遠端播放機診斷](images/holographicremotingplayer-diag.png)

* 轉譯 **-遠端** 播放程式在上一秒呈現的畫面格數目。 請注意，這與透過網路抵達的畫面格數目無關， (查看 **影片畫面**) 。 轉譯的畫面格之間的平均/最大轉譯時間（以毫秒為單位）會顯示于最後一秒。

* **影片畫面** -顯示的第一個數位是略過的影片畫面，第二個是重複使用的影片畫面，第三個則是接收到影片畫面。 所有數位都代表上一秒的計數。
    * ```Received frames``` 是在上一秒抵達的影片框架數目。 在正常狀況下，這應該是60，但如果不是，則表示因為網路問題或遠端/遠端端未產生具有預期速率的畫面格，所以可能會發生這種情況。
    * ```Reused frames``` 這是在上一秒內使用超過一次的影片框架計數。 比方說，如果影片畫面晚抵達，播放程式的轉譯迴圈仍會呈現畫面格，但需要 *重複* 使用先前框架所用的影片畫面。
    * ```Skipped frames``` 是播放程式的轉譯迴圈尚未使用的影片框架計數。 比方說，網路抖動的效果可能會讓影片畫面格抵達的效果不再平均分散。 例如，如果有一些延遲時間，而其他人會在執行 60 Hz 時，不會再有16.66 毫秒的差異，所以會有較晚的時間到達。 如果有一個以上的框架抵達播放程式轉譯迴圈的兩個刻度之間，就會發生這種情況。 在此情況下，播放程式會 *略過* 一或多個畫面格，因為它應該一律顯示最新收到的影片畫面。

    >[!NOTE]
    >當面對網路抖動時，略過和重複使用的框架通常會是相同的。 相反地，如果您只看到略過的畫面格，這就是播放程式未達到其目標畫面播放速率的指標。 在這種情況下，您應該在診斷問題時留意最大轉譯時間差異時間。

* **影片畫面差異** -上一秒收到的影片畫面之間的最小/最大差異。 此數目通常會與略過/重複使用的框架相互關聯，以防網路抖動所造成的問題。
* **延遲** -上一秒的平均週期（以毫秒為單位）。 此內容中的周轉表示從 HoloLens 傳送姿勢/感應器資料到遠端/遠端端的時間，直到顯示 HoloLens 顯示器上該姿勢/遙測資料的影片畫面為止。
* 已 **捨棄的影片框架**-上一秒捨棄的影片畫面數，以及自從建立連線之後的次數。 捨棄的影片畫面的主要原因是影片框架未按順序抵達，因此需要捨棄，因為已有較新的影片畫面。 這類似于 *捨棄的框架* ，但原因是在遠端堆疊中較低的層級。 只有在不正確的網路狀況下，才會出現已捨棄的影片畫面。

在主畫面上，您可以說「 **停用診斷** 」來關閉診斷。

## <a name="pc-system-requirements"></a>電腦系統需求
* 您的電腦 **必須** 執行 Windows 10 年度更新版或更新版本。
* 我們建議使用 GeForce GTX 970 或 AMD Radeon Junos r 9 290 或更佳的圖形配接器。
* 建議您透過乙太網路將您的電腦連線到您的網路，以減少無線躍點數目。

## <a name="see-also"></a>另請參閱
* [HoloLens (第一代) ：新增全像的遠端處理](add-holographic-remoting.md)
* [使用 Windows Mixed Reality Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-openxr.md)
* [全像攝影遠端軟體授權條款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)