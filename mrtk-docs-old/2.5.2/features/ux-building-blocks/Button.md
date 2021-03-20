---
title: Butons
description: MRTK 中的按鈕總覽
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、MRTK 按鈕
ms.openlocfilehash: 3791d2762c0c58cd375a7ec31e6dde44a1baaeb0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685801"
---
# <a name="button"></a>Button

![Button](../images/button/MRTK_Button_Main.png)

按鈕讓使用者得以觸發立即動作。 它是混合現實中最基本的元件之一。 MRTK 提供各種類型的按鈕 prefabs。

## <a name="button-prefabs-in-mrtk"></a>MRTK 中的按鈕 prefabs

[資料夾] 下的按鈕 prefabs 範例 ``MRTK/SDK/Features/UX/Interactable/Prefabs``

### <a name="unity-ui-imagegraphic-based-buttons"></a>Unity UI 影像/以圖形為基礎的按鈕

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>以碰撞式為基礎的按鈕

|  ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 | ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated | ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular |
|:--- | :--- | :--- |
| HoloLens 2 的 shell 樣式按鈕，其 backplate 支援各種視覺效果的意見反應，例如框線燈、相近光源和壓縮的 front 盤子 | 不含 backplate 的 HoloLens 2 shell 樣式按鈕  | 具有圓形圖形 HoloLens 2 的 shell 樣式按鈕  |
|  ![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96** | ![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H** | ![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V** |
| 寬 HoloLens 2 的 shell 樣式按鈕32x96mm | 具有共用 backplate 的水準 HoloLens 2 按鈕列 | 具有共用 backplate 的垂直 HoloLens 2 按鈕列 |
|  ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** | ![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32** | ![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32** |
| HoloLens 2 的 shell 樣式核取方塊32x32mm | HoloLens 2 的 shell 樣式參數32x32mm | HoloLens 2 的 shell 樣式選項按鈕32x32mm |
|  ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96** | ![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** | ![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** |
| HoloLens 2 的 shell 樣式核取方塊32x96mm | HoloLens 2 的 shell 樣式參數32x96mm | HoloLens 2 的 shell 樣式選項按鈕32x96mm |
|  ![星形 ](../images/button/MRTK_Button_Radial.png) **放射狀** | ![核取方塊](../images/button/MRTK_Button_Checkbox.png) **核取方塊** | ![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch** |
| 放射狀按鈕 | 核取方塊  | 切換開關 |
|  ![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1** | ![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton** | ![Button_Base ](../images/button/MRTK_Button_Base.png) **按鈕** |
| HoloLens 1 gen 的 shell 樣式按鈕 | 圓形形狀推播按鈕 | 基本按鈕 |

`Button` (的資產/MRTK/SDK/Features/UX/互動/Prefabs/預製專案) 是以[互動](Interactable.md)概念為基礎，可為按鈕或其他類型的互動表面提供簡單的 UI 控制項。 [基準] 按鈕支援所有可用的輸入方法，包括用於近距離互動的已表達手輸入，以及最遠互動的注視 + 無線電波。 您也可以使用語音命令來觸發按鈕。

`PressableButtonHoloLens2` (資產/MRTK/SDK/Features/UX/互動/Prefabs/PressableButtonHoloLens2. 預製專案) 是 HoloLens 2 的 shell 樣式按鈕，可支援直接手動追蹤輸入的按鈕精確移動。 它結合 `Interactable` 腳本與 `PressableButton` 腳本。

針對 HoloLens 2，建議使用具有不透明 backplate 的按鈕。 由於這些可用性和穩定性問題，因此不建議使用透明按鈕：

* 在實體環境中難以閱讀圖示和文字
* 當事件觸發時，很難瞭解
* 透過透明平面顯示的全像 LSR，可能不穩定，HoloLens 2 的深度穩定

![Button_UsePlated](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>如何使用 pressable 按鈕

### <a name="unity-ui-based-buttons"></a>Unity UI 型按鈕

在場景中建立畫布 (GameObject > UI-> Canvas) 。 在畫布的 [偵測器] 面板中：

* 按一下 [轉換成 MRTK Canvas]
* 按一下 [新增 NearInteractionTouchableUnityUI]
* 將矩形轉換元件的 X、Y 和 Z 刻度設定為0.001

然後，將 `PressableButtonUnityUI` (資產/MRTK/sdk/features/ux/互動/Prefabs/PressableButtonUnityUI. 預製專案) 、 `PressableButtonUnityUICircular` (資產/MRTK/Sdk/FEATURES/Ux/互動/Prefabs/PressableButtonUnityUICircular. 預製專案) ，或 `PressableButtonHoloLens2UnityUI` (資產/MRTK/sdk/features/ux/互動/Prefabs/PressableButtonHoloLens2UnityUI. 預製專案) 至畫布上。

### <a name="collider-based-buttons"></a>以碰撞式為基礎的按鈕

只要拖曳 `PressableButtonHoloLens2` (資產/MRTK/SDK/Features/UX/互動/Prefabs/PressableButtonHoloLens2. 預製專案) 或 `PressableButtonHoloLens2Unplated` (資產/MRTK/SDK/FEATURES/UX/互動/Prefabs/PressableButtonHoloLens2Unplated. 預製專案) 進入場景。 這些按鈕 prefabs 已設定為對各種類型的輸入具有音訊視覺效果的意見反應，包括清楚的輸入和注視。

預製專案本身以及 [互動](Interactable.md) 元件中公開的事件可以用來觸發其他動作。 [HandInteractionExample 場景](../example-scenes/HandInteractionExamples.md)中的 [pressable] 按鈕會使用互動的 *OnClick* 事件來觸發 cube 色彩的變更。 此事件會針對不同類型的輸入方法（例如注視、碰點、手光，以及透過 pressable 按鈕腳本的實體按鈕按下）觸發。

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to use Interactable Button Image">

您可以設定 [pressable] 按鈕透過按鈕上的來引發 *OnClick* 事件的時機 `PhysicalPressEventRouter` 。 例如，您可以將 *OnClick* 設定為第一次按下按鈕時引發，而不是按下和放開，方法是在 *按下* 時，按 [按一下] 事件來設定 *互動*。

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use Events Button Image">

若要利用特定的已表達手勢輸入狀態資訊，您可以使用 pressable 按鈕事件- *觸控開始*、 *觸控端*、 *按下按鈕*、 *按鈕已釋放*。 不過，這些事件將不會引發，以回應碰點、手動光線或眼睛輸入。 **若要同時支援近乎和遠的互動，建議使用互動的 *OnClick* 事件。**

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450" alt="How to use pressable button Image">

## <a name="interaction-states"></a>互動狀態

處於閒置狀態時，不會顯示按鈕的 front 板。 以手指方法或注視輸入的游標作為介面，會顯示 front 盤子的發光框線。 前端板介面上的 fingertip 位置有額外的反白顯示。 以手指推送時，front 板會隨著 fingertip 移動。 當 fingertip 觸及 front 板的介面時，它會顯示一個微妙的脈衝效果，以提供觸控點的視覺化意見反應。

在 HoloLens 2 shell 樣式按鈕中，有許多視覺提示和 affordances 可提高使用者對互動的信賴度。

|  ![近亮光](../images/button/ux_button_affordance_proximitylight.jpg) | ![焦點醒目提示](../images/button/ux_button_affordance_focushighlight.jpg)  | ![壓縮框架](../images/button/ux_button_affordance_compression.jpg) | ![觸發程式上的脈衝](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| 近亮光 | 焦點醒目提示 | 壓縮框架 | 觸發程式上的脈衝 |

微妙的脈衝效果是由 [pressable] 按鈕所觸發，它會尋找即時在目前互動指標上 *) 的 ProximityLight (s* 。 如果找到任何接近的燈，則會 `ProximityLight.Pulse` 呼叫方法，這會自動以動畫顯示著色器參數來顯示脈衝。

## <a name="inspector-properties"></a>偵測器屬性

![Button_Structure](../images/button/MRTK_Button_Structure.png)

方塊 **碰撞** 
 `Box Collider`按鈕的 front 板。

**Pressable 按鈕** 按鍵互動的按鈕移動邏輯。

**實體按事件路由器** 此腳本會將事件從手形的互動傳送至 [互動](Interactable.md)。

**互動** 
[互動](Interactable.md)可處理各種類型的互動狀態和事件。 HoloLens 的注視、手勢和語音輸入，以及沉浸式耳機移動控制器輸入都會由這個腳本直接處理。

**音訊來源** 音訊意見反應剪輯的 Unity 音訊來源。

*NearInteractionTouchable* 需要使用明確的手輸入進行任何物件可觸式。

## <a name="prefab-layout"></a>預製專案版面配置

*ButtonContent* 物件包含 front 板、文字標籤和圖示。 *FrontPlate* 會使用 *Button_Box* 著色器，回應索引 fingertip 的鄰近程度。 它會顯示對觸控的燈光框線、相近光源和脈衝效果。 文字標籤會使用 TextMesh Pro 進行。 *SeeItSayItLabel* 的可見度由 [互動](Interactable.md)的主題控制。

![Button_Layout](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>如何變更圖示和文字

MRTK 按鈕會使用 `ButtonConfigHelper` 元件來協助您變更按鈕的圖示、文字和標籤。  (請注意，如果選取的按鈕上沒有元素，某些欄位可能不存在。 ) 

![Button_Configure Helper](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>建立和修改圖示集

**圖示集** 是元件所使用的一組共用圖示資產 `ButtonConfigHelper` 。 支援三種圖示 *樣式* 。

* **四** 個圖示會在使用的四個上呈現 `MeshRenderer` 。 這是預設的圖示樣式。
* **Sprite** 圖示是使用來呈現 `SpriteRenderer` 。 如果您想要將圖示匯入為 sprite 工作表，或想要將圖示資產與 Unity UI 元件共用，這會很有用。 若要使用此樣式，您必須將 Sprite 編輯器套件安裝 **(Windows-> 封裝管理員 > 2D Sprite)**
* **字元** 圖示會使用元件來呈現 `TextMeshPro` 。 如果您想要使用圖示字型，這會很有用。 若要使用 HoloLens 圖示字型，您將需要建立 `TextMeshPro` 字型資產。

若要變更按鈕使用的樣式，請展開 ButtonConfigHelper 中的 [ *圖示* ] 下拉式清單，然後從 [ *圖示樣式* ] 下拉式清單中選取。

您可以使用 [資產] 功能表建立新的按鈕圖示集： **建立 > 混合現實工具組 > 圖示集。** 若要加入四個和 sprite 圖示，只要將它們拖曳到各自的陣列中即可。 若要新增字元圖示，您必須先建立並指派字型資產。

在 MRTK 2.4 和更高的範圍中，我們建議將自訂圖示紋理移至 IconSet。
若要將專案中所有按鈕的資產升級為新的建議格式，請使用 ButtonConfigHelperMigrationHandler。
 (混合現實工具組-> 公用程式-> 的遷移視窗-> 的遷移處理常式選取範圍-> MixedReality) 

匯入升級按鈕所需的 MixedRealityToolkit 工具套件。

![升級視窗對話方塊](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

如果在遷移期間于預設的圖示集中找不到圖示，則會在 MixedRealityToolkit 中建立自訂圖示集。產生/CustomIconSets。 對話方塊會指出已發生此情況。

![自訂圖示通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>建立 HoloLens 圖示字型資產

首先，將圖示字型匯入 Unity。 在 Windows 電腦上，您可以在 *windows/font-family/holomdl2. ttf* 中找到預設的 HoloLens 字型。 將此檔案複製並貼到您的 [資產] 資料夾中。

接下來，透過 **Window > TextMeshPro > 字型建立者** 來開啟 [TextMeshPro 字型資產建立者]。 以下是用來產生 HoloLens 字型塔的建議設定。 若要包含所有圖示，請在 [ *字元順序* ] 欄位中貼上下列 Unicode 範圍：

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Button_Creation 1](../images/button/MRTK_Font_Asset_Creation_1.png)

產生字型資產之後，請將其儲存至您的專案，並將其指派給您的圖示集的 *Char 圖示字型* 欄位。 現在將會填入 [ *可用圖示* ] 下拉式清單。 若要讓圖示可供按鈕使用，請按一下它。 它會新增至 [ *選取的圖示* ] 下拉式清單中，現在會顯示在中， `ButtonConfigHelper.` 您可以選擇性地為圖示提供標記。 這可讓您在執行時間設定圖示。

![Button_Creation 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Button_Creation 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

若要使用您的圖示集，請選取按鈕，展開中的 [圖示] 下拉式清單， `ButtonConfigHelper` 然後將它指派給 [ *圖示集* ] 欄位。

![Button_Icon 設定指派](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>如何變更按鈕的大小

HoloLens 2 的 shell 樣式按鈕大小為32x32mm。 若要自訂維度，請在按鈕預製專案中變更這些物件的大小：

1. **FrontPlate**
2. BackPlate 下的 **四** 個
3. 根的方塊 **碰撞**

然後，在 NearInteractionTouchable 腳本（位於按鈕的根目錄）中，按一下 [ **修正界限** ] 按鈕。

更新 FrontPlate ![ Button_Size 自訂1的大小](../images/button/MRTK_Button_SizeCustomization1.png)

更新四 ![ Button_Size 自訂2的大小](../images/button/MRTK_Button_SizeCustomization2.png)

將 Box 碰撞 Button_Size 的大小更新為 ![ 自訂3](../images/button/MRTK_Button_SizeCustomization3.png)

按一下 [修正界限] ![ Button_Size 自訂4](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it"></a>語音命令 ( 「請參閱-it」 ) 

**語音輸入處理常式** [Pressable 中的 [互動](Interactable.md) 腳本] 按鈕已經在執行 `IMixedRealitySpeechHandler` 。 您可以在這裡設定語音命令關鍵字。

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Speech Button 1 Image">

**語音輸入設定檔** 此外，您必須在全域 *語音命令設定檔* 中註冊 voice 命令關鍵字。

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Speech Button 2 Image">

**請參閱-it，例如 it 標籤** Pressable 按鈕預製專案在 *SeeItSayItLabel* 物件下具有預留位置 TextMesh Pro 標籤。 您可以使用此標籤，將按鈕的 voice 命令關鍵字傳達給使用者。

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Speech Button 3">

## <a name="how-to-make-a-button-from-scratch"></a>如何從頭建立按鈕

您可以在 **PressableButtonExample** 場景中找到這些按鈕的範例。

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. 建立具有 cube 的 pressable 按鈕 (近乎互動) 

1.  (GameObject > 3D 物件 > Cube 建立 Unity Cube) 
2. 新增 `PressableButton.cs` 腳本
3. 新增 `NearInteractionTouchable.cs` 腳本

在的 [ `PressableButton` 檢查] 面板中，將 cube 物件指派給 **移動按鈕視覺效果**。

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="Pressable button cube 3">

當您選取 cube 時，您會在物件上看到多個彩色圖層。 這會將 **按下設定** 下的距離值視覺化。 使用控制碼，您可以設定何時開始按 (將物件) 移動，以及何時觸發事件。

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Button Cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable Button Cube 2">

當您按下按鈕時，它會移動並產生腳本中公開的適當事件， `PressableButton.cs` 例如 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 。

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable Button cube1">

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. 將視覺效果意見反應新增至 [基本 cube] 按鈕

MRTK 標準著色器提供各種功能，可讓您輕鬆地新增視覺效果的意見反應。 建立材質並選取著色器 `Mixed Reality Toolkit/Standard` 。 或者，您可以使用或複製其中一個 `/SDK/StandardAssets/Materials/` 使用 MRTK 標準著色器的現有材質。

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

核取 [ `Hover Light` `Proximity Light` 流暢的 **選項**]。 這可讓您近乎接近的視覺效果回饋 (鄰近性光線) 和目前的指標 (停留) 互動。

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="Pressable Button Cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="Pressable button cube 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. 將音訊意見反應新增至 [基本 cube] 按鈕

由於 `PressableButton.cs` 腳本會公開 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 等事件，因此我們可以輕鬆地指派音訊意見反應。 只要將 Unity 新增 `Audio Source` 至 cube 物件，然後選取 [spatialize. PlayOneShot () 來指派音訊剪輯。 您可以使用 MRTK_Select_Main，並 MRTK_Select_Secondary 資料夾下的音訊剪輯 `/SDK/StandardAssets/Audio/` 。

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="Pressable button cue 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable button cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. 新增視覺狀態並處理最遠的互動事件

[互動](Interactable.md) 是一種腳本，可讓您輕鬆地為各種類型的輸入互動建立視覺狀態。 它也會處理大部分的互動事件。 `Interactable.cs`在 [**設定檔**] 下的 [**目標**] 欄位中加入 cube 物件，並將其拖放。 然後，使用類型 **ScaleOffsetColorTheme** 來建立新的主題。 在此主題下，您可以指定特定互動狀態（例如 **焦點** 和 **按下**）的物件色彩。 您也可以控制刻度和位移。 檢查 **簡化** 並設定持續時間，讓視覺效果轉換平滑。

![選取設定檔主題](../images/button/mrtk_button_profiles.gif)

您會看到物件對 (手光線或注視游標) 的回應，以及接近 (手) 互動。

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Run Cube 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Run Cube 4">

## <a name="custom-button-examples"></a>自訂按鈕範例

在 [HandInteractionExample 場景](../example-scenes/HandInteractionExamples.md)中，請參閱使用的鋼琴和圓形按鈕範例 `PressableButton` 。

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Button Custom 1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Button Custom 2">

每個鋼琴按鍵都有一個 `PressableButton` 和一個已 `NearInteractionTouchable` 指派的腳本。 請務必確認的 *本機向前* 方向 `NearInteractionTouchable` 正確無誤。 它是以編輯器中的白色箭號表示。 請確定箭號指向按鈕的正面臉部：

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Button Custom 3">

## <a name="see-also"></a>另請參閱

* [互動](Interactable.md)
* [視覺主題](../VisualThemes.md)
