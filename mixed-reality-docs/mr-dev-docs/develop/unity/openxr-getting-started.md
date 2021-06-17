---
title: 使用 Mixed Reality OpenXR 外掛程式
description: 瞭解如何啟用 Unity 專案的 Mixed Reality OpenXR 外掛程式。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: ffec0cbe2ea9fd87cbb5f38010dad2d64e2e82ee
ms.sourcegitcommit: adbe3baa6b1c284ed1c4fd796d8b5612c3ca3f42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112270433"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="2e185-104">使用 Mixed Reality OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="2e185-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="2e185-105">針對以 Unity 2020 為目標的開發人員建立 HoloLens 2 或混合的現實應用程式，OpenXR 外掛程式可以用來取代 WindowsXR 外掛程式，以獲得更好的跨平臺相容性。</span><span class="sxs-lookup"><span data-stu-id="2e185-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="2e185-106">Mixed Reality OpenXR 外掛程式也適用于最新的 [混合現實功能工具](welcome-to-mr-feature-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="2e185-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2e185-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="2e185-107">Prerequisites</span></span>

* <span data-ttu-id="2e185-108">最新的 Unity 2020.3 LTS，建議 2020.3.6 f1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2e185-108">Latest Unity 2020.3 LTS, recommend 2020.3.6f1 or above.</span></span>
* <span data-ttu-id="2e185-109">最新的 Unity OpenXR 外掛程式，建議1.2 或更新版本</span><span class="sxs-lookup"><span data-stu-id="2e185-109">Latest Unity OpenXR plugin, recommend 1.2 or later</span></span>
* <span data-ttu-id="2e185-110">[適用于 HoloLens 2 開發的](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)最新工具</span><span class="sxs-lookup"><span data-stu-id="2e185-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="2e185-111">最新的 MRTK (選用) ，建議2.6 版或更新版本</span><span class="sxs-lookup"><span data-stu-id="2e185-111">Latest MRTK (optional), recommend version 2.6 or later</span></span>
* <span data-ttu-id="2e185-112">最新的混合現實 OpenXR 外掛程式，建議版本0.9.5 或更新版本</span><span class="sxs-lookup"><span data-stu-id="2e185-112">Latest Mixed Reality OpenXR Plugin, recommend version 0.9.5 or later</span></span>

> [!NOTE]
> <span data-ttu-id="2e185-113">如果您是在 Windows 電腦上建立 VR 應用程式，則不一定需要混合現實 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="2e185-113">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="2e185-114">但是，如果您要自訂適用于 HP 重設系的控制器對應，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。</span><span class="sxs-lookup"><span data-stu-id="2e185-114">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="2e185-115">使用 MRTK 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="2e185-115">Setting up your project with MRTK</span></span>

<span data-ttu-id="2e185-116">適用于 Unity 的 MRTK 會提供跨平臺輸入系統、基礎元件，以及空間互動的常見組建區塊。</span><span class="sxs-lookup"><span data-stu-id="2e185-116">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="2e185-117">MRTK 第 2 版主要用於加速開發適用於 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2e185-117">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="2e185-118">此專案的目標是減少進入障礙、建立混合實境應用程式，以及回饋伴著我們成長的社群。</span><span class="sxs-lookup"><span data-stu-id="2e185-118">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e185-119">使用 MRTK 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="2e185-119">Set up your project using MRTK</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="2e185-120">如需詳細的功能詳細資料，請參閱 [MRTK 的檔](/windows/mixed-reality/mrtk-unity) 。</span><span class="sxs-lookup"><span data-stu-id="2e185-120">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="2e185-121">手動設定而不 MRTK</span><span class="sxs-lookup"><span data-stu-id="2e185-121">Manual setup without MRTK</span></span>

<span data-ttu-id="2e185-122">使用新的混合現實功能工具應用程式來安裝 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="2e185-122">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="2e185-123">遵循 [安裝和使用](welcome-to-mr-feature-tool.md) 方式的指示，然後在混合現實工具組類別中選取 **Mixed reality OpenXR 外掛程式** 套件：</span><span class="sxs-lookup"><span data-stu-id="2e185-123">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![醒目提示 open xr 外掛程式的混合現實功能工具套件視窗](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="2e185-125">設定您的組建目標</span><span class="sxs-lookup"><span data-stu-id="2e185-125">Setting your build target</span></span>

<span data-ttu-id="2e185-126">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="2e185-126">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](images/wmr-config-img-3.png)

<span data-ttu-id="2e185-128">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="2e185-128">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="2e185-129">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="2e185-129">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="2e185-130">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="2e185-130">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="2e185-131">將 **架構** 設定為 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="2e185-131">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="2e185-132">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="2e185-132">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="2e185-133">將 **組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="2e185-133">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="2e185-134">將 **UWP SDK** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="2e185-134">Set **UWP SDK** to **Latest installed**</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="2e185-136">設定 OpenXR 的 XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="2e185-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="2e185-137">若要將 OpenXR 設定為 Unity 中的執行時間：</span><span class="sxs-lookup"><span data-stu-id="2e185-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="2e185-138">在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]</span><span class="sxs-lookup"><span data-stu-id="2e185-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="2e185-139">在設定清單中，選取 [ **XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="2e185-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="2e185-140">檢查 Startup 和 **OpenXR** 方塊的 **Initialize XR**</span><span class="sxs-lookup"><span data-stu-id="2e185-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="2e185-141">如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [ **Microsoft HoloLens 功能集**]</span><span class="sxs-lookup"><span data-stu-id="2e185-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="2e185-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="2e185-143">Optimization</span></span>

<span data-ttu-id="2e185-144">如果您是針對 HoloLens 2 進行開發，請流覽至 **Mixed Reality> OpenXR > 套用建議的 HoloLens 2 專案設定** ，以取得更佳的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="2e185-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="2e185-146">如果您在 **OpenXR 外掛程式** 旁邊看到紅色警告圖示，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="2e185-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="2e185-147">Unity 編輯器可能需要自行重新開機，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="2e185-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 專案驗證視窗的螢幕擷取畫面](images/openxr-img-06.png)

<span data-ttu-id="2e185-149">您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！</span><span class="sxs-lookup"><span data-stu-id="2e185-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="2e185-150">繼續進行下一節，以瞭解如何使用 OpenXR 範例。</span><span class="sxs-lookup"><span data-stu-id="2e185-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="2e185-151">適用于 OpenXR 和 HoloLens 2 的 Unity 範例專案</span><span class="sxs-lookup"><span data-stu-id="2e185-151">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="2e185-152">查看範例 unity 專案的 [OpenXR Mixed Reality 範例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 存放庫展示如何使用 Mixed reality OpenXR 外掛程式建立 HoloLens 2 或混合現實耳機的 unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2e185-152">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="2e185-153">搭配使用 MRTK 與 OpenXR 支援</span><span class="sxs-lookup"><span data-stu-id="2e185-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="2e185-154">MRTK-Unity 支援從2.5.3 版本開始的 Mixed Reality OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="2e185-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="2e185-155">如果您還沒有這麼做，請再次開啟 [Mixed Reality 功能工具](welcome-to-mr-feature-tool.md) 以安裝混合現實工具組。</span><span class="sxs-lookup"><span data-stu-id="2e185-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="2e185-156">**基礎** 套件中的 OpenXR 支援。</span><span class="sxs-lookup"><span data-stu-id="2e185-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="2e185-157">移至偵測器中的 MixedReality 工具組元件腳本，並切換至 **DefaultOpenXRConfigurationProfile** 設定檔：</span><span class="sxs-lookup"><span data-stu-id="2e185-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![在偵測器的混合現實工具組元件中切換 MRTK 設定的螢幕擷取畫面](images/openxr-img-11.png)

    1. <span data-ttu-id="2e185-159">如需有關 [遷移至 OpenXR 的深入資訊](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，請參閱 MRTK 檔。</span><span class="sxs-lookup"><span data-stu-id="2e185-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="2e185-160">從舊版 MRTK 進行升級時，請確定 **資產/MixedRealityToolkit. 產生/link.xml** 檔案中有下列這一行：</span><span class="sxs-lookup"><span data-stu-id="2e185-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="2e185-161">如果您開始使用 MRTK 2.5.4 或更新版本，則預設會新增這一行。</span><span class="sxs-lookup"><span data-stu-id="2e185-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2e185-162">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2e185-162">Next steps</span></span>

<span data-ttu-id="2e185-163">現在您已將專案設定為 OpenXR 並可存取範例，請查看我們的 OpenXR 外掛程式目前支援的 [功能](openxr-supported-features.md) 。</span><span class="sxs-lookup"><span data-stu-id="2e185-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="2e185-164">有任何意見反應嗎？</span><span class="sxs-lookup"><span data-stu-id="2e185-164">Have Feedback?</span></span>

<span data-ttu-id="2e185-165">OpenXR 仍是實驗性的，因此我們會感謝您提供給我們的意見反應，以協助您更妥善地進行。</span><span class="sxs-lookup"><span data-stu-id="2e185-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="2e185-166">您可以使用 **Microsoft** OpenXR 標記您的論壇文章，並 [](https://aka.ms/unityforums)  +   **HoloLens 2** 或 **Windows Mixed Reality**，在 Unity 論壇中找到我們。</span><span class="sxs-lookup"><span data-stu-id="2e185-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e185-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e185-167">See also</span></span>

* [<span data-ttu-id="2e185-168">在沒有 MRTK 的情況下設定專案</span><span class="sxs-lookup"><span data-stu-id="2e185-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="2e185-169">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="2e185-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="2e185-170">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="2e185-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)