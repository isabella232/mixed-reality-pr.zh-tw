---
title: MRTK_Documentation
description: MRTK 使用者入門檔頁面
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: d7f6f7516b838b2b1a538c668917929f7696a2f2
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702014"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>何謂混合現實工具組

![混合實境工具組](features/images/Logo_MRTK_Unity_Banner.png)

MRTK-Unity 是由 Microsoft 所推動的專案，其提供一組元件與功能，可用來加快 Unity 中的跨平台 MR 應用程式開發。 以下是其中的一些功能：

* 提供 **空間互動和 UI 的跨平臺輸入系統和建立區塊**。
* 透過可讓您立即查看變更的編輯器內模擬，讓您能夠 **快速建立原型** 。
* 以可擴充的 **架構** 運作，讓開發人員能夠交換核心元件。
* **支援多種平臺**，包括
  * OpenXR (Unity 2020.2 或更新版本) 
    * Microsoft HoloLens 2
    * Windows Mixed Reality 頭戴式裝置
  * Windows Mixed Reality
    * Microsoft HoloLens
    * Microsoft HoloLens 2
    * Windows Mixed Reality 頭戴式裝置
  * Oculus (Unity 2019.3 或更新版本) 
    * Oculus 的追求
  * OpenVR
    * Windows Mixed Reality 頭戴式裝置
    * HTC Vive
    * Oculus Rift
  * Ultraleap 手部追蹤
  * IOS 和 Android 等行動裝置

## <a name="getting-started-with-mrtk"></a>開始使用 MRTK

如果您不熟悉 Unity 中的 MRTK 或混合現實開發， **我們建議您** 從 Microsoft Docs 的 [unity 開發旅程](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2) 開始著手。Unity 開發旅程是特別量身打造的，可透過安裝、核心概念和 MRTK 的使用方式來引導新的開發人員。

| 重要： Unity 開發旅程目前使用 **MRTK 版本 2.4.0** 和 **Unity 2019.4**。 |
| --- |

如果您是有經驗的混合現實或 MRTK 開發人員，請參閱下一節中的連結，以取得最新的套件和版本資訊。

## <a name="documentation"></a>文件

| [![版本資訊](features/images/MRTK_Icon_ReleaseNotes.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/ReleaseNotes.html)<br/>[版本資訊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/ReleaseNotes.html)| [![MRTK 總覽](features/images/MRTK_Icon_ArchitectureOverview.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html)<br/>[MRTK 總覽](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html)| [![功能指南](features/images/MRTK_Icon_FeatureGuides.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/features/ux-building-blocks/Button.html)<br/>[功能指南](https://microsoft.github.io/MixedRealityToolkit-Unity/features/ux-building-blocks/Button.html)| [![應用程式開發介面參考](features/images/MRTK_Icon_APIReference.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)<br/>[API 參考](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)|
|:---|:---|:---|:---|

## <a name="build-status"></a>組建狀態

| 分支 | CI 狀態 | 檔狀態 |
|---|---|---|
| `mrtk_development` |[![CI 狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![檔狀態](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="required-software"></a>必要的軟體

 | [ ![ Windows SDK 18362 +](features/images/MRTK170802_Short_17.png)](https://developer.microsoft.com/windows/downloads/windows-10-sdk) [Windows SDK 18362 +](https://developer.microsoft.com/windows/downloads/windows-10-sdk)| [ ![ Unity](features/images/MRTK170802_Short_18.png)](https://unity3d.com/get-unity/download/archive) [unity 2018.4. x](https://unity3d.com/get-unity/download/archive)| [ ![ Visual Studio 2019](features/images/MRTK170802_Short_19.png)](http://dev.windows.com/downloads) [Visual Studio 2019](http://dev.windows.com/downloads)| [ ![ 模擬器 (選擇性的) ](features/images/MRTK170802_Short_20.png)](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator) [模擬器 (選擇性) ](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator)|
| :--- | :--- | :--- | :--- |
| 若要使用 MRTK v2 來建立應用程式，您需要 Windows 10 2019 年5月更新 SDK。 <br> 若要執行沉浸式耳機的應用程式，您需要 Windows 10 Fall Creators Update。 | Unity 3D 引擎提供在 Windows 10 中建立混合現實專案的支援 | Visual Studio 用於程式碼編輯、部署和建立 UWP 應用程式套件 | 模擬器可讓您測試應用程式，而不需要在模擬環境中使用裝置 |

## <a name="feature-areas"></a>功能範圍

| ![輸入系統 ](features/images/MRTK_Icon_InputSystem.png) [輸入系統](features/input/overview.md)<br/>&nbsp;  | ![手動追蹤<br/> (HoloLens 2) ](features/images/MRTK_Icon_HandTracking.png) [手追蹤 <br/> (HoloLens 2](features/input/hand-tracking.md))  | ![眼睛追蹤<br/> (HoloLens 2) ](features/images/MRTK_Icon_EyeTracking.png) [眼睛追蹤 <br/> (](features/eye-tracking/eye-tracking-Main.md) HoloLens 2)  | ![設定檔 ](features/images/MRTK_Icon_Profiles.png) [設定檔](configuration/mixed-reality-configuration-guide.md)<br/>&nbsp; | ![手動追蹤<br/> (Ultraleap) ](features/images/MRTK_Icon_HandTracking.png) [手動追蹤 (Ultraleap) ](features/cross-platform/leap-motion-mrtk.md)|
| :--- | :--- | :--- | :--- | :--- |
| ![UI 控制項 1 ](features/images/MRTK_Icon_UIControls.png) [ui 控制項 2](welcome-to-mrtk.md#ux-building-blocks)<br/>&nbsp; | ![解析器 ](features/images/MRTK_Icon_Solver.png) [解析器 1](features/ux-building-blocks/solvers/solver.md)<br/>&nbsp; | ![多場景<br/> Manager ](features/images/MRTK_Icon_SceneSystem.png) [多場景 <br/> 管理員](features/scene-system/scene-system-getting-started.md) | ![空間<br/> 感知 ](features/images/MRTK_Icon_SpatialUnderstanding.png) [空間 <br/> 感知](features/spatial-awareness/spatial-awareness-getting-started.md) | ![診斷<br/> 工具 ](features/images/MRTK_Icon_Diagnostics.png) [診斷 <br/> 工具](features/diagnostics/diagnostics-system-getting-started.md) |
| ![MRTK 標準著色器視圖 ](features/images/MRTK_Icon_StandardShader.png) [MRTK 標準著色器範例視圖](features/rendering/mrtk-standard-shader.md?q=shader) | ![語音 & 聽寫 ](features/images/MRTK_Icon_VoiceCommand.png) [語音](features/input/speech.md)<br/> & [聽寫](features/input/dictation.md) | ![界限<br/>系統 ](features/images/MRTK_Icon_Boundary.png) [界限 <br/> 系統](features/boundary/boundary-system-getting-started.md)| ![編輯器內<br/>模擬 ](features/images/MRTK_Icon_InputSystem.png) [編輯器內 <br/> 模擬](features/input-simulation/input-simulation-service.md) | ![實驗性<br/>功能 ](features/images/MRTK_Icon_Experimental.png) [實驗性 <br/> 功能](contributing/experimental-features.md)|

## <a name="ux-building-blocks"></a>UX 組建區塊

|  [ ![ 按鈕](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md)[按鈕](features/ux-building-blocks/button.md) | [ ![ 界限控制項](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md)[界限控制項](features/ux-building-blocks/bounds-control.md) | [ ![ 物件](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md)操作工具[物件](features/ux-building-blocks/object-manipulator.md)操作工具 |
|:--- | :--- | :--- |
| 支援各種輸入方法的按鈕控制項，包括 HoloLens 2 的有向的手勢 | 在3D 空間中操作物件的標準 UI | 以一或兩個手中操作物件的腳本 |
|  [ ![ 平板](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md)[平板](features/ux-building-blocks/slate.md) | [ ![ 系統鍵盤](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md)[系統鍵盤](features/ux-building-blocks/system-keyboard.md) | [ ![ 互動](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md)[互動](features/ux-building-blocks/interactable.md) |
| 2D 樣式平面，支援以已明確表達的手寫輸入進行滾動 | 在 Unity 中使用系統鍵盤的範例腳本  | 使用視覺狀態和主題支援讓物件互動的腳本 |
|  [ ![ 規劃](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md)求解[規劃](features/ux-building-blocks/solvers/solver.md) | [ ![ 物件集合](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md)[物件集合](features/ux-building-blocks/object-collection.md) | [ ![ 工具](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md)提示[工具提示](features/ux-building-blocks/tooltip.md) |
| 各種物件定位行為，例如標記-沿著標記、主體鎖定、常數視圖大小和表面磁性 | 在三維圖形中設定物件陣列的腳本 | 具有彈性錨點/pivot 系統的注釋 UI，可用來標記動作控制器和物件 |
|  [ ![ 滑杆](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md)[滑杆](features/ux-building-blocks/sliders.md) | [ ![ MRTK 標準著色器視圖 2](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) [MRTK 標準著色器 2](features/rendering/mrtk-standard-shader.md) | [ ![ 手形功能表 1](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) [手功能表 2](features/ux-building-blocks/hand-menu.md) |
| 調整支援直接追蹤互動之值的滑杆 UI | MRTK 的標準著色器可支援各種流暢的設計項目與效能 | 使用手形條件約束規劃的手動鎖定 UI，以進行快速存取 |
|  [ ![ 應用程式行](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md)[應用程式行](features/ux-building-blocks/app-bar.md) | [ ![ 指標](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md)[指標](features/input/Pointers.md) | [ ![ Fingertip 視覺效果](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) [Fingertip 視覺效果](features/ux-building-blocks/fingertip-visualization.md) |
| 界限控制項手動啟用的 UI | 瞭解各種類型的指標 | Fingertip 上的視覺效果 affordance，可改善直接互動的信賴度 |
|  靠近[功能表](features/ux-building-blocks/near-menu.md)的[ ![ 附近功能表](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) | [ ![ 空間感知 1](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) [空間感知](features/spatial-awareness/spatial-awareness-getting-started.md) | [ ![ 語音命令](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md)[語音命令](features/input/speech.md)  /  [聽寫](features/input/dictation.md) |
| 接近互動的浮動功能表 UI | 讓您的全像攝影物件與實體環境互動 | 整合語音輸入的腳本和範例 |
|  [ ![ 進度指示器](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md)[進度指標](features/ux-building-blocks/progress-indicator.md) | [ ![ 對話方塊](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/experimental/dialog.md)[對話方塊 [實驗]](features/experimental/dialog.md) | [ ![ 手動教練](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/experimental/hand-coach.md)[指導 [實驗]](features/experimental/hand-coach.md) |
| 用於傳達資料處理或作業的視覺化指標 | 要求使用者確認或確認的 UI  | 當手勢未教授時，可協助引導使用者的元件 |
|  [ ![ 手物理服務](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md)的[物理服務 [實驗]](features/experimental/hand-physics-service.md) | [ ![ 滾動集合](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md)[滾動集合](features/ux-building-blocks/scrolling-object-collection.md) | [ ![ ](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md)停駐[固定 [實驗]](features/experimental/dock.md) |
| 實際的物理服務可讓您透過明確的方式進行固定的內文衝突事件和互動 | 原生滾動3D 物件的物件集合 | Dock 允許將物件移入和移出預定的位置 |
|  [ ![ 眼睛追蹤：目標選擇](features/images/eye-tracking/mrtk_et_targetselect.png)](features/eye-tracking/eye-tracking-target-selection.md)[眼睛追蹤：目標選取範圍](features/eye-tracking/eye-tracking-target-selection.md) | [ ![ 眼睛追蹤：導覽](features/images/eye-tracking/mrtk_et_navigation.png)](features/eye-tracking/eye-tracking-navigation.md)[眼睛追蹤：導覽](features/eye-tracking/eye-tracking-navigation.md) | [ ![ 眼睛追蹤：熱度圖](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/eye-tracking/eye-tracking-examples-overview.md#visualization-of-visual-attention)[視覺追蹤：熱度圖](features/eye-tracking/eye-tracking-examples-overview.md#visualization-of-visual-attention) |
| 結合眼睛、語音和手輸入，以快速且輕鬆地在場景中選取全像影像 | 瞭解如何根據您要查看的內容，自動滾動文字或流暢縮放至焦點內容 | 記錄、載入和視覺化使用者在您的應用程式中查看的範例 |

## <a name="tools"></a>工具

|  [ ![ 優化視窗](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md)[優化視窗](features/tools/optimize-window.md) | 相依性[ ![ 視窗](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md)相依性[視窗](features/tools/dependency-window.md) | ![組建視窗](features/images/MRTK_Icon_BuildWindow.png) 組建視窗 | [ ![ 輸入錄製](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md)[輸入記錄](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| 自動設定混合現實專案以進行效能優化 | 分析資產之間的相依性，並找出未使用的資產 |  設定及執行混合現實應用程式的端對端組建程式 | 在編輯器中錄製並播放前端移動和手動追蹤資料 |

## <a name="example-scenes"></a>範例場景

探索 MRTK 在 [此範例場景](features/example-scenes/hand-interaction-examples.md)中的各種互動和 UI 控制項類型。

您可以在 [資產/MixedRealityToolkit] 下找到其他範例場景 [**。範例/示範**](/Assets/MixedRealityToolkit.Examples/Demos) 資料夾。

[![範例場景2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>MRTK 範例中樞

您可以使用 MRTK 範例中樞來嘗試 MRTK 中的各種範例場景。
您可以在 [ [**發行資產**](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0) ] 資料夾下找到 HoloLens (x86) 、HOLOLENS 2 (ARM) 和 Windows Mixed Reality 沉浸式耳機 (x64) 的預先建立應用程式套件。 [使用 Windows 裝置入口網站在 HoloLens 上安裝應用程式](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)。 在 HoloLens 2 上，您可以 [透過 Microsoft Store 應用程式下載並安裝 MRTK 範例中樞](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)。

請參閱 [範例中樞的讀我檔案頁面](features/example-scenes/example-hub.md) ，以瞭解如何使用 MRTK 的場景系統和場景轉換服務建立多場景中樞的詳細資料。

[![範例場景中樞](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>使用 MRTK 建立的範例應用程式

| [![元素週期表](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Galaxy Explorer 1](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)| [![Galaxy Explorer 2](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)|
|:--- | :--- | :--- |
| 專案的[定期資料表](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)是開放原始碼範例應用程式，示範如何使用 MRTK 的輸入系統和建立區塊來建立 HoloLens 和沉浸式耳機的應用程式體驗。 閱讀移植案例：將專案 [應用程式的定期資料表帶入 MRTK v2 以 HoloLens 2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) 是一種開放原始碼範例應用程式，最初是在2016年3月的「分享您的想法」活動中所開發。 已使用 MRTK v2，以 HoloLens 2 的新功能更新了 Galaxy Explorer。 閱讀這篇文章： [HoloLens 2 的 Galaxy Explorer](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update) |介面是 HoloLens 2 的開放原始碼範例應用程式，[它會探索](https://github.com/Microsoft/GalaxyExplorer)如何使用視覺效果、音訊和完全帶清楚方式的手動追蹤來建立 tactile 刺痛。 查看 Microsoft MR Dev Days session [學習 from surface 應用程式](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) ，以取得詳細的設計和開發案例。 |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>來自混合現實開發日2020的研討會影片

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| 如何建立從開始到完成的簡單 MRTK 應用程式的教學課程。 瞭解互動概念和 MRTK 的多平臺功能。 | 深入探討 MRTK 的 UX 構成要素，協助您打造美觀的混合現實體驗。 | MRTK 和外部的效能工具簡介，以及 MRTK 標準著色器的總覽。 |

若要探索更多課程影片，請參閱 [混合現實開發日](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) 。

## <a name="engage-with-the-community"></a>與社區互動

* 在 MRTK 上加入關於 [時差](https://holodevelopers.slack.com/)的交談。 您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。

* 使用 **MRTK** 標記詢問有關在 [STACK OVERFLOW](https://stackoverflow.com/questions/tagged/mrtk)上使用 MRTK 的問題。

* 如果您發現 MRTK 程式碼中有問題，請搜尋 [已知問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 或提出 [新問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) 。

* 如有關于參與 MRTK 的問題，請移至「 [混合現實」工具](https://holodevelopers.slack.com/messages/C2H4HT858) 組頻道的時差。

此專案採用了 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/)。
如需詳細資訊，請參閱[管理辦法常見問題集](https://opensource.microsoft.com/codeofconduct/faq/)，如有其他問題或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>混合現實開發人員中心上的實用資源

| ![探索 ](features/images/mrdevcenter/icon-discover.png) [探索](https://docs.microsoft.com/windows/mixed-reality/)| ![設計 ](features/images/mrdevcenter/icon-design.png) [設計](https://docs.microsoft.com/windows/mixed-reality/design)| ![開發 ](features/images/mrdevcenter/icon-develop.png) [開發](https://docs.microsoft.com/windows/mixed-reality/development)| ![散發) ](features/images/mrdevcenter/icon-distribute.png) [散發](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| 瞭解如何建立 HoloLens 和沉浸式耳機的混合現實體驗 (VR) 。          | 取得設計指南。 建立使用者介面。 瞭解互動和輸入。     | 取得開發指南。 學習技術。 瞭解科學。       | 準備好您的應用程式以供其他人使用，並考慮建立 3D 啟動器。 |

## <a name="useful-resources-on-azure"></a>Azure 上的實用資源

| ![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/)| ![語音服務](features/images/mrdevcenter/icon-azurespeechservices.png) [語音服務](https://docs.microsoft.com/azure/cognitive-services/speech-service/)| ![視覺服務 ](features/images/mrdevcenter/icon-azurevisionservices.png) [視覺服務](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| 空間錨點是一種跨平臺服務，可讓您使用在一段時間內跨裝置保存其位置的物件，建立混合的現實體驗。| 探索及整合 Azure 提供的語音功能，例如語音轉換文字、說話者辨識或語音翻譯至您的應用程式。| 使用視覺服務識別並分析您的影像或視訊內容，例如電腦視覺、臉部偵測、表情辨識或影片索引器。 |

## <a name="learn-more-about-the-mrtk-project"></a>深入瞭解 MRTK 專案

您可以在 [專案管理] 區段下的 [wiki](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki) 中找到我們的規劃內容。 您永遠可以在反復專案計劃問題中看到小組正在積極處理的專案。

## <a name="how-to-contribute"></a>如何參與

瞭解您[如何參與 MRTK 的貢獻。](contributing/contributing.md)

**如需混合現實工具組存放庫中所使用之不同分支的詳細資訊，請參閱 [此處的分支指南](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Branch-Guide)。**

## <a name="getting-help"></a>取得說明

如果您遇到 MRTK 所造成的問題，或是有關于如何執行某些問題的問題，有一些資源可以提供協助：

* 針對錯誤報表，請在 GitHub 存放庫上提出 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) 。
* 如有任何問題，請在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 或「 [混合現實」工具組頻道](https://holodevelopers.slack.com/messages/C2H4HT858) 的時差上聯繫。 您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。
