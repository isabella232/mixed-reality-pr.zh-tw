---
title: OptimizeWindow
description: MRTK 中的檔優化視窗
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 4908877a4c81f4b54f059a941148250980761984
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781438"
---
# <a name="optimize-window"></a>優化視窗

[MRTK 優化] 視窗是一種公用程式，可協助自動化和通知設定混合現實專案的程式，以達到 Unity 的最佳 [效能](../../performance/PerfGettingStarted.md) 。 此工具通常著重于將設定設為正確預設值的設定，可節省處理的毫秒數。

作用中的 *組建目標* 是目前由專案進行編譯的 [組建平臺](https://docs.unity3d.com/Manual/BuildSettings.html) 。

*效能目標* 會指示優化工具的目標裝置端點類型。

- *AR 耳機* 是行動裝置類別的裝置，例如 HoloLens
- *VR 獨立式* 是行動裝置類別的裝置，例如 Oculus Go 或尋找
- *VR 行動網卡* 是電腦支援的裝置，例如 Samsung 電影對白、Oculus RIFT 或 HTC Vive 等等。

![MRTK 優化視窗效能目標](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>設定優化

[設定優化] 索引標籤包含 Unity 專案的一些重要轉譯設定。 本節可協助自動化，並通知您應變更哪些設定，以獲得最佳的執行結果。

綠色核取圖示表示已在專案/場景中為此特定設定設定最佳值。 黃色警告圖示表示可以改善目前的設定。 按一下指定區段中的相關聯按鈕，會將 Unity 專案/場景中的該設定自動設定為更理想的值。

![MRTK 優化視窗設定](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>單一階段實例轉譯

[單一傳遞實例](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 轉譯是混合現實應用程式最有效率的轉譯路徑。 這項設定可確保轉譯管線只針對兩個眼睛執行一次，而且繪製呼叫會在兩個眼睛之間進行具現化。

### <a name="depth-buffer-sharing"></a>深度緩衝區共用

為了改善全像全 [像影像，](../../performance/hologram-Stabilization.md)開發人員可以共用應用程式的深度緩衝區，以提供平臺資訊給要在轉譯的場景中穩定的位置和位置。

### <a name="depth-buffer-format"></a>深度緩衝區格式

此外，對於 *AR 耳機*，建議在啟用深度緩衝區共用時使用16位深度格式，相較于24位。 這表示較低的精確度，但會節省效能。 如果因為計算圖元深度的精確度較不精確而發生 [z 的](https://en.wikipedia.org/wiki/Z-fighting) 問題，建議您將距離最接近相機的 [剪切平面](https://docs.unity3d.com/Manual/class-Camera.html) 移 (例如：50m，而不是變更為 1000m) 。

> [!NOTE]
> 如果使用 *16 位深度格式*，則樣板緩衝區所需的效果將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。 相反地，選取 *24 位深度格式* 通常會建立 [8 位的樣板緩衝區](https://docs.unity3d.com/Manual/SL-Stencil.html)（如果適用于端點圖形平台）。
>
> 如果使用需要樣板緩衝區的 [遮罩元件](https://docs.unity3d.com/Manual/script-Mask.html) ，請考慮改用 [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) ，這不需要樣板緩衝區，因此可與 *16 位深度格式* 搭配使用。

### <a name="real-time-global-illumination"></a>即時全球照明

Unity 中的[即時全球照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供絕佳的美觀結果，但代價很高。 全球照明照明在混合現實中相當昂貴，因此建議您在開發期間停用這項功能。

> [!NOTE]
> Unity 中的全域照明設定是針對每個場景設定，而不是在整個專案中進行一次。

## <a name="scene-analysis"></a>場景分析

[ *場景分析* ] 索引標籤的設計目的，是要通知開發人員目前在場景中的元素，可能會對效能造成最大的影響。

![MRTK 優化視窗場景分析](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>光源分析

本節將檢查目前在場景中的燈數目，以及應該停用陰影的任何燈光。 陰影轉換是非常耗費資源的作業。

### <a name="polygon-count-analysis"></a>多邊形計數分析

此工具也會提供多邊形計數統計資料。 快速識別哪些 Gameobject 在指定場景中具有最高的多邊形複雜度以進行優化，可能會非常有説明。

### <a name="unity-ui-raycast-analysis"></a>Unity UI raycast 分析

圖形 raycast 作業會在 MRTK 中針對每個指標執行，以判斷是否有任何 Unity UI 元素成為焦點。 這些 raycasts 可能相當昂貴，而且為了協助改善效能，不需要在結果中傳回的 UI 元素應該停用為 raycast 目標。 每個 [圖形](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) 元素都有 [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) 屬性。 此工具會搜尋已啟用這個屬性的文字 UI 元素，因此可能會被停用。

## <a name="shader-analysis"></a>著色器分析

[Unity 標準著色器](https://docs.unity3d.com/Manual/shader-StandardShader.html)可以為遊戲產生非常高品質的視覺效果結果，但通常不適合混合現實應用程式的效能需求，特別是因為這類應用程式通常是 GPU 界限。 因此，建議開發人員利用 [MRTK 標準著色器](../rendering/MRTKStandardShader.md) 來平衡美學 & 圖形功能與效能。

[ *著色器分析* ] 索引標籤會使用 Unity 標準著色器來掃描目前專案的物料資產資料夾，或在需要時，使用「混合現實」工具組提供著色器的所有材質。 一旦探索到之後，開發人員就可以使用適當的按鈕來轉換所有材質或個別轉換。

![MRTK 優化視窗著色器分析](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>另請參閱

- [效能](../../performance/PerfGettingStarted.md)
- [全像穩定](../../performance/hologram-stabilization.md)
