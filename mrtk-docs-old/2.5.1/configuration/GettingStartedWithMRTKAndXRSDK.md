---
title: GettingStartedWithMRTKAndXRSDK
description: 具有 XRSDK 的 MRTK 登陸頁面
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、XRSDK、
ms.openlocfilehash: ac0529242a1f9d22876a847501dd32273b8c78b7
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779966"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="413d2-104">開始使用 MRTK 和 XR SDK</span><span class="sxs-lookup"><span data-stu-id="413d2-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="413d2-105">XR SDK 是 unity [2019.3 和以上的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。</span><span class="sxs-lookup"><span data-stu-id="413d2-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="413d2-106">在 Unity 2019 中，它會提供現有 XR 管線的替代方案。</span><span class="sxs-lookup"><span data-stu-id="413d2-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="413d2-107">在 Unity 2020 中，它將成為 Unity 中唯一的 XR 管線。</span><span class="sxs-lookup"><span data-stu-id="413d2-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="413d2-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="413d2-108">Prerequisites</span></span>

<span data-ttu-id="413d2-109">若要開始使用 Mixed Reality 工具組，請遵循 [提供的步驟](../WelcomeToMRTK.md) 將 MRTK 新增至專案。</span><span class="sxs-lookup"><span data-stu-id="413d2-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../WelcomeToMRTK.md) to add MRTK to a project.</span></span>

## <a name="add-xr-sdk-to-a-unity-project"></a><span data-ttu-id="413d2-110">將 XR SDK 新增至 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="413d2-110">Add XR SDK to a Unity project</span></span>

<span data-ttu-id="413d2-111">XR SDK 支援 Windows Mixed Reality 和 Oculus。</span><span class="sxs-lookup"><span data-stu-id="413d2-111">Windows Mixed Reality and Oculus are supported on XR SDK.</span></span>

### <a name="required-in-unity"></a><span data-ttu-id="413d2-112">Unity 中的必要項</span><span class="sxs-lookup"><span data-stu-id="413d2-112">Required in Unity</span></span>

#### <a name="windows-mixed-reality"></a><span data-ttu-id="413d2-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="413d2-113">Windows Mixed Reality</span></span>

1. <span data-ttu-id="413d2-114">移至 Unity 的套件管理員並安裝 Windows XR 外掛程式套件，以新增 XR SDK 上的 Windows Mixed Reality 支援。</span><span class="sxs-lookup"><span data-stu-id="413d2-114">Go into Unity's Package Manager and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="413d2-115">這也會提取一些相依性套件。</span><span class="sxs-lookup"><span data-stu-id="413d2-115">This will pull down a few dependency packages as well.</span></span> <span data-ttu-id="413d2-116">確定已成功安裝下列各項：</span><span class="sxs-lookup"><span data-stu-id="413d2-116">Ensure the following all successfully installed:</span></span>
   1. <span data-ttu-id="413d2-117">XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="413d2-117">XR Plugin Management</span></span>
   1. <span data-ttu-id="413d2-118">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="413d2-118">Windows XR Plugin</span></span>
   1. <span data-ttu-id="413d2-119">XR 舊版輸入協助程式</span><span class="sxs-lookup"><span data-stu-id="413d2-119">XR Legacy Input Helpers</span></span>
1. <span data-ttu-id="413d2-120">移至 [編輯 > 專案設定]。</span><span class="sxs-lookup"><span data-stu-id="413d2-120">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="413d2-121">在 [專案設定] 視窗中，按一下 [XR 外掛程式管理] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="413d2-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="413d2-122">移至 [通用 Windows 平臺] 設定，並確定已核取 [外掛程式提供者] 下的 [Windows Mixed Reality]。</span><span class="sxs-lookup"><span data-stu-id="413d2-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
1. <span data-ttu-id="413d2-123">確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="413d2-123">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="413d2-124"> (**_編輯中的 HoloLens 遠端處理需要，否則_** 請) 移至獨立設定，並確定已在外掛程式提供者底下檢查 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="413d2-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="413d2-125">也請確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="413d2-125">Also ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="413d2-126"> (**_選擇性_**) 按一下 [XR 外掛程式管理] 下的 [Windows Mixed Reality] 索引標籤，然後建立自訂設定設定檔來變更預設值。</span><span class="sxs-lookup"><span data-stu-id="413d2-126">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="413d2-127">如果設定清單已經存在，則不需要建立任何設定檔。</span><span class="sxs-lookup"><span data-stu-id="413d2-127">If the list of settings are already there, no profile needs to be created.</span></span>

![外掛程式管理](../features/images/xrsdk/PluginManagement.png)

### <a name="required-in-mrtk"></a><span data-ttu-id="413d2-129">MRTK 中的必要項</span><span class="sxs-lookup"><span data-stu-id="413d2-129">Required in MRTK</span></span>

<span data-ttu-id="413d2-130">選擇 "DefaultXRSDKConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。</span><span class="sxs-lookup"><span data-stu-id="413d2-130">Choose the "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span> <span data-ttu-id="413d2-131">此設定檔會在需要時，使用 MRTK 的 XR SDK 系統和提供者來設定。</span><span class="sxs-lookup"><span data-stu-id="413d2-131">This profile is set up with MRTK's XR SDK systems and providers, where needed.</span></span>

<span data-ttu-id="413d2-132">若要將現有的設定檔遷移至 XR SDK，應更新下列服務和資料提供者：</span><span class="sxs-lookup"><span data-stu-id="413d2-132">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

#### <a name="camera"></a><span data-ttu-id="413d2-133">相機</span><span class="sxs-lookup"><span data-stu-id="413d2-133">Camera</span></span>

<span data-ttu-id="413d2-134">從 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="413d2-134">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![舊版相機設定](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="413d2-136">至 [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **和**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="413d2-136">to [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span>

![XR SDK 攝影機設定](../features/images/xrsdk/CameraSystemXRSDK.png)

#### <a name="input"></a><span data-ttu-id="413d2-138">輸入</span><span class="sxs-lookup"><span data-stu-id="413d2-138">Input</span></span>

<span data-ttu-id="413d2-139">從 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="413d2-139">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![舊版輸入設定](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="413d2-141">自 [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="413d2-141">to [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)</span></span>

![XR SDK 輸入設定](../features/images/xrsdk/InputSystemWMRXRSDK.png)

#### <a name="boundary"></a><span data-ttu-id="413d2-143">界限</span><span class="sxs-lookup"><span data-stu-id="413d2-143">Boundary</span></span>

<span data-ttu-id="413d2-144">從 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="413d2-144">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![舊版界限設定](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="413d2-146">自  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="413d2-146">to  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)</span></span>

![XR SDK 界限設定](../features/images/xrsdk/BoundarySystemXRSDK.png)

#### <a name="spatial-awareness"></a><span data-ttu-id="413d2-148">空間感知</span><span class="sxs-lookup"><span data-stu-id="413d2-148">Spatial awareness</span></span>

<span data-ttu-id="413d2-149">從 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="413d2-149">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![舊版空間感知設定](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="413d2-151">自 [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="413d2-151">to [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)</span></span>

![XR SDK 空間感知設定](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

#### <a name="controller-mappings"></a><span data-ttu-id="413d2-153">控制器對應</span><span class="sxs-lookup"><span data-stu-id="413d2-153">Controller mappings</span></span>

<span data-ttu-id="413d2-154">如果使用自訂控制器對應設定檔，請開啟其中一個設定檔，並執行混合現實工具組-> 公用程式-> 更新 > 控制器對應設定檔] 功能表項目，以確保已定義新的 XR SDK 控制器類型。</span><span class="sxs-lookup"><span data-stu-id="413d2-154">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="413d2-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="413d2-155">See also</span></span>

* [<span data-ttu-id="413d2-156">Unity 中的 AR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="413d2-156">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="413d2-157">Unity 中的 VR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="413d2-157">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
