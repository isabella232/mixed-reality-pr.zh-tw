---
title: DirectX 中的共用空間錨點
description: 瞭解如何在 DirectX 應用程式中共用本機和 Azure 空間錨點，以同步處理兩個 HoloLens 裝置。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens，同步處理，空間錨點，傳輸，多人遊戲，視圖，案例，逐步解說，範例程式碼，azure，azure 空間錨點，ASA
ms.openlocfilehash: df78d9e2477fe377d61d2f2c13fc35e0a25b0b2cc37eeb883a69d2041fe42f9b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193542"
---
# <a name="shared-experiences-in-directx"></a>DirectX 中的共用體驗

> [!NOTE]
> 本文與舊版 WinRT 原生 Api 相關。  針對新的原生應用程式專案，建議使用 **[OPENXR API](../native/openxr-getting-started.md)**。

共用的體驗就是具有自己的 HoloLens、iOS 或 Android 裝置的多個使用者，會共同查看相同的全像影像並與其互動。 您可以使用空間錨點共用，在空間中的固定點放置全像影像。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

您可以使用<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>來建立持久的雲端支援空間錨點，讓您的應用程式可在多個 HoloLens、iOS 和 Android 裝置上找到。  藉由在多個裝置上共用一般空間錨點，每個使用者都可以在相同的實體位置中看到相對於該錨點轉譯的內容。  這可提供即時共用體驗。

您也可以在 HoloLens、iOS 和 Android 裝置上，使用<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>來取得非同步全像持續性。  藉由共用長期雲端空間錨點，即使這些裝置不會同時存在，多個裝置也可以觀察經過一段時間的相同保存全息圖。

若要開始在您的 HoloLens 應用程式中建立共用體驗，請嘗試5分鐘的<a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間錨點 HoloLens 快速入門</a>。

當您啟動並執行 Azure 空間錨點之後，您就可以<a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">在 HoloLens 上建立並找出錨點</a>。  適用于 <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> 的逐步解說也可讓您在所有裝置上共用相同的錨點。

## <a name="local-anchor-transfers"></a>本機錨點傳送

在您無法使用 Azure 空間錨點的情況下，[本機錨點傳輸](../../out-of-scope/local-anchor-transfers-in-directx.md)可讓一個 HoloLens 裝置匯出錨點，以供第二個 HoloLens 裝置匯入。  這種方法可提供比 Azure 空間錨點更便宜的錨點召回，且此方法不支援 iOS 和 Android 裝置。

## <a name="see-also"></a>另請參閱

* [混合實境中的共用體驗](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">適用于 HoloLens 的 Azure 空間錨點 SDK</a>