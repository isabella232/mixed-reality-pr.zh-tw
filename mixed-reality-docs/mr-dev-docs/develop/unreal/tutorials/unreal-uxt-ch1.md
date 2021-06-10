---
title: 1. 開始使用
description: 教學課程系列的第 1 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: efa0bc210fc20b9e639954a06e97eb78661d87e5
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712577"
---
# <a name="1-getting-started"></a><span data-ttu-id="c4873-104">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="c4873-104">1. Getting started</span></span>

<span data-ttu-id="c4873-105">無論您是混合實境的新手還是經驗豐富的專業人員，都可以從此處開始體驗 [HoloLens 2](../../../index.yml) 和 [Unreal Engine](https://www.unrealengine.com/en-US/)。</span><span class="sxs-lookup"><span data-stu-id="c4873-105">Whether you're new to mixed reality or a seasoned pro, you're in the right place to start your [HoloLens 2](../../../index.yml) and [Unreal Engine](https://www.unrealengine.com/en-US/) journey.</span></span> <span data-ttu-id="c4873-106">本教學課程系列將提供逐步指南，說明如何使用 [UX 工具外掛程式](https://github.com/microsoft/MixedReality-UXTools-Unreal)建立互動式的國際象棋應用程式 - 這是[適用於 Unreal 的混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unreal)的一部分。</span><span class="sxs-lookup"><span data-stu-id="c4873-106">This tutorial series will give you a step-by-step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="c4873-107">此外掛程式可協助您使用程式碼、藍圖和範例，將常用的 UX 功能新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="c4873-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![檢視區中的最終場景](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="c4873-109">在系列結束時，您將擁有以下方面的體驗：</span><span class="sxs-lookup"><span data-stu-id="c4873-109">By the end of the series you'll have experience with:</span></span>
* <span data-ttu-id="c4873-110">開始新專案</span><span class="sxs-lookup"><span data-stu-id="c4873-110">Starting a new project</span></span>
* <span data-ttu-id="c4873-111">設定混合實境</span><span class="sxs-lookup"><span data-stu-id="c4873-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="c4873-112">處理使用者輸入</span><span class="sxs-lookup"><span data-stu-id="c4873-112">Working with user input</span></span>
* <span data-ttu-id="c4873-113">新增按鈕</span><span class="sxs-lookup"><span data-stu-id="c4873-113">Adding buttons</span></span>
* <span data-ttu-id="c4873-114">在模擬器或裝置上播放</span><span class="sxs-lookup"><span data-stu-id="c4873-114">Playing on an emulator or device</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c4873-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="c4873-115">Prerequisites</span></span>

<span data-ttu-id="c4873-116">在進行之前，請確定您已安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="c4873-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="c4873-117">Windows 10 1809 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c4873-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="c4873-118">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c4873-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="c4873-119">[Unreal 引擎](https://www.unrealengine.com/en-US/get-now) 4.26 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c4873-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.26 or later</span></span>
* <span data-ttu-id="c4873-120">[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 Microsoft HoloLens 2 裝置或[模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)</span><span class="sxs-lookup"><span data-stu-id="c4873-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or [Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)</span></span>
* <span data-ttu-id="c4873-121">Visual Studio 2019 與下列工作負載</span><span class="sxs-lookup"><span data-stu-id="c4873-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="c4873-122">安裝 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="c4873-122">Installing Visual Studio 2019</span></span>

<span data-ttu-id="c4873-123">首先，請確定您的設定具有所有必要的 Visual Studio 套件：</span><span class="sxs-lookup"><span data-stu-id="c4873-123">First, make sure your setup with all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="c4873-124">安裝最新版 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="c4873-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
1. <span data-ttu-id="c4873-125">安裝下列[工作負載](/visualstudio/install/modify-visual-studio#modify-workloads)：</span><span class="sxs-lookup"><span data-stu-id="c4873-125">Install the following [workloads](/visualstudio/install/modify-visual-studio#modify-workloads):</span></span>
    * <span data-ttu-id="c4873-126">使用 C++ 的傳統型開發</span><span class="sxs-lookup"><span data-stu-id="c4873-126">Desktop development with C++</span></span>
    * <span data-ttu-id="c4873-127">.NET 桌面開發</span><span class="sxs-lookup"><span data-stu-id="c4873-127">.NET desktop development</span></span>
    * <span data-ttu-id="c4873-128">通用 Windows 平台開發</span><span class="sxs-lookup"><span data-stu-id="c4873-128">Universal Windows Platform development</span></span>
1. <span data-ttu-id="c4873-129">展開「通用 Windows 平台開發」，然後選取：</span><span class="sxs-lookup"><span data-stu-id="c4873-129">Expand Universal Windows Platform development and select:</span></span> 
    * <span data-ttu-id="c4873-130">USB 裝置連線</span><span class="sxs-lookup"><span data-stu-id="c4873-130">USB Device Connectivity</span></span>
    * <span data-ttu-id="c4873-131">C++ (v142) 通用 Windows 平台工具</span><span class="sxs-lookup"><span data-stu-id="c4873-131">C++ (v142) Universal Windows Platform tools</span></span>

1. <span data-ttu-id="c4873-132">安裝下列[元件](/visualstudio/install/modify-visual-studio#modify-individual-components)：</span><span class="sxs-lookup"><span data-stu-id="c4873-132">Install the following [components](/visualstudio/install/modify-visual-studio#modify-individual-components):</span></span>
    * <span data-ttu-id="c4873-133">編譯器、建置工具與執行階段 > MSVC v142 - VS 2019 C++ ARM64 建置工具 (最新版本)</span><span class="sxs-lookup"><span data-stu-id="c4873-133">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="c4873-134">您可以使用下列圖片來確認安裝</span><span class="sxs-lookup"><span data-stu-id="c4873-134">You can confirm the installation with the following picture</span></span>

![VS 安裝程式中的重要刻度](images/unreal-uxt/1-install-the-tools.png)

<span data-ttu-id="c4873-136">這樣就完成了！</span><span class="sxs-lookup"><span data-stu-id="c4873-136">That's it!</span></span> <span data-ttu-id="c4873-137">您已準備好繼續著手進行國際象棋專案。</span><span class="sxs-lookup"><span data-stu-id="c4873-137">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="c4873-138">下一節：2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="c4873-138">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)