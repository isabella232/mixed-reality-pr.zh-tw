---
title: Unity 中的筆勢和運動控制器
description: 瞭解如何在 Unity 中使用手手勢和移動控制器來採取行動。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 手勢、移動控制器、unity、注視、輸入、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: 122642bb7fc561e505098bca00b8bf65bfd4552e
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443575"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Unity 中的筆勢和運動控制器

您可以透過兩種主要方式，在您 [的 [Unity](gaze-in-unity.md)]、[ [手手勢](../../design/gaze-and-commit.md#composite-gestures) ] 和 [ [運動] 控制器](../../design/motion-controllers.md) 中針對 HoloLens 和沉浸式 HMD 採取行動。 您可以透過 Unity 中的相同 Api，存取兩個空間輸入來源的資料。

Unity 提供兩種主要方式來存取 Windows Mixed Reality 的空間輸入資料、 *GetButton/輸入 GetAxis* api （可跨多個 Unity XR sdk 運作），以及 Windows Mixed Reality 的特定 *InteractionManager/GestureRecognizer* api，該 api 會公開可用的完整空間輸入資料集。

## <a name="unity-xr-input-apis"></a>Unity XR 輸入 Api

針對新的專案，我們建議您從頭開始使用新的 XR 輸入 Api。 

您可以在這裡找到有關 [XR api](https://docs.unity3d.com/Manual/xr_input.html)的詳細資訊。

## <a name="unity-buttonaxis-mapping-table"></a>Unity 按鈕/軸對應表

下表中的按鈕和軸識別碼可透過 *GetButton/GetAxis* api，在 Unity 的輸入管理員中受到支援，而「Windows MR 特定」資料行則是指可從 *InteractionSourceState* 類型中 Windows Mixed Reality 取得的屬性。 下列各節將詳細說明每個 Api。

Windows Mixed Reality 的按鈕/軸識別碼對應通常會符合 Oculus 按鈕/軸識別碼。

Windows Mixed Reality 的按鈕/軸識別碼對應有兩種不同于 OpenVR 的對應：
1. 對應會使用與操縱杆不同的觸控板識別碼，以支援具有 thumbsticks 和 touchpads 的控制器。
2. 對應可避免多載功能表按鈕的 A 和 X 按鈕識別碼，讓它們可用於實體 ABXY 按鈕。

<table>
<tr>
<th rowspan="2">輸入 </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">通用 Unity API</a><br /> (輸入. GetButton/GetAxis)  </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 專用輸入 API</a><br /> (XR。Wsa。輸入) </th>
</tr><tr>
<th> 左手 </th><th> 右手</th>
</tr><tr>
<td> 已按下 Select 觸發程式 </td><td> 軸 9 = 1。0 </td><td> 軸 10 = 1。0 </td><td> selectPressed</td>
</tr><tr>
<td> 選取觸發程式類比值 </td><td> 軸9 </td><td> 軸10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 選取觸發程式部分按下 </td><td> 按鈕 14 <i> (遊戲台相容性) </i> </td><td> 按鈕 15 <i> (遊戲台相容性) </i> </td><td> selectPressedAmount &gt; 0。0</td>
</tr><tr>
<td> 已按下功能表按鈕 </td><td> 按鈕 6 * </td><td> 按鈕 7 * </td><td> menuPressed</td>
</tr><tr>
<td> 已按下手柄按鈕 </td><td> 軸 11 = 1.0 (沒有類比值) <br />按鈕 4 <i> (遊戲台相容性) </i> </td><td> 軸 12 = 1.0 (沒有類比值) <br />按鈕 5 <i> (遊戲台相容性) </i> </td><td> 抓住</td>
</tr><tr>
<td> 操縱杆 X <i> (左：-1.0，右： 1.0) </i> </td><td> 軸1 </td><td> 軸4 </td><td> thumbstickPosition. x</td>
</tr><tr>
<td> 操縱杆 Y <i> (top：-1.0，底端： 1.0) </i> </td><td> 軸2 </td><td> 軸5 </td><td> thumbstickPosition. y</td>
</tr><tr>
<td> 已按下操縱杆 </td><td> 按鈕8 </td><td> 按鈕9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> 觸控板 X <i> (左：-1.0、右邊： 1.0) </i> </td><td> 軸 17 * </td><td> 軸 19 * </td><td> touchpadPosition. x</td>
</tr><tr>
<td> 觸控板 Y <i> (頂端：-1.0、底部： 1.0) </i> </td><td> 軸 18 * </td><td> 軸 20 * </td><td> touchpadPosition. y</td>
</tr><tr>
<td> 觸及觸控板 </td><td> 按鈕 18 * </td><td> 按鈕 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> 已按下觸控板 </td><td> 按鈕 16 * </td><td> 按鈕 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 抓住姿勢或指標姿勢 </td><td colspan="2"> 僅限<i>握</i>姿勢： <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> 以引數 <i>形式傳遞底</i> 框或 <i>指標</i> ： SourceState. sourcePose. TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 追蹤狀態 </td><td colspan="2"> <i>職位精確度和來源遺失風險僅可透過 MR 專屬 API 取得</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState。 sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>這些按鈕/軸識別碼與 Unity 針對 OpenVR 所使用的識別碼不同，因為 gamepads、Oculus Touch 和 OpenVR 所使用的對應中發生衝突。

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a>底姿勢與指標姿勢

Windows Mixed Reality 支援各種外型規格中的運動控制器，每個控制器的設計各有不同之處，就是使用者的位置與應用程式在轉譯控制器時應使用的自然「向前」方向之間的關聯性。

為了更妥善地表示這些控制器，您可以針對每個互動來源（底框 **姿勢** 和 **指標姿勢**）調查兩種類型的姿勢。 框姿勢和指標姿勢座標都是由全域 Unity 全局座標中的所有 Unity Api 表示。

### <a name="grip-pose"></a>握住姿勢

底框 **姿勢** 代表 HoloLens 所偵測到的掌上的位置，或是持有移動控制器的掌上。

在沉浸式耳機上，把手姿勢最適合用來 **呈現使用者手或****使用者手中所持有的物件**，例如寶劍或機槍。 視覺化運動控制器時也會使用底框姿勢，因為移動控制器的 Windows 所提供的 **呈現模型** 會使用底框姿勢作為其原點和旋轉中心。

此底框姿勢的定義方式明確如下：
* 把手 **位置**：自然地按住控制器時的棕櫚距心，向左或向右調整以將位置置中置中。 在 Windows Mixed Reality 運動控制器上，此位置通常會與 [抓住] 按鈕對齊。
* 底 **圖方向的右軸**：當您完全開啟手來形成平面的5形姿勢時，您的掌上光 (的光線會從左至右向前復原，從右邊的棕櫚) 
* 底圖 **方向的向前軸**：當您關閉手部分 (時，如同按住控制器) 一樣，也就是由非拇指手指所形成的電子管「轉寄」的光線。
* 底圖 **方向的向上軸**：右邊和向前定義所隱含的向上軸。

您可以透過 Unity 的跨廠商輸入 API (XR 來存取抓住姿勢 *[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/輪替*) 或透過 WINDOWS MR 專屬 API (*SourceState. SourcePose. TryGetPosition/輪替*，要求 **) 的** 的資料。

### <a name="pointer-pose"></a>指標姿勢

**指標姿勢** 代表指向轉寄的控制器秘訣。

系統提供的指標姿勢最適合用來在您 **呈現控制器模型本身** 時 raycast。 如果您要轉譯某個其他的虛擬物件來取代控制器，例如虛擬的機槍，您應該指向該虛擬物件最自然的光線，例如沿著應用程式定義的機槍模型的圓柱移動光線。 因為使用者可以看到虛擬物件，而不是實體控制器，所以指向虛擬物件可能會比使用您的應用程式更自然。

目前，只有透過 Windows MR 專屬 API （ *sourceState. sourcePose. TryGetPosition/旋轉*）在 Unity 中提供指標姿勢，並傳入 *InteractionSourceNode* 作為引數。

## <a name="controller-tracking-state"></a>控制器追蹤狀態

如同耳機，Windows Mixed Reality 運動控制器不需要設定外部追蹤感應器。 相反地，控制器是由耳機本身的感應器追蹤。

如果使用者將控制器移出耳機的觀賞欄位，在大部分情況下，Windows 會繼續推斷控制器位置，並將其提供給應用程式。 如果控制器的長時間遺失視覺追蹤，控制器的位置將會降到大約精確度的位置。

此時，系統會將控制器主體鎖定給使用者，在移動時追蹤使用者的位置，同時仍會使用其內部方向感應器來公開控制器的真實方向。 許多使用控制器來指向和啟動 UI 元素的應用程式，可以正常運作，而不會察覺到使用者注意。

若要瞭解這一點，最好的方法就是親自試試看。 請觀看這段影片，其中包含可搭配各種追蹤狀態的運動控制器使用的沉浸式內容範例：

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>明確追蹤狀態的原因

希望根據追蹤狀態以不同方式來處理位置的應用程式，可能會進一步檢查控制器狀態的屬性，例如 *SourceLossRisk* 和 *PositionAccuracy*：

<table>
<tr>
<th> 追蹤狀態 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高精確度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精確度 (有遺失) 的風險 </b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>近似精確度</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>沒有位置</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: orange"> false</td>
</tr>
</table>

這些移動控制器追蹤狀態的定義如下：
* **高精確度：** 當移動控制器位於耳機的視圖範圍內時，它通常會根據視覺效果追蹤，提供高精確度的位置。 請注意，移動控制器會暫時離開視圖的欄位，或是短暫地遮蔽到耳機感應器 (例如，根據使用者的角度，) 會根據控制器本身的慣性追蹤，繼續傳回高精確度的姿勢。
* **高精確度 (有遺失) 的風險：** 當使用者將移動控制站移出耳機視圖的邊緣之後，耳機很快就無法以視覺化方式追蹤控制器的位置。 應用程式知道當控制器達到此 FOV 界限時，會看到 **SourceLossRisk** 達到1.0。 屆時，應用程式可能會選擇暫停需要穩定資料流程的控制器手勢，以提供高品質的物。
* **近似精確度：** 如果控制器的長時間遺失視覺追蹤，控制器的位置將會降到大約精確度的位置。 此時，系統會將控制器主體鎖定給使用者，在移動時追蹤使用者的位置，同時仍會使用其內部方向感應器來公開控制器的真實方向。 許多使用控制器來指向和啟動 UI 元素的應用程式，都可以正常運作，而不會察覺到使用者的精確度。 具有較長輸入需求的應用程式可能會藉由檢查 **PositionAccuracy** 屬性，選擇將此下降從 **高** 精確度到 **近似** 精確度，例如，讓使用者在這段時間內更有更多的螢幕目標 hitbox。
* **沒有位置：** 雖然控制器可在很長的時間內正常運作，但有時系統會知道即使主體鎖定的位置在當時都沒有意義。 例如，剛開啟的控制器可能未曾以視覺化的方式觀察到，或者使用者可能會放置由其他人挑選的控制器。 在這些時間，系統不會提供應用程式的任何位置，且 *TryGetPosition* 會傳回 false。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>通用 Unity Api (輸入 GetButton/GetAxis) 

**Namespace：** *UnityEngine*， *UnityEngine. XR*<br>
**類型**： *輸入*、 *XR。InputTracking*

Unity 目前使用其一般 *輸入. GetButton/GetAxis* api 來公開 [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 和 Windows Mixed Reality 的輸入，包括實習和移動控制器。 如果您的應用程式使用這些 Api 進行輸入，則可以輕鬆地支援跨多個 XR Sdk 的移動控制器，包括 Windows Mixed Reality。

### <a name="getting-a-logical-buttons-pressed-state"></a>取得邏輯按鈕的按下狀態

若要使用一般 Unity 輸入 Api，您通常會先將按鈕和軸連結到 [Unity 輸入管理員](https://docs.unity3d.com/Manual/ConventionalGameInput.html)中的邏輯名稱，然後將按鈕或軸識別碼系結至每個名稱。 然後，您可以撰寫參考該邏輯按鈕/軸名稱的程式碼。

例如，若要將左移動控制器的 [觸發程式] 按鈕對應至 [提交] 動作，請移至 Unity 內的 [ **編輯 > 專案設定] > 輸入** ，並展開 [軸] 下的 [提交] 區段的屬性。 將 **正面按鈕** 或 **Alt 正按鈕** 屬性變更為讀取 **搖桿按鈕 14**，如下所示：

![Unity 的 InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

然後，您的腳本可以使用 *GetButton* 來檢查提交動作：

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
您可以變更 [**軸**] 下的 [**大小**] 屬性，以新增更多邏輯按鈕。

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>直接取得實體按鈕的按下狀態

您也可以使用 *GetKey* 的完整名稱，以手動方式存取按鈕：

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>取得手或移動控制器的姿勢

您可以使用 XR 存取控制器的位置和旋轉 *。InputTracking*：

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

請注意，這代表控制器的底狀姿勢 (其中的使用者持有控制器) ，這對於在使用者手中轉譯寶劍或機槍，或控制器本身的模型很有用。

請注意，此底框之間的關聯性會造成，且指標會造成 (，控制器的提示會指向控制器的) 可能不同。 目前，只能透過 MR 專屬的輸入 API 來存取控制器的指標姿勢，如下一節所述。

## <a name="windows-specific-apis-xrwsainput"></a>Windows 特定 Api (XR。Wsa。輸入) 

> [!CAUTION]
> 如果您的專案使用任何 XR。WSA Api 在未來的 Unity 版本中，將會以 XR SDK 的方式來淘汰這些 Api。 針對新的專案，我們建議您從一開始就使用 XR SDK。 您可以在 [這裡找到 XR 輸入系統和 api](https://docs.unity3d.com/Manual/xr_input.html)的詳細資訊。

**命名空間：** *UnityEngine. XR。輸入*<br>
**類型**： *InteractionManager*、 *InteractionSourceState*、 *InteractionSource*、 *InteractionSourceProperties*、 *InteractionSourceKind*、 *InteractionSourceLocation*

若要取得 HoloLens) 和移動控制器的 Windows Mixed Reality 手輸入 (的詳細資訊，您可以選擇使用 *UnityEngine. XR* 底下的 Windows 特定空間輸入 api。 這可讓您存取額外的資訊，例如位置精確度或來源種類，讓您可以分辨手和控制器。

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>輪詢實習和移動控制器的狀態

您可以使用 *GetCurrentReading* 方法，輪詢每個互動來源 (手或移動控制器) 的此畫面格狀態。

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

您取回的每個 *InteractionSourceState* 都代表目前時間的互動來源。 *InteractionSourceState* 會公開如下的資訊：
*  (選取/功能表/抓住/觸控板/操縱杆) 會發生何[種類型的按鍵](../../design/motion-controllers.md)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* 動作控制器特定的其他資料，例如觸控板和/或操縱杆的 XY 座標和觸及的狀態

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* InteractionSourceKind，以瞭解來源是手或移動控制器

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>輪詢向前預測呈現的姿勢

* 當您輪詢來自手和控制器的互動來源資料時，您所得到的是向前預測的原因，是在此框架的光子到達使用者眼時的時間點。  這些向前預測的姿勢最適合 **用來轉譯** 控制器或每個畫面格的保留物件。  如果您的目標是使用控制器指定的按下或放開，如果您使用如下所述的歷程記錄事件 Api，這將會是最精確的。

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* 您也可以取得這個目前畫面格的向前預測標頭姿勢。  如同來源的原因，如果您使用如下所 **述的歷程** 記錄事件 api，則在轉譯資料指標時，這會很有用。

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>處理互動來源事件

若要在輸入事件發生時處理其正確的歷程記錄資料，您可以處理互動來源事件，而不是輪詢。

若要處理互動來源事件：
* 註冊 *InteractionManager* 輸入事件。 針對每個您感興趣的互動事件種類，您必須訂閱該事件。

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* 處理事件。 當您訂閱了互動事件之後，就會在適當的情況下取得回呼。 在 *SourcePressed* 範例中，這會在偵測到來源之後，且在釋放或遺失之前。

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>如何停止處理事件

當您不再想要處理事件，或終結已訂閱事件的物件時，您需要停止處理事件。 若要停止處理事件，您可以取消訂閱事件。

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>互動來源事件的清單

可用的互動來源事件如下：
* *InteractionSourceDetected* (來源會變成作用中) 
* *InteractionSourceLost* (變成非使用中) 
* *InteractionSourcePressed* (點擊、按下按鈕或「選取」從未提到) 
* *InteractionSourceReleased* (結束、放開按鈕或 "Select" 從未提到結尾) 
* *InteractionSourceUpdated* (會移動或以其他方式變更某些狀態) 

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>歷程記錄目標的事件，最精確地符合電子報或發行

稍早所述的輪詢 Api 會讓您的應用程式向前預測的姿勢。  雖然這些預測的姿勢最適合用來呈現控制器或虛擬掌上型物件，但未來的原因並不適合作為目標，原因有兩個：
* 當使用者按下控制器上的按鈕時，可能會有關于在系統收到按下之前，透過藍牙20毫秒無線延遲的情況。
* 然後，如果您使用向前預測的姿勢，則會有另一個 10 20 毫秒的向前預測套用到目標，也就是目前框架的光子到達使用者眼睛的時間。

這表示輪詢會提供您一個來源姿勢或 head 的原因，也就是從使用者的標頭開始，並在發生按下或放開時實際返回的40毫秒。  針對 HoloLens 手輸入，雖然沒有無線傳輸延遲，但偵測到按下的處理延遲也很類似。

若要根據使用者的原始意圖來精確地鎖定目標，請按下該 *InteractionSourcePressed* 或 *InteractionSourceReleased* 輸入事件的歷程記錄來源姿勢或 head 姿勢。

您可以使用來自使用者前端或其控制器的歷程記錄資料，來進行按下或釋放的目標：
* 當軌跡或控制器按下的時間點時，可能會用來做為 **目標** ，以判斷使用者的 [撥雲見日](../../design/gaze-and-commit.md) ：

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* 來源會在移動控制器按下的時間點發生，這可用於 **目標** ，以判斷使用者在何處指向控制器。  這會是遇到按下之控制器的狀態。  如果您要轉譯控制器本身，您可以要求指標姿勢，而不是把手姿勢，以將目標光線從使用者考慮到該轉譯控制器的自然秘訣：

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>事件處理常式範例

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高層級複合手勢 Api (GestureRecognizer) 

**命名空間：** *UnityEngine. XR。輸入*<br>
**類型**： *GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*

您的應用程式也可以辨識空間輸入來源、點擊、按住、操作和導覽手勢的較高層級複合手勢。 您可以使用 GestureRecognizer，跨 [手](../../design/gaze-and-commit.md#composite-gestures) 和 [移動控制器](../../design/motion-controllers.md) 辨識這些複合手勢。

GestureRecognizer 上的每個手勢事件都會提供輸入的 SourceKind，以及事件時的目標 head 光線。 某些事件提供其他內容特定資訊。

使用手勢辨識器來捕捉手勢時，只需要執行幾個步驟：
1. 建立新的手勢辨識器
2. 指定要監看的手勢
3. 訂閱這些手勢的事件
4. 開始捕獲手勢

### <a name="create-a-new-gesture-recognizer"></a>建立新的手勢辨識器

若要使用 *GestureRecognizer*，您必須建立 *GestureRecognizer*：

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>指定要監看的手勢

透過 SetRecognizableGestures 指定您感興趣的手勢 *( # B1*：

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>訂閱這些手勢的事件

針對您感興趣的手勢訂閱事件。

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>導覽和操作手勢在 *GestureRecognizer* 的實例上是互斥的。

### <a name="start-capturing-gestures"></a>開始捕獲手勢

根據預設， *GestureRecognizer* 會在呼叫 *StartCapturingGestures ( # B1* 之前，不會監視輸入。 如果在處理 *StopCapturingGestures ( # B3* 的框架之前執行輸入，可能會在 StopCapturingGestures 之後產生手勢事件， *( # B1* 呼叫。 *GestureRecognizer* 會記得在先前的畫面格進行實際發生的情況下，它是開啟或關閉，因此可以根據此框架的監看式目標啟動和停止手勢監視。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>停止捕捉手勢

若要停止手勢辨識：

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>移除手勢辨識器

請記得在終結 *GestureRecognizer* 物件之前取消訂閱的事件。

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>在 Unity 中轉譯移動控制器模型

![移動控制器模型和遙傳](images/motioncontrollertest-teleport-1000px.png)<br>
*移動控制器模型和遙傳*

若要在您的應用程式中轉譯與您的使用者所持有的實體控制器相符的移動控制站，並在按下各種按鈕時表達清楚，您可以在 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity/)組中使用 **MotionController 預製專案**。  這個預製專案會從系統已安裝的移動控制器驅動程式，在執行時間動態載入正確的 glTF 模型。  請務必以動態方式載入這些模型，而不是在編輯器中手動匯入這些模型，如此您的應用程式就會針對使用者可能擁有的任何目前和未來控制器顯示實際精確的3D 模型。

1. 遵循 [消費者入門](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 指示下載 Mixed Reality 工具組，並將它新增至 Unity 專案。
2. 如果您在消費者入門步驟中將相機替換成 *MixedRealityCameraParent* 預製專案，您就可以開始使用！  該預製專案包括移動控制器轉譯。  否則，請從 [專案] 窗格將 *資產/HoloToolkit/Input/Prefabs/MotionControllers* 加入場景中。  當使用者在場景中 teleports 時，您會想要將該預製專案新增為您用來移動攝影機之任何父物件的子系，以便讓控制器與使用者一起使用。  如果您的應用程式不需要 teleporting，只要在場景的根目錄新增預製專案即可。

## <a name="throwing-objects"></a>擲回物件

在虛擬實境中擲回物件是較困難的問題，因此可能會先出現。 如同大部分的實際互動，在遊戲中擲回時，它會以非預期的方式運作，並中斷深度。 我們花了一些時間來思考如何表示實體正確的擲回行為，並提供一些指導方針，讓我們想要與您分享，並透過我們的平臺更新來啟用。

您可以在 [這裡](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到建議如何執行擲回的範例。 此範例會遵循下列四個指導方針：
* **使用控制器的 *速度* ，而不是位置**。 在 Windows 的11月更新中，我們引進了「 [近似」位置追蹤狀態](../../design/motion-controllers.md#controller-tracking-state)時的行為變更。 處於此狀態時，系統會繼續回報控制器的相關速度資訊，只要我們認為它的精確度很高，通常會比位置維持高準確度更長。
* **納入控制器的 *角度速度***。 此邏輯全部包含在靜態方法的檔案中，該檔案 `throwing.cs` 位於 `GetThrownObjectVelAngVel` 上述連結的封裝內：
   1. 由於 conserved 的角度速度，擲回的物件必須維持與擲回時相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. 因為擲回之物件的中心可能不是在底框姿勢的原點，所以它可能會有不同的速度，而在使用者的參考框架中，控制器則可能會有不同的速度。 以這種方式產生的物件速度的部分，就是在控制器原點周圍擲回物件的最大中心的瞬間相切速度。 這種相切速度是控制器角度速度的交叉乘積，向量表示控制器原點與擲回物件的中央之間的距離。

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. 擲回物件的速度總計是控制器速度和這個相切速度的總和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* 請密切 **注意我們應用速度的 *時間***。 按下按鈕時，最多可能需要20毫秒該事件，才能透過藍牙向上到作業系統。 這表示，如果您將控制器狀態變更從按下的狀態變更為未按下（反之亦然），則控制器會引發您所取得的資訊，而這項資訊會在狀態變更之前出現。 此外，我們的輪詢 API 所呈現的控制器會向前預測，以反映畫面上顯示的可能原因，未來可能會更20毫秒。 這適合用來 *呈現* 保留的物件，但是會在使用者釋放擲回的時間點時，將我們的時間問題轉譯為 *目標* 物件。 幸運的是，在11月更新中，當傳送 *InteractionSourcePressed* 或 *InteractionSourceReleased* 這類 Unity 事件時，該狀態會包含實際按下或放開按鈕時的歷程記錄資料。  若要在擲回期間取得最精確的控制器轉譯和控制器目標，您必須適當地正確地使用輪詢和事件：
   * 針對每個畫面格的 **控制器呈現** ，您的應用程式應該將控制器的 *GameObject* 放在向前預測的控制器上，以表示目前畫面格的 photon 時間。  您可以從 Unity 輪詢 Api （例如 XR）取得此資料 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。Wsa。輸入. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。
   * 針對以按下或放開的 **控制器為目標的控制器** ，您的應用程式應該根據該按下或釋放事件的歷程控制器姿勢來 raycast 和計算軌跡。  您可以從 Unity 事件 Api 取得這類資料，例如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。
* **使用** 底框姿勢。 相對於底框姿勢（而不是指標姿勢）回報角度速度和速度。

未來的 Windows 更新將持續改善擲回，而您可以預期在此找到更多資訊。

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>MRTK v2 中的手勢和移動控制器

您可以從輸入管理員存取手勢和移動控制器。
* [MRTK v2 中的手勢](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [MRTK v2 中的動作控制器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>遵循教學課程

混合現實學術中提供逐步教學課程，包含更詳細的自訂範例：

- [MR Input 211：筆勢](tutorials/holograms-211.md)
- [MR Input 213：運動控制器](../../deprecated/mixed-reality-213.md)

[![MR 輸入 213-移動控制器](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR 輸入 213-移動控制器*

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unity 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [手部和眼睛追蹤](hand-eye-in-unit.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱

* [頭部目光和行動](../../design/gaze-and-commit.md)
* [運動控制器](../../design/motion-controllers.md)
