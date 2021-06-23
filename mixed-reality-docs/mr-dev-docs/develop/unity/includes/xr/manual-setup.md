---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2021
ms.locfileid: "112535825"
---
# <a name="openxr"></a>[<span data-ttu-id="4b03b-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4b03b-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="4b03b-102">使用新的混合現實功能工具應用程式來安裝 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="4b03b-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="4b03b-103">遵循 [安裝和使用方式指示](../../welcome-to-mr-feature-tool.md)，並在 **平臺支援** 類別中選取 **Mixed Reality OpenXR 外掛程式** 套件：</span><span class="sxs-lookup"><span data-stu-id="4b03b-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![醒目提示 open xr 外掛程式的混合現實功能工具套件視窗](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="4b03b-105">設定您的組建目標</span><span class="sxs-lookup"><span data-stu-id="4b03b-105">Setting your build target</span></span>

<span data-ttu-id="4b03b-106">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="4b03b-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

<span data-ttu-id="4b03b-108">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="4b03b-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="4b03b-109">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="4b03b-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="4b03b-110">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="4b03b-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="4b03b-111">將 [架構] 設定為 [ARM64]</span><span class="sxs-lookup"><span data-stu-id="4b03b-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="4b03b-112">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="4b03b-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="4b03b-113">將 [組建類型] 設定為 [D3D 專案]</span><span class="sxs-lookup"><span data-stu-id="4b03b-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="4b03b-114">將 **目標 SDK 版本** 設為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="4b03b-114">Set **Target SDK Version** to **Latest installed**</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="4b03b-116">設定 OpenXR 的 XR 外掛程式管理</span><span class="sxs-lookup"><span data-stu-id="4b03b-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="4b03b-117">若要將 OpenXR 設定為 Unity 中的執行時間：</span><span class="sxs-lookup"><span data-stu-id="4b03b-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="4b03b-118">在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]</span><span class="sxs-lookup"><span data-stu-id="4b03b-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="4b03b-119">在設定清單中，選取 [ **XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="4b03b-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="4b03b-120">如果已醒目提示 ![ XR 外掛程式管理的 unity 編輯器中開啟的 [專案設定] 視窗螢幕擷取畫面，請選取 [安裝 XR 外掛程式管理]](../../images/wmr-config-img-5.png)</span><span class="sxs-lookup"><span data-stu-id="4b03b-120">Select **Install XR Plugin Management** if it appears ![Screenshot of Project Settings window open in unity editor with XR Plugin management highlighted](../../images/wmr-config-img-5.png)</span></span>
4. <span data-ttu-id="4b03b-121">勾選 [ **啟動時初始化 XR** ] 方塊</span><span class="sxs-lookup"><span data-stu-id="4b03b-121">Check the **Initialize XR on Startup** box</span></span>
5. <span data-ttu-id="4b03b-122">如果以 Desktop VR 為目標，請停留在 [電腦獨立] 索引標籤 (監視器) 並檢查 **OpenXR** 和 **Windows Mixed Reality 功能集** 方塊</span><span class="sxs-lookup"><span data-stu-id="4b03b-122">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
6. <span data-ttu-id="4b03b-123">如果以 HoloLens 2 為目標，請切換至 (Windows 標誌) 的通用 Windows 平臺索引標籤，然後選取 [ **OpenXR** ] 和 [ **Microsoft HoloLens 功能集** ] 方塊。</span><span class="sxs-lookup"><span data-stu-id="4b03b-123">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="4b03b-125">如果您在 **OpenXR 外掛程式** 旁邊看到黃色警告圖示，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4b03b-125">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="4b03b-126">Unity 編輯器可能需要自行重新開機，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="4b03b-126">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 專案驗證視窗的螢幕擷取畫面](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="4b03b-128">Optimization</span><span class="sxs-lookup"><span data-stu-id="4b03b-128">Optimization</span></span>

<span data-ttu-id="4b03b-129">如果您是針對 HoloLens 2 進行開發，請選取 [ **混合現實] > 專案 > 套用 HoloLens 2 功能表項目的建議專案設定** ，以取得更佳的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="4b03b-129">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](../../images/openxr-img-08.png)

<span data-ttu-id="4b03b-131">您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！</span><span class="sxs-lookup"><span data-stu-id="4b03b-131">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="4b03b-132">繼續進行下一節，以瞭解如何使用 OpenXR 範例。</span><span class="sxs-lookup"><span data-stu-id="4b03b-132">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="4b03b-133">適用于 OpenXR 和 HoloLens 2 的 Unity 範例專案</span><span class="sxs-lookup"><span data-stu-id="4b03b-133">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="4b03b-134">查看範例 unity 專案的 [OpenXR Mixed Reality 範例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 存放庫展示如何使用 Mixed reality OpenXR 外掛程式建立 HoloLens 2 或混合現實耳機的 unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b03b-134">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="4b03b-135">或者，如果您已準備好從空白專案開始使用，請繼續進行 [攝影機安裝](../../camera-in-unity.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="4b03b-135">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="4b03b-136">Windows XR</span><span class="sxs-lookup"><span data-stu-id="4b03b-136">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="4b03b-137">Unity 2021.1 中的 Windows XR 外掛程式已被取代，並將在 Unity 2021.2 中移除。</span><span class="sxs-lookup"><span data-stu-id="4b03b-137">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="4b03b-138">針對 Unity 2020 開發，Microsoft 建議改用 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="4b03b-138">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="4b03b-139">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="4b03b-139">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

<span data-ttu-id="4b03b-141">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="4b03b-141">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="4b03b-142">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="4b03b-142">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="4b03b-143">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="4b03b-143">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="4b03b-144">將 [架構] 設定為 [ARM64]</span><span class="sxs-lookup"><span data-stu-id="4b03b-144">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="4b03b-145">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="4b03b-145">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="4b03b-146">將 [組建類型] 設定為 [D3D 專案]</span><span class="sxs-lookup"><span data-stu-id="4b03b-146">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="4b03b-147">將 **目標 SDK 版本** 設為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="4b03b-147">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="4b03b-148">將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題</span><span class="sxs-lookup"><span data-stu-id="4b03b-148">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

<span data-ttu-id="4b03b-150">設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../../../design/app-views.md) ，而不是2d 視圖：</span><span class="sxs-lookup"><span data-stu-id="4b03b-150">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="4b03b-151">在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]，然後選取 [ **XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="4b03b-151">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="4b03b-152">如果出現 **XR 外掛程式管理** ，請選取 [安裝]</span><span class="sxs-lookup"><span data-stu-id="4b03b-152">Select **Install XR Plugin Management** if it appears</span></span>

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="4b03b-154">選取 [ **啟動時初始化 XR** ] 和 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="4b03b-154">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="4b03b-156">選取 [ **XR 外掛程式管理**  >  **Windows Mixed Reality** ] 區段，檢查所有方塊，並將 **深度緩衝區格式** 設定為 **深度緩衝區16位**</span><span class="sxs-lookup"><span data-stu-id="4b03b-156">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![在 unity 編輯器中開啟的 [專案設定] 視窗的螢幕擷取畫面，其中已醒目提示 Windows Mixed Reality 區段](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="4b03b-158">傳統 XR</span><span class="sxs-lookup"><span data-stu-id="4b03b-158">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="4b03b-159">Unity 2019 中的舊版 XR 已被取代，並已在 Unity 2020 中移除。</span><span class="sxs-lookup"><span data-stu-id="4b03b-159">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="4b03b-160">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="4b03b-160">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

<span data-ttu-id="4b03b-162">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="4b03b-162">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="4b03b-163">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="4b03b-163">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="4b03b-164">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="4b03b-164">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="4b03b-165">將 [架構] 設定為 [ARM64]</span><span class="sxs-lookup"><span data-stu-id="4b03b-165">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="4b03b-166">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="4b03b-166">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="4b03b-167">將 [組建類型] 設定為 [D3D 專案]</span><span class="sxs-lookup"><span data-stu-id="4b03b-167">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="4b03b-168">將 **目標 SDK 版本** 設為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="4b03b-168">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="4b03b-169">將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題</span><span class="sxs-lookup"><span data-stu-id="4b03b-169">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

<span data-ttu-id="4b03b-171">設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../../../design/app-views.md) ，而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="4b03b-171">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="4b03b-172">從組建設定開啟 **播放機設定** ... **視窗** 並展開 [ **XR 設定** ] 群組</span><span class="sxs-lookup"><span data-stu-id="4b03b-172">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="4b03b-173">在 [ **XR 設定** ] 區段中，選取 [ **支援的虛擬實境** 新增虛擬實境裝置] 清單</span><span class="sxs-lookup"><span data-stu-id="4b03b-173">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="4b03b-174">將 **深度格式** 設定為 **16 位深度**，並勾選 [**啟用深度緩衝區共用**]</span><span class="sxs-lookup"><span data-stu-id="4b03b-174">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="4b03b-175">將 [立體聲轉譯模式] 設定為 [單程執行個體]</span><span class="sxs-lookup"><span data-stu-id="4b03b-175">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="4b03b-176">如果您想要使用全像攝影模式的遠端處理功能，請選取 [不 **支援的 WSA** 全像</span><span class="sxs-lookup"><span data-stu-id="4b03b-176">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![醒目提示 [播放程式設定] 區段的 [在 unity 編輯器中開啟專案設定] 視窗的螢幕擷取畫面](../../images/wmr-config-img-9.png)
