---
title: OpenXR 最佳做法
description: 瞭解 OpenXR 應用程式的視覺品質、穩定性和效能的最佳做法。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體、最佳作法、效能、品質、穩定性
ms.openlocfilehash: 2cbd05417f62f7380b048f692295bbbe98ceba5bce69c4f1dae21aec812ec450
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207846"
---
# <a name="openxr-app-best-practices"></a>OpenXR 應用程式最佳作法

您可以在 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>的 OpenXRProgram .cpp 檔案中看到下列最佳作法的範例。 開頭的 Run () 函式會從初始化到事件和轉譯迴圈，來捕獲一般的 OpenXR 應用程式程式碼流程。

## <a name="best-practices-for-visual-quality-and-stability"></a>視覺品質和穩定性的最佳作法

本節中的最佳作法說明如何在任何 OpenXR 應用程式中取得最佳的視覺品質和穩定性。

如需 HoloLens 2 特定的效能建議，請參閱下面 HoloLens 2 一節中的[效能最佳做法](#best-practices-for-performance-on-hololens-2)。

### <a name="gamma-correct-rendering"></a>Gamma-正確轉譯

請務必小心，以確保您的轉譯管線是 gamma 正確的。 轉譯為 swapchain 時，呈現目標視圖格式應符合 swapchain 格式。 例如， `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 針對 swapchain 格式和轉譯目標視圖。
如果應用程式的轉譯管線在著色器程式碼中執行手動 sRGB 轉換，就會發生例外狀況。 應用程式應該要求 sRGB swapchain 格式，但使用呈現目標視圖的線性格式。 例如，要求 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 為 swapchain 格式，但使用 `DXGI_FORMAT_B8G8R8A8_UNORM` 做為轉譯目標視圖，以防止內容被雙 gamma 修正。

### <a name="submit-depth-buffer-for-projection-layers"></a>提交投影層的深度緩衝區

請一律使用 `XR_KHR_composition_layer_depth` 擴充功能，並在提交框架時，連同投影層一起提交深度緩衝區 `xrEndFrame` 。
在 HoloLens 2 上啟用硬體深度 reprojection 可改善全像全像影像的穩定性。

### <a name="choose-a-reasonable-depth-range"></a>選擇合理的深度範圍

偏好較窄的深度範圍，以界定虛擬內容的範圍，以協助在 HoloLens 上建立影像穩定性。
例如，OpenXrProgram .cpp 範例使用0.1 計量至20個計量。
使用 [反向 z](https://developer.nvidia.com/content/depth-precision-visualized) 可獲得更一致的深度解析。
在 HoloLens 2 上，使用慣用的 `DXGI_FORMAT_D16_UNORM` 深度格式將有助於達到更好的畫面播放速率和效能，雖然16位深度緩衝區比24位深度緩衝區提供的深度解析度更低。
遵循這些最佳作法以充分利用深度解析會變得更重要。

### <a name="prepare-for-different-environment-blend-modes"></a>針對不同的環境 blend 模式進行準備

如果您的應用程式也會在完全封鎖世界的沉浸式耳機上執行，請務必使用 API 列舉支援的環境 blend 模式， `xrEnumerateEnvironmentBlendModes` 並正確地準備您的轉譯內容。
例如，對於具有例如 HoloLens 的系統而言， `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` 應用程式應該以透明的方式使用透明的色彩，而針對系統使用 `XR_ENVIRONMENT_BLEND_MODE_OPAQUE` ，應用程式應該在背景中轉譯一些不透明的色彩或某些虛擬房間。

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>選擇未系結的參考空間作為應用程式的根空間

應用程式通常會建立一些根全局座標空間，以將視圖、動作和全像組合連接在一起。
在 `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` 支援擴充功能以建立 [全球規模的座標系統](../../design/coordinate-systems.md#building-a-world-scale-experience)時使用，讓您的應用程式在使用者移到最 (（例如，5個計量) 離開應用程式啟動的位置）時，避免不想要的全像影像漂移。
`XR_REFERENCE_SPACE_TYPE_LOCAL`如果未系結的空間延伸模組不存在，請使用做為回復。

### <a name="associate-hologram-with-spatial-anchor"></a>將全像影像與空間錨點產生關聯

當您使用未系結的參考空間時，您直接放在該參考空間的全 [像投影可能會在使用者移到遙遠的房間之後漂移，然後再回來](../../design/coordinate-systems.md#building-a-world-scale-experience)。
若為全像使用者放在世界各地的不同位置，請使用延伸模組函式 [建立空間錨點](../../design/spatial-anchors.md#best-practices) ， `xrCreateSpatialAnchorSpaceMSFT` 並在其原點放置全像影像。 這會讓全像時間的全像變化一樣穩定。

### <a name="support-mixed-reality-capture"></a>支援 mixed reality capture

雖然 HoloLens 2 的主顯示器會使用加法的環境混合，但是當使用者啟動[mixed reality capture](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)時，應用程式的轉譯內容將會與環境影片串流進行 Alpha 混合。
若要在 mixed reality capture 影片中達成最佳的視覺品質，最好是 `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` 在投射圖層中設定 `layerFlags` 。

## <a name="best-practices-for-performance-on-hololens-2"></a>HoloLens 2 效能的最佳作法

做為具有硬體 reprojection 支援的行動裝置，HoloLens 2 有更嚴格的需求來達到最佳效能。  有許多方式可透過提交組合資料，而這會導致後續處理的效能受到顯著影響。

### <a name="select-a-swapchain-format"></a>選取 swapchain 格式

請一律使用來列舉支援 `xrEnumerateSwapchainFormats` 的像素格式，並從應用程式所支援的執行時間選擇第一個色彩和深度像素格式，因為這是執行時間慣用的最佳效能。 請注意，在 HoloLens 2 上， `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 和 `DXGI_FORMAT_D16_UNORM` 通常是達成更佳轉譯效能的第一種選擇。 在桌上型電腦上執行的 VR 耳機上，此喜好設定可能不同，其中24位深度緩衝區的效能影響較小。
  
**效能警告：** 使用主要 swapchain 色彩格式以外的格式，會導致執行時間後置處理，這會造成顯著的效能影響。

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>使用建議的轉譯參數和畫面格計時轉譯

一律使用建議的 view configuration width/height (`recommendedImageRectWidth` 和 `recommendedImageRectHeight` 從) 轉譯，並且在轉譯之前， `XrViewConfigurationView` 一律使用 `xrLocateViews` API 來查詢建議的視圖姿勢、FOV 和其他轉譯參數。
`XrFrameEndInfo.predictedDisplayTime` `xrWaitFrame` 當查詢姿勢和 views 時，請一律使用來自最新的呼叫。
這可讓 HoloLens 針對正在佩戴 HoloLens 的人員調整轉譯和優化視覺品質。

### <a name="use-a-single-projection-layer"></a>使用單一投射層

HoloLens 2 的 GPU 電源有限，可用於轉譯內容，以及針對單一投射層優化的硬體組合器。
一律使用單一投射層可協助應用程式的畫面播放速率、全像影像穩定性和視覺品質。  
  
**效能警告：** 提交任何一個保護層，會導致執行時間後置處理，而這會造成顯著的效能影響。

### <a name="render-with-texture-array-and-vprt"></a>使用材質陣列和 VPRT 轉譯

`xrSwapchain`使用 `arraySize=2` 針對色彩 swapchain 和深度來建立一個左右眼睛。
將最左邊的眼睛轉譯為配量0，並將適當的眼睛轉譯為磁區1。
使用著色器搭配 VPRT 和實例繪製呼叫來 stereoscopic 轉譯，以將 GPU 負載降至最低。
這也可以讓執行時間的優化達到 HoloLens 2 的最佳效能。
使用紋理陣列的替代方案（例如雙範圍轉譯或個別的 swapchain），會導致執行時間後置處理，而這會造成顯著的效能影響。

### <a name="avoid-quad-layers"></a>避免四層

將四個階層直接轉譯成投射圖層，而不是以組合圖層的形式提交四個圖層 `XrCompositionLayerQuad` 。

**效能警告：** 提供超出單一投射層的額外層級（例如四層）將會導致執行時間後置處理，而這會造成顯著的效能影響。