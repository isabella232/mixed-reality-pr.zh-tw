---
title: 適用於 Android 和 iOS 的 Azure Spatial Anchors
description: 完成此課程，以了解如何將包含混合實境工具組 (MRTK) 和 Azure Spatial Anchors 的 Unity 專案部署至 Android 和 iOS。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, android, ios, MRTK, 混合實境工具組, UWP, Azure 空間錨點, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 6e9ae377a11d74fd9cdfca7ddb0379542d365e3365bdf07319bc8580b2e87420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215763"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5.適用於 Android 和 iOS 的 Azure Spatial Anchors

在本教學課程中，您將了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，在 Android 和 iOS 裝置上建置專案。

## <a name="objectives"></a>目標

* 了解如何使用 Unity 的 AR Foundation 和 ARCore XR 外掛程式，在 Android 裝置上建置專案
* 了解如何使用 Unity 的 AR Foundation 和 ARKit XR 外掛程式，在 iOS 裝置上建置專案

## <a name="installing-inbuilt-unity-packages"></a>安裝內建的 Unity 套件

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a>針對 AR Foundation 相機設定 MRTK

在本節中，您將了解如何設定 MRTK 以部署至行動裝置。

在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件。 然後在 [偵測器] 視窗中，選取 [相機] 索引標籤、複製相機設定檔，並為其提供適當的名稱，例如，**AzureSpatialAnchors_ARCameraProfile**：

![已選取新建立 ARCameraProfile 的 Unity](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> 如需有關如何複製 MRTK 設定檔的提示，您可以參閱[設定混合實境工具組設定檔](mr-learning-base-03.md)的指示。

仍在 [偵測器] 視窗中選取 [**相機**] 索引標籤，展開 **相機設定提供者**，然後按一下 [-] 移除 **Windows Mixed Reality 相機設定** 或 **XR SDK Windows Mixed Reality 相機設定**：

![已新增新資料提供者的 Unity ARCameraProfile ](images/mr-learning-asa/asa-05-section2-step1-2.png)

然後按一下 [ **+ 新增相機設定提供者** ] 按鈕，再展開新加入的 **新資料提供者**：

![已新增適用于 Android 的 AR 攝影機](images/mr-learning-asa/asa-05-section2-step1-3.png)

使用 [類型] 下拉式清單，將類型變更為 [Microsoft.MixedReality.Toolkit.Experimental.UnityAR] > [UnityARCameraSettings]：

![具有資料提供者類型選取路徑的 Unity ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-4.png)

藉由叫用功能表項目來更新 MRTK UnityAR 腳本定義：**混合現實**  >  **工具** 組  >  **公用程式**  >  **UnityAR** > 更新腳本定義

## <a name="building-your-application-to-your-android-device"></a>在您的 Android 裝置上建置應用程式

在本節中，您將了解如何設定您的專案，以在 Android 裝置中建置及部署該專案。

在 Unity 功能表中，選取 [檔案] > [建置設定...] 來開啟 [建置設定] 視窗，然後將平台切換為 Android：

![已選取 Android 平台的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> 如需有關如何切換建置平台的提示，可參閱[切換建置平台](mr-learning-base-02.md#switching-the-build-platform)的指示。

關閉 [建置設定] 視窗。

在 Unity 功能表中，選取 [**混合的現實**  >  **工具** 組  >  **公用程式**  >  ]，**設定 MRTK Project** 以開啟 **MRTK Project** [設定] 視窗，確認已選取所有選項，然後按一下 [套用] 按鈕以套用設定：

![Unity MRTK Project 的配置器1](images/mr-learning-asa/asa-05-section3-step1-2.png)

在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [其他設定] 區段，選取 [Vulkan]，然後按一下 **"-"** 來將其移除：

![已選取 Vulcan 的 Unity [其他設定]](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景加入至 [建置中的場景] 清單。 然後，使用 USB 纜線，將您的 Android 裝置連接到您的電腦，並從 [執行裝置] 下拉式清單中將其選取：

![已新增場景並已選取 [執行裝置] 的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> 如果您的裝置未出現在 [執行裝置] 下拉式清單中，您可能需要按下下拉式清單旁的 [重新整理] 按鈕。

在 [建置設定] 視窗中，按一下 [建置並執行] 按鈕，以開啟 [建置 Android] 視窗。

選擇適當的位置來儲存您的建置，例如 _D:\MixedRealityLearning\Builds_，然後為 apk 提供適當的名稱，例如 _MRTKTutorials-AzureSpatialAnchors_，然後按一下 [儲存] 按鈕來啟動建置程序：

![具有 [儲存] 提示視窗 Android 的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> 如果您在 Unity 主控台視窗中遇到與 Android SDK、NDK 或 JDK 模組相關的任何錯誤，則需要開啟 Unity Hub，並安裝相關聯的 Android 建置支援模組。

當建置程序完成時，應用程式應該會自動載入您的 Android 裝置。

## <a name="building-your-application-to-your-ios-device"></a>在您的 iOS 裝置上建置應用程式

在本節中，您將了解如何設定您的專案，以在 iOS 裝置中建置及部署該專案。

在 Unity 功能表中，選取 [檔案] > [建置設定...] 來開啟 [建置設定] 視窗，然後將平台切換為 iOS：

![已選取 iOS 的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> 如需有關如何切換建置平台的提示，可參閱[切換建置平台](mr-learning-base-02.md#switching-the-build-platform)的指示。

關閉 [建置設定] 視窗。

在 Unity 功能表中，選取 [**混合的現實**  >  **工具** 組  >  **公用程式**  >  ]，**設定 MRTK Project** 以開啟 **MRTK Project** [設定] 視窗，確認已選取所有選項，然後按一下 [套用] 按鈕以套用設定：

![Unity [MRTK 專案設定程式] 視窗 iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [其他設定] 區段，取消核取 [Strip Engine Code] 核取方塊來將其停用：

![已停用 [Strip Engine Code] 的 Unity [其他設定]](images/mr-learning-asa/asa-05-section4-step1-3.png)

關閉 [玩家設定] 視窗，然後再次開啟 [建置設定] 視窗。

在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景加入至 [建置中的場景] 清單：

![已新增場景的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section4-step1-4.png)

在 [建置設定] 視窗中，按一下 [建置] 按鈕，以開啟 [建置 iOS] 視窗。

選擇適當的位置來儲存您的 Xcode 專案，例如 _D:\MixedRealityLearning\Builds_，建立新的資料夾並指定適當的名稱，例如 _MRTKTutorials-AzureSpatialAnchors_，然後按一下 [選取資料夾] 按鈕來開始建置程序：

![具有 [儲存] 提示視窗 iOS 的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section4-step1-5.png)

當建置程序完成時，請遵循[ Xcode 專案](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)的指示，以了解如何將 Xcode 專案部署至您的 iOS 裝置。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，在 Android 和 iOS 裝置上建置專案。
