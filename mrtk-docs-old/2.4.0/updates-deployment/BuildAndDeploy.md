---
title: BuildAndDeploy
description: 用來建立及部署應用程式至各種裝置的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Visual Studio、Android、IOS
ms.openlocfilehash: 43ce812a7da01ae99e4005856bade6ab291664b5
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780463"
---
# <a name="building-and-deploying-mrtk"></a>建立和部署 MRTK

若要在裝置上執行應用程式作為獨立應用程式 (HoloLens、Android、iOS 等 ) ，必須在 unity 專案中執行組建和部署步驟。 建立及部署使用 MRTK 的應用程式，就像是建立和部署任何其他 Unity 應用程式一樣。 沒有任何 MRTK 特定的指示。 請參閱下面的詳細步驟，以瞭解如何建立及部署適用于 HoloLens 的 Unity 應用程式。  深入瞭解如何在 [發行組建](https://docs.unity3d.com/Manual/PublishingBuilds.html)中建立其他平臺。

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a> (UWP) 建立及部署 MRTK 至 HoloLens 1 和 HoloLens 2

您可以在 [建立應用程式至裝置](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)時找到有關如何建立及部署 hololens 1 和 hololens 2 (UWP) 的指示。

**秘訣：** 針對 WMR、HoloLens 1 或 HoloLens 2 建立時，建議組建設定「目標 SDK 版本」和「最低平臺版本」看起來像下圖所示：

![組建視窗](../features/Images/getting_started/BuildWindow.png)

其他設定可能會不同 (例如，組建設定/架構/組建類型，而其他設定則一律會在 Visual Studio 方案) 內變更。

請確定 [目標 SDK 版本] 下拉式清單包含 [10.0.18362.0] 選項-如果缺少此選項，則必須安裝 [最新的 WINDOWS SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 。

### <a name="unity-20193-and-hololens"></a>Unity 2019.3 和 HoloLens

如果 HoloLens 應用程式在裝置上顯示為2D 面板，在部署 UWP 應用程式之前，請確定已在 Unity 2019.3 中設定下列設定：

如果使用舊版 XR：

1. 流覽至 [編輯] > 專案設定、播放機
1. 在 [UWP] 索引標籤中的 [ **XR 設定** ] 下，確定已啟用 [ **虛擬實境支援** ]，並已將 **Windows Mixed Reality** SDK 新增至 sdk。
1. Visual Studio 中的組建和部署

如果使用 XR 外掛程式：

1. Follow the steps found in [Getting Started with XRSDK](../configuration/GettingStartedWithMRTKAndXRSDK.md)
1. 請確定設定設定檔是 **DefaultXRSDKConfigurationProfile**
1. 流覽至 [ **編輯 > 專案設定]，XR-Plugin 管理** ]，並確定已啟用 [ **Windows Mixed Reality** ]。
1. Visual Studio 中的組建和部署

>[!IMPORTANT]
> 如果使用 Unity 2019.3，請在 Visual Studio 中選取 **ARM64** 而不是 **ARM** 作為組建架構。 使用 Unity 2019.3 中的預設 Unity 設定時，如果因為 Unity bug 而選取 ARM，Unity 應用程式將不會部署到 HoloLens。 您可以在 [Unity 的問題追蹤](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)程式上追蹤此資訊。
>
> 如果需要 ARM 架構，請流覽至 [ **編輯] > 專案設定**]、[播放程式]，然後在 [ **其他設定** ] 功能表下，停用 **圖形作業**。 停用 **圖形作業** 可讓應用程式使用 Unity 2019.3. x 的 ARM 組建架構進行部署，但建議使用 ARM64。

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a>建立及部署 MRTK 至 Windows Mixed Reality 耳機

Windows Mixed Reality (WMR) 耳機可用於通用 Windows 平臺 (UWP) 和獨立組建。  WMR 耳機的獨立組建需要下列額外步驟：

> [!NOTE]
> Unity 的 XR SDK 也支援獨立組建中的原生 WMR，但不需要 SteamVR 或 WMR 外掛程式。 Unity 的舊版 XR 需要這些步驟。

1. 安裝 [流](https://store.steampowered.com/about/)
1. 安裝 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)
1. 安裝 [WMR 外掛程式](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

### <a name="how-to-use-wmr-plugin"></a>如何使用 WMR 外掛程式

1. 開啟流並搜尋 Windows Mixed Reality 外掛程式
    - 啟動 WMR 外掛程式之前，請確定 SteamVR 已關閉。 啟動 WMR 外掛程式也會啟動 SteamVR。
    - 請確定已插入 WMR 耳機。

    ![WMR 外掛程式搜尋](../features/Images/BuildDeploy/WMR/SteamSearchWMRPlugin.png)

1. 針對 SteamVR 外掛程式的 Windows Mixed Reality，請選取 [ **啟動** ]。

    ![WMR 外掛程式](../features/Images/BuildDeploy/WMR/WMRPlugin.png)

    - SteamVR 和 WMR 外掛程式將會啟動，並顯示 WMR 耳機的新追蹤狀態視窗。
    - 如需詳細資訊，請造訪 [Windows Mixed Reality 流檔](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)

        ![WMR 啟動外觀](../features/Images/BuildDeploy/WMR/WMRPluginActive.png)

1. 在 Unity 中，開啟您的 MRTK 場景，然後流覽至 [檔案 **> 組建設定**]

1. 建立場景
    - 選取 [**新增開啟的場景**]
    - 請確定平臺是 **獨立** 的
    - 選取 **組建**
    - 在 [檔案瀏覽器] 中選擇新組建的位置

    ![獨立的組建設定](../features/Images/BuildDeploy/WMR/BuildSettingsStandaloneUnity.png)

1. 將會建立新的 Unity 可執行檔，以啟動您的應用程式在 [檔案瀏覽器] 中選取 Unity 可執行檔。

    ![File Explorer Unity](../features/Images/BuildDeploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>另請參閱

- [Android 和 iOS 支援](../features/CrossPlatform/UsingARFoundation.md)
- [Leap 移動支援](../features/CrossPlatform/LeapMotionMRTK.md)
- [偵測平臺功能](../features/DetectingPlatformCapabilities.md)
