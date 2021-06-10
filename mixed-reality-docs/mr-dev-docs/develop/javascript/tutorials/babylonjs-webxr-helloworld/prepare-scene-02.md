---
title: 使用基本3D 物件準備場景的 Babylon.js 教學課程
description: 瞭解如何使用 babylon.js，並將基本的3D 物件加入場景。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality、javascript、教學課程、BabylonJS、hololens、mixed reality、UWP、Windows 10、WebXR、沉浸式網路
ms.localizationpriority: high
ms.openlocfilehash: 8213c445da9c1bbf0eeb591b7995fb61bc6d5b5f
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584500"
---
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="4f7f2-104">教學課程：準備場景</span><span class="sxs-lookup"><span data-stu-id="4f7f2-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="4f7f2-105">瞭解如何準備場景，並在其中新增一些基本的3D 元素。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="4f7f2-106">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="4f7f2-107">建立場景</span><span class="sxs-lookup"><span data-stu-id="4f7f2-107">Create a scene</span></span>
> * <span data-ttu-id="4f7f2-108">新增相機</span><span class="sxs-lookup"><span data-stu-id="4f7f2-108">Add a camera</span></span>
> * <span data-ttu-id="4f7f2-109">新增燈光</span><span class="sxs-lookup"><span data-stu-id="4f7f2-109">Add light</span></span>
> * <span data-ttu-id="4f7f2-110">新增基本3D 元素</span><span class="sxs-lookup"><span data-stu-id="4f7f2-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="4f7f2-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="4f7f2-111">Before you begin</span></span>

<span data-ttu-id="4f7f2-112">在先前的教學課程步驟中，已建立基本的網頁。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="4f7f2-113">開啟網頁進行編輯。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-113">Have the web page open for editing.</span></span>

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

## <a name="create-a-scene"></a><span data-ttu-id="4f7f2-114">建立場景</span><span class="sxs-lookup"><span data-stu-id="4f7f2-114">Create a scene</span></span>

<span data-ttu-id="4f7f2-115">場景是所有內容將會顯示的位置。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="4f7f2-116">可能有多個場景，而且可以在幕後切換。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="4f7f2-117">閱讀 [babylon.js 場景](https://doc.babylonjs.com/divingDeeper/scene)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="4f7f2-118">將腳本標記新增至 canvas html 專案之後，然後加入下列程式碼來建立填滿黑色色彩的場景：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

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

    <span data-ttu-id="4f7f2-119">在上述程式碼中，我們必須建立 babylon.js web 轉譯引擎的實例，以轉譯場景並在畫布上攔截事件。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="4f7f2-120">如需有關引擎的詳細資訊，請參閱檔頁面 [babylon。](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span><span class="sxs-lookup"><span data-stu-id="4f7f2-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="4f7f2-121">預設不會呈現場景。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-121">The scene is not rendered by default.</span></span> <span data-ttu-id="4f7f2-122">請記住，可能有多個場景，您可以控制要顯示的場景。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="4f7f2-123">若要在每個畫面上重複呈現場景，請在呼叫 *createScene* 函式之後執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="4f7f2-124">新增基本3D 元素</span><span class="sxs-lookup"><span data-stu-id="4f7f2-124">Add basic 3D element</span></span>

1. <span data-ttu-id="4f7f2-125">讓我們加入第一個3D 圖形。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="4f7f2-126">在3D 虛擬世界中，圖形是由 *網格* 所建立，而多個三角形 facet 聯結在一起，每個面向都是從三個頂點所建立。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="4f7f2-127">您可以使用預先定義的網格或建立您自己的自訂網格。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="4f7f2-128">在這裡，我們將使用預先定義的方塊網格，亦即 cube。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="4f7f2-129">若要建立 box，請使用 [BABYLON。MeshBuilder. CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box)。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="4f7f2-130">這些參數是名稱，而選項 (選項會根據網格) 的類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="4f7f2-131">將下列程式碼附加至函數 *createScene*：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="4f7f2-132">在 Microsoft Edge 瀏覽器中開啟網頁，並檢查輸出。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="4f7f2-133">瀏覽器視窗會顯示空白頁面。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-133">The browser window shows a blank page.</span></span> <span data-ttu-id="4f7f2-134">使用鍵盤開啟 DevTools，然後選取 F12 或 Ctrl + Shift + I (Windows、Linux) 或命令 + 選項 + I (macOS) 。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="4f7f2-135">開啟 [ *主控台* ] 索引標籤之後，您就可以開始尋找錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="4f7f2-136">將會顯示錯誤：「未攔截的錯誤：未定義相機」。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="4f7f2-137">現在，我們必須將攝影機加入場景中。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="4f7f2-138">新增相機</span><span class="sxs-lookup"><span data-stu-id="4f7f2-138">Add a camera</span></span>

1. <span data-ttu-id="4f7f2-139">若要觀看虛擬世界並與其互動，必須將攝影機連接至畫布。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-139">In order to view the virtual world and interact with it, a camera must be attached to the canvas.</span></span> <span data-ttu-id="4f7f2-140">讓我們新增 BABYLON 類型的相機 [。ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera)，可在目標周圍旋轉。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), which can be rotated around a target.</span></span> <span data-ttu-id="4f7f2-141">建立相機實例所需的參數如下：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-141">The parameters required to create an instance of the camera are:</span></span>
    1. <span data-ttu-id="4f7f2-142">**名稱**：相機的名稱</span><span class="sxs-lookup"><span data-stu-id="4f7f2-142">**name**: name of the camera</span></span>
    1. <span data-ttu-id="4f7f2-143">**Alpha**：沿著 longitudinal 軸的角度定位 (弧度) </span><span class="sxs-lookup"><span data-stu-id="4f7f2-143">**alpha**: angular position along the longitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="4f7f2-144">**Beta**：沿著 latitudinal 軸的角度定位 (弧度) </span><span class="sxs-lookup"><span data-stu-id="4f7f2-144">**beta**: angular position along the latitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="4f7f2-145">**半徑**：與目標的距離</span><span class="sxs-lookup"><span data-stu-id="4f7f2-145">**radius**: distance from the target</span></span>
    1. <span data-ttu-id="4f7f2-146">**目標**：相機一律會面對 (x y z 座標所定義的點) </span><span class="sxs-lookup"><span data-stu-id="4f7f2-146">**target**: the point that the camera would always face towards (defined by x-y-z coordinates)</span></span>
    1. <span data-ttu-id="4f7f2-147">**場景**：相機所在的場景</span><span class="sxs-lookup"><span data-stu-id="4f7f2-147">**scene**: the scene that the camera is in</span></span>

    <span data-ttu-id="4f7f2-148">[Alpha]、[Beta]、[半徑] 和 [目標] 一起定義相機在空間中的位置，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-148">Alpha, beta, radius, and target together define the camera's position in the space, as shown in the diagram below:</span></span>

    ![攝影機 Alpha Beta 半徑](../images/camera-alpha-beta-radius.jpg)

    <span data-ttu-id="4f7f2-150">將下列程式碼新增至 *createScene* 函式：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-150">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="4f7f2-151">如果您在瀏覽器中檢查輸出，將會看到黑色的畫布。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-151">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="4f7f2-152">我們遺漏了燈光。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-152">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="4f7f2-153">新增燈光</span><span class="sxs-lookup"><span data-stu-id="4f7f2-153">Add light</span></span>

1. <span data-ttu-id="4f7f2-154">有四種類型的燈光可搭配燈光屬性範圍使用：點、方向、點和 Hemispheric 淺色。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-154">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="4f7f2-155">讓我們新增環境光源 [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-155">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="4f7f2-156">網頁的最後一個程式碼看起來會如下所示：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-156">The final code of the web page will look as follows:</span></span>

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

1. <span data-ttu-id="4f7f2-157">檢查瀏覽器中的輸出。</span><span class="sxs-lookup"><span data-stu-id="4f7f2-157">Check the output in the browser.</span></span> <span data-ttu-id="4f7f2-158">您應該會看到 cube，並使用滑鼠來旋轉立方體周圍的相機，並查看 cube 的不同臉部：</span><span class="sxs-lookup"><span data-stu-id="4f7f2-158">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![具有 cube 的基本場景](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="4f7f2-160">下一步</span><span class="sxs-lookup"><span data-stu-id="4f7f2-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4f7f2-161">下一個教學課程： 3. 與3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="4f7f2-161">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)
