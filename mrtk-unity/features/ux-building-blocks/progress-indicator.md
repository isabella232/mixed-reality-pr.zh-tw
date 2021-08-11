---
title: 進度指示器
description: MRTK 中的進度指標總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: b5147e5c592b80ab100a7cf7ce2487d971299832fec11f7ca57b1fdeef530900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202580"
---
# <a name="progress-indicator"></a>進度指示器

![進度指標](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>範例場景

您可以在場景中找到如何使用進度指標的範例 `ProgressIndicatorExamples` 。 此場景示範 SDK 中包含的每個進度指標 prefabs。 它也會示範如何搭配一些常見的非同步工作（例如場景載入）來使用進度指示器。

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>範例：開啟、更新 & 關閉進度指標

進度指示器會執行 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 介面。 您可以使用從 GameObject 中取出這個介面 `GetComponent` 。

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

和方法會傳回工作 `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` 。 [](xref:System.Threading.Tasks.Task) 建議您在非同步方法中等候這些工作。

MRTK 的預設進度指標 prefabs 在放置於場景時應為非使用中。 當其 `IProgressIndicator.OpenAsync()` 方法被呼叫時，進度指示器將會自動啟用並停用其 gameobject。  (此模式不是 IProgressIndicator 介面的需求。 ) 

將指標的 `Progress` 屬性設定為0-1 的值，以更新其顯示的進度。 設定其 `Message` 屬性，以更新其顯示的訊息。 不同的實施方式可能會以不同的方式顯示此內容。

```c#
private async void OpenProgressIndicator()
{
    await indicator.OpenAsync();

    float progress = 0;
    while (progress < 1)
    {
        progress += Time.deltaTime;
        indicator.Message = "Loading...";
        indicator.Progress = progress;
        await Task.Yield();
    }

    await indicator.CloseAsync();
}
```

## <a name="indicator-states"></a>指標狀態

指標的 `State` 屬性會決定哪些作業是有效的。 呼叫不正確方法通常會導致指標回報錯誤，而不採取任何動作。

狀態 | 有效的作業
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` 可以用來確保指標在使用之前已完全開啟或關閉。

```c#
private async void ToggleIndicator(IProgressIndicator indicator)
{
    await indicator.AwaitTransitionAsync();

    switch (indicator.State)
    {
        case ProgressIndicatorState.Closed:
            await indicator.OpenAsync();
            break;

        case ProgressIndicatorState.Open:
            await indicator.CloseAsync();
            break;
        }
    }
```
