---
title: MRTK_PakageContents
description: 與 MRTK 和 XR SDK 相關的套件。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 28b6766eefbd782a232e5738b80095032c662e0b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780715"
---
# <a name="mixed-reality-toolkit-packages"></a>混合現實工具組套件

Microsoft Mixed Reality 工具組是以套件集合的形式提供。 下列各節將說明這些封裝的內容。

- [基礎](#foundation)
- [擴充功能](#extensions)
- [工具](#tools)
- [範例](#examples)

## <a name="foundation"></a>Foundation

MixedRealityToolkit 套件包含建立混合現實應用程式所需的核心元件。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/核心 | | 介面和類型定義、基類、標準著色器。 |
| MRTK/提供者 | | |
| | [ObjectMeshObserver](../features/SpatialAwareness/SpatialObjectMeshObserver.md) | 空間感知觀察者使用3D 模型做為資料。 |
| | OpenVR | OpenVR 裝置的支援。 |
| | [UnityAR](../features/CameraSystem/UnityArCameraSettings.md) |  (實驗性) 攝影機設定提供者，讓 MRTK 與行動 AR 裝置搭配使用。 |
| | WindowsMixedReality | Windows Mixed Reality 裝置的支援，包括 Microsoft HoloLens 和沉浸式耳機。 |
| | WindowsVoiceInput | 支援 Microsoft Windows 平臺上的語音和聽寫。 |
| | XRSDK |  (unity 2019.3 中 [unity 新 XR 架構](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 的實驗性) 支援。 |
| MRTK/SDK | | |
| | 實驗 | 實驗性功能，包括著色器、使用者介面控制項和個別系統管理員。 |
| | 功能 | 建基於基礎封裝的功能。 |
| | Profiles | Microsoft Mixed Reality 工具組系統和服務的預設設定檔。 |
| | StandardAssets | 一般資產;模型、材質、材質等等。 |
| MRTK/服務 | | |
| | [BoundarySystem](../features/Boundary/BoundarySystemGettingStarted.md) | 執行 VR 界限支援的系統。 |
| | [CameraSystem](../features/CameraSystem/CameraSystemOverview.md) | 系統執行攝影機設定和管理。 |
| | [DiagnosticsSystem](../features/Diagnostics/DiagnosticsSystemGettingStarted.md) | 在 application diagnostics 中執行的系統，例如 visual profiler。 |
| | [InputAnimation](../features/InputSimulation/InputAnimationRecording.md) | 支援錄製 head 移動和手追蹤資料。 |
| | [InputSimulation](../features/InputSimulation/InputSimulationService.md) | 支援手形和眼睛輸入的編輯器內模擬。 |
| | [InputSystem](../features/Input/Overview.md) | 系統，提供存取和處理使用者輸入的支援。 |
| | [SceneSystem](../features/SceneSystem/SceneSystemGettingStarted.md) | 提供多場景應用程式支援的系統。 |
| | [SpatialAwarenessSystem](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md) | 提供使用者環境感知支援的系統。 |
| | [TeleportSystem](../features/TeleportSystem/Overview.md) | 提供 teleporting 支援的系統 (移至跳躍) 的體驗。 |

## <a name="extensions"></a>延伸模組

選用的 MixedRealityToolkit 套件包含擴充 Microsoft Mixed Reality 工具組功能的其他服務。

> [!NOTE]
> 延伸模組套件需要 MixedRealityToolkit。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/擴充功能 | |
| | HandPhysicsService | 將物理支援新增至明確表述的服務。 |
| | LostTrackingService | 這項服務可簡化 Microsoft HoloLens 裝置上的追蹤遺失處理。 |
| | [SceneTransitionService](../features/Extensions/SceneTransitionService/SceneTransitionServiceOverview.md) | 簡化加入平滑場景轉換的服務。 |

## <a name="tools"></a>工具

選用的 MixedRealityToolkit 套件包含實用的工具，可使用 Microsoft Mixed Reality 工具組強化混合現實開發體驗。
這些工具位於 Unity 編輯器中的 **混合現實工具組 > 公用程式** 功能表。

> [!NOTE]
> 此工具套件需要 MixedRealityToolkit。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/工具 | |
| | [DependencyWindow](../features/Tools/DependencyWindow.md) | 此工具會在專案中建立資產的相依性圖形。 |
| | [ExtensionServiceCreator](../features/Tools/ExtensionServiceCreationWizard.md) | 協助建立延伸模組服務的 Wizard。 |
| | [OptimizeWindow](../features/Tools/OptimizeWindow.md) | 此公用程式可協助您自動設定混合現實專案，以獲得 Unity 的最佳效能。 |
| | ReserializeAssetsUtility | 提供 reserializing 特定 Unity 檔案的支援。 |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/Tools/ControllerMappingTool.md) | 此公用程式可讓開發人員快速判斷硬體控制器的 Unity 對應。 |
| | ScreenshotUtility | 在 Unity 編輯器中啟用捕獲應用程式映射。 |
| | TextureCombinerWindow | 結合圖形材質的公用程式。 |

## <a name="examples"></a>範例

選擇性的 MixedRealityToolkit 範例套件包含說明 Microsoft Mixed Reality 工具組功能的示範專案。

> [!NOTE]
> 這些範例套件需要 MixedRealityToolkit。

| 資料夾 | 元件 | 描述 |
| --- | --- | --- |
| MRTK/範例 | | |
| | 示範 | 說明一或兩個相關功能的簡單場景。 |
| | 實驗 | 示範實驗性功能的示範場景。 |
| | 督察 | 示範場景所使用的 Unity 編輯器偵測器。 |
| | StandardAssets | 多個示範場景所共用的常見資產。 |

## <a name="see-also"></a>另請參閱

- [歡迎使用 MRTK](../WelcomeToMRTK.md)
- [NuGet 封裝](MRTKNuGetPackage.md)
