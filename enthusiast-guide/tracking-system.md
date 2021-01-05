---
title: 內外追蹤的運作方式
description: Windows Mixed Reality 耳機中所使用之以相機為基礎之內部追蹤系統的相關資訊。
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、內部、內部、追蹤、攝影機
ms.openlocfilehash: af7553b27bec63c2ae83bed390c17e1fcf006954
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725869"
---
# <a name="inside-out-tracking"></a>內外追蹤

## <a name="how-does-inside-out-tracking-work"></a>內部追蹤的運作方式為何？

**快速解答：** 追蹤系統使用兩個可見的低解析度攝影機來觀察您環境中的功能。 攝影機接著會使用 IMU 資料來保險絲資訊，以判斷裝置在您環境中的精確位置。

**更多詳細資料：** 追蹤系統使用兩個低解析度的黑色和白色攝影機，以可見的光線識別您環境中的功能。 系統會根據觀察到的功能分成三角形其位置，然後藉由融合高比率 IMU 資料來補充資訊，以針對您的環境中的 HMD 產生連續的估計。 這兩個應用程式會使用姿勢資訊來呈現場景和系統，以針對任何時間和位置的錯誤預測修正此轉譯。 您的電腦會儲存環境資訊，讓追蹤系統可以召回環境特定的資料，例如空間界限的實體位置。 如果您在多個房間內使用您的裝置，您可以在每個房間內設定不同的界限，而追蹤系統可以召回特定空間的特定界限。

由於追蹤 Windows Mixed Reality 沉浸式耳機的運作方式就像是在 [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens)上追蹤，您可能會發現這段影片很實用：

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>我需要什麼才能讓追蹤工作順利進行？

有兩個考慮要解決，以確保追蹤適用于您：
1. 確定您的電腦符合執行 Windows Mixed Reality 的需求。 如果您的電腦符合 Windows Mixed Reality 的最低需求，則追蹤將擁有足夠的資源，可在您的電腦上正常執行。
2. 確定您的環境適用于裝置所採用的視覺效果追蹤類型。 您應該在具有足夠光線的環境中使用裝置。 由於裝置的運作方式是在可見的光線中觀察您的環境，因此必須有足夠的燈光才能觀察到環境。 也必須有足夠的視覺效果功能 (換句話說、裝飾、對比等) ，追蹤系統才能運作。

## <a name="how-much-light-is-enough-light"></a>光線夠多了？

如果您可以輕鬆地在環境中四處移動，而不覺得太暗，而且如果您可以觀察另一位人的功能是否在房間內，則追蹤系統可能會有足夠的燈光。 別忘了，如果您想要在 sun 進行，相機可能會變得飽和而不會可靠地追蹤。 

## <a name="what-is-the-recommended-number-of-environmental-features"></a>建議的環境功能數目為何？

此產品已設計為可在一般環境中運作。 請考慮下列考慮實驗-如果您在空白的房間內，白色牆、白色上限和白色地板，則追蹤系統會找不到要追蹤的功能，並會失敗。 如果您所在的房間是在藝術作品和裝飾中所涵蓋的空間，則追蹤系統會找到許多要追蹤的功能，而且也能正常運作。 通常，裝飾的家庭和辦公室都已經過示範，讓您有足夠的功能詳細資料來追蹤。

## <a name="how-fast-can-i-move-with-the-device"></a>我可以將裝置移到多快嗎？

裝置的設計目的是要支援超過人類 head 運動通常會遇到的動作。 您可以隨意移動。 請記住，您在沉浸式耳機中已減少實體周圍的認知，因此請確保您在環境中安全地移動。

## <a name="where-will-tracking-not-work"></a>追蹤無法運作的位置為何？

追蹤無法在房間無法看到足夠功能的房間內運作，因為燈光很低。 追蹤不會 (或有時適用于移動車輛的所有) ，例如飛機、匯流排、訓練、汽車或電梯。 在太多光線或強式的情況下，追蹤也會失敗。 比方說，如果有直接的陽光串流進入房間，則攝影機可能會降低曝光，以降低飽和度，而且不會看到一般的自然功能。 建議您保持相對於燈光，如果您必須傾向或尋找 uncomfortably 亮的事物，則追蹤系統可能無法正常運作。 

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>3DOF 和6DOF 之間有何差異？

首先，DOF 是「自由度」的最短。 討論追蹤系統時，這表示可以偵測到的移動程度或類型。 這些移動分為兩大類：「旋轉」和「使用翻譯旋轉」。 3DOF 指的是3度的自由度，代表每個軸的旋轉。 單純地說，3DOF 追蹤可讓您向左/向右、向上/向下查看，並將您的 head (變換) 側邊。 您無法在3DOF 中轉譯或向前/向後流覽。 6DOF 是6度自由度的縮寫。 它是以3DOF 的旋轉為基礎，並新增至 it 翻譯。 這表示您可以向前/向後、向左/向下 strafe，以及 crouch 和上一步。 三個 DOF 追蹤是您通常會在手機或行動裝置的 VR 產品上發現的追蹤類型，而6DOF 則會在更強大的 VR 平臺上找到。 有些體驗是針對3DOF 量身訂做，只允許3DOF 移動 (旋轉) ，即使裝置支援6DOF 追蹤也一樣。 其中一個範例是觀看 Windows Mixed Reality 中的360影片。 影片可讓您查看，但不允許您在環境中進行逐步解說。

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>我的耳機中有 jittering 或間斷情形的東西。 我的追蹤無法運作嗎？

這類錯誤有幾個來源。 請務必將您觀察到的內容視為正確的原因，讓它可以解決。 請參閱 [疑難排解](tracking.md) 一節，協助您瞭解可能發生這種情況的原因。

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>我可以將自己的追蹤技術帶入 Windows Mixed Reality 嗎？

目前不支援此功能。

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>為什麼我會看到顯示「找不到您的界限？」的 UI。

因為安全界限是實體位置專屬的，所以如果您在不同的位置使用裝置，系統就會找不到界限。 此外，當您設定界限之後，系統一律會尋找它，即使您在不同的實體位置使用裝置也一樣。 當您在不同位置使用裝置，而且尚未在該位置設定界限時，您將會看到此 UI。 您可以在每個使用裝置的位置設定界限，而裝置將會重新叫用您的位置特定界限。

如果您在先前設定界限的位置中使用裝置，但裝置仍找不到，您可以設定新的界限，或清除所有環境資料，以移除裝置中的所有界限。 請參閱 [疑難排解](tracking.md) 一節，以瞭解為什麼系統找不到您的界限和修正步驟。

## <a name="how-do-i-set-up-tracking"></a>如何? 設定追蹤？

Windows Mixed Reality 中的追蹤很容易使用，因此不需要基礎結構或設定。 如果您選擇這樣做，您可以設定要使用的虛擬界限。 如需詳細資訊，請參閱 [設定界限](set-up-windows-mixed-reality.md#set-up-your-room-boundary) 的一節。

## <a name="how-do-i-clear-tracking-and-environment-data"></a>如何? 清除追蹤和環境資料嗎？

追蹤系統會儲存某些環境資料，讓它能夠重新叫用實際的實際位置，例如您的安全界限。 您可以隨時移除此資訊，包括您的安全界限。 如果移除此資訊，系統將無法再辨識您的空間或重新叫用您的安全界限。 如果您想要在清除環境資料之後使用安全性範圍，您必須再次設定它。 請參閱設定 [界限](set-up-windows-mixed-reality.md#set-up-your-room-boundary) 以設定新界限的一節。 若要移除所有資料，請開啟 [設定]，流覽至 [混合式事實]，然後選取左側功能表的 [環境] 區段。 選取標示為「清除環境資料」的按鈕，以移除所有環境和追蹤資料。

## <a name="see-also"></a>請參閱
* [追蹤系統疑難排解](tracking.md)
* [運動控制器](controllers-in-wmr.md)
* [您的 Windows Mixed Reality 首頁](your-mixed-reality-home.md)
* [在 Windows Mixed Reality 中使用遊戲和應用程式](using-games-and-apps-in-windows-mixed-reality.md)
