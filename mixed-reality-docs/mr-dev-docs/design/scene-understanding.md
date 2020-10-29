---
title: 場景理解
description: 適用于 HoloLens 的場景理解功能簡介
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 場景理解、空間對應、Windows Mixed Reality、Unity
ms.openlocfilehash: 6185d434b1687675f9ae46313277f61cf6d5e1f8
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679420"
---
# <a name="scene-understanding"></a><span data-ttu-id="d92c6-104">場景理解</span><span class="sxs-lookup"><span data-stu-id="d92c6-104">Scene understanding</span></span>

<span data-ttu-id="d92c6-105">場景理解為混合的現實開發人員提供結構化、高階的環境標記法，其設計目的是為了讓環保感知應用程式的開發變得直覺。</span><span class="sxs-lookup"><span data-stu-id="d92c6-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="d92c6-106">場景理解是藉由結合現有混合現實執行時間的強大功能來達成，例如，高度精確的結構化 [空間對應](spatial-mapping.md) 和新的 AI 驅動執行時間。</span><span class="sxs-lookup"><span data-stu-id="d92c6-106">Scene understanding does this by combining the power of existing mixed reality runtimes, such as the highly accurate less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="d92c6-107">藉由結合這些技術，場景理解會產生3D 環境的標記法，類似于您在 Unity 或 ARKit/ARCore 架構中所使用的環境。</span><span class="sxs-lookup"><span data-stu-id="d92c6-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="d92c6-108">場景理解進入點的開頭是場景觀察器，由您的應用程式呼叫以計算新場景。</span><span class="sxs-lookup"><span data-stu-id="d92c6-108">The Scene understanding entry point begins with a Scene Observer, which is called by your application to compute a new scene.</span></span> <span data-ttu-id="d92c6-109">目前，該技術能夠產生3個相異但相關的物件類別：簡化的防水環境網格，可推斷平面房間結構，而不會有雜亂的平面區域、我們呼叫四邊形的平面區域，以及與我們所呈現之四邊形/防水資料對齊的 [空間對應](spatial-mapping.md) 網格快照。</span><span class="sxs-lookup"><span data-stu-id="d92c6-109">Today, the technology is capable of generating 3 distinct but related object categories: simplified watertight environment meshes that infer the planar room structure without clutter, plane regions for placement that we call Quads, and a snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface.</span></span>

![空間對應網格、標示為平面介面、防水網格](images/SUScenarios.png)

<span data-ttu-id="d92c6-111">本檔的目的是要提供案例總覽，以及說明場景理解和空間對應共用的關聯性。</span><span class="sxs-lookup"><span data-stu-id="d92c6-111">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="d92c6-112">使用場景理解進行開發</span><span class="sxs-lookup"><span data-stu-id="d92c6-112">Developing with Scene Understanding</span></span>

<span data-ttu-id="d92c6-113">本文僅適用于引入場景瞭解執行時間和概念。</span><span class="sxs-lookup"><span data-stu-id="d92c6-113">This article only serves to introduce the Scene Understanding runtime and concepts.</span></span> <span data-ttu-id="d92c6-114">如果您想要瞭解如何使用場景理解進行開發的相關檔，您可能會對下列內容感興趣：</span><span class="sxs-lookup"><span data-stu-id="d92c6-114">If you are looking for documentation on how to develop with Scene Understanding, you may be interested in the following:</span></span>

[<span data-ttu-id="d92c6-115">場景理解 SDK 總覽</span><span class="sxs-lookup"><span data-stu-id="d92c6-115">Scene Understanding SDK overview</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

<span data-ttu-id="d92c6-116">您可以從範例 GitHub 網站下載場景理解範例應用程式：</span><span class="sxs-lookup"><span data-stu-id="d92c6-116">You can download the Scene Understanding Sample app from the sample GitHub site:</span></span>

[<span data-ttu-id="d92c6-117">場景理解範例</span><span class="sxs-lookup"><span data-stu-id="d92c6-117">Scene Understanding Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

<span data-ttu-id="d92c6-118">如果您沒有裝置，而且想要存取範例幕後以嘗試場景理解，則範例資產資料夾中會有場景：</span><span class="sxs-lookup"><span data-stu-id="d92c6-118">If you do not have a device and wish to access sample scenes to try Scene Understanding out, there are scenes in the sample asset folder:</span></span>

[<span data-ttu-id="d92c6-119">場景理解範例場景</span><span class="sxs-lookup"><span data-stu-id="d92c6-119">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a><span data-ttu-id="d92c6-120">SDK</span><span class="sxs-lookup"><span data-stu-id="d92c6-120">SDK</span></span>

<span data-ttu-id="d92c6-121">如果您要尋找有關如何開發以進行場景理解的特定詳細資料，或是場景理解如何運作的詳細資料，以及如何進行開發的詳細資訊，請參閱 [場景理解 SDK 總覽](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 檔。</span><span class="sxs-lookup"><span data-stu-id="d92c6-121">If you are looking for specific details on how to develop for Scene Understanding or details on how Scene understanding works and how to develop for it, see the [Scene Understanding SDK overview](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) documentation.</span></span>


### <a name="sample"></a><span data-ttu-id="d92c6-122">範例</span><span class="sxs-lookup"><span data-stu-id="d92c6-122">Sample</span></span>


## <a name="device-support"></a><span data-ttu-id="d92c6-123">裝置支援</span><span class="sxs-lookup"><span data-stu-id="d92c6-123">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d92c6-124"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="d92c6-124"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d92c6-125"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d92c6-125"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d92c6-126"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d92c6-126"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d92c6-127"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="d92c6-127"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d92c6-128">場景理解</span><span class="sxs-lookup"><span data-stu-id="d92c6-128">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="d92c6-129">✔️</span><span class="sxs-lookup"><span data-stu-id="d92c6-129">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="d92c6-130">常見使用案例</span><span class="sxs-lookup"><span data-stu-id="d92c6-130">Common usage scenarios</span></span>

<span data-ttu-id="d92c6-131">![一般空間對應使用案例的圖例：位置、遮蔽、物理和導覽](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="d92c6-131">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="d92c6-132">*常見的空間對應使用案例：位置、遮蔽、物理和導覽。*</span><span class="sxs-lookup"><span data-stu-id="d92c6-132">*Common spatial mapping usage scenarios: placement, occlusion, physics and navigation.*</span></span>

<br>

<span data-ttu-id="d92c6-133">環境感知應用程式的許多核心案例 (放置、遮蔽、物理等 ) 可透過空間對應和場景理解來定址，本節強調這些差異。</span><span class="sxs-lookup"><span data-stu-id="d92c6-133">Many of the core scenarios for environment aware applications (placement, occlusion, physics, etc.) are addressable by both Spatial mapping and Scene understanding, and this section highlights these differences.</span></span> <span data-ttu-id="d92c6-134">場景理解和空間對應之間的核心差異，在於結構和簡化的最大精確度和延遲的取捨。</span><span class="sxs-lookup"><span data-stu-id="d92c6-134">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="d92c6-135">如果您的應用程式需要最低延遲可能的和只有您想要存取的網格三角形，請直接使用空間對應。</span><span class="sxs-lookup"><span data-stu-id="d92c6-135">If your application requires the lowest-latency possible and mesh triangles that only you will want to access, use Spatial Mapping directly.</span></span> <span data-ttu-id="d92c6-136">如果您要執行較高層級的處理，可以考慮改用場景理解模型，因為它應該會提供您功能的超集合。</span><span class="sxs-lookup"><span data-stu-id="d92c6-136">If you are performing higher level processing, you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="d92c6-137">另請注意，因為場景理解會提供空間對應網格的快照做為其表示的一部分，所以您一律可以存取最完整且正確的空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="d92c6-137">Also note that because Scene understanding provides a snapshot of the spatial mapping mesh as part of its representation, you will always have access to the most complete and accurate spatial mapping data possible.</span></span>

<span data-ttu-id="d92c6-138">下列各節會在新的場景理解 SDK 內容中，重新流覽核心空間對應案例。</span><span class="sxs-lookup"><span data-stu-id="d92c6-138">The following sections re-visit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="d92c6-139">放置</span><span class="sxs-lookup"><span data-stu-id="d92c6-139">Placement</span></span>

<span data-ttu-id="d92c6-140">場景理解提供特別設計來簡化放置案例的新結構。</span><span class="sxs-lookup"><span data-stu-id="d92c6-140">Scene understanding provides new constructs specifically designed to simplify placement scenarios.</span></span> <span data-ttu-id="d92c6-141">場景可以計算稱為 SceneQuads 的基本專案，以描述可放置全像影像的平面表面。</span><span class="sxs-lookup"><span data-stu-id="d92c6-141">A scene can compute primitives called SceneQuads which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="d92c6-142">SceneQuads 特別設計圍繞放置和描述2D 介面，並提供可放置於該介面上的 API。</span><span class="sxs-lookup"><span data-stu-id="d92c6-142">SceneQuads have specifically been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="d92c6-143">先前，使用三角形網格來執行放置時，必須掃描四個部分的所有區域，並執行孔填滿/後置處理，以找出適合物件放置的位置。</span><span class="sxs-lookup"><span data-stu-id="d92c6-143">Previously, when using the triangle mesh to perform placement, one had to scan all areas of the quad and perform hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="d92c6-144">這不一定是四邊形的必要動作，因為場景瞭解執行時間可以推斷未掃描的四個區域，以及使不屬於表面的四個區域失效。</span><span class="sxs-lookup"><span data-stu-id="d92c6-144">This is not always necessary with Quads, as the Scene understanding runtime is capable of inferring which areas of the quad that were not scanned, and invalidate areas of the quad that are not part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d92c6-145">![已停用推斷的 SceneQuads，可捕獲掃描區域的放置區域。](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="d92c6-145">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="d92c6-146">**映射 #1** -已停用推斷的 SceneQuads，可捕獲掃描區域的放置區域。</span><span class="sxs-lookup"><span data-stu-id="d92c6-146">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="d92c6-147">![已啟用推斷的四邊形，放置不再限於掃描的區域。](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="d92c6-147">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="d92c6-148">**影像 #2** -已啟用推斷的四邊形，放置不再限於掃描的區域。</span><span class="sxs-lookup"><span data-stu-id="d92c6-148">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="d92c6-149">如果您的應用程式想要在您的環境的固定結構上放置2D 或3D 影像，則最好是從 [空間對應](spatial-mapping.md) 網格計算這項資訊，以方便放置 SceneQuads。</span><span class="sxs-lookup"><span data-stu-id="d92c6-149">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="d92c6-150">如需本主題的詳細資訊，請參閱 [場景理解 SDK 參考](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span><span class="sxs-lookup"><span data-stu-id="d92c6-150">For more details on this topic, please see the [Scene understanding SDK reference](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span></span>

<span data-ttu-id="d92c6-151">**注意** 若是相依于空間對應網格的舊版放置程式碼，則可以藉由設定 EnableWorldMesh 設定來計算空間對應網格和 SceneQuads。</span><span class="sxs-lookup"><span data-stu-id="d92c6-151">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="d92c6-152">如果場景理解 API 無法滿足您應用程式的延遲需求，我們建議您繼續使用 [空間對應 api](spatial-mapping.md#placement)。</span><span class="sxs-lookup"><span data-stu-id="d92c6-152">If Scene understanding API does not satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="d92c6-153">遮蔽</span><span class="sxs-lookup"><span data-stu-id="d92c6-153">Occlusion</span></span>

<span data-ttu-id="d92c6-154">[空間對應遮蔽](spatial-mapping.md#occlusion) 維持環境的即時狀態時，是最不重要的方式。</span><span class="sxs-lookup"><span data-stu-id="d92c6-154">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="d92c6-155">雖然這可能有助於在高度動態的場景中提供遮蔽，但您可能會想要考慮針對遮蔽的場景瞭解有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="d92c6-155">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="d92c6-156">如果您使用場景理解所產生的空間對應網格，則可以要求不會儲存在本機快取中，因此無法從認知 Api 使用的空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="d92c6-156">If you use the spatial mapping mesh generated by Scene Understanding, you can request data from spatial mapping that would not be stored in the local cache and therefore not available to you from the perception APIs.</span></span> <span data-ttu-id="d92c6-157">使用遮蔽和防水網格的空間對應可提供額外的價值，特別是完成未掃描的空間結構。</span><span class="sxs-lookup"><span data-stu-id="d92c6-157">Using Spatial Mapping for occlusion alongside watertight meshes will provide additional value, specifically completion of un-scanned room structure.</span></span>

<span data-ttu-id="d92c6-158">如果您的需求可容忍場景理解的延遲延遲，應用程式開發人員應該考慮使用場景理解防水網格，而且應有空間對應網格與平面表示一致。</span><span class="sxs-lookup"><span data-stu-id="d92c6-158">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and presumably the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="d92c6-159">這會提供「最棒的」案例，其中簡化的防水遮蔽會使用更精細的 nonplanar 幾何，提供最實際的遮蔽地圖。</span><span class="sxs-lookup"><span data-stu-id="d92c6-159">This would provide a "best of both worlds" scenario where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="d92c6-160">物理特性</span><span class="sxs-lookup"><span data-stu-id="d92c6-160">Physics</span></span>

<span data-ttu-id="d92c6-161">場景理解會產生防水網格，以使用語義分解空間，特別是為了解決空間對應網格所強加的物理限制。</span><span class="sxs-lookup"><span data-stu-id="d92c6-161">Scene understanding generates watertight meshes that decompose space with semantics, specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="d92c6-162">防水結構可確保一律會達到物理光線轉換，而且語義分解可讓您更輕鬆地產生室內導覽的導覽網格。</span><span class="sxs-lookup"><span data-stu-id="d92c6-162">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="d92c6-163">如 [遮蔽](#occlusion)一節中所述，使用 EnableSceneObjectMeshes 和 EnableWorldMesh 建立場景將會產生最實際的完整網狀。</span><span class="sxs-lookup"><span data-stu-id="d92c6-163">As described in the section on [occlusion](#occlusion), creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="d92c6-164">環境網格的 [防水] 屬性會防止點擊率測試失敗，而網格資料可確保物理與場景中的所有物件互動，而不是只與房間結構互動。</span><span class="sxs-lookup"><span data-stu-id="d92c6-164">The watertight property of the environment mesh will prevent hit tests from failing to hit surfaces and the mesh data will ensure that physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="d92c6-165">巡覽</span><span class="sxs-lookup"><span data-stu-id="d92c6-165">Navigation</span></span>

<span data-ttu-id="d92c6-166">以語義類別分解的平面網格是導覽和路徑規劃的理想結構，可簡化 [空間對應導覽](spatial-mapping.md#navigation) 總覽中所述的許多問題。</span><span class="sxs-lookup"><span data-stu-id="d92c6-166">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="d92c6-167">在場景中計算的 SceneMesh 物件已經由介面型別取消組成，以確保 nav 的產生僅限於可進行的表面。</span><span class="sxs-lookup"><span data-stu-id="d92c6-167">The SceneMesh objects computed in the scene are already de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="d92c6-168">由於樓層結構的簡易性，3d 引擎（例如 Unity）中的動態 nav 網狀架構會根據即時需求來實現。</span><span class="sxs-lookup"><span data-stu-id="d92c6-168">Due to the simplicity of the floor structure, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="d92c6-169">產生精確的 nav 網格目前仍需要進行後續處理，也就是應用程式仍然必須將阻隔器投影至樓層，以確保流覽不會通過雜亂/資料表等等。達成此目的最準確的方法，就是在使用 EnableWorldMesh 旗標計算場景時，投射提供的世界網格資料。</span><span class="sxs-lookup"><span data-stu-id="d92c6-169">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation does not pass through clutter/tables etc... The most accurate way to accomplish this is to project the world mesh data which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="d92c6-170">視覺效果</span><span class="sxs-lookup"><span data-stu-id="d92c6-170">Visualization</span></span>

<span data-ttu-id="d92c6-171">雖然 [空間對應視覺效果](spatial-mapping.md#visualization) 可用於環境的即時意見反應，但在許多情況下，平面和防水物件的簡易性可提供更多的效能或視覺品質。</span><span class="sxs-lookup"><span data-stu-id="d92c6-171">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="d92c6-172">如果投射在四邊形或平面防水網格所提供的平面表面上，使用空間對應所描述的陰影投影和接地技術可能更滿意。</span><span class="sxs-lookup"><span data-stu-id="d92c6-172">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="d92c6-173">這特別適用于進行全面掃描的環境/案例，因為場景會推斷出事實，而完成的環境和平面假設會將成品降至最低。</span><span class="sxs-lookup"><span data-stu-id="d92c6-173">This is especially true for environments/scenarios where thorough pre-scanning is not optimal due to the fact that the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="d92c6-174">此外，空間對應所傳回的表面總數會受限於內部空間快取，而場景理解的空間對應網格版本可以存取未快取的空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="d92c6-174">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh is able to access spatial mapping data that is not cached.</span></span> <span data-ttu-id="d92c6-175">因此，場景理解更適合用來針對較大的空間來捕捉網格標記法 (例如，大於單一房間) 來進行視覺效果或進一步的網格處理。</span><span class="sxs-lookup"><span data-stu-id="d92c6-175">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="d92c6-176">以 EnableWorldMesh 傳回的世界網格會有一致的詳細資料層級，如果轉譯為框線，可能會產生更美觀的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="d92c6-176">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="d92c6-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d92c6-177">See Also</span></span>

* [<span data-ttu-id="d92c6-178">場景理解 SDK</span><span class="sxs-lookup"><span data-stu-id="d92c6-178">Scene understanding SDK</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [<span data-ttu-id="d92c6-179">空間對應</span><span class="sxs-lookup"><span data-stu-id="d92c6-179">Spatial mapping</span></span>](spatial-mapping.md)
