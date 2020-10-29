---
title: 表面
description: 表面是 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。 它會探索如何使用視覺效果、音訊和完全明確的手動追蹤來建立 tactile 刺痛。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、mrtk、design、範例應用程式、控制項
ms.openlocfilehash: ee410e16a578efa53a38da2fb6b6477e109ac101
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91682681"
---
# <a name="surfaces"></a><span data-ttu-id="0f327-105">表面</span><span class="sxs-lookup"><span data-stu-id="0f327-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="0f327-106">本文討論我們在 [混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例，這是我們分享學習的地方，並提供混合現實應用程式開發的建議。</span><span class="sxs-lookup"><span data-stu-id="0f327-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="0f327-107">我們的設計相關文章和程式碼將隨著我們進行新探索而演進。</span><span class="sxs-lookup"><span data-stu-id="0f327-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="0f327-108">[表面](https://github.com/microsoft/MRDL_Unity_Surfaces)  是 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f327-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="0f327-109">它會探索如何使用視覺效果、音訊和完全明確的手動追蹤來建立 tactile 刺痛。</span><span class="sxs-lookup"><span data-stu-id="0f327-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![表面](images/MRDL_Surfaces_1.jpg)

## <a name="about-the-app"></a><span data-ttu-id="0f327-111">關於應用程式</span><span class="sxs-lookup"><span data-stu-id="0f327-111">About the app</span></span>
<span data-ttu-id="0f327-112">介面示範如何使用混合現實工具組 (MRTK) 的輸入系統和建立區塊，以建立 HoloLens 2 的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="0f327-112">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="0f327-113">在此專案中，您可以找到下列範例：</span><span class="sxs-lookup"><span data-stu-id="0f327-113">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="0f327-114">使用 MRTK 的 [輸入系統](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)，特別是手動/聯合追蹤。</span><span class="sxs-lookup"><span data-stu-id="0f327-114">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="0f327-115">針對高效能圖形使用 MRTK 的 [標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) 。</span><span class="sxs-lookup"><span data-stu-id="0f327-115">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="0f327-116">您可以使用此專案的元件來建立您自己的混合現實應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="0f327-116">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="0f327-117">MR 開發日 2020-學習自 MR 面應用程式</span><span class="sxs-lookup"><span data-stu-id="0f327-117">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="0f327-118">從 MR 表面應用程式學習</span><span class="sxs-lookup"><span data-stu-id="0f327-118">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="0f327-119">Lars Simkins 是 MRDL 表面應用程式背後的資深設計師，會討論應用程式的設計案例和技術重點。</span><span class="sxs-lookup"><span data-stu-id="0f327-119">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="0f327-120">GitHub 上的專案儲存機制</span><span class="sxs-lookup"><span data-stu-id="0f327-120">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="0f327-121">從 HoloLens 2 的 Microsoft Store 下載應用程式</span><span class="sxs-lookup"><span data-stu-id="0f327-121">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="0f327-122"> (應用程式僅適用于 HoloLens 2) </span><span class="sxs-lookup"><span data-stu-id="0f327-122">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="0f327-123">關於作者</span><span class="sxs-lookup"><span data-stu-id="0f327-123">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="0f327-124"><b>盾 Yoon 公園</b></span><span class="sxs-lookup"><span data-stu-id="0f327-124"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="0f327-125">UX 設計工具 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="0f327-125">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="0f327-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f327-126">See also</span></span>

* [<span data-ttu-id="0f327-127">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="0f327-127">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="0f327-128">物件集合</span><span class="sxs-lookup"><span data-stu-id="0f327-128">Object collection</span></span>](../../design/object-collection.md)
