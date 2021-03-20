---
title: 設定 Mixed Reality 功能工具
description: 瞭解如何從 HoloLens 和 VR 開發的 MR 功能工具下載並安裝混合現實 Unity 套件。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "99244567"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="46d52-104">設定 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="46d52-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="46d52-105">使用「混合現實」功能時，您可以存取三個不同的設定類別，您可以在此進行自訂：</span><span class="sxs-lookup"><span data-stu-id="46d52-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="46d52-106">下載設定</span><span class="sxs-lookup"><span data-stu-id="46d52-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="46d52-107">功能設定</span><span class="sxs-lookup"><span data-stu-id="46d52-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="46d52-108">匯入設定</span><span class="sxs-lookup"><span data-stu-id="46d52-108">Import settings</span></span>](#import-settings)

![設定](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="46d52-110">下載設定</span><span class="sxs-lookup"><span data-stu-id="46d52-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="46d52-111">覆寫現有封裝檔案</span><span class="sxs-lookup"><span data-stu-id="46d52-111">Overwrite existing package files</span></span>

<span data-ttu-id="46d52-112">啟用此設定會導致每次取得套件檔案時都會下載。</span><span class="sxs-lookup"><span data-stu-id="46d52-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="46d52-113">**建議您將此選項保持為停用狀態，以降低網路頻寬使用量**</span><span class="sxs-lookup"><span data-stu-id="46d52-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="46d52-114">依預設，不會重新下載先前取得的套件檔案</span><span class="sxs-lookup"><span data-stu-id="46d52-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="46d52-115">套件快取</span><span class="sxs-lookup"><span data-stu-id="46d52-115">Package cache</span></span>

<span data-ttu-id="46d52-116">變更此設定以更新功能套件的下載位置。</span><span class="sxs-lookup"><span data-stu-id="46d52-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="46d52-117">這項設定在此版本中是 **唯讀** 的。</span><span class="sxs-lookup"><span data-stu-id="46d52-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="46d52-118">未來的版本可能會讓此設定可供設定。</span><span class="sxs-lookup"><span data-stu-id="46d52-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="46d52-119">功能設定</span><span class="sxs-lookup"><span data-stu-id="46d52-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="46d52-120">包含預覽版本</span><span class="sxs-lookup"><span data-stu-id="46d52-120">Include preview releases</span></span>

<span data-ttu-id="46d52-121">啟用此設定以取得預覽版本。</span><span class="sxs-lookup"><span data-stu-id="46d52-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="46d52-122">依預設，預覽版本不會顯示在混合現實功能工具中</span><span class="sxs-lookup"><span data-stu-id="46d52-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="46d52-123">預覽版本定義為包含套件版本中的 **"-preview"** 指定。</span><span class="sxs-lookup"><span data-stu-id="46d52-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="46d52-124">匯入設定</span><span class="sxs-lookup"><span data-stu-id="46d52-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="46d52-125">取代現有的封裝檔案</span><span class="sxs-lookup"><span data-stu-id="46d52-125">Replace existing package files</span></span>

<span data-ttu-id="46d52-126">依預設，混合現實功能工具會移除匯入之套件的先前複本，以減少檔案大小和不必要的計算。</span><span class="sxs-lookup"><span data-stu-id="46d52-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="46d52-127">取消核取此設定以保留所有版本</span><span class="sxs-lookup"><span data-stu-id="46d52-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="46d52-128">專案相對匯入路徑</span><span class="sxs-lookup"><span data-stu-id="46d52-128">Project relative import path</span></span>

<span data-ttu-id="46d52-129">將此設定變更為更新匯入時複製功能套件的專案資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="46d52-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="46d52-130">例如，如果專案資料夾是 **C:\GalaxyExplorer**，則完整的匯入路徑將會是 **C:\GalaxyExplorer\Packages\MixedReality**。</span><span class="sxs-lookup"><span data-stu-id="46d52-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="46d52-131">這項設定在此版本中是 **唯讀** 的。</span><span class="sxs-lookup"><span data-stu-id="46d52-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="46d52-132">未來的版本可能會讓此設定可供設定。</span><span class="sxs-lookup"><span data-stu-id="46d52-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="46d52-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46d52-133">See also</span></span>

- [<span data-ttu-id="46d52-134">歡迎使用 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="46d52-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)