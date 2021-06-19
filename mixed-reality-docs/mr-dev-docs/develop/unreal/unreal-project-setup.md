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
# <a name="setting-up-your-unreal-project"></a><span data-ttu-id="80afa-104">設定您的 Unreal 專案</span><span class="sxs-lookup"><span data-stu-id="80afa-104">Setting up your Unreal project</span></span>

<span data-ttu-id="80afa-105">建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。</span><span class="sxs-lookup"><span data-stu-id="80afa-105">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="80afa-106">移至長篇遊戲啟動器中的 [ **媒體** 櫃] 索引標籤，選取 [ **啟動** ] 旁的下拉箭號，然後按一下 [ **選項**]。</span><span class="sxs-lookup"><span data-stu-id="80afa-106">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="80afa-107">在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="80afa-107">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="80afa-108">![Unreal 安裝選項 HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="80afa-108">![Unreal Install Option HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span></span>

## <a name="import-mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="80afa-109">匯入 Unreal 的混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="80afa-109">Import Mixed Reality Toolkit for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="80afa-111">混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="80afa-111">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="80afa-112">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="80afa-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="80afa-113">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="80afa-113">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="80afa-114">進行安裝時，建議您完成我們策劃的 [Unreal 開發旅程圖](unreal-development-overview.md)的[開始使用一節](unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="80afa-114">For installation, we recommend completing the [Getting Started section](unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](unreal-development-overview.md).</span></span> <span data-ttu-id="80afa-115">依循 Unreal 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="80afa-115">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="80afa-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 標誌影像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="80afa-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="80afa-117">**混合實境工具組-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="80afa-117">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="80afa-118">如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="80afa-118">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>