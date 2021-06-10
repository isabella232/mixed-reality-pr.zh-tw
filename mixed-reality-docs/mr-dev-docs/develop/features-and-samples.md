---
title: 範例和功能應用程式
description: 隨時掌握所有可用的 Microsoft 範例以及 HoloLens 的混合實境功能應用程式。
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 學習, 範例, MRTK, 研究模式, HoloLens 2, qr 代碼, WebRTC, 混合實境擷取, 全像攝影遠端處理, UX 工具
ms.localizationpriority: high
ms.openlocfilehash: 5738c26366b3c1aafd86b20dc70a4d078fbffb1f
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741940"
---
# <a name="samples-and-feature-apps"></a>範例和功能應用程式

![使用者配戴並手動操作 HoloLens 的圖片](unreal/images/unreal-developer.jpg)

每個開發旅程一開始都會回顧其他開發人員已成功建置的內容 - 混合實境也是如此。 目前，我們所有的教學課程和範例應用程式都是在 Unity 或 Unreal 中建置。 隨著我們開發其他引擎和平台的內容，您會在目錄中的相關標題底下找到它們。

## <a name="sample-apps"></a>範例應用程式

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>功能範例

下列功能範例對應於我們的文件中說明的特定實作，並涵蓋各種開發平臺和硬體裝置。

### <a name="openxr"></a>OpenXR

針對以 Unity 2020 為目標的開發人員建立 HoloLens 2 或混合的現實應用程式，OpenXR 外掛程式可以用來取代 WindowsXR 外掛程式，以獲得更好的跨平臺相容性。 Mixed Reality OpenXR 外掛程式也適用于最新的混合現實工具組2.7。

<br>

| 參考文章 | 範例 |
| --- | --- |
| [使用 OpenXR 外掛程式](unity/openxr-getting-started.md) | [混合現實 OpenXR 與 Unity 範例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| N/A | [OpenXR MRTK Base Unity 專案](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a>研究模式

研究模式是在第 1 代 HoloLens 中導入的，可讓您存取裝置上的主要感應器，特別是並非供部署之用的研究應用程式。 以下範例應用程式是存取和記錄研究模式資料流以及使用[內部函式和外部函式](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)的範例。

<br>

| 參考文章 | 範例應用程式 |
| --- | --- |
| [研究模式](platform-capabilities-and-apis/research-mode.md) | [HoloLens (第 1 代)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [研究模式](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>QR 代碼

HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。

<br>

| 參考文章 | 範例 |
| --- | --- |
| [QR 代碼](platform-capabilities-and-apis/qr-code-tracking.md) | [Unity 中的 QR 代碼追蹤](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a>場景理解

場景理解為混合的現實開發人員提供結構化、高階的環境標記法，其設計目的是為了讓環保感知應用程式的開發變得直覺。 場景理解藉由結合現有混合現實執行時間的強大功能，例如高度精確但較不具結構化的空間對應和全新的 AI 驅動執行時間。

<br>

| 參考文章 | 範例 |
| --- | --- |
| [場景理解](../design/scene-understanding.md) | [混合現實場景理解範例](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a>WebRTC

MixedReality-WebRTC 專案是多項元件的集合，可協助混合實境應用程式開發人員將點對點音訊、影片和資料即時通訊整合到其應用程式中。WebRTC 元件以即時通訊 (RTC) 的 WebRTC 通訊協定為基礎，大多數的新式網頁瀏覽器均加以支援。

<br>

| 參考文章 | 範例 |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [WebRTC 範例應用程式](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>全像攝影混合實境擷取

混合實境擷取 (MRC) 會以相片或影片的形式擷取將真實和數位世界融合的第一人稱體驗，並即時與其他人分享您所看到的內容。

<br>

| 參考文章 | 範例 |
| --- | --- |
| [混合實境擷取](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [混合實境擷取範例](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>全像攝影遠端處理

全像攝影遠端處理播放程式是一種隨附的應用程式，可連線至支援全像攝影遠端處理的電腦應用程式和遊戲。 全像攝影遠端處理會使用 Wi-Fi 連線即時將全像攝影內容從電腦串流至您的 Microsoft HoloLens，且在 HoloLens (第 1 代) 和 HoloLens 2 上均受支援。

<br>

| 參考文章 | 範例 |
| --- | --- |
| [全像攝影遠端處理](platform-capabilities-and-apis/holographic-remoting-player.md) | [全像攝影遠端處理範例](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |