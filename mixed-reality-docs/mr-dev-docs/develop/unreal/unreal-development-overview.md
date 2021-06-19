---
title: Unreal 開發概觀
description: 使用 Unreal Engine 4 搭配我們策劃的檢查點旅程，開始進行 HoloLens 和 VR 的 wit 混合實境開發。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 串流, 遠端, 混合實境, 開發, 開始使用, 功能, 新專案, 模擬器, 文件, 指南, 功能, 全像投影, 遊戲開發, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, OpenXR
ms.openlocfilehash: 1225c507ec46c6f42c2fc10582a7920802860ad0
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394312"
---
# <a name="unreal-development-overview"></a>Unreal 開發概觀

![Unreal 橫幅標誌](../images/unreal_logo_banner.png)

開始使用 <a href="/windows/mixed-reality" target="_blank" title="Mixed Reality Docs"> 混合實境應用程式</a>是一項大型工作。 新的概念、平台和尖端硬體看起來可能像是障礙。 不過，如果您是 Unreal 開發人員，很幸運。 Unreal Engine 4 具有 <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality Docs">Windows Mixed Reality</a> (VR) 和 <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2 Docs">HoloLens 2</a> (AR) 裝置的完整支援。

[!INCLUDE[](includes/tabs-unreal-features.md)]

如果您不熟悉 Unreal 開發，請不要盲目跳入。 探索 Unreal <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">教學課程系列</a>，並尋找 Unreal <a href="https://www.unrealengine.com/marketplace/store" target="_blank">市集</a>中的資產。 您也可以在混合實境<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">論壇</a>中找到支援。 這些資源可將您連結至今日混合實境市集中建置者和問題解決者的社群。

> [!IMPORTANT]
> 如果您有現有 Unreal 專案要帶到沉浸式頭戴式裝置 (例如 Reverb G2)，請參閱我們的 **[移植指南](unreal-reverb-g2-controllers.md)** 。

## <a name="development-checkpoints"></a>開發檢查點

使用下列檢查點，將您的 Unreal 遊戲和應用程式融入混合實境的世界中。 如果您尚未探索 [設計全像投影範例應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，建議您下載以熟悉混合實境 UX 的基本概念。

### <a name="1-getting-started"></a>1.開始使用

首先，您必須安裝適用於 HoloLens 2 開發的工具。 接下來，完成我們的教學課程系列，以大致了解混合實境工具組、針對混合實境應用程式正確設定的開發環境，以及可在 Unreal 中運作的 MRTK 專案。 從 Unreal 4.26 開始，您也可以選擇開發適用於 HoloLens 2 的 OpenXR 應用程式。

|  Checkpoint  |  結果  |
| --- | --- |
| [安裝最新工具](../install-the-tools.md) | 下載並安裝最新版的 Unreal Engine，並設定您的混合實境專案 |
| [設定專案](unreal-project-setup.md) | 取得最新版本的 Unreal Engine 和 MRTK |
| [建立您的第一個 HoloLens Unreal 應用程式](unreal-quickstart.md) | 藉由建立基本的混合現實應用程式，開始您的 Unreal 和 HoloLens 開發旅程 |
| [HoloLens 2 教學課程系列](tutorials/unreal-uxt-ch1.md) | 在 Unreal 中設定混合實境開發、使用 MRTK 建置您的第一個應用程式，並將您的應用程式部署至 HoloLens 2 |
| 開始在 Unreal 中使用[OpenXR](../native/openxr.md) | 從 Unreal 引擎 Marketplace 安裝和啟用下列外掛程式：<ul><li> [Microsoft OpenXR](https://www.unrealengine.com/marketplace/en-US/product/ef8930ca860148c498b46887da196239)</li></ul>確定已停用 Microsoft Windows Mixed Reality 外掛程式。<br><br>[以下](#supported-features)完整列出 OpenXR 中目前支援的功能。|

### <a name="2-core-building-blocks"></a>2.核心基本要素

有幾項重要的混合實境功能並不在我們的教學課程系列討論範圍內。 這些建置組塊是透過混合實境工具組提供的獨立功能。 您目前可能不需用到所有功能，但建議您及早探索。 深入探討下列核心建置組塊後，您將了解如何將包含多樣化功能的工具箱整合到混合實境專案中。

[適用於 Unreal 的混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unreal)是為了加速您在 Unreal 中進行開發而設計的一組外掛程式。 每個外掛程式都包含用於設定沉浸式體驗的元件、範例和文件。

* [適用於 Unreal 的 UX 工具](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)是第一個要發行的外掛程式，目前僅在 HoloLens 2 上提供支援。 外掛程式包含 C++ 程式碼、藍圖，以及用於輸入模擬、手部互動、表面磁性的常見 UX 功能的範例資產。

* [適用于 Unreal 的圖形工具](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/) 是一種 UE 遊戲外掛程式，其中包含程式碼、藍圖和範例資產，可協助改善混合現實應用程式的視覺精確度，同時維持在效能預算內。

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> 您可以深入探索 **[適用於 Unreal 的 UX 工具 GitHub](https://github.com/microsoft/MixedReality-UXTools-Unreal)** 存放庫，以取得更多詳細資料。

### <a name="3-advanced-features"></a>3.進階功能

在混合實境應用程式中各有作用的其他重要功能，不需要任何額外的封裝或設定即可使用。 這些功能可以新增至 Unreal 專案，且不一定需要先安裝 MRTK。 深入了解這些進階功能後，您將能夠建置更複雜的混合實境應用程式。

|  功能  |  功能  |
| --- | --- |
| [HoloLens 相機](unreal-hololens-camera.md) | 從您在 HoloLens 裝置上執行的應用程式，擷取混合實境和真實世界的視覺內容 |
| [QR 代碼](unreal-qr-codes.md) | 在每個代碼的實際位置上使用座標系統，將 QR 代碼轉譯為全像投影 |
| [WinRT](unreal-winrt.md) | 透過可供 Unreal 的建置系統使用的 WinRT 程式碼，建立個別的二進位檔 |

### <a name="4-streaming-and-deploying-to-a-device"></a>4.串流並部署至裝置

如果您想要在開發階段以 HoloLens 裝置測試應用程式，您可以使用 Unreal 編輯器或已封裝的 Windows 可執行檔，[直接從電腦加以串流](unreal-streaming.md)。

如果這是您第一次將 Unreal 應用程式部署至 HoloLens 2，則需從 Epic Launcher [下載支援的檔案](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。 安裝這些檔案之後，您就可以從 [Unreal 編輯器](unreal-deploying.md)或[裝置入口網站](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)進行部署。

### <a name="5-adding-services"></a>5.新增服務

到了開發旅程的這個階段，您可能會想要新增服務，或是需要商業部署方面的協助。 整合 [Azure 雲端服務](../mixed-reality-cloud-services.md) 可讓您以主要方式來設定專案的等級。 我們編譯了一些方便您探索及擴充混合實境知識的起點。

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

### <a name="6-low-code-alternatives"></a>6. 低程式碼替代方案

[!INCLUDE[](../includes/unreal-low-code.md)]

## <a name="whats-next"></a>接下來要做什麼？

開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。 完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。 請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！

### <a name="debugging"></a>偵錯

如果您想要使用 Visual Studio 對正在裝置上執行的應用程式進行偵錯，請依照這些[指示](/visualstudio/debugger/debug-installed-app-package#remote)操作。

### <a name="performance"></a>效能

針對混合實境進行開發時，隨附依賴平台的效能檢查點。 HoloLens 2 應用程式必須以每秒 60 格執行，才能讓全像投影穩定顯示並且看起來有回應。 幸好，我們的[效能建議](performance-recommendations-for-unreal.md)可讓您在 Unreal 應用程式中升級效能。

## <a name="supported-features"></a>支援的功能

| HoloLens 2 功能 | 最早支援的 Unreal Engine 版本 | OpenXR (4.26 +) 支援 |
| ----------- | ----------- | ----------- |
| ARM64 支援 | 4.23 | ✔️ |
| 來自電腦的串流 | 4.23 | ✔️ |
| 空間對應 | 4.23 | ✔️ |
| 手部和關節追蹤 | 4.23 | ✔️ |
| 眼球追蹤 | 4.23 | ✔️ |
| 語音輸入 | 4.23 | ✔️ |
| 空間錨點 | 4.23 | ✔️ |
| 相機存取 | 4.23 | ✔️ |
| QR 代碼 | 4.23 | ✔️ |
| 空間音訊 | 4.23 | ✔️ |
| 串流的觀眾螢幕支援 | 4.24 |
| 透過串流的平面 LSR | 4.24 |
| [範例應用程式](../features-and-samples.md) | 4.24 | ✔️ |
| 行動多重檢視：效能命中 60 fps | 4.25 | ✔️ |
| 第三相機轉譯 | 4.25 | ✔️ |
| 從已封裝的桌面應用程式串流 | 4.25.1 | ✔️ |
| 適用于 HoloLens 2 的 Azure 空間錨點 | 4.25 | ✔️ |
| 混合實境 UX 工具支援 | 4.25 | ✔️ |
| 開發人員文件和教學課程 | 4.25 | ✔️ |
| 系統鍵盤 | 4.26 | ✔️ |
| HoloLens 媒體播放器外掛程式 | 4.26 | ✔️ |
| 適用于 iOS 和 Android 的 Azure 空間錨點 | 4.26 |
| 具有 Microsoft 廠商特定 OpenXR 擴充功能的 Microsoft OpenXR 外掛程式 | 4.26 | ✔️ |
| 從 Azure 串流至 HoloLens 2 | 4.26 | ✔️ |
| 適用於已封裝應用程式的 Windows 應用程式認證套件合規性 | 4.26 | ✔️ |
| HP Reverb G2 控制器支援 | 4.26 | ✔️ |

> [!div class="nextstepaction"]
> [安裝工具](../install-the-tools.md)

## <a name="see-also"></a>另請參閱
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">適用於串流、部署至模擬器和裝置的 Unreal 文件</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">行動裝置的 Unreal 效能指導方針</a>