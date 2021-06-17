---
title: Unity 中的明確和眼睛追蹤
description: 深入瞭解在 Unity、手勢手勢和移動控制器上採取動作的兩個主要方式。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手勢、移動控制器、unity、注視、輸入、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: 2daa02a0681fe4f3da24fa32379e10877750af7e
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110221"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity 中的明確和眼睛追蹤

HoloLens 2 引進了一些令人興奮的新功能，例如明確的手和眼睛追蹤。

利用 Unity 的新功能，最簡單的方式是透過 MRTK。 另外還有一些範例場景可協助您開始使用。

* [開始在 MRTK 中使用明確的手](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [開始在 MRTK 中使用眼睛追蹤](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>在 MRTK 中支援手、眼睛和其他專案的建立組塊

MRTK v2 提供一組 UI 控制項和建立區塊，可協助您加速開發。

|  [ ![ 按鈕](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)[按鈕](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | 周[ ![ 框](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)方塊周[框](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)方塊 | [ ![ 操作處理常式](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler)[操作處理常式](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| 按鈕控制項，可支援各種輸入方法，包括 HoloLens2's 的明確表述 | 在3D 空間中操作物件的標準 UI | 以一或兩個手中操作物件的腳本 |
|  [ ![ 平板](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate)[平板](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [ ![ 系統鍵盤](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard)[系統鍵盤](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [ ![ 互動](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)[互動](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| 2D 樣式平面，可支援以明確方式輸入的滾動 | 在 Unity 中使用系統鍵盤的範例腳本  | 使用視覺狀態和主題支援讓物件互動的腳本 |
|  [ ![ 規劃](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver)求解[規劃](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [ ![ 物件集合](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)[物件集合](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [ ![ 工具](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip)提示[工具提示](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| 各種物件定位行為，例如標記-沿著標記、主體鎖定、常數視圖大小和表面磁性 | 用於在三維圖形中設定物件陣列的腳本 | 具有彈性錨點/pivot 系統的注釋 UI，可用來標記動作控制器和物件。 |
|  [ ![ 應用程式行](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar)[應用程式行](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [ ![ 指標](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers)[指標](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [ ![ Fingertip 視覺效果](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [Fingertip 視覺效果](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| 周框方塊手動啟用的 UI | 瞭解各種類型的指標 | Fingertip 上的視覺效果 affordance，可改善直接互動的信賴度 |
|  [ ![ 眼睛追蹤：目標選擇](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection)[眼睛追蹤：目標選取範圍](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [ ![ 眼睛追蹤：導覽](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation)[眼睛追蹤：導覽](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| 結合眼睛、語音和手邊輸入，以快速且輕鬆地在場景中選取全像影像 | 瞭解如何根據您要查看的內容，自動滾動文字或放大焦點內容| 記錄、載入和視覺化使用者在您的應用程式中查看的範例 |

## <a name="example-scenes"></a>範例場景

探索 MRTK 在 [此範例場景](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)中的各種互動和 UI 控制項類型。

您可以在 [資產/MixedRealityToolkit] 底下的 [ [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity) 組] GitHub 中找到其他範例場景： [ **範例/示範**] 資料夾。

[![範例場景](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。 接下來，您可以繼續進行下一個建置組塊：

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