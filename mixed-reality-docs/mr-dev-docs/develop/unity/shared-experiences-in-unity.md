---
title: Unity 中的共用體驗
description: 在 Unity 應用程式的多個使用者之間共用相同的全息。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共用、錨定、WorldAnchor、MR 共用250、WorldAnchorTransferBatch、>spatialperception、Azure、Azure 空間錨點、ASA、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: c9f432a2ef26e28a2329f9fd191f680a4148ca7e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678457"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="a5a0b-104">Unity 中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="a5a0b-104">Shared experiences in Unity</span></span>

<span data-ttu-id="a5a0b-105">共用體驗是指多個使用者，每個使用者都有自己的 HoloLens、iOS 或 Android 裝置，並共同查看位於空間內固定點的相同全息圖並進行互動。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="a5a0b-106">這是透過空間錨點共用來完成。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="a5a0b-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="a5a0b-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="a5a0b-108">您可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> 來建立持久的雲端支援空間錨點，讓您的應用程式可在多個 HoloLens、IOS 和 Android 裝置上找到。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="a5a0b-109">藉由在多個裝置上共用一般空間錨點，每個使用者都可以在相同的實體位置中看到相對於該錨點轉譯的內容。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="a5a0b-110">這可提供即時共用體驗。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="a5a0b-111">您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="a5a0b-112">藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="a5a0b-113">若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="a5a0b-114">在您啟動並執行 Azure 空間錨點之後，您可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="a5a0b-115">本機錨點傳送</span><span class="sxs-lookup"><span data-stu-id="a5a0b-115">Local anchor transfers</span></span>

<span data-ttu-id="a5a0b-116">在您無法使用 Azure 空間錨點的情況下， [本機錨點轉移](../../out-of-scope/local-anchor-transfers-in-unity.md) 可讓一部 hololens 裝置匯出錨點，以供第二個 hololens 裝置匯入。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="a5a0b-117">請注意，這種方法提供的錨點召回率比 Azure 空間錨點更便宜，而且此方法不支援 iOS 和 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a5a0b-118">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="a5a0b-118">Next Development Checkpoint</span></span>

<span data-ttu-id="a5a0b-119">如果您要遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實平臺功能和 Api。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-119">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="a5a0b-120">接下來，您可以繼續進行下一個主題：</span><span class="sxs-lookup"><span data-stu-id="a5a0b-120">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a5a0b-121">定位相機</span><span class="sxs-lookup"><span data-stu-id="a5a0b-121">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="a5a0b-122">或者，直接跳到在裝置或模擬器上部署應用程式的主題：</span><span class="sxs-lookup"><span data-stu-id="a5a0b-122">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a5a0b-123">部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="a5a0b-123">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="a5a0b-124">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#3-platform-capabilities-and-apis)。</span><span class="sxs-lookup"><span data-stu-id="a5a0b-124">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5a0b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5a0b-125">See also</span></span>
* [<span data-ttu-id="a5a0b-126">混合實境中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="a5a0b-126">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="a5a0b-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="a5a0b-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="a5a0b-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="a5a0b-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
