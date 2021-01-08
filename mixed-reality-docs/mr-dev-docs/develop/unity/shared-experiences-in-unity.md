---
title: Unity 中的共用體驗
description: 瞭解如何使用 Azure 空間錨點，在 Unity 應用程式的多個使用者之間共用相同的全像投影。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共用、錨定、WorldAnchor、MR 共用250、WorldAnchorTransferBatch、>spatialperception、Azure、Azure 空間錨點、ASA、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: a82439d5676bf4bcb7898a33aafc29b43e91a49f
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98031954"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="ab117-104">Unity 中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="ab117-104">Shared experiences in Unity</span></span>

<span data-ttu-id="ab117-105">共用的體驗可讓多個使用者（每個使用者都有自己的 HoloLens、iOS 或 Android 裝置）共同查看相同的全像影像，並與之互動。</span><span class="sxs-lookup"><span data-stu-id="ab117-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="ab117-106">全像是透過空間錨點共用，在空間中的固定點放置全像投影。</span><span class="sxs-lookup"><span data-stu-id="ab117-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="ab117-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="ab117-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="ab117-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> 會建立持久的雲端支援空間錨點，讓您的應用程式可在多個 HoloLens、IOS 和 Android 裝置上找到。</span><span class="sxs-lookup"><span data-stu-id="ab117-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="ab117-109">藉由在多個裝置上共用一般空間錨點，每個使用者都可以在相同的實體位置中看到相對於該錨點轉譯的內容。</span><span class="sxs-lookup"><span data-stu-id="ab117-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="ab117-110">您也可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> ，在 HoloLens、IOS 和 Android 裝置上進行非同步全像保存。</span><span class="sxs-lookup"><span data-stu-id="ab117-110">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="ab117-111">藉由共用長期雲端空間錨點，即使這些裝置不會同時存在，多個裝置也可以觀察經過一段時間的相同保存全息圖。</span><span class="sxs-lookup"><span data-stu-id="ab117-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="ab117-112">若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="ab117-112">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="ab117-113">設定好 Azure 空間錨點之後，您可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="ab117-113">Once Azure Spatial Anchors is set up, you can <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="ab117-114">本機錨點傳送</span><span class="sxs-lookup"><span data-stu-id="ab117-114">Local anchor transfers</span></span>

<span data-ttu-id="ab117-115">在您無法使用 Azure 空間錨點的情況下， [本機錨點轉移](../../out-of-scope/local-anchor-transfers-in-unity.md) 可讓一部 hololens 裝置匯出錨點，讓第二個 hololens 可以匯入錨點。</span><span class="sxs-lookup"><span data-stu-id="ab117-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="ab117-116">IOS 和 Android 裝置不支援此方法，而且提供比 Azure 空間錨點更低的健全錨點召回。</span><span class="sxs-lookup"><span data-stu-id="ab117-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="ab117-117">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="ab117-117">Next Development Checkpoint</span></span>

<span data-ttu-id="ab117-118">如果您正在遵循我們所配置的 Unity 開發旅程圖，您將會在探索混合現實平臺功能和 Api。</span><span class="sxs-lookup"><span data-stu-id="ab117-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="ab117-119">您可以從這裡繼續進行下一節：</span><span class="sxs-lookup"><span data-stu-id="ab117-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab117-120">定位相機</span><span class="sxs-lookup"><span data-stu-id="ab117-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="ab117-121">或者，直接跳到在裝置或模擬器上部署應用程式的主題：</span><span class="sxs-lookup"><span data-stu-id="ab117-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab117-122">部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="ab117-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="ab117-123">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#3-platform-capabilities-and-apis)。</span><span class="sxs-lookup"><span data-stu-id="ab117-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab117-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab117-124">See also</span></span>
* [<span data-ttu-id="ab117-125">混合實境中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="ab117-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="ab117-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="ab117-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="ab117-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="ab117-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
