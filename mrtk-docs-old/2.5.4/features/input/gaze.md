---
title: 注視
description: MRTK 中的注視類型 Docummentation
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、注視、
ms.openlocfilehash: 00b3cf9e56f40f72f722793883dfec0090086f5530c05305f050998478917eb8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209234"
---
# <a name="gaze"></a>注視

「[注視](https://docs.microsoft.com/windows/mixed-reality/gaze)」是一種輸入，可根據使用者的外觀與世界互動。 看看有兩種不同的類別

## <a name="head-gaze"></a>頭部注視

這種類型的注視是以前端/攝影機查看的方向為基礎。 在不支援眼睛的系統上，或在硬體可能支援眼睛的情況下，但未執行正確的 [許可權集和](../eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) 設定的情況下，前端看起來是作用中的。

前端看起來通常與與查看物件相關的 HoloLens 1 種樣式互動有關，方法是將它放在全像攝影框架的中央，然後執行 [點一下手勢]。

## <a name="eye-gaze"></a>眼睛目光

這種類型的看起來是根據使用者的眼睛。 只有支援眼睛追蹤的系統才會顯示眼睛。 如需如何使用眼睛的詳細資訊，請參閱 [眼睛追蹤檔](../eye-tracking/eye-tracking-main.md) 。

## <a name="gazeprovider"></a>GazeProvider

 (頭部和眼睛) 都是由 [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)所提供。 此提供者可在輸入系統設定檔的 [ *指標* ] 區段中設定：

![注視設定進入點](../images/input/GazeConfigurationEntrypoint.png)

如同輸入的其他來源，注視提供者會透過使用指標與場景中的物件互動 (如需 [) 指標的詳細資訊，請參閱這份檔 ](../../architecture/controllers-pointers-and-focus.md)。
在「注視」提供者的情況下，其指標是 `InternalGazePointer` 透過執行，而且不是透過設定檔設定。

您可以藉由將「 *注視提供者」類型* 變更為參考不同的類別來取代 [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) 和 [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)，以替代的實作為來取代股票 GazeProvider。
通常建議使用股票 GazeProvider (，並在) 發現 bug 時提出問題，因為重新執行 GazeProvider 並不重要。

### <a name="alternative-platform-provided-gaze-poses"></a>替代平臺提供的注視姿勢

根據預設，MRTK GazeProvider 會使用相機的框架中心作為注視原點。 某些平臺（例如 HoloLens 2 上的 Windows Mixed Reality）提供了一種定義的注視姿勢。 這是透過「 `Use Head Gaze Override` 注視設定」中的設定來管理。 啟用時，將會使用替代的注視覆寫。 停用時，將會使用預設的框架中心原點。 具體來說，就 HoloLens 2 來說，看看的外觀角度將會產生數度，以讓使用者在使用其標頭作為目標時感到舒適。

## <a name="usage"></a>使用方式

### <a name="how-get-the-current-gaze-target"></a>如何取得目前的注視目標

這個範例會示範如何取得使用者注視的目前遊戲物件。

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

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a>如何取得目前的注視方向和原點

這個範例會示範如何取得 Vector3，代表使用者注視的方向和原點 (方向) 的起點。

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
