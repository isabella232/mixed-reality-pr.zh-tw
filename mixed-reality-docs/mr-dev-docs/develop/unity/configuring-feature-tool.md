---
title: 設定 Mixed Reality 功能工具
description: 瞭解如何從 HoloLens 和 VR 開發的 MR 功能工具下載並安裝混合現實 Unity 套件。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731940"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="43a6c-104">設定 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="43a6c-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="43a6c-105">使用「混合現實」功能時，您可以存取三個不同的設定類別，您可以在此進行自訂：</span><span class="sxs-lookup"><span data-stu-id="43a6c-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="43a6c-106">下載設定</span><span class="sxs-lookup"><span data-stu-id="43a6c-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="43a6c-107">功能設定</span><span class="sxs-lookup"><span data-stu-id="43a6c-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="43a6c-108">匯入設定</span><span class="sxs-lookup"><span data-stu-id="43a6c-108">Import settings</span></span>](#import-settings)

## <a name="download-settings"></a><span data-ttu-id="43a6c-109">下載設定</span><span class="sxs-lookup"><span data-stu-id="43a6c-109">Download settings</span></span>

![下載設定](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="43a6c-111">覆寫現有封裝檔案</span><span class="sxs-lookup"><span data-stu-id="43a6c-111">Overwrite existing package files</span></span>

<span data-ttu-id="43a6c-112">啟用此設定會導致每次取得套件檔案時都會下載。</span><span class="sxs-lookup"><span data-stu-id="43a6c-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 

* <span data-ttu-id="43a6c-113">**建議您將此選項保持為停用狀態，以降低網路頻寬使用量**</span><span class="sxs-lookup"><span data-stu-id="43a6c-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="43a6c-114">依預設，不會重新下載先前取得的套件檔案</span><span class="sxs-lookup"><span data-stu-id="43a6c-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="43a6c-115">套件快取</span><span class="sxs-lookup"><span data-stu-id="43a6c-115">Package cache</span></span>

<span data-ttu-id="43a6c-116">變更此設定以更新功能套件的下載位置。</span><span class="sxs-lookup"><span data-stu-id="43a6c-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="43a6c-117">這項設定在此版本中是 **唯讀** 的。</span><span class="sxs-lookup"><span data-stu-id="43a6c-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="43a6c-118">未來的版本可能會讓此設定可供設定。</span><span class="sxs-lookup"><span data-stu-id="43a6c-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="43a6c-119">功能設定</span><span class="sxs-lookup"><span data-stu-id="43a6c-119">Feature settings</span></span>

![功能設定](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a><span data-ttu-id="43a6c-121">顯示預覽版本</span><span class="sxs-lookup"><span data-stu-id="43a6c-121">Show preview releases</span></span>

<span data-ttu-id="43a6c-122">啟用此設定以取得預覽版本。</span><span class="sxs-lookup"><span data-stu-id="43a6c-122">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="43a6c-123">依預設，預覽版本不會顯示在混合現實功能工具中</span><span class="sxs-lookup"><span data-stu-id="43a6c-123">By default, preview releases are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="43a6c-124">預覽版本定義為包含套件版本中的 **"-preview"** 指定。</span><span class="sxs-lookup"><span data-stu-id="43a6c-124">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

### <a name="show-early-access-program-features"></a><span data-ttu-id="43a6c-125">顯示早期訪問程式功能</span><span class="sxs-lookup"><span data-stu-id="43a6c-125">Show early access program features</span></span>

<span data-ttu-id="43a6c-126">啟用此設定可從註冊的早期訪問程式版本取得功能。</span><span class="sxs-lookup"><span data-stu-id="43a6c-126">Enable this setting to acquire features from registered early access programs releases.</span></span>

* <span data-ttu-id="43a6c-127">依預設，「混合現實」功能工具不會顯示早期存取功能</span><span class="sxs-lookup"><span data-stu-id="43a6c-127">By default, early access features are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="43a6c-128">`Show early access program features`在不啟用的情況下啟用， `Show preview releases` 可能會導致 eary 存取套件未出現在探索中。</span><span class="sxs-lookup"><span data-stu-id="43a6c-128">Enabling `Show early access program features` without `Show preview releases` may result in eary access packages not appearing in Discovery.</span></span>

## <a name="import-settings"></a><span data-ttu-id="43a6c-129">匯入設定</span><span class="sxs-lookup"><span data-stu-id="43a6c-129">Import settings</span></span>

![匯入設定](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a><span data-ttu-id="43a6c-131">取代現有的封裝檔案</span><span class="sxs-lookup"><span data-stu-id="43a6c-131">Replace existing package files</span></span>

<span data-ttu-id="43a6c-132">依預設，混合現實功能工具會移除匯入之套件的先前複本，以減少檔案大小和不必要的計算。</span><span class="sxs-lookup"><span data-stu-id="43a6c-132">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 

* <span data-ttu-id="43a6c-133">取消核取此設定以保留所有版本</span><span class="sxs-lookup"><span data-stu-id="43a6c-133">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="43a6c-134">專案相對匯入路徑</span><span class="sxs-lookup"><span data-stu-id="43a6c-134">Project relative import path</span></span>

<span data-ttu-id="43a6c-135">將此設定變更為更新匯入時複製功能套件的專案資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="43a6c-135">Change this setting to update project folder path where feature packages are copied on import.</span></span> 

* <span data-ttu-id="43a6c-136">例如，如果專案資料夾是 **C:\GalaxyExplorer**，則完整的匯入路徑將會是 **C:\GalaxyExplorer\Packages\MixedReality**。</span><span class="sxs-lookup"><span data-stu-id="43a6c-136">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="43a6c-137">這項設定在此版本中是 **唯讀** 的。</span><span class="sxs-lookup"><span data-stu-id="43a6c-137">This setting is **read-only** in this release.</span></span> <span data-ttu-id="43a6c-138">未來的版本可能會讓此設定可供設定。</span><span class="sxs-lookup"><span data-stu-id="43a6c-138">Future releases may make this setting configurable.</span></span>

## <a name="early-access-settings"></a><span data-ttu-id="43a6c-139">早期存取設定</span><span class="sxs-lookup"><span data-stu-id="43a6c-139">Early Access settings</span></span>

![早期存取設定](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a><span data-ttu-id="43a6c-141">移除早期存取程式之前要求確認</span><span class="sxs-lookup"><span data-stu-id="43a6c-141">Ask for confirmation before removing an early access program</span></span>

<span data-ttu-id="43a6c-142">這項設定會決定每次移除早期存取程式時，是否要顯示提示。</span><span class="sxs-lookup"><span data-stu-id="43a6c-142">This setting determines if a prompt will be displayed each time an early access program is removed.</span></span>

### <a name="my-previews"></a><span data-ttu-id="43a6c-143">我的預覽</span><span class="sxs-lookup"><span data-stu-id="43a6c-143">My previews</span></span>

<span data-ttu-id="43a6c-144">已註冊的早期存取程式清單。</span><span class="sxs-lookup"><span data-stu-id="43a6c-144">The list of registered early access programs.</span></span> <span data-ttu-id="43a6c-145">使用 `Add` 、 `Edit` 和 `Remove` 來管理已註冊程式的集合。</span><span class="sxs-lookup"><span data-stu-id="43a6c-145">Use the `Add`, `Edit` and `Remove` to manage the collection of registered programs.</span></span>

## <a name="diagnostic-settings"></a><span data-ttu-id="43a6c-146">診斷設定</span><span class="sxs-lookup"><span data-stu-id="43a6c-146">Diagnostic settings</span></span>

![診斷設定](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a><span data-ttu-id="43a6c-148">記錄檔</span><span class="sxs-lookup"><span data-stu-id="43a6c-148">Log file</span></span>

<span data-ttu-id="43a6c-149">顯示診斷記錄檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="43a6c-149">Displays the path to the diagnostic log file.</span></span>

## <a name="see-also"></a><span data-ttu-id="43a6c-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43a6c-150">See also</span></span>

- [<span data-ttu-id="43a6c-151">歡迎使用 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="43a6c-151">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)