---
title: 遺失追蹤服務
description: MRTK 中的 LostTracking 服務總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 70274639326563b1f3c3a2061dcdbf824fd43709
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176223"
---
# <a name="lost-tracking-service"></a><span data-ttu-id="fec5a-104">遺失追蹤服務</span><span class="sxs-lookup"><span data-stu-id="fec5a-104">Lost tracking service</span></span>

![遺失追蹤](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="fec5a-106">遺失追蹤延伸模組服務會為遺失的追蹤狀態提供 HoloLens shell 樣式的動畫視覺效果。</span><span class="sxs-lookup"><span data-stu-id="fec5a-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="fec5a-107">如何使用遺失的追蹤延伸模組</span><span class="sxs-lookup"><span data-stu-id="fec5a-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="fec5a-108">在 MRTK 設定檔中，將 **遺失的追蹤服務** 新增至延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fec5a-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="fec5a-109">指派包含 **LostTrackingVisualPrefab** 的 **DefaultLostTrackingServiceProfile** 。</span><span class="sxs-lookup"><span data-stu-id="fec5a-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
