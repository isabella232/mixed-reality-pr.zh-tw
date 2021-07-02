---
title: 使用 Unity 封裝管理員
description: 在 Unity 中使用 MRTK 封裝管理員
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK 套件、
ms.openlocfilehash: 524783c48b82722aec26648ea54477a6c7bcd4ae
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177327"
---
# <a name="using-the-unity-package-manager"></a><span data-ttu-id="d8ee2-104">使用 Unity 封裝管理員</span><span class="sxs-lookup"><span data-stu-id="d8ee2-104">Using the Unity Package Manager</span></span>

<span data-ttu-id="d8ee2-105">從版本2.5.0 開始，使用[混合現實功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)，Microsoft 混合現實工具組會在使用 unity 2019.4 和更新版本時，與 unity 封裝管理員 (UPM) 整合。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="d8ee2-106">使用 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="d8ee2-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="d8ee2-107">如「 [歡迎使用混合現實」功能](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 所述，您可以使用 [此連結](https://aka.ms/MRFeatureTool)來下載工具。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8ee2-108">如果專案的資訊清單 `Microsoft Mixed Reality` 在區段中有一個專案 `scopedRegistries` ，建議您將它移除。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="d8ee2-109">若要移除已設定的範圍登錄，請前往 `Edit`  >  `Project Settings`  >  `Package Manager` 。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![移除範圍登錄](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="d8ee2-111">探索功能時，MRTK 套件會出現在 `Mixed Reality Toolkit` 標題底下。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![探索功能](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="d8ee2-113">選取功能時，不需要擔心必要的相依性，工具將會自動下載並整合到專案中。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![必要的相依性](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="d8ee2-115">利用 Unity 封裝管理員管理混合的現實功能</span><span class="sxs-lookup"><span data-stu-id="d8ee2-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="d8ee2-116">一旦將混合現實工具組套件新增至套件資訊清單之後，就可以使用 Unity 封裝管理員使用者介面進行管理。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![MRTK Foundation UPM 套件](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="d8ee2-118">如果使用 Unity 封裝管理員移除混合現實工具組套件，就必須使用[先前所述的步驟](#using-the-mixed-reality-feature-tool)重新新增。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="d8ee2-119">使用混合現實工具組範例</span><span class="sxs-lookup"><span data-stu-id="d8ee2-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="d8ee2-120">不同于使用資產套件 ( unitypackage) 檔案， `com.microsoft.mixedreality.toolkit.examples` 而且 `com.microsoft.mixedreality.toolkit.handphysicsservice` 不會自動匯入範例場景和資產。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="d8ee2-121">若要利用一或多個範例，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d8ee2-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="d8ee2-122">在 Unity 編輯器中，流覽至 `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="d8ee2-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="d8ee2-123">在套件清單中，選取 `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="d8ee2-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="d8ee2-124">在清單中找出所需的範例 (s) `Samples`</span><span class="sxs-lookup"><span data-stu-id="d8ee2-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="d8ee2-125">按一下 `Import into Project`</span><span class="sxs-lookup"><span data-stu-id="d8ee2-125">Click `Import into Project`</span></span>

![匯入範例](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="d8ee2-127">更新範例套件時，Unity 會提供選項來更新匯入的範例。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="d8ee2-128">更新匯入的範例將會覆寫對該範例所做的任何變更，以及相關聯的資產。</span><span class="sxs-lookup"><span data-stu-id="d8ee2-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8ee2-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8ee2-129">See Also</span></span>

- [<span data-ttu-id="d8ee2-130">混合現實工具組套件</span><span class="sxs-lookup"><span data-stu-id="d8ee2-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)
