---
title: InputSimulationServices
description: MRTK 中輸入模擬服務的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: b36af476c3b7e257ee132e0e70c9aecf721a95b1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781100"
---
# <a name="input-simulation-service"></a>輸入模擬服務

輸入模擬服務會模擬可能無法在 Unity 編輯器中使用的裝置和平臺行為。 範例包括：

* HoloLens 或 VR 裝置標頭追蹤
* HoloLens 手勢
* HoloLens 2 已明確追蹤
* HoloLens 2 目視追蹤

使用者可以在執行時間使用傳統鍵盤和滑鼠組合來控制模擬的裝置。 這種方法可讓您在 Unity 編輯器中測試互動，而不需要先部署到裝置。

> [!WARNING]
> 使用 Unity 的 XR 全像 > 模擬模式 = 「在編輯器中模擬」時，這無法運作。 Unity 的編輯器內模擬將從 MRTK 的輸入模擬中取得控制權。 若要使用 MRTK 輸入模擬服務，您必須將 XR 全像模擬模式設定為模擬模式 = *"None"*

## <a name="enabling-the-input-simulation-service"></a>啟用輸入模擬服務

在 MRTK 隨附的設定檔中，預設會啟用輸入模擬。

但輸入模擬是選擇性的 [混合現實服務](../../out-of-scope/MixedRealityServices.md) ，而且可以在 [輸入系統設定檔](../Input/InputProviders.md)中移除為數據提供者。

在輸入系統資料提供者設定下，可以使用下列設定輸入模擬服務。

* **類型** 必須是 *MixedReality。輸入 > InputSimulationService*。
* 根據預設，**支援的平臺 (s)** 包含所有 *編輯器* 平臺，因為服務使用鍵盤和滑鼠輸入。

> [!NOTE]
> 輸入模擬服務可用於其他平臺端點（例如獨立式），方法是變更 **支援的平臺 (s)** 屬性，以包含所需的目標。
> ![輸入模擬支援的平臺](../Images/InputSimulation/InputSimulationSupportedPlatforms.gif)

## <a name="input-simulation-tools-window"></a>輸入模擬工具視窗

從 **混合現實** 工具組  >  **公用程式**  >  **輸入模擬** 功能表啟用輸入模擬工具視窗。 此視窗可讓您存取在播放模式期間的輸入模擬狀態。

## <a name="viewport-buttons"></a>視口按鈕

在 [指標] **預製專案** 下的輸入模擬設定檔中，可以指定用於控制基本放置之編輯器中按鈕的預製專案。 這是選擇性的公用程式，可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中存取相同的功能。

> [!NOTE]
> 依預設會停用視口指標，因為它們目前有時可能會干擾 Unity UI 互動。 請參閱問題 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)。 若要啟用，請將 InputSimulationIndicators 預製專案新增至指標 **預製專案**。

手圖示會顯示模擬手的狀態：

* ![未追蹤的手圖示](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Untracked.png) 手中沒有追蹤。 按一下以啟用手。
* ![追蹤的手形圖示](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Tracked.png "追蹤的手形圖示") 這會受到追蹤，但不是由使用者控制。 按一下以隱藏手。
* ![控制的手圖示](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Controlled.png "控制的手圖示") 手由使用者追蹤及控制。 按一下以隱藏手。
* ![重設手形圖示](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Reset.png "重設手形圖示") 按一下可將手重設為預設位置。

## <a name="camera-control"></a>攝影機控制項

輸入模擬服務可以模擬前端移動。

### <a name="rotating-the-camera"></a>旋轉相機

1. 將滑鼠停留在 [視口編輯器] 視窗上。
    *如果按鈕按下無法運作，您可能需要按一下視窗，以提供它的輸入焦點。*
1. 按住 **滑鼠 [搜尋] 按鈕** (預設：) 滑鼠右鍵。
1. 將滑鼠移至 [區] 視窗以旋轉相機。
1. 使用滾輪來圍繞視圖方向來旋轉相機。

您可以藉由變更輸入模擬設定檔中的 **滑鼠外觀速度** 設定，來設定相機旋轉速度。

或者，您也可以使用 [**外觀水準** / **外觀垂直** 軸]，將相機 (預設：遊戲控制器的右操縱杆) 。

### <a name="moving-the-camera"></a>移動相機

使用 **移動水準** / **移動垂直** 軸將相機移動 (預設： WASD 鍵或遊戲控制器離開操縱杆) 。

您也可以在 [工具] 視窗中明確設定相機位置和旋轉角度。 您可以使用 [ **重設** ] 按鈕，將相機重設為其預設值。

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

## <a name="hand-simulation"></a>手上模擬

輸入模擬支援模擬的裝置。 這些虛擬手可以與任何支援一般裝置的物件互動，例如按鈕或 grabbable 物件。

### <a name="hand-simulation-mode"></a>手動模擬模式

在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中，[ **手動模擬模式** ] 設定會在兩個不同的輸入模型之間切換。 您也可以在輸入模擬設定檔中設定預設模式。

* 明確表達的 *手：模擬* 具有聯合位置資料的全向裝置。

   模擬 HoloLens 2 互動模型。

   以確切定位或使用觸控為依據的互動，可在此模式中模擬。

* *手勢*：利用點擊和基本手勢模擬簡化的模型。

   模擬 [HoloLens 互動模型](https://docs.microsoft.com/windows/mixed-reality/gestures)。

   焦點是使用注視指標來控制。 「 *攻* 點」手勢用來與按鈕互動。

### <a name="controlling-hand-movement"></a>控制手間移動

按住 **左邊/右邊的 Control 鍵** (預設：左邊的左 *移* 和右邊的 *空格*) ，以取得任一手勢的控制權。 當按下操作鍵時，該手將會出現在區中。 釋放操作金鑰後，就會在短 **手隱藏 Timeout** 之後消失。

您可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中永久切換，或按下 **切換左/右邊鍵** (預設： *T* 代表左邊， *Y* 表示右邊的) 。 再按一次切換鍵，以再次隱藏手。

滑鼠移動會將手移至 [view] 平面。 您可以使用 **滑鼠滾輪**，更進一步或更靠近相機移動手。

若要使用滑鼠旋轉手，請將 **左/右邊的控制項按鍵** (*左移* 或 *空格*) *，然後* 將滑鼠 **旋轉按鈕** (預設值： *ctrl* 鍵) 然後移動滑鼠以旋轉手。 您可以藉由變更輸入模擬設定檔中的 **滑鼠右鍵旋轉速度** 設定來設定手旋轉速度。

所有放置也都可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中變更，包括重設為預設值。

### <a name="additional-profile-settings"></a>其他設定檔設定

* **右深度乘數** 控制滑鼠滾輪深度移動的敏感度。 較大的數位會加速縮放。
* [**預設距離**] 是從相機手上的初始距離。 按一下 [ **重設** ] 按鈕也會將手放在這個距離。
* **手抖動量** 會將隨機的動作新增至手中。 這項功能可用來模擬裝置上不正確的手追蹤，並確保互動適用于雜訊的輸入。

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="hand-gestures"></a>手勢

捏合、抓取、刺探等手勢也可以模擬。

1. 使用 **左側/右邊的控制項鍵** (*左移* 或 *空格*) 來啟用手形控制

   或者，使用切換鍵 (*T* 或 *Y*) 來切換實際操作。

2. 在操作時，按住滑鼠按鍵以執行手勢手勢。

您可以對應每個滑鼠按鍵，使用 *左/中/右滑鼠右鍵手勢* 設定，將手圖形轉換成不同的手勢。 當未按下任何按鈕時， *預設手勢* 是手的形狀。

> [!NOTE]
> 縮小 *手勢是* 唯一執行「選取」動作的手勢。

### <a name="one-hand-manipulation"></a>單次操作

1. 按住 **左邊/右邊的控制項鍵** (*左移* 或 *空格*) 
2. 物件上的點
3. 按住滑鼠按鍵以縮小
4. 使用您的滑鼠移動物件
5. 放開滑鼠按鍵以停止互動

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="two-hand-manipulation"></a>雙手勢操作

若要同時以兩種方式操作物件，建議使用持續性手動模式。

1. 按下切換鍵 (*T/Y*) 來切換。
1. 一次處理一個手勢：
    1. 按住 **空格鍵** 以控制右手邊
    1. 將手移至您要抓取物件的位置
    1. 按下 **滑鼠左鍵** 可啟動 *縮小手勢。* 在持續性模式中，當您放開滑鼠按鍵時，手勢將保持作用中狀態。
1. 以另一種方式重複此程式，在第二個位置抓取相同的物件。
1. 現在這兩個手都會抓取相同的物件，您可以將其中一個物件移至兩個執行中的操作。

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>GGV (注視、手勢和語音) 互動

根據預設，GGV 互動會在編輯器中啟用，但場景中不會有明確的手。

1. 旋轉相機以指向互動物件上的注視游標 (滑鼠右鍵) 
1. 按一下並按住 **滑鼠** 左鍵以進行互動
1. 再次旋轉相機以操作物件

您可以切換輸入模擬設定檔內的 [ *已啟用手動可用輸入* ] 選項來關閉此功能。

此外，您可以使用模擬的手 GGV 互動

1. 藉由將 **手動模擬模式** 切換至 [輸入模擬設定檔](#enabling-the-input-simulation-service)中的 *手勢* 來啟用 GGV 模擬
1. 旋轉相機以指向互動物件上的注視游標 (滑鼠右鍵) 
1. 按住 **空格鍵** 以控制右手邊
1. 按一下並按住 **滑鼠** 左鍵以進行互動
1. 使用您的滑鼠移動物件
1. 放開滑鼠按鍵以停止互動

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="eye-tracking"></a>眼球追蹤

您可以藉由檢查 [輸入模擬設定檔](#enabling-the-input-simulation-service)中的 [**模擬眼睛位置**] 選項來啟用 [眼睛追蹤模擬](../EyeTracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor)。 這不應該與 GGV 的樣式互動一起使用 (因此，請確定 *已將 [* **手動模擬模式]** 設定為 [已) ]。

## <a name="see-also"></a>另請參閱

* [輸入系統設定檔](../Input/InputProviders.md)。
