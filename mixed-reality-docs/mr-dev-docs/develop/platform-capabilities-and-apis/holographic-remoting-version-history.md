---
title: 全像遠端版本歷程記錄
description: 隨時掌握 HoloLens 2 的全像「全像」遠端功能的版本歷程記錄。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 06/10/2021
ms.topic: article
keywords: HoloLens、遠端、全像全像遠端、版本歷程記錄、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: dae7bc0dac792cbe1a8472415d5e9fa34532e918
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908225"
---
# <a name="holographic-remoting-version-history"></a>全像遠端版本歷程記錄

> [!IMPORTANT]
> 本指南專為 HoloLens 2 上的全像攝影遠端所特有。

## <a name="version-260-june-10-2021"></a>版本 2.6.0 (2021 年6月10日) <a name="v2.6.0"></a>
* 使用 OpenXR API 的全像攝影遠端功能現在支援：
  * 新的 XR_MSFT_holographic_remoting_speech 延伸模組，可讓應用程式以各種語言接聽自訂語音命令。
  * XR_MSFT_scene_understanding 擴充功能，可在使用者的環境中為應用程式提供平面、網格和物件的結構化、高階標記法，以啟用空間感知應用程式的開發。 不過，有一點要注意的是，XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT 是 xrComputeNewSceneMSFT 唯一支援的一致性。
  * XR_MSFT_spatial_graph_bridge 擴充功能，可讓應用程式建立 XrSpace 控制碼，以追蹤其他 Windows Mixed Reality 裝置平臺程式庫或 Api 的空間圖形節點。 不過，有一點要注意的是，XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT 是 xrCreateSpatialGraphNodeSpaceMSFT 唯一支援的節點類型。 
* 使用 Mixed Reality API 的全像攝影遠端功能現在支援：
  * SpatialGraphInteropPreview CreateCoordinateSystemForNode 多載，可讓應用程式追蹤靜態空間圖形節點，讓使用者可以在其環境中考慮位置和專案。
* 使用 OpenXR 和 Mixed Reality Api 的全像是，現在支援：
  * MixedReality. SceneUnderstanding SDK 可讓應用程式計算使用者 (的場景描述，例如牆壁、地面和表面，) 提供四邊形、網格和內容放置提示。
  * MixedReality，可讓應用程式追蹤偵測到的 QR 代碼的位置、大小和內容。
* OpenXR 遠端範例已更新為包含： 
  * 使用 XR_MSFT_holographic_remoting_speech 擴充功能的範例。
* 混合現實遠端範例已更新為包含：  
  * 使用 MixedReality. SceneUnderstanding SDK 的範例。
  *  (使用 MixedReality 的範例，其會取代先前的 QR 代碼偵測機制) 。
* 「全像遠端播放」播放程式現在會在建立連接時顯示載入動畫。
* 修正 OpenXR API 執行時間與混合現實 API 範例中 RenderDoc 相容性的問題。
* 各種 bug 修正和穩定性改進。

## <a name="version-250-february-12-2021"></a>版本 2.5.0 (2021 年2月12日) <a name="v2.5.0"></a>
* 使用 [OPENXR API](../native/openxr.md) 的全像攝影遠端功能現在支援：
  * XR_MSFT_spatial_anchor 延伸模組。 此延伸模組可讓應用程式建立空間錨點，這是使用者的實體環境中，執行時間將追蹤的任意可空間點。
  * XR_MSFT_controller_model 延伸模組。 此擴充功能會提供一種機制，以載入控制器的 GLTF 模型。
  * 自訂資料通道是 XR_MSFT_holographic_remoting 擴充功能的一部分。 [OpenXR 遠端範例](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中顯示的範例。
* 改進玩家與遠端端之間的同步處理。 這可讓您以動態方式變更姿勢和框架緩衝，以確保遠端轉譯的內容順暢地以預期的目標畫面播放速率到達顯示器。
* 改進了可透過 Microsoft Store 使用的全像遠端播放播放程式效能。 在 HoloLens 2，播放現在會在每秒60個畫面格上執行。
* 優化的空間介面網格傳輸，可透過遠端應用程式的 [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) 來進行查詢。
* 修正呼叫 SpatialAnchorManager 方法或釋出錨點在中斷連接時造成例外狀況的問題。
* 修正關閉 PlayerCoNtext 或 RemoteCoNtext 實例時，導致損毀的執行緒問題。
* 桌上型電腦上的全像遠端播放機：未安裝 Windows Mixed Reality 時顯示錯誤訊息，而不是以無訊息方式關閉。
* 許多其他 bug 修正和穩定性改進。

## <a name="version-241-january-22-2021"></a>版本 2.4.1 (2021 年1月22日) <a name="v2.4.1"></a>

* 修正 SpatialAnchorManager：： RequestStoreAsync 在連接時呼叫時無法可靠地運作的問題。
* 修正 SpatialAnchorManager：： TrySave 未找出問題錨點時，無法正確儲存錨點的問題。

## <a name="version-240-december-1-2020"></a>版本 2.4.0 (2020 年12月1日) <a name="v2.4.0"></a>

* 全像攝影遠端功能現在支援使用 [OPENXR API](../native/openxr.md)撰寫遠端應用程式。 請參閱 [使用 OpenXR Api 撰寫全像的遠端執行遠端應用程式](holographic-remoting-create-remote-openxr.md) 以開始使用。
* Bug 修正和穩定性改進。

## <a name="version-231-october-10-2020"></a>2020年10月10日 (版本 2.3.1) <a name="v2.3.1"></a>

* 修正了遠端引發預測的回歸，這會造成視覺抖動。
* 已實 PerceptionDeviceSetCreateFactoryOverride，可確保在全像全像的情況下隨附的 PerceptionDevice.dll 不會干擾 Windows 10 隨附的版本。

## <a name="version-230-october-2-2020"></a>版本 2.3.0 (2020 年10月2日) <a name="v2.3.0"></a>

* 已修正當攝影遠端播放程式暫停時可能發生的損毀。
* 穩定性改進。

## <a name="version-223-august-28-2020"></a>版本 2.2.3 (2020 年8月28日) <a name="v2.2.3"></a>

* Bug 修正和穩定性改進。

## <a name="version-222-july-10-2020"></a>2020年7月10日版本 2.2.2 () <a name="v2.2.2"></a>

* 修正了 [HolographicCamera. LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) 和 HolographicCamera 的問題。當您從 Windows Mixed Reality 耳機進行串流處理時， [RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) 不會傳回任何隱藏的區域網格頂點。
* 修正損毀，這種情況可能會導致網路連線不佳。

## <a name="version-221-july-6-2020"></a>版本 2.2.1 (2020 年7月6日) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [2.2.0](holographic-remoting-version-history.md#v2.2.0)版本的[Windows 應用程式認證套件](https://developer.microsoft.com/windows/downloads/app-certification-kit/)驗證將會失敗。 如果您是在版本 [2.2.0](holographic-remoting-version-history.md#v2.2.0) ，而且想要將您的應用程式提交至 Microsoft store p 租用期更新為至少版本2.2.1。
* 修正 [Windows 應用程式認證套件](https://developer.microsoft.com/windows/downloads/app-certification-kit/) 合規性問題。

## <a name="version-220-july-1-2020"></a>版本 2.2.0 (2020 年7月1日) <a name="v2.2.0"></a>

* 全像「全像遠端播放機」現在可以安裝在執行 [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)的電腦上，因此可以串流到沉浸式耳機。
* 您現在可以透過[SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)來取出[動態控制器](../../design/motion-controllers.md)和控制器專屬的資料，以支援移動控制站。
* 現在支援[SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) ，而且可以透過[SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)來取出目前的階段。 此外，也可以透過 SpatialStageFrameOfReference 來要求新階段 [。 RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)。
* 在先前的版本中，會由全像遠端播放程式在玩家端處理預測。 從版本2.2.0 開始，全像攝影遠端處理有時間同步處理，而由遠端應用程式完全完成預測。 在困難的網路情況下，使用者也應預期改良的全像影像穩定性。

## <a name="version-213-may-25-2020"></a>版本 2.1.3 (2020 月25日) <a name="v2.1.3"></a>

* 已變更 [HolographicSpace. CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 事件的行為。 在舊版中，在透過 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)建立下一個畫面格時，**不** 保證新增的 [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera)也具有有效的 [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) 。 從版本2.1.3 開始， [HolographicSpace. CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 會與來自全像的遠端播放播放程式的姿勢資料進行同步處理。 使用者可能會預期當相機新增時，也會在下一個畫面上提供該相機的有效 [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) 。
* 已 **停用** DepthBufferStreamResolution，可用來透過 RemoteContext.ConfigureDepthVideoStream 停用深度緩衝區串流。 請注意，如果使用 [HolographicCameraRenderingParameters，CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) 將會失敗，並 *E_ILLEGAL_METHOD_CALL*。
* 全像是「全像遠端播放機」的啟動畫面已經過重新設計，現在不會封鎖使用者的觀點。
* 穩定性改進與 bug 修正。

## <a name="version-212-april-5-2020"></a>版本 2.1.2 (2020 年4月5日) <a name="v2.1.2"></a>

* 使用小於2.1.0 的版本，修正最新全像全像遠端播放機和遠端應用程式之間的音訊回溯相容性問題。
* 固定空間錨點問題，此問題未預期地關閉全像「全像」遠端播放機。 此問題也會影響自訂玩家。

## <a name="version-211-march-20-2020"></a>版本 2.1.1 (2020 年3月20日) <a name="v2.1.1"></a>

* 修正使用 AMD Gpu 時遠端應用程式的影片編碼問題。
* 全像遠端播放機效能改進。

## <a name="version-210-march-11-2020"></a>版本 2.1.0 (2020 年3月11日) <a name="v2.1.0"></a>

* 切換網路傳輸以使用 [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP。 安全連線現在會使用 [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 。 請注意，「全像」的「全像」、「全像」版本的 [遠端播放](holographic-remoting-player.md) 程式仍與所有先前 為了讓新的網路傳輸受益，全像是「全像遠端播放機」和「遠端應用程式」，必須使用版本2.1.0。
* 已新增對 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)的支援。 

## <a name="version-2020-february-2-2020"></a>2020年2月2日 (版本2.0.20 版) <a name="v2.0.20"></a>

* 修正導致損毀的各種 bug。

## <a name="version-2018-december-17-2019"></a>版本2.0.18 版 (2019 年12月17日) <a name="v2.0.18"></a>

* 新增對[HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)的支援
* 修正導致損毀的各種 bug。
* 修正了 HolographicSpace 需要 CameraAdded 回呼才能接受，並在 HolographicFrame 中顯示為已新增攝影機的 bug。

## <a name="version-2016-november-11-2019"></a>版本 2.0.16 (2019 年11月11日) <a name="2.0.16"></a>

* 修正 QR 代碼追蹤中的鎖死。
* 已修正 unhandeled 例外狀況，因為在主執行緒中有封鎖等候。

## <a name="version-2014-october-26-2019"></a>版本2.0.14 版 (2019 年10月26日) <a name="v2.0.14"></a>

* 支援新的 PerceptionDevice Api (Windows 10 2019 年11月更新) 。
* 修正問題，這會導致 SpatialGestureRecognizer 觸發暫停手勢事件。
* 修正使用 SpatialSurfaceObserver. SetBoundingVolume 時的執行緒問題。

## <a name="version-2012-october-18-2019"></a>版本 2.0.12 (2019 年10月18日) <a name="v2.0.12"></a>

* 修正使用 NavigationRail (X/Y/Z) 時，SpatialGestureRecognizer 中的損毀。

## <a name="version-2010-october-10-2019"></a>版本2.0.10 版 (2019 年10月10日) <a name="v2.0.10"></a>

* 已修正使用 VR 控制器的觸發程式按鈕時的損毀。 全像「全像」的遠端處理並不完全支援控制器，如果與 HoloLens 2 配對，則只有 [觸發程式] 按鈕和 [Windows] 按鈕

## <a name="version-209-september-19-2019"></a>版本 2.0.9 (2019 年9月19日) <a name="v2.0.9"></a>

* 新增對[SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter)的支援
* 新增介面 ```IPlayerContext2``` (由 ```PlayerContext```) 提供下列成員來執行：
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  屬性。
* 已 ```Failed_RemoteFrameTooOld``` 將值新增至 ```BlitResult```
* 穩定性與可靠性的改進

## <a name="version-208-august-20-2019"></a>版本 2.0.8 (2019 年8月20日) <a name="v2.0.8"></a>

* 修正使用[IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)做為參數呼叫[HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)時的損毀。
* 穩定性與可靠性的改進

## <a name="version-207-july-26-2019"></a>版本 2.0.7 (2019 年7月26日) <a name="v2.0.7"></a>

* HoloLens 2 的全像全像的全像公開發行。

## <a name="see-also"></a>另請參閱

* [使用 Windows Mixed Reality Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-openxr.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [全像遠端的疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)