---
title: 平板
description: MRTK 中的平板相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、平板、
ms.openlocfilehash: 0c75ddd46a1b89ca992ac1069f10f32ae86efd85
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779661"
---
# <a name="slate"></a>平板

![平板](../images/slate/MRTK_Slate_Main.png)

[石板] 預製專案提供精簡的視窗樣式控制項，以顯示2D 內容，例如純文字或包含媒體的文章。 它提供了 grabbable 的標題列，以及 *追蹤* 和 *關閉* 功能。 您可以透過明確的手寫輸入來滾動內容視窗。

## <a name="how-to-use-a-slate-control"></a>如何使用平板控制項

[石板] 控制項是由下列元素所組成：

* **標題** 欄：平板最上層的整個標題列。
* **標題**：標題列左邊的標題區域。
* **按鈕**：標題列右側的按鈕區。
* **BackPlate**：蓋板的後端。
* **ContentQuad**：內容已指派為材質。 此範例使用範例材質 ' PanContent '。

<img src="../images/slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Strucutures">

## <a name="bounds-control"></a>界限控制項

石板控制項包含用於調整和旋轉的界限控制腳本。 如需界限控制的詳細資訊，請參閱 [界限控制](BoundsControl.md) 頁面。

<img src="../images/slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>按鈕

標準的平板版提供兩個按鈕，作為標題列右上角的預設值：

* **跟隨我**：切換 orbital 的求解元件，讓 [石板] 物件跟隨在使用者後面。
* **關閉**：停用 [石板] 物件。

<img src="../images/slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Buttons">

## <a name="scripts"></a>指令碼

一般而言， `NearInteractionTouchable.cs` 腳本必須附加至任何要接收觸控事件的物件 `IMixedRealityTouchHandler` 。

<img src="../images/slate/MRTK_Slate_Scripts.png" alt="Slate Scripts">

* `HandInteractionPan.cs` 此腳本會處理已表達的手輸入，以便在平板 *ContentQuad* 上接觸和移動內容。

* `HandInteractionPanZoom.cs`：除了移動流覽互動之外，此腳本也支援雙向縮放。

<img src="../images/slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate PanZoom">
