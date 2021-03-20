---
title: ExperimentalFeatures
description: 與 MRTK 中的實驗性功能相關的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: c2810f6f1f90b32ee7621f52e3911da23a86a983
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693745"
---
# <a name="experimental-features"></a><span data-ttu-id="a7fcc-104">實驗性功能</span><span class="sxs-lookup"><span data-stu-id="a7fcc-104">Experimental features</span></span>

<span data-ttu-id="a7fcc-105">MRTK 小組所處理的某些功能似乎有許多初始值，即使我們尚未完全增補詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="a7fcc-106">針對這些類型的功能，我們想要讓該社區提早看到它們。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="a7fcc-107">因為它們是在迴圈初期進行，所以我們會將它們標示為實驗性，以表示它們仍在不斷演進，且可能隨著時間變更。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="a7fcc-108">實驗性功能的期望</span><span class="sxs-lookup"><span data-stu-id="a7fcc-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="a7fcc-109">如果元件標示為實驗性，您可以預期會有下列各項：</span><span class="sxs-lookup"><span data-stu-id="a7fcc-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="a7fcc-110">示範使用方式的範例場景，位於 `MRTK/Examples/Experimental` 子資料夾下</span><span class="sxs-lookup"><span data-stu-id="a7fcc-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="a7fcc-111">實驗性功能可能沒有檔。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="a7fcc-112">他們可能沒有測試。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-112">They probably don't have tests.</span></span>
- <span data-ttu-id="a7fcc-113">實驗性功能可能會變更。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="a7fcc-114">實驗性功能指導方針</span><span class="sxs-lookup"><span data-stu-id="a7fcc-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="a7fcc-115">實驗性程式碼應該存留在不同的資料夾中</span><span class="sxs-lookup"><span data-stu-id="a7fcc-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="a7fcc-116">實驗性程式碼應進入最上層實驗資料夾，後面接著實驗功能名稱。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="a7fcc-117">例如，如果嘗試貢獻新的功能 FooBar，請將程式碼放在下列程式碼中：</span><span class="sxs-lookup"><span data-stu-id="a7fcc-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="a7fcc-118">範例場景，腳本進入 `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="a7fcc-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="a7fcc-119">元件腳本，prefabs 進入 `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="a7fcc-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="a7fcc-120">元件偵測器進入 `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="a7fcc-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="a7fcc-121">使用實驗性功能名稱下的子資料夾時，請嘗試鏡像相同的 MRTK 資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="a7fcc-122">例如，解析器會進入 `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="a7fcc-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="a7fcc-123">將場景保存在靠近頂端的場景資料夾中： `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="a7fcc-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="a7fcc-124">我們認為沒有單一的實驗根資料夾，而是在假設下進行實驗 `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` 。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="a7fcc-125">我們決定將資料夾放在基底，讓實驗性功能更容易探索。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="a7fcc-126">實驗性程式碼應該在特殊命名空間中</span><span class="sxs-lookup"><span data-stu-id="a7fcc-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="a7fcc-127">確定實驗性程式碼存在於符合非實驗性位置的實驗性命名空間中。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="a7fcc-128">例如，如果您的元件是解析器的一部分 `Microsoft.MixedReality.Toolkit.Utilities.Solvers` ，則其命名空間應該是 `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` 。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="a7fcc-129">如需範例，請參閱 [此 PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) 。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="a7fcc-130">實驗性功能應該要有 [實驗性] 屬性</span><span class="sxs-lookup"><span data-stu-id="a7fcc-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="a7fcc-131">將 `[Experimental]` 屬性新增至您的其中一個欄位上方，在元件編輯器中會出現一個小對話方塊，提及您的功能是實驗性的，並且受限於重大變更。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="a7fcc-132">實驗性功能的功能表應該會在 [實驗性] 子功能表下</span><span class="sxs-lookup"><span data-stu-id="a7fcc-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="a7fcc-133">將命令新增至編輯器中的功能表時，請確定實驗性功能位於 [實驗性] 子功能表。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="a7fcc-134">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="a7fcc-134">Here are a few examples:</span></span>

<span data-ttu-id="a7fcc-135">新增最上層的功能表命令：</span><span class="sxs-lookup"><span data-stu-id="a7fcc-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="a7fcc-136">新增元件功能表：</span><span class="sxs-lookup"><span data-stu-id="a7fcc-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="a7fcc-137">文件</span><span class="sxs-lookup"><span data-stu-id="a7fcc-137">Documentation</span></span>

<span data-ttu-id="a7fcc-138">請遵循下列步驟來新增實驗性功能的檔：</span><span class="sxs-lookup"><span data-stu-id="a7fcc-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="a7fcc-139">實驗性功能的任何檔都應該放在 `readme.md` 實驗資料夾的檔案中。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="a7fcc-140">例如： [`MRTK/SDK/Experimental/PulseShader/readme.md`](../features/experimental/pulse-shader.md) 。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-140">For example, [`MRTK/SDK/Experimental/PulseShader/readme.md`](../features/experimental/pulse-shader.md).</span></span>

1. <span data-ttu-id="a7fcc-141">在 [ *功能概述* ] 下的 [ *實驗* ] 區段中，新增連結 [`Documentation/toc.yml`](../toc.yml) 。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="a7fcc-142">將對 MRTK 程式碼的影響降至最低</span><span class="sxs-lookup"><span data-stu-id="a7fcc-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="a7fcc-143">雖然您的 MRTK 變更可能會讓實驗正常運作，但可能會以您預期的方式影響其他人。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="a7fcc-144">您對 MRTK core 程式碼所做的任何回歸都會導致您的提取要求獲得還原。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="a7fcc-145">在實驗資料夾以外的資料夾中，目標不會有任何變更。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="a7fcc-146">以下是可以進行實驗性變更的資料夾清單：</span><span class="sxs-lookup"><span data-stu-id="a7fcc-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="a7fcc-147">MRTK/SDK/實驗性</span><span class="sxs-lookup"><span data-stu-id="a7fcc-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="a7fcc-148">MRTK/SDK/檢查器/實驗性</span><span class="sxs-lookup"><span data-stu-id="a7fcc-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="a7fcc-149">MRTK/範例/實驗性</span><span class="sxs-lookup"><span data-stu-id="a7fcc-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="a7fcc-150">這些資料夾外部的變更應謹慎處理。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="a7fcc-151">如果您的實驗性功能必須包含 MRTK core 程式碼的變更，請考慮將 MRTK 變更分割成包含測試和檔的個別提取要求。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="a7fcc-152">使用您的實驗性功能不應該影響人們使用核心控制項的能力</span><span class="sxs-lookup"><span data-stu-id="a7fcc-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="a7fcc-153">大部分的人都經常使用核心 UX 元件，例如按鈕、ManipulationHandler 和互動。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="a7fcc-154">如果防止它們使用按鈕，它們可能不會使用您的實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="a7fcc-155">使用您的元件不應中斷按鈕、ManipulationHandler、BoundingBox 或互動。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="a7fcc-156">例如，在 [此 SCROLLABLEOBJECTCOLLECTION PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)中，新增 ScrollableObjectCollection 會導致人員無法使用 HoloLens 按鈕 prefabs。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="a7fcc-157">雖然這不是因為 PR 中的 bug 所造成 (，而是公開現有的錯誤) ，但是它會使 PR 無法進入簽入狀態。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="a7fcc-158">提供示範如何使用此功能的範例場景</span><span class="sxs-lookup"><span data-stu-id="a7fcc-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="a7fcc-159">人們必須瞭解如何使用您的功能，以及如何進行測試。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="a7fcc-160">在 MRTK/範例/實驗/YOUR_FEATURE 下提供範例</span><span class="sxs-lookup"><span data-stu-id="a7fcc-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="a7fcc-161">在實驗性功能中將使用者可見的瑕疵降至最低</span><span class="sxs-lookup"><span data-stu-id="a7fcc-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="a7fcc-162">如果沒有，則不會使用實驗性功能，而不會將它畢業至某項功能。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="a7fcc-163">在您的目標平臺上測試範例場景，並確定其如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="a7fcc-164">確定您的功能也可在編輯器中運作，讓使用者可以快速地逐一查看您的功能，即使它們沒有目標平臺也一樣。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="a7fcc-165">將實驗性程式碼即將畢業至 MRTK 程式碼</span><span class="sxs-lookup"><span data-stu-id="a7fcc-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="a7fcc-166">如果功能最終看到很多用途，則應該將它畢業至核心 MRTK 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="a7fcc-167">若要這樣做，此功能應該具有測試、檔和範例場景。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="a7fcc-168">當您準備好畢業功能 MRTK 時，請建立一個問題，以簽入您的 PR。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="a7fcc-169">PR 應包括將這項功能設為核心功能所需的所有專案：測試、檔，以及顯示使用方式的範例場景。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="a7fcc-170">此外，別忘了更新命名空間，以移除「實驗性」子空間。</span><span class="sxs-lookup"><span data-stu-id="a7fcc-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
