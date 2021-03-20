---
title: 匯入功能
description: 瞭解如何從 HoloLens 和 VR 開發的 MR 功能工具匯入和安裝功能。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230807"
---
# <a name="importing-features"></a><span data-ttu-id="1e252-104">匯入功能</span><span class="sxs-lookup"><span data-stu-id="1e252-104">Importing features</span></span>

<span data-ttu-id="1e252-105">下載您的功能之後，您就可以檢查並匯入至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="1e252-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="1e252-106">在這個步驟中，您的應用程式視窗看起來應該如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="1e252-106">At this step, your application window should look like the following image:</span></span>

![匯入功能](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="1e252-108">功能清單</span><span class="sxs-lookup"><span data-stu-id="1e252-108">Features list</span></span>

<span data-ttu-id="1e252-109">[ **功能** ] 清單包含探索期間選取的封裝集合。</span><span class="sxs-lookup"><span data-stu-id="1e252-109">The **Features** list contains the collection of packages selected during discovery.</span></span> <span data-ttu-id="1e252-110">您可以在匯入之前選取或取消選取每項功能。</span><span class="sxs-lookup"><span data-stu-id="1e252-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="1e252-111">您可以使用如下所示的 **詳細資料** 連結來查看套件詳細資料</span><span class="sxs-lookup"><span data-stu-id="1e252-111">Package details can be viewed using the **Details** link shown below</span></span>

![功能清單](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="1e252-113">必要相依性清單</span><span class="sxs-lookup"><span data-stu-id="1e252-113">Required dependencies list</span></span>

<span data-ttu-id="1e252-114">**必要** 的相依性清單包含一或多個所選功能需要運作的封裝。</span><span class="sxs-lookup"><span data-stu-id="1e252-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="1e252-115">這份清單也會包含相依性的相依性。</span><span class="sxs-lookup"><span data-stu-id="1e252-115">This list will also contain dependencies of dependencies.</span></span> <span data-ttu-id="1e252-116">您可以選取或取消選取每個相依性，然後再匯入。</span><span class="sxs-lookup"><span data-stu-id="1e252-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="1e252-117">您可以使用如下所示的 **詳細資料** 連結來查看套件詳細資料</span><span class="sxs-lookup"><span data-stu-id="1e252-117">Package details can be viewed using the **Details** link shown below</span></span>

![相依性清單](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="1e252-119">當您在 Unity 中載入專案時，取消選擇必要的相依性將會導致一個或多個遺失的相依性錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e252-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="1e252-120">這些功能無法在專案中使用。</span><span class="sxs-lookup"><span data-stu-id="1e252-120">These features won't be usable in the project.</span></span>

## <a name="validating-selections"></a><span data-ttu-id="1e252-121">驗證選取專案</span><span class="sxs-lookup"><span data-stu-id="1e252-121">Validating selections</span></span>

<span data-ttu-id="1e252-122">我們強烈建議您在匯入之前驗證特徵選取。</span><span class="sxs-lookup"><span data-stu-id="1e252-122">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="1e252-123">此步驟會引發任何可能妨礙專案開發成功的問題。</span><span class="sxs-lookup"><span data-stu-id="1e252-123">This step will raise any issues that are likely to impede successful project development.</span></span>

![驗證問題](images/ValidationIssues.png)

<span data-ttu-id="1e252-125">Mixed Reality 功能工具提供兩個自動問題解決方式，如下列各節) 所述，以及手動取消和解決問題的選項。</span><span class="sxs-lookup"><span data-stu-id="1e252-125">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="1e252-126">啟用相依性</span><span class="sxs-lookup"><span data-stu-id="1e252-126">Enable dependencies</span></span>

<span data-ttu-id="1e252-127">[ **啟用** 相依性] 按鈕將會自動重新選取遺失的相依性。</span><span class="sxs-lookup"><span data-stu-id="1e252-127">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="1e252-128">這適用于明確選取的相依性 (出現在 [ **功能** 清單]) 中，以及根據所選功能的需求隱含選取的相依性。</span><span class="sxs-lookup"><span data-stu-id="1e252-128">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="1e252-129">停用功能</span><span class="sxs-lookup"><span data-stu-id="1e252-129">Disable features</span></span>

<span data-ttu-id="1e252-130">選取 [ **停用功能** ] 將會自動取消選取相依于一或多個已取消選取之相依性的任何功能。</span><span class="sxs-lookup"><span data-stu-id="1e252-130">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="1e252-131">這適用于隱含選取的相依性封裝和明確選取的功能。</span><span class="sxs-lookup"><span data-stu-id="1e252-131">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="1e252-132">匯入</span><span class="sxs-lookup"><span data-stu-id="1e252-132">Importing</span></span>

<span data-ttu-id="1e252-133">選取 [匯 **入** ] 以新增您選取的功能，並在更新目標專案前提供 [最終核准](reviewing-changes.md) 。</span><span class="sxs-lookup"><span data-stu-id="1e252-133">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1e252-134">如果在匯入時仍有驗證問題，則會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="1e252-134">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="1e252-135">建議您選取 [否]，然後按一下 [ **驗證** ] 並解決任何出現的問題。</span><span class="sxs-lookup"><span data-stu-id="1e252-135">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![繼續進行驗證問題](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="1e252-137">回到上一個步驟</span><span class="sxs-lookup"><span data-stu-id="1e252-137">Going back to the previous step</span></span>

<span data-ttu-id="1e252-138">從匯 **入功能**，混合現實功能工具可讓您回頭流覽至 [探索](discovering-features.md)。</span><span class="sxs-lookup"><span data-stu-id="1e252-138">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="1e252-139">選取 **返回** 下載其他功能套件。</span><span class="sxs-lookup"><span data-stu-id="1e252-139">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e252-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e252-140">See also</span></span>

- [<span data-ttu-id="1e252-141">歡迎使用 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="1e252-141">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="1e252-142">探索和收購</span><span class="sxs-lookup"><span data-stu-id="1e252-142">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="1e252-143">查看功能套件詳細資料</span><span class="sxs-lookup"><span data-stu-id="1e252-143">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="1e252-144">審核和核准專案修改</span><span class="sxs-lookup"><span data-stu-id="1e252-144">Reviewing and approving project modifications</span></span>](reviewing-changes.md)