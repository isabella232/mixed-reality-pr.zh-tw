---
title: Feature_Contribution_Process
description: 將功能新增至 MRTK 的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: afc20c9764fe7fa8d10b10bdc34d952e657a20a6
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693735"
---
# <a name="feature-contribution-process"></a>功能貢獻流程

> [!WARNING]
> 10/1/2019：此頁面已被取代，因為它提供在2.0 版之前讓大型系統 MRTK 的指導方針。 在2.0 版本之後，需要更仔細地執行大型變更，但尚未決定這項處理常式。 我們預期大部分的 MRTK 貢獻都有較小的變更，而不是此處所涵蓋的變更。

將功能加入至混合現實工具組 (MRTK) 會分割成幾個反復專案步驟，因此維護人員可以有時間進行審核，並確保程式能順利執行。 開始之前，請務必先檢查 [功能需求](#new-feature-requirements) 的清單。

## <a name="process"></a>處理序

下列程式已經過草擬，可確保所有新的工作符合針對 MRTK 所定義的更新標準和架構，這已定義為：

1. [開啟新的提案和相關工作](#new-proposal)
2. [提交架構草稿或大綱](#architecture-draft)
3. [複習並完成架構檔](#architecture-documentation)
4. [提交 PR，以執行核心功能介面和事件基準 (（如果適用）) ](#core-implementation)
5. [提交執行任何必要 SDK 元件的 PR](#sdk-implementation)
6. [提交 PR 實行功能示範或完整調整範例](#example-implementation)

### <a name="new-proposal"></a>新提案

首先，開啟新的提案或工作，以描述您想要解決的功能或問題。 描述方法，以及如何將它融入您所設為目標的混合現實工具組版本。 這可讓每個人都有關于提案的討論，並希望在任何工作開始之前識別一些潛在的陷阱。

新提案會在每週寄送會議室會議期間進行審核及討論，而如果接受提案，則會建立並指派補充工作。

### <a name="architecture-draft"></a>架構草稿

第一項工作是在第一次接受初始提案之後，將會針對要完成的功能或工作，草擬初始的架構檔。 這份檔通常應該是一或兩頁頁面，其中包含功能的高階總覽，以及與混合現實工具組其他部分的關聯性。

* 草稿必須很容易使用，並醒目提示重要區域。
* 草稿必須包含建議的核心介面、設定設定檔和事件基準的清單。
* 草稿必須包含建議架構的簡單圖形。

確定功能的架構符合核心 MRTK 架構所設定的 [新功能需求](#new-feature-requirements) 。

>TODO：新增架構草稿範本的連結

完成草稿之後，您可以將這項功能附加至 GitHub 上的提案/工作問題，以進行最終公開評論。

### <a name="architecture-documentation"></a>架構檔

一旦接受草稿架構，就可以提出額外的提取要求，將最終的完整架構檔提交到存放庫。

>TODO：新增完整架構範本的連結

架構檔一經核准，就可以進行第一次提交程式碼。

開發可以在您自己的私用分支中開始，並在正常的情況下完成，不過，提交回核心 MRTK 專案的 PR 應分階段提交，以確保審查和核准會像 (一樣順利進行，並確保核心變更不會影響其他功能) 

### <a name="core-implementation"></a>核心執行

應提交的初始工作是執行：

* 定義
* 介面
* 組態設定檔
* 事件資料

如有需要，可以更新架構檔，使其符合對執行的任何變更。

請確認所有現有的單元測試和任何新的測試都在提交之前都通過。

### <a name="sdk-implementation"></a>SDK 執行

將核心介面和事件彙總到開發之後，即可提交 SDK 元件的工作。  針對支援的平臺和單元測試，新增功能的具體執行和測試。

### <a name="example-implementation"></a>範例執行

合併 SDK 元件之後，就可以提交範例幕後的任何示範場景或更新。

* 示範適用于特定功能的醒目提示和示範
* 範例是完整的工作場景學習範例

## <a name="new-feature-requirements"></a>新功能需求

大部分的功能執行都可以分為三個主要部分：

1. [功能管理員](#manager-implementation-requirements)
2. [事件資料](#event-data-implementation-requirements) (選擇性) 
3. [功能處理常式](#handler-implementation-requirements) (選擇性) 

### <a name="manager-implementation-requirements"></a>管理員執行需求

* 資料夾外部程式碼的元件定義 `MRTK/Core` 。
  * 這可確保功能是獨立的，而且沒有其他功能的相依性。
* 使用中找到的介面來定義 `MRTK/Core/Definitions/<FeatureName>System` 。
* 如果功能的實體管理員實作為，則應該直接繼承， `BaseManager` 或者 `MixedRealityEventManager` 它們會引發事件。
* 功能的實體管理員執行應設定，並確認該場景已準備好供該系統在中使用 `Initialize` 。
* 功能的實體管理員也應該在其移除在的場景中建立的任何程式之後清除 `Destroy` 。
* 向混合現實管理員註冊。
  * 如果功能是核心功能，則應該將此功能硬式編碼到 `MixedRealityToolkit` 和， `CoreServices` 並新增至 `MixedRealityConfigurationProfile` 。
    * 這包括能夠透過使用下拉式清單來指定具體的實作為 `SystemType` 。
    * 功能應該具有衍生自可編寫腳本之物件的設定檔。
    * 預設設定設定檔位於 `MRTK/SDK/Profiles` 並指派給混合現實管理員的預設設定設定檔
  * 如果這項功能 **不** 是核心功能，則必須使用延伸模組服務設定檔進行註冊並執行 `IMixedRealityExtensionService` 。
* 具有位於中的預設實作為 `MRTK/Services/<FeatureName>`
* 可以使用系統引發的事件應該在介面中定義，並使用所有必要的參數來將事件資料初始化。

### <a name="event-data-implementation-requirements"></a>事件資料執行需求

事件資料會明確定義處理常式預期要從事件接收哪些資料。

* 此功能的所有事件基準都應該在中定義 `MixedRealityToolkit/EventDatum/<FeatureName>` 。
* 所有新的事件資料類別都應該繼承自 `GenericBaseEventData`

### <a name="handler-implementation-requirements"></a>處理常式的執行需求

處理常式介面會定義元件應該接聽的每個事件，以及傳遞的資料類型。 終端使用者將會根據收到的事件資料來執行介面，以執行邏輯。

* 處理常式介面應該在中定義 `MixedRealityToolkit/Interfaces/<FeatureName>System/Handlers` 。
* 處理常式介面應該繼承自 `UnityEngine.EventSystems.IEventSystemHandler`
* 預設為加入宣告。 若要接收系統的事件，處理常式必須向系統註冊，才能接收這些事件。
