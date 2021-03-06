---
title: HoloLens 研究模式
description: 在 HoloLens 上使用 Research 模式時，應用程式可以存取主要裝置感應器串流 (深度、環境追蹤和 IR 反射率) 。
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: 研究模式、cv、rs4、電腦視覺、研究、HoloLens、HoloLens 2
ms.openlocfilehash: 6737f9b668b73258e65f8d00e85dcd19c28ddfb5
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237129"
---
# <a name="hololens-research-mode"></a>HoloLens 研究模式

研究模式是在 HoloLens (第一代) 裝置上引進，以提供金鑰感應器的存取權，特別是研究不打算進行部署的應用程式。  HoloLens 2 的研究模式會保留 HoloLens 1 的功能，但會新增下列資料流程的存取權：

* **可見的光線環境追蹤攝影機** -系統用來追蹤和地圖大樓的灰色縮放相機。
* **深度相機** –以兩種模式運作：  
    + AHAT、高頻率 (45 FPS) 用於手動追蹤的近深度感知。 與第一個版本的簡短擲回模式不同的是，AHAT 提供的虛擬深度與1計量以外的階段換行。 
    + 長時間擲回、低頻率 (1-5 FPS) [空間對應](../../design/spatial-mapping.md)所使用的深度感應

* **兩個版本的 IR 反射率串流** -由 HoloLens 用來計算深度。 這些影像會由紅外線發亮，並不受環境可見的光線影響。

如果您使用的是 HoloLens 2，您也可以存取下列其他輸入：

* **加速** 計–由系統用來判斷沿著 X、Y 和 Z 軸和重力的線性加速。
* **回轉** –系統用來判斷旋轉。
* **磁力計** –由系統用來估計絕對方向。

> [!IMPORTANT]
> 研究模式目前為公開預覽狀態。 

![研究模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)<br>
*測試應用程式的混合現實捕捉，可顯示研究模式中可用的八個感應器串流*

## <a name="usage"></a>使用方式

研究模式是專為學術與產業研究人員所設計，可探索電腦視覺和機器人領域中的新想法。  它不適用於企業環境中部署的應用程式，或可透過 Microsoft Store 或其他散發通道使用的應用程式。

此外，Microsoft 不保證未來的硬體或作業系統更新將會支援研究模式或同等功能。 不過，請勿讓您使用它來開發和測試新的想法！

## <a name="security-and-performance"></a>安全性和效能

即使使用研究模式功能的應用程式未執行，在正常情況下，啟用 Research 模式仍會使用較高的電池電力。  啟用此模式也會降低裝置的整體安全性，因為應用程式可能會誤用感應器資料。  您可以在 [HoloLens 安全性常見問題](/hololens/hololens-faq-security)中找到裝置安全性的詳細資訊。  

## <a name="device-support"></a>裝置支援
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens 第一代</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>Head 追蹤攝影機</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>IR 攝影機的深度 &</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>加速計</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>迴轉儀</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>磁力計</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>啟用 Research 模式 (HoloLens first Gen 和 HoloLens 2) 

研究模式是開發人員模式的延伸模組。 開始之前，必須先啟用裝置的開發人員功能，才能存取研究模式設定： 

* 開啟 [ **開始] 功能表 > 設定** ]，然後選取 [ **更新**]。
* **針對開發人員** 選取並啟用 **開發人員模式**。
* 向下捲動並啟用 **裝置入口網站**。

啟用開發人員功能之後，請連線 [到裝置入口網站](/windows/uwp/debug-test-perf/device-portal-hololens) 以啟用研究模式功能：

* 移至 **裝置入口網站** 中的 [**系統 > 研究模式]** 。
* 選取 [ **允許存取感應器串流**]。
* 從頁面頂端的 [ **電源** ] 功能表項目目重新開機裝置。

當您重新開機裝置之後，透過 **裝置入口網站** 載入的應用程式就可以存取研究模式串流。

![HoloLens 裝置入口網站的 [研究模式] 索引標籤](images/ResearchModeDevPortal.png)<br>
*HoloLens 裝置入口網站中的研究強制回應視窗*

> [!IMPORTANT]
> 從組建19041.1364 開始，可取得 HoloLens 2 的研究模式。 如果您需要在先前的組建中存取，請註冊我們的 [Insider preview](/hololens/hololens-insider) 計畫。 您可以在 [研究模式 GitHub 存放庫](https://github.com/microsoft/HoloLens2ForCV)中找到更多詳細資料。

### <a name="using-sensor-data-in-your-apps"></a>在您的應用程式中使用感應器資料

應用程式可存取感應器串流資料的方式，與 [媒體基礎](/windows/win32/medfound/microsoft-media-foundation-sdk) 存取相片和攝影機串流的方式相同。 

所有適用于 HoloLens 開發的 Api 也都可在研究模式中取得。 尤其是，應用程式會準確知道 HoloLens 在每個感應器畫面格捕獲時間的6DoF 空間中。

我們的範例應用程式會顯示研究模式串流存取、使用 [內建函式和 extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)，以及記錄資料流程：
* [HoloLens (第一代) ](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>支援

針對 HoloLens (第一代) ，請使用 HoloLensForCV 存放庫中的 [問題追蹤](https://github.com/Microsoft/HololensForCV/issues) 程式張貼意見反應，並追蹤已知問題。

針對 HoloLens 2，請使用 HoloLens2ForCV 存放庫中的 [問題追蹤](https://github.com/microsoft/HoloLens2ForCV/issues) 程式張貼意見反應，並追蹤已知問題。

## <a name="see-also"></a>另請參閱

* [Microsoft 媒體基礎](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [HoloLensForCV GitHub 存放庫](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens2ForCV GitHub 存放庫](https://github.com/microsoft/HoloLens2ForCV)
* [使用 Windows 裝置入口網站](using-the-windows-device-portal.md)