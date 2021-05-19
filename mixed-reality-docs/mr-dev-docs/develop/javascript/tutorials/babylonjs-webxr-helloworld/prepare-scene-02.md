---
title: 使用基本3D 物件準備場景的 Babylon.js 教學課程
description: 瞭解如何使用 babylon.js，並將基本的3D 物件加入場景。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality、javascript、教學課程、BabylonJS、hololens、mixed reality、UWP、Windows 10、WebXR、沉浸式網路
ms.localizationpriority: high
ms.openlocfilehash: 963589cb221b7dba1c197fff06ccb8926e12f89c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143686"
---
# <a name="tutorial-prepare-a-scene"></a>教學課程：準備場景

瞭解如何準備場景，並在其中新增一些基本的3D 元素。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
> * 建立場景
> * 新增相機
> * 新增燈光
> * 新增基本3D 元素

## <a name="before-you-begin"></a>開始之前

在先前的教學課程步驟中，已建立基本的網頁。 開啟網頁進行編輯。

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

## <a name="create-a-scene"></a>建立場景

場景是所有內容將會顯示的位置。 可能有多個場景，而且可以在幕後切換。 閱讀 [babylon.js 場景](https://doc.babylonjs.com/divingDeeper/scene)的詳細資訊。

1. 將腳本標記新增至 canvas html 專案之後，然後加入下列程式碼來建立填滿黑色色彩的場景：

    ```html
    <script type="text/javascript">
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        const sceneToRender = createScene();
    </script>
    ```

    在上述程式碼中，我們必須建立 babylon.js web 轉譯引擎的實例，以轉譯場景並在畫布上攔截事件。 如需有關引擎的詳細資訊，請參閱檔頁面 [babylon。](https://doc.babylonjs.com/typedoc/classes/babylon.engine)

1. 預設不會呈現場景。 請記住，可能有多個場景，您可以控制要顯示的場景。 若要在每個畫面上重複呈現場景，請在呼叫 *createScene* 函式之後執行下列程式碼：

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>新增基本3D 元素

1. 讓我們加入第一個3D 圖形。 在3D 虛擬世界中，圖形是由 *網格* 所建立，而多個三角形 facet 聯結在一起，每個面向都是從三個頂點所建立。 您可以使用預先定義的網格或建立您自己的自訂網格。 在這裡，我們將使用預先定義的方塊網格，亦即 cube。 若要建立 box，請使用 [BABYLON。MeshBuilder. CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box)。 這些參數是名稱，而選項 (選項會根據網格) 的類型而有所不同。 將下列程式碼附加至函數 *createScene*：

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. 在 Microsoft Edge 瀏覽器中開啟網頁，並檢查輸出。 瀏覽器視窗會顯示空白頁面。 使用鍵盤開啟 DevTools，然後選取 F12 或 Ctrl + Shift + I (Windows、Linux) 或命令 + 選項 + I (macOS) 。 開啟 [ *主控台* ] 索引標籤之後，您就可以開始尋找錯誤。 將會顯示錯誤：「未攔截的錯誤：未定義相機」。 現在，我們必須將攝影機加入場景中。

## <a name="add-a-camera"></a>新增相機

1. 若要允許使用者輸入，相機必須附加至畫布。 讓我們新增 BABYLON 類型的相機 [。ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) 可讓我們四處查看，也就是可以旋轉我們剛才新增至場景的物件。 建立相機實例所需的參數是 longitudinal 軸的名稱、Alpha (旋轉) 、沿著 latitudinal 軸的 Beta (旋轉) 、半徑 (距離目標) 的距離，以及相機應查看 (的目標目標) 。 將下列程式碼新增至 *createScene* 函式：

    ```javascript
    const alpha =  Math.PI;
    const beta = Math.PI;
    const radius = 5;
    
    const camera = new BABYLON.ArcRotateCamera("Camera", 0, 0, 0);
    camera.setPosition(new BABYLON.Vector3(alpha, beta, radius));
    camera.attachControl(canvas, true);
    ```

1. 如果您在瀏覽器中檢查輸出，將會看到黑色的畫布。 我們遺漏了燈光。

## <a name="add-light"></a>新增燈光

1. 有四種類型的燈光可搭配燈光屬性範圍使用：點、方向、點和 Hemispheric 淺色。 讓我們新增環境光源 [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight)，如下所示：

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. 網頁的最後一個程式碼看起來會如下所示：

    ```html
    <html>
    <head>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    <body>
        <canvas id="renderCanvas"></canvas>
        <script>
            const canvas = document.getElementById("renderCanvas");
            const engine = new BABYLON.Engine(canvas, true);
            
            const createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI;
                const beta = Math.PI;
                const radius = 5;
                
                const camera = new BABYLON.ArcRotateCamera("Camera", 0, 0, 0);
                camera.setPosition(new BABYLON.Vector3(alpha, beta, radius));
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            const sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. 檢查瀏覽器中的輸出。 您應該會看到 cube，並使用滑鼠來旋轉立方體周圍的相機，並查看 cube 的不同臉部：

![具有 cube 的基本場景](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [下一個教學課程： 3. 與3D 物件互動](interact-03.md)
