---
title: 指標
description: MRTK 中指標的檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、指標、
ms.openlocfilehash: 96d7e1c14361fdce94efcdef07b02a51f06ce599
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694305"
---
# <a name="pointers"></a>指標

![Pointer](../images/pointers/MRTK_Pointer_Main.png)

本文說明如何在實務上設定和回應指標輸入（相較于[指標架構](../../architecture/controllers-pointers-and-focus.md)）

偵測到新的控制器時，會在執行時間自動具現化指標。 有一個以上的指標可以附加至控制器。 例如，使用預設指標設定檔時，Windows Mixed Reality 控制器會同時取得一般選取和遙傳的行和拋物線指標。

## <a name="pointer-configuration"></a>指標設定

指標會在 MRTK 中透過進行設定為輸入系統的一部分 [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) 。 這種類型的設定檔會指派給 [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) MRTK Configuration inspector 中的。 指標設定檔會判斷游標、執行時間可用的指標類型，以及這些指標如何彼此通訊，以決定哪一個是作用中。

- *指向範圍* -定義指標可與 GameObject 互動的最大距離。

- *指向 Raycast 圖層遮罩* -這是 LayerMasks 的優先陣列，用來判斷任何指定指標可與其互動的可能 gameobject，以及嘗試的互動順序。 這可能有助於確保指標會在其他場景物件之前先與 UI 元素互動。
![指標設定檔範例](../images/input/pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>指標選項設定

預設的 MRTK 指標設定檔設定包含下列指標類別以及現成關聯的 prefabs。 在執行時間可供系統使用的指標清單，是在指標設定檔的 *指標選項* 下定義。 開發人員可以利用這份清單來重新設定現有的指標、加入新的指標，或刪除一個指標。

![指標選項設定檔範例](../images/input/pointers/PointerOptionsProfile.PNG)

每個指標專案都是由下列資料集所定義：

- *控制器類型* -指標有效的控制器集。
  - 例如， *PokePointer* 會負責具有手指的 "刺探" 物件，且預設標示為僅支援已標示的手型控制器類型。 只有當控制器可供使用時，才會具現化指標，而特定 *控制器類型* 則會定義此指標預製專案可以建立的控制器。

- *Handedness* -允許只針對特定的手具現化指標 (左/右) 

> [!NOTE]
> 將指標專案的 *Handedness* 屬性設定為 [ *無* ]，將會從系統中有效地停用它，作為從清單中移除該指標的替代方法。

- *指標預製專案* -當符合指定控制器類型和 handedness 的控制器開始追蹤時，會具現化此預製專案資產。

您可以有多個與控制器相關聯的指標。 例如，在 `DefaultHoloLens2InputSystemProfile` (資產/MRTK/SDK/設定檔/HoloLens2/) 中，有向 PokePointer、GrabPointer 和 DefaultControllerPointer 相關聯的、 和 (亦即 ) 的手。

> [!NOTE]
> MRTK 在 *資產/MRTK/SDK/Features/UX/prefabs/指標* 中提供一組指標 prefabs。 只要新的自訂預製專案包含 *資產/MRTK/SDK/功能/UX/腳本/指標* 或任何其他執行的腳本中的其中一個指標腳本，就可以建立新的自訂 [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) 。

### <a name="default-pointer-classes"></a>預設指標類別

下列類別是可用的現成 MRTK 指標，並定義于上面所述的預設 *MRTK 指標設定檔* 中。 在 *資產/MRTK/SDK/Features/UX/Prefabs/指標* 下提供的每個指標預製專案，都包含其中一個附加的指標元件。

![MRTK 預設指標](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>遠指標

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 *LinePointer*（基底指標類別）會從輸入的來源繪製一條線 (亦即，控制器) 指標方向，並支援以此方向進行的單一光線轉換。 一般而言，子類別（例如 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 和傳送指標）會具現化並利用 (也會繪製線條來指出遙傳最後在) 的位置，而不是主要提供一般功能的類別。

針對 Oculus、Vive 和 Windows Mixed Reality 等動作控制器，旋轉將符合控制器的旋轉。 針對其他控制器（例如 HoloLens 2 表達的手），旋轉會符合系統提供的手邊指標。

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*CurvePointer* 延伸 *LinePointer* 類別的方式，是允許沿著曲線的多重步驟光線轉換。 這個基底指標類別適用于彎曲的實例，例如遙傳指標，其中的線條會一直彎曲至 parabola。

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

*ShellHandRayPointer* 的實值（延伸自 [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) ）是用來做為 *MRTK 指標設定檔* 的預設值。 *DefaultControllerPointer* 預製專案會實作為 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 類別。

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

GGVPointer 也稱為「 *注視/手勢/語音」 (GGV)* 指標，其可支援 HoloLens 1 樣式的外觀和點一下互動，主要是透過注視和點擊，或注視和語音選取互動。 GGV 指標的位置和方向是由標頭的位置和旋轉所驅動。

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

*TouchPointer* 負責使用 Unity 觸控輸入 (也就是觸控式螢幕) 。 這些都是「遠的互動」，因為觸及螢幕的動作會將攝影機的光線轉換成場景中可能的位置。

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

*MousePointer* 可讓螢幕到世界 raycast，以進行遠距離的互動，而非觸控。

![滑鼠指標](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> 依預設，在 MRTK 中並不提供滑鼠支援，但可以藉由將類型的新 *輸入 Data Provider* 新增 [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) 至 MRTK 輸入設定檔，並將指派 [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) 給資料提供者來啟用。

#### <a name="near-pointers"></a>近端指標

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

*[PokePointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* 是用來與支援「近距離互動可觸式」的遊戲物件互動。 具有附加腳本的 Gameobject [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 。 在 UnityUI 的案例中，此指標會尋找 NearInteractionTouchableUnityUIs。  PokePointer 會使用 SphereCast 來決定最接近的可觸式元素，並用它來開啟 pressable 按鈕之類的功能。

 使用元件設定 GameObject 時 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) ，請務必將 *localForward* 參數設定為指向按鈕或其他應設為可觸式之物件的前方。 也請確定可觸式的 *界限* 符合可觸式物件的界限。

有用的連結指標屬性：

- *TouchableDistance*：可與可觸式介面互動的最大距離
- *視覺效果*：用來轉譯手指視覺 () 的遊戲物件，預設為。
- *Line*：從 fingertip 到現用輸入介面所要繪製的選擇性線條。
- LayerMasks *圖層遮罩*-優先順序較高的陣列，以判斷指標可與其互動的可能 gameobject，以及嘗試的互動順序。 請注意，GameObject 也必須有 `NearInteractionTouchable` 元件，才能與處理常式指標互動。

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

*[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* 會使用 [UnityEngine](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html)來識別最接近的 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 互動物件，這對類似的 "grabbable" 輸入很有用 `ManipulationHandler` 。 與 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 功能配對類似，為了與球體指標互動，遊戲物件必須包含腳本的元件 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 。

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

實用的球體指標屬性：

- *球體轉換半徑*：用來查詢 grabbable 物件之球體的半徑。
- *接近物件邊界*：球體轉換半徑的最上方距離，以查詢偵測物件是否接近指標。 接近物件偵測半徑總計為球體轉換半徑 + 接近物件邊界
- *接近物件磁區角度*：指向指標的正向軸周圍的角度，以查詢附近的物件。 使查詢函式 `IsNearObject` 如同錐形。 根據預設，這會設定為66度，以符合 Hololens 2 行為

![將球體指標修改為只查詢順向方向的物件](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- *接近物件平滑因數*：接近物件偵測的平滑因數。 如果在接近的物件半徑中偵測到物件，查詢的半徑就會變成接近物件半徑 * (1 + 接近物件平滑因數) 來降低敏感度，讓物件更難離開偵測範圍。
- *抓取圖層遮罩* -LayerMasks 的優先陣列，以判斷指標可與其互動的可能 gameobject，以及嘗試的互動順序。 請注意，GameObject 也必須有 `NearInteractionGrabbable` ，才能與 SpherePointer 互動。
    > [!NOTE]
    > 空間感知層會在 MRTK 提供的預設 GrabPointer 預製專案中停用。 這樣做的目的是為了降低使用空間網格來執行球體重迭查詢的效能影響。 您可以藉由修改 GrabPointer 預製專案來啟用此項。
- *忽略不在 FOV 中的 Colliders* -是否忽略可能接近指標的 Colliders，而不是實際在視覺效果 FOV 中的。
這可能會導致意外的抓取，並可讓您在接近 grabbable 但看不到時，可以開啟手片。 *視覺效果 FOV* 是透過錐形來定義，而不是基於效能考慮而使用一般的錐。 這個錐形的中心和方向與相機的錐狀相同，半徑等於半顯示器高度 (或垂直 FOV) 。

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a>傳送指標

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) 會在採取動作時引發傳送要求 (例如 您可以按下 [傳送] 按鈕) ，以移動使用者。
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) 會在採取動作時引發傳送要求 (例如 [傳送] 按鈕會按下) 拋物線行 raycast，以便移動使用者。

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a>混合現實平臺的指標支援

下表詳細說明通常用於 MRTK 中常見平臺的指標類型。 注意：您可以將不同的指標類型加入至這些平臺。 例如，您可以將「前往指標」或「球體」指標加入至 VR。 此外，使用遊戲台的 VR 裝置可以使用 GGV 指標。

|       Pointer              | OpenVR  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| ShellHandRayPointer | 有效   | 有效                 |            | 有效      |
| TeleportPointer     | 有效   | 有效                 |            |            |
| GGVPointer          |         |                       | 有效      |            |
| SpherePointer       |         |                       |            | 有效      |
| PokePointer         |         |                       |            | 有效      |

## <a name="pointer-interactions-via-code"></a>透過程式碼的指標互動

### <a name="pointer-event-interfaces"></a>指標事件介面

MonoBehaviours，它會執行下列一或多個介面，並將其指派給包含 `Collider` 相關聯介面所定義之指標互動事件的 GameObject。

| 事件 | 描述 | 處理常式 |
| --- | --- | --- |
| 焦點變更/焦點變更前 | 在遊戲物件上引發焦點，並在每次指標改變焦點時取得。 | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
焦點進入/離開 | 當第一個指標進入焦點時，會在遊戲物件上引發焦點，並在最後一個指標離開焦點時取得焦點。 | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
指標向下/拖曳/向上/按一下 | 引發至報表指標按下、拖曳和釋放。 | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
Touch 已開始/更新/已完成 | 由觸控感知指標引發，例如 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 報告觸控活動。 | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) 而且 [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) 應該在引發它們的物件中處理。 您可以全域接收焦點事件，但是與其他輸入事件不同的是，全域事件處理常式不會根據焦點封鎖接收事件 (事件將會由全域處理常式和焦點) 中的對應物件接收。

#### <a name="pointer-input-events-in-action"></a>作用中的指標輸入事件

MRTK 輸入系統可辨識並處理指標輸入事件，與 [一般輸入事件](input-events.md#input-events-in-action)的方式類似。 不同之處在于指標輸入事件只會由引發輸入事件的指標，以及任何全域輸入處理常式的 GameObject 來處理。 一般輸入事件是由所有使用中指標的焦點 Gameobject 來處理。

1. MRTK 輸入系統可識別輸入事件已發生
1. MRTK 輸入系統會將輸入事件的相關介面函式引發至所有已註冊的全域輸入處理常式
1. 輸入系統會決定要將哪些 GameObject 放在引發事件的指標
    1. 輸入系統會利用 [Unity 的事件系統](https://docs.unity3d.com/Manual/EventSystem.html) 來引發焦點 GameObject 上所有相符元件的相關介面函式
    1. 如果您在任何時間點輸入事件已 [標示為已使用](input-events.md#how-to-stop-input-events)，進程將會結束，且不會有進一步的 gameobject 接收回呼。
        - 範例：將會搜尋執行介面的元件 [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) ，以取得 GameObject 或失去焦點
        - 注意：如果在目前的 GameObject 上找不到符合所需介面的元件，Unity 事件系統將會反升搜尋父 GameObject。
1. 如果未註冊任何全域輸入處理常式，且找不到具有相符元件/介面的 GameObject，則輸入系統會呼叫每個已註冊的回溯輸入處理常式

#### <a name="example"></a>範例

以下範例腳本會在指標取得或離開焦點或指標選取物件時，變更附加轉譯器的色彩。

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a>查詢指標

您可以藉由迴圈查看可用的輸入來源，來收集目前作用中的所有指標 (例如 可用的控制器和輸入) 探索哪些指標附加至它們。

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a>主要指標

開發人員可以訂閱 FocusProviders PrimaryPointerChanged 事件，以在焦點的主要指標變更時收到通知。 這項功能非常適合用來識別使用者目前是否透過注視或手的光線或其他輸入來源與場景互動。

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

`PrimaryPointerExample` (資產/MRTK/範例/示範/輸入/場景/PrimaryPointer) 場景顯示如何使用 [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) for 事件來回應新的主要指標。

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a>指標結果

指標 [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) 屬性包含用來判斷具有焦點之物件的場景查詢目前的結果。 針對 raycast 指標，例如動作控制器預設所建立的指標、注視輸入和手光線，它會包含 raycast 點擊的位置和正常。

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

`PointerResultExample`場景 (資產/MRTK/範例/示範/輸入/場景/PointerResult/PointerResultExample unity) 示範如何使用指標在叫用 [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) 位置產生物件。

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a>停用指標

若要啟用和停用指標 (例如，若要停用手光線) ，請透過設定 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 指定指標類型的 [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) 。

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils)如需 [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 更多範例，請參閱和。

## <a name="pointer-interactions-via-editor"></a>經由編輯器的指標互動

若為所處理的指標事件 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) ，MRTK 會以元件的形式提供進一步的便利性 [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) ，讓指標事件可以透過 Unity 事件直接處理。

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a>指標範圍

大部分的指標都有設定，這些設定會限制它們在場景中 raycast 和與其他物件互動的程度。
依預設，此值設定為10個計量。 選擇這個值與 HoloLens shell 的行為保持一致。

這可以藉由更新 `DefaultControllerPointer` 預製專案 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 元件的欄位來變更：

*指標範圍* -這會控制指標會與之互動的最大距離。

*預設指標範圍* -這會控制當指標不與任何互動時，將呈現的指標光線/行長度。

## <a name="see-also"></a>另請參閱

- [指標架構](../../architecture/controllers-pointers-and-focus.md)
- [輸入事件](input-events.md)
