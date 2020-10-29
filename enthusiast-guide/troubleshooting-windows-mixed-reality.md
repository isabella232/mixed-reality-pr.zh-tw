---
title: 疑難排解 Windows Mixed Reality
description: 超越標準取用者支援檔的 Advanced Windows Mixed Reality 疑難排解。
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援
ms.openlocfilehash: bf972c70f46ad9045005b953e28831df3ee9906e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680276"
---
# <a name="troubleshooting-windows-mixed-reality-faqs"></a>疑難排解 Windows Mixed Reality (常見問題) 

## <a name="understanding-common-installation-error-messages"></a>瞭解常見安裝錯誤訊息

### <a name="your-pc-cant-run-windows-mixed-reality"></a>「您的電腦無法執行 Windows Mixed Reality」

您的電腦不符合執行 Windows Mixed Reality 所需的 [最低需求](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 。 這可能是因為電腦的硬體安裝程式與 Windows Mixed Reality 不相容，或是因為您需要 [更新至最新版本的 Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq)。 

請注意，Windows Mixed Reality 需要至少支援 WDDM 2.2 的圖形配接器驅動程式，因此請確定您已從製造商取得最新的驅動程式更新。 如果 Windows Mixed Reality 安裝程式指出您的圖形配接器不符合需求，而您認為它的確如此，請確定您的耳機已插入正確的卡片中。

### <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>「您差不多，這部電腦不符合執行 Windows Mixed Reality 所需的最低需求」

您的電腦不符合 Windows Mixed Reality 中最佳體驗所需的 [最低需求](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 。 您的電腦可能可以執行沉浸式耳機，但可能無法執行某些應用程式，或可能發生效能問題。

請注意，Windows Mixed Reality 需要至少支援 WDDM 2.2 的圖形配接器驅動程式，因此請確定您已從製造商取得最新的驅動程式更新。 如果 Windows Mixed Reality 安裝程式指出您的圖形配接器不符合需求，而您認為它的確如此，請確定您的耳機已插入正確的卡片中。

### <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>「在我們可以設定 Windows Mixed Reality 之前，您的系統管理員必須為您的組織啟用它。 深入瞭解」

您可能是在企業管理的網路上，而且您的組織使用 Windows Server Update Services (WSUS) 或有其他可能封鎖下載的原則。 請洽詢貴組織的 IT 部門或系統管理員，以 [啟用 Windows Mixed Reality](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable)。

### <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>「我們無法下載 mixed reality 軟體」或「在我們進行一些下載時無阻礙」

* 有時暫止的更新可能會封鎖混合的現實軟體下載。 移至 [ **設定] > 更新 & 安全性 > Windows Update** 並確認 Windows Update 已開啟。 然後下載並安裝任何正在等待安裝的更新。 如果您在嘗試這些步驟時收到 Windows Update 的錯誤，請移至 [這裡](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)。
* 請確定您的電腦已連線到網際網路，且至少有2GB 的可用儲存空間。 檢查網路狀態： **設定 > 網路 & 網際網路 > 狀態** 。 如果您無法連線到網際網路，請移至 [這裡](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues) 以取得協助。  
* 請重新開機您的電腦，然後再試一次。 

如果先前的解決方案無法運作，請嘗試：
* 如果您的 Wi-fi 網路連線設定為計量付費，請將它變更為「未 [計費](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq)」。 若要關閉計量付費連線，請移至：設定 **> 網路 & 網際網路 > 狀態 > 變更連接屬性 > 設定為計量付費連線** ，然後選取 [關閉]。  
* 如果您最近安裝了更新，可能會造成問題。 我們不建議您移除任何已安裝的更新，尤其是安全性更新，以確保電腦的安全，但有時移除最新的更新可協助判斷問題的根源。 若要這樣做： 
    * 移至 [ **設定] > 更新 & 安全性 > 查看已安裝的更新歷程記錄 > 卸載更新**
    * 選取上次安裝的更新，然後選取 [卸載]。
    * 當系統提示「您確定要卸載此更新嗎？」 回答「是」。 如果您在嘗試這些步驟時收到錯誤，請移至 [這裡](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)。 
    * 請重新開機您的電腦，然後再試一次。 
    * 如果 Windows Mixed Reality 正確安裝，請在 [設定] > 下重新安裝最新的更新， **Windows Update > 檢查是否有更新** ，並查看 Windows Mixed Reality 是否持續運作。 如果未正確安裝，請重新安裝最新的更新，並聯絡 Windows 支援。 

### <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>「發生問題，無法開始 Windows Mixed Reality」
* 從電腦拔下耳機的兩條纜線。
* 將電腦重新開機。
* 移至 [ **設定] > 更新 & 安全性 > Windows Update** 並確認已開啟 [Windows Update]。 然後下載並安裝任何等候中的更新。
* 將您的耳機重新連接到電腦，然後再次嘗試安裝程式。

如果上述步驟沒有作用，請嘗試卸載，然後重新安裝 Windows Mixed Reality：
* 移至 [ **設定 > 混合現實 > 卸載** ]，然後選取 [卸載]。 
* 重新啟動電腦。 
* 若要再次啟動安裝程式，只需將您的耳機插入您的電腦。
    

## <a name="troubleshooting-setup-questions"></a>針對設定問題進行疑難排解 

### <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>我的 Xbox 控制器無法使用 Windows Mixed Reality。

* 確定您的控制器已開啟、完全收費，並連接到電腦。
* 更換控制器的電池。
* 如果您使用 Bluetooth 控制器，請移至電腦上的 [ **設定] > 裝置 > 藍牙 &** 電腦上的其他裝置，並確定它已配對 (應該列在頁面) 上。

### <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>我無法直接將輸入 (控制器、遊戲台、滑鼠/鍵盤) 到 Windows Mixed Reality。

當您放入耳機時，輸入應該會透過耳機的狀態感應器自動切換至您的混合現實體驗。 您的桌面上應該會出現藍色橫條：

![將輸入導向耳機的 Windows Desktop](images/1050px-windowsy.png)

如果未自動切換輸入，您必須手動將輸入切換到耳機。 若要這麼做，您可以在鍵盤上輸入 **Windows 鍵 + Y** (以及將輸入切換回桌面) 。

### <a name="when-i-plug-in-my-headset-nothing-happens-the-mixed-reality-portal-doesnt-open"></a>當我插入耳機時，不會發生任何事。 混合實境入口不會開啟。
混合實境入口，會將您帶到 Windows Mixed Reality 安裝程式的應用程式，設計為在插入相容的耳機時自動開啟。 如果未開啟，請移至 [開始]，然後在 [搜尋] 方塊中輸入 "混合實境入口"，從該處開啟應用程式。 如果找不到混合實境入口，這可能表示您需要 [更新至最新版本的 Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq)。

### <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>如何? 在「站上和站內」和「所有體驗」之間做選擇？

如果您在耳機設定或更新版本中選擇「已待命」，則會使用沒有界限的耳機。 您可以離開或保持在同一處，但是您將不會有任何界限可協助您避免實體障礙。 某些應用程式可能是設計來搭配界限使用，因此您可能無法使用它們，或者如果您在沒有界限的情況下使用，則可能不會有相同的體驗。 請參閱「什麼是界限，為什麼應該建立一個？」 以下是詳細資訊。

如果您選擇 [所有體驗]，您將會設定界限，而且可以使用適用于界限的應用程式和體驗，以及不需要的應用程式和體驗。 

### <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-into-the-windows-mixed-reality-home"></a>學習混合實境不會在第一次啟動時執行，而是直接進入 Windows Mixed Reality 首頁。

您可以遵循 [重新執行的步驟](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience)，重新執行學習體驗。 


## <a name="boundary-setup-and-other-questions"></a>界限設定和其他問題

### <a name="whats-a-boundary-and-why-should-i-create-one"></a>什麼是界限，以及為什麼應該建立一個界限？

界限會定義您在戴 Windows Mixed Reality 沉浸式耳機時，可以四處移動的區域。 因為您在使用耳機時看不到您的周圍，所以請務必建立界限來協助避免阻礙。 界限在混合現實內部看起來像白色外框，當您接近它時，它就會出現。 當您看到它時，會使您的移動變慢，並避免跨越界限或將樹幹延伸至外。

界限內的區域應該是「傢俱」、「低燈燈燈」、「天花板風扇」等等，因此您不會在任何地方進行任何動作。 [瞭解 Windows Mixed Reality 中的健康狀態和安全性](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)。

### <a name="how-do-i-create-a-boundary"></a>如何? 建立界限？

當您第一次設定耳機時，安裝應用程式 (混合實境入口) 將會引導您完成建立界限的步驟。 但是您隨時都可以建立一個。 若要這樣做：
1. 選取您桌面上的 [ **開始] > 混合實境入口** 。 
2. 開啟 [功能表]。
3. 選取 [執行安裝程式] 以建立新的界限。

如果有其他人使用您的耳機，請務必瞭解界限，以及其使用方式。 如果您將耳機移至新位置，則必須設定適用于該空間的新界限。

### <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>當我嘗試建立界限時，收到錯誤訊息。

* 建立界限時，請勿太接近牆或其他障礙物。
* 請務必將您的耳機保持在 waist 高度，並在追蹤界限時面對您的電腦。
* 請確定感應器未遭到封鎖，且有足夠的光線。
* 您要追蹤的空間應大於三個正方形計量。
* 空間不應太大或太複雜。 不需要太多訣竅，就能繼續使用簡單的幾何形狀。
* 當您進行追蹤時，請勿交叉回復自己的路徑。
* 如果您卡在角落，請從頭開始。

### <a name="during-start-up-of-mixed-reality-im-stuck-at-the-step-turn-your-head-side-to-side-and-then-at-the-floor"></a>在混合現實的啟動過程中，我會停滯在「將您的前端移至側面，然後在地面」。

此步驟可讓您的耳機辨識您的空間，並還原任何現有的虛擬樓層和界限。 當您放入耳機時，此掃描程式最多可能需要10秒鐘的時間。 完成之後，您將會在混合現實首頁中，否則系統會提示您再次設定界限。

如果掃描程式所花費的時間超過10秒，則耳機中的鄰近感應器可能會發生問題：
1. 檢查是否已從鄰近感應器移除不乾膠。 近接感應器位於耳機內，大約是您冷汗中心的位置。
2. 檢查您的鄰近感應器是否正在將輸入切換至您的耳機：使用手指，在確認輸入正在切換到耳機時，請先涵蓋並找出鄰近感應器數次。 您應該會在電腦頂端看到 **Windows 鍵 + Y** 橫幅。 您可以在鍵盤上輸入 **Windows 鍵 + Y** ，隨時手動將輸入切換到耳機。

### <a name="i-see-a-message-that-says-my-boundary-cant-be-found-what-should-i-do"></a>我看到一則訊息，指出找不到我的界限。 我該怎麼辦？

Windows Mixed Reality 可能無法識別您的現有界限。 您可以建立新的界限，也可以在「站上和站上」模式中使用您的裝置。 

### <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>我看到一則訊息，指出「遺失追蹤」或「我們沒有這個空間的界限」。

您必須建立新的界限。 若要這樣做：
* 選取 [ **開始] > 混合實境入口** 。
* 選取 [執行安裝程式]。

### <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>界限一律可見。 如何讓它消失？

當您接近界限時，即會顯示界限。 如果您的界限包含任何具有窄或不規則圖形的區段，您最後可能會接近它，並使其出現，比您想要的還多。 若要修正此問題，請嘗試使用較大且更一般的圖形再次建立您的界限。 若要這樣做：
* 選取 [ **開始] > 混合實境入口** 。
* 選取 [執行安裝程式]。

### <a name="how-can-i-turn-off-the-boundary-temporarily"></a>如何暫時關閉界限？

* 選取 [ **開始] > 混合實境入口** 。
* 開啟 [功能表]。 
* 將「界限」變成「關閉」。 當界限關閉時，請務必保持在一個位置。


## <a name="problems-in-windows-mixed-reality-home"></a>Windows Mixed Reality 首頁的問題

### <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>我的控制器不會顯示在我的 Windows Mixed Reality 首頁中。

請確定您的控制器具有完整的電池，且已使用藍牙正確配對。 請嘗試使用 Windows 按鈕關閉和開啟控制器電源。 如果您仍然看不到您的控制器，請在 [ **裝置] > 藍牙** ] 下的 [設定] 功能表中，嘗試配對並重新配對各控制器。

### <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height-or-it-is-slanted"></a>我的 Windows Mixed Reality 首頁的樓層似乎不是正確的高度，也不是傾斜的。

選取 [ **開始] > 房間調整** ，一旦您將應用程式放在世界中，就會啟動，以在佩戴耳機時進行變更。 在此應用程式中，系統會將您導向使用觸控板 (移動控制器) 或方向 (板) 來調整樓層高度。 當地面感覺正確時，請使用 Windows 按鈕來結束您的首頁。

### <a name="my-headset-has-stopped-tracking"></a>我的耳機已停止追蹤。

請確定燈開啟，而且沒有任何阻礙在耳機前方的內部追蹤攝影機。 如果遺失追蹤，可能需要幾秒鐘的時間才能繼續。 如果追蹤未繼續，請嘗試重新開機 Windows Mixed Reality 入口網站。 如需詳細資料，請參閱 [追蹤疑難排解](tracking.md) 。

### <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop-screen"></a>我無法在我的桌上型電腦螢幕上，顯示我在耳機中看到的預覽。

混合實境入口在畫面底部有一個 [ **播放** ] 按鈕，可讓您在桌面畫面上顯示您在耳機中看到的內容預覽。 但基於效能考慮，只有在 Windows Mixed Reality Ultra (90Hz) 的電腦上才能使用此功能。

## <a name="headset-connectivity-issues"></a>耳機連接問題

### <a name="my-computer-does-not-have-an-hdmi-port"></a>我的電腦沒有 HDMI 埠。
如果您的電腦沒有 HDMI 埠，但是有 DisplayPort (DP) 、迷你 DisplayPort (miniDP) 或 USB 類型 C (USB C) 埠來輸出影片，您可能需要使用 [支援的介面卡](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)。

### <a name="can-i-use-usb-or-hdmi-extension-cables-with-windows-mixed-reality-headsets"></a>我可以使用 USB 或 HDMI 擴充纜線搭配 Windows Mixed Reality 耳機嗎？
Windows Mixed Reality 耳機未正式支援使用 USB 或 HDMI 延伸模組纜線。 使用這些纜線可能會大幅影響您的混合現實體驗，原因是您電腦的 USB 控制器與混合現實耳機之間的信號完整性與匯流排電源之間的差異。 如果耳機顯示器短暫顯示藍色畫面，然後在使用時開啟黑色和混合實境入口重新開機或完全解除列舉，或是當耳機音訊剪出或變成 glitchy，或是當耳機在黑色和正確顯示器之間閃爍時，請嘗試使用沒有分機線的耳機。

### <a name="i-am-getting-a-check-your-display-cable-error"></a>我收到「檢查您的顯示器纜線」錯誤。

* 如果您使用任何介面卡將耳機連接到您的電腦，請確定其支援 Windows Mixed Reality。 此外，請先嘗試將介面卡連線到電腦，再將 HMD 連接至介面卡。
* 如果您的電腦同時具有整合式和離散圖形，請確定您使用的是使用中的圖形配接器上的 HDMI 埠。 在某些情況下，這可能表示您必須將您的電腦顯示器連接至非 HDMI 埠。
* 如果您的電腦同時具有整合式和離散圖形，且整合式圖形較舊且不支援 Windows Mixed Reality，請嘗試停用整合式 GPU。
* 將電腦監視器連接到電腦的 HDMI 埠。 請確定您的圖形驅動程式是最新的。 直接從 AMD、Nvidia 或 Intel 下載並安裝，因為它們可能會比發行至 Windows Update 的版本還新。
* 請確定您已將耳機的 HDMI 纜線插入電腦上的 **hdmi 輸出** 埠，而不是埠中的 hdmi。
* Windows 可能無法偵測到顯示器纜線連接。 開啟裝置管理員，並查看耳機是否列在 [監視器] 之下。 如果沒有，請選取 [ **動作] > 掃描硬體變更** 。 

### <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>我看到一則訊息，指出「放在您的耳機」上，即使我有耳機也一樣。

當您放入耳機時，Windows Mixed Reality 可能需要幾秒鐘的時間才能重載您的空間。 如果這則訊息不會消失，請確定已從鄰近性感應器移除保護貼紙，其位於鏡頭之間的耳機內。 如果這無法解決問題，請洽詢您的耳機製造商。

### <a name="a-message-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>即使我已接上耳機，還是會顯示「連接您的耳機」訊息。

1. 請確定耳機的 USB 和 HDMI 纜線已連接到您電腦上的正確埠。 以下說明如何識別正確的埠：
    * USB 3.0 埠具有特殊標誌，其 "SS" 標示 (表示 "SuperSpeed" ) 。 埠的內部部分通常是藍色，而較舊的 USB 2.0 埠通常是在內部的黑色或白色。
    * 如果您的電腦有兩個 HDMI 埠，請使用連接到圖形配接器的埠，而不是電腦的主機板。 這並不一定很明顯，但離散埠通常位於電腦的展開位置。 如果您嘗試一個埠但無法運作，請嘗試其他埠。
2. 拔掉並插上耳機的 USB 和 HDMI 纜線，以確定它們已安全地連線。 插入 USB 纜線時，請不要在插入 USB 纜線期間暫停。
3. 開啟裝置管理員並確認您的耳機列在 [混合式現實裝置] 下方。 按兩下 [混合現實裝置] 下的耳機，並確認裝置狀態指出「此裝置運作正常」。 裝置管理員中所列裝置上的黃色驚嘆號表示連接到您電腦的裝置所回報的錯誤。
    * 如果在裝置管理員中以黃色驚嘆號列出「Hololens 感應器」，請按兩下裝置。 如果您看到「 **代碼10：未安裝此裝置的驅動程式」。此裝置沒有相容的驅動程式** 」，請依照 [指示](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset) 手動安裝耳機驅動程式。
    * 如果您在電腦上使用多個混合現實耳機，並且在之前手動安裝混合現實耳機驅動程式，則在某些情況下，手動驅動程式更新可能只會套用到目前連線的耳機，而不會套用到您的其他耳機。 在此情況下，您會看到「程式 **代碼31：此裝置無法正常運作，因為 Windows 無法載入此裝置所需的驅動程式。 (代碼 31) 。裝置管理員中已不再提供所要求的 ALPC 訊息** 」。 在裝置管理員中，以滑鼠右鍵按一下 [混合式現實裝置] 下的耳機，然後選取 [卸載裝置]。 選取 [確定] 以確認並 replug 您的耳機。
4. 如果您看到耳機的部分列舉 (一系列 USB 裝置列舉，但裝置管理員) 中的「混合現實耳機」沒有任何內容，請嘗試使用外部電源的 USB 3.0 中樞。
5. 移至耳機製造商的網站，並更新您耳機的驅動程式和固件。
6. 將您的耳機連接至另一部電腦，然後開啟裝置管理員。 即使該電腦與 Windows Mixed Reality 不完全相容，您仍可查看耳機是否列舉。 如果您的耳機未在多部電腦上列舉，則可能發生硬體問題。

**適用于 Surface 使用者的附注：** 較舊版本的 Surface Dock 和 Surface Book USB Hub 固件更新軟體與混合現實耳機不相容。 如果您在 Surface PC 上收到「連接耳機」訊息，請查看裝置管理員中是否有任何裝置回報「程式 **代碼10：裝置無法啟動」錯誤** 。 如果是，請 [移除衝突的驅動程式](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)。 您應該只需要做一次。

**請注意 Windows 10 N 使用者：** 如果您的電腦執行 Windows 10 N，在插入您的混合現實耳機之後，裝置管理員會看到「 **代碼28：安裝類別不存在或無效」錯誤** 。 Windows Mixed Reality 不支援 Windows 10 的 N 版。 如需詳細資訊，請遵循下列 [指示](troubleshooting-windows-mixed-reality.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 。

### <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>訊息顯示「檢查 USB 纜線」或「USB 速度不足」。

* 確定您是在電腦上使用支援的 USB 3.0 埠：
    * 請確定您的耳機 USB 纜線已插入。
    * 執行 [Windows Mixed Reality PC Check](https://aka.ms/pccheckapp) 應用程式，以確定您的電腦 USB 3.0 控制器受到支援。
    * 嘗試電腦上的每個其他 USB 3.0 埠。 有些電腦有一個以上的 USB 3.0 控制器。
    * 暫時中斷連接到您電腦的所有 USB 裝置，並只連接您的耳機。
    * 在自訂的電腦上，即使埠可能標示為 USB 3.0 埠，它還是可能連接到 USB 2.0 控制器。 在您的耳機連接後，開啟裝置管理員，找出並按一下任何從您的耳機列舉的裝置，然後移至 [ **依連接查看 > 裝置** ]。
* 試用另一台電腦上的耳機。 如果其他電腦與 Windows Mixed Reality 不完全相容，請簽入裝置管理員以查看是否看到「USB 速度不足」訊息。 如果您的耳機未在多部電腦上正確列舉，則您的耳機可能會有問題。

### <a name="the-mixed-reality-portal-did-not-launch-automatically-after-i-plugged-in-my-headset"></a>插入耳機之後，混合實境入口並未自動啟動。

因為基礎問題，可能未正確偵測到耳機。 請嘗試手動啟動混合實境入口，並尋找出現的任何錯誤訊息。 

### <a name="my-headset-stopped-working-after-putting-my-pc-to-sleep-in-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>我的耳機在讓電腦進入睡眠狀態、處於睡眠模式時，或在重新開機電腦時已連接我的耳機時，即停止運作。

1. 開啟裝置管理員並確認您的耳機列在 [混合式現實裝置] 下方。
2. 按兩下 [混合現實裝置] 下的耳機，並確認裝置狀態指出「此裝置運作正常」。
3. 如果您看到「代碼43」錯誤指出裝置已停止運作，或您沒有看到您的耳機列在「混合式現實裝置」底下，請在耳機的 USB 纜線中拔下並 replug。 Microsoft 正在調查可能導致此錯誤的潛在軟體/驅動程式互通性問題。 此問題會影響少量的電腦，而且預期會在未來的混合現實耳機驅動程式更新中解決。

### <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>當我讓電腦進入睡眠狀態或處於睡眠模式時，我的耳機會導致電腦產生錯誤檢查 (藍色螢幕) 。

Microsoft 正在調查可能的軟體/驅動程式互通性問題，這可能會導致少量的電腦產生「9F」錯誤檢查 (藍色畫面) 當電腦進入睡眠狀態或連接到耳機的睡眠模式時。 這個問題預期會在未來的混合現實耳機驅動程式更新中解決。

### <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>當我插入耳機時，不會自動安裝耳機驅動程式。

在新電腦上，或具有新安裝 Windows 10 複本的電腦上，耳機驅動程式可能會排在其他 Windows 更新後方，而且可能不會立即安裝。 如果您有「N」個版本的 Windows，則必須切換至一般版本的 Windows 10，才能使用 Windows Mixed Reality。 若要手動安裝：

1. 移至 [ **開始] > 裝置管理員** ，然後在 [其他裝置] 的 [hololens 感應器] 裝置中尋找黃色驚嘆號： ![ 裝置管理員 HoloLens 感應器的觀點](images/hololenssensors.png)
2. 在裝置上按一下滑鼠右鍵，然後選取 [屬性]。 如果裝置的 [內容] 讀取 **未安裝此裝置的驅動程式 (Code 28)** ，請關閉該視窗，然後繼續。 如果有其他訊息，請遵循此頁面其餘部分的疑難排解步驟。
![裝置管理員中的 HoloLens 感應器的 Code 28](images/code28.png)
3. 再以滑鼠右鍵按一下裝置，然後選取 [更新驅動程式 ...]然後，在裝置更新之後，[自動搜尋更新的驅動程式軟體]，您應該會在裝置管理員： ![ Mixed Reality 裝置出現在 [混合的現實裝置] 下方看到您的耳機：裝置管理員](images/mixedrealitydevices.png)

如果手動安裝無法運作，或是您在其他裝置下找不到驅動程式，則您可能需要卸載現有的驅動程式並重新安裝。 若要這樣做：
1. 移至 [ **開始] > 裝置管理員** ，並查看耳機的 [混合的現實裝置]。 裝置狀態應該會指出「裝置運作正常」。
2. 在裝置上按一下滑鼠右鍵，然後選取 [卸載裝置]。
3. 在出現的新快顯視窗中，選取 [刪除此裝置的驅動程式軟體] 核取方塊，然後選取 [卸載]。
4. 完成時，請從您的電腦拔下耳機，然後將它插回。 Windows Update 現在將會下載並安裝新的驅動程式。

### <a name="troubleshooting-flowchart"></a>疑難排解流程圖

![連接您的耳機/檢查 USB 纜線](images/hmd-connectivity2.jpg)


## <a name="mixed-reality-headset-display-problems"></a>混合現實耳機顯示器問題 ##

### <a name="my-headset-displays-are-black"></a>我的耳機顯示器為黑色。

* 檢查您的電腦效能和穩定性：
    * 使用工作管理員查看是否有任何進程提高電腦的 CPU、GPU 及/或磁片磁碟機。
    * 使用事件檢視器) 查看 Windows (中的應用程式和系統事件記錄檔，以查看您的應用程式經常損毀，並產生 Windows 錯誤報告 (WER) 報告。
    * 請檢查 Windows Update，確定您的 Windows 版本是最新的。 您可能必須選取 [檢查更新] 多次。
* 檢查應用程式和遊戲穩定性：
    * 確定您的電腦符合最低系統需求，才能執行任何未正確執行的應用程式/遊戲。    
    * 確定您的 GPU 驅動程式版本是最新的，並檢查是否有新的效能和相容性問題，以及是否有新驅動程式的回歸。
    * 如果您使用 SteamVR apps 和遊戲，請確定 SteamVR 和 SteamVR 元件的 Windows Mixed Reality 都是最新的。
* 檢查 HDMI 介面卡相容性：
    * 請確定 HDMI 纜線已插入所有的方式。
    * 如果您使用的是 HDMI 介面卡 (例如，迷你 DisplayPort 至 HDMI 介面卡) ，請確定其與 Windows Mixed Reality 相容。 介面卡必須支援 HDMI 2.0，而且有許多較舊的介面卡只支援1080p。 請參閱 [建議的 Windows Mixed Reality 配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)。
    * 外掛程式可能很重要。 先將 HDMI 介面卡連線到您的電腦，再將耳機連接到介面卡，特別是當您使用的是 USB 至 HDMI 介面卡時。 
    * 如果您正在使用延伸模組纜線，請嘗試移除它。
* 檢查圖形配接器和驅動程式相容性：
    * 使用電腦監視器來嘗試您電腦的 HDMI 埠。 有些電腦可能會有一個以上的 HDMI 埠，並非全部都在作用中。
    * 如果您的電腦同時具有整合式圖形處理器 (iGPU) 和離散圖形處理單元 (dGPU) ，請確定您已插入 dGPU 的 HDMI 埠。<br> ![HDMI 埠](images/HP_HDMI_Ports_s.png)
    * 再次檢查您的 GPU 驅動程式版本。 請確定它是最新的，但也請注意任何新的效能和相容性問題，以及對全新驅動程式的回歸。
    * 如果您在膝上型電腦上使用 Mixed Reality，並且從圖形配接器製造商的網站安裝了較新的圖形驅動程式，請嘗試降級為電腦製造商網站或 Windows Update 上提供的最新圖形配接器驅動程式。
    * 如果您有多部電腦監視器連接到您的電腦，請嘗試暫時中斷所有的電腦監視器，而不是一台電腦。
    * 如果您已為電腦監視器設定自訂的重新整理頻率，請嘗試暫時還原為標準的重新整理頻率，例如60Hz。
    * 如果您最近變更了您的圖形配接器，但未重新安裝 Windows，請檢查耳機監視器是否仍安裝正確的驅動程式。 當您的耳機插入電源時，請確認裝置管理員中的 [監視] 節點底下已列出 [混合現實耳機]。
    * 如果您的電腦有 Nvidia 圖形卡，請確定 Nvidia 的3D 視覺軟體已停用。
    * 在某些圖形配接器上 (特別是較舊的圖形配接器) ，HDMI 埠可能不支援 HDMI 2.0，或可能無法完全與 Windows Mixed Reality 相容。 請使用[主動 DisplayPort 1.2 至 HDMI 2.0 適配](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)卡來嘗試您的圖形配接器 DisplayPort 埠
    * Hp product number 1RJ99EA # 阿布達比的 HP Omen Pc 具有與 Windows Mixed Reality 不相容的 HDMI 埠。 若要查看此情況，請開啟「HP 支援助理」，產品編號將會列在應用程式的底部。
    * 如果您的電腦有 AMD Junos r 9 系列圖形介面卡，而您使用的是 Samsung Mixed Reality 耳機，您必須將耳機的固件更新為版本1.0.8 或更新版本，才能使用您的圖形配接器的 HDMI 埠搭配耳機。
    * 如果您是使用 Surface Book 2，請確定您使用的是 [SURFACE USB-C 至 HDMI 介面卡](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)。
* 檢查是否有混合現實耳機硬體問題：
    * 若要確認或排除混合現實耳機的硬體問題，請嘗試將您的混合現實耳機連接至另一台電腦。 
    * 請先檢查電腦相容性和安裝程式問題，因為徵兆很類似。
* 請檢查以確定 USB 纜線已插入 USB 3.0 或更快的埠。 USB 3.0 埠具有 SS () 在其旁邊寫入的速度。 它們通常 (，但不一定) 彩色藍色。        

如果有説明，請參閱下列耳機黑色畫面疑難排解流程圖。

![黑色畫面/看不到任何事](images/hmd-connectivity.jpg)

### <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>在某些用途之後，我的耳機顯示器偶爾會變成黑色。

* 請嘗試停用您電腦可能擁有的任何 USB 暫止或省電功能。 例如，在 Windows 電源選項中， [USB 選擇性暫](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend) 止、在裝置管理員中將 [允許電腦關閉此裝置來節省電源] 設定，以及電腦上任何 USB 電源節約設定。
* 暫時中斷連接到您電腦的任何其他 USB 裝置和週邊設備。
* 再次檢查您的 GPU 驅動程式版本。 請確定它是最新的，但也請注意任何新的效能和相容性問題，以及對全新驅動程式的回歸。

### <a name="one-of-the-displays-on-my-headset-is-black"></a>耳機中的其中一個顯示為黑色。

* 如果您使用的是 HDMI 介面卡，請確定它支援 HDMI 2.0。
* 移除任何您可能使用的 USB 和 HDMI 擴充纜線。
* 請確定您的圖形驅動程式是最新的。
* 在另一部電腦上嘗試混合現實耳機。

### <a name="my-headset-displays-turn-blue-for-a-moment-and-then-mixed-reality-portal-reinitializes"></a>我的耳機會顯示一段時間的藍色，然後混合實境入口重新初始化。

這通常表示您的電腦上發生偶爾的 USB 控制器可靠性問題：
* 嘗試其他 USB 埠。 您的電腦可能有多個 USB 3.0 控制器。
* 如果適用)  (移除任何擴充纜線。
* 嘗試從您的電腦撥出所有其他 USB 裝置。
* 請嘗試將外部驅動的 USB 3.0 中樞連接到您的電腦，並將您的耳機連接至中樞。
* 如果您使用的是桌上型電腦，請考慮購買 USB 3.0 PCIe 卡，以將另一個 USB 控制器新增至您的電腦。

### <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>我的耳機會導致電腦停止回應，或在啟動時顯示黑色畫面。

在某些電腦上，將您的耳機保持在開啟狀態，然後重新開機您的電腦，可能會干擾其啟動流程。 您的電腦可以選取耳機顯示為「主要監視器」來顯示電腦的啟動進度，或無法正常啟動，而且可能會「停止回應」及/或產生嗶聲錯誤碼。 此行為主要取決於 PC 製作和型號，以及/或圖形配接器的製作和型號。 修正方法：
* 將您的耳機連接到您圖形配接器上的不同埠 (您可能需要使用介面卡來) 使用其他埠。
* 請確定電腦的 BIOS/UEFI 固件是最新的 (但如果您很熟悉) ，只會更新您電腦的 BIOS/UEFI 固件。

### <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>使用 Surface PC 時，我的電腦或耳機顯示器閃爍、閃爍或保持黑色。

* 請確定您使用的是支援 HDMI 2.0 的 HDMI 介面卡。 許多較舊的 HDMI 介面卡僅支援1080p 解析度，這對混合現實耳機沒有足夠的支援。
* 請確定您的圖形驅動程式是最新的。 除了檢查 Windows Update 之外，您可能還想要檢查電腦製造商的網站，以取得更新的圖形驅動程式。
* 某些表面裝置與 Windows Mixed Reality 不相容。 深入瞭解 [介面相容性和需求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)。

### <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>當我關機並快速啟動時，我的耳機顯示器無法運作。

從耳機拔下 HDMI 纜線和 USB 纜線，然後將其插回。

### <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>我的耳機顯示器很穩定，但混合實境入口的預覽視窗看起來沒問題。

* 確定您的電腦系統資源 (的 CPU、記憶體和硬碟) 可供使用，而不是由另一個應用程式或進程進行限定或超量。
* 更新您的圖形驅動程式。

### <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>我收到裝置管理員中的「安裝類別不存在或無效」錯誤。

如果您在裝置管理員中看到有黃色驚嘆號的「HoloLens 感應器」，請按兩下裝置以取得其他詳細資料。 如果您看到一則訊息，指出「未安裝此裝置的驅動程式。  (代碼 28) --安裝類別不存在或無效」，這通常是因為您的電腦正在 [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)執行。請注意，N 版的 Windows 10 不支援 Windows Mixed Reality，而且您必須安裝 Windows 10 的非 N 版。

### <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>我的 WMR 環境會在移動前端並顯示雙重視覺時，抖動或口吃。

在具有整合式圖形和 Nvidia GPU 的膝上型電腦上，會在一段時間後發生錯誤，導致先前的畫面格在下一個畫面格之後顯示，導致雙重視覺效果加快偏擺、音調或變換移動頭部的速度。 問題似乎是 Nvidia Graphics Driver 436.48 之後的驅動程式。  安裝此驅動程式將會修正此問題，直到 Nvidia 解決更新驅動程式中的問題為止。 如需直接安裝 Nvidia Graphics Driver 436.48，請造訪 [nvidia](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)。

### <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>我在使用耳機時遇到不適感。
如需在 Windows Mixed Reality 中緩和的一般資訊，請參閱 [Windows Mixed Reality 沉浸式耳機健康情況、安全和緩和](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)。 如需特定耳機的詳細資訊，請洽詢耳機製造商。

### <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>我要如何在我的耳機中取得更清楚的觀點？
請嘗試調整您耳機的大小。 調整其在您臉部的位置，方法是將它向上或向下、向左和向右移動，然後調整母線使其感覺箱子。

如果您的耳機支援，您也可以調整其校正設定。 如果耳機有旋鈕來調整校正，請使用該旋鈕。 如果不是，請移至 [ **設定] > Mixed reality > 視覺品質** ，並在該處調整校正。 如需有關特定裝置的校正的詳細資訊，請洽詢您的耳機製造商。

## <a name="mixed-reality-portal-error-messages-and-problems"></a>混合實境入口錯誤訊息和問題

### <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>我收到「錯誤」的錯誤訊息，或混合實境入口發生問題。

重新開機 Windows Mixed Reality：
1. 從電腦中斷連接耳機纜線。
2. 重新啟動電腦。
3. 重新連接您的耳機。

如果無法運作，請確定您的電腦能夠辨識您的耳機：
1. 選取 [啟動]。
2. 在搜尋方塊中輸入「裝置管理員」，並在清單中選取它。 
3. 展開 [混合現實裝置]，並查看是否已列出您的耳機。 

如果未列出，請嘗試下列動作：
1. 將耳機插入電腦上的不同埠（如果有的話）。
2. 從 Windows Update 檢查是否有最新的軟體更新。
3. 卸載並重新安裝 Windows Mixed Reality：
    1. 從電腦中斷連接耳機纜線。
    2. 選取 [ **> 混合現實 > 卸載] 設定** 。
    3. 選取 **> 裝置 > 藍牙 & 其他裝置的設定** ，以將您的動作控制器。 選取每個控制器，然後選取 [移除裝置]。
    4. 將您的耳機插回電腦以重新安裝 Windows Mixed Reality。
    
### <a name="im-getting-a-check-your-usb-cable-error-message"></a>我收到「檢查您的 USB 纜線」錯誤訊息。

將您的耳機連接至不同的 USB 埠 (，並確定它是 SuperSpeed USB 3.0) 。 此外，請嘗試移除耳機與電腦之間的任何擴充項或中樞。

### <a name="im-getting-a-check-your-display-cable-error-message"></a>我收到 [檢查您的顯示器纜線] 錯誤訊息。

嘗試下列作業：
* 將您的耳機連接至 DisplayPort 1.2 或更新版本，或 HDMI 1.4 或更新版本。 請確定埠與您電腦上最先進的圖形配接器相對應。
* 如果您正在使用介面卡，請確定它可以使用4K。
* 請嘗試使用不同的 HDMI 埠。
* 如果您已將外部監視器插入至 HDMI 埠，請嘗試改為將其插入至 DisplayPort，並將 HDMI 埠用於耳機。


## <a name="something-went-wrong-error-codes-and-how-to-resolve-them"></a>「發生錯誤」錯誤碼以及如何解決這些錯誤代碼

| **Windows 10 錯誤碼** (版本 1809/1709 版、1803)  | **錯誤訊息和疑難排解建議**                    |
|-------------------------------------------------------------|--------------------------------------------------------------------|
|   1-4 / 2197815297-4  | **檢查您的顯示器纜線：確認耳機的顯示器纜線已正確插入。** <br/><br/><ol start="1"><li>拔掉耳機的 USB 和 HDMI 纜線，然後將它們插回。</li><li>檢查裝置管理員並確認在 [監視器] 底下，[混合現實耳機] 監視器存在。</li><li>確定您的圖形驅動程式是由您的圖形配接器製造商的網站)  (最新的。</li><li>如果您是使用介面卡來連接耳機，請確定它 [支援 Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)。</li><li>如果您的圖形配接器同時具有 DisplayPort 和 HDMI 埠，請嘗試在您的圖形配接器上使用 DisplayPort 埠，並使用支援的混合現實 DisplayPort 至 HDMI 介面卡。</li><li>在您的電腦上嘗試其他 USB 3.0 埠</li></ol> |
|   1-5 / 2197815297-5  | **檢查您的顯示器纜線：您的耳機顯示器無法正確初始化。請嘗試重新開機您的電腦並重新連接耳機。**<br/><br/>Windows 會看到您的耳機監視器，但 Windows Mixed Reality 與您的混合現實耳機上的顯示器通訊時發生問題。 修正方法：<br/><ol start="1"><li>確定您的圖形驅動程式是由您的圖形配接器製造商的網站)  (最新的。</li><li>如果您是使用介面卡來連接耳機，請確定它 [支援 Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)。</li><li>如果您的圖形配接器同時具有 DisplayPort 和 HDMI 埠，請嘗試在您的圖形配接器上使用 DisplayPort 埠，並使用支援的混合現實 DisplayPort 至 HDMI 介面卡。</li><li>請嘗試重新開機您的電腦。</li></ol> |
|   7-1、7-2、7-3/2181038087-1、2181038087-2、2181038087-3  | **Windows Mixed Reality 連接到您的耳機時發生問題。請試著拔掉耳機，然後重新插入。**<br/><br/>混合現實耳機無法完全初始化。 這很可能是暫時性錯誤。 拔掉耳機並插回以解決此問題。
|   7-4 / 2181038087-4  | **Windows Mixed Reality 連接到您的耳機時發生問題。請試著拔掉耳機，然後重新插入。**<br/><br/>混合現實耳機驅動程式無法初始化您耳機上的追蹤攝影機。 這很可能是暫時性錯誤。 拔掉您的耳機，然後重新插入，以解決此問題。
|   7-5 / 2181038087-5  | **Windows Mixed Reality 連接到您的耳機時發生問題。請嘗試將您的耳機插入不同的 USB 埠，並暫時拔掉連接到您電腦的任何其他 USB 裝置。**<br/><br/>混合現實攝影機框架時間戳記與電腦時間戳記之間的 Windows Mixed Reality 遺失同步處理。 這可能是暫時性錯誤，或 USB 信號完整性問題的指示。 修正方法：</li><li>暫時拔掉所有 USB 裝置和週邊設備，移除所有的擴充纜線，然後只插入您的耳機。</li><li>在您的電腦上停用任何 USB 暫止/省電功能，例如在 Windows 電源選項中選擇 [暫停]、在裝置管理員中 [允許電腦關閉此裝置來節省電源] 設定，以及您電腦的固件中的任何 USB 省電設定。</li></ul>
|   7-6 / 2181038087-6  | **耳機式固件發生問題。請試著拔掉耳機，然後重新插入。** <br/><br/>這可能是暫時性錯誤。 試著拔掉並重新插入耳機。 如果無法運作：</li><li>檢查 Windows Update 以確定您執行的是最新的耳機驅動程式。</li><li>試用另一台電腦上的耳機。 如果您看到相同的錯誤訊息，則必須提供您的耳機。</li></ul>
|   7-7 / 2181038087-7  | **Windows Mixed Reality 連接到您的耳機時發生問題。請嘗試將您的耳機插入不同的 USB 埠，並暫時拔掉連接到您電腦的任何其他 USB 裝置。**<br/><br/>混合現實耳機驅動程式無法初始化您耳機上的固件。 這可能是暫時性錯誤。 試著拔掉並重新插入耳機。 如果無法運作：<li>暫時拔下您不需要執行 Windows Mixed Reality 的 USB 裝置和週邊設備。</li><li>檢查 Windows Update 以確定您執行的是最新的可用耳機驅動程式。</li></ul>
|   7-11 / 2181038087-11 | **您的 CPU 太舊而無法與 Windows Mixed Reality 相容。**<br/><br/>因為您的 CPU 遺漏了混合現實移動控制器所需的 AVX 指令集，所以您的電腦無法通過相容性檢查。 您將需要 [Windows Mixed Reality 相容的電腦](https://www.microsoft.com/en-us/windows/view-all-devices?col=wmr-pcs#icons)。
|   7-12 / 2181038087-12 | **您的耳機連接到不相容的 USB 控制器。請嘗試將您的耳機插入不同的 USB 埠（如果有的話）。或者，嘗試安裝 Microsoft USB 驅動程式來取代任何不相容的驅動程式。**<br/><br/>您的耳機可能插到連接到不相容非 Microsoft USB 控制器驅動程式的 USB 埠。 這些 USB 3.0 控制器驅動程式通常缺少讀取和處理 [ContainerID 描述](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-containerids-in-windows)項的能力，其會將混合現實耳機的不同部分匯總到同一個單元中， (從正確的耳機播放音訊、將正確的顯示器顯示出來，並從正確的感應器) 提取追蹤資料。 若要變更 USB 控制器驅動程式： <ol start="1"><li>啟動裝置管理員。</li><li>展開 [通用序列匯流排控制器] 的類別，然後按一下滑鼠右鍵，將驅動程式的每個專案（包含「可延伸主機控制器」文字）卸載 **，並** 在名稱中沒有「Microsoft」。</li><li>選取 [刪除此裝置的驅動程式軟體]，以確保移除舊的驅動程式。</li><li>確認每個包含 "可延伸主機控制器" 文字的專案都在結尾有 "Microsoft"。</li><li>插入 HMD。</li></ol>或者，如果問題是間歇性的，HMD 可能無法正確地回應 HMD 驅動程式的命令。 若要修正此問題，請將 HMD 插到30秒以上，然後將其插回。 | 
|   7-13 / 2181038087-13 | **您的耳機連接到不相容的 USB 控制器。請嘗試將您的耳機插入不同的 USB 埠（如果有的話）。如果沒有，您必須安裝新的 USB 3.0 控制器。**<br/><br/>Windows Mixed Reality 無法將混合現實攝影機畫面時間戳記同步處理到您的電腦時間戳記。 這很可能是因為不支援 ITP (同步時間戳記封包) 的不相容 USB 3.0 主機控制器所造成。 請洽詢您的電腦製造商，以查看是否可以啟用 ITP，或切換至另一個具有 ITP 支援的 USB 主機控制器。 |
|   7-14 / 2181038087-14 | **Windows Mixed Reality 連接到您的耳機時發生問題。請試著拔掉耳機，然後重新插入。**<br/><br/>Windows Mixed Reality 在您的混合現實耳機上初始化目前狀態感應器時發生問題。 在裝置管理員中，耳機會顯示錯誤訊息「PoseThread 無法初始化狀態感應器」。 修正方法：<br/><ol start="1"><li>拔掉耳機，然後將它插回。 請確定 USB 纜線已插入。</li><li>在您的電腦上嘗試其他 USB 埠。</li><li>請在另一部電腦上嘗試您的耳機，以查看耳機是否完全以裝置管理員的方式在電腦上進行列舉。</li><li>檢查電腦上是否已安裝任何其他衝突的 HID 驅動程式，例如從您的鍵盤或滑鼠。  (在裝置管理員中尋找具有問號標誌的任何 HID 裝置。 ) </li><li>如果您使用執行 Windows 10 1709 版或1803版的 Samsung Mixed Reality 耳機，請依照錯誤碼2181038087-12 的指示，檢查您的 USB 3.0 控制器是否正在執行非 Microsoft USB 控制器驅動程式。</li></ol> |
|   7-15 / 2181038087-15 | **Windows Mixed Reality 偵測到安裝了不相容的 WinUSB 驅動程式。**<br/><br/><ol start="1"><li>確定電腦上的 WinUSB 驅動程式是 Windows 隨附的驅動程式，而且任何協力廠商 USB 驅動程式都沒有覆寫電腦上的 WinUSB 複本。</li><li>如果問題持續發生，您可能需要復原或重新安裝 Windows 安裝。</li></ol> |
|   13-11/-            | 混合實境入口發生 Windows 的應用程式註冊問題。 檢查應用程式事件記錄檔 (使用事件檢視器) 查看是否有其他詳細資料。 |
|   14-1/-            | 混合實境入口在初始化圖形和組合堆疊時遇到問題。 修正方法：<ul><li>桌面視窗管理員 (DWM，Windows 圖形堆疊) 的主要元件可能會損毀。 檢查應用程式事件記錄檔 (使用事件檢視器) 查看是否發生這種情況。</li><li>請嘗試全新卸載圖形驅動程式，然後從圖形配接器製造商的網站安裝最新的圖形驅動程式。</li></ul> |
|   14-2/C0001160-101  | **連接到您的耳機時發生問題。請嘗試移除您可能使用的任何擴充纜線，並確定您已將耳機連接到您的圖形配接器的正確埠。如果您使用的是任何介面卡，請確定它們與混合的現實都相容。如果您仍然遇到問題，請嘗試更新圖形驅動程式。**<br/><br/>混合現實顯示和組合堆疊無法初始化。 您電腦的圖形配接器或圖形配接器驅動程式可能與 Windows Mixed Reality 不相容。 若要檢查這一點： <ul><li>再次確認您的電腦符合 Windows Mixed Reality 的最低系統需求。</li><li>如果您在 Windows 10 版本1809或更新版本上使用 Dell Inspiron 5577 電腦，您可能會看到此錯誤，是因為與 Dell 的「真處理」後置處理功能發生衝突。 若要解決此問題，請使用 Dell 的「真」應用程式關閉「真」功能，然後再次嘗試執行混合實境入口。</li><li>在桌上型電腦上，從圖形配接器製造商的網站安裝最新的圖形驅動程式。 在膝上型電腦上，從膝上型電腦製造商的網站安裝適用于製造商和型號的最新圖形驅動程式。</li><li>如果您有協力廠商圖形或顯示軟體/附屬應用程式，請暫時卸載這些應用程式和驅動程式。</li><li>選取 [再試一次] 以查看是否為暫時性問題。</li></ul> |
|   14-3/-             | **連接到您的耳機時發生問題。請嘗試移除您可能使用的任何擴充纜線，並確定您已將耳機連接到您的圖形配接器的正確埠。如果您使用的是任何介面卡，請確定它們與混合的現實都相容。如果您仍然遇到問題，請嘗試更新圖形驅動程式。** <br/><br/><ul><li>如果您在電腦監視器上使用任何自訂模式或更新頻率，請嘗試將其重新整理率設定為60Hz。</li><li>請確定您使用的任何介面卡支援 Windows Mixed Reality。</li><li>請嘗試從圖形配接器製造商的網站安裝最新的圖形驅動程式。</li><li>按一下 [再試一次] 以查看是否為暫時性問題。</li></ul> |
| 14-4/-             | **連接到您的耳機時發生問題。請嘗試移除您可能使用的任何擴充纜線，並確定您已將耳機連接到您的圖形配接器的正確埠。如果您使用的是任何介面卡，請確定它們與混合的現實都相容。如果您仍然遇到問題，請嘗試更新圖形驅動程式。** <br/><br/><ul><li>電腦的電腦監視器可能比您的圖形配接器可支援的還要多。 將您的主要電腦監視器全部中斷連接。</li><li>請確定您使用的任何介面卡支援 Windows Mixed Reality。</li><li>從圖形配接器製造商的網站安裝最新的圖形驅動程式。</li><li>按一下 [再試一次] 以查看是否為暫時性問題。</li></ul> |
|   15-5/-             | **混合實境入口已失去與核心混合現實及其相依的 Windows 元件的同步處理。**<br/><br/><ul><li>這可能是因為您的電腦發生效能問題。 請確定您的 CPU、GPU 和 HDD 未在工作管理員中限定。</li><li>暫時中斷所有其他 USB 裝置與電腦的連線。</li><li>重新啟動電腦。</li></ul> |
|   -/H0002000-0    | **您電腦的作業系統進入不相符的狀態以進行 Windows Mixed Reality**<br/><br/>檢查 Windows Update 是否有更新。 |
|   -/S0002261-101、S0002361-101 | **混合現實 shell 元件的問題，導致無法正確啟動混合實境入口**<br/><br/><ul><li>在您的電腦上使用事件檢視器開啟應用程式記錄檔，以在您嘗試開始 Windows Mixed Reality 時，檢查是否有任何應用程式損毀。</li><li>請確定您的圖形驅動程式是最新的。</li><li>您使用的 HDMI 介面卡與 Windows Mixed Reality 不相容。 請參閱 [此處](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)的支援和建議的 HDMI，以將 (DP 的迷你顯示器通訊埠) 。</li></ul> |


## <a name="motion-controller-problems"></a>移動控制器問題

### <a name="my-motion-controllers-arent-working-properly"></a>我的動作控制器無法正常運作。

如果您的 [動作控制器](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) 沒有作用、未連線，或是當您戴耳機時看不到控制器的影像，請嘗試下列動作：
1. 請確定您的控制器已開啟。 若要開啟它們，請按住 Windows 按鈕兩秒鐘。
2. 請確定控制器是完全收費的，如果不是，則更換電池。
3. 將控制器放在您面前之前，請關閉並重新開啟控制器。 按住 [Windows] 按鈕四秒鐘以關閉控制器，然後再按一次再按住兩秒鐘來開啟。 
4. 選取 [ **> 裝置的設定] > 藍牙 &** 電腦上的其他裝置，並確定控制器列示為配對。 如果不是，您必須將 [它們配對](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality)。 
5. 請確定移動控制器顯示為「已連線」。 「配對」不一定表示控制器會連接到電腦。 控制器應該會出現在 [滑鼠、鍵盤 & 畫筆] 類別之下。 [其他裝置] 下的移動控制器無法進行配對程式，且無法正常運作。 檢查動作控制器 Led：已配對並連接明亮的控制器，dimly 亮控制器未連線。
6. 移至 [ **開始] > 混合實境入口** 在您的電腦上，然後選取 [功能表]。 您應該會看到已列出您的動作控制器，以及狀態訊息：
    * 就緒–控制器全都已設定。
    * 遺失追蹤–混合實境入口找不到您的控制器。 將它們放在耳機前方，然後按下 [Windows] 按鈕4秒，再重新開機，再按2秒。
    * 電力偏低–更換控制器電池。
7. 如果您使用的是外部 USB 藍牙介面卡，請確定它已插入黑色 USB 2.0 埠。 它也應該盡可能從任何其他無線發送器或 USB 快閃磁片磁碟機插入，包括耳機的 USB 連接器。 
8. 在 Windows [開始] 功能表上按一下滑鼠右鍵，然後選取 [裝置管理員]，確認電腦上只有一個藍牙無線電。 展開 [藍牙] 區段，並尋找一個介面卡。 如果您使用具有內建無線電的桌上型電腦設定，請檢查是否已連接外部天線。 如果沒有連線的外部天線，可能會導致追蹤問題。 或使用外部藍牙轉換器 (USB) 、停用內部藍牙功能，然後重試配對和連接。
9. 關閉 [藍牙設定] 視窗（如果已開啟）。 如果是在背景中開啟，則會對藍牙通訊協定進行許多額外的呼叫。
10. 檢查移動控制器上的虛擬電池音量。 在 [混合式事實] 中，開啟控制器，您就可以看到電池圖示。 若為紅色，則更換電池。 電池報告通常會在連接控制器後立即回報高於實際層級的報告。 等候約15秒，讓電池計量穩定，然後閱讀層級。
11. 在 [設定] > 裝置中移除藍牙耳機和喇叭 **> 藍牙 & 其他裝置** ，然後關閉裝置。 在您的混合現實耳機上使用耳機插口或內建喇叭，以獲得最佳的音訊體驗。
12. 如果您有其他 Bluetooth 裝置與您的電腦（例如耳機或 gamepads）配對，請將其移除。 選取 [ **> 裝置的設定] > 藍牙 & 電腦上的其他裝置** ，選取裝置，然後選取 [移除裝置]。
13. 拔掉耳機上的 USB 纜線，然後將它插回電腦以重新開機電腦上的控制器功能。
14. 控制器燈在進行固件更新時閃爍。 等候固件更新完成，控制器應該會出現在混合的現實中。
15. 請確定您的電腦已連線到5GHz 的 Wi-fi 網路。 如果您的膝上型電腦連線到 2.4 GHz Wifi 網路，通常會共用藍牙連線。 這可能會對 Wifi 或藍牙效能造成負面影響，視產品設計而定。 在網路介面卡設定中，將慣用的頻外變更為5Ghz。 如果您的網路不支援5GHz，則可以使用藍牙轉換器，而不是使用內部藍牙功能。
16. 如果您的藍牙設定已經配對，除非已將新的裝置移除，否則除非已使用特定的轉換器新增裝置，否則 Windows 將不會探索新裝置 (如果已使用特定的轉換器來新增裝置，則只能將其與該轉換器) 移除。
17. 如果您的電腦有內建的藍牙，而您遇到連線問題，請嘗試改用 USB 藍牙介面卡。 若要這樣做，您必須關閉裝置管理員中的內建藍牙無線電，然後將其他 Bluetooth 裝置與新的介面卡配對。

### <a name="motion-controller-troubleshooting-flowchart"></a>移動控制器疑難排解流程圖

![動畫控制器的疑難排解流程圖](images/motion-controllers.jpg)

### <a name="my-controller-is-stuck-in-an-infinite-reboot-buzzing-after-leds-cycle"></a>我的控制器卡在) 的 Led 迴圈之後，在無限重新開機 (聲止。

這是很重要的電池指標，因此請確定您的裝置有新的電池。 如果問題持續發生，請執行 [裝置](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) 復原，將控制器重設為原廠設定。

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>我正在嘗試配對控制器，但它們永遠不會顯示在 [藍牙設定] 的 [新增裝置] 功能表中。

檢查您是否已有未配對的控制器，請將其移除，然後再試一次。 如果問題持續發生，請重新開機電腦，然後再試一次。 如果失敗，請參閱 [藍牙常見問題](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。

### <a name="wi-fi-speeds-becomes-slow-on-my-notebook-when-motion-controllers-are-turned-on"></a>開啟運動控制器時，wi-fi 速度會變慢。

連線至 2.4 GHz 存取點時，您的筆記本可以與藍牙共用其 Wi-fi 天線。 如果您可以將波段喜好設定切換為5GHz，請從 [裝置管理員] 進行檢查。 如果無法使用5GHz 網路，而且效能受到嚴重的影響，請考慮使用藍牙轉換器。

![您可以透過 [裝置管理員] 找到 Wifi 波段選項設定](images/wifi5ghz.png)

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>我的第二個控制器需要很長的時間才能重新連接。

當移動控制器同時開啟時，某些較舊的 Intel 無線電波會遇到此問題。 避免同時開啟控制器。

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>我的 Qualcomm 藍牙無線電無法在電腦損毀之後配對控制器。

Qualcomm (QCA) 之前的藍牙無線電驅動程式在 Windows 損毀之後可能會處於不良狀態。 完全關閉電腦的電源來解決這個問題。 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>我在使用 Marvell 無線電時遇到不良的控制器追蹤。

移至 **裝置管理員 > 藍牙 > MARVELL AVASTAR 藍牙無線電介面卡 > 屬性 > 驅動程式** ，並確定您使用的是驅動程式15.68.9210.47 或更新版本。

### <a name="the-mixed-reality-portal-is-working-but-my-motion-controllers-are-tracking-poorly-controllers-keep-flying-away-shaking-etc"></a>混合實境入口可正常運作，但我的運動控制器正在追蹤不佳 (控制器會保持飛出、搖動等 ) 。

1. 某些照明條件可能會影響追蹤。 請確定您不會暴露在直接照明的情況下，而且您的 (HMD 不會看到很多的點光源，例如，像是耶誕節樹狀結構的燈等字串) 。 
2. 查看 [藍牙常見問題](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。 這些徵兆通常是因為控制器與主機電腦之間的通訊失敗，並指出藍牙連結品質不佳。

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>移動控制器 Led 不亮，但按鈕和操縱杆仍能在混合實境入口中運作。

移動控制器校正快取可能已損毀。 若要刪除快取，請在系統管理員命令提示字元中執行下列命令：

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

此資料夾無法在 Windows 檔案總管中存取，而且只能從系統管理員命令提示字元修改。 刪除資料夾之後，請重新開機您的電腦，然後重新連接您的動作控制器來還原校正檔案。

### <a name="motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>移動控制器不會出現在 SteamVR apps 和遊戲中。

如果您能夠在 cliff 房子中看到您的運動控制器，但無法在 SteamVR 的應用程式和遊戲中看到，移動控制器模型驅動程式可能無法正確安裝。 此驅動程式會透過 Windows Update 自動下載並安裝，但如果您是在具有企業原則的電腦上，或者如果 Windows Update 其他限制，您可能需要手動安裝。 若要檢查是否已正確安裝移動控制器模型驅動程式：
1. 開啟這兩個動作控制器，並確定它們在 [裝置] 下的 [設定] 應用程式中顯示為 [已連線]， **> 藍牙 & 其他裝置** 。 如果未顯示或顯示為「配對」，請將 [它們配對](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality)。
2. 開啟裝置管理員，然後在 [藍牙] 下尋找「移動控制器-左方」和「動作控制器-右側」。
3. 選取 [裝置]，然後移至 [ **依連接查看 > 裝置** ]。
4. 您現在會看到移動控制器藍牙裝置匯總到藍牙無線電的觀看。 在與兩個動作控制器相同的節點下，應該是兩個「Bluetooth HID 裝置」裝置，而且在每個藍牙 HID 裝置下都應該是名為「移動控制器」 (並) 灰色圖示的裝置。
5. 按兩下每個「移動控制器」裝置，然後移至 [ **驅動程式** ] 索引標籤。確認列出的驅動程式版本對應到其中一個 [移動控制器模型驅動程式版本](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history)。

若要手動下載並安裝移動控制器模型驅動程式，請流覽 [此頁面](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) ，並尋找與您的 Windows 10 版本對應的驅動程式版本。 您可以從下載頁面取得安裝指示。

### <a name="the-motion-controllers-firmware-update-takes-significantly-longer-than-two-minutes"></a>移動控制器固件更新花費的時間明顯超過兩分鐘。

查看 [藍牙常見問題](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。 藍牙連結品質不佳通常是這些問題的原因。

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>我剛剛插入了新電池，但是控制器的虛擬電池計量並沒有指出完整的層級。

移動控制器電池音量已針對 AA 電池調整。 部分低電壓充電電池可能不會報告為完整，但會完全收費。

### <a name="my-controller-does-not-vibrate-when-battery-is-low"></a>當電池計量偏低時，我的控制器不會震動。

當電池計量偏低時，會停用 Haptics。 更換您的電池。

### <a name="my-device-vibrated-three-times-and-then-shutdown"></a>我的裝置 vibrated 三次，然後關機。

您的電池不足，並達到截止閾值。 更換您的電池。

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>我的 Samsung 移動控制器的觸控板已關閉，或有不正確位置。

這可能是硬體瑕疵，您應回到零售商或設備製造商，以進行更換或交換。

### <a name="the-controller-isnt-working-correctly-and-i-cant-update-the-device"></a>控制器無法正常運作，且無法更新裝置。

將它還原至原廠條件 (您將需要全新的電池) ：
1. 拔掉控制器電源並關閉電源。
2. 開啟電池蓋。
3. 插入新的電池。
4. 按住 [配對] 按鈕 (電池) 下底部的索引標籤。
5. 按住 [配對] 按鈕時，按住 [Windows] 按鈕五秒，即可開啟控制器電源， (保持兩個按鈕) 。
6. 釋放按鈕，並等候控制器開啟電源。 這最多需要15秒的時間，而且在裝置復原發生時不會有任何指標。 如果裝置在按鈕發行時立即開啟電源，修復按鈕序列就不會註冊，您必須再試一次。
7. 移至 [ **設定] > 藍牙 > 其他裝置** ]，然後選取 [移動控制器-左方] 或 [動作控制器-右方] 和 [移除裝置] ) 以從藍牙設定移除舊的控制器關聯。 
8. 再次將控制器與電腦配對。
9. 連接主機和 HMD 之後，裝置將會更新至最新的可用固件。

### <a name="lights-and-indicators"></a>燈光和指標

LED constellation 環形和 haptics 指出移動控制器的狀態。

| State    | 導致狀態的原因 | 與狀態相關聯的燈光和震動行為 |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **開啟電源**               | 按住控制器上的 Windows 按鈕兩秒，以開啟控制器。       | Led 會開啟和控制器震動一次。 |
| **關閉電源**              | 在控制器上按住 Windows 按鈕四秒鐘，以關閉控制器。      | Led 關閉和控制器震動兩次。 |
| **休眠中**               | 當控制器 motionless 30 秒時，會自動進入睡眠狀態。 當控制器偵測到動作時，控制器會自動喚醒，但裝置未與主機電腦配對的情況除外。 在這種情況下，按下按鈕將需要喚醒。 | Led 會在睡眠狀態下每三秒關閉並閃爍。 |
| **配對**                | 按下並按住電池內的配對按鈕三秒鐘。     | 當配對模式時，Led 會慢慢地進入脈衝狀態，並在結束配對模式時進入穩固。 如果配對成功，則控制器會震動一次，如果配對失敗和超時，則會震動三次。 |
| **控制器連接/中斷與電腦的連線** | 當控制器開啟後，控制器會成功連線到電腦，而在使用時，控制器會與電腦中斷連接。| 控制器會在電腦連線或中斷連接時震動一次。 |
| **電力偏低等級**      | 電池計量偏低。| 當電池計量偏低時，不會有 LED 或震動的指示。 耳機中控制器標記法的控制碼上有電池指標圖示。 當電池計量偏低時，指標圖示會顯示1/4 已滿。 |
| **電力不足等級** | 當電池計量為「重大」時開啟電源。 「重大」電池等級表示電源不足，控制器將會自動關閉。| 當您開啟控制器時，控制器會震動三次，然後自動關閉。 當您使用此狀態時，電池指示器圖示會顯示紅色。 |


### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>如何得知我是否使用藍牙技術？

移動控制器使用許多消費者裝置中的相同藍牙技術，其設計目的是要與任何最近的電腦上所包含的藍牙功能搭配使用。 若要確認您的電腦具有藍牙無線電 (如果裝置通過混合現實相容性檢查程式，則應該) ： 
* 以滑鼠右鍵按一下 Windows [開始] 功能表，然後選取 [裝置管理員]。 
* 展開 [藍牙] 區段，並尋找介面卡。 
* 如果您的電腦沒有藍牙，則建議使用的其中一個轉換器是 [PLUGABLE USB 藍牙4.0 低功耗微介面卡](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom)。
![範例裝置管理員的螢幕擷取畫面。 介面卡是藍牙無線電。](images/devicemanagerbtadapterpic.png) 


### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-motion-controllers"></a>我的電腦具有藍牙技術，但我的動作控制器有問題。

移動控制器應該與其他 Bluetooth 鍵盤、滑鼠和遊戲控制器搭配運作，但其體驗會依您使用的鍵盤、滑鼠或遊戲控制器的模型而有所不同。 以下是您可以用來改善效能的一些事項：
* 如果您的電腦具有藍牙，但仍有行動電話控制器的問題，請考慮將您的藍牙無線電取代為插入 USB 的 Plugable 外部藍牙介面卡。 請注意，您一次只能有一個使用中的藍牙無線電配接器。 如果您在現有的電臺以外插入外部電臺，您必須在裝置管理員中停用現有的藍牙無線電 (以滑鼠右鍵按一下介面卡，然後選取 [停用裝置] ) 並取消配對所有先前的藍牙裝置。
* 如果您使用的是 USB Bluetooth 介面卡，請將它連接到 USB 2.0 埠 (2.0 埠為黑色，且未標示為 "SS" ) （如果有的話）。 埠應與下列實體分開：
    - HMD USB 連接器
    - 快閃磁碟機
    - 硬碟
    - 像是鍵盤/老鼠的無線 USB 接收器，理想的情況是將 USB Bluetooth 介面卡盡可能插入電腦的相反端。
* 請勿安裝任何協力廠商軟體。
* 關閉 [藍牙設定] 視窗（如果已開啟）。 讓它在背景中保持開啟，表示會對藍牙通訊協定進行許多額外的呼叫。
* 在 [藍牙 & 其他裝置] 下，停用 [顯示通知以使用迅速配對] 設定，以減少主機無線電掃描活動。
* 如果您使用的是內部藍牙卡，請確定您使用的是外部藍牙天線。 
  * 在此情況下，缺乏外部藍牙天線的已知原因是追蹤問題。 
  * 如果無法運作，請在停用內部藍牙之後，使用外部藍牙轉換器 (USB) 。
* 裝置必須出現在藍牙設定的 [滑鼠、鍵盤 & 畫筆] 類別之下。 如果在 [其他裝置] 下，則將並配對裝置。
* 移除、取消配對，以及關閉藍牙耳機和喇叭的電源。 Windows Mixed Reality 不支援這些。 您可以在混合現實耳機上使用耳機插口或內建喇叭，以獲得最佳的音訊體驗。

### <a name="how-can-i-pair-my-motion-controllers-to-a-windows-mixed-reality-headset-with-built-in-bluetooth-radio-or-return-them-to-their-factory-pairing"></a>我要如何將動畫控制器與內建藍牙無線電的 Windows Mixed Reality 耳機配對，或將它們退回給廠配對？

某些 Windows Mixed Reality 耳機（包括 Acer OJO 500 和 Samsung 電影對白 +）有內建的藍牙無線電波可搭配運動控制器使用。 隨附于這些耳機的移動控制器會預先配對至原廠的耳機，不需要您的電腦具有個別的藍牙無線電。 您 _可以_ 手動將這些移動控制器與電腦的藍牙無線電配對，例如與沒有內建藍牙無線電的 Windows Mixed Reality 耳機搭配使用。 若要將移動控制器歸還給站配對，或將它們與內建藍牙無線電的 Windows Mixed Reality 耳機配對，請執行耳機的裝置附屬應用程式 (例如，"Acer OJO 500" 應用程式或 "Samsung HMD 電影對白 + Setup" 應用程式，會在首次耳機插入) 時自動安裝，並遵循行動電話控制器配對的指示。


## <a name="performance-questions"></a>效能問題

### <a name="how-can-i-tell-if-the-windows-mixed-reality-headset-is-rendering-at-60hz-or-90hz-framerate"></a>如何判斷 Windows Mixed Reality 耳機是否以60Hz 或90Hz 幀呈現？

檢查 **裝置入口網站 > 效能** ] 索引標籤。 

**注意** ：如果您的離散 GPU 具有 HDMI 2.0 埠，而 CPU 有四個以上的實體核心，則應該取得 90 Hz。 如果您的 GPU 只有 HDMI 1.4 輸出，您可以使用 DisplayPort 至 [HDMI 2.0 介面卡](https://holodocswiki.com/wiki/Recommended_adapters_for_Windows_Mixed_Reality_Capable_PCs) 作為因應措施。 

**注意** ： **耳機顯示器 > 視覺品質設定** 只會影響 Windows Mixed Reality 首頁體驗的呈現。

### <a name="what-do-i-do-if-my-pc-appears-to-be-running-slowly"></a>如果電腦的執行速度很慢，該怎麼辦？

系統可能會因為許多原因而變慢，在大部分情況下，這會在幾秒鐘後減少。 如果您在一段長時間內遇到此問題：
1. 關閉桌面上所有未使用的應用程式。
2. 確定您的膝上型電腦已插入電源來源。
3. 確定電腦未準備好。
4. 降低 Windows Mixed Reality 首頁的視覺品質。
5. 確定您的電腦有最新的圖形驅動程式 (請參閱) 的 [圖形驅動程式] 區段。

### <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>我的電腦在執行混合現實體驗時正在準備。 如何? 保持不酷？

1. 確定電池已收費，而且電源來源已插入。
2. 請確定不會封鎖進出電腦的風扇。
3. 在相當酷炫的環境中使用電腦。
4. 請確定沒有任何熱度來源 (例如，在電腦上) 的太陽或熱度通風。

### <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>我的視覺效果斷斷續續、載入速度很慢，或看起來沒問題。
* 請確定您的耳機已插入您電腦上正確的圖形配接器。 有些電腦具有整合式和離散的圖形配接器。 離散卡片通常會提供最佳效能。 [深入瞭解電腦硬體](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)。
* 關閉桌面上未使用的應用程式。
* 確定您的耳機適合 snugly (將它移到較低和更高或左右左右，以調整) 。
* 在 [ **設定] > 混合現實 > 耳機顯示** 中調整您的耳機視覺效果設定。 當「視覺品質」設定為「自動」時，我們會為您的電腦選擇最佳的混合現實體驗。 如需更多視覺效果詳細資料的體驗，請將「視覺品質」設定為「高」。 如果您的視覺效果斷斷續續，您可能會想要選取較低的設定。
* 請嘗試調整耳機的校正。 應調整鏡頭以符合您的 interpupillary 距離 (IPD) ，也就是瞳孔之間的距離。 如果您不知道您的 IPD，optometrist 應該能夠為您進行測量。 也有設計來測量 IPD 的網站。 知道您的 IPD 之後，請使用耳機的校正旋鈕來進行調整。 如果耳機沒有校正旋鈕，請選取 [ **設定] > 混合現實 > 耳機顯示** 並調整「校正控制項」。


## <a name="tracking-system-problems"></a>追蹤系統問題

### <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>系統找不到界限，而且我會看到安裝程式 UI。

這表示追蹤系統無法辨識您的環境。 如果您是在新的環境中，您必須設定 [界限](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)。 如果您先前曾在此環境中使用裝置，並設定界限：
* 請確定房間有足夠的光線。
* 請確定您已將裝置磨損，並已查看房間。 裝置必須觀察您的環境，以瞭解其所在位置。 如果它位於桌上或桌上，它就不會找到您的界限。
* 將裝置拔下，關閉 Windows Mixed Reality，然後重新插入裝置。
* 您的環境中可能已有某些變更，而裝置無法再辨識。 嘗試設定新的界限。

如果這些步驟無法解決問題，則請刪除您的環境資料，然後再次設定界限。

### <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>系統會向我呈現 UI，要求我針對所有體驗或站上/站選設定，並看到我的範圍。

裝置花太多時間找出界限。 您可以藉由選擇使用界限的選項來略過此訊息，系統會將您的界限帶到您的 Windows Mixed Reality Home。

### <a name="i-frequently-see-a-message-saying-ive-lost-my-bounds"></a>我經常會看到一則訊息，指出「我已遺失界限」。

追蹤系統正在追蹤及識別您的環境。 在此狀態下，裝置不會再顯示您的界限，而耳機會切換至3DOF，讓您能夠上下加減一點到真實世界中的專案，直到它再次找到您的界限為止。 修正方法：
1. 請確定房間有足夠的光線。
2. 如果您最近 redecorated 或改建年份空間，請重新執行安裝程式。
3. 拔掉裝置，關閉 Windows Mixed Reality，然後重新插入。
4. 清除您的環境資料，然後再次設定裝置。
5. 如果訊息持續存在，請洽詢客戶支援。

### <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>我可以查看，但無法轉譯 (我卡在 3DOF) 。

這表示追蹤系統無法產生姿勢，或應用程式已停止使用新的姿勢資料來呈現。 檢查下列項目：
* 請確定房間有足夠的光線。
* 請確定房間有足夠的詳細資料可供追蹤。
* 拔下裝置，關閉 Windows Mixed Reality，然後重新插入裝置。
* 如果訊息持續存在，請洽詢客戶支援

### <a name="the-view-in-the-hmd-is-completely-frozen"></a>HMD 中的視圖已完全凍結。

這通常表示應用程式或系統層級元件已失敗。 嘗試：
1. 按 [首頁] 按鈕以離開應用程式。
2. 拔掉裝置，關閉 [MRP]，然後重新插入裝置。
3. 重新開機電腦。

### <a name="i-frequently-see-a-black-border-around-the-edges-of-the-view-in-the-hmd-sometimes-it-looks-like-im-looking-down-a-tunnel"></a>我經常會在 HMD 的邊緣周圍看到黑色框線。 有時看起來像是一個通道。

這表示應用程式無法在您的電腦上叫用畫面播放速率，而且系統會使用舊的畫面格在 HMD 中呈現視圖。 由於應用程式只會轉譯您正在查看的世界部分，如果它們不會一直碰到畫面播放速率，系統就會嘗試繼續從先前的觀點來呈現世界，並以黑色填滿遺漏的詳細資料。 如果經常發生這種情況：
1. 關閉或終止所有不必要的程式，以釋放記憶體和 CPU。
2. 減少應用程式中的詳細資料設定。
3. 減少 Windows Mixed Reality 設定中的詳細資料設定。

### <a name="the-view-in-the-hmd-is-jittering-and-stuttering-a-lot"></a>HMD 中的觀點是 jittering，而間斷情形很多。

有幾個原因可能會發生。 主要的原因是系統無法轉譯內容到耳機，或追蹤系統發生問題。 檢查下列項目：
1. 確定您的電腦未遭受資源爭用。 開啟工作管理員並確保您的計算資源是免費的 (例如，80% 的 CPU 可用、ram 400MB 和磁片 IO 低於 80% ) 。
2. 確定您擁有最新的硬體圖形驅動程式。 如需詳細資訊，請參閱圖形驅動程式一節。
3. 請確定房間有足夠的光線。
4. 將裝置拔下，關閉 Windows Mixed Reality，然後重新插入裝置。
5. 重新啟動電腦。
6. 如果問題持續發生，請洽詢客戶支援。

### <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-before-returning-to-normal"></a>在恢復正常之前，此世界短暫旁邊，可能是傾斜或翻轉。

這可能是因為應用程式或系統層級元件發生嚴重錯誤，或是暫時性缺乏記憶體或 CPU 資源所造成。 檢查下列項目：
1. 開啟 [工作管理員]，並確定您有至少20% 的 CPU 可用和400MB 記憶體可用 (例如 80% CPU 可用、ram 400MB 和磁片 IO 低於 80% ) 。
2. 開啟 [事件檢視器]，然後移至 [ **Windows 記錄檔] > [應用程式** ]，並在凍結時移至 [錯誤事件] 專案。 查看是否有任何進程損毀。
3. 如果此問題持續發生，請嘗試重新開機電腦。

### <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>世界會短暫反轉，並返回正常狀態。

這通常是因為從耳機取得感應器資料以通知追蹤演算法的錯誤所造成。 如果經常發生這種情況：
1. 將耳機插入不同的 USB 3.0 埠。
2. 將耳機直接插入電腦，而不是 USB 3.0 中樞。
3. 如果問題持續發生，請洽詢客戶支援。

### <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-fine-in-windows-mixed-reality"></a>世界是傾斜的，但我可以在 Windows Mixed Reality 中流覽和四處解說。

這通常是因為感應器資料錯誤會記錄到儲存在您電腦上的環境資料中。 這可能會導致 Windows Mixed Reality 出現傾斜，有時會永久出現。 嘗試下列作業：
1. 拔掉 HMD，關閉 Windows Mixed Reality 並插上耳機。
2. 重新開機電腦。
3. 清除您的環境資料。

## <a name="webvr-questions"></a>WebVR 問題

### <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>從 Edge 查看 VR 內容時，為什麼看不到我的控制器？

並非所有 WebVR 內容都是為了支援移動控制器而撰寫的。 WebVR 可讓內容開發人員支援不同類型的輸入，例如遊戲控制器或動作控制器。 如果您在網站上看不到您的控制器，可能是沒有動作控制器支援。

### <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>為什麼我無法在沉浸式 WebVR 視圖中使用滑鼠？

這是 WebVR 規格的選擇性功能。 並非所有瀏覽器都支援這項功能，而且並非所有 WebVR 內容都是為了支援滑鼠輸入而撰寫的。 WebVR 可讓內容開發人員支援不同類型的輸入，例如滑鼠、鍵盤、遊戲控制器或移動控制器。 滑鼠輸入行為會依瀏覽器而有所不同。 在 Microsoft Edge 中，網站作者必須確保在向耳機呈現時，會使用「pointerlock」來執行滑鼠輸入。

### <a name="why-does-my-controller-look-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>為什麼我的控制器看起來像是 Vive/Oculus，有奇怪的方向，或按鈕的對應不正確？

網站可能沒有完整的移動控制器支援。

### <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardiannew-york-times-etc-from-edge-in-vr"></a>為什麼我無法從 Youtube/Facebook/Vimeo/守護者/紐約時間，以及在 VR 的邊緣查看360度的影片？

就像任何其他 web 規格或標準一樣，作者也可以選擇執行它。 有一種 WebVR 規格，可讓網站直接從瀏覽器啟動 VR 體驗，而這些網站的作者目前尚未執行此規格。 某些平臺上可能會有可下載的應用程式，可讓您從這些廠商查看 VR 內容。

### <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>為什麼我無法從 Firefox 或 Chrome 輸入 VR？

目前只有 Edge Windows Mixed Reality 裝置才支援 WebVR。

### <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>當我從網站輸入 VR 時，為什麼我會在耳機中看到空白畫面？

網站可能尚未支援多 GPU 機器 (包括混合式 GPU 膝上型電腦) 。 嘗試：
* 重新載入頁面。
* 在桌上型電腦上，將耳機插入與顯示 Microsoft Edge 的監視器相同的圖形介面卡中。 將兩者插入至較高的電源圖形配接器，而不是整合式圖形介面卡。

### <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>當我在從 Edge 觀看影片時結束 VR 時，音效會持續播放，但 Edge 視窗會呈現灰色。

這是在混合現實 cliffhouse 中從邊緣執行 WebVR 時的已知問題。 若要解決此問題，請在鍵盤上按下 esc 鍵，而不是按下 [windows] 按鈕以結束 WebVR 體驗，或是選取它，然後停止影片來啟用灰色的邊緣視窗。

### <a name="can-i-use-webvr-on-the-hololens"></a>我可以在 HoloLens 上使用 WebVR 嗎？

Microsoft 目前尚未在 HoloLens 上宣佈任何關於 WebVR 的資訊。

### <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>當您從 Edge 觀看 WebVR 內容時，為什麼我的視圖位於樓層層？

網站未適當支援 Windows Mixed Reality 耳機。 若要解決這個問題︰
1. 將耳機放在您的空間地板上。
2. 使用桌面上的 Microsoft Edge 流覽至 [WebVR] 頁面， (不在混合現實) 內。
3. 按一下網頁上的按鈕，以輸入 VR。
4. 等候5-10 秒，讓體驗完全進入沉浸式模式。
5. 拿到耳機，把它放在您的頭部。

### <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>在某些 WebVR 體驗中，顯示器的解析度極低。

網站未適當支援高解析度耳機。 若要解決此問題：
* 如果從 (桌面啟動 WebVR，而不是從 Mixed Reality cliffhouse) 內，請確定視窗在進入 VR 之前都已最大化。
* 請避免在您輸入 VR 之後調整 Microsoft Edge 視窗的大小。

### <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>為什麼在變更瀏覽器索引標籤時，WebVR 沉浸式視圖結束？

這是預期行為。 基於安全性理由，只有作用中的瀏覽器索引標籤可以存取 connected 耳機。

### <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>為什麼我無法聆聽特定 WebVR 體驗的音訊？

網站可能使用 OGG 音訊檔案格式，Microsoft Edge 目前不支援此格式。

您可以直接向 [問題追蹤](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)程式中的 Microsoft Edge 瀏覽器小組報告已中斷的網站，或使用 [#EdgeBug](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)主題標籤，透過 twitter 來回報。

### <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>為什麼 Haptic 意見反應無法在使用移動控制器的 WebVR 中運作？

Microsoft Edge 目前不支援 WebVR 遊戲台 API 擴充功能上的 haptics。


## <a name="steamvr-questions"></a>SteamVR 問題

### <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-immersive-headset"></a>我要如何在 Windows Mixed Reality 的沉浸式耳機播放 SteamVR 遊戲？

您必須在電腦上安裝 SteamVR Windows Mixed Reality，並設定 SteamVR：
* [下載並安裝 SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)。
* 開始 SteamVR。 SteamVR 教學課程應該會自動啟動。
* 將您的耳機連接到您的電腦，然後開啟您的動作控制器。
* 一旦載入 Windows Mixed Reality 首頁，並顯示您的控制器，請在您的桌面上開啟串流應用程式。
* 使用流應用程式從您的串流庫啟動 SteamVR 遊戲。 若要在不離開耳機的情況下啟動 SteamVR 遊戲，您可以在 Windows Mixed Reality **開始 > 所有應用程式** 中找到並啟動遊戲。 

### <a name="i-get-a-message-that-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>我收到一則訊息，指出「若要搭配 Windows Mixed Reality 使用 SteamVR，您必須安裝最新的 Windows Update」或「需要 Windows 開發人員模式」。

1. 確定您的電腦正在執行最新版本的 Windows 10。 若要檢查這一點，請移至 [ **設定] > 系統 > 相關資訊** 。 在 [Windows 規格] 下，確定 [作業系統組建] 為16299.64 或更新版本。
2. 請確定您沒有任何更新正在等候下載或安裝。 移至 [ **設定] > 更新 & 安全性 > Windows Update** 然後選取 [檢查更新]。 您可能必須多次檢查更新，因此請繼續檢查更新，直到沒有其他可用的更新，然後重新開機電腦為止。

### <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR 在更新 Windows 之後損毀。

某些較舊版本的 SteamVR Windows Mixed Reality 不再與 Windows 相容。 您可能會有 SteamVR 的舊版 Windows Mixed Reality。 確定您是最新的：
1. 在您的串流媒體櫃中，移至 [ **軟體 >] Windows Mixed Reality 以進行 SteamVR** 。
2. 以滑鼠右鍵按一下該檔案，然後移至 [屬性]。
3. 選取 [更新] 索引標籤，然後選取 [永遠將此應用程式保持在最新狀態]。
4. 請前往 [本機檔案] 索引標籤，然後選取 [驗證應用程式檔的完整性]，來強制更新。
5. 重新開機流和 SteamVR。

如果 SteamVR 在更新之後仍損毀，您可能會在電腦上有兩個用於 SteamVR 的 Windows Mixed Reality 安裝。 若要確認是否為這種情況：
1. 找出%localappdata%\openvr\openvrpaths.vrpath，然後在 [記事本] 中開啟它。
2. 在 [外部驅動程式] 區段中，尋找 "MixedRealityVRDriver" 的多個專案 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. 如果您看到多個專案，請移除兩個專案中的舊專案。 請注意，當您只有一個專案時，行尾應該不會再有逗號，例如：
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. 儲存並關閉檔案。
5. 重新開機流和 SteamVR。

### <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>我的控制器在 SteamVR 中未如預期般運作。

1. 關閉 SteamVR。
2. 返回 Mixed Reality 首頁，並確認您的控制器如預期般運作。
3. 再次啟動 SteamVR 體驗，您的控制器應該恢復正常。
4. 如果問題持續發生，請使用混合現實類別下的 [Windows 意見反應中樞](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) 提出意見反應，並在摘要中包含 SteamVR。

請注意，您將在不同的遊戲中使用不同的移動控制器。 以下是一些可協助您開始使用的基本概念：
* 若要開啟 [串流] 儀表板，請在左側操縱杆上按直向下。
* 若要結束 SteamVR 遊戲並回到 Windows Mixed Reality 首頁，請按 [Windows] 按鈕。 然後選取畫面上顯示的 Mixed Reality 首頁按鈕。

### <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>我的左側和右側控制器會在 SteamVR 中反轉。

從您的控制器開始遊戲，然後開啟左側的遊戲，再按右邊一。

### <a name="my-games-are-running-slowly"></a>我的遊戲執行速度很慢。

1. 確認您的電腦符合 Windows Mixed Reality 的 SteamVR 規格
2. 確認您的電腦符合您所播放 SteamVR 遊戲的規格。
2. 在桌面上的混合實境入口中，選取 [暫停] 以停止桌面預覽版。
3. 遵循上面的指示，確定您正在執行 Windows 10 組建16299.64 或更新版本。
4. 請確定您的電腦具有最新的圖形驅動程式。
5. 檢查工作管理員，查看您的電腦上有哪些其他處理常式正在執行，並耗用資源。
6. 查看串流是否正在背景下載遊戲。 這可能會耗用資源，讓遊戲的執行效能不佳。
7. 已知的效能問題會影響沒有可見視窗的小型應用程式類別，例如 SteamVR Home。 大部分的應用程式並不屬於這個類別，未來的更新將會提供修正。

如果您仍在遇到未預期的效能問題，請使用 Windows 意見反應中樞傳送意見反應給我們。 請務必遵循指示來 [納入 SteamVR 效能追蹤](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)。 

### <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR 顯示組合器錯誤 (例如「共用的 IPC 組合器連接失敗 (400) 」 ) 。

已知的問題是，如果您的耳機和主要監視器位在兩個不同的視訊卡上，就會發生這種情況。 將您的監視器附加至與耳機相同的介面卡，並將該監視設定為 [設定] 應用程式中的主要監視 **> 系統 > 顯示** 。

### <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>SteamVR 內容會顯示在錯誤的位置，例如在地面下方或上方。

重設您的位置： 
1. 按一下左邊控制器的操縱杆以顯示「SteamVR 儀表板」。
2. 選取 [設定] 按鈕。
3. 選取 [重設已安裝的位置]。

### <a name="my-steam-app-closed-unexpectedly"></a>我的流應用程式意外關閉。

如果您鎖定電腦畫面、移除耳機、切換使用者，或電腦進入睡眠狀態，則會關閉流應用程式。


## <a name="speech-and-audio-problems"></a>語音和音訊問題

### <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>我無法聽到耳機中的任何聲音，或是透過電腦而非耳機播放音效。

* 如果您的沉浸式耳機未包含內建耳機，您必須將耳機連接到耳機上的音訊插孔。 插座通常位於耳機面板或鏡頭的後方。 如果找不到，請洽詢您的耳機製造商。
* 有些音訊耳機具有可控制音量的實體按鈕。 如果音訊無法運作，請檢查磁片區是否已關閉或靜音。
* Windows Mixed Reality 是設計用來在執行混合實境入口時，透過沉浸式耳機播放音效，而您也有連接耳機。 當您將耳機移開或翻轉面板時，請關閉混合實境入口的應用程式，或當該應用程式未使用15分鐘時，音訊會切換至您的預設 Windows 播放裝置。 您可以在 [ **設定 > 混合現實 > 音訊和語音** ] 中變更此設定。
* 請確定您的音訊耳機已完全插入音訊插孔。 尤其是 Acer 耳機可能需要更多的護理，以確保音訊耳機都已插入。
* 檢查音訊耳機/麥克風是否已插入耳機，而不是電腦。
* Windows 音效主控台只會顯示已啟用的音訊端點，而不會顯示已停用的端點。 當您未戴耳機時，耳機音訊裝置將會停用，因此您必須以滑鼠右鍵按一下音效控制台，然後選擇 [顯示已停用的裝置] 以查看它;裝置名稱為「Realtek USB 2.0 音訊」。 這麼做之後，您可以將 [屬性] 頁面中的名稱變更為您可以更輕鬆辨識的內容。 您可以針對 [播放] 和 [錄製] 索引標籤進行這項作業。
* 如果您的音訊無法在混合現實應用程式中運作 (例如，Netflix) ，這可能是因為已知的問題，Windows Mixed Reality 不會自動更新以符合作業系統版本。 若要修正此問題並獲得最佳的混合現實體驗，請移至 [ **設定] > 更新 & 安全性 > Windows Update > 檢查更新** 。

**注意：** Windows Mixed Reality 空間音訊最適合搭配內建或直接連線到您的沉浸式耳機的耳機。 連接到電腦的電腦喇叭或耳機可能無法正常適用于空間音訊。

**注意：** Windows Mixed Reality 不支援藍牙音訊耳機。

### <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>我遇到突然的音量變更、音訊遺失或蜂鳴。

* 某些應用程式（包括透過 SteamVR 啟動的許多應用程式）可能會在音訊裝置隨您啟動或停止混合實境入口時，遺失音訊或停止回應。 開啟混合實境入口應用程式之後，請重新開機應用程式以修正此錯誤。
* 如果另一個多媒體 USB 裝置 (例如網路凸輪) 與 Windows Mixed Reality 耳機共用相同的內部或外部 USB 集線器，則耳機的音訊插孔/耳機可能偶爾會有噪音音效或音訊。 將您的耳機插入使用不同中樞或中斷連接/停用其他 USB 多媒體裝置的 USB 埠。
* 如果您注意到耳機有大量的雜訊，則電腦的 USB 集線器可能無法提供足夠的電源給 Windows Mixed Reality 耳機。 如果發生這種情況，請立即提出 [意見反應中樞](https://docs.microsoft.com/hololens/hololens-feedback) 錯誤。 因應措施包括不使用延伸模組纜線、使用專用的外部驅動 USB 3.0 中樞，或嘗試在電腦上使用不同的 USB 埠。

### <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>我的藍牙音訊耳機未如預期般運作。

Microsoft 不建議搭配 Windows Mixed Reality 使用藍牙音訊耳機。 藍牙音訊週邊設備無法正常搭配 Windows Mixed Reality 的語音和空間音效體驗，而且藍牙音訊耳機無法同時支援麥克風輸入和身歷聲輸出，因此當您將音訊或 hrtf 音效用於 gamechat 或其他語音輸入時，就不會聽到它們。 藍牙音訊耳機也會對您的移動控制器體驗產生負面影響。 

### <a name="sound-isnt-coming-from-expected-directions"></a>音效並非來自預期的方向。

Windows Mixed Reality home 包含空間音效 (音訊，就像是來自家用) 的應用程式。 當您在每個應用程式之間來回移動和移動時，音效方向和層級將會變得更進一步瞭解其真實性。 以下是非預期的音效方向的一些原因： 
* 當您從支援背景的音樂應用程式開啟並播放音樂時 (例如您家中的 Groove 音樂) ，然後開啟沉浸式的 VR 體驗 (例如遊戲) ，音樂應用程式的音效將 crossfade 從空間音效到身歷聲。 它可能會比之前更大，因為您與音效之間已沒有任何距離。
* 如果您在使用 Windows Mixed Reality 耳機之前，已在主機電腦上啟用 Cortana，您可能會遺失 Windows Mixed Reality 首頁中的應用程式所套用的空間音效。 若要修正此問題，請在啟動 Windows Mixed Reality 之前，關閉桌上型電腦應用程式視窗中的 [讓 Cortana 回應嗨 Cortana **>** ]，或從 Windows Mixed Reality home 中的桌面應用程式視窗中啟用 [耳機用 Windows Sonic]：
    1. 以滑鼠左鍵按一下桌面工作列上的喇叭圖示，然後從音訊裝置清單中選取它。
    2. 以滑鼠右鍵按一下桌面工作列上的喇叭圖示，然後在 [喇叭設定] 功能表中選取 [耳機用 Windows Sonic]。
    3. 針對 (端點) 的所有音訊裝置重複這些步驟。

### <a name="speech-commands-are-not-working-as-expected"></a>語音命令未如預期般運作。

* 若要使用語音命令，您電腦上的語音和語言設定必須設定為 [Windows Mixed Reality 中支援的語言](https://support.microsoft.com/en-us/help/4039262/windows-10-mixed-reality-setup-faq#Languages)。 若要檢查您的 Windows 語音和語言設定，請選取 [ **設定 > 時間] & 語言 > 區域 & 語言** 和 **設定 > & 語言 > 語音** 。
* 如果您的耳機沒有內建的麥克風，您將需要使用麥克風連接耳機或您的電腦。 當您磨損麥克風時，若要讓麥克風自動切換至您的耳機，請移至 [ **設定] > Mixed reality > 音訊和語音** ，然後開啟 [當我磨損耳機時，切換到耳機 mic]。
* 有些音訊耳機具有實體按鈕，可將麥克風靜音和取消靜音。 如果語音命令無法運作，請查看您的麥克風是否已靜音。
* 使用麥克風 dangles 自 earbud 纜線的音訊耳機，在環境雜訊的環境中無法正常執行語音命令。
* 當您第一次在混合實境入口會話中叫用 Cortana 時，Cortana 可能會變慢。 移至 **cortana 的 [設定] > cortana > 與 cortana** 通訊，並確定已啟用 [讓 Cortana 回應嗨 Cortana]。
* 在某些電腦上，您耳機連接的麥克風的預設語音捕捉增益可能設定過低。 如果您遇到不可靠的語音命令或聽寫，可以試著執行麥克風設定疑難排解員。 您可以透過 [ **設定 > 時間] & 語言 > 語音** ，然後選取 [麥克風] 區段中的 [開始]，以連線到此疑難排解員。 您可以透過 Windows Mixed Reality 首頁中的桌面應用程式來執行這項操作，同時戴耳機以影響您用於 Windows Mixed Reality 的麥克風。 在疑難排解員 wizard 中選取適當的端點。

### <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>我只有一個音訊耳機，我想要將它用於桌上型電腦和我的耳機。

如果您只有一個音訊耳機，而且沒有內建耳機的耳機，請將音訊耳機連接到主機電腦，而不是耳機。 然後，在 [MRP 設定] 中關閉 [切換到耳機音訊]。

### <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>我想切換至 Dolby Atmos for Headphones。

Windows Mixed Reality 環境和其應用程式使用耳機用 Windows Sonic 的空間音訊技術，其會針對混合現實體驗進行自訂。 其他的空間音訊技術（例如 Dolby Atmos for Headphones）可以套用至全螢幕應用程式（例如 SteamVR 遊戲），但不適用於 Windows Mixed Reality shell 環境和應用程式 (例如，將網頁瀏覽器放在懸崖之屋的牆上，或使用) 空間音效和聲場設計的天空 Loft 耳機用 Windows Sonic。


## <a name="questions-about-desktop-in-mixed-reality"></a>混合式桌上型電腦的相關問題

### <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>如何? 在混合的生活中存取我的電腦桌面？
您可以使用桌面應用程式，在混合現實中存取您的電腦桌面。 從 Windows 按鈕的耳機中啟動它 **> 所有應用程式 > 桌面** 。 

### <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>如何查看混合現實中的多個監視器？
根據預設，桌面應用程式會自動切換為顯示具有焦點的監視器。 如果您想要在混合現實中看到所有的監視器： 
* 按一下應用程式左上角的 [監視] 圖示
* 停用 [自動切換監視器]
* 挑選您想要查看的監視
* 啟動桌面應用程式的另一個實例
* 選擇您想要在該實例上看到的監視器 
* 針對所有的實體監視器重複一次，請注意，每次您重新開機 Mixed Reality 時，都必須重新選擇要在每一個傳統型應用程式上顯示的監視器。 

### <a name="my-desktop-app-only-shows-a-black-screen"></a>我的桌面應用程式只會顯示黑色畫面。
如果您的電腦有 Nvidia 混合式 GPU，問題可能是因為 Nvidia 裝置在離散 GPU （而非整合模式）上執行 runtimebroker.exe 所造成。 若要修正此問題，請遵循「[如何? 建立新程式的 Optimus 設定](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)」底下的指示。 新增 C:\windows\system32\runtimebroker.exe 並強制它在「整合式圖形」處理器上執行。 


## <a name="other-questions"></a>其他問題

### <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-getting-stuck"></a>我的 Samsung 電影對白或電影對白 + 耳機固件更新正在停滯中。

Samsung 擁有併發布透過其 "Samsung HMD 電影對白 Setup" 和 "Samsung HMD 電影對白 + Setup" 裝置附屬應用程式所提供的耳機固件更新。 如需有關 Samsung 固件更新問題的詳細資訊和協助，請與 Samsung 客戶服務聯繫。

如果固件更新程式停滯，而且沒有超過五分鐘的進度：
* 暫時拔掉所有其他 USB 裝置，然後重試一次固件更新。
* 將 Samsung 耳機連接到您電腦上的其他 USB 3.0 埠。
* 停用和/或卸載任何可能幹擾固件更新的軟體，例如 Gb 的 AORUS App Center。
* 使用不同的電腦來執行 Samsung 耳機固件更新。

### <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>當我使用 Windows Mixed Reality 時，我的 Wi-fi 會變慢。

如果您使用 2.4 GHz Wi-fi 連線，則您的移動控制器可能會減緩 Wi-fi。 請嘗試下列其中一項：
* 切換至5GHz 的 Wi-fi 連線（如果有的話）。 [深入了解](https://support.microsoft.com/en-us/help/4000461)。
* 使用個別的 Bluetooth 介面卡，將您的動作控制器連接到您的電腦。 請參閱 [建議的介面卡](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)。

### <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>我收到一則訊息，表示插入和收取電腦的費用。 為何會這樣？

如果您使用的是膝上型電腦，則在電腦同時完全收取和插入電源時，Windows Mixed Reality 的效果最佳。 

### <a name="what-is-the-experience-options-setting"></a>何謂體驗選項設定？

體驗選項設定 ( **設定 > 混合現實 > 耳機顯示 > 體驗選項** ) 可讓您變更 Windows Mixed Reality 效能設定。 這可讓您在各種內容中選擇硬體設定的最佳可能體驗。 所有系統都可使用90Hz 體驗，但您可能會想要嘗試自動查看您偏好的設定。 選項如下：
* 自動： Windows Mixed Reality 將決定硬體設定的最佳體驗。 對於大部分的人來說，這是開始使用的最佳選擇。
* 60Hz：將重新整理頻率設定為60Hz，並關閉特定功能，例如混合實境入口中的影片捕獲和預覽。
* 90Hz：將更新頻率設定為90Hz。

### <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality 支援哪些語言？

Windows Mixed Reality 提供下列語言版本。 如果您的電腦設定為不同的語言，您仍然可以使用 Windows Mixed Reality，但介面會以英文 (顯示) ，而且語音命令和聽寫將無法使用。

* 簡體中文 (中國)
* 英文 (澳大利亞)
* 英文 (加拿大)
* 英文 (英國)
* 英文 (美國)
* 法文 (加拿大)
* 法文 (法國)
* 德文 (德國)
* 義大利文 (義大利)
* 日文 (日本)
* 西班牙文 (墨西哥)
* 西班牙文 (西班牙)

Windows Mixed Reality 螢幕小鍵盤僅限英文 (美國) 。 若要以另一種語言輸入文字，請使用連接到您電腦的實體鍵盤。 您也可以使用上面所列的其中一種支援 Windows Mixed Reality 語言的聽寫，只要在螢幕小鍵盤上選取 [麥克風] 即可。

Windows Mixed Reality 也提供下列語言版本，不需要語音命令或聽寫功能：

* 繁體中文 (臺灣和香港特別行政區) 
* 荷蘭文 (荷蘭)
* 韓文 (韓國)
* 俄文 (俄羅斯)

### <a name="i-have-questions-about-my-headset-hardware"></a>我有關于耳機硬體的問題。

如需有關耳機的詳細資訊，請洽詢製造商。 Box 中可能會有產品指南，您也可以嘗試製造商的網站。


## <a name="how-to-uninstall-windows-mixed-reality"></a>如何卸載 Windows Mixed Reality

### <a name="how-do-i-uninstall-windows-mixed-reality"></a>如何? 卸載 Windows Mixed Reality？

1. 中斷耳機與電腦的連線。
2. 關閉混合實境入口。
2. 移至 [  **開始] > 設定 > 混合現實** ，然後選取 [卸載]。

當您準備好再次使用耳機時，請將其插入，混合實境入口將會帶您完成設定。

### <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>我收到「我們無法完成卸載 Windows Mixed Reality」訊息。

這表示某些檔案（包括您的環境相關資訊）仍可能在您的電腦上。 如果您決定稍後重新安裝 Windows Mixed Reality，這可能會造成問題。 您可以藉由修改登錄和使用 Windows PowerShell 來執行命令，以手動方式從電腦移除任何剩餘的 Windows Mixed Reality 資訊。 _如果您不正確地修改登錄，可能會發生嚴重的問題。請務必小心遵循這些步驟。若要新增保護，請先備份登錄再進行修改，以便在問題就會發生時進行還原。_ 如需詳細資訊，請參閱 [如何在 Windows 中備份和 restory 登錄](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)。 

若要使用下列命令卸載 Windows mixed reality：
1. 重新啟動電腦。
2. 在 **搜尋** 方塊中，輸入 "regedit"，然後選取 **[是]** 。
3. 移除下列登錄值：
   <ul>
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>，然後刪除 <b>FirstRunSucceeded</b>。</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic\speechandaudio</b>，然後刪除 <b>PreferDesktopSpeaker</b> 和 <b>PreferDesktopMic</b>。</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\Holographic</b>，然後刪除 <b>DisableSpeechInput</b>。 注意：您必須針對已使用 Windows Mixed Reality 之電腦上的每個使用者帳戶，刪除 HHKEY_CURRENT_USER 中的登錄專案。</li> 
    <li><b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\perceptionsimulationextensions</b>，然後刪除 <b>DeviceID</b> 和 <b>模式</b>。</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>，然後刪除 <b>OnDeviceLearningCompleted</b>。</li> 
   </ul>
4. 移除下列登錄機碼： <ul>
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\ Speech_OneCore \Settings\HolographicPreferences</b></li><br/></ul>
5. 關閉登錄編輯程式。
6. 流覽至 **C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** ，然後刪除 **RoomBounds.js** 。 針對已使用 Windows Mixed Reality 的每個使用者重複此步驟。
7. 開啟系統管理員命令提示字元並流覽至 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** 。 然後刪除 **HeadTracking data** 資料夾的內容 (但不) 資料夾本身。
8. 在 **搜尋** 方塊中輸入 "powershell"，以滑鼠右鍵按一下 [ **Windows PowerShell** ]，然後選取 [以 **系統管理員身分執行** ]。
9. 在 Windows PowerShell 中，執行下列動作： <ul>
   <li>在命令提示字元中複製並貼上下列命令，然後按 Enter： <b>Dism/Online/Get-Capabilities</b></li> 
   <li>複製以類比.. (開頭的功能身分識別，如果&#39;t，則表示此專案不&#39;安裝。 在此情況下，請跳至步驟 10 ) 。</li> 
   <li>複製並貼上下列命令提示字元，然後按 Enter： <b>Dism/Online/Remove-Capability/CapabilityName：在最後一個步驟中複製的功能身分識別</b></li>
   </ul>
10. 重新開機您的電腦。




