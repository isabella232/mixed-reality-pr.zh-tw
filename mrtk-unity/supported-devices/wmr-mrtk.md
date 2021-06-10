---
title: 部署到 Hololens 和 WMR 耳機
description: 用來建立及部署應用程式至各種裝置的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Visual Studio
ms.openlocfilehash: 1547f0630d307e9e87505890adef4cad366d6c00
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441156"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="d37d6-104">部署到 Hololens 和 WMR 耳機</span><span class="sxs-lookup"><span data-stu-id="d37d6-104">Deploying to Hololens and WMR headsets</span></span>

<span data-ttu-id="d37d6-105">有兩種方式可將使用 MRTK 建立的應用程式部署至您的 windows 裝置、通用 Windows 平臺 (UWP) 和獨立平臺。</span><span class="sxs-lookup"><span data-stu-id="d37d6-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="d37d6-106">針對 HoloLens 1 或 HoloLens 2 所建立的應用程式必須以 UWP 為目標，而針對 WMR 耳機所建立的應用程式可能會以 UWP 或獨立式為目標。</span><span class="sxs-lookup"><span data-stu-id="d37d6-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="d37d6-107">建立和部署 MRTK 至 HoloLens 1、HoloLens 2 和 WMR 耳機 (UWP) </span><span class="sxs-lookup"><span data-stu-id="d37d6-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="d37d6-108">您可以在 [建立應用程式至裝置](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)時找到有關如何建立及部署 **HoloLens 1** 和 **HoloLens 2** (UWP) 的指示。</span><span class="sxs-lookup"><span data-stu-id="d37d6-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="d37d6-109">這些步驟也可讓您部署至 **WMR 耳機**。</span><span class="sxs-lookup"><span data-stu-id="d37d6-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="d37d6-110">在 Visual Studio 中將應用程式部署至您的裝置時，您需要根據裝置設定 Visual Studio 稍有不同。</span><span class="sxs-lookup"><span data-stu-id="d37d6-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="d37d6-111">設定如下所示</span><span class="sxs-lookup"><span data-stu-id="d37d6-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="d37d6-112">平台</span><span class="sxs-lookup"><span data-stu-id="d37d6-112">Platform</span></span> | <span data-ttu-id="d37d6-113">組態</span><span class="sxs-lookup"><span data-stu-id="d37d6-113">Configuration</span></span> | <span data-ttu-id="d37d6-114">架構</span><span class="sxs-lookup"><span data-stu-id="d37d6-114">Architecture</span></span> | <span data-ttu-id="d37d6-115">目標</span><span class="sxs-lookup"><span data-stu-id="d37d6-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="d37d6-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d37d6-116">HoloLens 2</span></span> | <span data-ttu-id="d37d6-117">Release 或 Master</span><span class="sxs-lookup"><span data-stu-id="d37d6-117">Release or Master</span></span> | <span data-ttu-id="d37d6-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="d37d6-118">ARM64</span></span> | <span data-ttu-id="d37d6-119">裝置</span><span class="sxs-lookup"><span data-stu-id="d37d6-119">Device</span></span> |
| <span data-ttu-id="d37d6-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="d37d6-120">HoloLens 1</span></span> | <span data-ttu-id="d37d6-121">Release 或 Master</span><span class="sxs-lookup"><span data-stu-id="d37d6-121">Release or Master</span></span> | <span data-ttu-id="d37d6-122">x86</span><span class="sxs-lookup"><span data-stu-id="d37d6-122">x86</span></span> | <span data-ttu-id="d37d6-123">裝置</span><span class="sxs-lookup"><span data-stu-id="d37d6-123">Device</span></span> |
| <span data-ttu-id="d37d6-124">WMR 耳機</span><span class="sxs-lookup"><span data-stu-id="d37d6-124">WMR Headsets</span></span> | <span data-ttu-id="d37d6-125">Release 或 Master</span><span class="sxs-lookup"><span data-stu-id="d37d6-125">Release or Master</span></span> | <span data-ttu-id="d37d6-126">x64</span><span class="sxs-lookup"><span data-stu-id="d37d6-126">x64</span></span> | <span data-ttu-id="d37d6-127">本機電腦</span><span class="sxs-lookup"><span data-stu-id="d37d6-127">Local Machine</span></span> |

<span data-ttu-id="d37d6-128">**秘訣：** 建立 HoloLens 1、HoloLens 2 或 WMR 時，建議組建設定「目標 SDK 版本」和「最低平臺版本」看起來像下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d37d6-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![組建視窗](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="d37d6-130">其他設定可以是不同的 (例如，組建設定/架構/組建類型，而其他設定則一律可在 Visual Studio 解決方案) 內變更。</span><span class="sxs-lookup"><span data-stu-id="d37d6-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="d37d6-131">請確定 [目標 SDK 版本] 下拉式清單包含 [10.0.18362.0] 選項-如果缺少此選項，則必須安裝 [最新的 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 。</span><span class="sxs-lookup"><span data-stu-id="d37d6-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="d37d6-132">Unity 2019.3 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="d37d6-132">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="d37d6-133">如果 HoloLens 應用程式在裝置上顯示為2D 面板，在部署 UWP 應用程式之前，請確定已在 Unity 2019.3 中設定下列設定：</span><span class="sxs-lookup"><span data-stu-id="d37d6-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="d37d6-134">如果使用舊版 XR：</span><span class="sxs-lookup"><span data-stu-id="d37d6-134">If using the legacy XR:</span></span>

1. <span data-ttu-id="d37d6-135">流覽至 [編輯] > 專案設定、播放機</span><span class="sxs-lookup"><span data-stu-id="d37d6-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="d37d6-136">在 [UWP] 索引標籤的 [ **XR 設定** ] 下，確定已啟用 [ **虛擬實境支援** ]，並已將 **Windows Mixed Reality** sdk 新增至 sdk。</span><span class="sxs-lookup"><span data-stu-id="d37d6-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="d37d6-137">在 Visual Studio 中建立和部署</span><span class="sxs-lookup"><span data-stu-id="d37d6-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="d37d6-138">如果使用 XR 外掛程式：</span><span class="sxs-lookup"><span data-stu-id="d37d6-138">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="d37d6-139">遵循開始使用中找到的步驟 [XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span><span class="sxs-lookup"><span data-stu-id="d37d6-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="d37d6-140">請確定設定設定檔是 **DefaultXRSDKConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="d37d6-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="d37d6-141">流覽至 [ **編輯 > 專案設定]，XR-Plugin 管理** ]，並確定 **Windows Mixed Reality** 已啟用。</span><span class="sxs-lookup"><span data-stu-id="d37d6-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="d37d6-142">在 Visual Studio 中建立和部署</span><span class="sxs-lookup"><span data-stu-id="d37d6-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d37d6-143">如果使用 Unity 2019.3，請選取 [ **ARM64** ]，而非 [ **ARM** ] 作為 Visual Studio 中的組建架構。</span><span class="sxs-lookup"><span data-stu-id="d37d6-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="d37d6-144">使用 Unity 2019.3 中的預設 Unity 設定時，如果因為 Unity bug 而選取 ARM，Unity 應用程式將不會部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d37d6-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="d37d6-145">您可以在 [Unity 的問題追蹤](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)程式上追蹤此資訊。</span><span class="sxs-lookup"><span data-stu-id="d37d6-145">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="d37d6-146">如果需要 ARM 架構，請流覽至 [ **編輯] > 專案設定**]、[播放程式]，然後在 [ **其他設定** ] 功能表下，停用 **圖形作業**。</span><span class="sxs-lookup"><span data-stu-id="d37d6-146">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="d37d6-147">停用 **圖形作業** 可讓應用程式使用 Unity 2019.3. x 的 ARM 組建架構進行部署，但建議使用 ARM64。</span><span class="sxs-lookup"><span data-stu-id="d37d6-147">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="d37d6-148">建立 MRTK，並將其部署至 WMR 耳機 (獨立) </span><span class="sxs-lookup"><span data-stu-id="d37d6-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="d37d6-149">MRTK 的獨立組建可用於 WMR 耳機。</span><span class="sxs-lookup"><span data-stu-id="d37d6-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="d37d6-150">WMR 耳機的獨立組建需要下列額外步驟：</span><span class="sxs-lookup"><span data-stu-id="d37d6-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="d37d6-151">Unity 的 XR SDK 也支援獨立組建中的原生 WMR，但不需要 SteamVR 或 WMR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="d37d6-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="d37d6-152">Unity 的舊版 XR 需要這些步驟。</span><span class="sxs-lookup"><span data-stu-id="d37d6-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="d37d6-153">安裝 [流](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="d37d6-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="d37d6-154">安裝 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="d37d6-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="d37d6-155">安裝 [WMR 外掛程式](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="d37d6-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="d37d6-156">如何使用 WMR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="d37d6-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="d37d6-157">開啟流並搜尋 Windows Mixed Reality 外掛程式</span><span class="sxs-lookup"><span data-stu-id="d37d6-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="d37d6-158">啟動 WMR 外掛程式之前，請確定 SteamVR 已關閉。</span><span class="sxs-lookup"><span data-stu-id="d37d6-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="d37d6-159">啟動 WMR 外掛程式也會啟動 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="d37d6-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="d37d6-160">請確定已插入 WMR 耳機。</span><span class="sxs-lookup"><span data-stu-id="d37d6-160">Make sure the WMR headset is plugged in.</span></span>

    ![WMR 外掛程式搜尋](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="d37d6-162">針對 SteamVR 外掛程式的 Windows Mixed Reality 選取 [ **啟動** ]。</span><span class="sxs-lookup"><span data-stu-id="d37d6-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR 外掛程式](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="d37d6-164">SteamVR 和 WMR 外掛程式將會啟動，並顯示 WMR 耳機的新追蹤狀態視窗。</span><span class="sxs-lookup"><span data-stu-id="d37d6-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="d37d6-165">如需詳細資訊，請造訪 [Windows Mixed Reality 流檔](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="d37d6-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![WMR 啟動外觀](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="d37d6-167">在 Unity 中，開啟您的 MRTK 場景，然後流覽至 [檔案 **> 組建設定**]</span><span class="sxs-lookup"><span data-stu-id="d37d6-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="d37d6-168">建立場景</span><span class="sxs-lookup"><span data-stu-id="d37d6-168">Build the scene</span></span>
    - <span data-ttu-id="d37d6-169">選取 [**新增開啟的場景**]</span><span class="sxs-lookup"><span data-stu-id="d37d6-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="d37d6-170">請確定平臺是 **獨立** 的</span><span class="sxs-lookup"><span data-stu-id="d37d6-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="d37d6-171">選取 **組建**</span><span class="sxs-lookup"><span data-stu-id="d37d6-171">Select **Build**</span></span>
    - <span data-ttu-id="d37d6-172">選擇新組建在檔案總管中的位置</span><span class="sxs-lookup"><span data-stu-id="d37d6-172">Choose the location for the new build in File Explorer</span></span>

    ![獨立的組建設定](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="d37d6-174">將會建立新的 Unity 可執行檔，以啟動您的應用程式，請在檔案總管中選取 Unity 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d37d6-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![檔案總管 Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="d37d6-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d37d6-176">See also</span></span>

- [<span data-ttu-id="d37d6-177">Android 和 iOS 支援</span><span class="sxs-lookup"><span data-stu-id="d37d6-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="d37d6-178">Leap 移動支援</span><span class="sxs-lookup"><span data-stu-id="d37d6-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="d37d6-179">偵測平臺功能</span><span class="sxs-lookup"><span data-stu-id="d37d6-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)