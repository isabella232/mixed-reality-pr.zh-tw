---
title: 適用於 Android 和 iOS 的 Azure Spatial Anchors
description: 完成此課程，以了解如何將包含混合實境工具組 (MRTK) 和 Azure Spatial Anchors 的 Unity 專案部署至 Android 和 iOS。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, android, ios, MRTK, 混合實境工具組, UWP, Azure 空間錨點, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 699c7689fcd23543f4d4b0e86f64cdbf98debc1f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590710"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="2896a-104">5.適用於 Android 和 iOS 的 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="2896a-104">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="2896a-105">在本教學課程中，您將了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，在 Android 和 iOS 裝置上建置專案。</span><span class="sxs-lookup"><span data-stu-id="2896a-105">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="2896a-106">目標</span><span class="sxs-lookup"><span data-stu-id="2896a-106">Objectives</span></span>

* <span data-ttu-id="2896a-107">了解如何使用 Unity 的 AR Foundation 和 ARCore XR 外掛程式，在 Android 裝置上建置專案</span><span class="sxs-lookup"><span data-stu-id="2896a-107">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="2896a-108">了解如何使用 Unity 的 AR Foundation 和 ARKit XR 外掛程式，在 iOS 裝置上建置專案</span><span class="sxs-lookup"><span data-stu-id="2896a-108">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="2896a-109">安裝內建的 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="2896a-109">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="2896a-110">在本節中，您將升級及安裝下列內建套件：</span><span class="sxs-lookup"><span data-stu-id="2896a-110">In this section, you will upgrade and install the following inbuilt packages:</span></span>

* <span data-ttu-id="2896a-111">AR Foundation 3.1.3</span><span class="sxs-lookup"><span data-stu-id="2896a-111">AR Foundation 3.1.3</span></span>
* <span data-ttu-id="2896a-112">XR 舊版輸入協助程式2.1。6</span><span class="sxs-lookup"><span data-stu-id="2896a-112">XR Legacy Input Helpers 2.1.6</span></span>
* <span data-ttu-id="2896a-113">適用於 Android 的 ARCore XR 外掛程式 3.1.3 支援</span><span class="sxs-lookup"><span data-stu-id="2896a-113">ARCore XR Plugin 3.1.3 for Android support</span></span>
* <span data-ttu-id="2896a-114">適用於 iOS 的 ARKit XR 外掛程式 3.1.3 支援</span><span class="sxs-lookup"><span data-stu-id="2896a-114">ARKit XR plugin 3.1.3 for iOS support</span></span>

> [!CAUTION]
> <span data-ttu-id="2896a-115">並非所有版本都與 MRTK 相容，而且只有特定版本能夠一起使用，因此請務必安裝上列確切版本。</span><span class="sxs-lookup"><span data-stu-id="2896a-115">Not all version are compatible with MRTK and only certain version works together, so make sure you install the exact versions listed above.</span></span>

<span data-ttu-id="2896a-116">在 Unity 功能表中，選取 [視窗] > [套件管理員] 以開啟 [套件管理員] 視窗，然後選取 [AR Foundation] > [3.1.3]，並按一下 [更新為 3.1.3] 按鈕以更新套件：</span><span class="sxs-lookup"><span data-stu-id="2896a-116">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** > **3.1.3** and click the **Update to 3.1.3** button to update the package:</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](images/mr-learning-asa/asa-05-section1-step1-1.png)

<span data-ttu-id="2896a-118">若有需要，遵循相同程序來匯入其餘套件。</span><span class="sxs-lookup"><span data-stu-id="2896a-118">Follow the same process to import the remaining packages as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="2896a-119">如果您正針對 Android 開發本專案，則不需要安裝 ARKit XR 外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="2896a-119">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="2896a-120">同樣地，如果您要針對 iOS 開發本專案，就不需要安裝 ARCore XR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="2896a-120">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="2896a-121">針對 AR Foundation 相機設定 MRTK</span><span class="sxs-lookup"><span data-stu-id="2896a-121">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="2896a-122">在本節中，您將了解如何設定 MRTK 以部署至行動裝置。</span><span class="sxs-lookup"><span data-stu-id="2896a-122">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="2896a-123">在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件。</span><span class="sxs-lookup"><span data-stu-id="2896a-123">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="2896a-124">然後在 [偵測器] 視窗中，選取 [相機] 索引標籤、複製相機設定檔，並為其提供適當的名稱，例如，**AzureSpatialAnchors_ARCameraProfile**：</span><span class="sxs-lookup"><span data-stu-id="2896a-124">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![已選取新建立 ARCameraProfile 的 Unity](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="2896a-126">如需有關如何複製 MRTK 設定檔的提示，您可以參閱[設定混合實境工具組設定檔](mr-learning-base-03.md)的指示。</span><span class="sxs-lookup"><span data-stu-id="2896a-126">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="2896a-127">在仍選取 [相機] 索引標籤的 [偵測器] 視窗中展開 [相機設定提供者]，然後按一下 [+ 新增相機設定提供者] 按鈕，再展開新增的 [新資料提供者 1]：</span><span class="sxs-lookup"><span data-stu-id="2896a-127">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider 1**:</span></span>

![已新增新資料提供者的 Unity ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="2896a-129">使用 [類型] 下拉式清單，將類型變更為 [Microsoft.MixedReality.Toolkit.Experimental.UnityAR] > [UnityARCameraSettings]：</span><span class="sxs-lookup"><span data-stu-id="2896a-129">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![具有資料提供者類型選取路徑的 Unity ARCameraProfile](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="2896a-131">在仍然選取 **MixedRealityToolkit** 物件的 [階層] 視窗中，使用 [新增元件] 按鈕來新增下列元件：</span><span class="sxs-lookup"><span data-stu-id="2896a-131">With the **MixedRealityToolkit** object still selected in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="2896a-132">AR Anchor Manager (指令碼)</span><span class="sxs-lookup"><span data-stu-id="2896a-132">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="2896a-133">DisableDiagnosticsSystem (指令碼)</span><span class="sxs-lookup"><span data-stu-id="2896a-133">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="2896a-134">已新增 AR 錨點管理員和 DisableDiagnosticsSystem 元件的 Unity MixedRealityToolkit 物件</span><span class="sxs-lookup"><span data-stu-id="2896a-134">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="2896a-135">AR Session Origin (指令碼) 元件會在您新增 AR Reference Point Manager (指令碼) 元件時自動加入，因為這是 AR Reference Point Manager (指令碼) 元件的必要項目。</span><span class="sxs-lookup"><span data-stu-id="2896a-135">When you add the AR Reference Point Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Reference Point Manager (Script) component.</span></span>



<span data-ttu-id="2896a-136">藉由叫用功能表項目來更新 MRTK UnityAR 腳本定義：**混合現實工具** 組  >  **公用程式**  >  **UnityAR** > 更新腳本定義</span><span class="sxs-lookup"><span data-stu-id="2896a-136">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit** > **Utilities** > **UnityAR** > Update Scripting Defines</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="2896a-137">在您的 Android 裝置上建置應用程式</span><span class="sxs-lookup"><span data-stu-id="2896a-137">Building your application to your Android device</span></span>

<span data-ttu-id="2896a-138">在本節中，您將了解如何設定您的專案，以在 Android 裝置中建置及部署該專案。</span><span class="sxs-lookup"><span data-stu-id="2896a-138">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="2896a-139">在 Unity 功能表中，選取 [檔案] > [建置設定...] 來開啟 [建置設定] 視窗，然後將平台切換為 Android：</span><span class="sxs-lookup"><span data-stu-id="2896a-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![已選取 Android 平台的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="2896a-141">如需有關如何切換建置平台的提示，可參閱[切換建置平台](mr-learning-base-02.md#switching-the-build-platform)的指示。</span><span class="sxs-lookup"><span data-stu-id="2896a-141">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="2896a-142">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="2896a-142">Close the Build Settings window.</span></span>

<span data-ttu-id="2896a-143">在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 來開啟 [MRTK 專案設定程式] 視窗，並確定已選取所有選項，然後按一下 [套用] 按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="2896a-143">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Unity [MRTK 專案設定程式] 視窗 Android](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="2896a-145">在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [其他設定] 區段，選取 [Vulkan]，然後按一下 **"-"** 來將其移除：</span><span class="sxs-lookup"><span data-stu-id="2896a-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![已選取 Vulcan 的 Unity [其他設定]](images/mr-learning-asa/asa-05-section3-step1-3.png)

<span data-ttu-id="2896a-147">在 Unity 功能表中，選取 [**編輯**  >  **專案設定 ...**  > ]。**播放機** > **XR 設定** 時，請確定您是在 **Android** 平臺中，並勾選 [**支援虛擬實境**] 核取方塊，然後按一下 + 圖示，然後選取 [無]：</span><span class="sxs-lookup"><span data-stu-id="2896a-147">In the Unity menu, select **Edit** > **Project Settings...** >**Player**> **XR Setting**, make sure you are in **Android** platform and check the **Virtual Reality Supported** checkbox then click the + icon, and select None:</span></span>

![Unity [MRTK 專案設定程式] 視窗 Android](images/mr-learning-asa/asa-05-section3-step1-2-1.png)

<span data-ttu-id="2896a-149">關閉 [玩家設定] 視窗，然後再次開啟 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="2896a-149">Close the Player Settings window and open the Build Settings window again.</span></span>

<span data-ttu-id="2896a-150">在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景加入至 [建置中的場景] 清單。</span><span class="sxs-lookup"><span data-stu-id="2896a-150">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="2896a-151">然後，使用 USB 纜線，將您的 Android 裝置連接到您的電腦，並從 [執行裝置] 下拉式清單中將其選取：</span><span class="sxs-lookup"><span data-stu-id="2896a-151">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![已新增場景並已選取 [執行裝置] 的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="2896a-153">如果您的裝置未出現在 [執行裝置] 下拉式清單中，您可能需要按下下拉式清單旁的 [重新整理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2896a-153">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="2896a-154">在 [建置設定] 視窗中，按一下 [建置並執行] 按鈕，以開啟 [建置 Android] 視窗。</span><span class="sxs-lookup"><span data-stu-id="2896a-154">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="2896a-155">選擇適當的位置來儲存您的建置，例如 _D:\MixedRealityLearning\Builds_，然後為 apk 提供適當的名稱，例如 _MRTKTutorials-AzureSpatialAnchors_，然後按一下 [儲存] 按鈕來啟動建置程序：</span><span class="sxs-lookup"><span data-stu-id="2896a-155">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![具有 [儲存] 提示視窗 Android 的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
<span data-ttu-id="2896a-157">如果您在 Unity 主控台視窗中遇到與 Android SDK、NDK 或 JDK 模組相關的任何錯誤，則需要開啟 Unity Hub，並安裝相關聯的 Android 建置支援模組。</span><span class="sxs-lookup"><span data-stu-id="2896a-157">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="2896a-158">當建置程序完成時，應用程式應該會自動載入您的 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="2896a-158">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="2896a-159">在您的 iOS 裝置上建置應用程式</span><span class="sxs-lookup"><span data-stu-id="2896a-159">Building your application to your iOS device</span></span>

<span data-ttu-id="2896a-160">在本節中，您將了解如何設定您的專案，以在 iOS 裝置中建置及部署該專案。</span><span class="sxs-lookup"><span data-stu-id="2896a-160">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="2896a-161">在 Unity 功能表中，選取 [檔案] > [建置設定...] 來開啟 [建置設定] 視窗，然後將平台切換為 iOS：</span><span class="sxs-lookup"><span data-stu-id="2896a-161">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![已選取 iOS 的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="2896a-163">如需有關如何切換建置平台的提示，可參閱[切換建置平台](mr-learning-base-02.md#switching-the-build-platform)的指示。</span><span class="sxs-lookup"><span data-stu-id="2896a-163">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="2896a-164">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="2896a-164">Close the Build Settings window.</span></span>

<span data-ttu-id="2896a-165">在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 來開啟 [MRTK 專案設定程式] 視窗，並確定已選取所有選項，然後按一下 [套用] 按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="2896a-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Unity [MRTK 專案設定程式] 視窗 iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

<span data-ttu-id="2896a-167">在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [其他設定] 區段，取消核取 [Strip Engine Code] 核取方塊來將其停用：</span><span class="sxs-lookup"><span data-stu-id="2896a-167">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![已停用 [Strip Engine Code] 的 Unity [其他設定]](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="2896a-169">關閉 [玩家設定] 視窗，然後再次開啟 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="2896a-169">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="2896a-170">在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景加入至 [建置中的場景] 清單：</span><span class="sxs-lookup"><span data-stu-id="2896a-170">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![已新增場景的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="2896a-172">在 [建置設定] 視窗中，按一下 [建置] 按鈕，以開啟 [建置 iOS] 視窗。</span><span class="sxs-lookup"><span data-stu-id="2896a-172">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="2896a-173">選擇適當的位置來儲存您的 Xcode 專案，例如 _D:\MixedRealityLearning\Builds_，建立新的資料夾並指定適當的名稱，例如 _MRTKTutorials-AzureSpatialAnchors_，然後按一下 [選取資料夾] 按鈕來開始建置程序：</span><span class="sxs-lookup"><span data-stu-id="2896a-173">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![具有 [儲存] 提示視窗 iOS 的 Unity [建置設定] 視窗](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="2896a-175">當建置程序完成時，請遵循[ Xcode 專案](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)的指示，以了解如何將 Xcode 專案部署至您的 iOS 裝置。</span><span class="sxs-lookup"><span data-stu-id="2896a-175">When the build process is complete, follow the [Export the Xcode project](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2896a-176">恭喜！</span><span class="sxs-lookup"><span data-stu-id="2896a-176">Congratulations</span></span>

<span data-ttu-id="2896a-177">在本教學課程中，您已了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，在 Android 和 iOS 裝置上建置專案。</span><span class="sxs-lookup"><span data-stu-id="2896a-177">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>