---
title: MRTK 2.5 版本資訊
description: MRTK 2.5 版的版本資訊
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: c9458e5236cc7de18eb27c3c3e13221a366c89a4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177511"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a>Microsoft Mixed Reality 工具組2.5 版本資訊

> [!IMPORTANT]
> 有一個已知的編譯器問題，會影響使用 ARM64 針對 Microsoft HoloLens 2 所建立的應用程式。 若要修正此問題，請將 Visual Studio 2019 更新至16.8 版或更新版本。 如果您無法更新 Visual Studio，請匯入套件以套用因應措施 `com.microsoft.mixedreality.toolkit.tools` 。

## <a name="whats-new-in-254"></a>2.5.4 的新功能

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>使用 UPM 來修正 Oculus 整合的 bug

使用 UPM 時，OculusXRSDKDeviceManagerProfile 在啟動時一律會將其 [prefabs 設定為 None](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160)。 此版本會將裝置管理員設定為在啟動時指向 prefabs 的工作集。

### <a name="fixes-an-issue-with-openxr-via-upm"></a>修正 OpenXR via UPM 的問題

修正在使用 OpenXR 和 MRTK 透過 Unity 的封裝管理員時，OpenXR 提供者預設不會新增至 link.xml 的問題，會導致新的專案無法在裝置上執行。 已升級的現有專案仍需要手動加入。

## <a name="whats-new-in-253"></a>2.5.3 的新功能

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>修正在2.5.2 中引進的 Oculus 回歸

2.5.2 在 [整合 OCULUS SDK 時引進了組建問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083)。 此版本會還原該問題。

## <a name="whats-new-in-252"></a>2.5.2 的新功能

### <a name="add-support-for-openxr"></a>新增對 OpenXR 的支援

已新增 Unity OpenXR preview 套件和 Microsoft Mixed Reality OpenXR 封裝的初始支援。 如需詳細資訊，請參閱 [MRTK/XRSDK 開始使用頁面](../configuration/getting-started-with-mrtk-and-xrsdk.md)、 [Unity 的論壇文章](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)或 [Microsoft 的檔](/windows/mixed-reality/develop/unity/openxr-getting-started) 。

> [!IMPORTANT]
> Unity 中的 OpenXR 僅支援 Unity 2020.3 和更新版本。
> 它也只支援 x64、ARM 和 ARM64 組建。

### <a name="boundary-visualization-errors-fixed"></a>已修正界限視覺效果錯誤

界限視覺效果（例如 floor 或牆壁）現在將會正確設定，並在執行時間根據界限設定檔顯示。

### <a name="msbuild-for-unity-support"></a>Unity 支援的 MSBuild

2.5.2 版本已移除對 unity 的 MSBuild 的支援，以配合[unity 的新套件指引](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)。

## <a name="whats-new-in-251"></a>2.5.1 的新功能

### <a name="package-dependency-errors-fixed"></a>已修正套件相依性錯誤

此版本修正不正確的套件間檔案相依性 (例如：標準資產中的檔案不再于基礎) 中正確參考檔案。 2.5.1 版也會在文字網狀 Pro 上新增明確的相依性。

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>複製到資產/MRTK/著色器的標準資產套件著色器

當標準資產套件透過 UPM 安裝時，著色器將會複製到 [資產/MRTK/著色器] 資料夾，使其不再是不可變的。 這可解決在下一次載入專案時， (URP) 還原舊版行為的通用轉譯管線所更新的著色器問題。

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>固定的傳送游標停留在手中

此版本修正了 [傳送目的地] 游標可以用來手上視覺效果的 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) 。

## <a name="whats-new-in-250"></a>2.5.0 的新功能

### <a name="unity-package-manager-upm-support"></a>Unity 封裝管理員 (UPM) 支援

混合現實工具組現在可以使用 Unity 封裝管理員進行管理。

![MRTK Foundation UPM 套件](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> 匯入 MRTK UPM 套件需要一些手動步驟。 如需詳細資訊，請參閱[混合現實工具組和 Unity 封裝管理員](../configuration/usingupm.md)。

### <a name="oculus-quest-xr-sdk-support"></a>Oculus 追求 XR SDK 支援

MRTK 現在支援使用原生 XR SDK 管線執行 Oculus 的執行耳機和控制器。 [Oculus Integration Unity 套件](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)也支援手動追蹤，感謝[ERIC Provencher](https://twitter.com/prvncher)在 MRTK 上的工作！

如需如何使用新的管線在 Oculus 上部署裝置的指示，請參閱 Oculus 操作 [設定指南](../supported-devices/oculus-quest-mrtk.md)

### <a name="scrolling-object-collection"></a>滾動物件集合

MRTK UX 元件已從實驗性功能進行升級，並可讓您更自由地 layouting 不同大小的3D 內容，並新增對尚未附加 colliders 之物件的支援。 另外也加入了停用內容遮罩的新選項，讓原型設計更容易。

如需詳細資訊，請參閱 [滾動物件集合](../features/ux-building-blocks/scrolling-object-collection.md) 。

![滾動物件集合](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a>傳送指標動畫、處理和音效改進

傳送指標現在已改善動畫和音訊意見反應。 我們也改善了「傳送」指標的處理方式，以便在從附近表面轉換到更遠的表面時處理更平滑的處理。

### <a name="input-simulation-cheat-sheet"></a>輸入模擬功能提要

HandInteractionExamples 場景現在具有可設定的快捷方式，可顯示輸入模擬的說明頁面

![輸入模擬功能提要](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a>使用滑鼠輸入模擬眼睛

使用者現在可以使用滑鼠來模擬眼睛追蹤。 查看 `Eye Simulation Mode` 輸入模擬設定檔中的欄位，並將它設定為滑鼠。 這會取代上一個 `Simulate Eye Position` 欄位。

![眼睛的老鼠](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a>編輯器播放模式下的輸入模擬移動控制器

使用者現在可以模擬移動控制器，就像手入編輯器播放模式一樣。 目前支援觸發程式、抓取和功能表按鈕。

### <a name="conical-grab-pointer"></a>圓錐抓取指標

您現在可以將抓取指標設定為使用來自抓取點的錐形來查詢附近的物件，而不是球體。 這與預設 HoloLens 2 介面中的行為更相似，後者會使用錐形來查詢附近的物件。 DefaultHoloLens2InputSystemProfile 也已調整為使用新的 `ConicalGrabPointer` 。

![圓錐抓取指標](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a>TestUtilities 套件

現在有一個套件 (MixedReality) ，其中包含 PlayMode 和 TestMode 測試基礎結構，MRTK 會使用該基礎結構來建立端對端測試。 此基礎結構對 MRTK 小組本身來說非常方便，而我們很高興能讓取用者使用這個基礎結構，將測試涵蓋範圍新增至自己的專案。

下列程式碼示範如何建立測試手、將它顯示在特定位置、四處移動，然後進行縮小並開啟。

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

如需如何使用這些 TestUtilities 撰寫測試的指示，請參閱這一節的 [撰寫測試](../contributing/unit-tests.md#writing-tests)。

如需使用此基礎結構的現有測試範例，請參閱 MRTK 的 [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)。

### <a name="support-for-the-leap-motion-451-unity-modules"></a>支援閏運動 4.5.1 Unity 模組

已新增對閏運動 Unity 模組4.5.1 版的支援，且已移除對4.4.0 資產的支援。 目前支援的 Leap Unity 模組版本為4.5.0 和4.5.1。

另外還有一項額外的步驟來進行初始的 Leap 移動整合，如需詳細資訊，請參閱 [如何在 MRTK 中設定 Leap 的追蹤動作](../supported-devices/leap-motion-mrtk.md) 。

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a>空間感知網格觀察者更妥善處理自訂的材質

在此版本中， `Windows Mixed Reality Spatial Mesh Observer` 和 `Generic XR SDK Spatial Mesh Observer` 元件已改進視覺材質處理。 當觀察者更新了網格，而這些資料在先前已重設為設定檔中所設定的預設 VisibleMaterial 時，現在會保留材質。

這可讓開發人員改變網格材質，而不會意外覆寫變更。

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a>Link.xml 在 MixedRealityToolkit 產生的資料夾中建立

隨著 Unity 套件管理員 MRTK 的推出，MRTK 現在會將檔案寫入 `link.xml` `Assets/MixedRealityToolkit.Generated` 資料夾中（如果沒有的話）。 建議您將這個檔案加入 (， `link.xml.meta`) 加入原始檔控制。 Link.xml 是用來影響 Unity 連結器的 [managed 程式碼去除](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) 功能。

如需 MRTK link.xml 檔案的詳細資訊，請參閱 [MRTK 和 managed code 抽出](../updates-deployment/mrtk-and-managed-code-stripping.md) 文章。

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a>Unity 2019.3 +： MRTK configuration 對話方塊不再嘗試啟用舊版 XR 支援

為了避免在使用 Unity 的 XR 平臺時可能發生衝突，已從 [MRTK 設定] 對話方塊中移除啟用舊版 XR 支援的選項。 如有需要，您可以在 Unity 2019 中使用 **編輯**  >  **Project 設定**  >
 **Player**  >  **XR**  >  **支援設定虛擬實境**，以啟用舊版 XR 支援。

### <a name="reduction-in-initializeonload-overhead"></a>減少 InitializeOnLoad 額外負荷

我們已執行工作來減少在 InitializeOnLoad 處理常式中執行的工作量，而這應該會導致內部迴圈開發速度的改進。 InitializeOnLoad 處理常式會在每次編譯腳本、進入播放模式之前，以及在編輯器啟動時執行。 這些處理常式現在會在較少的情況下執行，進而改善一般 Unity 回應性。

在某些情況下，必須進行取捨：

- 若要進行額外的整合步驟，請參閱 [Leap 動作手追蹤](../supported-devices/leap-motion-mrtk.md) 設定。
- 針對使用 ARFoundation 的使用者，現在可以在其快速入門步驟中進行額外的手動步驟。
  如需新步驟，請參閱 [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) 。
- 對於將在 HoloLens 2 上使用[舊版 XR 管線](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions)的使用者，現在有一個[手動步驟](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings)可以執行。

### <a name="bounds-control-graduated"></a>界限控制分級

![界限控制項](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

[界限控制項](../features/ux-building-blocks/bounds-control.md) 從實驗中開始，並提供一大堆新功能和大量的 bug 修正。
此更新的重點清單如下：

- 屬性分為設定，可讓您更輕鬆地設定界限控制項
- 設定可以透過可編寫腳本的物件共用
- 每個屬性/可編寫腳本的屬性都可設定執行時間
- 不再于屬性變更時重新建立界限控制設備
- 轉譯控制碼支援
- 透過條件約束管理員的完整條件約束支援
- 彈性系統整合 (實驗性) 

舊的周框方塊現在已被取代，而且使用周框方塊的現有遊戲物件可以 [使用「遷移工具](../features/tools/migration-window.md) 」或「周框方塊」偵測 [器](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control)進行升級。

### <a name="constraint-manager-component"></a>條件約束管理員元件

條件約束現在可透過新的 [條件約束管理員元件](../features/ux-building-blocks/constraint-manager.md)，用於界限控制項和物件操作工具。 這兩個元件都會建立每個預設的條件約束管理員，並自動處理任何附加的條件約束。

此外，自動行為條件約束管理員也會隨附手動模式，讓使用者決定應處理的條件約束。
基於這個理由，我們在屬性偵測器中顯示條件約束的方式改變了一點。

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

套用至元件的條件約束現在會顯示為條件約束管理員元件中的清單，而使用條件約束管理員 ([界限控制項](../features/ux-building-blocks/bounds-control.md#constraint-system) 或 [物件](../features/ux-building-blocks/object-manipulator.md#constraint-manager) 操作工具的元件) 現在會顯示選取的條件約束管理員和模式 (自動或手動) 。
如需詳細資訊，請參閱檔中的「 [條件約束管理員](../features/ux-building-blocks/constraint-manager.md) 」一節。

### <a name="hololens-2-button-material-update"></a>HoloLens 2 按鈕材質更新

已更新 HoloLens 2 按鈕的 front 籠材質，以移除 MRC 中的黑色色彩。

![HoloLens 2 按鈕材質更新](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a>描述面板更新、可移動範例場景

更新的描述面板。  (SceneDescriptionPanelRev. 預製專案) 新的設計提供 grabbable 的頂線，可讓使用者調整/移動整個場景。

![描述面板更新](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a>空間網格視覺效果-敲擊時的脈衝

已更新空間網格的脈衝著色器範例，以符合 HoloLens 2 的 shell 行為。

![按兩下時的脈衝](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a>彈性系統 (實驗性) 

![彈性 System2](../features/images/elastics/Elastics_Main.gif)

MRTK 現在隨附彈性的 [模擬系統](../features/experimental/elastic-system.md) ，其中包含各種可延伸和彈性的子類別，提供4維四元數的系結、三維的成交量彈簧和簡單線性彈簧系統。

目前支援 [彈性 manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 的下列 MRTK 元件可利用彈性功能：

- [界限控制項](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [物件操作工具](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a>實驗性)  (搖桿

可以控制大型目標物件的搖桿介面範例。

![操縱 杆](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a>色彩選擇器 (實驗性) 

實驗性控制項，可讓您輕鬆地在執行時間變更任何物件的材質色彩。

![色彩選擇器控制項的三種不同方法](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![色彩選擇器控制項四種不同的方法](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a>重大變更

### <a name="assembly-definition-files-changes"></a>元件定義檔變更

有些 asmdef 檔案已變更，現在僅支援 Unity 2018.4.13 f1 或更新版本。 在舊版 Unity 中更新至 MRTK 2.5 時，會顯示編譯錯誤。 若要修正此問題，請 `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` 移至 [專案] 視窗，並移除偵測器中遺漏的參考。 使用和重複執行這些步驟 `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` 。 請注意，您必須將這三個 asmdef 檔案取代為原始 (（亦即，升級至 Unity 2019 時未修改的) ），以還原變更。

### <a name="imixedrealitypointermediator"></a>IMixedRealityPointerMediator

此介面已更新為具有新的函式：

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

如果您有不具子類別 DefaultPointerMediator 的自訂指標中繼程式，您必須執行這個新的函式。 如需這種新增原因的詳細背景，請參閱 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) 。 這是為了確保指標喜好設定會明確地傳遞至中繼程式，而不是根據採用 IPointerPreferences 的函式是否存在而隱含地完成。

### <a name="rest--device-portal-api"></a>Rest/裝置入口網站 API

`UseSSL`靜態屬性已從移 `Rest` 至 `DevicePortal` 。

如果您先前已執行此操作 .。。

```csharp
Rest.UseSSL = true
```

現在就完成了 .。。

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a>Link.xml

如果應用程式先前使用了 MRTK 的 NuGet 分佈，則已 `link.xml` 從基礎封裝中移除該檔案。 若要還原程式碼保留規則，請在 Unity 中開啟專案一次，並在中建立預設檔案 `link.xml` `Assets/MixedRealityToolkit.Generated` 。 建議將此檔案 (，並 `link.xml.meta`) 新增至原始檔控制。

### <a name="transform-constraint-changes"></a>轉換條件約束變更

TargetTransform 屬性已標示為過時，因為條件約束系統未使用它。 條件約束邏輯是以傳遞至 Initialize 和 Apply 方法的轉換為基礎。 依賴這個屬性的衍生使用者條件約束，可以藉由儲存條件約束元件的轉換，來快取其實 TargetTransform，以達成相同的行為。

預存的初始世界姿勢 `worldPoseOnManipulationStart` 資料類型已從 MixedRealityPose 變更為 MixedRealityTransform，其中包含操作物件的本機縮放值。 有了這種變更，就不需要再另行快取任何初始調整值。

### <a name="new-property-in-imixedrealitydictationsystem"></a>IMixedRealityDictationSystem 中的新屬性

已將新的屬性 `AudioClip` 新增至 IMixedRealityDictationSystem 介面。 `AudioClip`屬性可讓您存取與目前聽寫會話相關聯的音訊剪輯。 使用者必須在其執行介面的腳本中執行屬性。

### <a name="service-facades-turn-down"></a>服務 facade 關機

服務 facade 會在2.5 中關閉。 這項功能最初是為了讓 MRTK 設定檔的設定變得更容易 (藉由建立假的場景內 Gameobject 來表示每個 MRTK 的服務) 。 在長時間執行的情況下，我們想要避免建立假的遊戲中物件，並嘗試將它們同步 (因為資料同步和「真實事實」問題很難調整規模，並能正確) 。

在2.5 中，服務外觀處理常式會保持不變，以確保專案升級順暢，服務外觀處理常式會刪除專案中的任何 facade，以確保在2.5 中開啟的場景會自動修正。

未來的版本將移除與服務外觀功能相關聯的其餘程式碼。

### <a name="addition-of-motion-controller-to-input-simulation-service"></a>將移動控制器新增至輸入模擬服務

動畫控制器模擬現在以編輯器播放模式提供，以及現有的手模擬。 為了啟用這項變更，許多目前的函式/欄位/屬性現在已標示為過時， `InputSimulationService.cs` 並會 `MixedRealityInputSimulationProfile.cs` 取得最重要的變更。 相關程式碼的邏輯和行為大多保持不變，而大部分的過時函式與將 "手形" 的參考取代為較泛型詞彙 "controller" (例如從 `DefaultHandSimulationMode` 到 `DefaultControllerSimulationMode`) 。 除了取得新的名稱之外，某些新函式的傳回型別也會更新，以符合名稱/行為變更 (例如 `GetControllerDevice` ，根據原始的，現在會傳回 `GetHandDevice` `BaseController` 而不是 `SimulatedHand`) 。

`IInputSimulationService` 現在有新的屬性 `MotionControllerDataLeft` 和 `MotionControllerDataRight` 。 `MixedRealityInputSimulationProfile` 現在包含特定移動控制器按鈕之鍵盤對應的新欄位。

## <a name="known-issues"></a>已知問題

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache 可能會在關機時建立新的攝影機

在某些情況下 (例如在 Unity 編輯器) 中使用 LeapMotion 提供者時，CameraCache 可能會在關閉時重新建立 MainCamera。 如需詳細資訊，請參閱 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 。

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException 透過 Unity 匯入範例的時機封裝管理員

視專案路徑的長度而定，透過 unity 匯入範例封裝管理員可能會在 unity 主控台中產生 FileNotFoundException 訊息。 造成這種情況的原因是「遺失」檔案的路徑超過 MAX_PATH (256 個字元) 。 若要解決此問題，請縮短專案路徑的長度。

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>未指定空間定位器。 應用程式將不支援空間音效

如果未設定音訊空間定位器，則會出現「未指定任何空間定位器」警告。 如果未安裝 XR 套件，則會發生這種情況，因為 Unity 包含這些套件中的 spatializers。

若要解決此問題，請確定：

- **視窗**  > **封裝管理員** 已安裝一或多個 XR 套件
- **混合現實工具**  >  組 **公用程式**  > **設定 Unity Project** 並為 **音訊空間定位器** 進行選取

  ![選取音訊空間定位器](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException：物件參考未設定為物件的實例 (SceneTransitionService.Initialize) 

在某些情況下，開啟 `EyeTrackingDemo-00-RootScene` 可能會在 SceneTransitionService 類別的 Initialize 方法中造成 NullReferenceException。
此錯誤是因為未設定場景轉換服務的設定檔。 若要解決此問題，請使用下列步驟：

- 流覽至階層 `MixedRealityToolkit` 中的物件
- 在 [偵測器] 視窗中，選取 `Extensions`
- 如果未展開，請展開 `Scene Transition Service`
- 將的值設定 `Configuration Profile` 為 **MRTKExamplesHubSceneTransitionServiceProfile**

![修正場景轉換](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus 的追求

目前在 [以獨立平臺為目標時，使用 OCULUS XR 外掛程式](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)的已知問題。 查看 Oculus bug 追蹤程式/論壇/版本資訊以取得更新。

Bug 會以這一組3個錯誤表示：

![Oculus XR 外掛程式錯誤](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI 和 TextMeshPro

較新版本的 TextMeshPro 有一個已知問題 (1.5.0 + 或 2.1.1 +) ，其中下拉式清單和粗體字字元間距的預設字型大小已改變。

![TMP 映射](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

這可以透過降級至舊版的 TextMeshPro 來解決。 See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.
