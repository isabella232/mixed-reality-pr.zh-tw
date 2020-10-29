---
title: 應用程式品質準則
description: 本檔說明影響混合現實應用程式品質的主要因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式品質準則，混合現實，混合現實應用程式
ms.openlocfilehash: 96d446e1f6f5649f842d674ea4692d619894cc32
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679320"
---
# <a name="app-quality-criteria"></a>應用程式品質準則

本檔說明影響混合現實應用程式品質的主要因素。 針對每個因素，會提供下列資訊
* 總覽-品質因素的簡短描述，以及其重要性。
* 裝置影響-受影響的視窗混合現實裝置類型。
* 品質準則–如何評估品質因素。
* 如何測量–測量問題 (或) 經驗的方法。
* 建議-提供更佳使用者體驗的方法摘要。
* 資源-相關的開發人員和設計資源，可用於建立更好的應用程式體驗。

## <a name="frame-rate"></a>畫面播放速率

畫面播放速率是全像全像要件的第一次，也是使用者的舒適。 低於建議目標的畫面播放速率可能會導致全息圖顯得抖動、對體驗的 believability 造成負面影響，並可能造成眼睛疲勞。 您在 Windows Mixed Reality 沉浸式耳機上體驗的目標畫面播放速率將會是60Hz 或90Hz，視您想要支援的 Windows Mixed Reality 相容電腦而定。 HoloLens 的目標畫面播放速率為60Hz。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
| 應用程式一致地符合每秒的畫面格 (FPS) 目標裝置的目標： HoloLens 上的 60fps;在 Ultra 電腦上 90fps;以及60fps 在主流電腦上。 | 應用程式有間歇性的框架下降不會阻礙核心體驗;或 FPS 一致地低於所需的目標，但不會妨礙應用程式體驗。 | 應用程式平均每10秒或更短的畫面播放速率都有下降。 |

### <a name="how-to-measure"></a>如何測量

* 「系統效能」下的 [Windows 裝置入口網站](using-the-windows-device-portal.md#system-performance) 會提供即時的畫面播放速率圖形。
* 針對開發的偵錯工具，請在應用程式中新增畫面播放速率診斷計數器。 請參閱範例計數器的資源。
* 當應用程式正在執行時，可能會在裝置上經歷畫面播放速率下降，方法是將您的標題從側邊移動 如果全息圖顯示非預期的抖動移動，則低畫面播放速率或穩定性平面可能是原因。

### <a name="recommendations"></a>建議

* 在開發工作的開頭新增畫面播放速率計數器。
* 產生下降畫面播放速率的變更應該進行評估，並適當地解析為效能錯誤。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)
* [全像穩定性和幀的影像](hologram-stability.md#frame-rate)
* [資產效能預算](../../design/asset-creation-process.md)
* [對 Unity 的效能建議](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MRToolkit，FPS 計數器顯示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit，著色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>外部參考

* [Unity，將行動應用程式優化](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>全像投影穩定性

穩定的全像影像會提高應用程式的可用性和 believability，並為使用者建立更舒適的觀賞體驗。 全像應用程式開發的結果，以及裝置瞭解 (追蹤) 其環境的能力。 雖然畫面播放速率是穩定性的第一要件，但其他因素可能會影響穩定性，包括：

* 使用穩定平面
* 距離空間錨點
* 追蹤

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
|  全像投影一樣穩定。 | 次要內容展示非預期的移動;或非預期的移動不會妨礙整體應用程式體驗。 | 框架中的主要內容表現了非預期的移動。 |

### <a name="how-to-measure"></a>如何測量

在佩戴裝置和觀賞體驗時：

* 將您的標題從側邊移至側面，如果全像是顯示非預期的移動，那麼低畫面播放速率或穩定性平面與焦點平面之間的對齊可能是可能的原因。
* 四處移動全像影像和環境，尋找像是泳道和 jumpiness 的行為。 這種類型的動作可能是因為裝置無法追蹤環境或空間錨點的距離所造成。
* 如果框架中有大型或多個全息圖，請觀察各種深度的全像全像投影行為，並將您的頭部位置從側邊移至側面，如果出現 shakiness，可能是穩定平面所造成。

### <a name="recommendations"></a>建議

* 在開發工作的開頭新增畫面播放速率計數器。
* 使用穩定平面。
* 一律在其錨點的3計量中轉譯錨定的全像投影。
* 請確定您的環境已設定適當的追蹤。
* 設計您的體驗，以避免在框架內的各種焦點深度層級進行全像投影。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [全像穩定性和幀的影像](hologram-stability.md#frame-rate)
* [使用穩定平面的案例研究](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)
* [對 Unity 的效能建議](../unity/performance-recommendations-for-unity.md)
* [空間錨點](../../design/spatial-anchors.md)
* [處理追蹤錯誤](../../design/coordinate-systems.md#handling-tracking-errors)
* [固定的參考框架](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR IPD 套件，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>在實際表面上的全息圖位置

不一致具有實體 (物件的全像地理位置的，如果要放置在彼此之間的關聯，) 會清楚指出非全像全像的非等量和真實世界。 放置的精確度應該相對於案例的需求;例如，一般表面放置可以使用空間地圖，但是更準確的放置將需要使用標記和校正。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
| 全像平面的全像平面的圖格對齊。 如果需要更多精確度，應用程式應該提供有效的方法，以在所需的應用程式規格內共同作業。 | NA | 將表面平面中斷或遠離表面，以將實體目標物件顯示為未對齊。 如果需要精確度，則全像全像全像）會符合案例的相近規格。 | 

### <a name="how-to-measure"></a>如何測量

* 放在空間地圖上的全像影像應該不會明顯地浮動在表面上方或下方。
* 需要精確放置的全像投影必須有某種形式的標記和校正系統，才能精確地因應案例需求。

### <a name="recommendations"></a>建議

* 空間地圖適用于在不需要 precision 時將物件放在表面上。
* 為了獲得最佳的精確度，請使用標記或海報來設定全像是 (或某些手動對齊機制) 來進行最終校正。
* 請考慮將超大的全像分割分成邏輯部分，並將每個部分對齊表面。
* 不正確地設定 interpupillary 距離 (IPD) 也可以影響全息圖對齊。 一律將 HoloLens 設定為使用者的 IPD。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [空間對應放置](../../design/spatial-mapping.md#placement)
* [會議室掃描流程](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [空間錨點最佳作法](../../design/spatial-anchors.md#best-practices)
* [處理追蹤錯誤](../../design/coordinate-systems.md#handling-tracking-errors)
* [Unity 中的空間對應](../unity/spatial-mapping-in-unity.md)
* [Vuforia 開發總覽](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR 工具組、空間對應庫](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR 配套套件，海報校正範例](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR IPD 套件，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>外部參考

* [Lowes 案例研究，精確度對齊](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>觀賞緩和區域

應用程式開發人員藉由在不同的深度放置內容和全息，來控制使用者的眼睛。 使用 HoloLens 的使用者永遠都能容納 2.0 m，以維護清楚的影像，因為 HoloLens 顯示器是固定于大約 2.0 m 與使用者之間的距離。 不當的內容深度可能會導致 visual 不適感或疲勞。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

<table>
<tr>
<td> 最佳 </td><td><ul>
<li>將內容放在2m。</li><li>當您無法在2m 上放置全像全像，但無法避免聚合和住宿之間的衝突時，將會在 1.25 m 和5m 之間放置全像位置的最佳區域。</li><li>在每個案例中，設計人員都應該結構內容，以鼓勵使用者在 (的情況下互動 1 + m，例如調整內容大小和預設位置參數) 。</li><li>除非此案例特別需要，否則裁剪平面應該會在 fadeout 開始時，從1m 開始執行。</li><li>如果需要更仔細觀察 motionless 全息圖，內容不應比50cm 更接近。</li>
</ul></td>
</tr><tr>
<td> 會見</td><td> 內容位於觀看和移動的指導方針中，但不正確的使用或不使用裁剪平面。</td>
</tr><tr>
<td> 失敗 </td><td> 內容呈現太接近的 (通常是 &lt; 1.25 m，或 &lt; 需要更深入觀察的靜止全像50cm。 ) </td>
</tr>
</table>

### <a name="how-to-measure"></a>如何測量

* 內容通常應該2m 離開，但不能比5m 更接近1.25 或更早。
* 除了少數例外狀況，您應該將 HoloLens 裁剪轉譯距離設定為. 85CM 與 fadeout 的內容，起價為1m。 處理內容並記下裁剪平面效果。
* 固定內容不應接近50cm 的距離。

### <a name="recommendations"></a>建議

* 設計內容以取得2m 的最佳觀賞距離。
* 將 [裁剪轉譯距離] 設定為 [85cm]，其中 fadeout 的內容是從1m 開始。
* 對於需要更近觀賞的靜止全像影像，裁剪平面應該不會接近30cm，而且 fadeout 至少應該從裁剪平面開始10cm。

### <a name="resources"></a>資源

* [呈現距離](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦點](../unity/focus-point-in-unity.md)
* [使用 scale 進行實驗](../../design/scale.md#experimenting-with-scale)
* [文字，建議使用的字型大小](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a>深度切換

不論是在哪裡觀賞緩和問題，使用者都需要經常或快速地在接近或遠的焦點物件之間切換， (包括全像全半形的內容) 可能會導致 oculomotor 疲勞和一般不適感。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
|  不會導致使用者 unnaturally 將的有限或自然深度切換。 | 最深度的參數是核心，並設計為應用程式體驗或非預期的真實世界內容所造成的深度深度切換。 | 一致的深度切換，或不必要或核心到應用程式體驗的深度切換。 | 

### <a name="how-to-measure"></a>如何測量

* 如果應用程式要求使用者一致且/或突然變更深度焦點，則會有深度切換問題。

### <a name="recommendations"></a>建議

* 將主要內容保持在一致的焦點平面上，並確定穩定平面符合焦點平面。 這可減輕 oculomotor 疲勞和非預期的全像移動。

### <a name="resources"></a>資源

* [呈現距離](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦點](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>使用空間音效

在 Windows Mixed Reality 中，音訊引擎會使用方向、距離和環境模擬來模擬3D 音效，以提供混合現實體驗的 aural 元件。 在應用程式中使用空間音效，可讓開發人員 convincingly 將音效放在三維空間 (球體) 在使用者周圍。 這些音效看起來就像是來自真實的實體物件，或是使用者的環境中的混合現實全息。 空間音效是深度、協助工具和 UX 設計在混合現實應用程式中的強大工具。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
|  音效會以邏輯方式 hrtf，而且 UX 會適當地使用音效來協助物件探索和使用者意見反應。 音效自然且與物件相關，並在整個案例中正規化。 | 空間音訊可適當地用於 believability，但卻遺失，以協助使用者提供意見反應和探索。 | 音效未如預期般 hrtf，以及/或缺乏音效來協助使用者在 UX 內。 或空間音訊在案例設計中未被視為或使用。 | 

### <a name="how-to-measure"></a>如何測量

* 一般情況下，相關的音效應該會從目標全息的 (（例如，來自全像狗的吠音效）發出。 ) 
* 聲音提示應該用於整個 UX，以協助使用者提供全像全像攝影框架外的動作意見反應或認知。

### <a name="recommendations"></a>建議

* 使用空間音訊協助物件探索和使用者介面。
* 實際音效的效果優於合成或非自然音效。
* 大部分的音效都應該 hrtf。
* 避免不可見的發射器。
* 避免空間遮罩。
* 將所有音效標準化。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [空間音效](../../design/spatial-sound.md)
* [空間音效設計](../../design/spatial-sound-design.md)
* [Unity 中的空間音效](../unity/spatial-sound-in-unity.md)
* [案例研究、HoloTour 的空間音效](../../design/case-study-spatial-sound-design-for-holotour.md)
* [個案研究，在 RoboRaid 中使用空間音效](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MRToolkit，空間音訊](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>專注于全像攝影框架 (FOV) 界限

設計完善的使用者體驗可以建立和維護在使用者周圍擴充之虛擬環境的實用內容。 減輕 FOV 界限的影響，牽涉到精心設計的內容規模和內容、空間音訊的使用、指引系統，以及使用者的位置。 如果完成，使用者會覺得 FOV 界限不會受到影響，同時讓應用程式體驗更舒適。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
|  使用者永遠都不會遺失內容和觀賞。 針對大型物件提供內容協助。 探索和觀看指引是針對框架外的物件提供。 一般情況下，全像影像的移動設計和縮放比例適用于舒適的觀賞體驗。 | 使用者絕對不會遺失內容，但在有限的情況下可能需要額外的頸部動作。 在有限的情況下，縮放會導致全像是垂直或水準框架，而導致某些頸部的移動顯示全像影像。 | 使用者可能遺失內容和（或）一致的頸部動作來觀看全像全像投影。 沒有大型全息型物件的內容指引、移動物件很容易在框架外遺失，也沒有可搜尋的指引，或高的全像全像投影需要定期移動。 | 

### <a name="how-to-measure"></a>如何測量

*  (大型) 全息圖的內容遺失或無法理解，因為已在界限上修剪。
* 因為缺乏注意總監或內容快速移入和移出全像外框，所以很難找到全像的位置。
* 案例需要定期和重複的向上和向下鍵，才能完全查看會導致疲勞的全像投影。

### <a name="recommendations"></a>建議

* 使用符合 FOV 的小型物件開始體驗，然後以視覺提示轉換成較大的版本。
* 使用「空間音訊」和「注意總監」來協助使用者尋找 FOV 以外的內容。
* 盡可能避免以垂直方式裁剪 FOV 的全像影像。
* 為使用者提供應用程式內的指引，以取得最佳的觀賞位置。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [全像攝影框架](../../design/holographic-frame.md)
* [案例研究、HoloStudio UI 和互動設計學習](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [物件和環境的規模](../../design/scale.md)
* [資料指標，視覺提示](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a>外部參考

* [關於 FOV 的許多 ado](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>內容會回應使用者位置

全像「真實」物件的方式，全像是對使用者的位置做出回應。 值得注意的設計考慮是 UI 元素，這些元素不一定會假設使用者的位置是固定的，而且會適應使用者的動作。 設計可正確調整為使用者位置的應用程式，將會建立更可信的體驗，並讓您更容易使用。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

<table>
<tr>
<td> 最佳 </td><td> 內容和 UI 會適應使用者的位置，讓使用者可以自然地與預期使用者移動範圍內的內容互動。</td>
</tr><tr>
<td> 會見 </td><td> UI 可適應使用者的位置，但可能會妨礙需要使用者調整其位置的重要內容。</td>
</tr><tr>
<td> 失敗 </td><td><ol>
<li>UI 元素在移動期間遺失或鎖定，導致使用者 unnaturally 回到 (或尋找) 控制項。</li><li>UI 元素會限制主要內容的顯示。</li><li>UI 移動不是針對以 <a href="../../design/billboarding-and-tag-along.md">標記方向</a> 的 UI 元素而優化的觀賞距離和動力。</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>如何測量

* 所有度量都應該在案例的合理範圍內完成。 雖然使用者移動會有所不同，但請不要嘗試對應用程式進行極大的使用者移動。
* 針對 UI 專案，不論使用者是否移動，都應該可以使用相關的控制項。 比方說，如果使用者是以縮放比例流覽3D 地圖，則不論位置為何，縮放控制項都應可立即提供給使用者使用。

### <a name="recommendations"></a>建議

* 使用者是相機，並負責控制移動。 讓它們磁片磁碟機。
* 請考慮 billboarding 適用于文字和功能表系統的情況，如果使用者要四處移動，則會被鎖定或遮蔽。
* 針對需要追蹤使用者的內容使用標籤，同時讓使用者能夠查看他們之前的內容。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [互動設計](../../discover/hologram.md)
* [色彩、燈光和材質](../../color,-light-and-materials.md)
* [佈告板和常駐標籤](../../design/billboarding-and-tag-along.md)
* [本能互動](../../design/interaction-fundamentals.md)
* [自我運動和使用者運動](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a>輸入互動清楚明瞭

輸入互動清楚地對應用程式的可用性很重要，並包括互動方法的輸入一致性、是多麼平易近人、可探索性。 使用者應該能夠在不重新的情況下使用全平臺的一般互動。 如果應用程式具有自訂輸入，則應該清楚地傳達和示範。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
|  輸入互動方法與 Windows Mixed Reality 提供的 [指導](../../design/interaction-fundamentals.md)方針一致。 任何自訂輸入都不應與標準輸入一樣重複 (而是使用標準的互動) ，而且必須清楚地傳達並向使用者展示。 | 類似于最佳，但自訂輸入是具有標準輸入方法的多餘。 使用者仍然可以透過應用程式體驗來達成目標和進度。 | 難以瞭解輸入方法或按鈕對應。 輸入經過大量自訂，不支援標準輸入、沒有指示，或可能造成疲勞和緩和問題。 | 

### <a name="how-to-measure"></a>如何測量

* 應用程式會使用一致的 [標準輸入方法。](../../design/interaction-fundamentals.md)
* 如果應用程式具有自訂輸入，則會透過下列方式明確地傳達：
* 首次執行體驗
* 簡介畫面
* 工具提示
* 手勢指導
* 說明區段
* 旁白

### <a name="recommendations"></a>建議

* 盡可能使用標準輸入方法。
* 提供非標準輸入方法的示範、教學課程和工具提示。
* 在整個應用程式中使用一致的互動模型。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [本能互動](../../design/interaction-fundamentals.md)
* [互動物件](../../design/interactable-object.md)
* [頭部目光和停駐](../../design/gaze-and-dwell.md)
* [資料指標](../../design/cursors.md)
* [緩和和注視](../../design/comfort.md#gaze-direction)
* [語音輸入](../../design/voice-input.md)
* [運動控制器](../../design/motion-controllers.md)
* [Unity 的輸入移植指南](../porting-apps/input-porting-guide-for-unity.md)
* [Unity 中的鍵盤輸入](../unity/keyboard-input-in-unity.md)
* [Unity 中的目光](../unity/gaze-in-unity.md)
* [Unity 中的筆勢和運動控制器](../unity/gestures-and-motion-controllers-in-unity.md)
* [Unity 中的語音輸入](../unity/voice-input-in-unity.md)
* [DirectX 中的鍵盤、滑鼠及控制器輸入](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [DirectX 中的頭部和眼睛目光](../native/gaze-in-directx.md)
* [DirectX 中的手部和運動控制器](../native/hands-and-motion-controllers-in-directx.md)
* [DirectX 中的語音輸入](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [案例研究：追求更多個人運算的能力](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Cast 研究： HoloStudio UI 和互動設計學習](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [範例應用程式：元素的定期資料表](../unity/periodic-table-of-the-elements.md)
* [範例應用程式：陰曆模組](../unity/lunar-module.md)

## <a name="interactable-objects"></a>互動物件

按鈕一直以來都是用來觸發2D 抽象世界中事件的比喻。 在三維混合現實世界中，我們不再需要局限于這種抽象概念。 任何專案都可以是觸發事件的互動物件。 互動物件可以表示為來自資料表咖啡杯的任何事物，以及浮動在空氣中的球形球。 無論表單為何，使用者都應該透過視覺和音訊提示清楚地辨識互動物件。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
|  無論何種形式，互動物件都可以透過視覺和音訊提示，在三種狀態中辨識：閒置、目標和選取。 「看起來」清楚且一致地在整個體驗中使用。 物件會進行調整並散佈，以允許無錯誤的目標。 | 使用者可以透過音訊或視覺效果的意見反應將物件辨識為互動，並且可以將物件設為目標並啟用。 | 由於沒有視覺效果或音訊提示，使用者無法辨識互動物件。 互動會因為物件之間的縮放或距離而容易出錯。 | 

### <a name="how-to-measure"></a>如何測量

* 互動物件可辨識為 ' 互動 ';包括按鈕、功能表和應用程式特定內容。 根據經驗法則，在目標為互動物件時，應該會有視覺和音訊提示。

### <a name="recommendations"></a>建議

* 使用視覺效果和音訊意見反應進行互動。
* 您應針對每個輸入狀態， (閒置、目標、選取的) ，來區分視覺效果意見反應
* 互動物件應該調整並放置，以找出錯誤的目標。
* 群組互動物件 (例如功能表列或清單) 應該具有適當的目標間距。
* 支援 voice 命令的按鈕和功能表應該提供命令關鍵字的文字標籤 ( "見它，例如" ) 

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [可互動的物件](../../design/interactable-object.md)
* [Unity 中的文字](../unity/text-in-unity.md)
* [週框方塊和應用程式列](../../design/app-bar-and-bounding-box.md)
* [語音輸入](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [混合現實工具組-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>掃描房間

需要空間對應資料的應用程式依賴裝置在一段時間內自動收集此資料，並在使用者探索其環境中使用中的裝置時，跨會話自動收集此資料。 這項資料的完整性和品質取決於許多因素，包括使用者已完成的探索量、從探索以來經過的時間，以及裝置掃描區域之後是否已移動傢俱和大門等物件。 許多應用程式會在體驗開始時分析空間對應資料，以判斷使用者是否應該執行額外的步驟，以改善空間地圖的完整性和品質。 如果使用者需要掃描環境，請在掃描體驗期間提供清楚的指引。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
|  空間網格的視覺效果可讓使用者掃描正在進行中。 使用者清楚知道要做什麼，以及何時開始和停止掃描。 | 提供空間網格的視覺效果，但使用者可能不清楚知道要執行的動作，也不會提供任何進度資訊。 | 沒有網格的視覺效果。 未提供任何指引資訊給使用者，找出要查看的位置，或掃描何時啟動/停止。 |

### <a name="how-to-measure"></a>如何測量

* 在需要的房間掃描期間，會提供視覺和音訊指引來指出要查看的位置，以及開始和停止掃描的時機。

### <a name="recommendations"></a>建議

* 指出使用者鄰近區中的總數量必須是經驗的一部分。
* 當掃描啟動並停止（例如進度指示器）時進行通訊。
* 在掃描期間使用網格的視覺效果。
* 提供視覺和音訊提示，以鼓勵使用者查看和四處移動房間。
* 通知使用者移至何處以改善資料。 在許多情況下，最好讓使用者知道他們需要做什麼事 (例如查看最上方的 [傢俱]) ，以便取得所需的掃描品質。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [空間位置掃描視覺效果](../../design/room-scan-visualization.md)
* [案例研究：擴充 HoloLens 的空間對應功能](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [案例研究： HoloTour 的空間音效設計](../../design/case-study-spatial-sound-design-for-holotour.md)
* [案例研究：在片段中建立沉浸式體驗](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [混合現實工具組-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>方向指標

在混合現實應用程式中，內容可能會在真實世界物件的視野或 pixels occluded 之外。 設計完善的應用程式可讓使用者更容易找到不可見的內容。 方向指標會將使用者警示至重要內容，並提供相對於使用者位置之內容的指引。 非可見內容的指引可以採用音效發射器、方向箭號或直接視覺提示的形式。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
|  視覺效果和音訊提示會直接引導使用者前往視野以外的相關內容。 | 箭號或某些指標，可在內容的一般方向中指向使用者。 | 相關內容位於視野的範圍之外，且不佳或未提供任何位置指引給使用者。 | 

### <a name="how-to-measure"></a>如何測量

* 您可以透過視覺和/或音訊提示，探索使用者欄位外的相關內容。

### <a name="recommendations"></a>建議

* 當相關內容不在使用者的 view 欄位之外時，請使用方向指標和音訊提示，將使用者引導至內容。 在許多情況下，直接的視覺效果指南優先于方向箭號。
* 方向指標不應內建在游標內。

### <a name="resources"></a>資源

* [全像攝影框架](../../design/holographic-frame.md)

## <a name="data-loading"></a>載入資料

進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。 這可能表示使用者無法在進度指標可見時與應用程式互動，也可以指出等候時間可能的時間長度。

### <a name="device-impact"></a>裝置影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  會見 |  失敗 |
--- | --- | ---
|  以進度列或環形形式呈現的動畫視覺指標，顯示任何資料載入或處理期間的進度。 視覺指標會提供等待時間長度的指引。 | 使用者會收到資料載入進行中的通知，但不會指出等候的時間長度。 | 沒有任何資料載入或處理時間超過5秒的程式指示器。 |

### <a name="how-to-measure"></a>如何測量

* 在資料載入期間，請確認沒有任何空白狀態超過5秒。

### <a name="recommendations"></a>建議

* 提供資料載入 animator，顯示當使用者可能會察覺到此應用程式停止或損毀時的進度。 合理的經驗法則是任何可能需要5秒以上的「載入」活動。

### <a name="resources"></a>資源

* [顯示進度](../../design/progress.md)
