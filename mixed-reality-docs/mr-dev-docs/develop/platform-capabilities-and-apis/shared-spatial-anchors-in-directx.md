---
title: DirectX 中的共用空間錨點
description: 說明如何藉由共用空間錨點來同步處理兩個 HoloLens 裝置。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens，同步處理，空間錨點，傳輸，多人遊戲，視圖，案例，逐步解說，範例程式碼，Azure，Azure 空間錨點，ASA
ms.openlocfilehash: 4e41975a18c28cb2228b20ebb5d3a445774cca44
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530327"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="bddfb-104">DirectX 中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="bddfb-104">Shared experiences in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="bddfb-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="bddfb-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="bddfb-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](../native/openxr-getting-started.md)**。</span><span class="sxs-lookup"><span data-stu-id="bddfb-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)**.</span></span>

<span data-ttu-id="bddfb-107">共用的體驗就是有多個使用者擁有自己的 HoloLens、iOS 或 Android 裝置，並共同查看相同的全像影像並與其互動。</span><span class="sxs-lookup"><span data-stu-id="bddfb-107">A shared experience is one where multiple users with their own HoloLens, iOS, or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="bddfb-108">您可以使用空間錨點共用，在空間中的固定點放置全像影像。</span><span class="sxs-lookup"><span data-stu-id="bddfb-108">The hologram is positioned at a fixed point in space using spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="bddfb-109">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="bddfb-109">Azure Spatial Anchors</span></span>

<span data-ttu-id="bddfb-110">您可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> 來建立持久的雲端支援空間錨點，讓您的應用程式可在多個 HoloLens、IOS 和 Android 裝置上找到。</span><span class="sxs-lookup"><span data-stu-id="bddfb-110">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="bddfb-111">藉由在多個裝置上共用一般空間錨點，每個使用者都可以在相同的實體位置中看到相對於該錨點轉譯的內容。</span><span class="sxs-lookup"><span data-stu-id="bddfb-111">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="bddfb-112">這可提供即時共用體驗。</span><span class="sxs-lookup"><span data-stu-id="bddfb-112">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="bddfb-113">您也可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> ，在 HoloLens、IOS 和 Android 裝置上進行非同步全像保存。</span><span class="sxs-lookup"><span data-stu-id="bddfb-113">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="bddfb-114">藉由共用長期雲端空間錨點，即使這些裝置不會同時存在，多個裝置也可以觀察經過一段時間的相同保存全息圖。</span><span class="sxs-lookup"><span data-stu-id="bddfb-114">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="bddfb-115">若要開始在您的 HoloLens 應用程式中建立共用體驗，請嘗試5分鐘的 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間錨點 HoloLens 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="bddfb-115">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="bddfb-116">當您啟動並執行 Azure 空間錨點之後，您就可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">在 HoloLens 上建立並找出錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="bddfb-116">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="bddfb-117">適用于 <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> 的逐步解說也可讓您在所有裝置上共用相同的錨點。</span><span class="sxs-lookup"><span data-stu-id="bddfb-117">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="bddfb-118">本機錨點傳送</span><span class="sxs-lookup"><span data-stu-id="bddfb-118">Local anchor transfers</span></span>

<span data-ttu-id="bddfb-119">在您無法使用 Azure 空間錨點的情況下， [本機錨點轉移](../../out-of-scope/local-anchor-transfers-in-directx.md) 可讓一部 hololens 裝置匯出錨點，以供第二個 hololens 裝置匯入。</span><span class="sxs-lookup"><span data-stu-id="bddfb-119">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="bddfb-120">這種方法可提供比 Azure 空間錨點更便宜的錨點召回，且此方法不支援 iOS 和 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="bddfb-120">This approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="bddfb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bddfb-121">See also</span></span>
* [<span data-ttu-id="bddfb-122">混合實境中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="bddfb-122">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="bddfb-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="bddfb-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="bddfb-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">適用于 HoloLens 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="bddfb-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>