---
title: 體驗設定
description: 適用于 MRTK 的不同體驗設定檔
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177351"
---
# <a name="experience-settings"></a><span data-ttu-id="6bb8b-104">體驗設定</span><span class="sxs-lookup"><span data-stu-id="6bb8b-104">Experience settings</span></span>

<span data-ttu-id="6bb8b-105">為混合現實建立 UI 的挑戰之一，就是在不同的體驗之間保持一致。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="6bb8b-106">透過 MRTK，您可以設定 `Target Experience Scale` 場景的和 `Content Offset` ，將會設定下列各項，以針對目標尺規適當地運作。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="6bb8b-107">混合現實場景內容</span><span class="sxs-lookup"><span data-stu-id="6bb8b-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="6bb8b-108">界限系統</span><span class="sxs-lookup"><span data-stu-id="6bb8b-108">Boundary System</span></span>

  ![MRTK 設定檔中的體驗設定](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="6bb8b-110">目標體驗規模</span><span class="sxs-lookup"><span data-stu-id="6bb8b-110">Target Experience Scale</span></span>

<span data-ttu-id="6bb8b-111">**目標體驗規模** 會指定已設計體驗的環境。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="6bb8b-112">它可以採用下列值。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-112">It can take on the following values.</span></span>

* <span data-ttu-id="6bb8b-113">*OrientationOnly* -只利用耳機方向的體驗，並與引力對齊。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="6bb8b-114">座標系統原點位於 head 層級。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="6bb8b-115">*固定* -專為使用中而設計的體驗。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="6bb8b-116">座標系統原點位於地面層級。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="6bb8b-117">*長期* -專為固定的使用而設計的體驗。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="6bb8b-118">座標系統原點位於地面層級。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="6bb8b-119">*房間* -設計用來支援在整個房間內移動的體驗。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="6bb8b-120">座標系統原點位於地面層級。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="6bb8b-121">*世界* -設計用來在實體世界上利用和移動的體驗。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="6bb8b-122">座標系統原點位於 head 層級。</span><span class="sxs-lookup"><span data-stu-id="6bb8b-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="6bb8b-123">內容位移</span><span class="sxs-lookup"><span data-stu-id="6bb8b-123">Content Offset</span></span>

<span data-ttu-id="6bb8b-124">此參數會指定當 **對齊類型** 設定為 **與經驗尺規一致** 時，在樓層上方位移 [混合現實場景內容](scene-content.md)的高度</span><span class="sxs-lookup"><span data-stu-id="6bb8b-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>
