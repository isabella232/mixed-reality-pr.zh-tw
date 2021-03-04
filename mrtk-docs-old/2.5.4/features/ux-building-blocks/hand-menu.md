---
title: HandMenu
description: MRTK 中的手邊功能表範例場景
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、HandMenu、
ms.openlocfilehash: ed4226936fc2af8d5e287f607291670fa9a5295b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779540"
---
# <a name="hand-menu"></a>手部功能表

![手形功能表 UX 範例](../images/solver/MRTK_UX_HandMenu.png)

手形功能表可讓使用者快速地為常用的函式顯示手動連接的 UI。 若要在與其他物件互動時防止啟用錯誤，請使用右功能表提供「需要平面」和「使用注視啟用」之類的選項。 建議使用這些選項來避免不必要的啟用。

## <a name="hand-menu-examples"></a>手形功能表範例

**HandMenuExamples。 unity** 場景位於 ``MRTK/Examples/Demos/HandTracking/Scenes`` 資料夾底下。 當該場景正在執行時，只會啟動目前選取的功能表類型。
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

您可以在 [資料夾] 底下找到這些功能表 prefabs ``MRTK/Examples/Demos/HandTracking/Prefabs`` 。

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop 和 HandMenu_Medium_HideOnHandDrop

這兩個範例只會啟動和停用 MenuContent 物件，以顯示和隱藏 **OnFirstHandDetected ()** 和 **OnLastHandLost ()** 事件上的功能表。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

針對需要較長互動時間的更複雜功能表，建議您在功能表上進行世界鎖定。 在此範例中，除了啟動和停用 **OnFirstHandDetected ()** 上的 MenuContent，以及 **OnLastHandLost ()** 事件之外，使用者還可以抓取並拉出功能表。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

Backplate `ManipulationHandler` 可讓它 grabbable 和可移動。 **在操作啟動** 事件時，SolverHandler 會停用 **UpdateSolvers** ，以世界鎖定功能表。 此外，它也會顯示 [ **關閉] 按鈕** ，讓使用者在工作完成時關閉功能表。 **在操作結束事件時** ，它會呼叫 **HandConstraintPalmUp** ，以允許使用者藉由產生並查看掌上，讓功能表回到手邊。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

[**關閉**] 按鈕會重新開機 **SolverHandler，UpdateSolvers** 並隱藏 **MenuContent**。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

此範例類似于 HandMenu_Large_WorldLock_On_GrabAndPull。 唯一的不同之處在于功能表會自動放在手上。 這是藉由單純不要隱藏 MenuContent on **OnLastHandLost ()** 事件來完成。 抓取 & 提取行為與 HandMenu_Large_WorldLock_On_GrabAndPull 範例相同。

## <a name="scripts"></a>指令碼

此 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 行為提供的規劃求解會將追蹤的物件限制為可安全的 (，例如，手動 UI、功能表等) 。 安全區域會被視為不會與手相交的區域。 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint)另外也包含了呼叫的衍生類別 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) ，以示範當掌上有使用者時啟動規劃求解追蹤物件的常見行為。

如需其他檔，請參閱每個屬性可用的工具提示 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 。 以下會更詳細地定義幾個屬性。

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **安全區域**：安全區域會指定要限制內容的位置。 建議將內容放在 Ulnar 端，以避免與手邊和改進的互動品質重迭。 安全區域的計算方式是將手投射到平面的平面上，並以圍繞手的周框方塊 raycasting。 安全區域的定義可搭配使用， [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 但也適用于其他控制器類型。 建議您探索每個安全區域代表不同控制器類型的內容。

* 在 **面對相機之前接手** 使用這個活動時，將會在功能表充分配合臉部的位置之後，進行規劃，並在該時間點面對攝影機。 這項作業的運作方式是將 HandConstraintSolver 中的 SolverRotationBehavior，從 LookAtTrackedObject 變更為 LookAtMainCamera，因為 GazeAlignment 角度與規劃求解會有所不同。

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **啟用事件**：目前 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 觸發四項啟用事件。 這些事件可用於許多不同的組合以建立獨特 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 的行為，請參閱下的 HandBasedMenuExample 場景， `MRTK/Examples/Demos/HandTracking/Scenes/` 以取得這些行為的範例。

  * *OnHandActivate*：當手符合 IsHandActive 方法時觸發。
  * *OnHandDeactivate*：當不再滿足 IsHandActive 方法時，就會觸發。
  * *OnFirstHandDetected*：當手動追蹤狀態從沒有實際的視圖變更為第一次觀看時，就會發生此情況。
  * *OnLastHandLost*：當手動追蹤狀態從至少一個手上變更為沒有實際畫面時，就會發生此情況。

* **規劃求解啟用/停用邏輯**：目前針對啟用和停用邏輯的建議 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 是透過使用 SolverHandler 的 UpdateSolver 值來執行，而不是停用/啟用物件。 您可以透過在附加功能表的 ManipulationHandler 「OnManipulationStarted/結束」事件之後所觸發的以編輯器為基礎的勾點，在範例場景中看到這種情況。

  * *停止手形條件約束邏輯*：嘗試設定手限制物件以停止 (以及不要執行啟用/停用邏輯) 時，請將 UpdateSolver 設定為 False，而不是停用 HandConstraintPalmUp。
    * 如果您想要啟用以注視為基礎的 (或甚至是非等式的) 重新附加邏輯，則會接著呼叫 HandConstraintPalmUp. StartWorldLockReattachCheckCoroutine () 函數。 這會觸發協同程式，然後繼續檢查是否符合 "IsValidController" 準則，並在 (或停用物件時將 UpdateSolver 設定為 True) 
  * *啟動手形條件約束邏輯*：當您嘗試設定手限制物件，使其根據是否符合啟動準則)  (，請將 SolverHandler 的 UpdateSolver 設定為 true。

* 重新 **附加邏輯**：目前 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 可以自動將目標物件重新附加至追蹤點，而不論 SolverHandler 的 UpdateSolver 是否為 True。 這是透過呼叫 HandConstraintPalmUp 的 StartWorldLockReattachCheckCoroutine () 函式來完成 (，在這種情況下，會將 SolverHandler 的 UpdateSolver 有效地設定為 False) 。

## <a name="see-also"></a>另請參閱

* [按鈕](button.md)
* [近端功能表](near-menu.md)
