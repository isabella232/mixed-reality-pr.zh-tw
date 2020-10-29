---
title: 案例研究-擴充 HoloLens 的空間對應功能
description: 當您建立第一個 Microsoft HoloLens 的應用程式時，我們會積極地查看我們可以在裝置上推送空間對應界限的程度。
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、空間對應
ms.openlocfilehash: b6546c5c14c5a16f5218721d007bc83798bacfad
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91681160"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="0ffcc-104">案例研究-擴充 HoloLens 的空間對應功能</span><span class="sxs-lookup"><span data-stu-id="0ffcc-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="0ffcc-105">當您建立第一個 Microsoft HoloLens 的應用程式時，我們會積極地查看我們可以在裝置上推送空間對應界限的程度。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="0ffcc-106">Microsoft 工作室的軟體工程師 Jeff Evertt，將說明如何開發新技術，而不需要更充分掌控在使用者的真實世界環境中如何放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

> [!NOTE]
> <span data-ttu-id="0ffcc-107">HoloLens 2 可實現新的 [場景理解運行](../design/scene-understanding.md)時間，為混合的現實開發人員提供結構化、高階環境的標記法，其設計目的是為了讓環保感知應用程式的開發變得直覺。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-107">HoloLens 2 implements a new [Scene Understanding Runtime](../design/scene-understanding.md), that provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> 

## <a name="watch-the-video"></a><span data-ttu-id="0ffcc-108">觀賞影片</span><span class="sxs-lookup"><span data-stu-id="0ffcc-108">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="0ffcc-109">超越空間對應</span><span class="sxs-lookup"><span data-stu-id="0ffcc-109">Beyond spatial mapping</span></span>

<span data-ttu-id="0ffcc-110">雖然我們正在處理 [片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8) 和 [年輕 Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)，這是兩個 HoloLens 的第一場遊戲，我們發現當我們在實體世界中進行程式化的程式放置時，我們需要更高層級的瞭解使用者環境。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-110">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="0ffcc-111">每個遊戲都有自己的特定放置需求：在片段中，我們想要能夠區分不同的表面（例如樓層或資料表），以在相關位置放置線索。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-111">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="0ffcc-112">我們也想要能夠找出生活大小的全像是沙發或椅子的表面。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-112">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="0ffcc-113">在年輕 Conker 中，我們希望 Conker 和他的對手能夠在玩家的房間內，以平臺的形式使用引發的表面。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-113">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="0ffcc-114">[Asobo 工作室](https://www.asobostudio.com/index.html)是這些遊戲的開發合作夥伴，面對這個問題，並建立了一個擴充 HoloLens 空間對應功能的技術。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-114">[Asobo Studios](https://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="0ffcc-115">您可以使用這種方式來分析玩家的房間，並找出牆、表格、椅子和地面等表面。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-115">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="0ffcc-116">它也讓我們能夠針對一組條件約束進行優化，以判斷全像攝影物件的最佳位置。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-116">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="0ffcc-117">空間理解程式碼</span><span class="sxs-lookup"><span data-stu-id="0ffcc-117">The spatial understanding code</span></span>

<span data-ttu-id="0ffcc-118">我們採用 Asobo 的原始程式碼，並建立了封裝這項技術的程式庫。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-118">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="0ffcc-119">Microsoft 與 Asobo 現已開放原始碼，並可在 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) 上使用，以供您在自己的專案中使用。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-119">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="0ffcc-120">包含所有原始程式碼，可讓您依據需求進行自訂，並與您的小組分享您的改進。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-120">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="0ffcc-121">C + + 規劃的程式碼已包裝成 UWP DLL，並使用 [MixedRealityToolkit 中包含的拖放預製專案](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)向 Unity 公開。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-121">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="0ffcc-122">Unity 範例中包含許多有用的查詢，可讓您在牆上尋找空白空間、將物件放在最上方，或放在地面的大型空間、找出要放置的字元位置，以及許多其他空間理解查詢。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-122">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="0ffcc-123">雖然 HoloLens 提供的空間對應解決方案設計成足以滿足整個問題空間的需求，但是空間的理解模組是為了支援兩項特定遊戲的需要而設計的。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-123">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="0ffcc-124">因此，其解決方案是以特定程式和假設集為結構：</span><span class="sxs-lookup"><span data-stu-id="0ffcc-124">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="0ffcc-125">**固定大小 playspace** ：使用者指定 init 呼叫中最大的 playspace 大小。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-125">**Fixed size playspace** : The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="0ffcc-126">單次 **掃描程式** ：此程式需要一段獨立的掃描階段，讓使用者四處進行，定義 playspace。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-126">**One-time scan process** : The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="0ffcc-127">查詢函式在完成掃描之前將無法運作。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-127">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="0ffcc-128">**使用者導向 playspace 「繪製** 」：在掃描階段期間，使用者會四處移動和尋找 playspace，以有效地繪製應該包含的區域。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-128">**User driven playspace “painting”** : During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="0ffcc-129">產生的網格很重要，可在此階段提供使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-129">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="0ffcc-130">**室內家用或 office 設定** ：查詢函式是以適當角度的平面和牆為中心設計的。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-130">**Indoors home or office setup** : The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="0ffcc-131">這是一項軟性限制。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-131">This is a soft limitation.</span></span> <span data-ttu-id="0ffcc-132">不過，在掃描階段期間，主要軸分析已完成，可將網格鑲嵌沿著主要和次要軸優化。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-132">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="0ffcc-133">會議室掃描流程</span><span class="sxs-lookup"><span data-stu-id="0ffcc-133">Room Scanning Process</span></span>

<span data-ttu-id="0ffcc-134">當您載入空間理解模組時，您要做的第一件事就是掃描您的空間，以便找出並標示所有可用的表面（例如樓層、上限和牆）。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-134">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="0ffcc-135">在掃描過程中，您可以查看您的房間，並「繪製」掃描中應包含的區域。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-135">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="0ffcc-136">在這個階段中看到的網格是一項很重要的視覺意見反應，可讓使用者知道即將掃描的房間部分。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-136">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="0ffcc-137">空間理解模組的 DLL 會在內部將 playspace 儲存為8cm 大小體素 cube 的方格。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-137">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="0ffcc-138">在掃描的初始部分期間，主要元件分析完成以判斷房間的座標軸。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-138">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="0ffcc-139">就內部而言，它會儲存其體素空間與這些軸對齊。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-139">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="0ffcc-140">從體素磁片區解壓縮 isosurface，大約每秒會產生一個網狀。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-140">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![白色的空間對應網格，並瞭解綠色的 playspace 網格](images/spatial-mapping-500px.png)

<span data-ttu-id="0ffcc-142">白色的空間對應網格，並瞭解綠色的 playspace 網格</span><span class="sxs-lookup"><span data-stu-id="0ffcc-142">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="0ffcc-143">內含的 SpatialUnderstanding.cs 檔案會管理掃描階段程式。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-143">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="0ffcc-144">它會呼叫下列函數：</span><span class="sxs-lookup"><span data-stu-id="0ffcc-144">It calls the following functions:</span></span>
* <span data-ttu-id="0ffcc-145">**SpatialUnderstanding_Init** ：在一開始就呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-145">**SpatialUnderstanding_Init** : Called once at the start.</span></span>
* <span data-ttu-id="0ffcc-146">**GeneratePlayspace_InitScan** ：表示掃描階段應開始。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-146">**GeneratePlayspace_InitScan** : Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="0ffcc-147">**GeneratePlayspace_UpdateScan_DynamicScan** ：呼叫每個畫面格，以更新掃描程式。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-147">**GeneratePlayspace_UpdateScan_DynamicScan** : Called each frame to update the scanning process.</span></span> <span data-ttu-id="0ffcc-148">相機位置和方向會傳入，並用於 playspace 繪製程式（如上所述）。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-148">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="0ffcc-149">**GeneratePlayspace_RequestFinish** ：呼叫以結束 playspace。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-149">**GeneratePlayspace_RequestFinish** : Called to finalize the playspace.</span></span> <span data-ttu-id="0ffcc-150">這會使用掃描階段期間「繪製」的區域來定義和鎖定 playspace。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-150">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="0ffcc-151">應用程式可以在掃描階段查詢統計資料，以及查詢自訂網格以提供使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-151">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="0ffcc-152">**Import_UnderstandingMesh** ：在掃描期間，模組所提供並放置於 [瞭解] 預製專案的 **SpatialUnderstandingCustomMesh** 行為，會定期查詢處理常式所產生的自訂網格。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-152">**Import_UnderstandingMesh** : During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="0ffcc-153">此外，也會在完成掃描之後再完成一次。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-153">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="0ffcc-154">**SpatialUnderstanding** 行為所驅動的掃描流程會呼叫 **InitScan** ，然後 **UpdateScan** 每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-154">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan** , then **UpdateScan** each frame.</span></span> <span data-ttu-id="0ffcc-155">當統計資料查詢報告合理的涵蓋範圍時，使用者可以 airtap 呼叫 **RequestFinish** 來指出掃描階段結束。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-155">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="0ffcc-156">**UpdateScan** 會繼續呼叫，直到它的傳回值指出 DLL 已完成處理。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-156">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="0ffcc-157">查詢</span><span class="sxs-lookup"><span data-stu-id="0ffcc-157">The queries</span></span>

<span data-ttu-id="0ffcc-158">掃描完成後，您將能夠在介面中存取三種不同類型的查詢：</span><span class="sxs-lookup"><span data-stu-id="0ffcc-158">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="0ffcc-159">**拓撲查詢** ：這些是以掃描的房間拓撲為基礎的快速查詢。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-159">**Topology queries** : These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="0ffcc-160">**圖形查詢** ：這些查詢會利用拓撲查詢的結果，來尋找與您所定義的自訂圖形很相符的水準表面。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-160">**Shape queries** : These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="0ffcc-161">**物件放置查詢** ：這些是更複雜的查詢，可根據一組規則和物件的條件約束，找出最適合的位置。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-161">**Object placement queries** : These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="0ffcc-162">除了三個主要查詢以外，還有一個 raycasting 介面可用來取出標記的介面類別型，而且可以複製自訂的防水室網格。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-162">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="0ffcc-163">拓撲查詢</span><span class="sxs-lookup"><span data-stu-id="0ffcc-163">Topology queries</span></span>

<span data-ttu-id="0ffcc-164">在 DLL 內，拓撲管理員會處理環境的標籤。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-164">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="0ffcc-165">如上所述，大部分的資料會儲存在 surfels 中，並包含在體素磁片區中。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-165">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="0ffcc-166">此外， **PlaySpaceInfos** 結構是用來儲存有關 playspace 的資訊，包括世界上的對齊 (更多有關以下) 、樓層和上限高度的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-166">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="0ffcc-167">啟發學習法可用來決定樓層、上限和牆。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-167">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="0ffcc-168">例如，具有大於1個 m2 介面區的最大和最低水準介面會被視為樓層。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-168">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="0ffcc-169">請注意，此程式也會使用掃描程式期間的相機路徑。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-169">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="0ffcc-170">拓撲管理員公開的查詢子集會透過 DLL 公開。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-170">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="0ffcc-171">公開的拓撲查詢如下所示：</span><span class="sxs-lookup"><span data-stu-id="0ffcc-171">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="0ffcc-172">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="0ffcc-172">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="0ffcc-173">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="0ffcc-173">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="0ffcc-174">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="0ffcc-174">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="0ffcc-175">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="0ffcc-175">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="0ffcc-176">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="0ffcc-176">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="0ffcc-177">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="0ffcc-177">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="0ffcc-178">每個查詢都有一組參數，特定于查詢類型。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-178">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="0ffcc-179">在下列範例中，使用者會指定所需磁片區的最小高度 & 寬度、地面上方的最小放置高度，以及磁片區前方的最小間隙量。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-179">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="0ffcc-180">所有度量都是計量。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-180">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="0ffcc-181">這些查詢都採用預先配置的 **TopologyResult** 結構陣列。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-181">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="0ffcc-182">**LocationCount** 參數會指定傳入陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-182">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="0ffcc-183">傳回值會回報傳回位置的數目。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-183">The return value reports the number of returned locations.</span></span> <span data-ttu-id="0ffcc-184">此數位絕不會大於傳入的 **locationCount** 參數。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-184">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="0ffcc-185">**TopologyResult** 包含傳回之磁片區的中心位置、面向方向 (例如正常) ，以及所找到空間的維度。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-185">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="0ffcc-186">請注意，在 Unity 範例中，每個查詢都會連結到虛擬 UI 面板中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-186">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="0ffcc-187">此範例會將每個查詢的參數設為合理的值。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-187">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="0ffcc-188">如需更多範例，請參閱範例程式碼中的 *SpaceVisualizer.cs* 。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-188">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="0ffcc-189">圖形查詢</span><span class="sxs-lookup"><span data-stu-id="0ffcc-189">Shape queries</span></span>

<span data-ttu-id="0ffcc-190">在 DLL 內，圖形分析器 ( **ShapeAnalyzer_W** ) 會使用拓撲分析器來比對使用者所定義的自訂圖形。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-190">Inside of the DLL, the shape analyzer ( **ShapeAnalyzer_W** ) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="0ffcc-191">Unity 範例中有一組預先定義的圖形，會顯示在 [查詢] 功能表的 [圖形] 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-191">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="0ffcc-192">請注意，圖形分析僅適用于水準表面。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-192">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="0ffcc-193">例如，一名沙發是由平面基座介面和沙發的一般頂端所定義。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-193">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="0ffcc-194">圖形查詢會尋找特定大小、高度和外觀範圍的兩個表面，並將兩個表面對齊並連接。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-194">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="0ffcc-195">使用 Api 術語時，沙發基座和沙發背面是圖形元件，而對齊需求則是圖形元件條件約束。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-195">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="0ffcc-196">Unity 範例中所定義的範例查詢 ( **ShapeDefinition.cs** ) ，適用于 "sittable" 物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0ffcc-196">An example query defined in the Unity sample ( **ShapeDefinition.cs** ), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="0ffcc-197">每個圖形查詢都是由一組圖形元件所定義，每個都有一組元件條件約束，以及一組可列出元件之間相依性的圖形條件約束。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-197">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="0ffcc-198">此範例包含單一元件定義中的三個條件約束，而且元件之間沒有任何形狀條件約束 (因為只有一個元件) 。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-198">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="0ffcc-199">相反地，「沙發」圖形有兩個圖形元件和四個「形狀」條件約束。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-199">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="0ffcc-200">請注意，在此範例中，元件會以其在使用者元件清單中的索引來識別 (0 和 1) 。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-200">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="0ffcc-201">Unity 模組中提供包裝函式，可讓您輕鬆地建立自訂圖形定義。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-201">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="0ffcc-202">您可以在 **ShapeComponentConstraint** 和 **ShapeConstraint** 結構內的 **SpatialUnderstandingDll.cs** 中找到元件和圖形條件約束的完整清單。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-202">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![藍色矩形會反白顯示「椅子圖形」查詢的結果。](images/chair-shape-query-500px.png)

<span data-ttu-id="0ffcc-204">藍色矩形會反白顯示「椅子圖形」查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-204">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="0ffcc-205">物件放置規劃求解</span><span class="sxs-lookup"><span data-stu-id="0ffcc-205">Object placement solver</span></span>

<span data-ttu-id="0ffcc-206">物件放置查詢可以用來識別實體房間中的理想位置，以放置您的物件。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-206">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="0ffcc-207">在指定物件規則和條件約束的情況下，規劃求解會尋找最適合的位置。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-207">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="0ffcc-208">此外，物件查詢會持續存在，直到使用 **Solver_RemoveObject** 或 **Solver_RemoveAllObjects** 呼叫來移除物件為止，以允許受限制的多重物件放置。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-208">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="0ffcc-209">物件放置查詢包含三個部分：具有參數的放置類型、規則清單和條件約束清單。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-209">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="0ffcc-210">若要執行查詢，請使用下列 API：</span><span class="sxs-lookup"><span data-stu-id="0ffcc-210">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="0ffcc-211">此函式會接受物件名稱、位置定義，以及規則和條件約束的清單。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-211">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="0ffcc-212">C # 包裝函式提供了結構協助程式函式，讓規則和條件約束結構更容易。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-212">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="0ffcc-213">放置定義包含查詢類型，也就是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0ffcc-213">The placement definition contains the query type — that is, one of the following:</span></span>




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

<span data-ttu-id="0ffcc-214">每個放置類型都有一組唯一類型的參數。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-214">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="0ffcc-215">**ObjectPlacementDefinition** 結構包含一組靜態 helper 函式，用來建立這些定義。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-215">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="0ffcc-216">例如，若要尋找將物件放在樓層的位置，您可以使用下列函數：</span><span class="sxs-lookup"><span data-stu-id="0ffcc-216">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="0ffcc-217">除了放置類型之外，您還可以提供一組規則和條件約束。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-217">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="0ffcc-218">無法違反規則。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-218">Rules cannot be violated.</span></span> <span data-ttu-id="0ffcc-219">接著，滿足型別和規則的可能放置位置會針對一組條件約束進行優化，以選取最佳放置位置。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-219">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="0ffcc-220">每個規則和條件約束都可以透過提供的靜態建立函式來建立。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-220">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="0ffcc-221">以下提供範例規則和條件約束結構函數。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-221">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="0ffcc-222">以下的物件放置查詢正在尋找在介面邊緣放置半計量立方體的位置，而不是其他先前放置的物件和靠近房間的中心。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-222">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="0ffcc-223">如果成功，則會傳回包含放置位置、維度和方向的 **ObjectPlacementResult** 結構。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-223">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="0ffcc-224">此外，會將放置新增至 DLL 的已放置物件的內部清單。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-224">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="0ffcc-225">後續的放置查詢會將此物件列入考慮。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-225">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="0ffcc-226">Unity 範例中的 **LevelSolver.cs** 檔案包含更多範例查詢。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-226">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![藍色方塊會顯示三個位置查詢的結果，其中包含「離開相機位置」規則。](images/away-from-camera-position-500px.png)

<span data-ttu-id="0ffcc-228">藍色方塊會顯示三個位置查詢的結果，其中包含「離開相機位置」規則。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-228">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="0ffcc-229">**祕訣：**</span><span class="sxs-lookup"><span data-stu-id="0ffcc-229">**Tips:**</span></span>
* <span data-ttu-id="0ffcc-230">當您針對層級或應用程式案例所需的多個物件進行放置位置的解決時，請先解決不可或缺和大型物件，以最大化找出空間的可能性。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-230">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="0ffcc-231">放置順序很重要。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-231">Placement order is important.</span></span> <span data-ttu-id="0ffcc-232">如果找不到物件放置，請嘗試較不受限制的設定。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-232">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="0ffcc-233">擁有一組恢復設定對於跨許多房間設定支援功能非常重要。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-233">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="0ffcc-234">光線轉換</span><span class="sxs-lookup"><span data-stu-id="0ffcc-234">Ray casting</span></span>

<span data-ttu-id="0ffcc-235">除了三個主要的查詢之外，還可以使用光線轉型介面來取出標記的表面型別，而且可以在掃描和結束空間之後，將自訂的防水 playspace 網格複製出，並在內部針對圖層、上限和牆壁等表面產生標籤。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-235">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="0ffcc-236">**PlayspaceRaycast** 函式會使用光線，並在光線與已知表面衝突時傳回，如果是，則會以 **RaycastResult** 的形式呈現該介面的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-236">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult** .</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="0ffcc-237">就內部而言，raycast 是針對 playspace 的計算8cm 立方體素表示來計算。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-237">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="0ffcc-238">每個體素都包含一組介面元素，其中包含已處理的拓撲資料 (也稱為 surfels) 。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-238">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="0ffcc-239">會比較交集體素資料格內所含的 surfels，以及用來查閱拓撲資訊的最佳相符項。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-239">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="0ffcc-240">此拓撲資料包含以 **SurfaceTypes** 列舉的形式傳回的標籤，以及交集資料表面的介面區。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-240">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="0ffcc-241">在 Unity 範例中，資料指標會將光線轉換成每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-241">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="0ffcc-242">首先，針對 Unity 的 colliders;第二，針對瞭解模組的世界標記法;最後，針對 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-242">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="0ffcc-243">在此應用程式中，UI 會取得優先順序，然後是瞭解結果，最後是 Unity 的 colliders。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-243">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="0ffcc-244">**SurfaceType** 會回報為數據指標旁的文字。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-244">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Raycast 與 floor 的結果報告交集。](images/raycast-result-500px.jpg)

<span data-ttu-id="0ffcc-246">Raycast 與 floor 的結果報告交集。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-246">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="0ffcc-247">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="0ffcc-247">Get the code</span></span>

<span data-ttu-id="0ffcc-248">開放原始碼程式碼可在 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)中取得。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-248">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="0ffcc-249">如果您在專案中使用程式碼，請讓我們知道 [HoloLens 開發人員論壇](https://forums.hololens.com/) 。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-249">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="0ffcc-250">我們無法等候看看您的做法！</span><span class="sxs-lookup"><span data-stu-id="0ffcc-250">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="0ffcc-251">關於作者</span><span class="sxs-lookup"><span data-stu-id="0ffcc-251">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="0ffcc-252"><b>Jeff Evertt</b> 是一種軟體工程組長，從 incubation 到經驗的早期，一直以來都在 HoloLens 上工作。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-252"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="0ffcc-253">在 HoloLens 之前，他曾在各式各樣的平臺和遊戲中，從事 Xbox Kinect 和遊戲產業的合作。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-253">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="0ffcc-254">Jeff 熱衷於著機器人、圖形，以及亮色燈發出嗶聲的東西。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-254">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="0ffcc-255">他喜歡學習新事物和處理軟體、硬體，特別是在兩者交集的空間中。</span><span class="sxs-lookup"><span data-stu-id="0ffcc-255">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="0ffcc-256">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ffcc-256">See also</span></span>
* [<span data-ttu-id="0ffcc-257">空間對應</span><span class="sxs-lookup"><span data-stu-id="0ffcc-257">Spatial mapping</span></span>](../design/spatial-mapping.md)
* [<span data-ttu-id="0ffcc-258">場景理解</span><span class="sxs-lookup"><span data-stu-id="0ffcc-258">Scene understanding</span></span>](../design/scene-understanding.md)
* [<span data-ttu-id="0ffcc-259">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="0ffcc-259">Room scan visualization</span></span>](../design/room-scan-visualization.md)
* [<span data-ttu-id="0ffcc-260">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="0ffcc-260">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="0ffcc-261">Asobo Studio： HoloLens 開發 frontline 的課程</span><span class="sxs-lookup"><span data-stu-id="0ffcc-261">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
