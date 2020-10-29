---
title: 空間位置掃描視覺效果
description: 需要空間對應資料的應用程式依賴裝置在一段時間內自動收集此資料，並在使用者探索其環境中使用中的裝置時，跨會話自動收集此資料。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，應用程式模式、設計、HoloLens、會議室掃描、空間對應、網格
ms.openlocfilehash: 25de181bbb2dedaba9e4917f51cc80bac77cc5f1
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679436"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="8e2b8-104">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="8e2b8-104">Room scan visualization</span></span>

<span data-ttu-id="8e2b8-105">需要空間對應資料的應用程式依賴裝置在一段時間內自動收集此資料，並在使用者探索其環境中使用中的裝置時，跨會話自動收集此資料。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="8e2b8-106">這項資料的完整性和品質取決於許多因素，包括使用者已完成的探索量、從探索以來經過的時間，以及裝置掃描區域之後是否已移動傢俱和大門等物件。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="8e2b8-107">為了確保有用的空間對應資料，應用程式開發人員有數個選項：</span><span class="sxs-lookup"><span data-stu-id="8e2b8-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="8e2b8-108">依賴可能已收集的內容。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="8e2b8-109">這種資料一開始可能不完整。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="8e2b8-110">要求使用者使用 bloom 手勢前往 Windows Mixed Reality 首頁，然後探索他們想要用於體驗的領域。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="8e2b8-111">他們可以使用 [點一下] 來確認裝置已知所有必要的區域。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="8e2b8-112">在自己的應用程式中建立自訂的探索體驗。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="8e2b8-113">請注意，在所有這些情況下，在探索期間收集的實際資料會由系統儲存，而應用程式則不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="8e2b8-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="8e2b8-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8e2b8-115"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="8e2b8-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="8e2b8-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8e2b8-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8e2b8-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="8e2b8-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8e2b8-118">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="8e2b8-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="8e2b8-119">✔️</span><span class="sxs-lookup"><span data-stu-id="8e2b8-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="8e2b8-120">建立自訂掃描體驗</span><span class="sxs-lookup"><span data-stu-id="8e2b8-120">Building a custom scanning experience</span></span>

<span data-ttu-id="8e2b8-121">應用程式可能會決定在體驗開始時分析空間對應資料，以判斷是否希望使用者執行額外的步驟來改善其完整性和品質。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="8e2b8-122">如果分析指出品質應獲得改善，開發人員應該提供視覺效果以在世界上重迭，以表示：</span><span class="sxs-lookup"><span data-stu-id="8e2b8-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="8e2b8-123">使用者鄰近區中的總數量必須是經驗的一部分</span><span class="sxs-lookup"><span data-stu-id="8e2b8-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="8e2b8-124">使用者應該前往哪裡改善資料</span><span class="sxs-lookup"><span data-stu-id="8e2b8-124">Where the user should go to improve data</span></span>

<span data-ttu-id="8e2b8-125">使用者不知道什麼會進行「良好」掃描。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="8e2b8-126">如果系統要求您評估掃描– flatness、與實際牆的距離等，則需要顯示或告知要尋找的內容。開發人員應執行意見反應迴圈，其中包含在掃描或探索階段期間重新整理空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="8e2b8-127">在許多情況下，最好讓使用者知道他們需要做什麼事 (例如查看最上方的 [傢俱]) ，以便取得所需的掃描品質。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="8e2b8-128">快取與連續空間對應</span><span class="sxs-lookup"><span data-stu-id="8e2b8-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="8e2b8-129">空間對應資料是最繁重的資料來源應用程式可取用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="8e2b8-130">若要避免效能問題（例如捨棄的畫面格或間斷情形），應謹慎地使用此資料。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="8e2b8-131">在體驗期間進行主動式掃描可能會有很大的説明，而開發人員必須根據經驗決定要使用的方法。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="8e2b8-132">快取的空間對應</span><span class="sxs-lookup"><span data-stu-id="8e2b8-132">Cached spatial mapping</span></span>

<span data-ttu-id="8e2b8-133">在快取空間對應的情況下，應用程式通常會取得空間對應資料的快照集，並在體驗期間使用此快照集。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="8e2b8-134">**優點**</span><span class="sxs-lookup"><span data-stu-id="8e2b8-134">**Benefits**</span></span>
* <span data-ttu-id="8e2b8-135">降低系統的額外負荷，同時體驗能大幅提高電源、冷卻和 cpu 效能。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="8e2b8-136">更簡單的主要體驗，因為空間資料的變更不會中斷。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="8e2b8-137">針對物理、圖形和其他用途之空間資料的任何後置處理，都是單一時間成本。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="8e2b8-138">**缺點**</span><span class="sxs-lookup"><span data-stu-id="8e2b8-138">**Drawbacks**</span></span>
* <span data-ttu-id="8e2b8-139">實際物件或人員的移動不會由快取的資料反映。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="8e2b8-140">例如</span><span class="sxs-lookup"><span data-stu-id="8e2b8-140">E.g.</span></span> <span data-ttu-id="8e2b8-141">應用程式可能會在實際關閉時，將門視為開啟。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="8e2b8-142">可能會有更多的應用程式記憶體，以維護資料的快取版本。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="8e2b8-143">這種方法的良好案例是受控制的環境或資料表最上層的遊戲。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="8e2b8-144">連續空間對應</span><span class="sxs-lookup"><span data-stu-id="8e2b8-144">Continuous spatial mapping</span></span>

<span data-ttu-id="8e2b8-145">某些應用程式可能會依賴繼續掃描以重新整理空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="8e2b8-146">**優點**</span><span class="sxs-lookup"><span data-stu-id="8e2b8-146">**Benefits**</span></span>
* <span data-ttu-id="8e2b8-147">您不需要在應用程式中事先建立個別的掃描或探索體驗。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="8e2b8-148">雖然有一些延遲，但遊戲可能會反映實際物件的移動。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="8e2b8-149">**缺點**</span><span class="sxs-lookup"><span data-stu-id="8e2b8-149">**Drawbacks**</span></span>
* <span data-ttu-id="8e2b8-150">在主要體驗的執行上有更高的複雜度。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="8e2b8-151">由於變更需要以累加方式內嵌這些系統，因此可能會額外增加圖形或物理處理的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="8e2b8-152">更高的電源、冷卻和 CPU 的影響。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="8e2b8-153">這種方法的理想情況是，全像投影應該與移動物件互動的情況，例如，地面磁片磁碟機可能會想要根據其是開啟或關閉的方式，正確地移入門。</span><span class="sxs-lookup"><span data-stu-id="8e2b8-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e2b8-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e2b8-154">See also</span></span>
* [<span data-ttu-id="8e2b8-155">空間對應</span><span class="sxs-lookup"><span data-stu-id="8e2b8-155">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="8e2b8-156">座標系統</span><span class="sxs-lookup"><span data-stu-id="8e2b8-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="8e2b8-157">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="8e2b8-157">Spatial sound design</span></span>](spatial-sound-design.md)
