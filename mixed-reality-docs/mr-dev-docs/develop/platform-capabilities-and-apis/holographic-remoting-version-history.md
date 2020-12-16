---
title: 全像遠端版本歷程記錄
description: HoloLens 2 上全像攝影的版本歷程記錄。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、遠端、全像全像遠端、版本歷程記錄、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: bda4d4a304c6d13a55ad0433fcd248d8513fa6a0
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530383"
---
# <a name="holographic-remoting-version-history"></a>全像遠端版本歷程記錄

> [!IMPORTANT]
> 本指南專為 HoloLens 2 上的全像攝影遠端所特有。

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
* 修正了 [HolographicCamera. LeftViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) 和 HolographicCamera 的問題。當您從 Windows Mixed Reality 耳機進行串流處理時， [RightViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) 不會傳回任何隱藏的區域網格頂點。
* 修正損毀，這種情況可能會導致網路連線不佳。

## <a name="version-221-july-6-2020"></a>版本 2.2.1 (2020 年7月6日) <a name="v2.2.1"></a>
> [!IMPORTANT]
> [2.2.0](holographic-remoting-version-history.md#v2.2.0)版本的[Windows 應用程式認證套件](https://developer.microsoft.com/windows/downloads/app-certification-kit/)驗證將會失敗。 如果您是在版本 [2.2.0](holographic-remoting-version-history.md#v2.2.0) ，而且想要將應用程式提交至 Microsoft store，請更新為至少版本2.2.1。
* 修正 [Windows 應用程式認證套件](https://developer.microsoft.com/windows/downloads/app-certification-kit/) 合規性問題。

## <a name="version-220-july-1-2020"></a>版本 2.2.0 (2020 年7月1日) <a name="v2.2.0"></a>
* 全像「全像遠端播放機」現在可以安裝在執行 [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)的電腦上，因此可以串流到沉浸式耳機。
* 您現在可以透過[SpatialInteractionSource](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)來取出[動態控制器](../../design/motion-controllers.md)和控制器專屬的資料，以支援移動控制站。
* 現在支援[SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference) ，而且可以透過[SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)來取出目前的階段。 此外，也可以透過 SpatialStageFrameOfReference 來要求新階段 [。 RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)。
* 在先前的版本中，會由全像遠端播放程式在玩家端處理預測。 從版本2.2.0 開始，全像攝影遠端處理有時間同步處理，而由遠端應用程式完全完成預測。 在困難的網路情況下，使用者也應預期改良的全像影像穩定性。

## <a name="version-213-may-25-2020"></a>版本 2.1.3 (2020 月25日) <a name="v2.1.3"></a>
* 已變更 [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 事件的行為。 在舊版中，在透過 [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)建立下一個畫面格時，**不** 保證新增的 [HolographicCamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera)也具有有效的 [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose) 。 從版本2.1.3 開始， [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 會與來自全像的遠端播放播放程式的姿勢資料進行同步處理。 使用者可能會預期當相機新增時，也會在下一個畫面上提供該相機的有效 [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose) 。
* 已 **停用** DepthBufferStreamResolution，可用來透過 RemoteContext.ConfigureDepthVideoStream 停用深度緩衝區串流。 請注意，如果使用 [HolographicCameraRenderingParameters，CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) 將會失敗，並 *E_ILLEGAL_METHOD_CALL*。
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
* 已新增對 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)的支援。 

## <a name="version-2020-february-2-2020"></a>2020年2月2日 (版本2.0.20 版) <a name="v2.0.20"></a>
* 修正導致損毀的各種 bug。

## <a name="version-2018-december-17-2019"></a>版本2.0.18 版 (2019 年12月17日) <a name="v2.0.18"></a>
* 新增對[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)的支援
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
* 新增對[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支援
* 新增介面 ```IPlayerContext2``` (由 ```PlayerContext```) 提供下列成員來執行：
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  屬性。
* 已 ```Failed_RemoteFrameTooOld``` 將值新增至 ```BlitResult```
* 穩定性與可靠性的改進

## <a name="version-208-august-20-2019"></a>版本 2.0.8 (2019 年8月20日) <a name="v2.0.8"></a>

* 修正使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)做為參數呼叫[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)時的損毀。
* 穩定性與可靠性的改進

## <a name="version-207-july-26-2019"></a>版本 2.0.7 (2019 年7月26日) <a name="v2.0.7"></a>

* HoloLens 2 的全像全像的全像公開發行。

## <a name="see-also"></a>另請參閱
* [使用 Windows Mixed Reality Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-openxr.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [全像遠端的疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
