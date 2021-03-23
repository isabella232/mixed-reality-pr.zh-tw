---
title: 在不 MRTK 的情況下設定您的專案
description: 瞭解如何為沒有混合現實工具組的 Windows Mixed Reality 設定新的 Unity 專案。
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity，混合的現實，開發，使用者入門，新專案，Windows Mixed Reality，UWP，XR，效能
ms.openlocfilehash: 47ca4041e997d623d08fa1732f7039c655810bfc
ms.sourcegitcommit: b0fb5497bf9f280ba5610c30e4b9e5aa1cda52c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104837412"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="51fcf-104">在沒有 MRTK 的情況下設定專案</span><span class="sxs-lookup"><span data-stu-id="51fcf-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="51fcf-105">Windows Mixed Reality (WMR) 是在 Windows 10 作業系統中引進的 Microsoft 平臺。</span><span class="sxs-lookup"><span data-stu-id="51fcf-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="51fcf-106">WMR 平臺可讓您建立應用程式，以在全像全像 VR 的顯示裝置上呈現數位內容。</span><span class="sxs-lookup"><span data-stu-id="51fcf-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="51fcf-107">雖然 Microsoft 和社區建立了開放原始碼工具，例如 [混合現實工具組 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) ，而這些工具會自動設定 WMR 的環境，但許多開發人員想要從頭開始建立他們的體驗。</span><span class="sxs-lookup"><span data-stu-id="51fcf-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="51fcf-108">當您使用 MRTK 時，下列檔將示範如何針對混合現實開發正確設定專案。</span><span class="sxs-lookup"><span data-stu-id="51fcf-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="51fcf-109">您需要變更的設定分為兩類：每個專案設定和個別場景設定。</span><span class="sxs-lookup"><span data-stu-id="51fcf-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="51fcf-110">您稍後可以隨時匯入 MRTK，如此一來，就不會再進行手動路由。</span><span class="sxs-lookup"><span data-stu-id="51fcf-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="51fcf-111">如果您選擇 WMR 手動設定，您需要變更的設定會分成兩種類別：個別專案和每一場景。</span><span class="sxs-lookup"><span data-stu-id="51fcf-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="51fcf-112">每個專案的設定</span><span class="sxs-lookup"><span data-stu-id="51fcf-112">Per-project settings</span></span>

<span data-ttu-id="51fcf-113">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="51fcf-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](images/wmr-config-img-3.png)

<span data-ttu-id="51fcf-115">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="51fcf-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="51fcf-116">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="51fcf-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="51fcf-117">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="51fcf-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="51fcf-118">將 **架構** 設定為 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="51fcf-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="51fcf-119">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="51fcf-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="51fcf-120">將 **組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="51fcf-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="51fcf-121">將 **UWP SDK** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="51fcf-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="51fcf-122">將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題</span><span class="sxs-lookup"><span data-stu-id="51fcf-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](images/wmr-config-img-4.png)

<span data-ttu-id="51fcf-124">設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../design/app-views.md) ，而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="51fcf-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="51fcf-125">針對 XRSDK</span><span class="sxs-lookup"><span data-stu-id="51fcf-125">For XRSDK</span></span> 

1. <span data-ttu-id="51fcf-126">在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]，然後選取 [ **XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="51fcf-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="51fcf-127">選取 [**安裝 XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="51fcf-127">Select **Install XR Plugin Management**</span></span>

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-5.png)

3. <span data-ttu-id="51fcf-129">選取 [ **啟動時初始化 XR** ] 和 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="51fcf-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-7.png)

4. <span data-ttu-id="51fcf-131">展開 [ **XR 外掛程式管理** ] 區段，然後選取 [ **通用 Windows 平臺設定** ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="51fcf-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="51fcf-132">如果您使用 Unity 2020 或更新版本，您會看到檢查 **OpenXR** 或 **Windows Mixed Reality** 的選項。</span><span class="sxs-lookup"><span data-stu-id="51fcf-132">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="51fcf-133">您可以選擇任一執行時間。</span><span class="sxs-lookup"><span data-stu-id="51fcf-133">You can choose either runtime.</span></span>  <span data-ttu-id="51fcf-134">如果您要特別針對 HoloLens 2 或 HP 回條 G2 進行開發，並決定嘗試 **OpenXR**，請選取 [OpenXR] 方塊，並查看我們的指南，以 [使用 Unity 的 Mixed Reality OpenXR 外掛程式](openxr-getting-started.md) ，以在返回本教學課程之前，為這些裝置正確設定</span><span class="sxs-lookup"><span data-stu-id="51fcf-134">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="51fcf-135">從 Unity 2020 LTS 開始，Microsoft 正採用 OpenXR 進行開發。</span><span class="sxs-lookup"><span data-stu-id="51fcf-135">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="51fcf-136">當我們遷移至此路徑時，在 Unity 2021.1 中，Windows XR 外掛程式將會被取代，並在2021.2 中移除，讓 OpenXR 唯一支援的路徑。</span><span class="sxs-lookup"><span data-stu-id="51fcf-136">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="51fcf-137">您可以在中找到更多有關 [使用 Mixed Reality OpenXR 外掛程式](openxr-getting-started.md)的資訊。</span><span class="sxs-lookup"><span data-stu-id="51fcf-137">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="51fcf-138">如果您決定選擇 **Windows Mixed Reality** 外掛程式，請檢查所有方塊，並將 **深度提交模式** 設定為 **深度16位**</span><span class="sxs-lookup"><span data-stu-id="51fcf-138">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![在 unity 編輯器中開啟的 [專案設定] 視窗的螢幕擷取畫面，其中已醒目提示 Windows Mixed Reality 區段](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="51fcf-140">針對舊版 XR</span><span class="sxs-lookup"><span data-stu-id="51fcf-140">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="51fcf-141">Unity 2019 中的舊版 XR 已被取代，並已在 Unity 2020 中移除。</span><span class="sxs-lookup"><span data-stu-id="51fcf-141">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="51fcf-142">從組建設定開啟 **播放機設定** ... **視窗** 並展開 [ **XR 設定** ] 群組</span><span class="sxs-lookup"><span data-stu-id="51fcf-142">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="51fcf-143">在 [ **XR 設定** ] 區段中，選取 [ **支援的虛擬實境** 新增虛擬實境裝置] 清單</span><span class="sxs-lookup"><span data-stu-id="51fcf-143">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="51fcf-144">將 **深度格式** 設定為 **16 位深度** ，並啟用 **深度緩衝區共用**</span><span class="sxs-lookup"><span data-stu-id="51fcf-144">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="51fcf-145">將 **身歷聲轉譯模式** 設定為 **單一傳遞實例**</span><span class="sxs-lookup"><span data-stu-id="51fcf-145">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="51fcf-146">如果您想要使用全像攝影的遠端處理，請選取 [不 **支援的 WSA** 全像</span><span class="sxs-lookup"><span data-stu-id="51fcf-146">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![醒目提示 [播放程式設定] 區段的 [在 unity 編輯器中開啟專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="51fcf-148">更新資訊清單</span><span class="sxs-lookup"><span data-stu-id="51fcf-148">Updating the manifest</span></span>

<span data-ttu-id="51fcf-149">您的應用程式現在可以處理全像呈現和空間輸入。</span><span class="sxs-lookup"><span data-stu-id="51fcf-149">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="51fcf-150">不過，您的應用程式需要在其資訊清單中宣告適當的功能，以利用特定功能。</span><span class="sxs-lookup"><span data-stu-id="51fcf-150">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="51fcf-151">您可以前往 [ **播放程式設定] > 設定通用 Windows 平臺 > 發佈設定 > 功能**，找出您的專案功能。</span><span class="sxs-lookup"><span data-stu-id="51fcf-151">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="51fcf-152">建議您讓 Unity 中的資訊清單宣告將它們包含在您匯出的所有未來專案中。</span><span class="sxs-lookup"><span data-stu-id="51fcf-152">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="51fcf-153">針對混合現實啟用常用 Unity Api 的適用功能如下：</span><span class="sxs-lookup"><span data-stu-id="51fcf-153">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="51fcf-154">功能</span><span class="sxs-lookup"><span data-stu-id="51fcf-154">Capability</span></span>  |  <span data-ttu-id="51fcf-155">需要功能的 Api</span><span class="sxs-lookup"><span data-stu-id="51fcf-155">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="51fcf-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="51fcf-156">SpatialPerception</span></span>  |  <span data-ttu-id="51fcf-157">SurfaceObserver (在 HoloLens 上存取 [空間對應](../../design/spatial-mapping.md)網格) &mdash; *不需要一般空間追蹤耳機的功能*</span><span class="sxs-lookup"><span data-stu-id="51fcf-157">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="51fcf-158">攝像頭</span><span class="sxs-lookup"><span data-stu-id="51fcf-158">WebCam</span></span>  |  <span data-ttu-id="51fcf-159">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="51fcf-159">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="51fcf-160">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="51fcf-160">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="51fcf-161">PhotoCapture 或 VideoCapture，分別 (儲存已捕捉的內容時) </span><span class="sxs-lookup"><span data-stu-id="51fcf-161">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="51fcf-162">麥克風</span><span class="sxs-lookup"><span data-stu-id="51fcf-162">Microphone</span></span>  |  <span data-ttu-id="51fcf-163">VideoCapture 捕獲音訊) 、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer 時的 (</span><span class="sxs-lookup"><span data-stu-id="51fcf-163">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="51fcf-164">InternetClient</span><span class="sxs-lookup"><span data-stu-id="51fcf-164">InternetClient</span></span>  |  <span data-ttu-id="51fcf-165">DictationRecognizer (並使用 Unity Profiler) </span><span class="sxs-lookup"><span data-stu-id="51fcf-165">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="51fcf-166">品質設定</span><span class="sxs-lookup"><span data-stu-id="51fcf-166">Quality settings</span></span>

<span data-ttu-id="51fcf-167">HoloLens 有行動類別 GPU。</span><span class="sxs-lookup"><span data-stu-id="51fcf-167">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="51fcf-168">如果您的應用程式是以 HoloLens 為目標，您會想要從已調整為最快效能的應用程式中品質設定開始，以確保其維持完整的畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="51fcf-168">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="51fcf-169">當您在開發過程中進一步開發之後，您可以考慮 upping 品質設定，以找出品質和效能的正確平衡：</span><span class="sxs-lookup"><span data-stu-id="51fcf-169">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="51fcf-170">選取 [ **編輯] > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="51fcf-170">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="51fcf-171">選取 [ **Windows Store**] 標誌底下的 **下拉式清單**   ，然後選取 [ **非常低**]。</span><span class="sxs-lookup"><span data-stu-id="51fcf-171">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="51fcf-172">您會知道當 Windows Store 資料行中的方塊和非常低的資料列中的方塊為綠色時，會正確套用設定</span><span class="sxs-lookup"><span data-stu-id="51fcf-172">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="51fcf-173">在 [ **遮蔽**]   區段中，選取 [停用 **陰影**]</span><span class="sxs-lookup"><span data-stu-id="51fcf-173">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="51fcf-174">![醒目提示 [品質設定] 區段的 unity 編輯器中開啟的 [專案設定] 視窗螢幕擷取畫面](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="51fcf-174">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="51fcf-175">*Unity 品質設定*</span><span class="sxs-lookup"><span data-stu-id="51fcf-175">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="51fcf-176">每場景設定</span><span class="sxs-lookup"><span data-stu-id="51fcf-176">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="51fcf-177">Unity 攝影機設定</span><span class="sxs-lookup"><span data-stu-id="51fcf-177">Unity camera settings</span></span>

<span data-ttu-id="51fcf-178">若已核取 [ **虛擬事實** ]，則 [Unity 攝影機](camera-in-unity.md) 元件會處理 [標頭追蹤和 stereoscopic](../platform-capabilities-and-apis/rendering.md)轉譯。</span><span class="sxs-lookup"><span data-stu-id="51fcf-178">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="51fcf-179">這表示您不需要使用自訂相機來取代主要攝影機物件。</span><span class="sxs-lookup"><span data-stu-id="51fcf-179">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="51fcf-180">如果您的應用程式是以 HoloLens 為目標，則您必須變更一些設定，以針對裝置的透明顯示進行優化。</span><span class="sxs-lookup"><span data-stu-id="51fcf-180">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="51fcf-181">這些設定可讓您的全像全球內容顯示到實體世界：</span><span class="sxs-lookup"><span data-stu-id="51fcf-181">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="51fcf-182">**在階層中，選取\*\*\*\*主要攝影機**</span><span class="sxs-lookup"><span data-stu-id="51fcf-182">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="51fcf-183">在 [偵測 **器** ] 面板中，將轉換 **位置** 設定為 **0、0、0** ，讓使用者的標頭位置開始于 Unity world 來源。</span><span class="sxs-lookup"><span data-stu-id="51fcf-183">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="51fcf-184">將 **清除旗標** 變更為 **純色**。</span><span class="sxs-lookup"><span data-stu-id="51fcf-184">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="51fcf-185">將 **背景** 色彩變更為 **RGBA 0、0、0、0**。</span><span class="sxs-lookup"><span data-stu-id="51fcf-185">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="51fcf-186">在 HoloLens 中，黑色呈現為透明。</span><span class="sxs-lookup"><span data-stu-id="51fcf-186">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="51fcf-187">變更 **裁剪平面-接近** [HoloLens 建議](camera-in-unity.md#clip-planes) 的 0.85 (計量) 。</span><span class="sxs-lookup"><span data-stu-id="51fcf-187">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="51fcf-188">![在 Unity 編輯器中開啟之偵測器索引標籤的螢幕擷取畫面](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="51fcf-188">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="51fcf-189">*Unity 攝影機設定*</span><span class="sxs-lookup"><span data-stu-id="51fcf-189">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51fcf-190">如果您刪除並建立新的相機，請確定您的新相機已標記為 **MainCamera**。</span><span class="sxs-lookup"><span data-stu-id="51fcf-190">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="51fcf-191">下一步</span><span class="sxs-lookup"><span data-stu-id="51fcf-191">Next steps</span></span>

<span data-ttu-id="51fcf-192">現在您的專案已經準備就緒，您可以開始開發混合現實體驗：</span><span class="sxs-lookup"><span data-stu-id="51fcf-192">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="51fcf-193">新增 [核心組建區塊](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="51fcf-193">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="51fcf-194">查看可用 [的平臺功能和 api](unity-development-overview.md#3-advanced-features)</span><span class="sxs-lookup"><span data-stu-id="51fcf-194">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="51fcf-195">瞭解如何 [部署您的應用程式](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="51fcf-195">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="51fcf-196">使用[混合現實](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)模擬器</span><span class="sxs-lookup"><span data-stu-id="51fcf-196">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="51fcf-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51fcf-197">See also</span></span>
* [<span data-ttu-id="51fcf-198">安裝工具</span><span class="sxs-lookup"><span data-stu-id="51fcf-198">Install the tools</span></span>](../install-the-tools.md)