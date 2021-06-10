---
title: babylon.js 和 WebXR 教學課程簡介
description: 完成本課程，以瞭解如何使用 babylon.js 並建立基本的混合現實應用程式。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality、javascript、教學課程、BabylonJS、hololens、mixed reality、UWP、Windows 10、WebXR、沉浸式網路
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600117"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>教學課程：使用 babylon.js 建立您的第一個 WebXR 應用程式

本教學課程將說明如何使用 babylon.js 和 Visual Studio Code 來建立基本的混合現實應用程式。 您要建立的應用程式將會轉譯 cube，讓您可以旋轉以將其他臉部移至視野，並加入互動。 在本教學課程中，您會了解如何：

> [!div class="checklist"]
> * 設定開發環境
> * 用來建立基本3D 元素的 babylon.js API  
> * 建立新的網頁
> * 與3D 元素互動
> * 在 Windows Mixed Reality 模擬器中執行應用程式

## <a name="prerequisites"></a>必要條件

* WebXR 支援的瀏覽器，例如 [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 或更高版本
* [NodeJS](https://nodejs.org/)
* 選擇性：如果您想要使用 Windows Mixed Reality 模擬器， [Windows 10 建立者更新](https://www.microsoft.com/software-download/windows10)
* 選用： [Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)模擬器

## <a name="getting-started"></a>使用者入門

若要從頭開始建立此專案，請從 Visual Studio Code (VSCode) 專案開始。

> [!NOTE]
> 使用 VSCode 並非必要，但我們將在整個教學課程中使用它來方便使用。 更有經驗的 JavaScript 開發人員可以使用他們選擇的任何其他編輯器，甚至是最簡單的 [記事本]。

1. 請下載 [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 單一檔案，或使用可在 [官方 babylon.js 網站](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers)上找到的線上版本。 您也可以從[GitHub](https://github.com/BabylonJS/Babylon.js)複製整個 babylon.js 專案
1. 建立空的檔案，並將它儲存為 html 網頁，例如 index.html
1. 建立基本的 html 標記，並參考 babylon.js 的 javascript 檔案。 最後的程式碼如下所示：

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

1. 在主體內新增 *canvas* HTML 元素，以轉譯 babylon.js 的內容。 請注意，畫布具有 id 屬性，可讓您稍後從 JavaScript 存取這個 HTML 元素。

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

1. 畫布佔用整個網頁。 這會完成我們的網頁。 到目前為止，網頁已準備就緒。 您可以在任何瀏覽器中開啟它，並確保不會顯示任何錯誤，但沒有任何沉浸式體驗。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [下一個教學課程： 2. 準備場景](prepare-scene-02.md)