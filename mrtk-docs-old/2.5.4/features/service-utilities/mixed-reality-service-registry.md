---
title: MixedRealityServiceRegistryAndIMixedRealityServiceRegistrar
description: MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar 的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 5e9bf98c9584e780bdeb79d7ca172f67a62a7601c289612a40082ecaa90e9448
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196100"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a>MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar 有哪些？

混合現實工具組有兩個類似的命名元件，可執行相關工作： MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar。

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)是包含每個已註冊服務實例的元件， (核心系統和擴充服務) 。

> [!NOTE]
> MixedRealityServiceRegistry 包含可執行 [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 介面之物件的實例，包括 [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)。
>
>執行 [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 的物件 (IMixedRealityService) 的子類別會明確地未在 MixedRealityServiceRegistry 中註冊。 這些物件是由個別服務所管理 (例如：空間感知) 。

MixedRealityServiceRegistry 會實作為靜態 c # 類別，並且是在應用程式程式碼中用來取得服務實例的建議模式。

下列程式碼片段示範如何取得 IMixedRealityInputSystem 實例。

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)是一個介面，定義管理一或多個服務之註冊的元件所執行的功能。 執行 IMixedRealityServiceRegistrar 的元件會負責新增和移除 MixedRealityServiceRegistry 中的資料。 [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)物件是一個這類元件。

其他註冊機構可以在 MRTK/SDK/實驗/功能資料夾中找到。 這些元件可以用來將單一服務 (例如：空間感知) 支援新增至應用程式。 以下列出這些單一服務管理員。

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

上述每個元件（InputSystemManager 除外）都會負責管理單一服務類型的註冊和狀態。 InputSystem 需要一些額外的支援服務 (例如： FocusProvider) ，也是由 InputSystemManager 管理。

一般來說，服務管理元件會在內部呼叫 IMixedRealityServiceRegistrar 所定義的方法，或由需要額外服務元件才能正常運作的服務呼叫。 一般來說，應用程式程式碼應該不會呼叫這些方法，因為這樣可能會導致應用程式無法預期的行為 (例如：快取的服務實例可能會變成不正確) 。

## <a name="see-also"></a>另請參閱

- [IMixedRealityServiceRegistrar API 檔](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [MixedRealityServiceRegistry API 檔](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
