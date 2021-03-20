---
title: DependencyWindow
description: 在 MRTK 中使用相依性視窗的相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: c53989151123f61988160b74fa876b907264bdd4
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104696015"
---
# <a name="dependency-window"></a>相依性視窗

在 Unity 中，通常很難 gleam 正在使用的資產，以及參考它們的內容。 當您只在意目前的場景時，[尋找場景中的參考] 選項的效果很好，但是整個 Unity 專案呢？ 這是相依性 **視窗** (資產/MRTK/工具/DependencyWindow) 可能很有用的地方。

[相依性] 視窗會顯示資產的參考方式，以及彼此之間的關係。 相依性的計算方式是剖析專案 YAML 檔中的 guid (注意：腳本相依性的腳本不會被視為) 。

## <a name="usage"></a>使用方式

若要開啟此視窗，請選取 [ *混合現實工具組->公用程式->相依性] 視窗* ，此視窗會開啟視窗並自動開始建立專案的相依性圖形。 建立相依性圖形之後，您可以在 [專案] 索引標籤中選取資產來檢查其相依性。

![相依性視窗](../images/dependency-window/MRTK_Dependency_Window.png)

此視窗會顯示目前所選資產相依的資產清單，以及相依于該資產的資產階層式清單。 如果沒有任何專案取決於目前選取的資產，您可以考慮將它從您的專案中刪除 (請注意，某些資產是透過著色器之類的 Api 以程式設計方式載入。尋找 () ，相依性追蹤程式) 可能不會攔截到這些資產。

此視窗也可以只顯示任何其他資產未參考的所有資產清單，並可將其視為刪除：

![顯示未參考資產的相依性視窗](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> 當相依性視窗正在使用中時，如果已修改、新增或移除資產，建議您重新整理相依性圖形以取得最新的結果。
