---
title: 使用 AR Foundation
description: 在 unity 中使用 ARFoundation 的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、AR Core、AR 套件、iOS、IOS、Android、AR Foundation
ms.openlocfilehash: 0f02eb94d95c2900348adaa9e1a02c3e54832a96
ms.sourcegitcommit: 62beb626b2db6ce7df86014bd22bf1946b8906b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2021
ms.locfileid: "110207444"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a><span data-ttu-id="11f0b-104">如何設定 iOS 和 Android 的 MRTK [實驗]</span><span class="sxs-lookup"><span data-stu-id="11f0b-104">How to configure MRTK for iOS and Android [Experimental]</span></span>

## <a name="install-required-packages"></a><span data-ttu-id="11f0b-105">安裝必要的套件</span><span class="sxs-lookup"><span data-stu-id="11f0b-105">Install required packages</span></span>

1. <span data-ttu-id="11f0b-106">從 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0)或 [Unity 封裝管理員](../configuration/usingupm.md)下載並匯入 **MixedReality 的套件。**</span><span class="sxs-lookup"><span data-stu-id="11f0b-106">Download and import the **Microsoft.MixedReality.Toolkit.Unity.Foundation** package, from [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) or the [Unity Package Manager](../configuration/usingupm.md)</span></span>

1. <span data-ttu-id="11f0b-107">在 Unity 封裝管理員 (UPM) 中，安裝下列套件：</span><span class="sxs-lookup"><span data-stu-id="11f0b-107">In the Unity Package Manager (UPM), install the following packages:</span></span>

    <span data-ttu-id="11f0b-108">**Unity 2018.4.x**</span><span class="sxs-lookup"><span data-stu-id="11f0b-108">**Unity 2018.4.x**</span></span>

    | <span data-ttu-id="11f0b-109">**Android**</span><span class="sxs-lookup"><span data-stu-id="11f0b-109">**Android**</span></span> | <span data-ttu-id="11f0b-110">**iOS**</span><span class="sxs-lookup"><span data-stu-id="11f0b-110">**iOS**</span></span> | <span data-ttu-id="11f0b-111">註解</span><span class="sxs-lookup"><span data-stu-id="11f0b-111">Comments</span></span> |
    | --- | --- | --- |
    | <span data-ttu-id="11f0b-112">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="11f0b-112">AR Foundation</span></span>  <br/> <span data-ttu-id="11f0b-113">版本： 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="11f0b-113">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="11f0b-114">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="11f0b-114">AR Foundation</span></span>  <br/> <span data-ttu-id="11f0b-115">版本： 1.5.0-preview 6</span><span class="sxs-lookup"><span data-stu-id="11f0b-115">Version: 1.5.0 - preview 6</span></span> | <span data-ttu-id="11f0b-116">針對 Unity 2018.4，此套件包含為預覽版本。</span><span class="sxs-lookup"><span data-stu-id="11f0b-116">For Unity 2018.4, this package is included as a preview.</span></span> <span data-ttu-id="11f0b-117">若要查看套件： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span><span class="sxs-lookup"><span data-stu-id="11f0b-117">To view the package: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages`</span></span> |
    | <span data-ttu-id="11f0b-118">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="11f0b-118">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="11f0b-119">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="11f0b-119">Version: 2.1.2</span></span> | <span data-ttu-id="11f0b-120">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="11f0b-120">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="11f0b-121">版本：2.1。2</span><span class="sxs-lookup"><span data-stu-id="11f0b-121">Version: 2.1.2</span></span> | |

    <span data-ttu-id="11f0b-122">**Unity 2019.4. x**</span><span class="sxs-lookup"><span data-stu-id="11f0b-122">**Unity 2019.4.x**</span></span>

    | <span data-ttu-id="11f0b-123">**Android**</span><span class="sxs-lookup"><span data-stu-id="11f0b-123">**Android**</span></span> | <span data-ttu-id="11f0b-124">**iOS**</span><span class="sxs-lookup"><span data-stu-id="11f0b-124">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="11f0b-125">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="11f0b-125">AR Foundation</span></span>  <br/> <span data-ttu-id="11f0b-126">版本：2.1。8</span><span class="sxs-lookup"><span data-stu-id="11f0b-126">Version: 2.1.8</span></span> |  <span data-ttu-id="11f0b-127">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="11f0b-127">AR Foundation</span></span>  <br/> <span data-ttu-id="11f0b-128">版本：2.1。8</span><span class="sxs-lookup"><span data-stu-id="11f0b-128">Version: 2.1.8</span></span> |
    | <span data-ttu-id="11f0b-129">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="11f0b-129">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="11f0b-130">版本：2.1.11</span><span class="sxs-lookup"><span data-stu-id="11f0b-130">Version: 2.1.11</span></span> | <span data-ttu-id="11f0b-131">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="11f0b-131">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="11f0b-132">版本：2.1。9</span><span class="sxs-lookup"><span data-stu-id="11f0b-132">Version: 2.1.9</span></span> |

    <span data-ttu-id="11f0b-133">**Unity 2020.1 (目前尚未正式支援，僅包含供資訊用途之用)**</span><span class="sxs-lookup"><span data-stu-id="11f0b-133">**Unity 2020.1.x (Not currently formally supported, included for informational purposes only)**</span></span>

    | <span data-ttu-id="11f0b-134">**Android**</span><span class="sxs-lookup"><span data-stu-id="11f0b-134">**Android**</span></span> | <span data-ttu-id="11f0b-135">**iOS**</span><span class="sxs-lookup"><span data-stu-id="11f0b-135">**iOS**</span></span> |
    | --- | --- |
    | <span data-ttu-id="11f0b-136">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="11f0b-136">AR Foundation</span></span>  <br/> <span data-ttu-id="11f0b-137">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="11f0b-137">Version: 3.1.3</span></span> |  <span data-ttu-id="11f0b-138">AR 基礎</span><span class="sxs-lookup"><span data-stu-id="11f0b-138">AR Foundation</span></span>  <br/> <span data-ttu-id="11f0b-139">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="11f0b-139">Version: 3.1.3</span></span> |
    | <span data-ttu-id="11f0b-140">ARCore XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="11f0b-140">ARCore XR Plugin</span></span> <br/> <span data-ttu-id="11f0b-141">版本：3.1。4</span><span class="sxs-lookup"><span data-stu-id="11f0b-141">Version: 3.1.4</span></span> | <span data-ttu-id="11f0b-142">ARKit XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="11f0b-142">ARKit XR Plugin</span></span> <br/> <span data-ttu-id="11f0b-143">版本：3.1。3</span><span class="sxs-lookup"><span data-stu-id="11f0b-143">Version: 3.1.3</span></span> |

1. <span data-ttu-id="11f0b-144">藉由叫用功能表項目來更新 MRTK UnityAR 腳本定義： **混合現實 > 工具組 > 公用程式 > UnityAR > 更新腳本定義**</span><span class="sxs-lookup"><span data-stu-id="11f0b-144">Update the MRTK UnityAR scripting defines by invoking the menu item: **Mixed Reality > Toolkit > Utilities > UnityAR > Update Scripting Defines**</span></span>

    ![更新腳本定義](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a><span data-ttu-id="11f0b-146">啟用 Unity AR 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="11f0b-146">Enabling the Unity AR camera settings provider</span></span>

<span data-ttu-id="11f0b-147">下列步驟假設使用 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="11f0b-147">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="11f0b-148">其他服務註冊機構所需的步驟可能會不同。</span><span class="sxs-lookup"><span data-stu-id="11f0b-148">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="11f0b-149">選取場景階層中的 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="11f0b-149">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 設定的場景階層](../features/images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="11f0b-151">選取 [ **複製並自訂** ] 以複製 MRTK 設定檔，以啟用自訂設定。</span><span class="sxs-lookup"><span data-stu-id="11f0b-151">Select **Copy and Customize** to Clone the MRTK Profile to enable custom configuration.</span></span>

    ![複製 MRTK 設定檔](../features/images/camera-system/CloneProfileARFoundation.png)

1. <span data-ttu-id="11f0b-153">選取相機設定檔旁邊的 [ **複製** ]。</span><span class="sxs-lookup"><span data-stu-id="11f0b-153">Select **Clone** next to the Camera Profile.</span></span>

    ![複製 MRTK 攝影機設定檔](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. <span data-ttu-id="11f0b-155">將 [偵測器] 面板移至 [相機系統] 區段，然後展開 [ **相機設定提供者** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="11f0b-155">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展開設定提供者](../features/images/camera-system/ExpandProviders.png)

1. <span data-ttu-id="11f0b-157">按一下 [新增 **相機設定提供者** ]，並展開新加入的 **新相機設定** 專案。</span><span class="sxs-lookup"><span data-stu-id="11f0b-157">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展開新的設定提供者](../features/images/camera-system/ExpandNewProvider.png)

1. <span data-ttu-id="11f0b-159">選取 Unity AR 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="11f0b-159">Select the Unity AR Camera Settings provider</span></span>

    ![選取 Unity AR 設定提供者](../features/images/camera-system/SelectUnityArSettings.png)

    <span data-ttu-id="11f0b-161">如需有關設定 Unity AR 攝影機設定提供者的詳細資訊： [UNITY ar 攝影機設定提供者](../features/camera-system/unity-ar-camera-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="11f0b-161">For more information about configuring the Unity AR camera settings provider: [Unity AR camera settings provider](../features/camera-system/unity-ar-camera-settings.md).</span></span>

> [!NOTE]
> <span data-ttu-id="11f0b-162">此安裝會在應用程式啟動時檢查 () 如果 AR 基礎元件在場景中。</span><span class="sxs-lookup"><span data-stu-id="11f0b-162">This installation checks (when the application starts) if the AR Foundation components are in the scene.</span></span> <span data-ttu-id="11f0b-163">如果沒有，則會自動新增它們，使其可搭配 ARCore 和 ARKit 使用。</span><span class="sxs-lookup"><span data-stu-id="11f0b-163">If not, they are automatically added to make it work with ARCore and ARKit.</span></span>
> <span data-ttu-id="11f0b-164">如果您需要設定特定行為，您應該自行新增您需要的元件。</span><span class="sxs-lookup"><span data-stu-id="11f0b-164">If you need to set a specific behaviour, you should add the components you need by yourself.</span></span>
> <span data-ttu-id="11f0b-165">如需 AR 基礎元件和安裝的詳細資訊，請參閱此 [檔](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)。</span><span class="sxs-lookup"><span data-stu-id="11f0b-165">For more information about AR Foundation components and installation, check this [documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples).</span></span>

## <a name="building-a-scene-for-android-and-ios-devices"></a><span data-ttu-id="11f0b-166">建立適用于 Android 和 iOS 裝置的場景</span><span class="sxs-lookup"><span data-stu-id="11f0b-166">Building a scene for Android and iOS devices</span></span>

1. <span data-ttu-id="11f0b-167">確定您已將 UnityAR 攝影機設定提供者新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="11f0b-167">Make sure you have added the UnityAR Camera Settings Provider to your scene.</span></span>

1. <span data-ttu-id="11f0b-168">將平臺切換至 Unity 組建設定中的 Android 或 iOS</span><span class="sxs-lookup"><span data-stu-id="11f0b-168">Switch platform to either Android or iOS in the Unity Build Settings</span></span>

1. <span data-ttu-id="11f0b-169">確定已啟用相關聯的 XR 外掛程式管理提供者</span><span class="sxs-lookup"><span data-stu-id="11f0b-169">Ensure the associated XR Plug-in management provider is enabled</span></span>

    <span data-ttu-id="11f0b-170">iOS XR 外掛程式管理：  ![ XR 外掛程式管理 ios](../features/images/XRManagementiOS.png)</span><span class="sxs-lookup"><span data-stu-id="11f0b-170">iOS XR Plug-in Management:  ![XR Plug-in Management iOS](../features/images/XRManagementiOS.png)</span></span>

1. <span data-ttu-id="11f0b-171">建立並執行場景</span><span class="sxs-lookup"><span data-stu-id="11f0b-171">Build and run the scene</span></span>

## <a name="see-also"></a><span data-ttu-id="11f0b-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11f0b-172">See also</span></span>

- [<span data-ttu-id="11f0b-173">Unity AR 相機設定</span><span class="sxs-lookup"><span data-stu-id="11f0b-173">Unity AR Camera Settings</span></span>](../features/camera-system/unity-ar-camera-settings.md)
