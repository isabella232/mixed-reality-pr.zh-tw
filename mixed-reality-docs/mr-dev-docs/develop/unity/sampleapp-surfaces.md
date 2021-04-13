---
title: 表面
description: 瞭解如何在表面範例應用程式中，使用視覺效果、音訊和已明確呈現的手勢來建立 tactile sensations。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality、設計、範例應用程式、控制項、MRTK、混合現實工具組、Unity、範例應用程式、範例應用程式、開放原始碼、Microsoft Store、HoloLens、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 0e75a72ec518dea3513b6868aec56d1c7c89bd05
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300133"
---
# <a name="surfaces"></a><span data-ttu-id="6d7be-104">表面</span><span class="sxs-lookup"><span data-stu-id="6d7be-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="6d7be-105">本文討論我們在 [混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例，這是我們分享學習的地方，並提供混合現實應用程式開發的建議。</span><span class="sxs-lookup"><span data-stu-id="6d7be-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="6d7be-106">我們的設計相關文章和程式碼將隨著我們進行新探索而演進。</span><span class="sxs-lookup"><span data-stu-id="6d7be-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="6d7be-107">[表面](https://github.com/microsoft/MRDL_Unity_Surfaces)  是 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="6d7be-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="6d7be-108">它會探索如何使用視覺效果、音訊和完全明確的手動追蹤來建立 tactile 刺痛。</span><span class="sxs-lookup"><span data-stu-id="6d7be-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![表面](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="6d7be-110">示範影片</span><span class="sxs-lookup"><span data-stu-id="6d7be-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="6d7be-111">使用混合實境擷取 HoloLens 2 記錄</span><span class="sxs-lookup"><span data-stu-id="6d7be-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="6d7be-112">關於應用程式</span><span class="sxs-lookup"><span data-stu-id="6d7be-112">About the app</span></span>

<span data-ttu-id="6d7be-113">介面示範如何使用混合現實工具組 (MRTK) 的輸入系統和建立區塊，以建立 HoloLens 2 的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="6d7be-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="6d7be-114">在此專案中，您可以找到下列範例：</span><span class="sxs-lookup"><span data-stu-id="6d7be-114">In this project, you can find the examples of:</span></span>

- <span data-ttu-id="6d7be-115">使用 MRTK 的 [輸入系統](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview)，特別是手動/聯合追蹤。</span><span class="sxs-lookup"><span data-stu-id="6d7be-115">Use MRTK's [Input System](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="6d7be-116">針對高效能圖形使用 MRTK 的 [標準著色器](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) 。</span><span class="sxs-lookup"><span data-stu-id="6d7be-116">Use MRTK's [Standard Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) for performant graphics.</span></span>

<span data-ttu-id="6d7be-117">您可以使用此專案的元件來建立您自己的混合現實應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="6d7be-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="6d7be-118">MR 開發日 2020-學習自 MR 面應用程式</span><span class="sxs-lookup"><span data-stu-id="6d7be-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="6d7be-119">從 MR 表面應用程式學習</span><span class="sxs-lookup"><span data-stu-id="6d7be-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="6d7be-120">Lars Simkins 是 MRDL 表面應用程式背後的資深設計師，會討論應用程式的設計案例和技術重點。</span><span class="sxs-lookup"><span data-stu-id="6d7be-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="6d7be-121">GitHub 上的專案儲存機制</span><span class="sxs-lookup"><span data-stu-id="6d7be-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="6d7be-122">從 HoloLens 2 的 Microsoft Store 下載應用程式</span><span class="sxs-lookup"><span data-stu-id="6d7be-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="6d7be-123"> (應用程式僅適用于 HoloLens 2) </span><span class="sxs-lookup"><span data-stu-id="6d7be-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="6d7be-124">關於作者</span><span class="sxs-lookup"><span data-stu-id="6d7be-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="6d7be-125"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="6d7be-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="6d7be-126">UX 設計者 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="6d7be-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="6d7be-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d7be-127">See also</span></span>

* <span data-ttu-id="6d7be-128">[MRTK 範例中樞](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="6d7be-128">[MRTK Examples Hub](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="6d7be-129">[表面](sampleapp-surfaces.md) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="6d7be-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="6d7be-130">元素週期表 2.0</span><span class="sxs-lookup"><span data-stu-id="6d7be-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="6d7be-131">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="6d7be-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
