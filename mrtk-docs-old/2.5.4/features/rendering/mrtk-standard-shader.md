---
title: MRTKStandardShader
description: MRTKStandardShader 檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、材質著色器
ms.openlocfilehash: fcbc61d35a8447187f75e204ac7fb90bbcc89d31
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781482"
---
# <a name="mrtk-standard-shader"></a>MRTK 標準著色器

![標準著色器範例](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

MRTK 標準陰影系統利用單一、彈性的著色器，其可達成與 Unity 標準著色器類似的視覺效果、實行 [流暢的設計系統](https://www.microsoft.com/design/fluent/) 準則，並在混合現實裝置上維持效能。

## <a name="example-scenes"></a>範例場景

您可以在下的 **MaterialGallery** 場景中找到著色器材質範例 `MRTK/Examples/Demos/StandardShader/Scenes/` 。 此場景中的所有資料都是使用 MRTK/Standard 著色器。

![材質資源庫](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

您可以在底下的 **StandardMaterialComparison** 場景中，找到比較場景，以針對 Unity/標準著色器範例來比較和測試 MRTK/標準著色器 `MRTK/Examples/Demos/StandardShader/Scenes/` 。

![材質比較](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>架構

MRTK/標準陰影系統是「uber 著色器」，其使用 [Unity 的著色器程式變異數功能](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) ，根據材質屬性自動產生最佳的著色器程式碼。 當使用者選取材質偵測器中的材質屬性時，它們只會對已啟用的功能產生效能成本。

## <a name="material-inspector"></a>材質檢查

MRTK/標準著色器的自訂材質偵測器已被呼叫 [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) 。 偵測器會根據使用者選取和設定轉譯狀態的有助於，自動啟用/停用著色器功能。 如需每項功能的詳細資訊， **請將滑鼠停留在 Unity 編輯器中的每個屬性上，以取得工具提示。**

![材質檢查](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

偵測器的第一個部分會控制材質的呈現狀態。 轉譯 *模式* 會決定呈現材質的時間和方式。 MRTK/標準著色器的目的是要鏡像 [Unity/standard 著色器中所找到](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)的轉譯模式。 MRTK/Standard 著色器也包含完整使用者控制項的 *加法* 轉譯模式和 *自訂* 呈現模式。

| 轉譯模式 |         描述                                                                                                                                                                                                                                                                                                                                                           |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Opaque         |  (預設) 適用于沒有透明區域的一般純色物件。                                                                                                                                                                                                                                                                                             |
| 剪影         | 允許建立透明效果，其在不透明和透明區域之間具有固定邊緣。 在此模式中，沒有半透明的區域，材質可能是100% 不透明或不可見。 使用透明度建立材質（例如植被指數）的形狀時，這非常有用。                                                              |
| 淡化           | 允許透明度值完全淡化物件，包括任何高光或可能具有的反射。 如果您想要建立物件的動畫，讓物件淡入或淡出，這個模式就很有用。它不適合用來呈現逼真的透明材質，例如清晰的塑膠或玻璃，因為反射和醒目顯示也會淡出。 |
| 透明    | 適用于呈現逼真的透明材質，例如清晰的塑膠或玻璃。 在此模式中，材質本身會根據材質的 Alpha 色板和色調色彩) 的 Alpha，來取得透明度值 (。 不過，反射和光源醒目顯示會以完全清楚的方式保持可見，就像是實際的透明材質一樣。 |
| 加法       | 啟用加法混合模式，以目前的圖元色彩加總先前的圖元色彩。 這是慣用的透明度模式，可避免出現透明度排序問題。                                                                                                                                                                                  |
| Custom         | 允許以手動方式控制轉譯模式的每個層面。 僅適用于先進的使用量。                                                                                                                                                                                                                                                                  |                                                                                                                                            |

![轉譯模式](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| 挑選模式 |             描述                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 關閉       | 停用臉部剔除。 只有在需要雙側邊網格時，才應該將剔除設定為 Off。                                                                                        |
| Front     | 啟用 front 臉部剔除。                                                                                                                                                        |
| 上一步      |  (預設值) 可讓您 [回頭挑選臉部](https://en.wikipedia.org/wiki/Back-face_culling)。 應該盡可能地啟用背景臉部剔除，以改善轉譯效能。 |

## <a name="performance"></a>效能

透過 Unity 標準著色器使用 MRTK 標準著色器的主要優點之一，就是效能。 MRTK 標準著色器是可擴充的，只能使用啟用的功能。 不過，MRTK 標準著色器也已撰寫成以 Unity 標準著色器的形式提供可比較的美觀結果，但成本更低。 比較著色器效能的一個簡單方式，就是透過在 GPU 上需要執行的作業數目。 當然，計算的大小可能會因為啟用的功能和其他轉譯設定而變動。 但一般而言，MRTK 標準著色器所執行的計算明顯比 Unity 標準著色器更少。

Unity 標準著色器統計資料範例

![Unity 標準著色器統計資料](../images/performance/UnityStandardShader-Stats.PNG)

MRTK 標準著色器統計資料範例

![MRTK 標準著色器統計資料](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> 您可以在 Unity 檢查程式中選取和查看 [著色器資產](https://docs.unity3d.com/Manual/class-Shader.html) ，然後按一下 [ *編譯和顯示程式碼* ] 按鈕，以產生這些結果。

## <a name="lighting"></a>光源

MRTK/Standard 會針對光源使用簡單的近似值。 因為此著色器不會計算實體正確性和節能，所以會快速且有效率地呈現。 Blinn-Phong 是主要光源技術，其混合使用 Fresnel 和以影像為基礎的光源來近似以實體為基礎的光源。 著色器支援下列光源技術：

### <a name="directional-light"></a>定向光線

著色器會遵循場景中第一個 Unity 方向光線的方向、色彩和強度 (如果已啟用) 。 動態點燈、點燈或任何其他 Unity 燈光都不會被視為即時光源。

### <a name="spherical-harmonics"></a>球形諧波

著色器會使用淺探查，在場景中使用 [球面諧波](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html)來接近燈光（若已啟用）。 會針對每個頂點執行球形諧波計算，以降低計算成本。

### <a name="lightmapping"></a>Lightmapping

針對靜態光源，著色器會遵循 Unity 的 [Lightmapping 系統](https://docs.unity3d.com/Manual/Lightmapping.html)所建立的 lightmaps。 只要將轉譯器標示為靜態 (或 lightmap 靜態) ，即可使用 lightmaps。

### <a name="hover-light"></a>停留燈

* 查看 [停留燈](hover-light.md)

### <a name="proximity-light"></a>近亮光

* 請參閱 [近亮燈](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>輕量可編寫腳本的轉譯管線支援

MRTK 包含的升級路徑，可讓開發人員利用 Unity 的輕量可編寫腳本轉譯管線 (LWRP) 搭配 MRTK 著色器。 在 Unity m153.azuredevops2019.1.1 f1 和輕量 RP 5.7.2 封裝中進行測試。 或者，如需開始使用 LWRP 的指示，請參閱 [此頁面](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)。

若要執行 MRTK 升級，請針對 **輕量轉譯管線選取：混合現實工具組-> 公用程式-> UPGRADE MRTK Standard 著色器**

![lwrp 升級](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

升級之後，MRTK/Standard 著色器將會改變，而任何洋紅色 (著色器錯誤) 材質應固定。 若要確認升級是否成功，請檢查主控台的：已 **升級的資產/MixedRealityToolkit/StandardAssets/著色器/MixedRealityStandard，以搭配輕量轉譯管線使用**。

## <a name="ugui-support"></a>UGUI 支援

MRTK 標準陰影系統可與 Unity 的內建 [UI 系統](https://docs.unity3d.com/Manual/UISystem.html)搭配使用。 在 Unity UI 元件上，unity_ObjectToWorld 矩陣不是圖形元件所在之本機轉換的轉換矩陣，而是其父畫布的轉換矩陣。 許多 MRTK/標準著色器效果都需要知道物件規模。 若要解決此問題， [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) 會在 UI 網格結構期間，將調整資訊儲存為 UV 通道屬性。

請注意，使用 Unity 映射元件時，建議您為來源影像指定「無 (Sprite) 」，以防止 Unity UI 產生額外的頂點。

當需要時，MRTK 中的畫布會提示您新增 a [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) ：

![調整網格效果](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>材質結合器

若要改善每個圖元金屬的 Unity 標準著色器的同位，可透過 [通道封裝](http://wiki.polycount.com/wiki/ChannelPacking)來控制平滑度、放射和遮蔽值。 例如：

![通道對應範例](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

當您使用通道封裝時，您只需要將一個材質取樣並載入到記憶體中，而不是四個不同的材質。 當您在諸如材質或 Photoshop 的程式中撰寫材質地圖時，您可以將它們封裝如下：

| 管道 | 屬性             |
|---------|----------------------|
| 紅色     | 金屬             |
| 綠色   | 遮蔽            |
| 藍色    | 發出 (灰階)  |
| Alpha   | 平滑           |

或者，您可以使用 MRTK 材質結合器工具。 若要開啟工具，請選取： **混合現實工具組-> 公用程式-> 材質結合器** ，這會開啟下列視窗：

![紋理結合器範例](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

您可以選取 Unity 標準著色器，然後按一下 [從標準材質自動填入]，自動填寫此視窗。 或者，您可以手動指定每個紅色、綠色、藍色或 Alpha 色板的材質 (或常數值) 。 材質組合是 GPU 加速的，不需要輸入材質就可以存取 CPU。

## <a name="additional-feature-documentation"></a>其他功能檔

以下是 MRTK/Standard 著色器提供的幾項功能詳細資料的額外詳細資料。

### <a name="primitive-clipping"></a>基本剪輯

![基本剪輯](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* 請參閱 [裁剪基本](clipping-primitive.md)

### <a name="mesh-outlines"></a>網狀大綱

許多網狀大綱技巧都是使用 [後置處理](https://docs.unity3d.com/Manual/PostProcessingOverview.html) 技術來完成。 後續處理可提供絕佳的品質大綱，但在許多混合現實裝置上可能會耗費大量資源。 您可以在底下的  **OutlineExamples** 場景中找到示範網格輪廓使用方式的場景 `MRTK/Examples/Demos/StandardShader/Scenes/` 。

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) 和 [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) 可以用來呈現網格轉譯器周圍的輪廓。 啟用此元件會為所述的物件引進額外的轉譯行程，但其設計目的是在行動混合現實裝置上執行 gen2，而不會使用任何後置流程。 這項效果的限制包括無法在不防水 (或必須是雙側) 的物件上運作，而且可能會在重迭的物件上發生深度排序問題。

大綱行為是設計用來搭配 MRTK/標準著色器。 外框材質通常是穩固的 unlit 色彩，但可以設定來達成各式各樣的效果。 外框材質的預設設定如下：

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. 深度寫入-應針對外框材質停用，以確保外框不會防止其他物件轉譯。
2. 頂點延伸-必須啟用才能轉譯大綱。
3. 使用平滑法線-針對某些網格，此設定是選擇性的。 藉由將頂點沿著頂點垂直移動來進行，而在某些網格上沿著預設法線的方向，則會導致大綱中的不連續。 若要修正這些不連續，您可以核取此方塊，以使用另一組會產生的平滑法線 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 是可用來在網格上自動產生平滑法線的元件。 這個方法會將網格中的頂點分組，並在空間中共用相同的位置，然後將這些頂點的法線平均。 此程式會建立基礎網格的複本，而且只在必要時才使用。

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. 經由產生的平滑法線 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 。
2. 預設使用的法線，請注意立方體周圍的構件。

### <a name="stencil-testing"></a>樣板測試

內建的可設定範本測試支援，可達成各式各樣的效果。 例如入口網站：

![樣板測試](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>實例色彩支援

實例色彩支援，以提供數千個 GPU 實例網格獨特的材質屬性：

![實例屬性](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Triplanar 對應

Triplanar 對應是以程式設計方式為網格材質紋理的技巧。 常用於地形、未 UVs 的網格，或難以解除包裝圖形。 這項實行支援世界或區域的空間投射、混合平滑的規格，以及正常的地圖支援。 請注意，使用的每個材質都需要3個紋理範例，因此請在效能嚴重不足的情況下謹慎使用。

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>頂點延伸

世界空間中的頂點延伸。 適用于視覺化拉伸的周框磁片區或轉換 in/out 網格。

![一般地圖示尺1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>其他

控制 >albedo 優化的核取方塊。 當未指定任何 >albedo 材質時，會停用優化 >albedo 作業。 這對控制 [遠端材質載入](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)很有用。

只要勾選此方塊：

![>albedo 指派](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

支援每圖元裁剪材質、區域邊緣型消除鋸齒和一般地圖縮放比例。

![一般地圖縮放比例2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>另請參閱

* [互動](../ux-building-blocks/interactable.md)
* [停留燈](hover-light.md)
* [近亮光](proximity-light.md)
* [裁剪基本](clipping-primitive.md)
