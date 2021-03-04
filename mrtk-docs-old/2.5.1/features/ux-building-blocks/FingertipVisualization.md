---
title: FingertipVisualization
description: MRTK 中的 FingerTip 視覺效果總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Fingertip
ms.openlocfilehash: 8f6630f46f2d1cf1681cd6ea68c70396eb69bc2a
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779830"
---
# <a name="fingertip-visualization"></a>Fingertip 視覺效果

![Fingertip 視覺效果主要](../images/fingertip/MRTK_FingertipVisualization_Main.png)

Fingertip affordance 可協助使用者辨識來自目標物件的距離。 「環形」圖形視覺效果會根據從 fingertip 到物件的距離來調整其大小。 Fingertip 視覺效果主要是由 (的 `FingerCursor` 資產/MRTK/SDK/Features/UX/Prefabs/cursor/FingerCursor. 預製專案)  (和腳本) 所控制，這會以 *預製專案* 的資料指標 PokePointer 來產生。 視覺效果的其他元件包括 *ProximityLight* 腳本和 *MixedRealityStandard* 著色器。

## <a name="how-to-use-the-fingertip-visualization"></a>如何使用 fingertip 視覺效果

根據預設，fingertip 視覺效果會在設定為產生 FingerCursor 的任何 Unity 場景中運作。 FingerCursor 的產生會出現在 *DefaultMixedRealityToolkitConfigurationProfile* 底下：

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*

概括而言，fingertip 視覺效果的運作方式是使用相近光線，在接受鄰近燈的任何鄰近表面上投影彩色漸層。 手指游標接著會尋找任何附近的互動介面（由父系決定 `IMixedRealityNearPointer(s)` ），以在手指移至表面時對齊手指環形。 手指的方法是使用 MixedRealityStandard 著色器的圓角屬性，動態地將手指環形動畫。

## <a name="example-scene"></a>範例場景

您可以在幾乎任何適用于已表達手的場景中找到 fingertip 的視覺效果範例，但在 [HandInteractionExample 場景](../example-scenes/HandInteractionExamples.md)中很明顯。

![Fingertip 視覺效果狀態](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>偵測器屬性

**FingerCursor** 許多手指指標屬性都是繼承自基底資料指標類別。 重要屬性包括在 MixedRealityStandard 著色器中驅動手指環形動畫的最遠/接近面邊界和寬度。 針對其他屬性，請將滑鼠停留在偵測器工具提示上。

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Finger Cursor Inspector">

**ProximityLight** 近亮光源設定會控制在表面接近或遠的光線外觀。 中央、中間和外部色彩會控制光線的漸層外觀，並且可以針對應用程式的色彩選擇區量身打造。 請注意，這些色彩是 HDR (高動態範圍) ，可讓使用者將接近度的光線調近一個以上的值。 針對其他屬性，請將滑鼠停留在偵測器工具提示上。

**MixedRealityStandard 著色器** MixedRealityStandard 著色器用於 MRTK 中的許多效果。 Fingertip 視覺效果的兩項設定是「近乎淡化」和「近亮」。 近乎淡化可讓物件在相機或光線接近時淡入/放大。 請務必核取 [淺色]，以允許鄰近燈來推動淡化 (而不是相機) 。 您可以反轉「淡化開始」和「淡化完成」的值，以反轉淡出的值。 針對您想要讓鄰近光線亮亮的任何表面，請檢查「近亮」。 針對其他屬性，請將滑鼠停留在偵測器工具提示上。

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Standerd Shader">
