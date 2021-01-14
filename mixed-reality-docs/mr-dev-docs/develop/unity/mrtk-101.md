---
title: MRTK 101 - 使用一般空間互動
description: 如何使用混合實境工具組 Unity 進行 HoloLens 2、HoloLens、Windows Mixed Reality 和 Open VR 的基本互動。
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, 混合實境工具組, Windows Mixed Reality, 設計, 範例應用程式, 控制項, 混合實境頭戴式裝置, Windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.localizationpriority: high
ms.openlocfilehash: ff3c6e055bca66fc5ad12548966140af8197235c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008938"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a>MRTK 101：如何使用混合實境工具組 Unity 進行常見的空間互動

![MRTK](images/MRTK101/MRTK101Cover.png)

了解如何使用 MRTK 來實現混合實境中一些最廣泛使用的常見互動模式。

- 如何在 Unity 編輯器中模擬輸入互動？
- 如何抓取和移動物件？
- 如何調整物件大小？
- 如何精確地移動或旋轉物件？
- 如何讓物件回應輸入事件？
- 如何新增視覺回饋？
- 如何新增音訊回饋？
- 如何使用 HoloLens 2 樣式的按鈕 Prefab？
- 如何讓物件跟著您移動？
- 如何讓物件面對您？

> [!NOTE]
> 本文已更新，以便反映 [MRTK v2.5.1 版本](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)中的變更

您可以在 Unity 編輯器中，使用 MRTK 的輸入模擬來測試此頁面中的所有內容。 如果您尚未這麼做，請遵循 [MRTK 安裝指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 以安裝最新版的 MRTK。

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a>如何在 Unity 編輯器中模擬輸入互動？

MRTK 支援編輯器內的輸入模擬。 按一下 Unity 的 [播放] 按鈕來執行場景，然後使用下列按鍵來模擬輸入：
- 按 W、A、S、D 鍵來移動相機。
- 按住滑鼠右鍵並移動滑鼠來瀏覽。
- 按空格鍵 (右手) 或左邊的 Shift 鍵 (左手) 來帶出模擬的雙手
- 按 T 或 Y 鍵讓模擬的雙手保持在視線內
- 按 Q 或 E (水平)/R 或 F (垂直) 來旋轉模擬的雙手

您可以在 [MRTK 文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)中深入了解輸入模擬。

## <a name="how-to-grab-and-move-an-object"></a>如何抓取和移動物件？

附加 **ObjectManipulator.cs** 和 **NearInteractionGrabbable.cs** 指令碼即可讓物件可供抓取。 ObjectManipulator 同時支援遠近互動。 您可以使用 HoloLens 2 的接合手部追蹤輸入 (近處)、手部射線 (遠處)、運動控制器的光束 (遠處)，以及 HoloLens 注視游標和空間點選 (遠處) 來抓取和移動物件。

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a>如何調整物件大小？
**ObjectManipulator.cs** 支援兩手的縮放/旋轉。 此指令碼適用於各種輸入類型，例如 HoloLens 2 的接合手部輸入、HoloLens 1 的注視 + 手勢輸入，以及 Windows Mixed Reality 沉浸式頭戴裝置的動作控制器輸入。

- [在 MRTK 文件中深入了解 Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>如何精確地移動或旋轉物件？
將 **BoundsControl.cs** 指派給物件以使用周框方塊，也就是用來縮放和旋轉物件的介面。 根據預設，其會顯示 HoloLens 1 樣式的藍色控點和連接線。 若要使用 HoloLens 2 樣式的鄰近動畫控點，您必須指派 Prefab 和材質。 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [在 MRTK 文件中深入了解邊界控制項](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a>如何讓物件回應輸入事件？
將 **PointerHandler.cs** 指派給物件。 在偵測器中，您可以使用 OnPointerDown()、OnPointerUp()、OnPointerClicked()、OnPointerDragged() 事件。若要在指令碼中使用這些事件，請實作 **IMixedRealityPointerHandler**。

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [在 MRTK 文件中深入了解輸入系統](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>如何新增視覺回饋？
將 **Interactable.cs** 指派給物件。 在偵測器中新增目標物件並建立新的主題。 您可以使用 Interactable (可互動) 的主題設定檔，輕鬆地在所有可用的輸入互動狀態中新增視覺回饋。

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable 提供各種主題類型，包括著色器主題，該主題可讓您控制每個互動狀態的著色器屬性。

- [在 MRTK 文件中深入了解 Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

視覺化回饋的另一個重要組成要素是 **MRTK 標準著色器**。 透過 MRTK 標準著色器，您可以輕鬆地加入視覺回饋效果，例如暫留光源和鄰近光源。 由於 MRTK 標準著色器執行的計算比 Unity 標準著色器少，因此可讓您建立高效能的體驗。

建立新的材質，然後選取著色器的 [混合實境工具組] > [標準]。 或者，您可以挑選其中一個使用 MRTK 標準著色器的現有材質。

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [在 MRTK 文件中深入了解 MRTK 標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>如何新增音訊回饋？
將 **AudioSource** 新增至物件。 然後，在公開輸入事件 (例如 Interactable.cs 或 PointerHandler.cs) 的指令碼中，將具有 AudioSource 的物件指派給事件，然後選取 [AudioSource.PlayOneShot()]。 您可以使用您的音訊片段，或從 MRTK 的音訊資產中選擇一個。

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a>如何使用 HoloLens 2 樣式的按鈕 Prefab？
MRTK 提供各種類型的 HoloLens 2 命令介面 (OS) 樣式按鈕，其中包括視覺回饋，例如鄰近光源、壓縮方塊和按鈕表面上的漣波效果，可改善使用者的信賴度。

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

將其中一個 **HoloLens 2 樣式的可點按按鈕 Prefab** 拖放到您的場景中即可。 Prefab 會使用上方介紹的 Interactable.cs。 您可以在 Interactable 中使用公開的事件 例如 (OnClick()) 來觸發動作。

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [在 MRTK 文件中深入了解按鈕 Prefab](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a>如何讓物件跟著您移動？
將 **RadialView.cs** 或 **Follow.cs** 指令碼指派給物件。 這是 Solver (解算器) 指令碼系列的一部分，可讓您在 3D 空間中實現各種物件類型的定位。 **SolverHandler.cs** 將會自動新增。
以下是使用 RadialView 設定達到 'lazy follow' 常駐標籤行為的範例，就像是 HoloLens 命令介面中的 [開始] 功能表。 您可以指定最小/最大距離和最小/最大檢視角度。 下列範例顯示物件在 0.4 m 和 0.8 m 範圍之間的 15° 檢視。 調整 Lerp 時間值，讓位置更新的速度更快或更慢。

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [在 MRTK 文件中深入了解 Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a>如何讓物件面對您？
將 **Billboard.cs** 指令碼指派給物件。 無論您的位置在哪，物件都會面對您。 您可以指定樞紐軸選項。

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


準備好建立混合實境的絕佳體驗了嗎？ 請瀏覽下列頁面，並深入了解 MRTK 和混合實境。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX 設計者 @Microsoft</td>
</tr>
</table>

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unity 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊： 

> [!div class="nextstepaction"]
> [相機](camera-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [MRTK 安裝指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [混合實境工具組-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK 文件入口網站 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [HoloToolkit 至 MRTK 的移植指導方針](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
