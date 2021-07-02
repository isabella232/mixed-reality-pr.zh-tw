---
title: 部署至 Oculus 的追求
description: 在 MRTK 中設定 Oculus 的相關檔
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Oculus 的追求
ms.openlocfilehash: d910f26374b21be26377bd40b9be0d45872e007a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177450"
---
# <a name="deploying-to-oculus-quest"></a><span data-ttu-id="b6f87-104">部署至 Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="b6f87-104">Deploying to Oculus Quest</span></span>

<span data-ttu-id="b6f87-105">需要進行 [Oculus](https://www.oculus.com/quest/) 。</span><span class="sxs-lookup"><span data-stu-id="b6f87-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="b6f87-106">MRTK 對 Oculus 的支援有兩個不同的來源： Unity 的 XR SDK 管線和 Oculus Integration Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="b6f87-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="b6f87-107">**Oculus XRSDK Data Provider** 可讓您同時使用這兩個來源，而且必須用來在 Oculus 上部署 MRTK。</span><span class="sxs-lookup"><span data-stu-id="b6f87-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="b6f87-108">[UNITY XR SDK 管線](https://docs.unity3d.com/Manual/XR.html)可讓您使用 Oculus 觸控控制器並搭配 Oculus 的進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="b6f87-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="b6f87-109">此管線是在 Unity 2019.3 和更多功能中開發 XR 應用程式的標準。</span><span class="sxs-lookup"><span data-stu-id="b6f87-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="b6f87-110">若要使用此管線，請確定您使用的是 **Unity 2019.3 或更新版本**。</span><span class="sxs-lookup"><span data-stu-id="b6f87-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="b6f87-111">這是將 MRTK 應用程式部署到 Oculus 的 **要求所需** 的。</span><span class="sxs-lookup"><span data-stu-id="b6f87-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="b6f87-112">[Oculus Integration Unity 封裝](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)可讓您搭配 Oculus 的執行來使用 **手動追蹤**。</span><span class="sxs-lookup"><span data-stu-id="b6f87-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="b6f87-113">此資料提供者 **不會使用 Unity** 的 **XR SDK 管線** 或 **舊版 XR 管線**。</span><span class="sxs-lookup"><span data-stu-id="b6f87-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="b6f87-114">設定專案以進行 Oculus 的尋找</span><span class="sxs-lookup"><span data-stu-id="b6f87-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="b6f87-115">請遵循下列 [步驟](https://developer.oculus.com/documentation/unity/book-unity-gsg/) ，以確保您的專案已準備好在 Oculus 時進行部署。</span><span class="sxs-lookup"><span data-stu-id="b6f87-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="b6f87-116">確定已在您的裝置上啟用 [開發人員模式](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 。</span><span class="sxs-lookup"><span data-stu-id="b6f87-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="b6f87-117">安裝 Oculus ADB 驅動程式是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="b6f87-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="b6f87-118">設定 XR SDK 管線以進行 Oculus 的尋找</span><span class="sxs-lookup"><span data-stu-id="b6f87-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="b6f87-119">確定 **Oculus XR 外掛程式** 已安裝在視窗下 **--> 封裝管理員**</span><span class="sxs-lookup"><span data-stu-id="b6f87-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Oculus XR 外掛程式套件](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="b6f87-121">前往 [**編輯--> Project 設定--> XR 外掛程式管理--> 外掛程式提供** 者]，以確定 Oculus 外掛程式提供者是否包含在專案中</span><span class="sxs-lookup"><span data-stu-id="b6f87-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Oculus 外掛程式提供者](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="b6f87-123">設定 Oculus Integration Unity 套件以啟用 handtracking</span><span class="sxs-lookup"><span data-stu-id="b6f87-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="b6f87-124">從 Unity 資產存放區下載並匯入 [Oculus 整合](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 。</span><span class="sxs-lookup"><span data-stu-id="b6f87-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="b6f87-125">測試的最新版本是20.0.0。</span><span class="sxs-lookup"><span data-stu-id="b6f87-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="b6f87-126">您 [可以從此封存](https://developer.oculus.com/downloads/package/unity-integration-archive/)中找到較舊的版本。</span><span class="sxs-lookup"><span data-stu-id="b6f87-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="b6f87-127">流覽至混合現實工具組 > 公用程式 > Oculus > 整合 Oculus Integration Unity 模組。</span><span class="sxs-lookup"><span data-stu-id="b6f87-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="b6f87-128">這麼做會使用相關 Oculus 執行程式碼運作所需的定義和參考，來更新 asmdefs。</span><span class="sxs-lookup"><span data-stu-id="b6f87-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="b6f87-129">它也會更新 csc 檔案，以篩選出 Oculus 整合資產所產生的過時警告。</span><span class="sxs-lookup"><span data-stu-id="b6f87-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="b6f87-130">MRTK 存放庫包含將警告轉換成錯誤的 csc 檔案，這種轉換會中止 MRTK-Quest 設定程式。</span><span class="sxs-lookup"><span data-stu-id="b6f87-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Oculus 整合 Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="b6f87-132">在匯入的 Oculus 資料夾中 (應該在資產/Oculus) 找到，其中有一個可編寫腳本的物件，稱為 OculusProjectConfig。</span><span class="sxs-lookup"><span data-stu-id="b6f87-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="b6f87-133">在該設定檔中，您必須將 HandTrackingSupport 設定為「控制器和手」。</span><span class="sxs-lookup"><span data-stu-id="b6f87-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Oculus 整合控制器與手](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="b6f87-135">設定場景</span><span class="sxs-lookup"><span data-stu-id="b6f87-135">Setting up the scene</span></span>

1. <span data-ttu-id="b6f87-136">建立新的 Unity 場景，或開啟預先存在的場景（例如 HandInteractionExamples）。</span><span class="sxs-lookup"><span data-stu-id="b6f87-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="b6f87-137">藉由流覽至 **混合現實工具** 組  >  **加入場景並設定**，將 MRTK 新增至場景。</span><span class="sxs-lookup"><span data-stu-id="b6f87-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="b6f87-138">使用 Oculus XR SDK Data Provider</span><span class="sxs-lookup"><span data-stu-id="b6f87-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="b6f87-139">將您的設定檔設定為使用 **OCULUS XR SDK Data Provider**</span><span class="sxs-lookup"><span data-stu-id="b6f87-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="b6f87-140">如果不打算修改設定設定檔</span><span class="sxs-lookup"><span data-stu-id="b6f87-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="b6f87-141">使用任何預設的 MRTK 設定檔，這些設定檔全都在 Unity 的 XR 管線中設定。</span><span class="sxs-lookup"><span data-stu-id="b6f87-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="b6f87-142">先前的 DefaultXRSDKConfigurationProfile 現在標示為過時。</span><span class="sxs-lookup"><span data-stu-id="b6f87-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="b6f87-143">移至 [ [組建]，並將專案部署至 Oculus 的尋找](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)。</span><span class="sxs-lookup"><span data-stu-id="b6f87-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="b6f87-144">否則，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b6f87-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="b6f87-145">選取階層中的 MixedRealityToolkit 遊戲物件，然後選取 [ **複製和自訂** ] 以複製預設的混合現實設定檔。</span><span class="sxs-lookup"><span data-stu-id="b6f87-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![複製設定檔](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="b6f87-147">選取 **輸入** 設定設定檔。</span><span class="sxs-lookup"><span data-stu-id="b6f87-147">Select the **Input** Configuration Profile.</span></span>

        ![輸入設定設定檔](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="b6f87-149">在輸入系統設定檔中選取 [ **複製** ]，以啟用修改。</span><span class="sxs-lookup"><span data-stu-id="b6f87-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![複製輸入系統設定檔](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="b6f87-151">開啟 [**輸入資料提供者**] 區段，選取頂端的 [**新增 Data Provider** ，然後在清單結尾加入新的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="b6f87-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="b6f87-152">開啟新的資料提供者，並將類型設定為 MixedReality，然後將 **類型** 設定為 **XRSDK. Oculus > OculusXRSDKDeviceManager**。</span><span class="sxs-lookup"><span data-stu-id="b6f87-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus 新增 XRSDK Data Provider](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="b6f87-154">將您的設定檔設定為使用 **OCULUS XR SDK Data Provider**</span><span class="sxs-lookup"><span data-stu-id="b6f87-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="b6f87-155">如果不打算修改設定設定檔</span><span class="sxs-lookup"><span data-stu-id="b6f87-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="b6f87-156">將設定檔變更為 DefaultXRSDKConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="b6f87-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="b6f87-157">移至 [ [組建]，並將專案部署至 Oculus 的尋找](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)。</span><span class="sxs-lookup"><span data-stu-id="b6f87-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="b6f87-158">否則，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b6f87-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="b6f87-159">選取階層中的 MixedRealityToolkit 遊戲物件，然後選取 [ **複製和自訂** ] 以複製預設的混合現實設定檔。</span><span class="sxs-lookup"><span data-stu-id="b6f87-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![複製設定檔](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="b6f87-161">選取 **輸入** 設定設定檔。</span><span class="sxs-lookup"><span data-stu-id="b6f87-161">Select the **Input** Configuration Profile.</span></span>

        ![輸入設定設定檔](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="b6f87-163">在輸入系統設定檔中選取 [ **複製** ]，以啟用修改。</span><span class="sxs-lookup"><span data-stu-id="b6f87-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![複製輸入系統設定檔](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="b6f87-165">開啟 [**輸入資料提供者**] 區段，選取頂端的 [**新增 Data Provider** ，然後在清單結尾加入新的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="b6f87-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="b6f87-166">開啟新的資料提供者，並將類型設定為 MixedReality，然後將 **類型** 設定為 **XRSDK. Oculus > OculusXRSDKDeviceManager**。</span><span class="sxs-lookup"><span data-stu-id="b6f87-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Oculus 新增 XRSDK Data Provider](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="b6f87-168">Oculus XR SDK Data Provider 包含 OVR 相機 rig 預製專案，此會使用 OVR 攝影機 rig 自動設定專案，並 OVR 手以正確地路由輸入。</span><span class="sxs-lookup"><span data-stu-id="b6f87-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="b6f87-169">手動將 OVR 攝影機裝備新增至場景需要手動設定設定和輸入。</span><span class="sxs-lookup"><span data-stu-id="b6f87-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="b6f87-170">建立您的專案，並將其部署至 Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="b6f87-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="b6f87-171">透過 USB 3.0-> USB C 纜線插入 Oculus 的尋找</span><span class="sxs-lookup"><span data-stu-id="b6f87-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="b6f87-172">流覽至 **File > Build 設定**</span><span class="sxs-lookup"><span data-stu-id="b6f87-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="b6f87-173">將部署變更為 **Android**</span><span class="sxs-lookup"><span data-stu-id="b6f87-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="b6f87-174">確定已選取 [Oculus]，作為適用的執行裝置</span><span class="sxs-lookup"><span data-stu-id="b6f87-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus 執行裝置](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="b6f87-176">選取組建並執行</span><span class="sxs-lookup"><span data-stu-id="b6f87-176">Select Build and Run</span></span>
    - <span data-ttu-id="b6f87-177">當您第一次選取 *組建並執行* 時，可能會遇到下列一組組建錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6f87-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="b6f87-178">當您選取 [ *組建] 並重新執行* 時，應該可以成功部署。</span><span class="sxs-lookup"><span data-stu-id="b6f87-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Oculus 預期的組建錯誤](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="b6f87-180">接受來自要求內的 _允許 USB 調試_</span><span class="sxs-lookup"><span data-stu-id="b6f87-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="b6f87-181">查看 Oculus 中的場景</span><span class="sxs-lookup"><span data-stu-id="b6f87-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="b6f87-182">從 Project 移除 Oculus 整合</span><span class="sxs-lookup"><span data-stu-id="b6f87-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="b6f87-183">流覽至混合現實工具組 > Oculus > 個別的 Oculus Integration Unity 模組  ![ Oculus 分隔 Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="b6f87-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="b6f87-184">讓 Unity 重新整理為 MixedReality 中的參考，在此步驟中會修改 Oculus asmdef 和其他檔案</span><span class="sxs-lookup"><span data-stu-id="b6f87-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="b6f87-185">關閉 Unity</span><span class="sxs-lookup"><span data-stu-id="b6f87-185">Close Unity</span></span>
1. <span data-ttu-id="b6f87-186">關閉 Visual Studio （如果已開啟）</span><span class="sxs-lookup"><span data-stu-id="b6f87-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="b6f87-187">開啟檔案總管並流覽至 MRTK Unity 專案的根目錄</span><span class="sxs-lookup"><span data-stu-id="b6f87-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="b6f87-188">刪除 UnityProjectName/Library 目錄</span><span class="sxs-lookup"><span data-stu-id="b6f87-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="b6f87-189">刪除 UnityProjectName/資產/Oculus 目錄</span><span class="sxs-lookup"><span data-stu-id="b6f87-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="b6f87-190">刪除 UnityProjectName/資產/Oculus 中繼檔案</span><span class="sxs-lookup"><span data-stu-id="b6f87-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="b6f87-191">重新開啟 Unity</span><span class="sxs-lookup"><span data-stu-id="b6f87-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="b6f87-192">常見錯誤</span><span class="sxs-lookup"><span data-stu-id="b6f87-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="b6f87-193">Unity 無法辨識的找出</span><span class="sxs-lookup"><span data-stu-id="b6f87-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="b6f87-194">請確定您的 Android 路徑已正確設定。</span><span class="sxs-lookup"><span data-stu-id="b6f87-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="b6f87-195">如果您持續遇到問題，請遵循本 [指南](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="b6f87-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="b6f87-196">**編輯 > 喜好設定 > 外部工具 > Android**</span><span class="sxs-lookup"><span data-stu-id="b6f87-196">**Edit > Preferences > External Tools > Android**</span></span>

![Android 工具設定](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
