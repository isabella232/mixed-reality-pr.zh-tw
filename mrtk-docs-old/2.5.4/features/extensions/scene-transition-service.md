---
title: SceneTransitionServiceOverview
description: MRTK 中的場景轉換檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、SceneTransition、
ms.openlocfilehash: 546facf53abe38e62176e32e9fb79728e6536d1b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685481"
---
# <a name="scene-transition-service"></a><span data-ttu-id="6e42f-104">場景轉換服務</span><span class="sxs-lookup"><span data-stu-id="6e42f-104">Scene transition service</span></span>

<span data-ttu-id="6e42f-105">此延伸模組可簡化將場景淡出的業務、顯示進度指標、載入場景，然後淡入。</span><span class="sxs-lookup"><span data-stu-id="6e42f-105">This extension simplifies the business of fading out a scene, displaying a progress indicator, loading a scene, then fading back in.</span></span>

<span data-ttu-id="6e42f-106">場景作業是由 SceneSystem 服務所驅動，但是任何以工作為基礎的作業都可以用來驅動轉換。</span><span class="sxs-lookup"><span data-stu-id="6e42f-106">Scene operations are driven by the SceneSystem service, but any Task-based operation can be used to drive a transition.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="6e42f-107">啟用擴充功能</span><span class="sxs-lookup"><span data-stu-id="6e42f-107">Enabling the extension</span></span>

<span data-ttu-id="6e42f-108">若要啟用擴充功能，請開啟您的 RegisteredServiceProvider 設定檔。</span><span class="sxs-lookup"><span data-stu-id="6e42f-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="6e42f-109">按一下 [註冊新的服務提供者]，以新增設定。</span><span class="sxs-lookup"><span data-stu-id="6e42f-109">Click Register a new Service Provider to add a new configuration.</span></span> <span data-ttu-id="6e42f-110">在 [元件類型] 欄位中，選取 [SceneTransitionService]。</span><span class="sxs-lookup"><span data-stu-id="6e42f-110">In the Component Type field, select SceneTransitionService.</span></span> <span data-ttu-id="6e42f-111">在 [設定檔] 欄位中，選取延伸模組隨附的預設場景轉換設定檔。</span><span class="sxs-lookup"><span data-stu-id="6e42f-111">In the Configuration Profile field, select the default scene transition profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="6e42f-112">設定檔選項</span><span class="sxs-lookup"><span data-stu-id="6e42f-112">Profile options</span></span>

### <a name="use-default-progress-indicator"></a><span data-ttu-id="6e42f-113">使用預設進度指標</span><span class="sxs-lookup"><span data-stu-id="6e42f-113">Use default progress indicator</span></span>

<span data-ttu-id="6e42f-114">若選取此選項，當呼叫進度指標物件時，如果未提供任何進度指標物件，將會使用預設的進度指標預製專案 `DoSceneTransition.` ，預設值將會被忽略。</span><span class="sxs-lookup"><span data-stu-id="6e42f-114">If checked, the default progress indicator prefab will be used when no progress indicator object is provided when calling `DoSceneTransition.` If a progress indicator object is provided, the default will be ignored.</span></span>

### <a name="use-fade-color"></a><span data-ttu-id="6e42f-115">使用淡化色彩</span><span class="sxs-lookup"><span data-stu-id="6e42f-115">Use fade color</span></span>

<span data-ttu-id="6e42f-116">若選取此選項，轉換服務會在您的轉換期間套用淡化。</span><span class="sxs-lookup"><span data-stu-id="6e42f-116">If checked, the transition service will apply a fade during your transition.</span></span> <span data-ttu-id="6e42f-117">您可以在執行時間透過服務的屬性變更這種設定 `UseFadeColor` 。</span><span class="sxs-lookup"><span data-stu-id="6e42f-117">This setting can be changed at runtime via the service's `UseFadeColor` property.</span></span>

### <a name="fade-color"></a><span data-ttu-id="6e42f-118">淡化色彩</span><span class="sxs-lookup"><span data-stu-id="6e42f-118">Fade color</span></span>

<span data-ttu-id="6e42f-119">控制淡化效果的色彩。</span><span class="sxs-lookup"><span data-stu-id="6e42f-119">Controls the color of the fade effect.</span></span> <span data-ttu-id="6e42f-120">已忽略 Alpha。</span><span class="sxs-lookup"><span data-stu-id="6e42f-120">Alpha is ignored.</span></span> <span data-ttu-id="6e42f-121">在透過服務的屬性轉換之前，您可以在執行時間變更這種設定 `FadeColor` 。</span><span class="sxs-lookup"><span data-stu-id="6e42f-121">This setting can be changed at runtime prior to a transition via the service's `FadeColor` property.</span></span>

### <a name="fade-targets"></a><span data-ttu-id="6e42f-122">淡化目標</span><span class="sxs-lookup"><span data-stu-id="6e42f-122">Fade targets</span></span>

<span data-ttu-id="6e42f-123">控制哪些相機會套用淡化效果。</span><span class="sxs-lookup"><span data-stu-id="6e42f-123">Controls which cameras will have a fade effect applied to them.</span></span> <span data-ttu-id="6e42f-124">您可以在執行時間透過服務的屬性變更這種設定 `FadeTargets` 。</span><span class="sxs-lookup"><span data-stu-id="6e42f-124">This setting can be changed at runtime via the service's `FadeTargets` property.</span></span>

<span data-ttu-id="6e42f-125">設定</span><span class="sxs-lookup"><span data-stu-id="6e42f-125">Setting</span></span> | <span data-ttu-id="6e42f-126">目標攝影機</span><span class="sxs-lookup"><span data-stu-id="6e42f-126">Targeted Cameras</span></span>
--- | --- | ---
<span data-ttu-id="6e42f-127">主要區段</span><span class="sxs-lookup"><span data-stu-id="6e42f-127">Main</span></span> | <span data-ttu-id="6e42f-128">將淡化效果套用至主要攝影機。</span><span class="sxs-lookup"><span data-stu-id="6e42f-128">Applies fade effect to the main camera.</span></span>
<span data-ttu-id="6e42f-129">UI</span><span class="sxs-lookup"><span data-stu-id="6e42f-129">UI</span></span> | <span data-ttu-id="6e42f-130">將淡化效果套用至 UI 圖層上的相機。</span><span class="sxs-lookup"><span data-stu-id="6e42f-130">Applies fade effect to cameras on the UI layer.</span></span> <span data-ttu-id="6e42f-131"> (不會影響重迭 UI) </span><span class="sxs-lookup"><span data-stu-id="6e42f-131">(Does not affect overlay UI)</span></span>
<span data-ttu-id="6e42f-132">全部</span><span class="sxs-lookup"><span data-stu-id="6e42f-132">All</span></span> | <span data-ttu-id="6e42f-133">適用于主要和 UI 攝影機。</span><span class="sxs-lookup"><span data-stu-id="6e42f-133">Applies to both main and UI cameras.</span></span>
<span data-ttu-id="6e42f-134">自訂</span><span class="sxs-lookup"><span data-stu-id="6e42f-134">Custom</span></span> | <span data-ttu-id="6e42f-135">適用于透過提供的一組自訂攝影機 `SetCustomFadeTargetCameras`</span><span class="sxs-lookup"><span data-stu-id="6e42f-135">Applies to a custom set of cameras provided via `SetCustomFadeTargetCameras`</span></span>

### <a name="fade-out-time--fade-in-time"></a><span data-ttu-id="6e42f-136">淡化時間/淡化時間</span><span class="sxs-lookup"><span data-stu-id="6e42f-136">Fade out time / fade in time</span></span>

<span data-ttu-id="6e42f-137">淡化進入/離開轉換的持續時間的預設設定。</span><span class="sxs-lookup"><span data-stu-id="6e42f-137">Default settings for the duration of a fade on entering / exiting a transition.</span></span> <span data-ttu-id="6e42f-138">您可以在執行時間透過服務的和屬性變更這些設定 `FadeOutTime` `FadeInTime` 。</span><span class="sxs-lookup"><span data-stu-id="6e42f-138">These settings can be changed at runtime via the service's `FadeOutTime` and `FadeInTime` properties.</span></span>

### <a name="camera-fader-type"></a><span data-ttu-id="6e42f-139">攝影機 fader 類型</span><span class="sxs-lookup"><span data-stu-id="6e42f-139">Camera fader type</span></span>

<span data-ttu-id="6e42f-140">用來將 `ICameraFader` 淡化效果套用至攝影機的類別。</span><span class="sxs-lookup"><span data-stu-id="6e42f-140">Which `ICameraFader` class to use for applying a fade effect to cameras.</span></span> <span data-ttu-id="6e42f-141">預設類別會具現 `CameraFaderQuad` 化四個四，並將目標相機前方的透明材質與剪輯平面接近。</span><span class="sxs-lookup"><span data-stu-id="6e42f-141">The default `CameraFaderQuad` class instantiates a quad with a transparent material in front of the target camera close to the clip plane.</span></span> <span data-ttu-id="6e42f-142">另一種方法可能是使用 post 效果系統。</span><span class="sxs-lookup"><span data-stu-id="6e42f-142">Another approach might be to use a post effects system.</span></span>

## <a name="using-the-extension"></a><span data-ttu-id="6e42f-143">使用延伸模組</span><span class="sxs-lookup"><span data-stu-id="6e42f-143">Using the extension</span></span>

<span data-ttu-id="6e42f-144">您可以藉由傳遞在相機淡出時執行的工作來使用轉換服務。</span><span class="sxs-lookup"><span data-stu-id="6e42f-144">You use the transition service by passing Tasks that are run while the camera is faded out.</span></span>

### <a name="using-scene-system-tasks"></a><span data-ttu-id="6e42f-145">使用場景系統工作</span><span class="sxs-lookup"><span data-stu-id="6e42f-145">Using scene system tasks</span></span>

<span data-ttu-id="6e42f-146">在大部分情況下，您將會使用 SceneSystem 服務所提供的工作：</span><span class="sxs-lookup"><span data-stu-id="6e42f-146">In most cases you will be using Tasks supplied by the SceneSystem service:</span></span>

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

### <a name="using-custom-tasks"></a><span data-ttu-id="6e42f-147">使用自訂工作</span><span class="sxs-lookup"><span data-stu-id="6e42f-147">Using custom tasks</span></span>

<span data-ttu-id="6e42f-148">在其他情況下，您可能會想要執行轉換，而不實際載入場景：</span><span class="sxs-lookup"><span data-stu-id="6e42f-148">In other cases you may want to perform a transition without actually loading a scene:</span></span>

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

<span data-ttu-id="6e42f-149">或者，您可能想要在不使用 SceneSystem 服務的情況下載入場景：</span><span class="sxs-lookup"><span data-stu-id="6e42f-149">Or you may want to load a scene without using the SceneSystem service:</span></span>

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

### <a name="using-multiple-tasks"></a><span data-ttu-id="6e42f-150">使用多個工作</span><span class="sxs-lookup"><span data-stu-id="6e42f-150">Using multiple tasks</span></span>

<span data-ttu-id="6e42f-151">您也可以提供多項工作，這些工作將依序執行：</span><span class="sxs-lookup"><span data-stu-id="6e42f-151">You can also supply multiple tasks, which will be executed in order:</span></span>

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

## <a name="using-the-progress-indicator"></a><span data-ttu-id="6e42f-152">使用進度列指示器</span><span class="sxs-lookup"><span data-stu-id="6e42f-152">Using the progress indicator</span></span>

<span data-ttu-id="6e42f-153">進度指標是任何實作為介面的程式 `IProgressIndicator` 。</span><span class="sxs-lookup"><span data-stu-id="6e42f-153">A progress indicator is anything that implements the `IProgressIndicator` interface.</span></span> <span data-ttu-id="6e42f-154">這可能會採用啟動顯示畫面的形式、3D tagalong 載入指標，或提供有關轉換進度的任何其他資訊。</span><span class="sxs-lookup"><span data-stu-id="6e42f-154">This can take the form of a splash screen, a 3D tagalong loading indicator, or anything else that provides feedback about transition progress.</span></span>

<span data-ttu-id="6e42f-155">如果 `UseDefaultProgressIndicator` 簽入 SceneTransitionService 設定檔中，則會在轉換開始時具現化進度指標。</span><span class="sxs-lookup"><span data-stu-id="6e42f-155">If `UseDefaultProgressIndicator` is checked in the SceneTransitionService profile, a progress indicator will be instantiated when a transition begins.</span></span> <span data-ttu-id="6e42f-156">在轉換期間，此指標的 `Progress` 和 `Message` 屬性可透過該服務的和方法來存取 `SetProgressValue` `SetProgressMessage` 。</span><span class="sxs-lookup"><span data-stu-id="6e42f-156">For the duration of the transition this indicator's `Progress` and `Message` properties can be accessed via that service's `SetProgressValue` and `SetProgressMessage` methods.</span></span>

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

<span data-ttu-id="6e42f-157">或者，在呼叫時， `DoSceneTransition` 您可以透過選擇性引數提供您自己的進度指標 `progressIndicator` 。</span><span class="sxs-lookup"><span data-stu-id="6e42f-157">Alternatively, when calling `DoSceneTransition` you can supply your own progress indicator via the optional `progressIndicator` argument.</span></span> <span data-ttu-id="6e42f-158">這會覆寫預設的進度指標。</span><span class="sxs-lookup"><span data-stu-id="6e42f-158">This will override the default progress indicator.</span></span>
