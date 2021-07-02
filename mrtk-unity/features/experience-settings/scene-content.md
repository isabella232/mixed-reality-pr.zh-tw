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
# <a name="mixed-reality-scene-content"></a>混合現實場景內容

將 MRTK 新增至場景時， `MixedRealitySceneContent` 會建立 gameobject。 此物件可作為放置和具現化混合現實內容的專用位置，以確保能在許多不同的體驗中適當地進行調整。 Gameobject 具有對等的 **MixedRealitySceneContent** monobehavior，可透過 **對齊類型** 參數來設定。 此參數可採用下列值。

* *AlignWithExperienceScale* -根據設定設定檔體驗中設定的 **目標體驗規模** 和 **內容位移** 來對齊內容 [設定](experience-settings.md)
* *AlignWithHeadHeight* ：將內容對齊使用者的標頭的 y 位置，也就是主要相機的位置。


  ![在編輯器中建立的混合現實場景內容物件](../images/experience-settings/MixedRealitySceneContent.png)
