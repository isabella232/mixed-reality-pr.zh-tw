---
title: Unity 中的共用體驗
description: 瞭解如何使用 Azure 空間錨點，在 Unity 應用程式的多個使用者之間共用相同的全像投影。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共用、錨定、WorldAnchor、MR 共用250、WorldAnchorTransferBatch、>spatialperception、Azure、Azure 空間錨點、ASA、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: f7725c8282d1b5a93d555ac0f55ee936b910ff6c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244195"
---
# <a name="shared-experiences-in-unity"></a>Unity 中的共用體驗

共用的體驗可讓多個使用者（每個使用者都有自己的 HoloLens、iOS 或 Android 裝置）共同查看相同的全像影像，並與之互動。 全像投影是透過空間錨點共用，置於空間的固定點上。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

### <a name="automated-with-world-locking-tools"></a>使用世界鎖定工具自動化

如同本機錨點，全球鎖定工具可以使用一組 Azure 空間錨點來鎖定與實體世界相關的整個座標空間，而不是使用個別錨點來鎖定個別物件。 全球鎖定整個空間不僅提供更採用遭利用精確配置的環境，也會在開發人員時間和執行時間資源中提高效率。

如需運用 Azure 空間錨點來跨 HoloLens、Android 和 iOS 裝置共用協調系統，以及跨會話保存空間的詳細資訊和範例，請參閱[全球鎖定工具檔](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLT_ASA.html)。

### <a name="manual-configuration-of-azure-spatial-anchors"></a>手動設定 Azure 空間錨點

<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>會建立持久的雲端支援空間錨點，讓您的應用程式可在多個 HoloLens、iOS 和 Android 裝置上找到。  藉由在多個裝置上共用一般空間錨點，每個使用者都可以在相同的實體位置中看到相對於該錨點轉譯的內容。

您也可以在 HoloLens、iOS 和 Android 裝置上，使用<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>來取得非同步全像持續性。  藉由共用長期雲端空間錨點，即使這些裝置不會同時存在，多個裝置也可以觀察經過一段時間的相同保存全息圖。

若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。

設定好 Azure 空間錨點之後，您可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。

## <a name="local-anchor-transfers"></a>本機錨點傳送

在您無法使用 Azure 空間錨點的情況下，[本機錨點傳輸](../../out-of-scope/local-anchor-transfers-in-unity.md)會讓一個 HoloLens 裝置匯出錨點，讓第二個 HoloLens 可以將它匯入。  IOS 和 Android 裝置不支援此方法，而且提供比 Azure 空間錨點更低的健全錨點召回。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unity 開發旅程圖，您將會在探索混合現實平臺功能和 Api。 您可以從這裡繼續進行下一節：

> [!div class="nextstepaction"]
> [定位相機](locatable-camera-in-unity.md)

或者，直接跳到在裝置或模擬器上部署應用程式的主題：

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機](../platform-capabilities-and-apis/using-visual-studio.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#3-advanced-features)。

## <a name="see-also"></a>另請參閱
* [混合實境中的共用體驗](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a>