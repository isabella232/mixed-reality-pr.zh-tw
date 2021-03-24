---
title: babylon.js 和 WebXR 教學課程簡介
description: 完成本課程，以瞭解如何使用 babylon.js 並建立基本的混合現實應用程式。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality、javascript、教學課程、BabylonJS、hololens、mixed reality、UWP、Windows 10、WebXR、沉浸式網路
ms.localizationpriority: high
ms.openlocfilehash: 945d27d13ac731447bd20e93805900605bc86f43
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104946420"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="3ccf0-104">教學課程：使用 babylon.js 建立您的第一個 WebXR 應用程式</span><span class="sxs-lookup"><span data-stu-id="3ccf0-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="3ccf0-105">本教學課程將說明如何使用 babylon.js 和 Visual Studio Code 來建立基本的混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="3ccf0-106">您要建立的應用程式將會轉譯 cube，讓您可以旋轉以將其他臉部移至視野，並加入互動。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="3ccf0-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="3ccf0-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3ccf0-108">設定開發環境</span><span class="sxs-lookup"><span data-stu-id="3ccf0-108">Set up a development environment</span></span>
> * <span data-ttu-id="3ccf0-109">用來建立基本3D 元素的 babylon.js API</span><span class="sxs-lookup"><span data-stu-id="3ccf0-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="3ccf0-110">建立新的網頁</span><span class="sxs-lookup"><span data-stu-id="3ccf0-110">Create a new web page</span></span>
> * <span data-ttu-id="3ccf0-111">與3D 元素互動</span><span class="sxs-lookup"><span data-stu-id="3ccf0-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="3ccf0-112">在 Windows Mixed Reality 模擬器中執行應用程式</span><span class="sxs-lookup"><span data-stu-id="3ccf0-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3ccf0-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3ccf0-113">Prerequisites</span></span>

* <span data-ttu-id="3ccf0-114">WebXR 支援的瀏覽器，例如 [Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/whats-new/new-microsoft-edge)</span><span class="sxs-lookup"><span data-stu-id="3ccf0-114">WebXR-supported browser, for example [Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/whats-new/new-microsoft-edge)</span></span>
* <span data-ttu-id="3ccf0-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="3ccf0-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="3ccf0-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="3ccf0-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="3ccf0-117">選擇性：如果您想要使用 Windows Mixed Reality 模擬器， [Windows 10 建立者更新](https://www.microsoft.com/software-download/windows10)</span><span class="sxs-lookup"><span data-stu-id="3ccf0-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="3ccf0-118">選用： [Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)模擬器</span><span class="sxs-lookup"><span data-stu-id="3ccf0-118">Optional: [Windows Mixed Reality simulator](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)</span></span>

## <a name="getting-started"></a><span data-ttu-id="3ccf0-119">開始使用</span><span class="sxs-lookup"><span data-stu-id="3ccf0-119">Getting started</span></span>

<span data-ttu-id="3ccf0-120">若要從頭開始建立此專案，請從 Visual Studio Code (VSCode) 專案開始。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="3ccf0-121">使用 VSCode 並非必要，但我們將在整個教學課程中使用它來方便使用。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="3ccf0-122">更有經驗的 JavaScript 開發人員可以使用他們選擇的任何其他編輯器，甚至是最簡單的 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="3ccf0-123">請下載 [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 單一檔案，或使用可在 [官方 babylon.js 網站](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers)上找到的線上版本。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="3ccf0-124">您也可以從[GitHub](https://github.com/BabylonJS/Babylon.js)複製整個 babylon.js 專案</span><span class="sxs-lookup"><span data-stu-id="3ccf0-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="3ccf0-125">建立空的檔案，並將它儲存為 html 網頁，例如 index.html</span><span class="sxs-lookup"><span data-stu-id="3ccf0-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="3ccf0-126">建立基本的 html 標記，並參考 babylon.js 的 javascript 檔案。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="3ccf0-127">最後的程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="3ccf0-127">The final code is as shown below:</span></span>

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. <span data-ttu-id="3ccf0-128">在主體內新增 *canvas* HTML 元素，以轉譯 babylon.js 的內容。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="3ccf0-129">請注意，畫布具有 id 屬性，可讓您稍後從 JavaScript 存取這個 HTML 元素。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
    <body>
        <canvas id="renderCanvas"></canvas>
    </body>
    </html>
    ```

1. <span data-ttu-id="3ccf0-130">畫布佔用整個網頁。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="3ccf0-131">這會完成我們的網頁。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-131">That completes our web page.</span></span> <span data-ttu-id="3ccf0-132">到目前為止，網頁已準備就緒。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-132">At this point, the web page is ready.</span></span> <span data-ttu-id="3ccf0-133">您可以在任何瀏覽器中開啟它，並確保不會顯示任何錯誤，但沒有任何沉浸式體驗。</span><span class="sxs-lookup"><span data-stu-id="3ccf0-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3ccf0-134">下一步</span><span class="sxs-lookup"><span data-stu-id="3ccf0-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3ccf0-135">下一個教學課程： 2. 準備場景</span><span class="sxs-lookup"><span data-stu-id="3ccf0-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)
