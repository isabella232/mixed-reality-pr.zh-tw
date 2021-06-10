---
title: Babylon.js 與3D 物件互動的教學課程
description: 瞭解如何使用 babylon.js 並與3D 物件互動。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality、javascript、教學課程、BabylonJS、hololens、mixed reality、UWP、Windows 10、WebXR、沉浸式網路
ms.localizationpriority: high
ms.openlocfilehash: a3dbab0572cd50105dac3d877a0d72c5cbc504b6
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584517"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="059a1-104">教學課程：與3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="059a1-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="059a1-105">瞭解如何使用 babylon.js 建立與混合現實體驗的3D 物件和互動。</span><span class="sxs-lookup"><span data-stu-id="059a1-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="059a1-106">在本節中，您將從簡單的部分開始，例如在選取物件時繪製 cube 的臉部。</span><span class="sxs-lookup"><span data-stu-id="059a1-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="059a1-107">本教學課程涵蓋下列主題：</span><span class="sxs-lookup"><span data-stu-id="059a1-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="059a1-108">如何新增互動</span><span class="sxs-lookup"><span data-stu-id="059a1-108">How to add interactions</span></span>
> * <span data-ttu-id="059a1-109">啟用 WebXR 沉浸式模式</span><span class="sxs-lookup"><span data-stu-id="059a1-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="059a1-110">在 Windows Mixed Reality 模擬器上執行應用程式</span><span class="sxs-lookup"><span data-stu-id="059a1-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="059a1-111">在 Android Chrome 上執行和偵錯工具</span><span class="sxs-lookup"><span data-stu-id="059a1-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="059a1-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="059a1-112">Before you begin</span></span>

<span data-ttu-id="059a1-113">在先前的教學課程步驟中，已建立一個具有場景的基本網頁。</span><span class="sxs-lookup"><span data-stu-id="059a1-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="059a1-114">讓裝載網頁開啟以供編輯。</span><span class="sxs-lookup"><span data-stu-id="059a1-114">Have the hosting web page open for editing.</span></span>

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
            
            const alpha =  Math.PI/4;
            const beta = Math.PI/3;
            const radius = 8;
            const target = new BABYLON.Vector3(0, 0, 0);
            
            const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
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

## <a name="add-interaction"></a><span data-ttu-id="059a1-115">新增互動</span><span class="sxs-lookup"><span data-stu-id="059a1-115">Add interaction</span></span>

1. <span data-ttu-id="059a1-116">首先，讓我們更新建立 cube 的程式碼，以便使用隨機色彩來繪製 cube。</span><span class="sxs-lookup"><span data-stu-id="059a1-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="059a1-117">若要這樣做，我們會將 [材質](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) 新增至 cube。</span><span class="sxs-lookup"><span data-stu-id="059a1-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="059a1-118">材質可讓我們指定色彩和材質，也可以用來涵蓋其他物件。</span><span class="sxs-lookup"><span data-stu-id="059a1-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="059a1-119">材質的顯示方式取決於場景中使用的燈光或光線，以及它如何設定為回應。</span><span class="sxs-lookup"><span data-stu-id="059a1-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="059a1-120">例如，diffuseColor 會將色彩全部散佈在其所連接的網格上。</span><span class="sxs-lookup"><span data-stu-id="059a1-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="059a1-121">新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="059a1-121">Add the following code:</span></span>

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="059a1-122">現在 cube 以隨機色彩繪製，讓我們加入互動：</span><span class="sxs-lookup"><span data-stu-id="059a1-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="059a1-123">變更按一下 cube 時的色彩</span><span class="sxs-lookup"><span data-stu-id="059a1-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="059a1-124">變更色彩之後移動 cube</span><span class="sxs-lookup"><span data-stu-id="059a1-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="059a1-125">若要加入互動，我們應該使用 [動作](https://doc.babylonjs.com/divingDeeper/events/actions)。</span><span class="sxs-lookup"><span data-stu-id="059a1-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="059a1-126">啟動動作以回應事件觸發程式。</span><span class="sxs-lookup"><span data-stu-id="059a1-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="059a1-127">例如，當使用者按一下 cube 時。</span><span class="sxs-lookup"><span data-stu-id="059a1-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="059a1-128">我們只需要將 BABYLON 具現化。ActionManager 並註冊特定觸發程式的動作。</span><span class="sxs-lookup"><span data-stu-id="059a1-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="059a1-129">當有人按一下 cube 時， [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) 會執行 JavaScript 函數：</span><span class="sxs-lookup"><span data-stu-id="059a1-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            const sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
    ```

1. <span data-ttu-id="059a1-130">網頁的最後一個程式碼看起來會如下所示：</span><span class="sxs-lookup"><span data-stu-id="059a1-130">The final code of the web page will look as follows:</span></span>

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
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="059a1-131">啟用 WebXR 沉浸式體驗</span><span class="sxs-lookup"><span data-stu-id="059a1-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="059a1-132">既然我們的 cube 正在變更色彩，我們就可以開始試用沉浸式體驗。</span><span class="sxs-lookup"><span data-stu-id="059a1-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="059a1-133">在這個步驟中，我們將介紹一個 [基礎](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground)。</span><span class="sxs-lookup"><span data-stu-id="059a1-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="059a1-134">Cube 將在空氣中掛斷，我們會在底部看到樓層。</span><span class="sxs-lookup"><span data-stu-id="059a1-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="059a1-135">以下列方式加入地面：</span><span class="sxs-lookup"><span data-stu-id="059a1-135">Add the ground as follows:</span></span>

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="059a1-136">這會建立一個簡單的4x4 計量樓層。</span><span class="sxs-lookup"><span data-stu-id="059a1-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="059a1-137">為了加入 WebXR 支援，我們必須呼叫 *createDefaultXRExperienceAsync*，其具有 *承諾* 結果。</span><span class="sxs-lookup"><span data-stu-id="059a1-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="059a1-138">將此程式碼新增至 *createScene* 函式的結尾，而不是傳回 *場景;*：</span><span class="sxs-lookup"><span data-stu-id="059a1-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="059a1-139">因為 *createScene* 函式現在會傳回承諾而不是場景，所以我們需要修改 *CreateScene* 和 *engine runRenderLoop* 的呼叫方式。</span><span class="sxs-lookup"><span data-stu-id="059a1-139">Since the *createScene* function is now returning a promise instead of a scene, we need to modify how *createScene* and *engine.runRenderLoop* are called.</span></span> <span data-ttu-id="059a1-140">以下列程式碼取代這些函式的目前呼叫（位於標記之前） *\</script>* ：</span><span class="sxs-lookup"><span data-stu-id="059a1-140">Replace the current calls of these functions, which are located right before the *\</script>* tag, with the code below:</span></span>

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. <span data-ttu-id="059a1-141">網頁的最後一個程式碼看起來會如下所示：</span><span class="sxs-lookup"><span data-stu-id="059a1-141">The final code of the web page will look as follows:</span></span>

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
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                const xrPromise = scene.createDefaultXRExperienceAsync({
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

1. <span data-ttu-id="059a1-142">上述程式碼會在瀏覽器視窗中產生下列輸出： ![ WebXR 場景](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="059a1-142">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="059a1-143">在 Windows Mixed Reality 模擬器上執行</span><span class="sxs-lookup"><span data-stu-id="059a1-143">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="059a1-144">如果您先前未執行過，請[啟用 Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)模擬器。</span><span class="sxs-lookup"><span data-stu-id="059a1-144">[Enable the Windows Mixed Reality Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) if you have not done so in the past.</span></span>

1. <span data-ttu-id="059a1-145">選取右下角的沉浸式-VR 按鈕： ![ 沉浸式 Vr 按鈕](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="059a1-145">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="059a1-146">此動作會啟動 Windows Mixed Reality 模擬器視窗，如下所示： ![ 混合實境入口](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="059a1-146">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="059a1-147">您可以使用鍵盤上的 W、A、S 和 D 鍵，據以向前、向左和向右向前復原。</span><span class="sxs-lookup"><span data-stu-id="059a1-147">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="059a1-148">使用模擬手將目標設為 cube，然後按鍵盤上的 Enter 鍵以執行按一下動作。</span><span class="sxs-lookup"><span data-stu-id="059a1-148">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="059a1-149">Cube 會變更其色彩並移至新位置。</span><span class="sxs-lookup"><span data-stu-id="059a1-149">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="059a1-150">以 cube 為目標時，請確定右邊的光線 (白色圓圈) 與 cube 交集，如上圖所示。</span><span class="sxs-lookup"><span data-stu-id="059a1-150">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="059a1-151">深入瞭解如何 [使用手上的 Point 和 commit](../../../../design/point-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="059a1-151">Learn more about [Point and commit with hands](../../../../design/point-and-commit.md).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="059a1-152">在 Android 裝置上執行和調試</span><span class="sxs-lookup"><span data-stu-id="059a1-152">Run and debug on Android device</span></span>

<span data-ttu-id="059a1-153">請執行下列步驟，在您的 Android 裝置上啟用偵錯工具：</span><span class="sxs-lookup"><span data-stu-id="059a1-153">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="059a1-154">必要條件</span><span class="sxs-lookup"><span data-stu-id="059a1-154">Prerequisites</span></span>

* <span data-ttu-id="059a1-155">在安全內容中提供靜態 html 網頁的 web 伺服器 (HTTPs://，或在開發電腦上的 localhost) 透過埠轉送來提供服務。</span><span class="sxs-lookup"><span data-stu-id="059a1-155">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="059a1-156">例如，利用 *服務* npm 套件作為靜態 html 檔案的簡易輕量 web 伺服器，檢查更多 [npm 服務](https://github.com/vercel/serve#readme)</span><span class="sxs-lookup"><span data-stu-id="059a1-156">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="059a1-157">最初隨 Google Play 商店出貨的裝置，必須執行 Android 7.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="059a1-157">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="059a1-158">開發工作站和裝置上的 [Google Chrome](https://support.google.com/chrome/answer/95346) 最新版本</span><span class="sxs-lookup"><span data-stu-id="059a1-158">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="059a1-159">若要確認裝置已正確設定為執行 WebXR，請流覽至裝置上的 [範例 WebXR 頁面](https://immersive-web.github.io/webxr-samples/) 。</span><span class="sxs-lookup"><span data-stu-id="059a1-159">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="059a1-160">您應該會看到如下的訊息：</span><span class="sxs-lookup"><span data-stu-id="059a1-160">You should see the message, such as:</span></span>

    > <span data-ttu-id="059a1-161">如果您有適當的硬體，您的瀏覽器支援 WebXR，而且可以執行虛擬實境和增強的現實體驗。</span><span class="sxs-lookup"><span data-stu-id="059a1-161">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="059a1-162">在 Android 裝置上啟用開發人員模式和 USB 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="059a1-162">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="059a1-163">請參閱在官方檔頁面[上設定裝置開發人員選項](https://developer.android.com/studio/debug/dev-options)，以瞭解如何為您的 Android 版本進行這項操作</span><span class="sxs-lookup"><span data-stu-id="059a1-163">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="059a1-164">接下來，透過 USB 纜線將 Android 裝置連接到您的開發電腦或膝上型電腦</span><span class="sxs-lookup"><span data-stu-id="059a1-164">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="059a1-165">確定開發電腦上的網頁伺服器正在執行。</span><span class="sxs-lookup"><span data-stu-id="059a1-165">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="059a1-166">例如，流覽至包含您的 web 裝載頁面 (index.html) 的根資料夾，然後執行下列程式碼 (假設您使用服務 npm 套件) ：</span><span class="sxs-lookup"><span data-stu-id="059a1-166">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="059a1-167">在您的開發電腦上開啟 Google Chrome，並在網址列中輸入下列文字：</span><span class="sxs-lookup"><span data-stu-id="059a1-167">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="059a1-168">chrome：//inspect # devices ![ CHROME USB 調試時間視窗](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="059a1-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="059a1-169">確定已啟用 [ *探索 USB 裝置* ] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="059a1-169">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="059a1-170">按一下 [ *埠轉送* ] 按鈕，並確認 *埠轉送* 已啟用且包含 *localhost： 5000* 輸入，如下所示：  ![ Chrome 埠轉送視窗](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="059a1-170">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="059a1-171">在連線的 Android 裝置中，開啟 Google Chrome 視窗並流覽至 *http://localhost:5000* ，您應該會看到 cube</span><span class="sxs-lookup"><span data-stu-id="059a1-171">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="059a1-172">在您的開發電腦上的 Chrome 中，您將會看到您的裝置，以及目前在該處開啟的網頁清單：  ![ Chrome 檢查視窗](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="059a1-172">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="059a1-173">按一下專案旁的 [ *檢查* ] 按鈕 *http://localhost:5000* ：  ![ Chrome DevTools Debug 視窗](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="059a1-173">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="059a1-174">使用 [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) 來偵測頁面</span><span class="sxs-lookup"><span data-stu-id="059a1-174">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="059a1-175">重要心得</span><span class="sxs-lookup"><span data-stu-id="059a1-175">Takeaways</span></span>

<span data-ttu-id="059a1-176">以下是本教學課程中最重要的優點：</span><span class="sxs-lookup"><span data-stu-id="059a1-176">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="059a1-177">Babylon.js 可讓您輕鬆地使用 JavaScript 建立沉浸式體驗</span><span class="sxs-lookup"><span data-stu-id="059a1-177">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="059a1-178">若要建立虛擬幕後，您不需要撰寫低層級的程式碼，或學習新的技術</span><span class="sxs-lookup"><span data-stu-id="059a1-178">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="059a1-179">您可以使用 WebXR 支援的瀏覽器來建立混合現實應用程式，而不需要購買耳機</span><span class="sxs-lookup"><span data-stu-id="059a1-179">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="059a1-180">後續步驟</span><span class="sxs-lookup"><span data-stu-id="059a1-180">Next steps</span></span>

<span data-ttu-id="059a1-181">恭喜！</span><span class="sxs-lookup"><span data-stu-id="059a1-181">Congratulations!</span></span> <span data-ttu-id="059a1-182">您已完成一系列的 babylon.js 教學課程，並瞭解如何：</span><span class="sxs-lookup"><span data-stu-id="059a1-182">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="059a1-183">設定開發環境</span><span class="sxs-lookup"><span data-stu-id="059a1-183">Set up a development environment</span></span>
> * <span data-ttu-id="059a1-184">建立新的網頁以顯示結果</span><span class="sxs-lookup"><span data-stu-id="059a1-184">Create a new web page to display results</span></span>
> * <span data-ttu-id="059a1-185">用來建立基本3D 元素並與其互動的 babylon.js API</span><span class="sxs-lookup"><span data-stu-id="059a1-185">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="059a1-186">在 Windows Mixed Reality 模擬器中執行和測試應用程式</span><span class="sxs-lookup"><span data-stu-id="059a1-186">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="059a1-187">如需混合現實 JavaScript 開發的詳細資訊，請參閱 [javascript 開發總覽](/javascript-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="059a1-187">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>
