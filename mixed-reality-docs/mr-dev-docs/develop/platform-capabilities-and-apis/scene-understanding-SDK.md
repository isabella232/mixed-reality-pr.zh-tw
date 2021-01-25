---
title: 場景理解 SDK
description: 瞭解如何安裝和使用場景理解 SDK，包括混合現實應用程式中的元件、網格和物件。
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: 場景理解、空間對應、Windows Mixed Reality、Unity
ms.openlocfilehash: 748ec444bfcbabb534f391a889fcc16c7671bf7d
ms.sourcegitcommit: 753f0ee94cf86be645cad8efd60f1b43ac529c96
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2021
ms.locfileid: "98758374"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="2e1a1-104">場景理解 SDK 總覽</span><span class="sxs-lookup"><span data-stu-id="2e1a1-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="2e1a1-105">場景理解會轉換混合式現實裝置所捕捉的非結構化環境感應器資料，並將其轉換成強大的抽象標記法。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="2e1a1-106">SDK 會作為應用程式與場景理解執行時間之間的通訊層。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="2e1a1-107">其目的是要模擬現有的標準結構，例如3d 呈現的3D 場景圖形，以及2D 應用程式的2D 矩形和麵板。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="2e1a1-108">雖然結構場景理解模擬會對應到具體的架構，但一般而言，SceneUnderstanding 是架構中立的，可讓與它互動的各種架構之間進行互通性。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="2e1a1-109">隨著場景的理解，發展 SDK 的角色是為了確保新的表示和功能能持續在統一架構中公開。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="2e1a1-110">在本檔中，我們會先介紹高階的概念，以協助您熟悉開發環境/使用方式，然後針對特定類別和結構提供更詳細的檔。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="2e1a1-111">哪裡可以取得 SDK？</span><span class="sxs-lookup"><span data-stu-id="2e1a1-111">Where do I get the SDK?</span></span>

<span data-ttu-id="2e1a1-112">您可以透過 NuGet 下載 SceneUnderstanding SDK。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="2e1a1-113">SceneUnderstanding SDK</span><span class="sxs-lookup"><span data-stu-id="2e1a1-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="2e1a1-114">**注意：** 最新版本取決於預覽套件，您將需要啟用發行前版本的套件才能看到它。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-114">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="2e1a1-115">針對 0.5.2022 rc 和更新版本，場景理解支援 c # 和 c + + 的語言投影，讓應用程式開發 Win32 或 UWP 平臺的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-115">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="2e1a1-116">從這個版本開始，SceneUnderstanding 支援支援 unity 的編輯器支援，而禁止使用 SceneObserver，這僅用於與 HoloLens2 通訊。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="2e1a1-117">SceneUnderstanding 需要 Windows SDK 18362 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="2e1a1-118">如果您是在 Unity 專案中使用 SDK，請使用 [適用于 unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity) 將套件安裝到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-118">If you're using the SDK in a Unity project, use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="2e1a1-119">概觀說明</span><span class="sxs-lookup"><span data-stu-id="2e1a1-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="2e1a1-120">場景</span><span class="sxs-lookup"><span data-stu-id="2e1a1-120">The Scene</span></span>

<span data-ttu-id="2e1a1-121">您的混合現實裝置會不斷地整合在您的環境中所看到內容的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="2e1a1-122">場景理解會漏斗圖所有的資料來源，並產生單一的緊密抽象概念。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="2e1a1-123">場景理解會產生場景，也就是代表單一事物之實例的 [SceneObjects](scene-understanding-SDK.md#sceneobjects) 組合， (例如牆壁/上限/樓層。 ) 場景物件本身是 [SceneComponents 的組合，代表組成此 SceneObject 的更細微部分。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-123">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="2e1a1-124">元件的範例包括四邊形和網格，但未來可能代表周框方塊、衝突網格、中繼資料等。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="2e1a1-125">將未經處理的感應器資料轉換為場景的程式，可能會花費幾秒鐘的中等空間 (~ 10x10m) 到數分鐘的空間 (~ 50x50m) ，因此不會由沒有應用程式要求的裝置所計算的內容。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="2e1a1-126">相反地，您的應用程式會視需要觸發場景產生。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="2e1a1-127">SceneObserver 類別具有可計算或還原序列化場景的靜態方法，您可以接著列舉/與其互動。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="2e1a1-128">「計算」動作會依需求執行，並在 CPU 上執行，但在混合現實驅動程式)  (的個別進程中執行。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="2e1a1-129">不過，當我們在另一個進程中進行計算時，產生的場景資料會儲存在您的應用程式中，並保留在場景物件中。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="2e1a1-130">以下圖表說明此程式流程，並顯示兩個應用程式與場景理解執行時間互動的範例。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![處理圖表](images/SU-ProcessFlow.png)

<span data-ttu-id="2e1a1-132">左側是混合現實執行時間的圖表，它會在自己的進程中保持開啟並執行。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-132">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="2e1a1-133">此執行時間負責執行裝置追蹤、空間對應，以及場景理解用來瞭解與世界周圍相關原因的其他作業。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="2e1a1-134">在圖表的右側，我們會顯示兩個理論上的應用程式，利用場景理解。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="2e1a1-135">第一個應用程式是使用 MRTK 的介面，它會在內部使用場景理解 SDK，第二個應用程式會計算並使用兩個不同的場景實例。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-135">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="2e1a1-136">此圖表中的三個場景都會產生不同的場景實例，驅動程式不會追蹤在不同場景中的應用程式與場景物件之間共用的全域狀態。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-136">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="2e1a1-137">場景理解確實提供了一段時間的追蹤機制，但這是使用 SDK 來完成的。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="2e1a1-138">在應用程式的程式中，追蹤程式碼已經在 SDK 中執行。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-138">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="2e1a1-139">因為每個場景會將它的資料儲存在您應用程式的記憶體空間中，所以您可以假設場景物件的所有功能或其內部資料一律會在應用程式的進程中執行。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-139">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="2e1a1-140">Layout</span><span class="sxs-lookup"><span data-stu-id="2e1a1-140">Layout</span></span>

<span data-ttu-id="2e1a1-141">若要使用場景理解，瞭解並瞭解執行時間如何以邏輯和實際方式代表元件，可能會有價值。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-141">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="2e1a1-142">場景代表具有特定版面配置的資料，並在維持 pliable 的基礎結構，而不需要進行重大修訂時，才會維持符合未來需求的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-142">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="2e1a1-143">場景會藉由儲存所有元件， (一般清單中) 的所有場景物件的所有元件，並透過參考（特定元件參考其他元件）定義階層和組合。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-143">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="2e1a1-144">以下範例顯示其平面和邏輯形式的結構範例。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-144">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="2e1a1-145">邏輯版面配置</span><span class="sxs-lookup"><span data-stu-id="2e1a1-145">Logical Layout</span></span></th><th><span data-ttu-id="2e1a1-146">實體配置</span><span class="sxs-lookup"><span data-stu-id="2e1a1-146">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="2e1a1-147">場景</span><span class="sxs-lookup"><span data-stu-id="2e1a1-147">Scene</span></span>
  <ul>
  <li><span data-ttu-id="2e1a1-148">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="2e1a1-148">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="2e1a1-149">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="2e1a1-149">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="2e1a1-150">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="2e1a1-150">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="2e1a1-151">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="2e1a1-151">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="2e1a1-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="2e1a1-152">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="2e1a1-153">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="2e1a1-153">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="2e1a1-154">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="2e1a1-154">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="2e1a1-155">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="2e1a1-155">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="2e1a1-156">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="2e1a1-156">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="2e1a1-157">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="2e1a1-157">SceneObject_1</span></span></li>
  <li><span data-ttu-id="2e1a1-158">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="2e1a1-158">SceneObject_2</span></span></li>
  <li><span data-ttu-id="2e1a1-159">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="2e1a1-159">SceneObject_3</span></span></li>
  <li><span data-ttu-id="2e1a1-160">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="2e1a1-160">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="2e1a1-161">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="2e1a1-161">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="2e1a1-162">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="2e1a1-162">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="2e1a1-163">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="2e1a1-163">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="2e1a1-164">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="2e1a1-164">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="2e1a1-165">下圖強調場景的實體和邏輯配置之間的差異。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-165">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="2e1a1-166">在左側，我們會看到您的應用程式在列舉場景時所看到的資料的階層式版面配置。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-166">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="2e1a1-167">在右側，我們看到場景是由12個不同的元件所組成，視需要個別存取。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-167">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="2e1a1-168">在處理新的場景時，我們預期應用程式會以邏輯方式來引導此階層，不過在場景更新之間進行追蹤時，有些應用程式可能只會對以兩種場景間共用的特定元件為目標感興趣。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-168">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="2e1a1-169">API 概觀</span><span class="sxs-lookup"><span data-stu-id="2e1a1-169">API overview</span></span>

<span data-ttu-id="2e1a1-170">下一節提供場景理解中的結構高階總覽。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-170">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="2e1a1-171">閱讀此區段可讓您瞭解幕後的呈現方式，以及各種元件的用途/用途。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-171">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="2e1a1-172">下一節將提供具體的程式碼範例，以及在此總覽中說明 mda 的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-172">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="2e1a1-173">以下所述的所有類型都位於 `Microsoft.MixedReality.SceneUnderstanding` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-173">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="2e1a1-174">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="2e1a1-174">SceneComponents</span></span>

<span data-ttu-id="2e1a1-175">現在您已瞭解幕後的邏輯配置，我們現在可以展示 SceneComponents 的概念，以及如何使用它們來撰寫階層。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-175">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="2e1a1-176">SceneComponents 是 SceneUnderstanding 中最細微的分解，代表單一核心事物，例如網格或四或周框方塊。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-176">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="2e1a1-177">SceneComponents 是可獨立更新，並且可由其他 SceneComponents 參考的專案，因此它們具有唯一識別碼的單一全域屬性，可允許這種類型的追蹤/參考機制。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-177">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="2e1a1-178">識別碼會用於場景階層的邏輯組合以及物件持續性， (與另一個場景相關的更新動作。 ) </span><span class="sxs-lookup"><span data-stu-id="2e1a1-178">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="2e1a1-179">如果您要將每個新計算的場景視為相異，只要列舉其中的所有資料，則識別碼對您而言都很透明。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-179">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="2e1a1-180">但是，如果您打算追蹤數個更新的元件，您將會使用這些識別碼來編制索引，並尋找場景物件之間的 SceneComponents。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-180">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="2e1a1-181">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="2e1a1-181">SceneObjects</span></span>

<span data-ttu-id="2e1a1-182">SceneObject 是一種 SceneComponent，代表「事物」的實例，例如牆、樓層、頂棚等等。以其 Kind 屬性工作表示。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-182">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="2e1a1-183">SceneObjects 是幾何，因此具有代表其在空間中位置的函式和屬性，但不包含任何幾何或邏輯結構。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-183">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="2e1a1-184">相反地，SceneObjects 會參考其他 SceneComponents，特別是 SceneQuads 和 SceneMeshes，以提供系統所支援的各種不同標記法。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-184">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="2e1a1-185">當計算新場景時，您的應用程式很可能會列舉場景的 SceneObjects 來處理其感興趣的內容。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-185">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="2e1a1-186">SceneObjects 可以有下列任何一項：</span><span class="sxs-lookup"><span data-stu-id="2e1a1-186">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="2e1a1-187">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="2e1a1-187">SceneObjectKind</span></span></th> <th><span data-ttu-id="2e1a1-188">描述</span><span class="sxs-lookup"><span data-stu-id="2e1a1-188">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="2e1a1-189">背景</span><span class="sxs-lookup"><span data-stu-id="2e1a1-189">Background</span></span></td><td><span data-ttu-id="2e1a1-190">已知 SceneObject <b>不</b> 是其他可辨識的場景物件類型之一。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-190">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="2e1a1-191">此類別不應與未知的情況混淆，因為背景已知不是牆壁/樓層/上限等 .。。雖然不明尚未分類。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-191">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="2e1a1-192">牆</span><span class="sxs-lookup"><span data-stu-id="2e1a1-192">Wall</span></span></td><td><span data-ttu-id="2e1a1-193">實體牆。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-193">A physical wall.</span></span> <span data-ttu-id="2e1a1-194">牆會假設為 immovable 環境結構。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-194">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="2e1a1-195">樓層</span><span class="sxs-lookup"><span data-stu-id="2e1a1-195">Floor</span></span></td><td><span data-ttu-id="2e1a1-196">樓層是任何可進行引導的表面。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-196">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="2e1a1-197">注意：階梯並非樓層。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-197">Note: stairs aren't floors.</span></span> <span data-ttu-id="2e1a1-198">另請注意，該樓層採用任何 walkable 介面，因此不會明確地假設單數地板。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-198">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="2e1a1-199">多層結構、斜坡等 .。。全都分類為 floor。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-199">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="2e1a1-200">Ceiling</span><span class="sxs-lookup"><span data-stu-id="2e1a1-200">Ceiling</span></span></td><td><span data-ttu-id="2e1a1-201">房間的上方面。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-201">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="2e1a1-202">平台</span><span class="sxs-lookup"><span data-stu-id="2e1a1-202">Platform</span></span></td><td><span data-ttu-id="2e1a1-203">您可以用來放置全息圖的大型平面。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-203">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="2e1a1-204">這些通常會代表資料表、countertops 和其他大型水準表面。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-204">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="2e1a1-205">World</span><span class="sxs-lookup"><span data-stu-id="2e1a1-205">World</span></span></td><td><span data-ttu-id="2e1a1-206">標記無關的幾何資料保留標籤。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-206">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="2e1a1-207">藉由設定 EnableWorldMesh 更新旗標所產生的網格會分類為 world。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-207">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="2e1a1-208">Unknown</span><span class="sxs-lookup"><span data-stu-id="2e1a1-208">Unknown</span></span></td><td><span data-ttu-id="2e1a1-209">這個場景物件尚未分類並指派給類型。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-209">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="2e1a1-210">這應該不會與背景混淆，因為此物件可能是任何事情，因此系統還不會為它提供強大的分類。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-210">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="2e1a1-211">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="2e1a1-211">SceneMesh</span></span>

<span data-ttu-id="2e1a1-212">SceneMesh 是一個 SceneComponent，使用三角形清單來近似任意幾何物件的幾何。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-212">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="2e1a1-213">SceneMeshes 會在數個不同的內容中使用，它們可以代表防水資料格結構的元件或 WorldMesh，代表與場景相關聯的未系結空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-213">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="2e1a1-214">每個網格所提供的索引和頂點資料，會使用與用來呈現所有新式轉譯 Api 中三角形網格的 [頂點和索引緩衝區](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) 相同的熟悉版面配置。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-214">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="2e1a1-215">在場景理解中，網格會使用32位的索引，而且可能需要針對某些轉譯引擎分割成區塊。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-215">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="2e1a1-216">纏繞順序和座標系統</span><span class="sxs-lookup"><span data-stu-id="2e1a1-216">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="2e1a1-217">場景理解所產生的所有網格都應該使用順向的纏繞順序，在 Right-Handed 座標系統中傳回網格。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-217">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="2e1a1-218">注意：在191105之前的 OS 組建可能會有已知的錯誤，其中「世界」網格以 Counter-Clockwise 的纏繞順序傳回，這會在之後修正。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-218">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="2e1a1-219">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="2e1a1-219">SceneQuad</span></span>

<span data-ttu-id="2e1a1-220">SceneQuad 是代表佔用3d 世界之2d 表面的 SceneComponent。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-220">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="2e1a1-221">SceneQuads 的使用方式類似于 ARKit ARPlaneAnchor 或 ARCore 平面，但它們提供了更高階的功能，像是一般應用程式使用的2d 畫布或增強的 UX。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-221">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="2e1a1-222">提供2D 特定 Api 供四邊形使用，讓放置和版面配置便於使用，並開發 (但使用四邊形轉譯) 的例外狀況，應該會比較類似于使用2d 畫布來處理3d 網格。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-222">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="2e1a1-223">SceneQuad 圖形</span><span class="sxs-lookup"><span data-stu-id="2e1a1-223">SceneQuad shape</span></span>

<span data-ttu-id="2e1a1-224">SceneQuads 在2d 中定義界限矩形介面。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-224">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="2e1a1-225">不過，SceneQuads 代表具有任意且可能複雜圖形 (例如環圈圖的圖形 ) 。若要代表四顆環的複雜圖形，您可以使用 GetSurfaceMask API 將介面的形狀轉譯至您提供的影像緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-225">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="2e1a1-226">如果具有四個的 SceneObject 也有網格，則網格三角形應該相當於這個呈現的影像，它們都代表介面的真實幾何，不論是2d 或3d 座標。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-226">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="2e1a1-227">場景理解 SDK 詳細資料和參考</span><span class="sxs-lookup"><span data-stu-id="2e1a1-227">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="2e1a1-228">下一節將協助您熟悉 SceneUnderstanding 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="2e1a1-229">本節應提供您基本概念，此時您應該有足夠的內容可流覽範例應用程式，以瞭解如何使用 SceneUnderstanding 全面性地型。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="2e1a1-230">初始化</span><span class="sxs-lookup"><span data-stu-id="2e1a1-230">Initialization</span></span>

<span data-ttu-id="2e1a1-231">使用 SceneUnderstanding 的第一個步驟是讓您的應用程式取得場景物件的參考。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="2e1a1-232">這可以透過兩種方式之一來完成，而場景可以由驅動程式計算，也可以取消序列化先前計算的現有場景。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="2e1a1-233">後者適用于在開發期間使用 SceneUnderstanding，其中應用程式和體驗可在沒有混合現實裝置的情況下快速建立原型。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="2e1a1-234">場景是使用 SceneObserver 來計算。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="2e1a1-235">建立場景之前，您的應用程式應該查詢您的裝置，以確保它支援 SceneUnderstanding，以及要求使用者存取 SceneUnderstanding 需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="2e1a1-236">如果未呼叫 RequestAccessAsync ( # A1，則計算新場景將會失敗。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="2e1a1-237">接下來，我們將計算以混合現實耳機為基礎的新場景，並擁有10計量的半徑。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="2e1a1-238">從資料初始化 (也稱為。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="2e1a1-239">電腦路徑) </span><span class="sxs-lookup"><span data-stu-id="2e1a1-239">the PC Path)</span></span>

<span data-ttu-id="2e1a1-240">雖然可以計算場景以進行直接取用，但也可以使用序列化形式來計算，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="2e1a1-241">這已證明適用于開發，因為它可讓開發人員在不需要裝置的情況下工作並測試場景理解。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="2e1a1-242">將場景序列化的動作與計算場景幾乎完全相同，而是將資料傳回到您的應用程式，而不是由 SDK 在本機還原序列化。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="2e1a1-243">您可以自行將其還原序列化，或將其儲存供日後使用。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-243">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="2e1a1-244">SceneObject 列舉</span><span class="sxs-lookup"><span data-stu-id="2e1a1-244">SceneObject Enumeration</span></span>

<span data-ttu-id="2e1a1-245">既然您的應用程式有場景，您的應用程式將會查看 SceneObjects 並與之互動。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="2e1a1-246">這是透過存取 **SceneObjects** 屬性來完成的：</span><span class="sxs-lookup"><span data-stu-id="2e1a1-246">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="2e1a1-247">元件更新和 refinding 元件</span><span class="sxs-lookup"><span data-stu-id="2e1a1-247">Component update and refinding components</span></span>

<span data-ttu-id="2e1a1-248">另外還有另一個函式可在場景中抓取元件，稱為 \**_sys.application.findcomponent_* _。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-248">There's another function that retrieves components in the Scene called \**_FindComponent_* _.</span></span> <span data-ttu-id="2e1a1-249">當更新追蹤物件，並在稍後的場景中尋找時，此函式很有用。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="2e1a1-250">下列程式碼會計算相對於前一個場景的新場景，然後在新場景中找出樓層。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="2e1a1-251">從場景物件存取網格和四邊形</span><span class="sxs-lookup"><span data-stu-id="2e1a1-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="2e1a1-252">一旦找到 SceneObjects，您的應用程式很可能會想要存取其所組成之四邊形/網格中所包含的資料。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="2e1a1-253">這項資料是使用 _\*_四邊形_\*_ 和 _\*_網格_\*_ 屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-253">This data is accessed with the _*_Quads_*_ and _*_Meshes_*_ properties.</span></span> <span data-ttu-id="2e1a1-254">下列程式碼將列舉 floor 物件的所有四邊形和網格。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="2e1a1-255">請注意，它是具有相對於場景原點之轉換的 SceneObject。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="2e1a1-256">這是因為 SceneObject 代表「東西」的實例，並可在空間中加以定位、四邊形和網格表示相對於其父系的轉換幾何。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="2e1a1-257">不同的 SceneObjects 可以參考相同的 SceneMesh/SceneQuad SceneComponents，也有可能是 SceneObject 有一個以上的 SceneMesh/SceneQuad。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="2e1a1-258">處理轉換</span><span class="sxs-lookup"><span data-stu-id="2e1a1-258">Dealing with Transforms</span></span>

<span data-ttu-id="2e1a1-259">在處理轉換時，場景理解已刻意嘗試配合傳統的3D 場景標記法。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="2e1a1-260">因此，每個場景會限制為單一座標系統，就像是最常見的3D 環境表示一樣。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="2e1a1-261">SceneObjects 每個都提供其相對於座標系統的位置。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="2e1a1-262">如果您的應用程式處理的場景會延展單一來源提供的限制，讓它可以將 SceneObjects 錨定到 SpatialAnchors，或是產生數個場景並將它們合併在一起，但為了簡單起見，我們假設防水場景存在於自己的原點，並由場景所定義的一個來當地語系化。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="2e1a1-263">例如，下列 Unity 程式碼示範如何使用 Windows 感知和 Unity Api 來調整座標系統的組合。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="2e1a1-264">如需有關取得與 Unity 世界原點對應之 SpatialCoordinateSystem 的詳細資訊，請參閱 [SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem) 和 [SpatialGraphInteropPreview](//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) ，以取得有關 Windows 認知 api 的詳細資料，以及 [Unity 中的混合現實原生物件](//windows/mixed-reality/unity-xrdevice-advanced) 。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-264">See [SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

<span data-ttu-id="2e1a1-265">每個都 `SceneObject` 有轉換，然後套用至該物件。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="2e1a1-266">在 Unity 中，我們轉換為右手座標，並將本機轉換指派為：</span><span class="sxs-lookup"><span data-stu-id="2e1a1-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a><span data-ttu-id="2e1a1-267">四</span><span class="sxs-lookup"><span data-stu-id="2e1a1-267">Quad</span></span>

<span data-ttu-id="2e1a1-268">四邊形的設計目的是要協助2D 放置案例，而且應該將其視為2D 畫布 UX 元素的延伸。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="2e1a1-269">雖然四邊形是 SceneObjects 的元件，而且可以在3D 中轉譯，但四個 Api 本身會假設四邊形是2D 結構。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="2e1a1-270">它們提供的資訊包括範圍、圖形，以及提供用於放置的 Api。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="2e1a1-271">四邊形具有矩形範圍，但代表任意成形的2D 表面。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="2e1a1-272">若要啟用與3D 環境互動之2D 表面上的放置，四邊形提供公用程式以實現這種互動。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="2e1a1-273">目前的場景理解提供兩種這類功能： _ *FindCentermostPlacement*\* 和 **GetSurfaceMask**。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-273">Currently Scene Understanding provides two such functions, _ *FindCentermostPlacement*\* and **GetSurfaceMask**.</span></span> <span data-ttu-id="2e1a1-274">FindCentermostPlacement 是高階 API，可找出四個位置上可放置物件的位置，並且會嘗試找出您的物件的最佳位置，以確保您提供的周框方塊會留在基礎介面上。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="2e1a1-275">輸出的座標相對於「四個空間」中的四個十字，左上角的 (x = 0，y = 0) ，就如同其他 windows Rect 類型一樣。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="2e1a1-276">使用您自己的物件的來源時，請務必將此納入考慮。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="2e1a1-277">下列範例示範如何尋找 centermost 可放置位置，並將全像點放置在四個位置。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="2e1a1-278">步驟1-4 高度取決於您的特定架構/執行，但主題應該類似。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="2e1a1-279">有一點要注意的是，四個只代表在空間中當地語系化的界限2D 平面。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="2e1a1-280">藉由讓您的引擎/架構知道四個部分，並將您的物件與四個實體相對應，您的全像是會正確地找出與真實世界相關的您的全像。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="2e1a1-281">網狀</span><span class="sxs-lookup"><span data-stu-id="2e1a1-281">Mesh</span></span>

<span data-ttu-id="2e1a1-282">網格代表物件或環境的幾何標記法。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="2e1a1-283">與 [空間對應](../../design/spatial-mapping.md)、網格索引和每個空間介面網格所提供的頂點資料非常類似，其使用的是與用來呈現所有新式轉譯 api 中三角形網格的頂點和索引緩衝區相同的熟悉版面配置。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="2e1a1-284">頂點位置是在的座標系統中提供 `Scene` 。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="2e1a1-285">用來參考此資料的特定 Api 如下：</span><span class="sxs-lookup"><span data-stu-id="2e1a1-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="2e1a1-286">下列程式碼提供從網格結構產生三角形清單的範例：</span><span class="sxs-lookup"><span data-stu-id="2e1a1-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="2e1a1-287">索引/頂點緩衝區必須 >= 索引/頂點計數，但也可以任意調整大小，以便有效率地重複使用記憶體。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="2e1a1-288">ColliderMesh</span><span class="sxs-lookup"><span data-stu-id="2e1a1-288">ColliderMesh</span></span>

<span data-ttu-id="2e1a1-289">場景物件可透過 [網格] 和 [ColliderMeshes] 屬性，提供網格和碰撞的網格資料存取。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="2e1a1-290">這些網格一律會相符，這表示網格屬性的 i'th 索引代表與 ColliderMeshes 屬性的 i'th 索引相同的幾何。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="2e1a1-291">如果執行時間/物件支援碰撞器網格，則在您的應用程式使用 colliders 的任何地方，都可保證您取得最小的多邊形、最高的順序近似值，以及使用 ColliderMeshes 的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="2e1a1-292">如果系統不支援 colliders，則在 ColliderMeshes 中傳回的網格物件將會是與網格減少記憶體限制相同的物件。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="2e1a1-293">使用場景理解進行開發</span><span class="sxs-lookup"><span data-stu-id="2e1a1-293">Developing with scene understanding</span></span>

<span data-ttu-id="2e1a1-294">至此，您應該瞭解場景瞭解執行時間和 SDK 的核心構成要素。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="2e1a1-295">大部分的電源和複雜性都是存取模式、與3D 架構的互動，以及可以撰寫在這些 Api 之上的工具，以進行空間規劃、房間分析、流覽、物理等等等更先進的工作。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="2e1a1-296">我們希望在範例中抓住這些範例，建議您以適當的方向引導您的案例。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="2e1a1-297">如果有未解決的範例或案例，請讓我們知道，我們會嘗試記錄/原型您所需的內容。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="2e1a1-298">我可以在哪裡取得範例程式碼？</span><span class="sxs-lookup"><span data-stu-id="2e1a1-298">Where can I get sample code?</span></span>

<span data-ttu-id="2e1a1-299">適用于 Unity 的場景理解範例程式碼可以在我們的 [Unity 範例頁面](https://github.com/sceneunderstanding-microsoft/unitysample) 頁面上找到。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="2e1a1-300">此應用程式可讓您與您的裝置通訊並轉譯各種場景物件，或者，它可讓您在電腦上載入已序列化的場景，並讓您在沒有裝置的情況下體驗到場景的理解。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="2e1a1-301">我可以在哪裡取得範例場景？</span><span class="sxs-lookup"><span data-stu-id="2e1a1-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="2e1a1-302">如果您有 HoloLens2，可以將 ComputeSerializedAsync 的輸出儲存至檔案，並在您自己的方便的情況下還原序列化，以儲存您所捕獲的任何場景。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="2e1a1-303">如果您沒有 HoloLens2 裝置，但想要在場景理解的情況下播放，您必須下載預先捕捉的場景。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="2e1a1-304">場景理解範例目前隨附的序列化場景，可供您自行下載及使用。</span><span class="sxs-lookup"><span data-stu-id="2e1a1-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="2e1a1-305">您可以在這裡找到：</span><span class="sxs-lookup"><span data-stu-id="2e1a1-305">You can find them here:</span></span>

[<span data-ttu-id="2e1a1-306">場景理解範例場景</span><span class="sxs-lookup"><span data-stu-id="2e1a1-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a><span data-ttu-id="2e1a1-307">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e1a1-307">See also</span></span>

* [<span data-ttu-id="2e1a1-308">空間對應</span><span class="sxs-lookup"><span data-stu-id="2e1a1-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="2e1a1-309">場景理解</span><span class="sxs-lookup"><span data-stu-id="2e1a1-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="2e1a1-310">Unity 範例</span><span class="sxs-lookup"><span data-stu-id="2e1a1-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)