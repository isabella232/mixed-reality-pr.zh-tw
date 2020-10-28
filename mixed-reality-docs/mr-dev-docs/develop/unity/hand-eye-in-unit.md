---
title: Unity 中的明確和眼睛追蹤
description: 有兩種主要方式可以在您的「Unity」、「手手勢」和「動作控制器」中採取動作。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手勢、動作控制器、unity、注視、輸入
ms.openlocfilehash: b184cf1d9e6f35e3750015b51374058df79ed19d
ms.sourcegitcommit: 24d96bf3bb9a3143445e018195edae99d91684c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92683234"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity 中的明確和眼睛追蹤

HoloLens 2 引進了一些令人興奮的新功能，例如明確的手和眼睛追蹤。

利用 Unity 的新功能，最簡單的方式是透過 MRTK v2。 另外還有一些範例場景可協助您開始使用。

* [開始在 MRTK v2 中使用明確的手](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [開始在 MRTK v2 中使用眼睛追蹤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>在 MRTK v2 中支援手、眼睛和其他專案的組建區塊

MRTK v2 提供一組 UI 控制項和建立區塊，可協助您加速開發。

|  [ ![ 按鈕](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)[按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | 周[ ![ 框](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)方塊周[框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)方塊 | [ ![ 操作處理常式](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)[操作處理常式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| 按鈕控制項，可支援各種輸入方法，包括 HoloLens2's 的明確表述 | 在3D 空間中操作物件的標準 UI | 以一或兩個手中操作物件的腳本 |
|  [ ![ 平板](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html)[平板](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [ ![ 系統鍵盤](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html)[系統鍵盤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [ ![ 互動](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)[互動](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| 2D 樣式平面，支援以已明確表達的手寫輸入進行滾動 | 在 Unity 中使用系統鍵盤的範例腳本  | 使用視覺狀態和主題支援讓物件互動的腳本 |
|  [ ![ 規劃](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)求解[規劃](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [ ![ 物件集合](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)[物件集合](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [ ![ 工具](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html)提示[工具提示](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| 各種物件定位行為，例如標記-沿著標記、主體鎖定、常數視圖大小和表面磁性 | 用於在三維圖形中設定物件陣列的腳本 | 具有彈性錨點/pivot 系統的注釋 UI，可用來標記動作控制器和物件。 |
|  [ ![ 應用程式行](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)[應用程式行](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [ ![ 指標](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)[指標](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) | [ ![ Fingertip 視覺效果](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) [Fingertip 視覺效果](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| 周框方塊手動啟用的 UI | 瞭解各種類型的指標 | Fingertip 上的視覺效果 affordance，可改善直接互動的信賴度 |
|  [ ![ 眼睛追蹤：目標選擇](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html)[眼睛追蹤：目標選取範圍](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [ ![ 眼睛追蹤：導覽](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html)[眼睛追蹤：導覽](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [ ![ 眼睛追蹤：熱度圖](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html)[視覺追蹤：熱度圖](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| 結合眼睛、語音和手輸入，以快速且輕鬆地在場景中選取全像影像 | 瞭解如何根據您要查看的內容，自動滾動文字或流暢縮放至焦點內容| 記錄、載入和視覺化使用者在您的應用程式中查看的範例 |

## <a name="example-scenes"></a>範例場景

探索 MRTK 在 [此範例場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)中的各種互動和 UI 控制項類型。

您可以在 [資產/MixedRealityToolkit] 底下的 [ [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity) 組] GitHub 中找到其他範例場景： [ **範例/示範** ] 資料夾。

[![範例場景](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unity 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [空間對應](spatial-mapping-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱

* [眼動式互動](../../design/eye-gaze-interaction.md)
* [HoloLens 2 的眼球追蹤](../../design/eye-tracking.md)
* [目光和行動](../../design/gaze-and-commit.md)
* [手 - 直接操作](../../design/direct-manipulation.md)
* [手 - 手勢](../../design/gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](../../design/point-and-commit.md)
* [本能互動](../../design/interaction-fundamentals.md)
* [運動控制器](../../design/motion-controllers.md)
* [UnityEngine. XR。輸入](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
