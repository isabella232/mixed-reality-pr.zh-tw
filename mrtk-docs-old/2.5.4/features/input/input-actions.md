---
title: InputActions
description: 在 MRTK 中建立輸入動作的檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、InputActions、
ms.openlocfilehash: 538dbc1b5e2e6de7af62d556144899f285048217
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685341"
---
# <a name="input-actions"></a>輸入動作

[**輸入動作**](input-actions.md) 是原始輸入的抽象概念，目的是要協助隔離應用程式邏輯與產生輸入的特定輸入來源。 例如，它可能很有用，例如，定義 *選取* 動作並將它對應至滑鼠左鍵、遊戲台中的按鈕，以及6個 DOF 控制器中的觸發程式。 然後，您可以讓應用程式邏輯接聽 *選取* 的輸入動作事件，而不需要知道可以產生的所有不同輸入。

## <a name="creating-an-input-action"></a>建立輸入動作

輸入動作是在 **輸入動作設定檔** 中設定，在混合現實工具組元件的 *輸入系統設定檔* 內、指定動作的名稱以及輸入的類型 (*軸條件約束* ，) 它可以對應到：

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

這些是 **軸條件約束** 最常使用的值：

軸條件約束 | Description
--- | ---
Digital | 開啟/關閉輸入，例如遊戲台或滑鼠中的二進位按鈕。
單一軸 | 單一軸將輸入與遊戲中的類比觸發程式相似。
雙軸 | 雙軸將輸入與操縱杆相似。
六 Dof | 以6個 DOF 控制器所產生的平移和旋轉進行3D 姿勢。

您可以在中找到完整清單 [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) 。

## <a name="mapping-input-to-actions"></a>將輸入對應至動作

您對應輸入和動作的方式取決於輸入來源的類型：

### <a name="controller-input"></a>控制器輸入

移至 [*輸入系統設定檔*] 下的 [**控制器輸入對應設定檔**]。 您會在這裡找到所有支援的控制器清單：

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

選取您要設定的專案，其中會出現一個對話方塊視窗與所有控制器輸入，讓您為每個控制器輸入設定動作：

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>語音輸入

在 **語音命令設定檔** 的 *輸入系統設定檔* 下，您可以找到目前定義的語音命令清單。 若要將其中一個對應至動作，只需在 [ *動作* ] 下拉式清單中選取它。

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>手勢輸入

*輸入系統設定檔* 底下的 **手勢設定檔** 包含所有已定義的手勢。 您可以在 [ *動作* ] 下拉式清單中選取每個動作，以將其對應至動作。

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>處理輸入動作

> [!WARNING]
> 目前只能使用本節所述的方法來處理 *數位* 類型的輸入動作。 針對其他動作類型，您必須改為直接處理對應輸入的事件。 例如，若要處理對應至控制器輸入的6個 DOF 動作，您必須搭配 [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) T = 使用 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 。

處理輸入動作最簡單的方式就是利用 [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) 腳本。 這可讓您定義您想要接聽的動作，並使用 Unity 事件回應動作開始和結束事件。

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

如果您想要更多控制，您可以 [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) 直接在腳本中執行介面。 如需透過處理常式介面處理事件的詳細資訊，請參閱 [**輸入事件**](input-events.md) 一節。

## <a name="examples"></a>範例

如需示範 `MRTK/Examples/Demos/Input/Scenes/InputActions` 如何建立動作、將其對應至控制器、語音和手勢輸入，以及用來在命令上旋轉物件的範例場景，請參閱。

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
