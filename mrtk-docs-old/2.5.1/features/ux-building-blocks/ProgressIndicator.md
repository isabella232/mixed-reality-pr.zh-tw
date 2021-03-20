---
title: ProgressIndicator
description: MRTK 中的進度指標總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: fb21c06bba122c1f8ad81b4ff6f4454d1472f7e0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683761"
---
# <a name="progress-indicators"></a><span data-ttu-id="1a398-104">進度指標</span><span class="sxs-lookup"><span data-stu-id="1a398-104">Progress Indicators</span></span>

![進度指標](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="1a398-106">範例場景</span><span class="sxs-lookup"><span data-stu-id="1a398-106">Example scene</span></span>

<span data-ttu-id="1a398-107">您可以在場景中找到如何使用進度指標的範例 `ProgressIndicatorExamples` 。</span><span class="sxs-lookup"><span data-stu-id="1a398-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="1a398-108">此場景示範 SDK 中包含的每個進度指標 prefabs。</span><span class="sxs-lookup"><span data-stu-id="1a398-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Example Scene">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="1a398-109">範例：開啟、更新 & 關閉進度指標</span><span class="sxs-lookup"><span data-stu-id="1a398-109">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="1a398-110">進度指示器會執行 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 介面。</span><span class="sxs-lookup"><span data-stu-id="1a398-110">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="1a398-111">您可以使用從 GameObject 中取出這個介面 `GetComponent` 。</span><span class="sxs-lookup"><span data-stu-id="1a398-111">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="1a398-112">和方法會傳回工作 `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` 。 [](xref:System.Threading.Tasks.Task)</span><span class="sxs-lookup"><span data-stu-id="1a398-112">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="1a398-113">建議您在非同步方法中等候這些工作。</span><span class="sxs-lookup"><span data-stu-id="1a398-113">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="1a398-114">將指標的 `Progress` 屬性設定為0-1 的值，以更新其顯示的進度。</span><span class="sxs-lookup"><span data-stu-id="1a398-114">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="1a398-115">設定其 `Message` 屬性，以更新其顯示的訊息。</span><span class="sxs-lookup"><span data-stu-id="1a398-115">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="1a398-116">不同的實施方式可能會以不同的方式顯示此內容。</span><span class="sxs-lookup"><span data-stu-id="1a398-116">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="1a398-117">指標狀態</span><span class="sxs-lookup"><span data-stu-id="1a398-117">Indicator states</span></span>

<span data-ttu-id="1a398-118">指標的 `State` 屬性會決定哪些作業是有效的。</span><span class="sxs-lookup"><span data-stu-id="1a398-118">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="1a398-119">呼叫不正確方法通常會導致指標回報錯誤，而不採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="1a398-119">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="1a398-120">狀態</span><span class="sxs-lookup"><span data-stu-id="1a398-120">State</span></span> | <span data-ttu-id="1a398-121">有效的作業</span><span class="sxs-lookup"><span data-stu-id="1a398-121">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="1a398-122">`AwaitTransitionAsync()` 可以用來確保指標在使用之前已完全開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="1a398-122">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
