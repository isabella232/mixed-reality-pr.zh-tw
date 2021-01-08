---
title: DirectX 中的手部和運動控制器
description: 開始使用在原生 DirectX 應用程式中使用手追蹤和移動控制器的開發人員指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: 手、移動控制器、directx、輸入、全像全像、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 43673602b01a1937953d16fcca9b4c4f4d3fd33a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009538"
---
# <a name="hands-and-motion-controllers-in-directx"></a>DirectX 中的手部和運動控制器

> [!NOTE]
> 本文與舊版 WinRT 原生 Api 相關。  針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)**。

在 Windows Mixed Reality 中，會透過空間輸入 Api 來處理手和 [移動控制器](../../design/motion-controllers.md) 的輸入，這些都是在 [ [輸入](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) ] 命名空間中找到。 這可讓您輕鬆地處理常見的動作，例如 **選取** 在雙手和移動控制器之間按相同方式。

## <a name="getting-started"></a>開始使用

若要存取 Windows Mixed Reality 中的空間輸入，請從 SpatialInteractionManager 介面開始。  您可以藉由呼叫  [SpatialInteractionManager：： GetForCurrentView](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)來存取此介面，通常是在應用程式啟動期間的一段時間。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager 的工作是提供 [SpatialInteractionSources](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)（代表輸入來源）的存取權。  系統中有三種可用的 SpatialInteractionSources。
* **手** 代表使用者偵測到的手。 手來源提供以裝置為基礎的不同功能，範圍從 HoloLens 上的基本手勢，到 HoloLens 2 上的完整明確表述的手動追蹤。 
* **控制器** 代表配對的移動控制器。 移動控制器可提供不同的功能，例如，[選取觸發程式]、[功能表] 按鈕、[功能表]、[touchpads] 和 [thumbsticks]。
* **語音** 代表使用者的語音說話系統偵測到的關鍵字。 例如，每當使用者說「選取」時，此來源就會插入 Select 按下和放開。

來源的每個畫面格資料會以  [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 介面表示。 有兩種不同的方式可存取這項資料，取決於您是否想要在應用程式中使用事件驅動或輪詢型模型。

### <a name="event-driven-input"></a>事件驅動的輸入
SpatialInteractionManager 會提供您的應用程式可接聽的一些事件。  其中一些範例包括   [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、[SourceReleased 和 [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)。

例如，下列程式碼會將名為 MyApp：： OnSourcePressed 的事件處理常式連結至 SourcePressed 事件。  這可讓您的應用程式偵測到任何類型的互動來源上按下。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

此按下的事件會以非同步方式傳送至您的應用程式，並在發生按下時與對應的 SpatialInteractionSourceState。 您的應用程式或遊戲引擎可能會想要立即開始處理，或在輸入處理常式中將事件資料排入佇列。 以下是 SourcePressed 事件的事件處理常式函數，它會檢查是否已按下 [選取] 按鈕。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

上述程式碼只會檢查與裝置上的主要動作對應的「選取」按下動作。 範例包括在 HoloLens 上執行 AirTap，或在移動控制器上提取觸發程式。  「選取」按下代表使用者想要啟用其目標的全像影像。  SourcePressed 事件將會針對一些不同的按鈕和手勢引發，而且您可以檢查 SpatialInteractionSource 上的其他屬性，以測試這些案例。

### <a name="polling-based-input"></a>以輪詢為基礎的輸入
您也可以使用 SpatialInteractionManager 來輪詢每個畫面格中輸入的目前狀態。  若要這樣做，請呼叫 [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 每個畫面格。  此函數會傳回陣列，其中包含每個使用中[SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)的一個[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 。 這表示每個作用中的動作控制器都有一個，每個追蹤的手都有一個，而如果最近從未提到了 ' select ' 命令，則會有一個適用于語音。 然後，您可以檢查每個 SpatialInteractionSourceState 上的屬性，以將輸入驅動至您的應用程式。 

以下是如何使用輪詢方法檢查「選取」動作的範例。 *預測* 變數代表可從 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)取得的 [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)物件。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

每個 SpatialInteractionSource 都有一個識別碼，可讓您用來識別新的來源，並將現有的來源與框架產生相互關聯。  在每次離開時都能取得新的識別碼，然後輸入 FOV，但在會話期間，控制器識別碼仍保持靜態。  您可以使用 SpatialInteractionManager （例如 [SourceDetected](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) 和 [SourceLost](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)）上的事件，以在進入或離開裝置的視圖時回應，或在動作控制器開啟/關閉或配對/不成對時做出反應。

### <a name="predicted-vs-historical-poses"></a>預測與歷程記錄
GetDetectedSourcesAtTimestamp 具有時間戳記參數。 這可讓您要求狀態，並提出預測或歷程記錄的資料，讓您可以將空間互動與其他輸入來源相互關聯。 例如，在目前的框架中呈現手的位置時，您可以傳入 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)所提供的預測時間戳記。 這可讓系統向前預測手的位置，以便與轉譯的畫面格輸出緊密對齊，並將察覺的延遲降至最低。

不過，這類預測的姿勢並不會產生以互動來源為目標的理想指標光線。 例如，按下 [移動控制器] 按鈕時，該事件最多可能需要20毫秒的時間，才能透過藍牙向上到作業系統。 同樣地，在使用者進行手勢手勢之後，某些時間可能會在系統偵測到手勢之前通過，而您的應用程式則會進行輪詢。 當您的應用程式輪詢狀態變更時，用來鎖定的 head 和手也會實際發生在過去。 如果您的目標是將目前的 HolographicFrame 時間戳記傳遞給 GetDetectedSourcesAtTimestamp，則會改為在畫面格顯示時，將姿勢預測到目標光線（未來可能超過20毫秒）。 這種未來的原因適用于 *呈現* 互動來源，但會將我們的時間問題轉譯為 *目標* ，因為使用者的目標是在過去發生。

幸運的是， [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、[SourceReleased 和 [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) 事件會提供與每個輸入事件相關聯的歷程記錄 [狀態](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 。  這會直接包括歷程記錄，以及可透過 [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)取得的歷史時間戳記，以及您可以傳遞給其他 api 來與此事件相互關聯的歷程 [時間戳記](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) 。

這會在每個畫面格的手和控制器呈現和鎖定時，產生下列最佳作法：
* 針對呈現每個畫面格的 **手入/控制器** ，您的應用程式應該在目前畫面格的 photon 時間 **輪詢** 每個互動來源的 **向前預測** 姿勢。  您可以藉由呼叫 [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 每個畫面格，並傳入 [HolographicFrame：： CurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.currentprediction)所提供的預測時間戳記，來輪詢所有的互動來源。
* 針對以按下或放開為目標的站上 **/控制器** ，您的應用程式應該處理已按下/已釋放的 **事件**，並根據該事件的歷程 **記錄** 標頭或手 raycasting。 您可以藉由處理 [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) 或 [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) 事件、從事件引數取得 [State](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 屬性，然後呼叫其 [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 方法，取得此目標光線。

## <a name="cross-device-input-properties"></a>跨裝置輸入屬性
SpatialInteractionSource API 支援具有各式各樣功能的控制器和手追蹤系統。 裝置類型之間有許多常見的功能。 例如，手追蹤和移動控制器都提供「選取」動作和3D 位置。 API 盡可能將這些常見的功能對應至 SpatialInteractionSource 上的相同屬性。  這可讓應用程式更輕鬆地支援廣泛的輸入類型。 下表描述支援的屬性，以及它們如何在輸入類型之間進行比較。

| 屬性 | 描述 | HoloLens (第1代) 手勢 | 移動控制器 | 明確表述的手|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource：：**Handedness**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | 右邊或左邊的/控制器。 | 不支援 | 支援 | 支援 |
| [SpatialInteractionSourceState：：**IsSelectPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 主要按鈕的目前狀態。 | 分流 | 觸發程序 | 寬鬆的空中點 (垂直縮小)  |
| [SpatialInteractionSourceState：：**IsGrasped**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | 抓取按鈕的目前狀態。 | 不支援 | 抓取按鈕 | 縮小或封閉手勢 |
| [SpatialInteractionSourceState：：**IsMenuPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | 功能表按鈕的目前狀態。    | 不支援 | 功能表按鈕 | 不支援 |
| [SpatialInteractionSourceLocation：：**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | 控制器上手或把手位置的 XYZ 位置。 | 掌上位置 | 握住姿勢位置 | 掌上位置 |
| [SpatialInteractionSourceLocation：：**取向**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | 四元數，代表控制器上的手或底姿勢的方向。 | 不支援 | 握住姿勢方向 | 掌上方向 |
| [SpatialPointerInteractionSourcePose：：**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | 指標光線的原點。 | 不支援 | 支援 | 支援 |
| [SpatialPointerInteractionSourcePose：：**ForwardDirection**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | 指標光線的方向。 | 不支援 | 支援 | 支援 |

有些以上的屬性在所有裝置上都無法使用，而且 API 提供了測試此功能的方法。 例如，您可以檢查 [SpatialInteractionSource：： IsGraspSupported](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) 屬性，以判斷來源是否提供理解動作。

### <a name="grip-pose-vs-pointing-pose"></a>底姿勢與指標姿勢

Windows Mixed Reality 支援不同外型規格的移動控制器。  它也支援已明確表述的手追蹤系統。  這些系統中的所有系統都有不同的關聯性，也就是應用程式在使用者手中用來指向或呈現物件的自然「向前」方向之間的關聯性。  為了支援上述所有動作，有兩種類型的3D 表示提供給手追蹤和移動控制器。  第一個是代表使用者手位置的底框姿勢。  第二個是指向姿勢，代表源自于使用者手或控制器的指標光線。 因此，如果您想要轉譯 **使用者的手** 或 **保留在使用者手中的物件**（例如寶劍或機槍），請使用底框姿勢。 如果您想要從控制器或手中 raycast （例如，當使用者是 * * 指向 UI 時），請使用指標姿勢。

您可以透過 [SpatialInteractionSourceState：:P 屬性 r) ：： TryGetLocation ( ... )](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_)來存取此框 **姿勢**。其定義如下：
* 把手 **位置**：自然地按住控制器時的棕櫚距心，向左或向右調整以將位置置中置中。
* 底 **圖方向的右軸**：當您完全開啟手來形成平面的5形姿勢時，您的掌上光 (的光線會從左至右向前復原，從右邊的棕櫚) 
* 底圖 **方向的向前軸**：當您關閉手部分 (時，如同按住控制器) 一樣，也就是由非拇指手指所形成的電子管「轉寄」的光線。
* 底圖 **方向的向上軸**：右邊和向前定義所隱含的向上軸。

您可以透過 [SpatialInteractionSourceState：:P 屬性 r) ：： TryGetLocation ( ... ) ：： SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或 [SpatialInteractionSourceState：： TryGetPointerPose ( ... ) ：： TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)來存取 **指標姿勢**。

## <a name="controller-specific-input-properties"></a>控制器特定的輸入屬性
針對控制器，SpatialInteractionSource 具有具有額外功能的控制器屬性。
* **HasThumbstick：** 若為 true，則控制器具有操縱杆。 檢查 SpatialInteractionSourceState 的 [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) 屬性，以取得 (ThumbstickX 和 ThumbstickY) 的操縱杆 x 和 y 值，以及其按下的狀態 (IsThumbstickPressed) 。
* **HasTouchpad：** 若為 true，表示控制器有一個觸控板。 檢查 SpatialInteractionSourceState 的 ControllerProperties 屬性，以取得 (TouchpadX 和 TouchpadY) 的 [觸控軸 x] 和 [y] 值，並知道使用者是否觸及板 (IsTouchpadTouched) ，以及是否按下觸控板， (IsTouchpadPressed) 。
* **SimpleHapticsController：** 控制器的 SimpleHapticsController API 可讓您檢查控制器的 haptics 功能，也可讓您控制 haptic 的意見反應。

觸控板和操縱杆的範圍為-1 到1，兩個軸 (從下到上，以及從左至右) 。 使用 SpatialInteractionSourceState：： SelectPressedValue 屬性存取的類比觸發程式範圍，範圍為0到1。 值1與 IsSelectPressed 等於 true 的關聯性;任何其他值與 IsSelectPressed 的關聯性等於 false。

## <a name="articulated-hand-tracking"></a>清楚的手追蹤
Windows Mixed Reality API 會提供對已進行的明確追蹤支援，例如 HoloLens 2。 明確的手追蹤可用來在您的應用程式中執行直接操作和點認可輸入模型。 它也可以用來撰寫完全自訂的互動。

### <a name="hand-skeleton"></a>手形基本架構
明確說明的手追蹤提供25個聯合基本架構，可啟用許多不同類型的互動。  此基本架構提供索引/中間/環形/小手指的五個接點、適用于 thumb 的四個接點，以及一個手腕的接點。  手腕聯合會作為階層的基礎。 下圖說明基本架構的版面配置。

![手形基本架構](images/hand-skeleton.png)

在大部分的情況下，每個聯合都會根據它所代表的骨骼來命名。  因為每個聯合都有兩個骨骼，所以我們會根據該位置的子骨骼，使用命名每個聯合的慣例。  子骨骼是從手腕進一步定義為骨骼。  例如，"Index 近端" 聯合包含 Index 近端骨骼的開始位置，以及該骨骼的方向。  它不包含骨骼的結束位置。  如果需要，您可以從階層中的下一個聯合（「索引中繼」聯合）取得它。

除了25個階層式接點之外，系統也提供了一種掌上接點。  手掌通常不會被視為框架結構的一部分。 它只是為了方便您取得手的整體位置和方向。

每個聯合都會提供下列資訊：

| 名稱 | 描述 |
|--- |--- |
|位置 | 聯合的3D 位置，適用于任何要求的座標系統。 |
|Orientation | 適用于骨骼的3D 方向，適用于任何要求的座標系統。 |
|半徑 | 面板在聯合位置的距離。 適用于微調依賴手指寬度的直接互動或視覺效果。 |
|精確度 | 提供提示，告訴您系統如何確保系統對這種聯合資訊的感覺。 |

您可以透過 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)上的函式來存取手形基本架構資料。  函數稱為 [TryGetHandPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)，它會傳回名為 [HandPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose)的物件。  如果來源不支援明確的手，則此函式會傳回 null。  一旦有了 HandPose，您就可以使用您感興趣的聯合名稱來呼叫 [TryGetJoint](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)，以取得目前的聯合資料。  資料會以 [JointPose](https://docs.microsoft.com//uwp/api/windows.perception.people.jointpose) 結構的形式傳回。  下列程式碼會取得索引手指提示的位置。 變數 *currentState* 代表 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)的實例。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>手上網格

明確 deformable 的手追蹤 API 允許完全三角形的手網格。  此網狀架構可以即時 deform，以及適用于視覺效果和先進的物理技術。  若要存取手形網格，您必須先在[SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)上呼叫[TryCreateHandMeshObserverAsync](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)來建立[HandMeshObserver](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver)物件。  這只需要針對每個來源執行一次，通常是您第一次看到它時。  這表示您會呼叫此函式，以在每次有手進入 FOV 時建立 HandMeshObserver 物件。  這是非同步函式，因此您必須在這裡處理一些並行處理。  一旦可以使用，您就可以呼叫 [GetTriangleIndices](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)，向 HandMeshObserver 物件要求三角形索引緩衝區。  索引不會變更框架的框架，因此您可以取得這一次，並在來源的存留期內加以快取。  以順時針的纏繞順序提供索引。

下列程式碼會啟動卸離的 std：： thread 以建立網格觀察器，並在有可用的網格觀察者時，將索引緩衝區解壓縮。  它會從名為 *currentState* 的變數開始，也就是代表追蹤手的 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 實例。

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
啟動卸離的執行緒只是一個處理非同步呼叫的選項。  或者，您可以使用 c + + 所支援的新 [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 功能/winrt

有了 HandMeshObserver 物件之後，您應該在其對應的 SpatialInteractionSource 作用中的持續時間內保存該物件。  然後，您可以藉由呼叫 [GetVertexStateForPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) 並傳入代表您想要頂點之姿勢的 [HandPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose) 實例，要求它提供最新的頂點緩衝區來代表手。  緩衝區中的每個頂點都有位置和一般。  以下是如何取得手中目前頂點集合的範例。  如同之前一樣， *currentState* 變數代表 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)的實例。

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

相對於基本架構接點，手形 API 不允許您指定頂點的座標系統。  相反地， [HandMeshVertexState](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshvertexstate) 會指定在中提供頂點的座標系統。  然後您可以藉由呼叫 [TryGetTransformTo](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) 並指定您想要的座標系統，來取得網格轉換。  每當您使用頂點時，都必須使用這個網格轉換。  這種方法可減少 CPU 額外負荷，尤其是當您只是為了轉譯而使用網格時更是如此。

## <a name="gaze-and-commit-composite-gestures"></a>注視和認可複合手勢
針對使用「注視認可」輸入模型的應用程式，特別是在 HoloLens (第一代) 上，空間輸入 API 會提供選擇性的 [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) ，可用來啟用以「選取」事件為基礎的複合手勢。  藉由將互動從 SpatialInteractionManager 路由傳送至全像 SpatialGestureRecognizer，應用程式可以跨手、語音和空間輸入裝置，以一致的方式來偵測點擊、保存、操作和導覽事件，而不需要手動處理按下和釋出。

SpatialGestureRecognizer 只會在您要求的手勢集合之間進行最短的混淆。 例如，如果您只要求點一下，使用者可能會在想要的時間點按下手指，且仍然會出現點一下。 如果您要求點一下和按住，則在大約第二個按住手指時，手勢會升階為按住，且不會再進行點碰。

若要使用 SpatialGestureRecognizer，請處理 SpatialInteractionManager 的 [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) 事件，並抓取該處公開的 SpatialPointerPose。 使用這個姿勢的使用者前端光線來與使用者的環境內的全像影像和介面網格交集，以判斷使用者想要與之互動。 然後，使用其 [CaptureInteraction](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) 方法，將事件引數中的 SpatialInteraction 路由傳送至目標全像 SpatialGestureRecognizer。 這會根據在建立時或由[TrySetGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)在該辨識器上設定的[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) ，開始解讀該互動。

在 HoloLens (第一代) 上，互動和手勢應衍生自使用者的標頭，而不是在手邊的位置呈現或互動。 一旦互動開始之後，就可以使用該手的相對運動來控制手勢，如同操作或導覽手勢一樣。

## <a name="see-also"></a>請參閱
* [DirectX 中的頭部和眼睛目光](gaze-in-directx.md)
* [直接操作輸入模型](../../design/direct-manipulation.md)
* [點認可輸入模型](../../design/point-and-commit.md)
* [注視和認可輸入模型](../../design/gaze-and-commit.md)
* [運動控制器](../../design/motion-controllers.md)
