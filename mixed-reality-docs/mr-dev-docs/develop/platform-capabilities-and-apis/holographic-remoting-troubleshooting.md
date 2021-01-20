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
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="ec584-104">全像遠端處理疑難排解</span><span class="sxs-lookup"><span data-stu-id="ec584-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec584-105">本指南專為 HoloLens 2 上的全像攝影遠端所特有。</span><span class="sxs-lookup"><span data-stu-id="ec584-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="ec584-106">找不到 Spectre 降低的程式庫。</span><span class="sxs-lookup"><span data-stu-id="ec584-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="ec584-107">內建的遠端範例應用程式在發行設定中啟用了 Spectre 的風險降低 (/Qspectre) 。</span><span class="sxs-lookup"><span data-stu-id="ec584-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="ec584-108">如果您的 *vccorlib.h 無法開啟* 嚴重錯誤，請確定您的 Visual Studio 工作負載包含 Spectre 緩和連結 [庫](/cpp/build/reference/qspectre)</span><span class="sxs-lookup"><span data-stu-id="ec584-108">If you get the *vccorlib.lib cannot be opened* fatal error, make sure that your Visual Studio Workload includes the [Spectre mitigated libraries](/cpp/build/reference/qspectre)</span></span>

## <a name="speech"></a><span data-ttu-id="ec584-109">語音</span><span class="sxs-lookup"><span data-stu-id="ec584-109">Speech</span></span>

<span data-ttu-id="ec584-110">全像是「全像」遠端播放機支援診斷重迭，您可以藉由說出 ```Enable Diagnostics``` 並停用它來啟用 ```Disable Diagnostics``` 。</span><span class="sxs-lookup"><span data-stu-id="ec584-110">The Holographic Remoting Player supports a diagnostics overlay, which can be enabled by saying ```Enable Diagnostics``` and disabled by saying ```Disable Diagnostics```.</span></span> <span data-ttu-id="ec584-111">如果您無法使用這些語音命令，您也可以使用做為 URL 的網頁瀏覽器來啟動全 ```ms-holographic-remoting:?stats``` 像遠端播放機。</span><span class="sxs-lookup"><span data-stu-id="ec584-111">If you have trouble with these voice commands, you can also launch the Holographic Remoting player via a web browser using ```ms-holographic-remoting:?stats``` as a URL.</span></span>

## <a name="h265-video-codec-not-available"></a><span data-ttu-id="ec584-112">H265 視頻編碼器無法使用</span><span class="sxs-lookup"><span data-stu-id="ec584-112">H265 video codec not available</span></span>

<span data-ttu-id="ec584-113">在遠端應用程式中使用 H265 video 編解碼器時，請安裝 [HEVC 影片擴充](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 功能。</span><span class="sxs-lookup"><span data-stu-id="ec584-113">Install the [HEVC Video Extensions](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) when using H265 video codec in your remote app.</span></span> <span data-ttu-id="ec584-114">如果您遇到已安裝但無法使用編解碼器的問題，請參閱 [疑難排解](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 指南。</span><span class="sxs-lookup"><span data-stu-id="ec584-114">If you run into issues where the codec is installed but can't be used, check out [troubleshooting](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) guide.</span></span>

## <a name="limitations"></a><span data-ttu-id="ec584-115">限制</span><span class="sxs-lookup"><span data-stu-id="ec584-115">Limitations</span></span>

<span data-ttu-id="ec584-116">下列 Api 目前 **不** 支援使用全像 HoloLens 2 的全像的遠端處理，除非另有說明，否則會引發 ```ERROR_NOT_SUPPORTED``` 錯誤：</span><span class="sxs-lookup"><span data-stu-id="ec584-116">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raise an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="ec584-117">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="ec584-117">Windows.Graphics.Holographic</span></span>](/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="ec584-118">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="ec584-118">HolographicCamera.ViewConfiguration</span></span>](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="ec584-119">從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援</span><span class="sxs-lookup"><span data-stu-id="ec584-119">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="ec584-120">在先前的版本中，一律會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="ec584-120">On previous versions always raise an error.</span></span>
* [<span data-ttu-id="ec584-121">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="ec584-121">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="ec584-122">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="ec584-122">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="ec584-123">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="ec584-123">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="ec584-124">先前的版本不會失敗，但轉譯目標大小也不會變更。</span><span class="sxs-lookup"><span data-stu-id="ec584-124">On previous versions don't fail, but the render target size won't be changed.</span></span>
* [<span data-ttu-id="ec584-125">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="ec584-125">HolographicCameraPose.OverrideProjectionTransform</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="ec584-126">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="ec584-126">HolographicCameraPose.OverrideViewport</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="ec584-127">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="ec584-127">HolographicCameraPose.OverrideViewTransform</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - <span data-ttu-id="ec584-128">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="ec584-128">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="ec584-129">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="ec584-129">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="ec584-130">能源部。</span><span class="sxs-lookup"><span data-stu-id="ec584-130">Doe.</span></span>
  - <span data-ttu-id="ec584-131">從版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="ec584-131">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="ec584-132">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="ec584-132">HolographicDisplay.TryGetViewConfiguration</span></span>](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="ec584-133">查詢 HolographicViewConfigurationKind 時，PhotoVideoCamera 一律會傳回 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="ec584-133">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="ec584-134">從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援</span><span class="sxs-lookup"><span data-stu-id="ec584-134">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="ec584-135">在先前的版本中，一律會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="ec584-135">On previous versions always raise an error.</span></span>
* [<span data-ttu-id="ec584-136">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="ec584-136">HolographicSpace.CreateFramePresentationMonitor</span></span>](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="ec584-137">HolographicDisplay.GetDefault</span><span class="sxs-lookup"><span data-stu-id="ec584-137">HolographicDisplay.GetDefault</span></span>](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="ec584-138">如果在建立連接之前呼叫，將會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="ec584-138">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="ec584-139">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="ec584-139">Windows.Perception.Spatial</span></span>](/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="ec584-140">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="ec584-140">SpatialLocation.AbsoluteAngularAcceleration</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="ec584-141">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="ec584-141">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="ec584-142">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="ec584-142">SpatialLocation.AbsoluteAngularVelocity</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="ec584-143">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="ec584-143">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="ec584-144">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="ec584-144">SpatialLocation.AbsoluteLinearAcceleration</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="ec584-145">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="ec584-145">SpatialLocation.AbsoluteLinearVelocity</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="ec584-146">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="ec584-146">SpatialStageFrameOfReference.Current</span></span>](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="ec584-147">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="ec584-147">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="ec584-148">在先前的版本中，一律會傳回 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="ec584-148">On previous versions always return ```nullptr```.</span></span>
* [<span data-ttu-id="ec584-149">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="ec584-149">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - <span data-ttu-id="ec584-150">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="ec584-150">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="ec584-151">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="ec584-151">SpatialAnchor.RemovedByUser</span></span>](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="ec584-152">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="ec584-152">SpatialAnchorExporter.GetDefault</span></span>](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="ec584-153">從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。</span><span class="sxs-lookup"><span data-stu-id="ec584-153">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="ec584-154">在先前的版本中，一律會傳回 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="ec584-154">On previous versions always return ```nullptr```.</span></span> 
* [<span data-ttu-id="ec584-155">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="ec584-155">SpatialAnchorExporter.RequestAccessAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="ec584-156">從版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。</span><span class="sxs-lookup"><span data-stu-id="ec584-156">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="ec584-157">在舊版中，非同步作業一律會使用完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="ec584-157">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="ec584-158">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="ec584-158">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="ec584-159">非同步作業一律會使用完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="ec584-159">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="ec584-160">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="ec584-160">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="ec584-161">非同步作業一律會使用完成 ```false``` 。</span><span class="sxs-lookup"><span data-stu-id="ec584-161">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="ec584-162">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="ec584-162">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="ec584-163">非同步作業一律會使用完成 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="ec584-163">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="ec584-164">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="ec584-164">Windows.UI.Input.Spatial</span></span>](/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="ec584-165">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="ec584-165">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="ec584-166">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="ec584-166">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="ec584-167">SpatialInteractionSource 控制器</span><span class="sxs-lookup"><span data-stu-id="ec584-167">SpatialInteractionSource.Controller</span></span>](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - <span data-ttu-id="ec584-168">從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="ec584-168">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>

[<span data-ttu-id="ec584-169">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="ec584-169">Windows.Perception.Spatial.Preview</span></span>](/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="ec584-170">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="ec584-170">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="ec584-171">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="ec584-171">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="ec584-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec584-172">See Also</span></span>
* [<span data-ttu-id="ec584-173">全像遠端版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="ec584-173">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="ec584-174">使用 Windows Mixed Reality Api 撰寫全像遠端執行遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="ec584-174">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="ec584-175">使用 OpenXR Api 撰寫全像遠端執行遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="ec584-175">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="ec584-176">撰寫自訂全像攝影遠端播放應用程式</span><span class="sxs-lookup"><span data-stu-id="ec584-176">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="ec584-177">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="ec584-177">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="ec584-178">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="ec584-178">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)