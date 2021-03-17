---
title: Unity 中的空間錨點
description: 瞭解如何在 Unity 混合現實應用程式中建立、儲存和提取空間錨點。
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity、空間錨點、錨定存放區、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623618"
---
# <a name="spatial-anchors-in-unity"></a>Unity 中的空間錨點

空間錨點會將影像儲存在應用程式會話之間的真實世界空間中。 一旦儲存在 HoloLens 的錨點存放區之後，就可以在不同的會話中找到和載入它們，而且當沒有網際網路連線時，就是理想的回復。

> [!IMPORTANT]
> 本機錨點會儲存在裝置上，而 Azure Spatial Anchors 會儲存在雲端。 如果您想要使用 Azure 雲端服務來儲存您的錨點，我們有一份文件可引導您整合 [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors)。 請注意，您在同一個專案中可以有本機和 Azure 錨點，而不會發生衝突。

## <a name="understanding-anchors"></a>瞭解錨點

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a>使用 AnchorStore

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實核心構成要素。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [空間對應](spatial-mapping-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [空間錨點持續性](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a>
* [體驗規模調整](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空間階段](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的追蹤遺失](tracking-loss-in-unity.md)
* [空間錨點](../../design/spatial-anchors.md)
* [Unity 中的共用體驗](shared-experiences-in-unity.md)