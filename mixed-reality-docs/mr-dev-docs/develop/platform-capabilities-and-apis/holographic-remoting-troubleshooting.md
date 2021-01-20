---
title: 全像遠端的疑難排解和限制
description: 尋找 HoloLens 2 裝置上的全像「全像」遠端功能的疑難排解資源和指示。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality，全像全像全像）、遠端轉譯、網路轉譯、HoloLens、遠端全息全像、疑難排解、說明、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 429ca7364d82e1713af059aa3c6da01852283120
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583829"
---
# <a name="holographic-remoting-troubleshooting"></a>全像遠端處理疑難排解

> [!IMPORTANT]
> 本指南專為 HoloLens 2 上的全像攝影遠端所特有。

## <a name="spectre-mitigated-libraries-not-found"></a>找不到 Spectre 降低的程式庫。

內建的遠端範例應用程式在發行設定中啟用了 Spectre 的風險降低 (/Qspectre) 。

如果您的 *vccorlib.h 無法開啟* 嚴重錯誤，請確定您的 Visual Studio 工作負載包含 Spectre 緩和連結 [庫](/cpp/build/reference/qspectre)

## <a name="speech"></a>語音

全像是「全像」遠端播放機支援診斷重迭，您可以藉由說出 ```Enable Diagnostics``` 並停用它來啟用 ```Disable Diagnostics``` 。 如果您無法使用這些語音命令，您也可以使用做為 URL 的網頁瀏覽器來啟動全 ```ms-holographic-remoting:?stats``` 像遠端播放機。

## <a name="h265-video-codec-not-available"></a>H265 視頻編碼器無法使用

在遠端應用程式中使用 H265 video 編解碼器時，請安裝 [HEVC 影片擴充](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 功能。 如果您遇到已安裝但無法使用編解碼器的問題，請參閱 [疑難排解](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 指南。

## <a name="limitations"></a>限制

下列 Api 目前 **不** 支援使用全像 HoloLens 2 的全像的遠端處理，除非另有說明，否則會引發 ```ERROR_NOT_SUPPORTED``` 錯誤：

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - 從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援
  - 在先前的版本中，一律會引發錯誤。
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援
  - 先前的版本不會失敗，但轉譯目標大小也不會變更。
* [HolographicCameraPose.OverrideProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - 能源部。
  - 從版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)開始支援
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - 查詢 HolographicViewConfigurationKind 時，PhotoVideoCamera 一律會傳回 ```nullptr``` 。
  - 從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援
  - 在先前的版本中，一律會引發錯誤。
* [HolographicSpace.CreateFramePresentationMonitor](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay.GetDefault](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - 如果在建立連接之前呼叫，將會報告錯誤。


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [SpatialLocation. AbsoluteAngularAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. AbsoluteAngularVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. AbsoluteLinearAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. AbsoluteLinearVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援
  - 在先前的版本中，一律會傳回 ```nullptr``` 。
* [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援
* [SpatialAnchor.RemovedByUser](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - 從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。 
  - 在先前的版本中，一律會傳回 ```nullptr``` 。 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - 從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。 
  - 在舊版中，非同步作業一律會使用完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。
* [SpatialAnchorTransferManager.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - 非同步作業一律會使用完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - 非同步作業一律會使用完成 ```false``` 。
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - 非同步作業一律會使用完成 ```nullptr``` 。

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource 控制器](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>另請參閱
* [全像遠端版本歷程記錄](holographic-remoting-version-history.md)
* [使用 Windows Mixed Reality Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-openxr.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [全像攝影遠端軟體授權條款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)