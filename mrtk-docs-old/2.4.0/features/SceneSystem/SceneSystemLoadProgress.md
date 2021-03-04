---
title: SceneSystemLoadProgress
description: 在 MRTK 中進行幕後內容載入的檔
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: ec0b82a0393b6129d5b4c6fe562845234c52eb44
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780341"
---
# <a name="monitoring-content-loading"></a>監視內容載入

## <a name="scene-operation-progress"></a>場景作業進度

載入或卸載內容時， `SceneOperationInProgress` 屬性會傳回 true。 您可以透過屬性監視此作業的進度 `SceneOperationProgress` 。

此 `SceneOperationProgress` 值為所有目前非同步場景作業的平均值。 在內容載入開始時，將會 `SceneOperationProgress` 是零。 一旦完全完成， `SceneOperationProgress` 將會設定為1，而且會維持為1，直到下一個作業發生為止。 請注意，只有內容場景作業會影響這些屬性。

這些屬性會反映從開始到完成的 *整個* 作業的狀態，即使該作業包含多個步驟：

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

### <a name="progress-examples"></a>進度範例

`SceneOperationInProgress` 如果活動應該在載入內容時暫停，則會很有用：

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

`SceneOperationProgress` 可以用來顯示進度對話方塊：

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

## <a name="monitoring-with-actions"></a>使用動作進行監視

場景系統提供數個動作，讓您知道載入或卸載場景的時機。 每個動作都會轉送受影響場景的名稱。

如果載入或卸載作業牽涉到多個場景，則會針對每個受影響的場景叫用一次相關的動作。 當載入或卸載作業 *完全完成* 時，也會一次叫用它們。 基於這個理由，建議您使用 *OnWillUnload* 動作來偵測要終結的內容， *而不是* 使用 *OnUnloaded* 動作來偵測事實之後的損毀內容。

在反轉端，因為只有在所有場景都已啟動且完全載入時，才會叫用 *OnLoaded* 動作，而使用 *OnLoaded* 動作來偵測和使用新的內容保證是安全的。

動作 | 叫用時 | 內容場景 | 燈光場景 | 管理員場景
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | 緊接在內容場景載入之前 | • | |  
`OnContentLoaded` | 在載入作業中的所有內容幕後都已完全載入並啟用 | • | |
`OnWillUnloadContent` | 在內容場景卸載操作之前 | • | |
`OnContentUnloaded` | 在卸載作業中的所有內容幕後全部卸載之後 | • | |
`OnWillLoadLighting` | 緊接在照明場景載入之前 | | • |
`OnLightingLoaded` | 在完整載入並啟用光源場景之後| | • |
`OnWillUnloadLighting` | 在光線場景卸載之前 | | • |
`OnLightingUnloaded` | 完整卸載燈光場景之後 | | • |
`OnWillLoadScene` | 正好在場景載入之前 | • | • | •
`OnSceneLoaded` | 在作業中的所有場景都已完全載入並啟用之後 | • | • | •
`OnWillUnloadScene` | 在場景卸載之前 | • | • | •
`OnSceneUnloaded` | 完整卸載場景之後 |  • | • | •

### <a name="action-examples"></a>動作範例

使用動作和協同程式而非 Update 的另一個進度對話方塊範例：

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

## <a name="controlling-scene-activation"></a>控制場景啟用

依預設，內容幕後會設定為 [已載入時啟動]。 如果您想要手動控制場景啟用，可以將傳遞 `SceneActivationToken` 給任何內容載入方法。 如果單一作業正在載入多個內容場景，此啟用權杖將會套用至所有場景。

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

## <a name="checking-which-content-is-loaded"></a>正在檢查載入的內容

屬性會依 `ContentSceneNames` 組建索引的順序提供可用內容幕後的陣列。 您可以檢查是否透過載入這些幕後 `IsContentLoaded(string contentName)` 。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
