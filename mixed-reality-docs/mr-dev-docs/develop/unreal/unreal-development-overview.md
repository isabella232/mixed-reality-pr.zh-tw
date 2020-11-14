---
title: Unreal 開發概觀
description: 使用 Unreal Engine 4 的混合實境開發概觀
author: hferrone
ms.author: v-hferrone
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 串流, 遠端, 混合實境, 開發, 開始使用, 功能, 新專案, 模擬器, 文件, 指南, 功能, 全像投影, 遊戲開發
ms.openlocfilehash: a8e345831167362745a45a8fa81ddae858083ca7
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340686"
---
# <a name="unreal-development-overview"></a>Unreal 開發概觀

![Unreal 橫幅標誌](../images/unreal_logo_banner.png)

開始使用 <a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Mixed Reality Docs"> 混合實境應用程式</a>是一項大型工作。 新的概念、平台和尖端硬體看起來可能像是障礙。 不過，如果您是 Unreal 開發人員，很幸運。 在 Unreal Engine 的最新 <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 版本資訊">版本</a>中，現在引進了 <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality Docs">Windows Mixed Reality</a> (VR) 和 <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2 Docs">HoloLens 2</a> (AR) 的支援。 此更新包括：
* 混合實境 UX 工具外掛程式支援
* OpenXR 支援
* 從傳統型應用程式進行的應用程式遠端處理
* 更好的效能
* 混合實境擷取
* Azure Spatial Anchors 的初始支援

如果您不熟悉 Unreal 開發，請不要盲目跳入。 探索 Unreal <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">教學課程系列</a>，以快速了解並尋找 Unreal <a href="https://www.unrealengine.com/marketplace/store" target="_blank">市集</a>和混合實境<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">論壇</a>中的資產和支援。 這些資源可將您連結至今日混合實境市集中建置者和問題解決者的社群。

> [!IMPORTANT]
> 如果您有現有 Unreal 專案要帶到 HoloLens 2 或沉浸式頭戴式裝置 (例如 Reverb G2)，請參閱我們的 **[移植指南](../porting-apps/porting-overview.md)** 。

## <a name="development-checkpoints"></a>開發檢查點

使用下列檢查點，將您的 Unreal 遊戲和應用程式融入混合實境的世界中。 如果您尚未探索 [設計全像投影範例應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，建議您下載並使用，以熟悉混合實境 UX 的基本概念。

### <a name="1-getting-started"></a>1.開始使用

[適用於 Unreal 的混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unreal)是為了加速您在 Unreal 中進行開發而設計的一組元件。 每個元件都包含用於設定沉浸式體驗的外掛程式、範例和文件。

* [適用於 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)是第一個要發行的元件，目前僅在 HoloLens 2 上提供支援。 元件外掛程式中包含常用 UX 功能的程式碼、藍圖和範例資產，用於輸入模擬、手部互動動作項目、可點按的按鈕元件、操作工具元件，以及下列行為元件。

閱讀本節的內容後，您大致上就已了解混合實境工具組、針對混合實境應用程式正確設定的開發環境，以及可在 Unreal 中運作的 MRTK 專案。

|  Checkpoint  |  結果  |
| --- | --- |
| [安裝最新工具](../install-the-tools.md) | 下載並安裝最新版的 Unreal Engine，並設定您的混合實境專案 |
| [HoloLens 2 教學課程系列](tutorials/unreal-uxt-ch1.md) | 進入 HoloLens 2 硬體的入門級 MRTK 教學課程 |

### <a name="2-core-building-blocks"></a>2.核心基本要素

混合實境開發有幾個重要功能不在我們的教學課程系列討論範圍內。 這些建置組塊是透過混合實境工具組提供的獨立功能。 您目前可能不需用到所有功能，但建議您及早探索。 深入探討下列核心建置組塊後，您將了解如何將包含多樣化功能的工具箱整合到混合實境專案中。

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> 您可以深入探索 **[適用於 Unreal 的 UX 工具 GitHub](https://github.com/microsoft/MixedReality-UXTools-Unreal)** 存放庫，以取得更多詳細資料。

### <a name="3-platform-capabilities-and-apis"></a>3.平台功能和 API

在混合實境應用程式中各有作用的其他重要功能，不需要任何額外的封裝或設定即可使用。 這些功能可以新增至 Unreal 專案，且不一定需要先安裝 MRTK。 深入了解這些進階功能後，您將能夠建置更複雜的混合實境應用程式。

|  功能  |  功能  |
| --- | --- |
| [HoloLens 相機](unreal-hololens-camera.md) | 從您在 HoloLens 裝置上執行的應用程式，擷取混合實境和真實世界的視覺內容 |
| [QR 代碼](unreal-qr-codes.md) | 在每個代碼的實際位置上使用座標系統，將 QR 代碼轉譯為全像投影 |
| [WinRT](unreal-winrt.md) | 透過可供 Unreal 的建置系統使用的 WinRT 程式碼，建立個別的二進位檔 |

### <a name="4-deploying-to-a-device"></a>4.部署至裝置

如果這是您第一次建立或部署適用於 HoloLens 的 Unreal 應用程式，則需從 Epic Launcher [下載支援的檔案](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。 安裝這些檔案之後，您就可以從 [Unreal 編輯器](unreal-deploying.md)或[裝置入口網站](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)進行部署。

### <a name="5-adding-services"></a>5.新增服務

到了開發旅程的這個階段，您可能會想要新增服務，或是需要商業部署方面的協助。 將 [Azure 雲端服務](../mixed-reality-cloud-services.md)與 Dynamics 365 功能整合，可以有效提升您的專案等級。 我們編譯了一些方便您探索及擴充混合實境知識的起點。

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>接下來要做什麼？

開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。 完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。 請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！

### <a name="streaming--debugging"></a>串流和偵錯

如果您想要在開發階段以 HoloLens 裝置測試應用程式，您可以使用 Unreal 編輯器或已封裝的 Windows 可執行檔，[直接從電腦加以串流](unreal-streaming.md)。

如果您想要使用 Visual Studio 對應用程式進行偵錯，請依照這些[指示](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote)操作。

### <a name="performance"></a>效能

針對混合實境進行開發時，隨附依賴平台的效能檢查點。 HoloLens 2 應用程式必須以每秒 60 格執行，才能讓全像投影穩定顯示並且看起來有回應。 幸好，我們的[效能建議](performance-recommendations-for-unreal.md)可在您的 Unreal 應用程式中實現此目的。

## <a name="supported-features"></a>支援的功能

| HoloLens 2 功能 | 最早支援的 Unreal Engine 版本 |
| ----------- | ----------- |
| ARM64 支援 | 4.23 |
| 來自電腦的串流 | 4.23 |
| 空間對應 | 4.23 |
| 手部和關節追蹤 | 4.23 |
| 眼球追蹤 | 4.23 |
| 語音輸入 | 4.23 |
| 空間錨點 | 4.23 |
| 相機存取 | 4.23 |
| QR 代碼 | 4.23 |
| 空間音訊 | 4.23 |
| 串流的觀眾螢幕支援 | 4.24 |
| 透過串流的平面 LSR | 4.24 |
| 範例應用程式 ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 和 [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| 行動多重檢視：效能命中 60 fps | 4.25 |
| 第三相機轉譯 | 4.25 |
| 從已封裝的桌面應用程式串流 | 4.25.1 |
| 適用於 HoloLens 2 的 Azure Spatial Anchors 搶鮮版 (Beta) | 4.25 |
| OpenXR 支援搶鮮版 (Beta) | 4.25 |
| UX 工具支援 (0.8) | 4.25 |
| 開發人員文件和教學課程 | 4.25 |

> [!div class="nextstepaction"]
> [安裝工具](../install-the-tools.md)

## <a name="see-also"></a>另請參閱
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">適用於串流、部署至模擬器和裝置的 Unreal 文件</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">行動裝置的 Unreal 效能指導方針</a>
