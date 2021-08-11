---
title: 眼睛追蹤導覽
description: 如何在 MRTK 中使用視覺目標進行導覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: e1ca34054a019e26bebf14282cd351467e5c65e2c2c3fa4f35647dd5aba680ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197108"
---
# <a name="eye-supported-navigation-in-mrtk"></a>MRTK 中的眼睛支援導覽

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

Imagine 您正在閱讀手上的資訊，當您到達所顯示文字的結尾時，文字會自動向上滾動以顯示更多內容。 或者，您可以流暢放大查看的位置。 地圖也會自動調整內容，以在您的視圖欄位中保留感興趣的專案。 另一個有趣的應用程式是：自動將您想要的全像是您想要的全像投影部分，將您想要的全像投影零件帶到最前面。 以下是此頁面在支援的導覽內容中所描述的一些範例。

下列說明假設您已經熟悉如何 [在 MRTK 場景中設定眼睛追蹤](eye-tracking-basic-setup.md) ，以及如何在 MRTK Unity 中 [存取眼睛追蹤資料](eye-tracking-target-selection.md) 的基本概念。
下列範例中所討論的範例都是 `EyeTrackingDemo-03-Navigation` (資產/MRTK/範例/示範/EyeTracking/場景/EyeTrackingDemo-03-導覽) 場景的一部分。

**摘要：** 自動滾動文字、眼睛眼支援的移動流覽和縮放虛擬地圖、無人參與的3D 旋轉。

## <a name="auto-scroll"></a>自動滾動

自動滾動可讓使用者在不需要手上的情況下，透過文字進行滾動。
只要繼續閱讀，文字就會根據使用者的外觀自動向上或向下移動。
您可以從 `EyeTrackingDemo-03-Navigation` (資產/MRTK/範例/示範/EyeTracking/場景) 中提供的範例開始。
此範例會使用 [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) 元件，以允許彈性地載入及格式化新的文字。
若要啟用自動滾動，只要將下列兩個腳本新增至文字方塊的碰撞元件即可：

### <a name="scrollrecttransf"></a>ScrollRectTransf

若要在 [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) 或更一般說話的 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) 元件中進行滾動，您可以使用 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) 腳本。
如果您想要滾動紋理而非 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html)，請使用 [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) 而不是 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)。
以下將更詳細說明 Unity 編輯器中可用的 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) 參數：

參數 | 描述
:---- | :----
LimitPanning | 啟用時，將會在其界限停止可滾動的內容。
RectTransfToNavigate | 要在其中滾動的 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) 參考。
RefToViewport | 參考可滾動內容的父 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) ，以判斷正確的位移和界限。
AutoGazeScrollIsActive | 若已啟用，當使用者查看作用中 *區域* 時，文字會自動滾動 (例如，如果垂直捲動速度不是零) ，則會自動滾動捲軸的上方和底部部分。
ScrollSpeed_x | 如果設定為不等於零的值，則會啟用水準捲軸。 負數值表示滾動方向的變更：由左至右和從右至左。
ScrollSpeed_y | 如果設定為不等於零的值，則會啟用垂直捲動條。 負數值表示滾動方向的變更：向上到下，與向下到下。
MinDistFromCenterForAutoScroll | 從目標的點擊方塊中央算起，x 和 y 中的最短距離最短距離 (0，0) 可滾動。 因此，值的範圍必須介於 0 (一律滾動) 和 0.5 (不會有捲軸) 。
UseSkimProofing | 啟用時，會在快速尋找時防止突然滾動移動。 不過，這可能會讓滾動感覺更沒有回應。 您可以使用 *SkimProofUpdateSpeed* 值來調整它。
SkimProofUpdateSpeed | 值越低，skimming 後滾動的速度就越慢。 建議值：5。

![Unity 中的眼睛支援滾動設定](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

附加 _EyeTrackingTarget_ 元件可讓您靈活地處理眼睛相關的事件。
滾動範例會示範 *當使用者查看* 面板時啟動的滾動文字，並在使用者 *離開* 時停止。
![Unity 中的眼睛支援滾動設定： EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>注視支援的平移和縮放

神秘在搜尋首頁或探索全新位置之前，尚未使用虛擬對應？ 眼睛追蹤可讓您直接深入瞭解您感興趣的部分，一旦放大之後，您就可以順暢地遵循街道的課程來探索您的鄰近地區！
這不僅適用于探索地理地圖，也可以查看相片、資料視覺效果或甚至是即時串流醫療影像的詳細資料。 若要在您的應用程式中使用這項功能很簡單！ 針對轉譯成 [材質]( https://docs.unity3d.com/ScriptReference/Texture.html) 的內容 (例如，相片、串流處理的資料) ，只要新增 [PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) 腳本即可。
若為 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) ，請使用 [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf)。 在擴充 [自動滾動](#auto-scroll) 功能的同時，我們基本上可讓您同時垂直和水準滾動，並在使用者目前的焦點點周圍放大內容。

參數 | 描述
:---- | :----
LimitPanning | 啟用時，將會在其界限停止可滾動的內容。
HandZoomEnabledOnStartup | 指出是否自動啟用手勢來執行縮放手勢。 您可能會想要先停用它，以避免不小心觸發縮放動作。
RendererOfTextureToBeNavigated | 要流覽之材質的參考轉譯器。
Zoom_Acceleration | Zoom 加速定義羅吉斯速度函式對應的 steepness。
Zoom_SpeedMax | 最大縮放速度。
Zoom_MinScale | 放大紋理的最小尺規，例如 0.5 f (原始大小) 的一半。
Zoom_MaxScale | 放大的材質最大刻度-例如，1f (原始大小) 或 2.0 f (兩倍的原始大小) 。
Zoom_TimeInSecToZoom | 計時縮放：觸發之後，會在指定的時間量（以秒為單位）執行放大/縮小。
Zoom_Gesture | 用來放大/縮小的手勢型別。
--- | ---
Pan_AutoScrollIsActive | 若已啟用，當使用者查看作用中 *區域* 時，文字會自動滾動 (例如，如果垂直捲動速度不是零) ，則會自動滾動捲軸的上方和底部部分。
Pan_Speed_x | 如果設定為不等於零的值，則會啟用水準捲軸。 負數值表示滾動方向的變更：由左至右和從右至左。
Pan_Speed_y | 如果設定為不等於零的值，則會啟用垂直捲動條。 負數值表示滾動方向的變更：向上到下，與向下到下。
Pan_MinDistFromCenter | 從目標的點擊方塊中央算起，x 和 y 中的最短距離最短距離 (0，0) 可滾動。 因此，值的範圍必須介於 0 (一律滾動) 和 0.5 (不會有捲軸) 。
UseSkimProofing | 啟用時，會在快速尋找時防止突然滾動移動。 不過，這可能會讓滾動感覺更沒有回應。 您可以使用 *SkimProofUpdateSpeed* 值來調整它。
SkimProofUpdateSpeed | 值越低，skimming 後滾動的速度就越慢。 建議值：5。

![Unity 中支援的平移和縮放設定](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>以注意力為基礎的3D 旋轉

Imagine 查看3d 物件和您想要看到的部分，讓您更安心地轉向您的工作，就像系統會閱讀您的想法，並知道如何將專案轉變成您一樣！
這是以提示為基礎的3D 旋轉的概念，可讓您調查全像影像的所有側邊，而不需要抬起手指。
若要啟用此行為，只要將 [OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) 腳本新增至具有 [碰撞](https://docs.unity3d.com/ScriptReference/Collider.html) 元件的 GameObject 部分即可。
您可以調整以下所列的數個參數，以限制全息圖的速度和方向。

您可以想像，讓這項行為隨時都在作用中，可能會在擁擠的場景中迅速成為很多的注意力。
這就是為什麼您可能想要在停用此行為的情況下開始，然後使用語音命令快速加以啟用。
另外，我們也在 `EyeTrackingDemo-03-Navigation` (資產/MRTK/範例/示範/EyeTracking/) 場景中新增了一個範例，以使用 [TargetMoveToCamera](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) ，您可以選取焦點的目標，並在您之前飛出，只需要說「 *來到我*」。

在接近模式的情況下，自動旋轉模式會自動啟用。
在此模式中，您可以從所有邊觀察它，只要回頭 leaning 並查看它、四處四處進行，或向外旋轉即可。 當您關閉目標 (查看 &，或說「 *送回* 」) 時，它會返回其原始位置，並停止 afar 的回應。

參數 | 描述
:---- | :----
SpeedX | 水準旋轉速度。
迅速 | 垂直旋轉速度。
InverseX | 反轉水準旋轉方向。
InverseY | 反向垂直旋轉方向。
RotationThreshInDegrees | 如果「注視目標」和「相機到目標」之間的角度小於此值，請勿執行任何動作。 這是為了防止輕微的抖動旋轉。
MinRotX | 水準旋轉角度的最小值。 這是為了限制不同方向的旋轉。
MaxRotX | 最大水準旋轉角度。 這是為了限制不同方向的旋轉。
MinRotY | 最短垂直旋轉角度，以限制 X 軸的旋轉。
MaxRotY | 用來限制 y 軸旋轉的最大垂直旋轉角度。

![Unity 中支援的3D 旋轉設定](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

總而言之，上述腳本應可讓您開始對各種輸入導覽工作（例如滾動文字、縮放和移動流覽材質，以及輪換調查3D 全息圖）使用眼睛。

### <a name="see-also"></a>另請參閱

- [使用眼睛追蹤的基本 MRTK 設定](eye-tracking-basic-setup.md)
- [目視支援的目標選取範圍](eye-tracking-target-selection.md)

---
[回到「MixedRealityToolkit 中的眼睛追蹤」](eye-tracking-main.md)
