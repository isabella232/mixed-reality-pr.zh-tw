---
ms.openlocfilehash: fb8b5b509ef83e2a4f9d978dbf0faebbf3e0be1d10d6697f16cfb9366d7a2edb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187262"
---
# <a name="426"></a>[4.26](#tab/426)

若要取得手片的資料，您應該使用上一節中的 Get 移動控制器資料函數。 傳回的結構包含兩個參數，您可以使用這兩個參數來建立手光線– **目標位置** 和 **目標旋轉**。 這些參數會形成您的肘線所導向的光線。 您應該採用它們，並尋找所指向的全像影像。

以下是判斷手光線是否叫用小工具和設定自訂命中結果的範例：

![取得移動控制器資料函式的藍圖](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

若要在藍圖中使用手片，請搜尋 **Windows Mixed Reality HMD** 下的任何動作：

![手中的最佳光線](../images/unreal/hand-rays-bp.png)

若要以 c + + 存取它們，請將加入 `WindowsMixedRealityFunctionLibrary.h` 至呼叫程式碼檔案的頂端。

### <a name="enum"></a>列舉

您也可以存取 **EHMDInputControllerButtons** 下的輸入案例，此案例可用於藍圖：

![輸入控制器按鈕](../images/unreal/input-controller-buttons.png)

若要在 c + + 中存取，請使用 `EHMDInputControllerButtons` 列舉類別：
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

以下是兩個適用列舉案例的明細：

* **選取** 使用者觸發的選取事件。
    * 在 HoloLens 2 中，藉由按下按鍵、注視和認可，或藉由在啟用[語音輸入](../unreal-voice-input.md)時說出「選取」來觸發。
* **理解** 使用者觸發的理解事件。
    * 在 HoloLens 2 中，藉由關閉使用者的手指來觸發。

您可以透過如下所示的列舉，在 c + + 中存取您的手形網格追蹤狀態 `EHMDTrackingStatus` ：

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

以下是兩個適用列舉案例的明細：

* **NotTracked** –不可見的手
* 已 **追蹤**--已完整追蹤手

### <a name="struct"></a>結構

PointerPoseInfo 結構可以提供下列資料的資訊：

* **原點** –手的原點
* **方向** –手形方向
* **向上** –向上向量
* **方向** –方向四元數
* **追蹤狀態** -目前的追蹤狀態

您可以透過藍圖存取 PointerPoseInfo 結構，如下所示：

![指標姿勢資訊 BP](../images/unreal/pointer-pose-info-bp.png)

或使用 c + +：

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>函式

您可以在每個畫面上呼叫以下列出的所有函式，以允許連續監視。

1. **取得指標姿勢資訊** 會傳回目前框架中的手光線方向的完整資訊。

藍圖：

![取得指標姿勢資訊](../images/unreal/get-pointer-pose-info.png)

C++：
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. 如果在目前的框架中 Grasped 手， **Grasped 會** 傳回 true。

藍圖：

![為 Grasped BP](../images/unreal/is-grasped-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. 如果使用者在目前的框架中觸發了 Select，**則 [已按下] 會** 傳回 true。

藍圖：

![選取 [按下 BP]](../images/unreal/is-select-pressed-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **按一下按鈕時** ，如果在目前的框架中觸發事件或按鈕，則會傳回 true。

藍圖：

![按鈕是否按下 BP](../images/unreal/is-button-clicked-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **取得控制器追蹤狀態** 會傳回目前框架中的追蹤狀態。

藍圖：

![取得控制器追蹤狀態 BP](../images/unreal/get-controller-tracking-status-bp.png)

C++：
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```