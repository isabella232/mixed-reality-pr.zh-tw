---
title: SceneSystemContentLoading
description: 使用 MRTK 載入場景系統的檔
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: de5a7e155a4c993ad128e4b3ab3fb46ea0873c1c
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690538"
---
# <a name="content-scene-loading"></a><span data-ttu-id="720b2-104">內容場景載入</span><span class="sxs-lookup"><span data-stu-id="720b2-104">Content scene loading</span></span>

<span data-ttu-id="720b2-105">所有內容載入作業都是非同步，而且依預設，所有內容載入都是附加的。</span><span class="sxs-lookup"><span data-stu-id="720b2-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="720b2-106">管理員和燈光場景永遠不會受到內容載入作業的影響。</span><span class="sxs-lookup"><span data-stu-id="720b2-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="720b2-107">如需監視載入進度和場景啟用的相關資訊，請參閱 [監視內容載入](SceneSystemLoadProgress.md)。</span><span class="sxs-lookup"><span data-stu-id="720b2-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](SceneSystemLoadProgress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="720b2-108">正在載入內容</span><span class="sxs-lookup"><span data-stu-id="720b2-108">Loading content</span></span>

<span data-ttu-id="720b2-109">若要載入內容場景，請使用 `LoadContent` 方法：</span><span class="sxs-lookup"><span data-stu-id="720b2-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="720b2-110">單一場景載入</span><span class="sxs-lookup"><span data-stu-id="720b2-110">Single scene loading</span></span>

<span data-ttu-id="720b2-111">您可以透過選擇性引數來達到單一場景負載的對等專案 `mode` 。</span><span class="sxs-lookup"><span data-stu-id="720b2-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="720b2-112">`LoadSceneMode.Single` 會先卸載所有載入的內容幕後，再繼續載入。</span><span class="sxs-lookup"><span data-stu-id="720b2-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

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

## <a name="next--previous-scene-loading"></a><span data-ttu-id="720b2-113">下一個/先前的場景載入</span><span class="sxs-lookup"><span data-stu-id="720b2-113">Next / previous scene loading</span></span>

<span data-ttu-id="720b2-114">您可以依組建索引的順序來單一載入內容。</span><span class="sxs-lookup"><span data-stu-id="720b2-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="720b2-115">這適合用來展示應用程式，讓使用者逐一流覽一組示範場景。</span><span class="sxs-lookup"><span data-stu-id="720b2-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![MRTK_SceneSystemBuildSettings 映射](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="720b2-117">請注意，下一個/上一個內容載入預設會使用 LoadSceneMode，以確保會卸載先前的內容。</span><span class="sxs-lookup"><span data-stu-id="720b2-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

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

<span data-ttu-id="720b2-118">`PrevContentExists` 如果至少有一個內容場景的組建索引較小，但目前載入的組建索引較小，則會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="720b2-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="720b2-119">`NextContentExists` 如果至少有一個內容場景具有比目前載入的最高組建索引更高的組建索引，則會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="720b2-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="720b2-120">如果 `wrap` 引數為 true，內容將會迴圈回到第一個/最後一個組建索引。</span><span class="sxs-lookup"><span data-stu-id="720b2-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="720b2-121">這樣就不需要檢查下一個/先前的內容：</span><span class="sxs-lookup"><span data-stu-id="720b2-121">This removes the need to check for next / previous content:</span></span>

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

## <a name="loading-by-tag"></a><span data-ttu-id="720b2-122">依標記載入</span><span class="sxs-lookup"><span data-stu-id="720b2-122">Loading by tag</span></span>

![MRTK_SceneSystemLoadingByTag 映射](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="720b2-124">有時候，在群組中載入內容場景是很理想的做法。</span><span class="sxs-lookup"><span data-stu-id="720b2-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="720b2-125">例如，可能會由多個場景組成體驗的階段，這些都必須同時載入，才能運作。</span><span class="sxs-lookup"><span data-stu-id="720b2-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="720b2-126">為了方便此作業，您可以標記場景，然後將其載入，或使用該標記將其卸載。</span><span class="sxs-lookup"><span data-stu-id="720b2-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="720b2-127">如果您想要在不修改腳本的情況下，從體驗中併入/移除專案，則依標記載入也會很有用。</span><span class="sxs-lookup"><span data-stu-id="720b2-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="720b2-128">例如，使用下列兩組標記來執行此腳本會產生不同的結果：</span><span class="sxs-lookup"><span data-stu-id="720b2-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="720b2-129">測試內容</span><span class="sxs-lookup"><span data-stu-id="720b2-129">Testing content</span></span>

<span data-ttu-id="720b2-130">場景名稱</span><span class="sxs-lookup"><span data-stu-id="720b2-130">Scene Name</span></span> | <span data-ttu-id="720b2-131">場景標記</span><span class="sxs-lookup"><span data-stu-id="720b2-131">Scene Tag</span></span> | <span data-ttu-id="720b2-132">由腳本載入</span><span class="sxs-lookup"><span data-stu-id="720b2-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="720b2-133">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="720b2-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="720b2-134">地形</span><span class="sxs-lookup"><span data-stu-id="720b2-134">Terrain</span></span> | <span data-ttu-id="720b2-135">•</span><span class="sxs-lookup"><span data-stu-id="720b2-135">•</span></span>
<span data-ttu-id="720b2-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="720b2-136">StructureTesting</span></span> | <span data-ttu-id="720b2-137">結構</span><span class="sxs-lookup"><span data-stu-id="720b2-137">Structures</span></span> | <span data-ttu-id="720b2-138">•</span><span class="sxs-lookup"><span data-stu-id="720b2-138">•</span></span>
<span data-ttu-id="720b2-139">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="720b2-139">VegetationTools</span></span> | <span data-ttu-id="720b2-140">植被</span><span class="sxs-lookup"><span data-stu-id="720b2-140">Vegetation</span></span> | <span data-ttu-id="720b2-141">•</span><span class="sxs-lookup"><span data-stu-id="720b2-141">•</span></span>
<span data-ttu-id="720b2-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="720b2-142">Mountain</span></span> | <span data-ttu-id="720b2-143">地形</span><span class="sxs-lookup"><span data-stu-id="720b2-143">Terrain</span></span> | <span data-ttu-id="720b2-144">•</span><span class="sxs-lookup"><span data-stu-id="720b2-144">•</span></span>
<span data-ttu-id="720b2-145">小屋</span><span class="sxs-lookup"><span data-stu-id="720b2-145">Cabin</span></span> | <span data-ttu-id="720b2-146">結構</span><span class="sxs-lookup"><span data-stu-id="720b2-146">Structures</span></span> | <span data-ttu-id="720b2-147">•</span><span class="sxs-lookup"><span data-stu-id="720b2-147">•</span></span>
<span data-ttu-id="720b2-148">樹木</span><span class="sxs-lookup"><span data-stu-id="720b2-148">Trees</span></span> | <span data-ttu-id="720b2-149">植被</span><span class="sxs-lookup"><span data-stu-id="720b2-149">Vegetation</span></span> | <span data-ttu-id="720b2-150">•</span><span class="sxs-lookup"><span data-stu-id="720b2-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="720b2-151">最終內容</span><span class="sxs-lookup"><span data-stu-id="720b2-151">Final content</span></span>

<span data-ttu-id="720b2-152">場景名稱</span><span class="sxs-lookup"><span data-stu-id="720b2-152">Scene Name</span></span> | <span data-ttu-id="720b2-153">場景標記</span><span class="sxs-lookup"><span data-stu-id="720b2-153">Scene Tag</span></span> | <span data-ttu-id="720b2-154">由腳本載入</span><span class="sxs-lookup"><span data-stu-id="720b2-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="720b2-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="720b2-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="720b2-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="720b2-156">DoNotInclude</span></span> |
<span data-ttu-id="720b2-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="720b2-157">StructureTesting</span></span> | <span data-ttu-id="720b2-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="720b2-158">DoNotInclude</span></span> |
<span data-ttu-id="720b2-159">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="720b2-159">VegetationTools</span></span> | <span data-ttu-id="720b2-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="720b2-160">DoNotInclude</span></span> |
<span data-ttu-id="720b2-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="720b2-161">Mountain</span></span> | <span data-ttu-id="720b2-162">地形</span><span class="sxs-lookup"><span data-stu-id="720b2-162">Terrain</span></span> | <span data-ttu-id="720b2-163">•</span><span class="sxs-lookup"><span data-stu-id="720b2-163">•</span></span>
<span data-ttu-id="720b2-164">小屋</span><span class="sxs-lookup"><span data-stu-id="720b2-164">Cabin</span></span> | <span data-ttu-id="720b2-165">結構</span><span class="sxs-lookup"><span data-stu-id="720b2-165">Structures</span></span> | <span data-ttu-id="720b2-166">•</span><span class="sxs-lookup"><span data-stu-id="720b2-166">•</span></span>
<span data-ttu-id="720b2-167">樹木</span><span class="sxs-lookup"><span data-stu-id="720b2-167">Trees</span></span> | <span data-ttu-id="720b2-168">植被</span><span class="sxs-lookup"><span data-stu-id="720b2-168">Vegetation</span></span> | <span data-ttu-id="720b2-169">•</span><span class="sxs-lookup"><span data-stu-id="720b2-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="720b2-170">編輯器行為</span><span class="sxs-lookup"><span data-stu-id="720b2-170">Editor behavior</span></span>

<span data-ttu-id="720b2-171">您可以使用場景系統的[服務偵測器](../../configuration/MixedRealityConfigurationGuide.md#editor-utilities)，在 [編輯器] 和 [播放] 模式中執行上述所有作業。</span><span class="sxs-lookup"><span data-stu-id="720b2-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/MixedRealityConfigurationGuide.md#editor-utilities)</span></span> <span data-ttu-id="720b2-172">在 [編輯] 模式中，場景載入將會立即進行，而在 [播放] 模式中，您可以觀察載入進度和使用 [啟用權杖。](SceneSystemLoadProgress.md)</span><span class="sxs-lookup"><span data-stu-id="720b2-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](SceneSystemLoadProgress.md)</span></span>

![MRTK_SceneSystemServiceInspector 映射](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
