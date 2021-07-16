---
title: 部署至 Android 和 iOS (AR Foundation) [實驗]
description: 在 unity 中為 Android 和 iOS (ARFoundation) 設定 MRTK 的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、AR Core、ar 套件、ios、ios、Android、ar Foundation
ms.openlocfilehash: d127b9b39cbaa90f0c8c5a8a6ac7955f33404cbf
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281944"
---
# <a name="deploying-to-android-and-ios-ar-foundation-experimental"></a><span data-ttu-id="2fe39-104">部署至 Android 和 iOS (AR Foundation) [實驗]</span><span class="sxs-lookup"><span data-stu-id="2fe39-104">Deploying to Android and iOS (AR Foundation) [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="2fe39-105">安裝必要的套件</span><span class="sxs-lookup"><span data-stu-id="2fe39-105">Install required packages</span></span>

1. <span data-ttu-id="2fe39-106">從 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/)或 [Unity 封裝管理員](../configuration/usingupm.md)下載並匯入 MixedReality 的套件 **。**</span><span class="sxs-lookup"><span data-stu-id="2fe39-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="2fe39-107">在 Unity 封裝管理員 (UPM) 中，安裝下列套件：</span><span class="sxs-lookup"><span data-stu-id="2fe39-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="2fe39-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="2fe39-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="2fe39-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="2fe39-109">**Android**</span></span> | <span data-ttu-id="2fe39-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="2fe39-110">**iOS**</span></span> | <span data-ttu-id="2fe39-111">註解</span><span class="sxs-lookup"><span data-stu-id="2fe39-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="2fe39-112">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="2fe39-112">AR Foundation</span></span>  <br/> <span data-ttu-id="2fe39-113">版本： 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="2fe39-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="2fe39-114">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="2fe39-114">AR Foundation</span></span>  <br/> <span data-ttu-id="2fe39-115">版本： 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="2fe39-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="2fe39-116">針對 Unity 2018.4，此套件包含為預覽版本。</span><span class="sxs-lookup"><span data-stu-id="2fe39-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="2fe39-117">若要查看套件： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="2fe39-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="2fe39-118">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="2fe39-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="2fe39-119">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="2fe39-119">Version: 2.1.2</span></span> | <span data-ttu-id="2fe39-120">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="2fe39-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="2fe39-121">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="2fe39-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="2fe39-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="2fe39-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="2fe39-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="2fe39-123">**Android**</span></span> | <span data-ttu-id="2fe39-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="2fe39-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="2fe39-125">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="2fe39-125">AR Foundation</span></span>  <br/> <span data-ttu-id="2fe39-126">版本：2.1。8</span><span class="sxs-lookup"><span data-stu-id="2fe39-126">Version: 2.1.8</span></span> |  <span data-ttu-id="2fe39-127">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="2fe39-127">AR Foundation</span></span>  <br/> <span data-ttu-id="2fe39-128">版本：2.1。8</span><span class="sxs-lookup"><span data-stu-id="2fe39-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="2fe39-129">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="2fe39-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="2fe39-130">版本：2.1.11</span><span class="sxs-lookup"><span data-stu-id="2fe39-130">Version: 2.1.11</span></span> | <span data-ttu-id="2fe39-131">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="2fe39-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="2fe39-132">版本：2.1。9</span><span class="sxs-lookup"><span data-stu-id="2fe39-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="2fe39-133">**Unity 2020.3. x**</span><span class="sxs-lookup"><span data-stu-id="2fe39-133">**Unity 2020.3.x**</span></span>

    | <span data-ttu-id="2fe39-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="2fe39-134">**Android**</span></span> | <span data-ttu-id="2fe39-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="2fe39-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="2fe39-136">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="2fe39-136">AR Foundation</span></span>  <br/> <span data-ttu-id="2fe39-137">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="2fe39-137">Version: 3.1.3</span></span> |  <span data-ttu-id="2fe39-138">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="2fe39-138">AR Foundation</span></span>  <br/> <span data-ttu-id="2fe39-139">版本：4.0.12</span><span class="sxs-lookup"><span data-stu-id="2fe39-139">Version: 4.0.12</span></span> |
    | <span data-ttu-id="2fe39-140">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="2fe39-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="2fe39-141">版本：3.1。4</span><span class="sxs-lookup"><span data-stu-id="2fe39-141">Version: 3.1.4</span></span> | <span data-ttu-id="2fe39-142">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="2fe39-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="2fe39-143">版本：4.1。7</span><span class="sxs-lookup"><span data-stu-id="2fe39-143">Version: 4.1.7</span></span> |

1. <span data-ttu-id="2fe39-144">藉由叫用功能表項目來更新 MRTK UnityAR 腳本定義： **混合現實 > 工具組 > 公用程式 > UnityAR > 更新腳本定義**</span><span class="sxs-lookup"><span data-stu-id="2fe39-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![更新腳本定義](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="2fe39-146">啟用 Unity AR 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="2fe39-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="2fe39-147">下列步驟假設使用 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="2fe39-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="2fe39-148">其他服務註冊機構所需的步驟可能會不同。</span><span class="sxs-lookup"><span data-stu-id="2fe39-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="2fe39-149">選取場景階層中的 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="2fe39-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 設定的場景階層](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="2fe39-151">選取 [ **複製並自訂** ] 以複製 MRTK 設定檔，以啟用自訂設定。</span><span class="sxs-lookup"><span data-stu-id="2fe39-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![複製 MRTK 設定檔](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="2fe39-153">選取相機設定檔旁邊的 [ **複製** ]。</span><span class="sxs-lookup"><span data-stu-id="2fe39-153">Select **Clone** next to the Camera Profile.</span></span>

    ![複製 MRTK 攝影機設定檔](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="2fe39-155">將 [偵測器] 面板移至 [相機系統] 區段，然後展開 [**相機設定提供者**] 區段。</span><span class="sxs-lookup"><span data-stu-id="2fe39-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展開設定提供者](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="2fe39-157">按一下 [新增 **相機設定提供者**]，並展開新加入的 **新相機設定** 專案。</span><span class="sxs-lookup"><span data-stu-id="2fe39-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展開新的設定提供者](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="2fe39-159">選取 Unity AR 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="2fe39-159">Select the Unity AR Camera Settings provider</span></span>

    ![選取 Unity AR 設定提供者](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="2fe39-161">如需有關設定 Unity AR 攝影機設定提供者的詳細資訊： [UNITY ar 攝影機設定提供者](../features/camera-system/unity-ar-camera-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="2fe39-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2fe39-162">此安裝會在應用程式啟動時檢查 () 如果 AR 基礎元件在場景中。</span><span class="sxs-lookup"><span data-stu-id="2fe39-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="2fe39-163">如果沒有，則會自動新增它們，使其可搭配 ARCore 和 ARKit 使用。</span><span class="sxs-lookup"><span data-stu-id="2fe39-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="2fe39-164">如果您需要設定特定行為，您應該自行新增您需要的元件。</span><span class="sxs-lookup"><span data-stu-id="2fe39-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="2fe39-165">如需 AR 基礎元件和安裝的詳細資訊，請參閱此 [檔](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)。</span><span class="sxs-lookup"><span data-stu-id="2fe39-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="2fe39-166">建立適用于 Android 和 iOS 裝置的場景</span><span class="sxs-lookup"><span data-stu-id="2fe39-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="2fe39-167">請確定您已將 UnityAR 攝影機設定提供者新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="2fe39-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="2fe39-168">將平臺切換至 Unity 組建中的 Android 或 iOS 設定</span><span class="sxs-lookup"><span data-stu-id="2fe39-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="2fe39-169">確定已啟用相關聯的 XR 外掛程式管理提供者</span><span class="sxs-lookup"><span data-stu-id="2fe39-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="2fe39-170">iOS XR 外掛程式管理：  ![ XR 外掛程式管理 ios](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="2fe39-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="2fe39-171">建立並執行場景</span><span class="sxs-lookup"><span data-stu-id="2fe39-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="2fe39-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fe39-172">See also</span></span>

- [<span data-ttu-id="2fe39-173">Unity AR 攝影機設定</span><span class="sxs-lookup"><span data-stu-id="2fe39-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
