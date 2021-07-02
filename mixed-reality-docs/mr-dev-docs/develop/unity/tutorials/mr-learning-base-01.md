---
title: MRTK 教學課程簡介
description: 本課程說明如何使用混合實境工具組 (MRTK) 從頭建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, 解算器, 眼球追蹤, 語音命令
ms.localizationpriority: high
ms.openlocfilehash: abee2163c3b92897396ea35cc43ae025e8e7b804
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175495"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="2ac56-104">1.MRTK 教學課程簡介</span><span class="sxs-lookup"><span data-stu-id="2ac56-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="2ac56-105">歡迎使用入門教學課程系列！</span><span class="sxs-lookup"><span data-stu-id="2ac56-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="2ac56-106">在這些教學課程中，您將了解混合實境工具組 (MRTK) 及其所提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="2ac56-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="2ac56-107">您也會建立一個混合實境體驗，讓使用者可以探索模仿 NASA Mars Curiosity Rover (好奇號火星探測車) 的全像投影。</span><span class="sxs-lookup"><span data-stu-id="2ac56-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="2ac56-108">在此系列結束時，您將完全了解 MRTK，以及其如何加速您的開發流程。</span><span class="sxs-lookup"><span data-stu-id="2ac56-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="2ac56-109">此系列中的教學課程都是連續的，因此請以正確的順序逐一查看：</span><span class="sxs-lookup"><span data-stu-id="2ac56-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="2ac56-110">[簡介](mr-learning-base-01.md) (您正在此教學課程中)</span><span class="sxs-lookup"><span data-stu-id="2ac56-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="2ac56-111">初始化您的專案並部署您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="2ac56-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="2ac56-112">設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="2ac56-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="2ac56-113">將物件置放在場景中</span><span class="sxs-lookup"><span data-stu-id="2ac56-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="2ac56-114">使用解析器建立動態內容</span><span class="sxs-lookup"><span data-stu-id="2ac56-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="2ac56-115">建立使用者介面</span><span class="sxs-lookup"><span data-stu-id="2ac56-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="2ac56-116">與 3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="2ac56-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="2ac56-117">使用眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="2ac56-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="2ac56-118">使用語音命令</span><span class="sxs-lookup"><span data-stu-id="2ac56-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="2ac56-119">目標</span><span class="sxs-lookup"><span data-stu-id="2ac56-119">Objectives</span></span>

* <span data-ttu-id="2ac56-120">了解如何為 MRTK 設定 Unity</span><span class="sxs-lookup"><span data-stu-id="2ac56-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="2ac56-121">了解如何在您的裝置上建置和部署</span><span class="sxs-lookup"><span data-stu-id="2ac56-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="2ac56-122">了解如何使用 MRTK 的重要功能</span><span class="sxs-lookup"><span data-stu-id="2ac56-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="2ac56-123">建立完整的混合實境體驗</span><span class="sxs-lookup"><span data-stu-id="2ac56-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ac56-124">必要條件</span><span class="sxs-lookup"><span data-stu-id="2ac56-124">Prerequisites</span></span>

* <span data-ttu-id="2ac56-125">已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="2ac56-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="2ac56-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="2ac56-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="2ac56-127">已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="2ac56-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="2ac56-128">Unity <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">中樞</a>已安裝 UNITY 2020.3 LTS 或 UNITY 2019.4 LTS (**OpenXR 需要2020.3.8 或更新版本，以防止錯誤**) </span><span class="sxs-lookup"><span data-stu-id="2ac56-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020.3 LTS or Unity 2019.4 LTS installed (**OpenXR requires 2020.3.8 or later to prevent bugs**)</span></span>

<span data-ttu-id="2ac56-129">安裝 Unity 時，請務必檢查「 **平臺**」底下的下列元件。</span><span class="sxs-lookup"><span data-stu-id="2ac56-129">When installing Unity, please make sure to check following components under **'Platforms'**.</span></span>

* <span data-ttu-id="2ac56-130">**通用 Windows 平臺組建支援**</span><span class="sxs-lookup"><span data-stu-id="2ac56-130">**Universal Windows Platform Build Support**</span></span>
* <span data-ttu-id="2ac56-131">**Windows組建支援 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="2ac56-131">**Windows Build Support (IL2CPP)**</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

<span data-ttu-id="2ac56-132">如果您已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項。</span><span class="sxs-lookup"><span data-stu-id="2ac56-132">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub.</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> <span data-ttu-id="2ac56-133">本教學課程系列的建議 MRTK 版本為 MRTK 2.7。2</span><span class="sxs-lookup"><span data-stu-id="2ac56-133">The recommended MRTK version for this tutorial series is MRTK 2.7.2</span></span>

> [!Important]
> <span data-ttu-id="2ac56-134">此教學課程系列支援 Unity 2020 LTS (目前的 2020.3) 如果您使用 Open XR 或 Windows XR 外掛程式，以及 unity 2019 LTS (目前 2019.4. x) 如果您使用舊版的 WSA 或 Windows XR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="2ac56-134">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="2ac56-135">這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求。</span><span class="sxs-lookup"><span data-stu-id="2ac56-135">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ac56-136">下一個教學課程：2.初始化您的專案並部署您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="2ac56-136">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
