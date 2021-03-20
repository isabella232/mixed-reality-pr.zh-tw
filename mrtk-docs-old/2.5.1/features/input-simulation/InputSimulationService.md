---
title: InputSimulationServices
description: MRTK 中輸入模擬服務的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: a2ff5e30db2d4c8e7d36dcf7faa3297b50f38fdc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693945"
---
# <a name="input-simulation-service"></a>輸入模擬服務

輸入模擬服務會模擬可能無法在 Unity 編輯器中使用的裝置和平臺行為。 範例包括：

* HoloLens 或 VR 裝置標頭追蹤
* HoloLens 手勢
* HoloLens 2 明確的手追蹤
* HoloLens 2 眼追蹤
* VR 裝置控制器

使用者可以在執行時間使用傳統鍵盤和滑鼠組合來控制模擬的裝置。 這種方法可讓您在 Unity 編輯器中測試互動，而不需要先部署到裝置。

> [!WARNING]
> 使用 Unity 的 XR 全像 > 模擬模式 = 「在編輯器中模擬」時，這無法運作。 Unity 的編輯器內模擬將從 MRTK 的輸入模擬中取得控制權。 若要使用 MRTK 輸入模擬服務，您必須將 XR 全像模擬模式設定為模擬模式 = *"None"*

## <a name="enabling-the-input-simulation-service"></a>啟用輸入模擬服務

在 MRTK 隨附的設定檔中，預設會啟用輸入模擬。

但輸入模擬是選擇性的 [混合現實服務](../../architecture/MixedRealityServices.md) ，而且可以在 [輸入系統設定檔](../input/InputProviders.md)中移除為數據提供者。

在輸入系統資料提供者設定下，可以使用下列設定輸入模擬服務。

* **類型** 必須是 *MixedReality。輸入 > InputSimulationService*。
* 根據預設，**支援的平臺 (s)** 包含所有 *編輯器* 平臺，因為服務使用鍵盤和滑鼠輸入。

> [!NOTE]
> 輸入模擬服務可用於其他平臺端點（例如獨立式），方法是變更 **支援的平臺 (s)** 屬性，以包含所需的目標。
> ![輸入模擬支援的平臺](../images/input-simulation/InputSimulationSupportedPlatforms.gif)

## <a name="input-simulation-tools-window"></a>輸入模擬工具視窗

從 **混合現實** 工具組  >  **公用程式**  >  **輸入模擬** 功能表啟用輸入模擬工具視窗。 此視窗可讓您存取在播放模式期間的輸入模擬狀態。

## <a name="viewport-buttons"></a>視口按鈕

在 [指標] **預製專案** 下的輸入模擬設定檔中，可以指定用於控制基本放置之編輯器中按鈕的預製專案。 這是選擇性的公用程式，可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中存取相同的功能。

> [!NOTE]
> 依預設會停用視口指標，因為它們目前有時可能會干擾 Unity UI 互動。 請參閱問題 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)。 若要啟用，請將 InputSimulationIndicators 預製專案新增至指標 **預製專案**。

手圖示會顯示模擬手的狀態：

* ![未追蹤的手圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) 手中沒有追蹤。 按一下以啟用手。
* ![追蹤的手形圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "追蹤的手形圖示") 這會受到追蹤，但不是由使用者控制。 按一下以隱藏手。
* ![控制的手圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "控制的手圖示") 手由使用者追蹤及控制。 按一下以隱藏手。
* ![重設手形圖示](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "重設手形圖示") 按一下可將手重設為預設位置。

## <a name="in-editor-input-simulation-cheat-sheet"></a>在編輯器中輸入模擬功能提要

在 HandInteractionExamples 場景中按左 Ctrl + H，以顯示具有輸入模擬控制項的提要表。

![輸入模擬功能提要](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

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

## <a name="controller-simulation"></a>控制器模擬

輸入模擬支援模擬控制器裝置 (亦即移動控制器和手) 。 這些虛擬控制器可以與任何支援一般控制器的物件互動，例如按鈕或 grabbable 物件。

### <a name="controller-simulation-mode"></a>控制器模擬模式

在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中， **預設控制器模擬模式** 設定會在三個不同的輸入模型之間切換。 您也可以在輸入模擬設定檔中設定此預設模式。

* 明確表達的 *手：模擬* 具有聯合位置資料的全向裝置。

   模擬 HoloLens 2 互動模型。

   以確切定位或使用觸控為依據的互動，可在此模式中模擬。

* *手手勢*：利用點擊和基本手勢模擬簡化的模型。

   模擬 [HoloLens 互動模型](https://docs.microsoft.com/windows/mixed-reality/gestures)。

   焦點是使用注視指標來控制。 「 *攻* 點」手勢用來與按鈕互動。

* *移動控制器*：模擬與 VR 耳機搭配使用的動作控制器，其運作方式類似于與明確表達的互動。

   使用控制器互動模型來模擬 VR 耳機。

   觸發程式、抓取和功能表鍵是透過鍵盤和滑鼠輸入模擬。

### <a name="simulating-controller-movement"></a>模擬控制器移動

按住 **左/靠右控制器操作金鑰** (預設：左方控制器的 *左移位* 和右邊控制器的 *空間*) ，以取得任一控制器的控制權。 當按下操作按鍵時，控制器將會出現在 [功能區] 中。 一旦釋放操作金鑰之後，控制器會在短暫的 **控制器隱藏 Timeout** 之後消失。

您可以透過 [ [輸入模擬工具] 視窗](#input-simulation-tools-window) 中的相機來切換和凍結控制器，或按下 **切換左/向右控制器鍵** (預設值： *T* 代表左邊， *Y* 表示右邊的) 。 再按一次切換鍵，再次隱藏控制器。 若要操控控制器，必須保留 **左/右控制器操作金鑰** 。 按兩下 **Left/Right 控制器操作金鑰** 也可以開啟/關閉控制器。

滑鼠移動會將控制器移至 [視圖] 平面。 您可以使用 **滑鼠滾輪**，更進一步或更接近相機來移動控制器。

若要使用滑鼠旋轉控制器，請將 **左/右控制器操作金鑰** (*左移* 或 *空格*) *，然後* 將 **控制器旋轉按鈕** (預設： *左方 Ctrl* 按鈕) ，然後移動滑鼠以旋轉控制器。 您可以藉由變更輸入模擬設定檔中的 **滑鼠控制器旋轉速度** 設定，來設定控制器旋轉速度。

所有放置也都可以在 [ [輸入模擬工具] 視窗](#input-simulation-tools-window)中變更，包括重設為預設值。

### <a name="additional-profile-settings"></a>其他設定檔設定

* **控制器深度乘數** 控制滑鼠滾輪深度移動的敏感度。 較大的數位會加速控制器縮放。
* **預設控制器距離** 是來自相機的控制器初始距離。 按一下 [ **重設** ] 按鈕控制器也會將控制器放在這個距離。
* **控制器抖動量** 會將隨機動作新增至控制器。 這項功能可用來模擬裝置上不正確的控制器追蹤，並確保互動適用于雜訊的輸入。

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="hand-gestures"></a>手勢

捏合、抓取、刺探等手勢也可以模擬。

1. 使用 **left/Right 控制器操作金鑰** (*左移* 或 *空格*) 來啟用手形控制

2. 在操作時，按住滑鼠按鍵以執行手勢手勢。

您可以對應每個滑鼠按鍵，使用 *左/中/右滑鼠右鍵手勢* 設定，將手圖形轉換成不同的手勢。 當未按下任何按鈕時， *預設手勢* 是手的形狀。

> [!NOTE]
> 縮小 *手勢是* 唯一執行「選取」動作的手勢。

### <a name="one-hand-manipulation"></a>單次操作

1. 按住 **left/Right 控制器操作金鑰** (*左移* 或 *空格*) 
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
    1. 按下 **滑鼠左鍵** 可啟動 *縮小手勢。*
    1. 釋放 **空間** 可停止控制右手邊。 手將會凍結並 *鎖定到縮小手勢，* 因為它已不再被操作。
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

### <a name="motion-controller-interaction"></a>移動控制器互動

模擬的動作控制器可透過與明確表達的相同方式來操作。 在觸發程式、抓取和功能表鍵分別對應至 *滑鼠左鍵*、 *G* 和 *M* 鍵的情況下，互動模型與明確的手互動很類似。

### <a name="eye-tracking"></a>眼球追蹤

您可以藉由檢查 [輸入模擬設定檔](#enabling-the-input-simulation-service)中的 [**模擬眼睛位置**] 選項來啟用 [眼睛追蹤模擬](../eye-tracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor)。 這不應該與 GGV 或移動控制器樣式互動一起使用 (因此，請確定 **預設控制器模擬模式** 已設定為 [ *已) ]* 。

## <a name="see-also"></a>另請參閱

* [輸入系統設定檔](../input/InputProviders.md)。
