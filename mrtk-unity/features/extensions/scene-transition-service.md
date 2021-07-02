---
title: 場景轉換服務
description: MRTK 中的場景轉換檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、SceneTransition、
ms.openlocfilehash: b645012a055f693fdac794b79e24fd20154fdb65
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176209"
---
# <a name="scene-transition-service"></a>場景轉換服務

此延伸模組可簡化將場景淡出的業務、顯示進度指標、載入場景，然後淡入。

場景作業是由 SceneSystem 服務所驅動，但是任何以工作為基礎的作業都可以用來驅動轉換。

## <a name="enabling-the-extension"></a>啟用擴充功能

若要啟用擴充功能，請開啟您的 RegisteredServiceProvider 設定檔。 按一下 [註冊新的服務提供者]，以新增設定。 在 [元件類型] 欄位中，選取 [SceneTransitionService]。 在 [設定檔] 欄位中，選取延伸模組隨附的預設場景轉換設定檔。

## <a name="profile-options"></a>設定檔選項

### <a name="use-default-progress-indicator"></a>使用預設進度指標

若選取此選項，當呼叫進度指標物件時，如果未提供任何進度指標物件，將會使用預設的進度指標預製專案 `DoSceneTransition.` ，預設值將會被忽略。

### <a name="use-fade-color"></a>使用淡化色彩

若選取此選項，轉換服務會在您的轉換期間套用淡化。 您可以在執行時間透過服務的屬性變更這種設定 `UseFadeColor` 。

### <a name="fade-color"></a>淡化色彩

控制淡化效果的色彩。 已忽略 Alpha。 在透過服務的屬性轉換之前，您可以在執行時間變更這種設定 `FadeColor` 。

### <a name="fade-targets"></a>淡化目標

控制哪些相機會套用淡化效果。 您可以在執行時間透過服務的屬性變更這種設定 `FadeTargets` 。

設定 | 目標攝影機
--- | --- | ---
主要區段 | 將淡化效果套用至主要攝影機。
UI | 將淡化效果套用至 UI 圖層上的相機。  (不會影響重迭 UI) 
全部 | 適用于主要和 UI 攝影機。
自訂 | 適用于透過提供的一組自訂攝影機 `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>淡化時間/淡化時間

淡化進入/離開轉換的持續時間的預設設定。 您可以在執行時間透過服務的和屬性變更這些設定 `FadeOutTime` `FadeInTime` 。

### <a name="camera-fader-type"></a>攝影機 fader 類型

用來將 `ICameraFader` 淡化效果套用至攝影機的類別。 預設類別會具現 `CameraFaderQuad` 化四個四，並將目標相機前方的透明材質與剪輯平面接近。 另一種方法可能是使用 post 效果系統。

## <a name="using-the-extension"></a>使用延伸模組

您可以藉由傳遞在相機淡出時執行的工作來使用轉換服務。

### <a name="using-scene-system-tasks"></a>使用場景系統工作

在大部分情況下，您將會使用 SceneSystem 服務所提供的工作：

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Runs LoadContent task
    // Fades back in
    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}
```

### <a name="using-custom-tasks"></a>使用自訂工作

在其他情況下，您可能會想要執行轉換，而不實際載入場景：

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Resets scene
    // Fades back in
    await transition.DoSceneTransition(
            () => ResetScene()
        );
}

private async Task ResetScene()
{
    // Go through all enemies in the current scene and move them back to starting positions
}
```

或者，您可能想要在不使用 SceneSystem 服務的情況下載入場景：

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Loads scene using Unity's scene manager
    // Fades back in
    await transition.DoSceneTransition(
            () => LoadScene("TestScene1")
        );
}

private async Task LoadScene(string sceneName)
{
    AsyncOperation asyncOp = SceneManager.LoadSceneAsync(sceneName, LoadSceneMode.Additive);
    while (!asyncOp.isDone)
    {
        await Task.Yield();
    }
}
```

### <a name="using-multiple-tasks"></a>使用多個工作

您也可以提供多項工作，這些工作將依序執行：

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Sets time scale to 0
    // Fades out audio to 0
    // Loads TestScene1
    // Fades in audio to 1
    // Sets time scale to 1
    // Fades back in
    await transition.DoSceneTransition(
            () => SetTimescale(0f),
            () => FadeAudio(0f, 1f),
            () => sceneSystem.LoadContent("TestScene1"),
            () => FadeAudio(1f, 1f),
            () => SetTimescale(1f)
        );
}

private async Task SetTimescale(float targetTime)
{
    Time.timeScale = targetTime;
    await Task.Yield();
}

private async Task FadeAudio(float targetVolume, float duration)
{
    float startTime = Time.realtimeSinceStartup;
    float startVolume = AudioListener.volume;
    while (Time.realtimeSinceStartup < startTime + duration)
    {
        AudioListener.volume = Mathf.Lerp(startVolume, targetVolume, Time.realtimeSinceStartup - startTime / duration);
        await Task.Yield();
       }
       AudioListener.volume = targetVolume;
}
```

## <a name="using-the-progress-indicator"></a>使用進度列指示器

進度指標是任何實作為介面的程式 `IProgressIndicator` 。 這可能會採用啟動顯示畫面的形式、3D tagalong 載入指標，或提供有關轉換進度的任何其他資訊。

如果 `UseDefaultProgressIndicator` 簽入 SceneTransitionService 設定檔中，則會在轉換開始時具現化進度指標。 在轉換期間，此指標的 `Progress` 和 `Message` 屬性可透過該服務的和方法來存取 `SetProgressValue` `SetProgressMessage` 。

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    ListenToSceneTransition(sceneSystem, transition);

    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}

private async void ListenToSceneTransition(IMixedRealitySceneSystem sceneSystem, ISceneTransitionService transition)
{
    transition.SetProgressMessage("Starting transition...");

    while (transition.TransitionInProgress)
    {
        if (sceneSystem.SceneOperationInProgress)
        {
            transition.SetProgressMessage("Loading scene...");
            transition.SetProgressValue(sceneSystem.SceneOperationProgress);
        }
        else
        {
            transition.SetProgressMessage("Finished loading scene...");
            transition.SetProgressValue(1);
        }

        await Task.Yield();
    }
}
```

或者，在呼叫時， `DoSceneTransition` 您可以透過選擇性引數提供您自己的進度指標 `progressIndicator` 。 這會覆寫預設的進度指標。
