---
title: Unity 中的共用體驗
description: 在 Unity 應用程式的多個使用者之間共用相同的全息。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共用、錨定、WorldAnchor、MR 共用250、WorldAnchorTransferBatch、>spatialperception、Azure、Azure 空間錨點、ASA
ms.openlocfilehash: 324aecdc89b4996625ce93514616c32d2d064ffa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679824"
---
# <a name="shared-experiences-in-unity"></a>Unity 中的共用體驗

共用體驗是指多個使用者，每個使用者都有自己的 HoloLens、iOS 或 Android 裝置，並共同查看位於空間內固定點的相同全息圖並進行互動。 這是透過空間錨點共用來完成。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

您可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> 來建立持久的雲端支援空間錨點，讓您的應用程式可在多個 HoloLens、IOS 和 Android 裝置上找到。  藉由在多個裝置上共用一般空間錨點，每個使用者都可以在相同的實體位置中看到相對於該錨點轉譯的內容。  這可提供即時共用體驗。

您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。  藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。

若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。

在您啟動並執行 Azure 空間錨點之後，您可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。

## <a name="local-anchor-transfers"></a>本機錨點傳送

在您無法使用 Azure 空間錨點的情況下， [本機錨點轉移](../../out-of-scope/local-anchor-transfers-in-unity.md) 可讓一部 hololens 裝置匯出錨點，以供第二個 hololens 裝置匯入。  請注意，這種方法提供的錨點召回率比 Azure 空間錨點更便宜，而且此方法不支援 iOS 和 Android 裝置。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您要遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實平臺功能和 Api。 您可以從這裡繼續進行下一個主題：

> [!div class="nextstepaction"]
> [定位相機](locatable-camera-in-unity.md)

或直接跳到在裝置或模擬器上部署您的應用程式：

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機](../platform-capabilities-and-apis/using-visual-studio.md)

您隨時都可以回到 [Unity 開發檢查點](unity-development-overview.md#3-platform-capabilities-and-apis) 。

## <a name="see-also"></a>另請參閱
* [混合實境中的共用體驗](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a>
