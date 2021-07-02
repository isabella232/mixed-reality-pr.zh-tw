---
title: 資產交換公用程式
description: 說明如何使用 MRTK for Unity 中的資產交換公用程式。
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176158"
---
# <a name="asset-swap-utility"></a>資產交換公用程式

當您在文字和內容建立工具中工作時，尋找和取代是普遍的。 當您需要交換 Unity 場景內的許多資產時，您可以在這裡 [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 和 editor 的手上。 此公用程式包含在 `Microsoft.MixedReality.Toolkit.Unity.Tools` 套件中。

`AssetSwapUtility`會將所有尋找和取代動作儲存為 ScriptableObject，使其 trival 為來回交換或儲存交換「主題」以供日後使用。

## <a name="swapping-assets"></a>交換資產

一旦建立之後，就可以輕鬆交換資產 `AssetSwapCollection` 。 讓我們示範如何使用場景中兩個藍色球體交換兩個紅色 cube。 首先，將兩個紅色 cube 新增至使用預設 Unity cube 和材質的場景 `MRTK_Standard_Red` 。

若要建立 `AssetSwapCollection` ，請流覽至 **混合現實工具組 > 公用程式 > 建立資產交換集合**。 使用 `AssetSwapCollection` 選取的填寫屬性，如下圖所示：

![Unity 編輯器中的資產交換集合](images/asset-swap-img-01.png)

接下來，從 [選取的主題] 下拉式清單中選取 [藍色球體]，然後按 [套用]。 您場景內的所有紅色 cube 都應取代為藍色球體。

![Unity 編輯器中已醒目提示所選主題的資產交換集合](images/asset-swap-img-02.png)

在此範例中，我們執行了完整的場景取代，但您可以藉由變更「選取模式」來取代場景的部分。 您也可以從 [選取的主題] 下拉式清單中選取 [紅色 Cube]，然後再按一次 [套用]，以切換回紅色 cube。

> [!NOTE]
> 您可以交換任何資產類型，例如音訊檔案、字型、prefabs 等。 `AssetSwapUtility` 會執行一些例行性檢查，以確保您會交換至類似的類型。
