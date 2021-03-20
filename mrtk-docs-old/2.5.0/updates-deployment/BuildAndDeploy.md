---
title: BuildAndDeploy
description: 用來建立及部署應用程式至各種裝置的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Visual Studio、Android、IOS
ms.openlocfilehash: cbf17cfd463ee375d285a36aef1705b4d911107f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687428"
---
# <a name="building-and-deploying-mrtk"></a><span data-ttu-id="237ce-104">建立和部署 MRTK</span><span class="sxs-lookup"><span data-stu-id="237ce-104">Building and deploying MRTK</span></span>

<span data-ttu-id="237ce-105">若要在裝置上執行應用程式作為獨立應用程式 (HoloLens、Android、iOS 等 ) ，必須在 unity 專案中執行組建和部署步驟。</span><span class="sxs-lookup"><span data-stu-id="237ce-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="237ce-106">建立及部署使用 MRTK 的應用程式，就像是建立和部署任何其他 Unity 應用程式一樣。</span><span class="sxs-lookup"><span data-stu-id="237ce-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="237ce-107">沒有任何 MRTK 特定的指示。</span><span class="sxs-lookup"><span data-stu-id="237ce-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="237ce-108">請參閱下面的詳細步驟，以瞭解如何建立及部署適用于 HoloLens 的 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="237ce-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span>  <span data-ttu-id="237ce-109">深入瞭解如何在 [發行組建](https://docs.unity3d.com/Manual/PublishingBuilds.html)中建立其他平臺。</span><span class="sxs-lookup"><span data-stu-id="237ce-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a><span data-ttu-id="237ce-110">建立及部署 MRTK 至 HoloLens 1 和 HoloLens 2 (UWP) </span><span class="sxs-lookup"><span data-stu-id="237ce-110">Building and deploying MRTK to HoloLens 1 and HoloLens 2 (UWP)</span></span>

<span data-ttu-id="237ce-111">您可以在 [建立應用程式至裝置](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)時找到有關如何建立及部署 HoloLens 1 和 HOLOLENS 2 (UWP) 的指示。</span><span class="sxs-lookup"><span data-stu-id="237ce-111">Instructions on how to build and deploy for HoloLens 1 and HoloLens 2 (UWP) can be found at [building your application to device](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span>

<span data-ttu-id="237ce-112">**秘訣：** 建立 WMR、HoloLens 1 或 HoloLens 2 時，建議組建設定「目標 SDK 版本」和「最低平臺版本」看起來像下圖所示：</span><span class="sxs-lookup"><span data-stu-id="237ce-112">**Tip:** When building for WMR, HoloLens 1, or HoloLens 2, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![組建視窗](../features/Images/getting_started/BuildWindow.png)

<span data-ttu-id="237ce-114">其他設定可以是不同的 (例如，組建設定/架構/組建類型，而其他設定則一律可在 Visual Studio 解決方案) 內變更。</span><span class="sxs-lookup"><span data-stu-id="237ce-114">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="237ce-115">請確定 [目標 SDK 版本] 下拉式清單包含 [10.0.18362.0] 選項-如果缺少此選項，則必須安裝 [最新的 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 。</span><span class="sxs-lookup"><span data-stu-id="237ce-115">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="237ce-116">Unity 2019.3 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="237ce-116">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="237ce-117">如果 HoloLens 應用程式在裝置上顯示為2D 面板，在部署 UWP 應用程式之前，請確定已在 Unity 2019.3 中設定下列設定：</span><span class="sxs-lookup"><span data-stu-id="237ce-117">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="237ce-118">如果使用舊版 XR：</span><span class="sxs-lookup"><span data-stu-id="237ce-118">If using the legacy XR:</span></span>

1. <span data-ttu-id="237ce-119">流覽至 [編輯] > 專案設定、播放機</span><span class="sxs-lookup"><span data-stu-id="237ce-119">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="237ce-120">在 [UWP] 索引標籤的 [ **XR 設定** ] 下，確定已啟用 [ **虛擬實境支援** ]，並已將 **Windows Mixed Reality** sdk 新增至 sdk。</span><span class="sxs-lookup"><span data-stu-id="237ce-120">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="237ce-121">在 Visual Studio 中建立和部署</span><span class="sxs-lookup"><span data-stu-id="237ce-121">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="237ce-122">如果使用 XR 外掛程式：</span><span class="sxs-lookup"><span data-stu-id="237ce-122">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="237ce-123">遵循開始使用中找到的步驟 [XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)</span><span class="sxs-lookup"><span data-stu-id="237ce-123">Follow the steps found in [Getting Started with XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)</span></span>
1. <span data-ttu-id="237ce-124">請確定設定設定檔是 **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="237ce-124">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="237ce-125">流覽至 [ **編輯 > 專案設定]，XR-Plugin 管理** ]，並確定 **Windows Mixed Reality** 已啟用。</span><span class="sxs-lookup"><span data-stu-id="237ce-125">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="237ce-126">在 Visual Studio 中建立和部署</span><span class="sxs-lookup"><span data-stu-id="237ce-126">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="237ce-127">如果使用 Unity 2019.3，請選取 [ **ARM64** ]，而非 [ **ARM** ] 作為 Visual Studio 中的組建架構。</span><span class="sxs-lookup"><span data-stu-id="237ce-127">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="237ce-128">使用 Unity 2019.3 中的預設 Unity 設定時，如果因為 Unity bug 而選取 ARM，Unity 應用程式將不會部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="237ce-128">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="237ce-129">您可以在 [Unity 的問題追蹤](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)程式上追蹤此資訊。</span><span class="sxs-lookup"><span data-stu-id="237ce-129">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="237ce-130">如果需要 ARM 架構，請流覽至 [ **編輯] > 專案設定**]、[播放程式]，然後在 [ **其他設定** ] 功能表下，停用 **圖形作業**。</span><span class="sxs-lookup"><span data-stu-id="237ce-130">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="237ce-131">停用 **圖形作業** 可讓應用程式使用 Unity 2019.3. x 的 ARM 組建架構進行部署，但建議使用 ARM64。</span><span class="sxs-lookup"><span data-stu-id="237ce-131">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a><span data-ttu-id="237ce-132">建立 MRTK 並部署到 Windows Mixed Reality 耳機</span><span class="sxs-lookup"><span data-stu-id="237ce-132">Building and deploying MRTK to a Windows Mixed Reality Headset</span></span>

<span data-ttu-id="237ce-133">Windows Mixed Reality (WMR) 耳機可用於通用 Windows 平臺 (UWP) 和獨立組建。</span><span class="sxs-lookup"><span data-stu-id="237ce-133">The Windows Mixed Reality (WMR) headset can be used for Universal Windows Platform (UWP) and Standalone builds.</span></span>  <span data-ttu-id="237ce-134">WMR 耳機的獨立組建需要下列額外步驟：</span><span class="sxs-lookup"><span data-stu-id="237ce-134">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="237ce-135">Unity 的 XR SDK 也支援獨立組建中的原生 WMR，但不需要 SteamVR 或 WMR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="237ce-135">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="237ce-136">Unity 的舊版 XR 需要這些步驟。</span><span class="sxs-lookup"><span data-stu-id="237ce-136">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="237ce-137">安裝 [流](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="237ce-137">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="237ce-138">安裝 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="237ce-138">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="237ce-139">安裝 [WMR 外掛程式](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="237ce-139">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="237ce-140">如何使用 WMR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="237ce-140">How to use WMR plugin</span></span>

1. <span data-ttu-id="237ce-141">開啟流並搜尋 Windows Mixed Reality 外掛程式</span><span class="sxs-lookup"><span data-stu-id="237ce-141">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="237ce-142">啟動 WMR 外掛程式之前，請確定 SteamVR 已關閉。</span><span class="sxs-lookup"><span data-stu-id="237ce-142">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="237ce-143">啟動 WMR 外掛程式也會啟動 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="237ce-143">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="237ce-144">請確定已插入 WMR 耳機。</span><span class="sxs-lookup"><span data-stu-id="237ce-144">Make sure the WMR headset is plugged in.</span></span>

    ![WMR 外掛程式搜尋](../features/Images/BuildDeploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="237ce-146">針對 SteamVR 外掛程式的 Windows Mixed Reality 選取 [ **啟動** ]。</span><span class="sxs-lookup"><span data-stu-id="237ce-146">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR 外掛程式](../features/Images/BuildDeploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="237ce-148">SteamVR 和 WMR 外掛程式將會啟動，並顯示 WMR 耳機的新追蹤狀態視窗。</span><span class="sxs-lookup"><span data-stu-id="237ce-148">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="237ce-149">如需詳細資訊，請造訪 [Windows Mixed Reality 流檔](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="237ce-149">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![WMR 啟動外觀](../features/Images/BuildDeploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="237ce-151">在 Unity 中，開啟您的 MRTK 場景，然後流覽至 [檔案 **> 組建設定**]</span><span class="sxs-lookup"><span data-stu-id="237ce-151">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="237ce-152">建立場景</span><span class="sxs-lookup"><span data-stu-id="237ce-152">Build the scene</span></span>
    - <span data-ttu-id="237ce-153">選取 [**新增開啟的場景**]</span><span class="sxs-lookup"><span data-stu-id="237ce-153">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="237ce-154">請確定平臺是 **獨立** 的</span><span class="sxs-lookup"><span data-stu-id="237ce-154">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="237ce-155">選取 **組建**</span><span class="sxs-lookup"><span data-stu-id="237ce-155">Select **Build**</span></span>
    - <span data-ttu-id="237ce-156">選擇新組建在檔案總管中的位置</span><span class="sxs-lookup"><span data-stu-id="237ce-156">Choose the location for the new build in File Explorer</span></span>

    ![獨立的組建設定](../features/Images/BuildDeploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="237ce-158">將會建立新的 Unity 可執行檔，以啟動您的應用程式，請在檔案總管中選取 Unity 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="237ce-158">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![檔案總管 Unity](../features/Images/BuildDeploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="237ce-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="237ce-160">See also</span></span>

- [<span data-ttu-id="237ce-161">Android 和 iOS 支援</span><span class="sxs-lookup"><span data-stu-id="237ce-161">Android and iOS Support</span></span>](../features/CrossPlatform/UsingARFoundation.md)
- [<span data-ttu-id="237ce-162">Leap 移動支援</span><span class="sxs-lookup"><span data-stu-id="237ce-162">Leap Motion Support</span></span>](../features/CrossPlatform/LeapMotionMRTK.md)
- [<span data-ttu-id="237ce-163">偵測平臺功能</span><span class="sxs-lookup"><span data-stu-id="237ce-163">Detecting Platform Capabilities</span></span>](../features/DetectingPlatformCapabilities.md)
