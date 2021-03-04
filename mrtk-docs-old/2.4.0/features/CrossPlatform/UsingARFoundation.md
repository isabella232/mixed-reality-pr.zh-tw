---
title: UsingARFoundation
description: 在 unity 中使用 ARFoundation 的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、AR Core、AR 套件
ms.openlocfilehash: c1d1e9f51304f57e46201972fbb0c419f1f941d7
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780235"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="e0798-104">如何設定 iOS 和 Android 的 MRTK [實驗]</span><span class="sxs-lookup"><span data-stu-id="e0798-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="e0798-105">安裝必要的套件</span><span class="sxs-lookup"><span data-stu-id="e0798-105">Install required packages</span></span>

1. <span data-ttu-id="e0798-106">從 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0)或 [NuGet](../../reference-docs/MRTKNuGetPackage.md)下載並匯入 **MixedReality 套件。**</span><span class="sxs-lookup"><span data-stu-id="e0798-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or [NuGet](../../reference-docs/MRTKNuGetPackage.md)</span></span>

1. <span data-ttu-id="e0798-107">在 Unity 套件管理員 (UPM) 中，安裝下列套件：</span><span class="sxs-lookup"><span data-stu-id="e0798-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="e0798-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="e0798-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="e0798-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="e0798-109">**Android**</span></span> | <span data-ttu-id="e0798-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e0798-110">**iOS**</span></span> | <span data-ttu-id="e0798-111">註解</span><span class="sxs-lookup"><span data-stu-id="e0798-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="e0798-112">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="e0798-112">AR Foundation</span></span>  <br/> <span data-ttu-id="e0798-113">版本： 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="e0798-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="e0798-114">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="e0798-114">AR Foundation</span></span>  <br/> <span data-ttu-id="e0798-115">版本： 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="e0798-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="e0798-116">針對 Unity 2018.4，此套件包含為預覽版本。</span><span class="sxs-lookup"><span data-stu-id="e0798-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="e0798-117">若要查看封裝： Window > 套件管理員 > Advanced > 顯示預覽套件</span><span class="sxs-lookup"><span data-stu-id="e0798-117">To view package: Window > Package Manager > Advanced > Show Preview Packages</span></span>|
    | <span data-ttu-id="e0798-118">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="e0798-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e0798-119">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="e0798-119">Version: 2.1.2</span></span> | <span data-ttu-id="e0798-120">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="e0798-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e0798-121">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="e0798-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="e0798-122">**Unity 2019.3. x**</span><span class="sxs-lookup"><span data-stu-id="e0798-122">**Unity 2019.3.x**</span></span>

    | <span data-ttu-id="e0798-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="e0798-123">**Android**</span></span> | <span data-ttu-id="e0798-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="e0798-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="e0798-125">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="e0798-125">AR Foundation</span></span>  <br/> <span data-ttu-id="e0798-126">版本：2.1。4</span><span class="sxs-lookup"><span data-stu-id="e0798-126">Version: 2.1.4</span></span> |  <span data-ttu-id="e0798-127">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="e0798-127">AR Foundation</span></span>  <br/> <span data-ttu-id="e0798-128">版本：2.1。4</span><span class="sxs-lookup"><span data-stu-id="e0798-128">Version: 2.1.4</span></span> |
    | <span data-ttu-id="e0798-129">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="e0798-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="e0798-130">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="e0798-130">Version: 2.1.2</span></span> | <span data-ttu-id="e0798-131">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="e0798-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="e0798-132">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="e0798-132">Version: 2.1.2</span></span> |

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="e0798-133">啟用 Unity AR 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="e0798-133">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="e0798-134">下列步驟假設使用 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="e0798-134">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="e0798-135">其他服務註冊機構所需的步驟可能會不同。</span><span class="sxs-lookup"><span data-stu-id="e0798-135">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="e0798-136">選取場景階層中的 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="e0798-136">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 設定的場景階層](../Images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="e0798-138">選取 [ **複製並自訂** ] 以複製 MRTK 設定檔，以啟用自訂設定。</span><span class="sxs-lookup"><span data-stu-id="e0798-138">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![複製 MRTK 設定檔](../Images/CameraSystem/CloneProfileARFoundation.png)

1. <span data-ttu-id="e0798-140">選取相機設定檔旁邊的 [ **複製** ]。</span><span class="sxs-lookup"><span data-stu-id="e0798-140">Select **Clone** next to the Camera Profile.</span></span>

    ![複製 MRTK 攝影機設定檔](../Images/CameraSystem/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="e0798-142">將 [偵測器] 面板移至 [相機系統] 區段，然後展開 [ **相機設定提供者** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="e0798-142">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展開設定提供者](../Images/CameraSystem/ExpandProviders.png)

1. <span data-ttu-id="e0798-144">按一下 [新增 **相機設定提供者** ]，並展開新加入的 **新相機設定** 專案。</span><span class="sxs-lookup"><span data-stu-id="e0798-144">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展開新的設定提供者](../Images/CameraSystem/ExpandNewProvider.png)

1. <span data-ttu-id="e0798-146">選取 Unity AR 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="e0798-146">Select the Unity AR Camera Settings provider</span></span>

    ![選取 Unity AR 設定提供者](../Images/CameraSystem/SelectUnityArSettings.png)

    <span data-ttu-id="e0798-148">如需有關設定 Unity AR 攝影機設定提供者的詳細資訊： [UNITY ar 攝影機設定提供者](../CameraSystem/UnityArCameraSettings.md)。</span><span class="sxs-lookup"><span data-stu-id="e0798-148">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../CameraSystem/UnityArCameraSettings.md).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="e0798-149">建立適用于 Android 和 iOS 裝置的場景</span><span class="sxs-lookup"><span data-stu-id="e0798-149">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="e0798-150">確定您已將 UnityAR 攝影機設定提供者新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="e0798-150">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="e0798-151">將平臺切換至 Unity 組建設定中的 Android 或 iOS</span><span class="sxs-lookup"><span data-stu-id="e0798-151">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="e0798-152">當您切換平臺時，您應該會看到 [MRTK 專案設定] 視窗，其中包含您所選平臺的設定。</span><span class="sxs-lookup"><span data-stu-id="e0798-152">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="e0798-153">按一下 [套用] 以啟用平臺特定設定。</span><span class="sxs-lookup"><span data-stu-id="e0798-153">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="e0798-154">iOS 專案設定器設定</span><span class="sxs-lookup"><span data-stu-id="e0798-154">iOS Project Configurator Settings</span></span>

    ![iOS 專案配置器](../Images/CameraSystem/MRTKProjectConfigurator.png)

1. <span data-ttu-id="e0798-156">切換 Android 的平臺後，不需要額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="e0798-156">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="e0798-157">如果平臺是 iOS，請編輯 > 專案設定 > 播放程式 > 其他設定，請在優化標頭下， **取消** 核取 [去除引擎程式碼]</span><span class="sxs-lookup"><span data-stu-id="e0798-157">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![iOS 設定](../Images/CameraSystem/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="e0798-159">取消核取區域引擎程式碼是 Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)的錯誤的短期解決方案。</span><span class="sxs-lookup"><span data-stu-id="e0798-159">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="e0798-160">我們正致力於長期解決方案。</span><span class="sxs-lookup"><span data-stu-id="e0798-160">We are working on a long term solution.</span></span>

1. <span data-ttu-id="e0798-161">建立並執行場景</span><span class="sxs-lookup"><span data-stu-id="e0798-161">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="e0798-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0798-162">See also</span></span>

- [<span data-ttu-id="e0798-163">Unity AR 相機設定</span><span class="sxs-lookup"><span data-stu-id="e0798-163">Unity AR Camera Settings</span></span>](../CameraSystem/UnityArCameraSettings.md)
