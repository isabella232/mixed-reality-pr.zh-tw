---
title: 設定常見問題
description: Advanced Windows Mixed Reality 針對超出標準取用者支援檔的設定問題進行疑難排解。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，疑難排解，錯誤，說明，支援，安裝，Windows Mixed Reality 家用 Windows Mixed Reality 入口網站
appliesto:
- Windows 10
ms.openlocfilehash: 2e079cae16a20a4e0a2e6c967ecedef1950ded57
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680317"
---
# <a name="setup-faqs"></a>設定常見問題 

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>當我插入耳機時，不會開啟混合實境入口。

混合實境入口，會將您帶到 Windows Mixed Reality 安裝程式的應用程式，設計為在插入相容的耳機時自動開啟。 如果未開啟，請移至 [開始]，然後在搜尋方塊中輸入 "混合實境入口" 以開啟應用程式。 如果找不到混合實境入口，這可能表示您需要 [更新至最新版本的 Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq)。

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>如何? 在「站上和站內」和「所有體驗」之間做選擇？

如果您在耳機設定或更新版本中選擇「已待命」，則會使用沒有界限的耳機。 您可以離開或保持在同一處，但是您將不會有任何界限可協助您避免實體障礙。 某些應用程式可能是設計來搭配界限使用，因此您可能無法使用它們，或者如果您在沒有界限的情況下使用，則可能不會有相同的體驗。 請參閱「 [什麼是界限，為什麼應該建立一個？](boundary-questions.md#whats-a-boundary-and-why-should-i-create-one)」。

如果您選擇 [所有體驗]，您將會設定界限，而且可以使用適用于界限的應用程式和體驗，以及不需要的應用程式和體驗。 

## <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-to-windows-mixed-reality-home"></a>學習混合實境不會在第一次啟動時執行，而是 Windows Mixed Reality home。

您可以遵循 [重新執行的步驟](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience)，重新執行學習體驗。 

## <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>我的控制器不會顯示在我的 Windows Mixed Reality 首頁中。

請確定您的控制器具有完整的電池，且已使用藍牙正確配對。 請嘗試使用 Windows 按鈕關閉和開啟控制器電源。 如果您仍然看不到您的控制器，請嘗試取消配對並重新配對每個控制器： 
* 如果您的耳機有內建的無線電，請使用耳機隨附的隨附應用程式來將，然後再次配對控制器 (混合實境入口可協助您找到正確的隨附應用程式) 。 
* 如果控制器與電腦配對，請移至 [ **裝置] > 藍牙 > 設定** ，再次將和配對控制器。 

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>我的 Windows Mixed Reality 首頁的樓層似乎不是正確的高度。

選取 [ **開始 > 地面調整** ]，這會在您將應用程式放在世界中時啟動，以在戴耳機時進行變更。 在此應用程式中，系統會將您導向使用觸控板 (移動控制器) 或方向 (板) 來調整樓層高度。 當地面感覺正確時，請使用 [Windows] 按鈕返回您的首頁。

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>我無法在我的電腦上，顯示我在耳機中看到的預覽。

Windows Mixed Reality 入口網站的畫面底部有一個 [ **播放** ] 按鈕，可讓您在桌面畫面上預覽您在耳機中看到的內容。 基於效能考慮，只有在 Windows Mixed Reality Ultra (90Hz) 的電腦上才能使用此功能。

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>我收到「發生錯誤」的錯誤訊息，或我遇到混合實境入口的問題
若要取得特定錯誤碼的詳細資訊，請參閱 [這裡](error-codes.md)。 您也可以嘗試：

重新開機 Windows Mixed Reality：
1. 從電腦中斷連接耳機纜線。
2. 重新啟動電腦。
3. 重新連接您的耳機。

確定您的電腦能夠辨識您的耳機：
1. 選取 [啟動]。
2. 在搜尋方塊中輸入 "裝置管理員"，然後在清單中選取它。 
3. 展開 [混合現實裝置]，並查看是否已列出您的耳機。 

如果未列出：
1. 將耳機插入電腦上的不同埠（如果有的話）。
2. 從 Windows Update 檢查是否有最新的軟體更新。
3. 卸載並重新安裝 Windows Mixed Reality：
    1. 從電腦中斷連接耳機纜線。
    2. 選取 [ **> 混合現實 > 卸載] 設定** 。
    3. 如果您的移動控制器已與您的電腦配對，請選取 [ **> 裝置] > 藍牙 & 其他裝置** 來將這些裝置的設定。 選取每個控制器，然後選取 [移除裝置]。 如果您的控制器與耳機配對，您可以略過此步驟。
    4. 將您的耳機插回電腦以重新安裝 Windows Mixed Reality。

## <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>我無法直接將輸入 (控制器、遊戲台、滑鼠/鍵盤) 到 Windows Mixed Reality。

當您放入耳機時，輸入應該會透過耳機的狀態感應器自動切換至您的混合現實體驗。 您的桌面上應該會出現藍色橫條：

![將輸入導向耳機的 Windows Desktop](images/1050px-windowsy.png)

如果未自動切換輸入，您可能會在 [ **設定 > 混合現實 > 耳機顯示器 > 輸入切換** 中停用自動輸入切換。 您一律可以在鍵盤上輸入 **Windows 鍵 + Y** ，以手動方式將輸入切換至您的耳機或回到桌面上。

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>在混合現實的過程中，我會在「將您的前端移至一邊，然後在地面」上停滯。

此步驟可讓您的耳機辨識您的空間，並還原任何現有的虛擬樓層和界限。 當您放入耳機時，此掃描程式最多可能需要10秒鐘的時間。 完成之後，您將會位於 Windows Mixed Reality home，否則系統會提示您再次設定界限。

如果掃描程式所花費的時間超過10秒，則耳機中的鄰近感應器可能會發生問題：
1. 檢查是否已從鄰近感應器移除不乾膠。 近接感應器位於耳機內，大約是您冷汗中心的位置。
2. 檢查您的鄰近感應器是否正在將輸入切換至您的耳機：使用手指，在確認輸入正在切換到耳機時，請先涵蓋並找出鄰近感應器數次。 您應該會在電腦頂端看到 **Windows 鍵 + Y** 橫幅。 您可以在鍵盤上輸入 **Windows 鍵 + Y** ，隨時手動將輸入切換到耳機。

## <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>我的 Xbox 控制器無法使用 Windows Mixed Reality。

* 確定您的控制器已開啟、完全收費，並連接到電腦。
* 更換控制器的電池。
* 如果您使用 Bluetooth 控制器，請移至電腦上的 [ **設定] > 裝置 > 藍牙 &** 電腦上的其他裝置，並確定它已配對 (應該列在頁面) 上。
