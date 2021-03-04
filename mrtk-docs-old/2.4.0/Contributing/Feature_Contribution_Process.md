---
title: Feature_Contribution_Process
description: 將功能新增至 MRTK 的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: da91e42abe39ced0939e328f340e6340b8b1d9d9
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780669"
---
# <a name="feature-contribution-process"></a><span data-ttu-id="cecd9-104">功能貢獻流程</span><span class="sxs-lookup"><span data-stu-id="cecd9-104">Feature contribution process</span></span>

> [!WARNING]
> <span data-ttu-id="cecd9-105">10/1/2019：此頁面已被取代，因為它提供在2.0 版之前讓大型系統 MRTK 的指導方針。</span><span class="sxs-lookup"><span data-stu-id="cecd9-105">10/1/2019: This page is deprecated because it provides guidelines for contributing very large systems to MRTK before the 2.0 release.</span></span> <span data-ttu-id="cecd9-106">在2.0 版本之後，需要更仔細地執行大型變更，但尚未決定這項處理常式。</span><span class="sxs-lookup"><span data-stu-id="cecd9-106">After the 2.0 release, large changes need to be performed more carefully, and the process for this is not yet decided.</span></span> <span data-ttu-id="cecd9-107">我們預期大部分的 MRTK 貢獻都有較小的變更，而不是此處所涵蓋的變更。</span><span class="sxs-lookup"><span data-stu-id="cecd9-107">We expect most MRTK contributions to have much smaller changes than what is covered here.</span></span>

<span data-ttu-id="cecd9-108">將功能加入至混合現實工具組 (MRTK) 會分割成幾個反復專案步驟，因此維護人員可以有時間進行審核，並確保程式能順利執行。</span><span class="sxs-lookup"><span data-stu-id="cecd9-108">Adding features to the Mixed Reality Toolkit (MRTK) is split up into a few iteration steps, so maintainers can have time to review and and ensure the process goes smoothly.</span></span> <span data-ttu-id="cecd9-109">開始之前，請務必先檢查 [功能需求](#new-feature-requirements) 的清單。</span><span class="sxs-lookup"><span data-stu-id="cecd9-109">Please be sure to review the list of [feature requirements](#new-feature-requirements) before you get started.</span></span>

## <a name="process"></a><span data-ttu-id="cecd9-110">處理序</span><span class="sxs-lookup"><span data-stu-id="cecd9-110">Process</span></span>

<span data-ttu-id="cecd9-111">下列程式已經過草擬，可確保所有新的工作符合針對 MRTK 所定義的更新標準和架構，這已定義為：</span><span class="sxs-lookup"><span data-stu-id="cecd9-111">The following process has been drafted to ensure all new work complies to the updated standards and architecture defined for the MRTK, this has been defined as:</span></span>

1. [<span data-ttu-id="cecd9-112">開啟新的提案和相關工作</span><span class="sxs-lookup"><span data-stu-id="cecd9-112">Open a new Proposal and related Tasks</span></span>](#new-proposal)
2. [<span data-ttu-id="cecd9-113">提交架構草稿或大綱</span><span class="sxs-lookup"><span data-stu-id="cecd9-113">Submit an Architecture Draft or Outline</span></span>](#architecture-draft)
3. [<span data-ttu-id="cecd9-114">複習並完成架構檔</span><span class="sxs-lookup"><span data-stu-id="cecd9-114">Review and finalize the Architecture documentation</span></span>](#architecture-documentation)
4. [<span data-ttu-id="cecd9-115">提交 PR，以執行核心功能介面和事件基準 (（如果適用）) </span><span class="sxs-lookup"><span data-stu-id="cecd9-115">Submit a PR implementing the Core feature interfaces and event datum (if applicable)</span></span>](#core-implementation)
5. [<span data-ttu-id="cecd9-116">提交執行任何必要 SDK 元件的 PR</span><span class="sxs-lookup"><span data-stu-id="cecd9-116">Submit a PR Implementing any required SDK components</span></span>](#sdk-implementation)
6. [<span data-ttu-id="cecd9-117">提交 PR 實行功能示範或完整調整範例</span><span class="sxs-lookup"><span data-stu-id="cecd9-117">Submit a PR Implementing feature demos or full scale Examples</span></span>](#example-implementation)

### <a name="new-proposal"></a><span data-ttu-id="cecd9-118">新提案</span><span class="sxs-lookup"><span data-stu-id="cecd9-118">New proposal</span></span>

<span data-ttu-id="cecd9-119">首先，開啟新的提案或工作，以描述您想要解決的功能或問題。</span><span class="sxs-lookup"><span data-stu-id="cecd9-119">Start by opening a new Proposal or Task describing the feature or the problem you want to solve.</span></span> <span data-ttu-id="cecd9-120">描述方法，以及如何將它融入您所設為目標的混合現實工具組版本。</span><span class="sxs-lookup"><span data-stu-id="cecd9-120">Describe the approach and how it fits into the version of the Mixed Reality Toolkit you're targeting.</span></span> <span data-ttu-id="cecd9-121">這可讓每個人都有關于提案的討論，並希望在任何工作開始之前識別一些潛在的陷阱。</span><span class="sxs-lookup"><span data-stu-id="cecd9-121">This will enable everyone have a discussion about the proposal and, hopefully, identify some potential pitfalls before any work is started.</span></span>

<span data-ttu-id="cecd9-122">新提案會在每週寄送會議室會議期間進行審核及討論，而如果接受提案，則會建立並指派補充工作。</span><span class="sxs-lookup"><span data-stu-id="cecd9-122">New Proposals will be reviewed and discussed during our weekly ship room meetings and if a proposal is accepted, supplemental tasks will then be created and assigned.</span></span>

### <a name="architecture-draft"></a><span data-ttu-id="cecd9-123">架構草稿</span><span class="sxs-lookup"><span data-stu-id="cecd9-123">Architecture draft</span></span>

<span data-ttu-id="cecd9-124">第一項工作是在第一次接受初始提案之後，將會針對要完成的功能或工作，草擬初始的架構檔。</span><span class="sxs-lookup"><span data-stu-id="cecd9-124">The first task once the initial proposal has been accepted, will be to draft the initial architecture document for the feature or work to be done.</span></span> <span data-ttu-id="cecd9-125">這份檔通常應該是一或兩頁頁面，其中包含功能的高階總覽，以及與混合現實工具組其他部分的關聯性。</span><span class="sxs-lookup"><span data-stu-id="cecd9-125">This document should typically be one or two pages long and include a high level overview of the feature and how it will relate to other parts of the Mixed Reality Toolkit.</span></span>

* <span data-ttu-id="cecd9-126">草稿必須很容易使用，並醒目提示重要區域。</span><span class="sxs-lookup"><span data-stu-id="cecd9-126">The draft must be easy to consume with key areas highlighted.</span></span>
* <span data-ttu-id="cecd9-127">草稿必須包含建議的核心介面、設定設定檔和事件基準的清單。</span><span class="sxs-lookup"><span data-stu-id="cecd9-127">The draft must include a list of the proposed core interfaces, configuration profiles, and event datum.</span></span>
* <span data-ttu-id="cecd9-128">草稿必須包含建議架構的簡單圖形。</span><span class="sxs-lookup"><span data-stu-id="cecd9-128">The draft must include a simple graphic of the proposed architecture.</span></span>

<span data-ttu-id="cecd9-129">確定功能的架構符合核心 MRTK 架構所設定的 [新功能需求](#new-feature-requirements) 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-129">Ensure that the architecture of the feature complies with the [New Feature Requirements](#new-feature-requirements) set out by the Core MRTK architecture.</span></span>

><span data-ttu-id="cecd9-130">TODO：新增架構草稿範本的連結</span><span class="sxs-lookup"><span data-stu-id="cecd9-130">TODO: Add link to architecture draft template</span></span>

<span data-ttu-id="cecd9-131">完成草稿之後，您可以將這項功能附加至 GitHub 上的提案/工作問題，以進行最終公開評論。</span><span class="sxs-lookup"><span data-stu-id="cecd9-131">Once the draft is completed, this can be appended to the Proposal / Task issue on GitHub for final public review.</span></span>

### <a name="architecture-documentation"></a><span data-ttu-id="cecd9-132">架構檔</span><span class="sxs-lookup"><span data-stu-id="cecd9-132">Architecture documentation</span></span>

<span data-ttu-id="cecd9-133">一旦接受草稿架構，就可以提出額外的提取要求，將最終的完整架構檔提交到存放庫。</span><span class="sxs-lookup"><span data-stu-id="cecd9-133">Once the draft architecture is accepted, additional pull requests can be made to submit the final full architecture documents to the repository.</span></span>

><span data-ttu-id="cecd9-134">TODO：新增完整架構範本的連結</span><span class="sxs-lookup"><span data-stu-id="cecd9-134">TODO: Add link to the full architecture template</span></span>

<span data-ttu-id="cecd9-135">架構檔一經核准，就可以進行第一次提交程式碼。</span><span class="sxs-lookup"><span data-stu-id="cecd9-135">Once the architecture document is approved, only then can the first code submissions can be made.</span></span>

<span data-ttu-id="cecd9-136">開發可以在您自己的私用分支中開始，並在正常的情況下完成，不過，提交回核心 MRTK 專案的 PR 應分階段提交，以確保審查和核准會像 (一樣順利進行，並確保核心變更不會影響其他功能) </span><span class="sxs-lookup"><span data-stu-id="cecd9-136">Development can begin in your own private branch and complete as normal, however, the PR's submitted back to the core MRTK project should be submitted in stages to ensure the review and approval is as smooth as it can be (and ensure core changes do not impact other features)</span></span>

### <a name="core-implementation"></a><span data-ttu-id="cecd9-137">核心執行</span><span class="sxs-lookup"><span data-stu-id="cecd9-137">Core implementation</span></span>

<span data-ttu-id="cecd9-138">應提交的初始工作是執行：</span><span class="sxs-lookup"><span data-stu-id="cecd9-138">The initial work that should be submitted, is to implement:</span></span>

* <span data-ttu-id="cecd9-139">定義</span><span class="sxs-lookup"><span data-stu-id="cecd9-139">Definitions</span></span>
* <span data-ttu-id="cecd9-140">介面</span><span class="sxs-lookup"><span data-stu-id="cecd9-140">Interfaces</span></span>
* <span data-ttu-id="cecd9-141">組態設定檔</span><span class="sxs-lookup"><span data-stu-id="cecd9-141">Configuration profiles</span></span>
* <span data-ttu-id="cecd9-142">事件資料</span><span class="sxs-lookup"><span data-stu-id="cecd9-142">Event data</span></span>

<span data-ttu-id="cecd9-143">如有需要，可以更新架構檔，使其符合對執行的任何變更。</span><span class="sxs-lookup"><span data-stu-id="cecd9-143">If needed, the architectural document can be updated to align with any changes to the implementation.</span></span>

<span data-ttu-id="cecd9-144">請確認所有現有的單元測試和任何新的測試都在提交之前都通過。</span><span class="sxs-lookup"><span data-stu-id="cecd9-144">Please ensure that all existing Unit Tests and any new tests are all passing prior to submission.</span></span>

### <a name="sdk-implementation"></a><span data-ttu-id="cecd9-145">SDK 執行</span><span class="sxs-lookup"><span data-stu-id="cecd9-145">SDK implementation</span></span>

<span data-ttu-id="cecd9-146">將核心介面和事件彙總到開發之後，即可提交 SDK 元件的工作。</span><span class="sxs-lookup"><span data-stu-id="cecd9-146">Once the core interfaces and events are merged in to development, work can then be submitted for the SDK components.</span></span>  <span data-ttu-id="cecd9-147">針對支援的平臺和單元測試，新增功能的具體執行和測試。</span><span class="sxs-lookup"><span data-stu-id="cecd9-147">Adding the concrete implementation of the feature and testing against the supported platforms and unit tests.</span></span>

### <a name="example-implementation"></a><span data-ttu-id="cecd9-148">範例執行</span><span class="sxs-lookup"><span data-stu-id="cecd9-148">Example implementation</span></span>

<span data-ttu-id="cecd9-149">合併 SDK 元件之後，就可以提交範例幕後的任何示範場景或更新。</span><span class="sxs-lookup"><span data-stu-id="cecd9-149">Once the SDK components are merged, then any demo scenes or updates to the example scenes can be submitted.</span></span>

* <span data-ttu-id="cecd9-150">示範適用于特定功能的醒目提示和示範</span><span class="sxs-lookup"><span data-stu-id="cecd9-150">Demos are for specific feature highlighting and demonstration</span></span>
* <span data-ttu-id="cecd9-151">範例是完整的工作場景學習範例</span><span class="sxs-lookup"><span data-stu-id="cecd9-151">Examples are full working scene learning examples</span></span>

## <a name="new-feature-requirements"></a><span data-ttu-id="cecd9-152">新功能需求</span><span class="sxs-lookup"><span data-stu-id="cecd9-152">New feature requirements</span></span>

<span data-ttu-id="cecd9-153">大部分的功能執行都可以分為三個主要部分：</span><span class="sxs-lookup"><span data-stu-id="cecd9-153">Most feature implementations can be broken down into 3 main parts:</span></span>

1. [<span data-ttu-id="cecd9-154">功能管理員</span><span class="sxs-lookup"><span data-stu-id="cecd9-154">The Feature Manager</span></span>](#manager-implementation-requirements)
2. <span data-ttu-id="cecd9-155">[事件資料](#event-data-implementation-requirements) (選擇性) </span><span class="sxs-lookup"><span data-stu-id="cecd9-155">[The Event Data](#event-data-implementation-requirements) (Optional)</span></span>
3. <span data-ttu-id="cecd9-156">[功能處理常式](#handler-implementation-requirements) (選擇性) </span><span class="sxs-lookup"><span data-stu-id="cecd9-156">[The Feature Handler](#handler-implementation-requirements) (Optional)</span></span>

### <a name="manager-implementation-requirements"></a><span data-ttu-id="cecd9-157">管理員執行需求</span><span class="sxs-lookup"><span data-stu-id="cecd9-157">Manager implementation requirements</span></span>

* <span data-ttu-id="cecd9-158">資料夾外部程式碼的元件定義 `MRTK/Core` 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-158">Assembly Definitions for code outside of the `MRTK/Core` folder.</span></span>
  * <span data-ttu-id="cecd9-159">這可確保功能是獨立的，而且沒有其他功能的相依性。</span><span class="sxs-lookup"><span data-stu-id="cecd9-159">This ensures features are self-contained and have no dependencies to other features.</span></span>
* <span data-ttu-id="cecd9-160">使用中找到的介面來定義 `MRTK/Core/Definitions/<FeatureName>System` 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-160">Be defined using an interface found in `MRTK/Core/Definitions/<FeatureName>System`.</span></span>
* <span data-ttu-id="cecd9-161">如果功能的實體管理員實作為，則應該直接繼承， `BaseManager` 或者 `MixedRealityEventManager` 它們會引發事件。</span><span class="sxs-lookup"><span data-stu-id="cecd9-161">A feature's concrete manager implementation should inherit directly from `BaseManager` or `MixedRealityEventManager` if they will raise events.</span></span>
* <span data-ttu-id="cecd9-162">功能的實體管理員執行應設定，並確認該場景已準備好供該系統在中使用 `Initialize` 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-162">A feature's concrete manager implementation should setup and verify that the scene is ready for that system to use in `Initialize`.</span></span>
* <span data-ttu-id="cecd9-163">功能的實體管理員也應該在其移除在的場景中建立的任何程式之後清除 `Destroy` 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-163">A feature's concrete manager should also clean up after themselves removing anything created in the scene in `Destroy`.</span></span>
* <span data-ttu-id="cecd9-164">向混合現實管理員註冊。</span><span class="sxs-lookup"><span data-stu-id="cecd9-164">Be registered with the Mixed Reality Manager.</span></span>
  * <span data-ttu-id="cecd9-165">如果功能是核心功能，則應該將此功能硬式編碼到 `MixedRealityToolkit` 和， `CoreServices` 並新增至 `MixedRealityConfigurationProfile` 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-165">If the feature is a core feature, this should be hard coded into the `MixedRealityToolkit` and `CoreServices` and added to the `MixedRealityConfigurationProfile`.</span></span>
    * <span data-ttu-id="cecd9-166">這包括能夠透過使用下拉式清單來指定具體的實作為 `SystemType` 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-166">This includes being able to specify a concrete implementation via dropdown using `SystemType`.</span></span>
    * <span data-ttu-id="cecd9-167">功能應該具有衍生自可編寫腳本之物件的設定檔。</span><span class="sxs-lookup"><span data-stu-id="cecd9-167">Features should have a configuration profile that derives from a scriptable object.</span></span>
    * <span data-ttu-id="cecd9-168">預設設定設定檔位於 `MRTK/SDK/Profiles` 並指派給混合現實管理員的預設設定設定檔</span><span class="sxs-lookup"><span data-stu-id="cecd9-168">A default configuration profile located in `MRTK/SDK/Profiles` and be assigned in the default configuration profile for the Mixed Reality Manager</span></span>
  * <span data-ttu-id="cecd9-169">如果這項功能 **不** 是核心功能，則必須使用延伸模組服務設定檔進行註冊並執行 `IMixedRealityExtensionService` 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-169">If this feature is **not** a core feature, then it must be registered using the extension service configuration profile and implement `IMixedRealityExtensionService`.</span></span>
* <span data-ttu-id="cecd9-170">具有位於中的預設實作為 `MRTK/Services/<FeatureName>`</span><span class="sxs-lookup"><span data-stu-id="cecd9-170">Have a default implementation located in `MRTK/Services/<FeatureName>`</span></span>
* <span data-ttu-id="cecd9-171">可以使用系統引發的事件應該在介面中定義，並使用所有必要的參數來將事件資料初始化。</span><span class="sxs-lookup"><span data-stu-id="cecd9-171">Events that can be raised with the system should be defined in the interface, with all the required parameters for initializing the event data.</span></span>

### <a name="event-data-implementation-requirements"></a><span data-ttu-id="cecd9-172">事件資料執行需求</span><span class="sxs-lookup"><span data-stu-id="cecd9-172">Event data implementation requirements</span></span>

<span data-ttu-id="cecd9-173">事件資料會明確定義處理常式預期要從事件接收哪些資料。</span><span class="sxs-lookup"><span data-stu-id="cecd9-173">The Event Data defines exactly what data the handler is expected to receive from the event.</span></span>

* <span data-ttu-id="cecd9-174">此功能的所有事件基準都應該在中定義 `MixedRealityToolkit/EventDatum/<FeatureName>` 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-174">All Event Datum for the feature should be defined in `MixedRealityToolkit/EventDatum/<FeatureName>`.</span></span>
* <span data-ttu-id="cecd9-175">所有新的事件資料類別都應該繼承自 `GenericBaseEventData`</span><span class="sxs-lookup"><span data-stu-id="cecd9-175">All new Event Data classes should inherit from `GenericBaseEventData`</span></span>

### <a name="handler-implementation-requirements"></a><span data-ttu-id="cecd9-176">處理常式的執行需求</span><span class="sxs-lookup"><span data-stu-id="cecd9-176">Handler implementation requirements</span></span>

<span data-ttu-id="cecd9-177">處理常式介面會定義元件應該接聽的每個事件，以及傳遞的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cecd9-177">The Handler Interface defines each event a component should be listening for and the types of data passed.</span></span> <span data-ttu-id="cecd9-178">終端使用者將會根據收到的事件資料來執行介面，以執行邏輯。</span><span class="sxs-lookup"><span data-stu-id="cecd9-178">End users will implement the interface to execute logic based on the event data received.</span></span>

* <span data-ttu-id="cecd9-179">處理常式介面應該在中定義 `MixedRealityToolkit/Interfaces/<FeatureName>System/Handlers` 。</span><span class="sxs-lookup"><span data-stu-id="cecd9-179">Handler interfaces should be defined in `MixedRealityToolkit/Interfaces/<FeatureName>System/Handlers`.</span></span>
* <span data-ttu-id="cecd9-180">處理常式介面應該繼承自 `UnityEngine.EventSystems.IEventSystemHandler`</span><span class="sxs-lookup"><span data-stu-id="cecd9-180">Handler interfaces should inherit from `UnityEngine.EventSystems.IEventSystemHandler`</span></span>
* <span data-ttu-id="cecd9-181">預設為加入宣告。</span><span class="sxs-lookup"><span data-stu-id="cecd9-181">Opt-in by default.</span></span> <span data-ttu-id="cecd9-182">若要接收系統的事件，處理常式必須向系統註冊，才能接收這些事件。</span><span class="sxs-lookup"><span data-stu-id="cecd9-182">To receive events from the system, the handler will need to register itself with the system to receive those events.</span></span>
