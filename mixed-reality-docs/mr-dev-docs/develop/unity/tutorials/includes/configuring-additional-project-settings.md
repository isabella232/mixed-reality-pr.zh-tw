---
ms.openlocfilehash: 2b0dc328a1a47d9a0bd385cac6a88563dcc3938d
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107327518"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="573ba-101">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="573ba-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="573ba-102">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="573ba-102">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity [專案設定...] 功能表路徑](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="573ba-104">在 [專案設定] 視窗中，選取 [ **XR 外掛程式管理**  >  **安裝 XR 外掛程式管理**]，以安裝 XR 外掛程式管理：</span><span class="sxs-lookup"><span data-stu-id="573ba-104">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Unity XR 設定](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="573ba-106">Unity 完成安裝 XR 外掛程式管理之後。</span><span class="sxs-lookup"><span data-stu-id="573ba-106">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="573ba-107">確定您處於通用 Windows 平臺設定，並 **在啟動時檢查 INITIALIZE XR** 並 **Windows Mixed Reality** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="573ba-107">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup** and **Windows Mixed Reality** checkbox.</span></span>

![使用新增 Windows Mixed Reality SDK 的 Unity XR 設定](../images/mr-learning-base/base-02-section5-step2-2-1.png)

<span data-ttu-id="573ba-109">Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="573ba-109">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="573ba-110">如果沒有出現，請使用 Unity 功能表開啟。</span><span class="sxs-lookup"><span data-stu-id="573ba-110">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="573ba-111">在 [MRTK 專案設定] 視窗中，使用 **Audio 空間定位器** 下拉式清單選取 [MS HRTF 空間定位器]，然後按一下 [套用] 按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="573ba-111">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![已選取 Windows Mixed Reality SDK 的 Unity XR 設定](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="573ba-113">您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="573ba-113">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="573ba-114">如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="573ba-114">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="573ba-115">若要深入瞭解本主題，您可以參考  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。</span><span class="sxs-lookup"><span data-stu-id="573ba-115">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="573ba-116">在 [專案設定] 視窗中，選取 **[XR 外掛程式管理**  >  **Windows Mixed Reality**  >  **執行時間設定**]，然後使用 [**深度緩衝區格式**] 下拉式清單選取 **16 位深度：**</span><span class="sxs-lookup"><span data-stu-id="573ba-116">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth:**</span></span>

![已反白顯示套件名稱的 Unity 發行設定](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> <span data-ttu-id="573ba-118">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="573ba-118">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="573ba-119">若要深入瞭解本主題，您可以參考 MRTK 的<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">效能</a>檔中的<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">深度緩衝區共用 (HoloLens) </a>一節。</span><span class="sxs-lookup"><span data-stu-id="573ba-119">To learn more about this topic, you can refer to the   <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="573ba-120">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="573ba-120">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![使用套件名稱的 Unity 發行設定](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="573ba-122">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="573ba-122">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="573ba-123">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="573ba-123">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="573ba-124">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="573ba-124">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="573ba-125">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="573ba-125">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="573ba-126">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="573ba-126">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="573ba-127">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="573ba-127">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity [專案設定...] 功能表路徑](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="573ba-129">在 [專案設定] 視窗中，選取 [ **XR 外掛程式管理**  >  **安裝 XR 外掛程式管理**]，以安裝 XR 外掛程式管理：</span><span class="sxs-lookup"><span data-stu-id="573ba-129">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![已選取安裝 XR 外掛程式管理的 Unity XR 設定](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="573ba-131">Unity 完成安裝 XR 外掛程式管理之後。</span><span class="sxs-lookup"><span data-stu-id="573ba-131">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="573ba-132">確定您處於通用 Windows 平臺設定，並 **在啟動時檢查 INITIALIZE XR**、 **OpenXR** 和 **Microsoft HoloLens 功能集** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="573ba-132">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup**, **OpenXR** and **Microsoft HoloLens feature set** checkboxes.</span></span>

![使用新增 OpenXR 和 Microsoft HoloLens 功能的 Unity XR 設定 selectedd](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

<span data-ttu-id="573ba-134">在畫面頂端的功能表列中，流覽至 **Mixed Reality> OpenXR > 套用適用于 HoloLens 2 的建議專案設定** ，以取得更佳的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="573ba-134">In the menu bar at the top of the screen, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![混合的現實功能表與 OpenXR，並針對選取的 HoloLens 2 套用建議的專案設定](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

>[!Important]
><span data-ttu-id="573ba-136">如果您在 OpenXR 外掛程式旁邊看到紅色警告圖示 (Preview) ，請按一下圖示並選取 [全部修正]，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="573ba-136">If you see a red warning icon next to OpenXR Plugin (Preview), click the icon and select Fix all before continuing.</span></span> <span data-ttu-id="573ba-137">Unity 編輯器可能需要自行重新開機，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="573ba-137">The Unity Editor may need to restart itself for the changes to take effect.</span></span>
><span data-ttu-id="573ba-138">![OpenXR 專案驗證功能表，其中已選取要修正的所有問題。](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span><span class="sxs-lookup"><span data-stu-id="573ba-138">![OpenXR project validation menu with all issues selected to be fixed.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span></span>

<span data-ttu-id="573ba-139">Unity 完成匯入必要的檔案之後，[MRTK 專案配置器] 視窗應該會再次出現。</span><span class="sxs-lookup"><span data-stu-id="573ba-139">After Unity has finished importing necessary files, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="573ba-140">如果沒有出現，請使用 Unity 功能表開啟。</span><span class="sxs-lookup"><span data-stu-id="573ba-140">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="573ba-141">在 [MRTK 專案設定] 視窗中，使用 **Audio 空間定位器** 下拉式清單選取 [MS HRTF 空間定位器]，然後按一下 [套用] 按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="573ba-141">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![已選取預設選項的 [MRTK 設定] 視窗](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="573ba-143">您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="573ba-143">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="573ba-144">如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="573ba-144">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="573ba-145">若要深入瞭解本主題，您可以參考  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。</span><span class="sxs-lookup"><span data-stu-id="573ba-145">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>


<span data-ttu-id="573ba-146">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="573ba-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 發行設定](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="573ba-148">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="573ba-148">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="573ba-149">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="573ba-149">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="573ba-150">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="573ba-150">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="573ba-151">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="573ba-151">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="573ba-152">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="573ba-152">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="573ba-153">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="573ba-153">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="573ba-154">在 [專案設定] 視窗中，選取 [ **Player**  >  **XR 設定**] 並選取 [**支援虛擬**] 核取方塊，然後按一下 **+** 圖示，然後選取 [Windows Mixed Reality] 以新增 Windows Mixed Reality SDK：</span><span class="sxs-lookup"><span data-stu-id="573ba-154">In the Project Settings window, select **Player** > **XR Settings** and check the **Virual Reality Supported** checkbox then click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Unity XR 設定，已選取 [新增 Windows Mixed Reality SDK](../images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="573ba-156">Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="573ba-156">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="573ba-157">如果沒有，您可以從 Unity 功能表手動開啟它，方法是前往 **混合現實工具** 組  >  **公用程式**  >  **設定 Unity 專案**</span><span class="sxs-lookup"><span data-stu-id="573ba-157">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="573ba-158">在 [MRTK 專案設定] 視窗中，使用 **Audio 空間定位器** 下拉式清單選取 [MS HRTF 空間定位器]，然後按一下 [套用] 按鈕來套用設定：</span><span class="sxs-lookup"><span data-stu-id="573ba-158">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 設定視窗](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="573ba-160">您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="573ba-160">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="573ba-161">如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="573ba-161">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="573ba-162">若要深入瞭解本主題，您可以參考  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。</span><span class="sxs-lookup"><span data-stu-id="573ba-162">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="573ba-163">在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，然後使用 **深度格式** 下拉式清單選取 **16 位元深度**：</span><span class="sxs-lookup"><span data-stu-id="573ba-163">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 啟用16深度](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="573ba-165">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="573ba-165">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="573ba-166">若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。</span><span class="sxs-lookup"><span data-stu-id="573ba-166">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="573ba-167">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="573ba-167">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 發行設定。](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="573ba-170">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="573ba-170">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="573ba-171">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="573ba-171">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="573ba-172">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="573ba-172">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="573ba-173">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="573ba-173">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
