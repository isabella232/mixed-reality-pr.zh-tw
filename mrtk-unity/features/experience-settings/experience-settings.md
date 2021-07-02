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
# <a name="experience-settings"></a>體驗設定

為混合現實建立 UI 的挑戰之一，就是在不同的體驗之間保持一致。 透過 MRTK，您可以設定 `Target Experience Scale` 場景的和 `Content Offset` ，將會設定下列各項，以針對目標尺規適當地運作。

- 混合現實場景內容
- 界限系統

  ![MRTK 設定檔中的體驗設定](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>目標體驗規模

**目標體驗規模** 會指定已設計體驗的環境。 它可以採用下列值。

* *OrientationOnly* -只利用耳機方向的體驗，並與引力對齊。 座標系統原點位於 head 層級。
* *固定* -專為使用中而設計的體驗。 座標系統原點位於地面層級。
* *長期* -專為固定的使用而設計的體驗。 座標系統原點位於地面層級。
* *房間* -設計用來支援在整個房間內移動的體驗。 座標系統原點位於地面層級。
* *世界* -設計用來在實體世界上利用和移動的體驗。 座標系統原點位於 head 層級。

## <a name="content-offset"></a>內容位移

此參數會指定當 **對齊類型** 設定為 **與經驗尺規一致** 時，在樓層上方位移 [混合現實場景內容](scene-content.md)的高度
