---
title: 使用 Mixed Reality OpenXR 外掛程式
description: 瞭解如何啟用 Unity 專案的 Mixed Reality OpenXR 外掛程式。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: 733bbbd75dd170241e8781e24989d23902781fb9
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333440"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a>使用 Mixed Reality OpenXR 外掛程式

針對以 Unity 2020 為目標的開發人員建立 HoloLens 2 或混合的現實應用程式，OpenXR 外掛程式可以用來取代 WindowsXR 外掛程式，以獲得更好的跨平臺相容性。  Mixed Reality OpenXR 外掛程式也適用于最新的 [混合現實功能工具](welcome-to-mr-feature-tool.md)。

## <a name="prerequisites"></a>必要條件

* 最新的 Unity 2020.3 LTS，建議 2020.3.6 f1 或更新版本。
* 最新的 Unity OpenXR 外掛程式，建議1.2 或更新版本
* [適用于 HoloLens 2 開發的](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)最新工具
* 最新的 MRTK (選用) ，建議2.6 版或更新版本
* 最新的混合現實 OpenXR 外掛程式，建議版本0.9.5 或更新版本

> [!NOTE]
> 如果您是在 Windows 電腦上建立 VR 應用程式，則不一定需要混合現實 OpenXR 外掛程式。 但是，如果您要自訂適用于 HP 重設系的控制器對應，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。

## <a name="setting-up-your-project-with-mrtk"></a>使用 MRTK 設定您的專案

適用于 Unity 的 MRTK 會提供跨平臺輸入系統、基礎元件，以及空間互動的常見組建區塊。 MRTK 第 2 版主要用於加速開發適用於 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台的應用程式。 此專案的目標是減少進入障礙、建立混合實境應用程式，以及回饋伴著我們成長的社群。

> [!div class="nextstepaction"]
> [使用 MRTK 設定您的專案](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

如需詳細的功能詳細資料，請參閱 [MRTK 的檔](/windows/mixed-reality/mrtk-unity) 。

## <a name="manual-setup-without-mrtk"></a>手動設定而不 MRTK

使用新的混合現實功能工具應用程式來安裝 OpenXR 外掛程式。 遵循 [安裝和使用](welcome-to-mr-feature-tool.md) 方式的指示，然後在混合現實工具組類別中選取 **Mixed reality OpenXR 外掛程式** 套件：

![醒目提示 open xr 外掛程式的混合現實功能工具套件視窗](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>設定您的組建目標

如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](images/wmr-config-img-3.png)

如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：

1. 選取 [檔案 **> 組建設定 ...** ]
2. 選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]
3. 將 **架構** 設定為 **ARM 64**
4. 將 **目標裝置** 設定為 **HoloLens**
5. 將 **組建類型** 設定為 **D3D**
6. 將 **UWP SDK** 設定為 **最新安裝**

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>設定 OpenXR 的 XR 外掛程式管理

若要將 OpenXR 設定為 Unity 中的執行時間：

1. 在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]
2. 在設定清單中，選取 [ **XR 外掛程式管理**]
3. 檢查 Startup 和 **OpenXR** 方塊的 **Initialize XR**
4. 如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [ **Microsoft HoloLens 功能集**]

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](images/openxr-img-05.png)

## <a name="optimization"></a>Optimization

如果您是針對 HoloLens 2 進行開發，請流覽至 **Mixed Reality> OpenXR > 套用建議的 HoloLens 2 專案設定** ，以取得更佳的應用程式效能。

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](images/openxr-img-08.png)

> [!IMPORTANT]
> 如果您在 **OpenXR 外掛程式** 旁邊看到紅色警告圖示，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。 Unity 編輯器可能需要自行重新開機，變更才會生效。

![OpenXR 專案驗證視窗的螢幕擷取畫面](images/openxr-img-06.png)

您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！  繼續進行下一節，以瞭解如何使用 OpenXR 範例。

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>適用于 OpenXR 和 HoloLens 2 的 Unity 範例專案

查看範例 unity 專案的 [OpenXR Mixed Reality 範例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 存放庫展示如何使用 Mixed reality OpenXR 外掛程式建立 HoloLens 2 或混合現實耳機的 unity 應用程式。

## <a name="using-mrtk-with-openxr-support"></a>搭配使用 MRTK 與 OpenXR 支援

MRTK-Unity 支援從2.5.3 版本開始的 Mixed Reality OpenXR 外掛程式。

1. 如果您還沒有這麼做，請再次開啟 [Mixed Reality 功能工具](welcome-to-mr-feature-tool.md) 以安裝混合現實工具組。 **基礎** 套件中的 OpenXR 支援。
2. 移至偵測器中的 MixedReality 工具組元件腳本，並切換至 **DefaultOpenXRConfigurationProfile** 設定檔：

    ![在偵測器的混合現實工具組元件中切換 MRTK 設定的螢幕擷取畫面](images/openxr-img-11.png)

    1. 如需有關 [遷移至 OpenXR 的深入資訊](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，請參閱 MRTK 檔。

> [!NOTE]
> 從舊版 MRTK 進行升級時，請確定 **資產/MixedRealityToolkit. 產生/link.xml** 檔案中有下列這一行：
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 如果您開始使用 MRTK 2.5.4 或更新版本，則預設會新增這一行。

## <a name="next-steps"></a>下一步

現在您已將專案設定為 OpenXR 並可存取範例，請查看我們的 OpenXR 外掛程式目前支援的 [功能](openxr-supported-features.md) 。

## <a name="have-feedback"></a>有任何意見反應嗎？

OpenXR 仍是實驗性的，因此我們會感謝您提供給我們的意見反應，以協助您更妥善地進行。 您可以使用 **Microsoft** OpenXR 標記您的論壇文章，並 [](https://aka.ms/unityforums)  +   **HoloLens 2** 或 **Windows Mixed Reality**，在 Unity 論壇中找到我們。

## <a name="see-also"></a>另請參閱

* [在沒有 MRTK 的情況下設定專案](configure-unity-project.md)
* [Unity 的建議設定](recommended-settings-for-unity.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md#how-to-profile-with-unity)
