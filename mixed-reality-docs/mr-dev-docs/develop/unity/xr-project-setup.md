---
title: 設定您的 XR 設定
description: 隨時掌握 HoloLens 應用程式開發的最新 Unity XR 設定建議。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603707"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="5e502-104">設定您的 XR 設定</span><span class="sxs-lookup"><span data-stu-id="5e502-104">Setting up your XR configuration</span></span>

<span data-ttu-id="5e502-105">[選擇 Unity 版本](choosing-unity-version.md)後，下一個步驟是選取您將用來建立混合現實應用程式的 XR 設定：</span><span class="sxs-lookup"><span data-stu-id="5e502-105">Once you've [chosen a Unity version](choosing-unity-version.md), the next step is to select the XR configuration you'll use to build your mixed reality app:</span></span>

## <a name="choosing-an-xr-configuration"></a><span data-ttu-id="5e502-106">選擇 XR 設定</span><span class="sxs-lookup"><span data-stu-id="5e502-106">Choosing an XR configuration</span></span>

<span data-ttu-id="5e502-107">當您啟動新的 Unity 專案時，您會有各種不同的 XR 設定可供您選擇：**混合現實 OpenXR 外掛程式**、 **Windows XR 外掛程式** 和 **舊版內建 XR**。</span><span class="sxs-lookup"><span data-stu-id="5e502-107">When you start a new Unity project, you have various XR configurations you can select from: the **Mixed Reality OpenXR plugin**, the **Windows XR plugin** and **Legacy Built-in XR**.</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="5e502-108">使用 MRTK 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="5e502-108">Setting up your project with MRTK</span></span>

<span data-ttu-id="5e502-109">讓 Unity 專案的混合現實設定最簡單的方式，就是使用混合現實工具組 (MRTK) 。</span><span class="sxs-lookup"><span data-stu-id="5e502-109">The easiest way to get your Unity project set up for mixed reality is with the Mixed Reality Toolkit (MRTK).</span></span>  <span data-ttu-id="5e502-110">適用于 Unity 的 MRTK 是開放原始碼的跨平臺開發工具組，旨在讓您輕鬆建立絕佳的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e502-110">MRTK for Unity is an open-source, cross-platform development kit designed to make it easy to build amazing mixed reality applications.</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="5e502-112">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="5e502-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span>  <span data-ttu-id="5e502-113">使用 MRTK 第2版，您可以加速 Microsoft HoloLens 的應用程式開發、Windows Mixed Reality 沉浸式 (VR) 耳機以及許多其他的 VR/AR 裝置。</span><span class="sxs-lookup"><span data-stu-id="5e502-113">With MRTK version 2, you can speed up your application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and many other VR/AR devices.</span></span> <span data-ttu-id="5e502-114">專案的目標是要減少進入專案的阻礙，讓每個人都能建立混合的現實應用程式，並在我們全部成長的情況下貢獻給社區。</span><span class="sxs-lookup"><span data-stu-id="5e502-114">The project is aimed at reducing barriers to entry, enabling everyone to build mixed reality applications and contribute back to the community as we all grow.</span></span>

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

<span data-ttu-id="5e502-115">若要深入瞭解混合現實工具組，請參閱 [MRTK 檔](/windows/mixed-reality/mrtk-unity)。</span><span class="sxs-lookup"><span data-stu-id="5e502-115">To learn more about the Mixed Reality Toolkit, check out the [MRTK documentation](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="5e502-116">手動設定而不 MRTK</span><span class="sxs-lookup"><span data-stu-id="5e502-116">Manual setup without MRTK</span></span>

<span data-ttu-id="5e502-117">雖然 Microsoft 和社區建立了開放原始碼工具，例如 [混合現實工具組 (MRTK) ](/windows/mixed-reality/mrtk-unity) ，而這些工具會自動為混合的現實設定環境，但有些開發人員可能會想要從頭開始建立他們的體驗。</span><span class="sxs-lookup"><span data-stu-id="5e502-117">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) that will automatically set up your environment for mixed reality, some developers may wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]