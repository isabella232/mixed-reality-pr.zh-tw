---
title: 語音和音訊常見問題
description: 語音和音訊 Windows Mixed Reality 不超過標準取用者支援檔的疑難排解。
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、疑難排解、錯誤、協助、支援、音訊問題、語音問題
ms.openlocfilehash: d1d30cebb40d54d579e978013b9abc60981fa943d43b95a96f358092631b4d27
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208978"
---
# <a name="speech-and-audio-faqs"></a>語音和音訊常見問題

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>我無法聽到耳機中的任何聲音，或是透過電腦播放音效，而不是我的耳機

* 如果您的沉浸式耳機未包含內建耳機，請將耳機連接到耳機上的音訊插孔。 插座通常位於耳機面板或鏡頭的後方。 如果找不到，請洽詢您的耳機製造商。
* 有些音訊耳機具有可控制音量的實體按鈕。 如果音訊無法運作，請檢查磁片區是否已關閉或靜音。
* 音訊將切換至預設的 Windows 播放裝置： 
    * 如果您走著耳機
    * 翻轉面板
    * 關閉混合實境入口應用程式
    * 當應用程式未使用15分鐘時。 
    * 您可以在 **設定 > 混合現實 > 音訊和語音**）中變更此設定。
* 請確定您的音訊耳機已插入音訊插孔。 Acer 耳機特別可能需要更小心，以確保音訊耳機已插入。
* 檢查音訊耳機/麥克風是否已插入耳機，而不是電腦。
* **設定 > 系統** 中的音效主控台 > 音效只會顯示已啟用的音訊端點，而不會顯示已停用的端點。 當您未戴耳機時，會停用耳機音訊裝置。 若要查看它，請以滑鼠右鍵按一下音效主控台然後選擇 [顯示已停用的裝置]。 裝置名稱是「Realtek USB 2.0 音訊」，可以在 [屬性] 頁面中重新命名。 您可以針對 [播放] 和 [錄製] 索引標籤進行這項作業。
* 如果您的音訊無法在混合現實應用程式中運作，例如，使用 Netflix 應用程式。 這可能是因為已知問題所造成，Windows Mixed Reality 不會自動更新以符合作業系統版本。 若要修正此問題，並獲得最佳的混合現實體驗，請移至 **設定 > 更新 & 安全性 > Windows Update > 檢查更新**。

> [!NOTE]
> * Windows Mixed Reality 空間音訊最適合搭配內建或直接連線到您的沉浸式耳機的耳機。 連接到電腦的電腦喇叭或耳機可能無法正常適用于空間音訊。
> * Windows Mixed Reality 不支援藍牙音訊耳機。

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>我遇到突然的音量變更、音訊遺失或蜂鳴

* 某些應用程式（例如透過 SteamVR 啟動的應用程式）可能會在音訊裝置隨您啟動或停止混合實境入口時，遺失音訊或停止回應。 若要更正此錯誤，請重新開啟混合實境入口，然後重新開機應用程式。
* 如果另一個多媒體 USB 裝置 (例如網路凸輪) 與 Windows Mixed Reality 耳機共用相同的內部或外部 USB 集線器，則耳機音訊插孔或耳機有時可能會有噪音音效或音訊。 將您的耳機插入使用不同中樞或中斷連接/停用其他 USB 多媒體裝置的 USB 埠。
* 如果您發現連接耳機有大量的雜訊，電腦的 USB 集線器可能無法提供足夠的電源給 Windows Mixed Reality 耳機。 如果發生這種情況，請提出 [意見反應中樞](/hololens/hololens-feedback) 錯誤的錯誤，並嘗試：
    * 移除擴充功能纜線
    * 使用專用的外部驅動 USB 3.0 中樞
    * 電腦上的其他 USB 埠

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>我的藍牙音訊耳機未如預期般運作

Microsoft 不建議搭配 Windows Mixed Reality 使用藍牙音訊耳機。 藍牙音訊週邊設備無法正常運作 Windows Mixed Reality 的語音和空間音效體驗。 藍牙音訊耳機無法同時支援麥克風輸入和身歷聲輸出，因此您在使用 gamechat 或其他語音輸入時，不會聽到身歷聲或 hrtf 音效。 藍牙音訊耳機也會對您的移動控制器體驗產生負面影響。

## <a name="sound-isnt-coming-from-expected-directions"></a>音效並非來自預期的方向

Windows Mixed Reality home 包含空間音效 (音訊，聽起來像是來自家用) 的應用程式。 當您在每個應用程式之間來回移動和移動時，音效方向和層級將會改變，以提升其真實性的意義。 以下是未預期的音效方向的一些可能原因：

* 如果您從具有背景功能的音樂應用程式開啟並播放音樂 (例如您家中的 Groove 音樂) ，然後開啟類似遊戲的沉浸式 VR 體驗，則音樂應用程式的音效 crossfades 從空間音效到身歷聲。 它可能會變得更大，因為您與音效之間沒有任何距離。
* 如果您在使用 Windows Mixed Reality 耳機之前已在電腦上啟用 Cortana，您可能會遺失 Windows Mixed Reality 首頁中的應用程式所適用的空間音效。 若要修正此問題，請在啟動 Cortana 之前，關閉 **設定 > Windows Mixed Reality** 中的 [讓 Cortana 回應嗨 Cortana]，或啟用 [耳機用 Windows Sonic]：
    1. 移至 Windows Mixed Reality 首頁中的桌面應用程式視窗。
    2. 以滑鼠左鍵按一下桌面工作列上的喇叭圖示，然後從音訊裝置清單中選取它。
    3. 以滑鼠右鍵按一下桌面工作列上的喇叭圖示，然後在 [喇叭設定] 功能表中選取 [耳機用 Windows Sonic]。
    4. 針對 (端點) 的所有音訊裝置重複這些步驟。

## <a name="speech-commands-are-not-working-as-expected"></a>語音命令未如預期般運作

* 若要使用語音命令，您電腦上的語音和語言設定必須設定為[Windows Mixed Reality 中支援的語言](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages)。 若要檢查您的 Windows 語音和語言設定，請選取 **設定 > time & language** > language & language 和 **設定 > language & language > language**。
* 如果您的耳機沒有內建的麥克風，您將需要使用麥克風連接耳機或您的電腦。 當您磨損麥克風時，若要讓麥克風自動切換至您的耳機，請移至 **設定 > 混合現實 > 音訊和語音**，然後開啟「當我磨損耳機時，切換到耳機 mic」。
* 有些音訊耳機具有實體按鈕，可將麥克風靜音和取消靜音。 如果語音命令無法運作，請查看您的麥克風是否已靜音。
* 使用麥克風 dangles 自 earbud 纜線的音訊耳機，在環境雜訊的環境中並不適合語音命令。
* Cortana 在混合實境入口會話中第一次叫用時，可能會變慢。 移至 **設定 > Cortana > 與 Cortana 交談**，並確定已啟用 [讓 Cortana 回應嗨 Cortana]。
* 在某些電腦上，您耳機連接的麥克風的預設語音捕捉增益可能設定過低。 如果您遇到不可靠的語音命令或聽寫，請執行麥克風設定疑難排解員：
    1. 移至 Windows Mixed Reality 首頁中的桌面應用程式，同時戴耳機 (，以影響 Windows Mixed Reality) 所使用的麥克風。
    2. 移至 **設定 > Time & Language > 語音**。
    3. 在 [麥克風] 區段中選取 [入門]。
    4. 在疑難排解員 wizard 中選取適當的端點。

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>我只有一個音訊耳機，我想要將它用於桌上型電腦和我的耳機

如果您只有一個音訊耳機，而且沒有內建耳機的耳機，請將音訊耳機連接到電腦，而不是耳機。 然後，在混合實境入口設定中關閉 [切換到耳機音訊]。

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>我想切換到 Dolby Atmos for Headphones

Windows Mixed Reality 環境和其應用程式使用耳機用 Windows Sonic 空間音訊技術，其會針對混合的現實體驗進行自訂。 其他空間音訊技術（例如 Dolby Atmos for Headphones）可以套用至全螢幕應用程式（例如 SteamVR 遊戲），但不適用於 Windows Mixed Reality shell 環境和應用程式 (例如，將網頁瀏覽器放在懸崖之屋的牆上，或使用) 空間音效和聲場設計的天空 Loft 耳機用 Windows Sonic。