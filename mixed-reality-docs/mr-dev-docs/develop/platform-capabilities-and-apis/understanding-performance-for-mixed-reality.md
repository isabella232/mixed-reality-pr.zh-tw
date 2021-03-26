---
title: 瞭解混合現實的效能
description: 瞭解分析和優化 Windows Mixed Reality 應用程式效能的 advanced 資訊和詳細資料。
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，效能，優化，CPU，GPU
ms.openlocfilehash: eabc151382652bc2588249ef78d2f9f3b0f8cd99
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550118"
---
# <a name="understanding-performance-for-mixed-reality"></a>瞭解混合現實的效能

本文是瞭解您的混合現實應用程式效能重要性的簡介。  如果您的應用程式不是以最佳的畫面播放速率執行，則使用者體驗可能會大幅降低。 全像是不穩定的，且環境的標頭追蹤將不穩定，而導致使用者體驗不佳。 您必須將效能視為混合現實開發的第一個類別功能，而不是波蘭文工作。

以下列出每個目標平臺的效能幀效能值。

| 平台 | 目標畫面播放速率 |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60 FPS |
| [Windows Mixed Reality Ultra 電腦](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality 電腦](../../discover/immersive-headset-hardware-details.md) | 60 FPS |

下列架構概述達到目標畫面播放速率的最佳作法。 建議您閱讀 [unity 文章的效能建議](../unity/performance-recommendations-for-unity.md) ，以取得在 unity 環境中測量及改善畫面播放速率的秘訣。

## <a name="understanding-performance-bottlenecks"></a>瞭解效能瓶頸

如果您的應用程式有表現不佳的畫面播放速率，則第一個步驟是分析並瞭解應用程式的計算密集型位置。 有兩個主要的處理器負責轉譯您場景的工作： CPU 和 GPU，每個都處理混合現實應用程式的不同層面。 可能發生瓶頸的三個主要位置如下： 

1. **應用程式執行緒-CPU** -
    負責您的應用程式邏輯，包括處理輸入、動畫、物理和其他應用程式邏輯。
2. **將執行緒 CPU 轉譯為 gpu** ，負責將您的繪製呼叫提交至 gpu。 當您的應用程式想要轉譯物件（例如 cube 或模型）時，此執行緒會將要求傳送至 GPU 以進行作業。
3. **GPU** -最常用來處理應用程式的圖形管線，以將3d 資料 (模型、材質等) 轉換成圖元。 它最終會產生要提交到您裝置畫面的2D 影像。

![框架的存留期](images/lifetime-of-a-frame.png)

通常，HoloLens 應用程式將會有 GPU 界限，但不一定會。 您可以使用下列工具和技術，來瞭解您的特定應用程式瓶頸的位置。

## <a name="how-to-analyze-your-application"></a>如何分析您的應用程式

有許多工具可讓您瞭解混合現實應用程式中的效能設定檔和潛在的瓶頸。 

以下是一些常見的工具，可協助您收集應用程式的深入分析資訊：
- [Intel 圖形效能分析器](https://software.intel.com/gpa)
- [Visual Studio 圖形偵錯工具](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 框架偵錯工具](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Unreal 見解](../unreal/unreal-insights.md)
- [Pix](https://devblogs.microsoft.com/pix/)
- [Unreal 中的 GPU Pofiling](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>如何在任何環境中進行分析

判斷您的應用程式是否為 GPU 或受 CPU 限制的其中一種方式，是降低轉譯目標輸出的解析度。 藉由減少要計算的圖元數，您將會降低 GPU 負載。 裝置會轉譯成較小的材質，然後轉譯為顯示您最終影像的向上取樣。

減少轉譯解析度之後，如果：
1) 應用程式的畫面播放速率增加時，您可能 **會** 受到 **GPU 的限制**
1) 應用程式 **的幀** 速率沒有變更，因此您可能會受 **限於 CPU**

>[!NOTE]
>Unity 能讓您在執行時間透過 *[XRSettings renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性，輕鬆修改應用程式的轉譯目標解析度。 裝置上顯示的最終映射具有固定的解析度。 平臺會取樣較低解析度的輸出，以建立較高的解析度影像，以便在顯示時呈現。 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>如何改進您的應用程式

### <a name="cpu-performance-recommendations"></a>CPU 效能建議

一般來說，在 CPU 上的混合現實應用程式中，大部分的工作都牽涉到執行場景的「模擬」，並處理您的應用程式邏輯。 以下是優化的目的地區域：

- 動畫
- 物理特性
- 記憶體配置
- 複雜的演算法 (即 反向運動，路徑-尋找) 

### <a name="gpu-performance-recommendations"></a>GPU 效能建議

#### <a name="understanding-bandwidth-vs-fill-rate"></a>瞭解頻寬與填滿率
在 GPU 上轉譯框架時，應用程式會受到記憶體頻寬或填滿率的限制。

- **記憶體頻寬** 是 GPU 可從記憶體進行的讀取和寫入速率
    - 若要找出頻寬限制，請減少材質品質，並檢查畫面播放速率是否已改善。
    - 在 Unity 中，變更 [**編輯**   >  **專案設定**  >  **[品質] 設定](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 中的材質品質。
- **填滿率** 是指 GPU 每秒可繪製的圖元。
    - 若要識別填滿速率限制，請降低顯示器解析度，並檢查是否已改善幀。 
    - 在 Unity 中，使用  *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性

記憶體頻寬通常牽涉到下列其中一項的優化：
1) 較低材質解析度
2) 使用較少的材質 (法線、反射等等) 

填滿率著重于減少需要針對最終轉譯圖元計算的作業數目，包括：
1) 要呈現/處理的物件數目
2) 每個著色器的作業數目
3) 最終結果的 GPU 階段數 (幾何著色器、後置處理效果等等) 
4) 轉譯 (顯示解析度) 的圖元數

#### <a name="reduce-polygon-count"></a>減少多邊形計數

較高的多邊形計數會導致 GPU 的更多作業，因此減少場景中的 [多邊形數目](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) 可減少轉譯時間。 還有其他因素會讓幾何的陰影變得相當昂貴，但是多邊形計數是最簡單的度量，可判斷呈現場景所需的工作量。

#### <a name="limit-overdraw"></a>限制過度繪製

當轉譯多個物件但未在螢幕上顯示時，如果遮蔽物件隱藏了多個物件，就會發生高過度繪製。 想像一下一下有物件背後的牆。 所有幾何都會處理以進行轉譯，但只需要轉譯不透明的牆，這會導致不必要的作業。

#### <a name="shaders"></a>著色器

著色器是在 GPU 上執行的小型程式，且會在轉譯時執行兩個重要的步驟：
1) 判斷應繪製哪些頂點，以及它們在螢幕空間 (頂點著色器的位置) 
    - 每個網格的頂點著色器都會針對每個頂點執行。
2) 判斷圖元著色器 (每個圖元的色彩) 
    - 圖元著色器是依圖元執行，並由幾何轉譯為目標呈現材質。

一般而言，著色器會進行許多轉換和光源計算。 雖然複雜的光源模型、陰影和其他作業可以產生絕佳的結果，但它們也有價格。 減少著色器中計算的作業數目，可以大幅減少每個畫面的 GPU 所需的工作量。

##### <a name="shader-coding-recommendations"></a>著色器編碼建議

- 盡可能使用雙線性篩選
- 重新排列運算式以使用 MAD 內建函式，同時執行乘法和 add
- 在 CPU 上盡可能 Precalculate 並以常數形式傳遞至材質
- **偏好將作業從圖元著色器移至頂點著色器**
    - 一般來說，頂點的數目小於圖元數 (720p 是921600圖元、1080p 是2073600圖元，依此類推) 

#### <a name="remove-gpu-stages"></a>移除 GPU 階段

後續處理的效果可能很昂貴，而且會提高應用程式的填滿率，包括如 MSAA 的消除鋸齒技術。 在 HoloLens 上，建議您避免使用這些技術和其他著色器階段，例如幾何、輪廓和計算著色器。

## <a name="memory-recommendations"></a>記憶體建議

過度的記憶體配置和解除配置作業可能會導致效能不一致、凍結的框架和其他不利行為。 在 Unity 中進行開發時，請務必瞭解記憶體考慮，因為記憶體管理是由垃圾收集行程所控制。

#### <a name="object-pooling"></a>物件集區

物件共用是一種常用的技巧，可降低持續配置和物件取消配置的成本。 這是藉由配置相同物件的大型集區，並重複使用此集區中非使用中的可用實例來完成，而不是在一段時間內不斷產生和終結物件。 物件集區非常適合在應用程式期間有變數存留期的重複使用元件。

## <a name="see-also"></a>另請參閱
- [對 Unity 的效能建議](../unity/performance-recommendations-for-unity.md)
- [Unity 的建議設定](../unity/recommended-settings-for-unity.md)
- [對 Unreal 的效能建議](../unreal/performance-recommendations-for-unreal.md)
- [Unreal 中的材質建議](../unreal/unreal-materials.md)
- [優化3D 模型](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [轉換和優化即時3D 模型的最佳作法](/dynamics365/mixed-reality/import-tool/best-practices)
- [適用于 Unreal 的演出者和設計工具效能指導方針](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Unreal 的 VR 最佳作法](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)