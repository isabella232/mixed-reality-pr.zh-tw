---
title: MRTK_Configuration_Dialog
description: 在 Unity 專案中設定 MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Unity
ms.openlocfilehash: b8984c81bf76268aa6643c918cb2acf0fac7f184
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694141"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="7f2ba-104">MRTK 專案設定對話方塊</span><span class="sxs-lookup"><span data-stu-id="7f2ba-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="7f2ba-105">當 Unity 載入專案時，會顯示 [MRTK 設定] 對話方塊，並判斷一或多個設定選項需要開發人員的注意力。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![稍後套用忽略](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="7f2ba-107">若要套用變更，請按一下 **[套用** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="7f2ba-108">**稍後** 的按鈕會延後變更，直到未來重新載入專案為止。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="7f2ba-109">如果有一或多個建議的設定保持未核取狀態，則 [設定] 對話方塊會再次出現。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="7f2ba-110">若要避免發生這種情況，請套用所需的選項，然後透過 **混合現實工具** 組公用程式來重新開機對話方塊，  >    >  **設定 Unity 專案**，然後按一下 [**忽略**]。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="7f2ba-111">這可防止設定對話方塊自動再次出現。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="7f2ba-112">一般設定</span><span class="sxs-lookup"><span data-stu-id="7f2ba-112">Common settings</span></span>

<span data-ttu-id="7f2ba-113">所有組建目標都會共用一組常見的選項。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-113">All build targets share a collection of common options.</span></span>

![一般設定](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="7f2ba-115">強制文字資產序列化和啟用可見的中繼檔案</span><span class="sxs-lookup"><span data-stu-id="7f2ba-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="7f2ba-116">這些設定有助於簡化使用 Unity 專案和原始檔控制系統 (例如： Git) 。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="7f2ba-117">啟用 VR 支援</span><span class="sxs-lookup"><span data-stu-id="7f2ba-117">Enable VR supported</span></span>

<span data-ttu-id="7f2ba-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="7f2ba-118">**Unity 2018**</span></span>

<span data-ttu-id="7f2ba-119">在 **Player 設定**  >  **XR 設定中設定** 虛擬實境支援的虛擬實境 SDK 選項。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="7f2ba-120">設定單一傳遞實例轉譯路徑</span><span class="sxs-lookup"><span data-stu-id="7f2ba-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="7f2ba-121">將 **播放機設定**  >  **XR 設定**  >  **身歷聲轉譯模式** 設定為 **單一階段實例**。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="7f2ba-122">設定預設空間感知層</span><span class="sxs-lookup"><span data-stu-id="7f2ba-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="7f2ba-123">將空間感知註冊為第31層，以啟用簡單且一致的 raycast 和物理選項設定。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="7f2ba-124">音訊空間定位器</span><span class="sxs-lookup"><span data-stu-id="7f2ba-124">Audio spatializer</span></span>

<span data-ttu-id="7f2ba-125">音訊 spatializers 是可發揮空間音效和位置音訊功能的元件，讓混合的現實體驗真正沉浸。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="7f2ba-126">將音訊空間定位器設定為 [無] 將會停用位置音訊功能。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="7f2ba-127">一般 spatializers</span><span class="sxs-lookup"><span data-stu-id="7f2ba-127">Common spatializers</span></span>

- <span data-ttu-id="7f2ba-128">Microsoft 空間定位器</span><span class="sxs-lookup"><span data-stu-id="7f2ba-128">Microsoft Spatializer</span></span>

<span data-ttu-id="7f2ba-129">Microsoft 提供的空間定位器可支援 HoloLens 2 上硬體加速的使用。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="7f2ba-130">此空間定位器可透過 [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) 和 [GitHub](https://github.com/microsoft/spatialaudio-unity)取得。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="7f2ba-131">如需 Microsoft 空間定位器的詳細資訊，請參閱 [空間音效檔](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-in-unity)。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="7f2ba-132">MS HRTF 空間定位器</span><span class="sxs-lookup"><span data-stu-id="7f2ba-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="7f2ba-133">Unity 提供的 Microsoft Windows 空間定位器，是 Windows Mixed Reality 和 Windows XR 平臺套件的一部分。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="7f2ba-134">共振音訊</span><span class="sxs-lookup"><span data-stu-id="7f2ba-134">Resonance Audio</span></span>

<span data-ttu-id="7f2ba-135">由 Unity 提供的 Google 跨平臺空間定位器。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="7f2ba-136">您可以在 [共振音訊檔](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) 網站上找到詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="7f2ba-137">通用 Windows 平臺設定</span><span class="sxs-lookup"><span data-stu-id="7f2ba-137">Universal Windows Platform settings</span></span>

![UWP 設定](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="enable-msbuild-for-unity"></a><span data-ttu-id="7f2ba-139">啟用適用于 Unity 的 MSBuild</span><span class="sxs-lookup"><span data-stu-id="7f2ba-139">Enable MSBuild for Unity</span></span>

<span data-ttu-id="7f2ba-140">**Unity 2019.2 及更早版本**</span><span class="sxs-lookup"><span data-stu-id="7f2ba-140">**Unity 2019.2 and earlier**</span></span>

<span data-ttu-id="7f2ba-141">MSBuild for Unity 是一種元件，可啟用特定 NuGet 套件的自動還原。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-141">MSBuild for Unity is a component that enables automatic restoring of specific NuGet packages.</span></span> <span data-ttu-id="7f2ba-142">在此版本中，會在啟用適用于 Unity 的 MSBuild 之後，安裝 **MixedReality. DotNetWinRT** 套件。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-142">In this version, the **Microsoft.Windows.MixedReality.DotNetWinRT** package will be installed after enabling MSBuild for Unity.</span></span>

### <a name="uwp-capabilities"></a><span data-ttu-id="7f2ba-143">UWP 功能</span><span class="sxs-lookup"><span data-stu-id="7f2ba-143">UWP Capabilities</span></span>

<span data-ttu-id="7f2ba-144">啟用通用 Windows 平臺應用程式的特定應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-144">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="7f2ba-145">這些功能可讓平臺通知和要求啟用特定功能的許可權。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-145">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="7f2ba-146">麥克風</span><span class="sxs-lookup"><span data-stu-id="7f2ba-146">Microphone</span></span>

  <span data-ttu-id="7f2ba-147">透過麥克風啟用捕捉音效。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-147">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="7f2ba-148">網際網路用戶端</span><span class="sxs-lookup"><span data-stu-id="7f2ba-148">Internet Client</span></span>

  <span data-ttu-id="7f2ba-149">啟用存取網際網路上資源的支援。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-149">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="7f2ba-150">空間感知</span><span class="sxs-lookup"><span data-stu-id="7f2ba-150">Spatial Perception</span></span>

  <span data-ttu-id="7f2ba-151">可支援使用真實世界的環境。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-151">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="7f2ba-152">眼睛</span><span class="sxs-lookup"><span data-stu-id="7f2ba-152">Eye Gaze</span></span>

  <span data-ttu-id="7f2ba-153">**Unity 2019.3 和更新版本**</span><span class="sxs-lookup"><span data-stu-id="7f2ba-153">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="7f2ba-154">啟用追蹤使用者眼睛的支援。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-154">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="7f2ba-155">避免 Unity ' PlayerSettings. graphicsJob ' 損毀</span><span class="sxs-lookup"><span data-stu-id="7f2ba-155">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="7f2ba-156">**Unity 2019.3 和更新版本**</span><span class="sxs-lookup"><span data-stu-id="7f2ba-156">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="7f2ba-157">在最新版的 Unity 2019 中，當啟用 [圖形工作] 時，應用程式會在部署到 HoloLens 2 時損毀。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-157">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="7f2ba-158">在 Unity 中，預設會啟用這項設定，但此錯誤存在 (查看 [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)) ，設定程式會預設為將圖形作業設定為 [false] (因此可讓部署到 HoloLens 2 的應用程式不會損毀) 。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-158">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="7f2ba-159">Android 設定</span><span class="sxs-lookup"><span data-stu-id="7f2ba-159">Android settings</span></span>

<span data-ttu-id="7f2ba-160">支援在 Android 供電裝置上進行 AR 應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-160">Configuration settings to support AR applications on Android powered devices.</span></span>

![Android 設定](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="7f2ba-162">停用多執行緒轉譯</span><span class="sxs-lookup"><span data-stu-id="7f2ba-162">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="7f2ba-163">停  >    >  用由 Android 的 AR 支援所需的其他設定 **多執行緒** 轉譯的播放程式設定。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-163">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="7f2ba-164">設定最小 API 層級</span><span class="sxs-lookup"><span data-stu-id="7f2ba-164">Set Minimum API Level</span></span>

<span data-ttu-id="7f2ba-165">將 [   >  **其他設定** 的  >  **最小 API 層級**] 設定的值設定為強制執行 AR 應用程式的作業系統需求。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-165">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="7f2ba-166">iOS 設定</span><span class="sxs-lookup"><span data-stu-id="7f2ba-166">iOS settings</span></span>

<span data-ttu-id="7f2ba-167">支援在 iOS 裝置上的 AR 應用程式進行的設定。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-167">Configuration settings to support AR applications on iOS powered devices.</span></span>

![iOS 設定](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="7f2ba-169">設定必要的 OS 版本</span><span class="sxs-lookup"><span data-stu-id="7f2ba-169">Set Required OS Version</span></span>

<span data-ttu-id="7f2ba-170">設定 [播放程式 **設定**] 的值 [  >  **其他設定**  >  **目標最小 iOS 版本**]，以強制執行 AR 應用程式的作業系統需求。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-170">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="7f2ba-171">設定必要的架構</span><span class="sxs-lookup"><span data-stu-id="7f2ba-171">Set Required Architecture</span></span>

<span data-ttu-id="7f2ba-172">設定 [ **Player 設定**  >  **其他設定**]  >  **架構** 的值，以強制執行 AR 應用程式的平臺需求。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-172">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="7f2ba-173">設定相機使用方式描述</span><span class="sxs-lookup"><span data-stu-id="7f2ba-173">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="7f2ba-174">設定 [播放程式 **設定**] 的值  >  **其他設定**  >  **相機** 使用方式描述，以要求使用裝置相機的許可權。</span><span class="sxs-lookup"><span data-stu-id="7f2ba-174">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>
