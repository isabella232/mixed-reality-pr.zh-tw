---
title: 移植概觀
description: 介紹各種移植選項，以將現有應用程式用於 HoloLens 和 VR 的混合現實。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 移植、unity、中介軟體、引擎、UWP、Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600497"
---
# <a name="porting-overview"></a>移植概觀

當您想要移植或升級現有的專案時，您的移植旅程取決於您的應用程式是使用 Unity 或 Unreal 引擎所建立，並以 HoloLens (第1代) 或 HoloLens 2 或 SteamVR 為目標。 此總覽頁面包含我們針對每個平臺和裝置目前的建議-請務必回頭查看這些流程一律會變更。

首先，根據我們的 [Unity](#unity) 和 [Unreal](#unreal) 建議來設定您的專案目標，然後遵循一或多個移植案例：

- [HoloLens (第1代) 至 HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Windows Mixed Reality 頭戴式裝置](#windows-mixed-reality-headsets)
- [SteamVR 應用程式](#steamvr-applications)
- [2D UWP 應用程式](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>建議的專案目標

無論您是將應用程式移植到另一個目標裝置，都必須保持您的專案最新狀態。 如需我們目前的建議，請參閱下列以引擎為基礎的資源。

### <a name="unity"></a>Unity

我們目前有混合現實的 Unity 開發建議，是 **使用舊版 XR 封裝的 unity 2019 LTS**。 如果您的專案使用 Mixed Reality 工具組，請再次檢查您是否使用最新版本，也就是目前的 **MRTK-Unity 2.5**。

> [!CAUTION]
> 雖然此版本的 Unity 可使用 XR SDK，但 Azure 空間錨點目前不與此設定相容。 這項建議將會更新為適用于 Unity 的 Azure 空間錨點套件未來版本。
> 
> * 如果您不需要 Azure 空間錨點，您可以 [設定您的 Unity 專案以進行 XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) ，並 [開始使用 MRTK 和 XR SDK](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)。
> 
> * 如果您目前在專案中使用 XR SDK，而且想要使用 Azure 空間錨點，請將 XR SDK 卸載，然後重新安裝舊版 XR 套件來還原您的專案設定。

### <a name="unreal"></a>Unreal

我們目前對混合現實的 Unreal 開發建議是 **Unreal Engine 4.26**。 如果您的專案使用「混合現實工具組 UX 工具」，請確定您使用的是最新版本，其目前為 **UXT 0.10**。

## <a name="porting-scenarios"></a>移植案例

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens (第1代) Unity 應用程式到 HoloLens 2

如果您有現有的 HoloLens (第1代) Unity 應用程式，而您想要將其移植到 HoloLens 2，請依照 [HoloLens 移植文章](./porting-hl1-hl2.md)中的指示進行。

### <a name="windows-mixed-reality-headsets"></a>Windows Mixed Reality 頭戴式裝置

如果您已建立其他裝置的內容（例如 Oculus Rift 或 HP 回送 G2），則您必須將廠商專屬的 VR Sdk 和可能的輸入對應 Api 重定目標。 您可以在「 [沉浸式應用程式移植指南](porting-guides.md)」中找到 Unity 和 Unreal 移植案例的相關資訊。

### <a name="steamvr-applications"></a>SteamVR 應用程式

如需任何您想要更新 Windows Mixed Reality 耳機的 SteamVR 體驗，請參閱我們的 [SteamVR 更新指南](updating-your-steamvr-application-for-windows-mixed-reality.md)。

### <a name="2d-universal-windows-applications"></a>2D 通用 Windows 應用程式

如果您有想要移植到 Windows Mixed Reality 沉浸式耳機或 HoloLens 的現有 2D UWP 應用程式，請遵循我們 [的移植 2D uwp 應用程式，以取得 Windows Mixed Reality 的](building-2d-apps.md) 指示。