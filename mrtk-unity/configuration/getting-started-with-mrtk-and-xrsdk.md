---
title: 開始使用 MRTK 和 XR SDK
description: 使用 XR SDK 的 MRTK 登陸頁面
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、XRSDK、XR SDK
ms.openlocfilehash: d3ff4306205cc6548bc5617d727f32a780855439
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647205"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="b85df-104">開始使用 MRTK 和 XR SDK</span><span class="sxs-lookup"><span data-stu-id="b85df-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="b85df-105">XR SDK 是 unity [2019.3 和以上的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。</span><span class="sxs-lookup"><span data-stu-id="b85df-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="b85df-106">在 Unity 2019 中，它會提供現有 XR 管線的替代方案。</span><span class="sxs-lookup"><span data-stu-id="b85df-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="b85df-107">在 Unity 2020 中，它將成為 Unity 中唯一的 XR 管線。</span><span class="sxs-lookup"><span data-stu-id="b85df-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b85df-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="b85df-108">Prerequisites</span></span>

<span data-ttu-id="b85df-109">若要開始使用 Mixed Reality 工具組，請遵循 [提供的步驟](../install-the-tools.md#importing-the-mixed-reality-toolkit) 將 MRTK 新增至專案。</span><span class="sxs-lookup"><span data-stu-id="b85df-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="b85df-110">設定 XR SDK 管線的 Unity</span><span class="sxs-lookup"><span data-stu-id="b85df-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="b85df-111">XR SDK 管線目前支援3個平臺： Windows Mixed Reality、Oculus 和 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="b85df-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="b85df-112">下列各節將涵蓋為每個平臺設定 XR SDK 所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="b85df-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="b85df-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b85df-113">Windows Mixed Reality</span></span>

<span data-ttu-id="b85df-114">進入 **Unity 的封裝管理員** ，並安裝 Windows XR 外掛程式套件，以新增 XR SDK 上的 Windows Mixed Reality 支援。</span><span class="sxs-lookup"><span data-stu-id="b85df-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="b85df-115">這也會提取一些相依性套件。</span><span class="sxs-lookup"><span data-stu-id="b85df-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="b85df-116">確定已成功安裝下列各項：</span><span class="sxs-lookup"><span data-stu-id="b85df-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="b85df-117">XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="b85df-117">XR Plugin Management</span></span>
   * <span data-ttu-id="b85df-118">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="b85df-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="b85df-119">XR 舊版輸入協助程式</span><span class="sxs-lookup"><span data-stu-id="b85df-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="b85df-120">移至 [編輯] > [專案設定]。</span><span class="sxs-lookup"><span data-stu-id="b85df-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="b85df-121">在 [專案設定] 視窗中，按一下 [XR 外掛程式管理] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b85df-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="b85df-122">移至 [通用 Windows 平臺設定]，並確定已核取 [外掛程式提供者] 下的 [Windows Mixed Reality]。</span><span class="sxs-lookup"><span data-stu-id="b85df-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="b85df-123">確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="b85df-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="b85df-124"> (**_編輯器中的 HoloLens 遠端處理需要，否則為選擇性_**) 移至獨立設定，並確定已在外掛程式提供者底下檢查 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="b85df-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="b85df-125">也請確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="b85df-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![已選取獨立索引標籤的 XR 外掛程式管理](images/xr-management-img-02.png)

7. <span data-ttu-id="b85df-127"> (**_選擇性_**) 按一下 [XR 外掛程式管理] 下的 [Windows Mixed Reality] 索引標籤，然後建立自訂設定設定檔來變更預設值。</span><span class="sxs-lookup"><span data-stu-id="b85df-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="b85df-128">如果設定清單已經存在，則不需要建立任何設定檔。</span><span class="sxs-lookup"><span data-stu-id="b85df-128">If the list of settings are already there, no profile needs to be created.</span></span>

![已選取 [Windows] 索引標籤的 XR 外掛程式管理](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="b85df-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="b85df-130">Oculus</span></span>

1. <span data-ttu-id="b85df-131">請遵循最後的 [XR SDK 管線指南，以瞭解如何在 MRTK 中設定 Oculus 的使用方式](../supported-devices/oculus-quest-mrtk.md) 。</span><span class="sxs-lookup"><span data-stu-id="b85df-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="b85df-132">本指南概述設定 Unity 和 MRTK 以使用 XR SDK 管線進行 Oculus 的要求所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="b85df-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="b85df-133">OpenXR (Preview) </span><span class="sxs-lookup"><span data-stu-id="b85df-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b85df-134">Unity 中的 OpenXR 僅支援 Unity 2020.2 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="b85df-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="b85df-135">目前它也只支援 x64 和 ARM64 組建。</span><span class="sxs-lookup"><span data-stu-id="b85df-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="b85df-136">遵循 [適用于 Unity 的 Mixed Reality OpenXR 外掛程式](/windows/mixed-reality/develop/unity/openxr-getting-started) 指南，包括設定 XR 外掛程式管理與優化的步驟，以將 OpenXR 外掛程式安裝至您的專案。</span><span class="sxs-lookup"><span data-stu-id="b85df-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="b85df-137">確定已成功安裝下列各項：</span><span class="sxs-lookup"><span data-stu-id="b85df-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="b85df-138">XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="b85df-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="b85df-139">OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="b85df-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="b85df-140">Mixed Reality OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="b85df-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="b85df-141">移至 [編輯 > 專案設定]。</span><span class="sxs-lookup"><span data-stu-id="b85df-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="b85df-142">在 [專案設定] 視窗中，按一下 [XR 外掛程式管理] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b85df-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="b85df-143">確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="b85df-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="b85df-144"> (**_選擇性_**) 如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [Microsoft HoloLens 功能組]</span><span class="sxs-lookup"><span data-stu-id="b85df-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![外掛程式管理開啟 XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="b85df-146">如果您有現有的專案正在使用 UPM 中的 MRTK，請確定下一行位於 MixedRealityToolkit 所產生資料夾的 **link.xml** 檔案中。</span><span class="sxs-lookup"><span data-stu-id="b85df-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="b85df-147">在 MRTK 和 OpenXR 的初始版本中，僅原生支援 HoloLens 2 表達的手和 Windows Mixed Reality 的移動控制器。</span><span class="sxs-lookup"><span data-stu-id="b85df-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="b85df-148">即將推出的版本中將會新增其他硬體的支援。</span><span class="sxs-lookup"><span data-stu-id="b85df-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="b85df-149">設定 XR SDK 管線的 MRTK</span><span class="sxs-lookup"><span data-stu-id="b85df-149">Configuring MRTK for the XR SDK pipeline</span></span>
::: moniker range=">= mrtkunity-2021-05" 
<span data-ttu-id="b85df-150">如果使用 OpenXR，請選擇 "DefaultOpenXRConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。</span><span class="sxs-lookup"><span data-stu-id="b85df-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="b85df-151">如果在 XR 外掛程式管理設定中使用其他 XR 執行時間（例如 Windows Mixed Reality 或 Oculus），請選擇 "DefaultXRSDKConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。</span><span class="sxs-lookup"><span data-stu-id="b85df-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="b85df-152">您可以視需要使用正確的系統和提供者來設定這些設定檔。</span><span class="sxs-lookup"><span data-stu-id="b85df-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="b85df-153">如需有關使用 XR SDK 的設定檔和範例支援的詳細資訊，請參閱 [設定檔](../features/profiles/profiles.md#xr-sdk) 檔。</span><span class="sxs-lookup"><span data-stu-id="b85df-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="b85df-154">若要將現有的設定檔遷移至 XR SDK，應新增下列服務和資料提供者。</span><span class="sxs-lookup"><span data-stu-id="b85df-154">To migrate an existing profile to XR SDK, the following services and data providers should be added.</span></span> <span data-ttu-id="b85df-155">您將能夠在 [XR SDK] 索引標籤下看到新的資料提供者</span><span class="sxs-lookup"><span data-stu-id="b85df-155">You will be able to see the new data providers under the XR SDK tab</span></span>

![[XR SDK] 索引標籤](../features/images/xrsdk/XrsdkTabView.png)

### <a name="camera"></a><span data-ttu-id="b85df-157">相機</span><span class="sxs-lookup"><span data-stu-id="b85df-157">Camera</span></span>

<span data-ttu-id="b85df-158">新增下列資料提供者</span><span class="sxs-lookup"><span data-stu-id="b85df-158">Add the following data providers</span></span> 

| <span data-ttu-id="b85df-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b85df-159">OpenXR</span></span> | <span data-ttu-id="b85df-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b85df-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="b85df-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**和**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="b85df-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![XR SDK 攝影機設定](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="b85df-163">輸入</span><span class="sxs-lookup"><span data-stu-id="b85df-163">Input</span></span>

<span data-ttu-id="b85df-164">新增下列資料提供者</span><span class="sxs-lookup"><span data-stu-id="b85df-164">Add the following data providers</span></span> 

| <span data-ttu-id="b85df-165">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b85df-165">OpenXR</span></span> | <span data-ttu-id="b85df-166">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b85df-166">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="b85df-167">__OpenXR__：</span><span class="sxs-lookup"><span data-stu-id="b85df-167">__OpenXR__:</span></span>

![OpenXR 輸入設定](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="b85df-169">__Windows Mixed Reality__：</span><span class="sxs-lookup"><span data-stu-id="b85df-169">__Windows Mixed Reality__:</span></span>

![XR SDK 輸入設定](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="b85df-171">界限</span><span class="sxs-lookup"><span data-stu-id="b85df-171">Boundary</span></span>

<span data-ttu-id="b85df-172">新增下列資料提供者</span><span class="sxs-lookup"><span data-stu-id="b85df-172">Add the following data providers</span></span> 

| <span data-ttu-id="b85df-173">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b85df-173">OpenXR</span></span> | <span data-ttu-id="b85df-174">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b85df-174">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 界限設定](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="b85df-176">空間感知</span><span class="sxs-lookup"><span data-stu-id="b85df-176">Spatial awareness</span></span>

<span data-ttu-id="b85df-177">新增下列資料提供者</span><span class="sxs-lookup"><span data-stu-id="b85df-177">Add the following data providers</span></span> 

| <span data-ttu-id="b85df-178">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b85df-178">OpenXR</span></span> | <span data-ttu-id="b85df-179">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b85df-179">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="b85df-180">正在進行</span><span class="sxs-lookup"><span data-stu-id="b85df-180">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![XR SDK 空間感知設定](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="b85df-182">控制器對應</span><span class="sxs-lookup"><span data-stu-id="b85df-182">Controller mappings</span></span>

<span data-ttu-id="b85df-183">如果使用自訂控制器對應設定檔，請開啟其中一個設定檔，並執行混合現實工具組-> 公用程式-> 更新 > 控制器對應設定檔] 功能表項目，以確保已定義新的 XR SDK 控制器類型。</span><span class="sxs-lookup"><span data-stu-id="b85df-183">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="b85df-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b85df-184">See also</span></span>

* [<span data-ttu-id="b85df-185">Unity 中的 AR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="b85df-185">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="b85df-186">Unity 中的 VR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="b85df-186">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="b85df-187">如果使用 OpenXR，請選擇 "DefaultOpenXRConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。</span><span class="sxs-lookup"><span data-stu-id="b85df-187">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="b85df-188">如果在 XR 外掛程式管理設定中使用其他 XR 執行時間（例如 Windows Mixed Reality 或 Oculus），請選擇 "DefaultXRSDKConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。</span><span class="sxs-lookup"><span data-stu-id="b85df-188">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="b85df-189">您可以視需要使用正確的系統和提供者來設定這些設定檔。</span><span class="sxs-lookup"><span data-stu-id="b85df-189">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="b85df-190">如需有關使用 XR SDK 的設定檔和範例支援的詳細資訊，請參閱 [設定檔](../features/profiles/profiles.md#xr-sdk) 檔。</span><span class="sxs-lookup"><span data-stu-id="b85df-190">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="b85df-191">若要將現有的設定檔遷移至 XR SDK，應更新下列服務和資料提供者：</span><span class="sxs-lookup"><span data-stu-id="b85df-191">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="b85df-192">相機</span><span class="sxs-lookup"><span data-stu-id="b85df-192">Camera</span></span>

<span data-ttu-id="b85df-193">從 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="b85df-193">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![舊版相機設定](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="b85df-195">to</span><span class="sxs-lookup"><span data-stu-id="b85df-195">to</span></span>

| <span data-ttu-id="b85df-196">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b85df-196">OpenXR</span></span> | <span data-ttu-id="b85df-197">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b85df-197">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="b85df-198">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**和**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="b85df-198">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![XR SDK 攝影機設定](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="b85df-200">輸入</span><span class="sxs-lookup"><span data-stu-id="b85df-200">Input</span></span>

<span data-ttu-id="b85df-201">從 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="b85df-201">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![舊版輸入設定](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="b85df-203">to</span><span class="sxs-lookup"><span data-stu-id="b85df-203">to</span></span>

| <span data-ttu-id="b85df-204">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b85df-204">OpenXR</span></span> | <span data-ttu-id="b85df-205">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b85df-205">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="b85df-206">__OpenXR__：</span><span class="sxs-lookup"><span data-stu-id="b85df-206">__OpenXR__:</span></span>

![OpenXR 輸入設定](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="b85df-208">__Windows Mixed Reality__：</span><span class="sxs-lookup"><span data-stu-id="b85df-208">__Windows Mixed Reality__:</span></span>

![XR SDK 輸入設定](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="b85df-210">界限</span><span class="sxs-lookup"><span data-stu-id="b85df-210">Boundary</span></span>

<span data-ttu-id="b85df-211">從 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="b85df-211">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![舊版界限設定](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="b85df-213">to</span><span class="sxs-lookup"><span data-stu-id="b85df-213">to</span></span>

| <span data-ttu-id="b85df-214">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b85df-214">OpenXR</span></span> | <span data-ttu-id="b85df-215">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b85df-215">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 界限設定](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="b85df-217">空間感知</span><span class="sxs-lookup"><span data-stu-id="b85df-217">Spatial awareness</span></span>

<span data-ttu-id="b85df-218">從 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="b85df-218">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![舊版空間感知設定](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="b85df-220">to</span><span class="sxs-lookup"><span data-stu-id="b85df-220">to</span></span>

| <span data-ttu-id="b85df-221">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b85df-221">OpenXR</span></span> | <span data-ttu-id="b85df-222">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b85df-222">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="b85df-223">正在進行</span><span class="sxs-lookup"><span data-stu-id="b85df-223">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![XR SDK 空間感知設定](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="b85df-225">控制器對應</span><span class="sxs-lookup"><span data-stu-id="b85df-225">Controller mappings</span></span>

<span data-ttu-id="b85df-226">如果使用自訂控制器對應設定檔，請開啟其中一個設定檔，並執行混合現實工具組-> 公用程式-> 更新 > 控制器對應設定檔] 功能表項目，以確保已定義新的 XR SDK 控制器類型。</span><span class="sxs-lookup"><span data-stu-id="b85df-226">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="b85df-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b85df-227">See also</span></span>

* [<span data-ttu-id="b85df-228">Unity 中的 AR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="b85df-228">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="b85df-229">Unity 中的 VR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="b85df-229">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end