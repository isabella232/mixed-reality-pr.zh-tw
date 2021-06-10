---
title: 開始使用 MRTK 和 XR SDK
description: 使用 XR SDK 的 MRTK 登陸頁面
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、XRSDK、XR SDK
ms.openlocfilehash: 01aca42ab4e883d26a814a1572d39eda7576ab57
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908384"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="6fe8a-104">開始使用 MRTK 和 XR SDK</span><span class="sxs-lookup"><span data-stu-id="6fe8a-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="6fe8a-105">XR SDK 是 unity [2019.3 和以上的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="6fe8a-106">在 Unity 2019 中，它會提供現有 XR 管線的替代方案。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="6fe8a-107">在 Unity 2020 中，它是 Unity 中唯一的 XR 管線。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-107">In Unity 2020, it is the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6fe8a-108">先決條件</span><span class="sxs-lookup"><span data-stu-id="6fe8a-108">Prerequisites</span></span>

<span data-ttu-id="6fe8a-109">若要開始使用 Mixed Reality 工具組，請遵循 [提供的步驟](../install-the-tools.md#importing-the-mixed-reality-toolkit) 將 MRTK 新增至專案。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="6fe8a-110">設定 XR SDK 管線的 Unity</span><span class="sxs-lookup"><span data-stu-id="6fe8a-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="6fe8a-111">XR SDK 管線目前支援3個平臺： Windows Mixed Reality、Oculus 和 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="6fe8a-112">下列各節將涵蓋為每個平臺設定 XR SDK 所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="6fe8a-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6fe8a-113">Windows Mixed Reality</span></span>

<span data-ttu-id="6fe8a-114">進入 **Unity 的封裝管理員** ，並安裝 Windows XR 外掛程式套件，以新增 XR SDK 上的 Windows Mixed Reality 支援。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="6fe8a-115">這也會提取一些相依性套件。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-115">This will pull down a few dependency packages as well.</span></span>

1. <span data-ttu-id="6fe8a-116">確定已成功安裝下列各項：</span><span class="sxs-lookup"><span data-stu-id="6fe8a-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="6fe8a-117">XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="6fe8a-117">XR Plugin Management</span></span>
   * <span data-ttu-id="6fe8a-118">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="6fe8a-119">XR 舊版輸入協助程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="6fe8a-120">移至 [編輯] > [專案設定]。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="6fe8a-121">在 [專案設定] 視窗中，按一下 [XR 外掛程式管理] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="6fe8a-122">移至 [通用 Windows 平臺設定]，並確定已核取 [外掛程式提供者] 下的 [Windows Mixed Reality]。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="6fe8a-123">確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="6fe8a-124"> (**_編輯器中的 HoloLens 遠端處理需要，否則為選擇性_**) 移至獨立設定，並確定已在外掛程式提供者底下檢查 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="6fe8a-125">也請確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-125">Also ensure that Initialize XR on Startup is checked.</span></span>

    ![已選取獨立索引標籤的 XR 外掛程式管理](images/xr-management-img-02.png)

7. <span data-ttu-id="6fe8a-127"> (**_選擇性_**) 按一下 [XR 外掛程式管理] 下的 [Windows Mixed Reality] 索引標籤，然後建立自訂設定設定檔來變更預設值。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="6fe8a-128">如果設定清單已經存在，則不需要建立任何設定檔。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-128">If the list of settings are already there, no profile needs to be created.</span></span>

    ![已選取 [Windows] 索引標籤的 XR 外掛程式管理](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="6fe8a-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="6fe8a-130">Oculus</span></span>

1. <span data-ttu-id="6fe8a-131">請遵循最後的 [XR SDK 管線指南，以瞭解如何在 MRTK 中設定 Oculus 的使用方式](../supported-devices/oculus-quest-mrtk.md) 。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="6fe8a-132">本指南概述設定 Unity 和 MRTK 以使用 XR SDK 管線進行 Oculus 的要求所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="6fe8a-133">OpenXR (Preview) </span><span class="sxs-lookup"><span data-stu-id="6fe8a-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6fe8a-134">Unity 中的 OpenXR 僅支援 Unity 2020.2 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
> <span data-ttu-id="6fe8a-135">它也只支援 x64、ARM 和 ARM64 組建。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-135">It also only supports x64, ARM, and ARM64 builds.</span></span>

1. <span data-ttu-id="6fe8a-136">遵循 [適用于 Unity 的 Mixed Reality OpenXR 外掛程式](/windows/mixed-reality/develop/unity/openxr-getting-started) 指南，包括設定 XR 外掛程式管理與優化的步驟，以將 OpenXR 外掛程式安裝至您的專案。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="6fe8a-137">確定已成功安裝下列各項：</span><span class="sxs-lookup"><span data-stu-id="6fe8a-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="6fe8a-138">XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="6fe8a-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="6fe8a-139">OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="6fe8a-140">Mixed Reality OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="6fe8a-141">移至 [編輯 > 專案設定]。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="6fe8a-142">在 [專案設定] 視窗中，按一下 [XR 外掛程式管理] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="6fe8a-143">確定已核取 [啟動時初始化 XR]。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="6fe8a-144"> (**_選擇性_**) 如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [Microsoft HoloLens 功能組]</span><span class="sxs-lookup"><span data-stu-id="6fe8a-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![外掛程式管理 OpenXR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="6fe8a-146">如果您有現有的專案正在使用 UPM 中的 MRTK，請確定下一行位於 MixedRealityToolkit 所產生資料夾的 **link.xml** 檔案中。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="6fe8a-147">在 MRTK 和 OpenXR 的初始版本中，僅原生支援 HoloLens 2 表達的手和 Windows Mixed Reality 的移動控制器。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="6fe8a-148">即將推出的版本中將會新增其他硬體的支援。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="6fe8a-149">設定 XR SDK 管線的 MRTK</span><span class="sxs-lookup"><span data-stu-id="6fe8a-149">Configuring MRTK for the XR SDK pipeline</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="6fe8a-150">使用任何預設的 MRTK 設定檔，這些設定檔全都在 Unity 的 XR 管線中設定。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-150">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="6fe8a-151">先前的 "DefaultOpenXRConfigurationProfile" 和 "DefaultXRSDKConfigurationProfile" 現在標示為過時。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-151">The previous "DefaultOpenXRConfigurationProfile" and "DefaultXRSDKConfigurationProfile" are now labeled obsolete.</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="6fe8a-152">如果使用 OpenXR，請選擇 "DefaultOpenXRConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-152">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="6fe8a-153">如果在 XR 外掛程式管理設定中使用其他 XR 執行時間（例如 Windows Mixed Reality 或 Oculus），請選擇 "DefaultXRSDKConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-153">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="6fe8a-154">您可以視需要使用正確的系統和提供者來設定這些設定檔。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-154">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="6fe8a-155">如需有關使用 XR SDK 的設定檔和範例支援的詳細資訊，請參閱 [設定檔](../features/profiles/profiles.md#xr-sdk) 檔。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-155">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>
::: moniker-end

<span data-ttu-id="6fe8a-156">若要將現有的設定檔遷移至 XR SDK，應更新下列服務和資料提供者。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-156">To migrate an existing profile to XR SDK, the following services and data providers should be updated.</span></span>
::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="6fe8a-157">您將能夠在 Unity 2019 的 [XR SDK] 索引標籤底下，或在 Unity 2020 + 的主要/唯一視圖中看到新的資料提供者，其中舊版 XR 並不存在。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-157">You will be able to see the new data providers under the XR SDK tab in Unity 2019, or in the main/only view in Unity 2020+, where legacy XR doesn't exist.</span></span>

![[XR SDK] 索引標籤](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a><span data-ttu-id="6fe8a-159">相機</span><span class="sxs-lookup"><span data-stu-id="6fe8a-159">Camera</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="6fe8a-160">新增下列資料提供者</span><span class="sxs-lookup"><span data-stu-id="6fe8a-160">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="6fe8a-161">從 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="6fe8a-161">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![舊版相機設定](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="6fe8a-163">to</span><span class="sxs-lookup"><span data-stu-id="6fe8a-163">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="6fe8a-164">OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-164">OpenXR Plugin</span></span> | <span data-ttu-id="6fe8a-165">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-165">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="6fe8a-166">OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-166">OpenXR Plugin</span></span> | <span data-ttu-id="6fe8a-167">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-167">Windows XR Plugin</span></span> |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![XR SDK 攝影機設定](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="6fe8a-169">輸入</span><span class="sxs-lookup"><span data-stu-id="6fe8a-169">Input</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="6fe8a-170">新增下列資料提供者</span><span class="sxs-lookup"><span data-stu-id="6fe8a-170">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="6fe8a-171">從 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="6fe8a-171">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![舊版輸入設定](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="6fe8a-173">to</span><span class="sxs-lookup"><span data-stu-id="6fe8a-173">to</span></span>
::: moniker-end

| <span data-ttu-id="6fe8a-174">OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-174">OpenXR Plugin</span></span> | <span data-ttu-id="6fe8a-175">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-175">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="6fe8a-176">__OpenXR__：</span><span class="sxs-lookup"><span data-stu-id="6fe8a-176">__OpenXR__:</span></span>

![OpenXR 輸入設定](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="6fe8a-178">__Windows Mixed Reality__：</span><span class="sxs-lookup"><span data-stu-id="6fe8a-178">__Windows Mixed Reality__:</span></span>

![XR SDK 輸入設定](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="6fe8a-180">界限</span><span class="sxs-lookup"><span data-stu-id="6fe8a-180">Boundary</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="6fe8a-181">新增下列資料提供者</span><span class="sxs-lookup"><span data-stu-id="6fe8a-181">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="6fe8a-182">從 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="6fe8a-182">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![舊版界限設定](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="6fe8a-184">to</span><span class="sxs-lookup"><span data-stu-id="6fe8a-184">to</span></span>
::: moniker-end

| <span data-ttu-id="6fe8a-185">OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-185">OpenXR Plugin</span></span> | <span data-ttu-id="6fe8a-186">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-186">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 界限設定](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="6fe8a-188">空間感知</span><span class="sxs-lookup"><span data-stu-id="6fe8a-188">Spatial awareness</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="6fe8a-189">新增下列資料提供者</span><span class="sxs-lookup"><span data-stu-id="6fe8a-189">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="6fe8a-190">從 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="6fe8a-190">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![舊版空間感知設定](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="6fe8a-192">to</span><span class="sxs-lookup"><span data-stu-id="6fe8a-192">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="6fe8a-193">OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-193">OpenXR Plugin</span></span> | <span data-ttu-id="6fe8a-194">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-194">Windows XR Plugin</span></span> |
|---------------|-------------------|
| <span data-ttu-id="6fe8a-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) UWP) 的 (</span><span class="sxs-lookup"><span data-stu-id="6fe8a-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (for UWP)</span></span> | <span data-ttu-id="6fe8a-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) UWP) 的 (</span><span class="sxs-lookup"><span data-stu-id="6fe8a-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (for UWP)</span></span> |
| <span data-ttu-id="6fe8a-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) 非 UWP) 的 (</span><span class="sxs-lookup"><span data-stu-id="6fe8a-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (for non-UWP)</span></span> | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="6fe8a-198">OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-198">OpenXR Plugin</span></span> | <span data-ttu-id="6fe8a-199">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="6fe8a-199">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![XR SDK 空間感知設定](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="6fe8a-201">控制器對應</span><span class="sxs-lookup"><span data-stu-id="6fe8a-201">Controller mappings</span></span>

<span data-ttu-id="6fe8a-202">如果使用自訂控制器對應設定檔，請開啟其中一個設定檔，並執行混合現實工具組-> 公用程式-> 更新 > 控制器對應設定檔] 功能表項目，以確保已定義新的 XR SDK 控制器類型。</span><span class="sxs-lookup"><span data-stu-id="6fe8a-202">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fe8a-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fe8a-203">See also</span></span>

* [<span data-ttu-id="6fe8a-204">Unity 中的 AR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="6fe8a-204">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="6fe8a-205">Unity 中的 VR 開發使用者入門</span><span class="sxs-lookup"><span data-stu-id="6fe8a-205">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
