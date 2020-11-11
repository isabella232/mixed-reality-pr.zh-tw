---
title: HP 回音
description: 有關使用 HP 回音（耳機）的常見問題
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援、效能
appliesto:
- Windows 10
ms.openlocfilehash: c24f6766cab242332e79a0c5cf5ed3cd92c4687d
ms.sourcegitcommit: f459c7deb254409fd5db3967bcc875bcbc367e77
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94482396"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>HP 的回音，常見問題

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>將耳機纜線連接到電腦時，應該遵循的特定順序

HP 建議：

- 先將6計量纜線連接到耳機，再連接到電腦或電源供應器。
- 初始安裝之後，請將6計量線連接到耳機。
- 當耳機未使用時，請將電源卡與6計量纜線中斷連線。

## <a name="what-should-i-do-to-get-a-crisper-image"></a>我該怎麼做才能獲得更銳利的影像

如果您覺得顯示器看起來有點模糊，有幾件事您可以試試看：

- 確定您的耳機正確地放在您的頭部，以便您的眼睛以鏡頭為中心。
- 請嘗試調整 IPD (interpupillary 距離) 。 請注意，「回音」 G2 使用硬體 IPD。 若要變更它，請在您的耳機上尋找 IPD 調整。
- 如果您需要眼鏡或連絡人，他們仍然是必要的。
- 如果您的鏡頭只需要進行 (清理，請檢查您的-沒有流體) 。
- 由於耳機的 advanced 設計，在啟動裝置時，前幾分鐘內可能會有一些輕微的影像重設，在 Lcd 有機會進行準備之前。

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>我在插入耳機時遇到7-14 「發生錯誤」的錯誤

如果您看到7-14 「發生錯誤」錯誤，請嘗試下列步驟：

- 請確定您已安裝最新的驅動程式。
- 請嘗試將纜線插入不同的 USB-3.0 埠。
- 請將 USB C 用於包含的介面卡，以嘗試不同的埠。

請嘗試將纜線插入不同的 USB 集線器。  

> [!NOTE]
> HP 建議僅使用內建于主機板的 USB 控制器，並搭配「裝置」 G2 裝置。
> 如果您無法連線到您的裝置，請聯絡 [HP 支援](https://support.hp.com/us-en)

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>我的電腦從休眠狀態 (S4 開始時，出現13-14 「發生錯誤」錯誤) 

有時，在繼續程式中，視訊卡無法建立連線，因此從您的電腦撥出 USB 類型 C 並將其重新插入，可能有助於建立連接。

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>混合實境入口指出「此耳機上無法執行混合的現實」，但這在先前的 WMR 耳機中運作正常

發生這種情況的原因可能是您的 HP 回箱 G2 需要更強大的電腦，以確保獲得最佳體驗。 如需詳細資訊，請參閱最小的 [電腦需求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>我的左顯示器似乎已伸展，右邊的顯示顯示在中央和半黑色

當您的耳機未以原生解析度執行時，就會發生這種情況。 由於「HP 回音」 G2 HMD 會顯示高解析度的本質，因此並非所有系統都能轉譯原生解析度。 未來的修正程式即將推出 Windows Update，當耳機不是原生解析度時，將會解決轉譯問題。

有幾個原因會導致您的系統無法以原生解析度轉譯：

- 系統上的 DisplayPort 可能不會與1.3 相容，或可能不支援全部4個通道。
- 如果您正在使用介面卡，它可能不支援 HBR3 相容，或可能不支援全部4個通道。
- 如果您的系統具有混合式 GPU，可能會限制 DisplayPort 可用的頻寬。

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>為什麼我的 HP 運動控制器模型未在遊戲中正確顯示

雖然許多遊戲都會立即與 HP 運動控制器搭配運作，但有些遊戲有現有控制器功能的相依性，因此可能會有一些問題：

- 顯示錯誤的模型：修正此問題需要遊戲更新。 這通常不會封鎖遊戲的任何功能，但可能會導致混淆或甚至是視覺效果的構件。
- 對觸控板的相依性，通常是在控制器的輸入版面配置上。 SteamVR 可讓您建立自訂系結，以協助規避這類問題：
    - SteamVR Windows Mixed Reality 包含一些遊戲的自訂系結。 當遊戲啟動時，不需要使用者動作，就會自動使用這些系結。

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>我的 SteamVR 遊戲似乎無法正常搭配我的 HP 運動控制器運作

雖然開發人員致力於更新其遊戲以進行 HP 運動控制器相容性，但我們為串流上許多最受歡迎的遊戲提供了自訂控制器系結。 使用 "Windows Mixed Reality for SteamVR" 完全更新至版本1.2.444 時，應會在遊戲執行時自動挑選這些系結。 但是，如果您的遊戲目前似乎沒有註冊您的動作，您可以使用 [SteamVR 設定] 功能表手動搜尋自訂系結設定檔。
若要執行此工作

- 按下右邊的動作控制器的功能表按鈕，開啟 [SteamVR] 功能表
- 選取 [SteamVR] 功能表右下角的 [設定] 圖示
- 選取 [控制器] 索引標籤
- 選取 [管理控制器系結] 選項

您可以從這裡將作用中控制器系結變更為「自訂」，這會開啟用來嘗試共用遊戲系結的選項。
如果 (尚未在此遊戲中共用任何自訂遊戲系結，或您未完全滿意所嘗試的) ，您也可以建立自己的自訂遊戲系結，甚至在幾個遊戲會話之後共用這些系結來協助其他人。