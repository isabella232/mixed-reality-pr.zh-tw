---
title: GettingStartedWithMRTKAndXRSDK
description: 具有 XRSDK 的 MRTK 登陸頁面
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、XRSDK、
ms.openlocfilehash: 9344f103edbf666a73577ae521271c870d8b4d89
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692195"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="0d590-104">開始使用 MRTK 和 XR SDK</span><span class="sxs-lookup"><span data-stu-id="0d590-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="0d590-105">XR SDK 是 unity [2019.3 和以上的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。</span><span class="sxs-lookup"><span data-stu-id="0d590-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="0d590-106">在 Unity 2019 中，它會提供現有 XR 管線的替代方案。</span><span class="sxs-lookup"><span data-stu-id="0d590-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="0d590-107">在 Unity 2020 中，它將成為 Unity 中唯一的 XR 管線。</span><span class="sxs-lookup"><span data-stu-id="0d590-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0d590-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="0d590-108">Prerequisites</span></span>

<span data-ttu-id="0d590-109">若要開始使用 Mixed Reality 工具組，請遵循 [提供的步驟](../WelcomeToMRTK.md) 將 MRTK 新增至專案。</span><span class="sxs-lookup"><span data-stu-id="0d590-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../WelcomeToMRTK.md) to add MRTK to a project.</span></span>

## <a name="add-xr-sdk-to-a-unity-project"></a><span data-ttu-id="0d590-110">將 XR SDK 新增至 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="0d590-110">Add XR SDK to a Unity project</span></span>

<span data-ttu-id="0d590-111">XR SDK 支援 Windows Mixed Reality 和 Oculus。</span><span class="sxs-lookup"><span data-stu-id="0d590-111">Windows Mixed Reality and Oculus are supported on XR SDK.</span></span>

### <a name="required-in-unity"></a><span data-ttu-id="0d590-112">Unity 中的必要項</span><span class="sxs-lookup"><span data-stu-id="0d590-112">Required in Unity</span></span>

#### <a name="windows-mixed-reality"></a><span data-ttu-id="0d590-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="0d590-113">Windows Mixed Reality</span></span>

1. <span data-ttu-id="0d590-114">進入 Unity 的封裝管理員，並安裝 Windows XR 外掛程式套件，以新增 XR SDK 上的 Windows Mixed Reality 支援。</span><span class="sxs-lookup"><span data-stu-id="0d590-114">Go into Unity's Package Manager and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="0d590-115">這也會提取一些相依性套件。</span><span class="sxs-lookup"><span data-stu-id="0d590-115">This will pull down a few dependency packages as well.</span></span> <span data-ttu-id="0d590-116">確定已成功安裝下列各項：</span><span class="sxs-lookup"><span data-stu-id="0d590-116">Ensure the following all successfully installed:</span></span>
   1. <span data-ttu-id="0d590-117">XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="0d590-117">XR Plugin Management</span></span>
   1. <span data-ttu-id="0d590-118">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="0d590-118">Windows XR Plugin</span></span>
   1. <span data-ttu-id="0d590-119">XR 舊版輸入協助程式</span><span class="sxs-lookup"><span data-stu-id="0d590-119">XR Legacy Input Helpers</span></span>
1. <span data-ttu-id="0d590-120">移至 [編輯 > 專案設定]。</span><span class="sxs-lookup"><span data-stu-id="0d590-120">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="0d590-121">在 [專案設定] 視窗中，按一下 [XR 外掛程式管理] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0d590-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="0d590-122">移至 [通用 Windows 平臺設定]，並確定已核取 [外掛程式提供者] 下的 [Windows Mixed Reality]。</span><span class="sxs-lookup"><span data-stu-id="0d590-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
1. <span data-ttu-id="0d590-123">確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="0d590-123">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="0d590-124"> (**_編輯器中的 HoloLens 遠端處理需要，否則為選擇性_**) 移至獨立設定，並確定已在外掛程式提供者底下檢查 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="0d590-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="0d590-125">也請確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="0d590-125">Also ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="0d590-126"> (**_選擇性_**) 按一下 [XR 外掛程式管理] 下的 [Windows Mixed Reality] 索引標籤，然後建立自訂設定設定檔來變更預設值。</span><span class="sxs-lookup"><span data-stu-id="0d590-126">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="0d590-127">如果設定清單已經存在，則不需要建立任何設定檔。</span><span class="sxs-lookup"><span data-stu-id="0d590-127">If the list of settings are already there, no profile needs to be created.</span></span>

![外掛程式管理](../features/Images/XRSDK/PluginManagement.png)

### <a name="required-in-mrtk"></a><span data-ttu-id="0d590-129">MRTK 中的必要項</span><span class="sxs-lookup"><span data-stu-id="0d590-129">Required in MRTK</span></span>

<span data-ttu-id="0d590-130">選擇 "DefaultXRSDKConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。</span><span class="sxs-lookup"><span data-stu-id="0d590-130">Choose the "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span> <span data-ttu-id="0d590-131">此設定檔會在需要時，使用 MRTK 的 XR SDK 系統和提供者來設定。</span><span class="sxs-lookup"><span data-stu-id="0d590-131">This profile is set up with MRTK's XR SDK systems and providers, where needed.</span></span>

<span data-ttu-id="0d590-132">若要將現有的設定檔遷移至 XR SDK，應更新下列服務和資料提供者：</span><span class="sxs-lookup"><span data-stu-id="0d590-132">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

#### <a name="camera"></a><span data-ttu-id="0d590-133">相機</span><span class="sxs-lookup"><span data-stu-id="0d590-133">Camera</span></span>

<span data-ttu-id="0d590-134">從 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="0d590-134">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![舊版相機設定](../features/Images/XRSDK/CameraSystemLegacy.png)

<span data-ttu-id="0d590-136">至 [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **和**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="0d590-136">to [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span>

![XR SDK 攝影機設定](../features/Images/XRSDK/CameraSystemXRSDK.png)

#### <a name="input"></a><span data-ttu-id="0d590-138">輸入</span><span class="sxs-lookup"><span data-stu-id="0d590-138">Input</span></span>

<span data-ttu-id="0d590-139">從 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="0d590-139">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![舊版輸入設定](../features/Images/XRSDK/InputSystemWMRLegacy.png)

<span data-ttu-id="0d590-141">自 [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="0d590-141">to [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)</span></span>

![XR SDK 輸入設定](../features/Images/XRSDK/InputSystemWMRXRSDK.png)

#### <a name="boundary"></a><span data-ttu-id="0d590-143">界限</span><span class="sxs-lookup"><span data-stu-id="0d590-143">Boundary</span></span>

<span data-ttu-id="0d590-144">從 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="0d590-144">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![舊版界限設定](../features/Images/XRSDK/BoundarySystemLegacy.png)

<span data-ttu-id="0d590-146">自  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="0d590-146">to  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)</span></span>

![XR SDK 界限設定](../features/Images/XRSDK/BoundarySystemXRSDK.png)

#### <a name="spatial-awareness"></a><span data-ttu-id="0d590-148">空間感知</span><span class="sxs-lookup"><span data-stu-id="0d590-148">Spatial awareness</span></span>

<span data-ttu-id="0d590-149">從 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="0d590-149">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![舊版空間感知設定](../features/Images/XRSDK/SpatialAwarenessLegacy.png)

<span data-ttu-id="0d590-151">自 [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="0d590-151">to [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)</span></span>

![XR SDK 空間感知設定](../features/Images/XRSDK/SpatialAwarenessXRSDK.png)

#### <a name="controller-mappings"></a><span data-ttu-id="0d590-153">控制器對應</span><span class="sxs-lookup"><span data-stu-id="0d590-153">Controller mappings</span></span>

<span data-ttu-id="0d590-154">如果使用自訂控制器對應設定檔，請開啟其中一個設定檔，並執行混合現實工具組-> 公用程式-> 更新 > 控制器對應設定檔] 功能表項目，以確保已定義新的 XR SDK 控制器類型。</span><span class="sxs-lookup"><span data-stu-id="0d590-154">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d590-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d590-155">See also</span></span>

* [<span data-ttu-id="0d590-156">Unity 中的 AR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="0d590-156">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="0d590-157">Unity 中的 VR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="0d590-157">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
