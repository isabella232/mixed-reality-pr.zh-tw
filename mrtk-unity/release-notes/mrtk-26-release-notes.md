---
title: MRTK 2.6 版本資訊
description: MRTK 2.6 版的版本資訊
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: c172e5d071bba22626e9c35b2b4318f1ff779335
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562508"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Microsoft Mixed Reality 工具組2.6 版本資訊

> [!IMPORTANT]
> 有一個已知的編譯器問題，會影響使用 ARM64 針對 Microsoft HoloLens 2 所建立的應用程式。 若要修正此問題，請將 Visual Studio 2019 更新至16.8 版或更新版本。 如果您無法更新 Visual Studio，請匯入套件以套用因應措施 `com.microsoft.mixedreality.toolkit.tools` 。

## <a name="whats-new-in-262"></a>2.6.2 的新功能

### <a name="corrects-parenting-of-the-spatial-mesh"></a>更正空間網格的父代

修正在混合現實 Playspace 物件移動之後，空間網格未正確定位的 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) (例如：透過傳送) 。

## <a name="whats-new-in-261"></a>2.6.1 的新功能

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>修正 OpenXR 未在 HoloLens 2/UWP 上執行

修正防止 MRTK 的 OpenXR 支援在 UWP 上執行的回歸。

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>修正閏運動 ObjectManipulator 未旋轉

修正 ObjectManipulator 腳本未將 Leap 運動手旋轉的回歸納入考慮。

### <a name="sample-scene-updates"></a>範例場景更新

更新場景理解範例場景，以正確地反映 Unity 外掛程式的出貨狀態。 也會更新此範例，使其不再相依于要匯入的空間感知範例場景。 更新至2.6.1 之前，您應該刪除已匯入的場景理解和空間感知範例（如果專案存在於您的專案中），以避免可能發生衝突。 如果您未移除這些範例，並在主控台中看到與這些範例相關的衝突，請 (或) 資料夾中移除兩個範例， `Assets/Samples/Mixed Reality Toolkit Examples` 然後再次嘗試匯入。

更新對話範例場景，以正確描述目前的對話案例。

## <a name="whats-new-in-260"></a>2.6.0 的新功能

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>新增對 OpenXR 的支援

已新增 Unity OpenXR preview 套件和 Microsoft Mixed Reality OpenXR 封裝的初始支援。 如需詳細資訊，請參閱 [MRTK/XRSDK 開始使用頁面](../configuration/getting-started-with-mrtk-and-xrsdk.md)、 [Unity 的論壇文章](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)或 [Microsoft 的檔](/windows/mixed-reality/develop/unity/openxr-getting-started) 。

> [!IMPORTANT]
> Unity 中的 OpenXR 僅支援 Unity 2020.2 和更新版本。
>
> 目前它也只支援 x64 和 ARM64 組建。

### <a name="asset-swap-utility"></a>資產交換公用程式

使用新的 [資產交換公用程式](../features/tools/asset-swap-utility.md)，在 Unity 場景中交換多個資產。

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>MRTK 現在支援 HP 動作控制器

HP 殘響 G2 的控制器現在可在 MRTK 中以原生方式運作。

### <a name="experimental-interactive-element--state-visualizer"></a>實驗性互動式元素 + 狀態視覺化

互動式元素是 MRTK 輸入系統的簡化集中進入點。 它包含狀態管理方法、事件管理，以及核心互動狀態的狀態設定邏輯。 如需詳細資訊，請參閱 [互動式元素檔](../features/experimental/interactive-element.md)集。

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

狀態視覺化是相依于互動式元素的動畫元件。 此元件會建立動畫剪輯、設定主要畫面格，並產生 Animator 狀態機器。 如需詳細資訊，請參閱 [狀態視覺化檔](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>所有平臺現在都支援使用「傳送」手勢進行遙傳

使用者現在可以使用「傳送」手勢，在所有平臺上四處移動其播放空間。 若要使用預設設定在 MR 裝置上傳送控制器，請使用操縱杆。 若要透過明確的手進行傳送，請與您的手朝外手勢，並將索引和捲動方塊朝外，以 curling 食指來完成傳送。 若要使用輸入模擬來傳送，請參閱更新的 [輸入模擬服務檔](../features/input-simulation/input-simulation-service.md)。

![傳送手勢](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>場景理解現在可在 MRTK 中作為實驗空間感知觀察者

[場景理解](/windows/mixed-reality/scene-understanding)的實驗性支援是在 MRTK 2.6 中引進。 使用者可以將 HoloLens 2 的場景理解功能納入以 MRTK 為基礎的專案中的空間感知觀察者。 如需詳細資訊，請參閱 [場景理解檔](../features/spatial-awareness/scene-understanding.md) 。

> [!IMPORTANT]
> 只有 HoloLens 2 和 Unity 2019.4 和更新版本才支援場景理解。
>
> 這項功能需要場景理解套件，現在可透過「 [混合現實」功能工具](https://aka.ms/MRFeatureTool)取得。
> 使用 Mixed Reality 功能工具或透過 UPM 匯入時，請先匯入示範-SpatialAwareness 範例，再匯入實驗性 SceneUnderstanding 範例，因為相依性問題。 如需詳細資訊，請參閱 [此 GitHub 問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 。

![場景理解](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>執行時間設定檔切換支援

MRTK 現在可讓您在初始化 MRTK (實例之前切換設定檔（亦即，預先 MRTK 初始化設定檔切換) ，以及在設定檔已在使用中時使用 (也就是使用中設定檔參數) 。 先前的參數可用來根據硬體的功能來啟用選取元件，而後者可以用來在使用者輸入應用程式子元件時修改體驗。 如需詳細資訊和程式碼範例，請閱讀 [設定檔切換的相關](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) 檔。

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>方向指標，並遵循實驗的解析器

有兩個新的解析器可供搭配主線 MRTK 使用。

![方向性指標規劃求解](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>從實驗性開始的手勢

這項功能現在已準備好搭配主線 MRTK 使用。

![手動指導範例](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>從實驗性分級的對話方塊控制項

對話方塊控制項現在已準備好搭配主線 MRTK 使用。

![對話方塊控制項](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>從實驗性分級的脈衝著色器

脈衝著色器腳本已從實驗性進行分級。 如需詳細資訊，請參閱： [脈衝著色器檔](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>輸入記錄服務改進

`InputRecordingService` 而且 `InputPlaybackService` 現在可以錄製並播放眼睛的眼睛輸入。 錄製已經過優化，可確保整段記錄期間的資料幀大小都一致，而記錄檔大小和節省時間也會降低大約50%。 現在可以非同步方式執行錄製檔案的儲存和載入作業。 請注意此 MRTK 版本中記錄的檔案格式已經變更，請參閱 [這裡](../features/input-simulation/input-animation-file-format.md) 以取得新版本1.1 規格的詳細資訊。

### <a name="reading-mode"></a>讀取模式

已新增 HoloLens 2 的 [讀取模式](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) 支援。 [讀取] 模式可減少系統的顯示欄位，但會排除 Unity 輸出的縮放比例。 Unity 轉譯的圖元會對應到 HoloLens 2 上的投射圖元。 應用程式作者應該使用多個個人進行測試，以確保這是他們在應用程式中所需的取捨。

![Windows Mixed Reality 閱讀模式](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>在 UWP 上支援3D 應用程式啟動器

新增為 UWP 設定 [3d 應用程式啟動器](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 的功能。 這項設定會在 [MRTK 組建] 視窗和 [MRTK] 專案設定的 [組建設定] 底下公開。 它會在 Unity 中的組建期間自動寫入至專案。

![組建設定](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>重大變更

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>匯入之 GLTF 物件的某些欄位現在已大寫

由於還原序列化相關的問題，已匯入 GLTF 物件的某些欄位現在以大寫字母開頭。 受影響的欄位會以新名稱 () ： `ComponentType` 、 `Path` 、 `Interpolation` 、、、、、、 `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` 、 `WrapT` 。

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>輸入動畫二進位檔案具有更新版本1.1 格式

輸入動畫二進位檔（由 `InputRecordingService` 和使用 `InputPlaybackService` ）現在具有更新的檔案格式，可讓您對這兩個服務進行優化。 如需新版本1.1 規格的詳細資訊，請參閱 [這裡](../features/input-simulation/input-animation-file-format.md) 。

### <a name="msbuild-for-unity-support"></a>適用于 Unity 的 MSBuild 支援

從2.5.2 版本開始，已移除對 MSBuild for Unity 的支援，以配合 [Unity 的新套件指引](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)。

## <a name="known-issues"></a>已知問題

### <a name="openxr"></a>OpenXR

目前有一個已知的全像是「全像」遠端和 OpenXR 的問題，也就是沒有一直可用的手接點。
此外，眼睛追蹤範例場景目前不相容，不過眼睛追蹤 _的確_ 可以運作。

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>部分混合現實工具組標準著色器功能需要基礎封裝

透過 Unity 封裝管理員匯入時，MRTK 標準著色器公用程式腳本 (例如：) HoverLight 不會與標準資產套件中的著色器共置。 若要存取此功能，應用程式將需要匯入基礎套件。

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache 可能會在關機時建立新的攝影機

在某些情況下 (例如在 Unity 編輯器) 中使用 LeapMotion 提供者時，CameraCache 可能會在關閉時重新建立 MainCamera。 如需詳細資訊，請參閱 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 。

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException 透過 Unity 匯入範例的時機封裝管理員

視專案路徑的長度而定，透過 Unity 匯入範例封裝管理員可能會在 Unity 主控台中產生 FileNotFoundException 訊息。 造成這種情況的原因是「遺失」檔案的路徑超過 MAX_PATH (256 個字元) 。 若要解決此問題，請縮短專案路徑的長度。

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>未指定空間定位器。 應用程式將不支援空間音效

如果未設定音訊空間定位器，則會出現「未指定任何空間定位器」警告。 如果未安裝 XR 套件，則會發生這種情況，因為 Unity 包含這些套件中的 spatializers。

若要解決此問題，請確定：

- **視窗**  > **封裝管理員** 已安裝一或多個 XR 套件
- **混合現實工具**  >  組 **公用程式**  > **設定 Unity 專案** 並為 **音訊空間定位器** 進行選取

  ![選取音訊空間定位器](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException：物件參考未設定為物件的實例 (SceneTransitionService.Initialize) 

在某些情況下，開啟 `EyeTrackingDemo-00-RootScene` 可能會在 SceneTransitionService 類別的 Initialize 方法中造成 NullReferenceException。
此錯誤是因為未設定場景轉換服務的設定檔。 若要解決此問題，請使用下列步驟：

- 流覽至階層 `MixedRealityToolkit` 中的物件
- 在 [偵測器] 視窗中，選取 `Extensions`
- 如果未展開，請展開 `Scene Transition Service`
- 將的值設定 `Configuration Profile` 為 **MRTKExamplesHubSceneTransitionServiceProfile**

![修正場景轉換設定檔](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus 的追求

目前在 [以獨立平臺為目標時，使用 OCULUS XR 外掛程式](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)的已知問題。 查看 Oculus bug 追蹤程式/論壇/版本資訊以取得更新。

Bug 會以這一組3個錯誤表示：

![Oculus XR 外掛程式錯誤](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI 和 TextMeshPro

較新版本的 TextMeshPro 有一個已知問題 (1.5.0 + 或 2.1.1 +) ，其中下拉式清單和粗體字字元間距的預設字型大小已改變。

![TMP 映射](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

這可以透過降級至舊版的 TextMeshPro 來解決。 See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.
