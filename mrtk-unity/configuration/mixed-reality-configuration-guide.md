---
title: MixedRealityConfigurationGuide
description: 將 MRTK 設定為 unity 的檔。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: bc5a0e286a8be588e14b469b965a216cedca4df5
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104701924"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a>混合現實工具組設定檔設定指南

![MRTK 標誌](../features/images/MRTK_Logo_Rev.png)

「混合現實」工具組盡可能集中管理工具組所需的設定， (除了真正的「事物」 ) 。

本指南是針對工具組目前可用的每個設定設定檔畫面的簡單逐步解說。

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>主要混合現實工具組設定檔

主要設定檔（附加至您場景中的 *MixedRealityToolkit* GameObject）會提供專案中工具組的主要進入點。

> [!NOTE]
> Mixed Reality 工具組會「鎖定」預設設定畫面，以確保您的專案一律會有一個共同的起點，而且建議您在專案發展時開始定義自己的設定。 在播放模式中，無法編輯 MRTK 設定。

![MRTK 設定檔](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

「混合現實」工具組的所有「預設」設定檔都可以在 [資產/MRTK/SDK/設定檔] 的 SDK 專案中找到。

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile 已針對 HoloLens 2 優化。 請參閱 [設定檔](../features/profiles/profiles.md) 以取得詳細資料。

當您開啟主要混合現實工具組設定檔時，您會在偵測器中看到下列畫面：

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

如果您選取場景中沒有 MixedRealityToolkit 的 MixedRealityToolkitConfigurationProfile 資產，則會詢問您是否要讓 MRTK 為您自動設定場景。 這是選擇性的，不過，場景中必須有作用中的 MixedRealityToolkit 物件，才能存取所有設定畫面。

這會裝載專案目前的使用中執行時間設定。

您可以從這裡流覽至 MRTK 的所有設定設定檔，包括：

- [混合現實工具組設定檔設定指南](#mixed-reality-toolkit-profile-configuration-guide)
  - [主要混合現實工具組設定檔](#the-main-mixed-reality-toolkit-configuration-profile)
  - [體驗設定](#experience-settings)
  - [攝影機設定](#camera-settings)
  - [輸入系統設定](#input-system-settings)
  - [界限視覺效果設定](#boundary-visualization-settings)
  - [遙傳系統選擇](#teleportation-system-selection)
  - [空間感知設定](#spatial-awareness-settings)
  - [診斷設定](#diagnostics-settings)
  - [場景系統設定](#scene-system-settings)
  - [其他服務設定](#additional-services-settings)
  - [輸入動作設定](#input-actions-settings)
  - [輸入動作規則](#input-actions-rules)
  - [指標設定](#pointer-configuration)
  - [手勢設定](#gestures-configuration)
  - [語音命令](#speech-commands)
  - [控制器對應設定](#controller-mapping-configuration)
  - [控制器視覺效果設定](#controller-visualization-settings)
  - [編輯器公用程式](#editor-utilities)
    - [服務偵測器](#service-inspectors)
    - [深度緩衝區轉譯器](#depth-buffer-renderer)
  - [在執行時間變更設定檔](#changing-profiles-at-runtime)
    - [預先 MRTK 初始化設定檔參數](#pre-mrtk-initialization-profile-switch)
    - [主動設定檔參數](#active-profile-switch)
  - [另請參閱](#see-also)

這些設定檔的詳細資訊如下：

---
<a name="experience"></a>

## <a name="experience-settings"></a>體驗設定

在 [主要混合現實工具組設定] 頁面上，此設定會定義您專案的 [混合現實環境規模](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity) 的預設操作。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>攝影機設定

攝影機設定會定義如何為您的混合現實專案設定相機，定義一般剪輯、品質和透明度設定。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>輸入系統設定

Mixed Reality 專案提供健全且妥善定型的輸入系統，以路由傳送預設選取之專案周圍的所有輸入事件。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

在 MRTK 所提供的輸入系統背後有數個其他系統，這些系統可協助您推動和管理複雜的 weavings，以抽象化多平臺/混合現實架構的複雜度。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

每個個別設定檔詳述如下：

- 焦點設定
- [輸入動作設定](#input-actions-settings)
- [輸入動作規則](#input-actions-rules)
- [指標設定](#pointer-configuration)
- [手勢設定](#gestures-configuration)
- [語音命令](#speech-commands)
- [控制器對應設定](#controller-mapping-configuration)
- [控制器視覺效果設定](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>界限視覺效果設定

界限系統會轉譯基礎平臺界限/守護者系統所報告的認知界限。 界限視覺化設定可讓您在相對於使用者位置的場景中，自動顯示記錄的界限。界限也會根據使用者在場景中 teleports 的位置做出反應/更新。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>遙傳系統選擇

Mixed Reality 專案提供一個功能完整的遙傳系統，可用於管理專案中依預設選取的遙傳事件。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>空間感知設定

Mixed Reality 專案提供重建的空間感知系統，以便在預設選取的專案中使用空間掃描系統。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

混合現實工具組空間感知設定可讓您自訂系統啟動的方式，不論是在應用程式以程式設計方式啟動或稍後以程式設計的方式，以及設定視野的範圍。

它也可讓您設定網格和介面設定，進一步自訂您的專案如何理解您的環境。

這僅適用于可提供掃描環境的裝置。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>診斷設定

MRTK 的選擇性但非常實用的功能是外掛程式診斷功能。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

診斷設定檔提供數個簡單的系統，讓您在專案執行時進行監視，包括方便的開啟/關閉參數，以啟用/停用場景中的顯示面板。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>場景系統設定

MRTK 會提供此選用服務，協助您管理複雜的加法場景載入/卸載。 若要判斷場景系統是否適合您的專案，請閱讀 [場景系統開始使用指南。](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>其他服務設定

混合現實工具組的其中一個更先進區域是其 [服務定位器模式](https://en.wikipedia.org/wiki/Service_locator_pattern) 的執行，可讓您向架構註冊任何「服務」。 這可讓您輕鬆地以新的功能/系統擴充架構，但也可讓專案利用這些功能來註冊自己的執行時間元件。

任何已註冊的服務仍會獲得所有 Unity 事件的完整優點，而不會有執行 MonoBehaviour 或相當笨拙單一模式的額外負荷和成本。 這可讓單純的 c # 元件執行前景和背景進程（例如，產生系統、執行時間遊戲邏輯或幾乎任何其他作業），而不會有場景額外負荷。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>輸入動作設定

輸入動作提供一種方法，可從執行時間專案中抽象化任何實體互動和輸入。 控制器/手/滑鼠/等) 的所有實體輸入 (都會轉譯成邏輯輸入動作，以便在執行時間專案中使用。 無論輸入的位置為何，您的專案都只會在您的場景中將這些動作實作為「要做的事」或「互動」。

若要建立新的輸入動作，只需按一下 [新增動作] 按鈕，然後為其代表的內容輸入易記的文字名稱。 然後，您只需要選取一個座標軸， (動作要傳達的資料類型) ，或在實體控制器的情況下，可以附加的實體輸入類型，例如：

| 軸條件約束 | 資料類型 | 描述 | 範例用法 |
| :--- | :--- | :--- | :--- |
| 無 | 無資料 | 用於空的動作或事件 | 事件觸發程式 |
| 原始 (保留)  | 物件 (object) | 保留供日後使用 | N/A |
| Digital | bool | 布林值 on 或 off 型別資料 | 控制器按鈕 |
| 單一軸 | FLOAT | 單一精確度資料值 | 範圍輸入，例如觸發程式 |
| 雙軸 | Vector2 | 多軸的雙重 float 類型日期 | Dpad 或操縱杆 |
| 三個 Dof 位置 | Vector3 | 具有3個 float 軸的位置型別資料 | 僅限3D 位置樣式控制器 |
| 三個 Dof 旋轉 | 四元數 | 只旋轉具有4個 float 軸的輸入 | 三度樣式的控制器，例如 Oculus Go 控制器 |
| 六 Dof | Mixed 事實會造成 (Vector3，四元數)  | 具有 Vector3 和四元陣列件的位置和旋轉樣式輸入 | 移動控制器或指標 |

使用輸入動作的事件不限於實體控制器，而且仍可在專案中使用，讓執行時間效果產生新的動作。

> [!NOTE]
> 輸入動作是在執行時間無法編輯的幾個元件之一，它們只是設計階段的設定。 當專案因為架構 (而執行時，不應該將此設定檔交換，而您的專案) 相依于每個動作所產生的識別碼。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>輸入動作規則

輸入動作規則可讓您根據其資料值，自動將一個輸入動作所引發的事件轉譯成不同的動作。 這些都是在架構內無縫管理的，而且不會產生任何效能成本。

例如，將單一雙重軸輸入事件從 DPad 中轉換為4對應的 "Dpad Up"/"DPad Down"/"Dpad Left"/"Dpad Right" 動作 (如下圖所示) 。

這也可以在您自己的程式碼中完成。 不過，因為這是一種非常常見的模式，架構會提供一種機制來執行這項「現成」

您可以針對任何可用的輸入軸設定輸入動作規則。 不過，您可以將一個軸類型的輸入動作轉譯為相同座標軸類型的另一個輸入動作。 您可以將雙重軸動作對應至另一個雙重軸動作，而不是數位或無動作。

![輸入動作規則設定檔](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>指標設定

指標是用來從任何輸入裝置驅動場景中的互動性，同時提供方向和點擊測試與場景 (中已附加碰撞器的任何物件，或是) 的 UI 元件。 預設會自動為控制器、耳機 (注視/焦點) 和滑鼠/觸控輸入設定指標。

指標也可以在作用中場景內視覺化，方法是使用混合現實工具組所提供的許多線條元件之一，或者，如果它們執行 MRTK IMixedRealityPointer 介面，則為您自己的介面。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- 指向範圍：決定所有指標的全域指向範圍，包括注視。
- 指向 Raycast 圖層遮罩：決定將 Raycast 的圖層指標。
- Debug Draw 指標放射：用來視覺化 raycasting 所使用之光線的 debug helper。
- 偵錯工具繪製指向放射片色彩：用來視覺化的一組色彩。
- 注視游標預製專案：可讓您輕鬆地指定任何場景的全球注視游標。

還有另一個協助程式按鈕，可快速跳至注視提供者，視需要覆寫一些特定的值。

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>手勢設定

手勢是系統特定的執行，可讓您將輸入動作指派給各種 Sdk 所提供的各種「手勢」輸入方法 (例如 HoloLens) 。

> [!NOTE]
> 目前的手勢實作為僅適用于 HoloLens，並且將在未來新增至工具組的其他系統中增強， (沒有任何日期) 。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>語音命令

就像手勢一樣，某些執行時間平臺也提供智慧型「語音轉換文字」功能，讓您能夠產生可由 Unity 專案接收的命令。 此設定檔可讓您設定下列各項：

1. 一般設定-設為自動啟動或手動啟動的 [啟動行為] 決定是否要在輸入系統啟動時初始化 KeywordRecognizer，或讓專案決定何時要初始化 KeywordRecognizer。 「辨識信賴等級」用來初始化 Unity 的 [KEYWORDRECOGNIZER API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)
2. 語音命令-註冊「單字」，並將其轉譯成可由您的專案接收的輸入動作。 如有需要，也可以附加至鍵盤動作。

> [!IMPORTANT]
> 系統目前僅支援在 Windows 10 平臺（例如 HoloLens 和 Windows 10 desktop）上執行的語音，並將在 (未來新增至 MRTK 的其他系統進行增強，而不) 任何日期。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>控制器對應設定

混合現實工具組的其中一個核心設定畫面是能夠設定和對應可供專案使用的各種控制器類型。

下方的 [設定] 畫面可讓您設定工具組目前所辨識的任何控制器。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

MRTK 會提供下列控制器/系統的預設設定：

- 滑鼠 (包括3D 空間滑鼠支援) 
- 觸控式螢幕
- Xbox 控制器
- Windows Mixed Reality 控制器
- HoloLens 手勢
- HTC Vive 杆控制器
- Oculus 觸控控制器
- Oculus 遠端控制器
- 一般 OpenVR 裝置只 (advanced 使用者) 

按一下任何預先建立之控制器系統的映射，可讓您為其所有對應的輸入設定單一輸入動作，例如，請參閱下方的 Oculus Touch controller 設定畫面：

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

另外還有一個可設定其他 OpenVR 或 Unity 輸入控制器（未在上方識別）的 advanced 畫面。

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>控制器視覺效果設定

除了控制器對應之外，還會提供個別的設定檔來自訂您的控制器在幕後的呈現方式。

這可以設定在「全域」 (特定手) 或個別控制器類型/手特定的控制器實例。

MRTK 也支援 Windows Mixed Reality 和 OpenVR 的原生 SDK 控制器模型。 這些會以 Gameobject 的形式載入場景，並使用平臺的控制器追蹤來定位。

如果場景中的控制器表示需要從實體控制器位置位移，則只要針對控制器模型的預製專案設定該位移 (例如，將控制器預製專案的轉換位置設定為位移位置) 。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>編輯器公用程式

下列公用程式只適用于編輯器，而且有助於改善開發生產力。

![MRTK 編輯器設定公用程式](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>服務偵測器

服務偵測器是一種僅限編輯器的功能，可產生代表作用中服務的場景物件。 選取這些物件會顯示提供檔連結的偵測器、控制編輯器視覺效果，以及深入瞭解服務的狀態。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

您可以勾選設定設定檔中的 [*編輯器設定*] 下的 [*使用服務* 偵測器]，以啟用服務偵測器。

### <a name="depth-buffer-renderer"></a>深度緩衝區轉譯器

與一些混合的現實平臺共用深度緩衝區可以改善全像 [影像的穩定](../performance/hologram-stabilization.md)。 例如，Windows Mixed Reality 平臺可以修改每圖元轉譯的場景，以在轉譯框架所需的時間內進行微妙的移動。 不過，這些技術需要具有精確資料的深度緩衝區，以瞭解幾何與使用者之間的位置和距離。

為了確保場景會將所有必要的資料轉譯至深度緩衝區，開發人員可以在設定檔中的 *編輯器設定* 下切換轉譯 *深度緩衝區* 功能。 這將會採用目前的深度緩衝區，並藉由將後置處理效果套用 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) 至主要攝影機，將其轉譯為場景視圖的色彩。

![轉譯深度緩衝區公用程式 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>場景中的藍色圓柱具有 ZWrite 關閉的材質，因此未寫入任何深度資料</sup>

## <a name="changing-profiles-at-runtime"></a>在執行時間變更設定檔

您可以在執行時間更新設定檔，而且在這種情況下，通常有兩個不同的案例和時間會有説明：

1. **預先 MRTK 的初始化設定檔參數**：啟動時，在 MRTK 初始化且設定檔變成作用中之前，請取代尚未使用的設定檔，以根據裝置功能啟用/停用不同的功能。 例如，如果在 VR 中執行的體驗沒有空間對應硬體，則啟用空間對應元件可能並不合理。
1. 使用中 **設定檔參數**：啟動後，在 MRTK 初始化且設定檔變成作用中之後，請將目前使用中的設定檔交換，以變更特定功能的行為方式。 例如，在應用程式中，可能會有想要完全移除的手指標的特定子體驗。

### <a name="pre-mrtk-initialization-profile-switch"></a>預先 MRTK 初始化設定檔參數

若要完成這項作業，請將 MonoBehaviour (範例附加在 MRTK 初始化之前執行的) ， (也就是喚醒 () ) 。 請注意，腳本 (例如，呼叫 `SetProfileBeforeInitialization`) 必須比腳本早執行 `MixedRealityToolkit` ，這可以藉由設定 [腳本執行順序設定](https://docs.unity3d.com/Manual/class-MonoManager.html)來達成。

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

不是 "profileToUse"，您可以有一組適用于特定平臺的任意設定檔 (例如，一個適用于 HoloLens 1、一個用於 VR、一個用於 HoloLens 2 等) 。 您可以使用各種其他指標 (例如 https://docs.unity3d.com/ScriptReference/SystemInfo.html ，或是攝影機是否為不透明/透明) ，以找出要載入的設定檔。

### <a name="active-profile-switch"></a>主動設定檔參數

這可以藉由將屬性設定 `MixedRealityToolkit.Instance.ActiveProfile` 為取代使用中設定檔的新設定檔來完成。

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

注意：在執行時間期間進行設定時 `ActiveProfile` ，在所有服務的最後一個 LateUpdate () 之後，將會發生目前正在執行之服務的終結，以及與新設定檔相關聯之服務的具現化和初始化，將在所有服務的第一次更新 () 之前發生。

在此程式期間，可能會發生明顯的應用程式 hesitation。 此外，任何優先順序高於腳本的腳本 `MixedRealityToolkit` 都可以先輸入更新，然後才能正確設定新的設定檔。 如需腳本優先順序的詳細資訊，請參閱 [腳本執行順序設定](https://docs.unity3d.com/Manual/class-MonoManager.html) 。

在設定檔切換程式中，現有的 UI 相機將保持不變，以確保需要 canvas 的 Unity UI 元件在切換之後仍能運作。

## <a name="see-also"></a>另請參閱

- [全像穩定](../performance/hologram-stabilization.md)
