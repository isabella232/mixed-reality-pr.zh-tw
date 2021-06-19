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
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>混合現實 OpenXR Unity 中支援的功能

**Mixed Reality OpenXR 外掛程式** 套件是 Unity **OpenXR 外掛程式** 的延伸模組，並支援 HoloLens 2 和 Windows Mixed Reality 耳機的功能套件。 繼續之前，請確定您的 Unity 專案已 [設定為 OpenXR](openxr-getting-started.md)。

## <a name="whats-supported"></a>支援的項目

目前支援下列功能：

* 支援 HoloLens 2 的 UWP 應用程式，並針對 HoloLens 2 應用程式模型進行優化。
* 支援適用于 Windows Mixed Reality 耳機的 Win32 VR 應用程式，具有最新的控制器設定檔和全像應用程式遠端。
* 使用錨點和未系結空間的世界規模追蹤。
* [錨點儲存體 API，以將錨點保存](spatial-anchors-in-unity.md) 到 HoloLens 2 的本機儲存體。
* [移動控制器和手互動](#motion-controller-and-hand-interactions)，包括新的 HP 回音卡控制器。
* 使用26個接點和聯合半徑輸入，以明確表述的手勢進行追蹤。
* HoloLens 2 上的眼睛注視互動。
* HoloLens 2 上尋找 (PV) 攝影機的相片/影片。
* 混合實境擷取使用透過 PV 攝影機的第三種眼睛呈現。
* 支援「播放」以使用全像「 [遠端處理」應用程式 HoloLens 2](unity-play-mode.md#unity-play-mode-with-holographic-remoting)，讓開發人員不需要建立及部署到裝置，即可將腳本進行偵錯工具。
* 透過 [MRTK OpenXR 提供者支援](openxr-getting-started.md#using-mrtk-with-openxr-support)，與 MRTK Unity 2.5.3 和更新版本相容。
* 與 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更新版本相容。
*  (在 0.1.3) 中新增的功能，可支援從組建和部署的 Windows 獨立應用程式進行傳統型 [應用程式](holographic-remoting-desktop.md) 全像開發。
*  (在0.1.4 中新增) 透過 SpatialGraphNode 支援 HoloLens2 上的[QR 代碼追蹤](#qr-codes)
*  (在0.2.0 中新增) 在全像遠端處理中支援 **錨點**
*  (在0.2.0 中新增) 支援 **手接頭和手形網格追蹤**
*  (在0.2.0 中新增) 支援使用 **ARPlaneSubsystems** 進行平面偵測，並使用 **ARRaycastManager** 來放置全像影像。
*  (0.9.0) 支援空間對應的 **XRMeshSubsystem** 和 **ARMeshManager** 。
*  (在0.9.0 中新增) 支援適用于 Windows 外掛程式的 Azure 空間錨點 SDK。 如需詳細資訊，請參閱 [GitHub 上的 Mixed Reality + OpenXR Azure 空間錨點範例專案](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)。
*  (在 0.9.1) 中新增的功能，可支援從建立和部署的 Windows UWP 應用程式進行傳統型應用程式全像的遠端
* 除了 ARM64 for HoloLens 2 應用程式之外， (在0.9.4 中新增的) 支援 ARM 平臺。

## <a name="motion-controller-and-hand-interactions"></a>移動控制器和手互動

若要瞭解 Unity 中混合現實互動的基本概念，請流覽 unity [Manual For UNITY XR 輸入](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。 這項 Unity 檔涵蓋從控制器專屬輸入到更一般化 **InputFeatureUsage** 的對應、如何識別和分類可用的 XR 輸入、如何從這些輸入讀取資料等等。

Mixed Reality OpenXR 外掛程式提供額外的輸入互動設定檔，對應至標準 **InputFeatureUsage** s，如下所述：

| InputFeatureUsage | HP 回音 (OpenXR)  | HoloLens (OpenXR)  |
| ---- | ---- | ---- |
| primary2DAxis | 操縱 杆 | |
| primary2DAxisClick | 搖桿-按一下 | |
| 觸發程序 (trigger) | 觸發程序  | |
| 握 | 握 | 點擊或擠壓 |
| primaryButton | [X/A]-按下 | 空中點選 |
| secondaryButton | [Y/B]-按下 | |
| gripButton | 握住-按 | |
| triggerButton | 觸發程式-按下 | |
| menuButton | 功能表 | |

### <a name="aim-and-grip-poses"></a>目標和底姿勢

您可以透過 OpenXR 輸入互動存取兩組姿勢：

* 抓手中呈現物件的底框
* 目標是指向世界。

有關此設計的詳細資訊，以及這兩個姿勢之間的差異，請參閱 [OpenXR 規格-輸入子路徑](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。

InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供 **的姿勢全都代表 OpenXR 的** 把手姿勢。 與框姿勢相關的 InputFeatureUsages 是在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定義。

InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿勢全都代表 OpenXR 的 **目標** 。 這些 InputFeatureUsages 不會定義在任何包含的 c # 檔案中，因此您必須定義您自己的 InputFeatureUsages，如下所示：

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

如需在 Unity 的 XR 輸入系統中使用 haptics 的相關資訊，請參閱 unity [Manual For UNITY XR 輸入-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的檔。

## <a name="qr-codes"></a>QR 代碼

HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。 您可以在我們的 [QR 代碼追蹤](../platform-capabilities-and-apis/qr-code-tracking.md) 檔中找到更多詳細資料。  使用 OpenXR 外掛程式時，請[ `SpatialGraphNodeId` 從 QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)抓取，並使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 來尋找 qr 代碼。

如需參考，我們[在 GitHub 上有 QR 追蹤範例專案](https://github.com/yl-msft/QRTracking)，並有更詳細的[ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)使用說明。

## <a name="troubleshooting"></a>疑難排解

當您在 HoloLens 2 上暫停和繼續 Unity 應用程式時，應用程式無法正確地繼續，這會導致 HoloLens 視圖中有4個旋轉點。

* 將 OpenXR 專案設定中的 **深度提交模式** 設定為 [ **無** ] 作為因應措施
