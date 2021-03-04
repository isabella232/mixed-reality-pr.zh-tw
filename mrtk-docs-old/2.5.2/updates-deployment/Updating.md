---
title: 更新
description: 從較低版本的 MRTK 遷移的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 5616da967774d93b6d356f588467197b8f1267a0
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781287"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a>更新 Microsoft Mixed Reality 工具組

- [升級至新版本的 MRTK](#upgrading-to-a-new-version-of-mrtk)
- [2.3.0 至2.4。0](#updating-230-to-240)
- [2.2.0 至2.3。0](#updating-220-to-230)
- [2.1.0 至2.2。0](#updating-210-to-220)
- [2.0.0 至2.1。0](#updating-200-to-210)
- [RC2 至2.0。0](#updating-rc2-to-200)

## <a name="upgrading-to-a-new-version-of-mrtk"></a>升級至新版本的 MRTK

*強烈建議您在取得 MRTK 更新 [](../features/tools/MigrationWindow.md)* 以自動修正，並從已淘汰的元件升級並進行升級時，執行遷移工具以進行中斷變更。 遷移工具是 **工具** 套件的一部分。

下列指示說明2.5.0 升級路徑的2.4.0。 如果您的專案是在2.3.0 或更早版本上，請閱讀各 [版本之間](#updating-230-to-240) 的變更，以瞭解升級路徑，或閱讀先前版本 [的指示](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) ，以進行版本版本的升級。

### <a name="unity-asset-unitypackage-files"></a>Unity 資產 (. unitypackage) 檔案

如需最順暢的升級路徑，請使用下列步驟。

1. 如果您在升級步驟中的任何時間點遇到任何阻礙，請儲存目前專案的複本。
1. 關閉 Unity
1. 在 [ *資產* ] 資料夾內，刪除下列 **MRTK** 資料夾以及其 (專案可能沒有所有列出的資料夾) 
    - MRTK/核心
    - MRTK/範例
    - MRTK/擴充功能
    > [!NOTE]
    > 如果已安裝其他延伸模組，請在刪除這些資料夾之前進行備份。
    - MRTK/提供者
    - MRTK/SDK
    - MRTK/服務
    - MRTK/工具
    > [!IMPORTANT]
    > 請勿刪除 **MixedRealityToolkit 產生** 的資料夾或其中繼檔案。
1. 刪除連結 **庫** 資料夾
    > [!IMPORTANT]
    > 某些 Unity 工具（例如 Unity Collaboration）會將設定資訊儲存至程式庫資料夾。 如果使用執行這項工作的工具，請先從程式庫複製工具的 [資料] 資料夾，然後再進行刪除，然後在重新產生程式庫之後將其還原。
1. 在 Unity 中重新開啟專案
1. 匯入新的 unity 套件
    - 基礎- _先匯入此套件_
    - 工具
    -  (選用) 擴充功能
    > [!NOTE]
    > 如果已安裝其他延伸模組，則可能需要重新匯入。
    -  (選擇性) 範例
1. 關閉 Unity 並刪除連結 **庫** 資料夾 (先閱讀以下的附注！ ) 。 必須執行此步驟，才能強制 Unity 重新整理其資產資料庫，並協調現有的自訂設定檔。
1. 啟動 Unity，然後針對專案中的每個場景
    - 從階層中刪除 **MixedRealityToolkit** 和 **MixedRealityPlayspace**（如果有的話）。 這將會刪除主要相機，但會在下一個步驟中重新建立。 如果已手動變更主要相機的任何內容，則在建立新的相機之後，必須手動重新套用這些屬性。
    - 選取 **MixedRealityToolkit-> 新增至場景並設定**
    - 選取 **MixedRealityToolkit-> 公用程式-> update-> 控制器對應設定檔** (只需要進行一次) -這會以更新的座標軸和資料更新任何自訂控制器對應設定檔，同時讓您的自訂指派輸入動作保持不變
1. 執行 [遷移工具](../features/tools/MigrationWindow.md) 並在 *完整的專案* 上執行工具，以確保您的所有程式碼都更新為最新版本。
   [遷移] 視窗包含許多不同的遷移處理常式，每個處理常式都必須自行執行。 此步驟包含：
   - 從 [ **遷移處理常式選取專案** ] 下拉式清單中，選取第一個遷移處理常式。
   - 按一下 [完整專案] 按鈕。
   - 按一下 [新增要遷移的完整專案] 按鈕 (這會掃描整個專案以取得要遷移) 的物件。
   - 按一下 [遷移] 按鈕，如果找到任何 migrateable 物件，則應啟用此按鈕。
   - 針對下拉式清單中的每個遷移處理常式重複上述三個步驟。
      (看到 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) ，其中涵蓋可在未來版本中簡化此遷移程式的工作) 

## <a name="updating-230-to-240"></a>將2.3.0 更新為2.4。0

[資料夾重新命名](#folder-renames-in-240) 
[API 變更](#api-changes-in-240)

### <a name="folder-renames-in-240"></a>2.4.0 中的資料夾重新命名

MixedRealityToolkit 資料夾已重新命名並移至2.4 版中的通用階層。 如果應用程式使用硬式編碼路徑來 MRTK 資源，則必須根據下表進行更新。

| 上一個資料夾 | 新增資料夾 |
| --- | --- |
| MixedRealityToolkit | MRTK/核心 |
| MixedRealityToolkit 範例 | MRTK/範例 |
| MixedRealityToolkit 副檔名 | MRTK/擴充功能 |
| MixedRealityToolkit。提供者 | MRTK/提供者 |
| MixedRealityToolkit SDK | MRTK/SDK |
| MixedRealityToolkit 服務 | MRTK/服務 |
| MixedRealityToolkit。測試 | MRTK/測試 |
| MixedRealityToolkit 工具 | MRTK/工具 |

> [!IMPORTANT]
> `MixedRealityToolkit.Generated`包含客戶產生的檔案，且保持不變。

### <a name="eye-gaze-setup-in-240"></a>2.4.0 中的眼睛設定

此版本的 MRTK 會修改眼睛設定所需的步驟。 您可以在輸入指標設定檔的注視設定中找到 [ _IsEyeTrackingEnabled_ ] 核取方塊。 核取此方塊將會啟用以眼睛為基礎的眼睛，而不是預設的標頭。

如需有關這些變更的詳細資訊，以及適用于眼睛追蹤設定的完整指示，請參閱 [眼睛追蹤](../features/eye-tracking/EyeTracking_BasicSetup.md) 文章。

### <a name="eye-gaze-pointer-behavior-in-240"></a>2.4.0 中的眼睛指標行為

眼睛的預設指標行為已經過修改，以符合標頭的預設指標行為。 一旦偵測到手中，就會自動抑制眼睛指標。 出現「選取」之後，眼睛指標將會再次顯示。

有關注視和手的詳細資訊，請參閱 [眼睛和手](../features/eye-tracking/EyeTracking_EyesAndHands.md#how-to-keep-gaze-pointer-always-on) 中的文章。

### <a name="api-changes-in-240"></a>2.4.0 中的 API 變更

**自訂控制器類別**

自訂控制器類別先前必須定義 `SetupDefaultInteractions(Handedness)` 。 此方法已在2.4 中淘汰，因為 handedness 參數對控制器類別的 handedness 是多餘的。 新方法沒有任何參數。 此外，許多控制器類別的定義方式和 () 的方式相同 `AssignControllerMappings(DefaultInteractions);` ，因此完整的呼叫已細分成 `BaseController` 並進行選擇性的覆寫，而不是必要的。

**眼睛眼屬性**

`UseEyeTracking`從執行的屬性 `GazeProvider` 已重新 `IMixedRealityEyeGazeProvider` 命名為 `IsEyeTrackingEnabled` 。

如果您先前已執行此操作 .。。

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

現在就完成了 .。。

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**WindowsApiChecker 屬性**

下列 WindowsApiChecker 屬性已標示為過時。 請使用 `IsMethodAvailable` 、 `IsPropertyAvailable` 或 `IsTypeAvailable` 。

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

基於未來的 API 合約版本，不打算將屬性新增至 WindowsApiChecker。

**GltfMeshPrimitiveAttributes 唯讀**

Gltf 網格基本屬性是用來設定的，現在它們是唯讀的。 還原序列化時，它們的值會設定一次。

### <a name="custom-button-icon-migration"></a>自訂按鈕圖示遷移

先前的自訂按鈕圖示需要將新的材質指派給按鈕的四轉譯器。 這已不再是必要的，建議您將自訂圖示材質移至 IconSet。 系統會保留現有的自訂材質和圖示。 不過，在升級之前，它們將會較不理想。
若要將專案中所有按鈕的資產升級為新的建議格式，請使用 ButtonConfigHelperMigrationHandler。
 (混合現實工具組-> 公用程式-> 的遷移視窗-> 的遷移處理常式選取範圍-> MixedReality) 

![升級視窗對話方塊](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

如果在遷移期間于預設的圖示集中找不到圖示，則會在 MixedRealityToolkit 中建立自訂圖示集。產生/CustomIconSets。 對話方塊會指出已發生此情況。

![自訂圖示通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>將2.2.0 更新為2.3。0

- [API 變更](#api-changes-in-230)

### <a name="api-changes-in-230"></a>2.3.0 中的 API 變更

**ControllerPoseSynchronizer**

私用 ControllerPoseSynchronizer. handedness 欄位已標示為過時。 這應該會對應用程式造成最大影響，因為欄位不會顯示在其類別之外。

已 ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)) 移除 public ControllerPoseSynchronizer. Handedness 屬性的 setter。

**適用于 Unity 的 MSBuild**

此版本的 MRTK 使用與舊版 MSBuild for Unity 的較新版本。 在專案載入期間，如果較舊的版本列在 Unity 套件管理員資訊清單中，則會顯示 [設定] 對話方塊，並核取 [啟用 MSBuild for Unity] 選項。 應用程式將會執行升級。

**ScriptingUtilities**

ScriptingUtilities 類別已標示為已淘汰，且已由 ScriptUtilities 取代，位於 MixedReality 元件中。 新的類別會改善先前的行為，並加入移除腳本定義的支援。

雖然現有的程式碼在版本2.3.0 中仍可繼續運作，但建議您更新至新的類別。

**ShellHandRayPointer**

ShellHandRayPointer 類別的 lineRendererSelected 和 lineRendererNoTarget 成員已由 lineMaterialSelected 和 lineMaterialNoTarget 分別取代 ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)) 。

請將 lineRendererSelected 取代為 lineMaterialSelected 和/或 lineRendererNoTarget with lineMaterialNoTarget，以解決編譯錯誤。

**空間觀察者讓 microsoft.systemforcrossdomainidentitymanagement.iprovider.startupbehavior**

以類別為基礎的空間觀察者現在會在 `BaseSpatialObserver` 重新啟用 ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)) 時，接受讓 microsoft.systemforcrossdomainidentitymanagement.iprovider.startupbehavior 的值。

不需要進行任何變更，即可充分利用此修正。

**UX 控制項 prefabs 已更新為使用 PressableButton**

下列 prefabs 現在使用 PressableButton 元件，而不是 TouchHandler 接近互動 ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070)) 

- AnimationButton
- 按鈕
- ButtonHoloLens1
- ButtonHoloLens1Toggle
- 核取方塊
- RadialSet
- ToggleButton
- ToggleSwitch
- UnityUIButton
- UnityUICheckboxButton
- UnityUIRadialButton
- UnityUIToggleButton

應用程式程式碼可能會因為這種變更而需要更新。

**WindowsMixedRealityUtilities 命名空間**

WindowsMixedRealityUtilities 的命名空間已從 MixedReality 變更為 WindowsMixedReality， [#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989))  (的命名空間。

請更新 #using 語句，以解決編譯錯誤。

## <a name="updating-210-to-220"></a>將2.1.0 更新為2.2。0

- [API 變更](#api-changes-in-220)

### <a name="api-changes-in-220"></a>2.2.0 中的 API 變更

**IMixedRealityBoundarySystem。 Contains**

這個方法先前採用特定的 Unity 定義實驗列舉。 它現在會採用與 Unity 列舉完全相同的 MRTK 定義列舉。 這種變更有助於為 Unity 未來的界限 Api 做好 MRTK 準備。

**MixedRealityServiceProfileAttribute**

為了更清楚地描述支援設定檔的需求，已更新 MixedRealityServiceProfileAttribute 以新增選擇性的排除類型集合。 作為這項變更的一部分，ServiceType 屬性已從類型變更為類型 []，並已重新命名為 RequiredTypes。

第二個屬性（ExcludedTypes）也已加入。

## <a name="updating-200-to-210"></a>將2.0.0 更新為2.1。0

- [API 變更](#api-changes-in-210)
- [設定檔變更](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>2.1.0 中的 API 變更

**BaseNearInteractionTouchable**

已 `BaseNearInteractionTouchable` 修改為將 `OnValidate` 方法標示為虛擬。 延伸 `BaseNearInteractionTouchable` (例如：) 的類別已 `NearInteractionTouchableUnityUI` 更新以反映此變更。

**ColliderNearInteractionTouchable**

`ColliderNearInteractionTouchable` 類別已被取代。 請更新要使用的程式碼參考 `BaseNearInteractionTouchable` 。

**IMixedRealityMouseDeviceManager**

**_添加_**

`IMixedRealityMouseDeviceManager` 已新增 `CursorSpeed` 並具有 `WheelSpeed` 屬性。 這些屬性可讓應用程式指定乘數，也就是資料指標和滾輪的速度會分別調整。

這是中斷性變更，需要修改現有的滑鼠裝置管理員。

>[!NOTE]
>這項變更與版本2.0.0 不相容。

**_廢棄_**

`MouseInputProfile`屬性已標示為已淘汰，將會從 Microsoft 混合現實工具組的未來版本中移除。 建議應用程式程式碼不再使用此屬性。

**互動**

以下是已淘汰的方法和屬性，將會從未來版本的 Microsoft Mixed Reality 工具組中移除。 建議您根據 [過時] 屬性中包含的指導方針來更新應用程式程式碼，並在主控台中顯示。

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

**NearInteractionTouchableSurface**

`NearInteractionTouchableSurface`類別已加入，現在可作為和的基類 `NearInteractionTouchable` `NearInteractionTouchableUnityUI` 。

### <a name="profile-changes-in-210"></a>2.1.0 中的設定檔變更

**手動追蹤設定檔**

手網格和聯合視覺效果現在有個別的編輯器和播放機設定。 已更新手形追蹤設定檔，以允許將這些視覺效果設定為;Nothing、所有專案、編輯器或播放機。

![手形視覺效果模式](../features/images/release-notes/HandTrackingVisualizationModes.png)

自訂的手追蹤設定檔可能需要更新，才能與版本2.1.0 正常搭配運作。

>[!NOTE]
>這項變更與版本2.0.0 不相容。

**輸入模擬設定檔**

輸入模擬系統已升級，這會變更輸入模擬設定檔中的幾項設定。 某些變更無法自動遷移，而使用者可能會發現設定檔使用預設值。

1. 設定檔中的所有 KeyCode 和滑鼠按鍵系結都已取代為泛型 `KeyBinding` 結構，此結構會儲存系結類型 (按鍵或滑鼠) 以及實際的系結程式碼， (KeyCode 或滑鼠按鍵編號分別) 。 此結構有自己的偵測器，可允許統一顯示並提供「自動系結」工具，只要按下個別的按鍵即可快速設定按鍵系結，而不需要從大型的下拉式清單中選取。

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` 先前已包含在 `MouseLookButton` 列舉中 `InputSimulationMouseButton.Focused` ，它現在是個別的選項。 啟用時，在放開按鈕之後，相機會繼續以滑鼠旋轉，直到按下 esc 鍵為止。
1. `HandDepthMultiplier` 預設值已從0.1 降至0.03，以配合輸入模擬的某些變更。 如果相機在滾動時移動速度太快，請嘗試降低此值。
1. 旋轉手的按鍵已經被移除，手旋轉現在也是由滑鼠所控制。 按住 `HandRotateButton` (Ctrl) ，以及左/右操作金鑰 (LShift/空格鍵) 將會啟用手旋轉。
1. 已將新的軸 "上下按鈕" 引進至輸入軸清單。 這會控制垂直和預設為 Q/E 按鍵以及控制器觸發程式按鈕的相機移動。

如需這些變更的詳細資訊，請參閱「 [輸入模擬服務](../features/input-simulation/InputSimulationService.md) 」一文。

**滑鼠資料提供者設定檔**

滑鼠資料提供者設定檔已經更新，以公開新的 `CursorSpeed` 和 `WheelSpeed` 屬性。 現有的自訂設定檔會自動提供預設值。 儲存設定檔時，將會保存這些新值。

**控制器對應設定檔**

某些軸和輸入類型已在2.1.0 中更新，尤其是在 OpenVR 平臺上。 升級時，請務必選取 [ **MixedRealityToolkit-> 公用程式-> 更新 > 控制器對應設定檔** ]。 這會將任何自訂控制器對應設定檔更新為更新的座標軸和資料，同時讓您的自訂指派輸入動作保持不變。

## <a name="updating-rc2-to-200"></a>正在將 RC2 更新至2.0。0

在 Microsoft Mixed Reality 工具組的 RC2 與2.0.0 版本之間，變更可能會影響現有的專案。 本檔將說明這些變更，以及如何將專案更新至2.0.0 版本。

- [API 變更](#api-changes-in-200)
- [元件名稱變更](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>2.0.0 中的 API 變更

自 RC2 發行以來，有許多 API 變更，包括可能會中斷現有專案的部分。 下列章節說明 RC2 與2.0.0 版本之間的變更。

**MixedRealityToolkit**

MixedRealityToolkit 物件上的下列公用屬性已被取代。

- `RegisteredMixedRealityServices` 不再包含已註冊延伸模組服務和資料提供者的集合。

若要存取擴充服務，請使用 `MixedRealityServiceRegistry.TryGetService<T>` 。 若要存取資料提供者，請將服務實例轉換為 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 和使用 `GetDataProvider<T>` 。

使用 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 或 [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) 取代下列已被取代的屬性

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

[`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)類別是靜態系統存取子的取代 (例如在物件中找到的 BoundarySystem) `MixedRealityToolkit` 。

>[!IMPORTANT]
>`MixedRealityToolkit`系統存取子在版本2.0.0 中已被取代，而且將在 MRTK 的未來版本中移除。

下列程式碼範例說明舊的和新的模式。

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

使用新的 CoreSystem 類別可確保您的應用程式程式碼在您將應用程式變更為使用不同的服務註冊機構時，不需要更新 (例如：其中一個實驗性服務管理員) 。

**IMixedRealityRaycastProvider**

新增 IMixedRealityRaycastProvider 之後，就會變更輸入系統設定檔。 如果您有自訂設定檔，當您執行應用程式時，可能會收到下列影像中的錯誤。

![選取 Raycast 提供者錯誤詳細資料](../features/images/release-notes/UnableToRegisterRaycastProvider.png)

若要修正這些問題，請將 IMixedRealityRaycastProvider 實例新增至輸入系統設定檔。

![選取 Raycast 提供者](../features/images/release-notes/SelectRaycastProvider.png)

**事件系統**

- `IMixedRealityEventSystem`舊的 API 方法 `Register` 和 `Unregister` 都已標示為過時。 它們是為了回溯相容性而保留。
- `InputSystemGlobalListener` 已標示為過時。 其功能尚未變更。
- `BaseInputHandler` 基類已從變更 `InputSystemGlobalListener` 為 `InputSystemGlobalHandlerListener` 。 這是的任何子代的重大變更 `BaseInputHandler` 。

**_變更背後的動機_**

舊的事件系統 API `Register` 可能 `Unregister` 會在執行時間中造成多個問題，主要是：

- 如果元件註冊全域事件，則會接收 *所有* 類型的全域輸入事件。
- 如果物件上的其中一個元件註冊全域輸入事件，此物件上的所有元件都會接收 *所有* 類型的全域輸入事件。
- 如果同一個物件上的兩個元件註冊到全域事件，然後在執行時間中停用其中一個，則第二個元件會停止接收全域事件。

新 `RegisterHandler` 的 API 和 `UnregisterHandler` ：

- 提供明確且細微的控制，以明確且細微地控制要對哪些輸入事件進行全域接聽，且應以焦點為基礎。
- 允許相同物件上的多個元件彼此獨立接聽全域事件。

**_如何遷移_**

- 如果您之前曾經呼叫過 `Register` / `Unregister` API，請將這些呼叫取代為的呼叫 `RegisterHandler` / `UnregisterHandler` 。 使用您實作為泛型參數的處理常式介面。 如果您執行多個介面，且其中有數個接聽全域輸入事件，請呼叫 `RegisterHandler` 多次。
- 如果您繼承自 `InputSystemGlobalListener` ，請將繼承變更為 `InputSystemGlobalHandlerListener` 。 執行 `RegisterHandlers` 和 `UnregisterHandlers` 抽象方法。 在「執行」呼叫中 `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) 在您要接聽全域事件的所有處理常式介面上註冊。
- 如果您繼承自、實 `BaseInputHandler` `RegisterHandlers` 和 `UnregisterHandlers` 抽象方法 (與 `InputSystemGlobalListener`) 相同。

**_遷移範例_**

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

**空間感知**

IMixedRealitySpatialAwarenessSystem 和 IMixedRealitySpatialAwarenessObserver 介面採用多個中斷變更，如下所述。

**_變更_**

下列方法 (s) 已重新命名，以更清楚地描述其使用方式。

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` 已重新命名為以 `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` 明確說明其使用方式。

**_新增項目_**

根據客戶的意見反應，我們已新增可輕鬆移除先前觀察到的空間感知資料的支援。

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**解算器**

部分的規劃求解元件和 SolverHandler manager 類別已變更，以修正各種 bug，並以更直覺的方式使用。

**_SolverHandler_**

- 類別不再延伸來源 `ControllerFinder`
- `TrackedObjectToReference` 公用屬性已被取代，並已重新命名為 `TrackedTargetType`
- `TrackedObjectType` 淘汰靠左 & 右控制器值。 改為使用 `MotionController` 或 `HandJoint` 值，並更新新 `TrackedHandedness` 屬性以將追蹤限制在左方或右控制器

**_Receivebegindoc_**

- `TrackedObjectForSecondTransform` 公用屬性已被取代，並已重新命名為 `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` 已移除。 若要更新規劃求解，請修改公用屬性 (例如 `SecondTrackedObjectType`)

**_SurfaceMagnetism_**

- `MaxDistance` 公用屬性已被取代，並已重新命名為 `MaxRaycastDistance`
- `CloseDistance` 公用屬性已被取代，並已重新命名為 `ClosestDistance`
- 的預設值 `RaycastDirectionMode` 現在會 `TrackedTargetForward` 以追蹤的目標轉換方向向前 raycasts
- `OrientationMode`列舉值 `Vertical` 和 `Full` 都已 `TrackedTarget` 分別重新命名為 `SurfaceNormal`
- `KeepOrientationVertical` 已新增公用屬性，以控制相關聯 GameObject 的方向是否維持垂直

**按鈕**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 現在 `DistanceSpaceMode` 將屬性設為 `Local` 預設值。 這可讓按鈕進行調整，同時仍 pressable

**剪出球體**

ClippingSphere 介面已變更，以反映在 ClippingBox 和 ClippingPlane 中找到的 Api。

現在會根據轉換比例，以隱含的方式來計算 ClippingSphere 的 Radius 屬性。 開發人員必須先在偵測器中指定 ClippingSphere 的半徑。 如果您想要變更半徑，只要以平常的方式更新轉換的轉換規模。

**NearInteractionTouchable 和 PokePointer**

- NearInteractionTouchable 不會處理 Unity UI 畫布的任何時間。 NearInteractionTouchableUnityUI 類別必須立即用於 Unity UI touchables。
- ColliderNearInteractionTouchable 是以 colliders 為基礎之 touchables 的新基類，也就是 NearInteractionTouchableUnityUI 以外的每個可觸式。
- BaseNearInteractionTouchable. DistFront 已移動並重新命名為 PokePointer。 TouchableDistance 這是 PokePointer 可以與 touchables 互動的距離。 先前每個可觸式都有自己的最大互動距離，但現在會在 PokePointer 中定義，以提供更佳的優化。
- BaseNearInteractionTouchable 已重新命名為 PokeThreshold，因此它會清楚指出 PokeThreshold 是 DebounceThreshold 的對應項。 當超過 PokeThreshold 時，即會啟動可觸式，並在超過 DebounceThreshold 時釋放。

**ReadOnlyAttribute**

已將 `Microsoft.MixedReality.Toolkit` 命名空間加入至 `ReadOnlyAttribute` 、 `BeginReadOnlyGroupAttribute` 和 `EndReadOnlyGroupAttribute` 。

**PointerClickHandler**

`PointerClickHandler` 類別已被取代。 您 `PointerHandler` 應該改為使用，它會提供相同的功能。

**HoloLens clicker 支援**

HoloLens clicker 的控制器對應已從狀況變更 [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) 為狀況 [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) 。 為了因應此情況，當您第一次開啟 ControllerMapping 設定檔時，會執行自動更新程式。 請至少在升級至2.0.0 之後開啟任何自訂設定檔一次，以觸發這個一次性的遷移步驟。

**InteractableHighlight**

`InteractableHighlight` 類別已被取代。 `InteractableOnFocus` `FocusInteractableStates` 應改為使用類別和資產。 若要為建立新的 `Theme` 資產 `InteractableOnFocus` ，請在 [專案] 視窗中按一下滑鼠右鍵，然後選取 [*建立*  >  *混合現實工具* 組  >  *互動*  >  *主題*]。

**HandInteractionPanZoom**

`HandInteractionPanZoom` 已移至 UI 命名空間，因為它不是輸入元件。 `HandPanEventData` 也已移至此命名空間，並簡化為與其他 UI 事件資料對應。

### <a name="assembly-name-changes-in-200"></a>2.0.0 中的元件名稱變更

在2.0.0 版本中，所有的官方混合現實工具組元件名稱及其相關聯的元件定義 (. asmdef) 檔案都已更新為符合下列模式。

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

在某些情況下，已合併多個元件以建立更好的 unity 內容。 如果您的專案使用自訂的 asmdef 檔案，則可能需要更新。

下表說明 RC2 asmdef 檔案名如何對應至2.0.0 版本。 所有元件名稱都符合 asmdef 檔案名。

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | MixedReality 工具組. asmdef |
| MixedRealityToolkit. BuildAndDeploy. asmdef | MixedReality. BuildAndDeploy. asmdef |
| MixedRealityToolkit，asmdef 的 | 已移除，請使用 MixedReality 工具組。 asmdef |
| MixedRealityToolkit. EditorClassExtensions. asmdef | MixedReality. ClassExtensions. asmdef
| MixedRealityToolkit asmdef | MixedReality. asmdef。 |
| MixedRealityToolkit ServiceInspectors. asmdef | MixedReality. ServiceInspectors. asmdef |
| MixedRealityToolkit. UtilitiesAsync. asmdef | MixedReality. asmdef。 |
| Asmdef 的 MixedRealityToolkit。 | MixedReality 工具組。 asmdef |
| MixedRealityToolkit Gltf. asmdef | MixedReality. Gltf. asmdef |
| MixedRealityToolkit，Gltf asmdef | MixedReality. Gltf. asmdef |

**MixedRealityToolkit。提供者**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. OpenVR. asmdef | MixedReality. OpenVR. asmdef |
| MixedRealityToolkit. WindowsMixedReality. asmdef | MixedReality. WindowsMixedReality. asmdef |
| MixedRealityToolkit. WindowsVoiceInput. asmdef | MixedReality. WindowsVoiceInput. asmdef |

**MixedRealityToolkit 服務**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. BoundarySystem. asmdef | MixedReality. BoundarySystem. asmdef |
| MixedRealityToolkit. CameraSystem. asmdef | MixedReality. CameraSystem. asmdef |
| MixedRealityToolkit. DiagnosticsSystem. asmdef | MixedReality. DiagnosticsSystem. asmdef |
| MixedRealityToolkit. InputSimulation. asmdef | MixedReality. InputSimulation. asmdef |
| MixedRealityToolkit. InputSimulation. asmdef | MixedReality. InputSimulation. asmdef。 |
| MixedRealityToolkit. InputSystem. asmdef | MixedReality. InputSystem. asmdef |
| MixedRealityToolkit asmdef | MixedReality. InputSystem. asmdef。 |
| MixedRealityToolkit. SceneSystem. asmdef | MixedReality. SceneSystem. asmdef |
| MixedRealityToolkit. SpatialAwarenessSystem. asmdef | MixedReality. SpatialAwarenessSystem. asmdef |
| MixedRealityToolkit. TeleportSystem. asmdef | MixedReality. TeleportSystem. asmdef |

**MixedRealityToolkit SDK**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. asmdef | MixedReality 工具組. asmdef |
| MixedRealityToolkit asmdef | MixedReality 工具組. asmdef |

**MixedRealityToolkit 範例**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit。例如 asmdef | MixedReality，例如 asmdef |
| MixedRealityToolkit. Gltf. asmdef | MixedReality. Gltf. asmdef |
| MixedRealityToolkit，例如 StandardShader asmdef | MixedReality. StandardShader. asmdef。 |
| MixedRealityToolkit，InspectorFields. asmdef | MixedReality. InspectorFields. asmdef |
| MixedRealityToolkit，例如 InspectorFields asmdef。 | MixedReality. InspectorFields. asmdef。 |
| MixedRealityToolkit，例如 Interactables. asmdef | MixedReality. Interactables. asmdef。 |
