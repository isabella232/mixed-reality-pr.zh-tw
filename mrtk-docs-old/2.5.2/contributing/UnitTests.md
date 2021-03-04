---
title: UnitTests
description: '>--run-unittests 以檢查 MRTK 的可靠性」。'
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、UnitTest、
ms.openlocfilehash: 958f6ae59736003141d0cc96a6706d211be5709c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780160"
---
# <a name="writing-and-running-tests-in-mrtk"></a><span data-ttu-id="c96af-104">在 MRTK 中撰寫和執行測試</span><span class="sxs-lookup"><span data-stu-id="c96af-104">Writing and running tests in MRTK</span></span>

<span data-ttu-id="c96af-105">為了確保 MRTK 可靠，MRTK 有一組測試，以確保程式碼的變更不會回歸現有的行為。</span><span class="sxs-lookup"><span data-stu-id="c96af-105">To ensure MRTK is reliable, MRTK has a set of tests to ensure that changes to the code does not regress existing behavior.</span></span> <span data-ttu-id="c96af-106">在大型程式碼基底（例如 MRTK）中提供良好的測試涵蓋範圍，對穩定性很重要，並且在進行變更時具有自信。</span><span class="sxs-lookup"><span data-stu-id="c96af-106">Having good test coverage in a big codebase like MRTK is crucial for stability and having confidence when making changes.</span></span>

<span data-ttu-id="c96af-107">MRTK 會使用 [Unity 測試](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 執行器，其使用 [NUnit](https://nunit.org/)的 unity 整合。</span><span class="sxs-lookup"><span data-stu-id="c96af-107">MRTK uses the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) which uses a Unity integration of [NUnit](https://nunit.org/).</span></span> <span data-ttu-id="c96af-108">本指南將提供如何將測試新增至 MRTK 的起點。</span><span class="sxs-lookup"><span data-stu-id="c96af-108">This guide will provide a starting point on how to add tests to MRTK.</span></span> <span data-ttu-id="c96af-109">它不會說明 [Unity 測試](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 執行器和 [NUnit](https://nunit.org/) ，您可以在提供的連結中查閱。</span><span class="sxs-lookup"><span data-stu-id="c96af-109">It will not explain the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) and [NUnit](https://nunit.org/) which can be looked up in the links provided.</span></span>

<span data-ttu-id="c96af-110">提交提取要求之前，請務必：</span><span class="sxs-lookup"><span data-stu-id="c96af-110">Before submitting a pull request, make sure to:</span></span>

1. <span data-ttu-id="c96af-111">在本機執行測試，讓您的變更不會回歸現有的行為 (完成 Pr 時，如果有任何測試) 失敗，則不允許。</span><span class="sxs-lookup"><span data-stu-id="c96af-111">Run the tests locally so your changes don't regress existing behavior (completing PRs won't be allowed if any tests fail).</span></span>

1. <span data-ttu-id="c96af-112">如果要修正錯誤，請撰寫測試來測試修正程式，並確定未來的程式碼修改不會再中斷。</span><span class="sxs-lookup"><span data-stu-id="c96af-112">If fixing a bug, write a test to test the fix and ensure that future code modifications won't break it again.</span></span>

1. <span data-ttu-id="c96af-113">如果要撰寫功能，請撰寫新的測試，以防止即將進行的程式碼變更中斷這項功能。</span><span class="sxs-lookup"><span data-stu-id="c96af-113">If writing a feature, write new tests to prevent upcoming code changes breaking this feature.</span></span>

<span data-ttu-id="c96af-114">目前 playmode 的測試是要在 Unity 2018.4 中執行，而其他版本的 Unity 可能會失敗</span><span class="sxs-lookup"><span data-stu-id="c96af-114">Currently playmode tests are meant to be run in Unity 2018.4 and may fail in other versions of Unity</span></span>

## <a name="running-tests"></a><span data-ttu-id="c96af-115">執行測試</span><span class="sxs-lookup"><span data-stu-id="c96af-115">Running tests</span></span>

### <a name="unity-editor"></a><span data-ttu-id="c96af-116">Unity 編輯器</span><span class="sxs-lookup"><span data-stu-id="c96af-116">Unity editor</span></span>

<span data-ttu-id="c96af-117">您可以在 [視窗一般測試執行器 **]** 下找到 [Unity 測試](https://docs.unity3d.com/Manual/testing-editortestsrunner.html)執行器  >    >   ，將會顯示所有可用的 MRTK 播放和編輯模式測試。</span><span class="sxs-lookup"><span data-stu-id="c96af-117">The [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) can be found under **Window** > **General** > **Test Runner** and will show all available MRTK play and edit mode tests.</span></span>

### <a name="command-line"></a><span data-ttu-id="c96af-118">命令列</span><span class="sxs-lookup"><span data-stu-id="c96af-118">Command line</span></span>

<span data-ttu-id="c96af-119">測試也可以透過位於的 [powershell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6add&preserve-view=true) 腳本來執行 `Scripts\test\run_playmode_tests.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="c96af-119">Tests can also be run by a [powershell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6add&preserve-view=true) script located at `Scripts\test\run_playmode_tests.ps1`.</span></span> <span data-ttu-id="c96af-120">這會執行 playmode 測試，就如同在 github/CI 上執行一樣 (請參閱下面) ，並列印結果。</span><span class="sxs-lookup"><span data-stu-id="c96af-120">This will run the playmode tests exactly as they are executed on github / CI (see below), and print results.</span></span> <span data-ttu-id="c96af-121">以下是一些如何執行腳本的範例</span><span class="sxs-lookup"><span data-stu-id="c96af-121">Here are some examples of how to run the script</span></span>

<span data-ttu-id="c96af-122">在位於 H:\mrtk.dev 的專案上執行測試，並使用 Unity 2018.4 (例如 Unity 2018.4.26 f1) </span><span class="sxs-lookup"><span data-stu-id="c96af-122">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4 (for example Unity 2018.4.26f1)</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

<span data-ttu-id="c96af-123">在位於 H:\mrtk.dev、Unity 2018.4 的專案上執行測試，並將結果輸出至 C：\ playmode_test_out</span><span class="sxs-lookup"><span data-stu-id="c96af-123">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4, output results to C:\playmode_test_out</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

<span data-ttu-id="c96af-124">您也可以透過腳本多次執行 playmode 測試 `run_repeat_tests.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="c96af-124">It's also possible to run the playmode tests multiple times via the `run_repeat_tests.ps1` script.</span></span> <span data-ttu-id="c96af-125">中使用的所有參數都可以 `run_playmode_tests.ps1` 使用。</span><span class="sxs-lookup"><span data-stu-id="c96af-125">All parameters used in `run_playmode_tests.ps1` may be used.</span></span>

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a><span data-ttu-id="c96af-126">提取要求驗證</span><span class="sxs-lookup"><span data-stu-id="c96af-126">Pull request validation</span></span>

<span data-ttu-id="c96af-127">MRTK 的 CI 將會建立所有設定的 MRTK，並執行所有的編輯和播放模式測試。</span><span class="sxs-lookup"><span data-stu-id="c96af-127">MRTK's CI will build MRTK in all configurations and run all edit and play mode tests.</span></span> <span data-ttu-id="c96af-128">如果使用者有足夠的許可權，就可以藉由在 github PR 上張貼批註來觸發 CI `/azp run mrtk_pr` 。</span><span class="sxs-lookup"><span data-stu-id="c96af-128">CI can be triggered by posting a comment on the github PR `/azp run mrtk_pr` if the user has sufficient rights.</span></span> <span data-ttu-id="c96af-129">CI 執行可在 PR 的 [檢查] 索引標籤中看到。</span><span class="sxs-lookup"><span data-stu-id="c96af-129">CI runs can be seen in the 'checks' tab of the PR.</span></span>

<span data-ttu-id="c96af-130">只有在成功通過所有測試之後，才可以將 PR 合併到 mrtk_development 中。</span><span class="sxs-lookup"><span data-stu-id="c96af-130">Only after all of the tests have passed successfully can the PR be merged into mrtk_development.</span></span>

### <a name="stress-tests--bulk-tests"></a><span data-ttu-id="c96af-131">壓力測試/大量測試</span><span class="sxs-lookup"><span data-stu-id="c96af-131">Stress tests / bulk tests</span></span>

<span data-ttu-id="c96af-132">有時測試只會偶爾失敗，而這可能會令人挫折地進行調試。</span><span class="sxs-lookup"><span data-stu-id="c96af-132">Sometimes tests will only fail occasionally which can be frustrating to debug.</span></span>

<span data-ttu-id="c96af-133">若要在本機執行多個測試，請修改根據測試腳本。</span><span class="sxs-lookup"><span data-stu-id="c96af-133">To have multiple test runs locally, modify the according test scripts.</span></span> <span data-ttu-id="c96af-134">下列 python 腳本應讓此案例更方便。</span><span class="sxs-lookup"><span data-stu-id="c96af-134">The following python script should make this scenario more convenient.</span></span>

<span data-ttu-id="c96af-135">執行 python 腳本的先決條件是 [安裝 python](https://www.python.org/downloads/)3.x。</span><span class="sxs-lookup"><span data-stu-id="c96af-135">Prerequisite for running the python script is having [Python 3.X installed](https://www.python.org/downloads/).</span></span>

<span data-ttu-id="c96af-136">針對需要多次執行的單一測試：</span><span class="sxs-lookup"><span data-stu-id="c96af-136">For a single test that needs to be executed multiple times:</span></span>

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="c96af-137">建議您從命令列執行下列命令 ([PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6#powershell-coreadd&preserve-view=true)) </span><span class="sxs-lookup"><span data-stu-id="c96af-137">Run the following from a command line ([PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6#powershell-coreadd&preserve-view=true) is recommended)</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

<span data-ttu-id="c96af-138">將輸出複製並貼上至您的測試檔案。</span><span class="sxs-lookup"><span data-stu-id="c96af-138">Copy and paste the output into your test file.</span></span> <span data-ttu-id="c96af-139">下列腳本適用于依序執行多個測試：</span><span class="sxs-lookup"><span data-stu-id="c96af-139">The following script is for running multiple tests in sequence:</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

<span data-ttu-id="c96af-140">新的測試檔案現在應該包含</span><span class="sxs-lookup"><span data-stu-id="c96af-140">The new test file should now contain</span></span>

```c#
[UnityTest]
public IEnumerator A1MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A2MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A3MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A4MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="c96af-141">開啟測試執行器，並觀察現在可以重複呼叫的新測試。</span><span class="sxs-lookup"><span data-stu-id="c96af-141">Open the test runner and observe the new tests that can now be called repeatedly.</span></span>

## <a name="writing-tests"></a><span data-ttu-id="c96af-142">撰寫測試</span><span class="sxs-lookup"><span data-stu-id="c96af-142">Writing tests</span></span>

<span data-ttu-id="c96af-143">有兩種類型的測試可以針對新程式碼新增</span><span class="sxs-lookup"><span data-stu-id="c96af-143">There are two types of tests that can be added for new code</span></span>

* <span data-ttu-id="c96af-144">播放模式測試</span><span class="sxs-lookup"><span data-stu-id="c96af-144">Play mode tests</span></span>
* <span data-ttu-id="c96af-145">編輯模式測試</span><span class="sxs-lookup"><span data-stu-id="c96af-145">Edit mode tests</span></span>

### <a name="play-mode-tests"></a><span data-ttu-id="c96af-146">播放模式測試</span><span class="sxs-lookup"><span data-stu-id="c96af-146">Play mode tests</span></span>

<span data-ttu-id="c96af-147">MRTK 播放模式測試能夠測試您的新功能如何回應不同的輸入來源，例如手或眼睛。</span><span class="sxs-lookup"><span data-stu-id="c96af-147">MRTK play mode tests have the ability to test how your new feature responds to different input sources such as hands or eyes.</span></span>

<span data-ttu-id="c96af-148">新的播放模式測試可以繼承 [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests.BasePlayModeTests) ，或者可以使用下面的基本架構。</span><span class="sxs-lookup"><span data-stu-id="c96af-148">New play mode tests can inherit [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests.BasePlayModeTests) or the skeleton below can be used.</span></span>

<span data-ttu-id="c96af-149">若要建立新的播放模式測試：</span><span class="sxs-lookup"><span data-stu-id="c96af-149">To create a new play mode test:</span></span>

* <span data-ttu-id="c96af-150">流覽至 [資產] > MRTK > 測試 > PlayModeTests</span><span class="sxs-lookup"><span data-stu-id="c96af-150">Navigate to Assets > MRTK > Tests > PlayModeTests</span></span>
* <span data-ttu-id="c96af-151">以滑鼠右鍵按一下，建立 > c # 測試腳本的 > 測試</span><span class="sxs-lookup"><span data-stu-id="c96af-151">Right click, Create > Testing > C# Test Script</span></span>
* <span data-ttu-id="c96af-152">以下列基本架構取代預設範本</span><span class="sxs-lookup"><span data-stu-id="c96af-152">Replace the default template with the skeleton below</span></span>

```c#
#if !WINDOWS_UWP
// When the .NET scripting backend is enabled and C# projects are built
// The assembly that this file is part of is still built for the player,
// even though the assembly itself is marked as a test assembly (this is not
// expected because test assemblies should not be included in player builds).
// Because the .NET backend is deprecated in 2018 and removed in 2019 and this
// issue will likely persist for 2018, this issue is worked around by wrapping all
// play mode tests in this check.

using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using NUnit.Framework;
using System;
using System.Collections;
using System.Linq;
using UnityEngine;
using UnityEngine.TestTools;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class ExamplePlayModeTests
    {
        // This method is called once before we enter play mode and execute any of the tests
        // do any kind of setup here that can't be done in playmode
        public void Setup()
        {
            // eg installing unity packages is only possible in edit mode
            // so if a test requires TextMeshPro we will need to check for the package before entering play mode
            PlayModeTestUtilities.InstallTextMeshProEssentials();
        }

        // Do common setup for each of your tests here - this will be called for each individual test after entering playmode
        // Note that this uses UnitySetUp instead of [SetUp] because the init function needs to await a frame passing
        // to ensure that the MRTK system has had the chance to fully set up before the test runs.
        [UnitySetUp]
        public IEnumerator Init()
        {
            // in most play mode test cases you would want to at least create an MRTK GameObject using the default profile
            TestUtilities.InitializeMixedRealityToolkit(true);
            yield return null;
        }

        // Destroy the scene - this method is called after each test listed below has completed
        // Note that this uses UnityTearDown instead of [TearDown] because the init function needs to await a frame passing
        // to ensure that the MRTK system has fully torn down before the next test setup->run cycle starts.
        [UnityTearDown]
        public IEnumerator TearDown()
        {
            PlayModeTestUtilities.TearDown();
            yield return null;
        }

        #region Tests

        /// <summary>
        /// Skeleton for a new MRTK play mode test.
        /// </summary>
        [UnityTest]
        public IEnumerator TestMyFeature()
        {
            // ----------------------------------------------------------
            // EXAMPLE PLAY MODE TEST METHODS
            // ----------------------------------------------------------
            // Getting the input system
            // var inputSystem = PlayModeTestUtilities.GetInputSystem();

            // Creating a new test hand for input
            // var rightHand = new TestHand(Handedness.Right);
            // yield return rightHand.Show(new Vector3(0, 0, 0.5f));

            // Moving the new test hand
            // We are doing a yield return here because moving the hand to a new position
            // requires multiple frames to complete the action.
            // yield return rightHand.MoveTo(new Vector3(0, 0, 2.0f));

            // Getting a specific pointer from the hand
            // var linePointer = PointerUtils.GetPointer<LinePointer>(Handedness.Right);
            // Assert.IsNotNull(linePointer);
            // ---------------------------------------------------------

            // Your new test here
            yield return null;
        }
        #endregion
    }
}
#endif
```

### <a name="edit-mode-tests"></a><span data-ttu-id="c96af-153">編輯模式測試</span><span class="sxs-lookup"><span data-stu-id="c96af-153">Edit mode tests</span></span>

<span data-ttu-id="c96af-154">編輯模式測試會在 Unity 的編輯模式下執行，而且可以新增在混合現實工具組存放庫的 [ **MRTK**  >  **測試**  >  **EditModeTests** ] 資料夾底下。</span><span class="sxs-lookup"><span data-stu-id="c96af-154">Edit mode tests are executed in Unity's edit mode and can be added under the **MRTK** > **Tests** > **EditModeTests** folder in the Mixed Reality Toolkit repo.</span></span>
<span data-ttu-id="c96af-155">若要建立新的測試，您可以使用下列範本：</span><span class="sxs-lookup"><span data-stu-id="c96af-155">To create a new test the following template can be used:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.

using NUnit.Framework;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class EditModeExampleTest
    {
        [Test]
        /// the name of this method will be used as test name in the unity test runner
        public void TestEditModeExampleFeature()
        {

        }
    }
}
```

### <a name="test-naming-conventions"></a><span data-ttu-id="c96af-156">測試命名慣例</span><span class="sxs-lookup"><span data-stu-id="c96af-156">Test naming conventions</span></span>

<span data-ttu-id="c96af-157">測試通常應該根據測試的類別或它們正在測試的案例來命名。</span><span class="sxs-lookup"><span data-stu-id="c96af-157">Tests should generally be named based on the class they are testing, or the scenario that they are testing.</span></span>
<span data-ttu-id="c96af-158">例如，假設有一個要測試的類別：</span><span class="sxs-lookup"><span data-stu-id="c96af-158">For example, given a to-be-tested class:</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

<span data-ttu-id="c96af-159">考慮為測試命名</span><span class="sxs-lookup"><span data-stu-id="c96af-159">Consider naming the test</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

<span data-ttu-id="c96af-160">請考慮將測試放置在類似于其對應的非測試檔案的資料夾階層中。</span><span class="sxs-lookup"><span data-stu-id="c96af-160">Consider placing the test in a folder hierarchy that is similar to its corresponding non-test file.</span></span>
<span data-ttu-id="c96af-161">例如：</span><span class="sxs-lookup"><span data-stu-id="c96af-161">For example:</span></span>

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

<span data-ttu-id="c96af-162">這是為了確保有明顯的方法可以找出每個類別的對應測試類別（如果有這樣的測試類別的話）。</span><span class="sxs-lookup"><span data-stu-id="c96af-162">This is to ensure that there's a clear an obvious way of finding each class's corresponding test class, if such a test class exists.</span></span>

<span data-ttu-id="c96af-163">以案例為基礎的測試放置較不明確-如果測試演練整體輸入系統，例如，請考慮將它放入對應編輯模式或播放模式測試檔案夾中的 "InputSystem" 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c96af-163">Placement of scenario based tests is less defined - if the test exercises the overall input system, for example, consider putting it into an "InputSystem" folder in the corresponding edit mode or play mode test folder.</span></span>

### <a name="test-script-icons"></a><span data-ttu-id="c96af-164">測試腳本圖示</span><span class="sxs-lookup"><span data-stu-id="c96af-164">Test script icons</span></span>

<span data-ttu-id="c96af-165">新增測試時，請修改腳本，使其具有正確的 MRTK 圖示。</span><span class="sxs-lookup"><span data-stu-id="c96af-165">When adding a new test, please modify the script to have the correct MRTK icon.</span></span> <span data-ttu-id="c96af-166">有一個簡單的 MRTK 工具可以這樣做：</span><span class="sxs-lookup"><span data-stu-id="c96af-166">There's an easy MRTK tool to do so:</span></span>

1. <span data-ttu-id="c96af-167">移至 Mixed Reality 工具組功能表項目</span><span class="sxs-lookup"><span data-stu-id="c96af-167">Go go the Mixed Reality Toolkit menu item</span></span>
1. <span data-ttu-id="c96af-168">依序按一下 [公用程式]、[更新] 和 [圖示]</span><span class="sxs-lookup"><span data-stu-id="c96af-168">Click on Utilities, then Update, then Icons</span></span>
1. <span data-ttu-id="c96af-169">按一下 [測試]，更新程式將會自動執行，並更新任何遺失其圖示的測試腳本</span><span class="sxs-lookup"><span data-stu-id="c96af-169">Click on Tests, and the updater will run automatically, updating any test scripts missing their icons</span></span>

### <a name="mrtk-utility-methods"></a><span data-ttu-id="c96af-170">MRTK 公用程式方法</span><span class="sxs-lookup"><span data-stu-id="c96af-170">MRTK Utility methods</span></span>

<span data-ttu-id="c96af-171">本節說明撰寫 MRTK 的測試時，所使用的一些常用程式碼片段/方法。</span><span class="sxs-lookup"><span data-stu-id="c96af-171">This section shows some of the commonly used code snippets / methods when writing tests for MRTK.</span></span>

<span data-ttu-id="c96af-172">有兩個公用程式類別可協助您在 MRTK 中設定 MRTK 及測試與元件的互動</span><span class="sxs-lookup"><span data-stu-id="c96af-172">There are two Utility classes that help with setting up MRTK and testing interactions with components in MRTK</span></span>

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

<span data-ttu-id="c96af-173">TestUtilities 提供下列方法來設定您的 MRTK 場景和 Gameobject：</span><span class="sxs-lookup"><span data-stu-id="c96af-173">TestUtilities provide the following methods to set up your MRTK scene and GameObjects:</span></span>

```c#
/// creates the mrtk GameObject and sets the default profile if passed param is true
TestUtilities.InitializeMixedRealityToolkit()

/// creates an empty scene prior to adding the mrtk GameObject to it
TestUtilities.InitializeMixedRealityToolkitAndCreateScenes();

/// sets the initial playspace transform and camera position
TestUtilities.InitializePlayspace();

/// destroys previously created mrtk GameObject and playspace
TestUtilities.ShutdownMixedRealityToolkit();
```

<span data-ttu-id="c96af-174">請參閱的 API 檔 [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) 以及 [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) 這些 util 類別的其他方法，因為它們會在新的測試新增至 MRTK 時定期擴充。</span><span class="sxs-lookup"><span data-stu-id="c96af-174">Please refer to the API docs of [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) and [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) for further methods of these util classes as they're extended on a regular basis while new tests get added to MRTK.</span></span>

## <a name="see-also"></a><span data-ttu-id="c96af-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c96af-175">See also</span></span>

* [<span data-ttu-id="c96af-176">檔入口網站產生指南</span><span class="sxs-lookup"><span data-stu-id="c96af-176">Documentation portal generation guide</span></span>](DevDocGuide.md)
