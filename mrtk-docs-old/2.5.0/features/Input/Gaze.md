---
title: 注視
description: MRTK 中的注視類型 Docummentation
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、注視、
ms.openlocfilehash: 8f3f7317cd0bc2bb120328453f1fedf8e27025ca
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779916"
---
# <a name="gaze"></a><span data-ttu-id="f7e18-104">注視</span><span class="sxs-lookup"><span data-stu-id="f7e18-104">Gaze</span></span>

<span data-ttu-id="f7e18-105">「[注視](https://docs.microsoft.com/windows/mixed-reality/gaze)」是一種輸入，可根據使用者的外觀與世界互動。</span><span class="sxs-lookup"><span data-stu-id="f7e18-105">[Gaze](https://docs.microsoft.com/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="f7e18-106">看看有兩種不同的類別</span><span class="sxs-lookup"><span data-stu-id="f7e18-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="f7e18-107">頭部注視</span><span class="sxs-lookup"><span data-stu-id="f7e18-107">Head gaze</span></span>

<span data-ttu-id="f7e18-108">這種類型的注視是以前端/攝影機查看的方向為基礎。</span><span class="sxs-lookup"><span data-stu-id="f7e18-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="f7e18-109">在不支援眼睛的系統上，或在硬體可能支援眼睛的情況下，但未執行正確的 [許可權集和](../EyeTracking/EyeTracking_BasicSetup.md#eye-tracking-requirements-checklist) 設定的情況下，前端看起來是作用中的。</span><span class="sxs-lookup"><span data-stu-id="f7e18-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](../EyeTracking/EyeTracking_BasicSetup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="f7e18-110">前端看起來通常會與 HoloLens 1 樣式互動相關，包括將物件放在全像攝影框架的中央，然後執行 [點一下] 手勢。</span><span class="sxs-lookup"><span data-stu-id="f7e18-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="f7e18-111">眼睛目光</span><span class="sxs-lookup"><span data-stu-id="f7e18-111">Eye gaze</span></span>

<span data-ttu-id="f7e18-112">這種類型的看起來是根據使用者的眼睛。</span><span class="sxs-lookup"><span data-stu-id="f7e18-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="f7e18-113">只有支援眼睛追蹤的系統才會顯示眼睛。</span><span class="sxs-lookup"><span data-stu-id="f7e18-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="f7e18-114">如需如何使用眼睛的詳細資訊，請參閱 [眼睛追蹤檔](../EyeTracking/EyeTracking_Main.md) 。</span><span class="sxs-lookup"><span data-stu-id="f7e18-114">See the [eye tracking documentation](../EyeTracking/EyeTracking_Main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="f7e18-115">GazeProvider</span><span class="sxs-lookup"><span data-stu-id="f7e18-115">GazeProvider</span></span>

<span data-ttu-id="f7e18-116"> (頭部和眼睛) 都是由 [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)所提供。</span><span class="sxs-lookup"><span data-stu-id="f7e18-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="f7e18-117">此提供者可在輸入系統設定檔的 [ *指標* ] 區段中設定：</span><span class="sxs-lookup"><span data-stu-id="f7e18-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![注視設定進入點](../Images/Input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="f7e18-119">如同輸入的其他來源，注視提供者會透過使用指標與場景中的物件互動 (如需 [) 指標的詳細資訊，請參閱這份檔 ](../../architecture/InputSystem/ControllersPointersAndFocus.md)。</span><span class="sxs-lookup"><span data-stu-id="f7e18-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/InputSystem/ControllersPointersAndFocus.md).</span></span>
<span data-ttu-id="f7e18-120">在「注視」提供者的情況下，其指標是 `InternalGazePointer` 透過執行，而且不是透過設定檔設定。</span><span class="sxs-lookup"><span data-stu-id="f7e18-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="f7e18-121">您可以藉由將「 *注視提供者」類型* 變更為參考不同的類別來取代 [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) 和 [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)，以替代的實作為來取代股票 GazeProvider。</span><span class="sxs-lookup"><span data-stu-id="f7e18-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="f7e18-122">通常建議使用股票 GazeProvider (，並在) 發現 bug 時提出問題，因為重新執行 GazeProvider 並不重要。</span><span class="sxs-lookup"><span data-stu-id="f7e18-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="f7e18-123">替代平臺提供的注視姿勢</span><span class="sxs-lookup"><span data-stu-id="f7e18-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="f7e18-124">根據預設，MRTK GazeProvider 會使用相機的框架中心作為注視原點。</span><span class="sxs-lookup"><span data-stu-id="f7e18-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="f7e18-125">某些平臺（像是在 HoloLens 2 上的 Windows Mixed Reality）提供了一種定義的注視姿勢。</span><span class="sxs-lookup"><span data-stu-id="f7e18-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="f7e18-126">這是透過「 `Use Head Gaze Override` 注視設定」中的設定來管理。</span><span class="sxs-lookup"><span data-stu-id="f7e18-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="f7e18-127">啟用時，將會使用替代的注視覆寫。</span><span class="sxs-lookup"><span data-stu-id="f7e18-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="f7e18-128">停用時，將會使用預設的框架中心原點。</span><span class="sxs-lookup"><span data-stu-id="f7e18-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="f7e18-129">具體而言，在 HoloLens 2 中，將會產生數度的外觀，讓使用者可以輕鬆地使用其標頭來設定目標。</span><span class="sxs-lookup"><span data-stu-id="f7e18-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="f7e18-130">使用方式</span><span class="sxs-lookup"><span data-stu-id="f7e18-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="f7e18-131">如何取得目前的注視目標</span><span class="sxs-lookup"><span data-stu-id="f7e18-131">How get the current gaze target</span></span>

<span data-ttu-id="f7e18-132">這個範例會示範如何取得使用者注視的目前遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="f7e18-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="f7e18-133">如何取得目前的注視方向和原點</span><span class="sxs-lookup"><span data-stu-id="f7e18-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="f7e18-134">這個範例會示範如何取得 Vector3，代表使用者注視的方向和原點 (方向) 的起點。</span><span class="sxs-lookup"><span data-stu-id="f7e18-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
