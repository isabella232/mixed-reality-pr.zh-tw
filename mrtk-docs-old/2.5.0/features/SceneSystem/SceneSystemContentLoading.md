---
title: SceneSystemContentLoading
description: 使用 MRTK 載入場景系統的檔
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 3151326fc79c317fa77788992b1591204bd0b0b0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689898"
---
# <a name="content-scene-loading"></a>內容場景載入

所有內容載入作業都是非同步，而且依預設，所有內容載入都是附加的。 管理員和燈光場景永遠不會受到內容載入作業的影響。 如需監視載入進度和場景啟用的相關資訊，請參閱 [監視內容載入](SceneSystemLoadProgress.md)。

## <a name="loading-content"></a>正在載入內容

若要載入內容場景，請使用 `LoadContent` 方法：

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>單一場景載入

您可以透過選擇性引數來達到單一場景負載的對等專案 `mode` 。 `LoadSceneMode.Single` 會先卸載所有載入的內容幕後，再繼續載入。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a>下一個/先前的場景載入

您可以依組建索引的順序來單一載入內容。 這適合用來展示應用程式，讓使用者逐一流覽一組示範場景。

![MRTK_SceneSystemBuildSettings](../Images/SceneSystem/MRTK_SceneSystemBuildSettings.png)

請注意，下一個/上一個內容載入預設會使用 LoadSceneMode，以確保會卸載先前的內容。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

`PrevContentExists` 如果至少有一個內容場景的組建索引較小，但目前載入的組建索引較小，則會傳回 true。 `NextContentExists` 如果至少有一個內容場景具有比目前載入的最高組建索引更高的組建索引，則會傳回 true。

如果 `wrap` 引數為 true，內容將會迴圈回到第一個/最後一個組建索引。 這樣就不需要檢查下一個/先前的內容：

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a>依標記載入

![MRTK_SceneSystemLoadingByTag](../Images/SceneSystem/MRTK_SceneSystemLoadingByTag.png)

有時候，在群組中載入內容場景是很理想的做法。 例如，可能會由多個場景組成體驗的階段，這些都必須同時載入，才能運作。 為了方便此作業，您可以標記場景，然後將其載入，或使用該標記將其卸載。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

如果您想要在不修改腳本的情況下，從體驗中併入/移除專案，則依標記載入也會很有用。 例如，使用下列兩組標記來執行此腳本會產生不同的結果：

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>測試內容

場景名稱 | 場景標記 | 由腳本載入
---|---|---
DebugTerrainPhysics | 地形 | •
StructureTesting | 結構 | •
VegetationTools | 植被 | •
Mountain | 地形 | •
小屋 | 結構 | •
樹木 | 植被 | •

### <a name="final-content"></a>最終內容

場景名稱 | 場景標記 | 由腳本載入
---|---|---
DebugTerrainPhysics | DoNotInclude |
StructureTesting | DoNotInclude |
VegetationTools | DoNotInclude |
Mountain | 地形 | •
小屋 | 結構 | •
樹木 | 植被 | •

---

## <a name="editor-behavior"></a>編輯器行為

您可以使用場景系統的[服務偵測器](../../out-of-scope/MixedRealityConfigurationGuide.md#editor-utilities)，在 [編輯器] 和 [播放] 模式中執行上述所有作業。 在 [編輯] 模式中，場景載入將會立即進行，而在 [播放] 模式中，您可以觀察載入進度和使用 [啟用權杖。](SceneSystemLoadProgress.md)

![MRTK_SceneSystemServiceInspector](../Images/SceneSystem/MRTK_SceneSystemServiceInspector.PNG)
