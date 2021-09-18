---
title: 使用 BabylonJS 在 WebXR 中建立鋼琴
description: 完成此教學課程系列，以瞭解如何使用 BabylonJS 在 WebXR 中建立可運作的 88-key 鋼琴鍵盤
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: mixed reality、javascript、教學課程、BabylonJS、hololens、mixed reality、UWP、Windows 10、WebXR、沉浸式網路
ms.localizationpriority: high
ms.openlocfilehash: 93a3896b081e736bb62bceb6c8ae609685d7c5b5
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932487"
---
# <a name="tutorial-build-a-piano-in-webxr-using-babylonjs"></a>教學課程：使用 Babylon.js 在 WebXR 中建立鋼琴

在真實世界中打造鋼琴需要大量時間、技能和材質。 針對 VR/AR world 建立一個呢？

在本教學課程系列中，您將瞭解如何使用 Babylon.js 來建立混合的真實 web 應用程式，其中包含虛擬環境中運作的 88-關鍵站立會議鋼琴。 在完成的應用程式中，您將能夠使用您的混合現實控制器來傳送到鋼琴並播放按鍵。

在本教學課程系列中，您將瞭解如何：

> [!div class="checklist"]
> * 建立、定位及合併網格以建立鋼琴鍵盤
> * 匯入站立會議鋼琴框架的 Babylon.js 模型
> * 將指標互動新增至每個鋼琴按鍵
> * 在 WebXR 中啟用遙傳和 multipointer 支援

## <a name="prerequisites"></a>必要條件

* 連線到網際網路的電腦
* 基本 JAVAscript 知識
* [WebXR JAVAscript Hello World 教學課程](../babylonjs-webxr-helloworld/introduction-01.md)
* WebXR 支援的瀏覽器，例如[Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 或更高版本
* 任何[VR 耳機](../../../../discover/immersive-headset-hardware-details.md)或[Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)模擬器
* 選擇性：如果您想要使用 Windows Mixed Reality 模擬器， [Windows 10 建立者更新](https://www.microsoft.com/software-download/windows10)

## <a name="getting-started"></a>開始使用

讓我們從設定將包含 Babylon.js 場景的 HTML 網頁開始。

1. 建立名為 babylonjs 的資料夾 *-鋼琴-教學* 課程，並在 Visual Studio Code 中開啟資料夾。

    > [!NOTE]
    > 雖然您可以使用任何程式碼編輯器來進行，但為了方便起見，我們將在本教學課程中使用 Visual Studio Code。

1. 在資料夾內建立名為 *index.html* 的檔案，並將下列範本插入檔案中：

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas"); 
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
        
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

    如果您需要此範本內容的詳細說明，請參閱 [Hello World 教學](../babylonjs-webxr-helloworld/introduction-01.md)課程，這是本教學課程的先決條件。

1. 如果您嘗試在瀏覽器中開啟此檔案，主控台會顯示錯誤，指出 `createScene()` 找不到該函數。 讓我們在下一節中執行函數來解決這個錯誤 `createScene()` 。

## <a name="setup-the-scene"></a>設定場景

1. 在 *index.html* 的相同資料夾中，建立另一個名為 *scene.js* 的檔案。 我們會儲存與設定場景相關的所有 javascript 程式碼，並在此檔案中建立鋼琴。

1. 讓我們將 `createScene()` 函數新增至 *scene.js*：

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        return scene;
    }
    ```

    請注意，我們正在進行 `createScene()` 非同步函式。 請持續關注以找出原因。

1. 接下來，我們需要輕量和攝影機，讓我們可以看見場景。 更新 `createScene()` 函數：

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);

        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;

        return scene;
    }
    ```

    在這裡，我們建立了 [ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera)，它會指向幾乎最接近的位置，並以空間的原點為目標。 我們所建立的燈是指向天空的 [HemisphericLight](https://doc.babylonjs.com/divingDeeper/lights/lights_introduction#the-hemispheric-light) ，很適合用來模擬環境空間。 我們也會降低其濃度，稍微淺一點。

    如果您需要複習一下如何建立相機和燈光，請重新流覽 [Hello World 教學課程系列的「準備場景」一節](../babylonjs-webxr-helloworld/prepare-scene-02.md#add-a-camera) ，再繼續進行下一個步驟。

1. 最後，由於我們是針對 WebXR 平臺進行開發，因此我們必須在場景中插入下列行，以啟用場景中 [的 XR 體驗](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR) `return scene;` ：

    ```javascript
    const xrHelper = await scene.createDefaultXRExperienceAsync();
    ```

    在 javascript 中，若要在函 `await` 式內的函式上使用鍵盤 `async` ，父函式也必須是 `async` ，這也是我們先前定義 `createScene` 函數為 async 的原因。 稍後在本教學課程系列中，我們將使用它 `xrHelper` 來啟用和設定 Babylon.js 所支援的不同 WebXR 功能。

1. 完成的 *scene.js* 看起來應該像這樣：

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        
        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. 現在我們已經有運作正常的函式 `createScene()` ，讓我們 *index.html* 將 *scene.js* 檔案載入為腳本，以便 `createScene()` 在 *index.html* 中辨識函式。 在 html 檔案的區段內加入這行程式碼 `<header>` ：

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <script src="scene.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas");
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
                
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

1. 在您的瀏覽器中開啟 *index.html* ，您會發現我們先前看到的錯誤訊息不再存在，而且頁面中有空白的 Babylon.js 場景。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [下一個教學課程：建立3D 鋼琴模型](keyboard-model-02.md)
