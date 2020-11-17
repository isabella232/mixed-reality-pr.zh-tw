---
title: 全像遠端的疑難排解和限制
description: HoloLens 2 上全像攝影的疑難排解步驟。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality，全像全像全像）、遠端轉譯、網路轉譯、HoloLens、遠端全息全像、疑難排解、說明、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 9577f9f028987be71fdb9cd839f86980db350f02
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679577"
---
# <a name="holographic-remoting-troubleshooting"></a>全像遠端處理疑難排解

> [!IMPORTANT]
> 本指南專為 HoloLens 2 上的全像攝影遠端所特有。

## <a name="spectre-mitigated-libraries-not-found"></a>找不到 Spectre 降低的程式庫。

內建的遠端範例應用程式在發行設定中啟用了 Spectre 的風險降低 (/Qspectre) 。

如果您收到嚴重的連結器錯誤，指出無法開啟 ' vccorlib.h .lib '，請確定您的 Visual Studio 工作負載包含 Spectre 緩和的程式庫。 如需詳細資訊，請參閱 https://aka.ms/Ofhn4c。

## <a name="speech"></a>語音

全像是「全像」遠端播放機支援診斷覆迭，藉由說出 ```Enable Diagnostics``` 並停用，您可以藉由說出 ```Disable Diagnostics``` 如果您無法使用這些語音命令，您也可以使用做為 URL 的網頁瀏覽器來啟動全像遠端播放機 ```ms-holographic-remoting:?stats``` 。

## <a name="h265-video-codec-not-available"></a>H265 視頻編碼器無法使用

當您在遠端應用程式中使用 H265 video 編解碼器時，必須安裝 [HEVC 影片擴充](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 功能。 如果您遇到已安裝但無法使用編解碼器的問題，請參閱 [疑難排解](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 指南。

## <a name="limitations"></a>限制

下列 Api 目前 **不** 支援使用全像 HoloLens 2 的全像遠端，而且除非另有說明，否則將會引發 ```ERROR_NOT_SUPPORTED``` 錯誤：

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - 從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援
  - 在先前的版本中，一律會引發錯誤。
* [HolographicCamera.IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援
  - 先前的版本不會失敗，但轉譯目標大小將不會變更。
* [HolographicCameraPose.OverrideProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - 不會失敗，但深度緩衝區將無法進行遠端處理。
  - 從版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)開始支援
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - 查詢 HolographicViewConfigurationKind 時，PhotoVideoCamera 一律會傳回 ```nullptr``` 。
  - 從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援
  - 在先前的版本中，一律會引發錯誤。
* [HolographicSpace.CreateFramePresentationMonitor](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay.GetDefault](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - 如果在建立連接之前呼叫，將會報告錯誤。


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation. AbsoluteAngularAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. AbsoluteAngularVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. AbsoluteLinearAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. AbsoluteLinearVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援
  - 在先前的版本中，一律會傳回 ```nullptr``` 。
* [SpatialStageFrameOfReference.RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援
* [SpatialAnchor.RemovedByUser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - 從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。 
  - 在先前的版本中，一律會傳回 ```nullptr``` 。 
* [SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - 從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。 
  - 在舊版中，非同步作業一律會使用完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。
* [SpatialAnchorTransferManager.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - 非同步作業一律會使用完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - 非同步作業一律會使用完成 ```false``` 。
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - 非同步作業一律會使用完成 ```nullptr``` 。

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource 控制器](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - 從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>另請參閱
* [全像遠端版本歷程記錄](holographic-remoting-version-history.md)
* [撰寫全像攝影遠端應用程式](holographic-remoting-create-host.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
