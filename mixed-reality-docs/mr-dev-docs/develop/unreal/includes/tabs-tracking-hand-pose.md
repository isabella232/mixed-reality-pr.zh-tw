---
ms.openlocfilehash: c5a13798ca6a73f1a6410abe310c2166b67f4626
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717786"
---
# <a name="426"></a>[4.26](#tab/426)

階層是由列舉所描述 `EHandKeypoint` ：

![手 keypoint bluprint 選項的影像](../images/hand-keypoint-bp.png)

您可以使用 **Get 移動控制器資料** 函式，從使用者的手中取得所有資料。 該函數會傳回 **XRMotionControllerData** 結構。 以下是範例藍圖腳本，它會剖析 XRMotionControllerData 結構以取得手入位置，並在每個聯合的位置繪製一個 debug 座標系統。

![依通道函數連接到行追蹤的 get 注視資料函式藍圖](../images/unreal-hand-tracking-img-03.png)

請務必檢查結構是否有效，以及是否正確。 否則，您可能會在存取位置、旋轉和半徑陣列時取得未定義的行為。

# <a name="425"></a>[4.25](#tab/425)

`EWMRHandKeypoint`列舉會描述手形的骨骼階層。 您可以找到藍圖中列出的每個 keypoint：

![手 Keypoint BP](../images/hand-keypoint-bp.png)

完整的 c + + 列舉如下所示：
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

您可以在 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 資料表中找到每個列舉案例的數值。

### <a name="supporting-hand-tracking"></a>支援手動追蹤

您可以藉由新增 **支援** 手動追蹤 **> Windows Mixed Reality**，在藍圖中使用手邊追蹤：

![手動追蹤 BP](../images/unreal/hand-tracking-bp.png)

`true`如果裝置上支援手形追蹤，而且 `false` 無法使用手形追蹤，此函式就會傳回。

![支援手動追蹤 BP](../images/unreal/supports-hand-tracking-bp.png)

C++：

包含 `WindowsMixedRealityHandTrackingFunctionLibrary.h`。

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>取得追蹤

您可以使用 **GetHandJointTransform** 來傳回手中的空間資料。 資料會每個畫面格更新，但如果您在框架內，則會快取傳回的值。 基於效能考慮，不建議在此函式中使用繁重的邏輯。

![取得手聯合轉換](../images/unreal/get-hand-joint-transform.png)

C++：
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

以下是 GetHandJointTransform 函數參數的細目：

* **手** –可以是使用者的左邊或右邊。
* **Keypoint** –手形的骨骼。
* **轉換** –骨骼基底的座標和方向。 您可以要求下一個骨骼的基底，以取得適用于骨骼結尾的轉換資料。 特殊的秘訣骨骼可提供 distal 的結尾。
* * * 半徑：骨骼基底的半徑。
* * * 傳回值-如果已追蹤此框架，則為 true; 如果未追蹤此骨骼，則為 false。

