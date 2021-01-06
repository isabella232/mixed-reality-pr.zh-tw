---
title: 使用 Unity 的 Mixed Reality OpenXR 外掛程式
description: 瞭解如何啟用 Unity 專案的 Mixed Reality OpenXR 外掛程式。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: 7d28dd50e111da4b010bcae699b7451d967e8f35
ms.sourcegitcommit: 653ddcae6d7a1617c89da1153fa8e7b482ef6818
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97905290"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="adc07-104">使用 Unity 的 Mixed Reality OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="adc07-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="adc07-105">從 Unity 2020.2 版開始，可以使用 Unity 封裝管理員 (UPM) 提供 Microsoft 的 Mixed Reality OpenXR 外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="adc07-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="adc07-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="adc07-106">Prerequisites</span></span>

* <span data-ttu-id="adc07-107">Unity 2020.2 或更新版本</span><span class="sxs-lookup"><span data-stu-id="adc07-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="adc07-108">Unity OpenXR 外掛程式0.1.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="adc07-108">Unity OpenXR plugin 0.1.1 or later</span></span>
* <span data-ttu-id="adc07-109">Visual Studio 2019 或更新版本</span><span class="sxs-lookup"><span data-stu-id="adc07-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="adc07-110">在 Unity 中為 HoloLens 2 應用程式安裝 **UWP** 平臺支援</span><span class="sxs-lookup"><span data-stu-id="adc07-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="adc07-111">如果您是在 Windows 電腦上建立 VR 應用程式，則不一定需要混合現實 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="adc07-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="adc07-112">但是，如果您要自訂適用于 HP 重設系的控制器對應，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。</span><span class="sxs-lookup"><span data-stu-id="adc07-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="adc07-113">安裝 Mixed Reality OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="adc07-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="adc07-114">您的專案必須先安裝 **OpenXR 外掛程式** 和 **XR 外掛程式管理** 套件，才能使用 Mixed Reality OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="adc07-114">Your project needs to install the **OpenXR Plugin** and **XR Plugin Management** packages before using the Mixed Reality OpenXR Plugin.</span></span> <span data-ttu-id="adc07-115">如果您已經安裝這些專案，很棒！</span><span class="sxs-lookup"><span data-stu-id="adc07-115">If you've already installed them, great!</span></span> <span data-ttu-id="adc07-116">如果不是，安裝 Mixed Reality OpenXR 外掛程式會自動將它們安裝為相依性：</span><span class="sxs-lookup"><span data-stu-id="adc07-116">If not, installing the Mixed Reality OpenXR plugin will automatically install them as dependencies:</span></span>

1. <span data-ttu-id="adc07-117">在 Unity 編輯器中，流覽至 [ **編輯 > 專案設定] > 封裝管理員**</span><span class="sxs-lookup"><span data-stu-id="adc07-117">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="adc07-118">展開 [限 **域** 登錄] 區段，輸入下列資訊，然後選取 [ **儲存**]：</span><span class="sxs-lookup"><span data-stu-id="adc07-118">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>
    * <span data-ttu-id="adc07-119">將 **名稱** 設定為 **Microsoft Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="adc07-119">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="adc07-120">將 **URL** 設定為 **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="adc07-120">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="adc07-121">將 **範圍 (s)** 設定為 **mixedreality**</span><span class="sxs-lookup"><span data-stu-id="adc07-121">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="adc07-122">在 [ **Advanced Settings**] 底下，選取 [**啟用預覽套件**]</span><span class="sxs-lookup"><span data-stu-id="adc07-122">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![在專案設定中開啟 Unity 封裝管理員視窗的螢幕擷取畫面](images/openxr-img-01.png)

<span data-ttu-id="adc07-124">Unity 封裝管理員使用名為 *manifest.js* 的資訊清單檔來決定要安裝的套件，以及可從中安裝的登錄。</span><span class="sxs-lookup"><span data-stu-id="adc07-124">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="adc07-125">OpenXR 仍是 Unity 中的實驗性，而此程式可能會隨著時間而改變，因為我們會將開發人員體驗優化。</span><span class="sxs-lookup"><span data-stu-id="adc07-125">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="adc07-126">註冊混合現實相依性</span><span class="sxs-lookup"><span data-stu-id="adc07-126">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="adc07-127">一旦將 Microsoft Mixed Reality 範圍登錄新增至資訊清單之後，就可以指定 OpenXR 封裝。</span><span class="sxs-lookup"><span data-stu-id="adc07-127">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="adc07-128">若要新增 OpenXR 套件：</span><span class="sxs-lookup"><span data-stu-id="adc07-128">To add the OpenXR package:</span></span>

1. <span data-ttu-id="adc07-129">在文字編輯器中開啟 **[projectRoot]/Packages/manifest.js** ，例如 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="adc07-129">Open **[projectRoot]/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
    1. <span data-ttu-id="adc07-130">若要取得這裡，請在 [專案] 視窗的左面板中，以滑鼠右鍵按一下 **套件** 。</span><span class="sxs-lookup"><span data-stu-id="adc07-130">To get here, right click on **Packages** in the left panel of the Project window.</span></span> <span data-ttu-id="adc07-131">然後，按一下 [ **在 Explorer 中顯示**]。</span><span class="sxs-lookup"><span data-stu-id="adc07-131">Then, click **Show in Explorer**.</span></span>
    <span data-ttu-id="adc07-132">![[專案] 視窗中的套件清單螢幕擷取畫面](images/packages.png)</span><span class="sxs-lookup"><span data-stu-id="adc07-132">![Screenshot of the packages listing in the Project window](images/packages.png)</span></span>
1. <span data-ttu-id="adc07-133">依照下列方式修改 *套件/manifest.js* 的 [相依性] 區段：</span><span class="sxs-lookup"><span data-stu-id="adc07-133">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="adc07-134">您的資訊清單檔中可能會有更多相依性，而不是此處所示。</span><span class="sxs-lookup"><span data-stu-id="adc07-134">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="adc07-135">請勿刪除其中任何一項，只要將 OpenXR 相依性新增至清單即可。</span><span class="sxs-lookup"><span data-stu-id="adc07-135">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.1",
      }
    ```

1. <span data-ttu-id="adc07-136">儲存檔案、切換回 Unity 編輯器，然後開啟 **封裝管理員** 來確認已安裝外掛程式：</span><span class="sxs-lookup"><span data-stu-id="adc07-136">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span>

    ![Unity 封裝管理員的螢幕擷取畫面，其中已反白顯示混合現實 OpenXR 外掛程式的 Unity 編輯器中開啟](images/openxr-img-03.png)

    > [!Note]
    > <span data-ttu-id="adc07-138">如果使用 Unity 封裝管理員移除 OpenXR 封裝，您必須使用先前所述的步驟重新新增它。</span><span class="sxs-lookup"><span data-stu-id="adc07-138">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="adc07-139">設定 OpenXR 的 XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="adc07-139">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="adc07-140">若要將 OpenXR 設定為 Unity 中的執行時間：</span><span class="sxs-lookup"><span data-stu-id="adc07-140">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="adc07-141">在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]</span><span class="sxs-lookup"><span data-stu-id="adc07-141">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="adc07-142">在設定清單中，選取 [ **XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="adc07-142">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="adc07-143">檢查 **啟動時初始化 XR** 和 **OpenXR (預覽)** 方塊</span><span class="sxs-lookup"><span data-stu-id="adc07-143">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="adc07-144">如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [ **Microsoft HoloLens 功能集**]</span><span class="sxs-lookup"><span data-stu-id="adc07-144">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="adc07-146">如果您在 OpenXR 外掛程式旁邊看到紅色警告圖示 **(Preview)**，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="adc07-146">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="adc07-147">Unity 編輯器可能需要自行重新開機，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="adc07-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 專案驗證視窗的螢幕擷取畫面](images/openxr-img-06.png)

<span data-ttu-id="adc07-149">您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！</span><span class="sxs-lookup"><span data-stu-id="adc07-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="adc07-150">繼續進行下一節，以瞭解如何使用 OpenXR 範例。</span><span class="sxs-lookup"><span data-stu-id="adc07-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="adc07-151">Optimization</span><span class="sxs-lookup"><span data-stu-id="adc07-151">Optimization</span></span>

<span data-ttu-id="adc07-152">如果您是針對 HoloLens 2 進行開發，請流覽至 **Mixed Reality> OpenXR > 套用建議的 HoloLens 2 專案設定** ，以取得更佳的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="adc07-152">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="adc07-154">試用 Unity 範例場景</span><span class="sxs-lookup"><span data-stu-id="adc07-154">Try out the Unity sample scenes</span></span>

<span data-ttu-id="adc07-155">若要利用一或多個範例，請從 **封裝管理員** 安裝 [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) ：</span><span class="sxs-lookup"><span data-stu-id="adc07-155">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Unity 封裝管理員在 Unity 編輯器中開啟，並醒目提示 AR Foundation 的螢幕擷取畫面](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="adc07-157">HoloLens 2 範例</span><span class="sxs-lookup"><span data-stu-id="adc07-157">HoloLens 2 samples</span></span>

1. <span data-ttu-id="adc07-158">在 Unity 編輯器中，流覽至 [ **Window >] 封裝管理員**</span><span class="sxs-lookup"><span data-stu-id="adc07-158">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="adc07-159">在套件清單中，選取 **Mixed Reality OpenXR 外掛程式**</span><span class="sxs-lookup"><span data-stu-id="adc07-159">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="adc07-160">在 **範例** 清單中找出範例，然後選取 [匯 **入**]</span><span class="sxs-lookup"><span data-stu-id="adc07-160">Locate the sample in the **Samples** list and select **Import**</span></span>

![Unity 封裝管理員在 Unity 編輯器中開啟的螢幕擷取畫面，其中已選取混合的現實 OpenXR 外掛程式，並醒目提示範例匯入按鈕](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="adc07-162">更新套件時，Unity 會提供選項來更新匯入的範例。</span><span class="sxs-lookup"><span data-stu-id="adc07-162">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="adc07-163">更新匯入的範例將會覆寫對範例和相關資產所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="adc07-163">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="adc07-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="adc07-164">Next steps</span></span>

<span data-ttu-id="adc07-165">現在您已將專案設定為 OpenXR 並可存取範例，請查看我們的 OpenXR 外掛程式目前支援的 [功能](openxr-supported-features.md) 。</span><span class="sxs-lookup"><span data-stu-id="adc07-165">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="adc07-166">有任何意見反應嗎？</span><span class="sxs-lookup"><span data-stu-id="adc07-166">Have Feedback?</span></span>

<span data-ttu-id="adc07-167">OpenXR 仍是實驗性的，因此我們會感謝您提供給我們的意見反應，以協助您更妥善地進行。</span><span class="sxs-lookup"><span data-stu-id="adc07-167">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="adc07-168">您可以使用 **Microsoft** OpenXR 標記您的論壇文章，並 [](https://aka.ms/unityforums)  +   **HoloLens 2** 或 **Windows Mixed Reality**，在 Unity 論壇中找到我們。</span><span class="sxs-lookup"><span data-stu-id="adc07-168">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="adc07-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adc07-169">See also</span></span>

* [<span data-ttu-id="adc07-170">在沒有 MRTK 的情況下設定專案</span><span class="sxs-lookup"><span data-stu-id="adc07-170">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="adc07-171">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="adc07-171">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="adc07-172">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="adc07-172">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
