---
title: 移植概觀
description: 介紹各種移植選項，以將現有的應用程式帶入 HoloLens 和 VR 的混合現實。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 移植、unity、中介軟體、引擎、UWP、Win32
ms.openlocfilehash: 519dae088e689e0a6e617bf5e2b34f81cc2e265256c4844df7dd34e99172d536
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189418"
---
# <a name="porting-overview"></a>移植概觀

當您想要移植或升級現有的專案時，您的移植旅程取決於您的應用程式是以 Unity 或 Unreal 引擎建立的，而且目標 HoloLens (第1代) 或 HoloLens 2 或 SteamVR。 此總覽頁面包含我們針對每個平臺和裝置目前的建議-請務必回頭查看這些流程一律會變更。

首先，根據我們的 [Unity](#unity) 和 [Unreal](#unreal) 建議來設定您的專案目標，然後遵循一或多個移植案例：

- [HoloLens (第1代) 到 HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [沉浸式 VR 頭戴裝置](#immersive-vr-headsets)
- [2D UWP 應用程式](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>建議的專案目標

無論您是將應用程式移植到另一個目標裝置，都必須保持您的專案最新狀態。 如需我們目前的建議，請參閱下列以引擎為基礎的資源。

### <a name="unity"></a>Unity

如需建議的 Unity 和 MRTK 版本的最新指引，請參閱 [選擇 Unity 版本](../unity/choosing-unity-version.md) 頁面。

### <a name="unreal"></a>Unreal

如需建議的 Unreal 和 MRTK 版本的最新指引，請參閱 [設定 Unreal 專案](../unreal/unreal-project-setup.md) 頁面。

## <a name="porting-scenarios"></a>移植案例

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens (第1代) Unity 應用程式到 HoloLens 2

如果您有現有的 HoloLens (第1代) Unity 應用程式，而您想要將其移植到 HoloLens 2，請依照我們[HoloLens 移植文章](./porting-hl1-hl2.md)中的指示進行。

### <a name="immersive-vr-headsets"></a>沉浸式 VR 頭戴裝置

如果您已建立其他 VR 裝置的內容，則必須將任何廠商專屬的 VR Sdk 和可能的輸入對應 Api 重定目標。 您可以在「 [沉浸式應用程式移植指南](porting-guides.md)」中找到 Unity 和 Unreal 移植案例的相關資訊。

如需您想要更新 Windows Mixed Reality 耳機的 SteamVR 體驗，請參閱我們的[SteamVR 更新指南](updating-your-steamvr-application-for-windows-mixed-reality.md)。

### <a name="2d-universal-windows-applications"></a>2d 通用 Windows 應用程式

如果您有想要移植到 Windows Mixed Reality 沉浸式耳機或 HoloLens 的現有 2d uwp 應用程式，請遵循我們[的移植 2d uwp 應用程式，以取得 Windows Mixed Reality](building-2d-apps.md)指示。