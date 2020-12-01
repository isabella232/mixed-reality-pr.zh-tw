---
title: 全像遠端的疑難排解和限制
description: HoloLens 2 上全像攝影的疑難排解步驟。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality，全像全像全像）、遠端轉譯、網路轉譯、HoloLens、遠端全息全像、疑難排解、說明、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: ca0e4b3a43eae5be09f2c0bfbee9056cd847787c
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443604"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="98a36-104">全像遠端處理疑難排解</span><span class="sxs-lookup"><span data-stu-id="98a36-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98a36-105">本指南專為 HoloLens 2 上的全像攝影遠端所特有。</span><span class="sxs-lookup"><span data-stu-id="98a36-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="98a36-106">找不到 Spectre 降低的程式庫。</span><span class="sxs-lookup"><span data-stu-id="98a36-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="98a36-107">內建的遠端範例應用程式在發行設定中啟用了 Spectre 的風險降低 (/Qspectre) 。</span><span class="sxs-lookup"><span data-stu-id="98a36-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="98a36-108">如果您收到嚴重的連結器錯誤，指出無法開啟 ' vccorlib.h .lib '，請確定您的 Visual Studio 工作負載包含 Spectre 緩和的程式庫。</span><span class="sxs-lookup"><span data-stu-id="98a36-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="98a36-109">如需詳細資訊，請參閱 https://aka.ms/Ofhn4c。</span><span class="sxs-lookup"><span data-stu-id="98a36-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="speech"></a><span data-ttu-id="98a36-110">語音</span><span class="sxs-lookup"><span data-stu-id="98a36-110">Speech</span></span>

<span data-ttu-id="98a36-111">全像是「全像」遠端播放機支援診斷覆迭，藉由說出 ```Enable Diagnostics``` 並停用，您可以藉由說出 ```Disable Diagnostics```</span><span class="sxs-lookup"><span data-stu-id="98a36-111">The Holographic Remoting Player supports a diagnostics overlay which can be enabled by saying ```Enable Diagnostics``` and disabled by saying ```Disable Diagnostics```.</span></span> <span data-ttu-id="98a36-112">如果您無法使用這些語音命令，您也可以使用做為 URL 的網頁瀏覽器來啟動全像遠端播放機 ```ms-holographic-remoting:?stats``` 。</span><span class="sxs-lookup"><span data-stu-id="98a36-112">If you have trouble with these voice commands you can also launch the Holographic Remoting player via a web browser using ```ms-holographic-remoting:?stats``` as an URL.</span></span>

## <a name="h265-video-codec-not-available"></a><span data-ttu-id="98a36-113">H265 視頻編碼器無法使用</span><span class="sxs-lookup"><span data-stu-id="98a36-113">H265 video codec not available</span></span>

<span data-ttu-id="98a36-114">當您在遠端應用程式中使用 H265 video 編解碼器時，必須安裝 [HEVC 影片擴充](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 功能。</span><span class="sxs-lookup"><span data-stu-id="98a36-114">You need to install the [HEVC Video Extensions](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) when using H265 video codec in your remote app.</span></span> <span data-ttu-id="98a36-115">如果您遇到已安裝但無法使用編解碼器的問題，請參閱 [疑難排解](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 指南。</span><span class="sxs-lookup"><span data-stu-id="98a36-115">If you run into issues where the codec is installed but can't be used, check out [troubleshooting](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) guide.</span></span>

## <a name="limitations"></a><span data-ttu-id="98a36-116">限制</span><span class="sxs-lookup"><span data-stu-id="98a36-116">Limitations</span></span>

<span data-ttu-id="98a36-117">下列 Api 目前 **不** 支援使用全像 HoloLens 2 的全像遠端，而且除非另有說明，否則將會引發 ```ERROR_NOT_SUPPORTED``` 錯誤：</span><span class="sxs-lookup"><span data-stu-id="98a36-117">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="98a36-118">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="98a36-118">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="98a36-119">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="98a36-119">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="98a36-120">從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援</span><span class="sxs-lookup"><span data-stu-id="98a36-120">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="98a36-121">在先前的版本中，一律會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="98a36-121">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="98a36-122">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="98a36-122">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="98a36-123">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="98a36-123">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="98a36-124">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="98a36-124">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="98a36-125">先前的版本不會失敗，但轉譯目標大小將不會變更。</span><span class="sxs-lookup"><span data-stu-id="98a36-125">On previous versions does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="98a36-126">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="98a36-126">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="98a36-127">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="98a36-127">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="98a36-128">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="98a36-128">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - <span data-ttu-id="98a36-129">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="98a36-129">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="98a36-130">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="98a36-130">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="98a36-131">不會失敗，但深度緩衝區將無法進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="98a36-131">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="98a36-132">從版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="98a36-132">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="98a36-133">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="98a36-133">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="98a36-134">查詢 HolographicViewConfigurationKind 時，PhotoVideoCamera 一律會傳回 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="98a36-134">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="98a36-135">從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援</span><span class="sxs-lookup"><span data-stu-id="98a36-135">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="98a36-136">在先前的版本中，一律會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="98a36-136">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="98a36-137">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="98a36-137">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="98a36-138">HolographicDisplay.GetDefault</span><span class="sxs-lookup"><span data-stu-id="98a36-138">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="98a36-139">如果在建立連接之前呼叫，將會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="98a36-139">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="98a36-140">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="98a36-140">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="98a36-141">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="98a36-141">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="98a36-142">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="98a36-142">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="98a36-143">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="98a36-143">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="98a36-144">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="98a36-144">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="98a36-145">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="98a36-145">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="98a36-146">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="98a36-146">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="98a36-147">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="98a36-147">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="98a36-148">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="98a36-148">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="98a36-149">在先前的版本中，一律會傳回 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="98a36-149">On previous versions always returns ```nullptr```.</span></span>
* [<span data-ttu-id="98a36-150">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="98a36-150">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - <span data-ttu-id="98a36-151">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="98a36-151">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="98a36-152">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="98a36-152">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="98a36-153">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="98a36-153">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="98a36-154">從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。</span><span class="sxs-lookup"><span data-stu-id="98a36-154">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="98a36-155">在先前的版本中，一律會傳回 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="98a36-155">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="98a36-156">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="98a36-156">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="98a36-157">從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。</span><span class="sxs-lookup"><span data-stu-id="98a36-157">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="98a36-158">在舊版中，非同步作業一律會使用完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="98a36-158">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="98a36-159">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="98a36-159">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="98a36-160">非同步作業一律會使用完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="98a36-160">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="98a36-161">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="98a36-161">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="98a36-162">非同步作業一律會使用完成 ```false``` 。</span><span class="sxs-lookup"><span data-stu-id="98a36-162">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="98a36-163">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="98a36-163">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="98a36-164">非同步作業一律會使用完成 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="98a36-164">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="98a36-165">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="98a36-165">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="98a36-166">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="98a36-166">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="98a36-167">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="98a36-167">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="98a36-168">SpatialInteractionSource 控制器</span><span class="sxs-lookup"><span data-stu-id="98a36-168">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - <span data-ttu-id="98a36-169">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="98a36-169">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>

[<span data-ttu-id="98a36-170">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="98a36-170">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="98a36-171">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="98a36-171">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="98a36-172">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="98a36-172">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="98a36-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98a36-173">See Also</span></span>
* [<span data-ttu-id="98a36-174">全像遠端版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="98a36-174">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="98a36-175">使用 Windows 混合 Realiy Api 撰寫全像遠端執行遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="98a36-175">Writing a Holographic Remoting remote app using Windows Mixed Realiy APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="98a36-176">使用 OpenXR Api 撰寫全像遠端執行遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="98a36-176">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="98a36-177">撰寫自訂全像攝影遠端播放應用程式</span><span class="sxs-lookup"><span data-stu-id="98a36-177">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="98a36-178">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="98a36-178">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="98a36-179">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="98a36-179">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
