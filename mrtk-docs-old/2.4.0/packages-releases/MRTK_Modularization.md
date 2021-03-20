---
title: MRTK_Modularization
description: 描述 MRTK 中的元件化。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 7558bf60cbcf2abf4fb2f59af5805d1286826f80
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687808"
---
# <a name="mixed-reality-toolkit-componentization"></a>混合現實工具組元件化

混合現實工具組 v2 有一項絕佳的新功能，元件化改善。 可能的話，個別的元件會與所有基礎的核心層隔離。

## <a name="minimized-dependencies"></a>最小化相關性

MRTK v2 刻意開發成模組化，並將系統服務之間的相依性降到最低， (例如：空間感知) 。

由於某些系統服務的本質 (例如：輸入和遙傳) ，因此存在少量的相依性。

雖然服務預期會需要一或多個資料提供者元件，但它們之間沒有直接連結。 SDK 功能也同樣適用 (例如：消費者介面元件) 。

## <a name="component-communication"></a>元件通訊

為了確保元件之間沒有任何直接連結，MRTK v2 會利用服務、資料提供者和應用程式程式碼之間的介面來進行通訊。 這些介面是在中定義，而且所有通訊都是透過混合現實工具組核心元件來路由傳送。

![使用空間感知系統 via 介面](../features//Images/Packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>最小化 MRTK 匯入使用量

目前，MRTK 會匯入為單一基礎封裝 (忽略範例套件是否存在，這是) 的完全選用套件。 您可以藉由手動將匯入的檔案剪下，讓這項耗用量變得較小，但這是高度手動的程式，它沒有妥善定義的指南。

您可以在匯入基礎封裝期間取消核取任意專案。 但是，不建議您在開發初期階段進行這項作業，因為它可能會中斷功能。 在瞭解應用程式的最後一個功能集之後，可以在下列資料夾中執行剪除不必要的提供者和服務：

- MRTK/服務
- MRTK/提供者
- MRTK/SDK/功能

> [!NOTE]
> MRTK v2 **_需要_** 資產/MRTK/核心資料夾的內容。

## <a name="upcoming-features"></a>即將推出的功能

### <a name="application-architecture"></a>應用程式架構

MRTK 將支援以各種不同的架構來建立應用程式，包括：

- [MixedRealityToolkit 服務定位器](#mixedrealitytoolkit-service-locator)
- [個別服務](#individual-service-components)
- [自訂服務定位器](#custom-service-locator)
- [混合式架構](#hybrid-architecture)

選取應用程式架構時，請務必考慮設計彈性和應用程式效能。 此處所述的架構不應該適用于每個應用程式。

#### <a name="mixedrealitytoolkit-service-locator"></a>MixedRealityToolkit 服務定位器

MRTK 可讓 (，並自動將) 應用程式場景設定為使用預設 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 服務定位器元件。 此元件包含透過設定偵測器設定 MRTK 系統和資料提供者，以及管理元件壽命和核心行為的支援， (例如：更新) 的時機。

所有系統都會以核心設定偵測器表示，不論它們是否存在於專案中或已啟用。 如需詳細資訊，請參閱 [混合式事實設定指南](../out-of-scope/MixedRealityConfigurationGuide.md) 。

#### <a name="individual-service-components"></a>個別的服務元件

有些開發人員表示想要在應用程式場景階層中包含個別的服務元件。 若要啟用這種用法，服務將需要封裝在自訂註冊機構中，或自行註冊/自我管理。

自我註冊服務會執行 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 並註冊本身，讓應用程式程式碼可以透過登錄探索服務實例。

自我管理服務可以實作為場景階層中的單一物件。 這個物件會提供應用程式程式碼可以用來直接存取服務功能的實例屬性和實例屬性。

#### <a name="custom-service-locator"></a>自訂服務定位器

某些開發人員已要求建立自訂服務定位器元件的能力。 自訂服務定位器會執行 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 介面，以及管理使用中服務的生命週期和核心行為。

#### <a name="hybrid-architecture"></a>混合式架構

MRTK 將支援混合式架構，讓開發人員可以視需要或想要的方式合併先前的方法。 例如，開發人員可以從 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 服務定位器開始，然後新增自我註冊服務。

> [!NOTE]
> 選擇混合式架構時，請務必留意任何重複的工作 (例如：從多個元件) 取得控制器資料。
