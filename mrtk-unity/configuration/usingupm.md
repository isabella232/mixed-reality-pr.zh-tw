---
title: 使用 Unity 封裝管理員
description: 在 Unity pakage 管理員中使用 MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK 套件、
ms.openlocfilehash: a231ae1d286541ae66ba4576b6eb11142a38170f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104701814"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a>混合現實工具組和 Unity 封裝管理員

從版本2.5.0 開始，使用 [混合現實功能工具](https://aka.ms/MRFeatureToolDocs)，Microsoft 混合現實工具組會在使用 unity 2019.4 和更新版本時，與 unity 封裝管理員 (UPM) 整合。

## <a name="using-the-mixed-reality-feature-tool"></a>使用 Mixed Reality 功能工具

如「 [歡迎使用混合現實」功能](https://aka.ms/MRFeatureToolDocs) 所述，您可以使用 [此連結](https://aka.ms/MRFeatureTool)來下載工具。

> [!IMPORTANT]
> 如果專案的資訊清單 `Microsoft Mixed Reality` 在區段中有一個專案 `scopedRegistries` ，建議您將它移除。
>
> 若要移除已設定的範圍登錄，請前往 `Edit`  >  `Project Settings`  >  `Package Manager` 。
>
> ![移除範圍登錄](../features/images/packaging/RemoveScopedRegistry.png)

探索功能時，MRTK 套件會出現在 `Mixed Reality Toolkit` 標題底下。

![探索功能](../features/images/packaging/DiscoverFeatures.png)

選取功能時，不需要擔心必要的相依性，工具將會自動下載並整合到專案中。

![必要的相依性](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>利用 Unity 封裝管理員管理混合的現實功能

一旦將混合現實工具組套件新增至套件資訊清單之後，就可以使用 Unity 封裝管理員使用者介面進行管理。

![MRTK Foundation UPM 套件](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> 如果使用 Unity 封裝管理員移除混合現實工具組套件，就必須使用 [先前所述的步驟](#using-the-mixed-reality-feature-tool)重新新增。

### <a name="using-mixed-reality-toolkit-examples"></a>使用混合現實工具組範例

不同于使用資產套件 ( unitypackage) 檔案， `com.microsoft.mixedreality.toolkit.examples` 而且 `com.microsoft.mixedreality.toolkit.handphysicsservice` 不會自動匯入範例場景和資產。

若要利用一或多個範例，請使用下列步驟：

1. 在 Unity 編輯器中，流覽至 `Window` > `Package Manager`
1. 在套件清單中，選取 `Mixed Reality Toolkit Examples`
1. 在清單中找出所需的範例 (s) `Samples`
1. 按一下 `Import into Project`

![匯入範例](../features/images/packaging/MRTK_ExamplesUpm.png)

更新範例套件時，Unity 會提供選項來更新匯入的範例。

> [!NOTE]
> 更新匯入的範例將會覆寫對該範例所做的任何變更，以及相關聯的資產。

## <a name="see-also"></a>另請參閱

- [混合現實工具組套件](../packages/mrtk-packages.md)
