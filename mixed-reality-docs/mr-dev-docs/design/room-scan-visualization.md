---
title: 空間位置掃描視覺效果
description: 需要空間對應的應用程式會使用裝置來收集隨時間和跨會話的資料。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、應用程式模式、設計、HoloLens、會議室掃描、空間對應、網格、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、HoloLens
ms.openlocfilehash: 8c7f1ae95cfdb520e84835f7fd5d78522e62e341
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143611"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="8fb94-104">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="8fb94-104">Room scan visualization</span></span>

<span data-ttu-id="8fb94-105">需要空間對應的應用程式會依賴裝置來收集隨時間和跨會話的資料。</span><span class="sxs-lookup"><span data-stu-id="8fb94-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="8fb94-106">對應資料的完整性和品質取決於許多因素，包括使用者已完成的探索量、從探索以來經過的時間，以及設備（例如傢俱和大門）在裝置掃描區域之後是否已移動。</span><span class="sxs-lookup"><span data-stu-id="8fb94-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="8fb94-107">為了確保有用的空間對應資料，應用程式開發人員有數個選項：</span><span class="sxs-lookup"><span data-stu-id="8fb94-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="8fb94-108">依賴可能已收集的內容。</span><span class="sxs-lookup"><span data-stu-id="8fb94-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="8fb94-109">這種資料一開始可能不完整。</span><span class="sxs-lookup"><span data-stu-id="8fb94-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="8fb94-110">要求使用者使用 bloom 手勢前往 Windows Mixed Reality 首頁，然後探索他們想要用於體驗的領域。</span><span class="sxs-lookup"><span data-stu-id="8fb94-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="8fb94-111">他們可以使用 [點一下] 來確認裝置已知所有必要的區域。</span><span class="sxs-lookup"><span data-stu-id="8fb94-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="8fb94-112">在自己的應用程式中建立自訂的探索體驗。</span><span class="sxs-lookup"><span data-stu-id="8fb94-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="8fb94-113">在這些情況下，在探索期間收集的實際資料會由系統儲存，而應用程式則不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="8fb94-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="8fb94-114">如果您想要查看作用中的房間掃描視覺效果，請參閱下面 [的設計全像影像空間感知]() 影片示範：</span><span class="sxs-lookup"><span data-stu-id="8fb94-114">If you'd like to see room scan visualization in action, check out our [Designing Holograms - Spatial Awareness]() video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="device-support"></a><span data-ttu-id="8fb94-115">裝置支援</span><span class="sxs-lookup"><span data-stu-id="8fb94-115">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8fb94-116"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="8fb94-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="8fb94-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8fb94-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8fb94-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="8fb94-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8fb94-119">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="8fb94-119">Room scan visualization</span></span></td>
        <td><span data-ttu-id="8fb94-120">✔️</span><span class="sxs-lookup"><span data-stu-id="8fb94-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="8fb94-121">建立自訂掃描體驗</span><span class="sxs-lookup"><span data-stu-id="8fb94-121">Building a custom scanning experience</span></span>

<span data-ttu-id="8fb94-122">應用程式可能會在體驗開始時分析空間對應資料，以判斷他們是否希望使用者執行額外的步驟來改善其完整性和品質。</span><span class="sxs-lookup"><span data-stu-id="8fb94-122">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="8fb94-123">如果分析指出品質應獲得改善，開發人員應該提供視覺效果以在世界上重迭，以表示：</span><span class="sxs-lookup"><span data-stu-id="8fb94-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="8fb94-124">使用者鄰近區中的總數量必須是經驗的一部分</span><span class="sxs-lookup"><span data-stu-id="8fb94-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="8fb94-125">使用者應該前往哪裡改善資料</span><span class="sxs-lookup"><span data-stu-id="8fb94-125">Where the user should go to improve data</span></span>

<span data-ttu-id="8fb94-126">使用者不知道什麼會進行「良好」掃描。</span><span class="sxs-lookup"><span data-stu-id="8fb94-126">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="8fb94-127">如果系統要求您評估掃描– flatness、與實際牆的距離等等，則需要顯示或告知要尋找的內容。</span><span class="sxs-lookup"><span data-stu-id="8fb94-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="8fb94-128">開發人員應執行意見反應迴圈，其中包含在掃描或探索階段期間重新整理空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="8fb94-128">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="8fb94-129">在許多情況下，最好告知使用者他們需要做什麼，才能取得所需的掃描品質。</span><span class="sxs-lookup"><span data-stu-id="8fb94-129">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="8fb94-130">例如，看看最高的、看看家具的後方等等。</span><span class="sxs-lookup"><span data-stu-id="8fb94-130">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="8fb94-131">快取與連續空間對應</span><span class="sxs-lookup"><span data-stu-id="8fb94-131">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="8fb94-132">空間對應資料是最繁重的資料來源應用程式可取用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8fb94-132">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="8fb94-133">若要避免效能問題（例如捨棄的畫面格或間斷情形），應謹慎地使用此資料。</span><span class="sxs-lookup"><span data-stu-id="8fb94-133">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="8fb94-134">使用體驗期間的主動式掃描可能會有很大的好處，因此您必須根據經驗決定要使用的方法。</span><span class="sxs-lookup"><span data-stu-id="8fb94-134">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="8fb94-135">快取的空間對應</span><span class="sxs-lookup"><span data-stu-id="8fb94-135">Cached spatial mapping</span></span>

<span data-ttu-id="8fb94-136">如果有快取的空間對應資料，應用程式通常會取得空間對應資料的快照集，並在體驗期間使用此快照集。</span><span class="sxs-lookup"><span data-stu-id="8fb94-136">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="8fb94-137">**優點**</span><span class="sxs-lookup"><span data-stu-id="8fb94-137">**Benefits**</span></span>
* <span data-ttu-id="8fb94-138">降低系統的額外負荷，同時體驗能大幅提高電源、散熱和 cpu 效能。</span><span class="sxs-lookup"><span data-stu-id="8fb94-138">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="8fb94-139">更簡單的主要體驗，因為空間資料的變更不會中斷。</span><span class="sxs-lookup"><span data-stu-id="8fb94-139">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="8fb94-140">針對物理、圖形和其他用途之空間資料的任何後置處理，都是單一時間成本。</span><span class="sxs-lookup"><span data-stu-id="8fb94-140">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="8fb94-141">**缺點**</span><span class="sxs-lookup"><span data-stu-id="8fb94-141">**Drawbacks**</span></span>
* <span data-ttu-id="8fb94-142">實際物件或人員的移動不會由快取的資料反映。</span><span class="sxs-lookup"><span data-stu-id="8fb94-142">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="8fb94-143">例如，應用程式可能會在現在關閉時將門視為開啟。</span><span class="sxs-lookup"><span data-stu-id="8fb94-143">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="8fb94-144">可能會有更多的應用程式記憶體，以維護資料的快取版本。</span><span class="sxs-lookup"><span data-stu-id="8fb94-144">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="8fb94-145">這種方法的良好案例是受控制的環境或資料表最上層的遊戲。</span><span class="sxs-lookup"><span data-stu-id="8fb94-145">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="8fb94-146">連續空間對應</span><span class="sxs-lookup"><span data-stu-id="8fb94-146">Continuous spatial mapping</span></span>

<span data-ttu-id="8fb94-147">某些應用程式可能會依賴繼續掃描以重新整理空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="8fb94-147">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="8fb94-148">**優點**</span><span class="sxs-lookup"><span data-stu-id="8fb94-148">**Benefits**</span></span>
* <span data-ttu-id="8fb94-149">您不需要在應用程式中事先建立個別的掃描或探索體驗。</span><span class="sxs-lookup"><span data-stu-id="8fb94-149">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="8fb94-150">雖然有一些延遲，但遊戲可能會反映實際物件的移動。</span><span class="sxs-lookup"><span data-stu-id="8fb94-150">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="8fb94-151">**缺點**</span><span class="sxs-lookup"><span data-stu-id="8fb94-151">**Drawbacks**</span></span>
* <span data-ttu-id="8fb94-152">在主要體驗的執行上有更高的複雜度。</span><span class="sxs-lookup"><span data-stu-id="8fb94-152">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="8fb94-153">由於這些系統必須以累加方式內嵌變更，因此可能會造成額外的圖形和物理處理的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="8fb94-153">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="8fb94-154">更高的電源、冷卻和 CPU 衝擊。</span><span class="sxs-lookup"><span data-stu-id="8fb94-154">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="8fb94-155">這種方法的理想情況是，全像投影必須與移動物件互動的情況，例如，地面磁片磁碟機可能會想要根據其為開啟或關閉而逐漸進入大門的全像汽車。</span><span class="sxs-lookup"><span data-stu-id="8fb94-155">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fb94-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fb94-156">See also</span></span>

* [<span data-ttu-id="8fb94-157">空間對應</span><span class="sxs-lookup"><span data-stu-id="8fb94-157">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="8fb94-158">座標系統</span><span class="sxs-lookup"><span data-stu-id="8fb94-158">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="8fb94-159">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="8fb94-159">Spatial sound design</span></span>](spatial-sound-design.md)