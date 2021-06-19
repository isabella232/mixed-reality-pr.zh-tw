---
title: Unity 中的 OpenXR 外掛程式支援功能
description: 探索 OpenXR 針對 Unity 中的混合現實開發所支援的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: 371815d6410a7add8ee9c62f72d746d74ad397b0
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392666"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="98441-104">混合現實 OpenXR Unity 中支援的功能</span><span class="sxs-lookup"><span data-stu-id="98441-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="98441-105">**Mixed Reality OpenXR 外掛程式** 套件是 Unity **OpenXR 外掛程式** 的延伸模組，並支援 HoloLens 2 和 Windows Mixed Reality 耳機的功能套件。</span><span class="sxs-lookup"><span data-stu-id="98441-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="98441-106">繼續之前，請確定您的 Unity 專案已 [設定為 OpenXR](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="98441-106">Before continuing, make sure your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="98441-107">支援的項目</span><span class="sxs-lookup"><span data-stu-id="98441-107">What's supported</span></span>

<span data-ttu-id="98441-108">目前支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="98441-108">The following features are currently supported:</span></span>

* <span data-ttu-id="98441-109">支援 HoloLens 2 的 UWP 應用程式，並針對 HoloLens 2 應用程式模型進行優化。</span><span class="sxs-lookup"><span data-stu-id="98441-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="98441-110">支援適用于 Windows Mixed Reality 耳機的 Win32 VR 應用程式，具有最新的控制器設定檔和全像應用程式遠端。</span><span class="sxs-lookup"><span data-stu-id="98441-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="98441-111">使用錨點和未系結空間的世界規模追蹤。</span><span class="sxs-lookup"><span data-stu-id="98441-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="98441-112">[錨點儲存體 API，以將錨點保存](spatial-anchors-in-unity.md) 到 HoloLens 2 的本機儲存體。</span><span class="sxs-lookup"><span data-stu-id="98441-112">[Anchor storage API to persist anchors](spatial-anchors-in-unity.md) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="98441-113">[移動控制器和手互動](#motion-controller-and-hand-interactions)，包括新的 HP 回音卡控制器。</span><span class="sxs-lookup"><span data-stu-id="98441-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="98441-114">使用26個接點和聯合半徑輸入，以明確表述的手勢進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="98441-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="98441-115">HoloLens 2 上的眼睛注視互動。</span><span class="sxs-lookup"><span data-stu-id="98441-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="98441-116">HoloLens 2 上尋找 (PV) 攝影機的相片/影片。</span><span class="sxs-lookup"><span data-stu-id="98441-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="98441-117">混合實境擷取使用透過 PV 攝影機的第三種眼睛呈現。</span><span class="sxs-lookup"><span data-stu-id="98441-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="98441-118">支援「播放」以使用全像「 [遠端處理」應用程式 HoloLens 2](unity-play-mode.md#unity-play-mode-with-holographic-remoting)，讓開發人員不需要建立及部署到裝置，即可將腳本進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="98441-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](unity-play-mode.md#unity-play-mode-with-holographic-remoting), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="98441-119">透過 [MRTK OpenXR 提供者支援](openxr-getting-started.md#using-mrtk-with-openxr-support)，與 MRTK Unity 2.5.3 和更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="98441-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="98441-120">與 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="98441-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="98441-121"> (在 0.1.3) 中新增的功能，可支援從組建和部署的 Windows 獨立應用程式進行傳統型 [應用程式](holographic-remoting-desktop.md) 全像開發。</span><span class="sxs-lookup"><span data-stu-id="98441-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](holographic-remoting-desktop.md) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="98441-122"> (在0.1.4 中新增) 透過 SpatialGraphNode 支援 HoloLens2 上的[QR 代碼追蹤](#qr-codes)</span><span class="sxs-lookup"><span data-stu-id="98441-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>
* <span data-ttu-id="98441-123"> (在0.2.0 中新增) 在全像遠端處理中支援 **錨點**</span><span class="sxs-lookup"><span data-stu-id="98441-123">(Added in 0.2.0) Supports **Anchor** in Holographic Remoting</span></span>
* <span data-ttu-id="98441-124"> (在0.2.0 中新增) 支援 **手接頭和手形網格追蹤**</span><span class="sxs-lookup"><span data-stu-id="98441-124">(Added in 0.2.0) Supports both **hand joints and hand mesh tracking**</span></span>
* <span data-ttu-id="98441-125"> (在0.2.0 中新增) 支援使用 **ARPlaneSubsystems** 進行平面偵測，並使用 **ARRaycastManager** 來放置全像影像。</span><span class="sxs-lookup"><span data-stu-id="98441-125">(Added in 0.2.0) Supports **ARPlaneSubsystems** for plane detection and place hologram using **ARRaycastManager**.</span></span>
* <span data-ttu-id="98441-126"> (0.9.0) 支援空間對應的 **XRMeshSubsystem** 和 **ARMeshManager** 。</span><span class="sxs-lookup"><span data-stu-id="98441-126">(0.9.0) Supports **XRMeshSubsystem** and **ARMeshManager** for spatial mapping.</span></span>
* <span data-ttu-id="98441-127"> (在0.9.0 中新增) 支援適用于 Windows 外掛程式的 Azure 空間錨點 SDK。</span><span class="sxs-lookup"><span data-stu-id="98441-127">(Added in 0.9.0) Supports the Azure Spatial Anchors SDK for Windows plugin.</span></span> <span data-ttu-id="98441-128">如需詳細資訊，請參閱 [GitHub 上的 Mixed Reality + OpenXR Azure 空間錨點範例專案](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)。</span><span class="sxs-lookup"><span data-stu-id="98441-128">For more information, see the [Mixed Reality + OpenXR Azure Spatial Anchors sample project on GitHub](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample).</span></span>
* <span data-ttu-id="98441-129"> (在 0.9.1) 中新增的功能，可支援從建立和部署的 Windows UWP 應用程式進行傳統型應用程式全像的遠端</span><span class="sxs-lookup"><span data-stu-id="98441-129">(Added in 0.9.1) Supports desktop app Holographic Remoting from a built and deployed Windows UWP app.</span></span>
* <span data-ttu-id="98441-130">除了 ARM64 for HoloLens 2 應用程式之外， (在0.9.4 中新增的) 支援 ARM 平臺。</span><span class="sxs-lookup"><span data-stu-id="98441-130">(Added in 0.9.4) Supports ARM platform in addition to ARM64 for HoloLens 2 application.</span></span>

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="98441-131">移動控制器和手互動</span><span class="sxs-lookup"><span data-stu-id="98441-131">Motion controller and hand interactions</span></span>

<span data-ttu-id="98441-132">若要瞭解 Unity 中混合現實互動的基本概念，請流覽 unity [Manual For UNITY XR 輸入](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="98441-132">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="98441-133">這項 Unity 檔涵蓋從控制器專屬輸入到更一般化 **InputFeatureUsage** 的對應、如何識別和分類可用的 XR 輸入、如何從這些輸入讀取資料等等。</span><span class="sxs-lookup"><span data-stu-id="98441-133">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="98441-134">Mixed Reality OpenXR 外掛程式提供額外的輸入互動設定檔，對應至標準 **InputFeatureUsage** s，如下所述：</span><span class="sxs-lookup"><span data-stu-id="98441-134">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="98441-135">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="98441-135">InputFeatureUsage</span></span> | <span data-ttu-id="98441-136">HP 回音 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="98441-136">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="98441-137">HoloLens (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="98441-137">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="98441-138">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="98441-138">primary2DAxis</span></span> | <span data-ttu-id="98441-139">操縱 杆</span><span class="sxs-lookup"><span data-stu-id="98441-139">Joystick</span></span> | |
| <span data-ttu-id="98441-140">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="98441-140">primary2DAxisClick</span></span> | <span data-ttu-id="98441-141">搖桿-按一下</span><span class="sxs-lookup"><span data-stu-id="98441-141">Joystick - Click</span></span> | |
| <span data-ttu-id="98441-142">觸發程序 (trigger)</span><span class="sxs-lookup"><span data-stu-id="98441-142">trigger</span></span> | <span data-ttu-id="98441-143">觸發程序</span><span class="sxs-lookup"><span data-stu-id="98441-143">Trigger</span></span>  | |
| <span data-ttu-id="98441-144">握</span><span class="sxs-lookup"><span data-stu-id="98441-144">grip</span></span> | <span data-ttu-id="98441-145">握</span><span class="sxs-lookup"><span data-stu-id="98441-145">Grip</span></span> | <span data-ttu-id="98441-146">點擊或擠壓</span><span class="sxs-lookup"><span data-stu-id="98441-146">Air tap or squeeze</span></span> |
| <span data-ttu-id="98441-147">primaryButton</span><span class="sxs-lookup"><span data-stu-id="98441-147">primaryButton</span></span> | <span data-ttu-id="98441-148">[X/A]-按下</span><span class="sxs-lookup"><span data-stu-id="98441-148">[X/A] - Press</span></span> | <span data-ttu-id="98441-149">空中點選</span><span class="sxs-lookup"><span data-stu-id="98441-149">Air tap</span></span> |
| <span data-ttu-id="98441-150">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="98441-150">secondaryButton</span></span> | <span data-ttu-id="98441-151">[Y/B]-按下</span><span class="sxs-lookup"><span data-stu-id="98441-151">[Y/B] - Press</span></span> | |
| <span data-ttu-id="98441-152">gripButton</span><span class="sxs-lookup"><span data-stu-id="98441-152">gripButton</span></span> | <span data-ttu-id="98441-153">握住-按</span><span class="sxs-lookup"><span data-stu-id="98441-153">Grip - Press</span></span> | |
| <span data-ttu-id="98441-154">triggerButton</span><span class="sxs-lookup"><span data-stu-id="98441-154">triggerButton</span></span> | <span data-ttu-id="98441-155">觸發程式-按下</span><span class="sxs-lookup"><span data-stu-id="98441-155">Trigger - Press</span></span> | |
| <span data-ttu-id="98441-156">menuButton</span><span class="sxs-lookup"><span data-stu-id="98441-156">menuButton</span></span> | <span data-ttu-id="98441-157">功能表</span><span class="sxs-lookup"><span data-stu-id="98441-157">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="98441-158">目標和底姿勢</span><span class="sxs-lookup"><span data-stu-id="98441-158">Aim and Grip Poses</span></span>

<span data-ttu-id="98441-159">您可以透過 OpenXR 輸入互動存取兩組姿勢：</span><span class="sxs-lookup"><span data-stu-id="98441-159">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="98441-160">抓手中呈現物件的底框</span><span class="sxs-lookup"><span data-stu-id="98441-160">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="98441-161">目標是指向世界。</span><span class="sxs-lookup"><span data-stu-id="98441-161">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="98441-162">有關此設計的詳細資訊，以及這兩個姿勢之間的差異，請參閱 [OpenXR 規格-輸入子路徑](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。</span><span class="sxs-lookup"><span data-stu-id="98441-162">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="98441-163">InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供 **的姿勢全都代表 OpenXR 的** 把手姿勢。</span><span class="sxs-lookup"><span data-stu-id="98441-163">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="98441-164">與框姿勢相關的 InputFeatureUsages 是在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定義。</span><span class="sxs-lookup"><span data-stu-id="98441-164">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="98441-165">InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿勢全都代表 OpenXR 的 **目標** 。</span><span class="sxs-lookup"><span data-stu-id="98441-165">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="98441-166">這些 InputFeatureUsages 不會定義在任何包含的 c # 檔案中，因此您必須定義您自己的 InputFeatureUsages，如下所示：</span><span class="sxs-lookup"><span data-stu-id="98441-166">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="98441-167">Haptics</span><span class="sxs-lookup"><span data-stu-id="98441-167">Haptics</span></span>

<span data-ttu-id="98441-168">如需在 Unity 的 XR 輸入系統中使用 haptics 的相關資訊，請參閱 unity [Manual For UNITY XR 輸入-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的檔。</span><span class="sxs-lookup"><span data-stu-id="98441-168">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="98441-169">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="98441-169">QR codes</span></span>

<span data-ttu-id="98441-170">HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。</span><span class="sxs-lookup"><span data-stu-id="98441-170">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="98441-171">您可以在我們的 [QR 代碼追蹤](../platform-capabilities-and-apis/qr-code-tracking.md) 檔中找到更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="98441-171">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="98441-172">使用 OpenXR 外掛程式時，請[ `SpatialGraphNodeId` 從 QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)抓取，並使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 來尋找 qr 代碼。</span><span class="sxs-lookup"><span data-stu-id="98441-172">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="98441-173">如需參考，我們[在 GitHub 上有 QR 追蹤範例專案](https://github.com/yl-msft/QRTracking)，並有更詳細的[ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)使用說明。</span><span class="sxs-lookup"><span data-stu-id="98441-173">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="98441-174">疑難排解</span><span class="sxs-lookup"><span data-stu-id="98441-174">Troubleshooting</span></span>

<span data-ttu-id="98441-175">當您在 HoloLens 2 上暫停和繼續 Unity 應用程式時，應用程式無法正確地繼續，這會導致 HoloLens 視圖中有4個旋轉點。</span><span class="sxs-lookup"><span data-stu-id="98441-175">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="98441-176">將 OpenXR 專案設定中的 **深度提交模式** 設定為 [ **無** ] 作為因應措施</span><span class="sxs-lookup"><span data-stu-id="98441-176">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
