---
title: PullRequests
description: 與提取要求相關的詳細資料。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、PR、
ms.openlocfilehash: acdabed1b6fe35c3f16db9cf3221481c1715321c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780161"
---
# <a name="pull-requests"></a><span data-ttu-id="e6604-104">提取要求</span><span class="sxs-lookup"><span data-stu-id="e6604-104">Pull requests</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6604-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="e6604-105">Prerequisites</span></span>

<span data-ttu-id="e6604-106">如果您之前尚未參與 Microsoft 專案，系統可能會要求您簽署 [投稿授權合約](https://cla.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="e6604-106">If you haven't contributed to a Microsoft project before, you may be asked to sign a [contribution license agreement](https://cla.microsoft.com/).</span></span>
<span data-ttu-id="e6604-107">PR 中的批註可讓您知道您的做法。</span><span class="sxs-lookup"><span data-stu-id="e6604-107">A comment in the PR will let you know if you do.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6604-108">如果您是 Microsoft 員工，而且不是 [GitHub 上的 microsoft 組織](https://github.com/Microsoft)成員，請在您開始提取要求之前，先造訪 [Microsoft 的開放原始](https://opensource.microsoft.com/) 碼，在公司網路上連結您的 microsoft 與 GitHub 帳戶。</span><span class="sxs-lookup"><span data-stu-id="e6604-108">If you are a Microsoft employee and are not a member of the [Microsoft organization on GitHub](https://github.com/Microsoft), please link your Microsoft and GitHub accounts on corpnet by visiting [Open Source at Microsoft](https://opensource.microsoft.com/) before you start your pull request.</span></span> <span data-ttu-id="e6604-109">您必須事先進行一些處理。</span><span class="sxs-lookup"><span data-stu-id="e6604-109">There's some process stuff you'll need to do ahead of time.</span></span>

## <a name="creating-a-pull-request"></a><span data-ttu-id="e6604-110">建立提取要求</span><span class="sxs-lookup"><span data-stu-id="e6604-110">Creating a pull request</span></span>

<span data-ttu-id="e6604-111">當您準備好提交提取要求時，請建立以[mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development)分支為目標的[提取要求](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1)。</span><span class="sxs-lookup"><span data-stu-id="e6604-111">When you are ready to submit a pull request, [create a pull request](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1) targeting the [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) branch.</span></span>

<span data-ttu-id="e6604-112">閱讀指導方針，並確保您的提取要求符合指導方針。</span><span class="sxs-lookup"><span data-stu-id="e6604-112">Read the guidelines and ensure your pull request meets the guidelines.</span></span>

* <span data-ttu-id="e6604-113">請務必參考 PR 相關的任何問題/功能要求或工作。</span><span class="sxs-lookup"><span data-stu-id="e6604-113">Make sure to reference any Issue / Feature Request or Task the PR relates to.</span></span>
* <span data-ttu-id="e6604-114">檢查提取要求只包含與 PR 相關的檔案/變更。</span><span class="sxs-lookup"><span data-stu-id="e6604-114">Check the pull request contains only files / changes related to the PR.</span></span>
* <span data-ttu-id="e6604-115">檢查檔是最新的，並且包含在內。</span><span class="sxs-lookup"><span data-stu-id="e6604-115">Check documentation is up to date and included.</span></span> <span data-ttu-id="e6604-116">檢查所有公用欄位都有批註。</span><span class="sxs-lookup"><span data-stu-id="e6604-116">Check all public fields have comments.</span></span>
* <span data-ttu-id="e6604-117">如果加入新的功能，請檢查是否包含測試以驗證功能 (查看 [>--run-unittests](UnitTests.md)) 。</span><span class="sxs-lookup"><span data-stu-id="e6604-117">If adding a new feature, check that tests are included to validate the feature (see [UnitTests](UnitTests.md)).</span></span>
* <span data-ttu-id="e6604-118">如果要修正錯誤，請撰寫測試來確認 bug 修正。</span><span class="sxs-lookup"><span data-stu-id="e6604-118">If fixing a bug, write a test to verify the bug fix.</span></span>

<span data-ttu-id="e6604-119">專案維護人員會檢查您的變更。</span><span class="sxs-lookup"><span data-stu-id="e6604-119">The project maintainers will review your changes.</span></span> <span data-ttu-id="e6604-120">我們的目標是要在三個工作天內檢查所有變更。</span><span class="sxs-lookup"><span data-stu-id="e6604-120">We aim to review all changes within three business days.</span></span> <span data-ttu-id="e6604-121">請解決任何審核批註、將其推送至您的主題分支，並張貼留言，讓我們知道有新的內容可以複習。</span><span class="sxs-lookup"><span data-stu-id="e6604-121">Please address any review comments, push to your topic branch, and post a comment letting us know that there's new stuff to review.</span></span>

> [!NOTE]
> <span data-ttu-id="e6604-122">所有提交至專案的 PR 也會根據 [MRTK 編碼標準指南](CodingGuidelines.md)進行通過，因此請在提交您的 pr 之前先進行檢查，以確保順暢的流程。</span><span class="sxs-lookup"><span data-stu-id="e6604-122">All PR's submitted to the project will also be vetted according to the [MRTK coding standards guide](CodingGuidelines.md), so please review these before submitting your PR to ensure a smooth process.</span></span>

## <a name="pull-request-guidelines"></a><span data-ttu-id="e6604-123">提取要求指導方針</span><span class="sxs-lookup"><span data-stu-id="e6604-123">Pull request guidelines</span></span>

<span data-ttu-id="e6604-124">這些指導方針是以 [Google 的工程實務](https://google.github.io/eng-practices/review/developer/small-cls.html)為基礎。</span><span class="sxs-lookup"><span data-stu-id="e6604-124">These guidelines are based off of the [Google's engineering practices](https://google.github.io/eng-practices/review/developer/small-cls.html).</span></span>

### <a name="keep-pull-requests-small"></a><span data-ttu-id="e6604-125">保持提取要求的大小</span><span class="sxs-lookup"><span data-stu-id="e6604-125">Keep pull requests small</span></span>

<span data-ttu-id="e6604-126">較小的 Pr 會更快速且詳盡地進行檢查，較不可能引進 bug、更容易復原，而且更容易合併。</span><span class="sxs-lookup"><span data-stu-id="e6604-126">Smaller PRs are reviewed more quickly and thoroughly, are less likely to introduce bugs, easier to roll back, and easier to merge.</span></span>

<span data-ttu-id="e6604-127">提取要求應該夠小，工程師可以在30分鐘內進行審核。</span><span class="sxs-lookup"><span data-stu-id="e6604-127">Pull requests should be small enough that an engineer could review it in under 30 minutes.</span></span> <span data-ttu-id="e6604-128">請嘗試進行不只解決一個問題的基本變更。</span><span class="sxs-lookup"><span data-stu-id="e6604-128">Try to make a minimal change that addresses just one thing.</span></span> <span data-ttu-id="e6604-129">如果您必須建立大型 PR，請將它分割成多個 Pr，以進入您的本機分支或 MRTK 的功能分支。</span><span class="sxs-lookup"><span data-stu-id="e6604-129">If you must create a large PR, split it into several PRs that go into either your local branch, or a feature branch of MRTK.</span></span> <span data-ttu-id="e6604-130">避免將新資產 (例如 fbx、obj 檔案) ，而改為重複使用現有的資產。</span><span class="sxs-lookup"><span data-stu-id="e6604-130">Avoid adding new assets (e.g. fbx, obj files) and instead aim to re-use existing assets.</span></span>

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a><span data-ttu-id="e6604-131">測試應新增至與您的修正/功能相同的 PR 中，但緊急情況除外</span><span class="sxs-lookup"><span data-stu-id="e6604-131">Tests should be added in the same PR as your fix / feature, except for emergencies</span></span>

<span data-ttu-id="e6604-132">測試是確保變更不會回歸現有程式碼的最佳方式，但在提交提取要求時，也很容易忘記測試。</span><span class="sxs-lookup"><span data-stu-id="e6604-132">Tests are the best way to ensure changes do not regress existing code, but it is also easy to forget about tests when submitting pull requests.</span></span> <span data-ttu-id="e6604-133">要求他們進入您的 PR，是確保測試可被撰寫的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="e6604-133">Requiring that they go in with your PR are a great way to ensure that tests get written.</span></span>

<span data-ttu-id="e6604-134">每項功能和錯誤修正都應該有相關聯的測試。</span><span class="sxs-lookup"><span data-stu-id="e6604-134">Every feature and bug fix should have tests associated with it.</span></span> <span data-ttu-id="e6604-135">如果您沒有撰寫測試的專業知識或時間，請建立一個問題來撰寫測試，並將其標示 **為目前反覆運算** 的標籤。</span><span class="sxs-lookup"><span data-stu-id="e6604-135">If you do not have the expertise or time to write a test, create an issue to write the tests, and mark them with label **Consider for Current Iteration**.</span></span>

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a><span data-ttu-id="e6604-136">檔應新增至與修正/功能相同的提取要求中</span><span class="sxs-lookup"><span data-stu-id="e6604-136">Documentation should be added in the same pull request as a fix / feature</span></span>

<span data-ttu-id="e6604-137">大部分的開發人員在瞭解如何使用某項功能時，會先查看檔，而不是程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6604-137">Most developers look first at documentation, not code, when understanding how to use a feature.</span></span> <span data-ttu-id="e6604-138">確保檔是最新的，讓人們更容易取用和信賴 MRTK。</span><span class="sxs-lookup"><span data-stu-id="e6604-138">Ensuring documentation is up to date makes it much easier for people to consume and rely MRTK.</span></span>  <span data-ttu-id="e6604-139">檔應一律與相關的提取配套，以確保專案保持在最新狀態且一致。</span><span class="sxs-lookup"><span data-stu-id="e6604-139">Documentation should always be bundled with the related pull to ensure items remain up-to-date and consistent.</span></span>

<span data-ttu-id="e6604-140">確定每個公用欄位、方法、屬性都有 [三個斜線的摘要批註](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) ，讓我們的 docfx 網站可以產生欄位/方法的描述。</span><span class="sxs-lookup"><span data-stu-id="e6604-140">Ensure every public field, method, property has [triple slash summary comments](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) so our docfx site can generate descriptions for fields / methods.</span></span> <span data-ttu-id="e6604-141">如有需要，請更新檔資料夾中的 markdown 檔。</span><span class="sxs-lookup"><span data-stu-id="e6604-141">If needed, update markdown files in Documentation folder.</span></span>

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a><span data-ttu-id="e6604-142">提取要求描述應該清楚且完整地描述變更</span><span class="sxs-lookup"><span data-stu-id="e6604-142">Pull request descriptions should clearly and completely describe changes</span></span>

<span data-ttu-id="e6604-143">清除並完成提取要求的說明，以確保審核者瞭解他們正在審核的內容。</span><span class="sxs-lookup"><span data-stu-id="e6604-143">Clear and complete descriptions of pull requests ensure reviewers understand what they are reviewing.</span></span>

<span data-ttu-id="e6604-144">如果加入的功能包含 UX，請新增您要變更之功能的影像/gif。</span><span class="sxs-lookup"><span data-stu-id="e6604-144">If adding features that contain UX, add an image / gif of the feature you are changing.</span></span> <span data-ttu-id="e6604-145">[以下是一個很好的範例](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532)。</span><span class="sxs-lookup"><span data-stu-id="e6604-145">[Here is a good example](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532).</span></span> <span data-ttu-id="e6604-146">另一個建議是 [在此提取要求中使用 gif，例如在此提取要求中](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896)。</span><span class="sxs-lookup"><span data-stu-id="e6604-146">Another suggestion is to have a gif of Before and After, [for example in this pull request](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896).</span></span> <span data-ttu-id="e6604-147">我們建議您從螢幕擷取畫面產生 gif 的工具是 [ScreenToGif](https://www.screentogif.com/)。</span><span class="sxs-lookup"><span data-stu-id="e6604-147">A tool we recommend for generating gifs from screen captures is [ScreenToGif](https://www.screentogif.com/).</span></span>
