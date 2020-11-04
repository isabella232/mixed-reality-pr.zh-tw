---
title: Unity 開發概觀
description: 開始在 Unity 中建置混合實境應用程式。
author: thetuvix
ms.author: kurtie
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合實境, 開發, 開始使用, 新專案, 移植, 功能, 相機, 模擬, 模擬, 文件
ms.openlocfilehash: 006814c17d7e2e7c343f28b83de845674c079a95
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638565"
---
# <a name="unity-development-overview"></a>Unity 開發概觀

![Unity 橫幅標誌](../images/unity_logo_banner.png)

要在 [Unity](https://unity.com) 中建置[混合實境應用程式](../../design/app-views.md)，使用混合實境工具組是最快速的途徑。 如果您是首次接觸 Unity，建議您先探索 Unity 學習平台上的入門級[教學課程](https://unity3d.com/learn/tutorials)，再繼續操作。 您也可以造訪內容豐富的[資產存放區](https://www.assetstore.unity3d.com/)和 [Unity 混合實境論壇](https://forum.unity3d.com/forums/hololens.102/)，與建置混合實境應用程式的線上社群交流。 您絕對想不到在這裡會發現哪些絕佳的資產或解決方案。 當您準備好開始使用 MRTK 時，請前往以下開發檢查點！

> [!IMPORTANT]
> 如果您想要將現有的 Unity 專案導入 HoloLens 2 中，請參閱我們的 **[移植指南](../porting-apps/porting-overview.md)** 。 對於使用 HTK、MRTK v1、SteamVR 的專案，或針對沉浸式頭戴裝置 (例如 Reverb G2、Oculus Rift、HTC Vive) 開發的專案，我們都提供了相關指南。

## <a name="development-checkpoints"></a>開發檢查點

使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。 如果您尚未探索 [設計全像投影範例應用程式](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，建議您下載並使用，以熟悉混合實境 UX 的基本概念。 

### <a name="1-getting-started"></a>1.開始使用
在 Unity 中開發最簡單的方式，就是使用混合實境工具組。 MRTK 可協助您自動設定混合實境的專案，並提供一組功能協助您加速開發流程。 閱讀本節的內容後，您大致上就已了解混合實境工具組、針對混合實境應用程式正確設定的開發環境，以及您自行建置且可在 Unity 中運作的 MRTK 專案。

|  Checkpoint  |  結果  |
| --- | --- |
| [什麼是 MRTK？](mrtk-getting-started.md) | 熟悉混合實境工具組及其提供的功能，開始您的旅程 |
| [安裝最新工具](../install-the-tools.md) | 下載並安裝最新的 Unity 套件，並設定您的混合實境專案 |
| [HoloLens 2 教學課程系列](tutorials/mr-learning-base-01.md) | 進入 HoloLens 2 硬體的入門級 MRTK 教學課程 |

> [!IMPORTANT]
> 如果您想要在未匯入混合實境工具組的情況下建立新的 Unity 專案，則您需要為 Windows Mixed Reality 手動變更一小組 Unity 設定。 這些設定分成兩個類別：每個專案和每個場景。 如需逐步程序，請參閱我們的設定指南。

> [!NOTE]
> 在您的專案中設定 MRTK V2 後，標準 Unity 遊戲物件 (例如相機) 會立即亮起，以提供坐姿級別體驗。 您可以在 [座標系統] 頁面上找到變更應用程式體驗級別的指示。

### <a name="2-core-building-blocks"></a>2.核心基本要素

混合實境應用程式的所有核心建置組塊都會以與其他 Unity API 一致的方式公開。 這些建置組塊是透過混合實境工具組提供的獨立功能。 您目前可能不需用到所有功能，但建議您及早探索。 深入探討下列核心建置組塊後，您將了解如何讓包含多樣化功能的工具箱自行或透過 MRTK 整合到混合實境專案中。

[!INCLUDE[](../includes/unity-building-blocks.md)]

### <a name="3-platform-capabilities-and-apis"></a>3.平台功能和 API

在混合實境應用程式中各有作用的其他重要功能可透過 Unity API 來使用，不需要任何額外的封裝或設定。 這些功能可以新增至 Unity 專案，且不一定需要先安裝 MRTK。 深入了解 Unity 提供的進階功能後，您將能夠建置更有深度的複雜混合實境應用程式。

|  功能  |  功能  |
| --- | --- |
| [共用體驗](shared-experiences-in-unity.md) | 使用空間錨點共用，共同檢視空間中固定點上的相同全像投影，並與其互動 |
| [定位相機](locatable-camera-in-unity.md) | 在您的混合實境應用程式中擷取相片和影片內容 |
| [對焦點](focus-point-in-unity.md) | 為 HoloLens 提供有關於如何對目前顯示的全像投影最有效地執行穩定性的提示 |
| [追蹤遺失](tracking-loss-in-unity.md) | 處理您的裝置無法在應用程式環境的空間中找到本身所在位置的狀況 |
| [鍵盤輸入](keyboard-input-in-unity.md) | 在您的應用程式中取得實際環境和混合實境鍵盤的輸入 |

### <a name="4-deploying-to-a-device-or-emulator"></a>4.部署至裝置或模擬器

當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是匯出和建置 Unity Visual Studio 解決方案。 有了該 VS 解決方案，您就可以在真正或模擬的裝置上，以三種方式之一來執行應用程式。 在本節結束時，您將能夠在任何裝置或模擬器上部署您的應用程式，以符合您的開發需求。

* [HoloLens 或 Windows 混合實境沉浸式頭戴裝置](../platform-capabilities-and-apis/using-visual-studio.md)
* [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Windows 混合實境沉浸式頭戴裝置模擬器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="5-adding-services"></a>5.新增服務

到了開發旅程的這個階段，您可能會想要新增服務，或是需要商業部署方面的協助。 將 [Azure 雲端服務](../mixed-reality-cloud-services.md)與 Dynamics 365 功能整合，可以有效提升您的專案等級。 我們編譯了一些方便您探索及擴充混合實境知識的起點。

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

針對其他可供您以自助方式新增至 Unity 專案的其他 Azure 服務，我們也提供了[完整的支援文件清單](../mixed-reality-cloud-services.md#standalone-unity-services)。

## <a name="whats-next"></a>接下來要做什麼？

開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。 完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。 請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！

### <a name="porting"></a>移植

如果您有想要移植的現有應用程式，您接下來即應參考下列文章：

* [HoloToolkit/MRTK 至 MRTK v2](mrtk-porting-guide.md)
* [沈浸式應用程式的移植指南](../porting-apps/porting-guides.md)
* [輸入移植指南](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>教學課程

如果您想要將特定的混合實境功能新增至應用程式，我們策劃了數個教學課程，可逐步引導您完成相關程序。 以下列出最多人使用的 HoloLens 2 和 HoloLens (第 1 代) 內容，但您可以瀏覽教學課程概觀以了解完整的系列。

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>其他資源

在您自行進入混合實境的世界之前，建議您先參閱下列 MRTK 相關文件。 這些文章是您深入了解 MRTK 運作方式的絕佳切入點，同時也提供如何讓應用程式更具效能的深入解析。

|  主題  |  描述  |
| --- | --- |
| [MRTK 架構概觀](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html) | 深入了解 MRTK SDK 在您的專案中如何運作 |
| [設定和效能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) | 分析您的應用程式、更新 Unity 設定，並取得最理想的全像投影穩定效能 |
| [開始使用 MRTK + XR](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) | 轉移至 Unity 所提供的替代 XR 管線 |

### <a name="unity-resources"></a>Unity 資源

除了可以在 docs.microsoft.com 上取得的本文件之外，Unity 還會隨著 Unity 編輯器一起安裝 Windows Mixed Reality 功能的文件。 Unity 提供的文件包含兩個不同的部分。

|  資源  |  描述  |
| --- | --- |
| [指令碼參考](https://docs.unity3d.com/ScriptReference/) | 這部分的文件包含 Unity 所提供之 API 指令碼的詳細資料，並且可從 Unity 編輯器線上存取，只要按一下 [說明] > [指令碼參考] 即可 |
| [手動](https://docs.unity3d.com/Manual/index.html) | 此手冊旨在協助您了解如何使用 Unity (包括基本與進階技術)，並且可從 Unity 編輯器線上存取，只要按一下 [說明] > [指令碼參考] 即可 |


> [!div class="nextstepaction"]
> [探索 MRTK](mrtk-getting-started.md)

## <a name="see-also"></a>另請參閱
* [混合實境工具組 v2](mrtk-getting-started.md)
* [MR Basics 100：開始使用 Unity](tutorials/holograms-100.md)
* [Unity 的建議設定](recommended-settings-for-unity.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [搭配使用 HoloLens 的 Windows 命名空間和 Unity 應用程式](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳作法](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 播放模式](unity-play-mode.md)
* [移植指南](../porting-apps/porting-guides.md)
