---
title: 適用于開發人員的混合現實 capture
description: 瞭解為開發人員啟用、使用和轉譯混合現實 capture 的最佳作法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、相片、影片、捕捉、攝影機
ms.openlocfilehash: e55100003859e3581bdd7f6e1da312e1fdd8cf57
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009938"
---
# <a name="mixed-reality-capture-for-developers"></a>適用于開發人員的混合現實 capture

> [!NOTE]
> 請參閱下面 [的 PV 攝影機](#render-from-the-pv-camera-opt-in) 轉譯，以取得 HoloLens 2 新的 MRC 功能的指引。

您可以隨時 (的) 相片或影片進行 [混合的現實 capture](../../mixed-reality-capture.md) ，但在開發應用程式時，請記住幾件事。 這包括了 MRC 視覺品質的最佳作法，並在 MRCs 時回應系統變更。

開發人員也可以將混合現實的捕獲和插入順暢地整合到他們的應用程式中。

HoloLens (第一代) 支援最高720p 的影片和相片，而 HoloLens 2 上的 MRC 可支援最高1080p 和最高4K 解析度的影像。

## <a name="the-importance-of-quality-mrc"></a>品質 MRC 的重要性

無論是 Microsoft Store 頁面上的混合現實螢幕擷取畫面，還是在社交網路上共用捕捉內容的其他使用者，混合實境擷取媒體通常是使用者首次暴露于您的應用程式。 您可以使用 MRC 來示範您的應用程式、教育使用者、鼓勵使用者共用其混合的世界互動，以及進行使用者研究和解決問題。

## <a name="how-mrc-impacts-your-app"></a>MRC 如何影響您的應用程式

### <a name="enabling-mrc-in-your-app"></a>在您的應用程式中啟用 MRC

根據預設，應用程式不需要執行任何動作，就能讓使用者採用混合的事實捕獲。

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>為您應用程式中的 MRC 啟用改良的對齊

依預設，mixed reality capture 會將適當的眼睛全像影像輸出與相片/影片 (PV) 攝影機。 這兩個來源會使用目前執行的沉浸式應用程式所設定的焦點點來合併。

這表示焦點平面以外的全像全像，不會因為 PV 攝影機和右邊顯示器之間的實體距離而對齊。

#### <a name="set-the-focus-point"></a>設定焦點點

在) HoloLens 上 (的沉浸式應用程式，應該將其穩定平面的 [焦點放](../unity/focus-point-in-unity.md) 在您要的位置。 這可確保耳機和混合式現實捕捉中的最佳對齊。

如果未設定焦點點，穩定平面會預設為2個計量。

#### <a name="render-from-the-pv-camera-opt-in"></a>從 PV 攝影機轉譯 (加入宣告) 

HoloLens 2 新增了當混合的現實捕捉正在執行時，可讓沉浸式應用程式 **從 PV 攝影機** 轉譯的功能。 為了確保應用程式能夠正確地支援其他轉譯，應用程式必須加入宣告這項功能。

從 PV 攝影機轉譯可針對預設的 MRC 體驗提供下列改良功能：
* 全像您的實體環境的全息圖對齊，而手近距離的互動應該都是正確的。 避免在焦點點（而非焦點點）之間有位移，如您在預設的 MRC 中所見。
* 耳機中的適當眼睛不會遭到入侵，因為它不會用來呈現 MRC 輸出的全像影像。

有三個步驟可讓您從 PV 攝影機進行轉譯：
1. 啟用 PhotoVideoCamera HolographicViewConfiguration
2. 處理其他 HolographicCamera 轉譯
3. 從這個額外的 HolographicCamera 確認您的著色器和程式碼轉譯正確

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>啟用 DirectX 中的 PhotoVideoCamera HolographicViewConfiguration

若要選擇從 PV 攝影機轉譯，應用程式只會啟用 PhotoVideoCamera 的 [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)：
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>處理 DirectX 中的其他 HolographicCamera 轉譯

當應用程式已從 PV 攝影機加入宣告，且混合現實捕捉開始時：
1. 將引發 HolographicSpace 的 CameraAdded 事件。 如果應用程式目前無法處理相機，則可以延後此事件。
2. 一旦完成事件且沒有未完成的延期，HolographicCamera 將會出現在下一個 HolographicFrame 的 AddedCameras 清單中。

當混合式事實 capture (停止，或應用程式在混合式事實捕捉正在執行時停用 view 設定) ： HolographicCamera 將會出現在下一個 HolographicFrame 的 RemovedCameras 清單中，而且 HolographicSpace 的 CameraRemoved 事件將會引發。

已將 [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) 屬性新增至 HolographicCamera，以協助識別相機所屬的設定。

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>在 Unity 中啟用 PhotoVideoCamera HolographicViewConfiguration

> [!NOTE]
> 這需要 **unity 2018.4.13 f1**、 **unity 2019.3.0 f1** 或更新版本。

若要在使用 [Mixed Reality 工具](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)組時選擇從 pv 攝影機進行轉譯，請啟用 [Windows Mixed Reality 攝影機設定](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html) 提供者，並檢查 **從 pv 攝影機** 轉譯。

如果您不是使用「混合現實」工具組，您可以使用元件以 [手動方式加入宣告](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) ，如上面的 DirectX 所述。

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>處理 Unity 中的其他 HolographicCamera 轉譯

Unity 會自動為您完成這項操作。

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>在 Unreal 中啟用 PhotoVideoCamera HolographicViewConfiguration

> [!NOTE]
> 這需要 **Unreal Engine 4.25** 或更新版本。

若要選擇從 PV 相機呈現：

1. 呼叫 **SetEnabledMixedRealityCamera** 和 **ResizeMixedRealityCamera**
    * 使用 **Size X** 和 **Size Y** 值來設定影片大小。

![第三相機](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>處理 Unreal 中的其他 HolographicCamera 轉譯

Unreal 會自動為您完成這項操作。

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>確認著色器和程式碼支援其他攝影機

執行混合現實的捕獲，並檢查是否有不尋常的對齊、遺漏內容或效能問題。 適當地更新著色器和程式碼。

如果有某些場景無法支援轉譯成其他相機，您可以停用 PhotoVideoCamera 的 HolographicViewConfiguration。

### <a name="disabling-mrc-in-your-app"></a>在您的應用程式中停用 MRC

#### <a name="2d-app"></a>2D 應用程式

當混合的現實捕捉正在執行時，2D 應用程式可以選擇將其視覺內容遮蔽：
* 以 [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) 旗標呈現
* 使用 [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 旗標來建立應用程式的交換鏈
* 使用 Windows 10 2019 年5月更新，設定 ApplicationView 的 [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>沉浸式應用程式

沉浸式應用程式可以選擇從混合現實捕捉中排除其視覺內容：
* 設定 HolographicCameraRenderingParameter 的 [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) ，以停用其相關聯框架的混合現實 capture
* 設定 HolographicCamera 的 [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) ，以停用其相關聯的全像攝影相機的混合現實 capture

#### <a name="password-keyboard"></a>密碼鍵盤

使用 Windows 10 2019 年5月更新，在顯示密碼或 pin 鍵盤時，會自動從混合現實捕獲中排除視覺內容。

### <a name="knowing-when-mrc-is-active"></a>知道當 MRC 處於作用中狀態

[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)類別可供應用程式用來知道系統 mixed reality capture (針對音訊或影片) 執行時。

>[!NOTE]
>如果裝置上沒有混合現實 capture，AppCapture 的 [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可能會傳回 null。 也請務必在您的應用程式暫停時，取消註冊 CapturingChanged 事件，否則，可能會進入封鎖狀態。

### <a name="best-practices-hololens-specific"></a> (HoloLens 專用) 的最佳作法

在不需要其他開發工作的情況下，必須留意到 MRC 的工作，但在提供最佳的混合現實捕獲經驗時，有幾件事要注意。

**MRC 使用全像 [相機](locatable-camera.md) 的 Alpha 色板來 blend 影像**

最重要的步驟是確保您的應用程式會清除為透明黑色，而不是清除為不透明的黑色。 在 Unity 中，這會依預設使用 MixedRealityToolkit 來完成。 如果您是在非 Unity 中進行開發，您可能需要進行一行變更。

如果您的應用程式未清除為透明黑色，您可能會在 MRC 中看到一些成品：

**範例失敗**：內容周圍的黑色邊緣 (無法清除為透明黑色) 

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**失敗範例**：全像全像全螢幕的背景場景會顯示黑色。 在黑色背景中設定一個結果的背景 Alpha 值

![將背景 Alpha 值設定為1會導致黑色背景](images/clearopaqueblack-300px.png)

**預期的結果**：如果清除透明) 黑色，則會以真實世界 (預期的結果來適當地混合影像：

![如果清除透明黑色，則預期的結果](images/cleartransparentblack-300px.png)

**解決方案**：
* 將顯示為不透明黑色的任何內容變更為具有 Alpha 值0。
* 確定應用程式已清除為透明的黑色。
* Unity 預設會自動使用 MixedRealityToolkit 來清除，但如果它是非 Unity 應用程式，您應該修改與 ID3D11DeiceCoNtext：： ClearRenderTargetView 搭配使用的色彩， ( # A1。 您想要確保清楚透明的黑色 (0、0、0、0) ，而不是不透明的黑色 (0、0、0、1) 。

如果您想要的話，現在可以調整資產的 Alpha 值，但通常不需要這麼做。 大部分的情況下，MRCs 都看起來不錯。 MRC 假設預乘 Alpha。 Alpha 值只會影響 MRC 捕捉。

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>HoloLens 在 HoloLens 上啟用時的預期結果

下列適用于 HoloLens (第一代) 和 HoloLens 2，除非另有注明：

* 系統會將應用程式節流至 30-Hz 轉譯。 這會建立一些可供 MRC 執行的空間，因此應用程式不需要保留固定的預算保留，也不需要符合每 30 fps 的 MRC 影片記錄幀率
* 錄製/串流處理常式時，裝置上的全息圖內容可能會顯示為「閃爍」：文字可能會變得更難閱讀，而全息圖邊緣可能會變得更 jaggy (選擇在 **HoloLens 2** 上進行第三個攝影機轉譯，以避免此折衷) 
* 如果應用程式已啟用，則 MRC 照片和影片將會遵循應用程式的 [焦點點](../unity/focus-point-in-unity.md) ，以協助確保全像投影正確放置。 針對影片，焦點會經過平滑處理，如此一來，如果焦點深度的變更大幅改變，則可能會出現緩慢的漂移。 來自焦點點之不同深度的全像影像可能會顯示在現實世界的位移 (請參閱下方的範例，其中焦點點是設定為2個計量，但全像是放置在1個計量) 。

![2米的全像全像全球的全像投影。 接近或遠距離的全像投影可能會稍微位移。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>從您的應用程式內整合 MRC 功能

您的混合現實應用程式可以從應用程式中啟動 MRC 相片或影片捕獲，而您的應用程式也可以使用所捕捉的內容，而不需儲存至裝置的「相機變換」。 您可以建立自訂的「MRC 錄製器」，或利用內建的「相機捕捉」 UI。 

### <a name="mrc-with-built-in-camera-ui"></a>使用內建相機 UI 的 MRC

只要幾行程式碼，開發人員就可以使用 *[相機捕捉 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 來取得使用者所取得的混合現實照片或影片。

此 API 會啟動內建的「MRC 攝影機」 UI，讓使用者可以拍攝相片或影片，並將產生的捕獲傳回您的應用程式。 如果您需要新增自己的攝影機 UI 或較低層級的存取權來捕捉串流，您可以建立自訂的混合實境擷取錄製器。

### <a name="creating-a-custom-mrc-recorder"></a>建立自訂的 MRC 錄製器

雖然使用者一律可以使用系統 MRC 捕捉服務來觸發相片或影片，但應用程式可能會想要建立自訂相機應用程式，以在相機串流中包含全像 MRC 一樣的影像。 這可讓應用程式從使用者輸入開始進行捕捉、建立自訂錄製 UI，或自訂 MRC 設定來命名一些範例。

**HoloStudio 使用 MRC 效果新增自訂的 MRC 攝影機**

![HoloStudio 使用 MRC 效果新增自訂的 MRC 攝影機](images/cameraiconholostudio-300px.jpg)

Unity 應用程式應該會看到屬性 [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) ，以啟用全像。

其他應用程式也可以使用 [Windows Media Capture api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) 來控制相機，並新增 MRC 影片和音訊效果，以在靜止和影片中包含虛擬全像影像和應用程式音訊。

應用程式有兩個選項可新增效果：
* 舊版 API： [MediaCapture. AddEffectAsync ( # B1 ](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* 新的 Microsoft 建議 API (會傳回物件，讓您可以操控動態屬性) ： [MediaCapture. AddVideoEffectAsync ( # B3](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [MediaCapture.. AddAudioEffectAsync ( # B5](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) ，這需要應用程式建立自己的[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)和[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)執行。 請參閱 MRC [效果範例，例如使用方式。

>[!NOTE]
> Visual Studio 不會辨識 MixedRealityCapture 命名空間，但字串仍然有效。

**MixedRealityCapture. MixedRealityCaptureVideoEffect**) 的 MRC 影片效果 (

|  屬性名稱  |  類型  |  預設值  |  描述 |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))   |  1 (VideoRecord)   |  描述此效果用於哪個捕獲資料流程。 無法使用音訊。 |
|  HologramCompositionEnabled  |  boolean  |  true  |  用來啟用或停用影片捕獲中全像影像的旗標。 |
|  RecordingIndicatorEnabled  |  boolean  |  true  |  用來啟用或停用全息圖捕獲期間在螢幕上錄製指標的旗標。 |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  此旗標可啟用或停用由 HoloLens 追蹤器提供技術支援的影片穩定。 |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  設定用於視頻穩定的歷程記錄畫面格數目。 0從電源和效能的觀點來看，有0延遲且幾乎「免費」。 針對最高品質 (，建議使用15，但延遲和記憶體) 的15個框架成本。 |
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 (HoloLens) 1.0 (沉浸式耳機)   |  在 0.0 (完全透明) 至 1.0 (完全不透明的) ，設定全像影像的全域不透明度係數。 |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  如果有 2d UWP 應用程式顯示受保護的內容，則為啟用或停用會傳回空框架的旗標。 如果此旗標為 false，而 2d UWP 應用程式顯示受保護的內容，則會在耳機和混合式現實捕捉中，以受保護的內容材質取代 2d UWP 應用程式。 |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  啟用或停用的旗標，顯示全像攝影的隱藏區域網格和連續的內容。 |
| OutputSize | 大小 | 0, 0 | 在裁剪影片穩定之後，設定所需的輸出大小。 如果指定0或不正確輸出大小，則會選擇預設裁剪大小。 |
| PreferredHologramPerspective | UINT32 | **從** Windows 裝置入口網站中的相機設定轉譯 | 列舉用來指出應捕捉的全像攝影相機視圖設定： 0 (顯示) 表示不會要求應用程式從相片/攝影機轉譯，1 (PhotoVideoCamera) 將會要求應用程式從相片/視頻攝影機轉譯 (如果應用程式支援) 。 僅 HoloLens 2 支援 |

>[!NOTE]
> 您可以在 Windows 裝置入口網站中變更 **PreferredHologramPerspective** 的預設值，方法是前往 [ [混合實境擷取] 頁面](using-the-windows-device-portal.md#mixed-reality-capture) ，並取消核取 [ **從相機** 轉譯]。 此設定預設為 **1 (PhotoVideoCamera)**，但可以取消核取，將它設為 **0 (顯示)**。
>
> **PreferredHologramPerspective** 的預設值為 **0 (顯示** 2020 年6月更新 (Windows 全像2004版組建19041.1106 和 windows 全像1903組建 18362.1064) 的) 。

**MixedRealityCapture. MixedRealityCaptureAudioEffect) 的** MRC 音訊效果 (

| 屬性名稱 | 類型 | 預設值 | 描述 |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (Mic 和系統音訊)  | 用來指出應使用哪些音訊來源的列舉： 0 (僅限 Mic 音訊) 、1 (僅限系統音訊) 、2 (Mic 和系統音訊)  |
| LoopbackGain | FLOAT | Windows 裝置入口網站中的 **應用程式音訊增益** 設定 | 適用于系統音訊音量的增益。 範圍從0.0 到5.0。 僅 HoloLens 2 支援 |
| MicrophoneGain | FLOAT | Windows 裝置入口網站中的 **Mic 音訊增益** 設定 | 適用于 mic 音量的增益。 範圍從0.0 到5.0。 僅 HoloLens 2 支援 |

>[!NOTE]
> 您可以在 Windows 裝置入口網站中變更 **LoopbackGain** 或 **MicrophoneGain** 的預設值，方法是移至 [ [混合實境擷取] 頁面](using-the-windows-device-portal.md#mixed-reality-capture) ，然後調整其各自設定旁邊的滑杆。 這兩個設定預設為 **1.0**，但可以設定為 **0.0** 與 **5.0** 之間的任何值。
>
> 在2020年6月的更新中，您可以使用 Windows 裝置入口網站來設定預設增益值 (Windows 全像2004組建19041.1106 和 Windows 全像版本1903組建 18362.1064) 。

### <a name="simultaneous-mrc-limitations"></a>同時 MRC 限制

有多個應用程式同時存取 MRC 有一些限制。

#### <a name="photovideo-camera-access"></a>相片/攝影機存取

相片/攝影機受限於可同時存取它的進程數目。 當處理常式錄製影片或拍攝相片時，任何其他程式將無法取得相片/攝影機。  (這適用于混合實境擷取和標準相片/影片捕獲) 

使用 HoloLens 2 時，應用程式可以使用 MediaCaptureInitializationSettings [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) 屬性，指出他們如果不需要對相片/攝影機進行獨佔控制，則會想要執行 SharedReadOnly。 捕捉的解析度和幀數將限制為其他應用程式已設定相機來提供。

##### <a name="built-in-mrc-photovideo-camera-access"></a>內建的 MRC 相片/攝影機存取

內建于透過 Cortana、[開始] 功能表、硬體快捷方式、Miracast、Windows 裝置入口網站) 的 Windows 10 (的 MRC 功能：
* 預設會以 ExclusiveControl 執行

不過，每個子系統都已新增支援，以在共用模式下運作：
* 如果應用程式要求相片/攝影機的 ExclusiveControl 存取權，內建的 MRC 將會自動停止使用相片/攝影機，因此應用程式的要求將會成功
* 如果在應用程式 ExclusiveControl 時啟動內建的 MRC，內建的 MRC 將會以 SharedReadOnly 模式執行

此共用模式功能有某些限制：
* 透過 Cortana、硬體快速鍵或 [開始] 功能表的相片：需要 Windows 10 2018 年4月更新 (或更新版本) 
* 透過 Cortana、硬體快速鍵或 [開始] 功能表的影片：需要 Windows 10 2018 年4月更新 (或更新版本) 
* 透過 Miracast 的串流處理 MRC：需要 Windows 10 2018 年10月更新 (或更新版本) 
* 透過 Windows 裝置入口網站或透過 HoloLens 附屬應用程式串流處理 MRC：需要 HoloLens 2

>[!NOTE]
> 當另一個應用程式正在使用相片/攝影機時，內建的 MRC 攝影機 UI 的解析度和畫面播放速率可能會從其正常值減少。

#### <a name="mrc-access"></a>MRC 存取

有了 Windows 10 2018 年4月更新，存取 MRC 串流的多個應用程式就不再有限制 (不過，相片/攝影機的存取權仍有) 的限制。

在 Windows 10 2018 年4月更新之前，應用程式的自訂 MRC 錄製器與系統 MRC 的互斥 (捕獲相片、捕獲影片或從 Windows 裝置入口網站) 進行串流。

## <a name="see-also"></a>另請參閱

* [混合實境擷取](../../mixed-reality-capture.md)
* [觀眾檢視](spectator-view.md)
* [Unity 開發總覽](../unity/unity-development-overview.md)
* [Unreal 開發概觀](../unreal/unreal-development-overview.md)
