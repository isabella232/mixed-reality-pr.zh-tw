---
title: 安裝指南
description: 在新專案中安裝 MRTK-Unity 的指南。
author: hferrone
ms.author: v-hferrone
ms.date: 09/8/2020
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 775001fe6a73274859230e774a913c0ad71727c1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692965"
---
# <a name="installation-guide"></a>安裝指南

> [!CAUTION]
> 如果您不熟悉 Unity 中的 MRTK 或混合現實開發，我們建議您從 [unity 開發旅程](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2)的開端開始著手。 Unity 開發旅程是建議的 **MRTK 起始點**，特別是為了引導您完成安裝、核心概念，以及 Unity 中的 MRTK 使用。

## <a name="prerequisites"></a>Prerequisites

若要開始使用 Mixed Reality 工具組，您將需要：

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
* [Unity 2018.4. x、Unity 2019](https://unity3d.com/get-unity/download/archive)

  MRTK 支援 Unity 2018 上的 IL2CPP 和 .NET 腳本後端

* [Windows SDK 18362 +](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。

  如果您要建立適用于 WMR、HoloLens 1 或 HoloLens 2 的 UWP 應用程式，則這是必要的。 這在建立 OpenVR 時並不是必要的。

## <a name="add-mrtk-to-your-unity-project"></a>將 MRTK 新增至您的 Unity 專案

### <a name="required"></a>必要

1. [取得最新的 MRTK Unity 套件](#get-the-latest-mrtk-unity-packages)
1. [將 MRTK 套件匯入到您的 Unity 專案](#import-mrtk-packages-into-your-unity-project)
1. [將您的 Unity 專案切換到目標平台](#switch-your-unity-project-to-the-target-platform)
1. [將 MRTK 新增至新場景或新專案](#add-mrtk-to-a-new-scene-or-new-project)

### <a name="optional"></a>選擇性

* [入門教學課程](#getting-started-tutorials)
* [XR SDK 快速入門手冊 (Unity 2019.3 或更新版本) ](configuration/GettingStartedWithMRTKAndXRSDK.md)。
* [瞭解 MRTK 的核心構成要素](#learn-about-the-core-building-blocks-of-mrtk)
* [在 Unity 編輯器中執行 HandInteractionExamples 場景](#run-the-handinteractionexamples-scene-in-the-unity-editor)

### <a name="get-the-latest-mrtk-unity-packages"></a>取得最新的 MRTK Unity 套件

1. 移至 [ <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">MRTK 發行] 頁面</a>。
1. 在 [資產] 底下，下載：
    * **Microsoft.MixedRealityToolkit.Unity.Foundation.unitypackage**
    *  (**_選用_**) MixedRealityToolkit。 unitypackage
    *  (**_選擇性_** 的) MixedRealityToolkit，例如 unitypackage
    *  (**_版本到版本的升級所需，否則請_**) unitypackage

如需套件內容的資訊，請參閱 [MRTK 套件內容](reference-docs/MRTK_PackageContents.md)。

您也可以在 NuGet.org 上下載 Mixed Reality 工具組;如需詳細資訊，請參閱 [MRTK NuGet 套件](reference-docs/MRTKNuGetPackage.md)。

### <a name="import-mrtk-packages-into-your-unity-project"></a>將 MRTK 套件匯入到您的 Unity 專案

1. 建立新的 Unity 專案，或開啟現有的專案。 建立專案時，請務必選取 [3D] 作為範本類型。
1. 匯入您下載的 **MixedRealityToolkit** ，方法是前往 [資產-> 匯入封裝-> 自訂套件]，選取 unitypackage 檔案，確定已核取所有要匯入的專案，然後選取 [匯入]。
1.  (**_選擇性_**) 匯入 **MixedRealityToolkit** ，遵循與基礎封裝相同的步驟。 擴充功能套件提供一組適用于 MRTK 的實用選擇性元件。
1.  (**_選擇性_**) 匯入 **MixedRealityToolkit** ，遵循與上述相同的步驟。 範例套件是選擇性的，包含目前 MRTK 功能的實用示範場景。 **請注意，範例套件需要副檔名套件。**
1. **_版本到版本升級需要 (，否則請_**) 匯入與基礎套件相同的步驟來匯入 **MixedRealityToolkit** 。 工具套件是選擇性的，並且包含可增強 MRTK 開發人員體驗的公用程式（例如 ExtensionServiceCreator）。

> [!Note]
> Android 和 iOS 開發需要額外的套件安裝。 如需詳細資訊，請參閱 [如何設定適用于 iOS 和 Android 的 MRTK](CrossPlatform/UsingARFoundation.md)。
匯入基礎套件之後，您可能會看到類似下列的提示：

![UnitySetupPrompt](features/Images/MRTK_UnitySetupPrompt.png)

MRTK 正在嘗試設定您的專案，藉由執行下列動作來建立混合的現實解決方案：

* 為您目前的平臺啟用 XR 設定， (啟用 [XR] 核取方塊) 。
* 使用原始檔控制) 來強制執行對 Unity 專案的文字序列化/可見的中繼檔案 (建議。

接受這些選項完全是選擇性的，但建議使用。

有些 prefabs 和資產需要 TextMesh Pro，這表示您需要安裝 TextMesh Pro 套件，且專案中的資產 (視窗-> TextMeshPro > 匯入 TMP 基本資源) 。 匯 **入 TMP Essentials 資源之後，您必須重新開機 Unity 才能看到變更**。

### <a name="switch-your-unity-project-to-the-target-platform"></a>將您的 Unity 專案切換到目標平台

匯入封裝後，下一個步驟是為應用程式選取正確的平臺。

若要建立 **HoloLens 應用程式**，請切換至通用 Windows 平臺：

1. 開啟功能表： File > 組建設定
1. 在 [**平臺**] 清單中選取 **通用 Windows 平臺**
1. 按一下 [ **切換平臺** ] 按鈕

![切換平台](features/Images/getting_started/SwitchPlatform.png)

>[!NOTE]
> 混合現實工具組會在選取平臺時，提示您將建議的變更套用至專案。 當平臺切換時，如有必要，將會檢查並提示適當的設定。

### <a name="add-mrtk-to-a-new-scene-or-new-project"></a>將 MRTK 新增至新場景或新專案

1. 建立新的 Unity 專案，或在您目前的專案中啟動新的場景。

1. 請確定您已匯入 MRTK 套件， (我們建議使用基礎和範例，但不需要) 遵循 [上述步驟](#import-mrtk-packages-into-your-unity-project)。

1. 從功能表列中，選取 [混合現實工具組-> 新增至場景並設定]

    ![設定為場景](features/Images/MRTK_ConfigureScene.png)

    偵測器現在會顯示目前使用中的 MRTK 設定檔和設定檔選取下拉式清單，其中已預先選取預設設定檔。
    設定檔會設定 MRTK 核心元件的行為，並在 [設定檔](features/Profiles/Profiles.md) 文章中有更詳細的說明。

    > [!NOTE]
    >
    > * 如果您是在 Unity 2019.3 或更新版本中使用 Unity 的 XR SDK，您應該選擇「DefaultXRSDKConfigurationProfile」。 此設定檔會在需要時，使用 MRTK 的 XR SDK 系統和提供者來設定。  
    > * 如果您是在 HoloLens 或 HoloLens 2 上開始使用，您應該改為選擇 [DefaultHoloLens1ConfigurationProfile] 或 [DefaultHoloLens2ConfigurationProfile]。  
    > * 如需 DefaultMixedRealityToolkitConfigurationProfile 與 DefaultHoloLens2ConfigurationProfile 之間差異的詳細資訊，請參閱 [設定檔](Profiles/Profiles.md#hololens-2-profile) 。

    然後，您會在場景階層中看到下列內容：

    ![MRTK 場景設定](features/Images/MRTK_SceneSetup.png)

    其中包含下列內容：

    * **混合現實工具** 組-工具組本身，提供整個架構的集中設定進入點。
    * **MixedRealityPlayspace** -耳機的父物件，可確保在場景中正確地管理耳機/控制器和其他所需的系統。
    * 主要相機會以子系的形式移至 Playspace，讓 Playspace 能夠與 Sdk 一起管理攝影機

    >[!NOTE]
    > 在場景中工作時， **請勿將主要攝影機** (或場景原點的 **MixedRealityPlayspace**)  (0、0、0) 。  這是由 MRTK 和使用中的 SDK 所控制。 如果您需要移動播放玩家的起點，請 **移動場景內容，而不是相機**！

1. 按下 **空格鍵**，然後按下 [播放] 和 [測試輸出]。

您現在可以開始建立及部署到裝置！ 遵循 [組建和部署 MRTK](updates-deployment/BuildAndDeploy.md)中的步驟指示。

### <a name="getting-started-tutorials"></a>入門教學課程

如果您不熟悉 MRTK 或 MR 開發，我們建議您查看使用 MRTK v2 的使用者 [入門教學](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-01) 課程。

### <a name="learn-about-the-core-building-blocks-of-mrtk"></a>瞭解 MRTK 的核心構成要素

請參閱 [MRTK 101：如何使用混合現實工具組 Unity 進行基本互動 (HoloLens 2、HoloLens、Windows Mixed Reality、OPEN VR) ， ](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) 以瞭解核心建立區塊。

### <a name="run-the-handinteractionexamples-scene-in-the-unity-editor"></a>在 Unity 編輯器中執行 HandInteractionExamples 場景

[手形互動範例場景](features/README_HandInteractionExamples.md)文章是深入瞭解 MRTK 中 UX 控制項和互動的絕佳位置。

[![HandInteractionExample 場景](features/Images/MRTK_Examples.png)](README_HandInteractionExamples.md)

若要嘗試進行「手動互動」場景，請執行下列步驟。

1. 開啟下方的 **HandInteractionExamples** 場景 `Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandInteractionExamples`

1. 您可能會收到提示，要求您匯入 "TMP Essentials"。

    ![TMP Essentials](features/Images/getting_started/MRTK_GettingStarted_TMPro.png)

    如果您收到這類提示，請選取 [匯入 TMP essentials] 按鈕。 "TMP Essentials" 指的是文字網格 Pro 外掛程式，其中一些 MRTK 範例會用來改善文字轉譯。  (如需詳細資訊，請參閱 [Unity 中的文字](https://docs.microsoft.com/windows/mixed-reality/text-in-unity)) 

1. 關閉 TMP 對話方塊。 之後，您需要重載場景。 您可以按兩下 [專案] 索引標籤中的場景來完成這項作業。

1. 在場景視圖的 [Gizmos] 索引標籤底下，取消選取或壓縮3d 圖示的大小，以減少場景雜亂

     ![Gizmos](https://user-images.githubusercontent.com/13754172/80819866-a8aed800-8b8a-11ea-8d7b-a3822fdfc907.png)

1. 按下 [播放] 按鈕。

## <a name="using-the-in-editor-hand-input-simulation-to-test-a-scene"></a>使用編輯器內的手寫輸入模擬來測試場景

編輯器內輸入模擬可讓您根據特定類型的輸入（例如 [手](features/InputSimulation/InputSimulationService.md#hand-simulation) 或 [眼睛](features/EyeTracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor)）來測試虛擬物件行為。

如何在場景中四處移動：

* 使用 **W/A/S/D** 鍵，將觀景窗向前/向左/向後/向右移動。
* 使用 **Q/E** 鍵，以垂直方式移動觀景窗。
* 長按 **滑鼠右鍵** 以旋轉觀景窗。

如何模擬手部輸入：

* 按住 **空格鍵** 以啟用右手邊。
* 按住空格鍵時，移動滑鼠來移動右手。
* 使用 **滑鼠滾輪** 來調整手的深度。
* 按一下 **滑鼠左鍵** 以模擬捏合手勢。
* 使用 **T/Y** 鍵，讓右手持續保持在檢視中。
* 按住 **CTRL** 鍵，並移動滑鼠以旋轉右手。

盡情探索場景！ 您可以深入瞭解 [《手形互動範例指南》中](features/README_HandInteractionExamples.md)的 UI 控制項。 此外，請閱讀 [輸入模擬](features/InputSimulation/InputSimulationService.md) 檔，以深入瞭解 MRTK 中的編輯器內輸入模擬。

恭喜，您剛使用了第一個 MRTK 場景。 現在就開始建立您自己的經驗 .。。

## <a name="next-steps"></a>下一步

以下是一些建議的後續步驟：

* 查看 [MRTK 101：如何使用混合現實工具組 Unity 進行基本互動](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) ，以瞭解如何達成常見的空間互動，例如抓取、移動、調整和旋轉。
* 深入瞭解 MRTK 中的 UX 控制項可在 [UI 和互動建立區塊](features/Experimental/README.md#ux-building-blocks)中使用。
* 試用 [MRTK 範例中樞](features/README_ExampleHub.md) (預先建立的應用程式套件已包含在 [發行] 頁面中，方便您) 
* 瞭解如何使用 [混合式事實設定指南](out-of-scope/MixedRealityConfigurationGuide.md)中的 MRTK 設定設定檔。
* 瞭解 [MRTK 的架構](architecture/Overview.md)
* 瞭解 [MRTK 的輸入系統](features/input/Overview.md)
* 瞭解可加強您的混合現實設計和開發的 [MRTK 工具](features/Experimental/README.md#tools) 。
* 請參閱 [輸入模擬指南](features/InputSimulation/InputSimulationService.md) ，以瞭解如何在編輯器中模擬手動輸入。

## <a name="getting-help"></a>取得說明

如果您遇到 MRTK 所造成的問題，或是有關于如何執行某些問題的問題，有一些資源可以提供協助：

* 針對錯誤報表，請在 GitHub 存放庫上提出 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) 。
* 如有任何問題，請在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 或「 [混合現實」工具組頻道](https://holodevelopers.slack.com/messages/C2H4HT858) 的時差上聯繫。 您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。

## <a name="upgrading-from-the-holotoolkit-htkmrtk-v1"></a>從 HoloToolkit (HTK/MRTK v1) 升級

由於重建架構的緣故，沒有從 HoloToolkit 到混合現實工具組 v2 的直接升級路徑。 不過，您可以將 MRTK 匯入您的 HoloToolkit 專案中，並遷移您的執行。 如需詳細資訊，請參閱 [HoloToolkit 至混合現實工具組移植指南](updates-deployment/HTKToMRTKPortingGuide.md)

## <a name="getting-started-with-unitys-xr-sdk"></a>開始使用 Unity 的 XR SDK

您可以在我們的 [XR SDK 快速入門手冊](configuration/GettingStartedWithMRTKAndXRSDK.md)中找到完整的指示和資訊。
