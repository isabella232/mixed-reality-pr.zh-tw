---
title: Unreal 中的 HoloLens 相片/影片相機
description: 在 Unreal 中使用 HoloLens 相片/影片相機的指南
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, 全像投影, 相機, PV 相機, MRC, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: ef557bc6492ced6bb9b3c47a8cccc897e33b76c1
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354583"
---
# <a name="hololens-photovideo-camera-in-unreal"></a>Unreal 中的 HoloLens 相片/影片相機

HoloLens 的面板上有相片/影片 (PV) 相機，不僅可用於混合實境擷取 (MRC)，也可供應用程式用來透過相機框架中的像素座標定位 Unreal 世界空間中的物件。

> [!IMPORTANT]
> PV 攝影機不支援全像攝影遠端功能，但可以使用連接到您電腦的網路攝影機來模擬 HoloLens PV 攝影機功能。

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發檢查點旅程，此時您會探索混合實境平台功能和 API。 接下來，您可以繼續進行下一個主題：

> [!div class="nextstepaction"]
> [QR 代碼](unreal-qr-codes.md)

或者，直接跳到在裝置或模擬器上部署應用程式的主題：

> [!div class="nextstepaction"]
> [部署至裝置](unreal-deploying.md)

您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#3-platform-capabilities-and-apis)。

## <a name="see-also"></a>另請參閱
* [定位相機](../platform-capabilities-and-apis/locatable-camera.md)
* [適用於開發人員的混合實境擷取](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
