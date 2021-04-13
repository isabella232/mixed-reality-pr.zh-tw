---
title: 入門教學課程 - 3。 設定 MRTK 設定檔
description: 本課程說明如何設定混合實境工具組 (MRTK) 設定檔。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, 空間感知
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300453"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="481e4-105">3.設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="481e4-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="481e4-106">概觀</span><span class="sxs-lookup"><span data-stu-id="481e4-106">Overview</span></span>

<span data-ttu-id="481e4-107">在本教學課程中，您將了解如何自訂和設定 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="481e4-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="481e4-108"><a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK 設定檔</a>是巢狀設定檔的樹狀結構，其構成了 MRTK 系統和功能應如何初始化的組態設定資訊。</span><span class="sxs-lookup"><span data-stu-id="481e4-108">The <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="481e4-109">最上層設定檔 (組態設定檔) 包含每個主要核心系統的巢狀設定檔。</span><span class="sxs-lookup"><span data-stu-id="481e4-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="481e4-110">每個巢狀設定檔都是設計來設定其對應系統的行為。</span><span class="sxs-lookup"><span data-stu-id="481e4-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="481e4-111">此特定範例將示範如何藉由變更空間網格觀察器的設定，來隱藏空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="481e4-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="481e4-112">不過，您也可以遵循這些相同原則，自訂 MRTK 設定檔中的任何設定或值。</span><span class="sxs-lookup"><span data-stu-id="481e4-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="481e4-113">正如您在進行[上一個教學課程](mr-learning-base-02.md#congratulations)的期間將專案部署至 HoloLens 2 時所經歷的體驗，<a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">空間感知</a>網格是代表環境幾何的網格所形成的集合。</span><span class="sxs-lookup"><span data-stu-id="481e4-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="481e4-114">一開始，這樣的視覺效果很有用，但我們一般會將此功能關閉，以免遇到開啟此功能時所會遭遇的視覺干擾和額外的效能減損。</span><span class="sxs-lookup"><span data-stu-id="481e4-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="481e4-115">目標</span><span class="sxs-lookup"><span data-stu-id="481e4-115">Objectives</span></span>

* <span data-ttu-id="481e4-116">了解如何自訂和設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="481e4-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="481e4-117">隱藏空間感知網格</span><span class="sxs-lookup"><span data-stu-id="481e4-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="481e4-118">變更空間感知顯示選項</span><span class="sxs-lookup"><span data-stu-id="481e4-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="481e4-119">隱藏空間感知網格所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="481e4-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="481e4-120">複製預設的組態設定檔</span><span class="sxs-lookup"><span data-stu-id="481e4-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="481e4-121">啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="481e4-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="481e4-122">複製預設的空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="481e4-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="481e4-123">複製預設的空間感知網格觀察器設定檔</span><span class="sxs-lookup"><span data-stu-id="481e4-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="481e4-124">變更空間感知網格的顯示</span><span class="sxs-lookup"><span data-stu-id="481e4-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="481e4-125">根據預設，您無法編輯 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="481e4-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="481e4-126">這些是預設的設定檔範本，您必須先加以複製，才能進行編輯。</span><span class="sxs-lookup"><span data-stu-id="481e4-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="481e4-127">其中有數個巢狀的設定檔層。</span><span class="sxs-lookup"><span data-stu-id="481e4-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="481e4-128">因此，在設定一個或多個設定時，通常會複製及編輯數個設定檔。</span><span class="sxs-lookup"><span data-stu-id="481e4-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a><span data-ttu-id="481e4-129">恭喜！</span><span class="sxs-lookup"><span data-stu-id="481e4-129">Congratulations</span></span>

<span data-ttu-id="481e4-130">在本教學課程中，您已了解如何複製、自訂和設定 MRTK 設定檔和設定。</span><span class="sxs-lookup"><span data-stu-id="481e4-130">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="481e4-131">下一個教學課程：4.將物件置放在場景中</span><span class="sxs-lookup"><span data-stu-id="481e4-131">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)