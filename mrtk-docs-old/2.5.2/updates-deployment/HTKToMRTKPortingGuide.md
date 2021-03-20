---
title: HTKToMRTKPortingGuide
description: 從 HTK 遷移至 MRTK。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、HTK、
ms.openlocfilehash: 443319c78a8d7b5b80d328758d981edebf7858c1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686452"
---
# <a name="porting-guide"></a>移植指南

## <a name="controller-and-hand-input"></a>控制器和手輸入

### <a name="setup-and-configuration"></a>設定和組態

|            方法               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 類型                      | 按鈕的特定事件，以及相關的輸入類型資訊。 | 動作/手勢型輸入，通過事件傳遞。 |
| 設定                     | 將 InputManager 放置在場景中。 | 在設定 [設定檔](../configuration/MixedRealityConfigurationGuide.md) 中啟用輸入系統，並指定具體的輸入系統類型。 |
| 組態             | 設定于偵測器中，在場景中的每個個別腳本上。 | 透過混合現實輸入系統設定檔及其相關設定檔設定，如下所示。 |

相關設定檔：

* 混合現實控制器對應設定檔
* 混合現實控制器視覺效果設定檔
* 混合現實手勢設定檔
* 混合現實輸入動作設定檔
* 混合現實輸入動作規則設定檔
* 混合現實指標設定檔

在場景中的主要攝影機物件上，會修改[注視提供者](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)設定。

平臺支援元件 (例如，必須將 Windows Mixed Reality 裝置管理員) 新增至其對應服務的資料提供者。

### <a name="interface-and-event-mappings"></a>介面和事件對應

某些事件不再有唯一的事件，現在包含 [MixedRealityInputAction](../features/input/InputActions.md)。 這些動作會指定于輸入動作設定檔中，並對應至控制器對應設定檔中的特定控制器和平臺。 像這樣 `OnInputDown` 的事件現在應該會檢查 MixedRealityInputAction 類型。

相關的輸入系統：

* [輸入概觀](../features/input/Overview.md)
* [輸入事件](../features/input/InputEvents.md)
* [輸入指標](../features/input/Pointers.md)

| HTK 2017 |  MRTK v2  | 動作對應 |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 對應至觸控板或操縱杆 |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | 對應至觸控板 |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | 對應以保存手勢設定檔 |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | 對應到控制器的按鈕或點一下 |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 對應至手勢設定檔中的操作 |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 對應至手勢設定檔中的導覽 |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 對應至觸發程式位置 |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 或 [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 對應到指標位置或手柄位置 |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 或 [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 對應到指標位置或手柄位置 |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) 和 [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 對應至各種控制器按鈕和 thumbsticks |

## <a name="camera"></a>相機

|       方法                    | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 設定                     | 刪除 MainCamera、將 MixedRealityCameraParent/MixedRealityCamera/HoloLensCamera 預製專案新增至場景 **或** 使用混合現實工具組 > 設定 > 套用混合現實場景設定] 功能表項目。 | 透過混合現實工具組在 MixedRealityPlayspace 底下 MainCamera 父代 > 新增至場景並設定 .。。 |
| 組態             | 在預製專案實例上執行的相機設定設定。 | 在 [混合實境相機設定檔](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile)中設定的相機設定。 |

## <a name="speech"></a>語音

### <a name="keyword-recognition"></a>關鍵字辨識

|          方法                 | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 設定                     | 將 SpeechInputSource 新增至您的場景。 | 關鍵字服務 (例如，Windows 語音輸入管理員) 必須加入至輸入系統的資料提供者。 |
| 組態             | 已辨識的關鍵字是在 SpeechInputSource 的偵測器中設定。 | 關鍵字是在 [Mixed Reality 語音命令設定檔](../features/input/Speech.md)中設定。 |
| 事件處理常式            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>聽寫

|             方法              | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 設定                     | 將 DictationInputManager 新增至您的場景。 | 聽寫支援需要服務 (例如，Windows 聽寫輸入管理員) 要加入至輸入系統的資料提供者。 |
| 事件處理常式            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>空間感知/對應

### <a name="mesh"></a>網狀

|         方法                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 設定                     | 將 SpatialMapping 預製專案加入場景。 | 在設定設定檔中啟用空間感知系統，並新增空間觀察者 (例如 Windows Mixed Reality 空間網格觀察器) 至空間感知系統的資料提供者。 |
| 組態             | 在偵測器中設定場景實例。 | 設定每個空間觀察者設定檔的設定。 |

### <a name="planes"></a>飛機

|              方法             | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 設定                     | 使用 `SurfaceMeshesToPlanes` 腳本。 | 尚未實作。 |

### <a name="spatial-understanding"></a>空間理解

|               方法            | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 設定                     | 將 SpatialUnderstanding 預製專案加入場景。 | 尚未實作。 |
| 組態             | 在偵測器中設定場景實例。 | 尚未實作。 |

## <a name="boundary"></a>界限

|            方法               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 設定                     | 將 `BoundaryManager` 腳本加入場景中。 | 在設定檔中啟用界限系統。 |
| 組態             | 在偵測器中設定場景實例。 | 設定界限視覺效果設定檔中的設定。 |

## <a name="sharing"></a>共用

|               方法            | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 設定                     | 共用服務：新增共用預製專案至場景。 UNet：使用 SharingWithUNET 範例。 | 進行中 |
| 組態             | 在偵測器中設定場景實例。 | 進行中 |

## <a name="ux"></a>Ux

|        方法                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 按鈕                     | [互動物件](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/InteractableObjectExample.md) | [按鈕](../features/ux-building-blocks/Button.md) |
| 互動                     | [互動物件](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/InteractableObjectExample.md) | [互動](../features/ux-building-blocks/Interactable.md) |
| 週框方塊             | [周框方塊](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/BoundingBoxGizmoExample.md) | [周框方塊](../features/ux-building-blocks/BoundingBox.md) |
| 應用程式行             | [應用程式行](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/BoundingBoxGizmoExample.md) | [應用程式行](../features/ux-building-blocks/AppBar.md) |
| 單次操作 (Grb 並移動)    | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [操作處理常式](../features/ux-building-blocks/ManipulationHandler.md) |
| 雙手勢操作 (抓取/移動/旋轉/調整)              | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [操作處理常式](../features/ux-building-blocks/ManipulationHandler.md) |
| 鍵盤             | [鍵盤預製專案]() | [系統鍵盤](../features/ux-building-blocks/SystemKeyboard.md) |
| 工具提示             | [工具提示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/TooltipExample.md) | [工具提示](../features/ux-building-blocks/Tooltip.md) |
| 物件集合             | [物件集合](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/ObjectCollection.md) | [物件集合](../features/ux-building-blocks/ObjectCollection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/Solver.md) |

## <a name="utilities"></a>公用程式

有些公用程式已與規劃工具系統一致。 如果遺漏任何您需要的腳本，請提出問題。

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| 廣告 牌 | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Tagalong | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) 或 [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [規劃求解](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[規劃求解](../features/ux-building-blocks/solvers/Solver.md) |
| FpsDisplay | 設定檔中的[診斷系統](../features/diagnostics/DiagnosticsSystemGettingStarted.md) ()  |
| NearFade | 內建的 [混合現實工具組標準著色器](../features/rendering/MRTKStandardShader.md) |
