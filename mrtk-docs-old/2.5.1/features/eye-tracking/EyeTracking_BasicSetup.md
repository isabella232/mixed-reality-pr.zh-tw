---
title: EyeTracking_BasicSetup
description: 如何在 MRTK 中設定眼睛追蹤
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、眼睛追蹤、
ms.openlocfilehash: c36c29d86f8ff47c57857bc36f358c9213ae4744
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682451"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="e7b4b-104">開始在 MRTK 中使用眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="e7b4b-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="e7b4b-105">本頁面涵蓋如何設定您的 Unity MRTK 場景，以在應用程式中使用眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="e7b4b-106">以下假設您是以全新的新場景開始。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="e7b4b-107">或者，您可以查看我們已設定的 [MRTK 眼睛追蹤範例](EyeTracking_ExamplesOverview.md) ，其中包含可供您直接建立的大量絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](EyeTracking_ExamplesOverview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="e7b4b-108">目視追蹤需求檢查清單</span><span class="sxs-lookup"><span data-stu-id="e7b4b-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="e7b4b-109">若要讓眼睛追蹤正常運作，必須符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="e7b4b-110">如果您不熟悉 HoloLens 2 上的眼睛追蹤，以及如何在 MRTK 中設定眼睛追蹤，請別擔心！</span><span class="sxs-lookup"><span data-stu-id="e7b4b-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="e7b4b-111">我們將詳細說明如何解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="e7b4b-112">您必須將「 _眼睛眼 Data Provider_ 」新增至輸入系統。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="e7b4b-113">這會從平臺提供眼睛追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="e7b4b-114">應用程式資訊清單中必須啟用 _' GazeInput '_ 功能。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="e7b4b-115">**這項功能可以在 Unity 2019 中設定，但在 Unity 2018 和更早版本中，這項功能僅適用于 Visual Studio 以及透過 MRTK build tool**</span><span class="sxs-lookup"><span data-stu-id="e7b4b-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="e7b4b-116">HoloLens **必須** 針對目前的使用者進行眼睛校正。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="e7b4b-117">請查看我們 [的範例，以偵測使用者是否已校正](EyeTracking_IsUserCalibrated.md)。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-117">Check out our [sample for detecting whether a user is eye calibrated or not](EyeTracking_IsUserCalibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="e7b4b-118">GazeInput 功能的注意事項</span><span class="sxs-lookup"><span data-stu-id="e7b4b-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="e7b4b-119">MRTK 提供的組建工具 (，也就是混合現實工具組-> 公用程式-> 組建視窗) 可以自動為您啟用 GazeInput 功能。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="e7b4b-120">若要這樣做，您必須確定已核取 [Appx 組建選項] 索引標籤上的 [注視輸入功能]：</span><span class="sxs-lookup"><span data-stu-id="e7b4b-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![MRTK Build Tools](../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="e7b4b-122">此工具會在 Unity 組建完成後找到 AppX 資訊清單，並以手動方式新增 GazeInput 功能。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="e7b4b-123">**在 unity 2019 之前，使用 unity 的內建組建視窗時，此工具不會處於使用中狀態， (也就是** > 的組建設定) 。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="e7b4b-124">在 Unity 2019 之前，使用 Unity 的 [組建] 視窗時，必須在 Unity 組建之後以手動方式新增功能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e7b4b-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="e7b4b-125">開啟您已編譯的 Visual Studio 專案，然後在您的方案中開啟 _' package.appxmanifest '_ 。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="e7b4b-126">請務必勾選 [_功能_] 下的 [ _GazeInput_ ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="e7b4b-127">如果您沒有看到「 _GazeInput_ 」功能，請確認您的系統符合 [使用 MRTK](../../Installation.md#prerequisites) (的必要條件，特別是 Windows SDK 版本) 。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](../../Installation.md#prerequisites) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="e7b4b-128">_請注意：_ 如果您建立的是新的組建資料夾，就只需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="e7b4b-129">這表示，如果您已經建立 Unity 專案，並在之前設定 package.appxmanifest，而且現在將目標設為相同的資料夾，您就不需要重新套用變更。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="e7b4b-130">逐步設定眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="e7b4b-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="e7b4b-131">設定場景</span><span class="sxs-lookup"><span data-stu-id="e7b4b-131">Setting up the scene</span></span>

<span data-ttu-id="e7b4b-132">只要按一下 [ _Mixed Reality 工具組-> 設定 ..._ ]，即可設定 _MixedRealityToolkit_</span><span class="sxs-lookup"><span data-stu-id="e7b4b-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="e7b4b-133">在功能表列中。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-133">in the menu bar.</span></span>

![MRTK 安裝程式設定](../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="e7b4b-135">設定眼睛追蹤所需的 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="e7b4b-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="e7b4b-136">設定 MRTK 場景之後，系統會要求您選擇 MRTK 的設定檔。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="e7b4b-137">您可以直接選取 [ _DefaultMixedRealityToolkitConfigurationProfile_ ]，然後選取 [ _複製 & 自訂_ ] 選項。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![MRTK 設定檔設定](../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a><span data-ttu-id="e7b4b-139">建立「眼睛注視資料提供者」</span><span class="sxs-lookup"><span data-stu-id="e7b4b-139">Create an "eye gaze data provider"</span></span>

- <span data-ttu-id="e7b4b-140">按一下 MRTK 設定檔中的 [ _輸入_ ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-140">Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id="e7b4b-141">若要編輯預設值 ( [ _DefaultMixedRealityInputSystemProfile_ ] ) ，請按一下其旁邊的 [ _複製_ ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="e7b4b-142">[ _複製設定檔_ ] 功能表隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="e7b4b-143">只要按一下該功能表底部的 [ _複製_ ] 即可。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="e7b4b-144">按兩下新的輸入設定檔，展開 [ _輸入資料提供者_]，然後選取 [ _+ 新增 Data Provider_]。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="e7b4b-145">建立新的資料提供者：</span><span class="sxs-lookup"><span data-stu-id="e7b4b-145">Create a new data provider:</span></span>
  - <span data-ttu-id="e7b4b-146">在 [**類型**] 下，選取 [ _MixedReality] WindowsMixedReality。輸入 '_  ->  _' WindowsMixedRealityEyeGazeDataProvider '_</span><span class="sxs-lookup"><span data-stu-id="e7b4b-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="e7b4b-147">針對 **平臺 (s)** 選取 [ _Windows 通用_]。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![MRTK 資料提供者](../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="e7b4b-149">在 Unity 編輯器中模擬目視追蹤</span><span class="sxs-lookup"><span data-stu-id="e7b4b-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="e7b4b-150">您可以在 Unity 編輯器中模擬眼睛追蹤輸入，以確保在將應用程式部署到您的 HoloLens 2 之前，已正確觸發事件。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="e7b4b-151">您只需使用相機的位置做為眼睛眼睛，並將攝影機的正向向量視為眼睛的方向，即可模擬眼睛信號。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="e7b4b-152">雖然這很適合用於初始測試，但請注意，它不是快速眼移動的理想仿造。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="e7b4b-153">為了達到此效果，最好是確保經常測試 HoloLens 2 上的眼睛型互動。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="e7b4b-154">**啟用模擬的眼睛追蹤**：</span><span class="sxs-lookup"><span data-stu-id="e7b4b-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="e7b4b-155">按一下 MRTK 設定檔中的 [ _輸入_ ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="e7b4b-156">從該處流覽至「_輸入資料提供者_」  ->  _的「輸入模擬服務_」。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="e7b4b-157">複製 _' DefaultMixedRealityInputSimpulationProfile '_ 以進行變更。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="e7b4b-158">選取 [ _模擬眼睛位置_ ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![MRTK 眼睛模擬設定](../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="e7b4b-160">**停用預設** 的前端資料指標：一般而言，建議您避免顯示眼睛指標，或是絕對需要使其變 _得非常_ 微妙。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="e7b4b-161">建議您根據預設，隱藏附加至 MRTK 注視指標設定檔的預設標頭注視游標。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="e7b4b-162">流覽至您的 MRTK 設定設定檔-> _' Input '_  ->  _' 指標 '_</span><span class="sxs-lookup"><span data-stu-id="e7b4b-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="e7b4b-163">複製 _' DefaultMixedRealityInputPointerProfile '_ 以進行變更。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="e7b4b-164">在 [ _指標設定_] 的頂端，您應該將不可見的資料指標預製專案指派給 _' GazeCursor '_。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="e7b4b-165">若要這麼做，您可以從 MRTK Foundation 中選取 [ _EyeGazeCursor_ ] 預製專案。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="e7b4b-166">在注視提供者中啟用以眼睛為基礎的注視</span><span class="sxs-lookup"><span data-stu-id="e7b4b-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="e7b4b-167">在 HoloLens v1 中，用來做為主要指標技術的標頭。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="e7b4b-168">雖然仍可透過連接到 [相機](https://docs.unity3d.com/ScriptReference/Camera.html)的 MRTK 中的 _GazeProvider_ 來使用前端，但您可以改為勾選輸入指標設定檔的眼睛設定中的 [ _IsEyeTrackingEnabled_ ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="e7b4b-169">藉由變更 _' GazeProvider '_ 的 _' IsEyeTrackingEnabled '_ 屬性，開發人員可以在程式碼中切換眼睛和前端。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="e7b4b-170">如果不符合任何眼睛追蹤需求，應用程式將會自動切換回以前端為基礎的注視。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="e7b4b-171">存取眼睛資料</span><span class="sxs-lookup"><span data-stu-id="e7b4b-171">Accessing eye gaze data</span></span>

<span data-ttu-id="e7b4b-172">現在您的場景已設定為使用眼睛追蹤，讓我們看看如何在您的腳本中進行存取：透過 EyeGazeProvider 和[支援的目標選取專案](EyeTracking_TargetSelection.md)來存取[眼睛追蹤資料](EyeTracking_EyeGazeProvider.md)。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](EyeTracking_EyeGazeProvider.md) and [eye-supported target selections](EyeTracking_TargetSelection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="e7b4b-173">在 HoloLens 2 上測試 Unity 應用程式</span><span class="sxs-lookup"><span data-stu-id="e7b4b-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="e7b4b-174">使用眼睛追蹤建立您的應用程式應該類似于編譯其他 HoloLens 2 MRTK 應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="e7b4b-175">請確定您已依照上述 [*GazeInput 功能*](#a-note-on-the-gazeinput-capability)一節中所述的方式啟用「*注視輸入*」功能。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="e7b4b-176">眼睛校正</span><span class="sxs-lookup"><span data-stu-id="e7b4b-176">Eye calibration</span></span>

<span data-ttu-id="e7b4b-177">最後，請別忘了在 HoloLens 2 上執行眼睛校正。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="e7b4b-178">如果未校正使用者，則眼睛追蹤系統將不會傳回任何輸入。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="e7b4b-179">取得校正最簡單的方式，就是向上復原面板和向下切換。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="e7b4b-180">系統通知應該會出現，歡迎您成為新的使用者，並要求您完成眼睛校正。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="e7b4b-181">或者，您可以在 [系統設定：設定 > 系統 > 校正] 中找到視覺校正 > 執行眼睛校正。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="e7b4b-182">目視追蹤許可權</span><span class="sxs-lookup"><span data-stu-id="e7b4b-182">Eye tracking permission</span></span>

<span data-ttu-id="e7b4b-183">當您第一次在 HoloLens 2 上啟動應用程式時，會出現提示，要求使用者提供使用眼睛追蹤的許可權。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="e7b4b-184">如果未顯示，則這通常表示未設定「 _GazeInput_ 」功能。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="e7b4b-185">許可權提示出現一次之後，就不會再自動顯示。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="e7b4b-186">如果您「已 _拒絕眼追蹤」許可權_，您可以在 [設定-> 隱私權-> 應用程式] 中重設此項。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="e7b4b-187">這應該可讓您開始在 MRTK Unity 應用程式中使用眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="e7b4b-188">別忘了看看 [我們的 MRTK 眼睛追蹤教學課程和範例，](EyeTracking_ExamplesOverview.md) 示範如何使用眼睛追蹤輸入，並以便利的方式提供可在專案中重複使用的腳本。</span><span class="sxs-lookup"><span data-stu-id="e7b4b-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](EyeTracking_ExamplesOverview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="e7b4b-189">回到「MixedRealityToolkit 中的眼睛追蹤」</span><span class="sxs-lookup"><span data-stu-id="e7b4b-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](EyeTracking_Main.md)
