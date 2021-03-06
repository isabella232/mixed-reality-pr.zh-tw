---
title: 以位置為基礎的娛樂和 Windows Mixed Reality
description: 瞭解以位置為基礎的娛樂的 Windows Mixed Reality —硬體、背包」的電腦、追蹤、設定和支援。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: 混合的現實、vr、lbe、位置、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、硬體、HoloLens、多玩家、雲端服務、azure
ms.openlocfilehash: 49e96b99d3f74bd24a4a0e71f212018108148ad2
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236909"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>以位置為基礎的娛樂和 Windows Mixed Reality

在過去幾年來，我們在以位置為基礎的娛樂類別中看到大量的成長和創新。 傳統的場地（例如主題公園和劇院）已開始提供沉浸式、多玩家體驗，作為現有乘車點和安裝的免費體驗。 新的操作員和場地為 masses 帶來了獨特的多 sensorial、多玩家體驗。 所有這些經驗都會將信封推播到混合現實的可能原因。

本檔是在以位置為基礎的娛樂類別中開始使用 Windows Mixed Reality 的指南。 下列指導方針可能還適用于除了訓練、產品設計和其他使用案例以外的位置型體驗。

## <a name="engineering-faq"></a>工程常見問題

### <a name="hardware"></a>硬體

**問： Microsoft 及其合作夥伴可在我的設定中使用的硬體有哪些？**

答： Microsoft 及其 OEM 合作夥伴提供了一套具吸引力的裝置組合，可根據您的需求進行選擇。  

如果您為客戶提供的體驗需要虛擬實境耳機，HP、Samsung 和 Acer 的市場耳機很適合。 每個耳機都有自己的差異化屬性。 下列各項的詳細資料。

HP 回音： [詳細資料](https://hp.com/go/Reverbpro)

Samsung 電影對白 +： [詳細資料](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer： [詳細資料](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

如果您的地點是以混合或增強的現實體驗來學習，請查看 Microsoft HoloLens 2。  

HoloLens 2： [預先訂購的興趣](https://www.microsoft.com//hololens/buy)

如果您想要試驗使用先進的電腦視覺、語音和內文追蹤的體驗，Azure Kinect 深色適合。  

Azure Kinect： [詳細資料](https://azure.microsoft.com//services/kinect-dk/)

**問：我可以使用哪些背包」電腦的組合來執行電腦行動網卡的 VR 體驗？**

針對電腦行動網卡的 VR 體驗，我們 Oem 提供了一系列完全為該需求打造的背包」電腦。

HP 剛剛推出了其 HP VR 背包」 G2，這是世界上最強大的穿戴式 PC –針對自由漫遊體驗進行優化，現在提供了30% 以上的 RTX 2080 GPU 功能。 [詳細資料](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>安裝程式

**問：如何可以更輕鬆地設定和自訂 LBE 的混合現實入口網站？**

>[!NOTE]
>這項功能需要版本2000.19061.1011.0 或更高版本。  

您可能會發現您需要更多的混合現實入口網站自訂，而不是透過應用程式，將應用程式部署到 kiosk 或自訂體驗。 混合現實入口網站的最新七月更新支援數個 advanced 設定，您可以透過設定檔來設定這些設定：  

允許失敗的系統檢查-在完成安裝之前，安裝程式通常會檢查電腦是否與 Windows Mixed Reality 相容。 如果發生相容性問題，略過相容性檢查可能會在嘗試執行 Windows Mixed Reality 時發生問題。  

略過裝置附屬應用程式– DCA 提供製造商提供的耳機專屬設定步驟，並允許更新耳機的固件。  

略過房間設定–而不是收到建立空間界限的提示，您可以直接進入站上/固定模式的耳機。  

略過從存放區安裝應用程式-一般安裝程式會安裝數個存放區應用程式，包括3D 檢視器和 Edge 360 檢視器附加元件。 這會略過這些應用程式的安裝，但您可能遺失裝置功能。  

以全螢幕顯示預覽：混合現實入口網站會預設為在使用耳機時，于桌上型電腦的全螢幕中顯示耳機預覽。  

隱藏您的 [新增] 側邊面板-防止在啟動混合現實入口網站時，擴充您的新面板。  

#### <a name="how-to-configure"></a>如何設定：  

若要設定這些設定中的任何一項，您必須在此目錄下建立名為 _UserConfig.js_ 的檔案： _$env \\ ： localappdata\packages\ Microsoft.MixedReality.Portal_8wekyb3d8bbwe \localstate_

對大部分的使用者而言，這看起來會像這樣： _C:\Users \<username> \Appdata\local\packages\ microsoft.mixedreality.portal_8wekyb3d8bbwe \localstate \\_

針對您想要啟用的任何上述設定，JSON 檔案的下列內容應設定為 "true"：  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**問：是否有設定 playspace 的任何指引？**

答：設定 playspace 的方式應該與取用者設定體驗一樣。 房間設定程式也可讓您定義您的房間界線。 您可以在 [這裡](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)閱讀更多有關設定空間界限的詳細資料。

如同上述檔中所述，最大合理的單一座標 playspace 大約是5mx5m。 如果您想要有更大的區域，您可以在 Windows 全像 API 堆疊中使用空間錨點功能。 使用此 API 時，您將需要在所產生的體驗中進行自訂工程。  

您可以在 [這裡](/windows/mixed-reality/coordinate-systems)閱讀更多有關如何將內容優化以取得不同空間大小的詳細資料。
 

**問：我的空間太大，當我嘗試設定具有界限的長期體驗時遇到錯誤。我該怎麼做才能設定我的大型自由漫遊體驗？**

答：若要設定比 ~ 18x18ft 更大的空間，您無法使用系統提供的界限體驗。  界限系統依賴單一固定座標「錨點」，當使用者距離中央階段錨點太遠時，這可能會變得不穩定。 

您可以設定「固定」模式，而不會顯示界限或設定階段界限或 playspace。  您必須在應用程式內設定多個空間錨點，以參考實體界限區域。 

應用程式開發人員負責顯示必要的保護措施，讓使用者不會與實體周圍發生衝突。  這些可能是在體驗或自訂遊戲界限視覺效果中的數位牆。 

您可以在 [這裡](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)找到使用 WMR 設定房間界限的指引。

**問： playspace 的原點在哪裡？**

答： playspace 的來源取決於房間設定體驗，更明確地說，在安裝期間按下中間按鈕的 HMD 位置。 

### <a name="multi-player-setup"></a>多玩家設定

**問：我在的地點部署了多玩家體驗。Windows Mixed Reality 是否支援？**

答：如果您透過我們的測試人員計畫加入宣告 Windows 20H1 或更新版本的組建，您可以存取地圖共用的新介面。 這項新功能可透過 Windows 裝置入口網站的 [ [對應管理員](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) ] 介面使用。 若要使用此工具，請依照下列步驟執行：
* 請確定您加入宣告20H1 或更新版本-2019 年9月之後，這表示使用我們的測試人員計畫
* 使用這些[指示](/windows/uwp/debug-test-perf/device-portal-desktop)啟用 Windows 裝置入口網站 (WDP) 
* 插入您想要從下載現有對應或匯入新對應的 Windows Mixed Reality HMD
* 使用 [設定] 畫面中提供的 URL，在您選擇的瀏覽器中流覽至 WDP。
    * 流覽至 [混合式事實] 區段，然後選取 [對應管理員]。
    * 您現在可以使用 [下載] 按鈕，從電腦匯出現有的對應。
    * 您可以使用 [上傳對應檔] 按鈕，從先前的匯出匯入對應 (可能在不同的電腦上) 。
    * 您可以使用 [匯入]，讓系統在這部電腦上針對此 HMD 使用該對應。

> [!NOTE] 
> 先前，您可以使用空間資料封裝工具，不過，該工具最初是以不受支援的形式發行，而且現在已正式淘汰，且不再于20H1 運作。 相反地，請使用如上所述的收件匣 [對應管理員](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) 工具。 

### <a name="tracking"></a>跟蹤

問： Windows Mixed Reality 耳機中的追蹤技術如何運作？  

混合現實與 HoloLens 共用相同的追蹤技術。 若要深入瞭解內部追蹤系統，請參閱 [此處](/windows/mixed-reality/enthusiast-guide/tracking-system)的檔。

如需更高層級空間對應系統運作方式的說明，請參閱 [這裡](../design/spatial-mapping.md)的說明。

**問：是否有任何取得可靠追蹤磁片區的最佳作法？**

若要以最佳方式設定追蹤成功的環境，您可以閱讀這 [篇文章](/hololens/hololens-environment-considerations)中的最佳做法。

**問：是否有任何特定的細微差異，可考慮在倉儲規模空間或優化中進行追蹤？**

答：下列做法有助於取得更可靠的追蹤磁片區：  

在多個位置重迭的房間內提供不同的功能，可協助追蹤系統取得穩固的鎖定。 請考慮隨機油漆 splatters 和影線，而不是使用實線輪廓樣式線條。 

盡可能將您區域中的燈光動態範圍降至最低。 混合現實 Hmd 上的追蹤攝影機不是 HDR，而且 AGC (自動取得) 和 AEC (自動曝光，) 處理不同的光源。 視 surface light、模式和對比的分佈而定，AGC 或 AEC 可能會讓您成為最大的白色或黑色房間，這可能會讓您的功能更有可能與「色彩」相反。 如果您想要將內部圖片放在具有亮日光背後的外部視窗前方，然後調整曝光，讓您可以在外部看到詳細資料，則內部的所有專案都是 underexposed 和黑色。 或者，如果是在內部進行設定，則外部的所有專案現在都是 overexposed，而且全部都是白色。  

在房間內的聚光燈 (甚至是) 的額外負荷，如果追蹤攝影機有時可能會原因，這會使追蹤攝影機的 AEC/AGC 混淆。 平面/漫射光源有助於。  

### <a name="mixed-reality-cloud-services-and-azure"></a>混合現實雲端服務與 AZURE 

**問： Microsoft Azure 如何協助我的企業規模？**

答：以 Azure 為基礎的現場和遠端系統管理，可協助您的業務成為資料驅動、降低營運成本，並在現有和新的地點調整部署規模。 Azure 雲端服務（例如 Azure 儲存體、Azure 函式、App Service、Azure 網路和 IOT 中樞）有助於下列使用案例：  

遠端裝置部署 & 管理 

Real-Time 現場分析 

智慧型適應性的 LBE 遊戲 

LBE 內容串流和部署 

LBE Player 喜好設定熱度圖 

LBE 保留與預約系統 

**問：我正在開發空間 MMOG，以部署大量的使用量。任何有助於管理內容和物件持續性的服務？**

答： Azure 空間錨點是全新的混合現實服務，可在 HoloLens、iOS 和 Android 裝置上啟用多使用者、空間感知的混合現實體驗。 您可以在 [這裡](https://azure.microsoft.com//services/spatial-anchors/)深入瞭解 Azure 空間錨點。

**問。我們的場地專門採用多玩家體驗，而我想要將開發時間專注于內容和前端開發。是否有可協助我啟動或卸載後端開發的供應專案？**

答： Azure PlayFab 是適用于即時遊戲的完整後端平臺。 您可以在 [這裡](https://playfab.com/)深入瞭解。

### <a name="misc"></a>其他

**問：我使用 SteamVR 來部署我的體驗。Windows Mixed Reality 是否與 SteamVR 搭配運作？**

答：適用于 SteamVR 的 Windows Mixed Reality 可讓使用者在 Windows Mixed Reality 沉浸式耳機上執行 SteamVR 體驗。 [在這裡](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)深入瞭解使用 WMR SteamVR。

### <a name="support-and-community"></a>支援和團體  

我們有幾個實用的資源，可協助您與小組的主題專家交流、取得疑難排解支援，以及對更廣大的混合現實開發人員群體貢獻。  

如果您遇到任何公開發行功能的問題，請使用意見反應中樞提出錯誤。如需指引，請參閱此 [頁面](/windows/mixed-reality/enthusiast-guide/filing-feedback)。

如需 WMR 的其他疑難排解協助，請向我們的客戶支援小組 [提出支援要求](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) 。

加入我們的 HoloDevelopers 時差頻道，與混合現實開發人員和主題專家互動： [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter：遵循我們的混合現實開發人員關係小組來取得新聞、活動和更新 @MxdRealityDev 

如果您一直在三藩市或周圍，在 Microsoft Reactor 一律會發生什麼事。 您可以在 [這裡](https://developer.microsoft.com//reactor/Location/San%20Francisco)看到我們的活動行事曆。
