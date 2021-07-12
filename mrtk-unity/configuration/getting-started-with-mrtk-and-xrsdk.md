---
title: 開始使用 MRTK 和 XR SDK
description: 使用 XR SDK 的 MRTK 登陸頁面
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、XRSDK、XR SDK
ms.openlocfilehash: bc2924f8e080b0c202f7c3e394a5382cf306431c
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603689"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>開始使用 MRTK 和 XR SDK

XR SDK 是 unity [2019.3 和以上的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。 在 Unity 2019 中，它會提供現有 XR 管線的替代方案。 在 Unity 2020 中，它是 Unity 中唯一的 XR 管線。

## <a name="prerequisites"></a>必要條件

若要開始使用 Mixed Reality 工具組，請遵循 [提供的步驟](../install-the-tools.md#importing-the-mixed-reality-toolkit) 將 MRTK 新增至專案。

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>設定 XR SDK 管線的 Unity

XR SDK 管線目前支援3個平臺： Windows Mixed Reality、Oculus 和 OpenXR。 下列各節將涵蓋為每個平臺設定 XR SDK 所需的步驟。

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

進入 **Unity 的封裝管理員**，並安裝 Windows XR 外掛程式套件，以新增對 XR SDK Windows Mixed Reality 的支援。 這也會提取一些相依性套件。

1. 確定已成功安裝下列各項：
   * XR 外掛程式管理
   * WindowsXR 外掛程式
   * XR 舊版輸入協助程式

2. 移至 [編輯] > [專案設定]。
3. 在 Project 設定] 視窗中，按一下 [XR 外掛程式管理] 索引標籤。
4. 移至 [通用 Windows 平臺設定]，並確定已核取 [外掛程式提供者] 下的 [Windows Mixed Reality]。
5. 確定已核取 [啟動時初始化 XR]。
6. **_在編輯器 HoloLens 遠端處理中需要 (，否則為選擇性_**) 移至 [獨立設定]，並確定已核取 [外掛程式提供者] 下的 Windows Mixed Reality。 也請確定已核取 [啟動時初始化 XR]。

    ![已選取獨立索引標籤的 XR 外掛程式管理](images/xr-management-img-02.png)

7.  (**_選擇性_**) 按一下 [XR 外掛程式管理] 下的 [Windows Mixed Reality] 索引標籤，然後建立自訂設定設定檔來變更預設值。 如果設定清單已經存在，則不需要建立任何設定檔。

    ![已選取 Windows 索引標籤的 XR 外掛程式管理](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. 請遵循最後的 [XR SDK 管線指南，以瞭解如何在 MRTK 中設定 Oculus 的使用方式](../supported-devices/oculus-quest-mrtk.md) 。 本指南概述設定 Unity 和 MRTK 以使用 XR SDK 管線進行 Oculus 的要求所需的步驟。

### <a name="openxr"></a>OpenXR

> [!IMPORTANT]
> Unity 中的 OpenXR 僅支援 Unity 2020.2 和更新版本。
> 它也只支援 x64、ARM 和 ARM64 組建。

1. 遵循 [適用于 Unity 的 Mixed Reality OpenXR 外掛程式](/windows/mixed-reality/develop/unity/openxr-getting-started) 指南，包括設定 XR 外掛程式管理與優化的步驟，以將 OpenXR 外掛程式安裝至您的專案。 確定已成功安裝下列各項：
   1. XR 外掛程式管理
   1. OpenXR 外掛程式
   1. Mixed Reality OpenXR 外掛程式
1. 移至 [編輯] > Project 設定。
1. 在 Project 設定] 視窗中，按一下 [XR 外掛程式管理] 索引標籤。
1. 確定已核取 [啟動時初始化 XR]。
1.  (**_選擇性_**) 如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [Microsoft HoloLens 功能組]

![外掛程式管理 OpenXR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> 如果您有現有的專案正在使用 UPM 中的 MRTK，請確定下一行位於 MixedRealityToolkit 所產生資料夾的 **link.xml** 檔案中。

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> 在 MRTK 和 OpenXR 的初始版本中，僅原生支援 HoloLens 2 表達的手和 Windows Mixed Reality 的移動控制器。 即將推出的版本中將會新增其他硬體的支援。

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>設定 XR SDK 管線的 MRTK

::: moniker range=">= mrtkunity-2021-05"
使用任何預設的 MRTK 設定檔，這些設定檔全都在 Unity 的 XR 管線中設定。 先前的 "DefaultOpenXRConfigurationProfile" 和 "DefaultXRSDKConfigurationProfile" 現在標示為過時。
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
如果使用 OpenXR，請選擇 "DefaultOpenXRConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。

如果在 XR 外掛程式管理設定中使用其他 XR 執行時間（例如 Windows Mixed Reality 或 Oculus），請選擇 "DefaultXRSDKConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。

您可以視需要使用正確的系統和提供者來設定這些設定檔。 如需有關使用 XR SDK 的設定檔和範例支援的詳細資訊，請參閱 [設定檔](../features/profiles/profiles.md#xr-sdk) 檔。
::: moniker-end

若要將現有的設定檔遷移至 XR SDK，應更新下列服務和資料提供者。
::: moniker range=">= mrtkunity-2021-05"
您將能夠在 Unity 2019 的 [XR SDK] 索引標籤底下，或在 Unity 2020 + 的主要/唯一視圖中看到新的資料提供者，其中舊版 XR 並不存在。

![[XR SDK] 索引標籤](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a>相機

::: moniker range=">= mrtkunity-2021-05"
新增下列資料提供者
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
從 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![舊版相機設定](../features/images/xrsdk/CameraSystemLegacy.png)

to
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| OpenXR 外掛程式 | WindowsXR 外掛程式 |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| OpenXR 外掛程式 | WindowsXR 外掛程式 |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![XR SDK 攝影機設定](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>輸入

::: moniker range=">= mrtkunity-2021-05"
新增下列資料提供者
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
從 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![舊版輸入設定](../features/images/xrsdk/InputSystemWMRLegacy.png)

to
::: moniker-end

| OpenXR 外掛程式 | WindowsXR 外掛程式 |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__：

![OpenXR 輸入設定](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__：

![XR SDK 輸入設定](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>界限

::: moniker range=">= mrtkunity-2021-05"
新增下列資料提供者
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
從 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![舊版界限設定](../features/images/xrsdk/BoundarySystemLegacy.png)

to
::: moniker-end

| OpenXR 外掛程式 | WindowsXR 外掛程式 |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 界限設定](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>空間感知

::: moniker range=">= mrtkunity-2021-05"
新增下列資料提供者
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
從 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![舊版空間感知設定](../features/images/xrsdk/SpatialAwarenessLegacy.png)

to
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| OpenXR 外掛程式 | WindowsXR 外掛程式 |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) UWP) 的 ( | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) UWP) 的 ( |
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) 非 UWP) 的 ( | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| OpenXR 外掛程式 | WindowsXR 外掛程式 |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![XR SDK 空間感知設定](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>控制器對應

如果使用自訂控制器對應設定檔，請開啟其中一個設定檔，並執行混合現實工具組-> 公用程式-> 更新 > 控制器對應設定檔] 功能表項目，以確保已定義新的 XR SDK 控制器類型。

## <a name="see-also"></a>另請參閱

* [Unity 中的 AR 開發使用者入門](https://docs.unity3d.com/Manual/AROverview.html)
* [Unity 中的 VR 開發使用者入門](https://docs.unity3d.com/Manual/VROverview.html)
