---
title: 場景理解
description: 瞭解如何使用 HoloLens 的場景理解進行開發，包括 SDK、功能和常見的使用案例。
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 場景理解、空間對應、Windows Mixed Reality、Unity、混合現實耳機、Windows Mixed reality 耳機、虛擬實境耳機、HoloLens、遮蔽、SDK
ms.openlocfilehash: 1458ca9e70a52913ae150c58393c3e030e2c1add
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583335"
---
# <a name="scene-understanding"></a><span data-ttu-id="a7783-104">場景理解</span><span class="sxs-lookup"><span data-stu-id="a7783-104">Scene understanding</span></span>

<span data-ttu-id="a7783-105">場景理解為混合的現實開發人員提供結構化、高階的環境標記法，其設計目的是為了讓環保感知應用程式的開發變得直覺。</span><span class="sxs-lookup"><span data-stu-id="a7783-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="a7783-106">場景理解藉由結合現有混合現實執行時間的強大功能，例如高度精確但較不具結構化的 [空間對應](spatial-mapping.md) 和全新的 AI 驅動執行時間。</span><span class="sxs-lookup"><span data-stu-id="a7783-106">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="a7783-107">藉由結合這些技術，場景理解會產生3D 環境的標記法，類似于您在 Unity 或 ARKit/ARCore 架構中所使用的環境。</span><span class="sxs-lookup"><span data-stu-id="a7783-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="a7783-108">場景理解進入點的開頭是場景觀察器，由您的應用程式呼叫以計算新場景。</span><span class="sxs-lookup"><span data-stu-id="a7783-108">The Scene understanding entry point begins with a Scene Observer, which is called by your application to compute a new scene.</span></span> <span data-ttu-id="a7783-109">現在，此技術可以產生3個相異但相關的物件類別：</span><span class="sxs-lookup"><span data-stu-id="a7783-109">Today, the technology can generate 3 distinct but related object categories:</span></span> 

* <span data-ttu-id="a7783-110">簡化的防水環境網格，可推斷平面房間結構而不會雜亂</span><span class="sxs-lookup"><span data-stu-id="a7783-110">Simplified watertight environment meshes that infer the planar room structure without clutter</span></span>
* <span data-ttu-id="a7783-111">用於放置的平面區域，我們稱之為四邊形</span><span class="sxs-lookup"><span data-stu-id="a7783-111">Plane regions for placement that we call Quads</span></span>
* <span data-ttu-id="a7783-112">與我們所呈現的四邊形/防水資料對齊的 [空間對應](spatial-mapping.md) 網格快照集</span><span class="sxs-lookup"><span data-stu-id="a7783-112">A snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface</span></span>

![空間對應網格、標示為平面介面、防水網格](images/SUScenarios.png)

<span data-ttu-id="a7783-114">本檔的目的是要提供案例總覽，以及說明場景理解和空間對應共用的關聯性。</span><span class="sxs-lookup"><span data-stu-id="a7783-114">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="a7783-115">使用場景理解進行開發</span><span class="sxs-lookup"><span data-stu-id="a7783-115">Developing with Scene Understanding</span></span>

<span data-ttu-id="a7783-116">本文僅適用于引入場景瞭解執行時間和概念。</span><span class="sxs-lookup"><span data-stu-id="a7783-116">This article only serves to introduce the Scene Understanding runtime and concepts.</span></span> <span data-ttu-id="a7783-117">如果您要尋找如何使用場景理解進行開發的相關檔，您可能會對下列文章感興趣：</span><span class="sxs-lookup"><span data-stu-id="a7783-117">If you're looking for documentation on how to develop with Scene Understanding, you may be interested in the following articles:</span></span>

[<span data-ttu-id="a7783-118">場景理解 SDK 總覽</span><span class="sxs-lookup"><span data-stu-id="a7783-118">Scene Understanding SDK overview</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

<span data-ttu-id="a7783-119">您可以從範例 GitHub 網站下載場景理解範例應用程式：</span><span class="sxs-lookup"><span data-stu-id="a7783-119">You can download the Scene Understanding Sample app from the sample GitHub site:</span></span>

[<span data-ttu-id="a7783-120">場景理解範例</span><span class="sxs-lookup"><span data-stu-id="a7783-120">Scene Understanding Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

<span data-ttu-id="a7783-121">如果您沒有裝置，而且想要存取範例場景來嘗試進行場景瞭解，則範例資產資料夾中會有場景：</span><span class="sxs-lookup"><span data-stu-id="a7783-121">If you don't have a device and wish to access sample scenes to try Scene Understanding out, there are scenes in the sample asset folder:</span></span>

[<span data-ttu-id="a7783-122">場景理解範例場景</span><span class="sxs-lookup"><span data-stu-id="a7783-122">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a><span data-ttu-id="a7783-123">SDK</span><span class="sxs-lookup"><span data-stu-id="a7783-123">SDK</span></span>

<span data-ttu-id="a7783-124">如果您要尋找以場景理解進行開發的特定詳細資料，請參閱 [場景理解 SDK 總覽](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 檔。</span><span class="sxs-lookup"><span data-stu-id="a7783-124">If you're looking for specific details on developing with Scene Understanding, see the [Scene Understanding SDK overview](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) documentation.</span></span>

### <a name="sample"></a><span data-ttu-id="a7783-125">範例</span><span class="sxs-lookup"><span data-stu-id="a7783-125">Sample</span></span>

## <a name="device-support"></a><span data-ttu-id="a7783-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="a7783-126">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a7783-127"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="a7783-127"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a7783-128"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7783-128"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a7783-129"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a7783-129"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a7783-130"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="a7783-130"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a7783-131">場景理解</span><span class="sxs-lookup"><span data-stu-id="a7783-131">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a7783-132">✔️</span><span class="sxs-lookup"><span data-stu-id="a7783-132">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="a7783-133">常見使用案例</span><span class="sxs-lookup"><span data-stu-id="a7783-133">Common usage scenarios</span></span>

<span data-ttu-id="a7783-134">![一般空間對應使用案例的圖例：位置、遮蔽、物理和導覽](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="a7783-134">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="a7783-135">*常見的空間對應使用案例：位置、遮蔽、物理和導覽。*</span><span class="sxs-lookup"><span data-stu-id="a7783-135">*Common spatial mapping usage scenarios: placement, occlusion, physics, and navigation.*</span></span>

<br>

<span data-ttu-id="a7783-136">環境感知應用程式的許多核心案例都可以透過空間對應和場景理解來解決。</span><span class="sxs-lookup"><span data-stu-id="a7783-136">Many of the core scenarios for environmentally aware applications can be addressed by both Spatial mapping and Scene understanding.</span></span> <span data-ttu-id="a7783-137">這些核心案例包括位置、遮蔽、物理等等。</span><span class="sxs-lookup"><span data-stu-id="a7783-137">These core scenarios include placement, occlusion, physics, and so on.</span></span> <span data-ttu-id="a7783-138">場景理解和空間對應之間的核心差異，在於結構和簡化的最大精確度和延遲的取捨。</span><span class="sxs-lookup"><span data-stu-id="a7783-138">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="a7783-139">如果您的應用程式需要最低延遲的可能，以及只想要存取的網格三角形，請直接使用空間對應。</span><span class="sxs-lookup"><span data-stu-id="a7783-139">If your application requires the lowest-latency possible and mesh triangles that only you'll want to access, use Spatial Mapping directly.</span></span> <span data-ttu-id="a7783-140">如果您要進行較高層級的處理，可以考慮改用場景理解模型，因為它應該會提供您功能的超集合。</span><span class="sxs-lookup"><span data-stu-id="a7783-140">If you're doing higher-level processing, you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="a7783-141">您一律可以存取最完整且正確的空間對應資料，因為場景理解會在其標記法中提供空間對應網格的快照。</span><span class="sxs-lookup"><span data-stu-id="a7783-141">You'll always have access to the most complete and accurate spatial mapping data possible because Scene understanding provides a snapshot of the spatial mapping mesh as part of its representation.</span></span>

<span data-ttu-id="a7783-142">下列各節會回顧新場景理解 SDK 內容中的核心空間對應案例。</span><span class="sxs-lookup"><span data-stu-id="a7783-142">The following sections revisit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="a7783-143">放置</span><span class="sxs-lookup"><span data-stu-id="a7783-143">Placement</span></span>

<span data-ttu-id="a7783-144">場景理解提供設計來簡化放置案例的新結構。</span><span class="sxs-lookup"><span data-stu-id="a7783-144">Scene understanding provides new constructs designed to simplify placement scenarios.</span></span> <span data-ttu-id="a7783-145">場景可以計算稱為 SceneQuads 的基本專案，其描述可放置全像影像的平面表面。</span><span class="sxs-lookup"><span data-stu-id="a7783-145">A scene can compute primitives called SceneQuads, which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="a7783-146">SceneQuads 的設計是圍繞放置，並描述2D 介面，並提供可放置於該介面上的 API。</span><span class="sxs-lookup"><span data-stu-id="a7783-146">SceneQuads have been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="a7783-147">先前，使用三角形網格來進行放置時，必須掃描四個部分的所有區域並進行填滿/後置處理，以找出適合物件放置的位置。</span><span class="sxs-lookup"><span data-stu-id="a7783-147">Previously, when using the triangle mesh to do placement, one had to scan all areas of the quad and do hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="a7783-148">在四邊形時，這不一定是必要的，因為場景瞭解執行時間會推斷未掃描的四個部分，並使不是表面的區域失效。</span><span class="sxs-lookup"><span data-stu-id="a7783-148">This isn't always necessary with Quads, as the Scene understanding runtime infers which quad areas weren't scanned, and invalidate areas that aren't part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="a7783-149">![已停用推斷的 SceneQuads，可捕獲掃描區域的放置區域。](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="a7783-149">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="a7783-150">**映射 #1** -已停用推斷的 SceneQuads，可捕獲掃描區域的放置區域。</span><span class="sxs-lookup"><span data-stu-id="a7783-150">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="a7783-151">![已啟用推斷的四邊形，放置不再限於掃描的區域。](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="a7783-151">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="a7783-152">**影像 #2** -已啟用推斷的四邊形，放置不再限於掃描的區域。</span><span class="sxs-lookup"><span data-stu-id="a7783-152">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="a7783-153">如果您的應用程式想要在您的環境的固定結構上放置2D 或3D 影像，則最好是從 [空間對應](spatial-mapping.md) 網格計算這項資訊，以方便放置 SceneQuads。</span><span class="sxs-lookup"><span data-stu-id="a7783-153">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="a7783-154">如需本主題的詳細資訊，請參閱 [場景理解 SDK 參考](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span><span class="sxs-lookup"><span data-stu-id="a7783-154">For more information on this topic, see the [Scene understanding SDK reference](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span></span>

<span data-ttu-id="a7783-155">**注意** 若是相依于空間對應網格的舊版放置程式碼，則可以藉由設定 EnableWorldMesh 設定來計算空間對應網格和 SceneQuads。</span><span class="sxs-lookup"><span data-stu-id="a7783-155">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="a7783-156">如果場景理解 API 無法滿足您應用程式的延遲需求，我們建議您繼續使用 [空間對應 api](spatial-mapping.md#placement)。</span><span class="sxs-lookup"><span data-stu-id="a7783-156">If Scene understanding API doesn't satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="a7783-157">遮蔽</span><span class="sxs-lookup"><span data-stu-id="a7783-157">Occlusion</span></span>

<span data-ttu-id="a7783-158">[空間對應遮蔽](spatial-mapping.md#occlusion) 維持環境的即時狀態時，是最不重要的方式。</span><span class="sxs-lookup"><span data-stu-id="a7783-158">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="a7783-159">雖然這可能有助於在高度動態的場景中提供遮蔽，但您可能會想要考慮針對遮蔽的場景瞭解有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="a7783-159">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="a7783-160">如果您使用場景理解所產生的空間對應網格，則可以要求不會儲存在本機快取中且無法從認知 Api 使用的空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="a7783-160">If you use the spatial mapping mesh generated by Scene Understanding, you can request data from spatial mapping that wouldn't be stored in the local cache and isn't available from the perception APIs.</span></span> <span data-ttu-id="a7783-161">使用遮蔽和防水網格的空間對應可提供額外的價值，特別是完成未掃描的空間結構。</span><span class="sxs-lookup"><span data-stu-id="a7783-161">Using Spatial Mapping for occlusion alongside watertight meshes will provide extra value, specifically completion of unscanned room structure.</span></span>

<span data-ttu-id="a7783-162">如果您的需求可容忍場景理解的延遲延遲，應用程式開發人員應該考慮使用場景理解防水網格，以及與平面表示一致的空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="a7783-162">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="a7783-163">這會提供「最棒的」案例，其中簡化的防水遮蔽會使用更精細的 nonplanar 幾何，提供最實際的遮蔽地圖。</span><span class="sxs-lookup"><span data-stu-id="a7783-163">This would provide a "best of both worlds" scenario where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="a7783-164">物理特性</span><span class="sxs-lookup"><span data-stu-id="a7783-164">Physics</span></span>

<span data-ttu-id="a7783-165">場景理解會產生防水網格，以使用語義分解空間，特別是為了解決空間對應網格所強加的物理限制。</span><span class="sxs-lookup"><span data-stu-id="a7783-165">Scene understanding generates watertight meshes that decompose space with semantics, specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="a7783-166">防水結構可確保一律會達到物理光線轉換，而且語義分解可讓您更輕鬆地產生室內導覽的導覽網格。</span><span class="sxs-lookup"><span data-stu-id="a7783-166">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="a7783-167">如 [遮蔽](#occlusion)一節中所述，使用 EnableSceneObjectMeshes 和 EnableWorldMesh 建立場景將會產生最實際的完整網狀。</span><span class="sxs-lookup"><span data-stu-id="a7783-167">As described in the section on [occlusion](#occlusion), creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="a7783-168">環境網格的防水屬性可防止點擊率測試失敗。</span><span class="sxs-lookup"><span data-stu-id="a7783-168">The watertight property of the environment mesh prevents hit tests from failing to hit surfaces.</span></span> <span data-ttu-id="a7783-169">網格資料可確保物理與場景中的所有物件互動，而不只是空間結構。</span><span class="sxs-lookup"><span data-stu-id="a7783-169">The mesh data will ensure physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="a7783-170">導覽</span><span class="sxs-lookup"><span data-stu-id="a7783-170">Navigation</span></span>

<span data-ttu-id="a7783-171">以語義類別分解的平面網格是導覽和路徑規劃的理想結構，可簡化 [空間對應導覽](spatial-mapping.md#navigation) 總覽中所述的許多問題。</span><span class="sxs-lookup"><span data-stu-id="a7783-171">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="a7783-172">在場景中計算的 SceneMesh 物件是由表面型別取消組成，以確保導覽網格產生僅限於可進行的介面。</span><span class="sxs-lookup"><span data-stu-id="a7783-172">The SceneMesh objects computed in the scene are de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="a7783-173">由於地板結構的簡單起見，3d 引擎（例如 Unity）中的動態 nav 網格產生會根據即時需求來實現。</span><span class="sxs-lookup"><span data-stu-id="a7783-173">Because of the floor structures' simplicity, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="a7783-174">產生精確的 nav 網格目前仍需要後置處理，也就是應用程式仍然必須將阻隔器投影至樓層，以確保流覽不會通過雜亂/資料表等等。</span><span class="sxs-lookup"><span data-stu-id="a7783-174">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation doesn't pass through clutter/tables and so on.</span></span> <span data-ttu-id="a7783-175">達成此目的最準確的方法是投射世界網格資料，如果場景是使用 EnableWorldMesh 旗標來計算的，就會提供此資料。</span><span class="sxs-lookup"><span data-stu-id="a7783-175">The most accurate way to accomplish this is to project the world mesh data, which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="a7783-176">視覺效果</span><span class="sxs-lookup"><span data-stu-id="a7783-176">Visualization</span></span>

<span data-ttu-id="a7783-177">雖然 [空間對應視覺效果](spatial-mapping.md#visualization) 可用於環境的即時意見反應，但在許多情況下，平面和防水物件的簡易性可提供更多的效能或視覺品質。</span><span class="sxs-lookup"><span data-stu-id="a7783-177">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="a7783-178">如果投射在四邊形或平面防水網格所提供的平面表面上，使用空間對應所描述的陰影投影和接地技術可能更滿意。</span><span class="sxs-lookup"><span data-stu-id="a7783-178">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="a7783-179">這特別適用于完全預先掃描不適合的環境/案例，因為場景會推斷出，而完整的環境和平面假設會將構件降至最低。</span><span class="sxs-lookup"><span data-stu-id="a7783-179">This is especially true for environments/scenarios where thorough pre-scanning isn't optimal because the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="a7783-180">此外，空間對應所傳回的表面總數會受限於內部空間快取，而場景理解的空間對應網格版本可以存取未快取的空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="a7783-180">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh can access spatial mapping data that isn't cached.</span></span> <span data-ttu-id="a7783-181">因此，場景理解更適合用來針對較大的空間來捕捉網格標記法 (例如，大於單一房間) 來進行視覺效果或進一步的網格處理。</span><span class="sxs-lookup"><span data-stu-id="a7783-181">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="a7783-182">以 EnableWorldMesh 傳回的世界網格會有一致的詳細資料層級，如果轉譯為框線，可能會產生更美觀的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="a7783-182">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="a7783-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7783-183">See Also</span></span>

* [<span data-ttu-id="a7783-184">場景理解 SDK</span><span class="sxs-lookup"><span data-stu-id="a7783-184">Scene understanding SDK</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [<span data-ttu-id="a7783-185">空間對應</span><span class="sxs-lookup"><span data-stu-id="a7783-185">Spatial mapping</span></span>](spatial-mapping.md)