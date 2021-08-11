---
title: 設定您的 XR 設定
description: 隨時掌握 HoloLens 應用程式開發的最新 Unity XR 設定建議。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: 72f17ec9fc74143a2ae6cc51e1ffed0c73d13ef04ef5c4004537be70d1daaaca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202721"
---
# <a name="setting-up-your-xr-configuration"></a>設定您的 XR 設定

[選擇 Unity 版本](choosing-unity-version.md)後，下一個步驟是選取您將用來建立混合現實應用程式的 XR 設定：

## <a name="choosing-an-xr-configuration"></a>選擇 XR 設定

當您啟動新的 Unity 專案時，您會有各種不同的 XR 設定可供您選擇：**混合現實 OpenXR 外掛程式**、 **Windows XR 外掛程式** 和 **舊版內建 XR**。

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>使用 MRTK 設定您的專案

讓 Unity 專案的混合現實設定最簡單的方式，就是使用混合現實工具組 (MRTK) 。  適用于 Unity 的 MRTK 是開放原始碼的跨平臺開發工具組，旨在讓您輕鬆建立絕佳的混合現實應用程式。

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。  使用 MRTK 第2版，您可以加速 Microsoft HoloLens 的應用程式開發、Windows Mixed Reality 沉浸式 (VR) 耳機以及許多其他的 VR/AR 裝置。 專案的目標是要減少進入專案的阻礙，讓每個人都能建立混合的現實應用程式，並在我們全部成長的情況下貢獻給社區。

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

若要深入瞭解混合現實工具組，請參閱 [MRTK 檔](/windows/mixed-reality/mrtk-unity)。

## <a name="manual-setup-without-mrtk"></a>手動設定而不 MRTK

雖然 Microsoft 和社區建立了開放原始碼工具，例如 [混合現實工具組 (MRTK) ](/windows/mixed-reality/mrtk-unity) ，而這些工具會自動為混合的現實設定環境，但有些開發人員可能會想要從頭開始建立他們的體驗。

[!INCLUDE[](includes/xr/manual-setup.md)]