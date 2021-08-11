---
title: 版本資訊 - 2017 年 10 月
description: 在2017年10月) Windows 10 Fall Creators Update (的 Windows Mixed Reality 版本資訊。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 版本資訊、版本、windows 10、組建、rs3、os
ms.openlocfilehash: 09a33e1bc4a13c75e4c8a0ee250c7b67eb8e68e21220840037085e727acfb1f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190592"
---
# <a name="release-notes---october-2017"></a>版本資訊 - 2017 年 10 月

Windows 歡迎畫面 Mixed Reality！ **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** 版引進了新的 [Windows Mixed Reality 沉浸式耳機](/windows/mixed-reality/discover/immersive-headset-hardware-details)和 [移動控制器](/windows/mixed-reality/design/motion-controllers)的支援。 您現在可以在連接到[Windows Mixed Reality 的電腦](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)時，探索新的世界、玩 VR 遊戲，以及體驗沉浸式娛樂功能。

Windows Mixed Reality 耳機和移動控制器版本是大規模團隊工作的高潮，也是[Windows Mixed Reality 平臺](/windows/mixed-reality/discover/mixed-reality)（包括[Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details)）向前邁進的一大步。 雖然 HoloLens 未收到具有 Windows 10 Fall Creators Update 的更新，但仍未停止處理 HoloLens。 我們將會有很多學習和深入解析，可從最近的工作套用到整體 Windows Mixed Reality 上。 事實上，Windows Mixed Reality 沉浸式耳機和移動控制器都代表 HoloLens 開發的絕佳進入點，因為相同的 api、工具和概念都適用于兩者。

若要更新為每個裝置的最新版本，請開啟 **設定** 應用程式，移至 [**更新 & 安全性**]，然後選取 [**檢查更新**] 按鈕。 在 Windows 10 的電腦上，您也可以使用[Windows 媒體建立工具](https://www.microsoft.com/software-download/windows10)手動安裝 Windows 10 Fall Creators Update。

 **適用于桌面的最新版本：** 2017 年10月 Windows 10 desktop (**10.0.16299.15**，Windows 10 Fall Creators Update) <br>
 **適用于 HoloLens 的最新版本：** [Windows 10 全像攝影版2016年8月](release-notes-august-2016.md) (**10.0.14393.0**、Windows 10 周年更新) 

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Windows Mixed Reality 簡介

Windows 10 Fall Creators Update 正式推出 Windows Mixed Reality 耳機和移動控制器的支援，並 Windows 10 世界的第一個空間作業系統。 重點如下：
* **[各種耳機](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)**-Windows Mixed Reality 可讓合作夥伴提供不同的耳機類型，起價為 $399 美元，與運動控制器配套。
* **[移動控制器](/windows/mixed-reality/design/motion-controllers)**-透過藍牙以無線方式與您的電腦進行 Windows Mixed Reality 的動作控制器，並提供六種自由度追蹤、大量的輸入方法和 IMUs。
* **[簡易設定和可攜性](./recommended-adapters-for-windows-mixed-reality-capable-pcs.md)** -在10分鐘內開始設定並開始使用。 沉浸式耳機使用內部追蹤來追蹤您的移動和您的運動控制器，並有六自由的程度。 不需要任何外部攝影機或 lighthouse 標記！
* **[支援更廣泛的電腦](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)**-Windows Mixed Reality 將可讓更多人體驗 desktop VR，而不支援從 $499 美元開始的全選整合式圖形卡和電腦。
* **[Windows Mixed Reality home](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)** -世界的第一個空間作業系統提供熟悉的主要環境，可供使用2d 應用程式進行多工處理、啟動 VR 遊戲和應用程式，以及放置裝飾性的全像影像。
* Microsoft Store 的絕佳的 **[VR 遊戲和應用程式](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)**，從 Hulu 的 vr 和 360 video，到像是 SUPERHOT 的 vr 和亞利桑那州的精彩遊戲，Microsoft Store 都有一系列的內容可以在 Windows Mixed Reality 中體驗。
* **[SteamVR 早期存取](./using-steamvr-with-windows-mixed-reality.md)**-Windows 10 Fall Creators Update 可讓您使用 Windows Mixed Reality 耳機和控制器來播放 SteamVR 標題，使 VR 標題的最大目錄可供 Windows Mixed Reality 使用者使用。

## <a name="known-issues"></a>已知問題

我們努力提供絕佳的 Windows Mixed Reality 經驗，但仍在追蹤一些已知問題。 如果您發現其他人，請 [提供意見反應給我們](/windows/mixed-reality/give-us-feedback)。

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 首頁中的桌面應用程式
* 剪取工具不適用於桌面應用程式。
* 桌面應用程式在重新開機時不會保存設定。
* 如果您在桌上型電腦上使用混合實境入口預覽版，在 Windows Mixed Reality 首頁中開啟桌面應用程式時，您可能會注意到無限的鏡像效果。 
* 執行傳統型應用程式可能會導致非 Ultra Windows Mixed Reality 電腦上的效能問題;不建議您這樣做。  
* 傳統型應用程式可能會自動啟動，因為桌面上的隱藏視窗具有焦點。 
* 桌面使用者帳戶控制提示會使耳機顯示為黑色，直到提示完成為止。

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality 設定
* 設定連接耳機的 Windows 時，您的電腦監視器可能會空白。 拔掉耳機以啟用電腦監視器的輸出，以完成 Windows 設定。
* 建立界限時，追蹤可能會失敗。 如果是的話，請再試一次，因為系統會在一段時間內進一步瞭解您的空間。
* 如果您在 Windows Mixed Reality 安裝期間開啟或關閉 Cortana，此變更將會套用至您的桌面 Cortana 設定。
* 如果您沒有連接耳機，您可能會在第一次造訪 Windows Mixed Reality 首頁時錯過提示。
* 藍牙耳機可能會干擾運動控制器。 建議您在 Windows Mixed Reality 會話期間取消配對或關閉藍牙控制器。

### <a name="games-and-apps-from-windows-store"></a>Windows 存放區的遊戲和應用程式
* 有些以圖形化密集的遊戲（例如 Forza Motorsports 6）可能會在 Windows Mixed Reality 內播放時，導致功能較差的電腦發生效能問題。

### <a name="audio"></a>音訊
* 如上所述，藍牙音訊週邊設備無法與 Windows Mixed Reality 語音和空間音效體驗正常搭配運作。 它們也會對您的移動控制器體驗產生負面影響。 我們不建議搭配 Windows Mixed Reality 使用藍牙音訊耳機。
* 當裝置未在使用中時，您無法使用連接到 (或) 耳機播放音訊的音訊裝置。 如果您只有一個音訊耳機，您可能會想要將音訊耳機連接到主機電腦，而不是耳機。 若是如此，您就必須在 **設定**  >  **Mixed Reality**  >  **音訊和語音** 中關閉「切換到耳機音訊」。
* 某些應用程式（包括透過 SteamVR 啟動的許多應用程式）可能會在音訊裝置隨您啟動或停止混合實境入口時，遺失音訊或停止回應。 開啟混合實境入口應用程式之後，請重新開機應用程式以修正此錯誤。
* 如果您在使用 Windows Mixed Reality 耳機之前，在主機電腦上啟用 Cortana，您可能會遺失套用至您在 Windows Mixed Reality home 周圍所放置應用程式的空間音效模擬。 解決辦法是在所有連接到您電腦的音訊裝置上啟用「耳機用 Windows Sonic」，即使是連接耳機的音訊裝置也是一樣：
   1. 以滑鼠左鍵按一下桌面工作列上的喇叭圖示，然後從音訊裝置清單中選取。
   2. 以滑鼠右鍵按一下桌面工作列上的喇叭圖示，然後在 [喇叭設定] 功能表中選取 [耳機用 Windows Sonic]。
   3. 針對 (端點) 的所有音訊裝置重複這些步驟。
>[!NOTE]
> - 由於連接到您的耳機的耳機/喇叭不會出現，除非您有佩戴，否則您必須從 Windows Mixed Reality 首頁的桌面應用程式視窗中，將此設定套用到連線到耳機 (或整合到耳機) 的音訊裝置。
> - 另一個選項是在啟動 Windows Mixed Reality 之前，先關閉桌面 **設定** Cortana 中的「讓 Cortana 回應嗨 Cortana」  >   。

* 當另一個多媒體 usb 裝置 (（例如網路凸輪）) 與 Windows Mixed Reality 耳機共用相同的 usb 集線器)  (，在罕見的情況下，耳機的音訊插孔/耳機可能會有噪音音效或完全沒有音訊。 您可以將耳機修正為沒有與其他裝置共用相同中樞的 USB 埠，或中斷連接/停用其他 USB 多媒體裝置。
* 在罕見的情況下，主機電腦的 USB 集線器無法提供足夠的電源給 Windows Mixed Reality 耳機，您可能會注意到連接到耳機的耳機有突然的雜訊。

### <a name="speech"></a>語音
* Cortana 可能無法播放其音訊提示，以進行接聽/思考以及命令的音訊回應。
* 中國和日本市場 Cortana 在使用期間，不會正確地顯示 Cortana 圓圈下的文字。
* Cortana 在混合實境入口會話中第一次叫用時，可能會變慢。 若要解決此問題，請確定  >  已啟用 [**Cortana**  >  **與 Cortana 交談**] 設定下的 [讓 Cortana 回應嗨 Cortana]。
* Cortana 可能在不 Windows Mixed Reality Ultra 電腦的電腦上執行得較慢。
* 當您的系統鍵盤設定為與 Windows Mixed Reality 中的 UI 語言不同的語言時，在 Windows Mixed Reality 中使用鍵盤上的聽寫會導致因為沒有 Wi-Fi 連接而無法運作的聽寫錯誤對話方塊。 若要修正此問題，請確定系統鍵盤語言符合 Windows Mixed Reality UI 語言。
* 西班牙的語音已啟用 Windows Mixed Reality，所以未正確辨識為市場。

### <a name="holograms"></a>全像投影
* 如果您在 Windows Mixed Reality 首頁中放入大量的全像投影，有些可能會在您的情況下消失並重新顯示。 若要避免這種情況，請移除 Windows Mixed Reality home 的該區域中的一些全息。

### <a name="motion-controllers"></a>運動控制器
* 有時候，如果您在 Edge 中選取網頁，內容將會縮放，而不是按下。
* 有時候當您選取 Edge 中的連結時，選取專案將無法運作。

## <a name="prior-release-notes"></a>先前的版本資訊
* [版本資訊 - 2016 年 8 月](release-notes-august-2016.md)
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [ (外部連結的沉浸式耳機支援) ](./troubleshooting-windows-mixed-reality.md)
* [HoloLens 的已知問題](/windows/mixed-reality/hololens-known-issues)
* [安裝工具](/windows/mixed-reality/develop/install-the-tools)
* [提供意見反應](/windows/mixed-reality/give-us-feedback)