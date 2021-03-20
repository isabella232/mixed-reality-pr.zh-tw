---
title: NearMenu_README
description: 總覽 MRTK 中的接近功能表類型
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、近端功能表、
ms.openlocfilehash: 1398a65275269287e2ada6a922afacb9e37f401e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682651"
---
# <a name="near-menu"></a>近端功能表

![近端功能表](Images/NearMenu/MRTK_UX_NearMenu.png)

近端功能表是 UX 控制項，可提供按鈕或其他 UI 元件的集合。 它是以使用者的主體為中心，而且隨時都可以輕鬆存取。 由於它與使用者鬆散結合，因此不會干擾使用者與目標內容的互動。 使用者可以使用 [釘選] 按鈕，以世界鎖定/解除鎖定功能表。 您可以抓取功能表，並將其置於特定位置。

## <a name="interaction-behavior"></a>互動行為

- **加** 上標籤：功能表會跟隨您，並保留在使用者的 30 60cm 範圍內，以進行近乎互動。
- **Pin**：您可以使用 [釘選] 按鈕，以世界鎖定和釋出功能表。
- **抓取和移動**：功能表一律為 grabbable 和可移動。 無論先前的狀態為何，在抓取和釋放時，功能表都會釘選 (世界鎖定的) 。 Grabbable 區域有視覺提示。 它們會顯示在手上。

<img src="Images/NearMenu/MRTK_UX_NearMenu_Grab.png" alt="Grab near menu">

## <a name="prefabs"></a>Prefabs

近端功能表 prefabs 的設計目的是要示範如何使用 MRTK 的各種元件來建立功能表以進行近乎互動。

- **NearMenu2x4. 預製專案**
- **NearMenu3x1. 預製專案**
- **NearMenu3x2. 預製專案**
- **NearMenu3x3. 預製專案**
- **NearMenu4x1. 預製專案**
- **NearMenu4x2. 預製專案**

## <a name="example-scene"></a>範例場景

您可以在場景中找到接近功能表 prefabs 的範例 `NearMenuExamples` 。

<img src="Images/NearMenu/MRTK_UX_NearMenu_Examples.png" alt="Near menu Examples">

## <a name="structure"></a>結構

附近的功能表 prefabs 會使用下列 MRTK 元件來進行。

- [**PressableButtonHoloLens2**](README_Button.md) 預製專案
- [**方格物件集合**](README_ObjectCollection.md)：方格中的多個按鈕版面配置
- [**操作處理常式**](README_ManipulationHandler.md)：抓取並移動功能表
- [**RadialView 規劃**](README_Solver.md)：追蹤 (標記-沿著) 的行為

![鄰近功能表預製專案](Images/NearMenu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>如何自訂

**1. 新增/移除按鈕**

在 [物件] 下 `ButtonCollection` ，[加入] 或 [移除] 按鈕。  
<img src="Images/NearMenu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu custom 0">

**2. 更新方格物件集合**

`Update Collection`在物件的偵測器中，按一下按鈕 `ButtonCollection` 。 它會更新格線版面配置。  
<img src="Images/NearMenu/MRTK_UX_NearMenu_Custom1.png" alt="Near menu custom 1">

您可以使用方格物件集合的屬性來設定資料列的數目 `Rows` 。  
<img src="Images/NearMenu/MRTK_UX_NearMenu_Custom2.png" alt="Near menu custom 2">

**3. 調整 backplate 大小**

調整 [物件] 下的大小 `Quad` `Backplate` 。 Backplate 的寬度和高度應該是 `0.032 * [Number of the buttons + 1]` 。 例如，如果您有 3 x 2 個按鈕，則 backplate 的寬度為， `0.032 * 4` 而高度為 `0.032 * 3` 。 您可以直接將此運算式放入 Unity 的欄位中。  
<img src="Images/NearMenu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="near menu custom 3">

- HoloLens 2 按鈕的預設大小為 3.2 x 3.2 cm (0.032 m) 

## <a name="see-also"></a>另請參閱

- [**按鈕**](README_Button.md)
- [**周框方塊**](README_BoundingBox.md)
- [**滑桿**](README_Sliders.md)
- [**方格物件集合**](README_ObjectCollection.md)
- [**操作處理常式**](README_ManipulationHandler.md)
- [**RadialView 規劃**](README_Solver.md)
