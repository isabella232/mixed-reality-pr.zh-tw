---
title: Babylon.js 與3D 物件互動的教學課程
description: 瞭解如何使用 babylon.js 並與3D 物件互動。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality、javascript、教學課程、BabylonJS、hololens、mixed reality、UWP、Windows 10、WebXR、沉浸式網路
ms.localizationpriority: high
ms.openlocfilehash: 50c491a12b4c1c8e21a2c1fa1ae61e213370d276
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104946423"
---
# <a name="tutorial-interact-with-3d-object"></a>教學課程：與3D 物件互動

瞭解如何使用 babylon.js 建立與混合現實體驗的3D 物件和互動。 在本節中，您將從簡單的部分開始，例如在選取物件時繪製 cube 的臉部。

本教學課程涵蓋下列主題：

> [!div class="checklist"]
> * 如何新增互動
> * 啟用 WebXR 沉浸式模式
> * 在 Windows Mixed Reality 模擬器上執行應用程式
> * 在 Android Chrome 上執行和偵錯工具

## <a name="before-you-begin"></a>開始之前

在先前的教學課程步驟中，已建立一個具有場景的基本網頁。 讓裝載網頁開啟以供編輯。

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
        var canvas = document.getElementById("renderCanvas");
        var engine = new BABYLON.Engine(canvas, true);
        
        var createScene = function() {
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
        
        var sceneToRender = createScene();
        engine.runRenderLoop(function(){
            sceneToRender.render();
        });
    </script>
</body>
</html>
```

## <a name="add-interaction"></a>新增互動

1. 首先，讓我們更新建立 cube 的程式碼，以便使用隨機色彩來繪製 cube。 若要這樣做，我們會將 [材質](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) 新增至 cube。 材質可讓我們指定色彩和材質，也可以用來涵蓋其他物件。 材質的顯示方式取決於場景中使用的燈光或光線，以及它如何設定為回應。 例如，diffuseColor 會將色彩全部散佈在其所連接的網格上。 新增下列程式碼：

    ```javascript
    var boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. 現在 cube 以隨機色彩繪製，讓我們加入互動：

    * 變更按一下 cube 時的色彩
    * 變更色彩之後移動 cube

    若要加入互動，我們應該使用 [動作](https://doc.babylonjs.com/divingDeeper/events/actions)。 啟動動作以回應事件觸發程式。 例如，當使用者按一下 cube 時。 我們只需要將 BABYLON 具現化。ActionManager 並註冊特定觸發程式的動作。 當有人按一下 cube 時， [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) 會執行 JavaScript 函數：

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            var sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
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
            var canvas = document.getElementById("renderCanvas");
            var engine = new BABYLON.Engine(canvas, true);
            
            var createScene = function() {
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

                var boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        var sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

                return scene;
            };
            
            var sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

## <a name="enable-webxr-immersive-experience"></a>啟用 WebXR 沉浸式體驗

既然我們的 cube 正在變更色彩，我們就可以開始試用沉浸式體驗。

1. 在這個步驟中，我們將介紹一個 [基礎](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground)。 Cube 將在空氣中掛斷，我們會在底部看到樓層。 以下列方式加入地面：

    ```javascript
    var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    這會建立一個簡單的4x4 計量樓層。

1. 為了加入 WebXR 支援，我們必須呼叫 *createDefaultXRExperienceAsync*，其具有 *承諾* 結果。 將此程式碼新增至 *createScene* 函式的結尾，而不是傳回 *場景;*：

    ```javascript
    var xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
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
            var canvas = document.getElementById("renderCanvas");
            var engine = new BABYLON.Engine(canvas, true);
            
            var createScene = function() {
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

                var boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        var sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                var xrPromise = scene.createDefaultXRExperienceAsync({
                    floorMeshes: [ground]
                });
                
                return xrPromise.then((xrExperience) => {
                    console.log("Done, WebXR is enabled.");
                    return scene;
                });
            };
            
            createScene().then(sceneToRender => {
                engine.runRenderLoop(() => sceneToRender.render());
            });
        </script>
    </body>
    </html>
    ```

1. 上述程式碼會在瀏覽器視窗中產生下列輸出： ![ WebXR 場景](../images/hello-world-webxr-scene.png)

## <a name="run-on-a-windows-mixed-reality-simulator"></a>在 Windows Mixed Reality 模擬器上執行

1. 選取右下角的沉浸式-VR 按鈕： ![ 沉浸式 Vr 按鈕](../images/immersive-vr-button.png)

1. 此動作會啟動 Windows Mixed Reality 模擬器視窗，如下所示： ![ 混合實境入口](../images/mixed-reality-portal.png)

1. 您可以使用鍵盤上的 W、A、S 和 D 鍵，據以向前、向左和向右向前復原。 使用模擬手將目標設為 cube，然後按鍵盤上的 Enter 鍵以執行按一下動作。 Cube 會變更其色彩並移至新位置。

> [!NOTE]
> 以 cube 為目標時，請確定右邊的光線 (白色圓圈) 與 cube 交集，如上圖所示。 深入瞭解如何 [使用手上的 Point 和 commit](https://docs.microsoft.com/windows/mixed-reality/design/point-and-commit)。

## <a name="run-and-debug-on-android-device"></a>在 Android 裝置上執行和調試

請執行下列步驟，在您的 Android 裝置上啟用偵錯工具：

### <a name="prerequisites"></a>Prerequisites

* 在安全內容中提供靜態 html 網頁的 web 伺服器 (HTTPs://，或在開發電腦上的 localhost) 透過埠轉送來提供服務。 例如，利用 *服務* npm 套件作為靜態 html 檔案的簡易輕量 web 伺服器，檢查更多 [npm 服務](https://github.com/vercel/serve#readme)
* 最初隨 Google Play 商店出貨的裝置，必須執行 Android 7.0 或更新版本
* 開發工作站和裝置上的 [Google Chrome](https://support.google.com/chrome/answer/95346) 最新版本
* 若要確認裝置已正確設定為執行 WebXR，請流覽至裝置上的 [範例 WebXR 頁面](https://immersive-web.github.io/webxr-samples/) 。 您應該會看到如下的訊息：

    > 如果您有適當的硬體，您的瀏覽器支援 WebXR，而且可以執行虛擬實境和增強的現實體驗。

1. 在 Android 裝置上啟用開發人員模式和 USB 偵錯工具。 請參閱在官方檔頁面[上設定裝置開發人員選項](https://developer.android.com/studio/debug/dev-options)，以瞭解如何為您的 Android 版本進行這項操作
1. 接下來，透過 USB 纜線將 Android 裝置連接到您的開發電腦或膝上型電腦
1. 確定開發電腦上的網頁伺服器正在執行。 例如，流覽至包含您的 web 裝載頁面 (index.html) 的根資料夾，然後執行下列程式碼 (假設您使用服務 npm 套件) ：

    ```bash
    serve
    ```

1. 在您的開發電腦上開啟 Google Chrome，並在網址列中輸入下列文字：
    > chrome：//inspect # devices ![ CHROME USB 調試時間視窗](../images/chrome-usb-debug.png)
1. 確定已啟用 [ *探索 USB 裝置* ] 核取方塊
1. 按一下 [ *埠轉送* ] 按鈕，並確認 *埠轉送* 已啟用且包含 *localhost： 5000* 輸入，如下所示：  ![ Chrome 埠轉送視窗](../images/chrome-port-forwarding.png)
1. 在連線的 Android 裝置中，開啟 Google Chrome 視窗並流覽至 *http://localhost:5000* ，您應該會看到 cube
1. 在您的開發電腦上的 Chrome 中，您將會看到您的裝置，以及目前在該處開啟的網頁清單：  ![ Chrome 檢查視窗](../images/chrome-inspect.png)
1. 按一下專案旁的 [ *檢查* ] 按鈕 *http://localhost:5000* ：  ![ Chrome DevTools Debug 視窗](../images/chrome-debug.png)
1. 使用 [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) 來偵測頁面

## <a name="takeaways"></a>重要心得

以下是本教學課程中最重要的優點：
* Babylon.js 可讓您輕鬆地使用 JavaScript 建立沉浸式體驗
* 若要建立虛擬幕後，您不需要撰寫低層級的程式碼，或學習新的技術
* 您可以使用 WebXR 支援的瀏覽器來建立混合現實應用程式，而不需要購買耳機

## <a name="next-steps"></a>後續步驟

恭喜！ 您已完成一系列的 babylon.js 教學課程，並瞭解如何：
> [!div class="checklist"]
> * 設定開發環境
> * 建立新的網頁以顯示結果
> * 用來建立基本3D 元素並與其互動的 babylon.js API
> * 在 Windows Mixed Reality 模擬器中執行和測試應用程式

如需混合現實 JavaScript 開發的詳細資訊，請參閱 [javascript 開發總覽](/javascript-development-overview.md)。
