---
title: OpenXR
description: 使用可移植 OpenXR API 標準建立引擎，並將其部署到 Windows Mixed Reality 和 HoloLens 2 耳機。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體
ms.openlocfilehash: 519d363c49f86a47eeaa5872c6f7911e12276c99
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903099"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR 是 <a href="https://www.khronos.org/" target="_blank">Khronos</a> 的開放免權利 API 標準，可為引擎提供原生存取範圍廣泛的各種裝置，這些廠商橫跨 [混合的現實](../../discover/mixed-reality.md)範圍。

您可以在 HoloLens 2 上使用 OpenXR 或在電腦上使用 Windows Mixed Reality 沉浸式頭戴裝置進行開發。  如果您沒有耳機的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

## <a name="why-openxr"></a>為什麼要 OpenXR？

有了 OpenXR，您就可以建立以兩種全像全像的裝置為目標的引擎 (像是 HoloLens 2) 將數位內容放在真實世界中，如同真正的所在一樣，還有沉浸式裝置 (像是桌上型電腦的 Windows Mixed Reality 耳機) 隱藏了實體世界，並以數位體驗取代。  OpenXR 可讓您撰寫程式碼一次，然後在各種不同的硬體平臺上進行移植。

OpenXR API 會使用載入器，將您的應用程式直接連接到耳機的原生平臺支援。  這可讓您的終端使用者在使用 Windows Mixed Reality 耳機或任何其他耳機時，達到最大效能和最小延遲。

## <a name="what-is-openxr"></a>什麼是 OpenXR？

OpenXR API 提供核心的預測、幀計時和空間輸入功能，您必須建立一個可將所有的全像裝置（例如 HoloLens 2 和沉浸式裝置，例如 Windows Mixed Reality 耳機的引擎）作為目標的引擎。

若要瞭解 OpenXR API，請參閱 OpenXR 1.0 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">規格</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 參考</a> 和 <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速參考指南</a>。  如需詳細資訊，請參閱 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 頁面</a>。

若要以 HoloLens 2 的完整功能集為目標，您也會使用跨廠商和供應商專屬的 OpenXR 延伸模組，以啟用 OpenXR 1.0 核心以外的其他功能，例如明確的手追蹤、眼睛追蹤、空間對應和空間錨點。  請參閱下面的「 [藍圖」一節](#roadmap) ，以取得今年稍後所推出的延伸模組的詳細資訊。

請注意，OpenXR 本身並不是混合的現實引擎。  相反地，OpenXR 能讓 Unity 和 Unreal 這類引擎撰寫可移植的程式碼一次，之後無論哪一家廠商建立該平臺，都可以存取使用者的全像或沉浸式裝置的原生平臺功能。

## <a name="roadmap"></a>藍圖

OpenXR 規格定義了延伸機制，可讓執行時間實作者在<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">基底 OpenXR 1.0 規格</a>中定義的[核心功能](#what-is-openxr)之外公開其他功能。

有三種類型的 OpenXR 延伸模組：
* **廠商延伸模組 (例如 `MSFT`) ：** 可在硬體或軟體功能中提供每一廠商的創新。  任何執行時間廠商都可以隨時引進並交付廠商延伸模組。
  * **實驗性廠商延伸 (例如 `MSFT_preview`) ：** 要預覽的實驗性廠商延伸模組，以收集意見反應。  `MSFT_preview` 擴充功能僅適用于開發人員裝置，並會在真正的延伸模組發行時移除。  若要進行實驗，您可以 [在開發人員裝置上啟用預覽延伸](openxr-getting-started.md#using-preview-extensions)模組。
* **跨廠商 `EXT` 延伸模組：** 多個公司所定義和實行的跨廠商擴充功能。  有興趣的公司群組隨時都可以引進 EXT 延伸模組。
* **官方 `KHR` 延伸模組：** 正式 Khronos 延伸模組會在核心規格版本中核准。  KHR 延伸模組是與核心規格本身相同的授權所涵蓋。

從2020年7月起，Windows Mixed Reality OpenXR 執行時間支援一組和延伸模組，可 `MSFT` `EXT` 為 OpenXR 應用程式帶來一組完整的 HoloLens 2 功能：

| 功能區域 | 延伸模組可用性 |
|--------------|------------------------|
| 系統 + 會話 | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [參考空間 (view、local、stage) ](../../design/coordinate-systems.md) | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
|  (mono、身歷聲) 視圖設定 | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Swapchains](../platform-capabilities-and-apis/rendering.md)  + [畫面格時間](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| 組合圖層<br /> (投射，四)  | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [輸入和 haptics](../../design/interaction-fundamentals.md) | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 整合 | **正式 `KHR` 擴充功能已發行：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12 整合 | **正式 `KHR` 擴充功能已發行：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [無限制的參考空間 <br /> (世界規模的體驗) ](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` 發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [空間錨點](../../design/spatial-anchors.md) | **`MSFT` 發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [手 <br /> 上互動 (把手/目標姿勢、碰點、抓住) ](../../design/hands-and-tools.md)<p>*僅 HoloLens 2*</p> | **`MSFT` 發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [手錶達 + 手形網格](../../design/hands-and-tools.md)<p>*僅 HoloLens 2*</p> | <p>**`EXT` 執行時間102中發行的延伸模組：**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` 執行時間102中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [眼睛目光](../../design/eye-tracking.md)<p>*僅 HoloLens 2*</p> | **`EXT` 發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| 與其他 HoloLens Sdk Interop<br /> (例如 [QR](../platform-capabilities-and-apis/qr-code-tracking.md)) <p>*僅 HoloLens 2*</p> | <p>**`MSFT` 執行時間102中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT`[預覽執行時間 104](openxr-getting-started.md#using-preview-extensions)中的延伸模組：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_perception_anchor_interop_preview">XR_MSFT_perception_anchor_interop_preview</a></code></p> |
| [混合實境擷取 <br /> (PV 攝影機的第三個轉譯) ](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*僅 HoloLens 2*</p> | **`MSFT` 執行時間102中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| 使用 UWP CoreWindow API 進行 Interop<br /> (例如鍵盤/滑鼠)  | **`MSFT` 執行時間103中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| 移動控制器互動設定檔 (Samsung 電影對白和 HP 迴響 G2)  | **`MSFT` 執行時間103中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [移動控制器轉譯模型](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT`[預覽執行時間 104](openxr-getting-started.md#using-preview-extensions)中的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [場景理解 (平面、網格) ](../../design/scene-understanding.md)<p>*僅 HoloLens 2*</p> | <p>**在 [預覽執行時間102或更新版本](openxr-getting-started.md#using-preview-extensions)中：**<br />搭配 <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> [場景理解 SDK](../platform-capabilities-and-apis/scene-understanding-sdk.md)使用</p><p>**`MSFT_preview` 未來預覽執行時間中的延伸** 模組 *(計畫的)*</p> |
| 其他跨廠商擴充功能 | <p>**正式 `KHR` 推出的延伸模組：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT` 發行的延伸模組：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

雖然其中有些擴充功能可能會隨著廠商專屬的延伸模組而開始 `MSFT` ，但 Microsoft 和其他 OpenXR 執行時間廠商會共同合作， `EXT` 為 `KHR` 許多這些功能領域設計跨廠商或延伸模組。  這可讓您針對這些功能所撰寫的程式碼可在執行時間廠商之間移植，就像核心規格一樣。

## <a name="get-started-with-openxr"></a>開始使用 OpenXR

您可以在 HoloLens 2 上使用 OpenXR 或在電腦上使用 Windows Mixed Reality 沉浸式頭戴裝置進行開發。  如果您沒有耳機的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

若要開始開發 HoloLens 2 或沉浸式 Windows Mixed Reality 耳機的 OpenXR 應用程式，請參閱 [如何開始使用 OpenXR 開發](openxr-getting-started.md)。

如需 OpenXR API 的所有主要元件的教學課程，以及目前使用 OpenXR 的真實世界應用程式範例，請參閱此60分鐘逐步解說影片：

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>請參閱

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR 的詳細資訊</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 參考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速參考指南</a>
