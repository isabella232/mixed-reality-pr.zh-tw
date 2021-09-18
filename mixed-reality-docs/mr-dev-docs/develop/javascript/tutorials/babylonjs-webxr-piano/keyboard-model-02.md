---
title: 建立3D 鋼琴模型
description: 瞭解如何使用 Babylon.js 撰寫程式碼來建立3D 鋼琴模型
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: mixed reality、javascript、教學課程、BabylonJS、hololens、mixed reality、UWP、Windows 10、WebXR、沉浸式網路
ms.localizationpriority: high
ms.openlocfilehash: e5c3dd6206566f781ceb52e5d13a49a0c9ab1018
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932504"
---
# <a name="tutorial-build-a-3d-piano-model"></a>教學課程：建立3D 鋼琴模型

在此系列的上一個教學課程中，我們設定了一個網頁，其中包含具有相機和燈光的 Babylon.js 場景。 在本教學課程中，我們將會在場景中建立並新增鋼琴模型。

![站立會議鋼琴網格](./images/standup-piano-mesh.png)

在本教學課程中，您將學會如何：

> [!div class="checklist"]
> * 建立、定位和合併網格
> * 從 box 網格建立鋼琴鍵盤
> * 匯入鋼琴框架的3D 模型

## <a name="before-you-begin"></a>開始之前

請確定您已完成 [本系列中的前一個教學](introduction-01.md) 課程，並已準備好繼續新增至程式碼。

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

## <a name="getting-started"></a>開始使用

首先，讓我們先建立一個具有下列結構的簡單鋼琴鍵盤：

![鋼琴註冊描述](./images/piano-register.jpg)

在此影像中，有7個白鍵和5個黑色按鍵，每個都標示筆記的名稱。 完整的 88-按鍵的大鋼琴鍵盤包含7個金鑰選取專案的完整重複 (也稱為註冊) 和4個額外的金鑰。 每個註冊程式都有兩倍的上一次註冊。 例如，C5 的音調頻率 (這表示第五個註冊) 中的 C 附注是雙 C4's、D5's 的音調頻率是 D4's 的雙精度浮點數。

每個註冊的視覺效果看起來完全相同，因此我們可以開始調查如何使用這項索引鍵來建立簡單的鋼琴鍵盤。 稍後，我們可以找到將範圍擴充至 88-key 全鋼琴鍵盤的方法。

## <a name="build-a-simple-piano-keyboard"></a>建立簡單的鋼琴鍵盤

> [!NOTE]
> 雖然可以從線上來源尋找多個鋼琴鍵盤的3D 模型，並將其匯入我們的網頁中，但我們將在本教學課程中從頭開始建立鍵盤，以允許最大自訂能力，並展示如何透過 Babylon.js 建立3D 模型。

1. 在開始建立用來建立鍵盤的任何網格之前，請注意每個黑色按鍵都不會在它周圍兩個白色按鍵的中間對齊，而且並非每個按鍵都有相同的寬度。 這表示我們必須針對每個金鑰個別建立並放置網格。

    ![黑色按鍵對齊](./images/black-key-position.png)

1. 針對白色鍵，我們可以觀察每個白色按鍵是由兩個部分組成： (1) 黑色索引鍵 (的下半部，) 和 (2) 黑色索引鍵 () 旁的上半部。 這兩個部分具有不同的維度，但會堆疊在一起以建立完整的白色鍵。

    ![白色按鍵圖形](./images/white-key-shape-label.png)

1. 以下是針對附注 C 建立單一白色按鍵的程式碼 (不需要擔心將它新增至 *scene.js* 但) ：

    ```javascript
    const whiteKeyBottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: 2.3, height: 1.5, depth: 4.5}, scene);
    const whiteKeyTop = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: 1.4, height: 1.5, depth: 5}, scene);
    whiteKeyTop.position.z += 4.75;
    whiteKeyTop.position.x -= 0.45;

    // Parameters of BABYLON.Mesh.MergeMeshes:
    // (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
    const whiteKeyV1 = BABYLON.Mesh.MergeMeshes([whiteKeyBottom, whiteKeyTop], true, false, null, false, false);
    whiteKeyV1.material = whiteMat;
    whiteKeyV1.name = "C4";
    ```

    在這裡，我們建立了兩個 [Box](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box#box-mesh) 網格，一個用於下半部，另一個用於白色鍵的上半部。 接著，我們會修改上半部的位置，以將其堆疊在下半部，並將其移到左方，以保留鄰近黑色按鍵的空間 (c # ) 。

    最後，這兩個部分已使用 [MergeMeshes](https://doc.babylonjs.com/divingDeeper/mesh/mergeMeshes) 函式合併成為一個完整的白色索引鍵。 這是此程式碼會產生的網格結果：

    ![白鍵 C](./images/white-key-c.png)

1. 建立黑色按鍵比較簡單。 因為所有的黑色按鍵都是方塊的形狀，所以只要建立具有黑色色彩 [StandardMaterial](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction#color)的方塊網格，就可以建立黑色按鍵。

    > [!NOTE]
    > 由於預設的網格色彩是類似白色的淺灰色，因此本教學課程不包含將白色色彩材質新增至白色鍵的步驟。 但是，如果您想要在白色按鍵上使用真正的白色色彩，請隨意新增材質。

    以下是建立黑色按鍵 c # 的程式碼 (不必擔心將此程式碼新增至 *scene.js*) ：

    ```javascript
    const blackMat = new BABYLON.StandardMaterial("black");
    blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

    const blackKey = BABYLON.MeshBuilder.CreateBox("C#4", {width: 1.4, height: 2, depth: 5}, scene);
    blackKey.position.z += 4.75;
    blackKey.position.y += 0.25;
    blackKey.position.x += 0.95;
    blackKey.material = blackMat;
    ```

    此程式碼所產生的黑色金鑰 (與上一個白色按鍵) 看起來像這樣：

    ![黑色按鍵 C#](./images/black-key-csharp.png)

1. 如您所見，建立每個金鑰可能會產生很多類似的程式碼，因為我們必須指定每個維度和位置。 在下一節中，讓我們試著讓建立程式更有效率。

## <a name="build-a-simple-piano-keyboard-efficiently"></a>有效率地打造簡單的鋼琴鍵盤

1. 雖然每個白色按鍵的形狀稍微不同，但它們都可以藉由合併上半部和下半部來建立。 讓我們執行泛型函式來建立並放置任何白色按鍵。

    將下列函式新增至函式外部 *scene.js* `createScene()` ：

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
    }
    ```

    在此程式碼區塊中，我們建立了名為的函式 `buildKey()` ，如果是，則會建立並傳回白色鍵 `props.type` `"white"` 。 藉由在參數中識別索引鍵的類型 `props` ，我們可以在相同函式中建立黑色索引鍵和白色鍵，方法是使用 if 語句進行分支。

    的參數為 `buildKey()` ：
    * **場景**：機碼所在的場景
    * **parent**：網格的父系 (這可讓我們將所有索引鍵群組在一起，成為單一父系) 
    * **.props**：將建立之索引鍵的屬性

    `props`白鍵的會包含下列專案：
    * **類型**： "白色"
    * **名稱**：索引鍵代表的附注名稱
    * **topWidth**：上半部的寬度
    * **bottomWidth**：下半部的寬度
    * **topPositionX**：相對於下半部的最上層位置的 x 位置
    * **wholePositionX**：相對於暫存器結束點的整個索引鍵的位置， (機碼 B) 的右邊緣。
    * **註冊**：註冊金鑰所屬的 (介於0和8之間的數位) 
    * **referencePositionX**：用來做為參考點) 的註冊 (結束點的 x 座標。

    藉由分隔 `wholePositionX` 和 `referencePositionX` ，我們可以初始化 `props` 建立特定類型的金鑰 (所需的參數，例如在任何暫存器中的 C) ，然後在 `register` (特定暫存器中（ `referencePositionX` `props` 例如 c4、c5) ）建立該金鑰時，將加入和新增至。

1. 同樣地，我們也可以撰寫泛型函數來建立黑色按鍵。 讓我們展開 `buildKey()` 函數以包含該邏輯：

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
    ```

    黑色索引鍵的會 `props` 包含下列專案：

    * **類型**： "黑色"
    * **名稱**：索引鍵代表的附注名稱
    * **wholePositionX**：相對於註冊結束點的整個索引鍵的位置， (索引鍵 B 的右邊緣) 
    * **註冊**：註冊金鑰所屬的 (介於0和8之間的數位) 
    * **referencePositionX**：用來做為參考點) 的註冊 (結束點的 x 座標。

    `props`建立黑色按鍵的是很簡單的動作，因為建立黑色按鍵只需要建立一個方塊，且每個黑色按鍵的寬度和 z 位置都相同。

1. 既然我們有更有效率的金鑰建立方式，讓我們初始化一個陣列來儲存對應至暫存器 `props` 中某個附注的每個索引鍵，然後使用每個索引鍵呼叫函式， `buildKey()` 以在第4個註冊中建立簡單的鍵盤。

    我們也會建立名為的 [TransformNode](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/transform_node#a-transformnode) `keyboard` ，作為所有鋼琴按鍵的 [父系](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/parent#overview-of-a-parent) 。 由於套用至父系的任何位置或調整變更也會套用至子系，因此以這種方式分組索引鍵可讓我們進行調整，或將它們全部移動。

    在函式中附加下列程式程式碼 `createScene()` ：

    ```javascript
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

    keyParams.forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
    })
    ```

    您可能已經注意到，在此程式碼區塊中，我們會將所有的索引鍵相對於空間的原點進行放置。

1. 以下是目前為止 *scene.js* 包含的程式碼：

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
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
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
    
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
        })

        const xrHelper = await scene.createDefaultXRExperienceAsync();

        return scene;
    }
    ```

1. 結果鍵盤看起來像這樣：

    ![使用一個註冊的鋼琴鍵盤](./images/piano-one-register.png)

## <a name="expanding-to-an-88-key-piano"></a>擴充至 88-關鍵的鋼琴

在本節中，我們將擴充金鑰建立函式的使用方式，以產生完整的 88-鑰匙鋼琴鍵盤。

1. 如先前所述，完整的 88-按鍵鋼琴鍵盤包含7個重複的暫存器和其他4個注意事項。 其中3個額外的附注是在 [暫存器 0] (左邊的鍵盤) ，而1則是在鍵盤) 的 [註冊 8] (右端。

    ![88-關鍵的鋼琴版面配置](./images/88-key-piano-keyboard-layout.jpg)

1. 我們將在稍早撰寫的迴圈周圍新增額外的迴圈，以建立7次完整的重複作業。 以下列程式碼取代函式的先前迴圈 `buildKey()` ：

    ```javascript
    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }
    ```

    在此迴圈中，我們會建立註冊1到7的金鑰，並在每次我們移至下一個註冊時，遞增參考位置。

1. 接下來，讓我們建立其餘的金鑰。 將下列程式碼片段新增至函式 `createScene()` ：

    ```javascript
    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    ```

    請注意，最左邊的索引鍵和鋼琴鍵盤最右邊的按鍵不適合 (中定義的 .props 維度 `keyParams` ，因為它們不在邊緣) 的黑色按鍵旁邊，因此我們必須為每個專案定義新的 `props` 物件，以指定其特殊圖形。

1. 在進行變更後，所產生的鍵盤應該如下所示：

    ![全鋼琴鍵盤網格](./images/full-keyboard-mesh.png)

## <a name="adding-a-piano-frame"></a>新增鋼琴框架

1. 場景看起來有點奇怪，只是在空間中浮動鍵盤。 讓我們在鍵盤周圍新增一個鋼琴框架，以建立站立會議鋼琴的外觀。

1. 與我們建立索引鍵的方式類似，我們也可以藉由定位和組合一組方塊網格來建立框架。

    不過，我們會讓您自行嘗試，並使用 BABYLON 來進行這項挑戰 [。SceneLoader. ImportMesh](https://doc.babylonjs.com/divingDeeper/importers/loadingFileTypes#sceneloaderimportmesh) 以匯入站立會議鋼琴框架的預先製作的網格。 將這段程式碼附加至 `createScene()` ：

    ```javascript
    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });
    ```

    請注意，我們也會建立一個名為的父代，將 `TransformNode` `piano` 鍵盤和框架全部群組在一起。 如果需要的話，這會讓整個鋼琴的移動或調整變得更容易。

1. 匯入框架之後，請注意鍵盤會位於框架 (的底部，因為索引鍵的 y 座標預設是0，) 。 讓我們將鍵盤放在站立會議的鋼琴框架中：

    ```javascript
    // Lift piano keys
    keyboard.position.y += 80;
    ```

    由於 `keyboard` 是所有鋼琴按鍵的父系，因此只要變更的 y 位置，就可以提起所有的鋼琴按鍵 `keyboard` 。

1. 最後的 *scene.js* 程式碼看起來應該像這樣：

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

1. 現在應該會有一個站立會議的鋼琴，看起來像這樣： ![ 站立會議鋼琴網格](./images/standup-piano-mesh.png)

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [下一個教學課程：播放3D 鋼琴](keyboard-interaction-03.md)
