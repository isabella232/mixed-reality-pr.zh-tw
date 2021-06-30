---
title: 全像投影穩定性
description: HoloLens 會自動穩定的全像影像，但開發人員可以採取一些步驟來進一步改善全像影像的穩定性。
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: 全像投影、穩定性、hololens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、畫面播放速率、轉譯、reprojection、色彩分隔
appliesto:
- HoloLens
ms.openlocfilehash: a4a22221d3238bb7dfed711e6ee1f11edc70238e
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042289"
---
# <a name="hologram-stability"></a>全像投影穩定性

為了達成穩定的全像，HoloLens 有內建的影像穩定管線。 穩定管線會在背景中自動運作，因此您不需要採取任何額外的步驟來啟用它。 不過，您應該練習改善全像全像的技術，並避免降低穩定性的案例。

## <a name="hologram-quality-terminology"></a>全像影像品質術語

全像是環境和良好應用程式開發的結果。 在 HoloLens 可以追蹤周圍的環境中，每秒在常數60畫面格上執行的應用程式，可確保全像影像和相符的座標系統都處於同步狀態。從使用者的觀點來看，要成為固定的全像全像，不會隨著環境而移動。

當您識別環境的問題、不一致或低轉譯率，或其他任何情況時，下列術語可以協助您。
* **精度。** 一旦全像世界鎖定並放在現實世界中，就應該將它放在相對於周圍環境的位置，以及與使用者移動或小型和稀疏的環境變更無關。 如果在非預期的位置中出現的全息圖，則是 *精確度* 問題。 如果兩個不同的房間看起來相同，就會發生這種情況。
* **抖動。** 使用者將抖動視為高頻率搖動的全像影像，這可能會在環境降低時發生。 針對使用者，解決方案正在執行 [感應器微調](/hololens/hololens-updates)。
* **Judder.** 低轉譯頻率會導致不平均的移動和雙空間影像。 Judder 在具有移動功能的全像影像中特別明顯。 開發人員必須維持 [固定的 60 FPS](hologram-stability.md#frame-rate)。
* **漂移。** 使用者會看到因為全像全像投影一樣的漂移。 當您放置離 [空間錨點遠離空間錨點](../../design/spatial-anchors.md)（尤其是在環境未對應的部分）時，就會發生漂移。 建立接近空間錨點的全像影像，可降低漂移的可能性。
* **Jumpiness.** 當全像的位置，而不是在它的位置， Jumpiness 可能會隨著追蹤調整，以符合對您環境的更新理解。
* **游泳。** 當與使用者前端的動作相對應的全像是 sway 時。 當應用程式未完全實 [reprojection](hologram-stability.md#reprojection)，且未針對目前使用者 [校正](/hololens/hololens-calibration) HoloLens 時，就會發生泳道。 使用者可以重新執行 [校正](/hololens/hololens-calibration) 應用程式以修正問題。 開發人員可以更新穩定平面來進一步增強穩定性。
* **色彩分隔。** HoloLens 中的顯示為彩色順序顯示，可在 60 Hz 將紅色-綠色-藍色-綠色的色頻閃爍 (個別的色彩欄位會顯示在 240 Hz) 。 每當使用者以眼睛來追蹤移動全息圖時，該全息圖的開頭和尾端邊緣會以其構成色彩分隔，產生彩虹效果。 分隔程度取決於全息圖的速度。 在某些罕見的情況下，在查看固定的全像點時快速移動一次，也會造成彩虹的效果，稱為 *[色彩分隔](hologram-stability.md#color-separation)*。

## <a name="frame-rate"></a>畫面播放速率

畫面播放速率是全像全像要件的第一次的影像。 若要讓全像全球的影像顯示穩定，則呈現給使用者的每個影像都必須以正確的位置繪製影像。 HoloLens 重新整理240次時，會顯示四個不同的色彩欄位給每個新轉譯的影像，讓使用者體驗 60 FPS (每秒畫面格) 。 為了盡可能提供最佳體驗，應用程式開發人員必須維持 60 FPS，這會轉譯成每16毫秒都能以一致的方式提供新的映射給作業系統。

**60 FPS** 為了繪製像是坐在現實世界的全像桌，HoloLens 需要從使用者的位置呈現影像。 由於影像轉譯需要一些時間，因此 HoloLens 會預測使用者的標頭在顯示中顯示時的位置。 不過，此預測演算法是近似值。 HoloLens 的硬體會調整轉譯的影像，以考慮預測的標頭位置與實際的 head 定位之間的差異。 調整會讓使用者看到的影像看起來像是從正確的位置轉譯，而全像是穩定的。 映射更新最適用于小型變更，而且無法完整修正轉譯影像中的特定專案，例如視差。

藉由轉譯 60 FPS，您會執行三個動作來協助您建立穩定的全像：
1. 將轉譯影像和使用者看到的影像之間的整體延遲降至最低。 在具有遊戲的引擎和在密集建置中執行的轉譯執行緒中，在30FPS 上執行時，可能會增加33.3 毫秒的額外延遲。 減少延遲可減少預測錯誤，並增加全像全像的穩定性。
2. 讓每個影像觸達使用者的眼睛，都有一致的延遲時間。 如果您在 30 fps 的情況下轉譯，顯示器仍會以 60 FPS 顯示影像，這表示相同的影像會顯示在資料列中兩次。 第二個框架的延遲比第一個畫面的延遲16.6 還要高，且必須更正更顯著的錯誤數量。 這種錯誤的大小不一致可能會造成不必要的 60 Hz judder。
3. 減少出現顫抖，它的特色是不平均的運動和雙重影像。 更快的全像投影動作和更低的轉譯率與更明顯的顫抖相關聯。 隨時致力於維護 60 FPS，將有助於避免特定移動全息圖的 judder。

**畫面播放速率一致性** 畫面播放速率一致性就像每秒高框架一樣重要。 針對任何內容豐富的應用程式，偶爾會捨棄的框架是不可避免的，而 HoloLens 會實行一些精密的演算法來從偶爾的問題中復原。 不過，不斷變動的畫面播放速率對使用者而言，比以較低的畫面播放速率一致地執行更為明顯。 例如，在這五個畫面的持續時間內，針對五個框架順暢轉譯的應用程式 (60 FPS) 然後卸載接下來10個畫面格的每個其他畫面格 (30 FPS，在這10個畫面的持續時間內，) 將會比一致呈現 30 FPS 的應用程式更不穩定。

在相關的附注中，當 [混合的現實 capture](/hololens/holographic-photos-and-videos) 正在執行時，作業系統會將應用程式限制為 30 FPS。

**效能分析** 有不同類型的工具可用來對您的應用程式框架速率進行基準測試，例如：
* GPUView
* Visual Studio 圖形偵錯工具
* 內建于3D 引擎（例如 Unity）中的分析工具

## <a name="hologram-render-distances"></a>全像影像轉譯距離

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

人力視覺系統在 fixates 和聚焦于物件時，會整合多個距離相關的信號。
* [住宿](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) -個人眼的焦點。
* [聚合](https://en.wikipedia.org/wiki/Convergence_(eye)) -在物件上向內或向外移動雙眼睛。
* [Binocular 視覺](https://en.wikipedia.org/wiki/Stereopsis) -Disparities 與距離您 fixation 點的物件距離相關的左側和右側影像。
* 陰影、相對角度大小和其他 monocular (單一眼睛) 提示。

聚合和便利的獨特之處在于，其視網膜的提示與眼睛如何變化來觀察不同距離的物件有關。 在自然觀賞中，聚合和住宿都已連結。 當眼睛接近 (例如，您的鼻子) 、眼睛交叉及接近接近的點。 當眼睛是無限大的地方時，眼睛會變成平行，而眼睛則會容納到無限大。 

使用 HoloLens 的使用者永遠都能容納 2.0 m，以維護清楚的影像，因為 HoloLens 顯示器是固定的，而與使用者之間的距離大約是 2.0 m。 應用程式開發人員藉由在不同的深度放置內容和全息，來控制使用者的眼睛。 當使用者配合並融合至不同的距離時，兩個提示之間的自然連結會中斷，而這可能會導致 visual 不適感或疲勞，特別是當衝突的程度很大時。 

不適感自 vergence-住宿衝突可以避免或最小化，方法是將交集內容保持在接近 2.0 m 的位置， (也就是，在有許多深度放置接近 2.0 m 的地方時，可能) 。 當內容不能放在 2.0 m 附近時，當使用者在不同距離之間回頭看時，從 vergence-住宿衝突的不適感是最大的。 換句話說，觀看保持在 50 公分距離的固定全像投影，比觀看在 50 公分距離而隨著時間離您忽遠忽近的全像投影，要來得舒適。

將內容放在 2.0 m 也很有利，因為這兩個顯示器的設計目的是要在這個距離完全重迭。 對於放置於此平面的影像，當它們移離全像攝影框架的側邊時，它們會顯示在另一個顯示器上。 這個 binocular rivalry 可能會干擾全像影像的深度理解。

**放置距離使用者的全像投影最佳距離**

![放置距離使用者的全像投影最佳距離](images/distanceguiderendering-750px.png)

**剪輯平面** 為了達到最大的限制，建議您在 85 cm 裁剪轉譯距離，並從 1 m 開始的內容淡化。 在全像是靜止的應用程式中，可輕鬆地以 50 cm 的形式來觀看全像。在這些情況下，應用程式應該將裁剪平面放置到接近 30 cm 的位置，淡出應該從剪切平面開始至少 10 cm。 每當內容比 85 cm 更近時，請務必確保使用者不會經常從全像移動或更遠地移至不同的全像或更遠的移動，也不會經常從使用者更接近或更遠地移動，因為這些情況最可能會導致不適感發生 vergence 的問題。 內容的設計目的，是要盡可能減少與使用者更接近 85 cm 的互動需求，但是當內容必須比 85 cm 更近時，很適合開發人員的經驗法則是設計一些案例，讓使用者和/或全息全像時間的深度不會超過25%。

**最佳做法** 當您無法在2分鐘放置全像，而且無法避免聚合和住宿之間的衝突時，將會在 1.25 m 和 5 m 之間放置全像位置的最佳區域。 在每個案例中，設計人員都應該結構內容，以鼓勵使用者在 (的情況下互動 1 + m，例如調整內容大小和預設位置參數) 。

## <a name="reprojection"></a>Reprojection
HoloLens 有一種精密的硬體輔助全像全像 reprojection。 Reprojection 會將移動點 (CameraPose) 在場景動畫中進行移動，並讓使用者移動其頭部。  應用程式必須採取特定動作，以充分使用 reprojection。


Reprojection 有四種主要類型
* **深度 Reprojection：**  從應用程式產生最少投入量的最佳結果。  轉譯的場景的所有元件都是根據與使用者的距離而獨立穩定。  某些呈現構件可能會顯示在深度的清晰變更。  此選項僅適用于 HoloLens 2 和沉浸式耳機。
* **平面 Reprojection：**  允許應用程式精確控制穩定。  平面是由應用程式所設定，而該平面上的所有專案都是場景中最穩定的部分。  另外一個全像是平面，也就是較不穩定的平面。  此選項適用于所有 Windows MR 平臺。
* **自動平面 Reprojection：**  系統會使用深度緩衝區中的資訊設定穩定平面。  此選項可在 HoloLens 世代1和 HoloLens 2 上使用。
* **無：** 如果應用程式沒有執行任何動作，就會在使用者的前端的方向以2個計量器固定的穩定平面使用平面 Reprojection，通常會產生 substandard 的結果。

應用程式必須採取特定動作來啟用不同類型的 reprojection
* **深度 Reprojection：** 應用程式會針對每個呈現的畫面格，將其深度緩衝區提交至系統。  在 Unity 上，會使用 [ **XR 外掛程式管理**] 下 [ **Windows Mixed Reality 設定**] 窗格中的 [**共用深度緩衝區**] 選項來完成深度 Reprojection。  DirectX 應用程式呼叫 CommitDirect3D11DepthBuffer。  應用程式不應呼叫 SetFocusPoint。
* **平面 Reprojection：** 在每個畫面上，應用程式會將平面的位置告訴系統穩定。  Unity 應用程式會呼叫 SetFocusPointForFrame，且應該停用 **共用深度緩衝區** 。  DirectX 應用程式呼叫 SetFocusPoint，不應呼叫 CommitDirect3D11DepthBuffer。
* **自動平面 Reprojection：** 若要啟用，應用程式必須將其深度緩衝區提交至系統，因為它們會進行深度 Reprojection。 使用混合現實工具組的應用程式 (MRTK) 可將 [相機設定提供者](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings#hololens-2-reprojection-method) 設定為使用 AutoPlanar Reprojection。 原生應用程式應該 `DepthReprojectionMode` 在 [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters) 中將設定為 `AutoPlanar` 每個框架。 若為 HoloLens 第1代，應用程式不應該呼叫 SetFocusPoint。

### <a name="choosing-reprojection-technique"></a>選擇 Reprojection 技術

穩定類型 |    沉浸式耳機 |    HoloLens 第1代 | HoloLens 2
--- | --- | --- | ---
深度 Reprojection |    建議 |   N/A |   建議<br/><br/>Unity 應用程式必須使用 Unity 2018.4.12 +、Unity 2019.3 + 或 Unity 2020.3 +。 否則，請使用自動平面 Reprojection。
自動平面 Reprojection | N/A |   建議的預設值 |   如果深度 Reprojection 未提供最佳結果，則建議使用<br/><br/>建議使用 unity 應用程式來使用 Unity 2018.4.12 +、Unity 2019.3 + 或 Unity 2020.3 +。  先前的 Unity 版本將會使用稍微降低的 reprojection 結果。
平面 Reprojection |   不建議 |   如果自動平面未提供最佳結果，則建議使用 | 如果沒有任何深度選項提供所需的結果，請使用    

### <a name="verifying-depth-is-set-correctly"></a>正在驗證深度設定是否正確
            
當 reprojection 方法使用深度緩衝區時，請務必確認深度緩衝區的內容是否代表應用程式呈現的場景。  許多因素可能會造成問題。 例如，如果有第二個相機用來呈現使用者介面重迭，則可能會覆寫實際視圖的所有深度資訊。  透明物件通常不會設定深度。  某些文字轉譯預設不會設定深度。  當深度不符合轉譯的全像投影時，轉譯中將會顯示問題。
            
HoloLens 2 具有可顯示深度為和未設定的視覺化效果，可從裝置入口網站啟用。  在 [**查看** 全像全像] 標籤上  >   ，選取 [**在耳機中顯示深度視覺效果**] 核取方塊。  已正確設定深度的區域會是藍色。  未設定深度的已轉譯專案會以紅色標示，並需要修正。  

> [!NOTE]
> 深度的視覺效果將不會顯示在混合實境擷取中。  只有透過裝置才能看到它。
            
某些 GPU 的查看工具將允許深度緩衝區的視覺效果。  應用程式開發人員可以使用這些工具來確定已正確設定深度。  請參閱應用程式工具的檔。

### <a name="using-planar-reprojection"></a>使用平面 Reprojection
> [!NOTE]
> 針對桌面沉浸式耳機，設定穩定平面通常會有生產力，因為它提供的視覺品質較低，因為它比提供應用程式深度緩衝區到系統，以啟用以圖元深度為基礎的 reprojection。 除非在 HoloLens 上執行，否則您通常應該避免設定穩定平面。

![3D 物件的穩定平面](images/stab-plane-500px.jpg)

裝置會自動嘗試選擇此平面，但應用程式應該在場景中選取焦點點來提供協助。 在 HoloLens 上執行的 Unity 應用程式應該根據您的場景選擇最佳焦點點，並將它傳遞至 [SetFocusPoint () ](../unity/focus-point-in-unity.md)。 預設的旋轉 cube 範本中包含設定 DirectX 中焦點點的範例。

Unity 會將您的深度緩衝區提交至 Windows，以在連線到桌上型電腦的沉浸式耳機上執行應用程式時啟用每圖元 reprojection，如此可提供更佳的影像品質，而不會由應用程式明確運作。 當您的應用程式在 HoloLens 上執行時，您應該只提供焦點點，否則將會覆寫每圖元 reprojection。


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

放置焦點點主要取決於全息圖所查看的內容。 應用程式有參考的注視向量，而應用程式設計師知道他們希望使用者觀察到的內容。

開發人員可以在穩定的全像投影上做的最重要的一件事，就是以 60 FPS 呈現。 低於 60 FPS 將大幅減少全像穩定平面優化的全像

**最佳做法** 沒有任何通用的方法可以設定穩定平面，而且它是應用程式特定的。 我們的主要建議是實驗並瞭解最適合您案例的功能。 但是，請儘量將穩定平面與最多的內容對齊，因為此平面上的所有內容都是完全穩定的。

例如：
* 如果您只有 (讀取應用程式的平面內容、影片播放應用程式) ，請將穩定平面與具有內容的平面對齊。
* 如果有三個小球體被全球鎖定，請讓穩定平面「剪下」到目前在使用者觀點的所有球體的中心。
* 如果您的場景具有本質上不同的內容，請優先採用物件。
* 請務必調整每個畫面格的穩定點，使其與使用者所查看的全像影像一致

**要避免的事項** 穩定平面是達成穩定全息的絕佳工具，但如果誤用，可能會導致嚴重的映射不穩定。
* 別「火災別忘了」。 最後，您可以使用使用者背後的穩定平面，或是附加至不再位於使用者觀點的物件。 請確定穩定平面是設定為相對相機向前 (，例如-攝影機。轉寄) 
* 不要在極端之間來回變更穩定平面
* 不要讓穩定平面設定為固定距離/方向
* 不要讓穩定平面剪下使用者
* 在桌上型電腦上執行時，請勿設定焦點，而是改為依賴每個圖元的深度型 reprojection。

## <a name="color-separation"></a>色彩分隔 

由於 HoloLens 顯示器的本質，有時可能會察覺稱為「色彩分隔」的成品。 它會將影像列為分隔為個別基底色彩的影像-紅色、綠色和藍色。 顯示白色物件時，可能會特別看到構件，因為它們有大量的紅色、綠色和藍色。 最重要的是，當使用者以視覺化方式追蹤在全像全像全像全像的全像影像畫面上移動的全像影像。 成品可以資訊清單的另一種方式是物件的變形/變形。 如果物件具有高對比及/或純粹的色彩（例如紅色、綠色、藍色），色彩分隔將會被視為物件的不同部分的變形。

**當標頭鎖定的白色圓形游標的色彩分離時，可能看起來像是使用者將其頭部旋轉到側邊的範例：**

![標頭鎖定的白色圓形游標的色彩分隔，在使用者將其標頭旋轉到側邊時可能看起來的範例。](images/colorseparationofroundwhitecursor-300px.png)

雖然很難完全避免色彩分隔，但是有幾種技巧可減輕問題。

**您可以在下列情況看到色彩分隔：**
* 快速移動的物件，包括標頭鎖定的物件，例如資料 [指標](../../design/cursors.md)。
* 遠距離 [穩定平面](hologram-stability.md#reprojection)的物件。

**若要 attenuate 色彩分隔的效果：**
* 讓物件延遲使用者的注視。 它看起來應該會像是有一些慣性，並且附加至注視的「上彈簧」。 這種方法會減緩游標 (減少分隔距離) ，並將它放在使用者可能的注視點後方。 只要它很快就會在使用者停止使其看起來很自然的時候，
* 如果您想要移動全息圖，如果您希望使用者以眼睛來追蹤，請嘗試將其移動速度維持在5度以下以下。
* 針對資料指標使用 *淺色* 而不是 *geometry* 。 附加至注視的虛擬照明來源會被視為互動式指標，但不會造成色彩分隔。
* 調整穩定平面，使其符合使用者所撥雲見日的全像影像。
* 將物件設為紅色、綠色或藍色。
* 切換至模糊的內容版本。 例如，您可以將圓形白色游標變更為移動方向中稍微模糊的線。

和之前一樣，在 60 FPS 和設定穩定平面的情況下，以最重要的方式呈現全像全像全像全像全像 如果面對明顯的色彩分隔，請先確定畫面播放速率符合預期。

## <a name="see-also"></a>另請參閱
* [瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)
* [色彩、光線和材質](../../design/color-light-and-materials.md)
* [本能互動](../../design/interaction-fundamentals.md)
* [MRTK 全像穩定](/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization)