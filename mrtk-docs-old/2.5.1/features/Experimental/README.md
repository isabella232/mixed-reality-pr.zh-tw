---
title: MRTK_Documentation
description: MRTK 使用者入門檔頁面
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: f73bea6bcb56993fbb6bab589f267136de8e2cc8
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779604"
---
## <a name="what-is-the-mixed-reality-toolkit"></a>何謂混合現實工具組

![混合實境工具組](../images/Logo_MRTK_Unity_Banner.png)

MRTK-Unity 是由 Microsoft 所推動的專案，其提供一組元件與功能，可用來加快 Unity 中的跨平台 MR 應用程式開發。 以下是其中的一些功能：

* 提供 **空間互動和 UI 的跨平臺輸入系統和建立區塊**。
* 透過可讓您立即查看變更的編輯器內模擬，讓您能夠 **快速建立原型** 。
* 以可擴充的 **架構** 運作，讓開發人員能夠交換核心元件。
* **支援多種平臺**，包括
  * Microsoft HoloLens
  * Microsoft HoloLens 2
  * Windows Mixed Reality 頭戴式裝置
  * OpenVR 頭戴式裝置 (HTC Vive / Oculus Rift)
  * Ultraleap 手部追蹤
  * IOS 和 Android 等行動裝置

## <a name="getting-started-with-mrtk"></a>開始使用 MRTK

如果您不熟悉 Unity 中的 MRTK 或混合現實開發， **我們建議您** 從 Microsoft 檔中的 [unity 開發旅程](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2) 開始著手。Unity 開發旅程是特別量身打造的，可透過安裝、核心概念和 MRTK 的使用方式來引導新的開發人員。

| 重要： Unity 開發旅程目前使用 **MRTK 版本 2.4.0** 和 **Unity 2019.4**。 |
| --- |

如果您是有經驗的混合現實或 MRTK 開發人員，請參閱下一節中的連結，以取得最新的套件和版本資訊。

## <a name="documentation"></a>文件

| [![版本資訊](../images/MRTK_Icon_ReleaseNotes.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/../ReleaseNotes.html)<br/>[版本資訊](https://microsoft.github.io/MixedRealityToolkit-Unity/../ReleaseNotes.html)| [![MRTK 總覽](../images/MRTK_Icon_ArchitectureOverview.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/../Architecture/Overview.html)<br/>[MRTK 總覽](https://microsoft.github.io/MixedRealityToolkit-Unity/../Architecture/Overview.html)| [![功能指南](../images/MRTK_Icon_FeatureGuides.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/../ux-building-blocks/Button.html)<br/>[功能指南](https://microsoft.github.io/MixedRealityToolkit-Unity/../ux-building-blocks/Button.html)| [![API 參考](../images/MRTK_Icon_APIReference.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)<br/>[API 參考](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)|
|:---|:---|:---|:---|

## <a name="build-status"></a>組建狀態

| 分支 | CI 狀態 | 檔狀態 |
|---|---|---|
| `mrtk_development` |[![CI 狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![檔狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="required-software"></a>必要的軟體

 | [ ![ Windows sdk 18362 +](../images/MRTK170802_Short_17.png)](https://developer.microsoft.com/windows/downloads/windows-10-sdk) [windows sdk 18362 +](https://developer.microsoft.com/windows/downloads/windows-10-sdk)| [ ![ Unity](../images/MRTK170802_Short_18.png)](https://unity3d.com/get-unity/download/archive) [unity 2018.4. x](https://unity3d.com/get-unity/download/archive)| [ ![ Visual studio 2019](../images/MRTK170802_Short_19.png)](http://dev.windows.com/downloads) [visual studio 2019](http://dev.windows.com/downloads)| [ ![ 模擬器 (選擇性的) ](../images/MRTK170802_Short_20.png)](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator) [模擬器 (選擇性) ](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator)|
| :--- | :--- | :--- | :--- |
| 若要使用 MRTK v2 來建立應用程式，您需要 Windows 10 2019 版 Update SDK。 <br> 若要執行沉浸式耳機的應用程式，您需要 Windows 10 秋季建立者更新。 | Unity 3D 引擎提供在 Windows 10 中建立混合現實專案的支援 | Visual Studio 可用於程式碼編輯、部署和建立 UWP 應用程式套件 | 模擬器可讓您測試應用程式，而不需要在模擬環境中使用裝置 |

## <a name="feature-areas"></a>功能範圍

| ![輸入系統 ](../images/MRTK_Icon_InputSystem.png) [輸入系統](../input/Overview.md)<br/>&nbsp;  | ![手動追蹤<br/> (HoloLens 2) ](../images/MRTK_Icon_HandTracking.png) [手動追蹤 <br/> (hololens 2) ](../input/HandTracking.md) | ![眼睛追蹤<br/> (HoloLens 2) ](../images/MRTK_Icon_EyeTracking.png) [眼睛追蹤 <br/> (hololens 2) ](../eye-tracking/EyeTracking_Main.md) | ![設定檔 ](../images/MRTK_Icon_Profiles.png) [設定檔](../../configuration/MixedRealityConfigurationGuide.md)<br/>&nbsp; | ![手動追蹤<br/> (Ultraleap) ](../images/MRTK_Icon_HandTracking.png) [手動追蹤 (Ultraleap) ](../cross-platform/LeapMotionMRTK.md)|
| :--- | :--- | :--- | :--- | :--- |
| ![UI 控制項 ](../images/MRTK_Icon_UIControls.png) [ui 控制項](README.md#ux-building-blocks)<br/>&nbsp; | ![解析器 ](../images/MRTK_Icon_Solver.png) [解析器](../ux-building-blocks/solvers/Solver.md)<br/>&nbsp; | ![多場景<br/> Manager ](../images/MRTK_Icon_SceneSystem.png) [多場景 <br/> 管理員](../scene-system/SceneSystemGettingStarted.md) | ![空間<br/> 認知 1 ](../images/MRTK_Icon_SpatialUnderstanding.png) [空間 <br/> 感知 2](../spatial-awareness/SpatialAwarenessGettingStarted.md) | ![診斷<br/> 工具 ](../images/MRTK_Icon_Diagnostics.png) [診斷 <br/> 工具](../diagnostics/DiagnosticsSystemGettingStarted.md) |
| ![MRTK Standard Shader1 ](../images/MRTK_Icon_StandardShader.png) [MRTK standard Shader2](../rendering/MRTKStandardShader.md?q=shader) | ![語音 & 聽寫 ](../images/MRTK_Icon_VoiceCommand.png) [語音](../input/Speech.md)<br/> & [聽寫](../input/Dictation.md) | ![界限<br/>系統 ](../images/MRTK_Icon_Boundary.png) [界限 <br/> 系統](../boundary/BoundarySystemGettingStarted.md)| ![編輯器內<br/>模擬 ](../images/MRTK_Icon_InputSystem.png) [編輯器內 <br/> 模擬](../input-simulation/InputSimulationService.md) | ![實驗性<br/>功能 ](../images/MRTK_Icon_Experimental.png) [實驗性 <br/> 功能](../../contributing/ExperimentalFeatures.md)|

## <a name="ux-building-blocks"></a>UX 組建區塊

|  [ ![ 按鈕](../images/Button/MRTK_Button_Main.png)](../ux-building-blocks/Button.md)[按鈕](../ux-building-blocks/Button.md) | [ ![ 界限控制項](../images/bounds-control/MRTK_BoundsControl_Main.png)](../ux-building-blocks/BoundsControl.md)[界限控制項](../ux-building-blocks/BoundsControl.md) | [ ![ 物件](../images/manipulation-handler/MRTK_Manipulation_Main.png)](../ux-building-blocks/ObjectManipulator.md)操作工具[物件](../ux-building-blocks/ObjectManipulator.md)操作工具 |
|:--- | :--- | :--- |
| 支援各種輸入方法的按鈕控制項，包括 HoloLens 2 的明確表述 | 在3D 空間中操作物件的標準 UI | 以一或兩個手中操作物件的腳本 |
|  [ ![ 平板](../images/slate/MRTK_Slate_Main.png)](../ux-building-blocks/Slate.md)[平板](../ux-building-blocks/Slate.md) | [ ![ 系統鍵盤](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)](../ux-building-blocks/SystemKeyboard.md)[系統鍵盤](../ux-building-blocks/SystemKeyboard.md) | [ ![ 互動](../images/Interactable/InteractableExamples.png)](../ux-building-blocks/Interactable.md)[互動](../ux-building-blocks/Interactable.md) |
| 2D 樣式平面，支援以已明確表達的手寫輸入進行滾動 | 在 Unity 中使用系統鍵盤的範例腳本  | 使用視覺狀態和主題支援讓物件互動的腳本 |
|  [ ![ 規劃](../images/solver/MRTK_Solver_Main.png)](../ux-building-blocks/solvers/Solver.md)求解[規劃](../ux-building-blocks/solvers/Solver.md) | [ ![ 物件集合](../images/object-collection/MRTK_ObjectCollection_Main.jpg)](../ux-building-blocks/ObjectCollection.md)[物件集合](../ux-building-blocks/ObjectCollection.md) | [ ![ 工具](../images/Tooltip/MRTK_Tooltip_Main.png)](../ux-building-blocks/Tooltip.md)提示[工具提示](../ux-building-blocks/Tooltip.md) |
| 各種物件定位行為，例如標記-沿著標記、主體鎖定、常數視圖大小和表面磁性 | 在三維圖形中設定物件陣列的腳本 | 具有彈性錨點/pivot 系統的注釋 UI，可用來標記動作控制器和物件 |
|  [ ![ 滑杆](../images/Slider/MRTK_UX_Slider_Main.jpg)](../ux-building-blocks/Sliders.md)[滑杆](../ux-building-blocks/Sliders.md) | [ ![ MRTK 標準著色器](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)](../rendering/MRTKStandardShader.md) [MRTK 標準著色器](../rendering/MRTKStandardShader.md) | [ ![ 手形功能表](../images/solver/MRTK_UX_HandMenu.png)](../ux-building-blocks/Handmenu.md)[功能表](../ux-building-blocks/Handmenu.md) |
| 調整支援直接追蹤互動之值的滑杆 UI | MRTK 的標準著色器可支援各種流暢的設計項目與效能 | 使用手形條件約束規劃的手動鎖定 UI，以進行快速存取 |
|  [ ![ 應用程式行](../images/app-bar/MRTK_AppBar_Main.png)](../ux-building-blocks/AppBar.md)[應用程式行](../ux-building-blocks/AppBar.md) | [ ![ 指標](../images/Pointers/MRTK_Pointer_Main.png)](../input/Pointers.md)[指標](../input/Pointers.md) | [ ![ Fingertip 視覺效果](../images/fingertip/MRTK_FingertipVisualization_Main.png)](../ux-building-blocks/FingertipVisualization.md) [Fingertip 視覺效果](../ux-building-blocks/FingertipVisualization.md) |
| 界限控制項手動啟用的 UI | 瞭解各種類型的指標 | Fingertip 上的視覺效果 affordance，可改善直接互動的信賴度 |
|  接近[ ![ Menu1](../images/near-menu/MRTK_UX_NearMenu.png)](../ux-building-blocks/NearMenu.md) [近 Menu2](../ux-building-blocks/NearMenu.md) | [ ![ 空間感知](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](../spatial-awareness/SpatialAwarenessGettingStarted.md)[空間感知](../spatial-awareness/SpatialAwarenessGettingStarted.md) | [ ![ 語音命令](../images/Input/MRTK_Input_Speech.png)](../input/Speech.md)[語音命令](../input/Speech.md)  /  [聽寫](../input/Dictation.md) |
| 接近互動的浮動功能表 UI | 讓您的全像攝影物件與實體環境互動 | 整合語音輸入的腳本和範例 |
|  [ ![ 進度指示器](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)](../ux-building-blocks/ProgressIndicator.md)[進度指標](../ux-building-blocks/ProgressIndicator.md) | [ ![ 對話方塊](../images/dialog/MRTK_UX_Dialog_Main.png)](dialog/dialog.md)[對話方塊 [實驗]](dialog/dialog.md) | [ ![ 手動教練](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](hand-coach/HandCoach.md)[指導 [實驗]](hand-coach/HandCoach.md) |
| 用於傳達資料處理或作業的視覺化指標 | 要求使用者確認或確認的 UI  | 當手勢未教授時，可協助引導使用者的元件 |
|  [ ![ 手物理服務](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](hand-physics-service/README.md)的[物理服務 [實驗]](hand-physics-service/README.md) | [ ![ 滾動集合](../images/scrolling-collection/ScrollingCollection_Main.jpg)](../ux-building-blocks/ScrollingObjectCollection.md)[滾動集合](../ux-building-blocks/ScrollingObjectCollection.md) | [ ![ ](../images/dock/MRTK_UX_Dock_Main.png)](dock/Dock.md)停駐[固定 [實驗]](dock/Dock.md) |
| 實際的物理服務可讓您透過明確的方式進行固定的內文衝突事件和互動 | 原生滾動3D 物件的物件集合 | Dock 允許將物件移入和移出預定的位置 |
|  [ ![ 眼睛追蹤：目標選擇](../images/eye-tracking/mrtk_et_targetselect.png)](../eye-tracking/EyeTracking_TargetSelection.md)[眼睛追蹤：目標選取範圍](../eye-tracking/EyeTracking_TargetSelection.md) | [ ![ 眼睛追蹤：導覽](../images/eye-tracking/mrtk_et_navigation.png)](../eye-tracking/EyeTracking_Navigation.md)[眼睛追蹤：導覽](../eye-tracking/EyeTracking_Navigation.md) | [ ![ 眼睛追蹤：熱度圖](../images/eye-tracking/mrtk_et_heatmaps.png)](../eye-tracking/EyeTracking_ExamplesOverview.md#visualization-of-visual-attention)[視覺追蹤：熱度圖](../eye-tracking/EyeTracking_ExamplesOverview.md#visualization-of-visual-attention) |
| 結合眼睛、語音和手輸入，以快速且輕鬆地在場景中選取全像影像 | 瞭解如何根據您要查看的內容，自動滾動文字或流暢縮放至焦點內容 | 記錄、載入和視覺化使用者在您的應用程式中查看的範例 |

## <a name="tools"></a>工具

|  [ ![ 優化視窗](../images/MRTK_Icon_OptimizeWindow.png)](../tools/OptimizeWindow.md)[優化視窗](../tools/OptimizeWindow.md) | 相依性[ ![ 視窗](../images/MRTK_Icon_DependencyWindow.png)](../tools/DependencyWindow.md)相依性[視窗](../tools/DependencyWindow.md) | ![組建視窗](../images/MRTK_Icon_BuildWindow.png) 組建視窗 | [ ![ 輸入錄製](../images/MRTK_Icon_InputRecording.png)](../input-simulation/InputAnimationRecording.md)[輸入記錄](../input-simulation/InputAnimationRecording.md) |
|:--- | :--- | :--- | :--- |
| 自動設定混合現實專案以進行效能優化 | 分析資產之間的相依性，並找出未使用的資產 |  設定及執行混合現實應用程式的端對端組建程式 | 在編輯器中錄製並播放前端移動和手動追蹤資料 |

## <a name="example-scenes"></a>範例場景

探索 MRTK 在 [此範例場景](../example-scenes/HandInteractionExamples.md)中的各種互動和 UI 控制項類型。

您可以在 [資產/MixedRealityToolkit] 下找到其他範例場景 [**。範例/示範**](/Assets/MixedRealityToolkit.Examples/Demos) 資料夾。

[![範例場景1](../images/MRTK_Examples.png)](../example-scenes/HandInteractionExamples.md)

## <a name="mrtk-examples-hub"></a>MRTK 範例中樞

您可以使用 MRTK 範例中樞來嘗試 MRTK 中的各種範例場景。
您可以在 [ [**發行資產**](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0) ] 資料夾下找到 HoloLens (x86) 、hololens 2 (ARM) 和 Windows Mixed Reality 沉浸式耳機 (x64) 的預先建立應用程式套件。 [使用 Windows 裝置入口網站在 HoloLens 上安裝應用程式](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)。 在 HoloLens 2 上，您可以 [透過 Microsoft Store 應用程式下載並安裝 MRTK 範例中樞](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)。

請參閱 [範例中樞的讀我檔案頁面](../example-scenes/ExampleHub.md) ，以瞭解如何使用 MRTK 的場景系統和場景轉換服務建立多場景中樞的詳細資料。

[![範例場景2](../images/MRTK_ExamplesHub.png)](../example-scenes/HandInteractionExamples.md)

## <a name="sample-apps-made-with-mrtk"></a>使用 MRTK 建立的範例應用程式

| [![元素1的定期資料表](../images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![星系探險](../images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)| [![Galaxy Explorer 1](../images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)|
|:--- | :--- | :--- |
| 專案[2 的定期表格](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)是開放原始碼範例應用程式，示範如何使用 MRTK 的輸入系統和建立區塊來建立 HoloLens 和沉浸式耳機的應用程式體驗。 閱讀移植案例： [使用 MRTK v2 將專案應用程式的定期資料表帶入 HoloLens 2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) 是一種開放原始碼範例應用程式，最初是在2016年3月的「分享您的想法」活動中所開發。 已使用 MRTK v2 以 HoloLens 2 的新功能更新 Galaxy Explorer。 閱讀案例： [適用于 HoloLens 2 的 Galaxy Explorer 製作](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update) |[表面](https://github.com/Microsoft/GalaxyExplorer) 是適用于 HoloLens 2 的開放原始碼範例應用程式，它會探索如何使用視覺效果、音訊和完全明確的手動追蹤來建立 tactile 刺痛。 查看 Microsoft MR Dev Days session [學習 from surface 應用程式](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) ，以取得詳細的設計和開發案例。 |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>來自混合現實開發日2020的研討會影片

| [![MRDevDays 1](../images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 2](../images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 3](../images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| 如何建立從開始到完成的簡單 MRTK 應用程式的教學課程。 瞭解互動概念和 MRTK 的多平臺功能。 | 深入探討 MRTK 的 UX 構成要素，協助您打造美觀的混合現實體驗。 | MRTK 和外部的效能工具簡介，以及 MRTK 標準著色器的總覽。    |

若要探索更多課程影片，請參閱 [混合現實開發日](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) 。

## <a name="engage-with-the-community"></a>與社區互動

* 在 MRTK 上加入關於 [時差](https://holodevelopers.slack.com/)的交談。 您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。

* 使用 **MRTK** 標記詢問有關使用 MRTK On [Stack 溢](https://stackoverflow.com/questions/tagged/mrtk)位的問題。

* 如果您發現 MRTK 程式碼中有問題，請搜尋 [已知問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 或提出 [新問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 。

* 如有關于參與 MRTK 的問題，請移至「 [混合現實」工具](https://holodevelopers.slack.com/messages/C2H4HT858) 組頻道的時差。

此專案採用了 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/)。
如需詳細資訊，請參閱[管理辦法常見問題集](https://opensource.microsoft.com/codeofconduct/faq/)，如有其他問題或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>混合現實開發人員中心上的實用資源

| ![探索 ](../images/mrdevcenter/icon-discover.png) [探索](https://docs.microsoft.com/windows/mixed-reality/)| ![設計 ](../images/mrdevcenter/icon-design.png) [設計](https://docs.microsoft.com/windows/mixed-reality/design)| ![開發 ](../images/mrdevcenter/icon-develop.png) [開發](https://docs.microsoft.com/windows/mixed-reality/development)| ![散發) ](../images/mrdevcenter/icon-distribute.png) [散發](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| 瞭解如何建立 HoloLens 和沉浸式耳機的混合現實體驗 (VR) 。          | 取得設計指南。 建立使用者介面。 瞭解互動和輸入。     | 取得開發指南。 學習技術。 瞭解科學。       | 準備好您的應用程式以供其他人使用，並考慮建立 3D 啟動器。 |

## <a name="useful-resources-on-azure"></a>Azure 上的實用資源

| ![Spatial Anchors](../images/mrdevcenter/icon-azurespatialanchors.png)<br> [Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/)| ![語音服務](../images/mrdevcenter/icon-azurespeechservices.png) [語音服務](https://docs.microsoft.com/azure/cognitive-services/speech-service/)| ![視覺服務 ](../images/mrdevcenter/icon-azurevisionservices.png) [視覺服務](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| 空間錨點是一種跨平臺服務，可讓您使用在一段時間內跨裝置保存其位置的物件，建立混合的現實體驗。| 探索及整合 Azure 提供的語音功能，例如語音轉換文字、說話者辨識或語音翻譯至您的應用程式。| 使用視覺服務識別並分析您的影像或視訊內容，例如電腦視覺、臉部偵測、表情辨識或影片索引器。 |

## <a name="learn-more-about-the-mrtk-project"></a>深入瞭解 MRTK 專案

您可以在 [專案管理] 區段下的 [wiki](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki) 中找到我們的規劃內容。 您永遠可以在反復專案計劃問題中看到小組正在積極處理的專案。

## <a name="how-to-contribute"></a>如何參與

瞭解您[如何參與 MRTK 的貢獻。](../../contributing/CONTRIBUTING.md)

**如需混合現實工具組存放庫中所使用之不同分支的詳細資訊，請參閱 [此處的分支指南](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Branch-Guide)。**
