---
title: 安裝錯誤
description: 超越標準取用者支援檔，Advanced Windows Mixed Reality 的安裝錯誤疑難排解。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，疑難排解，錯誤，協助，支援，安裝
appliesto:
- Windows 10
ms.openlocfilehash: 56ead28a5809eadef1797507168b68cbaf79953e
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726059"
---
# <a name="installation-errors"></a>安裝錯誤

## <a name="your-pc-cant-run-windows-mixed-reality"></a>「您的電腦無法執行 Windows Mixed Reality」

您的電腦不符合執行 Windows Mixed Reality 所需的 [最低需求](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 。 電腦的硬體安裝可能與 Windows Mixed Reality 不相容，或者您可能需要 [更新至最新版本的 Windows](https://support.microsoft.com/help/12373/windows-update-faq)。 

Windows Mixed Reality 需要至少支援 WDDM 2.2 的圖形配接器驅動程式。 請確定您有來自製造商的最新驅動程式更新。 如果 Windows Mixed Reality 安裝程式指出您的圖形配接器不符合需求，而您認為它的確如此，請確定您的耳機已插入正確的卡片中。

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>「您差不多，這部電腦不符合執行 Windows Mixed Reality 所需的最低需求」

您的電腦不符合 Windows Mixed Reality 中最佳體驗所需的 [最低需求](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 。 您的電腦可能可以執行沉浸式耳機，但可能會遇到效能問題，而且無法執行某些應用程式。

Windows Mixed Reality 需要至少支援 WDDM 2.2 的圖形配接器驅動程式。 請確定您有來自製造商的最新驅動程式更新。 如果 Windows Mixed Reality 安裝程式指出您的圖形配接器不符合需求，而您認為它的確如此，請確定您的耳機已插入正確的卡片中。

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>「在我們可以設定 Windows Mixed Reality 之前，您的系統管理員必須為您的組織啟用它。 深入瞭解」

您可能是在企業管理的網路上，而且您的組織使用 Windows Server Update Services (WSUS) 。 這些和其他可能會封鎖下載的原則。 請洽詢貴組織的 IT 部門或系統管理員，以 [啟用 Windows Mixed Reality](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable)。

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>「我們無法下載 mixed reality 軟體」或「在我們進行一些下載時無阻礙」

* 有時暫止的更新可能會封鎖混合的現實軟體下載。 移至 [ **設定] > 更新 & 安全性 > Windows Update** 並確認 Windows Update 已開啟。 然後下載並安裝任何等候中的更新。 如果您收到 Windows Update 錯誤，請 [在這裡](https://support.microsoft.com/help/10164/fix-windows-update-errors)取得協助。
* 請確定您的電腦已連線到網際網路，且至少有 2 GB 的可用儲存空間。 檢查網路狀態： **設定 > 網路 & 網際網路 > 狀態**。 如果您無法連線到網際網路，請 [在這裡](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues)取得協助。  
* 請重新開機您的電腦，然後再試一次。 

如果這些解決方案無法運作，請嘗試：
* 如果您的 Wi-Fi 網路連線設定為 [計量付費]，請將其變更為 [未 [計費](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq)]。 若要關閉計量付費連線，請移至：設定 **> 網路 & 網際網路 > 狀態 > 變更連接屬性 > 設定為計量付費連線** ，然後選取 [關閉]。  
* 如果您最近安裝了更新，可能會造成問題。 我們不建議您移除任何已安裝的更新，特別是安全更新，讓您的電腦保持安全。 不過，有時候移除最新的更新有助於判斷問題的根源： 
    * 移至 [ **設定] > 更新 & 安全性 > 查看已安裝的更新歷程記錄 > 卸載更新**
    * 選取上次安裝的更新，然後選取 [卸載]。
    * 當系統提示「您確定要卸載此更新嗎？」 回答「是」。 如果您在嘗試這些步驟時收到錯誤，請取得有關如何 [修正 windows update 錯誤](https://support.microsoft.com//help/10164/fix-windows-update-errors)的詳細資料。 
    * 請重新開機您的電腦，然後再試一次。 
    * 如果 Windows Mixed Reality 正確安裝，請在 [設定] > 下重新安裝最新的更新， **Windows Update > 檢查是否有更新** ，並查看 Windows Mixed Reality 是否持續運作。 如果未正確安裝，請重新安裝更新，並聯絡 Windows 支援。 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>「發生問題，無法開始 Windows Mixed Reality」
若要取得特定錯誤碼的詳細資訊，請參閱 [這裡](error-codes.md)。 您也可以嘗試：

* 從電腦拔下耳機纜線。
* 將電腦重新開機。
* 移至 [ **設定] > 更新 & 安全性 > Windows Update** 並確認已開啟 [Windows Update]。 下載並安裝任何等候中的更新。
* 將您的耳機重新連接到電腦，然後再次嘗試安裝程式。

如果這些步驟都沒有作用，請卸載，然後重新安裝 Windows Mixed Reality：
* 移至 [ **設定 > 混合現實 > 卸載** ]，然後選取 [卸載]。 
* 重新啟動電腦。 
* 若要再次啟動安裝程式，只需將您的耳機插入您的電腦。
