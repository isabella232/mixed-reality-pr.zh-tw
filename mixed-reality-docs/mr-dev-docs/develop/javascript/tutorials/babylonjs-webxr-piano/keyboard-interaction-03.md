---
title: 播放3D 鋼琴
description: 瞭解如何使用 Babylon.js 將互動新增至虛擬鋼琴
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: mixed reality、javascript、教學課程、BabylonJS、hololens、mixed reality、UWP、Windows 10、WebXR、沉浸式網路
ms.localizationpriority: high
ms.openlocfilehash: 8f995d618398fef56ce42d6c3e9863256627bf75
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932419"
---
# <a name="tutorial-play-the-3d-piano"></a>教學課程：播放3D 鋼琴

在上一個教學課程中，我們已成功建立完整 88-key 鋼琴鍵盤的模型。 現在讓我們讓它可在 XR 空間中播放。

在本教學課程中，您將學會如何：

> [!div class="checklist"]
> * 使用指標事件新增互動式鋼琴功能
> * 將網格調整至不同的大小
> * 在 XR 中啟用遙傳和多重指標支援

## <a name="before-you-begin"></a>開始之前

請確定您已完成本 [系列中的前一個教學](keyboard-model-02.md) 課程，以繼續將其新增至程式碼。

*index.html*

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

*scene.js*

```javascript
const buildKey = function (scene, parent, props) {
    if (props.type === "white") {
        /*
        Props for building a white key should contain: 
        note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX

        As an example, the props for building the middle C white key would be
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
        */

        // Create bottom part
        const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);

        // Create top part
        const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
        top.position.z =  4.75;
        top.position.x += props.topPositionX;

        // Merge bottom and top parts
        // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
        const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.name = props.note + props.register;
        key.parent = parent;

        return key;
    }
    else if (props.type === "black") {
        /*
        Props for building a black key should contain: 
        note, wholePositionX, register, referencePositionX

        As an example, the props for building the C#4 black key would be
        {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
        */

        // Create black color material
        const blackMat = new BABYLON.StandardMaterial("black");
        blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

        // Create black key
        const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
        key.position.z += 4.75;
        key.position.y += 0.25;
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.material = blackMat;
        key.parent = parent;

        return key;
    }
}

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

    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }

    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});

    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });

    // Lift the piano keyboard
    keyboard.position.y += 80;

    const xrHelper = await scene.createDefaultXRExperienceAsync();

    return scene;
}
```

## <a name="making-the-piano-keyboard-playable"></a>讓鋼琴鍵盤能播放

現在，我們建立的鋼琴鍵盤是靜態模型，不會回應任何使用者互動。 在這一節中，我們會在有人按下按鍵時，程式設計按鍵以向下移動並播放音效。

1. Babylon.js 提供可與其互動的不同類型事件（或 [可預見值](https://doc.babylonjs.com/divingDeeper/events/observables)）。 在我們的案例中，我們將會處理， `onPointerObservable` 因為我們想要在有人透過指標（可以是滑鼠點擊、觸控、XR 控制器按鈕點按下）來執行動作時，對按鍵進行程式設計。

    以下是如何將任何行為新增至的基本結構 `onPointerObservable` ：

    ```javascript
    scene.onPointerObservable.add((pointerInfo) => {
        // do something
    });
    ```

1. 當 Babylon.js 提供 [許多不同類型的指標事件](https://doc.babylonjs.com/typedoc/classes/babylon.pointereventtypes)時，我們只會使用 `POINTERDOWN` 和 `POINTERUP` 事件來程式設計鋼琴索引鍵的行為，並使用下列結構：

    ```javascript
    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                // When the pointer is down on a piano key,
                // move the piano key downward (to show that it is pressed)
                // and play the sound of the note
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                // When the pointer is released,
                // move the piano key upward to its original position
                // and stop the sound of the note of the key that is released
                break;
        }
    });
    ```

1. 當我們按下並放開按鍵時，讓我們先將鋼琴按鍵往下和向上移動。

    在指標下移事件中，我們需要偵測所按下的網格、確定它是鋼琴按鍵，並將網格的 y 座標變更為較小的數量，使其看起來像是按下按鍵。

    針對指標上事件，比較複雜一點，因為按下索引鍵的指標可能不會在機碼上釋放。 例如，有人可能按一下按鍵 C4、將其滑鼠拖曳至 E4，然後放開按一下。 在此情況下，我們仍然想要釋出已按下的按鍵 (C4) 而不是 `pointerUp` 事件發生的位置 (E4) 。

    讓我們看看下列程式碼如何達成我們所要的目標：

    ```javascript
    const pointerToKey = new Map();
    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                if(pointerInfo.pickInfo.hit) {
                    const pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    const pointerId = pointerInfo.event.pointerId;
                    if (pickedMesh.parent === keyboard) {
                        pickedMesh.position.y -= 0.5;
                        // play the sound of the note
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                const pointerId = pointerInfo.event.pointerId;
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5;
                    // stop the sound of the note of the key that is released
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });
    ```

    對 `pointerId` 每個指標而言都是唯一的，而且可以在有多個控制器或使用觸控式螢幕時協助我們識別指標。 在這裡，我們 `Map` 已將名為的物件 `pointerToKey` ，用來儲存在哪一個索引鍵上按下指標的關聯性，讓我們知道當指標釋出時所要釋放的金鑰，不論發行的位置為何。

1. 以下是與上述程式碼互動的樣子：

    ![互動式鋼琴按鍵](./images/interactive-piano-keys.gif)

1. 現在讓我們在按下並放開按鍵時，開始播放和停止音效。 為了達成此目的，我們將使用名為 **soundfont** 的 JAVAscript 程式庫，讓我們可以輕鬆地播放我們所選檢測的 MIDI 音效。

    [下載程式庫的縮減程式碼](./files/soundfont-player.min.js)，並將它儲存在 *index.html* 的相同資料夾中，並將它包含在 `<header>` *index.html* 的標記中：

    ```html
    <head>
        <title>Babylon Template</title>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <script src="scene.js"></script>
        <script src="soundfont-player.min.js"></script>
        <style>
                body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    ```

    匯入程式庫之後，以下是我們可以使用媒體櫃初始化檢測並播放/停止 MIDI 音效的方式：

    ```javascript
    const pianoSound = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');
    const C4 = piano.play("C4"); // Play note C4
    C4.stop(); // Stop note C4
    ```

1. 現在讓我們將它併入指標事件中，並完成本節的程式碼：

    ```javascript
    const pointerToKey = new Map()
    const piano = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');

    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                if(pointerInfo.pickInfo.hit) {
                    let pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    let pointerId = pointerInfo.event.pointerId;
                    if (keys.has(pickedMesh)) {
                        pickedMesh.position.y -= 0.5; // Move the key downward
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh,
                            note: pianoSound.play(pointerInfo.pickInfo.pickedMesh.name) // Play the sound of the note
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                let pointerId = pointerInfo.event.pointerId;
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5; // Move the key upward
                    pointerToKey.get(pointerId).note.stop(); // Stop the sound of the note
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });
    ```

    由於我們是以其所代表的附注來命名每個索引鍵的網格，因此我們可以輕鬆地指定要播放的附注，方法是將網格的名稱傳遞至函式 `pianoSound.play()` 。 也請注意，我們會將音效儲存在 `pointerToKey` 地圖中，讓我們知道釋放金鑰時要停止的音效。

## <a name="scaling-the-piano-for-immersive-vr-mode"></a>針對沉浸式 VR 模式調整鋼琴

現在，您可能已經在您的滑鼠 (上玩了鋼琴，甚至是在新增互動式功能時) 觸控畫面。 在本節中，我們將移至沉浸式 VR 空間。

1. 若要在沉浸式的 VR 耳機中開啟頁面，您必須先將耳機連接至開發人員電腦，並確定它已[設定為在 Windows Mixed Reality 應用程式中使用](/enthusiast-guide/set-up-windows-mixed-reality)。 如果您正在使用 Windows Mixed Reality 模擬器，請[確定已啟用它](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)。

1. 您現在會在網頁右下角看到一個沉浸式的 VR 按鈕。 按一下該檔案，您就可以在您所連線的 XR 裝置中看到鋼琴。

    ![沉浸式 VR 按鈕](../images/immersive-vr-button.png)

1. 當您進入虛擬空間之後，您可能會注意到我們建立的鋼琴非常龐大。 在 VR 世界中，我們只能將指標指向按鍵的距離，並將其播放。

    ![大鋼琴](./images/huge-piano.jpg)

1. 讓我們縮小鋼琴，使其大小更像真實生活中一般的站立會議鋼琴。 若要這樣做，我們必須使用公用程式函式，讓我們能夠 [調整相對於空間中某個點的網格](https://doc.babylonjs.com/toolsAndResources/utilities/Pivot#enlargement)。 將此函式新增至) 以外的 *scene.js* (`createScene()` ：

    ```javascript
    const scaleFromPivot = function(transformNode, pivotPoint, scale) {
        const _sx = scale / transformNode.scaling.x;
        const _sy = scale / transformNode.scaling.y;
        const _sz = scale / transformNode.scaling.z;
        transformNode.scaling = new BABYLON.Vector3(_sx, _sy, _sz); 
        transformNode.position = new BABYLON.Vector3(pivotPoint.x + _sx * (transformNode.position.x - pivotPoint.x), pivotPoint.y + _sy * (transformNode.position.y - pivotPoint.y), pivotPoint.z + _sz * (transformNode.position.z - pivotPoint.z));
    }
    ```

    此函式會使用3個參數：
    * **transformNode**： `TransformNode` 要調整的
    * **pivotPoint**： `Vector3` 物件，指出調整相對的點
    * **調整**：縮放比例

1. 我們將使用此函式，以0.015 的因數來調整鋼琴框架和按鍵，並在來源上使用 pivot 點。 將函式呼叫放在函式之後，將函式呼叫附加至函式 `createScene()` `keyboard.position.y += 80;` ：

    ```javascript
    // Put this line at the beginning of createScene()
    const scale = 0.015;
    ```

    ```javascript
    // Put this function call after keyboard.position.y += 80;

    // Scale the entire piano
    scaleFromPivot(piano, new BABYLON.Vector3(0, 0, 0), scale);
    ```

1. 也別忘了調整攝影機的位置：

    ```javascript
    const alpha =  3*Math.PI/2;
    const beta = Math.PI/50;
    const radius = 220*scale; // scale the radius
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. 現在當我們再次輸入 VR 空間時，鋼琴會是一般站立會議鋼琴的大小。

    ![VR 中的一般站立會議鋼琴](./images/normal-standup-piano.jpg)

## <a name="enabling-webxr-features"></a>啟用 WebXR 功能

既然我們已在 VR 空間中將鋼琴調整為適當的大小，讓我們來啟用一些酷炫的 WebXR 功能，以改善我們在空間中的大鋼琴體驗。

1. 如果您是使用沉浸式的 VR 控制器來播放鋼琴，可能已經注意到您一次只能使用一個控制器。 讓我們使用 Babylon.js 的[WebXR 功能管理員](https://doc.babylonjs.com/divingDeeper/webXR/webXRFeaturesManager)在 XR 空間中啟用[多重指標支援](https://doc.babylonjs.com/typedoc/interfaces/babylon.iwebxrcontrollerpointerselectionoptions)。

    將下列程式碼新增至函式 `createScene()` 的 `xrHelper` 初始化行之後：

    ```javascript
    const featuresManager = xrHelper.baseExperience.featuresManager;

    const pointerSelection = featuresManager.enableFeature(BABYLON.WebXRFeatureName.POINTER_SELECTION, "stable", {
        xrInput: xrHelper.input,
        enablePointerSelectionOnAllControllers: true        
    });
    ```

1. 此外，視起點的位置而定，您可能會發現很難將自己放在鋼琴前面。 如果您熟悉沉浸式 VR 環境，您可能已經知道 **遙傳**，這是一項功能，可讓您藉由指向空間中的另一個位置，立即移至空間中的另一個位置。

1. 為了使用 Babylon.js 的 [遙傳功能](https://doc.babylonjs.com/divingDeeper/webXR/WebXRSelectedFeatures#teleportation-module)，我們必須先有一個可在 VR 空間中「開啟」的地面網格。 將下列程式碼新增至函式 `createScene()` 以建立地面：

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 400, height: 400});
    ```

1. 遙傳支援也隨附一個非常有用的功能，稱為「 [貼齊」位置](https://doc.babylonjs.com/divingDeeper/webXR/WebXRSelectedFeatures#snap-to-hotspots)。 簡單來說，嵌入式管理單元位置是我們希望使用者進入的特定位置。

    例如，我們可以在鋼琴前方設定嵌入式管理單元位置，讓使用者可以在指向靠近鋼琴的指標時輕鬆地傳送至該位置。

    附加下列程式碼來啟用遙傳功能，並指定一個貼齊點：

    ```javascript
    const teleportation = featuresManager.enableFeature(BABYLON.WebXRFeatureName.TELEPORTATION, "stable", {
        xrInput: xrHelper.input,
        floorMeshes: [ground],
        snapPositions: [new BABYLON.Vector3(2.4*3.5*scale, 0, -10*scale)],
    });
    ```

1. 現在，您應該能夠藉由 teleporting 到鋼琴前面的貼齊點，輕鬆地將自己定位在鋼琴前面，您應該能夠使用兩個控制器一次播放兩個按鍵。

    ![遙傳至鋼琴](./images/teleportation-demo.gif)

    ![使用控制器播放鋼琴](./images/play-piano-controller.gif)

## <a name="summary"></a>摘要

恭喜！ 您已完成一連串的 Babylon.js 鋼琴建立教學課程，並瞭解如何：

> [!div class="checklist"]
> * 建立、定位及合併網格以建立鋼琴鍵盤的模型
> * 匯入站立會議鋼琴框架的 Babylon.js 模型
> * 將指標互動新增至每個鋼琴按鍵
> * 根據資料透視點調整網格大小
> * 啟用重要的 WebXR 功能，例如遙傳和 multipointer 支援

以下是 *scene.js* 和 *index.html* 的最終程式碼：

*scene.js*

```javascript
const buildKey = function (scene, parent, props) {
    if (props.type === "white") {
        /*
        Props for building a white key should contain: 
        note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX

        As an example, the props for building the middle C white key would be
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
        */

        // Create bottom part
        const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);

        // Create top part
        const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
        top.position.z =  4.75;
        top.position.x += props.topPositionX;

        // Merge bottom and top parts
        // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
        const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.name = props.note + props.register;
        key.parent = parent;

        return key;
    }
    else if (props.type === "black") {
        /*
        Props for building a black key should contain: 
        note, wholePositionX, register, referencePositionX

        As an example, the props for building the C#4 black key would be
        {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
        */

        // Create black color material
        const blackMat = new BABYLON.StandardMaterial("black");
        blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

        // Create black key
        const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
        key.position.z += 4.75;
        key.position.y += 0.25;
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.material = blackMat;
        key.parent = parent;

        return key;
    }
}

const scaleFromPivot = function(transformNode, pivotPoint, scale) {
    const _sx = scale / transformNode.scaling.x;
    const _sy = scale / transformNode.scaling.y;
    const _sz = scale / transformNode.scaling.z;
    transformNode.scaling = new BABYLON.Vector3(_sx, _sy, _sz); 
    transformNode.position = new BABYLON.Vector3(pivotPoint.x + _sx * (transformNode.position.x - pivotPoint.x), pivotPoint.y + _sy * (transformNode.position.y - pivotPoint.y), pivotPoint.z + _sz * (transformNode.position.z - pivotPoint.z));
}

const createScene = async function(engine) {
    const scale = 0.015;
    const scene = new BABYLON.Scene(engine);

    const alpha =  3*Math.PI/2;
    const beta = Math.PI/50;
    const radius = 220*scale;
    const target = new BABYLON.Vector3(0, 0, 0);

    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);

    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
    light.intensity = 0.6;

    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }

    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});

    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });

    // Lift the piano keyboard
    keyboard.position.y += 80;

    // Scale the entire piano
    scaleFromPivot(piano, new BABYLON.Vector3(0, 0, 0), scale);

    const pointerToKey = new Map()
    const pianoSound = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');

    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                // Only take action if the pointer is down on a mesh
                if(pointerInfo.pickInfo.hit) {
                    let pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    let pointerId = pointerInfo.event.pointerId;
                    if (pickedMesh.parent === keyboard) {
                        pickedMesh.position.y -= 0.5; // Move the key downward
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh,
                            note: pianoSound.play(pointerInfo.pickInfo.pickedMesh.name) // Play the sound of the note
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                let pointerId = pointerInfo.event.pointerId;
                // Only take action if the released pointer was recorded in pointerToKey
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5; // Move the key upward
                    pointerToKey.get(pointerId).note.stop(); // Stop the sound of the note
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });

    const xrHelper = await scene.createDefaultXRExperienceAsync();

    const featuresManager = xrHelper.baseExperience.featuresManager;

    featuresManager.enableFeature(BABYLON.WebXRFeatureName.POINTER_SELECTION, "stable", {
        xrInput: xrHelper.input,
        enablePointerSelectionOnAllControllers: true        
    });

    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 400, height: 400});

    featuresManager.enableFeature(BABYLON.WebXRFeatureName.TELEPORTATION, "stable", {
        xrInput: xrHelper.input,
        floorMeshes: [ground],
        snapPositions: [new BABYLON.Vector3(2.4*3.5*scale, 0, -10*scale)],
    });

    return scene;
}
```

*index.html*

```html
<html>
    <head>
        <title>Babylon Template</title>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <script src="scene.js"></script>
        <script src="soundfont-player.min.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
   <body>
    <canvas id="renderCanvas"></canvas>
    <script>
        const canvas = document.getElementById("renderCanvas"); // Get the canvas element
        const engine = new BABYLON.Engine(canvas, true); // Generate the BABYLON 3D engine

        // Register a render loop to repeatedly render the scene
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

## <a name="next-steps"></a>下一步

如需混合現實 JavaScript 開發的詳細資訊，請參閱 [javascript 開發總覽](/javascript-development-overview.md)。
