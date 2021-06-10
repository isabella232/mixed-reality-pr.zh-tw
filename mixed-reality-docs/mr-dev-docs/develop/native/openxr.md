---
title: OpenXR
description: 使用可移植 OpenXR API 標準建立引擎，並將其部署到 Windows Mixed Reality 和 HoloLens 2 耳機。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR、藍圖、延伸模組、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體
ms.openlocfilehash: 98b75f8b6059e6537d4cb4a10ecf8d057ad19a07
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110711537"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR 是 <a href="https://www.khronos.org/" target="_blank">Khronos</a>的開放免權利 API 標準，提供可在 [混合現實](../../discover/mixed-reality.md)範圍內原生存取各種裝置的引擎。

您可以在 HoloLens 2 上使用 OpenXR 或在電腦上使用 Windows Mixed Reality 沉浸式頭戴裝置進行開發。  如果您沒有耳機的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

## <a name="why-openxr"></a>為什麼要 OpenXR？

有了 OpenXR，您就可以建立以這兩種全像攝影裝置為目標的引擎，例如 HoloLens 2 和沉浸式裝置，例如桌上型電腦的 Windows Mixed Reality 耳機。 OpenXR 可讓您撰寫程式碼一次，然後在各種不同的硬體平臺上進行移植。

OpenXR API 會使用載入器，將您的應用程式直接連接到耳機的原生平臺支援。 使用者可以取得最大效能和最小延遲，不論它們是使用 Windows Mixed Reality 還是任何其他耳機。

## <a name="what-is-openxr"></a>什麼是 OpenXR？

OpenXR API 提供核心的預測、框架時間和空間輸入功能，您必須建立可將全像全像全像全像裝置的引擎。

若要瞭解 OpenXR API，請參閱 OpenXR 1.0 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">規格</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 參考</a>和 <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速參考指南</a>。  如需詳細資訊，請參閱 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 頁面</a>。

若要以 HoloLens 2 的完整功能集為目標，您也會使用跨廠商和供應商專屬的 OpenXR 延伸模組，以啟用 OpenXR 1.0 核心以外的其他功能，例如明確的手追蹤、眼睛追蹤、空間對應和空間錨點。 如需詳細資訊，請參閱下面的「 [藍圖」一節](#roadmap) ，以瞭解今年稍後推出的延伸模組。

OpenXR 本身不是混合的現實引擎。  相反地，OpenXR 能讓 Unity 和 Unreal 等引擎撰寫可移植的程式碼一次，之後就可以存取使用者全像或沉浸式裝置的原生平臺功能。

## <a name="roadmap"></a>藍圖

OpenXR 規格定義了延伸機制，可讓執行時間實作者在<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">基底 OpenXR 1.0 規格</a>中定義的[核心功能](#what-is-openxr)之外公開其他功能。

有三種類型的 OpenXR 延伸模組：
* **廠商擴充 (例如， `MSFT`) ：** 可在硬體或軟體功能中提供每一廠商的創新。  任何執行時間廠商都可以隨時引進並交付廠商延伸模組。
  * **實驗性廠商延伸 (例如 `MSFT_preview`) ：** 要預覽的實驗性廠商延伸模組，以收集意見反應。  `MSFT_preview` 擴充功能僅適用于開發人員裝置，並會在真正的延伸模組發行時移除。  若要進行實驗，您可以 [在開發人員裝置上啟用預覽延伸](openxr-getting-started.md#using-preview-extensions)模組。
* **跨廠商 `EXT` 延伸模組：** 多個公司所定義和實行的跨廠商擴充功能。  有興趣的公司群組隨時都可以引進 EXT 延伸模組。
* **官方 `KHR` 延伸模組：** 正式 Khronos 延伸模組會在核心規格版本中核准。  KHR 延伸模組是與核心規格本身相同的授權所涵蓋。

Windows Mixed Reality OpenXR 執行時間支援一組 `MSFT` 和 `EXT` 延伸模組，可為 OpenXR 應用程式帶來一組完整的 HoloLens 2 功能：

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
| 與其他 HoloLens Sdk Interop<br /> (例如， [QR](../platform-capabilities-and-apis/qr-code-tracking.md)) <p>*僅 HoloLens 2*</p> | <p>**`MSFT` 執行時間102中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` 執行時間105中的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| [混合實境擷取 <br /> (PV 攝影機的第三個轉譯) ](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*僅 HoloLens 2*</p> | **`MSFT` 執行時間102中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| 使用 UWP CoreWindow API 進行 Interop<br />例如鍵盤/滑鼠) 的 ( | **`MSFT` 執行時間103中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| 移動控制器互動設定檔<br /> (Samsung 電影對白和 HP 回音)  | **`MSFT` 執行時間103中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [移動控制器轉譯模型](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` 執行時間104中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [場景理解 (平面、網格) ](../../design/scene-understanding.md)<p>*僅 HoloLens 2*</p> | <p>**從執行時間102：**<br />搭配 <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> [場景理解 SDK](../platform-capabilities-and-apis/scene-understanding-sdk.md)使用</p><p>**`MSFT`[預覽執行時間 105](openxr-getting-started.md#using-preview-extensions)中的延伸模組：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_preview2">XR_MSFT_scene_understanding_preview2</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_serialization_preview">XR_MSFT_scene_understanding_serialization_preview</a></code></p> |
| [組合圖層 reprojection 模式 <br /> (自動平面或僅限方向的 reprojection) ](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT`[預覽執行時間 105](openxr-getting-started.md#using-preview-extensions)中的延伸模組：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_composition_layer_reprojection_preview">XR_MSFT_composition_layer_reprojection_preview</a></code> |
| 其他跨廠商擴充功能 | <p>**正式 `KHR` 推出的延伸模組：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code><p>**`EXT` 發行的延伸模組：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

雖然其中有些擴充功能可能會隨著廠商專屬的延伸模組而開始 `MSFT` ，但 Microsoft 和其他 OpenXR 執行時間廠商會共同合作， `EXT` 為 `KHR` 許多這些功能領域設計跨廠商或延伸模組。 跨廠商擴充功能可讓您撰寫的程式碼在執行時間廠商之間可移植，如同核心規格。

## <a name="getting-started-with-openxr"></a>開始使用 OpenXR

![使用者佩戴混合現實耳機時所播放 Minecraft 的螢幕擷取畫面](images/openxr-minecraft.jpg)

*Minecraft 的新 RenderDragon 引擎已使用 OpenXR 建立其桌上型電腦 VR 支援！*

Microsoft 一直在使用 Unity 和複雜的遊戲，以確保混合現實的未來已開放使用，而不只是為了 HoloLens 2，還能橫跨電腦 VR 的完整廣度，包括 [HP 的新的「回音」 G2 耳機](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。  OpenXR 會提供現今主要貨物運送的跨廠商 VR 支援，例如 Minecraft 和 Microsoft 航班模擬器！  如需有關開發 HoloLens (第一代) 的詳細資訊，請參閱 [版本](/hololens/hololens1-release-notes)資訊。

若要瞭解如何在 Unity、Unreal Engine 或您自己的引擎中開始使用 OpenXR，請繼續閱讀！

### <a name="openxr-in-unity"></a>Unity 中的 OpenXR

現今 HoloLens 2、HoloLens (第一代) 和 Windows Mixed Reality 耳機的支援 Unity 開發路徑，是現有的 WinRT API 後端的 **unity 2019 LTS** 。  您可以 [使用 Unity](../unity/openxr-getting-started.md)跳到 OpenXR;如果您將目標設為 Unity 2019 應用程式中的新 HP 回音 G2 控制器，請參閱我們的 Hp 的「 [回音」輸入](../unity/unity-reverb-g2-controllers.md)檔。

從 **unity 2020 LTS** 開始，unity 提供了支援 HoloLens 2 和 Windows Mixed Reality 耳機的 [OpenXR 後端](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/) 。  這包括對 OpenXR 延伸模組的支援，這些擴充 [功能可讓 HoloLens 2 和 Windows Mixed Reality 耳機的完整功能](#roadmap)，包括手上/眼睛追蹤、空間錨點和 HP 等號 G2 控制器。  MRTK-Unity 支援從 [MRTK 2.7](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)的 OpenXR。  如需有關 HoloLens 2 的 Unity 2020 LTS 支援目前狀態的詳細資訊，請參閱 [選擇 Unity 版本](../unity/choosing-unity-version.md)。

從 **Unity 2021** 開始，OpenXR 接著會畢業為目標 HoloLens 2 和 Windows Mixed Reality 耳機的唯一支援 Unity 後端。

### <a name="openxr-in-unreal-engine"></a>Unreal 引擎中的 OpenXR

從 **Unreal 引擎 4.23**，HoloLens 2 和 Windows Mixed Reality 耳機的完整支援可透過 Windows Mixed Reality (WinRT) 外掛程式取得。

Unreal Engine 4.23 也是第一個提供 OpenXR 1.0 預覽支援的主要遊戲引擎版本！  現在在 **Unreal engine 4.26** 中，HoloLens 2、Windows Mixed Reality 和其他 desktop VR 耳機的支援可透過 Unreal 引擎的內建 OpenXR 支援提供。  Unreal Engine 4.26 也支援 [Microsoft 的 OpenXR 延伸模組外掛程式](https://github.com/microsoft/Microsoft-OpenXR-Unreal)、啟用手互動和 HP 迴響 G2 控制器支援、HoloLens 2 的 [完整功能集，以及 Windows Mixed Reality 耳機](#roadmap)。  Unreal Engine 4.26 現在可在長篇的 [遊戲啟動器](https://www.unrealengine.com/download/creators)上取得，MRTK-Unreal 的支援將于4月推出。


### <a name="openxr-for-native-development"></a>適用于原生開發的 OpenXR

您可以在 HoloLens 2 上使用 OpenXR 或在電腦上使用 Windows Mixed Reality 沉浸式頭戴裝置進行開發。  如果您沒有耳機的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

若要開始開發 HoloLens 2 或沉浸式 Windows Mixed Reality 耳機的 OpenXR 應用程式，請參閱 [如何開始使用 OpenXR 開發](openxr-getting-started.md)。

如需 OpenXR API 的所有主要元件的教學課程，以及目前使用 OpenXR 的真實世界應用程式範例，請參閱此60分鐘逐步解說影片：

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>另請參閱

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR 的詳細資訊</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 參考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速參考指南</a>