---
title: 參與
description: 如何參與混合現實工具組
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Bug 報告、
ms.openlocfilehash: 11a62708b4cb1a5acc3d230f933be2e88e0ac87b
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850364"
---
# <a name="contributing"></a><span data-ttu-id="f426d-104">參與</span><span class="sxs-lookup"><span data-stu-id="f426d-104">Contributing</span></span>

<span data-ttu-id="f426d-105">「混合現實」工具組 (MRTK) 歡迎來自社區的投稿。</span><span class="sxs-lookup"><span data-stu-id="f426d-105">The Mixed Reality Toolkit (MRTK) welcomes contributions from the community.</span></span> <span data-ttu-id="f426d-106">所有變更都很小或很大，需要遵守 MRTK 的 [編碼標準](coding-guidelines.md)，因此請確定您在進行開發時熟悉這些變更，以避免在變更變更時延遲。</span><span class="sxs-lookup"><span data-stu-id="f426d-106">All changes be they small or large, need to adhere to the [MRTK coding standards](coding-guidelines.md), so please ensure you are familiar with these while developing to avoid delays when the change is being reviewed.</span></span>

<span data-ttu-id="f426d-107">如果您有任何問題，請在「 [混合現實-工具組頻道」上](https://holodevelopers.slack.com/messages/C2H4HT858)找到您的時差。</span><span class="sxs-lookup"><span data-stu-id="f426d-107">If you have any questions, please reach out on the [mixed-reality-toolkit channel on Slack](https://holodevelopers.slack.com/messages/C2H4HT858).</span></span>
<span data-ttu-id="f426d-108">您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。</span><span class="sxs-lookup"><span data-stu-id="f426d-108">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

## <a name="submission-process"></a><span data-ttu-id="f426d-109">提交程序</span><span class="sxs-lookup"><span data-stu-id="f426d-109">Submission process</span></span>

<span data-ttu-id="f426d-110">我們提供數個途徑，讓開發人員能夠參與混合現實工具組，並從 [建立新的問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)開始。</span><span class="sxs-lookup"><span data-stu-id="f426d-110">We provide several paths to enable developers to contribute to the Mixed Reality Toolkit, all starting with [creating a new Issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).</span></span>

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

<span data-ttu-id="f426d-111">您可以從這裡的檔案：</span><span class="sxs-lookup"><span data-stu-id="f426d-111">From here you file:</span></span>

- <span data-ttu-id="f426d-112">**Bug 報告** -其中一個混合現實工具組元件的功能問題</span><span class="sxs-lookup"><span data-stu-id="f426d-112">**Bug report** - Functionality issue with one of the Mixed Reality Toolkit components</span></span>
- <span data-ttu-id="f426d-113">**檔問題**-混合現實工具組 [檔](https://microsoft.github.io/MixedRealityToolkit-Unity)的問題</span><span class="sxs-lookup"><span data-stu-id="f426d-113">**Documentation issue** - Issue with the Mixed Reality Toolkit [documentation](https://microsoft.github.io/MixedRealityToolkit-Unity)</span></span>
- <span data-ttu-id="f426d-114">**功能要求** -全新混合現實工具組功能的提案</span><span class="sxs-lookup"><span data-stu-id="f426d-114">**Feature request** - Proposal for a new Mixed Reality Toolkit feature</span></span>

## <a name="proposing-feature-requests"></a><span data-ttu-id="f426d-115">建議功能要求</span><span class="sxs-lookup"><span data-stu-id="f426d-115">Proposing feature requests</span></span>

<span data-ttu-id="f426d-116">要求新的混合現實工具組功能時，請務必記錄要解決的客戶權益/問題。</span><span class="sxs-lookup"><span data-stu-id="f426d-116">When requesting a new Mixed Reality Toolkit feature, it is important to document the customer benefit / problem to be solved.</span></span> <span data-ttu-id="f426d-117">提交之後，會在 GitHub 上審核並討論功能要求。</span><span class="sxs-lookup"><span data-stu-id="f426d-117">Once submitted, a feature request will be reviewed and discussed on GitHub.</span></span> <span data-ttu-id="f426d-118">我們鼓勵各項功能提案的開放且建設性的討論，以確保工作對大型客戶的部門有利。</span><span class="sxs-lookup"><span data-stu-id="f426d-118">We encourage open and constructive discussion of each feature proposal to ensure that the work is beneficial to a large segment of customers.</span></span>

<span data-ttu-id="f426d-119">為了避免需要重新修改功能，通常建議在審核階段中不會開始開發功能。</span><span class="sxs-lookup"><span data-stu-id="f426d-119">To avoid needing to rework the feature, it is generally recommended that development of the feature does not begin during the review phase.</span></span> <span data-ttu-id="f426d-120">在許多情況下，「社區審核」程式會發現一或多個可能需要在建議的執行中進行重大變更的問題。</span><span class="sxs-lookup"><span data-stu-id="f426d-120">Many times, the community review process uncovers one or more issues that may require significant changes in the proposed implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="f426d-121">如果您想要處理已經存在於待處理專案上的專案，您可以使用該工作專案作為提案。</span><span class="sxs-lookup"><span data-stu-id="f426d-121">If you wish to work on something that already exists on our backlog, you can use that work item as your proposal.</span></span> <span data-ttu-id="f426d-122">請務必同時對工作發出批註，通知維護人員您正在完成該工作。</span><span class="sxs-lookup"><span data-stu-id="f426d-122">Be sure to also comment on the task notifying maintainers that you're working towards completing it.</span></span>

## <a name="contribution-process"></a><span data-ttu-id="f426d-123">投稿流程</span><span class="sxs-lookup"><span data-stu-id="f426d-123">Contribution process</span></span>

<span data-ttu-id="f426d-124">若要開始，只要遵循下列步驟即可：</span><span class="sxs-lookup"><span data-stu-id="f426d-124">To get started, simply follow these steps:</span></span>

1. <span data-ttu-id="f426d-125">分叉存放庫。</span><span class="sxs-lookup"><span data-stu-id="f426d-125">Fork the repository.</span></span> <span data-ttu-id="f426d-126">按一下頁面右上方的 [分支] 按鈕，然後遵循流程。</span><span class="sxs-lookup"><span data-stu-id="f426d-126">Click on the "Fork" button on the top right of the page and follow the flow.</span></span>
1. <span data-ttu-id="f426d-127">在您的分支中建立分支 (從 [主要](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) 分支) ，讓您可以更輕鬆地隔離任何變更，直到準備好提交為止。</span><span class="sxs-lookup"><span data-stu-id="f426d-127">Create a branch in your fork (off of the [main](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) branch) to make it easier to isolate any changes until ready for submission.</span></span> <span data-ttu-id="f426d-128">若要在發行穩定期間內修正錯誤，請尋找最新的 `prerelease/*` 分支。</span><span class="sxs-lookup"><span data-stu-id="f426d-128">For bug fixes during a release stabilization period, look for the latest `prerelease/*` branch.</span></span> <span data-ttu-id="f426d-129">新功能應該隨時進入 `main` 。</span><span class="sxs-lookup"><span data-stu-id="f426d-129">New features should always go into `main`.</span></span>

<span data-ttu-id="f426d-130">如果您不熟悉 Git 工作流程，請 [參閱 Github 的簡介](https://guides.github.com/activities/hello-world/)。</span><span class="sxs-lookup"><span data-stu-id="f426d-130">If you are new to to the Git workflow, [check out this introduction from Github](https://guides.github.com/activities/hello-world/).</span></span>

<span data-ttu-id="f426d-131">新增 bug 修正或功能時，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f426d-131">When adding a bug fix or feature, follow these steps:</span></span>

1. <span data-ttu-id="f426d-132">執行 bug 修正或功能。</span><span class="sxs-lookup"><span data-stu-id="f426d-132">Implement the bug fix or feature.</span></span> <span data-ttu-id="f426d-133">建立和部署 MRTK 的指示位於 [部署至 Hololens 和 WMR 裝置](../supported-devices/wmr-mrtk.md)。</span><span class="sxs-lookup"><span data-stu-id="f426d-133">Instructions for building and deploying MRTK are at [Deploying to Hololens and WMR devices](../supported-devices/wmr-mrtk.md).</span></span> <span data-ttu-id="f426d-134">請記得遵循程式 [代碼撰寫方針](../contributing/coding-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="f426d-134">Remember to follow the [Coding Guidelines](../contributing/coding-guidelines.md).</span></span>
1. <span data-ttu-id="f426d-135">如果加入功能，也請新增示範功能的範例場景。</span><span class="sxs-lookup"><span data-stu-id="f426d-135">If adding a feature, also add an example scene that demonstrates the feature.</span></span>
1. <span data-ttu-id="f426d-136">如果新增實驗性功能，則不需要撰寫測試和檔。</span><span class="sxs-lookup"><span data-stu-id="f426d-136">If adding an experimental feature, then writing tests and documentation are not necessary.</span></span> <span data-ttu-id="f426d-137">相反地，請依照 [實驗性功能指導方針](../contributing/experimental-features.md)進行。</span><span class="sxs-lookup"><span data-stu-id="f426d-137">Instead, follow [experimental feature guidelines](../contributing/experimental-features.md).</span></span>
1. <span data-ttu-id="f426d-138">加入測試以確認 bug 修正/功能。</span><span class="sxs-lookup"><span data-stu-id="f426d-138">Add tests to verify the bug fix / feature.</span></span> <span data-ttu-id="f426d-139">撰寫和執行測試的指示位於 [>--run-unittests](../contributing/unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="f426d-139">Instructions for writing and running tests are at [UnitTests](../contributing/unit-tests.md).</span></span>
1. <span data-ttu-id="f426d-140">請確定) 的程式碼和功能 (記載于 [檔指導方針](../contributing/documentation-guide.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="f426d-140">Ensure the code and feature(s) are documented as described in the [Documentation Guidelines](../contributing/documentation-guide.md).</span></span>
1. <span data-ttu-id="f426d-141">確定程式碼在所有平臺上都能以預期的方式運作。</span><span class="sxs-lookup"><span data-stu-id="f426d-141">Ensure the code works as intended on all platforms.</span></span> <span data-ttu-id="f426d-142">請參閱 [版本](../release-notes/mrtk-26-release-notes.md) 資訊以取得支援的平臺清單。</span><span class="sxs-lookup"><span data-stu-id="f426d-142">Please see [Release notes](../release-notes/mrtk-26-release-notes.md) for the list of supported platforms.</span></span> <span data-ttu-id="f426d-143">針對 Windows UWP 專案，程式碼必須 [符合 WACK 規範](https://developer.microsoft.com/windows/develop/app-certification-kit)。</span><span class="sxs-lookup"><span data-stu-id="f426d-143">For Windows UWP projects, code must be [WACK compliant](https://developer.microsoft.com/windows/develop/app-certification-kit).</span></span> <span data-ttu-id="f426d-144">若要這樣做，請產生 Visual Studio 方案，以滑鼠右鍵按一下專案;**存放區**  > **建立應用程式套件**。</span><span class="sxs-lookup"><span data-stu-id="f426d-144">To do this, generate a Visual Studio solution, right click on project; **Store** > **Create App Packages**.</span></span> <span data-ttu-id="f426d-145">遵循提示並執行 WACK 測試。</span><span class="sxs-lookup"><span data-stu-id="f426d-145">Follow the prompts and run WACK tests.</span></span> <span data-ttu-id="f426d-146">請確定它們都成功。</span><span class="sxs-lookup"><span data-stu-id="f426d-146">Make sure they all succeed.</span></span>
1. <span data-ttu-id="f426d-147">提出提取要求時，請遵循 [提取要求](../contributing/pull-requests.md) 中的指示。</span><span class="sxs-lookup"><span data-stu-id="f426d-147">Follow the instructions at [Pull Requests](../contributing/pull-requests.md) when making a pull request.</span></span>
