---
title: README_LostTrackingService
description: MRTK 中的 LostTracking 服務總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 30ca86f724f183e42e1332f5c26fc8bb54d56900
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780390"
---
# <a name="lost-tracking-visualization"></a>遺失追蹤視覺效果

![遺失追蹤](images/lost-tracking/LostTrackingVisualization.jpg)

遺失追蹤延伸模組服務會為遺失的追蹤狀態提供 HoloLens shell 樣式的動畫視覺效果。

## <a name="how-to-use-lost-tracking-extensions"></a>如何使用遺失的追蹤延伸模組

在 MRTK 設定檔中，將 **遺失的追蹤服務** 新增至延伸模組。 指派包含 **LostTrackingVisualPrefab** 的 **DefaultLostTrackingServiceProfile** 。

<img src="images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extensions">
