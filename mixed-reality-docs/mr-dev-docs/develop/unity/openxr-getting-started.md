---
title: 使用 Unity 的 Mixed Reality OpenXR 外掛程式
description: 瞭解如何啟用 Unity 專案的 Mixed Reality OpenXR 外掛程式。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: cae588acbcddeefae45a555f335f1c74389f1824
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496166"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="541be-104">使用 Unity 的 Mixed Reality OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="541be-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="541be-105">從 Unity 2020.2 版開始，可以使用 Unity 封裝管理員 (UPM) 提供 Microsoft 的 Mixed Reality OpenXR 外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="541be-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="541be-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="541be-106">Prerequisites</span></span>

* <span data-ttu-id="541be-107">Unity 2020.2 或更新版本</span><span class="sxs-lookup"><span data-stu-id="541be-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="541be-108">Unity OpenXR 外掛程式0.1.3 或更新版本</span><span class="sxs-lookup"><span data-stu-id="541be-108">Unity OpenXR plugin 0.1.3 or later</span></span>
* <span data-ttu-id="541be-109">Visual Studio 2019 或更新版本</span><span class="sxs-lookup"><span data-stu-id="541be-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="541be-110">在 Unity 中為 HoloLens 2 應用程式安裝 **UWP** 平臺支援</span><span class="sxs-lookup"><span data-stu-id="541be-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="541be-111">如果您是在 Windows 電腦上建立 VR 應用程式，則不一定需要混合現實 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="541be-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="541be-112">但是，如果您要自訂適用于 HP 重設系的控制器對應，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。</span><span class="sxs-lookup"><span data-stu-id="541be-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="541be-113">使用混合現實功能工具安裝 OpenXR</span><span class="sxs-lookup"><span data-stu-id="541be-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="541be-114">使用新的混合現實功能工具應用程式來安裝 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="541be-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="541be-115">遵循 [安裝和使用](welcome-to-mr-feature-tool.md) 方式的指示，然後在混合現實工具組類別中選取 **Mixed reality OpenXR 外掛程式** 套件：</span><span class="sxs-lookup"><span data-stu-id="541be-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![醒目提示 open xr 外掛程式的混合現實功能工具套件視窗](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="541be-117">設定 OpenXR 的 XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="541be-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="541be-118">若要將 OpenXR 設定為 Unity 中的執行時間：</span><span class="sxs-lookup"><span data-stu-id="541be-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="541be-119">在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]</span><span class="sxs-lookup"><span data-stu-id="541be-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="541be-120">在設定清單中，選取 [ **XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="541be-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="541be-121">檢查 **啟動時初始化 XR** 和 **OpenXR (預覽)** 方塊</span><span class="sxs-lookup"><span data-stu-id="541be-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="541be-122">如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [ **Microsoft HoloLens 功能集**]</span><span class="sxs-lookup"><span data-stu-id="541be-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="541be-124">如果您在 OpenXR 外掛程式旁邊看到紅色警告圖示 **(Preview)**，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="541be-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="541be-125">Unity 編輯器可能需要自行重新開機，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="541be-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 專案驗證視窗的螢幕擷取畫面](images/openxr-img-06.png)

<span data-ttu-id="541be-127">您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！</span><span class="sxs-lookup"><span data-stu-id="541be-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="541be-128">繼續進行下一節，以瞭解如何使用 OpenXR 範例。</span><span class="sxs-lookup"><span data-stu-id="541be-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="541be-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="541be-129">Optimization</span></span>

<span data-ttu-id="541be-130">如果您是針對 HoloLens 2 進行開發，請流覽至 **Mixed Reality> OpenXR > 套用建議的 HoloLens 2 專案設定** ，以取得更佳的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="541be-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="541be-132">試用 Unity 範例場景</span><span class="sxs-lookup"><span data-stu-id="541be-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="541be-133">若要利用一或多個範例，請從 **封裝管理員** 安裝 [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) ：</span><span class="sxs-lookup"><span data-stu-id="541be-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Unity 封裝管理員在 Unity 編輯器中開啟，並醒目提示 AR Foundation 的螢幕擷取畫面](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="541be-135">HoloLens 2 範例</span><span class="sxs-lookup"><span data-stu-id="541be-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="541be-136">在 Unity 編輯器中，流覽至 [ **Window >] 封裝管理員**</span><span class="sxs-lookup"><span data-stu-id="541be-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="541be-137">在套件清單中，選取 **Mixed Reality OpenXR 外掛程式**</span><span class="sxs-lookup"><span data-stu-id="541be-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="541be-138">在 **範例** 清單中找出範例，然後選取 [匯 **入**]</span><span class="sxs-lookup"><span data-stu-id="541be-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![Unity 封裝管理員在 Unity 編輯器中開啟的螢幕擷取畫面，其中已選取混合的現實 OpenXR 外掛程式，並醒目提示範例匯入按鈕](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="541be-140">更新套件時，Unity 會提供選項來更新匯入的範例。</span><span class="sxs-lookup"><span data-stu-id="541be-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="541be-141">更新匯入的範例將會覆寫對範例和相關資產所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="541be-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="541be-142">搭配使用 MRTK 與 OpenXR 支援</span><span class="sxs-lookup"><span data-stu-id="541be-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="541be-143">MRTK Unity 支援從2.5.3 版本開始的 Mixed Reality OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="541be-143">MRTK Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>  

1. <span data-ttu-id="541be-144">再次開啟 [Mixed Reality 功能工具](welcome-to-mr-feature-tool.md) ，並在平臺支援類別中選取 **Mixed reality OpenXR 外掛程式** 套件</span><span class="sxs-lookup"><span data-stu-id="541be-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again and select the **Mixed Reality OpenXR Plugin** package in the Platform Support category</span></span>
2. <span data-ttu-id="541be-145">移至偵測器中的 MixedReality 工具組元件腳本，並切換至 **DefaultOpenXRConfigurationProfile** 設定檔：</span><span class="sxs-lookup"><span data-stu-id="541be-145">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

![在偵測器的混合現實工具組元件中切換 MRTK 設定的螢幕擷取畫面](images/openxr-img-11.png)

### <a name="known-issues"></a><span data-ttu-id="541be-147">已知問題</span><span class="sxs-lookup"><span data-stu-id="541be-147">Known issues</span></span> 

<span data-ttu-id="541be-148">使用「手動追蹤」功能時，請將下列這一行新增至 **資產/MixedRealityToolkit 產生/link.xml** 檔案：</span><span class="sxs-lookup"><span data-stu-id="541be-148">When using the Hand Tracking feature, add following line in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a><span data-ttu-id="541be-149">下一步</span><span class="sxs-lookup"><span data-stu-id="541be-149">Next steps</span></span>

<span data-ttu-id="541be-150">現在您已將專案設定為 OpenXR 並可存取範例，請查看我們的 OpenXR 外掛程式目前支援的 [功能](openxr-supported-features.md) 。</span><span class="sxs-lookup"><span data-stu-id="541be-150">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="541be-151">有任何意見反應嗎？</span><span class="sxs-lookup"><span data-stu-id="541be-151">Have Feedback?</span></span>

<span data-ttu-id="541be-152">OpenXR 仍是實驗性的，因此我們會感謝您提供給我們的意見反應，以協助您更妥善地進行。</span><span class="sxs-lookup"><span data-stu-id="541be-152">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="541be-153">您可以使用 **Microsoft** OpenXR 標記您的論壇文章，並 [](https://aka.ms/unityforums)  +   **HoloLens 2** 或 **Windows Mixed Reality**，在 Unity 論壇中找到我們。</span><span class="sxs-lookup"><span data-stu-id="541be-153">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="541be-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="541be-154">See also</span></span>

* [<span data-ttu-id="541be-155">在沒有 MRTK 的情況下設定專案</span><span class="sxs-lookup"><span data-stu-id="541be-155">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="541be-156">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="541be-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="541be-157">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="541be-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
