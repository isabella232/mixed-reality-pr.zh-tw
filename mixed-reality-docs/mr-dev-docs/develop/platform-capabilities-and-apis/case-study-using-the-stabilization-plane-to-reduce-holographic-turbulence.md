---
title: 案例研究-使用穩定平面
description: 探索我們的開發團隊如何使用穩定平面來減少混合現實應用程式中的全像 turbulence。
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、全息全像、穩定、個案研究、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 85caee589a5f031f605417639eab2e980cb613c5
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006698"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>個案研究-使用穩定平面減少全像 turbulence

使用全像影像通常很難處理。 四處移動空間並查看所有不同角度的全像影像，提供了一般電腦螢幕上無法使用的深度層級。 將這些全像放在一起，並在實際的情況下，您可以透過 Microsoft HoloLens 的硬體和智慧型的全像攝影應用程式設計來達成技術。

## <a name="the-tech"></a>技術

為了讓全像是與您分享空間一樣，它們應該會正確轉譯，而不需要色彩分隔。 這項功能是以內建于 HoloLens 硬體的技術為基礎來達成，讓全像是在所謂的 [穩定平面](hologram-stability.md#reprojection)上的全像投影。

平面是由點和一般定義。 由於我們一定會想要平面來臉部相機，因此我們關心的是設定平面的點。 我們可以告訴 HoloLens 要將其處理放在哪一點，以保持所有錨定和穩定。 不過，設定此焦點點是應用程式特定的，而且可以根據內容來建立或中斷應用程式。

當穩定平面已正確套用時，全像投影的效果最佳，但實際的意義取決於您所建立的應用程式類型。 讓我們來看看目前提供給 HoloLens 的一些應用程式如何解決這個問題。

## <a name="behind-the-scenes"></a>在幕後

在開發下列應用程式時，我們注意到，當我們未使用平面時，物件會在我們的標頭移動時使用 sway。 我們也會看到色彩分隔與快速 head 或全像投影的移動。 我們最後會透過試用版進行學習，以及如何以最佳方式使用穩定平面，並針對無法修正的問題設計應用程式。

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer：固定內容、3D 互動

[Galaxy Explorer](../unity/galaxy-explorer.md) 在場景中有兩個主要元素：著天體內容的主要觀點，以及您的注視之後的小型 UI 工具列。 針對穩定邏輯，我們會查看您目前的注視向量與每個畫面格相交的內容，以判斷它是否會在指定的碰撞圖層上到達任何內容。 在此情況下，我們感興趣的圖層是行星，因此，如果您的注視落在地球上，穩定平面便會放在該處。 如果未叫用目標碰撞層中的任何物件，應用程式會使用次要「方案 B」層。 如果未 gazed 任何專案，則穩定平面會保持與撥雲見日內容時相同的距離。 UI 工具會以平面目標的形式離開，因為我們發現接近或遠低於整體場景的穩定性。

Galaxy Explorer 的設計非常適合讓事物保持穩定，並減少色彩分隔的影響。 我們鼓勵使用者四處四處移動內容，而不是從側邊移動，且行星的軌道速度夠慢，因此不會明顯地區分色彩。 此外，也會維持常數 60 FPS，以防止發生色彩分離的情形。

若要自行查看，請在 [GitHub 上的 Galaxy Explorer 程式碼](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)中尋找名為 LSRPlaneModifier.cs 的檔案。

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio：具有 UI 焦點的固定內容

在 HoloStudio 中，您大部分的時間都花在查看您正在處理的相同模型。 當您選取新的工具或想要流覽 UI 時，您的注視不會移動大量的數量，因此我們可以將平面設定邏輯保持簡單。 查看 UI 時，平面會設定為您要貼齊的任何 UI 元素。 查看模型時，平面是一組距離，與您與模型之間的預設距離相對應。

![HoloStudio 中的穩定平面會在 [首頁] 按鈕上以使用者 gazes 的形式視覺化](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour 和3D 檢視器：使用動畫和電影的固定內容

在 [HoloTour] 和 [3D 檢視器] 中，您會看到單獨的動畫物件或影片，並將3D 效果新增至其上方。 這些應用程式中的穩定會設定為您目前所觀看的任何內容。

HoloTour 也可讓您從虛擬世界 straying 太遠，而不需要離開固定位置。 這可確保在中，您將無法從其他的全像是其他的全像是穩定問題。

![在此範例中，HoloTour 會將穩定平面設定為 Hadrian 的 Pantheon 電影。](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid：動態內容和環境互動

儘管應用程式需要最突然的移動，但在 RoboRaid 中設定穩定平面非常簡單。 平面的目的是要與牆或周圍的物件有關，而且當您夠遠時，會在您前方的固定距離浮點數。

RoboRaid 是以穩定平面為考慮而設計的。 Reticle，因為它是標頭鎖定，所以最常使用紅色和藍色來規避，如此可將任何色彩不規則降至最低。 它也包含片段之間稍微的深度，藉由以預期的視差效果遮罩，以最小化所發生的色彩出血。 機器人不會快速移動，且只會以固定的間隔傳送短距離。 它們通常會在您之前停留2個計量，預設會設定穩定。

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>片段和年輕 Conker：具有環境互動的動態內容

Asobo Studio 在 c + + 中撰寫，片段和年輕 Conker 採用不同的方法來設定穩定平面。 感興趣的點 (POI) 是在程式碼中定義，並依優先順序排序。 Poi 是遊戲中的內容，例如年輕 Conker、功能表、意圖 reticle 和標誌的 Conker 模型。 Poi 會以使用者的注視來交集，且平面會設定為具有最高優先順序之物件的中心。 如果沒有任何交集，則會將平面設定為預設距離。

如果您移至先前掃描的播放空間以外的位置，則片段和年輕 Conker 也會藉由暫停應用程式，來設計離全像是 straying 太遠的影像。 因此，他們會將您保持在找到的界限內，以提供最穩定的體驗。

## <a name="do-it-yourself"></a>親自完成

如果您有 HoloLens，並且想要使用本文中的概念，您可以下載測試場景來嘗試下列練習。 測試場景會使用 Unity 的內建 gizmo API，協助您將平面的設定位置視覺化。 程式碼也用來捕捉此案例研究中的螢幕擷取畫面。
1. 同步最新版本的 [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)。
2. 開啟 [HoloToolkit-Examples/Utilities/場景/StabilizationPlaneSetting unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) 場景。
3. 建立並設定產生的專案。
4. 在您的裝置上執行。

### <a name="exercise-1"></a>練習1

您會看到幾個不同方向的點線。 在您之前，您會在不同的深度看到三個點。 按一下以變更平面設定的點。 在此練習中，如果是其他兩個，請在撥雲見日點時四處移動空間。 將您的頭部靠左、靠右、向上和向下。 從點更接近或更遠地移動。 查看當穩定平面設定為不同目標時如何回應。

### <a name="exercise-2"></a>練習2

現在，請在您看到兩個移動點、一個水準路徑上有一個不穩定的點，以及一個垂直路徑上，轉為您的右方。 同樣地，請按一下以變更平面設定的點。 請注意色彩分隔如何減少，並顯示在連接至平面的點上。 同樣地，在平面設定函數中使用點的速度。 此參數會針對物件的預期動作，提供 HoloLens 的提示。 使用此功能時，請務必瞭解使用方式，因為當您在某個點上使用速度時，另一個移動點會顯示較大的色彩分隔。 在設計您的應用程式時，請記住這點-對物件的動作具有一致的流程有助於防止出現成品。

### <a name="exercise-3"></a>練習3

再一次前往您的右方，直到您看到新的點設定。 在此情況下，距離中會有點，而一個點會在其前方進行。 按一下以變更平面設定的點，並在背面和移動點之間交替。 請注意，設定平面位置和螺旋式的速度會讓成品顯示在所有地方。

**提示**
* 讓您的平面設定邏輯保持簡單。 如您所見，您不需要複雜的平面設定演算法，就能獲得沉浸式體驗。 穩定平面只是拼圖的一部分。
* 可能的話，請一律在目標之間順暢地移動平面。 立即切換較遠的目標可能會以視覺化方式中斷場景。
* 請考慮在平面設定邏輯來鎖定特定目標的選項。 如此一來，您就可以視需要在物件上鎖定平面，例如標誌或標題畫面。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>軟體工程師 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>請參閱
* [MR Basics 100：開始使用 Unity](../unity/tutorials/holograms-100.md)
* [Unity 中的焦點](../unity/focus-point-in-unity.md)
* [全像投影穩定性](hologram-stability.md)
