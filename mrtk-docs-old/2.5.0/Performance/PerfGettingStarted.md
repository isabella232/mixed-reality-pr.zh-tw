---
title: PefGettingStarted
description: 在 MRTK 中瞭解及調整效能的檔。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: cfadc1ef998e31435d33bdebe4f7e57473837d3c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780790"
---
# <a name="performance"></a>效能

## <a name="getting-started"></a>開始使用

將效能合理化的最簡單方式是透過畫面播放速率，或應用程式每秒可轉譯影像的次數。 請務必符合目標的畫面播放速率，如目標平臺所述 (例如： [Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality)、 [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)等) 。 例如，在 HoloLens 上，目標畫面播放速率是 60 FPS。 低幀率的應用程式可能會導致日益惡化使用者體驗， [例如惡化全](hologram-Stabilization.md)像、世界追蹤、手追蹤等。 為了協助開發人員追蹤和達成品質的畫面播放速率，Mixed Reality 工具組提供各種不同的工具和腳本。

### <a name="visual-profiler"></a>Visual profiler

若要在開發的存留期間持續追蹤效能，強烈建議您在執行 & 的應用程式偵錯工具時，一律顯示畫面播放速率的視覺效果。 Mixed Reality 工具組提供的 [Visual Profiler](../features/Diagnostics/UsingVisualProfiler.md) 診斷工具，可提供應用程式視圖中目前 FPS 和記憶體使用量的即時資訊。 您可以透過 [ [MRTK 設定檔](../out-of-scope/MixedRealityConfigurationGuide.md)] 偵測器底下的 [[診斷系統] 設定](../features/Diagnostics/DiagnosticsSystemGettingStarted.md)來設定 Visual Profiler。

此外，在裝置上執行時，最好使用 Visual Profiler 來追蹤畫面播放速率，而不是在 Unity 編輯器或模擬器中執行。 在具有 [發行設定組建](https://docs.microsoft.com/visualstudio/debugger/how-to-set-debug-and-release-configurations?view=vs-2019)的裝置上執行時，會描述最精確的效能結果。

> [!NOTE]
> 如果是建立 Windows Mixed Reality，請使用[主要設定組建](https://docs.microsoft.com/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)進行部署

![Visual Profiler 介面](../features/Images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>優化視窗

[ [MRTK 優化] 視窗](../features/Tools/OptimizeWindow.md) 提供資訊和自動化工具，協助混合現實開發人員設定其環境以獲得效能最佳的結果，並找出場景 & 資產的潛在瓶頸。 Unity 中的某些重要設定可協助提供大幅優化的混合現實專案結果。

一般而言，這些設定牽涉到呈現適用于混合現實的設定。 相較于傳統的3D 圖形開發，混合現實應用程式是唯一的，因為有兩個畫面 (例如 針對整個場景呈現兩個眼睛) 。

您可以利用 [MRTK 優化] 視窗，在 Unity 專案中自動設定以下所述的建議設定。

![MRTK 優化視窗設定](../features/Images/Performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Unity Profiler

[Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html)是一個實用的工具，可在每個畫面格層級調查應用程式效能的詳細資料。

#### <a name="time-spent-on-the-cpu"></a>CPU 花費的時間

![範例 Unity Profiler 圖形](../features/Images/Performance/UnityProfilerGraph.png)

若要維持理想的畫面播放速率 (通常是每秒60個畫面格) ，應用程式必須達到16.6 毫秒的 CPU 時間最大畫面格時間。 為了協助識別 MRTK 功能的成本，Microsoft Mixed Reality 工具組包含每個畫面格 () 程式碼路徑的內部迴圈標記。 這些標記會使用下列格式，以協助您瞭解所使用的特定功能：

```
[MRTK] className.methodName
```

> [!Note]
> 在方法名稱之後可能會有其他資料。 這是用來識別有條件地執行，可能會因為應用程式程式碼的小型變更而避免的昂貴功能。

![範例 Unity Profiler 階層](../features/Images/Performance/UnityProfilerHierarchy.png)

在此範例中，階層已展開，以顯示 WindowsMixedRealityArticulatedHand 類別的 UpdateHandData 方法在分析框架期間耗用0.44 毫秒的 CPU 時間。 這項資料可以用來協助判斷效能問題是否與應用程式程式碼或系統中的其他位置有關。

強烈建議開發人員以類似的方式檢測應用程式程式碼。 應用程式程式碼檢測的主要焦點區域是在事件處理常式中，因為引發事件時，這些方法會向 MRTK 更新迴圈收取。 MRTK 更新迴圈內的高框架時間可能是指事件處理常式方法中的昂貴程式碼。

## <a name="recommended-settings-for-unity"></a>Unity 的建議設定

### <a name="single-pass-instanced-rendering"></a>Single-Pass 實例轉譯

Unity 中 XR 的預設轉譯設定是 [多重傳遞](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html)。 這項設定會指示 Unity 執行整個轉譯管線兩次，每次都有一次。 您可以改為選取 [ [單一傳遞實例](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 轉譯] 來將其優化。 這項設定會利用轉譯 [目標陣列](https://en.wikipedia.org/wiki/Multiple_Render_Targets) 來執行單一繪製呼叫，將實例放入適當的 [呈現目標](https://en.wikipedia.org/wiki/Render_Target) 中。 此外，這個模式允許在轉譯管線的單一執行中完成所有轉譯。 因此，選取單一傳遞實例轉譯作為混合現實應用程式的轉譯路徑，可以 [在 CPU & GPU 上節省大量時間](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) ，而且這是建議的轉譯設定。

不過，若要對每個網格發出單一繪製呼叫每個網格，所有著色器都必須支援 [GPU 實例](https://docs.unity3d.com/Manual/GPUInstancing.html) 。 實例可讓 GPU 跨兩個眼睛繪製呼叫。 Unity 內建著色器和 [MRTK 標準著色器](../features/README_MRTKStandardShader.md) 依預設會在著色器程式碼中包含必要的實例指示。 如果是針對 Unity 撰寫自訂著色器，可能需要更新這些著色器，以支援單一傳遞實例轉譯。

#### <a name="example-code-for-custom-shader"></a>[自訂著色器的範例程式碼](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a>品質設定

Unity 提供預設值 [來控制](https://docs.unity3d.com/Manual/class-QualitySettings.html) 每個平臺端點的轉譯品質。 這些預設值可控制哪些圖形功能可以啟用，例如陰影、消除鋸齒、全球照明等等。 建議您降低這些設定，並優化轉譯期間所執行的計算數目。

*步驟1：* 更新混合現實 Unity 專案以使用 *低品質* 層級設定  
**編輯**  > **專案設定**，然後選取 [**品質**] 類別 > 選取 UWP 平臺的 *低品質*

*步驟2：* 針對每個 Unity 場景檔案，停用 [即時全域照明](https://docs.unity3d.com/Manual/LightMode-Realtime.html)  
**視窗**  > 轉譯  > **光源設定**  > [取消核取 *即時全域照明*](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a> (HoloLens) 的深度緩衝區共用

如果是針對 Windows Mixed Reality 平臺進行開發，而在特別的 HoloLens 中，啟用 [ *XR 設定*] 下的 *深度緩衝區共用* 有助於進行全像 [影像穩定](../Performance/Hologram-Stabilization.md)。 不過，處理深度緩衝區可能會產生效能成本，特別是在使用 [24 位深度格式](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html)時。 因此， *強烈建議您* 將深度緩衝區設定為16位精確度。

如果因為較低的位格式而發生 [z](https://en.wikipedia.org/wiki/Z-fighting) 操作，請確認所有相機的最大 [剪輯平面](https://docs.unity3d.com/Manual/class-Camera.html) 都設為應用程式的最小可能值。 Unity 預設會設定變更為1000m 的裁剪平面。 在 HoloLens 上，50m 的剪輯平面通常比大部分的應用程式案例還多。

> [!NOTE]
> 如果使用 *16 位深度格式*，則樣板緩衝區所需的效果將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。 相反地，選取 *24 位深度格式* 通常會建立8位的樣板緩衝區（如果適用于端點圖形平台）。
>
> 如果使用需要樣板緩衝區的 [遮罩元件](https://docs.unity3d.com/Manual/script-Mask.html) ，請考慮改用 [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) ，這不需要樣板緩衝區，因此可與 *16 位深度格式* 搭配使用。

> [!NOTE]
> 若要快速判斷場景中的哪些物件不會以視覺化方式寫入深度緩衝區，可以使用 MRTK 設定檔中 *編輯器設定* 下的轉譯 [*深度緩衝區* 公用程式](../out-of-scope/MixedRealityConfigurationGuide.md#editor-utilities)。

### <a name="optimize-mesh-data"></a>優化網格資料

[優化網格資料](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html)設定會嘗試在您的應用程式中移除未使用的頂點屬性。 這項設定會藉由在組建中每個網格上每個資料的每個著色器上執行，來執行這項設定。 這適用于遊戲資料大小和執行時間效能，但可能會大幅阻礙組建時間。

建議您在開發期間停用此設定，並在建立「主要」組建期間重新啟用。 您可以在 [**編輯**  >  **專案設定**  >  **播放機**  >  **其他設定**  >  **優化網格資料**] 下找到此設定。

## <a name="general-recommendations"></a>一般建議

對於混合的現實開發人員來說，效能可能是不明確且不斷變化的挑戰，以及將效能合理化的知識範圍很廣。 但有一些一般建議可瞭解如何處理應用程式的效能。

將應用程式的執行簡化為 *CPU* 或 *GPU* 上執行的片段，並據以識別應用程式是否由任一元件所限制，是很有用的。  可能會有瓶頸跨越處理單位以及必須仔細調查的一些獨特案例。 不過，若要開始使用，最好先瞭解應用程式的執行時間。

### <a name="gpu-bounded"></a>GPU 界限

由於混合現實應用程式大部分的平臺都是利用 [stereoscopic](https://en.wikipedia.org/wiki/Stereoscopy)轉譯，因此因為轉譯「全半寬」畫面的本質，所以通常是 GPU 限定的。 Futhermore，行動混合現實平臺（例如 HoloLens 或 Oculus）會受到行動類別 CPU & GPU 處理能力的限制。

將焦點放在 GPU 上時，通常會有兩個重要的階段，應用程式必須完成每個畫面格。

1. 執行 [頂點著色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)
2. 執行 [圖元著色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (也稱為片段著色器) 

如果沒有深入探討電腦圖形 & 轉譯 [管線](https://en.wikipedia.org/wiki/Graphics_pipeline)的複雜欄位，每個著色器階段都是在 GPU 上執行的程式，以產生下列專案。

1. 頂點著色器會將網格頂點轉換成螢幕空間中的座標 (例如 每個頂點執行的程式碼) 
2. 圖元著色器會計算針對指定圖元和網格片段繪製的色彩 (例如 每圖元執行的程式碼) 

就效能微調而言，將焦點放在優化圖元著色器中的作業時，通常會更豐富。 應用程式可能只需要繪製一個 cube，它只會是8個頂點。 不過，cube 所佔用的螢幕空間可能是以上百萬圖元為單位。 因此，如果在圖元著色器上減少了10個作業，減少著色器程式碼的速度會比頂點著色器更多。

這是利用 [MRTK 標準著色器](../features/README_MRTKStandardShader.md) 的主要原因之一，因為此著色器通常會在每個圖元 & 頂點執行比 Unity 標準著色器更少的指令，同時達到可比較的美觀結果。

|    CPU 優化      |             GPU 優化              |
|---------------------------|--------------------------------------------|
| 應用程式模擬邏輯      | 轉譯作業 |
| 簡化物理          | 減少照明計算 |
| 簡化動畫       | 減少繪製物件 & 數目的多邊形計數 |
| 管理垃圾收集 | 減少透明物件的數目 |
| 快取參考          | 避免後續處理/全螢幕效果  |

### <a name="draw-call-instancing"></a>繪製呼叫實例

Unity 中可降低效能的最常見錯誤之一，就是在執行時間複製材質。 如果 Gameobject 共用相同的材質和/或相同的網格，則可以透過 *[靜態批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)*、 *[動態批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)* 和 *[GPU 實例](https://docs.unity3d.com/Manual/GPUInstancing.html)* 等技術，將它們優化成單一繪圖呼叫。 但是，如果開發人員在執行時間修改轉譯器 [材質](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 的屬性，Unity 將會建立所指派之材質的複製複本。

例如，如果場景中有 100 cube，開發人員可能會想要在執行時間為每個 cube 指派唯一的色彩。 轉譯器的存取權。 c # 中的 [*color*](https://docs.unity3d.com/ScriptReference/Material-color.html) 將會讓 Unity 在記憶體中為這個特定的轉譯器/GameObject 建立新的材質。 每個 100 cube 都有自己的資料，因此不能將它們合併成一個繪製呼叫，而是會成為100繪製從 CPU 到 GPU 的呼叫要求。

為了克服這種障礙，並且仍為每個 cube 指派獨特的色彩，開發人員應該利用 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)。

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a>Unity 效能工具

Unity 提供編輯器內建的絕佳效能工具。

- [Unity Profiler](https://docs.unity3d.com/Manual//Profiler.html)
- [Unity 框架偵錯工具](https://docs.unity3d.com/Manual/FrameDebugger.html)

如果評估一個著色器與另一個著色器之間的粗略效能取捨，則編譯每個著色器並查看每個著色器階段的作業數目會很有用。 這可以藉由選取 [著色器資產](https://docs.unity3d.com/Manual/class-Shader.html) ，然後按一下 [ *編譯] 和 [顯示程式碼* ] 按鈕來完成。 這會編譯所有著色器變異，並以結果開啟 visual studio。 注意：所產生的統計資料結果可能會根據在使用指定著色器的材質上啟用了哪些功能而有所不同。 Unity 只會編譯目前專案中直接使用的著色器變數。

Unity 標準著色器統計資料範例

![Unity 標準著色器統計資料](../features/Images/Performance/UnityStandardShader-Stats.PNG)

MRTK 標準著色器統計資料範例

![MRTK 標準著色器統計資料](../features/Images/Performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>另請參閱

### <a name="unity"></a>Unity

- [適用于初學者的 Unity 效能優化](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Unity 效能優化教學課程](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Unity 優化最佳做法](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [優化圖形效能](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [行動優化實用指南](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [適用于 Unity 的建議設定](https://docs.microsoft.com/windows/mixed-reality/recommended-settings-for-unity)
- [瞭解混合現實的效能](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [對 Unity 的效能建議](https://docs.microsoft.com/windows/mixed-reality/performance-recommendations-for-unity)
- [適用于 Windows Unity 的事件追蹤指南](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [效能方針](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [效能工具](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>網格優化

- [優化3D 模型](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [轉換和優化即時3D 模型的最佳作法](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)
