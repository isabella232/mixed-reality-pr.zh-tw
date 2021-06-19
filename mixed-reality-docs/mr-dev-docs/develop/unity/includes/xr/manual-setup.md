---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394582"
---
# <a name="openxr"></a>[<span data-ttu-id="e9d16-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="e9d16-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="e9d16-102">使用新的混合現實功能工具應用程式來安裝 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="e9d16-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="e9d16-103">遵循 [安裝和使用](../../welcome-to-mr-feature-tool.md) 方式的指示，然後在混合現實工具組類別中選取 **Mixed reality OpenXR 外掛程式** 套件：</span><span class="sxs-lookup"><span data-stu-id="e9d16-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![醒目提示 open xr 外掛程式的混合現實功能工具套件視窗](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="e9d16-105">設定您的組建目標</span><span class="sxs-lookup"><span data-stu-id="e9d16-105">Setting your build target</span></span>

<span data-ttu-id="e9d16-106">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="e9d16-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

<span data-ttu-id="e9d16-108">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="e9d16-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="e9d16-109">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="e9d16-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="e9d16-110">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="e9d16-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="e9d16-111">將 **架構** 設定為 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="e9d16-111">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="e9d16-112">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e9d16-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="e9d16-113">將 **組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="e9d16-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="e9d16-114">將 **UWP SDK** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="e9d16-114">Set **UWP SDK** to **Latest installed**</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="e9d16-116">設定 OpenXR 的 XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="e9d16-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="e9d16-117">若要將 OpenXR 設定為 Unity 中的執行時間：</span><span class="sxs-lookup"><span data-stu-id="e9d16-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="e9d16-118">在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]</span><span class="sxs-lookup"><span data-stu-id="e9d16-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="e9d16-119">在設定清單中，選取 [ **XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="e9d16-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="e9d16-120">檢查 Startup 和 **OpenXR** 方塊的 **Initialize XR**</span><span class="sxs-lookup"><span data-stu-id="e9d16-120">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="e9d16-121">如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [ **Microsoft HoloLens 功能集**]</span><span class="sxs-lookup"><span data-stu-id="e9d16-121">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](../../images/openxr-img-05.png)

### <a name="optimization"></a><span data-ttu-id="e9d16-123">Optimization</span><span class="sxs-lookup"><span data-stu-id="e9d16-123">Optimization</span></span>

<span data-ttu-id="e9d16-124">如果您是針對 HoloLens 2 進行開發，請流覽至 **Mixed Reality> OpenXR > 套用建議的 HoloLens 2 專案設定** ，以取得更佳的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="e9d16-124">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](../../images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="e9d16-126">如果您在 **OpenXR 外掛程式** 旁邊看到黃色警告圖示，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e9d16-126">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="e9d16-127">Unity 編輯器可能需要自行重新開機，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="e9d16-127">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 專案驗證視窗的螢幕擷取畫面](../../images/openxr-img-06.png)

<span data-ttu-id="e9d16-129">您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！</span><span class="sxs-lookup"><span data-stu-id="e9d16-129">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="e9d16-130">繼續進行下一節，以瞭解如何使用 OpenXR 範例。</span><span class="sxs-lookup"><span data-stu-id="e9d16-130">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="e9d16-131">適用于 OpenXR 和 HoloLens 2 的 Unity 範例專案</span><span class="sxs-lookup"><span data-stu-id="e9d16-131">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="e9d16-132">查看範例 unity 專案的 [OpenXR Mixed Reality 範例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 存放庫展示如何使用 Mixed reality OpenXR 外掛程式建立 HoloLens 2 或混合現實耳機的 unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9d16-132">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="e9d16-133">Windows XR</span><span class="sxs-lookup"><span data-stu-id="e9d16-133">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="e9d16-134">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="e9d16-134">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

<span data-ttu-id="e9d16-136">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="e9d16-136">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="e9d16-137">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="e9d16-137">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="e9d16-138">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="e9d16-138">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="e9d16-139">將 **架構** 設定為 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="e9d16-139">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="e9d16-140">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e9d16-140">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="e9d16-141">將 **組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="e9d16-141">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="e9d16-142">將 **UWP SDK** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="e9d16-142">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="e9d16-143">將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題</span><span class="sxs-lookup"><span data-stu-id="e9d16-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

<span data-ttu-id="e9d16-145">設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../../../design/app-views.md) ，而不是2d 視圖：</span><span class="sxs-lookup"><span data-stu-id="e9d16-145">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="e9d16-146">在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]，然後選取 [ **XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="e9d16-146">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="e9d16-147">選取 [**安裝 XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="e9d16-147">Select **Install XR Plugin Management**</span></span>

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="e9d16-149">選取 [ **啟動時初始化 XR** ] 和 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="e9d16-149">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="e9d16-151">展開 [ **XR 外掛程式管理** ] 區段，然後選取 [ **通用 Windows 平臺設定** ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="e9d16-151">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="e9d16-152">如果您使用 Unity 2020 或更新版本，您會看到檢查 **OpenXR** 或 **Windows Mixed Reality** 的選項。</span><span class="sxs-lookup"><span data-stu-id="e9d16-152">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="e9d16-153">您可以選擇任一執行時間。</span><span class="sxs-lookup"><span data-stu-id="e9d16-153">You can choose either runtime.</span></span>  <span data-ttu-id="e9d16-154">如果您要特別針對 HoloLens 2 或 HP 回條 G2 進行開發，並決定嘗試 **OpenXR**，請選取 [OpenXR] 方塊，並查看我們的指南，以 [使用 Unity 的 Mixed Reality OpenXR 外掛程式](../../openxr-getting-started.md) ，以在返回本教學課程之前，為這些裝置正確設定</span><span class="sxs-lookup"><span data-stu-id="e9d16-154">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](../../openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="e9d16-155">從 Unity 2020 LTS 開始，Microsoft 正採用 OpenXR 進行開發。</span><span class="sxs-lookup"><span data-stu-id="e9d16-155">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="e9d16-156">當我們遷移至此路徑時，在 Unity 2021.1 中，Windows XR 外掛程式將會被取代，並在2021.2 中移除，讓 OpenXR 唯一支援的路徑。</span><span class="sxs-lookup"><span data-stu-id="e9d16-156">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="e9d16-157">您可以在中找到更多有關 [使用 Mixed Reality OpenXR 外掛程式](../../openxr-getting-started.md)的資訊。</span><span class="sxs-lookup"><span data-stu-id="e9d16-157">You can find more information in [Using the Mixed Reality OpenXR plugin](../../openxr-getting-started.md).</span></span>

6. <span data-ttu-id="e9d16-158">如果您決定選擇 **Windows Mixed Reality** 外掛程式，請檢查所有方塊，並將 **深度提交模式** 設定為 **深度16位**</span><span class="sxs-lookup"><span data-stu-id="e9d16-158">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![在 unity 編輯器中開啟的 [專案設定] 視窗的螢幕擷取畫面，其中已醒目提示 Windows Mixed Reality 區段](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="e9d16-160">傳統 XR</span><span class="sxs-lookup"><span data-stu-id="e9d16-160">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="e9d16-161">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="e9d16-161">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

<span data-ttu-id="e9d16-163">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="e9d16-163">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="e9d16-164">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="e9d16-164">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="e9d16-165">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="e9d16-165">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="e9d16-166">將 **架構** 設定為 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="e9d16-166">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="e9d16-167">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="e9d16-167">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="e9d16-168">將 **組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="e9d16-168">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="e9d16-169">將 **UWP SDK** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="e9d16-169">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="e9d16-170">將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題</span><span class="sxs-lookup"><span data-stu-id="e9d16-170">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

<span data-ttu-id="e9d16-172">設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../../../design/app-views.md) ，而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="e9d16-172">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="e9d16-173">Unity 2019 中的舊版 XR 已被取代，並已在 Unity 2020 中移除。</span><span class="sxs-lookup"><span data-stu-id="e9d16-173">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="e9d16-174">從組建設定開啟 **播放機設定** ... **視窗** 並展開 [ **XR 設定** ] 群組</span><span class="sxs-lookup"><span data-stu-id="e9d16-174">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="e9d16-175">在 [ **XR 設定** ] 區段中，選取 [ **支援的虛擬實境** 新增虛擬實境裝置] 清單</span><span class="sxs-lookup"><span data-stu-id="e9d16-175">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="e9d16-176">將 **深度格式** 設定為 **16 位深度** ，並啟用 **深度緩衝區共用**</span><span class="sxs-lookup"><span data-stu-id="e9d16-176">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="e9d16-177">將 **身歷聲轉譯模式** 設定為 **單一傳遞實例**</span><span class="sxs-lookup"><span data-stu-id="e9d16-177">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="e9d16-178">如果您想要使用全像攝影的遠端處理，請選取 [不 **支援的 WSA** 全像</span><span class="sxs-lookup"><span data-stu-id="e9d16-178">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![醒目提示 [播放程式設定] 區段的 [在 unity 編輯器中開啟專案設定] 視窗的螢幕擷取畫面](../../images/wmr-config-img-9.png)