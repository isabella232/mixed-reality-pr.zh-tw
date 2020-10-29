---
title: Unreal 中的手勢追蹤
description: 說明如何在 Unreal 中使用手動追蹤
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、手追蹤、Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、混合現實、開發、功能、檔、指南、全息全像遊戲開發
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91676901"
---
# <a name="hand-tracking-in-unreal"></a>Unreal 中的手勢追蹤

## <a name="overview"></a>概觀

手追蹤系統會使用某人的手掌和手指做為輸入。 您可以在程式碼中取得每個手指的位置和旋轉、整個掌，甚至手手勢。 

## <a name="hand-pose"></a>手姿勢

手姿勢可讓您追蹤作用中使用者的手和手指，並將其作為輸入，您可以透過藍圖和 c + + 來存取。 您可以在 Unreal 的 [HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API 中找到更多的技術詳細資料。 Unreal API 會將資料傳送為座標系統，並與 Unreal 引擎同步處理刻度。

### <a name="understanding-the-bone-hierarchy"></a>瞭解骨骼階層

`EWMRHandKeypoint`列舉會描述手形的骨骼階層。 您可以找到藍圖中列出的每個 keypoint：

![手 Keypoint BP](images/hand-keypoint-bp.png)

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

您可以在 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 資料表中找到每個列舉案例的數值。 下圖顯示具有相符列舉案例的整個手姿勢配置：

![手形基本架構](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>支援手動追蹤

您可以藉由新增 **支援** 手動追蹤 **> Windows Mixed Reality** ，在藍圖中使用手邊追蹤：

![手動追蹤 BP](images/unreal/hand-tracking-bp.png)

`true`如果裝置上支援手形追蹤，而且 `false` 無法使用手動追蹤，此函式就會傳回。

![支援手動追蹤 BP](images/unreal/supports-hand-tracking-bp.png)

C++： 

包含 `WindowsMixedRealityHandTrackingFunctionLibrary.h`。

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>取得追蹤
您可以使用 **GetHandJointTransform** 來傳回手中的空間資料。 資料會每個畫面格更新，但如果您在框架內，則會快取傳回的值。 基於效能考慮，不建議在此函式中使用繁重的邏輯。 

![取得手聯合轉換](images/unreal/get-hand-joint-transform.png)
 
C++：
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

函數參數細目：

* **手形** –是使用者的左邊或右邊
* **Keypoint** –手形的骨骼。 
* **轉換** –骨骼基底的座標和方向。 您可以要求下一個骨骼的基底，以取得適用于骨骼結尾的轉換資料。 特殊的秘訣骨骼可提供 distal 的結尾。 
* **半徑** ：骨骼基底的半徑。
* 傳回 **值** -如果已追蹤此框架，則為 true; 如果未追蹤此骨骼，則為 false。

## <a name="hand-live-link-animation"></a>手實況連結動畫
使用 [即時連結外掛程式](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)可對動畫公開手。

如果已啟用 Windows Mixed Reality 和即時連結外掛程式： 
1. 選取 [ **Window > 即時連結** ] 以開啟 [即時連結編輯器] 視窗。 
2. 按一下 [ **來源** ] 並啟用 **Windows Mixed Reality 手追蹤來源**

![即時連結來源](images/unreal/live-link-source.png)
 
啟用來源並開啟動畫資產之後，展開 [ **預覽場景** ] 索引標籤中的 [ **動畫** ] 區段，也會看到其他選項 (詳細資料位於 Unreal 的即時連結檔中-當外掛程式在 Beta 版中，此程式可能會在稍後) 變更。

![即時連結動畫](images/unreal/live-link-animation.png)
 
手形動畫階層與中的相同 `EWMRHandKeypoint` 。 動畫可以使用 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 重定目標：

![即時連結動畫2](images/unreal/live-link-animation2.png)
 
它也可以在編輯器中進行子類別化：

![即時連結重新對應](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>存取手形網格資料

![手上網格](images/unreal/hand-mesh.png)

在您可以存取手中的資料之前，您必須：
- 選取您的 **ARSessionConfig** 資產，展開 [ **AR 設定-> 世界對應** 設定]，然後核取 [ **從追蹤的幾何產生網格資料** ]。 

以下是預設的網格參數：

1.  使用網格資料進行遮蔽
2.  產生網格資料的衝突
3.  產生網格資料的 Nav 網格
4.  轉譯線框中的網格資料-debug 參數，可顯示產生的網格

這些參數值會當做空間對應網格和手邊網格預設值使用。 您可以隨時在任何網格的藍圖或程式碼中變更它們。

### <a name="c-api-reference"></a>C + + API 參考 
用 `EEARObjectClassification` 來尋找所有可追蹤物件中的手網格值。
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

當系統偵測到任何可追蹤物件（包括手形網格）時，會呼叫下列委派。 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

請確定您的委派處理常式遵循以下的函數簽章：

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

您可以透過下列步驟存取網格資料  `UARTrackedGeometry::GetUnderlyingMesh` ：

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a>藍圖 API 參考

若要在藍圖中使用手形網格：
1. 將 **ARTrackableNotify** 元件新增至藍圖執行者

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
2. 移至 [ **詳細資料** ] 面板，然後展開 [ **事件** ] 區段。 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
3. 在事件圖中使用下列節點覆寫新增/更新/移除追蹤幾何：

![ARTrackable 通知時](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>手光

您可以在 c + + 和藍圖中使用手光線作為指標裝置，以公開 [SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API。

請務必注意，因為所有函式的結果都會變更每個畫面格，所以它們全都變成可呼叫。 如需有關純和 impure 或可呼叫函式的詳細資訊，請參閱藍圖的使用者 guid [功能](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

若要在藍圖中使用手片，請搜尋 **WINDOWS MIXED REALITY HMD** 下的任何動作：

![手中的最佳光線](images/unreal/hand-rays-bp.png)
 
若要以 c + + 存取它們，請將加入 `WindowsMixedRealityFunctionLibrary.h` 至呼叫程式碼檔案的頂端。

### <a name="enum"></a>列舉
您也可以存取 **EHMDInputControllerButtons** 下的輸入案例，此案例可用於藍圖：

![輸入控制器按鈕](images/unreal/input-controller-buttons.png)

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
    * 您可以藉由點一下、注視和認可，或藉由在啟用 [語音輸入](unreal-voice-input.md) 的情況下說出「選取」，在 HoloLens 2 中觸發事件。 
* **理解** 使用者觸發的理解事件。 
    * 在 HoloLens 2 中，您可以關閉使用者的手指，以觸發此事件。 

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
* 已 **追蹤** --已完整追蹤手

### <a name="struct"></a>結構
PointerPoseInfo 結構可以提供下列資料的資訊：
* **原點** –手的原點
* **方向** –手形方向
* **向上** –向上向量
* **方向** –方向四元數 
* **追蹤狀態** -目前的追蹤狀態

您可以透過藍圖來存取，如下所示：

![指標姿勢資訊 BP](images/unreal/pointer-pose-info-bp.png)

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

![取得指標姿勢資訊](images/unreal/get-pointer-pose-info.png)

C++： 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. 如果在目前的框架中 Grasped 手， **Grasped 會** 傳回 true。

藍圖：

![為 Grasped BP](images/unreal/is-grasped-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. 如果使用者在目前的框架中觸發了 Select， **則 [已按下] 會** 傳回 true。

藍圖：

![選取 [按下 BP]](images/unreal/is-select-pressed-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **按一下按鈕時** ，如果在目前的框架中觸發事件或按鈕，則會傳回 true。

藍圖：

![按鈕是否按下 BP](images/unreal/is-button-clicked-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **取得控制器追蹤狀態** 會傳回目前框架中的追蹤狀態。

藍圖：

![取得控制器追蹤狀態 BP](images/unreal/get-controller-tracking-status-bp.png)

C++：
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>軌跡

Hololens 2 可以追蹤空間手勢，這表示您可以將這些手勢視為輸入。 您可以在 [HoloLens 2 基本使用](https://docs.microsoft.com/hololens/hololens2-basic-usage) 方式檔中找到手勢的詳細資料。

您可以在 [ **Windows Mixed Reality 空間輸入** ] 下找到藍圖函式，然後在呼叫程式碼檔案中加入 c + + 函式 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 。

![捕捉手勢](images/unreal/capture-gestures.png)

### <a name="enum"></a>列舉
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
藍圖： 

![手勢類型](images/unreal/gesture-type.png)

C++：
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>函式
您可以使用函數來啟用和停用手勢捕捉 `CaptureGestures` 。 當已啟用的手勢引發輸入事件時， `true` 如果手勢捕捉成功，則函式會傳回，如果發生錯誤，則會傳回 `false` 。

藍圖：

![捕捉手勢 BP](images/unreal/capture-gestures-bp.png)

C++：
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

以下是重要事件，您可以在藍圖和 c + +：關鍵事件中找到這些事件 ![](images/unreal/key-events.png)

![關鍵事件2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unreal 開發檢查點旅程，您將在探索 MRTK 核心構成要素。 您可以從這裡繼續進行下一個組建區塊： 

> [!div class="nextstepaction"]
> [本機空間錨點](unreal-spatial-anchors.md)

或跳至混合的現實平臺功能和 Api：

> [!div class="nextstepaction"]
> [HoloLens 相機](unreal-hololens-camera.md)

您隨時都可以回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks) 。