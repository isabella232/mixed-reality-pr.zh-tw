---
title: MRTK 套件
description: MRTK 中的套件支援混合現實硬體和平臺。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Unity 封裝管理員、
ms.openlocfilehash: 13f18c0a43d8b0cf6cc8eb66949b506c51ca9bbaa733e74cd38de110f70d8ee1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212560"
---
# <a name="mrtk-packages"></a>MRTK 套件

 (MRTK) 的混合現實工具組是封裝的集合，可提供混合現實硬體和平臺的支援，藉此啟用跨平臺混合現實應用程式開發。

MRTK 可作為[資產](#asset-packages) ( unitypackage) 套件和透過[Unity 封裝管理員](#unity-package-manager)。

## <a name="asset-packages"></a>資產套件

您可以從[GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)下載 MRTK 資產 (. unitypackage) 。

使用資產套件的一些優點包括：

- 適用于 Unity 2018.4 和更新版本
- 輕鬆變更 MRTK
  - MRTK 在 [資產] 資料夾中

其中一些挑戰如下：

- MRTK 是專案 [資產] 資料夾的一部分，
  - 較大型的專案
  - 較慢的編譯時間
- 無相依性管理
  - 客戶必須手動解析套件相依性
- 手動更新程式
  - 多個步驟
  - 大型 (3000 + 檔案) 原始檔控制更新
  - 遺失對 MRTK 進行變更的風險
- 匯入範例封裝通常表示包含所有範例

可用的封裝如下：

- [基礎](#foundation-package)
- [擴充功能](#extensions-package)
- [工具](#tools-package)
- [測試公用程式](#test-utilities-package)
- [範例](#examples-package)

Microsoft 會從 GitHub 上的[mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release)分支中的原始程式碼發行並支援這些套件。

### <a name="foundation-package"></a>基礎封裝

混合現實工具組基礎是一組程式碼，可讓您的應用程式跨混合現實平臺運用一般功能。

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<sup>MRTK 基礎封裝</sup>

MRTK Foundation 套件包含下列各項。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/核心 | | 介面和類型定義、基類、標準著色器。 |
| MRTK/核心/提供者 | | 平臺中立的資料提供者 |
| | 手 | 用於手動追蹤的基類支援和服務。 |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | 支援錄製 head 移動和手追蹤資料。 |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | 支援手形和眼睛輸入的編輯器內模擬。 |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | 空間感知觀察者使用3D 模型做為資料。 |
| | UnityInput | 一般輸入裝置 (搖桿、滑鼠等 ) 透過 Unity 的輸入 API 來執行。 |
| MRTK/提供者 | | 平臺特定的資料提供者 |
| | LeapMotion | UltraLeap Leap 移動控制器的支援。 |
| | OpenVR | OpenVR 裝置的支援。 |
| | Oculus | Oculus 裝置的支援，例如尋找。 |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) |  (實驗性) 攝影機設定提供者，讓 MRTK 與行動 AR 裝置搭配使用。 |
| | WindowsMixedReality | 支援 Windows Mixed Reality 的裝置，包括 Microsoft HoloLens 和沉浸式耳機。 |
| | Windows | Microsoft Windows 特定 api 的支援，例如語音和聽寫。 |
| | XR SDK |  (unity 2019.3 和更新版本中 [unity 新 XR 架構](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的實驗性) 支援。 |
| MRTK/SDK | | |
| | 實驗 | 實驗性功能，包括著色器、使用者介面控制項和個別系統管理員。 |
| | 功能 | 建基於基礎封裝的功能。 |
| | Profiles | Microsoft Mixed Reality 工具組系統和服務的預設設定檔。 |
| | StandardAssets | 一般資產;模型、材質、材質等等。 |
| MRTK/SceneSystemResources | | 場景系統使用的資產和資源 |
| MRTK/服務 | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | 執行 VR 界限支援的系統。 |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | 系統執行攝影機設定和管理。 |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | 在 application diagnostics 中執行的系統，例如 visual profiler。 |
| | [InputSystem](../features/input/overview.md) | 系統，提供存取和處理使用者輸入的支援。 |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | 提供多場景應用程式支援的系統。 |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | 提供使用者環境感知支援的系統。 |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | 提供 teleporting 支援的系統 (移至跳躍) 的體驗。 |
| MRTK/StandardAssets | | 混合現實體驗的 MRTK 標準著色器、基本材質和其他標準資產 |

### <a name="extensions-package"></a>擴充功能套件

選用的 MixedRealityToolkit 套件包含擴充 Microsoft Mixed Reality 工具組功能的其他服務。

> [!NOTE]
> 延伸模組套件需要 MixedRealityToolkit。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/擴充功能 | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | 將物理支援新增至明確表述的服務。 |
| | LostTrackingService | 這項服務可簡化 Microsoft HoloLens 裝置上的追蹤遺失處理。 |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | 簡化加入平滑場景轉換的服務。 |

### <a name="tools-package"></a>工具套件

選用的 MixedRealityToolkit 套件包含實用的工具，可使用 Microsoft Mixed Reality 工具組強化混合現實開發體驗。
這些工具位於 Unity 編輯器中的 **混合現實工具組 > 公用程式** 功能表。

> [!NOTE]
> 此工具套件需要 MixedRealityToolkit。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/工具 | |
| | BuildWindow | 這項工具可協助簡化建立和部署 UWP 應用程式的流程。 |
| | [DependencyWindow](../features/tools/dependency-window.md) | 此工具會在專案中建立資產的相依性圖形。 |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | 協助建立延伸模組服務的 Wizard。 |
| | [MigrationWindow](../features/tools/migration-window.md) | 協助更新使用已淘汰 MRTK 元件之程式碼的工具。  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | 此公用程式可協助您自動設定混合現實專案，以獲得 Unity 的最佳效能。 |
| | ReserializeAssetsUtility | 提供 reserializing 特定 Unity 檔案的支援。 |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | 此公用程式可讓開發人員快速判斷硬體控制器的 Unity 對應。 |
| | ScreenshotUtility | 在 Unity 編輯器中啟用捕獲應用程式映射。 |
| | TextureCombinerWindow | 結合圖形材質的公用程式。 |
| | [工具箱](../features/ux-building-blocks/toolbox.md) | 可讓您輕鬆地探索及使用 MRTK UX 元件的 UI。 |

### <a name="test-utilities-package"></a>測試公用程式套件

選擇性的 MixedRealityToolkit TestUtilities 套件是協助程式腳本的集合，可讓開發人員輕鬆地 [建立播放模式測試](../contributing/unit-tests.md#play-mode-tests)。 這些公用程式特別適用于建立 MRTK 元件的開發人員。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/測試 | |
| | TestUtilities | 簡化播放模式測試建立的方法，包括手動模擬公用程式。 |

### <a name="examples-package"></a>範例套件

範例套件包含的示範、範例腳本，以及可在基礎套件中執行功能的範例幕後。 此套件包含 [HandInteractionExample 場景](../features/example-scenes/hand-interaction-examples.md) (如下圖所示) 其中包含的範例物件可回應各種類型的手寫輸入 (清楚說明的) 。

![HandInteractionExample 場景](../features/images/MRTK_Examples.png)

此套件也包含眼睛追蹤示範，其 [記載于此處](../features/example-scenes/eye-tracking-examples-overview.md)

更常見的情況是，MRTK 中的任何新功能都應該包含範例套件中的對應範例，大致遵循相同的資料夾結構和位置。

> [!NOTE]
> 這些範例套件需要 MixedRealityToolkit。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/範例 | | |
| | 示範 | 說明一或兩個相關功能的簡單場景。 |
| | 實驗 | 示範實驗性功能的示範場景。 |
| | StandardAssets | 多個示範場景所共用的常見資產。 |

## <a name="unity-package-manager"></a>Unity 封裝管理員

針對使用 unity 2019.4 和更新版本所建立的體驗，MRTK 可透過[unity 封裝管理員](https://docs.unity3d.com/Manual/Packages.html)取得。

使用資產套件的一些優點包括：

- 較小的專案
  - 更清楚的 Visual Studio 解決方案
  - 要簽入的檔案越少 (MRTK 是檔案中的簡單參考 `Packages/manifest.json`) 
- 更快速的編譯
  - Unity 不需要在建立期間重新編譯 MRTK
- 相依性解析
  - 指定具有相依性的套件時，會自動安裝必要的 MRTK 套件
- 簡易更新新的 MRTK 版本
  - 變更檔案 `Packages/manifest.json` 中的版本

其中一些挑戰如下：

- MRTK 不可變
  - 無法進行變更，而無法在封裝解析期間移除變更
- MRTK 不支援使用 Unity 2018.4 的 UPM 套件

### <a name="foundation-package"></a>基礎封裝

基礎封裝 (`com.microsoft.mixedreality.toolkit.foundation`) 形成混合現實工具組的基礎。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/核心 | | 介面和類型定義、基類、標準著色器。 |
| MRTK/核心/提供者 | | 平臺中立的資料提供者 |
| | 手 | 用於手動追蹤的基類支援和服務。 |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | 支援錄製 head 移動和手追蹤資料。 |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | 支援手形和眼睛輸入的編輯器內模擬。 |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | 空間感知觀察者使用3D 模型做為資料。 |
| | UnityInput | 一般輸入裝置 (搖桿、滑鼠等 ) 透過 Unity 的輸入 API 來執行。 |
| MRTK/提供者 | | 平臺特定的資料提供者 |
| | LeapMotion | UltraLeap Leap 移動控制器的支援。 |
| | OpenVR | OpenVR 裝置的支援。 |
| | Oculus | Oculus 裝置的支援，例如尋找。 |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) |  (實驗性) 攝影機設定提供者，讓 MRTK 與行動 AR 裝置搭配使用。 |
| | WindowsMixedReality | 支援 Windows Mixed Reality 的裝置，包括 Microsoft HoloLens 和沉浸式耳機。 |
| | Windows | Microsoft Windows 特定 api 的支援，例如語音和聽寫。 |
| | XR SDK |  (unity 2019.3 和更新版本中 [unity 新 XR 架構](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的實驗性) 支援。 |
| MRTK/SDK | | |
| | 實驗 | 實驗性功能，包括著色器、使用者介面控制項和個別系統管理員。 |
| | 功能 | 建基於基礎封裝的功能。 |
| | Profiles | Microsoft Mixed Reality 工具組系統和服務的預設設定檔。 |
| | StandardAssets | 一般資產;模型、材質、材質等等。 |
| MRTK/服務 | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | 執行 VR 界限支援的系統。 |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | 系統執行攝影機設定和管理。 |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | 在 application diagnostics 中執行的系統，例如 visual profiler。 |
| | [InputSystem](../features/input/overview.md) | 系統，提供存取和處理使用者輸入的支援。 |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | 提供多場景應用程式支援的系統。 |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | 提供使用者環境感知支援的系統。 |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | 提供 teleporting 支援的系統 (移至跳躍) 的體驗。 |

相依性：

- 標準資產 (`com.microsoft.mixedreality.toolkit.standardassets`) 

### <a name="standard-assets"></a>標準資產

標準資產套件 (`com.microsoft.mixedreality.toolkit.standardassets)` 是針對所有混合現實體驗所建議的元件集合，包括：

- MRTK 標準著色器
- 使用 MRTK 標準著色器的基本材質
- 音訊檔案
- 字型
- 紋理
- 圖示

> [!Note]
> 為了避免根據元件定義的重大變更，標準資產套件中不包含用來控制 MRTK 標準著色器某些功能的腳本。 您可以在資料夾的基礎套件中找到這些腳本 `MRTK/Core/Utilities/StandardShader` 。

相依性：無

### <a name="extension-packages"></a>擴充套件

選用的擴充套件 (`com.microsoft.mixedreality.toolkit.extensions)` 包含擴充 MRTK 功能的其他元件。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/擴充功能 | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | 將物理支援新增至明確表述的服務。 |
| | LostTrackingService | 這項服務可簡化 Microsoft HoloLens 裝置上的追蹤遺失處理。 |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | 簡化加入平滑場景轉換的服務。 |
| | 範例 ~ | Unity 編輯器中隱藏的 () 資料夾，其中包含範例場景和資產。 |

如需使用包含範例專案之封裝的詳細資訊，請參閱[混合現實工具組和 Unity 封裝管理員](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)文章。

相依性：

- Foundation (`com.microsoft.mixedreality.toolkit.foundation`) 

### <a name="tools-package"></a>工具套件

選用的工具套件 (`com.microsoft.mixedreality.toolkit.tools)` 包含適用于建立混合現實體驗的工具。 一般而言，這些工具是編輯器元件，而其程式碼不會隨附于應用程式的一部分。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/工具 | |
| | BuildWindow | 這項工具可協助簡化建立和部署 UWP 應用程式的流程。 |
| | [DependencyWindow](../features/tools/dependency-window.md) | 此工具會在專案中建立資產的相依性圖形。 |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | 協助建立延伸模組服務的 Wizard。 |
| | [MigrationWindow](../features/tools/migration-window.md) | 協助更新使用已淘汰 MRTK 元件之程式碼的工具。  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | 此公用程式可協助您自動設定混合現實專案，以獲得 Unity 的最佳效能。 |
| | ReserializeAssetsUtility | 提供 reserializing 特定 Unity 檔案的支援。 |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | 此公用程式可讓開發人員快速判斷硬體控制器的 Unity 對應。 |
| | ScreenshotUtility | 在 Unity 編輯器中啟用捕獲應用程式映射。 |
| | TextureCombinerWindow | 結合圖形材質的公用程式。 |
| | [工具箱](../features/ux-building-blocks/toolbox.md) | 可讓您輕鬆地探索及使用 MRTK UX 元件的 UI。 |

相依性：

- Foundation (`com.microsoft.mixedreality.toolkit.foundation`) 

### <a name="test-utilities-package"></a>測試公用程式套件

選用的測試公用程式套件 (`com.microsoft.mixedreality.toolkit.testutilities`) 包含協助程式腳本的集合，可讓開發人員輕鬆地建立播放模式測試。 這些公用程式特別適用于建立 MRTK 元件的開發人員。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/測試 | |
| | TestUtilities | 簡化播放模式測試建立的方法，包括手動模擬公用程式。 |

相依性：

- Foundation (`com.microsoft.mixedreality.toolkit.foundation`) 

### <a name="examples-package"></a>範例套件

範例封裝 (`com.microsoft.mixedreality.toolkit.examples`) ，其結構化可讓開發人員只匯入感興趣的範例。

如需使用包含範例專案之封裝的詳細資訊，請參閱[混合現實工具組和 Unity 封裝管理員](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)文章。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/範例 | | |
| | 範例 ~ | Unity 編輯器中隱藏的 () 資料夾，其中包含範例場景和資產。 |
| | StandardAssets | 多個示範場景所共用的常見資產。 |

相依性：

- Foundation (`com.microsoft.mixedreality.toolkit.foundation`) 
- 擴充 (`com.microsoft.mixedreality.toolkit.extensions`)

## <a name="see-also"></a>另請參閱

- [架構概觀](../architecture/overview.md)
- [系統、延伸模組服務和資料提供者](../architecture/systems-extensions-providers.md)
- [混合現實工具組和 Unity 封裝管理員](../configuration/usingupm.md)
