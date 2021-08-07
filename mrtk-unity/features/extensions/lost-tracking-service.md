---
title: 遺失追蹤服務
description: MRTK 中的 LostTracking 服務總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 3b12378780a9d57217b88de9fdcbc97d0f94c57200efd20fd30054b31aee669f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212632"
---
# <a name="lost-tracking-service"></a>遺失追蹤服務

![遺失追蹤](../images/lost-tracking/LostTrackingVisualization.jpg)

遺失追蹤延伸模組服務會為遺失的追蹤狀態提供 HoloLens shell 樣式的動畫視覺效果。

## <a name="how-to-use-lost-tracking-extensions"></a>如何使用遺失的追蹤延伸模組

在 MRTK 設定檔中，將 **遺失的追蹤服務** 新增至延伸模組。 指派包含 **LostTrackingVisualPrefab** 的 **DefaultLostTrackingServiceProfile** 。

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
