---
title: 手部與運動控制器
description: 瞭解手和移動控制器互動模型，其可以移除虛擬與實體之間的界限。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合的現實、手、運動控制器、互動、設計、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847320"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="4e6a1-104">手部與運動控制器</span><span class="sxs-lookup"><span data-stu-id="4e6a1-104">Hands and motion controllers</span></span>

## <a name="scenarios"></a><span data-ttu-id="4e6a1-105">案例</span><span class="sxs-lookup"><span data-stu-id="4e6a1-105">Scenarios</span></span>

<span data-ttu-id="4e6a1-106">閱讀 [互動總覽](interaction-fundamentals.md)之後，您可以選擇手和移動控制器互動模型。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-106">After reading the [interaction overview](interaction-fundamentals.md), you choose the hand and motion controller interaction model.</span></span> <span data-ttu-id="4e6a1-107">這表示您要開發一個應用程式，要求使用者使用兩次手與全像全球互動。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-107">This means you're developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="4e6a1-108">您的應用程式即將達成在虛擬和實體之間移除界限的目標。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-108">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="4e6a1-109">某些特定案例可能是：</span><span class="sxs-lookup"><span data-stu-id="4e6a1-109">Some specific scenarios might be:</span></span>
* <span data-ttu-id="4e6a1-110">為資訊工作者提供具有 UI 能供性的 2D 虛擬畫面，以顯示及控制內容</span><span class="sxs-lookup"><span data-stu-id="4e6a1-110">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="4e6a1-111">提供工廠元件線的第一行工作者教學課程和指南</span><span class="sxs-lookup"><span data-stu-id="4e6a1-111">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="4e6a1-112">開發專業工具以協助及教育醫療專業人員</span><span class="sxs-lookup"><span data-stu-id="4e6a1-112">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="4e6a1-113">使用 3D 虛擬物件來裝飾真實世界或建立第二個世界</span><span class="sxs-lookup"><span data-stu-id="4e6a1-113">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="4e6a1-114">以真實世界為背景來建立以位置為基礎的服務與遊戲</span><span class="sxs-lookup"><span data-stu-id="4e6a1-114">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="4e6a1-115">手和移動控制器形式</span><span class="sxs-lookup"><span data-stu-id="4e6a1-115">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="4e6a1-116">[![用手直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="4e6a1-116">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="4e6a1-117">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="4e6a1-117">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="4e6a1-118">運用使用者可用來觸控和操作全像的功能的樣式。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-118">Modality applying the power of hands that users can use to touch and manipulate holograms.</span></span> <span data-ttu-id="4e6a1-119">藉由使用每日體驗並提供適當的視覺 affordances，使用者就可以使用相同的方式來操作真實世界的物件，以與虛擬使用者互動。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-119">By using daily life experiences and providing proper visual affordances, users can use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="4e6a1-120">[![用手指向並認可](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="4e6a1-120">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="4e6a1-121">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="4e6a1-121">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="4e6a1-122">這種樣式可讓使用者在距離中與全像影像互動。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-122">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="4e6a1-123">它可讓使用者充分利用環境。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-123">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="4e6a1-124">使用者可以在任何地方放置全像位置，然後從任何距離進行存取。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-124">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="4e6a1-125">用來控制和操作2D 和3D 全像投影的精神模型和筆勢，與直接操作的高度同步。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-125">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="4e6a1-126">[![運動控制器](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="4e6a1-126">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="4e6a1-127">運動控制器</span><span class="sxs-lookup"><span data-stu-id="4e6a1-127">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="4e6a1-128">移動控制器會擴充使用者的實體功能，並在使用一或兩個區域時，以精確的方式進行互動。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-128">Motion controllers extend the user's physical capabilities with precise interactions across a range of distances while using one or both hands.</span></span> <span data-ttu-id="4e6a1-129">這些硬體配件提供許多常用互動的快捷方式，並針對各種動作提供 footed、tactile 的意見反應。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-129">These hardware accessories provide shortcuts to many commonly used interactions and provide sure-footed, tactile feedback for various actions.</span></span> <span data-ttu-id="4e6a1-130">目前，移動控制器僅適用于 Windows Mixed Reality (WMR) 案例。</span><span class="sxs-lookup"><span data-stu-id="4e6a1-130">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="4e6a1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e6a1-131">See also</span></span>
* [<span data-ttu-id="4e6a1-132">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="4e6a1-132">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="4e6a1-133">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="4e6a1-133">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="4e6a1-134">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="4e6a1-134">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4e6a1-135">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="4e6a1-135">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="4e6a1-136">免持式</span><span class="sxs-lookup"><span data-stu-id="4e6a1-136">Hands-free</span></span>](hands-free.md)
