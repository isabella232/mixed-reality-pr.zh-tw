---
title: UnitTests
description: '>--run-unittests 以檢查 MRTK 的可靠性」。'
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、UnitTest、
ms.openlocfilehash: 1a09406eac09a2905bce1b9a7b9d0987a49905d0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683451"
---
# <a name="writing-and-running-tests-in-mrtk"></a>在 MRTK 中撰寫和執行測試

為了確保 MRTK 可靠，MRTK 有一組測試，以確保程式碼的變更不會回歸現有的行為。 在大型程式碼基底（例如 MRTK）中提供良好的測試涵蓋範圍，對穩定性很重要，並且在進行變更時具有自信。

MRTK 會使用 [unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) ，其使用 [NUnit](https://nunit.org/)的 unity 整合。 本指南將提供如何將測試新增至 MRTK 的起點。 它不會說明 [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 和 [NUnit](https://nunit.org/) ，可在提供的連結中查閱。

提交提取要求之前，請務必：

1. 在本機執行測試，讓您的變更不會回歸現有的行為 (完成 Pr 時，如果有任何測試) 失敗，則不允許。

1. 如果要修正錯誤，請撰寫測試來測試修正程式，並確定未來的程式碼修改不會再中斷。

1. 如果要撰寫功能，請撰寫新的測試，以防止即將進行的程式碼變更中斷這項功能。

目前 playmode 的測試是要在 Unity 2018.4 中執行，而其他版本的 Unity 可能會失敗

## <a name="running-tests"></a>執行測試

### <a name="unity-editor"></a>Unity 編輯器

[Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html)可在 [視窗一般 **]**  >    >  **Test Runner** 下找到，並會顯示所有可用的 MRTK 播放和編輯模式測試。

### <a name="command-line"></a>命令列

測試也可以透過位於的 [powershell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6add&preserve-view=true) 腳本來執行 `Scripts\test\run_playmode_tests.ps1` 。 這會執行 playmode 測試，就如同在 github/CI 上執行一樣 (請參閱下面) ，並列印結果。 以下是一些如何執行腳本的範例

在位於 H:\mrtk.dev 的專案上執行測試，並使用 Unity 2018.4 (例如 Unity 2018.4.26 f1) 

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

在位於 H:\mrtk.dev、Unity 2018.4 的專案上執行測試，並將結果輸出至 C：\ playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

您也可以透過腳本多次執行 playmode 測試 `run_repeat_tests.ps1` 。 中使用的所有參數都可以 `run_playmode_tests.ps1` 使用。

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>提取要求驗證

MRTK 的 CI 將會建立所有設定的 MRTK，並執行所有的編輯和播放模式測試。 如果使用者有足夠的許可權，就可以藉由在 github PR 上張貼批註來觸發 CI `/azp run mrtk_pr` 。 CI 執行可在 PR 的 [檢查] 索引標籤中看到。

只有在成功通過所有測試之後，才可以將 PR 合併到 mrtk_development 中。

### <a name="stress-tests--bulk-tests"></a>壓力測試/大量測試

有時測試只會偶爾失敗，而這可能會令人挫折地進行調試。

若要在本機執行多個測試，請修改根據測試腳本。 下列 python 腳本應讓此案例更方便。

執行 python 腳本的先決條件是 [安裝 python](https://www.python.org/downloads/)3.x。

針對需要多次執行的單一測試：

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

建議您從命令列執行下列命令 ([PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-powershell?view=powershell-6#powershell-coreadd&preserve-view=true)) 

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

將輸出複製並貼上至您的測試檔案。 下列腳本適用于依序執行多個測試：

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

新的測試檔案現在應該包含

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

開啟測試執行器，並觀察現在可以重複呼叫的新測試。

## <a name="writing-tests"></a>撰寫測試

有兩種類型的測試可以針對新程式碼新增

* 播放模式測試
* 編輯模式測試

### <a name="play-mode-tests"></a>播放模式測試

MRTK 播放模式測試能夠測試您的新功能如何回應不同的輸入來源，例如手或眼睛。

新的播放模式測試可以繼承 [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests.BasePlayModeTests) ，或者可以使用下面的基本架構。

若要建立新的播放模式測試：

* 流覽至 [資產] > MRTK > 測試 > PlayModeTests
* 以滑鼠右鍵按一下，建立 > c # 測試腳本的 > 測試
* 以下列基本架構取代預設範本

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

### <a name="edit-mode-tests"></a>編輯模式測試

編輯模式測試會在 Unity 的編輯模式下執行，而且可以新增在混合現實工具組存放庫的 [ **MRTK**  >  **測試**  >  **EditModeTests** ] 資料夾底下。
若要建立新的測試，您可以使用下列範本：

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

### <a name="test-naming-conventions"></a>測試命名慣例

測試通常應該根據測試的類別或它們正在測試的案例來命名。
例如，假設有一個要測試的類別：

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

考慮為測試命名

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

請考慮將測試放置在類似于其對應的非測試檔案的資料夾階層中。
例如：

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

這是為了確保有明顯的方法可以找出每個類別的對應測試類別（如果有這樣的測試類別的話）。

以案例為基礎的測試放置較不明確-如果測試演練整體輸入系統，例如，請考慮將它放入對應編輯模式或播放模式測試檔案夾中的 "InputSystem" 資料夾。

### <a name="test-script-icons"></a>測試腳本圖示

新增測試時，請修改腳本，使其具有正確的 MRTK 圖示。 有一個簡單的 MRTK 工具可以這樣做：

1. 移至 Mixed Reality 工具組功能表項目
1. 依序按一下 [公用程式]、[更新] 和 [圖示]
1. 按一下 [測試]，更新程式將會自動執行，並更新任何遺失其圖示的測試腳本

### <a name="mrtk-utility-methods"></a>MRTK 公用程式方法

本節說明撰寫 MRTK 的測試時，所使用的一些常用程式碼片段/方法。

有兩個公用程式類別可協助您在 MRTK 中設定 MRTK 及測試與元件的互動

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities 提供下列方法來設定您的 MRTK 場景和 Gameobject：

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

請參閱的 API 檔 [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) 以及 [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) 這些 util 類別的其他方法，因為它們會在新的測試新增至 MRTK 時定期擴充。

## <a name="see-also"></a>另請參閱

* [檔入口網站產生指南](DevDocGuide.md)
