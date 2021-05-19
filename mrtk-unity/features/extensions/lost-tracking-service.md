---
title: 遺失追蹤服務
description: MRTK 中的 LostTracking 服務總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 96090b05c60cfaa6ff5d8c5e1dc7a58cc2658b71
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144519"
---
# <a name="lost-tracking-visualization"></a><span data-ttu-id="fbbda-104">遺失追蹤視覺效果</span><span class="sxs-lookup"><span data-stu-id="fbbda-104">Lost tracking visualization</span></span>

![遺失追蹤](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="fbbda-106">遺失追蹤延伸模組服務會為遺失的追蹤狀態提供 HoloLens shell 樣式的動畫視覺效果。</span><span class="sxs-lookup"><span data-stu-id="fbbda-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="fbbda-107">如何使用遺失的追蹤延伸模組</span><span class="sxs-lookup"><span data-stu-id="fbbda-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="fbbda-108">在 MRTK 設定檔中，將 **遺失的追蹤服務** 新增至延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fbbda-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="fbbda-109">指派包含 **LostTrackingVisualPrefab** 的 **DefaultLostTrackingServiceProfile** 。</span><span class="sxs-lookup"><span data-stu-id="fbbda-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
