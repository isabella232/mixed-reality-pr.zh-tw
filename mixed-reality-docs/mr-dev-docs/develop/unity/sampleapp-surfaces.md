---
title: 表面
description: 瞭解如何在表面範例應用程式中，使用視覺效果、音訊和已明確呈現的手勢來建立 tactile sensations。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality、設計、範例應用程式、控制項、MRTK、混合現實工具組、Unity、範例應用程式、範例應用程式、開放原始碼、Microsoft Store、HoloLens、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 28f8bc1e1f30573936067a83b1ad26133c23c5b8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743397"
---
# <a name="surfaces"></a><span data-ttu-id="b7762-104">表面</span><span class="sxs-lookup"><span data-stu-id="b7762-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="b7762-105">本文討論我們在 [混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例，這是我們分享學習的地方，並提供混合現實應用程式開發的建議。</span><span class="sxs-lookup"><span data-stu-id="b7762-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="b7762-106">我們的設計相關文章和程式碼將隨著我們進行新探索而演進。</span><span class="sxs-lookup"><span data-stu-id="b7762-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="b7762-107">[表面](https://github.com/microsoft/MRDL_Unity_Surfaces)  是 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7762-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="b7762-108">它會探索如何使用視覺效果、音訊和完全明確的手動追蹤來建立 tactile 刺痛。</span><span class="sxs-lookup"><span data-stu-id="b7762-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![表面](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="b7762-110">示範影片</span><span class="sxs-lookup"><span data-stu-id="b7762-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="b7762-111">使用混合實境擷取 HoloLens 2 記錄</span><span class="sxs-lookup"><span data-stu-id="b7762-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="b7762-112">關於應用程式</span><span class="sxs-lookup"><span data-stu-id="b7762-112">About the app</span></span>

<span data-ttu-id="b7762-113">介面示範如何使用混合現實工具組 (MRTK) 的輸入系統和建立區塊，以建立 HoloLens 2 的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="b7762-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="b7762-114">在此專案中，您可以找到下列範例：</span><span class="sxs-lookup"><span data-stu-id="b7762-114">In this project, you can find the examples of:</span></span>

- <span data-ttu-id="b7762-115">使用 MRTK 的 [輸入系統](/windows/mixed-reality/mrtk-unity/features/input/overview)，特別是手動/聯合追蹤。</span><span class="sxs-lookup"><span data-stu-id="b7762-115">Use MRTK's [Input System](/windows/mixed-reality/mrtk-unity/features/input/overview), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="b7762-116">針對高效能圖形使用 MRTK 的 [標準著色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) 。</span><span class="sxs-lookup"><span data-stu-id="b7762-116">Use MRTK's [Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) for performant graphics.</span></span>

<span data-ttu-id="b7762-117">您可以使用此專案的元件來建立您自己的混合現實應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="b7762-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="b7762-118">MR 開發日 2020-學習自 MR 面應用程式</span><span class="sxs-lookup"><span data-stu-id="b7762-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="b7762-119">從 MR 表面應用程式學習</span><span class="sxs-lookup"><span data-stu-id="b7762-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="b7762-120">Lars Simkins 是 MRDL 表面應用程式背後的資深設計師，會討論應用程式的設計案例和技術重點。</span><span class="sxs-lookup"><span data-stu-id="b7762-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="b7762-121">GitHub 上的專案儲存機制</span><span class="sxs-lookup"><span data-stu-id="b7762-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="b7762-122">從 HoloLens 2 的 Microsoft Store 下載應用程式</span><span class="sxs-lookup"><span data-stu-id="b7762-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="b7762-123"> (應用程式僅適用于 HoloLens 2) </span><span class="sxs-lookup"><span data-stu-id="b7762-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="b7762-124">關於作者</span><span class="sxs-lookup"><span data-stu-id="b7762-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="b7762-125"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="b7762-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="b7762-126">UX 設計者 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="b7762-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="b7762-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7762-127">See also</span></span>

* <span data-ttu-id="b7762-128">[MRTK 範例中樞](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="b7762-128">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="b7762-129">[表面](sampleapp-surfaces.md) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="b7762-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="b7762-130">元素週期表 2.0</span><span class="sxs-lookup"><span data-stu-id="b7762-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="b7762-131">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="b7762-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)