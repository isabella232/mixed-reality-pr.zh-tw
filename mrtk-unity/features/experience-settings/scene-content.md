---
title: 混合現實場景內容
description: 混合現實場景內容元件的檔
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7ed81352537bec799721b49c4e2d3d55066c5316
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177344"
---
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="a97a1-104">混合現實場景內容</span><span class="sxs-lookup"><span data-stu-id="a97a1-104">Mixed Reality scene content</span></span>

<span data-ttu-id="a97a1-105">將 MRTK 新增至場景時， `MixedRealitySceneContent` 會建立 gameobject。</span><span class="sxs-lookup"><span data-stu-id="a97a1-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="a97a1-106">此物件可作為放置和具現化混合現實內容的專用位置，以確保能在許多不同的體驗中適當地進行調整。</span><span class="sxs-lookup"><span data-stu-id="a97a1-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="a97a1-107">Gameobject 具有對等的 **MixedRealitySceneContent** monobehavior，可透過 **對齊類型** 參數來設定。</span><span class="sxs-lookup"><span data-stu-id="a97a1-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="a97a1-108">此參數可採用下列值。</span><span class="sxs-lookup"><span data-stu-id="a97a1-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="a97a1-109">*AlignWithExperienceScale* -根據設定設定檔體驗中設定的 **目標體驗規模** 和 **內容位移** 來對齊內容 [設定](experience-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a97a1-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="a97a1-110">*AlignWithHeadHeight* ：將內容對齊使用者的標頭的 y 位置，也就是主要相機的位置。</span><span class="sxs-lookup"><span data-stu-id="a97a1-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![在編輯器中建立的混合現實場景內容物件](../images/experience-settings/MixedRealitySceneContent.png)
