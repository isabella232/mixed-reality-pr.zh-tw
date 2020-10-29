---
title: DirectX 中的共用空間錨點
description: 說明如何藉由共用空間錨點來同步處理兩個 HoloLens 裝置。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens，同步處理，空間錨點，傳輸，多人遊戲，視圖，案例，逐步解說，範例程式碼，Azure，Azure 空間錨點，ASA
ms.openlocfilehash: 2d6485e46a9802e1ee7e5adc12d6e0d026c79ae9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679876"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="3ae0c-104">DirectX 中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="3ae0c-104">Shared experiences in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="3ae0c-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="3ae0c-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](../native/openxr-getting-started.md)** 。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)** .</span></span>

<span data-ttu-id="3ae0c-107">共用體驗是指多個使用者，每個使用者都有自己的 HoloLens、iOS 或 Android 裝置，並共同查看位於空間內固定點的相同全息圖並進行互動。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-107">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="3ae0c-108">這是透過空間錨點共用來完成。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-108">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="3ae0c-109">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="3ae0c-109">Azure Spatial Anchors</span></span>

<span data-ttu-id="3ae0c-110">您可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> 來建立持久的雲端支援空間錨點，讓您的應用程式可在多個 HoloLens、IOS 和 Android 裝置上找到。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-110">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="3ae0c-111">藉由在多個裝置上共用一般空間錨點，每個使用者都可以在相同的實體位置中看到相對於該錨點轉譯的內容。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-111">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="3ae0c-112">這可提供即時共用體驗。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-112">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="3ae0c-113">您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-113">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="3ae0c-114">藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-114">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="3ae0c-115">若要開始在您的 HoloLens 應用程式中建立共用體驗，請嘗試5分鐘的 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間錨點 HoloLens 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-115">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="3ae0c-116">當您啟動並執行 Azure 空間錨點之後，您就可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">在 HoloLens 上建立並找出錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-116">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="3ae0c-117">適用于 <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> 的逐步解說也可讓您在所有裝置上共用相同的錨點。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-117">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="3ae0c-118">本機錨點傳送</span><span class="sxs-lookup"><span data-stu-id="3ae0c-118">Local anchor transfers</span></span>

<span data-ttu-id="3ae0c-119">在您無法使用 Azure 空間錨點的情況下， [本機錨點轉移](../../out-of-scope/local-anchor-transfers-in-directx.md) 可讓一部 hololens 裝置匯出錨點，以供第二個 hololens 裝置匯入。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-119">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="3ae0c-120">請注意，這種方法提供的錨點召回率比 Azure 空間錨點更便宜，而且此方法不支援 iOS 和 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="3ae0c-120">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ae0c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ae0c-121">See also</span></span>
* [<span data-ttu-id="3ae0c-122">混合實境中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="3ae0c-122">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="3ae0c-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="3ae0c-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="3ae0c-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">適用于 HoloLens 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="3ae0c-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>