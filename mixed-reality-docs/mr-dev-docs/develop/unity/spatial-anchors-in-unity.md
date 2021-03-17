---
title: Unity 中的空間錨點
description: 瞭解如何在 Unity 混合現實應用程式中建立、儲存和提取空間錨點。
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity、空間錨點、錨定存放區、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623618"
---
# <a name="spatial-anchors-in-unity"></a><span data-ttu-id="7705b-104">Unity 中的空間錨點</span><span class="sxs-lookup"><span data-stu-id="7705b-104">Spatial Anchors in Unity</span></span>

<span data-ttu-id="7705b-105">空間錨點會將影像儲存在應用程式會話之間的真實世界空間中。</span><span class="sxs-lookup"><span data-stu-id="7705b-105">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="7705b-106">一旦儲存在 HoloLens 的錨點存放區之後，就可以在不同的會話中找到和載入它們，而且當沒有網際網路連線時，就是理想的回復。</span><span class="sxs-lookup"><span data-stu-id="7705b-106">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7705b-107">本機錨點會儲存在裝置上，而 Azure Spatial Anchors 會儲存在雲端。</span><span class="sxs-lookup"><span data-stu-id="7705b-107">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="7705b-108">如果您想要使用 Azure 雲端服務來儲存您的錨點，我們有一份文件可引導您整合 [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors)。</span><span class="sxs-lookup"><span data-stu-id="7705b-108">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="7705b-109">請注意，您在同一個專案中可以有本機和 Azure 錨點，而不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="7705b-109">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="understanding-anchors"></a><span data-ttu-id="7705b-110">瞭解錨點</span><span class="sxs-lookup"><span data-stu-id="7705b-110">Understanding Anchors</span></span>

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a><span data-ttu-id="7705b-111">使用 AnchorStore</span><span class="sxs-lookup"><span data-stu-id="7705b-111">Using the AnchorStore</span></span>

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="7705b-112">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="7705b-112">Next Development Checkpoint</span></span>

<span data-ttu-id="7705b-113">如果您正在遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實核心構成要素。</span><span class="sxs-lookup"><span data-stu-id="7705b-113">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="7705b-114">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="7705b-114">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7705b-115">空間對應</span><span class="sxs-lookup"><span data-stu-id="7705b-115">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="7705b-116">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="7705b-116">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7705b-117">共用體驗</span><span class="sxs-lookup"><span data-stu-id="7705b-117">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="7705b-118">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="7705b-118">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7705b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7705b-119">See Also</span></span>
* [<span data-ttu-id="7705b-120">空間錨點持續性</span><span class="sxs-lookup"><span data-stu-id="7705b-120">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="7705b-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="7705b-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="7705b-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="7705b-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="7705b-123">體驗規模調整</span><span class="sxs-lookup"><span data-stu-id="7705b-123">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="7705b-124">空間階段</span><span class="sxs-lookup"><span data-stu-id="7705b-124">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="7705b-125">Unity 中的追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="7705b-125">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="7705b-126">空間錨點</span><span class="sxs-lookup"><span data-stu-id="7705b-126">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="7705b-127">Unity 中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="7705b-127">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)