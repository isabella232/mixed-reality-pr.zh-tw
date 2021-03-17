---
title: Unity 中的 OpenXR 外掛程式支援功能
description: 探索 OpenXR 針對 Unity 中的混合現實開發所支援的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: 1c9e185c63d3efef66cdc2782d8d8d4e3692c705
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623628"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="ced11-104">混合現實 OpenXR Unity 中支援的功能</span><span class="sxs-lookup"><span data-stu-id="ced11-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="ced11-105">**Mixed Reality OpenXR 外掛程式** 套件是 Unity **OpenXR 外掛程式** 的延伸模組，並支援 HoloLens 2 和 Windows Mixed Reality 耳機的功能套件。</span><span class="sxs-lookup"><span data-stu-id="ced11-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="ced11-106">繼續之前，請確定您已安裝 **unity 2020.2** 或更新版本、 **OpenXR 外掛程式版本 0.1.3** 或更新版本，且您的 Unity 專案已 [設定 OpenXR](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="ced11-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="ced11-107">支援的項目</span><span class="sxs-lookup"><span data-stu-id="ced11-107">What's supported</span></span>

<span data-ttu-id="ced11-108">目前支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="ced11-108">The following features are currently supported:</span></span>

* <span data-ttu-id="ced11-109">支援 HoloLens 2 的 UWP 應用程式，並針對 HoloLens 2 應用程式模型進行優化。</span><span class="sxs-lookup"><span data-stu-id="ced11-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="ced11-110">支援 Win32 VR 應用程式，適用于具有最新控制器設定檔的 Windows Mixed Reality 耳機以及全像應用程式遠端處理。</span><span class="sxs-lookup"><span data-stu-id="ced11-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="ced11-111">使用錨點和未系結空間的世界規模追蹤。</span><span class="sxs-lookup"><span data-stu-id="ced11-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="ced11-112">[錨點儲存體 API，以將錨點保存](spatial-anchors-in-unity.md) 到 HoloLens 2 本機儲存體。</span><span class="sxs-lookup"><span data-stu-id="ced11-112">[Anchor storage API to persist anchors](spatial-anchors-in-unity.md) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="ced11-113">[移動控制器和手互動](#motion-controller-and-hand-interactions)，包括新的 HP 回音卡控制器。</span><span class="sxs-lookup"><span data-stu-id="ced11-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="ced11-114">使用26個接點和聯合半徑輸入，以明確表述的手勢進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="ced11-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="ced11-115">HoloLens 2 上的眼睛互動。</span><span class="sxs-lookup"><span data-stu-id="ced11-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="ced11-116">在 HoloLens 2 上尋找相片/影片 (PV) 攝影機。</span><span class="sxs-lookup"><span data-stu-id="ced11-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="ced11-117">混合現實捕捉使用透過 PV 攝影機的第三種視覺呈現。</span><span class="sxs-lookup"><span data-stu-id="ced11-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="ced11-118">支援「 [Play」至 HoloLens 2 （含全像遠端應用程式](#holographic-remoting-in-unity-editor-play-mode)），讓開發人員不需要建立及部署到裝置，即可將腳本進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ced11-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="ced11-119">透過 [MRTK OpenXR 提供者支援](openxr-getting-started.md#using-mrtk-with-openxr-support)，與 MRTK Unity 2.5.3 和更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="ced11-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="ced11-120">與 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="ced11-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="ced11-121"> (在 0.1.3) 中新增的功能，可支援從組建和部署的 Windows 獨立應用程式進行傳統型 [應用程式](holographic-remoting-desktop.md) 全像開發。</span><span class="sxs-lookup"><span data-stu-id="ced11-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](holographic-remoting-desktop.md) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="ced11-122"> (在0.1.4 中新增) 透過 SpatialGraphNode 支援 HoloLens2 上的[QR 代碼追蹤](#qr-codes)</span><span class="sxs-lookup"><span data-stu-id="ced11-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="ced11-123">全像遠端設定</span><span class="sxs-lookup"><span data-stu-id="ced11-123">Holographic Remoting setup</span></span>

1. <span data-ttu-id="ced11-124">首先，您必須從 HoloLens 2 上的 Microsoft Store 安裝全像[遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40)</span><span class="sxs-lookup"><span data-stu-id="ced11-124">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="ced11-125">在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址</span><span class="sxs-lookup"><span data-stu-id="ced11-125">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="ced11-126">您將需要2.4 或更新版本才能使用 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="ced11-126">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens 中執行的全像 Remoting 播放程式的螢幕擷取畫面](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="ced11-128">Unity 編輯器 play 模式的全像遠端功能</span><span class="sxs-lookup"><span data-stu-id="ced11-128">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="ced11-129">在 Visual Studio 專案中建立 UWP Unity 專案，然後將它封裝並部署到 HoloLens 2 裝置，可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="ced11-129">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="ced11-130">其中一個解決方法是啟用全像「全像」編輯器遠端功能，讓您可以使用「播放」模式，將 c # 腳本直接透過您的網路上的 HoloLens 2 裝置來進行。</span><span class="sxs-lookup"><span data-stu-id="ced11-130">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="ced11-131">此案例可避免建立 UWP 套件並將其部署至遠端裝置的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ced11-131">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="ced11-132">遵循全像全像[遠端設定](#holographic-remoting-setup)的步驟</span><span class="sxs-lookup"><span data-stu-id="ced11-132">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="ced11-133">開啟 [ **編輯-> 專案設定**]，流覽至 **XR 外掛程式管理**，然後選取 [ **Windows Mixed Reality 功能集** ] 方塊：</span><span class="sxs-lookup"><span data-stu-id="ced11-133">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟之 [專案設定] 面板的螢幕擷取畫面](images/openxr-features-img-02.png)

3. <span data-ttu-id="ced11-135">展開 [ **OpenXR** ] 底下的 [**功能**] 區段，然後選取 [**全部顯示**]</span><span class="sxs-lookup"><span data-stu-id="ced11-135">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="ced11-136">核取 [全像攝影 **編輯器遠端處理** ] 核取方塊，然後輸入您從「全像」遠端應用程式取得的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="ced11-136">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![在 Unity 編輯器中開啟專案設定面板的螢幕擷取畫面，其中已醒目提示功能](images/openxr-features-img-03.png)

<span data-ttu-id="ced11-138">現在您可以按一下 [播放] 按鈕，以在 HoloLens 上的全像遠端應用程式中播放 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ced11-138">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="ced11-139">您也可以 [將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以在播放模式中進行 c # 腳本的調試。</span><span class="sxs-lookup"><span data-stu-id="ced11-139">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="ced11-140">從0.1.0 版起，全像「全像」遠端執行時間不支援錨點，而 ARAnchorManager 功能將無法透過遠端處理。</span><span class="sxs-lookup"><span data-stu-id="ced11-140">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="ced11-141">這項功能會在未來的版本中推出。</span><span class="sxs-lookup"><span data-stu-id="ced11-141">This feature is coming in future releases.</span></span>

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="ced11-142">移動控制器和手互動</span><span class="sxs-lookup"><span data-stu-id="ced11-142">Motion controller and hand interactions</span></span>

<span data-ttu-id="ced11-143">若要瞭解 Unity 中混合現實互動的基本概念，請流覽 unity [Manual For UNITY XR 輸入](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="ced11-143">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="ced11-144">這項 Unity 檔涵蓋從控制器專屬輸入到更一般化 **InputFeatureUsage** 的對應、如何識別和分類可用的 XR 輸入、如何從這些輸入讀取資料等等。</span><span class="sxs-lookup"><span data-stu-id="ced11-144">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="ced11-145">Mixed Reality OpenXR 外掛程式提供額外的輸入互動設定檔，對應至標準 **InputFeatureUsage** s，如下所述：</span><span class="sxs-lookup"><span data-stu-id="ced11-145">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="ced11-146">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="ced11-146">InputFeatureUsage</span></span> | <span data-ttu-id="ced11-147">HP 回音 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="ced11-147">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="ced11-148">HoloLens (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="ced11-148">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="ced11-149">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="ced11-149">primary2DAxis</span></span> | <span data-ttu-id="ced11-150">操縱 杆</span><span class="sxs-lookup"><span data-stu-id="ced11-150">Joystick</span></span> | |
| <span data-ttu-id="ced11-151">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="ced11-151">primary2DAxisClick</span></span> | <span data-ttu-id="ced11-152">搖桿-按一下</span><span class="sxs-lookup"><span data-stu-id="ced11-152">Joystick - Click</span></span> | |
| <span data-ttu-id="ced11-153">觸發程序 (trigger)</span><span class="sxs-lookup"><span data-stu-id="ced11-153">trigger</span></span> | <span data-ttu-id="ced11-154">觸發程序</span><span class="sxs-lookup"><span data-stu-id="ced11-154">Trigger</span></span>  | |
| <span data-ttu-id="ced11-155">握</span><span class="sxs-lookup"><span data-stu-id="ced11-155">grip</span></span> | <span data-ttu-id="ced11-156">握</span><span class="sxs-lookup"><span data-stu-id="ced11-156">Grip</span></span> | <span data-ttu-id="ced11-157">點擊或擠壓</span><span class="sxs-lookup"><span data-stu-id="ced11-157">Air tap or squeeze</span></span> |
| <span data-ttu-id="ced11-158">primaryButton</span><span class="sxs-lookup"><span data-stu-id="ced11-158">primaryButton</span></span> | <span data-ttu-id="ced11-159">[X/A]-按下</span><span class="sxs-lookup"><span data-stu-id="ced11-159">[X/A] - Press</span></span> | <span data-ttu-id="ced11-160">空中點選</span><span class="sxs-lookup"><span data-stu-id="ced11-160">Air tap</span></span> |
| <span data-ttu-id="ced11-161">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="ced11-161">secondaryButton</span></span> | <span data-ttu-id="ced11-162">[Y/B]-按下</span><span class="sxs-lookup"><span data-stu-id="ced11-162">[Y/B] - Press</span></span> | |
| <span data-ttu-id="ced11-163">gripButton</span><span class="sxs-lookup"><span data-stu-id="ced11-163">gripButton</span></span> | <span data-ttu-id="ced11-164">握住-按</span><span class="sxs-lookup"><span data-stu-id="ced11-164">Grip - Press</span></span> | |
| <span data-ttu-id="ced11-165">triggerButton</span><span class="sxs-lookup"><span data-stu-id="ced11-165">triggerButton</span></span> | <span data-ttu-id="ced11-166">觸發程式-按下</span><span class="sxs-lookup"><span data-stu-id="ced11-166">Trigger - Press</span></span> | |
| <span data-ttu-id="ced11-167">menuButton</span><span class="sxs-lookup"><span data-stu-id="ced11-167">menuButton</span></span> | <span data-ttu-id="ced11-168">功能表</span><span class="sxs-lookup"><span data-stu-id="ced11-168">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="ced11-169">目標和底姿勢</span><span class="sxs-lookup"><span data-stu-id="ced11-169">Aim and Grip Poses</span></span>

<span data-ttu-id="ced11-170">您可以透過 OpenXR 輸入互動存取兩組姿勢：</span><span class="sxs-lookup"><span data-stu-id="ced11-170">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="ced11-171">抓手中呈現物件的底框</span><span class="sxs-lookup"><span data-stu-id="ced11-171">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="ced11-172">目標是指向世界。</span><span class="sxs-lookup"><span data-stu-id="ced11-172">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="ced11-173">有關此設計的詳細資訊，以及這兩個姿勢之間的差異，請參閱 [OpenXR 規格-輸入子路徑](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。</span><span class="sxs-lookup"><span data-stu-id="ced11-173">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="ced11-174">InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供 **的姿勢全都代表 OpenXR 的** 把手姿勢。</span><span class="sxs-lookup"><span data-stu-id="ced11-174">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="ced11-175">與框姿勢相關的 InputFeatureUsages 是在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定義。</span><span class="sxs-lookup"><span data-stu-id="ced11-175">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="ced11-176">InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿勢全都代表 OpenXR 的 **目標** 。</span><span class="sxs-lookup"><span data-stu-id="ced11-176">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="ced11-177">這些 InputFeatureUsages 不會定義在任何包含的 c # 檔案中，因此您必須定義您自己的 InputFeatureUsages，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ced11-177">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="ced11-178">Haptics</span><span class="sxs-lookup"><span data-stu-id="ced11-178">Haptics</span></span>

<span data-ttu-id="ced11-179">如需在 Unity 的 XR 輸入系統中使用 haptics 的相關資訊，請參閱 unity [Manual For UNITY XR 輸入-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的檔。</span><span class="sxs-lookup"><span data-stu-id="ced11-179">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="ced11-180">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="ced11-180">QR codes</span></span>

<span data-ttu-id="ced11-181">HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。</span><span class="sxs-lookup"><span data-stu-id="ced11-181">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="ced11-182">您可以在我們的 [QR 代碼追蹤](../platform-capabilities-and-apis/qr-code-tracking.md) 檔中找到更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ced11-182">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="ced11-183">使用 OpenXR 外掛程式時，請[ `SpatialGraphNodeId` 從 QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)抓取，並使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 來尋找 qr 代碼。</span><span class="sxs-lookup"><span data-stu-id="ced11-183">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="ced11-184">如需參考，我們[在 GitHub 上有 QR 追蹤範例專案](https://github.com/yl-msft/QRTracking)，並有更詳細的[ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)使用說明。</span><span class="sxs-lookup"><span data-stu-id="ced11-184">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="ced11-185">即將推出的內容</span><span class="sxs-lookup"><span data-stu-id="ced11-185">What's coming soon</span></span>

<span data-ttu-id="ced11-186">下列問題和遺漏的功能都是已知的混合現實 OpenXR 外掛程式 **版本 0.1.0**。</span><span class="sxs-lookup"><span data-stu-id="ced11-186">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="ced11-187">我們正在處理這些問題，並將在即將推出的版本中發行修正程式和新功能。</span><span class="sxs-lookup"><span data-stu-id="ced11-187">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="ced11-188">尚不支援 **ARPlaneSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="ced11-188">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="ced11-189">HoloLens 2 也不支援 **ARPlaneManager**、 **ARRaycastManager** 和相關的 API，例如 **ARAnchorManager. AttachAnchor** 。</span><span class="sxs-lookup"><span data-stu-id="ced11-189">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="ced11-190">目前的「全像」遠端功能不支援 **錨定持續** 性，但不久的未來將會推出。</span><span class="sxs-lookup"><span data-stu-id="ced11-190">**Anchor persistence** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="ced11-191">目前尚不支援 **手形** 追蹤和 **XRMeshSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="ced11-191">**Hand Mesh** tracking and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="ced11-192">**Azure 空間錨點** 支援即將在未來版本中推出。</span><span class="sxs-lookup"><span data-stu-id="ced11-192">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="ced11-193">**ARM64** 是 HoloLens 2 應用程式唯一支援的平臺。</span><span class="sxs-lookup"><span data-stu-id="ced11-193">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="ced11-194">**ARM** 平臺即將在未來版本中推出。</span><span class="sxs-lookup"><span data-stu-id="ced11-194">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="ced11-195">疑難排解</span><span class="sxs-lookup"><span data-stu-id="ced11-195">Troubleshooting</span></span>

<span data-ttu-id="ced11-196">當您在 HoloLens 2 上暫停和繼續 Unity 應用程式時，應用程式無法正確地繼續，這會導致 HoloLens 視圖中有4個旋轉點。</span><span class="sxs-lookup"><span data-stu-id="ced11-196">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="ced11-197">將 OpenXR 專案設定中的 **深度提交模式** 設定為 [ **無** ] 作為因應措施</span><span class="sxs-lookup"><span data-stu-id="ced11-197">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
