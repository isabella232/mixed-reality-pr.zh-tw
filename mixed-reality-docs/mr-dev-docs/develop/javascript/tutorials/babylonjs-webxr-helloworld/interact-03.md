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
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="d252c-104">教學課程：與3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="d252c-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="d252c-105">瞭解如何使用 babylon.js 建立與混合現實體驗的3D 物件和互動。</span><span class="sxs-lookup"><span data-stu-id="d252c-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="d252c-106">在本節中，您將從簡單的部分開始，例如在選取物件時繪製 cube 的臉部。</span><span class="sxs-lookup"><span data-stu-id="d252c-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="d252c-107">本教學課程涵蓋下列主題：</span><span class="sxs-lookup"><span data-stu-id="d252c-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="d252c-108">如何新增互動</span><span class="sxs-lookup"><span data-stu-id="d252c-108">How to add interactions</span></span>
> * <span data-ttu-id="d252c-109">啟用 WebXR 沉浸式模式</span><span class="sxs-lookup"><span data-stu-id="d252c-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="d252c-110">在 Windows Mixed Reality 模擬器上執行應用程式</span><span class="sxs-lookup"><span data-stu-id="d252c-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="d252c-111">在 Android Chrome 上執行和偵錯工具</span><span class="sxs-lookup"><span data-stu-id="d252c-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d252c-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="d252c-112">Before you begin</span></span>

<span data-ttu-id="d252c-113">在先前的教學課程步驟中，已建立一個具有場景的基本網頁。</span><span class="sxs-lookup"><span data-stu-id="d252c-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="d252c-114">讓裝載網頁開啟以供編輯。</span><span class="sxs-lookup"><span data-stu-id="d252c-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="d252c-115">新增互動</span><span class="sxs-lookup"><span data-stu-id="d252c-115">Add interaction</span></span>

1. <span data-ttu-id="d252c-116">首先，讓我們更新建立 cube 的程式碼，以便使用隨機色彩來繪製 cube。</span><span class="sxs-lookup"><span data-stu-id="d252c-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="d252c-117">若要這樣做，我們會將 [材質](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) 新增至 cube。</span><span class="sxs-lookup"><span data-stu-id="d252c-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="d252c-118">材質可讓我們指定色彩和材質，也可以用來涵蓋其他物件。</span><span class="sxs-lookup"><span data-stu-id="d252c-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="d252c-119">材質的顯示方式取決於場景中使用的燈光或光線，以及它如何設定為回應。</span><span class="sxs-lookup"><span data-stu-id="d252c-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="d252c-120">例如，diffuseColor 會將色彩全部散佈在其所連接的網格上。</span><span class="sxs-lookup"><span data-stu-id="d252c-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="d252c-121">新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d252c-121">Add the following code:</span></span>

    ```javascript
    var boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="d252c-122">現在 cube 以隨機色彩繪製，讓我們加入互動：</span><span class="sxs-lookup"><span data-stu-id="d252c-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="d252c-123">變更按一下 cube 時的色彩</span><span class="sxs-lookup"><span data-stu-id="d252c-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="d252c-124">變更色彩之後移動 cube</span><span class="sxs-lookup"><span data-stu-id="d252c-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="d252c-125">若要加入互動，我們應該使用 [動作](https://doc.babylonjs.com/divingDeeper/events/actions)。</span><span class="sxs-lookup"><span data-stu-id="d252c-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="d252c-126">啟動動作以回應事件觸發程式。</span><span class="sxs-lookup"><span data-stu-id="d252c-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="d252c-127">例如，當使用者按一下 cube 時。</span><span class="sxs-lookup"><span data-stu-id="d252c-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="d252c-128">我們只需要將 BABYLON 具現化。ActionManager 並註冊特定觸發程式的動作。</span><span class="sxs-lookup"><span data-stu-id="d252c-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="d252c-129">當有人按一下 cube 時， [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) 會執行 JavaScript 函數：</span><span class="sxs-lookup"><span data-stu-id="d252c-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

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

1. <span data-ttu-id="d252c-130">網頁的最後一個程式碼看起來會如下所示：</span><span class="sxs-lookup"><span data-stu-id="d252c-130">The final code of the web page will look as follows:</span></span>

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="d252c-131">啟用 WebXR 沉浸式體驗</span><span class="sxs-lookup"><span data-stu-id="d252c-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="d252c-132">既然我們的 cube 正在變更色彩，我們就可以開始試用沉浸式體驗。</span><span class="sxs-lookup"><span data-stu-id="d252c-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="d252c-133">在這個步驟中，我們將介紹一個 [基礎](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground)。</span><span class="sxs-lookup"><span data-stu-id="d252c-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="d252c-134">Cube 將在空氣中掛斷，我們會在底部看到樓層。</span><span class="sxs-lookup"><span data-stu-id="d252c-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="d252c-135">以下列方式加入地面：</span><span class="sxs-lookup"><span data-stu-id="d252c-135">Add the ground as follows:</span></span>

    ```javascript
    var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="d252c-136">這會建立一個簡單的4x4 計量樓層。</span><span class="sxs-lookup"><span data-stu-id="d252c-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="d252c-137">為了加入 WebXR 支援，我們必須呼叫 *createDefaultXRExperienceAsync*，其具有 *承諾* 結果。</span><span class="sxs-lookup"><span data-stu-id="d252c-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="d252c-138">將此程式碼新增至 *createScene* 函式的結尾，而不是傳回 *場景;*：</span><span class="sxs-lookup"><span data-stu-id="d252c-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    var xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="d252c-139">網頁的最後一個程式碼看起來會如下所示：</span><span class="sxs-lookup"><span data-stu-id="d252c-139">The final code of the web page will look as follows:</span></span>

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

1. <span data-ttu-id="d252c-140">上述程式碼會在瀏覽器視窗中產生下列輸出： ![ WebXR 場景](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="d252c-140">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="d252c-141">在 Windows Mixed Reality 模擬器上執行</span><span class="sxs-lookup"><span data-stu-id="d252c-141">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="d252c-142">選取右下角的沉浸式-VR 按鈕： ![ 沉浸式 Vr 按鈕](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="d252c-142">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="d252c-143">此動作會啟動 Windows Mixed Reality 模擬器視窗，如下所示： ![ 混合實境入口](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="d252c-143">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="d252c-144">您可以使用鍵盤上的 W、A、S 和 D 鍵，據以向前、向左和向右向前復原。</span><span class="sxs-lookup"><span data-stu-id="d252c-144">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="d252c-145">使用模擬手將目標設為 cube，然後按鍵盤上的 Enter 鍵以執行按一下動作。</span><span class="sxs-lookup"><span data-stu-id="d252c-145">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="d252c-146">Cube 會變更其色彩並移至新位置。</span><span class="sxs-lookup"><span data-stu-id="d252c-146">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="d252c-147">以 cube 為目標時，請確定右邊的光線 (白色圓圈) 與 cube 交集，如上圖所示。</span><span class="sxs-lookup"><span data-stu-id="d252c-147">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="d252c-148">深入瞭解如何 [使用手上的 Point 和 commit](https://docs.microsoft.com/windows/mixed-reality/design/point-and-commit)。</span><span class="sxs-lookup"><span data-stu-id="d252c-148">Learn more about [Point and commit with hands](https://docs.microsoft.com/windows/mixed-reality/design/point-and-commit).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="d252c-149">在 Android 裝置上執行和調試</span><span class="sxs-lookup"><span data-stu-id="d252c-149">Run and debug on Android device</span></span>

<span data-ttu-id="d252c-150">請執行下列步驟，在您的 Android 裝置上啟用偵錯工具：</span><span class="sxs-lookup"><span data-stu-id="d252c-150">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d252c-151">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d252c-151">Prerequisites</span></span>

* <span data-ttu-id="d252c-152">在安全內容中提供靜態 html 網頁的 web 伺服器 (HTTPs://，或在開發電腦上的 localhost) 透過埠轉送來提供服務。</span><span class="sxs-lookup"><span data-stu-id="d252c-152">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="d252c-153">例如，利用 *服務* npm 套件作為靜態 html 檔案的簡易輕量 web 伺服器，檢查更多 [npm 服務](https://github.com/vercel/serve#readme)</span><span class="sxs-lookup"><span data-stu-id="d252c-153">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="d252c-154">最初隨 Google Play 商店出貨的裝置，必須執行 Android 7.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="d252c-154">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="d252c-155">開發工作站和裝置上的 [Google Chrome](https://support.google.com/chrome/answer/95346) 最新版本</span><span class="sxs-lookup"><span data-stu-id="d252c-155">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="d252c-156">若要確認裝置已正確設定為執行 WebXR，請流覽至裝置上的 [範例 WebXR 頁面](https://immersive-web.github.io/webxr-samples/) 。</span><span class="sxs-lookup"><span data-stu-id="d252c-156">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="d252c-157">您應該會看到如下的訊息：</span><span class="sxs-lookup"><span data-stu-id="d252c-157">You should see the message, such as:</span></span>

    > <span data-ttu-id="d252c-158">如果您有適當的硬體，您的瀏覽器支援 WebXR，而且可以執行虛擬實境和增強的現實體驗。</span><span class="sxs-lookup"><span data-stu-id="d252c-158">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="d252c-159">在 Android 裝置上啟用開發人員模式和 USB 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d252c-159">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="d252c-160">請參閱在官方檔頁面[上設定裝置開發人員選項](https://developer.android.com/studio/debug/dev-options)，以瞭解如何為您的 Android 版本進行這項操作</span><span class="sxs-lookup"><span data-stu-id="d252c-160">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="d252c-161">接下來，透過 USB 纜線將 Android 裝置連接到您的開發電腦或膝上型電腦</span><span class="sxs-lookup"><span data-stu-id="d252c-161">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="d252c-162">確定開發電腦上的網頁伺服器正在執行。</span><span class="sxs-lookup"><span data-stu-id="d252c-162">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="d252c-163">例如，流覽至包含您的 web 裝載頁面 (index.html) 的根資料夾，然後執行下列程式碼 (假設您使用服務 npm 套件) ：</span><span class="sxs-lookup"><span data-stu-id="d252c-163">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="d252c-164">在您的開發電腦上開啟 Google Chrome，並在網址列中輸入下列文字：</span><span class="sxs-lookup"><span data-stu-id="d252c-164">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="d252c-165">chrome：//inspect # devices ![ CHROME USB 調試時間視窗](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="d252c-165">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="d252c-166">確定已啟用 [ *探索 USB 裝置* ] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="d252c-166">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="d252c-167">按一下 [ *埠轉送* ] 按鈕，並確認 *埠轉送* 已啟用且包含 *localhost： 5000* 輸入，如下所示：  ![ Chrome 埠轉送視窗](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="d252c-167">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="d252c-168">在連線的 Android 裝置中，開啟 Google Chrome 視窗並流覽至 *http://localhost:5000* ，您應該會看到 cube</span><span class="sxs-lookup"><span data-stu-id="d252c-168">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="d252c-169">在您的開發電腦上的 Chrome 中，您將會看到您的裝置，以及目前在該處開啟的網頁清單：  ![ Chrome 檢查視窗](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="d252c-169">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="d252c-170">按一下專案旁的 [ *檢查* ] 按鈕 *http://localhost:5000* ：  ![ Chrome DevTools Debug 視窗](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="d252c-170">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="d252c-171">使用 [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) 來偵測頁面</span><span class="sxs-lookup"><span data-stu-id="d252c-171">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="d252c-172">重要心得</span><span class="sxs-lookup"><span data-stu-id="d252c-172">Takeaways</span></span>

<span data-ttu-id="d252c-173">以下是本教學課程中最重要的優點：</span><span class="sxs-lookup"><span data-stu-id="d252c-173">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="d252c-174">Babylon.js 可讓您輕鬆地使用 JavaScript 建立沉浸式體驗</span><span class="sxs-lookup"><span data-stu-id="d252c-174">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="d252c-175">若要建立虛擬幕後，您不需要撰寫低層級的程式碼，或學習新的技術</span><span class="sxs-lookup"><span data-stu-id="d252c-175">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="d252c-176">您可以使用 WebXR 支援的瀏覽器來建立混合現實應用程式，而不需要購買耳機</span><span class="sxs-lookup"><span data-stu-id="d252c-176">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="d252c-177">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d252c-177">Next steps</span></span>

<span data-ttu-id="d252c-178">恭喜！</span><span class="sxs-lookup"><span data-stu-id="d252c-178">Congratulations!</span></span> <span data-ttu-id="d252c-179">您已完成一系列的 babylon.js 教學課程，並瞭解如何：</span><span class="sxs-lookup"><span data-stu-id="d252c-179">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d252c-180">設定開發環境</span><span class="sxs-lookup"><span data-stu-id="d252c-180">Set up a development environment</span></span>
> * <span data-ttu-id="d252c-181">建立新的網頁以顯示結果</span><span class="sxs-lookup"><span data-stu-id="d252c-181">Create a new web page to display results</span></span>
> * <span data-ttu-id="d252c-182">用來建立基本3D 元素並與其互動的 babylon.js API</span><span class="sxs-lookup"><span data-stu-id="d252c-182">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="d252c-183">在 Windows Mixed Reality 模擬器中執行和測試應用程式</span><span class="sxs-lookup"><span data-stu-id="d252c-183">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="d252c-184">如需混合現實 JavaScript 開發的詳細資訊，請參閱 [javascript 開發總覽](/javascript-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d252c-184">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>
