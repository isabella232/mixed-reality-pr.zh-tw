---
title: MRTK_Pakages
description: MRTK 中的套件支援混合現實硬體和平臺。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Unity Pakage Manager、
ms.openlocfilehash: 85757365044d6a7174f5b2f743ed582083d2b23b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687788"
---
# <a name="mixed-reality-toolkit-packages"></a>混合現實工具組套件

 (MRTK) 的混合現實工具組是封裝的集合，可提供混合現實硬體和平臺的支援，藉此啟用跨平臺混合現實應用程式開發。

MRTK 隨附于下列 Unity 套件：

- [基礎](#foundation-package)
- [擴充功能](#extensions-package)
- [範例](#examples-package)
- [工具](#tools-package)

Microsoft 會從 GitHub 上 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) 分支中的原始程式碼發行並支援這些套件。

## <a name="foundation-package"></a>基礎封裝

混合現實工具組基礎是一組程式碼，可讓您的應用程式跨混合現實平臺運用一般功能。

<img src="../features//Images/Input/MRTK_Package_Foundation.png" width="350px" alt="Pakage Foundation" style="display:block;">  
<sup>MRTK 基礎封裝</sup>

MRTK 基礎是由下列各項所組成：

- **核心套件**

核心封裝包含所有其他元件使用的所有通用介面、類別和資料類型的定義。 強烈建議應用程式透過定義的介面，以獨佔方式存取 MRTK 元件，以啟用跨平臺的最高層級相容性。

- **平臺提供者**

MRTK Platform Provider 套件是可讓 Mixed Reality 工具組以混合現實硬體和平臺功能為目標的元件。

支援的平臺包括：

- Windows Mixed Reality
- OpenVR
- Windows 語音

- **系統服務**

核心服務會為核心套件中定義的系統服務介面提供預設的執行方式。

MRTK foundation 包含下列系統服務：

- [界限系統](../features/Boundary/BoundarySystemGettingStarted.md)
- [診斷系統](../features/Diagnostics/DiagnosticsSystemGettingStarted.md)
- [輸入系統](../features/Input/Overview.md)
- [空間感知系統](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md)
- [傳送系統](../features/TeleportSystem/Overview.md)

- **功能資產**

功能資產是以 Unity 資產和腳本（包括使用者介面控制項、標準資產等等）提供的相關功能集合。

## <a name="extensions-package"></a>擴充功能套件

擴充套件包含額外的服務和元件，可延伸基礎套件的功能。

- [場景轉換服務](../features/Extensions/SceneTransitionService/SceneTransitionServiceOverview.md)

## <a name="examples-package"></a>範例套件

範例套件包含的示範、範例腳本，以及可在基礎套件中執行功能的範例幕後。 此套件包含 [HandInteractionExample 場景](../features/README_HandInteractionExamples.md) (如下圖所示) 其中包含的範例物件可回應各種類型的手寫輸入 (清楚說明的) 。

![HandInteractionExample 場景](../features/Images/MRTK_Examples.png)

此套件也包含眼睛追蹤示範，其 [記載于此處](../features/EyeTracking/EyeTracking_ExamplesOverview.md)

更常見的情況是，MRTK 中的任何新功能都應該包含範例套件中的對應範例，大致遵循相同的資料夾結構和位置。

## <a name="tools-package"></a>工具套件

工具套件包含的工具，可用於建立混合的現實體驗，而其程式碼最終不會隨附于應用程式的一部分。

- [相依性視窗](../features/Tools/DependencyWindow.md)
- [延伸模組服務建立嚮導](../features/Tools/ExtensionServiceCreationWizard.md)
- [優化視窗](../features/Tools/OptimizeWindow.md)
- [螢幕擷取畫面公用程式](../features/Tools/ScreenshotUtility.md)

## <a name="see-also"></a>另請參閱

- [架構概觀](../Architecture/Overview.md)
- [系統、延伸模組服務和資料提供者](../Architecture/SystemsExtensionsProviders.md)
