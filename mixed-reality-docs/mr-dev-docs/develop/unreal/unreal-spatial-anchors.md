---
title: Unreal 中的本機空間錨點
description: 在 Unreal 中使用空間錨點的指南
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, 全像投影, 空間錨點, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 1c9d9fa119e57c57ab126fc26a26a35d75e07db7
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926083"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="1469a-104">Unreal 中的本機空間錨點</span><span class="sxs-lookup"><span data-stu-id="1469a-104">Local Spatial Anchors in Unreal</span></span>

<span data-ttu-id="1469a-105">空間錨點能夠以 **ARPin** 的形式將全像投影儲存在應用程式工作階段之間的真實世界空間中。</span><span class="sxs-lookup"><span data-stu-id="1469a-105">Spatial anchors save holograms in real-world space between application sessions as **ARPin** s.</span></span> <span data-ttu-id="1469a-106">ARPin 儲存在 HoloLens 的錨定存放區之後，就可以在未來的工作階段中載入，且在沒有網際網路連線時，將是理想的備用選項。</span><span class="sxs-lookup"><span data-stu-id="1469a-106">Once saved in the HoloLens' anchor store, ARPin's can be loaded in future sessions and are an ideal fallback option when there's no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="1469a-107">UE 4.25 的錨點函式在 4.26 已過時，請以較新的函式加以取代。</span><span class="sxs-lookup"><span data-stu-id="1469a-107">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="1469a-108">本機錨點會儲存在裝置上，而 Azure Spatial Anchors 會儲存在雲端。</span><span class="sxs-lookup"><span data-stu-id="1469a-108">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="1469a-109">如果您想要使用 Azure 雲端服務來儲存您的錨點，我們有一份文件可引導您整合 [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)。</span><span class="sxs-lookup"><span data-stu-id="1469a-109">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="1469a-110">請注意，您在同一個專案中可以有本機和 Azure 錨點，而不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="1469a-110">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="1469a-111">檢查錨定存放區</span><span class="sxs-lookup"><span data-stu-id="1469a-111">Checking the anchor store</span></span>

<span data-ttu-id="1469a-112">在儲存或載入錨點之前，必須先檢查錨點存放區是否準備就緒。</span><span class="sxs-lookup"><span data-stu-id="1469a-112">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="1469a-113">在錨點存放區準備就緒之前，呼叫任何 HoloLens 錨點功能將會失敗。</span><span class="sxs-lookup"><span data-stu-id="1469a-113">Calling any of the HoloLens anchor functions before the anchor store is ready won't succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="1469a-114">儲存錨點</span><span class="sxs-lookup"><span data-stu-id="1469a-114">Saving anchors</span></span>

<span data-ttu-id="1469a-115">一旦應用程式具有您需要釘選到世界的元件，就可以下列序列儲存到錨點存放區：</span><span class="sxs-lookup"><span data-stu-id="1469a-115">Once the application has a component you need to pin to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="1469a-116">將此細分：</span><span class="sxs-lookup"><span data-stu-id="1469a-116">Breaking this down:</span></span>
1. <span data-ttu-id="1469a-117">在已知位置繁衍動作項目。</span><span class="sxs-lookup"><span data-stu-id="1469a-117">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="1469a-118">根據動作項目的類別，建立具有該位置和名稱的 **ARPin**。</span><span class="sxs-lookup"><span data-stu-id="1469a-118">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="1469a-119">將動作項目新增至 **ARPin**，並將圖釘儲存至 HoloLens 錨點存放區。</span><span class="sxs-lookup"><span data-stu-id="1469a-119">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="1469a-120">您選擇的錨點名稱必須是唯一的，在這個範例中，其為目前的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="1469a-120">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="1469a-121">如果錨點成功儲存至錨點存放區，則您可以在 [系統] > [對應管理員] > [裝置上儲存的錨點檔案] 底下的 HoloLens 裝置入口網站中查看該錨點。</span><span class="sxs-lookup"><span data-stu-id="1469a-121">If the anchor is successfully saved to the anchor store, you can see it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="1469a-122">載入錨點</span><span class="sxs-lookup"><span data-stu-id="1469a-122">Loading anchors</span></span>

<span data-ttu-id="1469a-123">當應用程式啟動時，您可以使用下列藍圖來將元件還原至其錨點位置：</span><span class="sxs-lookup"><span data-stu-id="1469a-123">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="1469a-124">將此細分：</span><span class="sxs-lookup"><span data-stu-id="1469a-124">Breaking this down:</span></span>
1. <span data-ttu-id="1469a-125">逐一查看錨點存放區中的所有錨點。</span><span class="sxs-lookup"><span data-stu-id="1469a-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="1469a-126">在身分識別中繁衍動作項目。</span><span class="sxs-lookup"><span data-stu-id="1469a-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="1469a-127">從錨點存放區將該動作項目釘選到 **ARPin**。</span><span class="sxs-lookup"><span data-stu-id="1469a-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="1469a-128">請務必在身分識別繁衍動作項目，因為錨點會負責根據儲存位置在世界中重新放置全像投影。</span><span class="sxs-lookup"><span data-stu-id="1469a-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="1469a-129">此處新增的任何轉換都會將位移新增至錨點。</span><span class="sxs-lookup"><span data-stu-id="1469a-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="1469a-130">也會查詢錨點識別碼，以便根據錨點的儲存名稱來繁衍不同的動作項目。</span><span class="sxs-lookup"><span data-stu-id="1469a-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="1469a-131">移除錨點</span><span class="sxs-lookup"><span data-stu-id="1469a-131">Removing anchors</span></span> 

<span data-ttu-id="1469a-132">當您完成錨點時，可以使用 **Remove ARPin from WMRAnchor Store** 和 **Remove All ARPins from WMRAnchor Store** 元件，清除個別錨點或整個錨點存放區。</span><span class="sxs-lookup"><span data-stu-id="1469a-132">When you're done with an anchor, you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="1469a-133">請記住，空間錨點仍是 Beta 版，因此請務必回頭查看是否有更新的資訊和功能。</span><span class="sxs-lookup"><span data-stu-id="1469a-133">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="1469a-134">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="1469a-134">Next Development Checkpoint</span></span>

<span data-ttu-id="1469a-135">依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="1469a-135">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="1469a-136">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="1469a-136">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="1469a-137">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="1469a-137">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="1469a-138">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="1469a-138">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1469a-139">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="1469a-139">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="1469a-140">您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="1469a-140">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="1469a-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1469a-141">See also</span></span>
* [<span data-ttu-id="1469a-142">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="1469a-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="1469a-143">空間錨點</span><span class="sxs-lookup"><span data-stu-id="1469a-143">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="1469a-144">座標系統</span><span class="sxs-lookup"><span data-stu-id="1469a-144">Coordinate systems</span></span>](../../design/coordinate-systems.md)
