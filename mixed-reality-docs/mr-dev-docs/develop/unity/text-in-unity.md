---
title: Unity 中的文字
description: 若要在 Unity 中顯示文字，您可以使用兩種類型的文字元件： UI 文字和3D 文字網格。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、控制項、字型、印刷樣式、ui、ux、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: dde8989998cf422c40ada927c0d8462cb4cd97b9
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489278"
---
# <a name="text-in-unity"></a>Unity 中的文字

文字是全像攝影應用程式中最重要的元件之一。 若要在 Unity 中顯示文字，有三種類型的文字元件可供您使用： UI 文字、3D 文字網格和文字網格 Pro。 根據預設，UI 文字和3D 文字網格會顯示為模糊且太大。 變更幾個變數會產生更清晰、品質較高的文字，並在 HoloLens 中提供可管理的大小。 使用 UI 文字和3D 文字網格元件時，您可以套用縮放比例來取得適當的維度，以達到更佳的轉譯品質。

![如何取得清晰且美觀的文字](images/hug-text-02-640px.png)<br>
*Unity 中的模糊預設文字*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>使用 Unity 的3D 文字 (文字網格) 和 UI 文字

Unity 假設所有新增至場景的新元素都是一個 Unity 單位，或100% 的轉換縮放比例。 一個 Unity 單位會在 HoloLens 上轉譯為約1個計量。 若是字型，3D TextMesh 的周框方塊預設會以大約1計量的高度來提供。

![使用 Unity 中的字型](images/640px-hug-text-03.png)<br>
*預設的 Unity 3D 文字 (文字網格) 佔用一個 Unity 單位，也就是1個計量*

<br>

大部分的視覺化設計工具會使用點來定義真實世界中的字型大小。 1計量中有大約 2835 (2，834.645666399962) 點。 根據指向1計量的點系統轉換，以及 Unity 的預設文字網格字型大小13，13的簡單數學運算（13）除以2835等於 0.0046 (0.004586111116 為精確) ，可提供良好的標準尺規來開始 (有些可能想要舍入至 0.005) 。 將文字物件或容器調整為這些值並不只允許在設計程式中轉換字型大小的1:1，也提供標準，因此您可以在整個體驗中維持一致性。

![調整 Unity 3D 文字和 UI 文字的值](images/Text_In_Unity_Measurements1.png)<br>
*調整 Unity 3D 文字和 UI 文字的值*

<br>

![具有優化值的 Unity 3D 文字網格](images/hug-text-05-1000px.png)<br>
*具有優化值的 Unity 3D 文字網格*

<br>

將 UI 或畫布型文字元素新增至場景時，大小差異仍會大於。 這兩種大小的差異大約是1000%，這會將以 UI 為基礎的文字元件的縮放因數帶到 0.00046 (0.0004586111116 為舍入值的精確) 或0.0005。

![具有優化值的 Unity UI 文字](images/hug-text-04-1000px.png)<br>
*具有優化值的 Unity UI 文字*

<br>

>[!NOTE]
>任何字型的預設值可能會受到該字型的材質大小或字型匯入 Unity 的影響。 這些測試是根據 Unity 中的預設 Arial 字型，還有另一個匯入的字型來執行。

## <a name="working-with-text-mesh-pro"></a>使用文字網格 Pro

您可以使用 Unity 的文字網格 Pro 來保護文字轉譯品質。 無論使用 [ [帶正負號的距離] 欄位 (.sdf) ](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 技術的距離為何，它都支援清晰的文字外框。 使用我們針對3D 文字網格和 UI 文字所使用的相同計算方法，我們可以找到適當的縮放比例值，以搭配傳統的印刷點使用。 因為大小為36的預設3D 文字網格 Pro 字型，其周框大小為 2.5 Unity 單位 (2.5 m) ，所以我們可以使用0.005 值來取得點大小。 UI 功能表下的文字網格 Pro，預設的周框大小為25個 Unity 單位 (25 m) 。 這可為我們提供0.0005 的調整值。

![調整 Unity 3D 文字和 UI 的值](images/Text_In_Unity_Measurements2.png)<br>
*調整 Unity 3D 文字和 UI 的值*

## <a name="recommended-text-size"></a>建議的文字大小

如您所見，我們在電腦或 (平板電腦上使用的類型大小，通常是在12–32pt 填補) 在兩個度量之間的距離，通常介於12到。 這取決於每個字型的特性，但在一般情況下，建議的最小觀賞角度和字型高度會根據我們的使用者研究研究，在0.35 °-0.4 °/12.21 13.97 mm 周圍。 這大約是 35-40 pt 和上面介紹的縮放比例。

針對在 0.45 m (45 cm) 的近距離互動，最小的可辨認字型的觀賞角度和高度是0.4 °-0.5 °/3.14 – 3.9 mm。 這大約是 9-12 pt 和上面介紹的縮放比例。

![近距離與遠距離互動範圍的互動範圍 ](images/typography-distance-1000px.jpg)
 *內容*

### <a name="the-minimum-legible-font-size"></a>最小清晰度的字型大小

| 距離 | 視角 | 文字高度 | 字型大小 |
|---------|---------|---------|---------|
| 45 cm (直接操作距離)  | 0.4 °-0.5 ° | 3.14 –3.9 分鐘 | 8.9 – 11.13 pt |
| 2分鐘 | 0.35 °-0.4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>方便閱讀的字型大小

| 距離 | 視角 | 文字高度 | 字型大小 |
|---------|---------|---------|---------|
| 45 cm (直接操作距離)  | 0.65 °-0.8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2分鐘 | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |

Segoe UI (Windows) 的預設字型在大部分情況下都能順利運作。 不過，請避免使用較小的淺色或半淺色字型系列，因為精簡型垂直筆觸會震動，而且會降低可讀性。 具有足夠筆觸粗細的新式字型可正常運作。 例如，Helvetica 和 Arial 外觀美觀，而且在 HoloLens 中會使用一般或粗體權數來辨認。

![視圖角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *觀賞距離、角度和文字高度*

## <a name="text-with-mixed-reality-toolkit-v2"></a>具有混合現實工具組 v2 的文字

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>具有適當維度的清晰文字轉譯品質

根據這些調整因素，我們 [使用了 UI 文字和3D 文字網格來建立文字 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)。 開發人員可以使用這些 prefabs 來取得清晰的文字和一致的字型大小。

![具有適當維度的清晰文字轉譯品質](images/hug-text-06-1000px.png)<br>
*具有適當維度的清晰文字轉譯品質*

### <a name="shader-with-occlusion-support"></a>具有遮蔽支援的著色器

Unity 的預設字型材質不支援遮蔽。 因此，根據預設，您會看到物件後面的文字。 我們已包含 [支援遮蔽的簡單著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader)。 下圖顯示具有預設字型材質 (左) 的文字，以及具有適當遮蔽 (右邊) 的文字。

![具有遮蔽支援的著色器](images/hug-text-07-1000px.png)<br>
*具有遮蔽支援的著色器*

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [語音輸入](voice-input-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱

* [MRTK 中的文字預製專案](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [印刷樣式](../../design/typography.md)
