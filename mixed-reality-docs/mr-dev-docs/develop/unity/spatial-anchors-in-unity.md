---
title: Unity 中的世界鎖定和空間錨點
description: 瞭解如何在 Unity 混合現實應用程式中使用世界鎖定工具和空間錨點。
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity、空間錨點、錨定存放區、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、全球鎖定工具、全像影像
ms.openlocfilehash: 1de3571d0ad43308acad459021f2c2e9a1a6e1e7
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244282"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a>Unity 中的世界鎖定和空間錨點

![全球鎖定工具主圖影像](images/wlt-img-01.jpeg)

讓您的全像坐放在原處、與您一起移動，或是在某些情況下，相對於其他的全像是其他的全像是建立混合現實應用程式的一大部分。 本文將引導您使用世界鎖定工具的建議解決方案，但我們也會討論如何在 Unity 專案中手動設定空間錨點。 在我們跳到任何程式碼之前，請務必先瞭解 Unity 如何處理其本身引擎中的座標空間和錨點。

## <a name="world-scale-coordinate-systems"></a>全球規模座標系統

現在，在撰寫遊戲、資料視覺效果應用程式或虛擬實境應用程式時，一般的方法是建立一個絕對 **全局座標系統** ，讓所有其他座標都能可靠地對應回。 在該環境中，您一律可以尋找穩定的轉換，以定義該世界中任何兩個物件之間的關聯性。 如果您未移動這些物件，其相對轉換一律會維持不變。 在轉譯單純的虛擬世界（您事先知道所有幾何）時，這種全域座標系統很容易就會出現。 現今的房間規模的 VR 應用程式通常會建立這種絕對房間縮放座標系統及其原點。

相反地，非網路共用的混合現實裝置（例如 HoloLens）對世界有動態的感應器驅動理解，並持續調整使用者周圍環境的知識，因為它們會在整個建築樓層中逐步進行許多計量。 在全球規模的體驗中，如果您將所有的全像放在全面固定的座標系統中，這些的全像離開會在一段時間後結束。

例如，耳機目前可能會認為世界上有兩個位置彼此之間有4個度量，然後在稍後調整該瞭解，並瞭解這些位置其實是3.9 計量。 如果這些全息片一開始在單一固定座標系統中放置4個計量，則其中一個會從真實世界一直顯示0.1 計量。

您可以手動將 **空間錨點** 放置在 Unity 中，以在使用者為行動裝置時，維持實體世界中的全息圖位置，而這犧牲虛擬世界內的自我一致性。 不同的錨點會不斷地彼此間移動，而且也會在全域座標空間中移動。 在此案例中，像是版面配置這樣簡單的工作會變得很困難，而物理模擬也

**世界鎖定工具** 為您提供兩種世界的最佳選擇，在使用者四處移動的情況下，使用內部提供的空間錨點，在整個虛擬場景中進行穩定的固定座標系統。 這些工具會分析相機的座標和每個畫面格的空間錨點。 這些工具不會變更世界中所有專案的座標，以彌補使用者的標頭中的校正，而是改為修正標頭的座標。

## <a name="choosing-your-world-locking-approach"></a>選擇您的世界鎖定方法

* 我們建議您針對所有的全像位置需求使用 **世界鎖定工具** 。
    * 全球鎖定工具提供穩定的座標系統，可將虛擬與真實世界標記之間的明顯不一致範圍降至最低。 以另一種方式進行，它會以共用的錨點鎖定整個場景，而不是使用群組本身的個別錨點鎖定每個物件群組。
    * 全球鎖定工具會自動處理內部的空間錨點建立和管理。 您不需要與 **ARAnchorManager** 或 **WorldAnchor** 互動，就能讓您的全像世界鎖定。
* **針對使用 OpenXR 或 Windows XR 外掛程式的 Unity 2019/2020**，您需要使用 **ARAnchorManager**
* **針對較舊的 Unity 版本或 WSA** 專案，您需要使用 **WorldAnchor**

## <a name="setting-up-world-locking"></a>設定世界鎖定

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a>持續性世界鎖定

空間錨點會將影像儲存在應用程式會話之間的真實世界空間中。 一旦儲存在 HoloLens 的錨點存放區中，就可以在不同的會話中找到和載入它們，而且在沒有網際網路連線時，是理想的回復。

> [!IMPORTANT]
> 本機錨點會儲存在裝置上，而 Azure Spatial Anchors 會儲存在雲端。 如果您想要使用 Azure 雲端服務來儲存您的錨點，我們有一份文件可引導您整合 [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors)。 請注意，您在同一個專案中可以有本機和 Azure 錨點，而不會發生衝突。

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a>共用座標空間

如果您想要共用世界鎖定的座標空間，請參閱我們的全方位 [共用體驗檔](shared-experiences-in-unity.md)。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實核心構成要素。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [空間對應](spatial-mapping-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [全球鎖定工具簡介](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [快速入門指南](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [教學課程](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [範例](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [空間錨點持續性](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a>
* [體驗規模調整](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空間階段](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的追蹤遺失](tracking-loss-in-unity.md)
* [空間錨點](../../design/spatial-anchors.md)
* [Unity 中的共用體驗](shared-experiences-in-unity.md)
