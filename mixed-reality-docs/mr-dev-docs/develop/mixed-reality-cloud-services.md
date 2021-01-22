---
layout: LandingPage
title: Azure 混合實境雲端服務概觀
description: 了解您可整合到 Unity 或 Unreal 應用程式中的所有 Azure 混合實境雲端服務。
author: hferrone
ms.author: v-haferr
ms.date: 12/9/2020
ms.topic: overview
ms.localizationpriority: high
keywords: 混合實境, 開發, 開發, HoloLens, 雲端服務, Azure, 遠端轉譯, 空間錨點, 認知服務, 認知, unity, 機器學習, 語音翻譯, 電腦視覺, Microsoft Graph
ms.openlocfilehash: 725e41e94923f1738eb11064c772f9138a6be09a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582699"
---
# <a name="azure-mixed-reality-cloud-services-overview"></a>Azure 混合實境雲端服務概觀

![ Azure Spatial Anchors 影像](../design/images/AzureSpatialAnchors.jpg)

我們週遭的三維真實世界，是人人都熟悉的領域，透過 Azure 混合實境服務，我們這方面的能力將得以發揮。 協助人們在其工作和真實世界融合的環境中擷取及呈現數位資訊，從而更有效率地創作、學習和共同作業。 將 3D 導入行動裝置、頭戴式裝置和其他未連線的裝置中。 使用 Azure，協助您確保最敏感的資訊會受到保護。

## <a name="mixed-reality-services"></a>混合實境服務

混合實境雲端服務 (例如 **Azure 遠端轉譯** 和 **Azure 空間錨點)** 可協助開發人員在各種平台上建置引人注目的沉浸式體驗。 這些服務可讓您為 3D 訓練、預測設備維護和設計審查 (都是在使用者環境的內容中) 提出申請時，將空間感知整合到您的專案中。

### <a name="azure-remote-rendering"></a>Azure 遠端轉譯
Azure 遠端轉譯 (或簡稱 ARR) 是一項服務，可讓您即時轉譯高度複雜的 3D 模型，並將其串流至裝置。 ARR 目前處於公開預覽階段，可新增至以 HoloLens 2 或 Windows 桌上型電腦為目標的 Unity 或原生 C++ 專案。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-Azure-Mixed-Reality-Services-Azure-Remote-Rendering/player]

對於任何在未連線的裝置上執行的混合實境應用程式而言，ARR 是不可或缺的元件，因為這類應用程式的計算轉譯能力較低。 以下列兩相比較的引擎模型為例：左邊的高逼真度模型有超過 1800 萬個三角形，而右邊逼真度較低的模型則只有約 20 萬個。 在講究各個細節的案例中 (工業設備管理、卡車引擎等資產的設計審查、外科手術術前規劃等等)，3D 視覺效果都可真實呈現出這類細節。 這可協助設計人員、工程師、醫生和學生進一步了解複雜的資訊，並做出正確的決定。 但在關鍵的商業和設計決策中，可能會因為這種簡化而失去不可或缺的重要細節。

![Unity 展示應用程式中的 Azure 遠端轉譯範例](images/arr-engine.png)

ARR 可將轉譯工作負載交由雲端中的高階 GPU 處理，而解決此問題。 裝載於雲端的圖形引擎會接管並轉譯影像、將其編碼為影片串流，然後直接將模型串流至目標裝置。 

* 若有模型太過複雜而難以由單一高階 GPU 處理，ARR 會將工作負載分配給多個 GPU，並將結果合併為單一影像，而處理過程會完全透明呈現給使用者。 

ARR 的連帶好處是，您可在應用程式中使用的使用者介面類型不會受到限制。 處理最後的畫面格時，您本機轉譯的內容將會與遠端影像自動結合，如下圖所示：

![Unity 展示應用程式中的 Azure 遠端轉譯範例](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors
Azure Spatial Anchors (或簡稱 ASA) 是一種跨平台服務，可讓您建置空間感知的混合實境應用程式。 您可以使用 Azure Spatial Anchors，在全球規模的多個裝置之間對應、保存及共用全像攝影內容。 

ASA 是專為混合實境的常見使用案例設計的解決方案，這類案例包括：
* **導向**：可以連接兩個或更多空間錨點，以建立使用者必須與其互動的工作清單或興趣點。
* **多重使用者體驗**：使用者可與相同虛擬空間中的物件互動，而來回移動。
* **在真實世界中保存虛擬內容**：使用者可在真實世界中放置能夠從其他支援裝置上檢視的虛擬物件。

![Azure Spatial Anchors 範例](images/persistence.gif)

可在許多環境中開發該服務，並將其部署到大量的裝置和平台上。 這可讓他們對自己的可用平台清單進行特殊分配：
* 適用於 HoloLens 的 Unity
* 適用於 iOS 的 Unity
* 適用於 Android 的 Unity
* 原生 iOS
* 原生 Android
* HoloLens 的 C++/WinRT 和 DirectX
* 適用於 iOS 的 Xamarin
* 適用於 Android 的 Xamarin

## <a name="cognitive-services"></a>認知服務

:::row:::
    :::column:::
       [![語音](../whats-new/images/speech.jpg)](/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[語音](/azure/cognitive-services/speech-service/)
        探索「語音」如何讓語音處理功能整合到任何應用程式或服務中。 使用標準 (或可自訂) 的聲音字型，將口說的語言轉換為文字，或從文字產生自然發音的語音。 歡迎免費試用任何服務，並使用下列功能快速建置具備語音功能的應用程式和服務。
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![視覺](../whats-new/images/vision.jpg)](/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[視覺](/azure/cognitive-services/computer-vision/)
        對您的圖片、影片和數位筆跡內容進行辨識、識別、製作字幕、編製索引和仲裁。了解「視覺」如何讓應用程式和服務正確識別和分析影像、影片和數位筆跡中的內容。
    :::column-end:::
:::row-end:::


## <a name="standalone-unity-services"></a>獨立 Unity 服務

下列獨立服務不適用於混合實境，但可在各種不同的開發內容中提供幫助。 如果您在 Unity 中進行開發，則這些服務中的每個服務都可以整合到新專案或現有的專案中。

### <a name="device-support"></a>裝置支援
<table>
    <tr>
        <td><strong>Azure 雲端服務</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td><a href="unity/tutorials/mr-azure-301.md">語言翻譯</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302.md">電腦視覺</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302b.md">自訂視覺</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-303.md">跨裝置通知</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-304.md">臉部辨識</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-305.md">功能與儲存空間</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-306.md">串流視訊</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-307.md">機器學習</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-308.md"mr-azure-308.md">功能與儲存空間</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-309.md">Application insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-310.md">物件偵測</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-312.md">Bot 整合</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="see-also"></a>另請參閱

* HoloLens 2 的 Azure Spatial Anchor 教學課程 - [開始使用 Azure Spatial Anchors 3 之 1](./unity/tutorials/mr-learning-asa-02.md)
* HoloLens 2 的 Azure 語音服務教學課程 - [整合並使用語音辨識和文字記錄 4 之 1](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)