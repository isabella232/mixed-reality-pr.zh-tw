---
title: MixedRealityServices
description: Unity 中與 MRTK 相關的服務。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: c23c16e7dac54ff209beca24bd8b8b857967f697
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694595"
---
# <a name="what-makes-a-mixed-reality-feature"></a>什麼是混合的現實功能

為了避免類別的效能額外負荷 `MonoBehaviour` ，所有的 *服務* (系統、功能或需要在混合現實解決方案中獨立作業的模組，例如輸入、界限、空間感知) 都必須是獨立的簡單 c # 類別，其會執行 `IMixedRealityService` 並向註冊 `MixedRealityToolkit` 。

`MixedRealityToolkit`接著會協調服務之間的所有參考，並確保它們會接收所有適當的事件 (例如 喚醒/初始化、更新、摧毀) 以及在需要時加速尋找其他服務。

此外，也會在 `MixedRealityToolkit` 執行中的專案中維護使用中的 VR/XR/AR SDK，以根據附加的硬體和 instigate 適當的作業來初始化作用中裝置。

## <a name="a-service"></a>服務

個別服務可以是任何需要在專案中執行的功能。 傳統上，有些專案使用的 *singleton* 必須在場景中保持運作，但此模式有其優點和缺點。 我們決定要打破這種模式，以配合採用傳統單一執行的多項優點 `MonoBehaviours` ，亦即：

* 效能-沒有的額外負荷 `MonoBehaviour` ， [腳本更新的速度大約是80%，而且不需要在 `GameObject` 場景中存留](https://blogs.unity3d.com/2015/12/23/1k-update-calls/)。
* 您可以從在 `MixedRealityToolkit` 場景中搜尋或使用，更快且更容易探索的參考能力服務 `GameObjects` `FindObjectsOfType<T>` 。
* 沒有類型相依性-雖然類似于相依性插入的方法，服務也可以從其型別分離，這表示可以在任何時間將實際執行交換，而不會對使用它的程式碼造成負面影響 (例如，將預設 InputSystem 取代為自訂的介面，只要您已完全實) 。
* 多場景使用-如果服務需要知道 `transform` 場景中的位置，它可以直接參考或建立， `GameObject` _而不是附加至元件的元件_。 這可讓您在專案橫跨多個場景時更輕鬆地尋找和使用服務。

## <a name="service-interfaces"></a>服務介面

*服務* 容器會使用預先定義的 *介面* 類型來儲存及抓取任何服務，這可確保混合現實工具組內不會有固定的相依性，因此只要每個子系統符合介面) ，就可以輕易地與另一個 (交換。

混合現實工具組所提供的目前系統介面包括：

* [`IMixedRealityInputSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputSystem)
* [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)
* [`IMixedRealityTeleportSystem`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportSystem)

當您建立自己的這些系統的執行時，必須確定每個都符合混合現實工具組所提供的介面 (例如，如果您將 InputSystem 取代為您自己的其他設計) 。

> [!NOTE]
> 所有服務也都必須繼承自 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 類別或實作為 [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) ，以執行所需的函 `MixedRealityToolkit` 式，以便適當地處理其生命週期。  (例如 已正確呼叫 Initialize、Update、摧毀。 ) 
