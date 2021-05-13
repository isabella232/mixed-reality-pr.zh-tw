---
title: OculusQuestMRTK
description: 在 MRTK 中設定 Oculus 的相關檔
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Oculus 的追求、
ms.openlocfilehash: 9350ed7c8426c3bb31cf41493056fb6fc1e26107
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852335"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a><span data-ttu-id="88557-104">如何使用 XR SDK 管線在 MRTK 中設定 Oculus 操作</span><span class="sxs-lookup"><span data-stu-id="88557-104">How to configure Oculus Quest in MRTK using the XR SDK pipeline</span></span>

<span data-ttu-id="88557-105">需要進行 [Oculus](https://www.oculus.com/quest/) 。</span><span class="sxs-lookup"><span data-stu-id="88557-105">A [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="88557-106">MRTK 對 Oculus 的支援有兩個不同的來源： Unity 的 XR 管線和 Oculus Integration Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="88557-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="88557-107">**OCULUS XRSDK Data Provider** 可讓您同時使用這兩個來源，而且必須用來在 Oculus 上使用 MRTK。</span><span class="sxs-lookup"><span data-stu-id="88557-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to use MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="88557-108">[Unity 的 XR 管線](https://docs.unity3d.com/Manual/XR.html)可讓您使用 Oculus 觸控控制器並搭配 Oculus 的進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="88557-108">The [Unity's XR Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="88557-109">此管線是在 Unity 2019.3 和更多功能中開發 XR 應用程式的標準。</span><span class="sxs-lookup"><span data-stu-id="88557-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="88557-110">若要使用此管線，請確定您使用的是 **Unity 2019.3 或更新版本**。</span><span class="sxs-lookup"><span data-stu-id="88557-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span>

<span data-ttu-id="88557-111">[Oculus Integration Unity 封裝](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)可讓您搭配 Oculus 的執行來使用 **手動追蹤**。</span><span class="sxs-lookup"><span data-stu-id="88557-111">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span>
<span data-ttu-id="88557-112">此資料提供者 **不會使用 unity** 的 **XR 管線** 或 **舊版 XR 管線**，但因為控制器和 Headtracking 是由 Unity 的 XR 管線處理，所以必須遵循為 **Oculus 執行設定專案** 的步驟，以確保您使用的是 **XR 管線** ，而不是即將淘汰的 **舊版 XR 管線**。</span><span class="sxs-lookup"><span data-stu-id="88557-112">This data provider does **NOT** use Unity's **XR Pipeline** or **Legacy XR Pipeline**, but because controllers and headtracking are handled by the Unity's XR Pipeline, the steps in **Setting up project for the Oculus Quest** must be followed to ensure that you are using the **XR Pipeline** and not the to-be-deprecated **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="88557-113">設定專案以進行 Oculus 的尋找</span><span class="sxs-lookup"><span data-stu-id="88557-113">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="88557-114">請遵循下列 [步驟](https://developer.oculus.com/documentation/unity/book-unity-gsg/) ，以確保您的專案已準備好在 Oculus 時進行部署。</span><span class="sxs-lookup"><span data-stu-id="88557-114">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="88557-115">確定已在您的裝置上啟用 [開發人員模式](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 。</span><span class="sxs-lookup"><span data-stu-id="88557-115">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="88557-116">安裝 Oculus ADB 驅動程式是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="88557-116">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a><span data-ttu-id="88557-117">設定 XR 管線以進行 Oculus 的尋找</span><span class="sxs-lookup"><span data-stu-id="88557-117">Setting up the XR Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="88557-118">確定 **OCULUS XR 外掛程式** 已安裝在視窗下 **--> 封裝管理員**</span><span class="sxs-lookup"><span data-stu-id="88557-118">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR 外掛程式套件](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="88557-120">前往 [**編輯--> 專案設定--> XR 外掛程式管理--> 外掛程式提供** 者]，以確定專案中包含 Oculus 外掛程式提供者</span><span class="sxs-lookup"><span data-stu-id="88557-120">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus 外掛程式提供者](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="88557-122">設定 Oculus Integration Unity 套件以啟用 handtracking</span><span class="sxs-lookup"><span data-stu-id="88557-122">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="88557-123">從 Unity 資產存放區下載並匯入 [Oculus 整合](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 。</span><span class="sxs-lookup"><span data-stu-id="88557-123">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="88557-124">測試的最新版本是20.0.0。</span><span class="sxs-lookup"><span data-stu-id="88557-124">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="88557-125">您[可以從此封存](https://developer.oculus.com/downloads/package/unity-integration-archive/)中找到較舊的版本</span><span class="sxs-lookup"><span data-stu-id="88557-125">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="88557-126">流覽至混合現實工具組 > 公用程式 > Oculus > 整合 Oculus Integration Unity 模組。</span><span class="sxs-lookup"><span data-stu-id="88557-126">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="88557-127">這麼做會使用相關 Oculus 執行程式碼運作所需的定義和參考，來更新 asmdefs。</span><span class="sxs-lookup"><span data-stu-id="88557-127">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="88557-128">它也會更新 csc 檔案，以篩選出 Oculus 整合資產所產生的過時警告。</span><span class="sxs-lookup"><span data-stu-id="88557-128">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="88557-129">MRTK 存放庫包含將警告轉換成錯誤的 csc 檔案，這種轉換會中止 MRTK-Quest 設定程式。</span><span class="sxs-lookup"><span data-stu-id="88557-129">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus 整合 Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="88557-131">在匯入的 Oculus 資料夾中 (應該在資產/Oculus) 找到，其中有一個可編寫腳本的物件，稱為 OculusProjectConfig。</span><span class="sxs-lookup"><span data-stu-id="88557-131">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="88557-132">在該設定檔中，您必須將 HandTrackingSupport 設定為「控制器和手」。</span><span class="sxs-lookup"><span data-stu-id="88557-132">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus 整合控制器與手](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="88557-134">設定場景</span><span class="sxs-lookup"><span data-stu-id="88557-134">Setting up the scene</span></span>

1. <span data-ttu-id="88557-135">建立新的 Unity 場景，或開啟預先存在的場景，例如 HandInteractionExamples</span><span class="sxs-lookup"><span data-stu-id="88557-135">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="88557-136">流覽至 **混合現實工具** 組  >  **新增至場景並設定**，以將 MRTK 新增至場景</span><span class="sxs-lookup"><span data-stu-id="88557-136">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="88557-137">使用 Oculus XR SDK Data Provider</span><span class="sxs-lookup"><span data-stu-id="88557-137">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="88557-138">將您的設定檔設定為使用 **OCULUS XR SDK Data Provider**</span><span class="sxs-lookup"><span data-stu-id="88557-138">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="88557-139">如果不打算修改設定設定檔</span><span class="sxs-lookup"><span data-stu-id="88557-139">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="88557-140">將您的設定檔變更為 DefaultXRSDKConfigurationProfile，然後移至 [ [組建]，並將專案部署至 Oculus 的追求](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="88557-140">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="88557-141">否則，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="88557-141">Otherwise follow the following:</span></span>
        - <span data-ttu-id="88557-142">選取階層中的 MixedRealityToolkit 遊戲物件，然後選取 [ **複製和自訂** ] 以複製預設的混合現實設定檔。</span><span class="sxs-lookup"><span data-stu-id="88557-142">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![複製設定檔](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="88557-144">選取 **輸入** 設定設定檔</span><span class="sxs-lookup"><span data-stu-id="88557-144">Select the **Input** Configuration Profile</span></span>

        ![輸入設定設定檔](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="88557-146">在輸入系統設定檔中選取 [ **複製** ]，以啟用修改。</span><span class="sxs-lookup"><span data-stu-id="88557-146">Select **Clone** in the input system profile to enable modification.</span></span>

        ![複製輸入系統設定檔](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="88557-148">開啟 [ **輸入資料提供者** ] 區段，選取頂端的 [ **新增 Data Provider** ，然後在清單結尾加入新的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="88557-148">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="88557-149">開啟新的資料提供者，並將類型設為 MixedReality，並將 **類型** 設定為 **XRSDK. Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="88557-149">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Oculus 新增 XRSDK Data Provider](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="88557-151">Oculus XR SDK Data Provider 包含 OVR 相機 Rig 預製專案，此會使用 OVR 攝影機 Rig 自動設定專案，並 OVR 手以正確地路由輸入。</span><span class="sxs-lookup"><span data-stu-id="88557-151">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="88557-152">手動將 OVR 攝影機裝備新增至場景需要手動設定設定和輸入。</span><span class="sxs-lookup"><span data-stu-id="88557-152">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="88557-153">建立您的專案，並將其部署至 Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="88557-153">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="88557-154">透過 USB 3.0-> USB C 纜線插入 Oculus 的尋找</span><span class="sxs-lookup"><span data-stu-id="88557-154">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="88557-155">流覽至檔案 **> 組建設定**</span><span class="sxs-lookup"><span data-stu-id="88557-155">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="88557-156">將部署變更為 **Android**</span><span class="sxs-lookup"><span data-stu-id="88557-156">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="88557-157">確定已選取 [Oculus]，作為適用的執行裝置</span><span class="sxs-lookup"><span data-stu-id="88557-157">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus 執行裝置](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="88557-159">選取組建並執行</span><span class="sxs-lookup"><span data-stu-id="88557-159">Select Build and Run</span></span>
    - <span data-ttu-id="88557-160">當您第一次選取 *組建並執行* 時，可能會遇到下列一組組建錯誤。</span><span class="sxs-lookup"><span data-stu-id="88557-160">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="88557-161">當您選取 [ *組建] 並重新執行* 時，應該可以成功部署。</span><span class="sxs-lookup"><span data-stu-id="88557-161">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus 預期的組建錯誤](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="88557-163">接受來自要求內的 _允許 USB 調試_</span><span class="sxs-lookup"><span data-stu-id="88557-163">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="88557-164">查看 Oculus 中的場景</span><span class="sxs-lookup"><span data-stu-id="88557-164">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="88557-165">從專案移除 Oculus 整合</span><span class="sxs-lookup"><span data-stu-id="88557-165">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="88557-166">流覽至混合現實工具組 > Oculus > 個別的 Oculus Integration Unity 模組  ![ Oculus 分隔 Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="88557-166">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="88557-167">讓 Unity 重新整理為 MixedReality 中的參考，在此步驟中會修改 Oculus asmdef 和其他檔案</span><span class="sxs-lookup"><span data-stu-id="88557-167">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="88557-168">關閉 Unity</span><span class="sxs-lookup"><span data-stu-id="88557-168">Close Unity</span></span>
1. <span data-ttu-id="88557-169">關閉 Visual Studio （如果已開啟）</span><span class="sxs-lookup"><span data-stu-id="88557-169">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="88557-170">開啟檔案總管並流覽至 MRTK Unity 專案的根目錄</span><span class="sxs-lookup"><span data-stu-id="88557-170">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="88557-171">刪除 UnityProjectName/Library 目錄</span><span class="sxs-lookup"><span data-stu-id="88557-171">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="88557-172">刪除 UnityProjectName/資產/Oculus 目錄</span><span class="sxs-lookup"><span data-stu-id="88557-172">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="88557-173">刪除 UnityProjectName/資產/Oculus 中繼檔案</span><span class="sxs-lookup"><span data-stu-id="88557-173">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="88557-174">重新開啟 Unity</span><span class="sxs-lookup"><span data-stu-id="88557-174">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="88557-175">常見錯誤</span><span class="sxs-lookup"><span data-stu-id="88557-175">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="88557-176">Unity 無法辨識的找出</span><span class="sxs-lookup"><span data-stu-id="88557-176">Quest not recognized by Unity</span></span>

<span data-ttu-id="88557-177">請確定您的 Android 路徑已正確設定。</span><span class="sxs-lookup"><span data-stu-id="88557-177">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="88557-178">如果您持續遇到問題，請遵循本 [指南](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="88557-178">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="88557-179">**編輯 > 喜好設定 > 外部工具 > Android**</span><span class="sxs-lookup"><span data-stu-id="88557-179">**Edit > Preferences > External Tools > Android**</span></span>

![Android 工具設定](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
