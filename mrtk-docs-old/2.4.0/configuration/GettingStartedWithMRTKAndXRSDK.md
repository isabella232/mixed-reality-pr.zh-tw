---
title: GettingStartedWithMRTKAndXRSDK
description: 具有 XRSDK 的 MRTK 登陸頁面
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、XRSDK、
ms.openlocfilehash: c1f4baec1927fd97948245f31c40788473c457d0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681271"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>開始使用 MRTK 和 XR SDK

XR SDK 是 unity [2019.3 和以上的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。 在 Unity 2019 中，它會提供現有 XR 管線的替代方案。 在 Unity 2020 中，它將成為 Unity 中唯一的 XR 管線。

## <a name="prerequisites"></a>Prerequisites

若要開始使用 Mixed Reality 工具組，請遵循 [提供的步驟](../WelcomeToMRTK.md) 將 MRTK 新增至專案。

## <a name="add-xr-sdk-to-a-unity-project"></a>將 XR SDK 新增至 Unity 專案

針對 MRTK 2.3，XR SDK 支援 Windows Mixed Reality。

### <a name="required-in-unity"></a>Unity 中的必要項

1. 進入 Unity 的封裝管理員，並安裝 Windows XR 外掛程式套件，以新增 XR SDK 上的 Windows Mixed Reality 支援。 這也會提取一些相依性套件。 確定已成功安裝下列各項：
   1. XR 外掛程式管理
   1. Windows XR 外掛程式
   1. XR 舊版輸入協助程式
1. 移至 [編輯 > 專案設定]。
1. 在 [專案設定] 視窗中，按一下 [XR 外掛程式管理] 索引標籤。
1. 移至 [通用 Windows 平臺設定]，並確定已核取 [外掛程式提供者] 下的 [Windows Mixed Reality]。
1. 確定已核取 [啟動時初始化 XR]。
1.  (**_選擇性_**) 按一下 [XR 外掛程式管理] 下的 [Windows Mixed Reality] 索引標籤，然後建立自訂設定設定檔來變更預設值。 如果設定清單已經存在，則不需要建立任何設定檔。

![外掛程式管理](../features/Images/XRSDK/PluginManagement.png)

### <a name="required-in-mrtk"></a>MRTK 中的必要項

選擇 "DefaultXRSDKConfigurationProfile" 作為使用中的設定檔，或將其複製以進行自訂。 此設定檔會在需要時，使用 MRTK 的 XR SDK 系統和提供者來設定。

若要將現有的設定檔遷移至 XR SDK，應更新下列服務和資料提供者：

#### <a name="camera"></a>相機

從 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![舊版相機設定](../features/Images/XRSDK/CameraSystemLegacy.png)

至 [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **和**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)

![XR SDK 攝影機設定](../features/Images/XRSDK/CameraSystemXRSDK.png)

#### <a name="input"></a>輸入

從 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![舊版輸入設定](../features/Images/XRSDK/InputSystemWMRLegacy.png)

自 [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager)

![XR SDK 輸入設定](../features/Images/XRSDK/InputSystemWMRXRSDK.png)

#### <a name="boundary"></a>界限

從 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![舊版界限設定](../features/Images/XRSDK/BoundarySystemLegacy.png)

自  [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem)

![XR SDK 界限設定](../features/Images/XRSDK/BoundarySystemXRSDK.png)

#### <a name="spatial-awareness"></a>空間感知

從 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![舊版空間感知設定](../features/Images/XRSDK/SpatialAwarenessLegacy.png)

自 [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver)

![XR SDK 空間感知設定](../features/Images/XRSDK/SpatialAwarenessXRSDK.png)

#### <a name="controller-mappings"></a>控制器對應

如果使用自訂控制器對應設定檔，請開啟其中一個設定檔，並執行混合現實工具組-> 公用程式-> 更新 > 控制器對應設定檔] 功能表項目，以確保已定義新的 XR SDK 控制器類型。

## <a name="see-also"></a>另請參閱

* [Unity 中的 AR 開發使用者入門](https://docs.unity3d.com/Manual/AROverview.html)
* [Unity 中的 VR 開發使用者入門](https://docs.unity3d.com/Manual/VROverview.html)
