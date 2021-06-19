---
title: 設定您的 Unreal 專案
description: 瞭解如何設定您的專案 wit 最新版本的 Unreal 引擎和混合現實功能工具。
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal、Unreal Engine 4、UE4、HoloLens 2、mixed reality、開發、功能、新專案、模擬器、檔、指南、全息全像、遊戲開發、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394642"
---
# <a name="setting-up-your-unreal-project"></a>設定您的 Unreal 專案

建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。

移至長篇遊戲啟動器中的 [ **媒體** 櫃] 索引標籤，選取 [ **啟動** ] 旁的下拉箭號，然後按一下 [ **選項**]。 在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。
![Unreal 安裝選項 HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>匯入 Unreal 的混合現實工具組

![MRTK](../../design/images/MRTK_UX_Hero.png)

混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。 MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。 該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。

進行安裝時，建議您完成我們策劃的 [Unreal 開發旅程圖](unreal-development-overview.md)的[開始使用一節](unreal-development-overview.md#1-getting-started)。 依循 Unreal 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](tutorials/unreal-uxt-ch1.md)。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 標誌影像](../images/MRTK-Unreal-Banner.png)<br>**混合實境工具組-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。