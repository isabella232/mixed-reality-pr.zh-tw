---
title: UsingARFoundation
description: 在 unity 中使用 ARFoundation 的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、AR Core、AR 套件
ms.openlocfilehash: c2cafe6e8133dfd6970ba9d5e8f824dea37783f1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781169"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="a7c7f-104">如何設定 iOS 和 Android 的 MRTK [實驗]</span><span class="sxs-lookup"><span data-stu-id="a7c7f-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="a7c7f-105">安裝必要的套件</span><span class="sxs-lookup"><span data-stu-id="a7c7f-105">Install required packages</span></span>

1. <span data-ttu-id="a7c7f-106">從 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0)或 [Unity 套件管理員](../../configuration/usingupm.md)下載並匯入 **MixedReality 套件。**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="a7c7f-107">在 Unity 套件管理員 (UPM) 中，安裝下列套件：</span><span class="sxs-lookup"><span data-stu-id="a7c7f-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="a7c7f-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="a7c7f-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-109">**Android**</span></span> | <span data-ttu-id="a7c7f-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-110">**iOS**</span></span> | <span data-ttu-id="a7c7f-111">註解</span><span class="sxs-lookup"><span data-stu-id="a7c7f-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="a7c7f-112">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="a7c7f-112">AR Foundation</span></span>  <br/> <span data-ttu-id="a7c7f-113">版本： 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="a7c7f-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="a7c7f-114">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="a7c7f-114">AR Foundation</span></span>  <br/> <span data-ttu-id="a7c7f-115">版本： 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="a7c7f-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="a7c7f-116">針對 Unity 2018.4，此套件包含為預覽版本。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="a7c7f-117">若要查看套件： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="a7c7f-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="a7c7f-118">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="a7c7f-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="a7c7f-119">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="a7c7f-119">Version: 2.1.2</span></span> | <span data-ttu-id="a7c7f-120">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="a7c7f-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="a7c7f-121">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="a7c7f-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="a7c7f-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="a7c7f-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-123">**Android**</span></span> | <span data-ttu-id="a7c7f-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="a7c7f-125">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="a7c7f-125">AR Foundation</span></span>  <br/> <span data-ttu-id="a7c7f-126">版本：2.1。8</span><span class="sxs-lookup"><span data-stu-id="a7c7f-126">Version: 2.1.8</span></span> |  <span data-ttu-id="a7c7f-127">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="a7c7f-127">AR Foundation</span></span>  <br/> <span data-ttu-id="a7c7f-128">版本：2.1。8</span><span class="sxs-lookup"><span data-stu-id="a7c7f-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="a7c7f-129">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="a7c7f-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="a7c7f-130">版本：2.1.11</span><span class="sxs-lookup"><span data-stu-id="a7c7f-130">Version: 2.1.11</span></span> | <span data-ttu-id="a7c7f-131">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="a7c7f-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="a7c7f-132">版本：2.1。9</span><span class="sxs-lookup"><span data-stu-id="a7c7f-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="a7c7f-133">**Unity 2020.1 (目前尚未正式支援，僅包含供資訊用途之用)**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="a7c7f-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-134">**Android**</span></span> | <span data-ttu-id="a7c7f-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="a7c7f-136">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="a7c7f-136">AR Foundation</span></span>  <br/> <span data-ttu-id="a7c7f-137">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="a7c7f-137">Version: 3.1.3</span></span> |  <span data-ttu-id="a7c7f-138">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="a7c7f-138">AR Foundation</span></span>  <br/> <span data-ttu-id="a7c7f-139">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="a7c7f-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="a7c7f-140">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="a7c7f-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="a7c7f-141">版本：3.1。4</span><span class="sxs-lookup"><span data-stu-id="a7c7f-141">Version: 3.1.4</span></span> | <span data-ttu-id="a7c7f-142">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="a7c7f-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="a7c7f-143">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="a7c7f-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="a7c7f-144">藉由叫用功能表項目來更新 MRTK UnityAR 腳本定義： **混合現實工具組 > 公用程式 > UnityAR > 更新腳本定義**</span><span class="sxs-lookup"><span data-stu-id="a7c7f-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="a7c7f-145">啟用 Unity AR 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="a7c7f-145">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="a7c7f-146">下列步驟假設使用 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-146">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="a7c7f-147">其他服務註冊機構所需的步驟可能會不同。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-147">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="a7c7f-148">選取場景階層中的 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-148">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="a7c7f-150">選取 [ **複製並自訂** ] 以複製 MRTK 設定檔，以啟用自訂設定。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-150">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![複製 MRTK 設定檔](../images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="a7c7f-152">選取相機設定檔旁邊的 [ **複製** ]。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-152">Select **Clone** next to the Camera Profile.</span></span>

    ![複製 MRTK 攝影機設定檔](../images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="a7c7f-154">將 [偵測器] 面板移至 [相機系統] 區段，然後展開 [ **相機設定提供者** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-154">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展開設定提供者](../images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="a7c7f-156">按一下 [新增 **相機設定提供者** ]，並展開新加入的 **新相機設定** 專案。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-156">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展開新的設定提供者](../images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="a7c7f-158">選取 Unity AR 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="a7c7f-158">Select the Unity AR Camera Settings provider</span></span>

    ![選取 Unity AR 設定提供者](../images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="a7c7f-160">如需有關設定 Unity AR 攝影機設定提供者的詳細資訊： [UNITY ar 攝影機設定提供者](../camera-system/unity-ar-camera-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-160">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a7c7f-161">此安裝會在應用程式啟動時檢查 () 如果 AR 基礎元件在場景中。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-161">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="a7c7f-162">如果沒有，則會自動新增它們，使其可搭配 ARCore 和 ARKit 使用。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-162">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="a7c7f-163">如果您需要設定特定行為，您應該自行新增您需要的元件。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-163">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="a7c7f-164">如需 AR 基礎元件和安裝的詳細資訊，請參閱此 [檔](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-164">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="a7c7f-165">建立適用于 Android 和 iOS 裝置的場景</span><span class="sxs-lookup"><span data-stu-id="a7c7f-165">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="a7c7f-166">確定您已將 UnityAR 攝影機設定提供者新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-166">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="a7c7f-167">將平臺切換至 Unity 組建設定中的 Android 或 iOS</span><span class="sxs-lookup"><span data-stu-id="a7c7f-167">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

    <span data-ttu-id="a7c7f-168">當您切換平臺時，您應該會看到 [MRTK 專案設定] 視窗，其中包含您所選平臺的設定。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-168">When you switch the platform you should see the MRTK Project Configurator Window with settings for your chosen platform.</span></span>  <span data-ttu-id="a7c7f-169">按一下 [套用] 以啟用平臺特定設定。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-169">Click Apply to enable platform specific settings.</span></span>

    <span data-ttu-id="a7c7f-170">iOS 專案設定器設定</span><span class="sxs-lookup"><span data-stu-id="a7c7f-170">iOS Project Configurator Settings</span></span>

    ![iOS 專案配置器](../images/camera-system/MRTKProjectConfigurator.png)

1. <span data-ttu-id="a7c7f-172">切換 Android 的平臺後，不需要額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-172">There are no additional steps after switching the platform for Android.</span></span>

1. <span data-ttu-id="a7c7f-173">如果平臺是 iOS，請編輯 > 專案設定 > 播放程式 > 其他設定，請在優化標頭下， **取消** 核取 [去除引擎程式碼]</span><span class="sxs-lookup"><span data-stu-id="a7c7f-173">If the platform is iOS, Edit > Project Settings > Player > Other Settings, under the Optimization header, **uncheck** Strip Engine Code</span></span>

    ![iOS 設定](../images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > <span data-ttu-id="a7c7f-175">取消核取區域引擎程式碼是 Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)的錯誤的短期解決方案。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-175">Unchecking Strip Engine Code is the short term solution to an error in Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646).</span></span>  <span data-ttu-id="a7c7f-176">我們正致力於長期解決方案。</span><span class="sxs-lookup"><span data-stu-id="a7c7f-176">We are working on a long term solution.</span></span>

1. <span data-ttu-id="a7c7f-177">建立並執行場景</span><span class="sxs-lookup"><span data-stu-id="a7c7f-177">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="a7c7f-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7c7f-178">See also</span></span>

- [<span data-ttu-id="a7c7f-179">Unity AR 相機設定</span><span class="sxs-lookup"><span data-stu-id="a7c7f-179">Unity AR Camera Settings</span></span>](../camera-system/unity-ar-camera-settings.md)
