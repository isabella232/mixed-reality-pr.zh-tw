---
title: README_Slate
description: MRTK 中的平板相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、平板、
ms.openlocfilehash: ac0c10a50ed3114150ede0988bf39c2c7696ea20
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682641"
---
# <a name="slate"></a>平板

![平板](Images/Slate/MRTK_Slate_Main.png)

[石板] 預製專案提供精簡的視窗樣式控制項，以顯示2D 內容，例如純文字或包含媒體的文章。 它提供了 grabbable 的標題列，以及 *追蹤* 和 *關閉* 功能。 您可以透過明確的手寫輸入來滾動內容視窗。

## <a name="how-to-use-a-slate-control"></a>如何使用平板控制項

[石板] 控制項是由下列元素所組成：

* **標題** 欄：平板最上層的整個標題列。
* **標題**：標題列左邊的標題區域。
* **按鈕**：標題列右側的按鈕區。
* **BackPlate**：蓋板的後端。
* **ContentQuad**：內容已指派為材質。 此範例使用範例材質 ' PanContent '。

<img src="Images/Slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structures">

## <a name="bounding-box"></a>週框方塊

一個石板控制項包含用來縮放和旋轉的周框方塊腳本。 如需周框方塊的詳細資訊，請參閱周 [框](README_BoundingBox.md) 方塊頁面。

<img src="Images/Slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>按鈕

標準的平板版提供兩個按鈕，作為標題列右上角的預設值：

* **跟隨我**：切換 orbital 的求解元件，讓 [石板] 物件跟隨在使用者後面。
* **關閉**：停用 [石板] 物件。

<img src="Images/Slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Buttons">

## <a name="scripts"></a>指令碼

一般而言， `NearInteractionTouchable.cs` 腳本必須附加至任何要接收觸控事件的物件 `IMixedRealityTouchHandler` 。

<img src="Images/Slate/MRTK_Slate_Scripts.png" alt="Scripts">

* `HandInteractionPan.cs` 此腳本會處理已表達的手輸入，以便在平板 *ContentQuad* 上接觸和移動內容。

* `HandInteractionPanZoom.cs`：除了移動流覽互動之外，此腳本也支援雙向縮放。

<img src="Images/Slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zoom">
