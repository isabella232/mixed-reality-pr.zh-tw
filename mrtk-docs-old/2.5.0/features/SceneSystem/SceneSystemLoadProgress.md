---
title: SceneSystemLoadProgress
description: 在 MRTK 中進行幕後內容載入的檔
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: d54349461583241d19f260964528786e58baf54d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689838"
---
# <a name="monitoring-content-loading"></a><span data-ttu-id="61189-104">監視內容載入</span><span class="sxs-lookup"><span data-stu-id="61189-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="61189-105">場景作業進度</span><span class="sxs-lookup"><span data-stu-id="61189-105">Scene operation progress</span></span>

<span data-ttu-id="61189-106">載入或卸載內容時， `SceneOperationInProgress` 屬性會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="61189-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="61189-107">您可以透過屬性監視此作業的進度 `SceneOperationProgress` 。</span><span class="sxs-lookup"><span data-stu-id="61189-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="61189-108">此 `SceneOperationProgress` 值為所有目前非同步場景作業的平均值。</span><span class="sxs-lookup"><span data-stu-id="61189-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="61189-109">在內容載入開始時，將會 `SceneOperationProgress` 是零。</span><span class="sxs-lookup"><span data-stu-id="61189-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="61189-110">一旦完全完成， `SceneOperationProgress` 將會設定為1，而且會維持為1，直到下一個作業發生為止。</span><span class="sxs-lookup"><span data-stu-id="61189-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="61189-111">請注意，只有內容場景作業會影響這些屬性。</span><span class="sxs-lookup"><span data-stu-id="61189-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="61189-112">這些屬性會反映從開始到完成的 *整個* 作業的狀態，即使該作業包含多個步驟：</span><span class="sxs-lookup"><span data-stu-id="61189-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// First do an additive scene load
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
await sceneSystem.LoadContent("ContentScene1");

// Now do a single scene load
// This will result in two actions back-to-back
// First "ContentScene1" will be unloaded
// Then "ContentScene2" will be loaded
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
sceneSystem.LoadContent("ContentScene2", LoadSceneMode.Single)
```

### <a name="progress-examples"></a><span data-ttu-id="61189-113">進度範例</span><span class="sxs-lookup"><span data-stu-id="61189-113">Progress examples</span></span>

<span data-ttu-id="61189-114">`SceneOperationInProgress` 如果活動應該在載入內容時暫停，則會很有用：</span><span class="sxs-lookup"><span data-stu-id="61189-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

```c#
public class FooManager : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        // Don't update foos while a scene operation is in progress
        if (sceneSystem.SceneOperationInProgress)
        {
            return;
        }

        // Update foos
        ...
    }
    ...
}
```

<span data-ttu-id="61189-115">`SceneOperationProgress` 可以用來顯示進度對話方塊：</span><span class="sxs-lookup"><span data-stu-id="61189-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        if (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
        }
        else
        {
            HideProgressIndicator();
        }
    }
    ...
}
```

---

## <a name="monitoring-with-actions"></a><span data-ttu-id="61189-116">使用動作進行監視</span><span class="sxs-lookup"><span data-stu-id="61189-116">Monitoring with actions</span></span>

<span data-ttu-id="61189-117">場景系統提供數個動作，讓您知道載入或卸載場景的時機。</span><span class="sxs-lookup"><span data-stu-id="61189-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="61189-118">每個動作都會轉送受影響場景的名稱。</span><span class="sxs-lookup"><span data-stu-id="61189-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="61189-119">如果載入或卸載作業牽涉到多個場景，則會針對每個受影響的場景叫用一次相關的動作。</span><span class="sxs-lookup"><span data-stu-id="61189-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="61189-120">當載入或卸載作業 *完全完成* 時，也會一次叫用它們。</span><span class="sxs-lookup"><span data-stu-id="61189-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="61189-121">基於這個理由，建議您使用 *OnWillUnload* 動作來偵測要終結的內容， *而不是* 使用 *OnUnloaded* 動作來偵測事實之後的損毀內容。</span><span class="sxs-lookup"><span data-stu-id="61189-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="61189-122">在反轉端，因為只有在所有場景都已啟動且完全載入時，才會叫用 *OnLoaded* 動作，而使用 *OnLoaded* 動作來偵測和使用新的內容保證是安全的。</span><span class="sxs-lookup"><span data-stu-id="61189-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="61189-123">動作</span><span class="sxs-lookup"><span data-stu-id="61189-123">Action</span></span> | <span data-ttu-id="61189-124">叫用時</span><span class="sxs-lookup"><span data-stu-id="61189-124">When it's invoked</span></span> | <span data-ttu-id="61189-125">內容場景</span><span class="sxs-lookup"><span data-stu-id="61189-125">Content Scenes</span></span> | <span data-ttu-id="61189-126">燈光場景</span><span class="sxs-lookup"><span data-stu-id="61189-126">Lighting Scenes</span></span> | <span data-ttu-id="61189-127">管理員場景</span><span class="sxs-lookup"><span data-stu-id="61189-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="61189-128">緊接在內容場景載入之前</span><span class="sxs-lookup"><span data-stu-id="61189-128">Just prior to a content scene load</span></span> | <span data-ttu-id="61189-129">•</span><span class="sxs-lookup"><span data-stu-id="61189-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="61189-130">在載入作業中的所有內容幕後都已完全載入並啟用</span><span class="sxs-lookup"><span data-stu-id="61189-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="61189-131">•</span><span class="sxs-lookup"><span data-stu-id="61189-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="61189-132">在內容場景卸載操作之前</span><span class="sxs-lookup"><span data-stu-id="61189-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="61189-133">•</span><span class="sxs-lookup"><span data-stu-id="61189-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="61189-134">在卸載作業中的所有內容幕後全部卸載之後</span><span class="sxs-lookup"><span data-stu-id="61189-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="61189-135">•</span><span class="sxs-lookup"><span data-stu-id="61189-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="61189-136">緊接在照明場景載入之前</span><span class="sxs-lookup"><span data-stu-id="61189-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="61189-137">•</span><span class="sxs-lookup"><span data-stu-id="61189-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="61189-138">在完整載入並啟用光源場景之後</span><span class="sxs-lookup"><span data-stu-id="61189-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="61189-139">•</span><span class="sxs-lookup"><span data-stu-id="61189-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="61189-140">在光線場景卸載之前</span><span class="sxs-lookup"><span data-stu-id="61189-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="61189-141">•</span><span class="sxs-lookup"><span data-stu-id="61189-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="61189-142">完整卸載燈光場景之後</span><span class="sxs-lookup"><span data-stu-id="61189-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="61189-143">•</span><span class="sxs-lookup"><span data-stu-id="61189-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="61189-144">正好在場景載入之前</span><span class="sxs-lookup"><span data-stu-id="61189-144">Just prior to a scene load</span></span> | <span data-ttu-id="61189-145">•</span><span class="sxs-lookup"><span data-stu-id="61189-145">•</span></span> | <span data-ttu-id="61189-146">•</span><span class="sxs-lookup"><span data-stu-id="61189-146">•</span></span> | <span data-ttu-id="61189-147">•</span><span class="sxs-lookup"><span data-stu-id="61189-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="61189-148">在作業中的所有場景都已完全載入並啟用之後</span><span class="sxs-lookup"><span data-stu-id="61189-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="61189-149">•</span><span class="sxs-lookup"><span data-stu-id="61189-149">•</span></span> | <span data-ttu-id="61189-150">•</span><span class="sxs-lookup"><span data-stu-id="61189-150">•</span></span> | <span data-ttu-id="61189-151">•</span><span class="sxs-lookup"><span data-stu-id="61189-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="61189-152">在場景卸載之前</span><span class="sxs-lookup"><span data-stu-id="61189-152">Just prior to a scene unload</span></span> | <span data-ttu-id="61189-153">•</span><span class="sxs-lookup"><span data-stu-id="61189-153">•</span></span> | <span data-ttu-id="61189-154">•</span><span class="sxs-lookup"><span data-stu-id="61189-154">•</span></span> | <span data-ttu-id="61189-155">•</span><span class="sxs-lookup"><span data-stu-id="61189-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="61189-156">完整卸載場景之後</span><span class="sxs-lookup"><span data-stu-id="61189-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="61189-157">•</span><span class="sxs-lookup"><span data-stu-id="61189-157">•</span></span> | <span data-ttu-id="61189-158">•</span><span class="sxs-lookup"><span data-stu-id="61189-158">•</span></span> | <span data-ttu-id="61189-159">•</span><span class="sxs-lookup"><span data-stu-id="61189-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="61189-160">動作範例</span><span class="sxs-lookup"><span data-stu-id="61189-160">Action examples</span></span>

<span data-ttu-id="61189-161">使用動作和協同程式而非 Update 的另一個進度對話方塊範例：</span><span class="sxs-lookup"><span data-stu-id="61189-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private bool displayingProgress = false;

    private void Start()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
        sceneSystem.OnWillLoadContent += HandleSceneOperation;
        sceneSystem.OnWillUnloadContent += HandleSceneOperation;
    }

    private void HandleSceneOperation (string sceneName)
    {
        // This may be invoked multiple times per frame - once per scene being loaded or unloaded.
        // So filter the events appropriately.
        if (displayingProgress)
        {
            return;
        }

        displayingProgress = true;
        StartCoroutine(DisplayProgress());
    }

    private IEnumerator DisplayProgress()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        while (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
            yield return null;
        }

        HideProgressIndicator();
        displayingProgress = false;
    }

    ...
}
```

---

## <a name="controlling-scene-activation"></a><span data-ttu-id="61189-162">控制場景啟用</span><span class="sxs-lookup"><span data-stu-id="61189-162">Controlling scene activation</span></span>

<span data-ttu-id="61189-163">依預設，內容幕後會設定為 [已載入時啟動]。</span><span class="sxs-lookup"><span data-stu-id="61189-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="61189-164">如果您想要手動控制場景啟用，可以將傳遞 `SceneActivationToken` 給任何內容載入方法。</span><span class="sxs-lookup"><span data-stu-id="61189-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="61189-165">如果單一作業正在載入多個內容場景，此啟用權杖將會套用至所有場景。</span><span class="sxs-lookup"><span data-stu-id="61189-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

SceneActivationToken activationToken = new SceneActivationToken();

// Load the content and pass the activation token
sceneSystem.LoadContent(new string[] { "ContentScene1", "ContentScene2", "ContentScene3" }, LoadSceneMode.Additive, activationToken);

// Wait until all users have joined the experience
while (!AllUsersHaveJoinedExperience())
{
    await Task.Yield();
}

// Let scene system know we're ready to activate all scenes
activationToken.AllowSceneActivation = true;

// Wait for all scenes to be fully loaded and activated
while (sceneSystem.SceneOperationInProgress)
{
    await Task.Yield();
}

// Proceed with experience
```

---

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="61189-166">正在檢查載入的內容</span><span class="sxs-lookup"><span data-stu-id="61189-166">Checking which content is loaded</span></span>

<span data-ttu-id="61189-167">屬性會依 `ContentSceneNames` 組建索引的順序提供可用內容幕後的陣列。</span><span class="sxs-lookup"><span data-stu-id="61189-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="61189-168">您可以檢查是否透過載入這些幕後 `IsContentLoaded(string contentName)` 。</span><span class="sxs-lookup"><span data-stu-id="61189-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
