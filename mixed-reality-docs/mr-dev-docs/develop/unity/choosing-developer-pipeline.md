---
title: 選擇您的開發人員管線
description: 隨時掌握最新的適用于 HoloLens 應用程式開發的 Unity 開發管線建議。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394552"
---
# <a name="choosing-your-developer-pipeline"></a><span data-ttu-id="625c3-104">選擇您的開發人員管線</span><span class="sxs-lookup"><span data-stu-id="625c3-104">Choosing your developer pipeline</span></span>

![Unity 標誌橫幅](../images/unity_logo_banner.png)<br>

<span data-ttu-id="625c3-106">雖然我們目前 **建議您安裝 unity 2019.4 LTS，並使用舊版內建 XR** 進行混合現實開發，但您也可以使用其他 Unity 設定來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="625c3-106">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="mixed-reality-toolkit-recommended"></a><span data-ttu-id="625c3-107">混合現實工具組 (建議的) </span><span class="sxs-lookup"><span data-stu-id="625c3-107">Mixed Reality Toolkit (Recommended)</span></span>

<span data-ttu-id="625c3-108">Microsoft 目前針對 HoloLens 2 所建議的 Unity 設定是混合現實工具組 .。。</span><span class="sxs-lookup"><span data-stu-id="625c3-108">Microsoft’s current recommended Unity configuration for HoloLens 2 is the Mixed Reality Toolkit...</span></span>

### <a name="install-the-mixed-reality-feature-tool"></a><span data-ttu-id="625c3-109">安裝 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="625c3-109">Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="625c3-110">「 [混合現實」功能工具](welcome-to-mr-feature-tool.md) 是一種新的方法，讓開發人員可以探索並將混合現實功能套件新增至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="625c3-110">The [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="625c3-111">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="625c3-111">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="625c3-112">驗證您想要的套件之後，混合實境功能工具會將這些套件下載到您選擇的專案。</span><span class="sxs-lookup"><span data-stu-id="625c3-112">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="625c3-113">匯入 Unity 的混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="625c3-113">Importing the Mixed Reality Toolkit for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="625c3-115">[混合實境工具組](mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="625c3-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="625c3-116">遵循 [安裝和使用方式指示](welcome-to-mr-feature-tool.md#system-requirements) ，並選取 **混合現實工具組基礎** 套件，以安裝混合現實工具組套件。</span><span class="sxs-lookup"><span data-stu-id="625c3-116">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="625c3-117">建議您在策劃 [HoloLens](unity-development-overview.md#1-getting-started) 或 [VR](unity-development-wmr-overview.md#1-getting-started) 開發旅程中完成「開始使用」一節。</span><span class="sxs-lookup"><span data-stu-id="625c3-117">We recommend completing the getting started section in our curated [HoloLens](unity-development-overview.md#1-getting-started) or [VR](unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="625c3-118">依循適用於 HoloLens 的 Unity 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="625c3-118">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="625c3-119">請注意，安裝指示的目標是 MRTK 和 Unity 版本的最新穩定組合，也就是 **MRTK 2.6.1** 和 **unity 2019.4 LTS**。</span><span class="sxs-lookup"><span data-stu-id="625c3-119">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="625c3-120">如果您不想要使用適用于 Unity 的 MRTK，您必須 [自行編寫所有互動和行為的腳本](configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="625c3-120">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="625c3-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 橫幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="625c3-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="625c3-122">**混合實境工具組-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="625c3-122">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a><span data-ttu-id="625c3-123">手動</span><span class="sxs-lookup"><span data-stu-id="625c3-123">Manual</span></span> 

<span data-ttu-id="625c3-124">待定。。。</span><span class="sxs-lookup"><span data-stu-id="625c3-124">TBD...</span></span>