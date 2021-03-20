---
title: ExperimentalFeatures
description: 與 MRTK 中的實驗性功能相關的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 75ec992cb2b7cbce79269af2c69f5ae9cc474d33
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684391"
---
# <a name="experimental-features"></a>實驗性功能

MRTK 小組所處理的某些功能似乎有許多初始值，即使我們尚未完全增補詳細資料。 針對這些類型的功能，我們想要讓該社區提早看到它們。 因為它們是在迴圈初期進行，所以我們會將它們標示為實驗性，以表示它們仍在不斷演進，且可能隨著時間變更。

## <a name="what-to-expect-from-an-experimental-feature"></a>實驗性功能的期望

如果元件標示為實驗性，您可以預期會有下列各項：

- 示範使用方式的範例場景，位於 `MRTK/Examples/Experimental` 子資料夾下
- 實驗性功能可能沒有檔。
- 他們可能沒有測試。
- 實驗性功能可能會變更。

## <a name="experimental-feature-guidelines"></a>實驗性功能指導方針

### <a name="experimental-code-should-live-in-a-separate-folder"></a>實驗性程式碼應該存留在不同的資料夾中

實驗性程式碼應進入最上層實驗資料夾，後面接著實驗功能名稱。 例如，如果嘗試貢獻新的功能 FooBar，請將程式碼放在下列程式碼中：

- 範例場景，腳本進入 `MRTK/Examples/Experimental/FooBar/`
- 元件腳本，prefabs 進入 `MRTK/SDK/Experimental/FooBar/`
- 元件偵測器進入 `MRTK/SDK/Inspectors/Experimental/FooBar`

使用實驗性功能名稱下的子資料夾時，請嘗試鏡像相同的 MRTK 資料夾結構。

例如，解析器會進入 `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`

將場景保存在靠近頂端的場景資料夾中： `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`

> [!NOTE]
> 我們認為沒有單一的實驗根資料夾，而是在假設下進行實驗 `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` 。 我們決定將資料夾放在基底，讓實驗性功能更容易探索。

### <a name="experimental-code-should-be-in-a-special-namespace"></a>實驗性程式碼應該在特殊命名空間中

確定實驗性程式碼存在於符合非實驗性位置的實驗性命名空間中。 例如，如果您的元件是解析器的一部分 `Microsoft.MixedReality.Toolkit.Utilities.Solvers` ，則其命名空間應該是 `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` 。

如需範例，請參閱 [此 PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) 。

### <a name="experimental-features-should-have-an-experimental-attribute"></a>實驗性功能應該要有 [實驗性] 屬性

將 `[Experimental]` 屬性新增至您的其中一個欄位上方，在元件編輯器中會出現一個小對話方塊，提及您的功能是實驗性的，並且受限於重大變更。

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>實驗性功能的功能表應該會在 [實驗性] 子功能表下

將命令新增至編輯器中的功能表時，請確定實驗性功能位於 [實驗性] 子功能表。 以下是一些範例：

新增最上層的功能表命令：

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

新增元件功能表：

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>文件

請遵循下列步驟來新增實驗性功能的檔：

1. 實驗性功能的任何檔都應該放在 `README.md` 實驗資料夾的檔案中。 例如： [`MRTK/SDK/Experimental/ScrollingObjectCollection/README.md`](../reference-docs/README.md) 。

1. 在 [ *功能概述* ] 下的 [ *實驗* ] 區段中，新增連結 [`Documentation/toc.yml`](../toc.yml) 。

### <a name="minimize-impact-to-mrtk-code"></a>將對 MRTK 程式碼的影響降至最低

雖然您的 MRTK 變更可能會讓實驗正常運作，但可能會以您預期的方式影響其他人。
您對 MRTK core 程式碼所做的任何回歸都會導致您的提取要求獲得還原。

在實驗資料夾以外的資料夾中，目標不會有任何變更。 以下是可以進行實驗性變更的資料夾清單：

- MRTK/SDK/實驗性
- MRTK/SDK/檢查器/實驗性
- MRTK/範例/實驗性

這些資料夾外部的變更應謹慎處理。 如果您的實驗性功能必須包含 MRTK core 程式碼的變更，請考慮將 MRTK 變更分割成包含測試和檔的個別提取要求。

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>使用您的實驗性功能不應該影響人們使用核心控制項的能力

大部分的人都經常使用核心 UX 元件，例如按鈕、ManipulationHandler 和互動。 如果防止它們使用按鈕，它們可能不會使用您的實驗性功能。

使用您的元件不應中斷按鈕、ManipulationHandler、BoundingBox 或互動。

例如，在 [此 SCROLLABLEOBJECTCOLLECTION PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)中，新增 ScrollableObjectCollection 會導致人員無法使用 HoloLens 按鈕 prefabs。 雖然這不是因為 PR 中的 bug 所造成 (，而是公開現有的錯誤) ，但是它會使 PR 無法進入簽入狀態。

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>提供示範如何使用此功能的範例場景

人們必須瞭解如何使用您的功能，以及如何進行測試。

在 MRTK/範例/實驗/YOUR_FEATURE 下提供範例

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>在實驗性功能中將使用者可見的瑕疵降至最低

如果沒有，則不會使用實驗性功能，而不會將它畢業至某項功能。

在您的目標平臺上測試範例場景，並確定其如預期般運作。 確定您的功能也可在編輯器中運作，讓使用者可以快速地逐一查看您的功能，即使它們沒有目標平臺也一樣。

## <a name="graduating-experimental-code-into-mrtk-code"></a>將實驗性程式碼即將畢業至 MRTK 程式碼

如果功能最終看到很多用途，則應該將它畢業至核心 MRTK 程式碼。 若要這樣做，此功能應該具有測試、檔和範例場景。

當您準備好畢業功能 MRTK 時，請建立一個問題，以簽入您的 PR。 PR 應包括將這項功能設為核心功能所需的所有專案：測試、檔，以及顯示使用方式的範例場景。

此外，別忘了更新命名空間，以移除「實驗性」子空間。
