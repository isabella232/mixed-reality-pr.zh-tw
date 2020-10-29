---
title: 使用全像攝影 DirectX 應用程式中的 XAML
description: 說明在您的 DirectX 應用程式中切換 2D XAML 視圖與沉浸式視圖之間的影響，以及如何有效率地使用 XAML 視圖和沉浸式視圖。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: windows mixed reality、UWP、應用程式視圖管理、xaml、鍵盤、逐步解說、DirectX
ms.openlocfilehash: 4908ffbded879709c848a4d767c35a150aa3dfba
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679128"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="d5579-104">使用全像攝影 DirectX 應用程式中的 XAML</span><span class="sxs-lookup"><span data-stu-id="d5579-104">Using XAML with holographic DirectX apps</span></span>

> [!NOTE]
> <span data-ttu-id="d5579-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="d5579-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="d5579-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](../native/openxr-getting-started.md)** 。</span><span class="sxs-lookup"><span data-stu-id="d5579-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)** .</span></span>

<span data-ttu-id="d5579-107">本主題說明在 DirectX 應用程式中切換 [2D XAML 視圖與沉浸式視圖](../../design/app-views.md) 之間的影響，以及如何有效率地使用 XAML 視圖和沉浸式視圖。</span><span class="sxs-lookup"><span data-stu-id="d5579-107">This topic explains the impact of switching between [2D XAML views and immersive views](../../design/app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="d5579-108">XAML 視圖切換總覽</span><span class="sxs-lookup"><span data-stu-id="d5579-108">XAML view switching overview</span></span>

<span data-ttu-id="d5579-109">在 HoloLens 上，可在稍後顯示 2D XAML 視圖的一般沉浸式應用程式，必須先初始化該 XAML 視圖，並立即從該處切換到沉浸式視圖。</span><span class="sxs-lookup"><span data-stu-id="d5579-109">On HoloLens, a generally immersive app that may later display a 2D XAML view must initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="d5579-110">這表示在您的應用程式可以進行任何動作之前，會先載入 XAML。</span><span class="sxs-lookup"><span data-stu-id="d5579-110">This means XAML will load before your app can do anything.</span></span> <span data-ttu-id="d5579-111">如此一來，您的啟動時間就會稍微增加，而且當應用程式位於背景時，XAML 將繼續佔用您應用程式進程中的記憶體空間;啟動延遲和記憶體使用量的數量，取決於您的應用程式在切換至原生視圖之前的 XAML 用途。</span><span class="sxs-lookup"><span data-stu-id="d5579-111">As a result, there will be a small increase in your startup time, and XAML will continue to occupy memory space in your app process while it resides in the background; the amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="d5579-112">如果您在第一次的 XAML 啟動程式碼中沒有執行任何動作，但開始您的沉浸式觀賞，則影回應該會很小。</span><span class="sxs-lookup"><span data-stu-id="d5579-112">If you do nothing in your XAML start up code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="d5579-113">此外，由於您的全像轉譯是直接在沉浸式觀賞中完成，因此您可以避免對該轉譯產生任何與 XAML 相關的限制。</span><span class="sxs-lookup"><span data-stu-id="d5579-113">Also, because your holographic rendering is done directly to the immersive view, you will avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="d5579-114">請注意，CPU 和 GPU 的記憶體使用量會計算。</span><span class="sxs-lookup"><span data-stu-id="d5579-114">Note that the memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="d5579-115">Direct3D 11 可以交換虛擬圖形記憶體，但它可能無法交換部分或所有的 XAML GPU 資源，而且可能會有明顯的效能衝擊。</span><span class="sxs-lookup"><span data-stu-id="d5579-115">Direct3D 11 is able to swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="d5579-116">無論何種方式，您都不需要載入任何 XAML 功能，也不需要載入更多應用程式的空間，並提供更好的體驗。</span><span class="sxs-lookup"><span data-stu-id="d5579-116">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="d5579-117">XAML 視圖切換工作流程</span><span class="sxs-lookup"><span data-stu-id="d5579-117">XAML view switching workflow</span></span>

<span data-ttu-id="d5579-118">從 XAML 直接進入沉浸式模式的應用程式工作流程，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d5579-118">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="d5579-119">應用程式會在 2D XAML 視圖中啟動。</span><span class="sxs-lookup"><span data-stu-id="d5579-119">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="d5579-120">應用程式的 XAML 啟動順序會偵測目前的系統是否支援全像轉譯：</span><span class="sxs-lookup"><span data-stu-id="d5579-120">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="d5579-121">如果是，應用程式會建立沉浸式視圖，並立即將它帶到前景。</span><span class="sxs-lookup"><span data-stu-id="d5579-121">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="d5579-122">在 Windows Mixed Reality 裝置上不需要的任何動作都會略過 XAML 載入，包括 XAML 視圖中的任何轉譯類別和資產載入。</span><span class="sxs-lookup"><span data-stu-id="d5579-122">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="d5579-123">如果應用程式使用 XAML 進行鍵盤輸入，則仍應建立該輸入頁面。</span><span class="sxs-lookup"><span data-stu-id="d5579-123">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="d5579-124">如果沒有，XAML view 可以像往常一樣繼續進行商務作業。</span><span class="sxs-lookup"><span data-stu-id="d5579-124">If not, the XAML view can proceed with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="d5579-125">跨兩個視圖呈現圖形的秘訣</span><span class="sxs-lookup"><span data-stu-id="d5579-125">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="d5579-126">如果您的應用程式需要針對 Windows Mixed Reality 中的 XAML 視圖在 DirectX 中執行某種程度的轉譯，最好的做法是建立一個可同時使用兩個視圖的轉譯器。</span><span class="sxs-lookup"><span data-stu-id="d5579-126">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="d5579-127">轉譯器應該是一個可從這兩個視圖存取的實例，而且應該能夠在2D 和全像攝影轉譯之間切換。</span><span class="sxs-lookup"><span data-stu-id="d5579-127">The renderer should be one instance that can be accessed from both views, and it should be able to switch between 2D and holographic rendering.</span></span> <span data-ttu-id="d5579-128">如此一來，GPU 資產只會載入一次-這可減少載入時間、記憶體影響，以及切換視圖時要交換的資源數量。</span><span class="sxs-lookup"><span data-stu-id="d5579-128">That way GPU assets are only loaded once - this reduces load times, memory impact, and the amount of resources to be swapped when switching views.</span></span>
